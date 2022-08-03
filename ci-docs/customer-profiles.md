---
title: Ügyfélprofilok megtekintése
description: Tekintse meg az egyesített ügyféladatokat, beleértve a keresés és a szűrés használatát
ms.date: 06/08/2022
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
ms.openlocfilehash: 6cdf47e6997f230811dcb0f2cf5542f3a6db2367
ms.sourcegitcommit: c45c3e044034bf866b0662f80a59166cee4ababe
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/22/2022
ms.locfileid: "9188096"
---
# <a name="view-customer-profiles"></a>Ügyfélprofilok megtekintése

Az ügyfélprofilok az egyesített Ügyfél [entitás létrehozása után *érhetők el*](data-unification.md). Az egyesített ügyfélprofilok kombinált nézete megjelenik az **Ügyfelek** oldalon. Az ügyfelek egyének vagy szervezetek is lehetnek.

**Az Ügyfelek** oldalon megtekintheti ügyfeleit és profiljait. Minden ügyfélprofilt egy csempe képvisel. A több bejegyzéshez használja az oldalszámvezérlőket. A kártya megjeleníti az *Ügyfél* entitás mezőit a **Keresés és szűrő** indexében meghatározottak szerint. Az egyes kártyákon belüli mezők sorrendjét a rendszer választja ki.

> [!NOTE]
> Ha nem látja a csempéket, amikor a Vevők lehetőséget választja **, a rendszergazdának** meg kell határoznia legalább egy kereshető attribútumot [a](search-filter-index.md) Keresés &szűrő indexben **.**

:::image type="content" source="media/customers-page-result-tiles-B2C.png" alt-text="Az ügyfelek oldal az eredménycsempéket mutatja.":::

Válasszon az alábbi műveletek közül:
- [Ügyféladatok megtekintése](#view-customer-details)
- [A keresési &szűrési index](search-filter-index.md) kezelése (csak rendszergazdáknak)
- [Ügyfelek szűrése](#filter-customers)
- **Kártyák** kibontása vagy **kártyák** összecsukása az ügyfélcsempén megjelenő információk kibontásához vagy összecsukásához
- **Rendezés egy adott attribútum szerint**
- [Ügyfelek keresése](#search-for-customers)

  > [!NOTE]
  > A keresés és szűrés használatához a rendszergazdának konfigurálnia kell a kereshető attribútumokat, és meg kell határoznia a szűrhető mezőket a keresési &szűrő index használatával.

## <a name="search-for-customers"></a>Ügyfelek keresése

Keressen ügyfeleket egy név vagy más attribútum megadásával az Ügyfelek **keresése mezőben**. A kereshető attribútumokat a rendszergazda határozza meg, és az egyesített *Ügyfél* entitásból származnak.

> [!NOTE]
> **A karakterlánc** az egyetlen adattípus, amely szerepel a keresésben. Használja a **Vevők oldal Ügyfelek** keresése mezőjében az ügyfelek kereséséhez.

## <a name="filter-customers"></a>Ügyfelek szűrése

Szűrje az ügyfeleket a *Vevő* entitás mezők alapján. A szűrhető mezőket a rendszergazda határozza meg.

1. Az Ügyfelek **lapon válassza a** Szűrők **megjelenítése lehetőséget**. Megjelenik a Szűrő panel.

1. Jelölje be a jelölőnégyzetet azon attribútumok mellett, amelyek alapján az ügyfeleket szűrni szeretné.

1. Távolítsa el az összes szűrőt a **Szűrők** törlése lehetőség kiválasztásával, vagy törölje a jelet a kijelölt attribútum melletti jelölőnégyzetből.

1. Válassza a Szűrők **elrejtése lehetőséget** a szűrőpanel bezárásához.

1. A szűrőeredmények szegmensként [való](segments.md) mentéséhez válassza a Szűrők mentése szegmensként **lehetőséget**.
   1. Adja meg a szegmens nevét.
   1. Válassza a Mentés **lehetőséget** a szegmens mentéséhez.
   1. Válassza ki, hogy most futtatja-e a szegmenst az Aktiválás **vagy a Későbbi** futtatás **lehetőség kiválasztásával**.

## <a name="view-customer-details"></a>Ügyféladatok megtekintése

**Az Ügyfelek** lapon válasszon ki egy vevői csempét a kiválasztott vevő részleteinek megtekintéséhez.

:::image type="content" source="media/customers-details-B2C.png" alt-text="Ügyféladatok oldal.":::

Az ügyféladatok a következőket tartalmazza:

**Az Ügyfélprofil csempe** az egyesített Ügyfél *entitás különböző értékeit jeleníti meg*. Ha egy mezőnek nincs értéke a kiválasztott vevői profilhoz, akkor a címmező kivételével nem jelenik meg. A mozaik szakaszokra van felosztva:

- Az első szakasz a mezők előre megadott halmazát, majd a keresés és szűrőindex részét képezi. Az összes címhez kapcsolódó mező egyetlen sorba van egyesítve, amely akkor is megjelenik, ha a profil nem tartalmaz címadatokat.
- **Az ügyfél** kapcsolattartói az üzleti fiókok környezetében jelennek meg. Minden kapcsolattartó megjelenik a saját mezőivel. Az üres mezők rejtettek.
- **A további mezők** a kiválasztott vevő fennmaradó mezőit jelenítik meg, az azonosítók kivételével.
- **Az azonosítók** az összes azonosítót a megfelelő entitásnév alatt sorolják fel. A mezőket szemantikája alapján azonosítóként azonosítják.

**A tevékenység idővonala** akkor jeleníti meg az adatokat, ha konfigurálta [a tevékenységeket](activities.md). Az idővonal nézet időrendi sorrendben rendezi a kijelölt ügyfél tevékenységeit, kezdve a legújabb tevékenységgel.

**Elemzések**:

- **A mértékek** azt mutatják, hogy konfigurálta-e [az ügyfélattribútum-mértékeket](measures.md). Magukban foglalják az egyéni ügyfelek szintjén az ügyfelekhez számított fő teljesítménymutatókat.

- **A potenciális érdeklődési körök, a potenciális márkák** akkor jelennek meg, ha márka- vagy érdeklődési affinitás gazdagítását [konfigurálta](enrichment-microsoft.md). A kiválasztott ügyfélprofilhoz hasonló profillal épülő potenciális érdeklődési okat és feltételeket képvisel.

Az Ügyfelek **oldalra való visszatéréshez válassza a** Vissza az ügyfelekhez **lehetőséget**.

## <a name="next-steps"></a>További lépések

[Vegyen fel további adatforrásokat](data-sources.md), [gyarapítsa az egységes profilokat](enrichment-hub.md), vagy [hozzon létre szegmenseket](segments.md) a más alkalmazásokban egységesített ügyfélprofilokkal való munkához.

[!INCLUDE [footer-include](includes/footer-banner.md)]
