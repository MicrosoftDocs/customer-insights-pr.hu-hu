---
title: A szolgáltatás korlátozásai
description: A korlátozásokkal és kikötésekkel kapcsolatos tudnivalók.
ms.date: 07/08/2021
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: JimsonChalissery
ms.author: jimsonc
ms.reviewer: mhart
manager: shellyha
ms.openlocfilehash: 81253332cbea3110c0b3804db3a4d03b514f92d4
ms.sourcegitcommit: 9a99e48e96dfb3d895db428f37c30ae55eea66b7
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/14/2021
ms.locfileid: "6604372"
---
# <a name="service-limits-in-dynamics-365-customer-insights-audience-insights-capability"></a>Szolgáltatási korlátozások a Dynamics 365 Customer Insights célközönség információkban

A cikk ismerteti a beépített korlátozásokat a Customer Insights szolgáltatásban, melyeknek a célja, hogy biztosítsa a szolgáltatás megbízhatóságát és stabilitását. A változtatásra vonatkozó kérelmeket az [Ötletfórumra](https://go.microsoft.com/fwlink/?linkid=2074172) nyújthatja be. 
 
| Terület  | Korlátozások  | Megjegyzések |
|-------------|---------------------------------------------------------------------|---------------------------------------------------------------------|
| Szegmensek és intézkedések | 100 szegmens vagy mérték | Az aktív [szegmensek](segments.md) számának és a [mértékek](measures.md) számának összege nem haladhatja meg a 100-at.  |
| Kapcsolatok | 20 mélységi szint az kapcsolatok elérési útjaiban. | A [szegmensek](segments.md) vagy [mértékek](measures.md) a szerkesztőfelület használatával való létrehozásakor az entitás elérési útjai a kezdő és a célentitás között legfeljebb 20 kapcsolati ugrást kaphatnak.  |


[!INCLUDE[footer-include](../includes/footer-banner.md)]