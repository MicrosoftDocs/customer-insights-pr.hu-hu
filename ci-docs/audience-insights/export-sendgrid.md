---
title: Customer Insights adatok exportálása a SendGridbe
description: Megismerheti, hogyan konfigurálható a kapcsolat a SendGriddel.
ms.date: 12/08/2020
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: phkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 1a1f679fa42d47d524ebfdd6e931ae2822565f77
ms.sourcegitcommit: bae40184312ab27b95c140a044875c2daea37951
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/15/2021
ms.locfileid: "5597284"
---
# <a name="connector-for-sendgrid-preview"></a><span data-ttu-id="d535a-103">A SendGrid összekötője (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="d535a-103">Connector for SendGrid (preview)</span></span>

<span data-ttu-id="d535a-104">Exportálja az egyesített ügyfélprofilok szegmenseit a SendGrid partnerlistákba, és használja őket kampányokhoz és e-mail marketinghez a SendGridben.</span><span class="sxs-lookup"><span data-stu-id="d535a-104">Export segments of unified customer profiles to SendGrid contact lists and use them for campaigns and email marketing in SendGrid.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="d535a-105">Előfeltételek</span><span class="sxs-lookup"><span data-stu-id="d535a-105">Prerequisites</span></span>

-   <span data-ttu-id="d535a-106">Rendelkezik [SendGrid-fiókkal](https://sendgrid.com/) és a megfelelő rendszergazdai hitelesítő adatokkal.</span><span class="sxs-lookup"><span data-stu-id="d535a-106">You have a [SendGrid account](https://sendgrid.com/) and corresponding administrator credentials.</span></span>
-   <span data-ttu-id="d535a-107">A SendGridben és a megfelelő azonosítókban meglévő partnerlisták találhatók.</span><span class="sxs-lookup"><span data-stu-id="d535a-107">There are existing contact lists in SendGrid and the corresponding IDs.</span></span> <span data-ttu-id="d535a-108">További információért lásd: [SendGrid – Kapcsolattartók kezelése](https://sendgrid.com/docs/ui/managing-contacts/create-and-manage-contacts/#manage-contacts).</span><span class="sxs-lookup"><span data-stu-id="d535a-108">For more information, see [SendGrid - Manage contacts](https://sendgrid.com/docs/ui/managing-contacts/create-and-manage-contacts/#manage-contacts).</span></span>
-   <span data-ttu-id="d535a-109">[Konfigurált szegmensekkel](segments.md) rendelkezik a célközönségi-információkban.</span><span class="sxs-lookup"><span data-stu-id="d535a-109">You have [configured segments](segments.md) in audience insights.</span></span>
-   <span data-ttu-id="d535a-110">Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.</span><span class="sxs-lookup"><span data-stu-id="d535a-110">Unified customer profiles in the exported segments contain a field representing an email address.</span></span>

## <a name="connect-to-sendgrid"></a><span data-ttu-id="d535a-111">Csatlakozás a SendGridhez</span><span class="sxs-lookup"><span data-stu-id="d535a-111">Connect to SendGrid</span></span>

1. <span data-ttu-id="d535a-112">Válassz a **Rendszergazda** > **Célok exportálása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="d535a-112">Go to **Admin** > **Export destinations**.</span></span>

1. <span data-ttu-id="d535a-113">A **SendGrid** részben válassza a **Beállítás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="d535a-113">Under **SendGrid**, select **Set up**.</span></span>

1. <span data-ttu-id="d535a-114">Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben az export helyének.</span><span class="sxs-lookup"><span data-stu-id="d535a-114">Give your export destination a recognizable name in the **Display name** field.</span></span>

   :::image type="content" source="media/export-sendgrid.PNG" alt-text="SendGrid exportálás konfigurációs panel.":::

1. <span data-ttu-id="d535a-116">Adja meg **SendGrid API-kulcsot** [SendGrid API-kulcs](https://sendgrid.com/docs/ui/account-and-settings/api-keys/).</span><span class="sxs-lookup"><span data-stu-id="d535a-116">Enter your **SendGrid API key** [SendGrid API key](https://sendgrid.com/docs/ui/account-and-settings/api-keys/).</span></span>

1. <span data-ttu-id="d535a-117">Adja meg a **[SendGrid lista azonosítóját](https://sendgrid.com/docs/ui/managing-contacts/create-and-manage-contacts/#manage-contacts)**.</span><span class="sxs-lookup"><span data-stu-id="d535a-117">Enter your **[SendGrid list ID](https://sendgrid.com/docs/ui/managing-contacts/create-and-manage-contacts/#manage-contacts)**.</span></span>

1. <span data-ttu-id="d535a-118">Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.</span><span class="sxs-lookup"><span data-stu-id="d535a-118">Select **I agree** to confirm the **Data privacy and compliance**.</span></span>

1. <span data-ttu-id="d535a-119">Válassza a **Csatlakozás** lehetőséget a SendGrid kapcsolat inicializálásához.</span><span class="sxs-lookup"><span data-stu-id="d535a-119">Select **Connect** to initialize the connection to SendGrid.</span></span>

1. <span data-ttu-id="d535a-120">Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.</span><span class="sxs-lookup"><span data-stu-id="d535a-120">Select **Add yourself as export user** and provide your Customer Insights credentials.</span></span>

1. <span data-ttu-id="d535a-121">Az Exportálás konfigurálásához válassza a **Tovább** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="d535a-121">Select **Next** to configure the export.</span></span>

## <a name="configure-the-connector"></a><span data-ttu-id="d535a-122">Konfigurálja az összekötőt</span><span class="sxs-lookup"><span data-stu-id="d535a-122">Configure the connector</span></span>

1. <span data-ttu-id="d535a-123">Az **Adategyeztetés** szakaszban az **E-mail** mezőben jelölje ki az egyesített ügyfélprofil ügyfél e-mail-címét jelképező mezőjét.</span><span class="sxs-lookup"><span data-stu-id="d535a-123">In the **Data matching** section, in the **Email** field, select the field in your unified customer profile that represents a customer's email address.</span></span> <span data-ttu-id="d535a-124">Ismételje meg ugyanezeket a lépéseket az egyéb választható mezőkön, például az **Utónév**, a **Vezetéknév**, **Ország/régió**, **Állam** **Város** és **Irányítószám mezőben**.</span><span class="sxs-lookup"><span data-stu-id="d535a-124">Repeat the same steps for other optional fields such as **First name**, **Last name**, **Country/Region**, **State**, **City**, and **Post code**.</span></span>

1. <span data-ttu-id="d535a-125">Jelölje ki a szegmenseket, amelyeket exportálni szeretne.</span><span class="sxs-lookup"><span data-stu-id="d535a-125">Select the segments you want to export.</span></span> <span data-ttu-id="d535a-126">**Javasoljuk, hogy ne exportáljon összesen 100 000-nél több ügyfélprofilt** a SendGridbe.</span><span class="sxs-lookup"><span data-stu-id="d535a-126">We strongly **recommend to not export more than 100'000 customer profiles in total** to SendGrid.</span></span> 

1. <span data-ttu-id="d535a-127">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="d535a-127">Select **Save**.</span></span>

## <a name="export-the-data"></a><span data-ttu-id="d535a-128">Az adatok exportálása</span><span class="sxs-lookup"><span data-stu-id="d535a-128">Export the data</span></span>

<span data-ttu-id="d535a-129">[Igény szerint exportálhatja az adatot](export-destinations.md).</span><span class="sxs-lookup"><span data-stu-id="d535a-129">You can [export data on demand](export-destinations.md).</span></span> <span data-ttu-id="d535a-130">Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) együtt is lefut.</span><span class="sxs-lookup"><span data-stu-id="d535a-130">The export will also run with every [scheduled refresh](system.md#schedule-tab).</span></span>

## <a name="known-limitations"></a><span data-ttu-id="d535a-131">Ismert korlátozások</span><span class="sxs-lookup"><span data-stu-id="d535a-131">Known limitations</span></span>

- <span data-ttu-id="d535a-132">Összesen legfeljebb 100 000 profil a SendGrid számára.</span><span class="sxs-lookup"><span data-stu-id="d535a-132">Up to 100'000 profiles in total to SendGrid.</span></span>
- <span data-ttu-id="d535a-133">A SendGridbe való exportálás csak szegmensekre korlátozódik.</span><span class="sxs-lookup"><span data-stu-id="d535a-133">Exporting to SendGrid is limited to segments.</span></span>
- <span data-ttu-id="d535a-134">Akár 100 000 profil SendGridbe való exportálása néhány órát is igénybe vehet.</span><span class="sxs-lookup"><span data-stu-id="d535a-134">Exporting up to 100'000 profiles to SendGrid can take up to a few hours to complete.</span></span> 
- <span data-ttu-id="d535a-135">A SendGridbe exportálható profilok száma függ a SendGrid szerződésről, és korlátozott.</span><span class="sxs-lookup"><span data-stu-id="d535a-135">The number of profiles that you can export to SendGrid is dependent and limited on your contract with SendGrid.</span></span>

## <a name="data-privacy-and-compliance"></a><span data-ttu-id="d535a-136">Adatvédelem és megfelelőség</span><span class="sxs-lookup"><span data-stu-id="d535a-136">Data privacy and compliance</span></span>

<span data-ttu-id="d535a-137">Amikor engedélyezi az Dynamics 365 Customer Insights szolgáltatást az adatok SendGridbe való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat.</span><span class="sxs-lookup"><span data-stu-id="d535a-137">When you enable Dynamics 365 Customer Insights to transmit data to SendGrid, you allow transfer of data outside of the compliance boundary for Dynamics 365 Customer Insights, including potentially sensitive data such as Personal Data.</span></span> <span data-ttu-id="d535a-138">A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy a SendGrid megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek.</span><span class="sxs-lookup"><span data-stu-id="d535a-138">Microsoft will transfer such data at your instruction, but you are responsible for ensuring that SendGrid meet any privacy or security obligations you may have.</span></span> <span data-ttu-id="d535a-139">További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).</span><span class="sxs-lookup"><span data-stu-id="d535a-139">For more information, see [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?linkid=396732).</span></span>
<span data-ttu-id="d535a-140">A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.</span><span class="sxs-lookup"><span data-stu-id="d535a-140">Your Dynamics 365 Customer Insights Administrator can remove this export destination at any time to discontinue use of this functionality.</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]