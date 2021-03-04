---
title: A Customer Insights adatok a Dynamics 365 Salesbe való exportálása
description: Megismerheti, hogyan konfigurálható a kapcsolat a Dynamics 365 Sales megoldással.
ms.date: 02/01/2021
ms.reviewer: philk
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: 0013c4e6a96401d6cdbea55ed38f85f5e10dcc56
ms.sourcegitcommit: 139548f8a2d0f24d54c4a6c404a743eeeb8ef8e0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/15/2021
ms.locfileid: "5269011"
---
# <a name="connector-for-dynamics-365-sales-preview"></a><span data-ttu-id="49497-103">Dynamics 365 Sales összekötője (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="49497-103">Connector for Dynamics 365 Sales (preview)</span></span>

[!INCLUDE [cc-data-platform-banner](../includes/cc-data-platform-banner.md)]

<span data-ttu-id="49497-104">A Dynamics 365 Sales modullal az ügyféladatokból marketinglistákat hozhat létre, nyomon követheti a munkafolyamatokat, és promóciós anyagokat küldhet ki.</span><span class="sxs-lookup"><span data-stu-id="49497-104">Use your customer data to create marketing lists, follow up workflows, and send out promotions with Dynamics 365 Sales.</span></span>

## <a name="prerequisite"></a><span data-ttu-id="49497-105">Előfeltétel</span><span class="sxs-lookup"><span data-stu-id="49497-105">Prerequisite</span></span>

1. <span data-ttu-id="49497-106">A kapcsolattartók bejegyzésének jelen kell lennie a Dynamics 365 Sales alkalmazásban, mielőtt egy szegmenst exportálhatna a Customer Insights alkalmazásból a Sales alkalmazásba.</span><span class="sxs-lookup"><span data-stu-id="49497-106">Contact records must be present in Dynamics 365 Sales before you can export a segment from Customer Insights to Sales.</span></span> <span data-ttu-id="49497-107">További információ a kapcsolattartók betöltéséről [a Dynamics 365 Sales alkalmazásba a Common Data Services használatával](connect-power-query.md).</span><span class="sxs-lookup"><span data-stu-id="49497-107">Read more on how to ingest contacts in [Dynamics 365 Sales using Common Data Services](connect-power-query.md).</span></span>

   > [!NOTE]
   > <span data-ttu-id="49497-108">Ha szegmenseket exportál a célközönséggel kapcsolatos információkból a Sales nem hoz létre új kapcsolattartói rekordokat a Sales példányban.</span><span class="sxs-lookup"><span data-stu-id="49497-108">Exporting segments from audience insights to Sales will not create new contact records in the Sales instances.</span></span> <span data-ttu-id="49497-109">A Sales kapcsolattartói bejegyzéseket be kell tölteni a célközönség kapcsolatos információkba és adatforrásként használni.</span><span class="sxs-lookup"><span data-stu-id="49497-109">The contact records from Sales must be ingested in audience insights and used as a data source.</span></span> <span data-ttu-id="49497-110">Emellett szerepelniük kell az egyesített Ügyfél entitásban ahhoz, hogy a szegmensek exportálása előtt le tudják képezni az ügyfélazonosítókat.</span><span class="sxs-lookup"><span data-stu-id="49497-110">They also need to be included in the unified Customer entity to map customer IDs to contact IDs before segments can be exported.</span></span>

## <a name="configure-the-connector-for-sales"></a><span data-ttu-id="49497-111">A Sales összekötő beállítása</span><span class="sxs-lookup"><span data-stu-id="49497-111">Configure the connector for Sales</span></span>

1. <span data-ttu-id="49497-112">A célközönség információin belül nyissa meg a következőt **Rendszergazda** > **Exportálási célhelyek**.</span><span class="sxs-lookup"><span data-stu-id="49497-112">In audience insights, go to **Admin** > **Export destinations**.</span></span>

1. <span data-ttu-id="49497-113">A **Dynamics 365 Sales** alatt válassza a **Beállítás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="49497-113">Under **Dynamics 365 Sales**, select **Set up**.</span></span>

1. <span data-ttu-id="49497-114">Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben az export helyének.</span><span class="sxs-lookup"><span data-stu-id="49497-114">Give your export destination a recognizable name in the **Display name** field.</span></span>

1. <span data-ttu-id="49497-115">Adja meg a szervezet értékesítési URL-címét a **Kiszolgáló címe** mezőben.</span><span class="sxs-lookup"><span data-stu-id="49497-115">Enter your organization's Sales URL in the **Server address** field.</span></span>

1. <span data-ttu-id="49497-116">A **Kiszolgáló rendszergazdai fiókja** területen válassza a **Bejelentkezés** lehetőséget, és válasszon egy Dynamics 365 Sales fiókot.</span><span class="sxs-lookup"><span data-stu-id="49497-116">In the **Server admin account** section, select **Sign in** and choose a Dynamics 365 Sales account.</span></span>

1. <span data-ttu-id="49497-117">Az ügyfélazonosító mező leképezése a Dynamics 365 kapcsolattartói azonosítóhoz.</span><span class="sxs-lookup"><span data-stu-id="49497-117">Map a customer ID field to the Dynamics 365 Contact ID.</span></span>

1. <span data-ttu-id="49497-118">Válassza a **Következő** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="49497-118">Select **Next**.</span></span>

1. <span data-ttu-id="49497-119">Jelöljön ki egy vagy több szegmenst.</span><span class="sxs-lookup"><span data-stu-id="49497-119">Choose one or more segments.</span></span>

1. <span data-ttu-id="49497-120">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="49497-120">Select **Save**.</span></span>

## <a name="export-the-data"></a><span data-ttu-id="49497-121">Az adatok exportálása</span><span class="sxs-lookup"><span data-stu-id="49497-121">Export the data</span></span>

<span data-ttu-id="49497-122">[Igény szerint exportálhatja az adatot](export-destinations.md).</span><span class="sxs-lookup"><span data-stu-id="49497-122">You can [export data on demand](export-destinations.md).</span></span> <span data-ttu-id="49497-123">Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) együtt is lefut.</span><span class="sxs-lookup"><span data-stu-id="49497-123">The export will also run with every [scheduled refresh](system.md#schedule-tab).</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]