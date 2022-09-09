---
title: Ügyfél-, fiók- vagy kapcsolategyesítési beállítások frissítése
description: Frissítse az ismétlődő szabályokat, az egyeztetési szabályokat vagy az egyesített mezőket az ügyfél- vagy fiókegyesítési beállításokban.
ms.date: 08/26/2022
ms.subservice: audience-insights
ms.topic: tutorial
author: Scott-Stabbert
ms.author: sstabbert
ms.reviewer: v-wendysmith
manager: shellyha
searchScope:
- ci-match
- ci-merge
- ci-relationships
- customerInsights
ms.openlocfilehash: e893e66fd7691b9703d51ed8f87cfad63880cc3b
ms.sourcegitcommit: 560c4ee16376a9c6fdd7860988ce2d2440194fa5
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/01/2022
ms.locfileid: "9392474"
---
# <a name="update-unification-settings"></a>Az egyesítési beállítások frissítése

Ha az egységesített profil létrehozása után át szeretné tekinteni vagy módosítani szeretné az egyesítési beállításokat, hajtsa végre a következő lépéseket.

1. Lépjen az Adatok **egyesítése oldalra** > **·**.

   Az egyes ügyfelek (B-től C-ig) esetében az **Egyesítés** oldal az egységesített ügyfélprofilok és csempék számát jeleníti meg az egyes egyesítési lépésekhez.

   :::image type="content" source="media/m3_unified.png" alt-text="Képernyőkép az Adatok egyesítése lapról az adatok egyesítése után." lightbox="media/m3_unified.png":::

   Üzleti fiókok (B-től B-ig) esetén az **Egységesítés** oldal az egyesített fiókprofilok és csempék számát jeleníti meg az egyes fiókegyesítési lépésekhez. Ha a névjegyek egységesek voltak, megjelenik az egyesített kapcsolattartói profilok és csempék száma az egyes kapcsolategyesítési lépésekhez. Válassza ki a megfelelő csempét a Fiókok **egyesítése vagy** a Partnerek egyesítése (előzetes verzió) **alatt** attól függően, hogy mit szeretne frissíteni.

   :::image type="content" source="media/b2b_unified.png" alt-text="Képernyőkép az Adatok egyesítése lapról a fiók- és kapcsolattartási adatok egységesítése után." lightbox="media/b2b_unified.png":::

   > [!TIP]
   > Az **Egyezési feltételek** csempe csak akkor jelenik meg, ha több entitás lett kiválasztva.

1. Válassza ki, hogy mit szeretne frissíteni:
   - [Forrásmezők](#edit-source-fields) attribútumok vagy entitások hozzáadásához vagy attribútumtípusok módosításához. Attribútum eltávolításához lásd: [Egyesített mező](#remove-a-unified-field) eltávolítása. Entitás eltávolításához lásd: [Egyesített entitás](#remove-a-unified-entity) eltávolítása.
   - [Duplikált rekordok](#manage-deduplication-rules) a deduplikációs szabályok kezeléséhez vagy a beállítások egyesítéséhez.
   - [Egyező feltételek](#manage-match-rules) két vagy több entitás egyező szabályainak frissítéséhez.
   - [Egyesített vevői mezők](#manage-unified-fields) a mezők egyesítéséhez vagy kizárásához. A kapcsolódó profilokat fürtökbe is csoportosíthatja.
   - [Szemantikai mezők](#manage-semantic-fields-for-unified-contacts) az egyesített kapcsolattartó mezők szemantikai típusainak kezeléséhez.
   - [kapcsolatok](#manage-contact-and-account-relationships) a kapcsolattartó és a partner közötti kapcsolat kezeléséhez.

1. A módosítások elvégzése után válassza ki a következő lehetőséget:

   - [Az egyező feltételek](#run-matching-conditions) futtatásával gyorsan kiértékelheti az egyező feltételek (deduplikáció és egyeztetési szabályok) minőségét az egységes profil frissítése nélkül. Az **Egyezési feltételek** csak futtatása beállítás nem jelenik meg egyetlen entitásnál.
   - [Egyesítse a profilokat](#run-updates-to-the-unified-profile) az egyező feltételek futtatásához, és frissítse az egységes profil entitást anélkül, hogy ez hatással lenne a függőségekre (például gazdagításokra, szegmensekre vagy mértékekre). A függő folyamatok nem futnak, hanem a frissítési ütemezésben [meghatározottak szerint](schedule-refresh.md) frissülnek.
   - [Egyesítse a profilokat és a függőségeket](#run-updates-to-the-unified-profile) az egyező feltételek futtatásához, frissítse az egyesített profil entitást, és frissítse az összes függőséget (például gazdagításokat, szegmenseket vagy mértékeket). Minden folyamat automatikusan újrafuttatható. A B-től B-ig az egyesítés az egyesített profilokat frissítő partner- és kapcsolattartó entitásokon is fut.

## <a name="edit-source-fields"></a>Forrásmezők szerkesztése

1. Válassza a Szerkesztés **lehetőséget** a **Forrásmezők** csempén.

   :::image type="content" source="media/m3_source_edit.png" alt-text="Képernyőkép: a Forrásmezők oldal az elsődleges kulcsok, a leképezett és a nem leképezett mezők számát mutatja":::

   Megjelenik a leképezett és a leképezés nélküli mezők száma.

1. Más attribútumok vagy entitások hozzáadásához válassza az Entitások és mezők **kiválasztása lehetőséget**.

1. Igény szerint módosíthatja az entitás elsődleges kulcsát, az attribútumtípusokat, és be- vagy kikapcsolhatja **az Intelligens leképezés** beállítást. További információ: [Forrásmezők](map-entities.md) kiválasztása.

1. Válassza a Tovább gombot a deduplikációs szabályok módosításához, vagy válassza a Mentés lehetőséget **, zárja be**, majd térjen vissza az Egyesítési beállítások frissítése **lapra**.[...](#update-unification-settings)

### <a name="remove-a-unified-field"></a>Egyesített mező eltávolítása

Egy egységesített mező eltávolításához a mezőt el kell távolítani minden függőségből, például szegmensekből, mértékekből, gazdagításokból vagy kapcsolatok.

1. Miután eltávolította a mező összes függőségét, lépjen az Adatok **egyesítése** > **lapra**.

1. Válassza a Szerkesztés **lehetőséget** az **Egyesített ügyfélmezők** csempén.

1. Jelölje ki a mező összes előfordulását, majd válassza a Kizárás **lehetőséget**.

   :::image type="content" source="media/m3_remove_attribute1.png" alt-text="Képernyőkép az Egyesített mezők lapról, amelyen a kijelölt mezők és a Kizárás gomb látható":::

1. Válassza a Kész **lehetőséget** a megerősítéshez, majd válassza a Mentés és bezárás **lehetőséget**.

   > [!TIP]
   > Ha a "Nem sikerült menteni az egyesítést" üzenet jelenik meg. A megadott erőforrás nem módosítható vagy törölhető az alsóbb rétegbeli függőségek miatt", majd a mező továbbra is egy lefelé irányuló függőségben van használva.

1. Ha a mezőt ismétlődő rekordokhoz vagy egyező feltételekhez használja egy szabályban, hajtsa végre a következő lépéseket. Ellenkező esetben folytassa a következő lépéssel.
   1. Válassza a Szerkesztés **lehetőséget** a **Rekordok** megkettőzése csempén.
   1. Távolítsa el a mezőt az összes szabályból, amelyben használják, ha van ilyen, majd válassza a Tovább **lehetőséget**.
   1. **Az Egyező feltételek** lapon távolítsa el a mezőt az összes szabályból, amelyben használják, ha vannak ilyenek, majd válassza a Mentés és bezárás **lehetőséget**.
   1. Válassza az Ügyfélprofilok és -függőségek egyesítése **lehetőséget** > **·**. Várja meg, amíg az egyesítés befejeződik, mielőtt továbblépne a következő lépésre.

1. Válassza a Szerkesztés **lehetőséget** a **Forrásmezők** csempén.

1. Válassza az Entitások és mezők **kiválasztása lehetőséget**, és törölje a jelet a mező minden előfordulása melletti jelölőnégyzetből.

   :::image type="content" source="media/m3_remove_attribute2.png" alt-text="Képernyőkép az Entitások és mezők kiválasztása párbeszédpanelről, amelyen a jelölőnégyzetek törlése látható":::

1. Válassza az **Alkalmaz** lehetőséget.

1. Válassza a **Mentés és bezárás** lehetőséget.

1. Válassza az Ügyfélprofilok és függőségek **egyesítése** > **lehetőséget** az egyesített profil frissítéséhez.

### <a name="remove-a-unified-entity"></a>Egyesített entitás eltávolítása

Az egyesített entitás eltávolításához az entitást el kell távolítani minden függőségből, például szegmensekből, mértékekből, gazdagodásokból vagy kapcsolatok.

1. Miután eltávolította az entitás összes függőségét, lépjen az Adatok **egyesítése** > **lapra**.

1. Válassza a Szerkesztés **lehetőséget** az **Egyesített ügyfélmezők** csempén.

1. Jelölje ki az entitás összes mezőjét, majd válassza a Kizárás **lehetőséget**.

   :::image type="content" source="media/m3_remove_entity1.png" alt-text="Képernyőkép az Egyesített mezőkről, amelyeken egy entitás összes mezője ki van választva, és a Kizárás gomb":::

1. Válassza a Kész **lehetőséget** a megerősítéshez, majd válassza a Mentés és bezárás **lehetőséget**.

   > [!TIP]
   > Ha a "Nem sikerült menteni az egyesítést" üzenet jelenik meg. A megadott erőforrás nem módosítható vagy törölhető az alsóbb rétegbeli függőségek miatt", majd az entitás továbbra is egy lefelé irányuló függőségben van használva.

1. Válassza a Szerkesztés **lehetőséget** a **Rekordok** megkettőzése csempén.

1. Távolítsa el az összes szabályt az entitásból, ha van ilyen, majd válassza a Tovább **lehetőséget**.

1. **Az Egyezési feltételek** lapon válassza ki az entitást, majd válassza a Törlés **lehetőséget**.

   :::image type="content" source="media/m3_remove_entity2.png" alt-text="Képernyőkép: Egyezési feltételek, amelyeken az entitás ki van választva, és a Törlés gomb":::

1. Válassza a **Mentés és bezárás** lehetőséget.

1. Válassza a Szerkesztés **lehetőséget** a **Forrásmezők** csempén.

1. Válassza az Entitások és mezők **kiválasztása lehetőséget**, és törölje a jelet az entitás melletti jelölőnégyzetből.

   :::image type="content" source="media/m3_remove_entity3.png" alt-text="Képernyőkép az Entitások és mezők kiválasztása párbeszédpanelről, amelyen az entitás jelölőnégyzete törölve van":::

1. Válassza az **Alkalmaz** lehetőséget.

1. Válassza a **Mentés és bezárás** lehetőséget.

1. Válassza az Ügyfélprofilok és függőségek **egyesítése** > **lehetőséget** az egyesített profil frissítéséhez.

## <a name="manage-deduplication-rules"></a>Deduplikációs szabályok kezelése

1. Válassza a Szerkesztés **lehetőséget** a **Rekordok** megkettőzése csempén.

   :::image type="content" source="media/m3_duplicates_edit.png" alt-text="Képernyőkép a Duplikált rekordok oldaláról, amelyen a duplikált rekordok száma látható" lightbox="media/m3_duplicates_edit.png":::

   A talált duplikált rekordok száma a Duplikátumok **alatt** jelenik meg. A **Rekordok deduplikált** oszlopban látható, hogy mely entitások rendelkeztek duplikált rekordokkal, és hogy hány százalékban voltak duplikált rekordok.

1. Bővített entitás használatához válassza a Bővített entitások **használata lehetőséget**. További információ: [Adatforrások](data-sources-enrichment.md) gazdagítása.

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

   1. Válassza a **Kész** lehetőséget.

1. Válassza a Tovább gombot az egyező feltételek módosításához, vagy válassza a Mentés és bezárás **lehetőséget**, és térjen vissza az Egyesítési beállítások frissítése **lapra**.[...](#update-unification-settings)

## <a name="manage-match-rules"></a>Egyezési szabályok kezelése

Az egyezési paraméterek nagy része konfigurálható és finomhangolható. Nem adhat hozzá és nem törölhet entitásokat. Az egyezési szabályok nem vonatkoznak egyetlen entitásra.

1. Válassza a Szerkesztés **lehetőséget** az **Egyező feltételek** csempén.

   :::image type="content" source="media/m3_match_edit.png" alt-text="Képernyőkép a Szabályok és feltételek egyeztetése lapról statisztikákkal." lightbox="media/m3_match_edit.png":::

   Az oldal megjeleníti az egyezési sorrendet és a meghatározott szabályokat, valamint a következő statisztikákat:
   - **Az egyedi forrásrekordok** a legutóbbi egyezési futtatás során feldolgozott egyes forrásrekordok számát mutatják.
   - **Az egyező és nem egyező rekordok** kiemelik, hogy hány egyedi rekord maradt az egyezési szabályok feldolgozása után.
   - **Az egyező rekordok csak** az összes páros egyezéseinek számát mutatják.

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

1. Válassza a Tovább gombot az egyesített mezők módosításához, vagy válassza a Mentés és bezárás **lehetőséget**, és térjen vissza az Egyesítési beállítások frissítése **lapra**.[...](#update-unification-settings)

## <a name="manage-unified-fields"></a>Egyesített mezők kezelése

1. Válassza a Szerkesztés **lehetőséget** az **Egyesített ügyfélmezők** csempén.

    :::image type="content" source="media/m3_merge_edit.png" alt-text="Képernyőkép az egyesített ügyfélmezőkről":::

1. Tekintse át a kombinált és a kizárt mezőket, és szükség szerint végezze el a módosításokat. Adja hozzá vagy szerkessze az Ügyfél-azonosító kulcsot, vagy csoportosítsa a profilokat fürtökbe. További információ: [Ügyfélmezők](merge-entities.md) egyesítése.

1. Ügyfelek vagy fiókok esetén válassza a Tovább **lehetőséget** az egyesített profil és [a függőségek](#run-updates-to-the-unified-profile) áttekintéséhez és frissítéséhez. Vagy válassza a Mentés és bezárás **lehetőséget**, és térjen vissza az [Egyesítési beállítások](#update-unification-settings) frissítése elemre a további módosítások elvégzéséhez.

   Kapcsolattartók esetén válassza a Tovább **lehetőséget** a szemantikai mezők kezeléséhez. Vagy válassza a Mentés és bezárás **lehetőséget**, és térjen vissza az [Egyesítési beállítások](#update-unification-settings) frissítése elemre a további módosítások elvégzéséhez.

## <a name="manage-semantic-fields-for-unified-contacts"></a>Egységes kapcsolattartók szemantikai mezőinek kezelése

1. Válassza a Szerkesztés **lehetőséget** a **Szemantikus mezők** csempén.

1. Egy egyesített mező szemantikai típusának módosításához válasszon egy új típust. További információ: [Az egyesített kapcsolattartók](data-unification-contacts.md#define-the-semantic-fields-for-unified-contacts) szemantikai mezőinek meghatározása.

1. Válassza a Tovább **lehetőséget** a fiók- és kapcsolat kezeléséhez, vagy válassza a Mentés és bezárás **lehetőséget**, és térjen vissza az Egyesítési beállítások [frissítése lapra](#update-unification-settings) további módosítások elvégzéséhez.

## <a name="manage-contact-and-account-relationships"></a>Kapcsolattartók és fiók-kapcsolatok kezelése

1. Válassza a Szerkesztés **lehetőséget** a **kapcsolatok** csempén.

1. A kapcsolat és a partner kapcsolatának módosításához módosítsa az alábbi adatok bármelyikét:

   - **Idegen kulcs a kapcsolattartó entitástól**: Válassza ki azt az attribútumot, amely összeköti a kapcsolattartót a partnerrel.
   - **Számlaentitáshoz**: Válassza ki a kapcsolattartóhoz társított fiókentitást.

1. Válassza a Tovább **lehetőséget** az egyesítési beállítások áttekintéséhez és [az egyesített profil és függőségek](#run-updates-to-the-unified-profile) frissítéséhez, vagy válassza a Mentés és bezárás **lehetőséget**, és térjen vissza az [Egyesítési beállítások](#update-unification-settings) frissítése elemre további módosítások elvégzéséhez.

## <a name="run-matching-conditions"></a>Egyezési feltételek futtatása

Az egyező feltételek futtatása csak a deduplikációt és az egyezési szabályokat futtatja, és frissíti a *Deduplication_* és a *ConflationMatchPair* entitásokat.

1. Az Adatok egyesítése **lapon válassza a** > **Csak** egyező feltételek futtatása lehetőséget **.**

   A **Duplikált rekordok** és **az Egyező feltételek** csempék a Várólista **vagy** a **Frissítés állapotot jelenítik meg**.

   [!INCLUDE [progress-details-pane-include](includes/progress-details-pane.md)]

1. Amikor az egyezési folyamat befejeződött, válassza a Szerkesztés **lehetőséget** az **Egyező feltételek** csempén.

   :::image type="content" source="media/match-KPIs.png" alt-text="Körülvágott képernyőkép a legfontosabb mutatókról a Egyezés oldalon, számokkal és részletekkel.":::

1. A módosítások elvégzéséhez lásd: [Deduplikációs szabályok](#manage-deduplication-rules) kezelése vagy [Egyezési szabályok kezelése](#manage-match-rules).

1. Futtassa újra az egyeztetési folyamatot, vagy [futtassa a profil](#run-updates-to-the-unified-profile) frissítéseit.

## <a name="run-updates-to-the-unified-profile"></a>Frissítések futtatása az egyesített profilhoz

- Ha egyező feltételeket szeretne futtatni, és a függőségek (például ügyfélkártyák, gazdagítások, szegmensek vagy mértékek) befolyásolása nélkül *szeretné frissíteni az egységesített profilt, és frissíteni szeretné az egységesített profil entitást*, válassza az Ügyfélprofilok **egyesítése lehetőséget**. Fiókok esetén válassza a Fiókok egyesítése profilok **egyesítése lehetőséget.** > **·** Partnerek esetén válassza a Névjegyek egyesítése (előzetes verzió) **Profilok** > **egyesítése lehetőséget**. A függő folyamatok nem futnak, hanem a frissítési ütemezésben [meghatározottak szerint](schedule-refresh.md) frissülnek.
- Az egyező feltételek futtatásához frissítse az egyesített profilt, és futtassa az összes függőséget, válassza az Ügyfélprofilok és -függőségek **egyesítése lehetőséget**. Minden folyamat automatikusan újrafuttatható. Partnerek és kapcsolattartók esetén válassza a Fiókok **egyesítése profilok és függőségek** > **egyesítése lehetőséget**. Az egyező feltételek mind a partnerek, mind a kapcsolattartók számára futnak, akik az egyesített profilokat és az összes többi függőséget is frissítik.

A Forrás mezők kivételével **minden csempe várólistán** vagy **Frissítésen** jelenik meg **.**

[!INCLUDE [progress-details-pane-include](includes/progress-details-pane.md)]

A sikeres futtatás eredményei megjelennek az Egységesítés **oldalon,** amely az egyesített profilok számát mutatja.
