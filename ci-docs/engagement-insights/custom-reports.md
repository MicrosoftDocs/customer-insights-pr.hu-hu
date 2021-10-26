---
title: Az egyéni jelentések ismertetése
description: Megtudhatja, hogyan hozhat létre egyéni jelentéseket.
author: mochimochi016
ms.reviewer: mhart
ms.author: jefhar
ms.date: 10/01/2021
ms.service: customer-insights
ms.subservice: engagement-insights
ms.topic: conceptual
ms.manager: shellyha
ms.openlocfilehash: 3fa801bfc8b0aee65c21b90de2423a3d5d5e4e26
ms.sourcegitcommit: d9965f4bfc09391698a34042f6b44367e53819e3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/30/2021
ms.locfileid: "7582880"
---
# <a name="create-and-edit-custom-reports"></a>Egyéni jelentések létrehozása és szerkesztése

[!INCLUDE [cc-beta-prerelease-disclaimer](includes/cc-beta-prerelease-disclaimer.md)]

Az előre elkészített (OOB) jelentések mellett egyéni jelentést is készíthet diagrammal és táblázatábrázolásokkal, amelyek segítenek megérteni a felhasználók viselkedését. Ez a cikk azt mutatja be, hogyan hozhat létre jelentést táblázatos és diagramos megjelenítéssel szükséges adatokkal. Az OOB-jelentésekről a [Jelentések megtekintése](view-reports.md) oldalon található tájékoztatás.

## <a name="create-a-custom-report"></a>Egyéni jelentés létrehozása

1. Az egyéni jelentéslista eléréséhez menjen az **Elemzés** > **Egyéni** oldalra.

1. Egyéni jelentés létrehozásának kezdéséhez válassza az **Új jelentés** lehetőséget.

   :::image type="content" source="media/new-custom-report.png" alt-text="Új egyéni jelentések.":::

1. Döntse el, milyen típusú jelentést akar létrehozni:

    - Válassza a **Megjelenítés hozzáadása** lehetőséget a parancssávban alapértelmezett táblázatábrázolás létrehozásához.
    - Vagy válasszon ki egy oszlop, sáv, vonal, terület, torta, fánk vagy táblázat megjelenítését a **Jelentésszerkesztő** ablaktáblából.

1. A **Vizualizációszerkesztő** ablaktábla **Adatok** szakaszában válassza ki a **Metrikák** legördülő menü egyik rendelkezésre álló beállítását (például oldalnézeteket). A megjelenítéshez **Dimenziókat** (például országot) is hozzáadhat. További tudnivalók: [Mérőszámok megtekintése és létrehozása](metrics.md), valamint [A méretek megtekintése és létrehozása](dimensions.md).

   :::image type="content" source="media/page-views.png" alt-text="Adjon metrikát a jelentéséhez.":::

1. Válassza ki a **Vizualizációszerkesztő** ablaktábla **Tervezés** szakaszában a **Cím szöveg** hozzáadásához és a **Cím** be- és kikapcsolt megjelenítéséhez.  A vizualizáció típusát egy másik diagram, például egy **tortadiagram** is módosíthatja.

1. A vizualizáció méretének és pozíciónak módosítása:
   - Válassza ki a vizualizációt, majd húzza át az egyik kierőltetve vagy visszahúzódva állítsa be a méretét.
   - Válassza ki a megjelenítést, és helyezze át új helyre. A nyílbillentyűk használatával a pozíciót is módosíthatja.
1. Egy másik megjelenítés hozzáadásához válassza a parancssoron a **Megjelenítés hozzáadása** lehetőséget.
1. Miután hozzáadta a jelentéshez kívánt megjelenítést, válassza a **Mentés** parancsot a parancssávban.

1. Adja meg az egyéni jelentés nevét, és létrehozásához válassza a **Mentés** lehetőséget.
 
## <a name="filter-a-custom-report"></a>Egyéni jelentés szűrése

Egyéni jelentésben kiválaszthatja a időkeret dátumtartományt, hogy egy értékre vagy időszakra összpontosítson.

A kiválasztott időkeret a jelentés nézetének jobb felső sarkában jelöljön ki egy értéket a jelentés legördülő listájából. Választhat **Rögzített dátumtartományt** is.

:::image type="content" source="media/filter-time-date-range.png" alt-text="Szűrés idő- vagy dátumtartomány szerint.":::

A legtöbb jelentés esetén válassza a **+ Feltétel hozzáadása** lehetőséget, ha kiválaszt egy betegséget vagy szegmenst a jelentés szűréséhez. További tudnivalók: [Szegmensek megtekintése és létrehozása](segments.md).

## <a name="edit-a-custom-report"></a>Egyéni jelentés szerkesztése

1. Az egyéni jelentéslista eléréséhez menjen az **Elemzés** > **Egyéni** oldalra.

1. Az egyéni jelentéslistában válassza a **További [...]** lehetőséget. 

1. Válassza a **Szerkesztés** nevet, ha módosítani szeretné a jelentés nevét.

1. Jelölje ki a jelentés nevét, és használja a **+ Megjelenítés hozzáadása** és **Szerkesztés** lehetőségek hozzáadása lehetőséget a megjelenítések hozzáadásához, eltávolításához, áthelyezéséhez vagy átméretezéséhez.

1. Ha módosítani szeretné a vizualizáció tulajdonságait, válassza ki a megjelenítést, válassza ki a **...** lehetőséget, majd a **Képi megjelenítés szerkesztése**.

   :::image type="content" source="media/edit-visual-control.png" alt-text="Egyéni jelentésekhez tartozó diagramtulajdonságok szerkesztése.":::

1. A jelentés szerkesztésének befejezését követően a módosítások alkalmazásához válassza a **Mentés** lehetőséget. 

## <a name="delete-a-custom-report"></a>Egyéni jelentés törlése

1. Az egyéni jelentéslista eléréséhez menjen az **Elemzés** > **Egyéni** oldalra.

1. Az egyéni jelentéslistában válassza a **...** lehetőséget.

1. A jelentés eltávolításához válassza a **Törlés** lehetőséget.

1. A jelentés végleges eltávolításához erősítse meg a törlést.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
