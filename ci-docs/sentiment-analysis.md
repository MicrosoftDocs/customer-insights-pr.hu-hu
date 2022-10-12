---
title: Hangulatelemzés az ügyfelek visszajelzéseihez (előzetes verzió)
description: Ismerje meg, hogyan használhatja a hangulatelemzési modellt az ügyfelek visszajelzésein a Dynamics 365 Customer Insights.
ms.date: 09/14/2022
ms.subservice: audience-insights
ms.reviewer: mhart
ms.topic: conceptual
author: wmelewong
ms.author: wameng
manager: shellyha
ms.openlocfilehash: 61ce9fb18efa6152dddb2e31f4fd0366a31ac2c7
ms.sourcegitcommit: be341cb69329e507f527409ac4636c18742777d2
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/30/2022
ms.locfileid: "9610469"
---
# <a name="analyze-sentiment-in-customer-feedback-preview"></a>Hangulat elemzése az ügyfelek visszajelzéseiben (előzetes verzió)

A hangulatelemzés lehetővé teszi az ügyfelek hangulatának szintetizálását és az üzleti szempontoknak a fejlesztés lehetőségként való azonosítását. Ez a Customer Insights funkció segít megérteni, hogy mi működik jól, és mivel kell foglalkoznia. Segíthet olyan üzleti műveletek ösztönzésében, amelyek olyan élményeket tesznek lehetővé, amelyek magas ügyfél-elégedettséget és lojalitást eredményeznek.

## <a name="overview"></a>Áttekintés

A hangulatelemzési funkció ügyfél-azonosítónként két származtatott betekintést hoz létre. Hangulati pontszám (-5-től 5-ig) és az alkalmazható üzleti szempontok (üzleti területek) listája, amelyek együttesen segítenek jobban megérteni az ügyfelek visszajelzéseit.

Ez az elemzés a következőkben segít:
- Áttekintést kaphat az ügyfelek márkával vagy szervezettel kapcsolatos hangulatáról
- Azonosítsd a negatív hangulattal rendelkező ügyfeleket, hogy a kampányaidra és az aktivitásaidra összpontosíts, és optimalizálj a magasabb hozam érdekében  
- Azonosítsa az üzleti szempontokat az ügyfelek által kiemelt problémákkal  
- Szegmentálja az ügyfeleket a hangulatuk alapján, hogy személyre szabott kampányokat futtasson célzott értékesítési, marketing- és támogatási erőfeszítésekkel
- Optimalizálja az üzleti műveleteket az ügyfelek által említett aggodalomra okot adó területek vagy lehetőségek kezelésével
- Ismerje fel a jól teljesítő üzleti szempontokat, és jutalmazza a boldog ügyfeleket hűség- és promóciós programokkal

A modell azoknak a szavaknak a listáját tartalmazza, amelyek befolyásolták a modell azon döntését, hogy egy adott hangulati pontszámot vagy üzleti szempontot rendel a visszajelzési megjegyzésekhez.  

Két **természetes nyelvi feldolgozási (NLP) modellt** használunk: Az első minden visszajelzési megjegyzéshez hangulati pontszámot rendel. A második modell minden visszajelzést az összes vonatkozó üzleti szemponthoz társít. A modelleket a közösségi média, a kiskereskedelem, az éttermek, a fogyasztási cikkek és az autóipar forrásaiból származó nyilvános adatok alapján képzik.
  
A modellnek a visszajelzési adatokhoz társítandó előre meghatározott üzleti szempontjai a következők:
- Fiókkezelés
- Pénztár és fizetés
- Ügyfélszolgálat
- Bolti átvétel
- Csomagolás szállítása és visszakeresése
- Előrendelés
- Ár
- Adatvédelem és biztonság
- Promóciók és jutalmak
- Nyugta és garancia
- Adatcsere visszaküldése és visszavonása
- Teljesítési pontosság
- Webhely/alkalmazás minősége

> [!NOTE]
> Jelenleg csak az angol ügyfelek visszajelzéseivel kapcsolatos hangulatelemzést támogatjuk. A jövőben több nyelvet is támogatni fogunk. Ha más nyelveken is feltölti a visszajelzést, a modell továbbra is eredményeket ad vissza. Ezek az eredmények azonban nem lesznek pontosak.

## <a name="prerequisites"></a>Előfeltételek

- Legalább [közreműködő engedélyek](permissions.md)
- [Egyesített](data-unification.md) szöveges visszajelzési adatok. Javasoljuk, hogy [a visszajelzési adatentitásokat szemantikai típusú tevékenységentitásokként](map-entities.md#select-primary-key-and-semantic-type-for-attributes) konfigurálja (Visszajelzés típusa).
- Egyesített ügyfél-azonosító (UCID) az adatok egyesítéséből, hogy a szöveges visszajelzési adatrekordokat egy adott ügyféllel egyeztesse.
- Visszajelzés azonosítója
- Visszajelzési időbélyegző
- Visszajelzés szövege

A Customer Insights akár 10 millió visszajelzési rekordot is képes feldolgozni egyetlen modellfuttatáshoz. A modell legfeljebb 128 szó képes elemezni a visszacsatolási megjegyzéseket. Ha egy visszajelzési megjegyzés hosszabb, az elemzés csak az első 128 szót veszi figyelembe.

> [!NOTE]
> Csak egy visszajelzési entitás konfigurálható. Ha több visszajelzési entitás van, egyesítse őket az Power Query adatbetöltés előtt.

## <a name="configure-a-sentiment-analysis"></a>Hangulatelemzés konfigurálása

1. Ugrás az Intelligencia-előrejelzések **oldalra** > **·**.

1. A Létrehozás **lapon válassza a** Modell **használata lehetőséget** az **Ügyfélhangulat-elemzés (előzetes verzió)** csempén.

1. Válassza az **Első lépések** lehetőséget.

1. **Nevezze el** az elemzést, és adja meg az **Üzleti szempont kimeneti entitás nevét** és a **Hangulati pontszám kimeneti entitás nevét**.

1. Válassza a **Következő** lehetőséget.

1. Válassza az Adatok hozzáadása lehetőséget **az ügyfelek visszajelzéseihez** **.**

1. Válassza ki a visszajelzési adatokat tartalmazó visszajelzés **szemantikai tevékenységtípust**. Ha a tevékenység nincs beállítva, válassza ki **itt**, és hozza létre.

   :::image type="content" source="media/sentiment-add-feedback-activities.png" alt-text="Konfigurációs lépés a visszajelzési tevékenységek kiválasztásához a hangulatelemzéshez.":::

1. Válassza ki a hangulatelemzéshez használni kívánt tevékenységeket, majd válassza a Tovább **lehetőséget**.

1. Leképezheti az adatok attribútumait a modellattribútumokra. 

1. Válassza a **Mentés** parancsot.

1. Válassza a **Következő** lehetőséget. Az **Áttekintés és futtatás** lépés megjeleníti a konfiguráció összegzését, és lehetőséget biztosít a módosítások elvégzésére az elemzés létrehozása előtt.

1. Válassza a Szerkesztés **lehetőséget** az áttekintéshez és a módosítások elvégzéséhez szükséges lépések bármelyikénél.

1. Ha elégedett a választásokkal, válassza a Mentés és futtatás **lehetőséget** a modell futtatásának megkezdéséhez. Válassza a **Kész** lehetőséget. A **Saját előrejelzések** lap a előrejelzés létrehozásakor jelenik meg. A folyamat – az előrejelzésben használt adatok mennyiségétől függően – több óráig is tarthat.

[!INCLUDE [progress-details](includes/progress-details-pane.md)]

## <a name="view-analysis-results"></a>Elemzési eredmények megtekintése

1. Ugrás az Intelligencia-előrejelzések **oldalra** > **·**.

1. **Az Előrejelzéseim** lapon válassza ki a megtekinteni kívánt előrejelzés.

Az eredményeknek két lapja van.

### <a name="sumary-tab"></a>Összegzés lap

Az eredmények oldalán belül az adatoknak négy elsődleges szakasza van.

- **Átlagos hangulati pontszám**: A hangulati pontszámok segítenek megérteni az összes ügyfél általános hangulatát.
  - **Negatív** (-5 > 2)
  - **Semleges** (-1 > 1)
  - **Pozitív** (2 > 5)
  
  :::image type="content" source="media/overall-customer-sentiment.png" alt-text="Az általános ügyfélhangulat vizuális ábrázolása.":::

- **Az ügyfelek megoszlása hangulati pontszámok** szerint: Az ügyfeleket negatív, semleges és pozitív csoportokba soroljuk a hangulati pontszámaik alapján. Vigye az egérmutatót a hisztogram sávjai fölé az egyes csoportok vevőinek számához és átlagos hangulati pontszámához. Ezek az adatok segíthetnek az [ügyfelek](prediction-based-segment.md) szegmenseinek létrehozásában a hangulati pontszámaik alapján.  

  :::image type="content" source="media/distribution-customer-sentiment.png" alt-text="oszlopdiagram mutatja az ügyfelek hangulatát a három hangulatcsoportban.":::

- **Átlagos hangulati pontszám az idő múlásával**: Az ügyfelek hangulata idővel változhat. Az ügyfelek hangulatának trendjeit az adatok időtartományára vonatkozóan biztosítjuk. Ez a nézet segít felmérni a szezonális promóciók, termékbevezetések vagy más időhöz kötött beavatkozások hatását az ügyfelek hangulatára. Tekintse meg a grafikont az érdeklődésre számot tartó év kiválasztásával a legördülő menüből.

  :::image type="content" source="media/sentiment-score-over-time.png" alt-text="előzménydiagram, hogy a hangulati pontszám az idő múlásával egy sorként jelenik meg.":::

- **Hangulat az üzleti szempontok között: Az üzleti szempontok** közötti átlagos hangulat segít felmérni, hogy vállalkozásának mely aspektusai elégítik ki már az ügyfeleket, vagy igényelnek nagyobb figyelmet. Azok a visszajelzési rekordok, amelyek nem igazodnak a támogatott üzleti szempontok egyikéhez sem, az Egyéb **kategóriába** vannak sorolva. Rendezze az adatokat bármelyik oszlop kiválasztásával.

  :::image type="content" source="media/sentiment-across-business-aspects.png" alt-text="Az üzleti szempontok listája a kapcsolódó hangulatérték és az azt megemlítő ügyfelek száma.":::

  Válassza ki egy üzleti szempont nevét annak megtekintéséhez, hogy a modell hogyan azonosítja az üzleti szempontokat:

  - **Befolyásos szavak**: A legfontosabb szavak, amelyek befolyásolták az AI-modell egy üzleti szempont azonosítását az ügyfelek visszajelzéseiben.
    **Sértő szavak** megjelenítése: Lehetővé teszi, hogy sértő szavakat vegyen fel a listába az eredeti ügyfél-visszajelzési adatokból. Alapértelmezés szerint ki van kapcsolva.  A sértő szómaszkolást egy AI-modell hajtja végre, és előfordulhat, hogy nem észlel minden sértő szót. Ha olyan sértő szót észlel, amelyet nem a várt módon szűrtek, tudassa velünk.

    :::image type="content" source="media/offensive-words-sentiment.png" alt-text="A befolyásos szavak listája a kapcsolóval a sértő szavak megjelenítéséhez vagy elrejtéséhez.":::

  - **Visszajelzési minták**: Tényleges visszajelzési rekordok az adatokban. A szavakat az üzleti szempont azonosítására gyakorolt hatásuk szerint színkódolják.

### <a name="influential-words-analysis-tab"></a>Befolyásos szavak elemzése lap

A további információknak három szakasza van, amelyek elmagyarázzák, hogyan működik a hangulatmodell.
  
- **A pozitív hangulathoz** hozzájáruló legfontosabb szavak: A legfontosabb szavak, amelyek befolyásolták az AI-modell pozitív hangulatának azonosítását az ügyfelek visszajelzéseiben.  

- **A negatív hangulathoz** hozzájáruló legfontosabb szavak: A legfontosabb szavak, amelyek befolyásolták az AI-modell negatív hangulatának azonosítását az ügyfelek visszajelzéseiben.

- **Visszajelzési minták**: Tényleges visszajelzési rekordok, amelyek negatív hangulattal és pozitív érzéssel rendelkeznek. A visszajelzési rekordokban szereplő szavakat a hozzárendelt hangulati pontszámhoz való hozzájárulásuknak megfelelően emeljük ki. A pozitív hangulati pontszámhoz hozzájáruló szavakat zöld színnel emeljük ki. A negatív pontszámhoz hozzájáruló szavak pirossal vannak kiemelve.
   Válassza a Továbbiak **megtekintése lehetőséget** további visszajelzési minták betöltéséhez.
  
   :::image type="content" source="media/sentiment-feedback-samples.png" alt-text="Példák az ügyfelek visszajelzéseinek hangulatelemzésére.":::

**Sértő szavak** megjelenítése: Lehetővé teszi, hogy sértő szavakat vegyen fel a listába az eredeti ügyfél-visszajelzési adatokból. Alapértelmezés szerint ki van kapcsolva.  A sértő szómaszkolást egy AI-modell hajtja végre, és előfordulhat, hogy nem észlel minden sértő szót. Ha olyan sértő szót észlel, amelyet nem a várt módon szűrtek, tudassa velünk.

## <a name="act-on-analysis-results"></a>Az elemzési eredményekre vonatkozó intézkedés

Ha új szegmenseket szeretne létrehozni az ügyfelekről a hangulatelemzés eredményeiből, válassza a Szegmensek **létrehozása lehetőséget** a modell eredményoldalának tetején.

## <a name="potential-bias"></a>Lehetséges elfogultság

Mint minden olyan funkció esetében, amely prediktív mesterséges intelligenciát használ, az ügyfelek hangulatának előrejelzésére használt adatokban is lehetnek potenciális elfogultságok. Ha például csak digitálisan gyűjtesz visszajelzést, előfordulhat, hogy lemaradsz az olyan ügyfelek visszajelzéseiről, akik elsősorban személyesen folytatnak üzleti tevékenységet veled, ami hatással van a funkció kimenetére.

Mivel ez a funkció automatizált eszközöket használ az adatok értékelésére és az adatokon alapuló előrejelzések készítésére, ezért képes profilalkotási módszerként használni, mivel ezt a kifejezést az általános adatvédelmi rendelet ("GDPR") határozza meg. A szolgáltatásnak az adatok feldolgozására való használatára a GDPR vagy más törvények vagy előírások vonatkozhatnak. Ön felelős annak biztosításáért, hogy az Ön általi használat, beleértve a Dynamics 365 Customer Insights hangulatelemzést is, megfeleljen az összes vonatkozó törvénynek és rendeletnek, beleértve a magánéletre, a személyes adatokra, a biometrikus adatokra, az adatvédelemre és a kommunikáció titkosságára vonatkozó törvényeket is.

[!INCLUDE [footer-include](includes/footer-banner.md)]

