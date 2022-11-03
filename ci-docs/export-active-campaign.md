---
title: Szegmensek exportálása az ActiveCampaign programba
description: További információ a kapcsolat konfigurálásához és az ActiveCampaign-hez való exportáláshoz.
ms.date: 07/25/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: conceptual
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: e62888a6d618fb1154890e607d8c23d3767d35f7
ms.sourcegitcommit: c3ae7e7e0c9566f9479ba71a26afc5a17fb589c2
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/27/2022
ms.locfileid: "9725403"
---
# <a name="export-segments-to-activecampaign-preview"></a>Szegmensek exportálása ActiveCampaign-be (előzetes verzió)

Exportálja az egyesített ügyfélprofilok szegmenseit az ActiveCampaign-be, és használja őket marketingtevékenységekhez.

## <a name="prerequisites"></a>Előfeltételek

- Egy [ActiveCampaign-fiók](https://www.activecampaign.com/) és a megfelelő rendszergazdai hitelesítő adatok.
- Egy [ActiveCampaign listaazonosító](https://help.activecampaign.com/hc/articles/360000030559-How-to-create-a-list-in-ActiveCampaign).
- Egy [ActiveCampaign API-kulcs](https://help.activecampaign.com/hc/articles/207317590-Getting-started-with-the-API#how-to-obtain-your-activecampaign-api-url-and-key) és REST végpont állomásnév.
- [Konfigurált szegmensek](segments.md) a Customer Insights alkalmazásban.
- Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.

## <a name="known-limitations"></a>Ismert korlátozások

- A privát kapcsolat a saját tároló használata (BYOS) funkcióval együtt nem támogatott.
- Az ActiveCampaign szolgáltatásba exportálásonként akár 1 millió ügyfélprofil is eltarthat, ami akár 90 percet is igénybe vehet. Az ActiveCampaign alkalmazásba exportálható ügyfélprofilok száma az ActiveCampaign szolgáltatással kötött szerződéstől függ, és csak korlátozott.
- Csak szegmensek.

## <a name="set-up-connection-to-activecampaign"></a>Állítsa be az ActiveCampaign-nel való kapcsolatot

[!INCLUDE [export-connection-include](includes/export-connection-admn.md)]

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza az Add connection (Kapcsolat **hozzáadása), majd az ActiveCampaign (ActiveCampaign**) lehetőséget **·**.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Alapértelmezés szerint csak a rendszergazdák. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Adja meg ActiveCampaign API-kulcsát és REST-végpont eszköznevet. A REST-végpont eszköznév csak eszköznév, a https:// tag nélkül.

1. Tekintse át az adatvédelmet és a megfelelőséget [, és válassza az](connections.md#data-privacy-and-compliance) Elfogadom **lehetőséget**.

1. Válassza a Csatlakozás **lehetőséget** a kapcsolat inicializálásához.

1. Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

## <a name="configure-an-export"></a>Exportálás konfigurálása

[!INCLUDE [export-permission-include](includes/export-permission.md)]

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Válassza az Exportálás **hozzáadása lehetőséget**.

1. Az **Exportálási kapcsolat** mezőben válasszon kapcsolatot az ActiveCampaign szakaszból. Ha nem érhető el egy kapcsolat sem, akkor forduljon a rendszergazdához.

1. Adja meg az exportálás nevét.

1. Adja meg az ActiveCampaign-lista **azonosítóját**.

1. Az **Adatok egyeztetése** szakaszban, az **E-mail** mezőben válassza ki az ügyfél e-mail címét jelképező mezőt.

1. Igény szerint exportálhatja **a utónév,** a vezetéknév és **a** **Telefon** alkalmazást személyre szabottabb e-mailek létrehozásához. Válassza az **Attribútum hozzáadása** lehetőséget a mezők leképezéséhez.

1. Jelölje ki a szegmenseket, amelyeket exportálni szeretne.

1. Válassza a **Mentés** parancsot.

[!INCLUDE [export-saving-include](includes/export-saving.md)]

[!INCLUDE [footer-include](includes/footer-banner.md)]
