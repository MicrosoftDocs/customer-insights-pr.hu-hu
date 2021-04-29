---
title: Customer Insights adatok exportálása a Facebook Ads Managerbe
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a Facebook Hirdetéskezelő.
ms.date: 04/15/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: phkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: ca32906a98bc734639fb369d6f5a92e8888fd850
ms.sourcegitcommit: 6d5dd572f75ba4c0303ec77c3b74e4318d52705c
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/16/2021
ms.locfileid: "5906813"
---
# <a name="export-segments-list-to-facebook-ads-manager-preview"></a><span data-ttu-id="57ca2-103">Szegmenslista exportálása a Facebook Hirdetéskezelő (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="57ca2-103">Export segments list to Facebook Ads Manager (preview)</span></span>

<span data-ttu-id="57ca2-104">Az egyesített ügyfélprofilokat tartalmazó szegmensek exportálása a Facebook hirdetéskezelőbe kampányok létrehozásához a Facebook-on és az Instagramon.</span><span class="sxs-lookup"><span data-stu-id="57ca2-104">Export segments of unified customer profiles to Facebook Ads Manager to create campaigns on Facebook and Instagram.</span></span>

## <a name="prerequisites-for-connection"></a><span data-ttu-id="57ca2-105">A kapcsolat előfeltételei</span><span class="sxs-lookup"><span data-stu-id="57ca2-105">Prerequisites for connection</span></span>

- <span data-ttu-id="57ca2-106">A [**Facebook üzleti fiókot**](https://www.facebook.com/business/learn/lessons/step-by-step-ads-manager-account) tartalmazó [**Facebook hirdetési fiókkal**](https://business.facebook.com/) kell rendelkeznie.</span><span class="sxs-lookup"><span data-stu-id="57ca2-106">You need to have a [**Facebook Ad Account**](https://www.facebook.com/business/learn/lessons/step-by-step-ads-manager-account) that includes a [**Facebook Business Account**](https://business.facebook.com/).</span></span>
- <span data-ttu-id="57ca2-107">A [**Facebook hirdetési fiók**](https://www.facebook.com/business/learn/lessons/step-by-step-ads-manager-account) rendszergazdájának kell lennie.</span><span class="sxs-lookup"><span data-stu-id="57ca2-107">You need to be an administrator on the [**Facebook Ad Account**](https://www.facebook.com/business/learn/lessons/step-by-step-ads-manager-account).</span></span>

## <a name="known-limitations"></a><span data-ttu-id="57ca2-108">Ismert korlátozások</span><span class="sxs-lookup"><span data-stu-id="57ca2-108">Known limitations</span></span>

- <span data-ttu-id="57ca2-109">Akár 10 millió ügyfélprofil exportálásonként a Facebook Hirdetéskezelőbe.</span><span class="sxs-lookup"><span data-stu-id="57ca2-109">Up to 10 million customer profile per export to Facebook Ads Manager.</span></span>
- <span data-ttu-id="57ca2-110">A Facebook hirdetéskezelőbe való exportálás csak szegmensekre korlátozódik.</span><span class="sxs-lookup"><span data-stu-id="57ca2-110">Export to Facebook Ads Manager is limited to segments.</span></span>
- <span data-ttu-id="57ca2-111">Kizárólag *ügyféllista* típusú célközönségek létrehozása vagy frissítése a Facebookon.</span><span class="sxs-lookup"><span data-stu-id="57ca2-111">Create or update custom audiences in Facebook of type *customer list* only.</span></span>
- <span data-ttu-id="57ca2-112">Az összesen 10 millió profillal rendelkező szegmensek exportálása akár 90 percig is eltarthat.</span><span class="sxs-lookup"><span data-stu-id="57ca2-112">Exporting segments with a total of 10 million profiles can take up to 90 minutes to complete.</span></span>

## <a name="set-up-connection-to-facebook-ads-manager"></a><span data-ttu-id="57ca2-113">Kapcsolat beállítása a Facebook Hirdetéskezelőhöz</span><span class="sxs-lookup"><span data-stu-id="57ca2-113">Set up connection to Facebook Ads Manager</span></span>

<span data-ttu-id="57ca2-114">Ahhoz, hogy a felhasználók exportálást tudjanak létrehozni, a rendszergazdának konfigurálnia kell a szolgáltatás kapcsolatát, és engedélyeznie kell a közreműködőknek a kapcsolat használatát.</span><span class="sxs-lookup"><span data-stu-id="57ca2-114">Before users can create an export, an administrator must configure the connection to the service and allow contributors to use the connection.</span></span>

1. <span data-ttu-id="57ca2-115">Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="57ca2-115">Go to **Admin** > **Connections**.</span></span>

1. <span data-ttu-id="57ca2-116">Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza a **Facebook Hirdetéskezelő** lehetőséget a kapcsolat konfigurálásához.</span><span class="sxs-lookup"><span data-stu-id="57ca2-116">Select **Add connection** and choose **Facebook Ads Manager** to configure the connection.</span></span>

1. <span data-ttu-id="57ca2-117">Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak.</span><span class="sxs-lookup"><span data-stu-id="57ca2-117">Give your connection a recognizable name in the **Display name** field.</span></span> <span data-ttu-id="57ca2-118">A név és a kapcsolat típusa írja le ezt a kapcsolatot.</span><span class="sxs-lookup"><span data-stu-id="57ca2-118">The name and the type of the connection describe this connection.</span></span> <span data-ttu-id="57ca2-119">Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.</span><span class="sxs-lookup"><span data-stu-id="57ca2-119">We recommend choosing a name that explains the purpose and target of the connection.</span></span>

1. <span data-ttu-id="57ca2-120">A kapcsolat használóinak kiválasztása.</span><span class="sxs-lookup"><span data-stu-id="57ca2-120">Choose who can use this connection.</span></span> <span data-ttu-id="57ca2-121">Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a **Rendszergazdák** lesz.</span><span class="sxs-lookup"><span data-stu-id="57ca2-121">If you take no action, the default will be **Administrators**.</span></span> <span data-ttu-id="57ca2-122">További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).</span><span class="sxs-lookup"><span data-stu-id="57ca2-122">For more information, see [Allow contributors to use a connection for exports](connections.md#allow-contributors-to-use-a-connection-for-exports).</span></span>

1. <span data-ttu-id="57ca2-123">Hitelesítés a Facebook-hirdetések használatával:</span><span class="sxs-lookup"><span data-stu-id="57ca2-123">Authenticate with Facebook Ads:</span></span> 

   1. <span data-ttu-id="57ca2-124">Válassza a **Folytatás Facebook-kal** lehetőséget a bejelentkezéshez a Facebook hirdetési fiókjába.</span><span class="sxs-lookup"><span data-stu-id="57ca2-124">Select **Continue with Facebook** to sign in to your Facebook Ad Account.</span></span>

   1. <span data-ttu-id="57ca2-125">A hitelesítés után engedélyezze a **ads_management** engedélyt a Facebookkal.</span><span class="sxs-lookup"><span data-stu-id="57ca2-125">Allow the **ads_management** permission after authenticating with Facebook.</span></span>

   1. <span data-ttu-id="57ca2-126">Válassza ki a **Facebook hirdetési fiókot**, amellyel dolgozni kíván.</span><span class="sxs-lookup"><span data-stu-id="57ca2-126">Select the **Facebook Ads Account** that you want to work with.</span></span>

   1. <span data-ttu-id="57ca2-127">Jelöljön ki egy **Meglévő egyéni célközönséget** a legördülő listából, vagy hozzon létre egy **Új egyéni célközönséget**.</span><span class="sxs-lookup"><span data-stu-id="57ca2-127">Select an **Existing custom audience** from the drop-down list or create a **New custom audience**.</span></span> <span data-ttu-id="57ca2-128">További tájékoztatás [**Célközönségek a Facebook hirdetéskezelőben**](https://www.facebook.com/business/help/744354708981227?id=2469097953376494) című témakörben olvashat.</span><span class="sxs-lookup"><span data-stu-id="57ca2-128">For more information, see [**Audiences in Facebook Ads Manager**](https://www.facebook.com/business/help/744354708981227?id=2469097953376494).</span></span>
      > [!NOTE]
      > <span data-ttu-id="57ca2-129">Ezzel az exportálással a Facebookon csak az adott típusú *ügyféllistán* hozhatók létre vagy frissíthetők egyéni célközönségek.</span><span class="sxs-lookup"><span data-stu-id="57ca2-129">You can only create or update custom audiences on Facebook of the type *customer list* with this export.</span></span> <span data-ttu-id="57ca2-130">Bizonyos esetekben a legördülő menüben különféle típusú egyéni célközönségek jelennek meg.</span><span class="sxs-lookup"><span data-stu-id="57ca2-130">In some cases, you see custom audiences of different types in the drop-down list.</span></span> <span data-ttu-id="57ca2-131">Ha az *ügyféllistától* eltérő típust választ, akkor az exportálás sikertelen lesz.</span><span class="sxs-lookup"><span data-stu-id="57ca2-131">Selecting a different type than *customer list* will result in a failing export.</span></span> 

1. <span data-ttu-id="57ca2-132">Tekintse át az **Adatvédelem és a megfelelés** lehetőséget, és válassza az **Elfogadom** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="57ca2-132">Review the **Data privacy and compliance** and select **I agree**.</span></span>

1. <span data-ttu-id="57ca2-133">A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="57ca2-133">Select **Save** to complete the connection.</span></span>

## <a name="configure-an-export"></a><span data-ttu-id="57ca2-134">Exportálás konfigurálása</span><span class="sxs-lookup"><span data-stu-id="57ca2-134">Configure an export</span></span>

<span data-ttu-id="57ca2-135">Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz.</span><span class="sxs-lookup"><span data-stu-id="57ca2-135">You can configure this export if you have access to a connection of this type.</span></span> <span data-ttu-id="57ca2-136">További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).</span><span class="sxs-lookup"><span data-stu-id="57ca2-136">For more information, see [Permissions needed to configure an export](export-destinations.md#set-up-a-new-export).</span></span>

1. <span data-ttu-id="57ca2-137">Menjen az **Adatok** > **Exportálások** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="57ca2-137">Go to **Data** > **Exports**.</span></span>

1. <span data-ttu-id="57ca2-138">Új exportálás létrehozásához válassza a **Célhely hozzáadása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="57ca2-138">To create a new export, select **Add destination**.</span></span> 

1. <span data-ttu-id="57ca2-139">A **Kapcsolat exportáláshoz** lehetőségen válasszon egy kapcsolatot a **Facebook hirdetéskezelőből**.</span><span class="sxs-lookup"><span data-stu-id="57ca2-139">In **Connection for export** choose a connection from the **Facebook Ads Manager** section.</span></span> <span data-ttu-id="57ca2-140">Ha nem látja ezt a szakasznevet, az Ön számára nincs ilyen típusú kapcsolat.</span><span class="sxs-lookup"><span data-stu-id="57ca2-140">If you don't see this section name, there are no connections of this type available to you.</span></span>

1. <span data-ttu-id="57ca2-141">A **Kulcsazonosító kiválasztása** mezőben válassza az **E-mail-cím**, **Név és a cím** vagy a **Telefon** lehetőséget, amelyet elküld a Facebook hirdetéskezelőnek.</span><span class="sxs-lookup"><span data-stu-id="57ca2-141">In the **Choose your key identifier field**, select **Email**, **Name and address**, or **Phone** to send to Facebook Ads Manager.</span></span> 

1. <span data-ttu-id="57ca2-142">Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak.</span><span class="sxs-lookup"><span data-stu-id="57ca2-142">Give your connection a recognizable name in the **Display name** field.</span></span>

1. <span data-ttu-id="57ca2-143">Képezze le a megfelelő attribútumokat az egyesített ügyfél entitásból a kiválasztott kulcsazonosítóhoz.</span><span class="sxs-lookup"><span data-stu-id="57ca2-143">Map the corresponding attributes from your unified customer entity for the selected key identifier.</span></span>
   > <span data-ttu-id="57ca2-144">[Tipp] A legjobb esély akkor van az egyezésre, ha az **E-mail-cím** lehetőséget választja kulcsazonosítónak.</span><span class="sxs-lookup"><span data-stu-id="57ca2-144">[TIP] The best chances for a match occur if you select **Email** as key identifier.</span></span> <span data-ttu-id="57ca2-145">A további azonosítók hozzáadásával javíthatja a megfeleltetést.</span><span class="sxs-lookup"><span data-stu-id="57ca2-145">Adding additional identifiers may improve the matching.</span></span>

1. <span data-ttu-id="57ca2-146">Válassza az **Attribútum hozzáadása** lehetőséget a több attribútum leképzésének Facebook hirdetéskezelőbe küldéséhez.</span><span class="sxs-lookup"><span data-stu-id="57ca2-146">Select **Add attribute** to map more attributes to send to Facebook Ads Manager.</span></span> <span data-ttu-id="57ca2-147">A Facebook Ads Manager a következő felhasználóbarát neveket használja a leképezéshez: **FN** = **Keresztnév**, **LN** = **Utónév**, **FI** = **Első kezdőbetű**, **PHONE** = **Telefon**, **GEN** = **Nem**, **DOB** = **Születési idő**, **ST** = **Állam**, **CT** = **Város**, **ZIP** = **Irányítószám**, **COUNTRY** = **Ország/régió**</span><span class="sxs-lookup"><span data-stu-id="57ca2-147">Attributes from Facebook Ads Manager are mapping to the following user-friendly names: **FN** = **First Name**, **LN** = **Last Name**, **FI** = **First Initial**, **PHONE** = **Phone**, **GEN** = **Gender**, **DOB** = **Date of birth**, **ST** = **State**, **CT** = **City**, **ZIP** = **Postal code / Zip code**, **COUNTRY** = **Country / Region**</span></span>

1. <span data-ttu-id="57ca2-148">Jelölje ki a szegmenseket, amelyeket exportálni szeretne.</span><span class="sxs-lookup"><span data-stu-id="57ca2-148">Select the segments you want to export.</span></span>

1. <span data-ttu-id="57ca2-149">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="57ca2-149">Select **Save**.</span></span>

<span data-ttu-id="57ca2-150">Az exportálás mentése nem futtatja azonnal az exportálást.</span><span class="sxs-lookup"><span data-stu-id="57ca2-150">Saving an export doesn't run the export immediately.</span></span>

<span data-ttu-id="57ca2-151">Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut.</span><span class="sxs-lookup"><span data-stu-id="57ca2-151">The export runs with every [scheduled refresh](system.md#schedule-tab).</span></span> <span data-ttu-id="57ca2-152">Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand).</span><span class="sxs-lookup"><span data-stu-id="57ca2-152">You can also [export data on demand](export-destinations.md#run-exports-on-demand).</span></span> 

## <a name="data-privacy-and-compliance"></a><span data-ttu-id="57ca2-153">Adatvédelem és megfelelőség</span><span class="sxs-lookup"><span data-stu-id="57ca2-153">Data privacy and compliance</span></span>

<span data-ttu-id="57ca2-154">Amikor engedélyezi a Dynamics 365 Customer Insights szolgáltatást az adatok Facebook Ads Managerbe való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat.</span><span class="sxs-lookup"><span data-stu-id="57ca2-154">When you enable Dynamics 365 Customer Insights to transmit data to Facebook Ads Manager, you allow transfer of data outside of the compliance boundary for Dynamics 365 Customer Insights, including potentially sensitive data such as Personal Data.</span></span> <span data-ttu-id="57ca2-155">A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy a Facebook Ads megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek.</span><span class="sxs-lookup"><span data-stu-id="57ca2-155">Microsoft will transfer such data at your instruction, but you are responsible for ensuring that Facebook Ads meet any privacy or security obligations you may have.</span></span> <span data-ttu-id="57ca2-156">További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).</span><span class="sxs-lookup"><span data-stu-id="57ca2-156">For more information, see [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?linkid=396732).</span></span>
<span data-ttu-id="57ca2-157">A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.</span><span class="sxs-lookup"><span data-stu-id="57ca2-157">Your Dynamics 365 Customer Insights Administrator can remove this export destination at any time to discontinue use of this functionality.</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]
