---
title: Adatok egységesítésének áttekintése
description: Tekintse át az adategyesítés lépéseit, hozzon létre egységes ügyfélprofilokat, és tekintse át az eredményeket
ms.date: 05/04/2022
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
ms.openlocfilehash: 4c709dfb55bf079dd2fe99e41adb4c77c2bece4b
ms.sourcegitcommit: 6a5f4312a2bb808c40830863f26620daf65b921d
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/11/2022
ms.locfileid: "8742970"
---
# <a name="review-data-unification"></a>Adatok egységesítésének áttekintése

[!INCLUDE [m3-prod-trial-note](includes/m3-prod-trial-note.md)]

Az egyesítési folyamat utolsó lépése a folyamat lépéseinek összegzését mutatja be, és lehetőséget ad a módosítások elvégzésére az egységes profil létrehozása előtt.

:::image type="content" source="media/m3_review.png" alt-text="Képernyőkép: Ügyfélprofilok áttekintése és létrehozása.":::

## <a name="review-the-data-unification-steps"></a>Az adategyesítés lépéseinek áttekintése

1. Az adategyesítési lépések bármelyikén válassza a Szerkesztés **lehetőséget** a módosítások áttekintéséhez és végrehajtásához.

1. Ha elégedett a választásokkal, válassza az Ügyfélprofilok létrehozása **lehetőséget**. Az **Egyesítés** lap az egységes ügyfélprofil létrehozása közben jelenik meg. Az egyesítő algoritmus végrehajtása időbe telik, és nem módosíthatja a konfigurációt, amíg be nem fejeződik.

   [!INCLUDE [m3-task-details-include](includes/m3-task-details.md)]

Amikor az egyesítési folyamat befejeződik, az Egyesített ügyfélprofil-entitás, az Ügyfél *a* Profilok **szakasz Entitások** lapján **jelenik meg**. Az első sikeres egyesítési futtatás létrehozza az egységes Vevő *entitást*. Minden további futtatás kibontja az entitást.

## <a name="review-the-results-of-data-unification"></a>Az adategyesítés eredményeinek áttekintése

Az egyesítés után az **Adategyesítés** > **lapon** az egységes ügyfélprofilok száma látható. Az egyesítési folyamat egyes lépéseinek eredményei minden csempén megjelennek. A Forrás mezők **például a leképezett attribútumok (mezők)** számát, **az Ismétlődő rekordok pedig** a talált ismétlődő rekordok számát mutatják.

:::image type="content" source="media/m3_unified.png" alt-text="Képernyőkép az Adatok egyesítése lapról az adatok egyesítése után.":::

> [!TIP]
> Az **Egyező feltételek** csempe csak akkor jelenik meg, ha több entitás van kijelölve.

Javasoljuk, hogy tekintse át az eredményeket, különösen a mérkőzésszabályok [minőségét](data-unification-update.md#manage-match-rules), és szükség esetén finomítsa azokat.

Szükség esetén módosítsa az egyesítési beállításokat [,](data-unification-update.md) és futtassa újra az egységes profilt.

## <a name="next-step"></a>Következő lépés

Konfiguráljon [tevékenységeket](activities.md), [gazdagodást](enrichment-hub.md), [kapcsolatok](relationships.md) vagy [intézkedéseket](measures.md), hogy több betekintést nyerjen az ügyfelekbe.

[!INCLUDE[footer-include](includes/footer-banner.md)]
