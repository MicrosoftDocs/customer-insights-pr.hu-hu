---
title: Szegmensek létrehozása és kezelése
description: Hozzon létre ügyfelekből álló szegmenseket, és csoportosítsa őket különböző attribútumok alapján.
ms.date: 03/02/2021
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: JimsonChalissery
ms.author: jimsonc
ms.reviewer: mhart
manager: shellyha
ms.openlocfilehash: 4a6e8a3216a2c0738d60247054afa9fc18412f55
ms.sourcegitcommit: bae40184312ab27b95c140a044875c2daea37951
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/15/2021
ms.locfileid: "5597055"
---
# <a name="create-and-manage-segments"></a><span data-ttu-id="8004a-103">Szegmensek létrehozása és kezelése</span><span class="sxs-lookup"><span data-stu-id="8004a-103">Create and manage segments</span></span>

<span data-ttu-id="8004a-104">A szegmensek segítségével csoportosíthatja ügyfeleit demográfiai-, tranzakciós- vagy viselkedési tulajdonságok alapján.</span><span class="sxs-lookup"><span data-stu-id="8004a-104">Segments let you group your customers based on demographic, transactional, or behavioral attributes.</span></span> <span data-ttu-id="8004a-105">A szegmensekkel népszerűsítheti az üzleti célok eléréséhez használható promóciós kampányokat, értékesítési tevékenységeket és ügyfélszolgálati tevékenységeket.</span><span class="sxs-lookup"><span data-stu-id="8004a-105">You can use segments to target promotional campaigns, sales activities, and customer support actions to achieve your business goals.</span></span>

<span data-ttu-id="8004a-106">Összetett szűrőket adhat meg az Ügyfélprofil entitás és kapcsolódó entitásai körül.</span><span class="sxs-lookup"><span data-stu-id="8004a-106">You can define complex filters around the Customer Profile entity and its related entities.</span></span> <span data-ttu-id="8004a-107">A feldolgozást követően minden szegmens létrehoz egy csoport olyan ügyfélrekordot, amellyel az exportálás után műveletek végezhetők.</span><span class="sxs-lookup"><span data-stu-id="8004a-107">Each segment, after processing, creates a set of customer records that you can export and take action on.</span></span> <span data-ttu-id="8004a-108">Bizonyos [szolgáltatási korlátozások](service-limits.md) érvényesek.</span><span class="sxs-lookup"><span data-stu-id="8004a-108">Some [service limits](service-limits.md) apply.</span></span>

<span data-ttu-id="8004a-109">Ha nincsen másként meghatározva, minden szegmens **Dinamikus szegmens**, amelyek ismétlődő ütemezés alapján frissítésre kerülnek.</span><span class="sxs-lookup"><span data-stu-id="8004a-109">Unless stated otherwise, all segments are **Dynamic segments**, which are refreshed on a recurring schedule.</span></span>

<span data-ttu-id="8004a-110">A következő példa bemutatja a szegmentációs képességet.</span><span class="sxs-lookup"><span data-stu-id="8004a-110">The following example illustrates the segmentation capability.</span></span> <span data-ttu-id="8004a-111">Egy szegmenst definiáltak azokhoz az ügyfelekhez, akik legalább $500 értékben árukat rendeltek az utolsó 90 napban, *és* részt vettek egy ügyfélszolgálat-hívásban, amelyet eszkaláltak.</span><span class="sxs-lookup"><span data-stu-id="8004a-111">We've defined a segment for customers who ordered at least $500 of goods in the last 90 days *and* who were involved in a customer service call that got escalated.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="8004a-112">![Több csoport](media/segmentation-group1-2.png "Több csoport")</span><span class="sxs-lookup"><span data-stu-id="8004a-112">![Multiple groups](media/segmentation-group1-2.png "Multiple groups")</span></span>

## <a name="create-a-new-segment"></a><span data-ttu-id="8004a-113">Új szegmens létrehozása</span><span class="sxs-lookup"><span data-stu-id="8004a-113">Create a new segment</span></span>

<span data-ttu-id="8004a-114">A szegmensek kezelése a **Szegmensek** oldalon történik.</span><span class="sxs-lookup"><span data-stu-id="8004a-114">Segments are managed on the **Segments** page.</span></span>

1. <span data-ttu-id="8004a-115">A célközönség információkban nyissa meg a **Szegmensek** oldalt.</span><span class="sxs-lookup"><span data-stu-id="8004a-115">In audience insights, go to the **Segments** page.</span></span>

1. <span data-ttu-id="8004a-116">Válassza az **új** > **üres szegmens** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="8004a-116">Select **New** > **Blank segment**.</span></span>

1. <span data-ttu-id="8004a-117">Az **Új szegmens** ablaktáblában válasszon egy szegmenstípust, és adja meg a **Név** értékét.</span><span class="sxs-lookup"><span data-stu-id="8004a-117">In the **New segment** pane, choose a segment type and provide a **Name**.</span></span>

   <span data-ttu-id="8004a-118">Tetszés szerint megadhat egy megjelenítendő nevet és egy leírást is, amely segít a szegmens azonosításában.</span><span class="sxs-lookup"><span data-stu-id="8004a-118">Optionally, provide a display name, and a description that helps identifying the segment.</span></span>

1. <span data-ttu-id="8004a-119">Válassza a **Következő** elemet a **Szegmensépítő** oldalára való eljutáshoz, ahol megadhat egy csoportot.</span><span class="sxs-lookup"><span data-stu-id="8004a-119">Select **Next** to get to the **Segment builder** page where you define a group.</span></span> <span data-ttu-id="8004a-120">A csoport az ügyfelek halmaza.</span><span class="sxs-lookup"><span data-stu-id="8004a-120">A group is a set of customers.</span></span>

1. <span data-ttu-id="8004a-121">Válassza ki az entitást, amelyben szerepel az attribútum, amely alapján szegmentálni szeretne.</span><span class="sxs-lookup"><span data-stu-id="8004a-121">Choose the entity that includes the attribute you want to segment by.</span></span>

1. <span data-ttu-id="8004a-122">Válassza ki a szegmenshez tartozó attribútumot.</span><span class="sxs-lookup"><span data-stu-id="8004a-122">Choose the attribute to segment by.</span></span> <span data-ttu-id="8004a-123">Ez az attribútum a következő négy értéktípus egyike lehet: numerikus, szöveges, dátum vagy logikai.</span><span class="sxs-lookup"><span data-stu-id="8004a-123">This attribute can have one of four value types: numerical, string, date, or Boolean.</span></span>

1. <span data-ttu-id="8004a-124">Válasszon egy operátort, és adja meg a kijelölt attribútum értékét.</span><span class="sxs-lookup"><span data-stu-id="8004a-124">Choose an operator and a value for the selected attribute.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="8004a-125">![Egyéni csoportszűrő](media/customer-group-numbers.png "Ügyfélcsoportszűrő")</span><span class="sxs-lookup"><span data-stu-id="8004a-125">![Custom group filter](media/customer-group-numbers.png "Customer group filter")</span></span>

   |<span data-ttu-id="8004a-126">Szám</span><span class="sxs-lookup"><span data-stu-id="8004a-126">Number</span></span> |<span data-ttu-id="8004a-127">Definíció</span><span class="sxs-lookup"><span data-stu-id="8004a-127">Definition</span></span>  |
   |---------|---------|
   |<span data-ttu-id="8004a-128">1</span><span class="sxs-lookup"><span data-stu-id="8004a-128">1</span></span>     |<span data-ttu-id="8004a-129">Entity</span><span class="sxs-lookup"><span data-stu-id="8004a-129">Entity</span></span>          |
   |<span data-ttu-id="8004a-130">2</span><span class="sxs-lookup"><span data-stu-id="8004a-130">2</span></span>     |<span data-ttu-id="8004a-131">Attribútum</span><span class="sxs-lookup"><span data-stu-id="8004a-131">Attribute</span></span>          |
   |<span data-ttu-id="8004a-132">3</span><span class="sxs-lookup"><span data-stu-id="8004a-132">3</span></span>    |<span data-ttu-id="8004a-133">Operátor</span><span class="sxs-lookup"><span data-stu-id="8004a-133">Operator</span></span>         |
   |<span data-ttu-id="8004a-134">4</span><span class="sxs-lookup"><span data-stu-id="8004a-134">4</span></span>    |<span data-ttu-id="8004a-135">Érték</span><span class="sxs-lookup"><span data-stu-id="8004a-135">Value</span></span>         |

8. <span data-ttu-id="8004a-136">Ha az entitás [kapcsolatokon](relationships.md) keresztül kapcsolódik az egyesített ügyfél entitáshoz, meg kell határoznia a kapcsolati útvonalat az érvényes szegmens létrehozásához.</span><span class="sxs-lookup"><span data-stu-id="8004a-136">If the entity is connected to the unified customer entity through [relationships](relationships.md), you need to define the relationship path to create a valid segment.</span></span> <span data-ttu-id="8004a-137">Adjon hozzá entitásokat a kapcsolati útvonalról, amíg ki nem tudja választani az **Ügyfél: CustomerInsights** entitást a legördülő menüből.</span><span class="sxs-lookup"><span data-stu-id="8004a-137">Add the entities from the relationship path until you can select the **Customer:CustomerInsights** entity from the dropdown.</span></span> <span data-ttu-id="8004a-138">Ezután válassza ki az **Összes rekordot** minden egyes feltételnél.</span><span class="sxs-lookup"><span data-stu-id="8004a-138">Then, choose **All records** for each condition.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="8004a-139">![Kapcsolati útvonal a szegmens létrehozása során](media/segments-multiple-relationships.png "Kapcsolati útvonal a szegmens létrehozása során")</span><span class="sxs-lookup"><span data-stu-id="8004a-139">![Relationship path during segment creation](media/segments-multiple-relationships.png "Relationship path during segment creation")</span></span>

1. <span data-ttu-id="8004a-140">A szegmensek alapértelmezés szerint létrehoznak egy kimeneti entitást, amely a definiált szűrőknek megfelelő ügyfélprofilok összes attribútumát tartalmazza.</span><span class="sxs-lookup"><span data-stu-id="8004a-140">By default, segments generate an output entity that contains all attributes of customer profiles which match the defined filters.</span></span> <span data-ttu-id="8004a-141">Ha egy szegmens nem az *Ügyfél* entitáson alapul, akkor ezekből az entitásokból további attribútumokat adhat a kimeneti entitáshoz.</span><span class="sxs-lookup"><span data-stu-id="8004a-141">If a segment is based on other entities than the *Customer* entity, you can add more attributes from these entities to the output entity.</span></span> <span data-ttu-id="8004a-142">A **Projektattribútumok** kiválasztásával kiválaszthatja a kimeneti entitáshoz hozzáfűzni kívánt attribútumokat.</span><span class="sxs-lookup"><span data-stu-id="8004a-142">Select **Project attributes** to choose the attributes that will be appended to the output entity.</span></span>  

   
   <span data-ttu-id="8004a-143">Példa: A szegmens egy olyan entitáson alapul, amely az *Ügyfél* entitáshoz kapcsolódó ügyféltevékenységi adatokat tartalmaz.</span><span class="sxs-lookup"><span data-stu-id="8004a-143">Example: A segment is based on an entity that contains customer activity data which is related to the *Customer* entity.</span></span> <span data-ttu-id="8004a-144">A szegmens az utóbbi 60 napban a súgónak telefonáló összes ügyfelet keresi.</span><span class="sxs-lookup"><span data-stu-id="8004a-144">The segment looks for all customers that called the help desk in the last 60 days.</span></span> <span data-ttu-id="8004a-145">Megadhatja, hogy a hívás időtartamát és a hívások számát hozzáfűzi a kimeneti entitásban található összes egyező ügyfélrekordhoz.</span><span class="sxs-lookup"><span data-stu-id="8004a-145">You can choose to append the call duration and the number of calls to all matching customer records in the output entity.</span></span> <span data-ttu-id="8004a-146">Ez az információ hasznosnak bizonyulhat, ha a gyakran telefonáló ügyfeleknek online súgócikkekre irányuló hasznos hivatkozásokat és a gyakori kérdések hivatkozását szeretné elküldeni.</span><span class="sxs-lookup"><span data-stu-id="8004a-146">This information might be useful to send an email with helpful links to online help articles and FAQs to customers who called frequently.</span></span>

1. <span data-ttu-id="8004a-147">Válassza a **Mentés** lehetőséget a szegmens mentéséhez.</span><span class="sxs-lookup"><span data-stu-id="8004a-147">Select **Save** to save your segment.</span></span> <span data-ttu-id="8004a-148">A rendszer menti a szegmenst és feldolgozza, ha az összes követelményt ellenőrizte.</span><span class="sxs-lookup"><span data-stu-id="8004a-148">Your segment will be saved and processed if all requirements are validated.</span></span> <span data-ttu-id="8004a-149">Ellenkező esetben vázlatként menti a program.</span><span class="sxs-lookup"><span data-stu-id="8004a-149">Otherwise, it will be saved as a draft.</span></span>

1. <span data-ttu-id="8004a-150">A **Szegmensek** oldalra a **Vissza a szegmensekhez** elemre kattintva léphet vissza.</span><span class="sxs-lookup"><span data-stu-id="8004a-150">Select **Back to segments** to go back to the **Segments** page.</span></span>

## <a name="manage-existing-segments"></a><span data-ttu-id="8004a-151">Meglévő szegmensek kezelése</span><span class="sxs-lookup"><span data-stu-id="8004a-151">Manage existing segments</span></span>

<span data-ttu-id="8004a-152">A **szegmensek** lapon megtekintheti az összes mentett szegmenst, és kezelheti azokat.</span><span class="sxs-lookup"><span data-stu-id="8004a-152">On the **Segments** page, you can view all your saved segments and manage them.</span></span>

<span data-ttu-id="8004a-153">Minden szegmenshez egy sor tartozik; ez a sor további információkat tartalmaz a szegmensről.</span><span class="sxs-lookup"><span data-stu-id="8004a-153">Each segment is represented by a row that includes additional information about the segment.</span></span>

<span data-ttu-id="8004a-154">A szegmenseket az oszlop fejlécének kiválasztásával rendezheti egy oszlopba.</span><span class="sxs-lookup"><span data-stu-id="8004a-154">You can sort the segments in a column by selecting the column heading.</span></span>

<span data-ttu-id="8004a-155">A jobb felső sarokban lévő **Keresés** mezővel szűrheti a szegmenseket.</span><span class="sxs-lookup"><span data-stu-id="8004a-155">Use the **Search** box in the top-right corner to filter the segments.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="8004a-156">![Meglévő szegmensek kezelésére szolgáló lehetőségek](media/segments-selected-segment.png "Meglévő szegmensek kezelésére szolgáló lehetőségek")</span><span class="sxs-lookup"><span data-stu-id="8004a-156">![Options to manage an existing segment](media/segments-selected-segment.png "Options to manage an existing segment")</span></span>

<span data-ttu-id="8004a-157">Szegmens kiválasztása esetén a következő művelet használható:</span><span class="sxs-lookup"><span data-stu-id="8004a-157">The following action are available when you select a segment:</span></span>

- <span data-ttu-id="8004a-158">**Megtekintés** a szegmens részleteinek, köztük a tagszám trendjének megtekintése és a szegmens tagjainak előnézete.</span><span class="sxs-lookup"><span data-stu-id="8004a-158">**View** the segment details, including member count trend a preview of segment members.</span></span>
- <span data-ttu-id="8004a-159">**Szerkesztés** a szegmens szerkesztése a tulajdonságainak módosításához.</span><span class="sxs-lookup"><span data-stu-id="8004a-159">**Edit** the segment to change its properties.</span></span>
- <span data-ttu-id="8004a-160">**Duplikált elem létrehozása** a szegmensről.</span><span class="sxs-lookup"><span data-stu-id="8004a-160">**Create duplicate** of a segment.</span></span> <span data-ttu-id="8004a-161">Megadhatja, hogy azonnal módosítja-e a tulajdonságait, vagy egyszerűen csak menti a duplikált példányt.</span><span class="sxs-lookup"><span data-stu-id="8004a-161">You can choose to edit its properties right away or simply save the duplicate.</span></span>
- <span data-ttu-id="8004a-162">**Frissítés** a szegmens frissítése a legfrissebb adatok felvételéhez.</span><span class="sxs-lookup"><span data-stu-id="8004a-162">**Refresh** the segment to include the latest data.</span></span>
- <span data-ttu-id="8004a-163">Szegmens **Aktiválása** vagy **inaktiválása**.</span><span class="sxs-lookup"><span data-stu-id="8004a-163">**Activate** or **Deactivate** the segment.</span></span> <span data-ttu-id="8004a-164">A szegmensek két lehetséges állapottal rendelkeznek – aktívak vagy inaktívak.</span><span class="sxs-lookup"><span data-stu-id="8004a-164">Segments have two possible states - active or inactive.</span></span> <span data-ttu-id="8004a-165">A szegmensek szerkesztésekor hasznosnak bizonyulnak ezek az állapotok.</span><span class="sxs-lookup"><span data-stu-id="8004a-165">These states come in handy when editing a segment.</span></span> <span data-ttu-id="8004a-166">Inaktív szegmensek esetén a szegmens definíciója létezik, de még nem tartalmaz ügyfeleket.</span><span class="sxs-lookup"><span data-stu-id="8004a-166">For inactive segments, the segment definition exists but it doesn't contain any customers yet.</span></span> <span data-ttu-id="8004a-167">A szegmens aktiválásakor az állapota az "inaktív" értékről "aktív" állapotra változik, és a szegmens meghatározásnak megfelelő ügyfeleket keresi meg.</span><span class="sxs-lookup"><span data-stu-id="8004a-167">When you activate a segment, its state changes from 'inactive' to 'active" and it starts looking for customers that match the segment definition.</span></span> <span data-ttu-id="8004a-168">Ha egy [ütemezett frissítés](system.md#schedule-tab) be van állítva, az inaktív szegmensek **állapota** **kihagyva** állapotú , jelezve, hogy a frissítést nem is kísérelte meg.</span><span class="sxs-lookup"><span data-stu-id="8004a-168">If a [scheduled refresh](system.md#schedule-tab) is configured, inactive segments have the **Status** listed as **Skipped**, indicating that a refresh wasn't even attempted.</span></span> <span data-ttu-id="8004a-169">Inaktív szegmens aktiválásakor a rendszer frissíti, és bekerül az ütemezett frissítésekbe.</span><span class="sxs-lookup"><span data-stu-id="8004a-169">When an inactive segment is activated, it will refresh and will be included in scheduled refreshes.</span></span>
  <span data-ttu-id="8004a-170">Másik lehetőségként használhatja **Ütemezés később** funkcióit az **Aktiválás/inaktiválás**, ahol megadhat egy adott szegmens aktiválására és inaktiválására vonatkozó jövőbeli dátumot és időpontot.</span><span class="sxs-lookup"><span data-stu-id="8004a-170">Alternatively, you can use the **Schedule later** functionality in the **Activate/Deactivate** dropdown to specify a future date and time for activation and deactivation of a particular segment.</span></span>
- <span data-ttu-id="8004a-171">Szegmens **átnevezése**.</span><span class="sxs-lookup"><span data-stu-id="8004a-171">**Rename** the segment.</span></span>
- <span data-ttu-id="8004a-172">A tagok listájának **letöltése** .CSV fájlként.</span><span class="sxs-lookup"><span data-stu-id="8004a-172">**Download** the list of members as a .CSV file.</span></span>
- <span data-ttu-id="8004a-173">A **Hozzáadás ehhez:** lehetőség a szegmensben szereplő ügyfelek azonosítóinak listáját egy másik alkalmazásban feldolgozásra küldi.</span><span class="sxs-lookup"><span data-stu-id="8004a-173">**Add to** option sends the list of customer IDs in the segment for processing in another application.</span></span>
- <span data-ttu-id="8004a-174">Szegmens **törlése**.</span><span class="sxs-lookup"><span data-stu-id="8004a-174">**Delete** the segment.</span></span>

## <a name="refresh-segments"></a><span data-ttu-id="8004a-175">Szegmensek frissítése</span><span class="sxs-lookup"><span data-stu-id="8004a-175">Refresh segments</span></span>

<span data-ttu-id="8004a-176">Az összes szegmenst egyszerre frissítheti a **Szegmensek** oldal **Az összes frissítése** elemével. Ha nem szeretné frissíteni az összes szegmenst, jelölje ki a frissítendőket, és válassza a **Frissítés** lehetőséget a beállítások között.</span><span class="sxs-lookup"><span data-stu-id="8004a-176">You can refresh all segments at once by selecting **Refresh all** on the **Segments** page or you can refresh one or multiple segments when you select them and choose **Refresh** in from the options.</span></span> <span data-ttu-id="8004a-177">Másik lehetőségként beállíthat egy ismétlődő frissítést is a **Felügyelet** > **Rendszer** > **Ütemezés** pontban.</span><span class="sxs-lookup"><span data-stu-id="8004a-177">Alternatively, you can configure a recurring refresh on **Admin** > **System** > **Schedule**.</span></span>

> [!TIP]
> <span data-ttu-id="8004a-178">A feladatokhoz/folyamatokhoz [hatféle állapot](system.md#status-types) tartozhat.</span><span class="sxs-lookup"><span data-stu-id="8004a-178">There are [six types of status](system.md#status-types) for tasks/processes.</span></span> <span data-ttu-id="8004a-179">Emellett a legtöbb folyamat [más alsóbb szintű folyamatoktól is függ](system.md#refresh-policies).</span><span class="sxs-lookup"><span data-stu-id="8004a-179">Additionally, most processes [depend on other downstream processes](system.md#refresh-policies).</span></span> <span data-ttu-id="8004a-180">Kiválaszthatja egy folyamat állapotát, és megtekintheti a hozzá tartozó teljes feladat folyamatának részleteit.</span><span class="sxs-lookup"><span data-stu-id="8004a-180">You can select the status of a process to see details on the progress of the entire job.</span></span> <span data-ttu-id="8004a-181">Miután kiválasztotta a **Részletek megtekintése** lehetőséget a feladat egyik feladatához, további információk jelennek meg: feldolgozási idő, legutóbbi feldolgozás dátuma, és a feladathoz társított összes hiba és figyelmeztetés.</span><span class="sxs-lookup"><span data-stu-id="8004a-181">After selecting **See details** for one of the job's tasks, you find additional information: processing time, the last processing date, and all errors and warnings associated with the task.</span></span>

## <a name="download-and-export-segments"></a><span data-ttu-id="8004a-182">Szegmensek letöltése és exportálása</span><span class="sxs-lookup"><span data-stu-id="8004a-182">Download and export segments</span></span>

<span data-ttu-id="8004a-183">A szegmensek egy CSV-fájlba tölthetők le, illetve exportálhatók a Dynamics 365 Sales programba.</span><span class="sxs-lookup"><span data-stu-id="8004a-183">You can download your segments to a CSV file or export them to Dynamics 365 Sales.</span></span>

### <a name="download-segments-to-a-csv-file"></a><span data-ttu-id="8004a-184">Szegmensek letöltése CSV-fájlba</span><span class="sxs-lookup"><span data-stu-id="8004a-184">Download segments to a CSV file</span></span>

1. <span data-ttu-id="8004a-185">A célközönség információkban nyissa meg a **Szegmensek** oldalt.</span><span class="sxs-lookup"><span data-stu-id="8004a-185">In audience insights, go to the **Segments** page.</span></span>

2. <span data-ttu-id="8004a-186">Jelöljön ki egy adott szegmens csempéjében a három pontot.</span><span class="sxs-lookup"><span data-stu-id="8004a-186">Select the ellipsis in a specific segment's tile.</span></span>

3. <span data-ttu-id="8004a-187">A műveletek legördülő listáról válassza a **Letöltés CSV-ként** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="8004a-187">Select **Download as CSV** from the actions drop-down list.</span></span>

### <a name="export-segments-to-dynamics-365-sales"></a><span data-ttu-id="8004a-188">Szegmensek exportálása a Dynamics 365 Sales alkalmazásba</span><span class="sxs-lookup"><span data-stu-id="8004a-188">Export segments to Dynamics 365 Sales</span></span>

<span data-ttu-id="8004a-189">Mielőtt exportálja a szegmenseket a Dynamics 365 Sales programba, egy rendszergazdának [létre kell hoznia az exportálási célhelyet](export-destinations.md) a Dynamics 365 Sales-hez.</span><span class="sxs-lookup"><span data-stu-id="8004a-189">Before exporting segments to Dynamics 365 Sales, an admin needs to [create the export destination](export-destinations.md) for Dynamics 365 Sales.</span></span>

1. <span data-ttu-id="8004a-190">A célközönség információkban nyissa meg a **Szegmensek** oldalt.</span><span class="sxs-lookup"><span data-stu-id="8004a-190">In audience insights, go to the **Segments** page.</span></span>

2. <span data-ttu-id="8004a-191">Jelöljön ki egy adott szegmens csempéjében a három pontot.</span><span class="sxs-lookup"><span data-stu-id="8004a-191">Select the ellipsis in a specific segment's tile.</span></span>

3. <span data-ttu-id="8004a-192">Válassza a **Hozzáadás** lehetőséget a Műveletek legördülő listából, és jelölje ki az exportálni kívánt célhelyet.</span><span class="sxs-lookup"><span data-stu-id="8004a-192">Select **Add to** from the actions drop-down list and select the export destination you want to send the data to.</span></span>

## <a name="draft-mode-for-segments"></a><span data-ttu-id="8004a-193">Vázlat mód szegmensekhez</span><span class="sxs-lookup"><span data-stu-id="8004a-193">Draft mode for segments</span></span>

<span data-ttu-id="8004a-194">Ha a szegmens feldolgozására vonatkozó összes követelmény nem teljesül, vázlatként mentheti a szegmenst, és hozzáférhet a **Szegmensek** oldalról.</span><span class="sxs-lookup"><span data-stu-id="8004a-194">If not all requirements to process a segment are met, you can save the segment as a draft and access it from the **Segments** page.</span></span>

<span data-ttu-id="8004a-195">Inaktív szegmensként menti a program, és mindaddig nem aktiválható, amíg érvényes nem lesz.</span><span class="sxs-lookup"><span data-stu-id="8004a-195">It will be saved as an inactive segment, and can't be activated it until it's valid.</span></span>

## <a name="add-more-conditions-to-a-group"></a><span data-ttu-id="8004a-196">További feltételek hozzáadása csoporthoz</span><span class="sxs-lookup"><span data-stu-id="8004a-196">Add more conditions to a group</span></span>

<span data-ttu-id="8004a-197">Ha további feltételeket szeretne hozzáadni egy csoporthoz, akkor két logikai operátort használhat:</span><span class="sxs-lookup"><span data-stu-id="8004a-197">To add more conditions to a group, you can use two logical operators:</span></span>

- <span data-ttu-id="8004a-198">**ÉS** operátor: mindkét feltételnek a szegmentálási folyamat részeként kell teljesülnie.</span><span class="sxs-lookup"><span data-stu-id="8004a-198">**AND** operator: Both conditions must be met as part of the segmentation process.</span></span> <span data-ttu-id="8004a-199">Ez a beállítás akkor a leghasznosabb, ha különböző entitások között határoz meg feltételeket.</span><span class="sxs-lookup"><span data-stu-id="8004a-199">This option is most useful when you define conditions across different entities.</span></span>

- <span data-ttu-id="8004a-200">**VAGY** operátor: a szegmentálási folyamat részeként az egyik feltételnek meg kell felelnie.</span><span class="sxs-lookup"><span data-stu-id="8004a-200">**OR** operator: Either one of the conditions needs to be met as part of the segmentation process.</span></span> <span data-ttu-id="8004a-201">Ez a beállítás akkor a leghasznosabb, ha különböző feltételeket ad meg ugyanahhoz az entitáshoz.</span><span class="sxs-lookup"><span data-stu-id="8004a-201">This option is most useful when you define multiple conditions for the same entity.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="8004a-202">![VAGY operátor, ahol valamelyik feltételt teljesíteni kell](media/segmentation-either-condition.png "VAGY operátor, ahol valamelyik feltételt teljesíteni kell")</span><span class="sxs-lookup"><span data-stu-id="8004a-202">![OR operator where either condition needs to be met](media/segmentation-either-condition.png "OR operator where either condition needs to be met")</span></span>

<span data-ttu-id="8004a-203">Jelenleg lehetséges egy **VAGY** operátor beágyazása egy **ÉS** operátor alá, de fordítva nem.</span><span class="sxs-lookup"><span data-stu-id="8004a-203">It's currently possible to nest an **OR** operator under an **AND** operator, but not the other way around.</span></span>

## <a name="combine-multiple-groups"></a><span data-ttu-id="8004a-204">Több csoport egyesítése</span><span class="sxs-lookup"><span data-stu-id="8004a-204">Combine multiple groups</span></span>

<span data-ttu-id="8004a-205">Mindegyik csoport adott ügyfelek csoportját hoz létre.</span><span class="sxs-lookup"><span data-stu-id="8004a-205">Each group produces a specific set of customers.</span></span> <span data-ttu-id="8004a-206">A csoportok kombinálásával szerepeltetheti a vállalati esethez szükséges ügyfeleket.</span><span class="sxs-lookup"><span data-stu-id="8004a-206">You can combine these groups to include the customers required for your business case.</span></span>

1. <span data-ttu-id="8004a-207">A célközönség információkban nyissa meg a **Szegmens** oldalt, és válasszon egy szegmenst.</span><span class="sxs-lookup"><span data-stu-id="8004a-207">In audience insights, go to the **Segments** page and select a segment.</span></span>

2. <span data-ttu-id="8004a-208">Válassza a **Csoport hozzáadása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="8004a-208">Select **Add Group**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="8004a-209">![Ügyfélcsoport hozzáadása csoport](media/customer-group-add-group.png "Ügyfélcsoport hozzáadása csoport")</span><span class="sxs-lookup"><span data-stu-id="8004a-209">![Customer group add group](media/customer-group-add-group.png "Customer group add group")</span></span>

3. <span data-ttu-id="8004a-210">Válasszon az alábbi operátorok közül: **Halmaz**, **Metszet** vagy **Kivéve**.</span><span class="sxs-lookup"><span data-stu-id="8004a-210">Select one of the following set operators: **Union**, **Intersect**, or **Except**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="8004a-211">![Ügyfélcsoport hozzáadása egyesülés](media/customer-group-union.png "Ügyfélcsoport hozzáadása egyesülés")</span><span class="sxs-lookup"><span data-stu-id="8004a-211">![Customer group add union](media/customer-group-union.png "Customer group add union")</span></span>

   <span data-ttu-id="8004a-212">Egy beállított operátor kiválasztásával új csoportot adhat meg.</span><span class="sxs-lookup"><span data-stu-id="8004a-212">Select a set operator to define a new group.</span></span> <span data-ttu-id="8004a-213">Különböző csoportok elmentésével határozza meg, hogy melyik adatok megtartandók:</span><span class="sxs-lookup"><span data-stu-id="8004a-213">Save different groups to determine what data gets retained:</span></span>

   - <span data-ttu-id="8004a-214">Az **Egyesülés** egyesíti a két csoportot.</span><span class="sxs-lookup"><span data-stu-id="8004a-214">**Union** unites the two groups.</span></span>

   - <span data-ttu-id="8004a-215">A **Metszet** a két csoport átfedését veszi.</span><span class="sxs-lookup"><span data-stu-id="8004a-215">**Intersect** overlaps the two groups.</span></span> <span data-ttu-id="8004a-216">Csak az az adat *amely közös* kerül megtartásra mindkét egységesített csoportban.</span><span class="sxs-lookup"><span data-stu-id="8004a-216">Only data that *is common* to both groups is retained in the unified group.</span></span>

   - <span data-ttu-id="8004a-217">**Kivéve** kombinálja a két csoportot.</span><span class="sxs-lookup"><span data-stu-id="8004a-217">**Except** combines the two groups.</span></span> <span data-ttu-id="8004a-218">Csak azon adat kerül megtartásra az A csoportban, amely *nem közös* a B csoport adatival.</span><span class="sxs-lookup"><span data-stu-id="8004a-218">Only data in group A that *is not common* to data in group B is retained.</span></span>

## <a name="view-processing-history-and-segment-members"></a><span data-ttu-id="8004a-219">A feldolgozási előzmények és a szegmenstagok megtekintése</span><span class="sxs-lookup"><span data-stu-id="8004a-219">View processing history and segment members</span></span>

<span data-ttu-id="8004a-220">A szegmensre vonatkozó konszolidált adatokat a részleteinek áttekintésével tekintheti meg.</span><span class="sxs-lookup"><span data-stu-id="8004a-220">You can see consolidated data about a segment by reviewing its details.</span></span>

<span data-ttu-id="8004a-221">A **Szegmens** lapon válassza ki az áttekinteni kívánt szegments.</span><span class="sxs-lookup"><span data-stu-id="8004a-221">On the **Segments** page, select the segment you want to review.</span></span>

<span data-ttu-id="8004a-222">Az oldal felső részén egy trendgráf látható, amely a tagok számának változásait ábrázolja.</span><span class="sxs-lookup"><span data-stu-id="8004a-222">The upper part of the page includes a trend graph that visualizes changes in member count.</span></span> <span data-ttu-id="8004a-223">Vigye az egérmutatót az adatpontok fölé, és tekintse meg egy adott napon a tagok számát.</span><span class="sxs-lookup"><span data-stu-id="8004a-223">Hover over data points to see the member count on a specific date.</span></span>

<span data-ttu-id="8004a-224">Frissítheti az ábrázolás időkeretét.</span><span class="sxs-lookup"><span data-stu-id="8004a-224">You can update the time frame of the visualization.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="8004a-225">![Szegmens időtartománya](media/segment-time-range.png "Szegmens időtartománya")</span><span class="sxs-lookup"><span data-stu-id="8004a-225">![Segment time range](media/segment-time-range.png "Segment time range")</span></span>

<span data-ttu-id="8004a-226">Az alsó rész a szegmenstagok listáját tartalmazza.</span><span class="sxs-lookup"><span data-stu-id="8004a-226">The lower part contains a list of the segment members.</span></span>

> [!NOTE]
> <span data-ttu-id="8004a-227">Az adott listában megjelenő mezők a szegmens entitásainak attribútumain alapulnak.</span><span class="sxs-lookup"><span data-stu-id="8004a-227">Fields that appear in this list are based on the attributes of your segment's entities.</span></span>
>
><span data-ttu-id="8004a-228">A lista az egyeztetett szegmestagok előzetes verziója, és a szegmens első 100 rekordját mutatja, így gyorsan kiértékelheti, és szükség esetén felülvizsgálhatja a meghatározásokat.</span><span class="sxs-lookup"><span data-stu-id="8004a-228">The list is a preview of the matching segment members and shows the first 100 records of your segment so that you can quickly evaluate it and review its definitions if needed.</span></span> <span data-ttu-id="8004a-229">Az összes egyező bejegyzés megjelenítéséhez [exportálnia kell a szegmenst](export-destinations.md).</span><span class="sxs-lookup"><span data-stu-id="8004a-229">To see all matching records, you need to [export the segment](export-destinations.md).</span></span>

## <a name="quick-segments"></a><span data-ttu-id="8004a-230">Gyors szegmens</span><span class="sxs-lookup"><span data-stu-id="8004a-230">Quick segments</span></span>

<span data-ttu-id="8004a-231">A szegmensszerkesztőn kívül van még egy módja a szegmensek létrehozásának.</span><span class="sxs-lookup"><span data-stu-id="8004a-231">In addition to the segment builder, there's another path for creating segments.</span></span> <span data-ttu-id="8004a-232">A gyors szegmensek segítségével gyorsan és azonnali betekintő információkkal hozhat létre egyszerű szegmenseket egyetlen operátorral.</span><span class="sxs-lookup"><span data-stu-id="8004a-232">Quick segments let you build simple segments with a single operator quickly and with instant insights.</span></span>

1. <span data-ttu-id="8004a-233">A **szegmensek** lapon válassza az **új** > **Gyorslétrehozási űrlap** elemet.</span><span class="sxs-lookup"><span data-stu-id="8004a-233">On the **Segments** page, select **New** > **Quickly create from**.</span></span>

   - <span data-ttu-id="8004a-234">Válassza a **profilok** lehetőséget, ha az egyesített Ügyfél entitáson alapuló szegmenset szeretne létrehozni.</span><span class="sxs-lookup"><span data-stu-id="8004a-234">Select the **Profiles** option to build a segment that is based on the unified Customer entity.</span></span>
   - <span data-ttu-id="8004a-235">Válassza az **Mérőszámok** lehetőséget, ha a **Mérőszámok** oldalon korábban létrehozott Ügyfélattribútum típusú mérőszámok mindegyikéhez szeretne szegmenst létrehozni.</span><span class="sxs-lookup"><span data-stu-id="8004a-235">Select the **Measures** option to build a segment around each of the Customer Attribute type of measures you have previously created on the **Measures** page.</span></span>
   - <span data-ttu-id="8004a-236">Válassza az **Információ** lehetőséget, ha egy szegmenst szeretne létrehozni az egyik olyan kimeneti entitás köré, amelyet vagy az **Előrejelzések** vagy az **egyéni modellek** használatával hozott létre.</span><span class="sxs-lookup"><span data-stu-id="8004a-236">Select the **Intelligence** option to build a segment around one of the output entities you generated using either the **Predictions** or **Custom Models** capabilities.</span></span>

2. <span data-ttu-id="8004a-237">Az **új gyors szegmens** párbeszédpanelen jelöljön ki egy attribútumot a **Mező** legördülő listában.</span><span class="sxs-lookup"><span data-stu-id="8004a-237">In the **New quick segment** dialog box, select an attribute from the **Field** dropdown.</span></span>

3. <span data-ttu-id="8004a-238">A rendszer néhány további betekintést biztosít, amelyek segítségével jobb szegmenseket hozhat létre az ügyfelek számára.</span><span class="sxs-lookup"><span data-stu-id="8004a-238">The system will provide some additional insights that help you create better segments of your customers.</span></span>
   - <span data-ttu-id="8004a-239">A kategorikus mezők esetén 10 első számú ügyfél számít.</span><span class="sxs-lookup"><span data-stu-id="8004a-239">For categorical fields, we'll show 10 top customer counts.</span></span> <span data-ttu-id="8004a-240">Válasszon egy **Értéket**, és válassza a **Felülvizsgálat** elemet.</span><span class="sxs-lookup"><span data-stu-id="8004a-240">Choose a **Value** and select **Review**.</span></span>

   - <span data-ttu-id="8004a-241">Numerikus attribútumok esetében a rendszer azt mutatja, hogy az egyes ügyfelek percentilis értékei alá milyen attribútumértékek tartoznak.</span><span class="sxs-lookup"><span data-stu-id="8004a-241">For a numerical attribute, the system will show what attribute value falls under each customer's percentile.</span></span> <span data-ttu-id="8004a-242">Válasszon egy **operátort** és egy **értéket**, majd válassza a **Felülvizsgálat** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="8004a-242">Choose an **Operator** and a **Value**, then select **Review**.</span></span>

4. <span data-ttu-id="8004a-243">A rendszer megadja a **Becsült szegmensméret** értékét.</span><span class="sxs-lookup"><span data-stu-id="8004a-243">The system will provide you with an **Estimated segment size**.</span></span> <span data-ttu-id="8004a-244">Kiválaszthatja, hogy létrehozza-e a megadott szegmenst, vagy először újra meg szeretné vizsgálni, hogy egy másik szegmens méretet kap-e.</span><span class="sxs-lookup"><span data-stu-id="8004a-244">You can choose whether to generate the segment you've defined, or first revisit it to get a different segment size.</span></span>

    > [!div class="mx-imgBorder"]
    > <span data-ttu-id="8004a-245">![Gyorsszegmens neve és becslése](media/quick-segment-name.png "Gyorsszegmens neve és becslése")</span><span class="sxs-lookup"><span data-stu-id="8004a-245">![Name and estimation for a quick segment](media/quick-segment-name.png "Name and estimation for a quick segment")</span></span>

5. <span data-ttu-id="8004a-246">Adjon meg egy **Név** értéket a szegmens számára.</span><span class="sxs-lookup"><span data-stu-id="8004a-246">Provide a **Name** for your segment.</span></span> <span data-ttu-id="8004a-247">Másik lehetőségként adjon meg **Megjelenítendő nevet**.</span><span class="sxs-lookup"><span data-stu-id="8004a-247">Optionally, provide a **Display name**.</span></span>

6. <span data-ttu-id="8004a-248">Válassza a **Mentés** lehetőséget a szegmens létrehozásához.</span><span class="sxs-lookup"><span data-stu-id="8004a-248">Select **Save** to create your segment.</span></span>

7. <span data-ttu-id="8004a-249">Miután a szegmens befejezte a feldolgozást, megtekintheti azt a létrehozott többi szegmenshez hasonlóan.</span><span class="sxs-lookup"><span data-stu-id="8004a-249">After the segment has finished processing, you can view it like any other segment you've created.</span></span>

<span data-ttu-id="8004a-250">A következő esetekben javasoljuk, hogy ne a javasolt szegmensek lehetőséget használja, hanem a szegmensépítő használatát:</span><span class="sxs-lookup"><span data-stu-id="8004a-250">For the following scenarios, we advise using the segment builder rather than the recommended segments capability:</span></span>

- <span data-ttu-id="8004a-251">Szegmensek létrehozása szűrőkkel kategorikus mezőkön, ahol az operátor eltér a **Létezik** operátortól</span><span class="sxs-lookup"><span data-stu-id="8004a-251">Creating segments with filters on categorical fields where the operator is different than the **Is** operator</span></span>
- <span data-ttu-id="8004a-252">Szegmensek létrehozása szűrővel azoknál a numerikus mezőknél, ahol az operátor más, mint a **Között**, **Nagyobb, mint** és **Kisebb, mint** operátor</span><span class="sxs-lookup"><span data-stu-id="8004a-252">Creating segments with filters on numerical fields where the operator is different than the **Between**, **Greater than**, and **Less than** operators</span></span>
- <span data-ttu-id="8004a-253">A szegmensek létrehozása szűrőkkel a dátum típusú mezőkön</span><span class="sxs-lookup"><span data-stu-id="8004a-253">Creating segments with filters on date type fields</span></span>

## <a name="next-steps"></a><span data-ttu-id="8004a-254">Következő lépések</span><span class="sxs-lookup"><span data-stu-id="8004a-254">Next steps</span></span>

<span data-ttu-id="8004a-255">[Exportáljon egy szegmenst](export-destinations.md), és fedezze fel az [Ügyfélkártya](customer-card-add-in.md) és [Összekötők](export-power-bi.md) elemeket, az ügyfélszintű információkhoz.</span><span class="sxs-lookup"><span data-stu-id="8004a-255">[Export a segment](export-destinations.md) and explore the [Customer Card](customer-card-add-in.md) and [Connectors](export-power-bi.md) to get insights on the customer level.</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]