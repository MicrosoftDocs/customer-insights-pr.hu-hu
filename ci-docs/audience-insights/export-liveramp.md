---
title: LiveRamp összekötő
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a LiveRampbe.
ms.date: 03/03/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: kishorem-ms
ms.author: kishorem
manager: shellyha
ms.openlocfilehash: 987457966fe1fc034d9e3cd2a1ce33902c7a84f4
ms.sourcegitcommit: 1b671c6100991fea1cace04b5d4fcedcd88aa94f
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/31/2021
ms.locfileid: "5760330"
---
# <a name="export-segments-to-liverampreg-preview"></a><span data-ttu-id="f8ce3-103">Szegmensek exportálása a LiveRampbe&reg; (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="f8ce3-103">Export segments to LiveRamp&reg; (preview)</span></span>

<span data-ttu-id="f8ce3-104">Aktiválja az adatokat a LiveRampben, hogy több mint 500 platformmal kapcsolódhasson a digitális és közösségi médiához, illetve a tévéadáshoz.</span><span class="sxs-lookup"><span data-stu-id="f8ce3-104">Activate your data in LiveRamp to connect with over 500 platforms across digital, social, and TVs.</span></span> <span data-ttu-id="f8ce3-105">A LiveRamp megoldásban az adatokkal dolgozhat a kampányok megcélzott, letiltási és személyre szabása céljából.</span><span class="sxs-lookup"><span data-stu-id="f8ce3-105">Work with your data in LiveRamp to target, suppress, and personalize ad campaigns.</span></span>

## <a name="prerequisites-for-a-connection"></a><span data-ttu-id="f8ce3-106">Egy kapcsolat előfeltételei</span><span class="sxs-lookup"><span data-stu-id="f8ce3-106">Prerequisites for a connection</span></span>

- <span data-ttu-id="f8ce3-107">Az összekötő használatához LiveRamp-előfizetésre van szükség.</span><span class="sxs-lookup"><span data-stu-id="f8ce3-107">You need a LiveRamp subscription to use this connector.</span></span>
- <span data-ttu-id="f8ce3-108">Az előfizetés megkezdéséhez [forduljon a LiveRamphez](https://liveramp.com/contact/) közvetlenül.</span><span class="sxs-lookup"><span data-stu-id="f8ce3-108">To get a subscription, [contact LiveRamp](https://liveramp.com/contact/) directly.</span></span> <span data-ttu-id="f8ce3-109">[További információ a LiveRamp előkészítésről](https://liveramp.com/our-platform/data-onboarding/).</span><span class="sxs-lookup"><span data-stu-id="f8ce3-109">[Learn more about LiveRamp Onboarding](https://liveramp.com/our-platform/data-onboarding/).</span></span>

## <a name="set-up-connection-to-liveramp"></a><span data-ttu-id="f8ce3-110">Állítsa be a LiveRamp való kapcsolatot</span><span class="sxs-lookup"><span data-stu-id="f8ce3-110">Set up connection to LiveRamp</span></span>

1. <span data-ttu-id="f8ce3-111">Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="f8ce3-111">Go to **Admin** > **Connections**.</span></span>

1. <span data-ttu-id="f8ce3-112">Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza a **LiveRamp** lehetőséget a kapcsolat konfigurálásához.</span><span class="sxs-lookup"><span data-stu-id="f8ce3-112">Select **Add connection** and choose **LiveRamp** to configure the connection.</span></span>

1. <span data-ttu-id="f8ce3-113">Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak.</span><span class="sxs-lookup"><span data-stu-id="f8ce3-113">Give your connection a recognizable name in the **Display name** field.</span></span> <span data-ttu-id="f8ce3-114">A név és a kapcsolat típusa írja le ezt a kapcsolatot.</span><span class="sxs-lookup"><span data-stu-id="f8ce3-114">The name and the type of the connection describe this connection.</span></span> <span data-ttu-id="f8ce3-115">Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.</span><span class="sxs-lookup"><span data-stu-id="f8ce3-115">We recommend choosing a name that explains the purpose and target of the connection.</span></span>

1. <span data-ttu-id="f8ce3-116">A kapcsolat használóinak kiválasztása.</span><span class="sxs-lookup"><span data-stu-id="f8ce3-116">Choose who can use this connection.</span></span> <span data-ttu-id="f8ce3-117">Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz.</span><span class="sxs-lookup"><span data-stu-id="f8ce3-117">If you take no action, the default will be Administrators.</span></span> <span data-ttu-id="f8ce3-118">További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).</span><span class="sxs-lookup"><span data-stu-id="f8ce3-118">For more information, see [Allow contributors to use a connection for exports](connections.md#allow-contributors-to-use-a-connection-for-exports).</span></span>

1. <span data-ttu-id="f8ce3-119">Adja meg a **felhasználónevet** és a **jelszót** a LiveRamp Secure FTP (SFTP) fiókhoz.</span><span class="sxs-lookup"><span data-stu-id="f8ce3-119">Provide a **Username** and **Password** for your LiveRamp Secure FTP (SFTP) account.</span></span>
<span data-ttu-id="f8ce3-120">Ezek a hitelesítő adatok eltérhetnek a LiveRamp betanítási hitelesítő adatoktól.</span><span class="sxs-lookup"><span data-stu-id="f8ce3-120">These credentials may be different from your LiveRamp Onboarding credentials.</span></span>

1. <span data-ttu-id="f8ce3-121">A LiveRamp kapcsolat teszteléséhez válassza az **Ellenőrzés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="f8ce3-121">Select **Verify** to test the connection to LiveRamp.</span></span>

1. <span data-ttu-id="f8ce3-122">A sikeres ellenőrzés után adja meg az **adatvédelemre és a megfelelőségre** vonatkozó beleegyezését az **Elfogadom** jelölőnégyzet bejelölésével.</span><span class="sxs-lookup"><span data-stu-id="f8ce3-122">After successful verification, provide your consent for **Data privacy and compliance** by selecting the **I agree** checkbox.</span></span>

1. <span data-ttu-id="f8ce3-123">A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="f8ce3-123">Select **Save** to complete the connection.</span></span>

## <a name="configure-an-export"></a><span data-ttu-id="f8ce3-124">Exportálás konfigurálása</span><span class="sxs-lookup"><span data-stu-id="f8ce3-124">Configure an export</span></span>

<span data-ttu-id="f8ce3-125">Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz.</span><span class="sxs-lookup"><span data-stu-id="f8ce3-125">You can configure this export if you have access to a connection of this type.</span></span> <span data-ttu-id="f8ce3-126">További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).</span><span class="sxs-lookup"><span data-stu-id="f8ce3-126">For more information, see [Permissions needed to configure an export](export-destinations.md#set-up-a-new-export).</span></span>

1. <span data-ttu-id="f8ce3-127">Menjen az **Adatok** > **Exportálások** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="f8ce3-127">Go to **Data** > **Exports**.</span></span>

1. <span data-ttu-id="f8ce3-128">Új exportálás létrehozásához válassza a **Célhely hozzáadása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="f8ce3-128">To create a new export, select **Add destination**.</span></span>

1. <span data-ttu-id="f8ce3-129">A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot a LiveRamp szakaszból.</span><span class="sxs-lookup"><span data-stu-id="f8ce3-129">In the **Connection for export** field, choose a connection from the LiveRamp section.</span></span> <span data-ttu-id="f8ce3-130">Ha nem látja ezt a szakasznevet, az Ön számára nincs ilyen típusú kapcsolat.</span><span class="sxs-lookup"><span data-stu-id="f8ce3-130">If you don't see this section name, there are no connections of this type available to you.</span></span>

1. <span data-ttu-id="f8ce3-131">Az **adja meg a kulcs azonosítóját** mezőben jelölje ki az **e-mailt**, a **nevet és a címet** vagy a **telefont**, hogy elküldje a LiveRamp rendszerbe a személyazonosság feloldása céljából.</span><span class="sxs-lookup"><span data-stu-id="f8ce3-131">In the **Choose your key identifier** field, select **Email**,  **Name and address**, or **Phone** to send to LiveRamp for identity resolution.</span></span>
   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="f8ce3-132">![LiveRamp összekötő attribútum-hozzárendeléssel](media/export-liveramp-segments.png "LiveRamp összekötő attribútum-hozzárendeléssel")</span><span class="sxs-lookup"><span data-stu-id="f8ce3-132">![LiveRamp connector with attribute mapping](media/export-liveramp-segments.png "LiveRamp connector with attribute mapping")</span></span>

1. <span data-ttu-id="f8ce3-133">Képezze le a megfelelő attribútumokat az egyesített ügyfél entitásból a kiválasztott kulcsazonosítóhoz.</span><span class="sxs-lookup"><span data-stu-id="f8ce3-133">Map the corresponding attributes from your unified customer entity for the selected key identifier.</span></span>

1. <span data-ttu-id="f8ce3-134">Válassza az **Attribútum hozzáadása** lehetőséget a több attribútum leképzésének LiveRampbe küldéséhez.</span><span class="sxs-lookup"><span data-stu-id="f8ce3-134">Select **Add attribute** to map more attributes to send to LiveRamp.</span></span>

   > [!TIP]
   > <span data-ttu-id="f8ce3-135">Ha további kulcsazonosító attribútumokat küld a LiveRamp számára, akkor valószínűleg magasabb szintű egyeztetést fog kapni.</span><span class="sxs-lookup"><span data-stu-id="f8ce3-135">Sending more key identifier attributes to LiveRamp is likely to get you a higher match rate.</span></span>

1. <span data-ttu-id="f8ce3-136">Jelölje ki azokat a szegmenseket, amelyeket exportálni szeretne a LiveRamp rendszerébe.</span><span class="sxs-lookup"><span data-stu-id="f8ce3-136">Select the segments you want to export to LiveRamp.</span></span>

1. <span data-ttu-id="f8ce3-137">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="f8ce3-137">Select **Save**.</span></span>

<span data-ttu-id="f8ce3-138">Az exportálás mentése nem futtatja azonnal az exportálást.</span><span class="sxs-lookup"><span data-stu-id="f8ce3-138">Saving an export doesn't run the export immediately.</span></span>

<span data-ttu-id="f8ce3-139">Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut.</span><span class="sxs-lookup"><span data-stu-id="f8ce3-139">The export runs with every [scheduled refresh](system.md#schedule-tab).</span></span> <span data-ttu-id="f8ce3-140">Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand).</span><span class="sxs-lookup"><span data-stu-id="f8ce3-140">You can also [export data on demand](export-destinations.md#run-exports-on-demand).</span></span> 


## <a name="data-privacy-and-compliance"></a><span data-ttu-id="f8ce3-141">Adatvédelem és megfelelőség</span><span class="sxs-lookup"><span data-stu-id="f8ce3-141">Data privacy and compliance</span></span>

<span data-ttu-id="f8ce3-142">Amikor engedélyezi az Dynamics 365 Customer Insights szolgáltatást az adatok Liveramphez való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat.</span><span class="sxs-lookup"><span data-stu-id="f8ce3-142">When you enable Dynamics 365 Customer Insights to transmit data to Liveramp, you allow transfer of data outside of the compliance boundary for Dynamics 365 Customer Insights, including potentially sensitive data such as Personal Data.</span></span> <span data-ttu-id="f8ce3-143">A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy a Liveramp megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek.</span><span class="sxs-lookup"><span data-stu-id="f8ce3-143">Microsoft will transfer such data at your instruction, but you are responsible for ensuring that Liveramp meets any privacy or security obligations you may have.</span></span> <span data-ttu-id="f8ce3-144">További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).</span><span class="sxs-lookup"><span data-stu-id="f8ce3-144">For more information, see [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?linkid=396732).</span></span>
<span data-ttu-id="f8ce3-145">A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.</span><span class="sxs-lookup"><span data-stu-id="f8ce3-145">Your Dynamics 365 Customer Insights Administrator can remove this export destination at any time to discontinue use of this functionality.</span></span>

[!INCLUDE[footer-include](../includes/footer-banner.md)]
