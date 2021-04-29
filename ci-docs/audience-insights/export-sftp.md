---
title: Customer Insights adatok exportálása a SFTP gazdaszámítógépekhez
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja az SFTP helyre.
ms.date: 03/03/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: phkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 96c6026aded315008439740646827ca910cead90
ms.sourcegitcommit: 1b671c6100991fea1cace04b5d4fcedcd88aa94f
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/31/2021
ms.locfileid: "5760422"
---
# <a name="export-segment-lists-and-other-data-to-sftp-preview"></a><span data-ttu-id="b66e3-103">Szegmenslisták és egyéb adatok exportálása az SFTP-be (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="b66e3-103">Export segment lists and other data to SFTP (preview)</span></span>

<span data-ttu-id="b66e3-104">Az ügyféladatokat külső alkalmazásokban használhatja, ha exportálja őket egy Biztonságos fájlátviteli protokoll (SFTP) helyre.</span><span class="sxs-lookup"><span data-stu-id="b66e3-104">Use your customer data in third-party applications by exporting them to a Secure File Transfer Protocol (SFTP) location.</span></span>

## <a name="prerequisites-for-connection"></a><span data-ttu-id="b66e3-105">A kapcsolat előfeltételei</span><span class="sxs-lookup"><span data-stu-id="b66e3-105">Prerequisites for connection</span></span>

- <span data-ttu-id="b66e3-106">Egy SFTP állomás és a hozzájuk tartozó hitelesítő adatok elérhetősége.</span><span class="sxs-lookup"><span data-stu-id="b66e3-106">Availability of an SFTP host and corresponding credentials.</span></span>

## <a name="known-limitations"></a><span data-ttu-id="b66e3-107">Ismert korlátozások</span><span class="sxs-lookup"><span data-stu-id="b66e3-107">Known limitations</span></span>

- <span data-ttu-id="b66e3-108">Az exportálás futtatása a rendszer teljesítményétől függ.</span><span class="sxs-lookup"><span data-stu-id="b66e3-108">The runtime of an export depends on your system performance.</span></span> <span data-ttu-id="b66e3-109">A kiszolgáló minimális konfigurációjának ajánlott két processzormag és 1 Gb memória.</span><span class="sxs-lookup"><span data-stu-id="b66e3-109">We recommend two CPU cores and 1 Gb of memory as minimal configuration of your server.</span></span> 
- <span data-ttu-id="b66e3-110">Az legfeljebb 100 millió ügyfélprofillal rendelkező entitások exportálása 90 percet is igénybe fog venni, ha két processzormag és 1 Gb memória ajánlott minimális konfigurációját használja.</span><span class="sxs-lookup"><span data-stu-id="b66e3-110">Exporting entities with up to 100 million customer profiles can take 90 minutes when using the recommended minimal configuration of two CPU cores and 1 Gb of memory.</span></span> 

## <a name="set-up-connection-to-sftp"></a><span data-ttu-id="b66e3-111">Kapcsolatok beállítása SFTP-hez</span><span class="sxs-lookup"><span data-stu-id="b66e3-111">Set up connection to SFTP</span></span>

1. <span data-ttu-id="b66e3-112">Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="b66e3-112">Go to **Admin** > **Connections**.</span></span>

1. <span data-ttu-id="b66e3-113">Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza az **SFTP** lehetőséget a kapcsolat konfigurálásához.</span><span class="sxs-lookup"><span data-stu-id="b66e3-113">Select **Add connection** and choose **SFTP** to configure the connection.</span></span>

1. <span data-ttu-id="b66e3-114">Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak.</span><span class="sxs-lookup"><span data-stu-id="b66e3-114">Give your connection a recognizable name in the **Display name** field.</span></span> <span data-ttu-id="b66e3-115">A név és a kapcsolat típusa írja le ezt a kapcsolatot.</span><span class="sxs-lookup"><span data-stu-id="b66e3-115">The name and the type of the connection describe this connection.</span></span> <span data-ttu-id="b66e3-116">Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.</span><span class="sxs-lookup"><span data-stu-id="b66e3-116">We recommend choosing a name that explains the purpose and target of the connection.</span></span>

1. <span data-ttu-id="b66e3-117">A kapcsolat használóinak kiválasztása.</span><span class="sxs-lookup"><span data-stu-id="b66e3-117">Choose who can use this connection.</span></span> <span data-ttu-id="b66e3-118">Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz.</span><span class="sxs-lookup"><span data-stu-id="b66e3-118">If you take no action, the default will be Administrators.</span></span> <span data-ttu-id="b66e3-119">További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).</span><span class="sxs-lookup"><span data-stu-id="b66e3-119">For more information, see [Allow contributors to use a connection for exports](connections.md#allow-contributors-to-use-a-connection-for-exports).</span></span>

1. <span data-ttu-id="b66e3-120">Adjon meg egy **Felhasználónevet**, **Jelszót**, **Állomásnevet** és **Exportálási mappát** az SFTP-fiókhoz.</span><span class="sxs-lookup"><span data-stu-id="b66e3-120">Provide a **Username**, **Password**, **Hostname**, and **Export folder** for your SFTP account.</span></span>

1. <span data-ttu-id="b66e3-121">A kapcsolat teszteléséhez válassza az **Ellenőrzés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="b66e3-121">Select **Verify** to test the connection.</span></span>

1. <span data-ttu-id="b66e3-122">Válassza ki, hogy szeretné-e exportálni a **Tömörített** vagy **Tömörítetlen** adatokat, és a **mező elválasztó karaktert** az exportált fájlokhoz.</span><span class="sxs-lookup"><span data-stu-id="b66e3-122">Choose if you want to export your data **Gzipped** or **Unzipped** and the **field delimiter** for the exported files.</span></span>

1. <span data-ttu-id="b66e3-123">Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.</span><span class="sxs-lookup"><span data-stu-id="b66e3-123">Select **I agree** to confirm the **Data privacy and compliance**.</span></span>

1. <span data-ttu-id="b66e3-124">A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="b66e3-124">Select **Save** to complete the connection.</span></span>

## <a name="configure-an-export"></a><span data-ttu-id="b66e3-125">Exportálás konfigurálása</span><span class="sxs-lookup"><span data-stu-id="b66e3-125">Configure an export</span></span>

<span data-ttu-id="b66e3-126">Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz.</span><span class="sxs-lookup"><span data-stu-id="b66e3-126">You can configure this export if you have access to a connection of this type.</span></span> <span data-ttu-id="b66e3-127">További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).</span><span class="sxs-lookup"><span data-stu-id="b66e3-127">For more information, see [Permissions needed to configure an export](export-destinations.md#set-up-a-new-export).</span></span>

1. <span data-ttu-id="b66e3-128">Menjen az **Adatok** > **Exportálások** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="b66e3-128">Go to **Data** > **Exports**.</span></span>

1. <span data-ttu-id="b66e3-129">Új exportálás létrehozásához válassza a **Célhely hozzáadása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="b66e3-129">To create a new export, select **Add destination**.</span></span>

1. <span data-ttu-id="b66e3-130">A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot az SFTP szakaszból.</span><span class="sxs-lookup"><span data-stu-id="b66e3-130">In the **Connection for export** field, choose a connection from the SFTP section.</span></span> <span data-ttu-id="b66e3-131">Ha nem látja ezt a szakasznevet, az Ön számára nincs ilyen típusú kapcsolat.</span><span class="sxs-lookup"><span data-stu-id="b66e3-131">If you don't see this section name, there are no connections of this type available to you.</span></span>

1. <span data-ttu-id="b66e3-132">Jelölje ki az exportálni kívánt entitásokat, például szegmenseket.</span><span class="sxs-lookup"><span data-stu-id="b66e3-132">Select the entities, for example segments, you want to export.</span></span>

   > [!NOTE]
   > <span data-ttu-id="b66e3-133">Az egyes kijelölt entitások exportáláskor legfeljebb öt kimeneti fájlra lesznek felosztva.</span><span class="sxs-lookup"><span data-stu-id="b66e3-133">Each selected entity will be split up into up to five output files when exported.</span></span> 

1. <span data-ttu-id="b66e3-134">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="b66e3-134">Select **Save**.</span></span>

<span data-ttu-id="b66e3-135">Az exportálás mentése nem futtatja azonnal az exportálást.</span><span class="sxs-lookup"><span data-stu-id="b66e3-135">Saving an export doesn't run the export immediately.</span></span>

<span data-ttu-id="b66e3-136">Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut.</span><span class="sxs-lookup"><span data-stu-id="b66e3-136">The export runs with every [scheduled refresh](system.md#schedule-tab).</span></span> <span data-ttu-id="b66e3-137">Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand).</span><span class="sxs-lookup"><span data-stu-id="b66e3-137">You can also [export data on demand](export-destinations.md#run-exports-on-demand).</span></span> 

## <a name="data-privacy-and-compliance"></a><span data-ttu-id="b66e3-138">Adatvédelem és megfelelőség</span><span class="sxs-lookup"><span data-stu-id="b66e3-138">Data privacy and compliance</span></span>

<span data-ttu-id="b66e3-139">Amikor engedélyezi az Dynamics 365 Customer Insights szolgáltatásnak az adatok átvitelét SFTP-n keresztül, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat.</span><span class="sxs-lookup"><span data-stu-id="b66e3-139">When you enable Dynamics 365 Customer Insights to transmit data via SFTP, you allow transfer of data outside of the compliance boundary for Dynamics 365 Customer Insights, including potentially sensitive data such as Personal Data.</span></span> <span data-ttu-id="b66e3-140">A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy az exportálási célhely megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek.</span><span class="sxs-lookup"><span data-stu-id="b66e3-140">Microsoft will transfer such data at your instruction, but you are responsible for ensuring that the export destination meets any privacy or security obligations you may have.</span></span> <span data-ttu-id="b66e3-141">További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).</span><span class="sxs-lookup"><span data-stu-id="b66e3-141">For more information, see [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?linkid=396732).</span></span>
<span data-ttu-id="b66e3-142">A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.</span><span class="sxs-lookup"><span data-stu-id="b66e3-142">Your Dynamics 365 Customer Insights Administrator can remove this export destination at any time to discontinue use of this functionality.</span></span>

[!INCLUDE[footer-include](../includes/footer-banner.md)]
