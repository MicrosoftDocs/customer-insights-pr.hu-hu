---
title: Szegmensek exportálása az Autopilotba (előzetes verzió)
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja az Autopilotba.
ms.date: 07/25/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: conceptual
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 449d2c5e32697e4a5d2c9dff4a5a1cbdb26aeb4d
ms.sourcegitcommit: 594081c82ca385f7143b3416378533aaf2d6d0d3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/27/2022
ms.locfileid: "9195063"
---
# <a name="export-segments-to-autopilot-preview"></a>Szegmensek exportálása az Autopilotba (előzetes verzió)

Exportálja az egyesített ügyfélprofilok szegmenseit az Autopilotba, és használja őket kampányokhoz és e-mail marketinghez az Autopilotban.

## <a name="prerequisites-for-a-connection"></a>Egy kapcsolat előfeltételei

- Egy [Autopilot-fiók](https://www.autopilothq.com/) és a megfelelő rendszergazdai hitelesítő adatok.
- Egy [Autopilot API-kulcs](https://autopilot.docs.apiary.io/#)
- [Konfigurált szegmensek](segments.md) a Customer Insights szolgáltatásban.
- Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.

## <a name="known-limitations"></a>Ismert korlátozások

- Az Autopilotba való exportálásonként akár 100 000 ügyfélprofil is lehet, ami akár néhány órát is igénybe vehet. Az Autopilotba exportálható ügyfélprofilok száma az Autopilottal kötött szerződéstől függ.
- Csak szegmensek.

## <a name="set-up-connection-to-autopilot"></a>Állítsa be az Autopilottal való kapcsolatot

[!INCLUDE [export-connection-include](includes/export-connection-admn.md)]

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a Kapcsolat **hozzáadása,** majd az Autopilot **lehetőséget**.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Alapértelmezés szerint csak a rendszergazdák. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Adja meg az Autopilot API-kulcsát.

1. Tekintse át az adatvédelmet és a megfelelőséget, és válassza az [Elfogadom lehetőséget](connections.md#data-privacy-and-compliance)**.**

1. Válassza a Csatlakozás **lehetőséget** a kapcsolat inicializálásához.

1. Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

## <a name="configure-an-export"></a>Exportálás konfigurálása

[!INCLUDE [export-permission-include](includes/export-permission.md)]

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Válassza az Exportálás **hozzáadása lehetőséget**.

1. A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot az Autopilot szakaszból. Ha nem érhető el egy kapcsolat sem, akkor forduljon a rendszergazdához.

1. Adja meg az exportálás nevét.

1. Az **Adatok egyeztetése** szakaszban, az **E-mail** mezőben válassza ki az ügyfél e-mail címét jelképező mezőt.

1. Igény szerint exportálhat más mezőket, például **utónév** és **vezetéknév**.

1. Válassza ki azokat a szegmenseket, amelyeket exportálni szeretne, betartva az ismert korlátozásokat.

1. Válassza a **Mentés** parancsot.

[!INCLUDE [export-saving-include](includes/export-saving.md)]

[!INCLUDE [footer-include](includes/footer-banner.md)]
