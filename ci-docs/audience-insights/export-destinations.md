---
title: Adatok exportálása a Customer Insightsból
description: Exportálások kezelése az adatok megosztásához.
ms.date: 06/14/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 28563e3a76535cb0c92bfcda4ef5037430d00cfa
ms.sourcegitcommit: d84d664e67f263bfeb741154d309088c5101b9c3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/24/2021
ms.locfileid: "6305481"
---
# <a name="exports-preview-overview"></a><span data-ttu-id="8249f-103">Exportálások (előzetes verzió) áttekintése</span><span class="sxs-lookup"><span data-stu-id="8249f-103">Exports (preview) overview</span></span>

<span data-ttu-id="8249f-104">Az **Exportálások** lap megjeleníti az összes konfigurált exportálást.</span><span class="sxs-lookup"><span data-stu-id="8249f-104">The **Exports** page shows you all configured exports.</span></span> <span data-ttu-id="8249f-105">Az exportálások meghatározott adatokat osztanak meg különböző alkalmazásokkal.</span><span class="sxs-lookup"><span data-stu-id="8249f-105">Exports share specific data with various applications.</span></span> <span data-ttu-id="8249f-106">Ezek tartalmazhatnak ügyfélprofilokat vagy entitásokat, sémákat és leképezési részleteket.</span><span class="sxs-lookup"><span data-stu-id="8249f-106">They can include customer profiles or entities, schemas, and mapping details.</span></span> <span data-ttu-id="8249f-107">Mindegyik exportáláshoz szükség van egy [rendszergazda kapcsolatra, beállításra, hogy kezelhesse a hitelesítést és a hozzáférést](connections.md).</span><span class="sxs-lookup"><span data-stu-id="8249f-107">Each export requires a [connection, set up by an administrator, to manage authentication and access](connections.md).</span></span>

<span data-ttu-id="8249f-108">Az exportálási lap megtekintéséhez menjen az **Adatok** > **Exportpálások** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="8249f-108">Go to **Data** > **Exports** to view the exports page.</span></span> <span data-ttu-id="8249f-109">Minden felhasználói szerepkör megtekintheti a konfigurált exportálást.</span><span class="sxs-lookup"><span data-stu-id="8249f-109">All user roles can view configured exports.</span></span> <span data-ttu-id="8249f-110">A parancssáv keresőmezőjében keresse meg az exportot a nevük, a kapcsolatnevük vagy a kapcsolattípusuk alapján.</span><span class="sxs-lookup"><span data-stu-id="8249f-110">Use the search field in the command bar to find exports by their name, connection name, or connection type.</span></span>

## <a name="set-up-a-new-export"></a><span data-ttu-id="8249f-111">Új exportálás beállítása</span><span class="sxs-lookup"><span data-stu-id="8249f-111">Set up a new export</span></span>

<span data-ttu-id="8249f-112">Az exportálás beállításához vagy szerkesztéséhez elérhető kapcsolatokra van szüksége.</span><span class="sxs-lookup"><span data-stu-id="8249f-112">To set up or edit an export, you need to have connections available to you.</span></span> <span data-ttu-id="8249f-113">A kapcsolatok a [felhasználói szerepkörtől](permissions.md) függnek:</span><span class="sxs-lookup"><span data-stu-id="8249f-113">Connections depend on your [user role](permissions.md):</span></span>
- <span data-ttu-id="8249f-114">A rendszergazdák minden kapcsolathoz rendelkeznek hozzáféréssel.</span><span class="sxs-lookup"><span data-stu-id="8249f-114">Administrators have access to all connections.</span></span> <span data-ttu-id="8249f-115">Az exportálás beállításakor új kapcsolatokat is létrehozhatnak.</span><span class="sxs-lookup"><span data-stu-id="8249f-115">They can also create new connections when setting up an export.</span></span>
- <span data-ttu-id="8249f-116">A közreműködő adott kapcsolatokhoz férhetnek hozzá.</span><span class="sxs-lookup"><span data-stu-id="8249f-116">Contributors can have access to specific connections.</span></span> <span data-ttu-id="8249f-117">Ezek a rendszergazdáktól függnek, a kapcsolatok konfigurálásához és megosztásához.</span><span class="sxs-lookup"><span data-stu-id="8249f-117">They depend on administrators to configure and share connections.</span></span> <span data-ttu-id="8249f-118">Az exportlista megmutatja, hogy a közreműködők szerkeszthetik-e vagy csak megtekinthetik-e az exportálást **Az Ön engedélyei** oszlopban.</span><span class="sxs-lookup"><span data-stu-id="8249f-118">The exports list shows contributors whether they can edit or only view an export in the **Your permissions** column.</span></span> <span data-ttu-id="8249f-119">További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).</span><span class="sxs-lookup"><span data-stu-id="8249f-119">For more information, see [Allow contributors to use a connection for exports](connections.md#allow-contributors-to-use-a-connection-for-exports).</span></span>
- <span data-ttu-id="8249f-120">A megtekintők csak a meglévő exportálásokat tekinthetik meg, létrehozni azonban nem jogosultak.</span><span class="sxs-lookup"><span data-stu-id="8249f-120">Viewers can only view existing exports but not create them.</span></span>

### <a name="define-a-new-export"></a><span data-ttu-id="8249f-121">Új exportálás definiálása</span><span class="sxs-lookup"><span data-stu-id="8249f-121">Define a new export</span></span>

1. <span data-ttu-id="8249f-122">Menjen az **Adatok** > **Exportálások** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="8249f-122">Go to **Data** > **Exports**.</span></span>

1. <span data-ttu-id="8249f-123">Új exportálás létrehozásához válassza az **Exportálás hozzáadása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="8249f-123">Select **Add export** to create a new export.</span></span>

1. <span data-ttu-id="8249f-124">Az **Exportálás beállítása** ablaktáblában válassza ki a használni kívánt kapcsolatot.</span><span class="sxs-lookup"><span data-stu-id="8249f-124">In the **Set up export** pane, select which connection to use.</span></span> <span data-ttu-id="8249f-125">A [Kapcsolatokat](connections.md) a rendszergazdák kezelik.</span><span class="sxs-lookup"><span data-stu-id="8249f-125">[Connections](connections.md) are managed by administrators.</span></span> 

1. <span data-ttu-id="8249f-126">Adja meg a szükséges adatokat, majd az exportálás létrehozásához válassza a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="8249f-126">Provide the required details and select **Save** to create the export.</span></span>

### <a name="define-a-new-export-based-on-an-existing-export"></a><span data-ttu-id="8249f-127">Új exportálás definiálása meglévő export alapján</span><span class="sxs-lookup"><span data-stu-id="8249f-127">Define a new export based on an existing export</span></span>

1. <span data-ttu-id="8249f-128">Menjen az **Adatok** > **Exportálások** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="8249f-128">Go to **Data** > **Exports**.</span></span>

1. <span data-ttu-id="8249f-129">Az exportálásáokat tartalmazó listán jelölje ki a duplikálni kívánt exportálást.</span><span class="sxs-lookup"><span data-stu-id="8249f-129">In the list of exports, select the export you want to duplicate.</span></span>

1. <span data-ttu-id="8249f-130">Válassza a **Duplikált elem létrehozása** lehetőséget a prancssávon az **Exportálás beállítása** panel megnyitásához, amely tartalmazza a kiválasztott exportálás részleteit.</span><span class="sxs-lookup"><span data-stu-id="8249f-130">Select **Create duplicate** in the command bar to open the **Set up export** pane with the details of the selected export.</span></span>

1. <span data-ttu-id="8249f-131">Tekintse át és adaptálja át az exportálást, és válassza a **Mentés** lehetőséget új exportálás létrehozásához.</span><span class="sxs-lookup"><span data-stu-id="8249f-131">Review and adapt the export and select **Save** to create a new export.</span></span>

### <a name="edit-an-export"></a><span data-ttu-id="8249f-132">Egy exportálás szerkesztése</span><span class="sxs-lookup"><span data-stu-id="8249f-132">Edit an export</span></span>

1. <span data-ttu-id="8249f-133">Menjen az **Adatok** > **Exportálások** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="8249f-133">Go to **Data** > **Exports**.</span></span>

1. <span data-ttu-id="8249f-134">Az exportálásokat tartalmazó listán jelölje ki a szerkeszteni kívánt exportálást.</span><span class="sxs-lookup"><span data-stu-id="8249f-134">In the list of exports, select the export you want to edit.</span></span>

1. <span data-ttu-id="8249f-135">Válassza a parancssávon a **Szerkesztés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="8249f-135">Select **Edit** in the command bar.</span></span>

1. <span data-ttu-id="8249f-136">Módosítsa a frissíteni kívánt értékeket, majd válassza a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="8249f-136">Change the values you want to update and select **Save**.</span></span>

## <a name="view-exports-and-export-details"></a><span data-ttu-id="8249f-137">Exportálás és exportálás részleteinek megtekintése</span><span class="sxs-lookup"><span data-stu-id="8249f-137">View exports and export details</span></span>

<span data-ttu-id="8249f-138">Az exportálási célhelyek a létrehozása után az **Adatok** > **Exportálások** listán jelennek meg.</span><span class="sxs-lookup"><span data-stu-id="8249f-138">After creating export destinations, they're listed on **Data** > **Exports**.</span></span> <span data-ttu-id="8249f-139">Minden felhasználó láthatja, hogy mely adatok lettek megosztva, és hogy milyen állapotúak.</span><span class="sxs-lookup"><span data-stu-id="8249f-139">All users can see which data is shared and its latest status.</span></span>

1. <span data-ttu-id="8249f-140">Menjen az **Adatok** > **Exportálások** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="8249f-140">Go to **Data** > **Exports**.</span></span>

1. <span data-ttu-id="8249f-141">A szerkesztési engedélyekkel nem rendelkező felhasználók a **Nézet** lehetőséget választják a **Szerkesztés** helyett az exportálás részleteinek megtekintéséhez.</span><span class="sxs-lookup"><span data-stu-id="8249f-141">Users without edit permissions select **View** instead of **Edit** to see the export details.</span></span>

1. <span data-ttu-id="8249f-142">Az oldalsó ablaktáblán megjelenik egy exportálás konfigurációja.</span><span class="sxs-lookup"><span data-stu-id="8249f-142">The side pane shows the configuration of an export.</span></span> <span data-ttu-id="8249f-143">Az értékek a szerkesztési jogosultságok nélkül nem módosíthatók.</span><span class="sxs-lookup"><span data-stu-id="8249f-143">Without edit permissions, you can't change values.</span></span> <span data-ttu-id="8249f-144">Az exportálások lapra való visszatéréshez válassza a **Bezárás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="8249f-144">Select **Close** to return to the exports page.</span></span>

## <a name="schedule-and-run-exports"></a><span data-ttu-id="8249f-145">Exportálás ütemezése ás futtatása</span><span class="sxs-lookup"><span data-stu-id="8249f-145">Schedule and run exports</span></span>

<span data-ttu-id="8249f-146">Minden konfigurált exportálás egy frissítési ütemezéssel rendelkezik.</span><span class="sxs-lookup"><span data-stu-id="8249f-146">Each export you configure has a refresh schedule.</span></span> <span data-ttu-id="8249f-147">A frissítés során a rendszer új vagy frissített adatokat keres, amelyek szerepeljenek az exportálásban.</span><span class="sxs-lookup"><span data-stu-id="8249f-147">During a refresh, the system looks for new or updated data to include in an export.</span></span> <span data-ttu-id="8249f-148">Alapértelmezés szerint az exportálás minden [ütemezett rendszerfrissítés](system.md#schedule-tab) részeként fut.</span><span class="sxs-lookup"><span data-stu-id="8249f-148">By default, exports are run as part of every [scheduled system refresh](system.md#schedule-tab).</span></span> <span data-ttu-id="8249f-149">Testreszabhatja a frissítési ütemezést, vagy ki is kapcsolhatja az exportálás manuális futtatásához.</span><span class="sxs-lookup"><span data-stu-id="8249f-149">You can customize the refresh schedule or turn it off to run exports manually.</span></span>

<span data-ttu-id="8249f-150">Az exportálási ütemezések a környezet állapotától függenek.</span><span class="sxs-lookup"><span data-stu-id="8249f-150">Export schedules depend on the state of your environment.</span></span> <span data-ttu-id="8249f-151">Ha folyamatban vannak frissítések [függőségeken](system.md#refresh-policies) ,amikor egy ütemezett exportálást el kell indítani, a rendszer először befejezi a frissítéseket, majd futtatja az exportálást.</span><span class="sxs-lookup"><span data-stu-id="8249f-151">If there are updates in progress on [dependencies](system.md#refresh-policies) when a scheduled export should start, the system will first complete the updates and then run the export.</span></span> <span data-ttu-id="8249f-152">A **Frissítve** oszlopban láthatja, hogy mikor frissült utoljára egy exportálás.</span><span class="sxs-lookup"><span data-stu-id="8249f-152">You can see when an export was last refreshed in column **Refreshed**.</span></span>

### <a name="schedule-exports"></a><span data-ttu-id="8249f-153">Exportálások ütemezése</span><span class="sxs-lookup"><span data-stu-id="8249f-153">Schedule exports</span></span>

<span data-ttu-id="8249f-154">Egyéni frissítési ütemezéseket az egyes exportálásokhoz és egyszerre több exportáláshoz is definiálhat.</span><span class="sxs-lookup"><span data-stu-id="8249f-154">You can define custom refresh schedules for individual exports or several exports at once.</span></span> <span data-ttu-id="8249f-155">A jelenleg meghatározott ütemezés az exportlista **Ütemezés** oszlopában található.</span><span class="sxs-lookup"><span data-stu-id="8249f-155">The currently defined schedule is listed in the **Schedule** column of the export list.</span></span> <span data-ttu-id="8249f-156">Az ütemterv módosításának engedélye megegyezik az [exportálások szerkesztése és definiálása](export-destinations.md#set-up-a-new-export) folyamattal.</span><span class="sxs-lookup"><span data-stu-id="8249f-156">The permission to change the schedule is the same as for [editing and defining exports](export-destinations.md#set-up-a-new-export).</span></span> 

1. <span data-ttu-id="8249f-157">Menjen az **Adatok** > **Exportálások** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="8249f-157">Go to **Data** > **Exports**.</span></span>

1. <span data-ttu-id="8249f-158">Válassza ki az exportálni kívánt ütemezést.</span><span class="sxs-lookup"><span data-stu-id="8249f-158">Select the export you want to schedule.</span></span>

1. <span data-ttu-id="8249f-159">Válassza a parancssávon az **Ütemezés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="8249f-159">Select **Schedule** in the command bar.</span></span>

1. <span data-ttu-id="8249f-160">Az **Exportálás ütemezése** ablaktáblában állítsa be az **Ütemezési futtatása** lehetőséget **Be** értékre az exportálás automatikus futtatásához.</span><span class="sxs-lookup"><span data-stu-id="8249f-160">In the **Schedule export** pane, set the **Schedule run** to **On** to run the export automatically.</span></span> <span data-ttu-id="8249f-161">Állítsa **Ki** értékre manuálisan frissítéshez.</span><span class="sxs-lookup"><span data-stu-id="8249f-161">Set it to **Off** to refresh it manually.</span></span>

1. <span data-ttu-id="8249f-162">Az automatikusan frissített exporthoz válasszon egy **Ismétlődés** értéket, és adja meg annak részleteit.</span><span class="sxs-lookup"><span data-stu-id="8249f-162">For automatically refreshed exports, choose a **Recurrence** value and specify the details for it.</span></span> <span data-ttu-id="8249f-163">A definiált idő az ismétlődés minden esetére vonatkozik.</span><span class="sxs-lookup"><span data-stu-id="8249f-163">The time defined applies to all instances of a recurrence.</span></span> <span data-ttu-id="8249f-164">Ez az az idő, amikor az exportálásnak frissülnie kell.</span><span class="sxs-lookup"><span data-stu-id="8249f-164">It's the time when an export should start refreshing.</span></span>

1. <span data-ttu-id="8249f-165">A módosítások alkalmazása és aktiválása a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="8249f-165">Apply and activate your changes by selecting **Save**.</span></span>

<span data-ttu-id="8249f-166">Több exportálás ütemezésének szerkesztésekor az **Ütemezés megtartása vagy felülbírálása** alatt válasszon:</span><span class="sxs-lookup"><span data-stu-id="8249f-166">When editing the schedule for several exports, you need to make a selection under **Keep or override schedules**:</span></span>
- <span data-ttu-id="8249f-167">**Egyéni ütemezések megtartása**: A kiválasztott export korábban meghatározott ütemezésének fenntartása, és csak annak letiltása vagy engedélyezése.</span><span class="sxs-lookup"><span data-stu-id="8249f-167">**Keep individual schedules**: Persist the previously defined schedule for the selected exports and only disable or enable them.</span></span>
- <span data-ttu-id="8249f-168">**Új ütemezés definiálása az összes kiválasztott exportáláshoz**: A kijelölt exportálás meglévő ütemezésének felülírása.</span><span class="sxs-lookup"><span data-stu-id="8249f-168">**Define new schedule for all selected exports**: Override the existing schedules of the selected exports.</span></span>

### <a name="run-exports-on-demand"></a><span data-ttu-id="8249f-169">Exportálások futtatása igény szerint</span><span class="sxs-lookup"><span data-stu-id="8249f-169">Run exports on demand</span></span>

<span data-ttu-id="8249f-170">Ütemezett frissítésre való várakozás nélküli adatexportáláshoz menjen az **Adatok** > **Exportálások** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="8249f-170">To export data without waiting for a scheduled refresh, go to **Data** > **Exports**.</span></span>

- <span data-ttu-id="8249f-171">Az összes exportálás futtatásához válassza az **Összes futtatása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="8249f-171">To run all exports, select **Run all** in the command bar.</span></span> <span data-ttu-id="8249f-172">Ez a művelet csak olyan exportot futtat, amelyekhez aktív ütemezéssel rendelkezik.</span><span class="sxs-lookup"><span data-stu-id="8249f-172">This action will only run exports that have an active schedule.</span></span>
- <span data-ttu-id="8249f-173">Egyetlen exportálás futtatásához jelölje ki azt a listában, és válassza a **Futtatás** lehetőséget a parancssávon.</span><span class="sxs-lookup"><span data-stu-id="8249f-173">To run a single export, select it in the list and select **Run** in the command bar.</span></span> <span data-ttu-id="8249f-174">Így futtathat az exportálást aktív ütemezés nélkül.</span><span class="sxs-lookup"><span data-stu-id="8249f-174">That's how you run exports with no active schedule.</span></span> 

## <a name="remove-an-export"></a><span data-ttu-id="8249f-175">Exportálás eltávolítása</span><span class="sxs-lookup"><span data-stu-id="8249f-175">Remove an Export</span></span>

1. <span data-ttu-id="8249f-176">Menjen az **Adatok** > **Exportálások** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="8249f-176">Go to **Data** > **Exports**.</span></span>

1. <span data-ttu-id="8249f-177">Jelölje ki az eltávolítandó exportálást.</span><span class="sxs-lookup"><span data-stu-id="8249f-177">Select the export you want to remove.</span></span>

1. <span data-ttu-id="8249f-178">A parancssávon válassza az **Eltávolítás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="8249f-178">Select **Remove** in the command bar.</span></span>

1. <span data-ttu-id="8249f-179">Erősítse meg az eltávolítást az **Eltávolítás** lehetőség választásával a megerősítő képernyőn.</span><span class="sxs-lookup"><span data-stu-id="8249f-179">Confirm the removal by selecting **Remove** on the confirmation screen.</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]
