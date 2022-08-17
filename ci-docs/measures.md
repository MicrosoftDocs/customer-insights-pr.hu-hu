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
ms.openlocfilehash: 99368a7ab2e8d7b3e53c04fbf25bb23bd2e550a9
ms.sourcegitcommit: 49394c7216db1ec7b754db6014b651177e82ae5b
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/10/2022
ms.locfileid: "9245376"
---
# <a name="measures-overview"></a>A mértékek áttekintése

A mértékek segítségével az ügyfelek viselkedése és üzleti teljesítménye jobban érthető. Az [egyesített profilokból](data-unification.md) származó releváns értékeket veszik alapul. Például egy vállalkozás látni szeretné az *ügyfélre jutó teljes költést* , hogy megértse az egyes ügyfelek vásárlási előzményeit, vagy mérje a *vállalat teljes értékesítését*, hogy megértse az egész üzlet összesített szintű bevételét.

Hozzon létre intézkedéseket az üzleti tevékenységek megtervezéséhez az ügyféladatok lekérdezésével és az elemzések kinyerésével. Létrehozhat például egy ügyfélenkénti teljes költés és *egy* ügyfélre *jutó teljes megtérülés mérését*, hogy segítsen azonosítani a magas kiadással, mégis magas hozammal rendelkező ügyfelek csoportját. [Ezután hozzon létre egy szegmenst](segments.md) ezen intézkedések alapján a következő legjobb műveletek végrehajtásához.

## <a name="create-a-measure"></a>Mérőszám létrehozása

Válassza ki, hogyan szeretne mértéket létrehozni a cél célközönség alapján.

# <a name="individual-consumers-b-to-c"></a>[Egyéni fogyasztók (B-to-C)](#tab/b2c)

- A semmiből a mérőkészítővel: [Építsd meg a sajátodat](measure-builder.md).
- Gyakran használt mértékekből: [Használjon előre definiált sablonokat](measure-templates.md).

# <a name="business-accounts-b-to-b"></a>[Üzleti számlák (B-to-B)](#tab/b2b)

A semmiből a mérőkészítővel: [Építsd meg a sajátodat](measure-builder.md).

---

## <a name="manage-existing-measures"></a>Meglévő intézkedések kezelése

**A Mértékek** lapon megtekintheti a létrehozott mértékeket, azok állapotát, mértéktípusát és az adatok legutóbbi frissítésének időpontját. A mértéklistákat bármely oszlop szerint rendezheti, vagy a keresőmező segítségével megkeresheti a kezelni kívánt mértéket.

Válasszon egy mérték mellett az elérhető műveletek megtekintéséhez. Válassza ki a mérték nevét a kimenet előnézetének megtekintéséhez és egy CSV-fájl letöltéséhez.

:::image type="content" source="media/measures-actions.png" alt-text="Az egyes intézkedések kezelésére szolgáló műveletek."lightbox="media/measures-actions.png":::

- **Szerkessze** a mértéket a tulajdonságainak módosításához.
- **Frissítse** a mértéket, hogy a legfrissebb adatokat tartalmazza.
- **Nevezze át** az intézkedést.
- **Az intézkedés aktiválása** vagy **inaktiválása**. Az inaktív mértékek nem frissülnek az [ütemezett frissítés](schedule-refresh.md) során, és az **Állapot** kihagyottként **jelenik** meg, ami azt jelzi, hogy a frissítést nem is kísérelték meg.
- **Címke** a [mérték címkéinek](work-with-tags-columns.md#manage-tags) kezeléséhez.
- **Törölje** az intézkedést.
- **Oszlopok** a megjelenő oszlopok [testreszabásához](work-with-tags-columns.md#customize-columns).
- **Szűrés** a címkék [szűréséhez](work-with-tags-columns.md#filter-on-tags).
- **Keressen rá a névre** a mérték neve szerinti kereséshez.

## <a name="refresh-measures"></a>Frissítési intézkedések

A mértékek automatikus ütemezéssel frissíthetők, vagy igény szerint manuálisan frissíthetők. Egy vagy több mérték manuális frissítéséhez jelölje ki őket, majd válassza a Frissítés **lehetőséget**. Az automatikus frissítés ütemezéséhez [lépjen a Rendszergazdai](schedule-refresh.md) rendszerütemezés **lapra** > **·** > **.**

[!INCLUDE [progress-details-include](includes/progress-details-pane.md)]

[!INCLUDE [footer-include](includes/footer-banner.md)]
