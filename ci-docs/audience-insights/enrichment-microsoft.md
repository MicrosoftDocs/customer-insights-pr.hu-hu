---
title: Ügyfélprofilok bővítése a Microsoftból származó adatokkal
description: A Microsoft saját adataival gazdagítsa ügyféladatait affinitásokkal és elérés megoszlása.
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
ms.openlocfilehash: 12704ec46832e9463e6115db6c4df64e72bf4f97
ms.sourcegitcommit: bb1f9e96023490ab340c114f54200ab4dd48da78
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/02/2022
ms.locfileid: "8372676"
---
# <a name="enrich-customer-profiles-with-affinities-and-share-of-voice-preview"></a>Ügyfélprofilok gazdagítása affinitásokkal és elérés megoszlása (előzetes verzió)

Használja a Microsoft saját adatait, hogy gazdagítsa ügyféladatait márka affinitásokkal, érdeklődési affinitásokkal és elérés megoszlása (SoV). Ezek az affinitások és a SoV az ügyfelekhez hasonló demográfiai adatokon alapulnak. Ezek az információk segítenek abban, hogy jobban megértse és szegmentálja ügyfeleit az adott márkákhoz és érdekekhez való affinitásuk vagy SoV alapján.

A célközönség-információkban lépjen az **Adatok** > **Bővítés** a [bővítések konfigurálásához és megtekintéséhez](enrichment-hub.md).

A márkaaffinitások és a SoV-gazdagodás konfigurálásához lépjen a **Felfedezés** fülre, és válassza **az Adatok** gazdagítása lehetőséget a **Márkák** csempén.

Az érdeklődési affinitások és a SoV-gazdagodás konfigurálásához lépjen a **Felfedezés** fülre, és válassza **az Adatok** gazdagítása lehetőséget az **Érdeklődések** csempén.

   > [!div class="mx-imgBorder"]
   > ![Márkák és érdeklődési mozaikok.](media/BrandsInterest-tile-Hub.png "Márkák és érdeklődési mozaikok")

## <a name="how-we-determine-affinities-and-sov"></a>Hogyan határozzuk meg az affinitásokat és a SoV-t

A Microsoft online keresési adatait arra használjuk, hogy megtaláljuk a márkák és érdeklődési körök affinitását és soV-ját a különböző demográfiai szegmensekben (életkor, nem vagy hely szerint meghatározva). Egy márka vagy érdeklődés online keresési volumene képezi az affinitás vagy a SoV meghatározásának alapját. Mindegyik más perspektívát biztosít az ügyfelek megértéséhez.

- Az affinitás a demográfiai szegmensek közötti összehasonlító. Ezeket az információkat olyan demográfiai szegmensek azonosítására használhatja, amelyek más szegmensekhez képest a legnagyobb affinitással rendelkeznek egy adott márkához vagy érdeklődéshez.

- Elérés megoszlása a kiválasztott márkák vagy érdekek összehasonlító része. Ezeket az információkat felhasználhatja annak azonosítására, hogy melyik márka vagy érdeklődés rendelkezik a legmagasabb hangmegosztással egy adott demográfiai szegmensben, összehasonlítva az Ön által kiválasztott más márkákkal vagy érdeklődési körökkel.

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

A SoV-t egy 100 pontos skálán számítjuk ki. A teljes SoV az összes márkában vagy érdeklődési körben minden gazdagított ügyfélprofil esetében 100-ra emelkedik. Az affinitásokkal ellentétben a SoV az Ön által kiválasztott márkákhoz és érdekekhez viszonyítva van. A "Microsoft" SoV-értékei például eltérőek lehetnek, ha a kiválasztott márkák ("Microsoft", "GitHub") és ("Microsoft", "LinkedIn") szemben vannak.

## <a name="supported-countriesregions"></a>Támogatott országok/régiók

Jelenleg a következő ország-/régió lehetőségeket támogatjuk: Ausztrália, Kanada (angol), Franciaország, Németország, Egyesült Királyság vagy Egyesült Államok (angol).

Ország vagy régió kiválasztásához nyissa meg a **Márkák bővítése** vagy **Érdeklődés bővítése** és válassza a **Változtat** lehetőséget az **Ország/Régió** mellett. Az **Ország/régió beállításai** ablaktáblában válasszon egy beállítást, és válassza az **Alkalmaz** lehetőséget.

### <a name="implications-related-to-country-selection"></a>Az országválasztással kapcsolatos következmények

- Saját [márkájának kiválasztásakor](#define-your-brands-or-interests) a rendszer a kiválasztott ország vagy régió alapján tesz javaslatokat.

- Egy [iparág kiválasztása](#define-your-brands-or-interests) esetén a kiválasztott ország vagy régió alapján megkapja a leginkább releváns márkákat és érdeklődési köröket.

- A [profilok bővítésénél](#refresh-enrichment) minden olyan ügyfélprofilt bővítünk, amelynél adatokat kapunk a kiválasztott márkákhoz és érdeklődésekhez, tartalmazva a profilokat, amelyek nincsenek benne a kiválasztott országban vagy régióban. Ha például Németországot választotta, akkor bővítjük az Egyesült Államokban található profilokat, ha rendelkezésre állnak adatok az Egyesült Államokban a kiválasztott márkákra és érdeklődésre.

## <a name="configure-enrichment"></a>A bővítés konfigurálása

Az interaktív élmény végig segít Önnek a bővítések konfigurálásában. 

### <a name="define-your-brands-or-interests"></a>Márkák vagy érdeklődési körök megadása

Válasszon legfeljebb öt márkát vagy érdeklődési kört az alábbi lehetőségek egyikének vagy mindkettőnek a használatával:

- **Iparág**: válassza ki saját iparágát a legördülő listából, majd válasszon a csúcsmárkákból vagy érdeklődési körökből ezt az iparágat illetően.
- **Válassza ki a sajátját**: Adjon meg egy, a szervezet számára releváns márkát vagy érdeklődési kört, majd válasszon a megfelelő javaslatok közül. Ha a keresett márkát vagy érdeklődési kört nem sorolja fel a rendszer, küldjön visszajelzést a **Javaslat** hivatkozás segítségével.

### <a name="review-enrichment-preferences"></a>Bővítési beállítások áttekintése

Tekintse át az alapértelmezett bővítési beállításokat, és szükség szerint frissítse azokat.

:::image type="content" source="media/affinity-enrichment-preferences.png" alt-text="Képernyőkép a bővítési beállítások ablakáról.":::

### <a name="select-entity-to-enrich"></a>Entitás kiválasztása bővítéshez

Válassza a Bővített entitás **lehetőséget**, és válassza ki a Microsoft adataival gazdagítani kívánt adatkészlet. Kiválaszthatja a Vevő entitást az összes ügyfélprofil gazdagítására, vagy kiválaszthat egy szegmens entitást, amely csak az adott szegmensben található vevőprofilokat gazdagítja.

### <a name="map-your-fields"></a>Mezők megfeleltetése

A egyesített ügyfélentitás mezőinek leképezésével meghatározhatja, hogy a rendszer az ügyféladatok gyarapítására melyik demográfiai szegmenst használja. Ország/régió leképezése, és legalább a születési dátum vagy nem attribútumát. Ezenkívül le kell képeznie legalább egy várost (és államot/tartományt) vagy irányítószámot. Válassza a **Szerkesztés** lehetőséget a mezők leképezésének definiálásához, és válassza az **Alkalmazás** lehetőséget, amikor elkészült. Válassza a **Mentés** lehetőséget a mezők leképezésének végrehajtásához.

A következő formátumok és értékek támogatottak (az értékek nem különböztetik meg a kis- és nagybetűket):

- **Születési dátum**: Azt ajánljuk, hogy az adatok betöltése során a születési dátumot a rendszer datetime típusúra alakítsa. Másik lehetőségként sztring lehet [ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html) "yyyy-MM-ddd" vagy "yyyy-MM-ddTHH:mm:ss" formátumban.
- **Nem**: férfi, nő, ismeretlen.
- **Irányítószám**: Ötjegyű irányítószámok az Egyesült Államok számára, standard irányítószám mindenhol máshol.
- **Város**: A város neve angolul.
- **Állam/megye**: Két betűs rövidítés az Egyesült Államok és Kanada esetében. Két- vagy három betűs rövidítés Ausztrália esetében. Franciaország, Németország és az Egyesült Királyság esetében nem alkalmazható.
- **Ország/régió**:

  - USA: Amerikai Egyesült Államok, Egyesült Államok, USA, US, Amerika
  - CA: Kanada, CA
  - GB: Egyesült Királyság, UK, Nagy-Britannia, GB, Nagy-Britannia és Észak-Írország Egyesült Királysága, Nagy-Britannia Egyesült Királysága
  - AU: Ausztrália, AU, Ausztrália, Ausztrál Nemzetközösség
  - FR: Franciaország, Francia Köztársaság
  - DE: Németország, német, Deutschland, Allemagne, DE, Német Szövetségi Köztársaság, Német Köztársaság

## <a name="review-and-name-the-enrichment"></a>A bővítés áttekintése és elnevezése

Végül áttekintheti az információkat, és nevet adhat a bővítésnek.

:::image type="content" source="media/enrichment-interests-summary.png" alt-text="Az érdeklődési kör áttekintése és elnevezési oldal.":::

## <a name="refresh-enrichment"></a>A bővítés frissítése

Futtassa a bővítést a márkák, érdeklődési körök konfigurálása és a mezők demográfiai adatokra vonatkozó leképezése után. A folyamat megkezdéséhez válassza a márka vagy az érdeklődési kör konfigurációja lapon a **Futtatás** lehetőséget. Emellett a rendszer automatikusan is futtathatja a dúsítást egy ütemezett frissítés részeként.

Az ügyféladatok méretétől függően előfordulhat, hogy a bővítés futtatása néhány percig is eltarthat.

[!INCLUDE [progress-details-include](../includes/progress-details-pane.md)]

## <a name="enrichment-results"></a>Bővítési eredmények

A bővítési folyamat futtatása után lépjen a **Saját bővítések** pontra, és nézze át a bővített ügyfelek teljes számát és a márkák vagy érdeklődési körök lebontását a bővített ügyfelek profiljaiban.

:::image type="content" source="media/my-enrichments.png" alt-text="Az eredmények előnézete a bővítési folyamat futtatása után.":::

Talál egy diagramot, amely tartalmazza a gazdagított ügyfélprofilok számát az idő múlásával és a gazdagított entitások előnézetét. Tekintse át a bővített adatokat a Továbbiak megtekintése **az Affinitási szint** vagy **elérés megoszlása** **diagramok között.** A márkák gazdagított adatai a **BrandAffinityFromMicrosoft** és **a BrandShareOfVoiceFromMicrosoft** szervezetekhez vezetnek. Az érdeklődési körökre vonatkozó adatok a **InterestAffinityFromMicrosoft** és **a InterestShareOfVoiceFromMicrosoft** entitások. Ezeket az entitásokat a **Bővítés** csoportban is megtekintheti az **Adatok** > **Entitások** helyen.

## <a name="see-enrichment-data-on-the-customer-card"></a>A bővítési adatok megtekintése az ügyfélkártyán

A márka és az érdeklődés SoV az egyes ügyfélkártyákon is megtekinthető. Nyissa meg az **Ügyfelek** lehetőséget, és válassza ki az ügyfél profilját. Az ügyfélkártyán a márka vagy az érdeklődés SoV diagramjait találja az adott ügyfél demográfiai profiljában szereplő személyek alapján.

:::image type="content" source="media/enrichment-customer-card.png" alt-text="Bővített adatokkal rendelkező ügyfél-kártya.":::

## <a name="next-steps"></a>További lépések

[!INCLUDE [next-steps-enrichment](../includes/next-steps-enrichment.md)]


[!INCLUDE[footer-include](../includes/footer-banner.md)]
