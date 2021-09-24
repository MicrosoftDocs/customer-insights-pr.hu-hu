---
title: Szolgáltatási korlátozások a Dynamics 365 Customer Insights szolgáltatásban
description: A korlátozásokkal és kikötésekkel kapcsolatos tudnivalók.
ms.date: 09/03/2021
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: JimsonChalissery
ms.author: jimsonc
ms.reviewer: mhart
manager: shellyha
ms.openlocfilehash: eba7871faf304d5945191b5b9bc215243b4f8a05
ms.sourcegitcommit: 5704002484cdf85ebbcf4e7e4fd12470fd8e259f
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/08/2021
ms.locfileid: "7483675"
---
# <a name="service-limits-in-customer-insights-capabilities"></a>Szolgáltatási korlátok a Customer Insights képességeiben

A cikk ismerteti a beépített korlátozásokat a Customer Insights szolgáltatásban, melyeknek a célja, hogy biztosítsa a szolgáltatás megbízhatóságát és stabilitását. A változtatásra vonatkozó kérelmeket az [Ötletfórumra](https://go.microsoft.com/fwlink/?linkid=2074172) nyújthatja be. 

## <a name="audience-insights"></a>Célközönséggel kapcsolatos információk

### <a name="service-limits-in-dynamics-365-customer-insights-audience-insights-capability"></a>Szolgáltatási korlátozások a Dynamics 365 Customer Insights célközönség információkban

| Terület  | Korlátozások  | Megjegyzések |
|-------------|---------------------------------------------------------------------|---------------------------------------------------------------------|
| Szegmensek és intézkedések | 100 szegmens vagy mérték | Az aktív [szegmensek](audience-insights/segments.md) számának és a [mértékek](audience-insights/measures.md) számának összege nem haladhatja meg a 100-at.  |
| Kapcsolatok | 20 mélységi szint az kapcsolatok elérési útjaiban. | A [szegmensek](audience-insights/segments.md) vagy [mértékek](audience-insights/measures.md) a szerkesztőfelület használatával való létrehozásakor az entitás elérési útjai a kezdő és a célentitás között legfeljebb 20 kapcsolati ugrást kaphatnak.  |


## <a name="engagement-insights"></a>Elkötelezettségi információk

### <a name="workspace-and-event-quotas"></a>Munkaterület és eseménykvóták

Az aktivitási információk egy nagyon méretezhető alkalmazás, amely másodpercenként több millió eseményt képes támogatni. Nyilvános előzetes verzió esetén az eseményeknek mennyiségi küszöbértékük van. A szervezeten belül a munkaterületek száma is korlátozott.

### <a name="engagement-insights-limits"></a>Aktivitási információk korlátozásai

- Munkaterületenként maximális eseménymennyiség = 100 esemény másodpercenként

- A munkaterületek maximális száma szervezetenként = 100

Ha az események túllépik a küszöbértéket, akkor adatvesztéshez vezethetnek a jelentésekben ezen események alapján. A [támogatási szolgálattól](https://go.microsoft.com/fwlink/?linkid=2145734) kérhet nagyobb mennyiségeket a határértékek túllépése előtt. Segítünk Önnek a mennyiségi növekedés meghatározásában és kérésének támogatásában.


[!INCLUDE[footer-include](includes/footer-banner.md)]