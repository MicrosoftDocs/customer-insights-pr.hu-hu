---
title: Szegmensek exportálása a RollWorksba (előzetes verzió)
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a RollWorksba.
ms.date: 07/25/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: conceptual
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: e13aeca4ee5309f85e7de2986cd1a2ba5d2992fb
ms.sourcegitcommit: 594081c82ca385f7143b3416378533aaf2d6d0d3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/27/2022
ms.locfileid: "9195615"
---
# <a name="export-segments-to-rollworks-preview"></a>Szegmensek exportálása a RollWorksba (előzetes verzió)

Exportálja az egyesített ügyfélprofilok szegmensét a RollWorksba, és használja őket hirdetési célokra.

## <a name="prerequisites"></a>Előfeltételek

- Egy [RollWorks-fiók](https://www.rollworks.com/) és a megfelelő rendszergazdai hitelesítő adatok.
- RollWorks [hirdetői azonosító](https://help.adroll.com/hc/articles/212011838-Advertiser-Profiles).
- [Konfigurált szegmensek](segments.md) a Customer Insights szolgáltatásban.
- Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.

## <a name="known-limitations"></a>Ismert korlátozások

- Akár 250 000 ügyfélprofil is exportálható a RollWorksbe, ami akár 10 percet is igénybe vehet. A RollWorksbe exportálható ügyfélprofilok száma a RollWorks-szel kötött szerződéstől függ.
- Csak szegmensek.

## <a name="set-up-connection-to-rollworks"></a>Állítsa be a RollWorksszal való kapcsolatot

[!INCLUDE [export-connection-include](includes/export-connection-admn.md)]

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a Kapcsolat **hozzáadása,** majd a RollWorks **lehetőséget**.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása.  Alapértelmezés szerint csak a rendszergazdák. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Tekintse át az adatvédelmet és a megfelelőséget, és válassza az [Elfogadom lehetőséget](connections.md#data-privacy-and-compliance)**.**

1. Válassza a Csatlakozás **lehetőséget** a kapcsolat inicializálásához.

1. Válassza a **Hitelesítés a RollWorksszel** lehetőséget, és adja meg a RollWorks rendszergazdai hitelesítő adatait.

1. Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

## <a name="configure-an-export"></a>Exportálás konfigurálása

[!INCLUDE [export-permission-include](includes/export-permission.md)]

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Válassza az Exportálás **hozzáadása lehetőséget**.

1. A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot a RollWorks szakaszból. Ha nem érhető el egy kapcsolat sem, akkor forduljon a rendszergazdához.

1. Adja meg az exportálás nevét.

1. Add meg a RollWorks hirdetői **azonosítódat**.

1. Az **Adatok egyeztetése** szakaszban, az **E-mail** mezőben válassza ki az ügyfél e-mail címét jelképező mezőt.

1. Jelölje ki a szegmenseket, amelyeket exportálni szeretne.

1. Válassza a **Mentés** parancsot.

[!INCLUDE [export-saving-include](includes/export-saving.md)]

[!INCLUDE [footer-include](includes/footer-banner.md)]
