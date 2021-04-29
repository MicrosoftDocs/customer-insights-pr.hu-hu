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
ms.openlocfilehash: 10c338b89a6f9971912d05986c105cba1221b01b
ms.sourcegitcommit: aaa275c60c0c77c88196277b266a91d653f8f759
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/14/2021
ms.locfileid: "5896008"
---
# <a name="enrichment-for-customer-profiles-preview"></a><span data-ttu-id="a1e92-103">Az ügyfelek profiljainak bővítése (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="a1e92-103">Enrichment for customer profiles (preview)</span></span>

<span data-ttu-id="a1e92-104">Adatok felhasználása olyan forrásokból, mint például a Microsoft és más partnerek az ügyféladatok bővítése céljából.</span><span class="sxs-lookup"><span data-stu-id="a1e92-104">Use data from sources like Microsoft and other partners to enrich your customer data.</span></span>

:::image type="content" source="media/enrichment-hub-page.png" alt-text="A bővítési központ oldala":::

<span data-ttu-id="a1e92-106">A célközönség-információkban lépjen az **Adatok** > **Bővítés** pontra a bővítési lehetőségek használatához.</span><span class="sxs-lookup"><span data-stu-id="a1e92-106">In audience insights, go to **Data** > **Enrichment** to work with enrichment options.</span></span>    
<span data-ttu-id="a1e92-107">A bővítések létrehozásához vagy módosításához Közreműködő vagy Rendszergazdai engedélyekkel kell rendelkeznie.</span><span class="sxs-lookup"><span data-stu-id="a1e92-107">You need to have Contributor or Administrator permissions to create or edit enrichments.</span></span> <span data-ttu-id="a1e92-108">További tudnivalók: [Engedélyek](permissions.md).</span><span class="sxs-lookup"><span data-stu-id="a1e92-108">For more information, see [Permissions](permissions.md).</span></span>

<span data-ttu-id="a1e92-109">A **felderítés** lapon a következő bővítések találhatók:</span><span class="sxs-lookup"><span data-stu-id="a1e92-109">On the **Discover** tab, you'll find the following enrichments:</span></span>

- <span data-ttu-id="a1e92-110">A Microsoft által biztosított [márkák](enrichment-microsoft.md)</span><span class="sxs-lookup"><span data-stu-id="a1e92-110">[Brands](enrichment-microsoft.md) provided by Microsoft</span></span>
- <span data-ttu-id="a1e92-111">A Microsoft által biztosított [érdeklődési körök](enrichment-microsoft.md)</span><span class="sxs-lookup"><span data-stu-id="a1e92-111">[Interests](enrichment-microsoft.md) provided by Microsoft</span></span>
- <span data-ttu-id="a1e92-112">A Leadspace által biztosított [vállalati adatok](enrichment-leadspace.md)</span><span class="sxs-lookup"><span data-stu-id="a1e92-112">[Company data](enrichment-leadspace.md) provided by Leadspace</span></span>
- <span data-ttu-id="a1e92-113">[Demográfia](enrichment-experian.md) az Experiantól</span><span class="sxs-lookup"><span data-stu-id="a1e92-113">[Demographics](enrichment-experian.md) provided by Experian</span></span>
- <span data-ttu-id="a1e92-114">A [Helyadatokat](enrichment-here.md) a HERE Technologies biztosította</span><span class="sxs-lookup"><span data-stu-id="a1e92-114">[Location data](enrichment-here.md) provided by HERE Technologies</span></span>
- <span data-ttu-id="a1e92-115">[Egyéni adatok](enrichment-SFTP-custom-import.md) SFTP-importálás biztonságos fájlátviteli protokollján keresztül</span><span class="sxs-lookup"><span data-stu-id="a1e92-115">[Custom data](enrichment-SFTP-custom-import.md) through Secure File Transfer Protocol (SFTP)</span></span>

<span data-ttu-id="a1e92-116">A **saját bővítések** lapon megtekintheti, hogy milyen bővítés van beállítva, illetve hogy szerkesztheti-e a tulajdonságait.</span><span class="sxs-lookup"><span data-stu-id="a1e92-116">On the **My enrichments** tab, you can see the enrichments you've configured and edit their properties.</span></span>

## <a name="manage-existing-enrichments"></a><span data-ttu-id="a1e92-117">Meglévő bővítések kezelése</span><span class="sxs-lookup"><span data-stu-id="a1e92-117">Manage existing enrichments</span></span>

<span data-ttu-id="a1e92-118">Nyissa meg a **Saját bővítések** lehetőséget az összes konfigurált bővítés megtekintéséhez.</span><span class="sxs-lookup"><span data-stu-id="a1e92-118">Go to the **My enrichments** to see all configured enrichments.</span></span> <span data-ttu-id="a1e92-119">Minden bővítés egy sor formájában jelenik meg, amely további információkat tartalmaz a bővítésről.</span><span class="sxs-lookup"><span data-stu-id="a1e92-119">Each enrichment is represented as a row that includes additional information about the enrichment.</span></span>

<span data-ttu-id="a1e92-120">A rendelkezésre álló lehetőségek megtekintéséhez válasszon egy bővítést.</span><span class="sxs-lookup"><span data-stu-id="a1e92-120">Select an enrichment to see the available options.</span></span> <span data-ttu-id="a1e92-121">A listaelemen a három pont (...) kijelölésével megtekintheti a lehetőségeket.</span><span class="sxs-lookup"><span data-stu-id="a1e92-121">You can also select the ellipsis (...) on a list item to see the options.</span></span>

:::image type="content" source="media/enrichment-hub-options-run.png" alt-text="A bővítések listájában a bővítés kezelésére szolgáló lehetőségek":::

- <span data-ttu-id="a1e92-123">**Nézet** a bővítés részleteinek megtekintése a bővített ügyfelek profiljainak számával.</span><span class="sxs-lookup"><span data-stu-id="a1e92-123">**View** enrichment details with the number of enriched customer profiles.</span></span>
- <span data-ttu-id="a1e92-124">**Szerkesztheti** bővítés konfigurációját.</span><span class="sxs-lookup"><span data-stu-id="a1e92-124">**Edit** the enrichment configuration.</span></span>
- <span data-ttu-id="a1e92-125">A bővítés **Futtatásával** frissítheti az ügyfelek profiljait a legfrissebb adatokkal.</span><span class="sxs-lookup"><span data-stu-id="a1e92-125">**Run** the enrichment to update customer profiles with the latest data.</span></span>
- <span data-ttu-id="a1e92-126">**Inaktiválhat** egy meglévő bővítést, hogy leállítsa annak automatikus frissítését az egyes ütemezett frissítések során.</span><span class="sxs-lookup"><span data-stu-id="a1e92-126">**Deactivate** an existing enrichment to stop it from refreshing automatically with every scheduled refresh.</span></span> <span data-ttu-id="a1e92-127">Az utolsó sikeres frissítésből származó adatok továbbra is elérhetők lesznek.</span><span class="sxs-lookup"><span data-stu-id="a1e92-127">Data from the last successful refresh will continue to be available.</span></span> <span data-ttu-id="a1e92-128">**Aktiválhat** egy inaktív bővítést az automatikus frissítés újraindításához minden ütemezett frissítéshez.</span><span class="sxs-lookup"><span data-stu-id="a1e92-128">**Activate** an inactive enrichment to restart automatic refreshing with every scheduled refresh.</span></span>
- <span data-ttu-id="a1e92-129">Egy bővítés **törlése**.</span><span class="sxs-lookup"><span data-stu-id="a1e92-129">**Delete** an enrichment.</span></span>

<span data-ttu-id="a1e92-130">Egyszerre több bővítést is futtathat vagy inaktiválhat, ha kijelöli azokat a listából.</span><span class="sxs-lookup"><span data-stu-id="a1e92-130">You can run or deactivate multiple enrichments at once by selecting them in the list.</span></span> <span data-ttu-id="a1e92-131">A beállítások megtekintése és szerkesztése nem érhető el tömeges műveletként, és egyszerre csak egy bővítéshez használható.</span><span class="sxs-lookup"><span data-stu-id="a1e92-131">View and edit options aren't available as bulk action and only work for one enrichment at a time.</span></span>

## <a name="enrichments-and-connections"></a><span data-ttu-id="a1e92-132">Bővítések és kapcsolatok</span><span class="sxs-lookup"><span data-stu-id="a1e92-132">Enrichments and connections</span></span>

<span data-ttu-id="a1e92-133">A külső gyártótól származó bővítéseket a [kapcsolatok](connections.md) használatával konfigurálhatja, amelyekhez a rendszergazda hitelesítő adatokat állít be, és hozzájárul az adatok átviteléhez.</span><span class="sxs-lookup"><span data-stu-id="a1e92-133">Third-party enrichments are configured using [connections](connections.md), which an administrator sets up with credentials and provides consent for data transfers.</span></span> <span data-ttu-id="a1e92-134">A kapcsolat ezután a rendszergazdák és a közreműködők által is használható a bővítések konfigurálásához.</span><span class="sxs-lookup"><span data-stu-id="a1e92-134">The connection can be used by administrators and contributors to configure enrichments.</span></span>  

## <a name="multiple-enrichments-of-the-same-type"></a><span data-ttu-id="a1e92-135">Azonos típusú többszörös bővítések</span><span class="sxs-lookup"><span data-stu-id="a1e92-135">Multiple enrichments of the same type</span></span>

<span data-ttu-id="a1e92-136">A bővíteni kívánt entitást a bővítési konfiguráció során adja meg, ezzel lehetővé teszi, hogy csak a profilok egy részében bővítsen.</span><span class="sxs-lookup"><span data-stu-id="a1e92-136">The entity to be enriched is specified during the enrichment configuration, which allows you to enrich only a subset of your profiles.</span></span> <span data-ttu-id="a1e92-137">Például csak egy adott szegmensre vonatkozó adatok bővítése.</span><span class="sxs-lookup"><span data-stu-id="a1e92-137">For exmaple, enrich data only for a specific segment.</span></span> <span data-ttu-id="a1e92-138">Konfigurálhat több ugyanolyan típusú bővítést, és újra felhasználhatja ugyanazt a kapcsolatot.</span><span class="sxs-lookup"><span data-stu-id="a1e92-138">You can configure several enrichments of the same type and reuse the same connection.</span></span> <span data-ttu-id="a1e92-139">Egyes bővítések az azonos típusú, létrehozható bővítések számára vonatkoznak korlátozások.</span><span class="sxs-lookup"><span data-stu-id="a1e92-139">Some enrichments will have limits to the number of enrichments of the same type that can be created.</span></span> <span data-ttu-id="a1e92-140">A korlátok és az aktuális használat a **Bővítés** oldalon látható.</span><span class="sxs-lookup"><span data-stu-id="a1e92-140">The limits and current use can be seen on the **Enrichment** page.</span></span>

[!INCLUDE[footer-include](../includes/footer-banner.md)]
