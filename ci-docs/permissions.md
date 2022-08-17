---
title: Felhasználói engedélyek hozzárendelése
description: További információk az engedélyekről és a felhasználói szerepkörökről.
ms.date: 08/08/2022
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
ms.openlocfilehash: a59a672b6f7e1e67c2162ea14bb9860df0d551aa
ms.sourcegitcommit: 49394c7216db1ec7b754db6014b651177e82ae5b
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/10/2022
ms.locfileid: "9245422"
---
# <a name="assign-user-permissions"></a>Felhasználói engedélyek hozzárendelése

A Customer Insightshoz való hozzáférés a szervezet azon felhasználóira korlátozódik, akiket egy rendszergazda ad hozzá az alkalmazáshoz. A rendszergazda hozzáadhat, szerkeszthet vagy távolíthat el felhasználókat. A felhasználó lehet egyetlen felhasználó, csoport vagy alkalmazás. A felhasználónak háromféle szerepköre lehet:

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
- Teljes **adategyesítés**, amely az egyesített ügyfélprofil-entitást eredményezi.
- Adja meg a **Kapcsolatokat** és **Tevékenységeket**.
- Hozzon létre szegmenseket a **Szegmensek** oldalán.
- Hozzon létre mérőszámokat a **Mérőszámok** oldalon.
- A konfiguráció kezelése és az ügyfelek profiljainak bővítése a **Bővítés** lapról (csak a belső bővítések esetében).
- Exportálások kezelése és létrehozása a közreműködőkkel megosztott kapcsolatok [alapján](connections.md#allow-contributors-to-use-a-connection-for-exports).

## <a name="admin"></a>Felügyelet

- A Közreműködő számára az összes engedély rendelkezésre áll.
- Módosítsa a beállításokat a **Rendszer** lapon, beleértve a munkanyelvet, a rendszerfolyamatok frissítési ütemezését és a diagnosztikai naplók exportálását.
- Módosítsa a beállításokat a Biztonság **lapon, beleértve a felhasználókat, az API-kulcsokat, a titkos hivatkozásokat és a** kulcstartót.
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

## <a name="add-users"></a>Felhasználók hozzáadása

1. Lépjen a Rendszergazdai biztonság elemre **, és válassza a** > **Felhasználók** **lapot.**

1. Válassza a **Felhasználók hozzáadása** lehetőséget az **Engedélyek hozzáadása/szerkesztése** ablaktábla megnyitásához.

1. **A Keresés** mező segítségével keresse meg a Azure Active Directory hozzáadni kívánt felhasználót vagy csoportot. Válassza ki azt a **szerepkört**, amelyet hozzá szeretne rendelni az adott felhasználóhoz vagy csoporthoz.

1. Válassza a **Mentés** parancsot. Az aktuális környezet automatikusan meg lesz osztva a csoport felhasználójával vagy tagjaival. A felhasználók a megadott szerepkörük szerint érhetik el a Customer Insights alkalmazást és a munkát.

## <a name="view-current-permissions"></a>Aktuális engedélyek megtekintése

A Rendszergazdai **biztonság** > **elemre kattintva** válassza a **Felhasználók** lapot az aktív felhasználók listájának és szerepkör-hozzárendelésük megtekintéséhez. A felhasználók listáját bármely oszlop szerint rendezheti, vagy a keresőmező segítségével megkereshet egy adott felhasználót.

## <a name="manage-current-users"></a>Jelenlegi felhasználók kezelése

Lépjen a Rendszergazdai biztonság elemre **, és válassza a** > **Felhasználók** **lapot.** A felhasználók listáját bármely oszlop szerint rendezheti, vagy a keresőmező segítségével megkeresheti a kezelni kívánt felhasználót.

Válasszon ki egy felhasználót az elérhető műveletek megtekintéséhez.

- **A szerkesztéssel** szerkesztheti a felhasználó szerepkörét a Customer Insights szolgáltatásban. Válassza a Mentés **lehetőséget** a módosítás megerősítéséhez.
- **Eltávolítással** távolítsa el, hogy eltávolítsa a felhasználót a Customer Insights szolgáltatáshoz való hozzáférésből. Válassza ki az **Eltávolítás** lehetőséget a törlés megerősítéséhez.

[!INCLUDE [footer-include](includes/footer-banner.md)]
