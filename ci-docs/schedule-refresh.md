---
title: Rendszerfrissítés ütemezése
description: A rendszer frissítésének időpontjának ütemezése
ms.date: 08/09/2022
ms.subservice: audience-insights
ms.topic: conceptual
author: NimrodMagen
ms.author: nimagen
ms.reviewer: v-wendysmith
manager: shellyha
searchScope:
- ci-system-schedule
- customerInsights
ms.openlocfilehash: ce10fcfe9906d33209270f8f6930a51b045b13e2
ms.sourcegitcommit: 49394c7216db1ec7b754db6014b651177e82ae5b
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/10/2022
ms.locfileid: "9246429"
---
# <a name="schedule-system-refresh"></a>Rendszerfrissítés ütemezése

Ütemezze az összes [betöltött adatforrás automatikus frissítését](data-sources.md). Az automatikus frissítéssel biztosítható, hogy az adatforrásokból származó frissítések megjelenjenek az egyesített ügyfélprofilokban.

> [!NOTE]
> Power Query az Ön által kezelt adatforrások a saját ütemezésük szerint frissülnek. Az adatforrások frissítésének ütemezéséhez Power Query konfigurálja a frissítési beállításokat az adott adatforrás az **Adatforrások** lapon.
> :::image type="content" source="media/PPDF-edit-refresh.png" alt-text="Power Platform Adatfolyam-frissítési beállítások.":::

## <a name="set-system-refresh-schedule"></a>Rendszerfrissítési ütemezés beállítása

1. Lépjen a Felügyeleti **rendszer elemre** > **,** és válassza az **Ütemezés** lapot.

   :::image type="content" source="media/schedule_refresh.png" alt-text="Frissítés ütemezése lap a Rendszer lapon.":::

1. Az ütemezett frissítés alapértelmezett állapota **Ki**. Az ütemezett frissítések engedélyezéséhez módosítsa a képernyő felső részén látható váltógombot **Be** állásra.

1. Választhat **Heti** (alapértelmezett) és **Napi** frissítések között. Ha heti frissítéseket szeretne ütemezni, jelöljön ki egy vagy több napot, amikor a frissítést futtatni szeretné.

1. Állítsa be az **Időzónát**, majd az **Idő** legördülő listában állítsa be a frissítés időpontját. Ha egy nap alatt több frissítést szeretne ütemezni, válassza a **Másik időpont hozzáadása**.

1. Válassza a **Mentés** lehetőséget a módosítások alkalmazásához.

[!INCLUDE [footer-include](includes/footer-banner.md)]
