---
title: Entitások a Customer Insights szolgáltatásban
description: Adatok megtekintése az Entitások lapon.
ms.date: 08/04/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: conceptual
author: mukeshpo
ms.author: mukeshpo
manager: shellyha
searchScope:
- ci-entities
- customerInsight
ms.openlocfilehash: e365945b27e7c985ca5371c6b72619610b6f3af1
ms.sourcegitcommit: be341cb69329e507f527409ac4636c18742777d2
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/30/2022
ms.locfileid: "9610101"
---
# <a name="entities-in-customer-insights"></a>Entitások a Customer Insights szolgáltatásban

Az [adatforrások konfigurálását követően nyissa](data-sources.md) meg az **Entitások** oldalt, és értékelje a beolvasott adatok minőségét. Az entitások adathalmazoknak számítanak. A Dynamics 365 Customer Insights több funkciója ezekre az entitásokra van építve. Az eredmények alapos áttekintése segítséget nyújt a lehetőségek kimenetének ellenőrzésében.

Miközben a Customer Insights szolgáltatásban dolgozik, amely gazdagítja az adatait, vagy szegmenseket, mértékeket és tevékenységeket hoz létre, az ezekből a műveletekből létrehozott entitások az Entitások **lapon jelennek meg**.

## <a name="view-a-list-of-entities"></a>Entitások listájának megtekintése

Az **Adatentitások** > **elemre kattintva** megtekintheti az entitások listáját. A következő információk jelennek meg az egyes entitások esetében.

- **Név**: Az adatentitás neve. Ha az entitás neve mellett egy figyelmeztető szimbólum látható, az azt jelenti, hogy az adott entitáshoz tartozó adatok nem töltődtek be sikeresen.
- **Forrás**: Az entitást betöltő adatforrás típusa.
- **Frissítve**: Az entitás utolsó frissítésének időpontja.
- **Állapot**: Az entitás legutóbbi frissítésének részletei.

## <a name="explore-a-specific-entitys-data"></a>Adott entitás adatainak feltárása

1. Lépjen az Adatentitások **elemre** > **·**.
1. Válasszon ki egy entitást a részletek oldal megnyitásához.  
1. Fedezze fel az adott entitáshoz tartozó különböző mezőket és rekordokat.

- Az **Attribútumok** lap alapértelmezés szerint be van jelölve, és a kiválasztott entitás részleteit jeleníti meg, például mezőneveket, adattípusokat és típusokat. A **Típus** oszlop a Common Data Modelhez társított típusokat jeleníti meg, amelyeket vagy a rendszer automatikusan azonosít, vagy a felhasználók [kézzel leképeznek](map-entities.md). Ezek a típusok olyan szemantikus típusok, amelyek eltérhetnek az attribútumok adattípusaitól. Az alábbi E-mail mező például *karakterlánc* adattípusú *, de a (szemantikai) Common Data Model típusa lehet* Email *,* EmailAddress *vagy* Identity.Service.Email *.*

   :::image type="content" source="media/data-manager-entities-fields.png" alt-text="Mezők tábla.":::

   > [!NOTE]
   > Ez az oldal csak az entitás adatainak egy mintáját jeleníti meg. A teljes adatkészlet megtekintéséhez lépjen az **Adatforrások** lapra, válasszon ki egy entitást, válassza a Szerkesztés **lehetőséget**, majd tekintse meg az entitás adatait a szerkesztővel az Power Query Adatforrások [részben](data-sources.md) leírtak szerint.

   Ha többet szeretne megtudni az entitásban betöltött adatokról, az **Összegzés** oszlop néhány fontos adatjellemzőt tartalmaz, például null értékeket, hiányzó értékeket, egyedi értékeket, darabszámokat és eloszlásokat, függetlenül attól, hogy az adatokra vonatkozik-e. Az adatok összegzésének megjelenítéséhez válassza ki a diagram ikont.

   :::image type="content" source="media/data-manager-entities-summary.png" alt-text="Adatösszesítő táblázat.":::

- Az **Adatok** lap az entitás egyes rekordjainak részleteit jeleníti meg. A felsorolt részletek az entitás adattípusától függenek.

   :::image type="content" source="media/data-manager-entities-data.png" alt-text="Entitás kiválasztása":::

- A **Jelentések** lap (amely egyes entitások számára elérhető) lehetővé teszi az adatok megjelenítését egy jelentés létrehozásával, amely a következő oszlopokat tartalmazza:

  - **Jelentés neve**: A jelentés neve.
  - **Létrehozta**: Annak a személynek a neve, aki létrehozta az entitást.
  - **Létrehozva**: Az entitás létrehozásának dátuma és időpontja.
  - **Szerkesztette**: Annak a személynek a neve, aki módosította az entitást.
  - **Szerkesztve**: Az entitás módosításának dátuma és időpontja.

[!INCLUDE [footer-include](includes/footer-banner.md)]
