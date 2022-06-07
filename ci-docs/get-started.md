---
title: Ismerkedés a Dynamics 365 Customer Insights rendszerrel
description: A Customer Insights áttekintése segít az erőforrások gyors elindításában.
ms.reviewer: v-wendysmith
ms.author: mhart
author: m-hartmann
ms.date: 04/12/2022
ms.subservice: engagement-insights
ms.topic: conceptual
ms.manager: shellyha
ms.custom: intro-internal
searchScope:
- ci-home
- customerInsights
ms.openlocfilehash: 68c26eb0ad0da787a9f594b4aebe679588b0d6bf
ms.sourcegitcommit: f5af5613afd9c3f2f0695e2d62d225f0b504f033
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/01/2022
ms.locfileid: "8833578"
---
# <a name="get-started-with-dynamics-365-customer-insights"></a>Ismerkedés a Dynamics 365 Customer Insights rendszerrel

A Customer Insights segítségével mélyebben megismerheti ügyfeleit. A különböző tranzakciós, viselkedésbeli és megfigyelési forrásokból származó adatok összekapcsolhatók a 360 fokos ügyfélnézet létrehozásához. Ezekkel a betekintéssel ügyfélközpontú élményeket és folyamatokat támogathat. Az ügyféladatokat egyesítheti és megértheti, és kiaknázhatja a belőlük származó intelligens összefüggéseket és műveleteket.

## <a name="step-1-create-an-environment"></a>1. lépés: Környezet létrehozása

Először is, hozzon létre egy környezetet, amelyben dolgozhat. Ha a szervezet már megvásárolt egy licencet, akkor lásd a [Környezet létrehozása](create-environment.md) részt. A Customer Insights próbaverziójának elindításához olvassa el a Próbakörnyezet beállítása című [témakört](trial-signup.md).

## <a name="step-2-explore-customer-insights"></a>2. lépés: Fedezze fel az ügyfélelemzéseket

Amikor először jelentkezik be a Customer Insights szolgáltatásba, konfigurálja a beállításokat és feltárja a terméket.

1. [jelentkezzen be a Customer Insights](https://home.ci.ai.dynamics.com) szolgáltatásba Microsoft Azure Active Directory (AAD) felhasználói fiókjával.

1. Módosítsa a környezetet a bemutatóadatok megtekintéséhez és [a Customer Insights felfedezéséhez](home.md).

## <a name="step-3-ingest-unify-and-set-up-relationships-for-your-data"></a>3. lépés: Betöltés, egyesítés és a kapcsolatok beállítása adataihoz

Az egyesített profilok az adatokkal kapcsolatos információk és a műveletek alapjai. Különböző forrásokból származó adatok behozása és az adategyesítési folyamat futtatása a unified profilok kombinálása érdekében. Adja meg kapcsolatok a betöltött entitások között, és gazdagító funkciókkal adja hozzá az információkat a profilokhoz.

1. Adatok betöltése többféle lehetőségből származó adatforrások létrehozásával. Válasszon az [Power Query összekötők](connect-power-query.md), a [Common Data Model mappa](connect-common-data-model.md) vagy [Microsoft Dataverse](connect-dataverse-managed-lake.md) a között.

1. Futtassa az adategyesítési folyamatot [a forrásmezők](data-unification.md) azonosításával, az [ismétlődések](map-entities.md) eltávolításával [,](remove-duplicates.md) a feltételek [egyeztetésével és](match-entities.md) a mezők egyesítésével [.](merge-entities.md)

1. Ismerkedjen meg a [rendszer által létrehozott entitásokkal](entities.md), és [hozzon létre kapcsolatok a betöltött entitások között](relationships.md).

## <a name="step-4-enhance-unified-profiles-with-predictions-activities-and-measures"></a>4. lépés: Az egyesített profilok bővítése előrejelzésekkel, tevékenységekkel és mértékekkel

Az egységes profilok beállításával javítsa adatait, és tovább növelje az általuk szolgáltatott információkat.

1. Az [ügyféladatok gyarapítása](enrichment-hub.md) érdekében válasszon a bővítési szolgáltatók közül.

1. Az [előre telepített modellekkel](predictions-overview.md) megbecsülheti az elvándorlást vagy a várható bevételeket.

1. A [tevékenységeket konfigurálhatja](activities.md) a beöltött adatok alapján, és kronologikus idővonalon ábrázolhatja az ügyfelekkel való kommunikációt.

1. Az üzleti célok és fő teljesítménymutatók megvalósításához [intézkedéseket hozhat létre](measures.md).

## <a name="step-5-create-segments-and-activate-data-through-various-export-options"></a>5. lépés: Szegmensek létrehozása és adatok aktiválása különféle exportálási lehetőségek segítségével

Most, hogy az adatok elkészültek, és széles körű információkat tartalmaznak az ügyfelekről, keresse meg a módját, hogy lépéseket tegyen az adatokkal kapcsolatban.

1. [Hozzon létre szegmenseket](segments.md) ( az ügyfélkör részhalmazai) annak érdekében, hogy a tevékenységek a megcélzott ügyfelek szempontjából relevánsak legyenek.

1. Tallózhat az [exportálási lehetőségek](export-destinations.md) bővülő katalógusában, ahol az ügyféladatok használhat. Az adatok segítségével például kezelheti a promóciókat és kapcsolatba léphet a digitális marketing alkalmazásával.

1. Tekintse át az integrációs lehetőségeket, például más Dynamics 365-alkalmazásokban az [Ügyfélkártya bővítményt](customer-card-add-in.md).  


[!INCLUDE [footer-include](includes/footer-banner.md)]
