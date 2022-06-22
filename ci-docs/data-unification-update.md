---
title: Az egyesítési beállítások frissítése
description: Frissítse az ismétlődő szabályokat, az egyeztetési szabályokat vagy az egyesített mezőket az egyesítési beállításokban.
ms.date: 06/01/2022
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
ms.openlocfilehash: 590a2996cf8b2b1c6def59b78583169ec1910b59
ms.sourcegitcommit: 760fbac397c738407c7dea59297d54cae19b6f57
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/03/2022
ms.locfileid: "8844043"
---
# <a name="update-the-unification-settings"></a>Az egyesítési beállítások frissítése

[!INCLUDE [m3-prod-trial-note](includes/m3-prod-trial-note.md)]

Ha az egységesített profil létrehozása után át szeretné tekinteni vagy módosítani szeretné az egyesítési beállításokat, hajtsa végre a következő lépéseket.

1. Lépjen az Adatok **egyesítése oldalra** > **·**.

   :::image type="content" source="media/m3_unified.png" alt-text="Képernyőkép az Adatok egyesítése lapról az adatok egyesítése után.":::

   > [!TIP]
   > Az **Egyezési feltételek** csempe csak akkor jelenik meg, ha több entitás lett kiválasztva.

1. Válassza ki, hogy mit szeretne frissíteni:
   - [Forrásmezők](#edit-source-fields) entitások vagy attribútumok hozzáadásához vagy attribútumtípusok módosításához.
   - [Duplikált rekordok](#manage-deduplication-rules) a deduplikációs szabályok kezeléséhez vagy a beállítások egyesítéséhez.
   - [Egyező feltételek](#manage-match-rules) két vagy több entitás egyező szabályainak frissítéséhez.
   - [Egyesített vevői mezők](#manage-unified-fields) a mezők egyesítéséhez vagy kizárásához. A kapcsolódó profilokat fürtökbe is csoportosíthatja.

1. A módosítások elvégzése után válassza ki a következő lehetőséget:

   :::image type="content" source="media/m3_run_match_merge.png" alt-text="Képernyőkép az Adatok egyesítése lapról, amelyen ki van emelve az Egységesítés lehetőségek.":::

   - [Az egyező feltételek](#run-matching-conditions) futtatásával gyorsan kiértékelheti az egyező feltételek (deduplikáció és egyeztetési szabályok) minőségét az egységes profil frissítése nélkül. Az **Egyezési feltételek** csak futtatása beállítás nem jelenik meg egyetlen entitásnál.
   - [Egyesítse az ügyfélprofilokat](#run-updates-to-the-unified-customer-profile) az egyező feltételek futtatásához, és frissítse az egyesített ügyfélprofil-entitást anélkül, hogy ez hatással lenne a függőségekre (például gazdagodásokra, szegmensekre vagy mértékekre). A függő folyamatok nem futnak, hanem a frissítési ütemezésben [meghatározottak szerint](system.md#schedule-tab) frissülnek.
   - [Egyesítse az ügyfélprofilokat és függőségeket](#run-updates-to-the-unified-customer-profile) az egyező feltételek futtatásához, és frissítse az egyesített ügyfélprofil-entitást és az összes függőséget (például gazdagításokat, szegmenseket vagy mértékeket). Minden folyamat automatikusan újrafuttatható.

## <a name="edit-source-fields"></a>Forrásmezők szerkesztése

Nem távolíthat el egy attribútumot vagy entitást, ha az már egységesített.

1. Válassza a Szerkesztés **lehetőséget** a **Forrásmezők** csempén.

   :::image type="content" source="media/m3_source_edit.png" alt-text="Képernyőkép: a Forrásmezők oldal az elsődleges kulcsok, a leképezett és a nem leképezett mezők számát mutatja":::

   Megjelenik a leképezett és a leképezés nélküli mezők száma.

1. Válassza az Entitások és mezők **kiválasztása lehetőséget** más attribútumok vagy entitások hozzáadásához. A keresés vagy a görgetés segítségével keresse meg és jelölje ki az érintett attribútumokat és entitásokat. Válassza az **Alkalmaz** lehetőséget.

1. Igény szerint módosíthatja az entitás elsődleges kulcsát, az attribútumtípusokat, és be- vagy kikapcsolhatja **az Intelligens leképezés** beállítást. További információ: [Elsődleges kulcs és szemantikai típus kiválasztása attribútumokhoz](map-entities.md#select-primary-key-and-semantic-type-for-attributes).

1. Válassza a Tovább gombot a deduplikációs szabályok módosításához, vagy válassza a Mentés lehetőséget **, zárja be**, majd térjen vissza az Egyesítési beállítások **frissítéseelemhez**.[...](#update-the-unification-settings)

## <a name="manage-deduplication-rules"></a>Deduplikációs szabályok kezelése

1. Válassza a Szerkesztés **lehetőséget** a **Rekordok** megkettőzése csempén.

   :::image type="content" source="media/m3_duplicates_edit.png" alt-text="Képernyőkép a Duplikált rekordok oldaláról, amelyen a duplikált rekordok száma látható" lightbox="media/m3_duplicates_edit.png":::

   A talált duplikált rekordok száma a Duplikátumok **alatt** jelenik meg. A **Rekordok deduplikált** oszlopban látható, hogy mely entitások rendelkeztek duplikált rekordokkal, és hogy hány százalékban voltak duplikált rekordok.

1. Ha bővített entitást adott hozzá, válassza a Bővített entitások **használata lehetőséget**. További információ: [Adatforrások](data-sources-enrichment.md) gazdagítása.

1. A deduplikációs szabályok kezeléséhez válasszon az alábbi lehetőségek közül:
   - **Új szabály** létrehozása: Válassza a Szabály **hozzáadása lehetőséget** a megfelelő entitás alatt. További információ: [Deduplikációs szabályok](remove-duplicates.md#define-deduplication-rules) meghatározása.
   - **Szabályfeltételek** módosítása: Jelölje ki a szabályt, majd **szerkesszen**. Mezők módosítása, feltételek hozzáadása vagy eltávolítása, illetve kivételek hozzáadása vagy eltávolítása.
   - **Előnézet**: Válassza ki a szabályt, majd az Előnézet lehetőséget **a** szabály utolsó futtatási eredményeinek megtekintéséhez.
   - **Szabály** inaktiválása: Válassza ki a szabályt, majd **inaktiválja** a deduplikációs szabály megtartásához, miközben kizárja azt az egyeztetési folyamatból.
   - **Szabály** megkettőzése: Jelölje ki a szabályt, majd **duplikáljon** egy hasonló szabály módosításokkal való létrehozásához.
   - **Szabály** törlése: Jelölje ki a szabályt, majd a Törlés **lehetőséget**.

1. Az egyesítési beállítások módosításához válassza ki az entitást. A beállításokat csak akkor módosíthatja, ha létrehoz egy szabályt.
   1. Válassza az Egyesítési beállítások **szerkesztése lehetőséget**, és módosítsa a **Rekord megtartandó** opciót.
   1. Egy entitás egyes attribútumainak egyesítési beállításainak módosításához válassza a Speciális **lehetőséget**, és végezze el a szükséges módosításokat.

      :::image type="content" source="media/m3_adv_merge.png" alt-text="Képernyőkép a speciális egyesítési beállításokról, amelyeken a legutóbbi e-mail és a legteljesebb cím látható":::

   1. Válassza a **Kész** lehetőséget.

1. Válassza a Tovább gombot az egyező feltételek módosításához, vagy válassza a Mentés és bezárás **lehetőséget**, és térjen vissza az Egyesítési beállítások frissítése **lapra**.[...](#update-the-unification-settings)

## <a name="manage-match-rules"></a>Egyezési szabályok kezelése

Az egyezési paraméterek nagy része konfigurálható és finomhangolható. Nem adhat hozzá és nem törölhet entitásokat. Az egyezési szabályok nem vonatkoznak egyetlen entitásra.

1. Válassza a Szerkesztés **lehetőséget** az **Egyező feltételek** csempén.

   :::image type="content" source="media/m3_match_edit.png" alt-text="Képernyőkép a Szabályok és feltételek egyeztetése lapról statisztikákkal." lightbox="media/m3_match_edit.png":::

   Az oldal megjeleníti az egyezési sorrendet és a meghatározott szabályokat, valamint a következő statisztikákat:
   - **Az egyedi forrásrekordok** az utolsó egyezési futtatásban feldolgozott forrásrekordok számát mutatják.
   - **Az egyező és nem egyező rekordok** kiemelik, hogy hány egyedi rekord marad meg az egyezésszabályok feldolgozása után.
   - A **Csak egyező rekordok** az összes egyezéspárban található egyezések számát mutatja.

1. Az összes szabály eredményének és pontszámának megtekintéséhez válassza az Utolsó futtatás **megtekintése lehetőséget**. Az eredmények megjelennek, beleértve a másodlagos névjegyazonosítókat is. Letöltheti az eredményeket.

1. Egy adott szabály eredményeinek és pontszámainak megtekintéséhez jelölje ki a szabályt, majd az Előnézet **lehetőséget**. Megjelennek az eredmények. Letöltheti az eredményeket.

1. Egy adott feltétel eredményeinek megtekintéséhez jelölje ki a szabályt, majd a Szerkesztés **lehetőséget**. A Szerkesztés panelen válassza az Előnézet **lehetőséget** a feltétel mellett. Letöltheti az eredményeket.

   :::image type="content" source="media/m3_match_condition_preview.png" alt-text="A nem egyező és egyező rekordok grafikus ábrázolása, beleértve az adatok listáját is.":::

1. Ha bővített entitást adott hozzá, válassza a Bővített entitások **használata lehetőséget**. További információ: [Adatforrások](data-sources-enrichment.md) gazdagítása.

1. A szabályok kezeléséhez válasszon az alábbi lehetőségek közül:
   - **Új szabály** létrehozása: Válassza a Szabály **hozzáadása lehetőséget** a megfelelő entitás alatt. További információ: [Szabályok definiálása egyező párokhoz](match-entities.md#define-rules-for-match-pairs).
   - **A szabályok** sorrendjének módosítása, ha több szabályt határozott meg: Húzza át a szabályokat a kívánt sorrendbe. További információ: [Az egyezési sorrend](match-entities.md#specify-the-match-order) megadása.
   - **Szabályfeltételek** módosítása: Jelölje ki a szabályt, majd **szerkesszen**. Mezők módosítása, feltételek hozzáadása vagy eltávolítása, illetve kivételek hozzáadása vagy eltávolítása.
   - **Szabály** inaktiválása: Válassza ki a szabályt, majd **inaktiválja** az egyezési szabály megtartásához, miközben kizárja azt az egyeztetési folyamatból.
   - **Szabály** megkettőzése: Jelölje ki a szabályt, majd **duplikáljon** egy hasonló szabály módosításokkal való létrehozásához.
   - **Szabály** törlése: Jelölje ki a szabályt, majd a Törlés **lehetőséget**.

1. Válassza a Tovább gombot az egyesített mezők módosításához, vagy válassza a Mentés és bezárás **lehetőséget**, és térjen vissza az Egyesítési beállítások frissítése **lapra**.[...](#update-the-unification-settings)

## <a name="manage-unified-fields"></a>Egyesített mezők kezelése

1. Válassza a Szerkesztés **lehetőséget** az **Egyesített ügyfélmezők** csempén.

    :::image type="content" source="media/m3_merge_edit.png" alt-text="Képernyőkép az egyesített ügyfélmezőkről":::

1. Tekintse át a kombinált és a kizárt mezőket, és szükség szerint végezze el a módosításokat. Adja hozzá vagy szerkessze az Ügyfél-azonosító kulcsot, vagy csoportosítsa a profilokat fürtökbe. További információ: [Ügyfélmezők](merge-entities.md) egyesítése.

1. Válassza a Tovább **lehetőséget** az egyesítési beállítások áttekintéséhez, valamint [az egyesített profil és függőségek](#run-updates-to-the-unified-customer-profile) frissítéséhez, vagy válassza a Mentés és bezárás **lehetőséget**, és térjen vissza az Egyesítési beállítások [frissítése lapra](#update-the-unification-settings) további módosításokhoz.

## <a name="run-matching-conditions"></a>Egyezési feltételek futtatása

Az egyező feltételek futtatása csak a deduplikációt és az egyezési szabályokat futtatja, és frissíti a *Deduplication_* és a *ConflationMatchPair* entitásokat.

1. Az Adatok egyesítése **lapon válassza a** > **Csak** egyező feltételek futtatása lehetőséget **.**

   A **Duplikált rekordok** és **az Egyező feltételek** csempék a Várólista **vagy** a **Frissítés állapotot jelenítik meg**.

   [!INCLUDE [progress-details-pane-include](includes/progress-details-pane.md)]

1. Amikor az egyezési folyamat befejeződött, válassza a Szerkesztés **lehetőséget** az **Egyező feltételek** csempén.

   :::image type="content" source="media/match-KPIs.png" alt-text="Körülvágott képernyőkép a legfontosabb mutatókról a Egyezés oldalon, számokkal és részletekkel.":::

1. A módosítások elvégzéséhez lásd: [Deduplikációs szabályok](#manage-deduplication-rules) kezelése vagy [Egyezési szabályok](#manage-match-rules) kezelése.

1. Futtassa újra az egyeztetési folyamatot, vagy [futtassa az ügyfélprofil](#run-updates-to-the-unified-customer-profile) frissítéseit.

## <a name="run-updates-to-the-unified-customer-profile"></a>Az egyesített ügyfélprofil frissítéseinek futtatása

1. Az Adatok **egyesítése** > **lapon válassza a** következőt:

   - **Ügyfélprofilok** egyesítése: Egyező feltételeket futtat, és a függőségek (például bővítések, szegmensek vagy mértékek) befolyásolása nélkül frissíti az egyesített ügyfélprofil-entitást. A függő folyamatok nem futnak, hanem a frissítési ütemezésben [meghatározottak szerint](system.md#schedule-tab) frissülnek.

   - **Ügyfélprofilok és függőségek** egyesítése: Egyező feltételeket futtat, és frissíti az egyesített profilt és az összes függőséget. Minden folyamat automatikusan újrafuttatható. Az összes lefelé irányuló folyamat befejezése után az ügyfélprofil tükrözi a frissített adatokat.

   A **Rekordok duplikálása**, **az Egyező feltételek** és **az Egyesített ügyfél mezők** csempéi várólistán **vagy** frissítésen **alapuló állapotot mutatnak**.

   [!INCLUDE [progress-details-pane-include](includes/progress-details-pane.md)]

A sikeres futtatás eredményei megjelennek az **Egységesítés** oldalon, amely az egyesített ügyfélprofilok számát mutatja.
