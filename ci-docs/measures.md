---
title: A mértékek áttekintése
description: Ismerje meg, hogyan segítenek a mértékek a vállalkozás teljesítményének elemzésében és tükrözésében.
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
ms.openlocfilehash: 880c06bffcfa269151d96cb4c597eed4832fc61b
ms.sourcegitcommit: dca46afb9e23ba87a0ff59a1776c1d139e209a32
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/29/2022
ms.locfileid: "9083121"
---
# <a name="measures-overview"></a>A mértékek áttekintése

A mértékek segítségével az ügyfelek viselkedése és üzleti teljesítménye jobban érthető. Az [egyesített profilokból](data-unification.md) származó releváns értékeket veszik alapul. Például egy vállalkozás látni szeretné az *ügyfélre jutó teljes költést* , hogy megértse az egyes ügyfelek vásárlási előzményeit, vagy mérje a *vállalat teljes értékesítését*, hogy megértse az egész üzlet összesített szintű bevételét.  

A mértékeket a mértékkészítővel [, egy különböző operátorokkal és egyszerű leképezési lehetőségekkel rendelkező adatlekérdezési platformmal hozzák létre](measure-builder.md). Lehetőséget ad az adatok szűrésére, az eredmények csoportosítására, az [entitáskapcsolatok elérési útjainak](relationships.md) észlelésére és a kimenet előnézetére. [Előre definiált sablonokkal](measure-templates.md) hatékonyan konfigurálhatja a gyakran használt mértékeket.

A mértékszerkesztő segítségével üzleti tevékenységeket tervezhet az ügyféladatok lekérdezésével és a betekintések kinyerésével. Ha például egy *ügyfélre jutó teljes költség* és az *egy ügyfélre jutó teljes megtérülés* mértékeket hozza létre, akkor könnyebben azonosítható a nagy költéssel, mégis nagy megtérüléssel jellemezhető ügyfelek csoportja. [Ezen mértékek alapján létrehozhat egy szegmenst](segments.md) a következő legjobb műveletek végrehajtásához.

## <a name="manage-your-measures"></a>Intézkedések kezelése

A **Mértékek** lapon láthatja a mértékek listáját.

Információkat talál a mérték típusáról, az létrehozóról, a létrehozás dátumáról, a státuszáról és az állapotáról. Ha kiválaszt egy mértéket a listából, megtekintheti a kimenetet, és letölthet egy CSV fájlt.

:::image type="content" source="media/measures-actions.png" alt-text="Az egyes intézkedések kezelésére szolgáló műveletek."lightbox="media/measures-actions.png":::

A következő műveletek érhetők el egy mérték kiválasztásakor:

- **Szerkessze** a mérőszám konfigurációját.
- **Mérték megkettőzése**. Megadhatja, hogy azonnal módosítja-e a tulajdonságait, vagy egyszerűen csak menti a duplikált példányt.
- **Frissítse** a mértéket a legújabb adatok alapján. Az összes mérték egyidejű frissítéséhez jelölje ki az összes mértéket, majd **a Frissítés lehetőséget**.
- **Nevezze át** az intézkedést.
- **Aktiválás** vagy **Inaktiválás**. Az inaktív mértékek nem frissülnek az [ütemezett frissítés](system.md#schedule-tab) során.
- **Címke** a [szegmens címkéinek](work-with-tags-columns.md#manage-tags) kezeléséhez.
- **Törölje** az intézkedést.

[!INCLUDE [progress-details-include](includes/progress-details-pane.md)]

## <a name="next-step"></a>Következő lépés

Meglévő intézkedésekkel létrehozhat [egy ügyfélszegmenst](segments.md).

[!INCLUDE [footer-include](includes/footer-banner.md)]
