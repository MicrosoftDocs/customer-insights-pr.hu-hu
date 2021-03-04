---
title: Customer Insights adatok exportálása Azure Data Lake Storage Gen 2 tárhelyre
description: Megismerheti, hogyan konfigurálható a kapcsolat az Azure Data Lake Storage Gen2 tárhellyel.
ms.date: 02/04/2021
ms.reviewer: sthe
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: b00c3d6178150cbc93fe800779f094809d4dc67b
ms.sourcegitcommit: 0260ed244b97c2fd0be5e9a084c4c489358e8d4f
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/18/2021
ms.locfileid: "5477182"
---
# <a name="connector-for-azure-data-lake-storage-gen2-preview"></a><span data-ttu-id="1ff6b-103">Az Azure Data Lake Storage Gen2 összekötője (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="1ff6b-103">Connector for Azure Data Lake Storage Gen2 (preview)</span></span>

<span data-ttu-id="1ff6b-104">A Customer Insights-adatokat az Azure Data Lake Storage Gen2 tárolóban tárolhatja, vagy segítségével adatait más alkalmazásokba továbbíthatja.</span><span class="sxs-lookup"><span data-stu-id="1ff6b-104">Store your Customer Insights data in Azure Data Lake Storage Gen2 or use it to transfer your data to other applications.</span></span>

## <a name="configure-the-connector-for-azure-data-lake-storage-gen2"></a><span data-ttu-id="1ff6b-105">Az Azure Data Lake Storage Gen2 összekötőjének konfigurálása</span><span class="sxs-lookup"><span data-stu-id="1ff6b-105">Configure the connector for Azure Data Lake Storage Gen2</span></span>

1. <span data-ttu-id="1ff6b-106">A célközönség információin belül nyissa meg a következőt **Rendszergazda** > **Exportálási célhelyek**.</span><span class="sxs-lookup"><span data-stu-id="1ff6b-106">In audience insights, go to **Admin** > **Export destinations**.</span></span>

1. <span data-ttu-id="1ff6b-107">A **Azure Data Lake Storage Gen2** részben válassza a **Beállítás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="1ff6b-107">Under **Azure Data Lake Storage Gen2**, select **Set up**.</span></span>

1. <span data-ttu-id="1ff6b-108">Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben.</span><span class="sxs-lookup"><span data-stu-id="1ff6b-108">Give your destination a recognizable name in the **Display name** field.</span></span>

1. <span data-ttu-id="1ff6b-109">Adja meg a **Fiók neve**, a **Fiók kulcsa** és a **Tároló** adatait az Azure Data Lake Storage Gen2 tárolóhoz.</span><span class="sxs-lookup"><span data-stu-id="1ff6b-109">Enter **Account name**, **Account key**, and **Container** for your Azure Data Lake Storage Gen2.</span></span>
    - <span data-ttu-id="1ff6b-110">Ha meg szeretne ismerkedni vele, hogyan hozhat létre tárhelyfiókot az Azure Data Lake Storage Gen2 tárhellyel való használatra, olvassa el a [Tárhelyfiók létrehozása](https://docs.microsoft.com/azure/storage/blobs/create-data-lake-storage-account) részt.</span><span class="sxs-lookup"><span data-stu-id="1ff6b-110">To learn how to create a storage account to use with Azure Data Lake Storage Gen2, see [Create storage account](https://docs.microsoft.com/azure/storage/blobs/create-data-lake-storage-account).</span></span> 
    - <span data-ttu-id="1ff6b-111">Ha szeretne többet megtudni az Azure Data Lake Gen2 tárfiók nevének és fiókkulcsának megkereséséről, olvassa el a [Tárfiók beállításainak kezelése az Azure portálon](https://docs.microsoft.com/azure/storage/common/storage-account-manage) című részt.</span><span class="sxs-lookup"><span data-stu-id="1ff6b-111">To learn more about how to find the Azure Data Lake Gen2 storage account name and account key, see [Manage storage account settings in the Azure portal](https://docs.microsoft.com/azure/storage/common/storage-account-manage).</span></span>

1. <span data-ttu-id="1ff6b-112">Válassza a **Következő** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="1ff6b-112">Select **Next**.</span></span>

1. <span data-ttu-id="1ff6b-113">Jelölje be a jelölőnégyzetet azon entitások mellett, amelyeket exportálni szeretne erre a célhelyre.</span><span class="sxs-lookup"><span data-stu-id="1ff6b-113">Select the box next to each of the entities you want to export to this destination.</span></span>

1. <span data-ttu-id="1ff6b-114">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="1ff6b-114">Select **Save**.</span></span>

## <a name="export-the-data"></a><span data-ttu-id="1ff6b-115">Az adatok exportálása</span><span class="sxs-lookup"><span data-stu-id="1ff6b-115">Export the data</span></span>

<span data-ttu-id="1ff6b-116">[Igény szerint exportálhatja az adatot](export-destinations.md#export-data-on-demand).</span><span class="sxs-lookup"><span data-stu-id="1ff6b-116">You can [export data on demand](export-destinations.md#export-data-on-demand).</span></span> <span data-ttu-id="1ff6b-117">Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) együtt is lefut.</span><span class="sxs-lookup"><span data-stu-id="1ff6b-117">The export will also run with every [scheduled refresh](system.md#schedule-tab).</span></span>
