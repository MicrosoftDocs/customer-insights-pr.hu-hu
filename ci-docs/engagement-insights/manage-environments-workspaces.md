---
title: Munkaterületek és környezetek kezelése
description: Munkaterületek és környezetek létrehozása, átnevezése és törlése.
author: jusali
ms.reviewer: mhart
ms.author: jusali
ms.date: 07/01/2021
ms.service: customer-insights
ms.subservice: engagement-insights
ms.topic: how-to
ms.manager: shellyha
ms.openlocfilehash: bf310b1a50ba7baac5d11d5f22ff42003fbba516efd7d165c00b59adc958da2e
ms.sourcegitcommit: aa0cfbf6240a9f560e3131bdec63e051a8786dd4
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/10/2021
ms.locfileid: "7034045"
---
# <a name="manage-environments-and-workspaces"></a>Környezetek és munkaterületek kezelése

[!INCLUDE [cc-beta-prerelease-disclaimer](includes/cc-beta-prerelease-disclaimer.md)]

## <a name="overview"></a>Áttekintés

A munkaterület olyan terület, amely tárolja és kezeli az eseményeket és jelentéseket. Itt valós időben lehet megtekinteni a felhasználói tevékenységeket. Munkaterület létrehozásakor kiválasztja a munkaterületre küldendő adatok típusát. Jelenleg a webes adatok és a mobilalkalmazások támogatottak.

A környezet olyan hely, ahol a munkaterületeket és a kapcsolatokat kezelheti. A környezetek használata a szervezettől és a használt esettől függ. Lehetőség van például a következők létrehozására:

-   Egyetlen környezet.
-   A teszt- és éles környezetek szétválasztása.
-   Környezeteket választhat szét a szervezeten belül egyes csoportokhoz vagy osztályokhoz, amelyek minden egyes szervezethez kapcsolódó eseményeket célközönség.
-   Környezeteket választhat szét a vállalat világszerte található különféle leányvállalatai számára is.
-   Célközönség-információk képesség kapcsolatai a Customer Insights eszközzel

## <a name="choose-an-environment-and-create-a-workspace"></a>Válasszon ki egy környezetet, és hozzon létre munkaterületet 

Minden munkaterületnek környezetben kell lennie. Választhat meglévő környezetet, illetve létrehozhat újat munkaterület létrehozásakor. Ezt követően kiválaszthatja, hogy munkaterület-tagokat ad hozzá, és adatokat gyűjt.

**Az első saját munkaterület létrehozásához**

1. Az aktivitási információk segítségével válassza az **Új** lehetőségeket a munkaterület-átváltóból. 

   :::image type="content" source="media/New-workspace.png" alt-text="Customer Insights oldal munkaterület-választója.":::

1. Válasszon egy környezetet a listából, vagy válassza az **Új környezet létrehozása** lehetőséget.

1. Adjon egy nevet a **Munkaterület neve** mezőben. 

1. Válassza ki a létrehozni kívánt környezet típusát, attól függően, hogy mérni szeretné, mi történik egy webhelyen vagy egy mobilalkalmazásban. 

1. A **Szerepkör** listából tagokat adhat hozzá, és hozzájuk rendelheti a jogosultsági szintjüket. A munkaterület létrehozásához válassza a **Befejezés**, illetve a **Tovább** gombra a kód telepítéséhez. 

1. Telepítse a kódrészletet az adatok fogadásának elindításához, majd válassza a **Kész** lehetőséget. 

## <a name="manage-a-workspace"></a>Munkaterület kezelése

A környezetben egyidejűleg több munkaterület is fenntartható. A [szerepköre](user-roles.md) határozza meg, hogyan dolgozhat velük. 

 - A munkaterület kezeléséhez környezet-rendszergazdának vagy munkaterület-rendszergazdának kell lennie.
 - Munkaterület-rendszergazdaként átnevezheti a meglévő munkaterületeket, vagy törölheti azokat. 

### <a name="edit-a-workspace-name"></a>A munkaterület nevének szerkesztése

1. Nyissa meg a **Felügyelet** > **Munkaterület** lapot, és válassza a **Beállítások** lehetőséget.

1. A **Munkaterület neve** mezőbe írjon be egy új nevet.

1. Válassza a **Mentés** lehetőséget a módosítások alkalmazásához.

### <a name="delete-a-workspace"></a>Munkaterület törlése

A munkaterület törlésével véglegesen eltávolítja annak összes tartalmát, adatát, beállítását és engedélyét. Ez a művelet nem vonható vissza.

1. Nyissa meg a **Felügyelet** > **Munkaterület** lapot, és válassza a **Beállítások** lehetőséget.

1. Válassza a **Munkaterület törlése** lehetőséget. 

1. A **munkaterület törlése** párbeszédablakban írja be a **TÖRLÉS MEGERŐSÍTÉSE** parancsot. 

1. A munkaterület végleges törléséhez írja be a **Törlés** lehetőséget.

### <a name="manage-workspace-members"></a>Munkaterületi tagok kezelése

1. Nyissa meg a **Felügyelet** > **Munkaterület** lapot, és válassza a **Tagok** lehetőséget.

1. Válassza a **Tagok hozzáadása** lehetőséget, ha hozzáférést és szerepköröket [szeretne hozzárendelni](user-roles.md). Jelenleg csak a **Munkaterület-rendszergazda** érhető el.

1. Ha beállít egy [kapcsolatot a célközönség-információkhoz](configure-connections.md), akkor kiválaszthatja a **Profiladatokhoz való hozzáférés engedélyezése** lehetőséget, hogy a tagok [felhasználói profilokon](profile-reports.md) alapuló jelentéseket láthassanak.

1. Jelölje ki a **Tagok felvétele** lehetőséget, és adja hozzá a munkaterületéhez.

## <a name="manage-an-environment"></a>Egy környezet kezelése

A környezet rendszergazdájaként a bal navigációs ablakból hozzáférhet egy környezethez. A környezetbeállítások, más környezet-rendszergazdák, munkaterületek és kapcsolatok konfigurálhatók az [kapcsolatok a célközönség-információkhoz](configure-connections.md) elemhez. A felügyeleti központban a különböző területek közötti mozgáshoz válassza ki a lapokat.

:::image type="content" source="media/New-environment.png" alt-text="Környezetfelügyeleti központ.":::

### <a name="create-an-environment"></a>Környezet létrehozása

1. A munkaterület választóban válassza a **+Új** lehetőséget.

1. Az interaktív élményben nyissa meg a **Környezet** legördülő menüt, és válassza az **Új környezet létrehozása** lehetőséget. 

1. Adja meg a **Környezet nevét**.

   :::image type="content" source="media/create-environment.png" alt-text="Lépjen az interaktív élménybe a környezet részleteinek megadásához.":::

1. Válassza ki a **Régiót**, és válassza a **Tovább** lehetőséget. 

1. Adja meg a Munkaterület nevét, és adja meg, hogy milyen típusú munkaterületet szeretne létrehozni. 

1.  Tetszés szerint tagokat is hozzáadhat, és kódrészletet másolhatja létrehozási folyamat befejezéséhez.

### <a name="rename-an-environment"></a>Környezet átnevezése

1. Nyissa meg a **Felügyelet** > **Környezet** lapot, és válassza a **Beállítások** lehetőséget.

1. Frissítse a **Környezet neve** elemet, és válassza a **Mentés** lehetőséget a módosítások alkalmazásához.

### <a name="manage-environment-members"></a>Környezeti tagok kezelése

1. Nyissa meg a **Felügyelet** > **Környezet** lapot, és válassza a **Tagok** lehetőséget.

1. Válassza a **Tagok hozzáadása** lehetőséget, ha tagokat szeretne frissíteni és szerepköröket [szeretne hozzárendelni](user-roles.md). Jelenleg csak a **Környezet-rendszergazda** érhető el.

1. Ha beállít egy [kapcsolatot a célközönség-információkhoz](configure-connections.md), akkor kiválaszthatja a **Profiladatokhoz való hozzáférés engedélyezése** lehetőséget, hogy a tagok [felhasználói profilokon](profile-reports.md) alapuló jelentéseket láthassanak.

1. Jelölje ki a **Tagok felvétele** lehetőséget, és adja hozzá a környezetéhez.

### <a name="delete-an-environment"></a>Környezet törlése

A környezeti rendszergazdák törölhetik a környezetet. A környezet törlése előtt el kell távolítania az alatta található összes munkaterületet.

1. Nyissa meg a **Felügyelet** > **Környezet** lapot, és válassza a **Beállítások** lehetőséget.

1. Válassza a **Környezet törlése** lehetőséget. 

1. A **munkaterület törlése** párbeszédablakban írja be a **TÖRLÉS MEGERŐSÍTÉSE** parancsot. 

1. A környezet végleges törléséhez válassza a **Törlés** lehetőséget.

## <a name="manage-connections"></a>Kapcsolatok kezelése

Ha kapcsolatokat hoz létre célközönség-információkhoz, egységes ügyfélprofilon alapuló, aktivitási információkhoz juthatnak a jelentések. 

További információkért lásd: [Kapcsolatok konfigurálása](configure-connections.md).

## <a name="manage-personal-data"></a>Személyes adatok kezelése

Az ügyfél személyes adatainak védelme érdekében törölheti vagy exportálhatja a végfelhasználók azonosítására alkalmas adatokat.

További információkért lásd: [Személyes adatokat tartalmazó eseményadatok törlése és exportálása](delete-export-personal-data.md).


[!INCLUDE[footer-include](../includes/footer-banner.md)]
