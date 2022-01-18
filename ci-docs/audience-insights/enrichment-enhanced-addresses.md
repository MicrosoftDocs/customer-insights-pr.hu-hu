---
title: Címjavítási gazdagodás (videót tartalmaz)
description: A Microsoft modelljeivel rendelkező ügyfélprofilok címinformációinak bővítése és normalizálása.
ms.date: 12/16/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: kishorem-ms
ms.author: kishorem
manager: shellyha
ms.openlocfilehash: afb1a6b4805702697889bb91ca36a96a714cba3d
ms.sourcegitcommit: 9132fdf54070cc551ab878378078e6285852818f
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/18/2021
ms.locfileid: "7934926"
---
# <a name="enrichment-of-customer-profiles-with-enhanced-addresses"></a>Ügyfélprofilok bővítése továbbfejlesztett címekkel

Az adatokban szereplő címek strukturálatlanok, hiányosak vagy helytelenek lehetnek. A Microsoft modelljeivel normalizálhatja és bővítheti [Common Data Model formátumba](/common-data-model/schema/core/applicationcommon/address) a címeket, amelyek így pontosabbak lehetnek.

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

A továbbfejlesztett címek csak a betöltött címadatokban már megtalálható értékekkel működnek. A modell nem: 

1. ellenőrzi, hogy a cím érvényes-e;
2. ellenőrzi, hogy az értékek (például az irányítószám vagy az utcanév) érvényesek-e;
3. módosítja a fel nem ismert értékeket.

A modell gépi tanuláson alapuló technikákat alkalmaz a címek továbbfejlesztéséhez. Bár magas megbízhatósági küszöböt alkalmazunk arra az időre, amikor a modell megváltoztatja a bemeneti értéket, mint minden gépi tanuláson alapuló modell esetében, a 100 százalékos pontosság nem garantált.

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

A címek egy ország/régió értéket tartalmazhatnak. Nem dolgozunk fel nem támogatott országokban és régiókban lévő címeket, illetve olyan címeket, ahol nincs megadva ország vagy régió.

## <a name="configure-the-enrichment"></a>Bővítés konfigurálása

1. Lépjen az **Adatok** > **Bővítés** pontra.

1. A **Továbbfejlesztett címek** csempén válassza **Az adataim bővítése** lehetőséget.

   :::image type="content" source="media/enhanced-addresses-tile.png" alt-text="A Továbbfejlesztett címek csempe képernyőképe.":::

1. Válassza ki az **Ügyféladatok beállítva** lehetőséget, majd a bővíteni kívánt címeket tartalmazó entitást. Az *Ügyfél* entitás kiválasztásával az összes ügyfélprofilban lévő címeket bővítheti, de kijelölhet olyan szegmensentitást is, amely csak az adott szegmensben található ügyfélprofilok címeit bővíti.

1. Adja meg, hogyan történjen az adatkészletben lévő címek formázása. Ha az adatokban lévő címek egy mezőt használnak, válassza az **Egyattribútumos cím** lehetőséget. Ha az adatokban lévő címek több adatmezőt használnak, válassza a **Többattribútumos cím** lehetőséget.

   > [!NOTE]
   > Az ország/régió kötelező mind az egy-attribútumos, mind a több attribútumos címekben. Az érvényes vagy támogatott ország/régió értékeket nem tartalmazó címek nem kerülnek bővítésre.

1.  Képezze le az egyesített ügyfélentitásból származó címmezőket.

    :::image type="content" source="media/enhanced-address-mapping.png" alt-text="Továbbfejlesztett címmező-leképezési oldal.":::

1. A mező leképezésének befejezéséhez válassza a **Következő** lehetőséget.

1. Adja meg a bővítés és a kimeneti entitás nevét.

1. Válassza a **Bővítés mentése** lehetőséget, miután áttekintette a lehetőségeit.

## <a name="enrichment-results"></a>Bővítési eredmények

A bővítési folyamat megkezdéséhez válassza a **Futtatás** parancsot a parancssorból. Azt is engedélyezheti, hogy a rendszer a bővítést automatikusan egy [ütemezett frissítés](system.md#schedule-tab) részeként futtassa. A feldolgozási idő az ügyféladatok mennyiségétől függ.

A bővítési folyamat befejeződése után áttekintheti az újonnan bővített ügyfelek profiljainak adatait a **Saját bővítések** alatt. Emellett megtalálhatja az utolsó frissítés időpontját és a bővített profilok számát is.

Az egyes bővített profilok részletes nézetét a **Bővített adatok megtekintése** lehetőségre kattintva érheti el.

### <a name="overview-card"></a>Áttekintő kártya

Az áttekintő kártya részletesen ismerteti a dúsítás lefedettségét. 

* **Feldolgozott és módosított ügyfelek** : A sikeresen gazdagított ügyfélprofilok száma.

* **Feldolgozott és nem módosított vevők** : A felismert, de nem módosított ügyfélprofilok száma. Ez általában akkor fordul elő, ha a bemeneti adatok érvényesek, és a gazdagítással nem javíthatók.

* **Nem feldolgozott és nem módosított ügyfelek** : A nem felismert profilok száma. Általában olyan bemeneti adatok esetében, amelyek érvénytelenek vagy a gazdagodás által nem támogatottak.

## <a name="next-steps"></a>További lépések

[!INCLUDE [next-steps-enrichment](../includes/next-steps-enrichment.md)]

[!INCLUDE[footer-include](../includes/footer-banner.md)]
