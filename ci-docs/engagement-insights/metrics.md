---
title: Metrikák megtekintése és létrehozása
description: Metrikák létrehozása, szerkesztése és törlése.
ms.reviewer: mhart
ms.author: jusali
author: jusali
ms.date: 06/09/2021
ms.service: customer-insights
ms.subservice: engagement-insights
ms.topic: how-to
ms.manager: shellyha
ms.openlocfilehash: 97189168e0f5586aad8be8089a1f9e27893c2115c7e805ddaab1efc00e11b860
ms.sourcegitcommit: aa0cfbf6240a9f560e3131bdec63e051a8786dd4
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/10/2021
ms.locfileid: "7034272"
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
   > A rendszer által generált metrikák csak olvashatók. Ezeket nem módosíthatja és nem törölheti. Csak egyéni metrikákat hozhat létre és szerkeszthet.

## <a name="create-a-metric"></a>Metrika létrehozása

A környezet- és munkaterület-rendszergazdák hozhatnak létre metrikákat. A metrikák létrehozása előtt az esemény tulajdonságait el kell küldeni a munkaterületre. Létrehozhat metrikákat az alapesemények által küldött eseménytulajdonságok alapján, vagy a webes SDK segítségével [küldhet egyéni eseménytulajdonságokat](advanced-SDK-implementation.md).

1. Ugorjon az **Adatok** > **Metrikák** menübe.
1. Válassz az **Új metrika** lehetőséget.

   :::image type="content" source="media/new-metric.png" alt-text="Metrika hozzáadása eseményhez.":::

1. A formátum beállításának válassza az **Egész** vagy a **Dupla** adattípust. Az Egész szám egy egész szám. Dupla esetében egy–három tizedesjegyet választhat.
1. Keresse meg az **Erőforrástár** ablaktáblában az esemény tulajdonságot, amely a metrika alapja.
1. Válassza ki a tulajdonság melletti **pluszjelet (+)** a képletben való használathoz. Csak egyetlen tulajdonság alapján hozhat létre képletet. 
1. Válasszon egyet a következők összesítő függvények közül. 

   - Összeg: az összes érték számtani összege 
   - Átlag: az összes érték átlaga
   - Számlálás: az értékek teljes száma
   - Egyedi értékek száma: az egyedi értékek teljes száma

   A metrika definiálása után a metrika műveleti előnézete látható az utolsó óráról.

1. Válassza a **Mentés** parancsot. 
1. Adja meg a metrika nevét, majd válassza a **Mentés** lehetőséget.

A metrika esetében percet is igénybe vehet, mire [egyéni jelentések létrehozására](custom-reports.md) használhatja.

## <a name="edit-a-metric"></a>Metrika szerkesztése

1. Ugorjon az **Adatok** > **Metrikák** menübe.
1. A listáról válassza ki a metrikát.
1. A metrika definíciójának módosítása
1. Válassza a **Mentés** parancsot.

## <a name="change-the-name-of-a-metric"></a>Egy metrika nevének megváltoztatása

1. Ugorjon az **Adatok** > **Metrikák** menübe.
1. Válassza a **Továbbiak [...]** lehetőséget egy metrikához, majd válassza a **Név szerkesztése** lehetőséget.
1. A név módosítása. 
1. Válassza az **Átnevezés** lehetőséget.

## <a name="delete-a-metric"></a>Metrika törlése

1. Ugorjon az **Adatok** > **Metrikák** menübe.
1. Válassza a **Továbbiak [...]** lehetőséget egy metrikánál, majd válassza a **Törlés** lehetőséget.

   :::image type="content" source="media/delete-metric.png" alt-text="Metrika törlése egy eseménytől.":::

1. Válassza ki az **Eltávolítás** lehetőséget a törlés megerősítéséhez.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
