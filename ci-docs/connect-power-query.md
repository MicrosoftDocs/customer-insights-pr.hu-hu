---
title: Adatok betöltése összekötőn keresztül Power Query (videót tartalmaz)
description: Összekötők adatforrásokhoz a alapján Power Query.
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
ms.openlocfilehash: 4db97ec02eb96662d30a8536ea42372f81f318d2
ms.sourcegitcommit: b515120bebd2638f2639004422cee3cff42fbdf7
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/24/2022
ms.locfileid: "8800151"
---
# <a name="connect-to-a-power-query-data-source"></a>Csatlakozás adatforrás Power Query

Power Query összekötők széles választékát kínálja az adatok betöltéséhez. A legtöbb ilyen csatlakozót a támogatja Dynamics 365 Customer Insights. 

Az összekötőkön alapuló Power Query adatforrások hozzáadása általában az ebben a szakaszban ismertetett lépéseket követi. A használt csatlakozótól függően azonban eltérő információra van szükség. További információt az összekötő-hivatkozásban található, az [Power Query egyes összekötőkről szóló dokumentációban talál](/power-query/connectors/).

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWN6EK]

## <a name="create-a-new-data-source"></a>Új adatforrás létrehozása

1. Válassza az **Adatok** > **Adatforrások** lehetőséget.

1. Válassza az **Adatforrás hozzáadása** lehetőséget.

1. Válassza a **Microsoft Power Query** lehetőséget.

1. Adja meg a adatforrás **Nevét**, majd válassza a **Következő** lehetőséget a adatforrás létrehozásához.

1. Válassza ki az egyik [elérhető csatlakozót](#available-power-query-data-sources). Ebben a példában a **Szöveg/CSV** összekötőt választjuk ki.

1. Adja meg a kijelölt összekötő **Kapcsolati beállításaiban** a szükséges adatokat, és az adatok előnézetének megtekintéséhez válassza a **Tovább** lehetőséget.

1. Válassza az **Adatok átalakítása** lehetőséget. Ebben a lépésben entitásokat ad hozzá az adatforráshoz. Az entitások adatkészletek. Ha olyan adatbázissal rendelkezik, amely több adathalmazt tartalmaz, akkor mindegyik adathalmazhoz saját entitás tartozik.

1. A **Power Query - Lekérdezések** szerkesztése párbeszédpanel lehetővé teszi az adatok áttekintését és finomítását. Az entitások, amelyekkel a rendszerek a kijelölt adatforrásban azonosítottak megjelennek a bal ablaktáblában.

   > [!div class="mx-imgBorder"]
   > ![Lekérdezések szerkesztése párbeszédpanel.](media/data-manager-configure-edit-queries.png "Lekérdezések szerkesztése párbeszédpanel")

1. Át is alakíthatja adatait. Jelöljön ki egy módosítani vagy átalakítani kívánt entitást. Átalakítások alkalmazásához használja az Power Query ablakban található beállításokat. Minden átalakítás az **Alkalmazott lépések** területen jelenik meg. Power Query számos előre elkészített átalakítási lehetőséget kínál. További információt az Átalakítások [Power Query című témakörben talál](/power-query/power-query-what-is-power-query#transformations).

   Javasoljuk, hogy a következő átalakításokat használja:

   - Ha egy CSV-fájlból tölti be az adatokat, az első sor gyakran tartalmaz fejléceket. Válassza az Átalakítás lehetőséget, **és** válassza **az Első sor használata fejlécként** lehetőséget.
   - Ügyeljen arra, hogy az adattípus megfelelően legyen beállítva. Dátummezőkhöz például válasszon ki egy dátumtípust.

1. Ha további entitásokat szeretne hozzáadni a adatforrás a Lekérdezések **szerkesztése párbeszédpanelen, nyissa meg** a Kezdőlap **lehetőséget, és válassza az** Adatok **beolvasása lehetőséget**.

1. Az átalakítások mentéséhez válassza az ablak alján található **Mentés** lehetőséget Power Query. A mentést követően az adatforrást az **Adatok** > **Adatforrások** helyen találja.

1. Az **Adatforrások** lapon látja, hogy az új adatforrás a **Frissítés** állapotában van.

## <a name="available-power-query-data-sources"></a>Elérhető Power Query adatforrások

Az összekötő hivatkozásában [Power Query találja az](/power-query/connectors/) összekötők listáját, amelyekkel adatokat importálhat a Customer Insights szolgáltatásba. 

Az Ügyfélelemzések (Adatfolyamok) **oszlopban** pipával ellátott összekötők új adatforrások létrehozásához érhetők el a program alapján Power Query. Egy adott csatlakozó dokumentációjának áttekintésével többet megtudhat az előfeltételekről, a korlátozásokról és egyéb részletekről.

## <a name="edit-power-query-data-sources"></a>Adatforrások szerkesztése Power Query

> [!NOTE]
> Előfordulhat, hogy az alkalmazás egyik folyamatában (például *szegmentálás*, *egyeztetés* vagy *egyesítés*) jelenleg használt adatforrások nem módosíthatók. 
>
> **A Beállítások** lapon nyomon követheti az egyes aktív folyamatok előrehaladását. A folyamat befejeződésekor visszaléphet az **Adatforrások** lapra, és elvégezheti a változtatásokat.

1. Válassza az **Adatok** > **Adatforrások** lehetőséget.

2. Jelölje ki a módosítani kívánt adatforrás melletti függőleges ellipszis (&vellip;) pontot, és válassza **a Legördülő menü Szerkesztés** parancsát.

   > [!div class="mx-imgBorder"]
   > ![Szerkesztés lehetőség.](media/edit-option-data-sources.png "Szerkesztés lehetőség")

   [!INCLUDE [progress-details-include](includes/progress-details-pane.md)]
   
3. Alkalmazza a módosításokat és átalakításokat a **Power Query - Lekérdezések** szerkesztése párbeszédpanelen az [Új adatforrás](#create-a-new-data-source) létrehozása szakaszban leírtak szerint.

4. A módosítások mentéséhez válassza **a Mentés** Power Query lehetőséget a módosítások mentése után.


[!INCLUDE [footer-include](includes/footer-banner.md)]
