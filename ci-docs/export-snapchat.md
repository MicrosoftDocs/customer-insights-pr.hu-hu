---
title: Szegmensek exportálása a Snapchatbe (előzetes verzió)
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a Snapchatbe.
ms.date: 07/25/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: conceptual
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 85443dcb54ebd58182997fbb56a738901f2a051f
ms.sourcegitcommit: 594081c82ca385f7143b3416378533aaf2d6d0d3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/27/2022
ms.locfileid: "9195385"
---
# <a name="export-segments-to-snapchat-preview"></a>Szegmensek exportálása a Snapchatbe (előzetes verzió)

Exportálja az egyesített ügyfélprofilok szegmensét a Snapchatbe, és használja őket hirdetési célokra.

## <a name="prerequisites"></a>Előfeltételek

- Snapchat [Business-fiók](https://business.snapchat.com/), [Snapchat-hirdetési fiók](https://ads.snapchat.com/) és a megfelelő rendszergazdai hitelesítő adatok. Legalább egy adott Hirdetési fiók Szervezeti fiókjának és Adatkezelőjének kell lennie.
- Legalább egy célközönség a Snapchatben célközönség SAM (Snap célközönség Match) típusú kezelője.
- A [Snapchat szegmens / célközönség azonosító](https://businesshelp.snapchat.com/s/article/custom-audiences). A célközönség azonosítója megtalálható az URL-ben, miután kiválasztotta a célközönség a Snapchat célközönség Manager alkalmazásban.
- [Konfigurált szegmensek](segments.md) a Customer Insights szolgáltatásban.
- Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.

## <a name="known-limitations"></a>Ismert korlátozások

- Akár 1 millió ügyfélprofil is lehet, amelyek elkészítése akár 15 percet is igénybe vehet.
- Csak szegmensek.

## <a name="set-up-connection-to-snapchat"></a>Állítsa be a Snapchettel való kapcsolatot

[!INCLUDE [export-connection-include](includes/export-connection-admn.md)]

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a Kapcsolat **hozzáadása lehetőséget**, majd válassza a Snapchat **lehetőséget**.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Alapértelmezés szerint csak a rendszergazdák. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Tekintse át az adatvédelmet és a megfelelőséget, és válassza az [Elfogadom lehetőséget](connections.md#data-privacy-and-compliance)**.**

1. Válassza a Csatlakozás **lehetőséget** a kapcsolat inicializálásához.

1. Válassza a **Hitelesítés a Snapchattel** lehetőséget, és adja meg a Snapchat rendszergazdai hitelesítő adatait.

1. Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

## <a name="configure-an-export"></a>Exportálás konfigurálása

[!INCLUDE [export-permission-include](includes/export-permission.md)]

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Válassza az Exportálás **hozzáadása lehetőséget**.

1. A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot a Snapchat szakaszból. Ha nem érhető el egy kapcsolat sem, akkor forduljon a rendszergazdához.

1. Adja meg az exportálás nevét.

1. Adja meg a **Snapchat szegmens / célközönség azonosítót**.

1. Az **Adatok egyeztetése** szakaszban, az **E-mail** mezőben válassza ki az ügyfél e-mail címét jelképező mezőt.

1. Jelölje ki a szegmenseket, amelyeket exportálni szeretne.

1. Válassza a **Mentés** parancsot.

[!INCLUDE [export-saving-include](includes/export-saving.md)]

[!INCLUDE [footer-include](includes/footer-banner.md)]
