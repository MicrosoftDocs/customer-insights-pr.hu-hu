---
title: Az adategyesítés feltételeinek egyeztetése
description: Entitások egyeztetése az egyesített ügyfélprofilok létrehozásához.
recommendations: false
ms.date: 10/07/2022
ms.subservice: audience-insights
ms.topic: tutorial
author: v-wendysmith
ms.author: mukeshpo
ms.reviewer: v-wendysmith
manager: shellyha
searchScope:
- ci-match
- ci-merge
- ci-map
- customerInsights
ms.openlocfilehash: bbd2c5f441b85460250c11f02358ea67260278d6
ms.sourcegitcommit: 52ea58c872b10f1e6f9d120be93df93cca1a12dd
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/26/2022
ms.locfileid: "9721524"
---
# <a name="match-conditions-for-data-unification"></a>Az adategyesítés feltételeinek egyeztetése

Ez az egységesítési lépés határozza meg az entitások közötti egyezés sorrendjét és szabályait. Ehhez a lépéshez legalább két entitásra van szükség.

> [!NOTE]
> Miután létrehozta az egyezési feltételeket, és kiválasztotta a Tovább **lehetőséget**, nem távolíthatja el a kiválasztott entitást vagy attribútumot. Ha szükséges, válassza a Vissza **lehetőséget** a kiválasztott entitások és attribútumok áttekintéséhez a folytatás előtt.

[!INCLUDE [m3-first-run-note](includes/m3-first-run-note.md)]

## <a name="include-enriched-entities-preview"></a>Bővített entitások belefoglalása (előzetes verzió)

Ha az egyesítési eredmények javítása érdekében adatforrás szinten bővítette az entitásokat, jelölje ki őket. További információ: [Adatforrások gazdagítása](data-sources-enrichment.md). Ha bővített entitásokat jelölt ki a **Rekordok** megkettőzése lapon, nem kell újra kijelölnie őket.

1. Az **Egyező feltételek** lapon válassza **a Bővített entitások** használata lehetőséget az oldal tetején.

1. **A Bővített entitások használata panelen válasszon ki egy vagy több bővített entitást**.

1. Válassza a **Kész** lehetőséget.

## <a name="specify-the-match-order"></a>Egyeztetési sorrend megadása

Mindegyik egyezés két vagy több entitást egyesül egyetlen, összesített entitásban. Ugyanakkor megőrzi az egyéni ügyfélrekordokat is. Az egyezési sorrend azt a sorrendet jelzi, amelyben a rendszer megpróbálja egyeztetni a rekordokat.

> [!IMPORTANT]
> Az első entitást elsődleges entitásnak nevezzük, amely az egyesített profilok alapjául szolgál. A kiválasztott további entitások hozzá lesznek adva ehhez az entitáshoz.
>
> Fontos szempontok:
>
> - Válassza ki azt az entitást, amely a legteljesebb és legmegbízhatóbb profiladatokkal rendelkezik az ügyfelekről elsődleges entitásként.
> - Válassza ki azt az entitást, amely több attribútummal rendelkezik más entitásokkal (például név, telefonszám vagy e-mail-cím) elsődleges entitásként.

1. Az **Egyező feltételek** lapon a felfelé és lefelé mutató nyilakkal mozgassa az entitásokat a kívánt sorrendben, vagy húzza át őket. Válassza például az eCommerceCustomers lehetőséget **elsődleges entitásként, a** loyCustomers **pedig** a második entitást.

1. Ha azt szeretné, hogy az entitás minden rekordja egyedi vevőként legyen, függetlenül attól, hogy talál-e egyezést, válassza az Összes rekord **belefoglalása lehetőséget**. Az entitás minden olyan rekordja, amely nem egyezik meg más entitás rekordjaival, szerepel az egyesített profilban. Azokat a rekordokat, amelyeknek nincs egyezése, singletonoknak nevezzük.
  
A Contacts:eCommerce *elsődleges entitás* megfeleltetve lesz a következő CustomerLoyalty:Loyalty *entitásnak*. Az első egyezési lépésből származó adatkészletet a rendszer a következő entitással egyezteti, ha kettőnél több entitással rendelkezik.

:::image type="content" source="media/m3_match.png" alt-text="Képernyőkép az entitások kiválasztott egyezési sorrendjéről." lightbox="media/m3_match.png":::

## <a name="define-rules-for-match-pairs"></a>Egyezéspárok szabályainak meghatározása

Az egyeztetési szabályok adják meg az entitások meghatározott párjának egyeztetését. Egy szabály egy vagy több feltételből áll.

Az entitás neve melletti figyelmeztetés azt jelenti, hogy nincs megadva egyezési szabály az egyezési párhoz.

1. Válassza a Szabály **hozzáadása egy entitáspárhoz lehetőséget** az egyezési szabályok meghatározásához.

1. **A Szabály** hozzáadása panelen konfigurálja a szabály feltételeit.

   :::image type="content" source="media/m3_add_rule.png" alt-text="Képernyőkép a Szabály hozzáadása panelről.":::

   - **Entitás/mező kiválasztása (első sor)**: Válasszon ki egy entitást és egy attribútumot, amely valószínűleg egyedi az ügyfél számára. Például egy telefonszám vagy egy e-mail-cím. Kerülje az tevékenységtípus-attribútumok egyeztetését. A vásárlási azonosító például valószínűleg nem talál egyezést más rekordtípusban.

   - **Entitás/mező kiválasztása (második sor)**: Válasszon ki egy attribútumot, amely az első sorban megadott entitás attribútumához kapcsolódik.

   - **Normalizálás**: Válasszon a következő normalizálási lehetőségek közül a kijelölt attribútumok esetén.
     - **Számok**: Más számrendszereket (például római számokat) arab számokká alakít át. A *VIII* számból *8* lesz.
     - **Szimbólumok**: Eltávolítja az összes szimbólumot és speciális karaktert. A *Head&Shoulder* kifejezésből *HeadShoulder* lesz.
     - **Szöveg kisbetűssé: Az összes karaktert kisbetűssé** alakítja. Az *ALL CAPS and Title Case* kifejezés *all caps and title case* lesz.
     - **Típus (telefon, név, cím, szervezet):** Szabványosítja a neveket, címeket, telefonszámokat, címeket és szervezeteket.
     - **Unicode – ASCII: A Unicode-jelölést ASCII-karakterekké** alakítja át. A */u00B2* jelölésből *2* lesz.
     - **Szóköz**: Eltávolítja az összes szóközt. A *Hello   World* kifejezésből *HelloWorld* lesz.

   - **Pontosság**: Az adott feltételre alkalmazandó pontossági szint beállítása.
     - **Alapszintű**: Válasszon az Alacsony (30%),*a* Közepes (60%), *a Magas (80%) és* a Pontos (100%)*·* *lehetőségek közül.* Válassza a Pontos **lehetőséget, ha csak a** 100 százaléknak megfelelő rekordokat szeretné egyeztetni.
     - **Egyéni**: Állítsa be, hogy a rekordoknak hány százalékban kell egyezniük. A rendszer csak az ezt a küszöbértéket meghaladó rekordokat egyezteti.

   - **Név**: A szabály neve.

1. Ha csak akkor szeretné egyeztetni az entitásokat, ha az attribútumok több feltételnek is megfelelnek, válassza a Feltétel **hozzáadása** > **lehetőséget**, ha további feltételeket szeretne hozzáadni egy egyezési szabályhoz. A feltételek logikai ÉS operátorral kapcsolódnak, és ezért csak akkor hajtódnak végre, ha minden feltétel teljesül.

1. Ha szükséges, fontolja meg a speciális beállításokat, például a kivételeket [vagy](#add-exceptions-to-a-rule) az [egyéni egyezési feltételeket](#specify-custom-match-conditions).

1. Válassza a Kész **lehetőséget** a szabály véglegesítéséhez.

1. Tetszés szerint [további szabályokat is felvehet](#add-rules-to-a-match-pair).

1. Kattintson a **Tovább** gombra.

> [!div class="nextstepaction"]
> [Következő lépés: Mezők egyesítése](merge-entities.md)

### <a name="add-rules-to-a-match-pair"></a>Szabályok hozzáadása egyezéspárhoz

Az egyezési szabályok feltételek egy csoportját jelentik. Ha több attribútumon alapuló feltételek szerint szeretné egyeztetni az entitásokat, adjon hozzá további szabályokat.

1. Válassza a **Szabály** hozzáadása lehetőséget ahhoz az entitáshoz, amelyhez szabályokat szeretne hozzáadni.

1. Kövesse az [Egyezéspárok szabályainak meghatározása](#define-rules-for-match-pairs) részben látható lépéseket.

> [!NOTE]
> A szabályok sorrendje számít. Az egyeztetési algoritmus az első szabály alapján próbál megfeleltetni egy adott ügyfélrekordot, és csak akkor folytatja a második szabályt, ha az első szabállyal nem azonosítottak egyezést.

## <a name="advanced-options"></a>Speciális beállítások

### <a name="add-exceptions-to-a-rule"></a>Kivételek hozzáadása szabályhoz

A legtöbb esetben az entitásegyeztetés egyedi ügyfélprofilokhoz vezet konszolidált adatokkal. A hamis pozitív és hamis negatív ritka esetek kezeléséhez határozzon meg kivételeket az egyezési szabályhoz. A kivételek az egyezési szabályok feldolgozása után kerülnek alkalmazásra, és elkerülik az összes olyan rekord egyeztetését, amely megfelel a kivételfeltételeknek.

Ha például az egyezési szabály a vezetéknév, a várost és a születési dátumot kombinálja, a rendszer azonosítja az azonos vezetéknév rendelkező ikreket, akik ugyanabban a városban élnek, mint ugyanaz a profil. Megadhat egy kivételt, amely nem felel meg a profiloknak, ha az egyesített entitások utónév nem azonosak.

1. A Szabály **szerkesztése panelen válassza a** Kivétel hozzáadása **lehetőséget** > **·**.

1. Adja meg a kivételfeltételeket.

1. A szabály mentéséhez válassza a **Kész** gombot.

### <a name="specify-custom-match-conditions"></a>Egyéni egyezés feltételeinek megadása

Adja meg azokat a feltételeket, amelyek felülbírálják az alapértelmezett egyezési logikát. Négy lehetőség áll rendelkezésre:

|Beállítás  |Description |Példa  |
|---------|---------|---------|
|Mindig egyezik     | Meghatározza a mindig egyező elsődleges kulcsok értékeit.         |  Az 12345-ös *elsődleges kulccsal rendelkező sort mindig egyeztesse az 54321-es elsődleges kulccsal* *rendelkező sorral*.       |
|Soha nem egyezik     | Meghatározza az elsődleges kulcsok értékeit, amelyek soha nem egyeznek.        | Soha ne egyeztesse az 12345-ös *elsődleges kulccsal rendelkező sort az 54321-es* elsődleges kulccsal *rendelkező* sorral.        |
|Megkerülés            | Meghatározza azokat az értékeket, amelyeket a rendszernek mindig figyelmen kívül kell hagynia az egyezési fázisban. |  Hagyja figyelmen kívül a 11111 *és* az Ismeretlen *értékeket* az egyezés során.        |
|Aliasleképezés    | Olyan értékek meghatározása, amelyeket a rendszernek azonos értéknek kell tekintenie.         | Tekintsd *Joe-t* egyenlőnek *Josephfel*.        |

1. **Egyedi** kiválasztása.

   :::image type="content" source="media/m3_match_custom.png" alt-text="Egyéni gomb":::

1. Válassza az Egyéni típust **, majd válassza a** Sablon **letöltése lehetőséget**. Nevezze át a sablont szóközök használata nélkül. Használjon külön sablont minden egyezési lehetőséghez.

1. Nyissa meg a letöltött sablonfájlt, és töltse ki a részleteket. A sablon mezőket tartalmaz, amelyek meghatározzák az entitást és az egyéni egyeztetésben használandó entitás elsődleges kulcsértékeit. Az entitásnevek megkülönböztetik a kis- és nagybetűket. Ha például azt szeretné, hogy az *Értékesítés* entitás *12345* elsődleges kulcsa mindig megegyezzen a *Kapcsolattartó* entitás *34567* elsődleges kulcsával, töltse ki a sablont:
   - Entity1: Értékesítés
   - Entity1Key: 12345
   - Entity2: Kapcsolattartó
   - Entity2Key: 34567

   Ugyanezzel a sablonfájllal megadhat több entitásból származó egyéni egyeztetési rekordokat is.

   > [!NOTE]
   > Ha a deduplikáláshoz egyéni egyeztetést kíván megadni egy entitáson, akkor ugyanazt az entitást kell megadnia, mint az Entity1 és az Entity2, és állítson be különböző elsődleges kulcsértékeket. Az egyéni egyeztetés használatához legalább egy deduplikációs szabályt meg kell határoznia az entitáshoz.

1. Az összes felülbírálás hozzáadása után mentse a sablonfájlt.

1. Nyissa meg az **Adatok** > **Adatforrások** pontot, és töltse fel a sablonfájlokat új entitásként.

1. A fájlok feltöltése után válassza ismét az **Egyéni** lehetőséget. Válassza ki a szükséges entitásokat a legördülő menüből, majd válassza a Kész **lehetőséget**.

   :::image type="content" source="media/custom-match-overrides.png" alt-text="Képernyőkép a párbeszédablakról az egyéni egyezés esetének felülbírálása esetén.":::

1. Az egyéni egyezés alkalmazása a használni kívánt egyezési beállítástól függ.

   - A **Mindig egyezzen vagy** a Soha ne egyezzen **lehetőséget**, folytassa a következő lépéssel.
   - A Megkerülés vagy aliasleképezés **beállításnál** válassza a Szerkesztés **meglévő egyezési szabályon lehetőséget**, vagy **hozzon létre egy új szabályt.** A Normalizálások legördülő menüben válassza az Egyéni megkerülés **vagy** az Alias leképezés **lehetőséget, majd válassza a** Kész **lehetőséget**.

1. Válassza a Kész **lehetőséget** az Egyéni **panelen az** egyéni egyezési konfiguráció alkalmazásához.

   Minden betöltött sablonfájl saját adatforrás. Ha olyan rekordokat fedez fel, amelyek különleges egyező kezelést igényelnek, frissítse a megfelelő adatforrás. A frissítés a következő egyesítési folyamat során lesz használva. Például azonosíthatja a közel azonos nevű ikreket, akik ugyanazon a címen élnek, és amelyeket egy személyként egyesítettek. Frissítse a adatforrás, hogy az ikreket különálló, egyedi rekordokként azonosítsa.

> [!div class="nextstepaction"]
> [Következő lépés: Mezők egyesítése](merge-entities.md)

[!INCLUDE [footer-include](includes/footer-banner.md)]
