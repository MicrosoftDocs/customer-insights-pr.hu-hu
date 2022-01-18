---
title: Adatok betöltése összekötőn keresztül Power Query (videót tartalmaz)
description: Az adatforrások összekötői a Power Query.
ms.date: 12/06/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: adkuppa
ms.author: adkuppa
manager: shellyha
ms.openlocfilehash: aae49be4364676ecc7a307e60eeca13859f1662a
ms.sourcegitcommit: 9132fdf54070cc551ab878378078e6285852818f
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/18/2021
ms.locfileid: "7934981"
---
# <a name="connect-to-a-power-query-data-source"></a>Csatlakozás Power Query adatforrás

Power Query az adatok betöltéséhez csatlakozók széles halmazát kínálja. A legtöbb ilyen csatlakozót a támogatja Dynamics 365 Customer Insights. 

Az adatforrások összekötők alapján történő hozzáadása Power Query általában az ebben a szakaszban ismertetett lépéseket követi. A használt csatlakozótól függően azonban eltérő információra van szükség. További információért tekintse meg az egyes összekötők dokumentációját az [Power Query összekötő hivatkozásában](/power-query/connectors/).

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWN6EK]

## <a name="create-a-new-data-source"></a>Új adatforrás létrehozása

1. A célközönség információin belül nyissa meg a következőt **Adatok** > **Adatforrások**.

1. Válassza az **Adatforrás hozzáadása** lehetőséget.

1. Válassza a **Microsoft Power Query** lehetőséget, majd válassza a **Következő** lehetőséget.

1. Adja meg a adatforrás **Nevét**, majd válassza a **Következő** lehetőséget a adatforrás létrehozásához.

1. Válassza ki az egyik [elérhető csatlakozót](#available-power-query-data-sources). Ebben a példában a **Szöveg/CSV** csatlakozót választjuk.

1. Adja meg a kijelölt összekötő **Kapcsolati beállításaiban** a szükséges adatokat, és az adatok előnézetének megtekintéséhez válassza a **Tovább** lehetőséget.

1. Válassza az **Adatok átalakítása** lehetőséget. Ebben a lépésben entitásokat ad hozzá az adatforráshoz. Az entitások adatkészletek. Ha olyan adatbázissal rendelkezik, amely több adathalmazt tartalmaz, akkor mindegyik adathalmazhoz saját entitás tartozik.

1. A **Power Query - Lekérdezések szerkesztése** párbeszédpanelen áttekintheti és finomíthatja az adatokat. Az entitások, amelyekkel a rendszerek a kijelölt adatforrásban azonosítottak megjelennek a bal ablaktáblában.

   > [!div class="mx-imgBorder"]
   > ![Lekérdezések szerkesztése párbeszédpanel.](media/data-manager-configure-edit-queries.png "Lekérdezések szerkesztése párbeszédpanel")

1. Át is alakíthatja adatait. Jelöljön ki egy módosítani vagy átalakítani kívánt entitást. Az ablakban lévő beállításokkal Power Query átalakításokat alkalmazhat. Minden átalakítás az **Alkalmazott lépések** területen jelenik meg. Power Query számos előre elkészített átalakítási lehetőséget kínál. További információ: [Power Query Átalakítások](/power-query/power-query-what-is-power-query#transformations).

1. A adatforráshoz további entitások hozzáadásához válassza az **Adatok beolvasása** elemet a **Lekérdezések szerkesztése** párbeszédpanelen.

   Javasoljuk, hogy a következő átalakításokat használja:

   - Ha egy CSV-fájlból tölti be az adatokat, az első sor gyakran tartalmaz fejléceket. Nyissa meg a **Tábla átalakítása** elemet, és válassza **Fejlécek használata első sorként** lehetőséget.
   - Ügyeljen arra, hogy az adattípus megfelelően legyen beállítva.

1. Az **átalakítások** mentéséhez válassza az ablak alján található Power Query Mentés lehetőséget. A mentést követően az adatforrást az **Adatok** > **Adatforrások** helyen találja.

1. Az **Adatforrások** lapon látja, hogy az új adatforrás a **Frissítés** állapotában van.

## <a name="available-power-query-data-sources"></a>Elérhető Power Query adatforrások

Tekintse meg az [Power Query](/power-query/connectors/) összekötő hivatkozását az összekötők listájáról, amelyekkel adatokat importálhat a Customer Insights szolgáltatásba. 

A **Customer Insights (Dataflows) oszlopban pipával rendelkező** összekötők a Power Query. Egy adott csatlakozó dokumentációjának áttekintésével többet megtudhat az előfeltételekről, a korlátozásokról és egyéb részletekről.

## <a name="edit-power-query-data-sources"></a>Power Query Adatforrások szerkesztése

> [!NOTE]
> Előfordulhat, hogy az alkalmazás egyik folyamatában (például *szegmentálás*, *egyeztetés* vagy *egyesítés*) jelenleg használt adatforrások nem módosíthatók. 
>
> A **Beállítások** lapon nyomon követheti az egyes aktív folyamatok előrehaladását. A folyamat befejeződésekor visszaléphet az **Adatforrások** lapra, és elvégezheti a változtatásokat.

1. A célközönség információin belül nyissa meg a következőt **Adatok** > **Adatforrások**.

2. Jelölje be a módosítani kívánt adatforrás melletti függőleges ellipszist, és válassza a legördülő menüből a **Szerkesztés** lehetőséget.

   > [!div class="mx-imgBorder"]
   > ![Szerkesztés lehetőség.](media/edit-option-data-sources.png "Szerkesztés lehetőség")

   [!INCLUDE [progress-details-include](../includes/progress-details-pane.md)]
   
3. Alkalmazza a módosításokat és átalakításokat a **Power Query - Lekérdezések szerkesztése** párbeszédpanelen az Új adatforrás létrehozása szakaszban leírtak [szerint](#create-a-new-data-source).

4. A módosítások mentéséhez válassza **a Mentés a** Power Query szerkesztések befejezése után lehetőséget.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
