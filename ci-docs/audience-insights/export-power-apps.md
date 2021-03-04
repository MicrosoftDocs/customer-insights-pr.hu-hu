---
title: Power Apps-csatlakozó
description: A Power Apps csatlakoztatása a Power Automate szolgáltatáshoz.
ms.date: 01/19/2021
ms.reviewer: nikeller
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: 5a8bbb9a09218d54228589d43c21c8894680b56e
ms.sourcegitcommit: 139548f8a2d0f24d54c4a6c404a743eeeb8ef8e0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/15/2021
ms.locfileid: "5268919"
---
# <a name="microsoft-power-apps-connector-preview"></a>Microsoft Power Apps összekötő (előzetes verzió)

Az egyesített ügyfélprofilokat beviheti a személyre szabott alkalmazásokba a Power Apps segítségével.

## <a name="connect-power-apps-and-dynamics-365-customer-insights"></a>A Power Apps és a Dynamics 365 Customer Insights összekapcsolása

A Customer Insights az [adatok egyik elérhető forrása a Power Apps szolgáltatásban](https://docs.microsoft.com/powerapps/maker/canvas-apps/working-with-data-sources).

A Power Apps dokumentációban megismerheti, hogyan [vehet fel adatkapcsolatot egy alkalmazásba](https://docs.microsoft.com/powerapps/maker/canvas-apps/add-data-connection). Ajánlott azt is megvizsgálni, hogy a [Power Apps delegálás használata hogyan kezeli a nagyméretű adatkészleteket vászonalapú alkalmazásokban](https://docs.microsoft.com/powerapps/maker/canvas-apps/delegation-overview).

## <a name="available-entities"></a>Elérhető entitások

A Customer Insights adatkapcsolatként való hozzáadása után kiválaszthatja a következő entitásokat a Power Apps szolgáltatásban:

- Ügyfél: az [egyesített ügyfélprofil](customer-profiles.md) adatainak használatához.
- UnifiedActivity: a [tevékenységi idővonal](activities.md) megjelenítése az alkalmazásban.

## <a name="limitations"></a>Korlátozások

### <a name="retrievable-entities"></a>Lekérhető entitások

Az **Ügyfél**, **UnifiedActivity** és **Szegmensek** entitásokat csak a Power Apps-összekötőn keresztül tudja lekérni. Más entitások láthatók, mert az alapul szolgáló összekötő támogatja azokat eseményindítókkal a Power Automate-szolgáltatásban.  

### <a name="delegation"></a>Meghatalmazás

A delegálás az Ügyfél entitáshoz és a UnifiedActivity entitáshoz használható. 

- Az **Ügyfél** entitásának delegálása: Az entitás delegálásának használatához a mezőket indexelni kell a [keresési & szűrő indexében](search-filter-index.md).  

- A **UnifiedActivity** delegálása: A delegálás ehhez az entitáshoz csak az **ActivityId** és a **CusomerId** mező esetében működik.  

- A delegálással kapcsolatban további tudnivalókat a [Power Apps delegálható funkciók és műveletek](https://docs.microsoft.com/connectors/commondataservice/#power-apps-delegable-functions-and-operations-for-the-cds-for-apps) című rész tartalmaz. 

## <a name="example-gallery-control"></a>Példa a katalógusvezérlőre

Az ügyfelek profiljait például egy [galériavezérlőhöz](https://docs.microsoft.com/powerapps/maker/canvas-apps/add-gallery) adhatja hozzá.

1. Adjon hozzá egy **Katalógus** vezérlőt az épített alkalmazáshoz.

> [!div class="mx-imgBorder"]
> ![Katalóguselem hozzáadása](media/connector-powerapps9.png "Katalóguselem hozzáadása")

1. Válassza az **Ügyfél** elemet az elemek adatforrásaként.

    > [!div class="mx-imgBorder"]
    > ![Adatforrás kijelölése](media/choose-datasource-powerapps.png "Adatforrás kijelölése")

1. A jobb oldali adatpanelt megváltoztatva megadhatja, hogy az Ügyfél entitásnál melyik mező jelenjen meg a katalógusban.

1. Ha a kiválasutott ügyfélből a katalóguson bármely mezőt meg szeretné jeleníteni, töltse ki a címke Szöveg tulajdonságát: **{Name_of_the_gallery}.Selected.{property_name}**

    Példa: Gallery1.Selected.address1_city

1. Ha egy ügyfélnél egyesített idősort szeretne megjeleníteni, adjon hozzá egy Katalógus elemet, és az Elemek tulajdonságot: **Filter('UnifiedActivity', CustomerId = {Customer_Id})**

    Példa: Filter('UnifiedActivity', CustomerId = Gallery1.Selected.CustomerId)


[!INCLUDE[footer-include](../includes/footer-banner.md)]