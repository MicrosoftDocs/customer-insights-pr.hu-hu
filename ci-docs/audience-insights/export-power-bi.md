---
title: Power BI-csatlakozó
description: Útmutató a Dynamics 365 Customer Insights összekötő használatához a Power BI megoldásban.
ms.date: 09/21/2020
ms.reviewer: sthe
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: d497ca779a337c512a7254524f597cff226bcb45
ms.sourcegitcommit: cf9b78559ca189d4c2086a66c879098d56c0377a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/03/2020
ms.locfileid: "4405983"
---
# <a name="connector-for-power-bi-preview"></a><span data-ttu-id="5d32b-103">Power BI összekötő (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="5d32b-103">Connector for Power BI (preview)</span></span>

<span data-ttu-id="5d32b-104">Az adatokhoz vizuális megjelenítést hozhat létre a Power BI Desktoppal.</span><span class="sxs-lookup"><span data-stu-id="5d32b-104">Create visualizations for your data with the Power BI Desktop.</span></span> <span data-ttu-id="5d32b-105">További betekintést hozhat létre és jelentéseket készíthet az egyesített ügyfelek adataival.</span><span class="sxs-lookup"><span data-stu-id="5d32b-105">Generate additional insights and build reports with your unified customer data.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5d32b-106">Előfeltételek</span><span class="sxs-lookup"><span data-stu-id="5d32b-106">Prerequisites</span></span>

- <span data-ttu-id="5d32b-107">Az egyesített ügyfélprofilokkal rendelkezik.</span><span class="sxs-lookup"><span data-stu-id="5d32b-107">You have unified customer profiles.</span></span>
- <span data-ttu-id="5d32b-108">A számítógépen telepítve van a [Microsoft Power BI Desktop](https://powerbi.microsoft.com/desktop/) legújabb verziója .</span><span class="sxs-lookup"><span data-stu-id="5d32b-108">The latest version of [Microsoft Power BI Desktop](https://powerbi.microsoft.com/desktop/) is installed on your computer.</span></span> <span data-ttu-id="5d32b-109">[További információk: Power BI Desktop](https://docs.microsoft.com/power-bi/desktop-what-is-desktop).</span><span class="sxs-lookup"><span data-stu-id="5d32b-109">[Learn more about Power BI Desktop](https://docs.microsoft.com/power-bi/desktop-what-is-desktop).</span></span>

## <a name="configure-the-connector-for-power-bi"></a><span data-ttu-id="5d32b-110">Az összekötő beállítása a Power BI számára</span><span class="sxs-lookup"><span data-stu-id="5d32b-110">Configure the connector for Power BI</span></span>

1. <span data-ttu-id="5d32b-111">A Power BI Desktop alkalmazásban válassza a **Fájl** > **Adatok lekérése** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="5d32b-111">In Power BI Desktop, select **File** > **Get Data**.</span></span>

1. <span data-ttu-id="5d32b-112">Válassza a **Továbbiak megtekintése** elemet, és keressen erre: **Dynamics 365 Customer Insights**</span><span class="sxs-lookup"><span data-stu-id="5d32b-112">Select **See more** and search for **Dynamics 365 Customer Insights**</span></span>

1. <span data-ttu-id="5d32b-113">Jelölje ki az eredményt, és válassza a **Kapcsolódás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="5d32b-113">Select the result and select **Connect**.</span></span>

1. <span data-ttu-id="5d32b-114">**Jelentkezzen be** ugyanazzal a szervezeti fiókkal, amelyet a Customer Insights esetében használ, és válassza a **Csatlakozás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="5d32b-114">**Sign in** with the same organizational account you use for Customer Insights and select **Connect**.</span></span>
   > [!NOTE]
   > <span data-ttu-id="5d32b-115">Az ebben a lépésben megadott fiók az adatoknak a Customer Insights alkalmazásból történő beolvasására szolgál, és nem kell ugyanannak lennie, mint a Power BI-ba bejelentkezéskor.</span><span class="sxs-lookup"><span data-stu-id="5d32b-115">The account you indicate in this step is used to fetch data from Customer Insights and doesn't need to be the same you are signed in to Power BI.</span></span> <span data-ttu-id="5d32b-116">Az adatok beolvasásához használt partner alaphelyzetbe állításához nyissa meg a Power BI-t, és nyissa meg a **Fájl** > **Beállítások** > **Beállítások** > **Adatforrás beállításai**.</span><span class="sxs-lookup"><span data-stu-id="5d32b-116">To reset the account that is used for data fetching, open Power BI and go to **File** > **Options** > **Settings** > **Data source settings**.</span></span> <span data-ttu-id="5d32b-117">Az adatforrások listájában válassza a **Dynamics 365 Customer Insights bejelentkezés** lehetőséget, és válassza az **engedélyek törlése** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="5d32b-117">In the list of data sources, select **Dynamics 365 Customer Insights Login** and select **Clear permissions**.</span></span>  

1. <span data-ttu-id="5d32b-118">A **Navigátor** párbeszédpanelen.</span><span class="sxs-lookup"><span data-stu-id="5d32b-118">In the **Navigator** dialog box.</span></span> <span data-ttu-id="5d32b-119">megtekintheti az összes olyan környezet listáját, amelyhez hozzáféréssel rendelkezik.</span><span class="sxs-lookup"><span data-stu-id="5d32b-119">you see the list of all environments you have access to.</span></span> <span data-ttu-id="5d32b-120">Bontson ki egy környezetet, és nyissa meg bármelyik mappát (entitások, intézkedések, szegmensek, bővítések).</span><span class="sxs-lookup"><span data-stu-id="5d32b-120">Expand an environment and open any of the folders (entities, measures, segments, enrichments).</span></span> <span data-ttu-id="5d32b-121">Nyissa meg például az **Entitások** mappát, és tekintse meg az összes importálható entitást.</span><span class="sxs-lookup"><span data-stu-id="5d32b-121">For example, open the **Entities** folder, to see all entities you can import.</span></span>

   <span data-ttu-id="5d32b-122">![Power BI összekötő navigátor](media/power-bi-navigator.png "Power BI összekötő navigátor")</span><span class="sxs-lookup"><span data-stu-id="5d32b-122">![Power BI Connector Navigator](media/power-bi-navigator.png "Power BI Connector Navigator")</span></span>

1. <span data-ttu-id="5d32b-123">Jelölje be a szerepeltetni és betölteni kívánt entitások melletti jelölőnégyzeteket, és válassza a **Betöltés** elemet.</span><span class="sxs-lookup"><span data-stu-id="5d32b-123">Select the check boxes next to the entities to include and **Load**.</span></span> <span data-ttu-id="5d32b-124">Többe entitást is kiválaszthat több környezetből.</span><span class="sxs-lookup"><span data-stu-id="5d32b-124">You can select multiple entities from multiple environments.</span></span>

1. <span data-ttu-id="5d32b-125">A betöltési párbeszédpanel jelenik meg az entitások betöltése közben.</span><span class="sxs-lookup"><span data-stu-id="5d32b-125">You'll see a loading dialog box while your entities are loaded.</span></span> <span data-ttu-id="5d32b-126">Ha az összes kijelölt entitás be van töltve, az adatok megjelenítéséhez használhatja a Power BI-lehetőségeket.</span><span class="sxs-lookup"><span data-stu-id="5d32b-126">Once all of your selected entities have loaded, you can use the capabilities of Power BI to visualize the data.</span></span>

## <a name="large-data-sets"></a><span data-ttu-id="5d32b-127">Nagy adathalmazok</span><span class="sxs-lookup"><span data-stu-id="5d32b-127">Large data sets</span></span>

<span data-ttu-id="5d32b-128">A Customer Insights Power BI-csatlakozója az egymillió ügyfélprofilig terjedő adatkészletek feldolgozására szolgál.</span><span class="sxs-lookup"><span data-stu-id="5d32b-128">The Customer Insights connector for Power BI is designed to work for data sets that contain up to 1 million customer profiles.</span></span> <span data-ttu-id="5d32b-129">A nagyobb adathalmazok importálása működhet, de hosszú időt igényel.</span><span class="sxs-lookup"><span data-stu-id="5d32b-129">Importing larger data sets may work, but it takes a long time.</span></span> <span data-ttu-id="5d32b-130">Emellett a folyamat a Power BI-korlátozásai miatt időtúllépés is előfordulhat.</span><span class="sxs-lookup"><span data-stu-id="5d32b-130">Additionally, the process could run into a time-out because of Power BI limitations.</span></span> <span data-ttu-id="5d32b-131">További információkért lásd [Power BI: Nagyméretű adathalmazokra vonatkozó ajánlások](https://docs.microsoft.com/power-bi/admin/service-premium-what-is#large-datasets).</span><span class="sxs-lookup"><span data-stu-id="5d32b-131">For more information, see [Power BI: Recommendations for large data sets](https://docs.microsoft.com/power-bi/admin/service-premium-what-is#large-datasets).</span></span> 

### <a name="work-with-a-subset-of-data"></a><span data-ttu-id="5d32b-132">Munka az adatok egy részhalmazával</span><span class="sxs-lookup"><span data-stu-id="5d32b-132">Work with a subset of data</span></span>

<span data-ttu-id="5d32b-133">Érdemes lehet az adatok egy részhalmazával dolgozni.</span><span class="sxs-lookup"><span data-stu-id="5d32b-133">Consider working with a subset of your data.</span></span> <span data-ttu-id="5d32b-134">Létrehozhatók például olyan [szegmensek](segments.md), amelyek nem exportálják az összes ügyfélrekordot a Power BI-be.</span><span class="sxs-lookup"><span data-stu-id="5d32b-134">For example, you can create [segments](segments.md) instead of exporting all customer records to Power BI.</span></span>
