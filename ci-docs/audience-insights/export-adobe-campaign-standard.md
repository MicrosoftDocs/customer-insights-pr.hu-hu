---
title: A Customer Insights adatainak exportálása az Adobe Campaign Standardba
description: Ismerje meg, hogyan használhatja a célközönség-infomációs szegmenseket az Adobe Campaign Standardban.
ms.date: 02/26/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: stefanie-msft
ms.author: antando
manager: shellyha
ms.openlocfilehash: a5d0154c3d7c473dcba03fac0847bafcf97de2f2
ms.sourcegitcommit: bae40184312ab27b95c140a044875c2daea37951
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/15/2021
ms.locfileid: "5596318"
---
# <a name="use-customer-insights-segments-in-adobe-campaign-standard-preview"></a><span data-ttu-id="6cd6f-103">A Customer Insights-szegmensek használata az Adobe Campaign Standardban (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="6cd6f-103">Use Customer Insights segments in Adobe Campaign Standard (preview)</span></span>

<span data-ttu-id="6cd6f-104">A Dynamics 365 Customer Insights célközönség-információinak felhasználójaként létrehozott szegmenseket, hogy a marketingkampányok hatékonyságát növelje a releváns célközönségek megcélzásával.</span><span class="sxs-lookup"><span data-stu-id="6cd6f-104">As a user of audience insights for Dynamics 365 Customer Insights, you may have created segments to make your marketing campaigns more efficient by targeting relevant audiences.</span></span> <span data-ttu-id="6cd6f-105">Az Adobe Experience Platformban és az Adobe Campaign Standardhoz hasonló alkalmazásokban található célközönség-információs szegmensek használatához a jelen cikkben ismertetett lépéseket kell követnie.</span><span class="sxs-lookup"><span data-stu-id="6cd6f-105">To use a segment from audience insights in Adobe Experience Platform and applications like Adobe Campaign Standard, you need to follow a few steps outlined in this article.</span></span>

:::image type="content" source="media/ACS-flow.png" alt-text="A jelen cikkben ismertetett lépések folyamatábrája.":::

## <a name="prerequisites"></a><span data-ttu-id="6cd6f-107">Előfeltételek</span><span class="sxs-lookup"><span data-stu-id="6cd6f-107">Prerequisites</span></span>

-   <span data-ttu-id="6cd6f-108">Dynamics 365 Customer Insights licenc</span><span class="sxs-lookup"><span data-stu-id="6cd6f-108">Dynamics 365 Customer Insights license</span></span>
-   <span data-ttu-id="6cd6f-109">Adobe Campaign Standard-licenc</span><span class="sxs-lookup"><span data-stu-id="6cd6f-109">Adobe Campaign Standard license</span></span>
-   <span data-ttu-id="6cd6f-110">Azure Blob Storage-fiók</span><span class="sxs-lookup"><span data-stu-id="6cd6f-110">Azure Blob Storage account</span></span>

## <a name="campaign-overview"></a><span data-ttu-id="6cd6f-111">Kampány áttekintése</span><span class="sxs-lookup"><span data-stu-id="6cd6f-111">Campaign Overview</span></span>

<span data-ttu-id="6cd6f-112">Hogy jobban meg tudja érteni, hogyan használhatja a célközönség-információs szegmenseket az Adobe Experience Platformban, tekintsünk át egy kitalált mintakampányt.</span><span class="sxs-lookup"><span data-stu-id="6cd6f-112">To better understand how you can use segments from audience insights in Adobe Experience Platform, let’s look at a fictitious sample campaign.</span></span>

<span data-ttu-id="6cd6f-113">Tegyük fel, hogy a vállalata havi előfizetéses szolgáltatást kínál egyesült államokbeli ügyfeleinek.</span><span class="sxs-lookup"><span data-stu-id="6cd6f-113">Let’s assume that your company offers a monthly, subscription-based service to your customers in the United States.</span></span> <span data-ttu-id="6cd6f-114">Meg szeretné határozni azokat az ügyfeleket, akiknek az előfizetései a következő nyolc napban megújításra esedékesek, de még nem újították meg előfizetésüket.</span><span class="sxs-lookup"><span data-stu-id="6cd6f-114">You want to identify customers whose subscriptions are due for renewal in the next eight days but haven't yet renewed their subscription.</span></span> <span data-ttu-id="6cd6f-115">Ezeknek az ügyfeleknek a megtartása érdekében e-mailben szeretne promóciós ajánlatot küldeni nekik az Adobe Campaign Standard segítségével.</span><span class="sxs-lookup"><span data-stu-id="6cd6f-115">To keep these customers, you want to send them a promotional offer via email, using Adobe Campaign Standard.</span></span>

<span data-ttu-id="6cd6f-116">Ebben a példában egy promóciós e-mail-kampányt egyszer szeretnénk futtatni.</span><span class="sxs-lookup"><span data-stu-id="6cd6f-116">In this example, we want to run the promotional email campaign once.</span></span> <span data-ttu-id="6cd6f-117">Ez a cikk nem terjed ki a kampány egynél több esetben való futtatásának esetére.</span><span class="sxs-lookup"><span data-stu-id="6cd6f-117">This article doesn’t cover the use-case of running the campaign more than once.</span></span> <span data-ttu-id="6cd6f-118">A célközönség-információk és az Adobe Campaign Standard azonban beállítható úgy is, hogy ismétlődő kampány esetén is működjön.</span><span class="sxs-lookup"><span data-stu-id="6cd6f-118">However, audience insights and Adobe Campaign Standard can be configured to work for a recurring campaign scenario too.</span></span>

## <a name="identify-your-target-audience"></a><span data-ttu-id="6cd6f-119">Azonosítsa a célközönséget</span><span class="sxs-lookup"><span data-stu-id="6cd6f-119">Identify your target audience</span></span>

<span data-ttu-id="6cd6f-120">A mi esetünkben feltételezzük, hogy az ügyfelek e-mail-címei elérhetők a célközönség-információkban, és promóciós preferenciáik elemzésével azonosítottuk a szegmens tagjait.</span><span class="sxs-lookup"><span data-stu-id="6cd6f-120">In our scenario, we assume that the email addresses of the customers are available in audience insights and their promotional preferences were analyzed to identify members of the segment.</span></span>

<span data-ttu-id="6cd6f-121">A [célközönség-információkban meghatározott szegmens](segments.md) neve **ChurnProneCustomers**, és az e-mail-promóció elküldését tervezi ezeknek az ügyfeleknek.</span><span class="sxs-lookup"><span data-stu-id="6cd6f-121">The [segment you defined in audience insights](segments.md) is called **ChurnProneCustomers** and you plan to send these customers the email promotion.</span></span>

:::image type="content" source="media/churn-prone-customers-segment.png" alt-text="Képernyőfelvétel a Szegmensek oldalról, amelyen a létrehozott ChurnProneCustomers szegmens látható.":::

<span data-ttu-id="6cd6f-123">Az elküldeni kívánt ajánlati e-mail tartalmazza az ügyfél utónevét, vezetéknevét és az előfizetés záró dátumát.</span><span class="sxs-lookup"><span data-stu-id="6cd6f-123">The offer email that you want to send out will contain the first name, last name, and the subscription end date of the customer.</span></span> <span data-ttu-id="6cd6f-124">Tájékoztatja az ügyfeleket az arról az engedményről, amit akkor kapnak, ha a vége előtt megújítják az előfizetésüket.</span><span class="sxs-lookup"><span data-stu-id="6cd6f-124">It informs the customers about the discount they’ll get if they renew their subscription before it ends.</span></span>

## <a name="export-your-target-audience"></a><span data-ttu-id="6cd6f-125">Exportálja a célközönséget</span><span class="sxs-lookup"><span data-stu-id="6cd6f-125">Export your target audience</span></span>

<span data-ttu-id="6cd6f-126">Az azonosított célközönség segítségével konfigurálható az exportálás az célközönség-információkból egy Azure Blob Storage-fiókba.</span><span class="sxs-lookup"><span data-stu-id="6cd6f-126">With our target audience identified, we can configure the export from audience insights to an Azure Blob Storage account.</span></span>

1. <span data-ttu-id="6cd6f-127">A célközönség információin belül nyissa meg a következőt **Rendszergazda** > **Exportálási célhelyek**.</span><span class="sxs-lookup"><span data-stu-id="6cd6f-127">In audience insights, go to **Admin** > **Export destinations**.</span></span>

1. <span data-ttu-id="6cd6f-128">A **Adobe Campaign** csempében válassza a **Beállítás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="6cd6f-128">In the **Adobe Campaign** tile, select **Set up**.</span></span>

   :::image type="content" source="media/adobe-campaign-standard-tile.png" alt-text="Az Adobe Campaign Standard konfigurációs csempéje.":::

1. <span data-ttu-id="6cd6f-130">Adja meg az új exportálási célhely **Megjelenítendő nevét**, és adja meg a **Fiók neve**, a **Fiókkulcs** és a **Tároló** értékét arra az Azure Blob Storage-fiókra vonatkozóan, ahova exportálni szeretné a szegmenst.</span><span class="sxs-lookup"><span data-stu-id="6cd6f-130">Provide a **Display name** for this new export destination and then enter the **Account name**, **Account key**, and **Container** of the Azure Blob Storage account where you want to export the segment to.</span></span>  
      
   :::image type="content" source="media/azure-blob-configuration.png" alt-text="Képernyőkép a tárfiók konfigurációjáról."::: 

   - <span data-ttu-id="6cd6f-132">Az Azure Blob Storage fióknév és fiókkulcs megkeresésével kapcsolatos további tudnivalókat lásd: [A tárolófiók beállításainak kezelése az Azure Portal webhelyen](/azure/storage/common/storage-account-manage).</span><span class="sxs-lookup"><span data-stu-id="6cd6f-132">To learn more about how to find the Azure Blob storage account name and account key, see [Manage storage account settings in the Azure portal](/azure/storage/common/storage-account-manage).</span></span>

   - <span data-ttu-id="6cd6f-133">A tároló létrehozásával kapcsolatosan lásd: [Tároló létrehozása](/azure/storage/blobs/storage-quickstart-blobs-portal#create-a-container).</span><span class="sxs-lookup"><span data-stu-id="6cd6f-133">To learn how to create a container, see [Create a container](/azure/storage/blobs/storage-quickstart-blobs-portal#create-a-container).</span></span>

1. <span data-ttu-id="6cd6f-134">Válassza a **Következő** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="6cd6f-134">Select **Next**.</span></span>

1. <span data-ttu-id="6cd6f-135">Válassza ki az exportálni kívánt szegmenst.</span><span class="sxs-lookup"><span data-stu-id="6cd6f-135">Choose the segment that you want to export.</span></span> <span data-ttu-id="6cd6f-136">Ebben a példában ez a **ChurnProneCustomers**.</span><span class="sxs-lookup"><span data-stu-id="6cd6f-136">In this example, it’s **ChurnProneCustomers**.</span></span>

   :::image type="content" source="media/select-segment-churnpronecustomers.png" alt-text="Képernyőkép a szegmenskijelölési felhasználói felületről, ahol a ChurnProneCustomers szegmens ki van választva.":::

1. <span data-ttu-id="6cd6f-138">Válassza a **Következő** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="6cd6f-138">Select **Next**.</span></span>

1. <span data-ttu-id="6cd6f-139">Most leképezzük a célközönség-információk szegmens **Forrás** mezőit az Adobe Campaign Standard profilsémában szereplő **Cél** mezők neveire.</span><span class="sxs-lookup"><span data-stu-id="6cd6f-139">Now we map the **Source** fields from the audience insights segment to the **Target** field names in the Adobe Campaign Standard profile schema.</span></span>

   :::image type="content" source="media/ACS-field-mapping.png" alt-text="Az Adobe Campaign Standard-összekötő mezőleképezése.":::

   <span data-ttu-id="6cd6f-141">Ha további attribútumokat szeretne hozzáadni, válassza az **Attribútum hozzáadása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="6cd6f-141">If you want to add more attributes, select **Add attribute**.</span></span> <span data-ttu-id="6cd6f-142">A cél neve nem lehet azonos a forrásmező nevével, így továbbra is leképezheti a célközönség-információkból származó szegmens kimenetét az Adobe Campaign Standard szolgáltatásba, ha mezőknek a két rendszerben nem ugyanaz a neve.</span><span class="sxs-lookup"><span data-stu-id="6cd6f-142">The target name can be different from the source field name so you can still map segment output from audience insights to Adobe Campaign Standard if the fields don’t have the same name in the two systems.</span></span>

   > [!NOTE]
   > <span data-ttu-id="6cd6f-143">Az e-mail-címet identitásmezőként használja a rendszer, de a célközönség-információk ügyfélprofil egyéb azonosítói segítségével az adatokat leképezheti az Adobe Campaign Standardra.</span><span class="sxs-lookup"><span data-stu-id="6cd6f-143">Email address is used as an identity field but you can use any other identifier from your audience insights customer profile to map data to Adobe Campaign Standard.</span></span>

1. <span data-ttu-id="6cd6f-144">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="6cd6f-144">Select **Save**.</span></span>

<span data-ttu-id="6cd6f-145">Az exportálási cél mentése után megtalálja a **Felügyelet** > **Exportálások** > **Saját exportálási célhelyek** helyen.</span><span class="sxs-lookup"><span data-stu-id="6cd6f-145">After saving the export destination, you find it on **Admin** > **Exports** > **My export destinations**.</span></span>

:::image type="content" source="media/export-destination-adobe-campaign-standard.png" alt-text="Képernyőkép az exportálások listájáról, amelyen a kiemelt mintaszegmens látható.":::

<span data-ttu-id="6cd6f-147">Mostantól [igény szerint exportálhatja a szegmenst](export-destinations.md#export-data-on-demand).</span><span class="sxs-lookup"><span data-stu-id="6cd6f-147">You can now [export the segment on demand](export-destinations.md#export-data-on-demand).</span></span> <span data-ttu-id="6cd6f-148">Az exportálás minden [ütemezett frissítéssel](system.md) együtt is lefut.</span><span class="sxs-lookup"><span data-stu-id="6cd6f-148">The export will also run with every [scheduled refresh](system.md).</span></span>

> [!NOTE]
> <span data-ttu-id="6cd6f-149">Győződjön meg róla, hogy az exportált szegmens rekordjainak száma az Adobe Campaign Standard licencének megengedett korlátjan belül van.</span><span class="sxs-lookup"><span data-stu-id="6cd6f-149">Ensure that the number of records in the exported segment are within the allowed limit of your Adobe Campaign Standard license.</span></span>

<span data-ttu-id="6cd6f-150">Az exportált adatokat a rendszer a fent beállított Azure Blob Storage-tárolóban tárolja.</span><span class="sxs-lookup"><span data-stu-id="6cd6f-150">Exported data is stored in the Azure Blob storage container you configured above.</span></span> <span data-ttu-id="6cd6f-151">A következő mappa elérési útja automatikusan létrejön a tárolóban:</span><span class="sxs-lookup"><span data-stu-id="6cd6f-151">The following folder path is automatically created in your container:</span></span>

<span data-ttu-id="6cd6f-152">*%ContainerName%/CustomerInsights_%instanceID%/% exportdestination-name%_%segmentname%_%timestamp%.csv*</span><span class="sxs-lookup"><span data-stu-id="6cd6f-152">*%ContainerName%/CustomerInsights_%instanceID%/% exportdestination-name%_%segmentname%_%timestamp%.csv*</span></span>

<span data-ttu-id="6cd6f-153">Példa: Dynamics365CustomerInsights/CustomerInsights_abcd1234-4312-11f4-93dc-24f72f43e7d5/ChurnSegmentDemo_ChurnProneCustomers_1613059542.csv</span><span class="sxs-lookup"><span data-stu-id="6cd6f-153">Example: Dynamics365CustomerInsights/CustomerInsights_abcd1234-4312-11f4-93dc-24f72f43e7d5/ChurnSegmentDemo_ChurnProneCustomers_1613059542.csv</span></span>

## <a name="configure-adobe-campaign-standard"></a><span data-ttu-id="6cd6f-154">Adobe Campaign Standard konfigurálása</span><span class="sxs-lookup"><span data-stu-id="6cd6f-154">Configure Adobe Campaign Standard</span></span>

<span data-ttu-id="6cd6f-155">Ha egy szegmenst exportál célközönség-információkból, akkor az előző lépésben az exportálási cél meghatározása során kiválasztott oszlopokat tartalmazza.</span><span class="sxs-lookup"><span data-stu-id="6cd6f-155">When a segment from audience insights is exported, it contains the columns you selected while defining the export destination in the previous step.</span></span> <span data-ttu-id="6cd6f-156">Ezek az adatok használhatók [profilok létrehozásához az Adobe Campaign Standardban](https://experienceleague.adobe.com/docs/campaign-standard/using/profiles-and-audiences/managing-profiles/about-profiles.html#managing-profiles).</span><span class="sxs-lookup"><span data-stu-id="6cd6f-156">This data can be used to [create profiles in Adobe Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard/using/profiles-and-audiences/managing-profiles/about-profiles.html#managing-profiles).</span></span>

<span data-ttu-id="6cd6f-157">A szegmens az Adobe Campaign Standardban való használata esetén két további mezőre is ki kell bővítenünk a profilsémát az Adobe Campaign Standardban.</span><span class="sxs-lookup"><span data-stu-id="6cd6f-157">To use the segment in Adobe Campaign Standard, we need to extend the profile schema in Adobe Campaign Standard to include two additional fields.</span></span> <span data-ttu-id="6cd6f-158">Ismerje meg, hogyan [bővítheti a profilerőforrást](https://experienceleague.adobe.com/docs/campaign-standard/using/developing/use-cases--extending-resources/extending-the-profile-resource-with-a-new-field.html#developing) az Adobe Campaign Standard új mezőivel.</span><span class="sxs-lookup"><span data-stu-id="6cd6f-158">Learn how to [extend the profile resource](https://experienceleague.adobe.com/docs/campaign-standard/using/developing/use-cases--extending-resources/extending-the-profile-resource-with-a-new-field.html#developing) with new fields in Adobe Campaign Standard.</span></span>

<span data-ttu-id="6cd6f-159">A példában ezek a mezők a *Szegmens neve és a Szegmens dátuma (nem kötelező).*</span><span class="sxs-lookup"><span data-stu-id="6cd6f-159">In our example, these fields are *Segment Name and Segment Date (optional).*</span></span>

<span data-ttu-id="6cd6f-160">Ezeket a mezőket arra használjuk, hogy azonosítsuk a kampányhoz megcélozni kívánt Adobe Campaign Standard-profilokat.</span><span class="sxs-lookup"><span data-stu-id="6cd6f-160">We will use these fields to identify the profiles in Adobe Campaign Standard we want to target for this campaign.</span></span>

<span data-ttu-id="6cd6f-161">Ha az Adobe Campaign Standardban nincs más rekord, mint amit importálni fog, ezt a lépést kihagyhatja.</span><span class="sxs-lookup"><span data-stu-id="6cd6f-161">If there are no other records in Adobe Campaign Standard, other than what you are going to import, you can skip this step.</span></span>

## <a name="import-data-into-adobe-campaign-standard"></a><span data-ttu-id="6cd6f-162">Adatok importálása az Adobe Campaign Standard programba</span><span class="sxs-lookup"><span data-stu-id="6cd6f-162">Import data into Adobe Campaign Standard</span></span>

<span data-ttu-id="6cd6f-163">Most, hogy minden a helyén van, a profilok létrehozásához importálni kell az előkészített célközönségadatokat az célközönség-információkból az Adobe Campaign Standardba.</span><span class="sxs-lookup"><span data-stu-id="6cd6f-163">Now that everything is in place, we need to import the prepared audience data from audience insights into Adobe Campaign Standard to create profiles.</span></span> <span data-ttu-id="6cd6f-164">Ismerje meg, [hogyan importálhat profilokat az Adobe Campaign Standardba](https://experienceleague.adobe.com/docs/campaign-standard/using/profiles-and-audiences/managing-profiles/creating-profiles.html#profiles-and-audiences) munkafolyamatok használatával.</span><span class="sxs-lookup"><span data-stu-id="6cd6f-164">Learn [how to import profiles in Adobe Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard/using/profiles-and-audiences/managing-profiles/creating-profiles.html#profiles-and-audiences) using a workflow.</span></span>

<span data-ttu-id="6cd6f-165">Az alábbi képen az importálási munkafolyamat 8 óránként fut, és exportált célközönség-információs szegmensek (.csv fájl az Azure Blob Storage-ban) után kutat.</span><span class="sxs-lookup"><span data-stu-id="6cd6f-165">The import workflow in the image below has been configured to run every 8 hours and looks for exported audience insights segments (.csv file in Azure Blob Storage).</span></span> <span data-ttu-id="6cd6f-166">A munkafolyamat meghatározott oszloprendben bontja ki a .csv fájl tartalmát.</span><span class="sxs-lookup"><span data-stu-id="6cd6f-166">The workflow extracts the .csv file content in a specified column order.</span></span> <span data-ttu-id="6cd6f-167">Ez a munkafolyamat az alapvető hibakezelés végrehajtásához készült, és biztosítja, hogy minden rekordhoz tartozzon e-mail-cím, mielőtt az adatokat átveszi az Adobe Campaign Standardban.</span><span class="sxs-lookup"><span data-stu-id="6cd6f-167">This workflow has been built to perform basic error handling and ensure that each record has an email address before hydrating the data in Adobe Campaign Standard.</span></span> <span data-ttu-id="6cd6f-168">A munkafolyamat ki is bontja a szegmens nevét a fájlnévből, mielőtt az ACS-profiladatokba upsertelné.</span><span class="sxs-lookup"><span data-stu-id="6cd6f-168">The workflow also extracts the segment name from the filename before upserting into ACS Profile data.</span></span>

:::image type="content" source="media/ACS-import-workflow.png" alt-text="Képernyőkép az importálási munkafolyamatról az Adobe Campaign Standard felhasználói felületén.":::

## <a name="retrieve-the-audience-in-adobe-campaign-standard"></a><span data-ttu-id="6cd6f-170">A célközönség lekérése az Adobe Campaign Standardban</span><span class="sxs-lookup"><span data-stu-id="6cd6f-170">Retrieve the audience in Adobe Campaign Standard</span></span>

<span data-ttu-id="6cd6f-171">Miután megtörtént az adatok importálása az Adobe Campaign Standardba, [létrehozhat egy munkafolyamatot](https://experienceleague.adobe.com/docs/campaign-standard/using/managing-processes-and-data/workflow-general-operation/building-a-workflow.html#managing-processes-and-data), és [lekérdezheti](https://experienceleague.adobe.com/docs/campaign-standard/using/managing-processes-and-data/targeting-activities/query.html#managing-processes-and-data) az ügyfeleket a *Szegmensnév* és *Szegmens dátuma* alapján, hogy kiválaszthassa a mintakampányhoz beazonosítótt profilokat.</span><span class="sxs-lookup"><span data-stu-id="6cd6f-171">Once the data is imported into Adobe Campaign Standard, you [can create a workflow](https://experienceleague.adobe.com/docs/campaign-standard/using/managing-processes-and-data/workflow-general-operation/building-a-workflow.html#managing-processes-and-data) and [query](https://experienceleague.adobe.com/docs/campaign-standard/using/managing-processes-and-data/targeting-activities/query.html#managing-processes-and-data) the customers based on the *Segment Name* and *Segment Date* to select profiles that were identified for our sample campaign.</span></span>

## <a name="create-and-send-the-email-using-adobe-campaign-standard"></a><span data-ttu-id="6cd6f-172">Az e-mail létrehozása és elküldése az Adobe Campaign Standard használatával</span><span class="sxs-lookup"><span data-stu-id="6cd6f-172">Create and send the email using Adobe Campaign Standard</span></span>

<span data-ttu-id="6cd6f-173">Hozza létre az e-mail tartalmát, majd [tesztelje, és küldje el](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/get-started-sending-messages.html#preparing-and-testing-messages) az e-mailt.</span><span class="sxs-lookup"><span data-stu-id="6cd6f-173">Create the email content and then [test and send](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/get-started-sending-messages.html#preparing-and-testing-messages) your email.</span></span>

:::image type="content" source="media/contoso-sample-email.jpg" alt-text="E-mail minta az Adobe Campaign Standard megújítási ajánlatával.":::