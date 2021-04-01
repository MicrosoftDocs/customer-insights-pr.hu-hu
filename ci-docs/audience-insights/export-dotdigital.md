---
title: Customer Insights adatok exportálása a DotDigitalbe
description: Megismerheti, hogyan konfigurálható a kapcsolat a DotDigitallal.
ms.date: 11/14/2020
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: phkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 51a28bdf0de34f0555d8ad7e3d13b2ef8911d417
ms.sourcegitcommit: bae40184312ab27b95c140a044875c2daea37951
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/15/2021
ms.locfileid: "5598020"
---
# <a name="connector-for-dotdigital-preview"></a><span data-ttu-id="82a0b-103">A DotDigital összekötője (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="82a0b-103">Connector for DotDigital (preview)</span></span>

<span data-ttu-id="82a0b-104">Az egyesített ügyfélprofilok szegmenseit exportálhatja a DotDigital címjegyzékekbe, és használhatja őet kampányokhoz, e-mail-marketinghez és ügyfélszegmensek létrehozásához a DotDigitallal.</span><span class="sxs-lookup"><span data-stu-id="82a0b-104">Export segments of unified customer profiles to DotDigital address books and use them for campaigns, email marketing, and to build customer segments with DotDigital.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="82a0b-105">Előfeltételek</span><span class="sxs-lookup"><span data-stu-id="82a0b-105">Prerequisites</span></span>

-   <span data-ttu-id="82a0b-106">Rendelkezik [DotDigital-fiókkal](https://dotdigital.com/) és a megfelelő rendszergazdai hitelesítő adatokkal.</span><span class="sxs-lookup"><span data-stu-id="82a0b-106">You have a [DotDigital account](https://dotdigital.com/) and corresponding administrator credentials.</span></span>
-   <span data-ttu-id="82a0b-107">A DotDigitalban és a megfelelő azonosítókban meglévő címjegyzékek találhatók.</span><span class="sxs-lookup"><span data-stu-id="82a0b-107">There are existing address books in DotDigital and the corresponding IDs.</span></span> <span data-ttu-id="82a0b-108">Az azonosító megtalálhatók az URL-címben, amikor kijelöli és megnyitja a címjegyzéket.</span><span class="sxs-lookup"><span data-stu-id="82a0b-108">The ID can be found in the URL when you select and open an address book.</span></span> <span data-ttu-id="82a0b-109">További információért lásd: [DotDigital címjegyzékek](https://support.dotdigital.com/hc/articles/212211968-Creating-an-address-book).</span><span class="sxs-lookup"><span data-stu-id="82a0b-109">For more information, see [DotDigital address books](https://support.dotdigital.com/hc/articles/212211968-Creating-an-address-book).</span></span>
-   <span data-ttu-id="82a0b-110">[Konfigurált szegmensekkel](segments.md) rendelkezik a célközönségi-információkban.</span><span class="sxs-lookup"><span data-stu-id="82a0b-110">You have [configured segments](segments.md) in audience insights.</span></span>
-   <span data-ttu-id="82a0b-111">Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.</span><span class="sxs-lookup"><span data-stu-id="82a0b-111">Unified customer profiles in the exported segments contain a field representing an email address.</span></span>

## <a name="connect-to-dotdigital"></a><span data-ttu-id="82a0b-112">Csatlakozás a DotDigitalhoz</span><span class="sxs-lookup"><span data-stu-id="82a0b-112">Connect to DotDigital</span></span>

1. <span data-ttu-id="82a0b-113">Válassz a **Rendszergazda** > **Célok exportálása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="82a0b-113">Go to **Admin** > **Export destinations**.</span></span>

1. <span data-ttu-id="82a0b-114">A **DotDigital** részben válassza a **Beállítás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="82a0b-114">Under **DotDigital**, select **Set up**.</span></span>

1. <span data-ttu-id="82a0b-115">Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben az export helyének.</span><span class="sxs-lookup"><span data-stu-id="82a0b-115">Give your export destination a recognizable name in the **Display name** field.</span></span>

   :::image type="content" source="media/DotDigital_config.PNG" alt-text="A DotDigital exportálásának konfigurációs ablaktáblája.":::

1. <span data-ttu-id="82a0b-117">Adja meg a **DotDigital felhasználói nevét és a jelszavát**.</span><span class="sxs-lookup"><span data-stu-id="82a0b-117">Enter your **DotDigital username and password**.</span></span>

1. <span data-ttu-id="82a0b-118">Adja meg a **[DotDigital címjegyzék-azonosítóját](https://support.dotdigital.com/hc/articles/212211968-Creating-an-address-book)**.</span><span class="sxs-lookup"><span data-stu-id="82a0b-118">Enter your **[DotDigital address book ID](https://support.dotdigital.com/hc/articles/212211968-Creating-an-address-book)**.</span></span>

1. <span data-ttu-id="82a0b-119">Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.</span><span class="sxs-lookup"><span data-stu-id="82a0b-119">Select **I agree** to confirm the **Data privacy and compliance**.</span></span>

1. <span data-ttu-id="82a0b-120">Válassza a **Csatlakozás** lehetőséget a DotDigital kapcsolat inicializálásához.</span><span class="sxs-lookup"><span data-stu-id="82a0b-120">Select **Connect** to initialize the connection to DotDigital.</span></span>

1. <span data-ttu-id="82a0b-121">Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.</span><span class="sxs-lookup"><span data-stu-id="82a0b-121">Select **Add yourself as export user** and provide your Customer Insights credentials.</span></span>

1. <span data-ttu-id="82a0b-122">Az Exportálás konfigurálásához válassza a **Tovább** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="82a0b-122">Select **Next** to configure the export.</span></span>

## <a name="configure-the-connector"></a><span data-ttu-id="82a0b-123">Konfigurálja az összekötőt</span><span class="sxs-lookup"><span data-stu-id="82a0b-123">Configure the connector</span></span>

1. <span data-ttu-id="82a0b-124">Az **Adategyeztetés** szakaszban az **E-mail** mezőben jelölje ki az egyesített ügyfélprofil ügyfél e-mail-címét jelképező mezőjét.</span><span class="sxs-lookup"><span data-stu-id="82a0b-124">In the **Data matching** section, in the **Email** field, select the field in your unified customer profile that represents a customer's email address.</span></span> <span data-ttu-id="82a0b-125">Ismételje meg ugyanezeket a lépéseket az egyéb választható mezőkön, például az **Utónév**, a **Vezetéknév** , a **Teljes név**, a **Nem** és az **Irányítószám** mezőben.</span><span class="sxs-lookup"><span data-stu-id="82a0b-125">Repeat the same steps for other optional fields such as **First name**, **Last name**, **Full name**, **Gender**, and **Post code**.</span></span>

1. <span data-ttu-id="82a0b-126">Jelölje ki a szegmenseket, amelyeket exportálni szeretne.</span><span class="sxs-lookup"><span data-stu-id="82a0b-126">Select the segments you want to export.</span></span> <span data-ttu-id="82a0b-127">Összesen legfeljebb 1 000 000 ügyfélprofilt exportálhat a DotDigitalba.</span><span class="sxs-lookup"><span data-stu-id="82a0b-127">You can export up to 1 million customer profiles in total to DotDigital.</span></span>

1. <span data-ttu-id="82a0b-128">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="82a0b-128">Select **Save**.</span></span>

## <a name="export-the-data"></a><span data-ttu-id="82a0b-129">Az adatok exportálása</span><span class="sxs-lookup"><span data-stu-id="82a0b-129">Export the data</span></span>

<span data-ttu-id="82a0b-130">[Igény szerint exportálhatja az adatot](export-destinations.md).</span><span class="sxs-lookup"><span data-stu-id="82a0b-130">You can [export data on demand](export-destinations.md).</span></span> <span data-ttu-id="82a0b-131">Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) együtt is lefut.</span><span class="sxs-lookup"><span data-stu-id="82a0b-131">The export will also run with every [scheduled refresh](system.md#schedule-tab).</span></span> <span data-ttu-id="82a0b-132">A DotDigitalban most már megtalálhatja a szegmenseket a [DotDigital címjegyzékekben](https://support.dotdigital.com/hc/articles/212211968-Creating-an-address-book).</span><span class="sxs-lookup"><span data-stu-id="82a0b-132">In DotDigital, you can now find your segments in [DotDigital address books](https://support.dotdigital.com/hc/articles/212211968-Creating-an-address-book).</span></span>

## <a name="known-limitations"></a><span data-ttu-id="82a0b-133">Ismert korlátozások</span><span class="sxs-lookup"><span data-stu-id="82a0b-133">Known limitations</span></span>

- <span data-ttu-id="82a0b-134">Legfeljebb 1 000 000 profilt exportálhat egyszerre a DotDigitalba.</span><span class="sxs-lookup"><span data-stu-id="82a0b-134">Up to 1 million profiles per export to DotDigital.</span></span>
- <span data-ttu-id="82a0b-135">A DotDigitalba való exportálás csak szegmensekre korlátozódik.</span><span class="sxs-lookup"><span data-stu-id="82a0b-135">Exporting to DotDigital is limited to segments.</span></span>
- <span data-ttu-id="82a0b-136">Az összesen 1 000 000 profillal rendelkező szegmens exportálása a szolgáltatói oldalon megjelenő korlátozások miatt akár 3 óráig is eltarthat.</span><span class="sxs-lookup"><span data-stu-id="82a0b-136">Exporting segments with a total of 1 million profiles can take up to 3 hours because of limitations on the provider side.</span></span> 
- <span data-ttu-id="82a0b-137">A DotDigitalba exportálható profilok száma függ a DotDigital szerződésről, és korlátozott.</span><span class="sxs-lookup"><span data-stu-id="82a0b-137">The number of profiles that you can export to DotDigital is dependent and limited on your contract with DotDigital.</span></span>

## <a name="data-privacy-and-compliance"></a><span data-ttu-id="82a0b-138">Adatvédelem és megfelelőség</span><span class="sxs-lookup"><span data-stu-id="82a0b-138">Data privacy and compliance</span></span>

<span data-ttu-id="82a0b-139">Amikor engedélyezi a Dynamics 365 Customer Insights szolgáltatást az adatok DotDigital szolgáltatásba való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat.</span><span class="sxs-lookup"><span data-stu-id="82a0b-139">When you enable Dynamics 365 Customer Insights to transmit data to DotDigital, you allow transfer of data outside of the compliance boundary for Dynamics 365 Customer Insights, including potentially sensitive data such as Personal Data.</span></span> <span data-ttu-id="82a0b-140">A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy a DotDigital megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek.</span><span class="sxs-lookup"><span data-stu-id="82a0b-140">Microsoft will transfer such data at your instruction, but you are responsible for ensuring that DotDigital meet any privacy or security obligations you may have.</span></span> <span data-ttu-id="82a0b-141">További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).</span><span class="sxs-lookup"><span data-stu-id="82a0b-141">For more information, see [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?linkid=396732).</span></span>
<span data-ttu-id="82a0b-142">A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.</span><span class="sxs-lookup"><span data-stu-id="82a0b-142">Your Dynamics 365 Customer Insights Administrator can remove this export destination at any time to discontinue use of this functionality.</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]