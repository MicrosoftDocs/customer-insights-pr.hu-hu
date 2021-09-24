---
title: Az adatalanyok jogainak (DSR) megfelelő kérelmek a GDPR szerint | Microsoft Docs
description: Adatalanyi kérelmekre adott válasz a Dynamics 365 Customer Insights célközönség-információ funkciójához.
ms.date: 08/11/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: wimohabb
manager: shellyha
ms.openlocfilehash: 6faaeb6a1ee34c3e5c8e7d465b37cee589bc920c
ms.sourcegitcommit: 5704002484cdf85ebbcf4e7e4fd12470fd8e259f
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/08/2021
ms.locfileid: "7483674"
---
# <a name="data-subject-rights-dsr-requests-under-gdpr"></a>Az adatalanyok jogainak (DSR) megfelelő kérelmek a GDPR szerint

Az Európai Tanács általános adatvédelmi szabályozása (GDPR) 2018. május 25. óta van hatályba. Az adatokkal kapcsolatban jelentős jogokat biztosít az egyének számára. A GDPR az egyének személyes adatainak védelme érdekében született. A Microsoft biztonsági és megfelelési helyzetére vonatkozó további tudnivalókat a [Microsoft biztonsági központban](https://www.microsoft.com/trust-center) olvashatja.

Eltökélt célunk, hogy segítünk ügyfeleinknek megfelelni a GDPR követelményeinek. Magában foglalja a személyes adatokat (például felhasználói azonosítókat, telefonszámokat és e-mail címeket) tartalmazó adatok törlésére és exportálására vonatkozó jogokat. A rendszergazdák a személyes adatok törlésére vagy exportálására vonatkozó felhasználói kérelmeket hajthatják végre.

## <a name="audience-insights"></a>Célközönséggel kapcsolatos információk

### <a name="responding-to-gdpr-data-subject-delete-requests-for-dynamics-365-customer-insights-audience-insights-capability"></a>GDPR adatalanyi törlési kérelmekre adott válasz a Dynamics 365 Customer Insights célközönség-információ funkciójához

A személyes adatoknak a szervezet ügyféladatok közüli törléséhez való jog kulcsfontosságú védelmi elem az Általános adatvédelmi rendeletben (GDPR). A személyes adatok eltávolítása magába foglalja az összes személyes adat és a rendszer által létrehozott naplók eltávolítását, kivéve az auditnaplózási információkat.

#### <a name="manage-data-subject-delete-requests"></a>Az adatalanyok törlési kérelmeinek kezelése

A célközönség-információk a következő termékeken belüli élményeket kínálja egy adott ügyfél vagy felhasználó személyes adatainak törléséhez:

- **Ügyféladatok törlési kérelmeinek kezelése**: A Customer Insights ügyféladatait a Customer Insights megoldáson kívüli adatforrásokból lettek betöltve. Minden GDPR szerinti törlési kérelmet az eredeti adatforráson kell végrehajtani.
- **Törlési kérelmek kezelése a Customer Insights felhasználói adatokhoz**: Customer Insights által felhasználókhoz létrehozott adatok. Minden GDPR szerinti törlési kérelmet a Customer Insights megoldásban kell elvégezni.

##### <a name="manage-requests-to-delete-customer-data"></a>Ügyféladatok törlési kérelmeinek kezelése

A Customer Insights rendszergazdák az alábbi lépések végrehajtásával eltávolíthatják az adatforrásban törölt ügyféladatokat:

1. Jelentkezzen be a Dynamics 365 Customer Insights rendszerbe.
2. A célközönség információin belül nyissa meg a következőt **Adatok** > **Adatforrások**
3. A törölt ügyféladatokat tartalmazó minden egyes adatforráshoz a listából:
   1. Válassza a (...), majd a **Frissítés** lehetőséget.
   2. Ellenőrizze az adatforrás állapotát az **Állapot** alatt. A pipa azt jelenti, hogy a frissítés sikeresen megtörtént. A figyelmeztető háromszög azt jelenti, hogy valamilyen hiba történt. Ha egy figyelmeztető háromszög jelenik meg, forduljon ide: D365CI@microsoft.com.

> [!div class="mx-imgBorder"]
> ![Ügyféladatok GDPR törlési kérelmeinek kezelése.](audience-insights/media/gdpr-data-sources.png "Ügyféladatok GDPR törlési kérelmeinek kezelése")

##### <a name="manage-delete-requests-for-user-data"></a>Felhasználói adatok törlési kérelmeinek kezelése

Egy Customer Insights rendszergazda a Customer Insights ügyféladatok törlését az alábbi lépésekkel hajthatja végre:

1. Jelentkezzen be a Dynamics 365 Customer Insights rendszerbe.
2. A célközönség információin belül nyissa meg a következőt **Rendszergazda** > **Engedélyek**.
3. Jelölje be a törölni kívánt felhasznáó jelölőnégyzetét.
4. Válassza az **Eltávolítás** lehetőséget.

### <a name="responding-to-gdpr-data-subject-export-requests"></a>GDPR szerinti Adatalanyi exportálási kérelmek megválaszolása

Az Általános adatvédelmi rendelet (GDPR) világában való eligazodás során az Önnel folytatott partneri elkötelezettség részeként egy előkészületeket elősegítő dokumentációt fejlesztettünk ki. Ez a dokumentáció ismerteti azokat a lépéseket, amelyeket ma a GDPR-megfelelőség támogatásához megtehet a célközönség-információk használatával.

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

## <a name="engagement-insights"></a>Elkötelezettségi információk

### <a name="deleting-and-exporting-event-data-containing-end-user-identifiable-information"></a>Végfelhasználók azonosítására alkalmas adatokat tartalmazó eseményadatok törlése és exportálása

A következő részek ismertetik, hogyan törölhetők és exportálhatók a személyes adatokat tartalmazó eseményadatok.

Adatok törléséhez vagy exportálásához:

1. Címkézze fel a személyes adatokat tartalmazó eseménytulajdonságokat.
2. Törölje vagy exportálja az adott értékekkel (például egy megadott felhasználói azonosítóval) kapcsolatos adatokat.

#### <a name="tag-and-update-event-properties"></a>Címkézzel fel és frissítse az eseménytulajdonságokat

A személyes adatok egy esemény tulajdonságszinten vannak címkézve. Első lépésként címkézni kell a törléshez vagy exportáláshoz figyelembe venni használt tulajdonságokat.

Ha személyes adatokat tartalmazóként címkézni akar egy esemény tulajdonságot, hajtsa végre a következő lépéseket:

1. Nyissa meg az eseményt tartalmazó munkaterületet.

1. Az **Adatok** > **Események** megnyitása esetén a kijelölt munkaterületen megjelenik az események listája.
  
1. Válassza ki a felcímkézni kívánt eseményt.

1. Válassza a **Tulajdonságok szerkesztése** lehetőséget, ha meg szeretné nyitni a kijelölt esemény összes tulajdonságát tartalmazó ablaktáblát.
     
1. Válassza a **...** lehetőséget, majd a **Szerkesztés** lehetőséget, ha el szeretné érni a **Tulajdonság frissítése** párbeszédpanelt.

   ![Esemény szerkesztése.](engagement-insights/media/edit-event.png "Esemény szerkesztése")

1. Válassza a **Tulajdonság frissítése** ablakban a **...** lehetőséget a jobb felső sarokban, majd válassza az **EUII-mező tartalma** lehetőséget. A módosítások mentéséhez válassza a **Frissítés** lehetőséget.

   ![Módosítások mentése.](engagement-insights/media/update-property.png "Módosítások mentése")

   > [!NOTE]
   > Minden alkalommal, amikor megváltozik az eseménysémája, vagy új eseményt hoz létre, szükség esetén ajánlott kiértékelni a társított eseménytulajdonságokat, illetve visszacímkézni őket személyes adatokként.

#### <a name="delete-or-export-tagged-event-data"></a>Címkézett eseményadatok törlése vagy exportálása

Ha az előző lépésben leírtaknak megfelelően az összes eseménytulajdonság címkéje meg van jelölve, a környezet rendszergazdája törlési kérelmet adhat ki a címkézett eseményadatokra.

Az EUII-törlési vagy -exportálási kérelmek kezelése

1. Menjen a **Felügyelet** > **Környezet** > **Beállítások** pontra.

1. A **végfelhasználói azonosító adatok kezelése (EUII)** szakaszban válassza az **EUII kezelése** lehetőséget.

##### <a name="deletion"></a>Törlés

Törléshez vesszővel elválasztott felhasználói azonosítók listáját adhatja meg a **Végfelhasználó azonosítására alkalmas adatok törlése (EUII)** szakaszban. Ezután a rendszer az aktuális környezet összes projektje címkézett eseménytulajdonságával összehasonlítja ezeket azazonosítókat a pontos karakterlánc-egyezésen keresztül. 

Ha egy tulajdonságérték egyezik az egyik megadottazonosítóval, a társított eseményt véglegesen törli a rendszer. A művelet nem véglegessége miatt a **Törlés** lehetőséget választva meg kell erősítenie a törlést.

##### <a name="export"></a>Export

Az exportálási folyamat azonos a törlési folyamattal, amikor a **Végfelhasználó azonosítására alkalmas adatok exportálása** szakaszban definiálja az esemény tulajdonságértékeket. Emellett meg kell adnia egy **Azure blob storage URL**-címet is az exportálási cél megadásához. Az Azure Blob URL-címnek tartalmaznia kell egy [megosztott hozzáférési aláírást (SAS)](/azure/storage/common/storage-sas-overview).

Az **Exportálás** lehetőség kiválasztása után az aktuális csoport egyező címkézett tulajdonságokat tartalmazó eseményei CSV formátumban exportálva lesznek az exportálási célba.

### <a name="good-practices"></a>Jó gyakorlatok

* Próbálja meg elkerülni a személyes adatokat tartalmazó események küldését.
* Ha EUII-adatokat tartalmazó eseményeket kell küldenie, korlátozza az EUII-adatokat tartalmazó események és eseménytulajdonságok számát. Ideális esetben csak egyetlen ilyen eseményre korlátozza magát.
* Győződjön meg róla, hogy csak néhány személy fér hozzá az elküldött személyes adatokhoz.
* Személyes adatokat tartalmazó események esetén ügyeljen arra, hogy egyetlen tulajdonsággal olyan egyedi azonosítót állítson be, amely egyszerűen csatolható egy adott felhasználóhoz (például felhasználói azonosítóhoz). Ez megkönnyíti az adatok exportálását vagy törlését.
* Eseményenként csak egy tulajdonságot címkéz fel személyes adatokat tartalmazóként. Ideális esetben csak egyedi azonosítót tartalmazó fájl.
* Ne címkézzen fel olyan tulajdonságokat, amelyek részletes értékeket tartalmaznak (például a kérelem teljes szövegét). Az aktivitási információk szolgáltatás pontos karakterlánc-egyezést használ annak eldöntéséhez, hogy mely eseményeket kell törölni vagy exportálni.

[!INCLUDE[footer-include](includes/footer-banner.md)]