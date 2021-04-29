---
title: Customer Insights adatok exportálása a Facebook Ads Managerbe
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a Facebook Hirdetéskezelő.
ms.date: 04/15/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: phkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: ca32906a98bc734639fb369d6f5a92e8888fd850
ms.sourcegitcommit: 6d5dd572f75ba4c0303ec77c3b74e4318d52705c
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/16/2021
ms.locfileid: "5906813"
---
# <a name="export-segments-list-to-facebook-ads-manager-preview"></a>Szegmenslista exportálása a Facebook Hirdetéskezelő (előzetes verzió)

Az egyesített ügyfélprofilokat tartalmazó szegmensek exportálása a Facebook hirdetéskezelőbe kampányok létrehozásához a Facebook-on és az Instagramon.

## <a name="prerequisites-for-connection"></a>A kapcsolat előfeltételei

- A [**Facebook üzleti fiókot**](https://www.facebook.com/business/learn/lessons/step-by-step-ads-manager-account) tartalmazó [**Facebook hirdetési fiókkal**](https://business.facebook.com/) kell rendelkeznie.
- A [**Facebook hirdetési fiók**](https://www.facebook.com/business/learn/lessons/step-by-step-ads-manager-account) rendszergazdájának kell lennie.

## <a name="known-limitations"></a>Ismert korlátozások

- Akár 10 millió ügyfélprofil exportálásonként a Facebook Hirdetéskezelőbe.
- A Facebook hirdetéskezelőbe való exportálás csak szegmensekre korlátozódik.
- Kizárólag *ügyféllista* típusú célközönségek létrehozása vagy frissítése a Facebookon.
- Az összesen 10 millió profillal rendelkező szegmensek exportálása akár 90 percig is eltarthat.

## <a name="set-up-connection-to-facebook-ads-manager"></a>Kapcsolat beállítása a Facebook Hirdetéskezelőhöz

Ahhoz, hogy a felhasználók exportálást tudjanak létrehozni, a rendszergazdának konfigurálnia kell a szolgáltatás kapcsolatát, és engedélyeznie kell a közreműködőknek a kapcsolat használatát.

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza a **Facebook Hirdetéskezelő** lehetőséget a kapcsolat konfigurálásához.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a **Rendszergazdák** lesz. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Hitelesítés a Facebook-hirdetések használatával: 

   1. Válassza a **Folytatás Facebook-kal** lehetőséget a bejelentkezéshez a Facebook hirdetési fiókjába.

   1. A hitelesítés után engedélyezze a **ads_management** engedélyt a Facebookkal.

   1. Válassza ki a **Facebook hirdetési fiókot**, amellyel dolgozni kíván.

   1. Jelöljön ki egy **Meglévő egyéni célközönséget** a legördülő listából, vagy hozzon létre egy **Új egyéni célközönséget**. További tájékoztatás [**Célközönségek a Facebook hirdetéskezelőben**](https://www.facebook.com/business/help/744354708981227?id=2469097953376494) című témakörben olvashat.
      > [!NOTE]
      > Ezzel az exportálással a Facebookon csak az adott típusú *ügyféllistán* hozhatók létre vagy frissíthetők egyéni célközönségek. Bizonyos esetekben a legördülő menüben különféle típusú egyéni célközönségek jelennek meg. Ha az *ügyféllistától* eltérő típust választ, akkor az exportálás sikertelen lesz. 

1. Tekintse át az **Adatvédelem és a megfelelés** lehetőséget, és válassza az **Elfogadom** lehetőséget.

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

## <a name="configure-an-export"></a>Exportálás konfigurálása

Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz. További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Új exportálás létrehozásához válassza a **Célhely hozzáadása** lehetőséget. 

1. A **Kapcsolat exportáláshoz** lehetőségen válasszon egy kapcsolatot a **Facebook hirdetéskezelőből**. Ha nem látja ezt a szakasznevet, az Ön számára nincs ilyen típusú kapcsolat.

1. A **Kulcsazonosító kiválasztása** mezőben válassza az **E-mail-cím**, **Név és a cím** vagy a **Telefon** lehetőséget, amelyet elküld a Facebook hirdetéskezelőnek. 

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak.

1. Képezze le a megfelelő attribútumokat az egyesített ügyfél entitásból a kiválasztott kulcsazonosítóhoz.
   > [Tipp] A legjobb esély akkor van az egyezésre, ha az **E-mail-cím** lehetőséget választja kulcsazonosítónak. A további azonosítók hozzáadásával javíthatja a megfeleltetést.

1. Válassza az **Attribútum hozzáadása** lehetőséget a több attribútum leképzésének Facebook hirdetéskezelőbe küldéséhez. A Facebook Ads Manager a következő felhasználóbarát neveket használja a leképezéshez: **FN** = **Keresztnév**, **LN** = **Utónév**, **FI** = **Első kezdőbetű**, **PHONE** = **Telefon**, **GEN** = **Nem**, **DOB** = **Születési idő**, **ST** = **Állam**, **CT** = **Város**, **ZIP** = **Irányítószám**, **COUNTRY** = **Ország/régió**

1. Jelölje ki a szegmenseket, amelyeket exportálni szeretne.

1. Válassza a **Mentés** parancsot.

Az exportálás mentése nem futtatja azonnal az exportálást.

Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut. Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand). 

## <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség

Amikor engedélyezi a Dynamics 365 Customer Insights szolgáltatást az adatok Facebook Ads Managerbe való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat. A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy a Facebook Ads megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek. További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).
A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
