---
title: Szegmensek exportálása Klaviyo-ba (előzetes verzió)
description: További információ a kapcsolat konfigurálásához és a Klaviyoba való exportáláshoz.
ms.date: 07/25/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: conceptual
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 6e45ca5827afa29d97a746bd1a474c2346cc32d2
ms.sourcegitcommit: 594081c82ca385f7143b3416378533aaf2d6d0d3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/27/2022
ms.locfileid: "9196765"
---
# <a name="export-segments-to-klaviyo-preview"></a>Szegmensek exportálása Klaviyo-ba (előzetes verzió)

Exportálja az egyesített ügyfélprofilok szegmenseit a Klaviyoba, és használja őket marketingtevékenységekhez.

## <a name="prerequisites"></a>Előfeltételek

- Klaviyo-fiók [és](https://www.klaviyo.com/) a megfelelő rendszergazdai hitelesítő adatok.
- Egy [Klaviyo API-kulcs](https://help.klaviyo.com/hc/articles/115005062267-How-to-Manage-Your-Account-s-API-Keys).
- Klaviyo-lista [azonosító](https://help.klaviyo.com/hc/articles/115005078647-How-to-Find-a-List-ID).
- [Konfigurált szegmensek](segments.md) a Customer Insights szolgáltatásban.
- Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.

## <a name="known-limitations"></a>Ismert korlátozások

- Klaviyo-ba irányuló exportálásonként akár 1 millió ügyfélprofil is lehet, ami akár 20 percet is igénybe vehet. A Klaviyo-ba exportálható ügyfélprofilok száma a Klaviyo-val kötött szerződésétől függ.
- Csak szegmensek.

## <a name="set-up-connection-to-klaviyo"></a>Állítsa be a Klaviyoval való kapcsolatot

[!INCLUDE [export-connection-include](includes/export-connection-admn.md)]

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a Kapcsolat **hozzáadása,** majd a Klaviyo **lehetőséget**.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Alapértelmezés szerint csak a rendszergazdák. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Adja meg a Klaviyo kulcsát a bejelentkezés folytatásához.

1. Tekintse át az adatvédelmet és a megfelelőséget, és válassza az [Elfogadom lehetőséget](connections.md#data-privacy-and-compliance)**.**

1. Válassza a Csatlakozás **lehetőséget** a kapcsolat inicializálásához.

1. Válassza a **Hitelesítés Klaviyóval** lehetőséget, és adja meg a rendszergazdai hitelesítő adatokat az Klaviyóhoz.

1. Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

## <a name="configure-an-export"></a>Exportálás konfigurálása

[!INCLUDE [export-permission-include](includes/export-permission.md)]

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Válassza az Exportálás **hozzáadása lehetőséget**.

1. Az **Exportálási kapcsolat** mezőben válasszon kapcsolatot a Klaviyo szakaszból. Ha nem érhető el egy kapcsolat sem, akkor forduljon a rendszergazdához.

1. Adja meg az exportálás nevét.

1. Adja meg Klaviyo **list azonosítóját**.

1. Az **Adatok egyeztetése** szakaszban, az **E-mail** mezőben válassza ki az ügyfél e-mail címét jelképező mezőt.

1. Jelölje ki a szegmenseket, amelyeket exportálni szeretne.

1. Válassza a **Mentés** parancsot.

[!INCLUDE [export-saving-include](includes/export-saving.md)]

[!INCLUDE [footer-include](includes/footer-banner.md)]