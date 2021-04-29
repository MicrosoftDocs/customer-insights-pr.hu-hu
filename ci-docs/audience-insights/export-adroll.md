---
title: Customer Insights adatok exportálása az AdRollba
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja az AdRollba.
ms.date: 03/03/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: e8f4d4ee6b2c6cdec513b700641db568fa16076d
ms.sourcegitcommit: aaa275c60c0c77c88196277b266a91d653f8f759
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/14/2021
ms.locfileid: "5895962"
---
# <a name="export-segment-lists-to-adroll-preview"></a><span data-ttu-id="1edde-103">Szegmenslisták exportálása az AdRollba (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="1edde-103">Export segment lists to AdRoll (preview)</span></span>

<span data-ttu-id="1edde-104">Exportálja az egyesített ügyfélprofilok szegmenseit az AdRollba, és használja őket a hirdetésekben.</span><span class="sxs-lookup"><span data-stu-id="1edde-104">Export segments of unified customer profiles to AdRoll and use them for advertising.</span></span> 

## <a name="prerequisites-for-a-connection"></a><span data-ttu-id="1edde-105">Egy kapcsolat előfeltételei</span><span class="sxs-lookup"><span data-stu-id="1edde-105">Prerequisites for a connection</span></span>

-   <span data-ttu-id="1edde-106">Rendelkezik [AdRoll-fiókkal](https://www.adroll.com/) és a megfelelő rendszergazdai hitelesítő adatokkal.</span><span class="sxs-lookup"><span data-stu-id="1edde-106">You have an [AdRoll account](https://www.adroll.com/) and corresponding administrator credentials.</span></span>
-   <span data-ttu-id="1edde-107">[Konfigurált szegmensekkel](segments.md) rendelkezik a célközönségi-információkban.</span><span class="sxs-lookup"><span data-stu-id="1edde-107">You have [configured segments](segments.md) in audience insights.</span></span>
-   <span data-ttu-id="1edde-108">Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.</span><span class="sxs-lookup"><span data-stu-id="1edde-108">Unified customer profiles in the exported segments contain a field representing an email address.</span></span>

## <a name="known-limitations"></a><span data-ttu-id="1edde-109">Ismert korlátozások</span><span class="sxs-lookup"><span data-stu-id="1edde-109">Known limitations</span></span>

- <span data-ttu-id="1edde-110">Összesen exportálásonként legfeljebb 250 000 ügyfélprofilt exportálhat az AdRollba.</span><span class="sxs-lookup"><span data-stu-id="1edde-110">You can export up to 250'000 profiles in per export to AdRoll.</span></span>
- <span data-ttu-id="1edde-111">100-nál kevesebb profillal rendelkező szegmensek nem exportálhatók az AdRollba.</span><span class="sxs-lookup"><span data-stu-id="1edde-111">You can't export segments with fewer than 100 profiles to AdRoll.</span></span> 
- <span data-ttu-id="1edde-112">Az AdRollba való exportálás csak szegmensekre korlátozódik.</span><span class="sxs-lookup"><span data-stu-id="1edde-112">Exporting to AdRoll is limited to segments.</span></span>
- <span data-ttu-id="1edde-113">Legfeljebb 250 000 profil az AdRollba való exportálása eltarthat 10 percig.</span><span class="sxs-lookup"><span data-stu-id="1edde-113">Exporting up to 250'000 profiles to AdRoll can take up to 10 minutes to complete.</span></span> 
- <span data-ttu-id="1edde-114">A Marketoba exportálható profilok száma függ a AdRoll szerződéstől, és korlátozott.</span><span class="sxs-lookup"><span data-stu-id="1edde-114">The number of profiles that you can export to AdRoll is dependent and limited on your contract with AdRoll.</span></span>

## <a name="set-up-connection-to-adroll"></a><span data-ttu-id="1edde-115">Állítsa be az AdRollal való kapcsolatot</span><span class="sxs-lookup"><span data-stu-id="1edde-115">Set up connection to AdRoll</span></span>

1. <span data-ttu-id="1edde-116">Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="1edde-116">Go to **Admin** > **Connections**.</span></span>

1. <span data-ttu-id="1edde-117">Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza az **AdRoll** lehetőséget a kapcsolat konfigurálásához.</span><span class="sxs-lookup"><span data-stu-id="1edde-117">Select **Add connection** and choose **AdRoll** to configure the connection.</span></span>

1. <span data-ttu-id="1edde-118">Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak.</span><span class="sxs-lookup"><span data-stu-id="1edde-118">Give your connection a recognizable name in the **Display name** field.</span></span> <span data-ttu-id="1edde-119">A név és a kapcsolat típusa írja le ezt a kapcsolatot.</span><span class="sxs-lookup"><span data-stu-id="1edde-119">The name and the type of the connection describe this connection.</span></span> <span data-ttu-id="1edde-120">Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.</span><span class="sxs-lookup"><span data-stu-id="1edde-120">We recommend choosing a name that explains the purpose and target of the connection.</span></span>

1. <span data-ttu-id="1edde-121">A kapcsolat használóinak kiválasztása.</span><span class="sxs-lookup"><span data-stu-id="1edde-121">Choose who can use this connection.</span></span> <span data-ttu-id="1edde-122">Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz.</span><span class="sxs-lookup"><span data-stu-id="1edde-122">If you take no action, the default will be Administrators.</span></span> <span data-ttu-id="1edde-123">További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).</span><span class="sxs-lookup"><span data-stu-id="1edde-123">For more information, see [Allow contributors to use a connection for exports](connections.md#allow-contributors-to-use-a-connection-for-exports).</span></span>

1. <span data-ttu-id="1edde-124">Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.</span><span class="sxs-lookup"><span data-stu-id="1edde-124">Select **I agree** to confirm the **Data privacy and compliance**.</span></span>

1. <span data-ttu-id="1edde-125">Válassza a **Csatlakozás** lehetőséget az AdRoll kapcsolat inicializálásához.</span><span class="sxs-lookup"><span data-stu-id="1edde-125">Select **Connect** to initialize the connection to AdRoll.</span></span>

1. <span data-ttu-id="1edde-126">Válassza a **Hitelesítés az AdRoll szolgáltatással** lehetőséget, és adja meg AdRoll rendszergazdai hitelesítő adatait.</span><span class="sxs-lookup"><span data-stu-id="1edde-126">Select **Authenticate with AdRoll** and provide your admin credentials for AdRoll.</span></span> 

1. <span data-ttu-id="1edde-127">Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.</span><span class="sxs-lookup"><span data-stu-id="1edde-127">Select **Add yourself as export user** and provide your Customer Insights credentials.</span></span>

1. <span data-ttu-id="1edde-128">A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="1edde-128">Select **Save** to complete the connection.</span></span>

## <a name="configure-an-export"></a><span data-ttu-id="1edde-129">Exportálás konfigurálása</span><span class="sxs-lookup"><span data-stu-id="1edde-129">Configure an export</span></span>

<span data-ttu-id="1edde-130">Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz.</span><span class="sxs-lookup"><span data-stu-id="1edde-130">You can configure this export if you have access to a connection of this type.</span></span> <span data-ttu-id="1edde-131">További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).</span><span class="sxs-lookup"><span data-stu-id="1edde-131">For more information, see [Permissions needed to configure an export](export-destinations.md#set-up-a-new-export).</span></span>

1. <span data-ttu-id="1edde-132">Menjen az **Adatok** > **Exportálások** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="1edde-132">Go to **Data** > **Exports**.</span></span>

1. <span data-ttu-id="1edde-133">Új exportálás létrehozásához válassza a **Célhely hozzáadása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="1edde-133">To create a new export, select **Add destination**.</span></span>

1. <span data-ttu-id="1edde-134">A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot az AdRoll szakaszból.</span><span class="sxs-lookup"><span data-stu-id="1edde-134">In the **Connection for export** field, choose a connection from the AdRoll section.</span></span> <span data-ttu-id="1edde-135">Ha nem látja ezt a szakasznevet, az Ön számára nincs ilyen típusú kapcsolat.</span><span class="sxs-lookup"><span data-stu-id="1edde-135">If you don't see this section name, there are no connections of this type available to you.</span></span>

1. <span data-ttu-id="1edde-136">Adja meg az **AdRoll Advertiser azonosítóját** További információkért lásd: [AdRoll Advertiser profilok](https://help.adroll.com/hc/articles/212011838-Advertiser-Profiles).</span><span class="sxs-lookup"><span data-stu-id="1edde-136">Enter your **AdRoll Advertiser ID** For more information, see [AdRoll Advertiser Profiles](https://help.adroll.com/hc/articles/212011838-Advertiser-Profiles).</span></span>

3. <span data-ttu-id="1edde-137">Az **Adategyeztetés** szakaszban az **E-mail** mezőben jelölje ki az egyesített ügyfélprofil ügyfél e-mail-címét jelképező mezőjét.</span><span class="sxs-lookup"><span data-stu-id="1edde-137">In the **Data matching** section, in the **Email** field, select the field in your unified customer profile that represents a customer's email address.</span></span> <span data-ttu-id="1edde-138">A szegmenseket exportálni kell az AdRollba.</span><span class="sxs-lookup"><span data-stu-id="1edde-138">It's required to export segments to AdRoll.</span></span>

1. <span data-ttu-id="1edde-139">Jelölje ki a szegmenseket, amelyeket exportálni szeretne.</span><span class="sxs-lookup"><span data-stu-id="1edde-139">Select the segments you want to export.</span></span> <span data-ttu-id="1edde-140">Jelöljön ki egy legalább 100 tagból álló szegmenst.</span><span class="sxs-lookup"><span data-stu-id="1edde-140">Select a segment with a least 100 members.</span></span> <span data-ttu-id="1edde-141">Kisebb szegmensek nem exportálhatók.</span><span class="sxs-lookup"><span data-stu-id="1edde-141">You can't export smaller segments.</span></span> <span data-ttu-id="1edde-142">Az exportálni kívánt szegmens maximális mérete exportálásonként 250 000 tag.</span><span class="sxs-lookup"><span data-stu-id="1edde-142">Additionally the maximum size of a segment to export is 250'000 members per export.</span></span> 

1. <span data-ttu-id="1edde-143">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="1edde-143">Select **Save**.</span></span>

<span data-ttu-id="1edde-144">Az exportálás mentése nem futtatja azonnal az exportálást.</span><span class="sxs-lookup"><span data-stu-id="1edde-144">Saving an export doesn't run the export immediately.</span></span>

<span data-ttu-id="1edde-145">Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut.</span><span class="sxs-lookup"><span data-stu-id="1edde-145">The export runs with every [scheduled refresh](system.md#schedule-tab).</span></span> <span data-ttu-id="1edde-146">Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand).</span><span class="sxs-lookup"><span data-stu-id="1edde-146">You can also [export data on demand](export-destinations.md#run-exports-on-demand).</span></span> 


## <a name="data-privacy-and-compliance"></a><span data-ttu-id="1edde-147">Adatvédelem és megfelelőség</span><span class="sxs-lookup"><span data-stu-id="1edde-147">Data privacy and compliance</span></span>

<span data-ttu-id="1edde-148">Amikor engedélyezi a Dynamics 365 Customer Insights szolgáltatást az adatok AdRoll szolgáltatásba való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat.</span><span class="sxs-lookup"><span data-stu-id="1edde-148">When you enable Dynamics 365 Customer Insights to transmit data to AdRoll, you allow transfer of data outside of the compliance boundary for Dynamics 365 Customer Insights, including potentially sensitive data such as Personal Data.</span></span> <span data-ttu-id="1edde-149">A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy az AdRoll megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek.</span><span class="sxs-lookup"><span data-stu-id="1edde-149">Microsoft will transfer such data at your instruction, but you are responsible for ensuring that AdRoll meets any privacy or security obligations you may have.</span></span> <span data-ttu-id="1edde-150">További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).</span><span class="sxs-lookup"><span data-stu-id="1edde-150">For more information, see [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?linkid=396732).</span></span>

<span data-ttu-id="1edde-151">A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.</span><span class="sxs-lookup"><span data-stu-id="1edde-151">Your Dynamics 365 Customer Insights Administrator can remove this export destination at any time to discontinue use of this functionality.</span></span>
