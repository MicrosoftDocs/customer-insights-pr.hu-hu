---
title: Customer Insights adatok exportálása a Google Adsbe
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a Google Adsbe.
ms.date: 09/27/2021
ms.subservice: audience-insights
ms.topic: how-to
author: pkieffer
ms.author: philk
ms.reviewer: mhart
manager: shellyha
ms.openlocfilehash: 28e2b35c5a47a025b8cdcccdb3f61c79878bf056
ms.sourcegitcommit: e7cdf36a78a2b1dd2850183224d39c8dde46b26f
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/16/2022
ms.locfileid: "8227013"
---
# <a name="export-segments-to-google-ads-preview"></a>Szegmensek exportálása a Google Ads szolgáltatásba (előzetes verzió)

Exportálja az egységes ügyfélprofilok szegmenseit a Google Ads célközönség listára, és használja őket a Google Keresés, a Gmail, YouTube és Google Display Network-ön történő hirdetésnél. 

> [!IMPORTANT]
> Jelenleg csak akkor hozható létre új kapcsolat, és csak akkor exportálhatók az adatok a Google Ads szolgáltatásba, ha már rendelkezik jóváhagyott Google Ads-fejlesztői jogkivonattal. A irányelvváltozások miatt hamarosan frissítjük a Google Ads exportálását, és olyan exportálási lehetőséget kínálunk, amelyhez nem szükséges fejlesztői jogkivonat az élmény folyamatossága és a Google Ads szolgáltatásba való exportálás egyszerűsítése érdekében. Javasoljuk, hogy ne állítson be további kapcsolatokat a Google Ads szolgáltatáshoz annak érdekében, hogy könnyebb legyen áttérni az új exportálási lehetőségre.

## <a name="prerequisites-for-connection"></a>A kapcsolat előfeltételei

-   Rendelkezik [Google Ads-fiókkal](https://ads.google.com/) és a megfelelő rendszergazdai hitelesítő adatokkal.
-   Rendelkezik egy [jóváhagyott Google Ads fejlesztői kóddal](https://developers.google.com/google-ads/api/docs/first-call/dev-token). 
-   Ön megfelel az [Ügyfél megfeleltetési szabályzat](https://support.google.com/adspolicy/answer/6299717) követelményeinek.
-   Ön teljesíti a [remarketing listaméretekre](https://support.google.com/google-ads/answer/7558048) vonatkozó követelményeket.
-   A Google Adsban és a megfelelő azonosítókban meglévő célközönségek találhatók. További információért lásd: [Google Ads-célközönségek](https://support.google.com/google-ads/answer/7558048?hl=en#:~:text=Audience%20lists%20is%20a%20section,Display%20Network%20through%20remarketing%20campaigns.).
-   Rendelkezik [konfigurált szegmensekkel](segments.md).
-   Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőket, amelyek e-mail-címet, utónevet és vezetéknevet tartalmaznak.

## <a name="known-limitations"></a>Ismert korlátozások

- Exportálásonként legfeljebb 1 millió ügyfélprofil kerül a Google Ads fájlba.
- A Google Adsbe való exportálás csak szegmensekre korlátozódik.
- Az összesen 1 millió ügyfélprofilt biztosító szegmensek exportálása a szolgáltatói oldalon korlátozások miatt akár 5 percet is igénybehet. 
- A Google Ads egyeztetése akár 48 óráig is eltarthat.

## <a name="set-up-connection-to-google-ads"></a>Kapcsolat beállítása a Google Adshez

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza a **Google Ads** lehetőséget a kapcsolat konfigurálásához.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Adja meg **[Google Ads ügyfél-azonosítóját](https://support.google.com/google-ads/answer/1704344)**.

1. Adja meg **[a jóváhagyott Google Ads-fejlesztői jogkivonatát](https://developers.google.com/google-ads/api/docs/first-call/dev-token)**.

1. Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.

1. Válassza a **Hitelesítés a Google Ads szolgáltatással** lehetőséget, és adja meg Google Ads-hitelesítő adatait.

1. Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget. 

## <a name="configure-an-export"></a>Exportálás konfigurálása

Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz. További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Új exportálás létrehozásához válassza a **Célhely hozzáadása** lehetőséget.

1. A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot a Google Ads szakaszból. Ha nem látja ezt a szakasznevet, akkor ilyen típusú kapcsolatok nem állnak az Ön rendelkezésére.

1. Adja meg a **[Google Ads célközönség azonosítóját](https://support.google.com/google-ads/answer/7558048?hl=en#:~:text=Audience%20lists%20is%20a%20section,Display%20Network%20through%20remarketing%20campaigns.)**, és válassza a **Csatlakozás** lehetőséget a Google Ads-kapcsolat kezdeményezéséhez.

1. Az **Adatok egyeztetése** szakaszban, az **E-mail** mezőben válassza ki az ügyfél e-mail címét jelképező mezőt.

1. Jelölje ki a szegmenseket, amelyeket exportálni szeretne. Összesen legfeljebb 1 000 000 ügyfélprofilt exportálhat a Google Adsbe.

Az exportálás mentése nem futtatja azonnal az exportálást.

Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut. 

Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand). 

## <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség

Amikor engedélyezi a Dynamics 365 Customer Insights szolgáltatást az adatok Google Ads szolgáltatásba való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat. A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy a Google Ads megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek. További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).
A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
