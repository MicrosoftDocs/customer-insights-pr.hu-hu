---
title: Adatok Azure Synapse Analytics exportálása (előzetes verzió)
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot Azure Synapse Analytics.
ms.date: 06/29/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: stefanie-msft
ms.author: sthe
manager: shellyha
ms.openlocfilehash: 60bacb313e0426564310f3c1339bf3b732e17489
ms.sourcegitcommit: dca46afb9e23ba87a0ff59a1776c1d139e209a32
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/29/2022
ms.locfileid: "9082869"
---
# <a name="export-data-to-azure-synapse-analytics-preview"></a>Adatok Azure Synapse Analytics exportálása (előzetes verzió)

Az Azure Synapse olyan elemzőszolgáltatás, amellyel gyorsabban áttekinthetők az adattárhházakban és a nagy adatrendszerekben lévő adatok. A Customer Insights-adatok betölthetők az [Azure Synapse](/azure/synapse-analytics/overview-what-is) rendszerbe, és használhatók ott.

## <a name="prerequisites"></a>Előfeltételek

A Customer Insights és az Azure Synapse közötti kapcsolat konfigurálásához a következő előfeltételeknek kell teljesülnie.

> [!NOTE]
> A leírt módon állítsa be az összes **szerepkör-hozzárendelést**.  

## <a name="prerequisites-in-customer-insights"></a>Előfeltételek a Customer Insights szolgáltatásban

* Az Azure Active Directory (AD) felhasználói fiók rendszergazdai **szerepkörrel** rendelkezik a Customer Insights szolgáltatásban. További információ a felhasználói engedélyek [beállításáról](permissions.md#assign-roles-and-permissions).

Az Azure-ban: 

- Aktív Azure-előfizetés.

- Ha új Azure Data Lake Storage Gen2-fiókot használ, a *Customer Insights* szolgáltatásnévnek Storage Blob Data közreműködő **engedélyre van szüksége**. További információ a Gen2-fiókhoz való csatlakozásról [az Azure Data Lake Storage Azure-szolgáltatásnévvel a Customer Insights](connect-service-principal.md) számára. A Data Lake Storage Gen2 szolgáltásnál **engedélyezni kell** a [hierarchikus névteret](/azure/storage/blobs/data-lake-storage-namespace).

- Azon az erőforráscsoporton, ahol a Azure Synapse munkaterület található, a *szolgáltatásnévhez* és a *Azure AD Customer Insightsban* rendszergazdai engedélyekkel rendelkező felhasználóhoz legalább **olvasó** engedélyt kell rendelni. További információk: [Azure-szerepkörök hozzárendelése az Azure Portal használatával](/azure/role-based-access-control/role-assignments-portal).

- A *Azure AD Customer Insightsban* rendszergazdai engedélyekkel rendelkező felhasználónak Storage Blob Data közreműködő **engedélyre van szüksége** azon a Gen2-fiókon, Azure Data Lake Storage ahol az adatok találhatók és a Azure Synapse munkaterülethez vannak kapcsolva. További információ arról, [hogyan rendelhető hozzá az Azure Portal használatával a blobhoz és a feldolgozási sor adataihoz való hozzáférésre szolgáló Azure-szerepkör](/azure/storage/common/storage-auth-aad-rbac-portal) és részletek [a Storage Blob Data közreműködői engedélyéről](/azure/role-based-access-control/built-in-roles#storage-blob-data-contributor).

- Az *[Azure Synapse-munkaterület felügyelt identitásához](/azure/synapse-analytics/security/synapse-workspace-managed-identity)* a **Storage Blob Data közreműködői** engedélyével kell rendelkezni abban az Azure Data Lake Storage Gen2-fiókban, ahol az adatok találhatók, és amelyet összekapcsoltak az Azure Synapse-munkaterülettel. További információ arról, [hogyan rendelhető hozzá az Azure Portal használatával a blobhoz és a feldolgozási sor adataihoz való hozzáférésre szolgáló Azure-szerepkör](/azure/storage/common/storage-auth-aad-rbac-portal) és részletek [a Storage Blob Data közreműködői engedélyéről](/azure/role-based-access-control/built-in-roles#storage-blob-data-contributor).

- A munkaterületen a Azure Synapse *Customer Insights* szolgáltatásnévhez hozzá kell **rendelni a Synapse-rendszergazdai** szerepkört. További információ: [A hozzáférés-vezérlés beállítása a Synapse-munkaterülethez](/azure/synapse-analytics/security/how-to-set-up-access-control).

## <a name="set-up-the-connection-and-export-to-azure-synapse"></a>A kapcsolat beállítása és exportálás az Azure Synapse rendszerbe

### <a name="configure-a-connection"></a>Kapcsolat konfigurálása

Kapcsolat létrehozásához a Szolgáltatásnévnek és a Felhasználói fióknak a Customer Insightsban olvasó **engedélyekkel kell rendelkeznie** azon az erőforráscsoporton *,* ahol a Synapse Analytics munkaterület található. Emellett a szolgáltatásnévnek és a Synapse Analytics-munkaterületen lévő felhasználónak Synapse-rendszergazdai **engedélyekre van szüksége**. 

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a Kapcsolat **hozzáadása lehetőséget**, és válassza **Azure Synapse Analytics** vagy válassza a **Beállítás** lehetőséget a csempén a **Azure Synapse Analytics** kapcsolat konfigurálásához.

1. Adjon meg egy felismerhető nevet a Megjelenítendő név mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Válassza ki vagy keresse meg azt az előfizetést, amelyben használni szeretné a Customer Insights adatait. Az előfizetés kiválasztása után a **Munkaterület**, a **Tárfiók** és a **Tároló** lehetőség is kiválasztható.

1. A kapcsolat mentéséhez válassza a **Mentés** lehetőséget.

### <a name="configure-an-export"></a>Exportálás konfigurálása

Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz. Az exportálás megosztott kapcsolattal való konfigurálásához legalább **közreműködő** engedélyre van szüksége a Customer Insights szolgáltatásban. További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Új exportálás létrehozásához válassza az **Exportálás hozzáadása** lehetőséget.

1. **A Kapcsolat exportáláshoz** mezőben válasszon ki egy kapcsolatot a **Azure Synapse Analytics** szakaszból. Ha nem látja ezt a szakasznevet, az Ön számára nem áll rendelkezésre ilyen típusú [kapcsolat](connections.md).

1. Adjon meg egy felismerhető **megjelenítendő nevet** és egy **adatbázisnevet** az exportáláshoz. Az exportálás egy új [Azure Synapse lake-adatbázist](/azure/synapse-analytics/database-designer/concepts-lake-database) hoz létre a kapcsolatban meghatározott munkaterületen.

1. Válassza ki, hogy mely entitásokba szeretne exportálni Azure Synapse Analytics.
   > [!NOTE]
   > A [Common Data Model mappán](connect-common-data-model.md) alapuló adatforrások nem támogatottak.

1. Válassza a **Mentés** parancsot.

Az exportálás mentése nem futtatja azonnal az exportálást.

Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut. Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand).

A Synapse Analyticsbe exportált adatok lekérdezéséhez Storage blobadatokra van szüksége **, olvasó** hozzáférést biztosítson az exportálások munkaterületén található céltárolóhoz. 

### <a name="update-an-export"></a>Exportálás frissítése

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Válassza ki a **Szerkesztés** lehetőséget a frissíteni kívánt exportálásnál.

   - **Adjon** hozzá entitásokat a kijelöléshez, vagy **távolítson el** belőle szakaszokat. A kijelölésből eltávolított entitások nem törlődnek a Synapse Analytics-adatbázisból. A későbbi adatfrissítések azonban nem frissítik az adott adatbázisban lévő eltávolított entitásokat.

   - Az **Adatbázis nevének megváltoztatása** beállítással új Synapse Analytics-adatbázis hozható létre. A korábban beállított nevű adatbázis nem fog frissülni a későbbi frissítések során.
