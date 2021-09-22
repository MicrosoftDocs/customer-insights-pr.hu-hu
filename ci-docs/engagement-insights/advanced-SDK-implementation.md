---
title: Speciális SDK forgatókönyvek
description: Speciális forgatókönyvek, amelyek figyelembe vehetőek a webhely egy SDK eszközzel való instrumentálásakor.
author: britl
ms.reviewer: mhart
ms.author: britl
ms.date: 11/12/2020
ms.service: customer-insights
ms.subservice: engagement-insights
ms.topic: conceptual
ms.manager: shellyha
ms.openlocfilehash: 7455d276035bfaf1f8a93d0e3b0b0884353a4010715c05d1d696309f7eb4b233
ms.sourcegitcommit: aa0cfbf6240a9f560e3131bdec63e051a8786dd4
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/10/2021
ms.locfileid: "7036331"
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
    
A következő példa egy felhasználói információkat küldő kódrészletet mutat be. Ahol a *-val megjegyzett Funkciók láthatók, helyettesítse be az értékek hívásának megvalósításával:  

```
[…]
window, document 
{
    src:"https://download.pi.dynamics.com/sdk/web/mspi-0.min.js", 
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

A felhasználói adatokat úgy is megadhatja, ha az SDK-n lehívja az `setUser(user: IUser)` API-t. A `setUser API` lehívása után küldött telemetria tartalmazza a felhasználói adatokat.

## <a name="adding-custom-properties-for-each-event"></a>Egyéni tulajdonságok hozzáadása minden eseményhez

Az SDK lehetővé teszi az egyéni tulajdonságok megadását, amelyek minden eseményhez elküldhetők. Az egyéni tulajdonságokat kulcs-érték párokat tartalmazó objektumként adhatja meg (az érték lehet `string | number | boolean` típusú). Az objektumot egy `props` nevű tulajdonságban lehet hozzáadni, hasonlóan a `src`, `name` és `cfg` tulajdonságokhoz a kódrészlet konfigurációjában. 

A következő példa az egyéni tulajdonságokat küldő kódrészletet mutat be:

```
[…]
window, document 
{
    src:"https://download.pi.dynamics.com/sdk/web/mspi-0.min.js", 
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

Egyéni tulajdonságokat egyénileg is megadhat, ha az SDK-n lehívja az `setProperty(name: string, value: string | number | boolean)` API-t.

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