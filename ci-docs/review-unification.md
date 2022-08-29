---
title: Adatok egységesítésének áttekintése
description: Tekintse át az adategyesítési lépéseket, hozzon létre egységes ügyfélprofilokat, és tekintse át az eredményeket
ms.date: 08/12/2022
ms.subservice: audience-insights
ms.topic: tutorial
author: v-wendysmith
ms.author: adkuppa
ms.reviewer: v-wendysmith
manager: shellyha
searchScope:
- ci-match
- ci-merge
- ci-relationships
- customerInsights
ms.openlocfilehash: b4d77effc347e40fecde625a1a42a24900456471
ms.sourcegitcommit: 267c317e10166146c9ac2c30560c479c9a005845
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/16/2022
ms.locfileid: "9303970"
---
# <a name="review-data-unification"></a>Adatok egységesítésének áttekintése

Tekintse át a módosítások összegzését, hozza létre az egységes profilt, és tekintse át az eredményeket.

## <a name="review-and-create-customer-profiles"></a>Ügyfélprofilok áttekintése és létrehozása

Az egyesítési folyamat ezen utolsó lépése a folyamat lépéseinek összegzését mutatja be, és lehetőséget nyújt a módosítások elvégzésére az egységes profil létrehozása előtt.

[!INCLUDE [m3-first-run-note](includes/m3-first-run-note.md)]

:::image type="content" source="media/m3_review.png" alt-text="Képernyőkép: Ügyfélprofilok áttekintése és létrehozása.":::

1. Válassza a Szerkesztés **lehetőséget** az adategyesítési lépések bármelyikénél az áttekintéshez és a módosítások elvégzéséhez.

1. Ha elégedett a választásokkal, válassza **az Ügyfélprofilok** létrehozása (vagy fiókprofilok **létrehozása** b-től B-ig lehetőséget). Az **Egységesítés** oldal az egyesített ügyfélprofil létrehozásakor jelenik meg.

   :::image type="content" source="media/m3_unify_refreshing.png" alt-text="Képernyőkép az Egyesítés lapról, amelyen a Sorok sorba sorba állítva vagy a Frissítő csempék láthatók.":::

   [!INCLUDE [progress-details-pane-include](includes/progress-details-pane.md)]

Az egyesítési algoritmus befejezése eltart egy ideig, és addig nem módosíthatja a konfigurációt, amíg be nem fejeződik.

## <a name="view-the-results-of-data-unification"></a>Az adategyesítés eredményeinek megtekintése

Az egyesítés után az **Adatok** > **egyesítése** oldal megjeleníti az egyesített ügyfélprofilok (vagy a B-től B-ig terjedő fiókprofilok) számát. Az egyesítési folyamat egyes lépéseinek eredményei megjelennek az egyes csempéken. A Forrás mezők **például** a leképezett attribútumok (mezők) számát, az Ismétlődő rekordok **pedig** a talált duplikált rekordok számát jelenítik meg.

:::image type="content" source="media/m3_unified.png" alt-text="Képernyőkép az Adatok egyesítése lapról az adatok egyesítése után.":::

> [!TIP]
> Az **Egyezési feltételek** csempe csak akkor jelenik meg, ha több entitás lett kiválasztva.

Javasoljuk, hogy tekintse át az eredményeket, különösen az egyezési szabályok [minőségét](data-unification-update.md#manage-match-rules), és szükség esetén finomítsa azokat.

Ha szükséges, módosítsa az egyesítési beállításokat [,](data-unification-update.md) és futtassa újra az egyesített profilt.

### <a name="verify-output-entities-from-data-unification"></a>Kimeneti entitások ellenőrzése adategyesítésből

Lépjen az **Adatentitások** > **elemre** a kimeneti entitások ellenőrzéséhez.

Az ügyfélprofil egységes entitása, az úgynevezett *Ügyfél*, a **Profilok** szakaszban jelenik meg. Az első sikeres egyesítési futtatás létrehozza az egyesített Ügyfél *entitást*. Az összes későbbi futtatás kibontja ezt az entitást.

A deduplikációs és konföderációs entitások létrehozása és megjelenítése a **Rendszer** szakaszban történik. Az egyes forrásentitások deduplikált entitása létrejön a Deduplication_DataSource_Entity **névvel**. A **ConflationMatchPairs** entitás információkat tartalmaz az entitások közötti egyezésekről.

A deduplikált kimeneti entitás a következő információkat tartalmazza:
- Azonosítók / kulcsok
  - Elsődleges kulcs és Alternatív azonosító mezők. Az Alternatív azonosító mező a rekordhoz azonosított összes alternatív azonosítóból áll.
  - Deduplication_GroupId mező mutatja az entitáson belül azonosított csoportot vagy fürtöt, amely a hasonló bejegyzéseket a megadott deduplikáció mezők alapján csoportosítja. Ezt a rendszerfeldolgozási célokra használják. Ha nincsenek megadva manuális deduplikációs szabályok, és a rendszer által definiált deduplikációs szabályok vonatkoznak, akkor előfordulhat, hogy ez a mező nem található meg a deduplikálás kimeneti entitásban.
  - Deduplication_WinnerId: Ez a mező tartalmazza az azonosított csoportokból vagy fürtökből a nyertes azonosítót. Ha a Deduplication_WinnerId megegyezik egy rekord elsődleges kulcsával, ez azt jelenti, hogy az a rekord lesz a győztes rekord.
- A deduplikációs szabályok definiáló mezői.
- Szabály és Pontszám mezők, amelyekben a deduplikációs szabályok alkalmazva lettek és az egyeztető algoritmus által visszaadott pontszám is megegyezik.

## <a name="next-step"></a>Következő lépés

- B-től B-ig opcionálisan végezze el [a kapcsolategyesítést](data-unification-contacts.md).

- B-től C-ig konfigurálhatja [a tevékenységeket](activities.md), [a gazdagításokat](enrichment-hub.md), [a kapcsolatok](relationships.md) vagy [a mértékeket](measures.md), hogy további betekintést nyerjen az ügyfelekbe.

[!INCLUDE[footer-include](includes/footer-banner.md)]
