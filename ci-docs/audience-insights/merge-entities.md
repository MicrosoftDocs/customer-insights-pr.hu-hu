---
title: Entitások egyesítése az adategyesítésben
description: Entitások egyesítése az egyesített ügyfélprofilok létrehozásához.
ms.date: 05/10/2021
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: tutorial
author: adkuppa
ms.author: adkuppa
ms.reviewer: mhart
manager: shellyha
ms.openlocfilehash: 2cab702509596dd87c0c9b9769d1af8ba8387f9d
ms.sourcegitcommit: fcc94f55dc2dce84eae188d582801dc47696c9cc
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/20/2021
ms.locfileid: "6085579"
---
# <a name="merge-entities"></a><span data-ttu-id="a36a4-103">Entitások összefésülése</span><span class="sxs-lookup"><span data-stu-id="a36a4-103">Merge entities</span></span>

<span data-ttu-id="a36a4-104">Az egyesítési fázis az adategységesítési folyamat legutolsó szakasza.</span><span class="sxs-lookup"><span data-stu-id="a36a4-104">The merge phase is the last phase in the data unification process.</span></span> <span data-ttu-id="a36a4-105">Célja az ütköző adatok feloldása.</span><span class="sxs-lookup"><span data-stu-id="a36a4-105">Its purpose is reconciling conflicting data.</span></span> <span data-ttu-id="a36a4-106">Az adatütközés egyik példája egy ügyfélnév, amely két adathalmazban is megtalálható, de kis eltéréssel („Grant Marshall” és „Grant Marshal”), vagy egy telefonszám, ami csak formátumában tér el (617-803-091X és 617803091X).</span><span class="sxs-lookup"><span data-stu-id="a36a4-106">Examples of conflicting data could include a customer name found in two of your datasets but that shows up a little differently in each ("Grant Marshall" versus "Grant Marshal"), or a phone number that differs in format (617-803-091X versus 617803091X).</span></span> <span data-ttu-id="a36a4-107">Az ütköző adatpontok egyesítése attribútumonként történik.</span><span class="sxs-lookup"><span data-stu-id="a36a4-107">Merging those conflicting data points is done on an attribute-by-attribute basis.</span></span>

:::image type="content" source="media/merge-fields-page.png" alt-text="Oldalak egyesítése az adategyesítési folyamatban; az egységes ügyfélprofilt meghatározó egyesített mezőket tartalmazó táblázat látható.":::

<span data-ttu-id="a36a4-109">Az [egyeztetési fázis](match-entities.md) befejezése után megkezdheti az egyesítési fázist az **Egyesítés** csempe kiválasztásával az **Egységesítés** oldalon.</span><span class="sxs-lookup"><span data-stu-id="a36a4-109">After completing the [match phase](match-entities.md), you start the merge phase by selecting the **Merge** tile on the **Unify** page.</span></span>

## <a name="review-system-recommendations"></a><span data-ttu-id="a36a4-110">Rendszer javaslatainak áttekintése</span><span class="sxs-lookup"><span data-stu-id="a36a4-110">Review system recommendations</span></span>

<span data-ttu-id="a36a4-111">Az **Adatok** > **Egységesítés** > **Egyesítés** részen válassza ki és zárja ki az egységes ügyfélprofilon belül egyesítendő attribútumokat.</span><span class="sxs-lookup"><span data-stu-id="a36a4-111">On **Data** > **Unify** > **Merge**, you choose and exclude attributes to merge within your unified customer profile entity.</span></span> <span data-ttu-id="a36a4-112">Az egységes ügyfélprofil az adategyesítési folyamat eredménye.</span><span class="sxs-lookup"><span data-stu-id="a36a4-112">The unified customer profile is the result of the data unification process.</span></span> <span data-ttu-id="a36a4-113">A rendszer automatikusan egyesít néhány attribútumot.</span><span class="sxs-lookup"><span data-stu-id="a36a4-113">Some attributes are automatically merged by the system.</span></span>

<span data-ttu-id="a36a4-114">Ha meg szeretné tekinteni az egyik automatikusan egyesített attribútumban szereplő attribútumokat, jelölje ki az egyesített attribútumot a tábla **Ügyfélmezők** lapján.</span><span class="sxs-lookup"><span data-stu-id="a36a4-114">To view the attributes that are included in one of your automatically merged attributes, select that merged attribute in the **Customer fields** tab of the table.</span></span> <span data-ttu-id="a36a4-115">Az egyesített attribútumot alkotó attribútumok két új sorban fognak megjelenni az egyesített attribútum alatt.</span><span class="sxs-lookup"><span data-stu-id="a36a4-115">The attributes that compose that merged attribute display in two new rows beneath the merged attribute.</span></span>

## <a name="separate-rename-exclude-and-edit-merged-fields"></a><span data-ttu-id="a36a4-116">Egyesített mezők szétválasztása, átnevezése, kizárása és szerkesztése</span><span class="sxs-lookup"><span data-stu-id="a36a4-116">Separate, rename, exclude, and edit merged fields</span></span>

<span data-ttu-id="a36a4-117">Módosíthatja, hogy a rendszer hogyan dolgozza fel az egyesített attribútumokat az egységes ügyfélprofil létrehozásához.</span><span class="sxs-lookup"><span data-stu-id="a36a4-117">You can change how the system processes merged attributes to generate the unified customer profile.</span></span> <span data-ttu-id="a36a4-118">Válassza a **Továbbiak** lehetőséget, és válassza ki a módosítandó elemet.</span><span class="sxs-lookup"><span data-stu-id="a36a4-118">Select **Show more** and choose what you want to change.</span></span>

:::image type="content" source="media/manage-merged-attributes.png" alt-text="A Továbbiak legördülő menüben lévő, az egyesített attribútumok kezeléséhez rendelkezésre álló beállítások.":::

<span data-ttu-id="a36a4-120">További információkat a következő szakaszokban talál.</span><span class="sxs-lookup"><span data-stu-id="a36a4-120">For more information, see the following sections.</span></span>

## <a name="separate-merged-fields"></a><span data-ttu-id="a36a4-121">Egyesített mezők szétválasztása</span><span class="sxs-lookup"><span data-stu-id="a36a4-121">Separate merged fields</span></span>

<span data-ttu-id="a36a4-122">Az egyesített mezők szétválasztásához keresse meg az attribútumot a táblázatban.</span><span class="sxs-lookup"><span data-stu-id="a36a4-122">To separate merged fields, find the attribute in the table.</span></span> <span data-ttu-id="a36a4-123">A szétválasztott mezők egyéni adatpontokként jelennek meg az egységes ügyfélprofilban.</span><span class="sxs-lookup"><span data-stu-id="a36a4-123">Separated fields show as individual data points on the unified customer profile.</span></span> 

1. <span data-ttu-id="a36a4-124">Válassza ki az egyesített mezőt.</span><span class="sxs-lookup"><span data-stu-id="a36a4-124">Select the merged field.</span></span>
  
1. <span data-ttu-id="a36a4-125">Válassza a **Továbbiak**, majd a **Mezők szétválasztása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="a36a4-125">Select **Show more** and choose **Separate fields**.</span></span>
 
1. <span data-ttu-id="a36a4-126">Erősítse meg a szétválasztást.</span><span class="sxs-lookup"><span data-stu-id="a36a4-126">Confirm the separation.</span></span>

1. <span data-ttu-id="a36a4-127">A módosítások feldolgozásához válassza a **Mentés** és a **Futtatás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="a36a4-127">Select **Save** and **Run** to process the changes.</span></span>

## <a name="rename-merged-fields"></a><span data-ttu-id="a36a4-128">Egyesített mezők átnevezése</span><span class="sxs-lookup"><span data-stu-id="a36a4-128">Rename merged fields</span></span>

<span data-ttu-id="a36a4-129">Módosítsa az egyesített attribútumok megjelenítendő nevét.</span><span class="sxs-lookup"><span data-stu-id="a36a4-129">Change the display name of merged attributes.</span></span> <span data-ttu-id="a36a4-130">A kimeneti entitás neve nem módosítható.</span><span class="sxs-lookup"><span data-stu-id="a36a4-130">You can't change the name of the output entity.</span></span>

1. <span data-ttu-id="a36a4-131">Válassza ki az egyesített mezőt.</span><span class="sxs-lookup"><span data-stu-id="a36a4-131">Select the merged field.</span></span>
  
1. <span data-ttu-id="a36a4-132">Válassza a **Továbbiak**, majd az **Átnevezés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="a36a4-132">Select **Show more** and choose **Rename**.</span></span>

1. <span data-ttu-id="a36a4-133">Erősítse meg a módosított megjelenítendő nevet.</span><span class="sxs-lookup"><span data-stu-id="a36a4-133">Confirm the changed display name.</span></span> 

1. <span data-ttu-id="a36a4-134">A módosítások feldolgozásához válassza a **Mentés** és a **Futtatás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="a36a4-134">Select **Save** and **Run** to process the changes.</span></span>

## <a name="exclude-merged-fields"></a><span data-ttu-id="a36a4-135">Egyesített mezők kizárása</span><span class="sxs-lookup"><span data-stu-id="a36a4-135">Exclude merged fields</span></span>

<span data-ttu-id="a36a4-136">Zárjon ki egy attribútumot az egységes ügyfélprofilból.</span><span class="sxs-lookup"><span data-stu-id="a36a4-136">Exclude an attribute from the unified customer profile.</span></span> <span data-ttu-id="a36a4-137">Ha a mező más folyamatokban – például szegmensekben – használatos, akkor az ügyfélprofilból való kizárás előtt távolítsa el ezekből a folyamatokból.</span><span class="sxs-lookup"><span data-stu-id="a36a4-137">If the field is used in other processes, for example in a segment, remove it from these processes before excluding it from the customer profile.</span></span> 

1. <span data-ttu-id="a36a4-138">Válassza ki az egyesített mezőt.</span><span class="sxs-lookup"><span data-stu-id="a36a4-138">Select the merged field.</span></span>
  
1. <span data-ttu-id="a36a4-139">Válassza a **Továbbiak**, majd a **Kizárás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="a36a4-139">Select **Show more** and choose **Exclude**.</span></span>

1. <span data-ttu-id="a36a4-140">Erősítse meg a kizárást.</span><span class="sxs-lookup"><span data-stu-id="a36a4-140">Confirm the exclusion.</span></span>

1. <span data-ttu-id="a36a4-141">A módosítások feldolgozásához válassza a **Mentés** és a **Futtatás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="a36a4-141">Select **Save** and **Run** to process the changes.</span></span> 

<span data-ttu-id="a36a4-142">Az összes kizárt mező megtekintéséhez az **EgyesítésMerge** oldalon válassza a **Kizárt mezők** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="a36a4-142">On the **Merge** page, select **Excluded fields** to see the list of all excluded fields.</span></span> <span data-ttu-id="a36a4-143">Ezen az ablaktáblán újra felveheti a kizárt mezőket.</span><span class="sxs-lookup"><span data-stu-id="a36a4-143">This pane lets you add excluded fields back.</span></span>

## <a name="manually-combine-fields"></a><span data-ttu-id="a36a4-144">Mezők manuális kombinálása</span><span class="sxs-lookup"><span data-stu-id="a36a4-144">Manually combine fields</span></span>

<span data-ttu-id="a36a4-145">Manuálisan adjon meg egy egyesített attribútumot.</span><span class="sxs-lookup"><span data-stu-id="a36a4-145">Specify a merged attribute manually.</span></span> 

1. <span data-ttu-id="a36a4-146">Az **Egyesítés** oldalon válassza a **Mezők kombinálása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="a36a4-146">On the **Merge** page, select **Combine fields**.</span></span>

1. <span data-ttu-id="a36a4-147">Adja meg a **Nevet** és egy **Kimeneti mező nevét**.</span><span class="sxs-lookup"><span data-stu-id="a36a4-147">Provide a **Name** and an **Output field name**.</span></span>

1. <span data-ttu-id="a36a4-148">Válasszon ki egy hozzáadni kívánt mezőt.</span><span class="sxs-lookup"><span data-stu-id="a36a4-148">Choose a field to add.</span></span> <span data-ttu-id="a36a4-149">További mezők kombinálásához válassza ki a **Mezők hozzáadása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="a36a4-149">Select **Add fields** to combine more fields.</span></span>

1. <span data-ttu-id="a36a4-150">Erősítse meg a kizárást.</span><span class="sxs-lookup"><span data-stu-id="a36a4-150">Confirm the exclusion.</span></span>

1. <span data-ttu-id="a36a4-151">A módosítások feldolgozásához válassza a **Mentés** és a **Futtatás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="a36a4-151">Select **Save** and **Run** to process the changes.</span></span> 

## <a name="change-the-order-of-fields"></a><span data-ttu-id="a36a4-152">Mezők sorrendjének módosítása</span><span class="sxs-lookup"><span data-stu-id="a36a4-152">Change the order of fields</span></span>

<span data-ttu-id="a36a4-153">Egyes entitások több adatot tartalmaznak, mint mások.</span><span class="sxs-lookup"><span data-stu-id="a36a4-153">Some entities contain more details than others.</span></span> <span data-ttu-id="a36a4-154">Ha egy entitás egy mezőre vonatkozóan a legfrissebb adatokat tartalmazza, az értékek egyesítésekor prioritást adhat neki a többi entitáshoz képest.</span><span class="sxs-lookup"><span data-stu-id="a36a4-154">If an entity includes the latest data about a field, you can prioritize it over other entities when merging values.</span></span>

1. <span data-ttu-id="a36a4-155">Válassza ki az egyesített mezőt.</span><span class="sxs-lookup"><span data-stu-id="a36a4-155">Select the merged field.</span></span>
  
1. <span data-ttu-id="a36a4-156">Válassza a **Továbbiak**, majd a **Szerkesztés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="a36a4-156">Select **Show more** and choose **Edit**.</span></span>

1. <span data-ttu-id="a36a4-157">A **Mezők kombinálása** panelen válassza a **Mozgatás le/fel** lehetőséget a sorrend megadásához, vagy húzza a kívánt helyre az elemeket.</span><span class="sxs-lookup"><span data-stu-id="a36a4-157">In the **Combine fields** pane, select **Move up/down** to set the order or drag and drop them in the desired position.</span></span>

1. <span data-ttu-id="a36a4-158">Erősítse meg a módosítást.</span><span class="sxs-lookup"><span data-stu-id="a36a4-158">Confirm the change.</span></span>

1. <span data-ttu-id="a36a4-159">A módosítások feldolgozásához válassza a **Mentés** és a **Futtatás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="a36a4-159">Select **Save** and **Run** to process the changes.</span></span>

## <a name="run-your-merge"></a><span data-ttu-id="a36a4-160">Az egyesítés futtatása</span><span class="sxs-lookup"><span data-stu-id="a36a4-160">Run your merge</span></span>

<span data-ttu-id="a36a4-161">Függetlenül attól, hogy kézzel egyesíti-e az attribútumokat, vagy a rendszer egyesíti-e őket, bármikor futtathatja az egyesítést.</span><span class="sxs-lookup"><span data-stu-id="a36a4-161">Whether you manually merge attributes or let the system merge them, you can always run your merge.</span></span> <span data-ttu-id="a36a4-162">A folyamat indításához az **Egyeztetés** oldalon válassza a **Futtatás** elemet.</span><span class="sxs-lookup"><span data-stu-id="a36a4-162">Select **Run** on the **Merge** page to start the process.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="a36a4-163">![Adatok egyesítése Mentés és Futtatás](media/configure-data-merge-save-run.png "Adatok egyesítése Mentés és Futtatás")</span><span class="sxs-lookup"><span data-stu-id="a36a4-163">![Data merge Save and Run](media/configure-data-merge-save-run.png "Data merge Save and Run")</span></span>

<span data-ttu-id="a36a4-164">Ha csak az egységesített ügyfélentitásban szereplő kimenetet szeretné látni, válassza a **Csak az Egyesítés futtatása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="a36a4-164">Choose **Run only Merge** if you only want to see the output reflected in the unified customer entity.</span></span> <span data-ttu-id="a36a4-165">A lefelé irányuló folyamatok [a frissítési ütemezésében meghatározottak szerint](system.md#schedule-tab) frissülnek.</span><span class="sxs-lookup"><span data-stu-id="a36a4-165">Downstream processes will be refreshed as [defined in the refresh schedule](system.md#schedule-tab).</span></span>

<span data-ttu-id="a36a4-166">Ha a saját módosításaival szeretné frissíteni a rendszert, válassza az **Egyesítési és lefelé irányuló folyamatok futtatása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="a36a4-166">Choose **Run Merge and downstream processes** to refresh the system with your changes.</span></span> <span data-ttu-id="a36a4-167">Minden folyamat (beleértve a bővítést, a szegmenseket és a mértékeket is) újrafut.</span><span class="sxs-lookup"><span data-stu-id="a36a4-167">All processes, including enrichment, segments, and measures will rerun automatically.</span></span> <span data-ttu-id="a36a4-168">Miután az összes lefelé irányuló folyamat befejeződött, az ügyfélprofilokban megjelennek a végrehajtott módosítások.</span><span class="sxs-lookup"><span data-stu-id="a36a4-168">After all downstream processes have completed, the customer profiles reflect any changes you made.</span></span>

<span data-ttu-id="a36a4-169">Ha további módosításokat szeretne végrehajtani, majd újrafuttatná a lépést, megszakíthatja a folyamatban lévő egyesítést.</span><span class="sxs-lookup"><span data-stu-id="a36a4-169">To make more changes and rerun the step, you can cancel an in-progress merge.</span></span> <span data-ttu-id="a36a4-170">Válassza ki a **Frissítés folyamatban...** szöveget és válassza a **Feladat megszakítása** lehetőséget a megjelenő oldalpanelen.</span><span class="sxs-lookup"><span data-stu-id="a36a4-170">Select **Refreshing ...** and select **Cancel job**  in the side pane that appears.</span></span>

> [!TIP]
> <span data-ttu-id="a36a4-171">A feladatokhoz/folyamatokhoz [hatféle állapot](system.md#status-types) tartozhat.</span><span class="sxs-lookup"><span data-stu-id="a36a4-171">There are [six types of status](system.md#status-types) for tasks/processes.</span></span> <span data-ttu-id="a36a4-172">Emellett a legtöbb folyamat [más alsóbb szintű folyamatoktól is függ](system.md#refresh-policies).</span><span class="sxs-lookup"><span data-stu-id="a36a4-172">Additionally, most processes [depend on other downstream processes](system.md#refresh-policies).</span></span> <span data-ttu-id="a36a4-173">Kiválaszthatja egy folyamat állapotát, és megtekintheti a hozzá tartozó teljes feladat folyamatának részleteit.</span><span class="sxs-lookup"><span data-stu-id="a36a4-173">You can select the status of a process to see details on the progress of the entire job.</span></span> <span data-ttu-id="a36a4-174">Miután kiválasztotta a **Részletek megtekintése** lehetőséget a feladat egyik feladatához, további információk jelennek meg: feldolgozási idő, legutóbbi feldolgozás dátuma, és a feladathoz társított összes hiba és figyelmeztetés.</span><span class="sxs-lookup"><span data-stu-id="a36a4-174">After selecting **See details** for one of the job's tasks, you find additional information: processing time, the last processing date, and all errors and warnings associated with the task.</span></span>

## <a name="next-step"></a><span data-ttu-id="a36a4-175">Következő lépés</span><span class="sxs-lookup"><span data-stu-id="a36a4-175">Next Step</span></span>

<span data-ttu-id="a36a4-176">Konfigurálja a [tevékenységek](activities.md), [bővítés](enrichment-hub.md) vagy [kapcsolatok](relationships.md) elemet, és még több információt kaphat ügyfeleiről.</span><span class="sxs-lookup"><span data-stu-id="a36a4-176">Configure [activities](activities.md), [enrichment](enrichment-hub.md), or [relationships](relationships.md) to gain more insights about your customers.</span></span>

<span data-ttu-id="a36a4-177">Ha már konfigurált tevékenységeket, bővítést vagy szegmenseket, akkor a rendszer automatikusan feldolgozza őket, hogy a legújabb ügyféladatokat lehessen használni.</span><span class="sxs-lookup"><span data-stu-id="a36a4-177">If you already configured activities, enrichment, or segments, they'll be processed automatically to use the latest customer data.</span></span>

[!INCLUDE[footer-include](../includes/footer-banner.md)]
