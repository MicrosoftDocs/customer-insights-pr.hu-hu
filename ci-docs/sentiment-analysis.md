---
title: Hangulatelemzés az ügyfelek visszajelzéseihez (előzetes verzió)
description: Ismerje meg, hogyan használhatja a hangulatelemzési modellt az ügyfelek visszajelzésein a Dynamics 365 Customer Insights.
ms.date: 12/23/2021
ms.subservice: audience-insights
ms.reviewer: mhart
ms.topic: conceptual
author: wmelewong
ms.author: wameng
manager: shellyha
ms.openlocfilehash: af1afd3eff8a795a9e199b1c1d411b79dc2841b4
ms.sourcegitcommit: a97d31a647a5d259140a1baaeef8c6ea10b8cbde
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/29/2022
ms.locfileid: "9055539"
---
# <a name="analyze-sentiment-in-customer-feedback-preview"></a>Hangulat elemzése az ügyfelek visszajelzéseiben (előzetes verzió)

Az ügyfelek manapság kiváló minőségű termékeket, szolgáltatásokat és élményeket várnak el. Különösen az ügyfelek, akik megosztják visszajelzéseiket. A szervezetek számára nagy kihívást jelent a növekvő adatmennyiség elemzése anélkül, hogy csökkentenék a pontosságot és a magasabb munkaerőköltségeket. Dynamics 365 Customer Insights hangulatelemzési modellt kínál az ügyfelek visszajelzéseihez, amely lehetővé teszi a szervezetek számára, hogy pontosabban és alacsonyabb költségek mellett elemezzék adataikat.

A hangulatelemzés lehetővé teszi az ügyfelek hangulatának szintetizálását és az üzleti szempontoknak a fejlesztés lehetőségként való azonosítását. Ez a Customer Insights funkció segít megérteni, hogy mi működik jól, és mivel kell foglalkoznia. Összpontosítson az üzleti élet legrelevánsabb és leghatásosabb területeire, hogy javítsa az ügyfelek élményét. Végső soron segíthet olyan üzleti műveletek ösztönzésében, amelyek olyan élményeket tesznek lehetővé, amelyek magas ügyfél-elégedettséget és lojalitást eredményeznek.

## <a name="overview"></a>Áttekintés

A hangulatelemzési funkció ügyfél-azonosítónként két származtatott betekintést hoz létre. A hangulati pontszám (-5-től 5-ig) és az alkalmazható üzleti szempontok (üzleti területek) listája együttesen segít jobban megérteni az ügyfelek visszajelzéseit. 

Ezek az információk a következő eredmények elérésében segíthetnek: 
- Áttekintést kaphat az ügyfelek márkával vagy szervezettel kapcsolatos hangulatáról
- Azonosítsd a negatív hangulattal rendelkező ügyfeleket, hogy a kampányaidra és az aktivitásaidra összpontosíts, és optimalizálj a magasabb hozam érdekében  
- Azonosítsa az üzleti szempontokat az ügyfelek által kiemelt problémákkal  
- Szegmentálja az ügyfeleket a hangulatuk alapján, hogy személyre szabott kampányokat futtasson célzott értékesítési, marketing- és támogatási erőfeszítésekkel
- Optimalizálja az üzleti műveleteket az ügyfelek által említett aggodalomra okot adó területek vagy lehetőségek kezelésével
- Ismerje fel a jól teljesítő üzleti szempontokat, és jutalmazza a boldog ügyfeleket hűség- és promóciós programokkal

Annak biztosítása érdekében, hogy megbízhasson a modellek eredményeiben, átlátható információkat nyújtunk arról, hogy a modellek hogyan hoznak döntéseket. Megjelenik azoknak a szavaknak a listája, amelyek befolyásolták a modellek azon döntését, hogy egy adott hangulati pontszámot vagy üzleti szempontot rendelnek a visszajelzési megjegyzésekhez.  

Két **természetes nyelvi feldolgozási (NLP) modellt** használunk: Az első minden visszajelzési megjegyzéshez hangulati pontszámot rendel. A második modell minden visszajelzést az összes vonatkozó üzleti szemponthoz társít. A modelleket a közösségi média, a kiskereskedelem, az éttermek, a fogyasztási cikkek és az autóipar forrásaiból származó nyilvános adatok alapján képzik.    
  
A modellnek a visszajelzési adatokhoz társítandó előre meghatározott üzleti szempontjai a következők:
-   Fiókkezelés
-   Pénztár és fizetés
-   Ügyfélszolgálat
-   Bolti átvétel
-   Csomagolás szállítása és visszakeresése
-   Előrendelés
-   Ár
-   Adatvédelem és biztonság
-   Promóciók és jutalmak
-   Nyugta és garancia
-   Adatcsere visszaküldése és visszavonása
-   Teljesítési pontosság
-   Webhely/alkalmazás minősége

> [!NOTE]
> Jelenleg csak az angol ügyfelek visszajelzéseivel kapcsolatos hangulatelemzést támogatjuk. A jövőben több nyelvet is támogatni fogunk. Ha más nyelveken is feltölti a visszajelzést, a modell továbbra is eredményeket ad vissza. Ezek az eredmények azonban nem lesznek pontosak. 

## <a name="prerequisites"></a>Előfeltételek

A hangulatelemzés olyan szöveges visszajelzési adatokon alapul, amelyek átmentek az [adategyesítési folyamaton](data-unification.md). Javasoljuk, hogy [a visszajelzési adatentitásokat előzetesen szemantikai típusú tevékenységentitásokként](map-entities.md#select-primary-key-and-semantic-type-for-attributes) (Visszajelzés típusa) konfigurálja. 

Hangulatelemzési modell konfigurálásához legalább [közreműködő engedélyre](permissions.md) van szüksége.

A Customer Insights akár 10 millió visszajelzési rekordot is képes feldolgozni egyetlen modellfuttatáshoz. A modell legfeljebb 128 szó képes elemezni a visszacsatolási megjegyzéseket. Ha egy visszajelzési megjegyzés hosszabb, az elemzés csak az első 128 szót veszi figyelembe.

### <a name="data-requirements"></a>Adatkövetelmények
  
A következő adatattribútumokra van szükség:
- Egyesített ügyfél-azonosító (UCID), amely megfelelteti a szöveges visszajelzési adatrekordokat egy adott ügyfélnek. Ez az azonosító az [adategyesítési folyamat](data-unification.md) eredménye.
- Visszajelzés azonosítója
- Visszajelzési időbélyegző
- Visszajelzés szövege   

> [!TIP]
> A hangulatelemzéshez az ügyfelek szöveges visszajelzésére van szükség. Jelenleg csak egy visszajelzési entitás konfigurálható. Ha több visszajelzési entitás van, az adatbetöltés megkezdése előtt egyesítheti őket Power Query.

## <a name="configure-a-sentiment-analysis"></a>Hangulatelemzés konfigurálása 

1. A Customer Insights szolgáltatásban lépjen az **Intelligencia** > **Előrejelzések** részre.

1. Az Ügyfélhangulat-elemzés **csempén válassza a** Modell **használata lehetőséget**.

1. **Az Ügyfélhangulat-elemzés (előzetes verzió)** panelen válassza az Első lépések **lehetőséget**.

1. A Modell neve **lépésben adja meg** az **elemzés nevét**. 

1. Adja meg az **Üzleti szempont kimeneti entitás nevét** és a Hangulati pontszám kimeneti entitás nevét **, majd válassza a** Tovább **lehetőséget**.

1. A Szükséges adatok **lépésben válassza az** Adatok **hozzáadása lehetőséget**.

   :::image type="content" source="media/sentiment-add-data.png" alt-text="Adjon hozzá adatfolyamot a hangulatelemzési modellhez.":::

1. **Az Adatok** hozzáadása panelen válassza ki a listából a Visszajelzés **szemantikai típust**.

   :::image type="content" source="media/sentiment-add-feedback-activities.png" alt-text="Konfigurációs lépés a visszajelzési tevékenységek kiválasztásához a hangulatelemzéshez.":::

1. Válassza ki a hangulatelemzéshez használni kívánt tevékenységeket, majd válassza a Tovább **lehetőséget**.
 
1. Leképezheti az adatok attribútumait a modellattribútumokra. Válassza a Mentés **lehetőséget** a kijelölések alkalmazásához. 

1. Láthatja az adatleképezés állapotát. A folytatáshoz válassza a **Tovább** lehetőséget. 

1. **A Modell részleteinek** áttekintése lépésben ellenőrizze a hangulatelemzés konfigurációját. Visszatérhet a előrejelzés konfiguráció bármely részéhez. Válassza a Mentés és futtatás lehetőséget **az** elemzés elindításához. 

   :::image type="content" source="media/sentiment-model-review-config.png" alt-text="Tekintse át az összes konfigurált elemet megjelenítő hangulatmodell lépését.":::

1. Válassza a Kész **lehetőséget** a konfigurációs élmény elhagyásához. A folyamat a felhasznált adatok mennyiségétől függően több órát is igénybe vehet. 

## <a name="review-analysis-status"></a>Elemzés állapotának áttekintése

1.  Nyissa meg az **Intelligencia** > **Előrejelzések** menüt, és válassza ki a **Saját előrejelzések** lapot.
2.  Jelölje ki az áttekinteni kívánt előrejelzést.
- **Előrejelzés neve**: Az előrejelzés neve, mely a létrehozáskor kerül megadásra.
- **előrejelzés típus**: A előrejelzés használt modell típusa.
- **Kimeneti entitás**: Az előrejelzés kimenetének tárolására szolgáló entitás neve. Az ilyen nevű entitás kereséséhez válassza az **Adatok** > **Entitások** lehetőséget.
- **Várható mező**: Ez a mező csak bizonyos típusú előrejelzésekhez megadható, és nem használható az ügyféléletciklus értékének előrejelzéshez.
- **Állapot**: A futtatott előrejelzés állapota.
  - **Feldolgozási sorban**: Az előrejelzés további folyamatok befejezésére vár.
  - **Frissítés**: Az előrejelzés jelenleg fut, hogy a kimeneti entitásba kerülő eredményt hozhassa létre.
  - **Sikertelen**: Az előrejelzés lefuttatása sikertelen. Ellenőrizze a naplókat a további részletekért.
  - **Sikeres**: Az Előrejelzés lefuttatása sikeresen megtörtént. Válassza a Megtekintés lehetőséget a függőleges három pont alatt a kiválasztott előrejelzés megtekintéséhez.
- **Szerkesztve**: Az előrejelzés konfigurációjának módosítási dátuma.
- **Utolsó frissítés**: Az a dátum, amikor a előrejelzés frissítette az eredményeket a kimeneti entitásban.

## <a name="manage-sentiment-analysis"></a>Hangulatelemzés kezelése

Optimalizálhatja, elháríthatja, frissítheti vagy törölheti az előrejelzéseket. Tekintse át a bemeneti adatok használhatósági jelentését, hogy megtudja, hogyan lehet egy előrejelzés gyorsabb és megbízhatóbb. További tudnivalókért lásd: [Előrejelzések kezelése](manage-predictions.md).

## <a name="review-analysis-results"></a>Az elemzés eredményeinek áttekintése
 
1. Nyissa meg az **Intelligencia** > **Előrejelzések** menüt, és válassza ki a **Saját előrejelzések** lapot. 
1. Válassza ki annak a előrejelzés a nevét, amelynek eredményeit át szeretné tekinteni. Ebben az esetben válassza ki az áttekinteni kívánt hangulatelemzést. 

### <a name="summary-tab"></a>Összegzés lap

Az eredmények oldalán belül az adatoknak négy elsődleges szakasza van. 

- **Átlagos hangulati pontszám**: Segít megérteni az összes ügyfél általános hangulatát. A hangulati pontszámok három kategóriába vannak csoportosítva: 
  1.    Negatív (-5 > 2)
  2.    Semleges (-1 > 1)
  3.    Pozitív (2 > 5) 
  
  :::image type="content" source="media/overall-customer-sentiment.png" alt-text="Az általános ügyfélhangulat vizuális ábrázolása.":::

- **Az ügyfelek megoszlása hangulati pontszámok** szerint: Az ügyfeleket negatív, semleges és pozitív csoportokba soroljuk a hangulati pontszámaik alapján. Vigye az egérmutatót a hisztogram sávjai fölé az egyes csoportok vevőinek számához és átlagos hangulati pontszámához. Ezek az adatok segíthetnek az [ügyfelek](segments.md) szegmenseinek létrehozásában a hangulati pontszámaik alapján.  

  :::image type="content" source="media/distribution-customer-sentiment.png" alt-text="oszlopdiagram mutatja az ügyfelek hangulatát a három hangulatcsoportban.":::

- **Átlagos hangulati pontszám az idő múlásával**: Az ügyfelek hangulata idővel változhat. Az ügyfelek hangulatának trendjeit az adatok időtartományára vonatkozóan biztosítjuk. Ez a nézet segíthet felmérni a szezonális promóciók, termékbevezetések vagy más időhöz kötött beavatkozások hatását az ügyfelek hangulatára. Tekintse meg a grafikont az érdeklődésre számot tartó év kiválasztásával a legördülő menüből. 

  :::image type="content" source="media/sentiment-score-over-time.png" alt-text="előzménydiagram, hogy a hangulati pontszám az idő múlásával egy sorként jelenik meg.":::
 
- **Hangulat az üzleti szempontok között**: Ez a táblázat az üzleti szempontok közötti átlagos hangulatot sorolja fel. Segíthet felmérni, hogy vállalkozásának mely aspektusai elégítik ki már az ügyfeleket, vagy olyan szempontokat, amelyek nagyobb figyelmet igényelnek. Azok a visszajelzési rekordok, amelyek nem igazodnak a támogatott üzleti szempontok egyikéhez sem, az Egyéb **kategóriába** vannak sorolva. A táblázat alapértelmezés szerint betűrendben van rendezve. A rendezést egy táblázatfejléc kiválasztásával módosíthatja.

  :::image type="content" source="media/sentiment-across-business-aspects.png" alt-text="Az üzleti szempontok listája a kapcsolódó hangulatérték és az azt megemlítő ügyfelek száma.":::
 
  Válassza ki egy üzleti szempont nevét, ha további információkat szeretne látni arról, hogy a modell hogyan azonosítja az üzleti szempontot. Ebben az ablaktáblában két rész található: 

  - **Befolyásos szavak**: Azokat a kulcsszavakat jeleníti meg, amelyek befolyásolták, hogy az AI-modell azonosította az üzleti szempontot az ügyfelek visszajelzéseiben. 
    **Sértő szavak** megjelenítése: Lehetővé teszi, hogy sértő szavakat vegyen fel a listába az eredeti ügyfél-visszajelzési adatokból. Alapértelmezés szerint ki van kapcsolva.  A sértő szómaszkolást egy AI-modell hajtja végre, és előfordulhat, hogy nem észlel minden sértő szót. Folytatjuk az iterálást és az osztályozó képzését az optimális teljesítmény érdekében. Ha olyan sértő szót észlel, amelyet nem a várt módon szűrtek, tudassa velünk. 
    
    :::image type="content" source="media/offensive-words-sentiment.png" alt-text="A befolyásos szavak listája a kapcsolóval a sértő szavak megjelenítéséhez vagy elrejtéséhez.":::
 
  - **Visszajelzési minták**: Az adatokban szereplő tényleges visszajelzési rekordokat jeleníti meg. A szavakat az üzleti szempont azonosítására gyakorolt hatásuk szerint színkódolják. 


### <a name="influential-words-analysis-tab"></a>Befolyásos szavak elemzése lap

A további információknak három szakasza van, amelyek elmagyarázzák, hogyan működik a hangulatmodell.
  
1. **A pozitív hangulathoz** hozzájáruló legfontosabb szavak: Azokat a legfontosabb szavakat jeleníti meg, amelyek befolyásolták az AI-modell pozitív hangulatának azonosítását az ügyfelek visszajelzéseiben.  
2. **A negatív hangulathoz** hozzájáruló legfontosabb szavak: Azokat a legfontosabb szavakat jeleníti meg, amelyek befolyásolták az AI-modell negatív hangulatának azonosítását az ügyfelek visszajelzéseiben.  
3. **Visszajelzési minták**: Tényleges visszajelzési rekordokat jelenít meg, amelyek negatív hangulattal és pozitív érzéssel rendelkeznek. A visszajelzési rekordokban szereplő szavakat a hozzárendelt hangulati pontszámhoz való hozzájárulásuknak megfelelően emeljük ki. A pozitív hangulati pontszámhoz hozzájáruló szavakat zöld színnel emeljük ki. A negatív pontszámhoz hozzájáruló szavak pirossal vannak kiemelve.
   Válassza a Továbbiak **megtekintése lehetőséget** további visszajelzési minták betöltéséhez, amelyek további információkat és kontextust biztosítanak a hangulatmodell működéséről.
   
   :::image type="content" source="media/sentiment-feedback-samples.png" alt-text="Példák az ügyfelek visszajelzéseinek hangulatelemzésére.":::
 
**Sértő szavak** megjelenítése: Lehetővé teszi, hogy sértő szavakat vegyen fel a listába az eredeti ügyfél-visszajelzési adatokból. Alapértelmezés szerint ki van kapcsolva.  A sértő szómaszkolást egy AI-modell hajtja végre, és előfordulhat, hogy nem észlel minden sértő szót. Folytatjuk az iterálást és az osztályozó képzését az optimális teljesítmény érdekében. Ha olyan sértő szót észlel, amelyet nem a várt módon szűrtek, tudassa velünk. 

## <a name="act-on-analysis-results"></a>Az elemzési eredményekre vonatkozó intézkedés

Egyszerűen elkezdheti létrehozni az ügyfelek új szegmenseit a hangulatelemzés eredményoldalán, ha a modell eredményoldalának tetején a Szegmensek **létrehozása lehetőséget választja**.

:::image type="content" source="media/create-segment-model.png" alt-text="Parancssáv a előrejelzés modellek beállításaival.":::
 
## <a name="potential-bias"></a>Lehetséges elfogultság

Mint minden olyan funkció esetében, amely prediktív mesterséges intelligenciát használ, tisztában kell lennie az ügyfelek hangulatának előrejelzésére használt adatok esetleges elfogultságával. Ha például csak digitálisan gyűjt visszajelzést, hiányozhat az olyan ügyfelek visszajelzései, akik elsősorban személyesen folytatnak önnel üzleti tevékenységet, ami hatással lehet a funkció kimenetére.

Mivel ez a funkció automatizált eszközöket használ az adatok értékelésére és az adatokon alapuló előrejelzések készítésére, ezért képes profilalkotási módszerként használni, mivel ezt a kifejezést az általános adatvédelmi rendelet ("GDPR") határozza meg. A szolgáltatásnak az adatok feldolgozására való használatára a GDPR vagy más törvények vagy előírások vonatkozhatnak. Ön felelős annak biztosításáért, hogy az Ön általi használat, beleértve a Dynamics 365 Customer Insights hangulatelemzést is, megfeleljen az összes vonatkozó törvénynek és rendeletnek, beleértve a magánéletre, a személyes adatokra, a biometrikus adatokra, az adatvédelemre és a kommunikáció titkosságára vonatkozó törvényeket is.

[!INCLUDE [footer-include](includes/footer-banner.md)]

