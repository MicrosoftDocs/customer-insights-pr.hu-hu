---
title: A vállalati adatok fejlesztése
description: Gazdagítsa és normalizálja a vállalati adatokat a Microsoft modelljeivel.
ms.date: 06/10/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: kishorem-ms
ms.author: kishorem
manager: shellyha
ms.openlocfilehash: 4247d59806468907d93fc7848231ec5a2985580e
ms.sourcegitcommit: 27c5473eecd851263e60b2b6c96f6c0a99d68acb
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/13/2022
ms.locfileid: "8953952"
---
# <a name="enrichment-of-company-profiles-with-enhanced-company-data"></a>Vállalati profilok gazdagítása továbbfejlesztett vállalati adatokkal

A Microsoft modelljeivel és lefordított vállalati adataival javíthatja, kiegészítheti és szabványosíthatja vállalati profiljait. A jobb pontosság és betekintés érdekében a [Common Data Model formátumot](/common-data-model/schema/core/applicationcommon/account) fogjuk használni.

Az adatforrásokra [vonatkozó vállalati adatokat is](data-sources-enrichment.md) javíthatja, hogy javítsa az egyezés pontosságát az adategyesítési folyamatban.

Az Egyesült Államokban működő állami vállalatok számára olyan információk állnak rendelkezésre, mint a bevétel, a részvénykijelző, az ipar és egyebek.  

## <a name="how-we-enhance-company-data"></a>Hogyan fejlesztjük a vállalati adatokat?

Modellünk kétlépcsős folyamaton megy keresztül a vállalati profil javítása érdekében. Először is normalizálja a vállalat nevét. Például a *Microsoft Corp-ot* kijavítjuk és szabványosítjuk a *Microsoft Corporation-re*. Megpróbál egyezést találni a Microsoft által összeállított vállalati adatokban. Ha talál egyezést, a vállalati profilt az összeállított vállalati adatokból származó információkkal bővítjük, beleértve a vállalat nevét is.

### <a name="example"></a>Példa

Előfordulhat, hogy a vállalati adatok nem követik a szabványosított formátumot, és helyesírási hibákat tartalmaznak. A modell megpróbálja kijavítani ezeket a problémákat, és konzisztens információkat hoz létre.

```Input
Microsft
```

```Output
- AccountName: Microsoft Corporation
- MainPhoneNumber: 8006427676
- Website: https://www.microsoft.com/
- Street1: One Microsoft Way
- City: Redmond
- StateOrProvince: Washington
- County: King
- ZipOrPostalCode: 98052
- CountryOrRegion: United States
```

## <a name="limitations"></a>Korlátozások

A modell nem:

- Erősítse meg a vállalat személyazonosságát. Nem ellenőrizzük, hogy a bemenet meglévő szervezet-e, vagy hogy egy vállalat a kimenetet használja-e szabványos neveként.
- Átfogóan fedje le a vállalatokat világszerte. A Microsoft összeállított vállalati adatai globális lefedettséggel rendelkeznek, de a legtöbb lefedettséget Ausztráliában, Kanadában, az Egyesült Királyságban és az Egyesült Államokban kínálják.
- A vállalati címek globális szabványosítása. Jelenleg ezekben az országokban vagy régiókban támogatjuk a címek szabványosítását: Ausztrália, Kanada, Franciaország, Németország, Olaszország, Japán, Egyesült Királyság és az Egyesült Államok.
- Garantálja az adatok pontosságát vagy frissességét. Mivel az üzleti információk gyakran változnak, nem tudjuk garantálni, hogy a megadott továbbfejlesztett vállalati adatok mindig pontosak vagy naprakészek.

## <a name="configure-the-enrichment"></a>Bővítés konfigurálása

1. Menjen a z **Adatok** > **Bővítés** menübe, és válassza a **Felfedezés** lapot.

1. Válassza az Adatok **gazdagítása lehetőséget** a **Továbbfejlesztett vállalati adatok** csempén.

   :::image type="content" source="media/enhanced-company-data-tile.png" alt-text="Gazdagítási csempe a vállalati adatok gazdagítási központjában.":::

1. Tekintse át az áttekintést, majd válassza a Tovább **lehetőséget**.

1. Válassza ki az **Ügyfél adatkészlet**, és válassza ki a gazdagítani kívánt profilt vagy szegmenst. Az *Ügyfél* entitás gazdagítja az összes ügyfélprofilt, míg egy szegmens csak az adott szegmensben található ügyfélprofilokat gazdagítja.

1. Válassza ki, hogy a vállalati profilok mely típusú mezőit használja a Microsoft lefordított vállalati adataival való egyeztetéshez. Ez a beállítás hatással van a következő lépésben elérhető leképezési mezőkre.

1. Válassza a **Következő** lehetőséget.

1. Leképezheti a vállalati mezőket a Microsoft vállalati adataira. A nagyobb egyezési pontosság érdekében adjon hozzá további mezőket.

    :::image type="content" source="media/enhanced-company-data-mapping.png" alt-text="Adatleképezési lépés a vállalati gazdagítás konfigurálásakor.":::

1. A mező leképezésének befejezéséhez válassza a **Következő** lehetőséget.

1. **Adja meg a gazdagítás nevét** és a **Kimenet entitást**.

1. Válassza a **Bővítés mentése** lehetőséget, miután áttekintette a lehetőségeit.

1. Válassza a Futtatás **lehetőséget** a gazdagítási folyamat elindításához, vagy a közel lehetőséget a **Bővítések** lapra való visszatéréshez.

## <a name="enrichment-results"></a>Bővítési eredmények

[!INCLUDE [enrichment-results](includes/enrichment-results.md)]

### <a name="overview-card"></a>Áttekintő kártya

Az **Ügyfelek változásai áttekintés** csempe a gazdagítás lefedettségének részleteit jeleníti meg

- **Feldolgozott és megváltozott** vállalatok: A sikeresen gazdagított ügyfélvállalati profilok száma.
- **Feldolgozott és nem módosított** vállalatok: Az elismert, de nem módosított ügyfélvállalati profilok száma. Ez általában akkor fordul elő, ha a bemeneti adatok érvényesek, és a gazdagítással nem javíthatók.
- **Nem feldolgozott és nem módosított** vállalatok: A nem elismert ügyfélvállalati profilok száma. Ez általában olyan bemeneti adatok esetében fordul elő, amelyek érvénytelenek vagy a gazdagítás nem támogatja őket.

## <a name="next-steps"></a>További lépések

[!INCLUDE [next-steps-enrichment](includes/next-steps-enrichment.md)]

[!INCLUDE [footer-include](includes/footer-banner.md)]
