---
title: Naplózás Dynamics 365 Customer Insights az Azure Monitorral
description: További információ arról, hogyan küldhet naplókat a Microsoft Azure Figyelőnek.
ms.date: 12/14/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: article
author: brndkfr
ms.author: bkief
manager: shellyha
ms.openlocfilehash: d962c359d70a068fcf939b61e340f86de088b419
ms.sourcegitcommit: 0c3c473e0220de9ee3c1f1ee1825de0b3b3663c3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/14/2021
ms.locfileid: "7920868"
---
# <a name="log-forwarding-in-dynamics-365-customer-insights-with-azure-monitor-preview"></a>Bejelentkezés az Dynamics 365 Customer Insights Azure Monitorral (előzetes verzió)

Dynamics 365 Customer Insights közvetlen integrációt biztosít az Azure Monitorral. Azure Monitor erőforrás-naplók lehetővé teszik a naplók figyelését és küldését [az Azure](https://azure.microsoft.com/services/storage/) Storage, azure Log Analytics, [vagy](/azure/azure-monitor/logs/log-analytics-overview) streamelhetik őket [az Azure Event Hubs](https://azure.microsoft.com/services/event-hubs/).

A Customer Insights a következő eseménynaplókat küldi el:

- **Audit események**
  - **APIEvent** - lehetővé teszi a változáskövetést a felhasználói Dynamics 365 Customer Insights felületen keresztül.
- **Operatív események**
  - **WorkflowEvent** - A munkafolyamat lehetővé teszi az adatforrások beállítását, [...](data-sources.md)[egyesítése és](data-unification.md)[gazdagítása](enrichment-hub.md), valamint végül az adatok [exportálása](export-destinations.md) más rendszerekbe. Mindezeket a lépéseket egyénileg (pl. egyetlen exportálás aktiválása) vagy hangszereléssel lehet végrehajtani (pl. adatforrásokból származó adatfrissítés, amely kiváltja az egyesítési folyamatot, amely további gazdagodásokat von be, és miután megtörtént, exportálja az adatokat egy másik rendszerbe). További részletekért lásd a [WorkflowEvent sémát](#workflow-event-schema).
  - **APIEvent** – az összes API-hívás az ügyfélpéldányhoz a Dynamics 365 Customer Insights. További részletekért lásd az [APIEvent-sémát](#api-event-schema).

## <a name="set-up-the-diagnostic-settings"></a>A diagnosztikai beállítások beállítása

### <a name="prerequisites"></a>Előfeltételek

A diagnosztika Ügyfélelemzésben való konfigurálásához a következő előfeltételeknek kell teljesülniük:

- Aktív [Azure-előfizetéssel](https://azure.microsoft.com/pricing/purchase-options/pay-as-you-go/) rendelkezik.
- [Rendszergazdai](permissions.md#administrator) engedélyekkel rendelkezik a Customer Insightsban.
- Az **·** **Azure-beli célerőforráson a közreműködő és a Felhasználói hozzáférés rendszergazda** szerepkörrel rendelkezik. Az erőforrás lehet Egy Azure Storage-fiók, egy Azure Event Hub vagy egy Azure Log Analytics-munkaterület. További információ: [Azure-szerepkör-hozzárendelések hozzáadása vagy eltávolítása a Azure Portal használatával](/azure/role-based-access-control/role-assignments-portal).
- [Az](/azure/azure-monitor/platform/diagnostic-settings#destination-requirements) Azure Storage, az Azure Event Hub vagy az Azure Log Analytics célkövetelményei teljesülnek.
- Legalább a olvasó szerepköre van **abban az** erőforráscsoportban, amelyhez az erőforrás tartozik.

### <a name="set-up-diagnostics-with-azure-monitor"></a>Diagnosztika beállítása az Azure Monitorral

1. A Customer Insightsban **válassza** > **a Rendszerdiagnosztika lehetőséget** az ebben a példányban konfigurált diagnosztikai célhelyek megtekintéséhez.

1. Válassza a **Cél hozzáadása** lehetőséget.

   > [!div class="mx-imgBorder"]
   > ![Diagnosztikai kapcsolat](media/diagnostics-pane.png "Diagnosztikai kapcsolat")

1. Adjon meg egy nevet a **Diagnosztika cél** mezőjében.

1. Válassza ki **az** Azure-előfizetés bérlőjét a célerőforrással, és válassza **a bejelentkezés** lehetőséget.

1. Válassza ki az **Erőforrás típusát** (Storage-fiók, Event Hub vagy log analytics).

1. Válassza ki **a** célerőforrás előfizetését.

1. Válassza ki a **célerőforrás** Erőforrás csoportját.

1. Válassza ki az **Erőforrás** elemet.

1. Erősítse meg az **adatvédelmi és megfelelőségi** nyilatkozatot.

1. Válassza a Csatlakozás a rendszerhez lehetőséget **a** célerőforráshoz való csatlakozáshoz. A naplók 15 perc elteltével kezdenek megjelenni a célhelyen, ha az API használatban van, és eseményeket generál.

### <a name="remove-a-destination"></a>Cél eltávolítása

1. Lépjen **a** > **Rendszerdiagnosztika** elemre.

1. Válassza ki a diagnosztikai célt a listában.

1. A **Műveletek** oszlopban jelölje ki a **Törlés** ikont.

1. Erősítse meg a törlést a naplótovábbítás leállításához. Az Azure-előfizetés erőforrása nem törlődik. A Műveletek oszlopban kiválaszthatja a hivatkozást **a kijelölt erőforrás Azure Portal** megnyitásához és ott való törléséhez.

## <a name="log-categories-and-event-schemas"></a>Kategóriák és eseményséma naplózása

Jelenleg [az API-események](apis.md) és munkafolyamat-események támogatottak, és a következő kategóriák és sémák érvényesek.
A naplóséma az [Azure Monitor közös sémáját követi](/azure/azure-monitor/platform/resource-logs-schema#top-level-common-schema).

### <a name="categories"></a>Kategóriák

A Customer Insights két kategóriát biztosít:

- **Naplózási események** : [API-események](#api-event-schema) a szolgáltatás konfigurációs változásainak nyomon követéséhez. `POST|PUT|DELETE|PATCH` műveletek ebbe a kategóriába tartoznak.
- **Működési események** : A szolgáltatás használata közben létrehozott [API](#api-event-schema)-események vagy [munkafolyamat-események.](#workflow-event-schema)  Például `GET` kérések vagy munkafolyamat végrehajtási eseményei.

## <a name="configuration-on-the-destination-resource"></a>Konfiguráció a célerőforráson

Az erőforrástípuson való választás alapján a következő lépések automatikusan érvényesek:

### <a name="storage-account"></a>Storage account

A Customer Insights szolgáltatásnév megkapja a **Storage-fiók közreműködő** engedélyt a kiválasztott erőforráson, és két tárolót hoz létre a kiválasztott névtér alatt:

- `insight-logs-audit`**ellenőrzési eseményeket tartalmaz**
- `insight-logs-operational`**operatív eseményeket tartalmaz**

### <a name="event-hub"></a>Esemény központja

A Customer Insights-szolgáltatásnév megkapja az **Azure Event Hubs Data Owner engedélyt az** erőforráson, és két Event Hubs hoz létre a kiválasztott névtér alatt:

- `insight-logs-audit`**ellenőrzési eseményeket tartalmaz**
- `insight-logs-operational`**operatív eseményeket tartalmaz**

### <a name="log-analytics"></a>Log Analytics

A Customer Insights-szolgáltatás főkötelezettje megkapja a **Log Analytics közreműködő engedélyt az** erőforrásra. A naplók **a** > **naplótáblák naplókezelése alatt lesznek elérhetők** > **a kiválasztott Log Analytics** munkaterületen. Bontsa ki a **Naplókezelési** megoldást, és keresse meg a `CIEventsAudit``CIEventsOperational` táblákat.

- `CIEventsAudit`**ellenőrzési eseményeket tartalmaz**
- `CIEventsOperational`**operatív eseményeket tartalmaz**

A **Lekérdezések** ablakban bontsa ki a **Naplózási** megoldást, és keresse meg a keresés által biztosított példalekérdezéseket. `CIEvents`

## <a name="event-schemas"></a>Eseményséma

Az API-események és munkafolyamat-események közös struktúrával és részletekkel rendelkeznek, ahol különböznek egymástól, [lásd: API-eseményséma](#api-event-schema) vagy [munkafolyamat-eseményséma](#workflow-event-schema).

### <a name="api-event-schema"></a>API-eseményséma

| Mező             | Adattípus  | Kötelező/nem kötelező | Description       | Példa        |
| ----------------- | --------- | ----------------- | --------------------- | ------------------------ |
| `time`            | Időbélyegző | Szükséges          | Az esemény időbélyege (UTC)       | `2020-09-08T09:48:14.8050869Z`         |
| `resourceId`      | Sztring    | Szükséges          | Az eseményt kibocsátó példány ResourceIdja         | `/SUBSCRIPTIONS/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXX/RESOURCEGROUPS/<RESOURCEGROUPNAME>/`<br>`PROVIDERS/MICROSOFT.D365CUSTOMERINSIGHTS/`<br>`INSTANCES/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXX`  |
| `operationName`   | Sztring    | Szükséges          | Az esemény által képviselt művelet neve.                                                                                                                | `Workflows.GetWorkFlowStatusAsync`                                                                                                                                       |
| `category`        | Sztring    | Szükséges          | Az esemény naplókategóriája. Vagy `Operational`, vagy `Audit`. Minden POST/PUT/PATCH/DELETE HTTP-kérés a következővel van `Audit` ellátva:, minden más`Operational` | `2020-09-08T09:48:14.8050869Z`                                                                                                                                           |
| `resultType`      | Sztring    | Szükséges          | Az esemény állapota. `Success`, `ClientError`, `Failure`                                                                                                        |                                                                                                                                                                          |
| `resultSignature` | Sztring    | Lehetséges          | Az esemény eredményállapota. Ha a művelet REST API hívásnak felel meg, akkor ez a HTTP állapotkódja.        | `200`             |
| `durationMs`      | Long      | Lehetséges          | A művelet időtartama ezredmásodpercben.     | `133`     |
| `callerIpAddress` | Sztring    | Lehetséges          | Hívó IP-címe, ha a művelet egy nyilvánosan elérhető IP-címről érkező API-hívásnak felel meg.                                                 | `144.318.99.233`         |
| `identity`        | Sztring    | Lehetséges          | A műveletet 84444-es JSON-objektum a műveletet elkeseredő felhasználó vagy alkalmazás identitását írja le.       | Lásd: [Identitás](#identity-schema) szakasz.     |  |
| `properties`      | Sztring    | Lehetséges          | Az adott eseménykategóriához több tulajdonsággal rendelkező JSON-objektum.      | Lásd: [Tulajdonságok](#api-properties-schema) szakasz.    |
| `level`           | Sztring    | Szükséges          | Az esemény súlyossági szintje.    | `Informational`, `Warning``Error`,, vagy `Critical`.           |
| `uri`             | Sztring    | Lehetséges          | Abszolút kérés URI.    |               |

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
| `Authorization.UserRole`      | A felhasználóhoz vagy az alkalmazáshoz hozzárendelt szerepkör. További információ: [Felhasználói engedélyek](permissions.md).                                     |
| `Authorization.RequiredRoles` | A művelet végrehajtásához szükséges szerepkörök. `Admin` A szerepkör minden műveletet elvégezhet.                                                    |
| `Claims`                      | A felhasználó vagy alkalmazás JSON webes jogkivonatának (JWT) jogcímei. A jogcímtulajdonságok szervezetenként és Azure Active Directory konfigurációnként eltérőek. |

#### <a name="api-properties-schema"></a>API-tulajdonságok sémája

[Az API-események](apis.md) a következő tulajdonságokkal rendelkeznek.

| Mező                        | Description                                                                                                            |
| ---------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| `properties.eventType`       | Mindig `ApiEvent`, a naplóeseményt API-eseményként jelöli meg.                                                                 |
| `properties.userAgent`       | Böngészőügynök, aki elküldi a kérelmet vagy `unknown`.                                                                        |
| `properties.method`          | HTTP módszer:`GET/POST/PUT/PATCH/HEAD`.                                                                                |
| `properties.path`            | A kérelem relatív elérési útja.                                                                                          |
| `properties.origin`          | URI jelzi, hogy honnan származik a lekérés vagy `unknown`.                                                                  |
| `properties.operationStatus` | `Success` HTTP állapotkód < 400 <br> `ClientError` 500 < HTTP állapotkódhoz <br> `Error` HTTP állapot >= 500 |
| `properties.tenantId`        | Szervezet azonosítója                                                                                                        |
| `properties.tenantName`      | A szervezet neve.                                                                                              |
| `properties.callerObjectId`  | Azure Active Directory A hívó objektumazonosítója.                                                                         |
| `properties.instanceId`      | Ügyfélelemzések`instanceId`                                                                                         |

### <a name="workflow-event-schema"></a>Munkafolyamat-eseményséma

A munkafolyamat több lépést tartalmaz. [Az adatforrások betöltása](data-sources.md), [egyesítése](data-unification.md), [gazdagítása és](enrichment-hub.md)[exportálása](export-destinations.md). Mindezek a lépések egyénileg vagy a következő folyamatokkal hangszerelhetők. 

#### <a name="operation-types"></a>Művelettípusok

| OperationType     | Csoportosítás                                     |
| ----------------- | ----------------------------------------- |
| Lenyelés         | [Adatforrások](data-sources.md)           |
| DataPreparáció   | [Adatforrások](data-sources.md)           |
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
| Modellmanagement   | [Előrejelzések](custom-models.md)                                           |
| Kapcsolat      | [Adategyesítés](relationships.md)                                           |

#### <a name="field-description"></a>Mező leírása

| Mező           | Adattípus  | Kötelező/nem kötelező | Description                                                                                                                                                   | Példa                                                                                                                                                                  |
| --------------- | --------- | ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `time`          | Időbélyegző | Szükséges          | Az esemény időbélyege (UTC).                                                                                                                                 | `2020-09-08T09:48:14.8050869Z`                                                                                                                                           |
| `resourceId`    | Sztring    | Szükséges          | Az eseményt kibocsátó példány ResourceIdja.                                                                                                            | `/SUBSCRIPTIONS/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXX/RESOURCEGROUPS/<RESOURCEGROUPNAME>/`<br>`PROVIDERS/MICROSOFT.D365CUSTOMERINSIGHTS/`<br>`INSTANCES/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXX` |
| `operationName` | Sztring    | Szükséges          | Az esemény által képviselt művelet neve. `{OperationType}.[WorkFlow|Task][Started|Completed]`. [Lásd: Művelettípusok](#operation-types) hivatkozás. | `Segmentation.WorkflowStarted`,<br> `Segmentation.TaskStarted`, <br> `Segmentation.TaskCompleted`, <br> `Segmentation.WorkflowCompleted`                                 |
| `category`      | Sztring    | Szükséges          | Az esemény naplókategóriája. Mindig `Operational` munkafolyamat-eseményekhez                                                                                           | `Operational`                                                                                                                                                            | 
| `resultType`    | Sztring    | Szükséges          | Az esemény állapota. `Running`, `Skipped`, `Successful`, `Failure`                                                                                            |                                                                                                                                                                          |
| `durationMs`    | Long      | Lehetséges          | A művelet időtartama ezredmásodpercben.                                                                                                                    | `133`                                                                                                                                                                    |
| `properties`    | Sztring    | Lehetséges          | Az adott eseménykategóriához több tulajdonsággal rendelkező JSON-objektum.                                                                                        | Lásd: [Munkafolyamat tulajdonságai](#workflow-properties-schema)                                                                                                       |
| `level`         | Sztring    | Szükséges          | Az esemény súlyossági szintje.                                                                                                                                  | `Informational`, `Warning` vagy `Error`                                                                                                                                   |
|                 |

#### <a name="workflow-properties-schema"></a>Munkafolyamat-tulajdonságok sémája

A munkafolyamat-események következő tulajdonságokkal rendelkeznek.

| Mező              | Workflow | Feladatok | Description            |
| ------------------------------- | -------- | ---- | ----------- |
| `properties.eventType`                       | Igen      | Igen  | Mindig `WorkflowEvent`, az esemény munkafolyamat-eseményként való megjelölése.                                                                                                                                                                                                |
| `properties.workflowJobId`                   | Igen      | Igen  | A munkafolyamat-futtatás azonosítója. A munkafolyamat-végrehajtáson belüli összes munkafolyamat- és feladatesemény ugyanaz `workflowJobId`.                                                                                                                                   |
| `properties.operationType`                   | Igen      | Igen  | A művelet azonosítója, lásd: [Művelettípusok]. (#operation típusok)                                                                                                                                                                                       |
| `properties.tasksCount`                      | Igen      | No   | Csak munkafolyamat. A munkafolyamat által kiváltott feladatok száma.                                                                                                                                                                                                       |
| `properties.submittedBy`                     | Igen      | No   | Opcionális. Csak munkafolyamat-események. A Azure Active Directory [munkafolyamatot aktiváló felhasználó objectId](/azure/marketplace/find-tenant-object-id#find-user-object-id) című témakört lásd `properties.workflowSubmissionKind` még.                                   |
| `properties.workflowType`                    | Igen      | No   | `full` vagy `incremental` frissítse.                                                                                                                                                                                                                            |
| `properties.workflowSubmissionKind`          | Igen      | No   | `OnDemand` vagy `Scheduled`.                                                                                                                                                                                                                                  |
| `properties.workflowStatus`                  | Igen      | No   | `Running` vagy `Successful`.                                                                                                                                                                                                                                 |
| `properties.startTimestamp`                  | Igen      | Igen  | UTC-időbélyegző`yyyy-MM-ddThh:mm:ss.SSSSSZ`                                                                                                                                                                                                                  |
| `properties.endTimestamp`                    | Igen      | Igen  | UTC-időbélyegző`yyyy-MM-ddThh:mm:ss.SSSSSZ`                                                                                                                                                                                                                  |
| `properties.submittedTimestamp`              | Igen      | Igen  | UTC-időbélyegző`yyyy-MM-ddThh:mm:ss.SSSSSZ`                                                                                                                                                                                                                  |
| `properties.instanceId`                      | Igen      | Igen  | Ügyfélelemzések`instanceId`                                                                                                                                                                                                                              |  |
| `properties.identifier`                      | No       | Igen  | - OperationType = `Export` esetén az azonosító az exportálási konfiguráció guidja. <br> - OperationType = `Enrichment` esetében ez a dúsítás vezérelve <br> - OperationType `Measures` és, az azonosító az entitás `Segmentation` neve. |
| `properties.friendlyName`                    | No       | Igen  | Az exportálás vagy a feldolgozott entitás felhasználóbarát neve.                                                                                                                                                                                           |
| `properties.error`                           | No       | Igen  | Opcionális. Hibaüzenet további részletekkel.                                                                                                                                                                                                                  |
| `properties.additionalInfo.Kind`             | No       | Igen  | Opcionális. Csak OperationType `Export` esetén. Azonosítja az exportálás típusát. További információ: [Az exportálási célpontok áttekintése](export-destinations.md).                                                                                          |
| `properties.additionalInfo.AffectedEntities` | No       | Igen  | Opcionális. Csak OperationType `Export` esetén. Az exportálásban konfigurált entitások listáját tartalmazza.                                                                                                                                                            |
| `properties.additionalInfo.MessageCode`      | No       | Igen  | Opcionális. Csak OperationType `Export` esetén. Részletes üzenet az exportáláshoz.                                                                                                                                                                                 |
| `properties.additionalInfo.entityCount`      | No       | Igen  | Opcionális. Csak OperationType `Segmentation` esetén. A szegmens tagjainak teljes számát jelzi.                                                                                                                                                    |
