---
title: Rendszerkonfiguráció a célközönség információk funkcióban
description: Ismerkedjen meg a rendszerbeállításokkal Dynamics 365 Customer Insights célközönség információkban.
ms.date: 06/02/2020
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
ms.reviewer: nimagen
manager: shellyha
ms.openlocfilehash: 7dd72e6512cd87ac70235d21667399298408db21
ms.sourcegitcommit: cf9b78559ca189d4c2086a66c879098d56c0377a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/03/2020
ms.locfileid: "4406022"
---
# <a name="system-configuration"></a>Rendszerkonfiguráció

A **Rendszer** oldal négy lapból áll: **Állapot**, **Ütemezés**, **Névjegy** és **Általános**.

> [!div class="mx-imgBorder"]
> ![Rendszer oldal](media/system-tabs.png "Rendszer oldal")

## <a name="status-tab"></a>Állapot lap

Az **Állapot lapon** nyomon követheti az adatbetöltés folyamatát, az adatok exportálását, valamint számos fontos termékfolyamatot. Tekintse át az ezen az oldalon található információkat, hogy megbizonyosodhasson az aktív folyamatok pontos működéséről.

Ezen a lapon az **Adatforrások**, a **Rendszerfolyamatok** és az **Adatelőkészítés** állapotjelentései szerepelnek. Minden tábla nyomon követi a feladat **Nevét**, valamint a hozzá tartozó entitást, a legutóbbi futtatás **Állapotát**, illetve azt, mikor történt a **Legutóbbi frissítés**.

A feladat utolsó néhány futtatásának részleteit a feladat nevét kijelölve tekintheti meg.

### <a name="status-types"></a>Állapottípusok

A feladatokhoz hatféle állapot tartozhat. A következő állapottípusok szintén megjelennek az *Egyeztetés*, az *Egyesítés*, az *Adatforrások*, a *Szegmensek*, a *Mértékek*, a *Bővítés*, a *Tevékenységek*, és az *Előrejelzések* oldalon:

- **Feldolgozás:** A feladat folyamatban van. Az állapot megváltozhat, Sikeres vagy Sikertelen állapotra.
- **Sikeres:** a feladat sikeresen befejeződött.
- **Kihagyva:** A feladat kimaradt. Egy vagy több olyan alsóbb szintű folyamat kimaradt vagy hibás volt, amelytől ez a feladat függ.
- **Sikertelen:** a feladat feldolgozása nem sikerült.
- **Megszakítva:** a feldolgozást a felhasználó a befejeződése előtt visszavonta.
- **Feldolgozási sorban:** A feldolgozás várólistára kerül, és a rendszer az összes későbbi feladat befejezését követően indul el. További információ: [Irányelvek frissítése](#refresh-policies).

### <a name="refresh-policies"></a>Irányelvek frissítése

A lista megmutatja a frissítési szabályzatokat minden egyes fő folyamathoz:

- **Adatforrások:** S [beállított ütemezésnek](#schedule-tab) megfelelően fut. Nem függ más folyamattól. A egyeztetés a folyamat sikeres befejezésétől függ.
- **Egyeztetés:** A [beállított ütemezésnek](#schedule-tab) megfelelően fut. Az egyeztetés definíciójában használt adatforrások feldolgozásából függ. A egyesítés a folyamat sikeres befejezésétől függ.
- **Egyesítés:** A [beállított ütemezésnek](#schedule-tab) megfelelően fut. Az egyeztetési folyamat befejezésétől függ. A szegmensek, a mértékek, a bővítés, a keresés, a tevékenységek, az előrejelzések és az adatok előkészítése a folyamat sikeres befejezésének függvénye.
- **Szegmensek**: Manuálisan fut (egyszeri frissítés) és a [konfigurális ütemezésnek](#schedule-tab) megfelelően. Az Egyesítéstől függ. Az Insights a feldolgozástól függ.
- **Mértékek**: Manuálisan fut (egyszeri frissítés) és a [konfigurális ütemezésnek](#schedule-tab) megfelelően. Az Egyesítéstől függ.
- **Tevékenységek**: Manuálisan fut (egyszeri frissítés) és a [konfigurális ütemezésnek](#schedule-tab) megfelelően. Az Egyesítéstől függ.
- **Bővítés**: Manuálisan fut (egyszeri frissítés) és a [konfigurális ütemezésnek](#schedule-tab) megfelelően. Az Egyesítéstől függ.
- **Keresés**: Manuálisan fut (egyszeri frissítés) és a [konfigurális ütemezésnek](#schedule-tab) megfelelően. Az Egyesítéstől függ.
- **Adat-előkészítés:** A [beállított ütemezésnek](#schedule-tab) megfelelően fut. Az Egyesítéstől függ.
- **Betekintő információk**: Manuálisan fut (egyszeri frissítés) és a [konfigurális ütemezésnek](#schedule-tab) megfelelően. A Szegmensektől függ.

Válassza ki egy feladat állapotát, és megtekintheti a hozzá tartozó teljes feladat folyamatának részleteit. A fenti frissítésre vonatkozó irányelvek segítségével megtudhatja, hogy mit tehet a **kihagyott** vagy **várólistán lévő** feladat kezelésére.

## <a name="schedule-tab"></a>Ütemezés lap

Használja az **Ütemezés** lapot, hogy ütemezze az automatikus frissítéseket minden egyes [betáplált adatforrásához](data-sources.md). Az automatikus frissítéssel biztosítható, hogy az adatforrásokból származó frissítések megjelenjenek az egyesített ügyfélprofilokban.

1. A célközönség információkban nyissa meg a **Rendszergazda** > **Rendszer** menüt és válassza az **Ütemezés** lapot.

2. Az ütemezett frissítés alapértelmezett állapota **Ki**. Az ütemezett frissítések engedélyezéséhez módosítsa a képernyő felső részén látható váltógombot **Be** állásra.

3. Választhat **Heti** (alapértelmezett) és **Napi** frissítések között. Ha heti frissítéseket szeretne ütemezni, jelöljön ki egy vagy több napot, amikor a frissítést futtatni szeretné.

4. Állítsa be az **Időzónát**, majd az **Idő** legördülő listában állítsa be a frissítés időpontját. Ha kész, válassza a **Beállítás** lehetőséget. Ha egy nap alatt több frissítést szeretne ütemezni, válassza a **Másik időpont hozzáadása**.

5. Válassza a **Mentés** lehetőséget a módosítások alkalmazásához.

## <a name="about-tab"></a>Névjegy lap

A **Névjegy** lapon a szervezet **megjelenítendő neve**, az aktív **környezeti azonosító**, a **régió** és a **munkamenet azonosítója** szerepel. Ha egynél több munkakörnyezet van, érdemes mindegyiknek adnia egy könnyen azonosítható megjelenítendő nevet.

## <a name="general-tab"></a>Általános lap

Két beállítás szerepel az **Általános** lapon, a **Nyelv** és az **Ország/régió formátuma**.

Az alkalmazás [számos nyelvet támogat](supported-languages.md). Az előnyben részesített nyelv megváltoztatásához válasszon egy **nyelvet** a legördülő listából.

Ha módosítani szeretné a dátumok, időpontok és számok preferált formázását, használja az **ország/régiók formátuma** a legördülő listában. Ebben a mezőben egy formázási előnézet jelenik meg. A rendszer automatikusan ajánlani fog egy választási lehetőséget, amikor új nyelvet választ ki.

A **Mentés** parancsot választva erősítse meg kiválasztásait.

## <a name="api-usage-tab"></a>API-használat lap

A lapon részletes információk találhatók a valós idejű API-használatáról, és látható, hogy egy adott időtartományban milyen események történtek. További információ: [Valós idejű adatbetöltés](real-time-data-ingestion.md).
