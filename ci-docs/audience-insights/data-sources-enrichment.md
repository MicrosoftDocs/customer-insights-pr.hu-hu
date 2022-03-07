---
title: Adatforrás gazdagodás
description: Az adategyesítési folyamat előtt gazdagítsa az adatforrásokat.
ms.date: 03/02/2022
ms.subservice: audience-insights
ms.topic: how-to
author: NimrodMagen
ms.author: nimagen
ms.reviewer: v-wendysmith
manager: shellyha
ms.openlocfilehash: eebaaf18795e80dd1ba16a15a23844d685c94c6e
ms.sourcegitcommit: bb1f9e96023490ab340c114f54200ab4dd48da78
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/02/2022
ms.locfileid: "8373065"
---
# <a name="enrichment-for-data-sources-preview"></a>Adatforrások gazdagítása (előzetes verzió)

Az adategyesítés előtt olyan forrásokból származó adatokat használhat, mint a Microsoft és más partnerek. Adatforrás gazdagodások segítenek nagyobb adat teljességet és minőséget eredményezni, ami segíthet jobb eredmények elérésében az adatok egyesítése után. Például a címek normalizált és szabványosított formátumának használata növeli az egyezési eredmények minőségét. A támogatott gazdagodások listáját a támogatott adatforrás gazdagodási lehetőségek című témakörben [talál](#supported-data-source-enrichments).

## <a name="enrich-a-data-source"></a>Gazdagítani egy adatforrás

A gazdagodások létrehozásához vagy szerkesztéséhez közreműködő vagy rendszergazdai engedéllyel kell rendelkeznie. További tudnivalók: [Engedélyek](permissions.md).  

1. Lépjen a DataUnify-ra **·** > **·**. Válassza ki a gazdagítani kívánt entitást, és jelöljön ki egy attribútumot elsődleges kulcsként az entitáshoz. További információt az Elsődleges kulcs kiválasztása című témakörben [talál](map-entities.md#select-primary-key-and-semantic-type-for-attributes).

1. Válassza az **Adatok** > **Adatforrások** lehetőséget.
 
1. Jelölje ki a gazdagítani kívánt adatforrás melletti függőleges ellipszis elemet, és válassza a Gazdagodás **lehetőséget**.

   :::image type="content" source="media/data_sources_enrich_discover.png" alt-text="Adatforrás-gazdagító lap.":::

   A **Felfedezés** lapon a [támogatott adatforrás gazdagodási beállítások jelennek](#supported-data-source-enrichments) meg.

1. A adatforrás gazdagodás konfigurálásához válassza a Adatok **gazdagítása lehetőséget**. A kimeneti entitás neve automatikusan ki van töltve.

## <a name="supported-data-source-enrichments"></a>Támogatott adatforrás dúsítások

Az adatforrások számára jelenleg a következő gazdagodások érhetők el. Tekintse át a gazdagodás részletes lépéseit, és ismerje meg, hogyan konfigurálhatja azt.

- [Továbbfejlesztett címek](enrichment-enhanced-addresses.md)
- [Identitásadatok a LiveRamp-ból](enrichment-liveramp.md)

## <a name="manage-existing-data-source-enrichments"></a>Meglévő adatforrás gazdagodások kezelése

Menjen a **Saját bővítéseim** fülre az összes konfigurált bővítés megtekintéséhez.

Az elérhető lehetőségekért válassza ki a bővítést. A listaelemen a három pont (...) kijelölésével megtekintheti a lehetőségeket. Ha több bővítést is konfigurált, a keresőmező segítségével gyorsan megkeresheti.

Megtekinthet, szerkeszthet, futtathat vagy törölhet egy adatforrás gazdagodást. További információt a Meglévő gazdagodások [kezelése című témakörben talál](enrichment-hub.md).
