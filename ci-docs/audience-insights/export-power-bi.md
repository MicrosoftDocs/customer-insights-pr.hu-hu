---
title: Power BI-csatlakozó
description: Útmutató a Dynamics 365 Customer Insights összekötő használatához a Power BI megoldásban.
ms.date: 09/21/2020
ms.reviewer: sthe
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: d497ca779a337c512a7254524f597cff226bcb45
ms.sourcegitcommit: cf9b78559ca189d4c2086a66c879098d56c0377a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/03/2020
ms.locfileid: "4405983"
---
# <a name="connector-for-power-bi-preview"></a>Power BI összekötő (előzetes verzió)

Az adatokhoz vizuális megjelenítést hozhat létre a Power BI Desktoppal. További betekintést hozhat létre és jelentéseket készíthet az egyesített ügyfelek adataival.

## <a name="prerequisites"></a>Előfeltételek

- Az egyesített ügyfélprofilokkal rendelkezik.
- A számítógépen telepítve van a [Microsoft Power BI Desktop](https://powerbi.microsoft.com/desktop/) legújabb verziója . [További információk: Power BI Desktop](https://docs.microsoft.com/power-bi/desktop-what-is-desktop).

## <a name="configure-the-connector-for-power-bi"></a>Az összekötő beállítása a Power BI számára

1. A Power BI Desktop alkalmazásban válassza a **Fájl** > **Adatok lekérése** lehetőséget.

1. Válassza a **Továbbiak megtekintése** elemet, és keressen erre: **Dynamics 365 Customer Insights**

1. Jelölje ki az eredményt, és válassza a **Kapcsolódás** lehetőséget.

1. **Jelentkezzen be** ugyanazzal a szervezeti fiókkal, amelyet a Customer Insights esetében használ, és válassza a **Csatlakozás** lehetőséget.
   > [!NOTE]
   > Az ebben a lépésben megadott fiók az adatoknak a Customer Insights alkalmazásból történő beolvasására szolgál, és nem kell ugyanannak lennie, mint a Power BI-ba bejelentkezéskor. Az adatok beolvasásához használt partner alaphelyzetbe állításához nyissa meg a Power BI-t, és nyissa meg a **Fájl** > **Beállítások** > **Beállítások** > **Adatforrás beállításai**. Az adatforrások listájában válassza a **Dynamics 365 Customer Insights bejelentkezés** lehetőséget, és válassza az **engedélyek törlése** lehetőséget.  

1. A **Navigátor** párbeszédpanelen. megtekintheti az összes olyan környezet listáját, amelyhez hozzáféréssel rendelkezik. Bontson ki egy környezetet, és nyissa meg bármelyik mappát (entitások, intézkedések, szegmensek, bővítések). Nyissa meg például az **Entitások** mappát, és tekintse meg az összes importálható entitást.

   ![Power BI összekötő navigátor](media/power-bi-navigator.png "Power BI összekötő navigátor")

1. Jelölje be a szerepeltetni és betölteni kívánt entitások melletti jelölőnégyzeteket, és válassza a **Betöltés** elemet. Többe entitást is kiválaszthat több környezetből.

1. A betöltési párbeszédpanel jelenik meg az entitások betöltése közben. Ha az összes kijelölt entitás be van töltve, az adatok megjelenítéséhez használhatja a Power BI-lehetőségeket.

## <a name="large-data-sets"></a>Nagy adathalmazok

A Customer Insights Power BI-csatlakozója az egymillió ügyfélprofilig terjedő adatkészletek feldolgozására szolgál. A nagyobb adathalmazok importálása működhet, de hosszú időt igényel. Emellett a folyamat a Power BI-korlátozásai miatt időtúllépés is előfordulhat. További információkért lásd [Power BI: Nagyméretű adathalmazokra vonatkozó ajánlások](https://docs.microsoft.com/power-bi/admin/service-premium-what-is#large-datasets). 

### <a name="work-with-a-subset-of-data"></a>Munka az adatok egy részhalmazával

Érdemes lehet az adatok egy részhalmazával dolgozni. Létrehozhatók például olyan [szegmensek](segments.md), amelyek nem exportálják az összes ügyfélrekordot a Power BI-be.
