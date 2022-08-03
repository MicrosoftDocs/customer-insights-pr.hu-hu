---
title: Javasolt szegmensek mérték alapján (előzetes verzió)
description: Az gépi tanulás segíthet megtalálni új és érdekes szegmenseket az ügyfélattribútumok alapján.
ms.date: 10/15/2021
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: JimsonChalissery
ms.author: jimsonc
manager: shellyha
searchScope:
- ci-segment-suggestions
- customerInsights
ms.openlocfilehash: e3f504827029afa12c65ec6f065a62606aaa823f
ms.sourcegitcommit: 8a28e9458b857adf8e90e25e43b9bc422ebbb2cd
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/18/2022
ms.locfileid: "9170960"
---
# <a name="suggested-segments-based-on-measures-preview"></a>Javasolt szegmensek mérték alapján (előzetes verzió)

Az ügyfelek érdekes szegmenseit fedezheti fel egy AI-modell segítségével. Ez gépi tanulás alapú funkció mérőszámok vagy ügyfélattribútumok alapján javasol szegmenseket. Segíthet a fő teljesítménymutatók (KPI-k) javításában, vagy jobban megértheti az attribútumok hatását más attribútumok kontextusában.

> [!NOTE]
> A javasolt szegmensek funkció automatizált eszközöket használ az adatok kiértékeléséhez és az adatokon alapuló előrejelzések készítéséhez. Ezért képes profilalkotási módszerként használni, mivel ezt a kifejezést az általános adatvédelmi rendelet (a továbbiakban: GDPR) határozza meg. A szolgáltatásnak az adatok feldolgozására való használatára a GDPR vagy más törvények vagy előírások vonatkozhatnak. Felelős azért, hogy biztosítsa, hogy a Dynamics 365 Customer Insights használata, ezzel a funkcióval együtt, megfeleljen a vonatkozó törvényeknek és szabályozásoknak, többek között az adatvédelemmel, személyes adatokkal, biometrikus adatokkal, adatok védelmével és a kommunikáció titkosságával kapcsolatos törvényeknek.

:::image type="content" source="media/suggested-segments.png" alt-text="A javasolt szegmensek oldala, ahol megjelennek az oldalpanelen lévő javaslatok részletei.":::

## <a name="suggested-segments-to-improve-your-kpis"></a>A fő teljesítménymutatók javítására javasolt szegmensek

Ha a KPI-k nyomon követésére létrehozott [mértékeket használ](measures.md), hozzon létre szegmenseket a KPI-re gyakorolt hatások megtekintéséhez. Ezeket az információkat felhasználhatja egy erősen célzott kampány futtatására.

Például egy *TotalSpendPerCustomer* nevű mérőszámot követ nyomon. Vállalatként szeretné látni, hogy ez a szám nő. Ha egy mértéket választ elsődleges attribútumként, válassza ki azokat az attribútumokat, amelyeket hatás szempontjából értékelni szeretne. Tegyük fel, hogy a *tagsági szint*, a *tagsági időszak* és *foglalkozás*. Ezután a Customer Insights javasolhat egy olyan szegmenst, amely közli, hogy ki gyakorolja a legnagyobb befolyást a mértékre. Például a *TotalSpendPerCustomer* legnagyobb befolyással bíró tagja *könyvelők*, akik *Arany* tagok, és akik már *legalább öt éve* vannak a vállalatában. Minden javaslathoz becsült szegmensméretet kap. Ezen információk segítségével kampányokat hozhat létre a célközönség számára.

## <a name="understand-what-influences-a-customer-attribute"></a>Az ügyfélattribútumokat befolyásoló tényezők

A mérőszám helyett választhat ügyfélattribútumot is elsődleges attribútumként. Az AI-modell a kiválasztott befolyásoló attribútumok alapján egy sor javaslatot hoz létre, amelyek megmutatják, hogy a kijelölt attribútumok hogyan befolyásolják az elsődleges attribútumot.

Elsődleges attribútumként például a *Jutalomprogram tagja (Igen/Nem)* lehetőséget választja. A *Hivatali idő*, *Foglalkozás* és a *Támogatási jegyek száma* vannak beállítva további befolyásoló attribútumokként. Az AI modell javasolhat olyan szegmenseket, amelyek leginkább két évnél hosszabb hivatali idővel rendelkező informatikai szakembereket mutatnak, aki jutalomprogram tagok. Egy másik javaslat azt mutathatja, hogy az egy évnél rövidebb hivatali idővel és háromnál kevesebb támogatási jegyekkel rendelkező könyvelők a kedvezményezett tagok.

## <a name="artificial-intelligence-usage"></a>A Mesterséges intelligencia használata

A döntési fa algoritmusa az elsődleges attribútumok és a befolyásoló attribútumok használatával javasol bizonyos szegmenseket. A javaslatok az AI-algoritmus által felvett szabályokon vagy mintákon alapulnak. Javaslatokként csak azok a szegmensek jelennek meg, amelyek jelentősen eltérnek az átlagos populációtól. Az átlagos populációval való összehasonlítás a kiválasztott mértéken vagy elsődleges attribútumon alapul.

### <a name="responsible-ai"></a>Felelős AI

A javasolt szegmensek esetében attribútumokat választ ki új szegmensek létrehozásához és a kiválasztott adatok feldolgozásához. Az attribútumok, beleértve az érzékeny természetű attribútumokat például a faj, a szexuális beállítottság vagy gondoskodnia kell arról, hogy az adatokat fel szabad dolgoznia és szükséges is azok feldolgozása. Ön a felelős azért, hogy megfeleljen a szervezetre vonatkozó törvényeknek, valamint be kell tartania a szervezete irányelveit és adatvédelmi irányelveit.

### <a name="different-results-for-primary-attributes-with-categorical-and-numeric-values"></a>Kategoriális és numerikus értékeket tartalmazó elsődleges attribútumok eltérő eredményei

A szegmensjavaslatok eltérőek, ha elsődleges attribútumként egy numerikus vagy egy kategoriális attribútumot választ. A kategoriális attribútum értékei két vagy több kategóriát vagy típust tartalmaznak. A numerikus attribútumok kvantitatív adatokat tartalmaznak, és hozzájuk van társítva mértékegység.

Ha az elsődleges attribútumként egy numerikus attribútum, például az *éves jövedelem* vagy a *tagsági időszak*, a rendszer olyan szegmenseket javasol, amelyek az összes ügyfélhez képest magasabb vagy alacsonyabb átlagértékkel bírnak.

Egy kategoriális attribútum, mint például az *ügyfél-elégedettség* mint elsődleges attribútum, olyan javasolt szegmenseket eredményez, amelyeknél az adott kategóriába tartozó ügyfelek aránya az adott kategóriába tartozó összes ügyfélhez képest magasabb vagy kisebb százalékú. Elsődleges attribútumként például az *ügyfél-elégedettséget* választja, amely három kategóriát tartalmaz (*Alacsony*, *Közepes* és *Magas*). Minden egyes kategória esetében olyan szegmenseket javasolunk, amelyek esetében magasabb vagy alacsonyabb az adott kategóriába tartozó ügyfelek aránya, mint az azonos kategóriába tartozó összes vevő aránya. Ha az ügyfelek 22%-ánál *Magas* az elégedettség szintje, akkor csak azok a szegmensek lesznek javasolva az adott kategóriához, amelyeknél magasabb vagy kisebb arányban vannak *Magas* magas elégedettségű ügyfelek a 22%-hoz képest. Az egyéb kategóriák (*Alacsony* és *Közepes*) esetében is javasolva lesznek szegmensek, amennyiben statisztikailag szignifikánsak.

> [!NOTE]
> Jelenleg csak az elsődleges kategorikus attribútumokat támogatjuk, amelyek legfeljebb 10 kategóriát tartalmaznak. Ha 10-nél több kategóriát tartalmazó elsődleges attribútumon alapuló szegmensjavaslatokat szeretne látni, javasoljuk, hogy egyes kategóriákat csoportosítson, hogy a kategóriák számát 10-re vagy annál kevesebbre csökkentse. Ez a korlátozás csak az elsődleges attribútumok esetén érvényes. A befolyásoló kategoriális attribútumokhoz jelenleg legfeljebb 100 kategóriát támogatunk.

## <a name="generate-suggested-segments"></a>Javasolt szegmensek létrehozása

1. Lépjen a Szegmensek **elemre,** és válassza a **Javaslatok (előnézet)** lapot.

1. Válassza az Új javaslatok **keresése,** majd a Mérték/mutató javítása **lehetőséget**. Válassza a Start **gombot**.

   :::image type="content" source="media/suggested-segments-measure.png" alt-text="A javasolt szegmensek javító intézkedésének kiválasztása.":::

1. Válasszon ki egy vevőattribútumot vagy mértéket elsődleges attribútumként, majd válassza a Tovább **lehetőséget**.

1. Válassza ki a befolyásoló attribútumokat, majd válassza a Futtatás **lehetőséget**.

   > [!TIP]
   > Több befolyásoló attribútum kiválasztásával nagyobb az esélye annak, hogy értékelve lesz, hogyan befolyásolják az elsődleges attribútumot. Ne használjon olyan attribútumokat, amelyek nincsenek hatással az elsődleges attribútumra. Ha például minden ügyfele egy adott országhoz tartozik, ne szerepeljen az *ország* attribútum, mivel az nem lesz hatással a kimenetre.

Az ügyfélprofilok és a kijelölt attribútumok számától függően a kijelölt attribútumok feldolgozása eltarthat néhány percig.

## <a name="manage-suggested-segments"></a>Javasolt szegmensek kezelése

Lépjen a Szegmensek **elemre,** és válassza a **Javaslatok (előnézet)** lapot. **Az Attribútumalapú szegmensjavaslatok** szakaszban válasszon ki egy javasolt szegmenst a rendelkezésre álló műveletek megtekintéséhez.

- **Tekintse meg** a javasolt szegmens részleteit és az AI-modell által megtanult attribútumértékeket vagy szabályokat.
- **Mentse szegmentáltként** a javaslatot szegmensként. Megjelenik a **Minden szegmens** lapon, és frissíthető [, szerkeszthető vagy törölhető](segments.md).
- **Szerkessze az attribútumokat**, és módosítsa a konfigurált attribútumokat, amelyek felváltják az aktuális javaslatokat.
- **Frissítse a javaslatokat** a javaslatok frissítéséhez a konfigurált attribútumok megtartása mellett.

## <a name="limitations"></a>Korlátozások

1. Becsült szegmensméret nem egyezik: Ha olyan elsődleges attribútumot választ, amely üres értékeket tartalmaz, akkor az befolyásolhatja a szegmensjavaslatok becsült szegmensméretét. Az ilyen szegmensek mentésekor a szegmens tényleges mérete más lehet, mint az eredeti szegmens mérete.

2. A logikai típusú elsődleges attribútumok nem működnek: Jelenleg csak a karakterlánc- és numerikus típusú adatokat támogatjuk elsődleges attribútumként.

3. A javasolt szegmensek nem elég különbözőek: Ne feledje, hogy a kijelölt attribútumok és az attribútumok értékeinek eloszlása befolyásolja az eredményeket. A különböző eredmények eléréséhez módosíthatja a befolyásoló attribútumokat vagy akár az elsődleges attribútumot is.

[!INCLUDE [footer-include](includes/footer-banner.md)]