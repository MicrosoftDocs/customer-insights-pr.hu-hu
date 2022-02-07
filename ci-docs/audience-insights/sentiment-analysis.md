---
title: Hangulatelemzés az ügyfelek visszajelzéseihez
description: 'További információ arról, hogyan használhatja a hangulatelemzési modellt a vevői visszajelzéseken a Dynamics 365 Customer Insights.'
ms.date: 12/23/2021
ms.service: customer-insights
ms.subservice: audience-insights
ms.reviewer: mhart
ms.topic: conceptual
author: wmelewong
ms.author: wameng
manager: shellyha
---

# <a name="analyze-sentiment-in-customer-feedback-preview"></a>Hangulatelemzés az ügyfelek visszajelzésében (előzetes verzió)

Az ügyfelek manapság kiváló minőségű termékeket, szolgáltatásokat és élményeket várnak. Különösen az ügyfelek, akik megosztják visszajelzéseiket. A szervezetek számára nagy kihívást jelent a növekvő mennyiségű adat elemzése a pontosság és a magasabb munkaerőköltség csökkentése nélkül. Dynamics 365 Customer Insights hangulatelemzési modellt kínál az ügyfelek visszajelzéseihez, amely lehetővé teszi a szervezetek számára, hogy pontosabban és alacsonyabb költséggel elemezzék adataikat.

A hangulatelemzés lehetővé teszi az ügyfelek hangulatának szintetizálását és az üzleti szempontok azonosítását a fejlődés lehetőségeként. Ez a Customer Insights funkció segít megérteni, hogy mi működik jól, és mit kell kezelnie. Összpontosítson a legrelevánsabb és leghatásosabb üzleti területekre, hogy javítsa az ügyfelek élményét. Végső soron segíthet olyan üzleti tevékenységek vezetésében, amelyek lehetővé teszik a magas ügyfél-elégedettséget és hűséget eredményező tapasztalatokat.

## <a name="overview"></a>Áttekintés

A hangulatelemzési funkció ügyfélazonosítónként két származtatott elemzési értéket generál. A hangulati pontszám (-5-5) és az alkalmazandó üzleti szempontok listája (üzleti területek) együttesen segít jobban megérteni az ügyfelek visszajelzéseit. 

Ezek az információk segíthetnek a következő eredmények elérésében: 
- Áttekintés az ügyfelek hangulatáról egy márkával vagy szervezettel szemben
- Azonosítsa a negatív hangulatú ügyfeleket, hogy kampányait és elkötelezettségeit összpontosítsa, és optimalizálja a magasabb megtérülést  
- Az üzleti szempontok azonosítása az ügyfelek által kiemelt problémákkal  
- Az ügyfelek szegmense a hangulatuk alapján személyre szabott kampányokat futtatnak célzott értékesítési, marketing- és támogatási erőfeszítésekkel
- Az üzleti műveletek optimalizálása az ügyfelek által említett aggodalomra okot adó területek vagy lehetőségek kezelésével
- Ismerje fel azokat az üzleti szempontokat, amelyek jól teljesítenek, és jutalmazza a boldog ügyfeleket hűség- és promóciós programokon keresztül

Annak érdekében, hogy megbízhat a modellek eredményeiben, átlátható tájékoztatást nyújtunk arról, hogy a modellek hogyan hoznak döntéseket. Kapsz egy listát azokról a szavakról, amelyek befolyásolták a modellek azon döntését, hogy egy adott hangulati pontszámot vagy üzleti szempontot rendelnek a visszajelzési megjegyzésekhez.  

Két **természetes nyelvi feldolgozás (NLP) modellt** használunk: Az első minden visszajelzést hozzáfűz egy hangulati pontszámhoz. A második modell minden visszajelzést az összes vonatkozó üzleti szemponthoz társít. A modelleket a közösségi média, a kiskereskedelem, az étterem, a fogyasztói termékek és az autóipar forrásaiból származó nyilvános adatok alapján képzik.    
  
A modell visszajelzési adatokkal való társítására vonatkozó előre meghatározott üzleti szempontok a következők:
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
> Jelenleg csak az angol ügyfelek visszajelzéseinek hangulatelemzését támogatjuk. A jövőben több nyelvet is támogatni fognak. Ha más nyelveken is feltölti a visszajelzéseket, a modell továbbra is eredményeket ad vissza. Ezek az eredmények azonban nem lesznek pontosak. 

## <a name="prerequisites"></a>Előfeltételek

A hangulatelemzés az adategyesítési folyamaton keresztülment [szöveges visszajelzési adatokon alapul](data-unification.md). Javasoljuk, hogy [előzetesen állítsa be a visszajelzési adategyezteseket szemantikai típusú tevékenység entitásként](map-entities.md#select-primary-key-and-semantic-type-for-attributes) (Visszajelzés típusa). 

Hangulatelemzési modell konfigurálásához legalább [közreműködő engedélyre](permissions.md) van szükség.

A Customer Insights egyetlen modell futtatásához akár 10 millió visszajelzési rekordot is feldolgozhat. A modell legfeljebb 128 szóból elemezheti a visszajelzési megjegyzéseket. Ha egy visszajelzési megjegyzés hosszabb, az elemzés csak az első 128 szót veszi figyelembe.

### <a name="data-requirements"></a>Adatkövetelmények
  
A következő adatattribútumokra van szükség:
- Egységes ügyfélazonosító (UCID), hogy a szöveges visszajelzési adatrekordokat egy adott ügyfélhez illessze. Ez az azonosító az [adategyesítési folyamat](data-unification.md) eredménye.
- Visszajelzés azonosítója
- Visszajelzési időbélyeg
- Visszajelzés szövege   

> [!TIP]
> A hangulatelemzéshez az ügyfelek szöveges visszajelzésére van szükség. Jelenleg csak egy visszacsatolási entitás konfigurálható. Ha több visszajelzési entitás van, az adatbetöltés megkezdése előtt beállíthatja őket Power Query.

## <a name="configure-a-sentiment-analysis"></a>Hangulatelemzés konfigurálása 

1. A Customer Insights szolgáltatásban lépjen az **Intelligencia** > **Előrejelzések** részre.

1. A Vevői hangulatelemzés **csempén válassza a** Modell **használata lehetőséget**.

1. **A Vevői hangulatelemzés (előnézet)** ablaktáblán válassza az Első lépések **lehetőséget**.

1. **A Modellnév** lépésben adja meg **az elemzés nevét**. 

1. Adja meg az **Üzleti szempont kimeneti entitás nevét** és a **Hangulati pontszám kimeneti entitás nevét**, majd válassza a Tovább **lehetőséget**.

1. A Szükséges adatok **lépésben válassza az** Adatok **hozzáadása lehetőséget**.

   :::image type="content" source="media/sentiment-add-data.png" alt-text="Adatáramlás hozzáadása a hangulatelemzési modellhez.":::

1. **Az Adatok** hozzáadása ablaktáblán válassza ki a visszajelzés **szemantikai típusát** a listából.

   :::image type="content" source="media/sentiment-add-feedback-activities.png" alt-text="Konfigurációs lépés a hangulatelemzéshez a visszajelzési tevékenységek kiválasztásához.":::

1. Jelölje ki az ehhez a hangulatelemzéshez használandó tevékenységeket, majd válassza a Tovább **lehetőséget**.
 
1. Az adatok attribútumainak leképezése a modellattribútumokhoz. A beállítások alkalmazásához válassza a Mentés **lehetőséget**. 

1. Megjelenik az adatleképezés állapota. A folytatáshoz válassza a **Tovább** lehetőséget. 

1. **A Modell részleteinek** áttekintése lépésben ellenőrizze a hangulatelemzés konfigurációját. A előrejelzés konfiguráció bármely részéhez visszatérhet. Az elemzés elindításához válassza a Mentés és futtatás **lehetőséget**. 

   :::image type="content" source="media/sentiment-model-review-config.png" alt-text="Az összes konfigurált elemet megjelenítő hangulatmodell áttekintő lépése.":::

1. Válassza a Kész **lehetőséget** a konfigurációs élmény elhagyásához. A folyamat a felhasznált adatok mennyiségétől függően több órát is igénybe vehet. 

## <a name="review-analysis-status"></a>Elemzés állapotának áttekintése

1.  Nyissa meg az **Intelligencia** > **Előrejelzések** menüt, és válassza ki a **Saját előrejelzések** lapot.
2.  Jelölje ki az áttekinteni kívánt előrejelzést.
- **Előrejelzés neve**: Az előrejelzés neve, mely a létrehozáskor kerül megadásra.
- **előrejelzés típusa**: A előrejelzés használt modell típusa.
- **Kimeneti entitás**: Az előrejelzés kimenetének tárolására szolgáló entitás neve. Az ilyen nevű entitás kereséséhez válassza az **Adatok** > **Entitások** lehetőséget.
- **Várható mező**: Ez a mező csak bizonyos típusú előrejelzésekhez megadható, és nem használható az ügyféléletciklus értékének előrejelzéshez.
- **Állapot**: A futtatott előrejelzés állapota.
  - **Feldolgozási sorban**: Az előrejelzés további folyamatok befejezésére vár.
  - **Frissítés**: Az előrejelzés jelenleg fut, hogy a kimeneti entitásba kerülő eredményt hozhassa létre.
  - **Sikertelen**: Az előrejelzés lefuttatása sikertelen. Ellenőrizze a naplókat a további részletekért.
  - **Sikeres**: Az Előrejelzés lefuttatása sikeresen megtörtént. Válassza a Megtekintés lehetőséget a függőleges három pont alatt a kiválasztott előrejelzés megtekintéséhez.
- **Szerkesztve**: Az előrejelzés konfigurációjának módosítási dátuma.
- **Utoljára frissítve**: Az a dátum, amikor a előrejelzés frissítette az eredményeket a kimeneti entitásban.

## <a name="manage-sentiment-analysis"></a>Hangulatelemzés kezelése

Optimalizálhatja, elháríthatja, frissítheti vagy törölheti az előrejelzéseket. Tekintse át a bemeneti adatok használhatósági jelentését, hogy megtudja, hogyan lehet egy előrejelzés gyorsabb és megbízhatóbb. További tudnivalókért lásd: [Előrejelzések kezelése](manage-predictions.md).

## <a name="review-analysis-results"></a>Elemzési eredmények áttekintése
 
1. Nyissa meg az **Intelligencia** > **Előrejelzések** menüt, és válassza ki a **Saját előrejelzések** lapot. 
1. Válassza ki annak a előrejelzés a nevét, amelyhez át szeretné vizsgálni az eredményeket. Ebben az esetben válassza ki a áttekinteni kívánt hangulatelemzést. 

### <a name="summary-tab"></a>Összegzés lap

Az eredményoldalon négy elsődleges adatszakasz található. 

- **Átlagos hangulati pontszám**: Segít megérteni az általános hangulatot az összes ügyfélben. A hangulati pontszámok három kategóriába sorolhatók: 
  1.    Negatív (-5 > 2)
  2.    Semleges (-1 > 1)
  3.    Pozitív (2 > 5) 
  
  :::image type="content" source="media/overall-customer-sentiment.png" alt-text="Az általános ügyfélhangulat vizuális ábrázolása.":::

- **Az ügyfelek megoszlása hangulati pontszám** szerint: Az ügyfelek negatív, semleges és pozitív csoportokba vannak sorolva a hangulati pontszámaik alapján. Vigye az egérmutatót a hisztogram sávjai fölé, hogy lássa az ügyfelek számát és az átlagos hangulati pontszámot az egyes csoportokban. Ezek az adatok segíthetnek [az ügyfelek](segments.md) szegmenseinek létrehozásában a hangulati pontszámaik alapján.  

  :::image type="content" source="media/distribution-customer-sentiment.png" alt-text="oszlopdiagram az ügyfél hangulatát mutatja a három hangulatcsoportban.":::

- **Átlagos hangulati pontszám az idő** múlásával: Az ügyfelek hangulata idővel változhat. Az adatok időtartományára vonatkozóan trendeket biztosítunk ügyfelei hangulatában. Ez a nézet segíthet felmérni a szezonális promóciók, termékbemutatók vagy más időhöz kötött beavatkozások hatását az ügyfelek hangulatára. Tekintse meg a grafikont az érdeklődés éve legördülő menüből történő kiválasztásával. 

  :::image type="content" source="media/sentiment-score-over-time.png" alt-text="előzménydiagram az érzelmek pontszám idővel képviselt, mint egy sort.":::
 
- **Hangulat az üzleti szempontok** között: Ez a táblázat felsorolja az átlagos hangulatot az üzleti szempontok között. Ez segíthet felmérni, hogy vállalkozásának mely aspektusai már kielégítik az ügyfeleket vagy olyan szempontokat, amelyek nagyobb figyelmet igényelnek. Azok a visszajelzési rekordok, amelyek nem felelnek meg a támogatott üzleti szempontok egyikének sem, az Egyéb **kategóriába** tartoznak. A táblázat alapértelmezés szerint betűrendben van rendezve. A rendezést táblázatfejléc kijelölésével módosíthatja.

  :::image type="content" source="media/sentiment-across-business-aspects.png" alt-text="A kapcsolódó hangulatérték kapcsolatos üzleti szempontok listája és az azt megemlítő ügyfelek száma.":::
 
  Válassza ki egy üzleti szempont nevét, ha további információkat szeretne látni arról, hogy a modell hogyan azonosítja az üzleti szempontot. Ebben az ablaktáblában két rész található: 

  - **Befolyásos szavak**: Megjeleníti a legfontosabb szavakat, amelyek befolyásolták az AI modell üzleti szempontjának azonosítását az ügyfelek visszajelzésében. 
    **Sértő szavak** megjelenítése: Lehetővé teszi, hogy sértő szavakat szerepeltess a listában az eredeti ügyfél-visszajelzési adatokból. Alapértelmezés szerint ki van kapcsolva.  A sértő szómaszkolást AI-modell hajtja, és előfordulhat, hogy nem észleli az összes sértő szót. Folytatjuk az osztályozó iterálását és képzését az optimális teljesítmény érdekében. Ha olyan sértő szót észlel, amelyet nem szűrtek a várt módon, tudassa velünk. 
    
    :::image type="content" source="media/offensive-words-sentiment.png" alt-text="A sértő szavak megjelenítésére vagy elrejtésére váltógombos befolyásos szavak listája.":::
 
  - **Visszajelzési minták**: Tényleges visszajelzési rekordokat jelenít meg az adatokban. A szavak színkódoltak az üzleti szempont azonosítására gyakorolt hatásuknak megfelelően. 


### <a name="influential-words-analysis-tab"></a>Befolyásos szavak elemzése lap

Három további információ van, amelyek elmagyarázzák, hogyan működik a hangulatmodell.
  
1. **A pozitív hangulathoz** hozzájáruló legfontosabb szavak: Olyan legfontosabb szavakat mutat be, amelyek befolyásolták az AI modell pozitív hangulatának azonosítását az ügyfelek visszajelzésében.  
2. **A negatív hangulathoz** hozzájáruló legfontosabb szavak: Olyan legfontosabb szavakat mutat, amelyek befolyásolták az AI modell negatív hangulatának azonosítását az ügyfelek visszajelzésében.  
3. **Visszajelzési minták**: Tényleges visszacsatolási rekordokat jelenít meg, az egyik negatív hangulattal, a másikat pozitív hangulattal. A visszacsatolási rekordokban lévő szavak a hozzárendelt hangulati pontszámhoz való hozzájárulásuk alapján kerülnek kiemelésre. Azok a szavak, amelyek hozzájárulnak a pozitív érzelmi pontszámhoz, zölddel vannak kiemelve. A negatív pontszámhoz hozzájáruló szavak pirossal vannak kiemelve.
   Válassza a **További információk lehetőséget** további visszajelzésminták betöltéséhez, amelyek további információkat és kontextust biztosítanak a hangulatmodell működéséről.
   
   :::image type="content" source="media/sentiment-feedback-samples.png" alt-text="Példák a hangulatelemzésre az ügyfelek visszajelzései alapján.":::
 
**Sértő szavak** megjelenítése: Lehetővé teszi, hogy sértő szavakat szerepeltess a listában az eredeti ügyfél-visszajelzési adatokból. Alapértelmezés szerint ki van kapcsolva.  A sértő szómaszkolást AI-modell hajtja, és előfordulhat, hogy nem észleli az összes sértő szót. Folytatjuk az osztályozó iterálását és képzését az optimális teljesítmény érdekében. Ha olyan sértő szót észlel, amelyet nem szűrtek a várt módon, tudassa velünk. 

## <a name="act-on-analysis-results"></a>Az elemzési eredményekről szóló törvény

A hangulatelemzés eredményoldalán egyszerűen elkezdhet új ügyfélszegmenseket létrehozni, ha a modell eredményoldalának tetején szegmensek **létrehozása lehetőséget választja**.

:::image type="content" source="media/create-segment-model.png" alt-text="Parancssáv előrejelzés modellek beállításaival.":::
 
## <a name="potential-bias"></a>Lehetséges torzítás

Mint minden olyan funkciónál, amely prediktív mesterséges intelligenciát használ, tisztában kell lennie az ügyfelek hangulatának előrejelzésére használt adatok potenciális elfogultságával. Ha például csak digitálisan gyűjti a visszajelzéseket, hiányozhatnak azoknak az ügyfeleknek a visszajelzései, akik elsősorban személyesen folytatnak üzleti tevékenységet Önnel, ami befolyásolhatja a funkció kimenetét.

Mivel ez a funkció automatizált eszközöket használ az adatok értékelésére és az ezen adatokon alapuló előrejelzések készítésére, ezért képes profilalkotási módszerként használni, mivel ezt a kifejezést az általános adatvédelmi rendelet ("GDPR") határozza meg. A szolgáltatásnak az adatok feldolgozására való használatára a GDPR vagy más törvények vagy előírások vonatkozhatnak. Ön felelős annak biztosításáért, hogy a használata – beleértve a Dynamics 365 Customer Insights hangulatelemzést is – megfeleljen az összes vonatkozó törvénynek és rendeletnek, beleértve a magánéletre, a személyes adatokra, a biometrikus adatokra, az adatvédelemre és a kommunikáció titkosságára vonatkozó törvényeket is.

[!INCLUDE[footer-include](../includes/footer-banner.md)]

