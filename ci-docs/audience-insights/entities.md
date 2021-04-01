---
title: Entitások és adathalmazok
description: Adatok megtekintése az Entitások lapon.
ms.date: 04/16/2020
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: mukeshpo
ms.author: mukeshpo
manager: shellyha
ms.openlocfilehash: 383523bad5105e08e57758838e90a49e805b5f9b
ms.sourcegitcommit: bae40184312ab27b95c140a044875c2daea37951
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/15/2021
ms.locfileid: "5596410"
---
# <a name="entities-in-audience-insights"></a>Entitások a célközönség-információkban

Az [adatforrások konfigurálását követően nyissa](data-sources.md) meg az **Entitások** oldalt, és értékelje a beolvasott adatok minőségét. Az entitások adathalmazoknak számítanak. A Dynamics 365 Customer Insights több funkciója ezekre az entitásokra van építve. Az eredmények alapos áttekintése segítséget nyújt a lehetőségek kimenetének ellenőrzésében.

Az **Entitások** lap felsorolja az entitásokat, és több oszlopot is tartalmaz:

- **Név**: Az adatentitás neve. Ha az entitás neve mellett egy figyelmeztető szimbólum látható, az azt jelenti, hogy az adott entitáshoz tartozó adatok nem töltődtek be sikeresen.
- **Forrás**: Az adatforrás típusa, amely be lett olvasva az entitásba
- **Létrehozta**: Az entitást létrehozó személy neve
- **Létrehozva**: Az entitás létrehozásának dátuma és időpontja
- **Frisítette**: Az entitást frissítő személy neve
- **Legutóbbi frissítés**: Az entitás utolsó módosításának dátuma és időpontja
- **Legutóbbi frissítés**: Az utolsó adatfrissítés dátuma és időpontja

## <a name="exploring-a-specific-entitys-data"></a>Adott entitás adatainak feltárása

Jelöljön ki egy entitást az adott entitáshoz tartozó különböző mezők és bejegyzések feltáráshoz.

> [!div class="mx-imgBorder"]
> ![Válasszon entitást](media/data-manager-entities-data.png "Válasszon ki egy entitást!")

- Az **Adatok** lap alapértelmezés szerint be van jelölve, és az entitás egyes bejegyzéseire vonatkozó adatokat tartalmazó táblázatot jelenít meg.

> [!div class="mx-imgBorder"]
> ![Mezők tábla](media/data-manager-entities-fields.PNG "Mezők tábla")

- A **Mezők** lapon látható egy táblázat, amely a kijelölt entitás adatainak, például mezőnevek, adattípusok és típusok áttekintésére szolgál. A **Típus** oszlop a Common Data Modelhez társított típusokat jeleníti meg, amelyeket vagy a rendszer automatikusan azonosít, vagy a felhasználók [kézzel leképeznek](map-entities.md). Ezek olyan szemantikai típusok, amelyek eltérhetnek az attribútumok adattípusaitól – például az alábbi *Ee-mail* mező adattípusa *Szöveg*, de (szemantikai) Common Data Model típusa lehet *E-mail* vagy *EmailAddress*.

> [!NOTE]
> Mindkét tábla csak az entitás adatainak mintáját jeleníti meg. Ha meg szeretné tekinteni a teljes adatkészlet, nyissa meg az **Adatforrások** oldalt, jelöljön kiegy entitást, válassza a **Szerkesztés** lehetőséget, majd tekintse meg az entitás adatait aPower Query-szerkesztővel, amint az az [Adatforrásokban](data-sources.md) látható.

Ha többet szeretne megtudni az entitásban lévő adatokról, akkor az **Összesítés** oszlop az adatokra vonatkozó néhány fontos jellemzőt tartalmaz az adatokról, például a nullák, a hiányzó értékek, az egyedi értékek, a számlálók és a disztribúciók, az Ön adatai szerint.

Az adatok összegzésének megjelenítéséhez válassza ki a diagram ikont.

> [!div class="mx-imgBorder"]
> ![Összegzés szimbólum](media/data-manager-entities-summary.png "Adatok összesítése tábla")

### <a name="next-step"></a>Következő lépés

Tekintse meg az [Egyesítés](data-unification.md) témakör, azzal kapcsolatosan, hogy hogyan lehet *leképezni*, *egyeztetni* és *egyesíteni* a leképezett adatokat.


[!INCLUDE[footer-include](../includes/footer-banner.md)]