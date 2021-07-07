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
ms.openlocfilehash: 54dd7b629d4b4e7f640b932b0f9246e0602f46bd
ms.sourcegitcommit: d84d664e67f263bfeb741154d309088c5101b9c3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/24/2021
ms.locfileid: "6304699"
---
# <a name="data-sources-overview"></a><span data-ttu-id="3c7eb-103">Adatforrások áttekintése</span><span class="sxs-lookup"><span data-stu-id="3c7eb-103">Data sources overview</span></span>

[!INCLUDE [cc-data-platform-banner](../includes/cc-data-platform-banner.md)]

<span data-ttu-id="3c7eb-104">A célközönség-információk funkció a Dynamics 365 Customer Insights szolgáltatásban összekapcsolja az adatokat források széles köréből.</span><span class="sxs-lookup"><span data-stu-id="3c7eb-104">The audience insights capability in Dynamics 365 Customer Insights connects to data from a broad set of sources.</span></span> <span data-ttu-id="3c7eb-105">A adatforrások összeskapcsolását gyakran nevezik *adatbetöltésnek*.</span><span class="sxs-lookup"><span data-stu-id="3c7eb-105">Connecting to a data source is often referred to as the process of *data ingestion*.</span></span> <span data-ttu-id="3c7eb-106">Az adatok betöltése után [egyesítheti](data-unification.md) és műveleteket hajthat végre rajtuk.</span><span class="sxs-lookup"><span data-stu-id="3c7eb-106">After ingesting the data, you can [unify](data-unification.md) and take action on it.</span></span>

## <a name="add-a-data-source"></a><span data-ttu-id="3c7eb-107">Adatforrás felvétele</span><span class="sxs-lookup"><span data-stu-id="3c7eb-107">Add a data source</span></span>

<span data-ttu-id="3c7eb-108">A kiválasztott lehetőségtől függően olvassa el a részletes cikkeket az adatforrás hozzáadásáról.</span><span class="sxs-lookup"><span data-stu-id="3c7eb-108">Refer to the detailed articles on how to add a data source, depending on which option you choose.</span></span>

<span data-ttu-id="3c7eb-109">A adatforrások három fő módon adhatók hozzá:</span><span class="sxs-lookup"><span data-stu-id="3c7eb-109">You can add a data source in three main ways:</span></span>

- [<span data-ttu-id="3c7eb-110">Több tucat Power Query-összekötőn keresztül</span><span class="sxs-lookup"><span data-stu-id="3c7eb-110">Through dozens of Power Query connectors</span></span>](connect-power-query.md)
- [<span data-ttu-id="3c7eb-111">Common Data Model-mappából</span><span class="sxs-lookup"><span data-stu-id="3c7eb-111">From a Common Data Model folder</span></span>](connect-common-data-model.md)
- [<span data-ttu-id="3c7eb-112">Saját Microsoft Dataverse tóból</span><span class="sxs-lookup"><span data-stu-id="3c7eb-112">From your own Microsoft Dataverse lake</span></span>](connect-common-data-service-lake.md)

## <a name="add-data-from-on-premises-data-sources"></a><span data-ttu-id="3c7eb-113">Adatok hozzáadása helyszíni adatforrásokból</span><span class="sxs-lookup"><span data-stu-id="3c7eb-113">Add data from on-premises data sources</span></span>

<span data-ttu-id="3c7eb-114">A célközönségi elemzésekben az adatok betöltése a helyi adatforrásokból a Microsoft Power Platform adatfolyamok alapján támogatott.</span><span class="sxs-lookup"><span data-stu-id="3c7eb-114">Ingesting data from on-premises data sources in audience insights is supported based on Microsoft Power Platform dataflows.</span></span> <span data-ttu-id="3c7eb-115">A Customer Insightsban úgy engedélyezhetők az adatfolyamok, ha a környezet beállításakor [meg van adva a Microsoft Dataverse környezet URL-címe](manage-environments.md#create-an-environment-in-an-existing-organization).</span><span class="sxs-lookup"><span data-stu-id="3c7eb-115">Dataflows can be enabled in Customer Insights by [providing the Microsoft Dataverse environment URL](manage-environments.md#create-an-environment-in-an-existing-organization) when setting up the environment.</span></span>

<span data-ttu-id="3c7eb-116">A Dataverse környezet Customer Insights-cal való társítása után létrehozott adatforrások alapértelmezés szerint [Power Platform adatfolyamokat](/power-query/dataflows/overview-dataflows-across-power-platform-dynamics-365) fognak használni.</span><span class="sxs-lookup"><span data-stu-id="3c7eb-116">Data sources that are created after associating a Dataverse environment with Customer Insights will use [Power Platform dataflows](/power-query/dataflows/overview-dataflows-across-power-platform-dynamics-365) by default.</span></span> <span data-ttu-id="3c7eb-117">Az adatfolyamok az adatátjáró használatával támogatják a helyszíni összekapcsolhatóságot.</span><span class="sxs-lookup"><span data-stu-id="3c7eb-117">Dataflows support on-premises connectivity using the data gateway.</span></span> <span data-ttu-id="3c7eb-118">Távolítsa el, majd hozza létre újból az adatforrásokat, amelyek azelőtt léteztek, hogy a Dataverse-környezet társítva lett volna [a helyszíni adatátjárók használatára](/data-integration/gateway/service-gateway-app.md).</span><span class="sxs-lookup"><span data-stu-id="3c7eb-118">Remove and recreate data sources that existed before a Dataverse environment was associated to [use the on-premises data gateways](/data-integration/gateway/service-gateway-app.md).</span></span>

<span data-ttu-id="3c7eb-119">A meglévő Power BI vagy Power Apps környezet adatátjárói láthatók lesznek, és újra felhasználhatók a Customer Insightsban.</span><span class="sxs-lookup"><span data-stu-id="3c7eb-119">Data gateways from an existing Power BI or Power Apps environment will be visible and you can reuse in Customer Insights.</span></span> <span data-ttu-id="3c7eb-120">Az adatforrások oldalon olyan Microsoft Power Platform környezetbe mutató hivatkozások láthatók, ahol megtekintheti és konfigurálhatja a helyszíni adatátjárókat.</span><span class="sxs-lookup"><span data-stu-id="3c7eb-120">The data sources page shows links to go to the Microsoft Power Platform environment where you can view and configure on-premises data gateways.</span></span>

## <a name="review-ingested-data"></a><span data-ttu-id="3c7eb-121">A betöltött adatok áttekintése</span><span class="sxs-lookup"><span data-stu-id="3c7eb-121">Review ingested data</span></span>

<span data-ttu-id="3c7eb-122">Látni fogja az egyes betöltött adatforrások nevét, állapotát, valamint az adatoknak az adott forrásra vonatkozó utolsó frissítését.</span><span class="sxs-lookup"><span data-stu-id="3c7eb-122">You'll see the name of each ingested data source, its status, and the last time the data was refreshed for that source.</span></span> <span data-ttu-id="3c7eb-123">Az adatforrások listáját minden oszlop szerint rendezheti.</span><span class="sxs-lookup"><span data-stu-id="3c7eb-123">You can sort the list of data sources by every column.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="3c7eb-124">![Adatforrás hozzáadva](media/configure-data-datasource-added.png "Adatforrás hozzáadva")</span><span class="sxs-lookup"><span data-stu-id="3c7eb-124">![Data source added](media/configure-data-datasource-added.png "Data source added")</span></span>

|<span data-ttu-id="3c7eb-125">Állapot</span><span class="sxs-lookup"><span data-stu-id="3c7eb-125">Status</span></span>  |<span data-ttu-id="3c7eb-126">Adatfolyam leírása</span><span class="sxs-lookup"><span data-stu-id="3c7eb-126">Description</span></span>  |
|---------|---------|
|<span data-ttu-id="3c7eb-127">Sikeres</span><span class="sxs-lookup"><span data-stu-id="3c7eb-127">Successful</span></span>   |<span data-ttu-id="3c7eb-128">A adatforrás betöltése sikeres volt, ha egy idő szerepel a **Frissített** oszlopban.</span><span class="sxs-lookup"><span data-stu-id="3c7eb-128">Data source was successfully ingested if a time is mentioned in the **Refreshed** column.</span></span>
|<span data-ttu-id="3c7eb-129">Nem kezdődött el</span><span class="sxs-lookup"><span data-stu-id="3c7eb-129">Not started</span></span>   |<span data-ttu-id="3c7eb-130">Az adatforrás még nem tartalmaz adatokat vagy még vázlat módban van.</span><span class="sxs-lookup"><span data-stu-id="3c7eb-130">The data source has no data ingested yet or still in draft mode.</span></span>         |
|<span data-ttu-id="3c7eb-131">Frissítés</span><span class="sxs-lookup"><span data-stu-id="3c7eb-131">Refreshing</span></span>    |<span data-ttu-id="3c7eb-132">Az adatbetöltés folyamatban van.</span><span class="sxs-lookup"><span data-stu-id="3c7eb-132">Data ingestion is in progress.</span></span> <span data-ttu-id="3c7eb-133">A művelet a **Műveletek** oszlop **Frissítés leállítása** parancsával vonható vissza.</span><span class="sxs-lookup"><span data-stu-id="3c7eb-133">You can cancel this operation by selecting **Stop refreshing** in the **Actions** column.</span></span> <span data-ttu-id="3c7eb-134">A adatforrás frissítésének leállítása visszaállítja azt az utolsó frissítéskori állapotára.</span><span class="sxs-lookup"><span data-stu-id="3c7eb-134">Stopping the refresh of a data source will revert it to its last refresh state.</span></span>       |
|<span data-ttu-id="3c7eb-135">Sikertelen</span><span class="sxs-lookup"><span data-stu-id="3c7eb-135">Failed</span></span>     |<span data-ttu-id="3c7eb-136">Az adatbetöltés hibákba ütközött.</span><span class="sxs-lookup"><span data-stu-id="3c7eb-136">Data ingestion ran into errors.</span></span>         |

<span data-ttu-id="3c7eb-137">A további részletekért válassza ki az adatforrás **Állapot** oszlopát.</span><span class="sxs-lookup"><span data-stu-id="3c7eb-137">Select the value in the **Status** column of any data source to review more details.</span></span> <span data-ttu-id="3c7eb-138">A **Folyamat részletei** ablaktáblában bontsa ki az **Adatforrások** részt.</span><span class="sxs-lookup"><span data-stu-id="3c7eb-138">In the **Progress details** pane, expand **Data sources**.</span></span> <span data-ttu-id="3c7eb-139">Válassza a **Részletek megtekintése** elemet a frissítési állapot további adatai áttekintéséhez, többek között hiba részleteit és a lefelé irányuló folyamat frissítéseit.</span><span class="sxs-lookup"><span data-stu-id="3c7eb-139">Select **See details** for more information about the refresh status, including error details and downstream process updates.</span></span>

<span data-ttu-id="3c7eb-140">Az adatok betöltése időbe telhet.</span><span class="sxs-lookup"><span data-stu-id="3c7eb-140">Loading data can take time.</span></span> <span data-ttu-id="3c7eb-141">A sikeres frissítés után a betöltött adatok áttekinthetők az **Entitások** lapról.</span><span class="sxs-lookup"><span data-stu-id="3c7eb-141">After a successful refresh, the ingested data can be reviewed from the **Entities** page.</span></span> <span data-ttu-id="3c7eb-142">További információ: [Entitások](entities.md).</span><span class="sxs-lookup"><span data-stu-id="3c7eb-142">For more information, see [Entities](entities.md).</span></span>

## <a name="refresh-a-data-source"></a><span data-ttu-id="3c7eb-143">Adatforrás frissítése</span><span class="sxs-lookup"><span data-stu-id="3c7eb-143">Refresh a data source</span></span>

<span data-ttu-id="3c7eb-144">Az adatforrások igény szerint automatikus frissítéssel vagy kézzel frissíthetők.</span><span class="sxs-lookup"><span data-stu-id="3c7eb-144">Data sources can be refreshed on an automatic schedule or refreshed manually on demand.</span></span> 

<span data-ttu-id="3c7eb-145">Nyissa meg a **Rendszergazda** > **Rendszer** > [**Ütemezés**](system.md#schedule-tab) elemet az összes betöltött adatforrás ütemezett frissítéseinek konfigurálása.</span><span class="sxs-lookup"><span data-stu-id="3c7eb-145">Go to **Admin** > **System** > [**Schedule**](system.md#schedule-tab) to configure scheduled refreshes of all your ingested data sources.</span></span>

<span data-ttu-id="3c7eb-146">Az adatforrás igény szerinti frissítéséhez hajtsa végre a következő lépéseket:</span><span class="sxs-lookup"><span data-stu-id="3c7eb-146">To refresh a data source on demand, follow these steps:</span></span>

1. <span data-ttu-id="3c7eb-147">A célközönség információin belül nyissa meg a következőt **Adatok** > **Adatforrások**.</span><span class="sxs-lookup"><span data-stu-id="3c7eb-147">In audience insights, go to **Data** > **Data sources**.</span></span>

2. <span data-ttu-id="3c7eb-148">Jelölje be a frissíteni kívánt adatforrás melletti függőleges ellipszist, és válassza a legördülő menüből a **Frissítés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="3c7eb-148">Select the vertical ellipsis next to the data source you want to refresh and select **Refresh** from the dropdown list.</span></span>

3. <span data-ttu-id="3c7eb-149">Az adatforrás most már a manuális frissítésre váltja ki.</span><span class="sxs-lookup"><span data-stu-id="3c7eb-149">The data source is now triggered for a manual refresh.</span></span> <span data-ttu-id="3c7eb-150">Egy adatforrás frissítése frissíteni fogja az entitássémát és az adatokat a frissítésben megadott összes adatforrás számára.</span><span class="sxs-lookup"><span data-stu-id="3c7eb-150">Refreshing a data source will update both the entity schema and data for all the entities specified in the data source.</span></span>

4. <span data-ttu-id="3c7eb-151">Válassza a **Frissítés leállítása**, ha meg akarja szakítani a meglévő frissítést, és az adatforrás visszaáll a legutóbbi frissítési állapotba.</span><span class="sxs-lookup"><span data-stu-id="3c7eb-151">Select **Stop refreshing** if you want to cancel an existing refresh and the data source will revert to its last refresh status.</span></span>

## <a name="delete-a-data-source"></a><span data-ttu-id="3c7eb-152">Adatforrás törlése</span><span class="sxs-lookup"><span data-stu-id="3c7eb-152">Delete a data source</span></span>

1. <span data-ttu-id="3c7eb-153">A célközönség információin belül nyissa meg a következőt **Adatok** > **Adatforrások**.</span><span class="sxs-lookup"><span data-stu-id="3c7eb-153">In audience insights, go to **Data** > **Data sources**.</span></span>

2. <span data-ttu-id="3c7eb-154">Jelölje be a törölni kívánt adatforrás melletti függőleges ellipszist, és válassza a legördülő menüből a **Törlés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="3c7eb-154">Select the vertical ellipsis next to the data source you want to remove and select **Delete** from the dropdown menu.</span></span>

3. <span data-ttu-id="3c7eb-155">Hagyja jóvá a törlést.</span><span class="sxs-lookup"><span data-stu-id="3c7eb-155">Confirm your deletion.</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]
