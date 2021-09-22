---
title: Az aktivitási információk szolgáltatás megismerésének első lépései
description: A gyors kezdéshez szükséges segédanyagok áttekintése.
ms.reviewer: mhart
ms.author: jefhar
author: mochimochi016
ms.date: 12/21/2020
ms.service: customer-insights
ms.subservice: engagement-insights
ms.topic: conceptual
ms.manager: shellyha
ms.custom: intro-internal
ms.openlocfilehash: 5ee1567cea834670a16aaa3253912b7957ce26b3
ms.sourcegitcommit: 86739a3f238162fc96837270b5d184e648fab15c
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/20/2021
ms.locfileid: "7405361"
---
# <a name="get-started-with-dynamics-365-customer-insights-engagement-insights-capability-public-preview"></a>Az Dynamics 365 Customer Insights aktivitási információk szolgáltatás (nyilvános előzetes verzió) megismerésének első lépései

[!INCLUDE [cc-beta-prerelease-disclaimer](includes/cc-beta-prerelease-disclaimer.md)]

Az aktivitási információk szolgáltatás segítségével összegyűjtheti és lemérheti az ügyfelek viselkedését a webhelyén. Ez a célközönség-információk szolgáltatással integrált, így az ügyfélprofil-jelentések mellett részletes, valós idejű viselkedéselemzéseket is kaphat. A cikkben található hivatkozások segítségével gyorsan konfigurálhatja és beállíthatja a környezetet.

## <a name="step-1-review-prerequisites"></a>1. lépés: Tekintse át az előfeltételeket

Aktív Microsoft Azure Active Directory-felhasználói fiókkal kell rendelkeznie. Ezután olvassa el a következő cikkeket az Engagements Insights munkaterületének beállítása előtt.

- Elolvastam és elfogadom a Microsoft [szolgáltatási feltételeket](terms-of-service.md).  
- Olvassa el [A cookie-k kezelése és a felhasználó beleegyezése](user-consent-storage.md) cikket. A cikk átnézése után ellenőrizze, hogy frissítenie kell-e a felhasználó beleegyezésével kapcsolatos értesítést. Ha korábban nem volt "nem lényeges" cookie, valószínűleg frissítenie kell a webhelyre vonatkozó irányelveit.
- Olvassa el a [szószedetet](glossary.md) a legfontosabb fogalmak rövid áttekintése érdekében.

## <a name="step-2-explore-engagement-insights"></a>2. lépés: Az aktivitási információk feltárására

Amikor első alkalommal meglátogatja az aktivitási információk szolgáltatást, konfigurálhatja a beállításokat, áttekintheti az irányelveket, és megismerheti a terméket.

1. Jelentkezzen be az [aktivitási információk szolgáltatás portálján](https://pi.dynamics.com) a Microsoft Azure Active Directory felhasználói fiókjával. (Ez lehet iskolai vagy munkahelyi fiók is.)

1. Válassza ki a régiót, és a jelölőnégyzet bejelölésével jelezze, hogy be szeretné-e fogadni e-mailben frissítéseket és ajánlatokat.

1. Tekintse át az **aktivitási információk (előzetes verzió) használati feltételeit** és **adatvédelmi nyilatkozatát**, majd válassza a **Demó megtekintése** lehetőséget az elfogadásukhoz.

1. Fedezze fel a terméket egy sor mintaadat segítségével.

##  <a name="step-3-set-up-a-workspace-and-add-code-to-your-website"></a>3. lépés: Munkaterület beállítása és kód hozzáadása a webhelyhez

A munkaterületen valós időben megtekintheti a felhasználói tevékenységeket, valamint tárolhatja és kezelheti a jelentéseket. Adja hozzá a kódot a webhelyhez az *események*, a felhasználóktól származó tevékenységadatok összegyűjtéséhez.

1. [Munkaterület létrehozása](create-workspace.md) és tagok hozzáadása.

1. [Adjon hozzá kódot webhelyéhez](instrument-website.md) vagy [mobilalkalmazásához](developer-resources.md#capture-events-from-mobile-apps) ,hogy lássa a munkaterületre érkező felhasználói tevékenységeket.

1. [Valós idejű jelentés](view-reports.md) megtekintése az aktív felhasználókat böngésző, eszköz, operációs rendszer, hely és nyelv szerint. Saját vizualizációk létrehozásához [egyéni jelentéseket](custom-reports.md) is létrehozhat.
    
## <a name="step-4-export-data-to-other-channels"></a>4. lépés: Adatok exportálása más csatornákba

Létrehozhat *eseményeket* (virtuális nézetet) a webelemzési adatokból. Ezután szűrje és exportálja az adatokat ide: Azure Data Lake Storage. Az exportált adatokat betöltheti importálási adatforrásként. További információkért lásd: [Hivatkozás létrehozása a célközönséggel kapcsolatos információk és az elkötelezettségi információk között](integrate-audience-insights-engagement-insights.md).

1. [Finomított események létrehozása](refined-events.md) exportálásra.

1. [Exportálja az adatokat](export-events.md) az Data Lake Storage-be.

1. Tekintse meg, hogyan [törölhet és exportálhat személyes adatokat tartalmazó eseményadatokat](delete-export-personal-data.md).
 
## <a name="step-5-stay-connected"></a>5. lépés: Kapcsolat fenntartása

Nagyra értékeljük az aktív részvételét, és megtervezhet minden releváns visszajelzést a jövőbeli kiadások fejlesztése során. Ossza meg visszajelzéseit, és számoljon be a problémákról a következő csatornák valamelyikével:
- [Közösség](https://go.microsoft.com/fwlink/?linkid=2141648)
- [Visszajelzés küldése](https://go.microsoft.com/fwlink/?linkid=2143222)
- [Támogatás kérése](https://go.microsoft.com/fwlink/?linkid=2145734) 


[!INCLUDE[footer-include](../includes/footer-banner.md)]
