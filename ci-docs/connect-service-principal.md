---
title: Csatlakozás egy Azure Data Lake Storage-fiókhoz egy szolgáltatásnév segítségével
description: Azure szolgáltatásnév használata a saját adattó csatlakoztatására.
ms.date: 04/26/2022
ms.subservice: audience-insights
ms.topic: how-to
author: adkuppa
ms.author: adkuppa
ms.reviewer: mhart
manager: shellyha
searchScope:
- ci-system-security
- customerInsights
ms.openlocfilehash: 1dd99edc327bd41b0442b390f2e4f8664269f553
ms.sourcegitcommit: b7dbcd5627c2ebfbcfe65589991c159ba290d377
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/27/2022
ms.locfileid: "8642658"
---
# <a name="connect-to-an-azure-data-lake-storage-account-by-using-an-azure-service-principal"></a>Csatlakozás egy Azure Data Lake Storage-fiókhoz egy Azure szolgáltatásnév segítségével

Ez a cikk azt ismerteti, hogyan lehet csatlakozni Dynamics 365 Customer Insights egy fiókhoz a Azure Data Lake Storage tárfiókkulcsok helyett egy Azure-szolgáltatásnév használatával. 

Az Azure-szolgáltatásokat használó automatizált eszközöknek mindig korlátozott engedélyekkel kell rendelkezniük. Ahelyett, hogy az alkalmazások teljes jogosultsággal rendelkező felhasználóként jelentkezzenek be, az Azure egyszerű szolgáltatásneveket biztosít. A szolgáltatásnévvel biztonságosan [hozzáadhat vagy szerkeszthet egy Common Data Model mappát adatforrás](connect-common-data-model.md), illetve [létrehozhat vagy frissíthet egy környezetet](create-environment.md).

> [!IMPORTANT]
> - Az egyszerű szolgáltatást használó Data Lake Storage fióknak Gen2-nek kell lennie, és engedélyeznie kell [hierarchikus névteret](/azure/storage/blobs/data-lake-storage-namespace). Az Azure Data Lake Gen1 tárfiókjai nem támogatottak.
> - Az egyszerű szolgáltatás létrehozásához rendszergazdai engedélyekre van szükség az Azure-előfizetéshez.

## <a name="create-an-azure-service-principal-for-customer-insights"></a>Azure szolgáltatásnév létrehozása a Customer Insightshoz

Mielőtt új szolgáltatáselemet hozna létre a Customer Insights számára, ellenőrizze, hogy létezik-e már a szervezetben.

### <a name="look-for-an-existing-service-principal"></a>Meglévő egyszerű szolgáltatásnév keresése

1. Nyissa meg az [Azure rendszergazdai portált](https://portal.azure.com), és jelentkezzen be a szervezetbe.

2. Az **Azure-szolgáltatások** csoportban válassza az **Azure Active Directory** lehetőséget.

3. Válassza a **Kezelés** területen a **Vállalati alkalmazások** lehetőséget.

4. Keresse meg a Microsoft alkalmazásazonosítót `0bfc4568-a4ba-4c58-bd3e-5d3e76bd7fff` a névvel `Dynamics 365 AI for Customer Insights`.

5. Ha talál egyező rekordot, az azt jelenti, hogy a szolgáltatásnév már létezik. 
   
   :::image type="content" source="media/ADLS-SP-AlreadyProvisioned.png" alt-text="Képernyőkép egy meglévő szolgáltatásnévről.":::
   
6. Ha a rendszer nem ad vissza eredményt, hozzon létre egy új egyszerű szolgáltatásnevet.

### <a name="create-a-new-service-principal"></a>Új egyszerű szolgáltatásnév létrehozása

1. Telepítse az Azure Active Directory PowerShell vagy Graph legújabb verzióját. További tájékoztatásért menjen az [Azure Active Directory PowerShell telepítése a Graph szolgáltatáshoz](/powershell/azure/active-directory/install-adv2) részbe.

   1. A számítógépen nyomja le a Windows gombot a billentyűzeten, és keressen a **Windows PowerShell** kifejezésre, és válassza a **Futtatás rendszergazdaként** lehetőséget.
   
   1. A megnyíló PowerShell ablakában adja meg az `Install-Module AzureAD` értéket.

2. Hozza létre a Customer Insights szolgáltatásnevét az Azure AD PowerShell modullal.

   1. A PowerShell ablakában adja meg az `Connect-AzureAD -TenantId "[your Directory ID]" -AzureEnvironmentName Azure` értéket. Cserélje le *[a címtárazonosítóját]* az Azure-előfizetés tényleges címtárazonosítójára, ahol létre szeretné hozni az egyszerű szolgáltatásnevet. Az `AzureEnvironmentName` környezetinév-paraméter nem kötelező.
  
   1. Adja meg a `New-AzureADServicePrincipal -AppId "0bfc4568-a4ba-4c58-bd3e-5d3e76bd7fff" -DisplayName "Dynamics 365 AI for Customer Insights"`. Ez a parancs létrehozza a Customer Insights szolgáltatáselemzőjét a kiválasztott Azure-előfizetésen. 

## <a name="grant-permissions-to-the-service-principal-to-access-the-storage-account"></a>Engedélyek biztosítása az egyszerű szolgáltatásnév számára a tárfiók eléréséhez

Nyissa meg az Azure Portal webhelyet, és adjon engedélyeket a Szolgáltatásnévnek a Customer Insightsban használni kívánt tárfiókhoz.

1. Nyissa meg az [Azure rendszergazdai portált](https://portal.azure.com), és jelentkezzen be a szervezetbe.

1. Nyissa meg azt a tárfiókot, amelyhez a Customer Insights szolgáltatásfőkiszolgálójának hozzáférést szeretne biztosítani.

1. A bal oldali ablaktáblában válassza a **Hozzáférés-vezérlő (IAM)** lehetőséget, majd válassza a **Hozzáadás** > **Szerepkör hozzárendelés hozzáadása** lehetőséget.

   :::image type="content" source="media/ADLS-SP-AddRoleAssignment.png" alt-text="Képernyőkép az Azure portálról, miközben szerepkör-hozzárendelést ad hozzá.":::

1. Állítsa be a **Szerepkör hozzárendelés hozzáadása** ablaktáblán állítsa be a következő tulajdonságokat:
   - szerepkör: **Storage Blob adat-közreműködő**
   - Rendeljen hozzáférést ehhez: **Felhasználó, csoport vagy egyszerű szolgáltatásnév**
   - Tagok kiválasztása: **Dynamics 365 AI for Customer Insights** (az [eljárás korábbi szakaszában létrehozott szolgáltatásnév](#create-a-new-service-principal))

1.  Válassza a Véleményezés + hozzárendelés **lehetőséget**.

A módosítások feltöltése 15 percet is igénybe vehet.

## <a name="enter-the-azure-resource-id-or-the-azure-subscription-details-in-the-storage-account-attachment-to-customer-insights"></a>Adja meg az Azure-erőforrás-azonosítót vagy az Azure-előfizetés részleteit a Tárfiók Ügyfélelemzés mellékletében

A Customer Insights szolgáltatásban adat lake storage-fiókot csatolhat a kimeneti adatok [tárolásához vagy](manage-environments.md) adatforrás [ként való használatához](connect-dataverse-managed-lake.md). Ez a beállítás lehetővé teszi, hogy erőforrás-alapú vagy előfizetéses megközelítést válasszon. A választott megközelítéstől függően kövesse az alábbi szakaszok egyikében található eljárást.

### <a name="resource-based-storage-account-connection"></a>Erőforrás-alapú tárfiókkapcsolat

1. Keresse fel az [Azure rendszergazdai portált](https://portal.azure.com), jelentkezzen be az előfizetésbe, és nyissa meg a tárfiókot.

1. A bal oldali ablaktáblában válassza a **Beállítások** > **Tulajdonságok** lehetőséget.

1. Másolja a tárfiók erőforrás-azonosítójának értékét.

   :::image type="content" source="media/ADLS-SP-ResourceId.png" alt-text="Másolja a tárfiók erőforrás-azonosítóját.":::

1. Az Ügyfélelemzések szolgáltatásban szúrja be az erőforrás-azonosítót a tárfiók kapcsolatának képernyőjén megjelenő erőforrásmezőbe.

   :::image type="content" source="media/ADLS-SP-ResourceIdConnection.png" alt-text="Adja meg a tárfiók erőforrás-azonosítójának adatait.":::   

1. Folytassa a Customer Insights további lépéseivel a tárfiók csatolásához.

### <a name="subscription-based-storage-account-connection"></a>Előfizetés-alapú tárfiókkapcsolat

1. Keresse fel az [Azure rendszergazdai portált](https://portal.azure.com), jelentkezzen be az előfizetésbe, és nyissa meg a tárfiókot.

1. A bal oldali ablaktáblában válassza a **Beállítások** > **Tulajdonságok** lehetőséget.

1. Tekintse át az Előfizetés, az **Erőforrás csoport** és a **tárfiók nevét**, és győződjön meg arról, hogy a megfelelő értékeket választotta ki az Ügyfélelemzésben **.**

1. A Customer Insights alkalmazásban válassza ki a megfelelő mezők értékeit a tárfiók csatolásakor.

1. Folytassa a Customer Insights további lépéseivel a tárfiók csatolásához.


[!INCLUDE [footer-include](includes/footer-banner.md)]