---
title: Customer Insights adatok exportálása a SFTP gazdaszámítógépekhez
description: Megismerkedhet vele, hogyan konfigurálható egy SFTP-hoszt kapcsolata.
ms.date: 06/05/2020
ms.reviewer: philk
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: c2529744d7a26a06324b79cad6a8001d75903545
ms.sourcegitcommit: 6a6df62fa12dcb9bd5f5a39cc3ee0e2b3988184b
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/25/2020
ms.locfileid: "4643506"
---
# <a name="connector-for-sftp-preview"></a><span data-ttu-id="6462b-103">SFTP-összekötő (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="6462b-103">Connector for SFTP (preview)</span></span>

<span data-ttu-id="6462b-104">Ügyféladatait külső alkalmazásokban is használhatja, ha Secure File Transfer Protocol (SFTP) gazdaszámítógépra exportálja.</span><span class="sxs-lookup"><span data-stu-id="6462b-104">Use your customer data in third-party applications by exporting them to a Secure File Transfer Protocol(SFTP) host.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6462b-105">Előfeltételek</span><span class="sxs-lookup"><span data-stu-id="6462b-105">Prerequisites</span></span>

- <span data-ttu-id="6462b-106">Az SFTP-hoszt és a megfelelő hitelesítő adatok rendelkezésre állása.</span><span class="sxs-lookup"><span data-stu-id="6462b-106">Availability of a SFTP host and corresponding credentials.</span></span>

## <a name="connect-to-sftp"></a><span data-ttu-id="6462b-107">Csatlakozás SFTP-hez</span><span class="sxs-lookup"><span data-stu-id="6462b-107">Connect to SFTP</span></span>

1. <span data-ttu-id="6462b-108">Válassz a **Rendszergazda** > **Célok exportálása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="6462b-108">Go to **Admin** > **Export destinations**.</span></span>

1. <span data-ttu-id="6462b-109">Az **SFTP** alatt válassza a **Beállítás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="6462b-109">Under **SFTP**, select **Set up**.</span></span>

1. <span data-ttu-id="6462b-110">Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben.</span><span class="sxs-lookup"><span data-stu-id="6462b-110">Give your destination a recognizable name in the **Display name** field.</span></span>

1. <span data-ttu-id="6462b-111">Adjon meg egy **Felhasználónevet**, **Jelszót** és **Eszköznév** értéket az SFTP-fiókhoz.</span><span class="sxs-lookup"><span data-stu-id="6462b-111">Provide a **Username**, **Password** and **Hostname** for your SFTP account.</span></span> <span data-ttu-id="6462b-112">Példa: Ha az SFTP kiszolgáló gyökérkönyvtára/root/folder, és szeretné, hogy az adatok a /root/folder/ci_export_destination_folder mappába exportálódjanak, akkor a gazdaszámítógép legyen: sftp://<server_address>/ci_export_destination_folder".</span><span class="sxs-lookup"><span data-stu-id="6462b-112">Example: If your SFTP server's root folder is /root/folder, and you would like the data to be exported to /root/folder/ci_export_destination_folder, the the host should be sftp://<server_address>/ci_export_destination_folder".</span></span>

1. <span data-ttu-id="6462b-113">A kapcsolat teszteléséhez válassza az **Ellenőrzés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="6462b-113">Select **Verify** to test the connection.</span></span>

1. <span data-ttu-id="6462b-114">A sikeres ellenőrzés után válassza ki, hogy **Tömörített** vagy **Kibontott** formátumban szeretné exportálni az adatokat, és jelölje ki az exportált fájlokhoz tartozó **mezőhatárolót**.</span><span class="sxs-lookup"><span data-stu-id="6462b-114">After successful verification, choose if you want to export your data **Zipped** or **Unzipped**, and select the **field delimiter** for the exported files.</span></span>

1. <span data-ttu-id="6462b-115">Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.</span><span class="sxs-lookup"><span data-stu-id="6462b-115">Select **I agree** to confirm the **Data privacy and compliance**.</span></span>

1. <span data-ttu-id="6462b-116">Az exportálás konfigurálásának megkezdéséhez válassza a **Tovább** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="6462b-116">Select **Next** to start configuring the export.</span></span>

## <a name="configure-the-connection"></a><span data-ttu-id="6462b-117">A kapcsolat konfigurálása</span><span class="sxs-lookup"><span data-stu-id="6462b-117">Configure the connection</span></span>

1. <span data-ttu-id="6462b-118">Jelölje ki az **ügyfélattribútumokat** amelyeket exportálni szeretne.</span><span class="sxs-lookup"><span data-stu-id="6462b-118">Select the **customer attributes** you want to export.</span></span> <span data-ttu-id="6462b-119">Egy vagy több attribútum is exportálható.</span><span class="sxs-lookup"><span data-stu-id="6462b-119">You can export one or multiple attributes.</span></span>

1. <span data-ttu-id="6462b-120">Válassza a **Következő** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="6462b-120">Select **Next**.</span></span>

1. <span data-ttu-id="6462b-121">Jelölje ki a szegmenseket, amelyeket exportálni szeretne.</span><span class="sxs-lookup"><span data-stu-id="6462b-121">Select the segments you want to export.</span></span>

1. <span data-ttu-id="6462b-122">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="6462b-122">Select **Save**.</span></span>

## <a name="export-the-data"></a><span data-ttu-id="6462b-123">Az adatok exportálása</span><span class="sxs-lookup"><span data-stu-id="6462b-123">Export the data</span></span>

<span data-ttu-id="6462b-124">[Igény szerint exportálhatja az adatot](export-destinations.md).</span><span class="sxs-lookup"><span data-stu-id="6462b-124">You can [export data on demand](export-destinations.md).</span></span> <span data-ttu-id="6462b-125">Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) együtt is lefut.</span><span class="sxs-lookup"><span data-stu-id="6462b-125">The export will also run with every [scheduled refresh](system.md#schedule-tab).</span></span>

## <a name="data-privacy-and-compliance"></a><span data-ttu-id="6462b-126">Adatvédelem és megfelelőség</span><span class="sxs-lookup"><span data-stu-id="6462b-126">Data privacy and compliance</span></span>

<span data-ttu-id="6462b-127">Amikor engedélyezi az Dynamics 365 Customer Insights szolgáltatásnak az adatok átvitelét SFTP-n keresztül, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat.</span><span class="sxs-lookup"><span data-stu-id="6462b-127">When you enable Dynamics 365 Customer Insights to transmit data via SFTP, you allow transfer of data outside of the compliance boundary for Dynamics 365 Customer Insights, including potentially sensitive data such as Personal Data.</span></span> <span data-ttu-id="6462b-128">A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy az exportálási célhely megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek.</span><span class="sxs-lookup"><span data-stu-id="6462b-128">Microsoft will transfer such data at your instruction, but you are responsible for ensuring that the export destination meets any privacy or security obligations you may have.</span></span> <span data-ttu-id="6462b-129">További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).</span><span class="sxs-lookup"><span data-stu-id="6462b-129">For more information, see [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?linkid=396732).</span></span>
<span data-ttu-id="6462b-130">A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.</span><span class="sxs-lookup"><span data-stu-id="6462b-130">Your Dynamics 365 Customer Insights Administrator can remove this export destination at any time to discontinue use of this functionality.</span></span>
