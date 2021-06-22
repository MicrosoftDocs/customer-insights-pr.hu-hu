---
title: Customer Insights adatok exportálása a DotDigitalbe
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a DotDigitalba.
ms.date: 03/03/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 8b0bda638c9bc7bb9cb2fdb01be11489b44f28a5
ms.sourcegitcommit: 831765a55775d358447cb7ffa56f2c3b85459084
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/01/2021
ms.locfileid: "6124414"
---
# <a name="export-segments-to-dotdigital-preview"></a>Szegmensek exportálása a DotDigitalba (előzetes verzió)

Az egyesített ügyfélprofilok szegmenseit exportálhatja a DotDigital címjegyzékekbe, és használhatja őet kampányokhoz, e-mail-marketinghez és ügyfélszegmensek létrehozásához a DotDigitallal. 

## <a name="prerequisites-for-a-connection"></a>Egy kapcsolat előfeltételei

-   Rendelkezik [DotDigital-fiókkal](https://dotdigital.com/) és a megfelelő rendszergazdai hitelesítő adatokkal.
-   A DotDigitalban és a megfelelő azonosítókban meglévő címjegyzékek találhatók. Az azonosító megtalálhatók az URL-címben, amikor kijelöli és megnyitja a címjegyzéket. További információért lásd: [DotDigital címjegyzékek](https://support.dotdigital.com/hc/articles/212211968-Creating-an-address-book).
-   [Konfigurált szegmensekkel](segments.md) rendelkezik a célközönségi-információkban.
-   Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.

## <a name="known-limitations"></a>Ismert korlátozások

- Legfeljebb 1 000 000 profilt exportálhat egyszerre a DotDigitalba.
- A DotDigitalba való exportálás csak szegmensekre korlátozódik.
- Az összesen 1 000 000 profillal rendelkező szegmens exportálása a szolgáltatói oldalon megjelenő korlátozások miatt akár 3 óráig is eltarthat. 
- A DotDigitalba exportálható profilok száma függ a DotDigital szerződésről, és korlátozott.

## <a name="set-up-connection-to-dotdigital"></a>Állítsa be a DotDigitallal való kapcsolatot

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza a **DotDigital** lehetőséget a kapcsolat konfigurálásához.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Adja meg a **DotDigital felhasználói nevét és a jelszavát**.

1. Adja meg a **[DotDigital címjegyzék-azonosítóját](https://support.dotdigital.com/hc/articles/212211968-Creating-an-address-book)**.

1. Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.

1. Válassza a **Csatlakozás** lehetőséget a DotDigital kapcsolat inicializálásához.

1. Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget. 

## <a name="configure-an-export"></a>Exportálás konfigurálása

Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz. További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Új exportálás létrehozásához válassza a **Célhely hozzáadása** lehetőséget.

1. A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot a DotDigital szakaszból. Ha nem látja ezt a szakasznevet, az Ön számára nincs ilyen típusú kapcsolat.


1. Az **Adategyeztetés** szakaszban az **E-mail** mezőben jelölje ki az egyesített ügyfélprofil ügyfél e-mail-címét jelképező mezőjét. Ismételje meg ugyanezeket a lépéseket az egyéb választható mezőkön, például az **Utónév**, a **Vezetéknév** , a **Teljes név**, a **Nem** és az **Irányítószám** mezőben.

1. Jelölje ki a szegmenseket, amelyeket exportálni szeretne. Összesen legfeljebb 1 000 000 ügyfélprofilt exportálhat a DotDigitalba.

1. Válassza a **Mentés** parancsot.

Az exportálás mentése nem futtatja azonnal az exportálást.

Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut. Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand). 
 
A DotDigitalban most már megtalálhatja a szegmenseket a [DotDigital címjegyzékekben](https://support.dotdigital.com/hc/articles/212211968-Creating-an-address-book).


## <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség

Amikor engedélyezi a Dynamics 365 Customer Insights szolgáltatást az adatok DotDigital szolgáltatásba való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat. A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy a DotDigital megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek. További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).
A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
