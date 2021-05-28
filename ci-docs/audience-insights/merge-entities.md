---
title: Entitások egyesítése az adategyesítésben
description: Entitások egyesítése az egyesített ügyfélprofilok létrehozásához.
ms.date: 05/10/2021
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: tutorial
author: adkuppa
ms.author: adkuppa
ms.reviewer: mhart
manager: shellyha
ms.openlocfilehash: 2cab702509596dd87c0c9b9769d1af8ba8387f9d
ms.sourcegitcommit: fcc94f55dc2dce84eae188d582801dc47696c9cc
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/20/2021
ms.locfileid: "6085579"
---
# <a name="merge-entities"></a>Entitások összefésülése

Az egyesítési fázis az adategységesítési folyamat legutolsó szakasza. Célja az ütköző adatok feloldása. Az adatütközés egyik példája egy ügyfélnév, amely két adathalmazban is megtalálható, de kis eltéréssel („Grant Marshall” és „Grant Marshal”), vagy egy telefonszám, ami csak formátumában tér el (617-803-091X és 617803091X). Az ütköző adatpontok egyesítése attribútumonként történik.

:::image type="content" source="media/merge-fields-page.png" alt-text="Oldalak egyesítése az adategyesítési folyamatban; az egységes ügyfélprofilt meghatározó egyesített mezőket tartalmazó táblázat látható.":::

Az [egyeztetési fázis](match-entities.md) befejezése után megkezdheti az egyesítési fázist az **Egyesítés** csempe kiválasztásával az **Egységesítés** oldalon.

## <a name="review-system-recommendations"></a>Rendszer javaslatainak áttekintése

Az **Adatok** > **Egységesítés** > **Egyesítés** részen válassza ki és zárja ki az egységes ügyfélprofilon belül egyesítendő attribútumokat. Az egységes ügyfélprofil az adategyesítési folyamat eredménye. A rendszer automatikusan egyesít néhány attribútumot.

Ha meg szeretné tekinteni az egyik automatikusan egyesített attribútumban szereplő attribútumokat, jelölje ki az egyesített attribútumot a tábla **Ügyfélmezők** lapján. Az egyesített attribútumot alkotó attribútumok két új sorban fognak megjelenni az egyesített attribútum alatt.

## <a name="separate-rename-exclude-and-edit-merged-fields"></a>Egyesített mezők szétválasztása, átnevezése, kizárása és szerkesztése

Módosíthatja, hogy a rendszer hogyan dolgozza fel az egyesített attribútumokat az egységes ügyfélprofil létrehozásához. Válassza a **Továbbiak** lehetőséget, és válassza ki a módosítandó elemet.

:::image type="content" source="media/manage-merged-attributes.png" alt-text="A Továbbiak legördülő menüben lévő, az egyesített attribútumok kezeléséhez rendelkezésre álló beállítások.":::

További információkat a következő szakaszokban talál.

## <a name="separate-merged-fields"></a>Egyesített mezők szétválasztása

Az egyesített mezők szétválasztásához keresse meg az attribútumot a táblázatban. A szétválasztott mezők egyéni adatpontokként jelennek meg az egységes ügyfélprofilban. 

1. Válassza ki az egyesített mezőt.
  
1. Válassza a **Továbbiak**, majd a **Mezők szétválasztása** lehetőséget.
 
1. Erősítse meg a szétválasztást.

1. A módosítások feldolgozásához válassza a **Mentés** és a **Futtatás** lehetőséget.

## <a name="rename-merged-fields"></a>Egyesített mezők átnevezése

Módosítsa az egyesített attribútumok megjelenítendő nevét. A kimeneti entitás neve nem módosítható.

1. Válassza ki az egyesített mezőt.
  
1. Válassza a **Továbbiak**, majd az **Átnevezés** lehetőséget.

1. Erősítse meg a módosított megjelenítendő nevet. 

1. A módosítások feldolgozásához válassza a **Mentés** és a **Futtatás** lehetőséget.

## <a name="exclude-merged-fields"></a>Egyesített mezők kizárása

Zárjon ki egy attribútumot az egységes ügyfélprofilból. Ha a mező más folyamatokban – például szegmensekben – használatos, akkor az ügyfélprofilból való kizárás előtt távolítsa el ezekből a folyamatokból. 

1. Válassza ki az egyesített mezőt.
  
1. Válassza a **Továbbiak**, majd a **Kizárás** lehetőséget.

1. Erősítse meg a kizárást.

1. A módosítások feldolgozásához válassza a **Mentés** és a **Futtatás** lehetőséget. 

Az összes kizárt mező megtekintéséhez az **EgyesítésMerge** oldalon válassza a **Kizárt mezők** lehetőséget. Ezen az ablaktáblán újra felveheti a kizárt mezőket.

## <a name="manually-combine-fields"></a>Mezők manuális kombinálása

Manuálisan adjon meg egy egyesített attribútumot. 

1. Az **Egyesítés** oldalon válassza a **Mezők kombinálása** lehetőséget.

1. Adja meg a **Nevet** és egy **Kimeneti mező nevét**.

1. Válasszon ki egy hozzáadni kívánt mezőt. További mezők kombinálásához válassza ki a **Mezők hozzáadása** lehetőséget.

1. Erősítse meg a kizárást.

1. A módosítások feldolgozásához válassza a **Mentés** és a **Futtatás** lehetőséget. 

## <a name="change-the-order-of-fields"></a>Mezők sorrendjének módosítása

Egyes entitások több adatot tartalmaznak, mint mások. Ha egy entitás egy mezőre vonatkozóan a legfrissebb adatokat tartalmazza, az értékek egyesítésekor prioritást adhat neki a többi entitáshoz képest.

1. Válassza ki az egyesített mezőt.
  
1. Válassza a **Továbbiak**, majd a **Szerkesztés** lehetőséget.

1. A **Mezők kombinálása** panelen válassza a **Mozgatás le/fel** lehetőséget a sorrend megadásához, vagy húzza a kívánt helyre az elemeket.

1. Erősítse meg a módosítást.

1. A módosítások feldolgozásához válassza a **Mentés** és a **Futtatás** lehetőséget.

## <a name="run-your-merge"></a>Az egyesítés futtatása

Függetlenül attól, hogy kézzel egyesíti-e az attribútumokat, vagy a rendszer egyesíti-e őket, bármikor futtathatja az egyesítést. A folyamat indításához az **Egyeztetés** oldalon válassza a **Futtatás** elemet.

> [!div class="mx-imgBorder"]
> ![Adatok egyesítése Mentés és Futtatás](media/configure-data-merge-save-run.png "Adatok egyesítése Mentés és Futtatás")

Ha csak az egységesített ügyfélentitásban szereplő kimenetet szeretné látni, válassza a **Csak az Egyesítés futtatása** lehetőséget. A lefelé irányuló folyamatok [a frissítési ütemezésében meghatározottak szerint](system.md#schedule-tab) frissülnek.

Ha a saját módosításaival szeretné frissíteni a rendszert, válassza az **Egyesítési és lefelé irányuló folyamatok futtatása** lehetőséget. Minden folyamat (beleértve a bővítést, a szegmenseket és a mértékeket is) újrafut. Miután az összes lefelé irányuló folyamat befejeződött, az ügyfélprofilokban megjelennek a végrehajtott módosítások.

Ha további módosításokat szeretne végrehajtani, majd újrafuttatná a lépést, megszakíthatja a folyamatban lévő egyesítést. Válassza ki a **Frissítés folyamatban...** szöveget és válassza a **Feladat megszakítása** lehetőséget a megjelenő oldalpanelen.

> [!TIP]
> A feladatokhoz/folyamatokhoz [hatféle állapot](system.md#status-types) tartozhat. Emellett a legtöbb folyamat [más alsóbb szintű folyamatoktól is függ](system.md#refresh-policies). Kiválaszthatja egy folyamat állapotát, és megtekintheti a hozzá tartozó teljes feladat folyamatának részleteit. Miután kiválasztotta a **Részletek megtekintése** lehetőséget a feladat egyik feladatához, további információk jelennek meg: feldolgozási idő, legutóbbi feldolgozás dátuma, és a feladathoz társított összes hiba és figyelmeztetés.

## <a name="next-step"></a>Következő lépés

Konfigurálja a [tevékenységek](activities.md), [bővítés](enrichment-hub.md) vagy [kapcsolatok](relationships.md) elemet, és még több információt kaphat ügyfeleiről.

Ha már konfigurált tevékenységeket, bővítést vagy szegmenseket, akkor a rendszer automatikusan feldolgozza őket, hogy a legújabb ügyféladatokat lehessen használni.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
