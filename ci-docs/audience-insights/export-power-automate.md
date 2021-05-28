---
title: Power Automate-összekötő | Microsoft Docs
description: Folyamatok létrehozása a Microsoft Power Automate rendszerben a Dynamics 365 Customer Insights szolgáltatásból.
ms.date: 01/20/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: ce2477d957a1792e0436a0dfc15a33621b1c89a9
ms.sourcegitcommit: e8e03309ba2515374a70c132d0758f3e1e1851d0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/04/2021
ms.locfileid: "5976091"
---
# <a name="power-automate-connector-preview"></a><span data-ttu-id="4e956-103">Power Automate összekötő (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="4e956-103">Power Automate connector (preview)</span></span>

<span data-ttu-id="4e956-104">Az adatok módosításakor automatikusan elindíthat meghatározott eseményeket, vagy az összetettebb folyamatokat közvetlenül a [Power Automate](https://flow.microsoft.com/) szolgáltatásban is kezelheti.</span><span class="sxs-lookup"><span data-stu-id="4e956-104">Trigger specific events to occur automatically when your data changes and manage more complex flows directly in [Power Automate](https://flow.microsoft.com/).</span></span>

## <a name="power-automate-triggers"></a><span data-ttu-id="4e956-105">Power Automate-eseményindítók</span><span class="sxs-lookup"><span data-stu-id="4e956-105">Power Automate triggers</span></span>

<span data-ttu-id="4e956-106">Az eseményindítók segítségével felhőfolyamatokat hozhat létre, és automatizálhatja az ismétlődő feladatokat, például értesítéseket és speciális műveleteket.</span><span class="sxs-lookup"><span data-stu-id="4e956-106">Use triggers to create cloud flows and automate repetitive tasks, such as notifications or more advanced actions.</span></span> 

- <span data-ttu-id="4e956-107">Az adatforrás frissítésének sikertelensége esetén aktiválódó eseményindító.</span><span class="sxs-lookup"><span data-stu-id="4e956-107">Trigger when a data source refresh fails.</span></span> 
- <span data-ttu-id="4e956-108">Az adatforrás sikeres frissítése esetén aktiválódó eseményindító.</span><span class="sxs-lookup"><span data-stu-id="4e956-108">Trigger when a data source refresh succeeds.</span></span>
- <span data-ttu-id="4e956-109">Egy szegmens küszöbértékének túllépésekor aktiválódó eseményindító.</span><span class="sxs-lookup"><span data-stu-id="4e956-109">Trigger when a threshold is crossed on a segment.</span></span> <span data-ttu-id="4e956-110">Az eseményindító csak a küszöbérték túllépésére korlátozott.</span><span class="sxs-lookup"><span data-stu-id="4e956-110">The trigger is limited to crossing above the threshold.</span></span>
- <span data-ttu-id="4e956-111">Egy üzleti mérőszám küszöbértékének túllépésekor aktiválódó eseményindító.</span><span class="sxs-lookup"><span data-stu-id="4e956-111">Trigger when a threshold is crossed on a business measure.</span></span> <span data-ttu-id="4e956-112">Csak a dimenzió nélküli üzleti mérőszámok támogatottak.</span><span class="sxs-lookup"><span data-stu-id="4e956-112">Only business measures without a dimension are supported.</span></span> <span data-ttu-id="4e956-113">Az eseményindító csak a küszöbérték túllépésére korlátozott.</span><span class="sxs-lookup"><span data-stu-id="4e956-113">The trigger is limited crossing above the threshold.</span></span>
- <span data-ttu-id="4e956-114">Az (adatforrások, a szegmensek, az intézkedések,...) teljes frissítésének indítása.</span><span class="sxs-lookup"><span data-stu-id="4e956-114">Trigger when a full refresh of (data sources, segments, measures,...) is completed.</span></span>
- <span data-ttu-id="4e956-115">Eseményindító az egyesítési folyamat (Térkép, egyeztetés, összefésülés) frissítésének befejezése után.</span><span class="sxs-lookup"><span data-stu-id="4e956-115">Trigger when a refresh of the unification process (map, match, merge) is completed.</span></span>

<span data-ttu-id="4e956-116">[Eseményindítók konfigurálása a Power Automate alkalmazásban](https://flow.microsoft.com/connectors/shared_customerinsights/dynamics-365-customer-insights-connector/).</span><span class="sxs-lookup"><span data-stu-id="4e956-116">[Configure your triggers in Power Automate](https://flow.microsoft.com/connectors/shared_customerinsights/dynamics-365-customer-insights-connector/).</span></span>

## <a name="power-automate-actions"></a><span data-ttu-id="4e956-117">Power Automate-műveletek</span><span class="sxs-lookup"><span data-stu-id="4e956-117">Power Automate actions</span></span>
<span data-ttu-id="4e956-118">A Power Automate-összekötő más műveleteket biztosít, mint az eseményindítók.</span><span class="sxs-lookup"><span data-stu-id="4e956-118">The Power Automate connector provides other actions than the available triggers.</span></span> <span data-ttu-id="4e956-119">További információ itt található: [Dynamics 365 Customer Insights Connector](/connectors/customerinsights/).</span><span class="sxs-lookup"><span data-stu-id="4e956-119">For more information, see the [Dynamics 365 Customer Insights Connector](/connectors/customerinsights/).</span></span>

## <a name="create-a-power-automate-flow"></a><span data-ttu-id="4e956-120">Power Automate-folyamat létrehozása</span><span class="sxs-lookup"><span data-stu-id="4e956-120">Create a Power Automate flow</span></span>

1. <span data-ttu-id="4e956-121">A célközönség információin belül nyissa meg a következőt **Rendszergazda** > **Exportálási célhelyek**.</span><span class="sxs-lookup"><span data-stu-id="4e956-121">In audience insights, go to **Admin** > **Export destinations**.</span></span>

1. <span data-ttu-id="4e956-122">A **Power Automate** csempén válassza a **Beállítás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="4e956-122">On the **Power Automate** tile, select **Set up**.</span></span>

1. <span data-ttu-id="4e956-123">Megnyílik a Customer Insights-összekötő (előzetes verzió) a Power Automate szolgáltatásban.</span><span class="sxs-lookup"><span data-stu-id="4e956-123">The Customer Insights Connector (preview) in Power Automate opens.</span></span> <span data-ttu-id="4e956-124">**Jelentkezzen be** a Power Automate-szolgáltatásba.</span><span class="sxs-lookup"><span data-stu-id="4e956-124">**Sign in** to Power Automate.</span></span>

1. <span data-ttu-id="4e956-125">Válassza ki az egyik elérhető eseményindítót, és adjon hozzá további lépéseket az új folyamathoz.</span><span class="sxs-lookup"><span data-stu-id="4e956-125">Choose one of the available triggers and add more steps to your new flow.</span></span> <span data-ttu-id="4e956-126">További információ: [Felhőfolyamat létrehozása a Power Automate-szolgáltatásban](/power-automate/get-started-logic-flow).</span><span class="sxs-lookup"><span data-stu-id="4e956-126">For more information, see [Create a cloud flow in Power Automate](/power-automate/get-started-logic-flow).</span></span>

<span data-ttu-id="4e956-127">Példák a folyamatok használatára:</span><span class="sxs-lookup"><span data-stu-id="4e956-127">Examples how to use flows:</span></span> 
- <span data-ttu-id="4e956-128">Ha az adatforrás frissítése sikertelen üzenet küldése a Microsoft Teams csatornára.</span><span class="sxs-lookup"><span data-stu-id="4e956-128">Post a message to a Microsoft Teams channel if a data source refresh fails.</span></span> 
- <span data-ttu-id="4e956-129">E-mail küldése az adattulajdonosoknak, ha egy szegmensre vonatkozó küszöbérték túllépésre kerül.</span><span class="sxs-lookup"><span data-stu-id="4e956-129">Send an email to the data owners when a threshold on a segment is crossed.</span></span>



[!INCLUDE[footer-include](../includes/footer-banner.md)]
