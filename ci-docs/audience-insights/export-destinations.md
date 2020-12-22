---
title: Exportálási célhelyek
description: Adatok exportálása és az exportálási célhelyek kezelése.
ms.date: 07/21/2020
ms.reviewer: philk
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: 9032d99357db86e66588eda544211a5f8eb2f23b
ms.sourcegitcommit: 6a6df62fa12dcb9bd5f5a39cc3ee0e2b3988184b
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/25/2020
ms.locfileid: "4643866"
---
# <a name="export-destinations-preview"></a><span data-ttu-id="381fd-103">Exportálási célhelyek (előzetes)</span><span class="sxs-lookup"><span data-stu-id="381fd-103">Export destinations (preview)</span></span>

<span data-ttu-id="381fd-104">Az **Exportálási célhelyek** lap megjeleníti az összes olyan helyet, amelyet beállított az adatok exportálási céljának.</span><span class="sxs-lookup"><span data-stu-id="381fd-104">The **Export destinations** page shows you all locations you've set up to export data to.</span></span> <span data-ttu-id="381fd-105">Az exportáláshoz új célhelyeket is hozzáadhat.</span><span class="sxs-lookup"><span data-stu-id="381fd-105">You can also add new destinations for export.</span></span> <span data-ttu-id="381fd-106">Emellett a jelenleg elérhető exportálási lehetőségeket is mutatja.</span><span class="sxs-lookup"><span data-stu-id="381fd-106">Additionally, it shows export currently available options.</span></span> <span data-ttu-id="381fd-107">Gyors áttekintést, leírást kaphat, és megtudhatja, mit tehet az egyes bővíthetőség-beállításokkal.</span><span class="sxs-lookup"><span data-stu-id="381fd-107">Get a quick overview, description, and find out what you can do with each extensibility option.</span></span> <span data-ttu-id="381fd-108">Egységesített profilok, intézkedések és szegmensek exportálása a vállalat szempontjából releváns támogatott alkalmazásokhoz.</span><span class="sxs-lookup"><span data-stu-id="381fd-108">Export unified profiles, measures, and segments to supported apps relevant for your business.</span></span>

<span data-ttu-id="381fd-109">Válassza a **Felügyelet** > **Exportálási célhelyek** lehetőséget a következő bővíthetőségi lehetőségek megkereséséhez:</span><span class="sxs-lookup"><span data-stu-id="381fd-109">Go to **Admin** > **Export destinations** to find the following extensibility options:</span></span>

- [<span data-ttu-id="381fd-110">Dynamics 365 Customer Card bővítmény</span><span class="sxs-lookup"><span data-stu-id="381fd-110">Dynamics 365 Customer Card Add-in</span></span>](customer-card-add-in.md)
- [<span data-ttu-id="381fd-111">Facebook Ads Manager összekötő</span><span class="sxs-lookup"><span data-stu-id="381fd-111">Facebook Ads Manager connector</span></span>](export-facebook.md)
- [<span data-ttu-id="381fd-112">Power Automate-csatlakozó</span><span class="sxs-lookup"><span data-stu-id="381fd-112">Power Automate connector</span></span>](export-power-automate.md)
- [<span data-ttu-id="381fd-113">Power Apps-csatlakozó</span><span class="sxs-lookup"><span data-stu-id="381fd-113">Power Apps connector</span></span>](export-power-apps.md)
- [<span data-ttu-id="381fd-114">Power BI-csatlakozó</span><span class="sxs-lookup"><span data-stu-id="381fd-114">Power BI connector</span></span>](export-power-bi.md)
- [<span data-ttu-id="381fd-115">DotDigital</span><span class="sxs-lookup"><span data-stu-id="381fd-115">DotDigital</span></span>](export-dotdigital.md)
- [<span data-ttu-id="381fd-116">Dynamics 365 Sales</span><span class="sxs-lookup"><span data-stu-id="381fd-116">Dynamics 365 Sales</span></span>](export-dynamics365-sales.md)
- [<span data-ttu-id="381fd-117">Dynamics 365 Marketing</span><span class="sxs-lookup"><span data-stu-id="381fd-117">Dynamics 365 Marketing</span></span>](export-dynamics365-marketing.md)
- [<span data-ttu-id="381fd-118">Azure Blob Storage</span><span class="sxs-lookup"><span data-stu-id="381fd-118">Azure Blob Storage</span></span>](export-azure-blob-storage.md)
- [<span data-ttu-id="381fd-119">LiveRamp&reg; összekötő</span><span class="sxs-lookup"><span data-stu-id="381fd-119">LiveRamp&reg; connector</span></span>](export-liveramp.md)
- [<span data-ttu-id="381fd-120">Microsoft Teams robot</span><span class="sxs-lookup"><span data-stu-id="381fd-120">Bot for Microsoft Teams</span></span>](export-teams-bot.md)
- [<span data-ttu-id="381fd-121">Mailchimp</span><span class="sxs-lookup"><span data-stu-id="381fd-121">Mailchimp</span></span>](export-mailchimp.md)
- [<span data-ttu-id="381fd-122">Customer Insights API</span><span class="sxs-lookup"><span data-stu-id="381fd-122">Customer Insights API</span></span>](apis.md)

## <a name="add-a-new-export-destination"></a><span data-ttu-id="381fd-123">Új exportálási cél hozzáadása</span><span class="sxs-lookup"><span data-stu-id="381fd-123">Add a new export destination</span></span>

<span data-ttu-id="381fd-124">Az exportálási célhelyek hozzáadásához [rendszergazdai jogosultságokkal kell rendelkeznie](permissions.md).</span><span class="sxs-lookup"><span data-stu-id="381fd-124">To add export destinations, you have [administrator permissions](permissions.md).</span></span> <span data-ttu-id="381fd-125">Ha Microsoft-szolgáltatásokba exportál, akkor feltételezzük, hogy mindkét szolgáltatás ugyanabban a szervezetben van.</span><span class="sxs-lookup"><span data-stu-id="381fd-125">If you export to Microsoft services, we assume both services are in the same organization.</span></span>

1. <span data-ttu-id="381fd-126">Válassz a **Rendszergazda** > **Célok exportálása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="381fd-126">Go to **Admin** > **Export destinations**.</span></span>

1. <span data-ttu-id="381fd-127">Váltson a **Saját exportálási célhelyek** lapra.</span><span class="sxs-lookup"><span data-stu-id="381fd-127">Switch to the **My export destinations** tab.</span></span>

1. <span data-ttu-id="381fd-128">Válassza a **Célhely hozzáadása** lehetőséget új célhely létrehozásához.</span><span class="sxs-lookup"><span data-stu-id="381fd-128">Select **Add destination** to create a new export destination.</span></span>

1. <span data-ttu-id="381fd-129">A **Célhely hozzáadása** ablaktáblában válassza ki az exportálási cél **Típusát** a legördülő listában.</span><span class="sxs-lookup"><span data-stu-id="381fd-129">In the **Add destination** pane, select the **Type** of export destination in the drop-down.</span></span>

1. <span data-ttu-id="381fd-130">Adja meg a szükséges adatokat, és válassza a **Következő** lehetőséget az exportálási cél létrehozásához.</span><span class="sxs-lookup"><span data-stu-id="381fd-130">Provide the required details and select **Next** to create the export destination.</span></span>

<span data-ttu-id="381fd-131">A **Beállítás** lehetőséget is választhatja egy mozaikon a **Felderítés** lapon.</span><span class="sxs-lookup"><span data-stu-id="381fd-131">You can also select **Set up** on a tile on the **Discover** tab.</span></span>

## <a name="view-export-destinations"></a><span data-ttu-id="381fd-132">Exportálási célhely megtekintése</span><span class="sxs-lookup"><span data-stu-id="381fd-132">View Export destinations</span></span>

<span data-ttu-id="381fd-133">Az exportálási célhelyek létrehozása után ezeket egy táblázatban találja a **Saját exportálási célhelyek** lapon. Ennek a táblának három oszlopa van:</span><span class="sxs-lookup"><span data-stu-id="381fd-133">After creating export destinations, you'll find them in a table on the **My export destinations** tab. This table has three columns:</span></span>

- <span data-ttu-id="381fd-134">**mMegjelenítendő név**: A cél létrehozásakor megadott név.</span><span class="sxs-lookup"><span data-stu-id="381fd-134">**Display name**: The name you entered when creating the destination.</span></span>
- <span data-ttu-id="381fd-135">**Típus**: A cél létrehozásakor beállított exportálási célhely típus.</span><span class="sxs-lookup"><span data-stu-id="381fd-135">**Type**: The export destination type you set when creating the destination.</span></span>
- <span data-ttu-id="381fd-136">**Létrehozva**: A célhely létrehozásának dátuma.</span><span class="sxs-lookup"><span data-stu-id="381fd-136">**Created**: The date you created the destination.</span></span>

## <a name="edit-an-export-destination"></a><span data-ttu-id="381fd-137">Exportálási cél szerkesztése</span><span class="sxs-lookup"><span data-stu-id="381fd-137">Edit an export destination</span></span>

1. <span data-ttu-id="381fd-138">Jelölje ki a szerkeszteni kívánt Exportálási célhely függőleges három pontját.</span><span class="sxs-lookup"><span data-stu-id="381fd-138">Select the vertical ellipsis for the Export destination you want to edit.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="381fd-139">![Függőleges három pont](media/export-destinations-page-ellipsis.png "Függőleges három pont")</span><span class="sxs-lookup"><span data-stu-id="381fd-139">![Vertical ellipsis](media/export-destinations-page-ellipsis.png "Vertical ellipsis")</span></span>

1. <span data-ttu-id="381fd-140">A legördülő menüben kattintson a **Szerkesztés** parancsra.</span><span class="sxs-lookup"><span data-stu-id="381fd-140">Select **Edit** from the dropdown menu.</span></span>

1. <span data-ttu-id="381fd-141">Módosítsa a frissítést igénylő értékeket, és válassza a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="381fd-141">Change the values that require update and select **Save**.</span></span>

## <a name="export-data-on-demand"></a><span data-ttu-id="381fd-142">Adatok igény szerinti exportálása</span><span class="sxs-lookup"><span data-stu-id="381fd-142">Export data on demand</span></span>

<span data-ttu-id="381fd-143">Az exportálási célhely összekötőjének konfigurálása után az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) együtt megtörténik.</span><span class="sxs-lookup"><span data-stu-id="381fd-143">After configuring a connector for an export destination, exports will run with every [scheduled refresh](system.md#schedule-tab).</span></span>

<span data-ttu-id="381fd-144">Ha az adatok exportálását az ütemezett frissítésre való várakozás nélkül szeretné elvégezni, akkor nyissa meg a **Saját exportálási célhelyek** lapot itt: **Rendszergazda** > **Exportálási célhelyek**.</span><span class="sxs-lookup"><span data-stu-id="381fd-144">To export data without waiting for a scheduled refresh, go the **My export destinations** tab on **Admin** > **Export destinations**.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="381fd-145">![Függőleges három pont](media/export-destinations-page-ellipsis.png "Függőleges három pont")</span><span class="sxs-lookup"><span data-stu-id="381fd-145">![Vertical ellipsis](media/export-destinations-page-ellipsis.png "Vertical ellipsis")</span></span>

- <span data-ttu-id="381fd-146">Válassza az **Exportálás** lehetőséget a lista felett, ha az exportálást egyszerre az összes exportálási célhelyre szeretné futtatni.</span><span class="sxs-lookup"><span data-stu-id="381fd-146">Select **Export** above the list to run the export to all export destinations simultaneously.</span></span>
- <span data-ttu-id="381fd-147">Jelölje ki a három pontot (...) egy listaelem után, majd válassza az **Exportálás** lehetőséget az exportálás egyetlen exportálási célhelyre való futtatásához.</span><span class="sxs-lookup"><span data-stu-id="381fd-147">Select the ellipsis (...) after a list item and then choose the **Export** option to run the export for a single export destination.</span></span>

## <a name="remove-an-export-destination"></a><span data-ttu-id="381fd-148">Exportálási cél eltávolítása</span><span class="sxs-lookup"><span data-stu-id="381fd-148">Remove an Export destination</span></span>

<span data-ttu-id="381fd-149">Az exportálási célhely eltávolításához induljon a fő **Exportálási célhelyek** oldalról.</span><span class="sxs-lookup"><span data-stu-id="381fd-149">To remove an Export destination, start from the main **Export destinations** page.</span></span>

1. <span data-ttu-id="381fd-150">Jelölje ki az eltávolítani kívánt Exportálási célhely függőleges három pontját.</span><span class="sxs-lookup"><span data-stu-id="381fd-150">Select the vertical ellipsis for the Export destination you want to remove.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="381fd-151">![Függőleges három pont](media/export-destinations-page-ellipsis.png "Függőleges három pont")</span><span class="sxs-lookup"><span data-stu-id="381fd-151">![Vertical ellipsis](media/export-destinations-page-ellipsis.png "Vertical ellipsis")</span></span>

2. <span data-ttu-id="381fd-152">Válassza a legördülő menü **Eltávolítás** elemét.</span><span class="sxs-lookup"><span data-stu-id="381fd-152">Select **Remove** from the dropdown menu.</span></span>

3. <span data-ttu-id="381fd-153">Erősítse meg az eltávolítást az **Eltávolítás** lehetőség választásával a megerősítő képernyőn.</span><span class="sxs-lookup"><span data-stu-id="381fd-153">Confirm the removal by selecting **Remove** on the confirmation screen.</span></span>
