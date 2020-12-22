---
title: Az adatalanyok jogainak (DSR) megfelelő kérelmek a GDPR szerint | Microsoft Docs
description: Adatalanyi kérelmekre adott válasz a Dynamics 365 Customer Insights célközönség-információ funkciójához.
ms.date: 05/14/2020
ms.reviewer: wimohabb
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: f276a73feca52023391ad92fbc84359921b85328
ms.sourcegitcommit: cf9b78559ca189d4c2086a66c879098d56c0377a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/03/2020
ms.locfileid: "4406009"
---
# <a name="data-subject-rights-dsr-requests-under-gdpr"></a><span data-ttu-id="94a04-103">Az adatalanyok jogainak (DSR) megfelelő kérelmek a GDPR szerint</span><span class="sxs-lookup"><span data-stu-id="94a04-103">Data Subject Rights (DSR) requests under GDPR</span></span>

## <a name="responding-to-gdpr-data-subject-delete-requests-for-dynamics-365-customer-insights-audience-insights-capability"></a><span data-ttu-id="94a04-104">GDPR adatalanyi törlési kérelmekre adott válasz a Dynamics 365 Customer Insights célközönség-információ funkciójához</span><span class="sxs-lookup"><span data-stu-id="94a04-104">Responding to GDPR data subject delete requests for Dynamics 365 Customer Insights audience insights capability</span></span>

<span data-ttu-id="94a04-105">A személyes adatoknak a szervezet ügyféladatok közüli törléséhez való jog kulcsfontosságú védelmi elem az Általános adatvédelmi rendeletben (GDPR).</span><span class="sxs-lookup"><span data-stu-id="94a04-105">The “right to erasure” by the removal of personal data from an organization’s customer data is a key protection in the General Data Protection Regulation (GDPR).</span></span> <span data-ttu-id="94a04-106">A személyes adatok eltávolítása magába foglalja az összes személyes adat és a rendszer által létrehozott naplók eltávolítását, kivéve az auditnaplózási információkat.</span><span class="sxs-lookup"><span data-stu-id="94a04-106">Removing personal data includes removing all personal data and system-generated logs, except audit log information.</span></span>

### <a name="manage-data-subject-delete-requests"></a><span data-ttu-id="94a04-107">Az adatalanyok törlési kérelmeinek kezelése</span><span class="sxs-lookup"><span data-stu-id="94a04-107">Manage data subject delete requests</span></span>

<span data-ttu-id="94a04-108">A célközönség-információk a következő termékeken belüli élményeket kínálja egy adott ügyfél vagy felhasználó személyes adatainak törléséhez:</span><span class="sxs-lookup"><span data-stu-id="94a04-108">Audience insights offers the following in-product experiences to delete personal data for a specific customer or user:</span></span>

- <span data-ttu-id="94a04-109">**Ügyféladatok törlési kérelmeinek kezelése**: A Customer Insights ügyféladatait a Customer Insights megoldáson kívüli adatforrásokból lettek betöltve.</span><span class="sxs-lookup"><span data-stu-id="94a04-109">**Manage delete requests for customer data**: Customer data in Customer Insights is ingested from original data sources external to Customer Insights.</span></span> <span data-ttu-id="94a04-110">Minden GDPR szerinti törlési kérelmet az eredeti adatforráson kell végrehajtani.</span><span class="sxs-lookup"><span data-stu-id="94a04-110">All GDPR delete requests must be performed in the original data source.</span></span>
- <span data-ttu-id="94a04-111">**Törlési kérelmek kezelése a Customer Insights felhasználói adatokhoz**: Customer Insights által felhasználókhoz létrehozott adatok.</span><span class="sxs-lookup"><span data-stu-id="94a04-111">**Manage delete requests for Customer Insights user data**: Data for users is created by Customer Insights.</span></span> <span data-ttu-id="94a04-112">Minden GDPR szerinti törlési kérelmet a Customer Insights megoldásban kell elvégezni.</span><span class="sxs-lookup"><span data-stu-id="94a04-112">All GDPR delete requests must be performed in Customer Insights.</span></span>

#### <a name="manage-delete-requests-for-customer-data"></a><span data-ttu-id="94a04-113">Ügyféladatok törlési kérelmeinek kezelése</span><span class="sxs-lookup"><span data-stu-id="94a04-113">Manage delete requests for customer data</span></span>

<span data-ttu-id="94a04-114">A Customer Insights rendszergazdák az alábbi lépések végrehajtásával eltávolíthatják az adatforrásban törölt ügyféladatokat:</span><span class="sxs-lookup"><span data-stu-id="94a04-114">A Customer Insights admin can follow these steps to remove customer data that was deleted in the data source:</span></span>

1. <span data-ttu-id="94a04-115">Jelentkezzen be a Dynamics 365 Customer Insights rendszerbe.</span><span class="sxs-lookup"><span data-stu-id="94a04-115">Sign in to Dynamics 365 Customer Insights.</span></span>
2. <span data-ttu-id="94a04-116">A célközönség információin belül nyissa meg a következőt **Adatok** > **Adatforrások**</span><span class="sxs-lookup"><span data-stu-id="94a04-116">In audience insights, go to **Data** > **Data sources**</span></span>
3. <span data-ttu-id="94a04-117">A törölt ügyféladatokat tartalmazó minden egyes adatforráshoz a listából:</span><span class="sxs-lookup"><span data-stu-id="94a04-117">For each data source in the list that contains deleted customer data:</span></span>
   1. <span data-ttu-id="94a04-118">Válassza a (...), majd a **Frissítés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="94a04-118">Select (...) and then select **Refresh**.</span></span>
   2. <span data-ttu-id="94a04-119">Ellenőrizze az adatforrás állapotát az **Állapot** alatt.</span><span class="sxs-lookup"><span data-stu-id="94a04-119">Check the status of the data source under **Status**.</span></span> <span data-ttu-id="94a04-120">A pipa azt jelenti, hogy a frissítés sikeresen megtörtént.</span><span class="sxs-lookup"><span data-stu-id="94a04-120">A check mark means the refresh was successful.</span></span> <span data-ttu-id="94a04-121">A figyelmeztető háromszög azt jelenti, hogy valamilyen hiba történt.</span><span class="sxs-lookup"><span data-stu-id="94a04-121">A warning triangle means something went wrong.</span></span> <span data-ttu-id="94a04-122">Ha egy figyelmeztető háromszög jelenik meg, forduljon ide: D365CI@microsoft.com.</span><span class="sxs-lookup"><span data-stu-id="94a04-122">If a warning triangle is displayed, contact D365CI@microsoft.com.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="94a04-123">![Ügyféladatok GDPR törlési kérelmeinek kezelése](media/gdpr-data-sources.png "Ügyféladatok GDPR törlési kérelmeinek kezelése")</span><span class="sxs-lookup"><span data-stu-id="94a04-123">![Handling GDPR delete requests for customer data](media/gdpr-data-sources.png "Handling GDPR delete requests for customer data")</span></span>

#### <a name="manage-delete-requests-for-user-data"></a><span data-ttu-id="94a04-124">Felhasználói adatok törlési kérelmeinek kezelése</span><span class="sxs-lookup"><span data-stu-id="94a04-124">Manage delete requests for user data</span></span>

<span data-ttu-id="94a04-125">Egy Customer Insights rendszergazda a Customer Insights ügyféladatok törlését az alábbi lépésekkel hajthatja végre:</span><span class="sxs-lookup"><span data-stu-id="94a04-125">A Customer Insights admin can follow these steps to delete Customer Insights user data:</span></span>

1. <span data-ttu-id="94a04-126">Jelentkezzen be a Dynamics 365 Customer Insights rendszerbe.</span><span class="sxs-lookup"><span data-stu-id="94a04-126">Sign in to Dynamics 365 Customer Insights.</span></span>
2. <span data-ttu-id="94a04-127">A célközönség információin belül nyissa meg a következőt **Rendszergazda** > **Engedélyek**.</span><span class="sxs-lookup"><span data-stu-id="94a04-127">In audience insights, go to **Admin** > **Permissions**.</span></span>
3. <span data-ttu-id="94a04-128">Jelölje be a törölni kívánt felhasznáó jelölőnégyzetét.</span><span class="sxs-lookup"><span data-stu-id="94a04-128">Select the check box for the user you want to delete.</span></span>
4. <span data-ttu-id="94a04-129">Válassza az **Eltávolítás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="94a04-129">Select **Remove**.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="94a04-130">![GDPR felhasználói adatokra vonatkozó törlési kérelmeinek kezelése](media/gdpr-permissions.png "GDPR felhasználói adatokra vonatkozó törlési kérelmeinek kezelése")</span><span class="sxs-lookup"><span data-stu-id="94a04-130">![Handling GDPR delete requests foruser data](media/gdpr-permissions.png "Handling GDPR delete requests for user data")</span></span>

## <a name="responding-to-gdpr-data-subject-export-requests"></a><span data-ttu-id="94a04-131">GDPR szerinti Adatalanyi exportálási kérelmek megválaszolása</span><span class="sxs-lookup"><span data-stu-id="94a04-131">Responding to GDPR data subject export requests</span></span>

<span data-ttu-id="94a04-132">Az Általános adatvédelmi rendelet (GDPR) világában való eligazodás során az Önnel folytatott partneri elkötelezettség részeként egy előkészületeket elősegítő dokumentációt fejlesztettünk ki.</span><span class="sxs-lookup"><span data-stu-id="94a04-132">As part of our commitment to partner with you on your journey to the General Data Protection Regulation (GDPR), we’ve developed documentation to help you prepare.</span></span> <span data-ttu-id="94a04-133">Ez a dokumentáció ismerteti azokat a lépéseket, amelyeket ma a GDPR-megfelelőség támogatásához megtehet a célközönség-információk használatával.</span><span class="sxs-lookup"><span data-stu-id="94a04-133">This documentation describes steps you can take today to support GDPR compliance when using audience insights.</span></span>

### <a name="manage-export-and-view-requests"></a><span data-ttu-id="94a04-134">Az exportálási és a megtekintési kérelmek kezelése</span><span class="sxs-lookup"><span data-stu-id="94a04-134">Manage export and view requests</span></span>

<span data-ttu-id="94a04-135">Az adathordozhatósági jog lehetővé teszi, hogy az adatalanyok személyes adataik másolatát elektronikus formátumban („strukturált, általánosan használt, géppel olvasható és interoperábilis formátumként”) formátumban elkérjék, amely átvihető másik adatkezelőhöz.</span><span class="sxs-lookup"><span data-stu-id="94a04-135">The right of data portability allows data subjects to request a copy of their personal data in an electronic format (a “structured, commonly used, machine readable, and interoperable format”) that can be transmitted to another data controller.</span></span>

#### <a name="export-customer-data-tenant-admin"></a><span data-ttu-id="94a04-136">Ügyféladatok exportálása (bérlői adminisztrátor)</span><span class="sxs-lookup"><span data-stu-id="94a04-136">Export customer data (tenant admin)</span></span>

<span data-ttu-id="94a04-137">Az adatok exportálásához a bérlői rendszergazda a következő lépéseket hajthatja végre:</span><span class="sxs-lookup"><span data-stu-id="94a04-137">A tenant administrator can follow these steps to export data:</span></span>

1. <span data-ttu-id="94a04-138">E-mailben elküldhet egy kérelmet az ügyfél e-mail címének meghatározásával a D365CI@microsoft.com címre.</span><span class="sxs-lookup"><span data-stu-id="94a04-138">Send an email to D365CI@microsoft.com specifying the customer’s email address in the request.</span></span> <span data-ttu-id="94a04-139">A Customer Insights csoport egy adminisztrátora e-mailt küld a regisztrált bérlői rendszergazdai e-mail címre, amelyben megerősítést kér az adatok exportálása céljából.</span><span class="sxs-lookup"><span data-stu-id="94a04-139">The Customer Insights team will send an email to the registered tenant admin email address, asking for confirmation to export data.</span></span>
2. <span data-ttu-id="94a04-140">Nyugtázza a kért ügyfél adatainak exportálását.</span><span class="sxs-lookup"><span data-stu-id="94a04-140">Acknowledge the confirmation to export the data for the requested customer.</span></span>
3. <span data-ttu-id="94a04-141">Az exportált adatok a bérlői rendszergazdai e-mail címen keresztül fogadhatók.</span><span class="sxs-lookup"><span data-stu-id="94a04-141">Receive the exported data through the tenant admin email address.</span></span>

#### <a name="export-user-data-tenant-admin"></a><span data-ttu-id="94a04-142">Felhasználói adatok exportálása (bérlői adminisztrátor)</span><span class="sxs-lookup"><span data-stu-id="94a04-142">Export user data (tenant admin)</span></span>

1. <span data-ttu-id="94a04-143">E-mailben elküldhet egy kérelmet a felhasználó e-mail címének meghatározásával a D365CI@microsoft.com címre.</span><span class="sxs-lookup"><span data-stu-id="94a04-143">Send an email to D365CI@microsoft.com specifying the user’s email address in the request.</span></span> <span data-ttu-id="94a04-144">A Customer Insights csoport egy adminisztrátora e-mailt küld a regisztrált bérlői rendszergazdai e-mail címre, amelyben megerősítést kér az adatok exportálása céljából.</span><span class="sxs-lookup"><span data-stu-id="94a04-144">The Customer Insights team will send an email to the registered tenant admin email address, asking for confirmation to export data.</span></span>
2. <span data-ttu-id="94a04-145">Nyugtázza a felhasználó adatainak exportálását.</span><span class="sxs-lookup"><span data-stu-id="94a04-145">Acknowledge the confirmation to export the data for the requested user.</span></span>
3. <span data-ttu-id="94a04-146">Az exportált adatok a bérlői rendszergazdai e-mail címen keresztül fogadhatók.</span><span class="sxs-lookup"><span data-stu-id="94a04-146">Receive the exported data through the tenant admin email address.</span></span>
