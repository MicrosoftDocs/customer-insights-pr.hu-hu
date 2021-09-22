---
title: Finomított események létrehozása és módosítása
description: Finomított események létrehozása és módosítása.
ms.reviewer: mhart
ms.author: jefhar
author: mochimochi016
ms.date: 04/30/2021
ms.service: customer-insights
ms.subservice: engagement-insights
ms.topic: how-to
ms.manager: shellyha
ms.openlocfilehash: 0344bac5f4d43df853309f43c94d95f962937f77c936ed7305c5de4a08835f04
ms.sourcegitcommit: aa0cfbf6240a9f560e3131bdec63e051a8786dd4
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/10/2021
ms.locfileid: "7034777"
---
# <a name="create-and-modify-refined-events"></a>Finomított események létrehozása és módosítása

[!INCLUDE [cc-beta-prerelease-disclaimer](includes/cc-beta-prerelease-disclaimer.md)]


Az esemény a felhasználói viselkedésnek, például a webhelyen végzett tevékenységnek megfelelő adat.

- Az *alap* esemény akkor rögzít, amikor a felhasználó megtekint egy oldalt (esemény megtekintése), vagy együttműködik a tartalommal (műveletesemény).
- A *finomított* esemény az alapesemények virtuális nézete. Az eseményeket definiálja tulajdonságok eltávolításával és hozzáadásával, illetve az események tulajdonságértékek alapján való szűrésével.

A finomított események segítségével leszűkítheti az alapeseményt [exportáláshoz](export-events.md), illetve eltávolíthatja azokat az eseményeket, amelyek nem szükségesek a kitettséghez vagy exportáláshoz.

## <a name="create-refined-events"></a>Kifinomult események létrehozása

Alapeseményből háromféleképpen hozható létre finomított esemény. 

1. Lépjen az **Adatok**> **Események** elemre, és válasszon egyet az alábbi lehetőségek közül:
    - Jelölje ki az **Új események** lehetőséget, majd válassza a **Finomított események létrehozása** lehetőséget.
    - Válassza ki az alapeseményt, ha részletes nézetet nyit meg, majd válassza a felső menüből a **Finomított események létrehozása** parancsot.
    - Az alapesemény helyi menüjének megnyitásához válassza a **További [...]** lehetőséget. Ezután válassza **Finomított esemény létrehozása** lehetőséget.
    
    :::image type="content" source="media/create-refined-events-options.png" alt-text="Finomított események létrehozási lehetőségei.":::

1. A **Finomított esemény létrehozása** párbeszédpanelen adja meg a következő adatokat:

- Ha új eseményt hoz létre, akkor válasszon ki egy eseményt az **Alapesemények** legördülő menüből.
- Adja meg a nevet a **Finomított események megjelenítendő neve** mezőben.
- Tetszés szerint szóközök használata nélkül is frissítheti a **Tényleges nevet**.

3. A beállítások alkalmazásához válassza a **Létrehozás** lehetőséget.

1. A finomított esemény részletes nézetében válassza a **Tulajdonságok hozzáadása és eltávolítása** lehetőséget a **Tulajdonságok szerkesztése** ablak megnyitásához. 

1. Jelölje be a jelölőnégyzeteket a mutatni kívánt, illetve elrejteni kívánt tulajdonságok kiválasztásához. 
   :::image type="content" source="media/edit-properties-refined-events.png" alt-text="Tulajdonságok szerkesztése finomított eseményekhez.":::

1. Válassza a **Megerősítés** lehetőséget a kijelölés alkalmazáshoz.

1. A konfiguráció mentéséhez válassza a **Mentés** lehetőséget.

## <a name="edit-refined-events"></a>Finomított események szerkesztése

Módosíthatja a finomított esemény nevét és tulajdonságait.

### <a name="edit-event-name"></a>Finomított esemény neve

1. Lépjen az **Adatok** > **Események** pontra. 
1. Válassza a valamely eseményhez tartozó **További [...]** elemet, majd válassza a **Név szerkesztése** lehetőséget.
1. Frissítse az esemény nevét, és válassza az **Átnevezés** lehetőséget.

### <a name="edit-selected-properties"></a>Kijelölt tulajdonságok szerkesztése

1. A részletes nézet megnyitásához nyissa meg az **Adatok** > **Események** lehetőséget, és válassza ki a részletes nézetben megnyitni kívánt finomított eseményeket.
1. Válassza a **Tulajdonságok hozzáadása és eltávolítása** lehetőséget. 
1. Szerkessze a jelölőnégyzetek kiválasztását.
1. A módosítások alkalmazáshoz válassza a **Megerősítés**, majd pedig a **Mentés** lehetőséget.

Az események exportálására vonatkozó információk az [Események exportálása](export-events.md) oldalon találhatók.
[!INCLUDE[footer-include](../includes/footer-banner.md)]
