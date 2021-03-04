---
title: A Customer Insights adatok a Dynamics 365 Marketingbe való exportálása
description: Megismerheti, hogyan konfigurálható a kapcsolat a Dynamics 365 Marketing megoldással.
ms.date: 02/01/2021
ms.reviewer: philk
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: a06920b8ff25d7102ccd14ae68cf42fe91fa1ee6
ms.sourcegitcommit: 139548f8a2d0f24d54c4a6c404a743eeeb8ef8e0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/15/2021
ms.locfileid: "5269057"
---
# <a name="connector-for-dynamics-365-marketing-preview"></a><span data-ttu-id="b8019-103">Dynamics 365 Marketing összekötője (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="b8019-103">Connector for Dynamics 365 Marketing (preview)</span></span>

[!INCLUDE [cc-data-platform-banner](../includes/cc-data-platform-banner.md)]

<span data-ttu-id="b8019-104">A [szegmensek](segments.md) segítségével kampányok és az ügyfelek adott csoportjaihoz fordulhat a Dynamics 365 Marketing alkalmazással.</span><span class="sxs-lookup"><span data-stu-id="b8019-104">Use [segments](segments.md) to generate campaigns and contact specific groups of customers with Dynamics 365 Marketing.</span></span> <span data-ttu-id="b8019-105">További tudnivalók: [szegmensek használata a Dynamics 365 Customer Insights szolgáltatásból a Dynamics 365 Marketing alkalmazással](https://docs.microsoft.com/dynamics365/marketing/customer-insights-segments)</span><span class="sxs-lookup"><span data-stu-id="b8019-105">For more information, see [Use segments from Dynamics 365 Customer Insights with Dynamics 365 Marketing](https://docs.microsoft.com/dynamics365/marketing/customer-insights-segments)</span></span>

## <a name="prerequisite"></a><span data-ttu-id="b8019-106">Előfeltétel</span><span class="sxs-lookup"><span data-stu-id="b8019-106">Prerequisite</span></span>

- <span data-ttu-id="b8019-107">A kapcsolattartók bejegyzésének jelen kell lennie a Dynamics 365 Marketing alkalmazásban, mielőtt egy szegmenst exportálhatna a Customer Insights alkalmazásból a Marketing alkalmazásba.</span><span class="sxs-lookup"><span data-stu-id="b8019-107">Contact records must be present in Dynamics 365 Marketing before you can export a segment from Customer Insights to Marketing.</span></span> <span data-ttu-id="b8019-108">További információ a kapcsolattartók betöltéséről [a Dynamics 365 Marketing alkalmazásba a Common Data Services használatával](connect-power-query.md).</span><span class="sxs-lookup"><span data-stu-id="b8019-108">Read more on how to ingest contacts in [Dynamics 365 Marketing using Common Data Services](connect-power-query.md).</span></span>

  > [!NOTE]
  > <span data-ttu-id="b8019-109">Ha szegmenseket exportál a célközönséggel kapcsolatos információkból a Marketing nem hoz létre új kapcsolattartói rekordokat a Marketing példányban.</span><span class="sxs-lookup"><span data-stu-id="b8019-109">Exporting segments from audience insights to Marketing will not create new contact records in the Marketing instances.</span></span> <span data-ttu-id="b8019-110">A Marketing kapcsolattartói bejegyzéseket be kell tölteni a célközönség kapcsolatos információkba és adatforrásként használni.</span><span class="sxs-lookup"><span data-stu-id="b8019-110">The contact records from Marketing must be ingested in audience insights and used as a data source.</span></span> <span data-ttu-id="b8019-111">Emellett szerepelniük kell az egyesített Ügyfél entitásban ahhoz, hogy a szegmensek exportálása előtt le tudják képezni az ügyfélazonosítókat.</span><span class="sxs-lookup"><span data-stu-id="b8019-111">They also need to be included in the unified Customer entity to map customer IDs to contact IDs before segments can be exported.</span></span>

## <a name="configure-the-connector-for-marketing"></a><span data-ttu-id="b8019-112">A Marketing összekötő beállítása</span><span class="sxs-lookup"><span data-stu-id="b8019-112">Configure the connector for Marketing</span></span>

1. <span data-ttu-id="b8019-113">A célközönség információin belül nyissa meg a következőt **Rendszergazda** > **Exportálási célhelyek**.</span><span class="sxs-lookup"><span data-stu-id="b8019-113">In audience insights, go to **Admin** > **Export destinations**.</span></span>

1. <span data-ttu-id="b8019-114">A **Dynamics 365 Marketing** alatt válassza a **Beállítás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="b8019-114">Under **Dynamics 365 Marketing**, select **Set up**.</span></span>

1. <span data-ttu-id="b8019-115">Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben az export helyének.</span><span class="sxs-lookup"><span data-stu-id="b8019-115">Give your export destination a recognizable name in the **Display name** field.</span></span>

1. <span data-ttu-id="b8019-116">Adja meg a szervezet Marketing URL-címét a **Kiszolgáló címe** mezőben.</span><span class="sxs-lookup"><span data-stu-id="b8019-116">Enter your organization's Marketing URL in the **Server address** field.</span></span>

1. <span data-ttu-id="b8019-117">A **Kiszolgáló rendszergazdai fiókja** területen válassza a **Bejelentkezés** lehetőséget, és válasszon egy Dynamics 365 Marketing fiókot.</span><span class="sxs-lookup"><span data-stu-id="b8019-117">In the **Server admin account** section, select **Sign in** and choose a Dynamics 365 Marketing account.</span></span>

1. <span data-ttu-id="b8019-118">Az ügyfélazonosító mező leképezése a Dynamics 365 kapcsolattartói azonosítóhoz.</span><span class="sxs-lookup"><span data-stu-id="b8019-118">Map a customer ID field to the Dynamics 365 Contact ID.</span></span>

1. <span data-ttu-id="b8019-119">Válassza a **Következő** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="b8019-119">Select **Next**.</span></span>

1. <span data-ttu-id="b8019-120">Jelöljön ki egy vagy több szegmenst.</span><span class="sxs-lookup"><span data-stu-id="b8019-120">Choose one or more segments.</span></span>

1. <span data-ttu-id="b8019-121">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="b8019-121">Select **Save**.</span></span>

## <a name="export-the-data"></a><span data-ttu-id="b8019-122">Az adatok exportálása</span><span class="sxs-lookup"><span data-stu-id="b8019-122">Export the data</span></span>

<span data-ttu-id="b8019-123">[Igény szerint exportálhatja az adatot](export-destinations.md).</span><span class="sxs-lookup"><span data-stu-id="b8019-123">You can [export data on demand](export-destinations.md).</span></span> <span data-ttu-id="b8019-124">Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) együtt is lefut.</span><span class="sxs-lookup"><span data-stu-id="b8019-124">The export will also run with every [scheduled refresh](system.md#schedule-tab).</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]