---
title: Szegmensek exportálása Iterable formátumba (előzetes verzió)
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja az Iterable-be.
ms.date: 03/29/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: conceptual
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 98d5aeab6b0e932d291213053d509ec72da82e47
ms.sourcegitcommit: a97d31a647a5d259140a1baaeef8c6ea10b8cbde
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/29/2022
ms.locfileid: "9052238"
---
# <a name="export-segments-to-iterable-preview"></a>Szegmensek exportálása Iterable formátumba (előzetes verzió)

Exportálja az egyesített ügyfélprofilok szegmenseit az Iterable fájlba, és használja őket marketingtevékenységekhez.

## <a name="prerequisites"></a>Előfeltételek

-   Iterable-fiókkal [és a megfelelő rendszergazdai hitelesítő adatokkal rendelkezik](https://iterable.com/).
-   [A szegmenseket](segments.md) a Customer Insights szolgáltatásban konfigurálta.
-   Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.

## <a name="known-limitations"></a>Ismert korlátozások

- Az Iterable-be való exportálás szegmensekre korlátozódik.
- Akár 1 millió ügyfélprofil iterable-be történő exportálása akár 30 percet is igénybe vehet. 
- Az Iterable-be exportálható ügyfélprofilok száma az Iterable-vel kötött szerződéstől függ és korlátozott.

## <a name="set-up-connection-to-iterable"></a>Kapcsolat beállítása az Iterable-hez

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a Kapcsolat **hozzáadása lehetőséget**, majd válassza az Iterable **lehetőséget** a kapcsolat konfigurálásához.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Adja meg az [Iterable API-kulcsot](https://support.iterable.com/hc/en-us/articles/360043464871) a további bejelentkezéshez. 

1. Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.

1. Válassza a Csatlakozás **lehetőséget** az Iterable-hez való kapcsolat inicializálásához.

1. Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

## <a name="configure-an-export"></a>Exportálás konfigurálása

Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz. További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Új exportálás létrehozásához válassza a **Célhely hozzáadása** lehetőséget.

1. **A Kapcsolat exportáláshoz** mezőben válasszon ki egy kapcsolatot az Iterable szakaszból. Ha nem látja ezt a szakasznevet, az Ön számára nincs ilyen típusú kapcsolat.

3. Az **Adatok egyeztetése** szakaszban, az **E-mail** mezőben válassza ki az ügyfél e-mail címét jelképező mezőt. A szegmenseket iterable-be kell exportálnia.Az Iterable-ben létrehozott lista pontosan ugyanazt a nevet kapja, mint a szegmens neve Dynamics 365 Customer Insights.

1. Válassza a **Mentés** parancsot.

Az exportálás mentése nem futtatja azonnal az exportálást.

Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut. Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand). 


## <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség

Ha engedélyezi Dynamics 365 Customer Insights az adatok továbbítását az Iterable-nek, engedélyezi az adatok továbbítását a megfelelőségi határon túlra Dynamics 365 Customer Insights, beleértve a potenciálisan bizalmas adatokat, például a személyes adatokat is. A Microsoft az Ön utasítására továbbítja ezeket az adatokat, de Ön felelős annak biztosításáért, hogy az Iterable megfeleljen az Ön esetleges adatvédelmi vagy biztonsági kötelezettségeinek. További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).

A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.
