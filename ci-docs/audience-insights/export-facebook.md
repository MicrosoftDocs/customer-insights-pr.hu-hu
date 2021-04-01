---
title: Customer Insights adatok exportálása a Facebook Ads Managerbe
description: Megismerkedhet vele, hogyan konfigurálható a Facebook hirdetéskezelő kapcsolata.
ms.date: 06/05/2020
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: phkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 3e2b52fe743563e4bf61d870cbf1718e6c752a67
ms.sourcegitcommit: bae40184312ab27b95c140a044875c2daea37951
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/15/2021
ms.locfileid: "5596685"
---
# <a name="connector-for-facebook-ads-manager-preview"></a>A Facebook csatlakozója összekötője (előzetes verzió)

Az egyesített ügyfélprofilokat tartalmazó szegmensek exportálása a Facebook hirdetéskezelőbe kampányok létrehozásához a Facebook-on és az Instagramon.

## <a name="prerequisites"></a>Előfeltételek

- Olyan [**Facebook hirdetési fiókkal**](https://www.facebook.com/business/learn/lessons/step-by-step-ads-manager-account) kell rendelkeznie, amely egy [**Facebook üzleti fiókot**](https://business.facebook.com/) is tartalmaz.
- A [**Facebook hirdetési fiók**](https://www.facebook.com/business/learn/lessons/step-by-step-ads-manager-account) rendszergazdájának kell lennie.

## <a name="connect-to-facebook-ads-manager"></a>Kapcsolódás a Facebook hirdetéskezelőhöz

1. Válassz a **Rendszergazda** > **Célok exportálása** lehetőséget.

1. A **Facebook hirdetéskezelő** alatt válassza a **Beállítás** lehetőséget.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben az export helyének.

1. Válassza a **Folytatás Facebook-kal** lehetőséget a bejelentkezéshez a Facebook hirdetési fiókjába.

1. A hitelesítés után engedélyezze a **ads_management** engedélyt a Facebookkal.

1. Válassza ki a **Facebook hirdetési fiókot**, amellyel dolgozni kíván.

1. Jelöljön ki egy **Meglévő egyéni célközönséget** a legördülő listából, vagy hozzon létre egy **Új egyéni célközönséget**. További tájékoztatás [**Célközönségek a Facebook hirdetéskezelőben**](https://www.facebook.com/business/help/744354708981227?id=2469097953376494) című témakörben olvashat.

1. Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.

1. Az Exportálás konfigurálásához válassza a **Tovább** lehetőséget.

## <a name="configure-the-connector"></a>Konfigurálja az összekötőt

1. A **Kulcsazonosító kiválasztása** mezőben válassza az **E-mail-cím**, **Név és a cím** vagy a **Telefon** lehetőséget, amelyet elküld a Facebook hirdetéskezelőnek.

1. Képezze le a megfelelő attribútumokat az egyesített ügyfél entitásból a kiválasztott kulcsazonosítóhoz.
   > [Tipp] A legjobb esély akkor van az egyezésre, ha az **E-mail-cím** lehetőséget választja kulcsazonosítónak. A további azonosítók hozzáadásával javíthatja a megfeleltetést.

1. Válassza az **Attribútum hozzáadása** lehetőséget , ha további attribútumokat szeretne leképezni a Facebook hirdetéskezelőnek. A Facebook Ads Manager a következő felhasználóbarát neveket használja a leképezéshez: **FN** = **Keresztnév**, **LN** = **Utónév**, **FI** = **Első kezdőbetű**, **PHONE** = **Telefon**, **GEN** = **Nem**, **DOB** = **Születési idő**, **ST** = **Állam**, **CT** = **Város**, **ZIP** = **Irányítószám**, **COUNTRY** = **Ország/régió**

1. Jelölje ki a szegmenseket, amelyeket exportálni szeretne.

1. Válassza a **Mentés** parancsot.

## <a name="export-the-data"></a>Az adatok exportálása

[Igény szerint exportálhatja az adatot](export-destinations.md). Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) együtt is lefut.

## <a name="known-limitations"></a>Ismert korlátozások

- Akár 10 millió ügyfélprofil exportálásonként a Facebook Hirdetéskezelőbe 
- A Facebook hirdetéskezelőbe való exportálás csak szegmensekre korlátozódik
- Az összesen 10 millió profillal rendelkező szegmensek exportálása akár 90 percig is eltarthat

## <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség

Amikor engedélyezi a Dynamics 365 Customer Insights szolgáltatást az adatok Facebook Ads Managerbe való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat. A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy a Facebook Ads megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek. További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).
A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.


[!INCLUDE[footer-include](../includes/footer-banner.md)]