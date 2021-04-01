---
title: Felhasználói engedélyek kezelése
description: További információk az engedélyekről és a felhasználói szerepkörökről.
ms.date: 10/27/2020
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: NimrodMagen
ms.author: nimagen
manager: shellyha
ms.openlocfilehash: e58bb1a3bd4c0920ff984daffabbf16162185f3d
ms.sourcegitcommit: bae40184312ab27b95c140a044875c2daea37951
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/15/2021
ms.locfileid: "5595705"
---
# <a name="user-permissions"></a>Felhasználói engedélyek

Az **Engedélyek** oldalon megadhatók a szerepkörök és az engedélyek a célközönség-információk használatához.

A lap megtekintéséhez rendszergazdai jogosultsággal kell rendelkeznie. Ha meg szeretné nyitni az engedélyek oldalt célközönség-információkban, akkor nyissa meg a **Rendszergazda** > **Engedélyek** pontot.

Háromféle típusú szerepkör van:

## <a name="viewer"></a>Megtekintő

- Fedezze fel a **Kezdőlap** és **Szegmensek** oldalak betekintő információit és szegmenseit.
- Keressen és szűrjön ügyfélprofilokat az **Ügyfelek** oldal használatával. A mezőknek kereshetőknek kell lenniük.
- A **Bővítés** oldal megtekintése felfedezése.
- Fedezzen fel és exportáljon entitásokat az **Entitások** lap használatával.
- A rendszerfolyamatok állapotának megtekintése a **Rendszer** oldalon történik.
- Szegmensek exportálása a **Szegmensek** lapról.
- Telepítse és használja a **Power BI Customer Insights** irányítópultot.

## <a name="contributor"></a>Közreműködő

- A Néző számára az összes engedély rendelkezésre áll.
- Adatok betöltése és átalakítása az **Adatforrások** oldal használatával történhet.
- Végezze el az *Adategységesítés* szakaszait (**Megfeleltetés**, **Egyeztetés** és **Egyesítés**), amelyekkel egységesített ügyfélprofil-entitást hozhat létre.
- Adja meg a **Kapcsolatokat** és **Tevékenységeket**.
- Hozzon létre szegmenseket a **Szegmensek** oldalán.
- Hozzon létre mérőszámokat a **Mérőszámok** oldalon.
- A konfiguráció kezelése és az ügyfelek profiljainak bővítése a **Bővítés** lapról (csak a belső bővítések esetében).

## <a name="administrator"></a>Adminisztrátor

- A Közreműködő számára az összes engedély rendelkezésre áll.
- A beállításokat a **Rendszer** oldalon módosíthatja, beleértve a munkanyelvet és a rendszerfolyamatok frissítési ütemezését.
- Az engedélyeket megtekintheti és hozzáadhatja az **Engedélyek** oldalon.
- Az Ügyfelek oldalra vonatkozóan beállíthatja a Keresés és Szűrés meghatározásait a **Keresési és szűrési index** oldalon (amely az **Ügyfelek** oldalról elérhető).
- Meghatározhatja a Dynamics 365 Sales szegmens célhelyeit a **Exportálási célhelyek** oldalon.
- A konfiguráció kezelése és az ügyfelek profiljainak bővítése a **Bővítés** lapról (az összes bővítés esetében).
- Telepítheti és használhatja az **Ügyfélkártya bővítményt**.
- Adja hozzá és használja a **Power Apps összekötőt**.
- [Customer Insights API-k](apis.md) használatának engedélyezése.

## <a name="assign-roles-and-permissions"></a>Szerepkörök és engedélyek hozzárendelése

1. A célközönség információin belül nyissa meg a következőt **Rendszergazda** > **Engedélyek**.

1. Válassza a **Felhasználók hozzáadása** lehetőséget az **Engedélyek hozzáadása/szerkesztése** ablaktábla megnyitásához.

1. A **Keresés** mező segítségével keresse meg azt az Azure Active Directory-felhasználót vagy csoportot, amelynek az engedélyeit módosítani szeretné. Válassza ki azt a **szerepkört**, amelyet hozzá szeretne rendelni az adott felhasználóhoz vagy csoporthoz.

1. Válassza a **Mentés** parancsot. Az aktuális környezet automatikusan meg lesz osztva azon felhasználóval vagy csoport tagjaival, akinek az engedélyeiz módosította. A felhasználók a megadott szerepkörük szerint érhetik el a Customer Insights alkalmazást és a munkát.

## <a name="view-current-permissions"></a>Aktuális engedélyek megtekintése

A célközönség-információkban keresse meg a **Rendszergazda** > **Engedélyek**, és tekintse meg a jelenleg aktív szerepkör-hozzárendeléseket.

- A **típus** oszlop egyetlen felhasználót, csoportot vagy alkalmazást ad meg. A rendszer támogatja az egyéni felhasználókat és csoportokat.
- A szerepköröket a **szerepkör** oszlopban kell megadni.
- Válassza ki az oszlop címét, hogy az adott oszlop értéke alapján rendezze az eredményeket.
- Adott felhasználók megkereséséhez használja a lap tetején található **Keresés** mezőt.


[!INCLUDE[footer-include](../includes/footer-banner.md)]