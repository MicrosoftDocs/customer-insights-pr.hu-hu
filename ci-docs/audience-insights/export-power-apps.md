---
title: Power Apps-csatlakozó
description: A Power Apps csatlakoztatása a Power Automate szolgáltatáshoz.
ms.date: 01/19/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: Nils-2m
ms.author: nikeller
manager: shellyha
ms.openlocfilehash: 3fa91553fd50a22ab62b5a2b1e3f13b9483776a8
ms.sourcegitcommit: bae40184312ab27b95c140a044875c2daea37951
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/15/2021
ms.locfileid: "5598158"
---
# <a name="microsoft-power-apps-connector-preview"></a><span data-ttu-id="522f2-103">Microsoft Power Apps összekötő (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="522f2-103">Microsoft Power Apps connector (preview)</span></span>

<span data-ttu-id="522f2-104">Az egyesített ügyfélprofilokat beviheti a személyre szabott alkalmazásokba a Power Apps segítségével.</span><span class="sxs-lookup"><span data-stu-id="522f2-104">Bring unified customer profiles into your personalized apps with Power Apps.</span></span>

## <a name="connect-power-apps-and-dynamics-365-customer-insights"></a><span data-ttu-id="522f2-105">A Power Apps és a Dynamics 365 Customer Insights összekapcsolása</span><span class="sxs-lookup"><span data-stu-id="522f2-105">Connect Power Apps and Dynamics 365 Customer Insights</span></span>

<span data-ttu-id="522f2-106">A Customer Insights az [adatok egyik elérhető forrása a Power Apps szolgáltatásban](/powerapps/maker/canvas-apps/working-with-data-sources).</span><span class="sxs-lookup"><span data-stu-id="522f2-106">Customer Insights is one of the many [available sources for data in Power Apps](/powerapps/maker/canvas-apps/working-with-data-sources).</span></span>

<span data-ttu-id="522f2-107">A Power Apps dokumentációban megismerheti, hogyan [vehet fel adatkapcsolatot egy alkalmazásba](/powerapps/maker/canvas-apps/add-data-connection).</span><span class="sxs-lookup"><span data-stu-id="522f2-107">Refer to the Power Apps documentation to learn how to [add a data connection to an app](/powerapps/maker/canvas-apps/add-data-connection).</span></span> <span data-ttu-id="522f2-108">Ajánlott azt is megvizsgálni, hogy a [Power Apps delegálás használata hogyan kezeli a nagyméretű adatkészleteket vászonalapú alkalmazásokban](/powerapps/maker/canvas-apps/delegation-overview).</span><span class="sxs-lookup"><span data-stu-id="522f2-108">We recommend you also review [how Power Apps uses delegation to handle large datasets in Canvas apps](/powerapps/maker/canvas-apps/delegation-overview).</span></span>

## <a name="available-entities"></a><span data-ttu-id="522f2-109">Elérhető entitások</span><span class="sxs-lookup"><span data-stu-id="522f2-109">Available entities</span></span>

<span data-ttu-id="522f2-110">A Customer Insights adatkapcsolatként való hozzáadása után kiválaszthatja a következő entitásokat a Power Apps szolgáltatásban:</span><span class="sxs-lookup"><span data-stu-id="522f2-110">After adding Customer Insights as a data connection, you can choose the following entities in Power Apps:</span></span>

- <span data-ttu-id="522f2-111">Ügyfél: az [egyesített ügyfélprofil](customer-profiles.md) adatainak használatához.</span><span class="sxs-lookup"><span data-stu-id="522f2-111">Customer: to use data from the [unified customer profile](customer-profiles.md).</span></span>
- <span data-ttu-id="522f2-112">UnifiedActivity: a [tevékenységi idővonal](activities.md) megjelenítése az alkalmazásban.</span><span class="sxs-lookup"><span data-stu-id="522f2-112">UnifiedActivity: to display the [activity timeline](activities.md) on the app.</span></span>

## <a name="limitations"></a><span data-ttu-id="522f2-113">Korlátozások</span><span class="sxs-lookup"><span data-stu-id="522f2-113">Limitations</span></span>

### <a name="retrievable-entities"></a><span data-ttu-id="522f2-114">Lekérhető entitások</span><span class="sxs-lookup"><span data-stu-id="522f2-114">Retrievable entities</span></span>

<span data-ttu-id="522f2-115">Az **Ügyfél**, **UnifiedActivity** és **Szegmensek** entitásokat csak a Power Apps-összekötőn keresztül tudja lekérni.</span><span class="sxs-lookup"><span data-stu-id="522f2-115">You can only retrieve the **Customer**, **UnifiedActivity**, and **Segments** entities through the Power Apps connector.</span></span> <span data-ttu-id="522f2-116">Más entitások láthatók, mert az alapul szolgáló összekötő támogatja azokat eseményindítókkal a Power Automate-szolgáltatásban.</span><span class="sxs-lookup"><span data-stu-id="522f2-116">Other entities are shown because the underlying connector supports them through triggers in Power Automate.</span></span>  

### <a name="delegation"></a><span data-ttu-id="522f2-117">Meghatalmazás</span><span class="sxs-lookup"><span data-stu-id="522f2-117">Delegation</span></span>

<span data-ttu-id="522f2-118">A delegálás az Ügyfél entitáshoz és a UnifiedActivity entitáshoz használható.</span><span class="sxs-lookup"><span data-stu-id="522f2-118">Delegation works for the Customer entity and UnifiedActivity entity.</span></span> 

- <span data-ttu-id="522f2-119">Az **Ügyfél** entitásának delegálása: Az entitás delegálásának használatához a mezőket indexelni kell a [keresési & szűrő indexében](search-filter-index.md).</span><span class="sxs-lookup"><span data-stu-id="522f2-119">Delegation for **Customer** entity: To use delegation for this entity, the fields need to be indexed in [Search & filter index](search-filter-index.md).</span></span>  

- <span data-ttu-id="522f2-120">A **UnifiedActivity** delegálása: A delegálás ehhez az entitáshoz csak az **ActivityId** és a **CusomerId** mező esetében működik.</span><span class="sxs-lookup"><span data-stu-id="522f2-120">Delegation for **UnifiedActivity**: Delegation for this entity only works for the fields **ActivityId** and **CustomerId**.</span></span>  

- <span data-ttu-id="522f2-121">A delegálással kapcsolatban további tudnivalókat a [Power Apps delegálható funkciók és műveletek](/connectors/commondataservice/#power-apps-delegable-functions-and-operations-for-the-cds-for-apps) című rész tartalmaz.</span><span class="sxs-lookup"><span data-stu-id="522f2-121">For more information about delegation, see [Power Apps delegable functions and operations](/connectors/commondataservice/#power-apps-delegable-functions-and-operations-for-the-cds-for-apps).</span></span> 

## <a name="example-gallery-control"></a><span data-ttu-id="522f2-122">Példa a katalógusvezérlőre</span><span class="sxs-lookup"><span data-stu-id="522f2-122">Example gallery control</span></span>

<span data-ttu-id="522f2-123">Az ügyfelek profiljait például egy [galériavezérlőhöz](/powerapps/maker/canvas-apps/add-gallery) adhatja hozzá.</span><span class="sxs-lookup"><span data-stu-id="522f2-123">For example, you add customer profiles to a [gallery control](/powerapps/maker/canvas-apps/add-gallery).</span></span>

1. <span data-ttu-id="522f2-124">Adjon hozzá egy **Katalógus** vezérlőt az épített alkalmazáshoz.</span><span class="sxs-lookup"><span data-stu-id="522f2-124">Add a **Gallery** control to an app you're building.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="522f2-125">![Katalóguselem hozzáadása](media/connector-powerapps9.png "Katalóguselem hozzáadása")</span><span class="sxs-lookup"><span data-stu-id="522f2-125">![Add a gallery element](media/connector-powerapps9.png "Add a gallery element")</span></span>

1. <span data-ttu-id="522f2-126">Válassza az **Ügyfél** elemet az elemek adatforrásaként.</span><span class="sxs-lookup"><span data-stu-id="522f2-126">Select **Customer** as the data source for items.</span></span>

    > [!div class="mx-imgBorder"]
    > <span data-ttu-id="522f2-127">![Adatforrás kijelölése](media/choose-datasource-powerapps.png "Adatforrás kijelölése")</span><span class="sxs-lookup"><span data-stu-id="522f2-127">![Select a data source](media/choose-datasource-powerapps.png "Select a data source")</span></span>

1. <span data-ttu-id="522f2-128">A jobb oldali adatpanelt megváltoztatva megadhatja, hogy az Ügyfél entitásnál melyik mező jelenjen meg a katalógusban.</span><span class="sxs-lookup"><span data-stu-id="522f2-128">You can change the data panel on the right to select which field for the Customer entity to show on the gallery.</span></span>

1. <span data-ttu-id="522f2-129">Ha a kiválasutott ügyfélből a katalóguson bármely mezőt meg szeretné jeleníteni, töltse ki a címke Szöveg tulajdonságát: **{Name_of_the_gallery}.Selected.{property_name}**</span><span class="sxs-lookup"><span data-stu-id="522f2-129">If you want to show any field from the selected customer on the gallery, fill in the Text property of a label:  **{Name_of_the_gallery}.Selected.{property_name}**</span></span>

    <span data-ttu-id="522f2-130">Példa: Gallery1.Selected.address1_city</span><span class="sxs-lookup"><span data-stu-id="522f2-130">Example: Gallery1.Selected.address1_city</span></span>

1. <span data-ttu-id="522f2-131">Ha egy ügyfélnél egyesített idősort szeretne megjeleníteni, adjon hozzá egy Katalógus elemet, és az Elemek tulajdonságot: **Filter('UnifiedActivity', CustomerId = {Customer_Id})**</span><span class="sxs-lookup"><span data-stu-id="522f2-131">To display the unified timeline for a customer, add a Gallery element, and add the Items property: **Filter('UnifiedActivity', CustomerId = {Customer_Id})**</span></span>

    <span data-ttu-id="522f2-132">Példa: Filter('UnifiedActivity', CustomerId = Gallery1.Selected.CustomerId)</span><span class="sxs-lookup"><span data-stu-id="522f2-132">Example: Filter('UnifiedActivity', CustomerId = Gallery1.Selected.CustomerId)</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]