---
title: Használjon Azure Machine Learning alapú modelleket
description: Használjon Azure Machine Learning alapú modelleket a Dynamics 365 Customer Insights alkalmazásban.
ms.date: 09/22/2022
ms.subservice: audience-insights
ms.topic: tutorial
author: naravill
ms.author: naravill
ms.reviewer: mhart
manager: shellyha
ms.openlocfilehash: 8d9c9324ea4840b585b9af1a58d505ccaea6f18e
ms.sourcegitcommit: be341cb69329e507f527409ac4636c18742777d2
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/30/2022
ms.locfileid: "9609828"
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

Azure gépi tanulás tervező vizuális vásznat biztosít, ahol áthúzhatja az adatkészleteket és modulokat. A tervező által létrehozott kötegelt csővezetékek a Customer Insights szolgáltatásba integrálhatók, ha ennek megfelelően vannak konfigurálva. 

## <a name="working-with-azure-machine-learning-sdk"></a>Az Azure Machine Learning SDK használata

Az adatszakértők és az AI-fejlesztők az [Azure Machine Learning SDK-t](/python/api/overview/azure/ml/?preserve-view=true&view=azure-ml-py) használják a gépi tanulási munkafolyamatok létrehozásához. Jelenleg az SDK segítségével betanított modellek nem integrálhatók közvetlenül a Customer Insights szolgáltatáshoz. A Customer Insights integrációhoz az adott modellt elfoglaló kötegelt származtatási folyamata.

## <a name="batch-pipeline-requirements-to-integrate-with-customer-insights"></a>A kötegelt folyamat követelményei a Customer Insights való integrálásra

### <a name="dataset-configuration"></a>Adathalmaz-konfiguráció

Adatkészletek létrehozása a Customer Insights entitásadatainak a kötegelt következtetési folyamathoz való használatához. Regisztrálja ezeket az adatkészleteket a munkaterületen. Jelenleg [a táblázatos adathalmazokat](/azure/machine-learning/how-to-create-register-datasets#tabulardataset) csak .csv formátumban támogatjuk. Folyamatparaméterként paraméterezze az entitásadatoknak megfelelő adatkészleteket.

- Az adathalmaz paraméterei a tervezőben

  Nyissa meg a tervezőben az **oszlopok kiválasztása az adathalmazban**, és válassza a **beállítás folyamatparaméterként**, ahol megadja a paraméter nevét.

  :::image type="content" source="media/intelligence-designer-dataset-parameters.png" alt-text="Az adathalmaz paraméterezései a tervezőben.":::

- DataSet paraméter az SDK (Python) alkalmazásban

   ```python
   HotelStayActivity_dataset = Dataset.get_by_name(ws, name='Hotel Stay Activity Data')
   HotelStayActivity_pipeline_param = PipelineParameter(name="HotelStayActivity_pipeline_param", default_value=HotelStayActivity_dataset)
   HotelStayActivity_ds_consumption = DatasetConsumptionConfig("HotelStayActivity_dataset", HotelStayActivity_pipeline_param)
   ```

### <a name="batch-inference-pipeline"></a>A kötegelt származtatott folyamatok
  
- A tervezőben egy betanítási folyamat használatával hozzon létre vagy frissítsen egy következtetési folyamatot. Jelenleg a rendszer csak a tételekre vonatkozó következtetéseket támogatja.

- Az SDK használatával tegye közzé a folyamatot egy végpont. A Customer Insights jelenleg a Machine Learning munkaterület kötegelt folyamatvégpontjában levő alapértelmezett folyamattal integrálható.

   ```python
   published_pipeline = pipeline.publish(name="ChurnInferencePipeline", description="Published Churn Inference pipeline")
   pipeline_endpoint = PipelineEndpoint.get(workspace=ws, name="ChurnPipelineEndpoint") 
   pipeline_endpoint.add_default(pipeline=published_pipeline)
   ```

### <a name="import-pipeline-data-into-customer-insights"></a>Folyamatadatok importálása a Customer Insightsba

- A tervező biztosítja az [exportálási adatmodult](/azure/machine-learning/algorithm-module-reference/export-data), amely lehetővé teszi a folyamat kimenetének exportálását az Azure Storage rendszerbe. Jelenleg a modulnak az **Azure Blob Storage** adattár típust kell használnia, és paraméterré kell alakítani az **adattár** és a relatív **elérési út** elemeket. A Customer Insights mindkét paramétert felülbírálja a folyamat végrehajtása során a termékhez elérhető adattár és elérési út értékével.

  :::image type="content" source="media/intelligence-designer-importdata.png" alt-text="Adatmodell-konfiguráció exportálása.":::

- Amikor a következtetési kimenetet kóddal írja, töltse fel a kimenetet egy elérési útra a munkaterületen *regisztrált adattárban*. Ha az elérési út és az adattár paraméterei a folyamatban vannak, a Customer Insights képes olvasni és importálni a származtatott kimenetet. Jelenleg egyetlen táblázatos kimenet támogatott CSV formátumban. Az elérési útnak tartalmaznia kell a könyvtárat és a fájlnevet.

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