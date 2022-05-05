---
title: 'Adatok betöltése innen: Azure Synapse Analytics'
description: Adatbázis Azure Synapse használata adatforrás a alkalmazásban Dynamics 365 Customer Insights.
ms.date: 02/24/2022
ms.reviewer: v-wendysmith
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: mukeshpo
ms.author: mukeshpo
manager: shellyha
ms.openlocfilehash: 7c758dccf7ea34dd7b8f80d05eff1ed12030526f
ms.sourcegitcommit: b7dbcd5627c2ebfbcfe65589991c159ba290d377
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/27/2022
ms.locfileid: "8642651"
---
# <a name="connect-an-azure-synapse-data-source-preview"></a>Azure Synapse adatforrás csatlakoztatása (előzetes verzió)

Azure Synapse Analytics egy vállalati elemzési szolgáltatás, amely felgyorsítja az adattárházak és a big data rendszerek betekintésének idejét. Azure Synapse Analytics egyesíti a vállalati adattárolásban használt legjobb SQL-technológiákat, a big data-okhoz használt Spark-technológiákat, a Data Explorert a napló- és idősorelemzéshez, a Folyamatokat az adatintegrációhoz és az ETL/ELT-hez, valamint Power BI a más Azure-szolgáltatásokkal, például a, Cosmos DB és az AzureML-lel való mély integrációt.

További információt az áttekintésben talál [Azure Synapse](/azure/synapse-analytics/overview-what-is).

## <a name="prerequisites"></a>Előfeltételek

A következő előfeltételeknek kell teljesülniük a következő rendszerhez Dynamics 365 Customer Insights való csatlakozás konfigurálásához Azure Synapse.

> [!IMPORTANT]
> A leírt módon állítsa be az összes **szerepkör-hozzárendelést**.  

## <a name="prerequisites-in-customer-insights"></a>Előfeltételek a Customer Insights szolgáltatásban

* Rendszergazdai **szerepkörrel** rendelkezik a Customer Insights alkalmazásban. További információ a felhasználói engedélyekről [a Customer Insightsban](permissions.md#assign-roles-and-permissions).

Az Azure-ban: 

- Aktív Azure-előfizetés.

- Ha új Azure Data Lake Storage Gen2-fiókot használ, a *Customer Insights* szolgáltatáselemzőjének tárolási blobadatokra közreműködő **engedélyekre van szüksége**. További információ a Customer Insights [szolgáltatásigazgatójához való csatlakozásról.Azure Data Lake Storage](connect-service-principal.md) A Data Lake Storage Gen2 szolgáltásnál **engedélyezni kell** a [hierarchikus névteret](/azure/storage/blobs/data-lake-storage-namespace).

- A munkaterület erőforráscsoportjában a Azure Synapse *szolgáltatásnévnek* és a *Customer Insights* felhasználójának legalább **olvasó** engedélyt kell rendelnie. További információk: [Azure-szerepkörök hozzárendelése az Azure Portal használatával](/azure/role-based-access-control/role-assignments-portal).

- A *felhasználónak* **Storage Blob Data-közreműködő** engedéllyel kell rendelkeznie ahhoz az Azure Data Lake Storage Gen2-fiókhoz, amelyben az adatok találhatók, és amely össze lett kapcsolva az Azure Synapse-munkaterülettel. További információ arról, [hogyan rendelhető hozzá az Azure Portal használatával a blobhoz és a feldolgozási sor adataihoz való hozzáférésre szolgáló Azure-szerepkör](/azure/storage/common/storage-auth-aad-rbac-portal) és részletek [a Storage Blob Data közreműködői engedélyéről](/azure/role-based-access-control/built-in-roles#storage-blob-data-contributor).

- Az *[Azure Synapse-munkaterület felügyelt identitásához](/azure/synapse-analytics/security/synapse-workspace-managed-identity)* a **Storage Blob Data közreműködői** engedélyével kell rendelkezni abban az Azure Data Lake Storage Gen2-fiókban, ahol az adatok találhatók, és amelyet összekapcsoltak az Azure Synapse-munkaterülettel. További információ arról, [hogyan rendelhető hozzá az Azure Portal használatával a blobhoz és a feldolgozási sor adataihoz való hozzáférésre szolgáló Azure-szerepkör](/azure/storage/common/storage-auth-aad-rbac-portal) és részletek [a Storage Blob Data közreműködői engedélyéről](/azure/role-based-access-control/built-in-roles#storage-blob-data-contributor).

- A munkaterületen a Azure Synapse *Customer Insights* szolgáltatáselemének Synapse Administrator **szerepkörre van** szüksége. További információ: [A hozzáférés-vezérlés beállítása a Synapse-munkaterülethez](/azure/synapse-analytics/security/how-to-set-up-access-control).

## <a name="connect-to-data-lake-databases-in-azure-synapse-analytics"></a>Csatlakozás adattava-adatbázisokhoz a következőben: Azure Synapse Analytics

1. Válassza az **Adatok** > **Adatforrások** lehetőséget.

1. Válassza az **Adatforrás hozzáadása** lehetőséget.

1. Válassza az **Azure Synapse Analytics (Előnézet)** metódust.

1. Adja meg a adatforrás **Nevét**, majd válassza a **Következő** lehetőséget a adatforrás létrehozásához. 

1. Válasszon egy [elérhető kapcsolatot](connections.md), Azure Synapse Analytics vagy hozzon létre egy újat.

1. Válasszon egy **Tóadatbázist** a kijelölt Azure Synapse Analytics kapcsolathoz csatlakoztatott munkaterületről, és válassza a Tovább **lehetőséget**.

1. Jelölje ki a csatlakoztatott adatbázisból lenyelni kívánt entitásokat. 

1. Válassza ki azokat az adattenzitásokat, amelyeken engedélyezni szeretné az adatprofilozást. 

1. Válassza a Mentés **lehetőséget** a kijelölés alkalmazásához, és indítsa el az újonnan létrehozott adatforrás származó adatok beolvasását a Tó adatbázistábláihoz csatolt újonnan létrehozott adatforrás a alkalmazásban Azure Synapse Analytics.
