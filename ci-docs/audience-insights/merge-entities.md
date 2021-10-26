---
title: Entitások egyesítése az adategyesítésben
description: Entitások egyesítése az egyesített ügyfélprofilok létrehozásához.
ms.date: 10/10/2021
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: tutorial
author: adkuppa
ms.author: adkuppa
ms.reviewer: mhart
manager: shellyha
searchScope:
- ci-merge
ms.openlocfilehash: 6b3002b21ea043315e50724ec103aef8a3ced98e
ms.sourcegitcommit: 37182127b93b90846cc91fbeb26dd7a18cf5610a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/18/2021
ms.locfileid: "7648257"
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

:::image type="content" source="media/manage-merged-attributes.png" alt-text="Lehetőségek a Mutass többet legördülő menüben az egyesített attribútumok kezeléséhez.":::

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

1. Válasszon egy egyesített mezőt.
  
1. Válassza a **Továbbiak**, majd a **Kizárás** lehetőséget.

1. Erősítse meg a kizárást.

1. A módosítások feldolgozásához válassza a **Mentés** és a **Futtatás** lehetőséget. 

Az összes kizárt mező megtekintéséhez az **EgyesítésMerge** oldalon válassza a **Kizárt mezők** lehetőséget. Ezen az ablaktáblán újra felveheti a kizárt mezőket.

## <a name="edit-a-merged-field"></a>Egy egyesített mező szerkesztése

1.  Válasszon egy egyesített mezőt.

1.  Válassza a **Továbbiak**, majd a **Szerkesztés** lehetőséget.

1.  Adja meg a mezők egyesítésének vagy összefésülésének módját a következő három lehetőség egyikével:
    - **Fontosság**: A résztvevő mezőkhöz megadott fontossági rang alapján meghatározza a győztes értékét. Ez az alapértelmezett egyesítési beállítás. A fontosság sorrendjének beállításhoz válassza a **Mozgatás felfelé vagy lefelé** lehetőséget.
    :::image type="content" source="media/importance-merge-option.png" alt-text="Fontosság beállítás a mezők egyesítése párbeszédpanelen."::: 
    - **Legújabb**: A győztes értékét a leginkább friss alapján azonosítja. Az létrehozás idejének meghatározásához az egyesítés mezők hatókörében minden részt vevő entitáshoz dátum vagy numerikus mező szükséges.
    :::image type="content" source="media/recency-merge-option.png" alt-text="Viszonosság beállítás a mezők egyesítése párbeszédpanelen.":::
    - **Legérlegebbi**: A győztes értékét a leginkább régi alapján azonosítja. Az létrehozás idejének meghatározásához az egyesítés mezők hatókörében minden részt vevő entitáshoz dátum vagy numerikus mező szükséges.

1.  Az összefésülésben való részvételhez további mezőket adhat hozzá.

1.  Az egyesített mező átnevezhető.

1. Válassza a **Kész** lehetőséget a módosítások alkalmazásához.

1. A módosítások feldolgozásához válassza a **Mentés** és a **Futtatás** lehetőséget. 

## <a name="manually-combine-fields"></a>Mezők manuális kombinálása

Manuálisan adjon meg egy egyesített attribútumot. 

1. Az **Egyesítés** oldalon válassza a **Mezők kombinálása** lehetőséget.

1. Adja meg az egyesítés győztesének irányelvét a **Mezők összevonása a következő alapján:** legördülő menüben.

1. Válasszon ki egy hozzáadni kívánt mezőt. További mezők kombinálásához válassza ki a **Mezők hozzáadása** lehetőséget.

1. Adja meg a **Nevet** és egy **Kimeneti mező nevét**.

1. Válassza a **Kész** lehetőséget a módosítások alkalmazásához.

1. A módosítások feldolgozásához válassza a **Mentés** és a **Futtatás** lehetőséget. 

## <a name="change-the-order-of-fields"></a>Mezők sorrendjének módosítása

Egyes entitások több adatot tartalmaznak, mint mások. Ha egy entitás egy mezőre vonatkozóan a legfrissebb adatokat tartalmazza, az értékek egyesítésekor prioritást adhat neki a többi entitáshoz képest.

1. Válassza ki az egyesített mezőt.
  
1. Válassza a **Továbbiak**, majd a **Szerkesztés** lehetőséget.

1. A **Mezők kombinálása** panelen válassza a **Mozgatás le/fel** lehetőséget a sorrend megadásához, vagy húzza a kívánt helyre az elemeket.

1. Erősítse meg a módosítást.

1. A módosítások feldolgozásához válassza a **Mentés** és a **Futtatás** lehetőséget.

## <a name="configure-customer-id-generation"></a>Egyedi ügyfélazonosító létrehozásának konfigurálása 

A mezők egyesítésének konfigurálását követően megadhatja, hogyan hozza létre a CustomerId értékeket, az egyedi ügyfélprofil-azonosítókat. Az adategyesítési folyamat egyesítési lépése létrehozza az egyedi ügyfélprofil-azonosítót. Az azonosító az *Ügyfél* entitás CustomerId-azonosítója, amely az adategyesítési folyamat eredménye. 

Az Ügyfél entitás CustomerId értéke a nem null győztes elsődleges kulcsok első értékének kivonatán alapul. Ezek a kulcsok az egyesítés és összefésülés fázisában használt entitásokből jönnek, és ezeket az egyezések sorrendje befolyásolja.Így a létrehozott CustomerID módosulhat, ha egy elsődleges kulcs értéke megváltozik az egyeztetés sorrendjének elsődleges entitásában. Előfordulhat, hogy az elsődleges kulcs értéke nem mindig ugyanazt az ügyfelet képviseli.

A megbízható ügyfélazonosító konfigurálása lehetővé teszi, hogy elkerülje ezt a viselkedést.

**Egyedi ügyfélazonosító konfigurálása**

1. Válassza az **Egységesítés** > **Egyesítés** lehetőséget.

1. Válassza ki a **Kulcsok** lapot. 

1. Mutasson az egérrel a **CustomerId** sorra, és válassza a **Konfigurálás** lehetőséget.
   :::image type="content" source="media/customize-stable-id.png" alt-text="Vezérlés az azonosítók generálásának testreszabásához.":::

1. Jelöljön ki legfeljebb öt olyan mezőt, amely egyedi ügyfélazonosítót tartalmaz, és stabilabb. A konfigurációnak nem megfelelő rekordok a rendszer által konfigurált azonosítót kell használják.  

1. Válassza a **Kész** lehetőséget, majd a módosítások alkalmazásához futtassa az egyesítési folyamatot.

## <a name="group-profiles-into-households-or-clusters"></a>A csoportos profilokat háztartásokba vagy fürtökbe kell csoportosítani

Az ügyfélprofilok generálási konfigurációs folyamatának részeként szabályokat határozhat meg, amelyek fürtbe csoportosítják a kapcsolódó profilokat. Jelenleg két fürttípus áll rendelkezésre: háztartási és egyéni fürtök. A rendszer automatikusan kiválasztja az előre definiált szabályokkal való használatot, ha az *Ügyfél* entitása a *Person.LastName* és *Location.Address* szemantikus mezőket tartalmazza. Az [egyező szabályokhoz](match-entities.md#define-rules-for-match-pairs) hasonlóan saját szabályokkal és feltételekkel is létrehozhat fürtöt.

**Definiálás vagy fürt meghatározása**

1. Válassza az **Egységesítés** > **Egyesítés** lehetőséget.

1. Az **Egyesítés** lapon válassza a **Haladó** > **Fürt létrehozása** lehetőséget.

   :::image type="content" source="media/create-cluster.png" alt-text="Új fürt létrehozásához szükséges vezérlő.":::

1. Válasszon a **Háztartási** vagy az **Egyéni** fürt lehetőségekközül. Ha a *Person.LastName* és *Location.Address* szemantikus mezők léteznek az *Ügyfél* entitásban, a program automatikusan kiválasztja a címzett nevét.

1. Adja meg a fürt nevét, és válassza a **Kész** lehetőséget.

1. A létrehozott fürt kereséséhez válassza a **Fürtök** lapot.

1. Adja meg a fürt definiáló szabályait és feltételeit.

1. Válassza a **Futtatás** lehetőséget az egyesítési folyamat futtatásához és a fürt létrehozásához.

Az egyesítési folyamat futtatása után a fürtazonosítók új mezőként kerülnek az *Ügyfél* entitásába.

## <a name="run-your-merge"></a>Az egyesítés futtatása

Függetlenül attól, hogy kézzel egyesíti-e az attribútumokat, vagy a rendszer egyesíti-e őket, bármikor futtathatja az egyesítést. A folyamat indításához az **Egyeztetés** oldalon válassza a **Futtatás** elemet.

> [!div class="mx-imgBorder"]
> ![Adatok egyesítése Mentés és Futtatás.](media/configure-data-merge-save-run.png "Adatok egyesítése Mentés és Futtatás")

Ha csak az egységesített ügyfélentitásban szereplő kimenetet szeretné látni, válassza a **Csak az Egyesítés futtatása** lehetőséget. A lefelé irányuló folyamatok [a frissítési ütemezésében meghatározottak szerint](system.md#schedule-tab) frissülnek.

Ha a saját módosításaival szeretné frissíteni a rendszert, válassza az **Egyesítési és lefelé irányuló folyamatok futtatása** lehetőséget. Minden folyamat (beleértve a bővítést, a szegmenseket és a mértékeket is) újrafut. Miután az összes lefelé irányuló folyamat befejeződött, az ügyfélprofilokban megjelennek a végrehajtott módosítások.

Ha további módosításokat szeretne végrehajtani, majd újrafuttatná a lépést, megszakíthatja a folyamatban lévő egyesítést. Válassza ki a **Frissítés folyamatban...** szöveget és válassza a **Feladat megszakítása** lehetőséget a megjelenő oldalpanelen.

> [!TIP]
> Az egyesítési folyamat futtatása után válassza ki a folyamat állapotát a **Feladat részletei** ablaktábla megnyitásához. Áttekintést ad a feldolgozási időről, az utolsó feldolgozási dátumról, valamint a feladathoz kapcsolódó összes hibáról és figyelmeztetésről. Válassza a **Részletek megtekintése** lehetőséget, hogy lássa, mely entitások vettek részt az egyeztetési folyamatban, hogy az ütközések feloldása sikerült-e, és hogy sikerült-e közzétenni a frissítéseket.  
> A feladatokhoz/folyamatokhoz [hatféle állapot](system.md#status-types) tartozhat. Emellett a legtöbb folyamat [más alsóbb szintű folyamatoktól is függ](system.md#refresh-policies).  
> :::image type="content" source="media/process-detail-path.png" alt-text="A feladat állapotára mutató hivatkozás részleteinek lefúrási útvonala.":::

## <a name="next-step"></a>Következő lépés

Konfigurálja a [tevékenységek](activities.md), [bővítés](enrichment-hub.md) vagy [kapcsolatok](relationships.md) elemet, és még több információt kaphat ügyfeleiről.

Ha már konfigurált tevékenységeket, bővítést vagy szegmenseket, akkor a rendszer automatikusan feldolgozza őket, hogy a legújabb ügyféladatokat lehessen használni.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
