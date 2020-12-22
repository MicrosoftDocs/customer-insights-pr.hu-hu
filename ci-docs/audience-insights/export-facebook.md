---
title: Customer Insights adatok exportálása a Facebook Ads Managerbe
description: Megismerkedhet vele, hogyan konfigurálható a Facebook hirdetéskezelő kapcsolata.
ms.date: 06/05/2020
ms.reviewer: philk
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: 8260e3b5e529f3d54678d9d6e11aebb2795e27fd
ms.sourcegitcommit: 6a6df62fa12dcb9bd5f5a39cc3ee0e2b3988184b
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/25/2020
ms.locfileid: "4643686"
---
# <a name="connector-for-facebook-ads-manager-preview"></a><span data-ttu-id="54731-103">A Facebook csatlakozója összekötője (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="54731-103">Connector for Facebook Ads Manager (preview)</span></span>

<span data-ttu-id="54731-104">Az egyesített ügyfélprofilokat tartalmazó szegmensek exportálása a Facebook hirdetéskezelőbe kampányok létrehozásához a Facebook-on és az Instagramon.</span><span class="sxs-lookup"><span data-stu-id="54731-104">Export segments of unified customer profiles to Facebook Ads Manager to create campaigns on Facebook and Instagram.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="54731-105">Előfeltételek</span><span class="sxs-lookup"><span data-stu-id="54731-105">Prerequisites</span></span>

- <span data-ttu-id="54731-106">Olyan [**Facebook hirdetési fiókkal**](https://www.facebook.com/business/learn/lessons/step-by-step-ads-manager-account) kell rendelkeznie, amely egy [**Facebook üzleti fiókot**](https://business.facebook.com/) is tartalmaz.</span><span class="sxs-lookup"><span data-stu-id="54731-106">You need to have a [**Facebook Ad Account**](https://www.facebook.com/business/learn/lessons/step-by-step-ads-manager-account) which includes a [**Facebook Business Account**](https://business.facebook.com/).</span></span>
- <span data-ttu-id="54731-107">A [**Facebook hirdetési fiók**](https://www.facebook.com/business/learn/lessons/step-by-step-ads-manager-account) rendszergazdájának kell lennie.</span><span class="sxs-lookup"><span data-stu-id="54731-107">You need to be an administrator on the [**Facebook Ad Account**](https://www.facebook.com/business/learn/lessons/step-by-step-ads-manager-account).</span></span>

## <a name="connect-to-facebook-ads-manager"></a><span data-ttu-id="54731-108">Kapcsolódás a Facebook hirdetéskezelőhöz</span><span class="sxs-lookup"><span data-stu-id="54731-108">Connect to Facebook Ads Manager</span></span>

1. <span data-ttu-id="54731-109">Válassz a **Rendszergazda** > **Célok exportálása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="54731-109">Go to **Admin** > **Export destinations**.</span></span>

1. <span data-ttu-id="54731-110">A **Facebook hirdetéskezelő** alatt válassza a **Beállítás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="54731-110">Under **Facebook Ads Manager**, select **Set up**.</span></span>

1. <span data-ttu-id="54731-111">Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben az export helyének.</span><span class="sxs-lookup"><span data-stu-id="54731-111">Give your export destination a recognizable name in the **Display name** field.</span></span>

1. <span data-ttu-id="54731-112">Válassza a **Folytatás Facebook-kal** lehetőséget a bejelentkezéshez a Facebook hirdetési fiókjába.</span><span class="sxs-lookup"><span data-stu-id="54731-112">Select **Continue with Facebook** to sign in to your Facebook Ad Account.</span></span>

1. <span data-ttu-id="54731-113">A hitelesítés után engedélyezze a **ads_management** engedélyt a Facebookkal.</span><span class="sxs-lookup"><span data-stu-id="54731-113">Allow the **ads_management** permission after authenticating with Facebook.</span></span>

1. <span data-ttu-id="54731-114">Válassza ki a **Facebook hirdetési fiókot**, amellyel dolgozni kíván.</span><span class="sxs-lookup"><span data-stu-id="54731-114">Select the **Facebook Ads Account** that you want to work with.</span></span>

1. <span data-ttu-id="54731-115">Jelöljön ki egy **Meglévő egyéni célközönséget** a legördülő listából, vagy hozzon létre egy **Új egyéni célközönséget**.</span><span class="sxs-lookup"><span data-stu-id="54731-115">Select an **Existing custom audience** from the drop-down list or create a **New custom audience**.</span></span> <span data-ttu-id="54731-116">További tájékoztatás [**Célközönségek a Facebook hirdetéskezelőben**](https://www.facebook.com/business/help/744354708981227?id=2469097953376494) című témakörben olvashat.</span><span class="sxs-lookup"><span data-stu-id="54731-116">For more information, see [**Audiences in Facebook Ads Manager**](https://www.facebook.com/business/help/744354708981227?id=2469097953376494).</span></span>

1. <span data-ttu-id="54731-117">Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.</span><span class="sxs-lookup"><span data-stu-id="54731-117">Select **I agree** to confirm the **Data privacy and compliance**.</span></span>

1. <span data-ttu-id="54731-118">Az Exportálás konfigurálásához válassza a **Tovább** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="54731-118">Select **Next** to configure the export.</span></span>

## <a name="configure-the-connector"></a><span data-ttu-id="54731-119">Konfigurálja az összekötőt</span><span class="sxs-lookup"><span data-stu-id="54731-119">Configure the connector</span></span>

1. <span data-ttu-id="54731-120">A **Kulcsazonosító kiválasztása** mezőben válassza az **E-mail-cím**, **Név és a cím** vagy a **Telefon** lehetőséget, amelyet elküld a Facebook hirdetéskezelőnek.</span><span class="sxs-lookup"><span data-stu-id="54731-120">In the **Choose your key identifier field**, select **Email**, **Name and address**, or **Phone** to send to Facebook Ads Manager.</span></span>

1. <span data-ttu-id="54731-121">Képezze le a megfelelő attribútumokat az egyesített ügyfél entitásból a kiválasztott kulcsazonosítóhoz.</span><span class="sxs-lookup"><span data-stu-id="54731-121">Map the corresponding attributes from your unified customer entity for the selected key identifier.</span></span>
   > <span data-ttu-id="54731-122">[Tipp] A legjobb esély akkor van az egyezésre, ha az **E-mail-cím** lehetőséget választja kulcsazonosítónak.</span><span class="sxs-lookup"><span data-stu-id="54731-122">[TIP] The best chances for a match occur if you select **Email** as key identifier.</span></span> <span data-ttu-id="54731-123">A további azonosítók hozzáadásával javíthatja a megfeleltetést.</span><span class="sxs-lookup"><span data-stu-id="54731-123">Adding additional identifiers may improve the matching.</span></span>

1. <span data-ttu-id="54731-124">Válassza az **Attribútum hozzáadása** lehetőséget , ha további attribútumokat szeretne leképezni a Facebook hirdetéskezelőnek.</span><span class="sxs-lookup"><span data-stu-id="54731-124">Select **Add attribute** to map additional attributes to send to Facebook Ads Manager.</span></span> <span data-ttu-id="54731-125">A Facebook Ads Manager a következő felhasználóbarát neveket használja a leképezéshez: **FN** = **Keresztnév**, **LN** = **Utónév**, **FI** = **Első kezdőbetű**, **PHONE** = **Telefon**, **GEN** = **Nem**, **DOB** = **Születési idő**, **ST** = **Állam**, **CT** = **Város**, **ZIP** = **Irányítószám**, **COUNTRY** = **Ország/régió**</span><span class="sxs-lookup"><span data-stu-id="54731-125">Attributes from Facebook Ads Manager are mapping to the following user friendly names: **FN** = **First Name**, **LN** = **Last Name**, **FI** = **First Initial**, **PHONE** = **Phone**, **GEN** = **Gender**, **DOB** = **Date of birth**, **ST** = **State**, **CT** = **City**, **ZIP** = **Postal code / Zip code**, **COUNTRY** = **Country / Region**</span></span>

1. <span data-ttu-id="54731-126">Jelölje ki a szegmenseket, amelyeket exportálni szeretne.</span><span class="sxs-lookup"><span data-stu-id="54731-126">Select the segments you want to export.</span></span>

1. <span data-ttu-id="54731-127">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="54731-127">Select **Save**.</span></span>

## <a name="export-the-data"></a><span data-ttu-id="54731-128">Az adatok exportálása</span><span class="sxs-lookup"><span data-stu-id="54731-128">Export the data</span></span>

<span data-ttu-id="54731-129">[Igény szerint exportálhatja az adatot](export-destinations.md).</span><span class="sxs-lookup"><span data-stu-id="54731-129">You can [export data on demand](export-destinations.md).</span></span> <span data-ttu-id="54731-130">Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) együtt is lefut.</span><span class="sxs-lookup"><span data-stu-id="54731-130">The export will also run with every [scheduled refresh](system.md#schedule-tab).</span></span>

## <a name="data-privacy-and-compliance"></a><span data-ttu-id="54731-131">Adatvédelem és megfelelőség</span><span class="sxs-lookup"><span data-stu-id="54731-131">Data privacy and compliance</span></span>

<span data-ttu-id="54731-132">Amikor engedélyezi a Dynamics 365 Customer Insights szolgáltatást az adatok Facebook Ads Managerbe való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat.</span><span class="sxs-lookup"><span data-stu-id="54731-132">When you enable Dynamics 365 Customer Insights to transmit data to Facebook Ads Manager, you allow transfer of data outside of the compliance boundary for Dynamics 365 Customer Insights, including potentially sensitive data such as Personal Data.</span></span> <span data-ttu-id="54731-133">A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy a Facebook Ads megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek.</span><span class="sxs-lookup"><span data-stu-id="54731-133">Microsoft will transfer such data at your instruction, but you are responsible for ensuring that Facebook Ads meet any privacy or security obligations you may have.</span></span> <span data-ttu-id="54731-134">További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).</span><span class="sxs-lookup"><span data-stu-id="54731-134">For more information, see [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?linkid=396732).</span></span>
<span data-ttu-id="54731-135">A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.</span><span class="sxs-lookup"><span data-stu-id="54731-135">Your Dynamics 365 Customer Insights Administrator can remove this export destination at any time to discontinue use of this functionality.</span></span>
