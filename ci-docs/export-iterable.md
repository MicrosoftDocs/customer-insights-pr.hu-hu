---
title: Szegmensek exportálása Iterable formátumba (előzetes verzió)
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja az Iterable-be.
ms.date: 07/25/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: conceptual
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: ccf10b6e3a28a75f9d1bd3d8da3bf870ebc2b1b2
ms.sourcegitcommit: 594081c82ca385f7143b3416378533aaf2d6d0d3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/27/2022
ms.locfileid: "9195432"
---
# <a name="export-segments-to-iterable-preview"></a>Szegmensek exportálása Iterable formátumba (előzetes verzió)

Exportálja az egyesített ügyfélprofilok szegmenseit az Iterable fájlba, és használja őket marketingtevékenységekhez.

## <a name="prerequisites"></a>Előfeltételek

- Iterable [fiók](https://iterable.com/) és a megfelelő rendszergazdai hitelesítő adatok.
- Iterálható [API-kulcs](https://support.iterable.com/hc/en-us/articles/360043464871)
- [Konfigurált szegmensek](segments.md) a Customer Insights szolgáltatásban.
- Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.

## <a name="known-limitations"></a>Ismert korlátozások

- Akár 1 millió ügyfélprofil is az Iterable-hez, ami akár 30 percet is igénybe vehet. Az Iterable-be exportálható ügyfélprofilok száma az Iterable-vel kötött szerződéstől függ.
- Csak szegmensek.

## <a name="set-up-connection-to-iterable"></a>Kapcsolat beállítása az Iterable-hez

[!INCLUDE [export-connection-include](includes/export-connection-admn.md)]

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a Kapcsolat **hozzáadása,** majd az Iterable **lehetőséget**.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Alapértelmezés szerint csak a rendszergazdák. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Adja meg az Iterable API-kulcsot a további bejelentkezéshez.

1. Tekintse át az adatvédelmet és a megfelelőséget, és válassza az [Elfogadom lehetőséget](connections.md#data-privacy-and-compliance)**.**

1. Válassza a Csatlakozás **lehetőséget** a kapcsolat inicializálásához.

1. Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

## <a name="configure-an-export"></a>Exportálás konfigurálása

[!INCLUDE [export-permission-include](includes/export-permission.md)]

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Válassza az Exportálás **hozzáadása lehetőséget**.

1. **A Kapcsolat exportáláshoz** mezőben válasszon ki egy kapcsolatot az Iterable szakaszból. Ha nem érhető el egy kapcsolat sem, akkor forduljon a rendszergazdához.

1. Adja meg az exportálás nevét.

1. Az **Adatok egyeztetése** szakaszban, az **E-mail** mezőben válassza ki az ügyfél e-mail címét jelképező mezőt. Az Iterable-ben létrehozott lista pontosan ugyanazt a nevet kapja, mint a szegmens neve a Dynamics 365 Customer Insights.

1. Jelölje ki a szegmenseket, amelyeket exportálni szeretne.

1. Válassza a **Mentés** parancsot.

[!INCLUDE [export-saving-include](includes/export-saving.md)]

[!INCLUDE [footer-include](includes/footer-banner.md)]
