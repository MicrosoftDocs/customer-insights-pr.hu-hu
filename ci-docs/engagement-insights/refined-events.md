---
title: Események létrehozása és módosítása
description: Hogyan hozhat létre és módosíthat finomított eseményeket?
ms.reviewer: mhart
ms.author: jefhar
author: mochimochi016
ms.date: 10/01/2021
ms.service: customer-insights
ms.subservice: engagement-insights
ms.topic: how-to
ms.manager: shellyha
ms.openlocfilehash: 935dc4cd41218842e8406b747daef47de04e337a
ms.sourcegitcommit: 693458e13e4b4d94b6205093559912f6a4dc4a1c
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/06/2021
ms.locfileid: "7606220"
---
# <a name="create-and-modify-events"></a>Események létrehozása és módosítása

[!INCLUDE [cc-beta-prerelease-disclaimer](includes/cc-beta-prerelease-disclaimer.md)]

Az esemény a felhasználói viselkedésnek, például a webhelyen végzett tevékenységnek megfelelő adat.

- Az *alap* esemény akkor rögzít, amikor a felhasználó megtekint egy oldalt (esemény megtekintése), vagy együttműködik a tartalommal (műveletesemény).
- A *finomított* esemény az alapesemények virtuális nézete. Az eseményeket definiálja tulajdonságok eltávolításával és hozzáadásával, illetve az események tulajdonságértékek alapján való szűrésével.

## <a name="prerequisites"></a>Előfeltételek

Az események megtekintése érdekében kapcsolja össze a webhely adatait az elemzési információkkal egy egyszerű kódrészlet segítségével. További információkért lásd [A webes SDK telepítése egy webhelyre](instrument-website.md) részt.

 :::image type="content" source="media/new-events-connect-data.png" alt-text="Elsőként kapcsolja össze a hívásadatokat.":::

## <a name="create-refined-events"></a>Finomított események létrehozása

A finomított események segítségével leszűkítheti az alapeseményt [exportáláshoz](export-events.md), illetve eltávolíthatja azokat az eseményeket, amelyek nem szükségesek a kitettséghez vagy exportáláshoz.

> [!NOTE]
> Miután hozzáadta a webes SDK-t a webhelyéhez, megtekintheti az alapeseményeket, és létrehozhatja a finomított eseményeket. 

Az alapesemények megtekintése:

1. Válassza a bal navigációs ablaktáblán az **Adatok** elemet.

1. Az **Események** kiválasztása mezőben a munkaterületen található összes esemény felsorolása látható.

    :::image type="content" source="media/data-events.png" alt-text="Új események megtekintése.":::

Az alapeseményből származó finomított esemény létrehozása: 

1. A képernyő tetején válassza az **Adat** > **Események** lehetőséget, és válassza a **+ Új események** lehetőséget.

1. Az **Új események** párbeszédpanelen válassza ki az **Finomított emények létrehozása** lehetőséget, majd válassza a **Tovább** lehetőséget.
   
     :::image type="content" source="media/new-events-wizard.png" alt-text="Új események varázsló.":::
     
1. Az **Új események** párbeszédpanelen adja meg a következő adatokat:

   - Válasszon ki egy eseményt az **Alapesemények** legördülő menüből.
   - Adja meg a nevet a **Finomított események megjelenítendő neve** mezőben.
   - Tetszés szerint szóközök használata nélkül is frissítheti a **Tényleges nevet**.

1. A beállítások alkalmazásához válassza a **Létrehozás** lehetőséget.

A esemény azonnal megjelenik az **Események** listában.

### <a name="edit-event-name"></a>Finomított esemény neve

Módosíthatja egy alap- vagy egy finomított esemény nevét és tulajdonságait.

1. Lépjen az **Adatok** > **Események** pontra. 

1. Válassza a valamely eseményhez tartozó **További [...]** elemet, majd válassza a **Név szerkesztése** lehetőséget.
    
     :::image type="content" source="media/create-refined-events-options.png" alt-text="Finomított események létrehozási lehetőségei.":::

3. Frissítse az esemény nevét, és válassza az **Átnevezés** lehetőséget.

### <a name="view-the-details-of-a-refined-event"></a>A finomított esemény adatainak megtekintése.

1. Az **Esemény** listában jelölje ki az alap- vagy a finomított eseményt. 

1. Válassza a **Tulajdonságok hozzáadása és eltávolítása** lehetőséget a képernyő tetején a **Tulajdonságok szerkesztése** ablak megnyitásához. 

     :::image type="content" source="media/add-remove-properties.png" alt-text="Tulajdonságok hozzáadása és eltávolítása.":::

1. Jelölje be a jelölőnégyzeteket a mutatni kívánt, illetve elrejteni kívánt tulajdonságok kiválasztásához. 

   :::image type="content" source="media/edit-properties-refined-events.png" alt-text="Tulajdonságok szerkesztése finomított eseményekhez.":::

1. Válassza a **Megerősítés** lehetőséget a kijelölés alkalmazáshoz, majd válassza a **Mentés** lehetőséget.


### <a name="edit-selected-properties-for-a-refined-event"></a>Kiválasztott tulajdonságok szerkesztése egy finomított eseményhez

1. A részletes nézet megnyitásához nyissa meg az **Adatok** > **Események** lehetőséget, és válassza ki a részletes nézetben megnyitni kívánt finomított eseményeket.
1. Válassza a **Tulajdonságok hozzáadása és eltávolítása** lehetőséget. 
1. Szerkessze a jelölőnégyzetek kiválasztását.
1. A módosítások alkalmazáshoz válassza a **Megerősítés**, majd pedig a **Mentés** lehetőséget.

Az események exportálására vonatkozó információk az [Események exportálása](export-events.md) oldalon találhatók.
[!INCLUDE[footer-include](../includes/footer-banner.md)]
