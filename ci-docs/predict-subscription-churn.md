---
title: Az előfizetés lemorzsolódásának előrejelzése (videót tartalmaz)
description: Előrejelzi, hogy az ügyfélnél fennáll-e annak veszélye, hogy a jövőben nem az Ön vállalatánál fizet elő termékekre vagy szolgáltatásokra.
ms.date: 09/30/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: zacookmsft
ms.author: zacook
manager: shellyha
ms.openlocfilehash: 7464707864c418bfcc625ddfd245622131434b33
ms.sourcegitcommit: be341cb69329e507f527409ac4636c18742777d2
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/30/2022
ms.locfileid: "9610239"
---
# <a name="predict-subscription-churn"></a>Előfizetési lemorzsolódás előrejelzése

Előrejelzi, hogy az ügyfélnél fennáll-e annak veszélye, hogy a jövőben nem az Ön vállalatánál fizet elő termékekre vagy szolgáltatásokra. Az előfizetési adatok magukban foglalják az egyes ügyfelek aktív és inaktív előfizetéseit, így ügyfél-azonosítónként több bejegyzés is van.

Üzleti ismeretekkel kell rendelkeznie ahhoz, hogy megértse, mit jelent a lemorzsolódás a vállalkozása számára. Támogatjuk az időalapú adatváltozás-definíciókat, ami azt jelenti, hogy az ügyfél úgy tekinthető, hogy az előfizetése lejárta után egy bizonyos időszakot lemorzsolódott.

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWOKNQ]

> [!TIP]
> Próbálja ki az előfizetés lemorzsolódását előrejelzés mintaadatokkal: [Előfizetési adatváltozás előrejelzés mintaútmutató](sample-guide-predict-subscription-churn.md).

## <a name="prerequisites"></a>Előfeltételek

- Legalább [közreműködői engedélyek](permissions.md).
- Legalább 10 ügyfélprofil, lehetőleg több mint 1,000 egyedi ügyfél.
- Ügyfél-azonosító, egy egyedi azonosító, amely megfelelteti az előfizetéseket az ügyfeleknek.
- Előfizetési adatok a kiválasztott időablak legalább kétszeresére. Lehetőség szerint két-három éves előfizetési adatok. Az előfizetési előzményeknek a következőket kell tartalmazniuk:
  - **Előfizetés azonosítója:** Az előfizetés egyedi azonosítója.
  - **Az előfizetés záró dátuma:** Az előfizetés lejáratának dátuma az ügyfél számára.
  - **Előfizetés kezdő dátuma:** Az előfizetés megkezdésének dátuma az ügyfél számára.
  - **Tranzakció dátuma:** Az előfizetés módosításának dátuma. Egy ügyfél például előfizet valamire vagy lemond egy előfizetést.
  - **Ismétlődő előfizetésről van szó:** Logikai igaz/hamis mező, amely meghatározza, hogy az előfizetés ugyanazzal az előfizetés-azonosítóval újul-e meg az ügyfél beavatkozása nélkül.
  - **Ismétlődés gyakorisága (hónapokban):** Ismétlődő előfizetések esetén az a hónap, amikor az előfizetés megújul. Például egy olyan éves előfizetés értéke, amely minden évben egy évre automatikusan megújul az ügyfél esetében, 12 lesz.
  - **Előfizetési összeg**: Az a pénznem, amelyet az ügyfél az előfizetés megújításáért fizet. Segíthet megtalálni a különböző előfizetési szintekre vonatkozó mintázatokat.
- Legalább két tevékenységrekord azoknak az ügyfeleknek az 50%-ánál, akikre ki szeretné számítani a lemorzsolódást. Az ügyféltevékenységeknek a következőket kell tartalmazniuk:
  - **Elsődleges kulcs:** Egy tevékenység egyedi azonosítója. Például egy webhely felkeresése vagy egy felhasználásra vonatkozó rekord, amely azt mutatja, hogy az ügyfél megtekintette egy tévésorozat valamelyik részét.
  - **Időbélyegző:** Az elsődleges kulccsal azonosított esemény dátuma és időpontja.
  - **Esemény:** A használni kívánt esemény neve. Egy folyamatos átvitelt használó videószolgáltatás „FelhasználóiMűvelet” mezőjének értéke például „Megtekintve” lehet.
  - **Részletek:** Részletes információk az eseményről. Egy folyamatos átvitelt használó videószolgáltatás „MűsorCíme” mezőjének értéke például egy ügyfél által megtekintett videó lehet.
- Kevesebb, mint 20% -ban hiányzik az érték a megadott entitás adatmezőjében.

## <a name="create-a-subscription-churn-prediction"></a>Előfizetési lemorzsolódás előrejelzésének létrehozása

Válassza a Piszkozat **mentése bármikor lehetőséget** a előrejelzés piszkozatként való mentéséhez. A piszkozat előrejelzés a **Saját előrejelzések** lapon jelenik meg.

1. Ugrás az Intelligencia-előrejelzések **oldalra** > **·**.

1. A Létrehozás lapon válassza a **Modell** használata lehetőséget **az** Ügyfél adatváltozás modelljének csempéjén **.**

1. Válassza az Előfizetés lehetőséget **a lemorzsolódás típusához, majd** az Első lépések lehetőséget **.**

1. **Nevezze el ezt a modellt** és a **Kimeneti entitás nevét**, hogy megkülönböztesse őket az egyéb modellektől vagy entitásoktól.

1. Válassza a **Következő** lehetőséget.

### <a name="define-customer-churn"></a>Ügyfél-lemorzsolódás meghatározása

1. Adja meg **Az előfizetés óta eltelt napok** számát; ez az az érték, ami után a vállalat lemorzsolódottnak tekint egy ügyfelet. Ez az időszak általában olyan üzleti tevékenységekhez kapcsolódik, mint az ajánlatok vagy más marketing erőfeszítések, amelyek megpróbálják megakadályozni az ügyfél elvesztését.

1. Adja meg a jövőbeli vizsgálat napjainak számát **a lemorzsolódás** előrejelzéséhez. Például, megjósolhatja a lemorzsolódás kockázatát egy ügyfele esetében, a következő 90 napban, hogy ehhez igazíthassa marketingmegőrzési törekvéseit. A hosszabb vagy rövidebb időszakokra visszavethető lemorzsolódási kockázata előrejelzése az adott üzleti követelményektől függően nehezebben tudja figyelembe venni a lemorzsolódási kockázat profiljában lévő tényezőket.

1. Válassza a **Következő** lehetőséget.

### <a name="add-required-data"></a>Szükséges adatok hozzáadása

1. Válassza az Adatok hozzáadása lehetőséget **az Előfizetési előzményekhez** **.**

1. Válassza ki az Előfizetés **szemantikai tevékenységtípust**, amely tartalmazza a szükséges előfizetési előzmények adatait. Ha a tevékenység nincs beállítva, válassza ki **itt**, és hozza létre.

1. Ha a Tevékenységek **alatt** a tevékenységattribútumok szemantikailag leképeződtek a tevékenység létrehozásakor, válassza ki azokat az attribútumokat vagy entitásokat, amelyekre a számítást összpontosítani szeretné. Ha a szemantikai leképezés nem történt meg, válassza az Adatok szerkesztése **és leképezése lehetőséget**.
  
   :::image type="content" source="media/subscription-churn-required.png" alt-text="Adja hozzá a szükséges adatokat az előfizetés lemorzsolódási modelljéhez":::

1. Válassza a Tovább **lehetőséget**, és tekintse át a modellhez szükséges attribútumokat.

1. Válassza a **Mentés** parancsot.

1. Válassza az Adatok **hozzáadása az** ügyféltevékenységekhez **lehetőséget**.

1. Válassza ki azt a szemantikai tevékenységtípust, amely az ügyféltevékenység adatait biztosítja. Ha a tevékenység nincs beállítva, válassza ki **itt**, és hozza létre.

1. Ha a Tevékenységek **alatt** a tevékenységattribútumok szemantikailag leképeződtek a tevékenység létrehozásakor, válassza ki azokat az attribútumokat vagy entitásokat, amelyekre a számítást összpontosítani szeretné. Ha a szemantikai leképezés nem történt meg, válassza az Adatok szerkesztése **és leképezése lehetőséget**.

1. Válassza a Tovább **lehetőséget**, és tekintse át a modellhez szükséges attribútumokat.

1. Válassza a **Mentés** parancsot.

1. Adjon hozzá további tevékenységeket, vagy válassza a Tovább **lehetőséget**.

### <a name="set-update-schedule"></a>Frissítési ütemezés beállítása

1. Válassza ki a frekvenciát a modell újratanításához. Ez a beállítás fontos az előrejelzések pontosságának frissítéséhez, mivel a rendszer új adatokat tölt be a Customer Insights szolgáltatásba. A legtöbb cég havonta egyszer végez újratanítást, és pontos előrejelzésekhez tud jutni.

1. Válassza a **Következő** lehetőséget.

### <a name="review-and-run-the-model-configuration"></a>A modellkonfiguráció áttekintése és futtatása

Az **Áttekintés és futtatás** lépés a konfiguráció összegzését jeleníti meg, és lehetőséget biztosít a módosítások elvégzésére a előrejelzés létrehozása előtt.

1. Válassza a Szerkesztés **lehetőséget** az áttekintéshez és a módosítások elvégzéséhez szükséges lépések bármelyikénél.

1. Ha elégedett a választásokkal, válassza a Mentés és futtatás **lehetőséget** a modell futtatásának megkezdéséhez. Válassza a **Kész** lehetőséget. A **Saját előrejelzések** lap a előrejelzés létrehozásakor jelenik meg. A folyamat – az előrejelzésben használt adatok mennyiségétől függően – több óráig is tarthat.

[!INCLUDE [progress-details](includes/progress-details-pane.md)]

## <a name="view-prediction-results"></a>Előrejelzés eredmények megtekintése

1. Ugrás az Intelligencia-előrejelzések **oldalra** > **·**.

1. **A Saját előrejelzések** lapon válassza ki a megtekinteni kívánt előrejelzés.

Az eredményoldalon lévő adatok három fő részben jelennek meg:

- **Betanítási modell teljesítménye**: Az A, B vagy C fokozatok jelzik a előrejelzés teljesítményét, és segíthetnek a kimeneti entitásban tárolt eredmények használatára vonatkozó döntés meghozatalában.
  
  :::image type="content" source="media/subscription-churn-modelperformance.PNG" alt-text="A modell pontszám információs mezője A osztályzattal":::

  Az osztályzatot a következő szabályok határozzák meg:
  - **A** amikor a modell pontosan megjósolta az összes előrejelzés legalább 50% -át, és amikor a pontos előrejelzések százalékos aránya az ügyfelek számára, akik lemorzsoltak, legalább 10% -kal meghaladja a múltbeli átlagos lemorzsolódási arányt.
  - **B**, ha a modell pontosan megjósolta az összes előrejelzés legalább 50%át, és amikor a pontos előrejelzések százalékos aránya a lemorzsolódott ügyfelek számára akár 10% -kal is nagyobb, mint a korábbi átlagos lemorzsolódási arány.
  - **C**, ha a modell pontosan megjósolta az összes előrejelzés kevesebb mint 50%-át, vagy ha a pontos előrejelzések százalékos aránya a lemorzsolódott ügyfelek számára kisebb, mint a korábbi átlagos lemorzsolódási arány.
  
- **Lemorzsolódási valószínűség (ügyfelek száma)**: Ügyfelek csoportjai a lemorzsolódás előrejelzett kockázata alapján. [Igény szerint magas lemorzsolódási kockázattal rendelkező ügyfelek](prediction-based-segment.md) szegmenseit is létrehozhatja. Az ilyen szegmensek segítségével felmérheti, hogy a szegmens tagsága esetén hol legyen a lezárás.  

  :::image type="content" source="media/subscription-churn-resultdistribution.PNG" alt-text="A lemorzsolódási eredmények megoszlását bemutató grafikon, 0–100%":::

- **Legbefolyásosabb tényezők:** Az előrejelzés létrehozásakor a rendszer számos tényezőt vesz figyelembe. A tényezők mindegyikének megvan a fontossága, az összesített előrejelzés számításaiban, melyet a modell hoz létre. Ezekkel a tényezőkkel ellenőrizheti a előrejelzés eredményeit. Vagy használja ezeket az információkat később olyan szegmensek [létrehozásához, amelyek segíthetnek befolyásolni](.//prediction-based-segment.md) az ügyfelek lemorzsolódási kockázatát.

  :::image type="content" source="media/subscription-churn-influentialfactors.PNG" alt-text="A befolyásos tényezőket és a fontosságukat mutató lista a lemorzsolódási eredmény előrejelzésében.":::

> [!NOTE]
> Ennek a modellnek a kimeneti entitásában a ChurnScore *a lemorzsolódás előrejelzett valószínűsége, az IsChurn* pedig *egy bináris címke,* amely a ChurnScore-on *alapul*, 0,5 küszöbértékkel. Ha ez az alapértelmezett küszöbérték nem működik a forgatókönyvben, [hozzon létre egy új szegmenst](segments.md) az előnyben részesített küszöbértékkel. A adatváltozási pontszám megtekintéséhez lépjen az **Adatentitások** > **elemre**, és tekintse meg a modellhez definiált kimeneti entitás adatok lapját.

[!INCLUDE [footer-include](includes/footer-banner.md)]
