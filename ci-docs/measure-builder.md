---
title: Új mértékek létrehozása a mértékkészítővel
description: A semmiből hozhat létre mértékeket a vállalkozásával kapcsolatos legfontosabb mutatók elemzéséhez.
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
ms.openlocfilehash: f3ec86806074a12c1107648303ed2d65e97ebc69
ms.sourcegitcommit: dca46afb9e23ba87a0ff59a1776c1d139e209a32
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/29/2022
ms.locfileid: "9083016"
---
# <a name="create-new-measures-with-the-measure-builder"></a>Új mértékek létrehozása a mértékkészítővel

Ez a cikk azt ismerteti, hogyan hozhat létre új [mértéket](measures.md) a semmiből. A mértékkészítő lehetővé teszi a számítások definiálását matematikai operátorok, összesítő függvények és szűrők használatával. Létrehozhat egy mértéket az egyesített *Ügyfél* entitáshoz kapcsolódó entitások attribútumaival.

A mértékek létrehozása B-től C-ig és B-től B-ig környezetekben ugyanúgy működik. Ha azonban b-b környezete [hierarchiával](relationships.md#set-up-account-hierarchies) rendelkező fiókokat használ, dönthet úgy, hogy összesíti a mértéket a kapcsolódó alfiókok között.

Gyorsan létrehozhat mértékeket is, ha általánosan használt és előre definiált mértékek közül választ. További információ: [Sablon használata mérték létrehozásához](measure-templates.md).

# <a name="individual-consumers-b-to-c"></a>[Egyéni fogyasztók (B-to-C)](#tab/b2c)

Mértékeket hozhat létre az egyes ügyfelek szintjén (vevőattribútum, vevői mérték) vagy a vállalkozás/szervezet szintjén (üzleti mérték). Az ügyfélattribútum és az ügyfélmérés két típus, amelyek lehetővé teszik az ügyfélenkénti teljesítmény nyomon követését. Például az egyes ügyfelek teljes költése. Az üzleti mérések lehetővé teszik a vállalkozásonkénti teljesítmény nyomon követését. Például a vállalat teljes bevétele.

- Ügyfélattribútum: A kimenetet új attribútumként hozza létre, amely új oszlopként kerül mentésre a rendszer által létrehozott, Customer_Measure *nevű* entitásban. Egy ügyfélattribútum frissítésekor a Customer_Measure *entitás összes többi vevőattribútuma* egyszerre frissül. Ezenkívül az ügyfél-attribútumok is megjelennek az ügyfélprofil-kártyán. A futtatás vagy mentés után az ügyfélattribútum nem módosíthatja azt ügyfélmérésre.

- Vevői mérték: A kimenetet saját entitásként hozza létre, és a futtatás vagy mentés után nem módosíthatja azt ügyfélattribútumra. Az ügyfélmérések nem jelennek meg az ügyfélprofil-kártyán.

- Üzleti mérték: A kimenetet saját entitásként hozza létre, és megjeleníti a Customer Insights-környezet kezdőlapján.

1. Lépjen a Measures (Intézkedések) elemre **·**.

1. Válassza az **Új** lehetőséget, és válassza a **Saját elkészítése** lehetőséget.

   :::image type="content" source="media/measure-b2c.png" alt-text="Üres konfigurációs képernyő egy B-től C-ig terjedő mértékhez." lightbox="media/measure-b2c.png":::

1. Az üzleti szintű teljesítmény nyomon követéséhez állítsa **a Mérték típusa** **beállítást Üzleti szintre**. **Az ügyfélszint** alapértelmezés szerint ki van választva. **Az ügyfélszintű** automatikusan hozzáadja a CustomerId *attribútumot a* Dimenziókhoz, míg **az Üzleti szint** automatikusan eltávolítja azt.

1. A konfigurációs területen válassza ki az összesítési függvényt a **Select function** legördülő menüből. Az összesítési függvények többek között a következők:
   - **Sum**
   - **Átlag**
   - **Számlálás**
   - **Egyedszámlálás**
   - **Max**
   - **Min**
   - **Első:** az adatrekord első értékét veszi fel
   - **Utolsó**: az adatrekordhoz hozzáadott utolsó értéket veszi fel
   - **ArgMax**: megkeresi a célfüggvény maximális értékét adó adatrekordot
   - **ArgMin**: megkeresi a célfüggvény minimális értékét megadó adatrekordot

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

1. Válassza a Dimenzió **lehetőséget**, ha további mezőket szeretne kiválasztani, amelyek oszlopként vannak hozzáadva a mérték kimeneti entitásához.

   1. Válassza a **Dimenziók szerkesztése** lehetőséget, ha olyan adatattribútumokat szeretne felvenni, amelyek szerint csoportosítja a mértékeket. Például város vagy nem.
   > [!TIP]
   > Ha a **Customer level (Ügyfélszint**) lehetőséget választotta **Measure típusként**, a *CustomerId* attribútum már hozzá lesz adva. Ha eltávolítja az attribútumot, **a Mérték típusa** üzleti szintre **vált**.
   1. Válassza a **Kész** lehetőséget, ha a dimenziókat hozzá szeretne adni a mértékhez.

1. Ha az adatokban olyan értékek vannak, amelyekre egész értéket kell lecserélni, válassza a **Szabályok** lehetőséget. Konfigurálja a szabályt, és csak egész számokat válasszon csereként. A *null* értéket cserélje ki például *0* értékkel.

1. Ha a leképezett adatentitás és az *Ügyfél* entitás között több elérési út is van, válasszon egyet az azonosított [entitáskapcsolat-útvonalak közül](relationships.md). A mértékek eredményei a kiválasztott elérési úttól függően változhatnak.

   1. Válassza ki a **Kapcsolat elérési útját**, és válassza ki az entitás elérési útját, amely a mérőszám azonosítására fog használni. Ha az *Ügyfél* entitásnak csak egyetlen elérési útja van, akkor a vezérlő nem fog mutatni.
   1. Válassza a **Kész** lehetőséget a kiválasztás alkalmazáshoz.

1. Ha további számításokat szeretne hozzáadni az mértékhez, válassza az **Új számítás** lehetőséget. Az új számításokhoz csak ugyanazon az entitás elérési úton használhatók entitások. A további számítások új oszlopként fognak megjelenni a mérték kimeneti entitásában.

1. Válassza ki a számítás függőleges három pontját (&vellip;) a következőre: **Duplikált**, **Átnevezés** vagy **Számítás eltávolítása** egy mértékből.

1. Az **Előnézet** területen a mérték kimeneti entitásának adatsémáját látja a szűrőkkel és a dimenziókkal. Az előnézet dinamikusan reagál a konfiguráció változásaira.

1. Válassza a Részletek **szerkesztése lehetőséget** a Névtelen mérték mellett. Adja meg a mérték nevét. Ha szükséges, adjon hozzá [címkéket](work-with-tags-columns.md#manage-tags) a mértékhez.

   :::image type="content" source="media/measures_edit_details.png" alt-text="Részletek szerkesztése párbeszédpanel.":::

1. Válassza a **Futtatás** lehetőséget a konfigurált mértékhez tartozó eredmények kiszámításához. Válassza a **Mentés és bezárás** lehetőséget, ha meg szeretné tartani az aktuális konfigurációt, és a mértéket később szeretné futtatni.

1. A listában az újonnan létrehozott mértékegységet a **Mértékek** listában jelenítheti meg.

# <a name="business-accounts-b-to-b"></a>[Üzleti számlák (B-to-B)](#tab/b2b)

Mértékeket hozhat létre az egyes számlák szintjén (vevői mérték) vagy az összes számla szintjén (üzleti mérték).

- Vevői mérték: A kimenetet saját entitásként hozza létre. Az ügyfélmérések nem jelennek meg az ügyfélprofil-kártyán.

- Üzleti mérték: A kimenetet saját entitásként hozza létre, és megjeleníti a Customer Insights-környezet kezdőlapján.

1. Lépjen a Measures (Intézkedések) elemre **·**.

1. Válassza az **Új** lehetőséget.

   :::image type="content" source="media/measure-b2b.png" alt-text="Üres konfigurációs képernyő egy B-től B-ig terjedő mértékhez.":::

1. A konfigurációs területen válassza ki az összesítési függvényt a **Select function** legördülő menüből. Az összesítési függvények többek között a következők:
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

1. Válassza a Dimenzió **lehetőséget**, ha további mezőket szeretne kiválasztani, amelyek oszlopként vannak hozzáadva a mérték kimeneti entitásához.

   1. Válassza a **Dimenziók szerkesztése** lehetőséget, ha olyan adatattribútumokat szeretne felvenni, amelyek szerint csoportosítja a mértékeket. Például város vagy nem.
      > [!TIP]
      > Ha a **Customer level (Ügyfélszint**) lehetőséget választotta **Measure típusként**, a *CustomerId* attribútum már hozzá lesz adva. Ha eltávolítja az attribútumot, **a Mérték típusa** Üzleti szintre **vált**.
   1. Válassza a **Kész** lehetőséget, ha a dimenziókat hozzá szeretne adni a mértékhez.

1. Ha az adatokban olyan értékek vannak, amelyekre egész értéket kell lecserélni, válassza a **Szabályok** lehetőséget. Konfigurálja a szabályt, és csak egész számokat válasszon csereként. A *null* értéket cserélje ki például *0* értékkel.

1. Az **Összesítő alfiókok** között válthat, ha [hierarchiával rendelkező partnerek vannak](relationships.md#set-up-account-hierarchies).
   - Ha a beállítása **Ki**, az intézkedés minden egyes számlára kiszámításra kerül. Minden egyes fióknak saját eredménye lesz.
   - Ha a beállítás **Be**, válassza a **Szerkesztés** lehetőséget, és válassza ki a fiókhierarchiát a betöltött hierarchia szerint. Az intézkedés eredménye csak egy lesz, mert alszámlákhoz van összesítve.

1. Ha a leképezett adatentitás és az *Ügyfél* entitás között több elérési út is van, válasszon egyet az azonosított [entitáskapcsolat-útvonalak közül](relationships.md). A mértékek eredményei a kiválasztott elérési úttól függően változhatnak.

   1. Válassza ki a **Kapcsolat elérési útját**, és válassza ki az entitás elérési útját, amely a mérőszám azonosítására fog használni. Ha az *Ügyfél* entitásnak csak egyetlen elérési útja van, akkor a vezérlő nem fog mutatni.
   1. Válassza a **Kész** lehetőséget a kiválasztás alkalmazáshoz.

1. Válassza ki a számítás függőleges három pontját (&vellip;) a következőre: **Duplikált**, **Átnevezés** vagy **Számítás eltávolítása** egy mértékből.

1. Az **Előnézet** területen a mérték kimeneti entitásának adatsémáját látja a szűrőkkel és a dimenziókkal. Az előnézet dinamikusan reagál a konfiguráció változásaira.

1. Válassza a Részletek **szerkesztése lehetőséget** a Névtelen mérték mellett. Adja meg a mérték nevét. Ha szükséges, adjon hozzá [címkéket](work-with-tags-columns.md#manage-tags) a mértékhez.

   :::image type="content" source="media/measures_edit_details.png" alt-text="Részletek szerkesztése párbeszédpanel.":::

1. Válassza a **Futtatás** lehetőséget a konfigurált mértékhez tartozó eredmények kiszámításához. Válassza a **Mentés és bezárás** lehetőséget, ha meg szeretné tartani az aktuális konfigurációt, és a mértéket később szeretné futtatni.

1. A listában az újonnan létrehozott mértékegységet a **Mértékek** listában jelenítheti meg.
