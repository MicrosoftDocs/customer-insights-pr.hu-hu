---
title: Vállalati adatjavítás
description: Bővítse és normalizálja a vállalati adatokat a Microsoft modelljeivel.
ms.date: 04/22/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: kishorem-ms
ms.author: kishorem
manager: shellyha
ms.openlocfilehash: 6aa38afa7f92b512d19b4967fc1652b5e43ad094
ms.sourcegitcommit: b7dbcd5627c2ebfbcfe65589991c159ba290d377
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/27/2022
ms.locfileid: "8642461"
---
# <a name="enrichment-of-company-profiles-with-enhanced-company-data"></a>A vállalati profilok gazdagítása továbbfejlesztett vállalati adatokkal

A Microsoft modelljeivel és lefordított vállalati adataival javíthatja, kiegészítheti és szabványosíthatja vállalati profiljait. A Common Data Model formátumot [fogjuk használni a](/common-data-model/schema/core/applicationcommon/account) jobb pontosság és betekintés érdekében.

Az adatforrásokra [vonatkozó vállalati adatokat is](data-sources-enrichment.md) javíthatja az adategyesítési folyamat egyezési pontosságának javítása érdekében. 

Az Egyesült Államokban működő állami vállalatok számára olyan információk állnak rendelkezésre, mint a bevétel, a részvényketyegő, az ipar és még sok más.  

## <a name="how-we-enhance-company-data"></a>Hogyan javítjuk a vállalati adatokat

Modellünk kétlépcsős folyamaton megy keresztül, hogy javítsa a vállalati profilt. Először is normalizálja a vállalat nevét. Például a *Microsoft Corp* .-ot kijavítják és szabványosítják a Microsoft Corporation *számára*. Megpróbálja megtalálni az egyezést a Microsoft lefordított vállalati adataiban. Ha egyezést találunk, a cég profilját a összeállított vállalati adatokból származó információkkal gazdagítjuk, beleértve a cég nevét is.


### <a name="example"></a>Példa

Előfordulhat, hogy a vállalati adatok nem szabványosított formátumot követnek, és helyesírási hibákat tartalmaznak. A modell megpróbálja kijavítani ezeket a problémákat, és konzisztens információkat hoz létre.

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

1.  Erősítse meg a vállalat személyazonosságát. Nem ellenőrizzük, hogy a bemenet meglévő szervezet-e, vagy hogy a vállalat a kimenetet használja-e szabványos neveként.
2.  Átfogóan lefedi a vállalatokat világszerte. A Microsoft összeállított vállalati adatai globális lefedettséggel rendelkeznek, de a legtöbb lefedettséget Ausztráliában, Kanadában, az Egyesült Királyságban és az Egyesült Államokban kínálják.
3.  A vállalati címek szabványosítása globális szinten. Jelenleg támogatjuk a címek szabványosítását ezekben az országokban vagy régiókban: Ausztráliában, Kanadában, Franciaországban, Németországban, Olaszországban, Japánban, az Egyesült Királyságban és az Egyesült Államokban.
4.  Garantálja az adatok pontosságát vagy frissességét. Mivel az üzleti információk gyakran változnak, nem tudjuk garantálni, hogy a megadott továbbfejlesztett vállalati adatok mindig pontosak vagy naprakészek.

## <a name="configure-the-enrichment"></a>Bővítés konfigurálása

1. Lépjen az **Adatok** > **Bővítés** pontra.

1. Válassza **az Adatok** bővítése lehetőséget a **Bővített vállalati adatcsempén**.

   :::image type="content" source="media/enhanced-company-data-tile.png" alt-text="Dúsító csempe a vállalati adatok dúsítási központjában.":::

1. Válassza ki az **Ügyféladatok beállítva** lehetőséget, majd a bővíteni kívánt címeket tartalmazó entitást. Az *Ügyfél* entitás kiválasztásával az összes ügyfélprofilban lévő címeket bővítheti, de kijelölhet olyan szegmensentitást is, amely csak az adott szegmensben található ügyfélprofilok címeit bővíti.

1. Válassza ki, hogy a vállalati profilok mely típusú mezőit használja a Microsoft lefordított vállalati adataival való egyeztetéshez. Ez a beállítás hatással van a következő lépésben elérhető leképezési mezőkre.

1.  A vállalat mezőinek leképezése az egyesített vevőegységből. Minél több kulcsazonosítót és mezőt térképez fel, annál nagyobb a valószínűsége a magasabb egyezési aránynak.

    :::image type="content" source="media/enhanced-company-data-mapping.png" alt-text="Adatleképezési lépés a vállalati gazdagodás konfigurálásakor.":::

1. A mező leképezésének befejezéséhez válassza a **Következő** lehetőséget.

1. Adja meg a bővítés és a kimeneti entitás nevét.

1. Válassza a **Bővítés mentése** lehetőséget, miután áttekintette a lehetőségeit.

## <a name="enrichment-results"></a>Bővítési eredmények

A bővítési folyamat megkezdéséhez válassza a **Futtatás** parancsot a parancssorból. Azt is engedélyezheti, hogy a rendszer a bővítést automatikusan egy [ütemezett frissítés](system.md#schedule-tab) részeként futtassa. A feldolgozási idő az ügyféladatok mennyiségétől függ.

A bővítési folyamat befejeződése után áttekintheti az újonnan bővített ügyfelek profiljainak adatait a **Saját bővítések** alatt. Emellett megtalálhatja az utolsó frissítés időpontját és a bővített profilok számát is.

A gazdagított adatok mintáját a Gazdagított ügyfelek előnézeti **csempéjén** tekintheti meg. Válassza **a Továbbiak** megtekintése lehetőséget, és válassza az Adatok **lapot az** egyes bővített profilok részletes nézetének eléréséhez.

### <a name="overview-card"></a>Áttekintő kártya

Az áttekintő kártya a gazdagodás lefedettségének részleteit mutatja. 

* **Feldolgozott és módosított** vállalatok: A sikeresen gazdagodott ügyfélvállalati profilok száma.

* **Feldolgozott és nem módosított** vállalatok: Az elismert, de nem módosított ügyfélvállalati profilok száma. Ez általában akkor fordul elő, ha a bemeneti adatok érvényesek, és a gazdagodás nem javítható.

* **Nem feldolgozott és nem módosított** vállalatok: A fel nem ismert ügyfélvállalati profilok száma. Ez általában olyan bemeneti adatok esetében fordul elő, amelyek érvénytelenek vagy a gazdagodás nem támogatottak.

## <a name="next-steps"></a>További lépések

[!INCLUDE [next-steps-enrichment](includes/next-steps-enrichment.md)]

[!INCLUDE [footer-include](includes/footer-banner.md)]
