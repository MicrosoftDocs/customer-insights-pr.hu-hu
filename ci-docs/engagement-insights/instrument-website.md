---
title: Kód hozzáadása a webhelyéhez
description: Hogyan adhat hozzá egy kódrészletet ahhoz, hogy Dynamics 365 Customer Insights eseményeket rögzítsen a webhelyén.
author: britl
ms.reviewer: mhart
ms.author: britl
ms.date: 09/27/2021
ms.service: customer-insights
ms.subservice: engagement-insights
ms.topic: how-to
ms.manager: shellyha
ms.openlocfilehash: ad835f762226d62fdb0f544627f2a76ff09a1ffd
ms.sourcegitcommit: f1e3cc51ea4cf68210eaf0210ad6e14b15ac4fe8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/27/2021
ms.locfileid: "7558860"
---
# <a name="install-the-web-sdk-on-a-website"></a>A webes SDK telepítése egy webhelyre

[!INCLUDE [cc-beta-prerelease-disclaimer](includes/cc-beta-prerelease-disclaimer.md)]

Ez a cikk azt ismerteti, hogyan telepíti a rendszergazda a webes szoftverfejlesztői eszközkészletet (SDK) egy webhelyen. Nem sokkal a webhelye felszerelése után eseményeket fog látni a munkaterületén. További információ a [Munkaterületek és környezet kezelése](manage-environments-workspaces.md) oldalon található. A mobilalkalmazásokban zajló események rögzítéséhez tekintse meg a [Fejlesztői erőforrások áttekintést](developer-resources.md).


### <a name="prerequisites"></a>Előfeltételek

* Az adatok tárolásához rendszergazdai jogosultsággal kell rendelkeznie ahhoz, hogy a munkaterületen tárolhassa az adatokat.
* A tevékenységek adatainak elküldéséhez a webhelyet vagy projektet online állapotban kell üzemeltetni. A kiszolgáló nem fogadja el a helyi fájlból küldött adatokat.


## <a name="add-web-sdk-to-your-website"></a>SDK hozzáadása a webhelyéhez

Válassza a **Felügyelet** > **Munkaterület** pontot, majd válassza a **Telepítési útmutató** lehetőséget. A webes SDK telepítésére két lehetőség van: Az első a letöltési hivatkozás használata, a második a csomópontcsomag-kezelő (NPM) csomag telepítése.

### <a name="option-1-using-the-download-link"></a>1. lehetőség: Letöltési hivatkozás használata

1. Válassza a **Kód másolása** lehetőséget a kódrészlet másolásához. Alapértelmezés szerint a munkaterület beviteli kulcsa be van ágyazva a kódrészletbe.
  :::image type="content" source="media/copy-code.png" alt-text="Képernyőfelvétel az kódrészlet oldalról.":::

1. Adja hozzá a másolt kódot a webhelyhez, a <head> címke közelében, a többi parancsfájl vagy CSS címke elé.
1. Tegye közzé a frissített webhelyet, és várjon néhány percet a bejövő webes forgalom rögzítésére.
1. Az adatok megtekintéséhez válassza ki saját munkaterületét a navigációs ablaktáblában lévő munkaterület-kapcsolóból. Ezután válasszon ki egy jelentést a **Felfedezés** szakaszban.

### <a name="option-2-using-the-npm-package-recommended-for-javascript-based-web-apps"></a>2. lehetőség: Az NPM csomag használata (JavaScript-alapú webalkalmazások esetén ajánlott)

1. Látogasson el az [NPM weboldalra](https://www.npmjs.com/package/engagementinsights-web) és kövesse az utasításokat a webes SDK NPM csomag telepítéséhez és beállításához.
1. Tegye közzé a frissített webhelyet, és várjon néhány percet a bejövő webes forgalom rögzítésére.
1. Az adatok megtekintéséhez válassza ki saját munkaterületét a navigációs ablaktáblában lévő munkaterület-kapcsolóból. Ezután válasszon ki egy jelentést a **Felfedezés** szakaszban.

## <a name="configuration-options"></a>Konfigurációs beállítások

A kódrészletben az alábbi konfigurációs beállításokat módosíthatja:

- **intionKey**: Az események munkaterületre való elküldését szolgáló beviteli kulcs. Módosíthatja a betöltési kulcsot, hogy az eseményeket másik munkaterületre küldje. A betöltési kulcs egyedi az egyes munkaterületeken.
- **autoCapture**: Azt adja meg, hogy a rendszer rögzíti-e az oldalmegtekintéseket és a webhelyekkel való interakciókat. Két lehetőségből áll:
    - **view**: Az oldalmegtekintések rögzítéséhez állítsa *igazra*. Az oldalmegtekintések *Megtekintési* [események](glossary.md#event) elemként rögzülnek, amely az [alapesemény](glossary.md#base-event) egy típusa.
    - **click**: Állítsa *Igazra*, hogy rögzítse a látogatók interakcióit a webhellyel. Az interakciók *Műveleti* [események](glossary.md#event) elemként rögzülnek, amely az [alapesemény](glossary.md#base-event) egy típusa.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
