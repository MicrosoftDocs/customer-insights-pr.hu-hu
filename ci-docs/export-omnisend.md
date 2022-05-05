---
title: Customer Insights-adatok exportálása az Ominsend-szolgáltatásba
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja az Ominsendbe.
ms.date: 10/08/2021
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: conceptual
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 70bd94ea5e4060094c3d215e3fc263a98df51229
ms.sourcegitcommit: b7dbcd5627c2ebfbcfe65589991c159ba290d377
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/27/2022
ms.locfileid: "8642796"
---
# <a name="export-segments-to-omnisend-preview"></a>Szegmensek exportálása az Ominsendbe (előzetes verzió)

Exportálja az egyesített ügyfélprofilok szegmensét az Ominsendbe, és használja őket marketing-tevékenységekre.

## <a name="prerequisites"></a>Előfeltételek

-   Van egy [Ominsend fiókja](https://www.omnisend.com/) és ahhoz tartozó rendszergazdai hitelesítő adatai.
-   Szegmenseket [konfigurált](segments.md) a Customer Insights szolgáltatásban.
-   Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.

## <a name="known-limitations"></a>Ismert korlátozások

- Exportálásonként legfeljebb 1 millió ügyfélprofil exportálható az Omnisend fájlba, és a művelet akár 4 órát is igénybe vehet.
- Az Ominsendbe való exportálás a szegmensekre korlátozódik.
- Az Omnisend alkalmazásba exportálható ügyfélprofilok száma az Omnisend szolgáltatással kötött szerződéstől függ, és csak korlátozott.

## <a name="set-up-connection-to-omnisend"></a>Állítsa be az Ominsenddel való kapcsolatot

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza az **Ominsend** lehetőséget a kapcsolat konfigurálásához.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Alapértelmezés szerint csak a rendszergazdák. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Adja meg az [Ominsend API-kulcsát](https://support.omnisend.com/en/articles/1061890-generating-api-key).

1. Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.

1. Válassza a **Kapcsolat** lehetőséget az Ominsend kapcsolatának inicializálására.

1. Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

## <a name="configure-an-export"></a>Exportálás konfigurálása

Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz. További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Új exportálás létrehozásához válassza a **Célhely hozzáadása** lehetőséget.

1. A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot az Ominsend szakaszból. Ha nem látja ezt a szakasznevet, az Ön számára nincs ilyen típusú kapcsolat.

1. Az **Adatok egyeztetése** szakaszban, az **E-mail** mezőben válassza ki az ügyfél e-mail címét jelképező mezőt. A szegmenseket exportálni kell az Ominsendbe. Tetszés szerint exportálhatja az Utónév, Vezetéknév, Cím, Ország/Régió, Állam, Város és Irányítószám lehetőségeket, hogy személyre szabottabb e-maileket hozzon létre. Válassza az **Attribútum hozzáadása** lehetőséget a mezők leképezéséhez.

1. Válassza a **Mentés** parancsot.

Az exportálás mentése nem futtatja azonnal az exportálást.

Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut. Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand). 


## <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség

Amikor engedélyezi Dynamics 365 Customer Insights számára, hogy adatokat továbbítson az Ominsendnek, akkor lehetővé teszi az adatok továbbítását a Dynamics 365 Customer Insights megfelelési határán kívülre is, beleértve az esetlegesen bizalmas adatokat is, például a Személyes adatokat. A Microsoft az Ön utasítására továbbítja az adatokat, de Ön a felelős azért, hogy az Ominsend megfeleljen az esetleges adatvédelmi vagy biztonsági kötelezettségeknek. További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).

A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.
