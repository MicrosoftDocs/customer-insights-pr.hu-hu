---
title: Az aktivitási információk szolgáltatás megismerésének első lépései
description: A gyors kezdéshez szükséges segédanyagok áttekintése.
ms.reviewer: mhart
ms.author: jefhar
author: mochimochi016
ms.date: 10/01/2021
ms.subservice: engagement-insights
ms.topic: conceptual
ms.manager: shellyha
ms.custom: intro-internal
ms.openlocfilehash: c435810e712bbbf69f8f1cfb582fc0a971566de6
ms.sourcegitcommit: e7cdf36a78a2b1dd2850183224d39c8dde46b26f
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/16/2022
ms.locfileid: "8225601"
---
# <a name="get-started-with-dynamics-365-customer-insights-engagement-insights-capability-public-preview"></a>Az Dynamics 365 Customer Insights aktivitási információk szolgáltatás (nyilvános előzetes verzió) megismerésének első lépései

[!INCLUDE [cc-beta-prerelease-disclaimer](includes/cc-beta-prerelease-disclaimer.md)]

Az aktivitási információk szolgáltatás segítségével összegyűjtheti és lemérheti az ügyfelek viselkedését a webhelyén. Ez a célközönség-információk szolgáltatással integrált, így az ügyfélprofil-jelentések mellett részletes, valós idejű viselkedéselemzéseket is kaphat. A cikkben található hivatkozások segítségével gyorsan konfigurálhatja és beállíthatja a környezetet.

## <a name="step-1-review-prerequisites"></a>1. lépés: Tekintse át az előfeltételeket

Először is Aktív Microsoft Azure Active Directory (AAD) felhasználói fiókkal kell rendelkeznie. Ezután olvassa el a következő cikkeket az Engagements Insights munkaterületének beállítása előtt.

- Elolvastam és elfogadom a Microsoft [szolgáltatási feltételeket](terms-of-service.md).  
- Olvassa el [A cookie-k kezelése és a felhasználó beleegyezése](user-consent-storage.md) cikket. Ezt követően döntse el, hogy frissítenie kell-e a felhasználó beleegyezésével kapcsolatos értesítést. Ha korábban nem volt "nem lényeges" cookie, valószínűleg frissítenie kell a webhelyre vonatkozó irányelveit.
- Olvassa el a [szószedetet](glossary.md) a legfontosabb fogalmak rövid áttekintése érdekében.

## <a name="step-2-explore-engagement-insights"></a>2. lépés: Az aktivitási információk feltárására

Amikor első alkalommal látogatja meg a célközönséggel kapcsolatosa információkat, konfigurálhatja a beállításokat, áttekintheti az irányelveket, és megismerheti a képességeket.

1. Jelentkezzen be az [elkötelezettségi információk szolgáltatási portáljára](https://home.ci.ai.dynamics.com/app/engagement-insights) a Microsoft AAD felhasználói (iskolai vagy munkahelyi) fiókjával.

1. Válassza ki a régiót, és jelölje be a jelölőnégyzetet, ha fel szeretné iratkozni e-mailben érkező frissítésekre és ajánlatokra.

1. Tekintse át az elkötelezettségi információk (előzetes verzió) **használati feltételeit** és az **Adatvédelmi nyilatkozatot**, majd válassza a **Fedezze fel a demót** lehetőséget, és fogadja el ezeket a beállításokat.

1. Fedezze fel a terméket egy sor mintaadat segítségével.

##  <a name="step-3-set-up-a-workspace-and-create-reports"></a>3. lépés: Munkaterület beállítása és jelentések létrehozása

A munkaterületen valós időben megtekinthetők a felhasználói tevékenységek, illetve tárolhatók és kezelhetők a jelentések. Adja hozzá a kódot a webhelyhez az *események*, a felhasználóktól származó tevékenységadatok összegyűjtéséhez.

1. [Munkaterület létrehozása](create-workspace.md) és tagok hozzáadása.

1. Adjon hozzá kódot [webhelyéhez](instrument-website.md) vagy [mobilalkalmazásához](developer-resources.md#capture-events-from-mobile-apps), hogy lássa a munkaterületre érkező felhasználói tevékenységeket.

1. Valós [idejű jelentés megtekintése](view-reports.md), amely az aktív felhasználókat böngésző, eszköz, operációs rendszer, hely és nyelv szerint jeleníti meg. Saját vizualizációk létrehozásához [egyéni jelentéseket](custom-reports.md) is létrehozhat.

1. Hozzon létre [méreteket](dimensions.md) a látogatók új és visszatérő felhasználók szerint való rendezése érdekében, a felhasználói viselkedés jobb érthetősége érdekében [mérőszámokat](metrics.md), illetve a látogatók részcsoportját a jellemzők vagy a webhely-kapcsolati tevékenységek alapján azonosító [szegmenseket](segments.md).
    
## <a name="step-4-export-data-to-other-channels"></a>4. lépés: Adatok exportálása más csatornákba

Létrehozhat *eseményeket* (virtuális nézetet) a webelemzési adatokból. Ezután szűrje és exportálja az adatokat ide: Azure Data Lake Storage. Az exportált adatokat betöltheti importálási adatforrásként.

1. [Finomított események létrehozása](refined-events.md) exportálásra.

1. [Az adatok exportálása](export-events.md) az Azure Data Lake Storage szolgáltatásba.

1. [Hozzon létre kapcsolatot a célközönséggel kapcsolatos információk és az elkötelezettségi információk](integrate-audience-insights-engagement-insights.md) között, hogy megossza az adatokat a két képesség között.

1. [A korábban hitelesített felhasználók webes eseményeinek felismerése](unknown-to-known.md) az **ismeretlenből ismert szolgáltatással**.

1. Tekintse meg, hogyan [törölhet és exportálhat személyes adatokat tartalmazó eseményadatokat](delete-export-personal-data.md).

## <a name="step-5-create-and-manage-funnel-reports"></a>5. lépés: Tölcsérjelentések létrehozása és kezelése

A tölcsérjelentés a webhelyen vagy mobilalkalmazáson keresztül ügyfélút információkat gyűjt a lépésekről. A használatra elérhető profiljelentések és egyéni jelentések létrehozása mellett tölcsérjelentést is létrehozhat, amely meghatározza, hogy az ügyfelek milyen útvonalat használnak a vásárlás előtt. 

1. [Hozzon létre egy tölcsérjelentést](funnel-reports.md), amely tájékoztatja a döntéseket, és azonosítja az optimalizálási és folyamatfejlesztésekkel kapcsolatos területeket.

1. Hozzon létre többcsatornás jelentéseket, ha már használatban van a mobilalkalmazás az elkötelezettségi elemzések [Android SDK](get-started-android.md) vagy [iOS SDK](get-started-ios.md) segítségével.

1. A [tölcsérelemzések](funnel-reports.md#funnel-insights) segítségével alaposan megismerheti az ügyfelek viselkedését a tölcsérjelentés lépéseivel kapcsolatosan.
 
## <a name="step-6-stay-connected"></a>6. lépés: Kapcsolat fenntartása

Nagyra értékeljük az aktív részvételét, és a jövőbeli kiadások fejlesztése során figyelembe vetünk minden releváns visszajelzést. Ossza meg visszajelzéseit, és számoljon be a problémákról a következő csatornák valamelyikével:
- [Közösség](https://go.microsoft.com/fwlink/?linkid=2141648)
- [Visszajelzés küldése](https://go.microsoft.com/fwlink/?linkid=2143222)
- [Támogatás kérése](https://go.microsoft.com/fwlink/?linkid=2145734) 


[!INCLUDE[footer-include](../includes/footer-banner.md)]
