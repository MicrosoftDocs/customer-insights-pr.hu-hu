---
title: Összetett szegmensek létrehozása a szegmensépítővel
description: A szegmensépítővel összetett szegmenseket hozhat létre az ügyfelekről úgy, hogy különböző attribútumok alapján csoportosítja őket.
ms.date: 08/12/2022
ms.subservice: audience-insights
ms.topic: how-to
author: JimsonChalissery
ms.author: jimsonc
ms.reviewer: v-wendysmith
manager: shellyha
searchScope:
- ci-segments
- ci-segment-builder
- ci-segment-details
- customerInsights
ms.openlocfilehash: 7f691fd0b2ea76a2960d5adf766a4b166f02ebb4
ms.sourcegitcommit: 267c317e10166146c9ac2c30560c479c9a005845
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/16/2022
ms.locfileid: "9304752"
---
# <a name="create-complex-segments-with-segment-builder"></a>Összetett szegmensek létrehozása a szegmensépítővel

Határozzon meg összetett szűrőket az egyesített ügyfél vagy az egyesített kapcsolattartó és a kapcsolódó entitások körül. A feldolgozás után minden szegmens létrehoz egy vevői vagy kapcsolattartói rekordkészletet, amelyet exportálhat és műveleteket hajthat végre.

> [!TIP]
> Az **egyéni ügyfeleken** alapuló szegmensek automatikusan tartalmazzák a szegmenstagok rendelkezésre álló kapcsolattartási adatait. Ha az üzleti **fiókokban**[egyesítette](data-unification.md) a partnereket és a kapcsolattartókat is, válassza ki, hogy a szegmens partnereken vagy üzleti kapcsolattartókon alapul-e. Ha olyan célhelyre szeretne exportálni, amely kapcsolattartási adatokat vár, használja a kapcsolattartók egy szegmensét. Ha egy célhelyre szeretné exportálni a számlaadatokat, használja a fiókok egy szegmensét.

## <a name="segment-builder"></a>Szegmensépítő

A következő kép a szegmensépítő különböző aspektusait szemlélteti. Egy olyan szegmenst mutat, amely az ügyfelek egy csoportját adja eredményül. Az ügyfelek adott időkeretben rendeltek termékeket és jutalmazási pontokat gyűjtöttek, vagy egy bizonyos összeget költöttek el.

:::image type="content" source="media/segment-builder-overview.png" alt-text="A szegmensszerkesztő elemei." lightbox="media/segment-builder-overview.png":::

1. A szegmens rendszerezése szabályok és alszabályok szerint. Minden szabály vagy alszabály feltételekből áll. Kombinálja a feltételeket logikai operátorokkal.

1. Válassza ki a szabályra vonatkozó entitások közötti [kapcsolati elérési utat](relationships.md). A kapcsolati elérési út határozza meg, hogy mely attribútumok használhatók egy feltételben.

1. Szabályok és alszabályok kezelése. Szabály pozíciójának módosítása vagy törlése.

1. Feltételek hozzáadása és a megfelelő szintű egymásba ágyazás kiépítése az alszabályokkal.

1. Halmaz-műveletek alkalmazása a csatlakoztatott szabályokra.

1. Az attribútumpanel használható entitásattribútumok hozzáadására vagy attribútumok alapján feltételek létrehozására. Az ablaktáblán a kijelölt szabály számára elérhető entitások és attribútumok listája látható a kijelölt kapcsolati útvonal alapján.

1. Attribútumon alapuló feltételek hozzáadása a meglévő szabályokhoz és alszabályokhoz, illetve új szabályhoz.

1. A változtatások visszavonása és ismétlése a szegmens létrehozása közben.

A fenti példa a szegmentációs képességet szemlélteti. Meghatároztunk egy szegmenst az olyan ügyfelek számára, akik legalább 500 dollár értékben termékeket vásároltak online, *és* érdeklődnek a szoftverfejlesztés iránt.

## <a name="create-a-new-segment-with-segment-builder"></a>Új szegmens létrehozása a szegmensépítővel

1. Kattintson a **Szegmensek** lehetőségre.

1. Válassza az **Új** > **Készítse el sajátját** lehetőséget. A szegmensszerkesztő lapon szabályokat definiál, illetve alkot. A szabály egy vagy több ügyfélkört definiáló feltételből áll.

   > [!NOTE]
   > Üzleti fiókokon alapuló környezetek esetén válassza a Partnerek **új** > **szegmense vagy** a Kapcsolattartók szegmense (előzetes verzió) **lehetőséget** a létrehozni kívánt szegmens típusa alapján. [Ha fiókhierarchia](relationships.md#set-up-account-hierarchies) van definiálva, és szabályokat szeretne létrehozni az adatok gyermek- és szülőkapcsolat alapján történő kiszűréséhez, válassza a **Hierarchia használata? (előzetes verzió)**, válassza ki a hierarchiát, majd **alkalmazza**.
   >
   > :::image type="content" source="media/segment_acct_hierarchy.png" alt-text="Szegmens kiválasztása fiókhierarchia panel.":::

1. Válassza a Részletek **szerkesztése lehetőséget** a Névtelen szegmens mellett. Adja meg a szegmens nevét, és frissítse a szegmens javasolt **Kimeneti entitás neve** értéket. Ha szükséges, adjon hozzá egy leírást és [címkéket](work-with-tags-columns.md#manage-tags) a szegmenshez.

   :::image type="content" source="media/segments_edit_details.png" alt-text="Részletek szerkesztése párbeszédpanel.":::

1. Az 1 **. szabály szakaszban válassza ki annak az** entitásnak az attribútumát, amely alapján szűrni szeretné az ügyfeleket. Kétféleképpen választhat ki attribútumokat.
   - Nézze át a **Hozzáadás szabályhoz** ablaktáblában a rendelkezésre álló entitások és attribútumok listáját, és válassza ki a hozzáadni kívánt attribútum melletti **+** ikont. Válassza ki, hogy az attribútumot hozzá szeretné-e adni egy meglévő szabályhoz, vagy új szabály létrehozására szeretné használni.
   - Az egyező javaslatokért írja be az attribútum nevét a szabály szakaszba.

1. Adja meg a feltétel egyező értékeit operátorok kiválasztásával. Az attribútum értéke a következő négy adattípus valamelyike lehet: numerikus, karakterlánc, dátum vagy logikai. Az attribútum adattípusától függően különböző operátorok határozzák meg a feltételt.

1. Válassza a **Feltétel hozzáadása** lehetőséget, ha további feltételeket szeretne hozzáadni egy szabályhoz. Ha az aktuális szabály alatt szeretne szabályt létrehozni, válassza az **Alszabály hozzáadása** lehetőséget.

1. Ha egy szabály más entitásokat használ, mint a *Vevő* entitás (vagy *a ContactProfile* entitás a B-to-B-hez), válassza a Kapcsolat elérési útjának **beállítása lehetőséget** a kiválasztott entitásnak az egységes vevői entitáshoz való hozzárendeléséhez. Ha csak egy lehetséges kapcsolati útvonal van, a rendszer automatikusan kiválasztja azt. A különböző [kapcsolati útvonalak különböző eredményeket hozhatnak](relationships.md#relationship-paths). Minden szabálynak megvan a saját kapcsolati elérési útja.

   :::image type="content" source="media/relationship-path.png" alt-text="Lehetséges kapcsolati elérési út az egyesített ügyfélentitásra leképezett entitáson alapuló szabály létrehozásakor.":::

1. Ha egy szabályban több feltétel is van, válassza ki, hogy melyik logikai operátor kapcsolja össze őket.  
   - **ÉS** operátor: Minden feltételnek teljesülnie kell ahhoz, hogy a rekord szerepeljen a szegmensben. Akkor használja ezt a beállítást, ha különböző entitások közötti feltételeket határoz meg.
   - **VAGY** operátor: Az egyik feltételnek teljesülnie kell ahhoz, hogy a rekord szerepeljen a szegmensben. Akkor használja ezt a beállítást, ha több feltételt határoz meg ugyanahhoz az entitáshoz.

   :::image type="content" source="media/segmentation-either-condition.png" alt-text="Szabály két ÉS feltétellel.":::

   Az VAGY operátor használata esetén minden feltételnek a kapcsolati elérési útban szereplő entitáson kell alapulnia.

1. Különböző vevőrekord-készletek létrehozásához hozzon létre több szabályt. Az üzleti esethez szükséges ügyfelek felvételéhez kombinálja a csoportokat. Pontosabban, ha a megadott kapcsolati útvonal miatt nem tud entitást belefoglalni egy szabályba, hozzon létre egy új szabályt, amely attribútumokat választ belőle.

      :::image type="content" source="media/segment-rule-grouping.png" alt-text="Vegyen fel egy új szabályt egy szegmensbe, és válassza ki a halmaz operátorát.":::

   1. Válassza a Szabály **hozzáadása lehetőséget**.
   1. Válasszon egyet a készletre vonatkozó operátorok közül: **Unió**, **Metszet** vagy **Kivétel**.

      - Az **Egyesülés** egyesíti a két csoportot.
      - A **Metszet** a két csoport átfedését veszi. Csak azok az adatok maradnak az egyesített csoportban, amelyek mindkét csoportban *közösek*.
      - **Kivéve** kombinálja a két csoportot. Csak az A csoportban lévő olyan adatokat tartja meg a rendszer, amelyek *nem közösek* a B csoport adataival.

1. Alapértelmezés szerint a kimeneti entitás automatikusan tartalmazza az ügyfélprofilok összes olyan attribútumát, amely megfelel a megadott szűrőknek. A ContactProfile *entitás használatakor a* B-től B-ig terjedő sávban a rendszer automatikusan tartalmazza a fiókazonosítót. Ha egy szegmens a *Vevő* entitástól eltérő entitásokon alapul, vagy ha több attribútumot szeretne tartalmazni a ContactProfile-ból *, válassza a* Project attribútumok **lehetőséget**, ha további attribútumokat szeretne hozzáadni ezekből az entitásokból a kimeneti entitáshoz.
 
   Például: A szegmens az *Ügyfél* entitáshoz kapcsolódó, vásárlási adatokat tartalmazó entitáson alapul. A szegmens az adott évben termékeket vásároló összes spanyolországi ügyfelet keresi. Dönthet úgy, hogy olyan attribútumokat fűz hozzá, mint az áruk ára vagy a vásárlás dátuma a kimeneti entitás összes egyező vevői rekordjához. Ez az információ hasznos lehet a teljes költéssel kapcsolatos szezonális korrelációk elemzéséhez.

   :::image type="content" source="media/segments-project-attributes.png" alt-text="Példa a kimeneti entitáshoz hozzáadandó, az oldalpanelen kijelölt elővetített attribútumokra.":::
 
   A kapcsolattartók tervezett attribútumával rendelkező üzleti partnereken alapuló szegmensekre vonatkozó mintakimenet:

   |Azonosító  |Számla neve  |Bevétel  |Kapcsolattartó neve  | Kapcsolattartó szerepköre|
   |---------|---------|---------|---------|---|
   |10021     | Contoso | 100K | [Abbie Moss, Ruth Soto]  | [CEO, beszerzési vezető]

   > [!NOTE]
   > - **A projektattribútumok csak olyan entitások** esetében működnek, amelyek egy-a-többhöz kapcsolatban állnak a Customer *vagy* ContactProfile *entitással*. Egy ügyfél például több előfizetéssel is rendelkezhet.
   > - Ha a kivetíteni kívánt attribútum egynél több ugrásnyira van a *kapcsolat által meghatározott Customer* vagy *ContactProfile* entitástól, akkor ezt az attribútumot a létrehozott szegmenslekérdezés minden szabályában használni kell.
   > - Ha a kivetíteni kívánt attribútum csak egy ugrásnyira van a Customer *vagy* ContactProfile *entitástól, ennek az* attribútumnak nem kell jelen lennie a létrehozott szegmenslekérdezés minden szabályában.
   > - A **Vetített attribútumokat** figyelembe veszi a rendszer a beállított operátorok használatakor.

1. Válassza a Futtatás **lehetőséget** a szegmens létrehozásához. Válassza a Mentés **lehetőséget**, ha meg szeretné tartani az aktuális konfigurációt, és később szeretné futtatni a szegmenst. Megjelenik a **Szegmensek** oldal.

### <a name="segment-builder-tips"></a>Szegmensépítői tippek

Amikor szegmenst hoz létre a szegmensépítővel, tartsa szem előtt az alábbi tippeket:

- A szegmensépítő nem javasol érvényes értékeket az entitásokból a feltételek operátorainak beállításakor. Az **Adatok** > **Entitások** helyen letöltheti az entitásadatokat, és láthatja, hogy mely értékek érhetők el.
- A dátumokon alapuló feltételek lehetővé teszik a rögzített dátumok és a lebegő dátumtartomány közötti váltást.
- Ha a szegmensre több szabály is vonatkozik, akkor a szerkesztett szabály mellett egy függőleges kék vonal van.
- A szabályokat és feltételeket a szegmensdefinícióban más helyre is áthelyezheti. Jelölje ki a függőleges három pontot (&vellip;) egy szabály vagy feltétel mellett, és válassza ki, hogyan és hol szeretné áthelyezni.
- A **Visszavonás** és a **Visszaállítás** vezérlőelemek a parancssávban visszagördülnek a változásokhoz.
- A szegmens létrehozása után egyes szegmensek lehetővé [teszik a szegmens](segments.md#track-usage-of-a-segment) használatának nyomon követését.

## <a name="next-steps"></a>További lépések

[Exportáljon egy szegmenst](export-destinations.md), és fedezze fel az [Ügyfélkártya integrációját](customer-card-add-in.md), hogy használhassa a szegmenseket más alkalmazásokban.

[!INCLUDE [footer-include](includes/footer-banner.md)]
