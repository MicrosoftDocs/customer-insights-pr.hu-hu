---
title: Egyéb szolgáltatásokhoz való kapcsolódás a Customer Insightsból.
description: Adatok megosztása más szolgáltatásokkal.
ms.date: 04/09/2021
ms.reviewer: nikeller
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: 106dbc26f95b309821d738e1484b1eaa79dd225b
ms.sourcegitcommit: aaa275c60c0c77c88196277b266a91d653f8f759
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/14/2021
ms.locfileid: "5896100"
---
# <a name="connections-preview-overview"></a><span data-ttu-id="b6120-103">Kapcsolatok (előzetes verzió) áttekintése</span><span class="sxs-lookup"><span data-stu-id="b6120-103">Connections (preview) overview</span></span>

<span data-ttu-id="b6120-104">A kapcsolatok kulcsfontosságúak az adatok Customer Insightsba és abból való megosztásának engedélyezéséhez.</span><span class="sxs-lookup"><span data-stu-id="b6120-104">Connections are the key to enable data sharing to and from Customer Insights.</span></span> <span data-ttu-id="b6120-105">Minden kapcsolat adatmegosztást hoz létre egy adott szolgáltatással.</span><span class="sxs-lookup"><span data-stu-id="b6120-105">Each connection establishes data sharing with a specific service.</span></span> <span data-ttu-id="b6120-106">A kapcsolatok a [külső gyártótól származó bővítések](enrichment-hub.md) és az [exportálások konfigurációjának](export-destinations.md) az alapja.</span><span class="sxs-lookup"><span data-stu-id="b6120-106">Connections are the foundation to [configure third-party enrichments](enrichment-hub.md) and [configure exports](export-destinations.md).</span></span> <span data-ttu-id="b6120-107">Egy kapcsolat többször is használható.</span><span class="sxs-lookup"><span data-stu-id="b6120-107">The same connection can be used multiple times.</span></span> <span data-ttu-id="b6120-108">A Dynamics 365 Marketing alkalmazással például egy kapcsolat több exportálásra használható, és egy Leadspace-kapcsolat használható több adat bővítésére is.</span><span class="sxs-lookup"><span data-stu-id="b6120-108">For example, one connection to Dynamics 365 Marketing works for multiple exports and one Leadspace connection can be used for several enrichments.</span></span>

<span data-ttu-id="b6120-109">A kapcsolatok létrehozásához és megtekintéséhez menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="b6120-109">Go to **Admin** > **Connections** to create and view connections.</span></span>

<span data-ttu-id="b6120-110">A **Kapcsolatok** fül megjeleníti az összes aktív kapcsolatot.</span><span class="sxs-lookup"><span data-stu-id="b6120-110">The **Connections** tab shows you all active connections.</span></span> <span data-ttu-id="b6120-111">A listában minden kapcsolathoz egy sor tartozik.</span><span class="sxs-lookup"><span data-stu-id="b6120-111">The list shows a row for each connection.</span></span> 

<span data-ttu-id="b6120-112">Gyors áttekintést és leírást kaphat, és a **Felfedezés** fülön megismerheti, hogy mikre lehet képes az egyes bővíthetőségi beállításokkal.</span><span class="sxs-lookup"><span data-stu-id="b6120-112">Get a quick overview, description, and find out what you can do with each extensibility option on the **Discover** tab.</span></span>

### <a name="exports"></a><span data-ttu-id="b6120-113">Exportálások</span><span class="sxs-lookup"><span data-stu-id="b6120-113">Exports</span></span>

<span data-ttu-id="b6120-114">Csak rendszergazdák konfigurálhatják az új kapcsolatokat, de hozzáférést adhatnak a munkatársaknak a meglévő kapcsolatok használatára.</span><span class="sxs-lookup"><span data-stu-id="b6120-114">Only administrators can configure new connections but they can grant access to contributors to use existing connections.</span></span> <span data-ttu-id="b6120-115">A rendszergazdák határozzák meg, hogy hová irányíthatják az adatokat, a munkatársak határozzák meg, hogy a hasznos adatok és a gyakoriság hogyan illeszkedjenek az igényekhez.</span><span class="sxs-lookup"><span data-stu-id="b6120-115">Administrators control where data can go, contributors define the payload and frequency fitting their needs.</span></span> <span data-ttu-id="b6120-116">További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](#allow-contributors-to-use-a-connection-for-exports).</span><span class="sxs-lookup"><span data-stu-id="b6120-116">For more information, see [Allow contributors to use a connection for exports](#allow-contributors-to-use-a-connection-for-exports).</span></span>

### <a name="enrichments"></a><span data-ttu-id="b6120-117">Bővítések</span><span class="sxs-lookup"><span data-stu-id="b6120-117">Enrichments</span></span>

<span data-ttu-id="b6120-118">Csak rendszergazdák konfigurálhatják az új kapcsolatokat, de a létrehozott kapcsolatok mindig elérhetők mind a rendszergazdák, mind a munkatársak számára.</span><span class="sxs-lookup"><span data-stu-id="b6120-118">Only administrators can configure new connections but the created connections are always available to both administrators and contributors.</span></span> <span data-ttu-id="b6120-119">A rendszergazdák kezelik az azonosító adatokat, és ők egyeznek bele az adatátvitelekbe.</span><span class="sxs-lookup"><span data-stu-id="b6120-119">Administrators manage credentials and give consent to data transfers.</span></span> <span data-ttu-id="b6120-120">A kapcsolatok ezután mind a rendszergazdák, mind a munkatársak általi bővítésekre használhatók.</span><span class="sxs-lookup"><span data-stu-id="b6120-120">The connections can then be used for enrichments by both administrators and contributors.</span></span>

## <a name="add-a-new-connection"></a><span data-ttu-id="b6120-121">Egy új kapcsolat hozzáadása</span><span class="sxs-lookup"><span data-stu-id="b6120-121">Add a new connection</span></span>

<span data-ttu-id="b6120-122">Kapcsolatok hozzáadásához [rendszergazdai engedélyekkel](permissions.md) kell rendelkeznie.</span><span class="sxs-lookup"><span data-stu-id="b6120-122">To add connections, you need to have [administrator permissions](permissions.md).</span></span> <span data-ttu-id="b6120-123">Ha más Microsoft-szolgáltatásokhoz kapcsolódik, akkor azt feltételezzük, hogy mindkét szolgáltatás ugyanabban a szervezetben van.</span><span class="sxs-lookup"><span data-stu-id="b6120-123">If you connect to other Microsoft services, we assume both services are in the same organization.</span></span>

1. <span data-ttu-id="b6120-124">Menjen a **Rendszergazda** > **Kapcsolatok (előzetes verzió)** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="b6120-124">Go to **Admin** > **Connections (preview)**.</span></span>

1. <span data-ttu-id="b6120-125">Menjen a **Kapcsolatok** fülre.</span><span class="sxs-lookup"><span data-stu-id="b6120-125">Go to the **Connections** tab.</span></span>

1. <span data-ttu-id="b6120-126">Új kapcsolat létrehozásához válassza a **Kapcsolat hozzáadása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="b6120-126">Select **Add connection** to create a new connection.</span></span> <span data-ttu-id="b6120-127">Válassza ki a legördülő menüből, hogy milyen típusú kapcsolatot kíván létrehozni.</span><span class="sxs-lookup"><span data-stu-id="b6120-127">Choose from the drop-down menu what type of connection you want to create.</span></span>

1. <span data-ttu-id="b6120-128">Adja meg a szükséges adatokat a **Kapcsolat beállítása** ablaktáblán.</span><span class="sxs-lookup"><span data-stu-id="b6120-128">In the **Set up connection** pane, provide the required details.</span></span> 
   1. <span data-ttu-id="b6120-129">A **Megjelenítendő név** és a kapcsolat típusa ír le egy kapcsolatot.</span><span class="sxs-lookup"><span data-stu-id="b6120-129">The **Display name** and the type of the connection describe a connection.</span></span> <span data-ttu-id="b6120-130">Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.</span><span class="sxs-lookup"><span data-stu-id="b6120-130">We recommend choosing a name that explains the purpose and target of this connection.</span></span>
   1. <span data-ttu-id="b6120-131">A pontos mezők attól függnek, hogy melyik szolgáltatáshoz kapcsolódik.</span><span class="sxs-lookup"><span data-stu-id="b6120-131">The exact fields depend on what service you are connecting to.</span></span> <span data-ttu-id="b6120-132">A specifikus kapcsolattípus részleteiről a célszolgáltatásról szóló cikk nyújt részletes információt.</span><span class="sxs-lookup"><span data-stu-id="b6120-132">You can learn about details of a specific connection type in the article about the target service.</span></span>

1. <span data-ttu-id="b6120-133">A kapcsolat létrehozásához válassza a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="b6120-133">To create the connection, select **Save**.</span></span>

<span data-ttu-id="b6120-134">A **Beállítás** lehetőséget is választhatja egy mozaikon a **Felderítés** lapon.</span><span class="sxs-lookup"><span data-stu-id="b6120-134">You can also select **Set up** on a tile on the **Discover** tab.</span></span>

### <a name="allow-contributors-to-use-a-connection-for-exports"></a><span data-ttu-id="b6120-135">Engedélyezze a közreműködőknek a kapcsolat exportálásokhoz való használatát</span><span class="sxs-lookup"><span data-stu-id="b6120-135">Allow contributors to use a connection for exports</span></span>

<span data-ttu-id="b6120-136">Az exportálási kapcsolat beállításakor és módosításakor megadhatja, hogy mely felhasználók használhatjak ezt a konkrét kapcsolatot az [exportálások](export-destinations.md) meghatározásához.</span><span class="sxs-lookup"><span data-stu-id="b6120-136">When setting up or editing an export connection, you choose which users are allowed to use this specific connection to define [exports](export-destinations.md).</span></span> <span data-ttu-id="b6120-137">Alapértelmezés szerint a rendszergazdai szerepkörrel rendelkező felhasználók számára érhető el a kapcsolat.</span><span class="sxs-lookup"><span data-stu-id="b6120-137">By default a connection is available to users with an administrator role.</span></span> <span data-ttu-id="b6120-138">Ezt a beállítást a **Válassza ki, hogy ki használhatja ezt a kapcsolatot** lehetőség alatt tudja megváltoztatni, és engedélyezheti a közreműködő szerepkörrel rendelkező felhasználóknak, hogy használják ezt a kapcsolatot.</span><span class="sxs-lookup"><span data-stu-id="b6120-138">You can change this setting under **Choose who can use this connection** and allow users with contributor role to use this connection.</span></span>

- <span data-ttu-id="b6120-139">A közreműködő nem tudják majd megtekinteni vagy szerkeszteni ezt a kapcsolatot.</span><span class="sxs-lookup"><span data-stu-id="b6120-139">Contributors won't be able to view or edit the connection.</span></span> <span data-ttu-id="b6120-140">Exportálás létrehozásakor csak a megjelenítendő név adatokat és azok típusát látják.</span><span class="sxs-lookup"><span data-stu-id="b6120-140">They will only see the display name and its type when creating an export.</span></span>
- <span data-ttu-id="b6120-141">A kapcsolat megosztásával lehetővé teszi a közreműködők számára a kapcsolat használatát.</span><span class="sxs-lookup"><span data-stu-id="b6120-141">By sharing a connection, you allow contributors to use a connection.</span></span> <span data-ttu-id="b6120-142">A közreműködő a megosztott kapcsolatokat láthatják az exportálások beállításakor.</span><span class="sxs-lookup"><span data-stu-id="b6120-142">Contributors will see shared connections when they set up exports.</span></span> <span data-ttu-id="b6120-143">Ők felügyelik az adott kapcsolatot használó minden exportálást.</span><span class="sxs-lookup"><span data-stu-id="b6120-143">They can manage every export that uses this specific connection.</span></span>
- <span data-ttu-id="b6120-144">Ezt a beállítást megváltoztathatja, miközben a közreműködők által már meghatározott exportálásokat megtartja.</span><span class="sxs-lookup"><span data-stu-id="b6120-144">You can change this setting while keeping the exports that have already been defined by contributors.</span></span>

## <a name="edit-a-connection"></a><span data-ttu-id="b6120-145">Kapcsolat szerkesztése</span><span class="sxs-lookup"><span data-stu-id="b6120-145">Edit a connection</span></span>

1. <span data-ttu-id="b6120-146">Menjen a **Rendszergazda** > **Kapcsolatok (előzetes verzió)** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="b6120-146">Go to **Admin** > **Connections (preview)**.</span></span>

1. <span data-ttu-id="b6120-147">Menjen a **Kapcsolatok** fülre.</span><span class="sxs-lookup"><span data-stu-id="b6120-147">Go to the **Connections** tab.</span></span>

1. <span data-ttu-id="b6120-148">Jelölje ki a szerkeszteni kívánt kapcsolat függőleges három pontját.</span><span class="sxs-lookup"><span data-stu-id="b6120-148">Select the vertical ellipsis for the connection you want to edit.</span></span>

1. <span data-ttu-id="b6120-149">Válassza a **Szerkesztés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="b6120-149">Select **Edit**.</span></span>

1. <span data-ttu-id="b6120-150">Módosítsa a frissíteni kívánt értékeket, majd válassza a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="b6120-150">Change the values you want to update and select **Save**.</span></span>

## <a name="remove-a-connection"></a><span data-ttu-id="b6120-151">Kapcsolat eltávolítása</span><span class="sxs-lookup"><span data-stu-id="b6120-151">Remove a connection</span></span>

<span data-ttu-id="b6120-152">Ha az eltávolítandó kapcsolatot bővítések vagy exportálások használják, előbb szét kell őket kapcsolni, vagy el kell távolítani.</span><span class="sxs-lookup"><span data-stu-id="b6120-152">If the connection you are removing is used by enrichments or exports, you first need to detach or remove them.</span></span> <span data-ttu-id="b6120-153">Az eltávolítási párbeszédpanel útmutatást nyújt a megfelelő bővítésekhez vagy exportálásokhoz.</span><span class="sxs-lookup"><span data-stu-id="b6120-153">The remove dialog will guide you to the relevant enrichments or exports.</span></span> <span data-ttu-id="b6120-154">A szétkapcsolt bővítések és exportálások inaktívvá válnak.</span><span class="sxs-lookup"><span data-stu-id="b6120-154">Detached enrichments and exports become inactive.</span></span> <span data-ttu-id="b6120-155">Újraaktiválhatja őket, ha új kapcsolatot ad hozzájuk a [Bővítések](enrichment-hub.md) és [Exportálások](export-destinations.md) oldalon.</span><span class="sxs-lookup"><span data-stu-id="b6120-155">You reactivate them by adding another connection to them on the [Enrichments](enrichment-hub.md) or [Exports](export-destinations.md) page.</span></span>

1. <span data-ttu-id="b6120-156">Menjen a **Rendszergazda** > **Kapcsolatok (előzetes verzió)** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="b6120-156">Go to **Admin** > **Connections (preview)**.</span></span>

1. <span data-ttu-id="b6120-157">Menjen a **Kapcsolatok** fülre.</span><span class="sxs-lookup"><span data-stu-id="b6120-157">Go to the **Connections** tab.</span></span>

1. <span data-ttu-id="b6120-158">Jelölje ki az eltávolítani kívánt kapcsolat függőleges három pontját.</span><span class="sxs-lookup"><span data-stu-id="b6120-158">Select the vertical ellipsis for the connection you want to remove.</span></span>

1. <span data-ttu-id="b6120-159">Válassza a legördülő menü **Eltávolítás** elemét.</span><span class="sxs-lookup"><span data-stu-id="b6120-159">Select **Remove** from the dropdown menu.</span></span> <span data-ttu-id="b6120-160">Megjelenik a jóváhagyást kérő párbeszéd.</span><span class="sxs-lookup"><span data-stu-id="b6120-160">A confirmation dialog appears.</span></span>

   1. <span data-ttu-id="b6120-161">Ha ezt a kapcsolatot bővítések vagy exportálások használják, akkor a gombra kattintva láthatja, hogy pontosan mi használja a kapcsolatot.</span><span class="sxs-lookup"><span data-stu-id="b6120-161">If there are enrichments or exports using this connection, select the button to see what's using the connection.</span></span>
      - <span data-ttu-id="b6120-162">**Exportálások**: Kiválaszthatja az exportálás eltávolítását vagy bontását, hogy el tudja távolítani a kapcsolatot.</span><span class="sxs-lookup"><span data-stu-id="b6120-162">**Exports:** You can choose to either remove or disconnect the exports to be able to remove the connection.</span></span> <span data-ttu-id="b6120-163">Az exportálás bontása érdekében a rendszergazdák a **Szétkapcsolás** műveletet használhatják.</span><span class="sxs-lookup"><span data-stu-id="b6120-163">To disconnect an export, administrators can use the **Disconnect** action.</span></span> <span data-ttu-id="b6120-164">Ez a művelet egyéni és több kijelölt exportáláshoz is elérhető.</span><span class="sxs-lookup"><span data-stu-id="b6120-164">This action is available for individual and multiple selected exports.</span></span> <span data-ttu-id="b6120-165">A kapcsolat szétkapcsolása megtartja az exportálási konfigurációs adatokat, de az mindaddig nem fut, amíg hozzá nem ad egy másik kapcsolatot.</span><span class="sxs-lookup"><span data-stu-id="b6120-165">By disconnecting you keep the export config, but it won't be run until another connection is added to it.</span></span>
      - <span data-ttu-id="b6120-166">**Bővítések:** Kiválaszthatja a bővítések eltávolítását vagy inaktiválását, hogy el tudja távolítani a kapcsolatot.</span><span class="sxs-lookup"><span data-stu-id="b6120-166">**Enrichments:** You can choose to either remove or deactivate the enrichments to be able to remove the connection.</span></span> 
   1. <span data-ttu-id="b6120-167">Ha a kapcsolatnak már nincsenek függőségei, menjen vissza a **Rendszergazda** > **Kapcsolatok** lehetőséghez, és próbálja meg ismét eltávolítani a kapcsolatot.</span><span class="sxs-lookup"><span data-stu-id="b6120-167">Once the connection has no more dependencies, go back to **Admin** > **Connections** and try removing the connection again.</span></span>

1. <span data-ttu-id="b6120-168">Jelölje be az **Eltávolítás** lehetőséget a törlés megerősítéséhez.</span><span class="sxs-lookup"><span data-stu-id="b6120-168">To confirm the deletion select **Remove**.</span></span>

