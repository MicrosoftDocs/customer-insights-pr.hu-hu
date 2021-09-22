---
title: Az iOS SDK minta futtatása
description: Az iOS SDK-val kapcsolatos tudnivalókat tartalmazó minta projekt
author: britl
ms.reviewer: mhart
ms.author: britl
ms.date: 06/23/2021
ms.service: customer-insights
ms.subservice: engagement-insights
ms.topic: conceptual
ms.manager: shellyha
ms.openlocfilehash: 053e626d06d3e17b39b448987410058e45e8ae0385f3ecdef40314cb46ae4bf4
ms.sourcegitcommit: aa0cfbf6240a9f560e3131bdec63e051a8786dd4
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/10/2021
ms.locfileid: "7036831"
---
# <a name="run-the-ios-sdk-sample"></a>Az iOS SDK minta futtatása

[!INCLUDE [cc-beta-prerelease-disclaimer](includes/cc-beta-prerelease-disclaimer.md)]

Ez a minta iOS projekt segít megérteni az SDK működését egy alkalmazásban. Nem kell kódot írnia. Egyszerűen adja hozzá a szöveghez az ingestion kulcsot, és azonnal láthatja az eseményeket a munkaterületén.

## <a name="prerequisites"></a>Előfeltételek

- [Xcode verzió 9+](https://developer.apple.com/xcode/downloads/)
- [Ingestion kulcs](get-started-ios.md)

## <a name="download-the-ios-sdk-sample"></a>Töltse le az iOS SDK mintát

1. [Az elköteleződési információk iOS SDK minta letöltése](https://download.pi.dynamics.com/sdk/EI-SDKs/ei-ios-sample.zip).
1. Bontsa ki a tömörített `ei-ios-sample.zip` fájlt.
1. Nyissa meg az alkalmazás-minta projektet Xcode-ban.
1. Az `EIConfig.plist` fájlban cserélje le a `“YOUR-INGESTION-KEY”` karakterláncot az `ingestionKey` mezőben a munkaterület ingestion kulcsra az elköteleződési információkból a **Rendszergazda** > **Munkaterület** > **Telepítési útmutató** alatt.
1. Ha el szeretné indítani a minta projektet, válassza a **Futtatás** gombot.
1. Megtekintheti az eseményeket a munkaterületén.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
