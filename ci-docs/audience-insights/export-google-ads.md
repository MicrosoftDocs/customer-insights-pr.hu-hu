---
title: Customer Insights adatok exportálása a Google Adsbe
description: Megismerheti, hogyan konfigurálható a kapcsolat a Google Adsszal.
ms.date: 11/18/2020
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: phkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 6d9a25af3913e755cccec745c532b35aef3cccf9
ms.sourcegitcommit: bae40184312ab27b95c140a044875c2daea37951
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/15/2021
ms.locfileid: "5598250"
---
# <a name="connector-for-google-ads-preview"></a>A Google Ads összekötője (előzetes verzió)

Exportáljon egyéni ügyfélprofilok szegmenseit a Google Ads célközönséglistába, és használja ezeket a hirdetésekhez a Google Kereső, a Gmail, a YouTube és a Google Display Network felületén. 

## <a name="prerequisites"></a>Előfeltételek

-   Rendelkezik [Google Ads-fiókkal](https://ads.google.com/) és a megfelelő rendszergazdai hitelesítő adatokkal.
-   A Google Adsban és a megfelelő azonosítókban meglévő célközönségek találhatók. További információért lásd: [Google Ads-célközönségek](https://support.google.com/google-ads/answer/7558048?hl=en#:~:text=Audience%20lists%20is%20a%20section,Display%20Network%20through%20remarketing%20campaigns.).
-   Rendelkezik [konfigurált szegmensekkel](segments.md)
-   Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőket, amelyek az e-mail-címet, utónevet és vezetéknevet tartalmazzák

## <a name="connect-to-google-ads"></a>Csatlakozás a Google Ads szolgáltatáshoz

1. Válassz a **Rendszergazda** > **Célok exportálása** lehetőséget.

1. A **Google Ads** részben válassza a **Beállítás** lehetőséget.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben az export helyének.

1. Adja meg **[Google Ads ügyfél-azonosítóját](https://support.google.com/google-ads/answer/1704344)**.

1. Adja meg **[a jóváhagyott Google Ads-fejlesztői jogkivonatát](https://developers.google.com/google-ads/api/docs/first-call/dev-token)**.

1. Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.

1. Adja meg a **[Google Ads célközönség azonosítóját](https://support.google.com/google-ads/answer/7558048?hl=en#:~:text=Audience%20lists%20is%20a%20section,Display%20Network%20through%20remarketing%20campaigns.)**, és válassza a **Csatlakozás** lehetőséget a Google Ads-kapcsolat kezdeményezéséhez.

1. Válassza a **Hitelesítés a Google Ads szolgáltatással** lehetőséget, és adja meg Google Ads-hitelesítő adatait.

1. Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.

   :::image type="content" source="media/export-segments-googleads.PNG" alt-text="Képernyőkép exportálása a Google Ads kapcsolatához":::

1. Az Exportálás konfigurálásához válassza a **Tovább** lehetőséget.

## <a name="configure-the-connector"></a>Konfigurálja az összekötőt

1. Az **Adategyeztetés** szakaszban az **E-mail** mezőben jelölje ki az egyesített ügyfélprofil ügyfél e-mail-címét jelképező mezőjét. Ismételje meg ugyanezeket a lépéseket az **Utónév** és a **Vezetéknév** mezőkkel is.

1. Jelölje ki a szegmenseket, amelyeket exportálni szeretne. Összesen legfeljebb 1 000 000 ügyfélprofilt exportálhat a Google Adsbe.

1. Válassza a **Mentés** parancsot.

## <a name="export-the-data"></a>Az adatok exportálása

[Igény szerint exportálhatja az adatot](export-destinations.md). Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) együtt is lefut. A Google Adsben most már megtalálhatja a szegmenseket a [Google Ads célközönségei](https://support.google.com/google-ads/answer/7558048?hl=en/) között.

## <a name="known-limitations"></a>Ismert korlátozások

- Legfeljebb 1 000 000 profilt exportálhat egyszerre a Google Adsbe.
- A Google Adsbe való exportálás csak szegmensekre korlátozódik.
- Az összesen 1 000 000 profillal rendelkező szegmens exportálása a szolgáltatói oldalon megjelenő korlátozások miatt akár 5 percig is eltarthat. 
- A Google Ads egyeztetése akár 48 óráig is eltarthat.

## <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség

Amikor engedélyezi a Dynamics 365 Customer Insights szolgáltatást az adatok Google Ads szolgáltatásba való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat. A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy a Google Ads megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek. További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).
A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.


[!INCLUDE[footer-include](../includes/footer-banner.md)]