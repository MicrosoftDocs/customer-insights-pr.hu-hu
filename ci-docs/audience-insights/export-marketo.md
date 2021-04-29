---
title: Customer Insights adatok exportálása a Marketóba
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a Marketoba.
ms.date: 03/03/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: phkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 01290d5fae7af1737b73373d75e334ae1ed67d37
ms.sourcegitcommit: 1b671c6100991fea1cace04b5d4fcedcd88aa94f
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/31/2021
ms.locfileid: "5759824"
---
# <a name="export-segments-to-marketo-preview"></a><span data-ttu-id="0aac6-103">Szegmensek exportálása a Marketoba (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="0aac6-103">Export segments to Marketo (preview)</span></span>

<span data-ttu-id="0aac6-104">Az egyesített ügyfélprofilok szegmensei exportálásának felhasználásával kampányokat hozhat létre, e-mail-marketing szolgáltatást biztosíthat és előnyt kovácsolhat az ügyfelek meghatározott csoportjából a Marketo szolgáltatással.</span><span class="sxs-lookup"><span data-stu-id="0aac6-104">Export segments of unified customer profiles to generate campaigns, provide email marketing and use specific groups of customers with Marketo.</span></span>

## <a name="prerequisites-for-connection"></a><span data-ttu-id="0aac6-105">A kapcsolat előfeltételei</span><span class="sxs-lookup"><span data-stu-id="0aac6-105">Prerequisites for connection</span></span>

-   <span data-ttu-id="0aac6-106">Rendelkezik [Marketo-fiókkal](https://login.marketo.com/) és a megfelelő rendszergazdai hitelesítő adatokkal.</span><span class="sxs-lookup"><span data-stu-id="0aac6-106">You have a [Marketo account](https://login.marketo.com/) and corresponding administrator credentials.</span></span>
-   <span data-ttu-id="0aac6-107">A Marketóban és a megfelelő azonosítókban meglévő listák találhatók.</span><span class="sxs-lookup"><span data-stu-id="0aac6-107">There are existing lists in Marketo and the corresponding IDs.</span></span> <span data-ttu-id="0aac6-108">További tájékoztatásért keresse fel a [Marketo listák](https://docs.marketo.com/display/public/DOCS/Understanding+Static+Lists) webhelyet.</span><span class="sxs-lookup"><span data-stu-id="0aac6-108">For more information, see [Marketo lists](https://docs.marketo.com/display/public/DOCS/Understanding+Static+Lists).</span></span>
-   <span data-ttu-id="0aac6-109">Rendelkezik [konfigurált szegmensekkel](segments.md).</span><span class="sxs-lookup"><span data-stu-id="0aac6-109">You have [configured segments](segments.md).</span></span>
-   <span data-ttu-id="0aac6-110">Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.</span><span class="sxs-lookup"><span data-stu-id="0aac6-110">Unified customer profiles in the exported segments contain a field representing an email address.</span></span>

## <a name="known-limitations"></a><span data-ttu-id="0aac6-111">Ismert korlátozások</span><span class="sxs-lookup"><span data-stu-id="0aac6-111">Known limitations</span></span>

- <span data-ttu-id="0aac6-112">Legfeljebb 1 000 000 profilt exportálhat egyszerre a Marketoba.</span><span class="sxs-lookup"><span data-stu-id="0aac6-112">Up to 1 million profiles per export to Marketo.</span></span>
- <span data-ttu-id="0aac6-113">A Marketoba való exportálás csak szegmensekre korlátozódik.</span><span class="sxs-lookup"><span data-stu-id="0aac6-113">Exporting to Marketo is limited to segments.</span></span>
- <span data-ttu-id="0aac6-114">Az összesen 1 000 000 profillal rendelkező szegmensek exportálása akár 3 óráig is eltarthat.</span><span class="sxs-lookup"><span data-stu-id="0aac6-114">Exporting segments with a total of 1 million profiles can take up to 3 hours.</span></span> 
- <span data-ttu-id="0aac6-115">A Marketoba exportálható profilok száma függ a Marketo szerződésről, és korlátozott.</span><span class="sxs-lookup"><span data-stu-id="0aac6-115">The number of profiles that you can export to Marketo is dependent and limited on your contract with Marketo.</span></span>

## <a name="set-up-connection-to-marketo"></a><span data-ttu-id="0aac6-116">Állítsa be a Marketoval való kapcsolatot</span><span class="sxs-lookup"><span data-stu-id="0aac6-116">Set up connection to Marketo</span></span>

1. <span data-ttu-id="0aac6-117">Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="0aac6-117">Go to **Admin** > **Connections**.</span></span>

1. <span data-ttu-id="0aac6-118">Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza a **Marketo** lehetőséget a kapcsolat konfigurálásához.</span><span class="sxs-lookup"><span data-stu-id="0aac6-118">Select **Add connection** and choose **Marketo** to configure the connection.</span></span>

1. <span data-ttu-id="0aac6-119">Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak.</span><span class="sxs-lookup"><span data-stu-id="0aac6-119">Give your connection a recognizable name in the **Display name** field.</span></span> <span data-ttu-id="0aac6-120">A név és a kapcsolat típusa írja le ezt a kapcsolatot.</span><span class="sxs-lookup"><span data-stu-id="0aac6-120">The name and the type of the connection describe this connection.</span></span> <span data-ttu-id="0aac6-121">Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.</span><span class="sxs-lookup"><span data-stu-id="0aac6-121">We recommend choosing a name that explains the purpose and target of the connection.</span></span>

1. <span data-ttu-id="0aac6-122">A kapcsolat használóinak kiválasztása.</span><span class="sxs-lookup"><span data-stu-id="0aac6-122">Choose who can use this connection.</span></span> <span data-ttu-id="0aac6-123">Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz.</span><span class="sxs-lookup"><span data-stu-id="0aac6-123">If you take no action, the default will be Administrators.</span></span> <span data-ttu-id="0aac6-124">További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).</span><span class="sxs-lookup"><span data-stu-id="0aac6-124">For more information, see [Allow contributors to use a connection for exports](connections.md#allow-contributors-to-use-a-connection-for-exports).</span></span>

1. <span data-ttu-id="0aac6-125">Adja meg a **[Marketo ügyfél-azonosítót, titkos ügyfélkódot és REST végpont eszköznevét](https://developers.marketo.com/rest-api/authentication/)**.</span><span class="sxs-lookup"><span data-stu-id="0aac6-125">Enter your **[Marketo client ID, Client secret, and REST Endpoint Hostname](https://developers.marketo.com/rest-api/authentication/)**.</span></span>

1. <span data-ttu-id="0aac6-126">Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez, majd válassza a **Csatlakozás** lehetőséget a Marketo kapcsolat inicializálásához.</span><span class="sxs-lookup"><span data-stu-id="0aac6-126">Select **I agree** to confirm the **Data privacy and compliance** and select **Connect** to initialize the connection to Marketo.</span></span>

1. <span data-ttu-id="0aac6-127">Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.</span><span class="sxs-lookup"><span data-stu-id="0aac6-127">Select **Add yourself as export user** and provide your Customer Insights credentials.</span></span>

1. <span data-ttu-id="0aac6-128">A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="0aac6-128">Select **Save** to complete the connection.</span></span>

## <a name="configure-an-export"></a><span data-ttu-id="0aac6-129">Exportálás konfigurálása</span><span class="sxs-lookup"><span data-stu-id="0aac6-129">Configure an export</span></span>

<span data-ttu-id="0aac6-130">Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz.</span><span class="sxs-lookup"><span data-stu-id="0aac6-130">You can configure this export if you have access to a connection of this type.</span></span> <span data-ttu-id="0aac6-131">További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).</span><span class="sxs-lookup"><span data-stu-id="0aac6-131">For more information, see [Permissions needed to configure an export](export-destinations.md#set-up-a-new-export).</span></span>

1. <span data-ttu-id="0aac6-132">Menjen az **Adatok** > **Exportálások** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="0aac6-132">Go to **Data** > **Exports**.</span></span>

1. <span data-ttu-id="0aac6-133">Új exportálás létrehozásához válassza a **Célhely hozzáadása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="0aac6-133">To create a new export, select **Add destination**.</span></span>

1. <span data-ttu-id="0aac6-134">A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot a Marketo szakaszból.</span><span class="sxs-lookup"><span data-stu-id="0aac6-134">In the **Connection for export** field, choose a connection from the Marketo section.</span></span> <span data-ttu-id="0aac6-135">Ha nem látja ezt a szakasznevet, az Ön számára nincs ilyen típusú kapcsolat.</span><span class="sxs-lookup"><span data-stu-id="0aac6-135">If you don't see this section name, there are no connections of this type available to you.</span></span>

1. <span data-ttu-id="0aac6-136">Adja meg a **[Marketo-lista azonosítóját](https://docs.marketo.com/display/public/DOCS/Understanding+Static+Lists)**</span><span class="sxs-lookup"><span data-stu-id="0aac6-136">Enter your **[Marketo list ID](https://docs.marketo.com/display/public/DOCS/Understanding+Static+Lists)**</span></span> 

1. <span data-ttu-id="0aac6-137">Az **Adategyeztetés** szakaszban az **E-mail** mezőben jelölje ki az egyesített ügyfélprofil ügyfél e-mail-címét jelképező mezőjét.</span><span class="sxs-lookup"><span data-stu-id="0aac6-137">In the **Data matching** section, in the **Email** field, select the field in your unified customer profile that represents a customer's email address.</span></span> 

1. <span data-ttu-id="0aac6-138">Tetszés szerint exportálhatja az **Utónév**, **Vezetéknév**, **Város**, **Megye** és **Ország/Régió** lehetőségeket, hogy személyre szabottabb e-maileket hozzon létre.</span><span class="sxs-lookup"><span data-stu-id="0aac6-138">Optionally, you can export **First name**, **Last name**, **City**, **State**, and **Country/Region**  to create more personalized emails.</span></span> <span data-ttu-id="0aac6-139">Válassza az **Attribútum hozzáadása** lehetőséget a mezők leképezéséhez.</span><span class="sxs-lookup"><span data-stu-id="0aac6-139">Select **Add attribute** to map these fields.</span></span>

1. <span data-ttu-id="0aac6-140">Jelölje ki a szegmenseket, amelyeket exportálni szeretne.</span><span class="sxs-lookup"><span data-stu-id="0aac6-140">Select the segments you want to export.</span></span> <span data-ttu-id="0aac6-141">Összesen legfeljebb 1 000 000 ügyfélprofilt exportálhat a Marketóba.</span><span class="sxs-lookup"><span data-stu-id="0aac6-141">You can export up to 1 million customer profiles in total to Marketo.</span></span>

1. <span data-ttu-id="0aac6-142">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="0aac6-142">Select **Save**.</span></span>

<span data-ttu-id="0aac6-143">Az exportálás mentése nem futtatja azonnal az exportálást.</span><span class="sxs-lookup"><span data-stu-id="0aac6-143">Saving an export doesn't run the export immediately.</span></span>

<span data-ttu-id="0aac6-144">Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut.</span><span class="sxs-lookup"><span data-stu-id="0aac6-144">The export runs with every [scheduled refresh](system.md#schedule-tab).</span></span> <span data-ttu-id="0aac6-145">Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand).</span><span class="sxs-lookup"><span data-stu-id="0aac6-145">You can also [export data on demand](export-destinations.md#run-exports-on-demand).</span></span> <span data-ttu-id="0aac6-146">A Marketóban most már megtalálhatja a szegmenseket a [Marketo listában](ttps://docs.marketo.com/display/public/DOCS/Understanding+Static+Lists).</span><span class="sxs-lookup"><span data-stu-id="0aac6-146">In Marketo, you can now find your segments under [Marketo lists](ttps://docs.marketo.com/display/public/DOCS/Understanding+Static+Lists).</span></span>


## <a name="data-privacy-and-compliance"></a><span data-ttu-id="0aac6-147">Adatvédelem és megfelelőség</span><span class="sxs-lookup"><span data-stu-id="0aac6-147">Data privacy and compliance</span></span>

<span data-ttu-id="0aac6-148">Amikor engedélyezi az Dynamics 365 Customer Insights szolgáltatást az adatok Marketoba való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat.</span><span class="sxs-lookup"><span data-stu-id="0aac6-148">When you enable Dynamics 365 Customer Insights to transmit data to Marketo, you allow transfer of data outside of the compliance boundary for Dynamics 365 Customer Insights, including potentially sensitive data such as Personal Data.</span></span> <span data-ttu-id="0aac6-149">A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy az Marketo megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek.</span><span class="sxs-lookup"><span data-stu-id="0aac6-149">Microsoft will transfer such data at your instruction, but you are responsible for ensuring that Marketo meets any privacy or security obligations you may have.</span></span> <span data-ttu-id="0aac6-150">További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).</span><span class="sxs-lookup"><span data-stu-id="0aac6-150">For more information, see [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?linkid=396732).</span></span>
<span data-ttu-id="0aac6-151">A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.</span><span class="sxs-lookup"><span data-stu-id="0aac6-151">Your Dynamics 365 Customer Insights Administrator can remove this export destination at any time to discontinue use of this functionality.</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]