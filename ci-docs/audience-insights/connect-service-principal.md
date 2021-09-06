---
title: Csatlakozás egy Azure Data Lake Storage-fiókhoz egy szolgáltatásnév segítségével
description: Azure szolgáltatásnév használata a saját adattó csatlakoztatására.
ms.date: 07/23/2021
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: adkuppa
ms.author: adkuppa
ms.reviewer: mhart
manager: shellyha
ms.openlocfilehash: 845d1f55eb99f2adf9b437124addec4f6d016fec
ms.sourcegitcommit: 1c396394470df8e68c2fafe3106567536ff87194
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/30/2021
ms.locfileid: "7461151"
---
# <a name="connect-to-an-azure-data-lake-storage-account-by-using-an-azure-service-principal"></a>Csatlakozás egy Azure Data Lake Storage-fiókhoz egy Azure szolgáltatásnév segítségével
<!--note from editor: The Cloud Style Guide would have us just use "Azure Data Lake Storage" to mean the current version, unless the old version (Gen1) is mentioned. I've followed this guidance, even though it seems that our docs and Azure docs are all over the map on this.-->
Az Azure-szolgáltatásokat használó automatizált eszközöknek mindig korlátozott engedélyekkel kell rendelkezniük. Ahelyett, hogy az alkalmazások teljes jogosultsággal rendelkező felhasználóként jelentkezzenek be, az Azure egyszerű szolgáltatásneveket biztosít. A cikkből megtudhatja, hogyan kapcsolódhat a Dynamics 365 Customer Insights alkalmazással egy Azure Data Lake Storage fiókhoz tárfiókkulcsok helyett egy Azure szolgáltatásnév használatával. 

A szolgáltatásnév segítségével biztonságos módon [hozzáadhat vagy szerkeszthet egy Common Data Model mappát adatforrásként](connect-common-data-model.md), illetve [létrehozhat vagy frissíthet egy környezetet](get-started-paid.md).<!--note from editor: Suggested. Or it could be ", or create a new environment or update an existing one". I think "new" is implied with "create". The comma is necessary.-->

> [!IMPORTANT]
> - A Data Lake Storage-fiók, amely használni fogja<!--note from editor: Suggested. Or perhaps it could be "The Data Lake Storage account to which you want to give access to the service principal..."--> a szolgáltatásnevet esetében a [hierarchikus névteret engedélyezni kell](/azure/storage/blobs/data-lake-storage-namespace).
> - Az egyszerű szolgáltatásnév létrehozásához rendszergazdai előfizetéssel kell rendelkezni az Azure-előfizetéshez.

## <a name="create-an-azure-service-principal-for-customer-insights"></a>Azure szolgáltatásnév létrehozása a Customer Insightshoz

Mielőtt létrehoznál egy új szolgáltatásnevet az célközönséggel kapcsolatos információkhoz vagy az elkötelezettségi információkhoz, ellenőrizze, hogy szerepel-e már a szervezetben.

### <a name="look-for-an-existing-service-principal"></a>Meglévő egyszerű szolgáltatásnév keresése

1. Nyissa meg az [Azure rendszergazdai portált](https://portal.azure.com), és jelentkezzen be a szervezetbe.

2. Az **Azure-szolgáltatások** csoportban válassza az **Azure Active Directory** lehetőséget.

3. Válassza a **Kezelés** területen a **Vállalati alkalmazások** lehetőséget.

4. Keresse meg a Microsoft<!--note from editor: Via Microsoft Writing Style Guide.--> alkalmazásazonosítót:
   - Célközönség információk: `0bfc4568-a4ba-4c58-bd3e-5d3e76bd7fff` `Dynamics 365 AI for Customer Insights` névvel
   - elkötelezettségi információk: `ffa7d2fe-fc04-4599-9f6d-7ca06dd0c4fd` `Dynamics 365 AI for Customer Insights engagement insights` névvel

5. Ha talál egyező rekordot, az azt jelenti, hogy a szolgáltatásnév már létezik. 
   
   :::image type="content" source="media/ADLS-SP-AlreadyProvisioned.png" alt-text="Képernyőkép egy meglévő szolgáltatásnévről.":::
   
6. Ha a rendszer nem ad vissza eredményt, hozzon létre egy új egyszerű szolgáltatásnevet.

>[!NOTE]
>A Dynamics 365 Customer Insights teljes kihasználása érdekében javasoljuk, hogy mindkét alkalmazást vegye fel a szolgáltatásnévhez.<!--note from editor: Using the note format is suggested, just so this doesn't get lost by being tucked up in the step.-->

### <a name="create-a-new-service-principal"></a>Új egyszerű szolgáltatásnév létrehozása
<!--note from editor: Some general formatting notes: The MWSG wants bold for text the user enters (in addition to UI strings and the settings users select), but there's plenty of precedent for using code format for entering text in PowerShell so I didn't change that. Note that italic should be used for placeholders, but not much else.-->
1. Telepítse az Azure Active Directory PowerShell vagy Graph legújabb verzióját. További tájékoztatásért menjen az [Azure Active Directory PowerShell telepítése a Graph szolgáltatáshoz](/powershell/azure/active-directory/install-adv2) részbe.

   1. A számítógépen nyomja le a Windows gombot a billentyűzeten, és keressen a **Windows PowerShell** kifejezésre, és válassza a **Futtatás rendszergazdaként** lehetőséget.<!--note from editor: Or should this be something like "search for **Windows PowerShell** and, if asked, select **Run as administrator**."?-->
   
   1. A megnyíló PowerShell ablakában adja meg az `Install-Module AzureAD` értéket.

2. Hozza létre a Customer Insights szolgáltatásnevét az Azure AD PowerShell modullal.

   1. A PowerShell ablakában adja meg az `Connect-AzureAD -TenantId "[your tenant ID]" -AzureEnvironmentName Azure` értéket. Cserélje le *"[bérlőazonosítóját]"*<!--note from editor: Edit okay? Or should the quotation marks stay in the command line, in which case it would be "Replace *[your tenant ID]* --> A bérlő tényleges azonosítójával, ahol létre szeretné hozni a szolgáltatásnevet. Az `AzureEnvironmentName` környezetinév-paraméter nem kötelező.
  
   1. Adja meg a `New-AzureADServicePrincipal -AppId "0bfc4568-a4ba-4c58-bd3e-5d3e76bd7fff" -DisplayName "Dynamics 365 AI for Customer Insights"`. Ez a parancs létrehozza az egyszerű szolgáltatásnevet a kiválasztott bérlő célközönség-információihoz. 

   1. Adja meg a `New-AzureADServicePrincipal -AppId "ffa7d2fe-fc04-4599-9f6d-7ca06dd0c4fd" -DisplayName "Dynamics 365 AI for Customer Insights engagement insights"`. Ez a parancs hozza létre a szolgáltatásnevet az elkötelezettségi információkhoz<!--note from editor: Edit okay?--> a kijelölt bérlőn.

## <a name="grant-permissions-to-the-service-principal-to-access-the-storage-account"></a>Engedélyek biztosítása az egyszerű szolgáltatásnév számára a tárfiók eléréséhez

Látogasson el az Azure portal webhelyre, és adja meg az egyszerű szolgáltatásnévre vonatkozó engedélyeket a tárfiók számára a célközönség-információkban való használatra.

1. Nyissa meg az [Azure rendszergazdai portált](https://portal.azure.com), és jelentkezzen be a szervezetbe.

1. Nyissa meg azt a tárfiókot, amelyhez a célközönség-információhoz tartozó egyszerű szolgáltatásnévnek hozzáféréssel kell rendelkeznie.

1. A bal oldali ablaktáblában válassza a **Hozzáférés-vezérlő (IAM)** lehetőséget, majd válassza a **Hozzáadás** > **Szerepkör hozzárendelés hozzáadása** lehetőséget.

   :::image type="content" source="media/ADLS-SP-AddRoleAssignment.png" alt-text="Képernyőkép az Azure portálról, miközben szerepkör-hozzárendelést ad hozzá.":::

1. Állítsa be a **Szerepkör hozzárendelés hozzáadása** ablaktáblán állítsa be a következő tulajdonságokat:
   - szerepkör: **Storage Blob adat-közreműködő**
   - Rendeljen hozzáférést ehhez: **Felhasználó, csoport vagy egyszerű szolgáltatásnév**
   - Válassza a következőt: **Dynamics 365 AI for Customer Insights** és **Dynamics 365 AI for Customer Insights elkötelezettségi információk** (az eljárás korábbi két [szolgáltatásneve](#create-a-new-service-principal))

1.  Válassza a **Mentés** parancsot.

A módosítások feltöltése 15 percet is igénybe vehet.

## <a name="enter-the-azure-resource-id-or-the-azure-subscription-details-in-the-storage-account-attachment-to-audience-insights"></a>Adja meg a célközönség-információkhoz csatolt tárfiókban az Azure forrásazonosítót vagy az Azure előfizetés részleteit

A lehetőségek a következők:<!--note from editor: Edit suggested only if this section is optional.--> csatolhat egy Data Lake Storage -fiókot a célközönség információkban a [kimeneti adatok tárolása](manage-environments.md) vagy [használhatja adatforrásként](connect-common-data-service-lake.md). Ez a beállítás lehetővé teszi, hogy erőforrás-alapú vagy előfizetéses megközelítést válasszon. A választott megközelítéstől függően kövesse az alábbi szakaszok egyikében található eljárást.<!--note from editor: Suggested.-->

### <a name="resource-based-storage-account-connection"></a>Erőforrás-alapú tárfiókkapcsolat

1. Keresse fel az [Azure rendszergazdai portált](https://portal.azure.com), jelentkezzen be az előfizetésbe, és nyissa meg a tárfiókot.

1. A bal oldali ablaktáblában válassza a **Beállítások** > **Tulajdonságok** lehetőséget.

1. Másolja a tárfiók erőforrás-azonosítójának értékét.

   :::image type="content" source="media/ADLS-SP-ResourceId.png" alt-text="Másolja a tárfiók erőforrás-azonosítóját.":::

1. A célközönséggel kapcsolatos információkban az erőforrás-azonosító a tárfiók kapcsolati képernyőjén jelenik meg az erőforrásmezőben.

   :::image type="content" source="media/ADLS-SP-ResourceIdConnection.png" alt-text="Adja meg a tárfiók erőforrás-azonosítójának adatait.":::   

1. Folytassa a többi lépést a célközönség-információkban, hogy csatolja a tárfiókot.

### <a name="subscription-based-storage-account-connection"></a>Előfizetés-alapú tárfiókkapcsolat

1. Keresse fel az [Azure rendszergazdai portált](https://portal.azure.com), jelentkezzen be az előfizetésbe, és nyissa meg a tárfiókot.

1. A bal oldali ablaktáblában válassza a **Beállítások** > **Tulajdonságok** lehetőséget.

1. Tekintse át az **Előfizetést**, az **Erőforráscsoportot** és a tárolási fiók **Nevét**, és ügyeljen rá, hogy célközönség-információknál jelölje ki a megfelelő értékeket.

1. Az célközönséggel kapcsolatos információkban válassza ki a tárfiók csatolásakor a megfelelő mezők értékeit.

1. Folytassa a többi lépést a célközönség-információkban, hogy csatolja a tárfiókot.


[!INCLUDE[footer-include](../includes/footer-banner.md)]