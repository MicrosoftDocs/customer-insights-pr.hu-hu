---
title: Távolítsa el az ismétlődéseket az adatok egyesítése előtt
description: Az egyesítési folyamat második lépése annak kiválasztása, hogy melyik rekordot kell megőrizni, ha duplikátumokat talál.
recommendations: false
ms.date: 08/01/2022
ms.subservice: audience-insights
ms.topic: tutorial
author: v-wendysmith
ms.author: sstabbert
ms.reviewer: v-wendysmith
manager: shellyha
searchScope:
- ci-map
- ci-match
- customerInsights
ms.openlocfilehash: 3f84c1c149f0befcbe489ccdd8a666ce6d5d798a
ms.sourcegitcommit: 267c317e10166146c9ac2c30560c479c9a005845
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/16/2022
ms.locfileid: "9304476"
---
# <a name="remove-duplicates-before-unifying-data"></a>Távolítsa el az ismétlődéseket az adatok egyesítése előtt

Az egyesítés ezen választható lépése lehetővé teszi, hogy szabályokat állítson be az entitáson belüli **ismétlődő rekordok** kiküszöbölésére. A deduplikáció több rekordot azonosít egy ügyfél számára, és kiválasztja a legjobb rekordot, amelyet meg kell őrizni (az alapvető egyesítési beállítások alapján), vagy egyesíti a rekordokat egybe (a speciális egyesítési beállítások alapján). A forrásrekordokat a rendszer összekapcsolja az egyesített rekordokat alternatív azonosítókkal. Ha a szabályok nincsenek konfigurálva, a rendszer által definiált szabályokat alkalmazza.

## <a name="default-deduplication"></a>Alapértelmezett deduplikáció

A rendszer által definiált szabályok akkor érvényesek, ha nincsenek deduplikációs szabályok hozzáadva.

- Az elsődleges kulcs deduplikált.
  Az azonos elsődleges kulccsal rendelkező rekordok esetében a **Legtöbb kitöltött** rekord (amelyik a legkevesebb null értékkel rendelkezik) a győztes.
- Az entitások közötti egyezési szabályok az entitásra vonatkoznak.
  Például: Az egyezési lépésben, ha az A entitást a FullName és a DateofBirth *B entitásával egyeztetik, akkor az A entitást a FullName* és *a DateofBirth* is deduplikálja *.* *·* Mivel *a FullName* és *a DateofBirth* érvényes kulcsok az A entitásban lévő ügyfél azonosítására, ezek a kulcsok az A entitás duplikált vevőinek azonosítására is érvényesek.

## <a name="include-enriched-entities-preview"></a>Bővített entitások belefoglalása (előzetes verzió)

Ha a adatforrás szinten bővítette az entitásokat az egyesítési eredmények javítása érdekében, válassza ki őket. További információ: [Adatforrások gazdagítása](data-sources-enrichment.md).

1. A Rekordok megkettőzése **lapon válassza a** Bővített entitások **használata lehetőséget** az oldal tetején.

1. **A Bővített entitások** használata panelen válasszon ki egy vagy több bővített entitást.

1. Válassza a **Kész** lehetőséget.

## <a name="define-deduplication-rules"></a>Deduplikációs szabályok meghatározása

1. **A Rekordok** megkettőzése lapon válasszon ki egy entitást, és válassza a Szabály **hozzáadása lehetőséget** a deduplikációs szabályok meghatározásához.

   :::image type="content" source="media/m3_duplicates_showmore.png" alt-text="Képernyőkép a Duplikált rekordok lapról, kiemelve az entitással és a Szabály hozzáadása felirattal"  lightbox="media/m3_duplicates_showmore.png":::

   1. **A Szabály** hozzáadása panelen adja meg a következő adatokat:
      - **Mező** kiválasztása: Válasszon az entitás elérhető mezőinek listájából, amelyeket ellenőrizni szeretne az ismétlődések után. Válassza ki a mezőket, amelyek valószínűleg egyediek minden egyes ügyfélnél. Például egy e-mail-cím, vagy a név, a város és a telefonszám kombinációja.
      - **Normalizálás**: Válasszon a következő normalizálási lehetőségek közül a kijelölt attribútumok esetén.
        - **Számok**: Más számrendszereket,például római számokat arab számokká alakít át. A *VIII* számból *8* lesz.
        - **Szimbólumok**: Eltávolítja az összes szimbólumot és speciális karaktert. A *Head&Shoulder* kifejezésből *HeadShoulder* lesz.
        - **Szöveg kisbetűsre: Az összes karaktert kisbetűsre** konvertálja. Az *ALL CAPS and Title Case* kifejezés *all caps and title case* lesz.
        - **Típus (telefon, név, cím, szervezet)**: Szabványosítja a neveket, címeket, telefonszámokat, címeket stb.
        - **Unicode-ból ASCII-be**: A Unicode-jelöléseket ASCII-karakterekké alakítja. A */u00B2* jelölésből *2* lesz.
        - **Szóköz**: Eltávolítja az összes szóközt. A *Hello   World* kifejezésből *HelloWorld* lesz.
      - **Pontosság**: Az adott feltételre alkalmazandó pontossági szint beállítása.
        - **Alapszintű**: Válasszon az Alacsony (30%)*,* a Közepes (60%)*, a* Magas (80%)*és* az Egzakt (100%) közül *·*. Válassza a Pontos **lehetőséget**, ha csak a 100%-nak megfelelő rekordokat szeretné egyeztetni.
        - **Egyéni**: Állítsa be, hogy a rekordoknak hány százalékban kell egyezniük. A rendszer csak az ezt a küszöbértéket meghaladó rekordokat egyezteti.
      - **Név**: A szabály neve.

      :::image type="content" source="media/m3_duplicates_add.png" alt-text="Képernyőkép: Szabály hozzáadása panel az ismétlődések eltávolításához.":::

   1. Ha szükséges, válassza a Feltétel **hozzáadása** > **lehetőséget**, ha további feltételeket szeretne hozzáadni a szabályhoz. A feltételek logikai ÉS operátorral kapcsolódnak, és ezért csak akkor hajtódnak végre, ha minden feltétel teljesül.

   1. Ha szükséges, adja hozzá **a Kivételt** > **,** hogy [kivételeket adjon a szabályhoz](match-entities.md#add-exceptions-to-a-rule). Kivételt képeznek a hamis pozitív és hamis negatívok ritka eseteinek kezelésére.

   1. Válassza a Kész **lehetőséget** a szabály létrehozásához.

1. Tetszés szerint [további szabályokat is felvehet](#define-deduplication-rules).

1. Válasszon ki egy entitást, majd **szerkessze az egyesítési beállításokat**.

1. **Az Egyesítési** beállítások ablaktáblán:
   1. Válasszon egyet a három lehetőség közül annak meghatározásához, hogy melyik rekordot szeretné megőrizni, ha duplikátumot talál:
      - **Legtöbbet kitöltött**: A nyertes rekordként a legtöbb kitöltött attribútummezővel rendelkező rekordot adja meg. Ez az alapértelmezett egyesítési beállítás.
      - **Legújabb**: A nyertes rekordot az időbeli frissesség alapján adja meg. Az időbeli frissesség definiálásához dátum vagy numerikus mező szükséges.
      - **Legrégebbi**: A nyertes rekord a legkevésbé friss rekord lesz. Az időbeli frissesség definiálásához dátum vagy numerikus mező szükséges.

      Döntetlen esetén a győztes rekord az, amelyik a MAX(PK) vagy a nagyobb elsődleges kulcsértékkel rendelkezik.

   1. Ha egy entitás egyes attribútumain meg szeretné határozni az egyesítési beállításokat, válassza a Speciális **lehetőséget** a panel alján. Dönthet például úgy, hogy a legfrissebb e-mail címet és a legteljesebb címet tartja meg a különböző nyilvántartásokból. Bontsa ki az entitást az összes attribútumának megtekintéséhez, és határozza meg, hogy melyik beállítást használja az egyes attribútumokhoz. Ha a recency-alapú beállítást választja, meg kell adnia egy dátum/idő mezőt is, amely meghatározza a recency-t.

      :::image type="content" source="media/m3_adv_merge.png" alt-text="Speciális egyesítési beállítások panel a legutóbbi e-mail-cím és a teljes cím megjelenítésekor":::

   1. Válassza a Kész **lehetőséget** az egyesítési beállítások alkalmazásához.

1. A deduplikációs szabályok és az egyesítési beállítások meghatározása után válassza a Tovább **lehetőséget**.
  
> [!div class="nextstepaction"]
> [Egyetlen entitás következő lépése: Mezők egyesítése](merge-entities.md)

> [!div class="nextstepaction"]
> [Több entitás következő lépése: Egyező feltételek](match-entities.md)

[!INCLUDE[footer-include](includes/footer-banner.md)]
