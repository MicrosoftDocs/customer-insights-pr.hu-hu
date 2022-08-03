---
title: Mértékek létrehozása sablonokból
description: Mértékeket definiálhat sablonok használatával a gyakori használati esetekhez.
ms.date: 03/25/2022
ms.subservice: audience-insights
ms.topic: conceptual
author: v-wendysmith
ms.author: wameng
ms.reviewer: v-wendysmith
manager: shellyha
searchScope:
- ci-measure-template
- customerInsights
ms.openlocfilehash: 6dc7fce78d10ba91de4b2abf54c6c6ab1c919d3a
ms.sourcegitcommit: 8a28e9458b857adf8e90e25e43b9bc422ebbb2cd
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/18/2022
ms.locfileid: "9170776"
---
# <a name="create-measures-from-templates"></a>Mértékek létrehozása sablonokból

A létrehozásukhoz használja az általánosan használt [mértékek](measures.md) előre definiált sablonjait. A sablonok az *Egyesített tevékenység* entitásból származó leképezett adatokra épülnek. Ezért mindenképpen konfiguráljon [ügyféltevékenységeket](activities.md), mielőtt sablonból hoz létre mértéket.

A mértéksablonok csak az egyes ügyfelek számára készült **környezetekben támogatottak**. Ha egyéni mértékeket szeretne létrehozni, vagy mértékeket szeretne létrehozni a B-től B-ig, tekintse meg a Mértékkészítő használatacímű [témakört](measure-builder.md).

Elérhető mértéksablonok:
- Tranzakció átlagos értéke (ATV)
- Tranzakció összértéke
- Átlagos napi bevétel
- Havi átlagos bevétel
- Átlagos éves bevétel
- Tranzakció száma
- Szerzett hűségpontok
- Beváltott hűségpontok
- Hűségpontok egyenlege
- Ügyfél aktív életciklusa
- Hűség tagságának időtartama
- Az utolsó vásárlás óta eltelt idő

## <a name="build-a-new-measure-using-a-template"></a>Új mérték létrehozása sablon használatával

1. Lépjen a Measures (Intézkedések) elemre **·**.

1. Válassza az **Új**, és a **Sablon kiválasztása** lehetőséget.

   :::image type="content" source="media/measure-use-template.png" alt-text="Képernyőkép a legördülő menüről, amikor új mérőintézkedést hoz létre, kiemelve a sablont.":::

1. Keresse meg az igényeinek megfelelő sablont, és válassza a **Sablon kiválasztása** lehetőséget.

1. Tekintse át a kötelező adatokat, és válassza az **Első lépések** lehetőséget, ha minden adat a megfelelő helyen van.

1. Válassza a Részletek **szerkesztése lehetőséget** a Mérték neve mellett. Adja meg a mérték nevét. Ha szükséges, adjon hozzá [címkéket](work-with-tags-columns.md#manage-tags) a mértékhez.

   :::image type="content" source="media/measures_edit_details.png" alt-text="Részletek szerkesztése párbeszédpanel.":::

1. Válassza a **Kész** lehetőséget.

1. **Az Időszak** beállítása szakaszban határozza meg az adatok időkeret. Válassza ki, hogy az új mérés lefedi-e a teljes adathalmazt az **Összes idő** kiválasztásával, vagy ha azt szeretné, hogy a mérés egy **Adott időszakra** összpontosítson.

   :::image type="content" source="media/measure-set-time-period.png" alt-text="Képernyőkép, amely egy sablonból származó mérték konfiguálásakor mutatja az időszak szakaszt.":::

1. A következő szakaszban válassza az **Adatok hozzáadása** lehetőséget a tevékenységek kiválasztásához, és az *Egyesített tevékenység* entitásból képezze le a megfelelő adatokat.

    1. A 1/2. lépés: A **Tevékenység típusa** alatt válassza ki a használni kívánt entitás típusát. A Tevékenységek **mezőben** válassza ki a leképezni kívánt entitásokat, majd kattintson a Tovább **gombra**.
    1. 2/2. lépés: Válassza ki az attribútumot az *Egyesített tevékenység* entitásból a képlet által megkövetelt összetevőhöz. Például az Átlagos tranzakció értéke a Tranzakció értéket képviselő attribútum. A Tevékenység időbélyegzője **mezőben** válassza ki az Egyesített tevékenység *entitás attribútumát*, amely a tevékenység dátumát és idejét jelöli.
    1. Válassza a **Mentés** parancsot.

    Ha az adatleképezés sikeres, az állapot a Befejezett **állapotot mutatja**, és megjelenik a leképezett tevékenységek és attribútumok neve.

1. Válassza a Futtatás **lehetőséget** a mérték eredményeinek kiszámításához. Válassza a Piszkozat **mentése lehetőséget**, ha meg szeretné tartani az aktuális konfigurációt, és később szeretné futtatni a mértéket. Megjelenik a **Mértékek** oldal.

## <a name="next-step"></a>Következő lépés

Vevői szegmens létrehozásához [használja a meglévő mértékeket](segments.md).

[!INCLUDE [footer-include](includes/footer-banner.md)]
