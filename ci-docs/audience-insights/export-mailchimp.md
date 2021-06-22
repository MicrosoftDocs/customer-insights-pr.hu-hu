---
title: Customer Insights adatok exportálása a Mailchimpbe
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a Mailchimpbe.
ms.date: 03/03/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 7922a6a69f863caae5401549ed6f88a61aa77d39
ms.sourcegitcommit: 831765a55775d358447cb7ffa56f2c3b85459084
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/01/2021
ms.locfileid: "6124230"
---
# <a name="export-segments-to-mailchimp-preview"></a>Szegmensek exportálása a Mailchimpbe (előzetes verzió)

Az egyesített ügyfélprofilok szegmenseinek Mailchimpbe való exportálásával hírleveleket és e-mail-kampányokat hozhat létre.

## <a name="prerequisites-for-connection"></a>A kapcsolat előfeltételei

-   Rendelkezik [Mailchimp-fiókkal](https://mailchimp.com/) és a megfelelő rendszergazdai hitelesítő adatokkal.
-   A Mailchimpben és a megfelelő azonosítókban meglévő célközönségek találhatók. További információért lásd: [Mailchimp-célközönségek](https://mailchimp.com/help/create-audience/).
-   Rendelkezik [konfigurált szegmensekkel](segments.md)
-   Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.

## <a name="known-limitations"></a>Ismert korlátozások

- Legfeljebb 1 000 000 profilt exportálhat egyszerre a Mailchimpbe.
- A Mailchimpbe való exportálás csak szegmensekre korlátozódik.
- Az 1 millió profilból álló szegmensek exportálása akár három órát is igénybe fog venni. 
- A Mailchimpbe exportálható profilok száma függ a Mailchimp szerződésről, és korlátozott.

## <a name="set-up-connection-to-mailchimp"></a>Állítsa be a Mailchimppel való kapcsolatot

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza az **Autopilot** lehetőséget a kapcsolat konfigurálásához.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.

1. Válassza a **Kapcsolat** lehetőséget a Mailchimp kapcsolatának inicializálására.

1. Válassza a **Hitelesítés a Mailchimp szolgáltatással** lehetőséget, és adja meg Mailchimp-hitelesítő adatait.

1. Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget. 

## <a name="configure-the-connector"></a>Konfigurálja az összekötőt

Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz. További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).

1. Menjen az **Adatok**> **Exportálások** lehetőségre.

1. Új exportálás létrehozásához válassza a **Célhely hozzáadása** lehetőséget.

1. A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot a Mailchimp szakaszból. Ha nem látja ezt a szakasznevet, az Ön számára nincs ilyen típusú kapcsolat.

1. Adja meg a **[MailChimp célközönség-azonosítóját](https://mailchimp.com/help/find-audience-id/)**

3. Az **Adategyeztetés** szakaszban az **E-mail** mezőben jelölje ki az egyesített ügyfélprofil ügyfél e-mail-címét jelképező mezőjét. 

1. Tetszés szerint exportálhatja az **Utónév** és **Vezetéknév** lehetőségeket, hogy személyre szabottabb e-maileket hozzon létre. Válassza az **Attribútum hozzáadása** lehetőséget a mezők leképezéséhez.

1. Jelölje ki a szegmenseket, amelyeket exportálni szeretne. Összesen legfeljebb 1 000 000 ügyfélprofilt exportálhat a Mailchimpbe.

1. Válassza a **Mentés** parancsot.

Az exportálás mentése nem futtatja azonnal az exportálást.

Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut. Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand). 

## <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség

Amikor engedélyezi a Dynamics 365 Customer Insights szolgáltatást az adatok Mailchimp szolgáltatásba való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat. A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy a Mailchimp megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek. További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).
A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
