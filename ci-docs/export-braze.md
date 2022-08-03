---
title: Szegmensek exportálása Braze-be (előzetes verzió)
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a Braze-be.
ms.date: 07/25/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: conceptual
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 84dc7f13f30e0334d431fe5b5866c7f87e82ab27
ms.sourcegitcommit: 594081c82ca385f7143b3416378533aaf2d6d0d3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/27/2022
ms.locfileid: "9195110"
---
# <a name="export-segments-to-braze-preview"></a>Szegmensek exportálása Braze-be (előzetes verzió)

Exportálja az egyesített ügyfélprofilok szegmenseit a Braze-be, és használja őket marketingtevékenységekhez.

## <a name="prerequisites"></a>Előfeltételek

- Braze-fiók [és](https://www.braze.com/) a megfelelő rendszergazdai hitelesítő adatok.
- Braze [API-kulcs](https://www.braze.com/docs/api/basics/)
- [Konfigurált szegmensek](segments.md) a Customer Insights szolgáltatásban.
- Az exportált szegmensek egyesített ügyfélprofiljai tartalmaznak egy mezőt, amely egy e-mail-címet és egy Braze-ügyfélazonosítót képvisel.

## <a name="known-limitations"></a>Ismert korlátozások

- Akár 1 millió ügyfélprofil a Braze-hez, ami akár 40 percet is igénybe vehet. A Braze-be exportálható ügyfélprofilok száma a Braze-szel kötött szerződésétől függ.
- Csak szegmensek.

## <a name="set-up-connection-to-braze"></a>Kapcsolat beállítása a Braze-hez

[!INCLUDE [export-connection-include](includes/export-connection-admn.md)]

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a Kapcsolat **hozzáadása,** majd a Braze **lehetőséget**.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Alapértelmezés szerint csak a rendszergazdák. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Adja meg a Braze API-kulcsot a bejelentkezés folytatásához.

1. Tekintse át az adatvédelmet és a megfelelőséget, és válassza az [Elfogadom lehetőséget](connections.md#data-privacy-and-compliance)**.**

1. Válassza a Csatlakozás **lehetőséget** a kapcsolat inicializálásához.

1. Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

## <a name="configure-an-export"></a>Exportálás konfigurálása

[!INCLUDE [export-permission-include](includes/export-permission.md)]

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Válassza az Exportálás **hozzáadása lehetőséget**.

1. **A Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot a Braze szakaszból. Ha nem érhető el egy kapcsolat sem, akkor forduljon a rendszergazdához.

1. Adja meg az exportálás nevét.

1. Az **Adatok egyeztetése** szakaszban, az **E-mail** mezőben válassza ki az ügyfél e-mail címét jelképező mezőt. **Az Ügyfél-azonosító** mezőben válassza ki azt a mezőt, amely az ügyfél Braze-azonosítóját jelöli. A Braze szegmensei ugyanazzal a névvel jönnek létre, mint Dynamics 365 Customer Insights a. Az adatok egyeztetéséhez több, opcionális mezőt is kiválaszthat.

1. Válassza ki az exportálni kívánt entitásokat vagy szegmenseket.

1. Válassza a **Mentés** parancsot.

[!INCLUDE [export-saving-include](includes/export-saving.md)]

[!INCLUDE [footer-include](includes/footer-banner.md)]
