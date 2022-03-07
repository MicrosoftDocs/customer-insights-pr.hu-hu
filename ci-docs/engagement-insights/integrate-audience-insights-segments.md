---
title: Az célközönség információk szegmensek használata az elkötelezettségi információk jelentések szűréséhez
description: A célközönséggel kapcsolatos szegmenseit használhatja a viselkedési adatok interaktív elemzésekben, amelyeket az elkötelezettségi információk segítségével gyűjtött az ügyfél weboldaláról.
ms.date: 07/27/2021
ms.topic: conceptual
author: mkisel
ms.author: mkisel
ms.reviewer: mhart
manager: shellyha
ms.openlocfilehash: 9c8c7a1a9216e04ebee100c548afbc745af396ec
ms.sourcegitcommit: e7cdf36a78a2b1dd2850183224d39c8dde46b26f
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/16/2022
ms.locfileid: "8230489"
---
# <a name="use-audience-insights-segments-to-filter-engagement-insights-reports"></a>Az célközönség információk szegmensek használata az elkötelezettségi információk jelentések szűréséhez

[!INCLUDE [cc-beta-prerelease-disclaimer](includes/cc-beta-prerelease-disclaimer.md)]

Az elkötelezettségi információk segítségével célközönséggel kapcsolatos szegmenseit használhatja a viselkedési adatok interaktív elemzésekben, amelyeket az elkötelezettségi információk segítségével gyűjtött adatokhoz.

## <a name="prerequisite"></a>Előfeltétel

- Az elkötelezettségi információk környezet, amelyben az célközönséggel kapcsolatos információk szegmensadatok a célközönség információk környezethez kapcsolódnak, ahol a szegmensek és az ügyfélprofilok létrejönnek. További információ: [Hivatkozás létrehozása a célközönséggel kapcsolatos információk és az elkötelezettségi információk között](integrate-audience-insights-engagement-insights.md)

## <a name="create-audience-insights-segments"></a>A célközönséggel kapcsolatos információk szegmensek létrehozása 

> [!IMPORTANT]
> Ahhoz, hogy a célközönséggel kapcsolatos információk megjelenjenek az elkötelezettséggel kapcsolatos információkban először [futtatnia kell egyesítési és későbbi folyamatokat](../audience-insights/merge-entities.md). A későbbi folyamatok azért fontosak, mert egyedi táblázatot hoznak létre, amely célközönséggel kapcsolatos információs szegmenseket előkészíti a megosztásra az elkötelezettséggel kapcsolatos információkkal. (Ha rendszerfrissítés van ütemezve, a későbbi folyamatokat automatikusan tartalmazza.)

Az célközönség információk szegmenseit használhatja az előre telepített jelentésekben és az Ön által létrehozott egyedi jelentésekben. További információ: [Előre telepített profiljelentések](profile-reports.md) és [Egyéni jelentések létrehozása és szerkesztése](custom-reports.md).

**Az célközönség információk szegmensek használata az elkötelezettségi információk jelentésekben**

1. Válassza a **Munkaterület** lapon az **Adatok** lehetőséget, majd válassza a **Szegmensek** lapot.

    :::image type="content" source="media/integrate-audience-insights-segments1.png" alt-text="A Szegmensek lap kiválasztása.":::

   >[!NOTE]
   > Ha kiválaszt egy célközönséggel kapcsolatos információk szegmenst, akkor célközönséggel kapcsolatos információk területre jut, ahol a szabályok és a logika szempontjából megtudhatja, hogyan lett létrehozva az adott szegmens. További tájékoztatásért menjen a célközönséggel kapcsolatos információk szegmenseivel kapcsolatosan lásd: [Szegmensek megtekintése és létrehozása](../audience-insights/segments.md).

2. Jelöljön ki egy el előre telepített jelentést, vagy hozzon létre egy [egyéni jelentést](custom-reports.md), majd válassza a **Feltétel hozzáadása** lehetőséget. (Ebben a példában az **Oldalmegtekintések** jelentést választottuk.)

    :::image type="content" source="media/integrate-audience-insights-segments2.png" alt-text="Újabb feltétel megadása.":::

3. Válassza a **Szűrés szegmens szerint** lehetőséget, bontsa ki a **Szegmens típusa** listát, majd válassza a **Demográfia** lehetőséget.

    :::image type="content" source="media/integrate-audience-insights-segments3.png" alt-text="Válassza ki a Demográfia szegmenstípust.":::

4. Bontsa ki a **Szegmens neve** listát, majd válasszon egy célközönséggel kapcsolatos információk szegmenst.

    :::image type="content" source="media/integrate-audience-insights-segments4.png" alt-text=" Szegmens kiválasztása.":::

5. Egy vagy több szegmenst is alkalmazhat, például a viselkedési (elkötelezettséggel kapcsolatos információk ) és a demográfiai (célközönséggel kapcsolatos információk) szegmenseket. 

    :::image type="content" source="media/integrate-audience-insights-segments6.png" alt-text="Az oldalnézetek jelentése az egyesült államokbeli ügyfelekre és a kezdőlap szegmensekre korlátozódik.":::

Az előző képen az **Amerikai ügyfelek** és a **Kezdőlap** szegmensek vannak kiválasztva, ami arra korlátozza az **Oldalmegtekintések** jelentését, hogy csak ezt a két szegmenst jelenítse meg. 


>[!NOTE]
> Az célközönség információk szegmenseit használhatja az előre telepített jelentésekben, egyéni jelentésekben és az elkötelezettséggel kapcsolatos információk tölcséreiben. 


[!INCLUDE[footer-include](../includes/footer-banner.md)]