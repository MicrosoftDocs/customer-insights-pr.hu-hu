---
title: A szegmensekre vonatkozó alapértelmezett hozzájárulási szabályok kezelése
description: A hozzájáruláskezelési funkcióval letilthatja vagy módosíthatja az alapértelmezett hozzájárulási szabályokat, ha a felülbírálások engedélyezve vannak.
ms.date: 12/01/2021
ms.service: customer-insights
mms.topic: how-to
author: smithy7
ms.author: smithc
ms.reviewer: mhart
manager: shellyha
ms.openlocfilehash: 28c9ea49b1f3aebd3abd7d4de58fe61e6474158b
ms.sourcegitcommit: 48d799535fad84e8b63c80aef48b5c5e87628f58
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/03/2021
ms.locfileid: "7884173"
---
# <a name="disable-or-change-default-consent-rules"></a>Alapértelmezett hozzájárulási szabályok letiltása vagy módosítása

Ha a szervezetek a [hozzájáruláskezelési képességet](../consent-management/overview.md) célközönség elemzéssel kombinálva használják, [a rendszergazdák kényszeríthetik](activate-consent.md) a szegmensekre vonatkozó jóváhagyási szabályokat. 

A szegmens területén érvényes hozzájárulási szabályokkal minden szegmens tájékoztatja a hozzájárulás ellenőrzésének állapotát és a szabályokat. Ha a felülbírálások engedélyezettek, az alapértelmezett hozzájárulási szabályok bizonyos szegmensek esetében ki vannak kapcsolva. Egy szegmens minden létrehozója további hozzájárulási szabályokat adhat hozzá az alapértelmezett szabályokon felül egy szegmenshez. 

## <a name="for-administrators"></a>Rendszergazdáknak

:::image type="content" source="../consent-management/media/consent-rules-segment.png" alt-text="Szegmensépítő hozzájárulási szabálybeállításokkal.":::

**Az alapértelmezett hozzájárulási szabályok inaktiválása:**

1. A **Hozzájárulási szabályok** értesítésben válassza a **Részletek megtekintése** lehetőséget. 

1. Állítsa be az **alapértelmezett hozzájárulási szabályokat** a Ki **értékre**.

**További hozzájárulási szabályok hozzáadása:**

1. A **Hozzájárulási szabályok** értesítésben válassza a **Részletek megtekintése** lehetőséget. 

1. Válassza a **Hozzájárulási szabályok hozzáadása** lehetőséget, és válasszon egy jóváhagyási szabályt a **Hozzájárulási adattípus kiválasztása** legördülő menüből.

1. Válassza a Mentés lehetőséget **az** új szabály szegmensre való alkalmazásához.

## <a name="for-contributors"></a>Közreműködőknek

Ha kényszerített beleegyezési szabályok nélküli szegmenst szeretne létrehozni, a rendszergazdával együtt kell működnie, hogy letiltsa őket a szegmensben. A saját hozzájárulási szabályokat azonban hozzáadhatja a saját és kezelt szegmenseihez.

Ez egy három lépésből álló folyamat: 
1. [Hozza létre a](segments.md) szegmenst célközönség elemzési adatokban, és mentse el. 

1. Ossza meg a szegmens nevét a rendszergazdával, és kérje meg őket, hogy [engedélyezze a szegmens felülbírálását](activate-consent.md). 

1. Nyissa meg újra a szegmenseket. A **Hozzájárulási szabályok értesítésben válassza a** Részletek **megtekintése** lehetőséget, és adja hozzá az alkalmazni kívánt hozzájárulási szabályokat. Ezután **mentse** és **futtassa** a szegmenst.



[!INCLUDE[footer-include](../includes/footer-banner.md)] 
