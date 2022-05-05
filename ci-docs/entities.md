---
title: Entitások és adathalmazok
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
ms.openlocfilehash: c1094bc2f6d137087b317ed20d0615289d6f1187
ms.sourcegitcommit: b7dbcd5627c2ebfbcfe65589991c159ba290d377
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/27/2022
ms.locfileid: "8642698"
---
# <a name="entities-in-customer-insights"></a>Entitások a Customer Insights szolgáltatásban

Az [adatforrások konfigurálását követően nyissa](data-sources.md) meg az **Entitások** oldalt, és értékelje a beolvasott adatok minőségét. Az entitások adathalmazoknak számítanak. A Dynamics 365 Customer Insights több funkciója ezekre az entitásokra van építve. Az eredmények alapos áttekintése segítséget nyújt a lehetőségek kimenetének ellenőrzésében.

Az **Entitások** lap felsorolja az entitásokat, és a következő oszlopokat tartalmazza:

- **Név**: Az adat entitás neve. Ha az entitás neve mellett egy figyelmeztető szimbólum látható, az azt jelenti, hogy az adott entitáshoz tartozó adatok nem töltődtek be sikeresen.
- **Forrás**: Az entitást lenyelő adatforrás típusa.
- **Frissítve**: Az entitás utolsó frissítésének időpontja.
- **Állapot**: Az entitás utolsó frissítésének részletei.

[!INCLUDE [progress-details-include](includes/progress-details-pane.md)]

## <a name="explore-a-specific-entitys-data"></a>Adott entitás adatainak feltárása

1. Nyissa meg a **DataEntities** > **oldalt**.
1. **Az Entitások** lapon jelöljön ki egy entitást a részletek lap megnyitásához.  
1. Fedezze fel az entitáshoz tartozó különböző mezőket és rekordokat.

- Az **Attribútumok** lap alapértelmezés szerint ki van választva, és megjelenik rajta egy táblázat, amelyben áttekinthetők a kiválasztott entitás részletei (például a mezőnevek vagy az adattípusok). A **Típus** oszlop a Common Data Modelhez társított típusokat jeleníti meg, amelyeket vagy a rendszer automatikusan azonosít, vagy a felhasználók [kézzel leképeznek](map-entities.md). Ezek a típusok olyan szemantikus típusok, amelyek eltérhetnek az attribútumok adattípusaitól. Az alábbi mezőben az *E-mail* mezőben van *Szöveg* adattípus, de a (szemantikus) Common Data Model típus lehet *E-mail* vagy *EmailAddress*.

> [!div class="mx-imgBorder"]
> ![Mezők tábla.](media/data-manager-entities-fields.PNG "Mezők tábla")

> [!NOTE]
> Ezen az oldalon csak az entitás adatainak mintája látható. A teljes adatkészlet megtekintéséhez lépjen az **Adatforrások** lapra, jelöljön ki egy entitást, válassza a Szerkesztés **lehetőséget**, majd tekintse meg az entitás adatait a szerkesztővel az Power Query Adatforrások [című témakörben](data-sources.md) leírtak szerint.

Ha többet szeretne megtudni az entitásban lévő adatokról, akkor az **Összesítés** oszlop az adatokra vonatkozó néhány fontos jellemzőt tartalmaz az adatokról, például a nullák, a hiányzó értékek, az egyedi értékek, a számlálók és a disztribúciók, az Ön adatai szerint. Az adatok összegzésének megjelenítéséhez válassza ki a diagram ikont.

> [!div class="mx-imgBorder"]
> ![Összegzés szimbólum.](media/data-manager-entities-summary.png "Adatok összesítése tábla")

- Az **Adatok** lapon megjelenik az entitás egyéni rekordjainak részleteit tartalmazó táblázat. A felsorolt adatok az entitás adattípusától függenek.

> [!div class="mx-imgBorder"]
> ![Entitás kiválasztása](media/data-manager-entities-data.png "Entitás kiválasztása")

- A **Jelentések** lap (amely egyes entitások esetében elérhető) lehetővé teszi az adatok megjelenítését jelentés létrehozásával, és a következő oszlopokat tartalmazza:

  - **Jelentés neve**: A jelentés neve.
  - **Készítette**: Az entitást létrehozó személy neve.
  - **Létrehozva**: Az entitás létrehozásának dátuma és időpontja.
  - **Szerkesztette**: Az entitást módosító személy neve.
  - **Szerkesztette**: Az entitás módosításának dátuma és időpontja. 

## <a name="entity-specific-information"></a>Entitásspecifikus információk

A következő rész egyes rendszer által létrehozott entitásokkal kapcsolatos információkat tartalmaz.

### <a name="corrupted-data-sources"></a>Sérült adatforrások

A betöltött adatforrásból származó mezők sérült adatokat tartalmazhatnak. A sérült mezőket tartalmazó rekordok láthatóak a rendszer által létrehozott entitások között. A sérült rekordok ismerete segít azonosítani, hogy mely adatokat kell átnézni és frissíteni a forrásrendszerben. Az adatforrás következő frissítésekor a kijavított bejegyzéseket a Customer Insights alkalmazásba be lesznek töltve és tovább lesznek küldve a későbbi folyamatoknak. 

Például egy "születési" oszlop adattípusának beállítása "dátum". Egy ügyfélrekord ban a születésnap értéke „01/01/19777”. A rendszer sérültként jelöli meg a bejegyzést. Most már valaki át tudja változtatni a forrásrendszerben az 1977-re a születésnapot. Az adatforrások automatikus frissítését követően a mező most már érvényes formátumban van, és a rekord törlődik a sérült entitásból. 

Nyissa meg az **Adatok** > **Entitások** lehetőséget és keressen sérült entitásokat a **Rendszer** szakaszban. Sérült entitások elnevezési sémája: "DataSourceName_EntityName_corrupt". Válasszon ki egy sérült entitást az összes sérült mező és az ok azonosításához az egyes bejegyzések szintjén.
> [!div class="mx-imgBorder"]
> ![Korrupciós ok.](media/corruption-reason.png "Korrupciós ok")

A Customer Insights továbbra is feldolgozza a sérült rekordokat. Ezek azonban problémákat okozhatnak a egyesített adatokkal való munka során.

A következő ellenőrzések a betöltött adatokon futnak a sérült bejegyzések felfedése érdekében: 

- A mező értéke nem egyezik meg az oszlopa adattípusával.
- A mezők olyan karaktereket tartalmaznak, amelyek hatására az oszlopok nem egyeznek meg a várt sémával. Például: nem megfelelően formázott idézőjelek, lezáratlan idézőjelek, vagy újsor karakterek.
- Ha vannak datetime/date/datetimeoffset oszlopok, a formátumukat meg kell adni a modellben, ha nem követi a szabványos ISO formátumot.


[!INCLUDE [footer-include](includes/footer-banner.md)]
