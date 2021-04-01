---
title: Az adatalanyok jogainak (DSR) megfelelő kérelmek a GDPR szerint | Microsoft Docs
description: Adatalanyi kérelmekre adott válasz a Dynamics 365 Customer Insights célközönség-információ funkciójához.
ms.date: 05/14/2020
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: wimohabb
manager: shellyha
ms.openlocfilehash: 9c453c9b416bff0e6362a8ccf7ff534f4efa1e00
ms.sourcegitcommit: bae40184312ab27b95c140a044875c2daea37951
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/15/2021
ms.locfileid: "5597514"
---
# <a name="data-subject-rights-dsr-requests-under-gdpr"></a>Az adatalanyok jogainak (DSR) megfelelő kérelmek a GDPR szerint

## <a name="responding-to-gdpr-data-subject-delete-requests-for-dynamics-365-customer-insights-audience-insights-capability"></a>GDPR adatalanyi törlési kérelmekre adott válasz a Dynamics 365 Customer Insights célközönség-információ funkciójához

A személyes adatoknak a szervezet ügyféladatok közüli törléséhez való jog kulcsfontosságú védelmi elem az Általános adatvédelmi rendeletben (GDPR). A személyes adatok eltávolítása magába foglalja az összes személyes adat és a rendszer által létrehozott naplók eltávolítását, kivéve az auditnaplózási információkat.

### <a name="manage-data-subject-delete-requests"></a>Az adatalanyok törlési kérelmeinek kezelése

A célközönség-információk a következő termékeken belüli élményeket kínálja egy adott ügyfél vagy felhasználó személyes adatainak törléséhez:

- **Ügyféladatok törlési kérelmeinek kezelése**: A Customer Insights ügyféladatait a Customer Insights megoldáson kívüli adatforrásokból lettek betöltve. Minden GDPR szerinti törlési kérelmet az eredeti adatforráson kell végrehajtani.
- **Törlési kérelmek kezelése a Customer Insights felhasználói adatokhoz**: Customer Insights által felhasználókhoz létrehozott adatok. Minden GDPR szerinti törlési kérelmet a Customer Insights megoldásban kell elvégezni.

#### <a name="manage-delete-requests-for-customer-data"></a>Ügyféladatok törlési kérelmeinek kezelése

A Customer Insights rendszergazdák az alábbi lépések végrehajtásával eltávolíthatják az adatforrásban törölt ügyféladatokat:

1. Jelentkezzen be a Dynamics 365 Customer Insights rendszerbe.
2. A célközönség információin belül nyissa meg a következőt **Adatok** > **Adatforrások**
3. A törölt ügyféladatokat tartalmazó minden egyes adatforráshoz a listából:
   1. Válassza a (...), majd a **Frissítés** lehetőséget.
   2. Ellenőrizze az adatforrás állapotát az **Állapot** alatt. A pipa azt jelenti, hogy a frissítés sikeresen megtörtént. A figyelmeztető háromszög azt jelenti, hogy valamilyen hiba történt. Ha egy figyelmeztető háromszög jelenik meg, forduljon ide: D365CI@microsoft.com.

> [!div class="mx-imgBorder"]
> ![Ügyféladatok GDPR törlési kérelmeinek kezelése](media/gdpr-data-sources.png "Ügyféladatok GDPR törlési kérelmeinek kezelése")

#### <a name="manage-delete-requests-for-user-data"></a>Felhasználói adatok törlési kérelmeinek kezelése

Egy Customer Insights rendszergazda a Customer Insights ügyféladatok törlését az alábbi lépésekkel hajthatja végre:

1. Jelentkezzen be a Dynamics 365 Customer Insights rendszerbe.
2. A célközönség információin belül nyissa meg a következőt **Rendszergazda** > **Engedélyek**.
3. Jelölje be a törölni kívánt felhasznáó jelölőnégyzetét.
4. Válassza az **Eltávolítás** lehetőséget.

> [!div class="mx-imgBorder"]
> ![GDPR felhasználói adatokra vonatkozó törlési kérelmeinek kezelése](media/gdpr-permissions.png "GDPR felhasználói adatokra vonatkozó törlési kérelmeinek kezelése")

## <a name="responding-to-gdpr-data-subject-export-requests"></a>GDPR szerinti Adatalanyi exportálási kérelmek megválaszolása

Az Általános adatvédelmi rendelet (GDPR) világában való eligazodás során az Önnel folytatott partneri elkötelezettség részeként egy előkészületeket elősegítő dokumentációt fejlesztettünk ki. Ez a dokumentáció ismerteti azokat a lépéseket, amelyeket ma a GDPR-megfelelőség támogatásához megtehet a célközönség-információk használatával.

### <a name="manage-export-and-view-requests"></a>Az exportálási és a megtekintési kérelmek kezelése

Az adathordozhatósági jog lehetővé teszi, hogy az adatalanyok személyes adataik másolatát elektronikus formátumban („strukturált, általánosan használt, géppel olvasható és interoperábilis formátumként”) formátumban elkérjék, amely átvihető másik adatkezelőhöz.

#### <a name="export-customer-data-tenant-admin"></a>Ügyféladatok exportálása (bérlői adminisztrátor)

Az adatok exportálásához a bérlői rendszergazda a következő lépéseket hajthatja végre:

1. E-mailben elküldhet egy kérelmet az ügyfél e-mail címének meghatározásával a D365CI@microsoft.com címre. A Customer Insights csoport egy adminisztrátora e-mailt küld a regisztrált bérlői rendszergazdai e-mail címre, amelyben megerősítést kér az adatok exportálása céljából.
2. Nyugtázza a kért ügyfél adatainak exportálását.
3. Az exportált adatok a bérlői rendszergazdai e-mail címen keresztül fogadhatók.

#### <a name="export-user-data-tenant-admin"></a>Felhasználói adatok exportálása (bérlői adminisztrátor)

1. E-mailben elküldhet egy kérelmet a felhasználó e-mail címének meghatározásával a D365CI@microsoft.com címre. A Customer Insights csoport egy adminisztrátora e-mailt küld a regisztrált bérlői rendszergazdai e-mail címre, amelyben megerősítést kér az adatok exportálása céljából.
2. Nyugtázza a felhasználó adatainak exportálását.
3. Az exportált adatok a bérlői rendszergazdai e-mail címen keresztül fogadhatók.


[!INCLUDE[footer-include](../includes/footer-banner.md)]