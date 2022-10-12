---
title: Termékjavaslatok előrejelzése
description: Olyan termékek előre jelzése, amelyekbe az ügyfél valószínűleg mag fog vásárolni vagy interakcióba lép velük.
ms.date: 09/30/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: conceptual
author: wmelewong
ms.author: wameng
manager: shellyha
ms.openlocfilehash: 0057d6796bb60db44d08b58d9e0daaf6e7c90fde
ms.sourcegitcommit: be341cb69329e507f527409ac4636c18742777d2
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/30/2022
ms.locfileid: "9610285"
---
# <a name="predict-product-recommendations"></a>Termékjavaslatok előrejelzése

A termékjavaslati modell prediktív termékjavaslatokat hoz létre. Az ajánlások a korábbi vásárlási viselkedésen és a hasonló vásárlási mintával rendelkező ügyfeleken alapulnak. Ez a modell az egyéni fogyasztóknak szól (B-től C-ig).

Üzleti ismeretekkel kell rendelkeznie a vállalkozás különböző típusú termékeiről és arról, hogy az ügyfelek hogyan lépnek kapcsolatba velük. Támogatjuk, hogy az ügyfelek által korábban megvásárolt termékekre vagy új termékekre vonatkozó javaslatokat.

A termékre vonatkozó javaslatokra a helyi jogszabályok és előírások, illetve az ügyfelek elvárásai vonatkozhatnak, amelyeket a modell tervezésekor nem vettek külön figyelembe. Ezért az ügyfeleknek **való kézbesítés előtt át kell tekintenie az ajánlásokat,** hogy megbizonyosodjon arról, hogy betartja-e a vonatkozó törvényeket vagy előírásokat, valamint az ügyfelek elvárásait azzal kapcsolatban, amit ön javasolhat.

A modell kimenete a termékazonosítón alapuló javaslatokat tartalmaz. A megjelenítési mechanizmusnak hozzá kell rendelnie az előrejelzett termékazonosítókat a megfelelő tartalomhoz, hogy az ügyfelek figyelembe tudják venni a honosítást, a képtartalmat és más, vállalkozásspecifikus tartalmakat vagy viselkedést.

> [!TIP]
> Próbálja ki a termékajánlási előrejelzés mintaadatok használatával: [Termékajánlás előrejelzés mintaútmutató](sample-guide-predict-product-recommendation.md).

## <a name="prerequisites"></a>Előfeltételek

- Legalább [közreműködő engedélyek](permissions.md)
- Legalább 100 ügyfél, lehetőleg több mint 10 000 ügyfél.
- Ügyfél-azonosító, egy egyedi azonosító, amely a tranzakciókat egy adott ügyféllel egyezteti
- Legalább egy év tranzakciós adatok, lehetőleg két-három év, hogy némi szezonalitást is tartalmazzon. Ideális esetben ügyfél-azonosítónként legalább három vagy több tranzakció. A tranzakciós előzményeknek tartalmazniuk kell a következőket:
  - **Tranzakcióazonosító**: Egy vásárlás vagy tranzakció egyedi azonosítója.
  - **Tranzakció dátuma**: A vásárlás vagy tranzakció dátuma.
  - **A tranzakció** értéke: A vásárlás vagy tranzakció számszerű értéke.
  - **Egyedi termékazonosító**: A megvásárolt termék vagy szolgáltatás azonosítója, ha az adatok sorszinten vannak.
  - **Vásárlás vagy visszaküldés**: Logikai igaz/hamis érték, ahol *a true* azt azonosítja, hogy egy tranzakció visszáru volt. Ha a vásárlási vagy visszaküldési adatok nem szerepelnek a modellben, és a **tranzakció** értéke negatív, akkor kikövetkeztetjük a visszaküldést.
- Termékkatalógus-adatentitás, amely termékszűrőként használható.

> [!NOTE]
> - A modellhez az ügyfelek tranzakciós előzményeire van szükség, ahol a tranzakció minden olyan adat, amely a felhasználó és a termék közötti interakciót írja le. Például termékvásárlás, tanfolyamon vagy eseményen való részvétel.
> - Csak egy tranzakciós előzményentitás konfigurálható. Ha több vásárlási entitás van, egyesítse őket az Power Query adatbetöltés előtt.
> - Ha a megrendelés és a megrendelés részletei eltérő entitások, akkor a modell használata előtt kapcsolja össze őket. A modell nem működik csak egy entitás megrendelésazonosítójával vagy bizonylatazonosítójával.

## <a name="create-a-product-recommendation-prediction"></a>Termékjavaslat-előrejelzés létrehozása

Válassza a Piszkozat **mentése bármikor lehetőséget** a előrejelzés piszkozatként való mentéséhez. A piszkozat előrejelzés a **Saját előrejelzések** lapon jelenik meg.

1. Ugrás az Intelligencia-előrejelzések **oldalra** > **·**.

1. A Létrehozás **lapon válassza a** Modell **használata lehetőséget** a **Termékajánlások (előzetes verzió)** csempén.

1. Válassza az **Első lépések** lehetőséget.

1. **Nevezze el ezt a modellt** és a **Kimeneti entitás nevét**, hogy megkülönböztesse őket az egyéb modellektől vagy entitásoktól.

1. Válassza a **Következő** lehetőséget.

### <a name="define-product-recommendation-preferences"></a>Termékajánlási beállítások meghatározása

1. Állítsa be az **ügyfélnek ajánlani kívánt termékek** számát. Ez az érték attól függ, hogy a szállítási módja hogyan tölti ki az adatokat.

1. Válassza ki, hogy fel szeretné-e venni azokat a termékeket, amelyeket az ügyfelek korábban vásároltak meg az **Elvárt** vásárlások megismétlése mezőben.

1. Állítsa be a **Visszatekintés ablakot** a modell által figyelembe vett időkeret, mielőtt újra ajánlaná a terméket a felhasználónak. Például jelezheti, hogy egy ügyfél két évente vásárol laptopot. A modell megvizsgálja az elmúlt két év vásárlási előzményeit, és ha talál egy cikket, az elemet a rendszer kiszűri a javaslatokból.

1. Válassza a **Tovább** lehetőséget

### <a name="add-purchase-history"></a>Vásárlási előzmények hozzáadása

1. Válassza az Adatok hozzáadása lehetőséget **az Ügyfél tranzakciós előzményeihez** **.**

1. Válassza ki a SalesOrderLine **szemantikai tevékenységtípust**, amely tartalmazza a szükséges tranzakciós vagy vásárlási előzményeket. Ha a tevékenység nincs beállítva, válassza ki **itt**, és hozza létre.

1. Ha a Tevékenységek **alatt** a tevékenységattribútumok szemantikailag leképeződtek a tevékenység létrehozásakor, válassza ki azokat az attribútumokat vagy entitásokat, amelyekre a számítást összpontosítani szeretné. Ha a szemantikai leképezés nem történt meg, válassza az Adatok szerkesztése **és leképezése lehetőséget**.

   :::image type="content" source="media/product-recommendation-select-semantic-activity.PNG" alt-text="A szemantikus típus alatti tevékenységek kiválasztását bemutató oldalsó panel.":::

1. Válassza a Tovább **lehetőséget**, és tekintse át a modellhez szükséges attribútumokat.

1. Válassza a **Mentés** parancsot.

1. Válassza a **Következő** lehetőséget.

### <a name="add-product-information-and-filters"></a>Termékinformációk és szűrők hozzáadása

Időnként csak bizonyos termékek hasznosak vagy megfelelőek a megtervezett előrejelzés típusának. A termékszűrők segítségével azonosíthatja a termékek egy olyan részhalmazát, amely meghatározott jellemzőkkel rendelkezik, és amelyeket ajánlhat ügyfeleinek. A modell a rendelkezésre álló összes terméket fel fogja használni a minták elsajátítása érdekében, de csak a termékszűrőnek megfelelő termékeket használja a kimenetben.

1. Adja hozzá a termékkatalógus-entitást, amely az egyes termékekre vonatkozó információkat tartalmazza. Térképezze fel a szükséges információkat, és válassza a Mentés **lehetőséget**.

1. Válassza a **Következő** lehetőséget.

1. Válassza a Termékszűrők **lehetőséget**:

   - **Nincsenek szűrők**: Használja a termékjavaslat előrejelzésében lévő összes terméket.

   - **Adott termékszűrők meghatározása**: Használjon a termékjavaslat előrejelzésében lévő specifikus termékeket. **A Termékkatalógus-attribútumok** panelen válassza ki a termékkatalógus-entitás azon attribútumait, amelyeket fel szeretne venni a szűrőbe.

     :::image type="content" source="media/product-filters-sidepane.png" alt-text="Az oldalsó ablaktábla a termékkatalógus entitásban hozzárendelve látszódik a termékszűrők kiválasztásához.":::

1. Válassza ki, hogy használni **szeretné-e a termékszűrőt, és**/vagy logikailag kombinálni szeretné-e **a** termékkatalógusból kiválasztott attribútumokat.

   :::image type="content" source="media/product-filters-sample.png" alt-text="Termékszűrők mintakonfigurációja logikai ÉS összekötőkkel kombinálva.":::

1. Válassza a **Következő** lehetőséget.

### <a name="set-update-schedule"></a>Frissítési ütemezés beállítása

1. Válasszon egy frekvenciát a modell újratanításához. Ez a beállítás fontos az előrejelzések pontosságának frissítéséhez, mivel a rendszer új adatokat tölt be a Customer Insights szolgáltatásba. A legtöbb cég havonta egyszer végez újratanítást, és pontos előrejelzésekhez tud jutni.

1. Válassza a **Következő** lehetőséget.

### <a name="review-and-run-the-model-configuration"></a>A modellkonfiguráció áttekintése és futtatása

Az **Áttekintés és futtatás** lépés a konfiguráció összegzését jeleníti meg, és lehetőséget biztosít a módosítások elvégzésére a előrejelzés létrehozása előtt.

1. Válassza a Szerkesztés **lehetőséget** az áttekintéshez és a módosítások elvégzéséhez szükséges lépések bármelyikénél.

1. Ha elégedett a választásokkal, válassza a Mentés és futtatás **lehetőséget** a modell futtatásának megkezdéséhez. Válassza a **Kész** lehetőséget. A **Saját előrejelzések** lap a előrejelzés létrehozásakor jelenik meg. A folyamat – az előrejelzésben használt adatok mennyiségétől függően – több óráig is tarthat.

[!INCLUDE [progress-details](includes/progress-details-pane.md)]

## <a name="view-prediction-results"></a>Előrejelzés eredmények megtekintése

1. Ugrás az Intelligencia-előrejelzések **oldalra** > **·**.

1. **A Saját előrejelzések** lapon válassza ki a megtekinteni kívánt előrejelzés.

Az eredmények oldalán belül az adatoknak öt elsődleges szakasza van.

- **Modell teljesítménye:** Az A, B vagy C fokozatok a előrejelzés teljesítményét jelzik, és segíthetnek a kimeneti entitásban tárolt eredmények használatára vonatkozó döntés meghozatalában.
  
  :::image type="content" source="media/product-recommendation-modelperformance.PNG" alt-text="A modell teljesítményének eredménye az A fokozattal.":::

  Az osztályzatot a következő szabályok határozzák meg:
  - **A** ha a "Success @ K" mutató legalább 10%-kal több, mint az alapérték.
  - **B**, ha a "Success @ K" mutató 0–10%-kal több, mint az alapérték.
  - **C**, ha a "Success @ K" metrika kisebb, mint az alapérték.
  - **Alapterv**: A vásárlás szerint leginkább ajánlott termékek száma az összes ügyfél között + a modell által azonosított tanult szabályok = az ügyfeleknek szóló javaslatok halmaza. Ezután a rendszer összeveti az előrejelzéseket a legjobb termékekkel, amit a terméket megvásárolt ügyfelek száma alapján számít. Ha egy ügyfélnek legalább egy olyan terméke van az ajánlott termékeiben, amelyek a legjobb megvásárolt termékeknél is láthatók, akkor ezek az alapérték részét jelentik. Ha például 10 ilyen ügyfélnek volt egy ajánlott terméke a 100 teljes vevőből, akkor az alapérték 10%.
  - **Success @ K**: A javaslatok minden ügyfél számára létrejönnek, és összehasonlítják a tranzakciók érvényességi időtartamának készletével. Például egy 12 hónapos időszakban a 12. hónapot érvényesítési adatkészletként kell elkülöníteni. Ha a modell legalább egy dolgot előre jelez, amit a 12. hónapban vásárolna az előző 11 hónap során tanultak alapján, az ügyfél megnövelné a "Siker @ K" mérőszámot.

- **A leggyakrabban javasolt termékek (egyezéssel):** Az öt legjobb termék, amit előre jeleztek az ügyfeleknek.
  
  :::image type="content" source="media/product-recommendation-topproducts.PNG" alt-text="A legjobb 5 ajánlott terméket bemutató grafikon.":::

- **A legfontosabb javaslati tényezők:** A modell az ügyfelek tranzakciós előzményei alapján tesz termékjavaslatokat. A mintákat a korábbi vásárlások alapján tanulja meg, és hasonlóságot keres az ügyfelek és a termékek között. Ezt követően a hasonlóságokat a termékre vonatkozó javaslatok létrehozásához használjuk.
  A következő tényezők befolyásolhatják a modell által generált termékajánlásokat.
  - **Korábbi tranzakciók**: Az ajánlott termék a korábbi vásárlási mintákon alapult. A modell javasolhatja például a *Surface Arc Mouse* használatát, ha valaki nemrég megvásárolt egy *Surface Book 3*, és egy *Surface Pent*. A modell korábban már megtanulta, hogy számos ügyfél megvásárolt egy *Surface Arc Mouse-t*, miután megvásárolt egy *Surface Book 3-at* és egy *Surface Pent*.
  - **Ügyfélhasonlóság**: Az ajánlott terméket korábban más, hasonló vásárlási mintákat mutató ügyfelek vásárolták meg. Például Johnnak ajánlották a *Surface Headphones 2-t*, mert Jennifer és Brad nemrég vásárolt egy *Surface Headphones 2-t*. A modell szerint John hasonló Jenniferhez és Bradhez, mert korábban hasonló vásárlási mintáik voltak.
  - **Termékhasonlóság**: Az ajánlott termék hasonló az ügyfél által korábban megvásárolt termékekhez. A modell két terméket akkor tekint hasonlónak, ha azokat egyben vagy hasonló ügyfelek vásárolják meg. Például valakinek ajánlanak egy *Pendrive-ot*, mert korábban vásárolt egy *USB-C–USB Adaptert*, és a modell szerint a korábbi vásárlási minták alapján a *Pendrive* hasonlít a *USB-C–USB Adapterhez*.

  Minden termékjavaslatot egy vagy több tényező befolyásol. A diagram ábrázolja azoknak a javaslatoknak a százalékos arányát, amelyeknél mindegyik tényező szerepet játszott. A következő példában az ajánlások 100%-át korábbi tranzakciók befolyásolták, 60%-át az ügyfélhasonlóság, 22%-át a termékhasonlóság. Menjen az egérrel a diagram sávjaira, és tekintse meg, hogy pontosan milyen százalékban játszottak szerepet a befolyásoló tényezők.
  
  :::image type="content" source="media/product-recommendation-keyrecommendationfactors.png" alt-text="A modell által a termékjavaslatok létrehozásához megtanult legfontosabb javaslati tényezők.":::

- **Adatstatisztikák**: A modell által figyelembe vett tranzakciók, ügyfelek és termékek számának áttekintése. A minták megtanulásához és a termékre vonatkozó javaslatok létrehozása során használt bemeneti adatokon alapul.

  :::image type="content" source="media/product-recommendation-datastatistics.png" alt-text="A modell által a minták megtanulásához használt bemeneti adatokkal kapcsolatos adatstatisztikák.":::
  
  A modell az összes rendelkezésre álló adatot felhasználja a minták megtanulásához. Ezért ha termékszűrést használ a modellkonfigurációban, ez a szakasz a modell által elemzett termékek teljes számát mutatja be a minták megtanulásához, ami eltérhet a meghatározott szűrési feltételeknek megfelelő termékek számától. A szűrés a modell által generált kimenetre vonatkozik.

- **Minta termékajánlások:** Olyan javaslatok mintája, amelyeket a modell szerint valószínűleg az ügyfél vásárol meg. Termékkatalógus hozzáadása esetén a termékazonosítókat a rendszer terméknevekre cseréli.

  :::image type="content" source="media/product-recommendation-highconfidence.PNG" alt-text="Az egyéni ügyfelek egy kiválasztott halmazára vonatkozó nagy megbízhatóságú javaslatokat mutató lista.":::

> [!NOTE]
> A modell *kimeneti entitásában a Score* a javaslat mennyiségi mértékét mutatja. A modell magasabb pontszámú termékeket ajánl az alacsonyabb pontszámú termékek helyett. A pontszám megtekintéséhez lépjen az **Adatentitások** > **lapra**, és tekintse meg a modellhez definiált kimeneti entitás adatok lapját.

[!INCLUDE [footer-include](includes/footer-banner.md)]
