---
title: Entitások leképezése az adategyesítésben
description: Adatok leképezése az egyesített ügyfélprofilok létrehozásához.
ms.date: 09/25/2020
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: tutorial
author: adkuppa
ms.author: adkuppa
ms.reviewer: mhart
manager: shellyha
ms.openlocfilehash: 36b7f7b2fac9497245cf6759506c53753972f173
ms.sourcegitcommit: bae40184312ab27b95c140a044875c2daea37951
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/15/2021
ms.locfileid: "5595996"
---
# <a name="map-entities-and-attributes"></a><span data-ttu-id="911ca-103">Entitások és attribútumok leképezése</span><span class="sxs-lookup"><span data-stu-id="911ca-103">Map entities and attributes</span></span>

<span data-ttu-id="911ca-104">A **Leképezés** az adategyesítési folyamat első fázisa a célközönség-információknál.</span><span class="sxs-lookup"><span data-stu-id="911ca-104">**Map** is the first stage in the data unification process of audience insights.</span></span> <span data-ttu-id="911ca-105">A leképezés három fázisból áll:</span><span class="sxs-lookup"><span data-stu-id="911ca-105">Mapping consists of three phases:</span></span>

- <span data-ttu-id="911ca-106">*Entitás kiválasztása*: Azonosítsa azokat az kombinálható-entitásokat, amelyek egy adatkészlethez vezetnek, amely az ügyfelekkel kapcsolatos bővebb információkat tartalmaznak.</span><span class="sxs-lookup"><span data-stu-id="911ca-106">*Entity selection*: Identify the combinable entities that lead to a dataset with more complete information about your customers.</span></span>
- <span data-ttu-id="911ca-107">*Attribútumok kijelölése*: Az egyes entitások esetében azonosítsa az összekapcsolni és összeegyeztetni kívánt oszlopokat a *egyeztetési* és *egyesítési* fázisokban.</span><span class="sxs-lookup"><span data-stu-id="911ca-107">*Attribute selection*: For each entity, identify the columns you want to combine and reconcile in the *match* and *merge* phases.</span></span> <span data-ttu-id="911ca-108">Ezeket az oszlopokat *Attribútumoknak* nevezik.</span><span class="sxs-lookup"><span data-stu-id="911ca-108">These columns are called *Attributes*.</span></span>
- <span data-ttu-id="911ca-109">*Elsődleges kulcs és szemantikai típus kijelölése*: Minden egyes entitásnál azonosítson egy attribútumot, amelyet az adott entitás elsődleges kulcsaként szeretne definiálni, és minden attribútumnál azonosítson egy olyan szemantikai típust, amely a legjobban leírja az adott attribútumot.</span><span class="sxs-lookup"><span data-stu-id="911ca-109">*Primary key and semantic type selection*: For each entity, identify an attribute you want to define as the primary key for that entity, and for each attribute, identify a semantic type that best describes that attribute.</span></span>

<span data-ttu-id="911ca-110">Az Adategyesítés általános folyamatáról az [Egységesítés](data-unification.md) című rész tartalmaz további tudnivalókat.</span><span class="sxs-lookup"><span data-stu-id="911ca-110">For more information about the general flow of data unification, see [Unify](data-unification.md).</span></span>

## <a name="select-the-first-entities"></a><span data-ttu-id="911ca-111">Jelölje ki az első entitásokat</span><span class="sxs-lookup"><span data-stu-id="911ca-111">Select the first entities</span></span>

1. <span data-ttu-id="911ca-112">A célközönség információin belül nyissa meg a következőt: **Adatok** > **Egyesítés** > **Leképezés**.</span><span class="sxs-lookup"><span data-stu-id="911ca-112">In audience insights, go to **Data** > **Unify** > **Map**.</span></span>

2. <span data-ttu-id="911ca-113">Az **Entitások kiválasztása** lehetőség választásával indítsa el a leképezési fázist.</span><span class="sxs-lookup"><span data-stu-id="911ca-113">Start the map phase by selecting **Select entities**.</span></span>

3. <span data-ttu-id="911ca-114">Válassza ki a használni kívánt entitásokat és attribútumokat az *egyeztetés* és *egyesítés* fázisokban.</span><span class="sxs-lookup"><span data-stu-id="911ca-114">Select the entities and attributes you want to use in the *match* and *merge* phases.</span></span> <span data-ttu-id="911ca-115">A kötelező attribútumokat egyenként is kijelölheti egy entitásból, illetve az összes attribútumot szerepeltetheti egy entitásban, ha bejelöli az **Összes mező belefoglalása** jelölőnégyzetet az entitás szintjén.</span><span class="sxs-lookup"><span data-stu-id="911ca-115">You can select the required attributes individually from an entity or include all attributes from an entity by selecting the **Include all fields** checkbox on the entity level.</span></span> <span data-ttu-id="911ca-116">Javasoljuk, hogy legalább két entitást válasszon az adategyesítési folyamat előnyeinek kiaknázásához.</span><span class="sxs-lookup"><span data-stu-id="911ca-116">We recommend selecting at least two entities to benefit from the data unification process.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="911ca-117">![Példa entitások hozzáadására](media/data-manager-configure-map-add-entities-example.png "Példa entitások hozzáadására")</span><span class="sxs-lookup"><span data-stu-id="911ca-117">![Add entities example](media/data-manager-configure-map-add-entities-example.png "Add entities example")</span></span>

   <span data-ttu-id="911ca-118">Ebben a példában az **eCommerceContacts** és az **loyCustomers** entitásokat adjuk hozzá.</span><span class="sxs-lookup"><span data-stu-id="911ca-118">In this example, we're adding the **eCommerceContacts** and **loyCustomers** entities.</span></span> <span data-ttu-id="911ca-119">Ezen entitások kiválasztásával betekintést nyerhet, hogy mely online üzleti ügyfelek tagjai a törzsvásárlói programnak.</span><span class="sxs-lookup"><span data-stu-id="911ca-119">By choosing these entities, you can derive insights on which of the online business customers are loyalty program members.</span></span>
   
   <span data-ttu-id="911ca-120">A kulcsszavakkal az összes attribútum és entitás közül keresheti ki a leképezni kívánt szükséges attribútumokat.</span><span class="sxs-lookup"><span data-stu-id="911ca-120">You can search on keywords across all attributes and entities to select the required attributes you want to map.</span></span>
   
     > [!div class="mx-imgBorder"]
   > <span data-ttu-id="911ca-121">![Példa keresési mezőkre](media/data-manager-configure-map-search-fields-example.png "Példa keresési mezőkre")</span><span class="sxs-lookup"><span data-stu-id="911ca-121">![Search fields example](media/data-manager-configure-map-search-fields-example.png "Search fields example")</span></span>

4. <span data-ttu-id="911ca-122">Válassza az **Alkalmaz** lehetőséget a kijelölések jóváhagyásához.</span><span class="sxs-lookup"><span data-stu-id="911ca-122">Select **Apply** to confirm your selections.</span></span>

## <a name="select-primary-key-and-semantic-type-for-attributes"></a><span data-ttu-id="911ca-123">Az elsődleges kulcs és a szemantikai típus kiválasztása az attribútumokhoz</span><span class="sxs-lookup"><span data-stu-id="911ca-123">Select primary key and semantic type for attributes</span></span>

<span data-ttu-id="911ca-124">Az entitások kijelölése után a **Leképezés** lap megjeleníti a kijelölt entitásokat az ellenőrzéshez.</span><span class="sxs-lookup"><span data-stu-id="911ca-124">After selecting your entities, the **Map** page lists the selected entities for your review.</span></span> <span data-ttu-id="911ca-125">Határozza meg egy entitás elsődleges kulcsát, és azonosítsa az entitáshoz tartozó attribútumok szemantikai típusát.</span><span class="sxs-lookup"><span data-stu-id="911ca-125">Define the primary key for an entity and identify the semantic type for an attribute in the entity.</span></span>

- <span data-ttu-id="911ca-126">**Elsődleges kulcs**:Az egyes entitások esetében jelöljön ki egy attribútumot elsődleges kulcsként.</span><span class="sxs-lookup"><span data-stu-id="911ca-126">**Primary key**: Select one attribute as a primary key for each of your entities.</span></span> <span data-ttu-id="911ca-127">Ahhoz, hogy egy attribútum érvényes elsődleges kulcs legyen, az ne tartalmazzon ismétlődő értékeket, a hiányzó értékeket vagy a null értékeket.</span><span class="sxs-lookup"><span data-stu-id="911ca-127">For an attribute to be a valid primary key, it shouldn't include duplicate values, missing values, or null values.</span></span> <span data-ttu-id="911ca-128">A karakterlánc, egész szám és a GUID-adattípus attribútumait elsődleges kulcsként támogatja a rendszer, és megjelenik abban a mezőben, amelyből választhat.</span><span class="sxs-lookup"><span data-stu-id="911ca-128">String, integer, and GUID data type attributes are supported as primary keys and will be displayed in a field for you to select from.</span></span>

- <span data-ttu-id="911ca-129">**Attribútum szemantikai típusa**: Az attribútumai kategóriái, például e-mail cím vagy név.</span><span class="sxs-lookup"><span data-stu-id="911ca-129">**Attribute semantic type**: Categories of your attributes, such as email address or name.</span></span> <span data-ttu-id="911ca-130">Ha AI modelleket szeretne használni a szemantika intelligens előrejelzéséhoz, időt takaríthat meg, és javíthatja a pontosságot, beállíthatja az **intelligens leképezés** értékét **BE** értékre.</span><span class="sxs-lookup"><span data-stu-id="911ca-130">To use AI models for smart prediction of semantics, save time and improve accuracy, set **Intelligent mapping** to **ON**.</span></span> <span data-ttu-id="911ca-131">Az intelligens leképezés kiemeli az AI-alapú szemantikai ajánlást a **típus** mezőben.</span><span class="sxs-lookup"><span data-stu-id="911ca-131">Intelligent mapping highlights AI-based semantics recommendation in the **Type** field.</span></span> <span data-ttu-id="911ca-132">Ha a beállítás értéke **KI**, akkor rendszeres leképezési javaslatokat lát majd.</span><span class="sxs-lookup"><span data-stu-id="911ca-132">If you set it to **OFF**, you will see our regular mapping recommendations.</span></span> <span data-ttu-id="911ca-133">A választható lehetőségek listájából tetszőleges szemantikai típust választhat, és felülbírálhatja a javasolt kijelölést.</span><span class="sxs-lookup"><span data-stu-id="911ca-133">You can select any semantic type from the available list of options and override the suggested selection.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="911ca-134">![az attribútum típusa és a szemantikai előrejelzés](media/data-manager-configure-map-add-attributes-semantic-prediction.png "Az attribútum típusa és a szemantikai előrejelzés")</span><span class="sxs-lookup"><span data-stu-id="911ca-134">![Attribute type and semantic prediction](media/data-manager-configure-map-add-attributes-semantic-prediction.png "Attribute type and semantic prediction")</span></span>

<span data-ttu-id="911ca-135">Az egyéni szemantikus típus hozzáadása is lehetséges.</span><span class="sxs-lookup"><span data-stu-id="911ca-135">Adding a custom semantic type is also possible.</span></span> <span data-ttu-id="911ca-136">Válassza ki egy attribútum típus mezőjét, majd írja be a szemantikus attribútum-típus nevét.</span><span class="sxs-lookup"><span data-stu-id="911ca-136">Select the type field for an attribute, and type your custom semantic type name.</span></span> <span data-ttu-id="911ca-137">Így a rendszer által automatikusan azonosított attribútum-típusokat is módosíthatja.</span><span class="sxs-lookup"><span data-stu-id="911ca-137">This way, you can also change the attribute types that were identified by the system.</span></span>

<span data-ttu-id="911ca-138">Minden attribútum, amelyhez a rendszer automatikusan azonosít egy szemantikai típust a **Leképezett mezők áttekintése** szakaszban van csoportosítva.</span><span class="sxs-lookup"><span data-stu-id="911ca-138">All attributes for which a semantic type is automatically identified are grouped in the **Review mapped fields** section.</span></span> <span data-ttu-id="911ca-139">Tekintse át ezeket az attribútumokat és a szemantikai típusokat, mivel ezek lesznek az adategyesítési lépésben az entitások egyesítésére használva.</span><span class="sxs-lookup"><span data-stu-id="911ca-139">Review these attributes and their semantic types because they'll be used to combine your entities in the merge step of data unification.</span></span>

<span data-ttu-id="911ca-140">A szemantikai típusokhoz automatikusan nem leképezett attribútumok az **Adatok definiálása a nem leképezett mezőkben** szakaszban vannak összegyűjtve.</span><span class="sxs-lookup"><span data-stu-id="911ca-140">Attributes that aren't automatically mapped to a semantic type are grouped in the **Define the data in the unmapped fields** section.</span></span> <span data-ttu-id="911ca-141">Jelölje ki a nem leképezett attribútumok szemantikai típus mezőjét, vagy írja be az egyéni attribútumtípus nevét.</span><span class="sxs-lookup"><span data-stu-id="911ca-141">Select the semantic type field for the unmapped attributes, or enter your custom attribute-type name.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="911ca-142">![Elsődleges kulcs és attribútum típusa](media/data-manager-configure-map-add-attributes.png "Elsődleges kulcs és attribútum típusa")</span><span class="sxs-lookup"><span data-stu-id="911ca-142">![Primary key and attribute type](media/data-manager-configure-map-add-attributes.png "Primary key and attribute type")</span></span>

> [!NOTE]
> <span data-ttu-id="911ca-143">Egy mezőnek a szemantika Person.FullName típushoz kell lennie leképezve, hogy fel legyen töltve az ügyfél neve az ügyfélkártyában.</span><span class="sxs-lookup"><span data-stu-id="911ca-143">One field should map to the semantic type Person.FullName to populate the customer name in customer card.</span></span> <span data-ttu-id="911ca-144">Ellenkező esetben az ügyfélkártyák neve nem lesz látható.</span><span class="sxs-lookup"><span data-stu-id="911ca-144">Otherwise, the customer cards will appear nameless.</span></span> 

## <a name="add-and-remove-attributes-and-entities"></a><span data-ttu-id="911ca-145">Attribútumok és entitások hozzáadása és eltávolítása</span><span class="sxs-lookup"><span data-stu-id="911ca-145">Add and remove attributes and entities</span></span>

1. <span data-ttu-id="911ca-146">Az **Egyesítés** > **Leképezés** alatt válassza a **Mezők szerkesztése** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="911ca-146">On **Unify** > **Map**, select **Edit fields**.</span></span>

2. <span data-ttu-id="911ca-147">Adja hozzá vagy távolítsa el az attribútumokat és entitásokat a **Mezők szerkesztése** ablaktáblában.</span><span class="sxs-lookup"><span data-stu-id="911ca-147">In the **Edit fields** pane, add or remove attributes and entities.</span></span> <span data-ttu-id="911ca-148">A keresés vagy a görgetés segítségével keresse meg és jelölje ki az érintett attribútumokat és entitásokat.</span><span class="sxs-lookup"><span data-stu-id="911ca-148">Use the search or scroll to find and select your attributes and entities of interest.</span></span> <span data-ttu-id="911ca-149">Az attribútumok és entitások nem távolíthatók el, ha már egyeztetve lettek.</span><span class="sxs-lookup"><span data-stu-id="911ca-149">You can't remove an attribute or an entity if they've already been matched.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="911ca-150">![Entitások hozzáadása vagy eltávolítása](media/configure-data-map-edit.png "Entitások hozzáadása vagy eltávolítása")</span><span class="sxs-lookup"><span data-stu-id="911ca-150">![Add or remove attributes](media/configure-data-map-edit.png "Add or remove attributes")</span></span>

3. <span data-ttu-id="911ca-151">Válassza az **Alkalmaz** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="911ca-151">Select **Apply**.</span></span>

## <a name="add-images-to-profiles"></a><span data-ttu-id="911ca-152">Képek hozzáadása profilokhoz</span><span class="sxs-lookup"><span data-stu-id="911ca-152">Add images to profiles</span></span>

<span data-ttu-id="911ca-153">Ha egy entitás a nyilvánosan elérhető profilhoz tartozó képekhez vagy emblémához URL-címeket tartalmaz, azokat felveheti az egyesített felhasználói profilba.</span><span class="sxs-lookup"><span data-stu-id="911ca-153">If an entity contains URLs to publicly available profile images or logos, you can add them to the unified customer profile.</span></span>

<span data-ttu-id="911ca-154">Jelölje ki az entitást, és keresse meg azt a mezőt, amely a profilkép URL-címét tartalmazza.</span><span class="sxs-lookup"><span data-stu-id="911ca-154">Select the entity and find the field that contains the URL to the profile image.</span></span> <span data-ttu-id="911ca-155">A **Típus** beviteli mezőben adja meg manuálisan a következő értéket:</span><span class="sxs-lookup"><span data-stu-id="911ca-155">In the **Type** input field, manually enter the following value:</span></span> 
- <span data-ttu-id="911ca-156">Személy számára: Person.ProfileImage</span><span class="sxs-lookup"><span data-stu-id="911ca-156">For a person: Person.ProfileImage</span></span>
- <span data-ttu-id="911ca-157">Szervezet esetén: Organization.LogoImage</span><span class="sxs-lookup"><span data-stu-id="911ca-157">For an organization: Organization.LogoImage</span></span>

<span data-ttu-id="911ca-158">Folytassa az egyesítési lépéseket, és gondoskodjon róla, hogy a kép URL-címét tartalmazó attribútumot is hozzáadja az [Egyesítés](merge-entities.md) lépéshez.</span><span class="sxs-lookup"><span data-stu-id="911ca-158">Continue with the unification steps and ensure the attribute that contains the image URL is also added in the [Merge](merge-entities.md) step.</span></span>

## <a name="set-attributes-for-organizations"></a><span data-ttu-id="911ca-159">Attribútumok beállítása szervezetekhez</span><span class="sxs-lookup"><span data-stu-id="911ca-159">Set attributes for organizations</span></span>

<span data-ttu-id="911ca-160">A szervezetek (előnézet) esetében az attribútum típusát le kell képezni az "Organization.Name" értékhez</span><span class="sxs-lookup"><span data-stu-id="911ca-160">For organizations (Preview), the attribute type should be mapped to "Organization.Name"</span></span>
> [!div class="mx-imgBorder"]
> <span data-ttu-id="911ca-161">![Elsődleges kulcs és attribútum B2B](media/configure-data-map-edit-b2b.png "Elsődleges kulcs és attribútum B2B")</span><span class="sxs-lookup"><span data-stu-id="911ca-161">![Primary key and attribute type B2B](media/configure-data-map-edit-b2b.png "Primary key and attribute type B2B")</span></span>

## <a name="next-step"></a><span data-ttu-id="911ca-162">Következő lépés</span><span class="sxs-lookup"><span data-stu-id="911ca-162">Next step</span></span>

<span data-ttu-id="911ca-163">Az adategyesítési folyamat részeként nyissa meg az **Egyeztetés** oldalt.</span><span class="sxs-lookup"><span data-stu-id="911ca-163">As part of the data unification process, go to the **Match** page.</span></span> <span data-ttu-id="911ca-164">Tekintse meg az [**Egyeztetés**](match-entities.md) szakaszt, ha többet szeretne megtudni erről a fázisról.</span><span class="sxs-lookup"><span data-stu-id="911ca-164">Visit [**Match**](match-entities.md) to learn about this phase.</span></span>

> [!TIP]
> <span data-ttu-id="911ca-165">Tekintse meg a következő videótL [Első lépések: Egyesített ügyfél profillétrehozása](https://youtu.be/oBfGEhucAxs).</span><span class="sxs-lookup"><span data-stu-id="911ca-165">Check out the following video: [Getting Started: Creating a Unified Customer Profile](https://youtu.be/oBfGEhucAxs).</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]