---
title: Szegmensek exportálása a Mailchimpbe (előzetes verzió)
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a Mailchimpbe.
ms.date: 07/25/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 54aec10e24b6356e2e4317cf33e740a1a086a2dd
ms.sourcegitcommit: 594081c82ca385f7143b3416378533aaf2d6d0d3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/27/2022
ms.locfileid: "9196857"
---
# <a name="export-segments-to-mailchimp-preview"></a>Szegmensek exportálása a Mailchimpbe (előzetes verzió)

Az egyesített ügyfélprofilok szegmenseinek Mailchimpbe való exportálásával hírleveleket és e-mail-kampányokat hozhat létre.

## <a name="prerequisites"></a>Előfeltételek

- Egy [Mailchimp-fiók](https://mailchimp.com/) és a megfelelő rendszergazdai hitelesítő adatok.
- [Meglévő közönségek a Mailchimpben](https://mailchimp.com/help/create-audience/) és a megfelelő [célközönség-azonosítókban](https://mailchimp.com/help/find-audience-id/).
- [Konfigurált szegmensek](segments.md).
- Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.

## <a name="known-limitations"></a>Ismert korlátozások

- Akár 1 millió ügyfélprofil a Mailchimpbe történő exportálásonként, ami akár három órát is igénybe vehet. A Mailchimpbe exportálható ügyfélprofilok száma a Mailchimppel kötött szerződésétől függ.
- Csak szegmensek.

## <a name="set-up-connection-to-mailchimp"></a>Állítsa be a Mailchimppel való kapcsolatot

[!INCLUDE [export-connection-include](includes/export-connection-admn.md)]

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a Kapcsolat **hozzáadása,** majd a Mailchimp **lehetőséget**.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Alapértelmezés szerint csak a rendszergazdák. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Tekintse át az adatvédelmet és a megfelelőséget, és válassza az [Elfogadom lehetőséget](connections.md#data-privacy-and-compliance)**.**

1. Válassza a Csatlakozás **lehetőséget** a kapcsolat inicializálásához.

1. Válassza a **Hitelesítés a Mailchimp szolgáltatással** lehetőséget, és adja meg Mailchimp-hitelesítő adatait.

1. Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

## <a name="configure-an-export"></a>Exportálás konfigurálása

[!INCLUDE [export-permission-include](includes/export-permission.md)]

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Válassza az Exportálás **hozzáadása lehetőséget**.

1. A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot a Mailchimp szakaszból. Ha nem érhető el egy kapcsolat sem, akkor forduljon a rendszergazdához.

1. Adja meg az exportálás nevét.

1. **Adja meg Mailchimp célközönség azonosítóját**.

1. Az **Adatok egyeztetése** szakaszban, az **E-mail** mezőben válassza ki az ügyfél e-mail címét jelképező mezőt.

1. Opcionálisan exportálja **utónév** és **vezetéknév** személyre szabottabb e-mailek létrehozásához. Válassza az **Attribútum hozzáadása** lehetőséget a mezők leképezéséhez.

1. Jelölje ki a szegmenseket, amelyeket exportálni szeretne.

1. Válassza a **Mentés** parancsot.

[!INCLUDE [export-saving-include](includes/export-saving.md)]

[!INCLUDE [footer-include](includes/footer-banner.md)]
