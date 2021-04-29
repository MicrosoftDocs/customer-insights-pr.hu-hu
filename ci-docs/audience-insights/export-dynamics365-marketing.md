---
title: A Customer Insights adatok a Dynamics 365 Marketingbe való exportálása
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a Dynamics 365 Marketingbe.
ms.date: 03/03/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: phkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: a13f6f81f5e2570d3302d88c02755f1d86321a01
ms.sourcegitcommit: 1b671c6100991fea1cace04b5d4fcedcd88aa94f
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/31/2021
ms.locfileid: "5759640"
---
# <a name="use-segments-in-dynamics-365-marketing-preview"></a><span data-ttu-id="19824-103">Szegmensek használata a Dynamics 365 Marketing alkalmazásban (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="19824-103">Use segments in Dynamics 365 Marketing (preview)</span></span>

[!INCLUDE [cc-data-platform-banner](../includes/cc-data-platform-banner.md)]

<span data-ttu-id="19824-104">A [szegmensek](segments.md) segítségével kampányok és az ügyfelek adott csoportjaihoz fordulhat a Dynamics 365 Marketing alkalmazással.</span><span class="sxs-lookup"><span data-stu-id="19824-104">Use [segments](segments.md) to generate campaigns and contact specific groups of customers with Dynamics 365 Marketing.</span></span> <span data-ttu-id="19824-105">További tudnivalók: [szegmensek használata a Dynamics 365 Customer Insights szolgáltatásból a Dynamics 365 Marketing alkalmazással](/dynamics365/marketing/customer-insights-segments)</span><span class="sxs-lookup"><span data-stu-id="19824-105">For more information, see [Use segments from Dynamics 365 Customer Insights with Dynamics 365 Marketing](/dynamics365/marketing/customer-insights-segments)</span></span>

## <a name="prerequisite-for-a-connection"></a><span data-ttu-id="19824-106">Egy kapcsolat előfeltétele</span><span class="sxs-lookup"><span data-stu-id="19824-106">Prerequisite for a connection</span></span>

- <span data-ttu-id="19824-107">A kapcsolattartók bejegyzésének jelen kell lennie a Dynamics 365 Marketing alkalmazásban, mielőtt egy szegmenst exportálhatna a Customer Insights alkalmazásból a Marketing alkalmazásba.</span><span class="sxs-lookup"><span data-stu-id="19824-107">Contact records must be present in Dynamics 365 Marketing before you can export a segment from Customer Insights to Marketing.</span></span> <span data-ttu-id="19824-108">További információ a kapcsolattartók betöltéséről [a Dynamics 365 Marketing alkalmazásba a Common Data Services használatával](connect-power-query.md).</span><span class="sxs-lookup"><span data-stu-id="19824-108">Read more on how to ingest contacts in [Dynamics 365 Marketing using Common Data Services](connect-power-query.md).</span></span>

  > [!NOTE]
  > <span data-ttu-id="19824-109">Ha szegmenseket exportál a célközönséggel kapcsolatos információkból a Marketing nem hoz létre új kapcsolattartói rekordokat a Marketing példányban.</span><span class="sxs-lookup"><span data-stu-id="19824-109">Exporting segments from audience insights to Marketing will not create new contact records in the Marketing instances.</span></span> <span data-ttu-id="19824-110">A Marketing kapcsolattartói bejegyzéseket be kell tölteni a célközönség kapcsolatos információkba és adatforrásként használni.</span><span class="sxs-lookup"><span data-stu-id="19824-110">The contact records from Marketing must be ingested in audience insights and used as a data source.</span></span> <span data-ttu-id="19824-111">Emellett szerepelniük kell az egyesített Ügyfél entitásban ahhoz, hogy a szegmensek exportálása előtt le tudják képezni az ügyfélazonosítókat.</span><span class="sxs-lookup"><span data-stu-id="19824-111">They also need to be included in the unified Customer entity to map customer IDs to contact IDs before segments can be exported.</span></span>

## <a name="set-up-connection-to-marketing"></a><span data-ttu-id="19824-112">Állítsa be a Marketinggel való kapcsolatot</span><span class="sxs-lookup"><span data-stu-id="19824-112">Set up connection to Marketing</span></span>

1. <span data-ttu-id="19824-113">Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="19824-113">Go to **Admin** > **Connections**.</span></span>

1. <span data-ttu-id="19824-114">Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza a **Dynamics 365 Marketing** lehetőséget a kapcsolat konfigurálásához.</span><span class="sxs-lookup"><span data-stu-id="19824-114">Select **Add connection** and choose **Dynamics 365 Marketing** to configure the connection.</span></span>

1. <span data-ttu-id="19824-115">Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak.</span><span class="sxs-lookup"><span data-stu-id="19824-115">Give your connection a recognizable name in the **Display name** field.</span></span> <span data-ttu-id="19824-116">A név és a kapcsolat típusa írja le ezt a kapcsolatot.</span><span class="sxs-lookup"><span data-stu-id="19824-116">The name and the type of the connection describe this connection.</span></span> <span data-ttu-id="19824-117">Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.</span><span class="sxs-lookup"><span data-stu-id="19824-117">We recommend choosing a name that explains the purpose and target of the connection.</span></span>

1. <span data-ttu-id="19824-118">A kapcsolat használóinak kiválasztása.</span><span class="sxs-lookup"><span data-stu-id="19824-118">Choose who can use this connection.</span></span> <span data-ttu-id="19824-119">Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz.</span><span class="sxs-lookup"><span data-stu-id="19824-119">If you take no action, the default will be Administrators.</span></span> <span data-ttu-id="19824-120">További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).</span><span class="sxs-lookup"><span data-stu-id="19824-120">For more information, see [Allow contributors to use a connection for exports](connections.md#allow-contributors-to-use-a-connection-for-exports).</span></span>

1. <span data-ttu-id="19824-121">Adja meg a szervezet Marketing URL-címét a **Kiszolgáló címe** mezőben.</span><span class="sxs-lookup"><span data-stu-id="19824-121">Enter your organization's Marketing URL in the **Server address** field.</span></span>

1. <span data-ttu-id="19824-122">A **Kiszolgáló rendszergazdai fiókja** területen válassza a **Bejelentkezés** lehetőséget, és válasszon egy Dynamics 365 Marketing fiókot.</span><span class="sxs-lookup"><span data-stu-id="19824-122">In the **Server admin account** section, select **Sign in** and choose a Dynamics 365 Marketing account.</span></span>

1. <span data-ttu-id="19824-123">Az ügyfélazonosító mező leképezése a Dynamics 365 kapcsolattartói azonosítóhoz.</span><span class="sxs-lookup"><span data-stu-id="19824-123">Map a customer ID field to the Dynamics 365 Contact ID.</span></span>

1. <span data-ttu-id="19824-124">A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="19824-124">Select **Save** to complete the connection.</span></span> 

## <a name="configure-an-export"></a><span data-ttu-id="19824-125">Exportálás konfigurálása</span><span class="sxs-lookup"><span data-stu-id="19824-125">Configure an export</span></span>

<span data-ttu-id="19824-126">Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz.</span><span class="sxs-lookup"><span data-stu-id="19824-126">You can configure this export if you have access to a connection of this type.</span></span> <span data-ttu-id="19824-127">További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).</span><span class="sxs-lookup"><span data-stu-id="19824-127">For more information, see [Permissions needed to configure an export](export-destinations.md#set-up-a-new-export).</span></span>

1. <span data-ttu-id="19824-128">Menjen az **Adatok** > **Exportálások** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="19824-128">Go to **Data** > **Exports**.</span></span>

1. <span data-ttu-id="19824-129">Új exportálás létrehozásához válassza a **Célhely hozzáadása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="19824-129">To create a new export, select **Add destination**.</span></span>

1. <span data-ttu-id="19824-130">A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot a Dynamics 365 Marketing szakaszból.</span><span class="sxs-lookup"><span data-stu-id="19824-130">In the **Connection for export** field, choose a connection from the Dynamics 365 Marketing section.</span></span> <span data-ttu-id="19824-131">Ha nem látja ezt a szakasznevet, az Ön számára nincs ilyen típusú kapcsolat.</span><span class="sxs-lookup"><span data-stu-id="19824-131">If you don't see this section name, there are no connections of this type available to you.</span></span>

1. <span data-ttu-id="19824-132">Jelöljön ki egy vagy több szegmenst.</span><span class="sxs-lookup"><span data-stu-id="19824-132">Choose one or more segments.</span></span>

1. <span data-ttu-id="19824-133">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="19824-133">Select **Save**.</span></span>

<span data-ttu-id="19824-134">Az exportálás mentése nem futtatja azonnal az exportálást.</span><span class="sxs-lookup"><span data-stu-id="19824-134">Saving an export doesn't run the export immediately.</span></span>

<span data-ttu-id="19824-135">Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut.</span><span class="sxs-lookup"><span data-stu-id="19824-135">The export runs with every [scheduled refresh](system.md#schedule-tab).</span></span> <span data-ttu-id="19824-136">Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand).</span><span class="sxs-lookup"><span data-stu-id="19824-136">You can also [export data on demand](export-destinations.md#run-exports-on-demand).</span></span> 

[!INCLUDE[footer-include](../includes/footer-banner.md)]
