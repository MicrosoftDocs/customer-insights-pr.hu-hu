---
title: Az ügyfelélprofilok bővítése a Microsoft Graph alkalmazással
description: A Microsoft Graph tulajdonosi adataival bővítheti az ügyféladatokat amárkák iránti hűséggel és érdeklődési körökkel.
ms.date: 09/28/2020
ms.reviewer: kishorem
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: 4f93a2337815f76b98185ecb3755e08443031748
ms.sourcegitcommit: cf9b78559ca189d4c2086a66c879098d56c0377a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/03/2020
ms.locfileid: "4405990"
---
# <a name="enrich-customer-profiles-with-brand-and-interest-affinities-preview"></a>Az ügyfelek profiljainak bővítése márkahűséggel és érdeklődési körökkel (előzetes verzió)

A Microsoft Graph tulajdonosi adataival bővítheti az ügyféladatokat amárkák iránti hűséggel és érdeklődési körökkel. Ezeket az affinitásokat az ügyfelekihez hasonló demográfiai adatokkal rendelkező emberek adatai alapján határozzák meg. Ez az információ segíti az ügyfelek jobb megértését és szegmentálásukban a márkahűségük és érdeklődésük alapján.

A célközönség-információkban lépjen az **Adatok** > **Bővítés** a [bővítések konfigurálásához és megtekintéséhez](enrichment-hub.md).

A márkaaffinitások bővítésének konfigurálásához nyissa meg a **Felfedezés** lapot, és válassza a **Saját adatok bővítése** elemet a **Márkák** csempén.

Az érdeklődésikör-affinitások bővítésének konfigurálásához nyissa meg a **Felfedezés** lapot, és válassza a **Saját adatok bővítése** elemet az **Érdeklődési körök** csempén.

   > [!div class="mx-imgBorder"]
   > ![Márkák és érdeklődési mozaikok](media/BrandsInterest-tile-Hub.png "Márkák és érdeklődés mozaikok")

## <a name="about-microsoft-graph"></a>A Microsoft Graph szolgáltatás

Az online keresési adatok segítségével a Microsoft Graph segítségével megkeresheti a márkák és érdeklődési körök iránti hűséget a különböző demográfiai szegmensekben (kor, nem vagy hely szerint meghatározva). A márka vagy az érdeklődési kör online keresési mennyisége határozza meg, hogy egy demografikus szegmens mekkora hűséggel rendelkezik a többi szegmenssel összehasonlítva az adott márkához vagy érdeklődési körhöz.

[További információk a Microsoft Graph szolgáltatásról](https://docs.microsoft.com/graph/overview).

## <a name="affinity-score-and-confidence"></a>Affinitási pontszám és konfidencia

Az **affinitás pontszám** értékét egy 100 pontos skálán számítja ki a rendszer, a 100 értéket az a szegmens kapja, amely a legmagasabb affinitással rendelkezik a márka vagy a érdeklődés szempontjából.

Az **affinitási konfidencia** értékét egy 100 pontos skálán is kiszámítja a rendszer. Jelzi a rendszer konfidenciaszintjét, hogy a szegmensnek a márkához vagy a kamathoz hűsége van. A konfidencia szintje a szegmens méretén és a szegmens granularitásán alapul. A szegmens méretét az adott szegmenshez tartozó adatok mennyisége határozza meg. A szegmensek részletességét az határozza meg, hogy a profilban hány attribútum (kor, nem, hely) áll rendelkezésre.

Nem normalizáljuk a pontszámokat az adatkészletéhez. Következésképpen előfordulhat, hogy nem látja az adatkészlet összes lehetséges affinitási értékét. Előfordulhat például, hogy az adatokban nincs 100 affinitás pontszámú ügyfélprofil. Ez akkor lehetséges, ha a demográfiai szegmensben nem szerepelnek olyan ügyfelek, akik egy adott márkához vagy érdeklődéshez 100 pontszámmal rendelkeznek.

> [!TIP]
> Ha az affinitás pontszámok segítségével [hoz létre szegmenseket](segments.md), tekintse át az affinitási pontszámok eloszlását az adatkészlethez, mielőtt döntene a megfelelő pontszámküszöbről. Egy 10-es affinitási pontszám például egy adatkészletben jelentősnek tekinthető, ahol egy adott márkához vagy érdeklődéshez a legmagasabb affinitási pontszám csak 25.

## <a name="supported-countriesregions"></a>Támogatott országok/régiók

Jelenleg a következő ország-/régió lehetőségeket támogatjuk: Ausztrália, Kanada (angol), Franciaország, Németország, Egyesült Királyság vagy Egyesült Államok (angol).

Ország kiválasztásához nyissa meg a **Márkák bővítése** vagy az **Érdeklődés bővítése** lehetőséget és válassza az **Módosítás** lehetőséget az **Ország/régió** mellett. Az **Ország/régió beállításai** ablaktáblában válasszon egy beállítást, és válassza az **Alkalmaz** lehetőséget.

### <a name="implications-related-to-country-selection"></a>Az országválasztással kapcsolatos következmények

- A [saját márkák kiválasztásakor](#define-your-brands-or-interests) a kiválasztott országra/régióra vonatkozó javaslatokat adunk meg.

- Az [iparág kiválasztásakor](#define-your-brands-or-interests) a kiválasztott ország/régió alapján azonosítjuk a legrelevánsabb márkákat és érdeklődéseket.

- Ha [a mezők leképezése](#map-your-fields) során az ország/régió mező nincs leképezve, a Microsoft Graph adatait a kiválasztott országból/régióból használjuk az ügyfélprofilok bővítéséhez. Emellett a kijelölés segítségével bővítheti az ügyfelek profilját, amelyhez nem állnak rendelkezésre ország/régió adatok.

- A [profilok bővítése](#refresh-enrichment) során minden olyan felhasználói profilt bővítünk, amelyhez a kiválasztott márkák és érdeklődési körök számára Microsoft Graph adatok állnak rendelkezésre, beleértve a kiválasztott országban/régióban nem szereplő profilokat is. Ha például Németországot jelölte ki, a rendszer az Egyesült Államokban található profilokat bővíti, ha a Microsoft Graph adatai elérhetők a kiválasztott márkákhoz és érdeklődési körökhöz az Egyesült Államokban.

## <a name="configure-enrichment"></a>A bővítés konfigurálása

A márkák vagy érdeklődési körök bővítésének beállítása két lépésből áll:

### <a name="define-your-brands-or-interests"></a>Márkák vagy érdeklődési körök megadása

Válasszon az alábbi lehetőségek közül:

- **Iparág**: A rendszer azonosítja az iparághoz kapcsolódó legnépszerűbb márkákat vagy érdeklődési köröket, és bővíti az ügyfelek adatait velük.
- **Válassza ki a sajátját**: Legfeljebb öt elemet jelölhet ki a szervezetéhez leginkább kapcsolódó márkák vagy érdeklődési körök listájából.

Ha márkát vagy érdeklődési kört szeretne hozzáadni, írja be a beviteli területen a megfelelő kifejezések alapján javaslatokat kapjon. Ha a keresett márkát vagy érdeklődési kört nem sorolja fel a rendszer, küldjön visszajelzést a **Javaslat** hivatkozás segítségével.

### <a name="map-your-fields"></a>Mezők megfeleltetése

Az egyesített ügyfélentitás mezőit feleltesse meg legalább két attribútummal a használni kívánt demográfiai szegmenshez az ügyféladatok bővítéséhez. Válassza a **Szerkesztés** lehetőséget a mezők leképezésének definiálásához, és válassza az **Alkalmazás** lehetőséget, amikor elkészült. Válassza a **Mentés** lehetőséget a mezők leképezésének végrehajtásához.

A következő formátumok és értékek támogatottak, az értékek nem különböztetik meg a kis- és nagybetűket:

- **Születési dátum**: Azt ajánljuk, hogy az adatok betöltése során a születési dátumot a rendszer datetime típusúra alakítsa. Másik lehetőségként [ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html) formátumú "éééé-hh-nn" vagy "éééé-hh-NNTóó:pp:mp" karakterláncot is meg lehet adni.
- **Nem**: férfi, nő, ismeretlen
- **Irányítószám**: Öt számjegyből álló ZIP-kód az Egyesült Államokban, szabványos irányítószám mindenhol máshol
- **Város**: A város neve angolul
- **Állam/megye**: Két betűs rövidítés az Egyesült Államok és Kanada esetében. Két vagy három betű rövidítés Ausztrália esetében. Franciaország, Németország és az Egyesült Királyság esetében nem alkalmazható.
- **Ország/régió**:

  - USA: Amerikai Egyesült Államok, Egyesült Államok, USA, US, Amerika
  - CA: Kanada, CA
  - GB: Egyesült Királyság, UK, Nagy-Britannia, GB, Nagy-Britannia és Észak-Írország Egyesült Királysága, Nagy-Britannia Egyesült Királysága
  - AU: Ausztrália, AU, Ausztrál nemzetközösség
  - FR: Franciaország, Francia Köztársaság
  - DE: Németország, német, Deutschland, Allemagne, DE, Német Szövetségi Köztársaság, Német Köztársaság

## <a name="refresh-enrichment"></a>A bővítés frissítése

Futtassa a bővítést a márkák, érdeklődési körök konfigurálása és a mezők demográfiai adatokra vonatkozó leképezése után. A folyamat megkezdéséhez válassza a márka vagy az érdeklődési kör konfigurációja lapon a **Futtatás** lehetőséget. Emellett a rendszer automatikusan is futtathatja a dúsítást egy ütemezett frissítés részeként.
Az ügyféladatok méretétől függően előfordulhat, hogy a bővítés futtatása néhány percig is eltarthat.

> [!TIP]
> A feladatokhoz/folyamatokhoz [hatféle állapot](system.md#status-types) tartozhat. Emellett a legtöbb folyamat [más alsóbb szintű folyamatoktól is függ](system.md#refresh-policies). Kiválaszthatja egy folyamat állapotát, és megtekintheti a hozzá tartozó teljes feladat folyamatának részleteit. Miután kiválasztotta a **Részletek megtekintése** lehetőséget a feladat egyik feladatához, további információk jelennek meg: feldolgozási idő, legutóbbi feldolgozás dátuma, és a feladathoz társított összes hiba és figyelmeztetés.

## <a name="enrichment-results"></a>Bővítési eredmények

A bővítési folyamat futtatása után lépjen a **Saját bővítések** pontra, és nézze át a bővített ügyfelek teljes számát és a márkák vagy érdeklődési körök lebontását a bővített ügyfelek profiljaiban.

:::image type="content" source="media/my-enrichments.png" alt-text="Az eredmények előnézete a bővítési folyamat futtatása után":::

A bővített adatok áttekintéséhez jelölje be a **Bővített adatok megtekintése** lehetőséget a diagramban. A márkák bővített adatai a **BrandAffinityFromMicrosoft** entitásba kerülnek. Az érdeklődési körök adatai az **InterestAffinityFromMicrosoft** entitásba kerülnek. Ezeket az entitásokat a **Bővítés** csoportban is megtekintheti az **Adatok** > **Entitások** helyen.

## <a name="see-enrichment-data-on-the-customer-card"></a>A bővítési adatok megtekintése az ügyfélkártyán

A márka és a érdeklődés affinitásokat az ügyfélkártyákon is meg lehet tekinteni. Nyissa meg az **Ügyfelek** lehetőséget, és válassza ki az ügyfél profilját. Az ügyfélkártyán megkeresheti a márkákra vagy az érdeklődési körökre vonatkozó diagramokat, amelyek szerint az adott ügyfél demográfiai profiljához tartozó személyek affinitással rendelkeznek.

:::image type="content" source="media/enrichment-customer-card.png" alt-text="Bővített adatokkal rendelkező ügyfél-kártya":::

## <a name="next-steps"></a>Következő lépések

Építsen a bővített ügyféladatokra. Hozzon létre [Szegmenseket](segments.md), [Mértékeket](measures.md) , sőt [Exportálhatja az adatokat](export-destinations.md), hogy személyre szabott élményeket tudjon nyújtani az ügyfeleknek.
