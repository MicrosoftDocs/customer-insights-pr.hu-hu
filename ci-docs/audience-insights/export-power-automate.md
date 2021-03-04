---
title: Power Automate-összekötő | Microsoft Docs
description: Hozzon létre folyamatokat a Microsoft Power Automate alkalmazásból a Dynamics 365 Customer Insights szolgáltatásba.
ms.date: 01/20/2021
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: m-hartmann
ms.author: mhart
ms.reviewer: philk
manager: shellyha
ms.openlocfilehash: fb1df4e9ab1f78300b8ec1f8dfdfbfbac0e71447
ms.sourcegitcommit: 139548f8a2d0f24d54c4a6c404a743eeeb8ef8e0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/15/2021
ms.locfileid: "5268827"
---
# <a name="power-automate-connector-preview"></a>Power Automate összekötő (előzetes verzió)

Az adatok módosításakor automatikusan elindíthat meghatározott eseményeket, vagy az összetettebb folyamatokat közvetlenül a [Power Automate](https://flow.microsoft.com/) szolgáltatásban is kezelheti.

## <a name="power-automate-triggers"></a>Power Automate-eseményindítók

Az eseményindítók segítségével felhőfolyamatokat hozhat létre, és automatizálhatja az ismétlődő feladatokat, például értesítéseket és speciális műveleteket. 

- Az adatforrás frissítésének sikertelensége esetén aktiválódó eseményindító. 
- Az adatforrás sikeres frissítése esetén aktiválódó eseményindító.
- Egy szegmens küszöbértékének túllépésekor aktiválódó eseményindító. Az eseményindító csak a küszöbérték túllépésére korlátozott.
- Egy üzleti mérőszám küszöbértékének túllépésekor aktiválódó eseményindító. Az eseményindító csak a küszöbérték túllépésére korlátozott.
- Az (adatforrások, a szegmensek, az intézkedések,...) teljes frissítésének indítása.
- Eseményindító az egyesítési folyamat (Térkép, egyeztetés, összefésülés) frissítésének befejezése után.

[Eseményindítók konfigurálása a Power Automate alkalmazásban](https://flow.microsoft.com/connectors/shared_customerinsights/dynamics-365-customer-insights-connector/).

## <a name="power-automate-actions"></a>Power Automate-műveletek
A Power Automate-összekötő más műveleteket biztosít, mint az eseményindítók. További információ itt található: [Dynamics 365 Customer Insights Connector](https://docs.microsoft.com/connectors/customerinsights/).

## <a name="create-a-power-automate-flow"></a>Power Automate-folyamat létrehozása

1. A célközönség információin belül nyissa meg a következőt **Rendszergazda** > **Exportálási célhelyek**.

1. A **Power Automate** csempén válassza a **Beállítás** lehetőséget.

1. Megnyílik a Customer Insights-összekötő (előzetes verzió) a Power Automate szolgáltatásban. **Jelentkezzen be** a Power Automate-szolgáltatásba.

1. Válassza ki az egyik elérhető eseményindítót, és adjon hozzá további lépéseket az új folyamathoz. További információ: [Felhőfolyamat létrehozása a Power Automate-szolgáltatásban](https://docs.microsoft.com/power-automate/get-started-logic-flow).

Példák a folyamatok használatára: 
- Ha az adatforrás frissítése sikertelen üzenet küldése a Microsoft Teams csatornára. 
- E-mail küldése az adattulajdonosoknak, ha egy szegmensre vonatkozó küszöbérték túllépésre kerül.



[!INCLUDE[footer-include](../includes/footer-banner.md)]