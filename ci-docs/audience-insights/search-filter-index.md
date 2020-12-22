---
title: Ügyfélprofilok keresése és szűrése
description: Gyorsan megtalálhatja az egyesített ügyfelek profiljaira vonatkozó információkat, és szűrhet a megadott attribútumokra.
ms.date: 04/16/2020
ms.reviewer: nimagen
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: 1842ad333c23bb155abc89167556163ae79cdd34
ms.sourcegitcommit: cf9b78559ca189d4c2086a66c879098d56c0377a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/03/2020
ms.locfileid: "4406025"
---
# <a name="customer-profiles-search--filter-index"></a><span data-ttu-id="68646-103">Felhasználói profilok: Keresés & szűrőindex</span><span class="sxs-lookup"><span data-stu-id="68646-103">Customer profiles: Search & filter index</span></span>

<span data-ttu-id="68646-104">Az ügyféladatok egységesítésének eredménye egy Ügyfélprofil entitás, amely egységes nézetet biztosít a teljes ügyfélkörre.</span><span class="sxs-lookup"><span data-stu-id="68646-104">The result of unifying your customer data is a Customer Profile entity that provides a unified view into your total customer base.</span></span> <span data-ttu-id="68646-105">Egy [adott ügyfélre vagy ügyfelek egy csoportjára vonatkozó információk](customer-profiles.md) gyors megkereséséhez konfigurálhatja a **Keresés** és a **Szűrés** lehetőségeket az **Ügyfelek** lapon .</span><span class="sxs-lookup"><span data-stu-id="68646-105">To quickly [find information on a specific customer or group of customers](customer-profiles.md), you can configure the **Search** and **Filter** capabilities on the **Customers** page.</span></span> <span data-ttu-id="68646-106">A cikkből megtudhatja, hogyan szerkeszthetik a rendszergazdák az attribútumokat a **Keresési és szűrési index** lapon, amely a felhasználók számára elérhető a kereséshez és a szűréshez.</span><span class="sxs-lookup"><span data-stu-id="68646-106">Read on to learn how admins can edit the attributes on the **Search & filter index** page, which are available to users for searching and filtering.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="68646-107">![Keresési szűrő](media/search-filter.png "Keresési szűrő")</span><span class="sxs-lookup"><span data-stu-id="68646-107">![Search filter](media/search-filter.png "Search filter")</span></span>

## <a name="add-fields-and-specify-attributes"></a><span data-ttu-id="68646-108">Mezők hozzáadása és attribútumok megadása</span><span class="sxs-lookup"><span data-stu-id="68646-108">Add fields and specify attributes</span></span>

<span data-ttu-id="68646-109">Ha első alkalommal határozza meg a kereshető attribútumokat rendszergazdaként, először meg kell határoznia az indexelt mezőket.</span><span class="sxs-lookup"><span data-stu-id="68646-109">If it's the first time you define searchable attributes as an administrator, you need to define indexed fields first.</span></span> <span data-ttu-id="68646-110">Javasoljuk, hogy az összes attribútumot válassza ki, amely alapján a felhasználók kereshetnek és szűrhetik az ügyfeleket az **Ügyfelek** oldalon.</span><span class="sxs-lookup"><span data-stu-id="68646-110">We suggest you choose all the attributes by which users can search and filter customers on the **Customers** page.</span></span> <span data-ttu-id="68646-111">Csak az adategyesítési folyamat során létrehozott Felhasználói profil entitásban található attribútumokat adhatja meg.</span><span class="sxs-lookup"><span data-stu-id="68646-111">You can only specify attributes that exist in the Customer Profile entity that you created during the data unification process.</span></span>

1. <span data-ttu-id="68646-112">Nyissa meg az **ügyfelek** oldalt, és válassza a **keresési & szűrő indexe** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="68646-112">Open the **Customers** page and select **Search & filter index**.</span></span>

> [!NOTE]
> <span data-ttu-id="68646-113">Létrehozzuk az alapértelmezett keresési index konfigurációt az Ügyfél entitás elérhető attribútumain az alábbi szemantikai típusokból, a Leképezés lapon megadott módon.</span><span class="sxs-lookup"><span data-stu-id="68646-113">We create a default search index configuration on the available attributes in the Customer entity from the following semantic types as defined on the Map page.</span></span>
> - <span data-ttu-id="68646-114">Személy utóneve, Vezetéknév, második utónév, teljes név</span><span class="sxs-lookup"><span data-stu-id="68646-114">Person First name, Last name, Middle name, Full Name</span></span>
> - <span data-ttu-id="68646-115">Szervezet neve</span><span class="sxs-lookup"><span data-stu-id="68646-115">Organization Name</span></span>
> - <span data-ttu-id="68646-116">E-mail cím</span><span class="sxs-lookup"><span data-stu-id="68646-116">Email address</span></span>
> - <span data-ttu-id="68646-117">Telefonszám</span><span class="sxs-lookup"><span data-stu-id="68646-117">Phone number</span></span>
> - <span data-ttu-id="68646-118">Helyadatok</span><span class="sxs-lookup"><span data-stu-id="68646-118">Location information</span></span>

2. <span data-ttu-id="68646-119">Válassza a **+ Hozzáadás** elemet az indexelt mezők meghatározásához.</span><span class="sxs-lookup"><span data-stu-id="68646-119">Select **+ Add** to specify the indexed fields.</span></span>

3. <span data-ttu-id="68646-120">A listában jelölje ki az indexelt mezőkként hozzáadni kívánt attribútumokat.</span><span class="sxs-lookup"><span data-stu-id="68646-120">Select the attributes in the list you want to add as indexed fields.</span></span> <span data-ttu-id="68646-121">A **Hozzáadás** lehetőséggel bármikor hozzáadhat további attribútumokat.</span><span class="sxs-lookup"><span data-stu-id="68646-121">You can always add more attributes by selecting **Add**.</span></span> <span data-ttu-id="68646-122">A kijelölt attribútumokat az **Eltávolítás** szimbólum választásával is eltávolíthatja.</span><span class="sxs-lookup"><span data-stu-id="68646-122">You can also remove any selected attributes by selecting the **Remove** symbol.</span></span>

## <a name="explore-the-indexed-customer-fields-table"></a><span data-ttu-id="68646-123">Az indexelt ügyféladatokat tartalmazó tábla felfedezése</span><span class="sxs-lookup"><span data-stu-id="68646-123">Explore the Indexed customer fields table</span></span>

<span data-ttu-id="68646-124">A következő információk láthatók a táblában.</span><span class="sxs-lookup"><span data-stu-id="68646-124">The following information is presented in the table.</span></span>

- <span data-ttu-id="68646-125">**Név**: Az attribútum nevét jelöli, ahogyan az az Ügyfélprofil entitásában jelenik meg.</span><span class="sxs-lookup"><span data-stu-id="68646-125">**Name**: Represents the attribute's name as it appears in the Customer Profile entity.</span></span>
- <span data-ttu-id="68646-126">**Adattípus**: Azt adja meg, hogy az adattípus karakterlánc, szám vagy dátum-e.</span><span class="sxs-lookup"><span data-stu-id="68646-126">**Data type**: Specifies whether the data type is a string, a number, or a date.</span></span>
- <span data-ttu-id="68646-127">**A keresésben szerepel**: Azt adja meg, hogy az attribútum használható-e az ügyfelek keresésére az **Ügyfelek** oldalon a **Keresés** mező segítségével.</span><span class="sxs-lookup"><span data-stu-id="68646-127">**Included in search**: Specifies whether this attribute can be used for searching customers on the **Customers** page using the **Search** field.</span></span>
- <span data-ttu-id="68646-128">**Szűrő hozzáadása**: Meghatározza, hogy az attribútum hogyan használható szűrésre az **Ügyfelek** lapon.</span><span class="sxs-lookup"><span data-stu-id="68646-128">**Add Filter**: Control to define how this attribute can be used for filtering on the **Customers** page.</span></span>

## <a name="editing-filtering-options-for-a-given-attribute"></a><span data-ttu-id="68646-129">Adott attribútum szűrési beállításainak módosítása</span><span class="sxs-lookup"><span data-stu-id="68646-129">Editing filtering options for a given attribute</span></span>

<span data-ttu-id="68646-130">Az **Ügyfelek** oldalon megjelenő **Szűrő** menüben szerepelhet több attribútumszint (például különböző korcsoportok az ügyfelek szűrése céljából).</span><span class="sxs-lookup"><span data-stu-id="68646-130">The **Filter** menu on the **Customers** page can include a varying number of attribute levels (for example, different age groups to filter customers by).</span></span>

1. <span data-ttu-id="68646-131">Válassza azadott attribútumhoz tartozó **Szűrő hozzáadása** lehetőséget a **Keresési és szűrési index** oldalon.</span><span class="sxs-lookup"><span data-stu-id="68646-131">Select **Add Filter** for a given attribute on the **Search & filter index** page.</span></span> <span data-ttu-id="68646-132">Megadhatja az eredmények számát és a rendezési sorrendet.</span><span class="sxs-lookup"><span data-stu-id="68646-132">You can define the number of results and the order in which they'll be organized.</span></span> <span data-ttu-id="68646-133">Az attribútum adattípusától függően a következő ablaktáblák egyike jelenik meg.</span><span class="sxs-lookup"><span data-stu-id="68646-133">Depending on the attribute's data type, one of the following panes appears.</span></span>

- <span data-ttu-id="68646-134">Karakterlánc típusú attribútumok: Meghatározzák a kívánt eredmények számát a **Karakterlánc szűrőbeállításai** panelen és a rendezési irányelvben, amely alapján rendezve lesznek.</span><span class="sxs-lookup"><span data-stu-id="68646-134">String-type attributes: Specify the number of desired results on the **String filter options** pane and the order policy by which they'll be organized.</span></span>

- <span data-ttu-id="68646-135">Numerikus típusú attribútumok: Meghatározzák a belefoglalt intervallumokat a **Számok szűrőbeállításai** panelen és a rendezési irányelvben, amely alapján rendezve lesznek.</span><span class="sxs-lookup"><span data-stu-id="68646-135">Numerical-type attributes: Specify the intervals included on the **Number filter options** pane and the order policy by which they'll be organized.</span></span>

- <span data-ttu-id="68646-136">Dátum típusú attribútumok: Meghatározzák a belefoglalt intervallumokat a **Dátumszűrő beállításai** panelen és a rendezési irányelvben, amely alapján rendezve lesznek.</span><span class="sxs-lookup"><span data-stu-id="68646-136">Date-type attributes:  Specify the intervals included on the **Date filter options** pane and the order policy by which they'll be organized.</span></span>

2. <span data-ttu-id="68646-137">Válassza a **Mentés** lehetőséget a módosítások alkalmazásához.</span><span class="sxs-lookup"><span data-stu-id="68646-137">Select **Save** to apply your changes.</span></span>

3. <span data-ttu-id="68646-138">Válassza a **Futtatás** lehetőséget, ha már készen áll a beállítások alkalmazására.</span><span class="sxs-lookup"><span data-stu-id="68646-138">Select **Run** once you're ready to apply your settings.</span></span>
