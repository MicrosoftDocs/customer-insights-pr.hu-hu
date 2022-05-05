---
title: Szolgáltatási korlátozások a Dynamics 365 Customer Insights szolgáltatásban
description: A korlátozásokkal és kikötésekkel kapcsolatos tudnivalók.
ms.date: 09/03/2021
ms.subservice: audience-insights
ms.topic: conceptual
author: JimsonChalissery
ms.author: jimsonc
ms.reviewer: mhart
manager: shellyha
ms.openlocfilehash: e2e7fc3033c25646693831d4c4c800d84ae6d6da
ms.sourcegitcommit: b7dbcd5627c2ebfbcfe65589991c159ba290d377
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/27/2022
ms.locfileid: "8641765"
---
# <a name="service-limits-in-customer-insights"></a>Szolgáltatási korlátok a Customer Insightsban

A cikk ismerteti a beépített korlátozásokat a Customer Insights szolgáltatásban, melyeknek a célja, hogy biztosítsa a szolgáltatás megbízhatóságát és stabilitását. A változtatásra vonatkozó kérelmeket az [Ötletfórumra](https://go.microsoft.com/fwlink/?linkid=2074172) nyújthatja be. 

## <a name="customer-insights"></a>Customer Insights

| Terület  | Korlátozások  | Megjegyzések |
|-------------|---------------------------------------------------------------------|---------------------------------------------------------------------|
| Szegmensek, mértékek és előrejelzések | 300  | A szegmensek, [mértékek](segments.md)[és](measures.md) előrejelzések [teljes száma](predictions.md) együttesen nem haladhatja meg a 300-at.  |
| Kapcsolatok | 20 mélységi szint az kapcsolatok elérési útjaiban. | A [szegmensek](segments.md) vagy [mértékek](measures.md) a szerkesztőfelület használatával való létrehozásakor az entitás elérési útjai a kezdő és a célentitás között legfeljebb 20 kapcsolati ugrást kaphatnak.  |


[!INCLUDE [footer-include](includes/footer-banner.md)]
