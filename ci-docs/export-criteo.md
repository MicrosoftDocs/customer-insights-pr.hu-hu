---
title: Ügyfélelemzési adatok exportálása a Criteo-ba
description: További információ a kapcsolat konfigurálásáról és a Criteo-ba való exportálásról.
ms.date: 05/27/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 854f5f0c53f053fc5d742d69a045db1926fec00c
ms.sourcegitcommit: bf65bc0a54cdab71680e658e1617bee7b2c2bb68
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/27/2022
ms.locfileid: "8808791"
---
# <a name="export-segments-to-criteo-preview"></a>Szegmensek exportálása Criteo-ba (előzetes verzió)

Egyesített ügyfélprofilok szegmenseinek exportálása kampányok létrehozásához, e-mail marketing biztosításához és bizonyos ügyfélcsoportok használatához a Criteo segítségével.

## <a name="prerequisites-for-connection"></a>A kapcsolat előfeltételei

-   Rendelkezik [Criteo Dynamics retargeting fiókkal](https://www.criteo.com/login/) és megfelelő rendszergazdai hitelesítő adatokkal.
-   Rendelkezik [konfigurált szegmensekkel](segments.md).
-   Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.

## <a name="known-limitations"></a>Ismert korlátozások

- Akár 1 millió ügyfélprofil exportonként a Criteo-ba.
- A Criteo-ba történő exportálás szegmensekre korlátozódik.
- Az összesen 1 millió ügyfélprofilt vevő szegmensek exportálása akár 30 percet is igénybe vehet. 
- A Criteo-ba exportálható ügyfélprofilok száma a Criteo-val kötött szerződésétől függ és korlátozott.

## <a name="set-up-connection-to-criteo"></a>Kapcsolat beállítása Criteo-val

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza **a Kapcsolat** hozzáadása lehetőséget, és válassza a Criteo **lehetőséget** a kapcsolat konfigurálásához.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Válassza **az** Elfogadom lehetőséget az Adatvédelem és a megfelelőség **megerősítéséhez, és válassza a** Csatlakozás **lehetőséget** a Criteo-val való kapcsolat inicializálásához.

1. Válassza a **Hitelesítés a Criteo-val** lehetőséget, és adja meg admini felhasználónevét és hitelesítő adatait a Criteo számára. 

1. Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

## <a name="configure-an-export"></a>Exportálás konfigurálása

Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz. További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Új exportálás létrehozásához válassza a **Célhely hozzáadása** lehetőséget.

1. A Kapcsolat exportáláshoz **mezőben** válasszon ki egy kapcsolatot a Criteo szakaszból. Ha nem látja ezt a szakasznevet, az Ön számára nincs ilyen típusú kapcsolat. 

1. Az **Adatok egyeztetése** szakaszban, az **E-mail** mezőben válassza ki az ügyfél e-mail címét jelképező mezőt. 

1. A hirdetői azonosítót **és** a nevet is **exportálhatja**

1. Jelölje ki a szegmenseket, amelyeket exportálni szeretne. 

1. Válassza a **Mentés** parancsot.

Az exportálás mentése nem futtatja azonnal az exportálást.

Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut. Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand). 

## <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség

Ha engedélyezi Dynamics 365 Customer Insights az adatok továbbítását a Criteo-nak, engedélyezi az adatok továbbítását a megfelelőségi határokon kívülre Dynamics 365 Customer Insights, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat is. A Microsoft ezeket az adatokat az Ön utasítására továbbítja, de Ön felelős annak biztosításáért, hogy a Criteo eleget tegyen az Esetleges adatvédelmi vagy biztonsági kötelezettségeinek. További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).
A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.


[!INCLUDE[footer-include](includes/footer-banner.md)]
