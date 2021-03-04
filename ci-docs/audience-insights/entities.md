---
title: Entitások és adathalmazok
description: Adatok megtekintése az Entitások lapon.
ms.date: 04/16/2020
ms.reviewer: mukeshpo
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: e71c69a6207147d8cd65363d51a5fa6bbf896151
ms.sourcegitcommit: 139548f8a2d0f24d54c4a6c404a743eeeb8ef8e0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/15/2021
ms.locfileid: "5269379"
---
# <a name="entities-in-audience-insights"></a><span data-ttu-id="ed581-103">Entitások a célközönség-információkban</span><span class="sxs-lookup"><span data-stu-id="ed581-103">Entities in audience insights</span></span>

<span data-ttu-id="ed581-104">Az [adatforrások konfigurálását követően nyissa](data-sources.md) meg az **Entitások** oldalt, és értékelje a beolvasott adatok minőségét.</span><span class="sxs-lookup"><span data-stu-id="ed581-104">After [configuring your data sources](data-sources.md), go to the **Entities** page to evaluate the quality of the ingested data.</span></span> <span data-ttu-id="ed581-105">Az entitások adathalmazoknak számítanak.</span><span class="sxs-lookup"><span data-stu-id="ed581-105">Entities are considered datasets.</span></span> <span data-ttu-id="ed581-106">A Dynamics 365 Customer Insights több funkciója ezekre az entitásokra van építve.</span><span class="sxs-lookup"><span data-stu-id="ed581-106">Multiple capabilities of Dynamics 365 Customer Insights are built around these entities.</span></span> <span data-ttu-id="ed581-107">Az eredmények alapos áttekintése segítséget nyújt a lehetőségek kimenetének ellenőrzésében.</span><span class="sxs-lookup"><span data-stu-id="ed581-107">Reviewing them closely can help you validate the output of those capabilities.</span></span>

<span data-ttu-id="ed581-108">Az **Entitások** lap felsorolja az entitásokat, és több oszlopot is tartalmaz:</span><span class="sxs-lookup"><span data-stu-id="ed581-108">The **Entities** page lists entities and includes several columns:</span></span>

- <span data-ttu-id="ed581-109">**Név**: Az adatentitás neve.</span><span class="sxs-lookup"><span data-stu-id="ed581-109">**Name**: The name of your data entity.</span></span> <span data-ttu-id="ed581-110">Ha az entitás neve mellett egy figyelmeztető szimbólum látható, az azt jelenti, hogy az adott entitáshoz tartozó adatok nem töltődtek be sikeresen.</span><span class="sxs-lookup"><span data-stu-id="ed581-110">If you see a warning symbol next to an entity name, it means that the data for that entity didn't load successfully.</span></span>
- <span data-ttu-id="ed581-111">**Forrás**: Az adatforrás típusa, amely be lett olvasva az entitásba</span><span class="sxs-lookup"><span data-stu-id="ed581-111">**Source**: The type of data source that ingested the entity</span></span>
- <span data-ttu-id="ed581-112">**Létrehozta**: Az entitást létrehozó személy neve</span><span class="sxs-lookup"><span data-stu-id="ed581-112">**Created by**: Name of the person who created the entity</span></span>
- <span data-ttu-id="ed581-113">**Létrehozva**: Az entitás létrehozásának dátuma és időpontja</span><span class="sxs-lookup"><span data-stu-id="ed581-113">**Created**: Date and time of the entity creation</span></span>
- <span data-ttu-id="ed581-114">**Frisítette**: Az entitást frissítő személy neve</span><span class="sxs-lookup"><span data-stu-id="ed581-114">**Updated by**: Name of the person who updated the entity</span></span>
- <span data-ttu-id="ed581-115">**Legutóbbi frissítés**: Az entitás utolsó módosításának dátuma és időpontja</span><span class="sxs-lookup"><span data-stu-id="ed581-115">**Last updated**: Date and time of the last update of the entity</span></span>
- <span data-ttu-id="ed581-116">**Legutóbbi frissítés**: Az utolsó adatfrissítés dátuma és időpontja</span><span class="sxs-lookup"><span data-stu-id="ed581-116">**Last refresh**: Date and time of the last data refresh</span></span>

## <a name="exploring-a-specific-entitys-data"></a><span data-ttu-id="ed581-117">Adott entitás adatainak feltárása</span><span class="sxs-lookup"><span data-stu-id="ed581-117">Exploring a specific entity's data</span></span>

<span data-ttu-id="ed581-118">Jelöljön ki egy entitást az adott entitáshoz tartozó különböző mezők és bejegyzések feltáráshoz.</span><span class="sxs-lookup"><span data-stu-id="ed581-118">Select an entity to explore the different fields and records included within that entity.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="ed581-119">![Válasszon entitást](media/data-manager-entities-data.png "Válasszon ki egy entitást!")</span><span class="sxs-lookup"><span data-stu-id="ed581-119">![Select an entity](media/data-manager-entities-data.png "Select an entity")</span></span>

- <span data-ttu-id="ed581-120">Az **Adatok** lap alapértelmezés szerint be van jelölve, és az entitás egyes bejegyzéseire vonatkozó adatokat tartalmazó táblázatot jelenít meg.</span><span class="sxs-lookup"><span data-stu-id="ed581-120">The **Data** tab is selected by default and shows a table listing details about individual records of the entity.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="ed581-121">![Mezők tábla](media/data-manager-entities-fields.PNG "Mezők tábla")</span><span class="sxs-lookup"><span data-stu-id="ed581-121">![Fields table](media/data-manager-entities-fields.PNG "Fields table")</span></span>

- <span data-ttu-id="ed581-122">A **Mezők** lapon látható egy táblázat, amely a kijelölt entitás adatainak, például mezőnevek, adattípusok és típusok áttekintésére szolgál.</span><span class="sxs-lookup"><span data-stu-id="ed581-122">The **Fields** tab shows a table to review details for the selected entity, such as field names, data types, and types.</span></span> <span data-ttu-id="ed581-123">A **Típus** oszlop a Common Data Modelhez társított típusokat jeleníti meg, amelyeket vagy a rendszer automatikusan azonosít, vagy a felhasználók [kézzel leképeznek](map-entities.md).</span><span class="sxs-lookup"><span data-stu-id="ed581-123">The **Type** column shows Common Data Model associated types, which are either auto-identified by the system or [manually mapped](map-entities.md) by users.</span></span> <span data-ttu-id="ed581-124">Ezek olyan szemantikai típusok, amelyek eltérhetnek az attribútumok adattípusaitól – például az alábbi *Ee-mail* mező adattípusa *Szöveg*, de (szemantikai) Common Data Model típusa lehet *E-mail* vagy *EmailAddress*.</span><span class="sxs-lookup"><span data-stu-id="ed581-124">These are semantic types that can differ from the attributes' data types—for example, the field *Email* below has a data type *Text* but its (semantic) Common Data Model type might be *Email* or *EmailAddress*.</span></span>

> [!NOTE]
> <span data-ttu-id="ed581-125">Mindkét tábla csak az entitás adatainak mintáját jeleníti meg.</span><span class="sxs-lookup"><span data-stu-id="ed581-125">Both tables show only a sample of your entity's data.</span></span> <span data-ttu-id="ed581-126">Ha meg szeretné tekinteni a teljes adatkészlet, nyissa meg az **Adatforrások** oldalt, jelöljön kiegy entitást, válassza a **Szerkesztés** lehetőséget, majd tekintse meg az entitás adatait aPower Query-szerkesztővel, amint az az [Adatforrásokban](data-sources.md) látható.</span><span class="sxs-lookup"><span data-stu-id="ed581-126">To view the full data set, go to the **Data sources** page, select an entity, select **Edit**, and then view this entity's data with the Power Query editor as explained in [Data sources](data-sources.md).</span></span>

<span data-ttu-id="ed581-127">Ha többet szeretne megtudni az entitásban lévő adatokról, akkor az **Összesítés** oszlop az adatokra vonatkozó néhány fontos jellemzőt tartalmaz az adatokról, például a nullák, a hiányzó értékek, az egyedi értékek, a számlálók és a disztribúciók, az Ön adatai szerint.</span><span class="sxs-lookup"><span data-stu-id="ed581-127">To learn more about the data ingested in the entity, the **Summary** column provides you with some important characteristics of the data, such as nulls, missing values, unique values, counts, and distributions, as applicable to your data.</span></span>

<span data-ttu-id="ed581-128">Az adatok összegzésének megjelenítéséhez válassza ki a diagram ikont.</span><span class="sxs-lookup"><span data-stu-id="ed581-128">Select the chart icon to see the summary of the data.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="ed581-129">![Összegzés szimbólum](media/data-manager-entities-summary.png "Adatok összesítése tábla")</span><span class="sxs-lookup"><span data-stu-id="ed581-129">![Summary symbol](media/data-manager-entities-summary.png "Data summary table")</span></span>

### <a name="next-step"></a><span data-ttu-id="ed581-130">Következő lépés</span><span class="sxs-lookup"><span data-stu-id="ed581-130">Next step</span></span>

<span data-ttu-id="ed581-131">Tekintse meg az [Egyesítés](data-unification.md) témakör, azzal kapcsolatosan, hogy hogyan lehet *leképezni*, *egyeztetni* és *egyesíteni* a leképezett adatokat.</span><span class="sxs-lookup"><span data-stu-id="ed581-131">See the [Unify](data-unification.md) topic to learn how to *map*, *match*, and *merge* the ingested data.</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]