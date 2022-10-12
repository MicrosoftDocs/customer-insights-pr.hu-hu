---
title: Tranzakciós adatváltozás előrejelzés (videót tartalmaz)
description: Megjósolja, hogy fennáll-e az ügyfélnél annak veszélye, hogy a jövőben már nem az Ön termékeit vagy szolgáltatásait vásárolja meg.
ms.date: 09/30/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: zacookmsft
ms.author: zacook
manager: shellyha
ms.openlocfilehash: fd8df0f0a168ddfab9e8ad3af9e1f1fc0bc1b7a2
ms.sourcegitcommit: be341cb69329e507f527409ac4636c18742777d2
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/30/2022
ms.locfileid: "9610515"
---
# <a name="predict-transaction-churn"></a>Tranzakció-lemorzsolódás előrejelzése

A Tranzakciós lemorzsolódási előrejelzés segít megjósolni, ha az ügyfél valószínűleg többé már nem fogja megvásárolni az Ön termékeit vagy szolgáltatásait egy adott játékablakon belül.

Üzleti ismeretekkel kell rendelkeznie ahhoz, hogy megértse, mit jelent a lemorzsolódás a vállalkozása számára. Az idő alapú lemorzsolódás meghatározást támogatjuk, ami azt jelenti, hogy az ügyfelet lemorzsolódottnak tekintjük, egy meghatározott vásárlás nélkül eltelt idő után.

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWN6Eg]

Üzleti partnereken alapuló környezet esetén a partnerek esetében tranzakciós lemorzsolódást, valamint a partnerek és más szintű információk, például a termékkategóriák kombinációját is megjósolhatjuk. Például egy dimenzió hozzáadása segíthet meghatározni, hogy mennyire valószínű, hogy a "Contoso" fiók leállítja az "irodai írószerek" termékkategória megvásárlását. Ezenkívül az üzleti partnerek esetében az AI segítségével összeállíthatjuk azoknak a lehetséges okoknak a listáját, amelyek miatt a partner valószínűleg lemorzsolódik a másodlagos szintű információk kategóriája miatt.

> [!TIP]
> Próbálja ki a tranzakciós adatváltozást előrejelzés mintaadatokkal: [Tranzakciós adatváltozás előrejelzés mintaútmutató](sample-guide-predict-transactional-churn.md).

## <a name="prerequisites"></a>Előfeltételek

- Legalább [közreműködői engedélyek](permissions.md).
- Legalább 10 ügyfélprofil, lehetőleg több mint 1,000 egyedi ügyfél.
- Ügyfél-azonosító, egy egyedi azonosító, amely megfelelteti a tranzakciókat az ügyfeleknek.
- Tranzakciós adatok a kiválasztott időablak legalább kétszeresére, például két-három éves tranzakciós előzményekre. Ideális esetben ügyfelenként legalább két tranzakció. A tranzakciós előzményeknek tartalmazniuk kell a következőket:
  - **Tranzakcióazonosító**: Egy vásárlás vagy tranzakció egyedi azonosítója.
  - **Tranzakció dátuma**: A vásárlás vagy tranzakció dátuma.
  - **A tranzakció** értéke: A tranzakció pénzneme vagy számértéke.
  - **Egyedi termékazonosító**: A megvásárolt termék vagy szolgáltatás azonosítója, ha az adatok sorszinten vannak.
  - **Hogy ez a tranzakció hozam** volt-e: Igaz/hamis mező, amely azonosítja, hogy a tranzakció hozam volt-e vagy sem. Ha a **tranzakció** értéke negatív, akkor hozamra következtetünk.
- Ügyféltevékenységi adatok:
  - Ügyfél-azonosító, egy egyedi azonosító, amellyel a tevékenységeket leképezheti az ügyfelekre.
  - **Elsődleges kulcs:** Egy tevékenység egyedi azonosítója. Például, ha egy webhelylátogatás vagy egy használati rekord azt mutatja, hogy az ügyfél kipróbálta az egyik mintatermékét.
  - **Időbélyegző:** Az elsődleges kulccsal azonosított esemény dátuma és időpontja.
  - **Esemény:** A használni kívánt esemény neve. Például, ha egy mező neve "FelhasználóiMűvelet" egy élelmiszerboltban, ez egy ügyfél által történő kuponhasználatot jelenthet.
  - **Részletek:** Részletes információk az eseményről. Például, ha egy mező neve "KuponÉrték" egy élelmiszerboltban, ez a kupon pénznembeli értékét jelentheti.
- A hiányzó értékek kevesebb mint 20%-a a megadott entitás adatmezőjében

Üzleti fiókok (B-től B-ig) esetén adjon hozzá statikusabb attribútumokhoz igazított ügyféladatokat, hogy a modell a legjobban teljesítsen:
- **Ügyfél-azonosító:** Egy ügyfél egyedi azonosítója.
- **Létrehozás dátuma:** Az ügyfél kezdeti hozzáadásának dátuma.
- **Állam vagy tartomány:** Az ügyfél állama vagy tartományának helye.
- **Ország:** Az ügyfél országa.
- **Iparág:** Az ügyfél iparági típusa. A kávékatarazóban az "Iparág" nevű mező például arra utalhat, hogy kiskereskedelmi értékesítésben volt-e az ügyfél.
- **Besorolás:** Az ügyfél kategorizálása a vállalkozás számára. Például egy kávéfőző "ValueSegment" nevű mezője lehet az ügyfél szintje a vevő mérete alapján.

> [!NOTE]
> A nagy ügyfélvásárlási gyakoriságú (néhány hetes) üzleti tevékenység esetén ajánlott rövidebb előrejelzési ablak és lemorzsolódás meghatározását választani. Az alacsony vásárlási gyakoriság (néhány havonta vagy évente egyszer) esetén válasszon hosszabb előrejelzési ablakot és lemorzsolódást.

## <a name="create-a-transaction-churn-prediction"></a>Tranzakciólemorzsolódási előrejelzés létrehozása

1. Ugrás az Intelligencia-előrejelzések **oldalra** > **·**.

1. A Létrehozás lapon válassza a **Modell** használata lehetőséget **az** Ügyfél adatváltozás modelljének csempéjén **.**

1. Válassza a Tranzakció lehetőséget **a lemorzsolódás típusához, majd** az Első lépések lehetőséget **.**

1. **Nevezze el ezt a modellt** és a **Kimeneti entitás nevét**, hogy megkülönböztesse őket az egyéb modellektől vagy entitásoktól.

1. Válassza a **Következő** lehetőséget.

### <a name="define-customer-churn"></a>Ügyfél-lemorzsolódás meghatározása

Válassza a Piszkozat **mentése bármikor lehetőséget** a előrejelzés piszkozatként való mentéséhez. A piszkozat előrejelzés a **Saját előrejelzések** lapon jelenik meg.

1. Állítsa be a **előrejelzés ablakot**. Például, megjósolhatja a lemorzsolódás kockázatát egy ügyfele esetében, a következő 90 napban, hogy ehhez igazíthassa marketingmegőrzési törekvéseit. A lemorzsolódási kockázat becslése egy hosszabb vagy rövidebb időintervallumra megnehezítheti a tényezők kezelését a lemorzsolódási kockázat-profiljában, de ez leginkább az Ön által meghatározott üzleti igényektől függ.

1. Adja meg a lemorzsolódás definiálásához szükséges napok számát a **Churn definíciója** mezőben. Ha például egy ügyfél az elmúlt 30 napban nem vásárolt, akkor úgy tekinthető, hogy a vállalkozása számára lemorzsolódott.

1. Válassza a **Következő** lehetőséget.

### <a name="add-purchase-history"></a>Vásárlási előzmények hozzáadása

1. Válassza az Adatok hozzáadása lehetőséget **az Ügyfél tranzakciós előzményeihez** **.**

1. Válassza ki a tranzakciós előzmények adatait tartalmazó salesorder **vagy** salesorderline **szemantikai tevékenységtípust**. Ha a tevékenység nincs beállítva, válassza ki **itt**, és hozza létre.

1. Ha a Tevékenységek **alatt** a tevékenységattribútumok szemantikailag leképeződtek a tevékenység létrehozásakor, válassza ki azokat az attribútumokat vagy entitásokat, amelyekre a számítást összpontosítani szeretné. Ha a szemantikai leképezés nem történt meg, válassza az Adatok szerkesztése **és leképezése lehetőséget**.

   :::image type="content" source="media/transaction-churn-select-activity.PNG" alt-text="A szemantikus típus alatti tevékenységek kiválasztását bemutató oldalsó panel.":::

1. Válassza a Tovább **lehetőséget**, és tekintse át a modellhez szükséges attribútumokat.

1. Válassza a **Mentés** parancsot.

1. Adjon hozzá további tevékenységeket, vagy válassza a Tovább **lehetőséget**.

# <a name="individual-consumers-b-to-c"></a>[Egyéni fogyasztók (B-to-C)](#tab/b2c)

### <a name="add-additional-data-optional"></a>További adatok hozzáadása (nem kötelező)

1. Válassza az Adatok **hozzáadása az** ügyféltevékenységekhez **lehetőséget**.

1. Válassza ki a használni kívánt adatokat tartalmazó szemantikai tevékenységtípust. Ha a tevékenység nincs beállítva, válassza ki **itt**, és hozza létre.

1. Ha a Tevékenységek **alatt** a tevékenységattribútumok szemantikailag leképeződtek a tevékenység létrehozásakor, válassza ki azokat az attribútumokat vagy entitásokat, amelyekre a számítást összpontosítani szeretné. Ha a szemantikai leképezés nem történt meg, válassza az Adatok szerkesztése **és leképezése lehetőséget**.

1. Válassza a Tovább **lehetőséget**, és tekintse át a modellhez szükséges attribútumokat.

1. Válassza a **Mentés** parancsot.

1. Válassza a **Tovább** lehetőséget

# <a name="business-accounts-b-to-b"></a>[Üzleti számlák (B-to-B)](#tab/b2b)

### <a name="select-prediction-level"></a>Előrejelzési szint kiválasztása

A legtöbb előrejelzés ügyfélszinten jön létre. Bizonyos esetekben előfordulhat, hogy az üzleti igényeihez nem elég granulált. Ezzel a funkcióval előrejelezheti például az ügyfél egy ágának lemorzsolódását, nem pedig az ügyfél egészére vonatkozóan.

1. Válassza az Entitás kiválasztása másodlagos szinthez **lehetőséget**. Ha a lehetőség nem érhető el, győződjön meg arról, hogy befejezte az előző szakaszt.

1. Bontsa ki azt az entitást, amelyből ki szeretné választani a másodlagos szintet, vagy használja a keresési szűrőt a kiválasztott beállítások szűréséhez.

1. Válassza ki a másodlagos szintként használni kívánt attribútumot, majd válassza a **Hozzáadás** lehetőséget.

1. Válassza a **Következő** lehetőséget.

> [!NOTE]
> Az ebben a szakaszban elérhető entitások azért jelennek meg, mert kapcsolatban állnak az előző részben kiválasztott entitással. Ha nem látja a hozzáadni kívánt entitást, győződjön meg arról, hogy érvényes kapcsolat van a **Kapcsolatokban**. A konfigurációhoz csak egy-az-egyhez és sok-az-egyhez kapcsolatok érvényesek.

### <a name="add-additional-data-optional"></a>További adatok hozzáadása (nem kötelező)

1. Válassza az Adatok **hozzáadása az** ügyféltevékenységekhez **lehetőséget**.

1. Válassza ki a használni kívánt adatokat tartalmazó szemantikai tevékenységtípust. Ha a tevékenység nincs beállítva, válassza ki **itt**, és hozza létre.

1. Ha a Tevékenységek **alatt** a tevékenységattribútumok szemantikailag leképeződtek a tevékenység létrehozásakor, válassza ki azokat az attribútumokat vagy entitásokat, amelyekre a számítást összpontosítani szeretné. Ha a szemantikai leképezés nem történt meg, válassza az Adatok szerkesztése **és leképezése lehetőséget**.

1. Válassza a Tovább **lehetőséget**, és tekintse át a modellhez szükséges attribútumokat.

1. Válassza a **Mentés** parancsot.

1. Válassza a **Tovább** lehetőséget

1. Ha szükséges, válassza az **Adatok hozzáadása** az **Ügyféladatokhoz** lehetőséget.

1. A szemantikus attribútumokat a saját ügyféladatok mezőire leképezi az azonosítottak szerint. A felhasznált mezők adatai nem változhatnak, gyakran a modell optimális teljesítménye érdekében. Például ha kiválaszt egy olyan mezőt az "Osztályozás" számára, amely minden hónapban megváltozott, csak az előrejelzés utolsó értékét használja, annak ellenére, hogy előzményileg ugyanaz az érték nem érvényes a vevőre az előrejelzési minták építésekor.

1. Válassza a **Következő** lehetőséget.

### <a name="provide-an-optional-list-of-benchmark-accounts"></a>Referenciapartnerek nem kötelező listájának megadása

Adja meg a referenciaként használni kívánt üzleti ügyfelek és partnerek listáját. [Ezeknek a benchmark számláknak](#view-prediction-results) a részletei közé tartozik a lemorzsolódási pontszámuk és a legbefolyásosabb jellemzők, amelyek hatással voltak a lemorzsolódási előrejelzés.

1. Válasza ki a **+ Ügyfél hozzáadása** lehetőséget.

1. Válassza ki a referenciaként használt ügyfeleket.

1. Válassza a **Következő** lehetőséget.

---

### <a name="set-update-schedule"></a>Frissítési ütemezés beállítása

1. Az Adatfrissítések **lépésben válassza ki a** modell újratanításának gyakoriságát. Ez a beállítás fontos az előrejelzések pontosságának frissítéséhez, mivel a rendszer új adatokat tölt be a Customer Insights szolgáltatásba. A legtöbb cég havonta egyszer végez újratanítást, és pontos előrejelzésekhez tud jutni.

1. Válassza a **Következő** lehetőséget.

### <a name="review-and-run-the-model-configuration"></a>A modellkonfiguráció áttekintése és futtatása

Az **Áttekintés és futtatás** lépés a konfiguráció összegzését jeleníti meg, és lehetőséget biztosít a módosítások elvégzésére a előrejelzés létrehozása előtt.

1. Válassza a Szerkesztés **lehetőséget** az áttekintéshez és a módosítások elvégzéséhez szükséges lépések bármelyikénél.

1. Ha elégedett a választásokkal, válassza a Mentés és futtatás **lehetőséget** a modell futtatásának megkezdéséhez. Válassza a **Kész** lehetőséget. A **Saját előrejelzések** lap a előrejelzés létrehozásakor jelenik meg. A folyamat – az előrejelzésben használt adatok mennyiségétől függően – több óráig is tarthat.

[!INCLUDE [progress-details](includes/progress-details-pane.md)]

## <a name="view-prediction-results"></a>Előrejelzés eredmények megtekintése

1. Ugrás az Intelligencia-előrejelzések **oldalra** > **·**.

1. **A Saját előrejelzések** lapon válassza ki a megtekinteni kívánt előrejelzés.

# <a name="individual-consumers-b-to-c"></a>[Egyéni fogyasztók (B-to-C)](#tab/b2c)

Az eredményoldalon lévő adatok három fő részben jelennek meg:

[!INCLUDE [predict-transaction-results](includes/predict-transaction-results.md)]

# <a name="business-accounts-b-to-b"></a>[Üzleti számlák (B-to-B)](#tab/b2b)

Az eredményoldalon lévő adatok három fő részben jelennek meg:

[!INCLUDE [predict-transaction-results](includes/predict-transaction-results.md)]

A **befolyásos jellemzőelemzési** információs oldal az adatok négy részéből áll:

- A jobb oldali ablaktáblában válasszon ki egy elemet a **Legnépszerűbb ügyfelek** vagy **az Ügyfelek összehasonlítása közül**. A két lista csökkenő lemorzsolódási értékkel van megrendelve, attól függően, hogy a pontszám csak az ügyfélnek, vagy egy összesített pontszámnak megfelelő az igénybe vett számára, valamint egy másodlagos szint, például a termékkategória. A kiválasztott elem határozza meg az oldal tartalmát.

  - **A legjobb ügyfelek**: 10 olyan ügyfélből állnak, akik a legnagyobb ki vannak tévelyedve, és a legalacsonyabb a úúgó pontszámok alapján.
  - **Teljesítményteszt-ügyfelek**: A modell konfigurálásakor kiválasztott legfeljebb 10 ügyfél listája.

- **Lesiklott pontszám**: A jobb oldali ablaktáblában kiválasztott elem lemorzsolódási pontszámának megjelenítése.

- **Lemorzsolódási kockázat eloszlása:** Megjeleníti a lemorzsolódási kockázat eloszlását az ügyfelek között, valamint azt a percentilist, amelyben a kiválasztott ügyfél van.

- **A lemorzsolódási kockázatot növelő és csökkenő legfontosabb funkciók:** Felsorolja az öt legfontosabb jellemzőt, amelyek növelték és csökkentették a kiválasztott elem lemorzsolódási kockázatát a jobb oldali ablaktáblában. Megjeleníti az adott elem jellemzőjének értékét és annak hatását az egyes befolyásos jellemzők lemorzsolódási pontszámára. Az egyes szolgáltatások átlagos értéke alacsony, közepes és magas ügyfélszegmensenként is megjelenik. Segít jobban kontextusba helyezni a kiválasztott elemre gyakorolt legnagyobb hatású szolgáltatások értékeit, és összehasonlítani az alacsony, közepes és nagy forgalmú ügyfélszegmensekkel.

  - Alacsony: a számla vagy a számla és a másodlagos szint kombinációi 0 és 0,33 közötti lemorzsolódási pontszámmal.
  - Közepes: számlák vagy számlák és másodlagos szintek kombinációi, amelyek lemorzsolódási pontszáma 0,33 és 0,66 között van.
  - Magas: 0,66-nál nagyobb lemorzsolódási pontszámmal rendelkező számlák vagy számlák és másodlagos szintek kombinációi.

  Amikor a partnerek szintjén előrejelzi a lemorzsolódástt, minden egyes partnert figyelembe kell venni a lemorzsolódási szegmensek átlagos funkcióértékének összefésülésében. A másodlagos szinten minden egyes fióknál a lemorzsolódási szegmensek kijelzése az oldalpanelen kiválasztott elem másodlagos szintjétől függ. Ha például egy cikknek másodlagos szintű termékkategóriája van (irodaszerek), akkor csak azokat a cikkeket veszi figyelembe a rendszer, amelyek termékkategóriájaként irodaszereket tartalmaznak, amikor a lemorzsolódási szegmensek átlagos jellemzőértékeit származtatjuk. Ez a logika biztosítja, hogy a program megfelelő összehasonlítást alkalmaz a elem funkcióértékeivel az alacsony, közepes és nagy lemorzsolódási szegmensek átlagos értékeivel.

  Bizonyos esetekben az alacsony, közepes vagy nagy lemorzsolódási szegmensek átlagos értéke üres vagy nem érhető el, mivel a fenti definíció alapján nem érhetők el elemek, amelyek a megfelelő piaci szegmenshez tartoznak.

  Az átlagos alacsony, a közepes és a magas oszlopok alatti értékek értelmezése eltérő a kategorikus funkciók (például az ország vagy az iparág) esetében. Mivel az „átlag” funkcióérték nem vonatkozik a kategorikus funkciókra, az ezekben az oszlopokban található értékek az alacsony, a közepes vagy a magas lemorzsolódási szegmensek olyan hányadai, amelyek a kategorikus funkcióval azonos értékkel rendelkeznek az oldalpanelen kiválasztott elemhez képest.

---

 > [!NOTE]
 > A modell kimeneti entitásában a ChurnScore *a lemorzsolódás előrejelzett valószínűségét, az IsChurn* pedig *egy bináris címke,* amely a ChurnScore-on *alapul*, 0,5 küszöbértékkel. Ha ez az alapértelmezett küszöbérték nem működik a forgatókönyvben, [hozzon létre egy új szegmenst](segments.md#create-a-segment) az előnyben részesített küszöbértékkel. Nem minden ügyfél feltétlenül aktív ügyfél. Némelyikük lehet, hogy már hosszú ideje nem végzett tevékenységet, és a már lemorzsolódottnak számít – az Ön lemorzsolódási definíciójától függően. A már lemorzsolódott ügyfeleknél a lemorzsolódási kockázat előrejelzése nem hasznos, mert nem ők az érdeklődő célközönség.
>
> A adatváltozási pontszám megtekintéséhez lépjen az **Adatentitások** > **elemre**, és tekintse meg a modellhez definiált kimeneti entitás adatok lapját.

[!INCLUDE [footer-include](includes/footer-banner.md)]
