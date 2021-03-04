---
title: Common Data Model-adatok összekapcsolása egy Azure Data Lake-fiókkal
description: Common Data Model-adatok használata Azure Data Lake Storage segítségével.
ms.date: 05/29/2020
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: m-hartmann
ms.author: mhart
ms.reviewer: adkuppa
manager: shellyha
ms.openlocfilehash: 247e4d9c47ff2373065ebf3c6d554323e45a120b
ms.sourcegitcommit: 139548f8a2d0f24d54c4a6c404a743eeeb8ef8e0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/15/2021
ms.locfileid: "5267863"
---
# <a name="connect-to-a-common-data-model-folder-using-an-azure-data-lake-account"></a><span data-ttu-id="f6cd8-103">Kapcsolódás a Common Data Model-mappához Azure Data Lake fiók használatával</span><span class="sxs-lookup"><span data-stu-id="f6cd8-103">Connect to a Common Data Model folder using an Azure Data Lake account</span></span>

<span data-ttu-id="f6cd8-104">A cikkből megtudhatja, hogyan lehet a Common Data Model mappából adatokat betölteni az Azure Data Lake Storage Gen2-fiók segítségével.</span><span class="sxs-lookup"><span data-stu-id="f6cd8-104">This article provides information on how to ingest data from a Common Data Model folder using your Azure Data Lake Storage Gen2 account.</span></span>

## <a name="important-considerations"></a><span data-ttu-id="f6cd8-105">Fontos tényezők</span><span class="sxs-lookup"><span data-stu-id="f6cd8-105">Important considerations</span></span>

- <span data-ttu-id="f6cd8-106">Az Azure Data Lake-ben szereplő adatoknak követniük kell a Common Data Model standardot.</span><span class="sxs-lookup"><span data-stu-id="f6cd8-106">Data in your Azure Data Lake needs to follow the Common Data Model standard.</span></span> <span data-ttu-id="f6cd8-107">A többi formátum jelenleg nem támogatott.</span><span class="sxs-lookup"><span data-stu-id="f6cd8-107">Other formats aren't supported at the moment.</span></span>

- <span data-ttu-id="f6cd8-108">Az adatbetöltés kizárólag csak az Azure Data Lake *Gen2* tárfiókokat támogatja.</span><span class="sxs-lookup"><span data-stu-id="f6cd8-108">Data ingestion supports Azure Data Lake *Gen2* storage accounts exclusively.</span></span> <span data-ttu-id="f6cd8-109">Az Azure Data Lake Gen1 tárfiókok nem használhatók adatok betöltésére.</span><span class="sxs-lookup"><span data-stu-id="f6cd8-109">You can't use Azure Data Lake Gen1 storage accounts to ingest data.</span></span>

- <span data-ttu-id="f6cd8-110">Az Azure-egyszerű szolgáltatásnév használatával történő hitelesítéshez ügyeljen arra, hogy az a bérlőn legyen konfigurálva.</span><span class="sxs-lookup"><span data-stu-id="f6cd8-110">To authenticate with an Azure service principal, make sure it's configured in your tenant.</span></span> <span data-ttu-id="f6cd8-111">További információkért lásd: [Célközönség-információk összekapcsolása az Azure Data Lake Storage Gen2 fiókjához az Azure egyszerű szolgáltatásnévvel](connect-service-principal.md).</span><span class="sxs-lookup"><span data-stu-id="f6cd8-111">For more information, see [Connect audience insights to an Azure Data Lake Storage Gen2 account with an Azure service principal](connect-service-principal.md).</span></span>

- <span data-ttu-id="f6cd8-112">Az Azure Data Lake, amelyhez kapcsolódni szeretne, és be szeretné tölteni az adatokat, ugyanabban az Azure régióban kell lennie, mint a Dynamics 365 Customer Insights-környezet.</span><span class="sxs-lookup"><span data-stu-id="f6cd8-112">The Azure Data Lake you want to connect and ingest data from have to be in the same Azure region as the Dynamics 365 Customer Insights environment.</span></span> <span data-ttu-id="f6cd8-113">A Common Data Model-mappába egy másik Azure-régióban található adattóból való kapcsolódás nem támogatott.</span><span class="sxs-lookup"><span data-stu-id="f6cd8-113">Connections to a Common Data Model folder from a data lake in a different Azure region is not supported.</span></span> <span data-ttu-id="f6cd8-114">A környezet Azure-régiójának megismeréséhez lépjen a **Rendszergazda** > **Rendszer** > **Névjegy** elemre a célközönség-információkban.</span><span class="sxs-lookup"><span data-stu-id="f6cd8-114">To know the Azure region of the environment, go to **Admin** > **System** > **About** in audience insights.</span></span>

- <span data-ttu-id="f6cd8-115">Az online szolgáltatásokban tárolt adatok más helyen is tárolhatók, mint ahol az adatok feldolgozása vagy tárolása történik a Dynamics 365 Customer Insights szolgáltatásban.</span><span class="sxs-lookup"><span data-stu-id="f6cd8-115">Data stored in online services, may be stored in a different location than where data is processed or stored in Dynamics 365 Customer Insights.</span></span><span data-ttu-id="f6cd8-116"> Az online szolgáltatásokban tárolt adatok importálásával vagy az ahhoz való kapcsolódással Ön elfogadja, hogy az adatok átvihetők és tárolhatók a Dynamics 365 Customer Insights alkalmazásban.  [Ismerje meg a Microsoft adatvédelmi központot](https://www.microsoft.com/trust-center)</span><span class="sxs-lookup"><span data-stu-id="f6cd8-116"> By importing or connecting to data stored in online services, you agree that data can be transferred to and stored with Dynamics 365 Customer Insights. [Learn more at the Microsoft Trust Center.](https://www.microsoft.com/trust-center)</span></span>

## <a name="connect-to-a-common-data-model-folder"></a><span data-ttu-id="f6cd8-117">Csatlakozás egy Common Data Model-mappához</span><span class="sxs-lookup"><span data-stu-id="f6cd8-117">Connect to a Common Data Model folder</span></span>

1. <span data-ttu-id="f6cd8-118">A célközönség információin belül nyissa meg a következőt **Adatok** > **Adatforrások**.</span><span class="sxs-lookup"><span data-stu-id="f6cd8-118">In audience insights, go to **Data** > **Data sources**.</span></span>

1. <span data-ttu-id="f6cd8-119">Válassza az **Adatforrás hozzáadása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="f6cd8-119">Select **Add data source**.</span></span>

1. <span data-ttu-id="f6cd8-120">Válassza a **Csatlakozás egy Common Data Model-mappához** lehetőséget , írja be az adatforrás **Nevét**, majd válassza a **Következő** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="f6cd8-120">Select **Connect to a Common Data Model folder**, enter a **Name** for the data source, and select **Next**.</span></span> <span data-ttu-id="f6cd8-121">Névvel kapcsolatos irányelvek:</span><span class="sxs-lookup"><span data-stu-id="f6cd8-121">Name guidelines:</span></span> 
   - <span data-ttu-id="f6cd8-122">Kezdje egy betűvel.</span><span class="sxs-lookup"><span data-stu-id="f6cd8-122">Start with a letter.</span></span>
   - <span data-ttu-id="f6cd8-123">Csak betűket és számokat használjon.</span><span class="sxs-lookup"><span data-stu-id="f6cd8-123">Use letters and numbers only.</span></span> <span data-ttu-id="f6cd8-124">Speciális karakterek és szóközök nem adhatók meg.</span><span class="sxs-lookup"><span data-stu-id="f6cd8-124">Special characters and spaces are not allowed.</span></span>
   - <span data-ttu-id="f6cd8-125">3–64 karakter használható.</span><span class="sxs-lookup"><span data-stu-id="f6cd8-125">Use between 3 and 64 characters.</span></span>

1. <span data-ttu-id="f6cd8-126">Választhat az erőforrás-alapú és az előfizetés-alapú hitelesítés használata között.</span><span class="sxs-lookup"><span data-stu-id="f6cd8-126">You can choose between using a resource-based option and a subscription-based option for authentication.</span></span> <span data-ttu-id="f6cd8-127">További információkért lásd: [Célközönség-információk összekapcsolása az Azure Data Lake Storage Gen2 fiókjához az Azure egyszerű szolgáltatásnévvel](connect-service-principal.md).</span><span class="sxs-lookup"><span data-stu-id="f6cd8-127">For more information, see [Connect audience insights to an Azure Data Lake Storage Gen2 account with an Azure service principal](connect-service-principal.md).</span></span> <span data-ttu-id="f6cd8-128">Adja meg a **Tároló** adatait, és válassza a **Következő** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="f6cd8-128">Enter the **Container** information and select **Next**.</span></span>
   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="f6cd8-129">![Párbeszédpanelen adja meg az új kapcsolat adatait az Azure Data Lake-hez](media/enter-new-storage-details.png)
   > </span><span class="sxs-lookup"><span data-stu-id="f6cd8-129">![Dialog box to enter new connection details for Azure Data Lake](media/enter-new-storage-details.png)
   > </span></span>[!NOTE]
<span data-ttu-id="f6cd8-130">Ahhoz, hogy a tárolóhoz vagy a fenti tárolókhoz kapcsolódhasson, és létre tudja hozni adatforrást a következő szerepkörök egyike szükséges:</span><span class="sxs-lookup"><span data-stu-id="f6cd8-130">You need one of the following roles either to the container or the storage account referred above to be able to connect to and create a data source:</span></span>
   >  - <span data-ttu-id="f6cd8-131">Storage Blob adatolvasó</span><span class="sxs-lookup"><span data-stu-id="f6cd8-131">Storage Blob Data Reader</span></span>
   >  - <span data-ttu-id="f6cd8-132">Storage Blob adattulajdonos</span><span class="sxs-lookup"><span data-stu-id="f6cd8-132">Storage Blob Data Owner</span></span>
   >  - <span data-ttu-id="f6cd8-133">Storage Blob adatközreműködő</span><span class="sxs-lookup"><span data-stu-id="f6cd8-133">Storage Blob Data Contributor</span></span>

1. <span data-ttu-id="f6cd8-134">A **Common Data Model-mappa kiválasztása** párbeszédpanelen válassza azt a manifest.json fájlt, amelyből adatokat szeretne importálni, majd válassza a **Következő** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="f6cd8-134">In the **Select a Common Data Model folder** dialog, select the model.json or manifest.json file to import data from, and select **Next**.</span></span>
   > [!NOTE]
   > <span data-ttu-id="f6cd8-135">A környezetben más adatforrással társított egyéb model.json vagy manifest.json fájlok nem jelennek meg a listában.</span><span class="sxs-lookup"><span data-stu-id="f6cd8-135">Any model.json or manifest.json file associated with another data source in the environment won't show in the list.</span></span>

1. <span data-ttu-id="f6cd8-136">A kiválasztott model.json vagy manifest.json fájlban a rendelkezésre álló entitások listája látható.</span><span class="sxs-lookup"><span data-stu-id="f6cd8-136">You'll get a list of available entities in the selected model.json or manifest.json file.</span></span> <span data-ttu-id="f6cd8-137">Áttekinthet és kiválaszthat rendelkezésre álló entitások listájából, és válassza a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="f6cd8-137">You can review and select from the list of available entities and select **Save**.</span></span> <span data-ttu-id="f6cd8-138">A rendszer az összes kiválasztott entitást betölti az új adatforrásból.</span><span class="sxs-lookup"><span data-stu-id="f6cd8-138">All of the selected entities will be ingested from the new data source.</span></span>
   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="f6cd8-139">![Párbeszédpanel, amely az entitások listáját jeleníti meg egy model.json fájlból](media/review-entities.png)</span><span class="sxs-lookup"><span data-stu-id="f6cd8-139">![Dialog box showing a list of entities from a model.json file](media/review-entities.png)</span></span>

8. <span data-ttu-id="f6cd8-140">Adja meg, hogy milyen adatentitásokat szeretne az adatprofil-készítés engedélyezéséhez, és válassza a **Mentést**.</span><span class="sxs-lookup"><span data-stu-id="f6cd8-140">Indicate which data entities you want to enable data profiling and select **Save**.</span></span> <span data-ttu-id="f6cd8-141">Az adatprofil-készítés lehetővé teszi az elemzések és egyéb lehetőségek használatát.</span><span class="sxs-lookup"><span data-stu-id="f6cd8-141">Data profiling enables analytics and other capabilities.</span></span> <span data-ttu-id="f6cd8-142">Kijelölheti a teljes entitást, amely az entitás összes attribútumát kijelöli, vagy kijelölhet bizonyos attribútumokat, amelyeket kiválasztott.</span><span class="sxs-lookup"><span data-stu-id="f6cd8-142">You can select the whole entity, which selects all attributes from the entity, or select certain attributes of your choice.</span></span> <span data-ttu-id="f6cd8-143">Alapértelmezés szerint egyetlen entitás sincs engedélyezve az adatok profilkészítéséhez.</span><span class="sxs-lookup"><span data-stu-id="f6cd8-143">By default, no entity is enabled for data profiling.</span></span>
   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="f6cd8-144">![Adatprofil-készítést megjelenítő párbeszédpanel](media/dataprofiling-entities.png)</span><span class="sxs-lookup"><span data-stu-id="f6cd8-144">![Dialog box showing a data profiling](media/dataprofiling-entities.png)</span></span>

9. <span data-ttu-id="f6cd8-145">A kiválasztott adatok mentése után megnyílik az **Adatforrások** lap.</span><span class="sxs-lookup"><span data-stu-id="f6cd8-145">After saving your selections, the **Data sources** page opens.</span></span> <span data-ttu-id="f6cd8-146">Ekkor a Common Data Model mappa kapcsolatot adatforrásként látja.</span><span class="sxs-lookup"><span data-stu-id="f6cd8-146">You should now see the Common Data Model folder connection as a data source.</span></span>

> [!NOTE]
> <span data-ttu-id="f6cd8-147">A model.json vagy manifest-json fájl csak egy-egy adatforráshoz társítható ugyanabban a környezetben.</span><span class="sxs-lookup"><span data-stu-id="f6cd8-147">A model.json file or manifest.json can only associate with one data source in the same environment.</span></span> <span data-ttu-id="f6cd8-148">Ugyanakkor ugyanez a model.json vagy manifest.json fájl több környezetben is használható adatforrásokhoz.</span><span class="sxs-lookup"><span data-stu-id="f6cd8-148">However, the same model.json or manifest.json file can be used for data sources in multiple environments.</span></span>

## <a name="edit-a-common-data-model-folder-data-source"></a><span data-ttu-id="f6cd8-149">Common Data Model-mappa adatforrás szerkesztése</span><span class="sxs-lookup"><span data-stu-id="f6cd8-149">Edit a Common Data Model folder data source</span></span>

<span data-ttu-id="f6cd8-150">A Common Data Model-mappát tartalmazó tárfiókhoz tartozó elérési kulcsot frissítheti.</span><span class="sxs-lookup"><span data-stu-id="f6cd8-150">You can update the access key for the storage account containing the Common Data Model folder.</span></span> <span data-ttu-id="f6cd8-151">A model.json vagy a manifest.json fájlt is módosíthatja.</span><span class="sxs-lookup"><span data-stu-id="f6cd8-151">You may also change the model.json or manifest.json file.</span></span> <span data-ttu-id="f6cd8-152">Ha a tárfiókból egy másik tárolóhoz szeretne kapcsolódni, vagy módosítani szeretné a fiók nevét, akkor [hozzon létre egy új adatforrás-kapcsolatot](#connect-to-a-common-data-model-folder).</span><span class="sxs-lookup"><span data-stu-id="f6cd8-152">To connect to a different container from your storage account, or change the account name, [create a new data source connection](#connect-to-a-common-data-model-folder).</span></span>

1. <span data-ttu-id="f6cd8-153">A célközönség információin belül nyissa meg a következőt **Adatok** > **Adatforrások**.</span><span class="sxs-lookup"><span data-stu-id="f6cd8-153">In audience insights, go to **Data** > **Data sources**.</span></span>

2. <span data-ttu-id="f6cd8-154">A frissíteni kívánt adatforrás mellett jelölje ki a három pontot.</span><span class="sxs-lookup"><span data-stu-id="f6cd8-154">Next to the data source you'd like to update, select the ellipsis.</span></span>

3. <span data-ttu-id="f6cd8-155">Válassza a lista **Szerkesztés** elemét.</span><span class="sxs-lookup"><span data-stu-id="f6cd8-155">Select the **Edit** option from the list.</span></span>

4. <span data-ttu-id="f6cd8-156">Opcionálisan frissítse a **Hozzáférési kulcsot**, és válassza a **Tovább** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="f6cd8-156">Optionally, update the **Access key** and select **Next**.</span></span>

   ![Párbeszéd a meglévő adatforráshoz tartozó hozzáférési kulcs szerkesztéséhez és frissítéséhez](media/edit-access-key.png)

5. <span data-ttu-id="f6cd8-158">Lehetőség van arra, hogy a fiókkulcs-kapcsolatot az erőforrás- vagy előfizetés-alapú kapcsolatra is frissítheti.</span><span class="sxs-lookup"><span data-stu-id="f6cd8-158">Optionally, you can update from an account key connection to a resource-based or a subscription-based connection.</span></span> <span data-ttu-id="f6cd8-159">További információkért lásd: [Célközönség-információk összekapcsolása az Azure Data Lake Storage Gen2 fiókjához az Azure egyszerű szolgáltatásnévvel](connect-service-principal.md).</span><span class="sxs-lookup"><span data-stu-id="f6cd8-159">For more information, see [Connect audience insights to an Azure Data Lake Storage Gen2 account with an Azure service principal](connect-service-principal.md).</span></span> <span data-ttu-id="f6cd8-160">A kapcsolat frissítésekor a **Tárolóra** vonatkozó információk nem módosíthatók.</span><span class="sxs-lookup"><span data-stu-id="f6cd8-160">You can't change **Container** information when updating the connection.</span></span>
   > [!div class="mx-imgBorder"]

   > ![Párbeszédpanel az Azure Data Lake kapcsolati adatainak megadásához egy meglévő tárhelyfiókhoz](media/enter-existing-storage-details.png)

   > [!NOTE]
   > <span data-ttu-id="f6cd8-162">Ahhoz, hogy a tárolóhoz vagy a fenti tárolókhoz kapcsolódhasson, és létre tudja hozni adatforrást a következő szerepkörök egyike szükséges:</span><span class="sxs-lookup"><span data-stu-id="f6cd8-162">You need one of the following roles either to the container or the storage account referred above to be able to connect to and create a data source:</span></span>
   >  - <span data-ttu-id="f6cd8-163">Storage Blob adatolvasó</span><span class="sxs-lookup"><span data-stu-id="f6cd8-163">Storage Blob Data Reader</span></span>
   >  - <span data-ttu-id="f6cd8-164">Storage Blob adattulajdonos</span><span class="sxs-lookup"><span data-stu-id="f6cd8-164">Storage Blob Data Owner</span></span>
   >  - <span data-ttu-id="f6cd8-165">Storage Blob adatközreműködő</span><span class="sxs-lookup"><span data-stu-id="f6cd8-165">Storage Blob Data Contributo</span></span>


6. <span data-ttu-id="f6cd8-166">Másik model.json vagy manifest.json fájl is választható, a tárolóból származó más entitáskészletekkel.</span><span class="sxs-lookup"><span data-stu-id="f6cd8-166">Optionally, choose a different model.json or manifest.json file with a different set of entities from the container.</span></span>

7. <span data-ttu-id="f6cd8-167">Tetszés szerint kiválaszthat további entitásokat is, amelyeket betölthet.</span><span class="sxs-lookup"><span data-stu-id="f6cd8-167">Optionally, you can select additional entities to ingest.</span></span> <span data-ttu-id="f6cd8-168">Ha nincsenek függőségek, akkor a már kijelölt entitásokat is eltávolíthatja.</span><span class="sxs-lookup"><span data-stu-id="f6cd8-168">You can also remove any already selected entities if there are no dependencies.</span></span>

   > [!IMPORTANT]
   > <span data-ttu-id="f6cd8-169">Ha függőségek vannak a meglévő model.json vagy manifest.json fájlhoz és az entitások készletéhez. egy hibaüzenet jelenik meg, és nem választhat másik model.json vagy manifest.json fájlt.</span><span class="sxs-lookup"><span data-stu-id="f6cd8-169">If there are dependencies on the existing model.json or manifest.json file and the set of entities, you'll see an error message and can't select a different model.json or manifest.json file.</span></span> <span data-ttu-id="f6cd8-170">A model.json vagy a manifest.json fájl módosítása előtt távolítsa el ezeket a függőségeket, vagy hozzon létre egy új adatforrást a használni kívánt model.json vagy a manifest.json fájllal a függőségek elkerüléséhez szükséges.</span><span class="sxs-lookup"><span data-stu-id="f6cd8-170">Remove those dependencies before changing the model.json or manifest.json file or create a new data source with the model.json or manifest.json file that you want to use to avoid removing the dependencies.</span></span>

8. <span data-ttu-id="f6cd8-171">Tetszés szerint kiválaszthat további attribútumokat vagy entitásokat, amelyek lehetővé teszik az adatok profilkészítésének engedélyezését vagy letiltását a már kijelöltek esetén.</span><span class="sxs-lookup"><span data-stu-id="f6cd8-171">Optionally, you can select additional attributes or entities to enable data profiling on or disable already selected ones.</span></span>   


[!INCLUDE[footer-include](../includes/footer-banner.md)]