---
title: Szegmensek exportálása Braze-be (előzetes verzió)
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a Braze-be.
ms.date: 06/29/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: conceptual
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 314a61f82c4040a8dbd6dff1dd5d92e20464f82a
ms.sourcegitcommit: dca46afb9e23ba87a0ff59a1776c1d139e209a32
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/29/2022
ms.locfileid: "9082680"
---
# <a name="export-segments-to-braze-preview"></a>Szegmensek exportálása Braze-be (előzetes verzió)

Exportálja az egyesített ügyfélprofilok szegmenseit a Braze-be, és használja őket marketingtevékenységekhez.

## <a name="prerequisites"></a>Előfeltételek

- Braze-fiók [és](https://www.braze.com/) a megfelelő rendszergazdai hitelesítő adatok.
- Meglévő [szegmensek a Braze-ban](https://www.braze.com/docs/user_guide/engagement_tools/segments/creating_a_segment/).
- [Konfigurált szegmensek](segments.md) a Customer Insights szolgáltatásban.
- Az exportált szegmensek egyesített ügyfélprofiljai tartalmaznak egy mezőt, amely egy e-mail-címet és egy Braze-ügyfélazonosítót képvisel.

## <a name="known-limitations"></a>Ismert korlátozások

- A Braze-be való exportálás szegmensekre korlátozódik.
- Akár 1 millió ügyfélprofil braze-be történő exportálása akár 40 percet is igénybe vehet.
- A Braze-be exportálható ügyfélprofilok száma a Braze-szel kötött szerződésétől függ és korlátozott.

## <a name="set-up-connection-to-braze"></a>Kapcsolat beállítása a Braze-hez

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a Kapcsolat **hozzáadása lehetőséget**, majd válassza a Braze **lehetőséget** a kapcsolat konfigurálásához.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Adja meg a [Braze API-kulcsot](https://www.braze.com/docs/api/basics/) a bejelentkezés folytatásához.

1. Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.

1. Válassza a Csatlakozás **lehetőséget** a Braze-hez való kapcsolat inicializálásához.

1. Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

## <a name="configure-an-export"></a>Exportálás konfigurálása

Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz. További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Új exportálás létrehozásához válassza a **Célhely hozzáadása** lehetőséget.

1. **A Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot a Braze szakaszból. Ha nem látja ezt a szakaszt, nem állnak rendelkezésre ilyen típusú kapcsolatok.  

1. Adjon hozzá egy **megjelenítendő név** az exportáláshoz.

1. Adja hozzá annak a Braze-szegmensnek az API-azonosítóját, amelybe exportálni szeretne a **Braze szegmens API-azonosítója** mezőben. Az azonosítót a Braze platformon található szegmens részletei között találja.

1. Az **Adatok egyeztetése** szakaszban, az **E-mail** mezőben válassza ki az ügyfél e-mail címét jelképező mezőt. **Az Ügyfél-azonosító** mezőben válassza ki azt a mezőt, amely az ügyfél Braze-azonosítóját jelöli. Szegmenseket kell exportálnia a Braze-be. További mezőket is kiválaszthat opcionálisan.

1. Válassza a **Mentés** parancsot.

Az exportálás mentése nem futtatja azonnal az exportálást.

Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut. Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand). 


## <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség

Ha engedélyezi Dynamics 365 Customer Insights az adatok továbbítását a Braze-nek, akkor engedélyezi az adatok továbbítását a megfelelőségi határon túlra Dynamics 365 Customer Insights, beleértve a potenciálisan bizalmas adatokat, például a Személyes adatokat is. A Microsoft az Ön utasítására továbbítja ezeket az adatokat, de Ön felelős azért, hogy a Braze teljesítse az Ön esetleges adatvédelmi vagy biztonsági kötelezettségeit. További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).

A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.
