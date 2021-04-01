---
title: Adatok betöltése Power Query összekötőn keresztül
description: Összekötők Power Query alapú adatforrásokhoz.
ms.date: 09/29/2020
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: adkuppa
ms.author: adkuppa
manager: shellyha
ms.openlocfilehash: b9a1b30e37c3792aa7bdfcfc177da9e8a32c324d
ms.sourcegitcommit: bae40184312ab27b95c140a044875c2daea37951
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/15/2021
ms.locfileid: "5596916"
---
# <a name="connect-to-a-power-query-data-source"></a><span data-ttu-id="14e43-103">Csatlakozás Power Queryhoz adatforráshoz</span><span class="sxs-lookup"><span data-stu-id="14e43-103">Connect to a Power Query data source</span></span>

<span data-ttu-id="14e43-104">A Power Query a csatlakozók széles körét biztosítja az adatok betöltéséhez.</span><span class="sxs-lookup"><span data-stu-id="14e43-104">Power Query offers a broad set of connectors to ingest data.</span></span> <span data-ttu-id="14e43-105">A legtöbb ilyen csatlakozót a támogatja Dynamics 365 Customer Insights.</span><span class="sxs-lookup"><span data-stu-id="14e43-105">Most of these connectors are supported by Dynamics 365 Customer Insights.</span></span> <span data-ttu-id="14e43-106">Power Query csatlakozón alapuló adatforrások hozzáadása általában a következő szakaszban leírt lépéseket követi.</span><span class="sxs-lookup"><span data-stu-id="14e43-106">Adding data sources based on Power Query connectors generally follows the steps outlined in the next section.</span></span> <span data-ttu-id="14e43-107">A használt csatlakozótól függően azonban eltérő információra van szükség.</span><span class="sxs-lookup"><span data-stu-id="14e43-107">However, depending on the connector you use, different information is required.</span></span> <span data-ttu-id="14e43-108">További információkért tekintse meg az egyes összekötők dokumentációját a [Power Query-összekötő referencia](/power-query/connectors/).</span><span class="sxs-lookup"><span data-stu-id="14e43-108">For more information, see the documentation about individual connectors in the [Power Query connector reference](/power-query/connectors/).</span></span>

## <a name="create-a-new-data-source"></a><span data-ttu-id="14e43-109">Új adatforrás létrehozása</span><span class="sxs-lookup"><span data-stu-id="14e43-109">Create a new data source</span></span>

1. <span data-ttu-id="14e43-110">A célközönség információin belül nyissa meg a következőt **Adatok** > **Adatforrások**.</span><span class="sxs-lookup"><span data-stu-id="14e43-110">In audience insights, go to **Data** > **Data sources**.</span></span>

1. <span data-ttu-id="14e43-111">Válassza az **Adatforrás hozzáadása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="14e43-111">Select **Add data source**.</span></span>

1. <span data-ttu-id="14e43-112">Válassza az **Adatok importálása** módszert, és válassza a **Tovább** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="14e43-112">Choose the **Import data** method and select **Next**.</span></span>

1. <span data-ttu-id="14e43-113">Adja meg a adatforrás **Nevét**, majd válassza a **Következő** lehetőséget a adatforrás létrehozásához.</span><span class="sxs-lookup"><span data-stu-id="14e43-113">Provide a **Name** for the data source, and select **Next** to create the data source.</span></span> <span data-ttu-id="14e43-114">Névvel kapcsolatos irányelvek:</span><span class="sxs-lookup"><span data-stu-id="14e43-114">Name guidelines:</span></span> 
   - <span data-ttu-id="14e43-115">Kezdje egy betűvel.</span><span class="sxs-lookup"><span data-stu-id="14e43-115">Start with a letter.</span></span>
   - <span data-ttu-id="14e43-116">Csak betűket és számokat használjon.</span><span class="sxs-lookup"><span data-stu-id="14e43-116">Use letters and numbers only.</span></span> <span data-ttu-id="14e43-117">Speciális karakterek és szóközök nem adhatók meg.</span><span class="sxs-lookup"><span data-stu-id="14e43-117">Special characters and spaces are not allowed.</span></span>
   - <span data-ttu-id="14e43-118">3–64 karakter használható.</span><span class="sxs-lookup"><span data-stu-id="14e43-118">Use between 3 and 64 characters.</span></span>

1. <span data-ttu-id="14e43-119">Válassza ki az egyik [elérhető csatlakozót](#available-power-query-data-sources).</span><span class="sxs-lookup"><span data-stu-id="14e43-119">Choose one of the [available connectors](#available-power-query-data-sources).</span></span> <span data-ttu-id="14e43-120">Ebben a példában a **Szöveg/CSV** összekötőt választjuk.</span><span class="sxs-lookup"><span data-stu-id="14e43-120">For this example, we select the **Text/CSV** connector.</span></span>

1. <span data-ttu-id="14e43-121">Adja meg a kijelölt összekötő **Kapcsolati beállításaiban** a szükséges adatokat, és az adatok előnézetének megtekintéséhez válassza a **Tovább** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="14e43-121">Enter the required details in the **Connection settings** for the selected connector and select **Next** to see a preview of the data.</span></span>

1. <span data-ttu-id="14e43-122">Válassza az **Adatok átalakítása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="14e43-122">Select **Transform data**.</span></span> <span data-ttu-id="14e43-123">Ebben a lépésben entitásokat ad hozzá az adatforráshoz.</span><span class="sxs-lookup"><span data-stu-id="14e43-123">In this step, you'll add entities to your data source.</span></span> <span data-ttu-id="14e43-124">Az entitások adatkészletek.</span><span class="sxs-lookup"><span data-stu-id="14e43-124">Entities are datasets.</span></span> <span data-ttu-id="14e43-125">Ha olyan adatbázissal rendelkezik, amely több adathalmazt tartalmaz, akkor mindegyik adathalmazhoz saját entitás tartozik.</span><span class="sxs-lookup"><span data-stu-id="14e43-125">If you have a database that includes multiple datasets, each dataset is its own entity.</span></span>

1. <span data-ttu-id="14e43-126">A **Power Query – Lekérdezések szerkesztése** párbeszédpanel lehetővé teszi az adatok áttekintését és finomítását.</span><span class="sxs-lookup"><span data-stu-id="14e43-126">The **Power Query - Edit queries** dialog lets you review and refine the data.</span></span> <span data-ttu-id="14e43-127">Az entitások, amelyekkel a rendszerek a kijelölt adatforrásban azonosítottak megjelennek a bal ablaktáblában.</span><span class="sxs-lookup"><span data-stu-id="14e43-127">The entities that the systems identified in your selected data source appear in the left pane.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="14e43-128">![Lekérdezések szerkesztése párbeszédpanel](media/data-manager-configure-edit-queries.png "Lekérdezések szerkesztése párbeszédpanel")</span><span class="sxs-lookup"><span data-stu-id="14e43-128">![Edit queries dialog](media/data-manager-configure-edit-queries.png "Edit queries dialog")</span></span>

1. <span data-ttu-id="14e43-129">Át is alakíthatja adatait.</span><span class="sxs-lookup"><span data-stu-id="14e43-129">You can also transform your data.</span></span> <span data-ttu-id="14e43-130">Jelöljön ki egy módosítani vagy átalakítani kívánt entitást.</span><span class="sxs-lookup"><span data-stu-id="14e43-130">Select an entity to edit or transform.</span></span> <span data-ttu-id="14e43-131">Az átalakítások alkalmazásához használja a Power Query ablak beállításait.</span><span class="sxs-lookup"><span data-stu-id="14e43-131">Use the options in the Power Query window to apply transformations.</span></span> <span data-ttu-id="14e43-132">Minden átalakítás az **Alkalmazott lépések** területen jelenik meg.</span><span class="sxs-lookup"><span data-stu-id="14e43-132">Each transformation gets listed under **Applied steps**.</span></span> <span data-ttu-id="14e43-133">A Power Query számos előre elkészített átalakítási beállítást biztosít.</span><span class="sxs-lookup"><span data-stu-id="14e43-133">Power Query provides numerous pre-built transformation options.</span></span> <span data-ttu-id="14e43-134">További információ: [Power Query átalakítások](/power-query/power-query-what-is-power-query#transformations).</span><span class="sxs-lookup"><span data-stu-id="14e43-134">For more information, see [Power Query Transformations](/power-query/power-query-what-is-power-query#transformations).</span></span>

1. <span data-ttu-id="14e43-135">A adatforráshoz további entitások hozzáadásához válassza az **Adatok beolvasása** elemet a **Lekérdezések szerkesztése** párbeszédpanelen.</span><span class="sxs-lookup"><span data-stu-id="14e43-135">You can add additional entities to your data source by selecting **Get data** in the **Edit queries** dialog.</span></span>

   <span data-ttu-id="14e43-136">Ezek az átalakítások erősen ajánlottak:</span><span class="sxs-lookup"><span data-stu-id="14e43-136">These transformations are highly recommended:</span></span>

   - <span data-ttu-id="14e43-137">Ha egy CSV-fájlból tölti be az adatokat, az első sor gyakran tartalmaz fejléceket.</span><span class="sxs-lookup"><span data-stu-id="14e43-137">If you're ingesting data from a CSV file, the first row often contains headers.</span></span> <span data-ttu-id="14e43-138">Nyissa meg a **Tábla átalakítása** elemet, és válassza **Fejlécek használata első sorként** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="14e43-138">Go to **Transform table** and select **Use headers as first row**.</span></span>
   - <span data-ttu-id="14e43-139">Ügyeljen arra, hogy az adattípus megfelelően legyen beállítva.</span><span class="sxs-lookup"><span data-stu-id="14e43-139">Ensure the data type is set appropriately.</span></span>

1. <span data-ttu-id="14e43-140">Az átalakítások elmentéséhez válassza a Power Query ablak alján lévő **Mentés** gombot.</span><span class="sxs-lookup"><span data-stu-id="14e43-140">Select **Save** at the bottom of the Power Query window to save the transformations.</span></span> <span data-ttu-id="14e43-141">A mentést követően az adatforrást az **Adatok** > **Adatforrások** helyen találja.</span><span class="sxs-lookup"><span data-stu-id="14e43-141">After saving, you'll find your data source on **Data** > **Data sources**.</span></span>

1. <span data-ttu-id="14e43-142">Az **Adatforrások** lapon látja, hogy az új adatforrás a **Frissítés** állapotában van.</span><span class="sxs-lookup"><span data-stu-id="14e43-142">On the **Data sources** page, you'll notice the new data source is in **Refreshing** status.</span></span>

## <a name="available-power-query-data-sources"></a><span data-ttu-id="14e43-143">Rendelkezésre álló Power Query-adatforrások</span><span class="sxs-lookup"><span data-stu-id="14e43-143">Available Power Query data sources</span></span>

<span data-ttu-id="14e43-144">Tekintse meg a [Power Query-összekötő referencia](/power-query/connectors/) dokumentumot azon összekötők listájának megjelenítéséhez, amelyeket kiválaszthat adatok importálásához a Customer Insights alkalmazásba.</span><span class="sxs-lookup"><span data-stu-id="14e43-144">See the [Power Query connector reference](/power-query/connectors/) for an up-to-date list of connectors that you can select to import data to Customer Insights.</span></span> 

<span data-ttu-id="14e43-145">Azok az összekötők, amelyeknél a **Customer Insights (adatfolyamok)** oszlopában egy pipa látható érhetők el új adatforrások létrehozásához a Power Query-re építve.</span><span class="sxs-lookup"><span data-stu-id="14e43-145">Connectors with a checkmark in the **Customer Insights (Dataflows)** column are available to create new data sources based on Power Query.</span></span> <span data-ttu-id="14e43-146">Egy adott csatlakozó dokumentációjának áttekintésével többet megtudhat az előfeltételekről, a korlátozásokról és egyéb részletekről.</span><span class="sxs-lookup"><span data-stu-id="14e43-146">Review the documentation of a specific connector to learn more about its prerequisites, limitations, and other details.</span></span>

## <a name="edit-power-query-data-sources"></a><span data-ttu-id="14e43-147">Power Query-adatforrások szerkesztése</span><span class="sxs-lookup"><span data-stu-id="14e43-147">Edit Power Query data sources</span></span>

> [!NOTE]
> <span data-ttu-id="14e43-148">Előfordulhat, hogy az alkalmazás egyik folyamatában (például *szegmentálás*, *egyeztetés* vagy *egyesítés*) jelenleg használt adatforrások nem módosíthatók.</span><span class="sxs-lookup"><span data-stu-id="14e43-148">It might not be possible to make changes to data sources that are currently being used in one of the app's processes (*segmentation*, *match*, or *merge*, for example).</span></span> 
>
> <span data-ttu-id="14e43-149">A **Beállítások** oldal használatával nyomon követheti az egyes aktív folyamatok állapotát.</span><span class="sxs-lookup"><span data-stu-id="14e43-149">Using the **Settings** page, you can track the progress of each of the active processes.</span></span> <span data-ttu-id="14e43-150">A folyamat befejeződésekor visszaléphet az **Adatforrások** lapra, és elvégezheti a változtatásokat.</span><span class="sxs-lookup"><span data-stu-id="14e43-150">When a process completes, you can return to the **Data Sources** page and make your changes.</span></span>

1. <span data-ttu-id="14e43-151">A célközönség információin belül nyissa meg a következőt **Adatok** > **Adatforrások**.</span><span class="sxs-lookup"><span data-stu-id="14e43-151">In audience insights, go to **Data** > **Data sources**.</span></span>

2. <span data-ttu-id="14e43-152">Jelölje ki a módosítani kívánt adatforrás melletti függőleges három pontot, és a legördülő menüben válassza a **Szerkesztés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="14e43-152">Select the vertical ellipsis next to the data source you want to change and select **Edit** from the drop-down menu.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="14e43-153">![Szerkesztés lehetőség](media/edit-option-data-sources.png "Szerkesztés lehetőség")</span><span class="sxs-lookup"><span data-stu-id="14e43-153">![Edit option](media/edit-option-data-sources.png "Edit option")</span></span>

3. <span data-ttu-id="14e43-154">Alkalmazza a változtatásokat és az átalakításokat az **Power Query - Lekérdezések szerkesztése** párbeszédpanelen az [Új adatforrás létrehozása](#create-a-new-data-source) című részben leírtak szerint.</span><span class="sxs-lookup"><span data-stu-id="14e43-154">Apply your changes and transformations in the **Power Query - Edit queries** dialog as described in the [Create a new data source](#create-a-new-data-source) section.</span></span>

4. <span data-ttu-id="14e43-155">A változtatások mentéséhez a módosítások elvégzése után válassza a **Mentés** lehetőséget a Power Query-ben.</span><span class="sxs-lookup"><span data-stu-id="14e43-155">Select **Save** in Power Query after completing your edits to save your changes.</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]