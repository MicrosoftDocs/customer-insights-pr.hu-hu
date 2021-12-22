---
title: Csatlakozás táblákhoz a Microsoft Dataverse-ben
description: Adatok importálása Microsoft Dataverse felügyelt adattóből.
ms.date: 12/06/2021
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: adkuppa
ms.author: adkuppa
manager: shellyha
ms.reviewer: mhart
ms.openlocfilehash: fecf3e33b5bc1eec17006fc196004be902c03b40
ms.sourcegitcommit: 11b343f6622665251ab84ae39ebcd91fa1c928ca
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/08/2021
ms.locfileid: "7900154"
---
# <a name="connect-to-data-in-a-microsoft-dataverse-managed-data-lake"></a>Kapcsolódás az adatokhoz egy Microsoft Dataverse felügyelt adattóban

[!INCLUDE [cc-data-platform-banner](../includes/cc-data-platform-banner.md)]

Ez a cikk arról nyújt tájékoztatást, hogy a felhasználók hogyan Dataverse csatlakozhatnak gyorsan a felügyelt tó analitikai entitásaihoz. Microsoft Dataverse 

> [!NOTE]
> A Dataverse felügyelt tóban elérhető entitások listájának folytatásához és megtekintéséhez rendszergazdának kell lennie a szervezetben.

## <a name="important-considerations"></a>Fontos tényezők

Az online szolgáltatásokban, például az Azure Data Lake Storage esetében tárolt adatok az adatok feldolgozásának vagy tárolásának helyétől eltérő helyen tárolhatók, vagy a Dynamics 365 Customer Insights megoldásban is tárolhatók.Az online szolgáltatásokban tárolt adatok importálásával vagy az ahhoz való csatlakozással Ön elfogadja, hogy az adatok továbbíthatók és tárolhatók a Dynamics 365 Customer Insights .  [További információ a Microsoft Trust Centerben](https://www.microsoft.com/trust-center).

## <a name="connect-to-a-dataverse-managed-lake"></a>Csatlakozás egy Dataverse felügyelt tóhoz

1. A célközönség információin belül nyissa meg a következőt **Adatok** > **Adatforrások**.

2. Válassza az **Adatforrás hozzáadása** lehetőséget.

3. Válassza ki **Microsoft Dataverse** és válassza a Tovább **lehetőséget**.

4. Adjon meg egy **Nevet** az adatforrás számára, majd válassza a **Tovább** elemet. 

5. Adja meg a **Kiszolgálói címét**, a Dataverse-szervezethez majd válassza a **Bejelentkezés** lehetőséget.

   :::image type="content" source="media/ingest-dataverse-server-address.png" alt-text="Az adatok beíratási lépésének képernyője, ahol a felhasználó megadhatja a Dataverse-környezet URL-címét.":::

6. Válassza ki azokat a táblákat, amelyeken entitásként szeretne betölteni célközönséggel kapcsolatos információkba az elérhető listából.    

   > [!NOTE]
   > Ha már vannak kijelölve táblák, akkor más Dynamics 365-alkalmazások (pl. a Dynamics 365 Sales Insights vagy a Customer Service Insights) is használni tudják ezeket. Ez a kijelölés nem módosítható. Ezek a táblák entitásként lesznek elérhetők az adatforrás létrehozása után.

   :::image type="content" source="media/select-dataverse-entities.png" alt-text="Egy párbeszédpanel, amely a Dataverse-környezetben található entitások listáját mutatja.":::

7. Mentse a beállítást, és indítsa el a kijelölt táblák szinkronizálását a Dataverse-ből. Az újonnan felvett kapcsolatot az **Adatforrások** lapon találja. Frissítési várólistára kerül, és az entitások számát 0-ként mutatja, amíg meg nem szinkronizálja az összes kijelölt táblát.

Csak egy környezethez tartozó adatforrás használhatja a egyszerre ugyanazt a Dataverse felügyelt tavat.

## <a name="edit-a-dataverse-managed-lake-data-source"></a>Egy Dataverse felügyelt tó adatforrásának szerkesztése

Az entitások kijelölését csak az adatforrás létrehozása után módosíthatja. Ha például további entitásokat adtak hozzá a Dataverse szolgáltatáshoz, és azokat is importálni kívánja.    
Ha másik Dataverse-adattóhoz szeretne kapcsolódni, [hozzon létre egy új adatforrást](#connect-to-a-dataverse-managed-lake).

1. A célközönség információin belül nyissa meg a következőt **Adatok** > **Adatforrások**.

2. A frissíteni kívánt adatforrás mellett jelölje ki a három pontot.

3. Válassza a lista **Szerkesztés** elemét.

4. Jelöljön ki további entitásokat a rendelkezésre álló entitások listájából, és válassza a **Mentés** lehetőséget.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
