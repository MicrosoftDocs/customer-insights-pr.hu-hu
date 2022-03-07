---
title: Mértékek létrehozása sablonokból
description: A gyakori használati esetek sablonjaival mér mérdesedik meg.
ms.date: 02/28/2022
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: wameng
ms.reviewer: mhart
manager: shellyha
searchScope:
- ci-measure-template
- customerInsights
ms.openlocfilehash: 0fe846691825b93732cbbe6d1c942a79e4a3934f
ms.sourcegitcommit: cf6a0ed44915908a44c70889a2dd199a9d0d4798
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/28/2022
ms.locfileid: "8359966"
---
# <a name="use-a-template-to-build-a-measure"></a>Sablon használata mértékek építéséhez

Ezek létrehozásához a gyakran használt [mértékek](measures.md) előre definiált sablonjait használhatja. A sablonok részletes leírása és az interaktív élmény segít a hatékony mérték létrehozásában. A sablonok az *Egyesített tevékenység* entitásból származó leképezett adatokra épülnek. Ezért mindenképpen konfiguráljon [ügyféltevékenységeket](activities.md), mielőtt sablonból hoz létre mértéket.

Egyéni mértékeket szeretne létrehozni, olvassa el a Mértékszerkesztő használata a semmiből történő intézkedések létrehozásához című [témakört](measure-builder.md).

# <a name="individual-consumers-b-to-c"></a>[Egyéni fogyasztók (B-to-C)](#tab/b2c)

Elérhető mértéksablonok: 
- Tranzakció átlagos értéke (ATV)
- Tranzakció összértéke
- Átlagos napi bevétel
- Átlagos éves bevétel
- Tranzakció száma
- Szerzett hűségpontok
- Beváltott hűségpontok
- Hűségpontok egyenlege
- Ügyfél aktív életciklusa
- Hűség tagságának időtartama
- Az utolsó vásárlás óta eltelt idő

## <a name="build-a-new-measure-using-a-template"></a>Új mérték létrehozása sablon használatával

1. Menjen az **Intézkedésekhez**.

1. Válassza az **Új**, és a **Sablon kiválasztása** lehetőséget.

   :::image type="content" source="media/measure-use-template.png" alt-text="Képernyőkép a legördülő menüről, amikor új mérőintézkedést hoz létre, kiemelve a sablont.":::

1. Keresse meg az igényeinek megfelelő sablont, és válassza a **Sablon kiválasztása** lehetőséget.

1. Tekintse át a kötelező adatokat, és válassza az **Első lépések** lehetőséget, ha minden adat a megfelelő helyen van.

1. A **Név szerkesztése** ablaktáblában állítsa be a mérték és a kimeneti entitás nevét. 

1. Válassza a **Kész** lehetőséget.

1. Adja meg az adat használandó időkeretét az **Időszak beállítása** szakaszban. Válassza ki, hogy az új mérés lefedi-e a teljes adathalmazt az **Összes idő** kiválasztásával, vagy ha azt szeretné, hogy a mérés egy **Adott időszakra** összpontosítson.

   :::image type="content" source="media/measure-set-time-period.png" alt-text="Képernyőkép, amely egy sablonból származó mérték konfiguálásakor mutatja az időszak szakaszt.":::

1. A következő szakaszban válassza az **Adatok hozzáadása** lehetőséget a tevékenységek kiválasztásához, és az *Egyesített tevékenység* entitásból képezze le a megfelelő adatokat.

    1. A 1/2. lépés: A **Tevékenység típusa** alatt válassza ki a használni kívánt entitás típusát. A **Tevékenységekhez** válassza ki a leképezni kívánt entitásokat.
    1. 2/2. lépés: Válassza ki az attribútumot az *Egyesített tevékenység* entitásból a képlet által megkövetelt összetevőhöz. Például az Átlagos tranzakció értéke a Tranzakció értéket képviselő attribútum. A **Tevékenység időbélyegző** esetén válassza ki az Egyesített tevékenység entitás attribútumát, amely a tevékenység dátumát és időpontját jelképezi.
   
1. Miután az adatleképezés sikeres volt, az állapot **Befejezett** értékre vált, valamint láthatja a leképezett tevékenységek és attribútumok nevét.

1. Most már a **Futtatás** lehetőséget is választhatja a mérték eredményének kiszámításához. Későbbi finomításhoz válassza a **Tervezet mentése** lehetőséget.

# <a name="business-accounts-b-to-b"></a>[Üzleti számlák (B-to-B)](#tab/b2b)

Ez a funkció csak az olyan környezetekben létrehozott mértékekhez érhetők el, ahol az egyéni ügyfelek elsődleges célként célközönség.

---
