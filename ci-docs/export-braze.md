---
title: Szegmensek exportálása a Braze alkalmazásba (előzetes verzió)
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a Braze-be.
ms.date: 10/06/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: conceptual
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: a3967008ec166cb6f099659b0791f1318126c0da
ms.sourcegitcommit: c3ae7e7e0c9566f9479ba71a26afc5a17fb589c2
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/27/2022
ms.locfileid: "9725219"
---
# <a name="export-segments-to-braze-preview"></a>Szegmensek exportálása a Braze alkalmazásba (előzetes verzió)

Exportálja az egységes ügyfélprofilok szegmenseit a Braze-be, és használja őket marketingtevékenységekhez.

## <a name="prerequisites"></a>Előfeltételek

- Egy [Braze-fiók](https://www.braze.com/) és a megfelelő rendszergazdai hitelesítő adatok.
- Braze [API-kulcs](https://www.braze.com/docs/api/basics/)
- A [Braze REST végpont](https://www.braze.com/docs/api/basics/#api-definitions) 
- [Konfigurált szegmensek](segments.md) a Customer Insights alkalmazásban.
- Az exportált szegmensek egyesített ügyfélprofiljai tartalmaznak egy mezőt, amely egy e-mail címet és egy Braze ügyfél-azonosítót jelöl.

## <a name="known-limitations"></a>Ismert korlátozások

- A privát kapcsolat a saját tároló használata (BYOS) funkcióval együtt nem támogatott.
- Akár 1 millió ügyfélprofil a Braze-hez, ami akár 40 percet is igénybe vehet. A Braze-be exportálható ügyfélprofilok száma a Braze-vel kötött szerződésétől függ.
- Csak szegmensek.
- Azure Private Link nem támogatott a Braze-exportáláshoz.

## <a name="set-up-connection-to-braze"></a>Kapcsolat beállítása a Braze-hez

[!INCLUDE [export-connection-include](includes/export-connection-admn.md)]

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a Kapcsolat **hozzáadása, majd a** Braze **lehetőséget**.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Alapértelmezés szerint csak a rendszergazdák. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Adja meg a Braze API-kulcsot a bejelentkezés folytatásához.

1. Tekintse át az adatvédelmet és a megfelelőséget [, és válassza az](connections.md#data-privacy-and-compliance) Elfogadom **lehetőséget**.

1. Válassza a Csatlakozás **lehetőséget** a kapcsolat inicializálásához.

1. Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

## <a name="configure-an-export"></a>Exportálás konfigurálása

[!INCLUDE [export-permission-include](includes/export-permission.md)]

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Válassza az Exportálás **hozzáadása lehetőséget**.

1. A Kapcsolat exportáláshoz **mezőben** válasszon egy kapcsolatot a Braze szakaszból. Ha nem érhető el egy kapcsolat sem, akkor forduljon a rendszergazdához.

1. Írja be a REST-végpont **a Gazdagépnév** mezőbe a következő formátumban:`rest.iad-03.braze.com`.

1. Adja meg az exportálás nevét.

1. Az **Adatok egyeztetése** szakaszban, az **E-mail** mezőben válassza ki az ügyfél e-mail címét jelképező mezőt. **A Vevőazonosító** mezőben válassza ki azt a mezőt, amely a vevő Braze azonosítóját jelöli. A Braze szegmensei ugyanazzal a szegmensnévvel jönnek létre, mint a Dynamics 365 Customer Insights. Az adatok egyeztetéséhez több, nem kötelező mezőt is kiválaszthat.

1. Válassza ki az exportálni kívánt entitásokat vagy szegmenseket.

1. Válassza a **Mentés** parancsot.

[!INCLUDE [export-saving-include](includes/export-saving.md)]

[!INCLUDE [footer-include](includes/footer-banner.md)]
