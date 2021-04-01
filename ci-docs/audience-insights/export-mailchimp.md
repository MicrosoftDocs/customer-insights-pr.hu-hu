---
title: Customer Insights adatok exportálása a Mailchimpbe
description: Megismerheti, hogyan konfigurálható a kapcsolat a Mailchimppel.
ms.date: 10/26/2020
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: phkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 9f86616731c3cc3d26370727103ea9c5d4288c8d
ms.sourcegitcommit: bae40184312ab27b95c140a044875c2daea37951
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/15/2021
ms.locfileid: "5598204"
---
# <a name="connector-for-mailchimp-preview"></a>A Mailchimp összekötője (előzetes verzió)

Az egyesített ügyfélprofilok szegmenseinek Mailchimpbe való exportálásával hírleveleket és e-mail-kampányokat hozhat létre.

## <a name="prerequisites"></a>Előfeltételek

-   Rendelkezik [Mailchimp-fiókkal](https://mailchimp.com/) és a megfelelő rendszergazdai hitelesítő adatokkal.
-   A Mailchimpben és a megfelelő azonosítókban meglévő célközönségek találhatók. További információért lásd: [Mailchimp-célközönségek](https://mailchimp.com/help/create-audience/).
-   Rendelkezik [konfigurált szegmensekkel](segments.md)
-   Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.

## <a name="connect-to-mailchimp"></a>Csatlakozás a MailChimp szolgáltatáshoz

1. Válassz a **Rendszergazda** > **Célok exportálása** lehetőséget.

1. A **Mailchimp** részben válassza a **Beállítás** lehetőséget.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben az export helyének.

1. Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.

1. Adja meg a **[Mailchimp célközönség azonosítóját](https://mailchimp.com/help/find-audience-id/)**, és válassza a **Csatlakozás** lehetőséget a Mailchimp-kapcsolat kezdeményezéséhez.

1. Válassza a **Hitelesítés a Mailchimp szolgáltatással** lehetőséget, és adja meg Mailchimp-hitelesítő adatait.

1. Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.

   :::image type="content" source="media/export-connect-mailchimp.png" alt-text="Képernyőkép exportálása a Mailchimp kapcsolatához":::

1. Az Exportálás konfigurálásához válassza a **Tovább** lehetőséget.

## <a name="configure-the-connector"></a>Konfigurálja az összekötőt

1. Az **Adategyeztetés** szakaszban az **E-mail** mezőben jelölje ki az egyesített ügyfélprofil ügyfél e-mail-címét jelképező mezőjét. 

1. Alternatív lehetőségként exportálhatja az **Utónév** és **Vezetéknév** mezőket további mezőként személyre szabottabb e-mailek létrehozásához. Válassza az **Attribútum hozzáadása** lehetőséget a mezők leképezéséhez.

1. Jelölje ki a szegmenseket, amelyeket exportálni szeretne. Összesen legfeljebb 1 000 000 ügyfélprofilt exportálhat a Mailchimpbe.

   :::image type="content" source="media/export-segments-mailchimp.png" alt-text="Mailchimpbe exportálandó mezők és szegmensek kijelölése":::

1. Válassza a **Mentés** parancsot.

## <a name="export-the-data"></a>Az adatok exportálása

[Igény szerint exportálhatja az adatot](export-destinations.md). Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) együtt is lefut. A Mailchimpben most már megtalálhatja a szegmenseket a [Mailchimp célközönségekben](https://mailchimp.com/help/create-audience/).

## <a name="known-limitations"></a>Ismert korlátozások

- Legfeljebb 1 000 000 profilt exportálhat egyszerre a Mailchimpbe.
- A Mailchimpbe való exportálás csak szegmensekre korlátozódik.
- Az összesen 1 000 000 profillal rendelkező szegmens exportálása a szolgáltatói oldalon megjelenő korlátozások miatt akár 3 óráig is eltarthat. 
- A Mailchimpbe exportálható profilok száma függ a Mailchimp szerződésről, és korlátozott.

## <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség

Amikor engedélyezi a Dynamics 365 Customer Insights szolgáltatást az adatok Mailchimp szolgáltatásba való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat. A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy a Mailchimp megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek. További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).
A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.


[!INCLUDE[footer-include](../includes/footer-banner.md)]