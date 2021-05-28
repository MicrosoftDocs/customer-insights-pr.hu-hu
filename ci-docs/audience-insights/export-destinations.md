---
title: Adatok exportálása a Customer Insightsból
description: Exportálások kezelése az adatok megosztásához.
ms.date: 03/25/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: c1078ed0ba259a6e9cde3c7ede3570890ae48e67
ms.sourcegitcommit: 33a8e21b3bf6521bdb8346f81f79fce88091ddfd
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/10/2021
ms.locfileid: "6016617"
---
# <a name="exports-preview-overview"></a><span data-ttu-id="a4cdc-103">Exportálások (előzetes verzió) áttekintése</span><span class="sxs-lookup"><span data-stu-id="a4cdc-103">Exports (preview) overview</span></span>

<span data-ttu-id="a4cdc-104">Az **Exportálások** lap megjeleníti az összes konfigurált exportálást.</span><span class="sxs-lookup"><span data-stu-id="a4cdc-104">The **Exports** page shows you all configured exports.</span></span> <span data-ttu-id="a4cdc-105">Az exportálások meghatározott adatokat osztanak meg különböző alkalmazásokkal.</span><span class="sxs-lookup"><span data-stu-id="a4cdc-105">Exports share specific data with various applications.</span></span> <span data-ttu-id="a4cdc-106">Ezek tartalmazhatnak ügyfélprofilokat vagy entitásokat, sémákat és leképezési részleteket.</span><span class="sxs-lookup"><span data-stu-id="a4cdc-106">They can include customer profiles or entities, schemas, and mapping details.</span></span> <span data-ttu-id="a4cdc-107">Mindegyik exportáláshoz szükség van egy [rendszergazda kapcsolatra, beállításra, hogy kezelhesse a hitelesítést és a hozzáférést](connections.md).</span><span class="sxs-lookup"><span data-stu-id="a4cdc-107">Each export requires a [connection, set up by an administrator, to manage authentication and access](connections.md).</span></span>

<span data-ttu-id="a4cdc-108">Az exportálási lap megtekintéséhez menjen az **Adatok** > **Exportpálások** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="a4cdc-108">Go to **Data** > **Exports** to view the exports page.</span></span> <span data-ttu-id="a4cdc-109">Minden felhasználói szerepkörrel rendelkező megtekintheti a konfigurált exportálásokat.</span><span class="sxs-lookup"><span data-stu-id="a4cdc-109">All user roles have access to view configured exports.</span></span> <span data-ttu-id="a4cdc-110">A parancssávban a keresési mező segítségével keresse meg az exportálás nevét, a kapcsolat nevét, vagy a kapcsolat típusát.</span><span class="sxs-lookup"><span data-stu-id="a4cdc-110">Use of the search field in the command bar to find exports by their name, connection name, or connection type.</span></span>

## <a name="set-up-a-new-export"></a><span data-ttu-id="a4cdc-111">Új exportálás beállítása</span><span class="sxs-lookup"><span data-stu-id="a4cdc-111">Set up a new export</span></span>

<span data-ttu-id="a4cdc-112">Az exportálás beállításához vagy szerkesztéséhez elérhető kapcsolatokra van szüksége.</span><span class="sxs-lookup"><span data-stu-id="a4cdc-112">To set up or edit an export, you need to have connections available to you.</span></span> <span data-ttu-id="a4cdc-113">A kapcsolatok a [felhasználói szerepkörtől](permissions.md) függnek:</span><span class="sxs-lookup"><span data-stu-id="a4cdc-113">Connections depend on your [user role](permissions.md):</span></span>
- <span data-ttu-id="a4cdc-114">A rendszergazdák minden kapcsolathoz rendelkeznek hozzáféréssel.</span><span class="sxs-lookup"><span data-stu-id="a4cdc-114">Administrators have access to all connections.</span></span> <span data-ttu-id="a4cdc-115">Az exportálás beállításakor új kapcsolatokat is létrehozhatnak.</span><span class="sxs-lookup"><span data-stu-id="a4cdc-115">They can also create new connections when setting up an export.</span></span>
- <span data-ttu-id="a4cdc-116">A közreműködő adott kapcsolatokhoz férhetnek hozzá.</span><span class="sxs-lookup"><span data-stu-id="a4cdc-116">Contributors can have access to specific connections.</span></span> <span data-ttu-id="a4cdc-117">Ezek a rendszergazdáktól függnek, a kapcsolatok konfigurálásához és megosztásához.</span><span class="sxs-lookup"><span data-stu-id="a4cdc-117">They depend on administrators to configure and share connections.</span></span> <span data-ttu-id="a4cdc-118">További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).</span><span class="sxs-lookup"><span data-stu-id="a4cdc-118">For more information, see [Allow contributors to use a connection for exports](connections.md#allow-contributors-to-use-a-connection-for-exports).</span></span>
- <span data-ttu-id="a4cdc-119">A megtekintők csak a meglévő exportálásokat tekinthetik meg, létrehozni azonban nem jogosultak.</span><span class="sxs-lookup"><span data-stu-id="a4cdc-119">Viewers can only view existing exports but not create them.</span></span>

1. <span data-ttu-id="a4cdc-120">Menjen az **Adatok** > **Exportálások** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="a4cdc-120">Go to **Data** > **Exports**.</span></span>

1. <span data-ttu-id="a4cdc-121">Új exportálási cél létrehozásához válassza az **Exportálás hozzáadása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="a4cdc-121">Select **Add export** to create a new export destination.</span></span>

1. <span data-ttu-id="a4cdc-122">Az **Exportálás beállítása** ablaktáblában válassza ki a használni kívánt kapcsolatot.</span><span class="sxs-lookup"><span data-stu-id="a4cdc-122">In the **Set up export** pane, select which connection to use.</span></span> <span data-ttu-id="a4cdc-123">A [Kapcsolatokat](connections.md) a rendszergazdák kezelik.</span><span class="sxs-lookup"><span data-stu-id="a4cdc-123">[Connections](connections.md) are managed by administrators.</span></span> 

1. <span data-ttu-id="a4cdc-124">Adja meg a szükséges adatokat, majd az exportálás létrehozásához válassza a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="a4cdc-124">Provide the required details and select **Save** to create the export.</span></span>

### <a name="edit-an-export"></a><span data-ttu-id="a4cdc-125">Egy exportálás szerkesztése</span><span class="sxs-lookup"><span data-stu-id="a4cdc-125">Edit an export</span></span>

1. <span data-ttu-id="a4cdc-126">Jelölje ki a szerkeszteni kívánt exportálási célhely függőleges három pontját.</span><span class="sxs-lookup"><span data-stu-id="a4cdc-126">Select the vertical ellipsis for the export destination you want to edit.</span></span>

1. <span data-ttu-id="a4cdc-127">Válassza a legördülő menü **Szerkesztés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="a4cdc-127">Select **Edit** from the drop-down menu.</span></span>

1. <span data-ttu-id="a4cdc-128">Módosítsa a frissíteni kívánt értékeket, majd válassza a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="a4cdc-128">Change the values you want to update and select **Save**.</span></span>

## <a name="view-exports-and-export-details"></a><span data-ttu-id="a4cdc-129">Exportálás és exportálás részleteinek megtekintése</span><span class="sxs-lookup"><span data-stu-id="a4cdc-129">View Exports and export details</span></span>

<span data-ttu-id="a4cdc-130">Az exportálási célhelyek a létrehozása után az **Adatok** > **Exportálások** listán jelennek meg.</span><span class="sxs-lookup"><span data-stu-id="a4cdc-130">After creating export destinations, they are listed on **Data** > **Exports**.</span></span> <span data-ttu-id="a4cdc-131">Minden felhasználó láthatja, hogy mely adatok lettek megosztva, és hogy milyen állapotúak.</span><span class="sxs-lookup"><span data-stu-id="a4cdc-131">All users can see which data is shared and its latest status.</span></span>

1. <span data-ttu-id="a4cdc-132">Menjen az **Adatok** > **Exportálások** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="a4cdc-132">Go to **Data** > **Exports**.</span></span>

1. <span data-ttu-id="a4cdc-133">A szerkesztési jogosultsággal nem rendelkező felhasználók a **Szerkesztés** helyett a **Megtekintés** lehetőséget választhatják az exportálás részleteinek megtekintéséhez.</span><span class="sxs-lookup"><span data-stu-id="a4cdc-133">Users without edit permissions select **View** instead of **Edit** see the export details.</span></span>

1. <span data-ttu-id="a4cdc-134">Ez az oldalpanel mutatja az exportálás beállítását.</span><span class="sxs-lookup"><span data-stu-id="a4cdc-134">This side pane shows the set up of this export.</span></span> <span data-ttu-id="a4cdc-135">Az értékek a szerkesztési jogosultságok nélkül nem módosíthatók.</span><span class="sxs-lookup"><span data-stu-id="a4cdc-135">Without edit permissions, you can't change values.</span></span> <span data-ttu-id="a4cdc-136">Az exportálások lapra való visszatéréshez válassza a **Bezárás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="a4cdc-136">Select **Close** to return to the exports page.</span></span>

## <a name="run-exports-on-demand"></a><span data-ttu-id="a4cdc-137">Exportálások futtatása igény szerint</span><span class="sxs-lookup"><span data-stu-id="a4cdc-137">Run exports on demand</span></span>

<span data-ttu-id="a4cdc-138">Az exportálás konfigurálása után az összes [ütemezett frissítéssel](system.md#schedule-tab) futni fog, amíg van működő kapcsolata.</span><span class="sxs-lookup"><span data-stu-id="a4cdc-138">After configuring an export, it will run with every [scheduled refresh](system.md#schedule-tab) as long as it has a working connection.</span></span>

<span data-ttu-id="a4cdc-139">Ütemezett frissítésre való várakozás nélküli adatexportáláshoz menjen az **Adatok** > **Exportálások** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="a4cdc-139">To export data without waiting for a scheduled refresh, go to **Data** > **Exports**.</span></span> <span data-ttu-id="a4cdc-140">Két lehetőség közül választhat:</span><span class="sxs-lookup"><span data-stu-id="a4cdc-140">You have two options:</span></span>

- <span data-ttu-id="a4cdc-141">Az összes exportálás futtatásához válassza az **Összes futtatása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="a4cdc-141">To run all exports, select **Run all** in the command bar.</span></span> 
- <span data-ttu-id="a4cdc-142">Egyetlen exportálás futtatásához jelölje ki a három pontot (...) a listaelemen, majd válassza a **Futtatás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="a4cdc-142">To run a single export, select the ellipsis (...) on a list item and then choose **Run**.</span></span>

## <a name="remove-an-export"></a><span data-ttu-id="a4cdc-143">Exportálás eltávolítása</span><span class="sxs-lookup"><span data-stu-id="a4cdc-143">Remove an Export</span></span>

1. <span data-ttu-id="a4cdc-144">Menjen az **Adatok** > **Exportálások** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="a4cdc-144">Go to **Data** > **Exports**.</span></span>

1. <span data-ttu-id="a4cdc-145">Jelölje ki az eltávolítani kívánt Exportálás függőleges három pontját.</span><span class="sxs-lookup"><span data-stu-id="a4cdc-145">Select the vertical ellipsis for the Export you want to remove.</span></span>

1. <span data-ttu-id="a4cdc-146">Válassza a legördülő menü **Eltávolítás** elemét.</span><span class="sxs-lookup"><span data-stu-id="a4cdc-146">Select **Remove** from the dropdown menu.</span></span>

1. <span data-ttu-id="a4cdc-147">Erősítse meg az eltávolítást az **Eltávolítás** lehetőség választásával a megerősítő képernyőn.</span><span class="sxs-lookup"><span data-stu-id="a4cdc-147">Confirm the removal by selecting **Remove** on the confirmation screen.</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]
