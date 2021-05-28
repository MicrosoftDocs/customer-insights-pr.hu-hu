---
title: Customer Insights adatok exportálása a SendGridbe
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a SendGridbe.
ms.date: 03/03/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 5d3d61d2b5b68079c7717e41dee5a2f698f2b62c
ms.sourcegitcommit: e8e03309ba2515374a70c132d0758f3e1e1851d0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/04/2021
ms.locfileid: "5976919"
---
# <a name="export-segments-to-sendgrid-preview"></a><span data-ttu-id="f5c87-103">Szegmensek exportálása a SendGridbe (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="f5c87-103">Export segments to SendGrid (preview)</span></span>

<span data-ttu-id="f5c87-104">Exportálja az egyesített ügyfélprofilok szegmenseit a SendGrid partnerlistákba, és használja őket kampányokhoz és e-mail marketinghez a SendGridben.</span><span class="sxs-lookup"><span data-stu-id="f5c87-104">Export segments of unified customer profiles to SendGrid contact lists and use them for campaigns and email marketing in SendGrid.</span></span> 

## <a name="prerequisites-for-a-connection"></a><span data-ttu-id="f5c87-105">Egy kapcsolat előfeltételei</span><span class="sxs-lookup"><span data-stu-id="f5c87-105">Prerequisites for a connection</span></span>

-   <span data-ttu-id="f5c87-106">Rendelkezik [SendGrid-fiókkal](https://sendgrid.com/) és a megfelelő rendszergazdai hitelesítő adatokkal.</span><span class="sxs-lookup"><span data-stu-id="f5c87-106">You have a [SendGrid account](https://sendgrid.com/) and corresponding administrator credentials.</span></span>
-   <span data-ttu-id="f5c87-107">A SendGridben és a megfelelő azonosítókban meglévő partnerlisták találhatók.</span><span class="sxs-lookup"><span data-stu-id="f5c87-107">There are existing contact lists in SendGrid and the corresponding IDs.</span></span> <span data-ttu-id="f5c87-108">További információért lásd: [SendGrid – Kapcsolattartók kezelése](https://sendgrid.com/docs/ui/managing-contacts/create-and-manage-contacts/#manage-contacts).</span><span class="sxs-lookup"><span data-stu-id="f5c87-108">For more information, see [SendGrid - Manage contacts](https://sendgrid.com/docs/ui/managing-contacts/create-and-manage-contacts/#manage-contacts).</span></span>
-   <span data-ttu-id="f5c87-109">[Konfigurált szegmensekkel](segments.md) rendelkezik a célközönségi-információkban.</span><span class="sxs-lookup"><span data-stu-id="f5c87-109">You have [configured segments](segments.md) in audience insights.</span></span>
-   <span data-ttu-id="f5c87-110">Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.</span><span class="sxs-lookup"><span data-stu-id="f5c87-110">Unified customer profiles in the exported segments contain a field representing an email address.</span></span>

## <a name="known-limitations"></a><span data-ttu-id="f5c87-111">Ismert korlátozások</span><span class="sxs-lookup"><span data-stu-id="f5c87-111">Known limitations</span></span>

- <span data-ttu-id="f5c87-112">Összesen legfeljebb 100 000 profil a SendGrid számára.</span><span class="sxs-lookup"><span data-stu-id="f5c87-112">Up to 100'000 profiles in total to SendGrid.</span></span>
- <span data-ttu-id="f5c87-113">A SendGridbe való exportálás csak szegmensekre korlátozódik.</span><span class="sxs-lookup"><span data-stu-id="f5c87-113">Exporting to SendGrid is limited to segments.</span></span>
- <span data-ttu-id="f5c87-114">Akár 100 000 profil SendGridbe való exportálása néhány órát is igénybe vehet.</span><span class="sxs-lookup"><span data-stu-id="f5c87-114">Exporting up to 100'000 profiles to SendGrid can take up to a few hours to complete.</span></span> 
- <span data-ttu-id="f5c87-115">A SendGridbe exportálható profilok száma függ a SendGrid szerződésről, és korlátozott.</span><span class="sxs-lookup"><span data-stu-id="f5c87-115">The number of profiles that you can export to SendGrid is dependent and limited on your contract with SendGrid.</span></span>

## <a name="set-up-connection-to-sendgrid"></a><span data-ttu-id="f5c87-116">Állítsa be a SendGriddel való kapcsolatot</span><span class="sxs-lookup"><span data-stu-id="f5c87-116">Set up connection to SendGrid</span></span>

1. <span data-ttu-id="f5c87-117">Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="f5c87-117">Go to **Admin** > **Connections**.</span></span>

1. <span data-ttu-id="f5c87-118">Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza a **SendGrid** lehetőséget a kapcsolat konfigurálásához.</span><span class="sxs-lookup"><span data-stu-id="f5c87-118">Select **Add connection** and choose **SendGrid** to configure the connection.</span></span>

1. <span data-ttu-id="f5c87-119">Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak.</span><span class="sxs-lookup"><span data-stu-id="f5c87-119">Give your connection a recognizable name in the **Display name** field.</span></span> <span data-ttu-id="f5c87-120">A név és a kapcsolat típusa írja le ezt a kapcsolatot.</span><span class="sxs-lookup"><span data-stu-id="f5c87-120">The name and the type of the connection describe this connection.</span></span> <span data-ttu-id="f5c87-121">Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.</span><span class="sxs-lookup"><span data-stu-id="f5c87-121">We recommend choosing a name that explains the purpose and target of the connection.</span></span>

1. <span data-ttu-id="f5c87-122">A kapcsolat használóinak kiválasztása.</span><span class="sxs-lookup"><span data-stu-id="f5c87-122">Choose who can use this connection.</span></span> <span data-ttu-id="f5c87-123">Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz.</span><span class="sxs-lookup"><span data-stu-id="f5c87-123">If you take no action, the default will be Administrators.</span></span> <span data-ttu-id="f5c87-124">További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).</span><span class="sxs-lookup"><span data-stu-id="f5c87-124">For more information, see [Allow contributors to use a connection for exports](connections.md#allow-contributors-to-use-a-connection-for-exports).</span></span>

1. <span data-ttu-id="f5c87-125">Adja meg **SendGrid API-kulcsot** [SendGrid API-kulcs](https://sendgrid.com/docs/ui/account-and-settings/api-keys/).</span><span class="sxs-lookup"><span data-stu-id="f5c87-125">Enter your **SendGrid API key** [SendGrid API key](https://sendgrid.com/docs/ui/account-and-settings/api-keys/).</span></span>

1. <span data-ttu-id="f5c87-126">Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.</span><span class="sxs-lookup"><span data-stu-id="f5c87-126">Select **I agree** to confirm the **Data privacy and compliance**.</span></span>

1. <span data-ttu-id="f5c87-127">Válassza a **Csatlakozás** lehetőséget a SendGrid kapcsolat inicializálásához.</span><span class="sxs-lookup"><span data-stu-id="f5c87-127">Select **Connect** to initialize the connection to SendGrid.</span></span>

1. <span data-ttu-id="f5c87-128">Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.</span><span class="sxs-lookup"><span data-stu-id="f5c87-128">Select **Add yourself as export user** and provide your Customer Insights credentials.</span></span>

1. <span data-ttu-id="f5c87-129">A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="f5c87-129">Select **Save** to complete the connection.</span></span>

## <a name="configure-an-export"></a><span data-ttu-id="f5c87-130">Exportálás konfigurálása</span><span class="sxs-lookup"><span data-stu-id="f5c87-130">Configure an export</span></span>

<span data-ttu-id="f5c87-131">Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz.</span><span class="sxs-lookup"><span data-stu-id="f5c87-131">You can configure this export if you have access to a connection of this type.</span></span> <span data-ttu-id="f5c87-132">További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).</span><span class="sxs-lookup"><span data-stu-id="f5c87-132">For more information, see [Permissions needed to configure an export](export-destinations.md#set-up-a-new-export).</span></span>

1. <span data-ttu-id="f5c87-133">Menjen az **Adatok** > **Exportálások** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="f5c87-133">Go to **Data** > **Exports**.</span></span>

1. <span data-ttu-id="f5c87-134">Új exportálás létrehozásához válassza a **Célhely hozzáadása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="f5c87-134">To create a new export, select **Add destination**.</span></span>

1. <span data-ttu-id="f5c87-135">A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot a SendGrid szakaszból.</span><span class="sxs-lookup"><span data-stu-id="f5c87-135">In the **Connection for export** field, choose a connection from the SendGrid section.</span></span> <span data-ttu-id="f5c87-136">Ha nem látja ezt a szakasznevet, az Ön számára nincs ilyen típusú kapcsolat.</span><span class="sxs-lookup"><span data-stu-id="f5c87-136">If you don't see this section name, there are no connections of this type available to you.</span></span>

1. <span data-ttu-id="f5c87-137">Adja meg a **[SendGrid lista azonosítóját](https://sendgrid.com/docs/ui/managing-contacts/create-and-manage-contacts/#manage-contacts)**.</span><span class="sxs-lookup"><span data-stu-id="f5c87-137">Enter your **[SendGrid list ID](https://sendgrid.com/docs/ui/managing-contacts/create-and-manage-contacts/#manage-contacts)**.</span></span>

1. <span data-ttu-id="f5c87-138">Az **Adategyeztetés** szakaszban az **E-mail** mezőben jelölje ki az egyesített ügyfélprofil ügyfél e-mail-címét jelképező mezőjét.</span><span class="sxs-lookup"><span data-stu-id="f5c87-138">In the **Data matching** section, in the **Email** field, select the field in your unified customer profile that represents a customer's email address.</span></span> <span data-ttu-id="f5c87-139">Ismételje meg ugyanezeket a lépéseket az egyéb választható mezőkön, például az **Utónév**, a **Vezetéknév**, **Ország/régió**, **Állam** **Város** és **Irányítószám mezőben**.</span><span class="sxs-lookup"><span data-stu-id="f5c87-139">Repeat the same steps for other optional fields such as **First name**, **Last name**, **Country/Region**, **State**, **City**, and **Post code**.</span></span>

1. <span data-ttu-id="f5c87-140">Jelölje ki a szegmenseket, amelyeket exportálni szeretne.</span><span class="sxs-lookup"><span data-stu-id="f5c87-140">Select the segments you want to export.</span></span> <span data-ttu-id="f5c87-141">**Javasoljuk, hogy ne exportáljon összesen 100 000-nél több ügyfélprofilt** a SendGridbe.</span><span class="sxs-lookup"><span data-stu-id="f5c87-141">We strongly **recommend to not export more than 100'000 customer profiles in total** to SendGrid.</span></span> 

1. <span data-ttu-id="f5c87-142">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="f5c87-142">Select **Save**.</span></span>

<span data-ttu-id="f5c87-143">Az exportálás mentése nem futtatja azonnal az exportálást.</span><span class="sxs-lookup"><span data-stu-id="f5c87-143">Saving an export doesn't run the export immediately.</span></span>

<span data-ttu-id="f5c87-144">Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut.</span><span class="sxs-lookup"><span data-stu-id="f5c87-144">The export runs with every [scheduled refresh](system.md#schedule-tab).</span></span> <span data-ttu-id="f5c87-145">Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand).</span><span class="sxs-lookup"><span data-stu-id="f5c87-145">You can also [export data on demand](export-destinations.md#run-exports-on-demand).</span></span> 

## <a name="data-privacy-and-compliance"></a><span data-ttu-id="f5c87-146">Adatvédelem és megfelelőség</span><span class="sxs-lookup"><span data-stu-id="f5c87-146">Data privacy and compliance</span></span>

<span data-ttu-id="f5c87-147">Amikor engedélyezi az Dynamics 365 Customer Insights szolgáltatást az adatok SendGridbe való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat.</span><span class="sxs-lookup"><span data-stu-id="f5c87-147">When you enable Dynamics 365 Customer Insights to transmit data to SendGrid, you allow transfer of data outside of the compliance boundary for Dynamics 365 Customer Insights, including potentially sensitive data such as Personal Data.</span></span> <span data-ttu-id="f5c87-148">A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy a SendGrid megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek.</span><span class="sxs-lookup"><span data-stu-id="f5c87-148">Microsoft will transfer such data at your instruction, but you are responsible for ensuring that SendGrid meet any privacy or security obligations you may have.</span></span> <span data-ttu-id="f5c87-149">További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).</span><span class="sxs-lookup"><span data-stu-id="f5c87-149">For more information, see [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?linkid=396732).</span></span>
<span data-ttu-id="f5c87-150">A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.</span><span class="sxs-lookup"><span data-stu-id="f5c87-150">Your Dynamics 365 Customer Insights Administrator can remove this export destination at any time to discontinue use of this functionality.</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]