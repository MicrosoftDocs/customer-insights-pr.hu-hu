---
title: Customer Insights adatok exportálása Sendinblue-ba
description: További információ a kapcsolat konfigurálásához és az Sendinblue-ba való exportáláshoz.
ms.date: 06/29/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: phkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 58ca0ae5ad4a3a291f4336984d14fefb23a58ab3
ms.sourcegitcommit: 057079532e31c12bac36f374857ba3dc847d6ad0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/29/2021
ms.locfileid: "6314625"
---
# <a name="export-segments-to-sendinblue-preview"></a><span data-ttu-id="3f077-103">Szegmensek exportálása Sendinblue-ba (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="3f077-103">Export segments to Sendinblue (preview)</span></span>

<span data-ttu-id="3f077-104">Az egyesített ügyfélprofilok szegmenseinek exportálása kampányok létrehozásához, e-mail-marketing szolgáltatást biztosíthat és az ügyfelek meghatározott csoportját használhatja a Sendinblue szolgáltatással.</span><span class="sxs-lookup"><span data-stu-id="3f077-104">Export segments of unified customer profiles to generate campaigns, provide email marketing and use specific groups of customers with Sendinblue.</span></span>

## <a name="prerequisites-for-connection"></a><span data-ttu-id="3f077-105">A kapcsolat előfeltételei</span><span class="sxs-lookup"><span data-stu-id="3f077-105">Prerequisites for connection</span></span>

-   <span data-ttu-id="3f077-106">[Sendinblue fiókkal](https://www.sendinblue.com/) és a megfelelő rendszergazdai hitelesítő adatokkal rendelkezik.</span><span class="sxs-lookup"><span data-stu-id="3f077-106">You have a [Sendinblue account](https://www.sendinblue.com/) and corresponding administrator credentials.</span></span>
-   <span data-ttu-id="3f077-107">A Sendinblue-ban és a megfelelő azonosítókban vannak meglévő listák.</span><span class="sxs-lookup"><span data-stu-id="3f077-107">There are existing lists in Sendinblue and the corresponding IDs.</span></span>
-   <span data-ttu-id="3f077-108">Rendelkezik [konfigurált szegmensekkel](segments.md).</span><span class="sxs-lookup"><span data-stu-id="3f077-108">You have [configured segments](segments.md).</span></span>
-   <span data-ttu-id="3f077-109">Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.</span><span class="sxs-lookup"><span data-stu-id="3f077-109">Unified customer profiles in the exported segments contain a field representing an email address.</span></span>

## <a name="known-limitations"></a><span data-ttu-id="3f077-110">Ismert korlátozások</span><span class="sxs-lookup"><span data-stu-id="3f077-110">Known limitations</span></span>

- <span data-ttu-id="3f077-111">A Sendinblue-nak küldhető exportonként legfeljebb 1 millió profil.</span><span class="sxs-lookup"><span data-stu-id="3f077-111">Up to 1 million profiles per export to Sendinblue.</span></span>
- <span data-ttu-id="3f077-112">Az Sendinblue-ba történő exportálás szegmensekre korlátozódik.</span><span class="sxs-lookup"><span data-stu-id="3f077-112">Exporting to Sendinblue is limited to segments.</span></span>
- <span data-ttu-id="3f077-113">Az összesen 1 millió profillal rendelkező szegmensek exportálása akár 90 percet is igénybe vehet.</span><span class="sxs-lookup"><span data-stu-id="3f077-113">Exporting segments with a total of 1 million profiles can take up to 90 minutes.</span></span> 
- <span data-ttu-id="3f077-114">Az Sendinblue-ba exportálható profilok száma a Sendinblue-val kötött szerződésétől függ.</span><span class="sxs-lookup"><span data-stu-id="3f077-114">The number of profiles that you can export to Sendinblue is dependent and limited on your contract with Sendinblue.</span></span>

## <a name="set-up-connection-to-sendinblue"></a><span data-ttu-id="3f077-115">Sendinblue-val való kapcsolat beállítása</span><span class="sxs-lookup"><span data-stu-id="3f077-115">Set up connection to Sendinblue</span></span>

1. <span data-ttu-id="3f077-116">Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="3f077-116">Go to **Admin** > **Connections**.</span></span>

1. <span data-ttu-id="3f077-117">Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza az **Sendinblue** lehetőséget a kapcsolat konfigurálásához.</span><span class="sxs-lookup"><span data-stu-id="3f077-117">Select **Add connection** and choose **Sendinblue** to configure the connection.</span></span>

1. <span data-ttu-id="3f077-118">Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak.</span><span class="sxs-lookup"><span data-stu-id="3f077-118">Give your connection a recognizable name in the **Display name** field.</span></span> <span data-ttu-id="3f077-119">A név és a kapcsolat típusa írja le ezt a kapcsolatot.</span><span class="sxs-lookup"><span data-stu-id="3f077-119">The name and the type of the connection describe this connection.</span></span> <span data-ttu-id="3f077-120">Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.</span><span class="sxs-lookup"><span data-stu-id="3f077-120">We recommend choosing a name that explains the purpose and target of the connection.</span></span>

1. <span data-ttu-id="3f077-121">A kapcsolat használóinak kiválasztása.</span><span class="sxs-lookup"><span data-stu-id="3f077-121">Choose who can use this connection.</span></span> <span data-ttu-id="3f077-122">Alapértelmezés szerint csak a rendszergazdák.</span><span class="sxs-lookup"><span data-stu-id="3f077-122">By default it's only administrators.</span></span> <span data-ttu-id="3f077-123">További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).</span><span class="sxs-lookup"><span data-stu-id="3f077-123">For more information, see [Allow contributors to use a connection for exports](connections.md#allow-contributors-to-use-a-connection-for-exports).</span></span>

1. <span data-ttu-id="3f077-124">Adja meg **[SendinBlue API-kulcsát](https://developers.sendinblue.com/docs/getting-started#:~:text=Get%20your%20API%20key&text=You%20can%20create%20one%20from,your%20settings%20This%20API%20key)**.</span><span class="sxs-lookup"><span data-stu-id="3f077-124">Enter your **[SendinBlue API key](https://developers.sendinblue.com/docs/getting-started#:~:text=Get%20your%20API%20key&text=You%20can%20create%20one%20from,your%20settings%20This%20API%20key)**.</span></span>

1. <span data-ttu-id="3f077-125">Válassza az **Elfogadom** lehetőséget, hogy megerősítse az **Adatvédelem és megfelelőség** opciót, és válassza a **Csatlakozás** lehetőséget, hogy inicializálja a kapcsolatot Sendinblue-val.</span><span class="sxs-lookup"><span data-stu-id="3f077-125">Select **I agree** to confirm the **Data privacy and compliance** and select **Connect** to initialize the connection to Sendinblue.</span></span>

1. <span data-ttu-id="3f077-126">Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.</span><span class="sxs-lookup"><span data-stu-id="3f077-126">Select **Add yourself as export user** and provide your Customer Insights credentials.</span></span>

1. <span data-ttu-id="3f077-127">A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="3f077-127">Select **Save** to complete the connection.</span></span>

## <a name="configure-an-export"></a><span data-ttu-id="3f077-128">Exportálás konfigurálása</span><span class="sxs-lookup"><span data-stu-id="3f077-128">Configure an export</span></span>

<span data-ttu-id="3f077-129">Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz.</span><span class="sxs-lookup"><span data-stu-id="3f077-129">You can configure this export if you have access to a connection of this type.</span></span> <span data-ttu-id="3f077-130">További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).</span><span class="sxs-lookup"><span data-stu-id="3f077-130">For more information, see [Permissions needed to configure an export](export-destinations.md#set-up-a-new-export).</span></span>

1. <span data-ttu-id="3f077-131">Menjen az **Adatok** > **Exportálások** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="3f077-131">Go to **Data** > **Exports**.</span></span>

1. <span data-ttu-id="3f077-132">Új exportálás létrehozásához válassza a **Célhely hozzáadása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="3f077-132">To create a new export, select **Add destination**.</span></span>

1. <span data-ttu-id="3f077-133">Az **Exportálási kapcsolat** mezőben válasszon kapcsolatot a Sendinblue szakaszból.</span><span class="sxs-lookup"><span data-stu-id="3f077-133">In the **Connection for export** field, choose a connection from the Sendinblue section.</span></span> <span data-ttu-id="3f077-134">Ha nem látja ezt a szakasznevet, az Ön számára nincs ilyen típusú kapcsolat.</span><span class="sxs-lookup"><span data-stu-id="3f077-134">If you don't see this section name, there are no connections of this type available to you.</span></span>

1. <span data-ttu-id="3f077-135">Adja meg **Sendinblue listaazonosítóját**</span><span class="sxs-lookup"><span data-stu-id="3f077-135">Enter your **Sendinblue list ID**</span></span> 

1. <span data-ttu-id="3f077-136">Az **Adategyeztetés** szakaszban az **E-mail** mezőben jelölje ki az egyesített ügyfélprofil ügyfél e-mail-címét jelképező mezőjét.</span><span class="sxs-lookup"><span data-stu-id="3f077-136">In the **Data matching** section, in the **Email** field, select the field in your unified customer profile that represents a customer's email address.</span></span> 

1. <span data-ttu-id="3f077-137">Opcionálisan exportálhat **utónév**, **vezetéknév**, és **telefon**-ra,hogy személyre szabottabb e-maileket hozzon létre.</span><span class="sxs-lookup"><span data-stu-id="3f077-137">Optionally, you can export **First name**, **Last name**, and **Phone**  to create more personalized emails.</span></span> <span data-ttu-id="3f077-138">Válassza az **Attribútum hozzáadása** lehetőséget a mezők leképezéséhez.</span><span class="sxs-lookup"><span data-stu-id="3f077-138">Select **Add attribute** to map these fields.</span></span>

1. <span data-ttu-id="3f077-139">Jelölje ki a szegmenseket, amelyeket exportálni szeretne.</span><span class="sxs-lookup"><span data-stu-id="3f077-139">Select the segments you want to export.</span></span> 

1. <span data-ttu-id="3f077-140">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="3f077-140">Select **Save**.</span></span>

<span data-ttu-id="3f077-141">Az exportálás mentése nem futtatja azonnal az exportálást.</span><span class="sxs-lookup"><span data-stu-id="3f077-141">Saving an export doesn't run the export immediately.</span></span>

<span data-ttu-id="3f077-142">Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut.</span><span class="sxs-lookup"><span data-stu-id="3f077-142">The export runs with every [scheduled refresh](system.md#schedule-tab).</span></span> <span data-ttu-id="3f077-143">Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand).</span><span class="sxs-lookup"><span data-stu-id="3f077-143">You can also [export data on demand](export-destinations.md#run-exports-on-demand).</span></span> 


## <a name="data-privacy-and-compliance"></a><span data-ttu-id="3f077-144">Adatvédelem és megfelelőség</span><span class="sxs-lookup"><span data-stu-id="3f077-144">Data privacy and compliance</span></span>

<span data-ttu-id="3f077-145">Amikor engedélyezi a Dynamics 365 Customer Insights -nak, hogy továbbítsa az adatokat Sendinblue-ba, engedélyezi az adatátvitelt a megfelelőséghatáron kívülre a Dynamics 365 Customer Insights -nak, beleértve az esetlegesen bizalmas adatokat, például személyes adatokat.</span><span class="sxs-lookup"><span data-stu-id="3f077-145">When you enable Dynamics 365 Customer Insights to transmit data to Sendinblue, you allow transfer of data outside of the compliance boundary for Dynamics 365 Customer Insights, including potentially sensitive data such as Personal Data.</span></span> <span data-ttu-id="3f077-146">A Microsoft az Ön utasítására továbbítja az ilyen adatokat, de Ön felelős annak biztosításáért, hogy a Sendinblue megfeleljen az esetleges adatvédelmi és biztonsági kötelezettségeknek.</span><span class="sxs-lookup"><span data-stu-id="3f077-146">Microsoft will transfer such data at your instruction, but you are responsible for ensuring that Sendinblue meets any privacy or security obligations you may have.</span></span> <span data-ttu-id="3f077-147">További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).</span><span class="sxs-lookup"><span data-stu-id="3f077-147">For more information, see [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?linkid=396732).</span></span>
<span data-ttu-id="3f077-148">A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.</span><span class="sxs-lookup"><span data-stu-id="3f077-148">Your Dynamics 365 Customer Insights administrator can remove this export destination at any time to discontinue use of this functionality.</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]
