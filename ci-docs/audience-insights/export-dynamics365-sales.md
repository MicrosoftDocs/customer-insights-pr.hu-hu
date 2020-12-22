---
title: A Customer Insights adatok a Dynamics 365 Salesbe való exportálása
description: Megismerheti, hogyan konfigurálható a kapcsolat a Dynamics 365 Sales megoldással.
ms.date: 08/21/2020
ms.reviewer: philk
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: af0824e69dfdf620a0ac756e32a9bd3dd85e5151
ms.sourcegitcommit: 6a6df62fa12dcb9bd5f5a39cc3ee0e2b3988184b
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/25/2020
ms.locfileid: "4643821"
---
# <a name="connector-for-dynamics-365-sales-preview"></a><span data-ttu-id="4bd8f-103">Dynamics 365 Sales összekötője (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="4bd8f-103">Connector for Dynamics 365 Sales (preview)</span></span>

[!INCLUDE [cc-data-platform-banner](../includes/cc-data-platform-banner.md)]

<span data-ttu-id="4bd8f-104">A Dynamics 365 Sales modullal az ügyféladatokból marketinglistákat hozhat létre, nyomon követheti a munkafolyamatokat, és promóciós anyagokat küldhet ki.</span><span class="sxs-lookup"><span data-stu-id="4bd8f-104">Use your customer data to create marketing lists, follow up workflows, and send out promotions with Dynamics 365 Sales.</span></span>

## <a name="prerequisite"></a><span data-ttu-id="4bd8f-105">Előfeltétel</span><span class="sxs-lookup"><span data-stu-id="4bd8f-105">Prerequisite</span></span>

<span data-ttu-id="4bd8f-106">[A betöltött Dynamics 365 Salest használó Common Data Service](connect-power-query.md) kapcsolattartói rekordjai.</span><span class="sxs-lookup"><span data-stu-id="4bd8f-106">Contact records [from Dynamics 365 Sales ingested using Common Data Service](connect-power-query.md).</span></span>

## <a name="configure-the-connector-for-sales"></a><span data-ttu-id="4bd8f-107">A Sales összekötő beállítása</span><span class="sxs-lookup"><span data-stu-id="4bd8f-107">Configure the connector for Sales</span></span>

1. <span data-ttu-id="4bd8f-108">A célközönség információin belül nyissa meg a következőt **Rendszergazda** > **Exportálási célhelyek**.</span><span class="sxs-lookup"><span data-stu-id="4bd8f-108">In audience insights, go to **Admin** > **Export destinations**.</span></span>

1. <span data-ttu-id="4bd8f-109">A **Dynamics 365 Sales** alatt válassza a **Beállítás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="4bd8f-109">Under **Dynamics 365 Sales**, select **Set up**.</span></span>

1. <span data-ttu-id="4bd8f-110">Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben az export helyének.</span><span class="sxs-lookup"><span data-stu-id="4bd8f-110">Give your export destination a recognizable name in the **Display name** field.</span></span>

1. <span data-ttu-id="4bd8f-111">Adja meg a szervezet értékesítési URL-címét a **Kiszolgáló címe** mezőben.</span><span class="sxs-lookup"><span data-stu-id="4bd8f-111">Enter your organization's Sales URL in the **Server address** field.</span></span>

1. <span data-ttu-id="4bd8f-112">A **Kiszolgáló rendszergazdai fiókja** területen válassza a **Bejelentkezés** lehetőséget, és válasszon egy Dynamics 365 Sales fiókot.</span><span class="sxs-lookup"><span data-stu-id="4bd8f-112">In the **Server admin account** section, select **Sign in** and choose a Dynamics 365 Sales account.</span></span>

1. <span data-ttu-id="4bd8f-113">Az ügyfélazonosító mező leképezése a Dynamics 365 kapcsolattartói azonosítóhoz.</span><span class="sxs-lookup"><span data-stu-id="4bd8f-113">Map a customer ID field to the Dynamics 365 Contact ID.</span></span>

1. <span data-ttu-id="4bd8f-114">Válassza a **Következő** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="4bd8f-114">Select **Next**.</span></span>

1. <span data-ttu-id="4bd8f-115">Jelöljön ki egy vagy több szegmenst.</span><span class="sxs-lookup"><span data-stu-id="4bd8f-115">Choose one or more segments.</span></span>

1. <span data-ttu-id="4bd8f-116">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="4bd8f-116">Select **Save**.</span></span>

## <a name="export-the-data"></a><span data-ttu-id="4bd8f-117">Az adatok exportálása</span><span class="sxs-lookup"><span data-stu-id="4bd8f-117">Export the data</span></span>

<span data-ttu-id="4bd8f-118">[Igény szerint exportálhatja az adatot](export-destinations.md).</span><span class="sxs-lookup"><span data-stu-id="4bd8f-118">You can [export data on demand](export-destinations.md).</span></span> <span data-ttu-id="4bd8f-119">Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) együtt is lefut.</span><span class="sxs-lookup"><span data-stu-id="4bd8f-119">The export will also run with every [scheduled refresh](system.md#schedule-tab).</span></span>
