---
title: A Customer Insights adatok exportálása az Azure Blob Storage rendszerbe
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a Blob Storage-ba.
ms.date: 03/03/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: phkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 294feff2f77c3756fbadb36c90aab430454f5967
ms.sourcegitcommit: 1b671c6100991fea1cace04b5d4fcedcd88aa94f
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/31/2021
ms.locfileid: "5760192"
---
# <a name="export-segment-list-and-other-data-to-azure-blob-storage-preview"></a><span data-ttu-id="9f9e6-103">Exportálja a szegmenslistát és az egyéb adatokat az Azure Blob Storage-ba (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="9f9e6-103">Export segment list and other data to Azure Blob Storage (preview)</span></span>

<span data-ttu-id="9f9e6-104">A Customer Insights-adatokat a Blob Storage-ban tárolhatja, vagy segítségével adatait más alkalmazásokba továbbíthatja.</span><span class="sxs-lookup"><span data-stu-id="9f9e6-104">Store your Customer Insights data in a Blob storage or use it to transfer your data to other applications.</span></span>

## <a name="set-up-the-connection-to-blob-storage"></a><span data-ttu-id="9f9e6-105">Állítsa be a Blob Storage-dzsal való kapcsolatot</span><span class="sxs-lookup"><span data-stu-id="9f9e6-105">Set up the connection to Blob storage</span></span>

1. <span data-ttu-id="9f9e6-106">Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="9f9e6-106">Go to **Admin** > **Connections**.</span></span>

1. <span data-ttu-id="9f9e6-107">Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza az **Azure Blob Storage** lehetőséget a kapcsolat konfigurálásához.</span><span class="sxs-lookup"><span data-stu-id="9f9e6-107">Select **Add connection** and choose **Azure Blob Storage** to configure the connection.</span></span>

1. <span data-ttu-id="9f9e6-108">Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak.</span><span class="sxs-lookup"><span data-stu-id="9f9e6-108">Give your connection a recognizable name in the **Display name** field.</span></span> <span data-ttu-id="9f9e6-109">A név és a kapcsolat típusa írja le ezt a kapcsolatot.</span><span class="sxs-lookup"><span data-stu-id="9f9e6-109">The name and the type of the connection describe this connection.</span></span> <span data-ttu-id="9f9e6-110">Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.</span><span class="sxs-lookup"><span data-stu-id="9f9e6-110">We recommend choosing a name that explains the purpose and target of the connection.</span></span>

1. <span data-ttu-id="9f9e6-111">A kapcsolat használóinak kiválasztása.</span><span class="sxs-lookup"><span data-stu-id="9f9e6-111">Choose who can use this connection.</span></span> <span data-ttu-id="9f9e6-112">Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz.</span><span class="sxs-lookup"><span data-stu-id="9f9e6-112">If you take no action, the default will be Administrators.</span></span> <span data-ttu-id="9f9e6-113">További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).</span><span class="sxs-lookup"><span data-stu-id="9f9e6-113">For more information, see [Allow contributors to use a connection for exports](connections.md#allow-contributors-to-use-a-connection-for-exports).</span></span>

1. <span data-ttu-id="9f9e6-114">Adja meg a Blob Storage fiókja **Fióknevét**, **Fiókkulcsát**, és **Tárolóját**.</span><span class="sxs-lookup"><span data-stu-id="9f9e6-114">Enter **Account name**, **Account key**, and **Container** for your Blob storage account.</span></span>
    - <span data-ttu-id="9f9e6-115">Ha szeretne többet megtudni arról, hogyan találja meg a Blob Storage-fiók nevét és fiókkulcsát, olvassa el a [Tárhelyfiók beállításainak kezelése az Azure-portálon](/azure/storage/common/storage-account-manage) részt.</span><span class="sxs-lookup"><span data-stu-id="9f9e6-115">To learn more about how to find the Blob storage account name and account key, see [Manage storage account settings in the Azure portal](/azure/storage/common/storage-account-manage).</span></span>
    - <span data-ttu-id="9f9e6-116">A tároló létrehozásával kapcsolatosan lásd: [Tároló létrehozása](/azure/storage/blobs/storage-quickstart-blobs-portal#create-a-container).</span><span class="sxs-lookup"><span data-stu-id="9f9e6-116">To learn how to create a container, see [Create a container](/azure/storage/blobs/storage-quickstart-blobs-portal#create-a-container).</span></span>

1. <span data-ttu-id="9f9e6-117">A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="9f9e6-117">Select **Save** to complete the connection.</span></span> 

## <a name="configure-an-export"></a><span data-ttu-id="9f9e6-118">Exportálás konfigurálása</span><span class="sxs-lookup"><span data-stu-id="9f9e6-118">Configure an export</span></span>

<span data-ttu-id="9f9e6-119">Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz.</span><span class="sxs-lookup"><span data-stu-id="9f9e6-119">You can configure this export if you have access to a connection of this type.</span></span> <span data-ttu-id="9f9e6-120">További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).</span><span class="sxs-lookup"><span data-stu-id="9f9e6-120">For more information, see [Permissions needed to configure an export](export-destinations.md#set-up-a-new-export).</span></span>

1. <span data-ttu-id="9f9e6-121">Menjen az **Adatok** > **Exportálások** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="9f9e6-121">Go to **Data** > **Exports**.</span></span>

1. <span data-ttu-id="9f9e6-122">Új exportálás létrehozásához válassza a **Célhely hozzáadása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="9f9e6-122">To create a new export, select **Add destination**.</span></span>

1. <span data-ttu-id="9f9e6-123">A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot az Azure Blob Storage szakaszból.</span><span class="sxs-lookup"><span data-stu-id="9f9e6-123">In the **Connection for export** field, choose a connection from the Azure Blob Storage section.</span></span> <span data-ttu-id="9f9e6-124">Ha nem látja ezt a szakasznevet, az Ön számára nincs ilyen típusú kapcsolat.</span><span class="sxs-lookup"><span data-stu-id="9f9e6-124">If you don't see this section name, there are no connections of this type available to you.</span></span>

1. <span data-ttu-id="9f9e6-125">Jelölje be a jelölőnégyzetet azon entitások mellett, amelyeket exportálni szeretne erre a célhelyre.</span><span class="sxs-lookup"><span data-stu-id="9f9e6-125">Select the box next to each of the entities you want to export to this destination.</span></span>

1. <span data-ttu-id="9f9e6-126">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="9f9e6-126">Select **Save**.</span></span>

<span data-ttu-id="9f9e6-127">Az exportálás mentése nem futtatja azonnal az exportálást.</span><span class="sxs-lookup"><span data-stu-id="9f9e6-127">Saving an export doesn't run the export immediately.</span></span>

<span data-ttu-id="9f9e6-128">Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut.</span><span class="sxs-lookup"><span data-stu-id="9f9e6-128">The export runs with every [scheduled refresh](system.md#schedule-tab).</span></span>     
<span data-ttu-id="9f9e6-129">Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand).</span><span class="sxs-lookup"><span data-stu-id="9f9e6-129">You can also [export data on demand](export-destinations.md#run-exports-on-demand).</span></span> 

<span data-ttu-id="9f9e6-130">Az exportált adatok az Ön által konfigurált Blob Storage tárolóban lesznek tárolva.</span><span class="sxs-lookup"><span data-stu-id="9f9e6-130">Exported data is stored in the Blob storage container you configured.</span></span> <span data-ttu-id="9f9e6-131">A tárolóban a következő elérési utak jönnek létre automatikusan:</span><span class="sxs-lookup"><span data-stu-id="9f9e6-131">The following folder paths are automatically created in your container:</span></span>

- <span data-ttu-id="9f9e6-132">A rendszer által létrehozott forrásoldali entitások és entitások esetén: `%ContainerName%/CustomerInsights_%instanceID%/%ExportDestinationName%/%EntityName%/%Year%/%Month%/%Day%/%HHMM%/%EntityName%_%PartitionId%.csv`</span><span class="sxs-lookup"><span data-stu-id="9f9e6-132">For source entities and entities generated by the system: `%ContainerName%/CustomerInsights_%instanceID%/%ExportDestinationName%/%EntityName%/%Year%/%Month%/%Day%/%HHMM%/%EntityName%_%PartitionId%.csv`</span></span>
  - <span data-ttu-id="9f9e6-133">Példa: `Dynamics365CustomerInsights/CustomerInsights_abcd1234-4312-11f4-93dc-24f72f43e7d5/BlobExport/HighValueSegment/2020/08/24/1433/HighValueSegment_1.csv`</span><span class="sxs-lookup"><span data-stu-id="9f9e6-133">Example: `Dynamics365CustomerInsights/CustomerInsights_abcd1234-4312-11f4-93dc-24f72f43e7d5/BlobExport/HighValueSegment/2020/08/24/1433/HighValueSegment_1.csv`</span></span>
- <span data-ttu-id="9f9e6-134">Az exportált entitások model.json fájlja a(z) %ExportDestinationName% szinten lesz</span><span class="sxs-lookup"><span data-stu-id="9f9e6-134">The model.json for the exported entities will be at the %ExportDestinationName% level</span></span>
  - <span data-ttu-id="9f9e6-135">Példa: `Dynamics365CustomerInsights/CustomerInsights_abcd1234-4312-11f4-93dc-24f72f43e7d5/BlobExport/model.json`</span><span class="sxs-lookup"><span data-stu-id="9f9e6-135">Example: `Dynamics365CustomerInsights/CustomerInsights_abcd1234-4312-11f4-93dc-24f72f43e7d5/BlobExport/model.json`</span></span>

[!INCLUDE[footer-include](../includes/footer-banner.md)]
