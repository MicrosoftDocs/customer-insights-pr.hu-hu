---
title: Power Automate összekötő (előzetes verzió) | Microsoft Dokumentumok
description: Folyamatok létrehozása a Microsoft Power Automate rendszerben a Dynamics 365 Customer Insights szolgáltatásból.
ms.date: 07/25/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: f87bd6db7143294a264813f6c5c7d7963f303628
ms.sourcegitcommit: 594081c82ca385f7143b3416378533aaf2d6d0d3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/27/2022
ms.locfileid: "9196121"
---
# <a name="power-automate-connector-preview"></a>Power Automate összekötő (előzetes verzió)

Az adatok módosításakor automatikusan elindíthat meghatározott eseményeket, vagy az összetettebb folyamatokat közvetlenül a [Microsoft Power Automate](https://flow.microsoft.com/) szolgáltatásban is kezelheti.

## <a name="known-limitations"></a>Ismert korlátozások

- Legfeljebb 100 hívás 60 másodpercenként. [A $skip paraméterrel](/connectors/customerinsights/#get-items-from-an-entity) többször is meghívhatja az API-végpont.

## <a name="power-automate-triggers"></a>Power Automate-eseményindítók

Az eseményindítók segítségével felhőfolyamatokat hozhat létre, és automatizálhatja az ismétlődő feladatokat, például értesítéseket és speciális műveleteket. Akkor használjon eseményindítókat, ha:

- A adatforrás frissítése sikertelen.
- A adatforrás frissítés sikeres.
- Egy szegmensen átlépnek egy küszöbértéket. Az eseményindító csak a küszöbérték túllépésére korlátozott.
- Egy küszöbértéket átlépnek egy üzleti intézkedésnél. Csak a dimenzió nélküli üzleti mérőszámok támogatottak. Az eseményindító csak a küszöbérték túllépésére korlátozott.
- A teljes ütemezett frissítés befejeződött. Ez az eseményindító nem működik a manuálisan elindított frissítéseknél.
- Az egyesítési folyamat frissítése befejeződött.

[Konfiguráld a triggereket Power Automate.](https://flow.microsoft.com/connectors/shared_customerinsights/dynamics-365-customer-insights-connector/)

## <a name="power-automate-actions"></a>Power Automate-műveletek

A Power Automate-összekötő más műveleteket biztosít, mint az eseményindítók. További információ itt található: [Dynamics 365 Customer Insights Connector](/connectors/customerinsights/).

## <a name="create-a-power-automate-flow"></a>Power Automate-folyamat létrehozása

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. A **Power Automate** csempén válassza a **Beállítás** lehetőséget.

1. Megnyílik a Customer Insights-összekötő (előzetes verzió) a Power Automate szolgáltatásban. **Jelentkezzen be** a Power Automate-szolgáltatásba.

1. Válassza ki az egyik elérhető eseményindítót, és adjon hozzá további lépéseket az új folyamathoz. További információ: [Felhőfolyamat létrehozása a Power Automate-szolgáltatásban](/power-automate/get-started-logic-flow).

Példák a folyamatok használatára: 
- Ha az adatforrás frissítése sikertelen üzenet küldése a Microsoft Teams csatornára. 
- E-mail küldése az adattulajdonosoknak, ha egy szegmensre vonatkozó küszöbérték túllépésre kerül.

[!INCLUDE [footer-include](includes/footer-banner.md)]
