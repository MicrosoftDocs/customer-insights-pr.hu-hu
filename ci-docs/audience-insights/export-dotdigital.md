---
title: Customer Insights adatok exportálása a DotDigitalbe
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a DotDigitalba.
ms.date: 03/03/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: d08504856e1c673ef32433b83bf491d7f4e8cee4
ms.sourcegitcommit: e8e03309ba2515374a70c132d0758f3e1e1851d0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/04/2021
ms.locfileid: "5976849"
---
# <a name="export-segment-lists-to-dotdigital-preview"></a><span data-ttu-id="20ac7-103">Szegmenslisták exportálása a DotDigitalba (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="20ac7-103">Export segment lists to DotDigital (preview)</span></span>

<span data-ttu-id="20ac7-104">Az egyesített ügyfélprofilok szegmenseit exportálhatja a DotDigital címjegyzékekbe, és használhatja őet kampányokhoz, e-mail-marketinghez és ügyfélszegmensek létrehozásához a DotDigitallal.</span><span class="sxs-lookup"><span data-stu-id="20ac7-104">Export segments of unified customer profiles to DotDigital address books and use them for campaigns, email marketing, and to build customer segments with DotDigital.</span></span> 

## <a name="prerequisites-for-a-connection"></a><span data-ttu-id="20ac7-105">Egy kapcsolat előfeltételei</span><span class="sxs-lookup"><span data-stu-id="20ac7-105">Prerequisites for a connection</span></span>

-   <span data-ttu-id="20ac7-106">Rendelkezik [DotDigital-fiókkal](https://dotdigital.com/) és a megfelelő rendszergazdai hitelesítő adatokkal.</span><span class="sxs-lookup"><span data-stu-id="20ac7-106">You have a [DotDigital account](https://dotdigital.com/) and corresponding administrator credentials.</span></span>
-   <span data-ttu-id="20ac7-107">A DotDigitalban és a megfelelő azonosítókban meglévő címjegyzékek találhatók.</span><span class="sxs-lookup"><span data-stu-id="20ac7-107">There are existing address books in DotDigital and the corresponding IDs.</span></span> <span data-ttu-id="20ac7-108">Az azonosító megtalálhatók az URL-címben, amikor kijelöli és megnyitja a címjegyzéket.</span><span class="sxs-lookup"><span data-stu-id="20ac7-108">The ID can be found in the URL when you select and open an address book.</span></span> <span data-ttu-id="20ac7-109">További információért lásd: [DotDigital címjegyzékek](https://support.dotdigital.com/hc/articles/212211968-Creating-an-address-book).</span><span class="sxs-lookup"><span data-stu-id="20ac7-109">For more information, see [DotDigital address books](https://support.dotdigital.com/hc/articles/212211968-Creating-an-address-book).</span></span>
-   <span data-ttu-id="20ac7-110">[Konfigurált szegmensekkel](segments.md) rendelkezik a célközönségi-információkban.</span><span class="sxs-lookup"><span data-stu-id="20ac7-110">You have [configured segments](segments.md) in audience insights.</span></span>
-   <span data-ttu-id="20ac7-111">Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.</span><span class="sxs-lookup"><span data-stu-id="20ac7-111">Unified customer profiles in the exported segments contain a field representing an email address.</span></span>

## <a name="known-limitations"></a><span data-ttu-id="20ac7-112">Ismert korlátozások</span><span class="sxs-lookup"><span data-stu-id="20ac7-112">Known limitations</span></span>

- <span data-ttu-id="20ac7-113">Legfeljebb 1 000 000 profilt exportálhat egyszerre a DotDigitalba.</span><span class="sxs-lookup"><span data-stu-id="20ac7-113">Up to 1 million profiles per export to DotDigital.</span></span>
- <span data-ttu-id="20ac7-114">A DotDigitalba való exportálás csak szegmensekre korlátozódik.</span><span class="sxs-lookup"><span data-stu-id="20ac7-114">Exporting to DotDigital is limited to segments.</span></span>
- <span data-ttu-id="20ac7-115">Az összesen 1 000 000 profillal rendelkező szegmens exportálása a szolgáltatói oldalon megjelenő korlátozások miatt akár 3 óráig is eltarthat.</span><span class="sxs-lookup"><span data-stu-id="20ac7-115">Exporting segments with a total of 1 million profiles can take up to 3 hours because of limitations on the provider side.</span></span> 
- <span data-ttu-id="20ac7-116">A DotDigitalba exportálható profilok száma függ a DotDigital szerződésről, és korlátozott.</span><span class="sxs-lookup"><span data-stu-id="20ac7-116">The number of profiles that you can export to DotDigital is dependent and limited on your contract with DotDigital.</span></span>

## <a name="set-up-connection-to-dotdigital"></a><span data-ttu-id="20ac7-117">Állítsa be a DotDigitallal való kapcsolatot</span><span class="sxs-lookup"><span data-stu-id="20ac7-117">Set up connection to DotDigital</span></span>

1. <span data-ttu-id="20ac7-118">Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="20ac7-118">Go to **Admin** > **Connections**.</span></span>

1. <span data-ttu-id="20ac7-119">Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza a **DotDigital** lehetőséget a kapcsolat konfigurálásához.</span><span class="sxs-lookup"><span data-stu-id="20ac7-119">Select **Add connection** and choose **DotDigital** to configure the connection.</span></span>

1. <span data-ttu-id="20ac7-120">Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak.</span><span class="sxs-lookup"><span data-stu-id="20ac7-120">Give your connection a recognizable name in the **Display name** field.</span></span> <span data-ttu-id="20ac7-121">A név és a kapcsolat típusa írja le ezt a kapcsolatot.</span><span class="sxs-lookup"><span data-stu-id="20ac7-121">The name and the type of the connection describe this connection.</span></span> <span data-ttu-id="20ac7-122">Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.</span><span class="sxs-lookup"><span data-stu-id="20ac7-122">We recommend choosing a name that explains the purpose and target of the connection.</span></span>

1. <span data-ttu-id="20ac7-123">A kapcsolat használóinak kiválasztása.</span><span class="sxs-lookup"><span data-stu-id="20ac7-123">Choose who can use this connection.</span></span> <span data-ttu-id="20ac7-124">Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz.</span><span class="sxs-lookup"><span data-stu-id="20ac7-124">If you take no action, the default will be Administrators.</span></span> <span data-ttu-id="20ac7-125">További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).</span><span class="sxs-lookup"><span data-stu-id="20ac7-125">For more information, see [Allow contributors to use a connection for exports](connections.md#allow-contributors-to-use-a-connection-for-exports).</span></span>

1. <span data-ttu-id="20ac7-126">Adja meg a **DotDigital felhasználói nevét és a jelszavát**.</span><span class="sxs-lookup"><span data-stu-id="20ac7-126">Enter your **DotDigital username and password**.</span></span>

1. <span data-ttu-id="20ac7-127">Adja meg a **[DotDigital címjegyzék-azonosítóját](https://support.dotdigital.com/hc/articles/212211968-Creating-an-address-book)**.</span><span class="sxs-lookup"><span data-stu-id="20ac7-127">Enter your **[DotDigital address book ID](https://support.dotdigital.com/hc/articles/212211968-Creating-an-address-book)**.</span></span>

1. <span data-ttu-id="20ac7-128">Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.</span><span class="sxs-lookup"><span data-stu-id="20ac7-128">Select **I agree** to confirm the **Data privacy and compliance**.</span></span>

1. <span data-ttu-id="20ac7-129">Válassza a **Csatlakozás** lehetőséget a DotDigital kapcsolat inicializálásához.</span><span class="sxs-lookup"><span data-stu-id="20ac7-129">Select **Connect** to initialize the connection to DotDigital.</span></span>

1. <span data-ttu-id="20ac7-130">Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.</span><span class="sxs-lookup"><span data-stu-id="20ac7-130">Select **Add yourself as export user** and provide your Customer Insights credentials.</span></span>

1. <span data-ttu-id="20ac7-131">A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="20ac7-131">Select **Save** to complete the connection.</span></span> 

## <a name="configure-an-export"></a><span data-ttu-id="20ac7-132">Exportálás konfigurálása</span><span class="sxs-lookup"><span data-stu-id="20ac7-132">Configure an export</span></span>

<span data-ttu-id="20ac7-133">Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz.</span><span class="sxs-lookup"><span data-stu-id="20ac7-133">You can configure this export if you have access to a connection of this type.</span></span> <span data-ttu-id="20ac7-134">További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).</span><span class="sxs-lookup"><span data-stu-id="20ac7-134">For more information, see [Permissions needed to configure an export](export-destinations.md#set-up-a-new-export).</span></span>

1. <span data-ttu-id="20ac7-135">Menjen az **Adatok** > **Exportálások** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="20ac7-135">Go to **Data** > **Exports**.</span></span>

1. <span data-ttu-id="20ac7-136">Új exportálás létrehozásához válassza a **Célhely hozzáadása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="20ac7-136">To create a new export, select **Add destination**.</span></span>

1. <span data-ttu-id="20ac7-137">A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot a DotDigital szakaszból.</span><span class="sxs-lookup"><span data-stu-id="20ac7-137">In the **Connection for export** field, choose a connection from the DotDigital section.</span></span> <span data-ttu-id="20ac7-138">Ha nem látja ezt a szakasznevet, az Ön számára nincs ilyen típusú kapcsolat.</span><span class="sxs-lookup"><span data-stu-id="20ac7-138">If you don't see this section name, there are no connections of this type available to you.</span></span>


1. <span data-ttu-id="20ac7-139">Az **Adategyeztetés** szakaszban az **E-mail** mezőben jelölje ki az egyesített ügyfélprofil ügyfél e-mail-címét jelképező mezőjét.</span><span class="sxs-lookup"><span data-stu-id="20ac7-139">In the **Data matching** section, in the **Email** field, select the field in your unified customer profile that represents a customer's email address.</span></span> <span data-ttu-id="20ac7-140">Ismételje meg ugyanezeket a lépéseket az egyéb választható mezőkön, például az **Utónév**, a **Vezetéknév** , a **Teljes név**, a **Nem** és az **Irányítószám** mezőben.</span><span class="sxs-lookup"><span data-stu-id="20ac7-140">Repeat the same steps for other optional fields such as **First name**, **Last name**, **Full name**, **Gender**, and **Post code**.</span></span>

1. <span data-ttu-id="20ac7-141">Jelölje ki a szegmenseket, amelyeket exportálni szeretne.</span><span class="sxs-lookup"><span data-stu-id="20ac7-141">Select the segments you want to export.</span></span> <span data-ttu-id="20ac7-142">Összesen legfeljebb 1 000 000 ügyfélprofilt exportálhat a DotDigitalba.</span><span class="sxs-lookup"><span data-stu-id="20ac7-142">You can export up to 1 million customer profiles in total to DotDigital.</span></span>

1. <span data-ttu-id="20ac7-143">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="20ac7-143">Select **Save**.</span></span>

<span data-ttu-id="20ac7-144">Az exportálás mentése nem futtatja azonnal az exportálást.</span><span class="sxs-lookup"><span data-stu-id="20ac7-144">Saving an export doesn't run the export immediately.</span></span>

<span data-ttu-id="20ac7-145">Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut.</span><span class="sxs-lookup"><span data-stu-id="20ac7-145">The export runs with every [scheduled refresh](system.md#schedule-tab).</span></span> <span data-ttu-id="20ac7-146">Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand).</span><span class="sxs-lookup"><span data-stu-id="20ac7-146">You can also [export data on demand](export-destinations.md#run-exports-on-demand).</span></span> 
 
<span data-ttu-id="20ac7-147">A DotDigitalban most már megtalálhatja a szegmenseket a [DotDigital címjegyzékekben](https://support.dotdigital.com/hc/articles/212211968-Creating-an-address-book).</span><span class="sxs-lookup"><span data-stu-id="20ac7-147">In DotDigital, you can now find your segments in [DotDigital address books](https://support.dotdigital.com/hc/articles/212211968-Creating-an-address-book).</span></span>


## <a name="data-privacy-and-compliance"></a><span data-ttu-id="20ac7-148">Adatvédelem és megfelelőség</span><span class="sxs-lookup"><span data-stu-id="20ac7-148">Data privacy and compliance</span></span>

<span data-ttu-id="20ac7-149">Amikor engedélyezi a Dynamics 365 Customer Insights szolgáltatást az adatok DotDigital szolgáltatásba való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat.</span><span class="sxs-lookup"><span data-stu-id="20ac7-149">When you enable Dynamics 365 Customer Insights to transmit data to DotDigital, you allow transfer of data outside of the compliance boundary for Dynamics 365 Customer Insights, including potentially sensitive data such as Personal Data.</span></span> <span data-ttu-id="20ac7-150">A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy a DotDigital megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek.</span><span class="sxs-lookup"><span data-stu-id="20ac7-150">Microsoft will transfer such data at your instruction, but you are responsible for ensuring that DotDigital meet any privacy or security obligations you may have.</span></span> <span data-ttu-id="20ac7-151">További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).</span><span class="sxs-lookup"><span data-stu-id="20ac7-151">For more information, see [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?linkid=396732).</span></span>
<span data-ttu-id="20ac7-152">A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.</span><span class="sxs-lookup"><span data-stu-id="20ac7-152">Your Dynamics 365 Customer Insights Administrator can remove this export destination at any time to discontinue use of this functionality.</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]
