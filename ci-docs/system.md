---
title: Rendszerkonfiguráció megtekintése
description: Ismerkedjen meg a rendszerbeállításokkal a Dynamics 365 Customer Insights alkalmazásban.
ms.date: 08/09/2022
ms.subservice: audience-insights
ms.topic: conceptual
author: NimrodMagen
ms.author: nimagen
ms.reviewer: mhart
manager: shellyha
searchScope:
- ci-system-status
- ci-system-about
- ci-system-general
- ci-system-api-usage
- customerInsights
ms.openlocfilehash: 2498814a3d2e6330124fb97c036b9b310bcf1f7a
ms.sourcegitcommit: 49394c7216db1ec7b754db6014b651177e82ae5b
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/10/2022
ms.locfileid: "9246250"
---
# <a name="view-system-configuration"></a>Rendszerkonfiguráció megtekintése

Megtekintheti a rendszerinformációkat, a rendszer állapotát és az API-használatot.

## <a name="view-api-usage"></a>API-használat megtekintése

Megtekintheti a valós idejű API-használat részleteit, és megtekintheti, hogy mely események történtek egy adott időkeret.

1. Lépjen a Felügyeleti **rendszer elemre** > **,** és válassza az **API-használat** lapot.

1. **Válassza ki a megtekinteni kívánt időkeret**.

   Az **API-használat** lap három részből áll:

   - **API-hívások** – olyan diagram, amely a kiválasztott időkeretben megjeleníti az API-hívásokat.
   - **Adatátvitel** – olyan diagram, amely az API-n keresztül továbbított adatok mennyiségét mutatja a kiválasztott időkeretben.
   - **Műveletek** – egy táblázat sorokkal minden elérhető API-művelethez, és részletek a műveletek használatáról. Válasszon ki egy műveletnevet az API-referenciához [való ugráshoz](https://developer.ci.ai.dynamics.com/api-details#api=CustomerInsights&operation=Get-all-instances).

   A valós idejű adatbetöltést [használó](real-time-data-ingestion.md) műveletek távcsőszimbólumot tartalmaznak a valós idejű API-használat megtekintéséhez.

   1. Válassza ki a távcsövet a **művelet használati adatait tartalmazó Valós idejű API-használat** panel megnyitásához.
   1. **Válassza ki a megtekinteni kívánt időkeret**.
   1. A Csoportosítási **szempont** mezőben kiválaszthatja, hogyan szeretné a legjobban bemutatni a valós idejű interakciókat. Csoportosítsa az adatokat API-módszer, entitás minősített neve **(betöltött entitás),** létrehozva **(az esemény forrása),** eredmény **(sikeres vagy sikertelen) vagy** hibakódok **szerint.** **·** Az adatok előzménydiagramként és táblaként érhetők el.

## <a name="view-system-information"></a>Rendszerinformációk megtekintése

Tekintse meg a környezeti megjelenítendő név, azonosítóját, régióját, típusát és munkamenet-azonosítóját.

1. Lépjen a Felügyeleti **rendszer elemre** > **,** és válassza a **Névjegy** lapot.

1. A nyelv és az ország/régió megtekintéséhez válassza az **Általános** lapot.

### <a name="update-preferred-language-or-countryregion"></a>Az előnyben részesített nyelv vagy ország/régió frissítése

A Customer Insights [számos nyelvet](/dynamics365/get-started/availability) támogat. Az alkalmazás felhasználja nyelvpreferenciát, hogy egyes elemeket, mint például a menü, a címszövegek és a rendszerüzenetek, a preferált nyelven jelenítsen meg.

A rendszer nem fordítja le a manuálisan bevitt és az importált adatokat.

1. Lépjen a Felügyeleti **rendszer elemre** > **,** és válassza az **Általános** lapot.

1. Az előnyben részesített nyelv megváltoztatásához válasszon egy **nyelvet** a legördülő listából.

1. Ha módosítani szeretné a dátumok, időpontok és számok preferált formázását, használja az **ország/régiók formátuma** a legördülő listában. Megjelenik egy formázási előnézet. A rendszer automatikusan javasolja a kiválasztást, amikor új nyelvet választ.

1. Válassza a **Mentés** parancsot.

## <a name="view-system-status"></a>A rendszer állapotának megtekintése

Nyomon követheti a tevékenységek, az adatbetöltés, az adatexportálás és számos más fontos termékfolyamat előrehaladását. Tekintse át az információkat, hogy megbizonyosodjon az aktív feladatok és folyamatok teljességéről.

1. Lépjen a Felügyeleti **rendszer elemre** > **,** és válassza az **Állapot** lapot.

   A különböző folyamatok állapot- és feldolgozási információi megjelennek. Tekintse meg a **feladat nevét**, a **legutóbbi futtatás állapotát** és azt, hogy mikor lett **utoljára frissítve**.

1. Az utolsó néhány futtatás részleteinek megtekintéséhez válassza ki a feladat vagy folyamat nevét.

1. Egy tevékenység előrehaladási részleteinek megtekintéséhez válassza ki az állapotot. Megjelenik a **Folyamat részletei** panel.

   :::image type="content" source="media/system-progress-details.png" alt-text="A rendszer előrehaladásának részletei panel":::

1. Az összes tevékenység előrehaladási részleteinek megtekintéséhez válassza a Teljes munkafolyamat **lehetőséget**.

### <a name="status-definitions"></a>Állapotdefiníciók

A rendszer a következő állapotokat használja a feladatokhoz és folyamatokhoz:

|Állam  |Definíció  |
|---------|---------|
|Megszakított |A feladatot vagy folyamatot a felhasználó megszakította, mielőtt az befejeződött volna.   |
|Sikertelen   |A feladat vagy folyamat hibákba ütközött.         |
|Nem sikerült  |A feladat vagy folyamat sikertelen volt.  |
|Nem kezdődött el   |Adatforrás még nincs betöltött adat, vagy a feladat még vázlat módban van.         |
|Feldolgozás folyamatban  |A tevékenység vagy folyamat folyamatban van.  |
|Frissítés    |A tevékenység vagy folyamat folyamatban van. A művelet megszakításához válassza a Frissítés és **a Feladat megszakítása lehetőséget.** **·** Egy tevékenység vagy folyamat frissítésének leállítása visszaállítja azt az utolsó frissítési állapotába.       |
|Kihagyva  |A feladat vagy folyamat kimaradt. Egy vagy több olyan alsóbb szintű folyamat kimaradt vagy hibás volt, amelytől ez a feladat függ.|
|Sikerült  |A feladat vagy folyamat sikeresen befejeződött. Adatforrások esetén azt jelzi, hogy az adatok betöltése sikeresen megtörtént, ha a Frissített **oszlopban** szerepel egy időpont.|
|Feldolgozási sorban | A feldolgozás várólistára kerül, és az összes felsőbb rétegbeli feladat és folyamat befejezése után indul el. További információ: [Folyamatok](#refresh-processes) frissítése.|

### <a name="refresh-processes"></a>Folyamatok frissítése

A feladatok és folyamatok frissítése a [konfigurált ütemezésnek](schedule-refresh.md) megfelelően fut.

|Folyamat  |Description  |
|---------|---------|
|Tevékenys.  |Manuálisan fut (egyszeri frissítés). Az egyesítési folyamattól függ. Az Insights a feldolgozástól függ.|
|Elemzés összekapcsolása |Manuálisan fut (egyszeri frissítés). A szegmensektől függ.  |
|Elemzés előkészítése |Manuálisan fut (egyszeri frissítés). A szegmensektől függ.  |
|Adatok előkészítése   |Szüksége van egy entitásra, amelyen futni kell. Adatforrás entitások a be- és A bővített entitások a gazdagodástól függenek. Az Ügyfél entitás az egyesítéstől függ.  |
|Adatforrások   |Nem függ más folyamattól. A egyeztetés a folyamat sikeres befejezésétől függ.  |
|Bővítések   |Manuálisan fut (egyszeri frissítés). Az egyesítési folyamattól függ. |
|Rendeltetési helyek exportálása |Manuálisan fut (egyszeri frissítés). A szegmensektől függ.  |
|Elemzések |Manuálisan fut (egyszeri frissítés). A szegmensektől függ.  |
|Intelligencia   |Az egyesítéstől függ.   |
|Match |Az egyeztetés definíciójában használt adatforrások feldolgozásából függ.      |
|Mértékek  |Manuálisan fut (egyszeri frissítés). Az egyesítési folyamattól függ.  |
|Összefűzés   |Az egyeztetési folyamat befejezésétől függ. A szegmensek, a mértékek, a bővítés, a keresés, a tevékenységek, az előrejelzések és az adatok előkészítése a folyamat sikeres befejezésének függvénye.   |
|Profilok   |Manuálisan fut (egyszeri frissítés). Az egyesítési folyamattól függ. |
|Keresés   |Manuálisan fut (egyszeri frissítés). Az egyesítési folyamattól függ. |
|Szegmensek  |Manuálisan fut (egyszeri frissítés). Az egyesítési folyamattól függ. Az Insights a feldolgozástól függ.|
|Rendszer   |Az egyeztetési folyamat befejezésétől függ. A szegmensek, a mértékek, a bővítés, a keresés, a tevékenységek, az előrejelzések és az adatok előkészítése a folyamat sikeres befejezésének függvénye.   |
|User  |Manuálisan fut (egyszeri frissítés). Az entitásoktól függ.  |

Válassza ki egy folyamat állapotát a teljes feladat előrehaladási részleteinek megtekintéséhez. A fenti frissítési folyamatok segíthetnek megérteni, hogy mit tehet egy **kihagyott vagy** várólistán lévő **feladat** vagy folyamat kezelése érdekében.


[!INCLUDE [footer-include](includes/footer-banner.md)]
