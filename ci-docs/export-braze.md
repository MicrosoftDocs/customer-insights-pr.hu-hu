---
title: Customer Insights-adatok exportálása a Braze-be
description: További információ a kapcsolat konfigurálásáról és a Braze-be való exportálásról.
ms.date: 03/29/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: conceptual
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: bfc9b34506dc3385b5edf12b31e74d05f2d20655
ms.sourcegitcommit: b7dbcd5627c2ebfbcfe65589991c159ba290d377
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/27/2022
ms.locfileid: "8642548"
---
# <a name="export-segment-lists-to-braze-preview"></a>Szegmenslisták exportálása a Braze programba (előzetes verzió)

Egyesített ügyfélprofilok szegmenseinek exportálása a Braze-be, és marketingtevékenységekhez való felhasználása.

## <a name="prerequisites"></a>Előfeltételek

-   Braze-fiókkal [és megfelelő rendszergazdai hitelesítő adatokkal rendelkezik](https://www.braze.com/).
-   Szegmenseket [konfigurált](segments.md) a Customer Insights szolgáltatásban.
-   Az exportált szegmensek egységes ügyfélprofiljai egy e-mail címet és egy Braze ügyfélazonosítót jelölő mezőt tartalmaznak. 

## <a name="known-limitations"></a>Ismert korlátozások

- A Braze-be történő exportálás szegmensekre korlátozódik.
- Akár 1 millió ügyfélprofil exportálása a Braze-be akár 40 percet is igénybe vehet. 
- A Braze-be exportálható ügyfélprofilok száma a Braze-szel kötött szerződésétől függ, és csak korlátozott.

## <a name="set-up-connection-to-braze"></a>Kapcsolat beállítása a Braze-hez

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a Kapcsolat **hozzáadása lehetőséget**, és válassza a Braze **lehetőséget** a kapcsolat konfigurálásához.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Adja meg a [Braze API-kulcsot](https://www.braze.com/docs/api/basics/) a bejelentkezés folytatásához. 

1. Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.

1. Válassza a Csatlakozás **lehetőséget** a Braze-szel való kapcsolat inicializálásához.

1. Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

## <a name="configure-an-export"></a>Exportálás konfigurálása

Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz. További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Új exportálás létrehozásához válassza a **Célhely hozzáadása** lehetőséget.

1. A Kapcsolat exportáláshoz **mezőben** válasszon ki egy kapcsolatot a Braze szakaszból. Ha nem látja ezt a szakasznevet, az Ön számára nincs ilyen típusú kapcsolat.  

3. **Az Adatok egyeztetése** szakaszban, az **E-mail** mezőben válassza ki a vevő e-mail címét jelölő mezőt, a "Vevőazonosító" mezőben válassza ki a vevő Braze azonosítóját képviselő mezőt. Szegmenseket kell exportálni Braze-be. A Braze szegmensei a szegmensek a szegmens nevével jönnek létre, mint a alkalmazásban Dynamics 365 Customer Insights. További, választható mezőket is választhat az adatok egyeztetéséhez. 

1. Válassza a **Mentés** parancsot.

Az exportálás mentése nem futtatja azonnal az exportálást.

Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut. Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand). 


## <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség

Ha engedélyezi Dynamics 365 Customer Insights az adatok továbbítását a Braze-nek, engedélyezi az adatok továbbítását a megfelelőségi határokon kívülre Dynamics 365 Customer Insights, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat is. A Microsoft az Ön utasítására továbbítja ezeket az adatokat, de Ön felelős annak biztosításáért, hogy a Braze megfeleljen az Esetleges adatvédelmi vagy biztonsági kötelezettségeinek. További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).

A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.
