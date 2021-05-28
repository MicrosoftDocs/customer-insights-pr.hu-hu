---
title: Az egyesített ügyfélprofilok bővítése
description: A funkciók segítségével bővítheti az ügyféladatokat.
ms.date: 04/09/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: jodahlMSFT
ms.author: jodahl
manager: shellyha
ms.openlocfilehash: c8e4a7247ccf575a62440038180010916b09d51b
ms.sourcegitcommit: f9e2fa3f11ecf11a5d9cccc376fdeb1ecea54880
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/28/2021
ms.locfileid: "5954490"
---
# <a name="enrichment-for-customer-profiles-preview"></a><span data-ttu-id="0069e-103">Az ügyfelek profiljainak bővítése (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="0069e-103">Enrichment for customer profiles (preview)</span></span>

<span data-ttu-id="0069e-104">Adatok felhasználása olyan forrásokból, mint például a Microsoft és más partnerek az ügyféladatok bővítése céljából.</span><span class="sxs-lookup"><span data-stu-id="0069e-104">Use data from sources like Microsoft and other partners to enrich your customer data.</span></span>

:::image type="content" source="media/enrichment-hub-page.png" alt-text="A bővítési központ oldala":::

<span data-ttu-id="0069e-106">A célközönség-információkban lépjen az **Adatok** > **Bővítés** pontra a bővítési lehetőségek használatához.</span><span class="sxs-lookup"><span data-stu-id="0069e-106">In audience insights, go to **Data** > **Enrichment** to work with enrichment options.</span></span>    
<span data-ttu-id="0069e-107">A bővítések létrehozásához vagy módosításához Közreműködő vagy Rendszergazdai engedélyekkel kell rendelkeznie.</span><span class="sxs-lookup"><span data-stu-id="0069e-107">You need to have Contributor or Administrator permissions to create or edit enrichments.</span></span> <span data-ttu-id="0069e-108">További tudnivalók: [Engedélyek](permissions.md).</span><span class="sxs-lookup"><span data-stu-id="0069e-108">For more information, see [Permissions](permissions.md).</span></span>

<span data-ttu-id="0069e-109">A **felderítés** lapon a következő bővítések találhatók:</span><span class="sxs-lookup"><span data-stu-id="0069e-109">On the **Discover** tab, you'll find the following enrichments:</span></span>

- <span data-ttu-id="0069e-110">A Microsoft által biztosított [márkák](enrichment-microsoft.md)</span><span class="sxs-lookup"><span data-stu-id="0069e-110">[Brands](enrichment-microsoft.md) provided by Microsoft</span></span>
- <span data-ttu-id="0069e-111">A Microsoft által biztosított [érdeklődési körök](enrichment-microsoft.md)</span><span class="sxs-lookup"><span data-stu-id="0069e-111">[Interests](enrichment-microsoft.md) provided by Microsoft</span></span>
- <span data-ttu-id="0069e-112">A Microsoft által biztosított [továbbfejlesztett címek](enrichment-enhanced-addresses.md)</span><span class="sxs-lookup"><span data-stu-id="0069e-112">[Enhanced addresses](enrichment-enhanced-addresses.md) provided by Microsoft</span></span>
- <span data-ttu-id="0069e-113">A Leadspace által biztosított [vállalati adatok](enrichment-leadspace.md)</span><span class="sxs-lookup"><span data-stu-id="0069e-113">[Company data](enrichment-leadspace.md) provided by Leadspace</span></span>
- <span data-ttu-id="0069e-114">[Demográfia](enrichment-experian.md) az Experiantól</span><span class="sxs-lookup"><span data-stu-id="0069e-114">[Demographics](enrichment-experian.md) provided by Experian</span></span>
- <span data-ttu-id="0069e-115">A [Helyadatokat](enrichment-here.md) a HERE Technologies biztosította</span><span class="sxs-lookup"><span data-stu-id="0069e-115">[Location data](enrichment-here.md) provided by HERE Technologies</span></span>
- <span data-ttu-id="0069e-116">[Egyéni adatok](enrichment-SFTP-custom-import.md) SFTP-importálás biztonságos fájlátviteli protokollján keresztül</span><span class="sxs-lookup"><span data-stu-id="0069e-116">[Custom data](enrichment-SFTP-custom-import.md) through Secure File Transfer Protocol (SFTP)</span></span>

<span data-ttu-id="0069e-117">A **saját bővítések** lapon megtekintheti, hogy milyen bővítés van beállítva, illetve hogy szerkesztheti-e a tulajdonságait.</span><span class="sxs-lookup"><span data-stu-id="0069e-117">On the **My enrichments** tab, you can see the enrichments you've configured and edit their properties.</span></span>

## <a name="manage-existing-enrichments"></a><span data-ttu-id="0069e-118">Meglévő bővítések kezelése</span><span class="sxs-lookup"><span data-stu-id="0069e-118">Manage existing enrichments</span></span>

<span data-ttu-id="0069e-119">Nyissa meg a **Saját bővítések** lehetőséget az összes konfigurált bővítés megtekintéséhez.</span><span class="sxs-lookup"><span data-stu-id="0069e-119">Go to the **My enrichments** to see all configured enrichments.</span></span> <span data-ttu-id="0069e-120">Minden bővítés egy sor formájában jelenik meg, amely további információkat tartalmaz a bővítésről.</span><span class="sxs-lookup"><span data-stu-id="0069e-120">Each enrichment is represented as a row that includes additional information about the enrichment.</span></span>

<span data-ttu-id="0069e-121">A rendelkezésre álló lehetőségek megtekintéséhez válasszon egy bővítést.</span><span class="sxs-lookup"><span data-stu-id="0069e-121">Select an enrichment to see the available options.</span></span> <span data-ttu-id="0069e-122">A listaelemen a három pont (...) kijelölésével megtekintheti a lehetőségeket.</span><span class="sxs-lookup"><span data-stu-id="0069e-122">You can also select the ellipsis (...) on a list item to see the options.</span></span>

:::image type="content" source="media/enrichment-hub-options-run.png" alt-text="A bővítések listájában a bővítés kezelésére szolgáló lehetőségek":::

- <span data-ttu-id="0069e-124">**Nézet** a bővítés részleteinek megtekintése a bővített ügyfelek profiljainak számával.</span><span class="sxs-lookup"><span data-stu-id="0069e-124">**View** enrichment details with the number of enriched customer profiles.</span></span>
- <span data-ttu-id="0069e-125">**Szerkesztheti** bővítés konfigurációját.</span><span class="sxs-lookup"><span data-stu-id="0069e-125">**Edit** the enrichment configuration.</span></span>
- <span data-ttu-id="0069e-126">A bővítés **Futtatásával** frissítheti az ügyfelek profiljait a legfrissebb adatokkal.</span><span class="sxs-lookup"><span data-stu-id="0069e-126">**Run** the enrichment to update customer profiles with the latest data.</span></span>
- <span data-ttu-id="0069e-127">**Inaktiválhat** egy meglévő bővítést, hogy leállítsa annak automatikus frissítését az egyes ütemezett frissítések során.</span><span class="sxs-lookup"><span data-stu-id="0069e-127">**Deactivate** an existing enrichment to stop it from refreshing automatically with every scheduled refresh.</span></span> <span data-ttu-id="0069e-128">Az utolsó sikeres frissítésből származó adatok továbbra is elérhetők lesznek.</span><span class="sxs-lookup"><span data-stu-id="0069e-128">Data from the last successful refresh will continue to be available.</span></span> <span data-ttu-id="0069e-129">**Aktiválhat** egy inaktív bővítést az automatikus frissítés újraindításához minden ütemezett frissítéshez.</span><span class="sxs-lookup"><span data-stu-id="0069e-129">**Activate** an inactive enrichment to restart automatic refreshing with every scheduled refresh.</span></span>
- <span data-ttu-id="0069e-130">Egy bővítés **törlése**.</span><span class="sxs-lookup"><span data-stu-id="0069e-130">**Delete** an enrichment.</span></span>

<span data-ttu-id="0069e-131">Egyszerre több bővítést is futtathat vagy inaktiválhat, ha kijelöli azokat a listából.</span><span class="sxs-lookup"><span data-stu-id="0069e-131">You can run or deactivate multiple enrichments at once by selecting them in the list.</span></span> <span data-ttu-id="0069e-132">A beállítások megtekintése és szerkesztése nem érhető el tömeges műveletként, és egyszerre csak egy bővítéshez használható.</span><span class="sxs-lookup"><span data-stu-id="0069e-132">View and edit options aren't available as bulk action and only work for one enrichment at a time.</span></span>

## <a name="enrichments-and-connections"></a><span data-ttu-id="0069e-133">Bővítések és kapcsolatok</span><span class="sxs-lookup"><span data-stu-id="0069e-133">Enrichments and connections</span></span>

<span data-ttu-id="0069e-134">A külső gyártótól származó bővítéseket a [kapcsolatok](connections.md) használatával konfigurálhatja, amelyekhez a rendszergazda hitelesítő adatokat állít be, és hozzájárul az adatok átviteléhez.</span><span class="sxs-lookup"><span data-stu-id="0069e-134">Third-party enrichments are configured using [connections](connections.md), which an administrator sets up with credentials and provides consent for data transfers.</span></span> <span data-ttu-id="0069e-135">A kapcsolat ezután a rendszergazdák és a közreműködők által is használható a bővítések konfigurálásához.</span><span class="sxs-lookup"><span data-stu-id="0069e-135">The connection can be used by administrators and contributors to configure enrichments.</span></span>  

## <a name="multiple-enrichments-of-the-same-type"></a><span data-ttu-id="0069e-136">Azonos típusú többszörös bővítések</span><span class="sxs-lookup"><span data-stu-id="0069e-136">Multiple enrichments of the same type</span></span>

<span data-ttu-id="0069e-137">A bővíteni kívánt entitást a bővítési konfiguráció során adja meg, ezzel lehetővé teszi, hogy csak a profilok egy részében bővítsen.</span><span class="sxs-lookup"><span data-stu-id="0069e-137">The entity to be enriched is specified during the enrichment configuration, which allows you to enrich only a subset of your profiles.</span></span> <span data-ttu-id="0069e-138">Például csak egy adott szegmensre vonatkozó adatok bővítése.</span><span class="sxs-lookup"><span data-stu-id="0069e-138">For exmaple, enrich data only for a specific segment.</span></span> <span data-ttu-id="0069e-139">Konfigurálhat több ugyanolyan típusú bővítést, és újra felhasználhatja ugyanazt a kapcsolatot.</span><span class="sxs-lookup"><span data-stu-id="0069e-139">You can configure several enrichments of the same type and reuse the same connection.</span></span> <span data-ttu-id="0069e-140">Egyes bővítések az azonos típusú, létrehozható bővítések számára vonatkoznak korlátozások.</span><span class="sxs-lookup"><span data-stu-id="0069e-140">Some enrichments will have limits to the number of enrichments of the same type that can be created.</span></span> <span data-ttu-id="0069e-141">A korlátok és az aktuális használat a **Bővítés** oldalon látható.</span><span class="sxs-lookup"><span data-stu-id="0069e-141">The limits and current use can be seen on the **Enrichment** page.</span></span>

[!INCLUDE[footer-include](../includes/footer-banner.md)]
