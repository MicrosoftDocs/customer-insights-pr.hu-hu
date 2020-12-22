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
# <a name="overview-about-data-sources"></a><span data-ttu-id="34cd4-103">Adatforrások áttekintése</span><span class="sxs-lookup"><span data-stu-id="34cd4-103">Overview about data sources</span></span>

[!INCLUDE [cc-data-platform-banner](../includes/cc-data-platform-banner.md)]

<span data-ttu-id="34cd4-104">A célközönség-információk funkció a Dynamics 365 Customer Insights szolgáltatásban összekapcsolja az adatokat források széles köréből.</span><span class="sxs-lookup"><span data-stu-id="34cd4-104">The audience insights capability in Dynamics 365 Customer Insights connects to data from a broad set of sources.</span></span> <span data-ttu-id="34cd4-105">A adatforrások összeskapcsolását gyakran nevezik *adatbetöltésnek*.</span><span class="sxs-lookup"><span data-stu-id="34cd4-105">Connecting to a data source is often referred to as the process of *data ingestion*.</span></span> <span data-ttu-id="34cd4-106">Az adatok betöltése után [egyesítheti](data-unification.md) és műveleteket hajthat végre rajtuk.</span><span class="sxs-lookup"><span data-stu-id="34cd4-106">After ingesting the data, you can [unify](data-unification.md) and take action on it.</span></span>

## <a name="add-a-data-source"></a><span data-ttu-id="34cd4-107">Adatforrás felvétele</span><span class="sxs-lookup"><span data-stu-id="34cd4-107">Add a data source</span></span>

<span data-ttu-id="34cd4-108">A kiválasztott lehetőségtől függően olvassa el a részletes cikkeket az adatforrás hozzáadásáról.</span><span class="sxs-lookup"><span data-stu-id="34cd4-108">Refer to the detailed articles on how to add a data source, depending on which option you choose.</span></span>

<span data-ttu-id="34cd4-109">A adatforrások három fő módon adhatók hozzá:</span><span class="sxs-lookup"><span data-stu-id="34cd4-109">You can add a data source in three main ways:</span></span>

- [<span data-ttu-id="34cd4-110">Több tucat Power Query-összekötőn keresztül</span><span class="sxs-lookup"><span data-stu-id="34cd4-110">Through dozens of Power Query connectors</span></span>](connect-power-query.md)
- [<span data-ttu-id="34cd4-111">Common Data Model-mappából</span><span class="sxs-lookup"><span data-stu-id="34cd4-111">From a Common Data Model folder</span></span>](connect-common-data-model.md)
- [<span data-ttu-id="34cd4-112">Saját Common Data Service tóból</span><span class="sxs-lookup"><span data-stu-id="34cd4-112">From your own Common Data Service lake</span></span>](connect-common-data-service-lake.md)

> [!NOTE]
> <span data-ttu-id="34cd4-113">Még nem vehetők fel adatok helyszíni-adatforrásokból.</span><span class="sxs-lookup"><span data-stu-id="34cd4-113">You can't add data from on-premises data sources yet.</span></span>

## <a name="review-ingested-data"></a><span data-ttu-id="34cd4-114">A betöltött adatok áttekintése</span><span class="sxs-lookup"><span data-stu-id="34cd4-114">Review ingested data</span></span>

<span data-ttu-id="34cd4-115">Látni fogja az egyes betöltött adatforrások nevét, állapotát, valamint az adatoknak az adott forrásra vonatkozó utolsó frissítését.</span><span class="sxs-lookup"><span data-stu-id="34cd4-115">You'll see the name of each ingested data source, its status, and the last time the data was refreshed for that source.</span></span> <span data-ttu-id="34cd4-116">Az adatforrások listáját minden oszlop szerint rendezheti.</span><span class="sxs-lookup"><span data-stu-id="34cd4-116">You can sort the list of data sources by every column.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="34cd4-117">![Adatforrás hozzáadva](media/configure-data-datasource-added.png "Adatforrás hozzáadva")</span><span class="sxs-lookup"><span data-stu-id="34cd4-117">![Data source added](media/configure-data-datasource-added.png "Data source added")</span></span>

|<span data-ttu-id="34cd4-118">Állapot</span><span class="sxs-lookup"><span data-stu-id="34cd4-118">Status</span></span>  |<span data-ttu-id="34cd4-119">Adatfolyam leírása</span><span class="sxs-lookup"><span data-stu-id="34cd4-119">Description</span></span>  |
|---------|---------|
|<span data-ttu-id="34cd4-120">Sikeres</span><span class="sxs-lookup"><span data-stu-id="34cd4-120">Successful</span></span>   |<span data-ttu-id="34cd4-121">A adatforrás betöltése sikeres volt, ha egy idő szerepel a **Frissített** oszlopban.</span><span class="sxs-lookup"><span data-stu-id="34cd4-121">Data source was successfully ingested if a time is mentioned in the **Refreshed** column.</span></span>
|<span data-ttu-id="34cd4-122">Nem kezdődött el</span><span class="sxs-lookup"><span data-stu-id="34cd4-122">Not started</span></span>   |<span data-ttu-id="34cd4-123">Az adatforrás még nem tartalmaz adatokat vagy még vázlat módban van.</span><span class="sxs-lookup"><span data-stu-id="34cd4-123">The data source has no data ingested yet or still in draft mode.</span></span>         |
|<span data-ttu-id="34cd4-124">Frissítés</span><span class="sxs-lookup"><span data-stu-id="34cd4-124">Refreshing</span></span>    |<span data-ttu-id="34cd4-125">Az adatbetöltés folyamatban van.</span><span class="sxs-lookup"><span data-stu-id="34cd4-125">Data ingestion is in progress.</span></span> <span data-ttu-id="34cd4-126">A művelet a **Műveletek** oszlop **Frissítés leállítása** parancsával vonható vissza.</span><span class="sxs-lookup"><span data-stu-id="34cd4-126">You can cancel this operation by selecting **Stop refreshing** in the **Actions** column.</span></span> <span data-ttu-id="34cd4-127">A adatforrás frissítésének leállítása visszaállítja azt az utolsó frissítéskori állapotára.</span><span class="sxs-lookup"><span data-stu-id="34cd4-127">Stopping the refresh of a data source will revert it to its last refresh state.</span></span>       |
|<span data-ttu-id="34cd4-128">Sikertelen</span><span class="sxs-lookup"><span data-stu-id="34cd4-128">Failed</span></span>     |<span data-ttu-id="34cd4-129">Az adatbetöltés hibákba ütközött.</span><span class="sxs-lookup"><span data-stu-id="34cd4-129">Data ingestion ran into errors.</span></span>         |

<span data-ttu-id="34cd4-130">Válassza a **Frissítési állapot** elemet a frissítési állapot további adatai áttekintéséhez, többek között hiba részleteit és a lefelé irányuló folyamat frissítéseit.</span><span class="sxs-lookup"><span data-stu-id="34cd4-130">Select **Refresh status** to review more details on the refresh status, including error details and downstream process updates.</span></span>

<span data-ttu-id="34cd4-131">Az adatok betöltése eltarthat egy ideig.</span><span class="sxs-lookup"><span data-stu-id="34cd4-131">Loading data can take some time.</span></span> <span data-ttu-id="34cd4-132">A sikeres frissítés után a betöltött adatok áttekinthetők az **Entitások** lapról.</span><span class="sxs-lookup"><span data-stu-id="34cd4-132">After a successful refresh, the ingested data can be reviewed from the **Entities** page.</span></span> <span data-ttu-id="34cd4-133">További információ: [Entitások](entities.md).</span><span class="sxs-lookup"><span data-stu-id="34cd4-133">For more information, see [Entities](entities.md).</span></span>

## <a name="refresh-a-data-source"></a><span data-ttu-id="34cd4-134">Adatforrás frissítése</span><span class="sxs-lookup"><span data-stu-id="34cd4-134">Refresh a data source</span></span>

<span data-ttu-id="34cd4-135">Az adatforrások igény szerint automatikus frissítéssel vagy kézzel frissíthetők.</span><span class="sxs-lookup"><span data-stu-id="34cd4-135">Data sources can be refreshed on an automatic schedule or refreshed manually on demand.</span></span> 

<span data-ttu-id="34cd4-136">Nyissa meg a **Rendszergazda** > **Rendszer** > [**Ütemezés**](system.md#schedule-tab) elemet az összes betöltött adatforrás ütemezett frissítéseinek konfigurálása.</span><span class="sxs-lookup"><span data-stu-id="34cd4-136">Go to **Admin** > **System** > [**Schedule**](system.md#schedule-tab) to configure scheduled refreshes of all your ingested data sources.</span></span>

<span data-ttu-id="34cd4-137">Az adatforrás igény szerinti frissítéséhez hajtsa végre a következő lépéseket:</span><span class="sxs-lookup"><span data-stu-id="34cd4-137">To refresh a data source on demand, follow these steps:</span></span>

1. <span data-ttu-id="34cd4-138">A célközönség információin belül nyissa meg a következőt **Adatok** > **Adatforrások**</span><span class="sxs-lookup"><span data-stu-id="34cd4-138">In audience insights, go to **Data** > **Data sources**</span></span>

2. <span data-ttu-id="34cd4-139">Jelölje ki a frissíteni kívánt adatforrás melletti függőleges ellipszist, és válassza a **Frissítés** elemet a legördülő listából.</span><span class="sxs-lookup"><span data-stu-id="34cd4-139">Select the vertical ellipsis next to the data source you want to refresh and select **Refresh** from the drop-down list.</span></span>

3. <span data-ttu-id="34cd4-140">Az adatforrás most már a manuális frissítésre váltja ki.</span><span class="sxs-lookup"><span data-stu-id="34cd4-140">The data source is now triggered for a manual refresh.</span></span> <span data-ttu-id="34cd4-141">Az adatforrás frissítésével mind az entitások sémája, mind az adatforrásban megadott entitások adatai is frissülnek.</span><span class="sxs-lookup"><span data-stu-id="34cd4-141">Refreshing a data source will update both the entity schema as well as data for all the entities specified in the data source.</span></span>

4. <span data-ttu-id="34cd4-142">Válassza a **Frissítés leállítása**, ha meg akarja szakítani a meglévő frissítést, és az adatforrás visszaáll a legutóbbi frissítési állapotba.</span><span class="sxs-lookup"><span data-stu-id="34cd4-142">Select **Stop refreshing** if you want to cancel an existing refresh and the data source will revert to its last refresh status.</span></span>

## <a name="delete-a-data-source"></a><span data-ttu-id="34cd4-143">Adatforrás törlése</span><span class="sxs-lookup"><span data-stu-id="34cd4-143">Delete a data source</span></span>

1. <span data-ttu-id="34cd4-144">A célközönség információin belül nyissa meg a következőt **Adatok** > **Adatforrások**.</span><span class="sxs-lookup"><span data-stu-id="34cd4-144">In audience insights, go to **Data** > **Data sources**.</span></span>

2. <span data-ttu-id="34cd4-145">Jelölje ki az eltávolítani kívánt adatforrás melletti függőleges három pontot, és a legördülő menüben válassza a **Törlés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="34cd4-145">Select the vertical ellipsis next to the data source you want to remove and select **Delete** from the drop-down menu.</span></span>

3. <span data-ttu-id="34cd4-146">Hagyja jóvá a törlést.</span><span class="sxs-lookup"><span data-stu-id="34cd4-146">Confirm your deletion.</span></span>
