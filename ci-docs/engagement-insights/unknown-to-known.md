---
title: Webes események felismerése a korábban hitelesített látogatóktól, ismertként vagy ismeretlenként
description: Az ismeretlenből ismert funkció lehetővé teszi, hogy a webhelyen az eseményeket társítsa a korábban hitelesített látogatókhoz.
ms.reviewer: mhart
ms.author: mkisel
author: mkisel11
ms.date: 7/15/2021
ms.service: customer-insights
ms.subservice: engagement-insights
ms.topic: overview
ms.manager: shellyha
ms.openlocfilehash: d1bbc3315b55e2ee233dc672456e0c27e4ad0fbd5937af09cc790c96ee274000
ms.sourcegitcommit: aa0cfbf6240a9f560e3131bdec63e051a8786dd4
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/10/2021
ms.locfileid: "7036786"
---
# <a name="recognize-web-events-from-previously-authenticated-visitors"></a>Webes események felismerése a korábban hitelesített látogatóktól

[!INCLUDE [cc-beta-prerelease-disclaimer](includes/cc-beta-prerelease-disclaimer.md)]

Az ügyfélkapcsolati információk szolgáltatás **ismeretlenből ismert** funkciója lehetővé teszi események társítását egy webhelyen a korábban hitelesített látogatókhoz. Ha a szolgáltatás le van tiltva, akkor az egy korábbi látogatás során hitelesített, majd távozó felhasználók nem lesznek azonosítva, ha nem hitelesítenek újra, amikor visszatérnek. 

Például egy személy a múlt héten felkeresett egy webhelyet, bejelentkezett a webhelyen a felhasználói fiókjába, és böngészte a termékkatalógust. Az illető a következő héten visszatér, és a fiókjába való bejelentkezés nélkül további termékeket böngész. Az **ismeretlenből ismert** szolgáltatást használó webhelytulajdonos tudni fog arról, hogy az adott személy visszatérő, és hogy mit tett a webhelyen. Így pontosabb jelentéskészítésre és elemzésre van lehetőség a webhely tevékenységeivel kapcsolatban.

## <a name="enable-unknown-to-known"></a>Ismeretlenből ismert engedélyezése

A szolgáltatás engedélyezéséhez [munkaterület-adminisztrátor](user-roles.md) jogosultság szükséges. 

1. Az aktivitási információkért menjen a **Rendszergazda** > **Munkaterület** menübe. 
2. Válassza a **Beállítások** fület.
3. Az **Ismeretlenből ismert** szakaszban állítsa a kapcsolót **Engedélyezve** értékre.

![Ismeretlenből ismert engedélyezése](media/U2Ktoggle.png "Ismeretlenből ismert engedélyezése")

## <a name="adding-javascript-code-to-your-sites-tracking-snippet"></a>JavaScript-kód hozzáadása a webhely nyomkövetési kódrészletéhez

Egy webhely az alábbi JavaScript-minta segítségével rögzítheti a **felhasználói authId** az [ügyfélkapcsolati információk webes SDK](advanced-SDK-implementation.md) használatával. Ahhoz, hogy az **ismeretlenből ismert** funkció működjön, rögzítenie kell az authId azonosítót, *és* engedélyeznie kell a userMapscript:True lehetőséget a JavaScript-kódrészletben az alábbi példában látható módon.

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
},
userMapping: true
},
user:{
authId: getLoggedInUserId()*,
email: getLoggedInUserEmail()*,
authType: "MSA",
name: "Alex Jensen"
}
[…]
```

[!INCLUDE[footer-include](../includes/footer-banner.md)]
