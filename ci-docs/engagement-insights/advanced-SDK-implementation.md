---
title: Speciális SDK forgatókönyvek
description: Speciális forgatókönyvek, amelyek figyelembe vehetőek a webhely egy SDK eszközzel való instrumentálásakor.
author: britl
ms.reviewer: mhart
ms.author: britl
ms.date: 09/27/2021
ms.subservice: engagement-insights
ms.topic: conceptual
ms.manager: shellyha
ms.openlocfilehash: a083d8215f295af0884257a016b62b8c7e4ab2c7
ms.sourcegitcommit: e7cdf36a78a2b1dd2850183224d39c8dde46b26f
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/16/2022
ms.locfileid: "8227201"
---
# <a name="advanced-web-sdk-instrumentation"></a>Speciális webes SDK-eszközök

[!INCLUDE [cc-beta-prerelease-disclaimer](includes/cc-beta-prerelease-disclaimer.md)]

Ez a cikk végigvezeti Önt a fejlett forgatókönyveken, amelyeket figyelembe kell vennie, amikor [instrumentálja weboldalát](instrument-website.md) egy Dynamics 365 Customer Insights elkötelezettségi betekintési képesség SDK-val.

## <a name="setting-user-details-for-your-event"></a>Az esemény felhasználói adatokat tartalmazó beállítása

Az SDK segítségével meghatározhatja a minden eseményhez elküldhető felhasználói adatokat. A felhasználó adatait egy `user` nevű tulajdonságban adhatja meg (ennek a tulajdonságnak az elvárt adatai a `IUser` objektum), hasonlóan a `src`, `name` és `cfg` objektumokhoz a kódrészlet konfigurációjában.

Az `IUser` objektum a következő karakterlánc-tulajdonságokat tartalmazza:

- **localId**: A felhasználó helyi azonosítója.
- **authId**: A hitelesített felhasználói azonosító.
- **authType**: A hitelesített felhasználói azonosító bekért hitelesítési típusa.
- **név**: A felhasználó neve.
- **e-mail**: A felhasználó e-mail-címe.

A következő példa egy felhasználói információkat küldő kódrészletet mutat be. Ahol a funkciókat csillag * szimbólum előzi meg, cserélje le a függvényt az egyéni implementációra:

```
[…]
window, document
{
    src:"https://download.pi.dynamics.com/sdk/web/msei-1.min.js",
    name:"myproject",
    cfg:{
      ingestionKey:<paste your ingestion key>",
      autoCapture:{
        view:true,
        click:true
      }
    },
    user:{
      authId: getLoggedInUserId()*,
      email: getLoggedInUserEmail()*,
      authType: "MSA",
      name: "John Doe"
    }
[…]
```

A felhasználói adatokat a `setUser(user: IUser)` API meghívásával is megadhatja. A `setUser` API meghívása után küldött telemetria tartalmazza a felhasználói adatokat.

## <a name="adding-custom-properties-for-each-event"></a>Egyéni tulajdonságok hozzáadása minden eseményhez

Az SDK lehetővé teszi az egyéni tulajdonságok megadását, amelyek minden eseményhez elküldhetők. Az egyéni tulajdonságokat kulcs-érték párokat tartalmazó objektumként adhatja meg (az érték lehet `string | number | boolean` típusú). Az objektumot hozzáadhatja egy `props` nevű tulajdonsághoz, amely hasonlít az `src`, `name` és `cfg` tulajdonsághoz a kódrészlet konfigurációjában.

A következő példa az egyéni tulajdonságokat küldő kódrészletet mutat be:

```
[…]
window, document
{
    src:"https://download.pi.dynamics.com/sdk/web/msei-1.min.js",
    name:"myproject",
    cfg:{
      ingestionKey:<paste your ingestion key>",
      autoCapture:{
        view:true,
        click:true
      }
    },
    props:{
      "key_name_string": "value",
      "key_name_number": 10,
      "key_name_bool": true
    }
[…]
```

Az egyéni tulajdonságokat külön külön, a `setProperty(name: string, value: string | number | boolean)` API meghívásával is megadhatja.

## <a name="sending-custom-events"></a>Egyéni események küldése

Az SDK segítségével egyéni eseményeket küldhet. Meg kell adnia az esemény nevét és az eseményhez küldendő tulajdonságokat.

A következő példa az egyéni eseményt nyomon követő kódrészletet mutat be: A "NÉV" a `name` kulcsban megadott érték a kódrészlet értéke. Szintén ez a változó neve annak az ablaknak az objektumában, ahol az SDK betöltődik.

```
window["NAME"].trackEvent({
    name: "event_name",
    properties: {
        "duration": 320,
        "name": "getting_started",
        "ad_shown": true
    }
});
```


[!INCLUDE[footer-include](../includes/footer-banner.md)]
