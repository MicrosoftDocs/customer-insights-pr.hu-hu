---
title: Customer Insights-adatok exportálása a LinkedIn Ads szolgáltatásba
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a LinkedIn Adsbe.
ms.date: 05/12/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 1c7b0c728bc4d4cf6b5aea79396cf0779fbf298d
ms.sourcegitcommit: 831765a55775d358447cb7ffa56f2c3b85459084
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/01/2021
ms.locfileid: "6124503"
---
# <a name="export-segments-to-linkedin-ads-preview"></a><span data-ttu-id="aa548-103">Szegmensek exportálása a LinkedIn Ads szolgáltatásba (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="aa548-103">Export segments to LinkedIn Ads (preview)</span></span>

<span data-ttu-id="aa548-104">Az egyesített ügyfélprofilok szegmenseinek exportálása a LinkedIn Ads-szolgáltatásba, hogy egyeztetett célközönségeket hozzon létre.</span><span class="sxs-lookup"><span data-stu-id="aa548-104">Export segments of unified customer profiles to LinkedIn Ads to create matched audiences.</span></span> <span data-ttu-id="aa548-105">Használja az egyeztetett célközönségeket a vállalati célzáshoz és a kapcsolati célzáshoz.</span><span class="sxs-lookup"><span data-stu-id="aa548-105">Use the matched audiences for company targeting and contact targeting.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="aa548-106">Előfeltételek</span><span class="sxs-lookup"><span data-stu-id="aa548-106">Prerequisites</span></span>

-   <span data-ttu-id="aa548-107">Van egy [LinkedIn Campaign Manager-fiókja](https://business.linkedin.com/marketing-solutions/ads) és ahhoz tartozó rendszergazdai hitelesítő adatai.</span><span class="sxs-lookup"><span data-stu-id="aa548-107">You have an [LinkedIn Campaign Manager account](https://business.linkedin.com/marketing-solutions/ads) and corresponding administrator credentials.</span></span>
-   <span data-ttu-id="aa548-108">[Konfigurált szegmensekkel](segments.md) rendelkezik a célközönségi-információkban.</span><span class="sxs-lookup"><span data-stu-id="aa548-108">You have [configured segments](segments.md) in audience insights.</span></span>
-   <span data-ttu-id="aa548-109">Az exportált szegmensek ügyfélprofiljai egy e-mail-címmel rendelkező mezőt tartalmaznak.</span><span class="sxs-lookup"><span data-stu-id="aa548-109">Customer profiles in the exported segments contain a field with an email address.</span></span>

## <a name="known-limitations"></a><span data-ttu-id="aa548-110">Ismert korlátozások</span><span class="sxs-lookup"><span data-stu-id="aa548-110">Known limitations</span></span>

- <span data-ttu-id="aa548-111">A LinkedIn Ads exportálásonként legfeljebb 100 000 profil exportálható.</span><span class="sxs-lookup"><span data-stu-id="aa548-111">You can export up to 100K profiles per export to LinkedIn Ads.</span></span>
- <span data-ttu-id="aa548-112">A LinkedIn Ads szolgáltatásba való exportálás a szegmensekre korlátozódik.</span><span class="sxs-lookup"><span data-stu-id="aa548-112">Exporting to LinkedIn Ads is limited to segments.</span></span>
- <span data-ttu-id="aa548-113">100 000 profil exportálása a LinkedIn Ads szolgáltatásba akár 10 percet is igénybe vehet.</span><span class="sxs-lookup"><span data-stu-id="aa548-113">Exporting up to 100K profiles to LinkedIn Ads can take up to 10 minutes to complete.</span></span> 

## <a name="set-up-the-connection-to-linkedin-ads"></a><span data-ttu-id="aa548-114">Állítsa be a LinkedIn Ads szolgáltatással való kapcsolatot</span><span class="sxs-lookup"><span data-stu-id="aa548-114">Set up the connection to LinkedIn Ads</span></span>

1. <span data-ttu-id="aa548-115">A célközönség információkban menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="aa548-115">In audience insights, go to **Admin** > **Connections**.</span></span>

1. <span data-ttu-id="aa548-116">Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza a **LinkedIn Ads** lehetőséget a kapcsolat konfigurálásához.</span><span class="sxs-lookup"><span data-stu-id="aa548-116">Select **Add connection** and choose **LinkedIn Ads** to configure the connection.</span></span>

1. <span data-ttu-id="aa548-117">Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak.</span><span class="sxs-lookup"><span data-stu-id="aa548-117">Give your connection a recognizable name in the **Display name** field.</span></span> <span data-ttu-id="aa548-118">A név és a kapcsolat típusa írja le ezt a kapcsolatot.</span><span class="sxs-lookup"><span data-stu-id="aa548-118">The name and the type of the connection describe this connection.</span></span> <span data-ttu-id="aa548-119">Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.</span><span class="sxs-lookup"><span data-stu-id="aa548-119">We recommend choosing a name that explains the purpose and target of the connection.</span></span>

1. <span data-ttu-id="aa548-120">A kapcsolat használóinak kiválasztása.</span><span class="sxs-lookup"><span data-stu-id="aa548-120">Choose who can use this connection.</span></span> <span data-ttu-id="aa548-121">Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a rendszergazdák.</span><span class="sxs-lookup"><span data-stu-id="aa548-121">If you take no action, the default is administrators.</span></span> <span data-ttu-id="aa548-122">További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).</span><span class="sxs-lookup"><span data-stu-id="aa548-122">For more information, see [Allow contributors to use a connection for exports](connections.md#allow-contributors-to-use-a-connection-for-exports).</span></span>

1. <span data-ttu-id="aa548-123">Adja meg [LinkedIn Campaign Manager fiókazonosítóját](https://www.linkedin.com/help/lms/answer/a424270).</span><span class="sxs-lookup"><span data-stu-id="aa548-123">Provide your [LinkedIn Campaign Manager Account ID](https://www.linkedin.com/help/lms/answer/a424270).</span></span>

1. <span data-ttu-id="aa548-124">Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.</span><span class="sxs-lookup"><span data-stu-id="aa548-124">Select **I agree** to confirm the **Data privacy and compliance**.</span></span>

1. <span data-ttu-id="aa548-125">Válassza a **Kapcsolat** lehetőséget a Campaign Monitor kapcsolatának inicializálására.</span><span class="sxs-lookup"><span data-stu-id="aa548-125">Select **Connect** to initialize the connection to Campaign Monitor.</span></span>

1. <span data-ttu-id="aa548-126">Válassza a **Hitelesítés a LinkedInnel** lehetőséget, és adja meg a LinkedIn Campaign Manager hitelesítő adatait.</span><span class="sxs-lookup"><span data-stu-id="aa548-126">Select **Authenticate with LinkedIn** and provide your admin credentials for LinkedIn Campaign Manager.</span></span>

1. <span data-ttu-id="aa548-127">Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.</span><span class="sxs-lookup"><span data-stu-id="aa548-127">Select **Add yourself as export user** and provide your Customer Insights credentials.</span></span>

1. <span data-ttu-id="aa548-128">A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="aa548-128">Select **Save** to complete the connection.</span></span>

## <a name="configure-an-export"></a><span data-ttu-id="aa548-129">Exportálás konfigurálása</span><span class="sxs-lookup"><span data-stu-id="aa548-129">Configure an export</span></span>

<span data-ttu-id="aa548-130">Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz.</span><span class="sxs-lookup"><span data-stu-id="aa548-130">You can configure an export if you have access to a connection of this type.</span></span> <span data-ttu-id="aa548-131">További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).</span><span class="sxs-lookup"><span data-stu-id="aa548-131">For more information, see [Permissions needed to configure an export](export-destinations.md#set-up-a-new-export).</span></span>

1. <span data-ttu-id="aa548-132">Menjen az **Adatok** > **Exportálások** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="aa548-132">Go to **Data** > **Exports**.</span></span>

1. <span data-ttu-id="aa548-133">Új exportálás létrehozásához válassza a **Célhely hozzáadása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="aa548-133">To create a new export, select **Add destination**.</span></span>

1. <span data-ttu-id="aa548-134">A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot a LinkedIn Ads szakaszból.</span><span class="sxs-lookup"><span data-stu-id="aa548-134">In the **Connection for export** field, choose a connection from the LinkedIn Ads section.</span></span> <span data-ttu-id="aa548-135">Ha nem látja ezt a szakasznevet, az Ön számára nincs ilyen típusú kapcsolat.</span><span class="sxs-lookup"><span data-stu-id="aa548-135">If you don't see this section name, there are no connections of this type available to you.</span></span>

1. <span data-ttu-id="aa548-136">Válassza ki, hogy az adatokat a LinkedIn-en [kapcsolati célzáshoz](https://business.linkedin.com/marketing-solutions/ad-targeting/contact-targeting) vagy [Vállalati célzáshoz](https://business.linkedin.com/marketing-solutions/ad-targeting/account-targeting) exportálja.</span><span class="sxs-lookup"><span data-stu-id="aa548-136">Choose whether you want to export data to do [contact targeting](https://business.linkedin.com/marketing-solutions/ad-targeting/contact-targeting) or [company targeting](https://business.linkedin.com/marketing-solutions/ad-targeting/account-targeting) on LinkedIn.</span></span> 

1. <span data-ttu-id="aa548-137">Az **Adategyeztetés** szakaszban válassza ki az egységes ügyfélprofil mezőjét, amely az ügyfél e-mail-címének felel meg.</span><span class="sxs-lookup"><span data-stu-id="aa548-137">In the **Data matching** section, select the field in your unified customer profile that represents a customer's email address.</span></span> <span data-ttu-id="aa548-138">A szegmenseket exportálni kell a LinkedIn Ads-szolgáltatásba.</span><span class="sxs-lookup"><span data-stu-id="aa548-138">It's required to export segments to LinkedIn Ads.</span></span>

1. <span data-ttu-id="aa548-139">Jelölje ki a szegmenseket, amelyeket exportálni szeretne.</span><span class="sxs-lookup"><span data-stu-id="aa548-139">Select the segments you want to export.</span></span> <span data-ttu-id="aa548-140">A LinkedIn Campaign Manager egyeztetett célközönségei automatikusan létrejönnek az exportálásra kiválasztott szegmensek nevével.</span><span class="sxs-lookup"><span data-stu-id="aa548-140">The matched audiences in LinkedIn Campaign Manager will automatically be created with the name of the segments that you selected to export.</span></span> <span data-ttu-id="aa548-141">Minden szegmens külön egyeztetett célközönséget eredményez.</span><span class="sxs-lookup"><span data-stu-id="aa548-141">Each segment will result in a separate matched audience.</span></span> 

1. <span data-ttu-id="aa548-142">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="aa548-142">Select **Save**.</span></span>

<span data-ttu-id="aa548-143">Az exportálás mentése nem futtatja azonnal az exportálást.</span><span class="sxs-lookup"><span data-stu-id="aa548-143">Saving an export doesn't run the export immediately.</span></span>

<span data-ttu-id="aa548-144">Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut.</span><span class="sxs-lookup"><span data-stu-id="aa548-144">The export runs with every [scheduled refresh](system.md#schedule-tab).</span></span> <span data-ttu-id="aa548-145">Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand).</span><span class="sxs-lookup"><span data-stu-id="aa548-145">You can also [export data on demand](export-destinations.md#run-exports-on-demand).</span></span> 


## <a name="data-privacy-and-compliance"></a><span data-ttu-id="aa548-146">Adatvédelem és megfelelőség</span><span class="sxs-lookup"><span data-stu-id="aa548-146">Data privacy and compliance</span></span>

<span data-ttu-id="aa548-147">Amikor engedélyezi Dynamics 365 Customer Insights számára, hogy adatokat továbbítson a LinkedIn Ads számára, akkor lehetővé teszi az adatok továbbítását a Dynamics 365 Customer Insights megfelelési határán kívülre is, beleértve az esetlegesen bizalmas adatokat is, például a Személyes adatokat.</span><span class="sxs-lookup"><span data-stu-id="aa548-147">When you enable Dynamics 365 Customer Insights to transmit data to LinkedIn Ads, you allow transfer of data outside of the compliance boundary for Dynamics 365 Customer Insights, including potentially sensitive data such as Personal Data.</span></span> <span data-ttu-id="aa548-148">A Microsoft az Ön utasítására továbbítja az adatokat, de Ön a felelős azért, hogy a LinkedIn Ads megfeleljen az esetleges adatvédelmi vagy biztonsági kötelezettségeknek.</span><span class="sxs-lookup"><span data-stu-id="aa548-148">Microsoft will transfer such data at your instruction, but you are responsible for ensuring that LinkedIn Ads meet any privacy or security obligations you may have.</span></span> <span data-ttu-id="aa548-149">További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).</span><span class="sxs-lookup"><span data-stu-id="aa548-149">For more information, see [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?linkid=396732).</span></span>

<span data-ttu-id="aa548-150">A funkció használatának leállítása érdekében az Ön Dynamics 365 Customer Insights rendszergazdája bármikor eltávolíthatja ezt az exportálási célhelyet.</span><span class="sxs-lookup"><span data-stu-id="aa548-150">Your Dynamics 365 Customer Insights Administrator can remove this export destination at any time to stop the use of this functionality.</span></span>
