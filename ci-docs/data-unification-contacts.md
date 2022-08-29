---
title: Egyesített kapcsolattartói profil létrehozása (előzetes verzió)
description: Az adategyesítési folyamaton keresztül egyetlen fő adatkészletet hozhat létre a kapcsolattartókról.
ms.date: 08/12/2022
ms.reviewer: v-wendysmith
ms.subservice: audience-insights
ms.topic: overview
author: Scott-Stabbert
ms.author: sstabbert
manager: shellyha
searchScope:
- ci-map
- ci-match
- ci-merge
- customerInsights
ms.openlocfilehash: 721f47563582a94b5b8244ca5d5d7d1350695512
ms.sourcegitcommit: 267c317e10166146c9ac2c30560c479c9a005845
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/16/2022
ms.locfileid: "9305081"
---
# <a name="create-a-unified-contact-profile-preview"></a>Egyesített kapcsolattartói profil létrehozása (előzetes verzió)

Az üzleti fiókok [egyesítése után](map-entities.md) opcionálisan egyesítheti a partnerek kapcsolattartóit, és összekapcsolhatja az egyesített kapcsolattartókat az egyesített fiókokkal. A kapcsolategyesítési folyamat több adatforrásból térképezi fel a kapcsolattartási adatokat, eltávolítja az ismétlődéseket, egyezteti az entitások adatait, beállítja a szemantikai leképezést, kapcsolatok hoz létre a kapcsolattartók és a partnerek között, majd létrehoz egy egységes kapcsolattartói profilt.

[!INCLUDE [m3-first-run-note](includes/m3-first-run-note.md)]

Az első néhány lépés megegyezik a fiókok egyesítésének lépéseivel.

## <a name="prerequisites"></a>Előfeltételek

A partner- és kapcsolattartói rekordoknak rendelkezniük kell egy egyedi kulccsal (más néven idegen kulccsal), amely összeköti őket. Például egy fiókazonosító, amely a partnerrekordban és a kapcsolattartói rekordban található, és amely összeköti a partnert és a kapcsolattartót.

## <a name="preview-limitations"></a>Az előnézet korlátozásai

- A fiókra mutató linkkel nem rendelkező névjegyek el lesznek dobva.
- Ha egy fiókot deduplikálnak, a rendszer az egyesítési beállítások alapján azonosítja a győztes rekordját. A vesztes rekordok nincsenek kiválasztva, ezért eldobódnak. A vesztes rekordokhoz társított névjegyek el lesznek dobva.
- Egy fióknak több névjegye is lehet, de egy névjegy egyetlen fiókhoz van kapcsolva.
- A szemantikai leképezési lépésben leképezett kapcsolattartó attribútumok az egyetlen attribútumok, amelyek megjeleníthetők az Ügyfél kártyán. 17 attribútum azonban rendelkezésre áll.

## <a name="select-source-fields"></a>Forrásmezők kiválasztása

1. A Névjegyek egyesítése (előzetes verzió) **alatt** válassza az Első lépések **lehetőséget**.

1. [Válassza ki a kapcsolattartói adatforrások entitásait és mezőit](map-entities.md), beleértve az elsődleges kulcsokat és attribútumtípusokat.

1. Válassza a **Következő** lehetőséget.

## <a name="remove-duplicate-records"></a>Duplikált rekordok eltávolítása

1. [Igény szerint deduplikációs szabályokat](remove-duplicates.md) is meghatározhat a kiválasztott entitásokhoz.

1. Válassza a **Következő** lehetőséget.

## <a name="match-conditions"></a>Egyezési feltételek

1. [Határozza meg az egyezési sorrendet és az entitások közötti egyeztetés szabályait](match-entities.md).

1. Válassza a **Következő** lehetőséget.

## <a name="unify-contact-fields"></a>Kapcsolatmezők egyesítése

1. [Kapcsolattartó mezők](merge-entities.md) egyesítése és kizárása.

1. Válassza a **Következő** lehetőséget.

## <a name="define-the-semantic-fields-for-unified-contacts"></a>Határozza meg az egyesített kapcsolattartók szemantikai mezőit

Az egyesítési folyamat ezen lépése leképezi az egyesített kapcsolattartó mezőket a szemantikai típusokra. A B-től B-ig az ügyfélkártyák a számlákat mutatják. Ha a kártya ki van választva, a fiókhoz társított összes névjegy megjelenik. Az ebben a lépésben leképezett mezők azok a mezők, amelyek megjelennek a kártyákon.

1. Válassza ki azt a szemantikai típust, amely leképezi az egyes egyesített mezőket. Válassza a Nincs **lehetőséget**, ha egy szemantikai típus nem érhető el.

   :::image type="content" source="media/semantic_mapping.png" alt-text="Képernyőkép a szemantikai mezők oldaláról a szemantikai típusok meghatározásához." lightbox="media/semantic_mapping.png":::

1. Az összes egyesített mező hozzárendelése után válassza a Tovább **lehetőséget**.

## <a name="set-the-relationship-between-contacts-and-accounts"></a>A kapcsolattartók és a partnerek közötti kapcsolat beállítása

Az egyesítési folyamat ezen lépése összekapcsolja a kapcsolattartási adatait a megfelelő fiókadatokkal.

1. Minden entitáshoz adja meg a következő adatokat:

   - **Idegen kulcs a kapcsolattartó entitástól**: Válassza ki azt az attribútumot, amely összeköti a kapcsolattartót a partnerrel.
   - **Számlaentitáshoz**: Válassza ki a kapcsolattartóhoz társított fiókentitást.

   :::image type="content" source="media/contact_relationship.png" alt-text="Képernyőkép a Kapcsolat lapról a kapcsolattartó és a partner entitások összekapcsolásához.":::

1. Válassza a **Következő** lehetőséget.

## <a name="review-contact-unification"></a>Kapcsolattartók egységesítésének áttekintése

Tekintse át a módosítások összegzését, hozza létre az egységes profilt, és tekintse át az eredményeket.

### <a name="review-and-create-contact-profiles"></a>Kapcsolattartói profilok áttekintése és létrehozása

Az egyesítési folyamat ezen utolsó lépése a folyamat lépéseinek összegzését mutatja be, és lehetőséget nyújt a módosítások elvégzésére az egyesített kapcsolattartói profil létrehozása előtt.

:::image type="content" source="media/b2b_review_contacts.png" alt-text="Képernyőkép: Kapcsolattartói profilok áttekintése és létrehozása.":::

1. Válassza a Szerkesztés **lehetőséget** a kapcsolategyesítési lépések bármelyikén az esetleges módosítások áttekintéséhez és végrehajtásához.

1. Ha elégedett a választásokkal, válassza a Névjegyprofilok **létrehozása lehetőséget**. Az **Egységesítés** lap az egyesített kapcsolattartói profil létrehozásakor jelenik meg.
  
   :::image type="content" source="media/b2b_unify_refreshing.png" alt-text="Képernyőkép a Névjegyek egyesítése lapról, amelyen a Várólista vagy a Frissítés felirat látható csempék láthatók.":::

   [!INCLUDE [progress-details-pane-include](includes/progress-details-pane.md)]

Az egyesítési algoritmus befejezése eltart egy ideig, és addig nem módosíthatja a konfigurációt, amíg be nem fejeződik.

### <a name="view-the-results-of-contact-unification"></a>A kapcsolategyesítés eredményeinek megtekintése

Az egyesítés befejezése után az **Adatok** > **egyesítése** oldal megjeleníti az egyesített kapcsolattartói profilok számát. Az egyesítési folyamat egyes lépéseinek eredményei az egyes csempéken megjelennek. A Forrás mezők **például** a leképezett attribútumok (mezők) számát, az Ismétlődő rekordok **pedig** a talált duplikált rekordok számát jelenítik meg.

:::image type="content" source="media/unified_contacts.png" alt-text="Képernyőkép az Adatok egyesítése lapról a névjegyek egységesítése után.":::

> [!TIP]
> Az **Egyezési feltételek** csempe csak akkor jelenik meg, ha több entitás lett kiválasztva.

Javasoljuk, hogy tekintse át az eredményeket, különösen az egyezési szabályok [minőségét](data-unification-update.md#manage-match-rules), és szükség esetén finomítsa azokat.

Ha szükséges, módosítsa a kapcsolattartó-egyesítési beállításokat [,](data-unification-update.md) és futtassa újra az egyesített profilt.

### <a name="verify-output-entities-from-data-unification"></a>Kimeneti entitások ellenőrzése adategyesítésből

Lépjen az **Adatentitások** > **elemre** a kimeneti entitások ellenőrzéséhez.

A ContactProfile *nevű* egyesített kapcsolattartói profil entitás a **Szemantikus entitások** szakaszban jelenik meg. Az első sikeres egyesítési futtatás létrehozza az egyesített ContactProfile *entitást*. Az összes későbbi futtatás kibontja ezt az entitást.

Létrejön a *ContactsCustomer* entitás (előzetes verzió), amely a **Profilok** szakaszban jelenik meg. Ez az entitás tartalmazza a kapcsolattartási adatokat a fiókokra mutató hivatkozások nélkül. Ez az entitás bemenetként szolgál a kapcsolategyesítés szemantikai leképezési és kapcsolati lépéseihez.

A deduplikációs és konföderációs entitások létrehozása és megjelenítése a **Rendszer** szakaszban történik. Az egyes forrásentitások deduplikált entitása létrejön a Deduplication_DataSource_Entity **névvel**. A **ContactsConflationMatchPairs** entitás információkat tartalmaz az entitások közötti egyezésekről.

A deduplikált kimeneti entitás a következő információkat tartalmazza:
- Azonosítók / kulcsok
  - Elsődleges kulcs és Alternatív azonosító mezők. Az Alternatív azonosító mező a rekordhoz azonosított összes alternatív azonosítóból áll.
  - Deduplication_GroupId mező mutatja az entitáson belül azonosított csoportot vagy fürtöt, amely a hasonló bejegyzéseket a megadott deduplikáció mezők alapján csoportosítja. Ezt a rendszerfeldolgozási célokra használják. Ha nincsenek megadva manuális deduplikációs szabályok, és a rendszer által definiált deduplikációs szabályok vonatkoznak, akkor előfordulhat, hogy ez a mező nem található meg a deduplikálás kimeneti entitásban.
  - Deduplication_WinnerId: Ez a mező tartalmazza az azonosított csoportokból vagy fürtökből a nyertes azonosítót. Ha a Deduplication_WinnerId megegyezik egy rekord elsődleges kulcsával, ez azt jelenti, hogy az a rekord lesz a győztes rekord.
- A deduplikációs szabályok definiáló mezői.
- Szabály és Pontszám mezők, amelyekben a deduplikációs szabályok alkalmazva lettek és az egyeztető algoritmus által visszaadott pontszám is megegyezik.

## <a name="next-step"></a>Következő lépés

Konfigurálja a [tevékenységeket](activities.md), [a gazdagítást](enrichment-hub.md) vagy [a kapcsolatok](relationships.md), hogy további betekintést nyerjen a névjegyekbe.
