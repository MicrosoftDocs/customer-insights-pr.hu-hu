---
title: Szegmensek létrehozása és kezelése
description: Hozzon létre ügyfelekből álló szegmenseket, és csoportosítsa őket különböző attribútumok alapján.
ms.date: 05/03/2021
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: JimsonChalissery
ms.author: jimsonc
ms.reviewer: mhart
manager: shellyha
ms.openlocfilehash: 550e509a24701fe5fcdeb9d54311872dc954156c
ms.sourcegitcommit: 72603fb39c4d5dbca71128815a2e1692542ea4dc
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/19/2021
ms.locfileid: "6064940"
---
# <a name="create-and-manage-segments"></a><span data-ttu-id="9d376-103">Szegmensek létrehozása és kezelése</span><span class="sxs-lookup"><span data-stu-id="9d376-103">Create and manage segments</span></span>

<span data-ttu-id="9d376-104">Összetett szűrőket definiálhat az egyesített ügyfélentitás és a kapcsolódó entitások körül.</span><span class="sxs-lookup"><span data-stu-id="9d376-104">Define complex filters around the unified customer entity and its related entities.</span></span> <span data-ttu-id="9d376-105">A feldolgozást követően minden szegmens létrehoz egy csoport olyan ügyfélrekordot, amellyel az exportálás után műveletek végezhetők.</span><span class="sxs-lookup"><span data-stu-id="9d376-105">Each segment, after processing, creates a set of customer records that you can export and take action on.</span></span> <span data-ttu-id="9d376-106">A szegmensek kezelése a **Szegmensek** oldalon történik.</span><span class="sxs-lookup"><span data-stu-id="9d376-106">Segments are managed on the **Segments** page.</span></span> 

<span data-ttu-id="9d376-107">A következő példa bemutatja a szegmentációs képességet.</span><span class="sxs-lookup"><span data-stu-id="9d376-107">The following example illustrates the segmentation capability.</span></span> <span data-ttu-id="9d376-108">Egy szegmenst definiáltak azokhoz az ügyfelekhez, akik legalább $500 értékben árukat rendeltek az utolsó 90 napban, *és* részt vettek egy ügyfélszolgálat-hívásban, amelyet eszkaláltak.</span><span class="sxs-lookup"><span data-stu-id="9d376-108">We've defined a segment for customers who ordered at least $500 of goods in the last 90 days *and* who were involved in a customer service call that got escalated.</span></span>

:::image type="content" source="media/segmentation-group1-2.png" alt-text="Képernyőkép a szegmensszerkesztő felhasználói felületéről; két, ügyfélszegmenst meghatározó csoport látható.":::

## <a name="create-a-new-segment"></a><span data-ttu-id="9d376-110">Új szegmens létrehozása</span><span class="sxs-lookup"><span data-stu-id="9d376-110">Create a new segment</span></span>

<span data-ttu-id="9d376-111">Új szegmens többféleképpen is létrehozható.</span><span class="sxs-lookup"><span data-stu-id="9d376-111">There are multiple ways to create a new segment.</span></span> <span data-ttu-id="9d376-112">Ez a szakasz azt ismerteti, hogyan hozhat létre üres *szegmenst* az alapoktól.</span><span class="sxs-lookup"><span data-stu-id="9d376-112">This section describes how to create a *blank segment* from scratch.</span></span> <span data-ttu-id="9d376-113">*Üres szegmenst* a meglévő entitások alapján, illetve a gépi tanulási modell *javasolt szegmensei* alapján is létrehozhat.</span><span class="sxs-lookup"><span data-stu-id="9d376-113">You can also create a *quick segment* based on existing entities or make use of machine learning models to get *suggested segments*.</span></span> <span data-ttu-id="9d376-114">További információk: [Szegmensek áttekintése](segments.md).</span><span class="sxs-lookup"><span data-stu-id="9d376-114">More information: [Segments overview](segments.md).</span></span>

<span data-ttu-id="9d376-115">A szegmensek létrehozásakor mentheti a tervezetet.</span><span class="sxs-lookup"><span data-stu-id="9d376-115">While creating a segment, you can save a draft.</span></span> <span data-ttu-id="9d376-116">A rendszer inaktív szegmensként menti a tervezetet, amely nem aktiválható, amíg be nem lett fejezve érvényes konfigurációval.</span><span class="sxs-lookup"><span data-stu-id="9d376-116">It will be saved as an inactive segment, and can't be activated it finished with a valid configuration.</span></span>

1. <span data-ttu-id="9d376-117">Lépjen a **Szegmensek** oldalra.</span><span class="sxs-lookup"><span data-stu-id="9d376-117">Go to the **Segments** page.</span></span>

1. <span data-ttu-id="9d376-118">Válassza az **új** > **üres szegmens** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="9d376-118">Select **New** > **Blank segment**.</span></span>

1. <span data-ttu-id="9d376-119">Az **Új szegmens** panelen válasszon egy szegmenstípust:</span><span class="sxs-lookup"><span data-stu-id="9d376-119">In the **New segment** pane, choose a segment type:</span></span>

   - <span data-ttu-id="9d376-120">A **dinamikus szegmens** ismétlődő ütemezés szerint [frissül](segments.md#refresh-segments).</span><span class="sxs-lookup"><span data-stu-id="9d376-120">**Dynamic segments** [refresh](segments.md#refresh-segments) on a recurring schedule.</span></span>
   - <span data-ttu-id="9d376-121">A **statikus szegmensek** egyszer, a létrehozásukkor futnak.</span><span class="sxs-lookup"><span data-stu-id="9d376-121">**Static segments** run once when you create it.</span></span>

1. <span data-ttu-id="9d376-122">Adja meg a szegmens **Kimeneti entitásának nevét**.</span><span class="sxs-lookup"><span data-stu-id="9d376-122">Provide an **Output entity name** for the segment.</span></span> <span data-ttu-id="9d376-123">Tetszés szerint megadhat egy megjelenítendő nevet és egy leírást is, amely segít a szegmens azonosításában.</span><span class="sxs-lookup"><span data-stu-id="9d376-123">Optionally, provide a display name, and a description that helps identifying the segment.</span></span>

1. <span data-ttu-id="9d376-124">Válassza a **Következő** elemet a **Szegmensépítő** oldalára való eljutáshoz, ahol megadhat egy csoportot.</span><span class="sxs-lookup"><span data-stu-id="9d376-124">Select **Next** to get to the **Segment builder** page where you define a group.</span></span> <span data-ttu-id="9d376-125">A csoport az ügyfelek halmaza.</span><span class="sxs-lookup"><span data-stu-id="9d376-125">A group is a set of customers.</span></span>

1. <span data-ttu-id="9d376-126">Válassza ki az entitást, amelyben szerepel az attribútum, amely alapján szegmentálni szeretne.</span><span class="sxs-lookup"><span data-stu-id="9d376-126">Choose the entity that includes the attribute you want to segment by.</span></span>

1. <span data-ttu-id="9d376-127">Válassza ki a szegmenshez tartozó attribútumot.</span><span class="sxs-lookup"><span data-stu-id="9d376-127">Choose the attribute to segment by.</span></span> <span data-ttu-id="9d376-128">Ez az attribútum a következő négy értéktípus egyike lehet: numerikus, szöveges, dátum vagy logikai.</span><span class="sxs-lookup"><span data-stu-id="9d376-128">This attribute can have one of four value types: numerical, string, date, or Boolean.</span></span>

1. <span data-ttu-id="9d376-129">Válasszon egy operátort, és adja meg a kijelölt attribútum értékét.</span><span class="sxs-lookup"><span data-stu-id="9d376-129">Choose an operator and a value for the selected attribute.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="9d376-130">![Egyéni csoportszűrő](media/customer-group-numbers.png "Ügyfélcsoportszűrő")</span><span class="sxs-lookup"><span data-stu-id="9d376-130">![Custom group filter](media/customer-group-numbers.png "Customer group filter")</span></span>

   |<span data-ttu-id="9d376-131">Szám</span><span class="sxs-lookup"><span data-stu-id="9d376-131">Number</span></span> |<span data-ttu-id="9d376-132">Definíció</span><span class="sxs-lookup"><span data-stu-id="9d376-132">Definition</span></span>  |
   |---------|---------|
   |<span data-ttu-id="9d376-133">0</span><span class="sxs-lookup"><span data-stu-id="9d376-133">1</span></span>     |<span data-ttu-id="9d376-134">Entity</span><span class="sxs-lookup"><span data-stu-id="9d376-134">Entity</span></span>          |
   |<span data-ttu-id="9d376-135">2</span><span class="sxs-lookup"><span data-stu-id="9d376-135">2</span></span>     |<span data-ttu-id="9d376-136">Attribútum</span><span class="sxs-lookup"><span data-stu-id="9d376-136">Attribute</span></span>          |
   |<span data-ttu-id="9d376-137">3</span><span class="sxs-lookup"><span data-stu-id="9d376-137">3</span></span>    |<span data-ttu-id="9d376-138">Operátor</span><span class="sxs-lookup"><span data-stu-id="9d376-138">Operator</span></span>         |
   |<span data-ttu-id="9d376-139">4</span><span class="sxs-lookup"><span data-stu-id="9d376-139">4</span></span>    |<span data-ttu-id="9d376-140">Érték</span><span class="sxs-lookup"><span data-stu-id="9d376-140">Value</span></span>         |

   1. <span data-ttu-id="9d376-141">Ha további feltételeket szeretne hozzáadni egy csoporthoz, akkor két logikai operátort használhat:</span><span class="sxs-lookup"><span data-stu-id="9d376-141">To add more conditions to a group, you can use two logical operators:</span></span>

      - <span data-ttu-id="9d376-142">**ÉS** operátor: mindkét feltételnek a szegmentálási folyamat részeként kell teljesülnie.</span><span class="sxs-lookup"><span data-stu-id="9d376-142">**AND** operator: Both conditions must be met as part of the segmentation process.</span></span> <span data-ttu-id="9d376-143">Ez a beállítás akkor a leghasznosabb, ha különböző entitások között határoz meg feltételeket.</span><span class="sxs-lookup"><span data-stu-id="9d376-143">This option is most useful when you define conditions across different entities.</span></span>

      - <span data-ttu-id="9d376-144">**VAGY** operátor: a szegmentálási folyamat részeként az egyik feltételnek meg kell felelnie.</span><span class="sxs-lookup"><span data-stu-id="9d376-144">**OR** operator: Either one of the conditions needs to be met as part of the segmentation process.</span></span> <span data-ttu-id="9d376-145">Ez a beállítás akkor a leghasznosabb, ha különböző feltételeket ad meg ugyanahhoz az entitáshoz.</span><span class="sxs-lookup"><span data-stu-id="9d376-145">This option is most useful when you define multiple conditions for the same entity.</span></span>

      > [!div class="mx-imgBorder"]
      > <span data-ttu-id="9d376-146">![VAGY operátor, ahol valamelyik feltételt teljesíteni kell](media/segmentation-either-condition.png "VAGY operátor, ahol valamelyik feltételt teljesíteni kell")</span><span class="sxs-lookup"><span data-stu-id="9d376-146">![OR operator where either condition needs to be met](media/segmentation-either-condition.png "OR operator where either condition needs to be met")</span></span>

      <span data-ttu-id="9d376-147">Jelenleg lehetséges egy **VAGY** operátor beágyazása egy **ÉS** operátor alá, de fordítva nem.</span><span class="sxs-lookup"><span data-stu-id="9d376-147">It's currently possible to nest an **OR** operator under an **AND** operator, but not the other way around.</span></span>

   1. <span data-ttu-id="9d376-148">Minden csoport ügyfelek egy csoportjával egyezik.</span><span class="sxs-lookup"><span data-stu-id="9d376-148">Each group matches set of customers.</span></span> <span data-ttu-id="9d376-149">A csoportok kombinálhatók, hogy tartalmazzák az üzleti esethez szükséges ügyfeleket.</span><span class="sxs-lookup"><span data-stu-id="9d376-149">You can combine groups to include the customers required for your business case.</span></span>    
   <span data-ttu-id="9d376-150">Válassza a **Csoport hozzáadása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="9d376-150">Select **Add Group**.</span></span>

      > [!div class="mx-imgBorder"]
      > <span data-ttu-id="9d376-151">![Ügyfélcsoport hozzáadása csoport](media/customer-group-add-group.png "Ügyfélcsoport hozzáadása csoport")</span><span class="sxs-lookup"><span data-stu-id="9d376-151">![Customer group add group](media/customer-group-add-group.png "Customer group add group")</span></span>

   1. <span data-ttu-id="9d376-152">Válasszon egyet a készletre vonatkozó operátorok közül: **Unió**, **Metszet** vagy **Kivétel**.</span><span class="sxs-lookup"><span data-stu-id="9d376-152">Select one of the set operators: **Union**, **Intersect**, or **Except**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="9d376-153">![Ügyfélcsoport hozzáadása egyesülés](media/customer-group-union.png "Ügyfélcsoport hozzáadása egyesülés")</span><span class="sxs-lookup"><span data-stu-id="9d376-153">![Customer group add union](media/customer-group-union.png "Customer group add union")</span></span>

   - <span data-ttu-id="9d376-154">Az **Egyesülés** egyesíti a két csoportot.</span><span class="sxs-lookup"><span data-stu-id="9d376-154">**Union** unites the two groups.</span></span>

   - <span data-ttu-id="9d376-155">A **Metszet** a két csoport átfedését veszi.</span><span class="sxs-lookup"><span data-stu-id="9d376-155">**Intersect** overlaps the two groups.</span></span> <span data-ttu-id="9d376-156">Csak az az adat *amely közös* kerül megtartásra mindkét egységesített csoportban.</span><span class="sxs-lookup"><span data-stu-id="9d376-156">Only data that *is common* to both groups is retained in the unified group.</span></span>

   - <span data-ttu-id="9d376-157">**Kivéve** kombinálja a két csoportot.</span><span class="sxs-lookup"><span data-stu-id="9d376-157">**Except** combines the two groups.</span></span> <span data-ttu-id="9d376-158">Csak azon adat kerül megtartásra az A csoportban, amely *nem közös* a B csoport adatival.</span><span class="sxs-lookup"><span data-stu-id="9d376-158">Only data in group A that *is not common* to data in group B is retained.</span></span>

1. <span data-ttu-id="9d376-159">Ha az entitás [kapcsolatokon](relationships.md) keresztül kapcsolódik az egyesített ügyfél entitáshoz, meg kell határoznia a kapcsolati útvonalat az érvényes szegmens létrehozásához.</span><span class="sxs-lookup"><span data-stu-id="9d376-159">If the entity is connected to the unified customer entity through [relationships](relationships.md), you need to define the relationship path to create a valid segment.</span></span> <span data-ttu-id="9d376-160">Adjon hozzá entitásokat a kapcsolati útvonalról, amíg ki nem tudja választani az **Ügyfél: CustomerInsights** entitást a legördülő menüből.</span><span class="sxs-lookup"><span data-stu-id="9d376-160">Add the entities from the relationship path until you can select the **Customer:CustomerInsights** entity from the dropdown.</span></span> <span data-ttu-id="9d376-161">Ezután minden lépéshez válassza ki az **Összes rekord** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="9d376-161">Then, choose **All records** for each step.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="9d376-162">![Kapcsolati útvonal a szegmens létrehozása során](media/segments-multiple-relationships.png "Kapcsolati útvonal a szegmens létrehozása során")</span><span class="sxs-lookup"><span data-stu-id="9d376-162">![Relationship path during segment creation](media/segments-multiple-relationships.png "Relationship path during segment creation")</span></span>

1. <span data-ttu-id="9d376-163">A szegmensek alapértelmezés szerint létrehoznak egy kimeneti entitást, amely a definiált szűrőknek megfelelő ügyfélprofilok összes attribútumát tartalmazza.</span><span class="sxs-lookup"><span data-stu-id="9d376-163">By default, segments generate an output entity that contains all attributes of customer profiles which match the defined filters.</span></span> <span data-ttu-id="9d376-164">Ha egy szegmens nem az *Ügyfél* entitáson alapul, akkor ezekből az entitásokból további attribútumokat adhat a kimeneti entitáshoz.</span><span class="sxs-lookup"><span data-stu-id="9d376-164">If a segment is based on other entities than the *Customer* entity, you can add more attributes from these entities to the output entity.</span></span> <span data-ttu-id="9d376-165">A **Projektattribútumok** kiválasztásával kiválaszthatja a kimeneti entitáshoz hozzáfűzni kívánt attribútumokat.</span><span class="sxs-lookup"><span data-stu-id="9d376-165">Select **Project attributes** to choose the attributes that will be appended to the output entity.</span></span>  
  
   <span data-ttu-id="9d376-166">Példa: A szegmens egy olyan entitáson alapul, amely az *Ügyfél* entitáshoz kapcsolódó ügyféltevékenységi adatokat tartalmaz.</span><span class="sxs-lookup"><span data-stu-id="9d376-166">Example: A segment is based on an entity that contains customer activity data which is related to the *Customer* entity.</span></span> <span data-ttu-id="9d376-167">A szegmens az utóbbi 60 napban a súgónak telefonáló összes ügyfelet keresi.</span><span class="sxs-lookup"><span data-stu-id="9d376-167">The segment looks for all customers that called the help desk in the last 60 days.</span></span> <span data-ttu-id="9d376-168">Megadhatja, hogy a hívás időtartamát és a hívások számát hozzáfűzi a kimeneti entitásban található összes egyező ügyfélrekordhoz.</span><span class="sxs-lookup"><span data-stu-id="9d376-168">You can choose to append the call duration and the number of calls to all matching customer records in the output entity.</span></span> <span data-ttu-id="9d376-169">Ez az információ hasznosnak bizonyulhat, ha a gyakran telefonáló ügyfeleknek online súgócikkekre irányuló hasznos hivatkozásokat és a gyakori kérdések hivatkozását szeretné elküldeni.</span><span class="sxs-lookup"><span data-stu-id="9d376-169">This information might be useful to send an email with helpful links to online help articles and FAQs to customers who called frequently.</span></span>

   > [!NOTE]
   > - <span data-ttu-id="9d376-170">A vetített attribútumok csak olyan entitások esetén működnek, amelyek egy-a-sokhoz kapcsolatban vannak az ügyfélentitással.</span><span class="sxs-lookup"><span data-stu-id="9d376-170">Projected attributes only work for entities that have a one-to-many relationship with the customer entity.</span></span> <span data-ttu-id="9d376-171">Egy ügyfél például több előfizetéssel is rendelkezhet.</span><span class="sxs-lookup"><span data-stu-id="9d376-171">For example, one customer can have multiple subscriptions.</span></span>
   > - <span data-ttu-id="9d376-172">Csak olyan entitásból vetíthető attribútum, amely a készített szegmenslekérdezés minden csoportjában használatos.</span><span class="sxs-lookup"><span data-stu-id="9d376-172">You can only project attributes from an entity that is used in every group of segment query you are building.</span></span>
   > - <span data-ttu-id="9d376-173">A vetített attribútumokat figyelembe veszi a rendszer a beállított operátorok használatakor.</span><span class="sxs-lookup"><span data-stu-id="9d376-173">Projected attributes are factored in when using set operators.</span></span>

1. <span data-ttu-id="9d376-174">Válassza a **Mentés** lehetőséget a szegmens mentéséhez.</span><span class="sxs-lookup"><span data-stu-id="9d376-174">Select **Save** to save your segment.</span></span> <span data-ttu-id="9d376-175">A rendszer menti a szegmenst és feldolgozza, ha az összes követelményt ellenőrizte.</span><span class="sxs-lookup"><span data-stu-id="9d376-175">Your segment will be saved and processed if all requirements are validated.</span></span> <span data-ttu-id="9d376-176">Ellenkező esetben vázlatként menti a program.</span><span class="sxs-lookup"><span data-stu-id="9d376-176">Otherwise, it will be saved as a draft.</span></span>

1. <span data-ttu-id="9d376-177">A **Szegmensek** oldalra a **Vissza a szegmensekhez** elemre kattintva léphet vissza.</span><span class="sxs-lookup"><span data-stu-id="9d376-177">Select **Back to segments** to go back to the **Segments** page.</span></span>



## <a name="quick-segments"></a><span data-ttu-id="9d376-178">Gyors szegmens</span><span class="sxs-lookup"><span data-stu-id="9d376-178">Quick segments</span></span>

<span data-ttu-id="9d376-179">A gyorsszegmensek segítségével gyorsan készíthet egyszerű, egy operátorral rendelkező szegmenseket a gyors elemzéshez.</span><span class="sxs-lookup"><span data-stu-id="9d376-179">Quick segments let you build simple segments with a single operator quickly for faster insights.</span></span>

1. <span data-ttu-id="9d376-180">A **Szegmensek** oldalon válassza az **Új** > **Létrehozás a következőből** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="9d376-180">On the **Segments** page, select **New** > **Create from**.</span></span>

   - <span data-ttu-id="9d376-181">Válassza a **Profilok** lehetőséget, ha az *egyesített ügyfél* entitáson alapuló szegmenset szeretne létrehozni.</span><span class="sxs-lookup"><span data-stu-id="9d376-181">Select the **Profiles** option to build a segment that is based on the *unified customer* entity.</span></span>
   - <span data-ttu-id="9d376-182">Ha korábban létrehozott mértékekhez szeretne szegmenst létrehozni, válassza a **Mértékek** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="9d376-182">Select the **Measures** option to build a segment around  measures you have previously created.</span></span>
   - <span data-ttu-id="9d376-183">Válassza az **Információ** lehetőséget, ha egy szegmenst szeretne létrehozni az egyik olyan kimeneti entitás köré, amelyet vagy az **Előrejelzések** vagy az **egyéni modellek** használatával hozott létre.</span><span class="sxs-lookup"><span data-stu-id="9d376-183">Select the **Intelligence** option to build a segment around one of the output entities you generated using either the **Predictions** or **Custom Models** capabilities.</span></span>

2. <span data-ttu-id="9d376-184">Az **új gyors szegmens** párbeszédpanelen jelöljön ki egy attribútumot a **Mező** legördülő listában.</span><span class="sxs-lookup"><span data-stu-id="9d376-184">In the **New quick segment** dialog box, select an attribute from the **Field** dropdown.</span></span>

3. <span data-ttu-id="9d376-185">A rendszer néhány további betekintést biztosít, amelyek segítségével jobb szegmenseket hozhat létre az ügyfelek számára.</span><span class="sxs-lookup"><span data-stu-id="9d376-185">The system will provide some additional insights that help you create better segments of your customers.</span></span>
   - <span data-ttu-id="9d376-186">A kategorikus mezők esetén 10 első számú ügyfél számít.</span><span class="sxs-lookup"><span data-stu-id="9d376-186">For categorical fields, we'll show 10 top customer counts.</span></span> <span data-ttu-id="9d376-187">Válasszon egy **Értéket**, és válassza a **Felülvizsgálat** elemet.</span><span class="sxs-lookup"><span data-stu-id="9d376-187">Choose a **Value** and select **Review**.</span></span>

   - <span data-ttu-id="9d376-188">Numerikus attribútumok esetében a rendszer azt mutatja, hogy az egyes ügyfelek percentilis értékei alá milyen attribútumértékek tartoznak.</span><span class="sxs-lookup"><span data-stu-id="9d376-188">For a numerical attribute, the system will show what attribute value falls under each customer's percentile.</span></span> <span data-ttu-id="9d376-189">Válasszon egy **operátort** és egy **értéket**, majd válassza a **Felülvizsgálat** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="9d376-189">Choose an **Operator** and a **Value**, then select **Review**.</span></span>

4. <span data-ttu-id="9d376-190">A rendszer megadja a **Becsült szegmensméret** értékét.</span><span class="sxs-lookup"><span data-stu-id="9d376-190">The system will provide you with an **Estimated segment size**.</span></span> <span data-ttu-id="9d376-191">Kiválaszthatja, hogy létrehozza-e a megadott szegmenst, vagy először újra meg szeretné vizsgálni, hogy egy másik szegmens méretet kap-e.</span><span class="sxs-lookup"><span data-stu-id="9d376-191">You can choose whether to generate the segment you've defined, or first revisit it to get a different segment size.</span></span>

    > [!div class="mx-imgBorder"]
    > <span data-ttu-id="9d376-192">![Gyorsszegmens neve és becslése](media/quick-segment-name.png "Gyorsszegmens neve és becslése")</span><span class="sxs-lookup"><span data-stu-id="9d376-192">![Name and estimation for a quick segment](media/quick-segment-name.png "Name and estimation for a quick segment")</span></span>

5. <span data-ttu-id="9d376-193">Adjon meg egy **Név** értéket a szegmens számára.</span><span class="sxs-lookup"><span data-stu-id="9d376-193">Provide a **Name** for your segment.</span></span> <span data-ttu-id="9d376-194">Másik lehetőségként adjon meg **Megjelenítendő nevet**.</span><span class="sxs-lookup"><span data-stu-id="9d376-194">Optionally, provide a **Display name**.</span></span>

6. <span data-ttu-id="9d376-195">Válassza a **Mentés** lehetőséget a szegmens létrehozásához.</span><span class="sxs-lookup"><span data-stu-id="9d376-195">Select **Save** to create your segment.</span></span>

7. <span data-ttu-id="9d376-196">Miután a szegmens befejezte a feldolgozást, megtekintheti azt a létrehozott többi szegmenshez hasonlóan.</span><span class="sxs-lookup"><span data-stu-id="9d376-196">After the segment has finished processing, you can view it like any other segment you've created.</span></span>

## <a name="next-steps"></a><span data-ttu-id="9d376-197">További lépések</span><span class="sxs-lookup"><span data-stu-id="9d376-197">Next steps</span></span>

<span data-ttu-id="9d376-198">[Exportáljon egy szegmenst](export-destinations.md), és fedezze fel az [Ügyfélkártya](customer-card-add-in.md) és [Összekötők](export-power-bi.md) elemeket, az ügyfélszintű információkhoz.</span><span class="sxs-lookup"><span data-stu-id="9d376-198">[Export a segment](export-destinations.md) and explore the [Customer Card](customer-card-add-in.md) and [Connectors](export-power-bi.md) to get insights on the customer level.</span></span>

[!INCLUDE[footer-include](../includes/footer-banner.md)]
