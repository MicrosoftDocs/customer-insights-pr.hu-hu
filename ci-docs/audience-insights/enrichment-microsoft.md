---
title: Ügyfélprofilok bővítése a Microsoftból származó adatokkal
description: Használja a Microsoft tulajdonát képező adatokat az ügyféladatok márkahűséggel és érdeklődéssel való bővítésre.
ms.date: 04/09/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: kishorem-MS
ms.author: kishorem
manager: shellyha
ms.openlocfilehash: 6f19033236190547f68d2b91ec6b32074bf7912a
ms.sourcegitcommit: aaa275c60c0c77c88196277b266a91d653f8f759
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/14/2021
ms.locfileid: "5896605"
---
# <a name="enrich-customer-profiles-with-brand-and-interest-affinities-preview"></a>Az ügyfelek profiljainak bővítése márkahűséggel és érdeklődési körökkel (előzetes verzió)

Használja a Microsoft tulajdonát képező adatokat az ügyféladatok márkahűséggel és érdeklődéssel való bővítésre. Ezeket az affinitásokat az ügyfelekihez hasonló demográfiai adatokkal rendelkező emberek adatai alapján határozzák meg. Ez az információ segíti az ügyfelek jobb megértését és szegmentálásukban a márkahűségük és érdeklődésük alapján.

A célközönség-információkban lépjen az **Adatok** > **Bővítés** a [bővítések konfigurálásához és megtekintéséhez](enrichment-hub.md).

A márkaaffinitások bővítésének konfigurálásához nyissa meg a **Felfedezés** lapot, és válassza a **Saját adatok bővítése** elemet a **Márkák** csempén.

Az érdeklődésikör-affinitások bővítésének konfigurálásához nyissa meg a **Felfedezés** lapot, és válassza a **Saját adatok bővítése** elemet az **Érdeklődési körök** csempén.

   > [!div class="mx-imgBorder"]
   > ![Márkák és érdeklődési mozaikok](media/BrandsInterest-tile-Hub.png "Márkák és érdeklődés mozaikok")

## <a name="how-we-determine-affinities"></a>Hogyan határozzuk meg a márkahűséget

A Microsoft online keresési adatait használjuk fel különböző demográfiai szegmensek (kor, gender vagy hely szerint meghatározva) megkerséséhez, például márkahűség és érdeklődési kör. A márka vagy az érdeklődési kör online keresési mennyisége határozza meg, hogy egy demografikus szegmens mekkora hűséggel rendelkezik a többi szegmenssel összehasonlítva az adott márkához vagy érdeklődési körhöz. márkahűség vagy érdeklődés.

## <a name="affinity-level-and-score"></a>Affinitás szintje és pontszám

Minden bővített ügyfélprofilon két kapcsolódó értéket biztosítunk – affinitás szintje és affinitás pontszáma. Ezek az értékek segítenek annak meghatározásában, hogy milyen erős az affinitás profil demográfiai szegmensében a márkához vagy érdeklődési körhöz az egyéb demográfiai szegmensekkel összehasonlítva.

Az *Affinitás szintje* négy szintből áll, és egy 100 pontos skálán számítja ki a rendszer az *affinitási pontszámot*, amely hozzárendeli az affintiási szinteket.


|Affinitás szintje |Affinitási pontszám  |
|---------|---------|
|Nagyon magas     | 85-100       |
|Magas     | 70-84        |
|Közepes     | 35-69        |
|Alacsony     | 1-34        |

Az affinitás méréséhez használt részletességtől függően használhatja az affinitás szintjét vagy a pontszámot is. Pontosabban szabályozható az affinitási pontszám.

## <a name="supported-countriesregions"></a>Támogatott országok/régiók

Jelenleg a következő ország-/régió lehetőségeket támogatjuk: Ausztrália, Kanada (angol), Franciaország, Németország, Egyesült Királyság vagy Egyesült Államok (angol).

Ország kiválasztásához nyissa meg a **Márkák bővítése** vagy az **Érdeklődés bővítése** lehetőséget és válassza az **Módosítás** lehetőséget az **Ország/régió** mellett. Az **Ország/régió beállításai** ablaktáblában válasszon egy beállítást, és válassza az **Alkalmaz** lehetőséget.

### <a name="implications-related-to-country-selection"></a>Az országválasztással kapcsolatos következmények

- Saját [márkájának kiválasztásakor](#define-your-brands-or-interests) a rendszer a kiválasztott ország vagy régió alapján tesz javaslatokat.

- Egy [iparág kiválasztása](#define-your-brands-or-interests) esetén a kiválasztott ország vagy régió alapján megkapja a leginkább releváns márkákat és érdeklődési köröket.

- A [profilok bővítésekor](#refresh-enrichment) minden ügyfélprofilt bővítünk, amelyhez a kiválasztott márkák és érdeklődési körök kapcsán adatokat kapunk. A nem a kijelölt országban vagy régióban található profilokat is. Ha például Németországot választotta, akkor bővítjük az Egyesült Államokban található profilokat, ha rendelkezésre állnak adatok az Egyesült Államokban a kiválasztott márkákra és érdeklődésre.

## <a name="configure-enrichment"></a>A bővítés konfigurálása

Az interaktív élmény végig segít Önnek a bővítések konfigurálásában. 

### <a name="define-your-brands-or-interests"></a>Márkák vagy érdeklődési körök megadása

Válasszon az alábbi lehetőségek közül:

- **Iparág**: A rendszer azonosítja az iparághoz kapcsolódó legnépszerűbb márkákat vagy érdeklődési köröket, és bővíti az ügyfelek adatait velük.
- **Válassza ki a sajátját**: Legfeljebb öt elemet jelölhet ki a szervezetéhez leginkább kapcsolódó márkák vagy érdeklődési körök listájából.

Ha márkát vagy érdeklődési kört szeretne hozzáadni, írja be a beviteli területen a megfelelő kifejezések alapján javaslatokat kapjon. Ha a keresett márkát vagy érdeklődési kört nem sorolja fel a rendszer, küldjön visszajelzést a **Javaslat** hivatkozás segítségével.

### <a name="review-enrichment-preferences"></a>Bővítési beállítások áttekintése

Tekintse át az alapértelmezett bővítési beállításokat, és szükség szerint frissítse azokat.

:::image type="content" source="media/affinity-enrichment-preferences.png" alt-text="Képernyőkép a bővítési beállítások ablakáról.":::

### <a name="select-entity-to-enrich"></a>Entitás kiválasztása bővítéshez

Válassza a **Bővített entitás** lehetőséget, és válassza a Microsoft vállalati adataival gyarapítani kívánt entitásokat. Kiválaszthatja a Vevő entitást az összes ügyfélprofil gazdagítására, vagy kiválaszthat egy szegmens entitást, amely csak az adott szegmensben található vevőprofilokat gazdagítja.

### <a name="map-your-fields"></a>Mezők megfeleltetése

A egyesített ügyfélentitás mezőinek leképezésével meghatározhatja, hogy a rendszer az ügyféladatok gyarapítására melyik demográfiai szegmenst használja. Ország/régió leképezése, és legalább a születési dátum vagy nem attribútumát. Ezenkívül le kell képeznie legalább egy várost (és államot/tartományt) vagy irányítószámot. Válassza a **Szerkesztés** lehetőséget a mezők leképezésének definiálásához, és válassza az **Alkalmazás** lehetőséget, amikor elkészült. Válassza a **Mentés** lehetőséget a mezők leképezésének végrehajtásához.

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

## <a name="review-and-name-the-enrichment"></a>A bővítés áttekintése és elnevezése

Végül áttekintheti az információkat, és nevet adhat a bővítésnek.

:::image type="content" source="media/enrichment-interests-summary.png" alt-text="Az érdeklődési kör áttekintése és elnevezési oldal.":::

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


[!INCLUDE[footer-include](../includes/footer-banner.md)]
