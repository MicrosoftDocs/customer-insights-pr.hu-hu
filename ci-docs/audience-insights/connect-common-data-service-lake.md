---
title: Entitások összekapcsolása a Common Data Service felügyelt tóhoz
description: Adatok importálása Common Data Service felügyelt adattóből.
ms.date: 09/29/2020
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.reviewer: adkuppa
ms.openlocfilehash: 029857e2bbb5f6357a5c01138ceaad78887b7518
ms.sourcegitcommit: 6a6df62fa12dcb9bd5f5a39cc3ee0e2b3988184b
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/25/2020
ms.locfileid: "4643401"
---
# <a name="connect-to-data-in-a-common-data-service-managed-data-lake"></a>Kapcsolódás az adatokhoz egy Common Data Service felügyelt adattóban

[!INCLUDE [cc-data-platform-banner](../includes/cc-data-platform-banner.md)]

A cikkből megtudhatja, hogy a meglévő Dynamics 365-ügyfelek hogyan tudnak gyorsan kapcsolódni az analitikus entitásokhoz a Common Data Service felügyelt adattóban. A Common Data Service szervezet rendszergazdájának kell lennie ahhoz, hogy folytathassa, és megtekintse a felügyelt tóban elérhető entitások listáját.

## <a name="important-considerations"></a>Fontos tényezők

Az online szolgáltatásokban, például az Azure Data Lake Storage esetében tárolt adatok az adatok feldolgozásának vagy tárolásának helyétől eltérő helyen tárolhatók, vagy a Dynamics 365 Customer Insights megoldásban is tárolhatók. Az online szolgáltatásokban tárolt adatok importálásával vagy az ahhoz való kapcsolódással Ön elfogadja, hogy az adatok átvihetők és tárolhatók a Dynamics 365 Customer Insights alkalmazásban.  [Ismerje meg a Microsoft adatvédelmi központot](https://www.microsoft.com/trust-center)

## <a name="connect-to-a-common-data-service-managed-lake"></a>Csatlakozás egy Common Data Service felügyelt tóhoz

1. A célközönség információin belül nyissa meg a következőt **Adatok** > **Adatforrások**.

2. Válassza az **Adatforrás hozzáadása** lehetőséget.

3. Válassza a **Kapcsolódás a Common Data Service szolgáltatáshoz** lehetőséget, majd válassza a **Következő** elemet.

4. Adjon meg egy **Nevet** az adatforrás számára, majd válassza a **Tovább** elemet.

5. Adja meg a **Kiszolgáló címét** a Common Data Service szervezet számára , és válassza a **Bejelentkezés** lehetőséget.

   > [!div class="mx-imgBorder"]
   > ![A kiszolgáló Common Data Service kiszolgáló címének megadására szolgáló párbeszédpanel](media/enter-CDS-org-details.png)

6. Jelölje ki a betölteni kívánt entitásokat az elérhető listán.    

   > [!NOTE]
   > Ha bizonyos entitások már ki vannak jelölve, akkor más Dynamics 365 alkalmazások (például a Dynamics 365 Sales Insights vagy a Customer Service Insights) esetleg már használják. Ez a kijelölés nem módosítható. Ezek az entitások a adatforrás létrehozása után lesznek elérhetők.

   > [!div class="mx-imgBorder"]
   > ![Párbeszédpanel az entitások listáját mutatja a Common Data Service szervezeten belül](media/select-analytical-entities.png)

7. Mentse a kijelölést, és indítsa el a kijelölt entitások szinkronizálását a Common Data Service felügyelt tóba. Az újonnan felvett kapcsolatot az **Adatforrások** lapon találja. Ütemezve lesz frissítésre, és az entitások számam 0 lesz, amíg az összes entitás szinkronizálása meg nem történik.

Csak egy környezethez tartozó adatforrás használhatja a egyszerre ugyanazt a Common Data Service felügyelt tavat.

## <a name="edit-a-common-data-service-managed-lake-data-source"></a>Egy Common Data Service felügyelt tó adatforrásának szerkesztése

Az entitások kijelölését csak az adatforrás létrehozása után módosíthatja. Ha például további entitásokat adtak hozzá a Common Data Service szolgáltatáshoz, és azokat is importálni kívánja.    
A kapcsolódáshoz egy másik Common Data Service szolgáltatáshoz [hozzon létre egy újadatforrást](#connect-to-a-common-data-service-managed-lake).

1. A célközönség információin belül nyissa meg a következőt **Adatok** > **Adatforrások**.

2. A frissíteni kívánt adatforrás mellett jelölje ki a három pontot.

3. Válassza a lista **Szerkesztés** elemét.

4. Jelöljön ki további entitásokat a rendelkezésre álló entitások listájából, és válassza a **Mentés** lehetőséget.
