---
title: Mértékek létrehozása és felügyelete
description: Definiálja a vállalkozás teljesítményét elemző és tükröző mértékeket.
ms.date: 02/02/2021
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: wameng
ms.reviewer: mhart
manager: shellyha
ms.openlocfilehash: 202ea22d290be04e54ce9676b6b693162354607f
ms.sourcegitcommit: d3eb07dcc72624a2d5cfc95c7ea9faaa2c1b6001
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/16/2021
ms.locfileid: "5654735"
---
# <a name="define-and-manage-measures"></a><span data-ttu-id="ed54e-103">Az intézkedések definiálása és kezelése</span><span class="sxs-lookup"><span data-stu-id="ed54e-103">Define and manage measures</span></span>

<span data-ttu-id="ed54e-104">A mértékek segítenek abban, hogy jobban megértse az ügyfelek viselkedését és az üzleti teljesítményt a kapcsolódó értékek lekérésével az [egyesített profilokból](data-unification.md).</span><span class="sxs-lookup"><span data-stu-id="ed54e-104">Measures help you to better understand customer behaviors and business performance by retrieving relevant values from [unified profiles](data-unification.md).</span></span> <span data-ttu-id="ed54e-105">Egy vállalat például az *egy ügyfélhez kapcsolódó teljes költést* szeretné látni az egyes ügyfelek vásárlási előzményeinek megismeréséhez.</span><span class="sxs-lookup"><span data-stu-id="ed54e-105">For example, a business wants to see the *total spend per customer* to understand individual customer’s purchase history.</span></span> <span data-ttu-id="ed54e-106">Vagy mérni szeretné a *vállalat teljes értékesítéseit*, hogy megértse a teljes vállalat összesített szintű bevételeit.</span><span class="sxs-lookup"><span data-stu-id="ed54e-106">Or measure *total sales of the company* to understand the aggregate-level revenue in the whole business.</span></span>  

<span data-ttu-id="ed54e-107">Az mértékek létrehozása a mértékkészítővel történik, ami egy adatlekérdezési platform számos operátorral és egyszerű leképezési lehetőségekkel.</span><span class="sxs-lookup"><span data-stu-id="ed54e-107">Measures are created using the measure builder, a data query platform with various operators and simple mapping options.</span></span> <span data-ttu-id="ed54e-108">Lehetőséget ad az adatok szűrésére, az eredmények csoportosítására, az [entitáskapcsolatok elérési útjainak](relationships.md) észlelésére és a kimenet előnézetére.</span><span class="sxs-lookup"><span data-stu-id="ed54e-108">It lets you filter the data, group results, detect [entity relationship paths](relationships.md), and preview the output.</span></span>

<span data-ttu-id="ed54e-109">A mértékszerkesztő segítségével üzleti tevékenységeket tervezhet az ügyféladatok lekérdezésével és a betekintések kinyerésével.</span><span class="sxs-lookup"><span data-stu-id="ed54e-109">Use the measure builder to plan business activities by querying customer data and extract insights.</span></span> <span data-ttu-id="ed54e-110">Ha például egy *ügyfélre jutó teljes költség* és az *egy ügyfélre jutó teljes megtérülés* mértékeket hozza létre, akkor könnyebben azonosítható a nagy költéssel, mégis nagy megtérüléssel jellemezhető ügyfelek csoportja.</span><span class="sxs-lookup"><span data-stu-id="ed54e-110">For example, creating a measure of *total spend per customer* and *total return per customer* helps identify a group of customers with high spend yet high return.</span></span> <span data-ttu-id="ed54e-111">A következő legjobb műveletek előremozdításához [létrehozhat egy szegmenst](segments.md).</span><span class="sxs-lookup"><span data-stu-id="ed54e-111">You can [create a segment](segments.md) to drive next best actions.</span></span> 

## <a name="create-a-measure"></a><span data-ttu-id="ed54e-112">Mérőszám létrehozása</span><span class="sxs-lookup"><span data-stu-id="ed54e-112">Create a measure</span></span>

<span data-ttu-id="ed54e-113">Ez a rész végigvezeti egy új mértéknek a nulláról való létrehozásán.</span><span class="sxs-lookup"><span data-stu-id="ed54e-113">This section walks you through creating a new measure from scratch.</span></span> <span data-ttu-id="ed54e-114">Az Ügyfél entitáshoz kapcsolattal beállított adatentitások adatattribútumainak segítségével mértéket állíthat össze.</span><span class="sxs-lookup"><span data-stu-id="ed54e-114">You can build a measure with data attributes from data entities that have a relationship set up to connect with the Customer entity.</span></span> 

1. <span data-ttu-id="ed54e-115">A célközönség információin belül nyissa meg a következőt: **Mérőszámok**.</span><span class="sxs-lookup"><span data-stu-id="ed54e-115">In audience insights, go to **Measures**.</span></span>

1. <span data-ttu-id="ed54e-116">Válassza az **Új** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="ed54e-116">Select **New**.</span></span>

1. <span data-ttu-id="ed54e-117">Válassza a **Név szerkesztése** lehetőséget, és adjon **Nevet** a mértéknek.</span><span class="sxs-lookup"><span data-stu-id="ed54e-117">Select **Edit name** and provide a **Name** for the measure.</span></span> 
   > [!NOTE]
   > <span data-ttu-id="ed54e-118">Ha az új mértékkonfigurációban csak két mező található , például, CustomerID és egy számítás – a kimenet új oszlopként kerül fel a rendszer által létrehozott Customer_Measure nevű entitáshoz.</span><span class="sxs-lookup"><span data-stu-id="ed54e-118">If your new measure configuration has only two fields, for exmample, CustomerID and one calculation, the output will be added as a new column to the system generated entity called Customer_Measure.</span></span> <span data-ttu-id="ed54e-119">A mérték értéke pedig az egyesített ügyfélprofilban is látható.</span><span class="sxs-lookup"><span data-stu-id="ed54e-119">And you will be able to see the measure’s value in the unified customer profile.</span></span> <span data-ttu-id="ed54e-120">Más mértékek létrehozzák a saját entitásaikat.</span><span class="sxs-lookup"><span data-stu-id="ed54e-120">Other measures will generate their own entities.</span></span>

1. <span data-ttu-id="ed54e-121">Válassza a konfigurációs területen az összesítési függvényt a **Függvény kiválasztása** legördülő menüből.</span><span class="sxs-lookup"><span data-stu-id="ed54e-121">In the configuration area, choose the aggregation function from the **Select Function** drop-down menu.</span></span> <span data-ttu-id="ed54e-122">Az összesítési függvények többek között a következők:</span><span class="sxs-lookup"><span data-stu-id="ed54e-122">Aggregation functions include:</span></span> 
   - <span data-ttu-id="ed54e-123">**Sum**</span><span class="sxs-lookup"><span data-stu-id="ed54e-123">**Sum**</span></span>
   - <span data-ttu-id="ed54e-124">**Átlag**</span><span class="sxs-lookup"><span data-stu-id="ed54e-124">**Average**</span></span>
   - <span data-ttu-id="ed54e-125">**Számlálás**</span><span class="sxs-lookup"><span data-stu-id="ed54e-125">**Count**</span></span>
   - <span data-ttu-id="ed54e-126">**Egyedszámlálás**</span><span class="sxs-lookup"><span data-stu-id="ed54e-126">**Count Unique**</span></span>
   - <span data-ttu-id="ed54e-127">**Max**</span><span class="sxs-lookup"><span data-stu-id="ed54e-127">**Max**</span></span>
   - <span data-ttu-id="ed54e-128">**Min**</span><span class="sxs-lookup"><span data-stu-id="ed54e-128">**Min**</span></span>
   - <span data-ttu-id="ed54e-129">**Első:** az adatrekord első értékét veszi fel</span><span class="sxs-lookup"><span data-stu-id="ed54e-129">**First**: takes the first value of the data record</span></span>
   - <span data-ttu-id="ed54e-130">**Utolsó**: az adatrekordhoz hozzáadott utolsó értéket veszi fel</span><span class="sxs-lookup"><span data-stu-id="ed54e-130">**Last**: takes the last value that was added to the data record</span></span>

   :::image type="content" source="media/measure-operators.png" alt-text="A mértékek számításához használható operátorok.":::

1. <span data-ttu-id="ed54e-132">Válassza az **Attribútum hozzáadása** lehetőséget a mérték létrehozásához szükséges adatok kiválasztásához.</span><span class="sxs-lookup"><span data-stu-id="ed54e-132">Select **Add attribute** to select the data you need to create this measure.</span></span>
   
   1. <span data-ttu-id="ed54e-133">Válassza az **Attribútumok** lapot.</span><span class="sxs-lookup"><span data-stu-id="ed54e-133">Select the **Attributes** tab.</span></span> 
   1. <span data-ttu-id="ed54e-134">Adatentitás: Válassza ki azt az entitást, amely a mérni kívánt attribútumot tartalmazza.</span><span class="sxs-lookup"><span data-stu-id="ed54e-134">Data entity: Choose the entity that includes the attribute you want to measure.</span></span> 
   1. <span data-ttu-id="ed54e-135">Adatattribútum: Válassza ki az összesítési függvényben az mérték kiszámításához használni kívánt attribútumot.</span><span class="sxs-lookup"><span data-stu-id="ed54e-135">Data attribute: Choose the attribute you want to use in the aggregation function to calculate the measure.</span></span> <span data-ttu-id="ed54e-136">Egyszerre csak egy attribútumot választhat ki.</span><span class="sxs-lookup"><span data-stu-id="ed54e-136">You can only select one attribute at a time.</span></span>
   1. <span data-ttu-id="ed54e-137">Meglévő mértékből is kiválaszthat adatattribútumokat a **Mértékek** lapon. Másik lehetőségként megkeresheti egy entitást vagy mérték nevét is.</span><span class="sxs-lookup"><span data-stu-id="ed54e-137">You can also select a data attribute from an existing measure by selecting the **Measures** tab. Or, you can search for an entity or measure name.</span></span> 
   1. <span data-ttu-id="ed54e-138">Válassza a **Hozzáadás** lehetőséget, ha a kijelölt attribútumot hozzá szeretne adni a mértékhez.</span><span class="sxs-lookup"><span data-stu-id="ed54e-138">Select **Add** to add the selected attribute to the measure.</span></span>

   :::image type="content" source="media/measure-attribute-selection.png" alt-text="Válassza ki a számításokban használni kívánt attribútumot.":::

1. <span data-ttu-id="ed54e-140">Összetettebb mértékek építéshez további attribútumokat adhat hozzá, vagy használhat operátorokat a mértékfüggvényben.</span><span class="sxs-lookup"><span data-stu-id="ed54e-140">To build more complex measures, you can add more attributes or use math operators on your measure function.</span></span>

   :::image type="content" source="media/measure-math-operators.png" alt-text="Hozzon létre egy összetett mértéket a matematikai műveletek segítségével.":::

1. <span data-ttu-id="ed54e-142">Szűrők hozzáadásához válassza ki a **Szűrő** lehetőséget a konfigurációs területen.</span><span class="sxs-lookup"><span data-stu-id="ed54e-142">To add filters, select the **Filter** in the configuration area.</span></span> 
  
   1. <span data-ttu-id="ed54e-143">A **Szűrők** panel **Attribútum hozzáadása** szakaszában jelölje ki a szűrők létrehozásához használni kívánt attribútumot.</span><span class="sxs-lookup"><span data-stu-id="ed54e-143">In **Add attribute** section of the **Filters** pane, select the attribute you want to use to create filters.</span></span>
   1. <span data-ttu-id="ed54e-144">Állítsa be a szűrőoperátorokat, hogy minden kijelölt attribútumhoz definiálja a szűrőt.</span><span class="sxs-lookup"><span data-stu-id="ed54e-144">Set the filter operators to define the filter for every selected attribute.</span></span>
   1. <span data-ttu-id="ed54e-145">Válassza az **Alkalmaz** lehetőséget, ha a szűrőket hozzá szeretne adni a mértékhez.</span><span class="sxs-lookup"><span data-stu-id="ed54e-145">Select **Apply** to add the filters to the measure.</span></span>

1. <span data-ttu-id="ed54e-146">Dimenziók hozzáadásához válassza ki a **Dimenzió** lehetőséget a konfigurációs területen.</span><span class="sxs-lookup"><span data-stu-id="ed54e-146">To add dimensions, select **Dimension** in the configuration area.</span></span> <span data-ttu-id="ed54e-147">A dimenziók oszlopként fognak megjelenni a mérték kimeneti entitásában.</span><span class="sxs-lookup"><span data-stu-id="ed54e-147">Dimensions will show as columns in the measure output entity.</span></span>
   1. <span data-ttu-id="ed54e-148">Válassza a **Dimenziók szerkesztése** lehetőséget, ha olyan adatattribútumokat szeretne felvenni, amelyek szerint csoportosítja a mértékeket.</span><span class="sxs-lookup"><span data-stu-id="ed54e-148">Select **Edit dimensions** to add data attributes you want to group the measure values by.</span></span> <span data-ttu-id="ed54e-149">Például város vagy nem.</span><span class="sxs-lookup"><span data-stu-id="ed54e-149">For example, city or gender.</span></span> <span data-ttu-id="ed54e-150">Az *ügyfélszintű mértékek* létrehozásához alapértelmezés szerint a *CustomerID* dimenzió van kiválasztva.</span><span class="sxs-lookup"><span data-stu-id="ed54e-150">By default, the *CustomerID* dimension is selected to create *customer-level measures*.</span></span> <span data-ttu-id="ed54e-151">Ha *üzleti szintű mértékeket* szeretne létrehozni, eltávolíthatja az alapértelmezett dimenziót.</span><span class="sxs-lookup"><span data-stu-id="ed54e-151">You can remove the default dimension if you want to create *business-level measures*.</span></span>
   1. <span data-ttu-id="ed54e-152">Válassza a **Kész** lehetőséget, ha a dimenziókat hozzá szeretne adni a mértékhez.</span><span class="sxs-lookup"><span data-stu-id="ed54e-152">Select **Done** to add the dimensions to the measure.</span></span>

1. <span data-ttu-id="ed54e-153">Ha a leképezett adatentitás és az *Ügyfél* entitás között több elérési út is van, válasszon egyet az azonosított [entitáskapcsolat-útvonalak közül](relationships.md).</span><span class="sxs-lookup"><span data-stu-id="ed54e-153">If there are multiple paths between the data entity you mapped and the *Customer* entity, you have to choose one of the identified [entity relationship paths](relationships.md).</span></span> <span data-ttu-id="ed54e-154">A mértékek eredményei a kiválasztott elérési úttól függően változhatnak.</span><span class="sxs-lookup"><span data-stu-id="ed54e-154">Measure results can vary depending on the selected path.</span></span> 
   1. <span data-ttu-id="ed54e-155">Válassza ki az **Adatbeállítások** lehetőséget, és válassza ki az entitás elérési útját, amely a mérték azonosítására fog használni.</span><span class="sxs-lookup"><span data-stu-id="ed54e-155">Select **Data preferences** and choose the entity path that should be used to identify your measure.</span></span> <span data-ttu-id="ed54e-156">Ha az *Ügyfél* entitásnak csak egyetlen elérési útja van, akkor a vezérlő nem fog mutatni.</span><span class="sxs-lookup"><span data-stu-id="ed54e-156">If there's only a single path to the *Customer* entity, this control won't show.</span></span>
   1. <span data-ttu-id="ed54e-157">Válassza a **Kész** lehetőséget a kiválasztás alkalmazáshoz.</span><span class="sxs-lookup"><span data-stu-id="ed54e-157">Select **Done** to apply your selection.</span></span> 

   :::image type="content" source="media/measures-data-preferences.png" alt-text="Válassza ki a mértékhez tartozó entitás elérési utat.":::

1. <span data-ttu-id="ed54e-159">Ha további számításokat szeretne hozzáadni az mértékhez, válassza az **Új számítás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="ed54e-159">To add more calculations for the measure, select **New calculation**.</span></span> <span data-ttu-id="ed54e-160">Az új számításokhoz csak ugyanazon az entitás elérési úton használhatók entitások.</span><span class="sxs-lookup"><span data-stu-id="ed54e-160">You can only use entities on the same entity path for new calculations.</span></span> <span data-ttu-id="ed54e-161">A további számítások új oszlopként fognak megjelenni a mérték kimeneti entitásában.</span><span class="sxs-lookup"><span data-stu-id="ed54e-161">More calculations will show as new columns in the measure output entity.</span></span>

1. <span data-ttu-id="ed54e-162">Válassza a **...** lehetőséget a mértékből szármató számítás **Duplikálásához**, **Átnevezéséhez** vagy **Eltávolításához**.</span><span class="sxs-lookup"><span data-stu-id="ed54e-162">Select **...** on the calculation to **Duplicate**, **Rename**, or **Remove** a calculation from a measure.</span></span>

1. <span data-ttu-id="ed54e-163">Az **Előnézet** területen a mérték kimeneti entitásának adatsémáját látja a szűrőkkel és a dimenziókkal.</span><span class="sxs-lookup"><span data-stu-id="ed54e-163">In the **Preview** area, you'll see the data schema of the measure output entity, including filters and dimensions.</span></span> <span data-ttu-id="ed54e-164">Az előnézet dinamikusan reagál a konfiguráció változásaira.</span><span class="sxs-lookup"><span data-stu-id="ed54e-164">The preview reacts dynamically to changes in the configuration.</span></span>

1. <span data-ttu-id="ed54e-165">Válassza a **Futtatás** lehetőséget a konfigurált mértékhez tartozó eredmények kiszámításához.</span><span class="sxs-lookup"><span data-stu-id="ed54e-165">Select **Run** to calculate results for the configured measure.</span></span> <span data-ttu-id="ed54e-166">Válassza a **Mentés és bezárás** lehetőséget, ha meg szeretné tartani az aktuális konfigurációt, és a mértéket később szeretné futtatni.</span><span class="sxs-lookup"><span data-stu-id="ed54e-166">Select **Save and close** if you want to keep the current configuration and run the measure later.</span></span>

1. <span data-ttu-id="ed54e-167">A listában az újonnan létrehozott mértékegységet a **Mértékek** listában jelenítheti meg.</span><span class="sxs-lookup"><span data-stu-id="ed54e-167">Go to **Measures** to see the newly created measure in the list.</span></span>

## <a name="manage-your-measures"></a><span data-ttu-id="ed54e-168">Intézkedések kezelése</span><span class="sxs-lookup"><span data-stu-id="ed54e-168">Manage your measures</span></span>

<span data-ttu-id="ed54e-169">[Egy mérték létrehozása](#create-a-measure) után megtekintheti a mértékek listáját a **Mértékek** oldalon.</span><span class="sxs-lookup"><span data-stu-id="ed54e-169">After [creating a measure](#create-a-measure), you see a list of measures on the **Measures** page.</span></span>

<span data-ttu-id="ed54e-170">Információkat talál a mérték típusáról, az létrehozóról, a létrehozás dátumáról, a státuszáról és az állapotáról.</span><span class="sxs-lookup"><span data-stu-id="ed54e-170">You'll find information about the measure type, the creator, creation date, status, and state.</span></span> <span data-ttu-id="ed54e-171">Ha kiválaszt egy mértéket a listából, akkor megtekintheti a kimenetet, és letölthet egy .CSV-fájl.</span><span class="sxs-lookup"><span data-stu-id="ed54e-171">When you select a measure from the list, you can preview the output and download a .CSV file.</span></span>

<span data-ttu-id="ed54e-172">Ha egyszerre szeretné frissíteni az összes intézkedést, akkor jelölje be az **összes frissítése** lehetőséget egy adott intézkedés kiválasztása nélkül.</span><span class="sxs-lookup"><span data-stu-id="ed54e-172">To refresh all of your measures at the same time, select **Refresh all** without selecting a specific measure.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="ed54e-173">![Az egyes intézkedések kezelésére szolgáló műveletek](media/measure-actions.png "Az egyes intézkedések kezelésére szolgáló műveletek")</span><span class="sxs-lookup"><span data-stu-id="ed54e-173">![Actions to manage single measures](media/measure-actions.png "Actions to manage single measures")</span></span>

<span data-ttu-id="ed54e-174">Válasszon ki egy mértéket a listából a következő lehetőségekhez:</span><span class="sxs-lookup"><span data-stu-id="ed54e-174">Select a measure from the list for the following options:</span></span>

- <span data-ttu-id="ed54e-175">Adja meg a mérőszám nevét a részletek megtekintéséhez.</span><span class="sxs-lookup"><span data-stu-id="ed54e-175">Select the measure name to see its details.</span></span>
- <span data-ttu-id="ed54e-176">**Szerkessze** a mérőszám konfigurációját.</span><span class="sxs-lookup"><span data-stu-id="ed54e-176">**Edit** the configuration of the measure.</span></span>
- <span data-ttu-id="ed54e-177">**Frissítse** a mértéket a legújabb adatok alapján.</span><span class="sxs-lookup"><span data-stu-id="ed54e-177">**Refresh** the measure based on the latest data.</span></span>
- <span data-ttu-id="ed54e-178">**Nevezze át** az intézkedést.</span><span class="sxs-lookup"><span data-stu-id="ed54e-178">**Rename** the measure.</span></span>
- <span data-ttu-id="ed54e-179">**Törölje** az intézkedést.</span><span class="sxs-lookup"><span data-stu-id="ed54e-179">**Delete** the measure.</span></span>
- <span data-ttu-id="ed54e-180">**Aktiválás** vagy **Inaktiválás**.</span><span class="sxs-lookup"><span data-stu-id="ed54e-180">**Activate** or **Deactivate**.</span></span> <span data-ttu-id="ed54e-181">Az inaktív mértékek nem frissülnek az [ütemezett frissítés](system.md#schedule-tab) során.</span><span class="sxs-lookup"><span data-stu-id="ed54e-181">Inactive measures won't get refreshed during a [scheduled refresh](system.md#schedule-tab).</span></span>

> [!TIP]
> <span data-ttu-id="ed54e-182">A feladatokhoz/folyamatokhoz [hatféle állapot](system.md#status-types) tartozhat.</span><span class="sxs-lookup"><span data-stu-id="ed54e-182">There are [six types of status](system.md#status-types) for tasks/processes.</span></span> <span data-ttu-id="ed54e-183">Emellett a legtöbb folyamat [más alsóbb szintű folyamatoktól is függ](system.md#refresh-policies).</span><span class="sxs-lookup"><span data-stu-id="ed54e-183">Additionally, most processes [depend on other downstream processes](system.md#refresh-policies).</span></span> <span data-ttu-id="ed54e-184">Kiválaszthatja egy folyamat állapotát, és megtekintheti a hozzá tartozó teljes feladat folyamatának részleteit.</span><span class="sxs-lookup"><span data-stu-id="ed54e-184">You can select the status of a process to see details on the progress of the entire job.</span></span> <span data-ttu-id="ed54e-185">Miután kiválasztotta a **Részletek megtekintése** lehetőséget a feladat egyik feladatához, további információk jelennek meg: feldolgozási idő, legutóbbi feldolgozás dátuma, és a feladathoz társított összes hiba és figyelmeztetés.</span><span class="sxs-lookup"><span data-stu-id="ed54e-185">After selecting **See details** for one of the job's tasks, you find additional information: processing time, the last processing date, and all errors and warnings associated with the task.</span></span>

## <a name="next-step"></a><span data-ttu-id="ed54e-186">Következő lépés</span><span class="sxs-lookup"><span data-stu-id="ed54e-186">Next step</span></span>

<span data-ttu-id="ed54e-187">Az [ügyfélszegmens](segments.md) létrehozásához meglévő mértéket használhat.</span><span class="sxs-lookup"><span data-stu-id="ed54e-187">You cam use existing measures to create [a customer segment](segments.md).</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]