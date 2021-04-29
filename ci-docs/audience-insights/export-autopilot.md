---
title: Customer Insights adatok exportálása az Autopilotba
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja az Autopilotba.
ms.date: 03/03/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: e320a48d5b7c35b530e3a38567b226b804879e4e
ms.sourcegitcommit: 1b671c6100991fea1cace04b5d4fcedcd88aa94f
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/31/2021
ms.locfileid: "5760146"
---
# <a name="export-segments-to-autopilot-preview"></a><span data-ttu-id="0fb5d-103">Szegmensek exportálása az Autopilotba (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="0fb5d-103">Export segments to Autopilot (preview)</span></span>

<span data-ttu-id="0fb5d-104">Exportálja az egyesített ügyfélprofilok szegmenseit az Autopilotba, és használja őket kampányokhoz és e-mail marketinghez az Autopilotban.</span><span class="sxs-lookup"><span data-stu-id="0fb5d-104">Export segments of unified customer profiles to Autopilot and use them for email marketing in Autopilot.</span></span> 

## <a name="prerequisites-for-a-connection"></a><span data-ttu-id="0fb5d-105">Egy kapcsolat előfeltételei</span><span class="sxs-lookup"><span data-stu-id="0fb5d-105">Prerequisites for a connection</span></span>

-   <span data-ttu-id="0fb5d-106">Rendelkezik [Autopilot-fiókkal](https://www.autopilothq.com/) és a megfelelő rendszergazdai hitelesítő adatokkal.</span><span class="sxs-lookup"><span data-stu-id="0fb5d-106">You have an [Autopilot account](https://www.autopilothq.com/) and corresponding administrator credentials.</span></span>
-   <span data-ttu-id="0fb5d-107">[Konfigurált szegmensekkel](segments.md) rendelkezik a célközönségi-információkban.</span><span class="sxs-lookup"><span data-stu-id="0fb5d-107">You have [configured segments](segments.md) in audience insights.</span></span>
-   <span data-ttu-id="0fb5d-108">Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.</span><span class="sxs-lookup"><span data-stu-id="0fb5d-108">Unified customer profiles in the exported segments contain a field representing an email address.</span></span>

## <a name="known-limitations"></a><span data-ttu-id="0fb5d-109">Ismert korlátozások</span><span class="sxs-lookup"><span data-stu-id="0fb5d-109">Known limitations</span></span>

- <span data-ttu-id="0fb5d-110">Összesen legfeljebb 100 000 ügyfélprofilt exportálhat az Autopilotba.</span><span class="sxs-lookup"><span data-stu-id="0fb5d-110">You can export up to 100'000 profiles in total to Autopilot.</span></span>
- <span data-ttu-id="0fb5d-111">Az Autopilotba való exportálás csak szegmensekre korlátozódik.</span><span class="sxs-lookup"><span data-stu-id="0fb5d-111">Exporting to Autopilot is limited to segments.</span></span>
- <span data-ttu-id="0fb5d-112">Akár 100 000 profil Autopilotba való exportálása néhány órát is igénybe vehet.</span><span class="sxs-lookup"><span data-stu-id="0fb5d-112">Exporting up to 100'000 profiles to Autopilot can take up to a few hours to complete.</span></span> 
- <span data-ttu-id="0fb5d-113">Az Autopilotba exportálható profilok száma függ az Autopilot szerződésről, és korlátozott.</span><span class="sxs-lookup"><span data-stu-id="0fb5d-113">The number of profiles that you can export to Autopilot is dependent and limited on your contract with Autopilot.</span></span>

## <a name="set-up-connection-to-autopilot"></a><span data-ttu-id="0fb5d-114">Állítsa be az Autopilottal való kapcsolatot</span><span class="sxs-lookup"><span data-stu-id="0fb5d-114">Set up connection to Autopilot</span></span>

1. <span data-ttu-id="0fb5d-115">Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="0fb5d-115">Go to **Admin** > **Connections**.</span></span>

1. <span data-ttu-id="0fb5d-116">Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza az **Autopilot** lehetőséget a kapcsolat konfigurálásához.</span><span class="sxs-lookup"><span data-stu-id="0fb5d-116">Select **Add connection** and choose **Autopilot** to configure the connection.</span></span>

1. <span data-ttu-id="0fb5d-117">Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak.</span><span class="sxs-lookup"><span data-stu-id="0fb5d-117">Give your connection a recognizable name in the **Display name** field.</span></span> <span data-ttu-id="0fb5d-118">A név és a kapcsolat típusa írja le ezt a kapcsolatot.</span><span class="sxs-lookup"><span data-stu-id="0fb5d-118">The name and the type of the connection describe this connection.</span></span> <span data-ttu-id="0fb5d-119">Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.</span><span class="sxs-lookup"><span data-stu-id="0fb5d-119">We recommend choosing a name that explains the purpose and target of the connection.</span></span>

1. <span data-ttu-id="0fb5d-120">A kapcsolat használóinak kiválasztása.</span><span class="sxs-lookup"><span data-stu-id="0fb5d-120">Choose who can use this connection.</span></span> <span data-ttu-id="0fb5d-121">Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz.</span><span class="sxs-lookup"><span data-stu-id="0fb5d-121">If you take no action, the default will be Administrators.</span></span> <span data-ttu-id="0fb5d-122">További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).</span><span class="sxs-lookup"><span data-stu-id="0fb5d-122">For more information, see [Allow contributors to use a connection for exports](connections.md#allow-contributors-to-use-a-connection-for-exports).</span></span>

3. <span data-ttu-id="0fb5d-123">Adja meg az [Autopilot API-kulcsát](https://autopilot.docs.apiary.io/#).</span><span class="sxs-lookup"><span data-stu-id="0fb5d-123">Enter your [Autopilot API key](https://autopilot.docs.apiary.io/#).</span></span>

1. <span data-ttu-id="0fb5d-124">Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.</span><span class="sxs-lookup"><span data-stu-id="0fb5d-124">Select **I agree** to confirm the **Data privacy and compliance**.</span></span>

1. <span data-ttu-id="0fb5d-125">Válassza a **Csatlakozás** lehetőséget az Autopilot kapcsolat inicializálásához.</span><span class="sxs-lookup"><span data-stu-id="0fb5d-125">Select **Connect** to initialize the connection to Autopilot.</span></span>

1. <span data-ttu-id="0fb5d-126">Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.</span><span class="sxs-lookup"><span data-stu-id="0fb5d-126">Select **Add yourself as export user** and provide your Customer Insights credentials.</span></span>

1. <span data-ttu-id="0fb5d-127">A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="0fb5d-127">Select **Save** to complete the connection.</span></span>

## <a name="configure-an-export"></a><span data-ttu-id="0fb5d-128">Exportálás konfigurálása</span><span class="sxs-lookup"><span data-stu-id="0fb5d-128">Configure an export</span></span>

<span data-ttu-id="0fb5d-129">Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz.</span><span class="sxs-lookup"><span data-stu-id="0fb5d-129">You can configure this export if you have access to a connection of this type.</span></span> <span data-ttu-id="0fb5d-130">További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).</span><span class="sxs-lookup"><span data-stu-id="0fb5d-130">For more information, see [Permissions needed to configure an export](export-destinations.md#set-up-a-new-export).</span></span>

1. <span data-ttu-id="0fb5d-131">Menjen az **Adatok** > **Exportálások** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="0fb5d-131">Go to **Data** > **Exports**.</span></span>

1. <span data-ttu-id="0fb5d-132">Új exportálás létrehozásához válassza a **Célhely hozzáadása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="0fb5d-132">To create a new export, select **Add destination**.</span></span>

1. <span data-ttu-id="0fb5d-133">A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot az Autopilot szakaszból.</span><span class="sxs-lookup"><span data-stu-id="0fb5d-133">In the **Connection for export** field, choose a connection from the Autopilot section.</span></span> <span data-ttu-id="0fb5d-134">Ha nem látja ezt a szakasznevet, az Ön számára nincs ilyen típusú kapcsolat.</span><span class="sxs-lookup"><span data-stu-id="0fb5d-134">If you don't see this section name, there are no connections of this type available to you.</span></span>

3. <span data-ttu-id="0fb5d-135">Az **Adategyeztetés** szakaszban az **E-mail** mezőben jelölje ki az egyesített ügyfélprofil ügyfél e-mail-címét jelképező mezőjét.</span><span class="sxs-lookup"><span data-stu-id="0fb5d-135">In the **Data matching** section, in the **Email** field, select the field in your unified customer profile that represents a customer's email address.</span></span> <span data-ttu-id="0fb5d-136">Ismételje meg ugyanezeket a lépéseket az egyéb választható mezőkön, például az **Utónév**, a **Vezetéknév**.</span><span class="sxs-lookup"><span data-stu-id="0fb5d-136">Repeat the same steps for other optional fields such as **First name**, **Last name**.</span></span>

1. <span data-ttu-id="0fb5d-137">Jelölje ki a szegmenseket, amelyeket exportálni szeretne.</span><span class="sxs-lookup"><span data-stu-id="0fb5d-137">Select the segments you want to export.</span></span> <span data-ttu-id="0fb5d-138">Fokozottan **javasoljuk, hogy ne exportáljon összesen 100 000-nél több ügyfélprofilt** az Autopilotba.</span><span class="sxs-lookup"><span data-stu-id="0fb5d-138">We strongly **recommend to not export more than 100'000 customer profiles in total** to Autopilot.</span></span> 

1. <span data-ttu-id="0fb5d-139">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="0fb5d-139">Select **Save**.</span></span>

<span data-ttu-id="0fb5d-140">Az exportálás mentése nem futtatja azonnal az exportálást.</span><span class="sxs-lookup"><span data-stu-id="0fb5d-140">Saving an export doesn't run the export immediately.</span></span>

<span data-ttu-id="0fb5d-141">Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut.</span><span class="sxs-lookup"><span data-stu-id="0fb5d-141">The export runs with every [scheduled refresh](system.md#schedule-tab).</span></span> <span data-ttu-id="0fb5d-142">Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand).</span><span class="sxs-lookup"><span data-stu-id="0fb5d-142">You can also [export data on demand](export-destinations.md#run-exports-on-demand).</span></span> 

## <a name="data-privacy-and-compliance"></a><span data-ttu-id="0fb5d-143">Adatvédelem és megfelelőség</span><span class="sxs-lookup"><span data-stu-id="0fb5d-143">Data privacy and compliance</span></span>

<span data-ttu-id="0fb5d-144">Amikor engedélyezi a Dynamics 365 Customer Insights szolgáltatást az adatok Autopilot szolgáltatásba való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat.</span><span class="sxs-lookup"><span data-stu-id="0fb5d-144">When you enable Dynamics 365 Customer Insights to transmit data to Autopilot, you allow transfer of data outside of the compliance boundary for Dynamics 365 Customer Insights, including potentially sensitive data such as Personal Data.</span></span> <span data-ttu-id="0fb5d-145">A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy az Autopilot megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek.</span><span class="sxs-lookup"><span data-stu-id="0fb5d-145">Microsoft will transfer such data at your instruction, but you are responsible for ensuring that Autopilot meet any privacy or security obligations you may have.</span></span> <span data-ttu-id="0fb5d-146">További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).</span><span class="sxs-lookup"><span data-stu-id="0fb5d-146">For more information, see [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?linkid=396732).</span></span>
<span data-ttu-id="0fb5d-147">A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.</span><span class="sxs-lookup"><span data-stu-id="0fb5d-147">Your Dynamics 365 Customer Insights Administrator can remove this export destination at any time to discontinue use of this functionality.</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]
