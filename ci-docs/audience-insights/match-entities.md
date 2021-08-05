---
title: Entitások egyeztetése az adategyesítéshez
description: Entitások egyeztetése az egyesített ügyfélprofilok létrehozásához.
ms.date: 02/23/2021
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: tutorial
author: adkuppa
ms.author: adkuppa
ms.reviewer: mhart
manager: shellyha
ms.openlocfilehash: de53927f7ed1f58176a7ba83f89be7c39064947c
ms.sourcegitcommit: 5c9c54ffe045017c19f0042437ada2c101dcaa0f
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/22/2021
ms.locfileid: "6650321"
---
# <a name="match-entities"></a>Entitások egyeztetése

Az egyeztetési fázis azt adja meg, hogy hogyan kell az adathalmazokat egyesíteni egy egyesített ügyfélprofil-adathalmazba. Az adategyesítési folyamat [leképezési lépésének](map-entities.md) befejezése után készen áll az entitások egyeztetésére. Az egyezetési fázishoz legalább két megfeleltetett entitás szükséges.

A megfeleltetési oldal három szakaszból áll: 
- Az egyező rekordok számát összegző fő mutatók
- Az entitásegyeztetés megfeleltetési sorrendjének és szabályai
- Egyező entitások deduplikálásának szabályai

## <a name="specify-the-match-order"></a>Egyeztetési sorrend megadása

Válassza az **Adatok** > **Egységesítés** > **Egyeztetés** lehetőséget, és válassza a **Sorrend beállítása** lehetőséget az egyeztetési fázisának indításához.

Mindegyik egyezés két vagy több entitást egyesül egyetlen, összesített entitásban. Ugyanakkor megőrzi az egyéni ügyfélrekordokat is. Például kiválasztottunk két entitást: **eCommerce:eCommerceContacts** elsődleges entitásként, és **LoyaltyScheme:loyCustomers** másodlagos entitásként. Az entitások sorrendje határozza meg, hogy a rendszer milyen sorrendben próbálja meg megfeleltetni a rekordokat.

:::image type="content" source="media/match-page.png" alt-text="Képernyőkép az adategyesítési folyamat Egységesítés területén található Megfeleltetés oldalról.":::
  
Az *eCommerce:eCommerceContacts* elsődleges entitást a rendszer megfelelteti a következő *LoyaltyScheme:loyCustomers* entitással. Az első egyeztetési lépésből származó adathalmazt a rendszer megfelelteti a következő entitással, ha több mint két entitás található.

> [!IMPORTANT]
> Az elsődleges entitásként választott entitás az egyesített profilok adathalmazának alapjául szolgál. Ehhez az entitáshoz az egyeztetési fázisban kiválasztott további entitásokat hozzáadja a rendszer. Ez nem jelenti azt, hogy a egyesített entitás az entitásban található *összes* adatot tartalmazni fogja.
>
> Az entitások hierarchiájának kiválasztásában két szempont segíthet:
>
> - Válassza ki azt az entitást, amely a legteljesebb és legmegbízhatóbb profiladatokkal rendelkezik az ügyfelekről elsődleges entitásként.
> - Válassza ki elsődleges entitásként azt az entitást, amely több közös attribútumot tartalmaz az egyéb entitásokkal (például név, telefonszám vagy e-mail-cím).

Az egyezések sorrendjének megadása után a definiált egyezéspárokat láthatja az **Egyező rekordok részletei** szakaszban az **Adatok** > **Egyesítés** > **Megfeleltetés** oldalon. A fő mutatók addig üresek maradnak, amíg be nem fejeződik az egyeztetés folyamata.

## <a name="define-rules-for-match-pairs"></a>Egyezéspárok szabályainak meghatározása

Az egyeztetési szabályok adják meg az entitások meghatározott párjának egyeztetését.

Egy entitásnév mellett szereplő **Szabályok szükségesek** figyelmeztetés azt jelzi, hogy az egyezéspárhoz nincs egyeztetési szabály meghatározva. 

:::image type="content" source="media/match-rule-add.png" alt-text="Képernyőkép az Egyező bejegyzés részletei szakaszról, amelyen kiemelve látható a szabályok hozzáadására szolgáló vezérlő.":::

1. Válassza a **Szabályok hozzáadása** lehetőséget egy entitás alatt az **Egyező bejegyzések részletei** szakaszban, hogy meghatározza az egyezési szabályokat.

1. A **Szabály létrehozása** panelben konfigurálja a szabály feltételeit.

   :::image type="content" source="media/match-rule-conditions.png" alt-text="Képernyőkép egy megnyitott egyezési szabályról, amelyhez feltételeket vettek fel.":::

   - **Entitás/mező (első sor)**: Válasszon egy kapcsolódó entitást és egy attribútumot egy olyan rekord tulajdonságának megadásához, amely valószínűleg csak egy ügyfélre jellemző. Például egy telefonszám vagy egy e-mail-cím. Kerülje az tevékenységtípus-attribútumok egyeztetését. A vásárlási azonosító például valószínűleg nem talál egyezést más rekordtípusban.

   - **Entitás/mező (második sor)**: Az első sorban megadott entitás attribútumának megfelelő attribútum kiválasztása.

   - **Normalizálás**: Válasszon a következő normalizálási lehetőségek közül a kijelölt attribútumok esetén. 
     - Szóköz: Az összes szóköz eltávolítása. A *Hello   World* kifejezésből *HelloWorld* lesz.
     - Szimbólumok: Minden szimbólumot és különleges karaktert eltávolít. A *Head&Shoulder* kifejezésből *HeadShoulder* lesz.
     - Szöveg kisbetűsre: Minden karaktert kisbetűsre alakít át. Az *ALL CAPS and Title Case* kifejezés *all caps and title case* lesz.
     - Unicode-ból ASCII: A Unicode-jelölést átalakítja ASCII-karakterekké. A */u00B2* jelölésből *2* lesz.
     - Számjegyek: Más numerális rendszereket, például a római számjegyeket arab számokká alakít át. A *VIII* számból *8* lesz.
     - Szemantikai típusok: Szabványosítja a neveket, beosztásokat, telefonszámokat, címeket stb. 

   - **Pontosság**: Az adott feltételre alkalmazandó pontossági szint beállítása. 
     - **Alap**: Válasszon az *Alacsony*, *Közepes*, *Magas* és *Pontos* közül. Válassza a **Pontos** lehetőséget, hogy csak az 100 százalékos egyezésű rekordokat egyeztesse. Válasszon másik szintet, ha nem 100%-ban egyező rekordokat szeretne egyeztetni.
     - **Egyéni**: Állítsa be, hogy a rekordoknak hány százalékban kell egyezniük. A rendszer csak az ezt a küszöbértéket meghaladó rekordokat egyezteti.

1. A **Név** mezőbe írja be a szabály nevét.

1. [Adjon hozzá további feltételeket](#add-conditions-to-a-rule), vagy válassza a **Kész** lehetőséget a szabály véglegesítéséhez.

1. Tetszés szerint [további szabályokat is felvehet](#add-rules-to-a-match-pair).

1. Válassza a **Mentés** lehetőséget a módosítások alkalmazásához.

### <a name="add-conditions-to-a-rule"></a>Feltételek hozzáadása szabályhoz

Ha csak akkor szeretne entitásokat egyeztetni, amikor több feltétel is teljesül, adjon feltételeket egy egyezési szabályhoz. A feltételek logikai ÉS operátorral kapcsolódnak, és ezért csak akkor hajtódnak végre, ha minden feltétel teljesül.

1. Lépjen az **Adatok** > **Egyesítés** > **Megfeleltetés** lehetőségre, és válassza azon szabály **Szerkesztés** elemét, amelyhez feltételeket akar hozzáadni.

1. A **Szabály szerkesztése** panelen válassza a **Feltétel hozzáadása** lehetőséget.

1. A szabály mentéséhez válassza a **Kész** gombot.

### <a name="add-rules-to-a-match-pair"></a>Szabályok hozzáadása egyezéspárhoz

Az egyezési szabályok feltételek egy csoportját jelentik. Ha több attribútum alapján létrehozott feltételekkel szeretne entitásokat egyeztetni, adjon hozzá több szabályt

1.  Lépjen az **Adatok** > **Egyesítés** > **Megfeleltetés** lehetőségre, és válassza azon entitás **Szabály hozzáadása** elemét, amelyhez szabályokat akar hozzáadni.

2. Kövesse az [Egyezéspárok szabályainak meghatározása](#define-rules-for-match-pairs) részben látható lépéseket.

> [!NOTE]
> A szabályok sorrendje számít. Az egyezési algoritmus az első szabály alapján próbál meg egyeztetni, és csak akkor halad tovább a második szabályhoz, ha az első szabály még nem adott meg egyezést.

### <a name="change-the-entity-order-in-match-rules"></a>Az entitások sorrendjének módosítása az egyezési szabályokban

Az egyezési szabályok entitásait átrendezheti, hogy módosítsa a feldolgozásuk sorrendjét. A módosított sorrend miatt ütköző szabályokat a rendszer eltávolítja. Az eltávolított szabályokat újra létre kell hozni frissített konfigurációval.

1. Lépjen az **Adatok** > **Egységesítés** > **Egyezés** részre, és válassza a **Szerkesztés** lehetőséget.

1. A **Szabály szerkesztése** panelen a **Mozgatás le/fel** vezérlővel vagy az entitások húzásával módosíthatja a sorrendet.

   :::image type="content" source="media/reorder-match-rules.png" alt-text="Az entitások egyeztetési fázisban való feldolgozási sorrendjének módosítára szolgáló beállítások.":::

1. A szabály mentéséhez válassza a **Kész** gombot.

## <a name="define-deduplication-on-a-match-entity"></a>Deduplikáció definiálása egyeztetett entitáson

Az [entitások közötti egyezés szabályok](#define-rules-for-match-pairs) mellett a deduplikációkat is megadhatja. A *deduplikáció* egy másik folyamat, amikor a rekordokat megfeleltetik. Azonosítja a duplikált bejegyzéseket, és egy rekordba egyesíti őket. A forrásrekordokat a rendszer összekapcsolja az egyesített rekordokat alternatív azonosítókkal.

A deduplikált rekordok ezután felhasználásra kerültek az entitáson keresztüli egyeztetési folyamatban. A deduplikáció az egyes entitások szintjén történik, és minden egyezéspárban használt entitás beállítható.

A deduplikációs szabályok megadása nem kötelező. Ha ilyen szabályok nincsenek konfigurálva, a rendszer által definiált szabályokat kell alkalmazni. Az összes rekordot egyetlen rekordba kombinálja, mielőtt átadja az entitásadatokat az entitások közötti egyeztetésnek a jobb teljesítmény érdekében.

### <a name="add-deduplication-rules"></a>Deduplikációs szabályok hozzáadása

1. Nyissa meg az **Adatok** > **Egységesítés** > **Egyeztetés**-t.

1. Az **egyesített ismétlődések** szakaszban válassza az **entitások beállítása** lehetőséget. Abban az esetben, ha a deduplikációra vonatkozó szabályok már létre vannak hozva, válassza a **Szerkesztés** lehetőséget.

1. Az **Egyesítési beállítások** panelen válassza ki azokat az entitásokat, amelyeken a deduplikációt futtatni szeretné.

1. Adja meg, hogyan kombinálja a duplikált rekordokat, és válasszon egyet a három beállítás közül:
   - **Legtöbbet kitöltött**: A nyertes rekordként a legtöbb kitöltött attribútummezővel rendelkező rekordot adja meg. Ez az alapértelmezett egyesítési beállítás.
   - **Legújabb**: A nyertes rekordot az időbeli frissesség alapján adja meg. Az időbeli frissesség definiálásához dátum vagy numerikus mező szükséges.
   - **Legrégebbi**: A nyertes rekord a legkevésbé friss rekord lesz. Az időbeli frissesség definiálásához dátum vagy numerikus mező szükséges.
 
   > [!div class="mx-imgBorder"]
   > ![Deduplikációs szabályok 1. lépése.](media/match-selfconflation.png "Deduplikációs szabályok 1. lépése")
 
1. Miután az entitások ki vannak jelölve, és az egyesítési preferencia be van állítva, válassza az **Szabály hozzáadása** lehetőséget a deduplikációs szabályok entitás szintjén történő definiálásához.
   - A **Mező kiválasztása** felsorolja az adott entitásból származó összes elérhető mezőt. Válassza ki, hogy melyik mezőt szeretné ellenőrizni a duplikált elemekkel kapcsolatban. Válassza ki a mezőket, amelyek valószínűleg egyediek minden egyes ügyfélnél. Például egy e-mail-cím, vagy a név, a város és a telefonszám kombinációja.
   - Adja meg a normalizálási és pontossági beállításokat.
   - További feltételeket a **Feltétel hozzáadása** lehetőség választásával adhat meg.
 
   > [!div class="mx-imgBorder"]
   > ![Deduplikációs szabályok 2. lépése.](media/match-selfconflation-rules.png "Deduplikációs szabályok 2. lépése")

  Egy entitáshoz több deduplikációs szabályt hozhat létre. 

1. Az egyeztetési folyamat futtatása során a rendszer a rekordokat a deduplikációs szabályokban megadott feltételek alapján csoportosítja. A rekordok csoportosítását követően a rendszer alkalmazza a nyertes rekord beazonosítására szolgáló egyesítési házirendet.

1. Ezt a győztes bejegyzést ezután át kell haladni az entitások közötti egyeztetésnek, a nem győztes rekordokkal (pl. másodlagos azonosítók) az egyeztetési minőség javítása érdekében.

1. Minden megadott egyéni egyezési szabály felülírja a deduplikációs szabályokat. Ha egy deduplikációs szabály azonosítja az egyező bejegyzéseket, és az egyéni egyeztetési szabály beállítása a rekorokhoz Soha ne egyezzen, akkor a két rekord egyeztetése nem történik meg.

1. Az [egyeztetési folyamat futtatása](#run-the-match-process) után megjelenik a deduplikációs statisztika a fő metrikák csempén.

### <a name="deduplication-output-as-an-entity"></a>Deduplikáció kimenete entitásként

A deduplikációs folyamat új entitást hoz létre az egyezéspárok minden entitásához, így azonosíthatók a deduplikált bejegyzések. Ezek az entitások az **Entitások** lap **Rendszer** szakaszában a **ConflationMatchPairs:CustomerInsights** elemmel együtt találhatók meg **Deduplication_DataSource_Entity** névvel.

A deduplikált kimeneti entitás a következő információkat tartalmazza:
- Azonosítók / kulcsok
  - Az elsődleges kulcs mezője és a másodlagos azonosító mezője. A másodlagos azonosítók mező a bejegyzéshez azonosított összes másodlagos azonosítóból áll.
  - Deduplication_GroupId mező mutatja az entitáson belül azonosított csoportot vagy fürtöt, amely a hasonló bejegyzéseket a megadott deduplikáció mezők alapján csoportosítja. Ezt a rendszerfeldolgozási célokra használják. Ha nincsenek megadva manuális deduplikációs szabályok, és a rendszer által definiált deduplikációs szabályok vonatkoznak, akkor előfordulhat, hogy ez a mező nem található meg a deduplikálás kimeneti entitásban.
  - Deduplication_WinnerId: Ez a mező tartalmazza az azonosított csoportokból vagy fürtökből a nyertes azonosítót. Ha a Deduplication_WinnerId megegyezik egy rekord elsődleges kulcsával, ez azt jelenti, hogy az a rekord lesz a győztes rekord.
- A deduplikációs szabályok definiáló mezői.
- Szabály és Pontszám mezők, amelyekben a deduplikációs szabályok alkalmazva lettek és az egyeztető algoritmus által visszaadott pontszám is megegyezik.
   
## <a name="run-the-match-process"></a>Az egyeztetési folyamat futtatása

Az egyeztetési szabályok konfigurálása után, beleértve a több entitásra kiterjedő egyeztetési és deduplikációs szabályokat is, futtathatja az egyeztetési folyamatot. 

Válassza az **Adatok** > **Egységesítés** > **Egyeztetés** lehetőséget, és válassza a **Futtatás** lehetőséget a folyamat indításához. Az egyeztetési algoritmusnak némi időt vesz igénybe a befejezése, és a konfigurációt a művelet befejezéséig nem módosíthatja. A módosítások végrehajtásához meg kell szakítania a futtatást. Jelölje ki a feladat állapotát, és válassza a **Feladat visszavonása** lehetőséget a **Folyamat részletei** ablaktáblában.

A sikeres futtatás eredményét, az egyesített ügyfélprofil entitást az **Entitások** oldalon találja. Az egyesített ügyfélentitás neve **Ügyfelek** a **Profilok** szakaszban. Az első sikeres egyezés futtatása létrehozza a egyesített *Ügyfél* entitást. Minden ezt követő egyezés kibontja az entitást.

> [!TIP]
> Az egyeztetési folyamat futtatása után válassza ki a folyamat állapotát a **Feladat részletei** ablaktábla megnyitásához. Áttekintést ad a feldolgozási időről, az utolsó feldolgozási dátumról, valamint a feladathoz kapcsolódó összes hibáról és figyelmeztetésről. Válassza a **Részletek megtekintése** lehetőséget, hogy lássa, mely entitások vettek részt az egyeztetési folyamatban, mely szabályok vonatkoztak rájuk, és hogy sikerült-e közzétenni a frissítéseket.  
> A feladatokhoz/folyamatokhoz [hatféle állapot](system.md#status-types) tartozhat. Emellett a legtöbb folyamat [más alsóbb szintű folyamatoktól is függ](system.md#refresh-policies).  
> :::image type="content" source="media/process-detail-path.png" alt-text="A feladat állapotára mutató hivatkozás részleteinek lefúrási útvonala.":::

## <a name="review-and-validate-your-matches"></a>Egyeztetések áttekintése és ellenőrzése

Az **Adatok** > **Egyesítés** > **Egyeztetés** részre lépve értékelheti az egyezéspárok minőségét, és finomíthatja őket, ha szükséges.

A lap tetején található csempék a fő metrikákat mutatják, összesitve az egyeztetett bejegyzések és duplikált elemek számát.

:::image type="content" source="media/match-KPIs.png" alt-text="Körülvágott képernyőkép a legfontosabb mutatókról a Egyezés oldalon, számokkal és részletekkel.":::

- **Az egyedi forrásrekordok** az utolsó egyezési futtatásban feldolgozott forrásrekordok számát mutatják.
- **Az egyező és nem egyező rekordok** kiemelik, hogy hány egyedi rekord marad meg az egyezésszabályok feldolgozása után.
- A **Csak egyező rekordok** az összes egyezéspárban található egyezések számát mutatja.

Az egyes egyezéspárok és a szabályainak eredményeit az **Egyező rekordok részletei** táblában mérheti fel. Hasonlítsa össze az egyezéspárból származó rekordok számát a sikeresen egyeztetett rekordok százalékával.

Az egyezéspár szabályait áttekintve láthatja, hogy a szabály szintjén milyen százalékban vannak a sikeresen egyeztetett bejegyzések. Jelölje ki a három pontot (...), majd válassza az **Egyeztetés előnézete** lehetőséget, és tekintse meg ezeket a rekordokat a szabályszinten. Javasoljuk, hogy ellenőrizzen néhány rekordot, hogy azok egyezése megfelelő-e.

Próbáljon meg különböző pontossági küszöbértékeket alkalmazni a feltételek esetén, hogy megtalálja az optimális értéket.

  1. Jelölje ki a három pontot (...) annál a szabálynál, amellyel kísérletezni szeretne, majd válassza a **Szerkesztés** lehetőséget.

  2. Módosítsa a pontossági értékeket a felülvizsgálni kívánt feltételekben.

  3. Válassza az **Előnézet** lehetőséget, így a kiválasztott feltétel esetén egyező és nem egyező bejegyzések számát láthatja.

## <a name="manage-match-rules"></a>Egyezési szabályok kezelése

Az egyezési paraméterek nagy része konfigurálható és finomhangolható.

:::image type="content" source="media/match-rules-management.png" alt-text="Képernyőkép a legördülő menüről az egyezési szabály beállításaival.":::

- **Szabályok sorrendjének módosítása**, ha több szabályt határozott meg. Az egyezésszabályokat átrendezhezi a **Felfelé mozgatás** és **Lefelé mozgatás** lehetőségekkel, vagy húzással.

- **A szabályfeltételek módosítása** a **Szerkesztés** lehetőség kiválasztásával és más mezők kiválasztásával történhet.

- **Inaktiválhat egy szabályt**, hogy megtartsa az egyeztetési szabályt, de azt kizárja az egyeztetési folyamatból.

- **Szabályok duplikálása** Ha egyezés szabályt határoz meg, és hasonló szabályt szeretne létrehozni módosítással, akkor válassza a **Duplikálás** lehetőséget.

- **Szabály törlése** a **Törlés** szimbólum kiválasztásával.

## <a name="specify-custom-match-conditions"></a>Egyéni egyezés feltételeinek megadása

Megadhat olyan feltételeket, hogy bizonyos rekordoknak mindig egyezniük kell vagy soha nem szabad egyezniük. Ezek a szabályok feltölthetők a szabványos egyezési folyamat felülbírálása érdekében. Ha például Gipsz Jakab 1 és Gipsz Jakab 2 található a rekordok között, előfordulhat, hogy a rendszer egy személyként egyezteti őket. Az egyéni egyezésszabályokkal megadhatja, hogy a profiljuk különböző személyekre hivatkozik. 

1. Válassza az **Adatok** > **Egységesítés** > **Egyeztetés** lehetőséget, és válassza az **Egyéni egyezés** lehetőséget az **Egyező rekordok részletei** szakaszban.

  :::image type="content" source="media/custom-match-create.png" alt-text="Képernyőkép az egyezésszabályok szakaszról, amelyen kiemelve látható az Egyéni egyezés vezérlő.":::

1. Ha nincs beállítva egyéni egyezésszabály, új **Egyéni egyezés** ablaktábla látható, amely további részleteket tartalmaz.

1. A **Sablon kitöltése** beállítással lekérhet egy olyan sablonfájlt, amellyel megadhatja, mely entitásokat kell mindig egyeztetni, vagy sosem egyeztetni. Két külön fájlban kell kitölteni a „mindig egyeztetendő” rekordokat és a „sosem egyeztetendő” rekordokat.

1. A sablon mezőket tartalmaz, amelyek meghatározzák az entitást és az egyéni egyeztetésben használandó entitás elsődleges kulcsértékeit. Ha például azt szeretné, hogy az *Értékesítés* entitás *12345* elsődleges kulcsa mindig megegyezzen a *Kapcsolattartó* entitás *34567* elsődleges kulcsával, töltse ki a sablont:
    - Entity1: Értékesítés
    - Entity1Key: 12345
    - Entity2: Kapcsolattartó
    - Entity2Key: 34567

   Ugyanezzel a sablonfájllal megadhat több entitásból származó egyéni egyeztetési rekordokat is.
   
   Ha a deduplikáláshoz egyéni egyeztetést kíván megadni egy entitáson, akkor ugyanazt az entitást kell megadnia, mint az Entity1 és az Entity2, és állítson be különböző elsődleges kulcsértékeket.

1. Az összes alkalmazni kívánt felülbírálás hozzáadását követően mentse a sablonfájlt.

1. Nyissa meg az **Adatok** > **Adatforrások** pontot, és töltse fel a sablonfájlokat új entitásként. A betöltés után ezekkel megadhatja az Egyeztetési konfigurációt.

1. A fájlok feltöltése után, amikor az entitások rendelkezésre állnak, válassza ismét az **Egyéni egyeztetés** lehetőséget. Megjelennek a szerepeltetni kívánt entitások meghatározására szolgáló lehetőségek. Válassza ki a szükséges entitásokat a legördülő menüből.

   :::image type="content" source="media/custom-match-overrides.png" alt-text="Képernyőkép a párbeszédablakról az egyéni egyezés esetének felülbírálása esetén.":::

1. Jelölje ki a **Mindig egyeztetendő** és **Sosem egyeztetendő** lehetőségekhez használni kívánt entitásokat, és válassza a **Kész** lehetőséget.

1. Az egyéni egyezési konfiguráció alkalmazáshoz válassza a **Mentés** lehetőséget az **Egyezés** lapon.

1. Az egyeztetési folyamat futtatásához válassza a **Futtatás** lehetőséget a **Egyezés** oldalon. Az egyéni egyezési konfiguráció felülírja az egyéb megadott egyezési szabályokat.

> [!TIP]
> Lépjen az **Adatok** > **Entitások** pontra, és tekintse át a **ConflationMatchPair** entitást a felülbírálások alkalmazásának ellenőrzése érdekében.

## <a name="next-step"></a>Következő lépés

Legalább egy egyeztetési párra vonatkozó egyeztetési folyamat végrehajtása után feloldhatja a lehetséges ellentmondásokat az adatokban, ha áttekinti az [**Egyesítés**](merge-entities.md) témakört.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
