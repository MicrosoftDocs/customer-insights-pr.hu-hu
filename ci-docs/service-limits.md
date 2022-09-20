---
title: Szolgáltatási korlátok a Customer Insights szolgáltatásban
description: Ismerje meg a Customer Insights SaaS-szolgáltatás korlátait és korlátozásait.
ms.date: 08/30/2022
ms.subservice: audience-insights
ms.topic: conceptual
author: JimsonChalissery
ms.author: jimsonc
ms.reviewer: mhart
manager: shellyha
ms.openlocfilehash: c3863b1a72fd92ddc87755699feda11371ec9214
ms.sourcegitcommit: dfba60e17ae6dc1e2e3830e6365e2c1f87230afd
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/09/2022
ms.locfileid: "9463222"
---
# <a name="service-limits-in-customer-insights"></a>Szolgáltatási korlátok a Customer Insights szolgáltatásban

 A Customer Insights beépített korlátokkal rendelkezik, amelyek célja a szolgáltatás megbízhatóságának és stabilitásának biztosítása. A változtatásra vonatkozó kérelmeket az [Ötletfórumra](https://go.microsoft.com/fwlink/?linkid=2074172) nyújthatja be.

## <a name="customer-insights"></a>Customer Insights

| Terület  | Korlátozások  | Megjegyzések |
|-------------|---------------------------------------------------------------------|---------------------------------------------------------------------|
| Szegmensek, mértékek és előrejelzések | 300  | A szegmensek, [mértékek](segments.md)[és](measures.md) előrejelzések [együttes száma](predictions-overview.md) nem haladhatja meg a 300-at.  |
| Kapcsolatok | 20 mélységi szint az kapcsolatok elérési útjaiban. | A [szegmensek](segments.md) vagy [mértékek](measures.md) a szerkesztőfelület használatával való létrehozásakor az entitás elérési útjai a kezdő és a célentitás között legfeljebb 20 kapcsolati ugrást kaphatnak.  |
|Adatok betöltése| Az adatforrások Power Query egyidejű kiértékelése korlátozott. | A Customer Insights ugyanazokkal [a frissítési korlátozásokkal rendelkezik, mint az adatfolyamok a PowerBI.com](/power-query/power-query-online-limits#refresh-limits). |

## <a name="fair-scheduling-of-jobs"></a>A feladatok tisztességes ütemezése

A Customer Insights egy SaaS-szolgáltatás, amely megosztott Azure-erőforrásokat használ. Az ügyfelek általában változó intenzitású és eltérő ütemezésű számítási feladatokkal rendelkeznek. A mögöttes erőforrásokhoz való méltányos hozzáférés biztosítása érdekében gondoskodunk arról, hogy a rendszerfolyamatok végrehajtása tisztességes sorrendben történjen. A rendszerfolyamatok közé tartoznak például az adategyesítéssel, a szegmensfrissítésekkel vagy a mértékszámítással kapcsolatos feladatok. A tisztességes ütemezés megvédi Önt az erőforrások sorban állásától, ha a kért feladatok kiugrása következik be. Ugyanakkor a Customer Insights nem garantálja, hogy a várólistára kerülő összes feladat párhuzamosan lesz feldolgozva.

[!INCLUDE [footer-include](includes/footer-banner.md)]
