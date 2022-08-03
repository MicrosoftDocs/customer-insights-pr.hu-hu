---
title: Szegmensek exportálása a Marketoba (előzetes verzió)
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a Marketoba.
ms.date: 07/25/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: f57cdfbb24df8a8ffa1670b426d50dbba2c5f40f
ms.sourcegitcommit: 594081c82ca385f7143b3416378533aaf2d6d0d3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/27/2022
ms.locfileid: "9195247"
---
# <a name="export-segments-to-marketo-preview"></a>Szegmensek exportálása a Marketoba (előzetes verzió)

Az egyesített ügyfélprofilok szegmensei exportálásának felhasználásával kampányokat hozhat létre, e-mail-marketing szolgáltatást biztosíthat és előnyt kovácsolhat az ügyfelek meghatározott csoportjából a Marketo szolgáltatással.

## <a name="prerequisites"></a>Előfeltételek

- A [Marketo-fiók](https://login.marketo.com/) és a megfelelő rendszergazdai hitelesítő adatok.
- A [Marketo ügyfél-azonosítója, az ügyfél titkos kulcsa és a REST végpont állomásnév](https://developers.marketo.com/rest-api/authentication/).
- [A Marketo](https://docs.marketo.com/display/public/DOCS/Understanding+Static+Lists) meglévő listái és a megfelelő azonosítók.
- [Konfigurált szegmensek](segments.md).
- Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.

## <a name="known-limitations"></a>Ismert korlátozások

- Akár 1 millió ügyfélprofil a Marketo-ba irányuló exportonként, ami akár 3 órát is igénybe vehet. A Marketo-ba exportálható ügyfélprofilok száma a Marketo-val kötött szerződésétől függ.
- Csak szegmensek.

## <a name="set-up-connection-to-marketo"></a>Állítsa be a Marketoval való kapcsolatot

[!INCLUDE [export-connection-include](includes/export-connection-admn.md)]

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a Kapcsolat **hozzáadása,** majd a Marketo **lehetőséget**.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Alapértelmezés szerint csak a rendszergazdák. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Adja meg Marketo-ügyfél-azonosítóját **, titkos ügyféltitkát és REST-végpont állomásnevét**. A REST-végpont eszköznév csak eszköznév, a https:// tag nélkül. Példa: xyz-abc-123.mktorest.com.

1. Tekintse át az adatvédelmet és a megfelelőséget, és válassza az [Elfogadom lehetőséget](connections.md#data-privacy-and-compliance)**.**

1. Válassza a Csatlakozás **lehetőséget** a kapcsolat inicializálásához.

1. Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

## <a name="configure-an-export"></a>Exportálás konfigurálása

[!INCLUDE [export-permission-include](includes/export-permission.md)]

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Válassza az Exportálás **hozzáadása lehetőséget**.

1. A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot a Marketo szakaszból. Ha nem érhető el egy kapcsolat sem, akkor forduljon a rendszergazdához.

1. Adja meg az exportálás nevét.

1. Adja meg Marketo **listaazonosítóját**. A listaazonosító tisztán numerikus érték. Ha például a Marketo-lista azonosítója ST12345A7, távolítsa el a karaktereket a számok előtt és után, és írja be *a 12345* értéket.

1. **Az Adategyeztetés** szakaszban válasszon ki legalább egy mezőt, amely az ügyfél e-mail-címét vagy az ügyfél Marketo-azonosítóját jelöli.

1. Igény szerint exportálhat utónév, vezetéknév, várost **,** **államot** és **országot/régiót**, hogy személyre szabottabb e-maileket hozzon létre.**·** **·** Válassza az **Attribútum hozzáadása** lehetőséget a mezők leképezéséhez.

1. Jelölje ki a szegmenseket, amelyeket exportálni szeretne.

1. Válassza a **Mentés** parancsot.

[!INCLUDE [export-saving-include](includes/export-saving.md)]

A Marketo-ban keresse meg szegmenseit a Marketo listák [alatt](https://docs.marketo.com/display/public/DOCS/Understanding+Static+Lists).

[!INCLUDE [footer-include](includes/footer-banner.md)]
