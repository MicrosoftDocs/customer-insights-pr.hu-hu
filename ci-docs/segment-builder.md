---
title: Szegmensek létrehozása a szegmensépítőben
description: Hozzon létre ügyfelekből álló szegmenseket, és csoportosítsa őket különböző attribútumok alapján.
ms.date: 03/25/2022
ms.subservice: audience-insights
ms.topic: how-to
author: JimsonChalissery
ms.author: jimsonc
ms.reviewer: v-wendysmith
manager: shellyha
searchScope:
- ci-segments
- ci-segment-builder
- ci-segment-details
- customerInsights
ms.openlocfilehash: e1a9cd0e3c0347285026d937ca7d951a602e7160
ms.sourcegitcommit: b515120bebd2638f2639004422cee3cff42fbdf7
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/24/2022
ms.locfileid: "8800099"
---
# <a name="create-segments"></a>Szegmensek létrehozása

Összetett szűrőket definiálhat az egyesített ügyfélentitás és a kapcsolódó entitások körül. A feldolgozást követően minden szegmens létrehoz egy csoport olyan ügyfélrekordot, amellyel az exportálás után műveletek végezhetők. A szegmensek kezelése a **Szegmensek** oldalon történik. A szegmensépítő segítségével [új szegmenseket hozhat létre](#create-a-new-segment), illetve [gyorsszegmenseket hozhat létre](#quick-segments) az alkalmazás egyéb területeiről.

> [!TIP]
> - A gyorsszegmenseket csak az **egyes ügyfelek** környezetekben támogatja a rendszer.
> - Az **egyéni ügyfeleken** alapuló szegmensek automatikusan tartalmazzák a szegmenstagok rendelkezésre álló kapcsolattartási adatait. Az **üzleti partnerek** környezetében a szegmensek partnereken (vállalatokon vagy leányvállalatok) alapulnak. Ha egy szegmensben meg kell jelenni a kapcsolattartási adatok, használja a szegmensszerkesztő **Projekt attribútuma** funkcióját. Ügyeljen arra, hogy a kapcsolattartó adatforrásai [ szemantikailag le legyenek leképezve a ContactProfile](semantic-mappings.md#define-a-contactprofile-semantic-entity-mapping) entitásra.

## <a name="segment-builder"></a>Szegmensépítő

A következő kép a szegmensépítő különböző aspektusait szemlélteti. Egy olyan szegmenst mutat, amely az ügyfelek egy csoportját adja eredményül. Az ügyfelek adott időkeretben rendeltek termékeket és jutalmazási pontokat gyűjtöttek, vagy egy bizonyos összeget költöttek el.

:::image type="content" source="media/segment-builder-overview.png" alt-text="A szegmensszerkesztő elemei." lightbox="media/segment-builder-overview.png":::

1. A szegmens rendszerezése szabályok és alszabályok szerint. Minden szabály vagy alszabály feltételekből áll. A feltételeket logikai operátorokkal egyesítése

1. Válassza ki a szabályra vonatkozó entitások közötti [kapcsolati elérési utat](relationships.md). A kapcsolati elérési út határozza meg, hogy mely attribútumok használhatók egy feltételben.

1. Szabályok és alszabályok kezelése. Szabály pozíciójának módosítása vagy törlése.

1. Feltételek hozzáadása és a megfelelő szintű egymásba ágyazás kiépítése az alszabályokkal.

1. Halmaz-műveletek alkalmazása a csatlakoztatott szabályokra.

1. Az attribútumpanel használható entitásattribútumok hozzáadására vagy attribútumok alapján feltételek létrehozására. Az ablaktáblán a kijelölt szabály számára elérhető entitások és attribútumok listája látható a kijelölt kapcsolati útvonal alapján.

1. Attribútumon alapuló feltételek hozzáadása a meglévő szabályokhoz és alszabályokhoz, illetve új szabályhoz.

1. A változtatások visszavonása és ismétlése a szegmens létrehozása közben.

A fenti példa a szegmentációs képességet szemlélteti. Meghatároztunk egy szegmenst az olyan ügyfelek számára, akik legalább 500 dollár értékben termékeket vásároltak online, *és* érdeklődnek a szoftverfejlesztés iránt.

## <a name="create-a-new-segment"></a>Új szegmens létrehozása

Új szegmens többféleképpen is létrehozható. Ez a rész ismerteti, hogyan lehet a saját szegmenst a nulláról felépíteni. *Üres szegmenst* a meglévő entitások alapján, illetve a gépi tanulási modell *javasolt szegmensei* alapján is létrehozhat. További információ a [Szegmensek áttekintése](segments.md) részhez.

A szegmensek létrehozásakor mentheti a tervezetet. A vázlat fázisban a rendszer inaktív szegmensként ment egy szegmenst. A szegmens konfigurálás befejezése után futtassa a szegmens aktiválásához. Másik lehetőségként **Aktiválhat** egy szegmenst a **Minden szegmens** oldalról.

1. Lépjen a **Szegmensek** oldalra.

1. Válassza az **Új** > **Készítse el sajátját** lehetőséget.

1. A szegmensszerkesztő lapon szabályokat definiál, illetve alkot. A szabály egy vagy több ügyfélkört definiáló feltételből áll.

1. A Szabály1 **szakaszban válassza ki annak az** entitásnak az attribútumát, amely szerint szűrni szeretné a vevőket. Kétféleképpen választhat ki attribútumokat.
   - Nézze át a **Hozzáadás szabályhoz** ablaktáblában a rendelkezésre álló entitások és attribútumok listáját, és válassza ki a hozzáadni kívánt attribútum melletti **+** ikont. Válassza ki, hogy az attribútumot hozzá szeretné-e adni egy meglévő szabályhoz, vagy új szabály létrehozására szeretné használni.
   - Az egyező javaslatokért írja be az attribútum nevét a szabály szakaszba.

1. Adja meg a feltétel egyező értékeit operátorok kiválasztásával. Az attribútum értéke a következő négy adattípus valamelyike lehet: numerikus, karakterlánc, dátum vagy logikai. Az attribútum adattípusától függően különböző operátorok határozzák meg a feltételt. Az üzleti fiókokkal rendelkező szegmensek esetében két speciális operátor áll rendelkezésre, amelyek potenciális hierarchiákat tartalmazhatnak a felvett fiókok között. Az operátorok *gyermekét* és *szülőjét* használhatja a kapcsolódó partnerek bevonására.

1. Válassza a **Feltétel hozzáadása** lehetőséget, ha további feltételeket szeretne hozzáadni egy szabályhoz. Ha az aktuális szabály alatt szeretne szabályt létrehozni, válassza az **Alszabály hozzáadása** lehetőséget.

1. Ha egy szabály nem az *Ügyfél* entitást használja, be kell állítania a kapcsolat elérési útját. A kapcsolati elérési útja a rendszert, rendszer tájékoztatásához szükséges amely kapcsolatok érjék el az egyesített ügyfélnetitást. Válassza a **Kapcsolati útvonal beállítása** lehetőséget, ha a kijelölt entitást az ügyfélentitásra leképezi. Ha csak egy lehetséges kapcsolati útvonal van, akkor a rendszer automatikusan kiválasztja azt. A különböző kapcsolati elérési utak eltérő eredményeket adhatnak. Minden szabálynak megvan a saját kapcsolati elérési útja.

   :::image type="content" source="media/relationship-path.png" alt-text="Lehetséges kapcsolati elérési út az egyesített ügyfélentitásra leképezett entitáson alapuló szabály létrehozásakor.":::

   Például az *eCommerce_eCommercePurchases* entitás a képernyőképen négy lehetőséget kínál az *Ügyfél* entitás leképezéséhez:
   - eCommerce_eCommercePurchases > eCommerce_eCommerceContacts > Ügyfél
   - eCommerce_eCommercePurchases > Ügyfél
   - eCommerce_eCommercePurchases > eCommerce_eCommerceContacts > POS_posPurchases > Ügyfél
   - eCommerce_eCommercePurchases > eCommerce_eCommerceContacts > POS_posPurchases > loyaltyScheme_loyCustomers > Ügyfél az utolsó lehetőség kiválasztásakor a szabályfeltételekben felsorolt entitások összes attribútumát belefoglalhatjuk. Valószínűleg kevesebb találat lesz, mert az egyező ügyfélrekordnak az összes entitás részét kell képeznie. Ebben a példában az e-commerce (*eCommerce_eCommercePurchases*) elemen keresztül kell az értékesítési ponton (*POS_posPurchases*) vásárolnia az termékeket, és részt vennie a hűségprogramban (*loyaltyScheme_loyCustomers*). A második lehetőség kiválasztásakor csak az *eCommerce_eCommercePurchases* és az *Ügyfél* entitásból választhatunk attribútumokat. Ennek eredménye valószínűleg több eredményül kapott ügyfélprofil lesz.

1. Ha egy szabályban több feltétel is van, kiválaszthatja, hogy melyik logikai operátor kapcsolja össze őket.  
   - **ÉS** operátor: Minden feltételnek teljesülnie kell ahhoz, hogy a rekord szerepeljen a szegmensben. Ez a beállítás akkor a leghasznosabb, ha különböző entitások között határoz meg feltételeket.
   - **VAGY** operátor: Az egyik feltételnek teljesülnie kell ahhoz, hogy a rekord szerepeljen a szegmensben. Ez a beállítás akkor a leghasznosabb, ha különböző feltételeket ad meg ugyanahhoz az entitáshoz.

   :::image type="content" source="media/segmentation-either-condition.png" alt-text="Szabály két ÉS feltétellel.":::

   Az VAGY operátor használata esetén minden feltételnek a kapcsolati elérési útban szereplő entitáson kell alapulnia.

   - Több szabályt is létrehozhat, hogy több ügyfélrekordot-halmazt hozzon létre. A csoportok kombinálhatók, hogy tartalmazzák az üzleti esethez szükséges ügyfeleket. Új szabály létrehozásához válassza az **Szabály hozzáadása** lehetőséget. Ha a megadott kapcsolati útvonal miatt nem lehet egy szabályba bevetni az entitást, új szabályt kell létrehozni, hogy kiválassza a benne található attribútumokat.

      :::image type="content" source="media/segment-rule-grouping.png" alt-text="Vegyen fel egy új szabályt egy szegmensbe, és válassza ki a halmaz operátorát.":::

   - Válasszon egyet a készletre vonatkozó operátorok közül: **Unió**, **Metszet** vagy **Kivétel**.

      - Az **Egyesülés** egyesíti a két csoportot.
      - A **Metszet** a két csoport átfedését veszi. Csak azok az adatok maradnak az egyesített csoportban, amelyek mindkét csoportban *közösek*.
      - **Kivéve** kombinálja a két csoportot. Csak az A csoportban lévő olyan adatokat tartja meg a rendszer, amelyek *nem közösek* a B csoport adataival.

1. A szegmensek alapértelmezés szerint a definiált szűrőknek megfelelő ügyfélprofilok összes attribútumát tartalmazó kimeneti entitást hozzák létre. Ha egy szegmens nem az *Ügyfél* entitáson alapul, akkor ezekből az entitásokból további attribútumokat adhat a kimeneti entitáshoz. A **Projektattribútumok** kiválasztásával kiválaszthatja a kimeneti entitáshoz hozzáfűzni kívánt attribútumokat.

   > [!IMPORTANT]
   > Az üzleti partnereken alapuló szegmensek esetében a szegmensben szerepelnie kell egy vagy több kapcsolattartó részleteinek a *ContactProfile* entitás mindegyik partneréből, hogy a szegmens aktiválható vagy exportálható legyen a kapcsolattartási adatokat igénylő célpontok felé. A *ContactProfile* entitásról a [Szemantikai leképezés](semantic-mappings.md) című részben olvasható további információ.
   > A kapcsolattartók tervezett attribútumával rendelkező üzleti partnereken alapuló szegmensekre vonatkozó mintakimenet:
   >
   > |Azonosító  |Számla neve  |Bevétel  |Kapcsolattartó neve  | Kapcsolattartó szerepköre|
   > |---------|---------|---------|---------|---|
   > |10021     | Contoso | 100K | [Abbie Moss, Ruth Soto]  | [CEO, beszerzési vezető]

   :::image type="content" source="media/segments-project-attributes.png" alt-text="Példa a kimeneti entitáshoz hozzáadandó, az oldalpanelen kijelölt elővetített attribútumokra.":::
  
   Például: A szegmens az *Ügyfél* entitáshoz kapcsolódó, vásárlási adatokat tartalmazó entitáson alapul. A szegmens az adott évben termékeket vásároló összes spanyolországi ügyfelet keresi. Kiválaszthatja, hogy attribútumokat fűz hozzá, például az áruk árát, vagy a vásárlási dátumot a kimeneti entitásban található összes egyező ügyfélrekordhoz. Ez az információ hasznos lehet a teljes költéssel kapcsolatos szezonális korrelációk elemzéséhez.

   > [!NOTE]
   > - A **projektattribútumok** csak az olyan entitások esetén működnek, amelyek "egy-a-sokhoz" viszonyban vannak az ügyfélentitással. Egy ügyfél például több előfizetéssel is rendelkezhet.
   > - Ha a projektben használni kívánt attribútum egynél több ugrást tartalmaz az *Ügyfél* entitástól, ezt a kapcsolat határozza meg, az attribútumot az összes olyan szegmenslekérdezésben fel kell használni, amelyet most hoz létre.
   > - Ha a projektben használni kívánt attribútum csak egy ugrást tartalmaz az *Ügyfél* entitástól, ennek az attribútumnak nem kell szerepelnie az épülő szegmenslekérdezés minden szabályában.
   > - A **Vetített attribútumokat** figyelembe veszi a rendszer a beállított operátorok használatakor.

1. Válassza **a Részletek** szerkesztése lehetőséget a Cím nélküli szegmens mellett. Adja meg a szegmens nevét, és frissítse a szegmens javasolt **Kimeneti entitás neve** értéket. Adjon hozzá leírást és [címkéket](work-with-tags-columns.md#manage-tags) a szegmenshez.

   :::image type="content" source="media/segments_edit_details.png" alt-text="Részletek szerkesztése párbeszédpanel.":::

1. Válassza a **Futtatás** lehetőséget a szegmens mentéshez, aktiválásához és a szegmens feldolgozásának megkezdéséhez az összes szabály és feltétel alapján. Máskülönben inaktív szegmensként menti a rendszer.

1. A **Szegmensek** oldalra a **Vissza a szegmensekhez** elemre kattintva léphet vissza.

1. A szegmens alapértelmezés szerint dinamikus szegmensként jön létre. Ez azt jelenti, hogy a rendszerfrissítés során frissül a szegmens. Ha [le szeretné állítani az automatikus frissítést](segments.md#manage-existing-segments), válassza ki a szegmenst, majd a **Statikussá tétel** lehetőséget. A statikus szegmensek bármikor [frissíthetők manuálisan](segments.md#refresh-segments).

> [!TIP]
> - A szegmensépítő nem javasol érvényes értékeket az entitásokból a feltételek operátorainak beállításakor. Az **Adatok** > **Entitások** helyen letöltheti az entitásadatokat, és láthatja, hogy mely értékek érhetők el.
> - A dátumon alapuló feltételek válthatnak a fix dátumok és egy lebegőpontos tartomány között.
> - Ha a szegmensre több szabály is vonatkozik, akkor a szerkesztett szabály mellett egy függőleges kék vonal van.
> - A szabályokat és feltételeket a szegmensdefinícióban más helyre is áthelyezheti. Jelölje ki a függőleges ellipszis (&vellip;) egy szabály vagy feltétel mellett, és válassza ki, hogyan és hol helyezze át.
> - A **Visszavonás** és a **Visszaállítás** vezérlőelemek a parancssávban visszagördülnek a változásokhoz.
> - A szegmens létrehozása után egyes szegmensek lehetővé teszik a szegmens [használatának](segments.md#track-usage-of-a-segment) nyomon követését.

## <a name="quick-segments"></a>Gyors szegmens

A gyorsszegmensek segítségével gyorsan készíthet egyszerű, egy operátorral rendelkező szegmenseket a gyors elemzéshez.

1. A **Szegmensek** oldalon válassza az **Új** > **Létrehozás a következőből** lehetőséget.
   - Válassza a **Profilok** lehetőséget, ha az *egyesített ügyfél* entitáson alapuló szegmenset szeretne létrehozni.
   - Ha korábban létrehozott mértékekhez szeretne szegmenst létrehozni, válassza a **Mértékek** lehetőséget.
   - Válassza az **Információ** lehetőséget, ha egy szegmenst szeretne létrehozni az egyik olyan kimeneti entitás köré, amelyet vagy az **Előrejelzések** vagy az **egyéni modellek** használatával hozott létre.

2. Az **új gyors szegmens** párbeszédpanelen jelöljön ki egy attribútumot a **Mező** legördülő listában.

3. A rendszer további információkat ad, ami segít az ügyfelek jobb szegmenseinek létrehozásában.
   - A kategorikus mezők esetén 10 első számú ügyfél számít. Válasszon egy **Értéket**, és válassza a **Felülvizsgálat** elemet.
   - Numerikus attribútumok esetében a rendszer azt mutatja, hogy az egyes ügyfelek percentilis értékei alá milyen attribútumértékek tartoznak. Válasszon egy **operátort** és egy **értéket**, majd válassza a **Felülvizsgálat** lehetőséget.

4. A rendszer megadja a **Becsült szegmensméret** értékét. Kiválaszthatja, hogy létrehozza-e a megadott szegmenst, vagy először újra meg szeretné vizsgálni, hogy egy másik szegmens méretet kap-e.

   :::image type="content" source="media/quick-segment-name.png" alt-text="Gyorsszegmens neve és becslése.":::

5. **Adjon nevet** és **kimenet entitásnevet** a szegmensnek. Opcionálisan adjon hozzá [címkéket](work-with-tags-columns.md#manage-tags).

6. Válassza a **Mentés** lehetőséget a szegmens létrehozásához.

7. Miután a szegmens befejezte a feldolgozást, megtekintheti azt a létrehozott többi szegmenshez hasonlóan.

## <a name="next-steps"></a>További lépések

[Exportáljon egy szegmenst](export-destinations.md), és fedezze fel az [Ügyfélkártya integrációját](customer-card-add-in.md), hogy használhassa a szegmenseket más alkalmazásokban.

[!INCLUDE [footer-include](includes/footer-banner.md)]
