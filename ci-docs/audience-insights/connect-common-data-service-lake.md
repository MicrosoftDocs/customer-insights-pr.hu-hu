---
title: Entitások összekapcsolása a Common Data Service felügyelt tóhoz
description: Adatok importálása Common Data Service felügyelt adattóből.
ms.date: 09/29/2020
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.reviewer: adkuppa
ms.openlocfilehash: 18b6cd3fdaf5b738877a73b520b91dbc6ded40de
ms.sourcegitcommit: 139548f8a2d0f24d54c4a6c404a743eeeb8ef8e0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/15/2021
ms.locfileid: "5267817"
---
# <a name="connect-to-data-in-a-common-data-service-managed-data-lake"></a><span data-ttu-id="d2f4f-103">Kapcsolódás az adatokhoz egy Common Data Service felügyelt adattóban</span><span class="sxs-lookup"><span data-stu-id="d2f4f-103">Connect to data in a Common Data Service managed data lake</span></span>

[!INCLUDE [cc-data-platform-banner](../includes/cc-data-platform-banner.md)]

<span data-ttu-id="d2f4f-104">A cikkből megtudhatja, hogy a meglévő Dynamics 365-ügyfelek hogyan tudnak gyorsan kapcsolódni az analitikus entitásokhoz a Common Data Service felügyelt adattóban.</span><span class="sxs-lookup"><span data-stu-id="d2f4f-104">This article provides information on how existing Dynamics 365 customers can quickly connect to their analytical entities in the Common Data Service managed lake.</span></span> <span data-ttu-id="d2f4f-105">A Common Data Service szervezet rendszergazdájának kell lennie ahhoz, hogy folytathassa, és megtekintse a felügyelt tóban elérhető entitások listáját.</span><span class="sxs-lookup"><span data-stu-id="d2f4f-105">You must be an admin on the Common Data Service organization to proceed and see the list of entities available in the managed lake.</span></span>

## <a name="important-considerations"></a><span data-ttu-id="d2f4f-106">Fontos tényezők</span><span class="sxs-lookup"><span data-stu-id="d2f4f-106">Important considerations</span></span>

<span data-ttu-id="d2f4f-107">Az online szolgáltatásokban, például az Azure Data Lake Storage esetében tárolt adatok az adatok feldolgozásának vagy tárolásának helyétől eltérő helyen tárolhatók, vagy a Dynamics 365 Customer Insights megoldásban is tárolhatók.</span><span class="sxs-lookup"><span data-stu-id="d2f4f-107">Data stored in online services, such as Azure Data Lake Storage, may be stored in a different location than where data is processed or stored in Dynamics 365 Customer Insights.</span></span><span data-ttu-id="d2f4f-108"> Az online szolgáltatásokban tárolt adatok importálásával vagy az ahhoz való kapcsolódással Ön elfogadja, hogy az adatok átvihetők és tárolhatók a Dynamics 365 Customer Insights alkalmazásban.  [Ismerje meg a Microsoft adatvédelmi központot](https://www.microsoft.com/trust-center)</span><span class="sxs-lookup"><span data-stu-id="d2f4f-108"> By importing or connecting to data stored in online services, you agree that data can be transferred to and stored with Dynamics 365 Customer Insights. [Learn more at the Microsoft Trust Center.](https://www.microsoft.com/trust-center)</span></span>

## <a name="connect-to-a-common-data-service-managed-lake"></a><span data-ttu-id="d2f4f-109">Csatlakozás egy Common Data Service felügyelt tóhoz</span><span class="sxs-lookup"><span data-stu-id="d2f4f-109">Connect to a Common Data Service managed lake</span></span>

1. <span data-ttu-id="d2f4f-110">A célközönség információin belül nyissa meg a következőt **Adatok** > **Adatforrások**.</span><span class="sxs-lookup"><span data-stu-id="d2f4f-110">In audience insights, go to **Data** > **Data sources**.</span></span>

2. <span data-ttu-id="d2f4f-111">Válassza az **Adatforrás hozzáadása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="d2f4f-111">Select **Add data source**.</span></span>

3. <span data-ttu-id="d2f4f-112">Válassza a **Kapcsolódás a Common Data Service szolgáltatáshoz** lehetőséget, majd válassza a **Következő** elemet.</span><span class="sxs-lookup"><span data-stu-id="d2f4f-112">Select **Connect to Common Data Service** and select **Next**.</span></span>

4. <span data-ttu-id="d2f4f-113">Adjon meg egy **Nevet** az adatforrás számára, majd válassza a **Tovább** elemet.</span><span class="sxs-lookup"><span data-stu-id="d2f4f-113">Enter a **Name** for the data source and select **Next**.</span></span> <span data-ttu-id="d2f4f-114">Névvel kapcsolatos irányelvek:</span><span class="sxs-lookup"><span data-stu-id="d2f4f-114">Name guidelines:</span></span> 
   - <span data-ttu-id="d2f4f-115">Kezdje egy betűvel.</span><span class="sxs-lookup"><span data-stu-id="d2f4f-115">Start with a letter.</span></span>
   - <span data-ttu-id="d2f4f-116">Csak betűket és számokat használjon.</span><span class="sxs-lookup"><span data-stu-id="d2f4f-116">Use letters and numbers only.</span></span> <span data-ttu-id="d2f4f-117">Speciális karakterek és szóközök nem adhatók meg.</span><span class="sxs-lookup"><span data-stu-id="d2f4f-117">Special characters and spaces are not allowed.</span></span>
   - <span data-ttu-id="d2f4f-118">3–64 karakter használható.</span><span class="sxs-lookup"><span data-stu-id="d2f4f-118">Use between 3 and 64 characters.</span></span>

5. <span data-ttu-id="d2f4f-119">Adja meg a **Kiszolgáló címét** a Common Data Service szervezet számára , és válassza a **Bejelentkezés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="d2f4f-119">Provide the **Server address** for your Common Data Service organization, and select **Sign in**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="d2f4f-120">![A kiszolgáló Common Data Service kiszolgáló címének megadására szolgáló párbeszédpanel](media/enter-CDS-org-details.png)</span><span class="sxs-lookup"><span data-stu-id="d2f4f-120">![Dialog box to enter Common Data Service server address](media/enter-CDS-org-details.png)</span></span>

6. <span data-ttu-id="d2f4f-121">Jelölje ki a betölteni kívánt entitásokat az elérhető listán.</span><span class="sxs-lookup"><span data-stu-id="d2f4f-121">Select the entities you want to ingest from the available list.</span></span>    

   > [!NOTE]
   > <span data-ttu-id="d2f4f-122">Ha bizonyos entitások már ki vannak jelölve, akkor más Dynamics 365 alkalmazások (például a Dynamics 365 Sales Insights vagy a Customer Service Insights) esetleg már használják.</span><span class="sxs-lookup"><span data-stu-id="d2f4f-122">If some entities are already selected, they might be used by other Dynamics 365 applications (such as Dynamics 365 Sales Insights or Customer Service Insights).</span></span> <span data-ttu-id="d2f4f-123">Ez a kijelölés nem módosítható.</span><span class="sxs-lookup"><span data-stu-id="d2f4f-123">You can't change the selection.</span></span> <span data-ttu-id="d2f4f-124">Ezek az entitások a adatforrás létrehozása után lesznek elérhetők.</span><span class="sxs-lookup"><span data-stu-id="d2f4f-124">These entities will be available once the data source is created.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="d2f4f-125">![Párbeszédpanel az entitások listáját mutatja a Common Data Service szervezeten belül](media/select-analytical-entities.png)</span><span class="sxs-lookup"><span data-stu-id="d2f4f-125">![Dialog box showing a list of entities in the Common Data Service org](media/select-analytical-entities.png)</span></span>

7. <span data-ttu-id="d2f4f-126">Mentse a kijelölést, és indítsa el a kijelölt entitások szinkronizálását a Common Data Service felügyelt tóba.</span><span class="sxs-lookup"><span data-stu-id="d2f4f-126">Save your selection to start syncing the selected entities to the Common Data Service managed lake.</span></span> <span data-ttu-id="d2f4f-127">Az újonnan felvett kapcsolatot az **Adatforrások** lapon találja.</span><span class="sxs-lookup"><span data-stu-id="d2f4f-127">You'll find the newly added connection on the **Data sources** page.</span></span> <span data-ttu-id="d2f4f-128">Ütemezve lesz frissítésre, és az entitások számam 0 lesz, amíg az összes entitás szinkronizálása meg nem történik.</span><span class="sxs-lookup"><span data-stu-id="d2f4f-128">It will be queued for refresh and show the entities count as 0 until all the entities are synced.</span></span>

<span data-ttu-id="d2f4f-129">Csak egy környezethez tartozó adatforrás használhatja a egyszerre ugyanazt a Common Data Service felügyelt tavat.</span><span class="sxs-lookup"><span data-stu-id="d2f4f-129">Only one data source of an environment can simultaneously use the same Common Data Service managed lake.</span></span>

## <a name="edit-a-common-data-service-managed-lake-data-source"></a><span data-ttu-id="d2f4f-130">Egy Common Data Service felügyelt tó adatforrásának szerkesztése</span><span class="sxs-lookup"><span data-stu-id="d2f4f-130">Edit a Common Data Service managed lake data source</span></span>

<span data-ttu-id="d2f4f-131">Az entitások kijelölését csak az adatforrás létrehozása után módosíthatja.</span><span class="sxs-lookup"><span data-stu-id="d2f4f-131">You only edit the entity selection after creating the data source.</span></span> <span data-ttu-id="d2f4f-132">Ha például további entitásokat adtak hozzá a Common Data Service szolgáltatáshoz, és azokat is importálni kívánja.</span><span class="sxs-lookup"><span data-stu-id="d2f4f-132">For example, if additional entities were added to Common Data Service and you want to import them too.</span></span>    
<span data-ttu-id="d2f4f-133">A kapcsolódáshoz egy másik Common Data Service szolgáltatáshoz [hozzon létre egy újadatforrást](#connect-to-a-common-data-service-managed-lake).</span><span class="sxs-lookup"><span data-stu-id="d2f4f-133">To connect to a different Common Data Service, [create a new data source](#connect-to-a-common-data-service-managed-lake).</span></span>

1. <span data-ttu-id="d2f4f-134">A célközönség információin belül nyissa meg a következőt **Adatok** > **Adatforrások**.</span><span class="sxs-lookup"><span data-stu-id="d2f4f-134">In audience insights, go to **Data** > **Data sources**.</span></span>

2. <span data-ttu-id="d2f4f-135">A frissíteni kívánt adatforrás mellett jelölje ki a három pontot.</span><span class="sxs-lookup"><span data-stu-id="d2f4f-135">Next to the data source you'd like to update, select the ellipsis.</span></span>

3. <span data-ttu-id="d2f4f-136">Válassza a lista **Szerkesztés** elemét.</span><span class="sxs-lookup"><span data-stu-id="d2f4f-136">Select the **Edit** option from the list.</span></span>

4. <span data-ttu-id="d2f4f-137">Jelöljön ki további entitásokat a rendelkezésre álló entitások listájából, és válassza a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="d2f4f-137">Select additional entities from the available list of entities and select **Save**.</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]