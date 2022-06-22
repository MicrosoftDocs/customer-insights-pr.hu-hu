---
title: Adatforrás dúsítás
description: Bővítse az adatforrásokat, mielőtt végigmegy az adategyesítési folyamaton.
ms.date: 05/20/2022
ms.subservice: audience-insights
ms.topic: how-to
author: NimrodMagen
ms.author: nimagen
ms.reviewer: v-wendysmith
manager: shellyha
ms.openlocfilehash: b34b83d7a73dbdf21984f626174524188f0f1dc1
ms.sourcegitcommit: 5e26cbb6d2258074471505af2da515818327cf2c
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/14/2022
ms.locfileid: "9011476"
---
# <a name="enrichment-for-data-sources-preview"></a>Adatforrások gazdagítása (előzetes verzió)

Használjon olyan forrásokból származó adatokat, mint a Microsoft és más partnerek, hogy az adatok egyesítése előtt gazdagítsa az ügyféladatokat. Adatforrás gazdagítások segítenek az adatok teljességének és minőségének javításában, ami segíthet jobb eredmények elérésében az adatok egységesítése után. Ha például normalizált és szabványosított formátumot használ a címekhez, az javítja az egyezési eredmények minőségét. A támogatott gazdagítások listáját lásd: [támogatott adatforrás gazdagítási lehetőségek](#supported-data-source-enrichments).

## <a name="enrich-a-data-source"></a>Adatforrás gazdagítása

A bővítések létrehozásához és szerkesztéséhez közreműködő vagy rendszergazdai engedéllyel kell rendelkeznie. További tudnivalók: [Engedélyek](permissions.md).  

1. Lépjen az Adatok **egyesítése oldalra** > **·**. Válassza ki a gazdagítani kívánt entitást, és válasszon ki egy attribútumot az entitás elsődleges kulcsaként. További információ: [Elsődleges kulcs kiválasztása](map-entities.md#select-primary-key-and-semantic-type-for-attributes).

1. Válassza az **Adatok** > **Adatforrások** lehetőséget.

1. Válassza ki a gazdagítani kívánt adatforrás melletti függőleges három pontot (&vellip;), majd válassza a Gazdagítás **lehetőséget**.

   :::image type="content" source="media/data_sources_enrich.png" alt-text="Adatforrások lapja kiemelt Enrich funkcióval":::

   A **Felderítés** lapon megjelenik a [támogatott adatforrás gazdagítási lehetőségek](#supported-data-source-enrichments).

   :::image type="content" source="media/data_sources_enrich_discover.png" alt-text="Adatforrások gazdagítási oldala.":::

1. Válassza az Adatok **gazdagítása lehetőséget** a adatforrás gazdagítás konfigurálásához. A kimeneti entitás neve automatikusan ki lesz töltve.

## <a name="supported-data-source-enrichments"></a>Támogatott adatforrás gazdagítások

Az adatforrásokhoz jelenleg a következő bővítések érhetők el. Tekintse át a gazdagítás részletes lépéseit, és ismerje meg, hogyan konfigurálhatja azt.

- [Továbbfejlesztett címek](enrichment-enhanced-addresses.md)
- [Továbbfejlesztett vállalati adatok](enrichment-enhanced-company-data.md)
- [Személyazonosító adatok a LiveRamp-ből](enrichment-liveramp.md)

## <a name="manage-existing-data-source-enrichments"></a>Meglévő adatforrás gazdagítások kezelése

Menjen a **Saját bővítéseim** fülre az összes konfigurált bővítés megtekintéséhez.

Az elérhető lehetőségekért válassza ki a bővítést. A beállítások megtekintéséhez kiválaszthatja a függőleges három pontot (&vellip;) egy listaelemen. Ha több bővítést is konfigurált, a keresőmező segítségével gyorsan megkeresheti.

Megtekintheti, szerkesztheti, futtathatja vagy törölheti a adatforrás gazdagítást. További információ: [Meglévő gazdagítások](enrichment-hub.md) kezelése.
