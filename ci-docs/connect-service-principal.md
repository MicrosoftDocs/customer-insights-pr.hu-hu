---
title: Csatlakozás egy Azure Data Lake Storage-fiókhoz egy Azure szolgáltatásnév segítségével
description: Azure szolgáltatásnév használata a saját adattó csatlakoztatására.
ms.date: 05/31/2022
ms.subservice: audience-insights
ms.topic: how-to
author: adkuppa
ms.author: adkuppa
ms.reviewer: mhart
manager: shellyha
searchScope:
- ci-system-security
- customerInsights
ms.openlocfilehash: 949caa73578dbe0a511726ec045c0fd5f4621de4
ms.sourcegitcommit: dca46afb9e23ba87a0ff59a1776c1d139e209a32
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/29/2022
ms.locfileid: "9082239"
---
# <a name="connect-to-an-azure-data-lake-storage-account-by-using-an-azure-service-principal"></a>Csatlakozás egy Azure Data Lake Storage-fiókhoz egy Azure szolgáltatásnév segítségével

Ez a cikk azt ismerteti, hogyan csatlakozhat Dynamics 365 Customer Insights egy Azure Data Lake Storage fiókhoz egy Azure-szolgáltatásnév használatával a tárfiókkulcsok helyett.

Az Azure-szolgáltatásokat használó automatizált eszközöknek mindig korlátozott engedélyekkel kell rendelkezniük. Ahelyett, hogy az alkalmazások teljes jogosultsággal rendelkező felhasználóként jelentkezzenek be, az Azure egyszerű szolgáltatásneveket biztosít. A szolgáltatásnév segítségével biztonságosan [hozzáadhat vagy szerkeszthet egy Common Data Model mappát adatforrás](connect-common-data-model.md), vagy [létrehozhat vagy frissíthet egy környezetet](create-environment.md).

> [!IMPORTANT]
>
> - A szolgáltatásnevet használni használni használni kívánt Data Lake Storage-fióknak Gen2-nek kell lennie, és engedélyeznie kell [hierarchikus névteret](/azure/storage/blobs/data-lake-storage-namespace). Az Azure Data Lake Gen1-tárfiókok nem támogatottak.
> - A szolgáltatásnév létrehozásához rendszergazdai engedélyekre van szüksége a Azure-bérlő.

## <a name="create-an-azure-service-principal-for-customer-insights"></a>Azure szolgáltatásnév létrehozása a Customer Insightshoz

Mielőtt létrehozna egy új szolgáltatásnevet a Customer Insights szolgáltatáshoz, ellenőrizze, hogy létezik-e már a szervezetben.

### <a name="look-for-an-existing-service-principal"></a>Meglévő egyszerű szolgáltatásnév keresése

1. Nyissa meg az [Azure rendszergazdai portált](https://portal.azure.com), és jelentkezzen be a szervezetbe.

2. Az **Azure-szolgáltatások** csoportban válassza az **Azure Active Directory** lehetőséget.

3. A Kezelés **alatt** válassza a Microsoft-alkalmazás **lehetőséget**.

4. Adjon hozzá egy szűrőt az alkalmazásazonosítóhoz **,**`0bfc4568-a4ba-4c58-bd3e-5d3e76bd7fff` vagy keressen rá a névvel `Dynamics 365 AI for Customer Insights`.

5. Ha talál egyező rekordot, az azt jelenti, hogy a szolgáltatásnév már létezik.

   :::image type="content" source="media/ADLS-SP-AlreadyProvisioned.png" alt-text="Képernyőkép egy meglévő szolgáltatásnévről.":::

6. Ha a rendszer nem ad vissza eredményt, [létrehozhat egy új szolgáltatásnevet](#create-a-new-service-principal). A legtöbb esetben már létezik, és csak a szolgáltatásnévnek kell engedélyeket adnia a tárfiók eléréséhez.

## <a name="grant-permissions-to-the-service-principal-to-access-the-storage-account"></a>Engedélyek biztosítása az egyszerű szolgáltatásnév számára a tárfiók eléréséhez

A Azure Portal, és engedélyeket adhat a szolgáltatásnévnek a Customer Insightsban használni kívánt tárfiókhoz. A következő szerepkörök egyikét hozzá kell rendelni a tárfiókhoz vagy a tárolóhoz:

|Megbízólevél|Követelmények|
|----------|------------|
|Jelenleg bejelentkezett felhasználó|**Szerepkör**: Storage Blob Data olvasó, Storage Blob közreműködő vagy Storage Blob tulajdonosa.<br>**Szint**: Engedélyek adhatók a tárfiókhoz vagy a tárolóhoz.</br>|
|Customer Insights szolgáltatásnév -<br>Használat Azure Data Lake Storage adatforrás</br>|1. lehetőség<ul><li>**Szerepkör**: Storage Blob Data olvasó, Storage Blob Data közreműködő vagy Storage Blob Data Owner.</li><li>**Szint**: Engedélyeket kell adni a tárfiókon.</li></ul>2 *. lehetőség (a tárfiókhoz való hozzáférés megosztása nélkül)*<ul><li>**1**. szerepkör: Storage Blob Data olvasó, Storage Blob Data közreműködő vagy Storage Blob Data Owner.</li><li>**Szint**: Az engedélyeket meg kell adni a tárolón.</li><li>**2**. szerepkör: Storage Blob adatdelegátor.</li><li>**Szint**: Engedélyeket kell adni a tárfiókon.</li></ul>|
|Customer Insights szolgáltatásnév - <br>Használat Azure Data Lake Storage kimenetként vagy célhelyként</br>|1. lehetőség<ul><li>**Szerepkör**: Storage Blob Data közreműködő vagy Storage Blob tulajdonosa.</li><li>**Szint**: Engedélyeket kell adni a tárfiókon.</li></ul>2 *. lehetőség (a tárfiókhoz való hozzáférés megosztása nélkül)*<ul><li>**Szerepkör**: Storage Blob Data közreműködő vagy Storage Blob tulajdonosa.</li><li>**Szint**: Az engedélyeket meg kell adni a tárolón.</li><li>**2**. szerepkör: Storage Blob delegátor.</li><li>**Szint**: Engedélyeket kell adni a tárfiókon.</li></ul>|

1. Nyissa meg az [Azure rendszergazdai portált](https://portal.azure.com), és jelentkezzen be a szervezetbe.

1. Nyissa meg azt a tárfiókot, amelyhez hozzá szeretne férni a Customer Insights szolgáltatásnév számára.

1. A bal oldali ablaktáblában válassza a **Hozzáférés-vezérlő (IAM)** lehetőséget, majd válassza a **Hozzáadás** > **Szerepkör hozzárendelés hozzáadása** lehetőséget.

   :::image type="content" source="media/ADLS-SP-AddRoleAssignment.png" alt-text="Képernyőkép az Azure portálról, miközben szerepkör-hozzárendelést ad hozzá.":::

1. Állítsa be a **Szerepkör hozzárendelés hozzáadása** ablaktáblán állítsa be a következő tulajdonságokat:
   - Szerepkör: Storage Blob Data olvasó, Storage Blob közreműködő vagy Storage Blob tulajdonosa a fent felsorolt hitelesítő adatok alapján.
   - Rendeljen hozzáférést ehhez: **Felhasználó, csoport vagy egyszerű szolgáltatásnév**
   - Tagok kiválasztása: **Dynamics 365 AI for Customer Insights** (az [eljárás korábbi szakaszában keresett szolgáltatásnév](#create-a-new-service-principal))

1. Válassza az Áttekintés + hozzárendelés **lehetőséget**.

A módosítások feltöltése 15 percet is igénybe vehet.

## <a name="enter-the-azure-resource-id-or-the-azure-subscription-details-in-the-storage-account-attachment-to-customer-insights"></a>Adja meg az Azure-erőforrás azonosítóját vagy az Azure-előfizetés adatait a Customer Insights tárfiókjának mellékletében

A Customer Insightsban csatolhat egy Data Lake Storage-fiókot a kimeneti adatok [tárolásához](manage-environments.md), vagy [adatforrás](connect-dataverse-managed-lake.md). Ez a beállítás lehetővé teszi, hogy erőforrás-alapú vagy előfizetéses megközelítést válasszon. A választott megközelítéstől függően kövesse az alábbi szakaszok egyikében található eljárást.

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

### <a name="create-a-new-service-principal"></a>Új egyszerű szolgáltatásnév létrehozása

1. Telepítse az Azure Active Directory PowerShell vagy Graph legújabb verzióját. További tájékoztatásért menjen az [Azure Active Directory PowerShell telepítése a Graph szolgáltatáshoz](/powershell/azure/active-directory/install-adv2) részbe.

   1. A számítógépen nyomja meg a Windows billentyűt a billentyűzeten, keresse meg a **Windows PowerShellt**, és válassza a Futtatás rendszergazdaként **lehetőséget**.

   1. A megnyíló PowerShell ablakában adja meg az `Install-Module AzureAD` értéket.

2. Hozza létre a Customer Insights szolgáltatásnevét az Azure AD PowerShell modullal.

   1. A PowerShell ablakában adja meg az `Connect-AzureAD -TenantId "[your Directory ID]" -AzureEnvironmentName Azure` értéket. Cserélje le *a [címtárazonosítót]* annak az Azure-előfizetésnek a tényleges címtár-azonosítójára, amelyben létre szeretné hozni a szolgáltatásnevet. Az `AzureEnvironmentName` környezetinév-paraméter nem kötelező.
  
   1. Adja meg a `New-AzureADServicePrincipal -AppId "0bfc4568-a4ba-4c58-bd3e-5d3e76bd7fff" -DisplayName "Dynamics 365 AI for Customer Insights"`. Ez a parancs létrehozza a Customer Insights szolgáltatásnévét a kiválasztott Azure-előfizetésben.

[!INCLUDE [footer-include](includes/footer-banner.md)]
