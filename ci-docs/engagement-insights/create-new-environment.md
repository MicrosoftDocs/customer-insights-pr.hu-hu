---
title: Új környezet létrehozása
description: A környezet célja és új létrehozása.
author: jusali
ms.reviewer: mhart
ms.author: jusali
ms.date: 10/04/2021
ms.service: customer-insights
ms.subservice: engagement-insights
ms.topic: how-to
ms.manager: shellyha
ms.openlocfilehash: 5e301b4ff0a7586fb143b154b773791b3bd645b7
ms.sourcegitcommit: 37182127b93b90846cc91fbeb26dd7a18cf5610a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/18/2021
ms.locfileid: "7648120"
---
# <a name="create-a-new-environment"></a>Új környezet létrehozása 

## <a name="overview"></a>Áttekintés

A környezet olyan hely, ahol a munkaterületeket és a kapcsolatokat kezelheti. A környezetek használata a szervezettől és a használt esettől függ. Lehetőség van például a következők létrehozására:

- Egyetlen környezet.
- A teszt- és éles környezetek szétválasztása.
- Környezeteket választhat szét a szervezeten belül egyes csoportokhoz vagy osztályokhoz, amelyek minden egyes szervezethez kapcsolódó eseményeket célközönség.
- Környezeteket választhat szét a vállalat világszerte található különféle leányvállalatai számára is.
- Célközönség-információk képesség kapcsolatai a Customer Insights eszközzel

## <a name="create-a-new-environment"></a>Új környezet létrehozása

1. A fő transzparens jobb oldalán válassza ki a környezetválasztót, majd **a +Új** lehetőséget.

   :::image type="content" source="media/environment-picker.png" alt-text="Környezetválasztó kiválasztása.":::

1. Írjon be egy **Környezet** nevet a **telepítőablakba**.

1. Válassza ki a partner **típusát** a terv típusától függően.

1. Válassza ki a **Régiót**, és válassza a **Tovább** lehetőséget. 

1. Írjon be egy **Munkaterület nevet**, amely lehetővé teszi adott webhelyre vagy alkalmazásokra vonatkozó adatok gyűjtését. További tudnivalókkal kapcsolatban lásd: [Munkaterület létrehozása](create-workspace.md).

1. Válassza ki a létrehozni kívánt **Munkaterület-típust** (web vagy mobil). 

1. Válassza a **Speciális beállítások** megjelenítése lehetőséget, ha engedélyezni vagy letiltani szeretné ezeket a nem kötelező beállításokat:

   - Állítja a kapcsolót az **Ismeretlenből ismert** lehetőségről "enabled" (Engedélyezve) értékre, hogy a webes eseményeket a korábban hitelesített felhasználókhoz társítsa. További információkért lásd: [Webes események felismerése a korábban hitelesített látogatóktól](unknown-to-known.md)
   - Állítsa a **Botok által generált forgalom** kapcsolót "engedélyezett" állásba, hogy eltávolítsa a robotok általi webes forgalmat ezen a munkaterületen. 

1. Válassza a **Kész** lehetőséget. 

1. Telepítse a kódrészletet, hogy elkezdje fogadni az adatokat, majd a **Befejezés** gombra kiválasztásával hozza létre a munkaterületet. További tudnivalókért lásd: [Fejlesztői erőforrások áttekintése](developer-resources.md).

> [!NOTE]
> Mostantól tagokat is hozzáadhat, és hozzárendelheti az engedélyek szintjét a **Szerepkör** listából. További információt az [Engedélyek és szerepkörök](user-roles.md) című cikkben talál. 

További információ a [Környezetek és munkaterületek kezelése](manage-environments-workspaces.md) oldalon található.

## <a name="work-with-your-new-environment"></a>Az új környezettel való munka

- [Munkaterület létrehozása](../engagement-insights/create-workspace.md) és tagok hozzáadása.
- [Adja hozzá a kódot a webhelyéhez](../engagement-insights/instrument-website.md) vagy a [mobilalkalmazáshoz](../engagement-insights/developer-resources.md#capture-events-from-mobile-apps).
- [Valós idejű jelentések](../engagement-insights/view-reports.md) megtekintése vagy [egyéni jelentések](../engagement-insights/custom-reports.md) létrehozása.
- [Finomított események létrehozása](../engagement-insights/refined-events.md) exportálásra.
- [Exportálja az adatokat](../engagement-insights/export-events.md) az Data Lake Storage-be.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
