---
title: Adatforrások kiválasztása adatok betöltéséhez
description: Megismerkedhet vele, hogyan importálhat különböző forrásokból származó adatokat.
ms.date: 11/01/2021
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: adkuppa
ms.author: adkuppa
ms.reviewer: mhart
manager: shellyha
ms.custom: intro-internal
ms.openlocfilehash: 27cbd0346b1219c7812f4b90327dd27b645c2b8e
ms.sourcegitcommit: 834651b933b1e50e7557d44f926a3fb757c1f83a
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/02/2021
ms.locfileid: "7732145"
---
# <a name="data-sources-overview"></a>Adatforrások áttekintése

[!INCLUDE [cc-data-platform-banner](../includes/cc-data-platform-banner.md)]

A Dynamics 365 Customer Insights célközönség elemzési képessége a források széles halmazából származó adatokhoz kapcsolódik. A adatforrások összeskapcsolását gyakran nevezik *adatbetöltésnek*. Az adatok betöltése után [egyesítheti](data-unification.md) és műveleteket hajthat végre rajtuk.

## <a name="add-a-data-source"></a>Adatforrás felvétele

A kiválasztott lehetőségtől függően olvassa el a részletes cikkeket az adatforrás hozzáadásáról.

A adatforrások három fő módon adhatók hozzá:

- [Több tucat Power Query-összekötőn keresztül](connect-power-query.md)
- [Common Data Model-mappából](connect-common-data-model.md)
- [Saját Microsoft Dataverse tóból](connect-dataverse-managed-lake.md)

## <a name="add-data-from-on-premises-data-sources"></a>Adatok hozzáadása helyszíni adatforrásokból

Az helyszíni adatforrásokból származó adatok célközönség elemzési adatok Microsoft Power Platform alapján támogatott. Az adatfolyamok engedélyezhetők a Customer Insightsban, ha [a környezet beállításakor megadják a Microsoft Dataverse](create-environment.md) környezet URL-címét.

A Dataverse környezet Ügyfélelemzéssel való társítása után létrehozott [adatforrások alapértelmezés szerint Power Platform adatfolyamokat használnak.](/power-query/dataflows/overview-dataflows-across-power-platform-dynamics-365) Az adatfolyamok az adatátjáró használatával támogatják a helyszíni összekapcsolhatóságot. Távolítsa el és hozza létre azokat az adatforrásokat, amelyek azelőtt léteztek, hogy egy Dataverse környezetet [társítottak volna az helyszíni adatátjárók használatához](/data-integration/gateway/service-gateway-app).

Egy meglévő Power BI vagy Power Apps környezetből származó adatátjárók láthatók lesznek, és újra felhasználhatók lesznek a Customer Insightsban. Az adatforrások lap olyan hivatkozásokat jelenít meg, amelyek a Microsoft Power Platform környezetbe mutatnak, ahol megtekintheti és konfigurálhatja helyszíni adatátjárókat.

## <a name="review-ingested-data"></a>A betöltött adatok áttekintése

Látni fogja az egyes betöltött adatforrások nevét, állapotát, valamint az adatoknak az adott forrásra vonatkozó utolsó frissítését. Az adatforrások listáját minden oszlop szerint rendezheti.

> [!div class="mx-imgBorder"]
> ![Adatforrás hozzáadva.](media/configure-data-datasource-added.png "Adatforrás hozzáadva")

[!INCLUDE [progress-details-include](../includes/progress-details-pane.md)]

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
