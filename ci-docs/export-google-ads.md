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
ms.openlocfilehash: a46623e609665f8031f223593a6644147e5209d8
ms.sourcegitcommit: c3ae7e7e0c9566f9479ba71a26afc5a17fb589c2
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/27/2022
ms.locfileid: "9725081"
---
# <a name="export-segments-to-google-ads-preview"></a>Szegmensek exportálása a Google Ads szolgáltatásba (előzetes verzió)

Exportálja az egységes ügyfélprofilok szegmenseit a Google Ads célközönség listára, és használja őket a Google Keresés, a Gmail, YouTube és Google Display Network-ön történő hirdetésnél.

## <a name="prerequisites"></a>Előfeltételek

- Egy Google Ads-fiók [és](https://ads.google.com/) a megfelelő rendszergazdai hitelesítő adatok.
- Egy Google Ads-ügyfél-azonosító [...](https://support.google.com/google-ads/answer/1704344).
- Az Ügyfélegyezési [szabályzat](https://support.google.com/adspolicy/answer/6299717) követelményei teljesülnek.
- A remarketinglista méretére [vonatkozó](https://support.google.com/google-ads/answer/7558048) követelmények teljesülnek.
- [Konfigurált szegmensek](segments.md).
- Az exportált szegmensek egyesített ügyfélprofiljai olyan mezőket tartalmaznak, amelyek e-mail-címet, telefont, mobilhirdetői azonosítót, harmadik féltől származó felhasználói azonosítót vagy címet jelölnek.

## <a name="known-limitations"></a>Ismert korlátozások

- A privát kapcsolat a saját tároló használata (BYOS) funkcióval együtt nem támogatott.
- Exportálásonként legfeljebb 1 millió ügyfélprofilt exportálhat a Google Ads szolgáltatásba, amelynek kitöltése a szolgáltatói oldal korlátozásai miatt akár 30 percet is igénybe vehet.
- Csak szegmensek.
- A Google Ads egyezése akár 48 órát is igénybe vehet.

## <a name="set-up-connection-to-google-ads"></a>Kapcsolat beállítása a Google Adshez

[!INCLUDE [export-connection-include](includes/export-connection-admn.md)]

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a Kapcsolat **hozzáadása, majd a** Google Ads **lehetőséget**.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Alapértelmezés szerint csak a rendszergazdák. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Adja meg Google Ads-ügyfél-azonosítóját.

1. Tekintse át az adatvédelmet és a megfelelőséget [, és válassza az](connections.md#data-privacy-and-compliance) Elfogadom **lehetőséget**.

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
   - Meglévő Google Ads-célközönség frissítéséhez adja meg a Google Ads-célközönség [azonosítót](https://support.google.com/google-ads/answer/7558048?hl=en#:~:text=Audience%20lists%20is%20a%20section,Display%20Network%20through%20remarketing%20campaigns).
   - Új célközönség létrehozásához hagyja üresen a Google célközönség azonosító mezőt. A Customer Insights automatikusan létrehoz egy új célközönség a Google Ads-fiókban, és az exportált szegmens nevét használja.

1. **Az Adategyeztetés** szakaszban válasszon ki egy vagy több exportálni kívánt adatmezőt, és válassza ki azt a mezőt, amely a Customer Insights megfelelő adatmezőit képviseli.

1. Jelölje ki a szegmenseket, amelyeket exportálni szeretne.

1. Válassza a **Mentés** parancsot.

[!INCLUDE [export-saving-include](includes/export-saving.md)]

[!INCLUDE [footer-include](includes/footer-banner.md)]
