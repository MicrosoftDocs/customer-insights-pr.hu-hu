---
title: Power BI összekötő (előzetes verzió)
description: Útmutató a Dynamics 365 Customer Insights összekötő használatához a Power BI megoldásban.
ms.date: 07/25/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: stefanie-msft
ms.author: sthe
manager: shellyha
ms.openlocfilehash: 656a695b8b3f1ec2b5fbaad69feba7f1f0b73dee
ms.sourcegitcommit: 594081c82ca385f7143b3416378533aaf2d6d0d3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/27/2022
ms.locfileid: "9196673"
---
# <a name="power-bi-connector-preview"></a>Power BI összekötő (előzetes verzió)

Vizualizációkat hozhat létre az adatokhoz az Microsoft Power BI Asztallal. További betekintést hozhat létre és jelentéseket készíthet az egyesített ügyfelek adataival.

## <a name="prerequisites"></a>Előfeltételek

- Egyesített ügyfélprofilok.
- A [Microsoft Power BI Desktop](https://powerbi.microsoft.com/desktop/) legújabb verziója telepítve van a számítógépére. [További információk: Power BI Desktop](/power-bi/desktop-what-is-desktop).

## <a name="configure-the-connector-for-power-bi"></a>Az összekötő beállítása a Power BI számára

1. A Power BI Desktop alkalmazásban válassza a **Fájl** > **Adatok lekérése** lehetőséget.

1. Válassza a **Továbbiak megtekintése** elemet, és keressen erre: **Dynamics 365 Customer Insights**

1. Válassza a **Kapcsolódás** lehetőséget.

1. **Jelentkezzen be** ugyanazzal a szervezeti fiókkal, amelyet a Customer Insights esetében használ, és válassza a **Csatlakozás** lehetőséget.
   > [!NOTE]
   > Az ebben a lépésben megadott fiók az adatoknak a Customer Insights alkalmazásból történő beolvasására szolgál, és nem kell ugyanannak lennie, mint a Power BI-ba bejelentkezéskor. Az adatok beolvasásához használt partner alaphelyzetbe állításához nyissa meg a Power BI-t, és nyissa meg a **Fájl** > **Beállítások** > **Beállítások** > **Adatforrás beállításai**. Az adatforrások listájában válassza a **Dynamics 365 Customer Insights bejelentkezés** lehetőséget, és válassza az **engedélyek törlése** lehetőséget.  

1. **A Kezelő** párbeszédpanelen tekintse meg az összes olyan környezet listáját, amelyhez hozzáféréssel rendelkezik. Bontson ki egy környezetet, és nyissa meg bármelyik mappát (entitások, intézkedések, szegmensek, bővítések). Nyissa meg például az **Entitások** mappát, és tekintse meg az összes importálható entitást.

   :::image type="content" source="media/power-bi-navigator.png" alt-text="Power BI összekötő navigátor.":::

1. Jelölje be a szerepeltetni és betölteni kívánt entitások melletti jelölőnégyzeteket, és válassza a **Betöltés** elemet. Többe entitást is kiválaszthat több környezetből.

   Az entitások betöltése közben megjelenik egy betöltő párbeszédpanel. Miután az összes kiválasztott entitás betöltődött, használja az adatok megjelenítésének képességeit Power BI.

## <a name="large-data-sets"></a>Nagy adathalmazok

A Customer Insights Power BI-csatlakozója az egymillió ügyfélprofilig terjedő adatkészletek feldolgozására szolgál. A nagyobb adatkészletek importálása működhet, de sokáig tarthat, és a Power BI korlátozások miatt időtúllépést okozhat. További információkért lásd [Power BI: Nagyméretű adathalmazokra vonatkozó ajánlások](/power-bi/admin/service-premium-what-is#large-datasets).

### <a name="work-with-a-subset-of-data"></a>Munka az adatok egy részhalmazával

Érdemes lehet az adatok egy részhalmazával dolgozni. Hozzon létre [például szegmenseket](segments.md) ahelyett, hogy az összes vevőrekordot exportálná a következőbe: Power BI.

## <a name="troubleshooting"></a>Hibaelhárítás

### <a name="customer-insights-environment-doesnt-show-in-power-bi"></a>A Customer Insights környezet nem jelenik meg a Power BI alatt

Azok a környezetek, amelyek egynél [több kapcsolat](relationships.md) van definiálva két azonos entitás között a Customer Insightsban, nem lesznek elérhetők az Power BI összekötőben.

Azonosítsa és távolítsa el a duplikált kapcsolatok.

1. Lépjen az **Adatok** > **kapcsolatok** elemre azon a környezeten, amelyben Power BI hiányzik.
1. Duplikált kapcsolatok azonosítása:
   - Ellenőrizze, hogy egynél több kapcsolat van-e definiálva ugyanazon két entitás között.
   - Ellenőrizze, hogy két olyan entitás között van-e kapcsolat, amelyek egyaránt szerepelnek az egyesítési folyamatban. Az egyesítési folyamatban szereplő összes entitás között implicit kapcsolat van definiálva.
1. Távolítsa el az azonosított duplikált kapcsolatokat.

A duplikált kapcsolatok eltávolítását, próbálja meg újra konfigurálni az Power BI-összekötőt.

### <a name="errors-on-date-fields-when-loading-entities-in-power-bi-desktop"></a>Hibák a dátummezőkben az entitások betöltésekor a Power BI Desktopban

Ha olyan entitásokat tölt be, amelyek olyan dátumformátumú mezőket tartalmaznak, mint az MM/DD/ÉÉÉÉÉ, hibákat tapasztalhat a területi beállítások nem megfelelő formátumai miatt. Ez az eltérés akkor fordul elő, ha a Power BI Desktop fájl az angoltól (Egyesült Államok) eltérő területi beállításra van beállítva, mert a Customer Insights dátummezői amerikai formátumban vannak mentve.

A Power BI Desktop fájlnak egyetlen területi beállítása van, amelyet az adatok beolvasásakor alkalmaz a program. A dátumhibák [kijavításához állítsa be a . BPI fájl](/power-bi/fundamentals/supported-languages-countries-regions#choose-the-language-or-locale-of-power-bi-desktop) angolra (Egyesült Államok).

[!INCLUDE [footer-include](includes/footer-banner.md)]
