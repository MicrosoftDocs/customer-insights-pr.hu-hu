---
title: Szegmensekre vonatkozó alapértelmezett hozzájárulási szabályok kezelése
description: A hozzájáruláskezelési lehetőséggel letilthatja vagy módosíthatja az alapértelmezett hozzájárulási szabályokat, ha a felülbírálás engedélyezve van.
ms.date: 12/01/2021
ms.topic: how-to
author: smithy7
ms.author: smithc
ms.reviewer: mhart
manager: shellyha
ms.openlocfilehash: 43f03ea97765e112a8ea2a7da97cc548c8c84dfc
ms.sourcegitcommit: b7dbcd5627c2ebfbcfe65589991c159ba290d377
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/27/2022
ms.locfileid: "8642578"
---
# <a name="disable-or-change-default-consent-rules"></a>Alapértelmezett hozzájárulási szabályok letiltása vagy módosítása

Ha szervezetei a beleegyezéskezelési képességet [használják](consent-management/overview.md), a rendszergazdák Dynamics 365 Customer Insights kényszeríthetik a [szegmensekre vonatkozó hozzájárulási szabályokat](activate-consent.md). 

A szegmens területén érvényes beleegyezési szabályokkal minden szegmens tájékoztatja a hozzájárulás ellenőrzésének állapotát és szabályait. Ha a felülbírálások engedélyezettek, az alapértelmezett hozzájárulási szabályok ki lesznek kapcsolva bizonyos szegmensek esetében. Egy szegmens minden létrehozója további hozzájárulási szabályokat adhat hozzá az alapértelmezett szabályokon felül egy szegmenshez. 

## <a name="for-administrators"></a>Rendszergazdáknak

:::image type="content" source="consent-management/media/consent-rules-segment.png" alt-text="Szegmensépítő hozzájárulási szabálybeállításokkal.":::

**Az alapértelmezett hozzájárulási szabályok inaktiválása:**

1. A Hozzájárulási **szabályokról** szóló értesítésben válassza a Részletek **megtekintése lehetőséget**. 

1. Állítsa az **Alapértelmezett hozzájárulási szabályokat** Ki **értékre**.

**További hozzájárulási szabályok hozzáadása:**

1. A Hozzájárulási **szabályokról** szóló értesítésben válassza a Részletek **megtekintése lehetőséget**. 

1. Válassza a **Hozzájárulási szabályok hozzáadása lehetőséget**, és válasszon egy hozzájárulási szabályt a **Hozzájárulás adattípusának** kiválasztása legördülő listából.

1. Válassza a Mentés **lehetőséget** az új szabály szegmensre való alkalmazásához.

## <a name="for-contributors"></a>Közreműködők számára

Ha kényszerített hozzájárulási szabályok nélkül szeretne szegmenst létrehozni, együtt kell működnie a rendszergazdával, hogy letiltsa őket a szegmensben. Saját hozzájárulási szabályokat azonban hozzáadhat a tulajdonában lévő és kezelt szegmensekhez.

Ez egy három lépésből álló folyamat: 
1. [Hozza létre a szegmenst](segments.md) a Customer Insights alkalmazásban, és mentse el. 

1. Ossza meg a szegmens nevét a rendszergazdával, és kérje meg őket, hogy engedélyezzék [a szegmens](activate-consent.md) felülbírálását. 

1. Nyissa meg újra a szegmenseket. A Hozzájárulási szabályokról **szóló értesítésben válassza** a **Részletek** megtekintése lehetőséget, és adja hozzá az alkalmazni kívánt hozzájárulási szabályokat. Ezután mentse **és** **futtassa** a szegmenst.



[!INCLUDE [footer-include](includes/footer-banner.md)] 
