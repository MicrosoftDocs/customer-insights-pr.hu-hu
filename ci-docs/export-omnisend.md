---
title: Szegmensek exportálása az Ominsendbe (előzetes verzió)
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja az Ominsendbe.
ms.date: 07/25/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: conceptual
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: c23d6d3538c4df6006c14064f95379169af06622
ms.sourcegitcommit: 594081c82ca385f7143b3416378533aaf2d6d0d3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/27/2022
ms.locfileid: "9196167"
---
# <a name="export-segments-to-omnisend-preview"></a>Szegmensek exportálása az Ominsendbe (előzetes verzió)

Exportálja az egyesített ügyfélprofilok szegmensét az Ominsendbe, és használja őket marketing-tevékenységekre.

## <a name="prerequisites"></a>Előfeltételek

- Omnisend-fiók [és](https://www.omnisend.com/) a megfelelő rendszergazdai hitelesítő adatok.
- Omnisend [API-kulcs](https://support.omnisend.com/en/articles/1061890-generating-api-key).
- [Konfigurált szegmensek](segments.md) a Customer Insights szolgáltatásban.
- Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.

## <a name="known-limitations"></a>Ismert korlátozások

- Omnisendbe exportálva akár 1 millió ügyfélprofil is lehet, ami akár négy órát is igénybe vehet. Az Omnisend alkalmazásba exportálható ügyfélprofilok száma az Omnisend szolgáltatással kötött szerződéstől függ, és csak korlátozott.
- Csak szegmensek.

## <a name="set-up-connection-to-omnisend"></a>Állítsa be az Ominsenddel való kapcsolatot

[!INCLUDE [export-connection-include](includes/export-connection-admn.md)]

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a Kapcsolat **hozzáadása,** majd az Omnisend **lehetőséget**.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Alapértelmezés szerint csak a rendszergazdák. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Adja meg az Ominsend API-kulcsát.

1. Tekintse át az adatvédelmet és a megfelelőséget, és válassza az [Elfogadom lehetőséget](connections.md#data-privacy-and-compliance)**.**

1. Válassza a Csatlakozás **lehetőséget** a kapcsolat inicializálásához.

1. Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

## <a name="configure-an-export"></a>Exportálás konfigurálása

[!INCLUDE [export-permission-include](includes/export-permission.md)]

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Válassza az Exportálás **hozzáadása lehetőséget**.

1. A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot az Ominsend szakaszból. Ha nem érhető el egy kapcsolat sem, akkor forduljon a rendszergazdához.

1. Adja meg az exportálás nevét.

1. Az **Adatok egyeztetése** szakaszban, az **E-mail** mezőben válassza ki az ügyfél e-mail címét jelképező mezőt.

1. Igény szerint exportálhat utónév, vezetéknév, címet **,** **országot/régiót**, **államot**, várost **és** irányítószámot **,** hogy személyre szabottabb e-maileket hozzon létre.**·** **·** Válassza az **Attribútum hozzáadása** lehetőséget a mezők leképezéséhez.

1. Jelölje ki a szegmenseket, amelyeket exportálni szeretne.

1. Válassza a **Mentés** parancsot.

[!INCLUDE [export-saving-include](includes/export-saving.md)]

[!INCLUDE [footer-include](includes/footer-banner.md)]
