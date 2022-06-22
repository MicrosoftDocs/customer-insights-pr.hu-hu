---
title: Címjavítás gazdagítása (videót tartalmaz)
description: A Microsoft modelljeivel rendelkező ügyfélprofilok címinformációinak bővítése és normalizálása.
ms.date: 06/10/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: kishorem-ms
ms.author: kishorem
manager: shellyha
searchScope:
- ci-data-sources-enrichment
- ci-data-sources-enrichment-details
- ci-enrichments
- ci-enrichment-wizard
- customerInsights
ms.openlocfilehash: f6279b9bb721d99d66f73e8dc839a92f1ad90140
ms.sourcegitcommit: 27c5473eecd851263e60b2b6c96f6c0a99d68acb
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/13/2022
ms.locfileid: "8953814"
---
# <a name="enrichment-of-customer-profiles-with-enhanced-addresses"></a>Ügyfélprofilok bővítése továbbfejlesztett címekkel

Az adatokban szereplő címek strukturálatlanok, hiányosak vagy helytelenek lehetnek. A Microsoft modelljeivel normalizálhatja és bővítheti [Common Data Model formátumba](/common-data-model/schema/core/applicationcommon/address) a címeket, amelyek így pontosabbak lehetnek.

Az adatforrások [címeit is](data-sources-enrichment.md) bővítheti, hogy javítsa az egyezési pontosságot az adategyesítési folyamatban. 

## <a name="how-we-enhance-addresses"></a>Hogyan történik a címek továbbfejlesztése?

A modell két lépést használ a címek továbbfejlesztéséhez. Először elemezi a címet, azonosítja az összetevőit, és strukturált formátumba alakítja őket. Ezután az AI-t használjuk a címben lévő értékek javítására, befejezésére és szabványosítására.

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWNewo]

### <a name="example"></a>Példa

Előfordulhat, hogy a címadatok nem szabványos formátumúak, és helyesírási hibákat tartalmaznak. A modell ezeket a problémákat ki tudja javítani, és egységes címeket hozhat létre az egységes ügyfélprofilokban.

```Input
4567 w main stret californa missouri 54321 us
```

```Output
- Street1: 4567 W Main St
- City: California
- StateOrProvince: MO
- ZipOrPostalCode: 54321
- CountryOrRegion: United States of America

- Address: 4567 W Main St, California, MO, 54321, United States of America
```

### <a name="limitations"></a>Korlátozások

A továbbfejlesztett címek csak a betöltött címadatokban már meglévő értékekkel működnek. A modell nem:

1. ellenőrzi, hogy a cím érvényes-e;
2. ellenőrzi, hogy az értékek (például az irányítószám vagy az utcanév) érvényesek-e;
3. módosítja a fel nem ismert értékeket.

A modell gépi tanuláson alapuló technikákat alkalmaz a címek továbbfejlesztéséhez. Mint minden gépi tanuláson alapuló modell esetében, a 100%-os pontosság nem garantált.

## <a name="supported-countries-or-regions"></a>Támogatott országok és régiók

Jelenleg a következő országokban és régiókban támogatjuk a címek bővítését:

- Ausztrália
- Kanada
- Franciaország
- Németország
- Olaszország
- Japán
- Egyesült Királyság
- Egyesült Államok

## <a name="configure-the-enrichment"></a>Bővítés konfigurálása

1. Menjen a z **Adatok** > **Bővítés** menübe, és válassza a **Felfedezés** lapot.

1. A **Továbbfejlesztett címek** csempén válassza **Az adataim bővítése** lehetőséget.

   :::image type="content" source="media/enhanced-addresses-tile.png" alt-text="A Továbbfejlesztett címek csempe képernyőképe.":::

1. Tekintse át az áttekintést, majd válassza a Tovább **lehetőséget**.

1. Válassza ki az **Ügyfél adatkészlet**, és válassza ki a gazdagítani kívánt profilt vagy szegmenst. Az *Ügyfél* entitás gazdagítja az összes ügyfélprofilt, míg egy szegmens csak az adott szegmensben található ügyfélprofilokat gazdagítja.

1. Adja meg, hogyan történjen az adatkészletben lévő címek formázása. Ha az adatokban lévő címek egy mezőt használnak, válassza az **Egyattribútumos cím** lehetőséget. Ha az adatokban lévő címek több adatmezőt használnak, válassza a **Többattribútumos cím** lehetőséget.

1. Válassza a Tovább **lehetőséget**, és leképezi a címmezőket az egyesített vevői entitásból.

    :::image type="content" source="media/enhanced-address-mapping.png" alt-text="Továbbfejlesztett címmező-leképezési oldal.":::

   > [!NOTE]
   > Az ország/régió kötelező mind az egy-attribútumos, mind a több attribútumos címekben. Az érvényes vagy támogatott ország/régió értékeket nem tartalmazó címek nem kerülnek bővítésre.

1. A mező leképezésének befejezéséhez válassza a **Következő** lehetőséget.

1. **Adja meg a gazdagítás nevét** és a **Kimenet entitást**.

1. Válassza a **Bővítés mentése** lehetőséget, miután áttekintette a lehetőségeit.

## <a name="enrichment-results"></a>Bővítési eredmények

[!INCLUDE [enrichment-results](includes/enrichment-results.md)]

A **mező** által gazdagított ügyfelek száma részletezést biztosít az egyes bővített mezők lefedettségében.

### <a name="overview-card"></a>Áttekintő kártya

Az **Ügyfelek változásai áttekintő** kártya a gazdagítás lefedettségének részleteit jeleníti meg:

- **Feldolgozott és módosított** címek: A sikeresen bővített címeket tartalmazó ügyfélprofilok száma.
- **Feldolgozott és nem módosított** címek: A felismert, de nem módosított címekkel rendelkező ügyfélprofilok száma. Ez általában akkor fordul elő, ha a bemeneti adatok érvényesek, és a gazdagítással nem javíthatók.
- **Nem feldolgozott és nem módosított** címek: A rendszer által nem felismert címekkel rendelkező profilok száma. Általában olyan bemeneti adatok esetében, amelyek érvénytelenek vagy a gazdagítás nem támogatja őket.

## <a name="next-steps"></a>További lépések

[!INCLUDE [next-steps-enrichment](includes/next-steps-enrichment.md)]

[!INCLUDE [footer-include](includes/footer-banner.md)]
