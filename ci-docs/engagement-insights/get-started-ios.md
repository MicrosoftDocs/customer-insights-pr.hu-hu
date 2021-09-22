---
title: Első lépések iOS SDK-val
description: Ismerje meg az iOS SDK személyre szabását és futtatását
author: britl
ms.reviewer: mhart
ms.author: britl
ms.date: 06/23/2021
ms.service: customer-insights
ms.subservice: engagement-insights
ms.topic: conceptual
ms.manager: shellyha
ms.openlocfilehash: de8291fc429ae6433301a47bfdf9a3271b1b77294fd58448c7aa6bd0783edc97
ms.sourcegitcommit: aa0cfbf6240a9f560e3131bdec63e051a8786dd4
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/10/2021
ms.locfileid: "7036876"
---
# <a name="get-started-with-the-ios-sdk"></a>Első lépések az iOS SDK-val

[!INCLUDE [cc-beta-prerelease-disclaimer](includes/cc-beta-prerelease-disclaimer.md)]

Ez az oktatóanyag végigvezeti az iOS alkalmazás a Dynamics 365 Customer Insights elköteleződési elemzések SDK-val történő instrumentálásának folyamatán. Öt perc múlva vagy hamarabb elkezdi látni az eseményeket a portálon.

## <a name="configuration-options"></a>Konfigurációs beállítások

A következő konfigurációs beállításokat lehet átadni az SDK-nak a megadott `EIConfig.plist` fájlon keresztül:

- **ingestionKey**: Az ingestion kulcs segítségével küldhet eseményeket a projektjéhez.
- **autocollectAction**: Logikai érték a műveletesemény automatikus instrumentálásának engedélyezéséhez vagy letiltásához.
- **autocollectView**: Logikai érték a nézet-esemény automatikus instrumentálásának engedélyezéséhez vagy letiltásához.
- **endpointUrl**: A végpont URL-cím, ahová az eseményeket irányítják.

## <a name="prerequisites"></a>Előfeltételek

- Xcode verzió 9+
- iOS verzió 8.2+
- Egy ingestion kulcs (lásd lejjebb a hozzáférési útmutatót)

## <a name="integrate-the-sdk-into-your-application"></a>SDK beágyazása az alkalmazásba

Kezdje a folyamatot munkaterület kiválasztásával, az iOS mobil platform kiválasztásával és az SDK letöltésével.

- A munkaterület kijelöléséhez használja a bal oldali navigációs ablakban található munkaterület-kapcsolót.

- Ha nem rendelkezik meglévő munkaterületekkel, válassza az **Új munkaterület** és kövesse a lépéseket az [új munkaterület](create-workspace.md) létrehozásához.

## <a name="configure-the-sdk"></a>Konfigurálja az SDK-t

Miután letöltötte az SDK-t, Xcode-ban dolgozhat vele az események engedélyezéséhez és definiálásához.

1. Munkaterület létrehozása után válassza a **Rendszergazda** > **Munkaterület** majd válassza a **Telepítési útmutatót**.

1. Töltse le az [elköteleződési információk iOS SDK-t](https://download.pi.dynamics.com/sdk/EI-SDKs/ei-ios-sdk.zip), és helyezze az `EIObjC.xcframework` fájlt a `Frameworks` mappába.

1. Ha `Frameworks` egy mappa nem létezik, hozzon létre egyet a projektmappában.

## <a name="enable-auto-instrumentation"></a>Automatikus műszerezés engedélyezése
 
Kódolás nélkül egyszerűen engedélyezheti az automatikus műszerezést. Amikor a projekt fut, automatikusan nyomon követi a `view` és `action` eseményeket a konfigurált ingestion kulcs segítségével. 

1. Frissítse és foglalja be a megadott `EIConfig.plist` fájlt a projektkönyvtár mappájába a következő mezőkhöz:
    - ingestionKey = `"Your-Ingestion-Key"`
    - autocollectView = IGEN
    - autocollectAction = IGEN

2. Ezután adja hozzá a `EIConfig.plist` fájlt a projekthez az Xcode-ban. 



Az auto-instrumentáció letiltásához frissítse a következő mezőket a megadott `EIConfig.plist` fájlban a projektkönyvtár mappában. 

```objectivec
'autocollectView' = NO (to disable)
'autocollectAction' = NO (to disable)
```


## <a name="implement-custom-events"></a>Egyéni események végrehajtása

1. Nyissa meg a projektet Xcode-ban, és menjen az **Általános** beállításokhoz. 
1. Adja hozzá `EIObjC.xcframework` a projekthez a "Keretrendszerek, könyvtárak és beágyazott tartalom" szakaszban.

1. Importálja a keretrendszer fejlécfájlját az AppDelegate.m alkalmazásban a következő kódrészlettel:

    ```objectivec
    #import <EIObjC/EIObjC.h>
    ```

1. Az elköteleződési információk SDK inicializálása az alkalmazásból: didFinishLaunchingWithOptions.
1. Másolja az XML-kódrészlet a **Telepítési útmutató** -ból.

    ```objectivec
    NSError *error = [NSError new];
    id<EIIAnalytics> analytics = [EIAnalyticsProvider analyticsForIngestionKey:nil error:&error];
    ```

1. Esemény nyomon követése:

    ```objectivec
    EIEvent *event = [EIEvent new];
    event.name = @"video.log";
    [event setLongValue:320 forKey:@"duration"];
    [event setBoolValue:YES forKey:@"ad_shown"];
    [analytics trackEvent:event];
    ```

## <a name="set-user-details-for-your-event"></a>Az esemény felhasználói adatokat tartalmazó beállítása

Az SDK segítségével meghatározhatja a minden eseményhez elküldhető felhasználói adatokat. A felhasználói adatokat úgy adhatja meg, ha az SDK-n a `setUser:(nonnull EIUser *)user` API-t hívja.

A felhasználói adatok megadása a `Analytics` szinten azt jelenti, hogy minden telemetriai adat rendelkezik ezzel az információval. Ha azonban az esemény szintjén megadja a `setUser:(nonnull EIUser *)user` API hívását az EIEvent objektumon, csak az adott esemény fogja tartalmazni az információkat.

Az `EIUser` adatosztály a következő NSString tulajdonságokat tartalmazza:

- **localId**: A felhasználó helyi azonosítója.
- **authId**: A hitelesített felhasználói azonosító.
- **authType**: A hitelesített felhasználói azonosító bekért hitelesítési típusa.
- **név**: A felhasználó neve.
- **e-mail**: A felhasználó e-mail-címe.


[!INCLUDE[footer-include](../includes/footer-banner.md)]