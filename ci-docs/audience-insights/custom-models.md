---
title: Egyéni gépi tanulás modellek | Microsoft Docs
description: Munka az Azure Machine Learning megoldásból származó modellekkel a Dynamics 365 Customer Insights alkalmazásban.
ms.date: 11/19/2020
ms.reviewer: zacook
ms.service: dynamics-365-ai
ms.topic: article
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: ef248086b30b870359970529a7bfb37792be62d5
ms.sourcegitcommit: a9b2cf598f256d07a48bba8617347ee90024a1dd
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/03/2020
ms.locfileid: "4668906"
---
# <a name="custom-machine-learning-models"></a><span data-ttu-id="4e44e-103">Egyéni gépi tanulás modellek</span><span class="sxs-lookup"><span data-stu-id="4e44e-103">Custom machine learning models</span></span>

<span data-ttu-id="4e44e-104">Az **Információk** > **Egyéni modellek** ponttal kezelheti a munkafolyamatokat az Azure Machine Learning-modellek alapján.</span><span class="sxs-lookup"><span data-stu-id="4e44e-104">**Intelligence** > **Custom models** lets you manage workflows based on Azure Machine Learning models.</span></span> <span data-ttu-id="4e44e-105">A munkafolyamatok segítségével kiválaszthatja azokat az adatokat, amelyekből betekintést szeretne létrehozni, és leképezi az eredményeket az egyesített ügyféladatokat.</span><span class="sxs-lookup"><span data-stu-id="4e44e-105">Workflows help you choose the data you want to generate insights from and map the results to your unified customer data.</span></span> <span data-ttu-id="4e44e-106">Az egyéni ML modellek készítésével kapcsolatos további információkért lásd: [Az Azure Machine Learning-alapú modellek használata](azure-machine-learning-experiments.md).</span><span class="sxs-lookup"><span data-stu-id="4e44e-106">For more information about building custom ML models, see [Use Azure Machine Learning-based models](azure-machine-learning-experiments.md).</span></span>

## <a name="responsible-ai"></a><span data-ttu-id="4e44e-107">Felelős AI</span><span class="sxs-lookup"><span data-stu-id="4e44e-107">Responsible AI</span></span>

<span data-ttu-id="4e44e-108">Az előrejelzések lehetőséget nyújtanak a jobb ügyfelekkel kapcsolatos tapasztalatok létrehozására, az üzleti lehetőségek fejlesztésére és a bevételi források javítására.</span><span class="sxs-lookup"><span data-stu-id="4e44e-108">Predictions offer capabilities to create better customer experiences, improve business capabilities, and revenue streams.</span></span> <span data-ttu-id="4e44e-109">Kifejezetten ajánljuk, hogy a előrejelzés értékét egyenlítsék ki annak hatásával és az esetleges torzításokkal szemben etikus módon.</span><span class="sxs-lookup"><span data-stu-id="4e44e-109">We strongly recommend you balance the value of your prediction against the impact it has and biases that may be introduced in an ethical manner.</span></span> <span data-ttu-id="4e44e-110">Ismerje meg, hogy a Microsoft hogyan [kezeli a felelős AI-t ](https://www.microsoft.com/ai/responsible-ai?activetab=pivot1%3aprimaryr6).</span><span class="sxs-lookup"><span data-stu-id="4e44e-110">Learn more about how Microsoft is [addressing Responsible AI](https://www.microsoft.com/ai/responsible-ai?activetab=pivot1%3aprimaryr6).</span></span> <span data-ttu-id="4e44e-111">Megtudhatja, hogyan használhatók [a felelős gépi tanulás technikái és folyamatai](https://docs.microsoft.com/azure/machine-learning/concept-responsible-ml), amelyek az Azure Machine Learningre jellemzőek.</span><span class="sxs-lookup"><span data-stu-id="4e44e-111">You can also learn about [techniques and processes for responsible machine learning](https://docs.microsoft.com/azure/machine-learning/concept-responsible-ml) specific to Azure Machine Learning.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4e44e-112">Előfeltételek</span><span class="sxs-lookup"><span data-stu-id="4e44e-112">Prerequisites</span></span>

- <span data-ttu-id="4e44e-113">Jelenleg ez a szolgáltatás támogatja a [Machine Learning Studio (klasszikus)](https://studio.azureml.net) verzióján és az [Azure Machine Learning kötegelt folyamaton](https://docs.microsoft.com/azure/machine-learning/concept-ml-pipelines) keresztül közzétett webszolgáltatásokat .</span><span class="sxs-lookup"><span data-stu-id="4e44e-113">Currently, this feature supports web services published through [Machine Learning Studio (classic)](https://studio.azureml.net) and [Azure Machine Learning batch pipelines](https://docs.microsoft.com/azure/machine-learning/concept-ml-pipelines).</span></span>

- <span data-ttu-id="4e44e-114">A funkció használatához az Azure Studio-példányhoz társított Azure Data Lake Gen2-fiókra van szükség.</span><span class="sxs-lookup"><span data-stu-id="4e44e-114">You need an Azure Data Lake Gen2 storage account associated with your Azure Studio instance to use this feature.</span></span> <span data-ttu-id="4e44e-115">További információ: [Azure Data Lake Storage Gen2 tárfiók létrehozása](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-quickstart-create-account)</span><span class="sxs-lookup"><span data-stu-id="4e44e-115">For more information, see [Create an Azure Data Lake Storage Gen2 storage account](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-quickstart-create-account)</span></span>

## <a name="add-a-new-workflow"></a><span data-ttu-id="4e44e-116">Új munkafolyamat hozzáadása</span><span class="sxs-lookup"><span data-stu-id="4e44e-116">Add a new workflow</span></span>

1. <span data-ttu-id="4e44e-117">Nyissa meg a **Információk** > **Egyéni modellek** elemet, és válassza az **Új munkafolyamat** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="4e44e-117">Go to **Intelligence** > **Custom models** and select **New workflow**.</span></span>

1. <span data-ttu-id="4e44e-118">Adjon meg egy felismerhető nevet a **Név** mezőben az egyéni modellnek.</span><span class="sxs-lookup"><span data-stu-id="4e44e-118">Give your custom model a recognizable name in the **Name** field.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="4e44e-119">![Képernyőkép – az új munkafolyamat ablaktábla](media/new-workflowv2.png "Képernyőkép – az új munkafolyamat ablaktábla")</span><span class="sxs-lookup"><span data-stu-id="4e44e-119">![Screenshot of the New workflow pane](media/new-workflowv2.png "Screenshot of the New workflow pane")</span></span>

1. <span data-ttu-id="4e44e-120">Válassza ki azt a szervezetet, amely a webszolgáltatást tartalmazza a **Bérlő, amely tartalmazza a webszolgáltatást** pontban.</span><span class="sxs-lookup"><span data-stu-id="4e44e-120">Select the organization that contains the web service in **Tenant that contains your web service**.</span></span>

1. <span data-ttu-id="4e44e-121">Ha az Azure Machine Learning-előfizetése egy másik bérlőn belül van, mint a Customer Insights, akkor válassza a **bejelentkezés** lehetőséget a kijelölt szervezethez tartozó hitelesítő adatokkal.</span><span class="sxs-lookup"><span data-stu-id="4e44e-121">If your Azure Machine Learning subscription is in a different tenant than Customer Insights, select **Sign in** with your credentials for the selected organization.</span></span>

1. <span data-ttu-id="4e44e-122">Jelölje ki a webszolgáltatáshoz társított **Munkaterületeket**.</span><span class="sxs-lookup"><span data-stu-id="4e44e-122">Select the **Workspaces** associated with your web service.</span></span> <span data-ttu-id="4e44e-123">Két szakasz van felsorolva, egy az Azure Machine Learning v1 (Machine Learning Studio (klasszikus)) és az Azure Machine Learning v2 (Azure Machine Learning).</span><span class="sxs-lookup"><span data-stu-id="4e44e-123">There are two sections listed, one for Azure Machine Learning v1 (Machine Learning Studio (classic)) and Azure Machine Learning v2 (Azure Machine Learning).</span></span> <span data-ttu-id="4e44e-124">Ha nem tudja biztosan, hogy melyik munkaterület a megfelelő a Machine Learning Studio (klasszikus) webszolgáltatáshoz, válassza a **Bármelyik** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="4e44e-124">If you're not sure which workspace is the right one for your Machine Learning Studio (classic) web service, select **Any**.</span></span>

1. <span data-ttu-id="4e44e-125">Válassza ki a Machine Learning Studio (klasszikus) webszolgáltatást vagy Azure Machine Learning folyamat lehetőséget a **Modellt tartalmazó webszolgáltatás** legördülő menüben.</span><span class="sxs-lookup"><span data-stu-id="4e44e-125">Choose the Machine Learning Studio (classic) web service or Azure Machine Learning pipeline in the **Web service that contains your model** dropdown.</span></span> <span data-ttu-id="4e44e-126">Azután válassza a **Következő** elemet.</span><span class="sxs-lookup"><span data-stu-id="4e44e-126">Then, select **Next**.</span></span>
   - <span data-ttu-id="4e44e-127">További információ a [webszolgáltatás közzétételéről a Machine Learning Studio (classic) szolgáltatásban](https://docs.microsoft.com/azure/machine-learning/studio/deploy-a-machine-learning-web-service#deploy-it-as-a-new-web-service)</span><span class="sxs-lookup"><span data-stu-id="4e44e-127">Learn more about [publishing a web service in Machine Learning Studio (classic)](https://docs.microsoft.com/azure/machine-learning/studio/deploy-a-machine-learning-web-service#deploy-it-as-a-new-web-service)</span></span>
   - <span data-ttu-id="4e44e-128">További információ a [folyamatok közzétételéről az Azure Machine Learning a tervezővel](https://docs.microsoft.com/azure/machine-learning/concept-ml-pipelines#building-pipelines-with-the-designer) vagy az [SDK-val](https://docs.microsoft.com/azure/machine-learning/concept-ml-pipelines#building-pipelines-with-the-python-sdk).</span><span class="sxs-lookup"><span data-stu-id="4e44e-128">Learn more about [publishing a pipeline in Azure Machine Learning using the designer](https://docs.microsoft.com/azure/machine-learning/concept-ml-pipelines#building-pipelines-with-the-designer) or [SDK](https://docs.microsoft.com/azure/machine-learning/concept-ml-pipelines#building-pipelines-with-the-python-sdk).</span></span> 
     > [!NOTE]
     > <span data-ttu-id="4e44e-129">A folyamatokat a [folyamatvégpont](https://docs.microsoft.com/azure/machine-learning/how-to-run-batch-predictions-designer#submit-a-pipeline-run) alatt közzé kell tenni.</span><span class="sxs-lookup"><span data-stu-id="4e44e-129">Your pipeline must be published under a [pipeline endpoint](https://docs.microsoft.com/azure/machine-learning/how-to-run-batch-predictions-designer#submit-a-pipeline-run).</span></span>

1. <span data-ttu-id="4e44e-130">Minden egyes **Webszolgáltatás-bemenetnél** válassza ki a megfelelő **Entitást** a célközönség-információkból, és válassza a **Következő** elemet.</span><span class="sxs-lookup"><span data-stu-id="4e44e-130">For each **Web service input**, select the matching **Entity** from audience insights and select **Next**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="4e44e-131">![Munkafolyamat konfigurálása](media/intelligence-screen2-updated.png "Munkafolyamat konfigurálása")</span><span class="sxs-lookup"><span data-stu-id="4e44e-131">![Configure a workflow](media/intelligence-screen2-updated.png "Configure a workflow")</span></span>

1. <span data-ttu-id="4e44e-132">Állítsa be a következő tulajdonságokat a **Modell kimeneti paraméterek** lépésében:</span><span class="sxs-lookup"><span data-stu-id="4e44e-132">In the **Model Output Parameters** step, set the following properties:</span></span>
   - <span data-ttu-id="4e44e-133">Machine Learning Studio (klasszikus)</span><span class="sxs-lookup"><span data-stu-id="4e44e-133">Machine Learning Studio (classic)</span></span>
      1. <span data-ttu-id="4e44e-134">Adja meg a kimeneti **Entitás nevét**, amelyet a webszolgáltatás kimenetének eredményére szeretne beáramlani.</span><span class="sxs-lookup"><span data-stu-id="4e44e-134">Enter the output **Entity name** you want web service output results to flow into.</span></span>
   - <span data-ttu-id="4e44e-135">Azure Machine Learning</span><span class="sxs-lookup"><span data-stu-id="4e44e-135">Azure Machine Learning</span></span>
      1. <span data-ttu-id="4e44e-136">Adja meg a kimeneti **Entitás nevét**, amelyet a folyamat kimenetének eredményére szeretne beáramlani.</span><span class="sxs-lookup"><span data-stu-id="4e44e-136">Enter the output **Entity name** you want pipeline output results to flow into.</span></span>
      1. <span data-ttu-id="4e44e-137">Válassza ki a **kimeneti adattár paraméter nevét** a kötegfolyamathoz a legördülő listából.</span><span class="sxs-lookup"><span data-stu-id="4e44e-137">Select the **Output data store parameter name** of your batch pipeline from the dropdown.</span></span>
      1. <span data-ttu-id="4e44e-138">Válassza ki a **Kimeneti útvonal paraméter nevét** a kötegfolyamathoz a legördülő listából.</span><span class="sxs-lookup"><span data-stu-id="4e44e-138">Select the **Output Path parameter name** of your batch pipeline from the dropdown.</span></span>
      
      > [!div class="mx-imgBorder"]
      > <span data-ttu-id="4e44e-139">![A modell kimenet paraméter panele](media/intelligence-screen3-outputparameters.png "A modell kimenet paraméter panele")</span><span class="sxs-lookup"><span data-stu-id="4e44e-139">![Model Output Parameter Pane](media/intelligence-screen3-outputparameters.png "Model Output Parameter Pane")</span></span>

1. <span data-ttu-id="4e44e-140">Válassza ki a megfelelő attribútumot az **Ügyfél-azonosító az eredményekben** legördülő listából, amely beazonosítja az ügyfeleket, és válassza a **Mentés** elemet.</span><span class="sxs-lookup"><span data-stu-id="4e44e-140">Select the matching attribute from the **Customer ID in results** drop-down list that identifies customers and select **Save**.</span></span>
   
   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="4e44e-141">![Eredmények összekapcsolása az Ügyfél adatpanelhlel](media/intelligence-screen4-relatetocustomer.png "Eredmények összekapcsolása az Ügyfél adatpanelhlel")</span><span class="sxs-lookup"><span data-stu-id="4e44e-141">![Relate results to Customer data pane](media/intelligence-screen4-relatetocustomer.png "Relate results to Customer data pane")</span></span>

1. <span data-ttu-id="4e44e-142">Megjelenik a **Munkafolyamat mentve** képernyő a munkafolyamat részleteivel.</span><span class="sxs-lookup"><span data-stu-id="4e44e-142">You'll see the **Workflow Saved** screen with details about the workflow.</span></span>    
   <span data-ttu-id="4e44e-143">Ha az Azure Machine Learning folyamathoz munkafolyamatot konfigurált, a célközönség-információk hozzákapcsolja a munkaterülethez, amely a folyamatot tartalmazza.</span><span class="sxs-lookup"><span data-stu-id="4e44e-143">If you configured a workflow for an Azure Machine Learning pipeline, audience insights will attach to the workspace that contains the pipeline.</span></span> <span data-ttu-id="4e44e-144">Célközönség-információk kap egy **Közreműködő** szerepkörrel az Azure workspace-ban.</span><span class="sxs-lookup"><span data-stu-id="4e44e-144">Audience insights will get a **Contributor** role on the Azure workspace.</span></span>

1. <span data-ttu-id="4e44e-145">Válassza a **Kész** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="4e44e-145">Select **Done**.</span></span>

1. <span data-ttu-id="4e44e-146">Ezután a munkafolyamatot az **egyéni modellek** oldalról futtathatja.</span><span class="sxs-lookup"><span data-stu-id="4e44e-146">You can now run the workflow from the **Custom Models** page.</span></span>

## <a name="edit-a-workflow"></a><span data-ttu-id="4e44e-147">Egy munkafolyamat szerkesztése</span><span class="sxs-lookup"><span data-stu-id="4e44e-147">Edit a workflow</span></span>

1. <span data-ttu-id="4e44e-148">Az **egyéni modellek** lapon jelölje ki a függőleges három pontot a **Műveletek** oszlopban a korábban létrehozott munkafolyamat mellett, és válassza a **Szerkesztés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="4e44e-148">On the **Custom Models** page, select the vertical ellipsis in the **Actions** column next to a workflow you've previously created and select **Edit**.</span></span>

1. <span data-ttu-id="4e44e-149">A munkafolyamat felismerhető nevét a **megjelenítendő név** mezőben frissítheti, de a konfigurált webszolgáltatás vagy folyamat nem módosítható.</span><span class="sxs-lookup"><span data-stu-id="4e44e-149">You can update your workflow's recognizable name in the **Display name** field, but you can't change the configured web service or pipeline.</span></span> <span data-ttu-id="4e44e-150">Válassza a **Következő** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="4e44e-150">Select **Next**.</span></span>

1. <span data-ttu-id="4e44e-151">Minden egyes **Webszolgáltatás-bemenetnél** frissítheti a megfelelő **Entitást** a célközönség-információkból, és válassza a Következő elemet.</span><span class="sxs-lookup"><span data-stu-id="4e44e-151">For each **Web service input**, you can update the matching **Entity** from audience insights.</span></span> <span data-ttu-id="4e44e-152">Azután válassza a **Következő** elemet.</span><span class="sxs-lookup"><span data-stu-id="4e44e-152">Then, select **Next**.</span></span>

1. <span data-ttu-id="4e44e-153">Állítsa be a következő tulajdonságokat a **Modell kimeneti paraméterek** lépésében:</span><span class="sxs-lookup"><span data-stu-id="4e44e-153">In the **Model Output Parameters** step, set the following properties:</span></span>
   - <span data-ttu-id="4e44e-154">Machine Learning Studio (klasszikus)</span><span class="sxs-lookup"><span data-stu-id="4e44e-154">Machine Learning Studio (classic)</span></span>
      1. <span data-ttu-id="4e44e-155">Adja meg a kimeneti **Entitás nevét**, amelyet a webszolgáltatás kimenetének eredményére szeretne beáramlani.</span><span class="sxs-lookup"><span data-stu-id="4e44e-155">Enter the output **Entity name** you want web service output results to flow into.</span></span>
   - <span data-ttu-id="4e44e-156">Azure Machine Learning</span><span class="sxs-lookup"><span data-stu-id="4e44e-156">Azure Machine Learning</span></span>
      1. <span data-ttu-id="4e44e-157">Adja meg a kimeneti **Entitás nevét**, amelyet a folyamat kimenetének eredményére szeretne beáramlani.</span><span class="sxs-lookup"><span data-stu-id="4e44e-157">Enter the output **Entity name** you want pipeline output results to flow into.</span></span>
      1. <span data-ttu-id="4e44e-158">Válassza ki a **kimeneti adattár paraméter nevét** a tesztelési folyamathoz.</span><span class="sxs-lookup"><span data-stu-id="4e44e-158">Select the **Output data store parameter name** for your test pipeline.</span></span>
      1. <span data-ttu-id="4e44e-159">Válassza ki a **kimeneti útvonal paraméter nevét** a tesztelési folyamathoz.</span><span class="sxs-lookup"><span data-stu-id="4e44e-159">Select the **Output Path parameter name** for your test pipeline.</span></span>

1. <span data-ttu-id="4e44e-160">Válassza ki a megfelelő attribútumot az **Ügyfél-azonosító az eredményekben** legördülő listából, amely beazonosítja az ügyfeleket, és válassza a **Mentés** elemet.</span><span class="sxs-lookup"><span data-stu-id="4e44e-160">Select the matching attribute from the **Customer ID in results** drop-down list that identifies customers and select **Save**.</span></span>
   <span data-ttu-id="4e44e-161">Ki kell választania egy attribútumot a származtatott kimenetből az ügyfél entitás ügyfél-azonosító oszlopához hasonló értékekkel.</span><span class="sxs-lookup"><span data-stu-id="4e44e-161">You need to choose an attribute from the inference output with values similar to the Customer ID column of the Customer entity.</span></span> <span data-ttu-id="4e44e-162">Ha nincs ilyen oszlop az adathalmazban, válasszon egy attribútumot, amely egyedileg azonosítja a sort.</span><span class="sxs-lookup"><span data-stu-id="4e44e-162">If don't have such a column in your data set, choose an attribute that uniquely identifies the row.</span></span>

## <a name="run-a-workflow"></a><span data-ttu-id="4e44e-163">Munkafolyamat futtatása</span><span class="sxs-lookup"><span data-stu-id="4e44e-163">Run a workflow</span></span>

1. <span data-ttu-id="4e44e-164">Az **Egyéni modellek** lapon jelölje ki a függőleges három pontot a **Műveletek** oszlopban a korábban létrehozott munkafolyamat mellett.</span><span class="sxs-lookup"><span data-stu-id="4e44e-164">On the **Custom Models** page, select the vertical ellipsis in the **Actions** column next to a workflow you've previously created.</span></span>

1. <span data-ttu-id="4e44e-165">Válassza a **Futtatás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="4e44e-165">Select **Run**.</span></span>

<span data-ttu-id="4e44e-166">A munkafolyamat minden ütemezett frissítéssel együtt automatikusan lefut.</span><span class="sxs-lookup"><span data-stu-id="4e44e-166">Your workflow also runs automatically with every scheduled refresh.</span></span> <span data-ttu-id="4e44e-167">További információk az [ütemezett frissítések beállításáról](system.md#schedule-tab).</span><span class="sxs-lookup"><span data-stu-id="4e44e-167">Learn more about [setting up scheduled refreshes](system.md#schedule-tab).</span></span>

## <a name="delete-a-workflow"></a><span data-ttu-id="4e44e-168">Egy munkafolyamat törlése</span><span class="sxs-lookup"><span data-stu-id="4e44e-168">Delete a workflow</span></span>

1. <span data-ttu-id="4e44e-169">Az **Egyéni modellek** lapon jelölje ki a függőleges három pontot a **Műveletek** oszlopban a korábban létrehozott munkafolyamat mellett.</span><span class="sxs-lookup"><span data-stu-id="4e44e-169">On the **Custom Models** page, select the vertical ellipsis in the **Actions** column next to a workflow you've previously created.</span></span>

1. <span data-ttu-id="4e44e-170">Válassza a **Törlés** lehetőséget, és hagyja jóvá a törlést.</span><span class="sxs-lookup"><span data-stu-id="4e44e-170">Select **Delete** and confirm your deletion.</span></span>

<span data-ttu-id="4e44e-171">A munkafolyamat törölve lesz.</span><span class="sxs-lookup"><span data-stu-id="4e44e-171">Your workflow will be deleted.</span></span> <span data-ttu-id="4e44e-172">A munkafolyamat létrehozásakor létrehozott [entitás](entities.md) továbbra is megmarad, és az **Entitások** lapról tekinthető meg.</span><span class="sxs-lookup"><span data-stu-id="4e44e-172">The [entity](entities.md) that was created when you created the workflow persists, and can be viewed from the **Entities** page.</span></span>
