---
title: Customer Insights-adatok exportálása a Campaign Monitorra
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a Campaign Monitorba.
ms.date: 03/03/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 091a3197dc0c19ff78f0419fb4e88868e0f78359
ms.sourcegitcommit: 831765a55775d358447cb7ffa56f2c3b85459084
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/01/2021
ms.locfileid: "6124184"
---
# <a name="export-segments-to-campaign-monitor-preview"></a>Szegmensek exportálása a Campaign Monitorba (előzetes verzió)

Exportálja az egyesített ügyfélprofilok szegmensét a Campaign Monitorba, és használja őket marketing-tevékenységekre.

## <a name="prerequisites"></a>Előfeltételek

-   Van egy [Campaign Monitor fiókja](https://www.campaignmonitor.com/) és ahhoz tartozó rendszergazdai hitelesítő adatai.
-   [Konfigurált szegmensekkel](segments.md) rendelkezik a célközönségi-információkban.
-   Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.

## <a name="known-limitations"></a>Ismert korlátozások

- A Campaign Monitorba exportálásonként legfeljebb 1 millió profil exportálható.
- A Campaign Monitorba való exportálás a szegmensekre korlátozódik.
- 1 millió profil exportálása a Campaign Monitor alkalmazásba akár 20 percet is igénybe vehet. 
- A Campaign Monitorba exportálható profilok száma a Campaign Monitorral kötött szerződéstől függ és az korlátozza.

## <a name="set-up-connection-to-campaign-monitor"></a>Kapcsolat beállítása a Campaign Monitor alkalmazáshoz

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza a **Campaign Monitor** lehetőséget a kapcsolat konfigurálásához.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.

1. Válassza a **Kapcsolat** lehetőséget a Campaign Monitor kapcsolatának inicializálására.

1. Válassza a **Hitelesítés a Campaign Monitorral** lehetőséget, és adja meg a Campaign Monitor rendszergazdai hitelesítő adatait.

1. Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

## <a name="configure-an-export"></a>Exportálás konfigurálása

Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz. További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Új exportálás létrehozásához válassza a **Célhely hozzáadása** lehetőséget.

1. A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot a Campaign Monitor szakaszból. Ha nem látja ezt a szakasznevet, az Ön számára nincs ilyen típusú kapcsolat.

1. Adja meg a [**Campaign Monitor listaazonosítóját**](https://www.campaignmonitor.com/api/getting-started/#your-list-id).    
   [Hozza létre az API-kulcsot](https://www.campaignmonitor.com/api/getting-started/) a Campaign Monitor **Fiókbeállításokból**, és először tekintse meg az API-lista azonosítóját.  

3. Az **Adategyeztetés** szakaszban az **E-mail** mezőben jelölje ki az egyesített ügyfélprofil ügyfél e-mail-címét jelképező mezőjét. A szegmenseket exportálni kell a Campaign Monitor alkalmazásba.

1. Válassza a **Mentés** parancsot.

Az exportálás mentése nem futtatja azonnal az exportálást.

Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut. Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand). 


## <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség

Amikor engedélyezi Dynamics 365 Customer Insightst, hogy adatokat továbbítson a Campaign Monitornak, akkor lehetővé teszi az adatok továbbítását a Dynamics 365 Customer Insights megfelelési határán kívülre is, beleértve az esetlegesen bizalmas adatokat is, például a Személyes adatokat. A Microsoft az Ön utasítására továbbítja az adatokat, de Ön a felelős azért, hogy a Campaign Monitor megfeleljen az esetleges adatvédelmi vagy biztonsági kötelezettségeknek. További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).

A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.
