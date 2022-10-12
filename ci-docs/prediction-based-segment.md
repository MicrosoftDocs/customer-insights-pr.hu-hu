---
title: Szegmens létrehozása előrejelzés modell alapján
description: Szegmensek létrehozása egy előrejelzési modell kimeneti entitása alapján.
ms.date: 09/19/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: zacookmsft
ms.author: zacook
manager: shellyha
ms.openlocfilehash: ed9c6247a1f9148628dc9b5217484e98a576224e
ms.sourcegitcommit: be341cb69329e507f527409ac4636c18742777d2
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/30/2022
ms.locfileid: "9610423"
---
# <a name="create-a-segment-based-on-a-prediction-model-preview"></a>Szegmens létrehozása egy előrejelzési modell (előzetes verzió) alapján

Az előrejelzések eredményei néha csak az ügyfelek egy részhalmazára vonatkoznak. A javaslatok személyre szabásának növelése az előrejelzési modellek eredményeiből való szegmensek létrehozásával. Előfordulhat például, hogy konkrét javaslatokat szeretne adni egy adott szolgáltatástípust előnyben részesítő ügyfeleknek.

## <a name="prerequisites"></a>Előfeltételek

- Legalább [közreműködői engedély](permissions.md) a Customer Insightsban.

- A Customer Insightsban konfigurált termékjavaslat, tranzakciós lemorzsolódás, előfizetési lemorzsolódás, vagy ügyfél élettartamra vetített értékmodell. A különböző modellek beállításához tekintse át a követelményeket:

  - [Termékjavaslati modell](predict-product-recommendation.md)
  - [Előfizetési lemorzsolódás modellje](predict-subscription-churn.md)
  - [Tranzakciós lemorzsolódási modell](predict-transactional-churn.md)
  - [Ügyfél élettartamára levetített értékmodell](predict-customer-lifetime-value.md)

## <a name="create-a-customer-segment-based-on-predictions"></a>Ügyfélszegmens létrehozása előrejelzések alapján

1. Nyissa meg az **Intelligencia** > **Előrejelzések** menüt, és válassza ki a **Saját előrejelzések** lapot.

1. Válassza ki az áttekinteni kívánt modellt, majd válassza a Nézet **lehetőséget**.

1. Az eredmény lapon válassza a **Szegmens létrehozása** lehetőséget. Az eredmények oldallal kapcsolatos további tudnivalókat a modellt ismertető cikk tartalmaz.

   :::image type="content" source="media/prediction-create-segment.png" alt-text="Képernyőkép az előrejelzés eredményei oldalról, a Szegmensművelet létrehozása kiemelésével.":::

1. Hozzon létre egy új szegmenst a kiválasztott modell kimeneti entitásának attribútumai alapján. További információ: [Szegmensek létrehozása és kezelése](segments.md).

> [!TIP]
> A szegmensek **lapon is létrehozhat szegmenst egy előrejelzés modellhez az Új**, **majd a Létrehozás az** Intelligenciából **lehetőség kiválasztásával** > **·**. További információ: [Új szegmens létrehozása gyors szegmensekkel](segment-quick.md).

[!INCLUDE [footer-include](includes/footer-banner.md)]
