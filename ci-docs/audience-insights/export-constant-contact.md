---
title: Customer Insights-adatok exportálása az Constant Contactra
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja az Constant Contactba.
ms.date: 03/22/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 29f4320c798db62609283e3c48f0b47a4f0b982f
ms.sourcegitcommit: 831765a55775d358447cb7ffa56f2c3b85459084
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/01/2021
ms.locfileid: "6124276"
---
# <a name="export-segments-to-constant-contact-preview"></a><span data-ttu-id="c4598-103">Szegmensek exportálása az Állandó kapcsolattartóba (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="c4598-103">Export segments to Constant Contact (preview)</span></span>

<span data-ttu-id="c4598-104">Exportálja az egyesített ügyfélprofilok szegmensét az Constant Contactba, és használja őket marketing-tevékenységekre.</span><span class="sxs-lookup"><span data-stu-id="c4598-104">Export segments of unified customer profiles to Constant Contact and use them for marketing activities.</span></span> 

## <a name="prerequisites-for-a-connection"></a><span data-ttu-id="c4598-105">Egy kapcsolat előfeltételei</span><span class="sxs-lookup"><span data-stu-id="c4598-105">Prerequisites for a connection</span></span>

-   <span data-ttu-id="c4598-106">Van egy [Constant Contact fiókja](https://www.constantcontact.com/account-home) és ahhoz tartozó rendszergazdai hitelesítő adatai.</span><span class="sxs-lookup"><span data-stu-id="c4598-106">You have an [Constant Contact account](https://www.constantcontact.com/account-home) and corresponding administrator credentials.</span></span>
-   <span data-ttu-id="c4598-107">[Konfigurált szegmensekkel](segments.md) rendelkezik a célközönségi-információkban.</span><span class="sxs-lookup"><span data-stu-id="c4598-107">You have [configured segments](segments.md) in audience insights.</span></span>
-   <span data-ttu-id="c4598-108">Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.</span><span class="sxs-lookup"><span data-stu-id="c4598-108">Unified customer profiles in the exported segments contain a field representing an email address.</span></span>

## <a name="known-limitations"></a><span data-ttu-id="c4598-109">Ismert korlátozások</span><span class="sxs-lookup"><span data-stu-id="c4598-109">Known limitations</span></span>

- <span data-ttu-id="c4598-110">Az Constant Contact exportálásonként legfeljebb 1 millió profil exportálható.</span><span class="sxs-lookup"><span data-stu-id="c4598-110">You can export up to 1 million profiles per export to Constant Contact.</span></span>
- <span data-ttu-id="c4598-111">Az Constant Contactba való exportálás a szegmensekre korlátozódik.</span><span class="sxs-lookup"><span data-stu-id="c4598-111">Exporting to Constant Contact is limited to segments.</span></span>
- <span data-ttu-id="c4598-112">1 millió profil exportálása az Constant Contact alkalmazásba akár 1 órát is igénybe vehet.</span><span class="sxs-lookup"><span data-stu-id="c4598-112">Exporting up to 1 million profiles to Constant Contact can take up to 1 hour to complete.</span></span> 
- <span data-ttu-id="c4598-113">Az Constant Contactba exportálható profilok száma az Constant Contacttal kötött szerződéstől függ és az korlátozza.</span><span class="sxs-lookup"><span data-stu-id="c4598-113">The number of profiles that you can export to Constant Contact is dependent and limited on your contract with Constant Contact.</span></span>

## <a name="set-up-connection-to-constant-contact"></a><span data-ttu-id="c4598-114">Kapcsolat beállítása Constant Contacthoz</span><span class="sxs-lookup"><span data-stu-id="c4598-114">Set up connection to Constant Contact</span></span>

1. <span data-ttu-id="c4598-115">Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="c4598-115">Go to **Admin** > **Connections**.</span></span>

1. <span data-ttu-id="c4598-116">Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza az **Constant Contact** lehetőséget a kapcsolat konfigurálásához.</span><span class="sxs-lookup"><span data-stu-id="c4598-116">Select **Add connection** and choose **Constant Contact** to configure the connection.</span></span>

1. <span data-ttu-id="c4598-117">Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak.</span><span class="sxs-lookup"><span data-stu-id="c4598-117">Give your connection a recognizable name in the **Display name** field.</span></span> <span data-ttu-id="c4598-118">A név és a kapcsolat típusa írja le ezt a kapcsolatot.</span><span class="sxs-lookup"><span data-stu-id="c4598-118">The name and the type of the connection describe this connection.</span></span> <span data-ttu-id="c4598-119">Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.</span><span class="sxs-lookup"><span data-stu-id="c4598-119">We recommend choosing a name that explains the purpose and target of the connection.</span></span>

1. <span data-ttu-id="c4598-120">A kapcsolat használóinak kiválasztása.</span><span class="sxs-lookup"><span data-stu-id="c4598-120">Choose who can use this connection.</span></span> <span data-ttu-id="c4598-121">Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz.</span><span class="sxs-lookup"><span data-stu-id="c4598-121">If you take no action, the default will be Administrators.</span></span> <span data-ttu-id="c4598-122">További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).</span><span class="sxs-lookup"><span data-stu-id="c4598-122">For more information, see [Allow contributors to use a connection for exports](connections.md#allow-contributors-to-use-a-connection-for-exports).</span></span>

1. <span data-ttu-id="c4598-123">Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.</span><span class="sxs-lookup"><span data-stu-id="c4598-123">Select **I agree** to confirm the **Data privacy and compliance**.</span></span>

1. <span data-ttu-id="c4598-124">Válassza a **Kapcsolat** lehetőséget az Constant Contact kapcsolatának inicializálására.</span><span class="sxs-lookup"><span data-stu-id="c4598-124">Select **Connect** to initialize the connection to Constant Contact.</span></span>

1. <span data-ttu-id="c4598-125">Válassza a **Hitelesítés az AdRollal** lehetőséget, és adja meg az Constant Contact rendszergazdai hitelesítő adatait.</span><span class="sxs-lookup"><span data-stu-id="c4598-125">Select **Authenticate with AdRoll** and provide your admin credentials for Constant Contact.</span></span> 

1. <span data-ttu-id="c4598-126">Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.</span><span class="sxs-lookup"><span data-stu-id="c4598-126">Select **Add yourself as export user** and provide your Customer Insights credentials.</span></span>

1. <span data-ttu-id="c4598-127">A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="c4598-127">Select **Save** to complete the connection.</span></span>

## <a name="configure-an-export"></a><span data-ttu-id="c4598-128">Exportálás konfigurálása</span><span class="sxs-lookup"><span data-stu-id="c4598-128">Configure an export</span></span>

<span data-ttu-id="c4598-129">Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz.</span><span class="sxs-lookup"><span data-stu-id="c4598-129">You can configure this export if you have access to a connection of this type.</span></span> <span data-ttu-id="c4598-130">További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).</span><span class="sxs-lookup"><span data-stu-id="c4598-130">For more information, see [Permissions needed to configure an export](export-destinations.md#set-up-a-new-export).</span></span>

1. <span data-ttu-id="c4598-131">Menjen az **Adatok** > **Exportálások** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="c4598-131">Go to **Data** > **Exports**.</span></span>

1. <span data-ttu-id="c4598-132">Új exportálás létrehozásához válassza a **Célhely hozzáadása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="c4598-132">To create a new export, select **Add destination**.</span></span>

1. <span data-ttu-id="c4598-133">A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot az Constant Contact szakaszból.</span><span class="sxs-lookup"><span data-stu-id="c4598-133">In the **Connection for export** field, choose a connection from the Constant Contact section.</span></span> <span data-ttu-id="c4598-134">Ha nem látja ezt a szakasznevet, az Ön számára nincs ilyen típusú kapcsolat.</span><span class="sxs-lookup"><span data-stu-id="c4598-134">If you don't see this section name, there are no connections of this type available to you.</span></span>

1. <span data-ttu-id="c4598-135">Adja meg az [**Constant Contact listájának azonosítóját**](https://app.constantcontact.com/pages/contacts/ui#lists).</span><span class="sxs-lookup"><span data-stu-id="c4598-135">Enter your [**Constant Contact List ID**](https://app.constantcontact.com/pages/contacts/ui#lists).</span></span> <span data-ttu-id="c4598-136">Nyisson meg egy listát az Constant Contactban, és keresse meg a lista azonosítóját az URL-címben.</span><span class="sxs-lookup"><span data-stu-id="c4598-136">Open a list in Constant Contact to find the list ID in the URL.</span></span>

1. <span data-ttu-id="c4598-137">Az **Adategyeztetés** szakaszban az **E-mail** mezőben jelölje ki az egyesített ügyfélprofil ügyfél e-mail-címét jelképező mezőjét.</span><span class="sxs-lookup"><span data-stu-id="c4598-137">In the **Data matching** section, in the **Email** field, select the field in your unified customer profile that represents a customer's email address.</span></span> <span data-ttu-id="c4598-138">A szegmenseket exportálni kell az Constant Contact alkalmazásba.</span><span class="sxs-lookup"><span data-stu-id="c4598-138">It's required to export segments to Constant Contact.</span></span>

1. <span data-ttu-id="c4598-139">Alternatív lehetőségként exportálhatja az Utónév és Vezetéknév mezőket további mezőként személyre szabottabb e-mailek létrehozásához.</span><span class="sxs-lookup"><span data-stu-id="c4598-139">Optionally, you can export First name and Last name as additional fields to create more personalized emails.</span></span> <span data-ttu-id="c4598-140">Válassza az **Attribútum hozzáadása** lehetőséget a mezők leképezéséhez.</span><span class="sxs-lookup"><span data-stu-id="c4598-140">Select **Add attribute** to map these fields.</span></span>

1. <span data-ttu-id="c4598-141">Jelölje ki a szegmenseket, amelyeket exportálni szeretne.</span><span class="sxs-lookup"><span data-stu-id="c4598-141">Select the segments you want to export.</span></span>

1. <span data-ttu-id="c4598-142">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="c4598-142">Select **Save**.</span></span>

<span data-ttu-id="c4598-143">Az exportálás mentése nem futtatja azonnal az exportálást.</span><span class="sxs-lookup"><span data-stu-id="c4598-143">Saving an export doesn't run the export immediately.</span></span>

<span data-ttu-id="c4598-144">Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut.</span><span class="sxs-lookup"><span data-stu-id="c4598-144">The export runs with every [scheduled refresh](system.md#schedule-tab).</span></span> <span data-ttu-id="c4598-145">Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand).</span><span class="sxs-lookup"><span data-stu-id="c4598-145">You can also [export data on demand](export-destinations.md#run-exports-on-demand).</span></span> 


## <a name="data-privacy-and-compliance"></a><span data-ttu-id="c4598-146">Adatvédelem és megfelelőség</span><span class="sxs-lookup"><span data-stu-id="c4598-146">Data privacy and compliance</span></span>

<span data-ttu-id="c4598-147">Amikor engedélyezi Dynamics 365 Customer Insightst, hogy adatokat továbbítson az Constant Contactnak, akkor lehetővé teszi az adatok továbbítását a Dynamics 365 Customer Insights megfelelési határán kívülre is, beleértve az esetlegesen bizalmas adatokat is, például a Személyes adatokat.</span><span class="sxs-lookup"><span data-stu-id="c4598-147">When you enable Dynamics 365 Customer Insights to transmit data to Constant Contact, you allow transfer of data outside of the compliance boundary for Dynamics 365 Customer Insights, including potentially sensitive data such as Personal Data.</span></span> <span data-ttu-id="c4598-148">A Microsoft az Ön utasítására továbbítja az adatokat, de Ön a felelős azért, hogy az Constant Contact megfeleljen az esetleges adatvédelmi vagy biztonsági kötelezettségeknek.</span><span class="sxs-lookup"><span data-stu-id="c4598-148">Microsoft will transfer such data at your instruction, but you are responsible for ensuring that Constant Contact meets any privacy or security obligations you may have.</span></span> <span data-ttu-id="c4598-149">További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).</span><span class="sxs-lookup"><span data-stu-id="c4598-149">For more information, see [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?linkid=396732).</span></span>

<span data-ttu-id="c4598-150">A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.</span><span class="sxs-lookup"><span data-stu-id="c4598-150">Your Dynamics 365 Customer Insights Administrator can remove this export destination at any time to discontinue use of this functionality.</span></span>
