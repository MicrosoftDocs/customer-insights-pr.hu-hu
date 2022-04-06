---
title: Customer Insights adatok exportálása a Google Adsbe
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a Google Adsbe.
ms.date: 03/31/2022
ms.subservice: audience-insights
ms.topic: how-to
author: pkieffer
ms.author: philk
ms.reviewer: mhart
manager: shellyha
ms.openlocfilehash: 7a85237f7aff564d6b540b2c11553a52f875fac4
ms.sourcegitcommit: 5bd07f3a1288f003704acd576741cf6aedc1ac33
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/31/2022
ms.locfileid: "8523803"
---
# <a name="export-segments-to-google-ads-preview"></a>Szegmensek exportálása a Google Ads szolgáltatásba (előzetes verzió)

Exportálja az egységes ügyfélprofilok szegmenseit a Google Ads célközönség listára, és használja őket a Google Keresés, a Gmail, YouTube és Google Display Network-ön történő hirdetésnél. 


## <a name="prerequisites-for-connection"></a>A kapcsolat előfeltételei

-   Rendelkezik [Google Ads-fiókkal](https://ads.google.com/) és a megfelelő rendszergazdai hitelesítő adatokkal.
-   Ön megfelel az [Ügyfél megfeleltetési szabályzat](https://support.google.com/adspolicy/answer/6299717) követelményeinek.
-   Ön teljesíti a [remarketing listaméretekre](https://support.google.com/google-ads/answer/7558048) vonatkozó követelményeket.
-   Rendelkezik [konfigurált szegmensekkel](segments.md).
-   Az exportált szegmensek egységes ügyfélprofiljai e-mail címet, telefont, mobil hirdetői azonosítót, harmadik fél felhasználói azonosítóját vagy címét képviselő mezőket tartalmaznak.

## <a name="known-limitations"></a>Ismert korlátozások

- A Google Adsbe való exportálás csak szegmensekre korlátozódik.
- Az összesen 1 millió ügyfélprofilt biztosító szegmensek exportálása a szolgáltatói oldalon korlátozások miatt akár 30 percet is igénybehet. 
- A Google Ads egyeztetése akár 48 óráig is eltarthat.

## <a name="set-up-connection-to-google-ads"></a>Kapcsolat beállítása a Google Adshez

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza a **Google Ads** lehetőséget a kapcsolat konfigurálásához.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Adja meg **[Google Ads ügyfél-azonosítóját](https://support.google.com/google-ads/answer/1704344)**.

1. Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.

1. Válassza a **Hitelesítés a Google Ads szolgáltatással** lehetőséget, és adja meg Google Ads-hitelesítő adatait.

1. Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget. 

## <a name="configure-an-export"></a>Exportálás konfigurálása

Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz. További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Új exportálás létrehozásához válassza a **Célhely hozzáadása** lehetőséget.

1. A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot a Google Ads szakaszból. Ha nem látja ezt a szakasznevet, akkor ilyen típusú kapcsolatok nem állnak az Ön rendelkezésére.

1. Ha új célközönség szeretne létrehozni, hagyja üresen a Google célközönség azonosító mezőt. Automatikusan létrehozunk egy új célközönség a Google Ads-fiókjában, és az exportált szegmens nevét használjuk. Ha frissíteni szeretne egy meglévő Google Ads-célközönség, adja meg [Google Ads-célközönség azonosítóját](https://support.google.com/google-ads/answer/7558048?hl=en#:~:text=Audience%20lists%20is%20a%20section,Display%20Network%20through%20remarketing%20campaigns.)

1. **Az Adategyeztetés** szakaszban jelöljön ki egy vagy több exportálni kívánt adatmezőt, és válassza ki azt a mezőt, amely a Megfelelő adatmezőket jelöli a Customer Insights alkalmazásban.

1. Jelölje ki a szegmenseket, amelyeket exportálni szeretne. 

Az exportálás mentése nem futtatja azonnal az exportálást.

Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut. 

Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand). 

## <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség

Amikor engedélyezi a Dynamics 365 Customer Insights szolgáltatást az adatok Google Ads szolgáltatásba való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat. A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy a Google Ads megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek. További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).
A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
