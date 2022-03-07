---
title: Előfizetési lemorzsolódás előrejelzés (videót tartalmaz)
description: Előrejelzi, hogy az ügyfélnél fennáll-e annak veszélye, hogy a jövőben nem az Ön vállalatánál fizet elő termékekre vagy szolgáltatásokra.
ms.date: 08/19/2020
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: zacookmsft
ms.author: zacook
manager: shellyha
ms.openlocfilehash: b61e87ad833dd7a8e51c6619945a9e216d85f221
ms.sourcegitcommit: 73cb021760516729e696c9a90731304d92e0e1ef
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/25/2022
ms.locfileid: "8354696"
---
# <a name="subscription-churn-prediction"></a>Előfizetési lemorzsolódás előrejelzése

Az előfizetési lemorzsolódást előrejelző funkcióval jelezhető, hogy az ügyfélnél fennáll-e annak veszélye, hogy a jövőben nem az Ön vállalatánál fizet elő termékekre vagy szolgáltatásokra. Az előfizetési lemorzsolódást jelző új előrejelzés az **Információk** > **Előrejelzések** oldalon hozható létre. Az Ön által létrehozott többi előrejelzés megtekintéséhez válassza a **Saját előrejelzések** lehetőséget.

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWOKNQ]

> [!TIP]
> Próbálja ki az előfizetési lemorzsolódási előrejelzést mintaadat használatával: [Előfizetési lemorzsolódási előrejelzés példaútmutató](sample-guide-predict-subscription-churn.md).

## <a name="prerequisites"></a>Előfeltételek

- Legalább [közreműködői engedélyek](permissions.md).
- Megfelelő üzleti ismeretek, hogy fel tudja mérni, mit jelent a vállalkozás számára a lemorzsolódás. Az időalapú lemorzsolódás meghatározásait támogatjuk. Ez azt jelenti, hogy egy ügyfél az előfizetés lejárata után egy adott idővel számít lemorzsolódottnak.
- Az előfizetésekkel és az előzményeikkel kapcsolatos adatok:
    - Az előfizetések megkülönböztetésére szolgáló előfizetési azonosítók.
    - Az ügyfelek és az előfizetések egyeztetésére szolgáló ügyfél-azonosítók.
    - Az előfizetési esemény dátumai, amelyek meghatározzák a kezdő és a záró dátumokat, illetve azokat a dátumokat, amelyeken sor került az előfizetésekre.
    - Az előfizetési információk, annak meghatározásához, hogy ismétlődő előfizetésről van-e szó, illetve hogy milyen gyakran újítják meg.
    - Az előfizetések szemantikai adatsémájának a következő információkra van szükség:
        - **Előfizetési azonosító:** Egy előfizetés egyedi azonosítója.
        - **Előfizetés záró dátuma:** Az előfizetés lejárati dátuma az ügyfél számára.
        - **Előfizetés kezdő dátuma:** Az előfizetés kezdetének dátuma az ügyfél számára.
        - **Tranzakció dátuma:** Az előfizetés megváltozásának dátuma. Egy ügyfél például előfizet valamire vagy lemond egy előfizetést.
        - **Ismétlődő előfizetés:** Logikai értékű igaz/hamis mező, amely meghatározza, hogy az előfizetés az ügyfél beavatkozása nélkül megújul-e ugyanazzal az előfizetési azonosítóval.
        - **Ismétlődés gyakorisága (hónapokban):** Ismétlődő előfizetések esetén az az időszak, amelyre a rendszer megújítja az előfizetést. Hónapokban jelenik meg. Például egy olyan éves előfizetés értéke, amely minden évben egy évre automatikusan megújul az ügyfél esetében, 12 lesz.
        - (Nem kötelező) **Előfizetés összege:** Az ügyfél által fizetett pénzösszeg az előfizetés megújításakor. Segíthet megtalálni a különböző előfizetési szintekre vonatkozó mintázatokat.
- Az ügyfelek tevékenységére vonatkozó adatok:
    - Az azonos típusú tevékenységek megkülönböztetésére szolgáló tevékenységazonosítók.
    - A tevékenységek ügyfelekhez rendelésére szolgáló ügyfél-azonosítók.
    - A tevékenység adatai a tevékenység nevét és dátumát tartalmazzák.
    - A felhasználói tevékenységekhez tartozó szemantikai adatséma a következőket tartalmazza:
        - **Elsődleges kulcs:** Egy tevékenység egyedi azonosítója. Például egy webhely felkeresése vagy egy felhasználásra vonatkozó rekord, amely azt mutatja, hogy az ügyfél megtekintette egy tévésorozat valamelyik részét.
        - **Időbélyegző:** Az elsődleges kulcs által azonosított esemény dátuma és időpontja.
        - **Esemény:** A használni kívánt esemény neve. Egy folyamatos átvitelt használó videószolgáltatás „FelhasználóiMűvelet” mezőjének értéke például „Megtekintve” lehet.
        - **Részletek:** Részletes információk az eseményről. Egy folyamatos átvitelt használó videószolgáltatás „MűsorCíme” mezőjének értéke például egy ügyfél által megtekintett videó lehet.
- Javasolt adatjellemzők:
    - Elegendő előzményadat: Az előfizetési adatok a kijelölt időablak legalább duplájához. Lehetőség szerint két-három éves előfizetési adatok.
    - Előfizetés állapota: Az adatok minden ügyfélhez aktív és inaktív előfizetéseket tartalmaznak, így ügyfélazonosítónként több bejegyzés van.
    - Ügyfelek száma: Legalább 10 ügyfélprofil, lehetőség szerint 1000-nél több egyedi ügyfél. A modell 10-nél kevesebb ügyfél esetén és ha nem áll rendelkezésre elegendő előzményadat, akkor nem működik.
    - Adat teljessége: A megadott entitás adatmezőjének hiányzó értékeinek kevesebb, mint 20%-a.
   
   > [!NOTE]
   > Legalább két tevékenységi bejegyzéshez lesz szüksége azon ügyfelek 50%-ához akiknél ki szeretné számítani a lemorzsolódás értékét.

## <a name="create-a-subscription-churn-prediction"></a>Előfizetési lemorzsolódás előrejelzésének létrehozása

1. A célközönség információin belül nyissa meg a következőt **Információk** > **Előrejelzések**.
1. Jelölje ki az **Előfizetés lemorzsolódási modellcsempét**, és válassza a A modell használata **lehetőséget**.
   > [!div class="mx-imgBorder"]
   > ![Az Előfizetési lemorzsolódás modellje csempe az Adott modell használata gombbal.](media/subscription-churn-usethismodel.PNG "Az Előfizetési lemorzsolódás modellje csempe az Adott modell használata gombbal")

### <a name="name-model"></a>Név modell

1. Adja meg a modell nevét; ez különbözteti majd meg a többi modelltől.
1. Adja meg a kimeneti entitás nevét: csak betűket és számokat használjon, szóközök nélkül. Ez lesz az a név, amelyet a modell entitás használni fog. Azután válassza a **Következő** elemet.

### <a name="define-customer-churn"></a>Ügyfél-lemorzsolódás meghatározása

1. Adja meg **Az előfizetés óta eltelt napok** számát; ez az az érték, ami után a vállalat lemorzsolódottnak tekint egy ügyfelet. Ezt az időszakot általában olyan üzleti tevékenységekkel szokták összevetni, amelyek az ügyfél elvesztését hivatottak megakadályozni (ajánlatok vagy egyéb marketinges erőfeszítések).
1. Adja meg a számot **A napok száma a jövőben a lemorzsolódás megjósolásához** alatt, hogy beállítsa az ablakot a lemorzsolódás előrejelzéséhez. Például megjósolhatja a lemorzsolódás kockázatát az ügyfelek számára a következő 90 nap során, hogy az megfeleljen a marketing megtartási törekvéseinek. A hosszabb vagy rövidebb időszakokra visszavethető lemorzsolódási kockázata előrejelzése az adott üzleti követelményektől függően nehezebben tudja figyelembe venni a lemorzsolódási kockázat profiljában lévő tényezőket. A folytatáshoz válassza a **Tovább** lehetőséget.
   >[!TIP]
   > A előrejelzés piszkozatként történő mentéséhez bármikor kiválaszthatja **a Piszkozat** mentése lehetőséget. Ha később folytatni szeretné a munkát, az előrejelzés vázlatát a **Saját előrejelzések** lapon találja majd.

### <a name="add-required-data"></a>Szükséges adatok hozzáadása

1. Az **Előfizetés előzményei** beállításnál válassza az **Adatok hozzáadása** lehetőséget, és válassza ki azt az entitást, amely – az [előfeltételek](#prerequisites) részen megadottaknak megfelelően – biztosítja az előfizetési előzményadatokat.
1. Ha az alábbi mezők nincsenek kitöltve, az előfizetési előzmények entitásból konfigurálja a kapcsolatot az Ügyfél entitáshoz.
    1. Válassza ki az **Előfizetés előzmények entitást**.
    1. Jelölje ki azt a **mezőt**, amellyel az előfizetési előzmények entitásában azonosítható az ügyfél. A mezőnek az Ügyfél entitás elsődleges ügyfél-azonosítójára kell vonatkoznia.
    1. Válassza ki azt az **Ügyfél entitást**, amely egyezik az elsődleges ügyfélentitással.
    1. Adjon meg egy olyan nevet, amely jól leírja a kapcsolatot.
       > [!div class="mx-imgBorder"]
       > ![Az Előfizetés előzményei oldal, amelyen az ügyfélhez fűződő kapcsolat létrehozása látható.](media/subscription-churn-subscriptionhistoryrelationship.PNG "Az Előfizetés előzményei oldal, amelyen az ügyfélhez fűződő kapcsolat létrehozása látható")
1. Válassza a **Következő** lehetőséget.
1. Képezze le a szemantikai mezőket az előfizetési előzmények entitás attribútumaira, és válassza a **Mentés** lehetőséget. A mezők leírása az [előfeltételek](#prerequisites) között található.
   > [!div class="mx-imgBorder"]
   > ![Az Előfizetés előzményei oldal, amelyen az előfizetési előzmények kijelölt entitásának mezőihez leképezett szemantikus attribútumok láthatók.](media/subscription-churn-subscriptionhistorymapping.PNG "Az Előfizetés előzményei oldal, amelyen az előfizetési előzmények kijelölt entitásának mezőihez leképezett szemantikus attribútumok láthatók")
1. Az **Ügyféltevékenységek** beállításnál válassza az **Adatok hozzáadása** lehetőséget, és válassza ki azt az ügyféltevékenységet, amely – az előfeltételek között leírtaknak megfelelően – biztosítja az előfizetési előzményadatokat.
1. Válasszon ki egy, az éppen konfigurált ügyféltevékenység típusának megfelelő tevékenységtípust.  Válassza az **Új létrehozása** lehetőséget, és adjon meg egy nevet, ha nem lát a kívánt tevékenység típusának megfelelő beállítást.
1. A kapcsolatot az ügyféltevékenység entitásából az Ügyfél entitáshoz kell konfigurálni.
    1. Válassza ki azt a mezőt, amely az ügyféltevékenység táblában azonosítja az ügyfelet; ez közvetlenül kapcsolódhat az Ügyfél entitás elsődleges ügyfél-azonosítójához.
    1. Válassza ki azt az Ügyfél entitást, amely egyezik az elsődleges Ügyfél entitással.
    1. Adjon meg egy olyan nevet, amely jól leírja a kapcsolatot.
1. Válassza a **Következő** lehetőséget.
1. Képezze le a szemantikai mezőket az ügyféltevékenység entitásának attribútumaira, és válassza a **Mentés** lehetőséget. A mezők leírása az [előfeltételek](#prerequisites) között található.
1. (Választható) Ha más ügyfélkapcsolatot is fel szeretne venni, akkor ismételje meg a fenti lépéseket.
   > [!div class="mx-imgBorder"]
   > ![Definiálja az entitás kapcsolatát.](media/subscription-churn-customeractivitiesmapping.PNG "Az Ügyféltevékenységek oldal, amelyen az ügyféltevékenység kijelölt entitásának mezőihez leképezett szemantikus attribútumok láthatók")
1. Válassza a **Következő** lehetőséget.

### <a name="set-schedule-and-review-configuration"></a>Ütemezési és felülvizsgálati konfiguráció beállítása

1. Állítsa be a modell újratanításának gyakoriságát. Ez a beállítás fontos, hogy frissíthesse az előrejelzéseinek pontosságát, ahogy új adat kerül betöltésre a célközönség-információkba. A legtöbb cég havonta egyszer végez újratanítást, és pontos előrejelzésekhez tud jutni.
1. Válassza a **Következő** lehetőséget.
1. Ellenőrizze a konfigurációt. A megjelenített érték alatt lévő **Szerkesztés** beállítással az előrejelzési konfiguráció bármelyik részéhez visszaléphet. Egy másik lehetőség, hogy kiválaszt egy konfigurációs lépést a folyamatjelzőn.
1. Ha minden érték megfelelően van konfigurálva, akkor az előrejelzési folyamat indításához válassza a **Mentés és Futtatás** lehetőséget. A **Saját előrejelzések** lapon tekintheti meg az előrejelzései állapotát. A folyamat – az előrejelzésben használt adatok mennyiségétől függően – több óráig is tarthat.

## <a name="review-a-prediction-status-and-results"></a>Előrejelzés állapotának és eredményeinek áttekintése

1. Lépjen az **Információk** > **Előrejelzések** rész **Saját előrejelzések** lapjára.
   > [!div class="mx-imgBorder"]
   > ![A Saját előrejelzések oldal képe.](media/subscription-churn-mypredictions.PNG "A Saját előrejelzések oldal képe")
1. Jelölje ki az áttekinteni kívánt előrejelzést.
   - **Előrejelzés neve:** Az előrejelzés létrehozáskor megadott neve.
   - **Előrejelzés típusa:** Az előrejelzéshez használt modell típusa.
   - **Kimeneti entitás:** Az előrejelzés kimenetének tárolására szolgáló entitás neve. Az ilyen nevű entitások az **Adatok** > **Entitások** részen találhatók.    
     A kimenetentitásban a *ChurnScore* a lemorzsolódás, illetve az *IsChurn* egy, a *ChurnScore* értéken alapuló bináris címke, amely 0,5-ös küszöbértéket biztosít. Előfordulhat, hogy az alapértelmezett küszöbérték nem működik a forgatókönyvnél. [Hozzon létre egy új szegmenst](segments.md#create-a-new-segment) az preferált küszöbértékkel.
   - **Várható mező:** Ez a mező csak bizonyos típusú előrejelzések esetén kap értéket; az előfizetési lemorzsolódás előrejelzése nem használja.
   - **Állapot:** Az előrejelzés aktuális futási állapota.
        - **Feldolgozási sorban:** Az előrejelzés jelenleg más folyamatok futására vár.
        - **Frissítés:** Az előrejelzés jelenleg a feldolgozás „pontszám" fázisát futtatja, hogy eredményekhez jusson a kimeneti entitás számára.
        - **Sikertelen:** Az előrejelzés futása nem sikerült. További részletek a **Naplók** elemre kattintva érhetők el.
        - **Sikerült:** Az előrejelzés sikeresen lefutott. Az előrejelzés megtekintéséhez válassza a függőleges pontok alatt lévő **Megtekintés** lehetőséget.
   - **Szerkesztve:** Az előrejelzés konfigurációjának módosítási dátuma.
   - **Legutóbbi frissítés:** A dátum, amikor az előrejelzés frissítette a kimeneti entitásban szereplő eredményeket.
1. Kattintson a függőleges pontok ikonjára azon előrejelzés mellett, amelynek meg szeretné tekinteni az eredményeit, és kattintson a **Megtekintés** elemre.
   > [!div class="mx-imgBorder"]
   > ![A függőleges pontok menüjének beállításai az előrejelzésekhez – többek között Szerkesztés, Frissítés, Megtekintés, Naplók és Törlés.](media/subscription-churn-verticalellipses.PNG "A függőleges pontok menüjének beállításai az előrejelzésekhez – többek között Szerkesztés, Frissítés, Megtekintés, Naplók és Törlés")
1. Az eredményoldalon lévő adatok három fő részben jelennek meg:
    1. **Betanítási modell teljesítménye:** A lehetséges értékek: A, B vagy C. Ez a pontszám jelzi az előrejelzés teljesítményét, és könnyebbé teheti a kimeneti entitásban tárolt eredmények használatára vonatkozó döntést.
        - A pontszámok meghatározása a következő szabályok alapján történik:
            - **A** ha a modell pontosan megjósolta legalább 50%-át a teljes előrejelzések, és amikor a pontos előrejelzések százalékértéke azon ügyfelek esetében, akik elvándoroltak nagyobb, mint az átlagos előzmény ügyfél-lemorzsolódás legalább az előzmény lemorzsolódási arány 10%-ával.
            - **B** ha a modell pontosan megjósolta legalább 50%-át a teljes előrejelzések, és amikor a pontos előrejelzések százalékértéke azon ügyfelek esetében, akik elvándoroltak nagyobb, mint az átlagos előzmény ügyfél-lemorzsolódás maximum az előzmény lemorzsolódási arány 10%-ával.
            - **C** Ha modell az összes előrejelzés kevesebb mint 50%-át jelezte előre pontosan, vagy amikor a lemorzsolódott ügyfelek előrejelzésének pontossága kisebb, mint az átlagos előzmény lemorzsolódási arány.
               > [!div class="mx-imgBorder"]
               > ![A modell teljesítményének megtekintése.](media/subscription-churn-modelperformance.PNG "A modell teljesítményének megtekintése")
    1. **Lemorzsolódási valószínűség (ügyfelek száma):** Ügyfelek csoportjai a lemorzsolódás előrejelzett kockázata alapján. Ez az adat a későbbiekben segítséget jelenthet, ha magas lemorzsolódási kockázattal rendelkező ügyfelekhez szeretne szegmenst létrehozni. Az ilyen szegmensek segítségével felmérheti, hogy a szegmens tagsága esetén hol legyen a lezárás.
       > [!div class="mx-imgBorder"]
       > ![A lemorzsolódási eredmények megoszlását bemutató grafikon, 0–100%.](media/subscription-churn-resultdistribution.PNG "A lemorzsolódási eredmények megoszlását bemutató grafikon, 0–100%")
    1. **Legbefolyásosabb tényezők:** Az előrejelzés létrehozásakor a rendszer számos tényezőt vesz figyelembe. Az egyes tényezők fontosságát a rendszer kiszámítja a modell által létrehozott összesített előrejelzésekhez. Ezekkel a tényezőkkel ellenőrizheti az előrejelzés eredményeit. Ezeket az információkat később is felhasználhatja, hogy olyan [szegmenseket hozzon létre,](segments.md) amelyekkel csökkenthető az ügyfelek lemorzsolódási kockázata.
       > [!div class="mx-imgBorder"]
       > ![A befolyásos tényezőket és a fontosságukat mutató lista a lemorzsolódási eredmény előrejelzésében.](media/subscription-churn-influentialfactors.PNG "A befolyásos tényezőket és a fontosságukat mutató lista a lemorzsolódási eredmény előrejelzésében")

## <a name="manage-predictions"></a>Előrejelzések kezelése

Lehetőség van az előrejelzések optimalizálására, hibaelhárítására, frissítésére vagy törlésére. Tekintse át a bemeneti adatok használhatósági jelentését, hogy megtudja, hogyan lehet egy előrejelzés gyorsabb és megbízhatóbb. További tudnivalókért lásd: [Előrejelzések kezelése](manage-predictions.md).


[!INCLUDE[footer-include](../includes/footer-banner.md)]
