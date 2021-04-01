---
title: Customer Insights adatok exportálása az AdRollba
description: Megismerheti, hogyan konfigurálható a kapcsolat az AdRoll szolgáltatással.
ms.date: 02/15/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 6fedd549c2e7de362f36e3fb23d363200bb92a04
ms.sourcegitcommit: d24e52150fe5a4fab45128e12d6a03637771d9b9
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/19/2021
ms.locfileid: "5697077"
---
# <a name="connector-for-adroll-preview"></a><span data-ttu-id="d22aa-103">Az AdRoll összekötője (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="d22aa-103">Connector for AdRoll (preview)</span></span>

<span data-ttu-id="d22aa-104">Exportálja az egyesített ügyfélprofilok szegmenseit az AdRollba, és használja őket a hirdetésekben.</span><span class="sxs-lookup"><span data-stu-id="d22aa-104">Export segments of unified customer profiles to AdRoll and use them for advertising.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="d22aa-105">Előfeltételek</span><span class="sxs-lookup"><span data-stu-id="d22aa-105">Prerequisites</span></span>

-   <span data-ttu-id="d22aa-106">Rendelkezik [AdRoll-fiókkal](https://www.adroll.com/) és a megfelelő rendszergazdai hitelesítő adatokkal.</span><span class="sxs-lookup"><span data-stu-id="d22aa-106">You have an [AdRoll account](https://www.adroll.com/) and corresponding administrator credentials.</span></span>
-   <span data-ttu-id="d22aa-107">[Konfigurált szegmensekkel](segments.md) rendelkezik a célközönségi-információkban.</span><span class="sxs-lookup"><span data-stu-id="d22aa-107">You have [configured segments](segments.md) in audience insights.</span></span>
-   <span data-ttu-id="d22aa-108">Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.</span><span class="sxs-lookup"><span data-stu-id="d22aa-108">Unified customer profiles in the exported segments contain a field representing an email address.</span></span>

## <a name="connect-to-adroll"></a><span data-ttu-id="d22aa-109">Csatlakozás az AdRollhoz</span><span class="sxs-lookup"><span data-stu-id="d22aa-109">Connect to AdRoll</span></span>

1. <span data-ttu-id="d22aa-110">Válassz a **Rendszergazda** > **Célok exportálása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="d22aa-110">Go to **Admin** > **Export destinations**.</span></span>

1. <span data-ttu-id="d22aa-111">A **AdRoll** részben válassza a **Beállítás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="d22aa-111">Under **AdRoll**, select **Set up**.</span></span>

1. <span data-ttu-id="d22aa-112">Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben az export helyének.</span><span class="sxs-lookup"><span data-stu-id="d22aa-112">Give your export destination a recognizable name in the **Display name** field.</span></span>

   :::image type="content" source="media/AdRoll_config.PNG" alt-text="Az AdRoll-kapcsolat konfigurációs ablaktáblája.":::

1. <span data-ttu-id="d22aa-114">Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.</span><span class="sxs-lookup"><span data-stu-id="d22aa-114">Select **I agree** to confirm the **Data privacy and compliance**.</span></span>

1. <span data-ttu-id="d22aa-115">Válassza a **Csatlakozás** lehetőséget az AdRoll kapcsolat inicializálásához.</span><span class="sxs-lookup"><span data-stu-id="d22aa-115">Select **Connect** to initialize the connection to AdRoll.</span></span>

1. <span data-ttu-id="d22aa-116">Válassza a **Hitelesítés az AdRoll szolgáltatással** lehetőséget, és adja meg AdRoll rendszergazdai hitelesítő adatait.</span><span class="sxs-lookup"><span data-stu-id="d22aa-116">Select **Authenticate with AdRoll** and provide your admin credentials for AdRoll.</span></span> 

1. <span data-ttu-id="d22aa-117">Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.</span><span class="sxs-lookup"><span data-stu-id="d22aa-117">Select **Add yourself as export user** and provide your Customer Insights credentials.</span></span>

1. <span data-ttu-id="d22aa-118">Adja meg az **AdRoll hirdetői azonosítóját** [AdRoll hirdethetőség](https://help.adroll.com/hc/en-us/articles/212011838-Advertiser-Profiles).</span><span class="sxs-lookup"><span data-stu-id="d22aa-118">Enter your **AdRoll Advertiser ID** [AdRoll Advertisable](https://help.adroll.com/hc/en-us/articles/212011838-Advertiser-Profiles).</span></span>

1. <span data-ttu-id="d22aa-119">Az Exportálás konfigurálásához válassza a **Tovább** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="d22aa-119">Select **Next** to configure the export.</span></span>

## <a name="configure-the-connector"></a><span data-ttu-id="d22aa-120">Konfigurálja az összekötőt</span><span class="sxs-lookup"><span data-stu-id="d22aa-120">Configure the connector</span></span>

1. <span data-ttu-id="d22aa-121">Az **Adategyeztetés** szakaszban az **E-mail** mezőben jelölje ki az egyesített ügyfélprofil ügyfél e-mail-címét jelképező mezőjét.</span><span class="sxs-lookup"><span data-stu-id="d22aa-121">In the **Data matching** section, in the **Email** field, select the field in your unified customer profile that represents a customer's email address.</span></span> <span data-ttu-id="d22aa-122">A szegmenseket exportálni kell az AdRollba.</span><span class="sxs-lookup"><span data-stu-id="d22aa-122">It's required to export segments to AdRoll.</span></span>

1. <span data-ttu-id="d22aa-123">Jelölje ki a szegmenseket, amelyeket exportálni szeretne.</span><span class="sxs-lookup"><span data-stu-id="d22aa-123">Select the segments you want to export.</span></span> <span data-ttu-id="d22aa-124">Jelöljön ki egy legalább 100 tagból álló szegmenst.</span><span class="sxs-lookup"><span data-stu-id="d22aa-124">Select a segment with a least 100 members.</span></span> <span data-ttu-id="d22aa-125">Kisebb szegmensek nem exportálhatók.</span><span class="sxs-lookup"><span data-stu-id="d22aa-125">You can't export smaller segments.</span></span> <span data-ttu-id="d22aa-126">Az exportálni kívánt szegmens maximális mérete exportálásonként 250 000 tag.</span><span class="sxs-lookup"><span data-stu-id="d22aa-126">Additionally the maximum size of a segment to export is 250'000 members per export.</span></span> 

1. <span data-ttu-id="d22aa-127">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="d22aa-127">Select **Save**.</span></span>

## <a name="export-the-data"></a><span data-ttu-id="d22aa-128">Az adatok exportálása</span><span class="sxs-lookup"><span data-stu-id="d22aa-128">Export the data</span></span>

<span data-ttu-id="d22aa-129">[Igény szerint exportálhatja az adatot](export-destinations.md).</span><span class="sxs-lookup"><span data-stu-id="d22aa-129">You can [export data on demand](export-destinations.md).</span></span> <span data-ttu-id="d22aa-130">Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) együtt is lefut.</span><span class="sxs-lookup"><span data-stu-id="d22aa-130">The export will also run with every [scheduled refresh](system.md#schedule-tab).</span></span>

## <a name="known-limitations"></a><span data-ttu-id="d22aa-131">Ismert korlátozások</span><span class="sxs-lookup"><span data-stu-id="d22aa-131">Known limitations</span></span>

- <span data-ttu-id="d22aa-132">Összesen exportálásonként legfeljebb 250 000 ügyfélprofilt exportálhat az AdRollba.</span><span class="sxs-lookup"><span data-stu-id="d22aa-132">You can export up to 250'000 profiles in per export to AdRoll.</span></span>
- <span data-ttu-id="d22aa-133">100-nál kevesebb profillal rendelkező szegmensek nem exportálhatók az AdRollba.</span><span class="sxs-lookup"><span data-stu-id="d22aa-133">You can't export segments with fewer than 100 profiles to AdRoll.</span></span> 
- <span data-ttu-id="d22aa-134">Az AdRollba való exportálás csak szegmensekre korlátozódik.</span><span class="sxs-lookup"><span data-stu-id="d22aa-134">Exporting to AdRoll is limited to segments.</span></span>
- <span data-ttu-id="d22aa-135">Legfeljebb 250 000 profil az AdRollba való exportálása eltarthat 10 percig.</span><span class="sxs-lookup"><span data-stu-id="d22aa-135">Exporting up to 250'000 profiles to AdRoll can take up to 10 minutes to complete.</span></span> 
- <span data-ttu-id="d22aa-136">A Marketoba exportálható profilok száma függ a AdRoll szerződéstől, és korlátozott.</span><span class="sxs-lookup"><span data-stu-id="d22aa-136">The number of profiles that you can export to AdRoll is dependent and limited on your contract with AdRoll.</span></span>

## <a name="data-privacy-and-compliance"></a><span data-ttu-id="d22aa-137">Adatvédelem és megfelelőség</span><span class="sxs-lookup"><span data-stu-id="d22aa-137">Data privacy and compliance</span></span>

<span data-ttu-id="d22aa-138">Amikor engedélyezi a Dynamics 365 Customer Insights szolgáltatást az adatok AdRoll szolgáltatásba való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat.</span><span class="sxs-lookup"><span data-stu-id="d22aa-138">When you enable Dynamics 365 Customer Insights to transmit data to AdRoll, you allow transfer of data outside of the compliance boundary for Dynamics 365 Customer Insights, including potentially sensitive data such as Personal Data.</span></span> <span data-ttu-id="d22aa-139">A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy az AdRoll megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek.</span><span class="sxs-lookup"><span data-stu-id="d22aa-139">Microsoft will transfer such data at your instruction, but you are responsible for ensuring that AdRoll meets any privacy or security obligations you may have.</span></span> <span data-ttu-id="d22aa-140">További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).</span><span class="sxs-lookup"><span data-stu-id="d22aa-140">For more information, see [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?linkid=396732).</span></span>

<span data-ttu-id="d22aa-141">A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.</span><span class="sxs-lookup"><span data-stu-id="d22aa-141">Your Dynamics 365 Customer Insights Administrator can remove this export destination at any time to discontinue use of this functionality.</span></span>
