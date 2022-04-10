---
title: Viselkedési adatok felosztása demográfiai dimenziók használatával (összeállított dimenziók)
description: Az egyesített profilok összeállított dimenziói használatával engedélyezheti célközönség információk ügyfélprofil-tulajdonságait.
ms.date: 07/27/2021
ms.topic: conceptual
author: mkisel
ms.author: mkisel
ms.reviewer: mhart
manager: shellyha
ms.openlocfilehash: 95395e09bc0ba5ba93138957c62105f31c709e91
ms.sourcegitcommit: e7cdf36a78a2b1dd2850183224d39c8dde46b26f
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/16/2022
ms.locfileid: "8233050"
---
# <a name="use-demographic-dimensions-for-splitting-behavioral-data"></a>Viselkedési adatok felosztása demográfiai dimenziók használatával

[!INCLUDE [cc-beta-prerelease-disclaimer](includes/cc-beta-prerelease-disclaimer.md)]

Az egyesített profil földrajzi dimenziók használatával az elkötelezettségi információk felhasználói elérhetik célközönség információk profiltulajdonságait. Ezután ezeket a tulajdonságokat a viselkedési adatok interaktív elemzéseiben használhatja, beleértve a webhelyén vagy mobilalkalmazásában az aktivitási információk által rögzített adatokat is.

>[!NOTE]
> Az elkötelezettségi információk gyári dimenziókat tartalmaz az eseménytulajdonságokhoz. További információ: [Dimenziók megtekintése és létrehozása](dimensions.md)

## <a name="prerequisite"></a>Előfeltétel

- Az elkötelezettségi információk környezet, amelyben az ügyfélprofil-adatok a célközönség információk környezethez kapcsolódnak, ahol az ügyfélprofilok létrejönnek. További információ: [Hivatkozás létrehozása a célközönséggel kapcsolatos információk és az elkötelezettségi információk között](integrate-audience-insights-engagement-insights.md)

> [!NOTE]
> Miután létrehozott egy kapcsolatot a célközönség információk és az elkötelezettségi információk környezetek között, akkor csak az ügyfélprofil adott tulajdonságaira vonatkozó adatokat szeretné látni, amelyek hasznosak lehetnek az elkötelezettségi információkban. További tájékoztatásért menjen a [Célközönséggel kapcsolatos információk egyesített profiljai attribútumainak és szegmenseinek engedélyezésére](integrate-audience-insights-engagement-insights.md#enable-audience-insights-unified-profiles-attributes-and-segments) részbe.

## <a name="create-a-new-custom-report"></a>Hozzon létre egy új egyéni jelentést

1. A bal oldali ablaktáblában válassza az **Egyéni** > **Új jelentés** lehetőséget, majd válassza ki a kívánt mértéket. (Ebben a példában az **Oldalmegtekintések óránként** lehetőséget választottuk.)

    :::image type="content" source="media/curated-dimensions1.png" alt-text="Válasszon egy mérőszámot.":::

2. Az Vizualizáció szerkesztőben válassza a **Dimenziók** lehetőséget, majd válassza a **Demográfia** lehetőséget a **Dimenzió típusa** legördülő menüben.

    :::image type="content" source="media/curated-dimensions2.png" alt-text="Demográfia kiválasztása.":::

3. Válassza a **Signal.Customer.*xxx*** dimenziót. (Ez a példa a Signal.Customer.Country entitást mutatja.)

    :::image type="content" source="media/curated-dimensions3.png" alt-text="Válasszon ki egy dimenziót.":::
  
## <a name="limitations"></a>Korlátozások

Jelenleg csak demográfiai dimenziók használatával oszthatja fel a viselkedési adatokat.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
