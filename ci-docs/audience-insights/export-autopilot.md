---
title: Customer Insights adatok exportálása az Autopilotba
description: Megismerheti, hogyan konfigurálható a kapcsolat a Autopilottal.
ms.date: 12/08/2020
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 6d039c4afd84eaad942d214d4e6fb8ef7b1ec72a
ms.sourcegitcommit: bae40184312ab27b95c140a044875c2daea37951
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/15/2021
ms.locfileid: "5596133"
---
# <a name="connector-for-autopilot-preview"></a><span data-ttu-id="d6317-103">Az Autopilot összekötője (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="d6317-103">Connector for Autopilot (preview)</span></span>

<span data-ttu-id="d6317-104">Exportálja az egyesített ügyfélprofilok szegmenseit az Autopilotba, és használja őket kampányokhoz és e-mail marketinghez az Autopilotban.</span><span class="sxs-lookup"><span data-stu-id="d6317-104">Export segments of unified customer profiles to Autopilot and use them for email marketing in Autopilot.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="d6317-105">Előfeltételek</span><span class="sxs-lookup"><span data-stu-id="d6317-105">Prerequisites</span></span>

-   <span data-ttu-id="d6317-106">Rendelkezik [Autopilot-fiókkal](https://www.autopilothq.com/) és a megfelelő rendszergazdai hitelesítő adatokkal.</span><span class="sxs-lookup"><span data-stu-id="d6317-106">You have an [Autopilot account](https://www.autopilothq.com/) and corresponding administrator credentials.</span></span>
-   <span data-ttu-id="d6317-107">[Konfigurált szegmensekkel](segments.md) rendelkezik a célközönségi-információkban.</span><span class="sxs-lookup"><span data-stu-id="d6317-107">You have [configured segments](segments.md) in audience insights.</span></span>
-   <span data-ttu-id="d6317-108">Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.</span><span class="sxs-lookup"><span data-stu-id="d6317-108">Unified customer profiles in the exported segments contain a field representing an email address.</span></span>

## <a name="connect-to-autopilot"></a><span data-ttu-id="d6317-109">Csatlakozás az AutoPilothoz</span><span class="sxs-lookup"><span data-stu-id="d6317-109">Connect to Autopilot</span></span>

1. <span data-ttu-id="d6317-110">Válassz a **Rendszergazda** > **Célok exportálása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="d6317-110">Go to **Admin** > **Export destinations**.</span></span>

1. <span data-ttu-id="d6317-111">Az **Autopilot** részben válassza a **Beállítás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="d6317-111">Under **Autopilot**, select **Set up**.</span></span>

1. <span data-ttu-id="d6317-112">Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben az export helyének.</span><span class="sxs-lookup"><span data-stu-id="d6317-112">Give your export destination a recognizable name in the **Display name** field.</span></span>

   :::image type="content" source="media/export-autopilot.PNG" alt-text="Az Autopilot-kapcsolat konfigurációs ablaktáblája.":::

1. <span data-ttu-id="d6317-114">Adja meg az **Autopilot API kulcsát** [Autopilot API-kulcs](https://autopilot.docs.apiary.io/#).</span><span class="sxs-lookup"><span data-stu-id="d6317-114">Enter your **Autopilot API key** [Autopilot API key](https://autopilot.docs.apiary.io/#).</span></span>

1. <span data-ttu-id="d6317-115">Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.</span><span class="sxs-lookup"><span data-stu-id="d6317-115">Select **I agree** to confirm the **Data privacy and compliance**.</span></span>

1. <span data-ttu-id="d6317-116">Válassza a **Csatlakozás** lehetőséget az Autopilot kapcsolat inicializálásához.</span><span class="sxs-lookup"><span data-stu-id="d6317-116">Select **Connect** to initialize the connection to Autopilot.</span></span>

1. <span data-ttu-id="d6317-117">Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.</span><span class="sxs-lookup"><span data-stu-id="d6317-117">Select **Add yourself as export user** and provide your Customer Insights credentials.</span></span>

1. <span data-ttu-id="d6317-118">Az Exportálás konfigurálásához válassza a **Tovább** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="d6317-118">Select **Next** to configure the export.</span></span>

## <a name="configure-the-connector"></a><span data-ttu-id="d6317-119">Konfigurálja az összekötőt</span><span class="sxs-lookup"><span data-stu-id="d6317-119">Configure the connector</span></span>

1. <span data-ttu-id="d6317-120">Az **Adategyeztetés** szakaszban az **E-mail** mezőben jelölje ki az egyesített ügyfélprofil ügyfél e-mail-címét jelképező mezőjét.</span><span class="sxs-lookup"><span data-stu-id="d6317-120">In the **Data matching** section, in the **Email** field, select the field in your unified customer profile that represents a customer's email address.</span></span> <span data-ttu-id="d6317-121">Ismételje meg ugyanezeket a lépéseket az egyéb választható mezőkön, például az **Utónév**, a **Vezetéknév**.</span><span class="sxs-lookup"><span data-stu-id="d6317-121">Repeat the same steps for other optional fields such as **First name**, **Last name**.</span></span>

1. <span data-ttu-id="d6317-122">Jelölje ki a szegmenseket, amelyeket exportálni szeretne.</span><span class="sxs-lookup"><span data-stu-id="d6317-122">Select the segments you want to export.</span></span> <span data-ttu-id="d6317-123">Fokozottan **javasoljuk, hogy ne exportáljon összesen 100 000-nél több ügyfélprofilt** az Autopilotba.</span><span class="sxs-lookup"><span data-stu-id="d6317-123">We strongly **recommend to not export more than 100'000 customer profiles in total** to Autopilot.</span></span> 

1. <span data-ttu-id="d6317-124">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="d6317-124">Select **Save**.</span></span>

## <a name="export-the-data"></a><span data-ttu-id="d6317-125">Az adatok exportálása</span><span class="sxs-lookup"><span data-stu-id="d6317-125">Export the data</span></span>

<span data-ttu-id="d6317-126">[Igény szerint exportálhatja az adatot](export-destinations.md).</span><span class="sxs-lookup"><span data-stu-id="d6317-126">You can [export data on demand](export-destinations.md).</span></span> <span data-ttu-id="d6317-127">Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) együtt is lefut.</span><span class="sxs-lookup"><span data-stu-id="d6317-127">The export will also run with every [scheduled refresh](system.md#schedule-tab).</span></span>

## <a name="known-limitations"></a><span data-ttu-id="d6317-128">Ismert korlátozások</span><span class="sxs-lookup"><span data-stu-id="d6317-128">Known limitations</span></span>

- <span data-ttu-id="d6317-129">Összesen legfeljebb 100 000 ügyfélprofilt exportálhat az Autopilotba.</span><span class="sxs-lookup"><span data-stu-id="d6317-129">You can export up to 100'000 profiles in total to Autopilot.</span></span>
- <span data-ttu-id="d6317-130">Az Autopilotba való exportálás csak szegmensekre korlátozódik.</span><span class="sxs-lookup"><span data-stu-id="d6317-130">Exporting to Autopilot is limited to segments.</span></span>
- <span data-ttu-id="d6317-131">Akár 100 000 profil Autopilotba való exportálása néhány órát is igénybe vehet.</span><span class="sxs-lookup"><span data-stu-id="d6317-131">Exporting up to 100'000 profiles to Autopilot can take up to a few hours to complete.</span></span> 
- <span data-ttu-id="d6317-132">Az Autopilotba exportálható profilok száma függ az Autopilot szerződésről, és korlátozott.</span><span class="sxs-lookup"><span data-stu-id="d6317-132">The number of profiles that you can export to Autopilot is dependent and limited on your contract with Autopilot.</span></span>

## <a name="data-privacy-and-compliance"></a><span data-ttu-id="d6317-133">Adatvédelem és megfelelőség</span><span class="sxs-lookup"><span data-stu-id="d6317-133">Data privacy and compliance</span></span>

<span data-ttu-id="d6317-134">Amikor engedélyezi a Dynamics 365 Customer Insights szolgáltatást az adatok Autopilot szolgáltatásba való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat.</span><span class="sxs-lookup"><span data-stu-id="d6317-134">When you enable Dynamics 365 Customer Insights to transmit data to Autopilot, you allow transfer of data outside of the compliance boundary for Dynamics 365 Customer Insights, including potentially sensitive data such as Personal Data.</span></span> <span data-ttu-id="d6317-135">A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy az Autopilot megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek.</span><span class="sxs-lookup"><span data-stu-id="d6317-135">Microsoft will transfer such data at your instruction, but you are responsible for ensuring that Autopilot meet any privacy or security obligations you may have.</span></span> <span data-ttu-id="d6317-136">További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).</span><span class="sxs-lookup"><span data-stu-id="d6317-136">For more information, see [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?linkid=396732).</span></span>
<span data-ttu-id="d6317-137">A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.</span><span class="sxs-lookup"><span data-stu-id="d6317-137">Your Dynamics 365 Customer Insights Administrator can remove this export destination at any time to discontinue use of this functionality.</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]