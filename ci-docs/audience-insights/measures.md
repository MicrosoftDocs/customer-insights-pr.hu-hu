---
title: Mértékek létrehozása és felügyelete
description: Definiálja a vállalkozás teljesítményét elemző és tükröző mértékeket.
ms.date: 04/12/2021
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: wameng
ms.reviewer: mhart
manager: shellyha
ms.openlocfilehash: 402e5ef3515bce0e6f56788781b7bd909738aaa6
ms.sourcegitcommit: b833e333745d321edeaf96d3ed14458cbce02ff1
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/17/2021
ms.locfileid: "6049253"
---
# <a name="define-and-manage-measures"></a><span data-ttu-id="de6a0-103">Az intézkedések definiálása és kezelése</span><span class="sxs-lookup"><span data-stu-id="de6a0-103">Define and manage measures</span></span>

<span data-ttu-id="de6a0-104">A mértékek segítségével az ügyfelek viselkedése és üzleti teljesítménye jobban érthető.</span><span class="sxs-lookup"><span data-stu-id="de6a0-104">Measures help you to better understand customer behaviors and business performance.</span></span> <span data-ttu-id="de6a0-105">Az [egyesített profilokból](data-unification.md) származó releváns értékeket veszik alapul.</span><span class="sxs-lookup"><span data-stu-id="de6a0-105">They look at relevant values from [unified profiles](data-unification.md).</span></span> <span data-ttu-id="de6a0-106">Egy vállalat például az *ügyfélenkénti teljes kiadást* szeretné látni, hogy megértsék az egyes ügyfelek vásárlási előzményeit, vagy lemérjék a *vállalat teljes értékesítéseit*, hogy megértsék a teljes vállalat összesítési szintű bevételét.</span><span class="sxs-lookup"><span data-stu-id="de6a0-106">For example, a business wants to see the *total spend per customer* to understand individual customer’s purchase history or measure *total sales of the company* to understand the aggregate-level revenue in the whole business.</span></span>  

<span data-ttu-id="de6a0-107">Az mértékek létrehozása a mértékkészítővel történik, ami egy adatlekérdezési platform számos operátorral és egyszerű leképezési lehetőségekkel.</span><span class="sxs-lookup"><span data-stu-id="de6a0-107">Measures are created using the measure builder, a data query platform with various operators and simple mapping options.</span></span> <span data-ttu-id="de6a0-108">Lehetőséget ad az adatok szűrésére, az eredmények csoportosítására, az [entitáskapcsolatok elérési útjainak](relationships.md) észlelésére és a kimenet előnézetére.</span><span class="sxs-lookup"><span data-stu-id="de6a0-108">It lets you filter the data, group results, detect [entity relationship paths](relationships.md), and preview the output.</span></span>

<span data-ttu-id="de6a0-109">A mértékszerkesztő segítségével üzleti tevékenységeket tervezhet az ügyféladatok lekérdezésével és a betekintések kinyerésével.</span><span class="sxs-lookup"><span data-stu-id="de6a0-109">Use the measure builder to plan business activities by querying customer data and extract insights.</span></span> <span data-ttu-id="de6a0-110">Ha például egy *ügyfélre jutó teljes költség* és az *egy ügyfélre jutó teljes megtérülés* mértékeket hozza létre, akkor könnyebben azonosítható a nagy költéssel, mégis nagy megtérüléssel jellemezhető ügyfelek csoportja.</span><span class="sxs-lookup"><span data-stu-id="de6a0-110">For example, creating a measure of *total spend per customer* and *total return per customer* helps identify a group of customers with high spend yet high return.</span></span> <span data-ttu-id="de6a0-111">A következő legjobb műveletek előremozdításához [létrehozhat egy szegmenst](segments.md).</span><span class="sxs-lookup"><span data-stu-id="de6a0-111">You can [create a segment](segments.md) to drive next best actions.</span></span> 

## <a name="build-your-own-measure-from-scratch"></a><span data-ttu-id="de6a0-112">Saját mérték létrehozása az alapoktól</span><span class="sxs-lookup"><span data-stu-id="de6a0-112">Build your own measure from scratch</span></span>

<span data-ttu-id="de6a0-113">Ez a rész végigvezeti egy új mértéknek a nulláról való létrehozásán.</span><span class="sxs-lookup"><span data-stu-id="de6a0-113">This section walks you through creating a new measure from scratch.</span></span> <span data-ttu-id="de6a0-114">Az Ügyfél entitáshoz kapcsolattal beállított adatentitások adatattribútumainak segítségével mértéket állíthat össze.</span><span class="sxs-lookup"><span data-stu-id="de6a0-114">You can build a measure with data attributes from data entities that have a relationship set up to connect with the Customer entity.</span></span> 

1. <span data-ttu-id="de6a0-115">A célközönség információin belül nyissa meg a következőt: **Mérőszámok**.</span><span class="sxs-lookup"><span data-stu-id="de6a0-115">In audience insights, go to **Measures**.</span></span>

1. <span data-ttu-id="de6a0-116">Válassza az **Új** lehetőséget, és válassza a **Saját elkészítése** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="de6a0-116">Select **New** and choose **Build your own**.</span></span>

1. <span data-ttu-id="de6a0-117">Válassza a **Név szerkesztése** lehetőséget, és adjon **Nevet** a mértéknek.</span><span class="sxs-lookup"><span data-stu-id="de6a0-117">Select **Edit name** and provide a **Name** for the measure.</span></span> 
   > [!NOTE]
   > <span data-ttu-id="de6a0-118">Ha az új mértékkonfigurációban csak két mező található (például az ügyfél-azonosító és egy számítás), akkor a kimenet új oszlopként keröl a rendszer által létrehozott, Customer_Measure nevű entitásba.</span><span class="sxs-lookup"><span data-stu-id="de6a0-118">If your new measure configuration has only two fields, for example, CustomerID and one calculation, the output will be added as a new column to the system generated entity called Customer_Measure.</span></span> <span data-ttu-id="de6a0-119">A mérték értéke pedig az egyesített ügyfélprofilban is látható.</span><span class="sxs-lookup"><span data-stu-id="de6a0-119">And you will be able to see the measure’s value in the unified customer profile.</span></span> <span data-ttu-id="de6a0-120">Más mértékek létrehozzák a saját entitásaikat.</span><span class="sxs-lookup"><span data-stu-id="de6a0-120">Other measures will generate their own entities.</span></span>

1. <span data-ttu-id="de6a0-121">Válassza a konfigurációs területen az összesítési függvényt a **Függvény kiválasztása** legördülő menüből.</span><span class="sxs-lookup"><span data-stu-id="de6a0-121">In the configuration area, choose the aggregation function from the **Select Function** drop-down menu.</span></span> <span data-ttu-id="de6a0-122">Az összesítési függvények többek között a következők:</span><span class="sxs-lookup"><span data-stu-id="de6a0-122">Aggregation functions include:</span></span> 
   - <span data-ttu-id="de6a0-123">**Sum**</span><span class="sxs-lookup"><span data-stu-id="de6a0-123">**Sum**</span></span>
   - <span data-ttu-id="de6a0-124">**Átlag**</span><span class="sxs-lookup"><span data-stu-id="de6a0-124">**Average**</span></span>
   - <span data-ttu-id="de6a0-125">**Számlálás**</span><span class="sxs-lookup"><span data-stu-id="de6a0-125">**Count**</span></span>
   - <span data-ttu-id="de6a0-126">**Egyedszámlálás**</span><span class="sxs-lookup"><span data-stu-id="de6a0-126">**Count Unique**</span></span>
   - <span data-ttu-id="de6a0-127">**Max**</span><span class="sxs-lookup"><span data-stu-id="de6a0-127">**Max**</span></span>
   - <span data-ttu-id="de6a0-128">**Min**</span><span class="sxs-lookup"><span data-stu-id="de6a0-128">**Min**</span></span>
   - <span data-ttu-id="de6a0-129">**Első:** az adatrekord első értékét veszi fel</span><span class="sxs-lookup"><span data-stu-id="de6a0-129">**First**: takes the first value of the data record</span></span>
   - <span data-ttu-id="de6a0-130">**Utolsó**: az adatrekordhoz hozzáadott utolsó értéket veszi fel</span><span class="sxs-lookup"><span data-stu-id="de6a0-130">**Last**: takes the last value that was added to the data record</span></span>

   :::image type="content" source="media/measure-operators.png" alt-text="A mértékek számításához használható operátorok.":::

1. <span data-ttu-id="de6a0-132">Válassza az **Attribútum hozzáadása** lehetőséget a mérték létrehozásához szükséges adatok kiválasztásához.</span><span class="sxs-lookup"><span data-stu-id="de6a0-132">Select **Add attribute** to select the data you need to create this measure.</span></span>
   
   1. <span data-ttu-id="de6a0-133">Válassza az **Attribútumok** lapot.</span><span class="sxs-lookup"><span data-stu-id="de6a0-133">Select the **Attributes** tab.</span></span> 
   1. <span data-ttu-id="de6a0-134">Adatentitás: Válassza ki azt az entitást, amely a mérni kívánt attribútumot tartalmazza.</span><span class="sxs-lookup"><span data-stu-id="de6a0-134">Data entity: Choose the entity that includes the attribute you want to measure.</span></span> 
   1. <span data-ttu-id="de6a0-135">Adatattribútum: Válassza ki az összesítési függvényben az mérték kiszámításához használni kívánt attribútumot.</span><span class="sxs-lookup"><span data-stu-id="de6a0-135">Data attribute: Choose the attribute you want to use in the aggregation function to calculate the measure.</span></span> <span data-ttu-id="de6a0-136">Egyszerre csak egy attribútumot választhat ki.</span><span class="sxs-lookup"><span data-stu-id="de6a0-136">You can only select one attribute at a time.</span></span>
   1. <span data-ttu-id="de6a0-137">Meglévő mértékből is kiválaszthat adatattribútumokat a **Mértékek** lapon. Másik lehetőségként megkeresheti egy entitást vagy mérték nevét is.</span><span class="sxs-lookup"><span data-stu-id="de6a0-137">You can also select a data attribute from an existing measure by selecting the **Measures** tab. Or, you can search for an entity or measure name.</span></span> 
   1. <span data-ttu-id="de6a0-138">Válassza a **Hozzáadás** lehetőséget, ha a kijelölt attribútumot hozzá szeretne adni a mértékhez.</span><span class="sxs-lookup"><span data-stu-id="de6a0-138">Select **Add** to add the selected attribute to the measure.</span></span>

   :::image type="content" source="media/measure-attribute-selection.png" alt-text="Válassza ki a számításokban használni kívánt attribútumot.":::

1. <span data-ttu-id="de6a0-140">Összetettebb mértékek építéshez további attribútumokat adhat hozzá, vagy használhat operátorokat a mértékfüggvényben.</span><span class="sxs-lookup"><span data-stu-id="de6a0-140">To build more complex measures, you can add more attributes or use math operators on your measure function.</span></span>

   :::image type="content" source="media/measure-math-operators.png" alt-text="Hozzon létre egy összetett mértéket a matematikai műveletek segítségével.":::

1. <span data-ttu-id="de6a0-142">Szűrők hozzáadásához válassza ki a **Szűrő** lehetőséget a konfigurációs területen.</span><span class="sxs-lookup"><span data-stu-id="de6a0-142">To add filters, select the **Filter** in the configuration area.</span></span> 
  
   1. <span data-ttu-id="de6a0-143">A **Szűrők** panel **Attribútum hozzáadása** szakaszában jelölje ki a szűrők létrehozásához használni kívánt attribútumot.</span><span class="sxs-lookup"><span data-stu-id="de6a0-143">In **Add attribute** section of the **Filters** pane, select the attribute you want to use to create filters.</span></span>
   1. <span data-ttu-id="de6a0-144">Állítsa be a szűrőoperátorokat, hogy minden kijelölt attribútumhoz definiálja a szűrőt.</span><span class="sxs-lookup"><span data-stu-id="de6a0-144">Set the filter operators to define the filter for every selected attribute.</span></span>
   1. <span data-ttu-id="de6a0-145">Válassza az **Alkalmaz** lehetőséget, ha a szűrőket hozzá szeretne adni a mértékhez.</span><span class="sxs-lookup"><span data-stu-id="de6a0-145">Select **Apply** to add the filters to the measure.</span></span>

1. <span data-ttu-id="de6a0-146">Dimenziók hozzáadásához válassza ki a **Dimenzió** lehetőséget a konfigurációs területen.</span><span class="sxs-lookup"><span data-stu-id="de6a0-146">To add dimensions, select **Dimension** in the configuration area.</span></span> <span data-ttu-id="de6a0-147">A dimenziók oszlopként fognak megjelenni a mérték kimeneti entitásában.</span><span class="sxs-lookup"><span data-stu-id="de6a0-147">Dimensions will show as columns in the measure output entity.</span></span>
   1. <span data-ttu-id="de6a0-148">Válassza a **Dimenziók szerkesztése** lehetőséget, ha olyan adatattribútumokat szeretne felvenni, amelyek szerint csoportosítja a mértékeket.</span><span class="sxs-lookup"><span data-stu-id="de6a0-148">Select **Edit dimensions** to add data attributes you want to group the measure values by.</span></span> <span data-ttu-id="de6a0-149">Például város vagy nem.</span><span class="sxs-lookup"><span data-stu-id="de6a0-149">For example, city or gender.</span></span> <span data-ttu-id="de6a0-150">Az *ügyfélszintű mértékek* létrehozásához alapértelmezés szerint a *CustomerID* dimenzió van kiválasztva.</span><span class="sxs-lookup"><span data-stu-id="de6a0-150">By default, the *CustomerID* dimension is selected to create *customer-level measures*.</span></span> <span data-ttu-id="de6a0-151">Ha *üzleti szintű mértékeket* szeretne létrehozni, eltávolíthatja az alapértelmezett dimenziót.</span><span class="sxs-lookup"><span data-stu-id="de6a0-151">You can remove the default dimension if you want to create *business-level measures*.</span></span>
   1. <span data-ttu-id="de6a0-152">Válassza a **Kész** lehetőséget, ha a dimenziókat hozzá szeretne adni a mértékhez.</span><span class="sxs-lookup"><span data-stu-id="de6a0-152">Select **Done** to add the dimensions to the measure.</span></span>

1. <span data-ttu-id="de6a0-153">Ha vannak olyan értékek az adatokban, amelyeket egész számra kell lecserélni, például a *null* értéket *0* értékkel, akkor válassza a **Szabályok** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="de6a0-153">If there are values in your data that you need to replace with an integer, for example, replace *null* with *0*, select **Rules**.</span></span> <span data-ttu-id="de6a0-154">Konfigurálja a szabályt, és csak egész számokat válasszon csereként.</span><span class="sxs-lookup"><span data-stu-id="de6a0-154">Configure the rule and make sure that you choose only whole numbers as replacements.</span></span>

1. <span data-ttu-id="de6a0-155">Ha a leképezett adatentitás és az *Ügyfél* entitás között több elérési út is van, válasszon egyet az azonosított [entitáskapcsolat-útvonalak közül](relationships.md).</span><span class="sxs-lookup"><span data-stu-id="de6a0-155">If there are multiple paths between the data entity you mapped and the *Customer* entity, you have to choose one of the identified [entity relationship paths](relationships.md).</span></span> <span data-ttu-id="de6a0-156">A mértékek eredményei a kiválasztott elérési úttól függően változhatnak.</span><span class="sxs-lookup"><span data-stu-id="de6a0-156">Measure results can vary depending on the selected path.</span></span> 
   1. <span data-ttu-id="de6a0-157">Válassza ki az **Adatbeállítások** lehetőséget, és válassza ki az entitás elérési útját, amely a mérték azonosítására fog használni.</span><span class="sxs-lookup"><span data-stu-id="de6a0-157">Select **Data preferences** and choose the entity path that should be used to identify your measure.</span></span> <span data-ttu-id="de6a0-158">Ha az *Ügyfél* entitásnak csak egyetlen elérési útja van, akkor a vezérlő nem fog mutatni.</span><span class="sxs-lookup"><span data-stu-id="de6a0-158">If there's only a single path to the *Customer* entity, this control won't show.</span></span>
   1. <span data-ttu-id="de6a0-159">Válassza a **Kész** lehetőséget a kiválasztás alkalmazáshoz.</span><span class="sxs-lookup"><span data-stu-id="de6a0-159">Select **Done** to apply your selection.</span></span> 

   :::image type="content" source="media/measures-data-preferences.png" alt-text="Válassza ki a mértékhez tartozó entitás elérési utat.":::

1. <span data-ttu-id="de6a0-161">Ha további számításokat szeretne hozzáadni az mértékhez, válassza az **Új számítás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="de6a0-161">To add more calculations for the measure, select **New calculation**.</span></span> <span data-ttu-id="de6a0-162">Az új számításokhoz csak ugyanazon az entitás elérési úton használhatók entitások.</span><span class="sxs-lookup"><span data-stu-id="de6a0-162">You can only use entities on the same entity path for new calculations.</span></span> <span data-ttu-id="de6a0-163">A további számítások új oszlopként fognak megjelenni a mérték kimeneti entitásában.</span><span class="sxs-lookup"><span data-stu-id="de6a0-163">More calculations will show as new columns in the measure output entity.</span></span>

1. <span data-ttu-id="de6a0-164">Válassza a **...** lehetőséget a mértékből szármató számítás **Duplikálásához**, **Átnevezéséhez** vagy **Eltávolításához**.</span><span class="sxs-lookup"><span data-stu-id="de6a0-164">Select **...** on the calculation to **Duplicate**, **Rename**, or **Remove** a calculation from a measure.</span></span>

1. <span data-ttu-id="de6a0-165">Az **Előnézet** területen a mérték kimeneti entitásának adatsémáját látja a szűrőkkel és a dimenziókkal.</span><span class="sxs-lookup"><span data-stu-id="de6a0-165">In the **Preview** area, you'll see the data schema of the measure output entity, including filters and dimensions.</span></span> <span data-ttu-id="de6a0-166">Az előnézet dinamikusan reagál a konfiguráció változásaira.</span><span class="sxs-lookup"><span data-stu-id="de6a0-166">The preview reacts dynamically to changes in the configuration.</span></span>

1. <span data-ttu-id="de6a0-167">Válassza a **Futtatás** lehetőséget a konfigurált mértékhez tartozó eredmények kiszámításához.</span><span class="sxs-lookup"><span data-stu-id="de6a0-167">Select **Run** to calculate results for the configured measure.</span></span> <span data-ttu-id="de6a0-168">Válassza a **Mentés és bezárás** lehetőséget, ha meg szeretné tartani az aktuális konfigurációt, és a mértéket később szeretné futtatni.</span><span class="sxs-lookup"><span data-stu-id="de6a0-168">Select **Save and close** if you want to keep the current configuration and run the measure later.</span></span>

1. <span data-ttu-id="de6a0-169">A listában az újonnan létrehozott mértékegységet a **Mértékek** listában jelenítheti meg.</span><span class="sxs-lookup"><span data-stu-id="de6a0-169">Go to **Measures** to see the newly created measure in the list.</span></span>

## <a name="use-a-template-to-build-a-measure"></a><span data-ttu-id="de6a0-170">Sablon használata mértékek építéséhez</span><span class="sxs-lookup"><span data-stu-id="de6a0-170">Use a template to build a measure</span></span>

<span data-ttu-id="de6a0-171">A leggyakrabban használt mértékeket előre definiált sablonok segítségével hozhatja létre.</span><span class="sxs-lookup"><span data-stu-id="de6a0-171">You can use predefined templates of commonly used measures to create them.</span></span> <span data-ttu-id="de6a0-172">A sablonok részletes leírása és az interaktív élmény segít a hatékony mérték létrehozásában.</span><span class="sxs-lookup"><span data-stu-id="de6a0-172">Detailed descriptions of the templates and a guided experience help you with efficient measure creation.</span></span> <span data-ttu-id="de6a0-173">A sablonok az *Egyesített tevékenység* entitásból származó leképezett adatokra épülnek.</span><span class="sxs-lookup"><span data-stu-id="de6a0-173">Templates build on mapped data from the *Unified Activity* entity.</span></span> <span data-ttu-id="de6a0-174">Ezért mindenképpen konfiguráljon [ügyféltevékenységeket](activities.md), mielőtt sablonból hoz létre mértéket.</span><span class="sxs-lookup"><span data-stu-id="de6a0-174">So make sure you have configured [customer activities](activities.md) before you create a measure from a template.</span></span>

<span data-ttu-id="de6a0-175">Elérhető mértéksablonok:</span><span class="sxs-lookup"><span data-stu-id="de6a0-175">Available measure templates:</span></span> 
- <span data-ttu-id="de6a0-176">Tranzakció átlagos értéke (ATV)</span><span class="sxs-lookup"><span data-stu-id="de6a0-176">Average transaction value (ATV)</span></span>
- <span data-ttu-id="de6a0-177">Tranzakció összértéke</span><span class="sxs-lookup"><span data-stu-id="de6a0-177">Total transaction value</span></span>
- <span data-ttu-id="de6a0-178">Átlagos napi bevétel</span><span class="sxs-lookup"><span data-stu-id="de6a0-178">Average daily revenue</span></span>
- <span data-ttu-id="de6a0-179">Átlagos éves bevétel</span><span class="sxs-lookup"><span data-stu-id="de6a0-179">Average yearly revenue</span></span>
- <span data-ttu-id="de6a0-180">Tranzakció száma</span><span class="sxs-lookup"><span data-stu-id="de6a0-180">Transaction count</span></span>
- <span data-ttu-id="de6a0-181">Szerzett hűségpontok</span><span class="sxs-lookup"><span data-stu-id="de6a0-181">Loyalty points earned</span></span>
- <span data-ttu-id="de6a0-182">Beváltott hűségpontok</span><span class="sxs-lookup"><span data-stu-id="de6a0-182">Loyalty points redeemed</span></span>
- <span data-ttu-id="de6a0-183">Hűségpontok egyenlege</span><span class="sxs-lookup"><span data-stu-id="de6a0-183">Loyalty points balance</span></span>
- <span data-ttu-id="de6a0-184">Ügyfél aktív életciklusa</span><span class="sxs-lookup"><span data-stu-id="de6a0-184">Active customer lifespan</span></span>
- <span data-ttu-id="de6a0-185">Hűség tagságának időtartama</span><span class="sxs-lookup"><span data-stu-id="de6a0-185">Loyalty membership duration</span></span>
- <span data-ttu-id="de6a0-186">Az utolsó vásárlás óta eltelt idő</span><span class="sxs-lookup"><span data-stu-id="de6a0-186">Time since last purchase</span></span>

<span data-ttu-id="de6a0-187">A következő eljárás egy új mérték használatával való felépítés lépéseit ismerteti.</span><span class="sxs-lookup"><span data-stu-id="de6a0-187">The following procedure outlines the steps to build a new measure using a template.</span></span>

1. <span data-ttu-id="de6a0-188">A célközönség információin belül nyissa meg a következőt: **Mérőszámok**.</span><span class="sxs-lookup"><span data-stu-id="de6a0-188">In audience insights, go to **Measures**.</span></span>

1. <span data-ttu-id="de6a0-189">Válassza az **Új**, és a **Sablon kiválasztása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="de6a0-189">Select **New** and select **Choose a template**.</span></span>

   :::image type="content" source="media/measure-use-template.png" alt-text="Képernyőkép a legördülő menüről, amikor új mértéket hoz létre a sablon kiemelése segítségével.":::

1. <span data-ttu-id="de6a0-191">Keresse meg az igényeinek megfelelő sablont, és válassza a **Sablon kiválasztása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="de6a0-191">Find the template that fits your need and select **Choose template**.</span></span>

1. <span data-ttu-id="de6a0-192">Tekintse át a kötelező adatokat, és válassza az **Első lépések** lehetőséget, ha minden adat a megfelelő helyen van.</span><span class="sxs-lookup"><span data-stu-id="de6a0-192">Review the required data and select **Get started** if you have all the data in place.</span></span>

1. <span data-ttu-id="de6a0-193">A **Név szerkesztése** ablaktáblában állítsa be a mérték és a kimeneti entitás nevét.</span><span class="sxs-lookup"><span data-stu-id="de6a0-193">In the **Edit name** pane, set the name for your measure and the output entity.</span></span> 

1. <span data-ttu-id="de6a0-194">Válassza a **Kész** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="de6a0-194">Select **Done**.</span></span>

1. <span data-ttu-id="de6a0-195">Adja meg az adat használandó időkeretét az **Időszak beállítása** szakaszban.</span><span class="sxs-lookup"><span data-stu-id="de6a0-195">In the **Set time period** section, define the time frame of the data to use.</span></span> <span data-ttu-id="de6a0-196">Válassza ki, hogy az új mérték lefedje-e a teljes adatkészletet a **Minden idő** kiválasztásával.</span><span class="sxs-lookup"><span data-stu-id="de6a0-196">Choose if you want the new measure to cover the entire data set by selecting **All time**.</span></span> <span data-ttu-id="de6a0-197">Vagy ha azt szeretné, hogy a mérték egy **Adott időszakra** összpontosítson.</span><span class="sxs-lookup"><span data-stu-id="de6a0-197">Or if you want the measure to focus on a **Specific time period**.</span></span>

   :::image type="content" source="media/measure-set-time-period.png" alt-text="Képernyőkép, amely egy sablonból származó mérték konfiguálásakor mutatja az időszak szakaszt.":::

1. <span data-ttu-id="de6a0-199">A következő szakaszban válassza az **Adatok hozzáadása** lehetőséget a tevékenységek kiválasztásához, és az *Egyesített tevékenység* entitásból képezze le a megfelelő adatokat.</span><span class="sxs-lookup"><span data-stu-id="de6a0-199">In the next section, select **Add data** to choose the activities and map the corresponding data from your *Unified Activity* entity.</span></span>

    1. <span data-ttu-id="de6a0-200">A 1/2. lépés: A **Tevékenység típusa** alatt válassza ki a használni kívánt entitás típusát.</span><span class="sxs-lookup"><span data-stu-id="de6a0-200">Step 1 of 2: Under **Activity type**, choose the type of the entity you want to use.</span></span> <span data-ttu-id="de6a0-201">A **Tevékenységekhez** válassza ki a leképezni kívánt entitásokat.</span><span class="sxs-lookup"><span data-stu-id="de6a0-201">For **Activities**, select the entities you want to map.</span></span>
    1. <span data-ttu-id="de6a0-202">2/2. lépés: Válassza ki az attribútumot az *Egyesített tevékenység* entitásból a képlet által megkövetelt összetevőhöz.</span><span class="sxs-lookup"><span data-stu-id="de6a0-202">Step 2 of 2: Choose the attribute from the *Unified Activity* entity for the component required by the formula.</span></span> <span data-ttu-id="de6a0-203">Például az Átlagos tranzakció értéke a Tranzakció értéket képviselő attribútum.</span><span class="sxs-lookup"><span data-stu-id="de6a0-203">For example, for Average transaction value, it's the attribute representing the Transaction value.</span></span> <span data-ttu-id="de6a0-204">A **Tevékenység időbélyegző** esetén válassza ki az Egyesített tevékenység entitás attribútumát, amely a tevékenység dátumát és időpontját jelképezi.</span><span class="sxs-lookup"><span data-stu-id="de6a0-204">For **Activity timestamp**, choose the attribute from the Unified Activity entity that represents the date and time of the activity.</span></span>
   
1. <span data-ttu-id="de6a0-205">Miután az adatleképezés sikeres volt, az állapot **Befejezett** értékre vált, valamint láthatja a leképezett tevékenységek és attribútumok nevét.</span><span class="sxs-lookup"><span data-stu-id="de6a0-205">Once the data mapping is successful, you can see the status as **Complete** and the name of the mapped activities and attributes.</span></span>

   :::image type="content" source="media/measure-template-configured.png" alt-text="Képernyőkép a mérősablon teljes konfigurálásról.":::

1. <span data-ttu-id="de6a0-207">Most már a **Futtatás** lehetőséget is választhatja a mérték eredményének kiszámításához.</span><span class="sxs-lookup"><span data-stu-id="de6a0-207">You can now select **Run** to calculate the results of the measure.</span></span> <span data-ttu-id="de6a0-208">Későbbi finomításhoz válassza a **Tervezet mentése** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="de6a0-208">To refine it later, select **Save draft**.</span></span>

## <a name="manage-your-measures"></a><span data-ttu-id="de6a0-209">Intézkedések kezelése</span><span class="sxs-lookup"><span data-stu-id="de6a0-209">Manage your measures</span></span>

<span data-ttu-id="de6a0-210">A **Mértékek** lapon láthatja a mértékek listáját.</span><span class="sxs-lookup"><span data-stu-id="de6a0-210">You can find the list of measures on the **Measures** page.</span></span>

<span data-ttu-id="de6a0-211">Információkat talál a mérték típusáról, az létrehozóról, a létrehozás dátumáról, a státuszáról és az állapotáról.</span><span class="sxs-lookup"><span data-stu-id="de6a0-211">You'll find information about the measure type, the creator, creation date, status, and state.</span></span> <span data-ttu-id="de6a0-212">Ha kiválaszt egy mértéket a listából, akkor megtekintheti a kimenetet, és letölthet egy .CSV-fájl.</span><span class="sxs-lookup"><span data-stu-id="de6a0-212">When you select a measure from the list, you can preview the output and download a .CSV file.</span></span>

<span data-ttu-id="de6a0-213">Ha egyszerre szeretné frissíteni az összes intézkedést, akkor jelölje be az **összes frissítése** lehetőséget egy adott intézkedés kiválasztása nélkül.</span><span class="sxs-lookup"><span data-stu-id="de6a0-213">To refresh all of your measures at the same time, select **Refresh all** without selecting a specific measure.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="de6a0-214">![Az egyes intézkedések kezelésére szolgáló műveletek](media/measure-actions.png "Az egyes intézkedések kezelésére szolgáló műveletek")</span><span class="sxs-lookup"><span data-stu-id="de6a0-214">![Actions to manage single measures](media/measure-actions.png "Actions to manage single measures")</span></span>

<span data-ttu-id="de6a0-215">Válasszon ki egy mértéket a listából a következő lehetőségekhez:</span><span class="sxs-lookup"><span data-stu-id="de6a0-215">Select a measure from the list for the following options:</span></span>

- <span data-ttu-id="de6a0-216">Adja meg a mérőszám nevét a részletek megtekintéséhez.</span><span class="sxs-lookup"><span data-stu-id="de6a0-216">Select the measure name to see its details.</span></span>
- <span data-ttu-id="de6a0-217">**Szerkessze** a mérőszám konfigurációját.</span><span class="sxs-lookup"><span data-stu-id="de6a0-217">**Edit** the configuration of the measure.</span></span>
- <span data-ttu-id="de6a0-218">**Frissítse** a mértéket a legújabb adatok alapján.</span><span class="sxs-lookup"><span data-stu-id="de6a0-218">**Refresh** the measure based on the latest data.</span></span>
- <span data-ttu-id="de6a0-219">**Nevezze át** az intézkedést.</span><span class="sxs-lookup"><span data-stu-id="de6a0-219">**Rename** the measure.</span></span>
- <span data-ttu-id="de6a0-220">**Törölje** az intézkedést.</span><span class="sxs-lookup"><span data-stu-id="de6a0-220">**Delete** the measure.</span></span>
- <span data-ttu-id="de6a0-221">**Aktiválás** vagy **Inaktiválás**.</span><span class="sxs-lookup"><span data-stu-id="de6a0-221">**Activate** or **Deactivate**.</span></span> <span data-ttu-id="de6a0-222">Az inaktív mértékek nem frissülnek az [ütemezett frissítés](system.md#schedule-tab) során.</span><span class="sxs-lookup"><span data-stu-id="de6a0-222">Inactive measures won't get refreshed during a [scheduled refresh](system.md#schedule-tab).</span></span>

> [!TIP]
> <span data-ttu-id="de6a0-223">A feladatokhoz/folyamatokhoz [hatféle állapot](system.md#status-types) tartozhat.</span><span class="sxs-lookup"><span data-stu-id="de6a0-223">There are [six types of status](system.md#status-types) for tasks/processes.</span></span> <span data-ttu-id="de6a0-224">Emellett a legtöbb folyamat [más alsóbb szintű folyamatoktól is függ](system.md#refresh-policies).</span><span class="sxs-lookup"><span data-stu-id="de6a0-224">Additionally, most processes [depend on other downstream processes](system.md#refresh-policies).</span></span> <span data-ttu-id="de6a0-225">Kiválaszthatja egy folyamat állapotát, és megtekintheti a hozzá tartozó teljes feladat folyamatának részleteit.</span><span class="sxs-lookup"><span data-stu-id="de6a0-225">You can select the status of a process to see details on the progress of the entire job.</span></span> <span data-ttu-id="de6a0-226">Miután kiválasztotta a **Részletek megtekintése** lehetőséget a feladat egyik feladatához, további információk jelennek meg: feldolgozási idő, legutóbbi feldolgozás dátuma, és a feladathoz társított összes hiba és figyelmeztetés.</span><span class="sxs-lookup"><span data-stu-id="de6a0-226">After selecting **See details** for one of the job's tasks, you find additional information: processing time, the last processing date, and all errors and warnings associated with the task.</span></span>

## <a name="next-step"></a><span data-ttu-id="de6a0-227">Következő lépés</span><span class="sxs-lookup"><span data-stu-id="de6a0-227">Next step</span></span>

<span data-ttu-id="de6a0-228">Az [ügyfélszegmens](segments.md) létrehozásához meglévő mértéket használhat.</span><span class="sxs-lookup"><span data-stu-id="de6a0-228">You cam use existing measures to create [a customer segment](segments.md).</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]
