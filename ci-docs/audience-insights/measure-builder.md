---
title: Új intézkedések létrehozása a mértékszerkesztővel
description: A nulláról készíthet intézkedéseket a vállalkozásával kapcsolatos legfontosabb mutatók elemzéséhez.
ms.date: 02/28/2022
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: wameng
ms.reviewer: mhart
manager: shellyha
searchScope:
- ci-measure-builder
- customerInsights
ms.openlocfilehash: 5329aea240ba40ec8698b3ddeb67fb5f21c62bbd
ms.sourcegitcommit: cf6a0ed44915908a44c70889a2dd199a9d0d4798
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/28/2022
ms.locfileid: "8359953"
---
# <a name="use-measure-builder-to-create-measures-from-scratch"></a>A mértékszerkesztő használata a nulláról hozhat létre intézkedéseket

Ez a cikk bemutatja, hogyan hozhat létre új [intézkedést](measures.md) a semmiből. A mértékszerkesztő lehetővé teszi a számítások matematikai operátorok, összesítő függvények és szűrők használatával történő meghatározását. Az egyesített Ügyfél *entitáshoz kapcsolódó entitások attribútumaival mérhet mértéket*. 

A B-C és B-to-B környezetben történő intézkedések létrehozása ugyanúgy működik. Ha azonban B-B-B környezetben [hierarchiákkal](relationships.md#set-up-account-hierarchies) rendelkező fiókokat használ, akkor a mértéket a kapcsolódó alszámlák között összesítheti.

Gyorsan létrehozhat egy mértéket is, ha egy sor általánosan használt és előre definiált intézkedés közül választ. További információt a Mérték létrehozásához sablon használata című témakörben [talál](measure-templates.md).

# <a name="individual-consumers-b-to-c"></a>[Egyéni fogyasztók (B-to-C)](#tab/b2c)

Intézkedéseket hozhat létre az egyes vevők szintjén (vevőattribútum, vevő mértéke) vagy az üzleti/szervezet szintjén (üzleti intézkedés). Az ügyfélattribútum és az ügyfélmérszám két típus, amelyek lehetővé teszik az ügyfélenkénti teljesítmény nyomon követését. Például az egyes ügyfelek teljes kiadásai. Az üzleti intézkedések lehetővé teszik a vállalkozásonkénti teljesítmény nyomon követését. Például a vállalat teljes bevétele.

- Vevőattribútum: Új attribútumként generál kimenetet, amely új oszlopként kerül mentésre a rendszer által létrehozott entitásban, Customer_Measure *.* Vevőattribútum frissítésekor a *Customer_Measure* entitás összes többi ügyfélattribútuma egyszerre frissül. Ezenkívül a vevői attribútumok megjelennek a vevőprofil-kártyán. A futtatás vagy mentés után az ügyfélattribútum nem módosíthatja vevői mértékre.

- Vevői mérték: Saját entitásként generál kimenetet, és futtatás vagy mentés után nem módosíthatja vevőattribútumra. Az ügyfélintézkedések nem jelennek meg a vevőprofil-kártyán.

- Üzleti mérték: Saját entitásként generál kimenetet, és megjelenik a Customer Insights-környezet kezdőlapján.

1. Menjen az **Intézkedésekhez**.

1. Válassza az **Új** lehetőséget, és válassza a **Saját elkészítése** lehetőséget.

   :::image type="content" source="media/measure-b2c.png" alt-text="Üres konfigurációs képernyő A B-C mértékegységhez.":::

1. Válassza a **Név szerkesztése** lehetőséget, és adjon **Nevet** a mértéknek. 

1. A konfigurációs területen válassza ki az összesítő függvényt a **Függvény** kiválasztása legördülő menüből. Az összesítési függvények többek között a következők: 
   - **Sum**
   - **Átlag**
   - **Számlálás**
   - **Egyedszámlálás**
   - **Max**
   - **Min**
   - **Első:** az adatrekord első értékét veszi fel
   - **Utolsó**: az adatrekordhoz hozzáadott utolsó értéket veszi fel
   - **ArgMax**: megkeresi a célfüggvény maximális értékét adó adatrekordot
   - **ArgMin**: megkeresi azt az adatrekordot, amely megadja a célfüggvény minimális értékét

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

1. Válassza a Dimenzió **lehetőséget**, ha további mezőket szeretne kiválasztani, amelyek oszlopként kerülnek a mértékkimeneti entitáshoz.
 
   1. Válassza a **Dimenziók szerkesztése** lehetőséget, ha olyan adatattribútumokat szeretne felvenni, amelyek szerint csoportosítja a mértékeket. Például város vagy nem. Az *ügyfélszintű mértékek* létrehozásához alapértelmezés szerint a *CustomerID* dimenzió van kiválasztva. Ha *üzleti szintű mértékeket* szeretne létrehozni, eltávolíthatja az alapértelmezett dimenziót.
   1. Válassza a **Kész** lehetőséget, ha a dimenziókat hozzá szeretne adni a mértékhez.

1. Ha az adatokban olyan értékek vannak, amelyekre egész értéket kell lecserélni, válassza a **Szabályok** lehetőséget. Konfigurálja a szabályt, és csak egész számokat válasszon csereként. A *null* értéket cserélje ki például *0* értékkel.

1. Ha a leképezett adatentitás és az *Ügyfél* entitás között több elérési út is van, válasszon egyet az azonosított [entitáskapcsolat-útvonalak közül](relationships.md). A mértékek eredményei a kiválasztott elérési úttól függően változhatnak. 
   
   1. Válassza ki a **Kapcsolat elérési útját**, és válassza ki az entitás elérési útját, amely a mérőszám azonosítására fog használni. Ha az *Ügyfél* entitásnak csak egyetlen elérési útja van, akkor a vezérlő nem fog mutatni.
   1. Válassza a **Kész** lehetőséget a kiválasztás alkalmazáshoz. 

1. Ha további számításokat szeretne hozzáadni az mértékhez, válassza az **Új számítás** lehetőséget. Az új számításokhoz csak ugyanazon az entitás elérési úton használhatók entitások. A további számítások új oszlopként fognak megjelenni a mérték kimeneti entitásában.

1. Válassza a **...** lehetőséget a mértékből szármató számítás **Duplikálásához**, **Átnevezéséhez** vagy **Eltávolításához**.

1. Az **Előnézet** területen a mérték kimeneti entitásának adatsémáját látja a szűrőkkel és a dimenziókkal. Az előnézet dinamikusan reagál a konfiguráció változásaira.

1. Válassza a **Futtatás** lehetőséget a konfigurált mértékhez tartozó eredmények kiszámításához. Válassza a **Mentés és bezárás** lehetőséget, ha meg szeretné tartani az aktuális konfigurációt, és a mértéket később szeretné futtatni.

1. A listában az újonnan létrehozott mértékegységet a **Mértékek** listában jelenítheti meg.

# <a name="business-accounts-b-to-b"></a>[Üzleti számlák (B-to-B)](#tab/b2b)


Intézkedéseket hozhat létre az egyes számlák szintjén (vevői mérték) vagy az összes számla szintjén (üzleti intézkedés). 

- Vevői mérték: Saját entitásként generál kimenetet. Az ügyfélintézkedések nem jelennek meg a vevőprofil-kártyán.

- Üzleti mérték: Saját entitásként generál kimenetet, és megjelenik a Customer Insights-környezet kezdőlapján.

1. Menjen az **Intézkedésekhez**.

1. Válassza az **Új** lehetőséget.

   :::image type="content" source="media/measure-b2b.png" alt-text="Üres konfigurációs képernyő A B-B-hez mértékegységhez.":::

1. Válassza a **Név szerkesztése** lehetőséget, és adjon **Nevet** a mértéknek. 

1. A konfigurációs területen válassza ki az összesítő függvényt a **Függvény** kiválasztása legördülő menüből. Az összesítési függvények többek között a következők: 
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

1. Válassza a Dimenzió **lehetőséget**, ha további mezőket szeretne kiválasztani, amelyek oszlopként kerülnek a mértékkimeneti entitáshoz.
 
   1. Válassza a **Dimenziók szerkesztése** lehetőséget, ha olyan adatattribútumokat szeretne felvenni, amelyek szerint csoportosítja a mértékeket. Például város vagy nem. Az *ügyfélszintű mértékek* létrehozásához alapértelmezés szerint a *CustomerID* dimenzió van kiválasztva. Ha *üzleti szintű mértékeket* szeretne létrehozni, eltávolíthatja az alapértelmezett dimenziót.
   1. Válassza a **Kész** lehetőséget, ha a dimenziókat hozzá szeretne adni a mértékhez.

1. Ha az adatokban olyan értékek vannak, amelyekre egész értéket kell lecserélni, válassza a **Szabályok** lehetőséget. Konfigurálja a szabályt, és csak egész számokat válasszon csereként. A *null* értéket cserélje ki például *0* értékkel.

1. Az **Összesítő alfiókok** között válthat, ha [hierarchiával rendelkező partnerek vannak](relationships.md#set-up-account-hierarchies).
   - Ha a beállítása **Ki**, az intézkedés minden egyes számlára kiszámításra kerül. Minden egyes fióknak saját eredménye lesz.
   - Ha a beállítás **Be**, válassza a **Szerkesztés** lehetőséget, és válassza ki a fiókhierarchiát a betöltött hierarchia szerint. Az intézkedés eredménye csak egy lesz, mert alszámlákhoz van összesítve.

1. Ha a leképezett adatentitás és az *Ügyfél* entitás között több elérési út is van, válasszon egyet az azonosított [entitáskapcsolat-útvonalak közül](relationships.md). A mértékek eredményei a kiválasztott elérési úttól függően változhatnak. 
   
   1. Válassza ki a **Kapcsolat elérési útját**, és válassza ki az entitás elérési útját, amely a mérőszám azonosítására fog használni. Ha az *Ügyfél* entitásnak csak egyetlen elérési útja van, akkor a vezérlő nem fog mutatni.
   1. Válassza a **Kész** lehetőséget a kiválasztás alkalmazáshoz. 

1. Válassza a **...** lehetőséget a mértékből szármató számítás **Duplikálásához**, **Átnevezéséhez** vagy **Eltávolításához**.

1. Az **Előnézet** területen a mérték kimeneti entitásának adatsémáját látja a szűrőkkel és a dimenziókkal. Az előnézet dinamikusan reagál a konfiguráció változásaira.

1. Válassza a **Futtatás** lehetőséget a konfigurált mértékhez tartozó eredmények kiszámításához. Válassza a **Mentés és bezárás** lehetőséget, ha meg szeretné tartani az aktuális konfigurációt, és a mértéket később szeretné futtatni.

1. A listában az újonnan létrehozott mértékegységet a **Mértékek** listában jelenítheti meg.

---