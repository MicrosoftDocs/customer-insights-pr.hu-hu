---
title: Adatok beolvasása a Azure Synapse Analytics
description: Adatbázis használata a adatforrás Azure Synapse a Dynamics 365 Customer Insights.
ms.date: 02/24/2022
ms.reviewer: v-wendysmith
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: mukeshpo
ms.author: mukeshpo
manager: shellyha
ms.openlocfilehash: 163bef897880f0497bf00e90fd095621a2d14378
ms.sourcegitcommit: 73cb021760516729e696c9a90731304d92e0e1ef
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/25/2022
ms.locfileid: "8356046"
---
# <a name="connect-an-azure-synapse-data-source-preview"></a>Azure Synapse adatforrás csatlakoztatása (előnézet)

Azure Synapse Analytics egy vállalati elemzési szolgáltatás, amely felgyorsítja az adattárházak és a big data rendszerek közötti betekintés idejét. Azure Synapse Analytics egyesíti a vállalati adattároláshoz használt legjobb SQL-technológiákat, a big data-hoz használt Spark-technológiákat, a Data Explorert a napló- és idősorelemzéshez, az adatintegrációs folyamatokat és az ETL/ELT-t, valamint a más Azure-szolgáltatásokkal, például Power BI a, Cosmos DB és az AzureML-rel való mély integrációt.

További információt az áttekintés [Azure Synapse című témakörben talál](/azure/synapse-analytics/overview-what-is).

## <a name="prerequisites"></a>Előfeltételek

A Customer Insights és az Azure Synapse közötti kapcsolat konfigurálásához a következő előfeltételeknek kell teljesülnie.

> [!IMPORTANT]
> A leírt módon állítsa be az összes **szerepkör-hozzárendelést**.  

## <a name="prerequisites-in-customer-insights"></a>Előfeltételek a Customer Insights szolgáltatásban

* Rendszergazdai **szerepkörrel** rendelkezik a Customer Insightsban. További információk a [célközönséggel kapcsolatos információk felhasználói jogosultságairól](permissions.md#assign-roles-and-permissions).

Az Azure-ban: 

- Aktív Azure-előfizetés.

- Ha új Azure Data Lake Storage Gen2-fiókot használ, a *szolgáltatás célközönség betekintési információihoz használatos rendszerbiztonsági tagjának* **Storage Blob adat-közreműködői** engedélyekkel kell rendelkeznie. További információ a szolgáltatásnévvel való csatlakozásról [Azure Data Lake Storage a célközönség elemzésekhez](connect-service-principal.md). A Data Lake Storage Gen2 szolgáltásnál **engedélyezni kell** a [hierarchikus névteret](/azure/storage/blobs/data-lake-storage-namespace).

- Az Azure Synapse-munkaterületet tartalmazó erőforráscsoportnál a *szolgáltatás rendszerbiztonsági tagjához* és a *célközönség betekintési információinak felhasználójához* legalább **Olvasó** engedélyt kell hozzárendelni. További információk: [Azure-szerepkörök hozzárendelése az Azure Portal használatával](/azure/role-based-access-control/role-assignments-portal).

- A *felhasználónak* **Storage Blob Data-közreműködő** engedéllyel kell rendelkeznie ahhoz az Azure Data Lake Storage Gen2-fiókhoz, amelyben az adatok találhatók, és amely össze lett kapcsolva az Azure Synapse-munkaterülettel. További információ arról, [hogyan rendelhető hozzá az Azure Portal használatával a blobhoz és a feldolgozási sor adataihoz való hozzáférésre szolgáló Azure-szerepkör](/azure/storage/common/storage-auth-aad-rbac-portal) és részletek [a Storage Blob Data közreműködői engedélyéről](/azure/role-based-access-control/built-in-roles#storage-blob-data-contributor).

- Az *[Azure Synapse-munkaterület felügyelt identitásához](/azure/synapse-analytics/security/synapse-workspace-managed-identity)* a **Storage Blob Data közreműködői** engedélyével kell rendelkezni abban az Azure Data Lake Storage Gen2-fiókban, ahol az adatok találhatók, és amelyet összekapcsoltak az Azure Synapse-munkaterülettel. További információ arról, [hogyan rendelhető hozzá az Azure Portal használatával a blobhoz és a feldolgozási sor adataihoz való hozzáférésre szolgáló Azure-szerepkör](/azure/storage/common/storage-auth-aad-rbac-portal) és részletek [a Storage Blob Data közreműködői engedélyéről](/azure/role-based-access-control/built-in-roles#storage-blob-data-contributor).

- Az Azure Synapse-munkaterületen a *célközönség betekintési információihoz használatos rendszerbiztonsági tagnak* **Rendszergazda** szerepkörrel kell rendelkeznie. További információ: [A hozzáférés-vezérlés beállítása a Synapse-munkaterülethez](/azure/synapse-analytics/security/how-to-set-up-access-control).

## <a name="connect-to-data-lake-databases-in-azure-synapse-analytics"></a>Csatlakozás az adattó adatbázisaihoz Azure Synapse Analytics

1. Válassza az **Adatok** > **Adatforrások** lehetőséget.

1. Válassza az **Adatforrás hozzáadása** lehetőséget.

1. Válassza ki az **Azure Synapse Analytics (Előnézet)** módszert.

1. Adja meg a adatforrás **Nevét**, majd válassza a **Következő** lehetőséget a adatforrás létrehozásához. 

1. Válasszon egy [elérhető kapcsolatot](connections.md), Azure Synapse Analytics vagy hozzon létre egy újat.

1. Válasszon egy Tó adatbázist **a** kijelölt Azure Synapse Analytics kapcsolathoz csatlakoztatott munkaterületről, és válassza a Tovább **lehetőséget**.

1. Válassza ki a csatlakoztatott adatbázisból bevetendő entitásokat. 

1. Válassza ki azokat az adategyetemeket, amelyeken engedélyezni szeretné az adatprofilozást. 

1. Válassza a Mentés **lehetőséget** a kijelölés alkalmazásához, és indítsa el az adatok beolvasását a Tó adatbázistábláihoz csatolt, újonnan létrehozott adatforrás.Azure Synapse Analytics
