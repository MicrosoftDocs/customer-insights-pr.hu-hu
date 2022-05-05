---
title: Hangulatelemzés az ügyfelek visszajelzéseihez
description: További információ arról, hogyan használhat hangulatelemző modellt az ügyfelek visszajelzéseihez a alkalmazásban Dynamics 365 Customer Insights.
ms.date: 12/23/2021
ms.subservice: audience-insights
ms.reviewer: mhart
ms.topic: conceptual
author: wmelewong
ms.author: wameng
manager: shellyha
ms.openlocfilehash: e51225bbfcd445180b12661cba12256c3f042045
ms.sourcegitcommit: b7dbcd5627c2ebfbcfe65589991c159ba290d377
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/27/2022
ms.locfileid: "8642748"
---
# <a name="analyze-sentiment-in-customer-feedback-preview"></a>Hangulat elemzése az ügyfelek visszajelzéseiben (előzetes verzió)

Az ügyfelek manapság kiváló minőségű termékeket, szolgáltatásokat és élményeket várnak el. Különösen azok az ügyfelek, akik megosztják visszajelzéseiket. A szervezetek számára nagy kihívást jelent a növekvő mennyiségű adat elemzése a pontosság és a magasabb munkaerőköltség csökkentése nélkül. Dynamics 365 Customer Insights hangulatelemzési modellt kínál az ügyfelek visszajelzéseihez, amely lehetővé teszi a szervezetek számára, hogy pontosabban és alacsonyabb költséggel elemezzék adataikat.

A hangulatelemzés lehetővé teszi az ügyfelek hangulatának szintetizálását és az üzleti szempontok azonosítását fejlesztési lehetőségként. Ez a Customer Insights funkció segít megérteni, hogy mi működik jól, és mit kell kezelnie. Összpontosítson a legrelevánsabb és leghatásosabb üzleti területekre, hogy javítsa ügyfelei élményét. Végső soron segíthet olyan üzleti tevékenységek ösztönzésében, amelyek lehetővé teszik a magas ügyfél-elégedettséget és hűséget eredményező élményeket.

## <a name="overview"></a>Áttekintés

A hangulatelemző funkció ügyfélazonosítónként két származtatott betekintést hoz létre. A hangulati pontszám (-5-től 5-ig) és az alkalmazandó üzleti szempontok (üzleti területek) listája együttesen segít jobban megérteni az ügyfelek visszajelzéseit. 

Ezek az információk segíthetnek a következő eredmények elérésében: 
- Áttekintést kaphat az ügyfelek márka vagy szervezet iránti érzéseiről
- Azonosítsa a negatív hangulatú ügyfeleket, hogy összpontosítsa kampányait és elkötelezettségeit, és optimalizálja a magasabb hozamot  
- Az üzleti szempontok azonosítása az ügyfelek által felvetett kérdésekkel  
- Szegmens ügyfelek hangulatuk alapján, hogy személyre szabott kampányokat futtassanak célzott értékesítési, marketing és támogatási erőfeszítésekkel
- Optimalizálja az üzleti műveleteket az ügyfelek által említett aggodalomra okot adó területek vagy lehetőségek kezelésével
- Ismerje fel azokat az üzleti szempontokat, amelyek jól teljesítenek, és jutalmazza a boldog ügyfeleket hűség- és promóciós programokon keresztül

Annak érdekében, hogy megbízhasson a modellek eredményeiben, átlátható információkat nyújtunk arról, hogy a modellek hogyan hoznak döntéseket. Kap egy listát azokról a szavakról, amelyek befolyásolták a modellek azon döntését, hogy egy adott hangulati pontszámot vagy üzleti szempontot rendelnek a visszajelzési megjegyzésekhez.  

Két **természetes nyelvi feldolgozási (NLP) modellt** használunk: Az első minden visszajelzési megjegyzéshez hozzárendel egy hangulati pontszámot. A második modell minden visszajelzést társít az összes vonatkozó üzleti szemponthoz. A modelleket a közösségi média, a kiskereskedelem, az étterem, a fogyasztási cikkek és az autóipar forrásaiból származó nyilvános adatokra képzik.    
  
A visszajelzési adatokhoz társítandó modell előre meghatározott üzleti szempontjai a következők:
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
> Jelenleg csak az angol ügyfelek visszajelzéseinek hangulatelemzését támogatjuk. A jövőben több nyelvet is támogatni fognak. Ha más nyelveken is feltölt visszajelzést, a modell továbbra is eredményeket ad vissza. Ezek az eredmények azonban nem lesznek pontosak. 

## <a name="prerequisites"></a>Előfeltételek

A hangulatelemzés olyan szöveges visszajelzési adatokon alapul, amelyek az [adategyesítési folyamaton mentek keresztül](data-unification.md). Javasoljuk, hogy [előzetesen konfigurálja a visszajelzési adat entitásokat szemantikai típusú tevékenységi entitásként](map-entities.md#select-primary-key-and-semantic-type-for-attributes) (Visszajelzés típusa). 

Hangulatelemzési modell konfigurálásához legalább [közreműködő engedélyre](permissions.md) van szükség.

A Customer Insights akár 10 millió visszajelzési rekordot is feldolgozhat egyetlen modell futtatásához. A modell legfeljebb 128 szóból képes elemezni a visszajelzési megjegyzéseket. Ha egy visszajelzési megjegyzés hosszabb, az elemzés csak az első 128 szót veszi figyelembe.

### <a name="data-requirements"></a>Adatkövetelmények
  
A következő adatattribútumok szükségesek:
- Egységes ügyfélazonosító (UCID), amely a szöveges visszajelzési adatrekordokat egy adott ügyfélhez igazítja. Ez az azonosító az adategyesítési folyamat [eredménye](data-unification.md).
- Visszajelzés azonosítója
- Visszajelzési időbélyegző
- Visszajelzés szövege   

> [!TIP]
> A hangulatelemzéshez az ügyfelek szöveges visszajelzésére van szükség. Jelenleg csak egy visszajelzési entitás konfigurálható. Ha több visszacsatolási entitás van, akkor az adatbetöltés megkezdése előtt egyesítheti őket Power Query.

## <a name="configure-a-sentiment-analysis"></a>Hangulatelemzés konfigurálása 

1. A Customer Insights szolgáltatásban lépjen az **Intelligencia** > **Előrejelzések** részre.

1. Az Ügyfél hangulatelemzés csempéjén válassza a **Modell használata lehetőséget** **.**

1. **Az Ügyfél hangulatelemzés (betekintés)** ablaktáblában válassza az Első lépések **lehetőséget**.

1. **A Modellnév** lépésben adja meg **az elemzés nevét**. 

1. Adja meg az **Üzleti szempont kimeneti entitásnevét** és a Sentiment score kimeneti entitás nevét **, majd válassza a** Tovább **lehetőséget**.

1. A Kötelező adatok **lépésben válassza az** Adatok **hozzáadása lehetőséget**.

   :::image type="content" source="media/sentiment-add-data.png" alt-text="Adatáramlás hozzáadása a hangulatelemzési modellhez.":::

1. **Az Adatok** hozzáadása ablaktáblán válassza ki a listából a Visszajelzés **szemantikai típusát**.

   :::image type="content" source="media/sentiment-add-feedback-activities.png" alt-text="Konfigurációs lépés a visszajelzési tevékenységek kiválasztásához hangulatelemzéshez.":::

1. Válassza ki az érzelemelemzéshez használni kívánt tevékenységeket, majd válassza a Tovább **lehetőséget**.
 
1. Az adatok attribútumainak leképezése a modellattribútumokhoz. A kijelölés alkalmazásához válassza a Mentés **lehetőséget**. 

1. Megjelenik az adatleképezés állapota. A folytatáshoz válassza a **Tovább** lehetőséget. 

1. **A Modell részleteinek** áttekintése lépésben ellenőrizze az érzéselemzés konfigurációját. Visszatérhet a előrejelzés konfiguráció bármely részéhez. Az elemzés megkezdéséhez válassza **a Mentés lehetőséget, és futtassa a futtatást**. 

   :::image type="content" source="media/sentiment-model-review-config.png" alt-text="Tekintse át az összes konfigurált elemet megjelenítő hangulatmodell lépését.":::

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
- **Utolsó frissítés**: Az a dátum, amikor a előrejelzés frissült, a kimeneti entitásban eredményt ad.

## <a name="manage-sentiment-analysis"></a>Hangulatelemzés kezelése

Optimalizálhatja, elháríthatja, frissítheti vagy törölheti az előrejelzéseket. Tekintse át a bemeneti adatok használhatósági jelentését, hogy megtudja, hogyan lehet egy előrejelzés gyorsabb és megbízhatóbb. További tudnivalókért lásd: [Előrejelzések kezelése](manage-predictions.md).

## <a name="review-analysis-results"></a>Elemzés eredményeinek áttekintése
 
1. Nyissa meg az **Intelligencia** > **Előrejelzések** menüt, és válassza ki a **Saját előrejelzések** lapot. 
1. Válassza ki annak a előrejelzés a nevét, amelynek eredményeit át szeretné tekinteni. Ebben az esetben válassza ki a megtekinteni kívánt hangulatelemzést. 

### <a name="summary-tab"></a>Összegzés lap

Az eredményoldalon négy fő adatszakasz található. 

- **Átlagos hangulati pontszám**: Segít megérteni az összes ügyfél általános hangulatát. A hangulati pontszámok három kategóriába sorolhatók: 
  1.    Negatív (-5 > 2)
  2.    Semleges (-1 > 1)
  3.    Pozitív (2 > 5) 
  
  :::image type="content" source="media/overall-customer-sentiment.png" alt-text="Az általános ügyfélhangulat vizuális ábrázolása.":::

- **Az ügyfelek eloszlása hangulati pontszám** szerint: Az ügyfeleket negatív, semleges és pozitív csoportokba sorolják hangulati pontszámaik alapján. Vigye az egérmutatót a hisztogram sávjai fölé az egyes csoportokban lévő ügyfelek számának és átlagos hangulati pontszámának megtekintéséhez. Ezek az adatok segíthetnek [az ügyfelek](segments.md) szegmenseinek létrehozásában a hangulati pontszámaik alapján.  

  :::image type="content" source="media/distribution-customer-sentiment.png" alt-text="oszlopdiagram mutatja az ügyfelek hangulatát a három hangulatcsoportban.":::

- **Átlagos hangulati pontszám idővel**: Az ügyfelek hangulata idővel változhat. Az ön ügyfelei hangulatának trendjeit biztosítjuk az adatok időtartományában. Ez a nézet segíthet felmérni a szezonális promóciók, termékbevezetések vagy más időhöz kötött beavatkozások hatását az ügyfelek hangulatára. Tekintse meg a grafikont a legördülő menü érdeklődési évének kiválasztásával. 

  :::image type="content" source="media/sentiment-score-over-time.png" alt-text="előzménydiagram, hogy az idő múlásával elért hangulati pontszám vonalként jelenik meg.":::
 
- **Hangulat az üzleti szempontok között**: Ez a táblázat felsorolja az üzleti szempontok közötti átlagos hangulatot. Segíthet felmérni, hogy vállalkozásának mely aspektusai már kielégítik az ügyfeleket vagy a nagyobb figyelmet igénylő szempontokat. Azok a visszajelzési rekordok, amelyek nem igazodnak a támogatott üzleti szempontok egyikéhez sem, az Egyéb **kategóriába** sorolhatók. A táblázat alapértelmezés szerint betűrendben van rendezve. A rendezést táblázatfejléc kiválasztásával módosíthatja.

  :::image type="content" source="media/sentiment-across-business-aspects.png" alt-text="Az üzleti szempontok listája a kapcsolódó hangulatérték és az azt említő ügyfelek számával.":::
 
  Válassza ki egy üzleti szempont nevét, ha további információkat szeretne látni arról, hogy a modell hogyan azonosítja az üzleti szempontot. Az ablaktáblán két rész található: 

  - **Befolyásos szavak**: Megmutatja azokat a legfontosabb szavakat, amelyek befolyásolták az AI modell üzleti szempontjának azonosítását az ügyfelek visszajelzéseiben. 
    **Sértő szavak** megjelenítése: Lehetővé teszi sértő szavak felvételét a listába az eredeti ügyfél-visszajelzési adatokból. Alapértelmezés szerint ki van kapcsolva.  A sértő szómaszkolást AI-modell hajtja, és előfordulhat, hogy nem észleli az összes sértő szót. Folytatjuk az iterálást és az osztályozó képzését az optimális teljesítmény érdekében. Ha olyan sértő szót észlel, amely nem a várt módon lett szűrve, tudassa velünk. 
    
    :::image type="content" source="media/offensive-words-sentiment.png" alt-text="A támadó szavak megjelenítéséhez vagy elrejtéséhez kapcsolóval rendelkező befolyásos szavak listája.":::
 
  - **Visszajelzési minták**: Tényleges visszajelzési rekordok megjelenítése az adatokban. A szavak színkódolása az üzleti szempont azonosítására gyakorolt hatásuk szerint történik. 


### <a name="influential-words-analysis-tab"></a>Befolyásos szavak elemzése lap

A további információknak három szakasza magyarázza el, hogyan működik a hangulatmodell.
  
1. **A pozitív hangulathoz** hozzájáruló legfontosabb szavak: Olyan legfontosabb szavakat mutat be, amelyek befolyásolták az AI modell pozitív hangulatának azonosítását az ügyfelek visszajelzéseiben.  
2. **A negatív hangulathoz** hozzájáruló legfontosabb szavak: Olyan legfontosabb szavakat mutat, amelyek befolyásolták az AI modell negatív hangulatának azonosítását az ügyfelek visszajelzéseiben.  
3. **Visszajelzési minták**: Tényleges visszajelzési rekordokat mutat, az egyik negatív érzéssel és pozitív érzéssel. A visszajelzési rekordokban szereplő szavakat a hozzárendelt hangulati pontszámhoz való hozzájárulásuk szerint emelik ki. Azok a szavak, amelyek hozzájárulnak a pozitív hangulati pontszámhoz, zöld színnel vannak kiemelve. A negatív pontszámhoz hozzájáruló szavak pirossal vannak kiemelve.
   Válassza a Továbbiak **megtekintése lehetőséget** további visszajelzésminták betöltéséhez, amelyek további információkat és kontextust biztosítanak a hangulatmodell működéséről.
   
   :::image type="content" source="media/sentiment-feedback-samples.png" alt-text="Példák az ügyfelek visszajelzéseire vonatkozó hangulatelemzésre.":::
 
**Sértő szavak** megjelenítése: Lehetővé teszi sértő szavak felvételét a listába az eredeti ügyfél-visszajelzési adatokból. Alapértelmezés szerint ki van kapcsolva.  A sértő szómaszkolást AI-modell hajtja, és előfordulhat, hogy nem észleli az összes sértő szót. Folytatjuk az iterálást és az osztályozó képzését az optimális teljesítmény érdekében. Ha olyan sértő szót észlel, amely nem a várt módon lett szűrve, tudassa velünk. 

## <a name="act-on-analysis-results"></a>Az elemzési eredményekre vonatkozó jogi aktus

A modell eredményoldalának tetején található Szegmensek **létrehozása lehetőséget választva** egyszerűen elkezdheti az ügyfelek új szegmenseinek létrehozását a hangulatelemzés eredményoldaláról.

:::image type="content" source="media/create-segment-model.png" alt-text="Parancssáv előrejelzés modelleken található beállításokkal.":::
 
## <a name="potential-bias"></a>Lehetséges torzítás

Mint minden olyan funkció esetében, amely prediktív mesterséges intelligenciát használ, tisztában kell lennie az ügyfelek hangulatának előrejelzéséhez használt adatok esetleges torzításával. Ha például csak digitálisan gyűjt visszajelzést, akkor lemaradhat az olyan ügyfelek visszajelzéseiről, akik elsősorban személyesen folytatnak üzleti tevékenységet Önnel, ami befolyásolhatja a funkció kimenetét.

Mivel ez a funkció automatizált eszközöket használ az adatok értékelésére és az ezen adatokon alapuló előrejelzések készítésére, ezért képes profilalkotási módszerként használni, mivel ezt a kifejezést az általános adatvédelmi rendelet ("GDPR") határozza meg. A szolgáltatásnak az adatok feldolgozására való használatára a GDPR vagy más törvények vagy előírások vonatkozhatnak. Ön felelős annak biztosításáért, hogy az Ön használata Dynamics 365 Customer Insights– beleértve a hangulatelemzést is – megfeleljen az összes vonatkozó törvénynek és rendeletnek, beleértve a magánélettel, a személyes adatokkal, a biometrikus adatokkal, az adatvédelemmel és a kommunikáció titkosságával kapcsolatos törvényeket is.

[!INCLUDE [footer-include](includes/footer-banner.md)]

