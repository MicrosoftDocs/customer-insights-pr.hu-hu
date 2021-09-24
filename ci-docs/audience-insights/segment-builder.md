---
title: Szegmensek létrehozása a szegmensépítőben
description: Hozzon létre ügyfelekből álló szegmenseket, és csoportosítsa őket különböző attribútumok alapján.
ms.date: 09/07/2021
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: JimsonChalissery
ms.author: jimsonc
ms.reviewer: mhart
manager: shellyha
ms.openlocfilehash: 7f7bd0e7e581305836287bd503ef273a2d556bff
ms.sourcegitcommit: fecdee73e26816c42d39d160d4d5cfb6c8a91596
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/15/2021
ms.locfileid: "7494502"
---
# <a name="create-segments"></a>Szegmensek létrehozása

Összetett szűrőket definiálhat az egyesített ügyfélentitás és a kapcsolódó entitások körül. A feldolgozást követően minden szegmens létrehoz egy csoport olyan ügyfélrekordot, amellyel az exportálás után műveletek végezhetők. A szegmensek kezelése a **Szegmensek** oldalon történik. A [szegmensépítő](#segment-builder) segítségével [új szegmenseket hozhat létre](#create-a-new-segment), illetve [gyorsszegmenseket](#quick-segments) hozhat létre az alkalmazás egyéb területeiről.

## <a name="segment-builder"></a>Szegmensépítő

A következő kép a szegmensépítő különböző aspektusait szemlélteti. Egy olyan szegmenst mutat, amely az ügyfelek egy csoportját adja eredményül. Az ügyfelek által egy adott időkeret alatt termékeket rendeltek, és több jutalompontot gyűjtöttek, vagy egy bizonyos összeget elköltöttek. 

:::image type="content" source="media/segment-builder-overview.png" alt-text="A szegmensszerkesztő elemei." lightbox="media/segment-builder-overview.png":::

1 . A szegmens rendszerezése szabályok és alszabályok szerint. Minden szabály vagy alszabály feltételekből áll. A feltételeket logikai operátorokkal egyesítése

2 . Válassza ki a szabályra vonatkozó entitások közötti [kapcsolati elérési utat](relationships.md). A kapcsolati elérési út határozza meg, hogy mely attribútumok használhatók egy feltételben.

3 – Szabályok és alszabályok kezelése. Szabály pozíciójának módosítása vagy törlése.

4 . Feltételek hozzáadása és a megfelelő szintű egymásba ágyazás kiépítése az alszabályokkal.

5 – Halmaz-műveletek alkalmazása a csatlakoztatott szabályokra.

6 – Az attribútumpanel használható entitásattribútumok hozzáadására vagy attribútumok alapján feltételek létrehozására. Az ablaktáblán a kijelölt szabály számára elérhető entitások és attribútumok listája látható a kijelölt kapcsolati útvonal alapján.

7 – Attribútumon alapuló feltételek hozzáadása a meglévő szabályokhoz és alszabályokhoz, illetve új szabályhoz.

8 – A változtatások visszavonása és ismétlése a szegmens létrehozása közben.

A fenti példa a szegmentációs képességet szemlélteti. Meghatároztunk egy szegmenst az olyan ügyfelek számára, akik legalább 500 dollár értékben termékeket vásároltak online, *és* érdeklődnek a szoftverfejlesztés iránt.

## <a name="create-a-new-segment"></a>Új szegmens létrehozása

Új szegmens többféleképpen is létrehozható. Ez a rész ismerteti, hogyan lehet a saját szegmenst a nulláról felépíteni. *Üres szegmenst* a meglévő entitások alapján, illetve a gépi tanulási modell *javasolt szegmensei* alapján is létrehozhat. További információk: [Szegmensek áttekintése](segments.md).

A szegmensek létrehozásakor mentheti a tervezetet. A rendszer inaktív szegmensként menti a tervezetet, amely nem aktiválható, amíg be nem lett fejezve érvényes konfigurációval.

1. Lépjen a **Szegmensek** oldalra.

1. Válassza az **Új** > **Készítse el sajátját** lehetőséget.

1. A szegmensépítőlapon definiálja az első szabályt. A szabály egy vagy több feltételből áll, és egy ügyfélkört határoz meg.

1. Az **1. szabály** szakaszban válassza ki annak az entitásnak az attribútumát, amely szerint meg szeretné szűrni az ügyfeleket. Kétféleképpen választhat ki attribútumokat. 
   - Nézze át a **Hozzáadás szabályhoz** ablaktáblában a rendelkezésre álló entitások és attribútumok listáját, és válassza ki a hozzáadni kívánt attribútum melletti **+** ikont. Válassza ki, hogy az attribútumot hozzá szeretné-e adni egy meglévő szabályhoz, vagy új szabály létrehozására szeretné használni.
   - Az egyező javaslatokért írja be az attribútum nevét a szabály szakaszba.

1. Adja meg a feltétel egyező értékeit operátorok kiválasztásával. Az attribútum értéke a következő négy adattípus valamelyike lehet: numerikus, karakterlánc, dátum vagy logikai. Az attribútum adattípusától függően különböző operátorok határozzák meg a feltételt. 

1. Válassza a **Feltétel hozzáadása** lehetőséget, ha további feltételeket szeretne hozzáadni egy szabályhoz. Ha az aktuális szabály alatt szeretne szabályt létrehozni, válassza az **Alszabály hozzáadása** lehetőséget.

1. Ha egy szabály nem az *Ügyfél* entitást használja, be kell állítania a kapcsolat elérési útját. A kapcsolati elérési útja a rendszert, rendszer tájékoztatásához szükséges amely kapcsolatok érjék el az egyesített ügyfélnetitást. Válassza a **Kapcsolati útvonal beállítása** lehetőséget, ha a kijelölt entitást az ügyfélentitásra leképezi. Ha csak egy lehetséges kapcsolati útvonal van, akkor a rendszer automatikusan kiválasztja azt. A különböző kapcsolati elérési utak eltérő eredményeket adhatnak. Minden szabálynak megvan a saját kapcsolati elérési útja.

   :::image type="content" source="media/relationship-path.png" alt-text="Lehetséges kapcsolati elérési út az egyesített ügyfélentitásra leképezett entitáson alapuló szabály létrehozásakor.":::

   Például az *eCommerce_eCommercePurchases* entitás a képernyőképen négy lehetőséget kínál az *Ügyfél* entitás leképezéséhez: 
   - eCommerce_eCommercePurchases > eCommerce_eCommerceContacts > Ügyfél
   - eCommerce_eCommercePurchases > Ügyfél
   - eCommerce_eCommercePurchases > eCommerce_eCommerceContacts > POS_posPurchases > Ügyfél
   - eCommerce_eCommercePurchases > eCommerce_eCommerceContacts > POS_posPurchases > loyaltyScheme_loyCustomers > Ügyfél az utolsó lehetőség kiválasztásakor a szabályfeltételekben felsorolt entitások összes attribútumát belefoglalhatjuk. Valószínűleg kevesebb eredményt kapunk, mert az egyező ügyfélrekordnak az összes entitásnak részének kell lennie. Ebben a példában az e-commerce (*eCommerce_eCommercePurchases*) elemen keresztül kell az értékesítési ponton (*POS_posPurchases*) vásárolnia az termékeket, és részt vennie a hűségprogramban (*loyaltyScheme_loyCustomers*). A második lehetőség kiválasztásakor csak az *eCommerce_eCommercePurchases* és az *Ügyfél* entitásból választhatunk attribútumokat. Ennek eredménye valószínűleg több eredményül kapott ügyfélprofil lesz.

1. Ha egy szabályban több feltétel is van, kiválaszthatja, hogy melyik logikai operátor kapcsolja össze őket.

   - **ÉS** operátor: Minden feltételnek teljesülnie kell ahhoz, hogy a rekord szerepeljen a szegmensben. Ez a beállítás akkor a leghasznosabb, ha különböző entitások között határoz meg feltételeket.

   - **VAGY** operátor: Az egyik feltételnek teljesülnie kell ahhoz, hogy a rekord szerepeljen a szegmensben. Ez a beállítás akkor a leghasznosabb, ha különböző feltételeket ad meg ugyanahhoz az entitáshoz.

   :::image type="content" source="media/segmentation-either-condition.png" alt-text="Szabály két ÉS feltétellel.":::

   Az VAGY operátor használata esetén minden feltételnek a kapcsolati elérési útban szereplő entitáson kell alapulnia.

   1. Több szabályt is létrehozhat, hogy több ügyfélrekordot-halmazt hozzon létre. A csoportok kombinálhatók, hogy tartalmazzák az üzleti esethez szükséges ügyfeleket. Új szabály létrehozásához válassza az **Szabály hozzáadása** lehetőséget. Ha a megadott kapcsolati útvonal miatt nem lehet szabályt és entitást létrehozni, új szabályt kell létrehozni, hogy attribútumokat válasszon belőle.

      :::image type="content" source="media/segment-rule-grouping.png" alt-text="Vegyen fel egy új szabályt egy szegmensbe, és válassza ki a halmaz operátorát.":::

   1. Válasszon egyet a készletre vonatkozó operátorok közül: **Unió**, **Metszet** vagy **Kivétel**.

   - Az **Egyesülés** egyesíti a két csoportot.

   - A **Metszet** a két csoport átfedését veszi. Csak az az adat *amely közös* kerül megtartásra mindkét egységesített csoportban.

   - **Kivéve** kombinálja a két csoportot. Csak azon adat kerül megtartásra az A csoportban, amely *nem közös* a B csoport adatival.

1. A szegmensek alapértelmezés szerint a definiált szűrőknek megfelelő ügyfélprofilok összes attribútumát tartalmazó kimeneti entitást hozzák létre. Ha egy szegmens nem az *Ügyfél* entitáson alapul, akkor ezekből az entitásokból további attribútumokat adhat a kimeneti entitáshoz. A **Projektattribútumok** kiválasztásával kiválaszthatja a kimeneti entitáshoz hozzáfűzni kívánt attribútumokat.  

   :::image type="content" source="media/segments-project-attributes.png" alt-text="Példa a kimeneti entitáshoz hozzáadandó, az oldalpanelen kijelölt elővetített attribútumokra.":::
  
   Példa: A szegmens az *Ügyfél* entitáshoz kapcsolódó, vásárlási adatokat tartalmazó entitáson alapul. A szegmens az adott évben termékeket vásároló összes spanyolországi ügyfelet keresi. Kiválaszthatja, hogy attribútumokat fűz hozzá, például az áruk árát, vagy a vásárlási dátumot a kimeneti entitásban található összes egyező ügyfélrekordhoz. Ez az információ hasznos lehet a teljes költéssel kapcsolatos szezonális korrelációk elemzéséhez.

   > [!NOTE]
   > - A vetített attribútumok csak olyan entitások esetén működnek, amelyek egy-a-sokhoz kapcsolatban vannak az ügyfélentitással. Egy ügyfél például több előfizetéssel is rendelkezhet.
   > - Csak olyan entitás attribútumai vetíthetők előre, amelyek az ön által létrehozandó szegmenslekérdezés minden szabályában használatosak.
   > - A vetített attribútumokat figyelembe veszi a rendszer a beállított operátorok használatakor.

1. A szegmens mentése és futtatása előtt válassza a Szegmens neve melletti **Részletek szerkesztése** lehetőséget. Adja meg a szegmens nevét, és frissítse a szegmens javasolt **Kimeneti entitás neve** értéket. A szegmenshez leírást is hozzáadhat.

1. Válassza a **Futtatás** lehetőséget a szegmens mentéshez és feldolgozásához, ha minden követelmény ellenőrizve lett. Máskülönben inaktív szegmensvázlatként menti a rendszer.

1. A **Szegmensek** oldalra a **Vissza a szegmensekhez** elemre kattintva léphet vissza.

> [!TIP]
> - A szegmensépítő nem javasol érvényes értékeket az entitásokból a feltételek operátorainak beállításakor. Az **Adatok** > **Entitások** helyen letöltheti az entitásadatokat, és láthatja, hogy mely értékek érhetők el.
> - A dátumon alapuló feltételek válthatnak a fix dátumok és egy lebegőpontos tartomány között.
> - Ha a szegmenshez több szabály is tartozik a szerkesztett szabály körül egy kék sáv található.
> - A szabályokat és feltételeket a szegmensdefinícióban más helyre is áthelyezheti. Válassza ki a [...] elemet egy szabály vagy feltétel mellet, és adja meg, hogy hová és hogyan helyezi át.
> - A **Visszavonás** és a **Ismét** vezérlők a parancssávban lehetővé teszik Önnek a változások visszavonását.

## <a name="quick-segments"></a>Gyors szegmens

A gyorsszegmensek segítségével gyorsan készíthet egyszerű, egy operátorral rendelkező szegmenseket a gyors elemzéshez.

1. A **Szegmensek** oldalon válassza az **Új** > **Létrehozás a következőből** lehetőséget.

   - Válassza a **Profilok** lehetőséget, ha az *egyesített ügyfél* entitáson alapuló szegmenset szeretne létrehozni.
   - Ha korábban létrehozott mértékekhez szeretne szegmenst létrehozni, válassza a **Mértékek** lehetőséget.
   - Válassza az **Információ** lehetőséget, ha egy szegmenst szeretne létrehozni az egyik olyan kimeneti entitás köré, amelyet vagy az **Előrejelzések** vagy az **egyéni modellek** használatával hozott létre.

2. Az **új gyors szegmens** párbeszédpanelen jelöljön ki egy attribútumot a **Mező** legördülő listában.

3. A rendszer további információkat ad, ami segít az ügyfelek jobb szegmenseinek létrehozásában.
   - A kategorikus mezők esetén 10 első számú ügyfél számít. Válasszon egy **Értéket**, és válassza a **Felülvizsgálat** elemet.

   - Numerikus attribútumok esetében a rendszer azt mutatja, hogy az egyes ügyfelek percentilis értékei alá milyen attribútumértékek tartoznak. Válasszon egy **operátort** és egy **értéket**, majd válassza a **Felülvizsgálat** lehetőséget.

4. A rendszer megadja a **Becsült szegmensméret** értékét. Kiválaszthatja, hogy létrehozza-e a megadott szegmenst, vagy először újra meg szeretné vizsgálni, hogy egy másik szegmens méretet kap-e.

    > [!div class="mx-imgBorder"]
    > ![Gyorsszegmens neve és becslése.](media/quick-segment-name.png "Gyorsszegmens neve és becslése")

5. Adjon meg egy **Név** értéket a szegmens számára. Másik lehetőségként adjon meg **Megjelenítendő nevet**.

6. Válassza a **Mentés** lehetőséget a szegmens létrehozásához.

7. Miután a szegmens befejezte a feldolgozást, megtekintheti azt a létrehozott többi szegmenshez hasonlóan.

## <a name="next-steps"></a>További lépések

[Exportáljon egy szegmenst](export-destinations.md), és fedezze fel az [Ügyfélkártya integrációját](customer-card-add-in.md), hogy használhassa a szegmenseket más alkalmazásokban.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
