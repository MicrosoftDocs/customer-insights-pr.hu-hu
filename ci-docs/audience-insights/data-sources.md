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
ms.openlocfilehash: 3c0b4690e18285aa37eef481b3cfac951884ead6
ms.sourcegitcommit: fcc94f55dc2dce84eae188d582801dc47696c9cc
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/20/2021
ms.locfileid: "6085533"
---
# <a name="data-sources-overview"></a>Adatforrások áttekintése

[!INCLUDE [cc-data-platform-banner](../includes/cc-data-platform-banner.md)]

A célközönség-információk funkció a Dynamics 365 Customer Insights szolgáltatásban összekapcsolja az adatokat források széles köréből. A adatforrások összeskapcsolását gyakran nevezik *adatbetöltésnek*. Az adatok betöltése után [egyesítheti](data-unification.md) és műveleteket hajthat végre rajtuk.

## <a name="add-a-data-source"></a>Adatforrás felvétele

A kiválasztott lehetőségtől függően olvassa el a részletes cikkeket az adatforrás hozzáadásáról.

A adatforrások három fő módon adhatók hozzá:

- [Több tucat Power Query-összekötőn keresztül](connect-power-query.md)
- [Common Data Model-mappából](connect-common-data-model.md)
- [Saját Common Data Service tóból](connect-common-data-service-lake.md)

## <a name="add-data-from-on-premises-data-sources"></a>Adatok hozzáadása helyszíni adatforrásokból

A helyszíni Audience Insights-ban az adatok betöltése a helyi adatforrásokból a Power Platform adatfolyamok alapján támogatott. A Customer Insightsban úgy engedélyezhetők az adatfolyamok, ha a környezet beállításakor [meg van adva a Microsoft Dataverse környezet URL-címe](manage-environments.md#create-an-environment-in-an-existing-organization).

A Dataverse környezet Customer Insights-cal való társítása után létrehozott adatforrások alapértelmezés szerint [Power Platform adatfolyamokat](/power-query/dataflows/overview-dataflows-across-power-platform-dynamics-365) fognak használni. Az adatfolyamok az adatátjáró használatával támogatják a helyszíni összekapcsolhatóságot. Távolítsa el, majd hozza létre újból az adatforrásokat, amelyek azelőtt léteztek, hogy a Dataverse-környezet társítva lett volna [a helyszíni adatátjárók használatára](/powerapps/maker/data-platform/using-dataflows-with-on-premises-data.md).

A meglévő Power BI vagy Power Apps környezet adatátjárói láthatók lesznek, és újra felhasználhatók a Customer Insightsban. Az adatforrások oldalon olyan hivatkozások láthatóak, amelyekre kattintva a Power Platform környezetbe mehet, ahol megtekintheti és konfigurálhatja a helyszíni adatátjárókat.

## <a name="review-ingested-data"></a>A betöltött adatok áttekintése

Látni fogja az egyes betöltött adatforrások nevét, állapotát, valamint az adatoknak az adott forrásra vonatkozó utolsó frissítését. Az adatforrások listáját minden oszlop szerint rendezheti.

> [!div class="mx-imgBorder"]
> ![Adatforrás hozzáadva](media/configure-data-datasource-added.png "Adatforrás hozzáadva")

|Állapot  |Adatfolyam leírása  |
|---------|---------|
|Sikeres   |A adatforrás betöltése sikeres volt, ha egy idő szerepel a **Frissített** oszlopban.
|Nem kezdődött el   |Az adatforrás még nem tartalmaz adatokat vagy még vázlat módban van.         |
|Frissítés    |Az adatbetöltés folyamatban van. A művelet a **Műveletek** oszlop **Frissítés leállítása** parancsával vonható vissza. A adatforrás frissítésének leállítása visszaállítja azt az utolsó frissítéskori állapotára.       |
|Sikertelen     |Az adatbetöltés hibákba ütközött.         |

A további részletekért válassza ki az adatforrás **Állapot** oszlopát. A **Folyamat részletei** ablaktáblában bontsa ki az **Adatforrások** részt. Válassza a **Részletek megtekintése** elemet a frissítési állapot további adatai áttekintéséhez, többek között hiba részleteit és a lefelé irányuló folyamat frissítéseit.

Az adatok betöltése eltarthat egy ideig. A sikeres frissítés után a betöltött adatok áttekinthetők az **Entitások** lapról. További információ: [Entitások](entities.md).

## <a name="refresh-a-data-source"></a>Adatforrás frissítése

Az adatforrások igény szerint automatikus frissítéssel vagy kézzel frissíthetők. 

Nyissa meg a **Rendszergazda** > **Rendszer** > [**Ütemezés**](system.md#schedule-tab) elemet az összes betöltött adatforrás ütemezett frissítéseinek konfigurálása.

Az adatforrás igény szerinti frissítéséhez hajtsa végre a következő lépéseket:

1. A célközönség információin belül nyissa meg a következőt **Adatok** > **Adatforrások**

2. Jelölje ki a frissíteni kívánt adatforrás melletti függőleges ellipszist, és válassza a **Frissítés** elemet a legördülő listából.

3. Az adatforrás most már a manuális frissítésre váltja ki. Egy adatforrás frissítése frissíteni fogja az entitássémát és az adatokat a frissítésben megadott összes adatforrás számára.

4. Válassza a **Frissítés leállítása**, ha meg akarja szakítani a meglévő frissítést, és az adatforrás visszaáll a legutóbbi frissítési állapotba.

## <a name="delete-a-data-source"></a>Adatforrás törlése

1. A célközönség információin belül nyissa meg a következőt **Adatok** > **Adatforrások**.

2. Jelölje ki az eltávolítani kívánt adatforrás melletti függőleges három pontot, és a legördülő menüben válassza a **Törlés** parancsot.

3. Hagyja jóvá a törlést.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
