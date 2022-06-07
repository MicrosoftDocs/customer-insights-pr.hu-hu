---
title: Új intézkedések létrehozása az intézkedéskészítővel
description: A semmiből hozhat létre intézkedéseket a vállalkozásával kapcsolatos kulcsfontosságú mutatók elemzéséhez.
ms.date: 03/25/2022
ms.subservice: audience-insights
ms.topic: conceptual
author: v-wendysmith
ms.author: wameng
ms.reviewer: v-wendysmith
manager: shellyha
searchScope:
- ci-measure-builder
- customerInsights
ms.openlocfilehash: d003d054145343cc2feeefeeee413810df43185a
ms.sourcegitcommit: b515120bebd2638f2639004422cee3cff42fbdf7
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/24/2022
ms.locfileid: "8800329"
---
# <a name="use-measure-builder-to-create-measures-from-scratch"></a>Mértékszerkesztő használata mértékszerkesztővel a semmiből történő létrehozáshoz

Ez a cikk bemutatja, hogyan hozhat létre új [mértéket](measures.md) a semmiből. A mértékszerkesztő lehetővé teszi a számítások matematikai operátorok, összesítési függvények és szűrők használatával történő meghatározását. Az egyesített *Vevő* entitáshoz kapcsolódó entitások attribútumaival létrehozhat mértékegységet.

Az intézkedések létrehozása B-to-C és B-to-B környezetben ugyanúgy működik. Ha azonban B-to-B környezet [hierarchiájú](relationships.md#set-up-account-hierarchies) fiókokat használ, dönthet úgy, hogy összesíti az intézkedést a kapcsolódó alszámlák között.

Gyorsan létrehozhat egy mértéket is, ha általánosan használt és előre definiált mértékkészletből választ. További információt a Mérték létrehozásához sablon használata című témakörben [talál](measure-templates.md).

# <a name="individual-consumers-b-to-c"></a>[Egyéni fogyasztók (B-to-C)](#tab/b2c)

Az egyes vevők (vevőattribútum, vevői mérték) vagy az üzleti/szervezeti szinten (üzleti mérték) hozhat létre mértékeket. A vevői attribútum és a vevői mérték két típus, amelyek lehetővé teszik a teljesítmény ügyfélenkénti nyomon követését. Például az egyes ügyfelek teljes költése. Az üzleti intézkedések lehetővé teszik a vállalkozásonkénti teljesítmény nyomon követését. Például a vállalat teljes bevétele.

- Ügyfélattribútum: Kimenetet hoz létre új attribútumként, amely a rendszer által létrehozott entitás új oszlopaként kerül mentésre Customer_Measure nevű, rendszer *által létrehozott entitásba*. Ügyfélattribútum frissítésekor a Customer_Measure *entitás összes többi vevőattribútuma* egyszerre frissül. Ezenkívül a vevői attribútumok megjelennek a vevőprofil kartonján. A futtatás vagy mentés után az ügyfélattribútum nem módosíthatja vevői mértékké.

- Vevői mérték: Saját entitásként hozza létre a kimenetet, és nem módosíthatja azt ügyfélattribútummá a futtatás vagy mentés után. Az ügyfél-intézkedések nem jelennek meg az ügyfélprofil-kartonon.

- Üzleti intézkedés: Saját entitásként generál kimenetet, és megjelenik a Customer Insights környezet kezdőlapján.

1. Ugrás az **intézkedésekre**.

1. Válassza az **Új** lehetőséget, és válassza a **Saját elkészítése** lehetőséget.

   :::image type="content" source="media/measure-b2c.png" alt-text="B-C mértékegység üres konfigurációs képernyője." lightbox="media/measure-b2c.png":::

1. Az üzleti szintű teljesítmény nyomon követéséhez váltson a **Mérték típus és** **az Üzleti szint között**. **A vevői szint** alapértelmezés szerint van kiválasztva. **A vevői szint** automatikusan hozzáadja a CustomerId *attribútumot a* Dimenziókhoz, míg **az Üzleti szint** automatikusan eltávolítja azt.

1. A konfigurációs területen válassza ki az összesítés funkciót a **Funkció kiválasztása** legördülő menüből. Az összesítési függvények többek között a következők:
   - **Sum**
   - **Átlag**
   - **Számlálás**
   - **Egyedszámlálás**
   - **Max**
   - **Min**
   - **Első:** az adatrekord első értékét veszi fel
   - **Utolsó**: az adatrekordhoz hozzáadott utolsó értéket veszi fel
   - **ArgMax**: megkeresi a célfüggvény maximális értékét adó adatrekordot
   - **ArgMin**: megkeresi a célfüggvény minimális értékét adó adatrekordot

1. Válassza az **Attribútum hozzáadása** lehetőséget a mérték létrehozásához szükséges adatok kiválasztásához.

   1. Válassza az **Attribútumok** lapot.
   1. Adatentitás: Válassza ki azt az entitást, amely a mérni kívánt attribútumot tartalmazza.
   1. Adatattribútum: Válassza ki az összesítési függvényben az mérték kiszámításához használni kívánt attribútumot. Egyszerre csak egy attribútumot választhat ki.
   1. Meglévő mértékből is kiválaszthat adatattribútumokat a **Mértékek** lapon, vagy másik lehetőségként megkereshet egy entitást vagy a mérték nevét is.
   1. Válassza a **Hozzáadás** lehetőséget, ha a kijelölt attribútumot hozzá szeretne adni a mértékhez.

1. Összetettebb mértékek építéshez további attribútumokat adhat hozzá, vagy használhat operátorokat a mértékfüggvényben.

1. Szűrők hozzáadásához válassza ki a **Szűrő** lehetőséget a konfigurációs területen. A szűrők alkalmazása csak a szűrőknek megfelelő rekordokat használja a mérték kiszámításához.
  
   1. Az **Attribútum hozzáadása** szakaszban a **Szűrők** ablaktáblán belül, jelölje ki a szűrők létrehozásához használni kívánt attribútumot.
   1. Állítsa be a szűrőoperátorokat, hogy minden kijelölt attribútumhoz definiálja a szűrőt.
   1. Válassza az **Alkalmaz** lehetőséget, ha a szűrőket hozzá szeretne adni a mértékhez.

1. Válassza a Dimenzió **lehetőséget**, ha további mezőket szeretne választani, amelyek oszlopként kerülnek a mértékkimeneti entitásba.

   1. Válassza a **Dimenziók szerkesztése** lehetőséget, ha olyan adatattribútumokat szeretne felvenni, amelyek szerint csoportosítja a mértékeket. Például város vagy nem.
   > [!TIP]
   > Ha a Mérték típusként **a** Vevőszint lehetőséget **választotta**, a *CustomerId* attribútum már hozzá lett adva. Ha eltávolítja az attribútumot, **a Mérték típus** üzleti szintre **vált**.
   1. Válassza a **Kész** lehetőséget, ha a dimenziókat hozzá szeretne adni a mértékhez.

1. Ha az adatokban olyan értékek vannak, amelyekre egész értéket kell lecserélni, válassza a **Szabályok** lehetőséget. Konfigurálja a szabályt, és csak egész számokat válasszon csereként. A *null* értéket cserélje ki például *0* értékkel.

1. Ha a leképezett adatentitás és az *Ügyfél* entitás között több elérési út is van, válasszon egyet az azonosított [entitáskapcsolat-útvonalak közül](relationships.md). A mértékek eredményei a kiválasztott elérési úttól függően változhatnak.

   1. Válassza ki a **Kapcsolat elérési útját**, és válassza ki az entitás elérési útját, amely a mérőszám azonosítására fog használni. Ha az *Ügyfél* entitásnak csak egyetlen elérési útja van, akkor a vezérlő nem fog mutatni.
   1. Válassza a **Kész** lehetőséget a kiválasztás alkalmazáshoz.

1. Ha további számításokat szeretne hozzáadni az mértékhez, válassza az **Új számítás** lehetőséget. Az új számításokhoz csak ugyanazon az entitás elérési úton használhatók entitások. A további számítások új oszlopként fognak megjelenni a mérték kimeneti entitásában.

1. Válassza ki a számítás függőleges ellipszisét (&vellip;) a számítás **másolata**, **átnevezése** vagy **eltávolítása** mértékegységből.

1. Az **Előnézet** területen a mérték kimeneti entitásának adatsémáját látja a szűrőkkel és a dimenziókkal. Az előnézet dinamikusan reagál a konfiguráció változásaira.

1. Válassza **a Részletek** szerkesztése lehetőséget a Cím nélküli mérték mellett. Adja meg a mérték nevét. A mértékhez is hozzáadhat [címkéket](work-with-tags-columns.md#manage-tags).

   :::image type="content" source="media/measures_edit_details.png" alt-text="Részletek szerkesztése párbeszédpanel.":::

1. Válassza a **Futtatás** lehetőséget a konfigurált mértékhez tartozó eredmények kiszámításához. Válassza a **Mentés és bezárás** lehetőséget, ha meg szeretné tartani az aktuális konfigurációt, és a mértéket később szeretné futtatni.

1. A listában az újonnan létrehozott mértékegységet a **Mértékek** listában jelenítheti meg.

# <a name="business-accounts-b-to-b"></a>[Üzleti számlák (B-to-B)](#tab/b2b)

Az egyes számlák (vevői intézkedés) vagy az összes számla szintjén (üzleti intézkedés) hozhat létre mértékeket.

- Vevői mérték: Saját entitásként hozza létre a kimenetet. Az ügyfél-intézkedések nem jelennek meg az ügyfélprofil-kartonon.

- Üzleti intézkedés: Saját entitásként generál kimenetet, és megjelenik a Customer Insights környezet kezdőlapján.

1. Ugrás az **intézkedésekre**.

1. Válassza az **Új** lehetőséget.

   :::image type="content" source="media/measure-b2b.png" alt-text="B-B mértékegység üres konfigurációs képernyője.":::

1. A konfigurációs területen válassza ki az összesítés funkciót a **Funkció kiválasztása** legördülő menüből. Az összesítési függvények többek között a következők:
   - **Sum**
   - **Átlag**
   - **Számlálás**
   - **Egyedszámlálás**
   - **Max**
   - **Min**
   - **Első:** az adatrekord első értékét veszi fel
   - **Utolsó**: az adatrekordhoz hozzáadott utolsó értéket veszi fel

1. Válassza az **Attribútum hozzáadása** lehetőséget a mérték létrehozásához szükséges adatok kiválasztásához.

   1. Válassza az **Attribútumok** lapot.
   1. Adatentitás: Válassza ki azt az entitást, amely a mérni kívánt attribútumot tartalmazza.
   1. Adatattribútum: Válassza ki az összesítési függvényben az mérték kiszámításához használni kívánt attribútumot. Egyszerre csak egy attribútumot választhat ki.
   1. Meglévő mértékből is kiválaszthat adatattribútumokat a **Mértékek** lapon, vagy másik lehetőségként megkereshet egy entitást vagy a mérték nevét is.
   1. Válassza a **Hozzáadás** lehetőséget, ha a kijelölt attribútumot hozzá szeretne adni a mértékhez.

1. Összetettebb mértékek építéshez további attribútumokat adhat hozzá, vagy használhat operátorokat a mértékfüggvényben.

1. Szűrők hozzáadásához válassza ki a **Szűrő** lehetőséget a konfigurációs területen. A szűrők alkalmazása csak a szűrőknek megfelelő rekordokat használja a mérték kiszámításához.
  
   1. Az **Attribútum hozzáadása** szakaszban a **Szűrők** ablaktáblán belül, jelölje ki a szűrők létrehozásához használni kívánt attribútumot.
   1. Állítsa be a szűrőoperátorokat, hogy minden kijelölt attribútumhoz definiálja a szűrőt.
   1. Válassza az **Alkalmaz** lehetőséget, ha a szűrőket hozzá szeretne adni a mértékhez.

1. Válassza a Dimenzió **lehetőséget**, ha további mezőket szeretne választani, amelyek oszlopként kerülnek a mértékkimeneti entitásba.

   1. Válassza a **Dimenziók szerkesztése** lehetőséget, ha olyan adatattribútumokat szeretne felvenni, amelyek szerint csoportosítja a mértékeket. Például város vagy nem.
      > [!TIP]
      > Ha a Mérték típusként **a** Vevőszint lehetőséget **választotta**, a *CustomerId* attribútum már hozzá lett adva. Ha eltávolítja az attribútumot, **a Mérték típusa** üzleti szintre **vált**.
   1. Válassza a **Kész** lehetőséget, ha a dimenziókat hozzá szeretne adni a mértékhez.

1. Ha az adatokban olyan értékek vannak, amelyekre egész értéket kell lecserélni, válassza a **Szabályok** lehetőséget. Konfigurálja a szabályt, és csak egész számokat válasszon csereként. A *null* értéket cserélje ki például *0* értékkel.

1. Az **Összesítő alfiókok** között válthat, ha [hierarchiával rendelkező partnerek vannak](relationships.md#set-up-account-hierarchies).
   - Ha a beállítása **Ki**, az intézkedés minden egyes számlára kiszámításra kerül. Minden egyes fióknak saját eredménye lesz.
   - Ha a beállítás **Be**, válassza a **Szerkesztés** lehetőséget, és válassza ki a fiókhierarchiát a betöltött hierarchia szerint. Az intézkedés eredménye csak egy lesz, mert alszámlákhoz van összesítve.

1. Ha a leképezett adatentitás és az *Ügyfél* entitás között több elérési út is van, válasszon egyet az azonosított [entitáskapcsolat-útvonalak közül](relationships.md). A mértékek eredményei a kiválasztott elérési úttól függően változhatnak.

   1. Válassza ki a **Kapcsolat elérési útját**, és válassza ki az entitás elérési útját, amely a mérőszám azonosítására fog használni. Ha az *Ügyfél* entitásnak csak egyetlen elérési útja van, akkor a vezérlő nem fog mutatni.
   1. Válassza a **Kész** lehetőséget a kiválasztás alkalmazáshoz.

1. Válassza ki a számítás függőleges ellipszisét (&vellip;) a számítás **másolata**, **átnevezése** vagy **eltávolítása** mértékegységből.

1. Az **Előnézet** területen a mérték kimeneti entitásának adatsémáját látja a szűrőkkel és a dimenziókkal. Az előnézet dinamikusan reagál a konfiguráció változásaira.

1. Válassza **a Részletek** szerkesztése lehetőséget a Cím nélküli mérték mellett. Adja meg a mérték nevét. A mértékhez is hozzáadhat [címkéket](work-with-tags-columns.md#manage-tags).

   :::image type="content" source="media/measures_edit_details.png" alt-text="Részletek szerkesztése párbeszédpanel.":::

1. Válassza a **Futtatás** lehetőséget a konfigurált mértékhez tartozó eredmények kiszámításához. Válassza a **Mentés és bezárás** lehetőséget, ha meg szeretné tartani az aktuális konfigurációt, és a mértéket később szeretné futtatni.

1. A listában az újonnan létrehozott mértékegységet a **Mértékek** listában jelenítheti meg.
