---
title: Customer Insights-adatok exportálása a Snapchatre
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a Snapchatbe.
ms.date: 03/22/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: d3dae7f0fef1fc3792c90c8ac0d3b037f5c0923d
ms.sourcegitcommit: 1b671c6100991fea1cace04b5d4fcedcd88aa94f
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/31/2021
ms.locfileid: "5760550"
---
# <a name="export-segment-lists-to-snapchat-preview"></a><span data-ttu-id="80f3e-103">Szegmenslisták exportálása a Snapchatbe (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="80f3e-103">Export segment lists to Snapchat (preview)</span></span>

<span data-ttu-id="80f3e-104">Exportálja az egyesített ügyfélprofilok szegmensét a Snapchatbe, és használja őket hirdetési célokra.</span><span class="sxs-lookup"><span data-stu-id="80f3e-104">Export segments of unified customer profiles to Snapchat and use them for advertising.</span></span> 

## <a name="prerequisites-for-a-connection"></a><span data-ttu-id="80f3e-105">Egy kapcsolat előfeltételei</span><span class="sxs-lookup"><span data-stu-id="80f3e-105">Prerequisites for a connection</span></span>

-   <span data-ttu-id="80f3e-106">Van egy [Snapchat Business fiókja](https://business.snapchat.com/), egy [Snapchat Ads fiókja](https://ads.snapchat.com/), és megfelelő rendszergazdai hitelesítő adatai.</span><span class="sxs-lookup"><span data-stu-id="80f3e-106">You have a [Snapchat Business account](https://business.snapchat.com/), a [Snapchat Ads account](https://ads.snapchat.com/), and corresponding administrator credentials.</span></span>
-   <span data-ttu-id="80f3e-107">[Konfigurált szegmensekkel](segments.md) rendelkezik a célközönségi-információkban.</span><span class="sxs-lookup"><span data-stu-id="80f3e-107">You have [configured segments](segments.md) in audience insights.</span></span>
-   <span data-ttu-id="80f3e-108">Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.</span><span class="sxs-lookup"><span data-stu-id="80f3e-108">Unified customer profiles in the exported segments contain a field representing an email address.</span></span>

## <a name="known-limitations"></a><span data-ttu-id="80f3e-109">Ismert korlátozások</span><span class="sxs-lookup"><span data-stu-id="80f3e-109">Known limitations</span></span>

- <span data-ttu-id="80f3e-110">A Snapchatbe való exportálás a szegmensekre korlátozódik.</span><span class="sxs-lookup"><span data-stu-id="80f3e-110">Exporting to Snapchat is limited to segments.</span></span>
- <span data-ttu-id="80f3e-111">1 millió profil exportálása a Snapchat alkalmazásba akár 15 percet is igénybe vehet.</span><span class="sxs-lookup"><span data-stu-id="80f3e-111">Exporting up to 1 million profiles to Snapchat can take up to 15 minutes to complete.</span></span> 

## <a name="set-up-connection-to-snapchat"></a><span data-ttu-id="80f3e-112">Állítsa be a Snapchettel való kapcsolatot</span><span class="sxs-lookup"><span data-stu-id="80f3e-112">Set up connection to Snapchat</span></span>

1. <span data-ttu-id="80f3e-113">Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="80f3e-113">Go to **Admin** > **Connections**.</span></span>

1. <span data-ttu-id="80f3e-114">Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza a **Snapchat** lehetőséget a kapcsolat konfigurálásához.</span><span class="sxs-lookup"><span data-stu-id="80f3e-114">Select **Add connection** and choose **Snapchat** to configure the connection.</span></span>

1. <span data-ttu-id="80f3e-115">Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak.</span><span class="sxs-lookup"><span data-stu-id="80f3e-115">Give your connection a recognizable name in the **Display name** field.</span></span> <span data-ttu-id="80f3e-116">A név és a kapcsolat típusa írja le ezt a kapcsolatot.</span><span class="sxs-lookup"><span data-stu-id="80f3e-116">The name and the type of the connection describe this connection.</span></span> <span data-ttu-id="80f3e-117">Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.</span><span class="sxs-lookup"><span data-stu-id="80f3e-117">We recommend choosing a name that explains the purpose and target of the connection.</span></span>

1. <span data-ttu-id="80f3e-118">A kapcsolat használóinak kiválasztása.</span><span class="sxs-lookup"><span data-stu-id="80f3e-118">Choose who can use this connection.</span></span> <span data-ttu-id="80f3e-119">Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz.</span><span class="sxs-lookup"><span data-stu-id="80f3e-119">If you take no action, the default will be Administrators.</span></span> <span data-ttu-id="80f3e-120">További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).</span><span class="sxs-lookup"><span data-stu-id="80f3e-120">For more information, see [Allow contributors to use a connection for exports](connections.md#allow-contributors-to-use-a-connection-for-exports).</span></span>

1. <span data-ttu-id="80f3e-121">Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.</span><span class="sxs-lookup"><span data-stu-id="80f3e-121">Select **I agree** to confirm the **Data privacy and compliance**.</span></span>

1. <span data-ttu-id="80f3e-122">Válassza a **Kapcsolat** lehetőséget a Snapchat kapcsolatának inicializálására.</span><span class="sxs-lookup"><span data-stu-id="80f3e-122">Select **Connect** to initialize the connection to Snapchat.</span></span>

1. <span data-ttu-id="80f3e-123">Válassza a **Hitelesítés a Snapchattel** lehetőséget, és adja meg a Snapchat rendszergazdai hitelesítő adatait.</span><span class="sxs-lookup"><span data-stu-id="80f3e-123">Select **Authenticate with Snapchat** and provide your admin credentials for Snapchat.</span></span> 

1. <span data-ttu-id="80f3e-124">Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.</span><span class="sxs-lookup"><span data-stu-id="80f3e-124">Select **Add yourself as export user** and provide your Customer Insights credentials.</span></span>

1. <span data-ttu-id="80f3e-125">A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="80f3e-125">Select **Save** to complete the connection.</span></span>

## <a name="configure-an-export"></a><span data-ttu-id="80f3e-126">Exportálás konfigurálása</span><span class="sxs-lookup"><span data-stu-id="80f3e-126">Configure an export</span></span>

<span data-ttu-id="80f3e-127">Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz.</span><span class="sxs-lookup"><span data-stu-id="80f3e-127">You can configure this export if you have access to a connection of this type.</span></span> <span data-ttu-id="80f3e-128">További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).</span><span class="sxs-lookup"><span data-stu-id="80f3e-128">For more information, see [Permissions needed to configure an export](export-destinations.md#set-up-a-new-export).</span></span>

1. <span data-ttu-id="80f3e-129">Menjen az **Adatok** > **Exportálások** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="80f3e-129">Go to **Data** > **Exports**.</span></span>

1. <span data-ttu-id="80f3e-130">Új exportálás létrehozásához válassza a **Célhely hozzáadása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="80f3e-130">To create a new export, select **Add destination**.</span></span>

1. <span data-ttu-id="80f3e-131">A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot a Snapchat szakaszból.</span><span class="sxs-lookup"><span data-stu-id="80f3e-131">In the **Connection for export** field, choose a connection from the Snapchat section.</span></span> <span data-ttu-id="80f3e-132">Ha nem látja ezt a szakasznevet, az Ön számára nincs ilyen típusú kapcsolat.</span><span class="sxs-lookup"><span data-stu-id="80f3e-132">If you don't see this section name, there are no connections of this type available to you.</span></span>

1. <span data-ttu-id="80f3e-133">Adja meg a [**Snapchat célközönségazonosítót**](https://businesshelp.snapchat.com/s/article/custom-audiences).</span><span class="sxs-lookup"><span data-stu-id="80f3e-133">Enter the [**Snapchat Audience ID**](https://businesshelp.snapchat.com/s/article/custom-audiences).</span></span>

1. <span data-ttu-id="80f3e-134">Az **Adategyeztetés** szakaszban az **E-mail** mezőben jelölje ki az egyesített ügyfélprofil ügyfél e-mail-címét jelképező mezőjét.</span><span class="sxs-lookup"><span data-stu-id="80f3e-134">In the **Data matching** section, in the **Email** field, select the field in your unified customer profile that represents a customer's email address.</span></span> <span data-ttu-id="80f3e-135">A szegmenseket exportálni kell a Snapchat alkalmazásba.</span><span class="sxs-lookup"><span data-stu-id="80f3e-135">It's required to export segments to Snapchat.</span></span>

1. <span data-ttu-id="80f3e-136">Jelölje ki a szegmenseket, amelyeket exportálni szeretne.</span><span class="sxs-lookup"><span data-stu-id="80f3e-136">Select the segments you want to export.</span></span> 

1. <span data-ttu-id="80f3e-137">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="80f3e-137">Select **Save**.</span></span>

<span data-ttu-id="80f3e-138">Az exportálás mentése nem futtatja azonnal az exportálást.</span><span class="sxs-lookup"><span data-stu-id="80f3e-138">Saving an export doesn't run the export immediately.</span></span>

<span data-ttu-id="80f3e-139">Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut.</span><span class="sxs-lookup"><span data-stu-id="80f3e-139">The export runs with every [scheduled refresh](system.md#schedule-tab).</span></span> <span data-ttu-id="80f3e-140">Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand).</span><span class="sxs-lookup"><span data-stu-id="80f3e-140">You can also [export data on demand](export-destinations.md#run-exports-on-demand).</span></span> 


## <a name="data-privacy-and-compliance"></a><span data-ttu-id="80f3e-141">Adatvédelem és megfelelőség</span><span class="sxs-lookup"><span data-stu-id="80f3e-141">Data privacy and compliance</span></span>

<span data-ttu-id="80f3e-142">Amikor engedélyezi Dynamics 365 Customer Insightst, hogy adatokat továbbítson a Snapchatnek, akkor lehetővé teszi az adatok továbbítását a Dynamics 365 Customer Insights megfelelési határán kívülre is, beleértve az esetlegesen bizalmas adatokat is, például a Személyes adatokat.</span><span class="sxs-lookup"><span data-stu-id="80f3e-142">When you enable Dynamics 365 Customer Insights to transmit data to Snapchat, you allow transfer of data outside of the compliance boundary for Dynamics 365 Customer Insights, including potentially sensitive data such as Personal Data.</span></span> <span data-ttu-id="80f3e-143">A Microsoft az Ön utasítására továbbítja az adatokat, de Ön a felelős azért, hogy a Snapchat megfeleljen az esetleges adatvédelmi vagy biztonsági kötelezettségeknek.</span><span class="sxs-lookup"><span data-stu-id="80f3e-143">Microsoft will transfer such data at your instruction, but you are responsible for ensuring that Snapchat meets any privacy or security obligations you may have.</span></span> <span data-ttu-id="80f3e-144">További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).</span><span class="sxs-lookup"><span data-stu-id="80f3e-144">For more information, see [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?linkid=396732).</span></span>

<span data-ttu-id="80f3e-145">A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.</span><span class="sxs-lookup"><span data-stu-id="80f3e-145">Your Dynamics 365 Customer Insights Administrator can remove this export destination at any time to discontinue use of this functionality.</span></span>
