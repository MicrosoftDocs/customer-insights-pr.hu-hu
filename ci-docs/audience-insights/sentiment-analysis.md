---
title: Hangulatelemzés az ügyfelek visszajelzéseihez
description: További információ arról, hogyan használhatja a hangulatelemzési modellt az ügyfelek visszajelzéseihez a Dynamics 365 Customer Insights.
ms.date: 12/23/2021
ms.subservice: audience-insights
ms.reviewer: mhart
ms.topic: conceptual
author: wmelewong
ms.author: wameng
manager: shellyha
ms.openlocfilehash: b06613b00a512a31479f9d30d539a010e17d33ba
ms.sourcegitcommit: e7cdf36a78a2b1dd2850183224d39c8dde46b26f
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/16/2022
ms.locfileid: "8231468"
---
# <a name="analyze-sentiment-in-customer-feedback-preview"></a>Hangulat elemzése az ügyfelek visszajelzéseiben (előzetes verzió)

Az ügyfelek manapság kiváló minőségű termékeket, szolgáltatásokat és élményeket várnak el. Különösen azok az ügyfelek, akik megosztják visszajelzéseiket. Nagy kihívást jelent a szervezetek számára, hogy elemezzék a növekvő mennyiségű adatot anélkül, hogy csökkentenék a pontosságot és a magasabb munkaerőköltséget. Dynamics 365 Customer Insights hangulatelemzési modellt kínál az ügyfelek visszajelzéséhez, amely lehetővé teszi a szervezetek számára, hogy pontosabban és alacsonyabb költséggel elemezzék adataikat.

A hangulatelemzés lehetővé teszi az ügyfél hangulatának szintetizálását és az üzleti szempontok azonosítását a fejlesztési lehetőségekként. Ez a Customer Insights funkció segít megérteni, hogy mi működik jól, és mit kell kezelnie. Összpontosítson a legrelevánsabb és leghatásosabb üzleti területekre, hogy javítsa ügyfelei élményét. Végső soron segíthet olyan üzleti tevékenységek ösztönzésében, amelyek lehetővé teszik a magas ügyfél-elégedettséget és hűséget eredményező élményeket.

## <a name="overview"></a>Áttekintés

A hangulatelemzési funkció ügyfélazonosítónként két származtatott betekintést hoz létre. A hangulat pontszám (-5-től 5-ig) és az alkalmazandó üzleti szempontok (üzleti területek) listája együttesen segít jobban megérteni az ügyfelek visszajelzéseit. 

Ezek az információk a következő eredmények elérésében segíthetnek: 
- Áttekintést kaphat a márkával vagy szervezettel kapcsolatos vásárlói hangulatról
- Azonosítsa a negatív hangulatú ügyfeleket, hogy összpontosítsa kampányait és elkötelezettségeit, és optimalizálja a magasabb megtérülést  
- Az üzleti szempontok azonosítása az ügyfelek által rámutatott kérdésekkel  
- Szegmentálja az ügyfeleket a hangulatuk alapján, hogy személyre szabott kampányokat futtasson célzott értékesítési, marketing és támogatási erőfeszítésekkel
- Optimalizálja az üzleti műveleteket az ügyfelek által említett aggodalomra okot adó területek vagy lehetőségek kezelésével
- Ismerje fel a jól teljesítő üzleti szempontokat, és jutalmazza a boldog ügyfeleket hűség- és promóciós programokon keresztül

Annak érdekében, hogy megbízhat a modellek eredményeiben, átlátható információkat nyújtunk arról, hogy a modellek hogyan hoznak döntéseket. Kap egy listát azokról a szavakról, amelyek befolyásolták a modellek azon döntését, hogy egy adott hangulati pontszámot vagy üzleti szempontot rendelnek a visszajelzési megjegyzésekhez.  

Két **természetes nyelvi feldolgozás (NLP) modellt** használunk: Az első minden visszajelzési megjegyzéshez hangulati pontszámot rendel. A második modell minden visszajelzést összekapcsol az összes vonatkozó üzleti szemponttal. A modelleket a közösségi média, a kiskereskedelem, az étterem, a fogyasztási cikkek és az autóipar forrásaiból származó nyilvános adatok alapján képzik.    
  
A modell előre meghatározott üzleti szempontjai a visszajelzési adatokhoz a következők:
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
> Jelenleg csak az angol ügyfelek visszajelzéseinek hangulatelemzését támogatjuk. A jövőben több nyelvet is támogatni fognak. Ha más nyelveken tölt fel visszajelzést, a modell továbbra is visszaadja az eredményeket. Ezek az eredmények azonban nem lesznek pontosak. 

## <a name="prerequisites"></a>Előfeltételek

A hangulatelemzés az adategyesítési folyamaton átesett [szöveges visszajelzési adatokon alapul](data-unification.md). Javasoljuk, hogy [a visszajelzési adat entitásokat előzetesen állítsa be szemantikai típusú tevékenységi entitásként](map-entities.md#select-primary-key-and-semantic-type-for-attributes) (Visszajelzés típusa). 

A hangulatelemzési modell konfigurálásához legalább [közreműködő engedélyre](permissions.md) van szükség.

A Customer Insights egyetlen modellfutothoz akár 10 millió visszajelzési rekordot is feldolgozhat. A modell legfeljebb 128 szót képes elemezni a visszajelzési megjegyzéseket. Ha egy visszajelzés hosszabb, az elemzés csak az első 128 szót veszi figyelembe.

### <a name="data-requirements"></a>Adatkövetelmények
  
A következő adatattribútumok szükségesek:
- Egyesített ügyfélazonosító (UCID), amely a szöveges visszajelzési adatrekordokat egy adott ügyféllel egyezteti. Ez az azonosító az [adategyesítési folyamat](data-unification.md) eredménye.
- Visszajelzés azonosítója
- Visszajelzési időbélyegző
- Visszajelzés szövege   

> [!TIP]
> A hangulatelemzéshez az ügyfelek szöveges visszajelzése szükséges. Jelenleg csak egy visszajelzési entitás konfigurálható. Ha több visszajelzési entitás van, az adatbetöltés megkezdése előtt egyesülhet.Power Query

## <a name="configure-a-sentiment-analysis"></a>Hangulatelemzés konfigurálása 

1. A Customer Insights szolgáltatásban lépjen az **Intelligencia** > **Előrejelzések** részre.

1. **Az Ügyfél hangulatelemzési** csempén válassza a Modell használata **lehetőséget**.

1. **Az Ügyfél hangulatelemzés (betekintő)** ablaktáblában válassza az Első lépések **lehetőséget**.

1. **A Modellnév** lépésben adjon meg egy **nevet** az elemzéshez. 

1. Adja meg az **Üzleti szempont kimeneti entitás nevét** és a Sentiment pontszám kimeneti entitás nevét **, majd válassza a** Tovább **lehetőséget**.

1. A Kötelező adatok **lépésben válassza az** Adatok **hozzáadása lehetőséget**.

   :::image type="content" source="media/sentiment-add-data.png" alt-text="Adatáramlás hozzáadása a hangulatelemzési modellhez.":::

1. **Az Adatok** hozzáadása ablaktáblán válassza ki a visszajelzés **szemantikai típust** a listából.

   :::image type="content" source="media/sentiment-add-feedback-activities.png" alt-text="Konfigurációs lépés a hangulatelemzéshez való visszajelzési tevékenységek kiválasztásához.":::

1. Válassza ki a hangulatelemzéshez használni kívánt tevékenységeket, majd válassza a Tovább **lehetőséget**.
 
1. Rendelje hozzá az adatok attribútumait a modellattribútumokhoz. A beállítások alkalmazásához válassza a Mentés **lehetőséget**. 

1. Megjelenik az adatleképezés állapota. A folytatáshoz válassza a **Tovább** lehetőséget. 

1. **A Modell részleteinek** áttekintése lépésben ellenőrizze a hangulatelemzés konfigurációját. Visszatérhet a előrejelzés konfiguráció bármely részéhez. Az elemzés elindításához válassza **a Mentés és futtatás** lehetőséget. 

   :::image type="content" source="media/sentiment-model-review-config.png" alt-text="Tekintse át az összes konfigurált elemet megjelenítő hangulati modell lépését.":::

1. A konfigurációs élmény elhagyásához válassza a Kész **lehetőséget**. A folyamat a felhasznált adatok mennyiségétől függően több órát is igénybe vehet. 

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
- **Utolsó frissítés**: Az a dátum, amikor a előrejelzés frissült, a kimeneti entitást eredményezi.

## <a name="manage-sentiment-analysis"></a>Hangulatelemzés kezelése

Optimalizálhatja, elháríthatja, frissítheti vagy törölheti az előrejelzéseket. Tekintse át a bemeneti adatok használhatósági jelentését, hogy megtudja, hogyan lehet egy előrejelzés gyorsabb és megbízhatóbb. További tudnivalókért lásd: [Előrejelzések kezelése](manage-predictions.md).

## <a name="review-analysis-results"></a>Az elemzési eredmények áttekintése
 
1. Nyissa meg az **Intelligencia** > **Előrejelzések** menüt, és válassza ki a **Saját előrejelzések** lapot. 
1. Válassza ki annak a előrejelzés a nevét, amelyhez az eredményeket át szeretné tekinteni. Ebben az esetben válassza ki az áttekinteni kívánt hangulatelemzést. 

### <a name="summary-tab"></a>Összegzés lap

Az eredmények oldalon négy elsődleges adatszakasz található. 

- **Átlagos hangulati pontszám**: Segít megérteni az összes ügyfél általános hangulatát. A hangulati pontszámok három kategóriába sorolhatók: 
  1.    Negatív (-5 > 2)
  2.    Semleges (-1 > 1)
  3.    Pozitív (2 > 5) 
  
  :::image type="content" source="media/overall-customer-sentiment.png" alt-text="Az általános ügyfélhangulat vizuális ábrázolása.":::

- **Az ügyfelek megoszlása hangulati pontszám** szerint: Az ügyfelek negatív, semleges és pozitív csoportokba vannak kategorizálva hangulati pontszámaik alapján. Vigye az egérmutatót a hisztogram sávjai fölé az ügyfelek számának és az egyes csoportok átlagos hangulati pontszámának megtekintéséhez. Ezek az adatok segíthetnek [az ügyfelek](segments.md) szegmenseinek létrehozásában a hangulati pontszámaik alapján.  

  :::image type="content" source="media/distribution-customer-sentiment.png" alt-text="oszlopdiagram a vásárlói hangulatot mutatja a három hangulatcsoportban.":::

- **Átlagos hangulati pontszám idővel**: Az ügyfelek hangulata idővel változhat. Trendeket biztosítunk ügyfelei érzéseiben az adatok időtartományában. Ez a nézet segíthet felmérni a szezonális promóciók, termékbemutatók vagy más időhöz kötött beavatkozások hatását az ügyfelek hangulatára. Tekintse meg a grafikont a legördülő menü érdeklődési évének kiválasztásával. 

  :::image type="content" source="media/sentiment-score-over-time.png" alt-text="előzménydiagram az idő múlásával a hangulat pontszámot vonalként képviselte.":::
 
- **Hangulat az üzleti szempontok között**: Ez a táblázat felsorolja az átlagos hangulatot az üzleti szempontok között. Segíthet felmérni, hogy vállalkozásának mely aspektusai elégítik ki az ügyfeleket vagy azokat a szempontokat, amelyek nagyobb figyelmet igényelnek. Azok a visszajelzési rekordok, amelyek nem igazodnak a támogatott üzleti szempontok egyikéhez sem, az Egyéb **kategóriába** tartoznak. A táblázat alapértelmezés szerint betűrendben van rendezve. A rendezést táblázatfej kiválasztásával módosíthatja.

  :::image type="content" source="media/sentiment-across-business-aspects.png" alt-text="A kapcsolódó hangulatérték kapcsolatos üzleti szempontok listája és az azt említő ügyfelek száma.":::
 
  Válassza ki egy üzleti szempont nevét, ha további információkat szeretne látni arról, hogyan azonosítja az üzleti szempontot a modell. Az ablaktáblán két rész található: 

  - **Befolyásos szavak**: Megmutatja azokat a legfontosabb szavakat, amelyek befolyásolták az AI-modell üzleti szempontjának azonosítását az ügyfelek visszajelzéseiben. 
    **Sértő szavak** megjelenítése: Lehetővé teszi sértő szavak felvétele az eredeti ügyfél-visszajelzési adatok listájára. Alapértelmezés szerint ki van kapcsolva.  A sértő szómaszkolást AI modell hajtja, és előfordulhat, hogy nem észleli az összes sértő szót. Folytatjuk az osztályozó iterálását és képzését az optimális teljesítmény érdekében. Ha olyan sértő szót észlel, amelyet nem szűrtek a várt módon, tudassa velünk. 
    
    :::image type="content" source="media/offensive-words-sentiment.png" alt-text="A sértő szavak megjelenítésére vagy elrejtésére váltóval ellátott befolyásos szavak listája.":::
 
  - **Visszajelzési minták**: Megjeleníti a tényleges visszajelzési rekordokat az adatokban. A szavak színkódoltak az üzleti szempont azonosítására gyakorolt hatásuk szerint. 


### <a name="influential-words-analysis-tab"></a>Befolyásos szavak elemzése lap

Három részből áll, amelyek elmagyarázzák, hogyan működik a hangulatmodell.
  
1. **A pozitív hangulathoz** hozzájáruló legfontosabb szavak: Azokat a legfontosabb szavakat mutatja, amelyek befolyásolták az AI modell pozitív hangulatának azonosítását az ügyfelek visszajelzéseiben.  
2. **A negatív hangulathoz** hozzájáruló legfontosabb szavak: Olyan legfontosabb szavakat mutat, amelyek befolyásolták az AI modell negatív hangulatának azonosítását az ügyfelek visszajelzéseiben.  
3. **Visszajelzési minták**: Tényleges visszacsatolási rekordokat mutat, egyet negatív hangulattal és egy pozitív hangulattal. A visszajelzési rekordokban szereplő szavakat a hozzárendelt hangulati pontszámhoz való hozzájárulásuk szerint emelik ki. A pozitív hangulati pontszámhoz hozzájáruló szavak zöld színnel vannak kiemelve. A negatív pontszámhoz hozzájáruló szavak pirossal vannak kiemelve.
   Válassza a **Továbbiak** lehetőséget, ha további visszajelzésmintákat szeretne betölteni, amelyek további információkat és kontextust biztosítanak a hangulati modell működéséről.
   
   :::image type="content" source="media/sentiment-feedback-samples.png" alt-text="Példák az ügyfelek visszajelzéseinek hangulatelemzésére.":::
 
**Sértő szavak** megjelenítése: Lehetővé teszi sértő szavak felvétele az eredeti ügyfél-visszajelzési adatok listájára. Alapértelmezés szerint ki van kapcsolva.  A sértő szómaszkolást AI modell hajtja, és előfordulhat, hogy nem észleli az összes sértő szót. Folytatjuk az osztályozó iterálását és képzését az optimális teljesítmény érdekében. Ha olyan sértő szót észlel, amelyet nem szűrtek a várt módon, tudassa velünk. 

## <a name="act-on-analysis-results"></a>Az elemzési eredményekről szóló törvény

A modell eredményoldalának tetején található Szegmensek **létrehozása lehetőséget választva** egyszerűen elkezdheti az ügyfelek új szegmenseinek létrehozását a hangulatelemzési eredmények oldaláról.

:::image type="content" source="media/create-segment-model.png" alt-text="Parancssor előrejelzés modellek beállításaival.":::
 
## <a name="potential-bias"></a>Lehetséges torzítás

Mint minden olyan funkciónál, amely prediktív mesterséges intelligenciát használ, tisztában kell lennie az ügyfelek hangulatának előrejelzéséhez használt adatok lehetséges elfogultságával. Ha például csak digitálisan gyűjt visszajelzést, akkor kihagyhatja az olyan ügyfelek visszajelzéseit, akik elsősorban személyesen folytatnak üzleti tevékenységet Önnel, ami befolyásolhatja a funkció kimenetét.

Mivel ez a funkció automatizált eszközöket használ az adatok értékelésére és az ezen adatokon alapuló előrejelzések értékelésére, ezért képes profilalkotási módszerként használni, mivel ezt a kifejezést az általános adatvédelmi rendelet ("GDPR") határozza meg. A szolgáltatásnak az adatok feldolgozására való használatára a GDPR vagy más törvények vagy előírások vonatkozhatnak. Ön felelős annak biztosításáért, hogy az Ön használata – beleértve a Dynamics 365 Customer Insights hangulatelemzést is – megfeleljen az összes vonatkozó törvénynek és rendeletnek, beleértve a magánéletre, a személyes adatokra, a biometrikus adatokra, az adatvédelemre és a kommunikáció titkosságára vonatkozó törvényeket is.

[!INCLUDE[footer-include](../includes/footer-banner.md)]

