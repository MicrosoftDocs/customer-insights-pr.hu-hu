---
title: Ügyféltevékenységek
description: Ügyféltevékenységek meghatározása és azok megtekintése az ügyfélprofilok idővonalán.
ms.date: 11/01/2021
ms.service: customer-insights
ms.subservice: audience-insights
ms.reviewer: mhart
ms.topic: conceptual
author: CadeSanthaMSFT
ms.author: cadesantha
manager: shellyha
ms.openlocfilehash: c99ec2e7d5e4bf32a509bbe4c0c53999129b2305
ms.sourcegitcommit: 834651b933b1e50e7557d44f926a3fb757c1f83a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/02/2021
ms.locfileid: "7732463"
---
# <a name="customer-activities"></a>Ügyféltevékenységek

A Dynamics 365 Customer Insights különböző adatforrásaiból származó ügyféltevékenységek [...](data-sources.md) kombinálása olyan ütemterv létrehozásához, amely időrendben felsorolja a tevékenységeket. Az idővonalat a Dynamics 365-alkalmazásokba is belefoglalja az [Ügyfélkártya](customer-card-add-in.md) bővítmény-megoldásba, vagy egy Power BI irányítópultba.

## <a name="define-an-activity"></a>Egy tevékenység definiálása

Az adatforrások több adatforrásból származó, tranzakciós és tevékenységi adatokkal rendelkező entitásokat tartalmazhatnak. Azonosítsa ezeket az entitásokat, és jelölje ki az ügyfél idővonalán megtekinteni kívánt tevékenységeket. Válassza ki azt az entitást, amely a cél tevékenységet vagy tevékenységeket tartalmazza.

Egy entitásben legalább egy **Dátum** típusú attribútumnak szerepelnie kell, hogy az bekerüljön az ügyfél idővonalába, és nem lehet entitásokat felvenni **Dátum** mezők nélkül. A **Tevékenység hozzáadása** vezérlő le van tiltva, ha nem talál ilyen entitást.

1. A célközönség információin belül nyissa meg a következőt: **Adatok** > **Tevékenységek**.

1. Válassza a **Tevékenység hozzáadása** lehetőséget az interaktív élmény elkezdéséhez a tevékenység beállítási folyamathoz.

1. A **Tevékenységadat** lépésben állítsa be a következő mezők értékeit:

   - **Tevékenység neve**: Válassza ki a tevékenység nevét.
   - **Entitás**: Jelöljön ki egy entitást, amely tranzakciós vagy tevékenységi adatot tartalmaz.
   - **Elsődleges kulcs**: Válassza ki azt a mezőt, amely egyértelműen azonosítja a rekordot. Nem tartalmazhat ismétlődő értékeket, üres értékeket vagy hiányzó értékeket.

   :::image type="content" source="media/Activity_Wizard1.PNG" alt-text="A tevékenységadatokat állítása be névvel, entitással és elsődleges kulcssal.":::

1. A **Tovább** gombot választva menjen tovább a következő lépésre.

1. A **Kapcsolat** lépésben konfigurálja az adatokat, hogy a tevékenység adatai hozzá csatlakozzon a megfelelő ügyféladatokhoz. Ez a lépés az entitások közötti kapcsolatot ábrázolja.  

   - **Első**: A tevékenységentitás egy másik entitással való kapcsolat létrehozására használt idegen mező.
   - **Második**: A megfelelő forrás ügyfélentitás, amellyel a tevékenységentitás kapcsolatban lesz. Csak az adategyesítési folyamatban használt forrás ügyfélentitásokhoz tud kapcsolódni.
   - **Harmadik**: Ha a tevékenységentitás és a kijelölt forrás ügyfélentitása között már létezik kapcsolat, a kapcsolat neve írásvédett módban lesz. Ha ilyen kapcsolat nem létezik, új kapcsolat jön létre a mezőben megadott névvel.

   :::image type="content" source="media/Activity_Wizard2.PNG" alt-text="Definiálja az entitás kapcsolatát.":::

   > [!TIP]
   > Az üzleti számlákkal (B-to-B) kapcsolatos környezetben a fiókentitások és az egyéb entitások között lehet választani. Ha kiválaszt egy fiókentitást, a kapcsolati elérési út automatikusan be lesz állítva. Más entitások esetében a kapcsolati elérési útját egy vagy több köztes entitásra vonatkozóan kell definiálni, amíg el nem ér egy fiókentitást.

1. A **Tovább** gombot választva menjen tovább a következő lépésre. 

1. A **Tevékenységegyesítés** lépésben válassza ki a tevékenységeseményt, valamint a tevékenység kezdési idejét. 
   - **Kötelező mezők**
      - **Eseménytevékenység**: A tevékenység eseményének megfelelő mező.
      - **Időbélyeg**: A tevékenység kezdő idejét jelképező mező.

   - **Választható mezők**
      - **További részletek**: Mező, amely a tevékenységre vonatkozó releváns információkat tartalmazza.
      - **Ikon**: Ezt a tevékenységtípust leginkább képviselő ikon.
      - **Webcím**: A tevékenységre vonatkozó információkat tartalmazó URL-címet tartalmazó mező. Például a tevékenység forrását jelentő tranzakciós rendszer. Ez az URL-cím az adatforrás tetszőleges mezője lehet, vagy Power Query átalakítást használó új mezőként lehet kialakítani. Az URL-adatokat az *Egyesített tevékenység* entitás tárolja, amely az [API-k](apis.md) használatával lefelé irányulóan használható.

   - **Megjelenítés idősoron**
      - Válassza ki , hogy meg szeretné-e jeleníteni ezt az információt az ügyfélprofilok idővonalnézetében. Az **Igen** lehetőséget választva a tevékenységet megjelenítheti az idővonalon vagy a **Nem** lehetőséget választva elrejtheti.

      :::image type="content" source="media/Activity_Wizard3.PNG" alt-text="Adja meg az ügyféltevékenység adatait egy Egyesített tevékenység entitásban.":::

1. A **Következő** lehetőség kiválasztásával a következő lépésre mehet. A **Befejezés és áttekintés** lehetőséget választva most már az **Egyéb** tevékenységtípussal mentheti a tevékenységet. 

1. A **Tevékenységtípus** lépésben válassza ki a tevékenységtípust, és tetszés szerint kiválaszthatja, hogy le szeretné-e szemantikusan képezni a Customer Insights más területein használat tevékenységtípusokat. Jelenleg a *Visszajelzés*, *Hűségprogram*, *SalesOrder*, *SalesOrderLine*, és *Előfizetés* tevékenységtípusok szemantikailag leképezhetők, miután megállapodtak a mezők feltérképezéséről. Ha egy tevékenységtípus nem releváns az új tevékenységhez, választhat az *Egyéb* vagy az *Új létrehozása* lehetőségek közül az egyéni tevékenységtípushoz.

1. A **Következő** lehetőség kiválasztásával a következő lépésre mehet. 

1. Az **Áttekintés** lépésben ellenőrizze a beállításokat. Lépjen vissza az előző lépések bármelyikéhez, és szükség esetén frissítse az információkat.

   :::image type="content" source="media/Activity_Wizard5.PNG" alt-text="Tevékenység megadott mezőinek áttekintése.":::
   
1. Válassza a **Tevékenység mentése** lehetőséget a módosítások alkalmazásához, majd válassza a **Kész** lehetőséget az **Adat** > **Tevékenységek** lehetőségekhez való visszatéréshez. Itt láthatja, hogy mely tevékenységek vannak beállítva az idősoron való megjelenítéshez. 

1. A **Tevékenységek** lapon válassza a **Futtatás** lehetőséget a tevékenység feldolgozásához. 

[!INCLUDE [progress-details-include](../includes/progress-details-pane.md)]

## <a name="manage-existing-activities"></a>Meglévő tevékenységek kezelése

Az **Adatok** > **Tevékenységek** oldalon megtekintheti az összes mentett tevékenységet, és kezelheti azokat. Minden tevékenységet egy sor képvisel, amely a forrásra, az entitásra és a tevékenységtípusra vonatkozó adatokat is tartalmazza.

A következő műveletek érhetők el, amikor kiválaszt egy tevékenységet. 

- **Szerkesztés**: Megnyitja a tevékenység beállítását az áttekintés lépésben. Ebben a lépésben bármelyiket vagy az összes aktuális konfigurációt módosíthatja. A konfiguráció módosítása után válassza a **Tevékenység mentése** lehetőséget, majd a **Futtatás** lehetőséget a változtatások feldolgozásához.

- **Átnevezés**: Megnyit egy párbeszédpanelt, ahol a kijelölt tevékenységhez más nevet adhat meg. Válassza a **Mentés** lehetőséget a módosítások alkalmazásához.

- **Törlés**: Párbeszéd megnyitása a kijelölt tevékenység törlésének megerősítéséhez. Egyszerre több tevékenységet is törölhet, ha kijelöli a tevékenységeket, majd kiválasztja a törlés ikont. Válassza ki az **Eltávolítás** lehetőséget a törlés megerősítéséhez.

## <a name="view-activity-timelines-on-customer-profiles"></a>Tevékenység ütemezésének megtekintése ügyfélprofilon

Az ügyféltevékenységek konfigurálása után válassza a **Tevékenység megjelenítése az idősoron** lehetőséget a tevékenységkonfigurációban, és keresse meg az ügyfél összes tevékenységét az ügyfél profiljában.

Az ügyfél idővonalának megnyitásához nyissa meg az **Ügyfelek** lehetőséget, és válassza ki a megtekinteni kívánt ügyfélprofilt.

Ha egy ügyfél részt vett egy Ön által beállított tevékenységben, akkor az a **Tevékenység idősora** szakaszban található.

:::image type="content" source="media/Activity_Timeline1.PNG" alt-text="A konfigurált tevékenységek megtekintése az Ügyfélprofilban.":::

A tevékenységeket többféleképpen is szűrheti a tevékenység ütemezésében:

- A tevékenységikonok kiválasztásával finomíthatja az eredményeket, hogy csak a kijelölt típus(ok) szerepeljenek a kiválasztottakban.

  :::image type="content" source="media/Activity_Timeline2.PNG" alt-text="A tevékenységeket típus szerint szűrheti az ikonok segítségével.":::

- A **Szűrő** kiválasztásával szűrőpanelt nyithat meg az idővonal szűrőinek konfigurálához.

   1. Szűrhet *ActivityType* és *Date* értékek szerint
   1. Válassza az **Alkalmaz** lehetőséget a tevékenység ütemezési szűrőinek használatához.

   :::image type="content" source="media/Activity_Timeline3.PNG" alt-text="A szűrőpanelen konfigurálhatja a szűrési feltételeket.":::

Szűrők eltávolításához válassza ki az idővonalon alkalmazott minden szűrő mellett az **x** ikont, vagy válassza a **Szűrők törlése** lehetőséget.


> [!NOTE]
> A tevékenységszűrőket a rendszer eltávolítja, amikor elhagyja az ügyfélprofilt. Azokat minden alkalommal alkalmaznia kell, amikor megnyit egy ügyfélprofilt.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
