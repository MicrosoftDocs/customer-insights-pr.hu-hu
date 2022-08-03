---
title: Power Apps összekötő (előzetes verzió)
description: A Power Apps csatlakoztatása a Power Automate szolgáltatáshoz.
ms.date: 07/25/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: Nils-2m
ms.author: nikeller
manager: shellyha
ms.openlocfilehash: 8807e82e65ea20d1a7f7dc07552229f377927eed
ms.sourcegitcommit: 594081c82ca385f7143b3416378533aaf2d6d0d3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/27/2022
ms.locfileid: "9196903"
---
# <a name="power-apps-connector-preview"></a>Power Apps összekötő (előzetes verzió)

Az egyesített ügyfélprofilokat beviheti a személyre szabott alkalmazásokba a Microsoft Power Apps segítségével.

## <a name="connect-power-apps-and-dynamics-365-customer-insights"></a>A Power Apps és a Dynamics 365 Customer Insights összekapcsolása

A Customer Insights az [adatok egyik elérhető forrása a Power Apps szolgáltatásban](/powerapps/maker/canvas-apps/working-with-data-sources).

A Power Apps dokumentációban megismerheti, hogyan [vehet fel adatkapcsolatot egy alkalmazásba](/powerapps/maker/canvas-apps/add-data-connection). Ajánlott azt is megvizsgálni, hogy a [Power Apps delegálás használata hogyan kezeli a nagyméretű adatkészleteket vászonalapú alkalmazásokban](/powerapps/maker/canvas-apps/delegation-overview).

## <a name="available-entities"></a>Elérhető entitások

Miután hozzáadta a Customer Insights-t adatkapcsolatként, válassza ki a következő entitásokat a következőben Power Apps:

- **Ügyfél**: az [egyesített ügyfélprofil](customer-profiles.md) adatainak használatához.
- **UnifiedActivity**: a [tevékenység ütemezésének](activities.md) megjelenítése az alkalmazásban.
- **ContactProfile**: az ügyfél kapcsolattartóinak megjelenítéséhez. Ez az entitás csak az üzleti fiókok Customer Insights-környezetében érhető el.

## <a name="limitations"></a>Korlátozások

### <a name="retrievable-entities"></a>Lekérhető entitások

Az **Ügyfél**, **UnifiedActivity**, **Szegmensek** és a **ContactProfile** entitások csak a Power Apps sszekötőn keresztül olvashatók be. A ContactProfile csak az üzleti fiókok Customer Insights-környezetében érhető el. Más entitások láthatók, mert az alapul szolgáló összekötő támogatja azokat eseményindítókkal a Power Automate-szolgáltatásban.

60 másodpercenként legfeljebb 100 hívást hajthat végre. Az API-t végpont többször is meghívhatja a $skip paraméter használatával. [További információ a $skip paraméterről](/connectors/customerinsights/#get-items-from-an-entity).

### <a name="delegation"></a>Meghatalmazás

A delegálás az **Ügyfél** entitáshoz és a **UnifiedActivity** entitáshoz használható.

- Delegálás vevői entitáshoz **: Ahhoz, hogy delegálást használjon ehhez az entitáshoz, a mezőket indexelni kell a keresési &szűrési indexben**.[...](search-filter-index.md)  
- A **UnifiedActivity** delegálása: A delegálás ehhez az entitáshoz csak az **ActivityId** és a **CusomerId** mező esetében működik.  
- Delegálás a **ContactProfile** fájlhoz: Az entitásra vonatkozó delegálás csak a **ContactId** és a **CustomerId** mezőknél működik. A ContactProfile csak az üzleti fiókok Customer Insights-környezetében érhető el.

A delegálásról a delegálásra vonatkozó további információkért menjen a [Power Apps delegálható funkciókhoz és műveletekhez](/powerapps/maker/canvas-apps/delegation-overview).

## <a name="example-gallery-control"></a>Példa a katalógusvezérlőre

Igény szerint ügyfélprofilokat is hozzáadhat egy [katalógusvezérlőhöz](/powerapps/maker/canvas-apps/add-gallery).

1. Adjon hozzá egy **katalógus** vezérlőt az épített alkalmazáshoz.
  
   :::image type="content" source="media/connector-powerapps9.png" alt-text="Katalóguselem hozzáadása.":::

1. Válassza az **Ügyfél** elemet az elemek adatforrásaként.

   :::image type="content" source="media/choose-datasource-powerapps.png" alt-text="Adatforrás kijelölése.":::

1. Módosítsa a jobb oldali adatpanelt, és válassza ki, hogy az Ügyfél entitás melyik mezőt jelenítse meg a katalógusban.

1. Ha a kiválasutott ügyfélből a katalóguson bármely mezőt meg szeretné jeleníteni, töltse ki a címke **Szöveg** tulajdonságát a **{Name_of_the_gallery}.Selected.{property_name}** használatával  
    - Például: _Gallery1.Selected.address1_city_

1. Az ügyfélnél egységes idősor megjelenítéséhez adjon hozzá egy Katalógus elemet, és adja hozzá az **Elemek** tulajdonságot a **Filter('UnifiedActivity', CustomerId = {Customer_Id})** használatával  
    - Például: _Filter('UnifiedActivity', CustomerId = Gallery1.Selected.CustomerId)_

[!INCLUDE [footer-include](includes/footer-banner.md)]
