---
title: Ügyféltevékenységek
description: Ügyféltevékenységek meghatározása és azok megtekintése az ügyfélprofilok idővonalán.
ms.date: 07/22/2022
ms.subservice: audience-insights
ms.reviewer: mhart
ms.topic: conceptual
author: CadeSanthaMSFT
ms.author: cadesantha
manager: shellyha
searchScope:
- ci-entities
- ci-customer-card
- ci-relationships
- ci-activities
- ci-activities-wizard
- ci-measures
- ci-segment-suggestions
- customerInsight
ms.openlocfilehash: cc21b0eeb368156437e60d851c2d144f3974c066
ms.sourcegitcommit: c45c3e044034bf866b0662f80a59166cee4ababe
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/22/2022
ms.locfileid: "9188142"
---
# <a name="customer-activities"></a>Ügyféltevékenységek

Az ügyféltevékenységek az ügyfelek által végrehajtott műveletek vagy események. Például tranzakciók, támogatási hívások időtartama, webhely-áttekintések, vásárlások vagy visszaküldések. Ezeket a tevékenységeket egy vagy több adatforrás tartalmazza. A Customers Insights segítségével konszolidálhatja az ezekből az [adatforrásokból](data-sources.md) származó ügyféltevékenységeket, és társíthatja őket az ügyfélprofilokhoz. Ezek a tevékenységek időrendben jelennek meg az ügyfélprofil idővonalán. Foglalja bele az idővonalat a Dynamics 365 alkalmazásokba az [Ügyfélkártya bővítménymegoldással](customer-card-add-in.md).

## <a name="define-an-activity"></a>Egy tevékenység definiálása

Az entitásnak rendelkeznie kell legalább egy Dátum **típusú** attribútummal ahhoz, hogy szerepeljen az ügyfél idővonalán. A **Tevékenység hozzáadása** vezérlő le van tiltva, ha nem talál ilyen entitást.

1. Lépjen az **Adattevékenységek** > **oldalra**.

1. Válassza a Tevékenység **hozzáadása lehetőséget** az irányított élmény elindításához.

1. **A Tevékenységadatok** lépésben adja meg a következő adatokat:

   - **Tevékenység neve**: A tevékenység neve.
   - **Tevékenységentitás**: Tranzakciós vagy tevékenységadatokat tartalmazó entitás.
   - **Elsődleges kulcs**: A rekordot egyedileg azonosító mező. Nem tartalmazhat ismétlődő értékeket, üres értékeket vagy hiányzó értékeket.

   :::image type="content" source="media/Activity_Wizard1.PNG" alt-text="A tevékenységadatokat állítása be névvel, entitással és elsődleges kulcssal.":::

1. Válassza a **Következő** lehetőséget.

1. A Kapcsolat **lépésben válassza a** Kapcsolat **hozzáadása lehetőséget**, hogy összekapcsolja a tevékenységadatokat a megfelelő ügyfélrekorddal. Ez a lépés az entitások közötti kapcsolatot ábrázolja.  

   - **Idegen kulcs az entitástól**: A tevékenységentitás azon mezője, amely egy másik entitással való kapcsolat létrehozására szolgál.
   - **Entitásnévhez**: Megfelelő forrás ügyfélentitás, amellyel a tevékenységentitás kapcsolatban lesz. Csak az adategyesítési folyamatban használt forrás ügyfélentitásokhoz tud kapcsolódni.
   - **Kapcsolat neve**: Az entitások közötti kapcsolatot azonosító név. Ha már létezik kapcsolat a tevékenységentitás és a kiválasztott forrás ügyfélentitás között, a kapcsolat neve csak olvasható.

   :::image type="content" source="media/Activity_Wizard2.PNG" alt-text="Definiálja az entitás kapcsolatát.":::

   > [!TIP]
   > Az üzleti számlákkal (B-to-B) kapcsolatos környezetben a fiókentitások és az egyéb entitások között lehet választani. Ha kiválaszt egy fiókentitást, a kapcsolati elérési út automatikusan be lesz állítva. Más entitások esetében a kapcsolati elérési útját egy vagy több köztes entitásra vonatkozóan kell definiálni, amíg el nem ér egy fiókentitást.

1. Válassza az Alkalmaz **lehetőséget** a kapcsolat létrehozásához.

1. Válassza a **Következő** lehetőséget.

1. A **Tevékenységegyesítés** lépésben válassza ki a tevékenységeseményt, valamint a tevékenység kezdési idejét.
   - **Kötelező mezők**
      - **Eseménytevékenység**: A tevékenység eseményének megfelelő mező.
      - **Időbélyeg**: A tevékenység kezdő idejét jelképező mező.

   - **Választható mezők**
      - **További részletek**: Mező, amely a tevékenységre vonatkozó releváns információkat tartalmazza.
      - **Ikon**: Ezt a tevékenységtípust leginkább képviselő ikon.
      - **Webcím**: A tevékenységre vonatkozó információkat tartalmazó URL-címet tartalmazó mező. Például a tevékenység forrását jelentő tranzakciós rendszer. Ez az URL-cím lehet a adatforrás bármely mezője, vagy átalakítással Power Query új mezőként is felépíthető. Az URL-adatokat az *Egyesített tevékenység* entitás tárolja, amely az [API-k](apis.md) használatával lefelé irányulóan használható.

   - **Megjelenítés idősoron**
      - Válassza ki , hogy meg szeretné-e jeleníteni ezt az információt az ügyfélprofilok idővonalnézetében. Az **Igen** lehetőséget választva a tevékenységet megjelenítheti az idővonalon vagy a **Nem** lehetőséget választva elrejtheti.

      :::image type="content" source="media/Activity_Wizard3.PNG" alt-text="Adja meg az ügyféltevékenység adatait egy Egyesített tevékenység entitásban.":::

1. Válassza a Tovább gombot **a tevékenységtípus kiválasztásához, vagy válassza a Befejezés és áttekintés** lehetőséget **a tevékenység mentéséhez, ha a tevékenységtípust Más** értékre állítja **.**

1. A **Tevékenységtípus** lépésben válassza ki a tevékenységtípust, és tetszés szerint kiválaszthatja, hogy le szeretné-e szemantikusan képezni a Customer Insights más területein használat tevékenységtípusokat. Jelenleg a *Visszajelzés*, *a* Hűség, *a SalesOrder*, *a SalesOrderLine* és *az Előfizetés* tevékenységtípusok támogatják a szemantikát, miután beleegyeztek a mezők leképezésébe. Ha egy tevékenységtípus nem releváns az új tevékenységhez, választhat az *Egyéb* vagy az *Új létrehozása* lehetőségek közül az egyéni tevékenységtípushoz.

1. Válassza a **Következő** lehetőséget.

1. Az **Áttekintés** lépésben ellenőrizze a beállításokat. Lépjen vissza az előző lépések bármelyikéhez, és szükség esetén frissítse az információkat.

1. Válassza a **Tevékenység mentése** lehetőséget a módosítások alkalmazásához, majd válassza a **Kész** lehetőséget az **Adat** > **Tevékenységek** lehetőségekhez való visszatéréshez. Megjelenik a létrehozott tevékenység.

1. Az összes tevékenység létrehozása után válassza a Futtatás **lehetőséget** a feldolgozásukhoz.

[!INCLUDE [progress-details-include](includes/progress-details-pane.md)]

## <a name="manage-existing-activities"></a>Meglévő tevékenységek kezelése

Az **Adattevékenységek** > **lapon** megtekintheti a mentett tevékenységeket, azok forrásentitását, a tevékenység típusát, valamint azt, hogy szerepelnek-e az ügyfél idővonalán. A tevékenységek listáját bármely oszlop szerint rendezheti, vagy a keresőmező segítségével megkeresheti a kezelni kívánt tevékenységet.

Válasszon ki egy tevékenységet az elérhető műveletek megtekintéséhez.

- **Szerkessze** a tevékenységet a konfigurációjának módosításához. A konfiguráció a felülvizsgálati lépésben nyílik meg. A konfiguráció módosítása után válassza a **Tevékenység mentése** lehetőséget, majd a **Futtatás** lehetőséget a változtatások feldolgozásához.
- **Nevezze át** a tevékenységet. Válassza a **Mentés** lehetőséget a módosítások alkalmazásához.
- **Törölje** a tevékenységet. Ha egyszerre több tevékenységet szeretne törölni, jelölje ki a tevékenységeket, majd **a Törlés lehetőséget**. Törlés jóváhagyása.

## <a name="view-activity-timelines-on-customer-profiles"></a>Tevékenység ütemezésének megtekintése ügyfélprofilon

1. Ha a Tevékenységkonfigurációban a Megjelenítés a tevékenység idővonalában lehetőséget választotta **, lépjen az Ügyfelekelemre** **, és válasszon ki egy ügyfélprofilt az ügyfél tevékenységeinek megtekintéséhez a** Tevékenység idővonala **szakaszban**.

   :::image type="content" source="media/Activity_Timeline1.PNG" alt-text="A konfigurált tevékenységek megtekintése az Ügyfélprofilban.":::

1. Tevékenységek szűrése a tevékenység idővonalán:

   - Válasszon ki egy vagy több tevékenységikont az eredmények finomításához, hogy csak a kiválasztott típusokat tartalmazza.

     :::image type="content" source="media/Activity_Timeline2.PNG" alt-text="A tevékenységeket típus szerint szűrheti az ikonok segítségével.":::

   - Válassza a Szűrő **lehetőséget** egy szűrőpanel megnyitásához az idővonal-szűrők konfigurálásához. Szűrés ActivityType *és/vagy* Date *szerint*. Válassza az **Alkalmaz** lehetőséget.

     :::image type="content" source="media/Activity_Timeline3.PNG" alt-text="A szűrőpanelen konfigurálhatja a szűrési feltételeket.":::

1. A szűrők eltávolításához válassza a Szűrők törlése lehetőséget **, vagy válassza a Szűrő** lehetőséget **, és törölje a szűrő jelölőnégyzet jelölését.**

> [!NOTE]
> A tevékenységszűrőket a rendszer eltávolítja, amikor elhagyja az ügyfélprofilt. Minden alkalommal alkalmaznia kell őket, amikor megnyit egy ügyfélprofilt.

[!INCLUDE [footer-include](includes/footer-banner.md)]
