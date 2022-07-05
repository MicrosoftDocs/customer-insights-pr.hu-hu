---
title: Szegmensek exportálása az Autopilotba (előzetes verzió)
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja az Autopilotba.
ms.date: 10/08/2021
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: conceptual
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: e3af3d03e70c4ce9d229c84c582ec4f302be8c9f
ms.sourcegitcommit: dca46afb9e23ba87a0ff59a1776c1d139e209a32
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/29/2022
ms.locfileid: "9082533"
---
# <a name="export-segments-to-autopilot-preview"></a>Szegmensek exportálása az Autopilotba (előzetes verzió)

Exportálja az egyesített ügyfélprofilok szegmenseit az Autopilotba, és használja őket kampányokhoz és e-mail marketinghez az Autopilotban. 

## <a name="prerequisites-for-a-connection"></a>Egy kapcsolat előfeltételei

-   Rendelkezik [Autopilot-fiókkal](https://www.autopilothq.com/) és a megfelelő rendszergazdai hitelesítő adatokkal.
-   [A szegmenseket](segments.md) a Customer Insights szolgáltatásban konfigurálta.
-   Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.

## <a name="known-limitations"></a>Ismert korlátozások

- Összesen legfeljebb 100 000 ügyfélprofilt exportálhat az Autopilot szolgáltatásba.
- Az Autopilotba való exportálás csak szegmensekre korlátozódik.
- 100 000 ügyfélprofil exportálása a Autopilot szolgáltatásba akár néhány órát is igénybe vehet. 
- Az Autopilot alkalmazásba exportálható ügyfélprofilok száma az Autopilottal kötött szerződéstől függ, és csak korlátozott.

## <a name="set-up-connection-to-autopilot"></a>Állítsa be az Autopilottal való kapcsolatot

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza az **Autopilot** lehetőséget a kapcsolat konfigurálásához.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Adja meg az [Autopilot API-kulcsát](https://autopilot.docs.apiary.io/#).

1. Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.

1. Válassza a **Csatlakozás** lehetőséget az Autopilot kapcsolat inicializálásához.

1. Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

## <a name="configure-an-export"></a>Exportálás konfigurálása

Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz. További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Új exportálás létrehozásához válassza a **Célhely hozzáadása** lehetőséget.

1. A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot az Autopilot szakaszból. Ha nem látja ezt a szakasznevet, az Ön számára nincs ilyen típusú kapcsolat.

1. Az **Adatok egyeztetése** szakaszban, az **E-mail** mezőben válassza ki az ügyfél e-mail címét jelképező mezőt. Ismételje meg ugyanezeket a lépéseket az egyéb választható mezőkön, például az **Utónév**, a **Vezetéknév**.

1. Jelölje ki a szegmenseket, amelyeket exportálni szeretne. Fokozottan **javasoljuk, hogy ne exportáljon összesen 100 000-nél több ügyfélprofilt** az Autopilotba. 

1. Válassza a **Mentés** parancsot.

Az exportálás mentése nem futtatja azonnal az exportálást.

Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut. Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand). 

## <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség

Amikor engedélyezi a Dynamics 365 Customer Insights szolgáltatást az adatok Autopilot szolgáltatásba való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat. A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy az Autopilot megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek. További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).
A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.


[!INCLUDE [footer-include](includes/footer-banner.md)]
