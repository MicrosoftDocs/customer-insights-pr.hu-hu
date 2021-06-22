---
title: Customer Insights-adatok exportálása a Campaign Monitorra
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a Campaign Monitorba.
ms.date: 03/03/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 091a3197dc0c19ff78f0419fb4e88868e0f78359
ms.sourcegitcommit: 831765a55775d358447cb7ffa56f2c3b85459084
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/01/2021
ms.locfileid: "6124184"
---
# <a name="export-segments-to-campaign-monitor-preview"></a><span data-ttu-id="8bb78-103">Szegmensek exportálása a Campaign Monitorba (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="8bb78-103">Export segments to Campaign Monitor (preview)</span></span>

<span data-ttu-id="8bb78-104">Exportálja az egyesített ügyfélprofilok szegmensét a Campaign Monitorba, és használja őket marketing-tevékenységekre.</span><span class="sxs-lookup"><span data-stu-id="8bb78-104">Export segments of unified customer profiles to Campaign Monitor and use them for marketing activities.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8bb78-105">Előfeltételek</span><span class="sxs-lookup"><span data-stu-id="8bb78-105">Prerequisites</span></span>

-   <span data-ttu-id="8bb78-106">Van egy [Campaign Monitor fiókja](https://www.campaignmonitor.com/) és ahhoz tartozó rendszergazdai hitelesítő adatai.</span><span class="sxs-lookup"><span data-stu-id="8bb78-106">You have an [Campaign Monitor account](https://www.campaignmonitor.com/) and corresponding administrator credentials.</span></span>
-   <span data-ttu-id="8bb78-107">[Konfigurált szegmensekkel](segments.md) rendelkezik a célközönségi-információkban.</span><span class="sxs-lookup"><span data-stu-id="8bb78-107">You have [configured segments](segments.md) in audience insights.</span></span>
-   <span data-ttu-id="8bb78-108">Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.</span><span class="sxs-lookup"><span data-stu-id="8bb78-108">Unified customer profiles in the exported segments contain a field representing an email address.</span></span>

## <a name="known-limitations"></a><span data-ttu-id="8bb78-109">Ismert korlátozások</span><span class="sxs-lookup"><span data-stu-id="8bb78-109">Known limitations</span></span>

- <span data-ttu-id="8bb78-110">A Campaign Monitorba exportálásonként legfeljebb 1 millió profil exportálható.</span><span class="sxs-lookup"><span data-stu-id="8bb78-110">You can export up to 1 million profiles per export to Campaign Monitor.</span></span>
- <span data-ttu-id="8bb78-111">A Campaign Monitorba való exportálás a szegmensekre korlátozódik.</span><span class="sxs-lookup"><span data-stu-id="8bb78-111">Exporting to Campaign Monitor is limited to segments.</span></span>
- <span data-ttu-id="8bb78-112">1 millió profil exportálása a Campaign Monitor alkalmazásba akár 20 percet is igénybe vehet.</span><span class="sxs-lookup"><span data-stu-id="8bb78-112">Exporting up to 1 million profiles to Campaign Monitor can take up to 20 minutes to complete.</span></span> 
- <span data-ttu-id="8bb78-113">A Campaign Monitorba exportálható profilok száma a Campaign Monitorral kötött szerződéstől függ és az korlátozza.</span><span class="sxs-lookup"><span data-stu-id="8bb78-113">The number of profiles that you can export to Campaign Monitor is dependent and limited on your contract with Campaign Monitor.</span></span>

## <a name="set-up-connection-to-campaign-monitor"></a><span data-ttu-id="8bb78-114">Kapcsolat beállítása a Campaign Monitor alkalmazáshoz</span><span class="sxs-lookup"><span data-stu-id="8bb78-114">Set up connection to Campaign Monitor</span></span>

1. <span data-ttu-id="8bb78-115">Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="8bb78-115">Go to **Admin** > **Connections**.</span></span>

1. <span data-ttu-id="8bb78-116">Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza a **Campaign Monitor** lehetőséget a kapcsolat konfigurálásához.</span><span class="sxs-lookup"><span data-stu-id="8bb78-116">Select **Add connection** and choose **Campaign Monitor** to configure the connection.</span></span>

1. <span data-ttu-id="8bb78-117">Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak.</span><span class="sxs-lookup"><span data-stu-id="8bb78-117">Give your connection a recognizable name in the **Display name** field.</span></span> <span data-ttu-id="8bb78-118">A név és a kapcsolat típusa írja le ezt a kapcsolatot.</span><span class="sxs-lookup"><span data-stu-id="8bb78-118">The name and the type of the connection describe this connection.</span></span> <span data-ttu-id="8bb78-119">Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.</span><span class="sxs-lookup"><span data-stu-id="8bb78-119">We recommend choosing a name that explains the purpose and target of the connection.</span></span>

1. <span data-ttu-id="8bb78-120">A kapcsolat használóinak kiválasztása.</span><span class="sxs-lookup"><span data-stu-id="8bb78-120">Choose who can use this connection.</span></span> <span data-ttu-id="8bb78-121">Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz.</span><span class="sxs-lookup"><span data-stu-id="8bb78-121">If you take no action, the default will be Administrators.</span></span> <span data-ttu-id="8bb78-122">További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).</span><span class="sxs-lookup"><span data-stu-id="8bb78-122">For more information, see [Allow contributors to use a connection for exports](connections.md#allow-contributors-to-use-a-connection-for-exports).</span></span>

1. <span data-ttu-id="8bb78-123">Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.</span><span class="sxs-lookup"><span data-stu-id="8bb78-123">Select **I agree** to confirm the **Data privacy and compliance**.</span></span>

1. <span data-ttu-id="8bb78-124">Válassza a **Kapcsolat** lehetőséget a Campaign Monitor kapcsolatának inicializálására.</span><span class="sxs-lookup"><span data-stu-id="8bb78-124">Select **Connect** to initialize the connection to Campaign Monitor.</span></span>

1. <span data-ttu-id="8bb78-125">Válassza a **Hitelesítés a Campaign Monitorral** lehetőséget, és adja meg a Campaign Monitor rendszergazdai hitelesítő adatait.</span><span class="sxs-lookup"><span data-stu-id="8bb78-125">Select **Authenticate with Campaign Monitor** and provide your admin credentials for Campaign Monitor.</span></span>

1. <span data-ttu-id="8bb78-126">Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.</span><span class="sxs-lookup"><span data-stu-id="8bb78-126">Select **Add yourself as export user** and provide your Customer Insights credentials.</span></span>

1. <span data-ttu-id="8bb78-127">A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="8bb78-127">Select **Save** to complete the connection.</span></span>

## <a name="configure-an-export"></a><span data-ttu-id="8bb78-128">Exportálás konfigurálása</span><span class="sxs-lookup"><span data-stu-id="8bb78-128">Configure an export</span></span>

<span data-ttu-id="8bb78-129">Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz.</span><span class="sxs-lookup"><span data-stu-id="8bb78-129">You can configure this export if you have access to a connection of this type.</span></span> <span data-ttu-id="8bb78-130">További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).</span><span class="sxs-lookup"><span data-stu-id="8bb78-130">For more information, see [Permissions needed to configure an export](export-destinations.md#set-up-a-new-export).</span></span>

1. <span data-ttu-id="8bb78-131">Menjen az **Adatok** > **Exportálások** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="8bb78-131">Go to **Data** > **Exports**.</span></span>

1. <span data-ttu-id="8bb78-132">Új exportálás létrehozásához válassza a **Célhely hozzáadása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="8bb78-132">To create a new export, select **Add destination**.</span></span>

1. <span data-ttu-id="8bb78-133">A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot a Campaign Monitor szakaszból.</span><span class="sxs-lookup"><span data-stu-id="8bb78-133">In the **Connection for export** field, choose a connection from the Campaign Monitor section.</span></span> <span data-ttu-id="8bb78-134">Ha nem látja ezt a szakasznevet, az Ön számára nincs ilyen típusú kapcsolat.</span><span class="sxs-lookup"><span data-stu-id="8bb78-134">If you don't see this section name, there are no connections of this type available to you.</span></span>

1. <span data-ttu-id="8bb78-135">Adja meg a [**Campaign Monitor listaazonosítóját**](https://www.campaignmonitor.com/api/getting-started/#your-list-id).</span><span class="sxs-lookup"><span data-stu-id="8bb78-135">Enter your [**Campaign Monitor List ID**](https://www.campaignmonitor.com/api/getting-started/#your-list-id).</span></span>    
   <span data-ttu-id="8bb78-136">[Hozza létre az API-kulcsot](https://www.campaignmonitor.com/api/getting-started/) a Campaign Monitor **Fiókbeállításokból**, és először tekintse meg az API-lista azonosítóját.</span><span class="sxs-lookup"><span data-stu-id="8bb78-136">[Generate the API key](https://www.campaignmonitor.com/api/getting-started/) from **Account Settings** in Campaign Monitor first to view the API list ID.</span></span>  

3. <span data-ttu-id="8bb78-137">Az **Adategyeztetés** szakaszban az **E-mail** mezőben jelölje ki az egyesített ügyfélprofil ügyfél e-mail-címét jelképező mezőjét.</span><span class="sxs-lookup"><span data-stu-id="8bb78-137">In the **Data matching** section, in the **Email** field, select the field in your unified customer profile that represents a customer's email address.</span></span> <span data-ttu-id="8bb78-138">A szegmenseket exportálni kell a Campaign Monitor alkalmazásba.</span><span class="sxs-lookup"><span data-stu-id="8bb78-138">It's required to export segments to Campaign Monitor.</span></span>

1. <span data-ttu-id="8bb78-139">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="8bb78-139">Select **Save**.</span></span>

<span data-ttu-id="8bb78-140">Az exportálás mentése nem futtatja azonnal az exportálást.</span><span class="sxs-lookup"><span data-stu-id="8bb78-140">Saving an export doesn't run the export immediately.</span></span>

<span data-ttu-id="8bb78-141">Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut.</span><span class="sxs-lookup"><span data-stu-id="8bb78-141">The export runs with every [scheduled refresh](system.md#schedule-tab).</span></span> <span data-ttu-id="8bb78-142">Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand).</span><span class="sxs-lookup"><span data-stu-id="8bb78-142">You can also [export data on demand](export-destinations.md#run-exports-on-demand).</span></span> 


## <a name="data-privacy-and-compliance"></a><span data-ttu-id="8bb78-143">Adatvédelem és megfelelőség</span><span class="sxs-lookup"><span data-stu-id="8bb78-143">Data privacy and compliance</span></span>

<span data-ttu-id="8bb78-144">Amikor engedélyezi Dynamics 365 Customer Insightst, hogy adatokat továbbítson a Campaign Monitornak, akkor lehetővé teszi az adatok továbbítását a Dynamics 365 Customer Insights megfelelési határán kívülre is, beleértve az esetlegesen bizalmas adatokat is, például a Személyes adatokat.</span><span class="sxs-lookup"><span data-stu-id="8bb78-144">When you enable Dynamics 365 Customer Insights to transmit data to Campaign Monitor, you allow transfer of data outside of the compliance boundary for Dynamics 365 Customer Insights, including potentially sensitive data such as Personal Data.</span></span> <span data-ttu-id="8bb78-145">A Microsoft az Ön utasítására továbbítja az adatokat, de Ön a felelős azért, hogy a Campaign Monitor megfeleljen az esetleges adatvédelmi vagy biztonsági kötelezettségeknek.</span><span class="sxs-lookup"><span data-stu-id="8bb78-145">Microsoft will transfer such data at your instruction, but you are responsible for ensuring that Campaign Monitor meets any privacy or security obligations you may have.</span></span> <span data-ttu-id="8bb78-146">További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).</span><span class="sxs-lookup"><span data-stu-id="8bb78-146">For more information, see [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?linkid=396732).</span></span>

<span data-ttu-id="8bb78-147">A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.</span><span class="sxs-lookup"><span data-stu-id="8bb78-147">Your Dynamics 365 Customer Insights Administrator can remove this export destination at any time to discontinue use of this functionality.</span></span>
