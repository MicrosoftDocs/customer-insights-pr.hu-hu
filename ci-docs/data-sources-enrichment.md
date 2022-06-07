---
title: Adatforrás gazdagodás
description: Az adategyesítési folyamat előtt gazdagítsa az adatforrásokat.
ms.date: 05/20/2022
ms.subservice: audience-insights
ms.topic: how-to
author: NimrodMagen
ms.author: nimagen
ms.reviewer: v-wendysmith
manager: shellyha
ms.openlocfilehash: 1225482c4bf432ed747537b2c9bec9ab0e692a51
ms.sourcegitcommit: b515120bebd2638f2639004422cee3cff42fbdf7
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/24/2022
ms.locfileid: "8800284"
---
# <a name="enrichment-for-data-sources-preview"></a>Adatforrások gazdagítása (előzetes verzió)

Az adatok egyesítése előtt olyan forrásokból származó adatokat használhat, mint a Microsoft és más partnerek. Adatforrás gazdagodás segít a nagyobb adattömörség és minőség elérésében, ami segíthet jobb eredmények elérésében az adatok egységesítése után. Például a címek normalizált és szabványosított formátumának használata növeli az egyezés eredményeinek minőségét. A támogatott gazdagodások listáját a támogatott adatforrás dúsítási lehetőségek című témakörben [találja](#supported-data-source-enrichments).

## <a name="enrich-a-data-source"></a>Gazdagítsa a adatforrás

Gazdagodás létrehozásához vagy szerkesztéséhez közreműködő vagy rendszergazdai engedéllyel kell rendelkeznie. További tudnivalók: [Engedélyek](permissions.md).  

1. Nyissa meg az **Adatok** > **egyesítését**. Válassza ki a gazdagítani kívánt entitást, és válasszon ki egy attribútumot elsődleges kulcsként az entitáshoz. További információt az Elsődleges kulcs kiválasztása című témakörben [talál](map-entities.md#select-primary-key-and-semantic-type-for-attributes).

1. Válassza az **Adatok** > **Adatforrások** lehetőséget.

1. Jelölje ki a gazdagítani kívánt adatforrás melletti függőleges ellipszis (&vellip;) pontot, és válassza a Gazdagodás **lehetőséget**.

   :::image type="content" source="media/data_sources_enrich_discover.png" alt-text="Adatforrások gazdagodó oldal.":::

   A **Felfedezés** lapon a [támogatott adatforrás gazdagodási beállítások](#supported-data-source-enrichments) jelennek meg.

1. Az adatok **gazdagítása lehetőséget választja** a adatforrás gazdagodás konfigurálásához. A kimeneti entitás neve automatikusan ki lesz töltve.

## <a name="supported-data-source-enrichments"></a>Támogatott adatforrás gazdagodás

Az adatforrások esetében jelenleg a következő bővítések állnak rendelkezésre. Tekintse át a gazdagodás részletes lépéseit, és ismerje meg, hogyan kell konfigurálni.

- [Továbbfejlesztett címek](enrichment-enhanced-addresses.md)
- [Továbbfejlesztett vállalati adatok](enrichment-enhanced-company-data.md)
- [Identitásadatok a LiveRamp-ból](enrichment-liveramp.md)

## <a name="manage-existing-data-source-enrichments"></a>Meglévő adatforrás-dúsítások kezelése

Menjen a **Saját bővítéseim** fülre az összes konfigurált bővítés megtekintéséhez.

Az elérhető lehetőségekért válassza ki a bővítést. A beállítások megtekintéséhez a listaelem függőleges ellipszisét (&vellip;) is kiválaszthatja. Ha több bővítést is konfigurált, a keresőmező segítségével gyorsan megkeresheti.

A gazdagodás adatforrás megtekintheti, szerkesztheti, futtathatja vagy törölheti. További információt a Meglévő dúsítások [kezelése című témakörben talál](enrichment-hub.md).
