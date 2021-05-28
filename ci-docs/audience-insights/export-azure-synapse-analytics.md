---
title: Customer Insights-adatok exportálása az Azure Synapse Analytics rendszerbe
description: Ismerje meg, hogyan konfigurálhatja az Azure Synapse Analytics rendszerrel kiépített kapcsolatot.
ms.date: 04/12/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: stefanie-msft
ms.author: sthe
manager: shellyha
ms.openlocfilehash: 822082d661863e737ea3d3a749a6c878db766967
ms.sourcegitcommit: e8e03309ba2515374a70c132d0758f3e1e1851d0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/04/2021
ms.locfileid: "5977380"
---
# <a name="export-data-to-azure-synapse-analytics-preview"></a><span data-ttu-id="c92b9-103">Aadtok exportálása az Azure Synapse Analytics rendszerbe (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="c92b9-103">Export data to Azure Synapse Analytics (Preview)</span></span>

<span data-ttu-id="c92b9-104">Az Azure Synapse olyan elemzőszolgáltatás, amellyel gyorsabban áttekinthetők az adattárhházakban és a nagy adatrendszerekben lévő adatok.</span><span class="sxs-lookup"><span data-stu-id="c92b9-104">Azure Synapse is an analytics service that accelerates time to insight across data warehouses and big data systems.</span></span> <span data-ttu-id="c92b9-105">A Customer Insights-adatok betölthetők az [Azure Synapse](/azure/synapse-analytics/overview-what-is) rendszerbe, és használhatók ott.</span><span class="sxs-lookup"><span data-stu-id="c92b9-105">You can ingest and use your Customer Insights data in [Azure Synapse](/azure/synapse-analytics/overview-what-is).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c92b9-106">Előfeltételek</span><span class="sxs-lookup"><span data-stu-id="c92b9-106">Prerequisites</span></span>

<span data-ttu-id="c92b9-107">A Customer Insights és az Azure Synapse közötti kapcsolat konfigurálásához a következő előfeltételeknek kell teljesülnie.</span><span class="sxs-lookup"><span data-stu-id="c92b9-107">The following prerequisites must be met to configure the connection from Customer Insights to Azure Synapse.</span></span>

> [!NOTE]
> <span data-ttu-id="c92b9-108">A leírt módon állítsa be az összes **szerepkör-hozzárendelést**.</span><span class="sxs-lookup"><span data-stu-id="c92b9-108">Make sure to set all **role assignments** as described.</span></span>  

## <a name="prerequisites-in-customer-insights"></a><span data-ttu-id="c92b9-109">Előfeltételek a Customer Insights szolgáltatásban</span><span class="sxs-lookup"><span data-stu-id="c92b9-109">Prerequisites in Customer Insights</span></span>

* <span data-ttu-id="c92b9-110">**Rendszergazda** szerepkörrel kell rendelkezni a célközönség betekintési információihoz.</span><span class="sxs-lookup"><span data-stu-id="c92b9-110">You have an **Administrator** role in audience insights.</span></span> <span data-ttu-id="c92b9-111">További információ [a célközönség betekintési információira vonatkozó felhasználói engedélyek beállításáról](permissions.md#assign-roles-and-permissions)</span><span class="sxs-lookup"><span data-stu-id="c92b9-111">Learn more about [setting user permissions in audience insights](permissions.md#assign-roles-and-permissions)</span></span>

<span data-ttu-id="c92b9-112">Az Azure-ban:</span><span class="sxs-lookup"><span data-stu-id="c92b9-112">In Azure:</span></span> 

- <span data-ttu-id="c92b9-113">Aktív Azure-előfizetés.</span><span class="sxs-lookup"><span data-stu-id="c92b9-113">An active Azure subscription.</span></span>

- <span data-ttu-id="c92b9-114">Ha új Azure Data Lake Storage Gen2-fiókot használ, a *szolgáltatás célközönség betekintési információihoz használatos rendszerbiztonsági tagjának* **Storage Blob adat-közreműködői** engedélyekkel kell rendelkeznie.</span><span class="sxs-lookup"><span data-stu-id="c92b9-114">If using a new Azure Data Lake Storage Gen2 account, the *service principal for audience insights* needs **Storage Blob Data Contributor** permissions.</span></span> <span data-ttu-id="c92b9-115">További információ az [Azure Data Lake Storage Gen2-fiók és az  account with Azure szolgáltatás célközönség betekintési információihoz használatos rendszerbiztonsági tagjának összekapcsolásáról](connect-service-principal.md).</span><span class="sxs-lookup"><span data-stu-id="c92b9-115">Learn more on [connecting to an Azure Data Lake Storage Gen2 account with Azure service principal for audience insights](connect-service-principal.md).</span></span> <span data-ttu-id="c92b9-116">A Data Lake Storage Gen2 szolgáltásnál **engedélyezni kell** a [hierarchikus névteret](/azure/storage/blobs/data-lake-storage-namespace).</span><span class="sxs-lookup"><span data-stu-id="c92b9-116">The Data Lake Storage Gen2 **must have** [hierarchical namespace](/azure/storage/blobs/data-lake-storage-namespace) enabled.</span></span>

- <span data-ttu-id="c92b9-117">Az Azure Synapse-munkaterületet tartalmazó erőforráscsoportnál a *szolgáltatás rendszerbiztonsági tagjához* és a *célközönség betekintési információinak felhasználójához* legalább **Olvasó** engedélyt kell hozzárendelni.</span><span class="sxs-lookup"><span data-stu-id="c92b9-117">On the resource group the Azure Synapse workspace is located, the *service principal* and the *user for audience insights* needs to be assigned at least **Reader** permissions.</span></span> <span data-ttu-id="c92b9-118">További információk: [Azure-szerepkörök hozzárendelése az Azure Portal használatával](/azure/role-based-access-control/role-assignments-portal).</span><span class="sxs-lookup"><span data-stu-id="c92b9-118">For more information, see [Assign Azure roles using the Azure portal](/azure/role-based-access-control/role-assignments-portal).</span></span>

- <span data-ttu-id="c92b9-119">A *felhasználónak* **Storage Blob Data-közreműködő** engedéllyel kell rendelkeznie ahhoz az Azure Data Lake Storage Gen2-fiókhoz, amelyben az adatok találhatók, és amely össze lett kapcsolva az Azure Synapse-munkaterülettel.</span><span class="sxs-lookup"><span data-stu-id="c92b9-119">The *user* needs **Storage Blob Data Contributor** permissions on the Azure Data Lake Storage Gen2 account where the data is located and linked to the Azure Synapse workspace.</span></span> <span data-ttu-id="c92b9-120">További információ arról, [hogyan rendelhető hozzá az Azure Portal használatával a blobhoz és a feldolgozási sor adataihoz való hozzáférésre szolgáló Azure-szerepkör](/azure/storage/common/storage-auth-aad-rbac-portal) és részletek [a Storage Blob Data közreműködői engedélyéről](/azure/role-based-access-control/built-in-roles#storage-blob-data-contributor).</span><span class="sxs-lookup"><span data-stu-id="c92b9-120">Learn more about [using the Azure portal to assign an Azure role for access to blob and queue data](/azure/storage/common/storage-auth-aad-rbac-portal) and [Storage Blob Data Contributor permissions](/azure/role-based-access-control/built-in-roles#storage-blob-data-contributor).</span></span>

- <span data-ttu-id="c92b9-121">Az *[Azure Synapse-munkaterület felügyelt identitásához](/azure/synapse-analytics/security/synapse-workspace-managed-identity)* a **Storage Blob Data közreműködői** engedélyével kell rendelkezni abban az Azure Data Lake Storage Gen2-fiókban, ahol az adatok találhatók, és amelyet összekapcsoltak az Azure Synapse-munkaterülettel.</span><span class="sxs-lookup"><span data-stu-id="c92b9-121">The *[Azure Synapse workspace managed identity](/azure/synapse-analytics/security/synapse-workspace-managed-identity)* needs **Storage Blob Data Contributor** permissions on the Azure Data Lake Storage Gen2 account where the data is located and linked to the Azure Synapse workspace.</span></span> <span data-ttu-id="c92b9-122">További információ arról, [hogyan rendelhető hozzá az Azure Portal használatával a blobhoz és a feldolgozási sor adataihoz való hozzáférésre szolgáló Azure-szerepkör](/azure/storage/common/storage-auth-aad-rbac-portal) és részletek [a Storage Blob Data közreműködői engedélyéről](/azure/role-based-access-control/built-in-roles#storage-blob-data-contributor).</span><span class="sxs-lookup"><span data-stu-id="c92b9-122">Learn more on [using the Azure portal to assign an Azure role for access to blob and queue data](/azure/storage/common/storage-auth-aad-rbac-portal) and [Storage Blob Data Contributor permissions](/azure/role-based-access-control/built-in-roles#storage-blob-data-contributor).</span></span>

- <span data-ttu-id="c92b9-123">Az Azure Synapse-munkaterületen a *célközönség betekintési információihoz használatos rendszerbiztonsági tagnak* **Rendszergazda** szerepkörrel kell rendelkeznie.</span><span class="sxs-lookup"><span data-stu-id="c92b9-123">On the Azure Synapse workspace, the *service principal for audience insights* needs **Synapse Administrator** role assigned.</span></span> <span data-ttu-id="c92b9-124">További információ: [A hozzáférés-vezérlés beállítása a Synapse-munkaterülethez](/azure/synapse-analytics/security/how-to-set-up-access-control).</span><span class="sxs-lookup"><span data-stu-id="c92b9-124">For more information, see [How to set up access control for your Synapse workspace](/azure/synapse-analytics/security/how-to-set-up-access-control).</span></span>

## <a name="set-up-the-connection-and-export-to-azure-synapse"></a><span data-ttu-id="c92b9-125">A kapcsolat beállítása és exportálás az Azure Synapse rendszerbe</span><span class="sxs-lookup"><span data-stu-id="c92b9-125">Set up the connection and export to Azure Synapse</span></span>

### <a name="configure-a-connection"></a><span data-ttu-id="c92b9-126">Kapcsolat konfigurálása</span><span class="sxs-lookup"><span data-stu-id="c92b9-126">Configure a connection</span></span>

1. <span data-ttu-id="c92b9-127">Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="c92b9-127">Go to **Admin** > **Connections**.</span></span>

1. <span data-ttu-id="c92b9-128">A kapcsolat konfigurálásához válassza a **Kapcsolat hozzáadása**, majd az **Azure Synapse Analytics** lehetőséget, vagy válassza a **Beállítás** lehetőséget az **Azure Synapse Analytics** csempén.</span><span class="sxs-lookup"><span data-stu-id="c92b9-128">Select **Add connection** and choose **Azure Synapse Analytics** or select the **Set up** on the **Azure Synapse Analytics** tile to configure the connection.</span></span>

1. <span data-ttu-id="c92b9-129">Adjon meg egy felismerhető nevet a Megjelenítendő név mezőben a kapcsolatnak.</span><span class="sxs-lookup"><span data-stu-id="c92b9-129">Give your connection a recognizable name in the Display name field.</span></span> <span data-ttu-id="c92b9-130">A név és a kapcsolat típusa írja le ezt a kapcsolatot.</span><span class="sxs-lookup"><span data-stu-id="c92b9-130">The name and the type of the connection describes this connection.</span></span> <span data-ttu-id="c92b9-131">Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.</span><span class="sxs-lookup"><span data-stu-id="c92b9-131">We recommend choosing a name that explains the purpose and target of the connection.</span></span>

1. <span data-ttu-id="c92b9-132">A kapcsolat használóinak kiválasztása.</span><span class="sxs-lookup"><span data-stu-id="c92b9-132">Choose who can use this connection.</span></span> <span data-ttu-id="c92b9-133">Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz.</span><span class="sxs-lookup"><span data-stu-id="c92b9-133">If you take no action, the default will be Administrators.</span></span> <span data-ttu-id="c92b9-134">További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).</span><span class="sxs-lookup"><span data-stu-id="c92b9-134">For more information, see [Allow contributors to use a connection for exports](connections.md#allow-contributors-to-use-a-connection-for-exports).</span></span>

1. <span data-ttu-id="c92b9-135">Válassza ki vagy keresse meg azt az előfizetést, amelyben használni szeretné a Customer Insights adatait.</span><span class="sxs-lookup"><span data-stu-id="c92b9-135">Select or search for the subscription you want to use the Customer Insights data in.</span></span> <span data-ttu-id="c92b9-136">Az előfizetés kiválasztása után a **Munkaterület**, a **Tárfiók** és a **Tároló** lehetőség is kiválasztható.</span><span class="sxs-lookup"><span data-stu-id="c92b9-136">As soon as a subscription is selected, you can also select **Workspace**, **Storage account**, and **Container**.</span></span>

1. <span data-ttu-id="c92b9-137">A kapcsolat mentéséhez válassza a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="c92b9-137">Select **Save** to save the connection.</span></span>

### <a name="configure-an-export"></a><span data-ttu-id="c92b9-138">Exportálás konfigurálása</span><span class="sxs-lookup"><span data-stu-id="c92b9-138">Configure an export</span></span>

<span data-ttu-id="c92b9-139">Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz.</span><span class="sxs-lookup"><span data-stu-id="c92b9-139">You can configure this export if you have access to a connection of this type.</span></span> <span data-ttu-id="c92b9-140">További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).</span><span class="sxs-lookup"><span data-stu-id="c92b9-140">For more information, see [permissions needed to configure an export](export-destinations.md#set-up-a-new-export).</span></span>

1. <span data-ttu-id="c92b9-141">Menjen az **Adatok** > **Exportálások** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="c92b9-141">Go to **Data** > **Exports**.</span></span>

1. <span data-ttu-id="c92b9-142">Új exportálás létrehozásához válassza az **Exportálás hozzáadása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="c92b9-142">To create a new export, select **Add export**.</span></span>

1. <span data-ttu-id="c92b9-143">A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot az **Azure Synapse Analytics** szakaszból.</span><span class="sxs-lookup"><span data-stu-id="c92b9-143">In the **Connection for export** field, choose a connection from the **Azure Synapse Analytics** section.</span></span> <span data-ttu-id="c92b9-144">Ha nem látja ezt a szakasznevet, az Ön számára nem áll rendelkezésre ilyen típusú [kapcsolat](connections.md).</span><span class="sxs-lookup"><span data-stu-id="c92b9-144">If you don't see this section name, there are no [connections](connections.md) of this type available to you.</span></span>

1. <span data-ttu-id="c92b9-145">Adjon meg egy felismerhető **megjelenítendő nevet** és egy **adatbázisnevet** az exportáláshoz.</span><span class="sxs-lookup"><span data-stu-id="c92b9-145">Provide a recognizable **Display name** for your export and a **Database name**.</span></span>

1. <span data-ttu-id="c92b9-146">Válassza ki, hogy melyik entitásokat szeretné exportálni az Azure Synapse Analytics alkalmazásba.</span><span class="sxs-lookup"><span data-stu-id="c92b9-146">Select which entities you want to export to Azure Synapse Analytics.</span></span>

1. <span data-ttu-id="c92b9-147">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="c92b9-147">Select **Save**.</span></span>

<span data-ttu-id="c92b9-148">Az exportálás mentése nem futtatja azonnal az exportálást.</span><span class="sxs-lookup"><span data-stu-id="c92b9-148">Saving an export doesn't run the export immediately.</span></span>

<span data-ttu-id="c92b9-149">Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut.</span><span class="sxs-lookup"><span data-stu-id="c92b9-149">The export runs with every [scheduled refresh](system.md#schedule-tab).</span></span> <span data-ttu-id="c92b9-150">Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand).</span><span class="sxs-lookup"><span data-stu-id="c92b9-150">You can also [export data on demand](export-destinations.md#run-exports-on-demand).</span></span>

### <a name="update-an-export"></a><span data-ttu-id="c92b9-151">Exportálás frissítése</span><span class="sxs-lookup"><span data-stu-id="c92b9-151">Update an export</span></span>

1. <span data-ttu-id="c92b9-152">Menjen az **Adatok** > **Exportálások** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="c92b9-152">Go to **Data** > **Exports**.</span></span>

1. <span data-ttu-id="c92b9-153">Válassza ki a **Szerkesztés** lehetőséget a frissíteni kívánt exportálásnál.</span><span class="sxs-lookup"><span data-stu-id="c92b9-153">Select **Edit** on the export you want to update.</span></span>

   - <span data-ttu-id="c92b9-154">**Adjon** hozzá entitásokat a kijelöléshez, vagy **távolítson el** belőle szakaszokat.</span><span class="sxs-lookup"><span data-stu-id="c92b9-154">**Add** or **Remove** entities from the selection.</span></span> <span data-ttu-id="c92b9-155">A kijelölésből eltávolított entitások nem törlődnek a Synapse Analytics-adatbázisból.</span><span class="sxs-lookup"><span data-stu-id="c92b9-155">If entities are removed from the selection, they aren't deleted from the Synapse Analytics database.</span></span> <span data-ttu-id="c92b9-156">A későbbi adatfrissítések azonban nem frissítik az adott adatbázisban lévő eltávolított entitásokat.</span><span class="sxs-lookup"><span data-stu-id="c92b9-156">However, future data refreshes won't update the removed entities in that database.</span></span>

   - <span data-ttu-id="c92b9-157">Az **Adatbázis nevének megváltoztatása** beállítással új Synapse Analytics-adatbázis hozható létre.</span><span class="sxs-lookup"><span data-stu-id="c92b9-157">**Changing the Database Name** creates a new Synapse Analytics database.</span></span> <span data-ttu-id="c92b9-158">A korábban beállított nevű adatbázis nem fog frissülni a későbbi frissítések során.</span><span class="sxs-lookup"><span data-stu-id="c92b9-158">The database with the name that was configured before won't receive any updates in future refreshes.</span></span>
