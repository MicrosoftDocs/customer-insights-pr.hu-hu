---
title: Customer Insights-adatok exportálása a Snapchatre
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a Snapchatbe.
ms.date: 06/08/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: conceptual
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: d64b482c322af8632e29ec41d6e34c390c5e646c
ms.sourcegitcommit: 8e9f0a9693fd8d91ad0227735ff03688fef5406f
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/10/2022
ms.locfileid: "8947279"
---
# <a name="export-segments-to-snapchat-preview"></a>Szegmensek exportálása a Snapchatbe (előzetes verzió)

Exportálja az egyesített ügyfélprofilok szegmensét a Snapchatbe, és használja őket hirdetési célokra. 

## <a name="prerequisites-for-a-connection"></a>Egy kapcsolat előfeltételei

-   Van egy [Snapchat Business fiókja](https://business.snapchat.com/), egy [Snapchat Ads fiókja](https://ads.snapchat.com/), és megfelelő rendszergazdai hitelesítő adatai. Legalább egy szervezeti fiók tagjának és egy adott Hirdetési fiók Adatkezelőjének kell lennie. 
-   Legalább egy célközönség van a Snapchatben célközönség SAM (Snap célközönség Match) típusú kezelőben. 
-   [A szegmenseket](segments.md) a Customer Insights szolgáltatásban konfigurálta.
-   Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.

## <a name="known-limitations"></a>Ismert korlátozások

- A Snapchatbe való exportálás a szegmensekre korlátozódik.
- 1 millió ügyfélprofil exportálása a Snapchat szolgáltatásba akár 15 percet is igénybe vehet. 

## <a name="set-up-connection-to-snapchat"></a>Állítsa be a Snapchettel való kapcsolatot

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza a **Snapchat** lehetőséget a kapcsolat konfigurálásához.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.

1. Válassza a **Kapcsolat** lehetőséget a Snapchat kapcsolatának inicializálására.

1. Válassza a **Hitelesítés a Snapchattel** lehetőséget, és adja meg a Snapchat rendszergazdai hitelesítő adatait. 

1. Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

## <a name="configure-an-export"></a>Exportálás konfigurálása

Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz. További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Új exportálás létrehozásához válassza a **Célhely hozzáadása** lehetőséget.

1. A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot a Snapchat szakaszból. Ha nem látja ezt a szakasznevet, az Ön számára nincs ilyen típusú kapcsolat.

1. Adja meg a [**Snapchat szegmens / célközönség azonosítót**](https://businesshelp.snapchat.com/s/article/custom-audiences). A célközönség azonosítója megtalálható az URL-ben, miután kiválasztotta a célközönség a Snapchat célközönség Manager alkalmazásban. 

1. Az **Adatok egyeztetése** szakaszban, az **E-mail** mezőben válassza ki az ügyfél e-mail címét jelképező mezőt. A szegmenseket exportálni kell a Snapchat alkalmazásba.

1. Jelölje ki a szegmenseket, amelyeket exportálni szeretne. 

1. Válassza a **Mentés** parancsot.

Az exportálás mentése nem futtatja azonnal az exportálást.

Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut. Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand). 


## <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség

Amikor engedélyezi Dynamics 365 Customer Insightst, hogy adatokat továbbítson a Snapchatnek, akkor lehetővé teszi az adatok továbbítását a Dynamics 365 Customer Insights megfelelési határán kívülre is, beleértve az esetlegesen bizalmas adatokat is, például a Személyes adatokat. A Microsoft az Ön utasítására továbbítja az adatokat, de Ön a felelős azért, hogy a Snapchat megfeleljen az esetleges adatvédelmi vagy biztonsági kötelezettségeknek. További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).

A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.
