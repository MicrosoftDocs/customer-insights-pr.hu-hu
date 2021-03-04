---
title: Mértékek létrehozása és felügyelete
description: Definiálja a vállalkozás teljesítményét elemző és tükröző mértékeket.
ms.date: 02/02/2021
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
ms.reviewer: wameng
manager: shellyha
ms.openlocfilehash: 5bcee3b4c51880740715575b18fd7a4dbf87e6d0
ms.sourcegitcommit: 139548f8a2d0f24d54c4a6c404a743eeeb8ef8e0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/15/2021
ms.locfileid: "5269931"
---
# <a name="define-and-manage-measures"></a>Az intézkedések definiálása és kezelése

A mértékek segítenek abban, hogy jobban megértse az ügyfelek viselkedését és az üzleti teljesítményt a kapcsolódó értékek lekérésével az [egyesített profilokból](data-unification.md). Egy vállalat például az *egy ügyfélhez kapcsolódó teljes költést* szeretné látni az egyes ügyfelek vásárlási előzményeinek megismeréséhez. Vagy mérni szeretné a *vállalat teljes értékesítéseit*, hogy megértse a teljes vállalat összesített szintű bevételeit.  

Az mértékek létrehozása a mértékkészítővel történik, ami egy adatlekérdezési platform számos operátorral és egyszerű leképezési lehetőségekkel. Lehetőséget ad az adatok szűrésére, az eredmények csoportosítására, az [entitáskapcsolatok elérési útjainak](relationships.md) észlelésére és a kimenet előnézetére.

A mértékszerkesztő segítségével üzleti tevékenységeket tervezhet az ügyféladatok lekérdezésével és a betekintések kinyerésével. Ha például egy *ügyfélre jutó teljes költség* és az *egy ügyfélre jutó teljes megtérülés* mértékeket hozza létre, akkor könnyebben azonosítható a nagy költéssel, mégis nagy megtérüléssel jellemezhető ügyfelek csoportja. A következő legjobb műveletek előremozdításához [létrehozhat egy szegmenst](segments.md). 

## <a name="create-a-measure"></a>Mérőszám létrehozása

Ez a rész végigvezeti egy új mértéknek a nulláról való létrehozásán. Az Ügyfél entitáshoz kapcsolattal beállított adatentitások adatattribútumainak segítségével mértéket állíthat össze. 

1. A célközönség információin belül nyissa meg a következőt: **Mérőszámok**.

1. Válassza az **Új** lehetőséget.

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

1. Ha a leképezett adatentitás és az Ügyfél entitás között több elérési út is van, válasszon egyet az azonosított [entitáskapcsolat -útvonalak](relationships.md) közül. A mértékek eredményei a kiválasztott elérési úttól függően változhatnak.
   1. Válassza ki az **Adatbeállítások** lehetőséget, és válassza ki az entitás elérési útját, amely a mérték azonosítására fog használni.
   1. Válassza a **Kész** lehetőséget a kiválasztás alkalmazáshoz. 

   :::image type="content" source="media/measures-data-preferences.png" alt-text="Válassza ki a mértékhez tartozó entitás elérési utat.":::

1. Ha további számításokat szeretne hozzáadni az mértékhez, válassza az **Új számítás** lehetőséget. Az új számításokhoz csak ugyanazon az entitás elérési úton használhatók entitások. A további számítások új oszlopként fognak megjelenni a mérték kimeneti entitásában.

1. Válassza a **...** lehetőséget a mértékből szármató számítás **Duplikálásához**, **Átnevezéséhez** vagy **Eltávolításához**.

1. Az **Előnézet** területen a mérték kimeneti entitásának adatsémáját látja a szűrőkkel és a dimenziókkal. Az előnézet dinamikusan reagál a konfiguráció változásaira.

1. Válassza a **Futtatás** lehetőséget a konfigurált mértékhez tartozó eredmények kiszámításához. Válassza a **Mentés és bezárás** lehetőséget, ha meg szeretné tartani az aktuális konfigurációt, és a mértéket később szeretné futtatni.

1. A listában az újonnan létrehozott mértékegységet a **Mértékek** listában jelenítheti meg.

## <a name="manage-your-measures"></a>Intézkedések kezelése

[Egy mérték létrehozása](#create-a-measure) után megtekintheti a mértékek listáját a **Mértékek** oldalon.

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