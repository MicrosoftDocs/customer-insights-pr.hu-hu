---
title: Szegmensek áttekintése
description: A szegmensek áttekintése, valamint információk a létrehozásukról és kezelésükről.
ms.date: 05/20/2022
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
ms.openlocfilehash: 8b2c2f9b84bf8b7f37d1468b871946ecb3e6aa98
ms.sourcegitcommit: a97d31a647a5d259140a1baaeef8c6ea10b8cbde
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/29/2022
ms.locfileid: "9050950"
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

Lépjen a Szegmensek **oldalra az** összes mentett szegmens megtekintéséhez és kezeléséhez.

Minden szegmenshez egy sor tartozik; ez a sor további információkat tartalmaz a szegmensről.

:::image type="content" source="media/segments-selected-segment.png" alt-text="Kijelölt szegmens az opciók legördülő listájával és a rendelkezésre álló lehetőségekkel." lightbox="media/segments-selected-segment.png":::

A szegmens kiválasztásakor a következő műveletek érhetők el:

- **Megtekintés** a szegmens részleteinek, köztük a tagszám trendjének megtekintése és a szegmens tagjainak előnézete.
- A tagok listájának **letöltése** .CSV fájlként.
- **Szerkesztés** a szegmens szerkesztése a tulajdonságainak módosításához.
- **Duplikált elem létrehozása** a szegmensről. Dönthet úgy, hogy azonnal szerkeszti a tulajdonságait, vagy menti az ismétlődést.
- **Frissítés** a szegmens frissítése a legfrissebb adatok felvételéhez.
- Szegmens **Aktiválása** vagy **inaktiválása**. Inaktív szegmensek esetén a szegmens definíciója létezik, de még nem tartalmaz ügyfeleket. Az aktív szegmens olyan ügyfeleket keres, akik megfelelnek a szegmensdefiníciónak. Ha egy [ütemezett frissítés](system.md#schedule-tab) be van állítva, az inaktív szegmensek **állapota** **kihagyva** állapotú , jelezve, hogy a frissítést nem is kísérelte meg. Inaktív szegmens aktiválásakor a rendszer frissíti, és bekerül az ütemezett frissítésekbe.
  Másik lehetőségként használhatja **Ütemezés később** funkcióit az **Aktiválás/inaktiválás**, ahol megadhat egy adott szegmens aktiválására és inaktiválására vonatkozó jövőbeli dátumot és időpontot.
- **[Keressen hasonló ügyfeleket](find-similar-customer-segments.md)** a szegmensből.
- Szegmens **átnevezése**.
- **Címke** a [szegmens címkéinek](work-with-tags-columns.md#manage-tags) kezeléséhez.
- A tagok listájának **letöltése** .CSV fájlként.
- Az **Exportálások kezelése** az exporttal kapcsolatos szegmensek megtekintéséhez és kezeléséhez. [További információ az exportálásokról.](export-destinations.md)
- Szegmens **törlése**.
- **Oszlopok** a megjelenő oszlopok [testreszabásához](work-with-tags-columns.md#customize-columns).
- **Szűrés** a címkék [szűréséhez](work-with-tags-columns.md#filter-on-tags).
- **Keressen nevet** a szegmens neve szerinti kereséshez.

## <a name="refresh-segments"></a>Szegmensek frissítése

Az összes szegmenst egyszerre frissítheti a **Szegmensek** oldal **Az összes frissítése** elemével. Ha nem szeretné frissíteni az összes szegmenst, jelölje ki a frissítendőket, és válassza a **Frissítés** lehetőséget a beállítások között. Másik lehetőségként beállíthat egy ismétlődő frissítést is a **Felügyelet** > **Rendszer** > **Ütemezés** pontban. Ismétlődő frissítés konfigurálásakor a következő szabályok érvényesek:

- A Dinamikus **vagy** a Bővítés **típusú** szegmensek automatikusan frissülnek a beállított ütemben. A frissítés befejezése után az **Állapot** jelzi, hogy voltak-e problémák a szegmens frissítésével. Az **Utolsó frissítés** az utolsó sikeres frissítés időbélyegét jeleníti meg. Ha hiba történik, válassza ki a hibát a történtek részleteinek megtekintéséhez.
- A Statikus **típusú** *szegmensek nem* frissülnek automatikusan. Az **Utolsó frissítés** a statikus szegmensek manuális futtatásának vagy frissítésének időbélyegét mutatja.

[!INCLUDE [progress-details-include](includes/progress-details-pane.md)]

## <a name="export-segments"></a>Szegmensek exportálása

Exportálhat egy szegmenst a szegmensek oldaláról vagy az [exportálások oldalról](export-destinations.md). 

1. Lépjen a **Szegmensek** oldalra.

1. Válassza ki az exportálni kívánt szegmens függőleges három pontját (&vellip;).

1. Válassza az **Exportálás kezelése** lehetőséget a műveletek legördülő listából.

1. Megnyílik az **Exportálás (előzetes verzió) szegmenshez** oldal. Az összes konfigurált exportálást csoportosítva láthatja, hogy azok tartalmazzák-e az aktuális szegmenst vagy sem.

   1. Ha a kijelölt szegmenst hozzá szeretné adni egy exportáláshoz, **Módosítsa** a megfelelő exportálást, és válassza ki a megfelelő szegmenst, majd mentse. Az egyes ügyfelek számára készült környezetekben ehelyett kiválaszthatja az exportálást a listában, és kiválaszthatja a Szegmens **hozzáadása lehetőséget** ugyanazon eredmény eléréséhez.

   1. Ha új exportálást szeretne létrehozni a kijelölt szegmenssel, válassza az **Exportálás hozzáadása** lehetőséget. Az exporálások létrehozásával kapcsolatos további információkért lásd: [Új exportálás beállítása](export-destinations.md#set-up-a-new-export).

1. Válassza a **Vissza** lehetőséget, hogy visszatérjen a szegmensek főoldalára.

## <a name="track-usage-of-a-segment"></a>Szegmens használatának nyomon követése

Ha olyan szegmenseket használ az alkalmazásokban, amelyek ugyanazon Microsoft Dataverse a szervezeten alapulnak, amely a Customer Insightshoz kapcsolódik, nyomon követheti egy szegmens használatát. A Dynamics 365 Marketing [ügyfélútjaiban használt Customer Insights szegmensek esetében](/dynamics365/marketing/real-time-marketing-ci-profile) a rendszer tájékoztatja Önt az adott szegmens használatáról.

Amikor olyan szegmenst szerkeszt, amelyet a Customer Insights környezetben vagy a Marketing ügyfélút használ, a [szegmenskészítő](segment-builder.md) egyik szalagcíme tájékoztatja a függőségekről. A függőség részleteit megvizsgálhatja közvetlenül a szalagcímből, vagy a szegmensépítő Használat **lehetőségének kiválasztásával**.

A **Szegmenshasználat** panel a szegmens használatának részleteit jeleníti meg a Dataverse-alapú alkalmazásokban. Az ügyfélutakban használt szegmensek esetében talál egy hivatkozást, amely megvizsgálja az utazást a Marketingben, ahol ezt a szegmenst használják. Ha rendelkezik engedéllyel a Marketing alkalmazás eléréséhez, ott további részleteket érhet el.

:::image type="content" source="media/segment-usage-pane.png" alt-text="Oldalsó panel a szegmenshasználat részleteivel a szegmenskészítőben.":::

A rendszer tájékoztatja Önt a nyomon követett szegmens használatáról, amikor megpróbálja törölni. Ha a törölni kívánt szegmenst a Marketing ügyfélút használja, az út a szegmens összes felhasználója számára leáll. Ha az út egy marketingkampány része, a törlés magára a kampányra lesz hatással. A figyelmeztetések ellenére azonban továbbra is törölheti a szegmenst.

:::image type="content" source="media/segment-usage-delete.png" alt-text="Párbeszédpanel a szegmens törlésének megerősítéséhez, ha egy szegmenst használ egy Dataverse alkalmazásban.":::

### <a name="supported-apps"></a>Támogatott alkalmazások

A használatot jelenleg a következő Dataverse-alapú alkalmazások követik nyomon:

- [Ügyfélutak a Dynamics 365 Marketing rendszerben](/dynamics365/marketing/real-time-marketing-ci-profile)

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
