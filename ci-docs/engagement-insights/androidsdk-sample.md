---
title: Android SDK minta
description: Az SDK-val kapcsolatos tudnivalókat tartalmazó minta Android projekt
author: britl
ms.reviewer: m-hartmann
ms.author: britl
ms.date: 06/23/2021
ms.service: customer-insights
ms.subservice: engagement-insights
ms.topic: conceptual
ms.manager: shellyha
ms.openlocfilehash: ba51961bc7f9555d7dba5b6a21c8636011438d75cba87bc132b896841c467a33
ms.sourcegitcommit: aa0cfbf6240a9f560e3131bdec63e051a8786dd4
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/10/2021
ms.locfileid: "7035829"
---
# <a name="run-the-android-sdk-sample"></a>Az Android SDK minta futtatása

[!INCLUDE [cc-beta-prerelease-disclaimer](includes/cc-beta-prerelease-disclaimer.md)]

Ez a mint Android projekt segít megérteni az SDK működését egy alkalmazásban. Nem kell kódot írnia. Egyszerűen adja hozzá a szöveghez az ingestion kulcsot, és azonnal láthatja az eseményeket a munkaterületén.

## <a name="prerequisites"></a>Előfeltételek

- [Android Studio](https://developer.android.com/studio)
- [Ingestion kulcs](get-started-android.md)

## <a name="download-the-android-sdk-sample"></a>Töltse le az Android SDK mintát

1. [Az elköteleződési információk Android SDK minta](https://download.pi.dynamics.com/sdk/EI-SDKs/ei-android-sample.zip) letöltése.
1. Bontsa ki a tömörített `ei-android-sample.zip` fájlt.
1. Nyissa meg a kibontott mappát a Android Studio -ban.
1. Az `AndroidManifest.xml` fájlban, cserélje le a sztringet `"Your-Ingestion-Key"` az Ön munkaterületén található ingestion kulcsra az elköteleződési információkból a **Rendszergazda** > **Munkaterület** > **Telepítési útmutató** alatt. 

   > [!NOTE]
   > A `${applicationId}` szakaszt nem kell lecserélni. A rendszer automatikusan feltölti.

   ```xml
   <application>
   ...
       <provider
           android:authorities="${applicationId}.com.microsoft.engagementinsights.eiandroidsdk.AnalyticsContentProvider"
           android:name="microsoft.dynamics.engagementinsights.eiandroidsdk.AnalyticsContentProvider" />
       <meta-data
           android:name="com.microsoft.engagementinsights.ingestionKey"
           android:value="Your-Ingestion-Key" />
       <meta-data
           android:name="com.microsoft.engagementinsights.autoCapture"
           android:value="true" />
   ...
   </application>
   ```

1. Ha el szeretné indítani a minta projektet, válassza a **Futtatás** gombot.
1. Megtekintheti az eseményeket a munkaterületén.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
