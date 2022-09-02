---
title: Szegmensekkel kapcsolatosa információk (előzetes verzió)
description: Szerezzen információkat a meglevő szegmensekről, hogy felfedezhesse a különbségeket és egyezéseket.
ms.date: 06/10/2020
ms.subservice: audience-insights
ms.topic: how-to
author: JimsonChalissery
ms.author: jimsonc
ms.reviewer: mhart
manager: shellyha
searchScope:
- ci-segment-insights
- customerInsights
ms.openlocfilehash: ccb33594a3a92e87d307f3300c77772ef8b4a82f
ms.sourcegitcommit: 8a28e9458b857adf8e90e25e43b9bc422ebbb2cd
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/18/2022
ms.locfileid: "9171006"
---
# <a name="segment-insights-preview"></a>Szegmensekkel kapcsolatosa információk (előzetes verzió)

Ismerje meg a meglévő szegmensekhez kapcsolódó további információkat és betekintést. Megtudhatja, hogy mi különbözteti meg a két szegmenst, illetve hogy mi a közös bennük.

## <a name="segment-overlap"></a>Szegmensátfedés

A szegmensátfedés elemzése azt mutatja, hogy hány és mely ügyfelek közösen két vagy több szegmensben. Tegyük fel például, hogy a gyakori ügyfelek egy szegmense átfedésben van egy olyan szegmenssel, amely a szolgáltatásával vagy a termékkel elégedett ügyfeleket tartalmaz.
Elemezheti azt is, hogyan módosul az átfedés az egyes attribútumok esetében.

### <a name="run-an-overlap-analysis"></a>Átfedéselemzés futtatása

1. Nyissa meg a **Szegmenseket** menüt, és válassza a **Háttér-információk** (előzetes verzió) lapot.

1. Válassza az **Új** lehetőséget, és válassza az **Átfedés** beállítást a **Háttér-információ típusának kiválasztása** ablaktáblában.

1. Válassza ki az érdekes szegmenseket, és válassza a **Következő** lehetőséget.

1. Tetszés szerint kiválaszthat egy vagy több érdekes mezőt is, amelyekkel elemezheti a átfedéseket minden lehetséges mezőérték esetében, majd válassza a **Tovább** lehetőséget.

1. Adja meg az átfedéselemzés nevét, a választható megjelenítendő nevet és leírást.

1. Az elemzés megkezdéséhez válassza a **Mentés** lehetőséget. Az átfedések elemzése elkészül, amikor az állapot a Frissítés értékről a Sikeres értékre változik.

### <a name="view-and-optimize-an-overlap-analysis"></a>Átfedések elemzésének megtekintése és optimalizálása

1. Az elemzés befejezése után a háttér-információ részleteit a **Szegmensek** > **Háttér információk (előzetes verzió)** helyen találja.

   :::image type="content" source="media/segment-overlap.png" alt-text="Szegmens átfedés háttér-információinak részletei.":::

1. Az elemzési eredmények megtekintéséhez válasszon ki egy betekintést:

   - Az elemzésre kiválasztott szegmensekben található átfedő tagok száma.
   - A szegmensek egyikében, azonban a többiben nem szereplő tagok száma.
   - Ha az átfedési elemzés konfigurálásakor kijelölt mezőket, a megfelelő lapokon találja azokat. A legördülő szűrő segítségével bármilyen attribútum szintet kijelölhet, és az alsó táblázatban a megfelelő adatok fognak mutatni.

## <a name="segment-differentiators"></a>Szegmensmegkülönböztetők

A szegmens-megkülönböztetők segítségével megtudhatja, hogy mi különbözteti meg a szegmenseket az ügyfelek többi részétől vagy egy másik szegmenstől. Válasszon ki egy szegmenst, és a rendszer azonosítja azokat a profilattribútumokat és mértékeket, amelyek megkülönböztetik a kijelölt szegmenst.

### <a name="run-a-differentiator-analysis"></a>Megkülönböztető elemzés futtatása

1. Nyissa meg a **Szegmenseket** menüt, és válassza a **Háttér-információk** (előzetes verzió) lapot.

1. Válassza az Új lehetőséget **, és válassza a** Megkülönböztető tényezők **lehetőséget a** Betekintés típusa **kiválasztása** panelen.

1. Válassza ki azt a szegmenst, amelyet szeretne elemezni **Elsődleges szegmensnek**, majd válassza a **Tovább** lehetőséget.

1. Válassza az **Összes ügyfél** vagy **Másodlagos szegmens** elemet az elsődleges szegmenssel való összehasonlításához, majd válassza a **Tovább** lehetőséget.

1. Tetszés szerint kiválaszthat egy vagy több érdekes mezőt is, amelyekkel az elemzést meghatározott attribútumokra összpontosíthatja, majd válassza a **Tovább** lehetőséget.

1. Adja meg a megkülönböztető elemzés nevét, egy opcionális megjelenítendő név és egy leírást.

1. Az elemzés megkezdéséhez válassza a **Mentés** lehetőséget. A megkülönböztető elemzés akkor áll készen, ha az állapot Frissítésről Sikeresre változik.

### <a name="view-and-optimize-a-differentiators-analysis"></a>Megkülönböztető elemzés megtekintése és optimalizálása

1. Az elemzés befejezése után lépjen a Segments **Insights (előzetes verzió) lapra** > **·**.

   :::image type="content" source="media/segment-differentiators.png" alt-text="Szegmens megkülönböztető háttér-információinak részletei.":::

1. Az elemzési eredmények megtekintéséhez válasszon ki egy betekintést. A megkülönböztető elemzés két lapból áll. Az **Attribútumok** lap felsorolja a megkülönböztető tulajdonságokkal rendelkező profil attribútumokat. Az **Mértékek** lapon a megkülönböztető elemek szerepelnek. Minden lap a következő adatokat tartalmazza:

   - A megkülönböztetők rangsorolt listája, a különbségpontszám szerint rendezve.
   - Az egyes megkülönböztető elemek **Különbségi pontszáma**. A különbségi pontszám egy attribútum két szegmens közötti különbségének fokát jelenti. Minél nagyobb a különbség, annál több attribútum tér el a két szegmens között. Válassza ki a pontszám értékét, a **Különbségi pontszám** ablaktábla megnyitásához az attribútumra vonatkozó értékek eloszlásával.

## <a name="manage-segment-insights"></a>Az Szegmensbetekintések kezelése

**A Segments** > **Insights (előzetes verzió)** oldalon megtekintheti a szegmenselemzéseket, és kezelheti azokat. Válasszon ki egy szegmenselemzést az elérhető műveletek megtekintéséhez.

- **Az elemzési elemzés megtekintése**
- **Szerkessze** az elemzéseket a tulajdonságainak módosításához
- **Frissítse** az elemzést az elemzés újbóli futtatásához
- **A betekintés átnevezése**
- **A betekintés törlése**

[!INCLUDE [footer-include](includes/footer-banner.md)]