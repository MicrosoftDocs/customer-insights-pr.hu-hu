---
title: Szegmensek az Ügyfélelemzésben
description: A szegmensek áttekintése, valamint információk a létrehozásukról és kezelésükről.
ms.date: 03/30/2022
ms.subservice: audience-insights
ms.topic: overview
author: JimsonChalissery
ms.author: jimsonc
ms.reviewer: v-wendysmith
manager: shellyha
searchScope:
- ci-customers-page
- ci-enrichment-details
- ci-segments
- ci-segment-details
- customerInsights
ms.openlocfilehash: 9791e971387eb7db91ed7c4e4fe76552656013ba
ms.sourcegitcommit: b7dbcd5627c2ebfbcfe65589991c159ba290d377
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/27/2022
ms.locfileid: "8642756"
---
# <a name="segments-overview"></a>Szegmensek áttekintése

A szegmensek segítségével csoportosíthatja ügyfeleit demográfiai-, tranzakciós- vagy viselkedési tulajdonságok alapján. A szegmensekkel népszerűsítheti az üzleti célok eléréséhez használható promóciós kampányokat, értékesítési tevékenységeket és ügyfélszolgálati tevékenységeket.

A szegmensdefiníciók szűrőivel egyező ügyfélprofilokat a szegmensek *tagjainak* nevezik. Bizonyos [szolgáltatási korlátozások](/dynamics365/customer-insights/service-limits) érvényesek.

## <a name="create-a-new-segment"></a>Új szegmens létrehozása

Új szegmens többféleképpen is létrehozható: 

# <a name="individual-consumers-b-to-c"></a>[Egyéni fogyasztók (B-to-C)](#tab/b2c)

- Összetett szegmens szegmensszerkesztővel: [Saját felépítés](segment-builder.md#create-a-new-segment) 
- Egyszerű szegmensek egyetlen operátorral: [Gyorsszegmens](segment-builder.md#quick-segments) 
- Hasonló ügyfelek keresése AI-alapú megoldással: [Hasonló ügyfelek](find-similar-customer-segments.md) 
- AI-alapú, mértékeken vagy attribútumokon alapuló javaslatok: [Javasolt szegmensek a mértékek javításához](suggested-segments.md) 
- Javaslatok tevékenységek alapján: [Ügyféltevékenységen alapuló javasolt szegmensek](suggested-segments-activity.md) 

# <a name="business-accounts-b-to-b"></a>[Üzleti számlák (B-to-B)](#tab/b2b)

- Összetett szegmens szegmensszerkesztővel: [Saját felépítés](segment-builder.md#create-a-new-segment)

---

## <a name="manage-existing-segments"></a>Meglévő szegmensek kezelése

Lépjen a **Szegmensek** lapra az összes mentett szegmens megtekintéséhez és kezeléséhez.

Minden szegmenshez egy sor tartozik; ez a sor további információkat tartalmaz a szegmensről.

:::image type="content" source="media/segments-selected-segment.png" alt-text="Kijelölt szegmens az opciók legördülő listájával és a rendelkezésre álló lehetőségekkel." lightbox="media/segments-selected-segment.png":::

Szegmens kiválasztásakor a következő műveletek érhetők el:

- **Megtekintés** a szegmens részleteinek, köztük a tagszám trendjének megtekintése és a szegmens tagjainak előnézete.
- A tagok listájának **letöltése** .CSV fájlként.
- **Szerkesztés** a szegmens szerkesztése a tulajdonságainak módosításához.
- **Duplikált elem létrehozása** a szegmensről. Megadhatja, hogy azonnal módosítja-e a tulajdonságait, vagy egyszerűen csak menti a duplikált példányt.
- **Frissítés** a szegmens frissítése a legfrissebb adatok felvételéhez.
- Szegmens **Aktiválása** vagy **inaktiválása**. Inaktív szegmensek esetén a szegmens definíciója létezik, de még nem tartalmaz ügyfeleket. Az aktív szegmens olyan ügyfeleket keres, akik megfelelnek a szegmensdefiníciónak. Ha egy [ütemezett frissítés](system.md#schedule-tab) be van állítva, az inaktív szegmensek **állapota** **kihagyva** állapotú , jelezve, hogy a frissítést nem is kísérelte meg. Inaktív szegmens aktiválásakor a rendszer frissíti, és bekerül az ütemezett frissítésekbe.
  Másik lehetőségként használhatja **Ütemezés később** funkcióit az **Aktiválás/inaktiválás**, ahol megadhat egy adott szegmens aktiválására és inaktiválására vonatkozó jövőbeli dátumot és időpontot.
- **[Keressen hasonló ügyfeleket](find-similar-customer-segments.md)** a szegmensből.
- Szegmens **átnevezése**.
- **Címke** a szegmens címkéinek [kezeléséhez](work-with-tags-columns.md#manage-tags).
- A tagok listájának **letöltése** .CSV fájlként.
- Az **Exportálások kezelése** az exporttal kapcsolatos szegmensek megtekintéséhez és kezeléséhez. [További információ az exportálásokról.](export-destinations.md)
- Szegmens **törlése**.
- **Oszlopok** a megjelenített oszlopok [testreszabásához](work-with-tags-columns.md#customize-columns).
- **Szűrjön** a címkék [szűréséhez](work-with-tags-columns.md#filter-on-tags).
- **A szegmensnév szerinti kereséshez keresett név** keresése.

## <a name="refresh-segments"></a>Szegmensek frissítése

Az összes szegmenst egyszerre frissítheti a **Szegmensek** oldal **Az összes frissítése** elemével. Ha nem szeretné frissíteni az összes szegmenst, jelölje ki a frissítendőket, és válassza a **Frissítés** lehetőséget a beállítások között. Másik lehetőségként beállíthat egy ismétlődő frissítést is a **Felügyelet** > **Rendszer** > **Ütemezés** pontban. Ismétlődő frissítés konfigurálásakor a következő szabályok érvényesek:
- A Dinamikus **vagy** Bővítés **típusú** szegmensek automatikusan frissülnek a beállított ütemben. Ha a frissítés befejeződött, az **állapot** azt jelzi, hogy problémák merültek-e fel a szegmens frissítésében. Az **Utolsó frissítés** az utolsó sikeres frissítés időbélyegét mutatja. Ha hiba történik, válassza ki a hibát a történtek részleteinek megtekintéséhez.
- A Statikus **típusú** *szegmensek nem* frissülnek automatikusan. Az **Utolsó frissítés** a statikus szegmensek manuális futtatásakor vagy frissítésének utolsó időbélyegét mutatja.

[!INCLUDE [progress-details-include](includes/progress-details-pane.md)]

## <a name="export-segments"></a>Szegmensek exportálása

Exportálhat egy szegmenst a szegmensek oldaláról vagy az [exportálások oldalról](export-destinations.md). 

1. Lépjen a **Szegmensek** oldalra.

1. Válassza ki a **Továbbiak megjelenítése [...]** lehetőséget exportálni kívánt szegmenshez.

1. Válassza az **Exportálás kezelése** lehetőséget a műveletek legördülő listából.

1. Megnyílik az **Exportálás (előzetes verzió) szegmenshez** oldal. Az összes konfigurált exportálást csoportosítva láthatja, hogy azok tartalmazzák-e az aktuális szegmenst vagy sem.

   1. Ha a kijelölt szegmenst hozzá szeretné adni egy exportáláshoz, **Módosítsa** a megfelelő exportálást, és válassza ki a megfelelő szegmenst, majd mentse. Egyéni ügyfelek környezetében kiválaszthatja a listában az exportálást, és a **Hozzáadás szegmens** lehetőséget választhatja ugyanez eléréséhez.

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


[!INCLUDE [footer-include](includes/footer-banner.md)]
