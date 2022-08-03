---
title: Javasolt szegmensek tevékenység alapján (előzetes verzió)
description: A gépi tanulás segítségével új, érdekes szegmenseket találhat az ügyféltevékenység alapján.
ms.date: 05/11/2021
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: JimsonChalissery
ms.author: jimsonc
manager: shellyha
searchScope:
- ci-segment-suggestions
- customerInsights
ms.openlocfilehash: df4f5f4b5c9a3ad66d57a6b349e18a0d714aff62
ms.sourcegitcommit: 8a28e9458b857adf8e90e25e43b9bc422ebbb2cd
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/18/2022
ms.locfileid: "9170592"
---
# <a name="suggested-segments-based-on-activity-preview"></a>Javasolt szegmensek tevékenység alapján (előzetes verzió)

Az ügyfelek Customer Insightsba feltöltött tevékenységadatai alapján az ügyfelek érdekes szegmenseit fedezheti fel. Tevékenységadatok például a tranzakciók, az ügyfélszolgálati hívás időtartama, a vásárlások vagy a visszatérítések. A szegmensek javaslásához elemezni kell a tevékenységadatokat, a közelmúltbeli tevékenység, a gyakoriság és a pénzben megadott érték (vagy időtartam) alapján. Másik megoldásként létrehozhat [javasolt szegmenseket a mértékek tökéletesítéséhez vagy az attribútumokat befolyásoló részletek pontosabb megállapításához](suggested-segments.md).

:::image type="content" source="media/suggested-segments-tab.png" alt-text="A Javasolt szegmensek lap, tevékenységalapú és attribútumalapú szegmensekre vonatkozó javaslatokkal.":::

## <a name="categorize-customers-by-activity"></a>Ügyfelek kategorizálása tevékenység szerint

A Customer Insights [tevékenységadatai](activities.md) alapján az ügyfélcsoportokat tükröző javaslatokat tudunk készíteni:

- legaktívabb ügyfelek 
- a legtöbb vásárlást végrehajtó ügyfelek 
- a legnagyobb bevételt eredményező ügyfelek 
- az utóbbi időben nem aktív ügyfelek 
- ügyfelek, akik gyakran lépnek kapcsolatba a vállalkozással  

Ha kiskereskedelmi vállalkozása van, akkor meg tudja állapítani, hogy melyik ügyfelek generálják a legnagyobb bevételt, és kuponokkal jutalmazhatja őket. Esetleg megtalálhatja az eseti ügyfeleket, és felajánlhatja nekik, hogy vegyenek részt egy jutalmazási programban, így gyakrabban kereshetik meg az Ön vállalkozását.
Ha közegészségügyi ellátást nyújt, és célja az egyes betegek költségeinek minimalizálása, megpróbálhatja csökkenteni az ismétlődő látogatásokat azáltal, hogy a lehető legkevesebb látogatás során a lehető legjobb ellátást nyújtja. Ebben az esetben az a célja, hogy a látogatások gyakorisága alacsony legyen, és hogy minimálisra csökkentse az ismétlődő költségeket. Esetleg megkeresheti a páciensek azon szegmenseit, amelyek esetében gyakoriak a találkozók és magasak az ismétlődő költségek, majd elemezheti az ilyen eseteket, hogy javítani tudja az egyes személyeknek kínált kezeléseket.

## <a name="required-data"></a>Szükséges adatok

A javaslatokat a kiválasztott bemeneti adatok alapján hozza létre a rendszer.

- Ügyfélprofilok: Egy adott szegmens összes ügyfele vagy tagja.

- Időszak: Legutóbbi hónap, legutóbbi év vagy bármilyen egyéni időszak.

- Tevékenységtípus: Vásárlások, kiskereskedelmi tranzakciók, online tranzakciók, ügyféltámogatási esetek, előfizetések stb.  

- A tevékenységadatokat tartalmazó Customer Insights-entitás: A UnifiedActivity entitás vagy egy adott tevékenységhez tartozó entitás.

- Használandó dimenziók: Az üzleti igényektől függően közelmúltbeli tevékenység, gyakoriság vagy pénzbeli dimenzió.

## <a name="generate-suggested-segments"></a>Javasolt szegmensek létrehozása

1. Lépjen a Szegmensek **elemre,** és válassza a **Javaslatok (előnézet)** lapot.

1. Válassza az **Új javaslatok keresése**, majd **Az ügyfél viselkedésének megtekintése vagy előrejelzése** lehetőséget. Válassza a Start **gombot**.

   :::image type="content" source="media/suggested-segments-activity-wizard.png" alt-text="A konfigurációs varázsló első lépése tevékenységen alapuló javasolt szegmensnél.":::

1. Adja meg a szükséges bemeneti adatokat, és válassza a Tovább **lehetőséget**.

   - Ügyfelek kiválasztása: Az összes ügyfelet tartalmazza, vagy egy adott szegmenst.
   - Tevékenység kiválasztása: Adja meg a tevékenység típusát és a tevékenységet leíró entitásokat.
   - Beállítások: Állítsa be a figyelembe venni kívánt időszakot, a tényezőket a javaslatokhoz, és képezze le az attribútumokat.

1. Tekintse át a bemeneti adatokat, és válassza a **Futtatás** lehetőséget a modell futtatásához és a javaslatok létrehozásához.

Az ügyfélprofilok számától és a kijelölt tevékenységektől számától függően ez eltarthat néhány percig.

A javaslatok létrehozása után szűrheti őket a dimenzió vagy a legérdekesebbnek tartott érték szerint.

## <a name="manage-suggested-segments"></a>Javasolt szegmensek kezelése

Lépjen a Szegmensek **elemre,** és válassza a **Javaslatok (előnézet)** lapot. **A Tevékenységalapú javaslatok** szakaszban válasszon ki egy javasolt szegmenst a rendelkezésre álló műveletek megtekintéséhez.

- **Lásd a javaslatot**, hogy megtekinthesse az adott szegmens részleteit, például az egyes dimenziók kiterjedését a célcsoporthoz képest. Ezenkívül kiemeli a lehetséges tagok számát a szegmensben és a teljes ügyfelek közötti arányukat.
- **Hozzon létre szegmenst** a javasolt szegmensként való mentéséhez. Megjelenik a **Minden szegmens lapon,** és frissíthető [vagy törölhető](segments.md). A szegmens részletei nem módosíthatók. A javaslatok bemeneti feltételei azonban megváltoztathatóak, és eltérő javaslatok is létrehozhatóak.
- **Szerkessze a javaslatokat** a konfigurált attribútumok módosításához, amelyek felváltják az aktuális javaslatokat.
- **Frissítse a javaslatokat** a javaslatok frissítéséhez a konfigurált attribútumok megtartása mellett.

[!INCLUDE [footer-include](includes/footer-banner.md)]
