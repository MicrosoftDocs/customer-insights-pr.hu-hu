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
ms.openlocfilehash: 1f8922703af506974c8b5b24086b61f05a83609d
ms.sourcegitcommit: 31985755c7c973fb1eb540c52fd1451731d2bed2
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/22/2021
ms.locfileid: "7673446"
---
# <a name="create-a-new-workspace-and-add-members"></a>Új munkaterület létrehozása és tagok hozzáadása

[!INCLUDE [cc-beta-prerelease-disclaimer](includes/cc-beta-prerelease-disclaimer.md)]

A munkaterületen valós időben megtekinthetők a felhasználói tevékenységek, hogy jobban megértsék célközönség. Itt tárol és kezelhet eseményeket és jelentéseket.

Munkaterület létrehozásakor kiválaszthatja, hogy milyen típusú adatokra összpontosítson. Bármikor hozzáadhat más felhasználókat vagy tagokat egy meglévő munkaterülethez. 

## <a name="create-a-new-workspace"></a>Új munkaterület létrehozása

A munkaterület létrehozásának folyamata magában foglalja a *környezet beállítását* a munkaterület rendszerezéséhez. A környezet egy vagy több munkaterületet tartalmazhat. Környezetben kezelheti munkaterületeit és kapcsolatait a célközönség elemzési lehetőséghez.

1. Válassza a +Új lehetőséget **a** munkaterület-kapcsolóból.

   :::image type="content" source="media/new-workspace.png" alt-text="Ügyfélelemzések lap felirattal a navigációs ablakban és leírással.":::

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
