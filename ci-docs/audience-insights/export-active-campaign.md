---
title: Customer Insights adatok exportálása ActiveCampaign-be
description: További információ a kapcsolat konfigurálásához és az ActiveCampaign-hez való exportáláshoz.
ms.date: 06/29/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 6d85fa9836618e27f7f3da6ce17c07b4bc89e187
ms.sourcegitcommit: 057079532e31c12bac36f374857ba3dc847d6ad0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/29/2021
ms.locfileid: "6314626"
---
# <a name="export-segments-to-activecampaign-preview"></a><span data-ttu-id="c72db-103">Szegmensek exportálása ActiveCampaign-be (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="c72db-103">Export segments to ActiveCampaign (preview)</span></span>

<span data-ttu-id="c72db-104">Exportálja az egyesített ügyfélprofilok szegmenseit az ActiveCampaign-be, és használja őket marketingtevékenységekhez.</span><span class="sxs-lookup"><span data-stu-id="c72db-104">Export segments of unified customer profiles to ActiveCampaign and use them for marketing activities.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c72db-105">Előfeltételek</span><span class="sxs-lookup"><span data-stu-id="c72db-105">Prerequisites</span></span>

-   <span data-ttu-id="c72db-106">[ActiveCampaign fiókkal](https://www.activecampaign.com/) és a megfelelő rendszergazdai hitelesítő adatokkal rendelkezik.</span><span class="sxs-lookup"><span data-stu-id="c72db-106">You have an [ActiveCampaign account](https://www.activecampaign.com/) and corresponding administrator credentials.</span></span>
-   <span data-ttu-id="c72db-107">[Konfigurált szegmensekkel](segments.md) rendelkezik a célközönségi-információkban.</span><span class="sxs-lookup"><span data-stu-id="c72db-107">You have [configured segments](segments.md) in audience insights.</span></span>
-   <span data-ttu-id="c72db-108">Az exportált szegmensek egységes ügyfélprofiljai egy e-mail-címmel rendelkező mezőt tartalmaznak.</span><span class="sxs-lookup"><span data-stu-id="c72db-108">Unified customer profiles in the exported segments contain a field with an email address.</span></span>

## <a name="known-limitations"></a><span data-ttu-id="c72db-109">Ismert korlátozások</span><span class="sxs-lookup"><span data-stu-id="c72db-109">Known limitations</span></span>

- <span data-ttu-id="c72db-110">Az ActiveCampaign-be exportálhat exportonként akár 1 millió profilt, és akár 90 percet is igénybe vehet.</span><span class="sxs-lookup"><span data-stu-id="c72db-110">You can export up to 1 million profiles per export to ActiveCampaign and it can take up to 90 minutes to complete.</span></span>
- <span data-ttu-id="c72db-111">Az ActiveCampaign-be történő exportálás szegmensekre korlátozódik.</span><span class="sxs-lookup"><span data-stu-id="c72db-111">Exporting to ActiveCampaign is limited to segments.</span></span>
- <span data-ttu-id="c72db-112">Az ActiveCampaign-be exportálható profilok száma az ActiveCampaign-nel kötött szerződésétől függ.</span><span class="sxs-lookup"><span data-stu-id="c72db-112">The number of profiles that you can export to ActiveCampaign depends on your contract with ActiveCampaign.</span></span>

## <a name="set-up-connection-to-activecampaign"></a><span data-ttu-id="c72db-113">Állítsa be az ActiveCampaign-nel való kapcsolatot</span><span class="sxs-lookup"><span data-stu-id="c72db-113">Set up connection to ActiveCampaign</span></span>

1. <span data-ttu-id="c72db-114">Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="c72db-114">Go to **Admin** > **Connections**.</span></span>

1. <span data-ttu-id="c72db-115">Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza az **ActiveCampaign** lehetőséget a kapcsolat konfigurálásához.</span><span class="sxs-lookup"><span data-stu-id="c72db-115">Select **Add connection** and choose **ActiveCampaign** to configure the connection.</span></span>

1. <span data-ttu-id="c72db-116">Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak.</span><span class="sxs-lookup"><span data-stu-id="c72db-116">Give your connection a recognizable name in the **Display name** field.</span></span> <span data-ttu-id="c72db-117">A név és a kapcsolat típusa írja le ezt a kapcsolatot.</span><span class="sxs-lookup"><span data-stu-id="c72db-117">The name and the type of the connection describe this connection.</span></span> <span data-ttu-id="c72db-118">Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.</span><span class="sxs-lookup"><span data-stu-id="c72db-118">We recommend choosing a name that explains the purpose and target of the connection.</span></span>

1. <span data-ttu-id="c72db-119">A kapcsolat használóinak kiválasztása.</span><span class="sxs-lookup"><span data-stu-id="c72db-119">Choose who can use this connection.</span></span> <span data-ttu-id="c72db-120">Alapértelmezés szerint csak a rendszergazdák.</span><span class="sxs-lookup"><span data-stu-id="c72db-120">By default, it's only administrators.</span></span> <span data-ttu-id="c72db-121">További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).</span><span class="sxs-lookup"><span data-stu-id="c72db-121">For more information, see [Allow contributors to use a connection for exports](connections.md#allow-contributors-to-use-a-connection-for-exports).</span></span>

1. <span data-ttu-id="c72db-122">Adja meg [ActiveCampaign API-kulcsát és REST-végpont eszköznevet](https://help.activecampaign.com/hc/articles/207317590-Getting-started-with-the-API#how-to-obtain-your-activecampaign-api-url-and-key).</span><span class="sxs-lookup"><span data-stu-id="c72db-122">Enter your [ActiveCampaign API Key and REST Endpoint Hostname](https://help.activecampaign.com/hc/articles/207317590-Getting-started-with-the-API#how-to-obtain-your-activecampaign-api-url-and-key).</span></span> <span data-ttu-id="c72db-123">A REST-végpont eszköznév csak eszköznév, a https:// tag nélkül.</span><span class="sxs-lookup"><span data-stu-id="c72db-123">The REST Endpoint Hostname is the hostname only, without https://.</span></span> 

1. <span data-ttu-id="c72db-124">Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.</span><span class="sxs-lookup"><span data-stu-id="c72db-124">Select **I agree** to confirm the **Data privacy and compliance**.</span></span>

1. <span data-ttu-id="c72db-125">Válassza a **Csatlakozás** lehetőséget, az ActiveCampaign inicializáláshoz.</span><span class="sxs-lookup"><span data-stu-id="c72db-125">Select **Connect** to initialize the connection to ActiveCampaign.</span></span>

1. <span data-ttu-id="c72db-126">Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.</span><span class="sxs-lookup"><span data-stu-id="c72db-126">Select **Add yourself as export user** and provide your Customer Insights credentials.</span></span>

1. <span data-ttu-id="c72db-127">A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="c72db-127">Select **Save** to complete the connection.</span></span>

## <a name="configure-an-export"></a><span data-ttu-id="c72db-128">Exportálás konfigurálása</span><span class="sxs-lookup"><span data-stu-id="c72db-128">Configure an export</span></span>

<span data-ttu-id="c72db-129">Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz.</span><span class="sxs-lookup"><span data-stu-id="c72db-129">You can configure an export if you have access to a connection of this type.</span></span> <span data-ttu-id="c72db-130">További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).</span><span class="sxs-lookup"><span data-stu-id="c72db-130">For more information, see [Permissions needed to configure an export](export-destinations.md#set-up-a-new-export).</span></span>

1. <span data-ttu-id="c72db-131">Menjen az **Adatok** > **Exportálások** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="c72db-131">Go to **Data** > **Exports**.</span></span>

1. <span data-ttu-id="c72db-132">Új exportálás létrehozásához válassza a **Célhely hozzáadása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="c72db-132">To create a new export, select **Add destination**.</span></span>

1. <span data-ttu-id="c72db-133">Az **Exportálási kapcsolat** mezőben válasszon kapcsolatot az ActiveCampaign szakaszból.</span><span class="sxs-lookup"><span data-stu-id="c72db-133">In the **Connection for export** field, choose a connection from the ActiveCampaign section.</span></span> <span data-ttu-id="c72db-134">Ha nem látja ezt a szakasznevet, az Ön számára nincs ilyen típusú kapcsolat.</span><span class="sxs-lookup"><span data-stu-id="c72db-134">If you don't see this section name, there are no connections of this type available to you.</span></span>

1. <span data-ttu-id="c72db-135">Adja meg [**ActiveCampaign listaazonosítóját**](https://help.activecampaign.com/hc/articles/360000030559-How-to-create-a-list-in-ActiveCampaign).</span><span class="sxs-lookup"><span data-stu-id="c72db-135">Enter your [**ActiveCampaign List ID**](https://help.activecampaign.com/hc/articles/360000030559-How-to-create-a-list-in-ActiveCampaign).</span></span>    

3. <span data-ttu-id="c72db-136">Az **Adategyeztetés** szakaszban az **E-mail** mezőben jelölje ki az egyesített ügyfélprofil ügyfél e-mail-címét jelképező mezőjét.</span><span class="sxs-lookup"><span data-stu-id="c72db-136">In the **Data matching** section, in the **Email** field, select the field in your unified customer profile that represents a customer's email address.</span></span> <span data-ttu-id="c72db-137">Kötelező a szegmensek ActiveCampaign-be történő exportálása.</span><span class="sxs-lookup"><span data-stu-id="c72db-137">It's required to export segments to ActiveCampaign.</span></span> <span data-ttu-id="c72db-138">Opcionálisan exportálhat utónév, vezetéknév és telefonon, hogy személyre szabottabb e-maileket hozzon létre.</span><span class="sxs-lookup"><span data-stu-id="c72db-138">Optionally, you can export First name, Last name, and Phone to create more personalized emails.</span></span> <span data-ttu-id="c72db-139">Válassza az Attribútum hozzáadása lehetőséget a mezők leképezéséhez.</span><span class="sxs-lookup"><span data-stu-id="c72db-139">Select Add attribute to map these fields.</span></span>

1. <span data-ttu-id="c72db-140">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="c72db-140">Select **Save**.</span></span>

<span data-ttu-id="c72db-141">Az exportálás mentése nem futtatja azonnal az exportálást.</span><span class="sxs-lookup"><span data-stu-id="c72db-141">Saving an export doesn't run the export immediately.</span></span>

<span data-ttu-id="c72db-142">Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut.</span><span class="sxs-lookup"><span data-stu-id="c72db-142">The export runs with every [scheduled refresh](system.md#schedule-tab).</span></span> <span data-ttu-id="c72db-143">Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand).</span><span class="sxs-lookup"><span data-stu-id="c72db-143">You can also [export data on demand](export-destinations.md#run-exports-on-demand).</span></span> 


## <a name="data-privacy-and-compliance"></a><span data-ttu-id="c72db-144">Adatvédelem és megfelelőség</span><span class="sxs-lookup"><span data-stu-id="c72db-144">Data privacy and compliance</span></span>

<span data-ttu-id="c72db-145">Amikor engedélyezed a Dynamics 365 Customer Insights -nak, hogy továbbítsa az adatokat ActiveCampaign-be, engedélyezed az adatátvitelt a megfelelőséghatáron kívülre a Dynamics 365 Customer Insights -nak, beleértve az esetlegesen bizalmas adatokat, például személyes adatokat.</span><span class="sxs-lookup"><span data-stu-id="c72db-145">When you enable Dynamics 365 Customer Insights to transmit data to ActiveCampaign, you allow transfer of data outside of the compliance boundary for Dynamics 365 Customer Insights, including potentially sensitive data such as Personal Data.</span></span> <span data-ttu-id="c72db-146">A Microsoft az Ön utasítására továbbítja az ilyen adatokat, de Ön felelős annak biztosításáért, hogy az ActiveCampaign megfeleljen az esetleges adatvédelmi és biztonsági kötelezettségeknek.</span><span class="sxs-lookup"><span data-stu-id="c72db-146">Microsoft will transfer such data at your instruction, but you are responsible for ensuring that ActiveCampaign meets any privacy or security obligations you may have.</span></span> <span data-ttu-id="c72db-147">További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).</span><span class="sxs-lookup"><span data-stu-id="c72db-147">For more information, see [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?linkid=396732).</span></span>

<span data-ttu-id="c72db-148">A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.</span><span class="sxs-lookup"><span data-stu-id="c72db-148">Your Dynamics 365 Customer Insights administrator can remove this export destination at any time to discontinue use of this functionality.</span></span>
