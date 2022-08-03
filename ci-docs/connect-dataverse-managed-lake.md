---
title: Kapcsolódás az adatokhoz egy Microsoft Dataverse felügyelt adattóban
description: Adatok importálása Microsoft Dataverse felügyelt adattóből.
ms.date: 07/26/2022
ms.subservice: audience-insights
ms.topic: how-to
author: adkuppa
ms.author: adkuppa
manager: shellyha
ms.reviewer: v-wendysmith
searchScope:
- ci-dataverse
- customerInsights
ms.openlocfilehash: b21150a1c51bdad35250cae7fde7f38a014ec876
ms.sourcegitcommit: 5807b7d8c822925b727b099713a74ce2cb7897ba
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/28/2022
ms.locfileid: "9206956"
---
# <a name="connect-to-data-in-a-microsoft-dataverse-managed-data-lake"></a>Kapcsolódás az adatokhoz egy Microsoft Dataverse felügyelt adattóban

Microsoft Dataverse a felhasználók gyorsan csatlakozhatnak a felügyelt tó elemzési entitásaihoz Microsoft Dataverse. Csak egy környezethez tartozó adatforrás használhatja a egyszerre ugyanazt a Dataverse felügyelt tavat.

> [!NOTE]
> A felügyelt tóban elérhető entitások listájának megtekintéséhez és a Dataverse szervezet rendszergazdájának kell lennie.

## <a name="prerequisites"></a>Előfeltételek

- Az online szolgáltatásokban, például az Azure Data Lake Storage esetében tárolt adatok az adatok feldolgozásának vagy tárolásának helyétől eltérő helyen tárolhatók, vagy a Dynamics 365 Customer Insights megoldásban is tárolhatók.Az online szolgáltatásokban tárolt adatok importálásával vagy az azokhoz való csatlakozással Ön elfogadja, hogy az adatok átvihetők és tárolhatók a következőkkel: Dynamics 365 Customer Insights. [További információt a Microsoft Adatvédelmi központban talál](https://www.microsoft.com/trust-center).

- Csak Dataverse olyan entitások láthatók, amelyeken [engedélyezve van a változáskövetés](/power-platform/admin/enable-change-tracking-control-data-synchronization). Ezek az entitások exportálhatók a Dataverse-managed data lake-be, és felhasználhatók a Customer Insightsban. A beépített Dataverse táblákon alapértelmezés szerint engedélyezve van a változáskövetés. Be kell kapcsolnia a változáskövetést az egyéni táblázatokhoz. Ha ellenőrizni szeretné, hogy egy Dataverse tábla engedélyezve van-e a változáskövetéshez, lépjen az Adattáblák [Power Apps](https://make.powerapps.com) > **oldalra** > **·**. Keresse meg az Ön számára érdekes táblázatot, és válassza ki. Lépjen a Beállítások **speciális beállításaihoz** > **,** és tekintse át a **Változások** követése beállítást.

## <a name="connect-to-a-dataverse-managed-lake"></a>Csatlakozás egy Dataverse felügyelt tóhoz

1. Válassza az **Adatok** > **Adatforrások** lehetőséget.

1. Válassza az **Adatforrás hozzáadása** lehetőséget.

1. Válassza a(z) **Microsoft Dataverse** beállítást.

1. **Adja meg a adatforrás nevét** és egy opcionális **leírást**.

1. Adja meg a **Kiszolgálói címét**, a Dataverse-szervezethez majd válassza a **Bejelentkezés** lehetőséget.

1. Válassza ki azokat a táblákat, amelyeket entitásként szeretne betölteni a Customer Insights szolgáltatásba az elérhető listából.

   > [!NOTE]
   > Ha már vannak kijelölve táblák, akkor más Dynamics 365-alkalmazások (pl. a Dynamics 365 Sales Insights vagy a Customer Service Insights) is használni tudják ezeket. Ez a kijelölés nem módosítható. Ezek a táblák entitásként lesznek elérhetők az adatforrás létrehozása után.

    :::image type="content" source="media/select-dataverse-entities.png" alt-text="Egy párbeszédpanel, amely a Dataverse-környezetben található entitások listáját mutatja.":::

1. Mentse a beállítást, és indítsa el a kijelölt táblák szinkronizálását a Dataverse-ből. Az újonnan felvett kapcsolatot az **Adatforrások** lapon találja. Frissítési várólistára kerül, és az entitások számát 0-ként mutatja, amíg meg nem szinkronizálja az összes kijelölt táblát.

   [!INCLUDE [progress-details-include](includes/progress-details-pane.md)]

Az adatok betöltése időbe telhet. A sikeres frissítés után a betöltött adatok az [**Entitások oldalon ellenőrizhetők**](entities.md).

## <a name="edit-a-dataverse-managed-lake-data-source"></a>Egy Dataverse felügyelt tó adatforrásának szerkesztése

Az entitások kijelölését csak az adatforrás létrehozása után módosíthatja. Ha például további entitásokat adtak hozzá a Dataverse szolgáltatáshoz, és azokat is importálni kívánja.
Ha másik Dataverse-adattóhoz szeretne kapcsolódni, [hozzon létre egy új adatforrást](#connect-to-a-dataverse-managed-lake).

1. Válassza az **Adatok** > **Adatforrások** lehetőséget.

1. A frissíteni kívánt adatforrás mellett válassza a Szerkesztés **lehetőséget**.

1. Válasszon ki további entitásokat az elérhető entitások listájából.

1. Kattintson a Mentés **gombra** a módosítások alkalmazásához és az **Adatforrások** lapra való visszatéréshez.

   [!INCLUDE [progress-details-include](includes/progress-details-pane.md)]

[!INCLUDE [footer-include](includes/footer-banner.md)]
