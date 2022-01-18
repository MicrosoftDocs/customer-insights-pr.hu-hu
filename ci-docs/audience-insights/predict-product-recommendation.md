---
title: Termékjavaslat-előrejelzések
description: Olyan termékek előre jelzése, amelyekbe az ügyfél valószínűleg mag fog vásárolni vagy interakcióba lép velük.
ms.date: 01/13/2022
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: wmelewong
ms.author: wameng
manager: shellyha
ms.openlocfilehash: 62b829b6ca3074e0ca52fb52584b74572bb05f05
ms.sourcegitcommit: 15b1521041149716f8031cfa6d0dc61a56a5e2ff
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/13/2022
ms.locfileid: "7967797"
---
# <a name="product-recommendation-prediction-preview"></a>Termékjavaslat-előrejelzés (előzetes verzió)

A termékjavaslati modell prediktív termékjavaslatokat hoz létre. Az ajánlások a korábbi vásárlási viselkedésen és a hasonló vásárlási mintával rendelkező ügyfeleken alapulnak. Új termékjavaslat-előrejelzéseket az **Információk** > **Előrejelzések** lapon hozhat létre. Az Ön által létrehozott többi előrejelzés megtekintéséhez válassza a **Saját előrejelzések** lehetőséget.

A termékre vonatkozó javaslatokra a helyi jogszabályok és előírások, illetve az ügyfelek elvárásai vonatkozhatnak, amelyeket a modell tervezésekor nem vettek külön figyelembe.  Ennek a prediktív lehetőségnek a felhasználójaként a **javaslatokat még az előtt át kell vizsgálnia, mielőtt azokat átadná az ügyfeleknek**, továbbá meg kell győződnie arról, hogy megfelel-e a vonatkozó jogszabályoknak és szabályozásoknak, illetve az ügyfél elvárásainak azzal szemben, amiről Ön már ajánlatot tett. 

Ezenkívül a modell kimenete a termékazonosítón alapuló javaslatokat is tartalmaz. A szállítási mechanizmusnak megfeleltethető termékazonosítókat kell leképezni a megfelelő tartalomra ahhoz, hogy az ügyfelek el tudjanak számolni a honosítással, a képi tartalommal és egyéb, az üzleti tevékenységre jellemző tartalommal vagy viselkedéssel.

## <a name="sample-guide"></a>Mintaútmutató

Ha ki szeretné próbálni ezt a szolgáltatást, de nem rendelkezik az alábbi követelményeknek való megfeleléshez szükséges adatokkal, létrehozhat [egy minta megvalósítást](sample-guide-predict-product-recommendation.md).

## <a name="prerequisites"></a>Előfeltételek

- Legalább [közreműködői engedély](permissions.md) a Customer Insightsban.

- Az üzleti ismeretek, hogy tisztában legyen azzal, milyen típusú termékeket kínál a vállalkozása, és hogyan lépnek interakcióba ezekkel az ügyfelek. Támogatjuk, hogy az ügyfelek által korábban megvásárolt termékekre vagy új termékekre vonatkozó javaslatokat.

- A tranzakciókkal, vásárlásokkal kapcsolatos adatok és a velük kapcsolatos előzmények:
    - A Tranzakcióazonosítók, hogy meghatározhassa a vásárlásokat vagy tranzakciókat.
    - Ügyfélazonosítók, a tranzakciókat hozzárendeléséhez az ügyfeleihez.
    - Tranzakciós események dátumai, amelyek meghatározzák a dátumot, amikor a tranzakció történt.
    - A tranzakció termékazonosító-információi.
    - (Nem kötelező) Termékkatalógus adatentitás a termékszűrő használatához.
    - (Nem kötelező) Hogy a tranzakció visszatérítés-e vagy sem.
    - A szemantikus adatréteg sémához a következő információk szükségesek:
        - **Tranzakcióazonosító:** Egy egyedi azonosító a vásárláshoz vagy tranzakcióhoz.
        - **Tranzakció dátuma:** A vásárlás vagy tranzakció dátuma.
        - **A tranzakció értéke:** A pénznembeli/számértékbeli értéke a vásárlásnak vagy tranzakciónak.
        - **Egyedi termékazonosító:** A megvásárolt termék vagy szolgáltatás azonosítója, ha az adat a sortétel szintjén szerepel.
        - (Nem kötelező) **Vásárlás vagy visszatérés:** Egy logikai mező, ahol az *igaz* érték azonosítja, hogy a tranzakció visszatérési érték volt. Ha nem adja meg a Vásárlási vagy Visszatérési adatokat a modellhez, és a **Tranzakció értéke** negatív, akkor ezt az információt a visszatérés levonásához is használjuk.
- Javasolt adatjellemzők:
    - Elegendő korábbi adatok: Legalább egy évre, lehetőség szerint 2-3 évre visszamenő tranzakciós adatok, hogy valamilyen szezonalitást ki lehessen mutatni.
    - Ügyfelenkénti több vásárlás: Ügyfélazonosítónkénti három vagy több tranzakció
    - Ügyfelek száma: Legalább 100 ügyfél, lehetőség szerint 10 000-nél több ügyfél. A modell 100-nál kevesebb ügyfél esetén nem működik.

> [!NOTE]
> - A modellhez az ügyfelek tranzakciós előzményeire van szükség. A tranzakció meghatározása nagyon rugalmas. A felhasználó és termék közötti interakciót leíró adatok bemeneti adatként is működhetnek. Például termékvásárlás, tanfolyamon vagy eseményen való részvétel.
> - Jelenleg csak egy tranzakcióelőzmény-entitás konfigurálható. Ha több beszerzési entitás van, az adatbetöltés előtt őket kell Power Query behozni.
> - Ha a megrendelés és a megrendelés részletei eltérő entitások, akkor a modell használata előtt kapcsolja össze őket. A modell nem működik csak egy entitás megrendelésazonosítójával vagy bizonylatazonosítójával.


## <a name="create-a-product-recommendation-prediction"></a>Termékjavaslat-előrejelzés létrehozása

1. A Customer Insights szolgáltatásban lépjen az **Intelligencia** > **Előrejelzések** részre.

1. Válassza ki a **Termékjavaslat-modell (előzetes verzió)** csempét, és ott válassza az **A modell használata** menüpontot.
   > [!div class="mx-imgBorder"]
   > ![Terméka javaslati modell csempéje a Modell használata gombbal.](media/product-recommendation-usethismodel.PNG "Terméka javaslati modell csempéje a Modell használata gombbal")

1. Tekintse át a modellkövetelményekkel kapcsolatos információkat. Ha rendelkezésére állnak a szükséges adatok, válassza az **Első lépések** lehetőséget.

### <a name="name-model"></a>Név modell

1. Adja meg a modell nevét; ez különbözteti majd meg a többi modelltől.

1. Adjon meg nevet a kimeneti entitásnak, kizárólag betűk és számok felhasználásával, szóközök nélkül. Ez lesz az a név, amelyet a modell entitás használni fog. Azután válassza a **Következő** elemet.

### <a name="define-product-recommendation-configuration"></a>Termékjavaslat konfigurációjának meghatározása

1. Állítsa be az ügyfélnek javasolni kívánt **Termékek számát**. Ez az érték attól függ, hogy a szállítási módja hogyan tölti ki az adatokat. Ha három terméket javasolhat, ennek megfelelően állítsa be ezt az értéket.
   
   >[!TIP]
   > A **piszkozatok mentése lehetőség** kiválasztásával bármikor beállíthatja a előrejelzés piszkozatként történő mentéséhez. A vázlat-előrejelzés a **Saját előrejelzések** lapon található.

1. Válassza ki, hogy a vevők által nemrégiben vásárolt termékeket is bele szeretné-e foglalni a **Vásárlások ismétlése várt** mezőbe.

1. Állítsa be a **Visszanéző ablakot**. Ez a beállítás megadja az időkeretet, amit a modell figyelembe, mielőtt újra javasolja a terméket a felhasználónak. Például jelezheti, hogy egy ügyfél két évente vásárol laptopot. Ez az ablak az utóbbi két év vásárlási előzményeit fogja megmutatni, és ha talál ilyen elemet, akkor a rendszer kiszűri az elemet a javaslatok közül.

1. Válassza a **Tovább** lehetőséget

### <a name="add-required-data"></a>Szükséges adatok hozzáadása

1. Válassza az **Adatok hozzáadása** lehetőséget, és válassza ki azt a tevékenységtípust az oldalsó panelen, amely a tranzakcióhoz vagy a vásárlási előzményekhez szükséges adatokat tartalmazza.

1. A **Tevékenységek kiválasztása** alatt válassza ki az adott lehetőségeket a kijelölt tevékenységből, amelyekre a számítással koncentrálni szeretne.

   :::image type="content" source="media/product-recommendation-select-semantic-activity.PNG" alt-text="A szemantikus típus alatti tevékenységek kiválasztását bemutató oldalsó panel.":::

1. Ha a tevékenységet még nem képezte le szemantikus típusra, akkor válassza a **Szerkesztés** lehetőséget ehhez. Megnyílik az irányított élmény a szemantikus tevékenységek leképezéséhez. Képezze le az adatokat a kiválasztott tevékenységtípus kapcsolódó mezőihez.

   :::image type="content" source="media/product-recommendation-set-activity-type.PNG" alt-text="Oldalbeállítás tevékenységtípus.":::

1. Miután leképezi a tevékenységet a megfelelő szemantikai típusra, válassza a **Tovább** gombot a folytatáshoz 
 
1. A szemantikus attribútumokat a modell futtatásához szükséges mezőkre kell leképezni.

1. Válassza a **Mentés** parancsot.

1. Válassza a **Következő** lehetőséget.


### <a name="configure-product-filters"></a>Termékszűrők konfigurálása

Időnként csak bizonyos termékek hasznosak vagy megfelelőek a megtervezett előrejelzés típusának. A termékszűrők segítségével meghatározott tulajdonságokkal bíró termékek egy csoportját azonosíthatja, amely az ügyfeleknek ajánlott. A modell a rendelkezésre álló összes terméket fel fogja használni a minták elsajátítása érdekében, de csak a termékszűrőnek megfelelő termékeket használja a kimenetben.

1. A **Termékinformáció hozzáadása** lépésben vegye fel az egyes termékekre vonatkozó információkat tartalmazó termékkatalógust. A **Következő** lehetőség kiválasztásával leképezheti a szükséges adatokat.

3. A **Termékszűrők** lépésben válasszon a következő lehetőségek közül.

   * **Nincsenek szűrők**: Használja a termékjavaslat előrejelzésében lévő összes terméket.

   * **Adott termékszűrők meghatározása**: Használjon a termékjavaslat előrejelzésében lévő specifikus termékeket.

1. Válassza a **Következő** lehetőséget.

1. Ha úgy dönt, hogy meghatároz egy termékszűrőt, akkor azt most kell megtennie. A **Termékkatalógus attribútumok** ablaktáblájában jelölje ki a szűrőbe foglalni kívánt attribútumokat a *Termékkatalógus entitásból*.

   :::image type="content" source="media/product-filters-sidepane.png" alt-text="Az oldalsó ablaktábla a termékkatalógus entitásban hozzárendelve látszódik a termékszűrők kiválasztásához.":::

1. Válassza ki, hogy szeretné-e, ha a termékszűrő **és** vagy **vagy** összekötőket használjon, hogy logikailag egyesítse a termékkatalógusból kiválasztott attribútumokat.
   
   :::image type="content" source="media/product-filters-sample.png" alt-text="Termékszűrők mintakonfigurációja logikai ÉS összekötőkkel kombinálva.":::

1. Válassza a **Következő** lehetőséget.

### <a name="set-update-schedule-and-review-configuration"></a>A frissítés ütemezésének és ellenőrzésének beállítása

1. Állítsa be a modell újratanításának gyakoriságát. Ez a beállítás fontos az előrejelzések pontosságának frissítéséhez, mivel a rendszer importálja az új adatokat a Customer Insightsba. A legtöbb cég havonta egyszer végez újratanítást, és pontos előrejelzésekhez tud jutni.

1. Válassza a **Következő** lehetőséget.

1. Ellenőrizze a konfigurációt. A megjelenített érték alatt lévő **Szerkesztés** beállítással az előrejelzési konfiguráció bármelyik részéhez visszaléphet. Egy másik lehetőség, hogy kiválaszt egy konfigurációs lépést a folyamatjelzőn.

1. Ha minden érték megfelelően van konfigurálva, akkor az előrejelzési folyamat indításához válassza a **Mentés és Futtatás** lehetőséget. A **Saját előrejelzések** lapon tekintheti meg az előrejelzései állapotát. A folyamat – az előrejelzésben használt adatok mennyiségétől függően – több óráig is tarthat.

## <a name="review-a-prediction-status-and-results"></a>Előrejelzés állapotának és eredményeinek áttekintése

1. Lépjen az **Információk** > **Előrejelzések** rész **Saját előrejelzések** lapjára.
   > [!div class="mx-imgBorder"]
   > ![A Saját előrejelzések oldal képe.](media/product-recommendation-mypredictions.PNG "A Saját előrejelzések oldal képe")

1. Jelölje ki az áttekinteni kívánt előrejelzést.
   - **Előrejelzés neve:** Az előrejelzés létrehozáskor megadott neve.
   - **Előrejelzés típusa:** Az előrejelzéshez használt modell típusa.
   - **Kimeneti entitás:** Az előrejelzés kimenetének tárolására szolgáló entitás neve. Az ilyen nevű entitások az **Adatok** > **Entitások** részen találhatók.    
      A kimeneti entitásban a *pontozás* az ajánlásnak egy fontos mérőszáma. A modell magasabb pontszámú termékeket ajánl az alacsonyabb pontszámú termékek helyett.
   - **Várható mező:** Ez a mező csak bizonyos típusú előrejelzések számára van megadva, és nincs használva a Termékjavaslati előrejelzésben.
   - **Állapot:** Az előrejelzés aktuális futási állapota.
        - **Feldolgozási sorban:** Az előrejelzés jelenleg más folyamatok futására vár.
        - **Frissítés:** Az előrejelzés jelenleg a feldolgozás „pontszám" fázisát futtatja, hogy eredményekhez jusson a kimeneti entitás számára.
        - **Sikertelen:** Az előrejelzés futása nem sikerült. További részletek a **Naplók** elemre kattintva érhetők el.
        - **Sikerült:** Az előrejelzés sikeresen lefutott. Az előrejelzés megtekintéséhez válassza a függőleges pontok alatt lévő **Megtekintés** lehetőséget.
   - **Szerkesztve:** Az előrejelzés konfigurációjának módosítási dátuma.
   - **Legutóbbi frissítés:** A dátum, amikor az előrejelzés frissítette a kimeneti entitásban szereplő eredményeket.

1. Kattintson a függőleges pontok ikonjára azon előrejelzés mellett, amelynek meg szeretné tekinteni az eredményeit, és kattintson a **Megtekintés** elemre.
   > [!div class="mx-imgBorder"]
   > ![A függőleges pontok menüjének beállításai az előrejelzésekhez – többek között Szerkesztés, Frissítés, Megtekintés, Naplók és Törlés.](media/product-recommendation-verticalellipses.PNG "A függőleges pontok menüjének beállításai az előrejelzésekhez – többek között Szerkesztés, Frissítés, Megtekintés, Naplók és Törlés")

1. Az eredmények oldalon öt elsődleges adatszakasz található:
    1. **Betanítási modell teljesítménye:** A lehetséges értékek: A, B vagy C. Ez a pontszám jelzi az előrejelzés teljesítményét, és könnyebbé teheti a kimeneti entitásban tárolt eredmények használatára vonatkozó döntést.
        - A pontszámok meghatározása a következő szabályok alapján történik:
            - **A** A modell figyelembe vett minősége **A** lesz, ha a „Success @ K” mérték legalább 10%-kal több, mint a kiindulási érték. 
            - **B** A modell figyelembe vett minősége **B** lesz, ha a „Success @ K” mérték legalább 0–10%-kal több, mint a kiindulási érték.
            - **C** A modell figyelembe vett minősége **C** lesz, ha a „Success @ K” mérték kevesebb, mint a kiindulási érték.
               
               > [!div class="mx-imgBorder"]
               > ![A modell teljesítményének megtekintése.](media/product-recommendation-modelperformance.PNG "A modell teljesítményének megtekintése")
            - **Alapérték**: A modell a legjobb ajánlott termékeket veszi figyelembe a vásárlások száma szerint az összes ügyfél esetében, és a modell által azonosított szabályok segítségével hozza létre az ügyfeleknek tett javaslatok egy sorát. Ezután a rendszer összeveti az előrejelzéseket a legjobb termékekkel, amit a terméket megvásárolt ügyfelek száma alapján számít. Ha egy ügyfélnek legalább egy olyan terméke van az ajánlott termékeiben, amelyek a legjobb megvásárolt termékeknél is láthatók, akkor ezek az alapérték részét jelentik. Ha ezen ügyfelek közül 10 olyan lenne, akik az ajánlott terméket a 100 teljes ügyfél közül megvásárolták, az alapérték 10%.
            - **Sikeres @ K**: A tranzakciók beállított időszakának ellenőrzésekor javaslatokat tesz a rendszer az összes ügyfél számára, és összehasonlítja a tranzakciók ellenőrzési készletével. Egy 12 hónapos időszakban például a 12. hónapot félre lehet tenni ellenőrzési adathalmazként. Ha a modell legalább egy dolgot előre jelez, amit a 12. hónapban vásárolna az előző 11 hónap során tanultak alapján, az ügyfél megnövelné a "Siker @ K" mérőszámot.
    
    1. **A leggyakrabban javasolt termékek (egyezéssel):** Az öt legjobb termék, amit előre jeleztek az ügyfeleknek.
       > [!div class="mx-imgBorder"]
       > ![A legjobb 5 ajánlott terméket bemutató grafikon.](media/product-recommendation-topproducts.PNG "A legjobb 5 ajánlott terméket bemutató grafikon")
    
    1. **A legfontosabb javaslati tényezők:** A modell az ügyfelek tranzakciós előzményei alapján tesz termékjavaslatokat. A mintákat a korábbi vásárlások alapján tanulja meg, és hasonlóságot keres az ügyfelek és a termékek között. Ezt követően a hasonlóságokat a termékre vonatkozó javaslatok létrehozásához használjuk.
    A következő tényezők befolyásolhatják a modell által létrehozott termékjavaslatot. 
        - **Múltbeli tranzakciók**: A modell korábban a termékjavaslatok előállításához felhasználta a vásárlási mintákat. A modell javasolhatja például a _Surface Arc Mouse_ használatát, ha valaki nemrég megvásárolt egy _Surface Book 3_, és egy _Surface Pent_. A modell korábban már megtanulta, hogy számos ügyfél megvásárolt egy _Surface Arc Mouse-t_, miután megvásárolt egy _Surface Book 3-at_ és egy _Surface Pent_.
        - **Ügyfélhasonlóság**: Az ajánlott terméket korábban más, hasonló vásárlási mintákat mutató ügyfelek vásárolták meg. Például Johnnak ajánlották a _Surface Headphones 2-t_, mert Jennifer és Brad nemrég vásárolt egy _Surface Headphones 2-t_. A modell szerint John hasonló Jenniferhez és Bradhez, mert korábban hasonló vásárlási mintáik voltak.
        - **Termékhasonlóság**: Az ajánlott termék hasonló az ügyfél által korábban megvásárolt termékekhez. A modell két terméket akkor tekint hasonlónak, ha azokat egyben vagy hasonló ügyfelek vásárolják meg. Például valakinek ajánlanak egy _Pendrive-ot_, mert korábban vásárolt egy _USB-C–USB Adaptert_, és a modell szerint a korábbi vásárlási minták alapján a _Pendrive_ hasonlít a _USB-C–USB Adapterhez_.

        Minden termékjavaslatot egy vagy több tényező befolyásol. A diagram ábrázolja azoknak a javaslatoknak a százalékos arányát, amelyeknél mindegyik tényező szerepet játszott. A következő példában az ajánlások 100%-át korábbi tranzakciók befolyásolták, 60%-át az ügyfélhasonlóság, 22%-át a termékhasonlóság. Menjen az egérrel a diagram sávjaira, és tekintse meg, hogy pontosan milyen százalékban játszottak szerepet a befolyásoló tényezők.

        > [!div class="mx-imgBorder"]
        > ![A legfontosabb javaslati tényezők.](media/product-recommendation-keyrecommendationfactors.png "A modell által a termékjavaslatok érdekében megtanult fő javaslati tényezők")
       
     
   1. **Adatstatisztika**: Áttekintést ad a modell által figyelembe vett tranzakciók, ügyfelek és termékek számáról. A minták megtanulásához és a termékre vonatkozó javaslatok létrehozása során használt bemeneti adatokon alapul.

      > [!div class="mx-imgBorder"]
      > ![Adatstatisztika.](media/product-recommendation-datastatistics.png "A modell által a minták elsajátítása érdekében használt kimeneti adatokra vonatkozó adatstatisztika")

      Ez a szakasz a modell által a tanulási minták elsajátításához és a termékre vonatkozó javaslatok létrehozásához használt adatpontokra vonatkozó statisztikákat mutatja be. A modellkonfigurációban konfigurált szűrés a modell által létrehozott kimeneti adatokra vonatkozik. A modell azonban a rendelkezésre álló összes adatot felhasználja a minták elsajátítása érdekében. Ezért ha a modellkonfigurációban termékszűrést használ, akkor ez a szakasz a modell által elemzett termékek teljes számát mutatja, hogy megismerje a mintákat, amelyek eltérhetnek a megadott szűrési feltételeknek megfelelő termékek számától.

   1. **Nagy magabiztosságú termékajánlások:** Az ügyfeleknek megjelenített ajánlatok egy listája, amelyekről a modell úgy gondolja, hogy az ügyfelei valószínűleg megvásárolják.    
      Ha hozzáad egy termékkatalógust, akkor a termékazonosítókat lecserélik a terméknevekre. A terméknevek használhatóbb és magától értetődőbb információkat biztosítanak az előrejelzésekről.
       > [!div class="mx-imgBorder"]
       > ![Az egyéni ügyfelek egy kiválasztott halmazára vonatkozó nagy megbízhatóságú javaslatokat mutató lista.](media/product-recommendation-highconfidence.PNG "Az egyéni ügyfelek egy kiválasztott halmazára vonatkozó nagy megbízhatóságú javaslatokat mutató lista")

## <a name="manage-predictions"></a>Előrejelzések kezelése

Lehetőség van az előrejelzések optimalizálására, hibaelhárítására, frissítésére vagy törlésére. Tekintse át a bemeneti adatok használhatósági jelentését, hogy megtudja, hogyan lehet egy előrejelzés gyorsabb és megbízhatóbb. További tudnivalókért lásd: [Előrejelzések kezelése](manage-predictions.md).


[!INCLUDE[footer-include](../includes/footer-banner.md)]
