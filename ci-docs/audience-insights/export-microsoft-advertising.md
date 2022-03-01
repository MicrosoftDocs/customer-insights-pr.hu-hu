---
title: A Customer Insights adatok exportálása a Microsoft Advertising-szolgáltatásba
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a Microsoft Advertising-szolgáltatásba.
ms.date: 05/12/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: c2ac92de2718cf7f0622b407bf198a7a7e50a37b
ms.sourcegitcommit: 831765a55775d358447cb7ffa56f2c3b85459084
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/01/2021
ms.locfileid: "6124501"
---
# <a name="export-segments-to-microsoft-advertising-preview"></a>Szegmensek exportálása a Microsoft Advertising-szolgáltatásba (előzetes verzió)

Customer Insights szegmensek exportálása a Microsoft Advertising-szolgáltatásba az Ügyfélegyezési célközönségek létrehozásához. Használja ezeket a célközönségeket a hirdetési kampányaihoz.

## <a name="prerequisites"></a>Előfeltételek

-   Egy [Microsoft Advertising-fiók](https://ads.microsoft.com/) és ahhoz tartozó rendszergazdai hitelesítő adatok.
-   Elfogadta az Ügyfélegyeztetés felhasználási feltételeit. 
-   [Konfigurált szegmenseket](segments.md) a célközönség információkban.
-   Az exportált szegmensek egységes ügyfélprofiljai egy e-mail-címmel rendelkező mezőt tartalmaznak.

## <a name="known-limitations"></a>Ismert korlátozások

- Microsoft Advertising exportálásonként legfeljebb 500 ezer profil exportálható.
- A Microsoft Advertising-szolgáltatásba való exportálás a szegmensekre korlátozódik.
- 500 ezer profil exportálása a Microsoft Advertising alkalmazásba akár 10 percet is igénybe vehet. 


## <a name="set-up-the-connection-to-microsoft-advertising"></a>Állítsa be a Microsoft Advertising-szolgáltatással való kapcsolatot

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza a **Microsoft Advertising** lehetőséget a kapcsolat konfigurálásához.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Az alapértelmezett a rendszergazdák. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.

1. Válassza a **Kapcsolat** lehetőséget az Microsoft Advertising kapcsolatának inicializálására.

1. Válassza a **Hitelesítés a Microsoft Advertising alkalmazással** lehetőséget, és adja meg a Microsoft Advertising rendszergazdai hitelesítő adatait.

1. Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

## <a name="configure-an-export"></a>Exportálás konfigurálása

Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz. További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Új exportálás létrehozásához válassza a **Célhely hozzáadása** lehetőséget.

1. A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot a Microsoft Advertising szakaszból. Ha nem látja ezt a szakasznevet, az Ön számára nincs ilyen típusú kapcsolat.

1. Válassza ki az exportálni kívánt szegmenseket. A Microsoft Advertising ügyfélegyeztetés célközönségei automatikusan létrejönnek az exportálásra kiválasztott szegmensek nevével. Minden szegmens külön ügyfélegyeztetési célközönséget eredményez. 

1. Adja meg a **Microsoft Advertising ügyfélazonosítóját és fiókazonosítóját**. Az Ügyfélazonosítót (`cid`) és a Fiókazonosítót (`aid`) az URL-cím paramétereiben találja, amikor bejelentkezett a Microsoft Advertising-szolgáltatásba.

1. Az **Adategyeztetés** szakaszban, az **E-mail** mezőben válassza ki az egységes ügyfélprofil mezőjét az ügyfél e-mail-címével. A szegmenseket exportálni kell a Microsoft Advertising alkalmazásba.

1. Válassza a **Mentés** parancsot.

Az exportálás mentése nem futtatja azonnal az exportálást.

Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut. Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand). 


## <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség

Amikor engedélyezi Dynamics 365 Customer Insights számára, hogy adatokat továbbítson a Microsoft Advertising számára, akkor lehetővé teszi az adatok továbbítását a Dynamics 365 Customer Insights megfelelési határán kívülre is, beleértve az esetlegesen bizalmas adatokat is, például a Személyes adatokat. A Microsoft az Ön utasítására továbbítja az adatokat, de Ön a felelős azért, hogy a Microsoft Advertising megfeleljen az esetleges adatvédelmi vagy biztonsági kötelezettségeknek. További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).

A funkció használatának leállítása érdekében az Ön Dynamics 365 Customer Insights rendszergazdája bármikor eltávolíthatja ezt az exportálási célhelyet.
