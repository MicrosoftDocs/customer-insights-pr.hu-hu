---
title: Megosztott feladatok előrejelzés forgatókönyvekhez
description: Ismerje meg az előrejelzések kezelését, hibaelhárítását és finomítását.
ms.date: 05/17/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: diegogranados117
ms.author: digranad
manager: shellyha
ms.openlocfilehash: dccb8dcca8f65f64973e46fed9d83034d58282e2
ms.sourcegitcommit: bcc47d15d4f0eacf008e4dbc09baac7f062b3ca8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/29/2021
ms.locfileid: "6315881"
---
# <a name="manage-predictions"></a>Előrejelzések kezelése

Ez a cikk néhány olyan feladatot tárgyal, amelyeken a legtöbb előrejelzési forgatókönyv osztozik.

## <a name="troubleshoot-a-failed-prediction"></a>A sikertelen előrejelzés hibáinak elhárítása.

1. Nyissa meg az **Intelligencia** > **Előrejelzések** menüt, és válassza ki a **Saját előrejelzések** lapot.

1. Válassza ki a függőleges ellipsziseket amellett az előrejelzés mellet, melynek hibanaplóját meg szeretné tekinteni.

1. Válassza ki a **Naplók** menüpontot.

1. Tekintse át a hibákat. Többféle típusú hiba fordulhat elő; a leírásból kiderül, milyen feltétel okozta a hibát. Ha például az a hiba, hogy nincs elég adat a pontos előrejelzéshez, akkor ez általában megoldható további adatok Customer Insightsba történő betöltésével.

## <a name="input-data-usability-report"></a>Bemeneti adatok használhatósági jelentése

A bemeneti adatok használhatósági jelentése egységes képet ad azokról a hibákról és figyelmeztetésekről, amelyeket a gyári előrejelzések generálhatnak. Ajánlásokat is ad a modell teljesítményének javítására.

A jelentés a modell betanítási folyamatának befejezése után érhető el. Minden modellhez külön-külön van létrehozva, függetlenül attól, hogy sikeresen befejeződött-e vagy sem.

### <a name="view-the-input-data-usability-report"></a>Bemeneti adatok használhatósági jelentésének megtekintése

Miután egy beépített modell befejezte a betanítási lépést, tekintse meg a jelentést:
- Jelölje ki a modell neve melletti három pontot, és válassza a **Bemeneti adatok használhatósági jelentése** lehetőséget.
- Válassza ki a modell állapotát, válassza a **Bemeneti adatok használhatósági jelentése** elemet az oldalsó ablaktáblában.
- Válasszon ki egyet a lista egyik modellje közül, és válassza a **Bemeneti adatok használhatósági jelentését** a parancssoron.
- Nyissa meg a modelleredmények oldalt, és válassza a **Bemeneti adatok használhatósági jelentését** a parancssoron.

### <a name="information-in-the-input-data-usability-report"></a>Információk a bemeneti adatok használhatósági jelentésében

A jelentés következő oszlopai hasznos információkat tartalmaznak a modell adatainak javításához.

:::image type="content" source="media/input-data-usability-report.png" alt-text="Példa egy bemeneti adatok használhatósági jelentésére, amely egy hibákat, figyelmeztetéseket és ajánlásokat megjelenítő táblázatot mutat be.":::

- Név: A hiba, figyelmeztetés vagy ajánlás leíró neve.
- Lépés: Modellfázis, tanítás vagy pontszám, amelyre az információ hivatkozik.
- Állapot: Az információ súlyossága (hiba, figyelmeztetés, ajánlás).
- Oszlopnév: Oszlop egy entitásban, amelyet módosítani kell a modell teljesítményének javítása érdekében.
- Entitásnév: Az entitás neve, amelyet módosítani kell a modell teljesítményének javítása érdekében.
- Részletek: Részletek a hibáról, figyelmeztetésről vagy ajánlásról.

## <a name="refresh-a-prediction"></a>Előrejelzés frissítése

Az előrejelzések automatikusan frissülnek az [adatok beállítások között megadott frissítési ütemezése](system.md#schedule-tab) szerint. Ezeket Ön manuálisan is frissíteni tudja.

1. Nyissa meg az **Intelligencia** > **Előrejelzések** menüt, és válassza ki a **Saját előrejelzések** lapot.

1. Kattintson a frissíteni kívánt előrejelzés mellett lévő pontokra.

1. Válassza a **Frissítés** lehetőséget.

## <a name="delete-a-prediction"></a>Előrejelzés törlése

Az előrejelzés törlésével annak kimeneti entitása is törlésre kerül.

1. Nyissa meg az **Intelligencia** > **Előrejelzések** menüt, és válassza ki a **Saját előrejelzések** lapot.

1. Kattintson a törölni kívánt előrejelzés mellett lévő pontokra.

1. Válassza a **Törlés** lehetőséget.
