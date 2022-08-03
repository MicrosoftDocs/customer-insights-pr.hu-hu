---
title: Szegmensek exportálása a DotDigitalba (előzetes verzió)
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a DotDigitalba.
ms.date: 07/25/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: cabaea84e31f8fe97bc558a8dca8d93bc40f43b7
ms.sourcegitcommit: 594081c82ca385f7143b3416378533aaf2d6d0d3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/27/2022
ms.locfileid: "9196075"
---
# <a name="export-segments-to-dotdigital-preview"></a>Szegmensek exportálása a DotDigitalba (előzetes verzió)

Az egyesített ügyfélprofilok szegmenseit exportálhatja a DotDigital címjegyzékekbe, és használhatja őet kampányokhoz, e-mail-marketinghez és ügyfélszegmensek létrehozásához a DotDigitallal.

## <a name="prerequisites"></a>Előfeltételek

- Egy [DotDigital fiók](https://dotdigital.com/) és egy [API-felhasználó](https://support.dotdigital.com/hc/articles/115001718730-How-do-I-create-an-API-user).
- DotDigital azonosító egy [új](https://support.dotdigital.com/hc/articles/212211968-Creating-an-address-book) vagy meglévő címjegyzékből a DotDigitalban. Az azonosító megtalálhatók az URL-címben, amikor kijelöli és megnyitja a címjegyzéket.
- [Konfigurált szegmensek](segments.md) a Customer Insights szolgáltatásban.
- Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.

## <a name="known-limitations"></a>Ismert korlátozások

- Akár 1 millió ügyfélprofil a DotDigitalba történő exportálásonként, amely akár három órát is igénybe vehet a szolgáltatói oldal korlátai miatt. A DotDigitalba exportálható ügyfélprofilok száma a DotDigitallal kötött szerződésétől függ.
- Csak szegmensek.

## <a name="set-up-connection-to-dotdigital"></a>Állítsa be a DotDigitallal való kapcsolatot

[!INCLUDE [export-connection-include](includes/export-connection-admn.md)]

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a Kapcsolat hozzáadása, **majd a DotDigital lehetőséget** **.**

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Alapértelmezés szerint csak a rendszergazdák. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Adja meg a **DotDigital API-felhasználói nevét és a jelszavát**.

1. Adja meg a **DotDigital címjegyzék azonosítóját**.

1. Tekintse át az adatvédelmet és a megfelelőséget, és válassza az [Elfogadom lehetőséget](connections.md#data-privacy-and-compliance)**.**

1. Válassza a Csatlakozás **lehetőséget** a kapcsolat inicializálásához.

1. Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

## <a name="configure-an-export"></a>Exportálás konfigurálása

[!INCLUDE [export-permission-include](includes/export-permission.md)]

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Válassza az Exportálás **hozzáadása lehetőséget**.

1. A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot a DotDigital szakaszból. Ha nem érhető el egy kapcsolat sem, akkor forduljon a rendszergazdához.

1. Adja meg az exportálás nevét.

1. Az **Adatok egyeztetése** szakaszban, az **E-mail** mezőben válassza ki az ügyfél e-mail címét jelképező mezőt.

1. Ha szükséges, exportálja **utónév**, **vezetéknév**, **Teljes név**, **Nem** és **Irányítószám.**

1. Jelölje ki a szegmenseket, amelyeket exportálni szeretne.

1. Válassza a **Mentés** parancsot.

[!INCLUDE [export-saving-include](includes/export-saving.md)]

A DotDigitalban keresse meg szegmenseit a DotDigital [címjegyzékekben](https://support.dotdigital.com/hc/articles/212211968-Creating-an-address-book).

[!INCLUDE [footer-include](includes/footer-banner.md)]
