---
title: Rendszerkonfiguráció a célközönség információk funkcióban
description: További információ a rendszerbeállításokról Dynamics 365 Customer Insights célközönség elemzési képességben.
ms.date: 11/01/2021
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: NimrodMagen
ms.author: nimagen
ms.reviewer: mhart
manager: shellyha
ms.openlocfilehash: 1b790106f8b9617d0c1f244e1d15a74c7ef9a82b
ms.sourcegitcommit: 834651b933b1e50e7557d44f926a3fb757c1f83a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/02/2021
ms.locfileid: "7732364"
---
# <a name="system-configuration"></a>Rendszerkonfiguráció

A rendszerkonfigurációk célközönség elemzési adatok eléréséhez a bal oldali navigációs sávon válassza a Rendszergazdai rendszer lehetőséget **·** > **a** rendszerfeladatok és folyamatok listájának megtekintéséhez.

A **Rendszer** lap a következő füleket tartalmazza:
- [Állam](#status-tab)
- [Ütemezés](#schedule-tab)
- [API-használat](#api-usage-tab)
- [Névjegy](#about-tab)
- [Általános](#general-tab)
- [Biztonsági](#security-tab)

:::image type="content" source="media/system-tabs.png" alt-text="A Beállítások lap a rendszeroldalon.":::

## <a name="status-tab"></a>Állapot lap

Az **Állapot lapon nyomon követheti a** tevékenységek, az adatbetöltés, az adatexport és számos más fontos termékfolyamat előrehaladását. Tekintse át a lapon található információkat az aktív feladatok és folyamatok teljességének biztosítása érdekében.

Ez a lap a különböző folyamatok állapot- és feldolgozási adatainak tábláit tartalmazza. Minden tábla nyomon követi a feladat **Nevét**, valamint a hozzá tartozó entitást, a legutóbbi futtatás **Állapotát**, illetve azt, mikor történt a **Legutóbbi frissítés**. Az utolsó több futtatás részleteit a tevékenység vagy a folyamat nevének kiválasztásával tekintheti meg. 

Válassza ki a tevékenység vagy folyamat melletti állapotot az **Állapot** oszlopban a **Haladás részletei ablaktábla megnyitásához.**

   :::image type="content" source="media/system-progress-details.png" alt-text="A rendszer előrehaladásának részletei ablaktábla":::

### <a name="status-definitions"></a>Állapotdefiníciók

A rendszer a következő állapotokat használja a feladatokhoz és folyamatokhoz:

|Állam  |Definíció  |
|---------|---------|
|Visszavonva |A feldolgozást a felhasználó megszakította, mielőtt befejeződött volna.   |
|Sikertelen   |Az adatbetöltés hibákba ütközött.         |
|Nem sikerült  |A feldolgozás sikertelen volt.  |
|Nincs elindítva   |Az adatforrás még nem tartalmaz adatokat vagy még vázlat módban van.         |
|Feldolgozás folyamatban  |A tevékenység vagy a folyamat folyamatban van.  |
|Frissítés    |Az adatbetöltés folyamatban van. A művelet a **Műveletek** oszlop **Frissítés leállítása** parancsával vonható vissza. A adatforrás frissítésének leállítása visszaállítja azt az utolsó frissítéskori állapotára.       |
|Kihagyva  |A feladat vagy a folyamat kimaradt. Egy vagy több olyan alsóbb szintű folyamat kimaradt vagy hibás volt, amelytől ez a feladat függ.|
|Sikerült  |A tevékenység vagy folyamat sikeresen befejeződött. Adatforrások esetén azt jelzi, hogy az adatok sikeresen betöltése megtörtént, ha a Frissített oszlopban időt **·** említenek.|
|Feldolgozási sorban | A feldolgozás várólistára kerül, és az összes upstream feladat és folyamat befejezése után kezdődik. További információ: [Folyamatok frissítése](#refresh-processes).|

### <a name="refresh-processes"></a>Folyamatok frissítése

A feladatok és folyamatok frissítése a konfigurált ütemezés szerint [...](#schedule-tab) fut. 

|Folyamat  |Ismertetés  |
|---------|---------|
|Tevékenység  |Manuálisan fut (egyszeri frissítés). Az egyesítési folyamattól függ. Az Insights a feldolgozástól függ.|
|Elemzés összekapcsolása |Manuálisan fut (egyszeri frissítés). A szegmensektől függ.  |
|Elemzés előkészítése |Manuálisan fut (egyszeri frissítés). A szegmensektől függ.  |
|Adatok előkészítése   |Az egyesüléstől függ.   |
|Adatforrások   |Nem függ más folyamattól. A egyeztetés a folyamat sikeres befejezésétől függ.  |
|Bővítések   |Manuálisan fut (egyszeri frissítés). Az egyesítési folyamattól függ. |
|Exportcélpontok |Manuálisan fut (egyszeri frissítés). A szegmensektől függ.  |
|Elemzések |Manuálisan fut (egyszeri frissítés). A szegmensektől függ.  |
|Információk   |Az egyesüléstől függ.   |
|Egyeztetés |Az egyeztetés definíciójában használt adatforrások feldolgozásából függ.      |
|Mérőszámok  |Manuálisan fut (egyszeri frissítés). Az egyesítési folyamattól függ.  |
|Összefűzés   |Az egyeztetési folyamat befejezésétől függ. A szegmensek, a mértékek, a bővítés, a keresés, a tevékenységek, az előrejelzések és az adatok előkészítése a folyamat sikeres befejezésének függvénye.   |
|Profilok   |Manuálisan fut (egyszeri frissítés). Az egyesítési folyamattól függ. |
|Keresés   |Manuálisan fut (egyszeri frissítés). Az egyesítési folyamattól függ. |
|Szegmensek  |Manuálisan fut (egyszeri frissítés). Az egyesítési folyamattól függ. Az Insights a feldolgozástól függ.|
|Rendszer   |Az egyeztetési folyamat befejezésétől függ. A szegmensek, a mértékek, a bővítés, a keresés, a tevékenységek, az előrejelzések és az adatok előkészítése a folyamat sikeres befejezésének függvénye.   |
|Felhasználó  |Manuálisan fut (egyszeri frissítés). Az entitásoktól függ.  |

Válassza ki egy folyamat állapotát a teljes feladat előrehaladási részleteinek megtekintéséhez. A fenti frissítési folyamatok segíthetnek megérteni, hogy mit tehet egy **kihagyott vagy várólistára helyezett feladat vagy folyamat kezelése** **·** érdekében.

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

   A valós idejű adatbetöltést használó műveletek [...](real-time-data-ingestion.md) tartalmaznak egy távcső szimbólummal ellátott gombot a valós idejű API-használat megtekintéséhez. A gomra kattintva megnyithat egy oldalpanelt, ami megmutatja a valós idejű API-használati adatokat a jelenlegi környezetben.   
   A **Valós idejű API-használati** ablakban a **Csoportosítás** mező segítségével választhatja ki, hogyan tudja a legjobban bemutatni a valós idejű interakciókat. Az adatok API-metódus, az entitás minősített neve (betöltött entitás), a létrehozó (az esemény forrása), az eredmény (siker vagy hiba) vagy a hibakódok alapján csoportosíthatók. Az adatok előzménydiagramként és táblaként érhetők el.

## <a name="security-tab"></a>Biztonság lap

A **Biztonság** lapon kezelheti a saját [Azure Key Vault kulcstartót](/azure/key-vault/general/basic-concepts), és összekapcsolhatja a környezettel.
A dedikált kulcstartó a szervezet megfelelési határán belül a fázisok és a titkok használatára használható. Célközönséggel kapcsolatos információk az Azure Key Vaultban tárolt titkokat a külső rendszerekhez való [kapcsolatok beállítására](connections.md) használhatja.

További információkért lásd: [Hozza magával saját Azure-kulcstartóját](use-azure-key-vault.md).


[!INCLUDE[footer-include](../includes/footer-banner.md)]
