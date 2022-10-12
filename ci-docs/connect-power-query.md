---
title: Csatlakozás adatforrás Power Query (videót tartalmaz)
description: Az adatok átvitele összekötőn Power Query keresztül (videót tartalmaz).
ms.date: 09/29/2022
ms.reviewer: v-wendysmith
ms.subservice: audience-insights
ms.topic: how-to
author: mukeshpo
ms.author: mukeshpo
manager: shellyha
searchScope:
- ci-data-sources
- ci-create-data-source
- customerInsights
ms.openlocfilehash: 4cc7e57dfb0f8d050e91adc441c24e849882f5d8
ms.sourcegitcommit: be341cb69329e507f527409ac4636c18742777d2
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/30/2022
ms.locfileid: "9609893"
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

1. Tekintse át és finomítsa az adatokat a **Power Query - Lekérdezések** szerkesztése lapon. Az entitások, amelyekkel a rendszerek a kijelölt adatforrásban azonosítottak megjelennek a bal ablaktáblában.

   :::image type="content" source="media/data-manager-configure-edit-queries.png" alt-text="Lekérdezések szerkesztése párbeszédpanel":::

1. Alakítsa át az adatokat. Jelöljön ki egy módosítani vagy átalakítani kívánt entitást. Az átalakítások alkalmazásához használja az Power Query ablak beállításait. Az egyes átalakítások az Alkalmazott lépések **alatt** vannak felsorolva. Power Query számos [előre elkészített átalakítási](/power-query/power-query-what-is-power-query#transformations) lehetőséget kínál.

   > [!IMPORTANT]
   > Javasoljuk, hogy használja a következő átalakításokat:
   >
   > - Ha egy CSV-fájlból tölti be az adatokat, az első sor gyakran tartalmaz fejléceket. Lépjen az Átalakítás **elemre,** és válassza az Első sor használata fejlécként **lehetőséget**.
   > - Győződjön meg arról, hogy az adattípus megfelelően van beállítva, és megegyezik az adatokkal. A dátummezőkhöz például válasszon ki egy dátumtípust.

1. Ha további entitásokat szeretne hozzáadni a adatforrás a Lekérdezések **szerkesztése párbeszédpanelen, lépjen a Kezdőlapra** **, és válassza az** Adatok **lekérése lehetőséget**. Ismételje az 5–10. lépést, amíg hozzá nem adta az összes entitást ehhez a adatforrás. Ha olyan adatbázissal rendelkezik, amely több adathalmazt tartalmaz, akkor mindegyik adathalmazhoz saját entitás tartozik.

1. Válassza a **Mentés** parancsot. **Megnyílik az Adatforrások** lap, amelyen az új adatforrás a Frissítés **állapot.**

   [!INCLUDE [progress-details-include](includes/progress-details-pane.md)]

Az adatok betöltése időbe telhet. A sikeres frissítés után a betöltött adatok az [**Entitások oldalon ellenőrizhetők**](entities.md).

> [!CAUTION]
>
> - A adatforrás alapján Power Query adatfolyamot [Dataverse](/power-query/dataflows/overview-dataflows-across-power-platform-dynamics-365) hoz létre. Ne módosítsa az adatfolyam nevét a Power Platform Customer Insightsban használt felügyeleti központban. Az adatfolyamok átnevezése problémákat okoz a Customer Insights adatforrás és az Dataverse adatfolyam közötti referenciákkal kapcsolatban.
> - Az adatforrások egyidejű kiértékelése Power Query a Customer Insightsban ugyanazokkal [a frissítési korlátokkal rendelkezik, mint például az adatfolyamok a PowerBI.com](/power-query/power-query-online-limits#refresh-limits). Ha egy adatfrissítés meghiúsul, mert elérte a kiértékelési korlátot, javasoljuk, hogy módosítsa az egyes adatfolyamok frissítési ütemezését annak biztosítása érdekében, hogy az adatforrások feldolgozása ne legyen egyszerre.

### <a name="available-power-query-data-sources"></a>Rendelkezésre álló Power Query adatforrások

Az összekötők referenciájában [Power Query megtekintheti azoknak az](/power-query/connectors/) összekötőknek a listáját, amelyek segítségével adatokat importálhat a Customer Insights szolgáltatásba.

A Customer Insights (Adatfolyamok) **oszlopban** pipával ellátott összekötők érhetők el új adatforrások létrehozásához a következő alapján Power Query: . Tekintse át egy adott összekötő dokumentációját, ha többet szeretne megtudni az előfeltételekről, [a lekérdezési korlátozásokról](/power-query/power-query-online-limits) és egyéb részletekről.

## <a name="add-data-from-on-premises-data-sources"></a>Adatok hozzáadása helyszíni adatforrásokból

Az adatok helyszíni adatforrásokból való betöltése adatfolyamok (PPDF-ek) alapján Microsoft Power Platform támogatott. Az adatfolyamokat a Customer Insightsban engedélyezheti, ha [megadja a Microsoft Dataverse környezet URL-címét](create-environment.md) a környezet beállításakor.

A környezet és a Dataverse Customer Insights társítása után létrehozott adatforrások alapértelmezés szerint adatfolyamokat [Power Platform használnak](/power-query/dataflows/overview-dataflows-across-power-platform-dynamics-365). Az adatfolyamok az adatátjáró használatával támogatják a helyszíni összekapcsolhatóságot. A környezet társítása Dataverse előtt [létező adatforrásokat helyszíni adatátjárók](/data-integration/gateway/service-gateway-app) használatával távolíthatja el és hozhatja létre újra.

Egy meglévő Power BI vagy Power Apps környezetből származó adatátjárók láthatók lesznek, és újra felhasználhatja őket a Customer Insightsban, ha az adatátjáró és a Customer Insights környezet ugyanabban az Azure-régióban található. Az adatforrások oldalon olyan Microsoft Power Platform környezetbe mutató hivatkozások láthatók, ahol megtekintheti és konfigurálhatja a helyszíni adatátjárókat.

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

## <a name="common-reasons-for-ingestion-errors-or-corrupt-data"></a>A betöltési hibák vagy a sérült adatok gyakori okai

### <a name="data-type-does-not-match-data"></a>Az adattípus nem egyezik az adatokkal

A leggyakoribb adattípus-eltérés akkor fordul elő, ha egy dátummező nincs a megfelelő dátumformátumra állítva.

Az adatok a forrásnál rögzíthetők és újra betölthetők. Vagy javítsa ki az átalakítást a Customer Insights segítségével. Az átalakítás javítása:

1. Válassza az **Adatok** > **Adatforrások** lehetőséget.

1. A sérült adatokat tartalmazó adatforrás mellett válassza a Szerkesztés **lehetőséget**.

1. Válassza a **Következő** lehetőséget.

1. Válassza ki az egyes lekérdezéseket, és keresse meg az "Alkalmazott lépések" alatt alkalmazott, helytelen átalakításokat, vagy azokat a dátumoszlopokat, amelyek nem lettek dátumformátummal átalakítva.

   :::image type="content" source="media/PQ_corruped_date.png" alt-text="Power Query- Helytelen dátumformátumot mutató szerkesztés":::

1. Módosítsa az adattípust úgy, hogy az megfelelően egyezzen az adatokkal.

1. Válassza a **Mentés** parancsot. Ez a adatforrás felfrissül.

## <a name="troubleshoot-ppdf-power-query-based-data-source-refresh-issues"></a>PPDF-alapú Power Query adatforrás frissítési problémák elhárítása

Ha az adatok elavultak, vagy adatforrás frissítés után hibaüzenetet kap, hajtsa végre a következő lépéseket:

1. Navigáljon ide: [Power Platform](https://make.powerapps.com).

1. Válassza ki a **Környezetet** a Customer Insights-példányhoz.

1. Lépjen az Adatfolyamok **lapra**.

1. A Customer Insights adatforrás megfelelő adatfolyamhoz válassza ki a függőleges három pontot (&vellip;), majd válassza a Frissítési előzmények **megjelenítése lehetőséget**.

1. Ha az **adatfolyam** állapota **Sikeres**, előfordulhat, hogy a Power Query-alapú adatforrás tulajdonjoga megváltozott:

   1. Tekintse át a frissítési ütemezést a frissítési előzményekből.
   1. Állítsa be az új tulajdonos ütemezését, és mentse el a beállításokat.

1. Ha az **adatfolyam** állapota **Sikertelen**:

   1. Töltse le a frissítési előzmények fájlját.
   1. Tekintse át a letöltött fájlt a hiba oka miatt.
   1. Ha a hiba nem oldható meg, válassza a **?** A támogatási jegy megnyitásához. Tartalmazza a letöltött frissítési előzmények fájlját.


[!INCLUDE [footer-include](includes/footer-banner.md)]
