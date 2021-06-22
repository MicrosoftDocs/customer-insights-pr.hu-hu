---
title: A környezetek létrehozása és kezelése
description: Megismerheti, hogyan lehet regisztrálni a szolgáltatásra, és hogyan kezelhetők a környezetek.
ms.date: 06/15/2021
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
ms.reviewer: mhart
author: NimrodMagen
ms.author: nimagen
manager: shellyha
ms.openlocfilehash: 06310ea6fc72f26e21e185a6abcb5d19d4b201f6
ms.sourcegitcommit: e5425f060c8d80f9510283dc610ce70a4e709b1e
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/15/2021
ms.locfileid: "6259102"
---
# <a name="manage-environments"></a><span data-ttu-id="a6209-103">Környezetek kezelése</span><span class="sxs-lookup"><span data-stu-id="a6209-103">Manage environments</span></span>

[!INCLUDE [cc-data-platform-banner](../includes/cc-data-platform-banner.md)]

<span data-ttu-id="a6209-104">Ez a cikk azt mutatja be, hogyan hozhat létre új szervezetet, és hogyan lehet létrehozni egy környezetet.</span><span class="sxs-lookup"><span data-stu-id="a6209-104">This article explains how to create a new organization and how to provision an environment.</span></span>

## <a name="sign-up-and-create-an-organization"></a><span data-ttu-id="a6209-105">Regisztráció és szervezet létrehozása</span><span class="sxs-lookup"><span data-stu-id="a6209-105">Sign up and create an organization</span></span>

1. <span data-ttu-id="a6209-106">Nyissa meg a [Dynamics 365 Customer Insights](https://dynamics.microsoft.com/ai/customer-insights/) webhelyet.</span><span class="sxs-lookup"><span data-stu-id="a6209-106">Go to the [Dynamics 365 Customer Insights](https://dynamics.microsoft.com/ai/customer-insights/) website.</span></span>

2. <span data-ttu-id="a6209-107">Válassza az **Első lépések** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="a6209-107">Select **Get Started**.</span></span>

3. <span data-ttu-id="a6209-108">Válassza ki az előnyben részesített feliratkozási forgatókönyvet, és válassza ki az ahhoz tartozó hivatkozást.</span><span class="sxs-lookup"><span data-stu-id="a6209-108">Choose your preferred sign-up scenario and select the corresponding link.</span></span>

4. <span data-ttu-id="a6209-109">Fogadja el a feltételeket, és válassza a **Folytatás** lehetőséget a szervezet létrehozásának megkezdéséhez.</span><span class="sxs-lookup"><span data-stu-id="a6209-109">Accept the terms and conditions and select **Continue** to start creating the organization.</span></span>

5. <span data-ttu-id="a6209-110">A környezet létrehozása után a rendszer átirányítja a [Customer Insights](https://home.ci.ai.dynamics.com) szolgáltatásra.</span><span class="sxs-lookup"><span data-stu-id="a6209-110">After the environment is created, you'll be redirected to [Customer Insights](https://home.ci.ai.dynamics.com).</span></span>

6. <span data-ttu-id="a6209-111">A bemutató környezettel ismerje meg az alkalmazást, vagy hozzon létre egy új környezetet a következő szakasz lépéseinek végrehajtásával.</span><span class="sxs-lookup"><span data-stu-id="a6209-111">Use the demo environment to explore the app, or create a new environment by following the steps in the next section.</span></span>

7. <span data-ttu-id="a6209-112">A környezeti beállítások megadása után válassza a **Létrehozás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="a6209-112">After specifying the environment settings, select **Create**.</span></span>

8. <span data-ttu-id="a6209-113">A környezet sikeres létrehozása után a rendszer bejelentkezteti a környezetbe.</span><span class="sxs-lookup"><span data-stu-id="a6209-113">You'll be signed in after the environment was created successfully.</span></span>

## <a name="create-an-environment-in-an-existing-organization"></a><span data-ttu-id="a6209-114">Környezet létrehozása meglévő szervezetből</span><span class="sxs-lookup"><span data-stu-id="a6209-114">Create an environment in an existing organization</span></span>

<span data-ttu-id="a6209-115">Kétféleképpen hozhat létre új környezetet.</span><span class="sxs-lookup"><span data-stu-id="a6209-115">There are two ways to create a new environment.</span></span> <span data-ttu-id="a6209-116">MEghatározhat teljesen új konfigurációt, vagy másolhat néhány konfigurációs beállítást egy meglévő környezetből.</span><span class="sxs-lookup"><span data-stu-id="a6209-116">You can either specify an entirely new configuration, or you can copy some configuration settings from an existing environment.</span></span>

> [!NOTE]
> <span data-ttu-id="a6209-117">A szervezetek minden Customer Insights licenchez *két* környezetet hozhatnak létre.</span><span class="sxs-lookup"><span data-stu-id="a6209-117">Organizations can create *two* environments for every Customer Insights license.</span></span> <span data-ttu-id="a6209-118">Ha a szervezete egynél több licencet vásárol, a rendelkezésre álló környezetek számának növelése érdekében [lépjen kapcsolatba a támogatási csoporttal](https://go.microsoft.com/fwlink/?linkid=2079641).</span><span class="sxs-lookup"><span data-stu-id="a6209-118">If your organization purchases more than once license, please [contact our support team](https://go.microsoft.com/fwlink/?linkid=2079641) to increase the number of available environments.</span></span> <span data-ttu-id="a6209-119">A kapacitással és a bővítménykapacitással kapcsolatos további információkért töltse le a [Dynamics 365 licencelési útmutatóját](https://go.microsoft.com/fwlink/?LinkId=866544).</span><span class="sxs-lookup"><span data-stu-id="a6209-119">For more information about capacity and add-on capacity, download [Dynamics 365 licensing guide](https://go.microsoft.com/fwlink/?LinkId=866544).</span></span>

<span data-ttu-id="a6209-120">Környezet létrehozásához:</span><span class="sxs-lookup"><span data-stu-id="a6209-120">To create an environment:</span></span>

1. <span data-ttu-id="a6209-121">Válassza ki az alkalmazás fejlécében a **Környezet** választót.</span><span class="sxs-lookup"><span data-stu-id="a6209-121">Select the **Environment** picker in the header of the app.</span></span>

1. <span data-ttu-id="a6209-122">Válassza az **Új** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="a6209-122">Select **New**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="a6209-123">![Környezeti beállítások](media/environment-settings-dialog.png)</span><span class="sxs-lookup"><span data-stu-id="a6209-123">![Environment settings](media/environment-settings-dialog.png)</span></span>

1. <span data-ttu-id="a6209-124">Az **új környezet létrehozása** párbeszédpanelen válassza az **új környezet** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="a6209-124">In the **Create new environment** dialog, select **New environment**.</span></span>

   <span data-ttu-id="a6209-125">Ha [az aktuális környezetből szeretne adatot másolni](#considerations-for-copy-configuration-preview), akkor válassza a **Másolás meglévő környezetből** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="a6209-125">If you want to [copy data from the current environment](#considerations-for-copy-configuration-preview), select **Copy from existing environment**.</span></span> <span data-ttu-id="a6209-126">A szervezetében összes elérhető környezet listáját látja, amelyekből adatokat másolhat.</span><span class="sxs-lookup"><span data-stu-id="a6209-126">You'll see a list of all available environments in your organization where you can copy data from.</span></span>

1. <span data-ttu-id="a6209-127">Adja meg a következő részleteket:</span><span class="sxs-lookup"><span data-stu-id="a6209-127">Provide the following details:</span></span>
   - <span data-ttu-id="a6209-128">**Név**: A környezet neve.</span><span class="sxs-lookup"><span data-stu-id="a6209-128">**Name**: The name for this environment.</span></span> <span data-ttu-id="a6209-129">Ha meglévő környezetből másolt, akkor ez a mező már ki van töltve, de ez módosítható.</span><span class="sxs-lookup"><span data-stu-id="a6209-129">This field is already filled in if you've copied an existing environment, but you can change it.</span></span>
   - <span data-ttu-id="a6209-130">**Régió**: Az a régió, ahová a szolgáltatást telepítették és üzemeltetik.</span><span class="sxs-lookup"><span data-stu-id="a6209-130">**Region**: The region into which the service is deployed and hosted.</span></span>
   - <span data-ttu-id="a6209-131">**Típus**: Adja meg, hogy szeretne-e működési vagy tesztkörnyezetet létrehozni.</span><span class="sxs-lookup"><span data-stu-id="a6209-131">**Type**: Select whether you want to create a Production or Sandbox environment.</span></span>

1. <span data-ttu-id="a6209-132">Nem kötelezően kiválaszthatja a **Speciális beállításokat**:</span><span class="sxs-lookup"><span data-stu-id="a6209-132">Optionally, you can select **Advanced settings**:</span></span>

   - <span data-ttu-id="a6209-133">**Összes adat mentése ide**: Megadja, hogy hol szeretné tárolni a Customer Insights-ból előállított kimeneti adatait.</span><span class="sxs-lookup"><span data-stu-id="a6209-133">**Save all data to**: Specifies where you want to store the output data generated from Customer Insights.</span></span> <span data-ttu-id="a6209-134">Két lehetőség közül választhat **Customer Insights tároló** ( egy Azure Data Lake, amelyet a Customer Insights csapata kezel) és **Azure Data Lake Storage Gen2** (saját Azure Data Lake Storage tárolója).</span><span class="sxs-lookup"><span data-stu-id="a6209-134">You'll have two options: **Customer Insights storage** (an Azure Data Lake managed by the Customer Insights team) and **Azure Data Lake Storage Gen2** (your own Azure Data Lake Storage).</span></span> <span data-ttu-id="a6209-135">Alapértelmezés szerint a Customer Insights tárolóhely beállítás van kiválasztva.</span><span class="sxs-lookup"><span data-stu-id="a6209-135">By default, the Customer Insights storage option is selected.</span></span>

   > [!NOTE]
   > <span data-ttu-id="a6209-136">Ha adatokat ment az Azure Data Lake Storage tárhelyre azzal elfogadja, hogy az adatok át lesznek víve az Azure tárfióknak megfelelő földrajzi helyre, és ott lesznek tárolva; ez eltérhet attól a helytől, ahol a Dynamics 365 Customer Insights adatai vannak tárolva.</span><span class="sxs-lookup"><span data-stu-id="a6209-136">By saving data to Azure Data Lake Storage, you agree that data will be transferred to and stored in the appropriate geographic location for that Azure storage account, which may differ from where data is stored in Dynamics 365 Customer Insights.</span></span> [<span data-ttu-id="a6209-137">További információ a Microsoft adatvédelmi központról.</span><span class="sxs-lookup"><span data-stu-id="a6209-137">Learn more at the Microsoft Trust Center.</span></span>](https://www.microsoft.com/trust-center)
   >
   > <span data-ttu-id="a6209-138">Jelenleg a beolvasott entitások tárolása mindig a Customer Insights által kezelt adattóban történik.</span><span class="sxs-lookup"><span data-stu-id="a6209-138">Currently, ingested entities are always stored in the Customer Insights managed data lake.</span></span>
   > <span data-ttu-id="a6209-139">Csak az Azure Data Lake Gen2 tárfiókokat támogatjuk, amelyek a környezet létrehozásakor kiválasztott Azure-régióból származnak.</span><span class="sxs-lookup"><span data-stu-id="a6209-139">We support only Azure Data Lake Gen2 storage accounts from the same Azure region you selected when creating the environment.</span></span>
   > <span data-ttu-id="a6209-140">Csak az Azure Data Lake Gen2 Hierarchical Name Space (HNS) képes tárhelyfiókokat támogatjuk.</span><span class="sxs-lookup"><span data-stu-id="a6209-140">We support only Azure Data Lake Gen2 Hierarchical Name Space (HNS) enabled storage accounts.</span></span>

   - <span data-ttu-id="a6209-141">Az Azure Data Lake Storage Gen2 beállításnál választhat az erőforrás-alapú és az előfizetés-alapú hitelesítés használata között.</span><span class="sxs-lookup"><span data-stu-id="a6209-141">For the Azure Data Lake Storage Gen2 option, you can choose between a resource-based option and a subscription-based option for authentication.</span></span> <span data-ttu-id="a6209-142">További információkért lásd: [Célközönség-információk összekapcsolása az Azure Data Lake Storage Gen2 fiókjához az Azure egyszerű szolgáltatásnévvel](connect-service-principal.md).</span><span class="sxs-lookup"><span data-stu-id="a6209-142">For more information, see [Connect audience insights to an Azure Data Lake Storage Gen2 account with an Azure service principal](connect-service-principal.md).</span></span> <span data-ttu-id="a6209-143">A **Tároló** neve nem változtatható meg, és `customerinsights` lesz.</span><span class="sxs-lookup"><span data-stu-id="a6209-143">The **Container** name can't be changed and will be `customerinsights`.</span></span>
   
   - <span data-ttu-id="a6209-144">Ha [előrejelzéseket](predictions.md) szeretne használni, konfigurálja az adatok megosztását a Microsoft Dataverse használatával, vagy engedélyezze a helyszíni környezet adatforrásokból való adatbetöltést, adja meg a Microsoft Dataverse környezet URL-címét az **Adatmegosztás konfigurálása Microsoft Dataverse-szel, és további képességek engedélyezése** alatt.</span><span class="sxs-lookup"><span data-stu-id="a6209-144">If you want to use [predictions](predictions.md), configure data sharing with Microsoft Dataverse, or enable data ingestion from on-premises data sources, provide the Microsoft Dataverse environment URL under **Configure data sharing with Microsoft Dataverse and enable additional capabilities**.</span></span> <span data-ttu-id="a6209-145">Válassza az **Adatmegosztás engedélyezése** lehetőséget, ha meg szeretné osztani a Customer Insights kimeneti adatait a Microsoft Dataverse Managed Data Lake használatával.</span><span class="sxs-lookup"><span data-stu-id="a6209-145">Select **Enable data sharing** to share Customer Insights output data with a Microsoft Dataverse Managed Data Lake.</span></span>

     > [!NOTE]
     > - <span data-ttu-id="a6209-146">A Microsoft Dataverse Managed Data Lake használatával való adatmegosztás jelenleg nem támogatott, ha az adatokat a saját Azure Data Lake Storage tárhelyére menti.</span><span class="sxs-lookup"><span data-stu-id="a6209-146">Data sharing with Microsoft Dataverse Managed Data Lake is currently not supported when you save all data to your own Azure Data Lake Storage.</span></span>
     > - <span data-ttu-id="a6209-147">[Az entitásból hiányzó értékek előrejelzése](predictions.md) jelenleg nem támogatott, ha engedélyezi az adatok megosztását a Microsoft Dataverse Managed Data Lake használatával.</span><span class="sxs-lookup"><span data-stu-id="a6209-147">[Prediction of missing values in an entity](predictions.md) is not currently supported when you enable data sharing with Microsoft Dataverse Managed Data Lake.</span></span>

     > [!div class="mx-imgBorder"]
     > <span data-ttu-id="a6209-148">![Konfigurálási lehetőségek az adatmegosztás engedélyezéséhez a Microsoft Dataverse-szolgáltatással](media/datasharing-with-DataverseMDL.png)</span><span class="sxs-lookup"><span data-stu-id="a6209-148">![Configuration options to enable data sharing with Microsoft Dataverse](media/datasharing-with-DataverseMDL.png)</span></span>

   <span data-ttu-id="a6209-149">A folyamatok – például adatbetöltés vagy szegmenslétrehozás – futtatásakor a megfelelő mappák létrejönnek a fent megadott tárfiókban.</span><span class="sxs-lookup"><span data-stu-id="a6209-149">When you run processes, such as data ingestion or segment creation, corresponding folders will be created in the storage account you specified above.</span></span> <span data-ttu-id="a6209-150">A rendszer a folyamat neve alapján adatfájlokat és model.json fájlokat hoz létre, és ad hozzá a megfelelőmappákhoz.</span><span class="sxs-lookup"><span data-stu-id="a6209-150">Data files and model.json files will be created and added to folders based on the process name.</span></span>

   <span data-ttu-id="a6209-151">Ha több Customer Insights-környezetet hoz létre, és úgy dönt, hogy menti a kimeneti entitást ezekből a környezetekből a tárfiókba, a rendszer minden környezethez külön mappát hoz létre a tárolóban ci_<environmentid>.</span><span class="sxs-lookup"><span data-stu-id="a6209-151">If you create multiple environments of Customer Insights and choose to save the output entities from those environments in your storage account, separate folders will be created for each environment with ci_<environmentid> in the container.</span></span>

### <a name="considerations-for-copy-configuration-preview"></a><span data-ttu-id="a6209-152">A másolási konfigurációval kapcsolatos szempontok (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="a6209-152">Considerations for copy configuration (preview)</span></span>

<span data-ttu-id="a6209-153">A következő konfigurációbeállítások vannak másolva:</span><span class="sxs-lookup"><span data-stu-id="a6209-153">The following configuration settings are copied:</span></span>

- <span data-ttu-id="a6209-154">Funkciókonfigurációk</span><span class="sxs-lookup"><span data-stu-id="a6209-154">Feature configurations</span></span>
- <span data-ttu-id="a6209-155">Betöltött/importált adatforrások</span><span class="sxs-lookup"><span data-stu-id="a6209-155">Ingested/imported data sources</span></span>
- <span data-ttu-id="a6209-156">Adategységesítési (Megfeleltetés/Egyeztetés/Egyesítés) konfiguráció</span><span class="sxs-lookup"><span data-stu-id="a6209-156">Data unification (Map, Match, Merge) configuration</span></span>
- <span data-ttu-id="a6209-157">Szegmensek</span><span class="sxs-lookup"><span data-stu-id="a6209-157">Segments</span></span>
- <span data-ttu-id="a6209-158">Mértékek</span><span class="sxs-lookup"><span data-stu-id="a6209-158">Measures</span></span>
- <span data-ttu-id="a6209-159">Kapcsolatok</span><span class="sxs-lookup"><span data-stu-id="a6209-159">Relationships</span></span>
- <span data-ttu-id="a6209-160">Tevékenységek</span><span class="sxs-lookup"><span data-stu-id="a6209-160">Activities</span></span>
- <span data-ttu-id="a6209-161">Keresési és szűrőindex</span><span class="sxs-lookup"><span data-stu-id="a6209-161">Search & filter Index</span></span>
- <span data-ttu-id="a6209-162">Exportálási célhelyek</span><span class="sxs-lookup"><span data-stu-id="a6209-162">Export destinations</span></span>
- <span data-ttu-id="a6209-163">Ütemezett frissítés</span><span class="sxs-lookup"><span data-stu-id="a6209-163">Scheduled refresh</span></span>
- <span data-ttu-id="a6209-164">Bővítések</span><span class="sxs-lookup"><span data-stu-id="a6209-164">Enrichments</span></span>
- <span data-ttu-id="a6209-165">Modellkezelés</span><span class="sxs-lookup"><span data-stu-id="a6209-165">Model management</span></span>
- <span data-ttu-id="a6209-166">Szerepkör-hozzárendelések</span><span class="sxs-lookup"><span data-stu-id="a6209-166">Role assignments</span></span>

<span data-ttu-id="a6209-167">A következő konfigurációbeállítások *nincsenek* másolva:</span><span class="sxs-lookup"><span data-stu-id="a6209-167">The following settings are *not* copied:</span></span>

- <span data-ttu-id="a6209-168">Ügyfélprofilok.</span><span class="sxs-lookup"><span data-stu-id="a6209-168">Customer profiles.</span></span>
- <span data-ttu-id="a6209-169">Adatforrás hitelesítő adatai.</span><span class="sxs-lookup"><span data-stu-id="a6209-169">Data source credentials.</span></span> <span data-ttu-id="a6209-170">A hitelesítő adatokat meg kell adnia minden adatforráshoz, és manuálisan kell frissítenie az adatforrásokat.</span><span class="sxs-lookup"><span data-stu-id="a6209-170">You'll have to provide the credentials for every data source and refresh the data sources manually.</span></span>
- <span data-ttu-id="a6209-171">Adatforrások a Common Data Model mappából és a Common Data Service felügyelt tóból.</span><span class="sxs-lookup"><span data-stu-id="a6209-171">Data sources from Common Data Model folder and Common Data Service managed lake.</span></span> <span data-ttu-id="a6209-172">Ezeket az adatforrásokat manuálisan, ugyanolyan néven kell létrehoznia, mint a forráskörnyezetében.</span><span class="sxs-lookup"><span data-stu-id="a6209-172">You'll have to create those data sources manually with the same name as in the source environment.</span></span>

<span data-ttu-id="a6209-173">Környezet másolásakor egy megerősítő üzenet jelenik meg, amely szerint létrejött az új környezet.</span><span class="sxs-lookup"><span data-stu-id="a6209-173">When you copy an environment, you'll see a confirmation message that the new environment has been created.</span></span> <span data-ttu-id="a6209-174">Válassza az **Ugrás az adatforrásokhoz** lehetőséget az adatforrások listájának megjelenítéséhez.</span><span class="sxs-lookup"><span data-stu-id="a6209-174">Select **Go to data sources** to see the list of data sources.</span></span>

<span data-ttu-id="a6209-175">Minden adatforrásnál megjelenik egy **Hitelesítő adatok szükségesek** állapot.</span><span class="sxs-lookup"><span data-stu-id="a6209-175">All the data sources will show a **Credentials Required** status.</span></span> <span data-ttu-id="a6209-176">Szerkessze az adatforrásokat, és adja meg a hitelesítő adatokat a frissítésükhöz.</span><span class="sxs-lookup"><span data-stu-id="a6209-176">Edit the data sources and enter the credentials to refresh them.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="a6209-177">![Másolt adatforrások](media/data-sources-copied.png)</span><span class="sxs-lookup"><span data-stu-id="a6209-177">![Data sources copied](media/data-sources-copied.png)</span></span>

<span data-ttu-id="a6209-178">Az adatforrások frissítését követően nyissa meg az **Adatok** > **Egyesítés** pontot.</span><span class="sxs-lookup"><span data-stu-id="a6209-178">After refreshing the data sources, go to **Data** > **Unify**.</span></span> <span data-ttu-id="a6209-179">Itt megtalálja a beállításokat a forráskörnyezetből.</span><span class="sxs-lookup"><span data-stu-id="a6209-179">Here you'll find settings from the source environment.</span></span> <span data-ttu-id="a6209-180">Igény szerint szerkessze őket, vagy válassza a **Futtatás** lehetőséget az adategyesítési folyamat elindításához, és hozzon létre egy egyesített ügyfélentitást.</span><span class="sxs-lookup"><span data-stu-id="a6209-180">Edit them as needed or select **Run** to start the data unification process and create the unified customer entity.</span></span>

<span data-ttu-id="a6209-181">Amikor az adatok egyesítése befejeződött, nyissa meg a **Mértékek** és a **Szegmensek** lehetőséget, hogy azokat is frissítse.</span><span class="sxs-lookup"><span data-stu-id="a6209-181">When the data unification is complete, go to **Measures** and **Segments** to refresh them too.</span></span>

## <a name="edit-an-existing-environment"></a><span data-ttu-id="a6209-182">Egy meglévő környezet szerkesztése</span><span class="sxs-lookup"><span data-stu-id="a6209-182">Edit an existing environment</span></span>

<span data-ttu-id="a6209-183">A meglévő környezetek bizonyos részleteit szerkesztheti.</span><span class="sxs-lookup"><span data-stu-id="a6209-183">You can edit some of the details of existing environments.</span></span>

1.  <span data-ttu-id="a6209-184">Válassza ki az alkalmazás fejlécében a **Környezet** választót.</span><span class="sxs-lookup"><span data-stu-id="a6209-184">Select the **Environment** picker in the header of the app.</span></span>

2.  <span data-ttu-id="a6209-185">Kattintson a **Szerkesztés** ikonra.</span><span class="sxs-lookup"><span data-stu-id="a6209-185">Select the **Edit** icon.</span></span>

3. <span data-ttu-id="a6209-186">A **Környezet szerkesztése** mezőben frissítheti a környezet **Megejelenő nevét**, de a **Régió** vagy a **Típus** nem módosítható.</span><span class="sxs-lookup"><span data-stu-id="a6209-186">In the **Edit environment** box, you can update the environment's **Display name**, but you can't change the **Region** or **Type**.</span></span>

4. <span data-ttu-id="a6209-187">Ha egy környezet úgy van beállítva, hogy az Azure Data Lake Storage Gen2-ben tárolja az adatokat, akkor frissítheti a **Fiókkulcsot**.</span><span class="sxs-lookup"><span data-stu-id="a6209-187">If an environment is configured to store data in Azure Data Lake Storage Gen2, you can update the **Account key**.</span></span> <span data-ttu-id="a6209-188">A **partner neve** vagy a **tároló** neve azonban nem módosítható.</span><span class="sxs-lookup"><span data-stu-id="a6209-188">However, you can't change the **Account name** or **Container** name.</span></span>

5. <span data-ttu-id="a6209-189">Lehetőség van arra, hogy a fiókkulcs-alapú kapcsolatot az erőforrás- vagy előfizetés-alapú kapcsolatra is frissítheti.</span><span class="sxs-lookup"><span data-stu-id="a6209-189">Optionally, you can update from an account key based connection to a resource-based or subscription-based connection.</span></span> <span data-ttu-id="a6209-190">A frissítést követően a frissítés után nem térhet vissza a fiókkulcshoz.</span><span class="sxs-lookup"><span data-stu-id="a6209-190">Once upgraded, you cannot revert to account key after the update.</span></span> <span data-ttu-id="a6209-191">További információkért lásd: [Célközönség-információk összekapcsolása az Azure Data Lake Storage Gen2 fiókjához az Azure egyszerű szolgáltatásnévvel](connect-service-principal.md).</span><span class="sxs-lookup"><span data-stu-id="a6209-191">For more information, see [Connect audience insights to an Azure Data Lake Storage Gen2 account with an Azure service principal](connect-service-principal.md).</span></span> <span data-ttu-id="a6209-192">A kapcsolat frissítésekor a **Tárolóra** vonatkozó információk nem módosíthatók.</span><span class="sxs-lookup"><span data-stu-id="a6209-192">You can't change **Container** information when updating the connection.</span></span>

6. <span data-ttu-id="a6209-193">Tetszés szerint megadhat egy Microsoft Dataverse környezet URL-címet az **Adatok megosztásának konfigurálása Microsoft Dataverseszel, és további képességek engedélyezése** alatt.</span><span class="sxs-lookup"><span data-stu-id="a6209-193">Optionally, you can provide a Microsoft Dataverse environment URL under **Configure data sharing with Microsoft Dataverse and enable additional capabilities**.</span></span> <span data-ttu-id="a6209-194">Ezek a lehetőségek olyan alkalmazások és megoldások használatával való adatmegosztásra használhatók, amelyek Microsoft Dataverse-en, helyszíni adatforrásból származó adatokon vagy a használat [előrejelzéseken](predictions.md) alapulnak.</span><span class="sxs-lookup"><span data-stu-id="a6209-194">These capabilities include data sharing with applications and solutions based on Microsoft Dataverse, data ingestion from on-premises data sources, or the use [predictions](predictions.md).</span></span> <span data-ttu-id="a6209-195">Válassza az **Adatmegosztás engedélyezése** lehetőséget, ha meg szeretné osztani a Customer Insights kimeneti adatait a Microsoft Dataverse Managed Data Lake használatával.</span><span class="sxs-lookup"><span data-stu-id="a6209-195">Select **Enable data sharing** to share Customer Insights output data with a Microsoft Dataverse Managed Data lake.</span></span>

   > [!NOTE]
   > - <span data-ttu-id="a6209-196">A Microsoft Dataverse Managed Data Lake használatával való adatmegosztás jelenleg nem támogatott, ha az adatokat a saját Azure Data Lake Storage tárhelyére menti.</span><span class="sxs-lookup"><span data-stu-id="a6209-196">Data sharing with Microsoft Dataverse Managed Data Lake is currently not supported when you save all data to your own Azure Data Lake Storage.</span></span>
   > - <span data-ttu-id="a6209-197">[Entitásból hiányzó értékek előrejelzése](predictions.md) jelenleg nem támogatott, ha engedélyezi az adatok megosztását a Microsoft Dataverse Managed Data Lake szolgáltatással.</span><span class="sxs-lookup"><span data-stu-id="a6209-197">[Prediction of missing values in an entity](predictions.md) is currently not supported when you enable data sharing with Microsoft Dataverse Managed Data Lake.</span></span>

   <span data-ttu-id="a6209-198">Miután engedélyezi az adatok megosztását a Microsoft Dataverse-szel, az adatforrások és más folyamatok egyszeri teljes frissítése elkezdődik.</span><span class="sxs-lookup"><span data-stu-id="a6209-198">After enabling data sharing with Microsoft Dataverse, a full refresh of your data sources and other processes starts.</span></span> <span data-ttu-id="a6209-199">Ha folyamatok futnak és, akkor nem fogja látni a lehetőséget, amelltel engedélyezhetné az adatok megosztását a Microsoft Dataverse-szel.</span><span class="sxs-lookup"><span data-stu-id="a6209-199">If processes are currently running, you don't see the option to enable data sharing with Microsoft Dataverse.</span></span> <span data-ttu-id="a6209-200">Az adatmegosztás engedélyezéséhez várja meg, amíg befejeződnek vagy visszavonják ezeket a folyamatokat.</span><span class="sxs-lookup"><span data-stu-id="a6209-200">Wait for those processes to complete or cancel them to enable data sharing.</span></span> 
   
   :::image type="content" source="media/datasharing-with-DataverseMDL.png" alt-text="Konfigurálási lehetőségek az adatmegosztás engedélyezéséhez a Microsoft Dataverse szolgáltatással.":::
   
   <span data-ttu-id="a6209-202">A folyamatok – például adatbetöltés vagy szegmenslétrehozás – futtatásakor a megfelelő mappák létrejönnek a fent megadott tárfiókban.</span><span class="sxs-lookup"><span data-stu-id="a6209-202">When you run processes, such as data ingestion or segment creation, corresponding folders will be created in the storage account you specified above.</span></span> <span data-ttu-id="a6209-203">A rendszer a futtatott folyamattól függően adatfájlokat és model.json fájlokat hoz létre, és ad hozzá a megfelelő almappákhoz.</span><span class="sxs-lookup"><span data-stu-id="a6209-203">Data files and model.json files will be created and added to the respective subfolders, depending on the process you run.</span></span>

## <a name="reset-an-existing-environment"></a><span data-ttu-id="a6209-204">Meglévő környezet visszaállítása</span><span class="sxs-lookup"><span data-stu-id="a6209-204">Reset an existing environment</span></span>

<span data-ttu-id="a6209-205">Rendszergazdaként a környezetet visszaállíthatja üres állapotba, ha szeretné törölni az összes konfigurációt, és eltávolítani a betöltött adatokat.</span><span class="sxs-lookup"><span data-stu-id="a6209-205">As an administrator, you can reset an environment to an empty state if you want to delete all configurations and remove the ingested data.</span></span>

1.  <span data-ttu-id="a6209-206">Válassza ki az alkalmazás fejlécében a **Környezet** választót.</span><span class="sxs-lookup"><span data-stu-id="a6209-206">Select the **Environment** picker in the header of the app.</span></span> 

2.  <span data-ttu-id="a6209-207">Válassza ki az alaphelyzetbe állítani kívánt környezetet, és válassza ki a három pontot **...**.</span><span class="sxs-lookup"><span data-stu-id="a6209-207">Select the environment you want to reset and select the ellipsis **...**.</span></span> 

3. <span data-ttu-id="a6209-208">Válassza az **Alaphelyzetbe állítás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="a6209-208">Choose the **Reset** option.</span></span> 

4.  <span data-ttu-id="a6209-209">A törlés jóváhagyásához írja be a környezet nevét, és válassza az **Alaphelyzetbe állítás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="a6209-209">To confirm the deletion, enter the environment name and select **Reset**.</span></span>

## <a name="delete-an-existing-environment-available-only-for-admins"></a><span data-ttu-id="a6209-210">Meglévő környezet törlése (csak rendszergazdák számára érhető el)</span><span class="sxs-lookup"><span data-stu-id="a6209-210">Delete an existing environment (available only for admins)</span></span>

<span data-ttu-id="a6209-211">Rendszergazdaként törölheti az Ön által felügyelt környezetet.</span><span class="sxs-lookup"><span data-stu-id="a6209-211">As an administrator, you can delete an environment you administer.</span></span>

1.  <span data-ttu-id="a6209-212">Válassza ki az alkalmazás fejlécében a **Környezet** választót.</span><span class="sxs-lookup"><span data-stu-id="a6209-212">Select the **Environment** picker in the header of the app.</span></span>

2.  <span data-ttu-id="a6209-213">Válassza ki az alaphelyzetbe állítani kívánt környezetet, és válassza ki a három pontot **...**.</span><span class="sxs-lookup"><span data-stu-id="a6209-213">Select the environment you want to reset and select the ellipsis **...**.</span></span> 

3. <span data-ttu-id="a6209-214">Válassza a **Törlés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="a6209-214">Choose the **Delete** option.</span></span> 

4.  <span data-ttu-id="a6209-215">A törlés jóváhagyásához adja meg a környezet nevét, és válassza a **Törlés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="a6209-215">To confirm the deletion, enter the environment name and select **Delete**.</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]
