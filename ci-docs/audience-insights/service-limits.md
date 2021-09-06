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
ms.openlocfilehash: 2966f2ede1ddbe0245471771365cbf5b593be608764aa10ed28d962c52bb8067
ms.sourcegitcommit: aa0cfbf6240a9f560e3131bdec63e051a8786dd4
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/10/2021
ms.locfileid: "7034867"
---
# <a name="service-limits-in-dynamics-365-customer-insights-audience-insights-capability"></a>Szolgáltatási korlátozások a Dynamics 365 Customer Insights célközönség információkban

A cikk ismerteti a beépített korlátozásokat a Customer Insights szolgáltatásban, melyeknek a célja, hogy biztosítsa a szolgáltatás megbízhatóságát és stabilitását. A változtatásra vonatkozó kérelmeket az [Ötletfórumra](https://go.microsoft.com/fwlink/?linkid=2074172) nyújthatja be. 
 
| Terület  | Korlátozások  | Megjegyzések |
|-------------|---------------------------------------------------------------------|---------------------------------------------------------------------|
| Szegmensek és intézkedések | 100 szegmens vagy mérték | Az aktív [szegmensek](segments.md) számának és a [mértékek](measures.md) számának összege nem haladhatja meg a 100-at.  |
| Kapcsolatok | 20 mélységi szint az kapcsolatok elérési útjaiban. | A [szegmensek](segments.md) vagy [mértékek](measures.md) a szerkesztőfelület használatával való létrehozásakor az entitás elérési útjai a kezdő és a célentitás között legfeljebb 20 kapcsolati ugrást kaphatnak.  |


[!INCLUDE[footer-include](../includes/footer-banner.md)]