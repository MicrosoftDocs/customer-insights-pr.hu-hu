---
title: A Customer Insights-adatok a Microsoft Dataverse-ben
description: Az Customer Insights-entitások használata táblákként a Microsoft Dataverse-ben.
ms.date: 06/15/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: wimohabb
manager: shellyha
ms.openlocfilehash: 220e01a06711a5d35b8df09e265017a6d8fd0490
ms.sourcegitcommit: 5c9c54ffe045017c19f0042437ada2c101dcaa0f
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/22/2021
ms.locfileid: "6650045"
---
# <a name="work-with-customer-insights-data-in-microsoft-dataverse"></a>A Customer Insights-adatok használata a Microsoft Dataverse-ben

A Customer Insights lehetőséget biztosít a kimeneti entitások elérhetővé tételére a [Microsoft Dataverse](/powerapps/maker/data-platform/data-platform-intro.md)-ben. Ez az integráció lehetővé teszi az egyszerű adatmegosztást és az egyéni fejlesztést kevés kódot használó / kód nélküli megközelítéssel. A kimeneti entitások táblákként lesznek elérhetők a Dataverse-ben. Ezek a táblák lehetővé teszik az olyan forgatókönyveket, mint az [automatizált munkafolyamatok a Power Automate használatával](/power-automate/getting-started), a [modellvezérelt alkalmazások](/powerapps/maker/model-driven-apps/) és a [vászonalapú alkalmazások](/powerapps/maker/canvas-apps/) a Power Apps-ben. Az adatokat bármely más, Dataverse-táblákon alapuló alkalmazáshoz felhasználhatja. A jelenlegi implementáció elsősorban azokat a kereséseket támogatja, ahol a rendelkezésre álló célközönség-információk entitások adatai lekérhetők egy adott ügyfélazonosítóhoz.

## <a name="attach-a-dataverse-environment-to-customer-insights"></a>Dataverse-környezet csatolása a Customer Insights alkalmazáshoz

**Meglévő Dataverse-környezettel rendelkező szervezetek**

Azok a szervezetek, amelyek már használják a Dataverse-t, [használhatják meglévő Dataverse-környezetüket](get-started-paid.md), ha a rendszergazda beállítja a célközönséggel kapcsolatos információkat. Azáltal, hogy az URL-t ad meg a Dataverse-környezethez, ez csatolja az új célközönség információk környezethez. A lehető legjobb teljesítmény biztosítása érdekében a Customer Insights szolgáltatást és a Dataverse-környezeteket ugyanabban a régióban kell üzemeltetni.

Egy Dataverse-környezet csatolásához bontsa ki a **Speciális beállítások** lehetőséget a célközönséggel kapcsolatos információk környezet létrehozásakor. Adja meg a **Microsoft Dataverse-környezet URL-címét**, és jelölje be a jelölőnégyzetet az **Adatmegosztás engedélyezéséhez**.

:::image type="content" source="media/Datasharing-with-DataverseMDL.png" alt-text="alt.":::

**Új szervezet**

Ha új szervezetet hoz létre a Customer Insights beállításakor, automatikusan új Dataverse-környezetet kap.

> [!NOTE]
> Ha a szervezetek már Dataverse-t használnak a bérlőjükben, fontos megjegyezni, hogy [Dataverse környezet létrehozását egy rendszergazda irányítja](/power-platform/admin/control-environment-creation.md). Ha például egy új célközönséggel kapcsolatos információk környezetet hoz létre a szervezeti fiókjával, és a rendszergazda letiltotta a próbaverziók létrehozását mindenki számára, kivéve az Dataverse-adminisztrátorokat, nem hozhat létre új próbaverziós környezetet.
> 
> A Customer Insights-ban létrehozott Dataverse próbaverziós környezetek 3 GB tárhellyel rendelkeznek, amely nem számít bele a bérlő számára elérhető teljes kapacitásba. A fizetett előfizetések 15 GB-os adatbázisra és 20 GB fájltárolásra jogosultak a Dataverse-szolgáltatáshoz.

## <a name="output-entities"></a>Kimeneti entitások

A célközönség információk egyes kimeneti entitásai táblaként érhetők el a Dataverse-ben. Az alábbi szakaszok e táblázatok várt sémáját írják le.

- [CustomerProfile](#customerprofile)
- [AlternateKey](#alternatekey)
- [UnifiedActivity](#unifiedactivity)
- [CustomerMeasure](#customermeasure)
- [Dúsítás](#enrichment)
- [Előrejelzés](#prediction)


### <a name="customerprofile"></a>CustomerProfile

Ez a tábla a Customer Insights egységes ügyfélprofilját tartalmazza. Az egységes ügyfélprofil sémája az egyesítési folyamatban használt entitásoktól és attribútumoktól függ. Az ügyfélprofilséma általában a [CustomerProfile Common Data Model-definíciója](/common-data-model/schema/core/applicationcommon/foundationcommon/crmcommon/solutions/customerinsights/customerprofile) attribútumainak egy részhalmazát tartalmazza.

### <a name="alternatekey"></a>AlternateKey

Az AlternateKey-tábla az egyesítési folyamatban részt vett entitások kulcsait tartalmazza.

|Column  |Típus szerint  |Ismertetés  |
|---------|---------|---------|
|DataSourceName    |Sztring         | Az adatforrás neve. Például: `datasource5`        |
|EntityName        | Sztring        | Az entitás neve a célközönséggel kapcsolatos információkban. Például: `contact1`        |
|AlternateValue    |Sztring         |Az ügyfélazonosítóhoz leképezett alternatív azonosító. Példa: `cntid_1078`         |
|KeyRing           | Többsoros szöveg        | JSON-érték  </br> Minta: [{"dataSourceName":" datasource5 ",</br>"entityName":" contact1",</br>"preferredKey":" cntid_1078",</br>"keys":[" cntid_1078"]}]       |
|Vevőkód         | Sztring        | Az egységes ügyfélprofil azonosítója.         |
|AlternateKeyId     | GUID         |  AlternateKey determinisztikus GUID az msdynci_identifier alapján       |
|msdynci_identifier |   Sztring      |   `DataSourceName|EntityName|AlternateValue`  </br> Minta: `testdatasource|contact1|cntid_1078`    |

### <a name="unifiedactivity"></a>UnifiedActivity

Ez a táblázat a Customer Insights-szolgáltatásban elérhető felhasználók tevékenységeit tartalmazza.

| Column            | Típus szerint        | Ismertetés                                                                              |
|-------------------|-------------|------------------------------------------------------------------------------------------|
| Vevőkód        | Sztring      | Ügyfélprofil-azonosító                                                                      |
| ActivityId        | Sztring      | Az ügyféltevékenység belső azonosítója (elsődleges kulcs)                                       |
| SourceEntityName  | Sztring      | A forrásentitás neve                                                                |
| SourceActivityId  | Sztring      | Elsődleges kulcs a forrásentitásból                                                       |
| ActivityType      | Sztring      | Szemantikai tevékenység típusa vagy az egyéni tevékenység neve                                        |
| ActivityTimeStamp | DATETIME    | Tevékenység időbélyege                                                                      |
| Beosztás             | Sztring      | A tevékenység címe vagy neve                                                               |
| Ismertetés       | Sztring      | Tevékenység leírása                                                                     |
| URL-cím               | Sztring      | Hivatkozás a tevékenységhez specifikus külső URL-címre                                         |
| SemanticData      | JSON-sztring | Tartalmazza a tevékenységtípusra jellemző szemantikai leképezési mezők legfontosabb értékpárjainak listáját |
| RangeIndex        | Sztring      | A tevékenység idővonalának és az érvényes tartomány-lekérdezések rendezésére használt Unix időbélyegző |
| mydynci_unifiedactivityid   | GUID | Az ügyféltevékenység belső azonosítója (ActivityId) |

### <a name="customermeasure"></a>CustomerMeasure

Ez a tábla az ügyfél attribútumalapú mérőszámait tartalmazza.

| Column             | Típus szerint             | Ismertetés                 |
|--------------------|------------------|-----------------------------|
| Vevőkód         | Sztring           | Ügyfélprofil-azonosító        |
| Mérőszámok           | JSON-sztring      | Tartalmazza az adott vevő kulcsérték-párjait a mérőszám nevéhez és értékeihez | 
| msdynci_identifier | Sztring           | `Customer_Measure|CustomerId` |
| msdynci_customermeasureid | GUID      | Ügyfélprofil-azonosító |


### <a name="enrichment"></a>Dúsítás

Ez a tábla a bővítési folyamat kimenetét tartalmazza.

| Column               | Típus szerint             |  Ismertetés                                          |
|----------------------|------------------|------------------------------------------------------|
| Vevőkód           | Sztring           | Ügyfélprofil-azonosító                                 |
| EnrichmentProvider   | Sztring           | A bővítés szolgáltatójának neve                                  |
| EnrichmentType       | Sztring           | A bővítés típusa                                      |
| Értékek               | JSON-sztring      | A bővítési folyamat által előállított attribútumok listája |
| msdynci_enrichmentid | GUID             | A msdynci_identifier elemhez generált determinisztikus GUID |
| msdynci_identifier   | Sztring           | `EnrichmentProvider|EnrichmentType|CustomerId`         |

### <a name="prediction"></a>Előrejelzés

Ez a tábla a modell-előrejelzések kimenetét tartalmazza.

| Column               | Típus szerint        | Ismertetés                                          |
|----------------------|-------------|------------------------------------------------------|
| Vevőkód           | Sztring      | Ügyfélprofil-azonosító                                  |
| ModelProvider        | Sztring      | A modell szolgáltatójának neve                                      |
| Modell                | Sztring      | Modell neve                                                |
| Értékek               | JSON-sztring | A modell által előállított attribútumok listája |
| msdynci_predictionid | GUID        | A msdynci_identifier elemhez generált determinisztikus GUID | 
| msdynci_identifier   | Sztring      |  `Model|ModelProvider|CustomerId`                      |
