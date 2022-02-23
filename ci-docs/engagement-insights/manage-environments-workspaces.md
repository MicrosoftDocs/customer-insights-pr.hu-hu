---
title: Munkaterületek és környezetek kezelése
description: Munkaterületek és környezetek létrehozása, átnevezése és törlése.
author: jusali
ms.reviewer: mhart
ms.author: jusali
ms.date: 10/01/2021
ms.service: customer-insights
ms.subservice: engagement-insights
ms.topic: how-to
ms.manager: shellyha
ms.openlocfilehash: 09cb3ddf0f8b4507b7eae6668ea3dad08cfcea29
ms.sourcegitcommit: 31985755c7c973fb1eb540c52fd1451731d2bed2
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/22/2021
ms.locfileid: "7673793"
---
# <a name="manage-environments-and-workspaces"></a>Környezetek és munkaterületek kezelése

[!INCLUDE [cc-beta-prerelease-disclaimer](includes/cc-beta-prerelease-disclaimer.md)]

## <a name="overview"></a>Áttekintés

A témakör ismerteti, hogyan kezelhetők a munkaterületek és a környezetek a létrehozás után. 

- A *munkaterület* olyan terület, amely tárolja és kezeli az eseményeket és jelentéseket. Itt valós időben lehet megtekinteni a felhasználói tevékenységeket. Munkaterület létrehozásakor kiválasztja a munkaterületre küldendő adatok típusát. Jelenleg a webes adatok és a mobilalkalmazások támogatottak. További információ: [Új munkaterület létrehozása és tagok felvétele](create-workspace.md).

- A *környezet* olyan hely, ahol a munkaterületeket és a kapcsolatokat kezelheti. További információ: [Új környezet létrehozása](create-new-environment.md).

## <a name="manage-an-existing-workspace"></a>Meglévő munkaterület kezelése

A környezetben egyidejűleg több munkaterület is fenntartható. A [szerepköre](user-roles.md) határozza meg, hogyan dolgozhat velük. 

 - A munkaterület kezeléséhez környezet-rendszergazdának vagy munkaterület-rendszergazdának kell lennie.
 - Munkaterület-rendszergazdaként átnevezheti a meglévő munkaterületeket, vagy törölheti azokat. 

:::image type="content" source="media/workspace-edit.png" alt-text="Munkaterületi rendszergazdaközpont.":::

### <a name="edit-a-workspace-name"></a>A munkaterület nevének szerkesztése

1. Nyissa meg a **Felügyelet** > **Munkaterület** lapot, és válassza a **Beállítások** lehetőséget.

1. A **Munkaterület neve** mezőbe írjon be egy új nevet.

1. Válassza a **Mentés** lehetőséget a módosítások alkalmazásához.

### <a name="delete-a-workspace"></a>Munkaterület törlése

A munkaterület törlése véglegesen eltávolítja az összes tartalmát, adatát, beállítását és engedélyét. Ez a művelet nem vonható vissza.

1. Nyissa meg a **Felügyelet** > **Munkaterület** lapot, és válassza a **Beállítások** lehetőséget.

1. Válassza a **Munkaterület törlése** lehetőséget. 

1. A **Munkaterület törlése** párbeszédpanelen írja be a **TÖRLÉS MEGERŐSÍTÉSE** parancsot minden felső beállításnál. 

1. A munkaterület végleges törléséhez írja be a **Törlés** lehetőséget.

### <a name="manage-workspace-members"></a>Munkaterületi tagok kezelése

1. Nyissa meg a **Felügyelet** > **Munkaterület** lapot, és válassza a **Tagok** lehetőséget.

1. Válassza a **Tagok hozzáadása** lehetőséget, ha hozzáférést és szerepköröket [szeretne hozzárendelni](user-roles.md). Jelenleg csak a **Munkaterület-rendszergazda** érhető el.

1. Jelölje ki a **Tagok felvétele** lehetőséget, és adja hozzá a munkaterületéhez.

## <a name="manage-an-existing-environment"></a>Meglévő környezet kezelése

A környezet rendszergazdájaként a bal navigációs ablakból hozzáférhet egy környezethez. Konfigurálhatja a környezetbeállításokat, más környezeti rendszergazdákat és a munkaterületeket. A felügyeleti központban a különböző területek közötti mozgáshoz válassza ki a lapokat.

:::image type="content" source="media/environment-edit.png" alt-text="Környezetfelügyeleti központ.":::

### <a name="edit-an-environment-name"></a>Környezetnév szerkesztése

1. Nyissa meg a **Felügyelet** > **Környezet** lapot, és válassza a **Beállítások** lehetőséget.

1. Frissítse a **Környezet neve** elemet, és válassza a **Mentés** lehetőséget a módosítások alkalmazásához.

### <a name="delete-an-environment"></a>Környezet törlése

A környezeti rendszergazdák törölhetik a környezetet. A környezet törlése előtt el kell távolítania az alatta található összes munkaterületet.

1. Nyissa meg a **Felügyelet** > **Környezet** lapot, és válassza a **Beállítások** lehetőséget.

1. Válassza a **Környezet törlése** lehetőséget. 

1. A **Munkaterület törlése** párbeszédpanelen írja be a **TÖRLÉS MEGERŐSÍTÉSE** parancsot minden felső beállításnál. 

1. A környezet végleges törléséhez válassza a **Törlés** lehetőséget.

### <a name="manage-environment-members"></a>Környezeti tagok kezelése

1. Nyissa meg a **Felügyelet** > **Környezet** lapot, és válassza a **Tagok** lehetőséget.

1. Válassza a **Tagok hozzáadása** lehetőséget, ha tagokat szeretne frissíteni és szerepköröket [szeretne hozzárendelni](user-roles.md). Jelenleg csak a **Környezet-rendszergazda** érhető el.

1. Jelölje ki a **Tagok felvétele** lehetőséget, és adja hozzá a környezetéhez.

## <a name="manage-connections"></a>Kapcsolatok kezelése

Ha kapcsolatokat hoz létre célközönség-információkhoz, egységes ügyfélprofilon alapuló, aktivitási információkhoz juthatnak a jelentések. 

További információkért lásd: [Hivatkozás létrehozása a célközönséggel kapcsolatos információk és az elkötelezettségi információk között](integrate-audience-insights-engagement-insights.md).

## <a name="manage-personal-data"></a>Személyes adatok kezelése

Az ügyfél személyes adatainak védelme érdekében törölheti vagy exportálhatja a végfelhasználók azonosítására alkalmas adatokat.

További információkért lásd: [Személyes adatokat tartalmazó eseményadatok törlése és exportálása](../dsr-rights-requests.md#deleting-and-exporting-event-data-containing-end-user-identifiable-information).

[!INCLUDE[footer-include](../includes/footer-banner.md)]
