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
ms.openlocfilehash: 2f52eb8196e057f934c8d2b5ac0518ce121606b6
ms.sourcegitcommit: 003c1929f730d7d505c108aba84f6269f4c98978
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/12/2022
ms.locfileid: "9655297"
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
