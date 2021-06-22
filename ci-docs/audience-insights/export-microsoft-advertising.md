---
title: A Customer Insights adatok exportálása a Microsoft Advertising-szolgáltatásba
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a Microsoft Advertising-szolgáltatásba.
ms.date: 05/12/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: c2ac92de2718cf7f0622b407bf198a7a7e50a37b
ms.sourcegitcommit: 831765a55775d358447cb7ffa56f2c3b85459084
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/01/2021
ms.locfileid: "6124501"
---
# <a name="export-segments-to-microsoft-advertising-preview"></a><span data-ttu-id="431d5-103">Szegmensek exportálása a Microsoft Advertising-szolgáltatásba (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="431d5-103">Export segments to Microsoft Advertising (preview)</span></span>

<span data-ttu-id="431d5-104">Customer Insights szegmensek exportálása a Microsoft Advertising-szolgáltatásba az Ügyfélegyezési célközönségek létrehozásához.</span><span class="sxs-lookup"><span data-stu-id="431d5-104">Export Customer Insights segments to Microsoft Advertising to create Customer Match audiences.</span></span> <span data-ttu-id="431d5-105">Használja ezeket a célközönségeket a hirdetési kampányaihoz.</span><span class="sxs-lookup"><span data-stu-id="431d5-105">Use these audiences for your ad campaigns.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="431d5-106">Előfeltételek</span><span class="sxs-lookup"><span data-stu-id="431d5-106">Prerequisites</span></span>

-   <span data-ttu-id="431d5-107">Egy [Microsoft Advertising-fiók](https://ads.microsoft.com/) és ahhoz tartozó rendszergazdai hitelesítő adatok.</span><span class="sxs-lookup"><span data-stu-id="431d5-107">An [Microsoft Advertising account](https://ads.microsoft.com/) and corresponding administrator credentials.</span></span>
-   <span data-ttu-id="431d5-108">Elfogadta az Ügyfélegyeztetés felhasználási feltételeit.</span><span class="sxs-lookup"><span data-stu-id="431d5-108">You've accepted the Customer Match terms of use.</span></span> 
-   <span data-ttu-id="431d5-109">[Konfigurált szegmenseket](segments.md) a célközönség információkban.</span><span class="sxs-lookup"><span data-stu-id="431d5-109">[Configured segments](segments.md) in audience insights.</span></span>
-   <span data-ttu-id="431d5-110">Az exportált szegmensek egységes ügyfélprofiljai egy e-mail-címmel rendelkező mezőt tartalmaznak.</span><span class="sxs-lookup"><span data-stu-id="431d5-110">Unified customer profiles in the exported segments contain a field with an email address.</span></span>

## <a name="known-limitations"></a><span data-ttu-id="431d5-111">Ismert korlátozások</span><span class="sxs-lookup"><span data-stu-id="431d5-111">Known limitations</span></span>

- <span data-ttu-id="431d5-112">Microsoft Advertising exportálásonként legfeljebb 500 ezer profil exportálható.</span><span class="sxs-lookup"><span data-stu-id="431d5-112">You can export up to 500 K profiles per export to Microsoft Advertising.</span></span>
- <span data-ttu-id="431d5-113">A Microsoft Advertising-szolgáltatásba való exportálás a szegmensekre korlátozódik.</span><span class="sxs-lookup"><span data-stu-id="431d5-113">Exporting to Microsoft Advertising is limited to segments.</span></span>
- <span data-ttu-id="431d5-114">500 ezer profil exportálása a Microsoft Advertising alkalmazásba akár 10 percet is igénybe vehet.</span><span class="sxs-lookup"><span data-stu-id="431d5-114">Exporting up to 500 K profiles to Microsoft Advertising can take up to 10 minutes to complete.</span></span> 


## <a name="set-up-the-connection-to-microsoft-advertising"></a><span data-ttu-id="431d5-115">Állítsa be a Microsoft Advertising-szolgáltatással való kapcsolatot</span><span class="sxs-lookup"><span data-stu-id="431d5-115">Set up the connection to Microsoft Advertising</span></span>

1. <span data-ttu-id="431d5-116">Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="431d5-116">Go to **Admin** > **Connections**.</span></span>

1. <span data-ttu-id="431d5-117">Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza a **Microsoft Advertising** lehetőséget a kapcsolat konfigurálásához.</span><span class="sxs-lookup"><span data-stu-id="431d5-117">Select **Add connection** and choose **Microsoft Advertising** to configure the connection.</span></span>

1. <span data-ttu-id="431d5-118">Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak.</span><span class="sxs-lookup"><span data-stu-id="431d5-118">Give your connection a recognizable name in the **Display name** field.</span></span> <span data-ttu-id="431d5-119">A név és a kapcsolat típusa írja le ezt a kapcsolatot.</span><span class="sxs-lookup"><span data-stu-id="431d5-119">The name and the type of the connection describe this connection.</span></span> <span data-ttu-id="431d5-120">Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.</span><span class="sxs-lookup"><span data-stu-id="431d5-120">We recommend choosing a name that explains the purpose and target of the connection.</span></span>

1. <span data-ttu-id="431d5-121">A kapcsolat használóinak kiválasztása.</span><span class="sxs-lookup"><span data-stu-id="431d5-121">Choose who can use this connection.</span></span> <span data-ttu-id="431d5-122">Az alapértelmezett a rendszergazdák.</span><span class="sxs-lookup"><span data-stu-id="431d5-122">The default is administrators.</span></span> <span data-ttu-id="431d5-123">További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).</span><span class="sxs-lookup"><span data-stu-id="431d5-123">For more information, see [Allow contributors to use a connection for exports](connections.md#allow-contributors-to-use-a-connection-for-exports).</span></span>

1. <span data-ttu-id="431d5-124">Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.</span><span class="sxs-lookup"><span data-stu-id="431d5-124">Select **I agree** to confirm the **Data privacy and compliance**.</span></span>

1. <span data-ttu-id="431d5-125">Válassza a **Kapcsolat** lehetőséget az Microsoft Advertising kapcsolatának inicializálására.</span><span class="sxs-lookup"><span data-stu-id="431d5-125">Select **Connect** to initialize the connection to Microsoft Advertising.</span></span>

1. <span data-ttu-id="431d5-126">Válassza a **Hitelesítés a Microsoft Advertising alkalmazással** lehetőséget, és adja meg a Microsoft Advertising rendszergazdai hitelesítő adatait.</span><span class="sxs-lookup"><span data-stu-id="431d5-126">Select **Authenticate with Microsoft Advertising** and provide your admin credentials for Microsoft Advertising.</span></span>

1. <span data-ttu-id="431d5-127">Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.</span><span class="sxs-lookup"><span data-stu-id="431d5-127">Select **Add yourself as export user** and provide your Customer Insights credentials.</span></span>

1. <span data-ttu-id="431d5-128">A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="431d5-128">Select **Save** to complete the connection.</span></span>

## <a name="configure-an-export"></a><span data-ttu-id="431d5-129">Exportálás konfigurálása</span><span class="sxs-lookup"><span data-stu-id="431d5-129">Configure an export</span></span>

<span data-ttu-id="431d5-130">Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz.</span><span class="sxs-lookup"><span data-stu-id="431d5-130">You can configure this export if you have access to a connection of this type.</span></span> <span data-ttu-id="431d5-131">További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).</span><span class="sxs-lookup"><span data-stu-id="431d5-131">For more information, see [Permissions needed to configure an export](export-destinations.md#set-up-a-new-export).</span></span>

1. <span data-ttu-id="431d5-132">Menjen az **Adatok** > **Exportálások** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="431d5-132">Go to **Data** > **Exports**.</span></span>

1. <span data-ttu-id="431d5-133">Új exportálás létrehozásához válassza a **Célhely hozzáadása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="431d5-133">To create a new export, select **Add destination**.</span></span>

1. <span data-ttu-id="431d5-134">A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot a Microsoft Advertising szakaszból.</span><span class="sxs-lookup"><span data-stu-id="431d5-134">In the **Connection for export** field, choose a connection from the Microsoft Advertising section.</span></span> <span data-ttu-id="431d5-135">Ha nem látja ezt a szakasznevet, az Ön számára nincs ilyen típusú kapcsolat.</span><span class="sxs-lookup"><span data-stu-id="431d5-135">If you don't see this section name, there are no connections of this type available to you.</span></span>

1. <span data-ttu-id="431d5-136">Válassza ki az exportálni kívánt szegmenseket.</span><span class="sxs-lookup"><span data-stu-id="431d5-136">Select the segments to export.</span></span> <span data-ttu-id="431d5-137">A Microsoft Advertising ügyfélegyeztetés célközönségei automatikusan létrejönnek az exportálásra kiválasztott szegmensek nevével.</span><span class="sxs-lookup"><span data-stu-id="431d5-137">The Customer Match audiences in Microsoft Advertising are automatically created with the name of the segments selected for export.</span></span> <span data-ttu-id="431d5-138">Minden szegmens külön ügyfélegyeztetési célközönséget eredményez.</span><span class="sxs-lookup"><span data-stu-id="431d5-138">Each segment will result in a separate Customer Match audience.</span></span> 

1. <span data-ttu-id="431d5-139">Adja meg a **Microsoft Advertising ügyfélazonosítóját és fiókazonosítóját**.</span><span class="sxs-lookup"><span data-stu-id="431d5-139">Enter your **Microsoft Advertising Customer ID and Account ID**.</span></span> <span data-ttu-id="431d5-140">Az Ügyfélazonosítót (`cid`) és a Fiókazonosítót (`aid`) az URL-cím paramétereiben találja, amikor bejelentkezett a Microsoft Advertising-szolgáltatásba.</span><span class="sxs-lookup"><span data-stu-id="431d5-140">You can find the Customer ID (`cid`) and Account ID (`aid`) in the parameters of the URL when you're signed in Microsoft Advertising.</span></span>

1. <span data-ttu-id="431d5-141">Az **Adategyeztetés** szakaszban, az **E-mail** mezőben válassza ki az egységes ügyfélprofil mezőjét az ügyfél e-mail-címével.</span><span class="sxs-lookup"><span data-stu-id="431d5-141">In the **Data matching** section, in the **Email** field, select the field in your unified customer profile with a customer's email address.</span></span> <span data-ttu-id="431d5-142">A szegmenseket exportálni kell a Microsoft Advertising alkalmazásba.</span><span class="sxs-lookup"><span data-stu-id="431d5-142">It's required to export segments to Microsoft Advertising.</span></span>

1. <span data-ttu-id="431d5-143">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="431d5-143">Select **Save**.</span></span>

<span data-ttu-id="431d5-144">Az exportálás mentése nem futtatja azonnal az exportálást.</span><span class="sxs-lookup"><span data-stu-id="431d5-144">Saving an export doesn't run the export immediately.</span></span>

<span data-ttu-id="431d5-145">Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut.</span><span class="sxs-lookup"><span data-stu-id="431d5-145">The export runs with every [scheduled refresh](system.md#schedule-tab).</span></span> <span data-ttu-id="431d5-146">Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand).</span><span class="sxs-lookup"><span data-stu-id="431d5-146">You can also [export data on demand](export-destinations.md#run-exports-on-demand).</span></span> 


## <a name="data-privacy-and-compliance"></a><span data-ttu-id="431d5-147">Adatvédelem és megfelelőség</span><span class="sxs-lookup"><span data-stu-id="431d5-147">Data privacy and compliance</span></span>

<span data-ttu-id="431d5-148">Amikor engedélyezi Dynamics 365 Customer Insights számára, hogy adatokat továbbítson a Microsoft Advertising számára, akkor lehetővé teszi az adatok továbbítását a Dynamics 365 Customer Insights megfelelési határán kívülre is, beleértve az esetlegesen bizalmas adatokat is, például a Személyes adatokat.</span><span class="sxs-lookup"><span data-stu-id="431d5-148">When you enable Dynamics 365 Customer Insights to transmit data to Microsoft Advertising, you allow transfer of data outside of the compliance boundary for Dynamics 365 Customer Insights, including potentially sensitive data such as Personal Data.</span></span> <span data-ttu-id="431d5-149">A Microsoft az Ön utasítására továbbítja az adatokat, de Ön a felelős azért, hogy a Microsoft Advertising megfeleljen az esetleges adatvédelmi vagy biztonsági kötelezettségeknek.</span><span class="sxs-lookup"><span data-stu-id="431d5-149">Microsoft will transfer such data at your instruction, but you are responsible for ensuring that Microsoft Advertising meets any privacy or security obligations you may have.</span></span> <span data-ttu-id="431d5-150">További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).</span><span class="sxs-lookup"><span data-stu-id="431d5-150">For more information, see [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?linkid=396732).</span></span>

<span data-ttu-id="431d5-151">A funkció használatának leállítása érdekében az Ön Dynamics 365 Customer Insights rendszergazdája bármikor eltávolíthatja ezt az exportálási célhelyet.</span><span class="sxs-lookup"><span data-stu-id="431d5-151">Your Dynamics 365 Customer Insights Administrator can remove this export destination at any time to stop use of this functionality.</span></span>
