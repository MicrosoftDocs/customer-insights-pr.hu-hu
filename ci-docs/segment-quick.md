---
title: Egyszerű szegmensek létrehozása gyorsszegmensekkel
description: Hozzon létre egyszerű szegmenseket az ügyfelekről, hogy különböző attribútumok alapján csoportosítsa őket.
ms.date: 03/25/2022
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
ms.openlocfilehash: 98260371a17ff8a05912cc1bc08c67fbe9755727
ms.sourcegitcommit: 8a28e9458b857adf8e90e25e43b9bc422ebbb2cd
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/18/2022
ms.locfileid: "9171157"
---
# <a name="create-simple-segments-with-quick-segments"></a>Egyszerű szegmensek létrehozása gyorsszegmensekkel

A gyorsszegmensek segítségével gyorsan készíthet egyszerű, egy operátorral rendelkező szegmenseket a gyors elemzéshez. A gyorsszegmenseket csak az **egyes ügyfelek** környezetekben támogatja a rendszer.

## <a name="create-a-new-segment-with-quick-segments"></a>Új szegmens létrehozása gyorsszegmensekkel

1. Kattintson a **Szegmensek** lehetőségre.

1. Válassza az Új **létrehozás innen lehetőséget** > **·**.
   - Válassza a **Profilok** lehetőséget, ha az *egyesített ügyfél* entitáson alapuló szegmenset szeretne létrehozni.
   - Ha korábban létrehozott mértékekhez szeretne szegmenst létrehozni, válassza a **Mértékek** lehetőséget.
   - Válassza az **Információ** lehetőséget, ha egy szegmenst szeretne létrehozni az egyik olyan kimeneti entitás köré, amelyet vagy az **Előrejelzések** vagy az **egyéni modellek** használatával hozott létre.

1. Az **új gyors szegmens** párbeszédpanelen jelöljön ki egy attribútumot a **Mező** legördülő listában. A választás alapján a rendszer különböző értékeket biztosít.
   - A kategorikus mezők esetében a 10 legfontosabb ügyfélszám jelenik meg. Válasszon egy **Értéket**, és válassza a **Felülvizsgálat** elemet.
   - Numerikus attribútum esetén a rendszer megmutatja, hogy melyik attribútumérték tartozik az egyes ügyfelek percentilisébe. Válasszon egy **operátort** és egy **értéket**, majd válassza a **Felülvizsgálat** lehetőséget.

1. A rendszer becsült szegmensméretet **biztosít**. Válassza ki, hogy a definiált szegmenst hozza létre, vagy térjen vissza egy másik mező kiválasztásához.

   :::image type="content" source="media/quick-segment-name.png" alt-text="Gyorsszegmens neve és becslése.":::

1. Adja meg a **szegmens név** - és **kimeneti entitásnevét**. Ha szükséges, adjon hozzá [címkéket](work-with-tags-columns.md#manage-tags).

1. Válassza a **Mentés** lehetőséget a szegmens létrehozásához. Megjelenik a **Szegmensek** oldal.

[!INCLUDE [progress-details-include](includes/progress-details-pane.md)]

## <a name="next-steps"></a>További lépések

[Exportáljon egy szegmenst](export-destinations.md), és fedezze fel az [Ügyfélkártya integrációját](customer-card-add-in.md), hogy használhassa a szegmenseket más alkalmazásokban.

[!INCLUDE [footer-include](includes/footer-banner.md)]
