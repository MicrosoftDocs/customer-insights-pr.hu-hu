---
title: Szegmensek exportálása az Állandó kapcsolattartóba (előzetes verzió)
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja az Constant Contactba.
ms.date: 07/25/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: conceptual
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: c0affd3ed45f462696850813bd50331061dde780
ms.sourcegitcommit: c3ae7e7e0c9566f9479ba71a26afc5a17fb589c2
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/27/2022
ms.locfileid: "9724504"
---
# <a name="export-segments-to-constant-contact-preview"></a>Szegmensek exportálása az Állandó kapcsolattartóba (előzetes verzió)

Exportálja az egyesített ügyfélprofilok szegmensét az Constant Contactba, és használja őket marketing-tevékenységekre.

## <a name="prerequisites"></a>Előfeltételek

- Constant [Contact fiók](https://www.constantcontact.com/account-home) és a megfelelő rendszergazdai hitelesítő adatok.
- Állandó [partnerlista azonosítója](https://app.constantcontact.com/pages/contacts/ui#lists). Nyisson meg egy listát az Constant Contactban, és keresse meg a lista azonosítóját az URL-címben.
- [Konfigurált szegmensek](segments.md) a Customer Insights alkalmazásban.
- Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.

## <a name="known-limitations"></a>Ismert korlátozások

- A privát kapcsolat a saját tároló használata (BYOS) funkcióval együtt nem támogatott.
- Exportálásonként akár 1 millió ügyfélprofil a Constant Contact szolgáltatásba, ami akár egy órát is igénybe vehet. A Constant Contact szolgáltatásba exportálható ügyfélprofilok száma a Constant Contact szolgáltatással kötött szerződésétől függ.
- Csak szegmensek.

## <a name="set-up-connection-to-constant-contact"></a>Kapcsolat beállítása Constant Contacthoz

[!INCLUDE [export-connection-include](includes/export-connection-admn.md)]

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a **Kapcsolat** hozzáadása, majd az Állandó kapcsolat **lehetőséget**.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Alapértelmezés szerint csak a rendszergazdák. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Tekintse át az adatvédelmet és a megfelelőséget [, és válassza az](connections.md#data-privacy-and-compliance) Elfogadom **lehetőséget**.

1. Válassza a Csatlakozás **lehetőséget** a kapcsolat inicializálásához.

1. Válassza a **Hitelesítés állandó kapcsolattartóval** lehetőséget, és adja meg a rendszergazdai hitelesítő adatokat az Állandó kapcsolattartóhoz.

1. Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

## <a name="configure-an-export"></a>Exportálás konfigurálása

[!INCLUDE [export-permission-include](includes/export-permission.md)]

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Válassza az Exportálás **hozzáadása lehetőséget**.

1. A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot az Constant Contact szakaszból. Ha nem érhető el egy kapcsolat sem, akkor forduljon a rendszergazdához.

1. Adja meg az exportálás nevét.

1. Adja meg az állandó kapcsolattartói lista **azonosítóját**.

1. Az **Adatok egyeztetése** szakaszban, az **E-mail** mezőben válassza ki az ügyfél e-mail címét jelképező mezőt.

1. Igény szerint exportálhatja **a utónév** és **vezetéknév** további mezőkként, hogy személyre szabottabb e-maileket hozzon létre. Válassza az **Attribútum hozzáadása** lehetőséget a mezők leképezéséhez.

1. Jelölje ki a szegmenseket, amelyeket exportálni szeretne.

1. Válassza a **Mentés** parancsot.

[!INCLUDE [export-saving-include](includes/export-saving.md)]

[!INCLUDE [footer-include](includes/footer-banner.md)]
