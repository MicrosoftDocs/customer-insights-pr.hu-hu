---
title: Azure Synapse adatforrás csatlakoztatása (előzetes verzió)
description: Azure Synapse Adatbázis használata adatforrás a Dynamics 365 Customer Insights.
ms.date: 07/26/2022
ms.reviewer: v-wendysmith
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: mukeshpo
ms.author: mukeshpo
manager: shellyha
ms.openlocfilehash: 7bc0c3614e6dd39fbd65ae098ed679d95d09de9d
ms.sourcegitcommit: 086f75136132d561cd78a4c2cb1e1933e2301f32
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/11/2022
ms.locfileid: "9259801"
---
# <a name="connect-an-azure-synapse-analytics-data-source-preview"></a>Azure Synapse Analytics adatforrás csatlakoztatása (előzetes verzió)

Azure Synapse Analytics egy vállalati elemzési szolgáltatás, amely felgyorsítja az adattárházak és big data-rendszerek közötti betekintéshez szükséges időt. Azure Synapse Analytics egyesíti a vállalati adattárházban használt SQL-technológiák, a big datahoz használt Spark-technológiák, a napló- és idősorozat-elemzésekhez használt Adatkezelő, az adatintegrációs és ETL-/ELT-folyamatok, valamint a más Azure-szolgáltatásokkal, például Power BI az Cosmos DB AzureML-lel való mély integrációban használt SQL-technológiákat.

További információt az áttekintésben talál [Azure Synapse](/azure/synapse-analytics/overview-what-is).

## <a name="prerequisites"></a>Előfeltételek

> [!NOTE]
> Azok a Synapse-munkaterületek, amelyeken engedélyezve van [a](/azure/synapse-analytics/security/synapse-workspace-ip-firewall) tűzfal, jelenleg nem támogatottak.
> [!IMPORTANT]
> A leírt módon állítsa be az összes **szerepkör-hozzárendelést**.  

**A Customer Insights szolgáltatásban**:

* Rendszergazdai **szerepkörrel** rendelkezik a Customer Insights szolgáltatásban. További információ a felhasználói engedélyekről [a Customer Insights szolgáltatásban](permissions.md#add-users).

**Az Azure-ban**:

- Aktív Azure-előfizetés.

- Új Azure Data Lake Storage Gen2-fiók használata esetén a *Customer Insights* szolgáltatásnévnek, azaz "Dynamics 365 AI for Customer Insights" szolgáltatásnévnek Storage blobadatokra közreműködő **engedélyekre van szüksége**. További információ a Customer Insights [szolgáltatásnévvel való csatlakozásáról.Azure Data Lake Storage](connect-service-principal.md) A Data Lake Storage Gen2 szolgáltásnál **engedélyezni kell** a [hierarchikus névteret](/azure/storage/blobs/data-lake-storage-namespace).

- Az erőforráscsoporton található a Azure Synapse munkaterület, a *"Dynamics 365 AI for Customer Insights" szolgáltatásnévhez* és a *Customer Insights* felhasználóhoz legalább **olvasó** engedélyt kell rendelni. További információk: [Azure-szerepkörök hozzárendelése az Azure Portal használatával](/azure/role-based-access-control/role-assignments-portal).

- A *felhasználónak* **Storage Blob Data-közreműködő** engedéllyel kell rendelkeznie ahhoz az Azure Data Lake Storage Gen2-fiókhoz, amelyben az adatok találhatók, és amely össze lett kapcsolva az Azure Synapse-munkaterülettel. További információ arról, [hogyan rendelhető hozzá az Azure Portal használatával a blobhoz és a feldolgozási sor adataihoz való hozzáférésre szolgáló Azure-szerepkör](/azure/storage/common/storage-auth-aad-rbac-portal) és részletek [a Storage Blob Data közreműködői engedélyéről](/azure/role-based-access-control/built-in-roles#storage-blob-data-contributor).

- Az *[Azure Synapse-munkaterület felügyelt identitásához](/azure/synapse-analytics/security/synapse-workspace-managed-identity)* a **Storage Blob Data közreműködői** engedélyével kell rendelkezni abban az Azure Data Lake Storage Gen2-fiókban, ahol az adatok találhatók, és amelyet összekapcsoltak az Azure Synapse-munkaterülettel. További információ arról, [hogyan rendelhető hozzá az Azure Portal használatával a blobhoz és a feldolgozási sor adataihoz való hozzáférésre szolgáló Azure-szerepkör](/azure/storage/common/storage-auth-aad-rbac-portal) és részletek [a Storage Blob Data közreműködői engedélyéről](/azure/role-based-access-control/built-in-roles#storage-blob-data-contributor).

- A munkaterületen a Azure Synapse *Customer Insights* szolgáltatásnévéhez, amely "Dynamics 365 AI for Customer Insights", synapse-rendszergazdai **szerepkört kell** hozzárendelni. További információ: [A hozzáférés-vezérlés beállítása a Synapse-munkaterülethez](/azure/synapse-analytics/security/how-to-set-up-access-control).

- Ha a Customer Insights-környezet a sajátjában [Azure Data Lake Storage](own-data-lake-storage.md) tárolja az adatokat, a kapcsolatot beállító felhasználónak Azure Synapse Analytics legalább a Data Lake Storage-fiók beépített **olvasó** szerepkörére van szüksége. További információk: [Azure-szerepkörök hozzárendelése az Azure Portal használatával](/azure/role-based-access-control/role-assignments-portal).

## <a name="connect-to-the-data-lake-database-in-azure-synapse-analytics"></a>Csatlakozás a Data Lake-adatbázishoz Azure Synapse Analytics

1. Válassza az **Adatok** > **Adatforrások** lehetőséget.

1. Válassza az **Adatforrás hozzáadása** lehetőséget.

1. Válassza az **Azure Synapse Analytics (előnézeti)** metódust.

   :::image type="content" source="media/data_sources_synapse.png" alt-text="Párbeszédpanel a Synapse Analytics-adatokhoz való csatlakozáshoz":::
  
1. **Adja meg a adatforrás nevét** és egy opcionális **leírást**.

1. Válasszon ki egy [elérhető kapcsolatot](connections.md), Azure Synapse Analytics vagy [hozzon létre egy újat](export-azure-synapse-analytics.md#set-up-connection-to-azure-synapse).

1. Válasszon ki egy **adatbázist a kiválasztott** kapcsolatban csatlakoztatott munkaterületről, majd válassza a Tovább Azure Synapse Analytics gombot **·**. Jelenleg csak a Lake adatbázistípust *támogatjuk*.

1. Válassza ki a csatlakoztatott adatbázisból betölteni kívánt entitásokat, majd kattintson a Tovább **gombra**.

1. Igény szerint válassza ki azokat az adatentitásokat, amelyeken engedélyezni szeretné az adatprofil-készítést.

1. Válassza a Mentés **lehetőséget** a kijelölés alkalmazásához, és az újonnan létrehozott adatforrás származó adatok betöltésének megkezdéséhez, amely a Lake-adatbázistáblákhoz Azure Synapse Analytics van csatolva. **Megnyílik az Adatforrások** lap, amelyen az új adatforrás a Frissítés **állapot.**

   [!INCLUDE [progress-details-include](includes/progress-details-pane.md)]

Az adatok betöltése időbe telhet. A sikeres frissítés után a betöltött adatok az [**Entitások oldalon ellenőrizhetők**](entities.md).

[!INCLUDE [footer-include](includes/footer-banner.md)]
