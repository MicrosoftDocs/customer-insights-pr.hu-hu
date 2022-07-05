---
title: Felhasználói engedélyek kezelése
description: További információk az engedélyekről és a felhasználói szerepkörökről.
ms.date: 02/09/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: conceptual
author: NimrodMagen
ms.author: nimagen
manager: shellyha
searchScope:
- ci-permissions
- ci-system-security
- customerInsights
ms.openlocfilehash: 30b37645cad4e795ef20579e20e3f2bbdb2afbf6
ms.sourcegitcommit: a97d31a647a5d259140a1baaeef8c6ea10b8cbde
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/29/2022
ms.locfileid: "9054871"
---
# <a name="manage-user-permissions"></a>Felhasználói engedélyek kezelése

Az **Engedélyek** lapon állíthatja be a szerepköröket és az engedélyeket a Customer Insights használatához.

A lap megtekintéséhez rendszergazdai jogosultsággal kell rendelkeznie. Az engedélyek lap eléréséhez lépjen a **Rendszergazdai** > **biztonsági** > **felhasználók elemre**.

Háromféle típusú szerepkör van:

## <a name="viewer"></a>Megtekintő

- Fedezze fel a **Kezdőlap** és **Szegmensek** oldalak betekintő információit és szegmenseit.
- Keressen és szűrjön ügyfélprofilokat az **Ügyfelek** oldal használatával. A mezőknek kereshetőknek kell lenniük.
- A **Bővítés** oldal megtekintése felfedezése.
- Fedezzen fel és exportáljon entitásokat az **Entitások** lap használatával.
- A rendszerfolyamatok állapotának megtekintése a **Rendszer** oldalon történik.
- Az exportálások megtekintése az **Exportálások** lapon.
- Telepítse és használja a **Power BI Customer Insights** irányítópultot.

## <a name="contributor"></a>Közreműködő

- A Néző számára az összes engedély rendelkezésre áll.
- Adatok betöltése és átalakítása az **Adatforrások** oldal használatával történhet.
- Teljes ***Adategyesítés**, amely egységes ügyfélprofil-entitást eredményez.
- Adja meg a **Kapcsolatokat** és **Tevékenységeket**.
- Hozzon létre szegmenseket a **Szegmensek** oldalán.
- Hozzon létre mérőszámokat a **Mérőszámok** oldalon.
- A konfiguráció kezelése és az ügyfelek profiljainak bővítése a **Bővítés** lapról (csak a belső bővítések esetében).
- Az exportálások kezelése és létrehozása a közreműködőkkel megosztott kapcsolatok alapján. [További információk arról, hogyan engedélyezik a rendszergazdák a közreműködőknek az exportálásokhoz használható kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

## <a name="admin"></a>Felügyelet

- A Közreműködő számára az összes engedély rendelkezésre áll.
- A beállításokat a **Rendszer** oldalon módosíthatja, beleértve a munkanyelvet és a rendszerfolyamatok frissítési ütemezését.
- Az engedélyeket megtekintheti és hozzáadhatja az **Engedélyek** oldalon.
- Az Ügyfelek oldalra vonatkozóan beállíthatja a Keresés és Szűrés meghatározásait a **Keresési és szűrési index** oldalon (amely az **Ügyfelek** oldalról elérhető).
- Kezelje a kapcsolatokat, és engedélyezze őket az egyéb felhasználói szerepkörökkel rendelkezők számára a **Kapcsolatok** lapon.
- A konfiguráció kezelése és az ügyfelek profiljainak bővítése a **Bővítés** lapról (az összes bővítés esetében).
- Exportálás kezelése és létrehozása az **Exportálások** lapon.
- Telepítheti és használhatja az **Ügyfélkártya bővítményt**.
- Adja hozzá és használja a **Power Apps összekötőt**.
- [Customer Insights API-k](apis.md) használatának engedélyezése.
- [Rendelje hozzá a környezet tulajdonjogát](manage-environments.md#change-the-owner-of-an-environment) egy másik rendszergazdához.

## <a name="admin-owner"></a>Rendszergazda (tulajdonos)

- Az adminisztrátor számára elérhető összes engedély.
- [Állítsa vissza és törölje](manage-environments.md#reset-an-existing-environment-preview) a környezetet.

## <a name="assign-roles-and-permissions"></a>Szerepkörök és engedélyek hozzárendelése

1. Lépjen a **Rendszergazdai** > **biztonság** > **Felhasználók*** oldalra.

1. Válassza a **Felhasználók hozzáadása** lehetőséget az **Engedélyek hozzáadása/szerkesztése** ablaktábla megnyitásához.

1. A **Keresés** mező segítségével keresse meg azt az Azure Active Directory-felhasználót vagy csoportot, amelynek az engedélyeit módosítani szeretné. Válassza ki azt a **szerepkört**, amelyet hozzá szeretne rendelni az adott felhasználóhoz vagy csoporthoz.

1. Válassza a **Mentés** parancsot. Az aktuális környezet automatikusan meg lesz osztva azon felhasználóval vagy csoport tagjaival, akinek az engedélyeiz módosította. A felhasználók a megadott szerepkörük szerint érhetik el a Customer Insights alkalmazást és a munkát.

## <a name="view-current-permissions"></a>Aktuális engedélyek megtekintése

**A Rendszergazdai** > **biztonsági** > **felhasználók lapon** megtekintheti, hogy jelenleg milyen szerepkör-hozzárendelések vannak aktívak.

- A **típus** oszlop egyetlen felhasználót, csoportot vagy alkalmazást ad meg. A rendszer támogatja az egyéni felhasználókat és csoportokat.
- A szerepköröket a **szerepkör** oszlopban kell megadni.
- Válassza ki az oszlop címét, hogy az adott oszlop értéke alapján rendezze az eredményeket.
- Adott felhasználók megkereséséhez használja a lap tetején található **Keresés** mezőt.


[!INCLUDE [footer-include](includes/footer-banner.md)]
