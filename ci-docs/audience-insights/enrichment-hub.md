---
title: Az egyesített ügyfélprofilok bővítése
description: A funkciók segítségével bővítheti az ügyféladatokat.
ms.date: 11/02/2020
ms.reviewer: kishorem
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: 6b73aa93ec1a98f2b8d20d02e88bc6304f887078
ms.sourcegitcommit: 139548f8a2d0f24d54c4a6c404a743eeeb8ef8e0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/15/2021
ms.locfileid: "5269471"
---
# <a name="enrichment-for-customer-profiles-preview"></a><span data-ttu-id="5140a-103">Az ügyfelek profiljainak bővítése (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="5140a-103">Enrichment for customer profiles (preview)</span></span>

<span data-ttu-id="5140a-104">Adatok felhasználása olyan forrásokból, mint például a Microsoft és más partnerek az ügyféladatok bővítése céljából.</span><span class="sxs-lookup"><span data-stu-id="5140a-104">Use data from sources like Microsoft and other partners to enrich your customer data.</span></span>

:::image type="content" source="media/enrichment-hub-page.png" alt-text="A bővítési központ oldala":::

<span data-ttu-id="5140a-106">A célközönség-információkban lépjen az **Adatok** > **Bővítés** pontra a bővítési lehetőségek használatához.</span><span class="sxs-lookup"><span data-stu-id="5140a-106">In audience insights, go to **Data** > **Enrichment** to work with enrichment options.</span></span>    
<span data-ttu-id="5140a-107">A bővítések létrehozásához vagy módosításához Közreműködő vagy Rendszergazdai engedélyekkel kell rendelkeznie.</span><span class="sxs-lookup"><span data-stu-id="5140a-107">You need to have Contributor or Administrator permissions to create or edit enrichments.</span></span> <span data-ttu-id="5140a-108">További tudnivalók: [Engedélyek](permissions.md).</span><span class="sxs-lookup"><span data-stu-id="5140a-108">For more information, see [Permissions](permissions.md).</span></span>

<span data-ttu-id="5140a-109">A **felderítés** lapon a következő bővítések találhatók:</span><span class="sxs-lookup"><span data-stu-id="5140a-109">On the **Discover** tab, you'll find the following enrichments:</span></span>

- <span data-ttu-id="5140a-110">[Márkák](enrichment-microsoft-graph.md) a Microsoft Graph által biztosítva.</span><span class="sxs-lookup"><span data-stu-id="5140a-110">[Brands](enrichment-microsoft-graph.md) provided by Microsoft Graph</span></span>
- <span data-ttu-id="5140a-111">[Érdeklődési körök](enrichment-microsoft-graph.md) a Microsoft Graph által biztosítva.</span><span class="sxs-lookup"><span data-stu-id="5140a-111">[Interests](enrichment-microsoft-graph.md) provided by Microsoft Graph</span></span>
- <span data-ttu-id="5140a-112">A Leadspace által biztosított [vállalati adatok](enrichment-leadspace.md)</span><span class="sxs-lookup"><span data-stu-id="5140a-112">[Company data](enrichment-leadspace.md) provided by Leadspace</span></span>
- <span data-ttu-id="5140a-113">[Demográfia](enrichment-experian.md) az Experiantól</span><span class="sxs-lookup"><span data-stu-id="5140a-113">[Demographics](enrichment-experian.md) provided by Experian</span></span>
- <span data-ttu-id="5140a-114">A [Helyadatokat](enrichment-here.md) a HERE Technologies biztosította</span><span class="sxs-lookup"><span data-stu-id="5140a-114">[Location data](enrichment-here.md) provided by HERE Technologies</span></span>
- <span data-ttu-id="5140a-115">[Egyéni adatok](enrichment-SFTP-custom-import.md) SFTP-importálás biztonságos fájlátviteli protokollján keresztül</span><span class="sxs-lookup"><span data-stu-id="5140a-115">[Custom data](enrichment-SFTP-custom-import.md) through Secure File Transfer Protocol (SFTP)</span></span>

<span data-ttu-id="5140a-116">A **saját bővítések** lapon megtekintheti, hogy milyen bővítés van beállítva, illetve hogy szerkesztheti-e a tulajdonságait.</span><span class="sxs-lookup"><span data-stu-id="5140a-116">On the **My enrichments** tab, you can see the enrichments you've configured and edit their properties.</span></span>

## <a name="manage-existing-enrichments"></a><span data-ttu-id="5140a-117">Meglévő bővítések kezelése</span><span class="sxs-lookup"><span data-stu-id="5140a-117">Manage existing enrichments</span></span>

<span data-ttu-id="5140a-118">Nyissa meg a **Saját bővítések** lehetőséget az összes konfigurált bővítés megtekintéséhez.</span><span class="sxs-lookup"><span data-stu-id="5140a-118">Go to the **My enrichments** to see all configured enrichments.</span></span> <span data-ttu-id="5140a-119">Minden bővítés egy sor formájában jelenik meg, amely további információkat tartalmaz a bővítésről.</span><span class="sxs-lookup"><span data-stu-id="5140a-119">Each enrichment is represented as a row that includes additional information about the enrichment.</span></span>

<span data-ttu-id="5140a-120">A rendelkezésre álló lehetőségek megtekintéséhez válasszon egy bővítést.</span><span class="sxs-lookup"><span data-stu-id="5140a-120">Select an enrichment to see the available options.</span></span> <span data-ttu-id="5140a-121">Másik lehetőségként kiválaszthatja a három pont (…) elemet egy listaelemnél a lehetőségek megtekintéséhez.</span><span class="sxs-lookup"><span data-stu-id="5140a-121">Alternatively, you can select the ellipsis (...) on a list item to see the options.</span></span>

:::image type="content" source="media/enrichment-hub-options-run.png" alt-text="A bővítések listájában a bővítés kezelésére szolgáló lehetőségek":::

- <span data-ttu-id="5140a-123">**Nézet** a bővítés részleteinek megtekintése a bővített ügyfelek profiljainak számával.</span><span class="sxs-lookup"><span data-stu-id="5140a-123">**View** enrichment details with the number of enriched customer profiles.</span></span>
- <span data-ttu-id="5140a-124">**Szerkesztheti** bővítés konfigurációját.</span><span class="sxs-lookup"><span data-stu-id="5140a-124">**Edit** the enrichment configuration.</span></span>
- <span data-ttu-id="5140a-125">A bővítés **Futtatásával** frissítheti az ügyfelek profiljait a legfrissebb adatokkal.</span><span class="sxs-lookup"><span data-stu-id="5140a-125">**Run** the enrichment to update customer profiles with the latest data.</span></span>
- <span data-ttu-id="5140a-126">**Inaktiválhat** egy meglévő bővítést, hogy leállítsa annak automatikus frissítését az egyes ütemezett frissítések során.</span><span class="sxs-lookup"><span data-stu-id="5140a-126">**Deactivate** an existing enrichment to stop it from refreshing automatically with every scheduled refresh.</span></span> <span data-ttu-id="5140a-127">Az utolsó sikeres frissítésből származó adatok továbbra is elérhetők lesznek.</span><span class="sxs-lookup"><span data-stu-id="5140a-127">Data from the last successful refresh will continue to be available.</span></span> <span data-ttu-id="5140a-128">**Aktiválhat** egy inaktív bővítést az automatikus frissítés újraindításához minden ütemezett frissítéshez.</span><span class="sxs-lookup"><span data-stu-id="5140a-128">**Activate** an inactive enrichment to restart automatic refreshing with every scheduled refresh.</span></span>
- <span data-ttu-id="5140a-129">Egy bővítés **törlése**.</span><span class="sxs-lookup"><span data-stu-id="5140a-129">**Delete** an enrichment.</span></span>

<span data-ttu-id="5140a-130">Egyszerre több bővítést is futtathat vagy inaktiválhat, ha kijelöli azokat a listából.</span><span class="sxs-lookup"><span data-stu-id="5140a-130">You can run or deactivate multiple enrichments at once by selecting them in the list.</span></span> <span data-ttu-id="5140a-131">A beállítások megtekintése és szerkesztése nem érhető el tömeges műveletként, és egyszerre csak egy bővítéshez használható.</span><span class="sxs-lookup"><span data-stu-id="5140a-131">View and edit options aren't available as bulk action and only work for one enrichment at a time.</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]