---
title: Adatok beolvasása összekötőn keresztül Power Query (videót tartalmaz)
description: Adatforrások összekötői a alapján Power Query.
ms.date: 12/06/2021
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: adkuppa
ms.author: adkuppa
manager: shellyha
searchScope:
- ci-data-sources
- ci-create-data-source
- customerInsights
ms.openlocfilehash: 4c12933a0684094702843be309525dd6d5d9b6f4
ms.sourcegitcommit: 73cb021760516729e696c9a90731304d92e0e1ef
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/25/2022
ms.locfileid: "8355524"
---
# <a name="connect-to-a-power-query-data-source"></a>Power Query Csatlakozás adatforrás

Power Query az adatok beolvasásához összekötők széles halmazát kínálja. A legtöbb ilyen csatlakozót a támogatja Dynamics 365 Customer Insights. 

Az összekötőkön alapuló Power Query adatforrások hozzáadása általában az ebben a szakaszban ismertetett lépéseket követi. A használt csatlakozótól függően azonban eltérő információra van szükség. További információért tekintse meg az összekötő hivatkozásában található [Power Query egyes összekötők dokumentációját](/power-query/connectors/).

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWN6EK]

## <a name="create-a-new-data-source"></a>Új adatforrás létrehozása

1. A célközönség információin belül nyissa meg a következőt **Adatok** > **Adatforrások**.

1. Válassza az **Adatforrás hozzáadása** lehetőséget.

1. Válassza a **Microsoft Power Query** lehetőséget.

1. Adja meg a adatforrás **Nevét**, majd válassza a **Következő** lehetőséget a adatforrás létrehozásához.

1. Válassza ki az egyik [elérhető csatlakozót](#available-power-query-data-sources). Ebben a példában a **Szöveg/CSV** összekötőt választjuk.

1. Adja meg a kijelölt összekötő **Kapcsolati beállításaiban** a szükséges adatokat, és az adatok előnézetének megtekintéséhez válassza a **Tovább** lehetőséget.

1. Válassza az **Adatok átalakítása** lehetőséget. Ebben a lépésben entitásokat ad hozzá az adatforráshoz. Az entitások adatkészletek. Ha olyan adatbázissal rendelkezik, amely több adathalmazt tartalmaz, akkor mindegyik adathalmazhoz saját entitás tartozik.

1. A **Power Query - Lekérdezések** szerkesztése párbeszédpanelen áttekintheti és finomíthatja az adatokat. Az entitások, amelyekkel a rendszerek a kijelölt adatforrásban azonosítottak megjelennek a bal ablaktáblában.

   > [!div class="mx-imgBorder"]
   > ![Lekérdezések szerkesztése párbeszédpanel.](media/data-manager-configure-edit-queries.png "Lekérdezések szerkesztése párbeszédpanel")

1. Át is alakíthatja adatait. Jelöljön ki egy módosítani vagy átalakítani kívánt entitást. Az átalakítások alkalmazásához használja az Power Query ablakban található beállításokat. Minden átalakítás az **Alkalmazott lépések** területen jelenik meg. Power Query számos előre elkészített átalakítási lehetőséget kínál. További információ: [Power Query Átalakítások](/power-query/power-query-what-is-power-query#transformations).

   Javasoljuk, hogy a következő átalakításokat használja:

   - Ha egy CSV-fájlból tölti be az adatokat, az első sor gyakran tartalmaz fejléceket. Lépjen az Átalakítás **elemre,** és válassza az **Első sor használata fejlécként** lehetőséget.
   - Ügyeljen arra, hogy az adattípus megfelelően legyen beállítva. A dátummezőkhöz például válasszon ki egy dátumtípust.

1. Ha további entitásokat szeretne hozzáadni a adatforrás a Lekérdezések **szerkesztése párbeszédpanelen, lépjen a** Kezdőlap **gombra**, és válassza az Adatok **beolvasása lehetőséget**.

1. Az átalakítások mentéséhez válassza az ablak alján található **Mentés** lehetőséget Power Query. A mentést követően az adatforrást az **Adatok** > **Adatforrások** helyen találja.

1. Az **Adatforrások** lapon látja, hogy az új adatforrás a **Frissítés** állapotában van.

## <a name="available-power-query-data-sources"></a>Elérhető Power Query adatforrások

Az összekötők listáját az [Power Query ügyfélelemzésbe történő importáláshoz használhatja összekötők hivatkozásában](/power-query/connectors/) találja. 

A Customer Insights (Dataflows) **oszlopban** bejelölt összekötők új adatforrások létrehozására érhetők el a alapján Power Query. Egy adott csatlakozó dokumentációjának áttekintésével többet megtudhat az előfeltételekről, a korlátozásokról és egyéb részletekről.

## <a name="edit-power-query-data-sources"></a>Adatforrások szerkesztése Power Query

> [!NOTE]
> Előfordulhat, hogy az alkalmazás egyik folyamatában (például *szegmentálás*, *egyeztetés* vagy *egyesítés*) jelenleg használt adatforrások nem módosíthatók. 
>
> **A Beállítások** lapon nyomon követheti az egyes aktív folyamatok előrehaladását. A folyamat befejeződésekor visszaléphet az **Adatforrások** lapra, és elvégezheti a változtatásokat.

1. A célközönség információin belül nyissa meg a következőt **Adatok** > **Adatforrások**.

2. Jelölje be a módosítani kívánt adatforrás melletti függőleges ellipszist, és válassza a legördülő menüből a **Szerkesztés** lehetőséget.

   > [!div class="mx-imgBorder"]
   > ![Szerkesztés lehetőség.](media/edit-option-data-sources.png "Szerkesztés lehetőség")

   [!INCLUDE [progress-details-include](../includes/progress-details-pane.md)]
   
3. Alkalmazza a módosításokat és átalakításokat a **Power Query - Lekérdezések** szerkesztése párbeszédpanelen az [Új adatforrás](#create-a-new-data-source) létrehozása szakaszban leírtak szerint.

4. A módosítások mentéséhez válassza **a Mentés** lehetőséget Power Query a módosítások befejezése után.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
