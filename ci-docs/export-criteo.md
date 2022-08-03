---
title: Szegmensek exportálása a Criteo-ba (előzetes verzió)
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja Criteo-ba.
ms.date: 07/25/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: d7c8d6f0121fe18a6c886ba3776109a1a592ef33
ms.sourcegitcommit: 594081c82ca385f7143b3416378533aaf2d6d0d3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/27/2022
ms.locfileid: "9195339"
---
# <a name="export-segments-to-criteo-preview"></a>Szegmensek exportálása a Criteo-ba (előzetes verzió)

Exportálja az egyesített ügyfélprofilok szegmenseit kampányok létrehozásához, e-mail marketing biztosításához és meghatározott ügyfélcsoportok használatához a Criteo segítségével.

## <a name="prerequisites"></a>Előfeltételek

- Egy [Criteo Dynamics Retargeting-fiók](https://www.criteo.com/login/) és a megfelelő rendszergazdai hitelesítő adatok.
- [Konfigurált szegmensek](segments.md).
- Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.

## <a name="known-limitations"></a>Ismert korlátozások

- Criteo-ba irányuló exportálásonként akár 1 millió ügyfélprofil is lehet, ami akár 30 percet is igénybe vehet. A Criteo-ba exportálható ügyfélprofilok száma a Criteo-val kötött szerződésétől függ.
- Csak szegmensek.

## <a name="set-up-connection-to-criteo"></a>Kapcsolat beállítása Criteo-val

[!INCLUDE [export-connection-include](includes/export-connection-admn.md)]

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a Kapcsolat **hozzáadása,** majd a Criteo **lehetőséget**.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Alapértelmezés szerint csak a rendszergazdák. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Tekintse át az adatvédelmet és a megfelelőséget, és válassza az [Elfogadom lehetőséget](connections.md#data-privacy-and-compliance)**.**

1. Válassza a Csatlakozás **lehetőséget** a kapcsolat inicializálásához.

1. Válassza a Hitelesítés Criteo-val lehetőséget **,** és adja meg rendszergazdai felhasználónevét és hitelesítő adatait a Criteo-hoz.

1. Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

## <a name="configure-an-export"></a>Exportálás konfigurálása

[!INCLUDE [export-permission-include](includes/export-permission.md)]

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Válassza az Exportálás **hozzáadása lehetőséget**.

1. **A Kapcsolat exportáláshoz** mezőben válasszon ki egy kapcsolatot a Criteo szakaszból. Ha nem érhető el egy kapcsolat sem, akkor forduljon a rendszergazdához.

1. Adja meg az exportálás nevét.

1. Az **Adatok egyeztetése** szakaszban, az **E-mail** mezőben válassza ki az ügyfél e-mail címét jelképező mezőt.

1. Ha szükséges, exportálja **a hirdetőazonosítót és a** **nevet**.

1. Jelölje ki a szegmenseket, amelyeket exportálni szeretne.

1. Válassza a **Mentés** parancsot.

[!INCLUDE [export-saving-include](includes/export-saving.md)]

[!INCLUDE [footer-include](includes/footer-banner.md)]
