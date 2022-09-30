---
title: Customer Insights-adatok exportálása a HubSpot-ba
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a HubSpot-ba.
ms.date: 09/23/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: conceptual
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 0281be288b2c4d9e5da7ad8e2ed25f7b51b8498e
ms.sourcegitcommit: f959c85871777e5f4eab289e91b2fd114cd72153
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/23/2022
ms.locfileid: "9588929"
---
# <a name="export-segments-to-hubspot-preview"></a>Szegmensek exportálása a HubSpotba (előzetes verzió)

Exportálja az egyesített ügyfélprofilok szegmenseit a HubSpot-ba, és használja őket e-mail marketinghez.

## <a name="prerequisites-for-a-connection"></a>Egy kapcsolat előfeltételei

- Egy [HubSpot-fiók](https://www.hubspot.com/) és a megfelelő rendszergazdai hitelesítő adatok.
- [API-kulcs](https://knowledge.hubspot.com/Integrations/How-do-I-get-my-HubSpot-API-key) a HubSpot-tól.
- [Konfigurált szegmensek](segments.md) a Customer Insights szolgáltatásban.

## <a name="known-limitations"></a>Ismert korlátozások

- A HubSpotba való exportálásonként akár 100 000 ügyfélprofil is lehet, ami akár 15 percet is igénybe vehet. A HubSpot-ba exportálható ügyfélprofilok száma a HubSpottal kötött szerződéstől függ és korlátozott.
- Csak szegmensek.

## <a name="set-up-connection-to-hubspot"></a>Kapcsolat beállítása a HubSpottal

[!INCLUDE [export-connection-include](includes/export-connection-admn.md)]

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a Kapcsolat **hozzáadása lehetőséget**, majd válassza a HubSpot **lehetőséget** a kapcsolat konfigurálásához.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Adja meg a HubSpot hitelesítő adatait, amikor a rendszer kéri.

1. Tekintse át az adatvédelmet és a megfelelőséget, és válassza az [Elfogadom lehetőséget](connections.md#data-privacy-and-compliance)**.**

1. Válassza a Csatlakozás **lehetőséget** a HubSpottal való kapcsolat inicializálásához.

1. Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

## <a name="configure-an-export"></a>Exportálás konfigurálása

[!INCLUDE [export-permission-include](includes/export-permission.md)]

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Új exportálás létrehozásához válassza az **Exportálás hozzáadása** lehetőséget.

1. **A Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot a HubSpot szakaszból. Ha nem látja ezt a szakasznevet, az Ön számára nincs ilyen típusú kapcsolat.

1. Az **Adatok egyeztetése** szakaszban, az **E-mail** mezőben válassza ki az ügyfél e-mail címét jelképező mezőt. Ismételje meg ugyanezeket a lépéseket más választható mezőkkel is.

1. Jelölje ki a szegmenseket, amelyeket exportálni szeretne.

1. Válassza a **Mentés** parancsot.

[!INCLUDE [export-saving-include](includes/export-saving.md)]

[!INCLUDE [footer-include](includes/footer-banner.md)]
