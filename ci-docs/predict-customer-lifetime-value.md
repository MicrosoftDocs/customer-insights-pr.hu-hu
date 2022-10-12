---
title: Ügyfél élettartamra vetített értékének előrejelzése (CLV)
description: Az aktív ügyfelek jövőbeli bevételi lehetőségeinek előrejelzése a jövőre vonatkozóan.
ms.date: 09/30/2022
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
ms.openlocfilehash: f27462ac327027e50e23387ac9f75a671db9a86d
ms.sourcegitcommit: be341cb69329e507f527409ac4636c18742777d2
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/30/2022
ms.locfileid: "9610377"
---
# <a name="predict-customer-lifetime-value-clv"></a>Ügyfél élettartamra vetített értékének előrejelzése (CLV)

Olyan potenciális érték (bevétel) előrejelzése, amit az egyes aktív ügyfelek egy megadott jövőbeli időszak során behoznak a vállalatba. Ez a előrejelzés a következőkben segít:

- Azonosítsa a nagy értékű ügyfeleket, és dolgozza fel ezt a betekintést.
- Stratégiai ügyfélszegmenseket hozhat létre a potenciális értékük alapján, hogy személyre szabott kampányokat futtasson célzott értékesítési, marketing- és támogatási erőfeszítésekkel.
- Irányítsa a termékfejlesztést azáltal, hogy az ügyfelek értékét növelő funkciókra összpontosít.
- Optimalizálja az értékesítési vagy marketingstratégiát, és pontosabban ossza fel a költségvetést az ügyfelek tájékoztatására.
- Ismerje fel és jutalmazza a nagy értékű ügyfeleket hűség- vagy jutalmazási programokkal.

Határozza meg, mit jelent a CLV a vállalkozása számára. Támogatjuk a tranzakcióalapú CLV előrejelzés. Az ügyfél előrejelzett értéke az üzleti tranzakciók történetén alapul. Fontolja meg több modell létrehozását különböző bemeneti beállításokkal, és hasonlítsa össze a modell eredményeit, hogy megtudja, melyik modellváltozat felel meg leginkább az üzleti igényeinek.

> [!TIP]
> Próbálja ki a CLV-előrejelzés mintaadatokkal: [Ügyfél élettartamra vetített érték (CLV) előrejelzés mintaútmutatóval](sample-guide-predict-clv.md).

## <a name="prerequisites"></a>Előfeltételek

- Legalább [közreműködő](permissions.md) engedélyek
- Legalább 100 egyedi ügyfél, lehetőleg több mint 10 000 ügyfél
- Ügyfél-azonosító, egy egyedi azonosító, amely a tranzakciókat egy adott ügyféllel egyezteti
- Legalább egyéves tranzakciós előzmények, lehetőleg két-három év. Ideális esetben ügyfél-azonosítónként legalább két-három tranzakció, lehetőleg több dátumon keresztül. A tranzakciós előzményeknek tartalmazniuk kell a következőket:
  - **Tranzakcióazonosító**: Az egyes tranzakciók egyedi azonosítója
  - **Tranzakció dátuma**: Az egyes tranzakciók dátum- vagy időbélyegzője
  - **Tranzakció összege**: Az egyes tranzakciók pénzben megadott értéke (például bevétel vagy fedezeti mutató)
  - **A visszatéréshez** rendelt címke: Logikai igaz/hamis érték, amely azt jelzi, hogy a tranzakció visszatérés-e
  - **Termékazonosító**: A tranzakcióban részt vevő termék termékazonosítója
- Az ügyfelek tevékenységére vonatkozó adatok:
  - **Elsődleges kulcs**: Egy tevékenység egyedi azonosítója
  - **Időbélyegző**: Az elsődleges kulccsal azonosított esemény dátuma és időpontja
  - **Esemény (tevékenység neve)**: A használni kívánt esemény neve
  - **Részletek (összeg vagy érték)**: Az ügyféltevékenység részletei
- További adatok, például:
  - Webes tevékenységek: Webhelylátogatási előzmények vagy e-mail előzmények
  - Hűségtevékenységek: Hűségjutalmas pontok eredményszemléletű és beváltási előzmények
  - ügyfélszolgálat napló: Szervizhívás, panasz vagy visszaküldési előzmények
  - Ügyfélprofil-információk
- Kevesebb mint 20%- ban hiányzik az értékek a kötelező mezőkből

> [!NOTE]
> Csak egy tranzakciós előzményentitás konfigurálható. Ha több beszerzési vagy tranzakciós entitás van, egyesítse őket az Power Query adatbetöltés előtt.

## <a name="create-a-customer-lifetime-value-prediction"></a>Ügyfélélettartam-érték előrejelzésének létrehozása

Válassza a Piszkozat **mentése bármikor lehetőséget** a előrejelzés piszkozatként való mentéséhez. A piszkozat előrejelzés a **Saját előrejelzések** lapon jelenik meg.

1. Ugrás az Intelligencia-előrejelzések **oldalra** > **·**.

1. A Létrehozás lapon válassza a **Modell** használata lehetőséget **az** Ügyfél élettartamának értéke **csempén.**

1. Válassza az **Első lépések** lehetőséget.

1. **Nevezze el ezt a modellt** és a **Kimeneti entitás nevét**, hogy megkülönböztesse őket az egyéb modellektől vagy entitásoktól.

1. Válassza a **Következő** lehetőséget.

### <a name="define-model-preferences"></a>Modellbeállítások definiálása

1. Állítsa be az **Előrejelzési időszakot**, hogy meghatározza milyen távol a jövőben szeretné előre jelezni a CLV-t. Az egység alapértelmezés szerint hónapként van beállítva.

   > [!TIP]
   > A CLV pontos előrejelzéséhez a beállított időszakra vonatkozóan összehasonlítható időszak előzményadatokra van szükség. Ha például a következő 12 hónapra szeretné megjósolni a CLV-t, legalább 18–24 hónapnyi előzményadattal kell rendelkeznie.

1. Állítsa be időkeretet amelyben az ügyfélnek legalább egy tranzakcióval kell rendelkeznie, hogy aktívnak minősüljön. A modell csak az aktív ügyfelek számára jósolja meg a CLV-t **·**.
   - **Hagyja, hogy a modell kiszámítsa a vásárlási intervallumot (ajánlott)**: A modell elemzi az adatokat, és az előzményvásárlások alapján meghatároz egy időtartamot.
   - **Időköz manuális** beállítása: Az aktív ügyfél definíciójának időszaka.

1. Határozza meg a nagy értékű ügyfél **percentilisét**.
    - **Modellszámítás (ajánlott)**: A modell 80/20 szabályt használ. Az ügyfelek százalékos értéke, amely hozzájárult a vállalat korábbi időszakban az összbevétel 80 %-ához nagy értékű ügyfélnek számít. Jellemzően 30-40%-nál kevesebb ügyfél járul hozzá az összbevétel 80%-ához. Ez a szám azonban a vállalattól és az iparágtól függően változhat.
    - **A legaktívabb ügyfelek** százalékos aránya: A nagy értékű ügyfelekre vonatkozó százalékos érték. Adja meg **például a 25** értéket, hogy a nagy értékű ügyfeleket a jövőbeli fizető ügyfelek felső 25%-aként határozza meg.

    Ha a vállalata más módon definiálja a nagy értékű ügyfeleket, [mondja el nekünk, szeretnének ezt megismerni](https://go.microsoft.com/fwlink/?linkid=2074172).

1. Válassza a **Következő** lehetőséget.

### <a name="add-required-data"></a>Szükséges adatok hozzáadása

1. Válassza az Adatok hozzáadása lehetőséget **az Ügyfél tranzakciós előzményeihez** **.**

1. Válassza ki a tranzakciós előzményeket tartalmazó salesorder **vagy** salesorderline **szemantikai tevékenységtípust**. Ha a tevékenység nincs beállítva, válassza ki **itt**, és hozza létre.

1. Ha a Tevékenységek **alatt** a tevékenységattribútumok szemantikailag leképeződtek a tevékenység létrehozásakor, válassza ki azokat az attribútumokat vagy entitásokat, amelyekre a számítást összpontosítani szeretné. Ha a szemantikai leképezés nem történt meg, válassza az Adatok szerkesztése **és leképezése lehetőséget**.
  
   :::image type="content" source="media/CLV-add-required.PNG" alt-text="A CLV-modellhez szükséges adatok hozzáadása":::

1. Válassza a Tovább **lehetőséget**, és tekintse át a modellhez szükséges attribútumokat.

1. Válassza a **Mentés** parancsot.

1. Adjon hozzá további tevékenységeket, vagy válassza a Tovább **lehetőséget**.

### <a name="add-optional-activity-data"></a>Opcionális tevékenységadatok hozzáadása

A fő ügyfélinterakciókat tükröző adatok (pl. a web, ügyfélszolgálat és eseménynaplók) környezeteti adatokat ad a tranzakciós bejegyzésekhez. Az ügyféltevékenységi adatokban talált további minták javíthatják az előrejelzések pontosságát.

1. Válassza az Adatok **hozzáadása lehetőséget** a Modellelemzések növelése további tevékenységadatokkal **alatt**.

1. Válassza ki a hozzáadni kívánt ügyféltevékenység típusának megfelelő tevékenységtípust. Ha a tevékenység nincs beállítva, válassza ki **itt**, és hozza létre.

1. A Tevékenységek **alatt**, ha a tevékenység attribútumai a tevékenység létrehozásakor voltak leképezve, válassza ki azokat az attribútumokat vagy entitásokat, amelyekre a számítást összpontosítani szeretné. Ha a leképezés nem történt meg, válassza a Szerkesztés **lehetőséget**, és képezze le az adatokat.

1. Válassza a Tovább **lehetőséget**, és tekintse át a modellhez szükséges attribútumokat.

1. Válassza a **Mentés** parancsot.

1. Válassza a **Következő** lehetőséget.

1. [Adjon hozzá opcionális ügyféladatokat](#add-optional-customer-data), vagy válassza a Tovább **lehetőséget**, és lépjen a [Frissítési ütemezés beállítása elemre](#set-update-schedule).

### <a name="add-optional-customer-data"></a>Opcionális ügyféladatok hozzáadása

Válasszon 18 gyakran használt ügyfélprofil-attribútum közül, amelyeket a modell bemeneteként szeretne szerepeltetni. Ezek az attribútumok személyre szabottabb, relevánsabb és gyakorlatban hasznosíthatóbb modelleredményeket eredményezhetnek az üzleti használati esetekben.

Például: Contoso Coffee előre szeretné jelezni az ügyfelek élettartamának értékét, hogy a nagy értékű ügyfeleket célozza meg az új eszpresszógépük elindításához kapcsolódó személyre szabott ajánlattal. Contoso a CLV modellt használja, és mind a 18 ügyfélprofil-attribútumot hozzáadja, hogy lássa, mely tényezők befolyásolják a legnagyobb értékű ügyfeleiket. Úgy találják, hogy az ügyfelek tartózkodási helye a legbefolyásosabb tényező ezen ügyfelek számára.
Ezen információk birtokában helyi rendezvényt szerveznek az eszpresszógép elindításához, és a helyi eladókkal együttműködve személyre szabott ajánlatokat és különleges élményt nyújtanak az eseményen. Ezen információk nélkül előfordulhat, hogy Contoso csak általános marketing e-maileket küldtek volna, és elszalasztották volna a lehetőséget, hogy személyre szabják nagy értékű ügyfeleiknek ezt a helyi szegmensét.

1. Válassza az Adatok **hozzáadása lehetőséget** a Modellelemzések növelése területen **, amely további ügyféladatokkal még tovább bővül**.

1. Az Entitás **mezőben** válassza a Customer: CustomerInsights **lehetőséget** az egyesített ügyfélprofil kiválasztásához, amely az ügyfélattribútum-adatokra van leképezve. Az **Ügyfél-azonosító** mezőben válassza **a System.Customer.CustomerId lehetőséget**.

1. Térképezzen le további mezőket, ha az adatok elérhetők az egységes ügyfélprofilokban.

   :::image type="content" source="media/clv-optional-customer-profile-mapping.png" alt-text="Példa az ügyfélprofil-adatok leképezett mezőire.":::

1. Válassza a **Mentés** parancsot.

1. Válassza a **Következő** lehetőséget.

### <a name="set-update-schedule"></a>Frissítési ütemezés beállítása

1. Válassza ki a modellt a legújabb adatok alapján történő újratanításhoz szükséges gyakoriságot. Ez a beállítás fontos az előrejelzések pontosságának frissítéséhez, mivel a rendszer új adatokat tölt be a Customer Insights szolgáltatásba. A legtöbb cég havonta egyszer végez újratanítást, és pontos előrejelzésekhez tud jutni.

1. Válassza a **Következő** lehetőséget.

### <a name="review-and-run-the-model-configuration"></a>A modellkonfiguráció áttekintése és futtatása

Az **Áttekintés és futtatás** lépés a konfiguráció összegzését jeleníti meg, és lehetőséget biztosít a módosítások elvégzésére a előrejelzés létrehozása előtt.

1. Válassza a Szerkesztés **lehetőséget** az áttekintéshez és a módosítások elvégzéséhez szükséges lépések bármelyikénél.

1. Ha elégedett a választásokkal, válassza a Mentés és futtatás **lehetőséget** a modell futtatásának megkezdéséhez. Válassza a **Kész** lehetőséget. A **Saját előrejelzések** lap a előrejelzés létrehozásakor jelenik meg. A folyamat – az előrejelzésben használt adatok mennyiségétől függően – több óráig is tarthat.

[!INCLUDE [progress-details](includes/progress-details-pane.md)]

## <a name="view-prediction-results"></a>Előrejelzés eredmények megtekintése

1. Ugrás az Intelligencia-előrejelzések **oldalra** > **·**.

1. **A Saját előrejelzések** lapon válassza ki a megtekinteni kívánt előrejelzés.

Az eredményoldalon lévő adatok három fő részben jelennek meg.

- **Betanítási modell teljesítménye**: Az A, B vagy C fokozatok jelzik a előrejelzés teljesítményét, és segíthetnek a kimeneti entitásban tárolt eredmények használatára vonatkozó döntés meghozatalában.
  
  :::image type="content" source="media/clv-model-score.png" alt-text="A modell pontszám információs mezője A osztályzattal":::

  A Customer Insights azt értékeli, hogy az AI-modell hogyan teljesített a nagy értékű ügyfelek előrejelzésében az alapmodellhez képest.

  Az osztályzatot a következő szabályok határozzák meg:
  - **A**, ha a modell legalább 5%-kal több nagy értékű ügyfelet jelzett előre alapmodellhez képest.
  - **B**, ha a modell 0–5%-kal több nagy értékű ügyfelet jelzett előre alapmodellhez képest.
  - **C**, ha a modell pontosan kevesebb nagy értékű ügyfelet jelzett előre alapmodellhez képest.
  
  Válassza a Ismerje meg ezt a pontszámot [**lehetőséget**](#learn-about-the-score) a **Modellminősítés** panel megnyitásához, amely további részleteket mutat be az AI-modell teljesítményéről és az alapmodellről. Ez segít jobban megérteni a modell mögöttes teljesítménymutatókat és azt, hogy hogyan jött létre a modell végső teljesítményosztálya. Az alapmodell nem AI-alapú megközelítést alkalmaz az ügyfelek élettartamának elsődlegesen az ügyfelek által történt korábbi vásárlások alapján történő kiszámításához.

- **Az ügyfelek értéke percentilis** szerint: Az alacsony és a nagy értékű ügyfelek diagramon jelennek meg. Vigye az egérmutatót a hisztogram sávjai fölé, hogy megtekintse az egyes csoportokban az ügyfelek számát és a csoport átlagos CLV-jét. [Igény szerint létrehozhatja az ügyfelek](prediction-based-segment.md) szegmenseit a CLV-előrejelzések alapján.
  
   :::image type="content" source="media/CLV-value-percent.png" alt-text="Az ügyfelek értéke percentilisenként a CLV modellhez":::

- **Legbefolyásosabb tényezők**: A CLV-előrejelzés a AI-modell bemeneti adatain alapuló számos tényezőt figyelembe vesz. Az egyes tényezők fontosságát a rendszer kiszámítja a modell által létrehozott összesített előrejelzésekhez. Ezekkel a tényezőkkel ellenőrizheti a előrejelzés eredményeit. Ezek a tényezők további képet adnak a legbefolyásosabb tényezőkről is, amelyek hozzájárultak a CLV minden ügyfélre való előrejelzése során.
  
   :::image type="content" source="media/CLV-influence-factors.png" alt-text="A CLV modell legbefolyásosabb tényezői":::

### <a name="learn-about-the-score"></a>További információ a pontszámról

A CLV-értéknek az alapmodellel való kiszámításához használt szabványos képlet:

 _**CLV minden egyes ügyfél** esetében = Az ügyfél által az aktív vevőablakban végrehajtott átlagos havi vásárlás * Hónapok száma a CLV előrejelzés időszakban * Az összes ügyfél általános megtartási aránya_

Az AI-modellt az alapmodellhez hasonlítják két teljesítménymérőszám-modell alapján.
  
- **A nagy értékű ügyfelek előrejelzésének sikerességi aránya**

  Megtekintheti a különbséget a nagy értékű ügyfelek előrejelzését az az AI modell használatával alapmodellhez képest. A 84%-os sikeresség például azt jelenti, hogy a képzési adatokban lévő értékes ügyfelekből az AI-modellnek sikerült pontosan rögzítenie a 84%-ot. Ezután összehasonlítjuk ezt az alapmodell sikerességi arányával a relatív változás jelentéséhez. Ez az érték egy osztályzatot rendel a modellhez.

- **Hibamutatók**

  Tekintse meg a modell általános teljesítményét a jövőbeli értékek előrejelzésének hibája szempontjából. A hiba felmérésére a gyök átlagos négyezetes eltérés (RMSE) mérőszámot használjuk. Az RMSE egy szabványos módja annak, hogy lemérje egy modell hibáját a kvantitatív adatok előrejelzésében. Összehasonlítják az AI modell RMSE-értékét az alapmodell RMSE-értékével, és a relatív különbség lesz jelentve.

Az AI modell előnyben részesíti ad az ügyfeleknek a vállalat számára behozott értéknek megfelelő pontos rangsorolásában. Az utolsó modellminőség származtatáshoz tehát csak a nagy értékű ügyfeleket jóslásának sikerességi aránya használható. Az RMSE mérőszám érzékeny a kiesőkre. Olyan helyzetekben, amikor az ügyfelek kis hányadánál nagyon magas a vásárlási érték, előfordulhat, hogy az általános RMSE metrika nem ad teljes képet a modell teljesítményével kapcsolatosan.

[!INCLUDE [footer-include](includes/footer-banner.md)]
