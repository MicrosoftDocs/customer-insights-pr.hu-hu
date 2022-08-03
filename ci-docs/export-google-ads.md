---
title: Szegmensek exportálása a Google Ads szolgáltatásba (előzetes verzió)
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a Google Adsbe.
ms.date: 07/25/2022
ms.subservice: audience-insights
ms.topic: how-to
author: pkieffer
ms.author: philk
ms.reviewer: mhart
manager: shellyha
ms.openlocfilehash: fd7498ecf17ef8a3a8f22dcc49ae204bef88b47f
ms.sourcegitcommit: 594081c82ca385f7143b3416378533aaf2d6d0d3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/27/2022
ms.locfileid: "9196581"
---
# <a name="export-segments-to-google-ads-preview"></a>Szegmensek exportálása a Google Ads szolgáltatásba (előzetes verzió)

Exportálja az egységes ügyfélprofilok szegmenseit a Google Ads célközönség listára, és használja őket a Google Keresés, a Gmail, YouTube és Google Display Network-ön történő hirdetésnél.

## <a name="prerequisites"></a>Előfeltételek

- Egy [Google Ads-fiók](https://ads.google.com/) és a megfelelő rendszergazdai hitelesítő adatok.
- Egy [Google Ads-ügyfél-azonosító](https://support.google.com/google-ads/answer/1704344).
- Az ügyfélegyezési szabályzat [követelményei](https://support.google.com/adspolicy/answer/6299717) teljesülnek.
- A remarketinglista-méretekre [vonatkozó követelmények](https://support.google.com/google-ads/answer/7558048) teljesülnek.
- [Konfigurált szegmensek](segments.md).
- Az exportált szegmensek egyesített ügyfélprofiljai e-mail-címet, telefont, mobilhirdető-azonosítót, harmadik fél felhasználói azonosítóját vagy címét ábrázoló mezőket tartalmaznak.

## <a name="known-limitations"></a>Ismert korlátozások

- Exportáljon exportálásonként legfeljebb 1 millió ügyfélprofilt a Google Ads szolgáltatásba, amelynek befejezése akár 30 percet is igénybe vehet a szolgáltatói oldal korlátai miatt.
- Csak szegmensek.
- A Google Ads szolgáltatásban az egyezés akár 48 órát is igénybe vehet.

## <a name="set-up-connection-to-google-ads"></a>Kapcsolat beállítása a Google Adshez

[!INCLUDE [export-connection-include](includes/export-connection-admn.md)]

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a Kapcsolat **hozzáadása,** majd a Google Ads **lehetőséget**.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Alapértelmezés szerint csak a rendszergazdák. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Adja meg a Google Ads-ügyfél-azonosítót.

1. Tekintse át az adatvédelmet és a megfelelőséget, és válassza az [Elfogadom lehetőséget](connections.md#data-privacy-and-compliance)**.**

1. Válassza a **Hitelesítés a Google Ads szolgáltatással** lehetőséget, és adja meg Google Ads-hitelesítő adatait.

1. Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

## <a name="configure-an-export"></a>Exportálás konfigurálása

[!INCLUDE [export-permission-include](includes/export-permission.md)]

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Válassza az Exportálás **hozzáadása lehetőséget**.

1. A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot a Google Ads szakaszból. Ha nem érhető el egy kapcsolat sem, akkor forduljon a rendszergazdához.

1. Adja meg az exportálás nevét.

1. Válassza ki, hogy meglévő célközönség használ-e, vagy újat hoz létre:
   - Meglévő Google Ads-célközönség frissítéséhez adja meg a [Google Ads célközönség-azonosítóját](https://support.google.com/google-ads/answer/7558048?hl=en#:~:text=Audience%20lists%20is%20a%20section,Display%20Network%20through%20remarketing%20campaigns).
   - Új célközönség létrehozásához hagyja üresen a Google célközönség ID mezőt. A Customer Insights automatikusan létrehoz egy új célközönség a Google Ads-fiókban, és az exportált szegmens nevét használja.

1. **Az Adategyeztetés** szakaszban válasszon ki egy vagy több exportálni kívánt adatmezőt, és válassza ki azt a mezőt, amely a Customer Insights megfelelő adatmezőit jelöli.

1. Jelölje ki a szegmenseket, amelyeket exportálni szeretne.

1. Válassza a **Mentés** parancsot.

[!INCLUDE [export-saving-include](includes/export-saving.md)]

[!INCLUDE [footer-include](includes/footer-banner.md)]
