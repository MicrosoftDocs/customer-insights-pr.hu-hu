---
title: Naplózás Dynamics 365 Customer Insights az Azure Monitorral
description: További információ a naplók Figyelőnek való Microsoft Azure elküldéséhez.
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
ms.openlocfilehash: 2e0801c2b6af591e48a7df485a8523903c07617c
ms.sourcegitcommit: 73cb021760516729e696c9a90731304d92e0e1ef
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/25/2022
ms.locfileid: "8354411"
---
# <a name="log-forwarding-in-dynamics-365-customer-insights-with-azure-monitor-preview"></a>Bejelentkezés az Dynamics 365 Customer Insights Azure Monitorral (előzetes verzió)

Dynamics 365 Customer Insights közvetlen integrációt biztosít az Azure Monitorral. Az Azure Monitor erőforrásnaplói lehetővé teszik a naplók figyelése és elküldése az [Azure Storageba](https://azure.microsoft.com/services/storage/), [az Azure Log Analytics-be](/azure/azure-monitor/logs/log-analytics-overview), vagy streamelheti őket az [Azure Event Hubs](https://azure.microsoft.com/services/event-hubs/).

A Customer Insights a következő eseménynaplókat küldi:

- **Események naplózása**
  - **APIEvent** - lehetővé teszi a változáskövetést a Dynamics 365 Customer Insights felhasználói felületen keresztül.
- **Működési események**
  - **WorkflowEvent** – A munkafolyamat lehetővé teszi az adatforrások [beállítását](data-sources.md), az adatok egyesítését [és](data-unification.md) gazdagítását [,](enrichment-hub.md) valamint végül [más rendszerekbe történő exportálását](export-destinations.md). Mindezeket a lépéseket egyedileg (pl. egyszeri exportálás kiváltása) vagy vezényelhetővé lehet tenni (pl. az adatforrásokból származó adatfrissítés, amely elindítja az egyesítési folyamatot, amely további gazdagodásokat von maga után, és miután befejezte az adatok exportálását egy másik rendszerbe). További részletek: [WorkflowEvent Schema](#workflow-event-schema).
  - **APIEvent** - az összes API-hívás az ügyfélpéldányhoz a Dynamics 365 Customer Insights. További részletek: [APIEvent Schema](#api-event-schema).

## <a name="set-up-the-diagnostic-settings"></a>A diagnosztikai beállítások beállítása

### <a name="prerequisites"></a>Előfeltételek

A diagnosztika Customer Insights szolgáltatásban való konfigurálásához a következő előfeltételeknek kell teljesülniük:

- Aktív [Azure-előfizetéssel](https://azure.microsoft.com/pricing/purchase-options/pay-as-you-go/) rendelkezik.
- Rendszergazdai [engedélyekkel rendelkezik](permissions.md#administrator) a Customer Insightsban.
- Az Azure célerőforrásában közreműködő **és** **Felhasználóhozzáférés-rendszergazda** szerepkört kap. Az erőforrás lehet Azure Storage-fiók, Azure Event Hub vagy Azure Log Analytics-munkaterület. További információ: [Azure-szerepkör-hozzárendelések hozzáadása vagy eltávolítása az Azure Portal](/azure/role-based-access-control/role-assignments-portal) használatával.
- [Az Azure Storage, az Azure Event Hub vagy az Azure Log Analytics célkövetelményei](/azure/azure-monitor/platform/diagnostic-settings#destination-requirements) teljesültek.
- Legalább olvasó **szerepköre** van azon az erőforráscsoporton, amelyhez az erőforrás tartozik.

### <a name="set-up-diagnostics-with-azure-monitor"></a>Diagnosztika beállítása az Azure Monitor segítségével

1. A Customer Insights programban válassza a **SystemDiagnostics** > **lehetőséget** a példány által konfigurált diagnosztikai célok megtekintéséhez.

1. Válassza a Cél hozzáadása **lehetőséget**.

   > [!div class="mx-imgBorder"]
   > ![Diagnosztikai kapcsolat](media/diagnostics-pane.png "Diagnosztikai kapcsolat")

1. Adjon meg egy nevet a **diagnosztikai cél** neve mezőben.

1. Válassza ki az **Azure-előfizetés bérlőjét** a célerőforrással, és válassza a **bejelentkezést**.

1. Válassza ki az **Erőforrástípust** (Tárfiók, Eseményközpont vagy naplóelemzés).

1. Válassza ki a **célerőforrás előfizetését**.

1. Válassza ki a **célerőforrás Erőforrás csoportját**.

1. Válassza ki az **erőforrást**.

1. Erősítse meg az **adatvédelmi és megfelelőségi** nyilatkozatot.

1. A célerőforráshoz való csatlakozáshoz válassza **a Csatlakozás a rendszerhez** lehetőséget. A naplók 15 perc elteltével jelennek meg a célhelyen, ha az API használatban van, és eseményeket hoz létre.

### <a name="remove-a-destination"></a>Cél eltávolítása

1. Lépjen a SystemDiagnostics-hez **·** > **·**.

1. Válassza ki a diagnosztikai célhelyet a listában.

1. **A Műveletek** oszlopban jelölje ki a **Törlés** ikont.

1. A naplótovábbítás leállításához erősítse meg a törlést. Az Azure-előfizetés erőforrása nem törlődik. A Műveletek **oszlopban kiválaszthatja a hivatkozást a** kijelölt erőforrás Azure Portal megnyitásához és törléséhez.

## <a name="log-categories-and-event-schemas"></a>Kategóriák és eseménysémák naplózása

Jelenleg [az API-események](apis.md) és munkafolyamat-események támogatottak, és a következő kategóriák és sémák érvényesek.
A naplóséma az [Azure Monitor közös sémáját követi](/azure/azure-monitor/platform/resource-logs-schema#top-level-common-schema).

### <a name="categories"></a>Kategóriák

A Customer Insights két kategóriát tartalmaz:

- **Naplózási események**: [API-események](#api-event-schema) a szolgáltatás konfigurációs változásainak nyomon követéséhez. `POST|PUT|DELETE|PATCH` A műveletek ebbe a kategóriába tartoznak.
- **Működési események**: [A szolgáltatás használata közben létrehozott API-események](#api-event-schema) vagy [munkafolyamat-események](#workflow-event-schema).  Például `GET` kérések vagy munkafolyamat végrehajtási eseményei.

## <a name="configuration-on-the-destination-resource"></a>Konfiguráció a célerőforráson

Az erőforrástípusra vonatkozó választás alapján a következő lépések lépnek fel automatikusan:

### <a name="storage-account"></a>Storage account

A Customer Insights szolgáltatás főkötelezettje megkapja a **Tárfiók közreműködő** engedélyt a kijelölt erőforrásra, és két tárolót hoz létre a kijelölt névtér alatt:

- `insight-logs-audit`**ellenőrzési események**
- `insight-logs-operational`**működési események**

### <a name="event-hub"></a>Esemény központja

A Customer Insights szolgáltatásnév megkapja az **Azure Event Hubs-adattulajdonos** engedélyét az erőforráshoz, és két Event Hubs hoz létre a kijelölt névtér alatt:

- `insight-logs-audit`**ellenőrzési események**
- `insight-logs-operational`**működési események**

### <a name="log-analytics"></a>Log Analytics

A Customer Insights szolgáltatás főkiszolgálója megkapja a **Log Analytics közreműködő** engedélyét az erőforráshoz. A naplók a **LogsTablesLog** > **Management** > **alatt** lesznek elérhetők a kijelölt Log Analytics-munkaterületen. Bontsa ki a **Naplókezelés** megoldást, és keresse meg a `CIEventsAudit` és `CIEventsOperational` táblákat.

- `CIEventsAudit`**ellenőrzési események**
- `CIEventsOperational`**működési események**

**A Lekérdezések ablakban bontsa** ki a **Naplózási** megoldást, és keresse meg a kereséssel `CIEvents` biztosított példalekérdezéseket.

## <a name="event-schemas"></a>Eseménysémák

Az API-események és munkafolyamat-események közös struktúrával és részletekkel rendelkeznek, ahol különböznek egymástól, lásd [az API-eseménysémát](#api-event-schema) vagy [a munkafolyamat-eseménysémát](#workflow-event-schema).

### <a name="api-event-schema"></a>API-eseménysémák

| Mező             | Adattípus  | Kötelező/nem kötelező | Description       | Példa        |
| ----------------- | --------- | ----------------- | --------------------- | ------------------------ |
| `time`            | Időbélyegző | Szükséges          | Az esemény időbélyege (UTC)       | `2020-09-08T09:48:14.8050869Z`         |
| `resourceId`      | Sztring    | Szükséges          | Az eseményt kibocsátó példány ResourceId-ja         | `/SUBSCRIPTIONS/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXX/RESOURCEGROUPS/<RESOURCEGROUPNAME>/`<br>`PROVIDERS/MICROSOFT.D365CUSTOMERINSIGHTS/`<br>`INSTANCES/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXX`  |
| `operationName`   | Sztring    | Szükséges          | Az esemény által képviselt művelet neve.                                                                                                                | `Workflows.GetWorkFlowStatusAsync`                                                                                                                                       |
| `category`        | Sztring    | Szükséges          | Az esemény naplózási kategóriája. Vagy `Operational`, vagy `Audit`. Minden POST/PUT/PATCH/DELETE HTTP kérés a következővel van ellátva `Audit`: `Operational` | `2020-09-08T09:48:14.8050869Z`                                                                                                                                           |
| `resultType`      | Sztring    | Szükséges          | Az esemény állapota. `Success`, `ClientError`, `Failure`                                                                                                        |                                                                                                                                                                          |
| `resultSignature` | Sztring    | Lehetséges          | Az esemény eredményállapota. Ha a művelet egy REST API hívásnak felel meg, akkor az a HTTP állapotkódja.        | `200`             |
| `durationMs`      | Long      | Lehetséges          | A művelet időtartama ezredmásodpercben.     | `133`     |
| `callerIpAddress` | Sztring    | Lehetséges          | Hívó IP-címe, ha a művelet egy nyilvánosan elérhető IP-címről származó API-hívásnak felel meg.                                                 | `144.318.99.233`         |
| `identity`        | Sztring    | Lehetséges          | A műveletet 1000000.000.000.000.000.000.000.000.000.       | Lásd: [Identitás](#identity-schema) szakasz.     |  |
| `properties`      | Sztring    | Lehetséges          | Az adott eseménykategóriához több tulajdonsággal rendelkező JSON-objektum.      | Lásd: [Tulajdonságok](#api-properties-schema) szakasz.    |
| `level`           | Sztring    | Szükséges          | Az esemény súlyossági szintje.    | `Informational`, `Warning`, `Error` vagy `Critical`.           |
| `uri`             | Sztring    | Lehetséges          | Abszolút kérés URI.    |               |

#### <a name="identity-schema"></a>Identitássémát

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
| `Authorization.UserRole`      | Hozzárendelt szerepkör a felhasználóhoz vagy alkalmazáshoz. További információt a felhasználói engedélyek [című témakörben talál](permissions.md).                                     |
| `Authorization.RequiredRoles` | A művelethez szükséges szerepkörök. `Admin` A szerepkör minden műveletet elvégezhet.                                                    |
| `Claims`                      | A felhasználó vagy alkalmazás JSON webes jogkivonatának (JWT) állításai. A jogcímtulajdonságok szervezetenként és Azure Active Directory konfigurációnként eltérőek. |

#### <a name="api-properties-schema"></a>API-tulajdonságok sémája

[Az API-események](apis.md) következő tulajdonságokkal rendelkeznek.

| Mező                        | Description                                                                                                            |
| ---------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| `properties.eventType`       | Always `ApiEvent`, a naplóesemény API-eseményként való megjelölése.                                                                 |
| `properties.userAgent`       | A kérést küldő böngészőügynök vagy `unknown`.                                                                        |
| `properties.method`          | HTTP-módszer:`GET/POST/PUT/PATCH/HEAD`.                                                                                |
| `properties.path`            | A kérelem relatív elérési útja.                                                                                          |
| `properties.origin`          | URI annak jelzése, hogy honnan származik a fetch vagy `unknown` a.                                                                  |
| `properties.operationStatus` | `Success` a 400-as < HTTP-állapotkódhoz <br> `ClientError` 500-as < HTTP-állapotkód esetén <br> `Error` HTTP állapot >= 500 esetén |
| `properties.tenantId`        | Szervezet azonosítója                                                                                                        |
| `properties.tenantName`      | A szervezet neve.                                                                                              |
| `properties.callerObjectId`  | Azure Active Directory A hívó objectId azonosítója.                                                                         |
| `properties.instanceId`      | Ügyfélelemzések`instanceId`                                                                                         |

### <a name="workflow-event-schema"></a>Munkafolyamat-eseménysémák

A munkafolyamat több lépést tartalmaz. [Adatforrások beolvasása,](data-sources.md) adatok egyesítése, [gazdagítása](data-unification.md)[és](enrichment-hub.md) exportálása [.](export-destinations.md) Mindezek a lépések egyénileg vagy a következő folyamatokkal vezényelhetők. 

#### <a name="operation-types"></a>Művelettípusok

| OperationType     | Csoportosítás                                     |
| ----------------- | ----------------------------------------- |
| Lenyelés         | [Adatforrások](data-sources.md)           |
| DataPreparation   | [Adatforrások](data-sources.md)           |
| Megfeleltetés               | [Adategyesítés](data-unification.md)   |
| Match             | [Adategyesítés](data-unification.md)   |
| Összefűzés             | [Adategyesítés](data-unification.md)   |
| Profiltár      | [Ügyfélprofilok](customer-profiles.md) |
| Keresés            | [Ügyfélprofilok](customer-profiles.md) |
| Tevékenys.          | [Tevékenységek](activities.md)                  |
| Attribútumintézkedések | [Szegmensek és intézkedések](segments.md)      |
| Entitásintézkedések    | [Szegmensek és intézkedések](segments.md)      |
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
| `time`          | Időbélyegző | Szükséges          | Az esemény időbélyege (UTC).                                                                                                                                 | `2020-09-08T09:48:14.8050869Z`                                                                                                                                           |
| `resourceId`    | Sztring    | Szükséges          | Az eseményt kibocsátó példány ResourceId-ja.                                                                                                            | `/SUBSCRIPTIONS/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXX/RESOURCEGROUPS/<RESOURCEGROUPNAME>/`<br>`PROVIDERS/MICROSOFT.D365CUSTOMERINSIGHTS/`<br>`INSTANCES/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXX` |
| `operationName` | Sztring    | Szükséges          | Az esemény által képviselt művelet neve. `{OperationType}.[WorkFlow|Task][Started|Completed]`. A művelettípusok [hivatkozást lásd](#operation-types). | `Segmentation.WorkflowStarted`,<br> `Segmentation.TaskStarted`, <br> `Segmentation.TaskCompleted`, <br> `Segmentation.WorkflowCompleted`                                 |
| `category`      | Sztring    | Szükséges          | Az esemény naplózási kategóriája. Mindig `Operational` munkafolyamat-eseményekhez                                                                                           | `Operational`                                                                                                                                                            | 
| `resultType`    | Sztring    | Szükséges          | Az esemény állapota. `Running`, `Skipped`, `Successful`, `Failure`                                                                                            |                                                                                                                                                                          |
| `durationMs`    | Long      | Lehetséges          | A művelet időtartama ezredmásodpercben.                                                                                                                    | `133`                                                                                                                                                                    |
| `properties`    | Sztring    | Lehetséges          | Az adott eseménykategóriához több tulajdonsággal rendelkező JSON-objektum.                                                                                        | Lásd a Munkafolyamat tulajdonságai [alszakaszt](#workflow-properties-schema)                                                                                                       |
| `level`         | Sztring    | Szükséges          | Az esemény súlyossági szintje.                                                                                                                                  | `Informational`, `Warning` vagy `Error`                                                                                                                                   |
|                 |

#### <a name="workflow-properties-schema"></a>Munkafolyamat tulajdonságainak sémája

A munkafolyamat-események következő tulajdonságokkal rendelkeznek.

| Mező              | Workflow | Feladatok | Description            |
| ------------------------------- | -------- | ---- | ----------- |
| `properties.eventType`                       | Igen      | Igen  | Mindig `WorkflowEvent`, az esemény megjelölése munkafolyamat-eseményként.                                                                                                                                                                                                |
| `properties.workflowJobId`                   | Igen      | Igen  | A munkafolyamat-futtatás azonosítója A munkafolyamat-végrehajtáson belüli összes munkafolyamat- és feladatesemény azonos `workflowJobId`.                                                                                                                                   |
| `properties.operationType`                   | Igen      | Igen  | A művelet azonosítója: [Művelettípusok]. (#operation típusú)                                                                                                                                                                                       |
| `properties.tasksCount`                      | Igen      | No   | Csak munkafolyamat. A munkafolyamat által indított feladatok száma.                                                                                                                                                                                                       |
| `properties.submittedBy`                     | Igen      | No   | Opcionális. Csak munkafolyamat-események. A Azure Active Directory [munkafolyamatot aktiváló felhasználó](/azure/marketplace/find-tenant-object-id#find-user-object-id) objectId azonosítóját lásd még `properties.workflowSubmissionKind`.                                   |
| `properties.workflowType`                    | Igen      | No   | `full` vagy `incremental` frissítsen.                                                                                                                                                                                                                            |
| `properties.workflowSubmissionKind`          | Igen      | No   | `OnDemand` vagy `Scheduled`.                                                                                                                                                                                                                                  |
| `properties.workflowStatus`                  | Igen      | No   | `Running` vagy `Successful`.                                                                                                                                                                                                                                 |
| `properties.startTimestamp`                  | Igen      | Igen  | UTC-időbélyegző`yyyy-MM-ddThh:mm:ss.SSSSSZ`                                                                                                                                                                                                                  |
| `properties.endTimestamp`                    | Igen      | Igen  | UTC-időbélyegző`yyyy-MM-ddThh:mm:ss.SSSSSZ`                                                                                                                                                                                                                  |
| `properties.submittedTimestamp`              | Igen      | Igen  | UTC-időbélyegző`yyyy-MM-ddThh:mm:ss.SSSSSZ`                                                                                                                                                                                                                  |
| `properties.instanceId`                      | Igen      | Igen  | Ügyfélelemzések`instanceId`                                                                                                                                                                                                                              |  |
| `properties.identifier`                      | No       | Igen  | - OperationType = `Export` esetén az azonosító az exportálási konfiguráció GUID azonosítója. <br> - OperationType = `Enrichment` esetén ez a gazdagodás GUID azonosítója <br> - OperationType `Measures` és esetén `Segmentation` az azonosító az entitás neve. |
| `properties.friendlyName`                    | No       | Igen  | Az exportálás vagy a feldolgozott entitás felhasználóbarát neve.                                                                                                                                                                                           |
| `properties.error`                           | No       | Igen  | Opcionális. Hibaüzenet további részletekkel.                                                                                                                                                                                                                  |
| `properties.additionalInfo.Kind`             | No       | Igen  | Opcionális. Csak OperationType esetén `Export`. Azonosítja az exportálás típusát. További információt az exportcélok [áttekintése című témakörben talál](export-destinations.md).                                                                                          |
| `properties.additionalInfo.AffectedEntities` | No       | Igen  | Opcionális. Csak OperationType esetén `Export`. Az exportálásban konfigurált entitások listáját tartalmazza.                                                                                                                                                            |
| `properties.additionalInfo.MessageCode`      | No       | Igen  | Opcionális. Csak OperationType esetén `Export`. Részletes üzenet az exportáláshoz.                                                                                                                                                                                 |
| `properties.additionalInfo.entityCount`      | No       | Igen  | Opcionális. Csak OperationType esetén `Segmentation`. A szegmens tagjainak teljes számát jelzi.                                                                                                                                                    |
