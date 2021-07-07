---
title: Customer Insights adatok exportálása a Google Adsbe
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a Google Adsbe.
ms.date: 03/03/2021
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: pkieffer
ms.author: philk
ms.reviewer: mhart
manager: shellyha
ms.openlocfilehash: c23c8b4e6758df08e04bf1e3ae0cba4dee06fe2b
ms.sourcegitcommit: d84d664e67f263bfeb741154d309088c5101b9c3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/24/2021
ms.locfileid: "6305343"
---
# <a name="export-segments-to-google-ads-preview"></a><span data-ttu-id="f30f3-103">Szegmensek exportálása a Google Ads szolgáltatásba (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="f30f3-103">Export segments to Google Ads (preview)</span></span>

<span data-ttu-id="f30f3-104">Exportálja az egységes ügyfélprofilok szegmenseit a Google Ads célközönség listára, és használja őket a Google Keresés, a Gmail, YouTube és Google Display Network-ön történő hirdetésnél.</span><span class="sxs-lookup"><span data-stu-id="f30f3-104">Export segments of unified customer profiles to a Google Ads audience list and use them to advertise on Google Search, Gmail, YouTube, and Google Display Network.</span></span> 

## <a name="prerequisites-for-connection"></a><span data-ttu-id="f30f3-105">A kapcsolat előfeltételei</span><span class="sxs-lookup"><span data-stu-id="f30f3-105">Prerequisites for connection</span></span>

-   <span data-ttu-id="f30f3-106">Rendelkezik [Google Ads-fiókkal](https://ads.google.com/) és a megfelelő rendszergazdai hitelesítő adatokkal.</span><span class="sxs-lookup"><span data-stu-id="f30f3-106">You have a [Google Ads account](https://ads.google.com/) and corresponding administrator credentials.</span></span>
-   <span data-ttu-id="f30f3-107">Rendelkezik egy [jóváhagyott Google Ads fejlesztői kóddal](https://developers.google.com/google-ads/api/docs/first-call/dev-token).</span><span class="sxs-lookup"><span data-stu-id="f30f3-107">You have an [approved Google Ads Developer token](https://developers.google.com/google-ads/api/docs/first-call/dev-token).</span></span> 
-   <span data-ttu-id="f30f3-108">Ön megfelel az [Ügyfél megfeleltetési szabályzat](https://support.google.com/adspolicy/answer/6299717) követelményeinek.</span><span class="sxs-lookup"><span data-stu-id="f30f3-108">You fulfill the requirements of the [Customer Match Policy](https://support.google.com/adspolicy/answer/6299717).</span></span>
-   <span data-ttu-id="f30f3-109">Ön teljesíti a [remarketing listaméretekre](https://support.google.com/google-ads/answer/7558048) vonatkozó követelményeket.</span><span class="sxs-lookup"><span data-stu-id="f30f3-109">You fulfill the requirements of the [remarketing list sizes](https://support.google.com/google-ads/answer/7558048).</span></span>
-   <span data-ttu-id="f30f3-110">A Google Adsban és a megfelelő azonosítókban meglévő célközönségek találhatók.</span><span class="sxs-lookup"><span data-stu-id="f30f3-110">There are existing audiences in Google Ads and the corresponding IDs.</span></span> <span data-ttu-id="f30f3-111">További információért lásd: [Google Ads-célközönségek](https://support.google.com/google-ads/answer/7558048?hl=en#:~:text=Audience%20lists%20is%20a%20section,Display%20Network%20through%20remarketing%20campaigns.).</span><span class="sxs-lookup"><span data-stu-id="f30f3-111">For more information, see [Google Ads audiences](https://support.google.com/google-ads/answer/7558048?hl=en#:~:text=Audience%20lists%20is%20a%20section,Display%20Network%20through%20remarketing%20campaigns.).</span></span>
-   <span data-ttu-id="f30f3-112">Rendelkezik [konfigurált szegmensekkel](segments.md).</span><span class="sxs-lookup"><span data-stu-id="f30f3-112">You have [configured segments](segments.md).</span></span>
-   <span data-ttu-id="f30f3-113">Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőket, amelyek e-mail-címet, utónevet és vezetéknevet tartalmaznak.</span><span class="sxs-lookup"><span data-stu-id="f30f3-113">Unified customer profiles in the exported segments contain fields representing an email address, first name, and last name.</span></span>

## <a name="known-limitations"></a><span data-ttu-id="f30f3-114">Ismert korlátozások</span><span class="sxs-lookup"><span data-stu-id="f30f3-114">Known limitations</span></span>

- <span data-ttu-id="f30f3-115">Legfeljebb 1 000 000 profilt exportálhat egyszerre a Google Adsbe.</span><span class="sxs-lookup"><span data-stu-id="f30f3-115">Up to 1 million profiles per export to Google Ads.</span></span>
- <span data-ttu-id="f30f3-116">A Google Adsbe való exportálás csak szegmensekre korlátozódik.</span><span class="sxs-lookup"><span data-stu-id="f30f3-116">Exporting to Google Ads is limited to segments.</span></span>
- <span data-ttu-id="f30f3-117">Az összesen 1 000 000 profillal rendelkező szegmens exportálása a szolgáltatói oldalon megjelenő korlátozások miatt akár 5 percig is eltarthat.</span><span class="sxs-lookup"><span data-stu-id="f30f3-117">Exporting segments with a total of 1 million profiles can take up to 5 minutes because of limitations on the provider side.</span></span> 
- <span data-ttu-id="f30f3-118">A Google Ads egyeztetése akár 48 óráig is eltarthat.</span><span class="sxs-lookup"><span data-stu-id="f30f3-118">The matching in Google Ads can take up to 48 hours.</span></span>

## <a name="set-up-connection-to-google-ads"></a><span data-ttu-id="f30f3-119">Kapcsolat beállítása a Google Adshez</span><span class="sxs-lookup"><span data-stu-id="f30f3-119">Set up connection to Google Ads</span></span>

1. <span data-ttu-id="f30f3-120">Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="f30f3-120">Go to **Admin** > **Connections**.</span></span>

1. <span data-ttu-id="f30f3-121">Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza a **Google Ads** lehetőséget a kapcsolat konfigurálásához.</span><span class="sxs-lookup"><span data-stu-id="f30f3-121">Select **Add connection** and choose **Google Ads** to configure the connection.</span></span>

1. <span data-ttu-id="f30f3-122">Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak.</span><span class="sxs-lookup"><span data-stu-id="f30f3-122">Give your connection a recognizable name in the **Display name** field.</span></span> <span data-ttu-id="f30f3-123">A név és a kapcsolat típusa írja le ezt a kapcsolatot.</span><span class="sxs-lookup"><span data-stu-id="f30f3-123">The name and the type of the connection describe this connection.</span></span> <span data-ttu-id="f30f3-124">Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.</span><span class="sxs-lookup"><span data-stu-id="f30f3-124">We recommend choosing a name that explains the purpose and target of the connection.</span></span>

1. <span data-ttu-id="f30f3-125">A kapcsolat használóinak kiválasztása.</span><span class="sxs-lookup"><span data-stu-id="f30f3-125">Choose who can use this connection.</span></span> <span data-ttu-id="f30f3-126">Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz.</span><span class="sxs-lookup"><span data-stu-id="f30f3-126">If you take no action, the default will be Administrators.</span></span> <span data-ttu-id="f30f3-127">További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).</span><span class="sxs-lookup"><span data-stu-id="f30f3-127">For more information, see [Allow contributors to use a connection for exports](connections.md#allow-contributors-to-use-a-connection-for-exports).</span></span>

1. <span data-ttu-id="f30f3-128">Adja meg **[Google Ads ügyfél-azonosítóját](https://support.google.com/google-ads/answer/1704344)**.</span><span class="sxs-lookup"><span data-stu-id="f30f3-128">Enter your **[Google Ads customer ID](https://support.google.com/google-ads/answer/1704344)**.</span></span>

1. <span data-ttu-id="f30f3-129">Adja meg **[a jóváhagyott Google Ads-fejlesztői jogkivonatát](https://developers.google.com/google-ads/api/docs/first-call/dev-token)**.</span><span class="sxs-lookup"><span data-stu-id="f30f3-129">Enter your **[Google Ads approved developer token](https://developers.google.com/google-ads/api/docs/first-call/dev-token)**.</span></span>

1. <span data-ttu-id="f30f3-130">Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.</span><span class="sxs-lookup"><span data-stu-id="f30f3-130">Select **I agree** to confirm the **Data privacy and compliance**.</span></span>

1. <span data-ttu-id="f30f3-131">Válassza a **Hitelesítés a Google Ads szolgáltatással** lehetőséget, és adja meg Google Ads-hitelesítő adatait.</span><span class="sxs-lookup"><span data-stu-id="f30f3-131">Select **Authenticate with Google Ads** and provide your Google Ads credentials.</span></span>

1. <span data-ttu-id="f30f3-132">Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.</span><span class="sxs-lookup"><span data-stu-id="f30f3-132">Select **Add yourself as export user** and provide your Customer Insights credentials.</span></span>

1. <span data-ttu-id="f30f3-133">A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="f30f3-133">Select **Save** to complete the connection.</span></span> 

## <a name="configure-an-export"></a><span data-ttu-id="f30f3-134">Exportálás konfigurálása</span><span class="sxs-lookup"><span data-stu-id="f30f3-134">Configure an export</span></span>

<span data-ttu-id="f30f3-135">Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz.</span><span class="sxs-lookup"><span data-stu-id="f30f3-135">You can configure this export if you have access to a connection of this type.</span></span> <span data-ttu-id="f30f3-136">További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).</span><span class="sxs-lookup"><span data-stu-id="f30f3-136">For more information, see [Permissions needed to configure an export](export-destinations.md#set-up-a-new-export).</span></span>

1. <span data-ttu-id="f30f3-137">Menjen az **Adatok** > **Exportálások** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="f30f3-137">Go to **Data** > **Exports**.</span></span>

1. <span data-ttu-id="f30f3-138">Új exportálás létrehozásához válassza a **Célhely hozzáadása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="f30f3-138">To create a new export, select **Add destination**.</span></span>

1. <span data-ttu-id="f30f3-139">A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot a Google Ads szakaszból.</span><span class="sxs-lookup"><span data-stu-id="f30f3-139">In the **Connection for export** field, choose a connection from the Google Ads section.</span></span> <span data-ttu-id="f30f3-140">Ha nem látja ezt a szakasznevet, akkor ilyen típusú kapcsolatok nem állnak az Ön rendelkezésére.</span><span class="sxs-lookup"><span data-stu-id="f30f3-140">If you don't see this section name, then no connections of this type are available to you.</span></span>

1. <span data-ttu-id="f30f3-141">Adja meg a **[Google Ads célközönség azonosítóját](https://support.google.com/google-ads/answer/7558048?hl=en#:~:text=Audience%20lists%20is%20a%20section,Display%20Network%20through%20remarketing%20campaigns.)**, és válassza a **Csatlakozás** lehetőséget a Google Ads-kapcsolat kezdeményezéséhez.</span><span class="sxs-lookup"><span data-stu-id="f30f3-141">Enter your **[Google Ads audience ID](https://support.google.com/google-ads/answer/7558048?hl=en#:~:text=Audience%20lists%20is%20a%20section,Display%20Network%20through%20remarketing%20campaigns.)** and select **Connect** to initialize the connection to Google Ads.</span></span>

1. <span data-ttu-id="f30f3-142">Az **Adategyeztetés** szakaszban az **E-mail** mezőben jelölje ki az egyesített ügyfélprofil ügyfél e-mail-címét jelképező mezőjét.</span><span class="sxs-lookup"><span data-stu-id="f30f3-142">In the **Data matching** section, in the **Email** field, select the field in your unified customer profile that represents a customer's email address.</span></span> <span data-ttu-id="f30f3-143">Ismételje meg ugyanezeket a lépéseket az **Utónév** és a **Vezetéknév** mezőkkel is.</span><span class="sxs-lookup"><span data-stu-id="f30f3-143">Repeat the same steps for **First name** and **Last name** fields.</span></span>

1. <span data-ttu-id="f30f3-144">Jelölje ki a szegmenseket, amelyeket exportálni szeretne.</span><span class="sxs-lookup"><span data-stu-id="f30f3-144">Select the segments you want to export.</span></span> <span data-ttu-id="f30f3-145">Összesen legfeljebb 1 000 000 ügyfélprofilt exportálhat a Google Adsbe.</span><span class="sxs-lookup"><span data-stu-id="f30f3-145">You can export up to 1 million customer profiles in total to Google Ads.</span></span>

<span data-ttu-id="f30f3-146">Az exportálás mentése nem futtatja azonnal az exportálást.</span><span class="sxs-lookup"><span data-stu-id="f30f3-146">Saving an export doesn't run the export immediately.</span></span>

<span data-ttu-id="f30f3-147">Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut.</span><span class="sxs-lookup"><span data-stu-id="f30f3-147">The export runs with every [scheduled refresh](system.md#schedule-tab).</span></span> 

<span data-ttu-id="f30f3-148">Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand).</span><span class="sxs-lookup"><span data-stu-id="f30f3-148">You can also [export data on demand](export-destinations.md#run-exports-on-demand).</span></span> 

## <a name="data-privacy-and-compliance"></a><span data-ttu-id="f30f3-149">Adatvédelem és megfelelőség</span><span class="sxs-lookup"><span data-stu-id="f30f3-149">Data privacy and compliance</span></span>

<span data-ttu-id="f30f3-150">Amikor engedélyezi a Dynamics 365 Customer Insights szolgáltatást az adatok Google Ads szolgáltatásba való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat.</span><span class="sxs-lookup"><span data-stu-id="f30f3-150">When you enable Dynamics 365 Customer Insights to transmit data to Google Ads, you allow transfer of data outside of the compliance boundary for Dynamics 365 Customer Insights, including potentially sensitive data such as Personal Data.</span></span> <span data-ttu-id="f30f3-151">A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy a Google Ads megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek.</span><span class="sxs-lookup"><span data-stu-id="f30f3-151">Microsoft will transfer such data at your instruction, but you are responsible for ensuring that Google Ads meet any privacy or security obligations you may have.</span></span> <span data-ttu-id="f30f3-152">További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).</span><span class="sxs-lookup"><span data-stu-id="f30f3-152">For more information, see [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?linkid=396732).</span></span>
<span data-ttu-id="f30f3-153">A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.</span><span class="sxs-lookup"><span data-stu-id="f30f3-153">Your Dynamics 365 Customer Insights administrator can remove this export destination at any time to discontinue use of this functionality.</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]
