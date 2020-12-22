---
title: LiveRamp összekötő
description: Megismerkedhet vele, hogyan exportálhatja az adatokat a LiveRamp megoldásba.
ms.date: 12/02/2020
ms.reviewer: kishorem
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: 86aa8c66a47ee61741082c95f05d2e5ce3f06f35
ms.sourcegitcommit: 334633cbd58f5659d20b4f87252c1a10cc7130db
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/03/2020
ms.locfileid: "4667187"
---
# <a name="liverampreg-connector-preview"></a><span data-ttu-id="b006d-103">LiveRamp&reg; összekötő (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="b006d-103">LiveRamp&reg; connector (preview)</span></span>

<span data-ttu-id="b006d-104">Az adatok aktiválása a LiveRamp megoldásban, hogy a digitális, a közösségi és a TV-ökoszisztémákban több mint 500 platformot csatlakoztasson.</span><span class="sxs-lookup"><span data-stu-id="b006d-104">Activate your data in LiveRamp to connect with over 500 platforms across digital, social, and TV ecosystems.</span></span> <span data-ttu-id="b006d-105">A LiveRamp megoldásban az adatokkal dolgozhat a kampányok megcélzott, letiltási és személyre szabása céljából.</span><span class="sxs-lookup"><span data-stu-id="b006d-105">Work with your data in LiveRamp to target, suppress, and personalize ad campaigns.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b006d-106">Előfeltételek</span><span class="sxs-lookup"><span data-stu-id="b006d-106">Prerequisites</span></span>

- <span data-ttu-id="b006d-107">Az összekötő használatához LiveRamp-előfizetésre van szükség.</span><span class="sxs-lookup"><span data-stu-id="b006d-107">You need a LiveRamp subscription to use this connector.</span></span>
- <span data-ttu-id="b006d-108">Az előfizetés megkezdéséhez [forduljon a LiveRamphez](https://liveramp.com/contact/) közvetlenül.</span><span class="sxs-lookup"><span data-stu-id="b006d-108">To get a subscription, [contact LiveRamp](https://liveramp.com/contact/) directly.</span></span> <span data-ttu-id="b006d-109">[További információ a LiveRamp előkészítésről](https://liveramp.com/our-platform/data-onboarding/).</span><span class="sxs-lookup"><span data-stu-id="b006d-109">[Learn more about LiveRamp Onboarding](https://liveramp.com/our-platform/data-onboarding/).</span></span>

## <a name="connect-to-liveramp"></a><span data-ttu-id="b006d-110">LiveRamp csatlakoztatás</span><span class="sxs-lookup"><span data-stu-id="b006d-110">Connect to LiveRamp</span></span>

1. <span data-ttu-id="b006d-111">A célközönség információin belül nyissa meg a következőt **Rendszergazda** > **Exportálási célhelyek**.</span><span class="sxs-lookup"><span data-stu-id="b006d-111">In audience insights, go to **Admin** > **Export destinations**.</span></span>

1. <span data-ttu-id="b006d-112">A **LiveRamp** csempében válassza a **Beállítás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="b006d-112">In the **LiveRamp** tile, select **Set up**.</span></span>

1. <span data-ttu-id="b006d-113">Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben.</span><span class="sxs-lookup"><span data-stu-id="b006d-113">Give your destination a recognizable name in the **Display name** field.</span></span>

1. <span data-ttu-id="b006d-114">Adja meg a **felhasználónevet** és a **jelszót** a LiveRamp Secure FTP (SFTP) fiókhoz.</span><span class="sxs-lookup"><span data-stu-id="b006d-114">Provide a **Username** and **Password** for your LiveRamp Secure FTP (SFTP) account.</span></span>
<span data-ttu-id="b006d-115">Ezek a hitelesítő adatok eltérhetnek a LiveRamp betanítási hitelesítő adatoktól.</span><span class="sxs-lookup"><span data-stu-id="b006d-115">These credentials may be different from your LiveRamp Onboarding credentials.</span></span>

1. <span data-ttu-id="b006d-116">A LiveRamp kapcsolat teszteléséhez válassza az **Ellenőrzés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="b006d-116">Select **Verify** to test the connection to LiveRamp.</span></span>

1. <span data-ttu-id="b006d-117">A sikeres ellenőrzés után adja meg az **adatvédelemre és a megfelelőségre** vonatkozó beleegyezését az **Elfogadom** jelölőnégyzet bejelölésével.</span><span class="sxs-lookup"><span data-stu-id="b006d-117">After successful verification, provide your consent for **Data privacy and compliance** by selecting the **I agree** checkbox.</span></span>

1. <span data-ttu-id="b006d-118">A LiveRamp csatlakozó beállításához válassza a **Tovább** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="b006d-118">Select **Next** to set up the LiveRamp connector.</span></span>

## <a name="configure-the-connector"></a><span data-ttu-id="b006d-119">Konfigurálja az összekötőt</span><span class="sxs-lookup"><span data-stu-id="b006d-119">Configure the connector</span></span>

1. <span data-ttu-id="b006d-120">Az **adja meg a kulcs azonosítóját** mezőben jelölje ki az **e-mailt**, a **nevet és a címet** vagy a **telefont**, hogy elküldje a LiveRamp rendszerbe a személyazonosság feloldása céljából.</span><span class="sxs-lookup"><span data-stu-id="b006d-120">In the **Choose your key identifier** field, select **Email**,  **Name and address**, or **Phone** to send to LiveRamp for identity resolution.</span></span>

1. <span data-ttu-id="b006d-121">Képezze le a megfelelő attribútumokat az egyesített ügyfél entitásból a kiválasztott kulcsazonosítóhoz.</span><span class="sxs-lookup"><span data-stu-id="b006d-121">Map the corresponding attributes from your unified customer entity for the selected key identifier.</span></span>

1. <span data-ttu-id="b006d-122">Válassza az **Attribútum hozzáadása** lehetőséget, ha további attribútumokat szeretne leképezni, amelyeket el szeretne küldeni a LiveRamp rendszerébe.</span><span class="sxs-lookup"><span data-stu-id="b006d-122">Select **Add attribute** to map additional attributes to send to LiveRamp.</span></span>

   > [!TIP]
   > <span data-ttu-id="b006d-123">Ha további kulcsazonosító attribútumokat küld a LiveRamp számára, akkor valószínűleg magasabb szintű egyeztetést fog kapni.</span><span class="sxs-lookup"><span data-stu-id="b006d-123">Sending more key identifier attributes to LiveRamp is likely to get you a higher match rate.</span></span>

1. <span data-ttu-id="b006d-124">Jelölje ki azokat a szegmenseket, amelyeket exportálni szeretne a LiveRamp rendszerébe.</span><span class="sxs-lookup"><span data-stu-id="b006d-124">Select the segments you want to export to LiveRamp.</span></span>

1. <span data-ttu-id="b006d-125">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="b006d-125">Select **Save**.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="b006d-126">![LiveRamp összekötő attribútum-hozzárendeléssel](media/export-liveramp-segments.png "LiveRamp összekötő attribútum-hozzárendeléssel")</span><span class="sxs-lookup"><span data-stu-id="b006d-126">![LiveRamp connector with attribute mapping](media/export-liveramp-segments.png "LiveRamp connector with attribute mapping")</span></span>

## <a name="export-the-data"></a><span data-ttu-id="b006d-127">Az adatok exportálása</span><span class="sxs-lookup"><span data-stu-id="b006d-127">Export the data</span></span>

<span data-ttu-id="b006d-128">Az exportálás hamarosan megkezdődik, ha az exportálás minden előfeltétele befejeződött.</span><span class="sxs-lookup"><span data-stu-id="b006d-128">The export will start shortly if all prerequisites for export have been completed.</span></span> <span data-ttu-id="b006d-129">Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) együtt is lefut.</span><span class="sxs-lookup"><span data-stu-id="b006d-129">The export will also run with every [scheduled refresh](system.md#schedule-tab).</span></span>
<span data-ttu-id="b006d-130">Miután az exportálás sikeresen befejeződött, bejelentkezhet az LiveRamp előkészítésbe az adatok aktiválásához és terjesztéséhez.</span><span class="sxs-lookup"><span data-stu-id="b006d-130">Once the export is successfully completed, you can sign in to LiveRamp Onboarding to activate and distribute your data.</span></span>

## <a name="data-privacy-and-compliance"></a><span data-ttu-id="b006d-131">Adatvédelem és megfelelőség</span><span class="sxs-lookup"><span data-stu-id="b006d-131">Data privacy and compliance</span></span>

<span data-ttu-id="b006d-132">Amikor engedélyezi az Dynamics 365 Customer Insights szolgáltatást az adatok Liveramphez való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat.</span><span class="sxs-lookup"><span data-stu-id="b006d-132">When you enable Dynamics 365 Customer Insights to transmit data to Liveramp, you allow transfer of data outside of the compliance boundary for Dynamics 365 Customer Insights, including potentially sensitive data such as Personal Data.</span></span> <span data-ttu-id="b006d-133">A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy a Liveramp megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek.</span><span class="sxs-lookup"><span data-stu-id="b006d-133">Microsoft will transfer such data at your instruction, but you are responsible for ensuring that Liveramp meets any privacy or security obligations you may have.</span></span> <span data-ttu-id="b006d-134">További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).</span><span class="sxs-lookup"><span data-stu-id="b006d-134">For more information, see [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?linkid=396732).</span></span>
<span data-ttu-id="b006d-135">A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.</span><span class="sxs-lookup"><span data-stu-id="b006d-135">Your Dynamics 365 Customer Insights Administrator can remove this export destination at any time to discontinue use of this functionality.</span></span>