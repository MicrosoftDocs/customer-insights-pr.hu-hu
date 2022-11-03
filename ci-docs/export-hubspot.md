---
title: Customer Insights-adatok exportálása a HubSpotba
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a HubSpotba.
ms.date: 09/23/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: conceptual
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: b34f1d54fa499f6c6b80fa547a8aaf61af3b35a1
ms.sourcegitcommit: c3ae7e7e0c9566f9479ba71a26afc5a17fb589c2
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/27/2022
ms.locfileid: "9725357"
---
# <a name="export-segments-to-hubspot-preview"></a>Szegmensek exportálása a HubSpot programba (előzetes verzió)

Exportálja az egyesített ügyfélprofilok szegmenseit a HubSpotba, és használja őket e-mail marketinghez.

## <a name="prerequisites-for-a-connection"></a>Egy kapcsolat előfeltételei

- Egy [HubSpot-fiók](https://www.hubspot.com/) és a megfelelő rendszergazdai hitelesítő adatok.
- [API-kulcs](https://knowledge.hubspot.com/Integrations/How-do-I-get-my-HubSpot-API-key) a HubSpot-tól.
- [Konfigurált szegmensek](segments.md) a Customer Insights alkalmazásban.

## <a name="known-limitations"></a>Ismert korlátozások

- A privát kapcsolat a saját tároló használata (BYOS) funkcióval együtt nem támogatott.
- Akár 100 000 ügyfélprofil exportálásonként a HubSpotba, ami akár 15 percet is igénybe vehet. A HubSpotba exportálható ügyfélprofilok száma a HubSpottal kötött szerződésétől függ és korlátozott.
- Csak szegmensek.

## <a name="set-up-connection-to-hubspot"></a>Kapcsolat beállítása a HubSpot-tal

[!INCLUDE [export-connection-include](includes/export-connection-admn.md)]

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a Kapcsolat **hozzáadása lehetőséget**, majd válassza a HubSpot **lehetőséget** a kapcsolat konfigurálásához.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Adja meg a HubSpot hitelesítő adatait, amikor a rendszer kéri.

1. Tekintse át az adatvédelmet és a megfelelőséget [, és válassza az](connections.md#data-privacy-and-compliance) Elfogadom **lehetőséget**.

1. Válassza a Csatlakozás **lehetőséget a** HubSpottal való kapcsolat inicializálásához.

1. Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

## <a name="configure-an-export"></a>Exportálás konfigurálása

[!INCLUDE [export-permission-include](includes/export-permission.md)]

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Új exportálás létrehozásához válassza az **Exportálás hozzáadása** lehetőséget.

1. A Kapcsolat exportáláshoz **mezőben** válasszon egy kapcsolatot a HubSpot szakaszból. Ha nem látja ezt a szakasznevet, az Ön számára nincs ilyen típusú kapcsolat.

1. Az **Adatok egyeztetése** szakaszban, az **E-mail** mezőben válassza ki az ügyfél e-mail címét jelképező mezőt. Ismételje meg ugyanezeket a lépéseket más opcionális mezők esetében is.

1. Jelölje ki a szegmenseket, amelyeket exportálni szeretne.

1. Válassza a **Mentés** parancsot.

[!INCLUDE [export-saving-include](includes/export-saving.md)]

[!INCLUDE [footer-include](includes/footer-banner.md)]
