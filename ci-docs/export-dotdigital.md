---
title: Szegmensek exportálása a DotDigitalba (előzetes verzió)
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a DotDigitalba.
ms.date: 10/08/2021
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: af0cce4edb9d47247c79ae08491366349da98b1c
ms.sourcegitcommit: dca46afb9e23ba87a0ff59a1776c1d139e209a32
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/29/2022
ms.locfileid: "9082932"
---
# <a name="export-segments-to-dotdigital-preview"></a>Szegmensek exportálása a DotDigitalba (előzetes verzió)

Az egyesített ügyfélprofilok szegmenseit exportálhatja a DotDigital címjegyzékekbe, és használhatja őet kampányokhoz, e-mail-marketinghez és ügyfélszegmensek létrehozásához a DotDigitallal. 

## <a name="prerequisites-for-a-connection"></a>Egy kapcsolat előfeltételei

-   [DotDigital fiókja](https://dotdigital.com/) van, és [API-felhasználót](https://support.dotdigital.com/hc/articles/115001718730-How-do-I-create-an-API-user) hozott létre. Kapcsolat létrehozásához az API-felhasználó hitelesítő adatait kell használnia
-   A DotDigitalban és a megfelelő azonosítókban meglévő címjegyzékek találhatók. Az azonosító megtalálhatók az URL-címben, amikor kijelöli és megnyitja a címjegyzéket. További információért lásd: [DotDigital címjegyzékek](https://support.dotdigital.com/hc/articles/212211968-Creating-an-address-book).
-   [A szegmenseket](segments.md) a Customer Insights szolgáltatásban konfigurálta.
-   Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.

## <a name="known-limitations"></a>Ismert korlátozások

- Exportálásonként legfeljebb 1 millió ügyfélprofil kerül a DotDigital fájlba.
- A DotDigitalba való exportálás csak szegmensekre korlátozódik.
- Az összesen 1 millió ügyfélprofilt biztosító szegmensek exportálása a szolgáltatói oldalon korlátozások miatt akár 3 órát is igénybehet. 
- A DotDigital alkalmazásba exportálható ügyfélprofilok száma a DotDigitallel kötött szerződéstől függ, és csak korlátozott.

## <a name="set-up-connection-to-dotdigital"></a>Állítsa be a DotDigitallal való kapcsolatot

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza a **DotDigital** lehetőséget a kapcsolat konfigurálásához.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Adja meg a **DotDigital API-felhasználói nevét és a jelszavát**. 

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


1. Az **Adatok egyeztetése** szakaszban, az **E-mail** mezőben válassza ki az ügyfél e-mail címét jelképező mezőt. Ismételje meg ugyanezeket a lépéseket az egyéb választható mezőkön, például az **Utónév**, a **Vezetéknév** , a **Teljes név**, a **Nem** és az **Irányítószám** mezőben.

1. Jelölje ki a szegmenseket, amelyeket exportálni szeretne. Összesen legfeljebb 1 000 000 ügyfélprofilt exportálhat a DotDigitalba.

1. Válassza a **Mentés** parancsot.

Az exportálás mentése nem futtatja azonnal az exportálást.

Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut. Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand). 
 
A DotDigitalban most már megtalálhatja a szegmenseket a [DotDigital címjegyzékekben](https://support.dotdigital.com/hc/articles/212211968-Creating-an-address-book).


## <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség

Amikor engedélyezi a Dynamics 365 Customer Insights szolgáltatást az adatok DotDigital szolgáltatásba való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat. A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy a DotDigital megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek. További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).
A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.


[!INCLUDE [footer-include](includes/footer-banner.md)]
