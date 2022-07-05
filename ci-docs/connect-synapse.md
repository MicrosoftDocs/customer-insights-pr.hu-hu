---
title: Azure Synapse adatforrás csatlakoztatása (előzetes verzió)
description: Azure Synapse Adatbázis használata adatforrás a Dynamics 365 Customer Insights.
ms.date: 03/25/2022
ms.reviewer: v-wendysmith
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: mukeshpo
ms.author: mukeshpo
manager: shellyha
ms.openlocfilehash: c4ae65613a02df38a30f907dae72d413bf1a702f
ms.sourcegitcommit: a97d31a647a5d259140a1baaeef8c6ea10b8cbde
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/29/2022
ms.locfileid: "9052702"
---
# <a name="connect-an-azure-synapse-analytics-data-source-preview"></a>Azure Synapse Analytics adatforrás csatlakoztatása (előzetes verzió)

Azure Synapse Analytics egy vállalati elemzési szolgáltatás, amely felgyorsítja az adattárházak és big data-rendszerek közötti betekintéshez szükséges időt. Azure Synapse Analytics egyesíti a vállalati adattárházban használt SQL-technológiák, a big datahoz használt Spark-technológiák, a napló- és idősorozat-elemzésekhez használt Adatkezelő, az adatintegrációs és ETL-/ELT-folyamatok, valamint a más Azure-szolgáltatásokkal, például Power BI az Cosmos DB AzureML-lel való mély integrációban használt SQL-technológiákat.

További információt az áttekintésben [Azure Synapse talál](/azure/synapse-analytics/overview-what-is).

## <a name="prerequisites"></a>Előfeltételek

> [!IMPORTANT]
> A leírt módon állítsa be az összes **szerepkör-hozzárendelést**.  

**A Customer Insights szolgáltatásban**:

* Rendszergazdai **szerepkörrel** rendelkezik a Customer Insights szolgáltatásban. További információ a felhasználói engedélyekről [a Customer Insights szolgáltatásban](permissions.md#assign-roles-and-permissions).

**Az Azure-ban**:

- Aktív Azure-előfizetés.

- Ha új Azure Data Lake Storage Gen2-fiókot használ, a *Customer Insights* szolgáltatásnévnek Storage Blob Data közreműködő **engedélyre van szüksége**. További információ a Customer Insights [szolgáltatásnévvel való csatlakozásáról.Azure Data Lake Storage](connect-service-principal.md) A Data Lake Storage Gen2 szolgáltásnál **engedélyezni kell** a [hierarchikus névteret](/azure/storage/blobs/data-lake-storage-namespace).

- Az erőforráscsoporton a Azure Synapse munkaterület található, a *Customer Insights* szolgáltatásnévhez *és* felhasználójához legalább **olvasó** engedélyeket kell rendelni. További információk: [Azure-szerepkörök hozzárendelése az Azure Portal használatával](/azure/role-based-access-control/role-assignments-portal).

- A *felhasználónak* **Storage Blob Data-közreműködő** engedéllyel kell rendelkeznie ahhoz az Azure Data Lake Storage Gen2-fiókhoz, amelyben az adatok találhatók, és amely össze lett kapcsolva az Azure Synapse-munkaterülettel. További információ arról, [hogyan rendelhető hozzá az Azure Portal használatával a blobhoz és a feldolgozási sor adataihoz való hozzáférésre szolgáló Azure-szerepkör](/azure/storage/common/storage-auth-aad-rbac-portal) és részletek [a Storage Blob Data közreműködői engedélyéről](/azure/role-based-access-control/built-in-roles#storage-blob-data-contributor).

- Az *[Azure Synapse-munkaterület felügyelt identitásához](/azure/synapse-analytics/security/synapse-workspace-managed-identity)* a **Storage Blob Data közreműködői** engedélyével kell rendelkezni abban az Azure Data Lake Storage Gen2-fiókban, ahol az adatok találhatók, és amelyet összekapcsoltak az Azure Synapse-munkaterülettel. További információ arról, [hogyan rendelhető hozzá az Azure Portal használatával a blobhoz és a feldolgozási sor adataihoz való hozzáférésre szolgáló Azure-szerepkör](/azure/storage/common/storage-auth-aad-rbac-portal) és részletek [a Storage Blob Data közreműködői engedélyéről](/azure/role-based-access-control/built-in-roles#storage-blob-data-contributor).

- A munkaterületen a Azure Synapse *Customer Insights* szolgáltatásnévhez hozzá kell **rendelni a Synapse-rendszergazdai** szerepkört. További információ: [A hozzáférés-vezérlés beállítása a Synapse-munkaterülethez](/azure/synapse-analytics/security/how-to-set-up-access-control).

## <a name="connect-to-the-data-lake-database-in-azure-synapse-analytics"></a>Csatlakozás a Data Lake-adatbázishoz Azure Synapse Analytics

1. Válassza az **Adatok** > **Adatforrások** lehetőséget.

1. Válassza az **Adatforrás hozzáadása** lehetőséget.

1. Válassza az **Azure Synapse Analytics (előnézeti)** metódust.

   :::image type="content" source="media/data_sources_synapse.png" alt-text="Párbeszédpanel a Synapse Analytics-adatokhoz való csatlakozáshoz":::
  
1. **Adja meg a adatforrás nevét** és egy opcionális **leírást**.

1. Válasszon ki egy [elérhető kapcsolatot](connections.md), Azure Synapse Analytics vagy hozzon létre egy újat.

1. Válasszon ki egy **adatbázist a kiválasztott** kapcsolatban csatlakoztatott munkaterületről, majd válassza a Tovább Azure Synapse Analytics gombot **·**. Jelenleg csak a Lake adatbázistípust *támogatjuk*.

1. Válassza ki a csatlakoztatott adatbázisból betölteni kívánt entitásokat, majd kattintson a Tovább **gombra**.

1. Igény szerint válassza ki azokat az adatentitásokat, amelyeken engedélyezni szeretné az adatprofil-készítést.

1. Válassza a Mentés **lehetőséget** a kijelölés alkalmazásához, és az újonnan létrehozott adatforrás származó adatok betöltésének megkezdéséhez, amely a Lake-adatbázistáblákhoz Azure Synapse Analytics van csatolva. **Megnyílik az Adatforrások** lap, amelyen az új adatforrás a Frissítés **állapot.**
