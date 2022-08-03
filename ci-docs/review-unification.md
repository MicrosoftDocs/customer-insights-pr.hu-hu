---
title: Adatok egységesítésének áttekintése
description: Tekintse át az adategyesítési lépéseket, hozzon létre egységes ügyfélprofilokat, és tekintse át az eredményeket
ms.date: 06/02/2022
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
ms.openlocfilehash: 20728ffaef9bb705410b3ac22d19868ffd5d1243
ms.sourcegitcommit: 3c5b0b40b2b45e420015bbdd228ce0e610245e6f
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/12/2022
ms.locfileid: "9139587"
---
# <a name="review-data-unification"></a>Adatok egységesítésének áttekintése

Az egyesítési folyamat ezen utolsó lépése a folyamat lépéseinek összegzését mutatja be, és lehetőséget nyújt a módosítások elvégzésére az egységes profil létrehozása előtt.

:::image type="content" source="media/m3_review.png" alt-text="Képernyőkép: Ügyfélprofilok áttekintése és létrehozása.":::

## <a name="review-the-data-unification-steps"></a>Az adategyesítési lépések áttekintése

1. Válassza a Szerkesztés **lehetőséget** az adategyesítési lépések bármelyikénél az áttekintéshez és a módosítások elvégzéséhez.

1. Ha elégedett a választásokkal, válassza az Ügyfélprofilok létrehozása **lehetőséget**. Az **Egységesítés** oldal az egyesített ügyfélprofil létrehozásakor jelenik meg. A Forrás mezők kivételével **minden csempe Várólistán** vagy **Frissítésen** alapuló állapotot mutat **.**

   :::image type="content" source="media/m3_unify_refreshing.png" alt-text="Képernyőkép az Egyesítés lapról, amelyen a Sorok sorba sorba állítva vagy a Frissítő csempék láthatók.":::

   [!INCLUDE [progress-details-pane-include](includes/progress-details-pane.md)]

Az egyesítési algoritmus befejezése eltart egy ideig, és addig nem módosíthatja a konfigurációt, amíg be nem fejeződik. Amikor az egyesítési folyamat befejeződik, az egyesített ügyfélprofil entitás, az úgynevezett *Ügyfél*, megjelenik a **Profilok** szakasz Entitások **lapján**. Az első sikeres egyesítési futtatás létrehozza az egyesített Ügyfél *entitást*. Az összes későbbi futtatás kibontja ezt az entitást.

## <a name="review-the-results-of-data-unification"></a>Az adategyesítés eredményeinek áttekintése

Az egyesítés után az **Adatok** > **egyesítése** oldal az egyesített ügyfélprofilok számát jeleníti meg. Az egyesítési folyamat egyes lépéseinek eredményei megjelennek az egyes csempéken. A Forrás mezők **például** a leképezett attribútumok (mezők) számát, az Ismétlődő rekordok **pedig** a talált duplikált rekordok számát jelenítik meg.

:::image type="content" source="media/m3_unified.png" alt-text="Képernyőkép az Adatok egyesítése lapról az adatok egyesítése után.":::

> [!TIP]
> Az **Egyezési feltételek** csempe csak akkor jelenik meg, ha több entitás lett kiválasztva.

Javasoljuk, hogy tekintse át az eredményeket, különösen az egyezési szabályok [minőségét](data-unification-update.md#manage-match-rules), és szükség esetén finomítsa azokat.

Ha szükséges, módosítsa az egyesítési beállításokat [,](data-unification-update.md) és futtassa újra az egyesített profilt.

## <a name="next-step"></a>Következő lépés

Konfigurálja a tevékenységeket, a gazdagítást [,](activities.md) a kapcsolatok [vagy](enrichment-hub.md) a mértékeket [, hogy további betekintést nyerjen ügyfeleibe.](relationships.md)[...](measures.md)

[!INCLUDE[footer-include](includes/footer-banner.md)]
