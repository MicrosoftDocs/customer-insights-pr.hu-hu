---
title: Csatlakozás adatforrás Power Query (videót tartalmaz)
description: Az adatok átvitele összekötőn Power Query keresztül (videót tartalmaz).
ms.date: 06/13/2022
ms.reviewer: v-wendysmith
ms.subservice: audience-insights
ms.topic: how-to
author: adkuppa
ms.author: matgos
manager: shellyha
searchScope:
- ci-data-sources
- ci-create-data-source
- customerInsights
ms.openlocfilehash: 6736b253e3a7e652f92f61bc44bfb31ca69be31a
ms.sourcegitcommit: dca46afb9e23ba87a0ff59a1776c1d139e209a32
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/29/2022
ms.locfileid: "9082176"
---
# <a name="connect-to-a-power-query-data-source"></a>Csatlakozás adatforrás Power Query

Power Query összekötők széles körét kínálja az adatok betöltéséhez. A legtöbb ilyen csatlakozót a támogatja Dynamics 365 Customer Insights.

Az összekötőkön alapuló Power Query adatforrások hozzáadása általában az ebben a szakaszban ismertetett lépéseket követi. A használt csatlakozótól függően azonban eltérő információra van szükség. További információért tekintse meg az egyes összekötők dokumentációját az [Power Query összekötő-referenciában](/power-query/connectors/).

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWN6EK]

## <a name="create-a-new-data-source"></a>Új adatforrás létrehozása

1. Válassza az **Adatok** > **Adatforrások** lehetőséget.

1. Válassza az **Adatforrás hozzáadása** lehetőséget.

1. Válassza a **Microsoft Power Query** lehetőséget.

1. Adjon meg egy **nevet** és egy opcionális **leírást** a adatforrás, majd válassza a Tovább **gombot**.

1. Válassza ki az egyik [elérhető csatlakozót](#available-power-query-data-sources). Ebben a példában a **Text/CSV-összekötőt** választjuk ki.

1. Adja meg a kijelölt összekötő **Kapcsolati beállításaiban** a szükséges adatokat, és az adatok előnézetének megtekintéséhez válassza a **Tovább** lehetőséget.

1. Válassza az **Adatok átalakítása** lehetőséget. Ebben a lépésben entitásokat ad hozzá az adatforráshoz. Az entitások adatkészletek. Ha olyan adatbázissal rendelkezik, amely több adathalmazt tartalmaz, akkor mindegyik adathalmazhoz saját entitás tartozik.

1. A **Power Query - Lekérdezések** szerkesztése párbeszédpanelen áttekintheti és finomíthatja az adatokat. Az entitások, amelyekkel a rendszerek a kijelölt adatforrásban azonosítottak megjelennek a bal ablaktáblában.

   :::image type="content" source="media/data-manager-configure-edit-queries.png" alt-text="Lekérdezések szerkesztése párbeszédpanel":::

1. Át is alakíthatja adatait. Jelöljön ki egy módosítani vagy átalakítani kívánt entitást. Az átalakítások alkalmazásához használja az Power Query ablak beállításait. Az egyes átalakítások az Alkalmazott lépések **alatt** vannak felsorolva. Power Query számos előre elkészített átalakítási lehetőséget kínál. További információ: [Power Query Átalakítások](/power-query/power-query-what-is-power-query#transformations).

   Javasoljuk, hogy használja a következő átalakításokat:

   - Ha egy CSV-fájlból tölti be az adatokat, az első sor gyakran tartalmaz fejléceket. Lépjen az Átalakítás **elemre,** és válassza az Első sor használata fejlécként **lehetőséget**.
   - Ügyeljen arra, hogy az adattípus megfelelően legyen beállítva. A dátummezőkhöz például válasszon ki egy dátumtípust.

1. Ha további entitásokat szeretne hozzáadni a adatforrás a Lekérdezések **szerkesztése párbeszédpanelen, lépjen a Kezdőlapra** **, és válassza az** Adatok **lekérése lehetőséget**. Ismételje meg a 6–10. lépést, amíg hozzá nem adta az összes entitást ehhez a adatforrás.

1. Válassza a **Mentés** parancsot. **Megnyílik az Adatforrások** lap, amelyen az új adatforrás a Frissítés **állapot.**

### <a name="available-power-query-data-sources"></a>Rendelkezésre álló Power Query adatforrások

Az összekötők referenciájában [Power Query megtekintheti azoknak az](/power-query/connectors/) összekötőknek a listáját, amelyek segítségével adatokat importálhat a Customer Insights szolgáltatásba.

A Customer Insights (Adatfolyamok) **oszlopban** pipával ellátott összekötők érhetők el új adatforrások létrehozásához a következő alapján Power Query: . Tekintse át egy adott összekötő dokumentációját, ha többet szeretne megtudni az előfeltételekről, [a lekérdezési korlátozásokról](/power-query/power-query-online-limits) és egyéb részletekről.

## <a name="add-data-from-on-premises-data-sources"></a>Adatok hozzáadása helyszíni adatforrásokból

Az adatok helyszíni adatforrásokból való betöltése adatfolyamok (PPDF-ek) alapján Microsoft Power Platform támogatott. Az adatfolyamokat a Customer Insightsban engedélyezheti, ha [megadja a Microsoft Dataverse környezet URL-címét](create-environment.md) a környezet beállításakor.

A környezet és a Dataverse Customer Insights társítása után létrehozott adatforrások alapértelmezés szerint adatfolyamokat [Power Platform használnak](/power-query/dataflows/overview-dataflows-across-power-platform-dynamics-365). Az adatfolyamok az adatátjáró használatával támogatják a helyszíni összekapcsolhatóságot. A környezet társítása Dataverse előtt [létező adatforrásokat helyszíni adatátjárók](/data-integration/gateway/service-gateway-app) használatával távolíthatja el és hozhatja létre újra.

A meglévő Power BI vagy Power Apps környezet adatátjárói láthatók lesznek, és újra felhasználhatók a Customer Insightsban. Az adatforrások oldalon olyan Microsoft Power Platform környezetbe mutató hivatkozások láthatók, ahol megtekintheti és konfigurálhatja a helyszíni adatátjárókat.

> [!IMPORTANT]
> Győződjön meg arról, hogy az átjárók frissítve vannak a legújabb verzióra. Telepíthet egy frissítést, és újrakonfigurálhat egy átjárót az átjáró képernyőjén közvetlenül megjelenő parancssorból, vagy [letöltheti a legújabb verziót](https://powerapps.microsoft.com/downloads/). Ha nem a legújabb átjáróverziót használja, az adatfolyam frissítése sikertelen az alábbi hibaüzenetekkel, például **A kulcsszó nem támogatott: konfigurációs tulajdonságok. Paraméter neve: kulcsszó**.

## <a name="edit-power-query-data-sources"></a>Adatforrások szerkesztése Power Query

> [!NOTE]
> Előfordulhat, hogy az alkalmazás egyik folyamatában (például *szegmentálás*, *egyeztetés* vagy *egyesítés*) jelenleg használt adatforrások nem módosíthatók.
>
> **A Beállítások** lapon nyomon követheti az egyes aktív folyamatok előrehaladását. A folyamat befejeződésekor visszaléphet az **Adatforrások** lapra, és elvégezheti a változtatásokat.

1. Válassza az **Adatok** > **Adatforrások** lehetőséget.

1. A frissíteni kívánt adatforrás mellett válassza a Szerkesztés **lehetőséget**.

   [!INCLUDE [progress-details-include](includes/progress-details-pane.md)]

1. Alkalmazza a módosításokat és átalakításokat a **Power Query - Lekérdezések** szerkesztése párbeszédpanelen az [Új adatforrás](#create-a-new-data-source) létrehozása szakaszban leírtak szerint.

1. A módosítások befejezése után válassza a Mentés **lehetőséget** Power Query a módosítások mentéséhez.
