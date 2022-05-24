---
title: Entitások egyeztetése az adategyesítéshez
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
ms.openlocfilehash: bc470dd932c2c981adc5840bb52d60f8dfe0de61
ms.sourcegitcommit: 6a5f4312a2bb808c40830863f26620daf65b921d
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/11/2022
ms.locfileid: "8740952"
---
# <a name="match-conditions"></a>Feltételek egyeztetése

[!INCLUDE [m3-prod-trial-note](includes/m3-prod-trial-note.md)]

Az egyesítés ezen lépése határozza meg az egyezési sorrendet és az entitások közötti egyeztetés szabályait. Ehhez a lépéshez legalább két entitásra van szükség.

> [!NOTE]
> Miután létrehozta az egyezési feltételeket, és a Tovább **lehetőséget választotta**, nem távolíthat el egy kijelölt entitást vagy attribútumot. Ha szükséges, a folytatás előtt válassza a Vissza **lehetőséget** a kijelölt entitások és attribútumok áttekintéséhez.

## <a name="include-enriched-entities-preview"></a>Gazdagított entitások belefoglalása (előzetes verzió)

Ha az egyesítési eredmények javítása érdekében adatforrás szinten gazdagította az entitásokat, válassza ki őket. További információt az adatforrások gazdagítása című témakörben [talál](data-sources-enrichment.md). Ha gazdagított entitásokat jelölt ki az **Ismétlődő rekordok** lapon, nem kell újra kijelölnie őket.

1. Az Egyező feltételek **lapon válassza** a **lap tetején található Gazdagított entitások** használata lehetőséget.

1. **A Gazdagított entitások** használata ablaktáblán válasszon ki egy vagy több gazdagított entitást.

1. Válassza a **Kész** lehetőséget.

## <a name="specify-the-match-order"></a>Egyeztetési sorrend megadása

Mindegyik egyezés két vagy több entitást egyesül egyetlen, összesített entitásban. Ugyanakkor megőrzi az egyéni ügyfélrekordokat is. Az egyezési sorrend azt a sorrendet jelzi, amelyben a rendszer megpróbálja egyeztetni a rekordokat.

> [!IMPORTANT]
> A lista első entitását elsődleges entitásnak nevezzük. Az elsődleges entitás az egységes profilok adatkészletének alapja. A kijelölt további entitások hozzáadódnak ehhez az entitáshoz.
>
> Fontos szempontok:
>
> - Válassza ki azt az entitást, amely elsődleges entitásként a legteljesebb és legmegbízhatóbb profiladatokat tartalmazza az ügyfelekről.
> - Elsődleges entitásként válassza ki azt az entitást, amely több attribútummal rendelkezik más entitásokkal (például névvel, telefonszámmal vagy e-mail címmel).

1. **Az Egyező feltételek** lapon a felfelé és lefelé mutató nyilakkal mozgassa az entitásokat a kívánt sorrendben, vagy húzza és dobja el őket. Válassza **például a Névjegyek:e-kereskedelem** lehetőséget elsődleges entitásként, a **CustomerLoyalty:Loyalty** lehetőséget pedig második entitásként.

1. Ha azt szeretné, hogy az entitás minden rekordja egyedi vevőként legyen, függetlenül attól, hogy talál-e egyezést, jelölje be az Összes bejegyzés **belefoglalása lehetőséget**. Az entitás bármely olyan bejegyzése, amely nem egyezik meg más entitások bejegyzéseivel, szerepel az egyesített profilban. Azokat a rekordokat, amelyek nem rendelkeznek egyezéssel, singletonoknak nevezzük.
  
Az elsődleges entitás *Contacts:eCommerce* egyezik a következő ügyfélloyalty:hűség *entitással*. Az első egyezési lépésből származó adatkészlet a következő entitással van párosítva, ha kettőnél több entitással rendelkezik.

:::image type="content" source="media/m3_match.png" alt-text="Képernyőkép az entitások kijelölt egyezési sorrendjéről." lightbox="media/m3_match.png":::

## <a name="define-rules-for-match-pairs"></a>Egyezéspárok szabályainak meghatározása

Az egyeztetési szabályok adják meg az entitások meghatározott párjának egyeztetését. A szabály egy vagy több feltételből áll.

Az entitásnév melletti figyelmeztetés azt jelenti, hogy egyezési párhoz nincs megadva egyezési szabály.

1. Válassza **a Szabály hozzáadása lehetőséget** egy entitáspárhoz az egyezési szabályok meghatározásához.

1. **A Szabály** hozzáadása ablaktáblán konfigurálja a szabály feltételeit.

   :::image type="content" source="media/m3_add_rule.png" alt-text="Képernyőkép: Szabály hozzáadása ablaktábla.":::

   - **Entitás/mező (első sor):** Válasszon ki egy kapcsolódó entitást és egy attribútumot egy olyan rekordtulajdonság megadásához, amely valószínűleg egyedi a vevőre nézve. Például egy telefonszám vagy egy e-mail-cím. Kerülje az tevékenységtípus-attribútumok egyeztetését. A vásárlási azonosító például valószínűleg nem talál egyezést más rekordtípusban.

   - **Entitás/mező (második sor)**: Válasszon olyan attribútumot, amely az első sorban megadott entitás attribútumához kapcsolódik.

   - **Normalizálás**: Válasszon a következő normalizálási lehetőségek közül a kijelölt attribútumok esetén.
     - **Számok**: Más számrendszereket, például római számokat arab számokká alakít át. A *VIII* számból *8* lesz.
     - **Szimbólumok**: Eltávolítja az összes szimbólumot és speciális karaktert. A *Head&Shoulder* kifejezésből *HeadShoulder* lesz.
     - **Szöveg kisbetűvé**: Az összes karaktert kisbetűvé alakítja. Az *ALL CAPS and Title Case* kifejezés *all caps and title case* lesz.
     - **Típus (Telefon, Név, Cím, Szervezet)**: Szabványosítja a neveket, címeket, telefonszámokat, címeket és szervezeteket.
     - **Unicode-ból ASCII-re**: A unicode jelölést ASCII karakterekké alakítja. A */u00B2* jelölésből *2* lesz.
     - **Szóköz**: Eltávolítja az összes szóközt. A *Hello   World* kifejezésből *HelloWorld* lesz.

   - **Pontosság**: Az adott feltételre alkalmazandó pontossági szint beállítása.
     - **Alap**: Válasszon az alacsony (30%)*,* a közepes (60%)*,* a magas (80%)*és* a pontos (100%)*közül*. Válassza az Pontos **lehetőséget**, ha csak a 100 százalékosnak megfelelő rekordoknak felel meg.
     - **Egyéni**: Állítsa be, hogy a rekordoknak hány százalékban kell egyezniük. A rendszer csak az ezt a küszöbértéket meghaladó rekordokat egyezteti.

   - **Név**: A szabály neve.

1. Ha csak akkor szeretne entitásokat egyeztetni, ha az attribútumok több feltételnek is megfelelnek, válassza a Feltétel **hozzáadása** > **lehetőséget**, ha további feltételeket szeretne hozzáadni egy egyezési szabályhoz. A feltételek logikai ÉS operátorral kapcsolódnak, és ezért csak akkor hajtódnak végre, ha minden feltétel teljesül.

1. Szükség esetén fontolja meg a speciális beállításokat, például [a kivételeket](#add-exceptions-to-a-rule) vagy [az egyéni egyeztetési feltételeket](#specify-custom-match-conditions).

1. A szabály véglegesítéséhez válassza a Kész **lehetőséget**.

1. Tetszés szerint [további szabályokat is felvehet](#add-rules-to-a-match-pair).

1. Kattintson a **Tovább** gombra.

> [!div class="nextstepaction"]
> [Következő lépés: Mezők egyesítése](merge-entities.md)

### <a name="add-rules-to-a-match-pair"></a>Szabályok hozzáadása egyezéspárhoz

Az egyezési szabályok feltételek egy csoportját jelentik. Ha az entitásokat több attribútumon alapuló feltételek szerint szeretné egyeztetni, adjon hozzá további szabályokat.

1. Válassza a Szabály hozzáadása lehetőséget **azon** entitáson, amelyhez szabályokat kíván hozzáadni.

1. Kövesse az [Egyezéspárok szabályainak meghatározása](#define-rules-for-match-pairs) részben látható lépéseket.

> [!NOTE]
> A szabályok sorrendje számít. Az egyező algoritmus az első szabály alapján próbál egyeztetni egy adott ügyfélrekorddal, és csak akkor folytatja a második szabályt, ha az első szabállyal nem azonosítottak egyezést.

## <a name="advanced-options"></a>Speciális beállítások

### <a name="add-exceptions-to-a-rule"></a>Kivételek hozzáadása szabályhoz

A legtöbb esetben az entitásegyeztetés egyedi ügyfélprofilokhoz vezet konszolidált adatokkal. A hamis pozitív és hamis negatívok ritka eseteinek dinamikus kezeléséhez kivételeket határozhat meg egyezési szabályhoz. A kivételek az egyezési szabályok feldolgozása után kerülnek alkalmazásra, és elkerülik az összes olyan rekord egyeztetését, amely megfelel a kivételfeltételeknek.

Ha például a mérkőzésszabály vezetéknév, várost és születési dátumot kombinál, a rendszer azonosítja azokat az ikreket, akik ugyanazzal a vezetéknév, akik ugyanabban a városban élnek, mint ugyanaz a profil. Megadhat olyan kivételt, amely nem egyezik meg a profilokkal, ha az egyesített entitások utónév nem azonosak.

1. A Szabály szerkesztése ablaktáblán válassza a **Hozzáadás kivétel lehetőséget** **.** > **·**

1. Adja meg a kivételi feltételeket.

1. A szabály mentéséhez válassza a **Kész** gombot.

### <a name="specify-custom-match-conditions"></a>Egyéni egyezés feltételeinek megadása

Megadhat olyan feltételeket, amelyek felülírják az alapértelmezett egyezési logikát. Négy lehetőség áll rendelkezésre:

|Beállítás  |Description |Példa  |
|---------|---------|---------|
|Mindig egyezik     | Olyan értékeket határoz meg, amelyek mindig egyeznek.         |  Mindig egyeznek *Mike-kal* és *MikeR-ral*.       |
|Soha nem egyezik     | Olyan értékeket határoz meg, amelyek soha nem egyeznek meg.        | Soha ne egyezzen *Johnnal* és *Jonathannal*.        |
|Egyéni megkerülő     | Olyan értékeket határoz meg, amelyeket a rendszernek mindig figyelmen kívül kell hagynia az egyezési fázisban. |  Hagyja figyelmen kívül az 11111 *és* az Ismeretlen *értékeket* a mérkőzés során.        |
|Aliasleképezés    | Olyan értékek meghatározása, amelyeket a rendszernek azonos értéknek kell tekintenie.         | Tekintsd Úgy *, hogy Joe* egyenlő *Józseffel*.        |

1. **Egyedi** kiválasztása.

   :::image type="content" source="media/m3_match_custom.png" alt-text="Egyéni gomb":::

1. Válassza ki az **Egyéni típust,** és válassza a Sablon letöltése **lehetőséget**. Minden egyeztetési lehetőséghez külön sablonra van szükség.

1. Nyissa meg a letöltött sablonfájlt, és töltse ki a részleteket. A sablon mezőket tartalmaz, amelyek meghatározzák az entitást és az egyéni egyeztetésben használandó entitás elsődleges kulcsértékeit. Ha például azt szeretné, hogy az *Értékesítés* entitás *12345* elsődleges kulcsa mindig megegyezzen a *Kapcsolattartó* entitás *34567* elsődleges kulcsával, töltse ki a sablont:
    - Entity1: Értékesítés
    - Entity1Key: 12345
    - Entity2: Kapcsolattartó
    - Entity2Key: 34567

   Ugyanezzel a sablonfájllal megadhat több entitásból származó egyéni egyeztetési rekordokat is.

   Ha a deduplikáláshoz egyéni egyeztetést kíván megadni egy entitáson, akkor ugyanazt az entitást kell megadnia, mint az Entity1 és az Entity2, és állítson be különböző elsődleges kulcsértékeket.

1. Az összes felülbírálás hozzáadása után mentse a sablonfájlt.

1. Nyissa meg az **Adatok** > **Adatforrások** pontot, és töltse fel a sablonfájlokat új entitásként.

1. A fájlok feltöltése után válassza újra az **Egyéni** lehetőséget. Válassza ki a szükséges entitásokat a legördülő menüből, és válassza a Kész **lehetőséget**.

   :::image type="content" source="media/custom-match-overrides.png" alt-text="Képernyőkép a párbeszédablakról az egyéni egyezés esetének felülbírálása esetén.":::

1. Az egyéni egyezés alkalmazása a használni kívánt egyezési beállítástól függ.

   - A **Mindig egyezés** vagy **a Soha ne egyezés** esetén folytassa a következő lépéssel.
   - A Megkerülés **vagy az Alias-hozzárendelés beállításnál** **válassza a Szerkesztés** lehetőséget **egy meglévő egyezési szabályon, vagy hozzon létre egy új** szabályt. A Normalizációk legördülő listában válassza az Egyéni bypass vagy aliasleképezés **lehetőséget, és válassza a** Kész lehetőséget.**·** **·**

1. Az egyéni egyezési konfiguráció alkalmazásához válassza **az** Egyéni **ablaktáblán a Kész** lehetőséget.

> [!div class="nextstepaction"]
> [Következő lépés: Mezők egyesítése](merge-entities.md)

[!INCLUDE [footer-include](includes/footer-banner.md)]
