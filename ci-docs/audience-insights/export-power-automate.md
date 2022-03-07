---
title: Power Automate-összekötő | Microsoft Docs
description: Folyamatok létrehozása a Microsoft Power Automate rendszerben a Dynamics 365 Customer Insights szolgáltatásból.
ms.date: 06/24/2021
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: dc9bbe22b7f10cf92f06cae18fbece9808b87dce
ms.sourcegitcommit: e7cdf36a78a2b1dd2850183224d39c8dde46b26f
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/16/2022
ms.locfileid: "8226717"
---
# <a name="power-automate-connector-preview"></a>Power Automate összekötő (előzetes verzió)

Az adatok módosításakor automatikusan elindíthat meghatározott eseményeket, vagy az összetettebb folyamatokat közvetlenül a [Power Automate](https://flow.microsoft.com/) szolgáltatásban is kezelheti.

## <a name="power-automate-triggers"></a>Power Automate-eseményindítók

Az eseményindítók segítségével felhőfolyamatokat hozhat létre, és automatizálhatja az ismétlődő feladatokat, például értesítéseket és speciális műveleteket. 

- Az adatforrás frissítésének sikertelensége esetén aktiválódó eseményindító. 
- Az adatforrás sikeres frissítése esetén aktiválódó eseményindító.
- Egy szegmens küszöbértékének túllépésekor aktiválódó eseményindító. Az eseményindító csak a küszöbérték túllépésére korlátozott.
- Egy üzleti mérőszám küszöbértékének túllépésekor aktiválódó eseményindító. Csak a dimenzió nélküli üzleti mérőszámok támogatottak. Az eseményindító csak a küszöbérték túllépésére korlátozott.
- Aktivál, amikor az (adatforrások, szegmensek, intézkedések,...) teljes frissítése befejeződött.
- Eseményindító az egyesítési folyamat (Térkép, egyeztetés, összefésülés) frissítésének befejezése után.

[Konfiguráld a triggereket Power Automate.](https://flow.microsoft.com/connectors/shared_customerinsights/dynamics-365-customer-insights-connector/)

## <a name="power-automate-actions"></a>Power Automate-műveletek

A Power Automate-összekötő más műveleteket biztosít, mint az eseményindítók. További információ itt található: [Dynamics 365 Customer Insights Connector](/connectors/customerinsights/).

## <a name="create-a-power-automate-flow"></a>Power Automate-folyamat létrehozása

1. A célközönség információin belül nyissa meg a következőt **Rendszergazda** > **Exportálási célhelyek**.

1. A **Power Automate** csempén válassza a **Beállítás** lehetőséget.

1. Megnyílik a Customer Insights-összekötő (előzetes verzió) a Power Automate szolgáltatásban. **Jelentkezzen be** a Power Automate-szolgáltatásba.

1. Válassza ki az egyik elérhető eseményindítót, és adjon hozzá további lépéseket az új folyamathoz. További információ: [Felhőfolyamat létrehozása a Power Automate-szolgáltatásban](/power-automate/get-started-logic-flow).

Példák a folyamatok használatára: 
- Ha az adatforrás frissítése sikertelen üzenet küldése a Microsoft Teams csatornára. 
- E-mail küldése az adattulajdonosoknak, ha egy szegmensre vonatkozó küszöbérték túllépésre kerül.



[!INCLUDE[footer-include](../includes/footer-banner.md)]
