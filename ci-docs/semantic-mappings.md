---
title: Szemantikai leképezések (előzetes verzió)
description: A szemantikus leképezések és használatuk áttekintése.
ms.date: 12/01/2021
ms.subservice: audience-insights
ms.reviewer: mhart
ms.topic: conceptual
author: CadeSanthaMSFT
ms.author: cadesantha
manager: shellyha
searchScope:
- ci-semantic-mapping
- customerInsights
ms.openlocfilehash: 7c9588ac7a132ca6f43cf26ea3a744109a0dd2b8
ms.sourcegitcommit: ad74ace653db9a25fce4343adef7db1c9b0d8904
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/21/2022
ms.locfileid: "9183634"
---
# <a name="semantic-mappings-preview"></a>Szemantikai leképezések (előzetes verzió)

A szemantikus leképezések segítségével előre definiált sémákra leképezi a nem tevékenységekhez szükséges adatokat. Ezek a sémák segítenek a Customer Insightsnak jobban megérteni az adatattribútumokat. A szemantikai leképezés és a megadott adatok új betekintést és funkciókat tesznek lehetővé a Customer Insights szolgáltatásban. A tevékenységadatok sémákra való leképezéséhez tekintse át a [tevékenységek](activities.md) dokumentációját.

**A szemantikus leképezések jelenleg engedélyezve vannak az üzleti partnereken alapuló környezetekhez**. *A ContactProfile* az egyetlen olyan típusú szemantikus leképezés, amely jelenleg elérhető a Customer Insights szolgáltatásban.

## <a name="define-a-contactprofile-semantic-entity-mapping"></a>A ContactProfile szemantikus entitásleképezésének definiálása

1. Lépjen az **Adatszemantikus** > **leképezések (előzetes verzió) elemre**.

1. Az irányított élmény indításhoz válassza a **Szemantikus leképezés hozzáadása** lehetőséget.

1. Az **Entitásadatok** lépésben állítsa be a következő mezők értékeit:

   - **Szemantikus entitásleképezési név**: A szemantikus entitásleképezés neve.
   - **Forrásentitás**: Kapcsolattartási adatokat tartalmazó entitás.
   - **Elsődleges kulcs**: Olyan mező, amely egyedileg azonosítja a kapcsolattartói rekordot. Nem tartalmazhat ismétlődő értékeket, üres értékeket vagy hiányzó értékeket.

   :::image type="content" source="media/Semantic_Mapping_Wizard1.png" alt-text="Állítsa be a szemantikus entitásleképezést névvel, forrásentitással és elsődleges kulcssal.":::

1. Válassza a **Következő** lehetőséget.

1. A **Kapcsolatok** lépésben konfigurálja az adatokat, hogy a kapcsolattartók adatai hozzá csatlakozzon a megfelelő partneradatokhoz. Ez a lépés az entitások közötti kapcsolatot ábrázolja.  

   Kétféle kapcsolati útvonal valósítható meg: **Közvetett kapcsolatok** és a **Közvetlen kapcsolatok**. További tájékoztatásért menjen a [közvetett és közvetlen kapcsolati elérési utakra](relationships.md#relationship-paths).

   1. Válassza a Kapcsolat **hozzáadása lehetőséget** a kapcsolat konfigurálásához.
   1. Válassza ki a forrásentitásból azt az attribútumot, amely a kapcsolattartó entitást egy másik entitáshoz kapcsolja.
   1. Válassza ki azt az entitást, amelyhez a kapcsolattartói entitást csatlakoztatnia kell. Válasszon ki egy entitást a **Számlaentitások** vagy a **Köztes entitás** szakaszból. Ha köztes entitást választ, határozzon meg egy második kapcsolatot a célfiók-entitáshoz való csatlakozáshoz.

      :::image type="content" source="media/Semantic_Mapping_Wizard2.png" alt-text="Válasszon egy Partnerentitást vagy egy Köztes entitást.":::

   1. Adja meg a **Kapcsolat nevét**. Ha az entitások között már létezik kapcsolat, a kapcsolat neve írásvédett. Ha nincs kapcsolat, akkor új kapcsolat jön létre az Ön nevével.
   1. A kapcsolat konfigurálás befejezéséhez válassza az **Alkalmaz** lehetőséget.

   > [!NOTE]
   > További kapcsolatokat konfigurálhat a kapcsolattartó entitás és a köztes entitásokkal rendelkező más partnerentitások között.
   
     :::image type="content" source="media/Semantic_Mapping_Wizard4.png" alt-text="A különböző kapcsolatok vizualizálása összeköti a kapcsolattartókat a partnerentitásokkal.":::

1. Válassza a **Következő** lehetőséget.

1. A **Szemantikus típus beállítása** lépésben válasszon **Szemantika típust**. Jelenleg egyetlen **Szemantikus típus** van, a *ContactProfile* elnevezésű.

1. Rendelje hozzá a kapcsolattartási azonosítóját a *ContactProfile* szemantikai típusú **kapcsolattartói azonosítóhoz**. Ha szükséges, képezzen le más mezőket, például utónév, vezetéknév, nemet vagy e-mailt.

   :::image type="content" source="media/Semantic_Mapping_Wizard5.png" alt-text="A kapcsolattartói adatok attribútumainak leképezhetőek a megadott kötelező és nem kötelező mezőkre.":::

1. Válassza a **Következő** lehetőséget.

1. **Az Áttekintés** lépésben tekintse át a szemantikai leképezés konfigurációját. A módosítások elvégzéséhez válassza a Szerkesztés **lehetőséget** a megfelelő szakaszhoz.

1. Válassza a **Mentés** parancsot.

1. A szemantikus leképezés feldolgozásához válassza a Futtatás **lehetőséget**. Vagy válassza a Bezárás **lehetőséget** a szemantikus leképezés feldolgozás nélküli mentéséhez. Ha később szeretné futtatni, válassza ki a szemantikai leképezést, majd válassza a Frissítés **lehetőséget**.

[!INCLUDE [progress-details-include](includes/progress-details-pane.md)]

## <a name="manage-existing-semantic-mappings"></a>A meglévő szemantikus leképezések kezelése

Az Adatszemantikai **leképezések (előzetes verzió)** > **lapon** megtekintheti a mentett szemantikai leképezéseket, azok forrásentitását, szemantikai típusát, leképezéstípusát és állapotát.

:::image type="content" source="media/semantic-mapping-options.png" alt-text="A szemantikus leképezések kezelésére vonatkozó lehetőségek.":::

Válassza ki a szemantikai leképezést az elérhető műveletek megtekintéséhez.
- **Szerkessze** az aktuális konfigurációt. A módosítások feldolgozásához válassza a **Mentés** és a **Futtatás** lehetőséget.
- **Frissítse** a szemantikai leképezést, hogy a legfrissebb adatokat tartalmazza. Egy adott szemantikus leképezés frissítése frissíti az ugyanolyan típusú összes szemantikus leképezést.
- **Nevezze át** a szemantikai leképezést. Válassza a **Mentés** parancsot.
- **Törölje** a szemantikai leképezést. Ha egyszerre több szemantikai leképezést szeretne törölni, válassza a szemantikai leképezéseket és a törlés ikont. Válassza ki az **Eltávolítás** lehetőséget a törlés megerősítéséhez.

## <a name="use-a-contactprofile-semantic-entity-mapping-to-create-contact-level-activities"></a>ContactProfile szemantikai entitásleképezés használata kapcsolattartói szintű tevékenységek létrehozásához

A ContactProfile szemantikai entitásleképezés létrehozása *után* rögzítheti a kapcsolattartók tevékenységeit. Lehetővé teszi, hogy egy fiók tevékenység-idővonalán megtekintse, hogy melyik kapcsolattartó volt felelős az egyes tevékenységekért. A legtöbb lépés a tipikus tevékenység-leképezési konfigurációt követi.

   > [!NOTE]
   > Ahhoz, hogy a kapcsolattartói szintű tevékenységek működjenek, a tevékenységadatokon belüli minden rekordhoz accountID és ContactID **attribútummal is rendelkeznie** kell.**·**

1. [Definiáljon egy *ContactProfile* szemantikai entitásleképezést,](#define-a-contactprofile-semantic-entity-mapping) és futtassa a szemantikai leképezést.

1. Lépjen az **Adattevékenységek** > **oldalra**.

1. Új tevékenység létrehozásához válassza a Tevékenység **hozzáadása lehetőséget**.

1. Nevezze el a tevékenységet, válassza ki a forrástevékenység-entitást, és válassza ki a tevékenységentitás elsődleges kulcsát.

1. **A kapcsolatok** lépésben hozzon létre közvetett kapcsolatot a tevékenységforrás adatai és a fiókok között, a kapcsolattartási adatokat köztes entitásként használva. További információ: [Közvetlen és közvetett kapcsolati útvonalak](relationships.md#relationship-paths).
   - Példa kapcsolat a Vásárlások *nevű* tevékenységre:
      - **Megvásárolja a forrástevékenységi adatok kapcsolattartási adatait** > **a** ContactID **attribútumon**
      - **Kapcsolattartási adatok** > **Fiókadatok** az AccountID **attribútumon**

   :::image type="content" source="media/Contact_Activities1.png" alt-text="Példa kapcsolatbeállításra.":::

1. A kapcsolatok beállítása után válassza a Tovább **lehetőséget**, és fejezze be a tevékenység-leképezés konfigurációját. A tevékenység létrehozásával kapcsolatos részletes lépésekért lásd: [Tevékenység](activities.md) definiálása.

1. Futtassa a tevékenységleképezéseket.

1. A kapcsolattartói szintű tevékenység-leképezés futtatása után válassza az Ügyfelek **lehetőséget**. A kapcsolattartói szintű tevékenységek az ügyfél idővonalán jelennek meg.

   :::image type="content" source="media/Contact_Activities2.png" alt-text="Végeredmény a kapcsolattartási tevékenységek konfigurálása után":::

### <a name="contact-level-activity-timeline-filtering"></a>Kapcsolattartói szintű tevékenységek idővonalának szűrése

Az ügyfelek tevékenység-idővonala tartalmazza az azonosítóikat vagy nevüket a ContactProfile *konfigurációjától függően* azokhoz a tevékenységekhez, amelyeken cselekedtek. Szűrje a tevékenységeket névjegyek szerint az idővonalon, hogy megtekinthesse az Önt érdeklő konkrét névjegyeket. Ha meg szeretné tekinteni az összes olyan tevékenységet, amely nincs hozzárendelve egy adott kapcsolattartóhoz, válassza a Nem partnerhez hozzárendelt tevékenységek **lehetőséget**.

:::image type="content" source="media/Contact_Activities3.png" alt-text="A kapcsolattartói szintű tevékenységekhez rendelkezésre álló szűrési lehetőségek érhetők el.":::

[!INCLUDE [footer-include](includes/footer-banner.md)]
