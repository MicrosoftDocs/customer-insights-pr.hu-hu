---
title: Adatforrások kiválasztása adatok betöltéséhez
description: Megismerkedhet vele, hogyan importálhat különböző forrásokból származó adatokat.
ms.date: 03/18/2022
ms.subservice: audience-insights
ms.topic: overview
author: adkuppa
ms.author: adkuppa
ms.reviewer: mhart
manager: shellyha
searchScope:
- ci-data-sources
- ci-create-data-source
- customerInsights
ms.openlocfilehash: 355d52eabde90e0764817cf479821264ebb2e5eb
ms.sourcegitcommit: b515120bebd2638f2639004422cee3cff42fbdf7
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/24/2022
ms.locfileid: "8800469"
---
# <a name="data-sources-overview"></a>Adatforrások áttekintése



Dynamics 365 Customer Insights széles forrásból származó adatokhoz kapcsolódik. A adatforrások összeskapcsolását gyakran nevezik *adatbetöltésnek*. Az adatok betöltése után [egyesítheti](data-unification.md) és műveleteket hajthat végre rajtuk.

## <a name="add-a-data-source"></a>Adatforrás felvétele

A választott beállítástól függően tekintse meg a adatforrás hozzáadásának részletes cikkeit.

A következő adatforrásokat adhatja hozzá:

- [Több tucat Power Query csatlakozón keresztül](connect-power-query.md)
- [Common Data Model-mappából](connect-common-data-model.md)
- [Saját Microsoft Dataverse tóból](connect-dataverse-managed-lake.md)
- [Azure Synapse Analytics Adatbázisból](connect-synapse.md)

## <a name="add-data-from-on-premises-data-sources"></a>Adatok hozzáadása helyszíni adatforrásokból

A helyszíni adatforrásokból származó adatok beolvasása az adatfolyamok alapján Microsoft Power Platform támogatott. Az adatfolyamokat a Customer Insights szolgáltatásban úgy engedélyezheti, hogy [a környezet beállításakor megadja a Microsoft Dataverse környezet URL-címét](create-environment.md).

A környezetnek a Dataverse Customer Insights szolgáltatással való társítása után létrehozott adatforrások alapértelmezés szerint adatfolyamokat [Power Platform használnak](/power-query/dataflows/overview-dataflows-across-power-platform-dynamics-365). Az adatfolyamok az adatátjáró használatával támogatják a helyszíni összekapcsolhatóságot. A környezet társítása Dataverse előtt [létező adatforrásokat helyszíni adatátjárók segítségével eltávolíthatja és újra létrehozhatja](/data-integration/gateway/service-gateway-app).

A meglévő Power BI vagy Power Apps környezet adatátjárói láthatók lesznek, és újra felhasználhatók a Customer Insightsban. Az adatforrások oldalon olyan Microsoft Power Platform környezetbe mutató hivatkozások láthatók, ahol megtekintheti és konfigurálhatja a helyszíni adatátjárókat.

> [!IMPORTANT]
> Győződjön meg arról, hogy az átjárók a legújabb verzióra vannak frissítve. Telepíthet egy frissítést, és újrakonfigurálhatja az átjárót az átjáró képernyőjén megjelenő parancssorból, vagy [letöltheti a legújabb verziót](https://powerapps.microsoft.com/downloads/). Ha nem a legújabb átjáróverziót használja, az adatfolyam frissítése olyan hibaüzenetekkel meghiúsul, mint a **Kulcsszó nem támogatott: konfigurációs tulajdonságok. Paraméter neve: kulcsszó**.

## <a name="review-ingested-data"></a>A betöltött adatok áttekintése
Ha a környezet adatfolyamokat tartalmaz Power Platform, az **Adatforrások** lap három szakaszt sorol fel: 
- **Megosztott**: Olyan adatforrások, amelyeket az összes Customer Insights-rendszergazda kezelhet. Power BI az adatfolyamok, a saját tárfiók és a Dataverse kezelt adattavahoz való csatolás példák a megosztott adatforrásokra.
- **Általam** kezelt adatáramlások: Power Platform az adatfolyamokat csak Ön hozhatja létre és kezelheti. Más Customer Insights-rendszergazdák csak ezeket az adatfolyamokat tekinthetik meg, de szerkeszthetik, frissíthetik vagy törölhetik őket.
- **Mások** által kezelt adatok: Power Platform más rendszergazdák által létrehozott adatfolyamok. Csak megtekintheti őket. Felsorolja az adatfolyam tulajdonosát, akivel bármilyen segítségért kapcsolatba léphet.
> [!NOTE]
> Minden entitás megtekinthető és használható más felhasználók számára. A felhasználói kontextualitás csak az adatforrásokra vonatkozik, az ezekből az adatfolyamokból származó entitásokra nem.

Ha nem Power Platform használ adatfolyamokat, nem fog látni csoportokat vagy szakaszokat. Az **Adatforrások** lap csak az összes adatforrás listáját tartalmazza.

Látni fogja az egyes betöltött adatforrások nevét, állapotát, valamint az adatoknak az adott forrásra vonatkozó utolsó frissítését. Az adatforrások listáját minden oszlop szerint rendezheti.

> [!div class="mx-imgBorder"]
> ![Adatforrás hozzáadva.](media/configure-data-datasource-added.png "Adatforrás hozzáadva")

[!INCLUDE [progress-details-include](includes/progress-details-pane.md)]

Az adatok betöltése időbe telhet. A sikeres frissítés után a betöltött adatok áttekinthetők az **Entitások** lapról. További információ: [Entitások](entities.md).

## <a name="refresh-a-data-source"></a>Adatforrás frissítése

Az adatforrások igény szerint automatikus frissítéssel vagy kézzel frissíthetők. 

Nyissa meg a **Rendszergazda** > **Rendszer** > [**Ütemezés**](system.md#schedule-tab) elemet az összes betöltött adatforrás ütemezett frissítéseinek konfigurálása.

Az adatforrás igény szerinti frissítéséhez hajtsa végre a következő lépéseket:

1. Válassza az **Adatok** > **Adatforrások** lehetőséget.

2. Jelölje ki a frissíteni kívánt adatforrás melletti függőleges ellipsziseket (&vellip;), és válassza **a Legördülő listából a Frissítés** lehetőséget.

3. Az adatforrás most már a manuális frissítésre váltja ki. Egy adatforrás frissítése frissíteni fogja az entitássémát és az adatokat a frissítésben megadott összes adatforrás számára.

4. Válassza a **Frissítés leállítása**, ha meg akarja szakítani a meglévő frissítést, és az adatforrás visszaáll a legutóbbi frissítési állapotba.

## <a name="delete-a-data-source"></a>Adatforrás törlése

1. Válassza az **Adatok** > **Adatforrások** lehetőséget.

2. Jelölje ki az eltávolítani kívánt adatforrás melletti függőleges ellipsziseket (&vellip;), és válassza a Törlés **parancsot** a legördülő menüből.

3. Hagyja jóvá a törlést.


[!INCLUDE [footer-include](includes/footer-banner.md)]
