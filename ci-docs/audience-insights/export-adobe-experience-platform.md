---
title: A Customer Insights adatainak exportálása az Adobe Experience Platformba
description: További információ a célközönség elemzési szegmensek használatáról az Adobe Experience Platformon.
ms.date: 03/29/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: stefanie-msft
ms.author: antando
manager: shellyha
ms.openlocfilehash: 1045d0e373fd5ea8987684e51bd9a07b7b535ee3
ms.sourcegitcommit: d84d664e67f263bfeb741154d309088c5101b9c3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/24/2021
ms.locfileid: "6305527"
---
# <a name="use-customer-insights-segments-in-adobe-experience-platform-preview"></a><span data-ttu-id="71d91-103">A Customer Insights-szegmensek használata az Adobe Experience Platformban (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="71d91-103">Use Customer Insights segments in Adobe Experience Platform (preview)</span></span>

<span data-ttu-id="71d91-104">A célközönségi elemzések felhasználójaként Dynamics 365 Customer Insights -ban előfordulhat, hogy szegmenseket hozott létre, hogy hatékonyabbá tegye marketingkampányait a releváns célközönségek megcélzásával.</span><span class="sxs-lookup"><span data-stu-id="71d91-104">As a user of audience insights in Dynamics 365 Customer Insights, you may have created segments to make your marketing campaigns more efficient by targeting relevant audiences.</span></span> <span data-ttu-id="71d91-105">Az Adobe Experience Platformban és az Adobe Campaign Standardhoz hasonló alkalmazásokban található célközönség-információs szegmensek használatához a jelen cikkben ismertetett lépéseket kell követnie.</span><span class="sxs-lookup"><span data-stu-id="71d91-105">To use a segment from audience insights in Adobe Experience Platform and applications like Adobe Campaign Standard, you need to follow a few steps outlined in this article.</span></span>

:::image type="content" source="media/AEP-flow.png" alt-text="A jelen cikkben ismertetett lépések folyamatábrája.":::

## <a name="prerequisites"></a><span data-ttu-id="71d91-107">Előfeltételek</span><span class="sxs-lookup"><span data-stu-id="71d91-107">Prerequisites</span></span>

-   <span data-ttu-id="71d91-108">Dynamics 365 Customer Insights licenc</span><span class="sxs-lookup"><span data-stu-id="71d91-108">Dynamics 365 Customer Insights license</span></span>
-   <span data-ttu-id="71d91-109">Adobe Experience Platform-licenc</span><span class="sxs-lookup"><span data-stu-id="71d91-109">Adobe Experience Platform license</span></span>
-   <span data-ttu-id="71d91-110">Adobe Campaign Standard-licenc</span><span class="sxs-lookup"><span data-stu-id="71d91-110">Adobe Campaign Standard license</span></span>
-   <span data-ttu-id="71d91-111">Azure Blob Storage-fiók</span><span class="sxs-lookup"><span data-stu-id="71d91-111">Azure Blob Storage account</span></span>

## <a name="campaign-overview"></a><span data-ttu-id="71d91-112">Kampány áttekintése</span><span class="sxs-lookup"><span data-stu-id="71d91-112">Campaign Overview</span></span>

<span data-ttu-id="71d91-113">Hogy jobban meg tudja érteni, hogyan használhatja a célközönség-információs szegmenseket az Adobe Experience Platformban, tekintsünk át egy kitalált mintakampányt.</span><span class="sxs-lookup"><span data-stu-id="71d91-113">To better understand how you can use segments from audience insights in Adobe Experience Platform, let’s look at a fictitious sample campaign.</span></span>

<span data-ttu-id="71d91-114">Tegyük fel, hogy a vállalata havi előfizetéses szolgáltatást kínál egyesült államokbeli ügyfeleinek.</span><span class="sxs-lookup"><span data-stu-id="71d91-114">Let’s assume that your company offers a monthly, subscription-based service to your customers in the United States.</span></span> <span data-ttu-id="71d91-115">Meg szeretné határozni azokat az ügyfeleket, akiknek az előfizetései a következő nyolc napban megújításra esedékesek, de még nem újították meg előfizetésüket.</span><span class="sxs-lookup"><span data-stu-id="71d91-115">You want to identify customers whose subscriptions are due for renewal in the next eight days but haven't yet renewed their subscription.</span></span> <span data-ttu-id="71d91-116">Ezeknek az ügyfeleknek a megtartása érdekében e-mailben szeretne promóciós ajánlatot küldeni nekik az Adobe Experience Platform segítségével.</span><span class="sxs-lookup"><span data-stu-id="71d91-116">To keep these customers, you want to send them a promotional offer via email, using Adobe Experience Platform.</span></span>

<span data-ttu-id="71d91-117">Ebben a példában egy promóciós e-mail-kampányt egyszer szeretnénk futtatni.</span><span class="sxs-lookup"><span data-stu-id="71d91-117">In this example, we want to run the promotional email campaign once.</span></span> <span data-ttu-id="71d91-118">Ez a cikk nem terjed ki a kampány egynél több esetben való futtatásának esetére.</span><span class="sxs-lookup"><span data-stu-id="71d91-118">This article doesn’t cover the use-case of running the campaign more than once.</span></span>

## <a name="identify-your-target-audience"></a><span data-ttu-id="71d91-119">Azonosítsa a célközönséget</span><span class="sxs-lookup"><span data-stu-id="71d91-119">Identify your target audience</span></span>

<span data-ttu-id="71d91-120">A mi esetünkben feltételezzük, hogy az ügyfelek e-mail-címei elérhetők a célközönség-információkban, és promóciós preferenciáik elemzésével azonosítottuk a szegmens tagjait.</span><span class="sxs-lookup"><span data-stu-id="71d91-120">In our scenario, we assume that the email addresses of the customers are available in audience insights and their promotional preferences were analyzed to identify members of the segment.</span></span>

<span data-ttu-id="71d91-121">A [célközönség-információkban meghatározott szegmens](segments.md) neve **ChurnProneCustomers**, és az e-mail-promóció elküldését tervezi ezeknek az ügyfeleknek.</span><span class="sxs-lookup"><span data-stu-id="71d91-121">The [segment you defined in audience insights](segments.md) is called **ChurnProneCustomers** and you plan to send these customers the email promotion.</span></span>

:::image type="content" source="media/churn-prone-customers-segment.png" alt-text="Képernyőfelvétel a Szegmensek oldalról, amelyen a létrehozott ChurnProneCustomers szegmens látható.":::

<span data-ttu-id="71d91-123">Az elküldeni kívánt ajánlati e-mail tartalmazza az ügyfél utónevét, vezetéknevét és az előfizetés záró dátumát.</span><span class="sxs-lookup"><span data-stu-id="71d91-123">The offer email that you want to send out will contain the first name, last name, and the subscription end date of the customer.</span></span> <span data-ttu-id="71d91-124">Tájékoztatja az ügyfeleket az arról az engedményről, amit akkor kapnak, ha a vége előtt megújítják az előfizetésüket.</span><span class="sxs-lookup"><span data-stu-id="71d91-124">It informs the customers about the discount they’ll get if they renew their subscription before it ends.</span></span>

## <a name="export-your-target-audience"></a><span data-ttu-id="71d91-125">Exportálja a célközönséget</span><span class="sxs-lookup"><span data-stu-id="71d91-125">Export your target audience</span></span>

<span data-ttu-id="71d91-126">Az azonosított célközönség segítségével konfigurálható az exportálás az célközönség-információkból egy Azure Blob Storage-fiókba.</span><span class="sxs-lookup"><span data-stu-id="71d91-126">With our target audience identified, we can configure the export from audience insights to an Azure Blob Storage account.</span></span>

### <a name="configure-a-connection"></a><span data-ttu-id="71d91-127">Kapcsolat konfigurálása</span><span class="sxs-lookup"><span data-stu-id="71d91-127">Configure a connection</span></span>

1. <span data-ttu-id="71d91-128">Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="71d91-128">Go to **Admin** > **Connections**.</span></span>

1. <span data-ttu-id="71d91-129">Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza az **Azure Blob Storage** vagy válassza a **Beállítás** lehetőséget az **Azure Blob Storage** csempében a kapcsolat konfigurálásához.</span><span class="sxs-lookup"><span data-stu-id="71d91-129">Select **Add connection** and choose **Azure Blob Storage** or select **Set up** in the **Azure Blob Storage** tile to configure the connection.</span></span>

   :::image type="content" source="media/export-azure-blob-storage-tile.png" alt-text="Az Azure Blob Storage konfigurációs csempéje."::: 

1. <span data-ttu-id="71d91-131">Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak.</span><span class="sxs-lookup"><span data-stu-id="71d91-131">Give your connection a recognizable name in the **Display name** field.</span></span> <span data-ttu-id="71d91-132">A név és a kapcsolat típusa írja le ezt a kapcsolatot.</span><span class="sxs-lookup"><span data-stu-id="71d91-132">The name and the type of the connection describe this connection.</span></span> <span data-ttu-id="71d91-133">Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.</span><span class="sxs-lookup"><span data-stu-id="71d91-133">We recommend choosing a name that explains the purpose and target of the connection.</span></span>

1. <span data-ttu-id="71d91-134">A kapcsolat használóinak kiválasztása.</span><span class="sxs-lookup"><span data-stu-id="71d91-134">Choose who can use this connection.</span></span> <span data-ttu-id="71d91-135">Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz.</span><span class="sxs-lookup"><span data-stu-id="71d91-135">If you take no action, the default will be Administrators.</span></span> <span data-ttu-id="71d91-136">További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).</span><span class="sxs-lookup"><span data-stu-id="71d91-136">For more information, see [Allow contributors to use a connection for exports](connections.md#allow-contributors-to-use-a-connection-for-exports).</span></span>

1. <span data-ttu-id="71d91-137">Adja meg annak a Blob Storage fióknak a **Fiók nevét**, **Fiókkulcsát** és **Tárolóját**, ahová exportálni szeretné a szegmenst.</span><span class="sxs-lookup"><span data-stu-id="71d91-137">Enter **Account name**, **Account key**, and **Container** for your Blob Storage account where you want to export the segment to.</span></span>  
      
   :::image type="content" source="media/azure-blob-configuration.png" alt-text="Képernyőkép a tárfiók konfigurációjáról."::: 
   
    - <span data-ttu-id="71d91-139">Ha szeretne többet megtudni arról, hogyan találja meg a Blob Storage fiók nevét és fiókkulcsát, olvassa el a [Tárfiók beállításainak kezelése az Azure-portálon](/azure/storage/common/storage-account-manage) részt.</span><span class="sxs-lookup"><span data-stu-id="71d91-139">To learn more about how to find the Blob Storage account name and account key, see [Manage storage account settings in the Azure portal](/azure/storage/common/storage-account-manage).</span></span>
    - <span data-ttu-id="71d91-140">A tároló létrehozásával kapcsolatosan lásd: [Tároló létrehozása](/azure/storage/blobs/storage-quickstart-blobs-portal#create-a-container).</span><span class="sxs-lookup"><span data-stu-id="71d91-140">To learn how to create a container, see [Create a container](/azure/storage/blobs/storage-quickstart-blobs-portal#create-a-container).</span></span>

1. <span data-ttu-id="71d91-141">A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="71d91-141">Select **Save** to complete the connection.</span></span> 

### <a name="configure-an-export"></a><span data-ttu-id="71d91-142">Exportálás konfigurálása</span><span class="sxs-lookup"><span data-stu-id="71d91-142">Configure an export</span></span>

<span data-ttu-id="71d91-143">Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz.</span><span class="sxs-lookup"><span data-stu-id="71d91-143">You can configure this export if you have access to a connection of this type.</span></span> <span data-ttu-id="71d91-144">További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).</span><span class="sxs-lookup"><span data-stu-id="71d91-144">For more information, see [Permissions needed to configure an export](export-destinations.md#set-up-a-new-export).</span></span>

1. <span data-ttu-id="71d91-145">Menjen az **Adatok** > **Exportálások** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="71d91-145">Go to **Data** > **Exports**.</span></span>

1. <span data-ttu-id="71d91-146">Új exportálás létrehozásához válassza az **Exportálás hozzáadása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="71d91-146">To create a new export, select **Add export**.</span></span>

1. <span data-ttu-id="71d91-147">A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot az Azure Blob Storage szakaszból.</span><span class="sxs-lookup"><span data-stu-id="71d91-147">In the **Connection for export** field, choose a connection from the Azure Blob Storage section.</span></span> <span data-ttu-id="71d91-148">Ha nem látja ezt a szakasznevet, akkor ilyen típusú kapcsolatok nem állnak az Ön rendelkezésére.</span><span class="sxs-lookup"><span data-stu-id="71d91-148">If you don't see this section name, then no connections of this type are available to you.</span></span>

1. <span data-ttu-id="71d91-149">Válassza ki az exportálni kívánt szegmenst.</span><span class="sxs-lookup"><span data-stu-id="71d91-149">Choose the segment that you want to export.</span></span> <span data-ttu-id="71d91-150">Ebben a példában ez a **ChurnProneCustomers**.</span><span class="sxs-lookup"><span data-stu-id="71d91-150">In this example, it’s **ChurnProneCustomers**.</span></span>

   :::image type="content" source="media/select-segment-churnpronecustomers.png" alt-text="Képernyőkép a szegmenskijelölési felhasználói felületről, ahol a ChurnProneCustomers szegmens ki van választva.":::

1. <span data-ttu-id="71d91-152">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="71d91-152">Select **Save**.</span></span>

<span data-ttu-id="71d91-153">Az exportálási cél mentése után az **Adatok** > **Exportálások** lehetőségnél található.</span><span class="sxs-lookup"><span data-stu-id="71d91-153">After saving the export destination, you find it on **Data** > **Exports**.</span></span>

<span data-ttu-id="71d91-154">Mostantól [igény szerint exportálhatja a szegmenst](export-destinations.md#run-exports-on-demand).</span><span class="sxs-lookup"><span data-stu-id="71d91-154">You can now [export the segment on demand](export-destinations.md#run-exports-on-demand).</span></span> <span data-ttu-id="71d91-155">Az exportálás minden [ütemezett frissítéssel](system.md) együtt is lefut.</span><span class="sxs-lookup"><span data-stu-id="71d91-155">The export will also run with every [scheduled refresh](system.md).</span></span>

> [!NOTE]
> <span data-ttu-id="71d91-156">Győződjön meg róla, hogy az exportált szegmens rekordjainak száma az Adobe Campaign Standard licencének megengedett korlátjan belül van.</span><span class="sxs-lookup"><span data-stu-id="71d91-156">Ensure that the number of records in the exported segment are within the allowed limit of your Adobe Campaign Standard license.</span></span>

<span data-ttu-id="71d91-157">Az exportált adatokat a rendszer a fent beállított Azure Blob Storage tárolóban tárolja.</span><span class="sxs-lookup"><span data-stu-id="71d91-157">Exported data is stored in the Azure Blob Storage container you configured above.</span></span> <span data-ttu-id="71d91-158">A következő mappa elérési útja automatikusan létrejön a tárolóban:</span><span class="sxs-lookup"><span data-stu-id="71d91-158">The following folder path is automatically created in your container:</span></span>

<span data-ttu-id="71d91-159">*%ContainerName%/CustomerInsights_%instanceID%/%ExportDestinationName%/%EntityName%/%Year%/%Month%/%Day%/%HHMM%/%EntityName%_%PartitionId%.csv*</span><span class="sxs-lookup"><span data-stu-id="71d91-159">*%ContainerName%/CustomerInsights_%instanceID%/%ExportDestinationName%/%EntityName%/%Year%/%Month%/%Day%/%HHMM%/%EntityName%_%PartitionId%.csv*</span></span>

<span data-ttu-id="71d91-160">Példa: Dynamics365CustomerInsights/CustomerInsights_abcd1234-4312-11f4-93dc-24f72f43e7d5/BlobExport/ChurnSegmentDemo/2021/02/16/1433/ChurnProneCustomers_1.csv</span><span class="sxs-lookup"><span data-stu-id="71d91-160">Example: Dynamics365CustomerInsights/CustomerInsights_abcd1234-4312-11f4-93dc-24f72f43e7d5/BlobExport/ChurnSegmentDemo/2021/02/16/1433/ChurnProneCustomers_1.csv</span></span>

<span data-ttu-id="71d91-161">Az exportált entitások *model.json* fájlja az *%ExportDestinationName%* szintjén helyezkedik el</span><span class="sxs-lookup"><span data-stu-id="71d91-161">The *model.json* for the exported entities resides at the *%ExportDestinationName%* level.</span></span>

<span data-ttu-id="71d91-162">Példa: Dynamics365CustomerInsights/CustomerInsights_abcd1234-4312-11f4-93dc-24f72f43e7d5/ChurnSegmentDemo/model.json</span><span class="sxs-lookup"><span data-stu-id="71d91-162">Example: Dynamics365CustomerInsights/CustomerInsights_abcd1234-4312-11f4-93dc-24f72f43e7d5/ChurnSegmentDemo/model.json</span></span>

## <a name="define-experience-data-model-xdm-in-adobe-experience-platform"></a><span data-ttu-id="71d91-163">A Tapasztalati adatmodell (XDM) definiálása az Adobe Experience Platformon</span><span class="sxs-lookup"><span data-stu-id="71d91-163">Define Experience Data Model (XDM) in Adobe Experience Platform</span></span>

<span data-ttu-id="71d91-164">Mielőtt az célközönség-információkból exportált adatokat használhatjuk az Adobe Experience Platformon belül, meg kell határozni a Tapasztalat adatmodell sémáját, és [konfigurálni kell az adatokat a valós idejű ügyfélprofilhoz](https://experienceleague.adobe.com/docs/experience-platform/profile/tutorials/dataset-configuration.html#tutorials).</span><span class="sxs-lookup"><span data-stu-id="71d91-164">Before the exported data from audience insights can be used within Adobe Experience Platform, we need to define the Experience Data Model schema and [configure the data for the Real-time Customer Profile](https://experienceleague.adobe.com/docs/experience-platform/profile/tutorials/dataset-configuration.html#tutorials).</span></span>

<span data-ttu-id="71d91-165">Ismerje meg, [mi az az XDM](https://experienceleague.adobe.com/docs/experience-platform/xdm/home.html), és ismerje meg a [sémaösszetétel alapjait](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html#schema).</span><span class="sxs-lookup"><span data-stu-id="71d91-165">Learn [what XDM is](https://experienceleague.adobe.com/docs/experience-platform/xdm/home.html) and understand the [basics of schema composition](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html#schema).</span></span>

## <a name="import-data-into-adobe-experience-platform"></a><span data-ttu-id="71d91-166">Adatok importálása az Adobe Experience Platformba</span><span class="sxs-lookup"><span data-stu-id="71d91-166">Import data into Adobe Experience Platform</span></span>

<span data-ttu-id="71d91-167">Most, hogy minden a helyén van, a profilok létrehozásához importálni kell az előkészített célközönségadatokat az célközönség-információkból az Adobe Experience Platformba.</span><span class="sxs-lookup"><span data-stu-id="71d91-167">Now that everything is in place, we need to import the prepared audience data from audience insights into Adobe Experience Platform.</span></span>

<span data-ttu-id="71d91-168">Először [hozzon létre egy Azure Blob Storage-forráskapcsolatot](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/cloud-storage/blob.html#getting-started).</span><span class="sxs-lookup"><span data-stu-id="71d91-168">First, [create an Azure Blob Storage source connection](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/cloud-storage/blob.html#getting-started).</span></span>    

<span data-ttu-id="71d91-169">A forráskapcsolat definiálása után [konfigurálja egy felhőalapú tároló kötegfájl-kapcsolat adatfolyamát](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/dataflow/cloud-storage.html#ui-tutorials), hogy a szegmens kimenetét a célközönség-információkból az Adobe Experience Platformba importálja.</span><span class="sxs-lookup"><span data-stu-id="71d91-169">After defining the source connection, [configure a dataflow](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/dataflow/cloud-storage.html#ui-tutorials) for a cloud storage batch connection to import the segment output from audience insights into Adobe Experience Platform.</span></span>

## <a name="create-an-audience-in-adobe-campaign-standard"></a><span data-ttu-id="71d91-170">A célközönség létrehozása az Adobe Campaign Standardban</span><span class="sxs-lookup"><span data-stu-id="71d91-170">Create an audience in Adobe Campaign Standard</span></span>

<span data-ttu-id="71d91-171">A kampányhoz szükséges e-mail elküldéséhez az Adobe Campaign Standardot használjuk.</span><span class="sxs-lookup"><span data-stu-id="71d91-171">To send the email for this campaign, we'll use Adobe Campaign Standard.</span></span> <span data-ttu-id="71d91-172">Miután importálta az adatokat az Adobe Experience Platformba, [létre kell hozni egy célközönséget](https://experienceleague.adobe.com/docs/campaign-standard/using/profiles-and-audiences/get-started-profiles-and-audiences.html#permission) az Adobe Campaign Standardban, az Adobe Experience Platform adatai segítségével.</span><span class="sxs-lookup"><span data-stu-id="71d91-172">After importing the data into Adobe Experience Platform, we need to [create an audience](https://experienceleague.adobe.com/docs/campaign-standard/using/profiles-and-audiences/get-started-profiles-and-audiences.html#permission) in Adobe Campaign Standard using the data in Adobe Experience Platform.</span></span>


<span data-ttu-id="71d91-173">Ismerje meg, hogyan [használható a szegmensszerkesztő](https://experienceleague.adobe.com/docs/campaign-standard/using/integrating-with-adobe-cloud/adobe-experience-platform/audience-destinations/aep-using-segment-builder.html) az Adobe Campaign Standardban egy célközönség meghatározásához az Adobe Experience Platform adatai alapján.</span><span class="sxs-lookup"><span data-stu-id="71d91-173">Learn how to [use segment builder](https://experienceleague.adobe.com/docs/campaign-standard/using/integrating-with-adobe-cloud/adobe-experience-platform/audience-destinations/aep-using-segment-builder.html) in Adobe Campaign Standard to define an audience based on the data in Adobe Experience Platform.</span></span>

## <a name="create-and-send-the-email-using-adobe-campaign-standard"></a><span data-ttu-id="71d91-174">Az e-mail létrehozása és elküldése az Adobe Campaign Standard használatával</span><span class="sxs-lookup"><span data-stu-id="71d91-174">Create and send the email using Adobe Campaign Standard</span></span>

<span data-ttu-id="71d91-175">Hozza létre az e-mail tartalmát, majd [tesztelje, és küldje el](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/get-started-sending-messages.html#preparing-and-testing-messages) az e-mailt.</span><span class="sxs-lookup"><span data-stu-id="71d91-175">Create the email content and then [test and send](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/get-started-sending-messages.html#preparing-and-testing-messages) your email.</span></span>

:::image type="content" source="media/contoso-sample-email.jpg" alt-text="E-mail minta az Adobe Campaign Standard megújítási ajánlatával.":::
