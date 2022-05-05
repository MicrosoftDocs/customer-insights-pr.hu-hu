---
title: Rendszerkonfiguráció a Customer Insights alkalmazásban
description: Ismerkedjen meg a rendszerbeállításokkal a Dynamics 365 Customer Insights alkalmazásban.
ms.date: 04/21/2022
ms.subservice: audience-insights
ms.topic: conceptual
author: NimrodMagen
ms.author: nimagen
ms.reviewer: mhart
manager: shellyha
searchScope:
- ci-system-status
- ci-system-schedule
- ci-system-about
- ci-system-general
- ci-system-api-usage
- customerInsights
ms.openlocfilehash: 3aa4c6529d705698e612adad86587e3c3a4db35b
ms.sourcegitcommit: cf74b8c20d88eb96e1ac86e18cd44fe27aad5ab9
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/28/2022
ms.locfileid: "8653619"
---
# <a name="system-configuration"></a>Rendszerkonfiguráció

A rendszerkonfigurációk eléréséhez nyissa meg az **AdminSystem** > **webhelyet** a rendszerfeladatok és -folyamatok listájának megtekintéséhez.

A **Rendszer** lap a következő füleket tartalmazza:
- [Állam](#status-tab)
- [Ütemezés](#schedule-tab)
- [API-használat](#api-usage-tab)
- [Névjegy](#about-tab)
- [Általános](#general-tab)

:::image type="content" source="media/system-tabs.png" alt-text="A Beállítások lap a rendszeroldalon.":::

## <a name="status-tab"></a>Állapot lap

Az **Állapot lapon** nyomon követheti a feladatok előrehaladását, az adatbetöltést, az adatexportot és számos más fontos termékfolyamatot. Tekintse át az ezen a lapon található információkat az aktív feladatok és folyamatok teljességének biztosítása érdekében.

Ez a lap a különböző folyamatok állapot- és feldolgozási adatainak tábláit tartalmazza. Minden tábla nyomon követi a feladat **Nevét**, valamint a hozzá tartozó entitást, a legutóbbi futtatás **Állapotát**, illetve azt, mikor történt a **Legutóbbi frissítés**. Az utolsó néhány futtatás részleteit a tevékenység vagy folyamat nevének kiválasztásával tekintheti meg. 

Válassza ki a tevékenység vagy folyamat melletti állapotot az **Állapot** oszlopban a **Folyamat részletei** ablaktábla megnyitásához.

   :::image type="content" source="media/system-progress-details.png" alt-text="Rendszer előrehaladásának részletei ablaktábla":::

### <a name="status-definitions"></a>Állapotdefiníciók

A rendszer a következő állapotokat használja a feladatokhoz és folyamatokhoz:

|Állam  |Definíció  |
|---------|---------|
|Megszakított |A feldolgozást a felhasználó megszakította, mielőtt befejeződött volna.   |
|Sikertelen   |Az adatbetöltés hibákba ütközött.         |
|Nem sikerült  |A feldolgozás nem sikerült.  |
|Nem kezdődött el   |Az adatforrás még nem tartalmaz adatokat vagy még vázlat módban van.         |
|Feldolgozás folyamatban  |A feladat vagy folyamat folyamatban van.  |
|Frissítés    |Az adatbetöltés folyamatban van. A művelet a **Műveletek** oszlop **Frissítés leállítása** parancsával vonható vissza. A adatforrás frissítésének leállítása visszaállítja azt az utolsó frissítéskori állapotára.       |
|Kihagyva  |A feladat vagy folyamat kimaradt. Egy vagy több olyan alsóbb szintű folyamat kimaradt vagy hibás volt, amelytől ez a feladat függ.|
|Sikerült  |A feladat vagy folyamat sikeresen befejeződött. Adatforrások esetén azt jelzi, hogy az adatok sikeresen be lettek nyelni, ha a **Frissített** oszlopban szerepel egy idő.|
|Feldolgozási sorban | A feldolgozás várólistára kerül, és az összes upstream feladat és folyamat befejezése után elindul. További információt a Folyamatok [frissítése című témakörben talál](#refresh-processes).|

### <a name="refresh-processes"></a>Folyamatok frissítése

A feladatok és folyamatok frissítése a [konfigurált ütemezés](#schedule-tab) szerint történik. 

|Folyamat  |Description  |
|---------|---------|
|Tevékenys.  |Manuálisan fut (egyszeri frissítés). Az egyesítési folyamattól függ. Az Insights a feldolgozástól függ.|
|Elemzés összekapcsolása |Manuálisan fut (egyszeri frissítés). Szegmensektől függ.  |
|Elemzés előkészítése |Manuálisan fut (egyszeri frissítés). Szegmensektől függ.  |
|Adatok előkészítése   |Szüksége van egy entitásra, hogy fusson. Adatforrás entitások a betöltéstől függenek. A gazdagodó entitások a gazdagodástól függenek. A Vevő entitás az egyesítéstől függ.  |
|Adatforrások   |Nem függ más folyamattól. A egyeztetés a folyamat sikeres befejezésétől függ.  |
|Bővítések   |Manuálisan fut (egyszeri frissítés). Az egyesítési folyamattól függ. |
|Exportcélok |Manuálisan fut (egyszeri frissítés). Szegmensektől függ.  |
|Elemzések |Manuálisan fut (egyszeri frissítés). Szegmensektől függ.  |
|Intelligencia   |Az egyesítéstől függ.   |
|Match |Az egyeztetés definíciójában használt adatforrások feldolgozásából függ.      |
|Mértékek  |Manuálisan fut (egyszeri frissítés). Az egyesítési folyamattól függ.  |
|Összefűzés   |Az egyeztetési folyamat befejezésétől függ. A szegmensek, a mértékek, a bővítés, a keresés, a tevékenységek, az előrejelzések és az adatok előkészítése a folyamat sikeres befejezésének függvénye.   |
|Profilok   |Manuálisan fut (egyszeri frissítés). Az egyesítési folyamattól függ. |
|Keresés   |Manuálisan fut (egyszeri frissítés). Az egyesítési folyamattól függ. |
|Szegmensek  |Manuálisan fut (egyszeri frissítés). Az egyesítési folyamattól függ. Az Insights a feldolgozástól függ.|
|Rendszer   |Az egyeztetési folyamat befejezésétől függ. A szegmensek, a mértékek, a bővítés, a keresés, a tevékenységek, az előrejelzések és az adatok előkészítése a folyamat sikeres befejezésének függvénye.   |
|User  |Manuálisan fut (egyszeri frissítés). Az entitásoktól függ.  |

Válassza ki egy folyamat állapotát, hogy megtekinthesse a teljes feladat előrehaladási részleteit. A fenti frissítési folyamatok segíthetnek megérteni, hogy mit tehet egy **kihagyott** vagy várólistára helyezett **feladat vagy** folyamat kezelése érdekében.

## <a name="schedule-tab"></a>Ütemezés lap

Használja az **Ütemezés** lapot, hogy ütemezze az automatikus frissítéseket minden egyes [betáplált adatforrásához](data-sources.md). Az automatikus frissítéssel biztosítható, hogy az adatforrásokból származó frissítések megjelenjenek az egyesített ügyfélprofilokban.

> [!NOTE]
> Az Ön által kezelt adatforrások saját ütemezésük szerint frissülnek. Az Ön által kezelt adatforrások frissítésének ütemezéséhez konfigurálja a frissítési beállításokat az adott adatforrás az **Adatforrások** lapon.
> :::image type="content" source="media/PPDF-edit-refresh.png" alt-text="Power Platform Adatfolyam frissítési beállításai.":::

1. Nyissa meg az **AdminSystem** > **elemet,** és válassza az **Ütemezés** lapot.

2. Az ütemezett frissítés alapértelmezett állapota **Ki**. Az ütemezett frissítések engedélyezéséhez módosítsa a képernyő felső részén látható váltógombot **Be** állásra.

3. Választhat **Heti** (alapértelmezett) és **Napi** frissítések között. Ha heti frissítéseket szeretne ütemezni, jelöljön ki egy vagy több napot, amikor a frissítést futtatni szeretné.

4. Állítsa be az **Időzónát**, majd az **Idő** legördülő listában állítsa be a frissítés időpontját. Ha kész, válassza a **Beállítás** lehetőséget. Ha egy nap alatt több frissítést szeretne ütemezni, válassza a **Másik időpont hozzáadása**.

5. Válassza a **Mentés** lehetőséget a módosítások alkalmazásához.

## <a name="about-tab"></a>Névjegy lap

A **Névjegy** lapon a szervezet **megjelenítendő neve**, az aktív **környezeti azonosító**, a **régió** és a **munkamenet azonosítója** szerepel. Ha egynél több munkakörnyezet van, érdemes mindegyiknek adnia egy könnyen azonosítható megjelenítendő nevet.

## <a name="general-tab"></a>Általános lap

Az **Általános** lapon módosíthatja a nyelvet és az országot/régiót.

A Customer Insights [számos nyelvet](/dynamics365/get-started/availability) támogat. Az alkalmazás felhasználja nyelvpreferenciát, hogy egyes elemeket, mint például a menü, a címszövegek és a rendszerüzenetek, a preferált nyelven jelenítsen meg.

A rendszer nem fordítja le a manuálisan bevitt és az importált adatokat.

### <a name="update-the-settings"></a>Beállítások frissítése

Az előnyben részesített nyelv megváltoztatásához válasszon egy **nyelvet** a legördülő listából.

Ha módosítani szeretné a dátumok, időpontok és számok preferált formázását, használja az **ország/régiók formátuma** a legördülő listában. Ebben a mezőben egy formázási előnézet jelenik meg. A rendszer automatikusan ajánlani fog egy választási lehetőséget, amikor új nyelvet választ ki.

A **Mentés** parancsot választva erősítse meg kiválasztásait.

## <a name="api-usage-tab"></a>API-használat lap

További információ a valós idejű API-használatról, és annak megtekintése, hogy mely események történtek egy adott időkeretben. Válassza ki az időkeretet a **Válasszon időkeretet** legördülő menüben. 

Az **API-használat** három szakaszból áll: 
- **API-hívások** – olyan diagram, amely a kiválasztott időkeretben megjeleníti az API-hívásokat.

- **Adatátvitel** – olyan diagram, amely az API-n keresztül továbbított adatok mennyiségét mutatja a kiválasztott időkeretben.

-  **Műveletek** – egy táblázat sorokkal minden elérhető API-művelethez, és részletek a műveletek használatáról. Az [API-hivatkozáshoz](https://developer.ci.ai.dynamics.com/api-details#api=CustomerInsights&operation=Get-all-instances) válassza ki egy művelet nevét.

   A valós idejű adatbetöltést [használó](real-time-data-ingestion.md) műveletek egy távcsőszimbólumot tartalmazó gombot tartalmaznak a valós idejű API-használat megtekintéséhez. A gomra kattintva megnyithat egy oldalpanelt, ami megmutatja a valós idejű API-használati adatokat a jelenlegi környezetben.   
   A **Valós idejű API-használati** ablakban a **Csoportosítás** mező segítségével választhatja ki, hogyan tudja a legjobban bemutatni a valós idejű interakciókat. Az adatok API-metódus, az entitás minősített neve (betöltött entitás), a létrehozó (az esemény forrása), az eredmény (siker vagy hiba) vagy a hibakódok alapján csoportosíthatók. Az adatok előzménydiagramként és táblaként érhetők el.


[!INCLUDE [footer-include](includes/footer-banner.md)]
