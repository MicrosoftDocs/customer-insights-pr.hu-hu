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
ms.openlocfilehash: 409792bc3f12fca451ef038e3300758bdf9ecf3b
ms.sourcegitcommit: b7dbcd5627c2ebfbcfe65589991c159ba290d377
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/27/2022
ms.locfileid: "8642819"
---
# <a name="power-automate-connector-preview"></a>Power Automate összekötő (előzetes verzió)

Az adatok módosításakor automatikusan elindíthat meghatározott eseményeket, vagy az összetettebb folyamatokat közvetlenül a [Power Automate](https://flow.microsoft.com/) szolgáltatásban is kezelheti.

## <a name="known-limitations"></a>Ismert korlátozások

- 60 másodpercenként legfeljebb 100 hívást hajthat végre. Az API-végpont többször is meghívhatja a $skip paraméterrel. [További információ a $skip paraméterről](/connectors/customerinsights/#get-items-from-an-entity).

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

1. Válassz a **Rendszergazda** > **Célok exportálása** lehetőséget.

1. A **Power Automate** csempén válassza a **Beállítás** lehetőséget.

1. Megnyílik a Customer Insights-összekötő (előzetes verzió) a Power Automate szolgáltatásban. **Jelentkezzen be** a Power Automate-szolgáltatásba.

1. Válassza ki az egyik elérhető eseményindítót, és adjon hozzá további lépéseket az új folyamathoz. További információ: [Felhőfolyamat létrehozása a Power Automate-szolgáltatásban](/power-automate/get-started-logic-flow).

Példák a folyamatok használatára: 
- Ha az adatforrás frissítése sikertelen üzenet küldése a Microsoft Teams csatornára. 
- E-mail küldése az adattulajdonosoknak, ha egy szegmensre vonatkozó küszöbérték túllépésre kerül.



[!INCLUDE [footer-include](includes/footer-banner.md)]
