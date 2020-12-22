---
title: Szegmensek létrehozása és kezelése
description: Hozzon létre ügyfelekből álló szegmenseket, és csoportosítsa őket különböző attribútumok alapján.
ms.date: 10/15/2020
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
ms.reviewer: jimsonc
manager: shellyha
ms.openlocfilehash: 6931110c2ae93cd2792d319aa5a34f0df3088552
ms.sourcegitcommit: cf9b78559ca189d4c2086a66c879098d56c0377a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/03/2020
ms.locfileid: "4406030"
---
# <a name="create-and-manage-segments"></a>Szegmensek létrehozása és kezelése

A szegmensek segítségével csoportosíthatja ügyfeleit demográfiai-, tranzakciós- vagy viselkedési tulajdonságok alapján. A szegmensekkel népszerűsítheti az üzleti célok eléréséhez használható promóciós kampányokat, értékesítési tevékenységeket és ügyfélszolgálati tevékenységeket.

Összetett szűrőket adhat meg az Ügyfélprofil entitás és kapcsolódó entitásai körül. A feldolgozást követően minden szegmens létrehoz egy csoport olyan ügyfélrekordot, amellyel az exportálás után műveletek végezhetők. Bizonyos [szolgáltatási korlátozások](service-limits.md) érvényesek.

Ha nincsen másként meghatározva, minden szegmens **Dinamikus szegmens**, amelyek ismétlődő ütemezés alapján frissítésre kerülnek.

A következő példa bemutatja a szegmentációs képességet. Egy szegmenst definiáltak azokhoz az ügyfelekhez, akik legalább $500 értékben árukat rendeltek az utolsó 90 napban, *és* részt vettek egy ügyfélszolgálat-hívásban, amelyet eszkaláltak.

> [!div class="mx-imgBorder"]
> ![Több csoport](media/segmentation-group1-2.png "Több csoport")

## <a name="create-a-new-segment"></a>Új szegmens létrehozása

A szegmensek kezelése a **Szegmensek** oldalon történik.

1. A célközönség információkban nyissa meg a **Szegmensek** oldalt.

2. Válassza az **új** > **üres szegmens** lehetőséget.

3. Az **Új szegmens** ablaktáblában válasszon egy szegmenstípust, és adja meg a **Név** értékét.

   Tetszés szerint megadhat egy megjelenítendő nevet és egy leírást is, amely segít a szegmens azonosításában.

4. Válassza a **Következő** elemet a **Szegmensépítő** oldalára való eljutáshoz, ahol megadhat egy csoportot. A csoport az ügyfelek halmaza.

5. Válassza ki az entitást, amelyben szerepel az attribútum, amely alapján szegmentálni szeretne.

6. Válassza ki a szegmenshez tartozó attribútumot. Ez az attribútum a következő négy értéktípus egyike lehet: numerikus, szöveges, dátum vagy logikai.

7. Válasszon egy operátort, és adja meg a kijelölt attribútum értékét.

   > [!div class="mx-imgBorder"]
   > ![Egyéni csoportszűrő](media/customer-group-numbers.png "Ügyfélcsoportszűrő")

   |Szám |Definíció  |
   |---------|---------|
   |1     |Entity          |
   |2     |Attribútum          |
   |3    |Operátor         |
   |4    |Érték         |

8. Ha az entitás [kapcsolatokon](relationships.md) keresztül kapcsolódik az egyesített ügyfél entitáshoz, meg kell határoznia a kapcsolati útvonalat az érvényes szegmens létrehozásához. Adjon hozzá entitásokat a kapcsolati útvonalról, amíg ki nem tudja választani az **Ügyfél: CustomerInsights** entitást a legördülő menüből. Ezután válassza ki az **Összes rekordot** minden egyes feltételnél.

   > [!div class="mx-imgBorder"]
   > ![Kapcsolati útvonal a szegmens létrehozása során](media/segments-multiple-relationships.png "Kapcsolati útvonal a szegmens létrehozása során")

9. Válassza a **Mentés** lehetőséget a szegmens mentéséhez. A rendszer menti a szegmenst és feldolgozza, ha az összes követelményt ellenőrizte. Ellenkező esetben vázlatként menti a program.

10. A **Szegmensek** oldalra a **Vissza a szegmensekhez** elemre kattintva léphet vissza.

## <a name="manage-existing-segments"></a>Meglévő szegmensek kezelése

A **szegmensek** lapon megtekintheti az összes mentett szegmenst, és kezelheti azokat.

Minden szegmenshez egy sor tartozik; ez a sor további információkat tartalmaz a szegmensről.

A szegmenseket az oszlop fejlécének kiválasztásával rendezheti egy oszlopba.

A jobb felső sarokban lévő **Keresés** mezővel szűrheti a szegmenseket.

> [!div class="mx-imgBorder"]
> ![Meglévő szegmensek kezelésére szolgáló lehetőségek](media/segments-selected-segment.png "Meglévő szegmensek kezelésére szolgáló lehetőségek")

Szegmens kiválasztása esetén a következő művelet használható:

- **Megtekintés** a szegmens részleteinek, köztük a tagszám trendjének megtekintése és a szegmens tagjainak előnézete.
- **Szerkesztés** a szegmens szerkesztése a tulajdonságainak módosításához.
- **Frissítés** a szegmens frissítése a legfrissebb adatok felvételéhez.
- Szegmens **Aktiválása** vagy **inaktiválása**. A szegmensek két lehetséges állapottal rendelkeznek – aktívak vagy inaktívak. A szegmensek szerkesztésekor hasznosnak bizonyulnak ezek az állapotok. Inaktív szegmensek esetén a szegmens definíciója létezik, de még nem tartalmaz ügyfeleket. A szegmens aktiválásakor az állapota az "inaktív" értékről "aktív" állapotra változik, és a szegmens meghatározásnak megfelelő ügyfeleket keresi meg. Ha egy [ütemezett frissítés](system.md#schedule-tab) be van állítva, az inaktív szegmensek **állapota** **kihagyva** állapotú , jelezve, hogy a frissítést nem is kísérelte meg. Inaktív szegmens aktiválásakor a rendszer frissíti, és bekerül az ütemezett frissítésekbe.
  Másik lehetőségként használhatja **Ütemezés később** funkcióit az **Aktiválás/inaktiválás**, ahol megadhat egy adott szegmens aktiválására és inaktiválására vonatkozó jövőbeli dátumot és időpontot.
- Szegmens **átnevezése**.
- A tagok listájának **letöltése** .CSV fájlként.
- A **Hozzáadás ehhez:** lehetőség a szegmensben szereplő ügyfelek azonosítóinak listáját egy másik alkalmazásban feldolgozásra küldi.
- Szegmens **törlése**.

## <a name="refresh-segments"></a>Szegmensek frissítése

Az összes szegmenst egyszerre frissítheti a **Szegmensek** oldal **Az összes frissítése** elemével. Ha nem szeretné frissíteni az összes szegmenst, jelölje ki a frissítendőket, és válassza a **Frissítés** lehetőséget a beállítások között. Másik lehetőségként beállíthat egy ismétlődő frissítést is a **Felügyelet** > **Rendszer** > **Ütemezés** pontban.

> [!TIP]
> A feladatokhoz/folyamatokhoz [hatféle állapot](system.md#status-types) tartozhat. Emellett a legtöbb folyamat [más alsóbb szintű folyamatoktól is függ](system.md#refresh-policies). Kiválaszthatja egy folyamat állapotát, és megtekintheti a hozzá tartozó teljes feladat folyamatának részleteit. Miután kiválasztotta a **Részletek megtekintése** lehetőséget a feladat egyik feladatához, további információk jelennek meg: feldolgozási idő, legutóbbi feldolgozás dátuma, és a feladathoz társított összes hiba és figyelmeztetés.

## <a name="download-and-export-segments"></a>Szegmensek letöltése és exportálása

A szegmensek egy CSV-fájlba tölthetők le, illetve exportálhatók a Dynamics 365 Sales programba.

### <a name="download-segments-to-a-csv-file"></a>Szegmensek letöltése CSV-fájlba

1. A célközönség információkban nyissa meg a **Szegmensek** oldalt.

2. Jelöljön ki egy adott szegmens csempéjében a három pontot.

3. A műveletek legördülő listáról válassza a **Letöltés CSV-ként** lehetőséget.

### <a name="export-segments-to-dynamics-365-sales"></a>Szegmensek exportálása a Dynamics 365 Sales alkalmazásba

Mielőtt exportálja a szegmenseket a Dynamics 365 Sales programba, egy rendszergazdának [létre kell hoznia az exportálási célhelyet](export-destinations.md) a Dynamics 365 Sales-hez.

1. A célközönség információkban nyissa meg a **Szegmensek** oldalt.

2. Jelöljön ki egy adott szegmens csempéjében a három pontot.

3. Válassza a **Hozzáadás** lehetőséget a Műveletek legördülő listából, és jelölje ki az exportálni kívánt célhelyet.

## <a name="draft-mode-for-segments"></a>Vázlat mód szegmensekhez

Ha a szegmens feldolgozására vonatkozó összes követelmény nem teljesül, vázlatként mentheti a szegmenst, és hozzáférhet a **Szegmensek** oldalról.

Inaktív szegmensként menti a program, és mindaddig nem aktiválható, amíg érvényes nem lesz.

## <a name="add-more-conditions-to-a-group"></a>További feltételek hozzáadása csoporthoz

Ha további feltételeket szeretne hozzáadni egy csoporthoz, akkor két logikai operátort használhat:

- **ÉS** operátor: mindkét feltételnek a szegmentálási folyamat részeként kell teljesülnie. Ez a beállítás akkor a leghasznosabb, ha különböző entitások között határoz meg feltételeket.

- **VAGY** operátor: a szegmentálási folyamat részeként az egyik feltételnek meg kell felelnie. Ez a beállítás akkor a leghasznosabb, ha különböző feltételeket ad meg ugyanahhoz az entitáshoz.

   > [!div class="mx-imgBorder"]
   > ![VAGY operátor, ahol valamelyik feltételt teljesíteni kell](media/segmentation-either-condition.png "VAGY operátor, ahol valamelyik feltételt teljesíteni kell")

Jelenleg lehetséges egy **VAGY** operátor beágyazása egy **ÉS** operátor alá, de fordítva nem.

## <a name="combine-multiple-groups"></a>Több csoport egyesítése

Mindegyik csoport adott ügyfelek csoportját hoz létre. A csoportok kombinálásával szerepeltetheti a vállalati esethez szükséges ügyfeleket.

1. A célközönség információkban nyissa meg a **Szegmens** oldalt, és válasszon egy szegmenst.

2. Válassza a **Csoport hozzáadása** lehetőséget.

   > [!div class="mx-imgBorder"]
   > ![Ügyfélcsoport hozzáadása csoport](media/customer-group-add-group.png "Ügyfélcsoport hozzáadása csoport")

3. Válasszon az alábbi operátorok közül: **Halmaz**, **Metszet** vagy **Kivéve**.

   > [!div class="mx-imgBorder"]
   > ![Ügyfélcsoport hozzáadása egyesülés](media/customer-group-union.png "Ügyfélcsoport hozzáadása egyesülés")

   Egy beállított operátor kiválasztásával új csoportot adhat meg. Különböző csoportok elmentésével határozza meg, hogy melyik adatok megtartandók:

   - Az **Egyesülés** egyesíti a két csoportot.

   - A **Metszet** a két csoport átfedését veszi. Csak az az adat *amely közös* kerül megtartásra mindkét egységesített csoportban.

   - **Kivéve** kombinálja a két csoportot. Csak azon adat kerül megtartásra az A csoportban, amely *nem közös* a B csoport adatival.

## <a name="view-processing-history-and-segment-members"></a>A feldolgozási előzmények és a szegmenstagok megtekintése

A szegmensre vonatkozó konszolidált adatokat a részleteinek áttekintésével tekintheti meg.

A **Szegmens** lapon válassza ki az áttekinteni kívánt szegments.

Az oldal felső részén egy trendgráf látható, amely a tagok számának változásait ábrázolja. Vigye az egérmutatót az adatpontok fölé, és tekintse meg egy adott napon a tagok számát.

Frissítheti az ábrázolás időkeretét.

> [!div class="mx-imgBorder"]
> ![Szegmens időtartománya](media/segment-time-range.png "Szegmens időtartománya")

Az alsó rész a szegmenstagok listáját tartalmazza.

> [!NOTE]
> Az adott listában megjelenő mezők a szegmens entitásainak attribútumain alapulnak.
>
>A lista az egyeztetett szegmestagok előzetes verziója, és a szegmens első 100 rekordját mutatja, így gyorsan kiértékelheti, és szükség esetén felülvizsgálhatja a meghatározásokat. Az összes egyező bejegyzés megjelenítéséhez [exportálnia kell a szegmenst](export-destinations.md).

## <a name="quick-segments"></a>Gyors szegmens

A szegmensszerkesztőn kívül van még egy módja a szegmensek létrehozásának. A gyors szegmensek segítségével gyorsan és azonnali betekintő információkkal hozhat létre egyszerű szegmenseket egyetlen operátorral.

1. A **szegmensek** lapon válassza az **új** > **Gyorslétrehozási űrlap** elemet.

   - Válassza a **profilok** lehetőséget, ha az egyesített Ügyfél entitáson alapuló szegmenset szeretne létrehozni.
   - Válassza az **Mérőszámok** lehetőséget, ha a **Mérőszámok** oldalon korábban létrehozott Ügyfélattribútum típusú mérőszámok mindegyikéhez szeretne szegmenst létrehozni.
   - Válassza az **Információ** lehetőséget, ha egy szegmenst szeretne létrehozni az egyik olyan kimeneti entitás köré, amelyet vagy az **Előrejelzések** vagy az **egyéni modellek** használatával hozott létre.

2. Az **új gyors szegmens** párbeszédpanelen jelöljön ki egy attribútumot a **Mező** legördülő listában.

3. A rendszer néhány további betekintést biztosít, amelyek segítségével jobb szegmenseket hozhat létre az ügyfelek számára.
   - A kategorikus mezők esetén 10 első számú ügyfél számít. Válasszon egy **Értéket**, és válassza a **Felülvizsgálat** elemet.

   - Numerikus attribútumok esetében a rendszer azt mutatja, hogy az egyes ügyfelek percentilis értékei alá milyen attribútumértékek tartoznak. Válasszon egy **operátort** és egy **értéket**, majd válassza a **Felülvizsgálat** lehetőséget.

4. A rendszer megadja a **Becsült szegmensméret** értékét. Kiválaszthatja, hogy létrehozza-e a megadott szegmenst, vagy először újra meg szeretné vizsgálni, hogy egy másik szegmens méretet kap-e.

    > [!div class="mx-imgBorder"]
    > ![Gyorsszegmens neve és becslése](media/quick-segment-name.png "Gyorsszegmens neve és becslése")

5. Adjon meg egy **Név** értéket a szegmens számára. Másik lehetőségként adjon meg **Megjelenítendő nevet**.

6. Válassza a **Mentés** lehetőséget a szegmens létrehozásához.

7. Miután a szegmens befejezte a feldolgozást, megtekintheti azt a létrehozott többi szegmenshez hasonlóan.

A következő esetekben javasoljuk, hogy ne a javasolt szegmensek lehetőséget használja, hanem a szegmensépítő használatát:

- Szegmensek létrehozása szűrőkkel kategorikus mezőkön, ahol az operátor eltér a **Létezik** operátortól
- Szegmensek létrehozása szűrővel azoknál a numerikus mezőknél, ahol az operátor más, mint a **Között**, **Nagyobb, mint** és **Kisebb, mint** operátor
- A szegmensek létrehozása szűrőkkel a dátum típusú mezőkön

## <a name="next-steps"></a>Következő lépések

[Exportáljon egy szegmenst](export-destinations.md), és fedezze fel az [Ügyfélkártya](customer-card-add-in.md) és [Összekötők](export-power-bi.md) elemeket, az ügyfélszintű információkhoz.
