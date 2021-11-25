---
title: Entitások és adathalmazok
description: Adatok megtekintése az Entitások lapon.
ms.date: 11/01/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: mukeshpo
ms.author: mukeshpo
manager: shellyha
ms.openlocfilehash: 2a207a3dcad4bf192efb6ee1554195f10b19670b
ms.sourcegitcommit: 834651b933b1e50e7557d44f926a3fb757c1f83a
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/02/2021
ms.locfileid: "7732083"
---
# <a name="entities-in-audience-insights"></a>Entitások a célközönség-információkban

Az [adatforrások konfigurálását követően nyissa](data-sources.md) meg az **Entitások** oldalt, és értékelje a beolvasott adatok minőségét. Az entitások adathalmazoknak számítanak. A Dynamics 365 Customer Insights több képessége épül ezek köré az entitások köré. Az eredmények alapos áttekintése segítséget nyújt a lehetőségek kimenetének ellenőrzésében.

Az **Entitások** lap felsorolja az entitásokat, és több oszlopot is tartalmaz:

- **Név**: Az adatentitás neve. Ha az entitás neve mellett egy figyelmeztető szimbólum látható, az azt jelenti, hogy az adott entitáshoz tartozó adatok nem töltődtek be sikeresen.
- **Forrás**: Az adatforrás típusa, amely be lett olvasva az entitásba
- **Létrehozta**: Az entitást létrehozó személy neve
- **Létrehozva**: Az entitás létrehozásának dátuma és időpontja
- **Frissítve** : Az entitást frissített személy neve
- **Állapot** : Részletek az entitás legutóbbi frissítéséről

[!INCLUDE [progress-details-include](../includes/progress-details-pane.md)]

## <a name="explore-a-specific-entitys-data"></a>Adott entitás adatainak feltárása

Jelöljön ki egy entitást az adott entitáshoz tartozó különböző mezők és bejegyzések feltáráshoz.

> [!div class="mx-imgBorder"]
> ![Entitás kiválasztása](media/data-manager-entities-data.png "Entitás kiválasztása")

- Az **Adatok** lapon megjelenik az entitás egyéni rekordjainak részleteit tartalmazó táblázat.

> [!div class="mx-imgBorder"]
> ![Mezők tábla.](media/data-manager-entities-fields.PNG "Mezők tábla")

- Az **Attribútumok** lap alapértelmezés szerint ki van választva, és megjelenik rajta egy táblázat, amelyben áttekinthetők a kiválasztott entitás részletei (például a mezőnevek vagy az adattípusok). A **Típus** oszlop a Common Data Modelhez társított típusokat jeleníti meg, amelyeket vagy a rendszer automatikusan azonosít, vagy a felhasználók [kézzel leképeznek](map-entities.md). Ezek a típusok olyan szemantikus típusok, amelyek eltérhetnek az attribútumok adattípusaitól. Az alábbi mezőben az *E-mail* mezőben van *Szöveg* adattípus, de a (szemantikus) Common Data Model típus lehet *E-mail* vagy *EmailAddress*.

> [!NOTE]
> Mindkét tábla csak az entitás adatainak mintáját jeleníti meg. Ha meg szeretné tekinteni a teljes adatkészlet, nyissa meg az **Adatforrások** oldalt, jelöljön kiegy entitást, válassza a **Szerkesztés** lehetőséget, majd tekintse meg az entitás adatait aPower Query-szerkesztővel, amint az az [Adatforrásokban](data-sources.md) látható.

Ha többet szeretne megtudni az entitásban lévő adatokról, akkor az **Összesítés** oszlop az adatokra vonatkozó néhány fontos jellemzőt tartalmaz az adatokról, például a nullák, a hiányzó értékek, az egyedi értékek, a számlálók és a disztribúciók, az Ön adatai szerint.

Az adatok összegzésének megjelenítéséhez válassza ki a diagram ikont.

> [!div class="mx-imgBorder"]
> ![Összegzés szimbólum.](media/data-manager-entities-summary.png "Adatok összesítése tábla")

## <a name="entity-specific-information"></a>Entitásspecifikus információk

A következő rész egyes rendszer által létrehozott entitásokkal kapcsolatos információkat tartalmaz.

### <a name="corrupted-data-sources"></a>Sérült adatforrások

A betöltött adatforrásból származó mezők sérült adatokat tartalmazhatnak. A sérült mezőket tartalmazó rekordok láthatóak a rendszer által létrehozott entitások között. A sérült rekordok ismerete segít azonosítani, hogy mely adatokat kell átnézni és frissíteni a forrásrendszerben. Az adatforrás következő frissítésekor a kijavított bejegyzéseket a Customer Insights alkalmazásba be lesznek töltve és tovább lesznek küldve a későbbi folyamatoknak. 

Például egy "születési" oszlop adattípusának beállítása "dátum". Egy ügyfélrekord ban a születésnap értéke „01/01/19777”. A rendszer sérültként jelöli meg a bejegyzést. Most már valaki át tudja változtatni a forrásrendszerben az 1977-re a születésnapot. Az adatforrások automatikus frissítését követően a mező most már érvényes formátumban van, és a rekord törlődik a sérült entitásból. 

Nyissa meg az **Adatok** > **Entitások** lehetőséget és keressen sérült entitásokat a **Rendszer** szakaszban. Sérült entitások elnevezési sémája: "DataSourceName_EntityName_corrupt".

A Customer Insights továbbra is feldolgozza a sérült rekordokat. Ezek azonban problémákat okozhatnak a egyesített adatokkal való munka során.

A következő ellenőrzések a betöltött adatokon futnak a sérült bejegyzések felfedése érdekében: 

- A mező értéke nem egyezik meg az oszlopa adattípusával.
- A mezők olyan karaktereket tartalmaznak, amelyek hatására az oszlopok nem egyeznek meg a várt sémával. Például: nem megfelelően formázott idézőjelek, lezáratlan idézőjelek, vagy újsor karakterek.
- Ha vannak datetime/date/datetimeset oszlopok, akkor azok formátumát meg kell adni a modellben, ha az nem követik a szabványos ISO formátumot.



[!INCLUDE[footer-include](../includes/footer-banner.md)]
