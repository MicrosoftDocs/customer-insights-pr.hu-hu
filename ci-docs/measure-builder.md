---
title: Mértékek létrehozása a mértékkészítővel
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
ms.openlocfilehash: fac00b8a1b4ca6e09dd29abe46dfe240adcc029e
ms.sourcegitcommit: 8a28e9458b857adf8e90e25e43b9bc422ebbb2cd
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/18/2022
ms.locfileid: "9170852"
---
# <a name="create-measures-with-measure-builder"></a>Mértékek létrehozása a mértékkészítővel

A mértékkészítő lehetővé teszi számítások definiálását matematikai operátorok, összesítő függvények és szűrők használatával. Mértékeket definiálhat az egyesített *Vevő* entitáshoz kapcsolódó entitások attribútumai alapján.

A mértékek létrehozása B-től C-ig és B-től B-ig környezetekben ugyanúgy működik. Ha azonban a B-to-B környezet [hierarchiával](relationships.md#set-up-account-hierarchies) rendelkező fiókokat használ, válassza ki, hogy összesíti-e a mértéket a kapcsolódó alszámlák között.

# <a name="individual-consumers-b-to-c"></a>[Egyéni fogyasztók (B-to-C)](#tab/b2c)

Hozzon létre mértékeket az egyes ügyfelek szintjén (ügyfélattribútum, vevői mérték) vagy a vállalkozás/szervezet szintjén (üzleti mérték). Az ügyfélattribútum és az ügyfélmérés lehetővé teszi az ügyfélenkénti teljesítmény nyomon követését. Például az egyes ügyfelek teljes költése. Az üzleti mérések nyomon követik a vállalkozásonkénti teljesítményt. Például a vállalat teljes bevétele.

- Vevőattribútum: A kimenetet új attribútumként hozza létre, amely új oszlopként kerül mentésre a rendszer által létrehozott, Customer_Measure nevű *entitásban*. Egy ügyfélattribútum frissítésekor a Customer_Measure *entitás összes többi vevőattribútuma* egyszerre frissül. Ezenkívül az ügyfél-attribútumok is megjelennek az ügyfélprofil-kártyán. A futtatás vagy a mentés után nem módosíthatja az ügyfélattribútumokat vevői mértékre.

- Vevői mérték: A kimenetet saját entitásként hozza létre, és a futtatás vagy mentés után nem módosíthatja azt ügyfélattribútumra. Az ügyfélmérések nem jelennek meg az ügyfélprofil-kártyán.

- Üzleti mérték: A kimenetet saját entitásként hozza létre, és a Customer Insights-környezet kezdőlapján jelenik meg.

1. Lépjen a Measures (Intézkedések) elemre **·**.

1. Válassza az **Új** > **Készítse el sajátját** lehetőséget.

   :::image type="content" source="media/measure-b2c.png" alt-text="Üres konfigurációs képernyő egy B-től C-ig terjedő mértékhez." lightbox="media/measure-b2c.png":::

1. Válassza a Részletek **szerkesztése lehetőséget** a Névtelen mérték mellett. Adja meg a mérték nevét. Ha szükséges, adjon hozzá [címkéket](work-with-tags-columns.md#manage-tags) a mértékhez.

   :::image type="content" source="media/measures_edit_details.png" alt-text="Részletek szerkesztése párbeszédpanel.":::

1. Válassza a **Kész** lehetőséget.

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

1. Válassza az Attribútum **hozzáadása lehetőséget** a mérték létrehozásához szükséges adatok kiválasztásához.

   1. Válassza az **Attribútumok** lapot.
   1. Adatentitás: Válassza ki azt az entitást, amely a mérni kívánt attribútumot tartalmazza.
   1. Adatattribútum: Válassza ki az összesítési függvényben az mérték kiszámításához használni kívánt attribútumot. Egyszerre csak egy attribútumot választhat ki.
   1. Ha szükséges, válasszon ki egy adatattribútumot egy meglévő mértékből a **Mértékek** lap kiválasztásával, vagy keressen rá egy entitás vagy mérték nevére.
   1. Válassza a **Hozzáadás** lehetőséget.

1. Összetettebb mértékek létrehozásához adjon hozzá további attribútumokat, vagy használjon matematikai operátorokat a mértékfüggvényen.

1. Szűrők hozzáadásához válassza ki a **Szűrő** lehetőséget a konfigurációs területen. A szűrők alkalmazása csak a szűrőknek megfelelő rekordokat használja a mérték kiszámításához.
  
   1. Az **Attribútum hozzáadása** szakaszban a **Szűrők** ablaktáblán belül, jelölje ki a szűrők létrehozásához használni kívánt attribútumot.
   1. Állítsa be a szűrőoperátorokat, hogy minden kijelölt attribútumhoz definiálja a szűrőt.
   1. Válassza az **Alkalmaz** lehetőséget.

1. Válassza a Dimenzió **lehetőséget**, ha további mezőket szeretne oszlopként hozzáadni a mérték kimeneti entitásához.

   1. Válassza a **Dimenziók szerkesztése** lehetőséget, ha olyan adatattribútumokat szeretne felvenni, amelyek szerint csoportosítja a mértékeket. Például város vagy nem.
      > [!TIP]
      > Ha a **Customer level (Ügyfélszint**) lehetőséget választotta **Measure típusként**, a *CustomerId* attribútum már hozzá lesz adva. Ha eltávolítja az attribútumot, **a Mérték típusa** üzleti szintre **vált**.
   1. Válassza a **Kész** lehetőséget.

1. Ha az adatokban vannak olyan értékek, amelyeket egész számra kell cserélni, válassza a Szabályok **lehetőséget**. Konfigurálja a szabályt, és csak egész számokat válasszon csereként. A *null* értéket cserélje ki például *0* értékkel.

1. Ha több útvonal van a leképezett adatentitás és az *Ügyfél* entitás között, válasszon egyet az azonosított [entitáskapcsolati](relationships.md) útvonalak közül. A mértékek eredményei a kiválasztott elérési úttól függően változhatnak.

   1. Válassza ki a **Kapcsolat elérési útját**, és válassza ki az entitás elérési útját, amely a mérőszám azonosítására fog használni. Ha az *Ügyfél* entitásnak csak egyetlen elérési útja van, akkor a vezérlő nem fog mutatni.
   1. Válassza a **Kész** lehetőséget.

1. Ha további számításokat szeretne hozzáadni az mértékhez, válassza az **Új számítás** lehetőséget. Az új számításokhoz csak az azonos entitásútvonalon lévő entitásokat használja. A további számítások új oszlopként fognak megjelenni a mérték kimeneti entitásában. Ha szükséges, válassza a Név **szerkesztése lehetőséget** a számítás nevének létrehozásához.

1. Válassza ki a számítás függőleges három pontját (&vellip;) a Számítás megkettőzése **vagy** **A** mérték eltávolítása értékre.

1. Az **Előnézet** területen a mérték kimeneti entitásának adatsémáját látja a szűrőkkel és a dimenziókkal. Az előnézet dinamikusan reagál a konfiguráció változásaira.

1. Válassza a **Futtatás** lehetőséget a konfigurált mértékhez tartozó eredmények kiszámításához. Válassza a **Mentés és bezárás** lehetőséget, ha meg szeretné tartani az aktuális konfigurációt, és a mértéket később szeretné futtatni. Megjelenik a **Mértékek** oldal.

# <a name="business-accounts-b-to-b"></a>[Üzleti számlák (B-to-B)](#tab/b2b)

Hozzon létre mértékeket az egyes számlák szintjén (vevői mérték) vagy az összes számla szintjén (üzleti mérték).

- Vevői mérték: A kimenetet saját entitásként hozza létre. Az ügyfélmérések nem jelennek meg az ügyfélprofil-kártyán.

- Üzleti mérték: A kimenetet saját entitásként hozza létre, és a Customer Insights-környezet kezdőlapján jelenik meg.

1. Lépjen a Measures (Intézkedések) elemre **·**.

1. Válassza az **Új** lehetőséget.

   :::image type="content" source="media/measure-b2b.png" alt-text="Üres konfigurációs képernyő egy B-től B-ig terjedő mértékhez.":::

1. Válassza a Részletek **szerkesztése lehetőséget** a Névtelen mérték mellett. Adja meg a mérték nevét. Ha szükséges, adjon hozzá [címkéket](work-with-tags-columns.md#manage-tags) a mértékhez. 
   :::image type="content" source="media/measures_edit_details.png" alt-text="Részletek szerkesztése párbeszédpanel.":::

1. Válassza a **Kész** lehetőséget.

1. A konfigurációs területen válassza ki az összesítési függvényt a **Select function** legördülő menüből. Az összesítési függvények többek között a következők:
   - **Sum**
   - **Átlag**
   - **Számlálás**
   - **Egyedszámlálás**
   - **Max**
   - **Min**
   - **Első:** az adatrekord első értékét veszi fel
   - **Utolsó**: az adatrekordhoz hozzáadott utolsó értéket veszi fel

1. Válassza az Attribútum **hozzáadása lehetőséget** a mérték létrehozásához szükséges adatok kiválasztásához.

   1. Válassza az **Attribútumok** lapot.
   1. Adatentitás: Válassza ki azt az entitást, amely a mérni kívánt attribútumot tartalmazza.
   1. Adatattribútum: Válassza ki az összesítési függvényben az mérték kiszámításához használni kívánt attribútumot. Egyszerre csak egy attribútumot választhat ki.
   1. Ha szükséges, válasszon ki egy adatattribútumot egy meglévő mértékből a **Mértékek** lap kiválasztásával, vagy keressen rá egy entitás vagy mérték nevére.
   1. Válassza a **Hozzáadás** lehetőséget, ha a kijelölt attribútumot hozzá szeretne adni a mértékhez.

1. Összetettebb mértékek létrehozásához adjon hozzá további attribútumokat, vagy használjon matematikai operátorokat a mértékfüggvényen.

1. Szűrők hozzáadásához válassza ki a **Szűrő** lehetőséget a konfigurációs területen. A szűrők alkalmazása csak a szűrőknek megfelelő rekordokat használja a mérték kiszámításához.
  
   1. Az **Attribútum hozzáadása** szakaszban a **Szűrők** ablaktáblán belül, jelölje ki a szűrők létrehozásához használni kívánt attribútumot.
   1. Állítsa be a szűrőoperátorokat, hogy minden kijelölt attribútumhoz definiálja a szűrőt.
   1. Válassza az **Alkalmaz** lehetőséget, ha a szűrőket hozzá szeretne adni a mértékhez.

1. Válassza a Dimenzió **lehetőséget**, ha további mezőket szeretne oszlopként hozzáadni a mérték kimeneti entitásához.

   1. Válassza a **Dimenziók szerkesztése** lehetőséget, ha olyan adatattribútumokat szeretne felvenni, amelyek szerint csoportosítja a mértékeket. Például város vagy nem.
      > [!TIP]
      > A *CustomerId* attribútum már hozzá van adva, jelezve, hogy ez egy ügyfélszintű mértéktípus. Ha eltávolítja az attribútumot, a mérték típusa üzleti szintre változik.
   1. Válassza a **Kész** lehetőséget, ha a dimenziókat hozzá szeretne adni a mértékhez.

1. Ha az adatokban vannak olyan értékek, amelyeket egész számra kell cserélni, válassza a Szabályok **lehetőséget**. Konfigurálja a szabályt, és csak egész számokat válasszon csereként. A *null* értéket cserélje ki például *0* értékkel.

1. Ha [hierarchiával](relationships.md#set-up-account-hierarchies) rendelkező fiókokat használ, tekintse át az Alfiókok összesítésecímű **témakört**.
   - Ha a beállítása **Ki**, az intézkedés minden egyes számlára kiszámításra kerül. Minden fiók megkapja a saját eredményét.
   - Ha a beállítás **Be**, válassza a **Szerkesztés** lehetőséget, és válassza ki a fiókhierarchiát a betöltött hierarchia szerint. A mérték csak egy eredményt hoz, mert alszámlákkal van összesítve.

1. Ha több útvonal van a leképezett adatentitás és az *Ügyfél* entitás között, válasszon egyet az azonosított [entitáskapcsolati](relationships.md) útvonalak közül. A mértékek eredményei a kiválasztott elérési úttól függően változhatnak.

   1. Válassza ki a **Kapcsolat elérési útját**, és válassza ki az entitás elérési útját, amely a mérőszám azonosítására fog használni. Ha az *Ügyfél* entitásnak csak egyetlen elérési útja van, akkor a vezérlő nem fog mutatni.
   1. Válassza a **Kész** lehetőséget a kiválasztás alkalmazáshoz.

1. Válassza ki a számítás függőleges három pontját (&vellip;) a Számítás megkettőzése **vagy** **A** mérték eltávolítása értékre.

1. Az **Előnézet** területen a mérték kimeneti entitásának adatsémáját látja a szűrőkkel és a dimenziókkal. Az előnézet dinamikusan reagál a konfiguráció változásaira.

1. Válassza a **Futtatás** lehetőséget a konfigurált mértékhez tartozó eredmények kiszámításához. Válassza a **Mentés és bezárás** lehetőséget, ha meg szeretné tartani az aktuális konfigurációt, és a mértéket később szeretné futtatni. Megjelenik a **Mértékek** oldal.

---

## <a name="next-step"></a>Következő lépés

Vevői szegmens létrehozásához [használja a meglévő mértékeket](segments.md).

[!INCLUDE [footer-include](includes/footer-banner.md)]
