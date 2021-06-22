---
title: Célközönség betekintési információinak szegmensei
description: A szegmensek áttekintése, valamint információk a létrehozásukról és kezelésükről.
ms.date: 05/03/2021
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: JimsonChalissery
ms.author: jimsonc
ms.reviewer: mhart
manager: shellyha
ms.openlocfilehash: 6cb7bd62bf0f61e6dc5811b20e5011e4a086c743
ms.sourcegitcommit: 84283d523a891298fca8aaf629d9f9ab2a1bc067
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/27/2021
ms.locfileid: "6111390"
---
# <a name="segments-overview"></a><span data-ttu-id="00600-103">Szegmensek áttekintése</span><span class="sxs-lookup"><span data-stu-id="00600-103">Segments overview</span></span>

<span data-ttu-id="00600-104">A szegmensek segítségével csoportosíthatja ügyfeleit demográfiai-, tranzakciós- vagy viselkedési tulajdonságok alapján.</span><span class="sxs-lookup"><span data-stu-id="00600-104">Segments let you group your customers based on demographic, transactional, or behavioral attributes.</span></span> <span data-ttu-id="00600-105">A szegmensekkel népszerűsítheti az üzleti célok eléréséhez használható promóciós kampányokat, értékesítési tevékenységeket és ügyfélszolgálati tevékenységeket.</span><span class="sxs-lookup"><span data-stu-id="00600-105">You can use segments to target promotional campaigns, sales activities, and customer support actions to achieve your business goals.</span></span>

<span data-ttu-id="00600-106">A szegmensdefiníciók szűrőivel egyező ügyfélprofilokat a szegmensek *tagjainak* nevezik.</span><span class="sxs-lookup"><span data-stu-id="00600-106">Customer profiles that match the filters of a segment definition are referred as *members* of a segment.</span></span> <span data-ttu-id="00600-107">Bizonyos [szolgáltatási korlátozások](service-limits.md) érvényesek.</span><span class="sxs-lookup"><span data-stu-id="00600-107">Some [service limits](service-limits.md) apply.</span></span>

## <a name="create-a-new-segment"></a><span data-ttu-id="00600-108">Új szegmens létrehozása</span><span class="sxs-lookup"><span data-stu-id="00600-108">Create a new segment</span></span>

<span data-ttu-id="00600-109">Új szegmens többféleképpen is létrehozható:</span><span class="sxs-lookup"><span data-stu-id="00600-109">There are multiple ways to create a new segment:</span></span> 

- <span data-ttu-id="00600-110">Összetett szegmens a szegmensszerkesztővel: [Üres szegmens](segment-builder.md#create-a-new-segment)</span><span class="sxs-lookup"><span data-stu-id="00600-110">Complex segment with segment builder: [Blank segment](segment-builder.md#create-a-new-segment)</span></span>
- <span data-ttu-id="00600-111">Egyszerű szegmensek egyetlen operátorral: [Gyorsszegmens](segment-builder.md#quick-segments)</span><span class="sxs-lookup"><span data-stu-id="00600-111">Simple segments with one operator: [Quick segment](segment-builder.md#quick-segments)</span></span>
- <span data-ttu-id="00600-112">Hasonló ügyfelek keresése AI-alapú megoldással: [Hasonló ügyfelek](find-similar-customer-segments.md)</span><span class="sxs-lookup"><span data-stu-id="00600-112">AI-powered way to find similar customers: [Similar Customers](find-similar-customer-segments.md)</span></span>
- <span data-ttu-id="00600-113">AI-alapú, mértékeken vagy attribútumokon alapuló javaslatok: [Javasolt szegmensek a mértékek javításához](suggested-segments.md)</span><span class="sxs-lookup"><span data-stu-id="00600-113">AI-powered suggestions based on measures or attributes: [Suggested segments to improve measures](suggested-segments.md)</span></span>
- <span data-ttu-id="00600-114">Javaslatok tevékenységek alapján: [Ügyféltevékenységen alapuló javasolt szegmensek](suggested-segments-activity.md)</span><span class="sxs-lookup"><span data-stu-id="00600-114">Suggestions based on activities: [Suggested segments based on customer activity](suggested-segments-activity.md)</span></span>

## <a name="manage-existing-segments"></a><span data-ttu-id="00600-115">Meglévő szegmensek kezelése</span><span class="sxs-lookup"><span data-stu-id="00600-115">Manage existing segments</span></span>

<span data-ttu-id="00600-116">A mentett szegmensek a **Szegmensek** oldalon tekinthetők és kezelhetők.</span><span class="sxs-lookup"><span data-stu-id="00600-116">Go to the **Segments** page, to view all your saved segments and manage them.</span></span>

<span data-ttu-id="00600-117">Minden szegmenshez egy sor tartozik; ez a sor további információkat tartalmaz a szegmensről.</span><span class="sxs-lookup"><span data-stu-id="00600-117">Each segment is represented by a row that includes additional information about the segment.</span></span>

:::image type="content" source="media/segments-selected-segment.png" alt-text="Kijelölt szegmens a lehetőségek legördülő listájával és a rendelkezésre álló lehetőségekkel.":::

<span data-ttu-id="00600-119">Szegmens kiválasztása esetén a következő művelet használható:</span><span class="sxs-lookup"><span data-stu-id="00600-119">The following action are available when you select a segment:</span></span>

- <span data-ttu-id="00600-120">**Megtekintés** a szegmens részleteinek, köztük a tagszám trendjének megtekintése és a szegmens tagjainak előnézete.</span><span class="sxs-lookup"><span data-stu-id="00600-120">**View** the segment details, including member count trend a preview of segment members.</span></span>
- <span data-ttu-id="00600-121">**Szerkesztés** a szegmens szerkesztése a tulajdonságainak módosításához.</span><span class="sxs-lookup"><span data-stu-id="00600-121">**Edit** the segment to change its properties.</span></span>
- <span data-ttu-id="00600-122">**Duplikált elem létrehozása** a szegmensről.</span><span class="sxs-lookup"><span data-stu-id="00600-122">**Create duplicate** of a segment.</span></span> <span data-ttu-id="00600-123">Megadhatja, hogy azonnal módosítja-e a tulajdonságait, vagy egyszerűen csak menti a duplikált példányt.</span><span class="sxs-lookup"><span data-stu-id="00600-123">You can choose to edit its properties right away or simply save the duplicate.</span></span>
- <span data-ttu-id="00600-124">**Frissítés** a szegmens frissítése a legfrissebb adatok felvételéhez.</span><span class="sxs-lookup"><span data-stu-id="00600-124">**Refresh** the segment to include the latest data.</span></span>
- <span data-ttu-id="00600-125">Szegmens **Aktiválása** vagy **inaktiválása**.</span><span class="sxs-lookup"><span data-stu-id="00600-125">**Activate** or **Deactivate** the segment.</span></span> <span data-ttu-id="00600-126">A szegmensek két lehetséges állapottal rendelkeznek – aktívak vagy inaktívak.</span><span class="sxs-lookup"><span data-stu-id="00600-126">Segments have two possible states - active or inactive.</span></span> <span data-ttu-id="00600-127">A szegmensek szerkesztésekor hasznosnak bizonyulnak ezek az állapotok.</span><span class="sxs-lookup"><span data-stu-id="00600-127">These states come in handy when editing a segment.</span></span> <span data-ttu-id="00600-128">Inaktív szegmensek esetén a szegmens definíciója létezik, de még nem tartalmaz ügyfeleket.</span><span class="sxs-lookup"><span data-stu-id="00600-128">For inactive segments, the segment definition exists but it doesn't contain any customers yet.</span></span> <span data-ttu-id="00600-129">A szegmens aktiválásakor az állapota az "inaktív" értékről "aktív" állapotra változik, és a szegmens meghatározásnak megfelelő ügyfeleket keresi meg.</span><span class="sxs-lookup"><span data-stu-id="00600-129">When you activate a segment, its state changes from 'inactive' to 'active" and it starts looking for customers that match the segment definition.</span></span> <span data-ttu-id="00600-130">Ha egy [ütemezett frissítés](system.md#schedule-tab) be van állítva, az inaktív szegmensek **állapota** **kihagyva** állapotú , jelezve, hogy a frissítést nem is kísérelte meg.</span><span class="sxs-lookup"><span data-stu-id="00600-130">If a [scheduled refresh](system.md#schedule-tab) is configured, inactive segments have the **Status** listed as **Skipped**, indicating that a refresh wasn't even attempted.</span></span> <span data-ttu-id="00600-131">Inaktív szegmens aktiválásakor a rendszer frissíti, és bekerül az ütemezett frissítésekbe.</span><span class="sxs-lookup"><span data-stu-id="00600-131">When an inactive segment is activated, it will refresh and will be included in scheduled refreshes.</span></span>
  <span data-ttu-id="00600-132">Másik lehetőségként használhatja **Ütemezés később** funkcióit az **Aktiválás/inaktiválás**, ahol megadhat egy adott szegmens aktiválására és inaktiválására vonatkozó jövőbeli dátumot és időpontot.</span><span class="sxs-lookup"><span data-stu-id="00600-132">Alternatively, you can use the **Schedule later** functionality in the **Activate/Deactivate** dropdown to specify a future date and time for activation and deactivation of a particular segment.</span></span>
- <span data-ttu-id="00600-133">Szegmens **átnevezése**.</span><span class="sxs-lookup"><span data-stu-id="00600-133">**Rename** the segment.</span></span>
- <span data-ttu-id="00600-134">A tagok listájának **letöltése** .CSV fájlként.</span><span class="sxs-lookup"><span data-stu-id="00600-134">**Download** the list of members as a .CSV file.</span></span>
- <span data-ttu-id="00600-135">Az **Exportálások kezelése** az exporttal kapcsolatos szegmensek megtekintéséhez és kezeléséhez.</span><span class="sxs-lookup"><span data-stu-id="00600-135">**Manage exports** to see exports related segment and manage them.</span></span> [<span data-ttu-id="00600-136">További információ az exportálásokról.</span><span class="sxs-lookup"><span data-stu-id="00600-136">Learn more about exports.</span></span>](export-destinations.md)
- <span data-ttu-id="00600-137">Szegmens **törlése**.</span><span class="sxs-lookup"><span data-stu-id="00600-137">**Delete** the segment.</span></span>

## <a name="refresh-segments"></a><span data-ttu-id="00600-138">Szegmensek frissítése</span><span class="sxs-lookup"><span data-stu-id="00600-138">Refresh segments</span></span>

<span data-ttu-id="00600-139">Az összes szegmenst egyszerre frissítheti a **Szegmensek** oldal **Az összes frissítése** elemével. Ha nem szeretné frissíteni az összes szegmenst, jelölje ki a frissítendőket, és válassza a **Frissítés** lehetőséget a beállítások között.</span><span class="sxs-lookup"><span data-stu-id="00600-139">You can refresh all segments at once by selecting **Refresh all** on the **Segments** page or you can refresh one or multiple segments when you select them and choose **Refresh** in from the options.</span></span> <span data-ttu-id="00600-140">Másik lehetőségként beállíthat egy ismétlődő frissítést is a **Felügyelet** > **Rendszer** > **Ütemezés** pontban.</span><span class="sxs-lookup"><span data-stu-id="00600-140">Alternatively, you can configure a recurring refresh on **Admin** > **System** > **Schedule**.</span></span>

> [!TIP]
> <span data-ttu-id="00600-141">A feladatokhoz/folyamatokhoz [hatféle állapot](system.md#status-types) tartozhat.</span><span class="sxs-lookup"><span data-stu-id="00600-141">There are [six types of status](system.md#status-types) for tasks/processes.</span></span> <span data-ttu-id="00600-142">Emellett a legtöbb folyamat [más alsóbb szintű folyamatoktól is függ](system.md#refresh-policies).</span><span class="sxs-lookup"><span data-stu-id="00600-142">Additionally, most processes [depend on other downstream processes](system.md#refresh-policies).</span></span> <span data-ttu-id="00600-143">Kiválaszthatja egy folyamat állapotát, és megtekintheti a hozzá tartozó teljes feladat folyamatának részleteit.</span><span class="sxs-lookup"><span data-stu-id="00600-143">You can select the status of a process to see details on the progress of the entire job.</span></span> <span data-ttu-id="00600-144">Miután kiválasztotta a **Részletek megtekintése** lehetőséget a feladat egyik feladatához, további információk jelennek meg: feldolgozási idő, legutóbbi feldolgozás dátuma, és a feladathoz társított összes hiba és figyelmeztetés.</span><span class="sxs-lookup"><span data-stu-id="00600-144">After selecting **See details** for one of the job's tasks, you find additional information: processing time, the last processing date, and all errors and warnings associated with the task.</span></span>

## <a name="export-segments"></a><span data-ttu-id="00600-145">Szegmensek exportálása</span><span class="sxs-lookup"><span data-stu-id="00600-145">Export segments</span></span>

<span data-ttu-id="00600-146">Exportálhat egy szegmenst a szegmensek oldaláról vagy az [exportálások oldalról](export-destinations.md).</span><span class="sxs-lookup"><span data-stu-id="00600-146">You can export a segment from the segments page or the [exports page](export-destinations.md).</span></span> 

1. <span data-ttu-id="00600-147">Lépjen a **Szegmensek** oldalra.</span><span class="sxs-lookup"><span data-stu-id="00600-147">Go to the **Segments** page.</span></span>

1. <span data-ttu-id="00600-148">Válassza ki a **Továbbiak megjelenítése [...]** lehetőséget exportálni kívánt szegmenshez.</span><span class="sxs-lookup"><span data-stu-id="00600-148">Select **Show more [...]** for the segment you want to export.</span></span>

1. <span data-ttu-id="00600-149">Válassza az **Exportálások kezelése** lehetőséget a műveletek legördülő listából.</span><span class="sxs-lookup"><span data-stu-id="00600-149">Select **Manage exports** from the actions drop-down list.</span></span>

1. <span data-ttu-id="00600-150">Megnyílik az **Exportálás (előzetes verzió) szegmenshez** oldal.</span><span class="sxs-lookup"><span data-stu-id="00600-150">The page **Exports (preview) for segment** opens.</span></span> <span data-ttu-id="00600-151">Láthatja az összes konfigurált exportálást export szerint csoportosítva, amely tartalmazza az aktuális szegmenst, vagy nem tartalmazza azt.</span><span class="sxs-lookup"><span data-stu-id="00600-151">You can see all configured exports grouped by by exports that contain the current segment or don't contain it.</span></span>

   1. <span data-ttu-id="00600-152">Ha a kijelölt szegmenst egy exportáláshoz szeretné hozzáadni, jelölje ki a listában az exportálást, és válassza a **Szegmens hozzáadása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="00600-152">To add the selected segment to an export, select the export in the list and select **Add segment**.</span></span>

   1. <span data-ttu-id="00600-153">Ha új exportálást szeretne létrehozni a kijelölt szegmenssel, válassza az **Exportálás hozzáadása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="00600-153">To create a new export with the selected segment, select **Add export**.</span></span> <span data-ttu-id="00600-154">Az exporálások létrehozásával kapcsolatos további információkért lásd: [Új exportálás beállítása](export-destinations.md#set-up-a-new-export).</span><span class="sxs-lookup"><span data-stu-id="00600-154">For more information about creating exports, see [Set up a new export](export-destinations.md#set-up-a-new-export).</span></span>

1. <span data-ttu-id="00600-155">Válassza a **Vissza** lehetőséget, hogy visszatérjen a szegmensek főoldalára.</span><span class="sxs-lookup"><span data-stu-id="00600-155">Select **Back** to return to the main page for segments.</span></span>

## <a name="view-processing-history-and-segment-members"></a><span data-ttu-id="00600-156">A feldolgozási előzmények és a szegmenstagok megtekintése</span><span class="sxs-lookup"><span data-stu-id="00600-156">View processing history and segment members</span></span>

<span data-ttu-id="00600-157">A szegmensre vonatkozó konszolidált adatokat a részleteinek áttekintésével tekintheti meg.</span><span class="sxs-lookup"><span data-stu-id="00600-157">You can see consolidated data about a segment by reviewing its details.</span></span>

<span data-ttu-id="00600-158">A **Szegmens** lapon válassza ki az áttekinteni kívánt szegments.</span><span class="sxs-lookup"><span data-stu-id="00600-158">On the **Segments** page, select the segment you want to review.</span></span>

<span data-ttu-id="00600-159">Az oldal felső részén egy trendgráf látható, amely a tagok számának változásait ábrázolja.</span><span class="sxs-lookup"><span data-stu-id="00600-159">The upper part of the page includes a trend graph that visualizes changes in member count.</span></span> <span data-ttu-id="00600-160">Vigye az egérmutatót az adatpontok fölé, és tekintse meg egy adott napon a tagok számát.</span><span class="sxs-lookup"><span data-stu-id="00600-160">Hover over data points to see the member count on a specific date.</span></span>

<span data-ttu-id="00600-161">Frissítheti az ábrázolás időkeretét.</span><span class="sxs-lookup"><span data-stu-id="00600-161">You can update the time frame of the visualization.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="00600-162">![Szegmens időtartománya](media/segment-time-range.png "Szegmens időtartománya")</span><span class="sxs-lookup"><span data-stu-id="00600-162">![Segment time range](media/segment-time-range.png "Segment time range")</span></span>

<span data-ttu-id="00600-163">Az alsó rész a szegmenstagok listáját tartalmazza.</span><span class="sxs-lookup"><span data-stu-id="00600-163">The lower part contains a list of the segment members.</span></span>

> [!NOTE]
> <span data-ttu-id="00600-164">Az adott listában megjelenő mezők a szegmens entitásainak attribútumain alapulnak.</span><span class="sxs-lookup"><span data-stu-id="00600-164">Fields that appear in this list are based on the attributes of your segment's entities.</span></span>
>
><span data-ttu-id="00600-165">A lista az egyeztetett szegmestagok előzetes verziója, és a szegmens első 100 rekordját mutatja, így gyorsan kiértékelheti, és szükség esetén felülvizsgálhatja a meghatározásokat.</span><span class="sxs-lookup"><span data-stu-id="00600-165">The list is a preview of the matching segment members and shows the first 100 records of your segment so that you can quickly evaluate it and review its definitions if needed.</span></span> <span data-ttu-id="00600-166">Az összes egyező bejegyzés megjelenítéséhez [exportálnia kell a szegmenst](export-destinations.md).</span><span class="sxs-lookup"><span data-stu-id="00600-166">To see all matching records, you need to [export the segment](export-destinations.md).</span></span>

[!INCLUDE[footer-include](../includes/footer-banner.md)] 
