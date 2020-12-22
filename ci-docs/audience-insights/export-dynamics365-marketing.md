---
title: A Customer Insights adatok a Dynamics 365 Marketingbe való exportálása
description: Megismerheti, hogyan konfigurálható a kapcsolat a Dynamics 365 Marketing megoldással.
ms.date: 08/21/2020
ms.reviewer: philk
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: 163387779b64bd78ef08e2d96a5f1c9615062f28
ms.sourcegitcommit: 6a6df62fa12dcb9bd5f5a39cc3ee0e2b3988184b
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/25/2020
ms.locfileid: "4643776"
---
# <a name="connector-for-dynamics-365-marketing-preview"></a><span data-ttu-id="5fce9-103">Dynamics 365 Marketing összekötője (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="5fce9-103">Connector for Dynamics 365 Marketing (preview)</span></span>

[!INCLUDE [cc-data-platform-banner](../includes/cc-data-platform-banner.md)]

<span data-ttu-id="5fce9-104">A [szegmensek](segments.md) segítségével kampányok és az ügyfelek adott csoportjaihoz fordulhat a Dynamics 365 Marketing alkalmazással.</span><span class="sxs-lookup"><span data-stu-id="5fce9-104">Use [segments](segments.md) to generate campaigns and contact specific groups of customers with Dynamics 365 Marketing.</span></span> <span data-ttu-id="5fce9-105">További tudnivalók: [szegmensek használata a Dynamics 365 Customer Insights szolgáltatásból a Dynamics 365 Marketing alkalmazással](https://docs.microsoft.com/dynamics365/marketing/customer-insights-segments)</span><span class="sxs-lookup"><span data-stu-id="5fce9-105">For more information, see [Use segments from Dynamics 365 Customer Insights with Dynamics 365 Marketing](https://docs.microsoft.com/dynamics365/marketing/customer-insights-segments)</span></span>

## <a name="prerequisite"></a><span data-ttu-id="5fce9-106">Előfeltétel</span><span class="sxs-lookup"><span data-stu-id="5fce9-106">Prerequisite</span></span>

<span data-ttu-id="5fce9-107">[A Dynamics 365 Marketing betöltött Common Data Service](connect-power-query.md) szolgáltatásból származó kapcsolattartói rekordjai.</span><span class="sxs-lookup"><span data-stu-id="5fce9-107">Contact records [from Dynamics 365 Marketing ingested Common Data Service](connect-power-query.md).</span></span>

## <a name="configure-the-connector-for-marketing"></a><span data-ttu-id="5fce9-108">A Marketing összekötő beállítása</span><span class="sxs-lookup"><span data-stu-id="5fce9-108">Configure the connector for Marketing</span></span>

1. <span data-ttu-id="5fce9-109">A célközönség információin belül nyissa meg a következőt **Rendszergazda** > **Exportálási célhelyek**.</span><span class="sxs-lookup"><span data-stu-id="5fce9-109">In audience insights, go to **Admin** > **Export destinations**.</span></span>

1. <span data-ttu-id="5fce9-110">A **Dynamics 365 Marketing** alatt válassza a **Beállítás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="5fce9-110">Under **Dynamics 365 Marketing**, select **Set up**.</span></span>

1. <span data-ttu-id="5fce9-111">Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben az export helyének.</span><span class="sxs-lookup"><span data-stu-id="5fce9-111">Give your export destination a recognizable name in the **Display name** field.</span></span>

1. <span data-ttu-id="5fce9-112">Adja meg a szervezet Marketing URL-címét a **Kiszolgáló címe** mezőben.</span><span class="sxs-lookup"><span data-stu-id="5fce9-112">Enter your organization's Marketing URL in the **Server address** field.</span></span>

1. <span data-ttu-id="5fce9-113">A **Kiszolgáló rendszergazdai fiókja** területen válassza a **Bejelentkezés** lehetőséget, és válasszon egy Dynamics 365 Marketing fiókot.</span><span class="sxs-lookup"><span data-stu-id="5fce9-113">In the **Server admin account** section, select **Sign in** and choose a Dynamics 365 Marketing account.</span></span>

1. <span data-ttu-id="5fce9-114">Az ügyfélazonosító mező leképezése a Dynamics 365 kapcsolattartói azonosítóhoz.</span><span class="sxs-lookup"><span data-stu-id="5fce9-114">Map a customer ID field to the Dynamics 365 Contact ID.</span></span>

1. <span data-ttu-id="5fce9-115">Válassza a **Következő** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="5fce9-115">Select **Next**.</span></span>

1. <span data-ttu-id="5fce9-116">Jelöljön ki egy vagy több szegmenst.</span><span class="sxs-lookup"><span data-stu-id="5fce9-116">Choose one or more segments.</span></span>

1. <span data-ttu-id="5fce9-117">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="5fce9-117">Select **Save**.</span></span>

## <a name="export-the-data"></a><span data-ttu-id="5fce9-118">Az adatok exportálása</span><span class="sxs-lookup"><span data-stu-id="5fce9-118">Export the data</span></span>

<span data-ttu-id="5fce9-119">[Igény szerint exportálhatja az adatot](export-destinations.md).</span><span class="sxs-lookup"><span data-stu-id="5fce9-119">You can [export data on demand](export-destinations.md).</span></span> <span data-ttu-id="5fce9-120">Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) együtt is lefut.</span><span class="sxs-lookup"><span data-stu-id="5fce9-120">The export will also run with every [scheduled refresh](system.md#schedule-tab).</span></span>
