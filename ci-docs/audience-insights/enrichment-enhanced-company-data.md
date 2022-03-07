---
title: Vállalati adatok javítása
description: Gazdagítsa és normalizálja a vállalati adatokat a Microsoft modelljeivel.
ms.date: 01/19/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: kishorem-ms
ms.author: kishorem
manager: shellyha
ms.openlocfilehash: 7a576621c71b925bd1563827aca10cad4ef9b4eb
ms.sourcegitcommit: e7cdf36a78a2b1dd2850183224d39c8dde46b26f
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/16/2022
ms.locfileid: "8229406"
---
# <a name="enrichment-of-company-profiles-with-enhanced-company-data"></a>Cégprofilok gazdagítása továbbfejlesztett vállalati adatokkal

A Microsoft modelljeinek és lefordított vállalati adatainak használatával javíthatja, kiegészítheti és szabványosíthatja vállalati profiljait. A jobb pontosság és betekintés érdekében a [Common Data Model formátumot](/common-data-model/schema/core/applicationcommon/account) fogjuk használni.

## <a name="how-we-enhance-company-data"></a>Hogyan javítjuk a vállalati adatokat

Modellünk kétlépcsős folyamaton megy keresztül a vállalati profil javítása érdekében. Először is normalizálja a vállalat nevét. Például a *Microsoft Corp-ot* kijavítják és szabványossá teszik a Microsoft Corporation *számára*. Megpróbál egyezést találni a Microsoft összeállított vállalati adataiban. Ha egyezést találunk, a cég profilját az összeállított cégadatokból származó információkkal gazdagítjuk, beleértve a cég nevét is.


### <a name="example"></a>Példa

Előfordulhat, hogy a vállalat adatai nem szabványosított formátumot követnek, és helyesírási hibákat tartalmaznak. A modell megpróbálja kijavítani ezeket a problémákat, és konzisztens információkat létrehozni.

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

A továbbfejlesztett adatoknak van néhány korlátja. Az alábbi listában szereplő elemeket a modell nem támogatja.

1.  Erősítse meg a vállalat személyazonosságát. Nem ellenőrizzük, hogy a bemenet egy meglévő szervezet-e, vagy hogy egy vállalat a kimenetet használja-e szabványos neveként.
2.  Átfogóan lefedi a vállalatokat világszerte. A Microsoft összeállított vállalati adatai globális lefedettséggel vannak, de a legtöbb lefedettséget Ausztráliában, Kanadában, az Egyesült Királyságban és az Egyesült Államokban kínálják.
3.  A vállalati címek szabványosítása globálisan. Jelenleg támogatjuk a címek szabványosítását ezekben az országokban vagy régiókban: Ausztrália, Kanada, Franciaország, Németország, Olaszország, Japán, Egyesült Királyság és az Egyesült Államok.
4.  Garantálja az adatok pontosságát vagy frissességét. Mivel az üzleti információk gyakran megváltoznak, nem tudjuk garantálni, hogy a megadott továbbfejlesztett vállalati adatok mindig pontosak vagy naprakészek.

## <a name="configure-the-enrichment"></a>Bővítés konfigurálása

1. Lépjen az **Adatok** > **Bővítés** pontra.

1. Válassza a Bővített vállalati adatok **csempén az** Adatok **gazdagítása lehetőséget**.

   :::image type="content" source="media/enhanced-company-data-tile.png" alt-text="Gazdagító csempe a vállalati adatok gazdagító központjában.":::

1. Válassza ki az **Ügyféladatok beállítva** lehetőséget, majd a bővíteni kívánt címeket tartalmazó entitást. Az *Ügyfél* entitás kiválasztásával az összes ügyfélprofilban lévő címeket bővítheti, de kijelölhet olyan szegmensentitást is, amely csak az adott szegmensben található ügyfélprofilok címeit bővíti.

1. Válassza ki, hogy a vállalati profilok mely típusú mezőit használja a Microsoft lefordított vállalati adataival való egyeztetéshez. Ez a beállítás hatással van a következő lépésben elérhető leképezési mezőkre.

1.  A vállalati mezők leképezése az egyesített ügyfél entitásból. Minél több kulcsfontosságú azonosítót és mezőt térképez fel, annál nagyobb a valószínűsége a magasabb egyezési aránynak.

    :::image type="content" source="media/enhanced-company-data-mapping.png" alt-text="Adatleképezési lépés a vállalati gazdagodás konfigurálásakor.":::

1. A mező leképezésének befejezéséhez válassza a **Következő** lehetőséget.

1. Adja meg a bővítés és a kimeneti entitás nevét.

1. Válassza a **Bővítés mentése** lehetőséget, miután áttekintette a lehetőségeit.

## <a name="enrichment-results"></a>Bővítési eredmények

A bővítési folyamat megkezdéséhez válassza a **Futtatás** parancsot a parancssorból. Azt is engedélyezheti, hogy a rendszer a bővítést automatikusan egy [ütemezett frissítés](system.md#schedule-tab) részeként futtassa. A feldolgozási idő az ügyféladatok mennyiségétől függ.

A bővítési folyamat befejeződése után áttekintheti az újonnan bővített ügyfelek profiljainak adatait a **Saját bővítések** alatt. Emellett megtalálhatja az utolsó frissítés időpontját és a bővített profilok számát is.

A bővített adatok **mintáját a Gazdagított vevők előnézeti** csempéjén tekintheti meg. Válassza a Továbbiak megtekintése lehetőséget **, és válassza az Adatok** lapot az **egyes bővített profil részletes nézetének eléréséhez.**

### <a name="overview-card"></a>Áttekintő kártya

Az áttekintő kártya a gazdagodás lefedettségének részleteit mutatja. 

* **Feldolgozott és módosított** vállalatok: A sikeresen gazdagított ügyfélvállalati profilok száma.

* **Feldolgozott és nem módosított** vállalatok: Az ügyfélvállalati profilok száma, amelyeket felismertek, de nem változtattak meg. Ez általában akkor fordul elő, ha a bemeneti adatok érvényesek, és a gazdagodás nem javítható.

* **Nem feldolgozott és nem módosított** vállalatok: A fel nem ismert ügyfélvállalati profilok száma. Ez általában olyan bemeneti adatok esetében történik, amelyek érvénytelenek vagy a gazdagítás nem támogatja őket.

## <a name="next-steps"></a>További lépések

[!INCLUDE [next-steps-enrichment](../includes/next-steps-enrichment.md)]

[!INCLUDE[footer-include](../includes/footer-banner.md)]
