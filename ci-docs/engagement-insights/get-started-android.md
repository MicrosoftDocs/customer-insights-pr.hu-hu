---
title: Első lépések az Android SDK-val
description: Ismerje meg az Android SDK személyre szabását és futtatását
author: britl
ms.reviewer: mhart
ms.author: britl
ms.date: 06/23/2021
ms.service: customer-insights
ms.subservice: engagement-insights
ms.topic: conceptual
ms.manager: shellyha
ms.openlocfilehash: 77e63929bbcc7ecff34a3839af525b76ec3c7f21173ddc5f8f2d69f11c25c441
ms.sourcegitcommit: aa0cfbf6240a9f560e3131bdec63e051a8786dd4
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/10/2021
ms.locfileid: "7036921"
---
# <a name="get-started-with-the-android-sdk"></a>Első lépések az Android SDK-val

[!INCLUDE [cc-beta-prerelease-disclaimer](includes/cc-beta-prerelease-disclaimer.md)]

Ez az oktatóanyag végigvezeti az Android alkalmazás a Dynamics 365 Customer Insights elköteleződési elemzések SDK-val történő instrumentálásának folyamatán. Öt perc múlva vagy hamarabb elkezdi látni az eseményeket a portálon.

## <a name="configuration-options"></a>Konfigurációs beállítások
A következő konfigurációs beállításokat lehet áttenni az SDK-ra:

- **ingestionKey**: Az ingestion kulcs segítségével küldhet eseményeket a munkaterületére.

## <a name="prerequisites"></a>Előfeltételek

- Android Studio

- Minimum Android API szint: 16 (Jelly Bean)

- Egy ingestion kulcs (lásd lejjebb a hozzáférési útmutatót)

## <a name="step-1-integrate-the-sdk-into-your-application"></a>1. lépés SDK beágyazása az alkalmazásba
Kezdje a folyamatot munkaterület kiválasztásával, az Android a mobil platform kiválasztásával és az Android SDK letöltésével.

- A munkaterület kijelöléséhez használja a bal oldali navigációs ablakban található munkaterület-kapcsolót.

- Ha nem rendelkezik meglévő munkaterületekkel, válassza az **Új munkaterület** és kövesse a lépéseket az [új munkaterület](create-workspace.md) létrehozásához.

## <a name="step-2-configure-the-sdk"></a>2. lépés Konfigurálja az SDK-t

1. Munkaterület létrehozása után válassza a **Rendszergazda** > **Munkaterület** majd válassza a  **Telepítési útmutatót**. 

1. Töltse le [az elköteleződési elemzések Android SDK-t](https://download.pi.dynamics.com/sdk/EI-SDKs/ei-android-sdk.zip), és helyezze a `eiandroidsdk-debug.aar` fájlt a `libs` mappába.

1. Nyissa meg a projektszintű `build.gradle` fájlt, és adja hozzá a következő részleteket:
    ```gradle
    dependencies {
        implementation(name: 'eiandroidsdk-debug', ext: 'aar')
        api 'com.google.code.gson:gson:2.8.1'
    }

    repositories {
        flatDir {
            dirs 'libs'
        }
    }
    ```

1. Az elköteleződési elemzések SDK konfigurációját az `AndroidManifest.xml` fájlon keresztül, amely a `manifests` mappa alatt található, állíthatja be. 
1. Másolja az XML-kódrészlet a **Telepítési útmutató** -ból. `Your-Ingestion-Key` adatokat a rendszer automatikusan feltölti.

   > [!NOTE]
   > A `${applicationId}` szakaszt nem kell lecserélni. A rendszer automatikusan feltölti.
   

   ```xml
   <application>
   ...
       <provider
           android:authorities="${applicationId}.com.microsoft.engagementinsights.AnalyticsContentProvider"
           android:name="com.microsoft.engagementinsights.AnalyticsContentProvider" />
       <meta-data
           android:name="com.microsoft.engagementinsights.ingestionKey"
           android:value="Your-Ingestion-Key" />
       <meta-data
           android:name="com.microsoft.engagementinsights.autoCapture"
           android:value="true" />
   ...
   </application>
   ```

1. Engedélyezi vagy letiltja a `View` események automatikus rögzítését a felül található `autoCapture` mező `true` vagy `false` -ra állításával.

1. (Nem kötelező) Az egyéb beállítások közé tartozik a végpont URL-címének beállítása. Az ingestion kulcs metaadatai között lehet hozzáadni `AndroidManifest.xml`-ben:
    ```xml
        <meta-data
            android:name="com.microsoft.engagementinsights.endpointUrl"
            android:value="https://some-endpoint-url.com" />
    ```

## <a name="step-3-initialize-the-sdk-from-mainactivity"></a>3. lépés Az SDK inicializálása a MainActivity-ről 

Az SDK inicializálása után az eseményekkel és azok tulajdonságaival is dolgozhat a MainActivity környezetben.

    
Java:
```java
Analytics analytics = new Analytics();
```

Kotlin:
```kotlin
var analytics = Analytics()
```

### <a name="set-property-for-all-events-optional"></a>Tulajdonság beállítása minden eseményhez (nem kötelező)
    
Java:
```java
analytics.setProperty("year", 2021);
```

Kotlin:
```kotlin
analytics.setProperty("year", 2021)
```

A kontextusesemény-tulajdonságok esetében a következő típusok támogatottak:
- Sztring
- Dátum
- Duplaszó
- Long
- Boolean
- UUID

### <a name="track-an-event"></a>Esemény nyomon követése

Java:
```java
Event event = new Event("video");
event.setProperty("duration", 320);
event.setProperty("ad_shown", true);
analytics.trackEvent(event);
```

Kotlin:
```kotlin
var event = Event("video")
event.setProperty("duration", 320)
event.setProperty("ad_shown", true)
analytics.trackEvent(event)
```

### <a name="set-user-details-for-your-event-optional"></a>Az esemény felhasználói adatokat tartalmazó beállítása (nem kötelező)

Az SDK segítségével meghatározhatja a minden eseményhez elküldhető felhasználói adatokat. A felhasználói adatokat úgy adhatja meg, ha az `setUser(user: User)` API-t az `Analytics` szinten hívja.

Java:
```java
User user = new User();
user.setName("testuser");
user.setEmail("abc@xyz.com");
analytics.setUser(user);
```

Kotlin:
```kotlin
var user = User()
user.name = "testuser"
user.email = "abc@xyz.com"
analytics.setUser(user)
```

Az `User` adatosztály a következő sztring-tulajdonságokat tartalmazza:

- **localId**: A felhasználó helyi azonosítója.
- **authId**: A hitelesített felhasználói azonosító.
- **authType**: A felhasználói azonosítók hitelesítéséhez használt hitelesítési típus.
- **név**: A felhasználó neve.
- **e-mail**: A felhasználó e-mail-címe.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
