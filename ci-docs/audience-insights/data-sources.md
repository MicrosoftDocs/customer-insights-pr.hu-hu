---
title: Adatforrások kiválasztása adatok betöltéséhez
description: 'Megismerkedhet vele, hogyan importálhat különböző forrásokból származó adatokat.'
ms.date: 12/06/2021
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: overview
author: adkuppa
ms.author: adkuppa
ms.reviewer: mhart
manager: shellyha
---

# <a name="data-sources-overview"></a>Adatforrások áttekintése



A célközönség-információk funkció a Dynamics 365 Customer Insights szolgáltatásban összekapcsolja az adatokat források széles köréből. A adatforrások összeskapcsolását gyakran nevezik *adatbetöltésnek*. Az adatok betöltése után [egyesítheti](data-unification.md) és műveleteket hajthat végre rajtuk.

## <a name="add-a-data-source"></a>Adatforrás felvétele

A választott lehetőségtől függően tekintse meg a adatforrás hozzáadásának részletes cikkeit.

A következő adatforrásokat adhatja hozzá:

- [Power Query Csatlakozók](connect-power-query.md)
- [Common Data Model](connect-common-data-model.md)
- [Microsoft Dataverse tó](connect-dataverse-managed-lake.md)

> [!NOTE]
> Ha a próbaverziót használja, az importálási módszerek szakasz tartalmaz egy **Customer Insights adattár** opciót. Ezzel a beállítással választhatja ki a különböző iparágak számára elérhető mintaadatkészletet. További információ: [Dynamics 365 Customer Insights trial](../trial-signup.md).

## <a name="add-data-from-on-premises-data-sources"></a>Adatok hozzáadása helyszíni adatforrásokból

A célközönségi elemzésekben az adatok betöltése a helyi adatforrásokból a Microsoft Power Platform adatfolyamok alapján támogatott. A Dataflowst a Customer Insightsban úgy engedélyezheti, hogy [a Microsoft Dataverse környezet URL-címét](create-environment.md) a környezet beállításakor megadja.

A környezet Ügyfélelemzéssel való társítása Dataverse után létrehozott adatforrások alapértelmezés szerint adatfolyamokat használnak [Power Platform](/power-query/dataflows/overview-dataflows-across-power-platform-dynamics-365). Az adatfolyamok az adatátjáró használatával támogatják a helyszíni összekapcsolhatóságot. A környezet társítása Dataverse előtt [meglévő adatforrásokat helyszíni adatátjárók](/data-integration/gateway/service-gateway-app) használatával távolíthatja el és hozhatja létre újra.

A meglévő Power BI vagy Power Apps környezet adatátjárói láthatók lesznek, és újra felhasználhatók a Customer Insightsban. Az adatforrások oldalon olyan Microsoft Power Platform környezetbe mutató hivatkozások láthatók, ahol megtekintheti és konfigurálhatja a helyszíni adatátjárókat.

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
