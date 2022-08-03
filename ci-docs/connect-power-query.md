---
title: Csatlakozás adatforrás Power Query (videót tartalmaz)
description: Az adatok átvitele összekötőn Power Query keresztül (videót tartalmaz).
ms.date: 07/26/2022
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
ms.openlocfilehash: 7af51ed04fbd28149ea501c58e6fe71b5fa6d4b6
ms.sourcegitcommit: 5807b7d8c822925b727b099713a74ce2cb7897ba
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/28/2022
ms.locfileid: "9207048"
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

1. Válassza az **Adatok átalakítása** lehetőséget.

1. A **Power Query - Lekérdezések** szerkesztése párbeszédpanelen áttekintheti és finomíthatja az adatokat. Az entitások, amelyekkel a rendszerek a kijelölt adatforrásban azonosítottak megjelennek a bal ablaktáblában.

   :::image type="content" source="media/data-manager-configure-edit-queries.png" alt-text="Lekérdezések szerkesztése párbeszédpanel":::

1. Át is alakíthatja adatait. Jelöljön ki egy módosítani vagy átalakítani kívánt entitást. Az átalakítások alkalmazásához használja az Power Query ablak beállításait. Az egyes átalakítások az Alkalmazott lépések **alatt** vannak felsorolva. Power Query számos [előre elkészített átalakítási](/power-query/power-query-what-is-power-query#transformations) lehetőséget kínál.

   Javasoljuk, hogy használja a következő átalakításokat:

   - Ha egy CSV-fájlból tölti be az adatokat, az első sor gyakran tartalmaz fejléceket. Lépjen az Átalakítás **elemre,** és válassza az Első sor használata fejlécként **lehetőséget**.
   - Ügyeljen arra, hogy az adattípus megfelelően legyen beállítva. A dátummezőkhöz például válasszon ki egy dátumtípust.

1. Ha további entitásokat szeretne hozzáadni a adatforrás a Lekérdezések **szerkesztése párbeszédpanelen, lépjen a Kezdőlapra** **, és válassza az** Adatok **lekérése lehetőséget**. Ismételje az 5–10. lépést, amíg hozzá nem adta az összes entitást ehhez a adatforrás. Ha olyan adatbázissal rendelkezik, amely több adathalmazt tartalmaz, akkor mindegyik adathalmazhoz saját entitás tartozik.

1. Válassza a **Mentés** parancsot. **Megnyílik az Adatforrások** lap, amelyen az új adatforrás a Frissítés **állapot.**

   [!INCLUDE [progress-details-include](includes/progress-details-pane.md)]

Az adatok betöltése időbe telhet. A sikeres frissítés után a betöltött adatok az [**Entitások oldalon ellenőrizhetők**](entities.md).

> [!CAUTION]
> A adatforrás alapján Power Query adatfolyamot [Dataverse](/power-query/dataflows/overview-dataflows-across-power-platform-dynamics-365) hoz létre. Ne módosítsa az adatfolyam nevét a Power Platform Customer Insightsban használt felügyeleti központban. Az adatfolyamok átnevezése problémákat okoz a Customer Insights adatforrás és az Dataverse adatfolyam közötti referenciákkal kapcsolatban.

### <a name="available-power-query-data-sources"></a>Rendelkezésre álló Power Query adatforrások

Az összekötők referenciájában [Power Query megtekintheti azoknak az](/power-query/connectors/) összekötőknek a listáját, amelyek segítségével adatokat importálhat a Customer Insights szolgáltatásba.

A Customer Insights (Adatfolyamok) **oszlopban** pipával ellátott összekötők érhetők el új adatforrások létrehozásához a következő alapján Power Query: . Tekintse át egy adott összekötő dokumentációját, ha többet szeretne megtudni az előfeltételekről, [a lekérdezési korlátozásokról](/power-query/power-query-online-limits) és egyéb részletekről.

## <a name="add-data-from-on-premises-data-sources"></a>Adatok hozzáadása helyszíni adatforrásokból

Az adatok helyszíni adatforrásokból való betöltése adatfolyamok (PPDF-ek) alapján Microsoft Power Platform támogatott. Az adatfolyamokat a Customer Insightsban engedélyezheti, ha [megadja a Microsoft Dataverse környezet URL-címét](create-environment.md) a környezet beállításakor.

A környezet és a Dataverse Customer Insights társítása után létrehozott adatforrások alapértelmezés szerint adatfolyamokat [Power Platform használnak](/power-query/dataflows/overview-dataflows-across-power-platform-dynamics-365). Az adatfolyamok az adatátjáró használatával támogatják a helyszíni összekapcsolhatóságot. A környezet társítása Dataverse előtt [létező adatforrásokat helyszíni adatátjárók](/data-integration/gateway/service-gateway-app) használatával távolíthatja el és hozhatja létre újra.

A meglévő Power BI vagy Power Apps környezetből származó adatátjárók láthatók lesznek, és újra felhasználhatja őket a Customer Insights szolgáltatásban. Az adatforrások oldalon olyan Microsoft Power Platform környezetbe mutató hivatkozások láthatók, ahol megtekintheti és konfigurálhatja a helyszíni adatátjárókat.

> [!IMPORTANT]
> Győződjön meg arról, hogy az átjárók frissítve vannak a legújabb verzióra. Telepíthet egy frissítést, és újrakonfigurálhat egy átjárót az átjáró képernyőjén közvetlenül megjelenő parancssorból, vagy [letöltheti a legújabb verziót](https://powerapps.microsoft.com/downloads/). Ha nem a legújabb átjáróverziót használja, az adatfolyam frissítése sikertelen az alábbi hibaüzenetekkel, például **A kulcsszó nem támogatott: konfigurációs tulajdonságok. Paraméter neve: kulcsszó**.
>
> A Customer Insights helyszíni adatátjáróival kapcsolatos hibákat gyakran konfigurációs problémák okozzák. Az adatátjárók hibaelhárításával kapcsolatos további információkért lásd: [A helyszíni adatátjáró hibaelhárítása](/data-integration/gateway/service-gateway-tshoot).

## <a name="edit-power-query-data-sources"></a>Adatforrások szerkesztése Power Query

> [!NOTE]
> Előfordulhat, hogy nem lehet módosítani az alkalmazás egyik folyamatában jelenleg használt adatforrásokat (például szegmentálás vagy adategyesítés).
>
> **A Beállítások** lapon nyomon követheti az egyes aktív folyamatok előrehaladását. A folyamat befejeződésekor visszaléphet az **Adatforrások** lapra, és elvégezheti a változtatásokat.

1. Válassza az **Adatok** > **Adatforrások** lehetőséget.

1. A frissíteni kívánt adatforrás mellett válassza a Szerkesztés **lehetőséget**.

1. Alkalmazza a módosításokat és átalakításokat a **Power Query - Lekérdezések** szerkesztése párbeszédpanelen az [Új adatforrás](#create-a-new-data-source) létrehozása szakaszban leírtak szerint.

1. Válassza a Mentés **lehetőséget** a módosítások alkalmazásához és az **Adatforrások** lapra való visszatéréshez.

   [!INCLUDE [progress-details-include](includes/progress-details-pane.md)]

[!INCLUDE [footer-include](includes/footer-banner.md)]
