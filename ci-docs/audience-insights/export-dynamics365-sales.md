---
title: A Customer Insights adatok a Dynamics 365 Salesbe való exportálása
description: Megismerheti, hogyan konfigurálható a kapcsolat a Dynamics 365 Sales megoldással.
ms.date: 02/01/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: phkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 39ecdf528c6be4d8fb420a52a6ed998317e43bcd
ms.sourcegitcommit: bae40184312ab27b95c140a044875c2daea37951
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/15/2021
ms.locfileid: "5598112"
---
# <a name="connector-for-dynamics-365-sales-preview"></a><span data-ttu-id="45f9c-103">Dynamics 365 Sales összekötője (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="45f9c-103">Connector for Dynamics 365 Sales (preview)</span></span>

[!INCLUDE [cc-data-platform-banner](../includes/cc-data-platform-banner.md)]

<span data-ttu-id="45f9c-104">A Dynamics 365 Sales modullal az ügyféladatokból marketinglistákat hozhat létre, nyomon követheti a munkafolyamatokat, és promóciós anyagokat küldhet ki.</span><span class="sxs-lookup"><span data-stu-id="45f9c-104">Use your customer data to create marketing lists, follow up workflows, and send out promotions with Dynamics 365 Sales.</span></span>

## <a name="prerequisite"></a><span data-ttu-id="45f9c-105">Előfeltétel</span><span class="sxs-lookup"><span data-stu-id="45f9c-105">Prerequisite</span></span>

1. <span data-ttu-id="45f9c-106">A kapcsolattartók bejegyzésének jelen kell lennie a Dynamics 365 Sales alkalmazásban, mielőtt egy szegmenst exportálhatna a Customer Insights alkalmazásból a Sales alkalmazásba.</span><span class="sxs-lookup"><span data-stu-id="45f9c-106">Contact records must be present in Dynamics 365 Sales before you can export a segment from Customer Insights to Sales.</span></span> <span data-ttu-id="45f9c-107">További információ a kapcsolattartók betöltéséről [a Dynamics 365 Sales alkalmazásba a Common Data Services használatával](connect-power-query.md).</span><span class="sxs-lookup"><span data-stu-id="45f9c-107">Read more on how to ingest contacts in [Dynamics 365 Sales using Common Data Services](connect-power-query.md).</span></span>

   > [!NOTE]
   > <span data-ttu-id="45f9c-108">Ha szegmenseket exportál a célközönséggel kapcsolatos információkból a Sales nem hoz létre új kapcsolattartói rekordokat a Sales példányban.</span><span class="sxs-lookup"><span data-stu-id="45f9c-108">Exporting segments from audience insights to Sales will not create new contact records in the Sales instances.</span></span> <span data-ttu-id="45f9c-109">A Sales kapcsolattartói bejegyzéseket be kell tölteni a célközönség kapcsolatos információkba és adatforrásként használni.</span><span class="sxs-lookup"><span data-stu-id="45f9c-109">The contact records from Sales must be ingested in audience insights and used as a data source.</span></span> <span data-ttu-id="45f9c-110">Emellett szerepelniük kell az egyesített Ügyfél entitásban ahhoz, hogy a szegmensek exportálása előtt le tudják képezni az ügyfélazonosítókat.</span><span class="sxs-lookup"><span data-stu-id="45f9c-110">They also need to be included in the unified Customer entity to map customer IDs to contact IDs before segments can be exported.</span></span>

## <a name="configure-the-connector-for-sales"></a><span data-ttu-id="45f9c-111">A Sales összekötő beállítása</span><span class="sxs-lookup"><span data-stu-id="45f9c-111">Configure the connector for Sales</span></span>

1. <span data-ttu-id="45f9c-112">A célközönség információin belül nyissa meg a következőt **Rendszergazda** > **Exportálási célhelyek**.</span><span class="sxs-lookup"><span data-stu-id="45f9c-112">In audience insights, go to **Admin** > **Export destinations**.</span></span>

1. <span data-ttu-id="45f9c-113">A **Dynamics 365 Sales** alatt válassza a **Beállítás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="45f9c-113">Under **Dynamics 365 Sales**, select **Set up**.</span></span>

1. <span data-ttu-id="45f9c-114">Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben az export helyének.</span><span class="sxs-lookup"><span data-stu-id="45f9c-114">Give your export destination a recognizable name in the **Display name** field.</span></span>

1. <span data-ttu-id="45f9c-115">Adja meg a szervezet értékesítési URL-címét a **Kiszolgáló címe** mezőben.</span><span class="sxs-lookup"><span data-stu-id="45f9c-115">Enter your organization's Sales URL in the **Server address** field.</span></span>

1. <span data-ttu-id="45f9c-116">A **Kiszolgáló rendszergazdai fiókja** területen válassza a **Bejelentkezés** lehetőséget, és válasszon egy Dynamics 365 Sales fiókot.</span><span class="sxs-lookup"><span data-stu-id="45f9c-116">In the **Server admin account** section, select **Sign in** and choose a Dynamics 365 Sales account.</span></span>

1. <span data-ttu-id="45f9c-117">Az ügyfélazonosító mező leképezése a Dynamics 365 kapcsolattartói azonosítóhoz.</span><span class="sxs-lookup"><span data-stu-id="45f9c-117">Map a customer ID field to the Dynamics 365 Contact ID.</span></span>

1. <span data-ttu-id="45f9c-118">Válassza a **Következő** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="45f9c-118">Select **Next**.</span></span>

1. <span data-ttu-id="45f9c-119">Jelöljön ki egy vagy több szegmenst.</span><span class="sxs-lookup"><span data-stu-id="45f9c-119">Choose one or more segments.</span></span>

1. <span data-ttu-id="45f9c-120">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="45f9c-120">Select **Save**.</span></span>

## <a name="export-the-data"></a><span data-ttu-id="45f9c-121">Az adatok exportálása</span><span class="sxs-lookup"><span data-stu-id="45f9c-121">Export the data</span></span>

<span data-ttu-id="45f9c-122">[Igény szerint exportálhatja az adatot](export-destinations.md).</span><span class="sxs-lookup"><span data-stu-id="45f9c-122">You can [export data on demand](export-destinations.md).</span></span> <span data-ttu-id="45f9c-123">Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) együtt is lefut.</span><span class="sxs-lookup"><span data-stu-id="45f9c-123">The export will also run with every [scheduled refresh](system.md#schedule-tab).</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]