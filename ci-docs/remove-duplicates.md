---
title: Duplikátumok eltávolítása az adatok egyesítése előtt
description: Az egyesítési folyamat második lépése annak kiválasztása, hogy melyik rekordot kell megőrizni, amikor ismétlődéseket talál.
recommendations: false
ms.date: 04/22/2022
ms.subservice: audience-insights
ms.topic: tutorial
author: v-wendysmith
ms.author: mukeshpo
ms.reviewer: v-wendysmith
manager: shellyha
searchScope:
- ci-map
- ci-match
- customerInsights
ms.openlocfilehash: 27dff3551ab411a12c273536d7431d651c48573e
ms.sourcegitcommit: 6a5f4312a2bb808c40830863f26620daf65b921d
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/11/2022
ms.locfileid: "8742945"
---
# <a name="remove-duplicates-before-unifying-data"></a>Duplikátumok eltávolítása az adatok egyesítése előtt

[!INCLUDE [m3-prod-trial-note](includes/m3-prod-trial-note.md)]

Az egyesítés ezen lépése opcionálisan lehetővé teszi az entitáson belüli ismétlődő bejegyzések kezelésére vonatkozó szabályok beállítását. *A deduplikáció* azonosítja az ismétlődő rekordokat, és egyetlen rekordba egyesíti őket. A forrásrekordokat a rendszer összekapcsolja az egyesített rekordokat alternatív azonosítókkal. Ha a szabályok nincsenek konfigurálva, a rendszer által definiált szabályokat alkalmaz.

## <a name="include-enriched-entities-preview"></a>Gazdagított entitások belefoglalása (előzetes verzió)

Ha az egyesítési eredmények javítása érdekében adatforrás szinten gazdagította az entitásokat, válassza ki őket. További információt az adatforrások gazdagítása című témakörben [talál](data-sources-enrichment.md).

1. A Rekordok **másolása lapon válassza** a **lap tetején található Gazdag entitások** használata lehetőséget.

1. **A Gazdagított entitások** használata ablaktáblán válasszon ki egy vagy több gazdagított entitást.

1. Válassza a **Kész** lehetőséget.

## <a name="define-deduplication-rules"></a>Deduplikációs szabályok meghatározása

1. **A Rekordok** másolása lapon jelöljön ki egy entitást, és válassza a Szabály **hozzáadása lehetőséget** a deduplikációs szabályok meghatározásához.

   :::image type="content" source="media/m3_duplicates_showmore.png" alt-text="Képernyőkép: Ismétlődő rekordok oldalai, amelyeken a Továbbiak megjelenítése kiemelve van":::

   1. **A Szabály** hozzáadása ablaktáblán adja meg a következő adatokat:
      - **Mező** kiválasztása: Válasszon az ismétlődéseket ellenőrizni kívánt entitás elérhető mezői közül. Válassza ki a mezőket, amelyek valószínűleg egyediek minden egyes ügyfélnél. Például egy e-mail-cím, vagy a név, a város és a telefonszám kombinációja.
      - **Normalizálás**: Válasszon a következő normalizálási lehetőségek közül a kijelölt attribútumok esetén.
        - **Számok**: Más számrendszereket, például római számokat arab számokká alakít át. A *VIII* számból *8* lesz.
        - **Szimbólumok**: Eltávolítja az összes szimbólumot és speciális karaktert. A *Head&Shoulder* kifejezésből *HeadShoulder* lesz.
        - **Szöveg kisbetűvé: Az összes karaktert kisbetűvé** alakítja. Az *ALL CAPS and Title Case* kifejezés *all caps and title case* lesz.
        - **Típus (Telefon, Név, Cím, Szervezet)**: Szabványosítja a neveket, címeket, telefonszámokat, címeket, címeket stb.
        - **Unicode-ból ASCII-re**: A unicode jelölést ASCII karakterekké alakítja. A */u00B2* jelölésből *2* lesz.
        - **Szóköz**: Eltávolítja az összes szóközt. A *Hello   World* kifejezésből *HelloWorld* lesz.
      - **Pontosság**: Az adott feltételre alkalmazandó pontossági szint beállítása.
        - **Alap**: Válasszon az alacsony (30%)*,* a közepes (60%)*,* a magas (80%)*és* a pontos (100%)*közül*. Válassza az Pontos **lehetőséget**, ha csak a 100 százalékosnak megfelelő rekordoknak felel meg.
        - **Egyéni**: Állítsa be, hogy a rekordoknak hány százalékban kell egyezniük. A rendszer csak az ezt a küszöbértéket meghaladó rekordokat egyezteti.
      - **Név**: A szabály neve.

      :::image type="content" source="media/m3_duplicates_add.png" alt-text="Képernyőkép: Szabály hozzáadása ablaktábla az ismétlődések eltávolításához.":::

   1. Ha további feltételeket szeretne hozzáadni a szabályhoz, válassza a Feltétel **hozzáadása** > **lehetőséget**. A feltételek logikai ÉS operátorral kapcsolódnak, és ezért csak akkor hajtódnak végre, ha minden feltétel teljesül.

   1. **A kivétel hozzáadása** > **kivétel hozzáadásához** is hozzáadhat [kivételeket a szabályhoz](match-entities.md#add-exceptions-to-a-rule). A kivételeket a hamis pozitív és hamis negatívok ritka eseteinek kezelésére használják.

   1. A szabály létrehozásához válassza a Kész **lehetőséget**.

1. Tetszés szerint [további szabályokat is felvehet](#define-deduplication-rules).

1. Jelöljön ki egy entitást, majd **szerkessze az egyesítési beállításokat**.

1. **A Beállítások** egyesítése ablaktáblán:
   1. Válasszon egyet a három lehetőség közül, hogy meghatározza, melyik rekordot kell megőriznie, ha duplikátumot talál:
      - **Legtöbbet kitöltött**: A nyertes rekordként a legtöbb kitöltött attribútummezővel rendelkező rekordot adja meg. Ez az alapértelmezett egyesítési beállítás.
      - **Legújabb**: A nyertes rekordot az időbeli frissesség alapján adja meg. Az időbeli frissesség definiálásához dátum vagy numerikus mező szükséges.
      - **Legrégebbi**: A nyertes rekord a legkevésbé friss rekord lesz. Az időbeli frissesség definiálásához dátum vagy numerikus mező szükséges.
      
      Döntetlen esetén a győztes rekord a MAX(PK) vagy a nagyobb elsődleges kulcsértékkel rendelkező rekord.
      
   1. Ha egy entitás egyes attribútumain egyesítési beállításokat szeretne definiálni, válassza **az ablaktábla alján található Speciális** lehetőséget. Például dönthet úgy, hogy megtartja a legutóbbi e-mail címet és a legteljesebb címet a különböző rekordokból. Bontsa ki az entitást az összes attribútum megtekintéséhez, és határozza meg, hogy melyik beállítást használja az egyes attribútumokhoz. Ha a recency-alapú beállítást választja, meg kell adnia egy dátum/idő mezőt is, amely meghatározza a pontosságot.

      :::image type="content" source="media/m3_adv_merge.png" alt-text="Speciális egyesítési beállítások ablaktábla, amely a legutóbbi e-maileket és a teljes címet mutatja":::

   1. Az egyesítési beállítások alkalmazásához válassza a Kész **lehetőséget**.

1. A deduplikációs szabályok és az egyesítési beállítások megadása után válassza a Tovább **lehetőséget**.
  
> [!div class="nextstepaction"]
> [Következő lépés egyetlen entitáshoz: Mezők egyesítése](merge-entities.md)

> [!div class="nextstepaction"]
> [Következő lépés több entitás esetében: Egyeztetési feltételek](match-entities.md)

## <a name="deduplication-output-as-an-entity"></a>Deduplikáció kimenete entitásként

A deduplikációs folyamat minden forrástűrőhöz létrehoz egy új deduplikált entitást. Ezek az entitások az **Entitások** lap **Rendszer** szakaszában a **ConflationMatchPairs:CustomerInsights** elemmel együtt találhatók meg **Deduplication_DataSource_Entity** névvel.

A deduplikált kimeneti entitás a következő információkat tartalmazza:

- Azonosítók / kulcsok
  - Elsődleges kulcs és Alternatív azonosító mezők. Az alternatív azonosító mező a rekordhoz azonosított összes másodlagos azonosítóból áll.
  - Deduplication_GroupId mező mutatja az entitáson belül azonosított csoportot vagy fürtöt, amely a hasonló bejegyzéseket a megadott deduplikáció mezők alapján csoportosítja. Ezt a rendszerfeldolgozási célokra használják. Ha nincsenek megadva manuális deduplikációs szabályok, és a rendszer által definiált deduplikációs szabályok vonatkoznak, akkor előfordulhat, hogy ez a mező nem található meg a deduplikálás kimeneti entitásban.
  - Deduplication_WinnerId: Ez a mező tartalmazza az azonosított csoportokból vagy fürtökből a nyertes azonosítót. Ha a Deduplication_WinnerId megegyezik egy rekord elsődleges kulcsával, ez azt jelenti, hogy az a rekord lesz a győztes rekord.
- A deduplikációs szabályok definiáló mezői.
- Szabály és Pontszám mezők, amelyekben a deduplikációs szabályok alkalmazva lettek és az egyeztető algoritmus által visszaadott pontszám is megegyezik.

[!INCLUDE[footer-include](includes/footer-banner.md)]
