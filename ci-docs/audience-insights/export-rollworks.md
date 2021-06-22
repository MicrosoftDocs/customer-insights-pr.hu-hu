---
title: Customer Insights-adatok exportálása a RollWorksra
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a RollWorksba.
ms.date: 03/03/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: dce5d51ca4587b4d7a0644cc701c1826854882b5
ms.sourcegitcommit: 831765a55775d358447cb7ffa56f2c3b85459084
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/01/2021
ms.locfileid: "6124092"
---
# <a name="export-segments-to-rollworks-preview"></a><span data-ttu-id="fe984-103">Szegmensek exportálása a RollWorksba (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="fe984-103">Export segments to RollWorks (preview)</span></span>

<span data-ttu-id="fe984-104">Exportálja az egyesített ügyfélprofilok szegmensét a RollWorksba, és használja őket hirdetési célokra.</span><span class="sxs-lookup"><span data-stu-id="fe984-104">Export segments of unified customer profiles to RollWorks and use them for advertising.</span></span> 

## <a name="prerequisites-for-a-connection"></a><span data-ttu-id="fe984-105">Egy kapcsolat előfeltételei</span><span class="sxs-lookup"><span data-stu-id="fe984-105">Prerequisites for a connection</span></span>

-   <span data-ttu-id="fe984-106">Van egy [RollWorks fiókja](https://www.rollworks.com/) és ahhoz tartozó rendszergazdai hitelesítő adatai.</span><span class="sxs-lookup"><span data-stu-id="fe984-106">You have an [RollWorks account](https://www.rollworks.com/) and corresponding administrator credentials.</span></span>
-   <span data-ttu-id="fe984-107">[Konfigurált szegmensekkel](segments.md) rendelkezik a célközönségi-információkban.</span><span class="sxs-lookup"><span data-stu-id="fe984-107">You have [configured segments](segments.md) in audience insights.</span></span>
-   <span data-ttu-id="fe984-108">Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.</span><span class="sxs-lookup"><span data-stu-id="fe984-108">Unified customer profiles in the exported segments contain a field representing an email address.</span></span>

## <a name="known-limitations"></a><span data-ttu-id="fe984-109">Ismert korlátozások</span><span class="sxs-lookup"><span data-stu-id="fe984-109">Known limitations</span></span>

- <span data-ttu-id="fe984-110">A RollWorks exportálásonként legfeljebb 250 000 profil exportálható.</span><span class="sxs-lookup"><span data-stu-id="fe984-110">You can export up to 250'000 profiles in per export to RollWorks.</span></span>
- <span data-ttu-id="fe984-111">A 100-nál kevesebb profillal rendelkező szegmensek nem exportálhatók a RollWorksba.</span><span class="sxs-lookup"><span data-stu-id="fe984-111">You can't export segments with fewer than 100 profiles to RollWorks.</span></span> 
- <span data-ttu-id="fe984-112">A RollWorksba való exportálás a szegmensekre korlátozódik.</span><span class="sxs-lookup"><span data-stu-id="fe984-112">Exporting to RollWorks is limited to segments.</span></span>
- <span data-ttu-id="fe984-113">250 000 profil exportálása a RollWorks alkalmazásba akár 10 percet is igénybe vehet.</span><span class="sxs-lookup"><span data-stu-id="fe984-113">Exporting up to 250'000 profiles to RollWorks can take up to 10 minutes to complete.</span></span> 
- <span data-ttu-id="fe984-114">A RollWorksba exportálható profilok száma a RollWorksszal kötött szerződéstől függ és az korlátozza.</span><span class="sxs-lookup"><span data-stu-id="fe984-114">The number of profiles that you can export to RollWorks is dependent and limited on your contract with RollWorks.</span></span>

## <a name="set-up-connection-to-rollworks"></a><span data-ttu-id="fe984-115">Állítsa be a RollWorksszal való kapcsolatot</span><span class="sxs-lookup"><span data-stu-id="fe984-115">Set up connection to RollWorks</span></span>

1. <span data-ttu-id="fe984-116">Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="fe984-116">Go to **Admin** > **Connections**.</span></span>

1. <span data-ttu-id="fe984-117">Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza a **RollWorks** lehetőséget a kapcsolat konfigurálásához.</span><span class="sxs-lookup"><span data-stu-id="fe984-117">Select **Add connection** and choose **RollWorks** to configure the connection.</span></span>

1. <span data-ttu-id="fe984-118">Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak.</span><span class="sxs-lookup"><span data-stu-id="fe984-118">Give your connection a recognizable name in the **Display name** field.</span></span> <span data-ttu-id="fe984-119">A név és a kapcsolat típusa írja le ezt a kapcsolatot.</span><span class="sxs-lookup"><span data-stu-id="fe984-119">The name and the type of the connection describe this connection.</span></span> <span data-ttu-id="fe984-120">Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.</span><span class="sxs-lookup"><span data-stu-id="fe984-120">We recommend choosing a name that explains the purpose and target of the connection.</span></span>

1. <span data-ttu-id="fe984-121">A kapcsolat használóinak kiválasztása.</span><span class="sxs-lookup"><span data-stu-id="fe984-121">Choose who can use this connection.</span></span> <span data-ttu-id="fe984-122">Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz.</span><span class="sxs-lookup"><span data-stu-id="fe984-122">If you take no action, the default will be Administrators.</span></span> <span data-ttu-id="fe984-123">További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).</span><span class="sxs-lookup"><span data-stu-id="fe984-123">For more information, see [Allow contributors to use a connection for exports](connections.md#allow-contributors-to-use-a-connection-for-exports).</span></span>

1. <span data-ttu-id="fe984-124">Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.</span><span class="sxs-lookup"><span data-stu-id="fe984-124">Select **I agree** to confirm the **Data privacy and compliance**.</span></span>

1. <span data-ttu-id="fe984-125">Válassza a **Kapcsolat** lehetőséget a RollWorks kapcsolatának inicializálására.</span><span class="sxs-lookup"><span data-stu-id="fe984-125">Select **Connect** to initialize the connection to RollWorks.</span></span>

1. <span data-ttu-id="fe984-126">Válassza a **Hitelesítés a RollWorksszel** lehetőséget, és adja meg a RollWorks rendszergazdai hitelesítő adatait.</span><span class="sxs-lookup"><span data-stu-id="fe984-126">Select **Authenticate with RollWorks** and provide your admin credentials for RollWorks.</span></span>

1. <span data-ttu-id="fe984-127">Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.</span><span class="sxs-lookup"><span data-stu-id="fe984-127">Select **Add yourself as export user** and provide your Customer Insights credentials.</span></span>

1. <span data-ttu-id="fe984-128">A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="fe984-128">Select **Save** to complete the connection.</span></span>

## <a name="configure-an-export"></a><span data-ttu-id="fe984-129">Exportálás konfigurálása</span><span class="sxs-lookup"><span data-stu-id="fe984-129">Configure an export</span></span>

<span data-ttu-id="fe984-130">Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz.</span><span class="sxs-lookup"><span data-stu-id="fe984-130">You can configure this export if you have access to a connection of this type.</span></span> <span data-ttu-id="fe984-131">További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).</span><span class="sxs-lookup"><span data-stu-id="fe984-131">For more information, see [Permissions needed to configure an export](export-destinations.md#set-up-a-new-export).</span></span>

1. <span data-ttu-id="fe984-132">Menjen az **Adatok** > **Exportálások** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="fe984-132">Go to **Data** > **Exports**.</span></span>

1. <span data-ttu-id="fe984-133">Új exportálás létrehozásához válassza a **Célhely hozzáadása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="fe984-133">To create a new export, select **Add destination**.</span></span>

1. <span data-ttu-id="fe984-134">A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot a RollWorks szakaszból.</span><span class="sxs-lookup"><span data-stu-id="fe984-134">In the **Connection for export** field, choose a connection from the RollWorks section.</span></span> <span data-ttu-id="fe984-135">Ha nem látja ezt a szakasznevet, az Ön számára nincs ilyen típusú kapcsolat.</span><span class="sxs-lookup"><span data-stu-id="fe984-135">If you don't see this section name, there are no connections of this type available to you.</span></span>

1. <span data-ttu-id="fe984-136">Adja meg a **RollWorks Advertiser azonosítót** [RollWorks Advertisable](https://help.adroll.com/hc/articles/212011838-Advertiser-Profiles) értéket.</span><span class="sxs-lookup"><span data-stu-id="fe984-136">Enter your **RollWorks Advertiser ID** [RollWorks Advertisable](https://help.adroll.com/hc/articles/212011838-Advertiser-Profiles).</span></span>

3. <span data-ttu-id="fe984-137">Az **Adategyeztetés** szakaszban az **E-mail** mezőben jelölje ki az egyesített ügyfélprofil ügyfél e-mail-címét jelképező mezőjét.</span><span class="sxs-lookup"><span data-stu-id="fe984-137">In the **Data matching** section, in the **Email** field, select the field in your unified customer profile that represents a customer's email address.</span></span> <span data-ttu-id="fe984-138">A szegmenseket exportálni kell a RollWorks alkalmazásba.</span><span class="sxs-lookup"><span data-stu-id="fe984-138">It's required to export segments to RollWorks.</span></span>

1. <span data-ttu-id="fe984-139">Jelölje ki a szegmenseket, amelyeket exportálni szeretne.</span><span class="sxs-lookup"><span data-stu-id="fe984-139">Select the segments you want to export.</span></span> <span data-ttu-id="fe984-140">Jelöljön ki egy legalább 100 tagból álló szegmenst.</span><span class="sxs-lookup"><span data-stu-id="fe984-140">Select a segment with a least 100 members.</span></span> <span data-ttu-id="fe984-141">Kisebb szegmensek nem exportálhatók.</span><span class="sxs-lookup"><span data-stu-id="fe984-141">You can't export smaller segments.</span></span> <span data-ttu-id="fe984-142">Az exportálni kívánt szegmens maximális mérete exportálásonként 250 000 tag.</span><span class="sxs-lookup"><span data-stu-id="fe984-142">Additionally the maximum size of a segment to export is 250'000 members per export.</span></span> 

1. <span data-ttu-id="fe984-143">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="fe984-143">Select **Save**.</span></span>

<span data-ttu-id="fe984-144">Az exportálás mentése nem futtatja azonnal az exportálást.</span><span class="sxs-lookup"><span data-stu-id="fe984-144">Saving an export doesn't run the export immediately.</span></span>

<span data-ttu-id="fe984-145">Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut.</span><span class="sxs-lookup"><span data-stu-id="fe984-145">The export runs with every [scheduled refresh](system.md#schedule-tab).</span></span> <span data-ttu-id="fe984-146">Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand).</span><span class="sxs-lookup"><span data-stu-id="fe984-146">You can also [export data on demand](export-destinations.md#run-exports-on-demand).</span></span> 


## <a name="data-privacy-and-compliance"></a><span data-ttu-id="fe984-147">Adatvédelem és megfelelőség</span><span class="sxs-lookup"><span data-stu-id="fe984-147">Data privacy and compliance</span></span>

<span data-ttu-id="fe984-148">Amikor engedélyezi Dynamics 365 Customer Insightst, hogy adatokat továbbítson a RollWorksnek, akkor lehetővé teszi az adatok továbbítását a Dynamics 365 Customer Insights megfelelési határán kívülre is, beleértve az esetlegesen bizalmas adatokat is, például a Személyes adatokat.</span><span class="sxs-lookup"><span data-stu-id="fe984-148">When you enable Dynamics 365 Customer Insights to transmit data to RollWorks, you allow transfer of data outside of the compliance boundary for Dynamics 365 Customer Insights, including potentially sensitive data such as Personal Data.</span></span> <span data-ttu-id="fe984-149">A Microsoft az Ön utasítására továbbítja az adatokat, de Ön a felelős azért, hogy a RollWorks megfeleljen az esetleges adatvédelmi vagy biztonsági kötelezettségeknek.</span><span class="sxs-lookup"><span data-stu-id="fe984-149">Microsoft will transfer such data at your instruction, but you are responsible for ensuring that RollWorks meets any privacy or security obligations you may have.</span></span> <span data-ttu-id="fe984-150">További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).</span><span class="sxs-lookup"><span data-stu-id="fe984-150">For more information, see [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?linkid=396732).</span></span>

<span data-ttu-id="fe984-151">A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.</span><span class="sxs-lookup"><span data-stu-id="fe984-151">Your Dynamics 365 Customer Insights Administrator can remove this export destination at any time to discontinue use of this functionality.</span></span>
