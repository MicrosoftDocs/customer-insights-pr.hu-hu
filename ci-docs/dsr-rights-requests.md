---
title: Az adatalanyok jogainak (DSR) megfelelő kérelmek a GDPR szerint | Microsoft Docs
description: Adatalanyi kérelmek megválaszolása a Dynamics 365 Customer Insights megoldásban.
ms.date: 08/11/2021
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: wimohabb
manager: shellyha
ms.openlocfilehash: af2583295627f98e980adbca4f216b9c34c3cad8
ms.sourcegitcommit: bf65bc0a54cdab71680e658e1617bee7b2c2bb68
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/27/2022
ms.locfileid: "8808564"
---
# <a name="data-subject-rights-dsr-requests-under-gdpr"></a>Az adatalanyok jogainak (DSR) megfelelő kérelmek a GDPR szerint

Az Európai Tanács általános adatvédelmi szabályozása (GDPR) 2018. május 25. óta van hatályba. Az adatokkal kapcsolatban jelentős jogokat biztosít az egyének számára. A GDPR az egyének személyes adatainak védelme érdekében született. A Microsoft biztonsági és megfelelési helyzetére vonatkozó további tudnivalókat a [Microsoft biztonsági központban](https://www.microsoft.com/trust-center) olvashatja.

Eltökélt célunk, hogy segítünk ügyfeleinknek megfelelni a GDPR követelményeinek. Magában foglalja a személyes adatokat (például felhasználói azonosítókat, telefonszámokat és e-mail címeket) tartalmazó adatok törlésére és exportálására vonatkozó jogokat. A rendszergazdák a személyes adatok törlésére vagy exportálására vonatkozó felhasználói kérelmeket hajthatják végre.

## <a name="dynamics-365-customer-insights"></a>Dynamics 365 Customer Insights

### <a name="responding-to-gdpr-data-subject-delete-requests-for-dynamics-365-customer-insights"></a>GDPR szerinti Adatalanyi kérelmek megválaszolása a Dynamics 365 Customer Insights megoldásban

A személyes adatoknak a szervezet ügyféladatok közüli törléséhez való jog kulcsfontosságú védelmi elem az Általános adatvédelmi rendeletben (GDPR). A személyes adatok eltávolítása magába foglalja az összes személyes adat és a rendszer által létrehozott naplók eltávolítását, kivéve az auditnaplózási információkat.

#### <a name="manage-data-subject-delete-requests"></a>Az adatalanyok törlési kérelmeinek kezelése

A Customer Insights a következő terméken belüli élményeket kínálja egy adott ügyfél vagy felhasználó személyes adatainak törléséhez:

- **Ügyféladatok törlési kérelmeinek kezelése**: A Customer Insights ügyféladatait a Customer Insights megoldáson kívüli adatforrásokból lettek betöltve. Minden GDPR szerinti törlési kérelmet az eredeti adatforráson kell végrehajtani.
- **Törlési kérelmek kezelése a Customer Insights felhasználói adatokhoz**: Customer Insights által felhasználókhoz létrehozott adatok. Minden GDPR szerinti törlési kérelmet a Customer Insights megoldásban kell elvégezni.

##### <a name="manage-requests-to-delete-customer-data"></a>Ügyféladatok törlési kérelmeinek kezelése

A Customer Insights rendszergazdák az alábbi lépések végrehajtásával eltávolíthatják az adatforrásban törölt ügyféladatokat:

1. Jelentkezzen be a Dynamics 365 Customer Insights rendszerbe.
2. Ugrás az **Adatforrásokra** > **·**
3. A törölt ügyféladatokat tartalmazó minden egyes adatforráshoz a listából:
   1. Jelölje ki a függőleges ellipszis () elemet,&vellip; majd válassza a Frissítés **lehetőséget**.
   2. Ellenőrizze az adatforrás állapotát az **Állapot** alatt. A pipa azt jelenti, hogy a frissítés sikeresen megtörtént. A figyelmeztető háromszög azt jelenti, hogy valamilyen hiba történt. Ha egy figyelmeztető háromszög jelenik meg, forduljon ide: D365CI@microsoft.com.

> [!div class="mx-imgBorder"]
> ![Ügyféladatok GDPR törlési kérelmeinek kezelése.](media/gdpr-data-sources.png "Ügyféladatok GDPR törlési kérelmeinek kezelése")

##### <a name="manage-delete-requests-for-user-data"></a>Felhasználói adatok törlési kérelmeinek kezelése

Egy Customer Insights rendszergazda a Customer Insights ügyféladatok törlését az alábbi lépésekkel hajthatja végre:

1. Jelentkezzen be a Dynamics 365 Customer Insights rendszerbe.
2. Nyissa meg a **Felügyeleti** > **biztonsági** > **engedélyek lehetőséget**.
3. Jelölje be a törölni kívánt felhasznáó jelölőnégyzetét.
4. Válassza az **Eltávolítás** lehetőséget.

### <a name="responding-to-gdpr-data-subject-export-requests"></a>GDPR szerinti Adatalanyi exportálási kérelmek megválaszolása

Az általános adatvédelmi rendelethez (GDPR) való utazás során az Önnel való partneri együttműködésünk részeként dokumentációt dolgoztunk ki, amely segít önnek válaszolni az érintettek kéréseire.

#### <a name="manage-export-and-view-requests"></a>Az exportálási és a megtekintési kérelmek kezelése

Az adathordozhatósági jog lehetővé teszi, hogy az adatalanyok személyes adataik másolatát elektronikus formátumban („strukturált, általánosan használt, géppel olvasható és interoperábilis formátumként”) formátumban elkérjék, amely átvihető másik adatkezelőhöz.

##### <a name="export-customer-data-tenant-admin"></a>Ügyféladatok exportálása (bérlői adminisztrátor)

Az adatok exportálásához a bérlői rendszergazda a következő lépéseket hajthatja végre:

1. E-mailben elküldhet egy kérelmet az ügyfél e-mail címének meghatározásával a D365CI@microsoft.com címre. A Customer Insights csoport egy adminisztrátora e-mailt küld a regisztrált bérlői rendszergazdai e-mail címre, amelyben megerősítést kér az adatok exportálása céljából.
2. Nyugtázza a kért ügyfél adatainak exportálását.
3. Az exportált adatok a bérlői rendszergazdai e-mail címen keresztül fogadhatók.

##### <a name="export-user-data-tenant-admin"></a>Felhasználói adatok exportálása (bérlői adminisztrátor)

1. E-mailben elküldhet egy kérelmet a felhasználó e-mail címének meghatározásával a D365CI@microsoft.com címre. A Customer Insights csoport egy adminisztrátora e-mailt küld a regisztrált bérlői rendszergazdai e-mail címre, amelyben megerősítést kér az adatok exportálása céljából.
2. Nyugtázza a felhasználó adatainak exportálását.
3. Az exportált adatok a bérlői rendszergazdai e-mail címen keresztül fogadhatók.

## <a name="consent-management-preview"></a>Hozzájárulás kezelése (előzetes verzió)

A hozzájáruláskezelési képesség nem gyűjt közvetlenül felhasználói adatokat. Csak olyan hozzájárulási adatokat importál és dolgoz fel, amelyeket a felhasználók más alkalmazásokban adnak meg.

Az adott felhasználókra vonatkozó hozzájárulási adatok eltávolításához távolítsa el azokat a hozzájáruláskezelési képességhez betöltött adatforrásokban. A adatforrás frissítése után az eltávolított adatok a Hozzájárulási központban is törlődnek. A beleegyezési entitást használó alkalmazások a frissítés után [a forráson eltávolított adatokat is törlik](system.md#refresh-processes). Javasoljuk, hogy az adatforrások gyors frissítése után gyorsan frissüljön, miután válaszolt az érintett kérésére, hogy eltávolítsa a felhasználó adatait az összes többi folyamatból és alkalmazásból.

[!INCLUDE [footer-include](includes/footer-banner.md)]