---
title: Gépitanulás-alapú ajánlott szegmensek
description: Az gépi tanulás segíthet megtalálni új és érdekes szegmenseket az ügyfélattribútumok alapján.
ms.date: 02/01/2021
ms.reviewer: jimsonc
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: 54655d57f4f0f723b497fe47891fd397ccb9dbf4
ms.sourcegitcommit: 139548f8a2d0f24d54c4a6c404a743eeeb8ef8e0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/15/2021
ms.locfileid: "5268229"
---
# <a name="suggested-segments-preview"></a>Javasolt szegmensek (előzetes verzió)

Az ügyfelek érdekes szegmenseit fedezheti fel egy AI-modell segítségével. Ez gépi tanulás alapú funkció mérőszámok vagy ügyfélattribútumok alapján javasol szegmenseket. Segíthet a fő teljesítménymutatók javításában, illetve az attribútumok más attribútumokkal kontextusában gyakorolt hatásának jobb megértésében. 

> [!NOTE]
> A javasolt szegmensek funkció automatizált eszközöket használ az adatok kiértékeléséhez és az adatok alapján történő előrejelzéséhez, ezért megvan a képessége, hogy profilkészítési módszerként használható legyen, az Általános adatvédelmi rendelet („GDPR”) által meghatározott értelemben. A szolgáltatásnak az adatok feldolgozására való használatára a GDPR vagy más törvények vagy előírások vonatkozhatnak. Felelős azért, hogy biztosítsa, hogy a Dynamics 365 Customer Insights használata, ezzel a funkcióval együtt, megfeleljen a vonatkozó törvényeknek és szabályozásoknak, többek között az adatvédelemmel, személyes adatokkal, biometrikus adatokkal, adatok védelmével és a kommunikáció titkosságával kapcsolatos törvényeknek.

:::image type="content" source="media/suggested-segments-details.png" alt-text="A Customer Insights javasolt szegmensek oldala egy oldalpanelen mutatja a javaslatok részleteit.":::

## <a name="suggested-segments-to-improve-your-kpis"></a>A fő teljesítménymutatók javítására javasolt szegmensek

A célközönséggel kapcsolatos információk felhasználójaként nagy valószínűséggel [hozott létre olyan intézkedéseket](measures.md), amelyek segítségével nyomon követhetők a fő teljesítménymutatók (KPI-k). Fontos megérteni, hogy bizonyos attribútumok hogyan befolyásolják ezt a fő teljesítménymutatót szegmensek létrehozásában és egy erősen célzott kampány futtatásában.   
Például egy *TotalSpendPerCustomer* nevű mérőszámot követ nyomon. Vállalatként szeretné látni, hogy ez a szám nő. Ha egy mértéket elsődleges attribútumként választ ki, kiválaszthatja azokat az attribútumokat, amelyeket a befolyás szempontjából mérni szeretne. Tegyük fel, hogy a *tagsági szint*, a *tagsági időszak* és *foglalkozás*. Ezután a Customer Insights javasolhat egy olyan szegmenst, amely közli, hogy ki gyakorolja a legnagyobb befolyást a mértékre. Például a *TotalSpendPerCustomer* legnagyobb befolyással bíró tagja *könyvelők*, akik *Arany* tagok, és akik már *legalább öt éve* vannak a vállalatában. Minden javaslathoz becsült szegmensméretet kap. Ezen információk segítségével kampányokat hozhat létre a célközönség számára.

## <a name="understand-what-influences-a-customer-attribute"></a>Az ügyfélattribútumokat befolyásoló tényezők

A mérőszám helyett választhat ügyfélattribútumot is elsődleges attribútumként. Az AI-modell a kiválasztott befolyásoló attribútumok alapján egy sor javaslatot hoz létre, amelyek megmutatják, hogy a kijelölt attribútumok hogyan befolyásolják az elsődleges attribútumot.   
Elsődleges attribútumként például a *Jutalomprogram tagja (Igen/Nem)* lehetőséget választja. A *Hivatali idő*, *Foglalkozás* és a *Támogatási jegyek száma* vannak beállítva további befolyásoló attribútumokként. Az AI modell javasolhat olyan szegmenseket, amelyek leginkább két évnél hosszabb hivatali idővel rendelkező informatikai szakembereket mutatnak, aki jutalomprogram tagok. Egy másik javaslat azt mutathatja, hogy az egy évnél rövidebb hivatali idővel és háromnál kevesebb támogatási jegyekkel rendelkező könyvelők a kedvezményezett tagok. 

## <a name="artificial-intelligence-usage"></a>A Mesterséges intelligencia használata

A döntési fa algoritmusa az elsődleges attribútumok és a befolyásoló attribútumok használatával javasol bizonyos szegmenseket. A javaslatok az AI-algoritmus által felvett szabályokon vagy mintákon alapulnak. Javaslatokként csak azok a szegmensek jelennek meg, amelyek jelentősen eltérnek az átlagos populációtól. Az átlagos populációval való összehasonlítás a kiválasztott mértéken vagy elsődleges attribútumon alapul.

### <a name="responsible-ai"></a>Felelős AI

A javasolt szegmensek lehetővé teszi, hogy új szegmensek létrehozásához és a kiválasztott adatok feldolgozásához attribútumokat válasszon. Az attribútumok, beleértve az érzékeny természetű attribútumokat például a faj, a szexuális beállítottság vagy gondoskodnia kell arról, hogy az adatokat fel szabad dolgoznia és szükséges is azok feldolgozása. Ön a felelős azért, hogy megfeleljen a szervezetre vonatkozó törvényeknek, valamint be kell tartania a szervezete irányelveit és adatvédelmi irányelveit.

### <a name="different-results-for-primary-attributes-with-categorical-and-numeric-values"></a>Kategoriális és numerikus értékeket tartalmazó elsődleges attribútumok eltérő eredményei

A szegmensjavaslatok eltérőek, ha elsődleges attribútumként egy numerikus vagy egy kategoriális attribútumot választ. A kategoriális attribútum értékei két vagy több kategóriát vagy típust tartalmaznak. A numerikus attribútumok kvantitatív adatokat tartalmaznak, és hozzájuk van társítva mértékegység.

Ha az elsődleges attribútumként egy numerikus attribútum, például az *éves jövedelem* vagy a *tagsági időszak*, a rendszer olyan szegmenseket javasol, amelyek az összes ügyfélhez képest magasabb vagy alacsonyabb átlagértékkel bírnak.

Egy kategoriális attribútum, mint például az *ügyfél-elégedettség* mint elsődleges attribútum, olyan javasolt szegmenseket eredményez, amelyeknél az adott kategóriába tartozó ügyfelek aránya az adott kategóriába tartozó összes ügyfélhez képest magasabb vagy kisebb százalékú. Elsődleges attribútumként például az *ügyfél-elégedettséget* választja, amely három kategóriát tartalmaz (*Alacsony*, *Közepes* és *Magas*). Az egyes kategóriák esetében olyan szegmensek lesznek javasolva, amelyeknél az adott kategóriába tartozó ügyfelek százaléka jóval magasabb vagy alacsonyabb az ugyanabban a kategóriában található összes ügyfél arányával összehasonlítva. Ha az ügyfelek 22%-ának elégedettsége *Magas*, akkor csak azok a szegmensek javasoltak az adott kategóriához, amelyekben jóval magasabb vagy kisebb arányban vannak a *Magas* elégedettségű ügyfelek a 22%-hoz képest. Az egyéb kategóriák (*Alacsony* és *Közepes*) esetében is javasolva lesznek szegmensek, amennyiben statisztikailag szignifikánsak.

> [!NOTE]
> Jelenleg csak az elsődleges kategorikus attribútumokat támogatjuk, amelyek legfeljebb 10 kategóriát tartalmaznak. Ha 10-től több kategóriával rendelkező elsődleges attribútum alapján szeretne látni a javaslatokat, akkor javasoljuk, hogy csoportosítsa egyes kategóriákat úgy, hogy a kategóriák számát 10-re vagy kevesebbre csökkentse. Ez a korlátozás csak az elsődleges attribútumok esetén érvényes. A befolyásoló kategoriális attribútumokhoz jelenleg legfeljebb 100 kategóriát támogatunk.

## <a name="generate-suggested-segments"></a>Javasolt szegmensek létrehozása

1. Kattintson a **Szegmensek** lehetőségre.

1. Válassza a **Javaslatok (előzetes verzió)** fület.

1. Válassza az **Új javaslatok lekérése** lehetőséget az irányított élmény elindításához.

1. Válasszon egy mértéket vagy ügyfélattribútumot is elsődleges attribútumként, majd válassza a **Tovább** lehetőséget.

   :::image type="content" source="media/suggested-segments-primary-attribute.png" alt-text="A javasolt szegmensekre vonatkozó javaslatok elsődleges attribútumának kiválasztása.":::

1. Jelölje ki az befolyásoló attribútumokat, és válassza a **Mentés** lehetőséget.
   
   > [!TIP]
   > Több befolyásoló attribútum kiválasztásával nagyobb az esélye annak, hogy értékelve lesz, hogyan befolyásolják az elsődleges attribútumot. Ne szerepeljenek az elsődleges attribútumot nem befolyásoló attribútumok. Ha például minden ügyfele egy adott országhoz tartozik, ne szerepeljen az *ország* attribútum, mivel az nem lesz hatással a kimenetre.

1. Az ügyfélprofilok és a kijelölt attribútumok számától függően a kijelölt attribútumok feldolgozása eltarthat néhány percig. 

## <a name="view-details-of-a-suggested-segment"></a>Javasolt szegmens részleteinek megtekintése

Miután az AI modell már generálta a javaslatokat, megjelennek a **Szegmensek** > **Javaslatok (előzetes verzió)** részben.
 
Válassza ki a javasolt szegmenst a javaslat részleteinek áttekintéshez, beleértve az átlagos érték és a szegmenstagok számának összehasonlítását. Emellett áttekintheti az attribútumértékeket és szabályokat is, amelyek alapján a AI modell a kiválasztott szegmens javaslását megtanulta.

## <a name="save-a-suggestion-as-a-segment"></a>Javaslat mentése szegmensként

1. Ugorjon a **Szegmensek** > **Javaslatok (előzetes verzió)** pontra.

1. Válassza ki a menteni kívánt szegmenst. 

1. Az oldalsó panelen válassza a **Mentés szegmensként** lehetőséget. 

1. A szegmens mentése után megjelenik a **Minden szegmens** lapon a szegmensek listájában. Most már [frissíthető, szerkeszthető vagy törölhető, mint bármely más szegmens](segments.md).

## <a name="refresh-or-edit-a-set-of-suggestions"></a>Javaslatok készletének frissítése és szerkesztése

1. Ugorjon a **Szegmensek** > **Javaslatok (előzetes verzió)** pontra.

1. Válassza a **Javaslatok frissítése** lehetőséget, a javaslatokat frissítéséhez, miközben a konfigurált attribútumokat megtartja. Vagy válassza az **Attribútumok szerkesztése** lehetőséget a konfigurált attribútumok módosításához. A rendszer újrafuttatja az AI-modellt, a legújabb adatok alapján szegmensjavaslatokat generál, és lecseréli az aktuális javaslatokat.

## <a name="limitations"></a>Korlátozások

1. Becsült szegmensméret nem egyezik: Ha olyan elsődleges attribútumot választ, amely üres értékeket tartalmaz, akkor az befolyásolhatja a szegmensjavaslatok becsült szegmensméretét. Az ilyen szegmensek mentésekor a szegmens tényleges mérete más lehet, mint az eredeti szegmens mérete.
 
2. A logikai típusú elsődleges attribútumok nem működnek: Jelenleg csak a karakterlánc- és numerikus típusú adatokat támogatjuk elsődleges attribútumként.

3. A javasolt szegmensek nem elég különbözőek: Ne feledje, hogy a kijelölt attribútumok és az attribútumok értékeinek eloszlása befolyásolja az eredményeket. A különböző eredmények eléréséhez módosíthatja a befolyásoló attribútumokat vagy akár az elsődleges attribútumot is.



[!INCLUDE[footer-include](../includes/footer-banner.md)]