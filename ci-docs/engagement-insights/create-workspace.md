---
title: Új munkaterület létrehozása
description: A munkaterület célja és új létrehozása.
author: jusali
ms.reviewer: mhart
ms.author: jusali
ms.date: 10/01/2021
ms.service: customer-insights
ms.subservice: engagement-insights
ms.topic: how-to
ms.manager: shellyha
ms.openlocfilehash: 816f948331a06794c15000eb779f93cc7fdda202
ms.sourcegitcommit: 53b133a716c73cb71e8bcbedc6273cec70ceba6c
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/15/2021
ms.locfileid: "7645313"
---
# <a name="create-a-new-workspace-and-add-members"></a>Új munkaterület létrehozása és tagok hozzáadása

[!INCLUDE [cc-beta-prerelease-disclaimer](includes/cc-beta-prerelease-disclaimer.md)]

A munkaterületen valós időben megtekinthetők a felhasználói tevékenységek, hogy jobban megértsék célközönség. Itt tárol és kezelhet eseményeket és jelentéseket.

Munkaterület létrehozásakor kiválaszthatja, hogy milyen típusú adatokra összpontosítson. Bármikor hozzáadhat más felhasználókat vagy tagokat egy meglévő munkaterülethez. 

## <a name="create-a-new-workspace"></a>Új munkaterület létrehozása

A munkaterület létrehozásának folyamata magában foglalja a *környezet beállítását* a munkaterület rendszerezéséhez. A környezet egy vagy több munkaterületet tartalmazhat. A környezet segítségével kezelheti a munkaterületeket és a Customer Insights eszközhöz tartozó célközönség-információk szolgáltatást.

1. Válassza az **Új** lehetőséget a munkaterület-kapcsolóból.

   :::image type="content" source="media/new-workspace.png" alt-text="Customer Insights oldal lehívással a navigációs ablaktáblában és leírásban.":::

1. Írjon be egy **Munkaterület** nevet a **Munkaterület** panelen.

   :::image type="content" source="media/workspace-name.png" alt-text="Írjon be egy munkaterületnevet.":::

1. Válassza ki a mérni kívánt platformtípust (web vagy mobil).

1. Válassza a **Speciális beállítások** megjelenítése lehetőséget, ha engedélyezni vagy letiltani szeretné ezeket a nem kötelező beállításokat:

   - Állítja a kapcsolót az **Ismeretlenből ismert** lehetőségről "enabled" (Engedélyezve) értékre, hogy a webes eseményeket a korábban hitelesített felhasználókhoz társítsa. További információkért lásd: [Webes események felismerése a korábban hitelesített látogatóktól](unknown-to-known.md)
   - Állítsa a **Botok által generált forgalom** kapcsolót "engedélyezett" állásba, hogy eltávolítsa a robotok általi webes forgalmat ezen a munkaterületen. 

1. Válassza a **Kész** lehetőséget. 

1. Telepítse a kódrészletet, hogy elkezdje fogadni az adatokat, majd a **Befejezés** gombra kiválasztásával hozza létre a munkaterületet. További tudnivalókért lásd: [Fejlesztői erőforrások áttekintése](developer-resources.md).

> [!NOTE]
> Mostantól tagokat is hozzáadhat, és hozzárendelheti az engedélyek szintjét a **Szerepkör** listából. További információt az [Engedélyek és szerepkörök](user-roles.md) című cikkben talál. 

További információ a [Környezetek és munkaterületek kezelése](manage-environments-workspaces.md) oldalon található.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
