---
title: Customer Insights-adatok exportálása az Azure Synapse Analytics rendszerbe
description: Ismerje meg, hogyan konfigurálhatja az Azure Synapse Analytics rendszerrel kiépített kapcsolatot.
ms.date: 04/12/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: stefanie-msft
ms.author: sthe
manager: shellyha
ms.openlocfilehash: 822082d661863e737ea3d3a749a6c878db766967
ms.sourcegitcommit: e8e03309ba2515374a70c132d0758f3e1e1851d0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/04/2021
ms.locfileid: "5977380"
---
# <a name="export-data-to-azure-synapse-analytics-preview"></a>Aadtok exportálása az Azure Synapse Analytics rendszerbe (előzetes verzió)

Az Azure Synapse olyan elemzőszolgáltatás, amellyel gyorsabban áttekinthetők az adattárhházakban és a nagy adatrendszerekben lévő adatok. A Customer Insights-adatok betölthetők az [Azure Synapse](/azure/synapse-analytics/overview-what-is) rendszerbe, és használhatók ott.

## <a name="prerequisites"></a>Előfeltételek

A Customer Insights és az Azure Synapse közötti kapcsolat konfigurálásához a következő előfeltételeknek kell teljesülnie.

> [!NOTE]
> A leírt módon állítsa be az összes **szerepkör-hozzárendelést**.  

## <a name="prerequisites-in-customer-insights"></a>Előfeltételek a Customer Insights szolgáltatásban

* **Rendszergazda** szerepkörrel kell rendelkezni a célközönség betekintési információihoz. További információ [a célközönség betekintési információira vonatkozó felhasználói engedélyek beállításáról](permissions.md#assign-roles-and-permissions)

Az Azure-ban: 

- Aktív Azure-előfizetés.

- Ha új Azure Data Lake Storage Gen2-fiókot használ, a *szolgáltatás célközönség betekintési információihoz használatos rendszerbiztonsági tagjának* **Storage Blob adat-közreműködői** engedélyekkel kell rendelkeznie. További információ az [Azure Data Lake Storage Gen2-fiók és az  account with Azure szolgáltatás célközönség betekintési információihoz használatos rendszerbiztonsági tagjának összekapcsolásáról](connect-service-principal.md). A Data Lake Storage Gen2 szolgáltásnál **engedélyezni kell** a [hierarchikus névteret](/azure/storage/blobs/data-lake-storage-namespace).

- Az Azure Synapse-munkaterületet tartalmazó erőforráscsoportnál a *szolgáltatás rendszerbiztonsági tagjához* és a *célközönség betekintési információinak felhasználójához* legalább **Olvasó** engedélyt kell hozzárendelni. További információk: [Azure-szerepkörök hozzárendelése az Azure Portal használatával](/azure/role-based-access-control/role-assignments-portal).

- A *felhasználónak* **Storage Blob Data-közreműködő** engedéllyel kell rendelkeznie ahhoz az Azure Data Lake Storage Gen2-fiókhoz, amelyben az adatok találhatók, és amely össze lett kapcsolva az Azure Synapse-munkaterülettel. További információ arról, [hogyan rendelhető hozzá az Azure Portal használatával a blobhoz és a feldolgozási sor adataihoz való hozzáférésre szolgáló Azure-szerepkör](/azure/storage/common/storage-auth-aad-rbac-portal) és részletek [a Storage Blob Data közreműködői engedélyéről](/azure/role-based-access-control/built-in-roles#storage-blob-data-contributor).

- Az *[Azure Synapse-munkaterület felügyelt identitásához](/azure/synapse-analytics/security/synapse-workspace-managed-identity)* a **Storage Blob Data közreműködői** engedélyével kell rendelkezni abban az Azure Data Lake Storage Gen2-fiókban, ahol az adatok találhatók, és amelyet összekapcsoltak az Azure Synapse-munkaterülettel. További információ arról, [hogyan rendelhető hozzá az Azure Portal használatával a blobhoz és a feldolgozási sor adataihoz való hozzáférésre szolgáló Azure-szerepkör](/azure/storage/common/storage-auth-aad-rbac-portal) és részletek [a Storage Blob Data közreműködői engedélyéről](/azure/role-based-access-control/built-in-roles#storage-blob-data-contributor).

- Az Azure Synapse-munkaterületen a *célközönség betekintési információihoz használatos rendszerbiztonsági tagnak* **Rendszergazda** szerepkörrel kell rendelkeznie. További információ: [A hozzáférés-vezérlés beállítása a Synapse-munkaterülethez](/azure/synapse-analytics/security/how-to-set-up-access-control).

## <a name="set-up-the-connection-and-export-to-azure-synapse"></a>A kapcsolat beállítása és exportálás az Azure Synapse rendszerbe

### <a name="configure-a-connection"></a>Kapcsolat konfigurálása

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. A kapcsolat konfigurálásához válassza a **Kapcsolat hozzáadása**, majd az **Azure Synapse Analytics** lehetőséget, vagy válassza a **Beállítás** lehetőséget az **Azure Synapse Analytics** csempén.

1. Adjon meg egy felismerhető nevet a Megjelenítendő név mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Válassza ki vagy keresse meg azt az előfizetést, amelyben használni szeretné a Customer Insights adatait. Az előfizetés kiválasztása után a **Munkaterület**, a **Tárfiók** és a **Tároló** lehetőség is kiválasztható.

1. A kapcsolat mentéséhez válassza a **Mentés** lehetőséget.

### <a name="configure-an-export"></a>Exportálás konfigurálása

Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz. További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Új exportálás létrehozásához válassza az **Exportálás hozzáadása** lehetőséget.

1. A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot az **Azure Synapse Analytics** szakaszból. Ha nem látja ezt a szakasznevet, az Ön számára nem áll rendelkezésre ilyen típusú [kapcsolat](connections.md).

1. Adjon meg egy felismerhető **megjelenítendő nevet** és egy **adatbázisnevet** az exportáláshoz.

1. Válassza ki, hogy melyik entitásokat szeretné exportálni az Azure Synapse Analytics alkalmazásba.

1. Válassza a **Mentés** parancsot.

Az exportálás mentése nem futtatja azonnal az exportálást.

Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut. Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand).

### <a name="update-an-export"></a>Exportálás frissítése

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Válassza ki a **Szerkesztés** lehetőséget a frissíteni kívánt exportálásnál.

   - **Adjon** hozzá entitásokat a kijelöléshez, vagy **távolítson el** belőle szakaszokat. A kijelölésből eltávolított entitások nem törlődnek a Synapse Analytics-adatbázisból. A későbbi adatfrissítések azonban nem frissítik az adott adatbázisban lévő eltávolított entitásokat.

   - Az **Adatbázis nevének megváltoztatása** beállítással új Synapse Analytics-adatbázis hozható létre. A korábban beállított nevű adatbázis nem fog frissülni a későbbi frissítések során.
