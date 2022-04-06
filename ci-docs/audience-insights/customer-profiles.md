---
title: Ügyfélprofilok megtekintése
description: Az egyesített ügyféladatok kombinált nézetének lekérése.
ms.date: 09/30/2021
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: conceptual
author: Nils-2m
ms.author: nikeller
manager: shellyha
searchScope:
- ci-customers-page
- ci-customer-card
- ci-activities
- ci-activities-wizard
- customerInsights
ms.openlocfilehash: 074d84eff65d52b083fff6c161282d4fafa1af85
ms.sourcegitcommit: 5bd07f3a1288f003704acd576741cf6aedc1ac33
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/31/2022
ms.locfileid: "8523729"
---
# <a name="customer-profiles"></a>Ügyfélprofilok

Az **Ügyfelek** oldal a egyesített ügyfélprofilok összesített nézetét jeleníti meg. Az ügyfélprofilok az [egységesített ügyfélentitás létrehozása után](data-unification.md) érhetők el. A lapon ügyfeleket kereshet, és meghatározhatja az adott keresés indexét.

Az ügyfelek egyének vagy szervezetek is lehetnek. Minden ügyfélprofilt egy csempe képvisel. A több bejegyzéshez használja az oldalszámvezérlőket. A kártya megjeleníti az *Ügyfél* entitás mezőit a **Keresés és szűrő** indexében meghatározottak szerint. Az egyes kartonokon belüli mezők sorrendjét a rendszer választja ki.

Válassza ki a mozaikot, ha látni fogja a kijelölt ügyfél adatait egy [Ügyfél adatai lap](customer-profiles.md#customer-details-page) nevű dedikált oldalon.

> [!div class="mx-imgBorder"] 
> ![Az Ügyfelek oldal mutatja az eredmény csempéket](media/customers-page-result-tiles-B2C.png "Az Ügyfelek oldal mutatja az eredmény csempéket")

> [!NOTE]
> Ha a navigációban az **Ügyfelek** lehetőséget választva nem látja a mozaikokat, a rendszergazdának legalább [egy kereshető attribútumot meg kell határoznia](search-filter-index.md) a **Keresés és szűrés indexben**.

## <a name="search-for-customers"></a>Ügyfelek keresése

Az ügyfelek megkereséséhez írja be a nevet vagy más attribútumot a keresőmezőbe. A keresés csak az adategyesítési folyamat során létrehozott _Ügyfél_ entitáson belül működik.

Rendszergazdaként a kereshető attribútumokat a **keresési & szűrő indexe** oldalon adhatja meg. További tájékoztatásért keresse fel a [Keresés és szűrő index kezelése](search-filter-index.md) oldalon található adatokat.

## <a name="filter-customers"></a>Ügyfelek szűrése

Az ügyfeleket az _Ügyfél_ entitása mezői szerint szűrheti. A kereséshez hasonlóan az adminisztrátornak először meg kell határoznia a mezőket kereshetőként a **keresési & szűrő index** oldal használatával.

1. Válassza a **Szűrők megjelenítése** lehetőséget az **Ügyfelek** lapon.

1. Jelölje be a jelölőnégyzetet azon attribútumok mellett, amelyek alapján az ügyfeleket szűrni szeretné.

1. Távolítsa el a szűrőket a **Szűrők törlése** lehetőséggel az **Ügyfelek** oldalon.

## <a name="customer-details-page"></a>Ügyféladatok oldal

Az **Ügyféladatok oldal** megnyitásához válassza ki bármelyik ügyfélcsempét. Ez a nézet a kijelölt ügyfélre vonatkozóan egységesített információkat tartalmaz. Az ügyfelek adatai a következő tartalmakat tartalmazzák:

**Ügyfélprofil mozaikja**: Ez a mozaik mutatja a egyesített _Ügyfél_ entitás különböző értékeit. Ha egy mezőnek nincs értéke a kijelölt ügyfélprofilhoz, akkor nem fog megjelenni. A mozaik szakaszokra van felosztva:  
  - Az első szakasz a mezők előre megadott halmazát, majd a keresés és szűrőindex részét képezi. Ha a profil ilyen mezőket tartalmaz, akkor a címhez kapcsolódó mezők egyetlen sorban vannak kombinálva. 
  - **Kapcsolattartók ehhez az ügyfélhez**: Üzleti partnerek környezetében az ügyfélhez kapcsolódó összes kapcsolattartó második szakaszként látható. Minden kapcsolattartó megjelenik a saját mezőivel. Az üres mezők rejtettek.
  - **További mezők**: A kijelölt ügyfél fennmaradó mezőit jeleníti meg az adatok kivételével. 
  - **IDs**: Felsorolja az összeset a megfelelő entitásnév alatt. A mezőket a szemantikájaik azonosítják, és ezek minősítik őket.

**Tevékenység ütemezése**: A tevékenységek konfigurálása esetén az adatokat jeleníti meg. Az idővonal nézet időrendi sorrendben rendezi a kijelölt ügyfél tevékenységeit, kezdve a legújabb tevékenységgel. További információt az [Ügyféltevékenységek](activities.md) részben találhat.

**Elemzések**:  
  - **Mérés**: Azt mutatja, hogy egy vagy több ügyfélattribútum-méri-e a konfigurált attribútumot. Magukban foglalják az egyéni ügyfelek szintjén az ügyfelekhez számított fő teljesítménymutatókat. További tájékoztatásért menjen a [Definiálás és kezelés](measures.md) oldalra.

  - **Lehetséges érdeklődés, potenciális érdeklődés**: Megmutatja, hogy beállított-e márka vagy érdeklődés gyarapítására. A kiválasztott ügyfélprofilhoz hasonló profillal épülő potenciális érdeklődési okat és feltételeket képvisel. További tájékoztatást az [Ügyfélprofilok gyarapítása márkahűséggel és érdeklődéssel](enrichment-microsoft.md) oldalon találhat.

Az ügyfélkeresési lapra való visszatéréshez válassza a **Vissza az ügyfelekhez** lehetőséget.

## <a name="next-steps"></a>További lépések

[Vegyen fel további adatforrásokat](data-sources.md), [gyarapítsa az egységes profilokat](enrichment-hub.md), vagy [hozzon létre szegmenseket](segments.md) a más alkalmazásokban egységesített ügyfélprofilokkal való munkához.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
