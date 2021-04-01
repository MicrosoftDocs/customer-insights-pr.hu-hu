---
title: A Customer Insights adatainak exportálása az Adobe Experience Platformba
description: Ismerje meg, hogyan használhatja a célközönség-infomációs szegmenseket az Adobe Experience Platformban.
ms.date: 02/26/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: stefanie-msft
ms.author: antando
manager: shellyha
ms.openlocfilehash: d1856861562be55c6d1d051050fe965560fa42f8
ms.sourcegitcommit: bae40184312ab27b95c140a044875c2daea37951
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/15/2021
ms.locfileid: "5596272"
---
# <a name="use-customer-insights-segments-in-adobe-experience-platform-preview"></a><span data-ttu-id="81805-103">A Customer Insights-szegmensek használata az Adobe Experience Platformban (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="81805-103">Use Customer Insights segments in Adobe Experience Platform (preview)</span></span>

<span data-ttu-id="81805-104">A Dynamics 365 Customer Insights célközönség-információinak felhasználójaként létrehozott szegmenseket, hogy a marketingkampányok hatékonyságát növelje a releváns célközönségek megcélzásával.</span><span class="sxs-lookup"><span data-stu-id="81805-104">As a user of audience insights for Dynamics 365 Customer Insights, you may have created segments to make your marketing campaigns more efficient by targeting relevant audiences.</span></span> <span data-ttu-id="81805-105">Az Adobe Experience Platformban és az Adobe Campaign Standardhoz hasonló alkalmazásokban található célközönség-információs szegmensek használatához a jelen cikkben ismertetett lépéseket kell követnie.</span><span class="sxs-lookup"><span data-stu-id="81805-105">To use a segment from audience insights in Adobe Experience Platform and applications like Adobe Campaign Standard, you need to follow a few steps outlined in this article.</span></span>

:::image type="content" source="media/AEP-flow.png" alt-text="A jelen cikkben ismertetett lépések folyamatábrája.":::

## <a name="prerequisites"></a><span data-ttu-id="81805-107">Előfeltételek</span><span class="sxs-lookup"><span data-stu-id="81805-107">Prerequisites</span></span>

-   <span data-ttu-id="81805-108">Dynamics 365 Customer Insights licenc</span><span class="sxs-lookup"><span data-stu-id="81805-108">Dynamics 365 Customer Insights license</span></span>
-   <span data-ttu-id="81805-109">Adobe Experience Platform-licenc</span><span class="sxs-lookup"><span data-stu-id="81805-109">Adobe Experience Platform license</span></span>
-   <span data-ttu-id="81805-110">Adobe Campaign Standard-licenc</span><span class="sxs-lookup"><span data-stu-id="81805-110">Adobe Campaign Standard license</span></span>
-   <span data-ttu-id="81805-111">Azure Blob Storage-fiók</span><span class="sxs-lookup"><span data-stu-id="81805-111">Azure Blob Storage account</span></span>

## <a name="campaign-overview"></a><span data-ttu-id="81805-112">Kampány áttekintése</span><span class="sxs-lookup"><span data-stu-id="81805-112">Campaign Overview</span></span>

<span data-ttu-id="81805-113">Hogy jobban meg tudja érteni, hogyan használhatja a célközönség-információs szegmenseket az Adobe Experience Platformban, tekintsünk át egy kitalált mintakampányt.</span><span class="sxs-lookup"><span data-stu-id="81805-113">To better understand how you can use segments from audience insights in Adobe Experience Platform, let’s look at a fictitious sample campaign.</span></span>

<span data-ttu-id="81805-114">Tegyük fel, hogy a vállalata havi előfizetéses szolgáltatást kínál egyesült államokbeli ügyfeleinek.</span><span class="sxs-lookup"><span data-stu-id="81805-114">Let’s assume that your company offers a monthly, subscription-based service to your customers in the United States.</span></span> <span data-ttu-id="81805-115">Meg szeretné határozni azokat az ügyfeleket, akiknek az előfizetései a következő nyolc napban megújításra esedékesek, de még nem újították meg előfizetésüket.</span><span class="sxs-lookup"><span data-stu-id="81805-115">You want to identify customers whose subscriptions are due for renewal in the next eight days but haven't yet renewed their subscription.</span></span> <span data-ttu-id="81805-116">Ezeknek az ügyfeleknek a megtartása érdekében e-mailben szeretne promóciós ajánlatot küldeni nekik az Adobe Experience Platform segítségével.</span><span class="sxs-lookup"><span data-stu-id="81805-116">To keep these customers, you want to send them a promotional offer via email, using Adobe Experience Platform.</span></span>

<span data-ttu-id="81805-117">Ebben a példában egy promóciós e-mail-kampányt egyszer szeretnénk futtatni.</span><span class="sxs-lookup"><span data-stu-id="81805-117">In this example, we want to run the promotional email campaign once.</span></span> <span data-ttu-id="81805-118">Ez a cikk nem terjed ki a kampány egynél több esetben való futtatásának esetére.</span><span class="sxs-lookup"><span data-stu-id="81805-118">This article doesn’t cover the use-case of running the campaign more than once.</span></span>

## <a name="identify-your-target-audience"></a><span data-ttu-id="81805-119">Azonosítsa a célközönséget</span><span class="sxs-lookup"><span data-stu-id="81805-119">Identify your target audience</span></span>

<span data-ttu-id="81805-120">A mi esetünkben feltételezzük, hogy az ügyfelek e-mail-címei elérhetők a célközönség-információkban, és promóciós preferenciáik elemzésével azonosítottuk a szegmens tagjait.</span><span class="sxs-lookup"><span data-stu-id="81805-120">In our scenario, we assume that the email addresses of the customers are available in audience insights and their promotional preferences were analyzed to identify members of the segment.</span></span>

<span data-ttu-id="81805-121">A [célközönség-információkban meghatározott szegmens](segments.md) neve **ChurnProneCustomers**, és az e-mail-promóció elküldését tervezi ezeknek az ügyfeleknek.</span><span class="sxs-lookup"><span data-stu-id="81805-121">The [segment you defined in audience insights](segments.md) is called **ChurnProneCustomers** and you plan to send these customers the email promotion.</span></span>

:::image type="content" source="media/churn-prone-customers-segment.png" alt-text="Képernyőfelvétel a Szegmensek oldalról, amelyen a létrehozott ChurnProneCustomers szegmens látható.":::

<span data-ttu-id="81805-123">Az elküldeni kívánt ajánlati e-mail tartalmazza az ügyfél utónevét, vezetéknevét és az előfizetés záró dátumát.</span><span class="sxs-lookup"><span data-stu-id="81805-123">The offer email that you want to send out will contain the first name, last name, and the subscription end date of the customer.</span></span> <span data-ttu-id="81805-124">Tájékoztatja az ügyfeleket az arról az engedményről, amit akkor kapnak, ha a vége előtt megújítják az előfizetésüket.</span><span class="sxs-lookup"><span data-stu-id="81805-124">It informs the customers about the discount they’ll get if they renew their subscription before it ends.</span></span>

## <a name="export-your-target-audience"></a><span data-ttu-id="81805-125">Exportálja a célközönséget</span><span class="sxs-lookup"><span data-stu-id="81805-125">Export your target audience</span></span>

<span data-ttu-id="81805-126">Az azonosított célközönség segítségével konfigurálható az exportálás az célközönség-információkból egy Azure Blob Storage-fiókba.</span><span class="sxs-lookup"><span data-stu-id="81805-126">With our target audience identified, we can configure the export from audience insights to an Azure Blob Storage account.</span></span>

1. <span data-ttu-id="81805-127">A célközönség információin belül nyissa meg a következőt **Rendszergazda** > **Exportálási célhelyek**.</span><span class="sxs-lookup"><span data-stu-id="81805-127">In audience insights, go to **Admin** > **Export destinations**.</span></span>

1. <span data-ttu-id="81805-128">Az **Azure Blob Storage** csempén válassza a **Beállítás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="81805-128">In the **Azure Blob Storage** tile, select **Set up**.</span></span>

   :::image type="content" source="media/export-azure-blob-storage-tile.png" alt-text="Az Azure Blob Storage konfigurációs csempéje.":::

1. <span data-ttu-id="81805-130">Adja meg az új exportálási célhely **Megjelenítendő nevét**, és adja meg a **Fiók neve**, a **Fiókkulcs** és a **Tároló** értékét arra az Azure Blob Storage-fiókra vonatkozóan, ahova exportálni szeretné a szegmenst.</span><span class="sxs-lookup"><span data-stu-id="81805-130">Provide a **Display name** for this new export destination and then enter the **Account name**, **Account key**, and **Container** of the Azure Blob Storage account where you want to export the segment to.</span></span>  
      
   :::image type="content" source="media/azure-blob-configuration.png" alt-text="Képernyőkép a tárfiók konfigurációjáról."::: 

   - <span data-ttu-id="81805-132">Az Azure Blob Storage fióknév és fiókkulcs megkeresésével kapcsolatos további tudnivalókat lásd: [A tárolófiók beállításainak kezelése az Azure Portal webhelyen](/azure/storage/common/storage-account-manage).</span><span class="sxs-lookup"><span data-stu-id="81805-132">To learn more about how to find the Azure Blob storage account name and account key, see [Manage storage account settings in the Azure portal](/azure/storage/common/storage-account-manage).</span></span>

   - <span data-ttu-id="81805-133">A tároló létrehozásával kapcsolatosan lásd: [Tároló létrehozása](/azure/storage/blobs/storage-quickstart-blobs-portal#create-a-container).</span><span class="sxs-lookup"><span data-stu-id="81805-133">To learn how to create a container, see [Create a container](/azure/storage/blobs/storage-quickstart-blobs-portal#create-a-container).</span></span>

1. <span data-ttu-id="81805-134">Válassza a **Következő** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="81805-134">Select **Next**.</span></span>

1. <span data-ttu-id="81805-135">Válassza ki az exportálni kívánt szegmenst.</span><span class="sxs-lookup"><span data-stu-id="81805-135">Choose the segment that you want to export.</span></span> <span data-ttu-id="81805-136">Ebben a példában ez a **ChurnProneCustomers**.</span><span class="sxs-lookup"><span data-stu-id="81805-136">In this example, it’s **ChurnProneCustomers**.</span></span>

   :::image type="content" source="media/select-segment-churnpronecustomers.png" alt-text="Képernyőkép a szegmenskijelölési felhasználói felületről, ahol a ChurnProneCustomers szegmens ki van választva.":::

1. <span data-ttu-id="81805-138">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="81805-138">Select **Save**.</span></span>

<span data-ttu-id="81805-139">Az exportálási cél mentése után megtalálja a **Felügyelet** > **Exportálások** > **Saját exportálási célhelyek** helyen.</span><span class="sxs-lookup"><span data-stu-id="81805-139">After saving the export destination, you find it on **Admin** > **Exports** > **My export destinations**.</span></span>

:::image type="content" source="media/export-destination-azure-blob-storage.png" alt-text="Képernyőkép az exportálások listájáról, amelyen a kiemelt mintaszegmens látható.":::

<span data-ttu-id="81805-141">Mostantól [igény szerint exportálhatja a szegmenst](export-destinations.md#export-data-on-demand).</span><span class="sxs-lookup"><span data-stu-id="81805-141">You can now [export the segment on demand](export-destinations.md#export-data-on-demand).</span></span> <span data-ttu-id="81805-142">Az exportálás minden [ütemezett frissítéssel](system.md) együtt is lefut.</span><span class="sxs-lookup"><span data-stu-id="81805-142">The export will also run with every [scheduled refresh](system.md).</span></span>

> [!NOTE]
> <span data-ttu-id="81805-143">Győződjön meg róla, hogy az exportált szegmens rekordjainak száma az Adobe Campaign Standard licencének megengedett korlátjan belül van.</span><span class="sxs-lookup"><span data-stu-id="81805-143">Ensure that the number of records in the exported segment are within the allowed limit of your Adobe Campaign Standard license.</span></span>

<span data-ttu-id="81805-144">Az exportált adatokat a rendszer a fent beállított Azure Blob Storage-tárolóban tárolja.</span><span class="sxs-lookup"><span data-stu-id="81805-144">Exported data is stored in the Azure Blob storage container you configured above.</span></span> <span data-ttu-id="81805-145">A következő mappa elérési útja automatikusan létrejön a tárolóban:</span><span class="sxs-lookup"><span data-stu-id="81805-145">The following folder path is automatically created in your container:</span></span>

<span data-ttu-id="81805-146">*%ContainerName%/CustomerInsights_%instanceID%/%ExportDestinationName%/%EntityName%/%Year%/%Month%/%Day%/%HHMM%/%EntityName%_%PartitionId%.csv*</span><span class="sxs-lookup"><span data-stu-id="81805-146">*%ContainerName%/CustomerInsights_%instanceID%/%ExportDestinationName%/%EntityName%/%Year%/%Month%/%Day%/%HHMM%/%EntityName%_%PartitionId%.csv*</span></span>

<span data-ttu-id="81805-147">Példa: Dynamics365CustomerInsights/CustomerInsights_abcd1234-4312-11f4-93dc-24f72f43e7d5/BlobExport/ChurnSegmentDemo/2021/02/16/1433/ChurnProneCustomers_1.csv</span><span class="sxs-lookup"><span data-stu-id="81805-147">Example: Dynamics365CustomerInsights/CustomerInsights_abcd1234-4312-11f4-93dc-24f72f43e7d5/BlobExport/ChurnSegmentDemo/2021/02/16/1433/ChurnProneCustomers_1.csv</span></span>

<span data-ttu-id="81805-148">Az exportált entitások *model.json* fájlja az *%ExportDestinationName%* szintjén helyezkedik el</span><span class="sxs-lookup"><span data-stu-id="81805-148">The *model.json* for the exported entities resides at the *%ExportDestinationName%* level.</span></span>

<span data-ttu-id="81805-149">Példa: Dynamics365CustomerInsights/CustomerInsights_abcd1234-4312-11f4-93dc-24f72f43e7d5/ChurnSegmentDemo/model.json</span><span class="sxs-lookup"><span data-stu-id="81805-149">Example: Dynamics365CustomerInsights/CustomerInsights_abcd1234-4312-11f4-93dc-24f72f43e7d5/ChurnSegmentDemo/model.json</span></span>

## <a name="define-experience-data-model-xdm-in-adobe-experience-platform"></a><span data-ttu-id="81805-150">A Tapasztalati adatmodell (XDM) definiálása az Adobe Experience Platformon</span><span class="sxs-lookup"><span data-stu-id="81805-150">Define Experience Data Model (XDM) in Adobe Experience Platform</span></span>

<span data-ttu-id="81805-151">Mielőtt az célközönség-információkból exportált adatokat használhatjuk az Adobe Experience Platformon belül, meg kell határozni a Tapasztalat adatmodell sémáját, és [konfigurálni kell az adatokat a valós idejű ügyfélprofilhoz](https://experienceleague.adobe.com/docs/experience-platform/profile/tutorials/dataset-configuration.html#tutorials).</span><span class="sxs-lookup"><span data-stu-id="81805-151">Before the exported data from audience insights can be used within Adobe Experience Platform, we need to define the Experience Data Model schema and [configure the data for the Real-time Customer Profile](https://experienceleague.adobe.com/docs/experience-platform/profile/tutorials/dataset-configuration.html#tutorials).</span></span>

<span data-ttu-id="81805-152">Ismerje meg, [mi az az XDM](https://experienceleague.adobe.com/docs/experience-platform/xdm/home.html), és ismerje meg a [sémaösszetétel alapjait](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html#schema).</span><span class="sxs-lookup"><span data-stu-id="81805-152">Learn [what XDM is](https://experienceleague.adobe.com/docs/experience-platform/xdm/home.html) and understand the [basics of schema composition](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html#schema).</span></span>

## <a name="import-data-into-adobe-experience-platform"></a><span data-ttu-id="81805-153">Adatok importálása az Adobe Experience Platformba</span><span class="sxs-lookup"><span data-stu-id="81805-153">Import data into Adobe Experience Platform</span></span>

<span data-ttu-id="81805-154">Most, hogy minden a helyén van, a profilok létrehozásához importálni kell az előkészített célközönségadatokat az célközönség-információkból az Adobe Experience Platformba.</span><span class="sxs-lookup"><span data-stu-id="81805-154">Now that everything is in place, we need to import the prepared audience data from audience insights into Adobe Experience Platform.</span></span>

<span data-ttu-id="81805-155">Először [hozzon létre egy Azure Blob Storage-forráskapcsolatot](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/cloud-storage/blob.html#getting-started).</span><span class="sxs-lookup"><span data-stu-id="81805-155">First, [create an Azure Blob Storage source connection](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/cloud-storage/blob.html#getting-started).</span></span>    

<span data-ttu-id="81805-156">A forráskapcsolat definiálása után [konfigurálja egy felhőalapú tároló kötegfájl-kapcsolat adatfolyamát](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/dataflow/cloud-storage.html#ui-tutorials), hogy a szegmens kimenetét a célközönség-információkból az Adobe Experience Platformba importálja.</span><span class="sxs-lookup"><span data-stu-id="81805-156">After defining the source connection, [configure a dataflow](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/dataflow/cloud-storage.html#ui-tutorials) for a cloud storage batch connection to import the segment output from audience insights into Adobe Experience Platform.</span></span>

## <a name="create-an-audience-in-adobe-campaign-standard"></a><span data-ttu-id="81805-157">A célközönség létrehozása az Adobe Campaign Standardban</span><span class="sxs-lookup"><span data-stu-id="81805-157">Create an audience in Adobe Campaign Standard</span></span>

<span data-ttu-id="81805-158">A kampányhoz tartozó e-mail elküldéséhez az Adobe Campaign Standardot fogjuk használni.</span><span class="sxs-lookup"><span data-stu-id="81805-158">To send the email for this campaign, we will use Adobe Campaign Standard.</span></span> <span data-ttu-id="81805-159">Miután importálta az adatokat az Adobe Experience Platformba, [létre kell hozni egy célközönséget](https://experienceleague.adobe.com/docs/campaign-standard/using/profiles-and-audiences/get-started-profiles-and-audiences.html#permission) az Adobe Campaign Standardban, az Adobe Experience Platform adatai segítségével.</span><span class="sxs-lookup"><span data-stu-id="81805-159">After importing the data into Adobe Experience Platform, we need to [create an audience](https://experienceleague.adobe.com/docs/campaign-standard/using/profiles-and-audiences/get-started-profiles-and-audiences.html#permission) in Adobe Campaign Standard using the data in Adobe Experience Platform.</span></span>

<span data-ttu-id="81805-160">Ismerje meg, hogyan [használható a szegmensszerkesztő](https://experienceleague.adobe.com/docs/campaign-standard/using/profiles-and-audiences/working-with-adobe-experience-platform/aep-using-segment-builder.html#building-a-segment) az Adobe Campaign Standardban egy célközönség meghatározásához az Adobe Experience Platform adatai alapján.</span><span class="sxs-lookup"><span data-stu-id="81805-160">Learn how to [use segment builder](https://experienceleague.adobe.com/docs/campaign-standard/using/profiles-and-audiences/working-with-adobe-experience-platform/aep-using-segment-builder.html#building-a-segment) in Adobe Campaign Standard to define an audience based on the data in Adobe Experience Platform.</span></span>

## <a name="create-and-send-the-email-using-adobe-campaign-standard"></a><span data-ttu-id="81805-161">Az e-mail létrehozása és elküldése az Adobe Campaign Standard használatával</span><span class="sxs-lookup"><span data-stu-id="81805-161">Create and send the email using Adobe Campaign Standard</span></span>

<span data-ttu-id="81805-162">Hozza létre az e-mail tartalmát, majd [tesztelje, és küldje el](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/get-started-sending-messages.html#preparing-and-testing-messages) az e-mailt.</span><span class="sxs-lookup"><span data-stu-id="81805-162">Create the email content and then [test and send](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/get-started-sending-messages.html#preparing-and-testing-messages) your email.</span></span>

:::image type="content" source="media/contoso-sample-email.jpg" alt-text="E-mail minta az Adobe Campaign Standard megújítási ajánlatával.":::