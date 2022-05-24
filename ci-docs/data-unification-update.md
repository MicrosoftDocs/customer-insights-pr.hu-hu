---
title: Az egyesítési beállítások frissítése
description: Duplikált szabályok, egyezési szabályok vagy egységes mezők frissítése az egyesítési beállításokban.
ms.date: 05/04/2022
ms.subservice: audience-insights
ms.topic: tutorial
author: v-wendysmith
ms.author: mukeshpo
ms.reviewer: v-wendysmith
manager: shellyha
searchScope:
- ci-match
- ci-merge
- ci-relationships
- customerInsights
ms.openlocfilehash: be399da9b98d8803d7d1a90f44a40e0d638a8d47
ms.sourcegitcommit: 4ae316c856b8de0f08a4605f73e75a8c2cf51c4e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2022
ms.locfileid: "8755593"
---
# <a name="update-the-unification-settings"></a>Az egyesítési beállítások frissítése

[!INCLUDE [m3-prod-trial-note](includes/m3-prod-trial-note.md)]

Ha az egységes profil létrehozása után szeretné áttekinteni vagy módosítani az egyesítési beállításokat, hajtsa végre az alábbi lépéseket.

1. Nyissa meg az **Adatok** > **egyesítését**.

   :::image type="content" source="media/m3_unified.png" alt-text="Képernyőkép az Adatok egyesítése lapról az adatok egyesítése után.":::

   > [!TIP]
   > Az **Egyező feltételek** csempe csak akkor jelenik meg, ha több entitás van kijelölve.

1. Válassza ki, hogy mit szeretne frissíteni:
   - [Forrásmezők](#edit-source-fields) entitások vagy attribútumok hozzáadásához vagy attribútumtípusok módosításához.
   - [Duplikált bejegyzések](#manage-deduplication-rules) a deduplikációs szabályok kezeléséhez vagy a beállítások egyesítéséhez.
   - [A feltételek](#manage-match-rules) egyeztetése a megfelelő szabályok frissítéséhez két vagy több entitás között.
   - [Egyesített vevőmezők](#manage-unified-fields) a mezők egyesítéséhez vagy kizárásához. A kapcsolódó profilokat fürtökbe is csoportosíthatja.

1. A módosítások elvégzése után válassza ki a következő lehetőséget:

   :::image type="content" source="media/m3_run_match_merge.png" alt-text="Képernyőkép az Adategyesítés lapról, amelyen az Egyesítés beállítások vannak kiemelve.":::

   - Az egységes ügyfélprofil frissítéséhez (függőségekkel vagy anélkül) olvassa el az ügyfélprofil frissítéseinek futtatása című [témakört](#run-updates-to-the-unified-customer-profile).
   - Ha az egységes profil frissítése nélkül szeretné kiértékelni a megfelelő feltételek minőségét, olvassa el az Egyező feltételek [futtatása című témakört](#run-matching-conditions). A **Csak** egyező feltételek futtatása beállítás nem jelenik meg egyetlen entitásnál.

## <a name="edit-source-fields"></a>Forrásmezők szerkesztése

Nem távolíthat el attribútumot vagy entitást, ha már egységesítették őket.

1. Válassza **a Szerkesztés** lehetőséget a **Forrásmezők** csempén.

   :::image type="content" source="media/m3_source_edit.png" alt-text="Képernyőkép a Forrásmezők lapról, amelyen az elsődleges kulcsok, a leképezett és a leképezetlen mezők száma látható":::

   A leképezett és leképezetlen mezők száma megjelenik.

1. Válassza **az Entitások és mezők** kijelölése lehetőséget más attribútumok vagy entitások hozzáadásához. A keresés vagy a görgetés segítségével keresse meg és jelölje ki az érintett attribútumokat és entitásokat. Válassza az **Alkalmaz** lehetőséget.

1. Az entitások elsődleges kulcsát, az attribútumtípusokat is módosíthatja, és be- és kikapcsolhatja **az intelligens hozzárendelést**. További információt az attribútumok [elsődleges kulcsának és szemantikai típusának kiválasztása című témakörben talál](map-entities.md#select-primary-key-and-semantic-type-for-attributes).

1. Válassza a Tovább lehetőséget **a deduplikációs szabályok módosításához, vagy válassza a Mentés és bezárás** lehetőséget **, és térjen vissza az egyesítési beállítások** frissítése parancsra [.](#update-the-unification-settings)

## <a name="manage-deduplication-rules"></a>Deduplikációs szabályok kezelése

1. Válassza a Szerkesztés **lehetőséget** az **Ismétlődő rekordok** csempén.

   :::image type="content" source="media/m3_duplicates_edit.png" alt-text="Képernyőkép: Ismétlődő rekordok lap a duplikált bejegyzések számát megjelenítő lapról" lightbox="media/m3_duplicates_edit.png":::

   Az Ismétlődések **csoportban** megjelenő ismétlődő rekordok száma. A **Rekordok deduplikált** oszlop azt mutatja, hogy mely entitások rendelkeztek ismétlődő rekordokkal és a duplikált rekordok százalékos arányával.

1. Ha gazdag entitást adott hozzá, válassza a Gazdagított entitások **használata lehetőséget**. További információt az adatforrások gazdagítása című témakörben [talál](data-sources-enrichment.md).

1. A deduplikációs szabályok kezeléséhez válasszon az alábbi lehetőségek közül:
   - **Új szabály** létrehozása: Válassza **a Szabály** hozzáadása lehetőséget a megfelelő entitás alatt. További információt a Deduplikációs szabályok [meghatározása című témakörben talál](remove-duplicates.md#define-deduplication-rules).
   - **Szabályfeltételek** módosítása: Jelölje ki a szabályt, majd **szerkessze**. Mezők módosítása, feltételek hozzáadása vagy eltávolítása, illetve kivételek hozzáadása vagy eltávolítása.
   - **Előnézet**: Jelölje ki a szabályt, majd **az Előnézet lehetőséget** a szabály utolsó futtatási eredményeinek megtekintéséhez.
   - **Szabály** inaktiválása: Jelölje ki a szabályt, majd **inaktiválva** a deduplikációs szabály megőrzéséhez, miközben kizárja azt az egyeztetési folyamatból.
   - **Szabály** másolása: Jelölje ki a szabályt, majd **duplikáljon**, ha módosításokat tartalmazó hasonló szabályt szeretne létrehozni.
   - **Szabály** törlése: Jelölje ki a szabályt, majd **törölje a sort**.

1. Az egyesítési beállítások módosításához jelölje ki az entitást. A beállításokat csak akkor módosíthatja, ha szabály jön létre.
   1. Válassza **az Egyesítés beállításainak szerkesztése lehetőséget**, és módosítsa a Rekord megtartása **beállítást**.
   1. Az entitás egyes attribútumainak egyesítési beállításainak módosításához válassza a Speciális **lehetőséget**, és végezze el a szükséges módosításokat.

      :::image type="content" source="media/m3_adv_merge.png" alt-text="Képernyőkép a legutóbbi e-mail és a legteljesebb cím megjelenítésére szolgáló speciális egyesítési beállításokról":::

   1. Válassza a **Kész** lehetőséget.

1. Válassza a Tovább lehetőséget **az egyező feltételek módosításához, vagy válassza a Mentés és bezárás** lehetőséget **, és térjen vissza az egyesítési beállítások** frissítéséhez [.](#update-the-unification-settings)

## <a name="manage-match-rules"></a>Egyezési szabályok kezelése

Az egyezési paraméterek nagy része konfigurálható és finomhangolható. Entitások nem adhatók hozzá és nem törölhetők. Az egyeztetési szabályok nem vonatkoznak egyetlen entitásra.

1. Válassza a Szerkesztés **lehetőséget** az **Egyező feltételek** csempén.

   :::image type="content" source="media/m3_match_edit.png" alt-text="Képernyőkép a Szabályok és feltételek egyeztetése lapról statisztikákkal." lightbox="media/m3_match_edit.png":::

   Az oldalon megjelenik az egyezési sorrend, a meghatározott szabályok és a következő statisztikák:
   - **Az egyedi forrásrekordok** az utolsó egyezési futtatásban feldolgozott forrásrekordok számát mutatják.
   - **Az egyező és nem egyező rekordok** kiemelik, hogy hány egyedi rekord marad meg az egyezésszabályok feldolgozása után.
   - A **Csak egyező rekordok** az összes egyezéspárban található egyezések számát mutatja.

1. Az összes szabály eredményeinek és pontszámainak megtekintéséhez válassza az Utolsó futtatás megtekintése **lehetőséget**. Az eredmények megjelennek, beleértve az alternatív névjegyazonosítókat is. Letöltheti az eredményeket.

1. Egy adott szabály eredményeinek és pontszámainak megtekintéséhez jelölje ki a szabályt, majd **az Előnézet parancsot**. Az eredmények megjelennek. Letöltheti az eredményeket.

1. Egy szabály adott feltételének eredményeinek megtekintéséhez jelölje ki a szabályt, majd **a Szerkesztés parancsot**. A Szerkesztés ablaktáblán válassza a Feltétel melletti Előnézet **lehetőséget**. Letöltheti az eredményeket.

   :::image type="content" source="media/m3_match_condition_preview.png" alt-text="Páratlan és egyező rekordok grafikus ábrázolása, beleértve az adatok listáját is.":::

1. Ha gazdag entitást adott hozzá, válassza a Gazdagított entitások **használata lehetőséget**. További információt az adatforrások gazdagítása című témakörben [talál](data-sources-enrichment.md).

1. A szabályok kezeléséhez válasszon az alábbi lehetőségek közül:
   - **Új szabály** létrehozása: Válassza **a Szabály** hozzáadása lehetőséget a megfelelő entitás alatt. További információt az egyezési párok [szabályainak meghatározása című témakörben talál](match-entities.md#define-rules-for-match-pairs).
   - **Módosítsa a szabályok** sorrendjét, ha több szabályt is megadott: Húzza és dobja a szabályokat a kívánt sorrendbe. További információt az Egyezési sorrend [megadása című témakörben talál](match-entities.md#specify-the-match-order).
   - **Szabályfeltételek** módosítása: Jelölje ki a szabályt, majd **szerkessze**. Mezők módosítása, feltételek hozzáadása vagy eltávolítása, illetve kivételek hozzáadása vagy eltávolítása.
   - **Szabály** inaktiválása: Jelölje ki a szabályt, majd **inaktiváljon** egy egyezési szabályt, hogy megtartsa az egyezési szabályt, miközben kizárja azt az egyeztetési folyamatból.
   - **Szabály** másolása: Jelölje ki a szabályt, majd **duplikáljon**, ha módosításokat tartalmazó hasonló szabályt szeretne létrehozni.
   - **Szabály** törlése: Jelölje ki a szabályt, majd **törölje a sort**.

1. Az egységes mezők módosításához kattintson a Tovább gombra **, vagy válassza a Mentés és bezárás** lehetőséget, majd térjen **vissza** az egyesítő beállítások [frissítéséhez](#update-the-unification-settings).

## <a name="manage-unified-fields"></a>Egységes mezők kezelése

1. Válassza a Szerkesztés **lehetőséget** az **Egyesített vevőmezők** csempén.

    :::image type="content" source="media/m3_merge_edit.png" alt-text="Képernyőkép az Egyesített vevőmezőkről":::

1. Tekintse át az egyesített és kizárt mezőket, és szükség szerint végezze el a módosításokat. Adja hozzá vagy szerkessze a CustomerID kulcsot vagy csoportprofilokat fürtökbe. További információt a Vevőmezők [egyesítése című témakörben talál](merge-entities.md).

1. Válassza a Tovább lehetőséget **az** egyesítési beállítások áttekintéséhez, valamint [az egyesített profil és függőségek](#run-updates-to-the-unified-customer-profile) frissítéséhez, vagy válassza a Mentés és bezárás **lehetőséget**, és térjen vissza az egyesítési beállítások [frissítéséhez](#update-the-unification-settings) a további módosításokhoz.

## <a name="run-matching-conditions"></a>Megfelelő feltételek futtatása

1. **Az Adatok** > **egyesítése** lapon válassza **a Csak** egyező feltételek futtatása lehetőséget.

   Az **Ismétlődő rekordok** és **az Egyező feltételek** csempék várólistán **vagy** frissítőn jelennek **meg**.

   [!INCLUDE [m3-task-details-include](includes/m3-task-details.md)]

1. Amikor az egyeztetési folyamat befejeződött, válassza a Szerkesztés **lehetőséget** az **Egyeztetési feltételek** csempén.

   :::image type="content" source="media/match-KPIs.png" alt-text="Körülvágott képernyőkép a legfontosabb mutatókról a Egyezés oldalon, számokkal és részletekkel.":::

1. A módosítások elvégzéséhez olvassa el a Deduplikációs szabályok kezelése vagy [az Egyezési szabályok kezelése című témakört.](#manage-deduplication-rules)[...](#manage-match-rules)

1. Futtassa újra az egyeztetési folyamatot, vagy [futtassa az ügyfélprofil frissítéseit](#run-updates-to-the-unified-customer-profile).

## <a name="run-updates-to-the-unified-customer-profile"></a>Az egységes ügyfélprofil frissítéseinek futtatása

1. Az Adatok **egyesítése** > **lapon válassza a** következőket:

   - **Ügyfélprofilok** egyesítése: Frissíti az egységes ügyfélprofil-entitást anélkül, hogy befolyásolná a függőségeket (például gazdagodásokat, szegmenseket vagy intézkedéseket). A függő folyamatok nem futnak, de a frissítési ütemezésben [meghatározottak szerint](system.md#schedule-tab) frissülnek.

   - **Ügyfélprofilok és függőségek** egyesítése: Frissíti az egységes profilt és az összes függőséget. A rendszer automatikusan futtatja az összes folyamatot. Miután az összes downstream folyamat befejeződött, az ügyfélprofil tükrözi a frissített adatokat.

   Az **Ismétlődő rekordok**, **az Egyező feltételek** és **az Egyesített vevőmezők** csempék várólistán **vagy** frissítve jelennek **meg**.

   [!INCLUDE [m3-task-details-include](includes/m3-task-details.md)]
