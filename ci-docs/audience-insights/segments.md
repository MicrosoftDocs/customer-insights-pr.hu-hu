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
ms.openlocfilehash: a7fa6515bd6e79dedfb21aa0f0b8e24b873a6771
ms.sourcegitcommit: 8341fa964365c185b65bc4b71fc0c695ea127dc0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/14/2021
ms.locfileid: "6034015"
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

## <a name="get-insights-on-existing-segments"></a>Információk kérése meglévő szegmensekről

A meglévő szegmensekről további információt kaphat a [Szegmenssel kapcsolatos információk](segment-insights.md) használatával. Megtudhatja, hogy mi különbözteti meg a két szegmenst, illetve hogy mi a közös bennük.

## <a name="find-similar-customers"></a>Hasonló ügyfelek keresése

A kiválasztott szegmens tagjaihoz hasonló ügyfelek megkereshetők a mesterséges intelligencia segítségével. További információ: [Hasonló ügyfelek](find-similar-customer-segments.md).

## <a name="manage-existing-segments"></a>Meglévő szegmensek kezelése

A mentett szegmensek a **Szegmensek** oldalon tekinthetők és kezelhetők.

Minden szegmenshez egy sor tartozik; ez a sor további információkat tartalmaz a szegmensről.

> [!div class="mx-imgBorder"]
> ![Meglévő szegmensek kezelésére szolgáló lehetőségek](media/segments-selected-segment.png "Meglévő szegmensek kezelésére szolgáló lehetőségek")

Szegmens kiválasztása esetén a következő művelet használható:

- **Megtekintés** a szegmens részleteinek, köztük a tagszám trendjének megtekintése és a szegmens tagjainak előnézete.
- **Szerkesztés** a szegmens szerkesztése a tulajdonságainak módosításához.
- **Duplikált elem létrehozása** a szegmensről. Megadhatja, hogy azonnal módosítja-e a tulajdonságait, vagy egyszerűen csak menti a duplikált példányt.
- **Frissítés** a szegmens frissítése a legfrissebb adatok felvételéhez.
- Szegmens **Aktiválása** vagy **inaktiválása**. A szegmensek két lehetséges állapottal rendelkeznek – aktívak vagy inaktívak. A szegmensek szerkesztésekor hasznosnak bizonyulnak ezek az állapotok. Inaktív szegmensek esetén a szegmens definíciója létezik, de még nem tartalmaz ügyfeleket. A szegmens aktiválásakor az állapota az "inaktív" értékről "aktív" állapotra változik, és a szegmens meghatározásnak megfelelő ügyfeleket keresi meg. Ha egy [ütemezett frissítés](system.md#schedule-tab) be van állítva, az inaktív szegmensek **állapota** **kihagyva** állapotú , jelezve, hogy a frissítést nem is kísérelte meg. Inaktív szegmens aktiválásakor a rendszer frissíti, és bekerül az ütemezett frissítésekbe.
  Másik lehetőségként használhatja **Ütemezés később** funkcióit az **Aktiválás/inaktiválás**, ahol megadhat egy adott szegmens aktiválására és inaktiválására vonatkozó jövőbeli dátumot és időpontot.
- Szegmens **átnevezése**.
- A tagok listájának **letöltése** .CSV fájlként.
- A **Hozzáadás ehhez:** lehetőség a szegmensben szereplő ügyfelek azonosítóinak listáját egy másik alkalmazásban feldolgozásra küldi.
- Szegmens **törlése**.

## <a name="refresh-segments"></a>Szegmensek frissítése

Az összes szegmenst egyszerre frissítheti a **Szegmensek** oldal **Az összes frissítése** elemével. Ha nem szeretné frissíteni az összes szegmenst, jelölje ki a frissítendőket, és válassza a **Frissítés** lehetőséget a beállítások között. Másik lehetőségként beállíthat egy ismétlődő frissítést is a **Felügyelet** > **Rendszer** > **Ütemezés** pontban.

> [!TIP]
> A feladatokhoz/folyamatokhoz [hatféle állapot](system.md#status-types) tartozhat. Emellett a legtöbb folyamat [más alsóbb szintű folyamatoktól is függ](system.md#refresh-policies). Kiválaszthatja egy folyamat állapotát, és megtekintheti a hozzá tartozó teljes feladat folyamatának részleteit. Miután kiválasztotta a **Részletek megtekintése** lehetőséget a feladat egyik feladatához, további információk jelennek meg: feldolgozási idő, legutóbbi feldolgozás dátuma, és a feladathoz társított összes hiba és figyelmeztetés.

## <a name="view-processing-history-and-segment-members"></a>A feldolgozási előzmények és a szegmenstagok megtekintése

A szegmensre vonatkozó konszolidált adatokat a részleteinek áttekintésével tekintheti meg.

A **Szegmens** lapon válassza ki az áttekinteni kívánt szegments.

Az oldal felső részén egy trendgráf látható, amely a tagok számának változásait ábrázolja. Vigye az egérmutatót az adatpontok fölé, és tekintse meg egy adott napon a tagok számát.

Frissítheti az ábrázolás időkeretét.

> [!div class="mx-imgBorder"]
> ![Szegmens időtartománya](media/segment-time-range.png "Szegmens időtartománya")

Az alsó rész a szegmenstagok listáját tartalmazza.

> [!NOTE]
> Az adott listában megjelenő mezők a szegmens entitásainak attribútumain alapulnak.
>
>A lista az egyeztetett szegmestagok előzetes verziója, és a szegmens első 100 rekordját mutatja, így gyorsan kiértékelheti, és szükség esetén felülvizsgálhatja a meghatározásokat. Az összes egyező bejegyzés megjelenítéséhez [exportálnia kell a szegmenst](export-destinations.md).

[!INCLUDE[footer-include](../includes/footer-banner.md)] 
