---
title: Csatlakozás egy Azure Data Lake Storage Gen2-fiókhoz egyszerű szolgáltatásnévvel
description: Azure egyszerű szolgáltatásnév használatával a célközöség-információkhoz a saját adattóhoz való csatlakozáshoz a célközönség-információkhoz való csatolás során.
ms.date: 02/10/2021
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: adkuppa
ms.author: adkuppa
ms.reviewer: mhart
manager: shellyha
ms.openlocfilehash: eebbac1370a847869d98beaf70db49b809d762e7
ms.sourcegitcommit: 139548f8a2d0f24d54c4a6c404a743eeeb8ef8e0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/15/2021
ms.locfileid: "5267725"
---
# <a name="connect-to-an-azure-data-lake-storage-gen2-account-with-an-azure-service-principal-for-audience-insights"></a><span data-ttu-id="946ea-103">Csatlakozás az Azure Data Lake Storage Gen2 fiókjához az Azure fő szolgáltatás célözönség információk funkcióján keresztül</span><span class="sxs-lookup"><span data-stu-id="946ea-103">Connect to an Azure Data Lake Storage Gen2 account with an Azure service principal for audience insights</span></span>

<span data-ttu-id="946ea-104">Az Azure-szolgáltatásokat használó automatizált eszközöknek mindig korlátozott engedélyekkel kell rendelkezniük.</span><span class="sxs-lookup"><span data-stu-id="946ea-104">Automated tools that use Azure services should always have restricted permissions.</span></span> <span data-ttu-id="946ea-105">Ahelyett, hogy az alkalmazások teljes jogosultsággal rendelkező felhasználóként jelentkezzenek be, az Azure egyszerű szolgáltatásneveket biztosít.</span><span class="sxs-lookup"><span data-stu-id="946ea-105">Instead of having applications sign in as a fully privileged user, Azure offers service principals.</span></span> <span data-ttu-id="946ea-106">A cikkből megtudhatja, hogyan kapcsolhatja össze a célközönség-információkat egy Azure Data Lake Storage Gen2-fiókkal Azure egyszerű szolgáltatásnév használatával tárfiókkulcsok helyett.</span><span class="sxs-lookup"><span data-stu-id="946ea-106">Read on to learn how to connect audience insights with an Azure Data Lake Storage Gen2 account using an Azure service principal instead of storage account keys.</span></span> 

<span data-ttu-id="946ea-107">Az egyszerű szolgáltatásnév használatával biztonságosan [hozzáadhat vagy szerkeszthet egy Common Data Model mappát adatforrásként](connect-common-data-model.md) vagy [létrehozhat egy új környezetet, vagy frissíthet egy meglévőt](manage-environments.md#create-an-environment-in-an-existing-organization).</span><span class="sxs-lookup"><span data-stu-id="946ea-107">You can use the service principal to securely [add or edit a Common Data Model folder as a data source](connect-common-data-model.md) or [create a new or update an existing environment](manage-environments.md#create-an-environment-in-an-existing-organization).</span></span>

> [!IMPORTANT]
> - <span data-ttu-id="946ea-108">A szolgáltatást használni kívánó Azure Data Lake Gen2 tárfióban [engedélyeznie kell hierarchikus a névterületet (HNS)](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-namespace).</span><span class="sxs-lookup"><span data-stu-id="946ea-108">The Azure Data Lake Gen2 storage account that intends to use the service principal must have [Hierarchical Name Space (HNS) enabled](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-namespace).</span></span>
> - <span data-ttu-id="946ea-109">Az egyszerű szolgáltatásnév létrehozásához rendszergazdai előfizetéssel kell rendelkezni az Azure-előfizetéshez.</span><span class="sxs-lookup"><span data-stu-id="946ea-109">You need admin permissions for your Azure subscription to create the service principal.</span></span>

## <a name="create-azure-service-principal-for-audience-insights"></a><span data-ttu-id="946ea-110">Azure egyszerű szolgáltatásnév létrehozása célközönség-információkhoz</span><span class="sxs-lookup"><span data-stu-id="946ea-110">Create Azure service principal for audience insights</span></span>

<span data-ttu-id="946ea-111">Mielőtt új egyszerű szolgáltatásnevet hozna létre célközönség-információkhoz, ellenőrizze, hogy a szervezetben már szerepel-e.</span><span class="sxs-lookup"><span data-stu-id="946ea-111">Before creating a new service principal for audience insights, check if it already exists in your organization.</span></span>

### <a name="look-for-an-existing-service-principal"></a><span data-ttu-id="946ea-112">Meglévő egyszerű szolgáltatásnév keresése</span><span class="sxs-lookup"><span data-stu-id="946ea-112">Look for an existing service principal</span></span>

1. <span data-ttu-id="946ea-113">Nyissa meg az [Azure rendszergazdai portált](https://portal.azure.com), és jelentkezzen be a szervezetbe.</span><span class="sxs-lookup"><span data-stu-id="946ea-113">Go to the [Azure admin portal](https://portal.azure.com) and sign in to your organization.</span></span>

2. <span data-ttu-id="946ea-114">Válassza **Azure Active Directory** lehetőséget az Azure-szolgáltatásokból.</span><span class="sxs-lookup"><span data-stu-id="946ea-114">Select **Azure Active Directory** from the Azure services.</span></span>

3. <span data-ttu-id="946ea-115">Válassza a **Kezelés** területen a **Vállalati alkalmazások** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="946ea-115">Under **Manage**, select **Enterprise Applications**.</span></span>

4. <span data-ttu-id="946ea-116">Keresse meg a célközönség-információk belső alkalmazásazonosítóját: `0bfc4568-a4ba-4c58-bd3e-5d3e76bd7fff`, vagy a nevet: `Dynamics 365 AI for Customer Insights`.</span><span class="sxs-lookup"><span data-stu-id="946ea-116">Search for the audience insights first party application ID `0bfc4568-a4ba-4c58-bd3e-5d3e76bd7fff` or the name `Dynamics 365 AI for Customer Insights`.</span></span>

5. <span data-ttu-id="946ea-117">Ha a megfelelő rekordot találja, az azt jelenti, hogy az egyszerű szolgáltatásnév létezik a célközönség-információkhoz.</span><span class="sxs-lookup"><span data-stu-id="946ea-117">If you find a matching record, it means that the service principal for audience insights exists.</span></span> <span data-ttu-id="946ea-118">Nem kell ismét létrehoznia.</span><span class="sxs-lookup"><span data-stu-id="946ea-118">You don't need to create it again.</span></span>
   
   :::image type="content" source="media/ADLS-SP-AlreadyProvisioned.png" alt-text="Képernyőkép a meglévő egyszerű szolgáltatásnévvel":::
   
6. <span data-ttu-id="946ea-120">Ha a rendszer nem ad vissza eredményt, hozzon létre egy új egyszerű szolgáltatásnevet.</span><span class="sxs-lookup"><span data-stu-id="946ea-120">If no results are returned, create a new service principal.</span></span>

### <a name="create-a-new-service-principal"></a><span data-ttu-id="946ea-121">Új egyszerű szolgáltatásnév létrehozása</span><span class="sxs-lookup"><span data-stu-id="946ea-121">Create a new service principal</span></span>

1. <span data-ttu-id="946ea-122">Telepítse az **Azure Active Directory PowerShell Graphhoz** legújabb verzióját.</span><span class="sxs-lookup"><span data-stu-id="946ea-122">Install the latest version of the **Azure Active Directory PowerShell for Graph**.</span></span> <span data-ttu-id="946ea-123">További információkért lásd: [Azure Active Directory PowerShell telepítése a graphhoz](https://docs.microsoft.com/powershell/azure/active-directory/install-adv2).</span><span class="sxs-lookup"><span data-stu-id="946ea-123">For more information, see [Install Azure Active Directory PowerShell for Graph](https://docs.microsoft.com/powershell/azure/active-directory/install-adv2).</span></span>
   - <span data-ttu-id="946ea-124">A számítógépen válassza ki a Windows billentyűt a billentyűzeten, és keresse meg a **Windows PowerShell** programot, és **Futtatás rendszergazdaként** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="946ea-124">On your PC, select the Windows key on your keyboard and search for **Windows PowerShell** and **Run as Administrator**.</span></span>
   
   - <span data-ttu-id="946ea-125">A megnyíló PowerShell ablakában adja meg az `Install-Module AzureAD` értéket.</span><span class="sxs-lookup"><span data-stu-id="946ea-125">In the PowerShell window that opens, enter `Install-Module AzureAD`.</span></span>

2. <span data-ttu-id="946ea-126">A célközönség-információkhoz tartozó egyszerű szolgáltatásnév létrehozása az Azure AD PowerShell modullal.</span><span class="sxs-lookup"><span data-stu-id="946ea-126">Create the  service principal for audience insights with the Azure AD PowerShell Module.</span></span>
   - <span data-ttu-id="946ea-127">A PowerShell ablakában adja meg az `Connect-AzureAD -TenantId "[your tenant ID]" -AzureEnvironmentName Azure` értéket.</span><span class="sxs-lookup"><span data-stu-id="946ea-127">In the PowerShell window, enter `Connect-AzureAD -TenantId "[your tenant ID]" -AzureEnvironmentName Azure`.</span></span> <span data-ttu-id="946ea-128">Cserélje ki az „Ön bérlői azonosítója” lehetőséget a bérlő tényleges azonosítójához, ahol létre akarja hozni az egyszerű szolgáltatásnevet.</span><span class="sxs-lookup"><span data-stu-id="946ea-128">Replace “your tenant ID” with the actual ID of your tenant where you want to create the service principal.</span></span> <span data-ttu-id="946ea-129">Az `AzureEnvironmentName` környezetinév-paraméter nem kötelező.</span><span class="sxs-lookup"><span data-stu-id="946ea-129">The environment name parameter `AzureEnvironmentName` is optional.</span></span>
  
   - <span data-ttu-id="946ea-130">Adja meg a `New-AzureADServicePrincipal -AppId "0bfc4568-a4ba-4c58-bd3e-5d3e76bd7fff" -DisplayName "Dynamics 365 AI for Customer Insights"`.</span><span class="sxs-lookup"><span data-stu-id="946ea-130">Enter `New-AzureADServicePrincipal -AppId "0bfc4568-a4ba-4c58-bd3e-5d3e76bd7fff" -DisplayName "Dynamics 365 AI for Customer Insights"`.</span></span> <span data-ttu-id="946ea-131">Ez a parancs létrehozza az egyszerű szolgáltatásnevet a kiválasztott bérlő célközönség-információihoz.</span><span class="sxs-lookup"><span data-stu-id="946ea-131">This command creates the service principal for audience insights on the selected tenant.</span></span>  

## <a name="grant-permissions-to-the-service-principal-to-access-the-storage-account"></a><span data-ttu-id="946ea-132">Engedélyek biztosítása az egyszerű szolgáltatásnév számára a tárfiók eléréséhez</span><span class="sxs-lookup"><span data-stu-id="946ea-132">Grant permissions to the service principal to access the storage account</span></span>

<span data-ttu-id="946ea-133">Látogasson el az Azure portal webhelyre, és adja meg az egyszerű szolgáltatásnévre vonatkozó engedélyeket a tárfiók számára a célközönség-információkban való használatra.</span><span class="sxs-lookup"><span data-stu-id="946ea-133">Go to the Azure portal to grant permissions to the service principal for the storage account you want to use in audience insights.</span></span>

1. <span data-ttu-id="946ea-134">Nyissa meg az [Azure rendszergazdai portált](https://portal.azure.com), és jelentkezzen be a szervezetbe.</span><span class="sxs-lookup"><span data-stu-id="946ea-134">Go to the [Azure admin portal](https://portal.azure.com) and sign in to your organization.</span></span>

1. <span data-ttu-id="946ea-135">Nyissa meg azt a tárfiókot, amelyhez a célközönség-információhoz tartozó egyszerű szolgáltatásnévnek hozzáféréssel kell rendelkeznie.</span><span class="sxs-lookup"><span data-stu-id="946ea-135">Open the storage account you want the service principal for audience insights to have access to.</span></span>

1. <span data-ttu-id="946ea-136">Válassza az **Access Control (IAM)** elemet a navigációs panelen, és válassza a **Hozzáadás** > **Szerepkör-hozzárendelés hozzáadása** elemet.</span><span class="sxs-lookup"><span data-stu-id="946ea-136">Select **Access control (IAM)** from the navigation pane and select **Add** > **Add role assignment**.</span></span>
   
   :::image type="content" source="media/ADLS-SP-AddRoleAssignment.png" alt-text="Képernyőkép – Azure portál szerepkör-hozzárendelés közben.":::
   
1. <span data-ttu-id="946ea-138">A **Szerepkör-hozzárendelés hozzáadása** panelen adja hozzá a következő tulajdonságokat:</span><span class="sxs-lookup"><span data-stu-id="946ea-138">In the **Add role assignment** pane, set the following properties:</span></span>
   - <span data-ttu-id="946ea-139">szerepkör: *Storage Blob adat-közreműködő*</span><span class="sxs-lookup"><span data-stu-id="946ea-139">Role: *Storage Blob Data Contributor*</span></span>
   - <span data-ttu-id="946ea-140">Rendeljen hozzáférést ehhez: *Felhasználó, csoport vagy egyszerű szolgáltatásnév*</span><span class="sxs-lookup"><span data-stu-id="946ea-140">Assign access to: *User, group, or service principal*</span></span>
   - <span data-ttu-id="946ea-141">Válassza: *Dynamics 365 AI Customer Insights szolgáltatáshoz* (a [létrehozott egyszerű szolgáltatásnév](#create-a-new-service-principal))</span><span class="sxs-lookup"><span data-stu-id="946ea-141">Select: *Dynamics 365 AI for Customer Insights* (the [service principal you created](#create-a-new-service-principal))</span></span>

1.  <span data-ttu-id="946ea-142">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="946ea-142">Select **Save**.</span></span>

<span data-ttu-id="946ea-143">A módosítások feltöltése 15 percet is igénybe vehet.</span><span class="sxs-lookup"><span data-stu-id="946ea-143">It can take up to 15 minutes to propagate the changes.</span></span>

## <a name="enter-the-azure-resource-id-or-the-azure-subscription-details-in-the-storage-account-attachment-to-audience-insights"></a><span data-ttu-id="946ea-144">Adja meg a Célközönség-információkhoz csatolt tárfiókban az Azure forrásazonosítót vagy az Azure előfizetés részleteit.</span><span class="sxs-lookup"><span data-stu-id="946ea-144">Enter the Azure Resource ID or the Azure Subscription details in the storage account attachment to Audience Insights.</span></span>

<span data-ttu-id="946ea-145">Kapcsoljon egy Azure Data Lake-tárfiókot a célközönség-információkban a [kimeneti adatok tárolásához](manage-environments.md) vagy [használhatja adatforrásként](connect-common-data-service-lake.md).</span><span class="sxs-lookup"><span data-stu-id="946ea-145">Attach an Azure Data Lake storage account in audience insights to [store output data](manage-environments.md) or [use it as a data source](connect-common-data-service-lake.md).</span></span> <span data-ttu-id="946ea-146">Az Azure Data Lake beállítás választásával az erőforrás-alapú vagy előfizetéses alapú megközelítések közül választhat.</span><span class="sxs-lookup"><span data-stu-id="946ea-146">Choosing the Azure Data Lake option lets you choose between a resource-based or a subscription-based based approach.</span></span>

<span data-ttu-id="946ea-147">Az alábbi lépések végrehajtásával adja meg a szükséges információkat a kiválasztott megközelítésről.</span><span class="sxs-lookup"><span data-stu-id="946ea-147">Follow the below steps to provide the required information on the selected approach.</span></span>

### <a name="resource-based-storage-account-connection"></a><span data-ttu-id="946ea-148">Erőforrás-alapú tárfiókkapcsolat</span><span class="sxs-lookup"><span data-stu-id="946ea-148">Resource-based storage account connection</span></span>

1. <span data-ttu-id="946ea-149">Keresse fel az [Azure rendszergazdai portált](https://portal.azure.com), jelentkezzen be az előfizetésbe, és nyissa meg a tárfiókot.</span><span class="sxs-lookup"><span data-stu-id="946ea-149">Go to the [Azure admin portal](https://portal.azure.com), sign in to your subscription and open the storage account.</span></span>

1. <span data-ttu-id="946ea-150">Nyissa meg a **Beállítások** > **Tulajdonságok** elemet a navigációs panelen.</span><span class="sxs-lookup"><span data-stu-id="946ea-150">Go to **Settings** > **Properties** on navigation pane.</span></span>

1. <span data-ttu-id="946ea-151">Másolja a tárfiók erőforrás-azonosítójának értékét.</span><span class="sxs-lookup"><span data-stu-id="946ea-151">Copy the storage account resource ID value.</span></span>

   :::image type="content" source="media/ADLS-SP-ResourceId.png" alt-text="Másolja a tárfiók erőforrás-azonosítóját.":::

1. <span data-ttu-id="946ea-153">A célközönság-információkban adja meg az erőforrás-azonosítót az erőforrás mezőben, amely a tárfiókkapcsolati képernyőn jelenik meg.</span><span class="sxs-lookup"><span data-stu-id="946ea-153">In audience insights, insert the resource ID in the resource field displayed in the storage account connection screen.</span></span>

   :::image type="content" source="media/ADLS-SP-ResourceIdConnection.png" alt-text="Adja meg a tárfiók erőforrás-azonosítójának adatait.":::   
   
1. <span data-ttu-id="946ea-155">Folytassa a többi lépést a célközönség-információkban, hogy csatolja a tárfiókot.</span><span class="sxs-lookup"><span data-stu-id="946ea-155">Continue with the remaining steps in audience insights to attach the storage account.</span></span>

### <a name="subscription-based-storage-account-connection"></a><span data-ttu-id="946ea-156">Előfizetés-alapú tárfiókkapcsolat</span><span class="sxs-lookup"><span data-stu-id="946ea-156">Subscription-based storage account connection</span></span>

1. <span data-ttu-id="946ea-157">Keresse fel az [Azure rendszergazdai portált](https://portal.azure.com), jelentkezzen be az előfizetésbe, és nyissa meg a tárfiókot.</span><span class="sxs-lookup"><span data-stu-id="946ea-157">Go to the [Azure admin portal](https://portal.azure.com), sign in to your subscription and open the storage account.</span></span>

1. <span data-ttu-id="946ea-158">Nyissa meg a **Beállítások** > **Tulajdonságok** elemet a navigációs panelen.</span><span class="sxs-lookup"><span data-stu-id="946ea-158">Go to **Settings** > **Properties** on navigation pane.</span></span>

1. <span data-ttu-id="946ea-159">Tekintse át az **Előfizetést**, az **Erőforráscsoportot** és a tárolási fiók **Nevét**, és ügyeljen rá, hogy célközönség-információknál jelölje ki a megfelelő értékeket.</span><span class="sxs-lookup"><span data-stu-id="946ea-159">Review the **Subscription**, **Resource group**, and the **Name** of the storage account to make sure you select the right values in audience insights.</span></span>

1. <span data-ttu-id="946ea-160">A célközönség-információkban válassza ki az értékeket vagy a megfelelő mezőket a tárfiók csatolásakor.</span><span class="sxs-lookup"><span data-stu-id="946ea-160">In audience insights, choose the values or for the corresponding fields when attaching the storage account.</span></span>
   
1. <span data-ttu-id="946ea-161">Folytassa a többi lépést a célközönség-információkban, hogy csatolja a tárfiókot.</span><span class="sxs-lookup"><span data-stu-id="946ea-161">Continue with the remaining steps in audience insights to attach the storage account.</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]