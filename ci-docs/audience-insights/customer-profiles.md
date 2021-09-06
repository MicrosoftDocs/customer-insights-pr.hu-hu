---
title: Ügyfélprofilok megtekintése
description: Az egyesített ügyféladatok kombinált nézetének lekérése.
ms.date: 12/01/2020
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: NimrodMagen
ms.author: nimagen
manager: shellyha
ms.openlocfilehash: 87323d15c44ef82ae8bc3cc971be6c36356121571cb9a9630be699ac2d157bf6
ms.sourcegitcommit: aa0cfbf6240a9f560e3131bdec63e051a8786dd4
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/10/2021
ms.locfileid: "7032807"
---
# <a name="customer-profiles"></a>Ügyfélprofilok

Az **Ügyfelek** lap az [összes adatforrásból](data-sources.md) összegyűjtött profiladatok alapján jeleníti meg az ügyfelek kombinált nézetét . Az ügyfelek profiljai csak az [egyesített ügyfél entitáslétrehozása](data-unification.md) után érhetők el. Ügyeljen arra, hogy az adatok egyesítésének folyamatát végrehajtsa, hogy bővített nézetet kapjon az ügyfelekről. Az oldal segítségével megkeresheti az ügyfeleket is.

Az ügyfelek lehetnek egyének vagy szervezetek (előzetes verzió). Minden egyes ügyfél- vagy szervezeti profilt egy csempe képvisel. A csempét kiválasztva megtekintheti az adott ügyfélre vagy szervezetre vonatkozó további információkat. További rekordok megtekintéséhez használja a lap alján található oldalszámozási vezérlőket.

> [!div class="mx-imgBorder"] 
> ![B2C ügyfélprofilok.](media/profiles-customers.png "B2C ügyfélprofilok")

Szervezetek (előzetes verzió)
> [!div class="mx-imgBorder"] 
> ![B2B ügyfélprofilok.](media/profile-customers-b2b.png "B2B ügyfélprofilok")

> [!NOTE]
> Ha nem látja a csempéket, amikor a navigációban kiválasztja az **Ügyfelek** elemet, a rendszergazdának [legalább egy kereshető attribútumot meg kell adnia](search-filter-index.md) a **Keresési és szűrőindex** pontban.

## <a name="search-for-customers"></a>Ügyfelek keresése

Az ügyfelek megkereséséhez írja be a nevet vagy más attribútumot a keresőmezőbe. A keresés csak az adategyesítési folyamat során létrehozott ügyfélprofil entitáson belül működik.

Rendszergazdaként a kereshető attribútumokat a **keresési & szűrő indexe** oldalon adhatja meg. További tudnivalókért lásd: [A keresési és szűrési index kezelése](search-filter-index.md).

## <a name="filter-customers"></a>Ügyfelek szűrése

Az ügyfelek az ügyfélprofil entitás mezői alapján szűrhetők. A kereséshez hasonlóan az adminisztrátornak először meg kell határoznia a mezőket kereshetőként a **keresési & szűrő index** oldal használatával.

1. Válassza a **Szűrő** lehetőséget az **Ügyfelek** oldalon.

2. Jelölje be a jelölőnégyzetet azon attribútumok mellett, amelyek alapján az ügyfeleket szűrni szeretné.

   > [!div class="mx-imgBorder"] 
   > ![Ügyfélprofilok.](media/profiles-customers3.png "Ügyfélprofilok")

3. Távolítsa el a szűrőket a **Szűrők törlése** lehetőséggel az **Ügyfelek** oldalon.

##  <a name="customer-details-page"></a>Ügyféladatok oldal

Az **Ügyféladatok oldal** megnyitásához válassza ki bármelyik ügyfélcsempét. Ez a nézet a kijelölt ügyfélre vonatkozóan egységesített információkat tartalmaz.

Az ügyféladatok a következőket tartalmazza:

-   **Ügyfélprofil csempe:** Ez a csempe megjeleníti az egyesített ügyfélprofil entitás különböző értékeit. Az adatok között szerepelhet az e-mail-cím, a név, a város stb. 

-   **Lehetséges érdeklődési körök, lehetséges márkák**: Azt mutatja, hogy konfigurált-e elsődleges bővítést. Lehetséges érdeklődési köröket és márkahűségeket jelent egy olyan ügyfélre vonatkozóan, akinek a profilja hasonló lehet ehhez az ügyfélhez. További információkért lásd: [Ügyfélprofilok bővítése márka- és érdeklődésikör-hűséggel](enrichment-microsoft.md).

-   **Mérőszámok**: Azt mutatja, hogy adott típus egy vagy több mérőszáma konfigurált-e: az ügyfél attribútumára vonatkozó mérőszámok. Magukban foglalják az egyéni ügyfelek szintjén az ügyfelekhez számított fő teljesítménymutatókat. További információ: [Mérőszámok meghatározása és kezelése](measures.md).

-   **Tevékenység idősora**: Azt mutatja, hogy van-e konfigurált tevékenysége. Az Idősornézet az ügyfél időrendben rendezett tevékenységeit tartalmazza, a legutóbbi tevékenységtől kezdve. További információ: [Ügyféltevékenységek](activities.md).

A **Visszatérés az Ügyfelekhez** lehetőséggel visszatérhet az ügyfelek keresési oldalára.

## <a name="next-steps"></a>További lépések

[Vegyen fel további adatforrásokat](data-sources.md), [gyarapítsa az egyesített profilokat](enrichment-hub.md), vagy [hozzon létre szegmenseket](segments.md), hogy más alkalmazásokban egységesített profilokkal dolgozzon.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
