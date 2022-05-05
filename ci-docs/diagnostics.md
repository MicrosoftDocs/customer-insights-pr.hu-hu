---
title: Naplózás Dynamics 365 Customer Insights az Azure Monitor segítségével
description: További információ arról, hogyan küldhet naplókat a Monitornak Microsoft Azure.
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
ms.openlocfilehash: 18fc072d129be6b4fc5470b1057f592dc2638216
ms.sourcegitcommit: b7dbcd5627c2ebfbcfe65589991c159ba290d377
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/27/2022
ms.locfileid: "8642481"
---
# <a name="log-forwarding-in-dynamics-365-customer-insights-with-azure-monitor-preview"></a>Bejelentkezés továbbítás az Dynamics 365 Customer Insights Azure Monitorral (előzetes verzió)

Dynamics 365 Customer Insights közvetlen integrációt biztosít az Azure Monitorral. Az Azure Monitor erőforrásnaplói lehetővé teszik a naplók figyelését és küldését az [Azure Storage-ba](https://azure.microsoft.com/services/storage/), [az Azure Log Analytics-be](/azure/azure-monitor/logs/log-analytics-overview), vagy streamelheti azokat [az Azure Event Hubs](https://azure.microsoft.com/services/event-hubs/).

A Customer Insights a következő eseménynaplókat küldi el:

- **Események naplózása**
  - **APIEvent** - lehetővé teszi a Dynamics 365 Customer Insights felhasználói felületen keresztül végzett változáskövetést.
- **Operatív események**
  - **WorkflowEvent** – A munkafolyamat lehetővé teszi az adatforrások [beállítását](data-sources.md), egyesítését [és](data-unification.md) gazdagítását [,](enrichment-hub.md) és végül [az adatok exportálását](export-destinations.md) más rendszerekbe. Mindezeket a lépéseket egyedileg (pl. egyetlen exportálás kiváltása) vagy vezényelhető (pl. olyan adatforrásokból származó adatfrissítés, amely elindítja az egyesítési folyamatot, amely további gazdagodásokat hajt végre, és miután elvégezte az adatok exportálását egy másik rendszerbe). További részletekért tekintse meg a [WorkflowEvent schema című témakört](#workflow-event-schema).
  - **APIEvent** - az összes API-hívás az ügyfelek példányához.Dynamics 365 Customer Insights További részletekért lásd az [APIEvent schema című témakört](#api-event-schema).

## <a name="set-up-the-diagnostic-settings"></a>A diagnosztikai beállítások beállítása

### <a name="prerequisites"></a>Előfeltételek

A diagnosztika Customer Insightsban való konfigurálásához a következő előfeltételeknek kell teljesülniük:

- Aktív [Azure-előfizetéssel](https://azure.microsoft.com/pricing/purchase-options/pay-as-you-go/) rendelkezik.
- Rendszergazdai [engedélyekkel rendelkezik](permissions.md#admin) a Customer Insights alkalmazásban.
- Az Azure célerőforrásán a közreműködő **és** a Felhasználói hozzáférés rendszergazdája **szerepkörrel rendelkezik**. Az erőforrás lehet Azure Storage-fiók, Azure Event Hub vagy Azure Log Analytics-munkaterület. További információt az Azure-szerepkör-hozzárendelések hozzáadása és eltávolítása az Azure Portal [használatával című témakörben talál](/azure/role-based-access-control/role-assignments-portal).
- [Az Azure Storage, az Azure Event Hub vagy az Azure Log Analytics célkövetelményei](/azure/azure-monitor/platform/diagnostic-settings#destination-requirements) teljesültek.
- Legalább abban az **erőforráscsoportban rendelkezik olvasó** szerepkörrel, amelyhez az erőforrás tartozik.

### <a name="set-up-diagnostics-with-azure-monitor"></a>Diagnosztikák beállítása az Azure Monitorral

1. A Customer Insights programban válassza a **SystemDiagnostics** > **lehetőséget** a példányban konfigurált diagnosztikai célok megtekintéséhez.

1. Válassza a Cél hozzáadása **lehetőséget**.

   > [!div class="mx-imgBorder"]
   > ![Diagnosztikai kapcsolat](media/diagnostics-pane.png "Diagnosztikai kapcsolat")

1. Adjon meg egy nevet a **Diagnosztikai cél** neve mezőben.

1. Válassza ki az **Azure-előfizetés bérlőjét** a célerőforrással, és válassza a Bejelentkezés **lehetőséget**.

1. Válassza ki az **erőforrás típusát** (Tárfiók, Eseményközpont vagy naplóelemzés).

1. Válassza ki a **célerőforrás előfizetését**.

1. Válassza ki a **célerőforrás erőforráscsoportját**.

1. Válassza ki az **erőforrást**.

1. Erősítse meg az **adatvédelmi és megfelelőségi** nyilatkozatot.

1. Válassza **a Csatlakozás a rendszerhez** lehetőséget a célerőforráshoz való csatlakozáshoz. A naplók 15 perc elteltével jelennek meg a célban, ha az API használatban van, és eseményeket generál.

### <a name="remove-a-destination"></a>Cél eltávolítása

1. Menj a **SystemDiagnostics** > **oldalra**.

1. Válassza ki a diagnosztikai célt a listában.

1. **A Műveletek** oszlopban jelölje ki a **Törlés ikont**.

1. Erősítse meg a törlést a naplótovábbítás leállításához. Az Azure-előfizetés erőforrása nem törlődik. A Műveletek **oszlopban kiválaszthatja a hivatkozást a** kijelölt erőforrás Azure Portaljának megnyitásához és ott történő törléséhez.

## <a name="log-categories-and-event-schemas"></a>Kategóriák és eseménysémák naplózása

Jelenleg [az API-események](apis.md) és munkafolyamat-események támogatottak, és a következő kategóriák és sémák érvényesek.
A naplóséma az [Azure Monitor közös sémáját követi](/azure/azure-monitor/platform/resource-logs-schema#top-level-common-schema).

### <a name="categories"></a>Kategóriák

A Customer Insights két kategóriát kínál:

- **Események** naplózása: [API-események](#api-event-schema) a szolgáltatás konfigurációs változásainak nyomon követéséhez. `POST|PUT|DELETE|PATCH` műveletek ebbe a kategóriába tartoznak.
- **Működési események**: [A szolgáltatás használata során létrehozott API-események](#api-event-schema) vagy [munkafolyamat-események](#workflow-event-schema).  `GET` Például egy munkafolyamat kérései vagy végrehajtási eseményei.

## <a name="configuration-on-the-destination-resource"></a>Konfiguráció a célerőforráson

Az erőforrástípuson megadott beállítások alapján a következő lépések automatikusan érvénybe lépnek:

### <a name="storage-account"></a>Storage account

A Customer Insights szolgáltatásnév megkapja a **Tárfiók közreműködő** engedélyt a kijelölt erőforrásra, és két tárolót hoz létre a kijelölt névtér alatt:

- `insight-logs-audit`**ellenőrzési eseményeket tartalmaz**
- `insight-logs-operational`**működési eseményeket tartalmaz**

### <a name="event-hub"></a>Esemény központja

A Customer Insights szolgáltatásnév megkapja az **Azure Event Hubs Data Owner** engedélyt az erőforráshoz, és két Event Hubs hoz létre a kiválasztott névtér alatt:

- `insight-logs-audit`**ellenőrzési eseményeket tartalmaz**
- `insight-logs-operational`**működési eseményeket tartalmaz**

### <a name="log-analytics"></a>Log Analytics

A Customer Insights szolgáltatás főkiszolgálója megkapja a **Log Analytics közreműködő** engedélyt az erőforrásra. A naplók a Kijelölt Log Analytics-munkaterületen a LogsTablesLog Management alatt **lesznek elérhetők** > **.** > **·** Bontsa ki a **Naplókezelés** megoldást, és keresse meg a és `CIEventsAudit` a `CIEventsOperational` táblákat.

- `CIEventsAudit`**ellenőrzési eseményeket tartalmaz**
- `CIEventsOperational`**működési eseményeket tartalmaz**

**A Lekérdezések ablakban bontsa** ki a **Naplózási** megoldást, és keresse meg a kereséssel `CIEvents` megadott példalekérdezéseket.

## <a name="event-schemas"></a>Eseménysémák

Az API-események és munkafolyamat-események közös struktúrával és részletekkel rendelkeznek, ahol különböznek egymástól, lásd: [API-eseménysémát](#api-event-schema) vagy [munkafolyamat-eseménysémát](#workflow-event-schema).

### <a name="api-event-schema"></a>API-eseményséma

| Mező             | Adattípus  | Kötelező/nem kötelező | Description       | Példa        |
| ----------------- | --------- | ----------------- | --------------------- | ------------------------ |
| `time`            | Időbélyegző | Szükséges          | Az esemény időbélyegzője (UTC)       | `2020-09-08T09:48:14.8050869Z`         |
| `resourceId`      | Sztring    | Szükséges          | Az eseményt kibocsátó példány ResourceId azonosítója         | `/SUBSCRIPTIONS/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXX/RESOURCEGROUPS/<RESOURCEGROUPNAME>/`<br>`PROVIDERS/MICROSOFT.D365CUSTOMERINSIGHTS/`<br>`INSTANCES/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXX`  |
| `operationName`   | Sztring    | Szükséges          | Az esemény által képviselt művelet neve.                                                                                                                | `Workflows.GetWorkFlowStatusAsync`                                                                                                                                       |
| `category`        | Sztring    | Szükséges          | Az esemény naplókategóriája. Vagy `Operational`, vagy `Audit`. Minden POST/PUT/PATCH/DELETE HTTP kérés címkével van ellátva `Audit`, minden más`Operational` | `2020-09-08T09:48:14.8050869Z`                                                                                                                                           |
| `resultType`      | Sztring    | Szükséges          | Az esemény állapota. `Success`, `ClientError`, `Failure`                                                                                                        |                                                                                                                                                                          |
| `resultSignature` | Sztring    | Lehetséges          | Az esemény eredményállapota. Ha a művelet REST API hívásnak felel meg, akkor az a HTTP-állapotkód.        | `200`             |
| `durationMs`      | Long      | Lehetséges          | A művelet időtartama ezredmásodpercben.     | `133`     |
| `callerIpAddress` | Sztring    | Lehetséges          | Hívó IP-címe, ha a művelet egy nyilvánosan elérhető IP-címről származó API-hívásnak felel meg.                                                 | `144.318.99.233`         |
| `identity`        | Sztring    | Lehetséges          | JSON-objektum, amely a műveletet végző felhasználó vagy alkalmazás identitását írja le.       | Lásd: [Identitás](#identity-schema) szakasz.     |  
| `properties`      | Sztring    | Lehetséges          | JSON-objektum, amely több tulajdonsággal rendelkezik az adott eseménykategóriához.      | Lásd: [Tulajdonságok](#api-properties-schema) szakasz.    |
| `level`           | Sztring    | Szükséges          | Az esemény súlyossági szintje.    | `Informational`, `Warning`, `Error`, vagy `Critical`.           |
| `uri`             | Sztring    | Lehetséges          | Abszolút kérés URI-ja.    |               |

#### <a name="identity-schema"></a>Identitásséma

A `identity` JSON objektum szerkezete a következő

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
| `Authorization.UserRole`      | Hozzárendelt szerepkör a felhasználóhoz vagy az alkalmazáshoz. További információt a felhasználói engedélyek [című témakörben talál](permissions.md).                                     |
| `Authorization.RequiredRoles` | A művelet végrehajtásához szükséges szerepkörök. `Admin` szerepkör minden műveletet elvégezhet.                                                    |
| `Claims`                      | A felhasználó vagy alkalmazás JSON web token (JWT) jogcímei. A jogcímtulajdonságok szervezetenként és Azure Active Directory konfigurációnként eltérőek. |

#### <a name="api-properties-schema"></a>API-tulajdonságok sémája

[Az API-események](apis.md) a következő tulajdonságokkal rendelkeznek.

| Mező                        | Description                                                                                                            |
| ---------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| `properties.eventType`       | Mindig `ApiEvent`, a naplóeseményt API-eseményként jelölve meg.                                                                 |
| `properties.userAgent`       | A kérést vagy `unknown` a programot küldő böngészőügynök vagy.                                                                        |
| `properties.method`          | HTTP-módszer:`GET/POST/PUT/PATCH/HEAD`.                                                                                |
| `properties.path`            | A kérés relatív elérési útja.                                                                                          |
| `properties.origin`          | URI jelzi, hogy honnan származik a lekérés vagy `unknown`.                                                                  |
| `properties.operationStatus` | `Success` a < 400-as HTTP-állapotkódhoz <br> `ClientError` az 500-as < HTTP-állapotkódhoz <br> `Error` HTTP-állapothoz > = 500 |
| `properties.tenantId`        | Szervezet azonosítója                                                                                                        |
| `properties.tenantName`      | A szervezet neve.                                                                                              |
| `properties.callerObjectId`  | Azure Active Directory A hívó objektumazonosítója.                                                                         |
| `properties.instanceId`      | Ügyfélelemzések`instanceId`                                                                                         |

### <a name="workflow-event-schema"></a>Munkafolyamat-eseményséma

A munkafolyamat több lépést tartalmaz. [Adatforrások](data-sources.md) betöltése, [adatok egyesítése](data-unification.md), [gazdagítása](enrichment-hub.md) és [exportálása](export-destinations.md). Mindezek a lépések egyénileg vagy a következő folyamatokkal vezényelhetők. 

#### <a name="operation-types"></a>Művelettípusok

| OperationType     | Csoportosítás                                     |
| ----------------- | ----------------------------------------- |
| Lenyelés         | [Adatforrások](data-sources.md)           |
| DataPreparation   | [Adatforrások](data-sources.md)           |
| Megfeleltetés               | [Adategyesítés](data-unification.md)   |
| Match             | [Adategyesítés](data-unification.md)   |
| Összefűzés             | [Adategyesítés](data-unification.md)   |
| ProfileStore      | [Ügyfélprofilok](customer-profiles.md) |
| Keresés            | [Ügyfélprofilok](customer-profiles.md) |
| Tevékenys.          | [Tevékenységek](activities.md)                  |
| AttributeMeasures | [Szegmensek és intézkedések](segments.md)      |
| EntityMeasures    | [Szegmensek és intézkedések](segments.md)      |
| Mértékek          | [Szegmensek és intézkedések](segments.md)      |
| Szegmentálás      | [Szegmensek és intézkedések](segments.md)      |
| Dúsítás        | [Dúsítás](enrichment-hub.md)                                          |
| Intelligencia      | [Előrejelzések](predictions-overview.md)                                          |
| AiBuilder         | [Előrejelzések](predictions-overview.md)                                          |
| Elemzések          | [Előrejelzések](predictions-overview.md)                                          |
| Export            | [Exportálások](export-destinations.md)                                          |
| ModelManagement   | [Előrejelzések](custom-models.md)                                           |
| Kapcsolat      | [Adategyesítés](relationships.md)                                           |

#### <a name="field-description"></a>Mező leírása

| Mező           | Adattípus  | Kötelező/nem kötelező | Description                                                                                                                                                   | Példa                                                                                                                                                                  |
| --------------- | --------- | ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `time`          | Időbélyegző | Szükséges          | Az esemény időbélyegzője (UTC).                                                                                                                                 | `2020-09-08T09:48:14.8050869Z`                                                                                                                                           |
| `resourceId`    | Sztring    | Szükséges          | Az eseményt kibocsátó példány ResourceId azonosítója.                                                                                                            | `/SUBSCRIPTIONS/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXX/RESOURCEGROUPS/<RESOURCEGROUPNAME>/`<br>`PROVIDERS/MICROSOFT.D365CUSTOMERINSIGHTS/`<br>`INSTANCES/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXX` |
| `operationName` | Sztring    | Szükséges          | Az esemény által képviselt művelet neve. `{OperationType}.[WorkFlow|Task][Started|Completed]`. Hivatkozásért lásd: [Művelettípusok](#operation-types). | `Segmentation.WorkflowStarted`,<br> `Segmentation.TaskStarted`, <br> `Segmentation.TaskCompleted`, <br> `Segmentation.WorkflowCompleted`                                 |
| `category`      | Sztring    | Szükséges          | Az esemény naplókategóriája. Mindig `Operational` munkafolyamat-eseményekhez                                                                                           | `Operational`                                                                                                                                                            | 
| `resultType`    | Sztring    | Szükséges          | Az esemény állapota. `Running`, `Skipped`, `Successful`, `Failure`                                                                                            |                                                                                                                                                                          |
| `durationMs`    | Long      | Lehetséges          | A művelet időtartama ezredmásodpercben.                                                                                                                    | `133`                                                                                                                                                                    |
| `properties`    | Sztring    | Lehetséges          | JSON-objektum, amely több tulajdonsággal rendelkezik az adott eseménykategóriához.                                                                                        | Lásd: Munkafolyamat tulajdonságai [alfejezet](#workflow-properties-schema)                                                                                                       |
| `level`         | Sztring    | Szükséges          | Az esemény súlyossági szintje.                                                                                                                                  | `Informational`, `Warning` vagy `Error`                                                                                                                                   |
|                 |

#### <a name="workflow-properties-schema"></a>Munkafolyamat-tulajdonságok séma

A munkafolyamat-események a következő tulajdonságokkal rendelkeznek.

| Mező              | Workflow | Feladatok | Description            |
| ------------------------------- | -------- | ---- | ----------- |
| `properties.eventType`                       | Igen      | Igen  | Mindig `WorkflowEvent`, az eseményt munkafolyamat-eseményként jelölve meg.                                                                                                                                                                                                |
| `properties.workflowJobId`                   | Igen      | Igen  | A munkafolyamat-futtatás azonosítója. A munkafolyamat-végrehajtáson belül minden munkafolyamat- és feladatesemény azonos `workflowJobId`.                                                                                                                                   |
| `properties.operationType`                   | Igen      | Igen  | A művelet azonosítója, lásd: [Művelettípusok](#operation-types).                                                                                                                                                                               |
| `properties.tasksCount`                      | Igen      | No   | Csak munkafolyamat. A munkafolyamat által kiváltott feladatok száma.                                                                                                                                                                                                       |
| `properties.submittedBy`                     | Igen      | No   | Opcionális. Csak munkafolyamat-események. A Azure Active Directory [munkafolyamatot aktiváló felhasználó](/azure/marketplace/find-tenant-object-id#find-user-object-id) objectId azonosítója lásd még:`properties.workflowSubmissionKind`.                                   |
| `properties.workflowType`                    | Igen      | No   | `full` vagy `incremental` frissíteni.                                                                                                                                                                                                                            |
| `properties.workflowSubmissionKind`          | Igen      | No   | `OnDemand` vagy `Scheduled`.                                                                                                                                                                                                                                  |
| `properties.workflowStatus`                  | Igen      | No   | `Running` vagy `Successful`.                                                                                                                                                                                                                                 |
| `properties.startTimestamp`                  | Igen      | Igen  | UTC-időbélyegző`yyyy-MM-ddThh:mm:ss.SSSSSZ`                                                                                                                                                                                                                  |
| `properties.endTimestamp`                    | Igen      | Igen  | UTC-időbélyegző`yyyy-MM-ddThh:mm:ss.SSSSSZ`                                                                                                                                                                                                                  |
| `properties.submittedTimestamp`              | Igen      | Igen  | UTC-időbélyegző`yyyy-MM-ddThh:mm:ss.SSSSSZ`                                                                                                                                                                                                                  |
| `properties.instanceId`                      | Igen      | Igen  | Ügyfélelemzések`instanceId`                                                                                                                                                                                                                              |  
| `properties.identifier`                      | No       | Igen  | - OperationType = `Export` esetén az azonosító az exportálási konfiguráció GUID azonosítója. <br> - OperationType = `Enrichment` esetén ez a gazdagodás GUID azonosítója <br> - OperationType `Measures` és `Segmentation`, esetén az azonosító az entitás neve. |
| `properties.friendlyName`                    | No       | Igen  | Az exportálás vagy a feldolgozott entitás felhasználóbarát neve.                                                                                                                                                                                           |
| `properties.error`                           | No       | Igen  | Opcionális. Hibaüzenet további részletekkel.                                                                                                                                                                                                                  |
| `properties.additionalInfo.Kind`             | No       | Igen  | Opcionális. Csak OperationType esetén `Export`. Azonosítja az exportálás típusát. További információt az exportálási célhelyek [áttekintésében talál](export-destinations.md).                                                                                          |
| `properties.additionalInfo.AffectedEntities` | No       | Igen  | Opcionális. Csak OperationType esetén `Export`. Az exportálásban konfigurált entitások listáját tartalmazza.                                                                                                                                                            |
| `properties.additionalInfo.MessageCode`      | No       | Igen  | Opcionális. Csak OperationType esetén `Export`. Részletes üzenet az exportáláshoz.                                                                                                                                                                                 |
| `properties.additionalInfo.entityCount`      | No       | Igen  | Opcionális. Csak OperationType esetén `Segmentation`. A szegmens tagjainak teljes számát jelzi.                                                                                                                                                    |
