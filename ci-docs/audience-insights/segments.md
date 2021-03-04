---
title: Szegmensek létrehozása és kezelése
description: Hozzon létre ügyfelekből álló szegmenseket, és csoportosítsa őket különböző attribútumok alapján.
ms.date: 10/15/2020
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: m-hartmann
ms.author: mhart
ms.reviewer: jimsonc
manager: shellyha
ms.openlocfilehash: a1308f07ac3ba7d4b09931bab3d19b6dfaf479ee
ms.sourcegitcommit: 139548f8a2d0f24d54c4a6c404a743eeeb8ef8e0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/15/2021
ms.locfileid: "5270359"
---
# <a name="create-and-manage-segments"></a><span data-ttu-id="df9ac-103">Szegmensek létrehozása és kezelése</span><span class="sxs-lookup"><span data-stu-id="df9ac-103">Create and manage segments</span></span>

<span data-ttu-id="df9ac-104">A szegmensek segítségével csoportosíthatja ügyfeleit demográfiai-, tranzakciós- vagy viselkedési tulajdonságok alapján.</span><span class="sxs-lookup"><span data-stu-id="df9ac-104">Segments let you group your customers based on demographic, transactional, or behavioral attributes.</span></span> <span data-ttu-id="df9ac-105">A szegmensekkel népszerűsítheti az üzleti célok eléréséhez használható promóciós kampányokat, értékesítési tevékenységeket és ügyfélszolgálati tevékenységeket.</span><span class="sxs-lookup"><span data-stu-id="df9ac-105">You can use segments to target promotional campaigns, sales activities, and customer support actions to achieve your business goals.</span></span>

<span data-ttu-id="df9ac-106">Összetett szűrőket adhat meg az Ügyfélprofil entitás és kapcsolódó entitásai körül.</span><span class="sxs-lookup"><span data-stu-id="df9ac-106">You can define complex filters around the Customer Profile entity and its related entities.</span></span> <span data-ttu-id="df9ac-107">A feldolgozást követően minden szegmens létrehoz egy csoport olyan ügyfélrekordot, amellyel az exportálás után műveletek végezhetők.</span><span class="sxs-lookup"><span data-stu-id="df9ac-107">Each segment, after processing, creates a set of customer records that you can export and take action on.</span></span> <span data-ttu-id="df9ac-108">Bizonyos [szolgáltatási korlátozások](service-limits.md) érvényesek.</span><span class="sxs-lookup"><span data-stu-id="df9ac-108">Some [service limits](service-limits.md) apply.</span></span>

<span data-ttu-id="df9ac-109">Ha nincsen másként meghatározva, minden szegmens **Dinamikus szegmens**, amelyek ismétlődő ütemezés alapján frissítésre kerülnek.</span><span class="sxs-lookup"><span data-stu-id="df9ac-109">Unless stated otherwise, all segments are **Dynamic segments**, which are refreshed on a recurring schedule.</span></span>

<span data-ttu-id="df9ac-110">A következő példa bemutatja a szegmentációs képességet.</span><span class="sxs-lookup"><span data-stu-id="df9ac-110">The following example illustrates the segmentation capability.</span></span> <span data-ttu-id="df9ac-111">Egy szegmenst definiáltak azokhoz az ügyfelekhez, akik legalább $500 értékben árukat rendeltek az utolsó 90 napban, *és* részt vettek egy ügyfélszolgálat-hívásban, amelyet eszkaláltak.</span><span class="sxs-lookup"><span data-stu-id="df9ac-111">We've defined a segment for customers who ordered at least $500 of goods in the last 90 days *and* who were involved in a customer service call that got escalated.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="df9ac-112">![Több csoport](media/segmentation-group1-2.png "Több csoport")</span><span class="sxs-lookup"><span data-stu-id="df9ac-112">![Multiple groups](media/segmentation-group1-2.png "Multiple groups")</span></span>

## <a name="create-a-new-segment"></a><span data-ttu-id="df9ac-113">Új szegmens létrehozása</span><span class="sxs-lookup"><span data-stu-id="df9ac-113">Create a new segment</span></span>

<span data-ttu-id="df9ac-114">A szegmensek kezelése a **Szegmensek** oldalon történik.</span><span class="sxs-lookup"><span data-stu-id="df9ac-114">Segments are managed on the **Segments** page.</span></span>

1. <span data-ttu-id="df9ac-115">A célközönség információkban nyissa meg a **Szegmensek** oldalt.</span><span class="sxs-lookup"><span data-stu-id="df9ac-115">In audience insights, go to the **Segments** page.</span></span>

2. <span data-ttu-id="df9ac-116">Válassza az **új** > **üres szegmens** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="df9ac-116">Select **New** > **Blank segment**.</span></span>

3. <span data-ttu-id="df9ac-117">Az **Új szegmens** ablaktáblában válasszon egy szegmenstípust, és adja meg a **Név** értékét.</span><span class="sxs-lookup"><span data-stu-id="df9ac-117">In the **New segment** pane, choose a segment type and provide a **Name**.</span></span>

   <span data-ttu-id="df9ac-118">Tetszés szerint megadhat egy megjelenítendő nevet és egy leírást is, amely segít a szegmens azonosításában.</span><span class="sxs-lookup"><span data-stu-id="df9ac-118">Optionally, provide a display name, and a description that helps identifying the segment.</span></span>

4. <span data-ttu-id="df9ac-119">Válassza a **Következő** elemet a **Szegmensépítő** oldalára való eljutáshoz, ahol megadhat egy csoportot.</span><span class="sxs-lookup"><span data-stu-id="df9ac-119">Select **Next** to get to the **Segment builder** page where you define a group.</span></span> <span data-ttu-id="df9ac-120">A csoport az ügyfelek halmaza.</span><span class="sxs-lookup"><span data-stu-id="df9ac-120">A group is a set of customers.</span></span>

5. <span data-ttu-id="df9ac-121">Válassza ki az entitást, amelyben szerepel az attribútum, amely alapján szegmentálni szeretne.</span><span class="sxs-lookup"><span data-stu-id="df9ac-121">Choose the entity that includes the attribute you want to segment by.</span></span>

6. <span data-ttu-id="df9ac-122">Válassza ki a szegmenshez tartozó attribútumot.</span><span class="sxs-lookup"><span data-stu-id="df9ac-122">Choose the attribute to segment by.</span></span> <span data-ttu-id="df9ac-123">Ez az attribútum a következő négy értéktípus egyike lehet: numerikus, szöveges, dátum vagy logikai.</span><span class="sxs-lookup"><span data-stu-id="df9ac-123">This attribute can have one of four value types: numerical, string, date, or Boolean.</span></span>

7. <span data-ttu-id="df9ac-124">Válasszon egy operátort, és adja meg a kijelölt attribútum értékét.</span><span class="sxs-lookup"><span data-stu-id="df9ac-124">Choose an operator and a value for the selected attribute.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="df9ac-125">![Egyéni csoportszűrő](media/customer-group-numbers.png "Ügyfélcsoportszűrő")</span><span class="sxs-lookup"><span data-stu-id="df9ac-125">![Custom group filter](media/customer-group-numbers.png "Customer group filter")</span></span>

   |<span data-ttu-id="df9ac-126">Szám</span><span class="sxs-lookup"><span data-stu-id="df9ac-126">Number</span></span> |<span data-ttu-id="df9ac-127">Definíció</span><span class="sxs-lookup"><span data-stu-id="df9ac-127">Definition</span></span>  |
   |---------|---------|
   |<span data-ttu-id="df9ac-128">1</span><span class="sxs-lookup"><span data-stu-id="df9ac-128">1</span></span>     |<span data-ttu-id="df9ac-129">Entity</span><span class="sxs-lookup"><span data-stu-id="df9ac-129">Entity</span></span>          |
   |<span data-ttu-id="df9ac-130">2</span><span class="sxs-lookup"><span data-stu-id="df9ac-130">2</span></span>     |<span data-ttu-id="df9ac-131">Attribútum</span><span class="sxs-lookup"><span data-stu-id="df9ac-131">Attribute</span></span>          |
   |<span data-ttu-id="df9ac-132">3</span><span class="sxs-lookup"><span data-stu-id="df9ac-132">3</span></span>    |<span data-ttu-id="df9ac-133">Operátor</span><span class="sxs-lookup"><span data-stu-id="df9ac-133">Operator</span></span>         |
   |<span data-ttu-id="df9ac-134">4</span><span class="sxs-lookup"><span data-stu-id="df9ac-134">4</span></span>    |<span data-ttu-id="df9ac-135">Érték</span><span class="sxs-lookup"><span data-stu-id="df9ac-135">Value</span></span>         |

8. <span data-ttu-id="df9ac-136">Ha az entitás [kapcsolatokon](relationships.md) keresztül kapcsolódik az egyesített ügyfél entitáshoz, meg kell határoznia a kapcsolati útvonalat az érvényes szegmens létrehozásához.</span><span class="sxs-lookup"><span data-stu-id="df9ac-136">If the entity is connected to the unified customer entity through [relationships](relationships.md), you need to define the relationship path to create a valid segment.</span></span> <span data-ttu-id="df9ac-137">Adjon hozzá entitásokat a kapcsolati útvonalról, amíg ki nem tudja választani az **Ügyfél: CustomerInsights** entitást a legördülő menüből.</span><span class="sxs-lookup"><span data-stu-id="df9ac-137">Add the entities from the relationship path until you can select the **Customer:CustomerInsights** entity from the dropdown.</span></span> <span data-ttu-id="df9ac-138">Ezután válassza ki az **Összes rekordot** minden egyes feltételnél.</span><span class="sxs-lookup"><span data-stu-id="df9ac-138">Then, choose **All records** for each condition.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="df9ac-139">![Kapcsolati útvonal a szegmens létrehozása során](media/segments-multiple-relationships.png "Kapcsolati útvonal a szegmens létrehozása során")</span><span class="sxs-lookup"><span data-stu-id="df9ac-139">![Relationship path during segment creation](media/segments-multiple-relationships.png "Relationship path during segment creation")</span></span>

9. <span data-ttu-id="df9ac-140">Válassza a **Mentés** lehetőséget a szegmens mentéséhez.</span><span class="sxs-lookup"><span data-stu-id="df9ac-140">Select **Save** to save your segment.</span></span> <span data-ttu-id="df9ac-141">A rendszer menti a szegmenst és feldolgozza, ha az összes követelményt ellenőrizte.</span><span class="sxs-lookup"><span data-stu-id="df9ac-141">Your segment will be saved and processed if all requirements are validated.</span></span> <span data-ttu-id="df9ac-142">Ellenkező esetben vázlatként menti a program.</span><span class="sxs-lookup"><span data-stu-id="df9ac-142">Otherwise, it will be saved as a draft.</span></span>

10. <span data-ttu-id="df9ac-143">A **Szegmensek** oldalra a **Vissza a szegmensekhez** elemre kattintva léphet vissza.</span><span class="sxs-lookup"><span data-stu-id="df9ac-143">Select **Back to segments** to go back to the **Segments** page.</span></span>

## <a name="manage-existing-segments"></a><span data-ttu-id="df9ac-144">Meglévő szegmensek kezelése</span><span class="sxs-lookup"><span data-stu-id="df9ac-144">Manage existing segments</span></span>

<span data-ttu-id="df9ac-145">A **szegmensek** lapon megtekintheti az összes mentett szegmenst, és kezelheti azokat.</span><span class="sxs-lookup"><span data-stu-id="df9ac-145">On the **Segments** page, you can view all your saved segments and manage them.</span></span>

<span data-ttu-id="df9ac-146">Minden szegmenshez egy sor tartozik; ez a sor további információkat tartalmaz a szegmensről.</span><span class="sxs-lookup"><span data-stu-id="df9ac-146">Each segment is represented by a row that includes additional information about the segment.</span></span>

<span data-ttu-id="df9ac-147">A szegmenseket az oszlop fejlécének kiválasztásával rendezheti egy oszlopba.</span><span class="sxs-lookup"><span data-stu-id="df9ac-147">You can sort the segments in a column by selecting the column heading.</span></span>

<span data-ttu-id="df9ac-148">A jobb felső sarokban lévő **Keresés** mezővel szűrheti a szegmenseket.</span><span class="sxs-lookup"><span data-stu-id="df9ac-148">Use the **Search** box in the top-right corner to filter the segments.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="df9ac-149">![Meglévő szegmensek kezelésére szolgáló lehetőségek](media/segments-selected-segment.png "Meglévő szegmensek kezelésére szolgáló lehetőségek")</span><span class="sxs-lookup"><span data-stu-id="df9ac-149">![Options to manage an existing segment](media/segments-selected-segment.png "Options to manage an existing segment")</span></span>

<span data-ttu-id="df9ac-150">Szegmens kiválasztása esetén a következő művelet használható:</span><span class="sxs-lookup"><span data-stu-id="df9ac-150">The following action are available when you select a segment:</span></span>

- <span data-ttu-id="df9ac-151">**Megtekintés** a szegmens részleteinek, köztük a tagszám trendjének megtekintése és a szegmens tagjainak előnézete.</span><span class="sxs-lookup"><span data-stu-id="df9ac-151">**View** the segment details, including member count trend a preview of segment members.</span></span>
- <span data-ttu-id="df9ac-152">**Szerkesztés** a szegmens szerkesztése a tulajdonságainak módosításához.</span><span class="sxs-lookup"><span data-stu-id="df9ac-152">**Edit** the segment to change its properties.</span></span>
- <span data-ttu-id="df9ac-153">**Frissítés** a szegmens frissítése a legfrissebb adatok felvételéhez.</span><span class="sxs-lookup"><span data-stu-id="df9ac-153">**Refresh** the segment to include the latest data.</span></span>
- <span data-ttu-id="df9ac-154">Szegmens **Aktiválása** vagy **inaktiválása**.</span><span class="sxs-lookup"><span data-stu-id="df9ac-154">**Activate** or **Deactivate** the segment.</span></span> <span data-ttu-id="df9ac-155">A szegmensek két lehetséges állapottal rendelkeznek – aktívak vagy inaktívak.</span><span class="sxs-lookup"><span data-stu-id="df9ac-155">Segments have two possible states - active or inactive.</span></span> <span data-ttu-id="df9ac-156">A szegmensek szerkesztésekor hasznosnak bizonyulnak ezek az állapotok.</span><span class="sxs-lookup"><span data-stu-id="df9ac-156">These states come in handy when editing a segment.</span></span> <span data-ttu-id="df9ac-157">Inaktív szegmensek esetén a szegmens definíciója létezik, de még nem tartalmaz ügyfeleket.</span><span class="sxs-lookup"><span data-stu-id="df9ac-157">For inactive segments, the segment definition exists but it doesn't contain any customers yet.</span></span> <span data-ttu-id="df9ac-158">A szegmens aktiválásakor az állapota az "inaktív" értékről "aktív" állapotra változik, és a szegmens meghatározásnak megfelelő ügyfeleket keresi meg.</span><span class="sxs-lookup"><span data-stu-id="df9ac-158">When you activate a segment, its state changes from 'inactive' to 'active" and it starts looking for customers that match the segment definition.</span></span> <span data-ttu-id="df9ac-159">Ha egy [ütemezett frissítés](system.md#schedule-tab) be van állítva, az inaktív szegmensek **állapota** **kihagyva** állapotú , jelezve, hogy a frissítést nem is kísérelte meg.</span><span class="sxs-lookup"><span data-stu-id="df9ac-159">If a [scheduled refresh](system.md#schedule-tab) is configured, inactive segments have the **Status** listed as **Skipped**, indicating that a refresh wasn't even attempted.</span></span> <span data-ttu-id="df9ac-160">Inaktív szegmens aktiválásakor a rendszer frissíti, és bekerül az ütemezett frissítésekbe.</span><span class="sxs-lookup"><span data-stu-id="df9ac-160">When an inactive segment is activated, it will refresh and will be included in scheduled refreshes.</span></span>
  <span data-ttu-id="df9ac-161">Másik lehetőségként használhatja **Ütemezés később** funkcióit az **Aktiválás/inaktiválás**, ahol megadhat egy adott szegmens aktiválására és inaktiválására vonatkozó jövőbeli dátumot és időpontot.</span><span class="sxs-lookup"><span data-stu-id="df9ac-161">Alternatively, you can use the **Schedule later** functionality in the **Activate/Deactivate** dropdown to specify a future date and time for activation and deactivation of a particular segment.</span></span>
- <span data-ttu-id="df9ac-162">Szegmens **átnevezése**.</span><span class="sxs-lookup"><span data-stu-id="df9ac-162">**Rename** the segment.</span></span>
- <span data-ttu-id="df9ac-163">A tagok listájának **letöltése** .CSV fájlként.</span><span class="sxs-lookup"><span data-stu-id="df9ac-163">**Download** the list of members as a .CSV file.</span></span>
- <span data-ttu-id="df9ac-164">A **Hozzáadás ehhez:** lehetőség a szegmensben szereplő ügyfelek azonosítóinak listáját egy másik alkalmazásban feldolgozásra küldi.</span><span class="sxs-lookup"><span data-stu-id="df9ac-164">**Add to** option sends the list of customer IDs in the segment for processing in another application.</span></span>
- <span data-ttu-id="df9ac-165">Szegmens **törlése**.</span><span class="sxs-lookup"><span data-stu-id="df9ac-165">**Delete** the segment.</span></span>

## <a name="refresh-segments"></a><span data-ttu-id="df9ac-166">Szegmensek frissítése</span><span class="sxs-lookup"><span data-stu-id="df9ac-166">Refresh segments</span></span>

<span data-ttu-id="df9ac-167">Az összes szegmenst egyszerre frissítheti a **Szegmensek** oldal **Az összes frissítése** elemével. Ha nem szeretné frissíteni az összes szegmenst, jelölje ki a frissítendőket, és válassza a **Frissítés** lehetőséget a beállítások között.</span><span class="sxs-lookup"><span data-stu-id="df9ac-167">You can refresh all segments at once by selecting **Refresh all** on the **Segments** page or you can refresh one or multiple segments when you select them and choose **Refresh** in from the options.</span></span> <span data-ttu-id="df9ac-168">Másik lehetőségként beállíthat egy ismétlődő frissítést is a **Felügyelet** > **Rendszer** > **Ütemezés** pontban.</span><span class="sxs-lookup"><span data-stu-id="df9ac-168">Alternatively, you can configure a recurring refresh on **Admin** > **System** > **Schedule**.</span></span>

> [!TIP]
> <span data-ttu-id="df9ac-169">A feladatokhoz/folyamatokhoz [hatféle állapot](system.md#status-types) tartozhat.</span><span class="sxs-lookup"><span data-stu-id="df9ac-169">There are [six types of status](system.md#status-types) for tasks/processes.</span></span> <span data-ttu-id="df9ac-170">Emellett a legtöbb folyamat [más alsóbb szintű folyamatoktól is függ](system.md#refresh-policies).</span><span class="sxs-lookup"><span data-stu-id="df9ac-170">Additionally, most processes [depend on other downstream processes](system.md#refresh-policies).</span></span> <span data-ttu-id="df9ac-171">Kiválaszthatja egy folyamat állapotát, és megtekintheti a hozzá tartozó teljes feladat folyamatának részleteit.</span><span class="sxs-lookup"><span data-stu-id="df9ac-171">You can select the status of a process to see details on the progress of the entire job.</span></span> <span data-ttu-id="df9ac-172">Miután kiválasztotta a **Részletek megtekintése** lehetőséget a feladat egyik feladatához, további információk jelennek meg: feldolgozási idő, legutóbbi feldolgozás dátuma, és a feladathoz társított összes hiba és figyelmeztetés.</span><span class="sxs-lookup"><span data-stu-id="df9ac-172">After selecting **See details** for one of the job's tasks, you find additional information: processing time, the last processing date, and all errors and warnings associated with the task.</span></span>

## <a name="download-and-export-segments"></a><span data-ttu-id="df9ac-173">Szegmensek letöltése és exportálása</span><span class="sxs-lookup"><span data-stu-id="df9ac-173">Download and export segments</span></span>

<span data-ttu-id="df9ac-174">A szegmensek egy CSV-fájlba tölthetők le, illetve exportálhatók a Dynamics 365 Sales programba.</span><span class="sxs-lookup"><span data-stu-id="df9ac-174">You can download your segments to a CSV file or export them to Dynamics 365 Sales.</span></span>

### <a name="download-segments-to-a-csv-file"></a><span data-ttu-id="df9ac-175">Szegmensek letöltése CSV-fájlba</span><span class="sxs-lookup"><span data-stu-id="df9ac-175">Download segments to a CSV file</span></span>

1. <span data-ttu-id="df9ac-176">A célközönség információkban nyissa meg a **Szegmensek** oldalt.</span><span class="sxs-lookup"><span data-stu-id="df9ac-176">In audience insights, go to the **Segments** page.</span></span>

2. <span data-ttu-id="df9ac-177">Jelöljön ki egy adott szegmens csempéjében a három pontot.</span><span class="sxs-lookup"><span data-stu-id="df9ac-177">Select the ellipsis in a specific segment's tile.</span></span>

3. <span data-ttu-id="df9ac-178">A műveletek legördülő listáról válassza a **Letöltés CSV-ként** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="df9ac-178">Select **Download as CSV** from the actions drop-down list.</span></span>

### <a name="export-segments-to-dynamics-365-sales"></a><span data-ttu-id="df9ac-179">Szegmensek exportálása a Dynamics 365 Sales alkalmazásba</span><span class="sxs-lookup"><span data-stu-id="df9ac-179">Export segments to Dynamics 365 Sales</span></span>

<span data-ttu-id="df9ac-180">Mielőtt exportálja a szegmenseket a Dynamics 365 Sales programba, egy rendszergazdának [létre kell hoznia az exportálási célhelyet](export-destinations.md) a Dynamics 365 Sales-hez.</span><span class="sxs-lookup"><span data-stu-id="df9ac-180">Before exporting segments to Dynamics 365 Sales, an admin needs to [create the export destination](export-destinations.md) for Dynamics 365 Sales.</span></span>

1. <span data-ttu-id="df9ac-181">A célközönség információkban nyissa meg a **Szegmensek** oldalt.</span><span class="sxs-lookup"><span data-stu-id="df9ac-181">In audience insights, go to the **Segments** page.</span></span>

2. <span data-ttu-id="df9ac-182">Jelöljön ki egy adott szegmens csempéjében a három pontot.</span><span class="sxs-lookup"><span data-stu-id="df9ac-182">Select the ellipsis in a specific segment's tile.</span></span>

3. <span data-ttu-id="df9ac-183">Válassza a **Hozzáadás** lehetőséget a Műveletek legördülő listából, és jelölje ki az exportálni kívánt célhelyet.</span><span class="sxs-lookup"><span data-stu-id="df9ac-183">Select **Add to** from the actions drop-down list and select the export destination you want to send the data to.</span></span>

## <a name="draft-mode-for-segments"></a><span data-ttu-id="df9ac-184">Vázlat mód szegmensekhez</span><span class="sxs-lookup"><span data-stu-id="df9ac-184">Draft mode for segments</span></span>

<span data-ttu-id="df9ac-185">Ha a szegmens feldolgozására vonatkozó összes követelmény nem teljesül, vázlatként mentheti a szegmenst, és hozzáférhet a **Szegmensek** oldalról.</span><span class="sxs-lookup"><span data-stu-id="df9ac-185">If not all requirements to process a segment are met, you can save the segment as a draft and access it from the **Segments** page.</span></span>

<span data-ttu-id="df9ac-186">Inaktív szegmensként menti a program, és mindaddig nem aktiválható, amíg érvényes nem lesz.</span><span class="sxs-lookup"><span data-stu-id="df9ac-186">It will be saved as an inactive segment, and can't be activated it until it's valid.</span></span>

## <a name="add-more-conditions-to-a-group"></a><span data-ttu-id="df9ac-187">További feltételek hozzáadása csoporthoz</span><span class="sxs-lookup"><span data-stu-id="df9ac-187">Add more conditions to a group</span></span>

<span data-ttu-id="df9ac-188">Ha további feltételeket szeretne hozzáadni egy csoporthoz, akkor két logikai operátort használhat:</span><span class="sxs-lookup"><span data-stu-id="df9ac-188">To add more conditions to a group, you can use two logical operators:</span></span>

- <span data-ttu-id="df9ac-189">**ÉS** operátor: mindkét feltételnek a szegmentálási folyamat részeként kell teljesülnie.</span><span class="sxs-lookup"><span data-stu-id="df9ac-189">**AND** operator: Both conditions must be met as part of the segmentation process.</span></span> <span data-ttu-id="df9ac-190">Ez a beállítás akkor a leghasznosabb, ha különböző entitások között határoz meg feltételeket.</span><span class="sxs-lookup"><span data-stu-id="df9ac-190">This option is most useful when you define conditions across different entities.</span></span>

- <span data-ttu-id="df9ac-191">**VAGY** operátor: a szegmentálási folyamat részeként az egyik feltételnek meg kell felelnie.</span><span class="sxs-lookup"><span data-stu-id="df9ac-191">**OR** operator: Either one of the conditions needs to be met as part of the segmentation process.</span></span> <span data-ttu-id="df9ac-192">Ez a beállítás akkor a leghasznosabb, ha különböző feltételeket ad meg ugyanahhoz az entitáshoz.</span><span class="sxs-lookup"><span data-stu-id="df9ac-192">This option is most useful when you define multiple conditions for the same entity.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="df9ac-193">![VAGY operátor, ahol valamelyik feltételt teljesíteni kell](media/segmentation-either-condition.png "VAGY operátor, ahol valamelyik feltételt teljesíteni kell")</span><span class="sxs-lookup"><span data-stu-id="df9ac-193">![OR operator where either condition needs to be met](media/segmentation-either-condition.png "OR operator where either condition needs to be met")</span></span>

<span data-ttu-id="df9ac-194">Jelenleg lehetséges egy **VAGY** operátor beágyazása egy **ÉS** operátor alá, de fordítva nem.</span><span class="sxs-lookup"><span data-stu-id="df9ac-194">It's currently possible to nest an **OR** operator under an **AND** operator, but not the other way around.</span></span>

## <a name="combine-multiple-groups"></a><span data-ttu-id="df9ac-195">Több csoport egyesítése</span><span class="sxs-lookup"><span data-stu-id="df9ac-195">Combine multiple groups</span></span>

<span data-ttu-id="df9ac-196">Mindegyik csoport adott ügyfelek csoportját hoz létre.</span><span class="sxs-lookup"><span data-stu-id="df9ac-196">Each group produces a specific set of customers.</span></span> <span data-ttu-id="df9ac-197">A csoportok kombinálásával szerepeltetheti a vállalati esethez szükséges ügyfeleket.</span><span class="sxs-lookup"><span data-stu-id="df9ac-197">You can combine these groups to include the customers required for your business case.</span></span>

1. <span data-ttu-id="df9ac-198">A célközönség információkban nyissa meg a **Szegmens** oldalt, és válasszon egy szegmenst.</span><span class="sxs-lookup"><span data-stu-id="df9ac-198">In audience insights, go to the **Segments** page and select a segment.</span></span>

2. <span data-ttu-id="df9ac-199">Válassza a **Csoport hozzáadása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="df9ac-199">Select **Add Group**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="df9ac-200">![Ügyfélcsoport hozzáadása csoport](media/customer-group-add-group.png "Ügyfélcsoport hozzáadása csoport")</span><span class="sxs-lookup"><span data-stu-id="df9ac-200">![Customer group add group](media/customer-group-add-group.png "Customer group add group")</span></span>

3. <span data-ttu-id="df9ac-201">Válasszon az alábbi operátorok közül: **Halmaz**, **Metszet** vagy **Kivéve**.</span><span class="sxs-lookup"><span data-stu-id="df9ac-201">Select one of the following set operators: **Union**, **Intersect**, or **Except**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="df9ac-202">![Ügyfélcsoport hozzáadása egyesülés](media/customer-group-union.png "Ügyfélcsoport hozzáadása egyesülés")</span><span class="sxs-lookup"><span data-stu-id="df9ac-202">![Customer group add union](media/customer-group-union.png "Customer group add union")</span></span>

   <span data-ttu-id="df9ac-203">Egy beállított operátor kiválasztásával új csoportot adhat meg.</span><span class="sxs-lookup"><span data-stu-id="df9ac-203">Select a set operator to define a new group.</span></span> <span data-ttu-id="df9ac-204">Különböző csoportok elmentésével határozza meg, hogy melyik adatok megtartandók:</span><span class="sxs-lookup"><span data-stu-id="df9ac-204">Save different groups to determine what data gets retained:</span></span>

   - <span data-ttu-id="df9ac-205">Az **Egyesülés** egyesíti a két csoportot.</span><span class="sxs-lookup"><span data-stu-id="df9ac-205">**Union** unites the two groups.</span></span>

   - <span data-ttu-id="df9ac-206">A **Metszet** a két csoport átfedését veszi.</span><span class="sxs-lookup"><span data-stu-id="df9ac-206">**Intersect** overlaps the two groups.</span></span> <span data-ttu-id="df9ac-207">Csak az az adat *amely közös* kerül megtartásra mindkét egységesített csoportban.</span><span class="sxs-lookup"><span data-stu-id="df9ac-207">Only data that *is common* to both groups is retained in the unified group.</span></span>

   - <span data-ttu-id="df9ac-208">**Kivéve** kombinálja a két csoportot.</span><span class="sxs-lookup"><span data-stu-id="df9ac-208">**Except** combines the two groups.</span></span> <span data-ttu-id="df9ac-209">Csak azon adat kerül megtartásra az A csoportban, amely *nem közös* a B csoport adatival.</span><span class="sxs-lookup"><span data-stu-id="df9ac-209">Only data in group A that *is not common* to data in group B is retained.</span></span>

## <a name="view-processing-history-and-segment-members"></a><span data-ttu-id="df9ac-210">A feldolgozási előzmények és a szegmenstagok megtekintése</span><span class="sxs-lookup"><span data-stu-id="df9ac-210">View processing history and segment members</span></span>

<span data-ttu-id="df9ac-211">A szegmensre vonatkozó konszolidált adatokat a részleteinek áttekintésével tekintheti meg.</span><span class="sxs-lookup"><span data-stu-id="df9ac-211">You can see consolidated data about a segment by reviewing its details.</span></span>

<span data-ttu-id="df9ac-212">A **Szegmens** lapon válassza ki az áttekinteni kívánt szegments.</span><span class="sxs-lookup"><span data-stu-id="df9ac-212">On the **Segments** page, select the segment you want to review.</span></span>

<span data-ttu-id="df9ac-213">Az oldal felső részén egy trendgráf látható, amely a tagok számának változásait ábrázolja.</span><span class="sxs-lookup"><span data-stu-id="df9ac-213">The upper part of the page includes a trend graph that visualizes changes in member count.</span></span> <span data-ttu-id="df9ac-214">Vigye az egérmutatót az adatpontok fölé, és tekintse meg egy adott napon a tagok számát.</span><span class="sxs-lookup"><span data-stu-id="df9ac-214">Hover over data points to see the member count on a specific date.</span></span>

<span data-ttu-id="df9ac-215">Frissítheti az ábrázolás időkeretét.</span><span class="sxs-lookup"><span data-stu-id="df9ac-215">You can update the time frame of the visualization.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="df9ac-216">![Szegmens időtartománya](media/segment-time-range.png "Szegmens időtartománya")</span><span class="sxs-lookup"><span data-stu-id="df9ac-216">![Segment time range](media/segment-time-range.png "Segment time range")</span></span>

<span data-ttu-id="df9ac-217">Az alsó rész a szegmenstagok listáját tartalmazza.</span><span class="sxs-lookup"><span data-stu-id="df9ac-217">The lower part contains a list of the segment members.</span></span>

> [!NOTE]
> <span data-ttu-id="df9ac-218">Az adott listában megjelenő mezők a szegmens entitásainak attribútumain alapulnak.</span><span class="sxs-lookup"><span data-stu-id="df9ac-218">Fields that appear in this list are based on the attributes of your segment's entities.</span></span>
>
><span data-ttu-id="df9ac-219">A lista az egyeztetett szegmestagok előzetes verziója, és a szegmens első 100 rekordját mutatja, így gyorsan kiértékelheti, és szükség esetén felülvizsgálhatja a meghatározásokat.</span><span class="sxs-lookup"><span data-stu-id="df9ac-219">The list is a preview of the matching segment members and shows the first 100 records of your segment so that you can quickly evaluate it and review its definitions if needed.</span></span> <span data-ttu-id="df9ac-220">Az összes egyező bejegyzés megjelenítéséhez [exportálnia kell a szegmenst](export-destinations.md).</span><span class="sxs-lookup"><span data-stu-id="df9ac-220">To see all matching records, you need to [export the segment](export-destinations.md).</span></span>

## <a name="quick-segments"></a><span data-ttu-id="df9ac-221">Gyors szegmens</span><span class="sxs-lookup"><span data-stu-id="df9ac-221">Quick segments</span></span>

<span data-ttu-id="df9ac-222">A szegmensszerkesztőn kívül van még egy módja a szegmensek létrehozásának.</span><span class="sxs-lookup"><span data-stu-id="df9ac-222">In addition to the segment builder, there's another path for creating segments.</span></span> <span data-ttu-id="df9ac-223">A gyors szegmensek segítségével gyorsan és azonnali betekintő információkkal hozhat létre egyszerű szegmenseket egyetlen operátorral.</span><span class="sxs-lookup"><span data-stu-id="df9ac-223">Quick segments let you build simple segments with a single operator quickly and with instant insights.</span></span>

1. <span data-ttu-id="df9ac-224">A **szegmensek** lapon válassza az **új** > **Gyorslétrehozási űrlap** elemet.</span><span class="sxs-lookup"><span data-stu-id="df9ac-224">On the **Segments** page, select **New** > **Quickly create from**.</span></span>

   - <span data-ttu-id="df9ac-225">Válassza a **profilok** lehetőséget, ha az egyesített Ügyfél entitáson alapuló szegmenset szeretne létrehozni.</span><span class="sxs-lookup"><span data-stu-id="df9ac-225">Select the **Profiles** option to build a segment that is based on the unified Customer entity.</span></span>
   - <span data-ttu-id="df9ac-226">Válassza az **Mérőszámok** lehetőséget, ha a **Mérőszámok** oldalon korábban létrehozott Ügyfélattribútum típusú mérőszámok mindegyikéhez szeretne szegmenst létrehozni.</span><span class="sxs-lookup"><span data-stu-id="df9ac-226">Select the **Measures** option to build a segment around each of the Customer Attribute type of measures you have previously created on the **Measures** page.</span></span>
   - <span data-ttu-id="df9ac-227">Válassza az **Információ** lehetőséget, ha egy szegmenst szeretne létrehozni az egyik olyan kimeneti entitás köré, amelyet vagy az **Előrejelzések** vagy az **egyéni modellek** használatával hozott létre.</span><span class="sxs-lookup"><span data-stu-id="df9ac-227">Select the **Intelligence** option to build a segment around one of the output entities you generated using either the **Predictions** or **Custom Models** capabilities.</span></span>

2. <span data-ttu-id="df9ac-228">Az **új gyors szegmens** párbeszédpanelen jelöljön ki egy attribútumot a **Mező** legördülő listában.</span><span class="sxs-lookup"><span data-stu-id="df9ac-228">In the **New quick segment** dialog box, select an attribute from the **Field** dropdown.</span></span>

3. <span data-ttu-id="df9ac-229">A rendszer néhány további betekintést biztosít, amelyek segítségével jobb szegmenseket hozhat létre az ügyfelek számára.</span><span class="sxs-lookup"><span data-stu-id="df9ac-229">The system will provide some additional insights that help you create better segments of your customers.</span></span>
   - <span data-ttu-id="df9ac-230">A kategorikus mezők esetén 10 első számú ügyfél számít.</span><span class="sxs-lookup"><span data-stu-id="df9ac-230">For categorical fields, we'll show 10 top customer counts.</span></span> <span data-ttu-id="df9ac-231">Válasszon egy **Értéket**, és válassza a **Felülvizsgálat** elemet.</span><span class="sxs-lookup"><span data-stu-id="df9ac-231">Choose a **Value** and select **Review**.</span></span>

   - <span data-ttu-id="df9ac-232">Numerikus attribútumok esetében a rendszer azt mutatja, hogy az egyes ügyfelek percentilis értékei alá milyen attribútumértékek tartoznak.</span><span class="sxs-lookup"><span data-stu-id="df9ac-232">For a numerical attribute, the system will show what attribute value falls under each customer's percentile.</span></span> <span data-ttu-id="df9ac-233">Válasszon egy **operátort** és egy **értéket**, majd válassza a **Felülvizsgálat** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="df9ac-233">Choose an **Operator** and a **Value**, then select **Review**.</span></span>

4. <span data-ttu-id="df9ac-234">A rendszer megadja a **Becsült szegmensméret** értékét.</span><span class="sxs-lookup"><span data-stu-id="df9ac-234">The system will provide you with an **Estimated segment size**.</span></span> <span data-ttu-id="df9ac-235">Kiválaszthatja, hogy létrehozza-e a megadott szegmenst, vagy először újra meg szeretné vizsgálni, hogy egy másik szegmens méretet kap-e.</span><span class="sxs-lookup"><span data-stu-id="df9ac-235">You can choose whether to generate the segment you've defined, or first revisit it to get a different segment size.</span></span>

    > [!div class="mx-imgBorder"]
    > <span data-ttu-id="df9ac-236">![Gyorsszegmens neve és becslése](media/quick-segment-name.png "Gyorsszegmens neve és becslése")</span><span class="sxs-lookup"><span data-stu-id="df9ac-236">![Name and estimation for a quick segment](media/quick-segment-name.png "Name and estimation for a quick segment")</span></span>

5. <span data-ttu-id="df9ac-237">Adjon meg egy **Név** értéket a szegmens számára.</span><span class="sxs-lookup"><span data-stu-id="df9ac-237">Provide a **Name** for your segment.</span></span> <span data-ttu-id="df9ac-238">Másik lehetőségként adjon meg **Megjelenítendő nevet**.</span><span class="sxs-lookup"><span data-stu-id="df9ac-238">Optionally, provide a **Display name**.</span></span>

6. <span data-ttu-id="df9ac-239">Válassza a **Mentés** lehetőséget a szegmens létrehozásához.</span><span class="sxs-lookup"><span data-stu-id="df9ac-239">Select **Save** to create your segment.</span></span>

7. <span data-ttu-id="df9ac-240">Miután a szegmens befejezte a feldolgozást, megtekintheti azt a létrehozott többi szegmenshez hasonlóan.</span><span class="sxs-lookup"><span data-stu-id="df9ac-240">After the segment has finished processing, you can view it like any other segment you've created.</span></span>

<span data-ttu-id="df9ac-241">A következő esetekben javasoljuk, hogy ne a javasolt szegmensek lehetőséget használja, hanem a szegmensépítő használatát:</span><span class="sxs-lookup"><span data-stu-id="df9ac-241">For the following scenarios, we advise using the segment builder rather than the recommended segments capability:</span></span>

- <span data-ttu-id="df9ac-242">Szegmensek létrehozása szűrőkkel kategorikus mezőkön, ahol az operátor eltér a **Létezik** operátortól</span><span class="sxs-lookup"><span data-stu-id="df9ac-242">Creating segments with filters on categorical fields where the operator is different than the **Is** operator</span></span>
- <span data-ttu-id="df9ac-243">Szegmensek létrehozása szűrővel azoknál a numerikus mezőknél, ahol az operátor más, mint a **Között**, **Nagyobb, mint** és **Kisebb, mint** operátor</span><span class="sxs-lookup"><span data-stu-id="df9ac-243">Creating segments with filters on numerical fields where the operator is different than the **Between**, **Greater than**, and **Less than** operators</span></span>
- <span data-ttu-id="df9ac-244">A szegmensek létrehozása szűrőkkel a dátum típusú mezőkön</span><span class="sxs-lookup"><span data-stu-id="df9ac-244">Creating segments with filters on date type fields</span></span>

## <a name="next-steps"></a><span data-ttu-id="df9ac-245">Következő lépések</span><span class="sxs-lookup"><span data-stu-id="df9ac-245">Next steps</span></span>

<span data-ttu-id="df9ac-246">[Exportáljon egy szegmenst](export-destinations.md), és fedezze fel az [Ügyfélkártya](customer-card-add-in.md) és [Összekötők](export-power-bi.md) elemeket, az ügyfélszintű információkhoz.</span><span class="sxs-lookup"><span data-stu-id="df9ac-246">[Export a segment](export-destinations.md) and explore the [Customer Card](customer-card-add-in.md) and [Connectors](export-power-bi.md) to get insights on the customer level.</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]