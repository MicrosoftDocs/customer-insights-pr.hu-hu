---
title: Szolgáltatási korlátok a Customer Insights szolgáltatásban
description: Ismerje meg a Customer Insights SaaS-szolgáltatás korlátait és korlátozásait.
ms.date: 05/28/2022
ms.subservice: audience-insights
ms.topic: conceptual
author: JimsonChalissery
ms.author: jimsonc
ms.reviewer: mhart
manager: shellyha
ms.openlocfilehash: 6d1b761a5c9f67bfdc7c5b152132c618db3ea36a
ms.sourcegitcommit: 78ef22cd39a1ebd7525f96829cd79d95f34438b9
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/07/2022
ms.locfileid: "8940671"
---
# <a name="service-limits-in-customer-insights"></a>Szolgáltatási korlátok a Customer Insights szolgáltatásban

A cikk ismerteti a beépített korlátozásokat a Customer Insights szolgáltatásban, melyeknek a célja, hogy biztosítsa a szolgáltatás megbízhatóságát és stabilitását. A változtatásra vonatkozó kérelmeket az [Ötletfórumra](https://go.microsoft.com/fwlink/?linkid=2074172) nyújthatja be.

## <a name="customer-insights"></a>Customer Insights

| Terület  | Korlátozások  | Megjegyzések |
|-------------|---------------------------------------------------------------------|---------------------------------------------------------------------|
| Szegmensek, mértékek és előrejelzések | 300  | A szegmensek, [mértékek](segments.md)[és](measures.md) előrejelzések [együttes száma](predictions.md) nem haladhatja meg a 300-at.  |
| Kapcsolatok | 20 mélységi szint az kapcsolatok elérési útjaiban. | A [szegmensek](segments.md) vagy [mértékek](measures.md) a szerkesztőfelület használatával való létrehozásakor az entitás elérési útjai a kezdő és a célentitás között legfeljebb 20 kapcsolati ugrást kaphatnak.  |

## <a name="fair-scheduling-of-jobs"></a>A feladatok tisztességes ütemezése

A Customer Insights egy SaaS-szolgáltatás, amely megosztott Azure-erőforrásokat használ. Az ügyfelek általában változó intenzitású és eltérő ütemezésű számítási feladatokkal rendelkeznek. A mögöttes erőforrásokhoz való méltányos hozzáférés biztosítása érdekében gondoskodunk arról, hogy a rendszerfolyamatok végrehajtása tisztességes sorrendben történjen. A rendszerfolyamatok közé tartoznak például az adategyesítéssel, a szegmensfrissítésekkel vagy a mértékszámítással kapcsolatos feladatok. A tisztességes ütemezés megvédi Önt az erőforrások sorban állásától, ha a kért feladatok kiugrása következik be. Ugyanakkor a Customer Insights nem garantálja, hogy a várólistára kerülő összes feladat párhuzamosan lesz feldolgozva.

[!INCLUDE [footer-include](includes/footer-banner.md)]
