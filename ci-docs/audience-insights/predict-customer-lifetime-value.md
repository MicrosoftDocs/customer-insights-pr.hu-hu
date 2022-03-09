---
title: Ügyfélélettartam érték (CLV) előrejelzése
description: Az aktív ügyfelek jövőbeli bevételi lehetőségeinek előrejelzése a jövőre vonatkozóan.
ms.date: 02/05/2021
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: m-hartmann
ms.author: wameng
manager: shellyha
searchScope:
- ci-predictions
- ci-create-prediction
- ci-custom-models
- customerInsights
ms.openlocfilehash: 07790604b06f21095a9220a6f57727cac80789c5
ms.sourcegitcommit: 73cb021760516729e696c9a90731304d92e0e1ef
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/25/2022
ms.locfileid: "8355792"
---
# <a name="customer-lifetime-value-clv-prediction"></a>Ügyfélélettartam érték (CLV) előrejelzése

Olyan potenciális érték (bevétel) előrejelzése, amit az egyes aktív ügyfelek egy megadott jövőbeli időszak során behoznak a vállalatba. Ez a funkció segíthet különböző célok elérésében: 
- Értékes ügyfelek azonosítása és ezen információ feldolgozása
- Stratégiai ügyfélszegmenseket hozhat létre azok potenciális értéke alapján, hogy célzott értékesítési, marketing- és támogatási erőfeszítésekkel személyre szabott kampányokat futtathasson
- A termékfejlesztés irányítása az ügyfelek értékét fokozó funkciókra összpontosítva
- Értékesítési és marketingstratégia optimalizálása és a költségkeretek pontosabb felosztásához az ügyfelek eléréséhez
- A nagy értékű ügyfelek felismerése és jutalmazása a hűség- és jutalmazási programokkal 

## <a name="prerequisites"></a>Előfeltételek

Az indulás előtt gondolja át a CLV mit jelent a vállalkozása számára. Jelenleg a tranzakcióalapú CLV-előrejelzést támogatjuk. Az ügyfél becsült értéke az üzleti tranzakciók előzményein alapul. Előrejelzés létrehozáshoz előrejelzés rendelkeznie kell legalább [Közreműködő](permissions.md) engedélyekkel.

Mivel a CLV-modell konfigurálása és futtatása nem igényel időt, érdemes létrehozni több olyan modellt, amelyek eltérő bemeneti beállításokat tartalmaznak, és a modellek eredményeivel összehasonlítva láthatja, hogy melyik az üzleti igényeknek leginkább megfelelő modellforgatókönyv.

###  <a name="data-requirements"></a>Adatkövetelmények

A következő adatok szükségesek, és ha nem kötelező megadni, akkor ajánlott a modell teljesítményének növelése érdekében. Minél több adatot képes feldolgozni a modell, annál pontosabb lesz előrejelzés. Ezért javasoljuk, hogy amennyiben rendelkezésre állnak, több ügyfélaktivitási adatot töltsön be.

- Ügyfélazonosító: Egyedi azonosító az egyes ügyfelekhez tranzakciók egyeztetéshez

- Tranzakcióelőzmények: A tranzakciók előzménynaplója a szemantikus adatséma alatt
    - **Tranzakcióazonosító**: Az egyes tranzakciók egyedi azonosítója
    - **Tranzakció dátuma**: Dátum, lehetőség szerint az egyes tranzakciók időbélyegzője
    - **Tranzakció összege**: Az egyes tranzakciók pénzben megadott értéke (például bevétel vagy fedezeti mutató)
    - **Visszatérítésekhez hozzárendelt címke** (nem kötelező): Olyan logikai érték, amely azt jelzi, hogy a tranzakció visszatérítés-e 
    - **Termékazonosító** (nem kötelező): A tranzakcióban érintett termék termékazonosítója

- További adatok (nem kötelező), például
    - Webes tevékenységek: webhelylátogatási előzmények, e-mail előzmények
    - Hűségtevékenységek: a hűségpontok egyenlege és beváltási előzmények
    - Ügyfélszolgálati napló, ügyfélszolgálati hívás panasz vagy visszaküldés előzményei
- Adatok az ügyfél tevékenységéről (nem kötelező):
    - Az azonos típusú tevékenységek megkülönböztetésére szolgáló tevékenységazonosítók
    - A tevékenységek ügyfelekhez rendelésére szolgáló ügyfél-azonosítók
    - A tevékenység adatai a tevékenység nevét és dátumát tartalmazzák
    - A tevékenységekhez tartozó szemantikus adatséma az alábbiakat tartalmazza: 
        - **Elsődleges kulcs**: Egy tevékenység egyedi azonosítója
        - **Időbélyegző**: Az elsődleges kulcs által azonosított esemény dátuma és időpontja
        - **Esemény (tevékenység neve)**: A használni kívánt esemény neve
        - **Részletek (összeg vagy érték)**: Az ügyféltevékenység részletei

- Javasolt adatjellemzők:
    - Elegendő korábbi adat: Legalább egy évnyi tranzakciós adat. A CLV egy évre való előrejelzéséhez lehetőség szerint 2-3 évnyi tranzakciós adat szükséges.
    - Több vásárlás ügyfélenként: Ideális esetben ügyfélazonosítónként legalább 2-3 tranzakció, lehetőség szerint eltérő dátummal.
    - Ügyfelek száma: Legalább 100 egyedi ügyfél; lehetőség szerint 10 000-nél több ügyfél. A modell nem működik 100-nál kevesebb ügyfél esetén, illetve ha nem áll rendelkezésre elegendő előzményadat.
    - Adatok teljessége: A bemeneti adatok kötelező mezőiben legfeljebb az értékek 20%-a hiányzik.   

> [!NOTE]
> - A modellhez az ügyfelek tranzakciós előzményeire van szükség. Jelenleg csak egy tranzakcióelőzmény-entitás konfigurálható. Ha több beszerzési/tranzakciós entitás van, az adatbetöltés előtt be lehet őket Power Query őket.
> - További ügyféltevékenység-adat esetén (nem kötelező) azonban annyi ügyféltevékenység-entitást adhat hozzá, amennyit a modellel figyelembe szeretne vetetni.

## <a name="create-a-customer-lifetime-value-prediction"></a>Ügyfélélettartam-érték előrejelzésének létrehozása

1. A célközönség információin belül nyissa meg a következőt **Információk** > **Előrejelzések**.

1. Válassza az **Ügyfélélettartam értéke** csempét, és válassza a **Modell használata** lehetőséget. 

1. A Vevő élettartam értéke **ablaktáblán válassza az** Első lépések **lehetőséget**.

1. **Nevezze el ezt a modellt** és a **Kimeneti entitás nevét**, hogy megkülönböztesse őket az egyéb modellektől vagy entitásoktól.

1. Válassza a **Következő** lehetőséget.

### <a name="define-model-preferences"></a>Modellbeállítások definiálása

1. Állítsa be az **Előrejelzési időszakot**, hogy meghatározza milyen távol a jövőben szeretné előre jelezni a CLV-t.    
   Az egység alapértelmezés szerint hónapként van beállítva. Ezt módosíthatja évekre, a ha távolabbi jövőt szeretné vizsgálni.

   > [!TIP]
   > Ahhoz, hogy a pontosan előre tudja jelezni a CLV-t a beállított időszakra vonatkozóan, hasonló időszakra van szükség a korábbi adatokból. Ha például a következő 12 hónapra szeretne előrejelzést készíteni a CLV-ről, ajánlott, hogy legalább 18–24 hónap korábbi adatait használja.

1. Adja meg, hogy mit jelentenek az **Aktív ügyfelek** a vállalat számára. Állítsa be időkeretet amelyben az ügyfélnek legalább egy tranzakcióval kell rendelkeznie, hogy aktívnak minősüljön. A modell csak az aktív ügyfelek CLV-jét fogja előre jelezni. 
   - **Hagyja, hogy a modell számítsa ki a beszerzési intervallumot (ajánlott)**: A modell elemzi az adatokat, és a korábbi vásárlások alapján határoz meg egy időszakot.
   - **Intervallum manuális beállítása**: Ha egy aktív ügyfélhez specifikus üzleti definíciója van, válassza ezt a beállítást, és ennek megfelelően állítsa be az időszakot.

1. Definiálja a **Nagy értékű ügyfél** percentilisét, hogy a modell az üzleti definíciónak megfelelő eredményeket nyújtson.
    - **Modellszámítás (ajánlott)**: A modell elemzi az adatokat, és meghatározza, hogy az ügyfelek tranzakciós előzményei alapján milyen lehet az értékes ügyfél a vállalkozás számára. A modell egy (a 80/20 szabály vagy a pareto elv által inspirált) heurisztikus szabályt használ a nagy értékű ügyfelek arányának megkeresésére. Az ügyfelek százalékos értéke, amely hozzájárult a vállalat korábbi időszakban az összbevétel 80 %-ához nagy értékű ügyfélnek számít. Jellemzően 30-40%-nál kevesebb ügyfél járul hozzá az összbevétel 80%-ához. Ez a szám azonban a vállalattól és az iparágtól függően változhat.    
    - **A legaktívabb ügyfelek százalékos aránya**: A vállalat értékes ügyfeleit a legnagyobb aktív fizető ügyfelek százalékos értékeként definiálhatja. Ezzel a beállítással például a nagy értékű ügyfeleket a jövőbeli fizető ügyfelek felső 20%-aként határozhatja meg.

    Ha a vállalata más módon definiálja a nagy értékű ügyfeleket, [mondja el nekünk, szeretnének ezt megismerni](https://go.microsoft.com/fwlink/?linkid=2074172).

1. A **Tovább** gombot választva lépjen tovább a következő lépésre.

### <a name="add-required-data"></a>Szükséges adatok hozzáadása

1. A **Szükséges adatok** lépésben válassza az **Adatok hozzáadása** elemet az **Ügyféltranzakció-előzményekhez**, és válassza ki au entitást, amely biztosítja a tranzakciós/vásárlási előzmény információt, amint azok részletezésre kerültek az [előfeltételekben](#prerequisites).

1. Képezze le a szemantikai mezőket olyan attribútumokra, melyek a beszerzési előzmények entitáson belül esnek, és válassza a **Tovább** lehetőséget.

   :::image type="content" source="media/clv-add-customer-data-mapping.png" alt-text="A konfigurációs lépés képe a kötelező adatok adatattribútumainak leképezéséhez.":::
 
1. Ha az alábbi mezők nincsenek megadva, konfigurálja a kapcsolatokat beszerzési előzmények entitásából az *Ügyfél* entitáshoz, és válassza a **Mentés** lehetőséget.
    1. Válassza ki a tranzakciós előzmények entitást.
    1. Válassza a mező lehetőséget, mely azonosít egy ügyfelet a beszerzési előzmények entitásban. A mezőnek az Ügyfél entitás elsődleges ügyfél-azonosítójára kell vonatkoznia.
    1. Válassza ki azt az entitást, amely megfelel az elsődleges ügyfélentitásnak.
    1. Adjon meg egy olyan nevet, amely jól leírja a kapcsolatot.

      :::image type="content" source="media/clv-add-customer-data-relationship.png" alt-text="Az ügyfélentitással való kapcsolatot definiáló konfigurációs lépés képe.":::

1. Válassza a **Következő** lehetőséget.

### <a name="add-optional-data"></a>Nem kötelező adatok hozzáadása

A fő ügyfélinterakciókat tükröző adatok (pl. a web, ügyfélszolgálat és eseménynaplók) környezeteti adatokat ad a tranzakciós bejegyzésekhez. Az ügyféltevékenységi adatokban talált további minták javíthatják az előrejelzések pontosságát. 

1. A **További adatok (nem kötelező)** lépésben válassza az **Adatok hozzáadása** lehetőséget. Válassza az ügyfélaktivitás entitást, amely biztosítja, hogy ügyféltevékenység információja az [előfeltételekben](#prerequisites) részletezett módon kerüljön megjelenítésre.

1. Képezze le a szemantikai mezőket olyan attribútumokra, melyek az ügyféltevékenység entitáson belül esnek és válassza a **Tovább** lehetőséget.

   :::image type="content" source="media/clv-additional-data-mapping.png" alt-text="A konfigurációs lépés képe a további adatok mezőinek leképezéséhez.":::

1. Válassza ki a hozzáadni kívánt ügyféltevékenység típusának megfelelő tevékenységtípust. Válasszon a meglévő tevékenységtípusok közül, vagy vegyen fel egy új tevékenységtípust.

1. Konfigurálja az ügyféltevékenység entitásának és az *Ügyfél* entitásnak a kapcsolatát.
    
    1. Válassza ki a mezőt, amely azonosítja az ügyfelet az ügyféltevékenység táblában. Ez közvetlenül kapcsolásra kerülhet *Ügyfél* entitásának Elsődleges ügyfél-azonosítójához.
    1. Válassza ki azt az *Ügyfél* entitást, amely egyezik az elsődleges *Ügyfél* entitással.
    1. Adjon meg egy olyan nevet, amely jól leírja a kapcsolatot.

   :::image type="content" source="media/clv-additional-data.png" alt-text="Kép a konfigurációs folyamat lépéséről további adatok felvételéhez és a tevékenység konfigurálásához kitöltött példákkal.":::

1. Válassza a **Mentés** parancsot.    
    Adjon hozzá további adatokat, ha más ügyféltevékenységeket is szeretne szerepeletni.

1. Válassza a **Következő** lehetőséget.

### <a name="set-update-schedule"></a>Frissítési ütemezés beállítása

1. Az **Adatfrissítés ütemezése** lépésben adja meg, hogy milyen gyakran tanítja újra a modellt a legújabb adatok alapján. Ez a beállítás fontos, hogy frissíthesse az előrejelzéseinek pontosságát, ahogy új adat kerül betöltésre a célközönség-információkba. A legtöbb cég havonta egyszer végez újratanítást, és pontos előrejelzésekhez tud jutni.

1. Válassza a **Következő** lehetőséget.

### <a name="review-and-run-the-model-configuration"></a>A modellkonfiguráció áttekintése és futtatása

1. Az **Ellenőrizze a modell részleteit** lépésben ellenőrizze a előrejelzés konfigurációját. A megjelenített érték alatt lévő **Szerkesztés** beállítással az előrejelzési konfiguráció bármelyik részéhez visszaléphet. A folyamatjelzőből egy konfigurációs lépést is kiválaszthat.

1. Ha minden érték megfelelően van beállítva, válassza a **Mentés és futtatás** lehetőséget a modell futtatásának megkezdéséhez. A **Saját előrejelzések** lapon látható az előrejelzési folyamat állapota. A folyamat – az előrejelzésben használt adatok mennyiségétől függően – több óráig is tarthat.

## <a name="review-prediction-status-and-results"></a>Az előrejelzési állapot és eredmények áttekintése

### <a name="review-prediction-status"></a>Előrejelzési állapot áttekintése

1.  Nyissa meg az **Intelligencia** > **Előrejelzések** menüt, és válassza ki a **Saját előrejelzések** lapot.
2.  Jelölje ki az áttekinteni kívánt előrejelzést.

- **Előrejelzés neve**: Az előrejelzés neve, mely a létrehozáskor kerül megadásra.
- **Előrejelzés típusa**: Az előrejelzéshez használt model típusa
- **Kimeneti entitás**: Az előrejelzés kimenetének tárolására szolgáló entitás neve. Az ilyen nevű entitás kereséséhez válassza az **Adatok** > **Entitások** lehetőséget.
- **Várható mező**: Ez a mező csak bizonyos típusú előrejelzésekhez megadható, és nem használható az ügyféléletciklus értékének előrejelzéshez.
- **Állapot**: A futtatott előrejelzés állapota.
    - **Feldolgozási sorban**: Az előrejelzés további folyamatok befejezésére vár.
    - **Frissítés**: Az előrejelzés jelenleg fut, hogy a kimeneti entitásba kerülő eredményt hozhassa létre.
    - **Sikertelen**: Az előrejelzés lefuttatása sikertelen. [Ellenőrizze a naplókat](manage-predictions.md#troubleshoot-a-failed-prediction) a további részletekért.
    - **Sikeres**: Az Előrejelzés lefuttatása sikeresen megtörtént. Válassza a **Megtekintés** lehetőséget a függőleges három pont alatt a kiválasztott előrejelzés megtekintéséhez.
- **Szerkesztve**: Az előrejelzés konfigurációjának módosítási dátuma.
- **Legutóbbi frissítés**: A dátum, amikor az előrejelzés frissítette a kimeneti entitásban szereplő eredményeket.

### <a name="review-prediction-results"></a>Előrejelzési eredmények áttekintése

1. Nyissa meg az **Intelligencia** > **Előrejelzések** menüt, és válassza ki a **Saját előrejelzések** lapot.

1. Válassza ki előrejelzést amelynek eredményekeit szeretné átnézni.

Az eredményoldalon lévő adatok három fő részben jelennek meg.

- **A képzési modell teljesítménye**: A, B vagy C lehetséges osztályzat. Ez a osztályzat jelzi az előrejelzés teljesítményét, és segíthet annak döntésében, hogy a kimeneti entitásban tárolt eredményeket felhasználja-e. Válassza a **Tudnivalók erről a pontszámról** lehetőséget, ha jobban meg szeretné érteni az alapul szolgáló modell teljesítménymérőszáma és a végső modell teljesítményminősége származtatásának módját.
  
  :::image type="content" source="media/clv-model-score.png" alt-text="A modell pontszám információs mezője A osztályzattal":::

  A rendszer a előrejelzés konfigurálása során megadott nagy értékű ügyfelek definícióját használva felméri, hogy az AI-modell hogyan teljesített a nagy értékű ügyfelek előrejelzésében az alapmodellhez képest.    

  Az osztályzatot a következő szabályok határozzák meg:
  - **A**, ha a modell legalább 5%-kal több nagy értékű ügyfelet jelzett előre alapmodellhez képest.
  - **B**, ha a modell 0–5%-kal több nagy értékű ügyfelet jelzett előre alapmodellhez képest.
  - **C**, ha a modell pontosan kevesebb nagy értékű ügyfelet jelzett előre alapmodellhez képest.

  A **Modell minősítése** panel további részleteket tartalmaz az AI-modell teljesítményéről és az alapmodellről. Az alapmodell nem AI-alapú megközelítést alkalmaz az ügyfelek élettartamának elsődlegesen az ügyfelek által történt korábbi vásárlások alapján történő kiszámításához.     
  A CLV-értéknek az alapmodellel való kiszámításához használt szabványos képlet:    

  _**Az egyes ügyfelek CLV-értéke** = Az ügyfél által az aktív ügyfélablakban végzett átlagos havi vásárlás * A hónapok száma a CLV-előrejelzési időszakban * Az ügyfelek összesített megtartási aránya*_

  Az AI-modellt az alapmodellhez hasonlítják két teljesítménymérőszám-modell alapján.
  
  - **A nagy értékű ügyfelek előrejelzésének sikerességi aránya**

    Megtekintheti a különbséget a nagy értékű ügyfelek előrejelzését az az AI modell használatával alapmodellhez képest. A 84%-os sikeresség például azt jelenti, hogy a képzési adatokban lévő értékes ügyfelekből az AI-modellnek sikerült pontosan rögzítenie a 84%-ot. Ezután összehasonlítjuk ezt az alapmodell sikerességi arányával a relatív változás jelentéséhez. Ez az érték egy osztályzatot rendel a modellhez.

  - **Hibamutatók**
    
    Egy másik mérőszám lehetővé teszi a modell általános teljesítményének áttekintését a jövőbeli értékek előrejelzésének hibái szempontjából. A hiba felmérésére a gyök átlagos négyezetes eltérés (RMSE) mérőszámot használjuk. Az RMSE egy szabványos módja annak, hogy lemérje egy modell hibáját a kvantitatív adatok előrejelzésében. Összehasonlítják az AI modell RMSE-értékét az alapmodell RMSE-értékével, és a relatív különbség lesz jelentve.

  Az AI modell előnyben részesíti ad az ügyfeleknek a vállalat számára behozott értéknek megfelelő pontos rangsorolásában. Az utolsó modellminőség származtatáshoz tehát csak a nagy értékű ügyfeleket jóslásának sikerességi aránya használható. Az RMSE mérőszám érzékeny a kiesőkre. Olyan helyzetekben, amikor az ügyfelek kis hányadánál nagyon magas a vásárlási érték, előfordulhat, hogy az általános RMSE metrika nem ad teljes képet a modell teljesítményével kapcsolatosan.   

- **Az ügyfelek értéke percentilis szerint**: A nagy értékű ügyfelek definíciójának használatával az ügyfelek alacsony és magas értékű csoportokba vannak csoportosítva a CLV-előrejelzésük alapján, és egy diagramban jelennek meg. A hisztogram sávjaira mutatva látható az egyes csoportokban található ügyfelek száma és az adott csoport átlagos CLV-je látható. Ezek az adatok segíthetnek abban, ha szeretne [ügyfélszegmenseket létrehozni](segments.md) a CLV-előrejelzésük alapján.

- **Legbefolyásosabb tényezők**: A CLV-előrejelzés a AI-modell bemeneti adatain alapuló számos tényezőt figyelembe vesz. Az egyes tényezők fontosságát a rendszer kiszámítja a modell által létrehozott összesített előrejelzésekhez. Ezekkel a tényezőkkel ellenőrizheti az előrejelzés eredményeit. Ezek a tényezők további képet adnak a legbefolyásosabb tényezőkről is, amelyek hozzájárultak a CLV minden ügyfélre való előrejelzése során.

## <a name="manage-predictions"></a>Előrejelzések kezelése

Lehetőség van az előrejelzések optimalizálására, hibaelhárítására, frissítésére vagy törlésére. Tekintse át a bemeneti adatok használhatósági jelentését, hogy megtudja, hogyan lehet egy előrejelzés gyorsabb és megbízhatóbb. További tudnivalókért lásd: [Előrejelzések kezelése](manage-predictions.md).

[!INCLUDE[footer-include](../includes/footer-banner.md)]
