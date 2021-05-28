---
title: Customer Insights adatok exportálása a Marketóba
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a Marketoba.
ms.date: 03/03/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: b5a644e286bd44d4ebf7d1837255326c005b48d6
ms.sourcegitcommit: 74cd4fa9cbb784d9dff174c0eec7b4dcb408d66b
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/18/2021
ms.locfileid: "6059319"
---
# <a name="export-segments-to-marketo-preview"></a><span data-ttu-id="ce65e-103">Szegmensek exportálása a Marketoba (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="ce65e-103">Export segments to Marketo (preview)</span></span>

<span data-ttu-id="ce65e-104">Az egyesített ügyfélprofilok szegmensei exportálásának felhasználásával kampányokat hozhat létre, e-mail-marketing szolgáltatást biztosíthat és előnyt kovácsolhat az ügyfelek meghatározott csoportjából a Marketo szolgáltatással.</span><span class="sxs-lookup"><span data-stu-id="ce65e-104">Export segments of unified customer profiles to generate campaigns, provide email marketing and use specific groups of customers with Marketo.</span></span>

## <a name="prerequisites-for-connection"></a><span data-ttu-id="ce65e-105">A kapcsolat előfeltételei</span><span class="sxs-lookup"><span data-stu-id="ce65e-105">Prerequisites for connection</span></span>

-   <span data-ttu-id="ce65e-106">Rendelkezik [Marketo-fiókkal](https://login.marketo.com/) és a megfelelő rendszergazdai hitelesítő adatokkal.</span><span class="sxs-lookup"><span data-stu-id="ce65e-106">You have a [Marketo account](https://login.marketo.com/) and corresponding administrator credentials.</span></span>
-   <span data-ttu-id="ce65e-107">A Marketóban és a megfelelő azonosítókban meglévő listák találhatók.</span><span class="sxs-lookup"><span data-stu-id="ce65e-107">There are existing lists in Marketo and the corresponding IDs.</span></span> <span data-ttu-id="ce65e-108">További tájékoztatásért keresse fel a [Marketo listák](https://docs.marketo.com/display/public/DOCS/Understanding+Static+Lists) webhelyet.</span><span class="sxs-lookup"><span data-stu-id="ce65e-108">For more information, see [Marketo lists](https://docs.marketo.com/display/public/DOCS/Understanding+Static+Lists).</span></span>
-   <span data-ttu-id="ce65e-109">Rendelkezik [konfigurált szegmensekkel](segments.md).</span><span class="sxs-lookup"><span data-stu-id="ce65e-109">You have [configured segments](segments.md).</span></span>
-   <span data-ttu-id="ce65e-110">Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.</span><span class="sxs-lookup"><span data-stu-id="ce65e-110">Unified customer profiles in the exported segments contain a field representing an email address.</span></span>

## <a name="known-limitations"></a><span data-ttu-id="ce65e-111">Ismert korlátozások</span><span class="sxs-lookup"><span data-stu-id="ce65e-111">Known limitations</span></span>

- <span data-ttu-id="ce65e-112">Legfeljebb 1 000 000 profilt exportálhat egyszerre a Marketoba.</span><span class="sxs-lookup"><span data-stu-id="ce65e-112">Up to 1 million profiles per export to Marketo.</span></span>
- <span data-ttu-id="ce65e-113">A Marketoba való exportálás csak szegmensekre korlátozódik.</span><span class="sxs-lookup"><span data-stu-id="ce65e-113">Exporting to Marketo is limited to segments.</span></span>
- <span data-ttu-id="ce65e-114">Az összesen 1 000 000 profillal rendelkező szegmensek exportálása akár 3 óráig is eltarthat.</span><span class="sxs-lookup"><span data-stu-id="ce65e-114">Exporting segments with a total of 1 million profiles can take up to 3 hours.</span></span> 
- <span data-ttu-id="ce65e-115">A Marketoba exportálható profilok száma függ a Marketo szerződésről, és korlátozott.</span><span class="sxs-lookup"><span data-stu-id="ce65e-115">The number of profiles that you can export to Marketo is dependent and limited on your contract with Marketo.</span></span>

## <a name="set-up-connection-to-marketo"></a><span data-ttu-id="ce65e-116">Állítsa be a Marketoval való kapcsolatot</span><span class="sxs-lookup"><span data-stu-id="ce65e-116">Set up connection to Marketo</span></span>

1. <span data-ttu-id="ce65e-117">Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="ce65e-117">Go to **Admin** > **Connections**.</span></span>

1. <span data-ttu-id="ce65e-118">Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza a **Marketo** lehetőséget a kapcsolat konfigurálásához.</span><span class="sxs-lookup"><span data-stu-id="ce65e-118">Select **Add connection** and choose **Marketo** to configure the connection.</span></span>

1. <span data-ttu-id="ce65e-119">Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak.</span><span class="sxs-lookup"><span data-stu-id="ce65e-119">Give your connection a recognizable name in the **Display name** field.</span></span> <span data-ttu-id="ce65e-120">A név és a kapcsolat típusa írja le ezt a kapcsolatot.</span><span class="sxs-lookup"><span data-stu-id="ce65e-120">The name and the type of the connection describe this connection.</span></span> <span data-ttu-id="ce65e-121">Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.</span><span class="sxs-lookup"><span data-stu-id="ce65e-121">We recommend choosing a name that explains the purpose and target of the connection.</span></span>

1. <span data-ttu-id="ce65e-122">A kapcsolat használóinak kiválasztása.</span><span class="sxs-lookup"><span data-stu-id="ce65e-122">Choose who can use this connection.</span></span> <span data-ttu-id="ce65e-123">Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz.</span><span class="sxs-lookup"><span data-stu-id="ce65e-123">If you take no action, the default will be Administrators.</span></span> <span data-ttu-id="ce65e-124">További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).</span><span class="sxs-lookup"><span data-stu-id="ce65e-124">For more information, see [Allow contributors to use a connection for exports](connections.md#allow-contributors-to-use-a-connection-for-exports).</span></span>

1. <span data-ttu-id="ce65e-125">Adja meg a **[Marketo ügyfél-azonosítót, titkos ügyfélkódot és REST végpont eszköznevét](https://developers.marketo.com/rest-api/authentication/)**.</span><span class="sxs-lookup"><span data-stu-id="ce65e-125">Enter your **[Marketo client ID, Client secret, and REST Endpoint Hostname](https://developers.marketo.com/rest-api/authentication/)**.</span></span> <span data-ttu-id="ce65e-126">A REST-végpont eszköznév csak eszköznév, a `https://` tag nélkül.</span><span class="sxs-lookup"><span data-stu-id="ce65e-126">The REST Endpoint Hostname is the hostname only, without `https://`.</span></span> <span data-ttu-id="ce65e-127">Példa: `xyz-abc-123.mktorest.com`.</span><span class="sxs-lookup"><span data-stu-id="ce65e-127">Example: `xyz-abc-123.mktorest.com`.</span></span> 

1. <span data-ttu-id="ce65e-128">Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez, majd válassza a **Csatlakozás** lehetőséget a Marketo kapcsolat inicializálásához.</span><span class="sxs-lookup"><span data-stu-id="ce65e-128">Select **I agree** to confirm the **Data privacy and compliance** and select **Connect** to initialize the connection to Marketo.</span></span>

1. <span data-ttu-id="ce65e-129">Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.</span><span class="sxs-lookup"><span data-stu-id="ce65e-129">Select **Add yourself as export user** and provide your Customer Insights credentials.</span></span>

1. <span data-ttu-id="ce65e-130">A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="ce65e-130">Select **Save** to complete the connection.</span></span>

## <a name="configure-an-export"></a><span data-ttu-id="ce65e-131">Exportálás konfigurálása</span><span class="sxs-lookup"><span data-stu-id="ce65e-131">Configure an export</span></span>

<span data-ttu-id="ce65e-132">Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz.</span><span class="sxs-lookup"><span data-stu-id="ce65e-132">You can configure this export if you have access to a connection of this type.</span></span> <span data-ttu-id="ce65e-133">További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).</span><span class="sxs-lookup"><span data-stu-id="ce65e-133">For more information, see [Permissions needed to configure an export](export-destinations.md#set-up-a-new-export).</span></span>

1. <span data-ttu-id="ce65e-134">Menjen az **Adatok** > **Exportálások** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="ce65e-134">Go to **Data** > **Exports**.</span></span>

1. <span data-ttu-id="ce65e-135">Új exportálás létrehozásához válassza a **Célhely hozzáadása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="ce65e-135">To create a new export, select **Add destination**.</span></span>

1. <span data-ttu-id="ce65e-136">A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot a Marketo szakaszból.</span><span class="sxs-lookup"><span data-stu-id="ce65e-136">In the **Connection for export** field, choose a connection from the Marketo section.</span></span> <span data-ttu-id="ce65e-137">Ha nem látja ezt a szakasznevet, az Ön számára nincs ilyen típusú kapcsolat.</span><span class="sxs-lookup"><span data-stu-id="ce65e-137">If you don't see this section name, there are no connections of this type available to you.</span></span>

1. <span data-ttu-id="ce65e-138">Adja meg a **[Marketo-listaazonosítót](https://docs.marketo.com/display/public/DOCS/Understanding+Static+Lists)**.</span><span class="sxs-lookup"><span data-stu-id="ce65e-138">Enter your **[Marketo list ID](https://docs.marketo.com/display/public/DOCS/Understanding+Static+Lists)**.</span></span> <span data-ttu-id="ce65e-139">A listaazonosító tisztán numerikus érték.</span><span class="sxs-lookup"><span data-stu-id="ce65e-139">The list ID is a purely numerical value.</span></span> <span data-ttu-id="ce65e-140">Ha például a Marketo-listaazonosító ST12345A7, akkor távolítsa el a számok előtt és után lévő karaktereket, és csak az `12345` értéket adja meg.</span><span class="sxs-lookup"><span data-stu-id="ce65e-140">For example, if your Marketo list ID is ST12345A7, remove the character before and after the numerals and enter `12345`.</span></span> 

1. <span data-ttu-id="ce65e-141">Az **Adategyeztetés** szakaszban az **E-mail** mezőben jelölje ki az egyesített ügyfélprofil ügyfél e-mail-címét jelképező mezőjét.</span><span class="sxs-lookup"><span data-stu-id="ce65e-141">In the **Data matching** section, in the **Email** field, select the field in your unified customer profile that represents a customer's email address.</span></span> 

1. <span data-ttu-id="ce65e-142">Tetszés szerint exportálhatja az **Utónév**, **Vezetéknév**, **Város**, **Megye** és **Ország/Régió** lehetőségeket, hogy személyre szabottabb e-maileket hozzon létre.</span><span class="sxs-lookup"><span data-stu-id="ce65e-142">Optionally, you can export **First name**, **Last name**, **City**, **State**, and **Country/Region**  to create more personalized emails.</span></span> <span data-ttu-id="ce65e-143">Válassza az **Attribútum hozzáadása** lehetőséget a mezők leképezéséhez.</span><span class="sxs-lookup"><span data-stu-id="ce65e-143">Select **Add attribute** to map these fields.</span></span>

1. <span data-ttu-id="ce65e-144">Jelölje ki a szegmenseket, amelyeket exportálni szeretne.</span><span class="sxs-lookup"><span data-stu-id="ce65e-144">Select the segments you want to export.</span></span> <span data-ttu-id="ce65e-145">Összesen legfeljebb 1 000 000 ügyfélprofilt exportálhat a Marketóba.</span><span class="sxs-lookup"><span data-stu-id="ce65e-145">You can export up to 1 million customer profiles in total to Marketo.</span></span>

1. <span data-ttu-id="ce65e-146">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="ce65e-146">Select **Save**.</span></span>

<span data-ttu-id="ce65e-147">Az exportálás mentése nem futtatja azonnal az exportálást.</span><span class="sxs-lookup"><span data-stu-id="ce65e-147">Saving an export doesn't run the export immediately.</span></span>

<span data-ttu-id="ce65e-148">Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut.</span><span class="sxs-lookup"><span data-stu-id="ce65e-148">The export runs with every [scheduled refresh](system.md#schedule-tab).</span></span> <span data-ttu-id="ce65e-149">Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand).</span><span class="sxs-lookup"><span data-stu-id="ce65e-149">You can also [export data on demand](export-destinations.md#run-exports-on-demand).</span></span> <span data-ttu-id="ce65e-150">A Marketóban most már megtalálhatja a szegmenseket a [Marketo listában](https://docs.marketo.com/display/public/DOCS/Understanding+Static+Lists).</span><span class="sxs-lookup"><span data-stu-id="ce65e-150">In Marketo, you can now find your segments under [Marketo lists](https://docs.marketo.com/display/public/DOCS/Understanding+Static+Lists).</span></span>


## <a name="data-privacy-and-compliance"></a><span data-ttu-id="ce65e-151">Adatvédelem és megfelelőség</span><span class="sxs-lookup"><span data-stu-id="ce65e-151">Data privacy and compliance</span></span>

<span data-ttu-id="ce65e-152">Amikor engedélyezi az Dynamics 365 Customer Insights szolgáltatást az adatok Marketoba való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat.</span><span class="sxs-lookup"><span data-stu-id="ce65e-152">When you enable Dynamics 365 Customer Insights to transmit data to Marketo, you allow transfer of data outside of the compliance boundary for Dynamics 365 Customer Insights, including potentially sensitive data such as Personal Data.</span></span> <span data-ttu-id="ce65e-153">A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy az Marketo megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek.</span><span class="sxs-lookup"><span data-stu-id="ce65e-153">Microsoft will transfer such data at your instruction, but you are responsible for ensuring that Marketo meets any privacy or security obligations you may have.</span></span> <span data-ttu-id="ce65e-154">További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).</span><span class="sxs-lookup"><span data-stu-id="ce65e-154">For more information, see [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?linkid=396732).</span></span>
<span data-ttu-id="ce65e-155">A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.</span><span class="sxs-lookup"><span data-stu-id="ce65e-155">Your Dynamics 365 Customer Insights Administrator can remove this export destination at any time to discontinue use of this functionality.</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]
