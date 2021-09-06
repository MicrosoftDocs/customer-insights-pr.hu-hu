---
title: Tevékenység alapján javasolt szegmensek.
description: A gépi tanulás segítségével új, érdekes szegmenseket találhat az ügyféltevékenység alapján.
ms.date: 05/11/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: JimsonChalissery
ms.author: jimsonc
manager: shellyha
ms.openlocfilehash: 46e8970f7fd116cb1654c94751923ce2a213ff87dd7bc7ee731a62bbd0093513
ms.sourcegitcommit: aa0cfbf6240a9f560e3131bdec63e051a8786dd4
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/10/2021
ms.locfileid: "7028409"
---
# <a name="suggested-segments-based-on-activity-data-preview"></a>Tevékenységadatok alapján javasolt szegmensek (előzetes verzió)

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
Ha nyilvános egészségügyi szolgáltatást nyújt, és minimálisra szeretné csökkenteni az egyes betegek költségeit. Ennek egyik módja lehet az ismétlődő látogatások számának csökkentése azzal, hogy a lehető legkevesebb látogatás során a lehető legjobb ellátást biztosítja. Ebben az esetben az a célja, hogy a látogatások gyakorisága alacsony legyen, és hogy minimálisra csökkentse az ismétlődő költségeket. Esetleg megkeresheti a páciensek azon szegmenseit, amelyek esetében gyakoriak a találkozók és magasak az ismétlődő költségek, majd elemezheti az ilyen eseteket, hogy javítani tudja az egyes személyeknek kínált kezeléseket. 

## <a name="required-data"></a>Szükséges adatok

A javaslatokat a kiválasztott bemeneti adatok alapján hozza létre a rendszer. 

- Ügyfélprofilok: Egy adott szegmens összes ügyfele vagy tagja. 

- Időszak: Legutóbbi hónap, legutóbbi év vagy bármilyen egyéni időszak.

- Tevékenységtípus: Vásárlások, kiskereskedelmi tranzakciók, online tranzakciók, ügyféltámogatási esetek, előfizetések stb.  

- A tevékenységadatokat tartalmazó Customer Insights-entitás: A UnifiedActivity entitás vagy egy adott tevékenységhez tartozó entitás. 

- Használandó dimenziók: Az üzleti igényektől függően közelmúltbeli tevékenység, gyakoriság vagy pénzbeli dimenzió.

## <a name="generate-suggested-segments"></a>Javasolt szegmensek létrehozása

1. Kattintson a **Szegmensek** lehetőségre.

1. Válassza a **Javaslatok (előzetes verzió)** fület.

1. Válassza az **Új javaslatok keresése**, majd **Az ügyfél viselkedésének megtekintése vagy előrejelzése** lehetőséget. Az irányított élmény futtatásához válassza az **Indítás** lehetőséget.

   :::image type="content" source="media/suggested-segments-activity-wizard.png" alt-text="A konfigurációs varázsló első lépése tevékenységen alapuló javasolt szegmensnél.":::

1. Adja meg a szükséges bemeneti adatokat, és válassza a **Tovább** lehetőséget.

   - Ügyfelek kiválasztása: Az összes ügyfelet tartalmazza, vagy egy adott szegmenst.
   - Tevékenység kiválasztása: Adja meg a tevékenység típusát és a tevékenységet leíró entitásokat.
   - Beállítások: Állítsa be a figyelembe venni kívánt időszakot, a tényezőket a javaslatokhoz, és képezze le az attribútumokat.

1. Tekintse át a bemeneti adatokat, és válassza a **Futtatás** lehetőséget a modell futtatásához és a javaslatok létrehozásához.

1. Az ügyfélprofilok számától és a kijelölt tevékenységektől számától függően ez eltarthat néhány percig. 

A javaslatok létrehozása után szűrheti őket a dimenzió vagy a legérdekesebbnek tartott érték szerint. 

## <a name="view-details-of-a-suggested-segment"></a>Javasolt szegmens részleteinek megtekintése

A létrehozott javaslatok a **Szegmensek** > **Javaslatok (előzetes verzió)** részen, a **Tevékenységalapú javaslatok** szakaszban láthatók.

:::image type="content" source="media/suggested-segments-details.png" alt-text="Egy javasolt szegmens részletes adatait mutató kibontott oldalpanel.":::

Az adott szegmens részleteinek megtekintéséhez válassza a **Javaslat megtekintése** lehetőséget egy javasolt szegmensnél. Az oldalpanel olyan adatokat tartalmaz, mint például az egyes dimenziók célcsoporthoz viszonyított mérete. Ezenkívül kiemeli a lehetséges tagok számát a szegmensben és a teljes ügyfelek közötti arányukat. Ha a javaslatot meg szeretné tartani szegmensként, válassza a **Szegmens létrehozása** lehetőséget.    

## <a name="save-a-suggestion-as-a-segment"></a>Javaslat mentése szegmensként

1. Ugorjon a **Szegmensek** > **Javaslatok (előzetes verzió)** pontra.

1. Válassza ki a menteni kívánt szegmenst. 

1. Az oldalpanelen válassza a **Szegmens létrehozása** lehetőséget. 

1. A mentett szegmens megjelenik a **Minden szegmens** lapon lévő szegmenslistán. Most már [frissíthető és törölhetők, mint bármelyik más szegmens](segments.md). A szegmens részletei nem módosíthatók. A javaslatok bemeneti feltételei azonban megváltoztathatóak, és eltérő javaslatok is létrehozhatóak.

## <a name="refresh-or-edit-a-set-of-suggestions"></a>Javaslatok készletének frissítése és szerkesztése

1. Lépjen a **Szegmensek** > **Javaslatok (előzetes verzió)** részre, és keresse meg a szegmenst a **Tevékenységalapú javaslatok** szakaszban.

1. Válassza a **Javaslatok frissítése** lehetőséget, a javaslatokat frissítéséhez, miközben a konfigurált attribútumokat megtartja. Egy másik megoldás, hogy a **Javaslatok szerkesztése** lehetőséggel módosítja a konfigurált attribútumokat. A rendszer újrafuttatja a folyamatot, a legújabb adatok alapján szegmensjavaslatokat generál, és lecseréli az aktuális javaslatokat.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
