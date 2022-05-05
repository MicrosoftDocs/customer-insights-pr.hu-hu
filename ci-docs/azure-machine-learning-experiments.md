---
title: Azure Machine Learning-kísérletek
description: Használjon Azure Machine Learning alapú modelleket a Dynamics 365 Customer Insights alkalmazásban.
ms.date: 12/02/2021
ms.subservice: audience-insights
ms.topic: tutorial
author: naravill
ms.author: naravill
ms.reviewer: mhart
manager: shellyha
ms.openlocfilehash: cefd037a021b669e827f0593d63b938d452963f7
ms.sourcegitcommit: b7dbcd5627c2ebfbcfe65589991c159ba290d377
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/27/2022
ms.locfileid: "8642608"
---
# <a name="use-azure-machine-learning-based-models"></a>Használjon Azure Machine Learning alapú modelleket

A Dynamics 365 Customer Insights egyesített adatok a forrása a gépi tanulás modellek létrehozásának, amelyek további üzleti ismereteket hozhatnak létre. A Customer Insights a saját egyéni modelljeinek használatával integrálódik az Azure Machine Learning rendszerbe.

## <a name="prerequisites"></a>Előfeltételek

- A Customer Insights szolgáltatás elérése
- Aktív Azure Enterprise-előfizetés
- [Egyesített ügyfélprofilok](data-unification.md)
- [Entitás exportálása az Azure Blob Storage-ba](export-azure-blob-storage.md) konfigurálva

## <a name="set-up-azure-machine-learning-workspace"></a>Az Azure Machine Learning munkaterület beállítása

1. További tudnivalókért lásd: [Azure Machine Learning munkaterület létrehozása](/azure/machine-learning/concept-workspace#-create-a-workspace) a munkaterület létrehozásához használt különböző beállításokhoz. A legjobb teljesítmény érdekében hozza létre a munkaterületet egy Azure-régióban, amely földrajzilag legközelebb áll a Customer Insights környezetéhez.

1. Nyissa meg a munkaterületet az [Azure Machine Learning Studio](https://ml.azure.com/) segítségével. A munkaterületre többféle [módon léphet kapcsolatba](/azure/machine-learning/concept-workspace#tools-for-workspace-interaction).

## <a name="work-with-azure-machine-learning-designer"></a>Az Azure Machine Learning tervező használata

Az Azure gépi tanulás designer vizuális vásznat biztosít, ahol az adatkészleteket és modulokat húzhatja és helyezheti el. A tervező által létrehozott kötegelt csővezetékek a Customer Insights szolgáltatásba integrálhatók, ha ennek megfelelően vannak konfigurálva. 
   
## <a name="working-with-azure-machine-learning-sdk"></a>Az Azure Machine Learning SDK használata

Az adatszakértők és az AI-fejlesztők az [Azure Machine Learning SDK-t](/python/api/overview/azure/ml/?preserve-view=true&view=azure-ml-py) használják a gépi tanulási munkafolyamatok létrehozásához. Jelenleg az SDK segítségével betanított modellek nem integrálhatók közvetlenül a Customer Insights szolgáltatáshoz. A Customer Insights integrációhoz az adott modellt elfoglaló kötegelt származtatási folyamata.

## <a name="batch-pipeline-requirements-to-integrate-with-customer-insights"></a>A kötegelt folyamat követelményei a Customer Insights való integrálásra

### <a name="dataset-configuration"></a>Adathalmaz konfigurálása

Létre kell hoznia az adathalmazokat ahhoz, hogy az entitások adatait a Customer Insights alapján a rendszer áttekintse a gyártási folyamatba. Ezeket az adathalmazokat regisztrálni kell a munkaterületen. Jelenleg [a táblázatos adathalmazokat](/azure/machine-learning/how-to-create-register-datasets#tabulardataset) csak .csv formátumban támogatjuk. Az entitásadatoknak megfelelő adathalmazokat a folyamatparaméterként kell megadni.
   
* Az adathalmaz paraméterei a tervezőben
   
     Nyissa meg a tervezőben az **oszlopok kiválasztása az adathalmazban**, és válassza a **beállítás folyamatparaméterként**, ahol megadja a paraméter nevét.

     > [!div class="mx-imgBorder"]
     > ![Az adathalmaz paraméterezései a tervezőben.](media/intelligence-designer-dataset-parameters.png "Az adathalmaz paraméterezései a tervezőben")
   
* DataSet paraméter az SDK (Python) alkalmazásban
   
   ```python
   HotelStayActivity_dataset = Dataset.get_by_name(ws, name='Hotel Stay Activity Data')
   HotelStayActivity_pipeline_param = PipelineParameter(name="HotelStayActivity_pipeline_param", default_value=HotelStayActivity_dataset)
   HotelStayActivity_ds_consumption = DatasetConsumptionConfig("HotelStayActivity_dataset", HotelStayActivity_pipeline_param)
   ```

### <a name="batch-inference-pipeline"></a>A kötegelt származtatott folyamatok
  
* A tervezőben egy képzési folyamat használható a következtetések közti folyamat létrehozására vagy frissítésére. Jelenleg a rendszer csak a tételekre vonatkozó következtetéseket támogatja.

* A SDK segítségével közzéteheti a folyamatot egy végpontra. A Customer Insights jelenleg a Machine Learning munkaterület kötegelt folyamatvégpontjában levő alapértelmezett folyamattal integrálható.
   
   ```python
   published_pipeline = pipeline.publish(name="ChurnInferencePipeline", description="Published Churn Inference pipeline")
   pipeline_endpoint = PipelineEndpoint.get(workspace=ws, name="ChurnPipelineEndpoint") 
   pipeline_endpoint.add_default(pipeline=published_pipeline)
   ```

### <a name="import-pipeline-data-into-customer-insights"></a>Folyamatadatok importálása a Customer Insightsba

* A tervező biztosítja az [exportálási adatmodult](/azure/machine-learning/algorithm-module-reference/export-data), amely lehetővé teszi a folyamat kimenetének exportálását az Azure Storage rendszerbe. Jelenleg a modulnak az **Azure Blob Storage** adattár típust kell használnia, és paraméterré kell alakítani az **adattár** és a relatív **elérési út** elemeket. A Customer Insights mindkét paramétert felülbírálja a folyamat végrehajtása során a termékhez elérhető adattár és elérési út értékével.
   > [!div class="mx-imgBorder"]
   > ![Adatmodell-konfiguráció exportálása.](media/intelligence-designer-importdata.png "Adatmodell-konfiguráció exportálása")
   
* Amikor kódot használ a származtatott kimenet írásakor, feltöltheti a kimenetet a megfelelő elérési útra a munkaterületen található *regisztrált adattáron* belül. Ha az elérési út és az adattár paraméterei a folyamatban vannak, a Customer Insights képes olvasni és importálni a származtatott kimenetet. Jelenleg egyetlen táblázatos kimenet támogatott CSV formátumban. Az elérési útnak tartalmaznia kell a könyvtárat és a fájlnevet.

   ```python
   # In Pipeline setup script
      OutputPathParameter = PipelineParameter(name="output_path", default_value="HotelChurnOutput/HotelChurnOutput.csv")
      OutputDatastoreParameter = PipelineParameter(name="output_datastore", default_value="workspaceblobstore")
   ...
   # In pipeline execution script
      run = Run.get_context()
      ws = run.experiment.workspace
      datastore = Datastore.get(ws, output_datastore) # output_datastore is parameterized
      directory_name =  os.path.dirname(output_path)  # output_path is parameterized.
      
      # Datastore.upload() or Dataset.File.upload_directory() are supported methods to uplaod the data
      # datastore.upload(src_dir=<<working directory>>, target_path=directory_name, overwrite=False, show_progress=True)
      output_dataset = Dataset.File.upload_directory(src_dir=<<working directory>>, target = (datastore, directory_name)) # Remove trailing "/" from directory_name
   ```


[!INCLUDE [footer-include](includes/footer-banner.md)]