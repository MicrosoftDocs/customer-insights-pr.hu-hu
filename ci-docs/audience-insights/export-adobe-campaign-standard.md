---
title: A Customer Insights adatainak exportálása az Adobe Campaign Standardba
description: Ismerje meg, hogyan használhatja a célközönség-infomációs szegmenseket az Adobe Campaign Standardban.
ms.date: 03/29/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: stefanie-msft
ms.author: antando
manager: shellyha
ms.openlocfilehash: b6c010d84119c2fa8b3ef99017c65f9939bf28c4
ms.sourcegitcommit: 1b671c6100991fea1cace04b5d4fcedcd88aa94f
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/31/2021
ms.locfileid: "5760284"
---
# <a name="use-customer-insights-segments-in-adobe-campaign-standard-preview"></a><span data-ttu-id="0f98e-103">A Customer Insights-szegmensek használata az Adobe Campaign Standardban (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="0f98e-103">Use Customer Insights segments in Adobe Campaign Standard (preview)</span></span>

<span data-ttu-id="0f98e-104">A Dynamics 365 Customer Insights célközönség-információinak felhasználójaként létrehozott szegmenseket, hogy a marketingkampányok hatékonyságát növelje a releváns célközönségek megcélzásával.</span><span class="sxs-lookup"><span data-stu-id="0f98e-104">As a user of audience insights for Dynamics 365 Customer Insights, you may have created segments to make your marketing campaigns more efficient by targeting relevant audiences.</span></span> <span data-ttu-id="0f98e-105">Az Adobe Experience Platformban és az Adobe Campaign Standardhoz hasonló alkalmazásokban található célközönség-információs szegmensek használatához a jelen cikkben ismertetett lépéseket kell követnie.</span><span class="sxs-lookup"><span data-stu-id="0f98e-105">To use a segment from audience insights in Adobe Experience Platform and applications like Adobe Campaign Standard, you need to follow a few steps outlined in this article.</span></span>

:::image type="content" source="media/ACS-flow.png" alt-text="A jelen cikkben ismertetett lépések folyamatábrája.":::

## <a name="prerequisites"></a><span data-ttu-id="0f98e-107">Előfeltételek</span><span class="sxs-lookup"><span data-stu-id="0f98e-107">Prerequisites</span></span>

-   <span data-ttu-id="0f98e-108">Dynamics 365 Customer Insights licenc</span><span class="sxs-lookup"><span data-stu-id="0f98e-108">Dynamics 365 Customer Insights license</span></span>
-   <span data-ttu-id="0f98e-109">Adobe Campaign Standard-licenc</span><span class="sxs-lookup"><span data-stu-id="0f98e-109">Adobe Campaign Standard license</span></span>
-   <span data-ttu-id="0f98e-110">Azure Blob Storage-fiók</span><span class="sxs-lookup"><span data-stu-id="0f98e-110">Azure Blob Storage account</span></span>

## <a name="campaign-overview"></a><span data-ttu-id="0f98e-111">Kampány áttekintése</span><span class="sxs-lookup"><span data-stu-id="0f98e-111">Campaign Overview</span></span>

<span data-ttu-id="0f98e-112">Hogy jobban meg tudja érteni, hogyan használhatja a célközönség-információs szegmenseket az Adobe Experience Platformban, tekintsünk át egy kitalált mintakampányt.</span><span class="sxs-lookup"><span data-stu-id="0f98e-112">To better understand how you can use segments from audience insights in Adobe Experience Platform, let’s look at a fictitious sample campaign.</span></span>

<span data-ttu-id="0f98e-113">Tegyük fel, hogy a vállalata havi előfizetéses szolgáltatást kínál egyesült államokbeli ügyfeleinek.</span><span class="sxs-lookup"><span data-stu-id="0f98e-113">Let’s assume that your company offers a monthly, subscription-based service to your customers in the United States.</span></span> <span data-ttu-id="0f98e-114">Meg szeretné határozni azokat az ügyfeleket, akiknek az előfizetései a következő nyolc napban megújításra esedékesek, de még nem újították meg előfizetésüket.</span><span class="sxs-lookup"><span data-stu-id="0f98e-114">You want to identify customers whose subscriptions are due for renewal in the next eight days but haven't yet renewed their subscription.</span></span> <span data-ttu-id="0f98e-115">Ezeknek az ügyfeleknek a megtartása érdekében e-mailben szeretne promóciós ajánlatot küldeni nekik az Adobe Campaign Standard segítségével.</span><span class="sxs-lookup"><span data-stu-id="0f98e-115">To keep these customers, you want to send them a promotional offer via email, using Adobe Campaign Standard.</span></span>

<span data-ttu-id="0f98e-116">Ebben a példában egy promóciós e-mail-kampányt egyszer szeretnénk futtatni.</span><span class="sxs-lookup"><span data-stu-id="0f98e-116">In this example, we want to run the promotional email campaign once.</span></span> <span data-ttu-id="0f98e-117">Ez a cikk nem terjed ki a kampány egynél több esetben való futtatásának esetére.</span><span class="sxs-lookup"><span data-stu-id="0f98e-117">This article doesn’t cover the use-case of running the campaign more than once.</span></span> <span data-ttu-id="0f98e-118">A célközönség-információk és az Adobe Campaign Standard azonban beállítható úgy is, hogy ismétlődő kampány esetén is működjön.</span><span class="sxs-lookup"><span data-stu-id="0f98e-118">However, audience insights and Adobe Campaign Standard can be configured to work for a recurring campaign scenario too.</span></span>

## <a name="identify-your-target-audience"></a><span data-ttu-id="0f98e-119">Azonosítsa a célközönséget</span><span class="sxs-lookup"><span data-stu-id="0f98e-119">Identify your target audience</span></span>

<span data-ttu-id="0f98e-120">A mi esetünkben feltételezzük, hogy az ügyfelek e-mail-címei elérhetők a célközönség-információkban, és promóciós preferenciáik elemzésével azonosítottuk a szegmens tagjait.</span><span class="sxs-lookup"><span data-stu-id="0f98e-120">In our scenario, we assume that the email addresses of the customers are available in audience insights and their promotional preferences were analyzed to identify members of the segment.</span></span>

<span data-ttu-id="0f98e-121">A [célközönség-információkban meghatározott szegmens](segments.md) neve **ChurnProneCustomers**, és az e-mail-promóció elküldését tervezi ezeknek az ügyfeleknek.</span><span class="sxs-lookup"><span data-stu-id="0f98e-121">The [segment you defined in audience insights](segments.md) is called **ChurnProneCustomers** and you plan to send these customers the email promotion.</span></span>

:::image type="content" source="media/churn-prone-customers-segment.png" alt-text="Képernyőfelvétel a Szegmensek oldalról, amelyen a létrehozott ChurnProneCustomers szegmens látható.":::

<span data-ttu-id="0f98e-123">Az elküldeni kívánt ajánlati e-mail tartalmazza az ügyfél utónevét, vezetéknevét és az előfizetés záró dátumát.</span><span class="sxs-lookup"><span data-stu-id="0f98e-123">The offer email that you want to send out will contain the first name, last name, and the subscription end date of the customer.</span></span> <span data-ttu-id="0f98e-124">Tájékoztatja az ügyfeleket az arról az engedményről, amit akkor kapnak, ha a vége előtt megújítják az előfizetésüket.</span><span class="sxs-lookup"><span data-stu-id="0f98e-124">It informs the customers about the discount they’ll get if they renew their subscription before it ends.</span></span>

## <a name="export-your-target-audience"></a><span data-ttu-id="0f98e-125">Exportálja a célközönséget</span><span class="sxs-lookup"><span data-stu-id="0f98e-125">Export your target audience</span></span>

### <a name="configure-a-connection"></a><span data-ttu-id="0f98e-126">Kapcsolat konfigurálása</span><span class="sxs-lookup"><span data-stu-id="0f98e-126">Configure a connection</span></span>

<span data-ttu-id="0f98e-127">Az azonosított célközönség segítségével konfigurálható az exportálás az célközönség-információkból egy Azure Blob Storage-fiókba.</span><span class="sxs-lookup"><span data-stu-id="0f98e-127">With our target audience identified, we can configure the export from audience insights to an Azure Blob Storage account.</span></span>

1. <span data-ttu-id="0f98e-128">A célközönség információkban menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="0f98e-128">In audience insights, go to **Admin** > **Connections**.</span></span>

1. <span data-ttu-id="0f98e-129">Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza az **Adobe Campaign** lehetőséget a kapcsolat konfigurálához, vagy válassza a **Beállítás** lehetőséget az **Adobe Campaign** csempén</span><span class="sxs-lookup"><span data-stu-id="0f98e-129">Select **Add connection** and choose **Adobe Campaign** to configure the connection or select **Set up** in the **Adobe Campaign** tile</span></span>

   :::image type="content" source="media/adobe-campaign-standard-tile.png" alt-text="Az Adobe Campaign Standard konfigurációs csempéje.":::

1. <span data-ttu-id="0f98e-131">Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak.</span><span class="sxs-lookup"><span data-stu-id="0f98e-131">Give your connection a recognizable name in the **Display name** field.</span></span> <span data-ttu-id="0f98e-132">A név és a kapcsolat típusa írja le ezt a kapcsolatot.</span><span class="sxs-lookup"><span data-stu-id="0f98e-132">The name and the type of the connection describe this connection.</span></span> <span data-ttu-id="0f98e-133">Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.</span><span class="sxs-lookup"><span data-stu-id="0f98e-133">We recommend choosing a name that explains the purpose and target of the connection.</span></span>

1. <span data-ttu-id="0f98e-134">A kapcsolat használóinak kiválasztása.</span><span class="sxs-lookup"><span data-stu-id="0f98e-134">Choose who can use this connection.</span></span> <span data-ttu-id="0f98e-135">Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz.</span><span class="sxs-lookup"><span data-stu-id="0f98e-135">If you take no action, the default will be Administrators.</span></span> <span data-ttu-id="0f98e-136">További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).</span><span class="sxs-lookup"><span data-stu-id="0f98e-136">For more information, see [Permissions needed to configure an export](export-destinations.md#set-up-a-new-export).</span></span>

1. <span data-ttu-id="0f98e-137">Adja meg annak az Azure Blob Storage fióknak a **Fiók nevét**, **Fiókkulcsát** és **Tárolóját**, ahová exportálni szeretné a szegmenst.</span><span class="sxs-lookup"><span data-stu-id="0f98e-137">Enter the **Account name**, **Account key**, and **Container** of the Azure Blob Storage account where you want to export the segment to.</span></span>  
      
   :::image type="content" source="media/azure-blob-configuration.png" alt-text="Képernyőkép a tárfiók konfigurációjáról."::: 

   - <span data-ttu-id="0f98e-139">Az Azure Blob Storage fióknév és fiókkulcs megkeresésével kapcsolatos további tudnivalókat lásd: [A tárolófiók beállításainak kezelése az Azure Portal webhelyen](/azure/storage/common/storage-account-manage).</span><span class="sxs-lookup"><span data-stu-id="0f98e-139">To learn more about how to find the Azure Blob storage account name and account key, see [Manage storage account settings in the Azure portal](/azure/storage/common/storage-account-manage).</span></span>

   - <span data-ttu-id="0f98e-140">A tároló létrehozásával kapcsolatosan lásd: [Tároló létrehozása](/azure/storage/blobs/storage-quickstart-blobs-portal#create-a-container).</span><span class="sxs-lookup"><span data-stu-id="0f98e-140">To learn how to create a container, see [Create a container](/azure/storage/blobs/storage-quickstart-blobs-portal#create-a-container).</span></span>

1. <span data-ttu-id="0f98e-141">A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="0f98e-141">Select **Save** to complete the connection.</span></span>

### <a name="configure-an-export"></a><span data-ttu-id="0f98e-142">Exportálás konfigurálása</span><span class="sxs-lookup"><span data-stu-id="0f98e-142">Configure an export</span></span>

<span data-ttu-id="0f98e-143">Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz.</span><span class="sxs-lookup"><span data-stu-id="0f98e-143">You can configure this export if you have access to a connection of this type.</span></span> <span data-ttu-id="0f98e-144">További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).</span><span class="sxs-lookup"><span data-stu-id="0f98e-144">For more information, see [Permissions needed to configure an export](export-destinations.md#set-up-a-new-export).</span></span>

1. <span data-ttu-id="0f98e-145">Menjen az **Adatok** > **Exportálások** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="0f98e-145">Go to **Data** > **Exports**.</span></span>

1. <span data-ttu-id="0f98e-146">Új exportálás létrehozásához válassza az **Exportálás hozzáadása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="0f98e-146">To create a new export, select **Add export**.</span></span>

1. <span data-ttu-id="0f98e-147">A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot az Adobe Campaign szakaszból.</span><span class="sxs-lookup"><span data-stu-id="0f98e-147">In the **Connection for export** field, choose a connection from the Adobe Campaign section.</span></span> <span data-ttu-id="0f98e-148">Ha nem látja ezt a szakasznevet, az Ön számára nincs ilyen típusú kapcsolat.</span><span class="sxs-lookup"><span data-stu-id="0f98e-148">If you don't see this section name, there are no connections of this type available to you.</span></span>

1. <span data-ttu-id="0f98e-149">Válassza ki az exportálni kívánt szegmenst.</span><span class="sxs-lookup"><span data-stu-id="0f98e-149">Choose the segment that you want to export.</span></span> <span data-ttu-id="0f98e-150">Ebben a példában ez a **ChurnProneCustomers**.</span><span class="sxs-lookup"><span data-stu-id="0f98e-150">In this example, it’s **ChurnProneCustomers**.</span></span>

   :::image type="content" source="media/select-segment-churnpronecustomers.png" alt-text="Képernyőkép a szegmenskijelölési felhasználói felületről, ahol a ChurnProneCustomers szegmens ki van választva.":::

1. <span data-ttu-id="0f98e-152">Válassza a **Következő** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="0f98e-152">Select **Next**.</span></span>

1. <span data-ttu-id="0f98e-153">Most leképezzük a célközönség-információk szegmens **Forrás** mezőit az Adobe Campaign Standard profilsémában szereplő **Cél** mezők neveire.</span><span class="sxs-lookup"><span data-stu-id="0f98e-153">Now we map the **Source** fields from the audience insights segment to the **Target** field names in the Adobe Campaign Standard profile schema.</span></span>

   :::image type="content" source="media/ACS-field-mapping.png" alt-text="Az Adobe Campaign Standard-összekötő mezőleképezése.":::

   <span data-ttu-id="0f98e-155">Ha további attribútumokat szeretne hozzáadni, válassza az **Attribútum hozzáadása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="0f98e-155">If you want to add more attributes, select **Add attribute**.</span></span> <span data-ttu-id="0f98e-156">A cél neve nem lehet azonos a forrásmező nevével, így továbbra is leképezheti a célközönség-információkból származó szegmens kimenetét az Adobe Campaign Standard szolgáltatásba, ha mezőknek a két rendszerben nem ugyanaz a neve.</span><span class="sxs-lookup"><span data-stu-id="0f98e-156">The target name can be different from the source field name so you can still map segment output from audience insights to Adobe Campaign Standard if the fields don’t have the same name in the two systems.</span></span>

   > [!NOTE]
   > <span data-ttu-id="0f98e-157">Az e-mail-címet identitásmezőként használja a rendszer, de a célközönség-információk ügyfélprofil egyéb azonosítói segítségével az adatokat leképezheti az Adobe Campaign Standardra.</span><span class="sxs-lookup"><span data-stu-id="0f98e-157">Email address is used as an identity field but you can use any other identifier from your audience insights customer profile to map data to Adobe Campaign Standard.</span></span>

1. <span data-ttu-id="0f98e-158">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="0f98e-158">Select **Save**.</span></span>

<span data-ttu-id="0f98e-159">Az exportálási cél mentése után az **Adatok** > **Exportálások** lehetőségnél található.</span><span class="sxs-lookup"><span data-stu-id="0f98e-159">After saving the export destination, you find it on **Data** > **Exports**.</span></span>

<span data-ttu-id="0f98e-160">Mostantól [igény szerint exportálhatja a szegmenst](export-destinations.md#run-exports-on-demand).</span><span class="sxs-lookup"><span data-stu-id="0f98e-160">You can now [export the segment on demand](export-destinations.md#run-exports-on-demand).</span></span> <span data-ttu-id="0f98e-161">Az exportálás minden [ütemezett frissítéssel](system.md) együtt is lefut.</span><span class="sxs-lookup"><span data-stu-id="0f98e-161">The export will also run with every [scheduled refresh](system.md).</span></span>

> [!NOTE]
> <span data-ttu-id="0f98e-162">Győződjön meg róla, hogy az exportált szegmens rekordjainak száma az Adobe Campaign Standard licencének megengedett korlátjan belül van.</span><span class="sxs-lookup"><span data-stu-id="0f98e-162">Ensure that the number of records in the exported segment are within the allowed limit of your Adobe Campaign Standard license.</span></span>

<span data-ttu-id="0f98e-163">Az exportált adatokat a rendszer a fent beállított Azure Blob Storage-tárolóban tárolja.</span><span class="sxs-lookup"><span data-stu-id="0f98e-163">Exported data is stored in the Azure Blob storage container you configured above.</span></span> <span data-ttu-id="0f98e-164">A következő mappa elérési útja automatikusan létrejön a tárolóban:</span><span class="sxs-lookup"><span data-stu-id="0f98e-164">The following folder path is automatically created in your container:</span></span>

<span data-ttu-id="0f98e-165">*%ContainerName%/CustomerInsights_%instanceID%/% exportdestination-name%_%segmentname%_%timestamp%.csv*</span><span class="sxs-lookup"><span data-stu-id="0f98e-165">*%ContainerName%/CustomerInsights_%instanceID%/% exportdestination-name%_%segmentname%_%timestamp%.csv*</span></span>

<span data-ttu-id="0f98e-166">Példa: Dynamics365CustomerInsights/CustomerInsights_abcd1234-4312-11f4-93dc-24f72f43e7d5/ChurnSegmentDemo_ChurnProneCustomers_1613059542.csv</span><span class="sxs-lookup"><span data-stu-id="0f98e-166">Example: Dynamics365CustomerInsights/CustomerInsights_abcd1234-4312-11f4-93dc-24f72f43e7d5/ChurnSegmentDemo_ChurnProneCustomers_1613059542.csv</span></span>

## <a name="configure-adobe-campaign-standard"></a><span data-ttu-id="0f98e-167">Adobe Campaign Standard konfigurálása</span><span class="sxs-lookup"><span data-stu-id="0f98e-167">Configure Adobe Campaign Standard</span></span>

<span data-ttu-id="0f98e-168">Ha egy szegmenst exportál célközönség-információkból, akkor az előző lépésben az exportálási cél meghatározása során kiválasztott oszlopokat tartalmazza.</span><span class="sxs-lookup"><span data-stu-id="0f98e-168">When a segment from audience insights is exported, it contains the columns you selected while defining the export destination in the previous step.</span></span> <span data-ttu-id="0f98e-169">Ezek az adatok használhatók [profilok létrehozásához az Adobe Campaign Standardban](https://experienceleague.adobe.com/docs/campaign-standard/using/profiles-and-audiences/managing-profiles/about-profiles.html#managing-profiles).</span><span class="sxs-lookup"><span data-stu-id="0f98e-169">This data can be used to [create profiles in Adobe Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard/using/profiles-and-audiences/managing-profiles/about-profiles.html#managing-profiles).</span></span>

<span data-ttu-id="0f98e-170">A szegmens az Adobe Campaign Standardban való használata esetén két további mezőre is ki kell bővítenünk a profilsémát az Adobe Campaign Standardban.</span><span class="sxs-lookup"><span data-stu-id="0f98e-170">To use the segment in Adobe Campaign Standard, we need to extend the profile schema in Adobe Campaign Standard to include two additional fields.</span></span> <span data-ttu-id="0f98e-171">Ismerje meg, hogyan [bővítheti a profilerőforrást](https://experienceleague.adobe.com/docs/campaign-standard/using/developing/use-cases--extending-resources/extending-the-profile-resource-with-a-new-field.html#developing) az Adobe Campaign Standard új mezőivel.</span><span class="sxs-lookup"><span data-stu-id="0f98e-171">Learn how to [extend the profile resource](https://experienceleague.adobe.com/docs/campaign-standard/using/developing/use-cases--extending-resources/extending-the-profile-resource-with-a-new-field.html#developing) with new fields in Adobe Campaign Standard.</span></span>

<span data-ttu-id="0f98e-172">A példában ezek a mezők a *Szegmens neve és a Szegmens dátuma (nem kötelező).*</span><span class="sxs-lookup"><span data-stu-id="0f98e-172">In our example, these fields are *Segment Name and Segment Date (optional).*</span></span>

<span data-ttu-id="0f98e-173">Ezeket a mezőket arra használjuk, hogy azonosítsuk a kampányhoz megcélozni kívánt Adobe Campaign Standard-profilokat.</span><span class="sxs-lookup"><span data-stu-id="0f98e-173">We will use these fields to identify the profiles in Adobe Campaign Standard we want to target for this campaign.</span></span>

<span data-ttu-id="0f98e-174">Ha az Adobe Campaign Standardban nincs más rekord, mint amit importálni fog, ezt a lépést kihagyhatja.</span><span class="sxs-lookup"><span data-stu-id="0f98e-174">If there are no other records in Adobe Campaign Standard, other than what you are going to import, you can skip this step.</span></span>

## <a name="import-data-into-adobe-campaign-standard"></a><span data-ttu-id="0f98e-175">Adatok importálása az Adobe Campaign Standard programba</span><span class="sxs-lookup"><span data-stu-id="0f98e-175">Import data into Adobe Campaign Standard</span></span>

<span data-ttu-id="0f98e-176">Most, hogy minden a helyén van, a profilok létrehozásához importálni kell az előkészített célközönségadatokat az célközönség-információkból az Adobe Campaign Standardba.</span><span class="sxs-lookup"><span data-stu-id="0f98e-176">Now that everything is in place, we need to import the prepared audience data from audience insights into Adobe Campaign Standard to create profiles.</span></span> <span data-ttu-id="0f98e-177">Ismerje meg, [hogyan importálhat profilokat az Adobe Campaign Standardba](https://experienceleague.adobe.com/docs/campaign-standard/using/profiles-and-audiences/managing-profiles/creating-profiles.html#profiles-and-audiences) munkafolyamatok használatával.</span><span class="sxs-lookup"><span data-stu-id="0f98e-177">Learn [how to import profiles in Adobe Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard/using/profiles-and-audiences/managing-profiles/creating-profiles.html#profiles-and-audiences) using a workflow.</span></span>

<span data-ttu-id="0f98e-178">Az alábbi képen az importálási munkafolyamat 8 óránként fut, és exportált célközönség-információs szegmensek (.csv fájl az Azure Blob Storage-ban) után kutat.</span><span class="sxs-lookup"><span data-stu-id="0f98e-178">The import workflow in the image below has been configured to run every 8 hours and looks for exported audience insights segments (.csv file in Azure Blob Storage).</span></span> <span data-ttu-id="0f98e-179">A munkafolyamat meghatározott oszloprendben bontja ki a .csv fájl tartalmát.</span><span class="sxs-lookup"><span data-stu-id="0f98e-179">The workflow extracts the .csv file content in a specified column order.</span></span> <span data-ttu-id="0f98e-180">Ez a munkafolyamat az alapvető hibakezelés végrehajtásához készült, és biztosítja, hogy minden rekordhoz tartozzon e-mail-cím, mielőtt az adatokat átveszi az Adobe Campaign Standardban.</span><span class="sxs-lookup"><span data-stu-id="0f98e-180">This workflow has been built to perform basic error handling and ensure that each record has an email address before hydrating the data in Adobe Campaign Standard.</span></span> <span data-ttu-id="0f98e-181">A munkafolyamat ki is bontja a szegmens nevét a fájlnévből, mielőtt az ACS-profiladatokba upsertelné.</span><span class="sxs-lookup"><span data-stu-id="0f98e-181">The workflow also extracts the segment name from the filename before upserting into ACS Profile data.</span></span>

:::image type="content" source="media/ACS-import-workflow.png" alt-text="Képernyőkép az importálási munkafolyamatról az Adobe Campaign Standard felhasználói felületén.":::

## <a name="retrieve-the-audience-in-adobe-campaign-standard"></a><span data-ttu-id="0f98e-183">A célközönség lekérése az Adobe Campaign Standardban</span><span class="sxs-lookup"><span data-stu-id="0f98e-183">Retrieve the audience in Adobe Campaign Standard</span></span>

<span data-ttu-id="0f98e-184">Miután megtörtént az adatok importálása az Adobe Campaign Standardba, [létrehozhat egy munkafolyamatot](https://experienceleague.adobe.com/docs/campaign-standard/using/managing-processes-and-data/workflow-general-operation/building-a-workflow.html#managing-processes-and-data), és [lekérdezheti](https://experienceleague.adobe.com/docs/campaign-standard/using/managing-processes-and-data/targeting-activities/query.html#managing-processes-and-data) az ügyfeleket a *Szegmensnév* és *Szegmens dátuma* alapján, hogy kiválaszthassa a mintakampányhoz beazonosítótt profilokat.</span><span class="sxs-lookup"><span data-stu-id="0f98e-184">Once the data is imported into Adobe Campaign Standard, you [can create a workflow](https://experienceleague.adobe.com/docs/campaign-standard/using/managing-processes-and-data/workflow-general-operation/building-a-workflow.html#managing-processes-and-data) and [query](https://experienceleague.adobe.com/docs/campaign-standard/using/managing-processes-and-data/targeting-activities/query.html#managing-processes-and-data) the customers based on the *Segment Name* and *Segment Date* to select profiles that were identified for our sample campaign.</span></span>

## <a name="create-and-send-the-email-using-adobe-campaign-standard"></a><span data-ttu-id="0f98e-185">Az e-mail létrehozása és elküldése az Adobe Campaign Standard használatával</span><span class="sxs-lookup"><span data-stu-id="0f98e-185">Create and send the email using Adobe Campaign Standard</span></span>

<span data-ttu-id="0f98e-186">Hozza létre az e-mail tartalmát, majd [tesztelje, és küldje el](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/get-started-sending-messages.html#preparing-and-testing-messages) az e-mailt.</span><span class="sxs-lookup"><span data-stu-id="0f98e-186">Create the email content and then [test and send](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/get-started-sending-messages.html#preparing-and-testing-messages) your email.</span></span>

:::image type="content" source="media/contoso-sample-email.jpg" alt-text="E-mail minta az Adobe Campaign Standard megújítási ajánlatával.":::
