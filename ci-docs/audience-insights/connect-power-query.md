---
title: Adatok betöltése Power Query összekötőn keresztül
description: Összekötők Power Query alapú adatforrásokhoz.
ms.date: 09/29/2020
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: adkuppa
ms.author: adkuppa
manager: shellyha
ms.openlocfilehash: 50c231070ff9930c1ea82971bf4f8541a89d5027
ms.sourcegitcommit: 0b754d194d765afef70d1008db7b347dd1f0ee40
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/24/2021
ms.locfileid: "6305894"
---
# <a name="connect-to-a-power-query-data-source"></a>Csatlakozás Power Queryhoz adatforráshoz

A Power Query a csatlakozók széles körét biztosítja az adatok betöltéséhez. A legtöbb ilyen csatlakozót a támogatja Dynamics 365 Customer Insights. Power Query csatlakozón alapuló adatforrások hozzáadása általában a következő szakaszban leírt lépéseket követi. A használt csatlakozótól függően azonban eltérő információra van szükség. További információkért tekintse meg az egyes összekötők dokumentációját a [Power Query-összekötő referencia](/power-query/connectors/).

## <a name="create-a-new-data-source"></a>Új adatforrás létrehozása

1. A célközönség információin belül nyissa meg a következőt **Adatok** > **Adatforrások**.

1. Válassza az **Adatforrás hozzáadása** lehetőséget.

1. Válassza az **Adatok importálása** módszert, és válassza a **Tovább** lehetőséget.

1. Adja meg a adatforrás **Nevét**, majd válassza a **Következő** lehetőséget a adatforrás létrehozásához. Névvel kapcsolatos irányelvek: 
   - Kezdje egy betűvel.
   - Csak betűket és számokat használjon. Speciális karakterek és szóközök nem adhatók meg.
   - 3–64 karakter használható.

1. Válassza ki az egyik [elérhető csatlakozót](#available-power-query-data-sources). Ebben a példában a **Szöveg/CSV** összekötőt választjuk.

1. Adja meg a kijelölt összekötő **Kapcsolati beállításaiban** a szükséges adatokat, és az adatok előnézetének megtekintéséhez válassza a **Tovább** lehetőséget.

1. Válassza az **Adatok átalakítása** lehetőséget. Ebben a lépésben entitásokat ad hozzá az adatforráshoz. Az entitások adatkészletek. Ha olyan adatbázissal rendelkezik, amely több adathalmazt tartalmaz, akkor mindegyik adathalmazhoz saját entitás tartozik.

1. A **Power Query – Lekérdezések szerkesztése** párbeszédpanel lehetővé teszi az adatok áttekintését és finomítását. Az entitások, amelyekkel a rendszerek a kijelölt adatforrásban azonosítottak megjelennek a bal ablaktáblában.

   > [!div class="mx-imgBorder"]
   > ![Lekérdezések szerkesztése párbeszédpanel](media/data-manager-configure-edit-queries.png "Lekérdezések szerkesztése párbeszédpanel")

1. Át is alakíthatja adatait. Jelöljön ki egy módosítani vagy átalakítani kívánt entitást. Az átalakítások alkalmazásához használja a Power Query ablak beállításait. Minden átalakítás az **Alkalmazott lépések** területen jelenik meg. A Power Query számos előre elkészített átalakítási beállítást biztosít. További információ: [Power Query átalakítások](/power-query/power-query-what-is-power-query#transformations).

1. A adatforráshoz további entitások hozzáadásához válassza az **Adatok beolvasása** elemet a **Lekérdezések szerkesztése** párbeszédpanelen.

   Ezek az átalakítások erősen ajánlottak:

   - Ha egy CSV-fájlból tölti be az adatokat, az első sor gyakran tartalmaz fejléceket. Nyissa meg a **Tábla átalakítása** elemet, és válassza **Fejlécek használata első sorként** lehetőséget.
   - Ügyeljen arra, hogy az adattípus megfelelően legyen beállítva.

1. Az átalakítások elmentéséhez válassza a Power Query ablak alján lévő **Mentés** gombot. A mentést követően az adatforrást az **Adatok** > **Adatforrások** helyen találja.

1. Az **Adatforrások** lapon látja, hogy az új adatforrás a **Frissítés** állapotában van.

## <a name="available-power-query-data-sources"></a>Rendelkezésre álló Power Query-adatforrások

Tekintse meg a [Power Query-összekötő referencia](/power-query/connectors/) dokumentumot azon összekötők listájának megjelenítéséhez, amelyeket kiválaszthat adatok importálásához a Customer Insights alkalmazásba. 

Azok az összekötők, amelyeknél a **Customer Insights (adatfolyamok)** oszlopában egy pipa látható érhetők el új adatforrások létrehozásához a Power Query-re építve. Egy adott csatlakozó dokumentációjának áttekintésével többet megtudhat az előfeltételekről, a korlátozásokról és egyéb részletekről.

## <a name="edit-power-query-data-sources"></a>Power Query-adatforrások szerkesztése

> [!NOTE]
> Előfordulhat, hogy az alkalmazás egyik folyamatában (például *szegmentálás*, *egyeztetés* vagy *egyesítés*) jelenleg használt adatforrások nem módosíthatók. 
>
> A **Beállítások** oldal használatával nyomon követheti az egyes aktív folyamatok állapotát. A folyamat befejeződésekor visszaléphet az **Adatforrások** lapra, és elvégezheti a változtatásokat.

1. A célközönség információin belül nyissa meg a következőt **Adatok** > **Adatforrások**.

2. Jelölje be a módosítani kívánt adatforrás melletti függőleges ellipszist, és válassza a legördülő menüből a **Szerkesztés** lehetőséget.

   > [!div class="mx-imgBorder"]
   > ![Szerkesztés lehetőség](media/edit-option-data-sources.png "Szerkesztés lehetőség")

3. Alkalmazza a változtatásokat és az átalakításokat az **Power Query - Lekérdezések szerkesztése** párbeszédpanelen az [Új adatforrás létrehozása](#create-a-new-data-source) című részben leírtak szerint.

4. A változtatások mentéséhez a módosítások elvégzése után válassza a **Mentés** lehetőséget a Power Query-ben.


[!INCLUDE[footer-include](../includes/footer-banner.md)]