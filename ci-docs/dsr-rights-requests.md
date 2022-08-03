---
title: Az adatalanyok jogainak (DSR) megfelelő kérelmek a GDPR szerint | Microsoft Docs
description: Adatalanyi kérelmek megválaszolása a Dynamics 365 Customer Insights megoldásban.
ms.date: 05/23/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: wimohabb
manager: shellyha
ms.openlocfilehash: 6c6ce49c18de3a09d28138316d893e6842919042
ms.sourcegitcommit: ff0f4b5664d995870c91adb87c7d3780a582efca
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/13/2022
ms.locfileid: "9146698"
---
# <a name="data-subject-rights-dsr-requests-under-gdpr"></a>Az adatalanyok jogainak (DSR) megfelelő kérelmek a GDPR szerint

Az Európai Tanács általános adatvédelmi szabályozása (GDPR) 2018. május 25. óta van hatályba. Az adatokkal kapcsolatban jelentős jogokat biztosít az egyének számára. A GDPR az egyének személyes adatainak védelme érdekében született. A Microsoft biztonsági és megfelelési helyzetére vonatkozó további tudnivalókat a [Microsoft biztonsági központban](https://www.microsoft.com/trust-center) olvashatja.

Eltökélt célunk, hogy segítünk ügyfeleinknek megfelelni a GDPR követelményeinek. Magában foglalja a személyes adatokat (például felhasználói azonosítókat, telefonszámokat és e-mail címeket) tartalmazó adatok törlésére és exportálására vonatkozó jogokat. A rendszergazdák a személyes adatok törlésére vagy exportálására vonatkozó felhasználói kérelmeket hajthatják végre.

## <a name="dynamics-365-customer-insights"></a>Dynamics 365 Customer Insights

### <a name="responding-to-gdpr-data-subject-delete-requests-for-dynamics-365-customer-insights"></a>GDPR szerinti Adatalanyi kérelmek megválaszolása a Dynamics 365 Customer Insights megoldásban

A személyes adatoknak a szervezet ügyféladatok közüli törléséhez való jog kulcsfontosságú védelmi elem az Általános adatvédelmi rendeletben (GDPR). A személyes adatok eltávolítása magába foglalja az összes személyes adat és a rendszer által létrehozott naplók eltávolítását, kivéve az auditnaplózási információkat.

#### <a name="manage-data-subject-delete-requests"></a>Az adatalanyok törlési kérelmeinek kezelése

A Customer Insights a következő terméken belüli élményeket kínálja egy adott ügyfél vagy felhasználó személyes adatainak törléséhez:

- **Ügyféladatok törlési kérelmeinek kezelése**: A Customer Insights ügyféladatait a Customer Insights megoldáson kívüli adatforrásokból lettek betöltve. Először hajtsa végre a GDPR törlési kérelmeit az eredeti adatforrás.
- **Törlési kérelmek kezelése a Customer Insights felhasználói adatokhoz**: Customer Insights által felhasználókhoz létrehozott adatok. Minden GDPR szerinti törlési kérelmet a Customer Insights megoldásban kell elvégezni.

##### <a name="manage-requests-to-delete-customer-data"></a>Ügyféladatok törlési kérelmeinek kezelése

A Customer Insights-rendszergazdák az alábbi lépéseket követve távolíthatják el a adatforrás törölt ügyféladatokat. Győződjön meg arról, hogy a törlési kérelem a adatforrás történt, mielőtt folytatná az alább felsorolt lépéseket. 

1. Jelentkezzen be a Dynamics 365 Customer Insights rendszerbe.
1. Ugrás az **Adatforrások** > **oldalra**
1. A törölt ügyféladatokat tartalmazó minden egyes adatforráshoz a listából:
   1. Válassza ki a függőleges három pontot (&vellip;), majd válassza a Frissítés **lehetőséget**.
   1. Ellenőrizze az adatforrás állapotát az **Állapot** alatt. A pipa azt jelenti, hogy a frissítés sikeresen megtörtént. A figyelmeztető háromszög azt jelenti, hogy valamilyen hiba történt. Ha egy figyelmeztető háromszög jelenik meg, forduljon ide: D365CI@microsoft.com.
1. A sikeres adatforrás-frissítés után futtassa az alsóbb rétegbeli frissítéseket is. Különösen akkor, ha nincs ütemezve a Customer Insights ismétlődő teljes frissítése. 

> [!IMPORTANT]
> A statikus szegmensek nem szerepelnek a teljes frissítésben vagy a törlési kérelem utáni lefelé irányuló frissítések futtatásában. Annak érdekében, hogy az ügyféladatok is el legyen távolítva a statikus szegmensekből, hozza létre újra a statikus szegmenseket a frissített forrásadatokkal.

> [!div class="mx-imgBorder"]
> ![Ügyféladatok GDPR törlési kérelmeinek kezelése.](media/gdpr-data-sources.png "Ügyféladatok GDPR törlési kérelmeinek kezelése")

##### <a name="manage-delete-requests-for-user-data"></a>Felhasználói adatok törlési kérelmeinek kezelése

Egy Customer Insights rendszergazda a Customer Insights ügyféladatok törlését az alábbi lépésekkel hajthatja végre:

1. Jelentkezzen be a Dynamics 365 Customer Insights rendszerbe.
2. Lépjen a **Rendszergazdai** > **biztonsági** > **engedélyek elemre**.
3. Jelölje be a törölni kívánt felhasznáó jelölőnégyzetét.
4. Válassza az **Eltávolítás** lehetőséget.

### <a name="responding-to-gdpr-data-subject-export-requests"></a>GDPR szerinti Adatalanyi exportálási kérelmek megválaszolása

Azon elkötelezettségünk részeként, hogy együttműködjünk Önnel az általános adatvédelmi rendelet (GDPR) felé vezető úton, olyan dokumentációt dolgoztunk ki, amely segít önnek válaszolni az érintettek kéréseire.

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

### <a name="data-deletion-handling-in-dynamics-365-customer-insights"></a>Adattörlések kezelése a Dynamics 365 Customer Insights

1. Az adatok (adatpartíciók és adat-pillanatképek) törlődnek, ha az adatpartíciók és az adat-pillanatképek több mint 30 napig inaktívak, ami azt jelenti, hogy egy új adatpartíció és pillanatkép váltotta fel őket az adatforrások frissítése révén.
2. Nem minden adat és pillanatkép törlődik. A legutóbbi adatpartíció és adat-pillanatkép definíció szerint aktív, mert a Customer Insights szolgáltatásban használják őket. A legfrissebb adatok esetében nem számít, hogy az adatforrások nem frissültek-e az elmúlt 30 napban.

[!INCLUDE [footer-include](includes/footer-banner.md)]
