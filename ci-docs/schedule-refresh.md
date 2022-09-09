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
ms.openlocfilehash: 949ea071ca41127b0c45488d5d7af3f6aa4e1c35
ms.sourcegitcommit: d7054a900f8c316804b6751e855e0fba4364914b
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/02/2022
ms.locfileid: "9395959"
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

1. Állítsa be az **Időzónát**, majd az **Idő** legördülő listában állítsa be a frissítés időpontját. Ha egy nap alatt több frissítést szeretne ütemezni, válassza a **Másik időpont hozzáadása**. Legfeljebb négy frissítést adhat hozzá.

1. Válassza a **Mentés** lehetőséget a módosítások alkalmazásához.

[!INCLUDE [footer-include](includes/footer-banner.md)]
