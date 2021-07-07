---
title: Power Automate-összekötő | Microsoft Docs
description: Folyamatok létrehozása a Microsoft Power Automate rendszerben a Dynamics 365 Customer Insights szolgáltatásból.
ms.date: 06/24/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 57be0a204ef920b7a4bb31cf9a5b3a77f96eca0d
ms.sourcegitcommit: d84d664e67f263bfeb741154d309088c5101b9c3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/24/2021
ms.locfileid: "6305067"
---
# <a name="power-automate-connector-preview"></a><span data-ttu-id="214fe-103">Power Automate összekötő (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="214fe-103">Power Automate connector (preview)</span></span>

<span data-ttu-id="214fe-104">Az adatok módosításakor automatikusan elindíthat meghatározott eseményeket, vagy az összetettebb folyamatokat közvetlenül a [Power Automate](https://flow.microsoft.com/) szolgáltatásban is kezelheti.</span><span class="sxs-lookup"><span data-stu-id="214fe-104">Trigger specific events to occur automatically when your data changes and manage more complex flows directly in [Power Automate](https://flow.microsoft.com/).</span></span>

## <a name="power-automate-triggers"></a><span data-ttu-id="214fe-105">Power Automate-eseményindítók</span><span class="sxs-lookup"><span data-stu-id="214fe-105">Power Automate triggers</span></span>

<span data-ttu-id="214fe-106">Az eseményindítók segítségével felhőfolyamatokat hozhat létre, és automatizálhatja az ismétlődő feladatokat, például értesítéseket és speciális műveleteket.</span><span class="sxs-lookup"><span data-stu-id="214fe-106">Use triggers to create cloud flows and automate repetitive tasks, such as notifications or more advanced actions.</span></span> 

- <span data-ttu-id="214fe-107">Az adatforrás frissítésének sikertelensége esetén aktiválódó eseményindító.</span><span class="sxs-lookup"><span data-stu-id="214fe-107">Trigger when a data source refresh fails.</span></span> 
- <span data-ttu-id="214fe-108">Az adatforrás sikeres frissítése esetén aktiválódó eseményindító.</span><span class="sxs-lookup"><span data-stu-id="214fe-108">Trigger when a data source refresh succeeds.</span></span>
- <span data-ttu-id="214fe-109">Egy szegmens küszöbértékének túllépésekor aktiválódó eseményindító.</span><span class="sxs-lookup"><span data-stu-id="214fe-109">Trigger when a threshold is crossed on a segment.</span></span> <span data-ttu-id="214fe-110">Az eseményindító csak a küszöbérték túllépésére korlátozott.</span><span class="sxs-lookup"><span data-stu-id="214fe-110">The trigger is limited to crossing above the threshold.</span></span>
- <span data-ttu-id="214fe-111">Egy üzleti mérőszám küszöbértékének túllépésekor aktiválódó eseményindító.</span><span class="sxs-lookup"><span data-stu-id="214fe-111">Trigger when a threshold is crossed on a business measure.</span></span> <span data-ttu-id="214fe-112">Csak a dimenzió nélküli üzleti mérőszámok támogatottak.</span><span class="sxs-lookup"><span data-stu-id="214fe-112">Only business measures without a dimension are supported.</span></span> <span data-ttu-id="214fe-113">Az eseményindító csak a küszöbérték túllépésére korlátozott.</span><span class="sxs-lookup"><span data-stu-id="214fe-113">The trigger is limited to crossing above the threshold.</span></span>
- <span data-ttu-id="214fe-114">Aktivál, amikor az (adatforrások, szegmensek, intézkedések,...) teljes frissítése befejeződött.</span><span class="sxs-lookup"><span data-stu-id="214fe-114">Trigger when a full refresh of (data sources, segments, measures, ...) is completed.</span></span>
- <span data-ttu-id="214fe-115">Eseményindító az egyesítési folyamat (Térkép, egyeztetés, összefésülés) frissítésének befejezése után.</span><span class="sxs-lookup"><span data-stu-id="214fe-115">Trigger when a refresh of the unification process (map, match, merge) is completed.</span></span>

[<span data-ttu-id="214fe-116">Konfiguráld a triggereket Power Automate.</span><span class="sxs-lookup"><span data-stu-id="214fe-116">Configure your triggers in Power Automate.</span></span>](https://flow.microsoft.com/connectors/shared_customerinsights/dynamics-365-customer-insights-connector/)

## <a name="power-automate-actions"></a><span data-ttu-id="214fe-117">Power Automate-műveletek</span><span class="sxs-lookup"><span data-stu-id="214fe-117">Power Automate actions</span></span>

<span data-ttu-id="214fe-118">A Power Automate-összekötő más műveleteket biztosít, mint az eseményindítók.</span><span class="sxs-lookup"><span data-stu-id="214fe-118">The Power Automate connector provides other actions than the available triggers.</span></span> <span data-ttu-id="214fe-119">További információ itt található: [Dynamics 365 Customer Insights Connector](/connectors/customerinsights/).</span><span class="sxs-lookup"><span data-stu-id="214fe-119">For more information, see the [Dynamics 365 Customer Insights Connector](/connectors/customerinsights/).</span></span>

## <a name="create-a-power-automate-flow"></a><span data-ttu-id="214fe-120">Power Automate-folyamat létrehozása</span><span class="sxs-lookup"><span data-stu-id="214fe-120">Create a Power Automate flow</span></span>

1. <span data-ttu-id="214fe-121">A célközönség információin belül nyissa meg a következőt **Rendszergazda** > **Exportálási célhelyek**.</span><span class="sxs-lookup"><span data-stu-id="214fe-121">In audience insights, go to **Admin** > **Export destinations**.</span></span>

1. <span data-ttu-id="214fe-122">A **Power Automate** csempén válassza a **Beállítás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="214fe-122">On the **Power Automate** tile, select **Set up**.</span></span>

1. <span data-ttu-id="214fe-123">Megnyílik a Customer Insights-összekötő (előzetes verzió) a Power Automate szolgáltatásban.</span><span class="sxs-lookup"><span data-stu-id="214fe-123">The Customer Insights Connector (preview) in Power Automate opens.</span></span> <span data-ttu-id="214fe-124">**Jelentkezzen be** a Power Automate-szolgáltatásba.</span><span class="sxs-lookup"><span data-stu-id="214fe-124">**Sign in** to Power Automate.</span></span>

1. <span data-ttu-id="214fe-125">Válassza ki az egyik elérhető eseményindítót, és adjon hozzá további lépéseket az új folyamathoz.</span><span class="sxs-lookup"><span data-stu-id="214fe-125">Choose one of the available triggers and add more steps to your new flow.</span></span> <span data-ttu-id="214fe-126">További információ: [Felhőfolyamat létrehozása a Power Automate-szolgáltatásban](/power-automate/get-started-logic-flow).</span><span class="sxs-lookup"><span data-stu-id="214fe-126">For more information, see [Create a cloud flow in Power Automate](/power-automate/get-started-logic-flow).</span></span>

<span data-ttu-id="214fe-127">Példák a folyamatok használatára:</span><span class="sxs-lookup"><span data-stu-id="214fe-127">Examples of how to use flows:</span></span> 
- <span data-ttu-id="214fe-128">Ha az adatforrás frissítése sikertelen üzenet küldése a Microsoft Teams csatornára.</span><span class="sxs-lookup"><span data-stu-id="214fe-128">Post a message to a Microsoft Teams channel if a data source refresh fails.</span></span> 
- <span data-ttu-id="214fe-129">E-mail küldése az adattulajdonosoknak, ha egy szegmensre vonatkozó küszöbérték túllépésre kerül.</span><span class="sxs-lookup"><span data-stu-id="214fe-129">Send an email to the data owners when a threshold on a segment is crossed.</span></span>



[!INCLUDE[footer-include](../includes/footer-banner.md)]
