---
title: Customer Insights adatok exportálása a Facebook Ads Managerbe
description: Megismerkedhet vele, hogyan konfigurálható a Facebook hirdetéskezelő kapcsolata.
ms.date: 06/05/2020
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: phkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 3e2b52fe743563e4bf61d870cbf1718e6c752a67
ms.sourcegitcommit: bae40184312ab27b95c140a044875c2daea37951
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/15/2021
ms.locfileid: "5596685"
---
# <a name="connector-for-facebook-ads-manager-preview"></a><span data-ttu-id="bace1-103">A Facebook csatlakozója összekötője (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="bace1-103">Connector for Facebook Ads Manager (preview)</span></span>

<span data-ttu-id="bace1-104">Az egyesített ügyfélprofilokat tartalmazó szegmensek exportálása a Facebook hirdetéskezelőbe kampányok létrehozásához a Facebook-on és az Instagramon.</span><span class="sxs-lookup"><span data-stu-id="bace1-104">Export segments of unified customer profiles to Facebook Ads Manager to create campaigns on Facebook and Instagram.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="bace1-105">Előfeltételek</span><span class="sxs-lookup"><span data-stu-id="bace1-105">Prerequisites</span></span>

- <span data-ttu-id="bace1-106">Olyan [**Facebook hirdetési fiókkal**](https://www.facebook.com/business/learn/lessons/step-by-step-ads-manager-account) kell rendelkeznie, amely egy [**Facebook üzleti fiókot**](https://business.facebook.com/) is tartalmaz.</span><span class="sxs-lookup"><span data-stu-id="bace1-106">You need to have a [**Facebook Ad Account**](https://www.facebook.com/business/learn/lessons/step-by-step-ads-manager-account) which includes a [**Facebook Business Account**](https://business.facebook.com/).</span></span>
- <span data-ttu-id="bace1-107">A [**Facebook hirdetési fiók**](https://www.facebook.com/business/learn/lessons/step-by-step-ads-manager-account) rendszergazdájának kell lennie.</span><span class="sxs-lookup"><span data-stu-id="bace1-107">You need to be an administrator on the [**Facebook Ad Account**](https://www.facebook.com/business/learn/lessons/step-by-step-ads-manager-account).</span></span>

## <a name="connect-to-facebook-ads-manager"></a><span data-ttu-id="bace1-108">Kapcsolódás a Facebook hirdetéskezelőhöz</span><span class="sxs-lookup"><span data-stu-id="bace1-108">Connect to Facebook Ads Manager</span></span>

1. <span data-ttu-id="bace1-109">Válassz a **Rendszergazda** > **Célok exportálása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="bace1-109">Go to **Admin** > **Export destinations**.</span></span>

1. <span data-ttu-id="bace1-110">A **Facebook hirdetéskezelő** alatt válassza a **Beállítás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="bace1-110">Under **Facebook Ads Manager**, select **Set up**.</span></span>

1. <span data-ttu-id="bace1-111">Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben az export helyének.</span><span class="sxs-lookup"><span data-stu-id="bace1-111">Give your export destination a recognizable name in the **Display name** field.</span></span>

1. <span data-ttu-id="bace1-112">Válassza a **Folytatás Facebook-kal** lehetőséget a bejelentkezéshez a Facebook hirdetési fiókjába.</span><span class="sxs-lookup"><span data-stu-id="bace1-112">Select **Continue with Facebook** to sign in to your Facebook Ad Account.</span></span>

1. <span data-ttu-id="bace1-113">A hitelesítés után engedélyezze a **ads_management** engedélyt a Facebookkal.</span><span class="sxs-lookup"><span data-stu-id="bace1-113">Allow the **ads_management** permission after authenticating with Facebook.</span></span>

1. <span data-ttu-id="bace1-114">Válassza ki a **Facebook hirdetési fiókot**, amellyel dolgozni kíván.</span><span class="sxs-lookup"><span data-stu-id="bace1-114">Select the **Facebook Ads Account** that you want to work with.</span></span>

1. <span data-ttu-id="bace1-115">Jelöljön ki egy **Meglévő egyéni célközönséget** a legördülő listából, vagy hozzon létre egy **Új egyéni célközönséget**.</span><span class="sxs-lookup"><span data-stu-id="bace1-115">Select an **Existing custom audience** from the drop-down list or create a **New custom audience**.</span></span> <span data-ttu-id="bace1-116">További tájékoztatás [**Célközönségek a Facebook hirdetéskezelőben**](https://www.facebook.com/business/help/744354708981227?id=2469097953376494) című témakörben olvashat.</span><span class="sxs-lookup"><span data-stu-id="bace1-116">For more information, see [**Audiences in Facebook Ads Manager**](https://www.facebook.com/business/help/744354708981227?id=2469097953376494).</span></span>

1. <span data-ttu-id="bace1-117">Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.</span><span class="sxs-lookup"><span data-stu-id="bace1-117">Select **I agree** to confirm the **Data privacy and compliance**.</span></span>

1. <span data-ttu-id="bace1-118">Az Exportálás konfigurálásához válassza a **Tovább** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="bace1-118">Select **Next** to configure the export.</span></span>

## <a name="configure-the-connector"></a><span data-ttu-id="bace1-119">Konfigurálja az összekötőt</span><span class="sxs-lookup"><span data-stu-id="bace1-119">Configure the connector</span></span>

1. <span data-ttu-id="bace1-120">A **Kulcsazonosító kiválasztása** mezőben válassza az **E-mail-cím**, **Név és a cím** vagy a **Telefon** lehetőséget, amelyet elküld a Facebook hirdetéskezelőnek.</span><span class="sxs-lookup"><span data-stu-id="bace1-120">In the **Choose your key identifier field**, select **Email**, **Name and address**, or **Phone** to send to Facebook Ads Manager.</span></span>

1. <span data-ttu-id="bace1-121">Képezze le a megfelelő attribútumokat az egyesített ügyfél entitásból a kiválasztott kulcsazonosítóhoz.</span><span class="sxs-lookup"><span data-stu-id="bace1-121">Map the corresponding attributes from your unified customer entity for the selected key identifier.</span></span>
   > <span data-ttu-id="bace1-122">[Tipp] A legjobb esély akkor van az egyezésre, ha az **E-mail-cím** lehetőséget választja kulcsazonosítónak.</span><span class="sxs-lookup"><span data-stu-id="bace1-122">[TIP] The best chances for a match occur if you select **Email** as key identifier.</span></span> <span data-ttu-id="bace1-123">A további azonosítók hozzáadásával javíthatja a megfeleltetést.</span><span class="sxs-lookup"><span data-stu-id="bace1-123">Adding additional identifiers may improve the matching.</span></span>

1. <span data-ttu-id="bace1-124">Válassza az **Attribútum hozzáadása** lehetőséget , ha további attribútumokat szeretne leképezni a Facebook hirdetéskezelőnek.</span><span class="sxs-lookup"><span data-stu-id="bace1-124">Select **Add attribute** to map additional attributes to send to Facebook Ads Manager.</span></span> <span data-ttu-id="bace1-125">A Facebook Ads Manager a következő felhasználóbarát neveket használja a leképezéshez: **FN** = **Keresztnév**, **LN** = **Utónév**, **FI** = **Első kezdőbetű**, **PHONE** = **Telefon**, **GEN** = **Nem**, **DOB** = **Születési idő**, **ST** = **Állam**, **CT** = **Város**, **ZIP** = **Irányítószám**, **COUNTRY** = **Ország/régió**</span><span class="sxs-lookup"><span data-stu-id="bace1-125">Attributes from Facebook Ads Manager are mapping to the following user friendly names: **FN** = **First Name**, **LN** = **Last Name**, **FI** = **First Initial**, **PHONE** = **Phone**, **GEN** = **Gender**, **DOB** = **Date of birth**, **ST** = **State**, **CT** = **City**, **ZIP** = **Postal code / Zip code**, **COUNTRY** = **Country / Region**</span></span>

1. <span data-ttu-id="bace1-126">Jelölje ki a szegmenseket, amelyeket exportálni szeretne.</span><span class="sxs-lookup"><span data-stu-id="bace1-126">Select the segments you want to export.</span></span>

1. <span data-ttu-id="bace1-127">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="bace1-127">Select **Save**.</span></span>

## <a name="export-the-data"></a><span data-ttu-id="bace1-128">Az adatok exportálása</span><span class="sxs-lookup"><span data-stu-id="bace1-128">Export the data</span></span>

<span data-ttu-id="bace1-129">[Igény szerint exportálhatja az adatot](export-destinations.md).</span><span class="sxs-lookup"><span data-stu-id="bace1-129">You can [export data on demand](export-destinations.md).</span></span> <span data-ttu-id="bace1-130">Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) együtt is lefut.</span><span class="sxs-lookup"><span data-stu-id="bace1-130">The export will also run with every [scheduled refresh](system.md#schedule-tab).</span></span>

## <a name="known-limitations"></a><span data-ttu-id="bace1-131">Ismert korlátozások</span><span class="sxs-lookup"><span data-stu-id="bace1-131">Known limitations</span></span>

- <span data-ttu-id="bace1-132">Akár 10 millió ügyfélprofil exportálásonként a Facebook Hirdetéskezelőbe</span><span class="sxs-lookup"><span data-stu-id="bace1-132">Up to 10 million customer profile per export to Facebook Ads Manager</span></span> 
- <span data-ttu-id="bace1-133">A Facebook hirdetéskezelőbe való exportálás csak szegmensekre korlátozódik</span><span class="sxs-lookup"><span data-stu-id="bace1-133">Export to Facebook Ads Manager is limited to segments</span></span>
- <span data-ttu-id="bace1-134">Az összesen 10 millió profillal rendelkező szegmensek exportálása akár 90 percig is eltarthat</span><span class="sxs-lookup"><span data-stu-id="bace1-134">Exporting segments with a total of 10 million profiles can take up to 90 minutes to complete</span></span>

## <a name="data-privacy-and-compliance"></a><span data-ttu-id="bace1-135">Adatvédelem és megfelelőség</span><span class="sxs-lookup"><span data-stu-id="bace1-135">Data privacy and compliance</span></span>

<span data-ttu-id="bace1-136">Amikor engedélyezi a Dynamics 365 Customer Insights szolgáltatást az adatok Facebook Ads Managerbe való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat.</span><span class="sxs-lookup"><span data-stu-id="bace1-136">When you enable Dynamics 365 Customer Insights to transmit data to Facebook Ads Manager, you allow transfer of data outside of the compliance boundary for Dynamics 365 Customer Insights, including potentially sensitive data such as Personal Data.</span></span> <span data-ttu-id="bace1-137">A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy a Facebook Ads megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek.</span><span class="sxs-lookup"><span data-stu-id="bace1-137">Microsoft will transfer such data at your instruction, but you are responsible for ensuring that Facebook Ads meet any privacy or security obligations you may have.</span></span> <span data-ttu-id="bace1-138">További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).</span><span class="sxs-lookup"><span data-stu-id="bace1-138">For more information, see [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?linkid=396732).</span></span>
<span data-ttu-id="bace1-139">A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.</span><span class="sxs-lookup"><span data-stu-id="bace1-139">Your Dynamics 365 Customer Insights Administrator can remove this export destination at any time to discontinue use of this functionality.</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]