---
title: Az intézkedések megértése és kezelése
description: Ismerje meg, hogy az intézkedések hogyan segítik a vállalkozás teljesítményének elemzését és tükrözését.
ms.date: 02/28/2022
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: wameng
ms.reviewer: mhart
manager: shellyha
searchScope:
- ci-measures
- ci-measure-builder
- ci-measure-template
- ci-enrichment-details
- customerInsights
ms.openlocfilehash: c46fcc3baba1d6c92c2c0fe459a62277343cc0e4
ms.sourcegitcommit: cf6a0ed44915908a44c70889a2dd199a9d0d4798
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/28/2022
ms.locfileid: "8359781"
---
# <a name="measures-overview"></a>Intézkedések – áttekintés

A mértékek segítségével az ügyfelek viselkedése és üzleti teljesítménye jobban érthető. Az [egyesített profilokból](data-unification.md) származó releváns értékeket veszik alapul. Például egy vállalkozás látni szeretné az *ügyfélre jutó teljes költést* , hogy megértse az egyes ügyfelek vásárlási előzményeit, vagy mérje a *vállalat teljes értékesítését*, hogy megértse az egész üzlet összesített szintű bevételét.  

A mértékszerkesztővel [, egy adatlekérdezési platformmal, különböző operátorokkal és egyszerű leképezési lehetőségekkel hozhatók létre](measure-builder.md). Lehetőséget ad az adatok szűrésére, az eredmények csoportosítására, az [entitáskapcsolatok elérési útjainak](relationships.md) észlelésére és a kimenet előnézetére. Előre definiált sablonokkal [hatékonyan konfigurálhatja](measure-templates.md) az általánosan használt mértékeket.

A mértékszerkesztő segítségével üzleti tevékenységeket tervezhet az ügyféladatok lekérdezésével és a betekintések kinyerésével. Ha például egy *ügyfélre jutó teljes költség* és az *egy ügyfélre jutó teljes megtérülés* mértékeket hozza létre, akkor könnyebben azonosítható a nagy költéssel, mégis nagy megtérüléssel jellemezhető ügyfelek csoportja. [Ezek alapján létrehozhat egy szegmenst](segments.md) a következő legjobb műveletek hajtásához. 

## <a name="manage-your-measures"></a>Intézkedések kezelése

A **Mértékek** lapon láthatja a mértékek listáját.

Információkat talál a mérték típusáról, az létrehozóról, a létrehozás dátumáról, a státuszáról és az állapotáról. Ha kiválaszt egy mértéket a listából, megtekintheti a kimenetet, és letölthet egy CSV fájlt.

Ha egyszerre szeretné frissíteni az összes intézkedést, akkor jelölje be az **összes frissítése** lehetőséget egy adott intézkedés kiválasztása nélkül.

:::image type="content" source="media/measure-actions.png" alt-text="Az egyes intézkedések kezelésére szolgáló műveletek.":::

Válasszon ki egy mértéket a listából a következő lehetőségekhez:

- Adja meg a mérőszám nevét a részletek megtekintéséhez.
- **Szerkessze** a mérőszám konfigurációját.
- **Frissítse** a mértéket a legújabb adatok alapján.
- **Nevezze át** az intézkedést.
- **Törölje** az intézkedést.
- **Aktiválás** vagy **Inaktiválás**. Az inaktív mértékek nem frissülnek az [ütemezett frissítés](system.md#schedule-tab) során.

[!INCLUDE [progress-details-include](../includes/progress-details-pane.md)]

## <a name="next-step"></a>Következő lépés

Meglévő intézkedésekkel létrehozhat [egy ügyfélszegmenst](segments.md).

[!INCLUDE[footer-include](../includes/footer-banner.md)]
