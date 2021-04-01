---
title: Customer Insights adatok exportálása a Google Adsbe
description: Megismerheti, hogyan konfigurálható a kapcsolat a Google Adsszal.
ms.date: 11/18/2020
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: phkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 6d9a25af3913e755cccec745c532b35aef3cccf9
ms.sourcegitcommit: bae40184312ab27b95c140a044875c2daea37951
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/15/2021
ms.locfileid: "5598250"
---
# <a name="connector-for-google-ads-preview"></a><span data-ttu-id="394ef-103">A Google Ads összekötője (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="394ef-103">Connector for Google Ads (preview)</span></span>

<span data-ttu-id="394ef-104">Exportáljon egyéni ügyfélprofilok szegmenseit a Google Ads célközönséglistába, és használja ezeket a hirdetésekhez a Google Kereső, a Gmail, a YouTube és a Google Display Network felületén.</span><span class="sxs-lookup"><span data-stu-id="394ef-104">Export segments of unified customer profiles to Google Ads audience list and use them to advertise on Google Search, Gmail, YouTube, and Google Display Network.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="394ef-105">Előfeltételek</span><span class="sxs-lookup"><span data-stu-id="394ef-105">Prerequisites</span></span>

-   <span data-ttu-id="394ef-106">Rendelkezik [Google Ads-fiókkal](https://ads.google.com/) és a megfelelő rendszergazdai hitelesítő adatokkal.</span><span class="sxs-lookup"><span data-stu-id="394ef-106">You have a [Google Ads account](https://ads.google.com/) and corresponding administrator credentials.</span></span>
-   <span data-ttu-id="394ef-107">A Google Adsban és a megfelelő azonosítókban meglévő célközönségek találhatók.</span><span class="sxs-lookup"><span data-stu-id="394ef-107">There are existing audiences in Google Ads and the corresponding IDs.</span></span> <span data-ttu-id="394ef-108">További információért lásd: [Google Ads-célközönségek](https://support.google.com/google-ads/answer/7558048?hl=en#:~:text=Audience%20lists%20is%20a%20section,Display%20Network%20through%20remarketing%20campaigns.).</span><span class="sxs-lookup"><span data-stu-id="394ef-108">For more information, see [Google Ads audiences](https://support.google.com/google-ads/answer/7558048?hl=en#:~:text=Audience%20lists%20is%20a%20section,Display%20Network%20through%20remarketing%20campaigns.).</span></span>
-   <span data-ttu-id="394ef-109">Rendelkezik [konfigurált szegmensekkel](segments.md)</span><span class="sxs-lookup"><span data-stu-id="394ef-109">You have [configured segments](segments.md)</span></span>
-   <span data-ttu-id="394ef-110">Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőket, amelyek az e-mail-címet, utónevet és vezetéknevet tartalmazzák</span><span class="sxs-lookup"><span data-stu-id="394ef-110">Unified customer profiles in the exported segments contain fields representing an email address, first name, and last name</span></span>

## <a name="connect-to-google-ads"></a><span data-ttu-id="394ef-111">Csatlakozás a Google Ads szolgáltatáshoz</span><span class="sxs-lookup"><span data-stu-id="394ef-111">Connect to Google Ads</span></span>

1. <span data-ttu-id="394ef-112">Válassz a **Rendszergazda** > **Célok exportálása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="394ef-112">Go to **Admin** > **Export destinations**.</span></span>

1. <span data-ttu-id="394ef-113">A **Google Ads** részben válassza a **Beállítás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="394ef-113">Under **Google Ads**, select **Set up**.</span></span>

1. <span data-ttu-id="394ef-114">Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben az export helyének.</span><span class="sxs-lookup"><span data-stu-id="394ef-114">Give your export destination a recognizable name in the **Display name** field.</span></span>

1. <span data-ttu-id="394ef-115">Adja meg **[Google Ads ügyfél-azonosítóját](https://support.google.com/google-ads/answer/1704344)**.</span><span class="sxs-lookup"><span data-stu-id="394ef-115">Enter your **[Google Ads customer ID](https://support.google.com/google-ads/answer/1704344)**.</span></span>

1. <span data-ttu-id="394ef-116">Adja meg **[a jóváhagyott Google Ads-fejlesztői jogkivonatát](https://developers.google.com/google-ads/api/docs/first-call/dev-token)**.</span><span class="sxs-lookup"><span data-stu-id="394ef-116">Enter your **[Google Ads approved developer token](https://developers.google.com/google-ads/api/docs/first-call/dev-token)**.</span></span>

1. <span data-ttu-id="394ef-117">Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.</span><span class="sxs-lookup"><span data-stu-id="394ef-117">Select **I agree** to confirm the **Data privacy and compliance**.</span></span>

1. <span data-ttu-id="394ef-118">Adja meg a **[Google Ads célközönség azonosítóját](https://support.google.com/google-ads/answer/7558048?hl=en#:~:text=Audience%20lists%20is%20a%20section,Display%20Network%20through%20remarketing%20campaigns.)**, és válassza a **Csatlakozás** lehetőséget a Google Ads-kapcsolat kezdeményezéséhez.</span><span class="sxs-lookup"><span data-stu-id="394ef-118">Enter your **[Google Ads audience ID](https://support.google.com/google-ads/answer/7558048?hl=en#:~:text=Audience%20lists%20is%20a%20section,Display%20Network%20through%20remarketing%20campaigns.)** and select **Connect** to initialize the connection to Google Ads.</span></span>

1. <span data-ttu-id="394ef-119">Válassza a **Hitelesítés a Google Ads szolgáltatással** lehetőséget, és adja meg Google Ads-hitelesítő adatait.</span><span class="sxs-lookup"><span data-stu-id="394ef-119">Select **Authenticate with Google Ads** and provide your Google Ads credentials.</span></span>

1. <span data-ttu-id="394ef-120">Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.</span><span class="sxs-lookup"><span data-stu-id="394ef-120">Select **Add yourself as export user** and provide your Customer Insights credentials.</span></span>

   :::image type="content" source="media/export-segments-googleads.PNG" alt-text="Képernyőkép exportálása a Google Ads kapcsolatához":::

1. <span data-ttu-id="394ef-122">Az Exportálás konfigurálásához válassza a **Tovább** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="394ef-122">Select **Next** to configure the export.</span></span>

## <a name="configure-the-connector"></a><span data-ttu-id="394ef-123">Konfigurálja az összekötőt</span><span class="sxs-lookup"><span data-stu-id="394ef-123">Configure the connector</span></span>

1. <span data-ttu-id="394ef-124">Az **Adategyeztetés** szakaszban az **E-mail** mezőben jelölje ki az egyesített ügyfélprofil ügyfél e-mail-címét jelképező mezőjét.</span><span class="sxs-lookup"><span data-stu-id="394ef-124">In the **Data matching** section, in the **Email** field, select the field in your unified customer profile that represents a customer's email address.</span></span> <span data-ttu-id="394ef-125">Ismételje meg ugyanezeket a lépéseket az **Utónév** és a **Vezetéknév** mezőkkel is.</span><span class="sxs-lookup"><span data-stu-id="394ef-125">Repeat the same steps for \*\*First name" and **Last name** fields.</span></span>

1. <span data-ttu-id="394ef-126">Jelölje ki a szegmenseket, amelyeket exportálni szeretne.</span><span class="sxs-lookup"><span data-stu-id="394ef-126">Select the segments you want to export.</span></span> <span data-ttu-id="394ef-127">Összesen legfeljebb 1 000 000 ügyfélprofilt exportálhat a Google Adsbe.</span><span class="sxs-lookup"><span data-stu-id="394ef-127">You can export up to 1 million customer profiles in total to Google Ads.</span></span>

1. <span data-ttu-id="394ef-128">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="394ef-128">Select **Save**.</span></span>

## <a name="export-the-data"></a><span data-ttu-id="394ef-129">Az adatok exportálása</span><span class="sxs-lookup"><span data-stu-id="394ef-129">Export the data</span></span>

<span data-ttu-id="394ef-130">[Igény szerint exportálhatja az adatot](export-destinations.md).</span><span class="sxs-lookup"><span data-stu-id="394ef-130">You can [export data on demand](export-destinations.md).</span></span> <span data-ttu-id="394ef-131">Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) együtt is lefut.</span><span class="sxs-lookup"><span data-stu-id="394ef-131">The export will also run with every [scheduled refresh](system.md#schedule-tab).</span></span> <span data-ttu-id="394ef-132">A Google Adsben most már megtalálhatja a szegmenseket a [Google Ads célközönségei](https://support.google.com/google-ads/answer/7558048?hl=en/) között.</span><span class="sxs-lookup"><span data-stu-id="394ef-132">In Google Ads, you can now find your segments under [Google Ads audiences](https://support.google.com/google-ads/answer/7558048?hl=en/).</span></span>

## <a name="known-limitations"></a><span data-ttu-id="394ef-133">Ismert korlátozások</span><span class="sxs-lookup"><span data-stu-id="394ef-133">Known limitations</span></span>

- <span data-ttu-id="394ef-134">Legfeljebb 1 000 000 profilt exportálhat egyszerre a Google Adsbe.</span><span class="sxs-lookup"><span data-stu-id="394ef-134">Up to 1 million profiles per export to Google Ads.</span></span>
- <span data-ttu-id="394ef-135">A Google Adsbe való exportálás csak szegmensekre korlátozódik.</span><span class="sxs-lookup"><span data-stu-id="394ef-135">Exporting to Google Ads is limited to segments.</span></span>
- <span data-ttu-id="394ef-136">Az összesen 1 000 000 profillal rendelkező szegmens exportálása a szolgáltatói oldalon megjelenő korlátozások miatt akár 5 percig is eltarthat.</span><span class="sxs-lookup"><span data-stu-id="394ef-136">Exporting segments with a total of 1 million profiles can take up to 5 minutes because of limitations on the provider side.</span></span> 
- <span data-ttu-id="394ef-137">A Google Ads egyeztetése akár 48 óráig is eltarthat.</span><span class="sxs-lookup"><span data-stu-id="394ef-137">The matching in Google Ads can take up to 48 hours.</span></span>

## <a name="data-privacy-and-compliance"></a><span data-ttu-id="394ef-138">Adatvédelem és megfelelőség</span><span class="sxs-lookup"><span data-stu-id="394ef-138">Data privacy and compliance</span></span>

<span data-ttu-id="394ef-139">Amikor engedélyezi a Dynamics 365 Customer Insights szolgáltatást az adatok Google Ads szolgáltatásba való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat.</span><span class="sxs-lookup"><span data-stu-id="394ef-139">When you enable Dynamics 365 Customer Insights to transmit data to Google Ads, you allow transfer of data outside of the compliance boundary for Dynamics 365 Customer Insights, including potentially sensitive data such as Personal Data.</span></span> <span data-ttu-id="394ef-140">A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy a Google Ads megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek.</span><span class="sxs-lookup"><span data-stu-id="394ef-140">Microsoft will transfer such data at your instruction, but you are responsible for ensuring that Google Ads meet any privacy or security obligations you may have.</span></span> <span data-ttu-id="394ef-141">További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).</span><span class="sxs-lookup"><span data-stu-id="394ef-141">For more information, see [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?linkid=396732).</span></span>
<span data-ttu-id="394ef-142">A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.</span><span class="sxs-lookup"><span data-stu-id="394ef-142">Your Dynamics 365 Customer Insights Administrator can remove this export destination at any time to discontinue use of this functionality.</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]