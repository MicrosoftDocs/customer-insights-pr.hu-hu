---
title: Csatlakozás táblákhoz a Microsoft Dataverse-ben
description: Adatok importálása Microsoft Dataverse felügyelt adattóből.
ms.date: 03/18/2022
ms.subservice: audience-insights
ms.topic: how-to
author: adkuppa
ms.author: adkuppa
manager: shellyha
ms.reviewer: mhart
searchScope:
- ci-dataverse
- customerInsights
ms.openlocfilehash: 7140e9254108bc6f0d518b3ccf4b10fc33cde115
ms.sourcegitcommit: b515120bebd2638f2639004422cee3cff42fbdf7
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/24/2022
ms.locfileid: "8800176"
---
# <a name="connect-to-data-in-a-microsoft-dataverse-managed-data-lake"></a>Kapcsolódás az adatokhoz egy Microsoft Dataverse felügyelt adattóban

Ez a cikk arról nyújt tájékoztatást, hogy a felhasználók hogyan Dataverse csatlakozhatnak gyorsan a Microsoft Dataverse felügyelt tó analitikus entitásaihoz. 

> [!NOTE]
> A felügyelt tóban elérhető entitások listájának megtekintéséhez a Dataverse szervezet rendszergazdájának kell lennie.

## <a name="important-considerations"></a>Fontos tényezők

1. Az online szolgáltatásokban, például az Azure Data Lake Storage esetében tárolt adatok az adatok feldolgozásának vagy tárolásának helyétől eltérő helyen tárolhatók, vagy a Dynamics 365 Customer Insights megoldásban is tárolhatók.Az online szolgáltatásokban tárolt adatok importálásával vagy az azokhoz való csatlakozással Ön elfogadja, hogy az adatok továbbíthatók és tárolhatók a rendszerben Dynamics 365 Customer Insights. [További információ a Microsoft Adatvédelmi központban](https://www.microsoft.com/trust-center).
2. Csak Dataverse azok az entitások láthatók, amelyeken [engedélyezve van a változáskövetés](/power-platform/admin/enable-change-tracking-control-data-synchronization). Ezek az entitások exportálhatók a Dataverse-managed data lake-be, és felhasználhatók a Customer Insights alkalmazásban. A beépített Dataverse táblákon alapértelmezés szerint engedélyezve van a változáskövetés. Egyéni táblák esetén be kell kapcsolnia a változáskövetést. Annak ellenőrzéséhez, hogy egy Dataverse tábla engedélyezve van-e a változások nyomon követésére, nyissa meg az [Power Apps](https://make.powerapps.com) > **Adattáblák** > **lehetőséget**. Keresse meg az érdeklődésre számot tartó táblázatot, és válassza ki. Nyissa meg a **Beállítások** > **speciális beállításait,** és tekintse át a **Változások** nyomon követése beállítást.

## <a name="connect-to-a-dataverse-managed-lake"></a>Csatlakozás egy Dataverse felügyelt tóhoz

1. A Customer Insights szolgáltatásban lépjen az **Adat** > **Adatforrások** részre.

2. Válassza az **Adatforrás hozzáadása** lehetőséget.

3. Válassza a Tovább lehetőséget **Microsoft Dataverse**, és válassza a Tovább **lehetőséget**.

4. Adjon meg egy **Nevet** az adatforrás számára, majd válassza a **Tovább** elemet. 

5. Adja meg a **Kiszolgálói címét**, a Dataverse-szervezethez majd válassza a **Bejelentkezés** lehetőséget.

   :::image type="content" source="media/ingest-dataverse-server-address.png" alt-text="Az adatok beíratási lépésének képernyője, ahol a felhasználó megadhatja a Dataverse-környezet URL-címét.":::

6. Az elérhető listából válassza ki azokat a táblákat, amelyeket entitásként szeretne beolvasni a Customer Insights szolgáltatásba.    

   > [!NOTE]
   > Ha már vannak kijelölve táblák, akkor más Dynamics 365-alkalmazások (pl. a Dynamics 365 Sales Insights vagy a Customer Service Insights) is használni tudják ezeket. Ez a kijelölés nem módosítható. Ezek a táblák entitásként lesznek elérhetők az adatforrás létrehozása után.

   :::image type="content" source="media/select-dataverse-entities.png" alt-text="Egy párbeszédpanel, amely a Dataverse-környezetben található entitások listáját mutatja.":::

7. Mentse a beállítást, és indítsa el a kijelölt táblák szinkronizálását a Dataverse-ből. Az újonnan felvett kapcsolatot az **Adatforrások** lapon találja. Frissítési várólistára kerül, és az entitások számát 0-ként mutatja, amíg meg nem szinkronizálja az összes kijelölt táblát.

Csak egy környezethez tartozó adatforrás használhatja a egyszerre ugyanazt a Dataverse felügyelt tavat.

## <a name="edit-a-dataverse-managed-lake-data-source"></a>Egy Dataverse felügyelt tó adatforrásának szerkesztése

Az entitások kijelölését csak az adatforrás létrehozása után módosíthatja. Ha például további entitásokat adtak hozzá a Dataverse szolgáltatáshoz, és azokat is importálni kívánja.    
Ha másik Dataverse-adattóhoz szeretne kapcsolódni, [hozzon létre egy új adatforrást](#connect-to-a-dataverse-managed-lake).

1. Válassza az **Adatok** > **Adatforrások** lehetőséget.

2. A frissíteni kívánt adatforrás mellett válassza ki a függőleges ellipszis (&vellip;) elemet.

3. Válassza a lista **Szerkesztés** elemét.

4. Jelöljön ki további entitásokat a rendelkezésre álló entitások listájából, és válassza a **Mentés** lehetőséget.

[!INCLUDE [footer-include](includes/footer-banner.md)]
