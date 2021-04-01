---
title: Entitások egyesítése az adategyesítésben
description: Entitások egyesítése az egyesített ügyfélprofilok létrehozásához.
ms.date: 04/16/2020
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: tutorial
author: adkuppa
ms.author: adkuppa
ms.reviewer: mhart
manager: shellyha
ms.openlocfilehash: 737c593353878a5e322488d00de5dc5db5befda9
ms.sourcegitcommit: bae40184312ab27b95c140a044875c2daea37951
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/15/2021
ms.locfileid: "5597836"
---
# <a name="merge-entities"></a>Entitások összefésülése

Az egyesítési fázis az adategységesítési folyamat legutolsó szakasza. Célja az ütköző adatok feloldása. Az adatütközés egyik példája egy ügyfélnév, amely két adathalmazban is megtalálható, de kis eltéréssel („Grant Marshall” és „Grant Marshal”), vagy egy telefonszám, ami csak formátumában tér el (617-803-091X és 617803091X). Az ütköző adatpontok egyesítése attribútumonként történik.

Az [egyeztetési fázis](match-entities.md) befejezése után megkezdheti az egyesítési fázist az **Egyesítés** csempe kiválasztásával az **Egységesítés** oldalon.

## <a name="review-system-recommendations"></a>Rendszer javaslatainak áttekintése

Az **Egyesítés** oldalon kiválaszthat és kizárhat attribútumokat az egységesített ügyfélprofil entitáson belüli egyesítésből (amely a konfigurációs folyamat eredménye). A rendszer automatikusan egyesít néhány attribútumot.

### <a name="view-merged-attributes"></a>Egyesített attribútumok megtekintése

Ha meg szeretné tekinteni az automatikusan egyesített attribútumok egyikében szereplő attribútumokat, jelölje ki az egyesített attribútumot. Az egyesített attribútumot alkotó két attribútum két új sorban fog megjelenni az egyesített attribútum alatt.

> [!div class="mx-imgBorder"]
> ![Egyesített attribútum kiválasztása](media/configure-data-merge-profile-attributes.png "Egyesített attribútum kiválasztása")

### <a name="separate-merged-attributes"></a>Egyesített attribútumok szétválasztása

Ha az automatikusan egyesített attribútumok bármelyikét szét szeretné választani vagy visszavonni az egyesítést keresse meg az attribútumot a **Profilattribútumok** táblában.

1. Válassza a három pont (...) választógombot.
  
2. A legördülő listában válassza a **Mezők szétválasztása** lehetőséget.

### <a name="remove-merged-attributes"></a>Egyesített attribútumok eltávolítása

Ha egy attribútumot ki szeretne zárni a végső Ügyfélprofil entitásból, keresse meg a **Profilattribútumok** táblában.

1. Válassza a három pont (...) választógombot.
  
2. A legördülő listában válassza a **Nincs egyesítés** lehetőséget.

   Az attribútum átkerül az **Eltávolítva ügyfélrekordból** szakaszba.

## <a name="manually-add-a-merged-attribute"></a>Egyesített attribútum manuális hozzáadása

Egyesített attribútum hozzáadásához nyissa meg az **Egyesítés** oldalt.

1. Válassza az **Egyesített attribútum kiválasztása** elemet.

2. Adjon meg egy **Nevet**, amellyel be tudja később azonosítani az **Egyesítés** oldalon.

3. Tetszés szerint megadhat egy **Megjelenítendő név** értéket is, amely megjelenik az egységesített Ügyfélprofil entitásban.

4. Konfigurálja az **Ismétlődő attribútumok kiválasztása** lehetőséget, hogy kiválassza azokat az attribútumokat, amelyeket egyesíteni szeretne az egyeztetett entitásokból. Az attribútumok keresésére is lehetőség van.

5. Állítsa be a **Rangsor fontosság szerint** elemet, hogy rangsorolja az egyik attribútumot a többi felett. Ha például a *WebAccountCSV* entitás tartalmazza a legpontosabb információkat a *Teljes nevek* attribútumáról, az entitást a *ContactCSV* fölé rangsorolhatja a *WebAccountCSV* kiválasztásával. Ennek eredményeként a *WebAccountCSV* az első prioritásba kerül, míg a *ContactCSV* második helyre kerül, amikor a *Teljes név* attribútum értékeit kéri le.

## <a name="run-your-merge"></a>Az egyesítés futtatása

Függetlenül attól, hogy kézzel egyesíti-e az attribútumokat, vagy a rendszer egyesíti-e őket, bármikor futtathatja az egyesítést. A folyamat indításához az **Egyeztetés** oldalon válassza a **Futtatás** elemet.

> [!div class="mx-imgBorder"]
> ![Adatok egyesítése Mentés és Futtatás](media/configure-data-merge-save-run.png "Adatok egyesítése Mentés és Futtatás")

A további módosítások elvégzéséhez és a lépés újrafuttatásához visszavonhat egy folyamatban lévő egyesítést. Válassza ki a **Frissítés folyamatban...** szöveget és válassza a **Feladat megszakítása** lehetőséget a megjelenő oldalpanelen.

Miután a **Frissítés folyamatban...** szöveg **Sikeres** elemre módosul, az egyesítés befejeződött, és megoldotta az adatokban levő ellentmondásokat a meghatározott házirendek alapján. Az egyesített és a nem egyesített attribútumok szerepelnek az egyesített profil entitásban. A kizárt attribútumok nem szerepelnek az egyesített profil entitásban.

Ha nem először sikerült az egyesítés futtatása, a rendszer automatikusan újrafuttatja az összes későbbi folyamatot, beleértve a bővítést, a szegmentálást és az intézkedéseket. Az összes folyamat újrafuttatását követően az ügyfelek profiljai tükrözik az elvégzett módosításokat.

> [!TIP]
> A feladatokhoz/folyamatokhoz [hatféle állapot](system.md#status-types) tartozhat. Emellett a legtöbb folyamat [más alsóbb szintű folyamatoktól is függ](system.md#refresh-policies). Kiválaszthatja egy folyamat állapotát, és megtekintheti a hozzá tartozó teljes feladat folyamatának részleteit. Miután kiválasztotta a **Részletek megtekintése** lehetőséget a feladat egyik feladatához, további információk jelennek meg: feldolgozási idő, legutóbbi feldolgozás dátuma, és a feladathoz társított összes hiba és figyelmeztetés.

## <a name="next-step"></a>Következő lépés

Konfigurálja a [tevékenységek](activities.md), [bővítés](enrichment-microsoft-graph.md) vagy [kapcsolatok](relationships.md) elemet, és még több információt kaphat ügyfeleiről.

Ha már beállította a tevékenységeket, a dúsítást vagy a kapcsolatok, vagy ha a szegmenseket definiálta, akkor a rendszer automatikusan feldolgozza a legfrissebb ügyféladatokat.




[!INCLUDE[footer-include](../includes/footer-banner.md)]