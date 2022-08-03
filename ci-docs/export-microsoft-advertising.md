---
title: Szegmensek exportálása a Microsoft Advertising-szolgáltatásba (előzetes verzió)
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a Microsoft Advertising-szolgáltatásba.
ms.date: 07/25/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: conceptual
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 44217e7823ffbe14d232b3e33de1b4ea6ed69dcf
ms.sourcegitcommit: 594081c82ca385f7143b3416378533aaf2d6d0d3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/27/2022
ms.locfileid: "9196535"
---
# <a name="export-segments-to-microsoft-advertising-preview"></a>Szegmensek exportálása a Microsoft Advertising-szolgáltatásba (előzetes verzió)

Customer Insights szegmensek exportálása a Microsoft Advertising-szolgáltatásba az Ügyfélegyezési célközönségek létrehozásához. Használja ezeket a célközönségeket a hirdetési kampányaihoz.

## <a name="prerequisites"></a>Előfeltételek

- Egy [Microsoft Advertising-fiók](https://ads.microsoft.com/) és a megfelelő rendszergazdai hitelesítő adatok.
- Microsoft advertising ügyfél-azonosító és fiókazonosító. Keresse meg az ügyfél-azonosítót (`cid`) és a fiókazonosítót (`aid`) az URL-cím paraméterei között, amikor be van jelentkezve a Microsoft Advertising szolgáltatásba.
- Az Ügyfélegyezés használati feltételeit elfogadjuk.
- [Konfigurált szegmensek](segments.md) a Customer Insights szolgáltatásban.
- Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.

## <a name="known-limitations"></a>Ismert korlátozások

- A Microsoft Advertising szolgáltatásba exportált exportonként akár 500 000 ügyfélprofil is lehet, ami akár 10 percet is igénybe vehet.
- Csak szegmensek.

## <a name="set-up-connection-to-microsoft-advertising"></a>Kapcsolat beállítása a Microsoft-hirdetésekkel

[!INCLUDE [export-connection-include](includes/export-connection-admn.md)]

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a Kapcsolat **hozzáadása,** majd a Microsoft-hirdetések **lehetőséget**.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Az alapértelmezett a rendszergazdák. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Adja meg a **Microsoft advertising ügyfél-azonosítóját**.

1. Tekintse át az adatvédelmet és a megfelelőséget, és válassza az [Elfogadom lehetőséget](connections.md#data-privacy-and-compliance)**.**

1. Válassza a Csatlakozás **lehetőséget** a kapcsolat inicializálásához.

1. Válassza a **Hitelesítés a Microsoft Advertising alkalmazással** lehetőséget, és adja meg a Microsoft Advertising rendszergazdai hitelesítő adatait.

1. Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

## <a name="configure-an-export"></a>Exportálás konfigurálása

[!INCLUDE [export-permission-include](includes/export-permission.md)]

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Válassza az Exportálás **hozzáadása lehetőséget**.

1. A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot a Microsoft Advertising szakaszból. Ha nem érhető el egy kapcsolat sem, akkor forduljon a rendszergazdához.

1. Adja meg az exportálás nevét.

1. Válassza ki az exportálni kívánt szegmenseket. A Microsoft Advertising ügyfélegyeztetés célközönségei automatikusan létrejönnek az exportálásra kiválasztott szegmensek nevével. Minden szegmens külön ügyfélegyeztetési célközönséget eredményez.

1. Adja meg a **Microsoft Advertising ügyfélazonosítóját és fiókazonosítóját**.

1. Az **Adatok egyeztetése** szakaszban, az **E-mail** mezőben válassza ki az ügyfél e-mail címét tartalmazó mezőt.

1. Válassza a **Mentés** parancsot.

[!INCLUDE [export-saving-include](includes/export-saving.md)]

[!INCLUDE [footer-include](includes/footer-banner.md)]
