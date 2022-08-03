---
title: Szegmensek exportálása a Campaign Monitorba (előzetes verzió)
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a Campaign Monitorba.
ms.date: 07/25/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: conceptual
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 3c04fc26dc690cf32b45913257e82b9a0f617185
ms.sourcegitcommit: 594081c82ca385f7143b3416378533aaf2d6d0d3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/27/2022
ms.locfileid: "9196305"
---
# <a name="export-segments-to-campaign-monitor-preview"></a>Szegmensek exportálása a Campaign Monitorba (előzetes verzió)

Exportálja az egyesített ügyfélprofilok szegmensét a Campaign Monitorba, és használja őket marketing-tevékenységekre.

## <a name="prerequisites"></a>Előfeltételek

- Egy [Campaign Monitor-fiók](https://www.campaignmonitor.com/) és a megfelelő rendszergazdai hitelesítő adatok.
- Kampányfigyelői [listaazonosító](https://www.campaignmonitor.com/api/getting-started/#your-list-id).
- Egy [generált API-kulcs](https://www.campaignmonitor.com/api/getting-started/) a Kampányfigyelő fiókbeállításaiból **az** API-lista azonosítójának beszerzéséhez.
- [Konfigurált szegmensek](segments.md) a Customer Insights szolgáltatásban.
- Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.

## <a name="known-limitations"></a>Ismert korlátozások

- A Campaign Monitorba történő exportálásonként akár 1 millió ügyfélprofil is lehet, amely akár 20 percet is igénybe vehet. A Campaign Monitorba exportálható ügyfélprofilok száma a Campaign Monitorral kötött szerződéstől függ.
- Csak szegmensek.

## <a name="set-up-connection-to-campaign-monitor"></a>Kapcsolat beállítása a Campaign Monitor alkalmazáshoz

[!INCLUDE [export-connection-include](includes/export-connection-admn.md)]

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a Kapcsolat **hozzáadása,** majd a Kampányfigyelő **lehetőséget**.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Alapértelmezés szerint csak a rendszergazdák. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Tekintse át az adatvédelmet és a megfelelőséget, és válassza az [Elfogadom lehetőséget](connections.md#data-privacy-and-compliance)**.**

1. Válassza a **Kapcsolat** lehetőséget a Campaign Monitor kapcsolatának inicializálására.

1. Válassza a **Hitelesítés a Campaign Monitorral** lehetőséget, és adja meg a Campaign Monitor rendszergazdai hitelesítő adatait.

1. Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

## <a name="configure-an-export"></a>Exportálás konfigurálása

[!INCLUDE [export-permission-include](includes/export-permission.md)]

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Új exportálás létrehozásához válassza az **Exportálás hozzáadása** lehetőséget.

1. A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot a Campaign Monitor szakaszból. Ha nem érhető el egy kapcsolat sem, akkor forduljon a rendszergazdához.

1. Adja meg az exportálás nevét.

1. Adja meg a **Kampányfigyelő listaazonosítóját**.

1. Az **Adatok egyeztetése** szakaszban, az **E-mail** mezőben válassza ki az ügyfél e-mail címét jelképező mezőt. A szegmenseket exportálni kell a Campaign Monitor alkalmazásba.

1. Jelölje ki a szegmenseket, amelyeket exportálni szeretne.

1. Válassza a **Mentés** parancsot.

[!INCLUDE [export-saving-include](includes/export-saving.md)]

[!INCLUDE [footer-include](includes/footer-banner.md)]
