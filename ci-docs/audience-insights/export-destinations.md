---
title: Adatok exportálása a Customer Insightsból
description: Exportálások kezelése az adatok megosztásához.
ms.date: 03/25/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: phkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 354ce9ef30fe918975d06290430996c84f8bd3f7
ms.sourcegitcommit: aaa275c60c0c77c88196277b266a91d653f8f759
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/14/2021
ms.locfileid: "5896146"
---
# <a name="exports-preview-overview"></a><span data-ttu-id="4aa1c-103">Exportálások (előzetes verzió) áttekintése</span><span class="sxs-lookup"><span data-stu-id="4aa1c-103">Exports (preview) overview</span></span>

<span data-ttu-id="4aa1c-104">Az **Exportálások** lap megjeleníti az összes konfigurált exportálást.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-104">The **Exports** page shows you all configured exports.</span></span> <span data-ttu-id="4aa1c-105">Az exportálások meghatározott adatokat osztanak meg különböző alkalmazásokkal.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-105">Exports share specific data with various applications.</span></span> <span data-ttu-id="4aa1c-106">Ezek tartalmazhatnak ügyfélprofilokat vagy entitásokat, sémákat és leképezési részleteket.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-106">They can include customer profiles or entities, schemas, and mapping details.</span></span> <span data-ttu-id="4aa1c-107">Mindegyik exportáláshoz szükség van egy [rendszergazda kapcsolatra, beállításra, hogy kezelhesse a hitelesítést és a hozzáférést](connections.md).</span><span class="sxs-lookup"><span data-stu-id="4aa1c-107">Each export requires a [connection, set up by an administrator, to manage authentication and access](connections.md).</span></span>

> [!NOTE]
> <span data-ttu-id="4aa1c-108">2021 márciusáig az exportálásáok automatikusan létrehoztak egy kapcsolatot a megfelelő szolgáltatáshoz.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-108">Until March 2021, exports created a connection to the corresponding service automatically.</span></span> <span data-ttu-id="4aa1c-109">Az exportálásokhoz már szükség van [egy rendszergazda által létrehozott és megosztott kapcsolatra](connections.md) még mielőtt létrehoznák őket.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-109">Exports now require a [connection, created and shared by an administrator](connections.md) before you can create them.</span></span>

<span data-ttu-id="4aa1c-110">Az exportálási lap megtekintéséhez menjen az **Adatok** > **Exportpálások** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-110">Go to **Data** > **Exports** to view the exports page.</span></span> <span data-ttu-id="4aa1c-111">Minden felhasználói szerepkörrel rendelkező megtekintheti a konfigurált exportálásokat.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-111">All user roles have access to view configured exports.</span></span> <span data-ttu-id="4aa1c-112">A parancssávban a keresési mező segítségével keresse meg az exportálás nevét, a kapcsolat nevét, vagy a kapcsolat típusát.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-112">Use of the search field in the command bar to find exports by their name, connection name, or connection type.</span></span>

## <a name="set-up-a-new-export"></a><span data-ttu-id="4aa1c-113">Új exportálás beállítása</span><span class="sxs-lookup"><span data-stu-id="4aa1c-113">Set up a new export</span></span>

<span data-ttu-id="4aa1c-114">Az exportálás beállításához vagy szerkesztéséhez elérhető kapcsolatokra van szüksége.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-114">To set up or edit an export, you need to have connections available to you.</span></span> <span data-ttu-id="4aa1c-115">A kapcsolatok a [felhasználói szerepkörtől](permissions.md) függnek:</span><span class="sxs-lookup"><span data-stu-id="4aa1c-115">Connections depend on your [user role](permissions.md):</span></span>
- <span data-ttu-id="4aa1c-116">A rendszergazdák minden kapcsolathoz rendelkeznek hozzáféréssel.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-116">Administrators have access to all connections.</span></span> <span data-ttu-id="4aa1c-117">Az exportálás beállításakor új kapcsolatokat is létrehozhatnak.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-117">They can also create new connections when setting up an export.</span></span>
- <span data-ttu-id="4aa1c-118">A közreműködő adott kapcsolatokhoz férhetnek hozzá.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-118">Contributors can have access to specific connections.</span></span> <span data-ttu-id="4aa1c-119">Ezek a rendszergazdáktól függnek, a kapcsolatok konfigurálásához és megosztásához.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-119">They depend on administrators to configure and share connections.</span></span> <span data-ttu-id="4aa1c-120">További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).</span><span class="sxs-lookup"><span data-stu-id="4aa1c-120">For more information, see [Allow contributors to use a connection for exports](connections.md#allow-contributors-to-use-a-connection-for-exports).</span></span>
- <span data-ttu-id="4aa1c-121">A megtekintők csak a meglévő exportálásokat tekinthetik meg, létrehozni azonban nem jogosultak.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-121">Viewers can only view existing exports but not create them.</span></span>

1. <span data-ttu-id="4aa1c-122">Menjen az **Adatok** > **Exportálások** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-122">Go to **Data** > **Exports**.</span></span>

1. <span data-ttu-id="4aa1c-123">Új exportálási cél létrehozásához válassza az **Exportálás hozzáadása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-123">Select **Add export** to create a new export destination.</span></span>

1. <span data-ttu-id="4aa1c-124">Az **Exportálás beállítása** ablaktáblában válassza ki a használni kívánt kapcsolatot.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-124">In the **Set up export** pane, select which connection to use.</span></span> <span data-ttu-id="4aa1c-125">A [Kapcsolatokat](connections.md) a rendszergazdák kezelik.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-125">[Connections](connections.md) are managed by administrators.</span></span> 

1. <span data-ttu-id="4aa1c-126">Adja meg a szükséges adatokat, majd az exportálás létrehozásához válassza a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-126">Provide the required details and select **Save** to create the export.</span></span>

### <a name="edit-an-export"></a><span data-ttu-id="4aa1c-127">Egy exportálás szerkesztése</span><span class="sxs-lookup"><span data-stu-id="4aa1c-127">Edit an export</span></span>

1. <span data-ttu-id="4aa1c-128">Jelölje ki a szerkeszteni kívánt exportálási célhely függőleges három pontját.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-128">Select the vertical ellipsis for the export destination you want to edit.</span></span>

1. <span data-ttu-id="4aa1c-129">Válassza a legördülő menü **Szerkesztés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-129">Select **Edit** from the drop-down menu.</span></span>

1. <span data-ttu-id="4aa1c-130">Módosítsa a frissíteni kívánt értékeket, majd válassza a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-130">Change the values you want to update and select **Save**.</span></span>

## <a name="view-exports-and-export-details"></a><span data-ttu-id="4aa1c-131">Exportálás és exportálás részleteinek megtekintése</span><span class="sxs-lookup"><span data-stu-id="4aa1c-131">View Exports and export details</span></span>

<span data-ttu-id="4aa1c-132">Az exportálási célhelyek a létrehozása után az **Adatok** > **Exportálások** listán jelennek meg.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-132">After creating export destinations, they are listed on **Data** > **Exports**.</span></span> <span data-ttu-id="4aa1c-133">Minden felhasználó láthatja, hogy mely adatok lettek megosztva, és hogy milyen állapotúak.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-133">All users can see which data is shared and its latest status.</span></span>

1. <span data-ttu-id="4aa1c-134">Menjen az **Adatok** > **Exportálások** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-134">Go to **Data** > **Exports**.</span></span>

1. <span data-ttu-id="4aa1c-135">A szerkesztési jogosultsággal nem rendelkező felhasználók a **Szerkesztés** helyett a **Megtekintés** lehetőséget választhatják az exportálás részleteinek megtekintéséhez.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-135">Users without edit permissions select **View** instead of **Edit** see the export details.</span></span>

1. <span data-ttu-id="4aa1c-136">Ez az oldalpanel mutatja az exportálás beállítását.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-136">This side pane shows the set up of this export.</span></span> <span data-ttu-id="4aa1c-137">Az értékek a szerkesztési jogosultságok nélkül nem módosíthatók.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-137">Without edit permissions, you can't change values.</span></span> <span data-ttu-id="4aa1c-138">Az exportálások lapra való visszatéréshez válassza a **Bezárás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-138">Select **Close** to return to the exports page.</span></span>

## <a name="run-exports-on-demand"></a><span data-ttu-id="4aa1c-139">Exportálások futtatása igény szerint</span><span class="sxs-lookup"><span data-stu-id="4aa1c-139">Run exports on demand</span></span>

<span data-ttu-id="4aa1c-140">Az exportálás konfigurálása után az összes [ütemezett frissítéssel](system.md#schedule-tab) futni fog, amíg van működő kapcsolata.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-140">After configuring an export, it will run with every [scheduled refresh](system.md#schedule-tab) as long as it has a working connection.</span></span>

<span data-ttu-id="4aa1c-141">Ütemezett frissítésre való várakozás nélküli adatexportáláshoz menjen az **Adatok** > **Exportálások** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-141">To export data without waiting for a scheduled refresh, go to **Data** > **Exports**.</span></span> <span data-ttu-id="4aa1c-142">Két lehetőség közül választhat:</span><span class="sxs-lookup"><span data-stu-id="4aa1c-142">You have two options:</span></span>

- <span data-ttu-id="4aa1c-143">Az összes exportálás futtatásához válassza az **Összes futtatása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-143">To run all exports, select **Run all** in the command bar.</span></span> 
- <span data-ttu-id="4aa1c-144">Egyetlen exportálás futtatásához jelölje ki a három pontot (...) a listaelemen, majd válassza a **Futtatás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-144">To run a single export, select the ellipsis (...) on a list item and then choose **Run**.</span></span>

## <a name="remove-an-export"></a><span data-ttu-id="4aa1c-145">Exportálás eltávolítása</span><span class="sxs-lookup"><span data-stu-id="4aa1c-145">Remove an Export</span></span>

1. <span data-ttu-id="4aa1c-146">Menjen az **Adatok** > **Exportálások** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-146">Go to **Data** > **Exports**.</span></span>

1. <span data-ttu-id="4aa1c-147">Jelölje ki az eltávolítani kívánt Exportálás függőleges három pontját.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-147">Select the vertical ellipsis for the Export you want to remove.</span></span>

1. <span data-ttu-id="4aa1c-148">Válassza a legördülő menü **Eltávolítás** elemét.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-148">Select **Remove** from the dropdown menu.</span></span>

1. <span data-ttu-id="4aa1c-149">Erősítse meg az eltávolítást az **Eltávolítás** lehetőség választásával a megerősítő képernyőn.</span><span class="sxs-lookup"><span data-stu-id="4aa1c-149">Confirm the removal by selecting **Remove** on the confirmation screen.</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]
