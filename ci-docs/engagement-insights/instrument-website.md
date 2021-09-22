---
title: Kód hozzáadása a webhelyéhez
description: Hogyan adhat hozzá egy kódrészletet ahhoz, hogy eseményeket rögzítsen a webhelyén.
author: britl
ms.reviewer: mhart
ms.author: britl
ms.date: 04/30/2021
ms.service: customer-insights
ms.subservice: engagement-insights
ms.topic: how-to
ms.manager: shellyha
ms.openlocfilehash: b5467da775a621c436bd9ddedb272506acc1e2b31dcf7c87feb5dd11e2daae2b
ms.sourcegitcommit: aa0cfbf6240a9f560e3131bdec63e051a8786dd4
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/10/2021
ms.locfileid: "7035097"
---
# <a name="install-the-code-snippet-on-a-website"></a>Telepítse a kódrészletet egy webhelyen

[!INCLUDE [cc-beta-prerelease-disclaimer](includes/cc-beta-prerelease-disclaimer.md)]

Ez a cikk azt ismerteti, hogyan telepíti a rendszergazda kódrészletet egy webhelyen. Röviddel a parancsfájlnak a webhelyhez való felvétele után láthatja az eseményeket a munkaterületén. További információ a [Munkaterületek és környezet kezelése](manage-environments-workspaces.md) oldalon található. A mobilalkalmazásokban zajló események rögzítéséhez tekintse meg a [Fejlesztői erőforrások áttekintést](developer-resources.md).


### <a name="prerequisites"></a>Előfeltételek

* Az adatok tárolásához rendszergazdai jogosultsággal kell rendelkeznie ahhoz, hogy a munkaterületen tárolhassa az adatokat.
* A tevékenységek adatainak elküldéséhez a webhelyet vagy projektet online állapotban kell üzemeltetni. A kiszolgáló nem fogadja el a helyi fájlból küldött adatokat.


## <a name="add-code-to-your-website"></a>Kód hozzáadása a webhelyéhez
1.  Válassza a **Felügyelet** > **Munkaterület** pontot, majd válassza a **Telepítési útmutató** lehetőséget.
1. Válassza a **Kód másolása** lehetőséget a kódrészlet másolásához. Alapértelmezés szerint a munkaterület beviteli kulcsa be van ágyazva a kódrészletbe.
:::image type="content" source="media/copy-code.png" alt-text="Képernyőfelvétel az kódrészlet oldalról.":::
3. Adja hozzá a másolt kódrészletet a webhelyhez, a <head> címke közelében, a többi parancsfájl vagy CSS címke elé.
4.  Tegye közzé a frissített webhelyet, és várjon néhány percet a bejövő webes forgalom rögzítésére.
5.  Az adatok megtekintéséhez válassza ki saját munkaterületét a navigációs ablaktáblában lévő munkaterület-kapcsolóból. Ezután válasszon ki egy jelentést a **Felfedezés** szakaszban.

## <a name="configuration-options"></a>Konfigurációs beállítások

A kódrészletben az alábbi konfigurációs beállításokat módosíthatja:

- **intionKey**: Az események munkaterületre való elküldését szolgáló beviteli kulcs. Módosíthatja a betöltési kulcsot, hogy az eseményeket másik munkaterületre küldje. A betöltési kulcs egyedi az egyes munkaterületeken. 
- **autoCapture**: Azt adja meg, hogy a rendszer rögzíti-e az oldalmegtekintéseket és a webhelyekkel való interakciókat. Két lehetőségből áll:
    - **view**: Az oldalmegtekintések rögzítéséhez állítsa *igazra*. Az oldalmegtekintések *Megtekintési* [események](glossary.md#event) elemként rögzülnek, amely az [alapesemény](glossary.md#base-event) egy típusa.
    - **click**: Állítsa *Igazra*, hogy rögzítse a látogatók interakcióit a webhellyel. Az interakciók *Műveleti* [események](glossary.md#event) elemként rögzülnek, amely az [alapesemény](glossary.md#base-event) egy típusa.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
