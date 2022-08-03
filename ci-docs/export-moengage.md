---
title: Szegmensek exportálása a MoEngage szolgáltatásba
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a MoEngage szolgáltatásba.
ms.date: 07/26/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: conceptual
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: ffc591c01a5a9434cde41f2da25fa930a515b8c1
ms.sourcegitcommit: 594081c82ca385f7143b3416378533aaf2d6d0d3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/27/2022
ms.locfileid: "9199220"
---
# <a name="export-segments-to-moengage-preview"></a>Szegmensek exportálása a MoEngage-be (előzetes verzió)

Exportálja az egyesített ügyfélprofilok szegmenseit a MoEngage-be, és használja őket e-mail marketinghez a MoEngage-ben.

## <a name="prerequisites-for-a-connection"></a>Egy kapcsolat előfeltételei

- [MoEngage-fiók](https://www.moengage.com/) és a megfelelő rendszergazdai hitelesítő adatok.
- MoEngage API-kulcs a Beállításokból > API-ból a MoEngage-ben.
- [Konfigurált szegmensek](segments.md) a Customer Insights szolgáltatásban.

## <a name="known-limitations"></a>Ismert korlátozások

- MoEngage-ba való exportálásonként akár 100 000 ügyfélprofil is lehet, ami akár 15 percet is igénybe vehet. A MoEngage-be exportálható ügyfélprofilok száma a MoEngage-szel kötött szerződésétől függ.
- Csak szegmensek.

## <a name="set-up-connection-to-moengage"></a>Kapcsolat beállítása a MoEngage-hez

[!INCLUDE [export-connection-include](includes/export-connection-admn.md)]

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a Kapcsolat **hozzáadása lehetőséget**, majd válassza a MoEngage **lehetőséget** a kapcsolat konfigurálásához.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Adja meg a [MoEngage Data API azonosítóját és API-kulcsát](https://developers.moengage.com/hc/articles/4404674776724-Overview#:~:text=Navigate%20to%20Settings%20%3E%20APIs%20%3E%20DATA,ID%20Password%20%2D%20DATA%20API%20KEY).

1. Tekintse át az adatvédelmet és a megfelelőséget, és válassza az [Elfogadom lehetőséget](connections.md#data-privacy-and-compliance)**.**

1. Válassza a Csatlakozás **lehetőséget** a MoEngage-hez való kapcsolat inicializálásához.

1. Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

## <a name="configure-an-export"></a>Exportálás konfigurálása

[!INCLUDE [export-permission-include](includes/export-permission.md)]

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Új exportálás létrehozásához válassza az **Exportálás hozzáadása** lehetőséget.

1. **A Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot a MoEngage szakaszból. Ha nem látja ezt a szakasznevet, az Ön számára nincs ilyen típusú kapcsolat.

1. Az **Adatok egyeztetése** szakaszban, az **E-mail** mezőben válassza ki az ügyfél e-mail címét jelképező mezőt. Ismételje meg ugyanezeket a lépéseket más választható mezőkkel is.

1. Jelölje ki a szegmenseket, amelyeket exportálni szeretne. Egy vagy több szegmenst hozunk létre ugyanazzal a névvel, mint a MoEngage kiválasztott szegmensei a Szegmensek egyéni **szegmensei** > **alatt**.

1. Válassza a **Mentés** parancsot.

[!INCLUDE [export-saving-include](includes/export-saving.md)]

[!INCLUDE [footer-include](includes/footer-banner.md)]
