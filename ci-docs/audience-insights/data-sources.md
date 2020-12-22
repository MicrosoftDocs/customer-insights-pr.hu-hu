---
title: Adatforrások kiválasztása adatok betöltéséhez
description: Megismerkedhet vele, hogyan importálhat különböző forrásokból származó adatokat.
ms.date: 11/03/2020
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
ms.reviewer: adkuppa
manager: shellyha
ms.openlocfilehash: a720641f7499fc71ff5bceeba48d296c51f77242
ms.sourcegitcommit: 6a6df62fa12dcb9bd5f5a39cc3ee0e2b3988184b
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/25/2020
ms.locfileid: "4643956"
---
# <a name="overview-about-data-sources"></a>Adatforrások áttekintése

[!INCLUDE [cc-data-platform-banner](../includes/cc-data-platform-banner.md)]

A célközönség-információk funkció a Dynamics 365 Customer Insights szolgáltatásban összekapcsolja az adatokat források széles köréből. A adatforrások összeskapcsolását gyakran nevezik *adatbetöltésnek*. Az adatok betöltése után [egyesítheti](data-unification.md) és műveleteket hajthat végre rajtuk.

## <a name="add-a-data-source"></a>Adatforrás felvétele

A kiválasztott lehetőségtől függően olvassa el a részletes cikkeket az adatforrás hozzáadásáról.

A adatforrások három fő módon adhatók hozzá:

- [Több tucat Power Query-összekötőn keresztül](connect-power-query.md)
- [Common Data Model-mappából](connect-common-data-model.md)
- [Saját Common Data Service tóból](connect-common-data-service-lake.md)

> [!NOTE]
> Még nem vehetők fel adatok helyszíni-adatforrásokból.

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

Válassza a **Frissítési állapot** elemet a frissítési állapot további adatai áttekintéséhez, többek között hiba részleteit és a lefelé irányuló folyamat frissítéseit.

Az adatok betöltése eltarthat egy ideig. A sikeres frissítés után a betöltött adatok áttekinthetők az **Entitások** lapról. További információ: [Entitások](entities.md).

## <a name="refresh-a-data-source"></a>Adatforrás frissítése

Az adatforrások igény szerint automatikus frissítéssel vagy kézzel frissíthetők. 

Nyissa meg a **Rendszergazda** > **Rendszer** > [**Ütemezés**](system.md#schedule-tab) elemet az összes betöltött adatforrás ütemezett frissítéseinek konfigurálása.

Az adatforrás igény szerinti frissítéséhez hajtsa végre a következő lépéseket:

1. A célközönség információin belül nyissa meg a következőt **Adatok** > **Adatforrások**

2. Jelölje ki a frissíteni kívánt adatforrás melletti függőleges ellipszist, és válassza a **Frissítés** elemet a legördülő listából.

3. Az adatforrás most már a manuális frissítésre váltja ki. Az adatforrás frissítésével mind az entitások sémája, mind az adatforrásban megadott entitások adatai is frissülnek.

4. Válassza a **Frissítés leállítása**, ha meg akarja szakítani a meglévő frissítést, és az adatforrás visszaáll a legutóbbi frissítési állapotba.

## <a name="delete-a-data-source"></a>Adatforrás törlése

1. A célközönség információin belül nyissa meg a következőt **Adatok** > **Adatforrások**.

2. Jelölje ki az eltávolítani kívánt adatforrás melletti függőleges három pontot, és a legördülő menüben válassza a **Törlés** parancsot.

3. Hagyja jóvá a törlést.
