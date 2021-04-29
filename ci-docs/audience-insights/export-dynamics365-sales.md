---
title: A Customer Insights adatok a Dynamics 365 Salesbe való exportálása
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a Dynamics 365 Salesbe.
ms.date: 03/03/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: phkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: fc1a05ba4d21d96aa1a9724d158687bbb86949b6
ms.sourcegitcommit: 1b671c6100991fea1cace04b5d4fcedcd88aa94f
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/31/2021
ms.locfileid: "5759607"
---
# <a name="use-segments-in-dynamics-365-sales-preview"></a><span data-ttu-id="70625-103">Szegmensek használata a Dynamics 365 Sales alkalmazásban (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="70625-103">Use segments in Dynamics 365 Sales (preview)</span></span>

[!INCLUDE [cc-data-platform-banner](../includes/cc-data-platform-banner.md)]

<span data-ttu-id="70625-104">A Dynamics 365 Sales modullal az ügyféladatokból marketinglistákat hozhat létre, nyomon követheti a munkafolyamatokat, és promóciós anyagokat küldhet ki.</span><span class="sxs-lookup"><span data-stu-id="70625-104">Use your customer data to create marketing lists, follow up workflows, and send out promotions with Dynamics 365 Sales.</span></span>

## <a name="prerequisite-for-connection"></a><span data-ttu-id="70625-105">A kapcsolat előfeltétele</span><span class="sxs-lookup"><span data-stu-id="70625-105">Prerequisite for connection</span></span>

1. <span data-ttu-id="70625-106">A kapcsolattartók bejegyzésének jelen kell lennie a Dynamics 365 Sales alkalmazásban, mielőtt egy szegmenst exportálhatna a Customer Insights alkalmazásból a Sales alkalmazásba.</span><span class="sxs-lookup"><span data-stu-id="70625-106">Contact records must be present in Dynamics 365 Sales before you can export a segment from Customer Insights to Sales.</span></span> <span data-ttu-id="70625-107">További információ a kapcsolattartók betöltéséről [a Dynamics 365 Sales alkalmazásba a Common Data Services használatával](connect-power-query.md).</span><span class="sxs-lookup"><span data-stu-id="70625-107">Read more on how to ingest contacts in [Dynamics 365 Sales using Common Data Services](connect-power-query.md).</span></span>

   > [!NOTE]
   > <span data-ttu-id="70625-108">Ha szegmenseket exportál a célközönséggel kapcsolatos információkból a Sales nem hoz létre új kapcsolattartói rekordokat a Sales példányban.</span><span class="sxs-lookup"><span data-stu-id="70625-108">Exporting segments from audience insights to Sales will not create new contact records in the Sales instances.</span></span> <span data-ttu-id="70625-109">A Sales kapcsolattartói bejegyzéseket be kell tölteni a célközönség kapcsolatos információkba és adatforrásként használni.</span><span class="sxs-lookup"><span data-stu-id="70625-109">The contact records from Sales must be ingested in audience insights and used as a data source.</span></span> <span data-ttu-id="70625-110">Emellett szerepelniük kell az egyesített Ügyfél entitásban ahhoz, hogy a szegmensek exportálása előtt le tudják képezni az ügyfélazonosítókat.</span><span class="sxs-lookup"><span data-stu-id="70625-110">They also need to be included in the unified Customer entity to map customer IDs to contact IDs before segments can be exported.</span></span>

## <a name="set-up-the-connection-to-sales"></a><span data-ttu-id="70625-111">Állítsa be a Sales rendszerrel való kapcsolatot</span><span class="sxs-lookup"><span data-stu-id="70625-111">Set up the connection to Sales</span></span>

1. <span data-ttu-id="70625-112">Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="70625-112">Go to **Admin** > **Connections**.</span></span>

1. <span data-ttu-id="70625-113">Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza a **Dynamics 365 Sales** lehetőséget a kapcsolat konfigurálásához.</span><span class="sxs-lookup"><span data-stu-id="70625-113">Select **Add connection** and choose **Dynamics 365 Sales** to configure the connection.</span></span>

1. <span data-ttu-id="70625-114">Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak.</span><span class="sxs-lookup"><span data-stu-id="70625-114">Give your connection a recognizable name in the **Display name** field.</span></span> <span data-ttu-id="70625-115">A név és a kapcsolat típusa írja le ezt a kapcsolatot.</span><span class="sxs-lookup"><span data-stu-id="70625-115">The name and the type of the connection describe this connection.</span></span> <span data-ttu-id="70625-116">Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.</span><span class="sxs-lookup"><span data-stu-id="70625-116">We recommend choosing a name that explains the purpose and target of the connection.</span></span>

1. <span data-ttu-id="70625-117">A kapcsolat használóinak kiválasztása.</span><span class="sxs-lookup"><span data-stu-id="70625-117">Choose who can use this connection.</span></span> <span data-ttu-id="70625-118">Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz.</span><span class="sxs-lookup"><span data-stu-id="70625-118">If you take no action, the default will be Administrators.</span></span> <span data-ttu-id="70625-119">További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).</span><span class="sxs-lookup"><span data-stu-id="70625-119">For more information, see [Allow contributors to use a connection for exports](connections.md#allow-contributors-to-use-a-connection-for-exports).</span></span>

1. <span data-ttu-id="70625-120">Adja meg a szervezet értékesítési URL-címét a **Kiszolgáló címe** mezőben.</span><span class="sxs-lookup"><span data-stu-id="70625-120">Enter your organization's Sales URL in the **Server address** field.</span></span>

1. <span data-ttu-id="70625-121">A **Kiszolgáló rendszergazdai fiókja** területen válassza a **Bejelentkezés** lehetőséget, és válasszon egy Dynamics 365 Sales fiókot.</span><span class="sxs-lookup"><span data-stu-id="70625-121">In the **Server admin account** section, select **Sign in** and choose a Dynamics 365 Sales account.</span></span>

1. <span data-ttu-id="70625-122">Az ügyfélazonosító mező leképezése a Dynamics 365 kapcsolattartói azonosítóhoz.</span><span class="sxs-lookup"><span data-stu-id="70625-122">Map a customer ID field to the Dynamics 365 Contact ID.</span></span>

1. <span data-ttu-id="70625-123">A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="70625-123">Select **Save** to complete the connection.</span></span> 

## <a name="configure-an-export"></a><span data-ttu-id="70625-124">Exportálás konfigurálása</span><span class="sxs-lookup"><span data-stu-id="70625-124">Configure an export</span></span>

<span data-ttu-id="70625-125">Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz.</span><span class="sxs-lookup"><span data-stu-id="70625-125">You can configure this export if you have access to a connection of this type.</span></span> <span data-ttu-id="70625-126">További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).</span><span class="sxs-lookup"><span data-stu-id="70625-126">For more information, see [Permissions needed to configure an export](export-destinations.md#set-up-a-new-export).</span></span>

1. <span data-ttu-id="70625-127">Menjen az **Adatok** > **Exportálások** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="70625-127">Go to **Data** > **Exports**.</span></span>

1. <span data-ttu-id="70625-128">Új exportálás létrehozásához válassza a **Célhely hozzáadása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="70625-128">To create a new export, select **Add destination**.</span></span>

1. <span data-ttu-id="70625-129">A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot a Dynamics 365 Sales szakaszból.</span><span class="sxs-lookup"><span data-stu-id="70625-129">In the **Connection for export** field, choose a connection from the Dynamics 365 Sales section.</span></span> <span data-ttu-id="70625-130">Ha nem látja ezt a szakasznevet, az Ön számára nincs ilyen típusú kapcsolat.</span><span class="sxs-lookup"><span data-stu-id="70625-130">If you don't see this section name, there are no connections of this type available to you.</span></span>

1. <span data-ttu-id="70625-131">Jelöljön ki egy vagy több szegmenst.</span><span class="sxs-lookup"><span data-stu-id="70625-131">Choose one or more segments.</span></span>

1. <span data-ttu-id="70625-132">Válassza a **Mentés** lehetőséget</span><span class="sxs-lookup"><span data-stu-id="70625-132">Select **Save**</span></span>

<span data-ttu-id="70625-133">Az exportálás mentése nem futtatja azonnal az exportálást.</span><span class="sxs-lookup"><span data-stu-id="70625-133">Saving an export doesn't run the export immediately.</span></span>

<span data-ttu-id="70625-134">Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut.</span><span class="sxs-lookup"><span data-stu-id="70625-134">The export runs with every [scheduled refresh](system.md#schedule-tab).</span></span> <span data-ttu-id="70625-135">Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand).</span><span class="sxs-lookup"><span data-stu-id="70625-135">You can also [export data on demand](export-destinations.md#run-exports-on-demand).</span></span> 

[!INCLUDE[footer-include](../includes/footer-banner.md)]
