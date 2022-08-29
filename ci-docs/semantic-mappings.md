---
title: Szemantikai leképezések (előzetes verzió)
description: A szemantikus leképezések és használatuk áttekintése.
ms.date: 08/12/2022
ms.subservice: audience-insights
ms.reviewer: v-wendysmith
ms.topic: conceptual
author: CadeSanthaMSFT
ms.author: cadesantha
manager: shellyha
searchScope:
- ci-semantic-mapping
- customerInsights
ms.openlocfilehash: 8780c11c8b091717349f0fd75a36b99c3a63ab49
ms.sourcegitcommit: 267c317e10166146c9ac2c30560c479c9a005845
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/16/2022
ms.locfileid: "9303879"
---
# <a name="semantic-mappings-preview"></a>Szemantikai leképezések (előzetes verzió)

> [!NOTE]
> A **szemantikai leképezések** oldal csak olyan üzleti környezetekben (B-től B-ig) érhető el, ahol a kapcsolatprofilok már létrejöttek ezen az oldalon. A szemantikai leképezések oldalon továbbra is létrehozhatja és kezelheti az **egyes kapcsolattartói profilokat**. Vagy egyesítse a kapcsolattartási adatokat [az](data-unification-contacts.md) ismétlődések eltávolításához, azonosítsa az entitások közötti egyezéseket, és hozzon létre egy egységes kapcsolattartási profilt. Ezután az egyesített kapcsolattartói profil segítségével kapcsolattartói szintű tevékenységeket hozhat létre.

A szemantikus leképezések segítségével előre definiált sémákra leképezi a nem tevékenységekhez szükséges adatokat. Ezek a sémák segítenek a Customer Insightsnak jobban megérteni az adatattribútumokat. A szemantikai leképezés és a megadott adatok új betekintést és funkciókat tesznek lehetővé a Customer Insights szolgáltatásban. A tevékenységadatok sémákra való leképezéséhez tekintse át a [tevékenységek](activities.md) dokumentációját.

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

[!INCLUDE [footer-include](includes/footer-banner.md)]
