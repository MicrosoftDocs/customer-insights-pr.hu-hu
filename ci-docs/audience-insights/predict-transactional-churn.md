---
title: Tranzakciólemorzsolódási előrejelzés
description: Megjósolja, hogy fennáll-e az ügyfélnél annak veszélye, hogy a jövőben már nem az Ön termékeit vagy szolgáltatásait vásárolja meg.
ms.date: 11/12/2020
ms.reviewer: zacook
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: af461d290c69687fb47bacfcff446a0c62978383
ms.sourcegitcommit: 139548f8a2d0f24d54c4a6c404a743eeeb8ef8e0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/15/2021
ms.locfileid: "5268321"
---
# <a name="transactional-churn-prediction-preview"></a>Tranzakciólemorzsolódási előrejelzés (előnézet)

A Tranzakciós lemorzsolódási előrejelzés segít megjósolni, ha az ügyfél valószínűleg többé már nem fogja megvásárolni az Ön termékeit vagy szolgáltatásait egy adott játékablakon belül. Új lemorzsolódási előrejelzéseket hozhat létre az **Intelligencia** > **Előrejelzések** menüponton. Az Ön által létrehozott többi előrejelzés megtekintéséhez válassza a **Saját előrejelzések** lehetőséget.

> [!TIP]
> Próbálja ki a tranzakciós lemorzsolódási előrejelzést mintaadat használatával: [Tranzakciós lemorzsolódási előrejelzés (előnézet) példaútmutató](sample-guide-predict-transactional-churn.md).

## <a name="prerequisites"></a>Előfeltételek

- Legalább [közreműködői engedély](permissions.md) a Customer Insightsban.
- Megfelelő üzleti ismeretek, hogy fel tudja mérni, mit jelent a vállalkozás számára a lemorzsolódás. Az idő alapú lemorzsolódás meghatározást támogatjuk, ami azt jelenti, hogy az ügyfelet lemorzsolódottnak tekintjük, egy meghatározott vásárlás nélkül eltelt idő után.
- A tranzakciókkal/vásárlásokkal kapcsolatos adatok és a velük kapcsolatos előzmények:
    - A Tranzakcióazonosítók, hogy meghatározhassa a vásárlásokat/tranzakciókat.
    - Ügyfélazonosítók, egyeztetni a tranzakciókat az ügyfelekkel.
    - Üzleti események dátumai, amely meghatározza a dátumot, amikor a tranzakció történt.
    - A szemantikus adatréteg séma a vásárlásokhoz/tranzakciókhoz a következő információk szükségesek:
        - **Tranzakcióazonosító:** Egy egyedi azonosító a vásárláshoz vagy tranzakcióhoz.
        - **Tranzakció dátuma:** A vásárlás vagy tranzakció dátuma.
        - **A tranzakció értéke:** A pénznembeli/számértékbeli értéke a tranzakciónak/elemnek.
        - (Választható) **Egyedi termékazonosító:** A megvásárolt termék vagy szolgáltatás azonosítója, ha az adat a sortétel szintjén szerepel.
        - (Választható) **Amennyiben ez a tranzakció visszatérítés:** Az igaz/hamis mező azonosítja, hogy ez a tranzakció visszatérítés volt -e vagy sem. Ha a **Tranzakció értéke** negatív, ezt az információt is felhasználjuk, a visszatérítés lehetőségeinek kikövetkeztetéséhez.
- (Választható) Adatok az ügyfél tevékenységéről:
    - Az azonos típusú tevékenységek megkülönböztetésére szolgáló tevékenységazonosítók.
    - A tevékenységek ügyfelekhez rendelésére szolgáló ügyfél-azonosítók.
    - A tevékenység adatai a tevékenység nevét és dátumát tartalmazzák.
    - A felhasználói tevékenységekhez tartozó szemantikai adatséma a következőket tartalmazza:
        - **Elsődleges kulcs:** Egy tevékenység egyedi azonosítója. Például, ha egy webhelylátogatás vagy egy használati rekord azt mutatja, hogy az ügyfél kipróbálta az egyik mintatermékét.
        - **Időbélyegző:** Az elsődleges kulcs által azonosított esemény dátuma és időpontja.
        - **Esemény:** A használni kívánt esemény neve. Például, ha egy mező neve "FelhasználóiMűvelet" egy élelmiszerboltban, ez egy ügyfél által történő kuponhasználatot jelenthet.
        - **Részletek:** Részletes információk az eseményről. Például, ha egy mező neve "KuponÉrték" egy élelmiszerboltban, ez a kupon pénznembeli értékét jelentheti.

## <a name="create-a-transactional-churn-prediction"></a>Tranzakciólemorzsolódási előrejelzés létrehozása

1. A Customer Insights szolgáltatásban lépjen az **Intelligencia** > **Előrejelzések** részre.

1. Válassza ki az **Ügyféllemorzsolódási modell (előnézet)** csempét, és ott válassza az **A modell használata** menüpontot.
   
1. Az **Ügyfél-lemorzsolódási modell** panelen kattintson a **Tranzakciós** lehetőségre, és válassza az **Első lépések** menüpontot.

:::image type="content" source="media/select-transaction-churn.PNG" alt-text="Képernyőkép a választott tranzakciós lehetőséggel az Ügyfél-lemorzsolódási modell-panelen.":::

### <a name="name-model"></a>Név modell

1. Adja meg a modell nevét; ez különbözteti majd meg a többi modelltől.

1. Adja meg a kimeneti entitás nevét: csak betűket és számokat használjon, szóközök nélkül. Ez lesz az a név, amelyet a modell entitás használni fog. 

1. Válassza a **Következő** lehetőséget.

### <a name="define-customer-churn"></a>Ügyfél-lemorzsolódás meghatározása

1. Állítsa be a napok ablakot, hogy megjósolhassa a lemorzsolódást a **Beazonosítani azokat az ügyfeleket, akik esetleg lemorzsolódhatnak a következő időszakban** mezőben. Például, megjósolhatja a lemorzsolódás kockázatát egy ügyfele esetében, a következő 90 napban, hogy ehhez igazíthassa marketingmegőrzési törekvéseit. A lemorzsolódási kockázat becslése egy hosszabb vagy rövidebb időintervallumra megnehezítheti a tényezők kezelését a lemorzsolódási kockázat-profiljában, de ez leginkább az Ön által meghatározott üzleti igényektől függ. 
   >[!TIP]
   > A **Mentés és bezárás** gombbal bármikor mentheti vázlatként az előrejelzést. Ha később folytatni szeretné a munkát, az előrejelzés vázlatát a **Saját előrejelzések** lapon találja majd.

1. Adja meg a napok számát, hogy meghatározhasson egy lemorzsolódást az **Az ügyfél lemorzsolódott, ha nem történt vásárlás ekkor:** mezőben. Például, ha egy ügyfél nem vásárolt az elmúlt 30 napban, vállalkozása számára lemorzsolódónak tekinthető. 

1. A folytatáshoz válassza a **Tovább** lehetőséget.

### <a name="add-required-data"></a>Szükséges adatok hozzáadása

1. Válassza az **Adatok felvétele** mezőt a **Beszerzési előzmények**-ben, és válassza azt az entitást, amely biztosítja a tranzakciós/vásárlási előzmény információt, amint azok részletezésre kerültek az [Előfeltételekben](#prerequisites).

1. Képezze le a szemantikai mezőket olyan attribútumokra, melyek a beszerzési előzmények entitáson belül esnek, és válassza a **Tovább** lehetőséget. A mezők leírása az [előfeltételek](#prerequisites) között található.

   :::image type="content" source="media/model-map-purchase-entity.PNG" alt-text="A vásárlási entitás szemantikai mezőinek leképezése.":::

1. Ha az alábbi mezők nincsenek megadva, konfigurálja a kapcsolatokat beszerzési előzmények entitásából a Ügyfélentitással.
    1. Válassza ki a **Beszerzési előzmények entitás**-t.
    1. Válassza a **Mező** lehetőséget, mely azonosítja az ügyfelet a beszerzési előzmények entitásban. A mezőnek az Ügyfél entitás elsődleges ügyfél-azonosítójára kell vonatkoznia.
    1. Válassza ki azt az **Ügyfél entitást**, amely egyezik az elsődleges ügyfélentitással.
    1. Adjon meg egy olyan nevet, amely jól leírja a kapcsolatot.

    :::image type="content" source="media/model-purchase-join.PNG" alt-text="A Vásárlási előzmények oldal megjeleníti az ügyféllel létrehozott kapcsolatot.":::
   
1. Válassza a **Következő** lehetőséget.

1. Tetszés szerint kiválaszthatja az **Adatok felvétele** az **Ügyféltevékenységek**-hezt. Válassza azt az entitást, amely biztosítja, hogy ügyféltevékenység információja az előfeltételekben részletezett módon kerüljön megjelenítésre.

1. Képezze le a szemantikai mezőket olyan attribútumokra, melyek az ügyféltevékenység entitáson belül esnek és válassza a **Tovább** lehetőséget. A mezők leírása az [előfeltételek](#prerequisites) között található.

   :::image type="content" source="media/map-transaction-data-fields.png" alt-text="Ügyfélmezők leképezése tranzakciós adatokhoz.":::

1. Válasszon ki egy, az éppen konfigurált ügyféltevékenység típusának megfelelő tevékenységtípust. Válassza az **Új létrehozása** lehetőséget és válasszon ki egy már elérhető tevékenységtípust, vagy hozzon létre egy új típust.

1. A kapcsolatot az ügyféltevékenység entitásából az Ügyfél entitáshoz kell konfigurálni.
    1. Válassza ki a mezőt, amely azonosítja az ügyfelet az ügyféltevékenység táblában. Ez közvetlenül kapcsolásra kerülhet Ügyfélentitásának Elsődleges ügyfél-azonosítójához.
    1. Válassza ki azt az Ügyfél entitást, amely egyezik az elsődleges Ügyfél entitással.
    1. Adjon meg egy olyan nevet, amely jól leírja a kapcsolatot.

1. Válassza a **Mentés** parancsot.

1. Ha más ügyféltevékenységgel is rendelkezik, amelyet fel szeretne venni, ismételje meg a fenti lépéseket.

1. Válassza a **Következő** lehetőséget.

### <a name="set-schedule-and-review-configuration"></a>Ütemezési és felülvizsgálati konfiguráció beállítása

1. Állítsa be a modell újratanításának gyakoriságát. Ez a beállítás fontos, hogy frissíthesse az előrejelzéseinek pontosságát, ahogy új adat kerül betöltésre. A legtöbb cég havonta egyszer végez újratanítást, és pontos előrejelzésekhez tud jutni.

1. Válassza a **Következő** lehetőséget.

1. Ellenőrizze az előrejelzés konfigurációját. Visszatérhet az előző lépésekre, ha a **Szerkesztés**-re kattint a megjelenő érték alatt. Egy másik lehetőség, hogy kiválaszt egy konfigurációs lépést a folyamatjelzőn.

1. Ha minden érték megfelelően van konfigurálva, akkor az előrejelzési folyamat indításához válassza a **Mentés és Futtatás** lehetőséget. A **Saját előrejelzések** lapon tekintheti meg az előrejelzései állapotát. A folyamat – az előrejelzésben használt adatok mennyiségétől függően – több óráig is tarthat.

## <a name="review-a-prediction-status-and-results"></a>Előrejelzés állapotának és eredményeinek áttekintése

1. Nyissa meg az **Intelligencia** > **Előrejelzések** menüt, és válassza ki a **Saját előrejelzések** lapot.

1. Jelölje ki az áttekinteni kívánt előrejelzést.
   - **Előrejelzés neve:** Az előrejelzés neve, mely a létrehozáskor kerül megadásra.
   - **Előrejelzés típusa:** Az előrejelzéshez használt model típusa
   - **Kimeneti entitás:** Az előrejelzés kimenetének tárolására szolgáló entitás neve. Az ilyen nevű entitások az **Adatok** > **Entitások** részen találhatók.
   - **Várható mező:** Ez a mező csak bizonyos típusú előrejelzésekhez megadható, és nem használható a lemorzsolódási előrejelzéshez.
   - **Állapot:** A futtatott előrejelzés állapota.
        - **Feldolgozási sorban:** Az előrejelzés további folyamatok futtatására vár.
        - **Frissítés:** Az előrejelzés jelenleg fut, hogy a kimeneti entitásba kerülő eredményt produkálhassa.
        - **Sikertelen:** Az előrejelzés lefuttatása sikertelen. [Ellenőrizze a naplókat](#troubleshoot-a-failed-prediction) a további részletekért.
        - **Sikeres:** Az Előrejelzés lefuttatása sikeresen megtörtént. Az előrejelzés megtekintéséhez válassza a függőleges pontok alatt lévő **Megtekintés** lehetőséget.
   - **Szerkesztve:** Az előrejelzés konfigurációjának módosítási dátuma.
   - **Legutóbbi frissítés:** A dátum, amikor az előrejelzés frissítette a kimeneti entitásban szereplő eredményeket.

1. Kattintson a függőleges pontok ikonjára azon előrejelzés mellett, amelynek meg szeretné tekinteni az eredményeit, és kattintson a **Megtekintés** elemre.

   :::image type="content" source="media/model-subs-view.PNG" alt-text="Tekintse meg az előrejelzés eredményeit a vezérlőn.":::   

1. Az eredményoldalon lévő adatok három fő részben jelennek meg:
    1. **Betanítási modell teljesítménye:** A lehetséges értékek: A, B vagy C. Ez a pontszám jelzi az előrejelzés teljesítményét, és könnyebbé teheti a kimeneti entitásban tárolt eredmények használatára vonatkozó döntést. A pontszámok meghatározása a következő szabályok alapján történik:
         
         - **A** amikor egy modell legalább 50%-ban pontos az összes előrejelzéshez mérten, és amikor a pontos előrejelzések százalékos aránya a lemorzsolódó ügyfelekről nagyobb, mint a viszonyítási alapérték, ami a legalább 10%.
            
         - **B** amikor egy modell legalább 50%-ban pontos az összes előrejelzéshez mérten, és amikor a pontos előrejelzések százalékos aránya a lemorzsolódó ügyfelekről nagyobb, mint 10%, ami nagyobb, mint a viszonyítási alapérték.
            
         - **C** amikor egy modell előrejelzése kevesebb, mint 50%-ban pontos, vagy amikor a pontos előrejelzések százalékos aránya a lemorzsolódó ügyfelekről kisebb, mint a viszonyítási alapérték.
               
         - Az **Alapérték** adja meg az előrejelzés idejét a modell bemeneti ablakán (például egy év), és a modell létrehozza a különböző időrészleteket, azáltal, hogy kettéosztja, amíg az el nem éri az egy hónap vagy kevesebbet. Ezen töredékek segítségével üzleti szabályokat hozhat létre azon ügyfeleknek, akik nem vásároltak ebben az időkeretben. Ezek az ügyfelek lemorzsolódónak vannak tekintve. Az idő alapú üzleti szabály rendelkezik a legnagyobb képességgel, hogy előre jelezhesse, ki a fog a legvalószínűbben lemorzsolódni, a megadott alapérték modellen.
            
    1. **Lemorzsolódási valószínűség (ügyfelek száma):** Ügyfelek csoportjai a lemorzsolódás előrejelzett kockázata alapján. Ez az adat a későbbiekben segítséget jelenthet, ha magas lemorzsolódási kockázattal rendelkező ügyfelekhez szeretne szegmenst létrehozni. Az ilyen szegmensek segítségével felmérheti, hogy a szegmens tagsága esetén hol legyen a lezárás.
       
    1. **Legbefolyásosabb tényezők:** Az előrejelzés létrehozásakor a rendszer számos tényezőt vesz figyelembe. A tényezők mindegyikének megvan a fontossága, az összesített előrejelzés számításaiban, melyet a modell hoz létre. Ezekkel a tényezőkkel ellenőrizheti az előrejelzés eredményeit. Ezeket az információkat később is felhasználhatja, hogy olyan [szegmenseket hozzon létre,](segments.md) amelyekkel csökkenthető az ügyfelek lemorzsolódási kockázata.

## <a name="troubleshoot-a-failed-prediction"></a>A sikertelen előrejelzés hibáinak elhárítása.

1. Nyissa meg az **Intelligencia** > **Előrejelzések** menüt, és válassza ki a **Saját előrejelzések** lapot.

1. Válassza ki a függőleges ellipsziseket amellett az előrejelzés mellet, melynek hibanaplóját meg szeretné tekinteni.

1. Válassza ki a **Naplók** menüpontot.

1. Tekintse át a hibákat. Többféle típusú hiba fordulhat elő; a leírásból kiderül, milyen feltétel okozta a hibát. Ha például az a hiba, hogy nincs elég adat a pontos előrejelzéshez, akkor ez általában megoldható további adatok Customer Insightsba történő betöltésével.

## <a name="refresh-a-prediction"></a>Előrejelzés frissítése

Az előrejelzések automatikusan frissülnek az [adatok beállítások között megadott frissítési ütemezése](system.md#schedule-tab) szerint. Ezeket Ön manuálisan is frissíteni tudja.

1. Nyissa meg az **Intelligencia** > **Előrejelzések** menüt, és válassza ki a **Saját előrejelzések** lapot.

1. Kattintson a frissíteni kívánt előrejelzés mellett lévő pontokra.

1. Válassza a **Frissítés** lehetőséget.

## <a name="delete-a-prediction"></a>Előrejelzés törlése

Az előrejelzés törlésével annak kimeneti entitása is törlésre kerül.

1. Nyissa meg az **Intelligencia** > **Előrejelzések** menüt, és válassza ki a **Saját előrejelzések** lapot.

1. Kattintson a törölni kívánt előrejelzés mellett lévő pontokra.

1. Válassza a **Törlés** lehetőséget.


[!INCLUDE[footer-include](../includes/footer-banner.md)]