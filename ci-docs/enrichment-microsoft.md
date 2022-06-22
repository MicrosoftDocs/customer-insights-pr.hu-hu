---
title: Ügyfélprofilok gazdagítása a Microsoft márkáinak és érdeklődési körére vonatkozó adatokkal
description: A Microsoft saját tulajdonú adataival affinitásokkal és elérés megoszlása gazdagíthatja ügyféladatait.
ms.date: 03/02/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: kishorem-MS
ms.author: kishorem
manager: shellyha
searchScope:
- ci-enrichments
- ci-enrichment-wizard
- customerInsights
ms.openlocfilehash: 61262980cafdcd130430e200e466ce7da6cc4d07
ms.sourcegitcommit: 27c5473eecd851263e60b2b6c96f6c0a99d68acb
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/13/2022
ms.locfileid: "8953768"
---
# <a name="enrich-customer-profiles-with-affinities-and-share-of-voice-preview"></a>Ügyfélprofilok gazdagítása affinitásokkal és elérés megoszlása (előzetes verzió)

A Microsoft saját tulajdonú adataival márkaaffinomságokkal, érdeklődési körökkel és elérés megoszlása (SoV) gazdagíthatja ügyféladatait. Ezek az affinitások és soV-k az ügyfelekhez hasonló demográfiai jellemzőkkel rendelkező emberek adatain alapulnak. Ezek az információk segítenek abban, hogy jobban megértse és szegmentálja ügyfeleit az affinitásaik vagy az adott márkákhoz és érdeklődési körökhöz való SoV-juk alapján.

## <a name="how-we-determine-affinities-and-sov"></a>Hogyan határozzuk meg az affinitásokat és a SoV-t?

A Microsoft online keresési adatait arra használjuk, hogy különböző demográfiai szegmensekben (életkor, nem vagy hely szerint meghatározva) különböző demográfiai szegmensekben (életkor, nem vagy hely alapján meghatározva) márkákhoz és érdeklődési körökhöz tartozó affinitásokat és soV-t találjunk. A márka vagy érdeklődési kör online keresési volumene képezi az affinitás vagy az SoV meghatározásának alapját. Mindazonáltal mindegyik más perspektívát biztosít az ügyfelek megértéséhez.

- Az affinitás a demográfiai szegmensek közötti összehasonlítás. Ezekkel az információkkal azonosíthatja azokat a demográfiai szegmenseket, amelyek más szegmensekhez képest a legnagyobb affinitással rendelkeznek egy adott márkához vagy érdeklődési körhöz.

- Elérés megoszlása a kiválasztott márkák vagy érdeklődési körök összehasonlító eleme. Ezeket az információkat arra használhatja, hogy azonosítsa, melyik márka vagy érdeklődési kör rendelkezik a legnagyobb hangaránnyal egy adott demográfiai szegmensben, összehasonlítva az Ön által kiválasztott más márkákkal vagy érdeklődési körökkel.

## <a name="affinity-level-and-score"></a>Affinitás szintje és pontszám

Minden bővített ügyfélprofilon két kapcsolódó értéket biztosítunk: affinitás szintje és affinitás értéke. Ezek az értékek segítenek annak meghatározásában, hogy milyen erős az affinitás profil demográfiai szegmensében a márkához vagy érdeklődési körhöz az egyéb demográfiai szegmensekkel összehasonlítva.

Az *Affinitás szintje* négy szintből áll, és egy 100 pontos skálán számítja ki a rendszer az *affinitási pontszámot*, amely hozzárendeli az affintiási szinteket.

|Affinitás szintje |Affinitási pontszám  |
|---------|---------|
|Nagyon magas     | 85-100       |
|Magas     | 70-84        |
|Közepes     | 35-69        |
|Alacsony     | 1-34        |

Az affinitás méréséhez használt részletességtől függően használhatja az affinitás szintjét vagy a pontszámot is. Pontosabban szabályozható az affinitási pontszám.

## <a name="share-of-voice-sov"></a>Elérés megoszlása (SoV)

A SoV-t 100 pontos skálán számítjuk ki. Az összes márkára vagy érdeklődési körre kiterjedő teljes SoV minden gazdag ügyfélprofilhoz 100-at tesz ki. Az affinitásokkal ellentétben a SoV az Ön által kiválasztott márkákhoz és érdeklődési körökhöz viszonyítva van. Például a "Microsoft" SoV-értékei eltérőek lehetnek, ha a kiválasztott márkák ("Microsoft", "GitHub") és ("Microsoft", "LinkedIn") helyett.

## <a name="supported-countriesregions"></a>Támogatott országok/régiók

Jelenleg a következő ország-/régió lehetőségeket támogatjuk: Ausztrália, Kanada (angol), Franciaország, Németország, Egyesült Királyság vagy Egyesült Államok (angol).

## <a name="configure-the-enrichment"></a>Bővítés konfigurálása

1. Menjen a z **Adatok** > **Bővítés** menübe, és válassza a **Felfedezés** lapot.

   - A márkaaffinitások és az SoV-gazdagítás konfigurálásához válassza az Adatok **gazdagítása lehetőséget** a **Márkák** csempén.

   - A kamataffinitások és az SoV-gazdagítás konfigurálásához válassza az Adatok **gazdagítása lehetőséget** az **Érdeklődési körök** csempén.

   > [!div class="mx-imgBorder"]
   > ![Márkák és érdeklődési mozaikok.](media/BrandsInterest-tile-Hub.png "Márkák és érdeklődési mozaikok")

1. Tekintse át az áttekintést, majd válassza a Tovább **lehetőséget**.

1. Az ország vagy régió módosításához válassza a Módosítás **lehetőséget** az Ország/régió **mellett**. **Az Ország/régió beállításai** panelen válasszon ki egy támogatott országot/régiót [...](#supported-countriesregions), majd válassza az Alkalmaz **lehetőséget**.

   > [!NOTE]
   > Saját márkájának kiválasztásakor a rendszer a kiválasztott ország vagy régió alapján tesz javaslatokat. Egy iparág kiválasztása esetén a kiválasztott ország vagy régió alapján megkapja a leginkább releváns márkákat és érdeklődési köröket.

1. Válasszon legfeljebb öt márkát vagy érdeklődési kört az alábbi lehetőségek egyikének vagy mindkettőnek a használatával:

   - **Iparág**: válassza ki saját iparágát a legördülő listából, majd válasszon a csúcsmárkákból vagy érdeklődési körökből ezt az iparágat illetően.
   - **Válassza ki a sajátját**: Adjon meg egy, a szervezet számára releváns márkát vagy érdeklődési kört, majd válasszon a megfelelő javaslatok közül. Ha a keresett márkát vagy érdeklődési kört nem sorolja fel a rendszer, küldjön visszajelzést a **Javaslat** hivatkozás segítségével.

1. Válassza a Tovább **lehetőséget**, tekintse át az alapértelmezett gazdagítási beállításokat, és szükség szerint frissítse őket.

   :::image type="content" source="media/affinity-enrichment-preferences.png" alt-text="Képernyőkép a bővítési beállítások ablakáról.":::

1. Válassza a **Következő** lehetőséget.

1. Válassza ki az **Ügyfél adatkészlet**, és válassza ki azt a profilt vagy szegmenst, amelyet a Microsofttól származó adatokkal szeretne gazdagítani. Az *Ügyfél* entitás gazdagítja az összes ügyfélprofilt, míg egy szegmens csak az adott szegmensben található ügyfélprofilokat gazdagítja.

1. Válassza a **Következő** lehetőséget.

1. Leképezheti a mezőket az egységes ügyfélentitásból a Microsoft adataira.

   > [!NOTE]
   > Legalább a születési dátum vagy a nem attribútumok szükségesek. Ország/régió és legalább város (és állam/tartomány) vagy irányítószám szükséges. Javasoljuk, hogy a születési dátum az adatbetöltés során legyen DateTime típusúra konvertálva. Másik lehetőségként sztring lehet [ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html) "yyyy-MM-ddd" vagy "yyyy-MM-ddTHH:mm:ss" formátumban.

1. A mező leképezésének befejezéséhez válassza a **Következő** lehetőséget.

1. Adjon nevet a bővítésnek. A **Kimeneti entitás neve** automatikusan ki lesz választva.

   :::image type="content" source="media/enrichment-interests-summary.png" alt-text="Az érdeklődési kör áttekintése és elnevezési oldal.":::

1. Válassza a **Bővítés mentése** lehetőséget, miután áttekintette a lehetőségeit.

1. Válassza a Futtatás **lehetőséget** a gazdagítási folyamat elindításához, vagy a közel lehetőséget a **Bővítések** lapra való visszatéréshez.

   A profilok bővítésénél minden olyan ügyfélprofilt bővítünk, amelynél adatokat kapunk a kiválasztott márkákhoz és érdeklődésekhez, tartalmazva a profilokat, amelyek nincsenek benne a kiválasztott országban vagy régióban. Ha például Németországot választotta, akkor bővítjük az Egyesült Államokban található profilokat, ha rendelkezésre állnak adatok az Egyesült Államokban a kiválasztott márkákra és érdeklődésre.

## <a name="enrichment-results"></a>Bővítési eredmények

[!INCLUDE [enrichment-results](includes/enrichment-results.md)]

:::image type="content" source="media/my-enrichments.png" alt-text="Az eredmények előnézete a bővítési folyamat futtatása után.":::

Az eredmények közé tartozik **az Affinitás szintje** vagy **a elérés megoszlása** diagramok.

A gazdagításokból létrehozott entitások az **Adatentitások** Gazdagítási **csoportjában** > **vannak felsorolva**. A márkákkal kapcsolatos bővített adatok a BrandAffinityFromMicrosoft **és** a **BrandShareOfVoiceFromMicrosoft** entitásokhoz kerülnek. Az érdekeltségekre vonatkozó adatok a **InterestAffinityFromMicrosoft** és **a InterestShareOfVoiceFromMicrosoft** entitásokban találhatók.

## <a name="see-enrichment-data-on-the-customer-card"></a>A bővítési adatok megtekintése az ügyfélkártyán

Márka és érdeklődés SoV az egyes ügyfélkártyákon is megtekinthető. Nyissa meg az **Ügyfelek** lehetőséget, és válassza ki az ügyfél profilját. Az ügyfélkártyán diagramokat talál a márkához vagy érdeklődési körhöz tartozó SoV-hez az adott ügyfél demográfiai profiljában szereplő személyek alapján.

:::image type="content" source="media/enrichment-customer-card.png" alt-text="Bővített adatokkal rendelkező ügyfél-kártya.":::

## <a name="next-steps"></a>További lépések

[!INCLUDE [next-steps-enrichment](includes/next-steps-enrichment.md)]


[!INCLUDE [footer-include](includes/footer-banner.md)]
