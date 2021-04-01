---
title: A környezetek létrehozása és kezelése
description: Megismerheti, hogyan lehet regisztrálni a szolgáltatásra, és hogyan kezelhetők a környezetek.
ms.date: 02/01/2021
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
ms.reviewer: mhart
author: NimrodMagen
ms.author: nimagen
manager: shellyha
ms.openlocfilehash: 1c2dfdd2889b5cb6c5285b4d7cc7f52a3d6de4d1
ms.sourcegitcommit: bae40184312ab27b95c140a044875c2daea37951
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/15/2021
ms.locfileid: "5598296"
---
# <a name="manage-environments"></a><span data-ttu-id="843c0-103">Környezetek kezelése</span><span class="sxs-lookup"><span data-stu-id="843c0-103">Manage environments</span></span>

[!INCLUDE [cc-data-platform-banner](../includes/cc-data-platform-banner.md)]

<span data-ttu-id="843c0-104">Ez a cikk azt mutatja be, hogyan hozhat létre új szervezetet, és hogyan lehet létrehozni egy környezetet.</span><span class="sxs-lookup"><span data-stu-id="843c0-104">This article explains how to create a new organization and how to provision an environment.</span></span>

## <a name="sign-up-and-create-an-organization"></a><span data-ttu-id="843c0-105">Regisztráció és szervezet létrehozása</span><span class="sxs-lookup"><span data-stu-id="843c0-105">Sign up and create an organization</span></span>

1. <span data-ttu-id="843c0-106">Nyissa meg a [Dynamics 365 Customer Insights](https://dynamics.microsoft.com/ai/customer-insights/) webhelyet.</span><span class="sxs-lookup"><span data-stu-id="843c0-106">Go to the [Dynamics 365 Customer Insights](https://dynamics.microsoft.com/ai/customer-insights/) website.</span></span>

2. <span data-ttu-id="843c0-107">Válassza az **Első lépések** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="843c0-107">Select **Get Started**.</span></span>

3. <span data-ttu-id="843c0-108">Válassza ki az előnyben részesített feliratkozási forgatókönyvet, és válassza ki az ahhoz tartozó hivatkozást.</span><span class="sxs-lookup"><span data-stu-id="843c0-108">Choose your preferred sign-up scenario and select the corresponding link.</span></span>

4. <span data-ttu-id="843c0-109">Fogadja el a feltételeket, és válassza a **Folytatás** lehetőséget a szervezet létrehozásának megkezdéséhez.</span><span class="sxs-lookup"><span data-stu-id="843c0-109">Accept the terms and conditions and select **Continue** to start creating the organization.</span></span>

5. <span data-ttu-id="843c0-110">A környezet létrehozása után a rendszer átirányítja a [Customer Insights](https://home.ci.ai.dynamics.com) szolgáltatásra.</span><span class="sxs-lookup"><span data-stu-id="843c0-110">After the environment is created, you'll be redirected to [Customer Insights](https://home.ci.ai.dynamics.com).</span></span>

6. <span data-ttu-id="843c0-111">A bemutató környezettel ismerje meg az alkalmazást, vagy hozzon létre egy új környezetet a következő szakasz lépéseinek végrehajtásával.</span><span class="sxs-lookup"><span data-stu-id="843c0-111">Use the demo environment to explore the app, or create a new environment by following the steps in the next section.</span></span>

7. <span data-ttu-id="843c0-112">A környezeti beállítások megadása után válassza a **Létrehozás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="843c0-112">After specifying the environment settings, select **Create**.</span></span>

8. <span data-ttu-id="843c0-113">A környezet sikeres létrehozása után a rendszer bejelentkezteti a környezetbe.</span><span class="sxs-lookup"><span data-stu-id="843c0-113">You'll be signed in after the environment was created successfully.</span></span>

## <a name="create-an-environment-in-an-existing-organization"></a><span data-ttu-id="843c0-114">Környezet létrehozása meglévő szervezetből</span><span class="sxs-lookup"><span data-stu-id="843c0-114">Create an environment in an existing organization</span></span>

<span data-ttu-id="843c0-115">Kétféleképpen hozhat létre új környezetet.</span><span class="sxs-lookup"><span data-stu-id="843c0-115">There are two ways to create a new environment.</span></span> <span data-ttu-id="843c0-116">MEghatározhat teljesen új konfigurációt, vagy másolhat néhány konfigurációs beállítást egy meglévő környezetből.</span><span class="sxs-lookup"><span data-stu-id="843c0-116">You can either specify an entirely new configuration, or you can copy some configuration settings from an existing environment.</span></span>

<span data-ttu-id="843c0-117">Környezet létrehozásához:</span><span class="sxs-lookup"><span data-stu-id="843c0-117">To create an environment:</span></span>

1. <span data-ttu-id="843c0-118">Válassza ki az alkalmazás fejlécében a **Környezet** választót.</span><span class="sxs-lookup"><span data-stu-id="843c0-118">Select the **Environment** picker in the header of the app.</span></span>

1. <span data-ttu-id="843c0-119">Válassza az **Új** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="843c0-119">Select **New**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="843c0-120">![Környezeti beállítások](media/environment-settings-dialog.png)</span><span class="sxs-lookup"><span data-stu-id="843c0-120">![Environment settings](media/environment-settings-dialog.png)</span></span>

1. <span data-ttu-id="843c0-121">Az **új környezet létrehozása** párbeszédpanelen válassza az **új környezet** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="843c0-121">In the **Create new environment** dialog, select **New environment**.</span></span>

   <span data-ttu-id="843c0-122">Ha [az aktuális környezetből szeretne adatot másolni](#additional-considerations-for-copy-configuration-preview), akkor válassza a **Másolás meglévő környezetből** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="843c0-122">If you want to [copy data from the current environment](#additional-considerations-for-copy-configuration-preview), select **Copy from existing environment**.</span></span> <span data-ttu-id="843c0-123">A szervezetében összes elérhető környezet listáját látja, amelyekből adatokat másolhat.</span><span class="sxs-lookup"><span data-stu-id="843c0-123">You'll see a list of all available environments in your organization where you can copy data from.</span></span>

1. <span data-ttu-id="843c0-124">Adja meg a következő részleteket:</span><span class="sxs-lookup"><span data-stu-id="843c0-124">Provide the following details:</span></span>
   - <span data-ttu-id="843c0-125">**Név**: A környezet neve.</span><span class="sxs-lookup"><span data-stu-id="843c0-125">**Name**: The name for this environment.</span></span> <span data-ttu-id="843c0-126">Ha meglévő környezetből másolt, akkor ez a mező már ki van töltve, de ez módosítható.</span><span class="sxs-lookup"><span data-stu-id="843c0-126">This field is already filled in if you've copied an existing environment, but you can change it.</span></span>
   - <span data-ttu-id="843c0-127">**Régió**: Az a régió, ahová a szolgáltatást telepítették és üzemeltetik.</span><span class="sxs-lookup"><span data-stu-id="843c0-127">**Region**: The region into which the service is deployed and hosted.</span></span>
   - <span data-ttu-id="843c0-128">**Típus**: Adja meg, hogy szeretne-e működési vagy tesztkörnyezetet létrehozni.</span><span class="sxs-lookup"><span data-stu-id="843c0-128">**Type**: Select whether you want to create a Production or Sandbox environment.</span></span>

2. <span data-ttu-id="843c0-129">Nem kötelezően kiválaszthatja a **Speciális beállításokat**:</span><span class="sxs-lookup"><span data-stu-id="843c0-129">Optionally, you can select **Advanced settings**:</span></span>

   - <span data-ttu-id="843c0-130">**Összes adat mentése ide**: Megadja, hogy hol szeretné tárolni a Customer Insights-ból előállított kimeneti adatait.</span><span class="sxs-lookup"><span data-stu-id="843c0-130">**Save all data to**: Specifies where you want to store the output data generated from Customer Insights.</span></span> <span data-ttu-id="843c0-131">Két lehetőség közül választhat **Customer Insights tároló** ( egy Azure Data Lake, amelyet a Customer Insights csapata kezel) és **Azure Data Lake Storage Gen2** (saját Azure Data Lake Storage tárolója).</span><span class="sxs-lookup"><span data-stu-id="843c0-131">You'll have two options: **Customer Insights storage** (an Azure Data Lake managed by the Customer Insights team) and **Azure Data Lake Storage Gen2** (your own Azure Data Lake Storage).</span></span> <span data-ttu-id="843c0-132">Alapértelmezés szerint a Customer Insights tárolóhely beállítás van kiválasztva.</span><span class="sxs-lookup"><span data-stu-id="843c0-132">By default, the Customer Insights storage option is selected.</span></span>

   > [!NOTE]
   > <span data-ttu-id="843c0-133">Ha adatokat ment az Azure Data Lake Storage tárhelyre azzal elfogadja, hogy az adatok át lesznek víve az Azure tárfióknak megfelelő földrajzi helyre, és ott lesznek tárolva; ez eltérhet attól a helytől, ahol a Dynamics 365 Customer Insights adatai vannak tárolva.</span><span class="sxs-lookup"><span data-stu-id="843c0-133">By saving data to Azure Data Lake Storage, you agree that data will be transferred to and stored in the appropriate geographic location for that Azure storage account, which may differ from where data is stored in Dynamics 365 Customer Insights.</span></span> [<span data-ttu-id="843c0-134">További információ a Microsoft adatvédelmi központról.</span><span class="sxs-lookup"><span data-stu-id="843c0-134">Learn more at the Microsoft Trust Center.</span></span>](https://www.microsoft.com/trust-center)
   >
   > <span data-ttu-id="843c0-135">Jelenleg a beolvasott entitások tárolása mindig a Customer Insights által kezelt adattóban történik.</span><span class="sxs-lookup"><span data-stu-id="843c0-135">Currently, ingested entities are always stored in the Customer Insights managed data lake.</span></span>
   > <span data-ttu-id="843c0-136">Csak az Azure Data Lake Gen2 tárfiókokat támogatjuk, amelyek a környezet létrehozásakor kiválasztott Azure-régióból származnak.</span><span class="sxs-lookup"><span data-stu-id="843c0-136">We support only Azure Data Lake Gen2 storage accounts from the same Azure region you selected when creating the environment.</span></span>
   > <span data-ttu-id="843c0-137">Csak az Azure Data Lake Gen2 Hierarchical Name Space (HNS) képes tárhelyfiókokat támogatjuk.</span><span class="sxs-lookup"><span data-stu-id="843c0-137">We support only Azure Data Lake Gen2 Hierarchical Name Space (HNS) enabled storage accounts.</span></span>

   - <span data-ttu-id="843c0-138">Az Azure Data Lake Storage Gen2 beállításnál választhat az erőforrás-alapú és az előfizetés-alapú hitelesítés használata között.</span><span class="sxs-lookup"><span data-stu-id="843c0-138">For the Azure Data Lake Storage Gen2 option, you can choose between a resource-based option and a subscription-based option for authentication.</span></span> <span data-ttu-id="843c0-139">További információkért lásd: [Célközönség-információk összekapcsolása az Azure Data Lake Storage Gen2 fiókjához az Azure egyszerű szolgáltatásnévvel](connect-service-principal.md).</span><span class="sxs-lookup"><span data-stu-id="843c0-139">For more information, see [Connect audience insights to an Azure Data Lake Storage Gen2 account with an Azure service principal](connect-service-principal.md).</span></span> <span data-ttu-id="843c0-140">A **Tároló** neve nem módosítható, és "customerinsights" lesz.</span><span class="sxs-lookup"><span data-stu-id="843c0-140">The **Container** name can't be changed and will be "customerinsights".</span></span>
   
   - <span data-ttu-id="843c0-141">Ha [Előrejelzéseket](predictions.md) szeretne használni, vagy szeretné konfigurálni az adatok megosztását az alkalmazásokkal és megoldásokkal a Microsoft Dataverse alapján, akkor adja meg a Microsoft Dataverse környezet URL-címét a **konfigurálja a Microsoft Dataverse adatmegosztást és engedélyezze a további szolgáltatásokat** alatt.</span><span class="sxs-lookup"><span data-stu-id="843c0-141">If you want to use [predictions](predictions.md) or configure data sharing with applications and solutions based on Microsoft Dataverse, provide the Microsoft Dataverse environment URL under **Configure data sharing with Microsoft Dataverse and enable additional capabilities**.</span></span> <span data-ttu-id="843c0-142">Válassza az **Adatmegosztás engedélyezése** lehetőséget, ha meg szeretné osztani a Customer Insights kimeneti adatait a Microsoft Dataverse Managed Data Lake használatával.</span><span class="sxs-lookup"><span data-stu-id="843c0-142">Select **Enable data sharing** to share Customer Insights output data with a Microsoft Dataverse Managed Data Lake.</span></span>

     > [!NOTE]
     > - <span data-ttu-id="843c0-143">A Microsoft Dataverse Managed Data Lake használatával való adatmegosztás jelenleg nem támogatott, ha az adatokat a saját Azure Data Lake Storage tárhelyére menti.</span><span class="sxs-lookup"><span data-stu-id="843c0-143">Data sharing with Microsoft Dataverse Managed Data Lake is currently not supported when you save all data to your own Azure Data Lake Storage.</span></span>
     > - <span data-ttu-id="843c0-144">[Az entitásból hiányzó értékek előrejelzése](predictions.md) jelenleg nem támogatott, ha engedélyezi az adatok megosztását a Microsoft Dataverse Managed Data Lake használatával.</span><span class="sxs-lookup"><span data-stu-id="843c0-144">[Prediction of missing values in an entity](predictions.md) is not currently supported when you enable data sharing with Microsoft Dataverse Managed Data Lake.</span></span>

     > [!div class="mx-imgBorder"]
     > <span data-ttu-id="843c0-145">![Konfigurálási lehetőségek az adatmegosztás engedélyezéséhez a Microsoft Dataverse-szolgáltatással](media/Datasharing-with-DataverseMDL.png)</span><span class="sxs-lookup"><span data-stu-id="843c0-145">![Configuration options to enable data sharing with Microsoft Dataverse](media/Datasharing-with-DataverseMDL.png)</span></span>

   <span data-ttu-id="843c0-146">A folyamatok – például adatbetöltés vagy szegmenslétrehozás – futtatásakor a megfelelő mappák létrejönnek a fent megadott tárfiókban.</span><span class="sxs-lookup"><span data-stu-id="843c0-146">When you run processes, such as data ingestion or segment creation, corresponding folders will be created in the storage account you specified above.</span></span> <span data-ttu-id="843c0-147">Az adatfájlok és a model.json fájlok a futtatott folyamat alapján jönnek létre, és hozzáadódnak a megfelelő almappákhoz.</span><span class="sxs-lookup"><span data-stu-id="843c0-147">Data files and model.json files will be created and added to the respective subfolders based on the process you run.</span></span>

   <span data-ttu-id="843c0-148">Ha több Customer Insights-környezetet hoz létre, és úgy dönt, hogy menti a kimeneti entitást ezekből a környezetekből a tárfiókba, a rendszer minden környezethez külön mappát hoz létre a tárolóban ci_<environmentid>.</span><span class="sxs-lookup"><span data-stu-id="843c0-148">If you create multiple environments of Customer Insights and choose to save the output entities from those environments in your storage account, separate folders will be created for each environment with ci_<environmentid> in the container.</span></span>

### <a name="additional-considerations-for-copy-configuration-preview"></a><span data-ttu-id="843c0-149">A konfiguráció másolásának további szempontjai (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="843c0-149">Additional considerations for copy configuration (preview)</span></span>

<span data-ttu-id="843c0-150">A következő konfigurációbeállítások vannak másolva:</span><span class="sxs-lookup"><span data-stu-id="843c0-150">The following configuration settings are copied:</span></span>

- <span data-ttu-id="843c0-151">Funkciókonfigurációk</span><span class="sxs-lookup"><span data-stu-id="843c0-151">Feature configurations</span></span>
- <span data-ttu-id="843c0-152">Betöltött/importált adatforrások</span><span class="sxs-lookup"><span data-stu-id="843c0-152">Ingested/imported data sources</span></span>
- <span data-ttu-id="843c0-153">Adategységesítési (Megfeleltetés/Egyeztetés/Egyesítés) konfiguráció</span><span class="sxs-lookup"><span data-stu-id="843c0-153">Data unification (Map, Match, Merge) configuration</span></span>
- <span data-ttu-id="843c0-154">Szegmensek</span><span class="sxs-lookup"><span data-stu-id="843c0-154">Segments</span></span>
- <span data-ttu-id="843c0-155">Mértékek</span><span class="sxs-lookup"><span data-stu-id="843c0-155">Measures</span></span>
- <span data-ttu-id="843c0-156">Kapcsolatok</span><span class="sxs-lookup"><span data-stu-id="843c0-156">Relationships</span></span>
- <span data-ttu-id="843c0-157">Tevékenységek</span><span class="sxs-lookup"><span data-stu-id="843c0-157">Activities</span></span>
- <span data-ttu-id="843c0-158">Keresési és szűrőindex</span><span class="sxs-lookup"><span data-stu-id="843c0-158">Search & filter Index</span></span>
- <span data-ttu-id="843c0-159">Exportálási célhelyek</span><span class="sxs-lookup"><span data-stu-id="843c0-159">Export destinations</span></span>
- <span data-ttu-id="843c0-160">Ütemezett frissítés</span><span class="sxs-lookup"><span data-stu-id="843c0-160">Scheduled refresh</span></span>
- <span data-ttu-id="843c0-161">Bővítések</span><span class="sxs-lookup"><span data-stu-id="843c0-161">Enrichments</span></span>
- <span data-ttu-id="843c0-162">Modellkezelés</span><span class="sxs-lookup"><span data-stu-id="843c0-162">Model management</span></span>
- <span data-ttu-id="843c0-163">Szerepkör-hozzárendelések</span><span class="sxs-lookup"><span data-stu-id="843c0-163">Role assignments</span></span>

<span data-ttu-id="843c0-164">A következő konfigurációbeállítások *nincsenek* másolva:</span><span class="sxs-lookup"><span data-stu-id="843c0-164">The following settings are *not* copied:</span></span>

- <span data-ttu-id="843c0-165">Ügyfélprofilok.</span><span class="sxs-lookup"><span data-stu-id="843c0-165">Customer profiles.</span></span>
- <span data-ttu-id="843c0-166">Adatforrás hitelesítő adatai.</span><span class="sxs-lookup"><span data-stu-id="843c0-166">Data source credentials.</span></span> <span data-ttu-id="843c0-167">A hitelesítő adatokat meg kell adnia minden adatforráshoz, és manuálisan kell frissítenie az adatforrásokat.</span><span class="sxs-lookup"><span data-stu-id="843c0-167">You'll have to provide the credentials for every data source and refresh the data sources manually.</span></span>
- <span data-ttu-id="843c0-168">Adatforrások a Common Data Model mappából és a Common Data Service felügyelt tóból.</span><span class="sxs-lookup"><span data-stu-id="843c0-168">Data sources from Common Data Model folder and Common Data Service managed lake.</span></span> <span data-ttu-id="843c0-169">Ezeket az adatforrásokat manuálisan, ugyanolyan néven kell létrehoznia, mint a forráskörnyezetében.</span><span class="sxs-lookup"><span data-stu-id="843c0-169">You'll have to create those data sources manually with the same name as in the source environment.</span></span>

<span data-ttu-id="843c0-170">Környezet másolásakor egy megerősítő üzenet jelenik meg, amely szerint létrejött az új környezet.</span><span class="sxs-lookup"><span data-stu-id="843c0-170">When you copy an environment, you'll see a confirmation message that the new environment has been created.</span></span> <span data-ttu-id="843c0-171">Válassza az **Ugrás az adatforrásokhoz** lehetőséget az adatforrások listájának megjelenítéséhez.</span><span class="sxs-lookup"><span data-stu-id="843c0-171">Select **Go to data sources** to see the list of data sources.</span></span>

<span data-ttu-id="843c0-172">Minden adatforrásnál megjelenik egy **Hitelesítő adatok szükségesek** állapot.</span><span class="sxs-lookup"><span data-stu-id="843c0-172">All the data sources will show a **Credentials Required** status.</span></span> <span data-ttu-id="843c0-173">Szerkessze az adatforrásokat, és adja meg a hitelesítő adatokat a frissítésükhöz.</span><span class="sxs-lookup"><span data-stu-id="843c0-173">Edit the data sources and enter the credentials to refresh them.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="843c0-174">![Másolt adatforrások](media/data-sources-copied.png)</span><span class="sxs-lookup"><span data-stu-id="843c0-174">![Data sources copied](media/data-sources-copied.png)</span></span>

<span data-ttu-id="843c0-175">Az adatforrások frissítését követően nyissa meg az **Adatok** > **Egyesítés** pontot.</span><span class="sxs-lookup"><span data-stu-id="843c0-175">After refreshing the data sources, go to **Data** > **Unify**.</span></span> <span data-ttu-id="843c0-176">Itt megtalálja a beállításokat a forráskörnyezetből.</span><span class="sxs-lookup"><span data-stu-id="843c0-176">Here you'll find settings from the source environment.</span></span> <span data-ttu-id="843c0-177">Igény szerint szerkessze őket, vagy válassza a **Futtatás** lehetőséget az adategyesítési folyamat elindításához, és hozzon létre egy egyesített ügyfélentitást.</span><span class="sxs-lookup"><span data-stu-id="843c0-177">Edit them as needed or select **Run** to start the data unification process and create the unified customer entity.</span></span>

<span data-ttu-id="843c0-178">Amikor az adatok egyesítése befejeződött, nyissa meg a **Mértékek** és a **Szegmensek** lehetőséget, hogy azokat is frissítse.</span><span class="sxs-lookup"><span data-stu-id="843c0-178">When the data unification is complete, go to **Measures** and **Segments** to refresh them too.</span></span>

## <a name="edit-an-existing-environment"></a><span data-ttu-id="843c0-179">Egy meglévő környezet szerkesztése</span><span class="sxs-lookup"><span data-stu-id="843c0-179">Edit an existing environment</span></span>

<span data-ttu-id="843c0-180">A meglévő környezetek bizonyos részleteit szerkesztheti.</span><span class="sxs-lookup"><span data-stu-id="843c0-180">You can edit some of the details of existing environments.</span></span>

1.  <span data-ttu-id="843c0-181">Válassza ki az alkalmazás fejlécében a **Környezet** választót.</span><span class="sxs-lookup"><span data-stu-id="843c0-181">Select the **Environment** picker in the header of the app.</span></span>

2.  <span data-ttu-id="843c0-182">Kattintson a **Szerkesztés** ikonra.</span><span class="sxs-lookup"><span data-stu-id="843c0-182">Select the **Edit** icon.</span></span>

3. <span data-ttu-id="843c0-183">A **Környezet szerkesztése** mezőben frissítheti a környezet **Megejelenő nevét**, de a **Régió** vagy a **Típus** nem módosítható.</span><span class="sxs-lookup"><span data-stu-id="843c0-183">In the **Edit environment** box, you can update the environment's **Display name**, but you can't change the **Region** or **Type**.</span></span>

4. <span data-ttu-id="843c0-184">Ha egy környezet úgy van beállítva, hogy az Azure Data Lake Storage Gen2-ben tárolja az adatokat, akkor frissítheti a **Fiókkulcsot**.</span><span class="sxs-lookup"><span data-stu-id="843c0-184">If an environment is configured to store data in Azure Data Lake Storage Gen2, you can update the **Account key**.</span></span> <span data-ttu-id="843c0-185">A **partner neve** vagy a **tároló** neve azonban nem módosítható.</span><span class="sxs-lookup"><span data-stu-id="843c0-185">However, you can't change the **Account name** or **Container** name.</span></span>

5. <span data-ttu-id="843c0-186">Lehetőség van arra, hogy a fiókkulcs-alapú kapcsolatot az erőforrás- vagy előfizetés-alapú kapcsolatra is frissítheti.</span><span class="sxs-lookup"><span data-stu-id="843c0-186">Optionally, you can update from an account key based connection to a resource-based or subscription-based connection.</span></span> <span data-ttu-id="843c0-187">A frissítést követően a frissítés után nem térhet vissza a fiókkulcshoz.</span><span class="sxs-lookup"><span data-stu-id="843c0-187">Once upgraded, you cannot revert to account key after the update.</span></span> <span data-ttu-id="843c0-188">További információkért lásd: [Célközönség-információk összekapcsolása az Azure Data Lake Storage Gen2 fiókjához az Azure egyszerű szolgáltatásnévvel](connect-service-principal.md).</span><span class="sxs-lookup"><span data-stu-id="843c0-188">For more information, see [Connect audience insights to an Azure Data Lake Storage Gen2 account with an Azure service principal](connect-service-principal.md).</span></span> <span data-ttu-id="843c0-189">A kapcsolat frissítésekor a **Tárolóra** vonatkozó információk nem módosíthatók.</span><span class="sxs-lookup"><span data-stu-id="843c0-189">You can't change **Container** information when updating the connection.</span></span>

## <a name="reset-an-existing-environment"></a><span data-ttu-id="843c0-190">Meglévő környezet visszaállítása</span><span class="sxs-lookup"><span data-stu-id="843c0-190">Reset an existing environment</span></span>

<span data-ttu-id="843c0-191">Rendszergazdaként a környezetet visszaállíthatja üres állapotba, ha szeretné törölni az összes konfigurációt, és eltávolítani a betöltött adatokat.</span><span class="sxs-lookup"><span data-stu-id="843c0-191">As an administrator, you can reset an environment to an empty state if you want to delete all configurations and remove the ingested data.</span></span>

1.  <span data-ttu-id="843c0-192">Válassza ki az alkalmazás fejlécében a **Környezet** választót.</span><span class="sxs-lookup"><span data-stu-id="843c0-192">Select the **Environment** picker in the header of the app.</span></span> 

2.  <span data-ttu-id="843c0-193">Válassza ki az alaphelyzetbe állítani kívánt környezetet, és válassza ki a három pontot **...**.</span><span class="sxs-lookup"><span data-stu-id="843c0-193">Select the environment you want to reset and select the ellipsis **...**.</span></span> 

3. <span data-ttu-id="843c0-194">Válassza az **Alaphelyzetbe állítás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="843c0-194">Choose the **Reset** option.</span></span> 

4.  <span data-ttu-id="843c0-195">A törlés jóváhagyásához írja be a környezet nevét, és válassza az **Alaphelyzetbe állítás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="843c0-195">To confirm the deletion, enter the environment name and select **Reset**.</span></span>

## <a name="delete-an-existing-environment-available-only-for-admins"></a><span data-ttu-id="843c0-196">Meglévő környezet törlése (csak rendszergazdák számára érhető el)</span><span class="sxs-lookup"><span data-stu-id="843c0-196">Delete an existing environment (available only for admins)</span></span>

<span data-ttu-id="843c0-197">Rendszergazdaként törölheti az Ön által felügyelt környezetet.</span><span class="sxs-lookup"><span data-stu-id="843c0-197">As an administrator, you can delete an environment you administer.</span></span>

1.  <span data-ttu-id="843c0-198">Válassza ki az alkalmazás fejlécében a **Környezet** választót.</span><span class="sxs-lookup"><span data-stu-id="843c0-198">Select the **Environment** picker in the header of the app.</span></span>

2.  <span data-ttu-id="843c0-199">Válassza ki az alaphelyzetbe állítani kívánt környezetet, és válassza ki a három pontot **...**.</span><span class="sxs-lookup"><span data-stu-id="843c0-199">Select the environment you want to reset and select the ellipsis **...**.</span></span> 

3. <span data-ttu-id="843c0-200">Válassza a **Törlés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="843c0-200">Choose the **Delete** option.</span></span> 

4.  <span data-ttu-id="843c0-201">A törlés jóváhagyásához adja meg a környezet nevét, és válassza a **Törlés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="843c0-201">To confirm the deletion, enter the environment name and select **Delete**.</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]