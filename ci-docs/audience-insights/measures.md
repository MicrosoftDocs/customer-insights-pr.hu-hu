---
title: Mérőszámok létrehozása és szerkesztése
description: Határozza meg az ügyfélhez kapcsolódó mérőszámokat, amelyekkel elemezheti és szemléltetheti bizonyos üzleti területek teljesítményét.
ms.date: 10/15/2020
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
ms.reviewer: wameng
manager: shellyha
ms.openlocfilehash: 0e214a6eb66abd27f7292db3ce2c2a6e16a8ff33
ms.sourcegitcommit: cf9b78559ca189d4c2086a66c879098d56c0377a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/03/2020
ms.locfileid: "4406021"
---
# <a name="define-and-manage-measures"></a><span data-ttu-id="f2a8d-103">Az intézkedések definiálása és kezelése</span><span class="sxs-lookup"><span data-stu-id="f2a8d-103">Define and manage measures</span></span>

<span data-ttu-id="f2a8d-104">A **Mérőszámok** olyan fő teljesítménymutatókat (KPI) jelentenek, amelyek adott üzleti területek teljesítményét és működését tükrözik.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-104">**Measures** represent key performance indicators (KPIs) that reflect the performance and health of specific business areas.</span></span> <span data-ttu-id="f2a8d-105">A célközönség-információk a különböző típusú intézkedések kiépítésére szolgáló intuitív élményt nyújt, egy lekérdezés-szerkesztő segítségével, amely nem igényli az intézkedések kézi kódolását vagy érvényesítését.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-105">Audience insights provides an intuitive experience for building different types of measures, using a query builder that doesn't require you to code or validate your measures manually.</span></span> <span data-ttu-id="f2a8d-106">Az üzleti mérőszámokat a **Kezdőlap** oldalon követheti nyomon, és megtekintheti az egyes ügyfelekre vonatkozó mérőszámokat az **Ügyfélkártya** részben, és mérőszámokkal meghatározhatja az ügyfélszegmenseket a **Szegmensek** oldalon.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-106">You can track your business measures on the **Home** page, see measures for specific customers on the **Customer Card**, and use measures to define customer segments on the **Segments** page.</span></span>

## <a name="create-a-measure"></a><span data-ttu-id="f2a8d-107">Mérőszám létrehozása</span><span class="sxs-lookup"><span data-stu-id="f2a8d-107">Create a measure</span></span>

<span data-ttu-id="f2a8d-108">Ez a rész végigvezeti a mérőszám semmiből történő létrehozásának lépésein.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-108">This section walks you through creating a measure from scratch.</span></span> <span data-ttu-id="f2a8d-109">Mérőszámokat hozhat létre olyan adatokkal, amelyek több adatforrásból származnak, és az ügyfél entitáson keresztül kapcsolódnak egymáshoz.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-109">You can build measures with data from multiple data sources that are connected through the Customer entity.</span></span> <span data-ttu-id="f2a8d-110">Bizonyos [szolgáltatási korlátozások](service-limits.md) érvényesek.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-110">Some [service limits](service-limits.md) apply.</span></span>

1. <span data-ttu-id="f2a8d-111">A célközönség információin belül nyissa meg a következőt: **Mérőszámok**.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-111">In audience insights, go to **Measures**.</span></span>

2. <span data-ttu-id="f2a8d-112">Válassza az **Új mérőszám** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-112">Select **New measure**.</span></span>

3. <span data-ttu-id="f2a8d-113">Válassza ki a mérőszám **típusát**:</span><span class="sxs-lookup"><span data-stu-id="f2a8d-113">Choose the measure **Type**:</span></span>

   - <span data-ttu-id="f2a8d-114">**Ügyfélattribútum**: Egyetlen mező ügyfelenként, amely az ügyfél pontszámát, értékét vagy állapotát tükrözi.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-114">**Customer attribute**: A single field per customer that reflects a score, value, or state for the customer.</span></span> <span data-ttu-id="f2a8d-115">Az ügyfelek attribútumai egy új, a rendszer által létrehozott, **Customer_Measure** nevű entitásban attribútumokként jönnek létre.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-115">Customer attributes are created as attributes in a new system-generated entity called **Customer_Measure**.</span></span>

   - <span data-ttu-id="f2a8d-116">**Ügyfélmérőszám**: Az ügyfelek viselkedésének vonatkozó információk a kijelölt dimenziók szerinti részletezéssel.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-116">**Customer measure**: Insights on customer behavior with breakdown by selected dimensions.</span></span> <span data-ttu-id="f2a8d-117">A rendszer minden egyes mérőszámhoz létrehoz egy új entitást, amely esetleg több bejegyzést tartalmaz egy ügyfélnél.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-117">A new entity is generated for each measure, potentially with multiple records per customer.</span></span>

   - <span data-ttu-id="f2a8d-118">**Üzleti mérőszám**: Nyomon követi a vállalkozás teljesítményét és egészségét.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-118">**Business measure**: Tracks your business performance and health of the business.</span></span> <span data-ttu-id="f2a8d-119">Az üzleti mérőszámok két különböző kimenettel rendelkezhetnek: egy numerikus kimenet, amely a **Kezdőlapon** jelenik meg, vagy egy új entitás, amelyet az **Entitások** oldalon talál.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-119">Business measures can have two different outputs: a numeric output that shows on the **Home** page or a new entity that you find on the **Entities** page.</span></span>

4. <span data-ttu-id="f2a8d-120">Adjon meg egy **Név** értéket, és egy nem kötelező **Megjelenítendő nevet**, majd nyomja meg a **Tovább** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-120">Provide a **Name** and an optional **Display name**, then select **Next**.</span></span>

5. <span data-ttu-id="f2a8d-121">Az **Entitás** részben válassza ki az első entitást a legördülő listából.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-121">In the **Entities** section, select the first entity from the drop-down list.</span></span> <span data-ttu-id="f2a8d-122">Ezen a ponton el kell döntenie, hogy szükségesek-e további entitások a mértékegység meghatározásának részeként.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-122">At this point, you should decide whether additional entities are needed as part of your measure definition.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="f2a8d-123">![Mérőszám definíciója](media/measure-definition.png "Mérőszám definíciója")</span><span class="sxs-lookup"><span data-stu-id="f2a8d-123">![Measure definition](media/measure-definition.png "Measure definition")</span></span>

   <span data-ttu-id="f2a8d-124">További entitások hozzáadásához válassza az **Entitás hozzáadása** lehetőséget, és válassza ki a mérőszámhoz használni kívánt entitásokat.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-124">To add more entities, select **Add entity** and select entities you want to use for the measure.</span></span>

   > [!NOTE]
   > <span data-ttu-id="f2a8d-125">Olyan entitásokat választhat csak, amelyek kapcsolódnak az elsőként kiválasztott entitáshoz.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-125">You can select only entities that have relationships to your starting entity.</span></span> <span data-ttu-id="f2a8d-126">Ha további tájékoztatást szeretne kapni a kapcsolatok meghatározásáról, lásd. [Kapcsolatok](relationships.md).</span><span class="sxs-lookup"><span data-stu-id="f2a8d-126">For more information about defining relationships, see [Relationships](relationships.md).</span></span>

6. <span data-ttu-id="f2a8d-127">Másik megoldásként Ön is konfigurálhatja a változókat.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-127">Optionally, you can configure variables.</span></span> <span data-ttu-id="f2a8d-128">A **Változók** szakaszban válassza az **új változó** elemet.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-128">In the **Variables** section, select **New variable**.</span></span>

   <span data-ttu-id="f2a8d-129">A változók a kijelölt rekordokon végrehajtott számítások.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-129">Variables are calculations that are made on each of your selected records.</span></span> <span data-ttu-id="f2a8d-130">Például a pénztári (POS) és online értékesítés összesítése az egyes ügyfelek rekordjaira vonatkozóan.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-130">For example, summing point-of-sale (POS) and online sales for each of your customers' records.</span></span>

7. <span data-ttu-id="f2a8d-131">Adja meg a változó **nevét**.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-131">Provide a **Name** for the variable.</span></span>

8. <span data-ttu-id="f2a8d-132">A **Kifejezés** területen válassza ki azt a mezőt, amellyel el szeretné kezdeni a számítást.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-132">In the **Expression** area, choose a field to begin your calculation with.</span></span>

9. <span data-ttu-id="f2a8d-133">Írjon be egy kifejezést a **Kifejezés** területen, és válassza ki a számításba szerepeltetendő további mezőket.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-133">Type an expression in the **Expression** area while choosing more fields to be included in your calculation.</span></span>

   > [!NOTE]
   > <span data-ttu-id="f2a8d-134">Jelenleg csak aritmetikai kifejezések támogatottak.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-134">Currently, only arithmetic expressions are supported.</span></span> <span data-ttu-id="f2a8d-135">Emellett a változók számítása nem támogatott a különböző [entitásútvonalról](relationships.md) származó entitások esetén.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-135">Additionally, variable calculation isn't supported for entities from different [entity paths](relationships.md).</span></span>

10. <span data-ttu-id="f2a8d-136">Válassza a **Kész** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-136">Select **Done**.</span></span>

11. <span data-ttu-id="f2a8d-137">A **Mértékegység meghatározása** szakaszban azt határozhatja meg, hogy a kiválasztott entitások és a számított változók hogyan legyenek összesítve egy új mérőszám entitásában vagy attribútumában.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-137">In the **Measure definition** section, you'll define how your chosen entities and calculated variables are aggregated in a new measure entity or attribute.</span></span>

12. <span data-ttu-id="f2a8d-138">Válassza az **Új dimenzió** elemet.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-138">Select **New dimension**.</span></span> <span data-ttu-id="f2a8d-139">A dimenzióra *csoportosítási szempont* függvényként is tekinthet.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-139">You can think of a dimension as a *group by* function.</span></span> <span data-ttu-id="f2a8d-140">A Mérőszám entitás vagy attribútum adatkimeneteit a rendszer az összes megadott dimenzió alapján csoportosítja.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-140">The data output of your Measure entity or attribute will be grouped by all of your defined dimensions.</span></span>

    > [!div class="mx-imgBorder"]
    > <span data-ttu-id="f2a8d-141">![Összesítési ciklus kiválasztása](media/measures-businessreport-measure-definition2.png "Összesítési ciklus kiválasztása")</span><span class="sxs-lookup"><span data-stu-id="f2a8d-141">![Choose aggregate cycle](media/measures-businessreport-measure-definition2.png "Choose aggregate cycle")</span></span>

    <span data-ttu-id="f2a8d-142">Válassza ki vagy adja meg a következő adatokat a dimenzió meghatározása részeként:</span><span class="sxs-lookup"><span data-stu-id="f2a8d-142">Select or enter the following information as part of your dimension's definition:</span></span>

    - <span data-ttu-id="f2a8d-143">**Entitás**: Ha egy Mérőszám entitást definiál, akkor legalább egy attribútumot tartalmaznia kell.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-143">**Entity**: If you define a Measure entity, it should include at least one attribute.</span></span> <span data-ttu-id="f2a8d-144">Ha Mérőszám attribútumot határoz meg, akkor alapértelmezés szerint csak egyetlen attribútumot fog tartalmazni.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-144">If you define a Measure attribute, it will include only one attribute by default.</span></span> <span data-ttu-id="f2a8d-145">Ez a beállítás az attribútumot tartalmazó entitás kiválasztásáról szól.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-145">This selection is about choosing the entity that includes that attribute.</span></span>
    - <span data-ttu-id="f2a8d-146">**Mező**: válassza ki azt a konkrét attribútumot, amelyet be szeretne vonni a mérőszám entitásba vagy attribútumba.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-146">**Field**: Choose the specific attribute to be included either in your Measure entity or attribute.</span></span>
    - <span data-ttu-id="f2a8d-147">**Gyűjtő**: válassza ki, hogy az adatokat napi, havi vagy éves szinten szeretné összesíteni.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-147">**Bucket**: Choose whether you want to aggregate data on a daily, monthly, or annual basis.</span></span> <span data-ttu-id="f2a8d-148">Csak akkor szükséges, ha a Dátumtípus attribútumot jelölte ki.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-148">It's a required selection only if you've selected a Date type attribute.</span></span>
    - <span data-ttu-id="f2a8d-149">**Mint**: Meghatározza az új mező nevét.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-149">**As**: Defines the name of your new field.</span></span>
    - <span data-ttu-id="f2a8d-150">**Megjelenítendő név**: meghatározza a mező megjelenítendő nevét.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-150">**Display name**: Defines the display name of your field.</span></span>

    > [!NOTE]
    > <span data-ttu-id="f2a8d-151">Az üzleti mérőszámot egyszámos entitásként menti a rendszer és megjelenik a **Kezdőlap** oldalon, ha csak nem ad több dimenziót a mérőszámhoz.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-151">Your business measure will be saved as a single-number entity and will appear on the **Home** page unless you add more dimensions to your measure.</span></span> <span data-ttu-id="f2a8d-152">További dimenziók hozzáadását követően a mérőszám *nem* jelenik meg a **kezdőlapon**.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-152">After adding more dimensions, the measure will *not* show up on the **Home** page.</span></span>

13. <span data-ttu-id="f2a8d-153">Tetszés szerint az összesítési funkciókat is hozzáadhatja.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-153">Optionally, add aggregation functions.</span></span> <span data-ttu-id="f2a8d-154">Bármely Ön által létrehozott összesítés az eredményeket egy új értékben hozza létre a Mérőszám entitást vagy attribútumot.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-154">Any aggregation that you create results in a new value within your Measures entity or attribute.</span></span> <span data-ttu-id="f2a8d-155">A támogatott aggregációs függvények a következők: **Min**, **Max**, **Average**, **Median**, **Sum**, **Count Unique**, **First** (a dimenzióérték rekordjai közül az elsőt veszi) és **Last** (a dimenzióértékhez utoljára hozzáadott rekordot veszi).</span><span class="sxs-lookup"><span data-stu-id="f2a8d-155">Supported aggregation functions are: **Min**, **Max**, **Average**, **Median**, **Sum**, **Count Unique**, **First** (takes the first record of a dimension value), and **Last** (takes the last record added to a dimension value).</span></span>

14. <span data-ttu-id="f2a8d-156">A mérőszám módosításainak alkalmazásához válassza a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-156">Select **Save** to apply your changes to the measure.</span></span>

## <a name="manage-your-measures"></a><span data-ttu-id="f2a8d-157">Intézkedések kezelése</span><span class="sxs-lookup"><span data-stu-id="f2a8d-157">Manage your measures</span></span>

<span data-ttu-id="f2a8d-158">Legalább egy mérték létrehozása után megtekintheti a mértékek listáját a **Mértékek** oldalon.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-158">After creating at least one measure, you'll see a list of measures on the **Measures** page.</span></span>

<span data-ttu-id="f2a8d-159">Itt információk találhatók a mérőszám típusáról, a létrehozóról, a létrehozás dátumáról és idejéről, az utolsó módosítás dátumáról és időpontjáról, állapotról (hogy a mérőszám aktív, inaktív vagy sikertelen) és az utolsó frissítés dátumáról és időpontjáról.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-159">You'll find information about the measure type, the creator, creation date and time, last edit date and time, status (whether the measure is active, inactive, or failed), and last refresh date and time.</span></span> <span data-ttu-id="f2a8d-160">Ha egy intézkedést kiválaszt a listából, láthatja a kimenetének előnézetét.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-160">When you select a measure from the list, you can see a preview of its output.</span></span>

<span data-ttu-id="f2a8d-161">Ha egyszerre szeretné frissíteni az összes intézkedést, akkor jelölje be az **összes frissítése** lehetőséget egy adott intézkedés kiválasztása nélkül.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-161">To refresh all of your measures at the same time, select **Refresh all** without selecting a specific measure.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="f2a8d-162">![Az egyes intézkedések kezelésére szolgáló műveletek](media/measure-actions.png "Az egyes intézkedések kezelésére szolgáló műveletek")</span><span class="sxs-lookup"><span data-stu-id="f2a8d-162">![Actions to manage single measures](media/measure-actions.png "Actions to manage single measures")</span></span>

<span data-ttu-id="f2a8d-163">Másik lehetőségként jelöljön ki egy intézkedést a listából, és hajtsa végre az alábbi műveletek egyikét:</span><span class="sxs-lookup"><span data-stu-id="f2a8d-163">Alternatively, select a measure from the list and perform one of the following actions:</span></span>

- <span data-ttu-id="f2a8d-164">Adja meg a mérőszám nevét a részletek megtekintéséhez.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-164">Select the measure name to see its details.</span></span>
- <span data-ttu-id="f2a8d-165">**Szerkessze** a mérőszám konfigurációját.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-165">**Edit** the configuration of the measure.</span></span>
- <span data-ttu-id="f2a8d-166">**Nevezze át** az intézkedést.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-166">**Rename** the measure.</span></span>
- <span data-ttu-id="f2a8d-167">**Törölje** az intézkedést.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-167">**Delete** the measure.</span></span>
- <span data-ttu-id="f2a8d-168">Jelölje ki a három pontot (...), majd a **Frissítés** lehetőséggel indítsa el az intézkedés frissítési folyamatát.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-168">Select the ellipsis (...) and then **Refresh** to start the refresh process for the measure.</span></span>
- <span data-ttu-id="f2a8d-169">Jelölje ki a három pontot (...), majd a **Letöltés** lehetőséggel töltse le az intézkedés .CSV fájlját.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-169">Select the ellipsis (...) and then **Download** to get a .CSV file of the measure.</span></span>

> [!TIP]
> <span data-ttu-id="f2a8d-170">A feladatokhoz/folyamatokhoz [hatféle állapot](system.md#status-types) tartozhat.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-170">There are [six types of status](system.md#status-types) for tasks/processes.</span></span> <span data-ttu-id="f2a8d-171">Emellett a legtöbb folyamat [más alsóbb szintű folyamatoktól is függ](system.md#refresh-policies).</span><span class="sxs-lookup"><span data-stu-id="f2a8d-171">Additionally, most processes [depend on other downstream processes](system.md#refresh-policies).</span></span> <span data-ttu-id="f2a8d-172">Kiválaszthatja egy folyamat állapotát, és megtekintheti a hozzá tartozó teljes feladat folyamatának részleteit.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-172">You can select the status of a process to see details on the progress of the entire job.</span></span> <span data-ttu-id="f2a8d-173">Miután kiválasztotta a **Részletek megtekintése** lehetőséget a feladat egyik feladatához, további információk jelennek meg: feldolgozási idő, legutóbbi feldolgozás dátuma, és a feladathoz társított összes hiba és figyelmeztetés.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-173">After selecting **See details** for one of the job's tasks, you find additional information: processing time, the last processing date, and all errors and warnings associated with the task.</span></span>

## <a name="next-step"></a><span data-ttu-id="f2a8d-174">Következő lépés</span><span class="sxs-lookup"><span data-stu-id="f2a8d-174">Next step</span></span>

<span data-ttu-id="f2a8d-175">A meglévő mérőszámok használatával a **Szegmensek** oldalon hozhatja létre az első ügyfélszegmenst.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-175">You cam use existing measures to create your first customer segment on the **Segments** page.</span></span> <span data-ttu-id="f2a8d-176">További tudnivalókat a [Szegmensek](segments.md) részben talál.</span><span class="sxs-lookup"><span data-stu-id="f2a8d-176">For more information, see [Segments](segments.md).</span></span>
