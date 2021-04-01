---
title: Power Automate-összekötő | Microsoft Docs
description: Folyamatok létrehozása a Microsoft Power Automate rendszerben a Dynamics 365 Customer Insights szolgáltatásból.
ms.date: 01/20/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: phkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: e973bb11b31c9e70b695ebec8aa2700fdaa5e44f
ms.sourcegitcommit: bae40184312ab27b95c140a044875c2daea37951
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/15/2021
ms.locfileid: "5597928"
---
# <a name="power-automate-connector-preview"></a><span data-ttu-id="023b6-103">Power Automate összekötő (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="023b6-103">Power Automate connector (preview)</span></span>

<span data-ttu-id="023b6-104">Az adatok módosításakor automatikusan elindíthat meghatározott eseményeket, vagy az összetettebb folyamatokat közvetlenül a [Power Automate](https://flow.microsoft.com/) szolgáltatásban is kezelheti.</span><span class="sxs-lookup"><span data-stu-id="023b6-104">Trigger specific events to occur automatically when your data changes and manage more complex flows directly in [Power Automate](https://flow.microsoft.com/).</span></span>

## <a name="power-automate-triggers"></a><span data-ttu-id="023b6-105">Power Automate-eseményindítók</span><span class="sxs-lookup"><span data-stu-id="023b6-105">Power Automate triggers</span></span>

<span data-ttu-id="023b6-106">Az eseményindítók segítségével felhőfolyamatokat hozhat létre, és automatizálhatja az ismétlődő feladatokat, például értesítéseket és speciális műveleteket.</span><span class="sxs-lookup"><span data-stu-id="023b6-106">Use triggers to create cloud flows and automate repetitive tasks, such as notifications or more advanced actions.</span></span> 

- <span data-ttu-id="023b6-107">Az adatforrás frissítésének sikertelensége esetén aktiválódó eseményindító.</span><span class="sxs-lookup"><span data-stu-id="023b6-107">Trigger when a data source refresh fails.</span></span> 
- <span data-ttu-id="023b6-108">Az adatforrás sikeres frissítése esetén aktiválódó eseményindító.</span><span class="sxs-lookup"><span data-stu-id="023b6-108">Trigger when a data source refresh succeeds.</span></span>
- <span data-ttu-id="023b6-109">Egy szegmens küszöbértékének túllépésekor aktiválódó eseményindító.</span><span class="sxs-lookup"><span data-stu-id="023b6-109">Trigger when a threshold is crossed on a segment.</span></span> <span data-ttu-id="023b6-110">Az eseményindító csak a küszöbérték túllépésére korlátozott.</span><span class="sxs-lookup"><span data-stu-id="023b6-110">The trigger is limited to crossing above the threshold.</span></span>
- <span data-ttu-id="023b6-111">Egy üzleti mérőszám küszöbértékének túllépésekor aktiválódó eseményindító.</span><span class="sxs-lookup"><span data-stu-id="023b6-111">Trigger when a threshold is crossed on a business measure.</span></span> <span data-ttu-id="023b6-112">Az eseményindító csak a küszöbérték túllépésére korlátozott.</span><span class="sxs-lookup"><span data-stu-id="023b6-112">The trigger is limited crossing above the threshold.</span></span>
- <span data-ttu-id="023b6-113">Az (adatforrások, a szegmensek, az intézkedések,...) teljes frissítésének indítása.</span><span class="sxs-lookup"><span data-stu-id="023b6-113">Trigger when a full refresh of (data sources, segments, measures,...) is completed.</span></span>
- <span data-ttu-id="023b6-114">Eseményindító az egyesítési folyamat (Térkép, egyeztetés, összefésülés) frissítésének befejezése után.</span><span class="sxs-lookup"><span data-stu-id="023b6-114">Trigger when a refresh of the unification process (map, match, merge) is completed.</span></span>

<span data-ttu-id="023b6-115">[Eseményindítók konfigurálása a Power Automate alkalmazásban](https://flow.microsoft.com/connectors/shared_customerinsights/dynamics-365-customer-insights-connector/).</span><span class="sxs-lookup"><span data-stu-id="023b6-115">[Configure your triggers in Power Automate](https://flow.microsoft.com/connectors/shared_customerinsights/dynamics-365-customer-insights-connector/).</span></span>

## <a name="power-automate-actions"></a><span data-ttu-id="023b6-116">Power Automate-műveletek</span><span class="sxs-lookup"><span data-stu-id="023b6-116">Power Automate actions</span></span>
<span data-ttu-id="023b6-117">A Power Automate-összekötő más műveleteket biztosít, mint az eseményindítók.</span><span class="sxs-lookup"><span data-stu-id="023b6-117">The Power Automate connector provides other actions than the available triggers.</span></span> <span data-ttu-id="023b6-118">További információ itt található: [Dynamics 365 Customer Insights Connector](/connectors/customerinsights/).</span><span class="sxs-lookup"><span data-stu-id="023b6-118">For more information, see the [Dynamics 365 Customer Insights Connector](/connectors/customerinsights/).</span></span>

## <a name="create-a-power-automate-flow"></a><span data-ttu-id="023b6-119">Power Automate-folyamat létrehozása</span><span class="sxs-lookup"><span data-stu-id="023b6-119">Create a Power Automate flow</span></span>

1. <span data-ttu-id="023b6-120">A célközönség információin belül nyissa meg a következőt **Rendszergazda** > **Exportálási célhelyek**.</span><span class="sxs-lookup"><span data-stu-id="023b6-120">In audience insights, go to **Admin** > **Export destinations**.</span></span>

1. <span data-ttu-id="023b6-121">A **Power Automate** csempén válassza a **Beállítás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="023b6-121">On the **Power Automate** tile, select **Set up**.</span></span>

1. <span data-ttu-id="023b6-122">Megnyílik a Customer Insights-összekötő (előzetes verzió) a Power Automate szolgáltatásban.</span><span class="sxs-lookup"><span data-stu-id="023b6-122">The Customer Insights Connector (preview) in Power Automate opens.</span></span> <span data-ttu-id="023b6-123">**Jelentkezzen be** a Power Automate-szolgáltatásba.</span><span class="sxs-lookup"><span data-stu-id="023b6-123">**Sign in** to Power Automate.</span></span>

1. <span data-ttu-id="023b6-124">Válassza ki az egyik elérhető eseményindítót, és adjon hozzá további lépéseket az új folyamathoz.</span><span class="sxs-lookup"><span data-stu-id="023b6-124">Choose one of the available triggers and add more steps to your new flow.</span></span> <span data-ttu-id="023b6-125">További információ: [Felhőfolyamat létrehozása a Power Automate-szolgáltatásban](/power-automate/get-started-logic-flow).</span><span class="sxs-lookup"><span data-stu-id="023b6-125">For more information, see [Create a cloud flow in Power Automate](/power-automate/get-started-logic-flow).</span></span>

<span data-ttu-id="023b6-126">Példák a folyamatok használatára:</span><span class="sxs-lookup"><span data-stu-id="023b6-126">Examples how to use flows:</span></span> 
- <span data-ttu-id="023b6-127">Ha az adatforrás frissítése sikertelen üzenet küldése a Microsoft Teams csatornára.</span><span class="sxs-lookup"><span data-stu-id="023b6-127">Post a message to a Microsoft Teams channel if a data source refresh fails.</span></span> 
- <span data-ttu-id="023b6-128">E-mail küldése az adattulajdonosoknak, ha egy szegmensre vonatkozó küszöbérték túllépésre kerül.</span><span class="sxs-lookup"><span data-stu-id="023b6-128">Send an email to the data owners when a threshold on a segment is crossed.</span></span>



[!INCLUDE[footer-include](../includes/footer-banner.md)]