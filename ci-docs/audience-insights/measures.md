---
title: Mértékek létrehozása és felügyelete
description: Definiálja a vállalkozás teljesítményét elemző és tükröző mértékeket.
ms.date: 04/12/2021
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: wameng
ms.reviewer: mhart
manager: shellyha
ms.openlocfilehash: 9a94a32a04f2a8beb661c27271fe96f23d998722
ms.sourcegitcommit: d89b19b2a3497722b78362aeee688ae7e94915d9
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/13/2021
ms.locfileid: "5887943"
---
# <a name="define-and-manage-measures"></a>Az intézkedések definiálása és kezelése

A mértékek segítségével az ügyfelek viselkedése és üzleti teljesítménye jobban érthető. Az [egyesített profilokból](data-unification.md) származó releváns értékeket veszik alapul. Egy vállalat például az *ügyfélenkénti teljes kiadást* szeretné látni, hogy megértsék az egyes ügyfelek vásárlási előzményeit, vagy lemérjék a *vállalat teljes értékesítéseit*, hogy megértsék a teljes vállalat összesítési szintű bevételét.  

Az mértékek létrehozása a mértékkészítővel történik, ami egy adatlekérdezési platform számos operátorral és egyszerű leképezési lehetőségekkel. Lehetőséget ad az adatok szűrésére, az eredmények csoportosítására, az [entitáskapcsolatok elérési útjainak](relationships.md) észlelésére és a kimenet előnézetére.

A mértékszerkesztő segítségével üzleti tevékenységeket tervezhet az ügyféladatok lekérdezésével és a betekintések kinyerésével. Ha például egy *ügyfélre jutó teljes költség* és az *egy ügyfélre jutó teljes megtérülés* mértékeket hozza létre, akkor könnyebben azonosítható a nagy költéssel, mégis nagy megtérüléssel jellemezhető ügyfelek csoportja. A következő legjobb műveletek előremozdításához [létrehozhat egy szegmenst](segments.md). 

## <a name="build-your-own-measure-from-scratch"></a>Saját mérték létrehozása az alapoktól

Ez a rész végigvezeti egy új mértéknek a nulláról való létrehozásán. Az Ügyfél entitáshoz kapcsolattal beállított adatentitások adatattribútumainak segítségével mértéket állíthat össze. 

1. A célközönség információin belül nyissa meg a következőt: **Mérőszámok**.

1. Válassza az **Új** lehetőséget, és válassza a **Saját elkészítése** lehetőséget.

1. Válassza a **Név szerkesztése** lehetőséget, és adjon **Nevet** a mértéknek. 
   > [!NOTE]
   > Ha az új mértékkonfigurációban csak két mező található , például, CustomerID és egy számítás – a kimenet új oszlopként kerül fel a rendszer által létrehozott Customer_Measure nevű entitáshoz. A mérték értéke pedig az egyesített ügyfélprofilban is látható. Más mértékek létrehozzák a saját entitásaikat.

1. Válassza a konfigurációs területen az összesítési függvényt a **Függvény kiválasztása** legördülő menüből. Az összesítési függvények többek között a következők: 
   - **Sum**
   - **Átlag**
   - **Számlálás**
   - **Egyedszámlálás**
   - **Max**
   - **Min**
   - **Első:** az adatrekord első értékét veszi fel
   - **Utolsó**: az adatrekordhoz hozzáadott utolsó értéket veszi fel

   :::image type="content" source="media/measure-operators.png" alt-text="A mértékek számításához használható operátorok.":::

1. Válassza az **Attribútum hozzáadása** lehetőséget a mérték létrehozásához szükséges adatok kiválasztásához.
   
   1. Válassza az **Attribútumok** lapot. 
   1. Adatentitás: Válassza ki azt az entitást, amely a mérni kívánt attribútumot tartalmazza. 
   1. Adatattribútum: Válassza ki az összesítési függvényben az mérték kiszámításához használni kívánt attribútumot. Egyszerre csak egy attribútumot választhat ki.
   1. Meglévő mértékből is kiválaszthat adatattribútumokat a **Mértékek** lapon. Másik lehetőségként megkeresheti egy entitást vagy mérték nevét is. 
   1. Válassza a **Hozzáadás** lehetőséget, ha a kijelölt attribútumot hozzá szeretne adni a mértékhez.

   :::image type="content" source="media/measure-attribute-selection.png" alt-text="Válassza ki a számításokban használni kívánt attribútumot.":::

1. Összetettebb mértékek építéshez további attribútumokat adhat hozzá, vagy használhat operátorokat a mértékfüggvényben.

   :::image type="content" source="media/measure-math-operators.png" alt-text="Hozzon létre egy összetett mértéket a matematikai műveletek segítségével.":::

1. Szűrők hozzáadásához válassza ki a **Szűrő** lehetőséget a konfigurációs területen. 
  
   1. A **Szűrők** panel **Attribútum hozzáadása** szakaszában jelölje ki a szűrők létrehozásához használni kívánt attribútumot.
   1. Állítsa be a szűrőoperátorokat, hogy minden kijelölt attribútumhoz definiálja a szűrőt.
   1. Válassza az **Alkalmaz** lehetőséget, ha a szűrőket hozzá szeretne adni a mértékhez.

1. Dimenziók hozzáadásához válassza ki a **Dimenzió** lehetőséget a konfigurációs területen. A dimenziók oszlopként fognak megjelenni a mérték kimeneti entitásában.
   1. Válassza a **Dimenziók szerkesztése** lehetőséget, ha olyan adatattribútumokat szeretne felvenni, amelyek szerint csoportosítja a mértékeket. Például város vagy nem. Az *ügyfélszintű mértékek* létrehozásához alapértelmezés szerint a *CustomerID* dimenzió van kiválasztva. Ha *üzleti szintű mértékeket* szeretne létrehozni, eltávolíthatja az alapértelmezett dimenziót.
   1. Válassza a **Kész** lehetőséget, ha a dimenziókat hozzá szeretne adni a mértékhez.

1. Ha vannak olyan értékek az adatokban, amelyeket egész számra kell lecserélni, például a *null* értéket *0* értékkel, akkor válassza a **Szabályok** lehetőséget. Konfigurálja a szabályt, és csak egész számokat válasszon csereként.

1. Ha a leképezett adatentitás és az *Ügyfél* entitás között több elérési út is van, válasszon egyet az azonosított [entitáskapcsolat-útvonalak közül](relationships.md). A mértékek eredményei a kiválasztott elérési úttól függően változhatnak. 
   1. Válassza ki az **Adatbeállítások** lehetőséget, és válassza ki az entitás elérési útját, amely a mérték azonosítására fog használni. Ha az *Ügyfél* entitásnak csak egyetlen elérési útja van, akkor a vezérlő nem fog mutatni.
   1. Válassza a **Kész** lehetőséget a kiválasztás alkalmazáshoz. 

   :::image type="content" source="media/measures-data-preferences.png" alt-text="Válassza ki a mértékhez tartozó entitás elérési utat.":::

1. Ha további számításokat szeretne hozzáadni az mértékhez, válassza az **Új számítás** lehetőséget. Az új számításokhoz csak ugyanazon az entitás elérési úton használhatók entitások. A további számítások új oszlopként fognak megjelenni a mérték kimeneti entitásában.

1. Válassza a **...** lehetőséget a mértékből szármató számítás **Duplikálásához**, **Átnevezéséhez** vagy **Eltávolításához**.

1. Az **Előnézet** területen a mérték kimeneti entitásának adatsémáját látja a szűrőkkel és a dimenziókkal. Az előnézet dinamikusan reagál a konfiguráció változásaira.

1. Válassza a **Futtatás** lehetőséget a konfigurált mértékhez tartozó eredmények kiszámításához. Válassza a **Mentés és bezárás** lehetőséget, ha meg szeretné tartani az aktuális konfigurációt, és a mértéket később szeretné futtatni.

1. A listában az újonnan létrehozott mértékegységet a **Mértékek** listában jelenítheti meg.

## <a name="use-a-template-to-build-a-measure"></a>Sablon használata mértékek építéséhez

A leggyakrabban használt mértékeket előre definiált sablonok segítségével hozhatja létre. A sablonok részletes leírása és az interaktív élmény segít a hatékony mérték létrehozásában. A sablonok az *Egyesített tevékenység* entitásból származó leképezett adatokra épülnek. Ezért mindenképpen konfiguráljon [ügyféltevékenységeket](activities.md), mielőtt sablonból hoz létre mértéket.

Elérhető mértéksablonok: 
- Tranzakció átlagos értéke (ATV)
- Tranzakció összértéke
- Átlagos napi bevétel
- Átlagos éves bevétel
- Tranzakció száma
- Szerzett hűségpontok
- Beváltott hűségpontok
- Hűségpontok egyenlege
- Ügyfél aktív életciklusa
- Hűség tagságának időtartama
- Az utolsó vásárlás óta eltelt idő

A következő eljárás egy új mérték használatával való felépítés lépéseit ismerteti.

1. A célközönség információin belül nyissa meg a következőt: **Mérőszámok**.

1. Válassza az **Új**, és a **Sablon kiválasztása** lehetőséget.

   :::image type="content" source="media/measure-use-template.png" alt-text="Képernyőkép a legördülő menüről, amikor új mértéket hoz létre a sablon kiemelése segítségével.":::

1. Keresse meg az igényeinek megfelelő sablont, és válassza a **Sablon kiválasztása** lehetőséget.

1. Tekintse át a kötelező adatokat, és válassza az **Első lépések** lehetőséget, ha minden adat a megfelelő helyen van.

1. A **Név szerkesztése** ablaktáblában állítsa be a mérték és a kimeneti entitás nevét. 

1. Válassza a **Kész** lehetőséget.

1. Adja meg az adat használandó időkeretét az **Időszak beállítása** szakaszban. Válassza ki, hogy az új mérték lefedje-e a teljes adatkészletet a **Minden idő** kiválasztásával. Vagy ha azt szeretné, hogy a mérték egy **Adott időszakra** összpontosítson.

   :::image type="content" source="media/measure-set-time-period.png" alt-text="Képernyőkép, amely egy sablonból származó mérték konfiguálásakor mutatja az időszak szakaszt.":::

1. A következő szakaszban válassza az **Adatok hozzáadása** lehetőséget a tevékenységek kiválasztásához, és az *Egyesített tevékenység* entitásból képezze le a megfelelő adatokat.

    1. A 1/2. lépés: A **Tevékenység típusa** alatt válassza ki a használni kívánt entitás típusát. A **Tevékenységekhez** válassza ki a leképezni kívánt entitásokat.
    1. 2/2. lépés: Válassza ki az attribútumot az *Egyesített tevékenység* entitásból a képlet által megkövetelt összetevőhöz. Például az Átlagos tranzakció értéke a Tranzakció értéket képviselő attribútum. A **Tevékenység időbélyegző** esetén válassza ki az Egyesített tevékenység entitás attribútumát, amely a tevékenység dátumát és időpontját jelképezi.
   
1. Miután az adatleképezés sikeres volt, az állapot **Befejezett** értékre vált, valamint láthatja a leképezett tevékenységek és attribútumok nevét.

   :::image type="content" source="media/measure-template-configured.png" alt-text="Képernyőkép a mérősablon teljes konfigurálásról.":::

1. Most már a **Futtatás** lehetőséget is választhatja a mérték eredményének kiszámításához. Későbbi finomításhoz válassza a **Tervezet mentése** lehetőséget.

## <a name="manage-your-measures"></a>Intézkedések kezelése

A **Mértékek** lapon láthatja a mértékek listáját.

Információkat talál a mérték típusáról, az létrehozóról, a létrehozás dátumáról, a státuszáról és az állapotáról. Ha kiválaszt egy mértéket a listából, akkor megtekintheti a kimenetet, és letölthet egy .CSV-fájl.

Ha egyszerre szeretné frissíteni az összes intézkedést, akkor jelölje be az **összes frissítése** lehetőséget egy adott intézkedés kiválasztása nélkül.

> [!div class="mx-imgBorder"]
> ![Az egyes intézkedések kezelésére szolgáló műveletek](media/measure-actions.png "Az egyes intézkedések kezelésére szolgáló műveletek")

Válasszon ki egy mértéket a listából a következő lehetőségekhez:

- Adja meg a mérőszám nevét a részletek megtekintéséhez.
- **Szerkessze** a mérőszám konfigurációját.
- **Frissítse** a mértéket a legújabb adatok alapján.
- **Nevezze át** az intézkedést.
- **Törölje** az intézkedést.
- **Aktiválás** vagy **Inaktiválás**. Az inaktív mértékek nem frissülnek az [ütemezett frissítés](system.md#schedule-tab) során.

> [!TIP]
> A feladatokhoz/folyamatokhoz [hatféle állapot](system.md#status-types) tartozhat. Emellett a legtöbb folyamat [más alsóbb szintű folyamatoktól is függ](system.md#refresh-policies). Kiválaszthatja egy folyamat állapotát, és megtekintheti a hozzá tartozó teljes feladat folyamatának részleteit. Miután kiválasztotta a **Részletek megtekintése** lehetőséget a feladat egyik feladatához, további információk jelennek meg: feldolgozási idő, legutóbbi feldolgozás dátuma, és a feladathoz társított összes hiba és figyelmeztetés.

## <a name="next-step"></a>Következő lépés

Az [ügyfélszegmens](segments.md) létrehozásához meglévő mértéket használhat.


[!INCLUDE[footer-include](../includes/footer-banner.md)]