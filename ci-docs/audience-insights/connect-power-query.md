---
title: Adatok betöltése Power Query-összekötőn keresztül (Videó)
description: Összekötők Power Query alapú adatforrásokhoz.
ms.date: 12/06/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: adkuppa
ms.author: adkuppa
manager: shellyha
ms.openlocfilehash: 38c447d80a25feca087ca9f110278b8401423018
ms.sourcegitcommit: 12910882ca990ec0e890ed4deaf3dac7e01621e5
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/10/2021
ms.locfileid: "7903843"
---
# <a name="connect-to-a-power-query-data-source"></a>Csatlakozás Power Queryhoz adatforráshoz

A Power Query a csatlakozók széles körét biztosítja az adatok betöltéséhez. A legtöbb ilyen csatlakozót a támogatja Dynamics 365 Customer Insights. 

Az adatforrások hozzáadása Power Query összekötők alapján általában az ebben a szakaszban ismertetett lépéseket követi. A használt csatlakozótól függően azonban eltérő információra van szükség. További információért tekintse meg az egyes csatlakozók dokumentációját a [Power Query csatlakozó hivatkozásában](/power-query/connectors/).

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWN6EK]

## <a name="create-a-new-data-source"></a>Új adatforrás létrehozása

1. A célközönség információin belül nyissa meg a következőt **Adatok** > **Adatforrások**.

1. Válassza az **Adatforrás hozzáadása** lehetőséget.

1. Válassza **a Microsoft Power Query** lehetőséget, majd válassza a Tovább **lehetőséget**.

1. Adja meg a adatforrás **Nevét**, majd válassza a **Következő** lehetőséget a adatforrás létrehozásához.

1. Válassza ki az egyik [elérhető csatlakozót](#available-power-query-data-sources). Ebben a példában a **Szöveg/CSV** csatlakozót választjuk.

1. Adja meg a kijelölt összekötő **Kapcsolati beállításaiban** a szükséges adatokat, és az adatok előnézetének megtekintéséhez válassza a **Tovább** lehetőséget.

1. Válassza az **Adatok átalakítása** lehetőséget. Ebben a lépésben entitásokat ad hozzá az adatforráshoz. Az entitások adatkészletek. Ha olyan adatbázissal rendelkezik, amely több adathalmazt tartalmaz, akkor mindegyik adathalmazhoz saját entitás tartozik.

1. A **Power Query – Lekérdezések szerkesztése** párbeszédpanel lehetővé teszi az adatok áttekintését és finomítását. Az entitások, amelyekkel a rendszerek a kijelölt adatforrásban azonosítottak megjelennek a bal ablaktáblában.

   > [!div class="mx-imgBorder"]
   > ![Lekérdezések szerkesztése párbeszédpanel.](media/data-manager-configure-edit-queries.png "Lekérdezések szerkesztése párbeszédpanel")

1. Át is alakíthatja adatait. Jelöljön ki egy módosítani vagy átalakítani kívánt entitást. Az átalakítások alkalmazásához használja a Power Query ablak beállításait. Minden átalakítás az **Alkalmazott lépések** területen jelenik meg. A Power Query számos előre elkészített átalakítási beállítást biztosít. További információ: [Power Query átalakítások](/power-query/power-query-what-is-power-query#transformations).

1. A adatforráshoz további entitások hozzáadásához válassza az **Adatok beolvasása** elemet a **Lekérdezések szerkesztése** párbeszédpanelen.

   Javasoljuk, hogy a következő átalakításokat használja:

   - Ha egy CSV-fájlból tölti be az adatokat, az első sor gyakran tartalmaz fejléceket. Nyissa meg a **Tábla átalakítása** elemet, és válassza **Fejlécek használata első sorként** lehetőséget.
   - Ügyeljen arra, hogy az adattípus megfelelően legyen beállítva.

1. Az átalakítások elmentéséhez válassza a Power Query ablak alján lévő **Mentés** gombot. A mentést követően az adatforrást az **Adatok** > **Adatforrások** helyen találja.

1. Az **Adatforrások** lapon látja, hogy az új adatforrás a **Frissítés** állapotában van.

## <a name="available-power-query-data-sources"></a>Rendelkezésre álló Power Query-adatforrások

Tekintse meg a [Power Query összekötő](/power-query/connectors/) hivatkozását azon összekötők listájáról, amelyekkel adatokat importálhat a Customer Insights szolgáltatásba. 

Azok az összekötők, amelyeknél a **Customer Insights (adatfolyamok)** oszlopában egy pipa látható érhetők el új adatforrások létrehozásához a Power Query-re építve. Egy adott csatlakozó dokumentációjának áttekintésével többet megtudhat az előfeltételekről, a korlátozásokról és egyéb részletekről.

## <a name="edit-power-query-data-sources"></a>Power Query-adatforrások szerkesztése

> [!NOTE]
> Előfordulhat, hogy az alkalmazás egyik folyamatában (például *szegmentálás*, *egyeztetés* vagy *egyesítés*) jelenleg használt adatforrások nem módosíthatók. 
>
> A **Beállítások** lapon nyomon követheti az egyes aktív folyamatok előrehaladását. A folyamat befejeződésekor visszaléphet az **Adatforrások** lapra, és elvégezheti a változtatásokat.

1. A célközönség információin belül nyissa meg a következőt **Adatok** > **Adatforrások**.

2. Jelölje be a módosítani kívánt adatforrás melletti függőleges ellipszist, és válassza a legördülő menüből a **Szerkesztés** lehetőséget.

   > [!div class="mx-imgBorder"]
   > ![Szerkesztés lehetőség.](media/edit-option-data-sources.png "Szerkesztés lehetőség")

   [!INCLUDE [progress-details-include](../includes/progress-details-pane.md)]
   
3. Alkalmazza a változtatásokat és az átalakításokat az **Power Query - Lekérdezések szerkesztése** párbeszédpanelen az [Új adatforrás létrehozása](#create-a-new-data-source) című részben leírtak szerint.

4. A változtatások mentéséhez a módosítások elvégzése után válassza a **Mentés** lehetőséget a Power Query-ben.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
