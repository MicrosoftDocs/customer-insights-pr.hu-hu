---
title: Azure Machine Learning-kísérletek
description: Használjon Azure Machine Learning alapú modelleket a Dynamics 365 Customer Insights alkalmazásban.
ms.date: 11/30/2020
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: tutorial
author: naravill
ms.author: mhart
ms.reviewer: m-hartmann
manager: shellyha
ms.openlocfilehash: c166015b92596da0c6097e3d25e89579a5186ce0
ms.sourcegitcommit: 139548f8a2d0f24d54c4a6c404a743eeeb8ef8e0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/15/2021
ms.locfileid: "5267909"
---
# <a name="use-azure-machine-learning-based-models"></a><span data-ttu-id="6638b-103">Használjon Azure Machine Learning alapú modelleket</span><span class="sxs-lookup"><span data-stu-id="6638b-103">Use Azure Machine Learning-based models</span></span>

<span data-ttu-id="6638b-104">A Dynamics 365 Customer Insights egyesített adatok a forrása a gépi tanulás modellek létrehozásának, amelyek további üzleti ismereteket hozhatnak létre.</span><span class="sxs-lookup"><span data-stu-id="6638b-104">The unified data in Dynamics 365 Customer Insights is a source for building machine learning models that can generate additional business insights.</span></span> <span data-ttu-id="6638b-105">A Customer Insights integrál a Machine Learning Studióval (klasszikus) és az Azure Machine Learninggel a saját egyéni modelljei használatához.</span><span class="sxs-lookup"><span data-stu-id="6638b-105">Customer Insights integrates with Machine Learning Studio (classic) and Azure Machine Learning to use your own custom models.</span></span> <span data-ttu-id="6638b-106">A Machine Learning Studio (klasszikus) verzióra épülő kísérletekre vonatkozóan a [Machine Learning Studio (klasszikus) kísérletek](machine-learning-studio-experiments.md) című rész tartalmaz példákat.</span><span class="sxs-lookup"><span data-stu-id="6638b-106">Refer to [Machine Learning Studio (classic) experiments](machine-learning-studio-experiments.md) for examples of experiments built on Machine Learning Studio (classic).</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="6638b-107">Előfeltételek</span><span class="sxs-lookup"><span data-stu-id="6638b-107">Prerequisites</span></span>

- <span data-ttu-id="6638b-108">A Customer Insights szolgáltatás elérése</span><span class="sxs-lookup"><span data-stu-id="6638b-108">Access to Customer Insights</span></span>
- <span data-ttu-id="6638b-109">Aktív Azure Enterprise-előfizetés</span><span class="sxs-lookup"><span data-stu-id="6638b-109">Active Azure Enterprise subscription</span></span>
- [<span data-ttu-id="6638b-110">Egyesített ügyfélprofilok</span><span class="sxs-lookup"><span data-stu-id="6638b-110">Unified customer profiles</span></span>](data-unification.md)
- <span data-ttu-id="6638b-111">[Entitás exportálása az Azure Blob Storage-ba](export-azure-blob-storage.md) konfigurálva</span><span class="sxs-lookup"><span data-stu-id="6638b-111">[Entity export to Azure Blob storage](export-azure-blob-storage.md) configured</span></span>

## <a name="set-up-azure-machine-learning-workspace"></a><span data-ttu-id="6638b-112">Az Azure Machine Learning munkaterület beállítása</span><span class="sxs-lookup"><span data-stu-id="6638b-112">Set up Azure Machine Learning workspace</span></span>

1. <span data-ttu-id="6638b-113">További tudnivalókért lásd: [Azure Machine Learning munkaterület létrehozása](https://docs.microsoft.com/azure/machine-learning/concept-workspace#-create-a-workspace) a munkaterület létrehozásához használt különböző beállításokhoz.</span><span class="sxs-lookup"><span data-stu-id="6638b-113">See [create a Azure Machine Learning workspace](https://docs.microsoft.com/azure/machine-learning/concept-workspace#-create-a-workspace) for different options to create the workspace.</span></span> <span data-ttu-id="6638b-114">A legjobb teljesítmény érdekében hozza létre a munkaterületet egy Azure-régióban, amely földrajzilag legközelebb áll a Customer Insights környezetéhez.</span><span class="sxs-lookup"><span data-stu-id="6638b-114">For best performance, create the workspace in an Azure region that is geographically closest to your Customer Insights environment.</span></span>

1. <span data-ttu-id="6638b-115">Nyissa meg a munkaterületet az [Azure Machine Learning Studio](https://ml.azure.com/) segítségével.</span><span class="sxs-lookup"><span data-stu-id="6638b-115">Access your workspace through the [Azure Machine Learning Studio](https://ml.azure.com/).</span></span> <span data-ttu-id="6638b-116">A munkaterületre többféle [módon léphet kapcsolatba](https://docs.microsoft.com/azure/machine-learning/concept-workspace#tools-for-workspace-interaction).</span><span class="sxs-lookup"><span data-stu-id="6638b-116">There are several [ways to interact](https://docs.microsoft.com/azure/machine-learning/concept-workspace#tools-for-workspace-interaction) with your workspace.</span></span>

## <a name="work-with-azure-machine-learning-designer"></a><span data-ttu-id="6638b-117">Az Azure Machine Learning tervező használata</span><span class="sxs-lookup"><span data-stu-id="6638b-117">Work with Azure Machine Learning designer</span></span>

<span data-ttu-id="6638b-118">Az Azure Machine Learning tervező vizuális vásznat biztosít, ahol húzással mozgathat adathalmazokat és modulokat, hasonlóképp a Machine Learning Studio (klasszikus) verzióhoz.</span><span class="sxs-lookup"><span data-stu-id="6638b-118">Azure Machine Learning designer provides a visual canvas where you can drag and drop datasets and modules, similar to Machine Learning Studio (classic).</span></span> <span data-ttu-id="6638b-119">A tervező által létrehozott kötegelt csővezetékek a Customer Insights szolgáltatásba integrálhatók, ha ennek megfelelően vannak konfigurálva.</span><span class="sxs-lookup"><span data-stu-id="6638b-119">A batch pipeline created from the designer can be integrated into Customer Insights if they are configured accordingly.</span></span> 
   
## <a name="working-with-azure-machine-learning-sdk"></a><span data-ttu-id="6638b-120">Az Azure Machine Learning SDK használata</span><span class="sxs-lookup"><span data-stu-id="6638b-120">Working with Azure Machine Learning SDK</span></span>

<span data-ttu-id="6638b-121">Az adatszakértők és az AI-fejlesztők az [Azure Machine Learning SDK-t](https://docs.microsoft.com/python/api/overview/azure/ml/?view=azure-ml-py&preserve-view=true) használják a gépi tanulási munkafolyamatok létrehozásához.</span><span class="sxs-lookup"><span data-stu-id="6638b-121">Data scientists and AI developers use the [Azure Machine Learning SDK](https://docs.microsoft.com/python/api/overview/azure/ml/?view=azure-ml-py&preserve-view=true) to build machine learning workflows.</span></span> <span data-ttu-id="6638b-122">Jelenleg az SDK segítségével betanított modellek nem integrálhatók közvetlenül a Customer Insights szolgáltatáshoz.</span><span class="sxs-lookup"><span data-stu-id="6638b-122">Currently, models trained using the SDK can't be integrated directly with Customer Insights.</span></span> <span data-ttu-id="6638b-123">A Customer Insights integrációhoz az adott modellt elfoglaló kötegelt származtatási folyamata.</span><span class="sxs-lookup"><span data-stu-id="6638b-123">A batch inference pipeline that consumes that model is required for integration with Customer Insights.</span></span>

## <a name="batch-pipeline-requirements-to-integrate-with-customer-insights"></a><span data-ttu-id="6638b-124">A kötegelt folyamat követelményei a Customer Insights való integrálásra</span><span class="sxs-lookup"><span data-stu-id="6638b-124">Batch pipeline requirements to integrate with Customer Insights</span></span>

### <a name="dataset-configuration"></a><span data-ttu-id="6638b-125">Adathalmaz konfigurálása</span><span class="sxs-lookup"><span data-stu-id="6638b-125">Dataset Configuration</span></span>

<span data-ttu-id="6638b-126">Létre kell hoznia az adathalmazokat ahhoz, hogy az entitások adatait a Customer Insights alapján a rendszer áttekintse a gyártási folyamatba.</span><span class="sxs-lookup"><span data-stu-id="6638b-126">You need to create datasets to use entity data from Customer Insights to your batch inference pipeline.</span></span> <span data-ttu-id="6638b-127">Ezeket az adathalmazokat regisztrálni kell a munkaterületen.</span><span class="sxs-lookup"><span data-stu-id="6638b-127">These datasets need to be registered in the workspace.</span></span> <span data-ttu-id="6638b-128">Jelenleg [a táblázatos adathalmazokat](https://docs.microsoft.com/azure/machine-learning/how-to-create-register-datasets#tabulardataset) csak .csv formátumban támogatjuk.</span><span class="sxs-lookup"><span data-stu-id="6638b-128">Currently, we only support [tabular datasets](https://docs.microsoft.com/azure/machine-learning/how-to-create-register-datasets#tabulardataset) in .csv format.</span></span> <span data-ttu-id="6638b-129">Az entitásadatoknak megfelelő adathalmazokat a folyamatparaméterként kell megadni.</span><span class="sxs-lookup"><span data-stu-id="6638b-129">The datasets that correspond to entity data need to be parameterized as a pipeline parameter.</span></span>
   
* <span data-ttu-id="6638b-130">Az adathalmaz paraméterei a tervezőben</span><span class="sxs-lookup"><span data-stu-id="6638b-130">Dataset parameters in Designer</span></span>
   
     <span data-ttu-id="6638b-131">Nyissa meg a tervezőben az **oszlopok kiválasztása az adathalmazban**, és válassza a **beállítás folyamatparaméterként**, ahol megadja a paraméter nevét.</span><span class="sxs-lookup"><span data-stu-id="6638b-131">In the designer, open **Select Columns in Dataset** and select **Set as pipeline parameter** where you provide a name for the parameter.</span></span>

     > [!div class="mx-imgBorder"]
     > <span data-ttu-id="6638b-132">![Az adathalmaz paraméterezései a tervezőben](media/intelligence-designer-dataset-parameters.png "Az adathalmaz paraméterezései a tervezőben")</span><span class="sxs-lookup"><span data-stu-id="6638b-132">![Dataset parameterization in designer](media/intelligence-designer-dataset-parameters.png "Dataset parameterization in designer")</span></span>
   
* <span data-ttu-id="6638b-133">DataSet paraméter az SDK (Python) alkalmazásban</span><span class="sxs-lookup"><span data-stu-id="6638b-133">Dataset parameter in SDK (Python)</span></span>
   
   ```python
   HotelStayActivity_dataset = Dataset.get_by_name(ws, name='Hotel Stay Activity Data')
   HotelStayActivity_pipeline_param = PipelineParameter(name="HotelStayActivity_pipeline_param", default_value=HotelStayActivity_dataset)
   HotelStayActivity_ds_consumption = DatasetConsumptionConfig("HotelStayActivity_dataset", HotelStayActivity_pipeline_param)
   ```

### <a name="batch-inference-pipeline"></a><span data-ttu-id="6638b-134">A kötegelt származtatott folyamatok</span><span class="sxs-lookup"><span data-stu-id="6638b-134">Batch inference pipeline</span></span>
  
* <span data-ttu-id="6638b-135">A tervezőben egy képzési folyamat használható a következtetések közti folyamat létrehozására vagy frissítésére.</span><span class="sxs-lookup"><span data-stu-id="6638b-135">In the designer, a training pipeline can be used to create or update an inference pipeline.</span></span> <span data-ttu-id="6638b-136">Jelenleg a rendszer csak a tételekre vonatkozó következtetéseket támogatja.</span><span class="sxs-lookup"><span data-stu-id="6638b-136">Currently, only batch inference pipelines are supported.</span></span>

* <span data-ttu-id="6638b-137">A SDK segítségével közzéteheti a folyamatot egy végpontra.</span><span class="sxs-lookup"><span data-stu-id="6638b-137">Using the SDK, you can publish the pipeline to an endpoint.</span></span> <span data-ttu-id="6638b-138">A Customer Insights jelenleg a Machine Learning munkaterület kötegelt folyamatvégpontjában levő alapértelmezett folyamattal integrálható.</span><span class="sxs-lookup"><span data-stu-id="6638b-138">Currently, Customer Insights integrates with the default pipeline in a batch pipeline endpoint in the Machine Learning workspace.</span></span>
   
   ```python
   published_pipeline = pipeline.publish(name="ChurnInferencePipeline", description="Published Churn Inference pipeline")
   pipeline_endpoint = PipelineEndpoint.get(workspace=ws, name="ChurnPipelineEndpoint") 
   pipeline_endpoint.add_default(pipeline=published_pipeline)
   ```

### <a name="import-pipeline-data-into-customer-insights"></a><span data-ttu-id="6638b-139">Folyamatadatok importálása a Customer Insightsba</span><span class="sxs-lookup"><span data-stu-id="6638b-139">Import pipeline data into Customer Insights</span></span>

* <span data-ttu-id="6638b-140">A tervező biztosítja az [exportálási adatmodult](https://docs.microsoft.com/azure/machine-learning/algorithm-module-reference/export-data), amely lehetővé teszi a folyamat kimenetének exportálását az Azure Storage rendszerbe.</span><span class="sxs-lookup"><span data-stu-id="6638b-140">The designer provides the [Export Data module](https://docs.microsoft.com/azure/machine-learning/algorithm-module-reference/export-data) that allows the output of a pipeline to be exported to Azure storage.</span></span> <span data-ttu-id="6638b-141">Jelenleg a modulnak az **Azure Blob Storage** adattár típust kell használnia, és paraméterré kell alakítani az **adattár** és a relatív **elérési út** elemeket.</span><span class="sxs-lookup"><span data-stu-id="6638b-141">Currently, the module must use the datastore type **Azure Blob Storage** and parameterize the **Datastore** and relative **Path**.</span></span> <span data-ttu-id="6638b-142">A Customer Insights mindkét paramétert felülbírálja a folyamat végrehajtása során a termékhez elérhető adattár és elérési út értékével.</span><span class="sxs-lookup"><span data-stu-id="6638b-142">Customer Insights overrides both these parameters during pipeline execution with a datastore and path that is accessible to the product.</span></span>
   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="6638b-143">![Adatmodell-konfiguráció exportálása](media/intelligence-designer-importdata.png "Adatmodell-konfiguráció exportálása")</span><span class="sxs-lookup"><span data-stu-id="6638b-143">![Export Data Module Configuration](media/intelligence-designer-importdata.png "Export Data Module Configuration")</span></span>
   
* <span data-ttu-id="6638b-144">Amikor kódot használ a származtatott kimenet írásakor, feltöltheti a kimenetet a megfelelő elérési útra a munkaterületen található *regisztrált adattáron* belül.</span><span class="sxs-lookup"><span data-stu-id="6638b-144">When writing the inference output using code, you can upload the output to the a path within a *registered datastore* in the workspace.</span></span> <span data-ttu-id="6638b-145">Ha az elérési út és az adattár paraméterei a folyamatban vannak, a Customer Insights képes olvasni és importálni a származtatott kimenetet.</span><span class="sxs-lookup"><span data-stu-id="6638b-145">If the path and datastore are parameterized in the pipeline, Customer insights will be able to read and import the inference output.</span></span> <span data-ttu-id="6638b-146">Jelenleg egyetlen táblázatos kimenet támogatott CSV formátumban.</span><span class="sxs-lookup"><span data-stu-id="6638b-146">Currently, a single tabular output in csv format is supported.</span></span> <span data-ttu-id="6638b-147">Az elérési útnak tartalmaznia kell a könyvtárat és a fájlnevet.</span><span class="sxs-lookup"><span data-stu-id="6638b-147">The path must include the directory and filename.</span></span>

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


[!INCLUDE[footer-include](../includes/footer-banner.md)]