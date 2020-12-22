---
title: Power Automate-összekötő | Microsoft Docs
description: Hozzon létre folyamatokat a Microsoft Power Automate alkalmazásból a Dynamics 365 Customer Insights szolgáltatásba.
ms.date: 08/03/2020
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
ms.reviewer: philk
manager: shellyha
ms.openlocfilehash: ffe92414365b0b777691a4a2d585100e4fbea591
ms.sourcegitcommit: cf9b78559ca189d4c2086a66c879098d56c0377a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/03/2020
ms.locfileid: "4405978"
---
# <a name="power-automate-connector-preview"></a><span data-ttu-id="a80e9-103">Power Automate összekötő (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="a80e9-103">Power Automate connector (preview)</span></span>

<span data-ttu-id="a80e9-104">Az adatok módosításakor automatikusan elindíthat meghatározott eseményeket, vagy az összetettebb folyamatokat közvetlenül a [Power Automate](https://flow.microsoft.com/) szolgáltatásban is kezelheti.</span><span class="sxs-lookup"><span data-stu-id="a80e9-104">Trigger specific events to occur automatically when your data changes and manage more complex flows directly in [Power Automate](https://flow.microsoft.com/).</span></span>

## <a name="power-automate-triggers"></a><span data-ttu-id="a80e9-105">Power Automate-eseményindítók</span><span class="sxs-lookup"><span data-stu-id="a80e9-105">Power Automate triggers</span></span>

<span data-ttu-id="a80e9-106">Számos eseményindító használható ismétlődő feladatok (például értesítések vagy speciálisabb műveletek) automatizálására szolgáló munkamenetek létrehozásához.</span><span class="sxs-lookup"><span data-stu-id="a80e9-106">You can use a variety of triggers that allow you to create flows to automate repetitive tasks, such as notifications or more advanced actions.</span></span> 

- <span data-ttu-id="a80e9-107">Az adatforrás frissítésének sikertelensége esetén aktiválódó eseményindító.</span><span class="sxs-lookup"><span data-stu-id="a80e9-107">Trigger when a data source refresh fails.</span></span> 
- <span data-ttu-id="a80e9-108">Az adatforrás sikeres frissítése esetén aktiválódó eseményindító.</span><span class="sxs-lookup"><span data-stu-id="a80e9-108">Trigger when a data source refresh succeeds.</span></span>
- <span data-ttu-id="a80e9-109">Egy szegmens küszöbértékének túllépésekor aktiválódó eseményindító.</span><span class="sxs-lookup"><span data-stu-id="a80e9-109">Trigger when a threshold is crossed on a segment.</span></span> <span data-ttu-id="a80e9-110">Az eseményindító csak a küszöbérték túllépésére korlátozott.</span><span class="sxs-lookup"><span data-stu-id="a80e9-110">The trigger is limited to crossing above the threshold.</span></span>
- <span data-ttu-id="a80e9-111">Egy üzleti mérőszám küszöbértékének túllépésekor aktiválódó eseményindító.</span><span class="sxs-lookup"><span data-stu-id="a80e9-111">Trigger when a threshold is crossed on a business measure.</span></span> <span data-ttu-id="a80e9-112">Az eseményindító csak a küszöbérték túllépésére korlátozott.</span><span class="sxs-lookup"><span data-stu-id="a80e9-112">The trigger is limited crossing above the threshold.</span></span>
- <span data-ttu-id="a80e9-113">Az (adatforrások, a szegmensek, az intézkedések,...) teljes frissítésének indítása.</span><span class="sxs-lookup"><span data-stu-id="a80e9-113">Trigger when a full refresh of (data sources, segments, measures,...) is completed.</span></span>
- <span data-ttu-id="a80e9-114">Eseményindító az egyesítési folyamat (Térkép, egyeztetés, összefésülés) frissítésének befejezése után.</span><span class="sxs-lookup"><span data-stu-id="a80e9-114">Trigger when a refresh of the unification process (map, match, merge) is completed.</span></span>

<span data-ttu-id="a80e9-115">[Eseményindítók konfigurálása a Power Automate alkalmazásban](https://flow.microsoft.com/connectors/shared_customerinsights/dynamics-365-customer-insights-connector/).</span><span class="sxs-lookup"><span data-stu-id="a80e9-115">[Configure your triggers in Power Automate](https://flow.microsoft.com/connectors/shared_customerinsights/dynamics-365-customer-insights-connector/).</span></span>

## <a name="power-automate-actions"></a><span data-ttu-id="a80e9-116">Power Automate-műveletek</span><span class="sxs-lookup"><span data-stu-id="a80e9-116">Power Automate actions</span></span>
<span data-ttu-id="a80e9-117">A Power Automate-összekötő más műveleteket biztosít, mint az eseményindítók.</span><span class="sxs-lookup"><span data-stu-id="a80e9-117">The Power Automate connector provides other actions than the available triggers.</span></span> <span data-ttu-id="a80e9-118">További információ itt található: [Dynamics 365 Customer Insights Connector](https://docs.microsoft.com/connectors/customerinsights/).</span><span class="sxs-lookup"><span data-stu-id="a80e9-118">For more information, see the [Dynamics 365 Customer Insights Connector](https://docs.microsoft.com/connectors/customerinsights/).</span></span>

## <a name="create-a-power-automate-flow-in-audience-insights"></a><span data-ttu-id="a80e9-119">Power Automate-folyamat létrehozása a célközönség-információkban</span><span class="sxs-lookup"><span data-stu-id="a80e9-119">Create a Power Automate flow in audience insights</span></span>

1. <span data-ttu-id="a80e9-120">A célközönség információin belül nyissa meg a következőt: **Rendszergazda** > **Rendszer**.</span><span class="sxs-lookup"><span data-stu-id="a80e9-120">In audience insights, go to **Admin** > **System**.</span></span>

1. <span data-ttu-id="a80e9-121">A **Rendszer** oldalon válassza ki az **Állapot** lapot.</span><span class="sxs-lookup"><span data-stu-id="a80e9-121">On the **System** page, select the **Status** tab.</span></span>

1. <span data-ttu-id="a80e9-122">Az **adatforrások** területen válassza a **Folyamatok** lehetőséget, és válassza a **Folyamat létrehozása** lehetőséget a legördülő listából.</span><span class="sxs-lookup"><span data-stu-id="a80e9-122">In the **Data Sources** section, select **Flows** and select **Create a flow** from the dropdown list.</span></span>
   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="a80e9-123">![Power Automate-összekötő, amely a Folyamat létrehozása műveletet mutatja](media/power-automate-connector-create-flow.png "Power Automate-összekötő, amely a Folyamat létrehozása műveletet mutatja")</span><span class="sxs-lookup"><span data-stu-id="a80e9-123">![Power Automate connector showing Create a Flow action](media/power-automate-connector-create-flow.png "Power Automate connector showing Create a Flow action")</span></span>

1. <span data-ttu-id="a80e9-124">A Power Automate területen válassza ki az egyik elérhető eseményindítót, hogy létrehozza a kívánt folyamatot.</span><span class="sxs-lookup"><span data-stu-id="a80e9-124">In Power Automate, select one of the available triggers to create your preferred flow.</span></span> <span data-ttu-id="a80e9-125">Ha az első folyamatot hozza létre, akkor először hitelesítenie kell a Power Automate-összekötővel.</span><span class="sxs-lookup"><span data-stu-id="a80e9-125">If you're creating your first flow, you'll need to authenticate with the Power Automate connector first.</span></span>
