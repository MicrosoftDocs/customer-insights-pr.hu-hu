---
title: Entitások egyeztetése az adategyesítéshez
description: Entitások egyeztetése az egyesített ügyfélprofilok létrehozásához.
ms.date: 10/14/2020
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: tutorial
author: m-hartmann
ms.author: mhart
ms.reviewer: adkuppa
manager: shellyha
ms.openlocfilehash: 05afd17b7f1b34f7f24a8fa8cb2dc32c1649d40f
ms.sourcegitcommit: 139548f8a2d0f24d54c4a6c404a743eeeb8ef8e0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/15/2021
ms.locfileid: "5267481"
---
# <a name="match-entities"></a>Entitások egyeztetése

A megfeleltetési fázis befejezése után készen áll az entitások egyeztetésére. Az egyeztetési fázis azt adja meg, hogy hogyan kell az adathalmazokat egyesíteni egy egyesített ügyfélprofil-adathalmazba. Az egyezetési fázishoz legalább [két megfeleltetett entitás](map-entities.md) szükséges.

## <a name="specify-the-match-order"></a>Egyeztetési sorrend megadása

Válassza az **Adatok** > **Egységesítés** > **Egyeztetés** lehetőséget, és válassza a **Sorrend beállítása** lehetőséget az egyeztetési fázisának indításához.

Az egyes egyeztetések két vagy több entitást egyetlen entitásba egyesítenek, miközben megtartják az egyedi ügyfélrekordokat. A következő példában három entitást választottunk: **ContactCSV: TestData** **Elsődleges** entitásként, **WebAccountCSV: TestData** **2. entitás** entitásként, és **CallRecordSmall: TestData** **3. entitás** entitásként. A kijelölések feletti ábra bemutatja, hogyan történik az egyeztetési sorrend végrehajtása.

> [!div class="mx-imgBorder"]
> ![Az adatok egyeztetési sorrendjének módosítása](media/configure-data-match-order-edit-page.png "Az adatok egyeztetési sorrendjének módosítása")
  
Az **Elsődleges** entitás egyeztetése a **2. entitással** történik. Az első egyeztetésből származó adathalmazt a rendszer a **3. entitással** egyezteti.
Ebben a példában csak két egyeztetést választottunk, de a rendszer többet is támogathat.

> [!IMPORTANT]
> Az **elsődleges** entitásként választott entitás az egyesített fő adathalmaz alapjául szolgál. Ehhez az entitáshoz az egyeztetési fázisban kiválasztott további entitásokat hozzáadja a rendszer. Ez ugyanakkor nem jelenti azt, hogy az egyesített entitás tartalmazza az entitáshoz tartozó *összes* adatot.
>
> Az entitások hierarchiájának kiválasztásában két szempont segíthet:
>
> - Ön szerint melyik entitás tartalmazza a legteljesebb és legmegbízhatóbb adatokat az ügyfelekről?
> - Az imént azonosított entitáshoz tartoznak-e olyan attribútumok, amelyekkel más entitások is rendelkeznek (például név, telefonszám vagy e-mail-cím)? Ha nem, válassza ki a második legmegbízhatóbb entitást.

Válassza a **Kész** lehetőséget az egyeztetési sorrend mentéséhez.

## <a name="define-rules-for-your-first-match-pair"></a>Az első egyeztetési pár szabályainak megadása

Az egyeztetési sorrend megadását követően az **Egyeztetés** oldalon láthatók a megadott egyezések. A képernyő felső részén lévő csempék mindaddig üresek, amíg le nem futtatja az egyeztetési sorrendet.

> [!div class="mx-imgBorder"]
> ![Szabályok definiálása](media/configure-data-match-need-rules.png "Szabályok definiálása")

A **Szabályok szükségesek** figyelmeztetés azt jelzi, hogy az egyeztetési párhoz nincs egyeztetési szabály meghatározva. Az egyeztetési szabályok adják meg az entitások meghatározott párjának egyeztetését.

1. Az első szabály megadásához nyissa meg a **Szabály meghatározása** panelt a megfelelő egyeztetési sor kiválasztásával az egyeztetési táblában (1), majd válassza az **Új szabály létrehozása** (2) lehetőséget.

   > [!div class="mx-imgBorder"]
   > ![Új szabály létrehozása](media/configure-data-match-new-rule2.png "Új szabály létrehozása")

2. A **Szabály szerkesztése** panelen konfigurálhatja az adott szabály feltételeit. Az egyes feltételeket két sor jelöli, amelyek kötelezően kiválasztandó elemeket foglalnak magukban.

   > [!div class="mx-imgBorder"]
   > ![Új szabály panel](media/configure-data-match-new-rule-condition.png "Új szabály panel")

   Entitás/mező (első) – Olyan attribútum, amelyet a rendszer az első egyeztetési pár entitásának egyeztetésre használ. A példák közé tartozik a telefonszám vagy az e-mail-cím. Válasszon olyan attribútumot, amely valószínűleg egyedi az ügyfélre nézve.

   > [!TIP]
   > Kerülje a tevékenység típusú attribútumok alapján történő egyeztetést. Más szavakkal, ha egy attribútum tevékenységnek tűnik, akkor lehet, hogy egy rossz feltétel az egyeztetéshez.  

   Entitás/mező (második) – Olyan attribútum, amelyet a rendszer a második egyeztetési pár entitásának egyeztetésre használ.

   Normalizálás – **Normalizálás módszer**: különböző normalizáló lehetőségek állnak rendelkezésre a kijelölt attribútumokhoz. Például az írásjelek eltávolításával vagy a szóközök eltávolításával

   A szervezet nevének normalizálása (előzetes verzió) esetében kiválaszthatja a **Típus (Telefonszám, név, szervezet)** lehetőséget

   > [!div class="mx-imgBorder"]
   > ![Normalizálás – B2B](media/match-normalization-b2b.png "Normalizálás – B2B")

   Pontossági szint – A feltételhez használandó pontossági szint. A pontossági szint egyeztetési feltételhez való beállításának két típusa lehet: **Alapszintű** és **Egyéni**.  
   - Alapszitű: Négy választási lehetőséget biztosít: alacsony, közepes, magas és pontos. Válassza a **Pontos** lehetőséget, hogy csak az 100 százalékos egyezésű rekordokat egyeztesse. Válasszon másik szintet, ha nem 100%-ban egyező rekordokat szeretne egyeztetni.
   - Egyéni: A csúszka segítségével határozza meg, hogy milyen egyéni százalékértékkel kell megegyezniük a rekordoknak, vagy adjon meg egy értéket az **Egyéni** mezőben. A rendszer csak az ezt a küszöbértéket átlépő rekordokat fog összevont egyeztetett párokként egyeztetni. A csúszka értékei 0 és 1 közöttiek. Tehát az 0,64 a 64 százalékot jelenti.

3. A szabály mentéséhez válassza a **Kész** gombot.

### <a name="add-multiple-conditions"></a>Több feltétel hozzáadása

Ha csak több feltétel teljesülése esetén szeretné egyeztetni az entitásokat, adjon hozzá további feltételeket, amelyek egy ÉS operátorral kapcsolódnak egymáshoz.

1. A **Szabály szerkesztése** panelen válassza a **Feltétel hozzáadása** lehetőséget. A feltételeket egy létező feltétel melletti Eltávolítás gomb kiválasztásával is törölheti.

2. A szabály mentéséhez válassza a **Kész** gombot.

## <a name="add-multiple-rules"></a>Több szabály hozzáadása

Minden feltétel egyetlen attribútumpárra vonatkozik, míg a szabályok a feltételeket határozzák meg. Ha az entitásokat különböző attribútumhalmazok alapján szeretné egyeztetni, több szabályt is hozzáadhat.

1. A célközönség információin belül nyissa meg a következőt: **Adatok** > **Egyesítés** > **Egyeztetés**.

2. Válassza a frissítendő entitást, és válassza a **Szabályok hozzáadása** elemet.

3. Kövesse a [Szabályok meghatározása az első egyeztetési párra vonatkozóan](#define-rules-for-your-first-match-pair) részben leírt eljárást.

> [!NOTE]
> A szabály sorrendje számít. Az egyeztetési algoritmus az első szabály alapján próbál egyeztetni, majd ha az első szabály alapján nem talált egyezést, folytatja a második szabállyal.

## <a name="define-deduplication-on-a-match-entity"></a>Deduplikáció definiálása egyeztetett entitáson

A fenti szakaszokban körvonalazott módon a több entitásra vonatkozó egyeztetési szabályok megadásával együtt megadhatja a deduplikáció szabályait is. A *deduplikáció* egy folyamat. Azonosítja a duplikált bejegyzéseket, egyesíti őket egy rekordba, és az egyesített rekordhoz hozzákapcsolja az összes forrásrekordot az egyesített rekordhoz tartozó eltérő azonosítóval.

A deduplikált rekord beazonosítása után a rekordot a rendszer az entitások közötti egyeztetési folyamatban használja. A rendszer az entitás szintjén hajtja végre a deduplikációt, és a egyeztetési folyamat során használt minden entitásra alkalmazható.

### <a name="add-deduplication-rules"></a>Deduplikációs szabályok hozzáadása

1. A célközönség információin belül nyissa meg a következőt: **Adatok** > **Egyesítés** > **Egyeztetés**.

1. Az **egyesített ismétlődések** szakaszban válassza az **entitások beállítása** lehetőséget.

1. Az **Egyesítési beállítások** szakaszban válassza ki azokat az entitásokat, amelyeken a deduplikációt alkalmazni szeretné.

1. Adja meg, hogyan egyesítse a duplikált rekordokat, és válasszon egyet a három egyesítési beállítás közül:
   - *Legtöbbet kitöltött*: A nyertes rekordként a legtöbb kitöltött attribútummal rendelkező rekordot adja meg. Ez az alapértelmezett egyesítési beállítás.
   - *Legújabb*: A nyertes rekordot az időbeli frissesség alapján adja meg. Az időbeli frissesség definiálásához dátum vagy numerikus mező szükséges.
   - *Legrégebbi*: A nyertes rekord a legkevésbé friss rekord lesz. Az időbeli frissesség definiálásához dátum vagy numerikus mező szükséges.
 
   > [!div class="mx-imgBorder"]
   > ![Deduplikációs szabályok 1. lépése](media/match-selfconflation.png "Deduplikációs szabályok 1. lépése")
 
1. Miután az entitások ki vannak jelölve, és az egyesítési preferencia be van állítva, válassza az **Új szabály létrehozása** lehetőséget a deduplikációs szabályok entitás szintjén történő definiálásához.
   - A **Mező kiválasztása** felsorolja az adott entitás minden rendelkezésre álló mezőjét, amelynél a forrásadatok deduplikációját el szeretné végezni.
   - Adja meg a normalizálás és a pontosság beállításait hasonló módon, ahogy az az entitások közti egyeztetésben meg van adva.
   - További feltételeket a **Feltétel hozzáadása** lehetőség választásával adhat meg.
 
   > [!div class="mx-imgBorder"]
   > ![Deduplikációs szabályok 2. lépése](media/match-selfconflation-rules.png "Deduplikációs szabályok 2. lépése")

  Egy entitáshoz több deduplikációs szabályt hozhat létre. 

1. Az egyeztetési folyamat futtatása során a rendszer a rekordokat a deduplikációs szabályokban megadott feltételek alapján csoportosítja. A rekordok csoportosítását követően a rendszer alkalmazza a nyertes rekord beazonosítására szolgáló egyesítési házirendet.

1. Ezt a győztes bejegyzést ezután át kell haladni az entitások közötti egyeztetésnek, a nem győztes rekordokkal (pl. másodlagos azonosítók) az egyeztetési minőség javítása érdekében.

1. A Mindig egyezzen és Soha ne egyezzen típushoz megadott bármely egyéni egyeztetési szabály mindig felülbírálja a deduplikációs szabályokat. Ha egy deduplikációs szabály azonosítja az egyező bejegyzéseket, és az egyéni egyeztetési szabály beállítása a rekorokhoz Soha ne egyezzen, akkor a két rekord egyeztetése nem történik meg.

1. Az egyeztetési folyamat futtatása után megjelenik a deduplikációs statisztika.
   
> [!NOTE]
> A deduplikációs szabályok megadása nem kötelező. Ha ilyen szabályok nincsenek konfigurálva, a rendszer által definiált szabályokat kell alkalmazni. Ezek összecsukják az összes olyan rekordot, amelyek azonos értékkombinációval (pontos egyezéssel) rendelkeznek az elsődleges kulcsból, és az egyeztetési szabályokban található mezőket egyetlen rekordba, mielőtt továbbadják az entitásadatokat az entitások közti egyeztetésnek a javított teljesítmény és rendszerstabilitás érdekében.

## <a name="run-your-match-order"></a>Az egyeztetési sorrend futtatása

Az egyeztetési szabályok megadása után, beleértve a több entitásra kiterjedő egyeztetési és deduplikációs szabályokat is, futtathatja az egyeztetési sorrendet. A folyamat indításához az **Egyeztetés** oldalon válassza a **Futtatás** elemet. Az egyeztetési algoritmus végrehajtása kis időt vehet igénybe. Az **Egyeztetés** oldalon található tulajdonságokat az egyeztetési folyamat befejezéséig nem módosíthatja. A létrehozott egyesített ügyfélprofil-entitást az **Entitások** oldalon találja. Az egyesített ügyfélentitás neve a következő: **ConflationMatchPairs : CustomerInsights**.

A további módosítások elvégzéséhez és a lépés újrafuttatásához visszavonhat egy folyamatban lévő egyeztetést. Válassza ki a **Frissítés folyamatban...** szöveget és válassza a **Feladat megszakítása** lehetőséget a megjelenő oldalpanel alján.

Amikor az egyeztetési folyamat kész, a **Frissítés folyamatban...** szöveg módosul **Sikeres** értékre, és ismét használhatja az oldal összes funkcióját.

Az első egyeztetési folyamat egy egyesített fő entitás létrehozását eredményezi. Az összes ezt követő egyeztetés futtatása ezen entitás bővítését eredményezi.

> [!TIP]
> A feladatokhoz/folyamatokhoz [hatféle állapot](system.md#status-types) tartozhat. Emellett a legtöbb folyamat [más alsóbb szintű folyamatoktól is függ](system.md#refresh-policies). Kiválaszthatja egy folyamat állapotát, és megtekintheti a hozzá tartozó teljes feladat folyamatának részleteit. Miután kiválasztotta a **Részletek megtekintése** lehetőséget a feladat egyik feladatához, további információk jelennek meg: feldolgozási idő, legutóbbi feldolgozás dátuma, és a feladathoz társított összes hiba és figyelmeztetés.

## <a name="deduplication-output-as-an-entity"></a>Deduplikáció kimenete entitásként
Az egyeztetésének részeként létrehozott egységes főentitáson kívül a deduplikáció-folyamat az egyeztetési sorrendben létrehozott minden entitáshoz létrehoz egy új entitást, hogy azonosíthatók a deduplikált bejegyzések. Ezek az entitások az **Entitások** lap **Rendszer** szakaszában a **ConflationMatchPairs:CustomerInsights** elemmel együtt találhatók meg **Deduplication_Datasource_Entity** névvel.

A deduplikált kimeneti entitás a következő információkat tartalmazza:
- Azonosítók / kulcsok
  - Az elsődleges kulcs mezője és a másodlagos azonosító mezője. A másodlagos azonosítók mező a bejegyzéshez azonosított összes másodlagos azonosítóból áll.
  - Deduplication_GroupId mező mutatja az entitáson belül azonosított csoportot vagy fürtöt, amely a hasonló bejegyzéseket a megadott deduplikáció mezők alapján csoportosítja. Ezt a rendszerfeldolgozási célokra használják. Ha nincsenek megadva manuális deduplikációs szabályok, és a rendszer által definiált deduplikációs szabályok vonatkoznak, akkor előfordulhat, hogy ez a mező nem található meg a deduplikálás kimeneti entitásban.
  - Deduplication_WinnerId: Ez a mező tartalmazza az azonosított csoportokból vagy fürtökből a nyertes azonosítót. Ha a Deduplication_WinnerId megegyezik egy rekord elsődleges kulcsával, ez azt jelenti, hogy az a rekord lesz a győztes rekord.
- A deduplikációs szabályok definiáló mezői.
- Szabály és Pontszám mezők, amelyekben a deduplikációs szabályok alkalmazva lettek és az egyeztető algoritmus által visszaadott pontszám is megegyezik.

## <a name="review-and-validate-your-matches"></a>Egyeztetések áttekintése és ellenőrzése

Értékelje az egyeztetési párok minőségét, és finomítson rajtuk:

- Az **Egyeztetés** oldalon két csempe található, amelyek az adatokkal kapcsolatos kezdeti információkat tartalmazzák.

  - **Egyedi ügyfelek**: a rendszer által azonosított egyedi profilok számát jeleníti meg.
  - **Egyeztetett bejegyzések**: az összes egyeztetési párra vonatkozóan mutatja meg az egyeztetések számát.

- Az **Egyeztetési sorrend** táblában értékelheti az egyes egyeztetési párok eredményeit, ha összehasonlítja az adott egyeztetési pár entitásból származó rekordok számát a sikeresen egyeztetett rekordok számával.

- Az **Egyeztetési sorrend** táblában az entitás **Szabályok** szakaszában látható a sikeresen egyeztetett rekordok százaléka a szabály szintjén. A szabály mellett látható táblaszimbólum kiválasztásával a szabály szintjén tekintheti meg az összes ilyen rekordot. Javasoljuk, hogy tekintse át a rekordok egy részét, és ellenőrizze, hogy helyesen egyeztette-e őket a rendszer.

- Kísérletezzen a feltételeinél különböző pontossági küszöbértékekkel az optimális érték meghatározásához.

  1. Válassza a három pont (...) lehetőséget annál az egyeztetési párra vonatkozó szabálynál, amellyel kísérletezni szeretne, és válassza a **Szerkesztés** lehetőséget.

  2. Válassza ki a feltételt, amellyel kísérletezni szeretne. Az egyes feltételeket az **Egyeztetési szabály** panel egyes sorai jelölik.

  3. A **Feltételek előnézete** lapon látható, hogy milyen pontossági szinttel választotta ki a feltételt. Keresse meg a kiválasztott feltételhez tartozó egyeztetett és nem egyeztetett rekordok számát.

     Ismerje meg alaposan a különböző küszöbértékszintek hatásait. Összehasonlíthatja, hogy a rekordok egyeztetése hogyan történik az egyes küszöbértékszintek esetén, és megtekintheti az egyes lehetőségek alatt a rekordokat. Válassza ki az egyes csempéket, és tekintse át a táblaszakaszban található adatokat.

## <a name="optimize-your-matches"></a>Egyeztetések optimalizálása

Javítsa a minőséget bizonyos egyeztetési paraméterek újrakonfigurálásával:

- **Egyeztetési sorrend módosítása** a **Szerkesztés** lehetőség kiválasztásával, majd az egyeztetési sorrend mezők módosításával.

  > [!div class="mx-imgBorder"]
  > ![Adatok egyeztetési sorrendjének módosítása](media/configure-data-match-order-edit.png "Adatok egyeztetési sorrendjének módosítása")

- **Szabályok sorrendjének módosítása**, ha több szabályt határozott meg. Az egyeztetési szabályok sorrendjét átrendezheti az egyeztetési szabályok rácsán a **Mozgatás felfelé** és **Mozgatás lefelé** lehetőségekkel.

  > [!div class="mx-imgBorder"]
  > ![Szabálysorrend módosítása](media/configure-data-change-rule-order.png "Szabálysorrend módosítása")

- **Szabályok megkettőzése**, ha megadott egy olyan egyeztetési szabályt, amelyhez hasonló szabályt szeretne létrehozni bizonyos módosításokkal. Ehhez válassza a **Megkettőzés** elemet.

  > [!div class="mx-imgBorder"]
  > ![Szabály megkettőzése](media/configure-data-duplicate-rule.png "Szabály megkettőzése")

- **Inaktiválhat egy szabályt**, hogy megtartsa az egyeztetési szabályt, de azt kizárja az egyeztetési folyamatból.

  > [!div class="mx-imgBorder"]
  > ![Szabály inaktiválása](media/configure-data-deactivate-rule.png "Szabály inaktiválása")

- **Szabályok módosítása** a **Szerkesztés** szimbólum választásával. Az alábbi módosításokat is alkalmazhatja:

  - Feltétel attribútumainak módosítása: Válasszon új attribútumokat az adott feltétel sorában.
  - A feltétel küszöbértékének módosítása: Állítsa be a pontosság csúszkáját.
  - A feltétel normalizációs módszerének módosítása: Frissítse a normalizációs módszert.

## <a name="specify-your-custom-match-records"></a>Egyéni egyeztetési rekordok megadása

Megadhat olyan feltételeket, hogy bizonyos rekordoknak mindig egyezniük kell vagy soha nem szabad egyezniük. Ezeket a szabályokat tömegesen is feltöltheti az egyeztetési folyamatba.

1. Válassza az **Egyéni egyeztetés** lehetőséget az **Egyeztetési sorrend** képernyőn.

   > [!div class="mx-imgBorder"]
   > ![Egyéni egyeztetés létrehozása](media/custom-match-create.png "Egyéni egyeztetés létrehozása")

2. Ha nincs feltöltött entitása, egy új **Egyéni egyeztetés** párbeszédpanel jelenik meg, amelyhez bizonyos részleteket ki kell töltenie. Ha korábban már megadta ezeket az adatokat, ugorjon a 8. lépésre.

   > [!div class="mx-imgBorder"]
   > ![Új egyéni egyeztetés párbeszédpanel](media/custom-match-new-dialog-box.png "Új egyéni egyeztetés párbeszédpanel")

3. A **Sablon kitöltése** beállítással lekérhet egy olyan sablonfájlt, amellyel megadhatja, mely entitásokat kell mindig egyeztetni, vagy sosem egyeztetni. Két külön fájlban kell kitölteni a „mindig egyeztetendő” rekordokat és a „sosem egyeztetendő” rekordokat.

4. A sablon mezőket tartalmaz, amelyek meghatározzák az entitást és az egyéni egyeztetésben használandó entitás elsődleges kulcsértékeit. Ha például azt szeretné, hogy az Értékesítés entitás 12345 elsődleges kulcsa mindig egyeztetve legyen a Kapcsolattartó entitás 34567 elsődleges kulcsával, a következőt kell megadnia:
    - Entity1: Értékesítés
    - Entity1Key: 12345
    - Entity2: Kapcsolattartó
    - Entity2Key: 34567

   Ugyanezzel a sablonfájllal megadhat több entitásból származó egyéni egyeztetési rekordokat is.
   
   Ha a deduplikáláshoz egyéni egyeztetést kíván megadni egy entitáson, akkor ugyanazt az entitást kell megadnia, mint az Entity1 és az Entity2, és állítson be különböző elsődleges kulcsértékeket.

5. Az összes alkalmazni kívánt felülbírálás hozzáadását követően mentse a sablonfájlt.

6. Nyissa meg az **Adatok** > **Adatforrások** pontot, és töltse fel a sablonfájlokat új entitásként. A betöltés után ezekkel megadhatja az Egyeztetési konfigurációt.

7. A fájlok feltöltése után, amikor az entitások rendelkezésre állnak, válassza ismét az **Egyéni egyeztetés** lehetőséget. Megjelennek a szerepeltetni kívánt entitások meghatározására szolgáló lehetőségek. Válassza ki a szükséges entitásokat a legördülő menüből.

   > [!div class="mx-imgBorder"]
   > ![Egyéni egyeztetés felülbírálásai](media/custom-match-overrides.png "Egyéni egyeztetés felülbírálásai")

8. Jelölje ki a **Mindig egyeztetendő** és **Sosem egyeztetendő** lehetőségekhez használni kívánt entitásokat, és válassza a **Kész** lehetőséget.

9. Válassza a **Mentés** elemet az **Egyeztetés** oldalon az imént beállított egyéni egyeztetés konfigurációnál.

10. Válassza a **Futtatás** elemet az **Egyeztetés** oldalon, amellyel elindítja az egyeztetési folyamatot, és az egyéni egyeztetési konfiguráció érvénybe lép. A konfigurációs készlet felülbírálja a rendszer által egyeztetett szabályokat.

11. Az egyeztetés végrehajtása után ellenőrizheti a **ConflationMatchPair** entitást, és megerősítheti, hogy a felülbírálásokat a rendszer alkalmazta az összevont egyeztetésekre.

## <a name="next-step"></a>Következő lépés

Legalább egy egyeztetési párra vonatkozó egyeztetési folyamat végrehajtása után feloldhatja a lehetséges ellentmondásokat az adatokban, ha áttekinti az [**Egyesítés**](merge-entities.md) témakört.


[!INCLUDE[footer-include](../includes/footer-banner.md)]