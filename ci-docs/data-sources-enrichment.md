---
title: Adatforrások gazdagítása (előzetes verzió)
description: Bővítse az adatforrásokat, mielőtt végigmegy az adategyesítési folyamaton.
ms.date: 05/20/2022
ms.subservice: audience-insights
ms.topic: how-to
author: NimrodMagen
ms.author: nimagen
ms.reviewer: v-wendysmith
manager: shellyha
ms.openlocfilehash: 98e9e330e7ef9cf085caa94a506fa788cebdd67b
ms.sourcegitcommit: 5807b7d8c822925b727b099713a74ce2cb7897ba
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/28/2022
ms.locfileid: "9207186"
---
# <a name="enrichment-for-data-sources-preview"></a>Adatforrások gazdagítása (előzetes verzió)

Használjon olyan forrásokból származó adatokat, mint a Microsoft és más partnerek, hogy az adatok egyesítése előtt gazdagítsa az ügyféladatokat. Adatforrás gazdagítások segítenek az adatok teljességének és minőségének javításában, ami segíthet jobb eredmények elérésében az adatok egységesítése után. Ha például normalizált és szabványosított formátumot használ a címekhez, az javítja az egyezési eredmények minőségét. A támogatott gazdagítások listáját lásd: [támogatott adatforrás gazdagítási lehetőségek](#supported-data-source-enrichments).

## <a name="enrich-a-data-source"></a>Adatforrás gazdagítása

A bővítések létrehozásához és szerkesztéséhez közreműködő vagy rendszergazdai [engedéllyel](permissions.md) kell rendelkeznie.  

1. Lépjen az Adatok **egyesítése oldalra** > **·**. Válassza ki a gazdagítani kívánt entitást, és válasszon ki egy [attribútumot az entitás elsődleges kulcsaként](map-entities.md#select-primary-key-and-semantic-type-for-attributes).

1. Válassza az **Adatok** > **Adatforrások** lehetőséget.

1. Válassza ki a gazdagítani kívánt adatforrás melletti függőleges három pontot (&vellip;), majd válassza a Gazdagítás **lehetőséget**.

   :::image type="content" source="media/data_sources_enrich.png" alt-text="Adatforrások lapja kiemelt Enrich funkcióval":::

   A **Felfedezés** lapon megjelenik a [támogatott adatforrás gazdagítási lehetőségek](#supported-data-source-enrichments).

   :::image type="content" source="media/data_sources_enrich_discover.png" alt-text="Adatforrások gazdagítási oldala.":::

1. Válassza az Adatok **gazdagítása lehetőséget** a adatforrás gazdagítás konfigurálásához. A kimeneti entitás neve automatikusan ki lesz töltve.

## <a name="supported-data-source-enrichments"></a>Támogatott adatforrás gazdagítások

Az adatforrásokhoz jelenleg a következő bővítések érhetők el. Tekintse át a gazdagítás részletes lépéseit, és ismerje meg, hogyan konfigurálhatja azt.

- [Továbbfejlesztett címek](enrichment-enhanced-addresses.md)
- [Továbbfejlesztett vállalati adatok](enrichment-enhanced-company-data.md)
- [Személyazonosító adatok a LiveRamp-ből](enrichment-liveramp.md)

## <a name="manage-existing-data-source-enrichments"></a>Meglévő adatforrás gazdagítások kezelése

Lépjen az **Adatok** > **Bővítés** pontra. **A Saját bővítések** lapon tekintse meg a konfigurált gazdagításokat, azok állapotát, a bővített ügyfelek számát és az adatok legutóbbi frissítésének időpontját. A gazdagodások listáját bármely oszlop szerint rendezheti, vagy a keresőmező segítségével megkeresheti a kezelni kívánt gazdagítást.

Az elérhető lehetőségekért válassza ki a bővítést. A beállítások megtekintéséhez kiválaszthatja a függőleges három pontot (&vellip;) egy listaelemen.

Megtekintheti, szerkesztheti, futtathatja vagy törölheti a adatforrás gazdagítást. További információ: [Meglévő gazdagítások](enrichment-hub.md#manage-existing-enrichments) kezelése.
