---
title: Első lépések a Dynamics 365 Customer Insights alkalmazásban
description: A Customer Insights áttekintése segít a források gyors megkezdésében.
ms.reviewer: mhart
ms.author: mhart
author: m-hartmann
ms.date: 08/31/2021
ms.subservice: audience-insights
ms.topic: conceptual
ms.manager: shellyha
ms.custom: intro-internal
searchScope:
- ci-home
- customerInsights
ms.openlocfilehash: ce0336c4bf853bc81ec01c45410169a63b69eb03
ms.sourcegitcommit: 267c317e10166146c9ac2c30560c479c9a005845
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/16/2022
ms.locfileid: "9304614"
---
# <a name="get-started-with-dynamics-365-customer-insights"></a>Első lépések a Dynamics 365 Customer Insights alkalmazásban

A Customer Insights segítségével mélyebben megértheti ügyfeleit. A különböző tranzakciós, viselkedésbeli és megfigyelési forrásokból származó adatok összekapcsolhatók a 360 fokos ügyfélnézet létrehozásához. Ezekkel a betekintéssel ügyfélközpontú élményeket és folyamatokat támogathat. Az ügyféladatokat egyesítheti és megértheti, és kiaknázhatja a belőlük származó intelligens összefüggéseket és műveleteket.

## <a name="step-1-create-an-environment"></a>1. lépés: Környezet létrehozása

Először hozzon létre egy környezetet, amelyben dolgozni szeretne. Ha a szervezet már megvásárolt egy licencet, akkor lásd a [Környezet létrehozása](create-environment.md) részt. A Customer Insights próbaverziójának elindításához lásd: [Próbakörnyezet beállítása](trial-signup.md).

## <a name="step-2-explore-customer-insights"></a>2. lépés: Fedezze fel a Customer Insights szolgáltatást

Amikor először jelentkezik be a Customer Insights szolgáltatásba, konfigurálja a beállításokat, és fedezze fel a terméket.

1. [jelentkezzen be a Customer Insights szolgáltatásba](https://home.ci.ai.dynamics.com) Microsoft Azure Active Directory (AAD) felhasználói fiókjával.

1. Módosítsa a környezetet a bemutató adatok megtekintéséhez és [a Customer Insights felfedezéséhez](home.md).

## <a name="step-3-ingest-unify-and-set-up-relationships-for-your-data"></a>3. lépés: Betöltés, egyesítés és a kapcsolatok beállítása adataihoz

Az egyesített profilok az adatokkal kapcsolatos információk és a műveletek alapjai. Különböző forrásokból származó adatok behozása és az adategyesítési folyamat futtatása a unified profilok kombinálása érdekében. Adja meg kapcsolatok a betöltött entitások között, és bővítő funkciókkal adjon hozzá információkat a profilokhoz.

1. Adatok betöltése többféle lehetőségből származó adatforrások létrehozásával. Válasszon a, beleértve a Common Data Modelt [Azure Data Lake Storage is,](connect-common-data-model.md)[Azure Synapse Analytics](connect-synapse.md) vagy [Microsoft Dataverse](connect-dataverse-managed-lake.md) az összekötők [Power Query közül](connect-power-query.md).

1. Futtassa az [adategyesítési folyamatot](data-unification.md) a forrásmezők [azonosításával, az](map-entities.md) ismétlődések [eltávolításával](remove-duplicates.md), [a feltételek](match-entities.md) egyeztetésével és [a mezők](merge-entities.md) egyesítésével.

1. Ismerkedjen meg a [rendszer által létrehozott entitásokkal](entities.md), és [hozzon létre kapcsolatok a betöltött entitások között](relationships.md).

## <a name="step-4-enhance-unified-profiles-with-predictions-activities-and-measures"></a>4. lépés: Az egyesített profilok bővítése előrejelzésekkel, tevékenységekkel és mértékekkel

Az egységes profilok beállításával bővítheti az adatokat, és tovább növelheti az általuk biztosított információkat.

1. Az [ügyféladatok gyarapítása](enrichment-hub.md) érdekében válasszon a bővítési szolgáltatók közül.

1. Az [előre telepített modellekkel](predictions-overview.md) megbecsülheti az elvándorlást vagy a várható bevételeket.

1. A [tevékenységeket konfigurálhatja](activities.md) a beöltött adatok alapján, és kronologikus idővonalon ábrázolhatja az ügyfelekkel való kommunikációt.

1. Az üzleti célok és fő teljesítménymutatók megvalósításához [intézkedéseket hozhat létre](measures.md).

## <a name="step-5-create-segments-and-activate-data-through-various-export-options"></a>5. lépés: Szegmensek létrehozása és adatok aktiválása különféle exportálási lehetőségek segítségével

Most, hogy az adatok teljesek, és az ügyfelekkel kapcsolatos információk széles skáláját tartalmazzák, keresse meg az adatokkal kapcsolatos műveletek módjait.

1. [Hozzon létre szegmenseket](segments.md) ( az ügyfélkör részhalmazai) annak érdekében, hogy a tevékenységek a megcélzott ügyfelek szempontjából relevánsak legyenek.

1. Tallózhat az [exportálási lehetőségek](export-destinations.md) bővülő katalógusában, ahol az ügyféladatok használhat. Az adatok segítségével például kezelheti a promóciókat és kapcsolatba léphet a digitális marketing alkalmazásával.

1. Tekintse át az integrációs beállításokat, például más Dynamics 365-alkalmazásokhoz az [Ügyfélkártya bővítménnyel](customer-card-add-in.md).  


[!INCLUDE [footer-include](includes/footer-banner.md)]