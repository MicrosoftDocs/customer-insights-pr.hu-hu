---
title: A cookie-k és a felhasználói beleegyezés kezelése a felhasználói adatoknak a Dynamics 365 Customer Insights-ban való tárolására
description: A cookie-k és a felhasználó beleegyezésének használata a webhely látogatóinak azonosítására.
author: mochimochi016
ms.reviewer: mhart
ms.author: jefhar
ms.date: 09/27/2021
ms.service: customer-insights
ms.subservice: engagement-insights
ms.topic: conceptual
ms.manager: shellyha
ms.openlocfilehash: c824e50b723fe7f3b421048bb6ab96b7a9efc31f
ms.sourcegitcommit: f1e3cc51ea4cf68210eaf0210ad6e14b15ac4fe8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/27/2021
ms.locfileid: "7558874"
---
# <a name="manage-cookies-and-user-consent"></a>Cookie-k és felhasználói hozzájárulások kezelése

[!INCLUDE [cc-beta-prerelease-disclaimer](includes/cc-beta-prerelease-disclaimer.md)]

A Dynamics 365 Customer Insights elkötelezettségi információk szolgáltatás cookie-k és (`localStorage`) kulcsok segítségével azonosítja a webhely látogatóit.

A cookie-k kisméretű fájlok, amelyek a felhasználó webhellyel való kapcsolati tevékenységére vonatkozó információkat tárolják. A fájlok webböngészőkben tárolódnak. Amikor a felhasználó meglátogat egy webhelyet, ahol a felhasználók cookie-kat tároltak, a böngésző elküldi ezeket az információkat a kiszolgálónak, ami egyedi információkat ad eredményül a felhasználónak. Ez az a technológia, amely lehetővé teszi például, hogy egy online áruházban akkor is megtartsa a kijelölt elemeket, ha egy felhasználó eligazodik a webhelyről.

## <a name="user-consent"></a>Felhasználói hozzájárulás

Az [általános adatvédelmi rendelet (GDPR)](/dynamics365/get-started/gdpr/) az Európai Unió (EU) rendelete, amely előírja, hogy a szervezeteknek hogyan kell kezelniük a felhasználók adatvédelmét és biztonságát. A cookie-k gyakran "személyes adatokat" tárolnak vagy gyűjtenek, például egy online azonosítót, amelyre a GDPR kiterjed. Ha az Ön vállalkozása EU-s adatalanyokat foglalkoztat és/vagy azok számára értékesít, a GDPR vonatkozik Önre. [További információk arról, hogyan tud segítséget kérni a Microsofttól a GDPR-nak való megfelelésben](https://www.microsoft.com/trust-center/privacy/gdpr-faqs).

Ahhoz, hogy az aktivitási információk SDK cookie-kat vagy más bizalmas adatokat tárolhassanak, meg kell adnia, hogy a felhasználók beleegyeztek-e. Ez az SDK inicializálása során történik elő a konfigurációban egy `userConsent` mező beállításával.

Ha azt jelzi, hogy nincs felhasználói beleegyezés, az SDK nem tárol semmilyen adatot, és nem küld olyan eseményeket, amelyek a felhasználói viselkedés nyomon követésére használhatók. A korábban tárolt adatokat a rendszer törli a böngészőből.

Ha nincs megadva a felhasználói beleegyezés értéke, az SDK azt feltételezi, hogy a felhasználó beleegyezését adta. Ez azt jelenti, hogy ha Ön (az ügyfélként) nem adja meg a felhasználói beleegyezés értékét az SDK-ban, akkor adatokat gyűjtünk. Ha viszont azt adja meg, hogy a felhasználó beleegyezésének értéke "igaz" legyen, a rendszer nem gyűjt adatokat, ha a felhasználó elutasítja vagy nem adja meg a kifejezett beleegyezését.

Az alábbiakban egy kódrészlet található, amely inicializálja a webes SDK-t a felhasználói tartalommal:
```js
<script>
  (function(a,t,i){var e="MSEI";var s="Analytics";var o=e+"queue";a[o]=a[o]||[];var r=a[e]||function(n){var t={};t[s]={};function e(e){while(e.length){var r=e.pop();t[s][r]=function(e){return function(){a[o].push([e,n,arguments])}}(r)}}var r="track";var i="set";e([r+"Event",r+"View",r+"Action",i+"Property",i+"User","initialize","teardown"]);return t}(i.name);var n=i.name;if(!a[e]){a[n]=r[s];a[o].push(["new",n]);setTimeout(function(){var e="script";var r=t.createElement(e);r.async=1;r.src=i.src;var n=t.getElementsByTagName(e)[0];n.parentNode.insertBefore(r,n)},1)}else{a[n]=new r[s]}if(i.user){a[n].setUser(i.user)}if(i.props){for(var c in i.props){a[n].setProperty(c,i.props[c])}}a[n].initialize(i.cfg)})(window,document,{
    src:"https://download.pi.dynamics.com/sdk/web/msei-1.min.js",
    name:"EiJS",
    cfg:{
      ingestionKey:"YOUR-INGESTIONKEY",
      autoCapture:{
        view:true,
        click:true
      },
      userConsent: true
    }
  });
</script>
```

## <a name="visitor-data-storage-in-engagement-insights-capability"></a>A látogatók adatainak tárolása az aktivitási információk szolgáltatásban

### <a name="cookies"></a>Cookie-k

- _msei
    - Tárolja a névtelen felhasználói azonosítót. Ez a cookie az ügyfél tartományában van beállítva, és 365 napon belül lejár.

### <a name="local-storage"></a>Helyi tárterület

Az Elkötelezettségi információk képesség a (`localStorage`) kulcsokat is használja a nem bizalmas adatok nyomon követéséhez. Ezek az adatok teljes mértékben a böngészőben tárolódnak, így a kiszolgálói nem bonyolítanak forgalmat.

- *EISession.Id*
    - A folyamatban lévő felhasználói munkamenet adatait, például a munkamenet-azonosítót, illetve annak kezdő időpontját és lejáratát tárolja.
- *EISession.Previous*
    - Az aktuális munkamenetben tárolja a korábban felkeresett oldal URL-címét.

A helyi tárolóban található kulcsok nem járnak le automatikusan, és a következő SDK munkamenet során alaphelyzetbe kerülnek.

## <a name="deleting-cookies"></a>Cookie-k törlése

Az ügyfelei a böngésző beállításain keresztül bármikor törölhetik manuálisan a cookie-kat és a helyi tárolókulcsokat.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
