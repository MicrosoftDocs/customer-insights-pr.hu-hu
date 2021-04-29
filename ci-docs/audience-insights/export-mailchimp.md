---
title: Customer Insights adatok exportálása a Mailchimpbe
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a Mailchimpbe.
ms.date: 03/03/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: phkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: b94a8e8b6bb867ca04a64007d592b22fbd700618
ms.sourcegitcommit: 1b671c6100991fea1cace04b5d4fcedcd88aa94f
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/31/2021
ms.locfileid: "5759881"
---
# <a name="export-segment-lists-to-mailchimp-preview"></a><span data-ttu-id="7486d-103">Szegmenslisták exportálása a Mailchimpbe (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="7486d-103">Export segment lists to Mailchimp (preview)</span></span>

<span data-ttu-id="7486d-104">Az egyesített ügyfélprofilok szegmenseinek Mailchimpbe való exportálásával hírleveleket és e-mail-kampányokat hozhat létre.</span><span class="sxs-lookup"><span data-stu-id="7486d-104">Export segments of unified customer profiles to Mailchimp to create newsletters and email campaigns.</span></span>

## <a name="prerequisites-for-connection"></a><span data-ttu-id="7486d-105">A kapcsolat előfeltételei</span><span class="sxs-lookup"><span data-stu-id="7486d-105">Prerequisites for connection</span></span>

-   <span data-ttu-id="7486d-106">Rendelkezik [Mailchimp-fiókkal](https://mailchimp.com/) és a megfelelő rendszergazdai hitelesítő adatokkal.</span><span class="sxs-lookup"><span data-stu-id="7486d-106">You have a [Mailchimp account](https://mailchimp.com/) and corresponding administrator credentials.</span></span>
-   <span data-ttu-id="7486d-107">A Mailchimpben és a megfelelő azonosítókban meglévő célközönségek találhatók.</span><span class="sxs-lookup"><span data-stu-id="7486d-107">There are existing audiences in Mailchimp and the corresponding IDs.</span></span> <span data-ttu-id="7486d-108">További információért lásd: [Mailchimp-célközönségek](https://mailchimp.com/help/create-audience/).</span><span class="sxs-lookup"><span data-stu-id="7486d-108">For more information, see [Mailchimp audiences](https://mailchimp.com/help/create-audience/).</span></span>
-   <span data-ttu-id="7486d-109">Rendelkezik [konfigurált szegmensekkel](segments.md)</span><span class="sxs-lookup"><span data-stu-id="7486d-109">You have [configured segments](segments.md)</span></span>
-   <span data-ttu-id="7486d-110">Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.</span><span class="sxs-lookup"><span data-stu-id="7486d-110">Unified customer profiles in the exported segments contain a field representing an email address.</span></span>

## <a name="known-limitations"></a><span data-ttu-id="7486d-111">Ismert korlátozások</span><span class="sxs-lookup"><span data-stu-id="7486d-111">Known limitations</span></span>

- <span data-ttu-id="7486d-112">Legfeljebb 1 000 000 profilt exportálhat egyszerre a Mailchimpbe.</span><span class="sxs-lookup"><span data-stu-id="7486d-112">Up to 1 million profiles per export to Mailchimp.</span></span>
- <span data-ttu-id="7486d-113">A Mailchimpbe való exportálás csak szegmensekre korlátozódik.</span><span class="sxs-lookup"><span data-stu-id="7486d-113">Exporting to Mailchimp is limited to segments.</span></span>
- <span data-ttu-id="7486d-114">Az 1 millió profilból álló szegmensek exportálása akár három órát is igénybe fog venni.</span><span class="sxs-lookup"><span data-stu-id="7486d-114">Exporting segments with 1 million profiles can take up to three hours.</span></span> 
- <span data-ttu-id="7486d-115">A Mailchimpbe exportálható profilok száma függ a Mailchimp szerződésről, és korlátozott.</span><span class="sxs-lookup"><span data-stu-id="7486d-115">The number of profiles that you can export to Mailchimp is dependent and limited on your contract with Mailchimp.</span></span>

## <a name="set-up-connection-to-mailchimp"></a><span data-ttu-id="7486d-116">Állítsa be a Mailchimppel való kapcsolatot</span><span class="sxs-lookup"><span data-stu-id="7486d-116">Set up connection to Mailchimp</span></span>

1. <span data-ttu-id="7486d-117">Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="7486d-117">Go to **Admin** > **Connections**.</span></span>

1. <span data-ttu-id="7486d-118">Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza az **Autopilot** lehetőséget a kapcsolat konfigurálásához.</span><span class="sxs-lookup"><span data-stu-id="7486d-118">Select **Add connection** and choose **Autopilot** to configure the connection.</span></span>

1. <span data-ttu-id="7486d-119">Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak.</span><span class="sxs-lookup"><span data-stu-id="7486d-119">Give your connection a recognizable name in the **Display name** field.</span></span> <span data-ttu-id="7486d-120">A név és a kapcsolat típusa írja le ezt a kapcsolatot.</span><span class="sxs-lookup"><span data-stu-id="7486d-120">The name and the type of the connection describe this connection.</span></span> <span data-ttu-id="7486d-121">Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.</span><span class="sxs-lookup"><span data-stu-id="7486d-121">We recommend choosing a name that explains the purpose and target of the connection.</span></span>

1. <span data-ttu-id="7486d-122">A kapcsolat használóinak kiválasztása.</span><span class="sxs-lookup"><span data-stu-id="7486d-122">Choose who can use this connection.</span></span> <span data-ttu-id="7486d-123">Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz.</span><span class="sxs-lookup"><span data-stu-id="7486d-123">If you take no action, the default will be Administrators.</span></span> <span data-ttu-id="7486d-124">További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).</span><span class="sxs-lookup"><span data-stu-id="7486d-124">For more information, see [Allow contributors to use a connection for exports](connections.md#allow-contributors-to-use-a-connection-for-exports).</span></span>

1. <span data-ttu-id="7486d-125">Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.</span><span class="sxs-lookup"><span data-stu-id="7486d-125">Select **I agree** to confirm the **Data privacy and compliance**.</span></span>

1. <span data-ttu-id="7486d-126">Válassza a **Kapcsolat** lehetőséget a Mailchimp kapcsolatának inicializálására.</span><span class="sxs-lookup"><span data-stu-id="7486d-126">Select **Connect** to initialize the connection to Mailchimp.</span></span>

1. <span data-ttu-id="7486d-127">Válassza a **Hitelesítés a Mailchimp szolgáltatással** lehetőséget, és adja meg Mailchimp-hitelesítő adatait.</span><span class="sxs-lookup"><span data-stu-id="7486d-127">Select **Authenticate with Mailchimp** and provide your Mailchimp credentials.</span></span>

1. <span data-ttu-id="7486d-128">Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.</span><span class="sxs-lookup"><span data-stu-id="7486d-128">Select **Add yourself as export user** and provide your Customer Insights credentials.</span></span>

1. <span data-ttu-id="7486d-129">A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="7486d-129">Select **Save** to complete the connection.</span></span> 

## <a name="configure-the-connector"></a><span data-ttu-id="7486d-130">Konfigurálja az összekötőt</span><span class="sxs-lookup"><span data-stu-id="7486d-130">Configure the connector</span></span>

<span data-ttu-id="7486d-131">Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz.</span><span class="sxs-lookup"><span data-stu-id="7486d-131">You can configure this export if you have access to a connection of this type.</span></span> <span data-ttu-id="7486d-132">További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).</span><span class="sxs-lookup"><span data-stu-id="7486d-132">For more information, see [Permissions needed to configure an export](export-destinations.md#set-up-a-new-export).</span></span>

1. <span data-ttu-id="7486d-133">Menjen az **Adatok**> **Exportálások** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="7486d-133">Go to **Data**> **Exports**.</span></span>

1. <span data-ttu-id="7486d-134">Új exportálás létrehozásához válassza a **Célhely hozzáadása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="7486d-134">To create a new export, select **Add destination**.</span></span>

1. <span data-ttu-id="7486d-135">A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot a Mailchimp szakaszból.</span><span class="sxs-lookup"><span data-stu-id="7486d-135">In the **Connection for export** field, choose a connection from the Mailchimp section.</span></span> <span data-ttu-id="7486d-136">Ha nem látja ezt a szakasznevet, az Ön számára nincs ilyen típusú kapcsolat.</span><span class="sxs-lookup"><span data-stu-id="7486d-136">If you don't see this section name, there are no connections of this type available to you.</span></span>

1. <span data-ttu-id="7486d-137">Adja meg a **[MailChimp célközönség-azonosítóját](https://mailchimp.com/help/find-audience-id/)**</span><span class="sxs-lookup"><span data-stu-id="7486d-137">Enter your **[Mailchimp audience ID](https://mailchimp.com/help/find-audience-id/)**</span></span>

3. <span data-ttu-id="7486d-138">Az **Adategyeztetés** szakaszban az **E-mail** mezőben jelölje ki az egyesített ügyfélprofil ügyfél e-mail-címét jelképező mezőjét.</span><span class="sxs-lookup"><span data-stu-id="7486d-138">In the **Data matching** section, in the **Email** field, select the field in your unified customer profile that represents a customer's email address.</span></span> 

1. <span data-ttu-id="7486d-139">Tetszés szerint exportálhatja az **Utónév** és **Vezetéknév** lehetőségeket, hogy személyre szabottabb e-maileket hozzon létre.</span><span class="sxs-lookup"><span data-stu-id="7486d-139">Optionally, you can export **First name** and **Last name** to create more personalized emails.</span></span> <span data-ttu-id="7486d-140">Válassza az **Attribútum hozzáadása** lehetőséget a mezők leképezéséhez.</span><span class="sxs-lookup"><span data-stu-id="7486d-140">Select **Add attribute** to map these fields.</span></span>

1. <span data-ttu-id="7486d-141">Jelölje ki a szegmenseket, amelyeket exportálni szeretne.</span><span class="sxs-lookup"><span data-stu-id="7486d-141">Select the segments you want to export.</span></span> <span data-ttu-id="7486d-142">Összesen legfeljebb 1 000 000 ügyfélprofilt exportálhat a Mailchimpbe.</span><span class="sxs-lookup"><span data-stu-id="7486d-142">You can export up to 1 million customer profiles in total to Mailchimp.</span></span>

1. <span data-ttu-id="7486d-143">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="7486d-143">Select **Save**.</span></span>

<span data-ttu-id="7486d-144">Az exportálás mentése nem futtatja azonnal az exportálást.</span><span class="sxs-lookup"><span data-stu-id="7486d-144">Saving an export doesn't run the export immediately.</span></span>

<span data-ttu-id="7486d-145">Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut.</span><span class="sxs-lookup"><span data-stu-id="7486d-145">The export runs with every [scheduled refresh](system.md#schedule-tab).</span></span> <span data-ttu-id="7486d-146">Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand).</span><span class="sxs-lookup"><span data-stu-id="7486d-146">You can also [export data on demand](export-destinations.md#run-exports-on-demand).</span></span> 

## <a name="data-privacy-and-compliance"></a><span data-ttu-id="7486d-147">Adatvédelem és megfelelőség</span><span class="sxs-lookup"><span data-stu-id="7486d-147">Data privacy and compliance</span></span>

<span data-ttu-id="7486d-148">Amikor engedélyezi a Dynamics 365 Customer Insights szolgáltatást az adatok Mailchimp szolgáltatásba való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat.</span><span class="sxs-lookup"><span data-stu-id="7486d-148">When you enable Dynamics 365 Customer Insights to transmit data to Mailchimp, you allow transfer of data outside of the compliance boundary for Dynamics 365 Customer Insights, including potentially sensitive data such as Personal Data.</span></span> <span data-ttu-id="7486d-149">A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy a Mailchimp megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek.</span><span class="sxs-lookup"><span data-stu-id="7486d-149">Microsoft will transfer such data at your instruction, but you are responsible for ensuring that Mailchimp meets any privacy or security obligations you may have.</span></span> <span data-ttu-id="7486d-150">További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).</span><span class="sxs-lookup"><span data-stu-id="7486d-150">For more information, see [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?linkid=396732).</span></span>
<span data-ttu-id="7486d-151">A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.</span><span class="sxs-lookup"><span data-stu-id="7486d-151">Your Dynamics 365 Customer Insights Administrator can remove this export destination at any time to discontinue use of this functionality.</span></span>

[!INCLUDE[footer-include](../includes/footer-banner.md)]
