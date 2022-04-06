---
title: Customer Insights adatok exportálása a Marketóba
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a Marketoba.
ms.date: 10/08/2021
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: d56ed779c342bb0855ee84d949f8d3ca604b92c1
ms.sourcegitcommit: a5e4503cf9ce0cea562bab9389748d8ca1451f9d
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/25/2022
ms.locfileid: "8487518"
---
# <a name="export-segments-to-marketo-preview"></a>Szegmensek exportálása a Marketoba (előzetes verzió)

Az egyesített ügyfélprofilok szegmensei exportálásának felhasználásával kampányokat hozhat létre, e-mail-marketing szolgáltatást biztosíthat és előnyt kovácsolhat az ügyfelek meghatározott csoportjából a Marketo szolgáltatással.

## <a name="prerequisites-for-connection"></a>A kapcsolat előfeltételei

-   Rendelkezik [Marketo-fiókkal](https://login.marketo.com/) és a megfelelő rendszergazdai hitelesítő adatokkal.
-   A Marketóban és a megfelelő azonosítókban meglévő listák találhatók. További tájékoztatásért keresse fel a [Marketo listák](https://docs.marketo.com/display/public/DOCS/Understanding+Static+Lists) webhelyet.
-   Rendelkezik [konfigurált szegmensekkel](segments.md).
-   Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.

## <a name="known-limitations"></a>Ismert korlátozások

- Exportálásonként legfeljebb 1 millió ügyfélprofil kerül a Marketo fájlba.
- A Marketoba való exportálás csak szegmensekre korlátozódik.
- Az összesen 1 millió ügyfélprofilt vevő szegmensek exportálása akár 3 órát is igénybehat. 
- A Marketo alkalmazásba exportálható ügyfélprofilok száma a Marketoval kötött szerződéstől függ, és csak korlátozott.

## <a name="set-up-connection-to-marketo"></a>Állítsa be a Marketoval való kapcsolatot

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza a **Marketo** lehetőséget a kapcsolat konfigurálásához.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Adja meg a **[Marketo ügyfél-azonosítót, titkos ügyfélkódot és REST végpont eszköznevét](https://developers.marketo.com/rest-api/authentication/)**. A REST-végpont eszköznév csak eszköznév, a `https://` tag nélkül. Példa: `xyz-abc-123.mktorest.com`. 

1. Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez, majd válassza a **Csatlakozás** lehetőséget a Marketo kapcsolat inicializálásához.

1. Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

## <a name="configure-an-export"></a>Exportálás konfigurálása

Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz. További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Új exportálás létrehozásához válassza a **Célhely hozzáadása** lehetőséget.

1. A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot a Marketo szakaszból. Ha nem látja ezt a szakasznevet, az Ön számára nincs ilyen típusú kapcsolat.

1. Adja meg a **[Marketo-listaazonosítót](https://docs.marketo.com/display/public/DOCS/Understanding+Static+Lists)**. A listaazonosító tisztán numerikus érték. Ha például a Marketo-listaazonosító ST12345A7, akkor távolítsa el a számok előtt és után lévő karaktereket, és csak az `12345` értéket adja meg. 

1. **Az Adategyeztetés** szakaszban jelöljön ki legalább egy mezőt, amely az ügyfél e-mail címét vagy az ügyfél Marketo azonosítóját jelöli. 

1. Tetszés szerint exportálhatja az **Utónév**, **Vezetéknév**, **Város**, **Megye** és **Ország/Régió** lehetőségeket, hogy személyre szabottabb e-maileket hozzon létre. Válassza az **Attribútum hozzáadása** lehetőséget a mezők leképezéséhez.

1. Jelölje ki a szegmenseket, amelyeket exportálni szeretne. Összesen legfeljebb 1 000 000 ügyfélprofilt exportálhat a Marketóba.

1. Válassza a **Mentés** parancsot.

Az exportálás mentése nem futtatja azonnal az exportálást.

Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut. Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand). A Marketóban most már megtalálhatja a szegmenseket a [Marketo listában](https://docs.marketo.com/display/public/DOCS/Understanding+Static+Lists).


## <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség

Amikor engedélyezi az Dynamics 365 Customer Insights szolgáltatást az adatok Marketoba való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat. A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy az Marketo megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek. További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).
A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
