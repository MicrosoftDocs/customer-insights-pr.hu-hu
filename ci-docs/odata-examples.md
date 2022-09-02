---
title: OData-lekérdezési példák Customer Insights API-khoz
description: Gyakran használt példák az Open Data Protocol (OData) számára a Customer Insights API-k lekérdezésére az adatok áttekintéséhez.
ms.date: 08/30/2022
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
ms.reviewer: mhart
manager: shellyha
ms.openlocfilehash: 26e56a3bab01ba55284a52e72efbcbfbaadaad6f
ms.sourcegitcommit: 624b27bb65a0de1970dc1ac436643b493f0a31cf
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/31/2022
ms.locfileid: "9387205"
---
# <a name="odata-query-examples-for-customer-insights-apis"></a>OData-lekérdezési példák Customer Insights API-khoz

Az Open Data Protocol (OData) egy olyan adatelérési protokoll, amely olyan alapvető protokollokra épül, mint a HTTP. Általánosan elfogadott módszertanokat használ, mint például a REST for the web. Az OData-szolgáltatások felhasználására különféle könyvtárak és eszközök használhatók.

Ha segíteni szeretne saját implementációk felépítésében a [Customer Insights API-k](apis.md) alapján, tekintsen át néhány gyakran kért példalekérdezést.

Módosítsa a lekérdezésmintákat, hogy működjenek a célkörnyezetekben:

- {serviceRoot}: `https://api.ci.ai.dynamics.com/v1/instances/{instanceId}/data` hol {instanceId} van a lekérdezni kívánt Customer Insights-környezet GUID azonosítója. A [ListAllInstances művelet](https://developer.ci.ai.dynamics.com/api-details#api=CustomerInsights&operation=Get-all-instances) lehetővé teszi, hogy megtalálja azt {InstanceId}, amelyhez hozzáféréssel rendelkezik.
- {CID}: Egységes ügyfélrekord GUID azonosítója. Példa: `ce759201f786d590bf2134bff576c369`.
- {AlternateKey}: Egy ügyfélrekord elsődleges kulcsának azonosítója egy adatforrás. Példa: `CNTID_1002`
- {DSname}: Sztring egy olyan adatforrás entitásnevével, amely a Customer Insights szolgáltatásba kerül. Példa: `Website_contacts`.
- {SegmentName}: Sztring egy szegmens kimeneti entitásnevével a Customer Insights szolgáltatásban. Példa: `Male_under_40`.

## <a name="customer"></a>Ügyfelünk

Mintalekérdezések az *Ügyfél* entitáshoz.

|Lekérdezés típusa |Példa  | Feljegyzés  |
|---------|---------|---------|
|Egyetlen ügyfél-azonosító     | `{serviceRoot}/Customer?$filter=CustomerId eq '{CID}'`          |  |
|Másodlagos kulcs    | `{serviceRoot}/Customer?$filter={DSname_EntityName_PrimaryKeyColumnName} eq '{AlternateKey}'`         |  Az alternatív kulcsok megmaradnak az egyesített vevői entitásban       |
|Select   | `{serviceRoot}/Customer?$select=CustomerId,FullName&$filter=customerid eq '1'`        |         |
|Ennyi idő múlva:    | `{serviceRoot}/Customer?$filter=CustomerId in ('{CID1}',’{CID2}’)`        |         |
|Másodlagos kulcs + Be   | `{serviceRoot}/Customer?$filter={DSname_EntityName_PrimaryKeyColumnName} in ('{AlternateKey}','{AlternateKey}')`         |         |
|Keresés  | `{serviceRoot}/Customer?$top=10&$skip=0&$search="string"`        |   Keresési karakterlánc esetén a 10 legjobb eredményt adja eredményül.      |
|Szegmens tagság  | `{serviceRoot}/Customer?select=*&$filter=IsMemberOfSegment('{SegmentName}')&$top=10`     | A szegmentálási entitás sorainak előre beállított számát adja eredményül.      |
|Szegmenstagság egy ügyfél számára | `{serviceRoot}/Customer?$filter=CustomerId eq '{CID}'&IsMemberOfSegment('{SegmentName}')`     | Visszaadja az ügyfélprofilt, ha az adott szegmens tagja     |

## <a name="unified-activity"></a>Egyesített tevékenység

Mintalekérdezések a *UnifiedActivity* entitáshoz.

|Lekérdezés típusa |Példa  | Feljegyzés  |
|---------|---------|---------|
|A CID tevékenysége     | `{serviceRoot}/UnifiedActivity?$filter=CustomerId eq '{CID}'`          | Egy adott ügyfélprofil tevékenységeit listázza |
|Tevékenységi időkeret    | `{serviceRoot}/UnifiedActivity?$filter=CustomerId eq '{CID}' and ActivityTime gt 2017-01-01T00:00:00.000Z and ActivityTime lt 2020-01-01T00:00:00.000Z`     |  Ügyfélprofil tevékenységei egy időkeret       |
|Tevékenység típusa    |   `{serviceRoot}/UnifiedActivity?$filter=CustomerId eq '{CID}' and ActivityType eq '{ActivityName}'`        |         |
|Megjelenítendő név tevékenysége     | `{serviceRoot}/UnifiedActivity$filter=CustomerId eq ‘{CID}’ and ActivityTypeDisplay eq ‘{ActivityDisplayName}’`        | |
|Tevékenységek rendezése    | `{serviceRoot}/UnifiedActivity?$filter=CustomerId eq ‘{CID}’ & $orderby=ActivityTime asc`     |  Növekvő vagy csökkenő tevékenységek rendezése       |
|A szegmenstagságból bővült tevékenység  |   `{serviceRoot}/Customer?$expand=UnifiedActivity,Customer_Measure&$filter=CustomerId eq '{CID}'`     |         |

## <a name="other-examples"></a>Más példák

Mintalekérdezések más entitásokhoz.

|Lekérdezés típusa |Példa  | Feljegyzés  |
|---------|---------|---------|
|A CID intézkedései    | `{serviceRoot}/Customer_Measure?$filter=CustomerId eq '{CID}'`          |  |
|A CID dúsított márkái    | `{serviceRoot}/BrandShareOfVoiceFromMicrosoft?$filter=CustomerId eq '{CID}'`  |       |
|A CID gazdagabb érdekei    |   `{serviceRoot}/InterestShareOfVoiceFromMicrosoft?$filter=CustomerId eq '{CID}'`       |         |
|In-Clause + Kibontás     | `{serviceRoot}/Customer?$expand=UnifiedActivity,Customer_Measure&$filter=CustomerId in ('{CID}', '{CID}')`         | |

## <a name="not-supported-odata-queries"></a>Nem támogatott OData-lekérdezések

A következő lekérdezéseket a Customer Insights nem támogatja:

- `$filter` a betöltött forrás entitásokon. Csak $filter lekérdezéseket futtathat a Customer Insights által létrehozott rendszerentitásokon.
- `$expand` egy `$search` lekérdezésből. Példa: `Customer?$expand=UnifiedActivity$top=10&$skip=0&$search="corey"`
- `$expand` akkor, `$select` ha az attribútumoknak csak egy részhalmaza van kiválasztva. Példa: `Customer?$select=CustomerId,FullName&$expand=UnifiedActivity&$filter=CustomerId eq '{CID}'`
- `$expand` gazdagított márka- vagy érdeklődési affinitások egy adott ügyfél számára. Példa: `Customer?$expand=BrandShareOfVoiceFromMicrosoft&$filter=CustomerId eq '518291faaa12f6d853c417835d40eb10'`
- A modell kimeneti entitásainak lekérdezése előrejelzés másodlagos kulcs keresztül. Példa: `OOBModelOutputEntity?$filter=HotelCustomerID eq '{AK}'`
