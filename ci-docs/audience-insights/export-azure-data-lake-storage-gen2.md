---
title: Customer Insights adatok exportálása Azure Data Lake Storage Gen 2 tárhelyre
description: Megismerheti, hogyan konfigurálható a kapcsolat az Azure Data Lake Storage Gen2 tárhellyel.
ms.date: 03/03/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: stefanie-msft
ms.author: sthe
manager: shellyha
ms.openlocfilehash: f431b707e1d65ffe47f8b3aa1c52abaa964e871a
ms.sourcegitcommit: 1b671c6100991fea1cace04b5d4fcedcd88aa94f
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/31/2021
ms.locfileid: "5760054"
---
# <a name="set-up-the-connection-to-azure-data-lake-storage-gen2-preview"></a><span data-ttu-id="2fac2-103">Állítsa be az Azure Data Lake Storage Gen2-vel való kapcsolatot (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="2fac2-103">Set up the connection to Azure Data Lake Storage Gen2 (preview)</span></span>

1. <span data-ttu-id="2fac2-104">Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="2fac2-104">Go to **Admin** > **Connections**.</span></span>

1. <span data-ttu-id="2fac2-105">Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza az **Azure Data Lake Gen 2** lehetőséget a kapcsolat konfigurálásához.</span><span class="sxs-lookup"><span data-stu-id="2fac2-105">Select **Add connection** and choose **Azure Data Lake Gen 2** to configure the connection.</span></span>

1. <span data-ttu-id="2fac2-106">Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak.</span><span class="sxs-lookup"><span data-stu-id="2fac2-106">Give your connection a recognizable name in the **Display name** field.</span></span> <span data-ttu-id="2fac2-107">A név és a kapcsolat típusa írja le ezt a kapcsolatot.</span><span class="sxs-lookup"><span data-stu-id="2fac2-107">The name and the type of the connection describe this connection.</span></span> <span data-ttu-id="2fac2-108">Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.</span><span class="sxs-lookup"><span data-stu-id="2fac2-108">We recommend choosing a name that explains the purpose and target of the connection.</span></span>

1. <span data-ttu-id="2fac2-109">A kapcsolat használóinak kiválasztása.</span><span class="sxs-lookup"><span data-stu-id="2fac2-109">Choose who can use this connection.</span></span> <span data-ttu-id="2fac2-110">Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz.</span><span class="sxs-lookup"><span data-stu-id="2fac2-110">If you take no action, the default will be Administrators.</span></span> <span data-ttu-id="2fac2-111">További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).</span><span class="sxs-lookup"><span data-stu-id="2fac2-111">For more information, see [Allow contributors to use a connection for exports](connections.md#allow-contributors-to-use-a-connection-for-exports).</span></span>

1. <span data-ttu-id="2fac2-112">Adja meg a **Fiók neve**, a **Fiók kulcsa** és a **Tároló** adatait az Azure Data Lake Storage Gen2 tárolóhoz.</span><span class="sxs-lookup"><span data-stu-id="2fac2-112">Enter **Account name**, **Account key**, and **Container** for your Azure Data Lake Storage Gen2.</span></span>
    - <span data-ttu-id="2fac2-113">Ha meg szeretne ismerkedni vele, hogyan hozhat létre tárhelyfiókot az Azure Data Lake Storage Gen2 tárhellyel való használatra, olvassa el a [Tárhelyfiók létrehozása](/azure/storage/blobs/create-data-lake-storage-account) részt.</span><span class="sxs-lookup"><span data-stu-id="2fac2-113">To learn how to create a storage account to use with Azure Data Lake Storage Gen2, see [Create storage account](/azure/storage/blobs/create-data-lake-storage-account).</span></span> 
    - <span data-ttu-id="2fac2-114">Ha szeretne többet megtudni az Azure Data Lake Gen2 tárfiók nevét és fiókkulcsát, olvassa el a [Tárhelyfiók beállításainak kezelése az Azure-portálon](/azure/storage/common/storage-account-manage) részt.</span><span class="sxs-lookup"><span data-stu-id="2fac2-114">To learn more about Azure Data Lake Gen2 storage account name and account key, see [Manage storage account settings in the Azure portal](/azure/storage/common/storage-account-manage).</span></span>

1. <span data-ttu-id="2fac2-115">A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="2fac2-115">Select **Save** to complete the connection.</span></span> 

## <a name="configure-an-export"></a><span data-ttu-id="2fac2-116">Exportálás konfigurálása</span><span class="sxs-lookup"><span data-stu-id="2fac2-116">Configure an export</span></span>

<span data-ttu-id="2fac2-117">Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz.</span><span class="sxs-lookup"><span data-stu-id="2fac2-117">You can configure this export if you have access to a connection of this type.</span></span> <span data-ttu-id="2fac2-118">További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).</span><span class="sxs-lookup"><span data-stu-id="2fac2-118">For more information, see [Permissions needed to configure an export](export-destinations.md#set-up-a-new-export).</span></span>

1. <span data-ttu-id="2fac2-119">Menjen az **Adatok** > **Exportálások** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="2fac2-119">Go to **Data** > **Exports**.</span></span>

1. <span data-ttu-id="2fac2-120">Új exportálás létrehozásához válassza az **Exportálás hozzáadása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="2fac2-120">To create a new export, select **Add export**.</span></span>

1. <span data-ttu-id="2fac2-121">A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot az **Azure Data Lake** szakaszból.</span><span class="sxs-lookup"><span data-stu-id="2fac2-121">In the **Connection for export** field, choose a connection from the **Azure Data Lake** section.</span></span> <span data-ttu-id="2fac2-122">Ha nem látja ezt a szakasznevet, az Ön számára nincs ilyen típusú kapcsolat.</span><span class="sxs-lookup"><span data-stu-id="2fac2-122">If you don't see this section name, there are no connections of this type available to you.</span></span>

1. <span data-ttu-id="2fac2-123">Jelölje be a jelölőnégyzetet azon entitások mellett, amelyeket exportálni szeretne erre a célhelyre.</span><span class="sxs-lookup"><span data-stu-id="2fac2-123">Select the box next to each of the entities you want to export to this destination.</span></span>

1. <span data-ttu-id="2fac2-124">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="2fac2-124">Select **Save**.</span></span>

<span data-ttu-id="2fac2-125">Az exportálás mentése nem futtatja azonnal az exportálást.</span><span class="sxs-lookup"><span data-stu-id="2fac2-125">Saving an export doesn't run the export immediately.</span></span>

<span data-ttu-id="2fac2-126">Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut.</span><span class="sxs-lookup"><span data-stu-id="2fac2-126">The export runs with every [scheduled refresh](system.md#schedule-tab).</span></span> <span data-ttu-id="2fac2-127">Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand).</span><span class="sxs-lookup"><span data-stu-id="2fac2-127">You can also [export data on demand](export-destinations.md#run-exports-on-demand).</span></span> 

<span data-ttu-id="2fac2-128">Az exportált adatok az Ön által konfigurált az Azure Data Lake Gen 2 tárolóban lesznek tárolva.</span><span class="sxs-lookup"><span data-stu-id="2fac2-128">Exported data is stored in the Azure Data Lake Gen 2 storage container you configured.</span></span> 

[!INCLUDE[footer-include](../includes/footer-banner.md)]
