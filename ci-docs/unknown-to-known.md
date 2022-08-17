---
title: A felhasználói élmény személyre szabása ismert és ismeretlen felhasználókra vonatkozó adatokkal
description: Foglalja bele a korábban ismeretlen felhasználókra vonatkozó információkat, ha ismeri a személyazonosságukat.
ms.date: 07/07/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: conceptual
author: mukeshpo
ms.author: mukeshpo
manager: shellyha
searchScope:
- ci-system-diagnostic
- customerInsights
ms.openlocfilehash: 8e3477750d82f965dc2d62174fb35554d9447b7b
ms.sourcegitcommit: 52eca81c36e93d553140f5a37cf6013aaa42623a
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/03/2022
ms.locfileid: "9224298"
---
# <a name="personalize-your-experiences-with-data-about-known-and-unknown-users"></a>A felhasználói élmény személyre szabása ismert és ismeretlen felhasználókra vonatkozó adatokkal

Az ügyféladatok kezelése nem új kihívás, de egyre nehezebbé válik, ahogy a felhasználók eligazodnak a márkák által kínált különböző digitális csatornákon. Az egyik csatornán ismert (hitelesített) felhasználó ismeretlenné (nem hitelesítetté) válik egy másikban, ha nincs bejelentkezve. A probléma gyakran az, hogy a nem hitelesített (ismeretlen) felhasználók nem rendelkeznek közös azonosítóval. Használható értelmes profilok attribútumainak társítására és egységes ügyfélprofilok létrehozására. A Customer Insights segít megoldani ezt a problémát azáltal, hogy adatokat tölt be a forrásrendszereken lévő nyomkövetési módszerekből. Az ismeretlen és ismert profilok konszolidálása teljes körű áttekintést nyújt a szervezeteknek a naprakész profilokról, valamint azok korábbi tranzakcióiról, viselkedéséről és demográfiai adatairól. Még egy lépéssel tovább is megy azáltal, hogy identitásfeloldást biztosít, amely lehetővé teszi az ügyfelek tevékenységének egyesítését több csatornán keresztül, beleértve a webhelyet, az üzleten belüli vásárlást, a hűségprogramokat és így tovább.

## <a name="sample-scenario"></a>Példaforgatókönyv

Gondoljunk csak egy kávézóláncra, amely széles ügyfélkörrel rendelkezik, amely kávét és élelmiszert vásárol az üzletekben, és online rendel termékeket. Gyakran előfordul, hogy az online látogatókat nem hitelesítik a termékek böngészése során, így "ismeretlen felhasználókká" válnak. A kávézólánc számára nehéz személyre szabott ajánlatokat és élményeket nyújtani, ha a felhasználók ismeretlenek. Másrészt az ügyfelek bejelentkezhetnek a fiókjukba, és "ismert felhasználókká" válhatnak a vállalat számára, ha csatlakoznak egy hűségrendszerhez, amely viszont személyre szabottabb élményt tesz lehetővé. A Customer Insights segítségével a kávézólánc betekintést nyerhet az ismert és korábban ismeretlen felhasználókba.

A Customer Insights segítségével a vállalat kombinálhatja az ügyfélprofilokat a nem hitelesített (ismeretlen) munkamenetekből származó tevékenységadatokkal, miután egy felhasználó bejelentkezik és ismertté válik. A kávézólánc más adatforrásokból származó adatokat is áthozhat a beépített összekötők használatával a Customer Insights szolgáltatásba, hogy egyesítse a különböző csatornákból származó ügyfelek identitását.

## <a name="prerequisites"></a>Előfeltételek

- A rendszer webes adatokat gyűjt, és minden látogató számára "látogatói azonosítókat" tartalmaz.
- A webes adatok "hitelesített felhasználói azonosítókat" tartalmaznak a bejelentkezett látogatók számára. Ezek az azonosítók a hűségrendszerhez kapcsolódnak.
- A nagy értékű eseményekre vonatkozó adatok, például a "Terméknézet" és a "Fizetés" definiálva vannak, és szerepelnek a forrásadatokban, az esemény időbélyegével és egy eseményazonosítóval együtt.

Az alábbi táblázat egy egyszerűsített példát mutat be arra, hogy a rendszer milyen nagy értékű webes eseményeket rögzíthet.

|EventID|EseményTimeStamp|UserID|Hűségazonosító|Esemény neve|
|--|--|--|--|--|
|0|07-23-2022 10:00:00|abc123|--|Termék nézet|
|2|07-23-2022 10:05:00|abc123|707.|Hűségbejelentkezés|
|3|07-23-2022 10:10:00|abc123|707.|Megrendelés|
|4|07-23-2022 10:20:00|xyz789|--|Termék nézet|

## <a name="data-ingestion"></a>Adatok betöltése

Az ügyfelekre vonatkozó adatok eseményadatként származhatnak az Ön webhelyéről, és tárolhatók saját házon belüli vagy harmadik féltől származó adatelemzési szolgáltatásaiban. A webes adatok ismert és ismeretlen felhasználókat tartalmaznak, ha a webhely olyan hitelesítési folyamattal rendelkezik, amely integrálható egy hitelesítési szolgáltatással. Például egy e-kereskedelmi rendszer, amely megköveteli a felhasználóktól, hogy teljes adataikat megadják a vásárlási tranzakció befejezéséhez. Vagy egy hűségrendszer, amely hitelesítést igényel a jutalomkedvezmények érvényes címzettjének megerősítéséhez.

A fenti példánkban szereplő eseményadatok az ismert és ismeretlen felhasználók különböző profilazonosítóit tartalmazzák. Az 1. és 4. esetben a felhasználók ismeretlenek, míg a 2. és 3. esetben az abc123 azonosítóval rendelkező felhasználó hűségprogramra regisztrál.

:::image type="content" source="media/website-data-source.png" alt-text="Adatforrások, beleértve a Contoso weboldalt.":::

Az adatbetöltés elérhető lehetőségeivel kapcsolatos további információkért lásd: [Adatforrások áttekintése](data-sources.md).

## <a name="data-unification"></a>Adategyesítés

Az ismeretlen identitások ismert identitásokkal való konvergálása segít lehetővé tenni a felhasználói viselkedésen alapuló személyre szabást, függetlenül a profil állapotától (ismert vagy ismeretlen). Az összes felhasználó számára személyre szabott tartalom segít az ügyfeleknek gyorsan eljutni a legrelevánsabb termékekhez vagy szolgáltatásokhoz, amelyek abban a pillanatban érdeklik őket.

Mivel az adatainkban szereplő felhasználók egy része ismert, a Customer Insights segítségével kombinálhatjuk ezeket az adatokat a felhasználó profiljával. Az ügyfélprofilok egységesítésével kapcsolatos további információkért lásd: [Adategyesítés áttekintése](data-unification.md).

1. Válassza ki a forrásmezőket a webes adatentitásból. Használja a webes adatokban tárolt profiladatokat, és válassza ki azokat a mezőket, amelyek demográfiai adatokkal rendelkező azonosítókat képviselnek.

   :::image type="content" source="media/website-source-fields.png" alt-text="A webes adatforrás forrásmezői.":::

1. Adjon hozzá szabályokat az ismétlődő rekordok egyesítéséhez. Webes adatok esetén válassza ki a leginkább kitöltött adatokat.

1. Egyeztetési szabályok és feltételek konfigurálása. Az ebben a példában szereplő webes profilok eseményadatait az azonosítókon egyeztetni fogjuk az ügyféladatokat tartalmazó egyéb adatforrások profiljaival. Állítson be pontos egyezési szabályokat az azonosítókon külön szabályokként a többi olyan profilentitással, amely rendelkezik a megfelelő elsődleges kulccsal vagy azonosítóval. A példában a webes eseményprofil adatait használjuk utolsó egyező entitásként, így először más profiladatokat egyesítünk.
   1. Nem ellenőrzi **Az összes rekord** belefoglalása jelölőnégyzet egységes profilokat hoz létre az ismert felhasználók számára, és tartalmazza a hozzájuk tartozó ismeretlen felhasználói azonosítókat. Hasznos olyan helyzetekben, amikor érdekli az ismert felhasználók múltbeli viselkedési tevékenységeinek megtekintése, amikor még ismeretlenek voltak.
   1. A Minden rekord **belefoglalása jelölőnégyzet** külön profilrekordokat hoz létre az ismeretlen felhasználók számára. Az ismeretlen felhasználók egyedi ügyfél-azonosítót kapnak. A jövőben, ha egy ismert profil társítva van a webes események profiladataiban, akkor az újonnan ismert felhasználó útja megtekinthető és felhasználható a korábbi ismeretlen viselkedési adatokon alapuló személyre szabáshoz is.

:::image type="content" source="media/website-match-rule.png" alt-text="A webhely adatforrás entitás egyeztetési szabálya.":::

## <a name="get-insights"></a>Háttér-információk megtekintése

Ha az ügyfélprofilokat ismeretlen és ismert felhasználók számára hozzák létre, a nagy értékű webes eseményadatok tevékenységként [használhatók](activities.md). Ezekkel a tevékenységekkel további betekintést hozhat létre. Például azok az ügyfelek, akik hat hónappal ezelőtt látogattak meg egy webhelyet (amikor még ismeretlenek voltak), vagy azok az ügyfelek, akik nem rendelkeznek hűségazonosítóval, soha nem fejezték be a fizetést.

:::image type="content" source="media/website-known-unknown.png" alt-text="Képernyőkép az ügyféloldalról ismert és ismeretlen ügyfelekkel.":::

[Gazdagítsa](enrichment-hub.md) adatait, hozzon létre [mértékeket](measures.md), és hozzon létre [szegmenseket](segments.md) a további aktiváláshoz.

Létrehozhat például olyan ismert felhasználók szegmenseit, amelyek megnéztek néhány terméket, de soha nem fejezték be a fizetést.

További információ: [Szegmensek áttekintése](segments.md).

## <a name="activate-insights"></a>Elemzések aktiválása

Az adatok exportálásának és a mögöttes elemzések alapján többféleképpen is elvégezhető.

További információ: [Exportálások áttekintése](export-destinations.md).
