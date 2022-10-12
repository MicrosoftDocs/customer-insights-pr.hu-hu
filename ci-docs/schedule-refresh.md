---
title: Rendszerfrissítés ütemezése
description: A rendszer frissítésének időpontjának ütemezése
ms.date: 09/27/2022
ms.subservice: audience-insights
ms.topic: conceptual
author: NimrodMagen
ms.author: nimagen
ms.reviewer: v-wendysmith
manager: shellyha
searchScope:
- ci-system-schedule
- customerInsights
ms.openlocfilehash: 4aac02b570357d2086f7a9d7340b0e4837157a0b
ms.sourcegitcommit: be341cb69329e507f527409ac4636c18742777d2
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/30/2022
ms.locfileid: "9610331"
---
# <a name="schedule-system-refresh"></a>Rendszerfrissítés ütemezése

Ütemezze az összes [betöltött adatforrás automatikus frissítését](data-sources.md). Az automatikus frissítéssel biztosítható, hogy az adatforrásokból származó frissítések megjelenjenek az egyesített ügyfélprofilokban.

> [!NOTE]
> Power Query az Ön által kezelt adatforrások a saját ütemezésük szerint frissülnek. Az adatforrások frissítésének ütemezéséhez Power Query konfigurálja a frissítési beállításokat az adott adatforrás az **Adatforrások** lapon. Igazítsa az időzítést a felsőbb rétegbeli adatfrissítési ütemezéshez, hogy a frissítések ne egyszerre történjenek meg.
> :::image type="content" source="media/PPDF-edit-refresh.png" alt-text="Power Platform Adatfolyam-frissítési beállítások.":::

## <a name="set-system-refresh-schedule"></a>Rendszerfrissítési ütemezés beállítása

1. Lépjen a Felügyeleti **rendszer elemre** > **,** és válassza az **Ütemezés** lapot.

   :::image type="content" source="media/schedule_refresh.png" alt-text="Frissítés ütemezése lap a Rendszer lapon.":::

1. Az ütemezett frissítés alapértelmezett állapota **Ki**. Az ütemezett frissítések engedélyezéséhez módosítsa a képernyő felső részén látható váltógombot **Be** állásra.

1. Választhat **Heti** (alapértelmezett) és **Napi** frissítések között. Ha heti frissítéseket szeretne ütemezni, jelöljön ki egy vagy több napot, amikor a frissítést futtatni szeretné.

1. Állítsa be az **Időzónát**, majd az **Idő** legördülő listában állítsa be a frissítés időpontját. Ha egy nap alatt több frissítést szeretne ütemezni, válassza a **Másik időpont hozzáadása**. Legfeljebb négy frissítést adhat hozzá.

1. Válassza a **Mentés** lehetőséget a módosítások alkalmazásához.

[!INCLUDE [footer-include](includes/footer-banner.md)]
