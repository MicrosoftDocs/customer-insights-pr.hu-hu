---
title: Hivatkozás létrehozása a célközönséggel kapcsolatos információk és az elkötelezettségi információk között
description: Aktív kapcsolatot hozhat létre a célközönséggel kapcsolatos információk és az elkötelezettségi információk között, hogy lehetővé tegye az adatok kétirányú megosztását.
ms.date: 09/08/2021
ms.service: customer-insights
ms.topic: conceptual
author: mkisel
ms.author: mkisel
ms.reviewer: mhart
manager: shellyha
ms.openlocfilehash: db38778c0da862e119f9b374e07c82ead0d3a4f2
ms.sourcegitcommit: 53b133a716c73cb71e8bcbedc6273cec70ceba6c
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/15/2021
ms.locfileid: "7645585"
---
# <a name="create-a-link-between-audience-insights-and-engagement-insights"></a>Hivatkozás létrehozása a célközönséggel kapcsolatos információk és az elkötelezettségi információk között

[!INCLUDE [cc-beta-prerelease-disclaimer](includes/cc-beta-prerelease-disclaimer.md)]

Az elkötelezettséggel kapcsolatos információk és az célközönséggel kapcsolatos információk közötti integráció mindkét szolgáltatásból összekapcsolja a környezeteket, és lehetővé teszi az adatok kétirányú megosztottságát közöttük.

Használhatja a célközönséggel kapcsolatos információk egyesített profiljait és szegmenseit, hogy több elemzési lehetősége legyen az elkötelezettségi információkban. Exportálja a nagy üzleti értéket képviselő eseményeket az elkötelezettségi információkból. Ezekkel az eseményekkel adatokat adhat hozzá a célközönséggel kapcsolatos információk profiljaihoz.

## <a name="prerequisites"></a>Előfeltételek

- Célközönséggel kapcsolatos információk profilokat egy saját Azure Data Lake Storage fiókban vagy egy [Microsoft Dataverse](/powerapps/maker/data-platform/data-platform-intro.md)&ndash;felügyelt adattóban kell tárolni. 
- Emellett a célközönséggel kapcsolatos információk környezetnek szükséges egy társított Dataverse-környezet. Ha pedig az a környezet is Dataverse-t használ adattárolásra van használatban, akkor jelölje be az **Adatok megosztásának engedélyezése** beállítást az célközönség információkban. További tudnivalókért lásd: [Környezet létrehozása és konfigurálása a célközönséggel kapcsolatos információkban](../audience-insights/create-environment.md).
- Rendszergazdai engedélyekre van szüksége az elkötelezettségi információkhoz és a célközönséggel kapcsolatos információk környezetekhez is.
- A csatolt környezetnek ugyanabban a földrajzi régióban kell lennie.

> [!NOTE]
> - Ha a célközönséggel kapcsolatos információk előfizetése egy próbaverzió, amely, a célközönséggel kapcsolatos információk belülről kezelt adattavát használja, vegye fel velünk a kapcsolatot az [pirequest@microsoft.com](mailto:pirequest@microsoft.com) e-mail-címen segítségért. 
> - Ha a célközönséggel kapcsolatos információk saját Azure Data Lake Storage tárhelyét használja az adatok tárolásához, akkor fel kell vennie egy elkötelezettséggel kapcsolatos információk szolgáltatásnevet a tárfiókjába. A részletekért látogasson el a [Kapcsolódás Azure Data Lake Storage-fiókhoz Azure szolgáltatásnévvel a célközönséggel kapcsolatos információkhoz](../audience-insights/connect-service-principal.md). 


## <a name="create-an-environment-link"></a>Környezethivatkozás létrehozása

A **Felügyelet** > **Környezet** beállításainak módosításával létrehozhat egy környezethivatkozást az elkötelezettségi információkban.

**Aktív hivatkozás létrehozásához a célközönséggel kapcsolatos információk és az elkötelezettségi információk között.**

1. A **Környezeti rendszergazda** lapon válassza a **Környezetek összekapcsolása** lapot.

    :::image type="content" source="media/integrate1.png" alt-text="Egy környezet beállítása.":::

1. Válassza a **Környezetek beállítása** lehetőséget a bal felső sarokban vagy a képernyő alján.

     :::image type="content" source="media/integrate2.png" alt-text="Válasszon egy célközönség-információk környezetet.":::

1. Válasszon egy célközönség információk környezetet, majd válassza a ***Tovább** lehetőséget a befejezéshez. Most már kiválaszthatja a kapcsolt környezetek opcionális szolgáltatásait.
 
## <a name="enable-audience-insights-unified-profiles-attributes-and-segments"></a>A Célközönséggel kapcsolatos információk egyesített profiljai attribútumainak és szegmenseinek engedélyezése

A környezetek összekapcsolása után kiválaszthatja a kapcsolt környezetek opcionális szolgáltatásait. Ezekkel a funkciókkal egységes profilattribútumokat és -szegmenseket érhet el célközönséggel kapcsolatos információkból az ügyféladatokon végzett interaktív elemzéshez.

> [!IMPORTANT]
> Ahhoz, hogy a célközönséggel kapcsolatos információk megjelenjenek az elkötelezettséggel kapcsolatos információkban először [futtatnia kell egyesítési és későbbi folyamatokat](../audience-insights/merge-entities.md). A későbbi folyamatok azért fontosak, mert egyedi táblázatot hoznak létre, amely célközönséggel kapcsolatos információs szegmenseket előkészíti a megosztásra az elkötelezettséggel kapcsolatos információkkal. (Ha rendszerfrissítés van ütemezve, a későbbi folyamatokat automatikusan tartalmazza.)

**A webes adatok elemzése az elkötelezettséggel kapcsolatos információkban**

1. A **Környezet rendszergazda** oldalon kapcsolja be az **Adatok megosztása a célközönséggel kapcsolatos információkból az elkötelezettséggel kapcsolatos információkkal** kapcsolót, majd válassza a **Tovább** lehetőséget.

    :::image type="content" source="media/integrate4.png" alt-text="Funkciók kiválasztása.":::

1. Válassza ki azokat az attribútumokat az egyesített profilokból, amelyek a elkötelezettséggel kapcsolatos információkban profilok lesznek. (Nem minden attribútum hasznos dimenzió. Nem valószínű például, hogy a webhely eseményeinek elemzéséhez **Utónév** vagy **Vezetéknév** attribútumokra szüksége lenne.)

    :::image type="content" source="media/integrate5.png" alt-text="Dimenziók összeválogatása.":::

   >[!NOTE]
   > A célközönséggel kapcsolatos információk minden attribútumát, amely azonosítókat (például **azonosítót** és **másodlagos azonosítót**) jelképez, kiszűri a rendelkezésre álló attribútumokból, és dimenziókká válnak az elkötelezettséggel kapcsolatos információkban.

1. Amikor végzett az attribútumok kiválasztásával, válassza a **Tovább** lehetőséget.
1. Olyan felhasználókat is hozzáadhat, akik megtekinthetik az célközönséggel kapcsolatos információk profildimenzióit és szegmenseket az elkötelezettséggel kapcsolatos információkban.

    :::image type="content" source="media/integrate6.png" alt-text="Az ügyféladatokhoz való hozzáférés kezelése.":::

   > [!IMPORTANT]
   > Ha ebben a lépésben nem ad hozzá konkrétan felhasználókat, akkor a rendszer elrejti az adatokat az elkötelezettségi információkban a felhasználók elől.
   > Ahhoz, hogy a célközönséggel kapcsolatos információk megjelenjenek az elkötelezettséggel kapcsolatos információkban először [futtatnia kell egyesítési és későbbi folyamatokat](../audience-insights/merge-entities.md). A későbbi folyamatok azért fontosak, mert egyedi táblázatot hoznak létre, amely célközönséggel kapcsolatos információs szegmenseket előkészíti a megosztásra az elkötelezettséggel kapcsolatos információkkal. (Ha rendszerfrissítés van ütemezve, a későbbi folyamatokat automatikusan tartalmazza.)

1. Ellenőrizze a kiválasztott elemeket, majd kattintson a **Befejezés** gombra.

    :::image type="content" source="media/integrate7.png" alt-text="Az ügyféladatok beállításainak áttekintése.":::

## <a name="export-refined-events-to-audience-insights"></a>exportálja a finomított eseményeket a célközönséggel kapcsolatos információkba

A környezetek közötti kapcsolat létrehozása után exportálhatja a finomított eseményeket az elkötelezettségi információkból a célközönséggel kapcsolatos információkba, és betöltheti azokat új adatforrásként. 

További tájékoztatásért menjen a [Az elkötelezettségi elemzésekből származó webes adatok megosztása a célközönséggel kapcsolatos információkkal](../audience-insights/integrate-engagement-insights.md) részbe.

<!--
## Share engagement insights refined events with audience insights

After you create a link between environments, a new option becomes available for you to share [refined events](refined-events.md) with audience insights.

Consider the following when creating refined events for audience insights: 

- Provide a meaningful name for the refined event. It will be used as an activity name in audience insights.
- Select at least the following properties to create an activity in audience insights: 
    - Signal.Action.Name indicates the activity details.
    - Signal.User.Id maps with the customer ID.
    - Signal.View.Uri is a web address as a basis for segments or measures.
    - Signal.Export.Id is a primary key for events.
    - Signal.Timestamp determines the date and time for the activity.

To share refined events:

1. From the engagement insights menu, select **Data** and then select the **Events** tab.
2. On the **Action** menu, select **Share as activity**.

    :::image type="content" source="media/integrate8.png" alt-text="Data shared events settings.":::

3. You can view and stop actively shared events on the **Export and Sharing** tab.
4. -- per Michael K, we need a mock here (Mukesh needs to update to reflect what happens in AUI once a user shares a refined event (i.e. no longer AUI, data wrangler needs to go discover data in the storage, the shared event is available as a DS and entity, correct?)

### Attach refined events shared as activities to unified profiles in audience insights

You can bring customer web activity data from engagement insights into audience insights. In addition to transactional, demographic, or behavioral data, you can view activities on the web in unified customer profiles. You can then use these profiles to get insights such as segments, measures, and predictions for audience activation.

Follow the steps in [data unification](../audience-insights/data-unification.md) to map, match, and merge website authentication information to unified profiles in audience insights.

You can also share refined events that are now available in audience insights, identified as data sources and entities. 

Next, you can relate event data from engagement insights as unified activities in customer profiles.

### Relate refined event data as an activity of a customer profile

After unifying the data, you can configure the activity for the customer profile. For more information, go to [Customer activities](../audience-insights/activities.md).

:::image type="content" source="media/web-event-activity.png" alt-text="Activities page with expanded Edit activity pane.":::

Next, configure the new activity by using mapping elements: 

- **Primary Key**: Signal.Export.Id, a unique ID that is available for every event record in engagement insights. This property is automatically generated.

- **Timestamp**: Signal.Timestamp in the event property.

- **Event**: Signal.Name, the event name that you want to track.

- **Web address**: Signal.View.Uri that refers to the URI of the page that created the event.

- **Details**: Signal.Action.Name to represent the information to associate with the event. The selected property in this case indicates that the event is for email promotion.

- **Activity type**: In this example, we choose the existing activity type WebLog. This selection is a useful filter option to run prediction models or create segments based on this activity type.

- **Set up relationship**: This important setting ties the activity to existing customer profiles. **Signal.User.Id** is the identifier configured in the SDK to be collected. It relates to the user ID in other data sources that are configured in audience insights. 

This example configures the relationship between Signal.User.Id and RetailCustomers:CustomerRetailId, which is the primary key that was identified in the map step of the data unification process.

After processing the activities, you can review customer records and open a customer card to see activities from engagement insights in the timeline. 

> [!TIP]
> To find a customer ID that has an engagement insights activity, go to **Entities** and preview the data for the UnifiedActivity entity. **ActivityTypeDisplay = WebLog** contains the engagement insights activity configured in the preceding example. Copy the customer ID for one of those records and search<!--note from editor: Edit okay? I couldn't quite follow this.-- > for that ID on the **Customers** page.

--> 

[!INCLUDE[footer-include](../includes/footer-banner.md)]
