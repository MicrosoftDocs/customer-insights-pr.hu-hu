---
title: Webes SDK-minta futtatása
description: A webes SDK-minta személyre szabása és futtatása.
author: britl
ms.reviewer: mhart
ms.author: britl
ms.date: 10/01/2021
ms.subservice: engagement-insights
ms.topic: conceptual
ms.manager: shellyha
ms.openlocfilehash: a50a10db784ec7c1943c94e74000713309787e5c
ms.sourcegitcommit: e7cdf36a78a2b1dd2850183224d39c8dde46b26f
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/16/2022
ms.locfileid: "8225334"
---
# <a name="run-the-web-sdk-sample-for-dynamics-365-customer-insights-engagement-insights-capability"></a>A webes SDK-minta futtatása az Dynamics 365 Customer Insights aktivitási információk szolgáltatáshoz

[!INCLUDE [cc-beta-prerelease-disclaimer](includes/cc-beta-prerelease-disclaimer.md)]

Az aktivitási információk szolgáltatásának webes SDK-függvénytára egy JavaScript-függvénytár, amely a webhelyén használható mintakódot tartalmaz.

## <a name="prerequisites"></a>Előfeltételek

- Telepítse a [Visual Studio kódot](https://code.visualstudio.com/).
- [Telepítse a Live Server bővítményt](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) a Visual Studio Code programba, és ismerkedjen meg a Live Server futtatásával.
- Rendelkeznie kell egy [tevékenységi műveletek munkaterülettel](create-workspace.md).

## <a name="run-sample"></a>Minta futtatása

1. [A webes SDK-minta letöltése](https://download.pi.dynamics.com/sdk/EngagementInsightsSamples/ei_websdk_sample.zip).

1. Bontsa ki a tömörített `ei_websdk_sample.zip` fájlt.

1. Nyissa meg a Visual Studio kódban lévő kicsomagolt mappát.

1. A tevékenységi műveletek portál megnyitása a munkaterülete számára. Válassza az **Admin** > **Munkaterület** lehetőséget, majd a **Telepítési útmutatót**. Kövesse az első lehetőséget, és válassza a **Kód másolása** lehetőséget a JavaScript-kód kódrészlet.

1. Illessze az `ei_websdk_sample.html` fájlba az ez alatti vonal alá másolt kódrészletet:

   - <-- ILLESSZE BE A JAVASCRIPT-KÓDOT KÓDRÉSZLET AZ ENGAGMENT INSIGHTS PORTÁLRÓL IDE, A SOR ALÁ -- >

1. Nyissa meg a `ei_websdk_sample.html` fájlt a Visual Studio kódban található Live Server segítségével az állapotsoron lévő **Közzététel** elem kiválasztásával.

1. Az oldal megnyitásakor a nézeteseményeket a rendszer automatikusan elküldi. Ha rákattint bármelyik gombra az oldalon, akkor a program műveleteseményeket küld. Az **Események nyomon követése** gomb egyéni eseményeket is küld. Az **Ugrás a Binghez** gombra kattintva műveleteseményt küld, mielőtt megnyitja a Bing-webhelyet.

1. Ha a munkaterületre navigál, nézze meg, hogyan áramlanak az események. Ez a munkaterület a 4. lépésben beírt beviteli kulcshoz van hozzárendelve.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
