---
title: Az adatalanyok jogainak (DSR) megfelelő kérelmek a GDPR szerint | Microsoft Docs
description: Adatalanyi kérelmek megválaszolása a Dynamics 365 Customer Insights megoldásban.
ms.date: 08/31/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: wimohabb
manager: shellyha
ms.openlocfilehash: 49251fb46957c4d7ec205b93c9547a3cd380eb11
ms.sourcegitcommit: 624b27bb65a0de1970dc1ac436643b493f0a31cf
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/31/2022
ms.locfileid: "9387114"
---
# <a name="data-subject-rights-dsr-requests-under-gdpr"></a>Az adatalanyok jogainak (DSR) megfelelő kérelmek a GDPR szerint

Az Európai Tanács általános adatvédelmi szabályozása (GDPR) 2018. május 25. óta van hatályba. Az adatokkal kapcsolatban jelentős jogokat biztosít az egyének számára. A GDPR az egyének személyes adatainak védelme érdekében született. A Microsoft biztonság és megfelelőség iránti elkötelezettségéről a [Microsoft adatvédelmi központban olvashat bővebben](https://www.microsoft.com/trust-center).

Eltökélt célunk, hogy segítünk ügyfeleinknek megfelelni a GDPR követelményeinek. Ez magában foglalja a személyes adatokat, például felhasználói azonosítókat, telefonszámokat és e-mail címeket tartalmazó adatok törlésének vagy exportálásának jogát. A rendszergazdák a személyes adatok törlésére vagy exportálására vonatkozó felhasználói kérelmeket hajthatják végre.

## <a name="responding-to-gdpr-data-subject-delete-requests-for-customer-insights"></a>Válasz a GDPR érintettjeinek törlési kérelmeire a Customer Insights szolgáltatással kapcsolatban

A személyes adatoknak a szervezet ügyféladatok közüli törléséhez való jog kulcsfontosságú védelmi elem az Általános adatvédelmi rendeletben (GDPR). A személyes adatok eltávolítása magába foglalja az összes személyes adat és a rendszer által létrehozott naplók eltávolítását, kivéve az auditnaplózási információkat.

### <a name="manage-data-subject-delete-requests"></a>Az adatalanyok törlési kérelmeinek kezelése

A Customer Insights a következő terméken belüli élményeket kínálja egy adott ügyfél vagy felhasználó személyes adatainak törléséhez:

- **Ügyféladatok törlési kérelmeinek kezelése**: A Customer Insights ügyféladatait a Customer Insights megoldáson kívüli adatforrásokból lettek betöltve. Először hajtsa végre a GDPR törlési kérelmeit az eredeti adatforrás.
- **Törlési kérelmek kezelése a Customer Insights felhasználói adatokhoz**: Customer Insights által felhasználókhoz létrehozott adatok. Hajtsa végre az összes GDPR törlési kérelmet a Customer Insights szolgáltatásban.

#### <a name="manage-requests-to-delete-customer-data"></a>Ügyféladatok törlési kérelmeinek kezelése

Customer Insights-rendszergazdaként távolítsa el a adatforrás törölt Customer Insights-ügyféladatokat. Ellenőrizze, hogy a GDPR törlési kérelmei az eredeti adatforrás történtek-e.

1. Jelentkezzen be a Dynamics 365 Customer Insights rendszerbe.

1. Válassza az **Adatok** > **Adatforrások** lehetőséget.

1. A törölt ügyféladatokat tartalmazó minden egyes adatforráshoz a listából:
   1. Válassza ki a adatforrás, majd válassza a Frissítés **lehetőséget**.
   1. Ellenőrizze az adatforrás állapotát az **Állapot** alatt. A pipa azt jelenti, hogy a frissítés sikeresen megtörtént. A figyelmeztető háromszög azt jelenti, hogy valamilyen hiba történt. Ha egy figyelmeztető háromszög jelenik meg, forduljon ide: D365CI@microsoft.com.

   :::image type="content" source="media/gdpr-data-sources.png" alt-text="Ügyféladatok GDPR törlési kérelmeinek kezelése.":::

1. A sikeres adatforrás-frissítés után futtassa az alsóbb rétegbeli frissítéseket is. Különösen akkor, ha nincs ütemezve a Customer Insights ismétlődő teljes frissítése.

   > [!IMPORTANT]
   > A statikus szegmensek nem szerepelnek a teljes frissítésben vagy a törlési kérelem utáni lefelé irányuló frissítések futtatásában. Annak érdekében, hogy az ügyféladatok is el legyen távolítva a statikus szegmensekből, hozza létre újra a statikus szegmenseket a frissített forrásadatokkal.

#### <a name="manage-delete-requests-for-user-data"></a>Felhasználói adatok törlési kérelmeinek kezelése

Customer Insights-rendszergazdaként törölje a Customer Insights felhasználói adatait.

1. Jelentkezzen be a Dynamics 365 Customer Insights rendszerbe.

1. Lépjen a **Rendszergazdai** > **biztonság** >, és válassza a **Felhasználók** lapot.

1. Jelölje be a törölni kívánt felhasználók jelölőnégyzetét.

1. Válassza az **Eltávolítás** lehetőséget.

1. Törlés jóváhagyása.

## <a name="responding-to-gdpr-data-subject-export-requests"></a>GDPR szerinti Adatalanyi exportálási kérelmek megválaszolása

Az adathordozhatósági jog lehetővé teszi, hogy az adatalanyok személyes adataik másolatát elektronikus formátumban („strukturált, általánosan használt, géppel olvasható és interoperábilis formátumként”) formátumban elkérjék, amely átvihető másik adatkezelőhöz.

### <a name="manage-export-and-view-requests"></a>Az exportálási és a megtekintési kérelmek kezelése

Ügyfél- vagy felhasználói adatok exportálására vonatkozó kérelmek kezelése.

#### <a name="export-customer-data-tenant-admin"></a>Ügyféladatok exportálása (bérlői adminisztrátor)

Bérlői rendszergazdaként exportálja az ügyféladatokat.

1. E-mailben elküldhet egy kérelmet az ügyfél e-mail címének meghatározásával a D365CI@microsoft.com címre. A Customer Insights csoport egy adminisztrátora e-mailt küld a regisztrált bérlői rendszergazdai e-mail címre, amelyben megerősítést kér az adatok exportálása céljából.
2. Nyugtázza a kért ügyfél adatainak exportálását.
3. Az exportált adatok a bérlői rendszergazdai e-mail címen keresztül fogadhatók.

#### <a name="export-user-data-tenant-admin"></a>Felhasználói adatok exportálása (bérlői adminisztrátor)

Bérlői rendszergazdaként exportálja a felhasználói adatokat.

1. E-mailben elküldhet egy kérelmet a felhasználó e-mail címének meghatározásával a D365CI@microsoft.com címre. A Customer Insights csapata e-mailt küld a regisztrált bérlői rendszergazdai e-mail-címre, amelyben megerősítést kér az adatok exportálásához.
1. Nyugtázza a felhasználó adatainak exportálását.
1. Az exportált adatok a bérlői rendszergazdai e-mail címen keresztül fogadhatók.

## <a name="data-deletion-handling-in-dynamics-365-customer-insights"></a>Adattörlések kezelése a Dynamics 365 Customer Insights

Az adatok (adatpartíciók és adat-pillanatképek) törlődnek, ha az adatpartíciók és az adat-pillanatképek több mint 30 napig inaktívak, ami azt jelenti, hogy az adatforrások frissítése révén egy új adatpartíció és pillanatkép váltotta fel őket.

Nem minden adat és pillanatkép törlődik. A legutóbbi adatpartíció és adat-pillanatkép aktív, mert a Customer Insightsban használják őket. A legfrissebb adatok esetében nem számít, hogy az adatforrások nem frissültek-e az elmúlt 30 napban.

[!INCLUDE [footer-include](includes/footer-banner.md)]
