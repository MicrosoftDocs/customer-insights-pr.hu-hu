---
title: OData példák az Dynamics 365 Customer Insights API-khoz
description: Gyakran használt példák az Open Data Protocol (OData) protokollra, hogy lekérdezzék a Customer Insights API-kat az adatok áttekintéséhez.
ms.date: 05/25/2022
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
ms.reviewer: mhart
manager: shellyha
ms.openlocfilehash: cdadd72bfe4272d8d83d923baaa6fd40d008473b
ms.sourcegitcommit: bf65bc0a54cdab71680e658e1617bee7b2c2bb68
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/27/2022
ms.locfileid: "8808464"
---
# <a name="odata-query-examples"></a>Példák OData lekérdezésre

Az Open Data Protocol (OData) egy adatelérési protokoll, amely olyan alapvető protokollokra épül, mint a HTTP. Olyan általánosan elfogadott módszereket használ, mint a REST az interneten. Az OData-szolgáltatások felhasználására különféle könyvtárak és eszközök használhatók.

Ez a cikk felsorol néhány gyakran kért példalekérdezést, amelyek segítenek a saját implementációk létrehozásában az [Ügyfélelemzés API-k alapján](apis.md).

Módosítania kell a lekérdezésmintákat, hogy azok a célkörnyezetekben működjenek: 

- {serviceRoot}: `https://api.ci.ai.dynamics.com/v1/instances/{instanceId}` hol {instanceId} van a lekérdezni kívánt Customer Insights-környezet GUID azonosítója. A [ListAllInstances művelet](https://developer.ci.ai.dynamics.com/api-details#api=CustomerInsights&operation=Get-all-instances) lehetővé teszi, hogy megtalálja azt, amelyhez {InstanceId} hozzáféréssel rendelkezik.
- {CID}: Egységes ügyfélbejegyzés GUID azonosítója. Példa: `ce759201f786d590bf2134bff576c369`.
- {AlternateKey}: Egy ügyfélbejegyzés elsődleges kulcsának azonosítója egy adatforrás. Példa: `CNTID_1002`
- {DSname}: Karakterlánc egy adatforrás entitásnevével, amely a Customer Insights szolgáltatásba kerül. Példa: `Website_contacts`.
- {SegmentName}: Karakterlánc egy szegmens kimeneti entitásnevével a Customer Insights alkalmazásban. Példa: `Male_under_40`.

## <a name="customer"></a>Ügyfelünk

Az alábbi táblázat a *Vevő* entitás mintalekérdezéseit tartalmazza.

|Lekérdezés típusa |Példa  | Feljegyzés  |
|---------|---------|---------|
|Egyetlen vevő azonosítója     | `{serviceRoot}/Customer?$filter=CustomerId eq '{CID}'`          |  |
|Másodlagos kulcs    | `{serviceRoot}/Customer?$filter={DSname_EntityName_PrimaryKeyColumnName} eq '{AlternateKey}'`         |  A helyettesítő kulcsok megmaradnak az egyesített vevő entitásban       |
|Select   | `{serviceRoot}/Customer?$select=CustomerId,FullName&$filter=customerid eq '1'`        |         |
|Ennyi idő múlva:    | `{serviceRoot}/Customer?$filter=CustomerId in ('{CID1}',’{CID2}’)`        |         |
|Másodlagos kulcs + hüvelyk   | `Customer?$filter={DSname_EntityName_PrimaryKeyColumnName} in ('{AlternateKey}','{AlternateKey}')`         |         |
|Keresés  | `{serviceRoot}/Customer?$top=10&$skip=0&$search="string"`        |   A keresési karakterlánc top 10 találatát adja vissza      |
|Szegmenstagság  | `{serviceRoot}/Customer?select=*&$filter=IsMemberOfSegment('{SegmentName}')&$top=10`     | A szegmentálási entitásból származó sorok előre beállított számát adja eredményül.      |

## <a name="unified-activity"></a>Egységes tevékenység

Az alábbi táblázat a *UnifiedActivity* entitás mintalekérdezéseit tartalmazza.

|Lekérdezés típusa |Példa  | Feljegyzés  |
|---------|---------|---------|
|A CID tevékenysége     | `{serviceRoot}/UnifiedActivity?$filter=CustomerId eq '{CID}'`          | Egy adott ügyfélprofil tevékenységeinek felsorolása |
|Tevékenység időkeret    | `{serviceRoot}/UnifiedActivity?$filter=CustomerId eq '{CID}' and ActivityTime gt 2017-01-01T00:00:00.000Z and ActivityTime lt 2020-01-01T00:00:00.000Z`     |  Ügyfélprofil tevékenységei időkeret       |
|Tevékenység típusa    |   `{serviceRoot}/UnifiedActivity?$filter=CustomerId eq '{CID}' and ActivityType eq '{ActivityName}'`        |         |
|A megjelenítendő név tevékenysége     | `{serviceRoot}/UnifiedActivity$filter=CustomerId eq ‘{CID}’ and ActivityTypeDisplay eq ‘{ActivityDisplayName}’`        | |
|Tevékenységrendezés    | `{serviceRoot}/UnifiedActivity?$filter=CustomerId eq ‘{CID}’ & $orderby=ActivityTime asc`     |  Növekvő vagy csökkenő tevékenységek rendezése       |
|Szegmenstagságból kibővült tevékenység  |   `{serviceRoot}/Customer?$expand=UnifiedActivity,Customer_Measure&$filter=CustomerId eq '{CID}'`     |         |

## <a name="other-examples"></a>Más példák

Az alábbi táblázat más entitások mintalekérdezéseit tartalmazza.

|Lekérdezés típusa |Példa  | Feljegyzés  |
|---------|---------|---------|
|A CID mérései    | `{serviceRoot}/Customer_Measure?$filter=CustomerId eq '{CID}'`          |  |
|A CID dúsított márkái    | `{serviceRoot}/BrandShareOfVoiceFromMicrosoft?$filter=CustomerId eq '{CID}'`  |       |
|A CID gazdagodott érdekei    |   `{serviceRoot}/InterestShareOfVoiceFromMicrosoft?$filter=CustomerId eq '{CID}'`       |         |
|Záradékon belül + kibontás     | `{serviceRoot}/Customer?$expand=UnifiedActivity,Customer_Measure&$filter=CustomerId in ('{CID}', '{CID}')`         | |

## <a name="not-supported-odata-queries"></a>Nem támogatott OData-lekérdezések

A Customer Insights nem támogatja a következő lekérdezéseket:

- `$filter` a beolvasott forrás entitásokon. A $filter lekérdezéseket csak a Customer Insights által létrehozott rendszertentitásokon futtathatja.
- `$expand` lekérdezésből`$search`. Példa: `Customer?$expand=UnifiedActivity$top=10&$skip=0&$search="corey"`
- `$expand` ha `$select` csak az attribútumok egy részhalmaza van kijelölve. Példa: `Customer?$select=CustomerId,FullName&$expand=UnifiedActivity&$filter=CustomerId eq '{CID}'`
- `$expand` gazdagított márka- vagy érdeklődési affinitás egy adott ügyfél számára. Példa: `Customer?$expand=BrandShareOfVoiceFromMicrosoft&$filter=CustomerId eq '518291faaa12f6d853c417835d40eb10'`
- Modell kimeneti entitásainak lekérdezése előrejelzés másodlagos kulcs keresztül. Példa: `OOBModelOutputEntity?$filter=HotelCustomerID eq '{AK}'`
