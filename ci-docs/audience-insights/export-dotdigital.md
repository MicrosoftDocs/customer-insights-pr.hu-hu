---
title: Customer Insights adatok exportálása a DotDigitalbe
description: Megismerheti, hogyan konfigurálható a kapcsolat a DotDigitallal.
ms.date: 11/14/2020
ms.reviewer: philk
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: 573a22e24f84c65fc4d21faf823cace801cc7ea3
ms.sourcegitcommit: 139548f8a2d0f24d54c4a6c404a743eeeb8ef8e0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/15/2021
ms.locfileid: "5269103"
---
# <a name="connector-for-dotdigital-preview"></a>A DotDigital összekötője (előzetes verzió)

Az egyesített ügyfélprofilok szegmenseit exportálhatja a DotDigital címjegyzékekbe, és használhatja őet kampányokhoz, e-mail-marketinghez és ügyfélszegmensek létrehozásához a DotDigitallal. 

## <a name="prerequisites"></a>Előfeltételek

-   Rendelkezik [DotDigital-fiókkal](https://dotdigital.com/) és a megfelelő rendszergazdai hitelesítő adatokkal.
-   A DotDigitalban és a megfelelő azonosítókban meglévő címjegyzékek találhatók. Az azonosító megtalálhatók az URL-címben, amikor kijelöli és megnyitja a címjegyzéket. További információért lásd: [DotDigital címjegyzékek](https://support.dotdigital.com/hc/articles/212211968-Creating-an-address-book).
-   [Konfigurált szegmensekkel](segments.md) rendelkezik a célközönségi-információkban.
-   Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.

## <a name="connect-to-dotdigital"></a>Csatlakozás a DotDigitalhoz

1. Válassz a **Rendszergazda** > **Célok exportálása** lehetőséget.

1. A **DotDigital** részben válassza a **Beállítás** lehetőséget.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben az export helyének.

   :::image type="content" source="media/DotDigital_config.PNG" alt-text="A DotDigital exportálásának konfigurációs ablaktáblája.":::

1. Adja meg a **DotDigital felhasználói nevét és a jelszavát**.

1. Adja meg a **[DotDigital címjegyzék-azonosítóját](https://support.dotdigital.com/hc/articles/212211968-Creating-an-address-book)**.

1. Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.

1. Válassza a **Csatlakozás** lehetőséget a DotDigital kapcsolat inicializálásához.

1. Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.

1. Az Exportálás konfigurálásához válassza a **Tovább** lehetőséget.

## <a name="configure-the-connector"></a>Konfigurálja az összekötőt

1. Az **Adategyeztetés** szakaszban az **E-mail** mezőben jelölje ki az egyesített ügyfélprofil ügyfél e-mail-címét jelképező mezőjét. Ismételje meg ugyanezeket a lépéseket az egyéb választható mezőkön, például az **Utónév**, a **Vezetéknév** , a **Teljes név**, a **Nem** és az **Irányítószám** mezőben.

1. Jelölje ki a szegmenseket, amelyeket exportálni szeretne. Összesen legfeljebb 1 000 000 ügyfélprofilt exportálhat a DotDigitalba.

1. Válassza a **Mentés** parancsot.

## <a name="export-the-data"></a>Az adatok exportálása

[Igény szerint exportálhatja az adatot](export-destinations.md). Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) együtt is lefut. A DotDigitalban most már megtalálhatja a szegmenseket a [DotDigital címjegyzékekben](https://support.dotdigital.com/hc/articles/212211968-Creating-an-address-book).

## <a name="known-limitations"></a>Ismert korlátozások

- Legfeljebb 1 000 000 profilt exportálhat egyszerre a DotDigitalba.
- A DotDigitalba való exportálás csak szegmensekre korlátozódik.
- Az összesen 1 000 000 profillal rendelkező szegmens exportálása a szolgáltatói oldalon megjelenő korlátozások miatt akár 3 óráig is eltarthat. 
- A DotDigitalba exportálható profilok száma függ a DotDigital szerződésről, és korlátozott.

## <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség

Amikor engedélyezi a Dynamics 365 Customer Insights szolgáltatást az adatok DotDigital szolgáltatásba való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat. A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy a DotDigital megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek. További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).
A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.


[!INCLUDE[footer-include](../includes/footer-banner.md)]