---
title: Tranzakciós lemorzsolódás előrejelzés (videót tartalmaz)
description: Megjósolja, hogy fennáll-e az ügyfélnél annak veszélye, hogy a jövőben már nem az Ön termékeit vagy szolgáltatásait vásárolja meg.
ms.date: 01/13/2022
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: zacookmsft
ms.author: zacook
manager: shellyha
ms.openlocfilehash: 602a86a67006925faac00add8e089d28f7071c14
ms.sourcegitcommit: 15b1521041149716f8031cfa6d0dc61a56a5e2ff
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/13/2022
ms.locfileid: "7967750"
---
# <a name="transaction-churn-prediction-preview"></a>Tranzakciólemorzsolódási előrejelzés (előzetes verzió)

A Tranzakciós lemorzsolódási előrejelzés segít megjósolni, ha az ügyfél valószínűleg többé már nem fogja megvásárolni az Ön termékeit vagy szolgáltatásait egy adott játékablakon belül. Új lemorzsolódási előrejelzéseket hozhat létre az **Intelligencia** > **Előrejelzések** menüponton. Az Ön által létrehozott többi előrejelzés megtekintéséhez válassza a **Saját előrejelzések** lehetőséget. 

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWN6Eg]

Üzleti partnereken alapuló környezet esetén a partnerek esetében tranzakciós lemorzsolódást, valamint a partnerek és más szintű információk, például a termékkategóriák kombinációját is megjósolhatjuk. Egy dimenzió hozzáadása segíthet kideríteni, hogy mennyire valószínű, hogy a "Contoso" fiók leállítja az "irodaszerek" termékkategória vásárlását. Ezenkívül az üzleti partnerek esetében az AI segítségével összeállíthatjuk azoknak a lehetséges okoknak a listáját, amelyek miatt a partner valószínűleg lemorzsolódik a másodlagos szintű információk kategóriája miatt.

> [!TIP]
> Próbálja ki az oktatóanyagot egy tranzakciós lemorzsolódási előrejelzés mintaadatok használatával: [Tranzakciós lemorzsolódási előrejelzés (előzetes verzió) útmutató](sample-guide-predict-transactional-churn.md).

## <a name="prerequisites"></a>Előfeltételek

# <a name="individual-consumers-b-to-c"></a>[Egyéni fogyasztók (B-to-C)](#tab/b2c)

- Legalább [közreműködői engedély](permissions.md) a Customer Insightsban.
- Megfelelő üzleti ismeretek, hogy fel tudja mérni, mit jelent a vállalkozás számára a lemorzsolódás. Az idő alapú lemorzsolódás meghatározást támogatjuk, ami azt jelenti, hogy az ügyfelet lemorzsolódottnak tekintjük, egy meghatározott vásárlás nélkül eltelt idő után.
- A tranzakciókkal/vásárlásokkal kapcsolatos adatok és a velük kapcsolatos előzmények:
    - A Tranzakcióazonosítók, hogy meghatározhassa a vásárlásokat/tranzakciókat.
    - Ügyfélazonosítók, egyeztetni a tranzakciókat az ügyfelekkel.
    - Üzleti események dátumai, amely meghatározza a dátumot, amikor a tranzakció történt.
    - A szemantikus adatréteg séma a vásárlásokhoz/tranzakciókhoz a következő információk szükségesek:
        - **Tranzakcióazonosító**: Egy egyedi azonosító a vásárláshoz vagy tranzakcióhoz.
        - **Tranzakció dátuma**: A vásárlás vagy tranzakció dátuma.
        - **A tranzakció értéke**: A pénznembeli/számértékbeli értéke a tranzakciónak/elemnek.
        - (Nem kötelező) **Egyedi termékazonosító**: A megvásárolt termék vagy szolgáltatás azonosítója, ha az adat a sortétel szintjén szerepel.
        - (Nem kötelező) **Amennyiben ez a tranzakció visszatérítés**: Az igaz/hamis mező azonosítja, hogy ez a tranzakció visszatérítés volt-e vagy sem. Ha a **Tranzakció értéke** negatív, ezt az információt is felhasználjuk, a visszatérítés lehetőségeinek kikövetkeztetéséhez.
- (Választható) Adatok az ügyfél tevékenységéről:
    - Az azonos típusú tevékenységek megkülönböztetésére szolgáló tevékenységazonosítók.
    - A tevékenységek ügyfelekhez rendelésére szolgáló ügyfél-azonosítók.
    - A tevékenység adatai a tevékenység nevét és dátumát tartalmazzák.
    - A felhasználói tevékenységekhez tartozó szemantikai adatséma a következőket tartalmazza:
        - **Elsődleges kulcs:** Egy tevékenység egyedi azonosítója. Például, ha egy webhelylátogatás vagy egy használati rekord azt mutatja, hogy az ügyfél kipróbálta az egyik mintatermékét.
        - **Időbélyegző:** Az elsődleges kulcs által azonosított esemény dátuma és időpontja.
        - **Esemény:** A használni kívánt esemény neve. Például, ha egy mező neve "FelhasználóiMűvelet" egy élelmiszerboltban, ez egy ügyfél által történő kuponhasználatot jelenthet.
        - **Részletek:** Részletes információk az eseményről. Például, ha egy mező neve "KuponÉrték" egy élelmiszerboltban, ez a kupon pénznembeli értékét jelentheti.

# <a name="business-accounts-b-to-b"></a>[Üzleti számlák (B-to-B)](#tab/b2b)

- Legalább [közreműködői engedély](permissions.md) a Customer Insightsban.
- Megfelelő üzleti ismeretek, hogy fel tudja mérni, mit jelent a vállalkozás számára a lemorzsolódás. Az idő alapú lemorzsolódás meghatározást támogatjuk, ami azt jelenti, hogy az ügyfelet lemorzsolódottnak tekintjük, egy meghatározott vásárlás nélkül eltelt idő után.
- A tranzakciókkal/vásárlásokkal kapcsolatos adatok és a velük kapcsolatos előzmények:
    - A Tranzakcióazonosítók, hogy meghatározhassa a vásárlásokat/tranzakciókat.
    - Ügyfélazonosítók, egyeztetni a tranzakciókat az ügyfelekkel.
    - Üzleti események dátumai, amely meghatározza a dátumot, amikor a tranzakció történt.
    - A szemantikus adatréteg séma a vásárlásokhoz/tranzakciókhoz a következő információk szükségesek:
        - **Tranzakcióazonosító**: Egy egyedi azonosító a vásárláshoz vagy tranzakcióhoz.
        - **Tranzakció dátuma**: A vásárlás vagy tranzakció dátuma.
        - **A tranzakció értéke**: A pénznembeli/számértékbeli értéke a tranzakciónak/elemnek.
        - (Nem kötelező) **Egyedi termékazonosító**: A megvásárolt termék vagy szolgáltatás azonosítója, ha az adat a sortétel szintjén szerepel.
        - (Nem kötelező) **Amennyiben ez a tranzakció visszatérítés**: Az igaz/hamis mező azonosítja, hogy ez a tranzakció visszatérítés volt-e vagy sem. Ha a **Tranzakció értéke** negatív, ezt az információt is felhasználjuk, a visszatérítés lehetőségeinek kikövetkeztetéséhez.
- (Választható) Adatok az ügyfél tevékenységéről:
    - Az azonos típusú tevékenységek megkülönböztetésére szolgáló tevékenységazonosítók.
    - A tevékenységek ügyfelekhez rendelésére szolgáló ügyfél-azonosítók.
    - A tevékenység adatai a tevékenység nevét és dátumát tartalmazzák.
    - A felhasználói tevékenységekhez tartozó szemantikai adatséma a következőket tartalmazza:
        - **Elsődleges kulcs:** Egy tevékenység egyedi azonosítója. Például, ha egy webhelylátogatás vagy egy használati rekord azt mutatja, hogy az ügyfél kipróbálta az egyik mintatermékét.
        - **Időbélyegző:** Az elsődleges kulcs által azonosított esemény dátuma és időpontja.
        - **Esemény:** A használni kívánt esemény neve. Például, ha egy mező neve "FelhasználóiMűvelet" egy élelmiszerboltban, ez egy ügyfél által történő kuponhasználatot jelenthet.
        - **Részletek:** Részletes információk az eseményről. Például, ha egy mező neve "KuponÉrték" egy élelmiszerboltban, ez a kupon pénznembeli értékét jelentheti.
- (Nem kötelező) Az ügyfelekre vonatkozó adatok:
    - Ezeknek az adatoknak a statikusabb attribútumokhoz kell igazodniuk, hogy biztosítsák a modell legjobb teljesítményét.
    - Az ügyféladatokhoz a szemantikus adatséma a következőket tartalmazza:
        - **CustomerID:** Egy ügyfél egyedi azonosítója.
        - **Létrehozás dátuma:** Az ügyfél kezdeti hozzáadási dátuma.
        - **Állam vagy megye:** Egy ügyfél állama vagy megye helye.
        - **Ország:** Az ügyfél országa.
        - **Iparág:** Az ügyfél iparágtípusa. A kávékatarazóban az "Iparág" nevű mező például arra utalhat, hogy kiskereskedelmi értékesítésben volt-e az ügyfél.
        - **Osztályozás:** A vállalat ügyfeleinek kategorizálása. Például egy kávéfőző "ValueSegment" nevű mezője lehet az ügyfél szintje a vevő mérete alapján.

---

- Javasolt adatjellemzők:
    - Elegendő előzményadat: A tranzakciós adatok a kijelölt időablak legalább duplájához. Lehetőség szerint két-három évnyi tranzakcióelőzmény. 
    - Ügyfelenkénti több vásárlás: Lehetőség szerint ügyfelenként legalább két tranzakció.
    - Ügyfelek száma: Legalább 10 ügyfélprofil, lehetőség szerint 1000-nél több egyedi ügyfél. A modell 10-nél kevesebb ügyfél esetén és ha nem áll rendelkezésre elegendő előzményadat, akkor nem működik.
    - Adat teljessége: A megadott entitás adatmezőjének hiányzó értékeinek kevesebb, mint 20%-a.

> [!NOTE]
> A nagy ügyfélvásárlási gyakoriságú (néhány hetes) üzleti tevékenység esetén ajánlott rövidebb előrejelzési ablak és lemorzsolódás meghatározását választani. Az alacsony vásárlási gyakoriság (néhány havonta vagy évente egyszer) esetén válasszon hosszabb előrejelzési ablakot és lemorzsolódást.

## <a name="create-a-transaction-churn-prediction"></a>Tranzakciólemorzsolódási előrejelzés létrehozása

1. A Customer Insights szolgáltatásban lépjen az **Intelligencia** > **Előrejelzések** részre.

1. Válassza ki az **Ügyféllemorzsolódási modell (előnézet)** csempét, és ott válassza az **A modell használata** menüpontot.

1. A **Vevő lemorzsolódási modell (előnézet)** ablaktáblán válassza a Tranzakció lehetőséget, **és válassza az Első lépések** **lehetőséget**.

:::image type="content" source="media/select-transaction-churn.PNG" alt-text="Képernyőfelvétel a kiválasztott tranzakciós lehetőséggel az Ügyfél-lemorzsolódás modell ablaktáblán.":::
 
### <a name="name-model"></a>Név modell

1. Adja meg a modell nevét; ez különbözteti majd meg a többi modelltől.

1. Adja meg a kimeneti entitás nevét: csak betűket és számokat használjon, szóközök nélkül. Ez lesz az a név, amelyet a modell entitás használni fog. 

1. Válassza a **Következő** lehetőséget.

### <a name="define-customer-churn"></a>Ügyfél-lemorzsolódás meghatározása

1. Állítsa be a **előrejelzés ablakot**. Például, megjósolhatja a lemorzsolódás kockázatát egy ügyfele esetében, a következő 90 napban, hogy ehhez igazíthassa marketingmegőrzési törekvéseit. A lemorzsolódási kockázat becslése egy hosszabb vagy rövidebb időintervallumra megnehezítheti a tényezők kezelését a lemorzsolódási kockázat-profiljában, de ez leginkább az Ön által meghatározott üzleti igényektől függ.
   >[!TIP]
   > A **piszkozatok mentése lehetőség** kiválasztásával bármikor beállíthatja a előrejelzés piszkozatként történő mentéséhez. Ha később folytatni szeretné a munkát, az előrejelzés vázlatát a **Saját előrejelzések** lapon találja majd.

1. Adja meg a lemorzsolódás meghatározásához megadott napok számát a **Lemorzsolódás definíció** mezőben. Például, ha egy ügyfél nem vásárolt az elmúlt 30 napban, vállalkozása számára lemorzsolódónak tekinthető. 

1. A folytatáshoz válassza a **Tovább** lehetőséget.

### <a name="add-required-data"></a>Szükséges adatok hozzáadása

1. Válassza az **Adatok hozzáadása** lehetőséget, és válassza ki azt a tevékenységtípust az oldalsó panelen, amely a tranzakcióhoz vagy a vásárlási előzményekhez szükséges adatokat tartalmazza.

1. A Tevékenységek kiválasztása csoportban **válassza ki az adott tevékenységeket abból a kiválasztott** tevékenységtípusból, amelyre a számítást összpontosítani szeretné.

   :::image type="content" source="media/transaction-churn-select-activity.PNG" alt-text="A szemantikus típus alatti tevékenységek kiválasztását bemutató oldalsó panel.":::

   Ha a tevékenységet még nem képezte le szemantikus típusra, akkor válassza a **Szerkesztés** lehetőséget ehhez. Megnyílik az irányított élmény a szemantikus tevékenységek leképezéséhez. Képezze le az adatokat a kiválasztott tevékenységtípus kapcsolódó mezőihez.

1. A szemantikus attribútumokat a modell futtatásához szükséges mezőkre kell leképezni. Ha az alábbi mezők nincsenek megadva, konfigurálja a kapcsolatokat a beszerzési előzmények entitásából az *Ügyfélentitás* között. Válassza a **Mentés** parancsot.

1. A **Szükséges adatok hozzáadása lépésben válassza a** Tovább gombot **a** folytatáshoz, ha nem szeretne további tevékenységeket hozzáadni.


# <a name="individual-consumers-b-to-c"></a>[Egyéni fogyasztók (B-to-C)](#tab/b2c)

### <a name="add-additional-data-optional"></a>További adatok hozzáadása (nem kötelező)

Konfigurálja az ügyféltevékenység entitásának és az *Ügyfél* entitásnak a kapcsolatát.

1. Válassza ki a mezőt, amely azonosítja az ügyfelet az ügyféltevékenység táblában. Ez közvetlenül kapcsolásra kerülhet *Ügyfél* entitásának Elsődleges ügyfél-azonosítójához.

1. Válassza ki azt az entitást, amely az elsődleges *Ügyfél* entitása.

1. Adjon meg egy olyan nevet, amely jól leírja a kapcsolatot.

#### <a name="customer-activities"></a>Ügyféltevékenységek

1. Tetszés szerint kiválaszthatja az **Adatok felvétele** az **Ügyféltevékenységek**-hezt.

1. Válassza ki a használni kívánt adatokat tartalmazó szemantikus tevékenységtípust, majd a **Tevékenységek** szakaszban jelöljön ki egy vagy több tevékenységet.

1. Válasszon ki egy, az éppen konfigurált ügyféltevékenység típusának megfelelő tevékenységtípust. Válassza az **Új létrehozása** lehetőséget és válasszon ki egy már elérhető tevékenységtípust, vagy hozzon létre egy új típust.

1. Válassza a **Következő**, majd a **Mentés** elemet.

1. Ha más ügyféltevékenységgel is rendelkezik, amelyet fel szeretne venni, ismételje meg a fenti lépéseket.

# <a name="business-accounts-b-to-b"></a>[Üzleti számlák (B-to-B)](#tab/b2b)

### <a name="select-prediction-level"></a>Előrejelzési szint kiválasztása

A legtöbb előrejelzés ügyfélszinten jön létre. Bizonyos esetekben előfordulhat, hogy az üzleti igényeihez nem elég granulált. Ezzel a funkcióval például előre jelezheti egy ügyfél egy ágának lemorzsolódását, nem pedig az ügyfél egészének.

1. Ha előrejelzést szeretne készíteni az ügyfélnél részletesebb szinten, válassza az **Entitás kiválasztása másodlagos szinthez** lehetőséget. Ha a lehetőség nem érhető el, győződjön meg arról, hogy befejezte az előző szakaszt.

1. Bontsa ki azt az entitást, amelyből ki szeretné választani a másodlagos szintet, vagy használja a keresési szűrőt a kiválasztott beállítások szűréséhez.

1. Válassza ki a másodlagos szintként használni kívánt attribútumot, majd válassza a **Hozzáadás** lehetőséget.

1. Válassza a **Következő** lehetőséget.

> [!NOTE]
> Az ebben a szakaszban elérhető entitások azért jelennek meg, mert kapcsolatban állnak az előző részben kiválasztott entitással. Ha nem látja a hozzáadni kívánt entitást, győződjön meg arról, hogy érvényes kapcsolat van a **Kapcsolatokban**. A konfigurációhoz csak egy-az-egyhez és sok-az-egyhez kapcsolatok érvényesek.

### <a name="add-additional-data-optional"></a>További adatok hozzáadása (nem kötelező)

Konfigurálja az ügyféltevékenység entitásának és az *Ügyfél* entitásnak a kapcsolatát.

1. Válassza ki a mezőt, amely azonosítja az ügyfelet az ügyféltevékenység táblában. Ez közvetlenül kapcsolásra kerülhet *Ügyfél* entitásának Elsődleges ügyfél-azonosítójához.

1. Válassza ki azt az entitást, amely az elsődleges *Ügyfél* entitása.

1. Adjon meg egy olyan nevet, amely jól leírja a kapcsolatot.

#### <a name="customer-activities"></a>Ügyféltevékenységek

1. Tetszés szerint kiválaszthatja az **Adatok felvétele** az **Ügyféltevékenységek**-hezt.

1. Válassza ki a használni kívánt adatokat tartalmazó szemantikus tevékenységtípust, majd a **Tevékenységek** szakaszban jelöljön ki egy vagy több tevékenységet.

1. Válasszon ki egy, az éppen konfigurált ügyféltevékenység típusának megfelelő tevékenységtípust. Válassza az **Új létrehozása** lehetőséget és válasszon ki egy már elérhető tevékenységtípust, vagy hozzon létre egy új típust.

1. Válassza a **Következő**, majd a **Mentés** elemet.

1. Ha más ügyféltevékenységgel is rendelkezik, amelyet fel szeretne venni, ismételje meg a fenti lépéseket.

#### <a name="customers-data"></a>Ügyfelek adatai

1. Ha szükséges, válassza az **Adatok hozzáadása** az **Ügyféladatokhoz** lehetőséget.

1. A szemantikus attribútumokat a saját ügyféladatok mezőire leképezi az azonosítottak szerint. A felhasznált mezők adatai nem változhatnak, gyakran a modell optimális teljesítménye érdekében. Például ha kiválaszt egy olyan mezőt az "Osztályozás" számára, amely minden hónapban megváltozott, csak az előrejelzés utolsó értékét használja, annak ellenére, hogy előzményileg ugyanaz az érték nem érvényes a vevőre az előrejelzési minták építésekor.

1. Válassza a **Következő** lehetőséget.

### <a name="provide-an-optional-list-of-benchmark-accounts"></a>Referenciapartnerek nem kötelező listájának megadása

Adja meg a referenciaként használni kívánt üzleti ügyfelek és partnerek listáját. Megkapja a [referenciapartnerek adatait](#review-a-prediction-status-and-results), beleértve a lemorzsolódási pontszámukat és a legbefolyásosabb jellemzőket, amelyek hatással voltak a lemorzsolódásra.

1. Válasza ki a **+ Ügyfél hozzáadása** lehetőséget.

1. Válassza ki a referenciaként használt ügyfeleket.

1. A folytatáshoz válassza a **Tovább** lehetőséget.

---

### <a name="set-schedule-and-review-configuration"></a>Ütemezési és felülvizsgálati konfiguráció beállítása

1. Állítsa be a modell újratanításának gyakoriságát. Ez a beállítás fontos, hogy frissíthesse az előrejelzéseinek pontosságát, ahogy új adat kerül betöltésre. A legtöbb cég havonta egyszer végez újratanítást, és pontos előrejelzésekhez tud jutni.

1. Válassza a **Következő** lehetőséget.

1. Ellenőrizze az előrejelzés konfigurációját. Visszatérhet az előző lépésekre, ha a **Szerkesztés**-re kattint a megjelenő érték alatt. Egy másik lehetőség, hogy kiválaszt egy konfigurációs lépést a folyamatjelzőn.

1. Ha minden érték megfelelően van konfigurálva, akkor az előrejelzési folyamat indításához válassza a **Mentés és Futtatás** lehetőséget. A **Saját előrejelzések** lapon tekintheti meg az előrejelzései állapotát. A folyamat – az előrejelzésben használt adatok mennyiségétől függően – több óráig is tarthat.

## <a name="review-a-prediction-status-and-results"></a>Előrejelzés állapotának és eredményeinek áttekintése

1. Nyissa meg az **Intelligencia** > **Előrejelzések** menüt, és válassza ki a **Saját előrejelzések** lapot.

1. Jelölje ki az áttekinteni kívánt előrejelzést.
   - **Előrejelzés neve**: Az előrejelzés neve, mely a létrehozáskor kerül megadásra.
   - **Előrejelzés típusa**: Az előrejelzéshez használt model típusa
   - **Kimeneti entitás**: Az előrejelzés kimenetének tárolására szolgáló entitás neve. Az ilyen nevű entitások az **Adatok** > **Entitások** részen találhatók.
     A kimenetentitásban a *ChurnScore* a lemorzsolódás, illetve az *IsChurn* egy, a *ChurnScore* értéken alapuló bináris címke, amely 0,5-ös küszöbértéket biztosít. Előfordulhat, hogy az alapértelmezett küszöbérték nem működik a forgatókönyvnél. [Hozzon létre egy új szegmenst](segments.md#create-a-new-segment) az preferált küszöbértékkel.
     Nem minden ügyfél feltétlenül aktív ügyfél. Némelyikük lehet, hogy már hosszú ideje nem végzett tevékenységet, és a már lemorzsolódottnak számít – az Ön lemorzsolódási definíciójától függően. A már lemorzsolódott ügyfeleknél a lemorzsolódási kockázat előrejelzése nem hasznos, mert nem ők az érdeklődő célközönség.
   - **Várható mező**: Ez a mező csak bizonyos típusú előrejelzésekhez megadható, és nem használható a lemorzsolódási előrejelzéshez.
   - **Állapot**: A futtatott előrejelzés állapota.
        - **Feldolgozási sorban**: Az előrejelzés további folyamatok futtatására vár.
        - **Frissítés**: Az előrejelzés jelenleg fut, hogy a kimeneti entitásba kerülő eredményt produkálhassa.
        - **Sikertelen**: Az előrejelzés lefuttatása sikertelen. [Ellenőrizze a naplókat](manage-predictions.md#troubleshoot-a-failed-prediction) a további részletekért.
        - **Sikeres**: Az Előrejelzés lefuttatása sikeresen megtörtént. Az előrejelzés megtekintéséhez válassza a függőleges pontok alatt lévő **Megtekintés** lehetőséget.
   - **Szerkesztve**: Az előrejelzés konfigurációjának módosítási dátuma.
   - **Legutóbbi frissítés**: A dátum, amikor az előrejelzés frissítette a kimeneti entitásban szereplő eredményeket.

1. Kattintson a függőleges pontok ikonjára azon előrejelzés mellett, amelynek meg szeretné tekinteni az eredményeit, és kattintson a **Megtekintés** elemre.

   :::image type="content" source="media/model-subs-view.PNG" alt-text="Tekintse meg az előrejelzés eredményeit a vezérlőn.":::

# <a name="individual-consumers-b-to-c"></a>[Egyéni fogyasztók (B-to-C)](#tab/b2c)

1. Az eredményoldalon lévő adatok három fő részben jelennek meg:
   - **Betanítási modell teljesítménye**: A lehetséges értékek az A, B vagy C. Ez a pontszám jelzi az előrejelzés teljesítményét, és könnyebbé teheti a kimeneti entitásban tárolt eredmények használatára vonatkozó döntést. A pontszámok meghatározása a következő szabályok alapján történik: 
        - **A** amikor egy modell legalább 50%-ban pontos az összes előrejelzéshez mérten, és amikor a pontos előrejelzések százalékos aránya a lemorzsolódó ügyfelekről nagyobb, mint a viszonyítási alapérték, ami a legalább 10%.
            
        - **B** amikor egy modell legalább 50%-ban pontos az összes előrejelzéshez mérten, és amikor a pontos előrejelzések százalékos aránya a lemorzsolódó ügyfelekről nagyobb, mint 10%, ami nagyobb, mint a viszonyítási alapérték.
            
        - **C** amikor egy modell előrejelzése kevesebb, mint 50%-ban pontos, vagy amikor a pontos előrejelzések százalékos aránya a lemorzsolódó ügyfelekről kisebb, mint a viszonyítási alapérték.
               
        - Az **Alapérték** adja meg az előrejelzés idejét a modell bemeneti ablakán (például egy év), és a modell létrehozza a különböző időrészleteket, azáltal, hogy kettéosztja, amíg az el nem éri az egy hónap vagy kevesebbet. Ezen töredékek segítségével üzleti szabályokat hozhat létre azon ügyfeleknek, akik nem vásároltak ebben az időkeretben. Ezek az ügyfelek lemorzsolódónak vannak tekintve. Az idő alapú üzleti szabály rendelkezik a legnagyobb képességgel, hogy előre jelezhesse, ki a fog a legvalószínűbben lemorzsolódni, a megadott alapérték modellen.
            
    - **Lemorzsolódási valószínűség (ügyfelek száma)**: Ügyfelek csoportjai a lemorzsolódás előrejelzett kockázata alapján. Ez az adat a későbbiekben segítséget jelenthet, ha magas lemorzsolódási kockázattal rendelkező ügyfelekhez szeretne szegmenst létrehozni. Az ilyen szegmensek segítségével felmérheti, hogy a szegmens tagsága esetén hol legyen a lezárás.
       
    - **Legbefolyásosabb tényezők**: Az előrejelzés létrehozásakor a rendszer számos tényezőt vesz figyelembe. A tényezők mindegyikének megvan a fontossága, az összesített előrejelzés számításaiban, melyet a modell hoz létre. Ezeket a tényezőket a saját eredményének előrejelzés, illetve később felhasználhatja ezeket az információkat olyan [szegmensek létrehozásához](segments.md), amelyek befolyásolhatják az ügyfelek számára a dezinformáció kockázatát.


# <a name="business-accounts-b-to-b"></a>[Üzleti számlák (B-to-B)](#tab/b2b)

1. Az eredményoldalon lévő adatok három fő részben jelennek meg:
   - **Betanítási modell teljesítménye**: A lehetséges értékek az A, B vagy C. Ez a pontszám jelzi az előrejelzés teljesítményét, és könnyebbé teheti a kimeneti entitásban tárolt eredmények használatára vonatkozó döntést. A pontszámok meghatározása a következő szabályok alapján történik: 
        - **A** amikor egy modell legalább 50%-ban pontos az összes előrejelzéshez mérten, és amikor a pontos előrejelzések százalékos aránya a lemorzsolódó ügyfelekről nagyobb, mint a viszonyítási alapérték, ami a legalább 10%.
            
        - **B** amikor egy modell legalább 50%-ban pontos az összes előrejelzéshez mérten, és amikor a pontos előrejelzések százalékos aránya a lemorzsolódó ügyfelekről nagyobb, mint 10%, ami nagyobb, mint a viszonyítási alapérték.
            
        - **C** amikor egy modell előrejelzése kevesebb, mint 50%-ban pontos, vagy amikor a pontos előrejelzések százalékos aránya a lemorzsolódó ügyfelekről kisebb, mint a viszonyítási alapérték.
               
        - Az **Alapérték** adja meg az előrejelzés idejét a modell bemeneti ablakán (például egy év), és a modell létrehozza a különböző időrészleteket, azáltal, hogy kettéosztja, amíg az el nem éri az egy hónap vagy kevesebbet. Ezen töredékek segítségével üzleti szabályokat hozhat létre azon ügyfeleknek, akik nem vásároltak ebben az időkeretben. Ezek az ügyfelek lemorzsolódónak vannak tekintve. Az idő alapú üzleti szabály rendelkezik a legnagyobb képességgel, hogy előre jelezhesse, ki a fog a legvalószínűbben lemorzsolódni, a megadott alapérték modellen.
            
    - **Lemorzsolódási valószínűség (ügyfelek száma)**: Ügyfelek csoportjai a lemorzsolódás előrejelzett kockázata alapján. Ez az adat a későbbiekben segítséget jelenthet, ha magas lemorzsolódási kockázattal rendelkező ügyfelekhez szeretne szegmenst létrehozni. Az ilyen szegmensek segítségével felmérheti, hogy a szegmens tagsága esetén hol legyen a lezárás.
       
    - **Legbefolyásosabb tényezők**: Az előrejelzés létrehozásakor a rendszer számos tényezőt vesz figyelembe. A tényezők mindegyikének megvan a fontossága, az összesített előrejelzés számításaiban, melyet a modell hoz létre. Ezeket a tényezőket a saját eredményének előrejelzés, illetve később felhasználhatja ezeket az információkat olyan [szegmensek létrehozásához](segments.md), amelyek befolyásolhatják az ügyfelek számára a dezinformáció kockázatát.


1. Üzleti partnerek esetén találni fog egy **Befolyásoló funkciók elemzése** nevű információs oldalt. A következő négy adatszakaszt tartalmazza:

    - A jobb oldali ablaktáblában kiválasztott elem határozza meg az oldal tartalmát. Jelöljön ki egy elemet a **Tegjobb ügyfelekből** vagy a **Referenciaügyfelekből**. A két lista csökkenő lemorzsolódási értékkel van megrendelve, attól függően, hogy a pontszám csak az ügyfélnek, vagy egy összesített pontszámnak megfelelő az igénybe vett számára, valamint egy másodlagos szint, például a termékkategória.
        
        - **A legjobb ügyfelek**: 10 olyan ügyfélből állnak, akik a legnagyobb ki vannak tévelyedve, és a legalacsonyabb a úúgó pontszámok alapján. 
        - **Teljesítményteszt-ügyfelek**: A modell konfigurálásakor kiválasztott legfeljebb 10 ügyfél listája.
 
    - **Lesiklott pontszám**: A jobb oldali ablaktáblában kiválasztott elem lemorzsolódási pontszámának megjelenítése.
    
    - **Lemorzsolódási kockázatok eloszlása**: A lemorzsolódási kockázatok eloszlását mutatja az ügyfelek között, valamint azt a százalékos terjedést, amelyben a kijelölt ügyfél van. 
    
    - **A növekvő és csökkenő lemorzsolódási kockázatok legfontosabb funkciói**: A jobb oldali ablaktáblában kiválasztott elem esetén a listában az az öt legjobb funkció szerepel, amely megnövelte és csökkentette a lemorzsolódási kockázatot. Minden jellemzőnél megtalálja a funkció értékét az adott elemhez, valamint azt, hogy mi a hatása a lemorzsolódási pontra. Az egyes szolgáltatások átlagos értéke alacsony, közepes és magas ügyfélszegmensenként is megjelenik. Segít jobban kontextusba helyezni a kiválasztott elemre gyakorolt legnagyobb hatású szolgáltatások értékeit, és összehasonlítani az alacsony, közepes és nagy forgalmú ügyfélszegmensekkel.

       - Alacsony: partnerek vagy a partner és a másodlagos szint kombinációi, 0 és 0,33 közötti lemorzsolódási pontszámmal
       - Közepes: partnerek vagy a partnerek és a másodlagos szintek kombinációi, 0,33 és 0,66 közötti lemorzsolódási pontszámmal
       - Magas: partnerek vagy a partnerek és a másodlagos szintek kombinációi, 0,66-nál nagyobb lemorzsolódási pontszámmal
    
       Amikor a partnerek szintjén előrejelzi a lemorzsolódástt, minden egyes partnert figyelembe kell venni a lemorzsolódási szegmensek átlagos funkcióértékének összefésülésében. A másodlagos szinten minden egyes fióknál a lemorzsolódási szegmensek kijelzése az oldalpanelen kiválasztott elem másodlagos szintjétől függ. Ha például egy tételnek a termékkategóriák másodlagos szintje = irodai felszerelések, akkor csak azok a cikkek számítanak termékkategóriának, amelyekhez irodai felszerelések tartoznak, amikor a lemorzsolódási szegmensek átlagos funkcióértékét számítja ki. Ez a logika biztosítja, hogy a program megfelelő összehasonlítást alkalmaz a elem funkcióértékeivel az alacsony, közepes és nagy lemorzsolódási szegmensek átlagos értékeivel.

       Bizonyos esetekben az alacsony, közepes vagy nagy lemorzsolódási szegmensek átlagos értéke üres vagy nem érhető el, mivel a fenti definíció alapján nem érhetők el elemek, amelyek a megfelelő piaci szegmenshez tartoznak.
       
       > [!NOTE]
       > Az átlagos alacsony, a közepes és a magas oszlopok alatti értékek értelmezése eltérő a kategorikus funkciók (például az ország vagy az iparág) esetében. Mivel az „átlag” funkcióérték nem vonatkozik a kategorikus funkciókra, az ezekben az oszlopokban található értékek az alacsony, a közepes vagy a magas lemorzsolódási szegmensek olyan hányadai, amelyek a kategorikus funkcióval azonos értékkel rendelkeznek az oldalpanelen kiválasztott elemhez képest.

---

## <a name="manage-predictions"></a>Előrejelzések kezelése

Lehetőség van az előrejelzések optimalizálására, hibaelhárítására, frissítésére vagy törlésére. Tekintse át a bemeneti adatok használhatósági jelentését, hogy megtudja, hogyan lehet egy előrejelzés gyorsabb és megbízhatóbb. További információért ugorjon az [Előrejelzések kezelése](manage-predictions.md) részhez.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
