---
title: Power Apps összekötő (előzetes verzió)
description: A Power Apps csatlakoztatása a Power Automate szolgáltatáshoz.
ms.date: 10/01/2021
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: Nils-2m
ms.author: nikeller
manager: shellyha
ms.openlocfilehash: 0b71f723d1e491d422d24b1be6616d2f33c95d40
ms.sourcegitcommit: a97d31a647a5d259140a1baaeef8c6ea10b8cbde
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/29/2022
ms.locfileid: "9055263"
---
# <a name="power-apps-connector-preview"></a>Power Apps összekötő (előzetes verzió)

Az egyesített ügyfélprofilokat beviheti a személyre szabott alkalmazásokba a Microsoft Power Apps segítségével.

## <a name="connect-power-apps-and-dynamics-365-customer-insights"></a>A Power Apps és a Dynamics 365 Customer Insights összekapcsolása

A Customer Insights az [adatok egyik elérhető forrása a Power Apps szolgáltatásban](/powerapps/maker/canvas-apps/working-with-data-sources).

A Power Apps dokumentációban megismerheti, hogyan [vehet fel adatkapcsolatot egy alkalmazásba](/powerapps/maker/canvas-apps/add-data-connection). Ajánlott azt is megvizsgálni, hogy a [Power Apps delegálás használata hogyan kezeli a nagyméretű adatkészleteket vászonalapú alkalmazásokban](/powerapps/maker/canvas-apps/delegation-overview).

## <a name="available-entities"></a>Elérhető entitások

A Customer Insights adatkapcsolatként való hozzáadása után kiválaszthatja a következő entitásokat a Power Apps szolgáltatásban:

- **Ügyfél**: az [egyesített ügyfélprofil](customer-profiles.md) adatainak használatához.
- **UnifiedActivity**: a [tevékenység ütemezésének](activities.md) megjelenítése az alkalmazásban.
- **ContactProfile**: az ügyfél kapcsolattartóinak megjelenítéséhez. Ez az entitás csak az üzleti fiókok Customer Insights-környezetében érhető el.

## <a name="limitations"></a>Korlátozások

### <a name="retrievable-entities"></a>Lekérhető entitások

Az **Ügyfél**, **UnifiedActivity**, **Szegmensek** és a **ContactProfile** entitások csak a Power Apps sszekötőn keresztül olvashatók be. A ContactProfile csak a Customer Insights-példányban érhető el üzleti fiókokhoz. Más entitások láthatók, mert az alapul szolgáló összekötő támogatja azokat eseményindítókkal a Power Automate-szolgáltatásban.

60 másodpercenként legfeljebb 100 hívást hajthat végre. Az API-t végpont többször is meghívhatja a $skip paraméter használatával. [További információ a $skip paraméterről](/connectors/customerinsights/#get-items-from-an-entity).

### <a name="delegation"></a>Meghatalmazás

A delegálás az **Ügyfél** entitáshoz és a **UnifiedActivity** entitáshoz használható. 

- Az **Ügyfél** entitásának delegálása: Az entitás delegálásának használatához a mezőket indexelni kell a [keresési & szűrő indexében](search-filter-index.md).  
- A **UnifiedActivity** delegálása: A delegálás ehhez az entitáshoz csak az **ActivityId** és a **CusomerId** mező esetében működik.  
- Delegálás a **ContactProfile** fájlhoz: Az entitásra vonatkozó delegálás csak a **ContactId** és a **CustomerId** mezőknél működik. A ContactProfile csak az üzleti fiókok Customer Insights-környezetében érhető el.

A delegálásról a delegálásra vonatkozó további információkért menjen a [Power Apps delegálható funkciókhoz és műveletekhez](/powerapps/maker/canvas-apps/delegation-overview). 

## <a name="example-gallery-control"></a>Példa a katalógusvezérlőre

Ügyfélprofilokat adhat hozzá egy [galériavezérlőhöz](/powerapps/maker/canvas-apps/add-gallery).

1. Adjon hozzá egy **katalógus** vezérlőt az épített alkalmazáshoz.

    > [!div class="mx-imgBorder"]
    > ![Katalóguselem hozzáadása.](media/connector-powerapps9.png "Katalóguselem hozzáadása.")

2. Válassza az **Ügyfél** elemet az elemek adatforrásaként.

    > [!div class="mx-imgBorder"]
    > ![Adatforrás kijelölése.](media/choose-datasource-powerapps.png "Adatforrás kijelölése.")

3. A jobb oldali adatpanelt megváltoztatva megadhatja, hogy az Ügyfél entitásnál melyik mező jelenjen meg a katalógusban.

4. Ha a kiválasutott ügyfélből a katalóguson bármely mezőt meg szeretné jeleníteni, töltse ki a címke **Szöveg** tulajdonságát a **{Name_of_the_gallery}.Selected.{property_name}** használatával  
    - Például: _Gallery1.Selected.address1_city_

5. Az ügyfélnél egységes idősor megjelenítéséhez adjon hozzá egy Katalógus elemet, és adja hozzá az **Elemek** tulajdonságot a **Filter('UnifiedActivity', CustomerId = {Customer_Id})** használatával  
    - Például: _Filter('UnifiedActivity', CustomerId = Gallery1.Selected.CustomerId)_


[!INCLUDE [footer-include](includes/footer-banner.md)]
