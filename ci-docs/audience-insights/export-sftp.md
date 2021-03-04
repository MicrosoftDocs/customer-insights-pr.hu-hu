---
title: Customer Insights adatok exportálása a SFTP gazdaszámítógépekhez
description: Megismerkedhet vele, hogyan konfigurálható egy SFTP-hoszt kapcsolata.
ms.date: 01/27/2021
ms.reviewer: philk
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: ddba55b3ca159c0095371e46385dcf1d3ed4a63d
ms.sourcegitcommit: 139548f8a2d0f24d54c4a6c404a743eeeb8ef8e0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/15/2021
ms.locfileid: "5268001"
---
# <a name="connector-for-sftp-preview"></a><span data-ttu-id="1b927-103">SFTP-összekötő (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="1b927-103">Connector for SFTP (preview)</span></span>

<span data-ttu-id="1b927-104">Ügyféladatait külső alkalmazásokban is használhatja, ha Secure File Transfer Protocol (SFTP) gazdaszámítógépra exportálja.</span><span class="sxs-lookup"><span data-stu-id="1b927-104">Use your customer data in third-party applications by exporting them to a Secure File Transfer Protocol (SFTP) host.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1b927-105">Előfeltételek</span><span class="sxs-lookup"><span data-stu-id="1b927-105">Prerequisites</span></span>

- <span data-ttu-id="1b927-106">Egy SFTP állomás és a hozzájuk tartozó hitelesítő adatok elérhetősége.</span><span class="sxs-lookup"><span data-stu-id="1b927-106">Availability of an SFTP host and corresponding credentials.</span></span>

## <a name="connect-to-sftp"></a><span data-ttu-id="1b927-107">Csatlakozás a SFTP-hez</span><span class="sxs-lookup"><span data-stu-id="1b927-107">Connect to SFTP</span></span>

1. <span data-ttu-id="1b927-108">Válassz a **Rendszergazda** > **Célok exportálása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="1b927-108">Go to **Admin** > **Export destinations**.</span></span>

1. <span data-ttu-id="1b927-109">Az **SFTP** alatt válassza a **Beállítás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="1b927-109">Under **SFTP**, select **Set up**.</span></span>

1. <span data-ttu-id="1b927-110">Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben.</span><span class="sxs-lookup"><span data-stu-id="1b927-110">Give your destination a recognizable name in the **Display name** field.</span></span>

1. <span data-ttu-id="1b927-111">Adjon meg egy **Felhasználónevet**, **Jelszót**, **Állomásnevet** és **Exportálási mappát** az SFTP-fiókhoz.</span><span class="sxs-lookup"><span data-stu-id="1b927-111">Provide a **Username**, **Password**, **Hostname**, and **Export folder** for your SFTP account.</span></span>

1. <span data-ttu-id="1b927-112">A kapcsolat teszteléséhez válassza az **Ellenőrzés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="1b927-112">Select **Verify** to test the connection.</span></span>

1. <span data-ttu-id="1b927-113">A sikeres ellenőrzés után válassza ki, hogy szeretné-e exportálni az adatokat **Tömörített** vagy **Nem tömörített** formátumban, válassza ki a **mezőelválasztót** az exportált fájlokhoz.</span><span class="sxs-lookup"><span data-stu-id="1b927-113">After successful verification, choose if you want to export your data **Gzipped** or **Unzipped**, and select the **field delimiter** for the exported files.</span></span>

1. <span data-ttu-id="1b927-114">Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.</span><span class="sxs-lookup"><span data-stu-id="1b927-114">Select **I agree** to confirm the **Data privacy and compliance**.</span></span>

1. <span data-ttu-id="1b927-115">Az exportálás konfigurálásának megkezdéséhez válassza a **Tovább** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="1b927-115">Select **Next** to start configuring the export.</span></span>

## <a name="configure-the-export"></a><span data-ttu-id="1b927-116">Az exportálás konfigurálása</span><span class="sxs-lookup"><span data-stu-id="1b927-116">Configure the export</span></span>

1. <span data-ttu-id="1b927-117">Jelölje ki az exportálni kívánt entitásokat, például szegmenseket.</span><span class="sxs-lookup"><span data-stu-id="1b927-117">Select the entities, for example segments, you want to export.</span></span>

   > [!NOTE]
   > <span data-ttu-id="1b927-118">Minden egyes kijelölt entitás legfeljebb öt kimeneti fájlt képes exportálni.</span><span class="sxs-lookup"><span data-stu-id="1b927-118">Each selected entity will be up to five output files when exported.</span></span> 

1. <span data-ttu-id="1b927-119">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="1b927-119">Select **Save**.</span></span>

## <a name="export-the-data"></a><span data-ttu-id="1b927-120">Az adatok exportálása</span><span class="sxs-lookup"><span data-stu-id="1b927-120">Export the data</span></span>

<span data-ttu-id="1b927-121">[Igény szerint exportálhatja az adatot](export-destinations.md).</span><span class="sxs-lookup"><span data-stu-id="1b927-121">You can [export data on demand](export-destinations.md).</span></span> <span data-ttu-id="1b927-122">Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) együtt is lefut.</span><span class="sxs-lookup"><span data-stu-id="1b927-122">The export will also run with every [scheduled refresh](system.md#schedule-tab).</span></span>

## <a name="known-limitations"></a><span data-ttu-id="1b927-123">Ismert korlátozások</span><span class="sxs-lookup"><span data-stu-id="1b927-123">Known limitations</span></span>

- <span data-ttu-id="1b927-124">Az exportálás futtatása a rendszer teljesítményétől függ.</span><span class="sxs-lookup"><span data-stu-id="1b927-124">The runtime of an export depends on your system performance.</span></span> <span data-ttu-id="1b927-125">A kiszolgáló minimális konfigurációjának ajánlott két processzormag és 1 Gb memória.</span><span class="sxs-lookup"><span data-stu-id="1b927-125">We recommend two CPU cores and 1 Gb of memory as minimal configuration of your server.</span></span> 
- <span data-ttu-id="1b927-126">Az legfeljebb 100 millió ügyfélprofillal rendelkező entitások exportálása 90 percet is igénybe fog venni, ha két processzormag és 1 Gb memória ajánlott minimális konfigurációját használja.</span><span class="sxs-lookup"><span data-stu-id="1b927-126">Exporting entities with up to 100 million customer profiles can take 90 minutes when using the recommended minimal configuration of two CPU cores and 1 Gb of memory.</span></span> 

## <a name="data-privacy-and-compliance"></a><span data-ttu-id="1b927-127">Adatvédelem és megfelelőség</span><span class="sxs-lookup"><span data-stu-id="1b927-127">Data privacy and compliance</span></span>

<span data-ttu-id="1b927-128">Amikor engedélyezi az Dynamics 365 Customer Insights szolgáltatásnak az adatok átvitelét SFTP-n keresztül, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat.</span><span class="sxs-lookup"><span data-stu-id="1b927-128">When you enable Dynamics 365 Customer Insights to transmit data via SFTP, you allow transfer of data outside of the compliance boundary for Dynamics 365 Customer Insights, including potentially sensitive data such as Personal Data.</span></span> <span data-ttu-id="1b927-129">A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy az exportálási célhely megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek.</span><span class="sxs-lookup"><span data-stu-id="1b927-129">Microsoft will transfer such data at your instruction, but you are responsible for ensuring that the export destination meets any privacy or security obligations you may have.</span></span> <span data-ttu-id="1b927-130">További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).</span><span class="sxs-lookup"><span data-stu-id="1b927-130">For more information, see [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?linkid=396732).</span></span>
<span data-ttu-id="1b927-131">A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.</span><span class="sxs-lookup"><span data-stu-id="1b927-131">Your Dynamics 365 Customer Insights Administrator can remove this export destination at any time to discontinue use of this functionality.</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]