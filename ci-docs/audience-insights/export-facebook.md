---
title: Customer Insights adatok exportálása a Facebook Ads Managerbe
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a Facebook Hirdetéskezelő.
ms.date: 04/15/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: e20c7b7fd3989d7621cb7765f38b85c8ab4adfcb
ms.sourcegitcommit: d84d664e67f263bfeb741154d309088c5101b9c3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/24/2021
ms.locfileid: "6305113"
---
# <a name="export-segments-list-to-facebook-ads-manager-preview"></a><span data-ttu-id="d46eb-103">Szegmenslista exportálása a Facebook Hirdetéskezelő (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="d46eb-103">Export segments list to Facebook Ads Manager (preview)</span></span>

<span data-ttu-id="d46eb-104">Az egyesített ügyfélprofilokat tartalmazó szegmensek exportálása a Facebook hirdetéskezelőbe kampányok létrehozásához a Facebook-on és az Instagramon.</span><span class="sxs-lookup"><span data-stu-id="d46eb-104">Export segments of unified customer profiles to Facebook Ads Manager to create campaigns on Facebook and Instagram.</span></span>

## <a name="prerequisites-for-connection"></a><span data-ttu-id="d46eb-105">A kapcsolat előfeltételei</span><span class="sxs-lookup"><span data-stu-id="d46eb-105">Prerequisites for connection</span></span>

- <span data-ttu-id="d46eb-106">Rendelkeznie kell egy [**Facebook hirdetési fiókkal**](https://www.facebook.com/business/learn/lessons/step-by-step-ads-manager-account) amely tartalmaz egy [**Facebook üzleti fiókot**](https://business.facebook.com/).</span><span class="sxs-lookup"><span data-stu-id="d46eb-106">You need to have a [**Facebook Ads Account**](https://www.facebook.com/business/learn/lessons/step-by-step-ads-manager-account) that includes a [**Facebook Business Account**](https://business.facebook.com/).</span></span>
- <span data-ttu-id="d46eb-107">Rendszergazdának kell lennie a [**Facebook hirdetési fiókban**](https://www.facebook.com/business/learn/lessons/step-by-step-ads-manager-account).</span><span class="sxs-lookup"><span data-stu-id="d46eb-107">You need to be an administrator on the [**Facebook Ads Account**](https://www.facebook.com/business/learn/lessons/step-by-step-ads-manager-account).</span></span>

## <a name="known-limitations"></a><span data-ttu-id="d46eb-108">Ismert korlátozások</span><span class="sxs-lookup"><span data-stu-id="d46eb-108">Known limitations</span></span>

- <span data-ttu-id="d46eb-109">Exportálásonként legfeljebb 10 millió ügyfélprofilt lehet a Facebook hirdetéskezelőbe exportálni.</span><span class="sxs-lookup"><span data-stu-id="d46eb-109">Up to 10 million customer profiles per export to Facebook Ads Manager.</span></span>
- <span data-ttu-id="d46eb-110">A Facebook hirdetéskezelőbe való exportálás csak szegmensekre korlátozódik.</span><span class="sxs-lookup"><span data-stu-id="d46eb-110">Export to Facebook Ads Manager is limited to segments.</span></span>
- <span data-ttu-id="d46eb-111">Kizárólag *ügyféllista* típusú célközönségek létrehozása vagy frissítése a Facebookon.</span><span class="sxs-lookup"><span data-stu-id="d46eb-111">Create or update custom audiences in Facebook of type *customer list* only.</span></span>
- <span data-ttu-id="d46eb-112">Az összesen 10 millió profillal rendelkező szegmensek exportálása akár 90 percig is eltarthat.</span><span class="sxs-lookup"><span data-stu-id="d46eb-112">Exporting segments with a total of 10 million profiles can take up to 90 minutes to complete.</span></span>

## <a name="set-up-connection-to-facebook-ads-manager"></a><span data-ttu-id="d46eb-113">Kapcsolat beállítása a Facebook Hirdetéskezelőhöz</span><span class="sxs-lookup"><span data-stu-id="d46eb-113">Set up connection to Facebook Ads Manager</span></span>

<span data-ttu-id="d46eb-114">Ahhoz, hogy a felhasználók exportálást tudjanak létrehozni, a rendszergazdának konfigurálnia kell a szolgáltatás kapcsolatát, és engedélyeznie kell a közreműködőknek a kapcsolat használatát.</span><span class="sxs-lookup"><span data-stu-id="d46eb-114">Before users can create an export, an administrator must configure the connection to the service and allow contributors to use the connection.</span></span>

1. <span data-ttu-id="d46eb-115">Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="d46eb-115">Go to **Admin** > **Connections**.</span></span>

1. <span data-ttu-id="d46eb-116">Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza a **Facebook Hirdetéskezelő** lehetőséget a kapcsolat konfigurálásához.</span><span class="sxs-lookup"><span data-stu-id="d46eb-116">Select **Add connection** and choose **Facebook Ads Manager** to configure the connection.</span></span>

1. <span data-ttu-id="d46eb-117">Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak.</span><span class="sxs-lookup"><span data-stu-id="d46eb-117">Give your connection a recognizable name in the **Display name** field.</span></span> <span data-ttu-id="d46eb-118">A név és a kapcsolat típusa írja le ezt a kapcsolatot.</span><span class="sxs-lookup"><span data-stu-id="d46eb-118">The name and the type of the connection describe this connection.</span></span> <span data-ttu-id="d46eb-119">Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.</span><span class="sxs-lookup"><span data-stu-id="d46eb-119">We recommend choosing a name that explains the purpose and target of the connection.</span></span>

1. <span data-ttu-id="d46eb-120">A kapcsolat használóinak kiválasztása.</span><span class="sxs-lookup"><span data-stu-id="d46eb-120">Choose who can use this connection.</span></span> <span data-ttu-id="d46eb-121">Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz.</span><span class="sxs-lookup"><span data-stu-id="d46eb-121">If you take no action, the default will be Administrators.</span></span> <span data-ttu-id="d46eb-122">További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).</span><span class="sxs-lookup"><span data-stu-id="d46eb-122">For more information, see [Allow contributors to use a connection for exports](connections.md#allow-contributors-to-use-a-connection-for-exports).</span></span>

1. <span data-ttu-id="d46eb-123">Hitelesítés a Facebook-hirdetések használatával:</span><span class="sxs-lookup"><span data-stu-id="d46eb-123">Authenticate with Facebook Ads:</span></span> 

   1. <span data-ttu-id="d46eb-124">A **Folytatás Facebook** gomb kiválasztásával jelentkezzen be a Facebook hirdetési fiókjába.</span><span class="sxs-lookup"><span data-stu-id="d46eb-124">Select **Continue with Facebook** to sign in to your Facebook Ads account.</span></span>

   1. <span data-ttu-id="d46eb-125">A hitelesítés után engedélyezze a **ads_management** engedélyt a Facebookkal.</span><span class="sxs-lookup"><span data-stu-id="d46eb-125">Allow the **ads_management** permission after authenticating with Facebook.</span></span>

   1. <span data-ttu-id="d46eb-126">Válassza ki a **Facebook hirdetési fiókot**, amellyel dolgozni kíván.</span><span class="sxs-lookup"><span data-stu-id="d46eb-126">Select the **Facebook Ads Account** that you want to work with.</span></span>

   1. <span data-ttu-id="d46eb-127">Válasszon egy **meglévő egyéni célközönséget** a legördülő listából, vagy hozzon létre egy **új egyéni célközönséget**.</span><span class="sxs-lookup"><span data-stu-id="d46eb-127">Select an **Existing custom audience** from the dropdown list or create a **New custom audience**.</span></span> <span data-ttu-id="d46eb-128">További tájékoztatás [**Célközönségek a Facebook hirdetéskezelőben**](https://www.facebook.com/business/help/744354708981227?id=2469097953376494) című témakörben olvashat.</span><span class="sxs-lookup"><span data-stu-id="d46eb-128">For more information, see [**Audiences in Facebook Ads Manager**](https://www.facebook.com/business/help/744354708981227?id=2469097953376494).</span></span>
      > [!NOTE]
      > <span data-ttu-id="d46eb-129">Ezzel az exportálással a Facebookon csak az adott típusú *ügyféllistán* hozhatók létre vagy frissíthetők egyéni célközönségek.</span><span class="sxs-lookup"><span data-stu-id="d46eb-129">You can only create or update custom audiences on Facebook of the type *customer list* with this export.</span></span> <span data-ttu-id="d46eb-130">Bizonyos esetekben a legördülő listában különféle típusú egyéni célközönségek láthatóak.</span><span class="sxs-lookup"><span data-stu-id="d46eb-130">In some cases, you see custom audiences of different types in the dropdown list.</span></span> <span data-ttu-id="d46eb-131">Ha az *ügyféllistától* eltérő típust választ, akkor az exportálás sikertelen lesz.</span><span class="sxs-lookup"><span data-stu-id="d46eb-131">Selecting a different type than *customer list* will result in a failing export.</span></span> 

1. <span data-ttu-id="d46eb-132">Tekintse át az **Adatvédelem és a megfelelés** lehetőséget, és válassza az **Elfogadom** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="d46eb-132">Review the **Data privacy and compliance** and select **I agree**.</span></span>

1. <span data-ttu-id="d46eb-133">A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="d46eb-133">Select **Save** to complete the connection.</span></span>

## <a name="configure-an-export"></a><span data-ttu-id="d46eb-134">Exportálás konfigurálása</span><span class="sxs-lookup"><span data-stu-id="d46eb-134">Configure an export</span></span>

<span data-ttu-id="d46eb-135">Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz.</span><span class="sxs-lookup"><span data-stu-id="d46eb-135">You can configure this export if you have access to a connection of this type.</span></span> <span data-ttu-id="d46eb-136">További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).</span><span class="sxs-lookup"><span data-stu-id="d46eb-136">For more information, see [Permissions needed to configure an export](export-destinations.md#set-up-a-new-export).</span></span>

1. <span data-ttu-id="d46eb-137">Menjen az **Adatok** > **Exportálások** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="d46eb-137">Go to **Data** > **Exports**.</span></span>

1. <span data-ttu-id="d46eb-138">Új exportálás létrehozásához válassza a **Célhely hozzáadása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="d46eb-138">To create a new export, select **Add destination**.</span></span> 

1. <span data-ttu-id="d46eb-139">A **Kapcsolat exportáláshoz** lehetőségen válasszon egy kapcsolatot a **Facebook hirdetéskezelőből**.</span><span class="sxs-lookup"><span data-stu-id="d46eb-139">In **Connection for export** choose a connection from the **Facebook Ads Manager** section.</span></span> <span data-ttu-id="d46eb-140">Ha nem látja ezt a szakasznevet, akkor ilyen típusú kapcsolatok nem állnak az Ön rendelkezésére.</span><span class="sxs-lookup"><span data-stu-id="d46eb-140">If you don't see this section name, then no connections of this type are available to you.</span></span>

1. <span data-ttu-id="d46eb-141">A **Kulcsazonosító kiválasztása** mezőben válassza az **E-mail-cím**, **Név és a cím** vagy a **Telefon** lehetőséget, amelyet elküld a Facebook hirdetéskezelőnek.</span><span class="sxs-lookup"><span data-stu-id="d46eb-141">In the **Choose your key identifier field**, select **Email**, **Name and address**, or **Phone** to send to Facebook Ads Manager.</span></span> 

1. <span data-ttu-id="d46eb-142">Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak.</span><span class="sxs-lookup"><span data-stu-id="d46eb-142">Give your connection a recognizable name in the **Display name** field.</span></span>

1. <span data-ttu-id="d46eb-143">Képezze le a megfelelő attribútumokat az egyesített ügyfél entitásból a kiválasztott kulcsazonosítóhoz.</span><span class="sxs-lookup"><span data-stu-id="d46eb-143">Map the corresponding attributes from your unified customer entity for the selected key identifier.</span></span>
   > [!TIP]
   > <span data-ttu-id="d46eb-144">A legjobb esély akkor van az egyezésre, ha az **E-mail-cím** lehetőséget választja kulcsazonosítónak.</span><span class="sxs-lookup"><span data-stu-id="d46eb-144">The best chances for a match occur if you select **Email** as key identifier.</span></span> <span data-ttu-id="d46eb-145">A további azonosítók hozzáadásával javíthatja a megfeleltetést.</span><span class="sxs-lookup"><span data-stu-id="d46eb-145">Adding additional identifiers may improve the matching.</span></span>

1. <span data-ttu-id="d46eb-146">Válassza az **Attribútum hozzáadása** lehetőséget a több attribútum leképzésének Facebook hirdetéskezelőbe küldéséhez.</span><span class="sxs-lookup"><span data-stu-id="d46eb-146">Select **Add attribute** to map more attributes to send to Facebook Ads Manager.</span></span> <span data-ttu-id="d46eb-147">A Facebook hirdetéskezelő attribútumai a következő felhasználóbarát neveket használják a leképezéshez: **FN** = **Keresztnév**, **LN** = **Utónév**, **FI** = **Első kezdőbetű**, **PHONE** = **Telefon**, **GEN** = **Nem**, **DOB** = **Születési idő**, **ST** = **Állam**, **CT** = **Város**, **ZIP** = **Irányítószám / postafiók**, **COUNTRY** = **Ország/régió**</span><span class="sxs-lookup"><span data-stu-id="d46eb-147">Attributes from Facebook Ads Manager are mapping to the following user-friendly names: **FN** = **First Name**, **LN** = **Last Name**, **FI** = **First Initial**, **PHONE** = **Phone**, **GEN** = **Gender**, **DOB** = **Date of birth**, **ST** = **State**, **CT** = **City**, **ZIP** = **Postal code / ZIP Code**, **COUNTRY** = **Country / Region**</span></span>

1. <span data-ttu-id="d46eb-148">Jelölje ki a szegmenseket, amelyeket exportálni szeretne.</span><span class="sxs-lookup"><span data-stu-id="d46eb-148">Select the segments you want to export.</span></span>

1. <span data-ttu-id="d46eb-149">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="d46eb-149">Select **Save**.</span></span>

<span data-ttu-id="d46eb-150">Az exportálás mentése nem futtatja azonnal az exportálást.</span><span class="sxs-lookup"><span data-stu-id="d46eb-150">Saving an export doesn't run the export immediately.</span></span>

<span data-ttu-id="d46eb-151">Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut.</span><span class="sxs-lookup"><span data-stu-id="d46eb-151">The export runs with every [scheduled refresh](system.md#schedule-tab).</span></span> 

<span data-ttu-id="d46eb-152">Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand).</span><span class="sxs-lookup"><span data-stu-id="d46eb-152">You can also [export data on demand](export-destinations.md#run-exports-on-demand).</span></span> 

## <a name="data-privacy-and-compliance"></a><span data-ttu-id="d46eb-153">Adatvédelem és megfelelőség</span><span class="sxs-lookup"><span data-stu-id="d46eb-153">Data privacy and compliance</span></span>

<span data-ttu-id="d46eb-154">Amikor engedélyezi a Dynamics 365 Customer Insights szolgáltatást az adatok Facebook Ads Managerbe való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat.</span><span class="sxs-lookup"><span data-stu-id="d46eb-154">When you enable Dynamics 365 Customer Insights to transmit data to Facebook Ads Manager, you allow transfer of data outside of the compliance boundary for Dynamics 365 Customer Insights, including potentially sensitive data such as Personal Data.</span></span> <span data-ttu-id="d46eb-155">A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy a Facebook Ads megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek.</span><span class="sxs-lookup"><span data-stu-id="d46eb-155">Microsoft will transfer such data at your instruction, but you are responsible for ensuring that Facebook Ads meet any privacy or security obligations you may have.</span></span> <span data-ttu-id="d46eb-156">További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).</span><span class="sxs-lookup"><span data-stu-id="d46eb-156">For more information, see [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?linkid=396732).</span></span>
<span data-ttu-id="d46eb-157">A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.</span><span class="sxs-lookup"><span data-stu-id="d46eb-157">Your Dynamics 365 Customer Insights administrator can remove this export destination at any time to discontinue use of this functionality.</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]
