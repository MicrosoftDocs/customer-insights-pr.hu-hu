---
title: Azure Synapse adatforrás csatlakoztatása (előzetes verzió)
description: 'Adatbázis Azure Synapse használata adatforrás a következőben: Dynamics 365 Customer Insights.'
ms.date: 07/26/2022
ms.reviewer: v-wendysmith
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: mukeshpo
ms.author: mukeshpo
manager: shellyha
ms.openlocfilehash: 675fd03c44a7a7a492b111895d79c2e77f93a5b5
ms.sourcegitcommit: 4ba74816ebfa46412c64c40a61e1f31c4ccc40f2
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/03/2022
ms.locfileid: "9738159"
---
# <a name="connect-an-azure-synapse-analytics-data-source-preview"></a>Azure Synapse Analytics adatforrás csatlakoztatása (előzetes verzió)

Azure Synapse Analytics egy nagyvállalati elemzési szolgáltatás, amely felgyorsítja az adattárházak és big data rendszerek elemzéséhez szükséges időt. Azure Synapse Analytics egyesíti a vállalati adattárházakban használt SQL-technológiák, a big data-hoz használt Spark-technológiák, a napló- és idősorozat-elemzéshez használt Adatkezelő, az adatintegrációs folyamatok és az ETL/ELT, valamint a más Azure-szolgáltatásokkal, például Power BI a , Cosmos DB és az AzureML-lel való mély integráció.

További információt az Áttekintés [Azure Synapse című témakörben talál](/azure/synapse-analytics/overview-what-is).

## <a name="prerequisites"></a>Előfeltételek

> [!NOTE]
> Azok a Synapse-munkaterületek, amelyeken engedélyezve van [a](/azure/synapse-analytics/security/synapse-workspace-ip-firewall) tűzfal, jelenleg nem támogatottak.
> [!IMPORTANT]
> A leírt módon állítsa be az összes **szerepkör-hozzárendelést**.  

**A Customer Insights** alkalmazásban:

* Rendszergazdai **szerepkörrel rendelkezik** a Customer Insights szolgáltatásban. További információ a felhasználói engedélyekről a [Customer Insights](permissions.md#add-users) szolgáltatásban.

**Az Azure-ban**:

- Aktív Azure-előfizetés.

- Ha új Azure Data Lake Storage Gen2-fiókot használ, a Customer Insights szolgáltatásnévnek, azaz a *"Dynamics 365 AI for Customer Insights*" tárolási blobadatokra közreműködő **engedélyekre van szüksége**. További információ a [Customer Insights Azure Data Lake Storage szolgáltatásnévvel való csatlakozásáról](connect-service-principal.md). A Data Lake Storage Gen2 szolgáltásnál **engedélyezni kell** a [hierarchikus névteret](/azure/storage/blobs/data-lake-storage-namespace).

- A munkaterület erőforráscsoportjában Azure Synapse található *a "Dynamics 365 AI for Customer Insights" szolgáltatásnév* és a *Customer Insights* felhasználója legalább **olvasó** engedéllyel kell rendelkeznie. További információk: [Azure-szerepkörök hozzárendelése az Azure Portal használatával](/azure/role-based-access-control/role-assignments-portal).

- A *felhasználónak* **Storage Blob Data-közreműködő** engedéllyel kell rendelkeznie ahhoz az Azure Data Lake Storage Gen2-fiókhoz, amelyben az adatok találhatók, és amely össze lett kapcsolva az Azure Synapse-munkaterülettel. További információ arról, [hogyan rendelhető hozzá az Azure Portal használatával a blobhoz és a feldolgozási sor adataihoz való hozzáférésre szolgáló Azure-szerepkör](/azure/storage/common/storage-auth-aad-rbac-portal) és részletek [a Storage Blob Data közreműködői engedélyéről](/azure/role-based-access-control/built-in-roles#storage-blob-data-contributor).

- Az *[Azure Synapse-munkaterület felügyelt identitásához](/azure/synapse-analytics/security/synapse-workspace-managed-identity)* a **Storage Blob Data közreműködői** engedélyével kell rendelkezni abban az Azure Data Lake Storage Gen2-fiókban, ahol az adatok találhatók, és amelyet összekapcsoltak az Azure Synapse-munkaterülettel. További információ arról, [hogyan rendelhető hozzá az Azure Portal használatával a blobhoz és a feldolgozási sor adataihoz való hozzáférésre szolgáló Azure-szerepkör](/azure/storage/common/storage-auth-aad-rbac-portal) és részletek [a Storage Blob Data közreműködői engedélyéről](/azure/role-based-access-control/built-in-roles#storage-blob-data-contributor).

- A munkaterületen Azure Synapse a Customer Insights szolgáltatásnévnek, amely a "Dynamics 365 AI for Customer Insights *", hozzá kell* rendelnie a **Synapse-rendszergazda** szerepkört. A **felhasználónak** legalább egy **Synapse-közreműködő** szerepkörre van szüksége a munkaterülethez rendelve. További információ: [A hozzáférés-vezérlés beállítása a Synapse-munkaterülethez](/azure/synapse-analytics/security/how-to-set-up-access-control).

- Ha a Customer Insights-környezet a saját [tulajdonában Azure Data Lake Storage](own-data-lake-storage.md) tárolja az adatokat, a kapcsolatot Azure Synapse Analytics beállító felhasználónak legalább a beépített olvasó **szerepkörre van szüksége a Data Lake Storage-fiókban**. További információk: [Azure-szerepkörök hozzárendelése az Azure Portal használatával](/azure/role-based-access-control/role-assignments-portal).

## <a name="connect-to-the-data-lake-database-in-azure-synapse-analytics"></a>Csatlakozás a Data Lake-adatbázishoz a Azure Synapse Analytics

1. Válassza az **Adatok** > **Adatforrások** lehetőséget.

1. Válassza az **Adatforrás hozzáadása** lehetőséget.

1. Válassza az **Azure Synapse Analytics (Előnézet)** módszert.

   :::image type="content" source="media/data_sources_synapse.png" alt-text="A Synapse Analytics-adatokhoz való kapcsolódásra szolgáló párbeszédpanel":::
  
1. **Adja meg a adatforrás nevét** és opcionális **leírását**.

1. Válasszon ki egy [elérhető kapcsolatot](connections.md) , Azure Synapse Analytics vagy [hozzon létre egy újat](export-azure-synapse-analytics.md#set-up-connection-to-azure-synapse).

1. Válasszon ki egy adatbázist **a** kiválasztott Azure Synapse Analytics kapcsolathoz csatlakoztatott munkaterületről, majd válassza a Tovább **lehetőséget**. Jelenleg csak a Lake adatbázis típusú *adatbázist* támogatjuk.

1. Válassza ki a betölteni kívánt entitásokat a csatlakoztatott adatbázisból, majd válassza a Tovább **lehetőséget**.

1. Ha szükséges, válassza ki azokat az adatentitásokat, amelyeken engedélyezni szeretné az adatprofil-készítést.

1. Válassza a Mentés **lehetőséget a kijelölés alkalmazásához, és kezdje el az újonnan létrehozott adatforrás a Lake adatbázistábláihoz csatolt adatok betöltését a** Azure Synapse Analytics. Megnyílik az Adatforrások **lap, amelyen az** új adatforrás frissítési **állapotban látható**.

   [!INCLUDE [progress-details-include](includes/progress-details-pane.md)]

Az adatok betöltése időbe telhet. A sikeres frissítés után a betöltött adatok az Entitások [**lapon tekinthetők át**](entities.md).

[!INCLUDE [footer-include](includes/footer-banner.md)]
