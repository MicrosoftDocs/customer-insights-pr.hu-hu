---
title: Webes SDK-minta futtatása
description: A webes SDK-minta személyre szabása és futtatása.
author: britl
ms.reviewer: mhart
ms.author: britl
ms.date: 10/30/2020
ms.service: customer-insights
ms.subservice: engagement-insights
ms.topic: conceptual
ms.manager: shellyha
ms.openlocfilehash: 97e50a51231bcf05f3e381397f0cf41e49afc10e3c3674d7c709c8f521979e12
ms.sourcegitcommit: aa0cfbf6240a9f560e3131bdec63e051a8786dd4
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/10/2021
ms.locfileid: "7036606"
---
# <a name="run-the-web-sdk-sample-for-dynamics-365-customer-insights-engagement-insights-capability"></a>A webes SDK-minta futtatása az Dynamics 365 Customer Insights aktivitási információk szolgáltatáshoz

[!INCLUDE [cc-beta-prerelease-disclaimer](includes/cc-beta-prerelease-disclaimer.md)]

Az aktivitási információk szolgáltatásának webes SDK-függvénytára egy JavaScript-függvénytár, amely a webhelyén használható mintakódot tartalmaz.

## <a name="prerequisites"></a>Előfeltételek

- Telepítse a [Visual Studio kódot](https://code.visualstudio.com/).
- [Telepítse a Live Server bővítményt](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) a Visual Studio Code programba, és ismerkedjen meg a Live Server futtatásával.
- Rendelkeznie kell a [beviteli kulccsal](instrument-website.md).

## <a name="run-sample"></a>Minta futtatása

1. [A webes SDK-minta letöltése](https://download.pi.dynamics.com/sdk/EngagementInsightsSamples/ei_websdk_sample.zip).

1. Bontsa ki a tömörített `ei_websdk_sample.zip` fájlt.

1. Nyissa meg a Visual Studio kódban lévő kicsomagolt mappát.

1. A `ei_websdk_sample.html` fájlban cserélje le a "INGESTION_KEY" karakterláncot az aktivitási információk szolgáltatás portálon található beviteli kulcs értékére, majd a "NAME" karakterláncot az SDK példányának globális nevére. Győződjön meg róla, hogy az összes előfordulást lecseréli.

1. Nyissa meg a `ei_websdk_sample.html` fájlt a Visual Studio kódban található Live Server segítségével az állapotsoron lévő **Közzététel** elem kiválasztásával.

1. Az oldal megnyitásakor a nézeteseményeket a rendszer automatikusan elküldi. Ha rákattint bármelyik gombra az oldalon, akkor a program műveleteseményeket küld. Az **Események nyomon követése** gomb egyéni eseményeket is küld. Az **Ugrás a Binghez** gombra kattintva műveleteseményt küld, mielőtt megnyitja a Bing-webhelyet.

1. Ha a munkaterületre navigál, nézze meg, hogyan áramlanak az események. Ez a munkaterület a 4. lépésben beírt beviteli kulcshoz van hozzárendelve.


[!INCLUDE[footer-include](../includes/footer-banner.md)]