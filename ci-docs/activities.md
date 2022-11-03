---
title: Ügyfél- vagy üzleti kapcsolatfelvételi tevékenységek
description: Határozza meg az ügyfél- vagy kapcsolattartói tevékenységeket, és tekintse meg őket az ügyfélprofilok idővonalán.
ms.date: 10/26/2022
ms.subservice: audience-insights
ms.reviewer: v-wendysmith
ms.topic: conceptual
author: srivas15
ms.author: shsri
manager: shellyha
searchScope:
- ci-entities
- ci-customer-card
- ci-relationships
- ci-activities
- ci-activities-wizard
- ci-measures
- ci-segment-suggestions
- customerInsights
ms.openlocfilehash: d8caa477278f04c3a0a95ced15f4bea2a22aa8cd
ms.sourcegitcommit: da6a2d189edacc8f2c0f2abedcb28245f26fe74c
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/27/2022
ms.locfileid: "9723784"
---
# <a name="customer-or-business-contact-activities"></a>Ügyfél- vagy üzleti kapcsolatfelvételi tevékenységek

Az ügyféltevékenységek olyan műveletek vagy események, amelyeket ügyfelek vagy üzleti kapcsolattartók hajtanak végre. Például tranzakciók, támogatási hívások időtartama, webhely-felülvizsgálatok, vásárlások vagy visszaküldések. Ezeket a tevékenységeket egy vagy több adatforrás tartalmazza. A Customers Insights segítségével konszolidálhatja az ügyféltevékenységeket ezekből az [adatforrásokból](data-sources.md), és társíthatja őket az ügyfélprofilokhoz. Ezek a tevékenységek időrendi sorrendben jelennek meg az ügyfélprofil idővonalán. Foglalja bele az idővonalat a Dynamics 365 alkalmazásokba az [Ügyfélkártya bővítménymegoldással](customer-card-add-in.md).

## <a name="define-a-customer-activity"></a>Vevői tevékenység meghatározása

A gazdálkodó egységnek rendelkeznie kell legalább egy Date **típusú** attribútummal ahhoz, hogy bekerüljön a vevői idővonalba. A **Tevékenység hozzáadása** vezérlő le van tiltva, ha nem talál ilyen entitást.

1. Lépjen az Adattevékenységek **oldalra** > **·**.

1. Válassza a Tevékenység **hozzáadása lehetőséget** az interaktív élmény elindításához.

1. **A Tevékenységadatok** lépésben adja meg a következő adatokat:

   - **Tevékenység neve**: Válassza ki a tevékenység nevét.
   - **Tevékenységentitás**: Válasszon ki egy entitást, amely tranzakciós vagy tevékenységadatokat tartalmaz.
   - **Elsődleges kulcs**: Válassza ki azt a mezőt, amely egyértelműen azonosítja a rekordot. Nem tartalmazhat ismétlődő értékeket, üres értékeket vagy hiányzó értékeket.

     > [!NOTE]
     > Az egyes sorok elsődleges kulcsának konzisztensnek kell maradnia adatforrás frissítésekben. Ha egy sor elsődleges kulcsa frissül egy adatforrás frissítésben, az ismétlődéseket hoz létre a kimeneti Tevékenység entitásban. 

   :::image type="content" source="media/Activity_Wizard1.PNG" alt-text="A tevékenységadatokat állítása be névvel, entitással és elsődleges kulcssal.":::

1. Válassza a **Következő** lehetőséget.

1. A Kapcsolat **lépésben válassza a Kapcsolat** hozzáadása lehetőséget a **tevékenységadatok** és a megfelelő ügyfélrekord összekapcsolásához. Ez a lépés az entitások közötti kapcsolatot ábrázolja.  

   - **Idegen kulcs**: Idegen mező a tevékenységentitásban, amely egy másik entitással való kapcsolat létrehozására szolgál.
   - **Entitásnévhez**: Megfelelő forrás ügyfélentitás, amellyel a tevékenységentitás kapcsolatban lesz. Csak az adategyesítési folyamatban használt forrás ügyfélentitásokhoz tud kapcsolódni.
   - **Kapcsolat neve: Ha már létezik kapcsolat a tevékenységentitás és a kiválasztott forrás ügyfélentitás között, a kapcsolat neve** csak olvasható módban lesz. Ha ilyen kapcsolat nem létezik, új kapcsolat jön létre a mezőben megadott névvel.

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

1. Válassza a Tovább **lehetőséget a tevékenység típusának kiválasztásához, vagy válassza a Befejezés és áttekintés** lehetőséget **a** tevékenység mentéséhez úgy, hogy a tevékenység típusa Egyéb értékre **van** állítva.

1. A **Tevékenységtípus** lépésben válassza ki a tevékenységtípust, és tetszés szerint kiválaszthatja, hogy le szeretné-e szemantikusan képezni a Customer Insights más területein használat tevékenységtípusokat. Jelenleg a Visszajelzés *, a Hűség, a SalesOrder*, a SalesOrderLine *és* az Előfizetési *tevékenységtípusok támogatják a szemantikát,* *miután beleegyeztek a* *mezők* leképezésébe. Ha egy tevékenységtípus nem releváns az új tevékenységhez, választhat az *Egyéb* vagy az *Új létrehozása* lehetőségek közül az egyéni tevékenységtípushoz.

1. Válassza a **Következő** lehetőséget.

1. Az **Áttekintés** lépésben ellenőrizze a beállításokat. Lépjen vissza az előző lépések bármelyikéhez, és szükség esetén frissítse az információkat.

1. Válassza a **Tevékenység mentése** lehetőséget a módosítások alkalmazásához, majd válassza a **Kész** lehetőséget az **Adat** > **Tevékenységek** lehetőségekhez való visszatéréshez. Megjelenik a létrehozott tevékenység.

1. Az összes tevékenység létrehozása után válassza a Futtatás **lehetőséget** a feldolgozásukhoz.

[!INCLUDE [progress-details-include](includes/progress-details-pane.md)]

## <a name="manage-existing-customer-activities"></a>Meglévő ügyféltevékenységek kezelése

Az **Adattevékenységek** > **oldalon** megtekintheti a mentett tevékenységeket, azok forrásentitását, a tevékenység típusát, valamint azt, hogy szerepelnek-e az ügyfél idővonalán. A tevékenységek listáját bármely oszlop szerint rendezheti, vagy a keresőmező segítségével megkeresheti a kezelni kívánt tevékenységet.

Válasszon ki egy tevékenységet az elérhető műveletek megtekintéséhez.

- **Szerkessze** a tevékenységet a konfiguráció módosításához. A konfiguráció megnyílik az ellenőrzési lépésben. A konfiguráció módosítása után válassza a **Tevékenység mentése** lehetőséget, majd a **Futtatás** lehetőséget a változtatások feldolgozásához.
- **Nevezze át** a tevékenységet. Válassza a **Mentés** lehetőséget a módosítások alkalmazásához.
- **Törölje** a tevékenységet. Ha egyszerre több tevékenységet szeretne törölni, válassza ki a tevékenységeket, majd a Törlés **lehetőséget**. Törlés jóváhagyása.

## <a name="view-activity-timelines-on-customer-profiles"></a>Tevékenység ütemezésének megtekintése ügyfélprofilon

1. Ha a Megjelenítés a tevékenység idővonalán lehetőséget választotta **a tevékenységkonfigurációban, lépjen az Ügyfelek** elemre **, és válasszon ki egy ügyfélprofilt az ügyfél tevékenységeinek megtekintéséhez a** Tevékenység idővonala **szakaszban.**

   :::image type="content" source="media/Activity_Timeline1.PNG" alt-text="A konfigurált tevékenységek megtekintése az Ügyfélprofilban.":::

1. Tevékenységek szűrése a tevékenység idővonalán:

   - Válasszon ki egy vagy több tevékenységikont az eredmények finomításához, hogy csak a kiválasztott típusokat tartalmazzák.

     :::image type="content" source="media/Activity_Timeline2.PNG" alt-text="A tevékenységeket típus szerint szűrheti az ikonok segítségével.":::

   - Válassza a Szűrő **lehetőséget** egy szűrőpanel megnyitásához az idővonal-szűrők konfigurálásához. Szűrés tevékenységtípus *és/vagy* dátum *szerint*. Válassza az **Alkalmaz** lehetőséget.

     :::image type="content" source="media/Activity_Timeline3.PNG" alt-text="A szűrőpanelen konfigurálhatja a szűrési feltételeket.":::

> [!NOTE]
> A tevékenységszűrőket a rendszer eltávolítja, amikor elhagyja az ügyfélprofilt. Minden alkalommal alkalmaznia kell őket, amikor megnyit egy ügyfélprofilt.

## <a name="define-a-contact-activity"></a>Kapcsolattartói tevékenység meghatározása

Üzleti partnerek (B-to-B) esetén használjon ContactProfile *entitást* a kapcsolattartók tevékenységeinek rögzítéséhez. A partner tevékenységének idővonalán láthatja, hogy melyik kapcsolattartó volt felelős az egyes tevékenységekért. A legtöbb lépés az ügyféltevékenység-leképezési konfigurációt követi.

   > [!NOTE]
   > Kapcsolattartói szintű tevékenység meghatározásához létre kell hozni egy *ContactProfile* entitást, akár egységes kapcsolattartói [profilként](data-unification-contacts.md), akár [szemantikai leképezéssel](semantic-mappings.md#define-a-contactprofile-semantic-entity-mapping).
   >
   > A tevékenységadatokban szereplő minden egyes rekordhoz rendelkeznie **kell AccountID és** ContactID **attribútummal** is.
  
1. Lépjen az Adattevékenységek **oldalra** > **·**.

1. Válassza a Tevékenység **hozzáadása lehetőséget**.

1. **A Tevékenységadatok** lépésben adja meg a következő adatokat:

   - **Tevékenység neve**: Válassza ki a tevékenység nevét.
   - **Tevékenységentitás**: Válasszon ki egy entitást, amely tranzakciós vagy tevékenységadatokat tartalmaz.
   - **Elsődleges kulcs**: Válassza ki azt a mezőt, amely egyértelműen azonosítja a rekordot. Nem tartalmazhat ismétlődő értékeket, üres értékeket vagy hiányzó értékeket.

     > [!NOTE]
     > Az egyes sorok elsődleges kulcsának konzisztensnek kell maradnia adatforrás frissítésekben. Ha egy sor elsődleges kulcsa frissül egy adatforrás frissítésben, az ismétlődéseket hoz létre a kimeneti Tevékenység entitásban. 


1. **A kapcsolatok** lépésben hozzon létre közvetett kapcsolatot a tevékenységforrás-adatok és a partnerek között, a kapcsolattartási adatokat közvetítő entitásként használva. További információ: [Közvetlen és közvetett kapcsolati útvonalak](relationships.md#relationship-paths).
   - Példa a Vásárlások *nevű* tevékenységre:
      - **Vásárlások forrástevékenységére vonatkozó adatok Kapcsolatfelvételi adatok** > **a** ContactID **attribútumon**
      - **Kapcsolatfelvételi adatok** > **Fiókadatok** az AccountID **attribútumon**

   :::image type="content" source="media/Contact_Activities1.png" alt-text="Példa a kapcsolat beállítására.":::

1. A kapcsolatok beállítása után válassza a Tovább **lehetőséget**, és fejezze be a tevékenységleképezés konfigurációját. A tevékenység létrehozásával kapcsolatos részletes lépésekért lásd: [ügyféltevékenység](#define-a-customer-activity) meghatározása.

1. Futtassa a tevékenységleképezéseket.

1. A kapcsolattartói szintű tevékenységek mostantól láthatók lesznek az ügyfél idővonalán.

   :::image type="content" source="media/Contact_Activities2.png" alt-text="Végeredmény a kapcsolatfelvételi tevékenységek konfigurálása után":::

## <a name="contact-level-activity-timeline-filtering"></a>Kapcsolattartói szintű tevékenység-idővonal-szűrés

A kapcsolattartói szintű tevékenységleképezés konfigurálása és futtatása után az ügyfelek tevékenység-idővonala frissül. Tartalmazza az azonosítóikat vagy nevüket, a ContactProfile *konfigurációjától függően, azokhoz a* tevékenységekhez, amelyeken cselekedtek. Az idővonalon kapcsolattartók szerint szűrheti a tevékenységeket, hogy megtekinthesse az Önt érdeklő kapcsolattartókat. Ezenkívül megtekintheti az összes olyan tevékenységet, amely nincs hozzárendelve egy adott kapcsolattartóhoz, ha kiválasztja a Kapcsolattartóhoz **nem hozzárendelt tevékenységek lehetőséget**.

   :::image type="content" source="media/Contact_Activities3.png" alt-text="A kapcsolattartói szintű tevékenységekhez elérhető szűrési lehetőségek.":::

[!INCLUDE [footer-include](includes/footer-banner.md)]
