---
title: Szegmensekre vonatkozó alapértelmezett hozzájárulási szabályok kezelése
description: A hozzájárulás-kezelési képességgel letilthatja vagy módosíthatja az alapértelmezett jóváhagyási szabályokat, ha a felülírások engedélyezve vannak.
ms.date: 12/01/2021
mms.topic: how-to
author: smithy7
ms.author: smithc
ms.reviewer: mhart
manager: shellyha
ms.openlocfilehash: 4eae4da67fd4c6e70800f495ba30366d4fc9a0dd
ms.sourcegitcommit: e7cdf36a78a2b1dd2850183224d39c8dde46b26f
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/16/2022
ms.locfileid: "8228942"
---
# <a name="disable-or-change-default-consent-rules"></a>Alapértelmezett hozzájárulási szabályok letiltása vagy módosítása

Ha szervezetei a beleegyezéskezelési képességet célközönség [elemzésekhez kombinálva használják,](../consent-management/overview.md) a rendszergazdák kényszeríthetik a szegmensekre vonatkozó jóváhagyási szabályokat [.](activate-consent.md) 

A szegmens területén érvényes beleegyezési szabályokkal minden szegmens tájékoztatja a beleegyezési ellenőrzés állapotát és szabályait. Ha a felülbírálások engedélyezettek, az alapértelmezett hozzájárulási szabályok bizonyos szegmensek esetében ki vannak kapcsolva. Egy szegmens minden létrehozója további beleegyezési szabályokat adhat hozzá az alapértelmezett szabályokon felül egy szegmenshez. 

## <a name="for-administrators"></a>Rendszergazdáknak

:::image type="content" source="../consent-management/media/consent-rules-segment.png" alt-text="Szegmensszerkesztő a jóváhagyási szabály beállításaival.":::

**Az alapértelmezett hozzájárulási szabályok inaktiválása:**

1. A Hozzájárulási szabályokról **szóló értesítésben válassza a** Részletek **megtekintése lehetőséget**. 

1. Állítsa az Alapértelmezett hozzájárulási **szabályokat** Ki **értékre**.

**További hozzájárulási szabályok hozzáadása:**

1. A Hozzájárulási szabályokról **szóló értesítésben válassza a** Részletek **megtekintése lehetőséget**. 

1. Válassza a Hozzájárulási szabályok hozzáadása lehetőséget **, és válasszon egy hozzájárulási szabályt a** Hozzájárulás adattípusának **kiválasztása legördülő listából.**

1. Az új szabály szegmensre való alkalmazásához kattintson **a Mentés** gombra.

## <a name="for-contributors"></a>Közreműködőknek

Ha kényszerített beleegyezési szabályok nélkül szeretne szegmenst létrehozni, együtt kell működnie a rendszergazdával, hogy letiltsa őket a szegmensben. A saját beleegyezési szabályait azonban hozzáadhatja a tulajdonában és kezeléséhez.

Ez egy három lépésből álló folyamat: 
1. [Hozza létre a szegmenst](segments.md) célközönség elemzésekben, és mentse el. 

1. Ossza meg a szegmens nevét a rendszergazdával, és kérje meg őket, hogy engedélyezzék [a](activate-consent.md) szegmens felülbírálását. 

1. Nyissa meg újra a szegmenseket. A Hozzájárulási szabályokról **szóló értesítésben válassza** a **Részletek** megtekintése lehetőséget, és adja hozzá az alkalmazni kívánt hozzájárulási szabályokat. Ezután mentse **és** **futtassa** a szegmenst.



[!INCLUDE[footer-include](../includes/footer-banner.md)] 
