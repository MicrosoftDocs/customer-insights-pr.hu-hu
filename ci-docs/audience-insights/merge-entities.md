---
title: Entitások egyesítése az adategyesítésben
description: Entitások egyesítése az egyesített ügyfélprofilok létrehozásához.
ms.date: 04/16/2020
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
ms.reviewer: adkuppa
manager: shellyha
ms.openlocfilehash: 045fd8d8f65161b91caabed2ac52494dc4fb3910
ms.sourcegitcommit: cf9b78559ca189d4c2086a66c879098d56c0377a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/03/2020
ms.locfileid: "4406018"
---
# <a name="merge-entities"></a><span data-ttu-id="65269-103">Entitások összefésülése</span><span class="sxs-lookup"><span data-stu-id="65269-103">Merge entities</span></span>

<span data-ttu-id="65269-104">Az egyesítési fázis az adategységesítési folyamat legutolsó szakasza.</span><span class="sxs-lookup"><span data-stu-id="65269-104">The merge phase is the last phase in the data unification process.</span></span> <span data-ttu-id="65269-105">Célja az ütköző adatok feloldása.</span><span class="sxs-lookup"><span data-stu-id="65269-105">Its purpose is reconciling conflicting data.</span></span> <span data-ttu-id="65269-106">Az adatütközés egyik példája egy ügyfélnév, amely két adathalmazban is megtalálható, de kis eltéréssel („Grant Marshall” és „Grant Marshal”), vagy egy telefonszám, ami csak formátumában tér el (617-803-091X és 617803091X).</span><span class="sxs-lookup"><span data-stu-id="65269-106">Examples of conflicting data could include a customer name found in two of your datasets but that shows up a little differently in each ("Grant Marshall" versus "Grant Marshal"), or a phone number that differs in format (617-803-091X versus 617803091X).</span></span> <span data-ttu-id="65269-107">Az ütköző adatpontok egyesítése attribútumonként történik.</span><span class="sxs-lookup"><span data-stu-id="65269-107">Merging those conflicting data points is done on an attribute-by-attribute basis.</span></span>

<span data-ttu-id="65269-108">Az [egyeztetési fázis](match-entities.md) befejezése után megkezdheti az egyesítési fázist az **Egyesítés** csempe kiválasztásával az **Egységesítés** oldalon.</span><span class="sxs-lookup"><span data-stu-id="65269-108">After completing the [match phase](match-entities.md), you start the merge phase by selecting the **Merge** tile on the **Unify** page.</span></span>

## <a name="review-system-recommendations"></a><span data-ttu-id="65269-109">Rendszer javaslatainak áttekintése</span><span class="sxs-lookup"><span data-stu-id="65269-109">Review system recommendations</span></span>

<span data-ttu-id="65269-110">Az **Egyesítés** oldalon kiválaszthat és kizárhat attribútumokat az egységesített ügyfélprofil entitáson belüli egyesítésből (amely a konfigurációs folyamat eredménye).</span><span class="sxs-lookup"><span data-stu-id="65269-110">On the **Merge** page, you choose and exclude attributes to merge within your unified customer profile entity (the result of the configuration process).</span></span> <span data-ttu-id="65269-111">A rendszer automatikusan egyesít néhány attribútumot.</span><span class="sxs-lookup"><span data-stu-id="65269-111">Some attributes are automatically merged by the system.</span></span>

### <a name="view-merged-attributes"></a><span data-ttu-id="65269-112">Egyesített attribútumok megtekintése</span><span class="sxs-lookup"><span data-stu-id="65269-112">View merged attributes</span></span>

<span data-ttu-id="65269-113">Ha meg szeretné tekinteni az automatikusan egyesített attribútumok egyikében szereplő attribútumokat, jelölje ki az egyesített attribútumot.</span><span class="sxs-lookup"><span data-stu-id="65269-113">To view the attributes that are included in one of your automatically merged attributes, select that merged attribute.</span></span> <span data-ttu-id="65269-114">Az egyesített attribútumot alkotó két attribútum két új sorban fog megjelenni az egyesített attribútum alatt.</span><span class="sxs-lookup"><span data-stu-id="65269-114">The two attributes that compose that merged attribute display in two new rows beneath the merged attribute.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="65269-115">![Egyesített attribútum kiválasztása](media/configure-data-merge-profile-attributes.png "Egyesített attribútum kiválasztása")</span><span class="sxs-lookup"><span data-stu-id="65269-115">![Select merged attribute](media/configure-data-merge-profile-attributes.png "Select merged attribute")</span></span>

### <a name="separate-merged-attributes"></a><span data-ttu-id="65269-116">Egyesített attribútumok szétválasztása</span><span class="sxs-lookup"><span data-stu-id="65269-116">Separate merged attributes</span></span>

<span data-ttu-id="65269-117">Ha az automatikusan egyesített attribútumok bármelyikét szét szeretné választani vagy visszavonni az egyesítést keresse meg az attribútumot a **Profilattribútumok** táblában.</span><span class="sxs-lookup"><span data-stu-id="65269-117">To separate or unmerge any of the automatically merged attributes, find the attribute in the **Profile attributes** table.</span></span>

1. <span data-ttu-id="65269-118">Válassza a három pont (...) választógombot.</span><span class="sxs-lookup"><span data-stu-id="65269-118">Select the ellipsis (...) button.</span></span>
  
2. <span data-ttu-id="65269-119">A legördülő listában válassza a **Mezők szétválasztása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="65269-119">In the dropdown list, select **Separate fields**.</span></span>

### <a name="remove-merged-attributes"></a><span data-ttu-id="65269-120">Egyesített attribútumok eltávolítása</span><span class="sxs-lookup"><span data-stu-id="65269-120">Remove merged attributes</span></span>

<span data-ttu-id="65269-121">Ha egy attribútumot ki szeretne zárni a végső Ügyfélprofil entitásból, keresse meg a **Profilattribútumok** táblában.</span><span class="sxs-lookup"><span data-stu-id="65269-121">To exclude an attribute from the final customer profile entity, find it in the **Profile attributes** table.</span></span>

1. <span data-ttu-id="65269-122">Válassza a három pont (...) választógombot.</span><span class="sxs-lookup"><span data-stu-id="65269-122">Select the ellipsis (...) button.</span></span>
  
2. <span data-ttu-id="65269-123">A legördülő listában válassza a **Nincs egyesítés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="65269-123">In the dropdown list, select **Don't merge**.</span></span>

   <span data-ttu-id="65269-124">Az attribútum átkerül az **Eltávolítva ügyfélrekordból** szakaszba.</span><span class="sxs-lookup"><span data-stu-id="65269-124">The attribute is moved to the **Removed from customer record** section.</span></span>

## <a name="manually-add-a-merged-attribute"></a><span data-ttu-id="65269-125">Egyesített attribútum manuális hozzáadása</span><span class="sxs-lookup"><span data-stu-id="65269-125">Manually add a merged attribute</span></span>

<span data-ttu-id="65269-126">Egyesített attribútum hozzáadásához nyissa meg az **Egyesítés** oldalt.</span><span class="sxs-lookup"><span data-stu-id="65269-126">To add a merged attribute, go to the **Merge** page.</span></span>

1. <span data-ttu-id="65269-127">Válassza az **Egyesített attribútum kiválasztása** elemet.</span><span class="sxs-lookup"><span data-stu-id="65269-127">Select **Add merged attribute**.</span></span>

2. <span data-ttu-id="65269-128">Adjon meg egy **Nevet**, amellyel be tudja később azonosítani az **Egyesítés** oldalon.</span><span class="sxs-lookup"><span data-stu-id="65269-128">Provide a **Name** to identify it on the **Merge** page later.</span></span>

3. <span data-ttu-id="65269-129">Tetszés szerint megadhat egy **Megjelenítendő név** értéket is, amely megjelenik az egységesített Ügyfélprofil entitásban.</span><span class="sxs-lookup"><span data-stu-id="65269-129">Optionally, provide a **Display name** to appear in the unified Customer Profile entity.</span></span>

4. <span data-ttu-id="65269-130">Konfigurálja az **Ismétlődő attribútumok kiválasztása** lehetőséget, hogy kiválassza azokat az attribútumokat, amelyeket egyesíteni szeretne az egyeztetett entitásokból.</span><span class="sxs-lookup"><span data-stu-id="65269-130">Configure **Select duplicate attributes** to select the attributes that you want to merge from the matched entities.</span></span> <span data-ttu-id="65269-131">Az attribútumok keresésére is lehetőség van.</span><span class="sxs-lookup"><span data-stu-id="65269-131">You can also search for attributes.</span></span>

5. <span data-ttu-id="65269-132">Állítsa be a **Rangsor fontosság szerint** elemet, hogy rangsorolja az egyik attribútumot a többi felett.</span><span class="sxs-lookup"><span data-stu-id="65269-132">Set the **Rank by importance** to prioritize one attribute above the others.</span></span> <span data-ttu-id="65269-133">Ha például a *WebAccountCSV* entitás tartalmazza a legpontosabb információkat a *Teljes nevek* attribútumáról, az entitást a *ContactCSV* fölé rangsorolhatja a *WebAccountCSV* kiválasztásával.</span><span class="sxs-lookup"><span data-stu-id="65269-133">For example, if the *WebAccountCSV* entity includes the most accurate data about the *Full Names* attribute, you could prioritize this entity over *ContactCSV* by selecting *WebAccountCSV*.</span></span> <span data-ttu-id="65269-134">Ennek eredményeként a *WebAccountCSV* az első prioritásba kerül, míg a *ContactCSV* második helyre kerül, amikor a *Teljes név* attribútum értékeit kéri le.</span><span class="sxs-lookup"><span data-stu-id="65269-134">As a result, *WebAccountCSV* moves to first priority, while *ContactCSV* moves to second priority when pulling values for the *Full Name* attribute.</span></span>

## <a name="run-your-merge"></a><span data-ttu-id="65269-135">Az egyesítés futtatása</span><span class="sxs-lookup"><span data-stu-id="65269-135">Run your merge</span></span>

<span data-ttu-id="65269-136">Függetlenül attól, hogy kézzel egyesíti-e az attribútumokat, vagy a rendszer egyesíti-e őket, bármikor futtathatja az egyesítést.</span><span class="sxs-lookup"><span data-stu-id="65269-136">Whether you manually merge attributes or let the system merge them, you can always run your merge.</span></span> <span data-ttu-id="65269-137">A folyamat indításához az **Egyeztetés** oldalon válassza a **Futtatás** elemet.</span><span class="sxs-lookup"><span data-stu-id="65269-137">Select **Run** on the **Merge** page to start the process.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="65269-138">![Adatok egyesítése Mentés és Futtatás](media/configure-data-merge-save-run.png "Adatok egyesítése Mentés és Futtatás")</span><span class="sxs-lookup"><span data-stu-id="65269-138">![Data merge Save and Run](media/configure-data-merge-save-run.png "Data merge Save and Run")</span></span>

<span data-ttu-id="65269-139">A további módosítások elvégzéséhez és a lépés újrafuttatásához visszavonhat egy folyamatban lévő egyesítést.</span><span class="sxs-lookup"><span data-stu-id="65269-139">To make additional changes and rerun the step, you can cancel an in-progress merge.</span></span> <span data-ttu-id="65269-140">Válassza ki a **Frissítés folyamatban...** szöveget és válassza a **Feladat megszakítása** lehetőséget a megjelenő oldalpanelen.</span><span class="sxs-lookup"><span data-stu-id="65269-140">Select **Refreshing ...** and select **Cancel job**  in the side pane that appears.</span></span>

<span data-ttu-id="65269-141">Miután a **Frissítés folyamatban...** szöveg **Sikeres** elemre módosul, az egyesítés befejeződött, és megoldotta az adatokban levő ellentmondásokat a meghatározott házirendek alapján.</span><span class="sxs-lookup"><span data-stu-id="65269-141">After the **Refreshing ...** text changes to **Successful**, merge has completed and resolved contradictions in your data according to the policies you defined.</span></span> <span data-ttu-id="65269-142">Az egyesített és a nem egyesített attribútumok szerepelnek az egyesített profil entitásban.</span><span class="sxs-lookup"><span data-stu-id="65269-142">Merged and unmerged attributes are included in the unified profile entity.</span></span> <span data-ttu-id="65269-143">A kizárt attribútumok nem szerepelnek az egyesített profil entitásban.</span><span class="sxs-lookup"><span data-stu-id="65269-143">Excluded attributes aren't included in the unified profile entity.</span></span>

<span data-ttu-id="65269-144">Ha nem először sikerült az egyesítés futtatása, a rendszer automatikusan újrafuttatja az összes későbbi folyamatot, beleértve a bővítést, a szegmentálást és az intézkedéseket.</span><span class="sxs-lookup"><span data-stu-id="65269-144">If it wasn't the first time you ran a merge successfully, all downstream processes, including enrichment, segmentation, and measures will rerun automatically.</span></span> <span data-ttu-id="65269-145">Az összes folyamat újrafuttatását követően az ügyfelek profiljai tükrözik az elvégzett módosításokat.</span><span class="sxs-lookup"><span data-stu-id="65269-145">After all downstream processes have been rerun, the customer profiles reflect any changes you made.</span></span>

> [!TIP]
> <span data-ttu-id="65269-146">A feladatokhoz/folyamatokhoz [hatféle állapot](system.md#status-types) tartozhat.</span><span class="sxs-lookup"><span data-stu-id="65269-146">There are [six types of status](system.md#status-types) for tasks/processes.</span></span> <span data-ttu-id="65269-147">Emellett a legtöbb folyamat [más alsóbb szintű folyamatoktól is függ](system.md#refresh-policies).</span><span class="sxs-lookup"><span data-stu-id="65269-147">Additionally, most processes [depend on other downstream processes](system.md#refresh-policies).</span></span> <span data-ttu-id="65269-148">Kiválaszthatja egy folyamat állapotát, és megtekintheti a hozzá tartozó teljes feladat folyamatának részleteit.</span><span class="sxs-lookup"><span data-stu-id="65269-148">You can select the status of a process to see details on the progress of the entire job.</span></span> <span data-ttu-id="65269-149">Miután kiválasztotta a **Részletek megtekintése** lehetőséget a feladat egyik feladatához, további információk jelennek meg: feldolgozási idő, legutóbbi feldolgozás dátuma, és a feladathoz társított összes hiba és figyelmeztetés.</span><span class="sxs-lookup"><span data-stu-id="65269-149">After selecting **See details** for one of the job's tasks, you find additional information: processing time, the last processing date, and all errors and warnings associated with the task.</span></span>

## <a name="next-step"></a><span data-ttu-id="65269-150">Következő lépés</span><span class="sxs-lookup"><span data-stu-id="65269-150">Next Step</span></span>

<span data-ttu-id="65269-151">Konfigurálja a [tevékenységek](activities.md), [bővítés](enrichment-microsoft-graph.md) vagy [kapcsolatok](relationships.md) elemet, és még több információt kaphat ügyfeleiről.</span><span class="sxs-lookup"><span data-stu-id="65269-151">Configure [activities](activities.md), [enrichment](enrichment-microsoft-graph.md), or [relationships](relationships.md) to gain more insights about your customers.</span></span>

<span data-ttu-id="65269-152">Ha már beállította a tevékenységeket, a dúsítást vagy a kapcsolatok, vagy ha a szegmenseket definiálta, akkor a rendszer automatikusan feldolgozza a legfrissebb ügyféladatokat.</span><span class="sxs-lookup"><span data-stu-id="65269-152">If you already configured activities, enrichment, or relationships, or if you defined segments, they'll be processed automatically to use the latest customer data.</span></span>


