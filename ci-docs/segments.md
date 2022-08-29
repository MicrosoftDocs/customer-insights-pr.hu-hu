---
title: Szegmensek áttekintése
description: A szegmensek áttekintése, valamint információk a létrehozásukról és kezelésükről.
ms.date: 08/12/2022
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
ms.openlocfilehash: d4de3a6af6bc7d54305a23e3fbd3cc95d464d352
ms.sourcegitcommit: 267c317e10166146c9ac2c30560c479c9a005845
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/16/2022
ms.locfileid: "9304798"
---
# <a name="segments-overview"></a>Szegmensek áttekintése

A szegmensek segítségével csoportosíthatja ügyfeleit demográfiai-, tranzakciós- vagy viselkedési tulajdonságok alapján. A szegmensekkel népszerűsítheti az üzleti célok eléréséhez használható promóciós kampányokat, értékesítési tevékenységeket és ügyfélszolgálati tevékenységeket.

A szegmensdefiníciók szűrőinek megfelelő ügyfél- vagy kapcsolattartói profilokat egy szegmens tagjainak *nevezzük*. Bizonyos [szolgáltatási korlátozások](/dynamics365/customer-insights/service-limits) érvényesek.

## <a name="create-a-segment"></a>Szegmens létrehozása

Válassza ki, hogyan szeretne szegmenst létrehozni a cél célközönség alapján.

# <a name="individual-consumers-b-to-c"></a>[Egyéni fogyasztók (B-to-C)](#tab/b2c)

- Összetett szegmensek a szegmensépítővel: [Készítse el sajátját](segment-builder.md)
- Egyszerű szegmensek egyetlen operátorral: [Gyorsszegmens](segment-quick.md)
- AI-alapú módszer a hasonló ügyfelek megtalálására: [Hasonló ügyfelek](find-similar-customer-segments.md)
- AI-alapú javaslatok mértékek vagy attribútumok alapján: [Javasolt szegmensek mértékek alapján](suggested-segments.md)
- Javaslatok tevékenységek alapján: [Ügyféltevékenységen alapuló javasolt szegmensek](suggested-segments-activity.md)

# <a name="business-accounts-b-to-b"></a>[Üzleti számlák (B-to-B)](#tab/b2b)

Fiókok vagy kapcsolattartók szegmense (előzetes verzió) a szegmensépítővel: [Készítse el sajátját](segment-builder.md)

> [!NOTE]
> A legtöbb exportálási célhelyhez marketing célokra kapcsolattartási adatokra van szükség. Ezért hozzon létre kapcsolattartói szegmenseket az exportálásokhoz.

---

## <a name="manage-existing-segments"></a>Meglévő szegmensek kezelése

**A Szegmensek** lapon megtekintheti a létrehozott szegmenseket, azok állapotát és állapotát, valamint az adatok legutóbbi frissítésének időpontját. A szegmensek listáját rendezheti bármely oszlop szerint, vagy a keresőmező segítségével megkeresheti a kezelni kívánt szegmenst.

> [!TIP]
> B-to-B környezetekben a **célközönség Típus** oszlop azonosítja, hogy egy szegmens partnereken vagy kapcsolattartókon alapul-e.

Válasszon ki egy szegmenst az elérhető műveletek megtekintéséhez.

:::image type="content" source="media/segments-selected-segment.png" alt-text="Kijelölt szegmens az opciók legördülő listájával és a rendelkezésre álló lehetőségekkel." lightbox="media/segments-selected-segment.png":::

- [**Tekintse meg**](#view-segment-details) a szegmens részleteit, beleértve a tagok számának trendjét és a szegmenstagok előnézetét.
- A tagok listájának **letöltése** .CSV fájlként.
- **Szerkesztés** a szegmens szerkesztése a tulajdonságainak módosításához.
- **Duplikált elem létrehozása** a szegmensről. Dönthet úgy, hogy azonnal szerkeszti a tulajdonságait, vagy menti az ismétlődést.
- [**Frissítse**](#refresh-segments) a szegmenst, hogy a legfrissebb adatokat tartalmazza.
- Szegmens **Aktiválása** vagy **inaktiválása**. Az inaktív szegmensek nem frissülnek az [ütemezett frissítés](schedule-refresh.md) során, és az **Állapot** kihagyottként **jelenik** meg, ami azt jelzi, hogy a frissítést meg sem kísérelték. Az aktív szegmensek típusuk alapján frissülnek: statikus vagy dinamikus.
- **Statikussá** tenni vagy **dinamikussá** tenni a szegmens típusát. A statikus szegmenseket manuálisan kell frissíteni. A dinamikus szegmensek automatikusan frissülnek a rendszerfrissítések során.
- [**Keressen hasonló ügyfeleket**](find-similar-customer-segments.md) a szegmensből.
- Szegmens **átnevezése**.
- **Címke** a [szegmens címkéinek](work-with-tags-columns.md#manage-tags) kezeléséhez.
- [**Az exportálások**](#export-segments) kezelése az exportálással kapcsolatos szegmensek megtekintéséhez és kezeléséhez. [További információ az exportálásokról.](export-destinations.md)
- Szegmens **törlése**.
- **Oszlopok** a megjelenő oszlopok [testreszabásához](work-with-tags-columns.md#customize-columns).
- **Szűrés** a címkék [szűréséhez](work-with-tags-columns.md#filter-on-tags).
- **Keressen nevet** a szegmens neve szerinti kereséshez.

## <a name="view-segment-details"></a>Szegmens részleteinek megtekintése

**A Szegmensek** lapon válasszon ki egy szegmenst a feldolgozási előzmények és a szegmenstagok megtekintéséhez.

Az oldal felső részén egy trendgráf látható, amely a tagok számának változásait ábrázolja. Vigye az egérmutatót az adatpontok fölé, és tekintse meg egy adott napon a tagok számát. Módosítsa a vizualizáció időkeret.

:::image type="content" source="media/segment-time-range.png" alt-text="Szegmens időtartománya.":::

Az alsó rész a szegmenstagok listáját tartalmazza.

> [!NOTE]
> Az adott listában megjelenő mezők a szegmens entitásainak attribútumain alapulnak.
>
> A lista az egyeztetett szegmestagok előzetes verziója, és a szegmens első 100 rekordját mutatja, így gyorsan kiértékelheti, és szükség esetén felülvizsgálhatja a meghatározásokat. Az összes egyező rekord megtekintéséhez válassza a Továbbiak megtekintése lehetőséget **, amely megnyitja az** Entitások [**lapot, vagy**](entities.md) exportálja a szegmenst [.](export-destinations.md)

## <a name="refresh-segments"></a>Szegmensek frissítése

A szegmensek automatikus ütemezéssel frissíthetők, vagy igény szerint manuálisan frissíthetők. Egy vagy több szegmens manuális frissítéséhez jelölje ki őket, majd válassza a Frissítés **lehetőséget**.

Az automatikus frissítés ütemezéséhez [lépjen a Rendszergazdai](schedule-refresh.md) rendszerütemezés **lapra** > **·** > **.** A következő szabályok érvényesek:

- A Dinamikus **vagy** a Bővítés **típusú** szegmensek automatikusan frissülnek a beállított ütemben. A frissítés befejezése után az **Állapot** azt jelzi, hogy voltak-e problémák a szegmens frissítésével. Az **Utolsó frissítés** az utolsó sikeres frissítés időbélyegét jeleníti meg. Ha hiba történik, válassza ki a hibát a történtek részleteinek megtekintéséhez.
- A Statikus **típusú** *szegmensek nem* frissülnek automatikusan. Az **Utolsó frissítés** egy időbélyeget mutat arról, hogy a statikus szegmens utoljára manuálisan futtatták vagy frissítették.

[!INCLUDE [progress-details-include](includes/progress-details-pane.md)]

## <a name="export-segments"></a>Szegmensek exportálása

Exportálja a szegmenseket más alkalmazásokba az adatok további felhasználásához. Exportáljon egy szegmenst a szegmensek oldalról vagy az [exportálási oldalról](export-destinations.md).

1. Lépjen a Szegmensek **oldalra,** és válassza ki az exportálni kívánt szegmenst.

1. Válassza az Exportálások **kezelése lehetőséget**. Megnyílik az **Exportálás (előzetes verzió) szegmenshez** oldal. Tekintse meg az összes konfigurált exportálást aszerint csoportosítva, hogy tartalmazzák-e az aktuális szegmenst vagy sem.

   1. Ha a kijelölt szegmenst hozzá szeretné adni egy exportáláshoz, **Módosítsa** a megfelelő exportálást, és válassza ki a megfelelő szegmenst, majd mentse. Az egyes ügyfelek számára készült környezetekben válassza ki az exportálást a listából, majd válassza a Szegmens **hozzáadása lehetőséget** ugyanazon eredmény eléréséhez.

   1. Ha új exportálást szeretne létrehozni a kijelölt szegmenssel, válassza az **Exportálás hozzáadása** lehetőséget. Az exporálások létrehozásával kapcsolatos további információkért lásd: [Új exportálás beállítása](export-destinations.md#set-up-a-new-export).

1. Válassza a **Vissza** lehetőséget, hogy visszatérjen a szegmensek főoldalára.

## <a name="track-usage-of-a-segment"></a>Szegmens használatának nyomon követése

Ha olyan szegmenseket használ az alkalmazásokban, amelyek ugyanazon a szervezeten alapulnak, amely a Microsoft Dataverse Customer Insights szolgáltatáshoz kapcsolódik, nyomon követheti egy szegmens használatát. A Dynamics 365 Marketing [ügyfélútjaiban használt Customer Insights szegmensek esetében](/dynamics365/marketing/real-time-marketing-ci-profile) a rendszer tájékoztatja Önt az adott szegmens használatáról.

Amikor olyan szegmenst szerkeszt, amelyet a Customer Insights környezetben vagy a Marketing ügyfélút használ, a [szegmenskészítő](segment-builder.md) egyik szalagcíme tájékoztatja a függőségekről. Vizsgálja meg a függőség részleteit közvetlenül a szalagcímből, vagy válassza a Használat **lehetőséget** a szegmensépítőben.

A **Szegmenshasználat** panel a szegmens használatának részleteit jeleníti meg a Dataverse-alapú alkalmazásokban. Az ügyfélutakban használt szegmensek esetében talál egy hivatkozást, amely megvizsgálja az utazást a Marketingben, ahol ezt a szegmenst használják. Ha rendelkezik engedélyekkel a Marketing alkalmazás eléréséhez, tekintse meg az ott található további részleteket.

:::image type="content" source="media/segment-usage-pane.png" alt-text="Oldalsó panel a szegmenshasználat részleteivel a szegmenskészítőben.":::

A rendszer tájékoztatja Önt a nyomon követett szegmens használatáról, amikor megpróbálja törölni. Ha a törölni kívánt szegmenst a Marketing ügyfélút használja, az út a szegmens összes felhasználója számára leáll. Ha az út egy marketingkampány része, a törlés magára a kampányra lesz hatással. A figyelmeztetések ellenére azonban továbbra is törölheti a szegmenst.

:::image type="content" source="media/segment-usage-delete.png" alt-text="Párbeszédpanel a szegmens törlésének megerősítéséhez, ha egy szegmenst használ egy Dataverse alkalmazásban.":::

### <a name="supported-apps"></a>Támogatott alkalmazások

A használatot jelenleg a következő Dataverse-alapú alkalmazások követik nyomon:

- [Ügyfélutak a Dynamics 365 Marketing rendszerben](/dynamics365/marketing/real-time-marketing-ci-profile)

[!INCLUDE [footer-include](includes/footer-banner.md)]
