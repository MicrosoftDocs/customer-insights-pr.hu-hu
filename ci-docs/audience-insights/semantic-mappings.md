---
title: Szemantikai leképezések (előzetes verzió)
description: A szemantikus leképezések és használatuk áttekintése.
ms.date: 12/01/2021
ms.service: customer-insights
ms.subservice: audience-insights
ms.reviewer: mhart
ms.topic: conceptual
author: CadeSanthaMSFT
ms.author: cadesantha
manager: shellyha
ms.openlocfilehash: 08b257b97704b219bb3277042516e00deb886a49
ms.sourcegitcommit: 58651d33e0a7d438a2587c9ceeaf7ff58ae3b648
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/02/2021
ms.locfileid: "7881833"
---
# <a name="semantic-mappings-preview"></a>Szemantikai leképezések (előzetes verzió)

A szemantikus leképezések segítségével előre definiált sémákra leképezi a nem tevékenységekhez szükséges adatokat. Ezek a sémák segítenek a célközönségnek, hogy jobban megértse az adatattribútumokat. A szemantikus leképezés és a megadott adatok engedélyezik az új információkat és szolgáltatásokat a célközönséggel kapcsolatos információkban. A tevékenységadatok sémákra való leképezéséhez tekintse át a [tevékenységek](activities.md) dokumentációját.

**A szemantikus leképezések jelenleg engedélyezve vannak az üzleti partnereken alapuló környezetekhez**. A *ContactProfile* az egyetlen szemantikus leképezés, amely jelenleg elérhető a célközönséggel kapcsolatos információk szolgáltatásban.

## <a name="define-a-contactprofile-semantic-entity-mapping"></a>A ContactProfile szemantikus entitásleképezésének definiálása

1. Az célközönség információkért tekintse meg az **Adat** > **Szementikai leképezések (előzetes verzió)** megtekintését.

1. Az irányított élmény indításhoz válassza a **Szemantikus leképezés hozzáadása** lehetőséget.

1. Az **Entitásadatok** lépésben állítsa be a következő mezők értékeit:

   - **Szemantikus entitásleképezés neve**: Adja meg a szemantikus entitásleképezés nevét.
   - **Forrásentitás**: Válassza ki a kapcsolattartói adatokat tartalmazó entitást.
   - **Elsődleges kulcs**: Válassza ki azt a mezőt, amely egyértelműen azonosítja a kapcsolattartói rekordot. Nem tartalmazhat ismétlődő értékeket, üres értékeket vagy hiányzó értékeket.

   :::image type="content" source="media/Semantic_Mapping_Wizard1.png" alt-text="Állítsa be a szemantikus entitásleképezést névvel, forrásentitással és elsődleges kulcssal.":::

1. A folytatáshoz válassza a **Tovább** lehetőséget.

1. A **Kapcsolatok** lépésben konfigurálja az adatokat, hogy a kapcsolattartók adatai hozzá csatlakozzon a megfelelő partneradatokhoz. Ez a lépés az entitások közötti kapcsolatot ábrázolja.  

   Kétféle kapcsolati útvonal valósítható meg: **Közvetett kapcsolatok** és a **Közvetlen kapcsolatok**. További tájékoztatásért menjen a [közvetett és közvetlen kapcsolati elérési utakra](relationships.md#relationship-paths).

   1. Válassza a **Kapcsolat hozzáadása** a kapcsolat beállításához.
   1. Válassza ki a forrásentitásból azt az attribútumot, amely a kapcsolattartó entitást egy másik entitáshoz kapcsolja.
   1. Válassza ki azt az entitást, amelyhez a kapcsolattartói entitást csatlakoztatnia kell. A **Partnerentitások** vagy a **Köztes entitás** szakaszban választhat entitást. Ha köztes entitást választ ki, akkor egy második kapcsolatot is meg kell határoznia a célpartner-entitáshoz való kapcsolódáshoz.

      :::image type="content" source="media/Semantic_Mapping_Wizard2.png" alt-text="Válasszon egy Partnerentitást vagy egy Köztes entitást.":::

   1. Adja meg a **Kapcsolat nevét**. Ha az entitások között már létezik kapcsolat, a kapcsolat neve írásvédett. Ha nincs kapcsolat, akkor új kapcsolat jön létre az Ön nevével.
   1. A kapcsolat konfigurálás befejezéséhez válassza az **Alkalmaz** lehetőséget.

   > [!NOTE]
   > További kapcsolatokat konfigurálhat a kapcsolattartó entitás és a köztes entitásokkal rendelkező más partnerentitások között.
   >  :::image type="content" source="media/Semantic_Mapping_Wizard4.png" alt-text="A különböző kapcsolatok vizualizálása összeköti a kapcsolattartókat a partnerentitásokkal.":::

1. Válassza a **Tovább** lehetőséget, amikor végzett a kapcsolatkonfigurációval.

1. A **Szemantikus típus beállítása** lépésben válasszon **Szemantika típust**. Jelenleg egyetlen **Szemantikus típus** van, a *ContactProfile* elnevezésű.

1. Térképezze le adatait a *ContactProfile* **Szemantikai típusához** a megjelenített mezőkhöz.
   - Kötelező mező: Kapcsolattartó azonosítója
   - Nem kötelező mezők: utónév, vezetéknév, születési dátum, nem, elsődleges e-mail és elsődleges telefon

   :::image type="content" source="media/Semantic_Mapping_Wizard5.png" alt-text="A kapcsolattartói adatok attribútumainak leképezhetőek a megadott kötelező és nem kötelező mezőkre.":::

1. A folytatáshoz válassza a **Tovább** lehetőséget.

1. Az **Áttekintés** lépésben vizsgálja meg a szemantikus leképezés konfigurációját. A módosításokhoz válassza a **Szerkesztés** lehetőséget a megfelelő szakaszhoz.

1. Az új **Szemantikus leképezés** mentéshez válassza a **Mentés** lehetőséget.

1. A mentés után választhatja a szemantikus leképezés **Futtatása** lehetőséget, illetve a **Bezárás** lehetőséget is, ha feldolgozás nélkül menti a szemantikus leképezést.

1. Ha később szemantikus leképezést kell futtatnia, válassza ki a szemantikus leképezést, majd válassza a **Frissítés** lehetőséget.

[!INCLUDE [progress-details-include](../includes/progress-details-pane.md)]

## <a name="manage-existing-semantic-mappings"></a>A meglévő szemantikus leképezések kezelése

Az **Adat** > **Szemantikus leképezésekben (előzetes verzió)** megtekintheti az összes mentett szemantikus leképezést, és kezelheti azokat. Minden szemantikus leképezést külön sor képvisel. Részletes információkat talál a forrásentitásról, a szemantikus típusról, a leképezés típusáról és állapotáról.

:::image type="content" source="media/semantic-mapping-options.png" alt-text="A szemantikus leképezések kezelésére vonatkozó lehetőségek.":::

- **Szerkesztés**: Megnyitja a szemantikus leképezés konfigurációját a vélemény lépésben. Az aktuális konfiguráció megváltoztatható. A módosítások feldolgozásához válassza a **Mentés** és a **Futtatás** lehetőséget.

- **Frissítés**: Frissíti a kiválasztott szemantikus leképezést a konfiguráció részét képezi az entitások legfrissebb adataival. Egy adott szemantikus leképezés frissítése frissíti az ugyanolyan típusú összes szemantikus leképezést.

- **Átnevezés**: Megnyit egy párbeszédpanelt, ahol másik nevet is megadhatja a kiválasztott szemantikus leképezés számára. Válassza a **Mentés** lehetőséget a módosítások alkalmazásához.

- **Törlés**: Párbeszéd megnyitása a kijelölt szemantikus leképezés törlésének megerősítése érdekében. Egyszerre több szemantikus leképezést is törölhet a szemantikus leképezések és a törlés ikon kiválasztásával. Válassza ki az **Eltávolítás** lehetőséget a törlés megerősítéséhez.

## <a name="use-a-contactprofile-semantic-entity-mapping-to-create-contact-level-activities"></a>Kapcsolatprofile szemantikai entitásleképezés használata kapcsolatszintű tevékenységek létrehozásához

A *ContactProfile* szemantikai entitásleképezés létrehozása után rögzítheti a névjegyek tevékenységeit. Lehetővé teszi, hogy egy olyan fiók tevékenységi idővonalában láthassa, hogy melyik kapcsolattartó volt felelős az egyes tevékenységekért. A legtöbb lépés a tipikus tevékenységleképezési konfigurációt követi.

   > [!NOTE]
   > Ahhoz, hogy a kapcsolattartói szintű tevékenységek működjenek, **a** tevékenységadatokon belül minden rekordhoz AccountID és **ContactID attribútumokkal kell** rendelkeznie.

1. [*Kapcsolatprofile* szemantikai entitásleképezés definiálása.](#define-a-contactprofile-semantic-entity-mapping) és futtassa a szemantikai leképezést.

1. A célközönség információin belül nyissa meg a következőt: **Adatok** > **Tevékenységek**.

1. Új tevékenység létrehozásához válassza **a Tevékenység hozzáadása** lehetőséget.

1. Nevezze meg a tevékenységet, jelölje ki a forrástevékenység-entitást, és válassza ki a tevékenység entitás elsődleges kulcsát.

1. A **kapcsolatok** lépésben közvetett kapcsolatot hozhat létre a tevékenységforrás-adatok és a fiókok között, a kapcsolattartási adatokat közvetítő entitásként használva. További információ: [Közvetlen és közvetett kapcsolati útvonalak](relationships.md#relationship-paths).
   - Példakapcsolat a Vásárlások nevű *tevékenységhez*:
      - **Beszerzési forrástevékenység adatai** > **Kapcsolatfelvételi adatok** a ContactID **attribútumon**
      - **Kapcsolati adatok** > **fiókadatai** az AccountID **attribútumon**

   :::image type="content" source="media/Contact_Activities1.png" alt-text="Példa kapcsolatbeállításra.":::

1. A kapcsolatok beállítása után válassza a Tovább lehetőséget, **és fejezze be a** tevékenységleképezési konfigurációt. A tevékenység létrehozásával kapcsolatos részletes lépésekért lásd: [Tevékenység definiálása](activities.md).

1. Futtassa a tevékenységleképezéseket.

1. A partneri szintű tevékenységek mostantól láthatók lesznek az ügyfél idővonalán.

   :::image type="content" source="media/Contact_Activities2.png" alt-text="Végeredmény a kapcsolattartási tevékenységek konfigurálása után":::

### <a name="contact-level-activity-timeline-filtering"></a>Kapcsolattartó szintű tevékenység idővonalának szűrése

A partnerszintű tevékenységleképezés konfigurálása és futtatása után az ügyfelek tevékenységi ütemterve frissül. Ez magában foglalja az ön által végzett tevékenységekhez adott adat- vagy nevüket *a ContactProfile* konfigurációjától függően. Szűrheti a tevékenységeket az idővonal névjegyei szerint, hogy megtekinthesse az Önt érdeklő névjegyeket. Ezenkívül megtekintheti az összes olyan tevékenységet, amely nincs hozzárendelve egy adott partnerhez, ha a **Nem partnerhez leképezett tevékenységek lehetőséget** választja.

   :::image type="content" source="media/Contact_Activities3.png" alt-text="A partnerszintű tevékenységek szűrési beállításai.":::

[!INCLUDE[footer-include](../includes/footer-banner.md)]
