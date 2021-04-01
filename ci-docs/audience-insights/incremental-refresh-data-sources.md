---
title: A Power Queryn alapuló adatforrások növekményes frissítése
description: Az új és frissített adatok frissítése a nagyméretű adatforrásoknál Power Query alapján.
ms.date: 09/28/2020
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: adkuppa
ms.author: adkuppa
manager: shellyha
ms.openlocfilehash: 03f76bcfc7336d8430146e8a26ffa649c6a17db0
ms.sourcegitcommit: bae40184312ab27b95c140a044875c2daea37951
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/15/2021
ms.locfileid: "5596824"
---
# <a name="incremental-refresh-for-data-sources-based-on-power-query"></a><span data-ttu-id="799d2-103">A Power Queryn alapuló adatforrások növekményes frissítése</span><span class="sxs-lookup"><span data-stu-id="799d2-103">Incremental refresh for data sources based on Power Query</span></span>

<span data-ttu-id="799d2-104">Az adatforrások növekményes frissítése a következő előnyöket nyújtja:</span><span class="sxs-lookup"><span data-stu-id="799d2-104">Incremental refresh for data sources provides the following advantages:</span></span>

- <span data-ttu-id="799d2-105">**Gyorsabb frissítések** - Csak a megváltozott adatok frissülnek.</span><span class="sxs-lookup"><span data-stu-id="799d2-105">**Faster refreshes** - Only data that has changed gets refreshed.</span></span> <span data-ttu-id="799d2-106">Előfordulhat például, hogy a régi adatkészletből csak az elmúlt öt napot frissíti.</span><span class="sxs-lookup"><span data-stu-id="799d2-106">For example, you might refresh only the past five days of a historical dataset.</span></span>
- <span data-ttu-id="799d2-107">**Fokozott megbízhatóság** – Kisebb frissítésekkel nem kell kapcsolatot olyan sokáig fenntartania a változékony forrásoldali rendszerekkel így a kapcsolati problémák veszélye csökkenthető.</span><span class="sxs-lookup"><span data-stu-id="799d2-107">**Increased reliability** - With smaller refreshes, you don't need to maintain connections to volatile source systems for as long, reducing the risk of connection issues.</span></span>
- <span data-ttu-id="799d2-108">**Csökkentett erőforrás- felhasználás** – A teljes adatok csak egy részhalmazának frissítése a számítási erőforrások hatékonyabb kihasználásával és a környezeti lábnyom csökkentésével jár.</span><span class="sxs-lookup"><span data-stu-id="799d2-108">**Reduced resource consumption** - Refreshing only a subset of your total data leads to more efficient use of computing resources and decreases the environmental footprint.</span></span>

## <a name="configure-incremental-refresh"></a><span data-ttu-id="799d2-109">Növekményes frissítés konfigurálása</span><span class="sxs-lookup"><span data-stu-id="799d2-109">Configure incremental refresh</span></span>

<span data-ttu-id="799d2-110">A célközönség-információk lehetővé teszi a növekményes betöltést támogató Power Query keresztül importált adatforrások növekményes frissítésére.</span><span class="sxs-lookup"><span data-stu-id="799d2-110">Audience insights allows incremental refresh for data sources imported through Power Query that support incremental ingestion.</span></span> <span data-ttu-id="799d2-111">Például a dátum és idő típusú mezőkkel rendelkező Azure SQL-adatbázisokat, amelyek jelzik az adatbejegyzések legutóbbi frissítését.</span><span class="sxs-lookup"><span data-stu-id="799d2-111">For example, Azure SQL databases with date and time fields, which indicate when data records were last updated.</span></span>

1. <span data-ttu-id="799d2-112">[Új adatforrás létrehozása a Power Query alapján ](connect-power-query.md).</span><span class="sxs-lookup"><span data-stu-id="799d2-112">[Create a new data source based on Power Query](connect-power-query.md).</span></span>

1. <span data-ttu-id="799d2-113">Írja be az adatforrás nevét.</span><span class="sxs-lookup"><span data-stu-id="799d2-113">Provide a name for the data source.</span></span>

1. <span data-ttu-id="799d2-114">Jelöljön ki egy olyan adatforrás, amely támogatja a növekményes frissítést, például egy Azure SQL-adatbázist.</span><span class="sxs-lookup"><span data-stu-id="799d2-114">Select a data source that supports incremental refresh, such as Azure SQL database.</span></span>

1. <span data-ttu-id="799d2-115">Jelölje ki a betölteni kívánt entitásokat vagy táblákat.</span><span class="sxs-lookup"><span data-stu-id="799d2-115">Select the entities or tables to ingest.</span></span>

1. <span data-ttu-id="799d2-116">Hajtsa végre az átalakítási lépéseket, és válassza a **Tovább** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="799d2-116">Complete the transformation steps and select **Next**.</span></span>

1. <span data-ttu-id="799d2-117">A **Növekményes frissítés beállítása** párbeszédpanelen válassza a **Beállítás** lehetőséget **Növekményes frissítés beállításainak** megnyitásához.</span><span class="sxs-lookup"><span data-stu-id="799d2-117">In the **Set up incremental refresh** dialog box, select **Set up** to open the **Incremental refresh settings**.</span></span> <span data-ttu-id="799d2-118">Ha a **Kihagyás** lehetőséget választja, akkor a adatforrás frissíti a teljes adatkészlet.</span><span class="sxs-lookup"><span data-stu-id="799d2-118">If you select **Skip**, the data source will refresh the entire data set.</span></span>
   > [!TIP]
   > <span data-ttu-id="799d2-119">A növekményes frissítést később is alkalmazhatja egy meglévő adatforrás szerkesztésével.</span><span class="sxs-lookup"><span data-stu-id="799d2-119">You can also apply incremental refresh later by editing an existing data source.</span></span>

1. <span data-ttu-id="799d2-120">A **Növekményes frissítésbeállításai** alatt a adatforrás létrehozásakor kiválasztott összes entitásra vonatkozóan konfigurálja a növekményes frissítést.</span><span class="sxs-lookup"><span data-stu-id="799d2-120">On **Incremental refresh settings**, you'll configure the incremental refresh for all entities that you selected when creating the data source.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="799d2-121">![Entitások konfigurálása egy adatforrásban növekményes frissítéshez](media/incremental-refresh-settings.png "Entitások konfigurálása egy adatforrásban növekményes frissítéshez")</span><span class="sxs-lookup"><span data-stu-id="799d2-121">![Configure entities in a data source for incremental refresh](media/incremental-refresh-settings.png "Configure entities in a data source for incremental refresh")</span></span>

1. <span data-ttu-id="799d2-122">Jelöljön ki egy entitást, és adja meg a következő adatokat:</span><span class="sxs-lookup"><span data-stu-id="799d2-122">Select an entity, and provide the following details:</span></span>

   - <span data-ttu-id="799d2-123">**Adja meg az elsődlegeskulcsot**: Válasszon ki egy elsődleges kulcsot az entitáshoz vagy a táblához.</span><span class="sxs-lookup"><span data-stu-id="799d2-123">**Define the primary key**: Select a primary key for the entity or table.</span></span>
   - <span data-ttu-id="799d2-124">**Határozza meg a „legutóbbi frissítve”mezőt**: Ez a mező csak a dátum vagy idő típusú attribútumokat jeleníti meg.</span><span class="sxs-lookup"><span data-stu-id="799d2-124">**Define the "last updated" field**: This field will only display attributes of type date or time.</span></span> <span data-ttu-id="799d2-125">Jelöljön ki egy attribútumot, amely jelzi, hogy mikor frissítették utoljára a bejegyzéseket.</span><span class="sxs-lookup"><span data-stu-id="799d2-125">Select an attribute that indicates when the records were last updated.</span></span> <span data-ttu-id="799d2-126">A rendszer a növekményes frissítés időkeretébe tartozó bejegyzések azonosítására szolgál.</span><span class="sxs-lookup"><span data-stu-id="799d2-126">It will be used to identify the records that fall within the incremental refresh time frame.</span></span>
   - <span data-ttu-id="799d2-127">**Frissítések keresése minden**: Határozza meg, hogy a növekményes frissítés milyen hosszú időkerettel rendelkezzen.</span><span class="sxs-lookup"><span data-stu-id="799d2-127">**Check for updates every**: Specify how long you want the incremental refresh time frame to be.</span></span>

1. <span data-ttu-id="799d2-128">Válassza a **Mentés** lehetőséget a adatforrás létrehozásának befejezéséhez.</span><span class="sxs-lookup"><span data-stu-id="799d2-128">Select **Save** to complete the creation of the data source.</span></span> <span data-ttu-id="799d2-129">A kezdeti adatfrissítés teljes körű frissítés lesz.</span><span class="sxs-lookup"><span data-stu-id="799d2-129">The initial data refresh will be a full refresh.</span></span> <span data-ttu-id="799d2-130">Ezt követően a növekményes adatfrissítés történik az előző lépésben beállítottak alapján.</span><span class="sxs-lookup"><span data-stu-id="799d2-130">Afterwards, the incremental data refresh happens as configured in the previous step.</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]