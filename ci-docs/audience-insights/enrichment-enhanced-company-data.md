---
title: Vállalati adatok javítása
description: Gazdagítsa és normalizálja a vállalati adatokat a Microsoft modelljeivel.
ms.date: 11/15/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: kishorem-ms
ms.author: kishorem
manager: shellyha
ms.openlocfilehash: d11700c87f31cedc40d32b201251d8a9e2e2c312
ms.sourcegitcommit: dfc4843cc78857f1e3ca49d7b938e3ba77969169
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/15/2021
ms.locfileid: "7813921"
---
# <a name="enrichment-of-company-profiles-with-enhanced-company-data"></a>Vállalati profilok gazdagítása továbbfejlesztett vállalati adatokkal

A Microsoft modelljei és a lefordított vállalati adatok segítségével javíthatja, kiegészítheti és szabványosíthatja vállalati profiljait. A common data model formátumot fogjuk használni a [jobb pontosság és betekintés](/common-data-model/schema/core/applicationcommon/account) érdekében.

## <a name="how-we-enhance-company-data"></a>Hogyan javítjuk a vállalati adatokat

Modellünk kétlépcsős folyamaton megy keresztül a vállalati profil javítása érdekében. Először is normalizálja a cég nevét. Például a *Microsoft* Corp-ot kijavítják és szabványosítják a *Microsoft Corporation számára*. Megpróbálja megtalálni a mérkőzést a Microsoft összeállított vállalati adataiban. Ha egyezést találunk, a cég profilját az összeállított vállalati adatainkból származó információkkal gazdagítjuk, beleértve a vállalat nevét is.


### <a name="example"></a>Példa

Előfordulhat, hogy a vállalati adatok nem követik a szabványosított formátumot, és helyesírási hibákat tartalmaznak. A modell megpróbálja kijavítani ezeket a problémákat, és következetes információkat hoz létre.

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

1.  Erősítse meg a vállalat személyazonosságát. Nem ellenőrizzük, hogy a bemenet meglévő szervezet-e, vagy hogy egy vállalat a kimenetet használja-e szabványos névként.
2.  Átfogóan lefedi a vállalatokat világszerte. A Microsoft összeállított vállalati adatai globális lefedettséggel rendelkeznek, de a legtöbb lefedettséget Ausztráliában, Kanadában, az Egyesült Királyságban és az Egyesült Államokban kínálják.
3.  Szabványosítsa a vállalati címeket világszerte. Jelenleg támogatjuk a címek szabványosítását ezekben az országokban vagy régiókban: Ausztrália, Kanada, Franciaország, Németország, Olaszország, Japán, Egyesült Királyság és az Egyesült Államok.
4.  Garantálja az adatok pontosságát vagy frissességét. Mivel az üzleti információk gyakran változnak, nem tudjuk garantálni, hogy a megadott továbbfejlesztett vállalati adatok mindig pontosak vagy naprakészek.

## <a name="configure-the-enrichment"></a>Bővítés konfigurálása

1. Lépjen az **Adatok** > **Bővítés** pontra.

1. Válassza **az Adatok gazdagítása lehetőséget a** **Továbbfejlesztett vállalati** adatlapon.

   :::image type="content" source="media/enhanced-company-data-tile.png" alt-text="Dúsítási csempe a vállalati adatok gazdagító központjában.":::

1. Válassza ki az **Ügyféladatok beállítva** lehetőséget, majd a bővíteni kívánt címeket tartalmazó entitást. Az *Ügyfél* entitás kiválasztásával az összes ügyfélprofilban lévő címeket bővítheti, de kijelölhet olyan szegmensentitást is, amely csak az adott szegmensben található ügyfélprofilok címeit bővíti.

1. Válassza ki, hogy a vállalati profilokból mely típusú mezőket kell használni a Microsoft által összeállított vállalati adatokkal való egyeztetéshez. Ez a beállítás hatással van a következő lépésben elérhető leképezési mezőkre.

1.  Az egyesített vevői entitás vállalati mezőinek leképezése. Minél több kulcsazonosítót és mezőt térképez fel, annál nagyobb a valószínűsége a magasabb egyezési aránynak.

    :::image type="content" source="media/enhanced-company-data-mapping.png" alt-text="Adatleképezési lépés a vállalat gazdagításának konfigurálásakor.":::

1. A mező leképezésének befejezéséhez válassza a **Következő** lehetőséget.

1. Adja meg a bővítés és a kimeneti entitás nevét.

1. Válassza a **Bővítés mentése** lehetőséget, miután áttekintette a lehetőségeit.

## <a name="enrichment-results"></a>Bővítési eredmények

A bővítési folyamat megkezdéséhez válassza a **Futtatás** parancsot a parancssorból. Azt is engedélyezheti, hogy a rendszer a bővítést automatikusan egy [ütemezett frissítés](system.md#schedule-tab) részeként futtassa. A feldolgozási idő az ügyféladatok mennyiségétől függ.

A bővítési folyamat befejeződése után áttekintheti az újonnan bővített ügyfelek profiljainak adatait a **Saját bővítések** alatt. Emellett megtalálhatja az utolsó frissítés időpontját és a bővített profilok számát is.

Az egyes bővített profilok részletes nézetét a **Bővített adatok megtekintése** lehetőségre kattintva érheti el.

## <a name="next-steps"></a>További lépések

[!INCLUDE [next-steps-enrichment](../includes/next-steps-enrichment.md)]

[!INCLUDE[footer-include](../includes/footer-banner.md)]