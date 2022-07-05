---
title: Bejelentkezés továbbítás a Dynamics 365 Customer Insights Azure Monitor (előzetes verzió)
description: Megtudhatja, hogyan küldhet naplókat a Figyelőnek Microsoft Azure.
ms.date: 12/14/2021
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: article
author: brndkfr
ms.author: bkief
manager: shellyha
searchScope:
- ci-system-diagnostic
- customerInsights
ms.openlocfilehash: 8c72df7054a682244215bbee54968d6aef4bbf59
ms.sourcegitcommit: a97d31a647a5d259140a1baaeef8c6ea10b8cbde
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/29/2022
ms.locfileid: "9052656"
---
# <a name="log-forwarding-in-dynamics-365-customer-insights-with-azure-monitor-preview"></a>Bejelentkezés továbbítás a Dynamics 365 Customer Insights Azure Monitor (előzetes verzió)

Dynamics 365 Customer Insights közvetlen integrációt biztosít a Azure Monitor. Azure Monitor erőforrásnaplók segítségével figyelheti és elküldheti a naplókat az Azure Storage-ba, az Azure Log [Analyticsbe](https://azure.microsoft.com/services/storage/), vagy streamelheti őket az [Azure Event Hubs.](/azure/azure-monitor/logs/log-analytics-overview)[...](https://azure.microsoft.com/services/event-hubs/)

A Customer Insights a következő eseménynaplókat küldi el:

- **Naplózási események**
  - **APIEvent** – lehetővé teszi a Dynamics 365 Customer Insights felhasználói felületen keresztül végzett változáskövetést.
- **Működési események**
  - **WorkflowEvent** – A munkafolyamat lehetővé teszi az adatforrások [beállítását](data-sources.md), [az adatok egyesítését](data-unification.md), [gazdagítását](enrichment-hub.md) és végül [exportálását](export-destinations.md) más rendszerekbe. Mindezek a lépések egyenként is elvégezhetők (például egyetlen exportálást aktiválhatnak). A vezénylést is futtathatja (például az adatforrásokból származó adatok frissítése, amely elindítja az egyesítési folyamatot, amely lekéri a gazdagításokat, és ha elkészült, exportálja az adatokat egy másik rendszerbe). További információt a [WorkflowEvent sémában talál](#workflow-event-schema).
  - **APIEvent** – az összes API-hívás az ügyfelek példányához a következőre:Dynamics 365 Customer Insights. További információ: [APIEvent séma](#api-event-schema).

## <a name="set-up-the-diagnostic-settings"></a>A diagnosztikai beállítások megadása

### <a name="prerequisites"></a>Előfeltételek

A diagnosztika Customer Insightsban való konfigurálásához a következő előfeltételeknek kell teljesülniük:

- Aktív [Azure-előfizetéssel](https://azure.microsoft.com/pricing/purchase-options/pay-as-you-go/) rendelkezik.
- Rendszergazdai [engedélyekkel rendelkezik](permissions.md#admin) a Customer Insights szolgáltatásban.
- A közreműködő **és** a **felhasználói hozzáférés rendszergazdája** szerepkörrel rendelkezik az Azure-beli célerőforráson. Az erőforrás lehet egy Azure Data Lake Storage fiók, egy Azure Event Hub vagy egy Azure Log Analytics-munkaterület. További információ: [Azure-beli szerepkör-hozzárendelések hozzáadása vagy eltávolítása a Azure Portal](/azure/role-based-access-control/role-assignments-portal). Erre az engedélyre a diagnosztikai beállítások Customer Insightsban való konfigurálásakor van szükség, és a sikeres beállítás után módosítható.
- [Teljesültek az Azure Storage, az Azure Event Hub vagy az Azure Log Analytics célkövetelményei](/azure/azure-monitor/platform/diagnostic-settings#destination-requirements).
- Legalább **olvasó** szerepkörrel rendelkezik azon az erőforráscsoporton, amelyhez az erőforrás tartozik.

### <a name="set-up-diagnostics-with-azure-monitor"></a>Diagnosztika beállítása a Azure Monitor

1. A Customer Insights válassza a System **Diagnostics** > **lehetőséget** a példányt konfigurált diagnosztikai célhelyek megtekintéséhez.

1. Válassza a Cél **hozzáadása lehetőséget**.

   > [!div class="mx-imgBorder"]
   > ![Diagnosztikai kapcsolat](media/diagnostics-pane.png "Diagnosztikai kapcsolat")

1. Adjon meg egy nevet a **Diagnosztikai cél neve** mezőben.

1. Válassza ki az **Azure-előfizetés bérlőjét** a célerőforrással, majd válassza a bejelentkezés **lehetőséget**.

1. Válassza ki az **erőforrás típusát** (Storage-fiók, eseményközpont vagy log analytics).

1. Válassza ki a **célerőforrás előfizetését**.

1. Válassza ki a **célerőforrás erőforráscsoportját**.

1. Válassza ki az **erőforrást**.

1. Erősítse meg az **adatvédelmi és megfelelőségi** nyilatkozatot.

1. Válassza **Csatlakozás a rendszerhez** lehetőséget a célerőforráshoz való csatlakozáshoz. A naplók 15 perc elteltével kezdenek megjelenni a célhelyen, ha az API használatban van, és eseményeket hoz létre.

### <a name="remove-a-destination"></a>Célhely eltávolítása

1. Nyissa meg a **Rendszerdiagnosztikát** > **·**.

1. Válassza ki a diagnosztikai célhelyet a listából.

1. **A Műveletek** oszlopban válassza a **Törlés** ikont.

1. Erősítse meg a törlést a napló továbbításának leállításához. Az Azure-előfizetés erőforrása nem törlődik. A Műveletek **oszlopban található hivatkozásra kattintva megnyithatja a** Azure Portal a kiválasztott erőforráshoz, és ott törölheti azt.

## <a name="log-categories-and-event-schemas"></a>Naplókategóriák és eseménysémák

Jelenleg [az API-események](apis.md) és a munkafolyamat-események támogatottak, és a következő kategóriák és sémák érvényesek.
A naplóséma a [Azure Monitor közös sémát követi](/azure/azure-monitor/platform/resource-logs-schema#top-level-common-schema).

### <a name="categories"></a>Kategóriák

A Customer Insights két kategóriát kínál:

- **Naplózási események**: [API-események](#api-event-schema) a szolgáltatás konfigurációs változásainak nyomon követéséhez. `POST|PUT|DELETE|PATCH` a műveletek ebbe a kategóriába tartoznak.
- **Működési események**: A [szolgáltatás használata során létrehozott API-események](#api-event-schema) vagy [munkafolyamat-események](#workflow-event-schema).  Ilyenek például `GET` egy munkafolyamat kérései vagy végrehajtási eseményei.

## <a name="configuration-on-the-destination-resource"></a>Konfiguráció a célerőforráson

Az erőforrástípus választása alapján a következő lépések automatikusan érvénybe lépnek:

### <a name="storage-account"></a>Storage account

A Customer Insights szolgáltatásnév lekéri a **Storage-fiók közreműködő** engedélyt a kiválasztott erőforráshoz, és két tárolót hoz létre a kiválasztott névtérben:

- `insight-logs-audit` ellenőrzési eseményeket **tartalmaz**
- `insight-logs-operational` működési eseményeket **tartalmaz**

### <a name="event-hub"></a>Esemény központja

A Customer Insights szolgáltatásnév megkapja az **Azure Event Hubs-adattulajdonosi** engedélyt az erőforráshoz, és két Event Hubs hoz létre a kiválasztott névtér alatt:

- `insight-logs-audit` ellenőrzési eseményeket **tartalmaz**
- `insight-logs-operational` működési eseményeket **tartalmaz**

### <a name="log-analytics"></a>Log Analytics

A Customer Insights szolgáltatásnév log **Analytics-közreműködő** engedélyt kap az erőforráshoz. A naplók a Log Analytics-munkaterület **Naplótáblák** > **naplókezelése** > **alatt** lesznek elérhetők. Bontsa ki a **Naplókezelés** megoldást, és keresse meg az `CIEventsAudit` és `CIEventsOperational` táblákat.

- `CIEventsAudit` ellenőrzési eseményeket **tartalmaz**
- `CIEventsOperational` működési eseményeket **tartalmaz**

**A Lekérdezések** ablakban bontsa ki a **Naplózási** megoldást, és keresse meg a `CIEvents`.

## <a name="event-schemas"></a>Eseménysémák

Az API-események és munkafolyamat-események közös struktúrával és részletekkel rendelkeznek, ahol különböznek egymástól, lásd: [API-eseményséma](#api-event-schema) vagy [munkafolyamat-eseményséma](#workflow-event-schema).

### <a name="api-event-schema"></a>API-eseményséma

| Mező             | Adattípus  | Kötelező/nem kötelező | Description       | Példa        |
| ----------------- | --------- | ----------------- | --------------------- | ------------------------ |
| `time`            | Időbélyegző | Szükséges          | Az esemény időbélyegzője (UTC)       | `2020-09-08T09:48:14.8050869Z`         |
| `resourceId`      | Sztring    | Szükséges          | Az eseményt kibocsátó példány ResourceId azonosítója         | `/SUBSCRIPTIONS/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXX/RESOURCEGROUPS/<RESOURCEGROUPNAME>/`<br>`PROVIDERS/MICROSOFT.D365CUSTOMERINSIGHTS/`<br>`INSTANCES/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXX`  |
| `operationName`   | Sztring    | Szükséges          | Az esemény által képviselt művelet neve.                                                                                                                | `Workflows.GetWorkFlowStatusAsync`                                                                                                                                       |
| `category`        | Sztring    | Szükséges          | Az esemény naplókategóriája. Vagy `Operational`, vagy `Audit`. Minden POST/PUT/PATCH/DELETE HTTP-kérés meg van címkézve `Audit`, minden más a`Operational` | `2020-09-08T09:48:14.8050869Z`                                                                                                                                           |
| `resultType`      | Sztring    | Szükséges          | Az esemény állapota. `Success`, `ClientError`, `Failure`                                                                                                        |                                                                                                                                                                          |
| `resultSignature` | Sztring    | Lehetséges          | Az esemény eredményállapota. Ha a művelet egy REST API hívásnak felel meg, akkor ez a HTTP-állapotkód.        | `200`             |
| `durationMs`      | Long      | Lehetséges          | A művelet időtartama ezredmásodpercben.     | `133`     |
| `callerIpAddress` | Sztring    | Lehetséges          | Hívó IP-címe, ha a művelet egy nyilvánosan elérhető IP-címről származó API-hívásnak felel meg.                                                 | `144.318.99.233`         |
| `identity`        | Sztring    | Lehetséges          | A műveletet végző felhasználó vagy alkalmazás identitását leíró JSON-objektum.       | Lásd az [Identitás](#identity-schema) szakaszt.     |  
| `properties`      | Sztring    | Lehetséges          | JSON-objektum több tulajdonsággal az adott eseménykategóriához.      | Lásd a [Tulajdonságok](#api-properties-schema) szakaszt.    |
| `level`           | Sztring    | Szükséges          | Az esemény súlyossági szintje.    | `Informational`, `Warning`, `Error` vagy `Critical`.           |
| `uri`             | Sztring    | Lehetséges          | Abszolút kérés URI-ja.    |               |

#### <a name="identity-schema"></a>Identitásséma

A `identity` JSON-objektum szerkezete a következő

```json
{
  "Authorization" : {
    "UserRole": "Admin",
    "RequiredRoles": [
      "Contributor",
      "Viewer"
      ]
    },
  "Claims" {
    "claimNameX" : "claimValueX",
    "claimNameY" : "claimValueY"
   }
}  
```

| Mező                         | Description                                                                                                                          |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| `Authorization.UserRole`      | Hozzárendelt szerepkör a felhasználóhoz vagy az alkalmazáshoz. További információ: [Felhasználói engedélyek](permissions.md).                                     |
| `Authorization.RequiredRoles` | A művelet végrehajtásához szükséges szerepkörök. `Admin` szerepkör minden művelet elvégzésére engedélyezett.                                                    |
| `Claims`                      | A felhasználó vagy az alkalmazás JSON-webtokenjének (JWT) jogcímei. A jogcímtulajdonságok szervezetenként és konfigurációnként Azure Active Directory eltérőek lehetnek. |

#### <a name="api-properties-schema"></a>API-tulajdonságok sémája

[Az API-események](apis.md) a következő tulajdonságokkal rendelkeznek.

| Mező                        | Description                                                                                                            |
| ---------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| `properties.eventType`       | Mindig `ApiEvent`, a naplóeseményt API-eseményként jelölve meg.                                                                 |
| `properties.userAgent`       | A kérést vagy `unknown`.                                                                        |
| `properties.method`          | HTTP-módszer:`GET/POST/PUT/PATCH/HEAD`.                                                                                |
| `properties.path`            | A kérés relatív elérési útja.                                                                                          |
| `properties.origin`          | URI, amely jelzi, hogy a lekérés honnan származik, vagy `unknown`.                                                                  |
| `properties.operationStatus` | `Success` a 400-as < HTTP-állapotkódhoz <br> `ClientError` http-állapotkódhoz < 500 <br> `Error` HTTP-állapot esetén >= 500 |
| `properties.tenantId`        | Szervezet azonosítója                                                                                                        |
| `properties.tenantName`      | A szervezet neve.                                                                                              |
| `properties.callerObjectId`  | Azure Active Directory A hívó ObjectId azonosítója.                                                                         |
| `properties.instanceId`      | Vásárlói betekintések`instanceId`                                                                                         |

### <a name="workflow-event-schema"></a>Munkafolyamat-eseményséma

A munkafolyamat több lépést tartalmaz. [Adatforrások](data-sources.md) betöltése, [adatok egyesítése](data-unification.md), [gazdagítása](enrichment-hub.md) és [exportálása](export-destinations.md). Ezek a lépések egyenként vagy a következő folyamatokkal vezényelten is futtathatók.

#### <a name="operation-types"></a>Művelettípusok

| OperationType     | Csoportosítás                                     |
| ----------------- | ----------------------------------------- |
| Lenyelés         | [Adatforrások](data-sources.md)           |
| DataPreparation   | [Adatforrások](data-sources.md)           |
| Megfeleltetés               | [Adategyesítés](data-unification.md)   |
| Match             | [Adategyesítés](data-unification.md)   |
| Összefűzés             | [Adategyesítés](data-unification.md)   |
| ProfilStore      | [Ügyfélprofilok](customer-profiles.md) |
| Keresés            | [Ügyfélprofilok](customer-profiles.md) |
| Tevékenys.          | [Tevékenységek](activities.md)                  |
| Attribútumbecslések | [Szegmensek és mértékek](segments.md)      |
| EntityMeasures    | [Szegmensek és mértékek](segments.md)      |
| Mértékek          | [Szegmensek és mértékek](segments.md)      |
| Szegmentálás      | [Szegmensek és mértékek](segments.md)      |
| Dúsítás        | [Dúsítás](enrichment-hub.md)                                          |
| Intelligencia      | [Előrejelzések](predictions-overview.md)                                          |
| AiBuilder         | [Előrejelzések](predictions-overview.md)                                          |
| Elemzések          | [Előrejelzések](predictions-overview.md)                                          |
| Export            | [Exportálások](export-destinations.md)                                          |
| Modellkezelés   | [Előrejelzések](custom-models.md)                                           |
| Kapcsolat      | [Adategyesítés](relationships.md)                                           |

#### <a name="field-description"></a>Mező leírása

| Mező           | Adattípus  | Kötelező/nem kötelező | Description                                                                                                                                                   | Példa                                                                                                                                                                  |
| --------------- | --------- | ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `time`          | Időbélyegző | Szükséges          | Az esemény időbélyegzője (UTC).                                                                                                                                 | `2020-09-08T09:48:14.8050869Z`                                                                                                                                           |
| `resourceId`    | Sztring    | Szükséges          | Az eseményt kibocsátó példány ResourceId azonosítója.                                                                                                            | `/SUBSCRIPTIONS/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXX/RESOURCEGROUPS/<RESOURCEGROUPNAME>/`<br>`PROVIDERS/MICROSOFT.D365CUSTOMERINSIGHTS/`<br>`INSTANCES/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXX` |
| `operationName` | Sztring    | Szükséges          | Az esemény által képviselt művelet neve. `{OperationType}.[WorkFlow|Task][Started|Completed]`. Lásd: [Művelettípusok](#operation-types) referenciaként. | `Segmentation.WorkflowStarted`,<br> `Segmentation.TaskStarted`, <br> `Segmentation.TaskCompleted`, <br> `Segmentation.WorkflowCompleted`                                 |
| `category`      | Sztring    | Szükséges          | Az esemény naplókategóriája. Mindig `Operational` munkafolyamat-eseményekhez                                                                                           | `Operational`                                                                                                                                                            |
| `resultType`    | Sztring    | Szükséges          | Az esemény állapota. `Running`, `Skipped`, `Successful`, `Failure`                                                                                            |                                                                                                                                                                          |
| `durationMs`    | Long      | Lehetséges          | A művelet időtartama ezredmásodpercben.                                                                                                                    | `133`                                                                                                                                                                    |
| `properties`    | Sztring    | Lehetséges          | JSON-objektum több tulajdonsággal az adott eseménykategóriához.                                                                                        | Lásd a Munkafolyamat tulajdonságai című [alszakaszt](#workflow-properties-schema)                                                                                                       |
| `level`         | Sztring    | Szükséges          | Az esemény súlyossági szintje.                                                                                                                                  | `Informational`, `Warning` vagy `Error`                                                                                                                                   |
|                 |

#### <a name="workflow-properties-schema"></a>Munkafolyamat-tulajdonságok sémája

A munkafolyamat-események a következő tulajdonságokkal rendelkeznek.

| Mező              | Workflow | Feladatok | Description            |
| ------------------------------- | -------- | ---- | ----------- |
| `properties.eventType`                       | Igen      | Igen  | Mindig `WorkflowEvent`, az esemény munkafolyamat-eseményként való megjelölése.                                                                                                                                                                                                |
| `properties.workflowJobId`                   | Igen      | Igen  | A munkafolyamat futtatásának azonosítója. A munkafolyamat végrehajtásán belüli összes munkafolyamat- és feladatesemény azonos `workflowJobId`.                                                                                                                                   |
| `properties.operationType`                   | Igen      | Igen  | A művelet azonosítója, lásd: [Művelettípusok](#operation-types).                                                                                                                                                                               |
| `properties.tasksCount`                      | Igen      | No   | Csak munkafolyamat. A munkafolyamat által elindított feladatok száma.                                                                                                                                                                                                       |
| `properties.submittedBy`                     | Igen      | No   | Opcionális. Csak munkafolyamat-események. A Azure Active Directory [munkafolyamatot elindító felhasználó](/azure/marketplace/find-tenant-object-id#find-user-object-id) objectId azonosítója, lásd még `properties.workflowSubmissionKind`.                                   |
| `properties.workflowType`                    | Igen      | No   | `full` vagy `incremental` frissítsen.                                                                                                                                                                                                                            |
| `properties.workflowSubmissionKind`          | Igen      | No   | `OnDemand` vagy `Scheduled`.                                                                                                                                                                                                                                  |
| `properties.workflowStatus`                  | Igen      | No   | `Running` vagy `Successful`.                                                                                                                                                                                                                                 |
| `properties.startTimestamp`                  | Igen      | Igen  | UTC-időbélyegző`yyyy-MM-ddThh:mm:ss.SSSSSZ`                                                                                                                                                                                                                  |
| `properties.endTimestamp`                    | Igen      | Igen  | UTC-időbélyegző`yyyy-MM-ddThh:mm:ss.SSSSSZ`                                                                                                                                                                                                                  |
| `properties.submittedTimestamp`              | Igen      | Igen  | UTC-időbélyegző`yyyy-MM-ddThh:mm:ss.SSSSSZ`                                                                                                                                                                                                                  |
| `properties.instanceId`                      | Igen      | Igen  | Vásárlói betekintések`instanceId`                                                                                                                                                                                                                              |  
| `properties.identifier`                      | No       | Igen  | - Az OperationType = esetében `Export` az azonosító az exportálási konfiguráció guid azonosítója. <br> - Az OperationType =, `Enrichment` ez a gazdagítás guidja <br> - Az OperationType `Measures` és `Segmentation` az, az azonosító az entitás neve. |
| `properties.friendlyName`                    | No       | Igen  | Az exportálás vagy a feldolgozott entitás felhasználóbarát neve.                                                                                                                                                                                           |
| `properties.error`                           | No       | Igen  | Opcionális. Hibaüzenet további részletekkel.                                                                                                                                                                                                                  |
| `properties.additionalInfo.Kind`             | No       | Igen  | Opcionális. Csak az OperationType típushoz `Export`. Az exportálás típusát azonosítja. További információt az exportálási célhelyek [áttekintésében talál](export-destinations.md).                                                                                          |
| `properties.additionalInfo.AffectedEntities` | No       | Igen  | Opcionális. Csak az OperationType típushoz `Export`. Az exportálásban konfigurált entitások listáját tartalmazza.                                                                                                                                                            |
| `properties.additionalInfo.MessageCode`      | No       | Igen  | Opcionális. Csak az OperationType típushoz `Export`. Részletes üzenet az exportáláshoz.                                                                                                                                                                                 |
| `properties.additionalInfo.entityCount`      | No       | Igen  | Opcionális. Csak az OperationType típushoz `Segmentation`. A szegmens tagjainak teljes számát jelzi.                                                                                                                                                    |
