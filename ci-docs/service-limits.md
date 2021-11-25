---
title: Szolgáltatási korlátok Dynamics 365 Customer Insights
description: A korlátozásokkal és kikötésekkel kapcsolatos tudnivalók.
ms.date: 09/03/2021
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: JimsonChalissery
ms.author: jimsonc
ms.reviewer: mhart
manager: shellyha
ms.openlocfilehash: eb25e050b8aa768e6e1d8d4c5adce6095cccc346
ms.sourcegitcommit: 31a9b531dacd3a6465b3030c704ff5c085b7e122
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/10/2021
ms.locfileid: "7791984"
---
# <a name="service-limits-in-customer-insights-capabilities"></a>Szolgáltatási korlátok a Customer Insights képességeiben

A cikk ismerteti a beépített korlátozásokat a Customer Insights szolgáltatásban, melyeknek a célja, hogy biztosítsa a szolgáltatás megbízhatóságát és stabilitását. A változtatásra vonatkozó kérelmeket az [Ötletfórumra](https://go.microsoft.com/fwlink/?linkid=2074172) nyújthatja be. 

## <a name="audience-insights"></a>Célközönséggel kapcsolatos információk

### <a name="service-limits-in-dynamics-365-customer-insights-audience-insights-capability"></a>Szolgáltatási korlátok Dynamics 365 Customer Insights célközönség elemzési képességben

| Terület  | Korlátozások  | Megjegyzések |
|-------------|---------------------------------------------------------------------|---------------------------------------------------------------------|
| Szegmensek, intézkedések és előrejelzések | 300  | A szegmensek, intézkedések és előrejelzések összesített száma [...](audience-insights/segments.md) nem [...](audience-insights/measures.md)[...](audience-insights/predictions.md) haladhatja meg a 300-at.  |
| Kapcsolatok | 20 mélységi szint az kapcsolatok elérési útjaiban. | A [szegmensek](audience-insights/segments.md) vagy [mértékek](audience-insights/measures.md) a szerkesztőfelület használatával való létrehozásakor az entitás elérési útjai a kezdő és a célentitás között legfeljebb 20 kapcsolati ugrást kaphatnak.  |


## <a name="engagement-insights"></a>Elkötelezettségi információk

### <a name="workspace-and-event-quotas"></a>Munkaterület és eseménykvóták

Az aktivitási információk egy nagyon méretezhető alkalmazás, amely másodpercenként több millió eseményt képes támogatni. Nyilvános előzetes verzió esetén az eseményeknek mennyiségi küszöbértékük van. A szervezeten belül a munkaterületek száma is korlátozott.

### <a name="engagement-insights-limits"></a>Aktivitási információk korlátozásai

- Munkaterületenként maximális eseménymennyiség = 100 esemény másodpercenként

- A munkaterületek maximális száma szervezetenként = 100

Ha az események túllépik a küszöbértéket, akkor adatvesztéshez vezethetnek a jelentésekben ezen események alapján. A [támogatási szolgálattól](https://go.microsoft.com/fwlink/?linkid=2145734) kérhet nagyobb mennyiségeket a határértékek túllépése előtt. Segítünk Önnek a mennyiségi növekedés meghatározásában és kérésének támogatásában.


[!INCLUDE[footer-include](includes/footer-banner.md)]
