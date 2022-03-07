---
title: Metrikák megtekintése és létrehozása
description: Metrikák létrehozása, szerkesztése és törlése.
ms.reviewer: mhart
ms.author: jusali
author: jusali
ms.date: 10/01/2021
ms.subservice: engagement-insights
ms.topic: how-to
ms.manager: shellyha
ms.openlocfilehash: 7e8c96f38af74f25080a40fd92e73f05c71320a8
ms.sourcegitcommit: e7cdf36a78a2b1dd2850183224d39c8dde46b26f
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/16/2022
ms.locfileid: "8229819"
---
# <a name="view-and-create-metrics"></a>Metrikák megtekintése és létrehozása

[!INCLUDE [cc-beta-prerelease-disclaimer](includes/cc-beta-prerelease-disclaimer.md)]

A metrikák segítenek megérteni a látogatók viselkedését. Összesítik az eseménytulajdonságokat, és mérik a statisztikákat és a webes tulajdonságok teljesítményét.  

Tegyük fel, hogy marketingpromóciót futtat a webhelyén. A metrikák segítségével nyomon követheti azoknak az egyedi látogatóknak vagy felhasználóknak a számát, akik a promóció során érkeztek a webhelyére. A metrikák elemzése segít jobban megérteni a webhely célközönségét. A metrikák és az [egyéni jelentés](custom-reports.md) [dimenzióinak](dimensions.md) kombinálása lehetővé teszi a viselkedés mérését a felhasználók megértéséhez. Például a látogatókat új és visszatérő kategóriákba sorolhatja, hogy azonosítsa a csoportok közötti érdeklődési és szándékbeli különbségeket.

## <a name="view-metrics"></a>Metrikák megtekintése

Az aktivitási információk az eseménytulajdonságok gyakran használt összesítését tartalmazzák rendszermutatóként: 

- Látogatók
- Látogatások
- Oldalmegtekintések
- Kattintások

Ezek a rendszermutatók az alapesemények meglévő eseménytulajdonságaira épülnek.

1. Válassza a bal navigációs ablaktáblán az **Adatok** elemet. 
1. Jelölje ki a **Metrikák** lapot a munkaterület összes metrikája listájának megtekintéséhez. 
   > [!NOTE]
   > A rendszer által generált metrikák csak olvashatók. A témák nem szerkeszthetők. Csak egyéni metrikákat hozhat létre és szerkeszthet.

## <a name="create-a-metric"></a>Metrika létrehozása

A környezet- és munkaterület-rendszergazdák hozhatnak létre metrikákat. A metrikák létrehozása előtt az esemény tulajdonságait el kell küldeni a munkaterületre. Létrehozhat metrikákat az alapesemények által küldött eseménytulajdonságok alapján, vagy a webes SDK segítségével [küldhet egyéni eseménytulajdonságokat](advanced-SDK-implementation.md).

1. Ugorjon az **Adatok** > **Metrikák** menübe.
1. Válassza az **Új mérőszám** lehetőséget az **Erőforrástár** és az **Új névtelen mérőszám** párbeszédpanel megnyitásához.

   :::image type="content" source="media/new-metric.png" alt-text="Metrika hozzáadása eseményhez.":::

1. Az **Új névtelen metrika** párbeszédpanelen válassza a **Formátum** legördülő listát, és válassza az **Egész szám** vagy a **Dupla** adattípust. Az Egész szám egy egész szám. Dupla értékként egy és három tizedesjegyet választhat.

   :::image type="content" source="media/create-new-metric.png" alt-text="Új metrika létrehozása.":::
   
5. Keresse meg az **Erőforrástár** ablaktáblában az esemény tulajdonságot, amely a metrika alapja.
6. Válassza ki a tulajdonság melletti **pluszjelet (+)** a képletben való használathoz. Csak egyetlen tulajdonság alapján hozhat létre képletet. 
7. Válasszon egyet a következők összesítő függvények közül. 

   - Összeg: az összes érték számtani összege 
   - Átlag: az összes érték átlaga
   - Számlálás: az értékek teljes száma
   - Egyedi értékek száma: az egyedi értékek teljes száma

   A metrika definiálása után a metrika műveleti előnézete látható az utolsó óráról.

1. Válassza a **Mentés** parancsot. 
1. Adja meg a metrika nevét, majd válassza a **Mentés** lehetőséget.

A metrika esetében percet is igénybe vehet, mire [egyéni jelentések létrehozására](custom-reports.md) használhatja.

## <a name="edit-a-metric"></a>Metrika szerkesztése

Csak az egyéni mérőszámok módosíthatók.

1. Ugorjon az **Adatok** > **Metrikák** menübe.
1. A listáról válassza ki a metrikát.
1. A metrika definíciójának módosítása
1. Válassza a **Mentés** parancsot.

## <a name="change-the-name-of-a-metric"></a>Egy metrika nevének megváltoztatása

Csak az egyéni metrika nevét lehet módosítani.

1. Ugorjon az **Adatok** > **Metrikák** menübe.
1. Válassza a **Továbbiak [...]** lehetőséget egy metrikához, majd válassza a **Név szerkesztése** lehetőséget.
1. A név módosítása. 
1. Válassza az **Átnevezés** lehetőséget.

## <a name="delete-a-metric"></a>Metrika törlése

Csak az egyéni mérőszámok törölhetők.

1. Ugorjon az **Adatok** > **Metrikák** menübe.
1. Válassza a **Továbbiak [...]** lehetőséget egy metrikánál, majd válassza a **Törlés** lehetőséget.

   :::image type="content" source="media/delete-metric.png" alt-text="Metrika törlése egy eseménytől.":::

1. Válassza ki az **Eltávolítás** lehetőséget a törlés megerősítéséhez.



[!INCLUDE[footer-include](../includes/footer-banner.md)]
