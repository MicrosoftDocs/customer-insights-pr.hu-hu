---
title: Customer Insights-adatok exportálása az Ominsend-szolgáltatásba
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja az Ominsendbe.
ms.date: 05/21/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 8bd692819fa8451ded5e74191ee717f81f87425d
ms.sourcegitcommit: 831765a55775d358447cb7ffa56f2c3b85459084
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/01/2021
ms.locfileid: "6124502"
---
# <a name="export-segments-to-omnisend-preview"></a><span data-ttu-id="f0628-103">Szegmensek exportálása az Ominsendbe (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="f0628-103">Export segments to Omnisend (preview)</span></span>

<span data-ttu-id="f0628-104">Exportálja az egyesített ügyfélprofilok szegmensét az Ominsendbe, és használja őket marketing-tevékenységekre.</span><span class="sxs-lookup"><span data-stu-id="f0628-104">Export segments of unified customer profiles to Omnisend and use them for marketing activities.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f0628-105">Előfeltételek</span><span class="sxs-lookup"><span data-stu-id="f0628-105">Prerequisites</span></span>

-   <span data-ttu-id="f0628-106">Van egy [Ominsend fiókja](https://www.omnisend.com/) és ahhoz tartozó rendszergazdai hitelesítő adatai.</span><span class="sxs-lookup"><span data-stu-id="f0628-106">You have an [Omnisend account](https://www.omnisend.com/) and corresponding administrator credentials.</span></span>
-   <span data-ttu-id="f0628-107">[Konfigurált szegmensekkel](segments.md) rendelkezik a célközönségi-információkban.</span><span class="sxs-lookup"><span data-stu-id="f0628-107">You have [configured segments](segments.md) in audience insights.</span></span>
-   <span data-ttu-id="f0628-108">Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.</span><span class="sxs-lookup"><span data-stu-id="f0628-108">Unified customer profiles in the exported segments contain a field representing an email address.</span></span>

## <a name="known-limitations"></a><span data-ttu-id="f0628-109">Ismert korlátozások</span><span class="sxs-lookup"><span data-stu-id="f0628-109">Known limitations</span></span>

- <span data-ttu-id="f0628-110">Az Omnisendbe exportálhat exportálásonként akár 1 millió profilt, és ez akár 4 órát is igénybe vehet.</span><span class="sxs-lookup"><span data-stu-id="f0628-110">You can export up to 1 million profiles per export to Omnisend and it can take up to 4 hours to complete.</span></span>
- <span data-ttu-id="f0628-111">Az Ominsendbe való exportálás a szegmensekre korlátozódik.</span><span class="sxs-lookup"><span data-stu-id="f0628-111">Exporting to Omnisend is limited to segments.</span></span>
- <span data-ttu-id="f0628-112">Az Omnisendbe exportálható profilok száma az Omnisenddel kötött szerződésétől függ.</span><span class="sxs-lookup"><span data-stu-id="f0628-112">The number of profiles that you can export to Omnisend depends on your contract with Omnisend.</span></span>

## <a name="set-up-connection-to-omnisend"></a><span data-ttu-id="f0628-113">Állítsa be az Ominsenddel való kapcsolatot</span><span class="sxs-lookup"><span data-stu-id="f0628-113">Set up connection to Omnisend</span></span>

1. <span data-ttu-id="f0628-114">Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="f0628-114">Go to **Admin** > **Connections**.</span></span>

1. <span data-ttu-id="f0628-115">Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza az **Ominsend** lehetőséget a kapcsolat konfigurálásához.</span><span class="sxs-lookup"><span data-stu-id="f0628-115">Select **Add connection** and choose **Omnisend** to configure the connection.</span></span>

1. <span data-ttu-id="f0628-116">Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak.</span><span class="sxs-lookup"><span data-stu-id="f0628-116">Give your connection a recognizable name in the **Display name** field.</span></span> <span data-ttu-id="f0628-117">A név és a kapcsolat típusa írja le ezt a kapcsolatot.</span><span class="sxs-lookup"><span data-stu-id="f0628-117">The name and the type of the connection describe this connection.</span></span> <span data-ttu-id="f0628-118">Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.</span><span class="sxs-lookup"><span data-stu-id="f0628-118">We recommend choosing a name that explains the purpose and target of the connection.</span></span>

1. <span data-ttu-id="f0628-119">A kapcsolat használóinak kiválasztása.</span><span class="sxs-lookup"><span data-stu-id="f0628-119">Choose who can use this connection.</span></span> <span data-ttu-id="f0628-120">Alapértelmezés szerint csak a rendszergazdák.</span><span class="sxs-lookup"><span data-stu-id="f0628-120">By default it's only administrators.</span></span> <span data-ttu-id="f0628-121">További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).</span><span class="sxs-lookup"><span data-stu-id="f0628-121">For more information, see [Allow contributors to use a connection for exports](connections.md#allow-contributors-to-use-a-connection-for-exports).</span></span>

1. <span data-ttu-id="f0628-122">Adja meg az [Ominsend API-kulcsát](https://support.omnisend.com/en/articles/1061890-generating-api-key).</span><span class="sxs-lookup"><span data-stu-id="f0628-122">Enter your [Omnisend API key](https://support.omnisend.com/en/articles/1061890-generating-api-key).</span></span>

1. <span data-ttu-id="f0628-123">Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.</span><span class="sxs-lookup"><span data-stu-id="f0628-123">Select **I agree** to confirm the **Data privacy and compliance**.</span></span>

1. <span data-ttu-id="f0628-124">Válassza a **Kapcsolat** lehetőséget az Ominsend kapcsolatának inicializálására.</span><span class="sxs-lookup"><span data-stu-id="f0628-124">Select **Connect** to initialize the connection to Omnisend.</span></span>

1. <span data-ttu-id="f0628-125">Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.</span><span class="sxs-lookup"><span data-stu-id="f0628-125">Select **Add yourself as export user** and provide your Customer Insights credentials.</span></span>

1. <span data-ttu-id="f0628-126">A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="f0628-126">Select **Save** to complete the connection.</span></span>

## <a name="configure-an-export"></a><span data-ttu-id="f0628-127">Exportálás konfigurálása</span><span class="sxs-lookup"><span data-stu-id="f0628-127">Configure an export</span></span>

<span data-ttu-id="f0628-128">Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz.</span><span class="sxs-lookup"><span data-stu-id="f0628-128">You can configure this export if you have access to a connection of this type.</span></span> <span data-ttu-id="f0628-129">További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).</span><span class="sxs-lookup"><span data-stu-id="f0628-129">For more information, see [Permissions needed to configure an export](export-destinations.md#set-up-a-new-export).</span></span>

1. <span data-ttu-id="f0628-130">Menjen az **Adatok** > **Exportálások** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="f0628-130">Go to **Data** > **Exports**.</span></span>

1. <span data-ttu-id="f0628-131">Új exportálás létrehozásához válassza a **Célhely hozzáadása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="f0628-131">To create a new export, select **Add destination**.</span></span>

1. <span data-ttu-id="f0628-132">A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot az Ominsend szakaszból.</span><span class="sxs-lookup"><span data-stu-id="f0628-132">In the **Connection for export** field, choose a connection from the Omnisend section.</span></span> <span data-ttu-id="f0628-133">Ha nem látja ezt a szakasznevet, az Ön számára nincs ilyen típusú kapcsolat.</span><span class="sxs-lookup"><span data-stu-id="f0628-133">If you don't see this section name, there are no connections of this type available to you.</span></span>

1. <span data-ttu-id="f0628-134">Az **Adategyeztetés** szakaszban az **E-mail** mezőben jelölje ki az egyesített ügyfélprofil ügyfél e-mail-címét jelképező mezőjét.</span><span class="sxs-lookup"><span data-stu-id="f0628-134">In the **Data matching** section, in the **Email** field, select the field in your unified customer profile that represents a customer's email address.</span></span> <span data-ttu-id="f0628-135">A szegmenseket exportálni kell az Ominsendbe.</span><span class="sxs-lookup"><span data-stu-id="f0628-135">It's required to export segments to Omnisend.</span></span> <span data-ttu-id="f0628-136">Tetszés szerint exportálhatja az Utónév, Vezetéknév, Cím, Ország/Régió, Állam, Város és Irányítószám lehetőségeket, hogy személyre szabottabb e-maileket hozzon létre.</span><span class="sxs-lookup"><span data-stu-id="f0628-136">Optionally, you can export First name, Last name, Address, Country/Region, State, City, and Post Code to create more personalized emails.</span></span> <span data-ttu-id="f0628-137">Válassza az **Attribútum hozzáadása** lehetőséget a mezők leképezéséhez.</span><span class="sxs-lookup"><span data-stu-id="f0628-137">Select **Add attribute** to map these fields.</span></span>

1. <span data-ttu-id="f0628-138">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="f0628-138">Select **Save**.</span></span>

<span data-ttu-id="f0628-139">Az exportálás mentése nem futtatja azonnal az exportálást.</span><span class="sxs-lookup"><span data-stu-id="f0628-139">Saving an export doesn't run the export immediately.</span></span>

<span data-ttu-id="f0628-140">Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut.</span><span class="sxs-lookup"><span data-stu-id="f0628-140">The export runs with every [scheduled refresh](system.md#schedule-tab).</span></span> <span data-ttu-id="f0628-141">Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand).</span><span class="sxs-lookup"><span data-stu-id="f0628-141">You can also [export data on demand](export-destinations.md#run-exports-on-demand).</span></span> 


## <a name="data-privacy-and-compliance"></a><span data-ttu-id="f0628-142">Adatvédelem és megfelelőség</span><span class="sxs-lookup"><span data-stu-id="f0628-142">Data privacy and compliance</span></span>

<span data-ttu-id="f0628-143">Amikor engedélyezi Dynamics 365 Customer Insights számára, hogy adatokat továbbítson az Ominsendnek, akkor lehetővé teszi az adatok továbbítását a Dynamics 365 Customer Insights megfelelési határán kívülre is, beleértve az esetlegesen bizalmas adatokat is, például a Személyes adatokat.</span><span class="sxs-lookup"><span data-stu-id="f0628-143">When you enable Dynamics 365 Customer Insights to transmit data to Ommisend, you allow transfer of data outside of the compliance boundary for Dynamics 365 Customer Insights, including potentially sensitive data such as Personal Data.</span></span> <span data-ttu-id="f0628-144">A Microsoft az Ön utasítására továbbítja az adatokat, de Ön a felelős azért, hogy az Ominsend megfeleljen az esetleges adatvédelmi vagy biztonsági kötelezettségeknek.</span><span class="sxs-lookup"><span data-stu-id="f0628-144">Microsoft will transfer such data at your instruction, but you are responsible for ensuring that Omnisend meets any privacy or security obligations you may have.</span></span> <span data-ttu-id="f0628-145">További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).</span><span class="sxs-lookup"><span data-stu-id="f0628-145">For more information, see [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?linkid=396732).</span></span>

<span data-ttu-id="f0628-146">A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.</span><span class="sxs-lookup"><span data-stu-id="f0628-146">Your Dynamics 365 Customer Insights administrator can remove this export destination at any time to discontinue use of this functionality.</span></span>
