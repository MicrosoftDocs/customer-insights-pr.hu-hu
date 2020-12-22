---
title: Csatlakozás egy Azure Data Lake Storage Gen2-fiókhoz egyszerű szolgáltatásnévvel
description: Azure egyszerű szolgáltatásnév használatával a célközöség-információkhoz a saját adattóhoz való csatlakozáshoz a célközönség-információkhoz való csatolás során.
ms.date: 11/24/2020
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: adkuppa
ms.author: adkuppa
ms.reviewer: mhart
manager: shellyha
ms.openlocfilehash: c2fae278d34fa02b9168ac70dfa8dd351653245e
ms.sourcegitcommit: 6a6df62fa12dcb9bd5f5a39cc3ee0e2b3988184b
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/25/2020
ms.locfileid: "4644091"
---
# <a name="connect-to-an-azure-data-lake-storage-gen2-account-with-an-azure-service-principal-for-audience-insights"></a>Csatlakozás az Azure Data Lake Storage Gen2 fiókjához az Azure fő szolgáltatás célözönség információk funkcióján keresztül

Az Azure-szolgáltatásokat használó automatizált eszközöknek mindig korlátozott engedélyekkel kell rendelkezniük. Ahelyett, hogy az alkalmazások teljes jogosultsággal rendelkező felhasználóként jelentkezzenek be, az Azure egyszerű szolgáltatásneveket biztosít. A cikkből megtudhatja, hogyan kapcsolhatja össze a célközönség-információkat egy Azure Data Lake Storage Gen2-fiókkal Azure egyszerű szolgáltatásnév használatával tárfiókkulcsok helyett. 

Az egyszerű szolgáltatásnév használatával biztonságosan [hozzáadhat vagy szerkeszthet egy Common Data Model mappát adatforrásként](connect-common-data-model.md) vagy [létrehozhat egy új környezetet, vagy frissíthet egy meglévőt](manage-environments.md#create-an-environment-in-an-existing-organization).

Az egyszerű szolgáltatásnév létrehozásához rendszergazdai előfizetéssel kell rendelkezni az Azure-előfizetéshez.

## <a name="create-azure-service-principal-for-audience-insights"></a>Azure egyszerű szolgáltatásnév létrehozása célközönség-információkhoz

Mielőtt új egyszerű szolgáltatásnevet hozna létre célközönség-információkhoz, ellenőrizze, hogy a szervezetben már szerepel-e.

### <a name="look-for-an-existing-service-principal"></a>Meglévő egyszerű szolgáltatásnév keresése

1. Nyissa meg az [Azure rendszergazdai portált](https://portal.azure.com), és jelentkezzen be a szervezetbe.

2. Válassza **Azure Active Directory** lehetőséget az Azure-szolgáltatásokból.

3. Válassza a **Kezelés** területen a **Vállalati alkalmazások** lehetőséget.

4. Keresse meg a célközönség-információk belső alkalmazásazonosítóját: `0bfc4568-a4ba-4c58-bd3e-5d3e76bd7fff`, vagy a nevet: `Dynamics 365 AI for Customer Insights`.

5. Ha a megfelelő rekordot találja, az azt jelenti, hogy az egyszerű szolgáltatásnév létezik a célközönség-információkhoz. Nem kell ismét létrehoznia.
   
   :::image type="content" source="media/ADLS-SP-AlreadyProvisioned.png" alt-text="Képernyőkép a meglévő egyszerű szolgáltatásnévvel":::
   
6. Ha a rendszer nem ad vissza eredményt, hozzon létre egy új egyszerű szolgáltatásnevet.

### <a name="create-a-new-service-principal"></a>Új egyszerű szolgáltatásnév létrehozása

1. Telepítse az **Azure Active Directory PowerShell Graphhoz** legújabb verzióját. További információkért lásd: [Azure Active Directory PowerShell telepítése a graphhoz](https://docs.microsoft.com/powershell/azure/active-directory/install-adv2).
   - A számítógépen válassza ki a Windows billentyűt a billentyűzeten, és keresse meg a **Windows PowerShell** programot, és **Futtatás rendszergazdaként** lehetőséget.
   
   - A megnyíló PowerShell ablakában adja meg az `Install-Module AzureAD` értéket.

2. A célközönség-információkhoz tartozó egyszerű szolgáltatásnév létrehozása az Azure AD PowerShell modullal.
   - A PowerShell ablakában adja meg az `Connect-AzureAD -TenantId "[your tenant ID]" -AzureEnvironmentName Azure` értéket. Cserélje ki az „Ön bérlői azonosítója” lehetőséget a bérlő tényleges azonosítójához, ahol létre akarja hozni az egyszerű szolgáltatásnevet. Az `AzureEnvironmentName` környezetinév-paraméter nem kötelező.
  
   - Adja meg a `New-AzureADServicePrincipal -AppId "0bfc4568-a4ba-4c58-bd3e-5d3e76bd7fff" -DisplayName "Dynamics 365 AI for Customer Insights"`. Ez a parancs létrehozza az egyszerű szolgáltatásnevet a kiválasztott bérlő célközönség-információihoz.  

## <a name="grant-permissions-to-the-service-principal-to-access-the-storage-account"></a>Engedélyek biztosítása az egyszerű szolgáltatásnév számára a tárfiók eléréséhez

Látogasson el az Azure portal webhelyre, és adja meg az egyszerű szolgáltatásnévre vonatkozó engedélyeket a tárfiók számára a célközönség-információkban való használatra.

1. Nyissa meg az [Azure rendszergazdai portált](https://portal.azure.com), és jelentkezzen be a szervezetbe.

1. Nyissa meg azt a tárfiókot, amelyhez a célközönség-információhoz tartozó egyszerű szolgáltatásnévnek hozzáféréssel kell rendelkeznie.

1. Válassza az **Access Control (IAM)** elemet a navigációs panelen, és válassza a **Hozzáadás** > **Szerepkör-hozzárendelés hozzáadása** elemet.
   
   :::image type="content" source="media/ADLS-SP-AddRoleAssignment.png" alt-text="Képernyőkép – Azure portál szerepkör-hozzárendelés közben.":::
   
1. A **Szerepkör-hozzárendelés hozzáadása** panelen adja hozzá a következő tulajdonságokat:
   - szerepkör: *Storage Blob adat-közreműködő*
   - Rendeljen hozzáférést ehhez: *Felhasználó, csoport vagy egyszerű szolgáltatásnév*
   - Válassza: *Dynamics 365 AI Customer Insights szolgáltatáshoz* (a [létrehozott egyszerű szolgáltatásnév](#create-a-new-service-principal))

1.  Válassza a **Mentés** parancsot.

A módosítások feltöltése 15 percet is igénybe vehet.

## <a name="enter-the-azure-resource-id-or-the-azure-subscription-details-in-the-storage-account-attachment-to-audience-insights"></a>Adja meg a Célközönség-információkhoz csatolt tárfiókban az Azure forrásazonosítót vagy az Azure előfizetés részleteit.

Kapcsoljon egy Azure Data Lake-tárfiókot a célközönség-információkban a [kimeneti adatok tárolásához](manage-environments.md) vagy [használhatja adatforrásként](connect-common-data-service-lake.md). Az Azure Data Lake beállítás választásával az erőforrás-alapú vagy előfizetéses alapú megközelítések közül választhat.

Az alábbi lépések végrehajtásával adja meg a szükséges információkat a kiválasztott megközelítésről.

### <a name="resounce-based-storage-account-connection"></a>Erőforrás-alapú tárfiókkapcsolat

1. Keresse fel az [Azure rendszergazdai portált](https://portal.azure.com), jelentkezzen be az előfizetésbe, és nyissa meg a tárfiókot.

1. Nyissa meg a **Beállítások** > **Tulajdonságok** elemet a navigációs panelen.

1. Másolja a tárfiók erőforrás-azonosítójának értékét.

   :::image type="content" source="media/ADLS-SP-ResourceId.png" alt-text="Másolja a tárfiók erőforrás-azonosítóját.":::

1. A célközönság-információkban adja meg az erőforrás-azonosítót az erőforrás mezőben, amely a tárfiókkapcsolati képernyőn jelenik meg.

   :::image type="content" source="media/ADLS-SP-ResourceIdConnection.png" alt-text="Adja meg a tárfiók erőforrás-azonosítójának adatait.":::   
   
1. Folytassa a többi lépést a célközönség-információkban, hogy csatolja a tárfiókot.

### <a name="subscription-based-storage-account-connection"></a>Előfizetés-alapú tárfiókkapcsolat

1. Keresse fel az [Azure rendszergazdai portált](https://portal.azure.com), jelentkezzen be az előfizetésbe, és nyissa meg a tárfiókot.

1. Nyissa meg a **Beállítások** > **Tulajdonságok** elemet a navigációs panelen.

1. Tekintse át az **Előfizetést**, az **Erőforráscsoportot** és a tárolási fiók **Nevét**, és ügyeljen rá, hogy célközönség-információknál jelölje ki a megfelelő értékeket.

1. A célközönség-információkban válassza ki az értékeket vagy a megfelelő mezőket a tárfiók csatolásakor.

   :::image type="content" source="media/ADLS-SP-SubscriptionConnection.png" alt-text="Adja meg a tárfiók erőforrás-azonosítójának adatait.":::
   
1. Folytassa a többi lépést a célközönség-információkban, hogy csatolja a tárfiókot.
