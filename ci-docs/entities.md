---
title: Entitások a Customer Insights szolgáltatásban
description: Adatok megtekintése az Entitások lapon.
ms.date: 12/06/2021
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: conceptual
author: mukeshpo
ms.author: mukeshpo
manager: shellyha
searchScope:
- ci-entities
- customerInsight
ms.openlocfilehash: 0beaa46d47545ac195ced876b509dfc57821bfaf
ms.sourcegitcommit: ad74ace653db9a25fce4343adef7db1c9b0d8904
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/21/2022
ms.locfileid: "9183560"
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

## <a name="entity-specific-information"></a>Entitásspecifikus információk

A következő rész egyes rendszer által létrehozott entitásokkal kapcsolatos információkat tartalmaz.

### <a name="corrupted-data-sources"></a>Sérült adatforrások

A betöltött adatforrásból származó mezők sérült adatokat tartalmazhatnak. A sérült mezőket tartalmazó rekordok láthatóak a rendszer által létrehozott entitások között. A sérült rekordok ismerete segít azonosítani, hogy mely adatokat kell átnézni és frissíteni a forrásrendszerben. Az adatforrás következő frissítésekor a kijavított bejegyzéseket a Customer Insights alkalmazásba be lesznek töltve és tovább lesznek küldve a későbbi folyamatoknak. 

Például egy "születési" oszlop adattípusának beállítása "dátum". Egy ügyfélrekord ban a születésnap értéke „01/01/19777”. A rendszer sérültként jelöli meg a bejegyzést. Most már valaki át tudja változtatni a forrásrendszerben az 1977-re a születésnapot. Az adatforrások automatikus frissítését követően a mező most már érvényes formátumban van, és a rekord törlődik a sérült entitásból.

Nyissa meg az **Adatok** > **Entitások** lehetőséget és keressen sérült entitásokat a **Rendszer** szakaszban. Sérült entitások elnevezési sémája: "DataSourceName_EntityName_corrupt". Válasszon ki egy sérült entitást a sérült mezők és az ok azonosításához az egyes rekordok szintjén.

   :::image type="content" source="media/corruption-reason.png" alt-text="Korrupciós ok.":::

A Customer Insights továbbra is feldolgozza a sérült rekordokat. Ezek azonban problémákat okozhatnak a egyesített adatokkal való munka során.

A következő ellenőrzések a betöltött adatokon futnak a sérült bejegyzések felfedése érdekében:

- A mező értéke nem egyezik meg az oszlopa adattípusával.
- A mezők olyan karaktereket tartalmaznak, amelyek hatására az oszlopok nem egyeznek meg a várt sémával. Például: nem megfelelően formázott idézőjelek, lezáratlan idézőjelek, vagy újsor karakterek.
- Ha vannak datetime/date/datetimeoffset oszlopok, akkor a formátumukat meg kell adni a modellben, ha az nem követi a szabványos ISO formátumot.

[!INCLUDE [footer-include](includes/footer-banner.md)]
