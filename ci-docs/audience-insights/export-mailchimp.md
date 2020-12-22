---
title: Customer Insights adatok exportálása a Mailchimpbe
description: Megismerheti, hogyan konfigurálható a kapcsolat a Mailchimppel.
ms.date: 10/26/2020
ms.reviewer: philk
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: edff494f6edf26a8b641cb1d788a715389ddb346
ms.sourcegitcommit: cf9b78559ca189d4c2086a66c879098d56c0377a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/03/2020
ms.locfileid: "4405984"
---
# <a name="connector-for-mailchimp-preview"></a><span data-ttu-id="e28dc-103">A Mailchimp összekötője (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="e28dc-103">Connector for Mailchimp (preview)</span></span>

<span data-ttu-id="e28dc-104">Az egyesített ügyfélprofilok szegmenseinek Mailchimpbe való exportálásával hírleveleket és e-mail-kampányokat hozhat létre.</span><span class="sxs-lookup"><span data-stu-id="e28dc-104">Export segments of unified customer profiles to Mailchimp to create newsletters and email campaigns.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e28dc-105">Előfeltételek</span><span class="sxs-lookup"><span data-stu-id="e28dc-105">Prerequisites</span></span>

-   <span data-ttu-id="e28dc-106">Rendelkezik [Mailchimp-fiókkal](https://mailchimp.com/) és a megfelelő rendszergazdai hitelesítő adatokkal.</span><span class="sxs-lookup"><span data-stu-id="e28dc-106">You have a [Mailchimp account](https://mailchimp.com/) and corresponding administrator credentials.</span></span>
-   <span data-ttu-id="e28dc-107">A Mailchimpben és a megfelelő azonosítókban meglévő célközönségek találhatók.</span><span class="sxs-lookup"><span data-stu-id="e28dc-107">There are existing audiences in Mailchimp and the corresponding IDs.</span></span> <span data-ttu-id="e28dc-108">További információért lásd: [Mailchimp-célközönségek](https://mailchimp.com/help/create-audience/).</span><span class="sxs-lookup"><span data-stu-id="e28dc-108">For more information, see [Mailchimp audiences](https://mailchimp.com/help/create-audience/).</span></span>
-   <span data-ttu-id="e28dc-109">Rendelkezik [konfigurált szegmensekkel](segments.md)</span><span class="sxs-lookup"><span data-stu-id="e28dc-109">You have [configured segments](segments.md)</span></span>
-   <span data-ttu-id="e28dc-110">Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.</span><span class="sxs-lookup"><span data-stu-id="e28dc-110">Unified customer profiles in the exported segments contain a field representing an email address.</span></span>

## <a name="connect-to-mailchimp"></a><span data-ttu-id="e28dc-111">Csatlakozás a MailChimp szolgáltatáshoz</span><span class="sxs-lookup"><span data-stu-id="e28dc-111">Connect to Mailchimp</span></span>

1. <span data-ttu-id="e28dc-112">Válassz a **Rendszergazda** > **Célok exportálása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="e28dc-112">Go to **Admin** > **Export destinations**.</span></span>

1. <span data-ttu-id="e28dc-113">A **Mailchimp** részben válassza a **Beállítás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="e28dc-113">Under **Mailchimp**, select **Set up**.</span></span>

1. <span data-ttu-id="e28dc-114">Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben az export helyének.</span><span class="sxs-lookup"><span data-stu-id="e28dc-114">Give your export destination a recognizable name in the **Display name** field.</span></span>

1. <span data-ttu-id="e28dc-115">Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.</span><span class="sxs-lookup"><span data-stu-id="e28dc-115">Select **I agree** to confirm the **Data privacy and compliance**.</span></span>

1. <span data-ttu-id="e28dc-116">Adja meg a **[Mailchimp célközönség azonosítóját](https://mailchimp.com/help/find-audience-id/)**, és válassza a **Csatlakozás** lehetőséget a Mailchimp-kapcsolat kezdeményezéséhez.</span><span class="sxs-lookup"><span data-stu-id="e28dc-116">Enter your **[Mailchimp audience ID](https://mailchimp.com/help/find-audience-id/)** and select **Connect** to initialize the connection to Mailchimp.</span></span>

1. <span data-ttu-id="e28dc-117">Válassza a **Hitelesítés a Mailchimp szolgáltatással** lehetőséget, és adja meg Mailchimp-hitelesítő adatait.</span><span class="sxs-lookup"><span data-stu-id="e28dc-117">Select **Authenticate with Mailchimp** and provide your Mailchimp credentials.</span></span>

1. <span data-ttu-id="e28dc-118">Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.</span><span class="sxs-lookup"><span data-stu-id="e28dc-118">Select **Add yourself as export user** and provide your Customer Insights credentials.</span></span>

   :::image type="content" source="media/export-connect-mailchimp.png" alt-text="Képernyőkép exportálása a Mailchimp kapcsolatához":::

1. <span data-ttu-id="e28dc-120">Az Exportálás konfigurálásához válassza a **Tovább** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="e28dc-120">Select **Next** to configure the export.</span></span>

## <a name="configure-the-connector"></a><span data-ttu-id="e28dc-121">Konfigurálja az összekötőt</span><span class="sxs-lookup"><span data-stu-id="e28dc-121">Configure the connector</span></span>

1. <span data-ttu-id="e28dc-122">Az **Adategyeztetés** szakaszban az **E-mail** mezőben jelölje ki az egyesített ügyfélprofil ügyfél e-mail-címét jelképező mezőjét.</span><span class="sxs-lookup"><span data-stu-id="e28dc-122">In the **Data matching** section, in the **Email** field, select the field in your unified customer profile that represents a customer's email address.</span></span> 

1. <span data-ttu-id="e28dc-123">Alternatív lehetőségként exportálhatja az **Utónév** és **Vezetéknév** mezőket további mezőként személyre szabottabb e-mailek létrehozásához.</span><span class="sxs-lookup"><span data-stu-id="e28dc-123">Optionally, you can export **First name** and **Last name** as additional fields to create more personalized emails.</span></span> <span data-ttu-id="e28dc-124">Válassza az **Attribútum hozzáadása** lehetőséget a mezők leképezéséhez.</span><span class="sxs-lookup"><span data-stu-id="e28dc-124">Select **Add attribute** to map these fields.</span></span>

1. <span data-ttu-id="e28dc-125">Jelölje ki a szegmenseket, amelyeket exportálni szeretne.</span><span class="sxs-lookup"><span data-stu-id="e28dc-125">Select the segments you want to export.</span></span> <span data-ttu-id="e28dc-126">Összesen legfeljebb 1 000 000 ügyfélprofilt exportálhat a Mailchimpbe.</span><span class="sxs-lookup"><span data-stu-id="e28dc-126">You can export up to 1 million customer profiles in total to Mailchimp.</span></span>

   :::image type="content" source="media/export-segments-mailchimp.png" alt-text="Mailchimpbe exportálandó mezők és szegmensek kijelölése":::

1. <span data-ttu-id="e28dc-128">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="e28dc-128">Select **Save**.</span></span>

## <a name="export-the-data"></a><span data-ttu-id="e28dc-129">Az adatok exportálása</span><span class="sxs-lookup"><span data-stu-id="e28dc-129">Export the data</span></span>

<span data-ttu-id="e28dc-130">[Igény szerint exportálhatja az adatot](export-destinations.md).</span><span class="sxs-lookup"><span data-stu-id="e28dc-130">You can [export data on demand](export-destinations.md).</span></span> <span data-ttu-id="e28dc-131">Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) együtt is lefut.</span><span class="sxs-lookup"><span data-stu-id="e28dc-131">The export will also run with every [scheduled refresh](system.md#schedule-tab).</span></span> <span data-ttu-id="e28dc-132">A Mailchimpben most már megtalálhatja a szegmenseket a [Mailchimp célközönségekben](https://mailchimp.com/help/create-audience/).</span><span class="sxs-lookup"><span data-stu-id="e28dc-132">In Mailchimp, you can now find your segments under [Mailchimp audiences](https://mailchimp.com/help/create-audience/).</span></span>

## <a name="known-limitations"></a><span data-ttu-id="e28dc-133">Ismert korlátozások</span><span class="sxs-lookup"><span data-stu-id="e28dc-133">Known limitations</span></span>

- <span data-ttu-id="e28dc-134">Legfeljebb 1 000 000 profilt exportálhat egyszerre a Mailchimpbe.</span><span class="sxs-lookup"><span data-stu-id="e28dc-134">Up to 1 million profiles per export to Mailchimp.</span></span>
- <span data-ttu-id="e28dc-135">A Mailchimpbe való exportálás csak szegmensekre korlátozódik.</span><span class="sxs-lookup"><span data-stu-id="e28dc-135">Exporting to Mailchimp is limited to segments.</span></span>
- <span data-ttu-id="e28dc-136">Az összesen 1 000 000 profillal rendelkező szegmens exportálása a szolgáltatói oldalon megjelenő korlátozások miatt akár 3 óráig is eltarthat.</span><span class="sxs-lookup"><span data-stu-id="e28dc-136">Exporting segments with a total of 1 million profiles can take up to three hours due to limitations on the provider side.</span></span> 
- <span data-ttu-id="e28dc-137">A Mailchimpbe exportálható profilok száma függ a Mailchimp szerződésről, és korlátozott.</span><span class="sxs-lookup"><span data-stu-id="e28dc-137">The number of profiles that you can export to Mailchimp is dependent and limited on your contract with Mailchimp.</span></span>

## <a name="data-privacy-and-compliance"></a><span data-ttu-id="e28dc-138">Adatvédelem és megfelelőség</span><span class="sxs-lookup"><span data-stu-id="e28dc-138">Data privacy and compliance</span></span>

<span data-ttu-id="e28dc-139">Amikor engedélyezi a Dynamics 365 Customer Insights szolgáltatást az adatok Mailchimp szolgáltatásba való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat.</span><span class="sxs-lookup"><span data-stu-id="e28dc-139">When you enable Dynamics 365 Customer Insights to transmit data to Mailchimp, you allow transfer of data outside of the compliance boundary for Dynamics 365 Customer Insights, including potentially sensitive data such as Personal Data.</span></span> <span data-ttu-id="e28dc-140">A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy a Mailchimp megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek.</span><span class="sxs-lookup"><span data-stu-id="e28dc-140">Microsoft will transfer such data at your instruction, but you are responsible for ensuring that Mailchimp meets any privacy or security obligations you may have.</span></span> <span data-ttu-id="e28dc-141">További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).</span><span class="sxs-lookup"><span data-stu-id="e28dc-141">For more information, see [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?linkid=396732).</span></span>
<span data-ttu-id="e28dc-142">A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.</span><span class="sxs-lookup"><span data-stu-id="e28dc-142">Your Dynamics 365 Customer Insights Administrator can remove this export destination at any time to discontinue use of this functionality.</span></span>
