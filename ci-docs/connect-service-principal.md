---
title: Csatlakozás egy Azure Data Lake Storage-fiókhoz egy Azure szolgáltatásnév segítségével
description: Azure szolgáltatásnév használata a saját adattó csatlakoztatására.
ms.date: 08/12/2022
ms.subservice: audience-insights
ms.topic: how-to
author: adkuppa
ms.author: adkuppa
ms.reviewer: mhart
manager: shellyha
searchScope:
- ci-system-security
- customerInsights
ms.openlocfilehash: eba10068c48db5c147100c25a397bcc13b014784
ms.sourcegitcommit: 267c317e10166146c9ac2c30560c479c9a005845
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/16/2022
ms.locfileid: "9304200"
---
# <a name="connect-to-an-azure-data-lake-storage-account-by-using-an-azure-service-principal"></a>Csatlakozás egy Azure Data Lake Storage-fiókhoz egy Azure szolgáltatásnév segítségével

Dynamics 365 Customer Insights lehetőséget biztosít arra, hogy a tárfiókkulcsok helyett egy Azure-szolgáltatásnévvel csatlakozzon egy Azure Data Lake Storage fiókhoz.

Az Azure-szolgáltatásokat használó automatizált eszközöknek korlátozott engedélyekkel kell rendelkezniük. Ahelyett, hogy az alkalmazások teljes jogosultsággal rendelkező felhasználóként jelentkezzenek be, az Azure egyszerű szolgáltatásneveket biztosít. A szolgáltatásnév használatával biztonságosan [hozzáadhat vagy szerkeszthet egy Common Data Model mappát adatforrás](connect-common-data-model.md), vagy [létrehozhat vagy frissíthet egy környezetet](create-environment.md).

## <a name="prerequisites"></a>Előfeltételek

- A szolgáltatásnevet használni használni fog Data Lake Storage fióknak Gen2-nek kell lennie. Az Azure Data Lake Gen1-tárfiókok nem támogatottak.
- A Data Lake Storage-fiókban engedélyezve van [hierarchikus névtér](/azure/storage/blobs/data-lake-storage-namespace).
- Rendszergazdai engedélyek a Azure-bérlő, ha új szolgáltatásnevet kell létrehoznia.

## <a name="create-an-azure-service-principal-for-customer-insights"></a>Azure szolgáltatásnév létrehozása a Customer Insightshoz

Mielőtt létrehozna egy új szolgáltatásnevet a Customer Insights szolgáltatáshoz, ellenőrizze, hogy létezik-e már a szervezetben. A legtöbb esetben már létezik.

### <a name="look-for-an-existing-service-principal"></a>Meglévő egyszerű szolgáltatásnév keresése

1. Nyissa meg az [Azure rendszergazdai portált](https://portal.azure.com), és jelentkezzen be a szervezetbe.

2. Az **Azure-szolgáltatások** csoportban válassza az **Azure Active Directory** lehetőséget.

3. A Kezelés **alatt** válassza a Microsoft-alkalmazás **lehetőséget**.

4. Adjon hozzá egy szűrőt az alkalmazásazonosítóhoz **,**`0bfc4568-a4ba-4c58-bd3e-5d3e76bd7fff` vagy keressen rá a névvel `Dynamics 365 AI for Customer Insights`.

5. Ha talál egyező rekordot, az azt jelenti, hogy a szolgáltatásnév már létezik. [Adjon engedélyeket](#grant-permissions-to-the-service-principal-to-access-the-storage-account) a szolgáltatásnévnek a tárfiók eléréséhez.

   :::image type="content" source="media/ADLS-SP-AlreadyProvisioned.png" alt-text="Képernyőkép egy meglévő szolgáltatásnévről.":::

6. Ha nem ad vissza eredményt, [hozzon létre egy új szolgáltatásnevet](#create-a-new-service-principal).

### <a name="create-a-new-service-principal"></a>Új egyszerű szolgáltatásnév létrehozása

1. Telepítse az Azure Active Directory PowerShell vagy Graph legújabb verzióját. További tájékoztatásért menjen az [Azure Active Directory PowerShell telepítése a Graph szolgáltatáshoz](/powershell/azure/active-directory/install-adv2) részbe.

   1. A számítógépen nyomja meg a Windows billentyűt a billentyűzeten, keresse meg a **Windows PowerShellt**, és válassza a Futtatás rendszergazdaként **lehetőséget**.

   1. A megnyíló PowerShell ablakában adja meg az `Install-Module AzureAD` értéket.

2. Hozza létre a Customer Insights szolgáltatásnevét az Azure AD PowerShell modullal.

   1. A PowerShell ablakában adja meg az `Connect-AzureAD -TenantId "[your Directory ID]" -AzureEnvironmentName Azure` értéket. Cserélje le *a [címtárazonosítót]* annak az Azure-előfizetésnek a tényleges címtár-azonosítójára, amelyben létre szeretné hozni a szolgáltatásnevet. Az `AzureEnvironmentName` környezetinév-paraméter nem kötelező.
  
   1. Adja meg a `New-AzureADServicePrincipal -AppId "0bfc4568-a4ba-4c58-bd3e-5d3e76bd7fff" -DisplayName "Dynamics 365 AI for Customer Insights"`. Ez a parancs létrehozza a Customer Insights szolgáltatásnévét a kiválasztott Azure-előfizetésben.

## <a name="grant-permissions-to-the-service-principal-to-access-the-storage-account"></a>Engedélyek biztosítása az egyszerű szolgáltatásnév számára a tárfiók eléréséhez

Ahhoz, hogy engedélyeket adjon a szolgáltatásnévnek a Customer Insightsban használni kívánt tárfiókhoz, a következő szerepkörök egyikét kell hozzárendelni a tárfiókhoz vagy a tárolóhoz:

|Megbízólevél|Követelmények|
|----------|------------|
|Jelenleg bejelentkezett felhasználó|**Szerepkör**: Storage Blob Data olvasó, Storage Blob közreműködő vagy Storage Blob tulajdonosa.<br>**Szint**: A tárfiókon vagy a tárolón megadott engedélyek.</br>|
|Customer Insights szolgáltatásnév -<br>Használat Azure Data Lake Storage adatforrás</br>|1. lehetőség<ul><li>**Szerepkör**: Storage Blob Data olvasó, Storage Blob Data közreműködő vagy Storage Blob Data Owner.</li><li>**Szint**: A tárfiókon megadott engedélyek.</li></ul>2 *. lehetőség (a tárfiókhoz való hozzáférés megosztása nélkül)*<ul><li>**1**. szerepkör: Storage Blob Data olvasó, Storage Blob Data közreműködő vagy Storage Blob Data Owner.</li><li>**Szint**: A tárolón megadott engedélyek.</li><li>**2**. szerepkör: Storage Blob adatdelegátor.</li><li>**Szint**: A tárfiókon megadott engedélyek.</li></ul>|
|Customer Insights szolgáltatásnév - <br>Használat Azure Data Lake Storage kimenetként vagy célhelyként</br>|1. lehetőség<ul><li>**Szerepkör**: Storage Blob Data közreműködő vagy Storage Blob tulajdonosa.</li><li>**Szint**: A tárfiókon megadott engedélyek.</li></ul>2 *. lehetőség (a tárfiókhoz való hozzáférés megosztása nélkül)*<ul><li>**Szerepkör**: Storage Blob Data közreműködő vagy Storage Blob tulajdonosa.</li><li>**Szint**: A tárolón megadott engedélyek.</li><li>**2**. szerepkör: Storage Blob delegátor.</li><li>**Szint**: A tárfiókon megadott engedélyek.</li></ul>|

1. Nyissa meg az [Azure rendszergazdai portált](https://portal.azure.com), és jelentkezzen be a szervezetbe.

1. Nyissa meg azt a tárfiókot, amelyhez hozzá szeretne férni a Customer Insights szolgáltatásnév számára.

1. A bal oldali ablaktáblában válassza a **Hozzáférés-vezérlő (IAM)** lehetőséget, majd válassza a **Hozzáadás** > **Szerepkör hozzárendelés hozzáadása** lehetőséget.

   :::image type="content" source="media/ADLS-SP-AddRoleAssignment.png" alt-text="Képernyőkép az Azure portálról, miközben szerepkör-hozzárendelést ad hozzá.":::

1. Állítsa be a **Szerepkör hozzárendelés hozzáadása** ablaktáblán állítsa be a következő tulajdonságokat:
   - **Szerepkör**: Storage Blob Data olvasó, Storage Blob közreműködő vagy Storage Blob tulajdonosa a fent felsorolt hitelesítő adatok alapján.
   - **Hozzáférés hozzárendelése a következőkhöz**: **Felhasználó, csoport vagy szolgáltatásnév**
   - **Tagok kiválasztása** : **Dynamics 365 AI for Customer Insights** (az [eljárás korábbi szakaszában keresett szolgáltatásnév](#create-a-new-service-principal))

1. Válassza az Áttekintés + hozzárendelés **lehetőséget**.

A módosítások feltöltése 15 percet is igénybe vehet.

## <a name="enter-the-azure-resource-id-or-the-azure-subscription-details-in-the-storage-account-attachment-to-customer-insights"></a>Adja meg az Azure-erőforrás azonosítóját vagy az Azure-előfizetés adatait a Customer Insights tárfiókjának mellékletében

Csatoljon egy Data Lake Storage-fiókot a Customer Insights a kimeneti adatok [tárolásához](manage-environments.md) vagy [adatforrás](connect-dataverse-managed-lake.md) való használatához. Válasszon az [erőforrás-alapú](#resource-based-storage-account-connection) vagy az előfizetés-alapú [megközelítés közül,](#subscription-based-storage-account-connection) és kövesse az alábbi lépéseket.

### <a name="resource-based-storage-account-connection"></a>Erőforrás-alapú tárfiókkapcsolat

1. Keresse fel az [Azure rendszergazdai portált](https://portal.azure.com), jelentkezzen be az előfizetésbe, és nyissa meg a tárfiókot.

1. A bal oldali panelen válassza a **Végpontok gépház** > **·**.

1. Másolja a tárfiók erőforrás-azonosítójának értékét.

   :::image type="content" source="media/ADLS-SP-ResourceId.png" alt-text="Másolja a tárfiók erőforrás-azonosítóját.":::

1. A Customer Insightsban szúrja be az erőforrás-azonosítót a tárfiók kapcsolati képernyőjén megjelenő erőforrásmezőbe.

   :::image type="content" source="media/ADLS-SP-ResourceIdConnection.png" alt-text="Adja meg a tárfiók erőforrás-azonosítójának adatait.":::

1. Folytassa a Customer Insights további lépéseit a tárfiók csatolásához.

### <a name="subscription-based-storage-account-connection"></a>Előfizetés-alapú tárfiókkapcsolat

1. Keresse fel az [Azure rendszergazdai portált](https://portal.azure.com), jelentkezzen be az előfizetésbe, és nyissa meg a tárfiókot.

1. A bal oldali ablaktáblában válassza a **Beállítások** > **Tulajdonságok** lehetőséget.

1. Tekintse át az előfizetést **,** az **erőforráscsoportot** és a **tárfiók nevét**, és győződjön meg arról, hogy a megfelelő értékeket választja ki a Customer Insightsban.

1. A Customer Insightsban válassza ki a megfelelő mezők értékeit a tárfiók csatolásakor.

1. Folytassa a Customer Insights további lépéseit a tárfiók csatolásához.

[!INCLUDE [footer-include](includes/footer-banner.md)]
