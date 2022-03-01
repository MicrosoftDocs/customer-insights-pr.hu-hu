---
title: Power Automate-összekötő | Microsoft Docs
description: Hozzon létre folyamatokat a Microsoft Power Automate alkalmazásból a Dynamics 365 Customer Insights szolgáltatásba.
ms.date: 08/03/2020
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
ms.reviewer: philk
manager: shellyha
ms.openlocfilehash: ffe92414365b0b777691a4a2d585100e4fbea591
ms.sourcegitcommit: cf9b78559ca189d4c2086a66c879098d56c0377a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/03/2020
ms.locfileid: "4405978"
---
# <a name="power-automate-connector-preview"></a>Power Automate összekötő (előzetes verzió)

Az adatok módosításakor automatikusan elindíthat meghatározott eseményeket, vagy az összetettebb folyamatokat közvetlenül a [Power Automate](https://flow.microsoft.com/) szolgáltatásban is kezelheti.

## <a name="power-automate-triggers"></a>Power Automate-eseményindítók

Számos eseményindító használható ismétlődő feladatok (például értesítések vagy speciálisabb műveletek) automatizálására szolgáló munkamenetek létrehozásához. 

- Az adatforrás frissítésének sikertelensége esetén aktiválódó eseményindító. 
- Az adatforrás sikeres frissítése esetén aktiválódó eseményindító.
- Egy szegmens küszöbértékének túllépésekor aktiválódó eseményindító. Az eseményindító csak a küszöbérték túllépésére korlátozott.
- Egy üzleti mérőszám küszöbértékének túllépésekor aktiválódó eseményindító. Az eseményindító csak a küszöbérték túllépésére korlátozott.
- Az (adatforrások, a szegmensek, az intézkedések,...) teljes frissítésének indítása.
- Eseményindító az egyesítési folyamat (Térkép, egyeztetés, összefésülés) frissítésének befejezése után.

[Eseményindítók konfigurálása a Power Automate alkalmazásban](https://flow.microsoft.com/connectors/shared_customerinsights/dynamics-365-customer-insights-connector/).

## <a name="power-automate-actions"></a>Power Automate-műveletek
A Power Automate-összekötő más műveleteket biztosít, mint az eseményindítók. További információ itt található: [Dynamics 365 Customer Insights Connector](https://docs.microsoft.com/connectors/customerinsights/).

## <a name="create-a-power-automate-flow-in-audience-insights"></a>Power Automate-folyamat létrehozása a célközönség-információkban

1. A célközönség információin belül nyissa meg a következőt: **Rendszergazda** > **Rendszer**.

1. A **Rendszer** oldalon válassza ki az **Állapot** lapot.

1. Az **adatforrások** területen válassza a **Folyamatok** lehetőséget, és válassza a **Folyamat létrehozása** lehetőséget a legördülő listából.
   > [!div class="mx-imgBorder"]
   > ![Power Automate-összekötő, amely a Folyamat létrehozása műveletet mutatja](media/power-automate-connector-create-flow.png "Power Automate-összekötő, amely a Folyamat létrehozása műveletet mutatja")

1. A Power Automate területen válassza ki az egyik elérhető eseményindítót, hogy létrehozza a kívánt folyamatot. Ha az első folyamatot hozza létre, akkor először hitelesítenie kell a Power Automate-összekötővel.
