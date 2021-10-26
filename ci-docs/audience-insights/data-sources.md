---
title: Adatforrások kiválasztása adatok betöltéséhez
description: Megismerkedhet vele, hogyan importálhat különböző forrásokból származó adatokat.
ms.date: 04/12/2021
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: adkuppa
ms.author: adkuppa
ms.reviewer: mhart
manager: shellyha
ms.custom: intro-internal
ms.openlocfilehash: de31e1f25c08d0bcb5341c5f465b1999de48acf3
ms.sourcegitcommit: 53b133a716c73cb71e8bcbedc6273cec70ceba6c
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/15/2021
ms.locfileid: "7645358"
---
# <a name="data-sources-overview"></a>Adatforrások áttekintése

[!INCLUDE [cc-data-platform-banner](../includes/cc-data-platform-banner.md)]

A célközönség-információk funkció a Dynamics 365 Customer Insights szolgáltatásban összekapcsolja az adatokat források széles köréből. A adatforrások összeskapcsolását gyakran nevezik *adatbetöltésnek*. Az adatok betöltése után [egyesítheti](data-unification.md) és műveleteket hajthat végre rajtuk.

## <a name="add-a-data-source"></a>Adatforrás felvétele

A kiválasztott lehetőségtől függően olvassa el a részletes cikkeket az adatforrás hozzáadásáról.

A adatforrások három fő módon adhatók hozzá:

- [Több tucat Power Query-összekötőn keresztül](connect-power-query.md)
- [Common Data Model-mappából](connect-common-data-model.md)
- [Saját Microsoft Dataverse tóból](connect-dataverse-managed-lake.md)

## <a name="add-data-from-on-premises-data-sources"></a>Adatok hozzáadása helyszíni adatforrásokból

A célközönségi elemzésekben az adatok betöltése a helyi adatforrásokból a Microsoft Power Platform adatfolyamok alapján támogatott. A Customer Insightsban úgy engedélyezhetők az adatfolyamok, ha a környezet beállításakor [meg van adva a Microsoft Dataverse környezet URL-címe](create-environment.md).

A Dataverse környezet Customer Insights-cal való társítása után létrehozott adatforrások alapértelmezés szerint [Power Platform adatfolyamokat](/power-query/dataflows/overview-dataflows-across-power-platform-dynamics-365) fognak használni. Az adatfolyamok az adatátjáró használatával támogatják a helyszíni összekapcsolhatóságot. Távolítsa el, majd hozza létre újból az adatforrásokat, amelyek azelőtt léteztek, hogy a Dataverse-környezet társítva lett volna [a helyszíni adatátjárók használatára](/data-integration/gateway/service-gateway-app).

A meglévő Power BI vagy Power Apps környezet adatátjárói láthatók lesznek, és újra felhasználhatók a Customer Insightsban. Az adatforrások oldalon olyan Microsoft Power Platform környezetbe mutató hivatkozások láthatók, ahol megtekintheti és konfigurálhatja a helyszíni adatátjárókat.

## <a name="review-ingested-data"></a>A betöltött adatok áttekintése

Látni fogja az egyes betöltött adatforrások nevét, állapotát, valamint az adatoknak az adott forrásra vonatkozó utolsó frissítését. Az adatforrások listáját minden oszlop szerint rendezheti.

> [!div class="mx-imgBorder"]
> ![Adatforrás hozzáadva.](media/configure-data-datasource-added.png "Adatforrás hozzáadva")

|Státusz  |Ismertetés  |
|---------|---------|
|Sikerült   |A adatforrás betöltése sikeres volt, ha egy idő szerepel a **Frissített** oszlopban.
|Nem kezdődött el   |Az adatforrás még nem tartalmaz adatokat vagy még vázlat módban van.         |
|Frissítés    |Az adatbetöltés folyamatban van. A művelet a **Műveletek** oszlop **Frissítés leállítása** parancsával vonható vissza. A adatforrás frissítésének leállítása visszaállítja azt az utolsó frissítéskori állapotára.       |
|Sikertelen     |Az adatbetöltés hibákba ütközött.         |

A további részletekért válassza ki az adatforrás **Állapot** oszlopát. A **Folyamat részletei** ablaktáblában bontsa ki az **Adatforrások** részt. Válassza a **Részletek megtekintése** elemet a frissítési állapot további adatai áttekintéséhez, többek között hiba részleteit és a lefelé irányuló folyamat frissítéseit.

Az adatok betöltése időbe telhet. A sikeres frissítés után a betöltött adatok áttekinthetők az **Entitások** lapról. További információ: [Entitások](entities.md).

## <a name="refresh-a-data-source"></a>Adatforrás frissítése

Az adatforrások igény szerint automatikus frissítéssel vagy kézzel frissíthetők. 

Nyissa meg a **Rendszergazda** > **Rendszer** > [**Ütemezés**](system.md#schedule-tab) elemet az összes betöltött adatforrás ütemezett frissítéseinek konfigurálása.

Az adatforrás igény szerinti frissítéséhez hajtsa végre a következő lépéseket:

1. A célközönség információin belül nyissa meg a következőt **Adatok** > **Adatforrások**.

2. Jelölje be a frissíteni kívánt adatforrás melletti függőleges ellipszist, és válassza a legördülő menüből a **Frissítés** lehetőséget.

3. Az adatforrás most már a manuális frissítésre váltja ki. Egy adatforrás frissítése frissíteni fogja az entitássémát és az adatokat a frissítésben megadott összes adatforrás számára.

4. Válassza a **Frissítés leállítása**, ha meg akarja szakítani a meglévő frissítést, és az adatforrás visszaáll a legutóbbi frissítési állapotba.

## <a name="delete-a-data-source"></a>Adatforrás törlése

1. A célközönség információin belül nyissa meg a következőt **Adatok** > **Adatforrások**.

2. Jelölje be a törölni kívánt adatforrás melletti függőleges ellipszist, és válassza a legördülő menüből a **Törlés** lehetőséget.

3. Hagyja jóvá a törlést.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
