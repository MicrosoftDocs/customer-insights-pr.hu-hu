---
title: Power Apps-csatlakozó
description: A Power Apps csatlakoztatása a Power Automate szolgáltatáshoz.
ms.date: 10/01/2021
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: Nils-2m
ms.author: nikeller
manager: shellyha
ms.openlocfilehash: ae2a3b7c05e9ed860da31853c47af2aec8634e7a
ms.sourcegitcommit: e7cdf36a78a2b1dd2850183224d39c8dde46b26f
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/16/2022
ms.locfileid: "8229034"
---
# <a name="microsoft-power-apps-connector-preview"></a>Microsoft Power Apps összekötő (előzetes verzió)

Az egyesített ügyfélprofilokat beviheti a személyre szabott alkalmazásokba a Power Apps segítségével.

## <a name="connect-power-apps-and-dynamics-365-customer-insights"></a>A Power Apps és a Dynamics 365 Customer Insights összekapcsolása

A Customer Insights az [adatok egyik elérhető forrása a Power Apps szolgáltatásban](/powerapps/maker/canvas-apps/working-with-data-sources).

A Power Apps dokumentációban megismerheti, hogyan [vehet fel adatkapcsolatot egy alkalmazásba](/powerapps/maker/canvas-apps/add-data-connection). Ajánlott azt is megvizsgálni, hogy a [Power Apps delegálás használata hogyan kezeli a nagyméretű adatkészleteket vászonalapú alkalmazásokban](/powerapps/maker/canvas-apps/delegation-overview).

## <a name="available-entities"></a>Elérhető entitások

A Customer Insights adatkapcsolatként való hozzáadása után kiválaszthatja a következő entitásokat a Power Apps szolgáltatásban:

- **Ügyfél**: az [egyesített ügyfélprofil](customer-profiles.md) adatainak használatához.
- **UnifiedActivity**: a [tevékenység ütemezésének](activities.md) megjelenítése az alkalmazásban.
- **ContactProfile**: az ügyfél kapcsolattartóinak megjelenítéséhez. Ez az entitás csak az ügyfelekkel kapcsolatos információk környezetben érhető el az üzleti partnereknek.

## <a name="limitations"></a>Korlátozások

### <a name="retrievable-entities"></a>Lekérhető entitások

Az **Ügyfél**, **UnifiedActivity**, **Szegmensek** és a **ContactProfile** entitások csak a Power Apps sszekötőn keresztül olvashatók be. A ContactProfile csak az ügyfelekkel kapcsolatos információk páldányban érhető el az üzleti partnereknek. Más entitások láthatók, mert az alapul szolgáló összekötő támogatja azokat eseményindítókkal a Power Automate-szolgáltatásban.

### <a name="delegation"></a>Meghatalmazás

A delegálás az **Ügyfél** entitáshoz és a **UnifiedActivity** entitáshoz használható. 

- Az **Ügyfél** entitásának delegálása: Az entitás delegálásának használatához a mezőket indexelni kell a [keresési & szűrő indexében](search-filter-index.md).  
- A **UnifiedActivity** delegálása: A delegálás ehhez az entitáshoz csak az **ActivityId** és a **CusomerId** mező esetében működik.  
- Delegálás a **ContactProfile** fájlhoz: Az entitásra vonatkozó delegálás csak a **ContactId** és a **CustomerId** mezőknél működik. A ContactProfile csak az ügyfelekkel kapcsolatos információk környezeteiben érhető el az üzleti partnereknek.

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


[!INCLUDE[footer-include](../includes/footer-banner.md)]
