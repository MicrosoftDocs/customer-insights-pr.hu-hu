---
title: Customer Insights adatok exportálása Azure Data Lake Storage Gen 2 tárhelyre
description: Megismerheti, hogyan konfigurálható a kapcsolat az Azure Data Lake Storage Gen2 tárhellyel.
ms.date: 02/04/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: stefanie-msft
ms.author: sthe
manager: shellyha
ms.openlocfilehash: 7c0eef575f745efa6312d7141a6dd96607f9797e
ms.sourcegitcommit: bae40184312ab27b95c140a044875c2daea37951
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/15/2021
ms.locfileid: "5596640"
---
# <a name="connector-for-azure-data-lake-storage-gen2-preview"></a><span data-ttu-id="e846a-103">Az Azure Data Lake Storage Gen2 összekötője (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="e846a-103">Connector for Azure Data Lake Storage Gen2 (preview)</span></span>

<span data-ttu-id="e846a-104">A Customer Insights-adatokat az Azure Data Lake Storage Gen2 tárolóban tárolhatja, vagy segítségével adatait más alkalmazásokba továbbíthatja.</span><span class="sxs-lookup"><span data-stu-id="e846a-104">Store your Customer Insights data in Azure Data Lake Storage Gen2 or use it to transfer your data to other applications.</span></span>

## <a name="configure-the-connector-for-azure-data-lake-storage-gen2"></a><span data-ttu-id="e846a-105">Az Azure Data Lake Storage Gen2 összekötőjének konfigurálása</span><span class="sxs-lookup"><span data-stu-id="e846a-105">Configure the connector for Azure Data Lake Storage Gen2</span></span>

1. <span data-ttu-id="e846a-106">A célközönség információin belül nyissa meg a következőt **Rendszergazda** > **Exportálási célhelyek**.</span><span class="sxs-lookup"><span data-stu-id="e846a-106">In audience insights, go to **Admin** > **Export destinations**.</span></span>

1. <span data-ttu-id="e846a-107">A **Azure Data Lake Storage Gen2** részben válassza a **Beállítás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="e846a-107">Under **Azure Data Lake Storage Gen2**, select **Set up**.</span></span>

1. <span data-ttu-id="e846a-108">Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben.</span><span class="sxs-lookup"><span data-stu-id="e846a-108">Give your destination a recognizable name in the **Display name** field.</span></span>

1. <span data-ttu-id="e846a-109">Adja meg a **Fiók neve**, a **Fiók kulcsa** és a **Tároló** adatait az Azure Data Lake Storage Gen2 tárolóhoz.</span><span class="sxs-lookup"><span data-stu-id="e846a-109">Enter **Account name**, **Account key**, and **Container** for your Azure Data Lake Storage Gen2.</span></span>
    - <span data-ttu-id="e846a-110">Ha meg szeretne ismerkedni vele, hogyan hozhat létre tárhelyfiókot az Azure Data Lake Storage Gen2 tárhellyel való használatra, olvassa el a [Tárhelyfiók létrehozása](/azure/storage/blobs/create-data-lake-storage-account) részt.</span><span class="sxs-lookup"><span data-stu-id="e846a-110">To learn how to create a storage account to use with Azure Data Lake Storage Gen2, see [Create storage account](/azure/storage/blobs/create-data-lake-storage-account).</span></span> 
    - <span data-ttu-id="e846a-111">Ha szeretne többet megtudni az Azure Data Lake Gen2 tárfiók nevének és fiókkulcsának megkereséséről, olvassa el a [Tárfiók beállításainak kezelése az Azure portálon](/azure/storage/common/storage-account-manage) című részt.</span><span class="sxs-lookup"><span data-stu-id="e846a-111">To learn more about how to find the Azure Data Lake Gen2 storage account name and account key, see [Manage storage account settings in the Azure portal](/azure/storage/common/storage-account-manage).</span></span>

1. <span data-ttu-id="e846a-112">Válassza a **Következő** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="e846a-112">Select **Next**.</span></span>

1. <span data-ttu-id="e846a-113">Jelölje be a jelölőnégyzetet azon entitások mellett, amelyeket exportálni szeretne erre a célhelyre.</span><span class="sxs-lookup"><span data-stu-id="e846a-113">Select the box next to each of the entities you want to export to this destination.</span></span>

1. <span data-ttu-id="e846a-114">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="e846a-114">Select **Save**.</span></span>

## <a name="export-the-data"></a><span data-ttu-id="e846a-115">Az adatok exportálása</span><span class="sxs-lookup"><span data-stu-id="e846a-115">Export the data</span></span>

<span data-ttu-id="e846a-116">[Igény szerint exportálhatja az adatot](export-destinations.md#export-data-on-demand).</span><span class="sxs-lookup"><span data-stu-id="e846a-116">You can [export data on demand](export-destinations.md#export-data-on-demand).</span></span> <span data-ttu-id="e846a-117">Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) együtt is lefut.</span><span class="sxs-lookup"><span data-stu-id="e846a-117">The export will also run with every [scheduled refresh](system.md#schedule-tab).</span></span>