---
title: Első lépések az Android SDK-val
description: Ismerje meg az Android SDK személyre szabását és futtatását
author: britl
ms.reviewer: mhart
ms.custom: intro-internal
ms.author: britl
ms.date: 10/19/2021
ms.service: customer-insights
ms.subservice: engagement-insights
ms.topic: conceptual
ms.manager: shellyha
ms.openlocfilehash: 71ec4841303bd17d3f605547be8d6032c58a7b21
ms.sourcegitcommit: bb1ca84bc38e81fb2ff2961c457384b7beb5b5fa
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2022
ms.locfileid: "7977578"
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

## <a name="integrate-the-sdk-into-your-application"></a>SDK beágyazása az alkalmazásba
Kezdje a folyamatot munkaterület kiválasztásával, az Android a mobil platform kiválasztásával és az Android SDK letöltésével.

- A munkaterület kijelöléséhez használja a bal oldali navigációs ablakban található munkaterület-kapcsolót.

- Ha nem rendelkezik meglévő munkaterületekkel, válassza az **Új munkaterület** és kövesse a lépéseket az [új munkaterület](create-workspace.md) létrehozásához.

- Munkaterület létrehozása után válassza a **Rendszergazda** > **Munkaterület** majd válassza a  **Telepítési útmutatót**.

## <a name="configure-the-sdk"></a>Konfigurálja az SDK-t

Miután letöltötte az SDK-t, az Android Studio-ban dolgozhat vele az események engedélyezéséhez és definiálásához. Kétféleképpen teheti ezt meg:
### <a name="option-1-use-jitpack-recommended"></a>1. lehetőség: Használja a JitPack-et (ajánlott)
1. Adja hozzá a gyökér `build.gradle`-höz a JitPack-adattár csomagot:
    ```gradle
    allprojects {
        repositories {
            ...
            maven { url 'https://jitpack.io' }
        }
    }
    ```

1. Adja hozzá a függőséget:
    ```gradle
    dependencies {
        implementation 'com.github.microsoft:engagementinsights-sdk-android:v1.0.0'
        api 'com.google.code.gson:gson:2.8.1'
    }
    ```

### <a name="option-2-use-download-link"></a>2. lehetőség: Letöltési link használata
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

## <a name="enable-auto-instrumentation"></a>Automatikus műszerezés engedélyezése

1. Adja hozzá a hálózatra és internetre vonatkozó jogosultságot a `manifests` mappa alatt található `AndroidManifest.xml` fájlban.
    ```xml
    <manifest>
        ...
        <uses-permission android:name="android.permission.INTERNET" />
        <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
    ```

1. Az elköteleződési elemzések SDK konfigurációját az `AndroidManifest.xml` fájlon keresztül.

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

   >[!NOTE]
   >`Action` az eseményeket manuálisan kell hozzáadni.

1. (Nem kötelező) Az egyéb beállítások közé tartozik a végpont URL-címének beállítása. A betöltési kulcs metaadatai alá adhatók hozzá a `AndroidManifest.xml`.

   ```xml
        <meta-data
            android:name="com.microsoft.engagementinsights.endpointUrl"
            android:value="https://some-endpoint-url.com" />
   ```

## <a name="implement-custom-events"></a>Egyéni események végrehajtása

Az SDK inicializálása után az eseményekkel és azok tulajdonságaival is dolgozhat a `MainActivity` környezetben.


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

## <a name="set-user-details-for-your-event-optional"></a>Az esemény felhasználói adatokat tartalmazó beállítása (nem kötelező)

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
