---
title: A cookie-k kezelése és a felhasználói beleegyezés a felhasználói adatok tárolására
description: A cookie-k és a felhasználó beleegyezésének használata a webhely látogatóinak azonosítására.
author: mochimochi016
ms.reviewer: mhart
ms.author: jefhar
ms.date: 10/30/2020
ms.service: customer-insights
ms.subservice: engagement-insights
ms.topic: conceptual
ms.manager: shellyha
ms.openlocfilehash: 7b3195a92c969ab36e5b43f4c2e4221ff477a0a8958838e1256528f58fe13dce
ms.sourcegitcommit: aa0cfbf6240a9f560e3131bdec63e051a8786dd4
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/10/2021
ms.locfileid: "7036741"
---
# <a name="manage-cookies-and-user-consent"></a>Cookie-k és felhasználói hozzájárulások kezelése

[!INCLUDE [cc-beta-prerelease-disclaimer](includes/cc-beta-prerelease-disclaimer.md)]

Az Dynamics 365 Customer Insights aktivitási információk képesség cookie-kat és helyi tárolást (`localStorage`) alkalmaz a weboldal látogatóinak azonosítására.

A cookie-k kisméretű fájlok, amelyek a felhasználó webhellyel való kapcsolati tevékenységére vonatkozó információkat tárolják. A fájlok webböngészőkben tárolódnak. Amikor a felhasználó meglátogat egy webhelyet, ahol a felhasználók cookie-kat tároltak, a böngésző elküldi ezeket az információkat a kiszolgálónak, ami egyedi információkat ad eredményül a felhasználónak. Ez az a technológia, amely lehetővé teszi például, hogy egy online áruházban akkor is megtartsa a kijelölt elemeket, ha egy felhasználó eligazodik a webhelyről.

## <a name="user-consent"></a>Felhasználói hozzájárulás

Az [általános adatvédelmi rendelet (GDPR)](/dynamics365/get-started/gdpr/) az Európai Unió (EU) rendelete, amely előírja, hogy a szervezeteknek hogyan kell kezelniük a felhasználók adatvédelmét és biztonságát. A cookie-k gyakran "személyes adatokat" tárolnak vagy gyűjtenek, például egy online azonosítót, amelyre a GDPR kiterjed. Ha az Ön vállalkozása EU-s adatalanyokat foglalkoztat és/vagy azok számára értékesít, a GDPR vonatkozik Önre. [További információk arról, hogyan tud segítséget kérni a Microsofttól a GDPR-nak való megfelelésben](https://www.microsoft.com/trust-center/privacy/gdpr-faqs).

Ahhoz, hogy az aktivitási információk SDK cookie-kat vagy más bizalmas adatokat tárolhassanak, meg kell adnia, hogy a felhasználók beleegyeztek-e. Ez az SDK inicializációja esetén fordul elő.

Ha azt jelzi, hogy nincs felhasználói beleegyezés, az SDK nem tárol semmilyen adatot, és nem küld olyan eseményeket, amelyek a felhasználói viselkedés nyomon követésére használhatók. A korábban tárolt adatokat a rendszer törli a böngészőből.

Ha nincs megadva a felhasználói beleegyezés értéke, az SDK azt feltételezi, hogy a felhasználó beleegyezését adta. Ez azt jelenti, hogy ha Ön (az ügyfélként) nem adja meg a felhasználói beleegyezés értékét az SDK-ban, akkor adatokat gyűjtünk. Ha viszont azt adja meg, hogy a felhasználó beleegyezésének értéke "igaz" legyen, a rendszer nem gyűjt adatokat, ha a felhasználó elutasítja vagy nem adja meg a kifejezett beleegyezését.

## <a name="visitor-data-storage-in-engagement-insights-capability"></a>A látogatók adatainak tárolása az aktivitási információk szolgáltatásban

### <a name="cookies"></a>Cookies

- _msei
    - Tárolja a névtelen felhasználói azonosítót. Ez a cookie az ügyfél tartományában van beállítva, és 365 napon belül lejár.

### <a name="local-storage"></a>Helyi tárterület

Az aktivitási információk szolgáltatás a helyi tárolást (`localStorage`) is használja a nem bizalmas adatok nyomon követésére. Ezek az adatok teljes mértékben a böngészőben tárolódnak, így a kiszolgálói nem bonyolítanak forgalmat.

- *EISession.Id* 
    - A folyamatban lévő felhasználói munkamenet adatait, például a munkamenet-azonosítót, illetve annak kezdő időpontját és lejáratát tárolja.
- *EISession.Previous*
    - Az aktuális munkamenetben tárolja a korábban felkeresett oldal URL-címét.
    
A helyi tárolóban található kulcsok nem járnak le automatikusan. Az SDK a következő munkamenet során alaphelyzetbe állítja őket.

## <a name="deleting-cookies"></a>Cookie-k törlése

Az ügyfelei a böngésző beállításain keresztül bármikor törölhetik manuálisan a cookie-kat és a helyi tárolókulcsokat.


[!INCLUDE[footer-include](../includes/footer-banner.md)]