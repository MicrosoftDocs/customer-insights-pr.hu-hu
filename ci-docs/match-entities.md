---
title: Az adategyesítés egyezési feltételei
description: Entitások egyeztetése az egyesített ügyfélprofilok létrehozásához.
recommendations: false
ms.date: 05/05/2022
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
ms.openlocfilehash: 770a18f3a7471714a7e044ae034da168a2601010
ms.sourcegitcommit: dca46afb9e23ba87a0ff59a1776c1d139e209a32
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/29/2022
ms.locfileid: "9082407"
---
# <a name="match-conditions-for-data-unification"></a>Az adategyesítés egyezési feltételei

[!INCLUDE [m3-prod-trial-note](includes/m3-prod-trial-note.md)]

Az egyesítés ezen lépése határozza meg az egyezési sorrendet és az entitások közötti egyeztetés szabályait. Ehhez a lépéshez legalább két entitásra van szükség.

> [!NOTE]
> Miután létrehozta az egyezési feltételeket, és a Tovább **lehetőséget választotta**, nem távolíthat el egy kiválasztott entitást vagy attribútumot. Ha szükséges, válassza a Vissza **lehetőséget** a kiválasztott entitások és attribútumok áttekintéséhez a folytatás előtt.

## <a name="include-enriched-entities-preview"></a>Bővített entitások belefoglalása (előzetes verzió)

Ha a adatforrás szinten bővítette az entitásokat az egyesítési eredmények javítása érdekében, válassza ki őket. További információ: [Adatforrások gazdagítása](data-sources-enrichment.md). Ha bővített entitásokat választott ki a **Rekordok megkettőzése** lapon, nem kell újra kijelölnie őket.

1. Az Egyezési feltételek **lapon válassza a** Bővített entitások **használata lehetőséget** az oldal tetején.

1. **A Bővített entitások** használata panelen válasszon ki egy vagy több bővített entitást.

1. Válassza a **Kész** lehetőséget.

## <a name="specify-the-match-order"></a>Egyeztetési sorrend megadása

Mindegyik egyezés két vagy több entitást egyesül egyetlen, összesített entitásban. Ugyanakkor megőrzi az egyéni ügyfélrekordokat is. Az egyezési sorrend azt a sorrendet jelzi, amelyben a rendszer megpróbálja egyeztetni a rekordokat.

> [!IMPORTANT]
> A lista első entitását elsődleges entitásnak nevezzük. Az elsődleges entitás szolgál az egyesített profilok adatkészletének alapjául. A kiválasztott további entitások hozzáadódnak ehhez az entitáshoz.
>
> Fontos szempontok:
>
> - Elsődleges entitásként válassza ki azt az entitást, amely a legteljesebb és legmegbízhatóbb profiladatokat tartalmazza az ügyfelekről.
> - Elsődleges entitásként azt az entitást válassza ki, amely több, más entitásokkal közös attribútummal (például névvel, telefonszámmal vagy e-mail-címmel) rendelkezik.

1. Az Egyező feltételek **lapon a** felfelé és lefelé mutató nyilakkal mozgassa az entitásokat a kívánt sorrendben, vagy húzza át őket. Válassza például a **Contacts:eCommerce** lehetőséget elsődleges entitásként, és **a CustomerLoyalty:Loyalty-t** második entitásként.

1. Ha azt szeretné, hogy az entitás minden rekordja egyedi ügyfél legyen, függetlenül attól, hogy talál-e egyezést, válassza az Összes rekord **belefoglalása lehetőséget**. Az entitás minden olyan rekordja, amely nem egyezik meg más entitások rekordjaival, szerepel az egyesített profilban. Azokat a rekordokat, amelyeknek nincs egyezésük, singletonoknak nevezzük.
  
A Contacts:eCommerce elsődleges entitás *megegyezik a következő CustomerLoyalty:Loyalty* entitással *.* Az első egyezési lépésből származó adatkészlet a következő entitással lesz párosítva, ha kettőnél több entitással rendelkezik.

:::image type="content" source="media/m3_match.png" alt-text="Képernyőkép az entitások kiválasztott egyezési sorrendjéről." lightbox="media/m3_match.png":::

## <a name="define-rules-for-match-pairs"></a>Egyezéspárok szabályainak meghatározása

Az egyeztetési szabályok adják meg az entitások meghatározott párjának egyeztetését. Egy szabály egy vagy több feltételből áll.

Az entitásnév melletti figyelmeztetés azt jelenti, hogy egyezőpárhoz nincs megadva egyezési szabály.

1. Válassza a Szabály **hozzáadása entitáspárhoz lehetőséget** az egyezési szabályok meghatározásához.

1. **A Szabály** hozzáadása panelen konfigurálja a szabály feltételeit.

   :::image type="content" source="media/m3_add_rule.png" alt-text="Képernyőkép: a Szabály hozzáadása panel.":::

   - **Entitás/mező (első sor)**: Válasszon ki egy kapcsolódó entitást és egy attribútumot egy olyan rekordtulajdonság megadásához, amely valószínűleg egyedi a vevő számára. Például egy telefonszám vagy egy e-mail-cím. Kerülje az tevékenységtípus-attribútumok egyeztetését. A vásárlási azonosító például valószínűleg nem talál egyezést más rekordtípusban.

   - **Entitás/mező (második sor)**: Válasszon ki egy olyan attribútumot, amely az első sorban megadott entitás attribútumához kapcsolódik.

   - **Normalizálás**: Válasszon a következő normalizálási lehetőségek közül a kijelölt attribútumok esetén.
     - **Számok**: Más számrendszereket,például római számokat arab számokká alakít át. A *VIII* számból *8* lesz.
     - **Szimbólumok**: Eltávolítja az összes szimbólumot és speciális karaktert. A *Head&Shoulder* kifejezésből *HeadShoulder* lesz.
     - **Szöveg kisbetűsre**: Az összes karaktert kisbetűsre konvertálja. Az *ALL CAPS and Title Case* kifejezés *all caps and title case* lesz.
     - **Típus (telefon, név, cím, szervezet)**: Szabványosítja a neveket, címeket, telefonszámokat, címeket és szervezeteket.
     - **Unicode-ból ASCII-be**: A Unicode-jelöléseket ASCII-karakterekké alakítja. A */u00B2* jelölésből *2* lesz.
     - **Szóköz**: Eltávolítja az összes szóközt. A *Hello   World* kifejezésből *HelloWorld* lesz.

   - **Pontosság**: Az adott feltételre alkalmazandó pontossági szint beállítása.
     - **Alapszintű**: Válasszon az Alacsony (30%)*,* a Közepes (60%)*, a* Magas (80%)*és* az Egzakt (100%) közül *·*. Válassza a Pontos **lehetőséget**, ha csak a 100%-nak megfelelő rekordokat szeretné egyeztetni.
     - **Egyéni**: Állítsa be, hogy a rekordoknak hány százalékban kell egyezniük. A rendszer csak az ezt a küszöbértéket meghaladó rekordokat egyezteti.

   - **Név**: A szabály neve.

1. Ha csak akkor szeretné egyeztetni az entitásokat, ha az attribútumok több feltételnek is megfelelnek, válassza a Feltétel **hozzáadása** > **lehetőséget**, ha további feltételeket szeretne hozzáadni egy egyező szabályhoz. A feltételek logikai ÉS operátorral kapcsolódnak, és ezért csak akkor hajtódnak végre, ha minden feltétel teljesül.

1. Ha szükséges, fontolja meg a speciális beállításokat, például [a kivételeket](#add-exceptions-to-a-rule) vagy [az egyéni egyezési feltételeket](#specify-custom-match-conditions).

1. Válassza a Kész **lehetőséget** a szabály véglegesítéséhez.

1. Tetszés szerint [további szabályokat is felvehet](#add-rules-to-a-match-pair).

1. Kattintson a **Tovább** gombra.

> [!div class="nextstepaction"]
> [Következő lépés: Mezők egyesítése](merge-entities.md)

### <a name="add-rules-to-a-match-pair"></a>Szabályok hozzáadása egyezéspárhoz

Az egyezési szabályok feltételek egy csoportját jelentik. Ha az entitásokat több attribútumon alapuló feltételek szerint szeretné egyeztetni, adjon hozzá további szabályokat.

1. Válassza a Szabály **hozzáadása lehetőséget** ahhoz az entitáshoz, amelyhez szabályokat szeretne hozzáadni.

1. Kövesse az [Egyezéspárok szabályainak meghatározása](#define-rules-for-match-pairs) részben látható lépéseket.

> [!NOTE]
> A szabályok sorrendje számít. Az egyező algoritmus az első szabály alapján megpróbál egyeztetni egy adott ügyfélrekorddal, és csak akkor folytatja a második szabályt, ha nem azonosítottak egyezést az első szabállyal.

## <a name="advanced-options"></a>Speciális beállítások

### <a name="add-exceptions-to-a-rule"></a>Kivételek hozzáadása egy szabályhoz

A legtöbb esetben az entitásegyeztetés egyedi ügyfélprofilokhoz vezet, konszolidált adatokkal. A hamis pozitív és hamis negatívok ritka eseteinek dinamikus kezeléséhez kivételeket határozhat meg egy egyező szabályhoz. A kivételeket a rendszer az egyezési szabályok feldolgozása után alkalmazza, és elkerüli az összes olyan rekord egyeztetését, amely megfelel a kivételi feltételeknek.

Ha például az egyezési szabály vezetéknév, a várost és a születési dátumot kombinálja, a rendszer azonosítja azokat az ikereket, akiknek ugyanaz a vezetéknév, akik ugyanabban a városban élnek, mint az azonos profil. Megadhat olyan kivételt, amely nem egyezik meg a profilokkal, ha a kombinált entitások utónév nem azonosak.

1. A Szabály **szerkesztése panelen válassza a** Kivétel hozzáadása **lehetőséget** > **·**.

1. Adja meg a kivételfeltételeket.

1. A szabály mentéséhez válassza a **Kész** gombot.

### <a name="specify-custom-match-conditions"></a>Egyéni egyezés feltételeinek megadása

Megadhat olyan feltételeket, amelyek felülbírálják az alapértelmezett egyezési logikát. Négy lehetőség áll rendelkezésre:

|Beállítás  |Description |Példa  |
|---------|---------|---------|
|Mindig egyezik     | Meghatározza a mindig egyező értékeket.         |  Mindig egyezzen Mike-tal *és* *MikeR-rel*.       |
|Soha nem egyezik     | Olyan értékeket határoz meg, amelyek soha nem egyeznek meg.        | Soha ne egyezzen meg *Johnnal* és *Jonathannal*.        |
|Egyéni megkerülő     | Meghatározza azokat az értékeket, amelyeket a rendszernek mindig figyelmen kívül kell hagynia az egyeztetési fázisban. |  Hagyja figyelmen kívül a 11111 *és* az Ismeretlen *értékeket* az egyeztetés során.        |
|Aliasleképezés    | Olyan értékek meghatározása, amelyeket a rendszernek azonos értéknek kell tekintenie.         | Gondold úgy *, hogy Joe* egyenlő *Josephfel*.        |

1. **Egyedi** kiválasztása.

   :::image type="content" source="media/m3_match_custom.png" alt-text="Egyéni gomb":::

1. Válassza az **Egyéni típust,** majd a Sablon **letöltése lehetőséget**. Minden egyes egyeztetési lehetőséghez külön sablonra van szükség.

1. Nyissa meg a letöltött sablonfájlt, és töltse ki a részleteket. A sablon mezőket tartalmaz, amelyek meghatározzák az entitást és az egyéni egyeztetésben használandó entitás elsődleges kulcsértékeit. Ha például azt szeretné, hogy az *Értékesítés* entitás *12345* elsődleges kulcsa mindig megegyezzen a *Kapcsolattartó* entitás *34567* elsődleges kulcsával, töltse ki a sablont:
    - Entity1: Értékesítés
    - Entity1Key: 12345
    - Entity2: Kapcsolattartó
    - Entity2Key: 34567

   Ugyanezzel a sablonfájllal megadhat több entitásból származó egyéni egyeztetési rekordokat is.

   Ha a deduplikáláshoz egyéni egyeztetést kíván megadni egy entitáson, akkor ugyanazt az entitást kell megadnia, mint az Entity1 és az Entity2, és állítson be különböző elsődleges kulcsértékeket.

1. Az összes felülbírálás hozzáadása után mentse a sablonfájlt.

1. Nyissa meg az **Adatok** > **Adatforrások** pontot, és töltse fel a sablonfájlokat új entitásként.

1. A fájlok feltöltése után válassza ismét az **Egyéni** lehetőséget. Válassza ki a szükséges entitásokat a legördülő menüből, majd válassza a Kész **lehetőséget**.

   :::image type="content" source="media/custom-match-overrides.png" alt-text="Képernyőkép a párbeszédablakról az egyéni egyezés esetének felülbírálása esetén.":::

1. Az egyéni egyezés alkalmazása a használni kívánt egyezési lehetőségtől függ.

   - A **Mindig egyezz** vagy **a Soha ne egyezzek** beállításnál folytassa a következő lépéssel.
   - A Megkerülés **vagy az Alias-leképezés beállításnál** **válassza a Szerkesztés** egy meglévő egyezési szabályon lehetőséget **, vagy hozzon létre egy új** szabályt. A Normalizálások legördülő menüben válassza az Egyéni megkerülés **vagy** alias leképezés **lehetőséget, majd válassza a** Kész **lehetőséget**.

1. Válassza a Kész **lehetőséget** az **Egyéni** panelen az egyéni egyezés konfigurációjának alkalmazásához.

> [!div class="nextstepaction"]
> [Következő lépés: Mezők egyesítése](merge-entities.md)

[!INCLUDE [footer-include](includes/footer-banner.md)]
