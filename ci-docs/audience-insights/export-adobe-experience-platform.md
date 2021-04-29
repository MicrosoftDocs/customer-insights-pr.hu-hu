---
title: A Customer Insights adatainak exportálása az Adobe Experience Platformba
description: Ismerje meg, hogyan használhatja a célközönség-infomációs szegmenseket az Adobe Experience Platformban.
ms.date: 03/29/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: stefanie-msft
ms.author: antando
manager: shellyha
ms.openlocfilehash: 884f4d30f354bed29909d57be84dce4c8e46965a
ms.sourcegitcommit: 1b671c6100991fea1cace04b5d4fcedcd88aa94f
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/31/2021
ms.locfileid: "5760104"
---
# <a name="use-customer-insights-segments-in-adobe-experience-platform-preview"></a><span data-ttu-id="f6e52-103">A Customer Insights-szegmensek használata az Adobe Experience Platformban (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="f6e52-103">Use Customer Insights segments in Adobe Experience Platform (preview)</span></span>

<span data-ttu-id="f6e52-104">A Dynamics 365 Customer Insights célközönség-információinak felhasználójaként létrehozott szegmenseket, hogy a marketingkampányok hatékonyságát növelje a releváns célközönségek megcélzásával.</span><span class="sxs-lookup"><span data-stu-id="f6e52-104">As a user of audience insights for Dynamics 365 Customer Insights, you may have created segments to make your marketing campaigns more efficient by targeting relevant audiences.</span></span> <span data-ttu-id="f6e52-105">Az Adobe Experience Platformban és az Adobe Campaign Standardhoz hasonló alkalmazásokban található célközönség-információs szegmensek használatához a jelen cikkben ismertetett lépéseket kell követnie.</span><span class="sxs-lookup"><span data-stu-id="f6e52-105">To use a segment from audience insights in Adobe Experience Platform and applications like Adobe Campaign Standard, you need to follow a few steps outlined in this article.</span></span>

:::image type="content" source="media/AEP-flow.png" alt-text="A jelen cikkben ismertetett lépések folyamatábrája.":::

## <a name="prerequisites"></a><span data-ttu-id="f6e52-107">Előfeltételek</span><span class="sxs-lookup"><span data-stu-id="f6e52-107">Prerequisites</span></span>

-   <span data-ttu-id="f6e52-108">Dynamics 365 Customer Insights licenc</span><span class="sxs-lookup"><span data-stu-id="f6e52-108">Dynamics 365 Customer Insights license</span></span>
-   <span data-ttu-id="f6e52-109">Adobe Experience Platform-licenc</span><span class="sxs-lookup"><span data-stu-id="f6e52-109">Adobe Experience Platform license</span></span>
-   <span data-ttu-id="f6e52-110">Adobe Campaign Standard-licenc</span><span class="sxs-lookup"><span data-stu-id="f6e52-110">Adobe Campaign Standard license</span></span>
-   <span data-ttu-id="f6e52-111">Azure Blob Storage-fiók</span><span class="sxs-lookup"><span data-stu-id="f6e52-111">Azure Blob Storage account</span></span>

## <a name="campaign-overview"></a><span data-ttu-id="f6e52-112">Kampány áttekintése</span><span class="sxs-lookup"><span data-stu-id="f6e52-112">Campaign Overview</span></span>

<span data-ttu-id="f6e52-113">Hogy jobban meg tudja érteni, hogyan használhatja a célközönség-információs szegmenseket az Adobe Experience Platformban, tekintsünk át egy kitalált mintakampányt.</span><span class="sxs-lookup"><span data-stu-id="f6e52-113">To better understand how you can use segments from audience insights in Adobe Experience Platform, let’s look at a fictitious sample campaign.</span></span>

<span data-ttu-id="f6e52-114">Tegyük fel, hogy a vállalata havi előfizetéses szolgáltatást kínál egyesült államokbeli ügyfeleinek.</span><span class="sxs-lookup"><span data-stu-id="f6e52-114">Let’s assume that your company offers a monthly, subscription-based service to your customers in the United States.</span></span> <span data-ttu-id="f6e52-115">Meg szeretné határozni azokat az ügyfeleket, akiknek az előfizetései a következő nyolc napban megújításra esedékesek, de még nem újították meg előfizetésüket.</span><span class="sxs-lookup"><span data-stu-id="f6e52-115">You want to identify customers whose subscriptions are due for renewal in the next eight days but haven't yet renewed their subscription.</span></span> <span data-ttu-id="f6e52-116">Ezeknek az ügyfeleknek a megtartása érdekében e-mailben szeretne promóciós ajánlatot küldeni nekik az Adobe Experience Platform segítségével.</span><span class="sxs-lookup"><span data-stu-id="f6e52-116">To keep these customers, you want to send them a promotional offer via email, using Adobe Experience Platform.</span></span>

<span data-ttu-id="f6e52-117">Ebben a példában egy promóciós e-mail-kampányt egyszer szeretnénk futtatni.</span><span class="sxs-lookup"><span data-stu-id="f6e52-117">In this example, we want to run the promotional email campaign once.</span></span> <span data-ttu-id="f6e52-118">Ez a cikk nem terjed ki a kampány egynél több esetben való futtatásának esetére.</span><span class="sxs-lookup"><span data-stu-id="f6e52-118">This article doesn’t cover the use-case of running the campaign more than once.</span></span>

## <a name="identify-your-target-audience"></a><span data-ttu-id="f6e52-119">Azonosítsa a célközönséget</span><span class="sxs-lookup"><span data-stu-id="f6e52-119">Identify your target audience</span></span>

<span data-ttu-id="f6e52-120">A mi esetünkben feltételezzük, hogy az ügyfelek e-mail-címei elérhetők a célközönség-információkban, és promóciós preferenciáik elemzésével azonosítottuk a szegmens tagjait.</span><span class="sxs-lookup"><span data-stu-id="f6e52-120">In our scenario, we assume that the email addresses of the customers are available in audience insights and their promotional preferences were analyzed to identify members of the segment.</span></span>

<span data-ttu-id="f6e52-121">A [célközönség-információkban meghatározott szegmens](segments.md) neve **ChurnProneCustomers**, és az e-mail-promóció elküldését tervezi ezeknek az ügyfeleknek.</span><span class="sxs-lookup"><span data-stu-id="f6e52-121">The [segment you defined in audience insights](segments.md) is called **ChurnProneCustomers** and you plan to send these customers the email promotion.</span></span>

:::image type="content" source="media/churn-prone-customers-segment.png" alt-text="Képernyőfelvétel a Szegmensek oldalról, amelyen a létrehozott ChurnProneCustomers szegmens látható.":::

<span data-ttu-id="f6e52-123">Az elküldeni kívánt ajánlati e-mail tartalmazza az ügyfél utónevét, vezetéknevét és az előfizetés záró dátumát.</span><span class="sxs-lookup"><span data-stu-id="f6e52-123">The offer email that you want to send out will contain the first name, last name, and the subscription end date of the customer.</span></span> <span data-ttu-id="f6e52-124">Tájékoztatja az ügyfeleket az arról az engedményről, amit akkor kapnak, ha a vége előtt megújítják az előfizetésüket.</span><span class="sxs-lookup"><span data-stu-id="f6e52-124">It informs the customers about the discount they’ll get if they renew their subscription before it ends.</span></span>

## <a name="export-your-target-audience"></a><span data-ttu-id="f6e52-125">Exportálja a célközönséget</span><span class="sxs-lookup"><span data-stu-id="f6e52-125">Export your target audience</span></span>

<span data-ttu-id="f6e52-126">Az azonosított célközönség segítségével konfigurálható az exportálás az célközönség-információkból egy Azure Blob Storage-fiókba.</span><span class="sxs-lookup"><span data-stu-id="f6e52-126">With our target audience identified, we can configure the export from audience insights to an Azure Blob Storage account.</span></span>

### <a name="configure-a-connection"></a><span data-ttu-id="f6e52-127">Kapcsolat konfigurálása</span><span class="sxs-lookup"><span data-stu-id="f6e52-127">Configure a connection</span></span>

1. <span data-ttu-id="f6e52-128">Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="f6e52-128">Go to **Admin** > **Connections**.</span></span>

1. <span data-ttu-id="f6e52-129">Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza az **Azure Blob Storage** vagy a **Beállítás** lehetőséget az **Azure Blob Storage** csempén:</span><span class="sxs-lookup"><span data-stu-id="f6e52-129">Select **Add connection** and choose **Azure Blob Storage** or select **Set up** in the **Azure Blob Storage** tile:</span></span>

   :::image type="content" source="media/export-azure-blob-storage-tile.png" alt-text="Az Azure Blob Storage konfigurációs csempéje."::: <span data-ttu-id="f6e52-131">a kapcsolat konfigurálásához.</span><span class="sxs-lookup"><span data-stu-id="f6e52-131">to configure the connection.</span></span>

1. <span data-ttu-id="f6e52-132">Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak.</span><span class="sxs-lookup"><span data-stu-id="f6e52-132">Give your connection a recognizable name in the **Display name** field.</span></span> <span data-ttu-id="f6e52-133">A név és a kapcsolat típusa írja le ezt a kapcsolatot.</span><span class="sxs-lookup"><span data-stu-id="f6e52-133">The name and the type of the connection describe this connection.</span></span> <span data-ttu-id="f6e52-134">Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.</span><span class="sxs-lookup"><span data-stu-id="f6e52-134">We recommend choosing a name that explains the purpose and target of the connection.</span></span>

1. <span data-ttu-id="f6e52-135">A kapcsolat használóinak kiválasztása.</span><span class="sxs-lookup"><span data-stu-id="f6e52-135">Choose who can use this connection.</span></span> <span data-ttu-id="f6e52-136">Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz.</span><span class="sxs-lookup"><span data-stu-id="f6e52-136">If you take no action, the default will be Administrators.</span></span> <span data-ttu-id="f6e52-137">További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).</span><span class="sxs-lookup"><span data-stu-id="f6e52-137">For more information, see [Allow contributors to use a connection for exports](connections.md#allow-contributors-to-use-a-connection-for-exports).</span></span>

1. <span data-ttu-id="f6e52-138">Adja meg annak a Blob Storage fióknak a **Fiók nevét**, **Fiókkulcsát** és **Tárolóját**, ahová exportálni szeretné a szegmenst.</span><span class="sxs-lookup"><span data-stu-id="f6e52-138">Enter **Account name**, **Account key**, and **Container** for your Blob storage account where you want to export the segment to.</span></span>  
      
   :::image type="content" source="media/azure-blob-configuration.png" alt-text="Képernyőkép a tárfiók konfigurációjáról."::: 
   
    - <span data-ttu-id="f6e52-140">Ha szeretne többet megtudni arról, hogyan találja meg a Blob Storage-fiók nevét és fiókkulcsát, olvassa el a [Tárhelyfiók beállításainak kezelése az Azure-portálon](/azure/storage/common/storage-account-manage) részt.</span><span class="sxs-lookup"><span data-stu-id="f6e52-140">To learn more about how to find the Blob storage account name and account key, see [Manage storage account settings in the Azure portal](/azure/storage/common/storage-account-manage).</span></span>
    - <span data-ttu-id="f6e52-141">A tároló létrehozásával kapcsolatosan lásd: [Tároló létrehozása](/azure/storage/blobs/storage-quickstart-blobs-portal#create-a-container).</span><span class="sxs-lookup"><span data-stu-id="f6e52-141">To learn how to create a container, see [Create a container](/azure/storage/blobs/storage-quickstart-blobs-portal#create-a-container).</span></span>

1. <span data-ttu-id="f6e52-142">A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="f6e52-142">Select **Save** to complete the connection.</span></span> 

### <a name="configure-an-export"></a><span data-ttu-id="f6e52-143">Exportálás konfigurálása</span><span class="sxs-lookup"><span data-stu-id="f6e52-143">Configure an export</span></span>

<span data-ttu-id="f6e52-144">Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz.</span><span class="sxs-lookup"><span data-stu-id="f6e52-144">You can configure this export if you have access to a connection of this type.</span></span> <span data-ttu-id="f6e52-145">További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).</span><span class="sxs-lookup"><span data-stu-id="f6e52-145">For more information, see [Permissions needed to configure an export](export-destinations.md#set-up-a-new-export).</span></span>

1. <span data-ttu-id="f6e52-146">Menjen az **Adatok** > **Exportálások** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="f6e52-146">Go to **Data** > **Exports**.</span></span>

1. <span data-ttu-id="f6e52-147">Új exportálás létrehozásához válassza az **Exportálás hozzáadása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="f6e52-147">To create a new export, select **Add export**.</span></span>

1. <span data-ttu-id="f6e52-148">A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot az Azure Blob Storage szakaszból.</span><span class="sxs-lookup"><span data-stu-id="f6e52-148">In the **Connection for export** field, choose a connection from the Azure Blob Storage section.</span></span> <span data-ttu-id="f6e52-149">Ha nem látja ezt a szakasznevet, az Ön számára nincs ilyen típusú kapcsolat.</span><span class="sxs-lookup"><span data-stu-id="f6e52-149">If you don't see this section name, there are no connections of this type available to you.</span></span>

1. <span data-ttu-id="f6e52-150">Válassza ki az exportálni kívánt szegmenst.</span><span class="sxs-lookup"><span data-stu-id="f6e52-150">Choose the segment that you want to export.</span></span> <span data-ttu-id="f6e52-151">Ebben a példában ez a **ChurnProneCustomers**.</span><span class="sxs-lookup"><span data-stu-id="f6e52-151">In this example, it’s **ChurnProneCustomers**.</span></span>

   :::image type="content" source="media/select-segment-churnpronecustomers.png" alt-text="Képernyőkép a szegmenskijelölési felhasználói felületről, ahol a ChurnProneCustomers szegmens ki van választva.":::

1. <span data-ttu-id="f6e52-153">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="f6e52-153">Select **Save**.</span></span>

<span data-ttu-id="f6e52-154">Az exportálási cél mentése után az **Adatok** > **Exportálások** lehetőségnél található.</span><span class="sxs-lookup"><span data-stu-id="f6e52-154">After saving the export destination, you find it on **Data** > **Exports**.</span></span>

<span data-ttu-id="f6e52-155">Mostantól [igény szerint exportálhatja a szegmenst](export-destinations.md#run-exports-on-demand).</span><span class="sxs-lookup"><span data-stu-id="f6e52-155">You can now [export the segment on demand](export-destinations.md#run-exports-on-demand).</span></span> <span data-ttu-id="f6e52-156">Az exportálás minden [ütemezett frissítéssel](system.md) együtt is lefut.</span><span class="sxs-lookup"><span data-stu-id="f6e52-156">The export will also run with every [scheduled refresh](system.md).</span></span>

> [!NOTE]
> <span data-ttu-id="f6e52-157">Győződjön meg róla, hogy az exportált szegmens rekordjainak száma az Adobe Campaign Standard licencének megengedett korlátjan belül van.</span><span class="sxs-lookup"><span data-stu-id="f6e52-157">Ensure that the number of records in the exported segment are within the allowed limit of your Adobe Campaign Standard license.</span></span>

<span data-ttu-id="f6e52-158">Az exportált adatokat a rendszer a fent beállított Azure Blob Storage-tárolóban tárolja.</span><span class="sxs-lookup"><span data-stu-id="f6e52-158">Exported data is stored in the Azure Blob storage container you configured above.</span></span> <span data-ttu-id="f6e52-159">A következő mappa elérési útja automatikusan létrejön a tárolóban:</span><span class="sxs-lookup"><span data-stu-id="f6e52-159">The following folder path is automatically created in your container:</span></span>

<span data-ttu-id="f6e52-160">*%ContainerName%/CustomerInsights_%instanceID%/%ExportDestinationName%/%EntityName%/%Year%/%Month%/%Day%/%HHMM%/%EntityName%_%PartitionId%.csv*</span><span class="sxs-lookup"><span data-stu-id="f6e52-160">*%ContainerName%/CustomerInsights_%instanceID%/%ExportDestinationName%/%EntityName%/%Year%/%Month%/%Day%/%HHMM%/%EntityName%_%PartitionId%.csv*</span></span>

<span data-ttu-id="f6e52-161">Példa: Dynamics365CustomerInsights/CustomerInsights_abcd1234-4312-11f4-93dc-24f72f43e7d5/BlobExport/ChurnSegmentDemo/2021/02/16/1433/ChurnProneCustomers_1.csv</span><span class="sxs-lookup"><span data-stu-id="f6e52-161">Example: Dynamics365CustomerInsights/CustomerInsights_abcd1234-4312-11f4-93dc-24f72f43e7d5/BlobExport/ChurnSegmentDemo/2021/02/16/1433/ChurnProneCustomers_1.csv</span></span>

<span data-ttu-id="f6e52-162">Az exportált entitások *model.json* fájlja az *%ExportDestinationName%* szintjén helyezkedik el</span><span class="sxs-lookup"><span data-stu-id="f6e52-162">The *model.json* for the exported entities resides at the *%ExportDestinationName%* level.</span></span>

<span data-ttu-id="f6e52-163">Példa: Dynamics365CustomerInsights/CustomerInsights_abcd1234-4312-11f4-93dc-24f72f43e7d5/ChurnSegmentDemo/model.json</span><span class="sxs-lookup"><span data-stu-id="f6e52-163">Example: Dynamics365CustomerInsights/CustomerInsights_abcd1234-4312-11f4-93dc-24f72f43e7d5/ChurnSegmentDemo/model.json</span></span>

## <a name="define-experience-data-model-xdm-in-adobe-experience-platform"></a><span data-ttu-id="f6e52-164">A Tapasztalati adatmodell (XDM) definiálása az Adobe Experience Platformon</span><span class="sxs-lookup"><span data-stu-id="f6e52-164">Define Experience Data Model (XDM) in Adobe Experience Platform</span></span>

<span data-ttu-id="f6e52-165">Mielőtt az célközönség-információkból exportált adatokat használhatjuk az Adobe Experience Platformon belül, meg kell határozni a Tapasztalat adatmodell sémáját, és [konfigurálni kell az adatokat a valós idejű ügyfélprofilhoz](https://experienceleague.adobe.com/docs/experience-platform/profile/tutorials/dataset-configuration.html#tutorials).</span><span class="sxs-lookup"><span data-stu-id="f6e52-165">Before the exported data from audience insights can be used within Adobe Experience Platform, we need to define the Experience Data Model schema and [configure the data for the Real-time Customer Profile](https://experienceleague.adobe.com/docs/experience-platform/profile/tutorials/dataset-configuration.html#tutorials).</span></span>

<span data-ttu-id="f6e52-166">Ismerje meg, [mi az az XDM](https://experienceleague.adobe.com/docs/experience-platform/xdm/home.html), és ismerje meg a [sémaösszetétel alapjait](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html#schema).</span><span class="sxs-lookup"><span data-stu-id="f6e52-166">Learn [what XDM is](https://experienceleague.adobe.com/docs/experience-platform/xdm/home.html) and understand the [basics of schema composition](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html#schema).</span></span>

## <a name="import-data-into-adobe-experience-platform"></a><span data-ttu-id="f6e52-167">Adatok importálása az Adobe Experience Platformba</span><span class="sxs-lookup"><span data-stu-id="f6e52-167">Import data into Adobe Experience Platform</span></span>

<span data-ttu-id="f6e52-168">Most, hogy minden a helyén van, a profilok létrehozásához importálni kell az előkészített célközönségadatokat az célközönség-információkból az Adobe Experience Platformba.</span><span class="sxs-lookup"><span data-stu-id="f6e52-168">Now that everything is in place, we need to import the prepared audience data from audience insights into Adobe Experience Platform.</span></span>

<span data-ttu-id="f6e52-169">Először [hozzon létre egy Azure Blob Storage-forráskapcsolatot](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/cloud-storage/blob.html#getting-started).</span><span class="sxs-lookup"><span data-stu-id="f6e52-169">First, [create an Azure Blob Storage source connection](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/cloud-storage/blob.html#getting-started).</span></span>    

<span data-ttu-id="f6e52-170">A forráskapcsolat definiálása után [konfigurálja egy felhőalapú tároló kötegfájl-kapcsolat adatfolyamát](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/dataflow/cloud-storage.html#ui-tutorials), hogy a szegmens kimenetét a célközönség-információkból az Adobe Experience Platformba importálja.</span><span class="sxs-lookup"><span data-stu-id="f6e52-170">After defining the source connection, [configure a dataflow](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/dataflow/cloud-storage.html#ui-tutorials) for a cloud storage batch connection to import the segment output from audience insights into Adobe Experience Platform.</span></span>

## <a name="create-an-audience-in-adobe-campaign-standard"></a><span data-ttu-id="f6e52-171">A célközönség létrehozása az Adobe Campaign Standardban</span><span class="sxs-lookup"><span data-stu-id="f6e52-171">Create an audience in Adobe Campaign Standard</span></span>

<span data-ttu-id="f6e52-172">A kampányhoz tartozó e-mail elküldéséhez az Adobe Campaign Standardot fogjuk használni.</span><span class="sxs-lookup"><span data-stu-id="f6e52-172">To send the email for this campaign, we will use Adobe Campaign Standard.</span></span> <span data-ttu-id="f6e52-173">Miután importálta az adatokat az Adobe Experience Platformba, [létre kell hozni egy célközönséget](https://experienceleague.adobe.com/docs/campaign-standard/using/profiles-and-audiences/get-started-profiles-and-audiences.html#permission) az Adobe Campaign Standardban, az Adobe Experience Platform adatai segítségével.</span><span class="sxs-lookup"><span data-stu-id="f6e52-173">After importing the data into Adobe Experience Platform, we need to [create an audience](https://experienceleague.adobe.com/docs/campaign-standard/using/profiles-and-audiences/get-started-profiles-and-audiences.html#permission) in Adobe Campaign Standard using the data in Adobe Experience Platform.</span></span>

<span data-ttu-id="f6e52-174">Ismerje meg, hogyan [használható a szegmensszerkesztő](https://experienceleague.adobe.com/docs/campaign-standard/using/profiles-and-audiences/working-with-adobe-experience-platform/aep-using-segment-builder.html#building-a-segment) az Adobe Campaign Standardban egy célközönség meghatározásához az Adobe Experience Platform adatai alapján.</span><span class="sxs-lookup"><span data-stu-id="f6e52-174">Learn how to [use segment builder](https://experienceleague.adobe.com/docs/campaign-standard/using/profiles-and-audiences/working-with-adobe-experience-platform/aep-using-segment-builder.html#building-a-segment) in Adobe Campaign Standard to define an audience based on the data in Adobe Experience Platform.</span></span>

## <a name="create-and-send-the-email-using-adobe-campaign-standard"></a><span data-ttu-id="f6e52-175">Az e-mail létrehozása és elküldése az Adobe Campaign Standard használatával</span><span class="sxs-lookup"><span data-stu-id="f6e52-175">Create and send the email using Adobe Campaign Standard</span></span>

<span data-ttu-id="f6e52-176">Hozza létre az e-mail tartalmát, majd [tesztelje, és küldje el](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/get-started-sending-messages.html#preparing-and-testing-messages) az e-mailt.</span><span class="sxs-lookup"><span data-stu-id="f6e52-176">Create the email content and then [test and send](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/get-started-sending-messages.html#preparing-and-testing-messages) your email.</span></span>

:::image type="content" source="media/contoso-sample-email.jpg" alt-text="E-mail minta az Adobe Campaign Standard megújítási ajánlatával.":::
