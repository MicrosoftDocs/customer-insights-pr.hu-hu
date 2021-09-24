---
title: Első lépések a célközönséggel kapcsolatos információk szolgáltatással a Dynamics 365 Customer Insights alkalmazásban
description: A célközönségfel kapcsolatos információk segítenek ez erőforrásoknak a gyors indulásban.
ms.reviewer: mhart
ms.author: mhart
author: m-hartmann
ms.date: 08/31/2021
ms.service: customer-insights
ms.subservice: engagement-insights
ms.topic: conceptual
ms.manager: shellyha
ms.custom: intro-internal
ms.openlocfilehash: aaaf1848df175469d8af07754ac153b777781ffb
ms.sourcegitcommit: 971716c761871cee390519cacef617dac21ecd60
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/01/2021
ms.locfileid: "7466580"
---
# <a name="get-started-with-dynamics-365-customer-insights-audience-insights-capability"></a>Első lépések a Dynamics 365 Customer Insights célközönséggel kapcsolatos információk képességével

A Célközönség információk az ügyfelek mélyebb megértésében nyújt segítséget. A különböző tranzakciós, viselkedésbeli és megfigyelési forrásokból származó adatok összekapcsolhatók a 360 fokos ügyfélnézet létrehozásához. Ezekkel a betekintéssel ügyfélközpontú élményeket és folyamatokat támogathat. Az ügyféladatokat egyesítheti és megértheti, és kiaknázhatja a belőlük származó intelligens összefüggéseket és műveleteket.

## <a name="step-1-create-an-environment"></a>1. lépés: Környezet létrehozása

Első lépésként létre kell hozni egy környezetet, amelyben dolgozik majd. Ha a szervezet már megvásárolt egy licencet, akkor tekintse meg az [Első lépések fizetett előfizetéssel](get-started-paid.md) részt. Ha próbaidőszakra van szükség a célközönség információkhoz, akkor tekintse meg a [Próbakörnyezet beállítása](get-started-trial.md) részt. 

## <a name="step-2-explore-audience-insights"></a>2. lépés: Célközönséggel kapcsolatos információk felfedezése

Amikor első alkalommal jelentkezik be a célközönséggel kapcsolatosa információkba, konfigurálhatja a beállításokat, és megismerheti a terméket.

1. [Jelentkezzen be a célközönséggel kapcsolatos információkba](https://home.ci.ai.dynamics.com) Microsoft Azure Active Directory (AAD) felhasználói fiókjával.

1. [Módosítsa a környezetet](manage-environments.md#switch-environments) a bemutató adatok megtekintése és az [célközönséggel kapcsolatosinformációk felfedezése](home.md) érdekében.

##  <a name="step-3-ingest-unify-and-set-up-relationships-for-your-data"></a>3. lépés: Betöltés, egyesítés és a kapcsolatok beállítása adataihoz

Az egyesített profilok az adatokkal kapcsolatos információk és a műveletek alapjai. Különböző forrásokból származó adatok behozása és az adategyesítési folyamat futtatása a unified profilok kombinálása érdekében. Határozza meg a kapcsolatokat az entitások közötti, használja a bővítési funkciót, hogy információkat adjon a profilokhoz. 

1. Adatok betöltése többféle lehetőségből származó adatforrások létrehozásával. Válasszon a [Power Query-összekötők](connect-power-query.md), egy [Common Data Model mappa](connect-common-data-model.md) vagy a [Microsoft Dataverse](connect-common-data-service-lake.md) között. 

1. Futtassa az [adategyesítési folyamatot](data-unification.md), menjen végig a [leképezésen](map-entities.md), az [egyeztetésen](match-entities.md) és az [egyesítési](merge-entities.md) fázison.

1. Ismerkedjen meg a [rendszer által létrehozott entitásokkal](entities.md), és [hozzon létre kapcsolatok a betöltött entitások között](relationships.md).
    
## <a name="step-4-enhance-unified-profiles-with-predictions-activities-and-measures"></a>4. lépés: Az egyesített profilok bővítése előrejelzésekkel, tevékenységekkel és mértékekkel

A beállított egységes profilokkal bővítheti az adatokat, és tovább bővítheti az ezekből származó információkat.

1. Az [ügyféladatok gyarapítása](enrichment-hub.md) érdekében válasszon a bővítési szolgáltatók közül.

1. Az [előre telepített modellekkel](predictions-overview.md) megbecsülheti az elvándorlást vagy a várható bevételeket.

1. A [tevékenységeket konfigurálhatja](activities.md) a beöltött adatok alapján, és kronologikus idővonalon ábrázolhatja az ügyfelekkel való kommunikációt. 

1. Az üzleti célok és fő teljesítménymutatók megvalósításához [intézkedéseket hozhat létre](measures.md).
 
## <a name="step-5-create-segments-and-activate-data-through-various-export-options"></a>5. lépés: Szegmensek létrehozása és adatok aktiválása különféle exportálási lehetőségek segítségével

Most, hogy az adatok teljesek, és az ügyfelekre vonatkozó információk széles körét tartalmazzák, ideje, hogy megnézzük, hogyan lehet az adatokkal műveletet végrehajtani. 

1. [Hozzon létre szegmenseket](segments.md) ( az ügyfélkör részhalmazai) annak érdekében, hogy a tevékenységek a megcélzott ügyfelek szempontjából relevánsak legyenek.

1. Tallózhat az [exportálási lehetőségek](export-destinations.md) bővülő katalógusában, ahol az ügyféladatok használhat. Az adatok segítségével például kezelheti a promóciókat és kapcsolatba léphet a digitális marketing alkalmazásával.

1. Tekintse át az integrációs lehetőségeket, például a közvetlen kapcsolatot az [aktivitási információkhoz](../engagement-insights/integrate-audience-insights-engagement-insights.md) vagy más Dynamics 365 alkalmazásokhoz az [Ügyfélkártya bővítmény](customer-card-add-in.md) segítségével.  


[!INCLUDE[footer-include](../includes/footer-banner.md)]
