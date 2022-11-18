---
title: Ismeretlen profilok kezelése a Customer Insights segítségével
description: 'Ismeretlen ügyfélprofilok használata, amelyeket a következőben hoznak létre és kezelnek: Dynamics 365 Customer Insights.'
ms.date: 09/14/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: conceptual
author: andtapia
ms.author: andreatapia
manager: shellyha
ms.openlocfilehash: 0e12f64a22b93d117009fb8aee76d02a7583e699
ms.sourcegitcommit: 24627d53dcdf607baaab1cc3c299a3584c386173
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/15/2022
ms.locfileid: "9776824"
---
# <a name="manage-unknown-profiles-with-customer-insights"></a>Ismeretlen profilok kezelése a Customer Insights segítségével

Az internethasználók gyakran azonosítatlanok vagy névtelenek az interneten. Még a leghűségesebb ügyfelek is "ismeretlennek" tűnhetnek, ha nincsenek bejelentkezve különböző eszközökön. Sok márka esetében az ismert vagy hitelesített felhasználók kisebbségben vannak, annak ellenére, hogy az ügyfelek egyre nagyobb elvárásokat támasztanak a személyre szabással kapcsolatban. A harmadik féltől származó cookie-k jövőjével kapcsolatban a felhasználói preferenciák belső adatokon alapuló kezelése elengedhetetlen a személyre szabott élmény eléréséhez.

Az emlékezetes személyre szabás attól függ, hogy mennyire ismeri az ügyfelet, és a Customer Insights segít ebben azáltal, hogy nyomon követi az összes ügyfelet.  Nem kell korlátoznia vagy leállítania a ügyfélút elején gyűjtött adatok felhasználását. A Customer Insights lehetővé teszi, hogy saját adatokat hozzon létre egy ügyfélprofil létrehozásához ismeretlen felhasználók számára. Ezután ezt a profilt további műveletekhez használhatja, annak ellenére, hogy hiányoznak a kapcsolattartási adatok. Belső adatokat importálhat olyan forrásokból, mint a webes, mobil- vagy CRM-rendszerek a Customer Insights szolgáltatásba, hogy folyamatosan bővítse az ügyfélprofilokat. Ahogy egyre több interakciót [egyesít, az *ismeretlen* ügyfelet ismert *ügyféllé* alakíthatja](unknown-to-known.md).

## <a name="sample-scenario"></a>Minta forgatókönyv

Tegyük fel, hogy egy felhasználó a mobileszközét használja az e-kereskedelmi webhely böngészésére. A weboldal egyedi azonosítóként rendeli hozzá a látogatóhoz a "mobile_guest123" szót, és Ön elkezdi gyűjteni a viselkedési tevékenységeket az online tevékenységük alapján. Például azt, hogy mely oldalakat látogatták meg, mennyi időt töltöttek ezeken az oldalakon, vagy mely linkekre kattintottak. Nem tudja a nevüket vagy az e-mail-címüket, de ezek az adatok segíthetnek abban, hogy a márkák érdemi betekintést nyerjenek az adott felhasználóba. Ezeket az elemzéseket viszont hasznosíthatja, amikor a felhasználó legközelebb meglátogatja a webhelyet. A Customer Insights "mobile_guest123" lekérdezésével lekérheti a felhasználó szegmenslistáját, például "organikus", "mobil előrendelési ügyfelek", "nagy értékű ügyfelek" stb., vagy lekérheti a profilt személyre szabott webes élmények létrehozásához. Ugyanezt bármely aktiválási rendszerbe exportálhatja az adatokat.

## <a name="prerequisites"></a>Előfeltételek

- Belső adatok betöltése a Customer Insights szolgáltatásba
- Minden entitás egyedi azonosítóval rendelkezik, amely elsődleges kulcsként van beállítva
- Minden entitás, amely elsődleges kulccsal rendelkezik a személyre szabáshoz, egységesen van
- A webhely tartalomkezelő rendszere API-kat használhat (a Customer Insights szolgáltatással való közvetlen kommunikáción alapuló webes személyre szabáshoz)

Az alábbi táblázat egy egyszerűsített példát mutat be a nagy értékű webes események rögzítésére.

|EventID|EseményTimeStamp|UserID|ElsődlegesKey|Esemény neve|
|--|--|--|--|--|
|0|09-15-2022 9:00:00|abc123|Cookie-azonosító1|Termék nézet|
|2|09-18-2022 10:05:00|abc123|Cookie-azonosító1|Termék nézet|
|3|09-18-2022 10:10:00|abc123|Cookie-azonosító1|Kosárba|
|4|09-21-2022 09:05:00|abc123|Cookie-azonosító1|Termék nézet|

## <a name="data-ingestion"></a>Adatok betöltése

Az adatbetöltéshez rendelkezésre álló lehetőségekkel kapcsolatos további információkért lásd: [Adatforrások áttekintése](data-sources.md).

## <a name="data-unification"></a>Adategyesítés

Az ügyfélprofilok egységesítésével kapcsolatos további információkért lásd: [Adategyesítés áttekintése](data-unification.md).

## <a name="get-insights"></a>Háttér-információk megtekintése

[Bővítse](enrichment-hub.md) adatait, hozzon létre mértékeket, és hozzon létre [szegmenseket](measures.md) [a](segments.md) további aktiváláshoz.

Létrehozhat például olyan szegmenseket ismeretlen felhasználókból, amelyek ugyanazokat a termékoldalakat böngészték, de soha nem fejezték be a fizetést.

## <a name="activation"></a>Aktiválás

Ha a Customer Insights szolgáltatásban tárolt adatai és a betekintései készen állnak a munkára, a Customer Insights segítségével személyre szabhatja a dolgokat:

1. Az OData [API használata szegmenstagság vagy ügyfélprofil lekéréséhez További példákért lásd:](apis.md) OData-lekérdezési példák Customer Insights API-khoz [...](odata-examples.md).

1. [Exportálja](export-destinations.md) adatait az aktiválási rendszerekbe.

Példa: Egy ismeretlen felhasználó többször is felkeres egy webhelyet, és különböző bőrcipőmodellek termékoldalait látogatja meg. A Customer Insights szolgáltatásban elérhető adatokkal az ismeretlen felhasználót is bevonhatja a bőrcipők iránt érdeklődők szegmensébe. Használja ezt a szegmenst, hogy tájékoztassa webhelyét a visszatérő látogatók személyre szabásáról. A következő látogatáskor a webhely felismeri az ismeretlen felhasználót, és 10% -os kupont kínálhat nekik a bőrcipőkre.

[!INCLUDE [footer-include](includes/footer-banner.md)]
