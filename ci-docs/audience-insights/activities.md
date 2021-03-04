---
title: Ügyféltevékenységek
description: Az ügyféltevékenységek definiálása és a megtekintése az ügyfelek idővonalában.
ms.date: 10/13/2020
ms.service: customer-insights
ms.subservice: audience-insights
ms.reviewer: adkuppa
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: dcef8f0547009e1488f1abe91423fa0bf5b061de
ms.sourcegitcommit: 139548f8a2d0f24d54c4a6c404a743eeeb8ef8e0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/15/2021
ms.locfileid: "5267435"
---
# <a name="customer-activities"></a><span data-ttu-id="93c97-103">Ügyféltevékenységek</span><span class="sxs-lookup"><span data-stu-id="93c97-103">Customer activities</span></span>

<span data-ttu-id="93c97-104">Az ügyféltevékenységeket kombinálja a [különböző adatforrásokból](data-sources.md) a Dynamics 365 Customer Insights-ban olyan ügyfélidővonal létrehozásához, amely a tevékenységeket időrendi sorrendben sorolja fel.</span><span class="sxs-lookup"><span data-stu-id="93c97-104">Combine customer activities from [various data sources](data-sources.md) in Dynamics 365 Customer Insights to create a customer timeline that lists the activities in chronological order.</span></span> <span data-ttu-id="93c97-105">Az idővonalat alkalmazhat Dynamics 365 az ügyfélkapcsolati alkalmazásaiban az [Ügyfélkártya bővítmény](customer-card-add-in.md) vagy a Power BI irányítópult segítségével.</span><span class="sxs-lookup"><span data-stu-id="93c97-105">You can include the timeline in customer engagement apps in Dynamics 365 via the [Customer Card add-in](customer-card-add-in.md), or in a Power BI dashboard.</span></span>

## <a name="define-an-activity"></a><span data-ttu-id="93c97-106">Egy tevékenység definiálása</span><span class="sxs-lookup"><span data-stu-id="93c97-106">Define an activity</span></span>

<span data-ttu-id="93c97-107">Az adatforrások több adatforrásból származó, tranzakciós és tevékenységi adatokkal rendelkező entitásokat tartalmaznak.</span><span class="sxs-lookup"><span data-stu-id="93c97-107">Your data sources include entities with transactional and activity data from multiple data sources.</span></span> <span data-ttu-id="93c97-108">Azonosítsa ezeket az entitásokat, és jelölje ki az ügyfél idővonalán megtekinteni kívánt tevékenységeket.</span><span class="sxs-lookup"><span data-stu-id="93c97-108">Identify these entities and select the activities you want to view on the customer's timeline.</span></span> <span data-ttu-id="93c97-109">Válassza ki azt az entitást, amely a cél tevékenységet vagy tevékenységeket tartalmazza.</span><span class="sxs-lookup"><span data-stu-id="93c97-109">Choose the entity that includes your target activity or activities.</span></span>

1. <span data-ttu-id="93c97-110">A célközönség információin belül nyissa meg a következőt: **Adatok** > **Tevékenységek**.</span><span class="sxs-lookup"><span data-stu-id="93c97-110">In audience insights, go to **Data** > **Activities**.</span></span>

1. <span data-ttu-id="93c97-111">Válassza a **Tevékenység hozzáadása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="93c97-111">Select **Add activity**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="93c97-112">Egy entitásben legalább egy **Dátum** típusú attribútumnak szerepelnie kell, hogy az bekerüljön az ügyfél idővonalába, és nem lehet entitásokat felvenni **Dátum** mezők nélkül.</span><span class="sxs-lookup"><span data-stu-id="93c97-112">An entity must have at least one attribute of type **Date** to be included in a customer timeline and you can't add entities without **Date** fields.</span></span> <span data-ttu-id="93c97-113">A **Tevékenység hozzáadása** vezérlő le van tiltva, ha nem talál ilyen entitást.</span><span class="sxs-lookup"><span data-stu-id="93c97-113">The **Add activity** control is disabled if no such entity is found.</span></span>

1. <span data-ttu-id="93c97-114">A **Tevékenység hozzáadása** ablaktáblában adja meg a következő mezők értékeit:</span><span class="sxs-lookup"><span data-stu-id="93c97-114">In the **Add activity** pane, set the values for the following fields:</span></span>

   - <span data-ttu-id="93c97-115">**Entitás**: Jelöljön ki egy entitást, amely tranzakciós vagy tevékenységi adatot tartalmaz.</span><span class="sxs-lookup"><span data-stu-id="93c97-115">**Entity**: Select an entity that includes transactional or activity data.</span></span>
   - <span data-ttu-id="93c97-116">**Elsődleges kulcs**: Válassza ki azt a mezőt, amely egyértelműen azonosítja a rekordot.</span><span class="sxs-lookup"><span data-stu-id="93c97-116">**Primary key**: Select the field that uniquely identifies a record.</span></span> <span data-ttu-id="93c97-117">Nem tartalmazhat ismétlődő értékeket, üres értékeket vagy hiányzó értékeket.</span><span class="sxs-lookup"><span data-stu-id="93c97-117">It shouldn't contain any duplicate values, empty values, or missing values.</span></span>
   - <span data-ttu-id="93c97-118">**Időbélyegző**: Válassza ki azt a mezőt, amely a tevékenység kezdési időpontját jelzi.</span><span class="sxs-lookup"><span data-stu-id="93c97-118">**Timestamp**: Select the field that represents the start time of your activity.</span></span>
   - <span data-ttu-id="93c97-119">**Esemény**: Válassza ki azt a mezőt, amely a tevékenységhez tartozó esemény.</span><span class="sxs-lookup"><span data-stu-id="93c97-119">**Event**: Select the field that is the event for the activity.</span></span>
   - <span data-ttu-id="93c97-120">**Internetcím**: Válassza ki azt a mezőt, amely a tevékenységre vonatkozóan további információkat tartalmazó URL-címet jelent.</span><span class="sxs-lookup"><span data-stu-id="93c97-120">**Web address**: Select the field that represents a URL providing additional information about this activity.</span></span> <span data-ttu-id="93c97-121">Például a tevékenység forrását jelentő tranzakciós rendszer.</span><span class="sxs-lookup"><span data-stu-id="93c97-121">For example, the transactional system that sources this activity.</span></span> <span data-ttu-id="93c97-122">Ez az URL-cím az adatforrás tetszőleges mezője lehet, vagy Power Query átalakítást használó új mezőként lehet kialakítani.</span><span class="sxs-lookup"><span data-stu-id="93c97-122">This URL can be any field from the data source, or it can be constructed as a new field using a Power Query transformation.</span></span> <span data-ttu-id="93c97-123">Ez az URL-cím az egyesített tevékenység entitásban tárolódik, amelyet lefelé irányulóan az API-k használatával lehet használni.</span><span class="sxs-lookup"><span data-stu-id="93c97-123">This URL data will be stored in the Unified Activity entity, which can be consumed downstream using APIs.</span></span>
   - <span data-ttu-id="93c97-124">**Részletek**: Tetszés szerint jelölje ki a további részletekért hozzáadott mezőt.</span><span class="sxs-lookup"><span data-stu-id="93c97-124">**Details**: Optionally, select the field that is added for additional details.</span></span>
   - <span data-ttu-id="93c97-125">**Ikon**: Tetszés szerint jelölje ki a tevékenységet jelképező ikont.</span><span class="sxs-lookup"><span data-stu-id="93c97-125">**Icon**: Optionally, select the icon that represents this activity.</span></span>
   - <span data-ttu-id="93c97-126">**Tevékenység típusa**: Adja meg a tevékenységtípus hivatkozását a Common Data Modelhez, amely a legjobban leírja a művelet szemantikai meghatározását.</span><span class="sxs-lookup"><span data-stu-id="93c97-126">**Activity Type**: Define the activity type reference to Common Data Model that best describes the semantic definition of the activity.</span></span>

1. <span data-ttu-id="93c97-127">A **Kapcsolat beállítása** szakaszban állítsa be a részleteket, hogy a tevékenység adatait a megfelelő ügyfélhez csatlakoztassa.</span><span class="sxs-lookup"><span data-stu-id="93c97-127">In the **Set up relationship** section, configure the details to connect your activity data to its corresponding customer.</span></span>

    - <span data-ttu-id="93c97-128">**Tevékenység entitás mezője**: Jelölje ki a tevékenység entitásban egy másik entitással fennálló kapcsolat létesítéséhez használandó mezőt.</span><span class="sxs-lookup"><span data-stu-id="93c97-128">**Activity entity field**: Select the field in your activity entity that will be used to establish a relationship with another entity.</span></span>
    - <span data-ttu-id="93c97-129">**Ügyfél entitás**: Válassza ki a megfelelő forrás ügyfélentitást, amellyel a tevékenység entitása kapcsolatban lesz.</span><span class="sxs-lookup"><span data-stu-id="93c97-129">**Customer entity**: Select the corresponding source customer entity with which your activity entity will be in relationship.</span></span> <span data-ttu-id="93c97-130">Csak az adategyesítési folyamat során használt forrás ügyfél-entitásokhoz kapcsolódhat.</span><span class="sxs-lookup"><span data-stu-id="93c97-130">You can relate to only those source customer entities that are used in the data unification process.</span></span>
    - <span data-ttu-id="93c97-131">**Ügyfél entitás mezője**: Ez a mező mutatja a forrás ügyfél entitás elsődleges kulcsát a leképezési folyamatban kiválasztottként.</span><span class="sxs-lookup"><span data-stu-id="93c97-131">**Customer entity field**: This field shows the primary key of the source customer entity as selected in the map process.</span></span> <span data-ttu-id="93c97-132">A forrás ügyfél entitásban ez az elsődlegeskulcs-mező a tevékenység entitással fennálló kapcsolat létrehozására használt.</span><span class="sxs-lookup"><span data-stu-id="93c97-132">This primary key field in the source customer entity is used to establish a relationship with the activity entity.</span></span>
    - <span data-ttu-id="93c97-133">**Név**: Ha a tevékenység entitás és a kiválasztott forrásoldali ügyfél entitás között már létezik kapcsolat, a kapcsolat neve írásvédett módban lesz.</span><span class="sxs-lookup"><span data-stu-id="93c97-133">**Name**: If a relationship between this activity entity and the selected source customer entity already exists, the relationship name will be in read-only mode.</span></span> <span data-ttu-id="93c97-134">Ha nincs ilyen kapcsolat, akkor létrejön egy új kapcsolat az itt megadott néven.</span><span class="sxs-lookup"><span data-stu-id="93c97-134">If there no such relationship exists, a new relationship will be created with the name provided here.</span></span>
   
   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="93c97-135">![Definiálja az entitás kapcsolatát](media/activities-entities-define.png "Definiálja az entitás kapcsolatát")</span><span class="sxs-lookup"><span data-stu-id="93c97-135">![Define the entity relationship](media/activities-entities-define.png "Define the entity relationship")</span></span>

1. <span data-ttu-id="93c97-136">Válassza a **Mentés** lehetőséget a módosítások alkalmazásához.</span><span class="sxs-lookup"><span data-stu-id="93c97-136">Select **Save** to apply your changes.</span></span>

1. <span data-ttu-id="93c97-137">A **Tevékenységek** lapon válassza a **Futtatás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="93c97-137">On the **Activities** page, select **Run**.</span></span>

> [!TIP]
> <span data-ttu-id="93c97-138">A feladatokhoz/folyamatokhoz [hatféle állapot](system.md#status-types) tartozhat.</span><span class="sxs-lookup"><span data-stu-id="93c97-138">There are [six types of status](system.md#status-types) for tasks/processes.</span></span> <span data-ttu-id="93c97-139">Emellett a legtöbb folyamat [más alsóbb szintű folyamatoktól is függ](system.md#refresh-policies).</span><span class="sxs-lookup"><span data-stu-id="93c97-139">Additionally, most processes [depend on other downstream processes](system.md#refresh-policies).</span></span> <span data-ttu-id="93c97-140">Kiválaszthatja egy folyamat állapotát, és megtekintheti a hozzá tartozó teljes feladat folyamatának részleteit.</span><span class="sxs-lookup"><span data-stu-id="93c97-140">You can select the status of a process to see details on the progress of the entire job.</span></span> <span data-ttu-id="93c97-141">Miután kiválasztotta a **Részletek megtekintése** lehetőséget a feladat egyik feladatához, további információk jelennek meg: feldolgozási idő, legutóbbi feldolgozás dátuma, és a feladathoz társított összes hiba és figyelmeztetés.</span><span class="sxs-lookup"><span data-stu-id="93c97-141">After selecting **See details** for one of the job's tasks, you find additional information: processing time, the last processing date, and all errors and warnings associated with the task.</span></span>

## <a name="edit-an-activity"></a><span data-ttu-id="93c97-142">Tevékenység szerkesztése</span><span class="sxs-lookup"><span data-stu-id="93c97-142">Edit an activity</span></span>

1. <span data-ttu-id="93c97-143">A célközönség információin belül nyissa meg a következőt: **Adatok** > **Tevékenységek**.</span><span class="sxs-lookup"><span data-stu-id="93c97-143">In audience insights, go to **Data** > **Activities**.</span></span>

2. <span data-ttu-id="93c97-144">Keresse meg a szerkeszteni kívánt tevékenységentitást, és válassza a **Szerkesztés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="93c97-144">Select the activity entity you want to edit and select **Edit**.</span></span> <span data-ttu-id="93c97-145">Másik lehetőségként az egérmutatót az entitás sorára helyezheti, és kiválaszthatja a **Szerkesztés** ikont.</span><span class="sxs-lookup"><span data-stu-id="93c97-145">Or, you can hover over the entity row and select the **Edit** icon.</span></span>

3. <span data-ttu-id="93c97-146">Kattintson a **Szerkesztés** ikonra.</span><span class="sxs-lookup"><span data-stu-id="93c97-146">Click on the **Edit** icon.</span></span>

4. <span data-ttu-id="93c97-147">A **Tevékenység szerkesztése** ablaktáblában frissítse az értékeket, és válassza a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="93c97-147">In the **Edit activity** pane, update the values and select **Save**.</span></span>

5. <span data-ttu-id="93c97-148">A **Tevékenységek** lapon válassza a **Futtatás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="93c97-148">On the **Activities** page, select **Run**.</span></span>

## <a name="delete-an-activity"></a><span data-ttu-id="93c97-149">Tevékenység törlése</span><span class="sxs-lookup"><span data-stu-id="93c97-149">Delete an activity</span></span>

1. <span data-ttu-id="93c97-150">A célközönség információin belül nyissa meg a következőt: **Adatok** > **Tevékenységek**.</span><span class="sxs-lookup"><span data-stu-id="93c97-150">In audience insights, go to **Data** > **Activities**.</span></span>

2. <span data-ttu-id="93c97-151">Keresse meg az eltávolítani kívánt tevékenységentitást, és válassza a **Törlés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="93c97-151">Select the activity entity you want to remove and select **Delete**.</span></span> <span data-ttu-id="93c97-152">Másik lehetőségként az egérmutatót az entitás sorára helyezheti, és kiválaszthatja a **Törlés** ikont.</span><span class="sxs-lookup"><span data-stu-id="93c97-152">Or, you can hover over the entity row and select the **Delete** icon.</span></span> <span data-ttu-id="93c97-153">Emellett több tevékenységentitás is kijelölhető, amelyet egyszerre kell törölni.</span><span class="sxs-lookup"><span data-stu-id="93c97-153">Additionally, you can select multiple activity entities to be deleted at once.</span></span>
   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="93c97-154">![Az entitáskapcsolatok szerkesztése vagy törlése](media/activities-entities-edit-delete.png "Az entitáskapcsolatok szerkesztése vagy törlése")</span><span class="sxs-lookup"><span data-stu-id="93c97-154">![Edit or delete the entity relationship](media/activities-entities-edit-delete.png "Edit or delete the entity relationship")</span></span>

3. <span data-ttu-id="93c97-155">**Törlés** ikon kiválasztása.</span><span class="sxs-lookup"><span data-stu-id="93c97-155">Select on the **Delete** icon.</span></span>

4. <span data-ttu-id="93c97-156">Hagyja jóvá a törlést.</span><span class="sxs-lookup"><span data-stu-id="93c97-156">Confirm your deletion.</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]