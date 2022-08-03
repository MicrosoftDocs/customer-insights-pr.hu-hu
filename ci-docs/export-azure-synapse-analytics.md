---
title: Adatok Azure Synapse Analytics exportálása (előzetes verzió)
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot Azure Synapse Analytics.
ms.date: 07/25/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: stefanie-msft
ms.author: sthe
manager: shellyha
ms.openlocfilehash: f9c9ee55f2874ae1dcaf82f2ff17ed0fbbb7804d
ms.sourcegitcommit: 594081c82ca385f7143b3416378533aaf2d6d0d3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/27/2022
ms.locfileid: "9196397"
---
# <a name="export-data-to-azure-synapse-analytics-preview"></a>Adatok Azure Synapse Analytics exportálása (előzetes verzió)

Az Azure Synapse olyan elemzőszolgáltatás, amellyel gyorsabban áttekinthetők az adattárhházakban és a nagy adatrendszerekben lévő adatok. A Customer Insights-adatok betölthetők az [Azure Synapse](/azure/synapse-analytics/overview-what-is) rendszerbe, és használhatók ott.

## <a name="prerequisites"></a>Előfeltételek

> [!NOTE]
> A leírt módon állítsa be az összes **szerepkör-hozzárendelést**.

- A Customer Insightsban az Azure Active Directory (AD) felhasználói fióknak rendszergazdai szerepkörrel [kell rendelkeznie](permissions.md#assign-roles-and-permissions).

Az Azure-ban:

- Aktív Azure-előfizetés.

- Ha új Azure Data Lake Storage Gen2-fiókot használ, a [Customer Insights](connect-service-principal.md) szolgáltatásnév Storage Blob Data közreműködő **engedélyekkel rendelkezik**. A Data Lake Storage Gen2 szolgáltásnál **engedélyezni kell** a [hierarchikus névteret](/azure/storage/blobs/data-lake-storage-namespace).

- Azon az erőforráscsoporton, ahol a Azure Synapse munkaterület található, a *szolgáltatásnévhez* és a *Azure AD Customer Insightsban* rendszergazdai engedélyekkel rendelkező felhasználóhoz legalább **olvasó**[engedélyt](/azure/role-based-access-control/role-assignments-portal) kell rendelni.

- A *Azure AD Customer Insights* rendszergazdai engedélyekkel rendelkező felhasználó Storage Blob Data közreműködő **engedélyekkel rendelkezik** azon a Gen2-fiókon, Azure Data Lake Storage ahol az adatok találhatók és a Azure Synapse munkaterülethez vannak kapcsolva. További információ arról, [hogyan rendelhető hozzá az Azure Portal használatával a blobhoz és a feldolgozási sor adataihoz való hozzáférésre szolgáló Azure-szerepkör](/azure/storage/common/storage-auth-aad-rbac-portal) és részletek [a Storage Blob Data közreműködői engedélyéről](/azure/role-based-access-control/built-in-roles#storage-blob-data-contributor).

- A *[Azure Synapse munkaterület felügyelt identitása](/azure/synapse-analytics/security/synapse-workspace-managed-identity)* Storage Blob-adatokkal közreműködő **engedélyekkel rendelkezik** azon a Azure Data Lake Storage Gen2-fiókon, ahol az adatok találhatók, és a Azure Synapse munkaterülethez vannak csatolva. További információ arról, [hogyan rendelhető hozzá az Azure Portal használatával a blobhoz és a feldolgozási sor adataihoz való hozzáférésre szolgáló Azure-szerepkör](/azure/storage/common/storage-auth-aad-rbac-portal) és részletek [a Storage Blob Data közreműködői engedélyéről](/azure/role-based-access-control/built-in-roles#storage-blob-data-contributor).

- A munkaterületen a Azure Synapse Customer Insights *szolgáltatásnév synapse-rendszergazdai* **szerepkörrel rendelkezik** hozzárendelve [.](/azure/synapse-analytics/security/how-to-set-up-access-control)

## <a name="set-up-connection-to-azure-synapse"></a>Kapcsolat beállítása Azure Synapse

[!INCLUDE [export-connection-include](includes/export-connection-admn.md)]

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a Kapcsolat **hozzáadása lehetőséget**, majd válassza a **Azure Synapse Analytics** lehetőséget.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Alapértelmezés szerint csak a rendszergazdák. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Válassza ki vagy keresse meg azt az előfizetést, amelyben használni szeretné a Customer Insights adatait. Az előfizetés kiválasztása után a **Munkaterület**, a **Tárfiók** és a **Tároló** lehetőség is kiválasztható.

1. Tekintse át az adatvédelmet és a megfelelőséget, és válassza az [Elfogadom lehetőséget](connections.md#data-privacy-and-compliance)**.**

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

## <a name="configure-an-export"></a>Exportálás konfigurálása

[!INCLUDE [export-permission-include](includes/export-permission.md)] Az exportálás megosztott kapcsolattal való konfigurálásához legalább **közreműködő** engedélyre van szüksége a Customer Insights szolgáltatásban.

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Válassza az Exportálás **hozzáadása lehetőséget**.

1. **A Kapcsolat exportáláshoz** mezőben válasszon ki egy kapcsolatot a Azure Synapse Analytics szakaszból. Ha nem érhető el egy kapcsolat sem, akkor forduljon a rendszergazdához.

1. Adjon meg egy felismerhető **megjelenítendő nevet** és egy **adatbázisnevet** az exportáláshoz. Az exportálás létrehoz egy új [Azure Synapse lake-adatbázist](/azure/synapse-analytics/database-designer/concepts-lake-database) a kapcsolatban meghatározott munkaterületen.

1. Válassza ki, hogy mely entitásokba szeretne exportálni Azure Synapse Analytics.
   > [!NOTE]
   > A [Common Data Model mappán](connect-common-data-model.md) alapuló adatforrások nem támogatottak.

1. Válassza a **Mentés** parancsot.

[!INCLUDE [export-saving-include](includes/export-saving.md)]

A Synapse Analyticsbe exportált adatok lekérdezéséhez Storage blobadatokra van szüksége **, olvasó** hozzáférést biztosítson az exportálások munkaterületén található céltárolóhoz.

## <a name="update-an-export"></a>Exportálás frissítése

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Válassza ki a **Szerkesztés** lehetőséget a frissíteni kívánt exportálásnál.

   - **Adjon** hozzá entitásokat a kijelöléshez, vagy **távolítson el** belőle szakaszokat. A kijelölésből eltávolított entitások nem törlődnek a Synapse Analytics-adatbázisból. A későbbi adatfrissítések azonban nem frissítik az adott adatbázisban lévő eltávolított entitásokat.

   - Az **Adatbázis nevének megváltoztatása** beállítással új Synapse Analytics-adatbázis hozható létre. A korábban beállított nevű adatbázis nem fog frissülni a későbbi frissítések során.

[!INCLUDE [footer-include](includes/footer-banner.md)]
