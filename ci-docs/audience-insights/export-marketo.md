---
title: Customer Insights adatok exportálása a Marketóba
description: Megismerheti, hogyan konfigurálható a kapcsolat a Marketóval.
ms.date: 11/12/2020
ms.reviewer: philk
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: 34ccee2894f1f2b552d0c6a88a6810e2dfc677a3
ms.sourcegitcommit: 0b1d3ca11b8ba362a959da0eea15c37e9cdba084
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/18/2020
ms.locfileid: "4570406"
---
# <a name="connector-for-marketo-preview"></a>A Marketo összekötője (előzetes verzió)

Az egyesített ügyfélprofilok szegmensei exportálásának felhasználásával kampányokat hozhat létre, e-mail-marketing szolgáltatást biztosíthat és előnyt kovácsolhat az ügyfelek meghatározott csoportjából a Marketo szolgáltatással.

## <a name="prerequisites"></a>Előfeltételek

-   Rendelkezik [Marketo-fiókkal](https://login.marketo.com/) és a megfelelő rendszergazdai hitelesítő adatokkal.
-   A Marketóban és a megfelelő azonosítókban meglévő listák találhatók. További tájékoztatásért keresse fel a [Marketo listák](https://docs.marketo.com/display/public/DOCS/Understanding+Static+Lists) webhelyet.
-   Rendelkezik [konfigurált szegmensekkel](segments.md).
-   Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.

## <a name="connect-to-marketo"></a>Csatlakozás a Marketóhoz

1. Válassz a **Rendszergazda** > **Célok exportálása** lehetőséget.

1. A **Marketo** részben válassza a **Beállítás** lehetőséget.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben az export helyének.

1. Adja meg a **[Marketo ügyfél-azonosítót, titkos ügyfélkódot és REST végpont eszköznevét](https://developers.marketo.com/rest-api/authentication/)**.

1. Adja meg a **[Marketo-lista azonosítóját](https://docs.marketo.com/display/public/DOCS/Understanding+Static+Lists)** 

1. Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez, majd válassza a **Csatlakozás** lehetőséget a Marketo kapcsolat inicializálásához.

1. Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.

   :::image type="content" source="media/export-connect-marketo.png" alt-text="Képernyőkép exportálása a Marketo kapcsolatához":::

1. Az Exportálás konfigurálásához válassza a **Tovább** lehetőséget.

## <a name="configure-the-connector"></a>Konfigurálja az összekötőt

1. Az **Adategyeztetés** szakaszban az **E-mail** mezőben jelölje ki az egyesített ügyfélprofil ügyfél e-mail-címét jelképező mezőjét. 

1. Alternatív lehetőségként exportálhatja az **Utónév**, **Vezetéknév**, **Város**, **Állam** és **Ország/régió** mezőket további mezőként személyre szabottabb e-mailek létrehozásához. Válassza az **Attribútum hozzáadása** lehetőséget a mezők leképezéséhez.

1. Jelölje ki a szegmenseket, amelyeket exportálni szeretne. Összesen legfeljebb 1 000 000 ügyfélprofilt exportálhat a Marketóba.

   :::image type="content" source="media/export-segment-marketo.png" alt-text="Marketóba exportálandó mezők és szegmensek kijelölése":::

1. Válassza a **Mentés** parancsot.

## <a name="export-the-data"></a>Az adatok exportálása

[Igény szerint exportálhatja az adatot](export-destinations.md). Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) együtt is lefut. A Marketóban most már megtalálhatja a szegmenseket a [Marketo listában](ttps://docs.marketo.com/display/public/DOCS/Understanding+Static+Lists).

## <a name="known-limitations"></a>Ismert korlátozások

- Legfeljebb 1 000 000 profilt exportálhat egyszerre a Marketoba.
- A Marketoba való exportálás csak szegmensekre korlátozódik.
- Az összesen 1 000 000 profillal rendelkező szegmensek exportálása akár 3 óráig is eltarthat. 
- A Marketoba exportálható profilok száma függ a Marketo szerződésről, és korlátozott.

## <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség

Amikor engedélyezi az Dynamics 365 Customer Insights szolgáltatást az adatok Marketoba való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat. A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy az Marketo megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek. További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).
A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.
