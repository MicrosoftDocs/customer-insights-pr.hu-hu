---
title: Célközönség betekintési információinak szegmensei
description: A szegmensek áttekintése, valamint információk a létrehozásukról és kezelésükről.
ms.date: 05/03/2021
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: JimsonChalissery
ms.author: jimsonc
ms.reviewer: mhart
manager: shellyha
ms.openlocfilehash: f1003b53b17e3ba2c37c0f2d94b89f7e97c2b6f10e28b7bbe93160e4c7f08d54
ms.sourcegitcommit: aa0cfbf6240a9f560e3131bdec63e051a8786dd4
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/10/2021
ms.locfileid: "7036376"
---
# <a name="segments-overview"></a>Szegmensek áttekintése

A szegmensek segítségével csoportosíthatja ügyfeleit demográfiai-, tranzakciós- vagy viselkedési tulajdonságok alapján. A szegmensekkel népszerűsítheti az üzleti célok eléréséhez használható promóciós kampányokat, értékesítési tevékenységeket és ügyfélszolgálati tevékenységeket.

A szegmensdefiníciók szűrőivel egyező ügyfélprofilokat a szegmensek *tagjainak* nevezik. Bizonyos [szolgáltatási korlátozások](service-limits.md) érvényesek.

## <a name="create-a-new-segment"></a>Új szegmens létrehozása

Új szegmens többféleképpen is létrehozható: 

- Összetett szegmens a szegmensszerkesztővel: [Üres szegmens](segment-builder.md#create-a-new-segment)
- Egyszerű szegmensek egyetlen operátorral: [Gyorsszegmens](segment-builder.md#quick-segments)
- Hasonló ügyfelek keresése AI-alapú megoldással: [Hasonló ügyfelek](find-similar-customer-segments.md)
- AI-alapú, mértékeken vagy attribútumokon alapuló javaslatok: [Javasolt szegmensek a mértékek javításához](suggested-segments.md)
- Javaslatok tevékenységek alapján: [Ügyféltevékenységen alapuló javasolt szegmensek](suggested-segments-activity.md)

## <a name="manage-existing-segments"></a>Meglévő szegmensek kezelése

A mentett szegmensek a **Szegmensek** oldalon tekinthetők és kezelhetők.

Minden szegmenshez egy sor tartozik; ez a sor további információkat tartalmaz a szegmensről.

:::image type="content" source="media/segments-selected-segment.png" alt-text="Kijelölt szegmens az opciók legördülő listájával és a rendelkezésre álló lehetőségekkel.":::

Szegmens kiválasztása esetén a következő művelet használható:

- **Megtekintés** a szegmens részleteinek, köztük a tagszám trendjének megtekintése és a szegmens tagjainak előnézete.
- **Szerkesztés** a szegmens szerkesztése a tulajdonságainak módosításához.
- **Duplikált elem létrehozása** a szegmensről. Megadhatja, hogy azonnal módosítja-e a tulajdonságait, vagy egyszerűen csak menti a duplikált példányt.
- **Frissítés** a szegmens frissítése a legfrissebb adatok felvételéhez.
- Szegmens **Aktiválása** vagy **inaktiválása**. A szegmensek két lehetséges állapottal rendelkeznek – aktívak vagy inaktívak. A szegmensek szerkesztésekor hasznosnak bizonyulnak ezek az állapotok. Inaktív szegmensek esetén a szegmens definíciója létezik, de még nem tartalmaz ügyfeleket. A szegmens aktiválásakor az állapota az "inaktív" értékről "aktív" állapotra változik, és a szegmens meghatározásnak megfelelő ügyfeleket keresi meg. Ha egy [ütemezett frissítés](system.md#schedule-tab) be van állítva, az inaktív szegmensek **állapota** **kihagyva** állapotú , jelezve, hogy a frissítést nem is kísérelte meg. Inaktív szegmens aktiválásakor a rendszer frissíti, és bekerül az ütemezett frissítésekbe.
  Másik lehetőségként használhatja **Ütemezés később** funkcióit az **Aktiválás/inaktiválás**, ahol megadhat egy adott szegmens aktiválására és inaktiválására vonatkozó jövőbeli dátumot és időpontot.
- Szegmens **átnevezése**.
- A tagok listájának **letöltése** .CSV fájlként.
- Az **Exportálások kezelése** az exporttal kapcsolatos szegmensek megtekintéséhez és kezeléséhez. [További információ az exportálásokról.](export-destinations.md)
- Szegmens **törlése**.

## <a name="refresh-segments"></a>Szegmensek frissítése

Az összes szegmenst egyszerre frissítheti a **Szegmensek** oldal **Az összes frissítése** elemével. Ha nem szeretné frissíteni az összes szegmenst, jelölje ki a frissítendőket, és válassza a **Frissítés** lehetőséget a beállítások között. Másik lehetőségként beállíthat egy ismétlődő frissítést is a **Felügyelet** > **Rendszer** > **Ütemezés** pontban.

> [!TIP]
> A feladatokhoz/folyamatokhoz [hatféle állapot](system.md#status-types) tartozhat. Emellett a legtöbb folyamat [más alsóbb szintű folyamatoktól is függ](system.md#refresh-policies). Kiválaszthatja egy folyamat állapotát, és megtekintheti a hozzá tartozó teljes feladat folyamatának részleteit. Miután kiválasztotta a **Részletek megtekintése** lehetőséget a feladat egyik feladatához, további információk jelennek meg: feldolgozási idő, legutóbbi feldolgozás dátuma, és a feladathoz társított összes hiba és figyelmeztetés.

## <a name="export-segments"></a>Szegmensek exportálása

Exportálhat egy szegmenst a szegmensek oldaláról vagy az [exportálások oldalról](export-destinations.md). 

1. Lépjen a **Szegmensek** oldalra.

1. Válassza ki a **Továbbiak megjelenítése [...]** lehetőséget exportálni kívánt szegmenshez.

1. Válassza az **Exportálás kezelése** lehetőséget a műveletek legördülő listából.

1. Megnyílik az **Exportálás (előzetes verzió) szegmenshez** oldal. Láthatja az összes konfigurált exportálást export szerint csoportosítva, amely tartalmazza az aktuális szegmenst, vagy nem tartalmazza azt.

   1. Ha a kijelölt szegmenst egy exportáláshoz szeretné hozzáadni, jelölje ki a listában az exportálást, és válassza a **Szegmens hozzáadása** lehetőséget.

   1. Ha új exportálást szeretne létrehozni a kijelölt szegmenssel, válassza az **Exportálás hozzáadása** lehetőséget. Az exporálások létrehozásával kapcsolatos további információkért lásd: [Új exportálás beállítása](export-destinations.md#set-up-a-new-export).

1. Válassza a **Vissza** lehetőséget, hogy visszatérjen a szegmensek főoldalára.

## <a name="view-processing-history-and-segment-members"></a>A feldolgozási előzmények és a szegmenstagok megtekintése

A szegmensre vonatkozó konszolidált adatokat a részleteinek áttekintésével tekintheti meg.

A **Szegmens** lapon válassza ki az áttekinteni kívánt szegments.

Az oldal felső részén egy trendgráf látható, amely a tagok számának változásait ábrázolja. Vigye az egérmutatót az adatpontok fölé, és tekintse meg egy adott napon a tagok számát.

Frissítheti az ábrázolás időkeretét.

> [!div class="mx-imgBorder"]
> ![Szegmens időtartománya.](media/segment-time-range.png "Szegmens időtartománya")

Az alsó rész a szegmenstagok listáját tartalmazza.

> [!NOTE]
> Az adott listában megjelenő mezők a szegmens entitásainak attribútumain alapulnak.
>
>A lista az egyeztetett szegmestagok előzetes verziója, és a szegmens első 100 rekordját mutatja, így gyorsan kiértékelheti, és szükség esetén felülvizsgálhatja a meghatározásokat. Az összes egyező bejegyzés megjelenítéséhez [exportálnia kell a szegmenst](export-destinations.md).

[!INCLUDE[footer-include](../includes/footer-banner.md)] 
