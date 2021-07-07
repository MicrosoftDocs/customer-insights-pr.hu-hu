---
title: Ügyfélprofilok megtekintése
description: Az egyesített ügyféladatok kombinált nézetének lekérése.
ms.date: 12/01/2020
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: NimrodMagen
ms.author: nimagen
manager: shellyha
ms.openlocfilehash: c9adb4d7db74573d0512ae7a68a0e7ab51c994a0
ms.sourcegitcommit: d84d664e67f263bfeb741154d309088c5101b9c3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/24/2021
ms.locfileid: "6304607"
---
# <a name="customer-profiles"></a><span data-ttu-id="e1129-103">Ügyfélprofilok</span><span class="sxs-lookup"><span data-stu-id="e1129-103">Customer profiles</span></span>

<span data-ttu-id="e1129-104">Az **Ügyfelek** lap az [összes adatforrásból](data-sources.md) összegyűjtött profiladatok alapján jeleníti meg az ügyfelek kombinált nézetét .</span><span class="sxs-lookup"><span data-stu-id="e1129-104">The **Customers** page shows a combined view of your customers, based on profile data gathered from [all data sources](data-sources.md).</span></span> <span data-ttu-id="e1129-105">Az ügyfelek profiljai csak az [egyesített ügyfél entitáslétrehozása](data-unification.md) után érhetők el.</span><span class="sxs-lookup"><span data-stu-id="e1129-105">Customer profiles are available once you [create the unified Customer entity](data-unification.md).</span></span> <span data-ttu-id="e1129-106">Ügyeljen arra, hogy az adatok egyesítésének folyamatát végrehajtsa, hogy bővített nézetet kapjon az ügyfelekről.</span><span class="sxs-lookup"><span data-stu-id="e1129-106">Make sure you complete the data unification process to get richer views of your customers.</span></span> <span data-ttu-id="e1129-107">Az oldal segítségével megkeresheti az ügyfeleket is.</span><span class="sxs-lookup"><span data-stu-id="e1129-107">The page also lets you search for customers.</span></span>

<span data-ttu-id="e1129-108">Az ügyfelek lehetnek egyének vagy szervezetek (előzetes verzió).</span><span class="sxs-lookup"><span data-stu-id="e1129-108">Customers can be individuals or organizations (preview).</span></span> <span data-ttu-id="e1129-109">Minden egyes ügyfél- vagy szervezeti profilt egy csempe képvisel.</span><span class="sxs-lookup"><span data-stu-id="e1129-109">Each customer or organization profile is represented by a tile.</span></span> <span data-ttu-id="e1129-110">A csempét kiválasztva megtekintheti az adott ügyfélre vagy szervezetre vonatkozó további információkat.</span><span class="sxs-lookup"><span data-stu-id="e1129-110">Select a tile to see additional information on that specific customer or organization.</span></span> <span data-ttu-id="e1129-111">További rekordok megtekintéséhez használja a lap alján található oldalszámozási vezérlőket.</span><span class="sxs-lookup"><span data-stu-id="e1129-111">Use the pagination controls at the bottom of the page to see additional records.</span></span>

> [!div class="mx-imgBorder"] 
> <span data-ttu-id="e1129-112">![B2C ügyfélprofilok](media/profiles-customers.png "B2C ügyfélprofilok")</span><span class="sxs-lookup"><span data-stu-id="e1129-112">![B2C customer profiles](media/profiles-customers.png "B2C customer profiles")</span></span>

<span data-ttu-id="e1129-113">Szervezetek (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="e1129-113">Organizations (Preview)</span></span>
> [!div class="mx-imgBorder"] 
> <span data-ttu-id="e1129-114">![B2B ügyfélprofilok](media/profile-customers-b2b.png "B2B ügyfélprofilok")</span><span class="sxs-lookup"><span data-stu-id="e1129-114">![B2B customer profiles](media/profile-customers-b2b.png "B2B customer profiles")</span></span>

> [!NOTE]
> <span data-ttu-id="e1129-115">Ha nem látja a csempéket, amikor a navigációban kiválasztja az **Ügyfelek** elemet, a rendszergazdának [legalább egy kereshető attribútumot meg kell adnia](search-filter-index.md) a **Keresési és szűrőindex** pontban.</span><span class="sxs-lookup"><span data-stu-id="e1129-115">If you can't see the tiles when you select **Customers** in navigation, your administrator needs to [define at least one searchable attribute](search-filter-index.md) on the **Search & filter index**.</span></span>

## <a name="search-for-customers"></a><span data-ttu-id="e1129-116">Ügyfelek keresése</span><span class="sxs-lookup"><span data-stu-id="e1129-116">Search for customers</span></span>

<span data-ttu-id="e1129-117">Az ügyfelek megkereséséhez írja be a nevet vagy más attribútumot a keresőmezőbe.</span><span class="sxs-lookup"><span data-stu-id="e1129-117">Search for customers by entering a name or some other attribute in the search box.</span></span> <span data-ttu-id="e1129-118">A keresés csak az adategyesítési folyamat során létrehozott ügyfélprofil entitáson belül működik.</span><span class="sxs-lookup"><span data-stu-id="e1129-118">The search only works within the Customer Profile entity created during the data unification process.</span></span>

<span data-ttu-id="e1129-119">Rendszergazdaként a kereshető attribútumokat a **keresési & szűrő indexe** oldalon adhatja meg.</span><span class="sxs-lookup"><span data-stu-id="e1129-119">As an admin, you can configure the searchable attributes using the **Search & filter index** page.</span></span> <span data-ttu-id="e1129-120">További tudnivalókért lásd: [A keresési és szűrési index kezelése](search-filter-index.md).</span><span class="sxs-lookup"><span data-stu-id="e1129-120">For more information, see [Manage search & filter index](search-filter-index.md).</span></span>

## <a name="filter-customers"></a><span data-ttu-id="e1129-121">Ügyfelek szűrése</span><span class="sxs-lookup"><span data-stu-id="e1129-121">Filter customers</span></span>

<span data-ttu-id="e1129-122">Az ügyfelek az ügyfélprofil entitás mezői alapján szűrhetők.</span><span class="sxs-lookup"><span data-stu-id="e1129-122">You can filter customers by the Customer Profile entity fields.</span></span> <span data-ttu-id="e1129-123">A kereséshez hasonlóan az adminisztrátornak először meg kell határoznia a mezőket kereshetőként a **keresési & szűrő index** oldal használatával.</span><span class="sxs-lookup"><span data-stu-id="e1129-123">Similar to search, your admin will first need to define the fields as filterable using the **Search & filter index** page.</span></span>

1. <span data-ttu-id="e1129-124">Válassza a **Szűrő** lehetőséget az **Ügyfelek** oldalon.</span><span class="sxs-lookup"><span data-stu-id="e1129-124">Select **Filter** on the **Customers** page.</span></span>

2. <span data-ttu-id="e1129-125">Jelölje be a jelölőnégyzetet azon attribútumok mellett, amelyek alapján az ügyfeleket szűrni szeretné.</span><span class="sxs-lookup"><span data-stu-id="e1129-125">Check the boxes next to the attributes you want to filter customers by.</span></span>

   > [!div class="mx-imgBorder"] 
   > <span data-ttu-id="e1129-126">![Ügyfélprofilok](media/profiles-customers3.png "Ügyfélprofilok")</span><span class="sxs-lookup"><span data-stu-id="e1129-126">![Customer profiles](media/profiles-customers3.png "Customer profiles")</span></span>

3. <span data-ttu-id="e1129-127">Távolítsa el a szűrőket a **Szűrők törlése** lehetőséggel az **Ügyfelek** oldalon.</span><span class="sxs-lookup"><span data-stu-id="e1129-127">Remove your filters by selecting **Clear filters** on the **Customers** page.</span></span>

##  <a name="customer-details-page"></a><span data-ttu-id="e1129-128">Ügyféladatok oldal</span><span class="sxs-lookup"><span data-stu-id="e1129-128">Customer details page</span></span>

<span data-ttu-id="e1129-129">Az **Ügyféladatok oldal** megnyitásához válassza ki bármelyik ügyfélcsempét.</span><span class="sxs-lookup"><span data-stu-id="e1129-129">Select any of the customer tiles to open the **Customer details page**.</span></span> <span data-ttu-id="e1129-130">Ez a nézet a kijelölt ügyfélre vonatkozóan egységesített információkat tartalmaz.</span><span class="sxs-lookup"><span data-stu-id="e1129-130">This view contains unified information for the selected customer.</span></span>

<span data-ttu-id="e1129-131">Az ügyféladatok a következőket tartalmazza:</span><span class="sxs-lookup"><span data-stu-id="e1129-131">Customer details include:</span></span>

-   <span data-ttu-id="e1129-132">**Ügyfélprofil csempe:** Ez a csempe megjeleníti az egyesített ügyfélprofil entitás különböző értékeit.</span><span class="sxs-lookup"><span data-stu-id="e1129-132">**Customer profile tile**: This tile shows the different values from the unified customer profile entity.</span></span> <span data-ttu-id="e1129-133">Az adatok között szerepelhet az e-mail-cím, a név, a város stb.</span><span class="sxs-lookup"><span data-stu-id="e1129-133">These details can include email address, name, city, and so on.</span></span> 

-   <span data-ttu-id="e1129-134">**Lehetséges érdeklődési körök, lehetséges márkák**: Azt mutatja, hogy konfigurált-e elsődleges bővítést.</span><span class="sxs-lookup"><span data-stu-id="e1129-134">**Potential interests, potential brands**: Shows if you configured a first-party enrichment.</span></span> <span data-ttu-id="e1129-135">Lehetséges érdeklődési köröket és márkahűségeket jelent egy olyan ügyfélre vonatkozóan, akinek a profilja hasonló lehet ehhez az ügyfélhez.</span><span class="sxs-lookup"><span data-stu-id="e1129-135">It represents potential interests and affinities for brands a customer with a profile similar to this customer might have.</span></span> <span data-ttu-id="e1129-136">További információkért lásd: [Ügyfélprofilok bővítése márka- és érdeklődésikör-hűséggel](enrichment-microsoft.md).</span><span class="sxs-lookup"><span data-stu-id="e1129-136">For more information, see [Enrich customer profiles with brand and interest affinities](enrichment-microsoft.md).</span></span>

-   <span data-ttu-id="e1129-137">**Mérőszámok**: Azt mutatja, hogy adott típus egy vagy több mérőszáma konfigurált-e: az ügyfél attribútumára vonatkozó mérőszámok.</span><span class="sxs-lookup"><span data-stu-id="e1129-137">**Measures**: Shows if you configured one or more measures of a specific type: customer attribute measures.</span></span> <span data-ttu-id="e1129-138">Magukban foglalják az egyéni ügyfelek szintjén az ügyfelekhez számított fő teljesítménymutatókat.</span><span class="sxs-lookup"><span data-stu-id="e1129-138">They include calculated KPIs around your customers on the individual customer level.</span></span> <span data-ttu-id="e1129-139">További információ: [Mérőszámok meghatározása és kezelése](measures.md).</span><span class="sxs-lookup"><span data-stu-id="e1129-139">For more information, see [Define and manage measures](measures.md).</span></span>

-   <span data-ttu-id="e1129-140">**Tevékenység idősora**: Azt mutatja, hogy van-e konfigurált tevékenysége.</span><span class="sxs-lookup"><span data-stu-id="e1129-140">**Activity timeline**: Shows if you have configured activities.</span></span> <span data-ttu-id="e1129-141">Az Idősornézet az ügyfél időrendben rendezett tevékenységeit tartalmazza, a legutóbbi tevékenységtől kezdve.</span><span class="sxs-lookup"><span data-stu-id="e1129-141">The timeline view contains chronologically sorted activities of this customer, starting with the most recent activity.</span></span> <span data-ttu-id="e1129-142">További információ: [Ügyféltevékenységek](activities.md).</span><span class="sxs-lookup"><span data-stu-id="e1129-142">For more information, see [Customer activities](activities.md).</span></span>

<span data-ttu-id="e1129-143">A **Visszatérés az Ügyfelekhez** lehetőséggel visszatérhet az ügyfelek keresési oldalára.</span><span class="sxs-lookup"><span data-stu-id="e1129-143">Select **Back to Customers** to return to the customer search page.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e1129-144">Következő lépések</span><span class="sxs-lookup"><span data-stu-id="e1129-144">Next steps</span></span>

<span data-ttu-id="e1129-145">[További adatforrások hozzáadása](data-sources.md) vagy az [ügyfelek szegmensének létrehozása](segments.md).</span><span class="sxs-lookup"><span data-stu-id="e1129-145">[Add more data sources](data-sources.md) or [create customer segments](segments.md).</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]
