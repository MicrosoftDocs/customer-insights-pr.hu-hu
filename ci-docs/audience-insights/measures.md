---
title: Az intézkedések megértése és kezelése
description: Ismerje meg, hogy az intézkedések hogyan segítenek elemezni és tükrözni vállalkozása teljesítményét.
ms.date: 03/24/2022
ms.subservice: audience-insights
ms.topic: conceptual
author: v-wendysmith
ms.author: wameng
ms.reviewer: v-wendysmith
manager: shellyha
searchScope:
- ci-measures
- ci-measure-builder
- ci-measure-template
- ci-enrichment-details
- customerInsights
ms.openlocfilehash: ef10f480086ccac4fa5c6c58818e35ecae67532c
ms.sourcegitcommit: 9ef2cf99b847e7bd8f890f83d84b3a4045aaf8cc
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/01/2022
ms.locfileid: "8529680"
---
# <a name="measures-overview"></a>Intézkedések áttekintése

A mértékek segítségével az ügyfelek viselkedése és üzleti teljesítménye jobban érthető. Az [egyesített profilokból](data-unification.md) származó releváns értékeket veszik alapul. Például egy vállalkozás látni szeretné az *ügyfélre jutó teljes költést* , hogy megértse az egyes ügyfelek vásárlási előzményeit, vagy mérje a *vállalat teljes értékesítését*, hogy megértse az egész üzlet összesített szintű bevételét.  

A mértékeket a mértékszerkesztővel [, egy adatlekérdező platformmal, különböző operátorokkal és egyszerű leképezési lehetőségekkel hozzák létre](measure-builder.md). Lehetőséget ad az adatok szűrésére, az eredmények csoportosítására, az [entitáskapcsolatok elérési útjainak](relationships.md) észlelésére és a kimenet előnézetére. Az általánosan használt mértékek hatékony konfigurálásához előre definiált sablonokat [használhat](measure-templates.md).

A mértékszerkesztő segítségével üzleti tevékenységeket tervezhet az ügyféladatok lekérdezésével és a betekintések kinyerésével. Ha például egy *ügyfélre jutó teljes költség* és az *egy ügyfélre jutó teljes megtérülés* mértékeket hozza létre, akkor könnyebben azonosítható a nagy költéssel, mégis nagy megtérüléssel jellemezhető ügyfelek csoportja. Ezen intézkedések alapján létrehozhat [egy szegmenst](segments.md) a következő legjobb műveletek végrehajtásához.

## <a name="manage-your-measures"></a>Intézkedések kezelése

A **Mértékek** lapon láthatja a mértékek listáját.

Információkat talál a mérték típusáról, az létrehozóról, a létrehozás dátumáról, a státuszáról és az állapotáról. Ha kiválaszt egy mértéket a listából, megtekintheti a kimenetet, és letölthet egy CSV fájlt.

:::image type="content" source="media/measures-actions.png" alt-text="Az egyes intézkedések kezelésére szolgáló műveletek."lightbox="media/measures-actions.png":::

A mértékegység kiválasztásakor a következő műveletek érhetők el:

- **Szerkessze** a mérőszám konfigurációját.
- **Mérték megkettőzése**. Megadhatja, hogy azonnal módosítja-e a tulajdonságait, vagy egyszerűen csak menti a duplikált példányt.
- **Frissítse** a mértéket a legújabb adatok alapján. Ha egyszerre szeretné frissíteni az összes mértéket, jelölje ki az összes mértéket, majd a **Frissítés parancsot**.
- **Nevezze át** az intézkedést.
- **Aktiválás** vagy **Inaktiválás**. Az inaktív mértékek nem frissülnek az [ütemezett frissítés](system.md#schedule-tab) során.
- **Címke** a szegmens címkéinek [kezeléséhez](work-with-tags-columns.md#manage-tags).
- **Törölje** az intézkedést.

[!INCLUDE [progress-details-include](../includes/progress-details-pane.md)]

## <a name="next-step"></a>Következő lépés

Meglévő intézkedésekkel létrehozhat [egy ügyfélszegmenst](segments.md).

[!INCLUDE[footer-include](../includes/footer-banner.md)]
