---
title: Ismeretlen profilok kezelése a Customer Insights segítségével
description: Ismeretlen ügyfélprofilok használata, amelyek a Dynamics 365 Customer Insights.
ms.date: 09/14/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: conceptual
author: andtapia
ms.author: andreatapia
manager: shellyha
ms.openlocfilehash: d7e5050ee5832df5ecf40a352f7ea8d42830fa45
ms.sourcegitcommit: f6b6a4c4ce9cf12e449488b24aab80a2cbfe0c47
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/21/2022
ms.locfileid: "9556399"
---
# <a name="manage-unknown-profiles-with-customer-insights"></a>Ismeretlen profilok kezelése a Customer Insights segítségével

Az internethasználók gyakran azonosítatlanok és névtelenek az interneten. Ha nincsenek bejelentkezve, mert különböző eszközöket vagy csatornákat használnak, az még a leghűségesebb ügyfelekre is igaz. Mivel a harmadik féltől származó cookie-k valószínűleg hamarosan megszűnnek, a felhasználói preferenciák belső adatokon alapuló kezelése elengedhetetlen a differenciált, személyre szabott élmény eléréséhez. Sok márka esetében az ismert vagy hitelesített felhasználók alkotják a kisebbséget, annak ellenére, hogy a személyre szabással kapcsolatos növekvő vásárlói elvárásokat támasztanak. A vállalkozások számára nagyszerű, ha megbízható, részletes és egységes adatok alapján tudják, kik az ügyfeleik.

Az emlékezetes személyre szabás az ügyféladatok gazdagságától és teljességétől függ, és a Customer Insights segít elérni ezeket a célokat. Nem kell korlátoznia vagy leállítania a ügyfélút elején gyűjtött adatok felhasználását. A Customer Insights lehetővé teszi, hogy saját adatokat hozzon létre egy ügyfélprofil létrehozásához ismeretlen felhasználók számára. Ezután ezt a profilt további műveletekhez használhatja, annak ellenére, hogy hiányoznak a kapcsolattartási adatok. Importáljon belső adatokat olyan forrásokból, mint a webes, mobil- vagy CRM-rendszerek, hogy folyamatosan bővítse az ügyfélprofilokat. Ahogy egyesíted a további interakciókat, [változtasd az *ismeretlen* ügyfelet ismert *ügyféllé*](unknown-to-known.md).

## <a name="sample-scenario"></a>Példaforgatókönyv

Az e-kereskedelem az elmúlt évtized leggyorsabban növekvő csatornája. Tegyük fel, hogy egy felhasználó a mobileszközét használja az e-kereskedelmi webhely böngészéséhez. A weboldal egyedi azonosítóként rendeli hozzá a látogató "mobile_guest123", és Ön az online tevékenysége alapján kezdi el gyűjteni a viselkedési tevékenységeket. Például, hogy mely oldalakat látogatták meg, mennyi időt töltöttek ezeken az oldalakon, vagy mely linkekre kattintottak. Nem tudja a nevüket vagy az e-mail-címüket, de ezek az adatok segíthetnek abban, hogy a márkák értelmes betekintést nyerjenek az adott felhasználóba. Ezeket az elemzéseket viszont akkor is üzembe helyezheti, amikor a felhasználó legközelebb felkeresi a webhelyet. A Customer Insights "mobile_guest123" lekérdezésével lekérdezheti a felhasználó szegmenslistáját, például az "organikus", "mobil előrendelési ügyfeleket", a "nagy értékű ügyfeleket" stb., vagy lekérheti a profilt személyre szabott webes élmények létrehozásához. Az adatokat bármely aktiválási rendszerbe exportálhatja, hogy ugyanezt tegye.

## <a name="prerequisites"></a>Előfeltételek

- Belső adatok betöltése a Customer Insights szolgáltatásba
- Minden entitás egyedi azonosítóval rendelkezik, amely elsődleges kulcsként van beállítva
- Minden entitás, amely elsődleges kulccsal rendelkezik a személyre szabáshoz, egységes
- Webhelye tartalomkezelő rendszere képes API-k használatára (a Customer Insights szolgáltatással való közvetlen kommunikáción alapuló webes személyre szabáshoz)

Az alábbi táblázat egy egyszerűsített példát mutat be arra, hogyan lehet rögzíteni a nagy értékű webes eseményeket.

|EventID|EseményTimeStamp|UserID|Elsődleges kulcs|Esemény neve|
|--|--|--|--|--|
|0|09-15-2022 9:00:00|abc123|Cookie AZONOSÍTÓ1|Termék nézet|
|2|09-18-2022 10:05:00|abc123|Cookie AZONOSÍTÓ1|Termék nézet|
|3|09-18-2022 10:10:00|abc123|Cookie AZONOSÍTÓ1|Kosárba|
|4|09-21-2022 09:05:00|abc123|Cookie AZONOSÍTÓ1|Termék nézet|

## <a name="data-ingestion"></a>Adatok betöltése

Az adatbetöltés elérhető lehetőségeivel kapcsolatos további információkért lásd: [Adatforrások áttekintése](data-sources.md).

## <a name="data-unification"></a>Adategyesítés

Az ügyfélprofilok egységesítésével kapcsolatos további információkért lásd: [Adategyesítés áttekintése](data-unification.md).

## <a name="get-insights"></a>Háttér-információk megtekintése

[Gazdagítsa](enrichment-hub.md) adatait, hozzon létre [mértékeket](measures.md), és hozzon létre [szegmenseket](segments.md) a további aktiváláshoz.

Létrehozhat például ismeretlen felhasználók szegmenseit, amelyek ugyanazokat a termékoldalakat böngészték, de soha nem fejezték be a fizetést.

## <a name="activation"></a>Aktiválás

Mivel a Customer Insightsban tárolt adatai és a munkára kész elemzések készen állnak a munkára, a Customer Insights segítségével személyre szabhatja a személyre szabást:

1. [Az OData API-val](apis.md) lekérhet egy szegmenstagságot vagy ügyfélprofilt További példákért lásd: [OData-lekérdezési példák a Customer Insights API-khoz](odata-examples.md).

1. [Exportálja](export-destinations.md) adatait az aktiválási rendszerekbe.

Példa: Egy ismeretlen felhasználó többször is ellátogat egy webhelyre, és meglátogatja a bőrcipő különböző modelljeinek termékoldalait. A Customer Insights-ban elérhető adatokkal az ismeretlen felhasználót felveheti a bőrcipők iránt érdeklődők szegmensébe. Használja ezt a szegmenst, hogy tájékoztassa webhelyét, hogy személyre szabja a visszatérő látogatók személyre szabását. A következő látogatáskor az oldal felismeri az ismeretlen felhasználót, és 10% -os kupont kínálhat nekik bőrcipőkön.

[!INCLUDE [footer-include](includes/footer-banner.md)]
