---
title: 'Bővítés külső bővítéssel: HERE Technologies'
description: Általános információk a HERE Technologies harmadik fél bővítésről.
ms.date: 04/09/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: jodahlMSFT
ms.author: jodahl
manager: shellyha
ms.openlocfilehash: 5d1f037377010153045c9255d2d01f98ebf1fdfd
ms.sourcegitcommit: aaa275c60c0c77c88196277b266a91d653f8f759
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/14/2021
ms.locfileid: "5896054"
---
# <a name="enrichment-of-customer-profiles-with-here-technologies-preview"></a><span data-ttu-id="4662a-103">Ügyfélprofilok bővítése a HERE Technologies (előzetes verzió) segítségével</span><span class="sxs-lookup"><span data-stu-id="4662a-103">Enrichment of customer profiles with HERE Technologies (preview)</span></span>

<span data-ttu-id="4662a-104">A HERE Technologies egy helyplatformot biztosító vállalat, amely helyalapú adatokat és szolgáltatásokat nyújt.</span><span class="sxs-lookup"><span data-stu-id="4662a-104">HERE Technologies is a location platform company that provides location-centric data and services.</span></span> <span data-ttu-id="4662a-105">A HERE Technologies adatbővítési szolgáltatásaival pontosabb helyértelmezést hozhat létre az ügyfelekről a cím normalizálásával, földrajzi hosszúság és szélesség kinyerésével stb.</span><span class="sxs-lookup"><span data-stu-id="4662a-105">With HERE Technologies' data enrichment services, you can build a more precise location understanding of your customers with address normalization, latitude and longitude extraction, and more.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4662a-106">Előfeltételek</span><span class="sxs-lookup"><span data-stu-id="4662a-106">Prerequisites</span></span>

<span data-ttu-id="4662a-107">A HERE Technologies bővítések konfigurálásához a következő előfeltételeknek kell teljesülnie:</span><span class="sxs-lookup"><span data-stu-id="4662a-107">To configure HERE Technologies enrichments, the following prerequisites must be met:</span></span>

- <span data-ttu-id="4662a-108">Aktív HERE Technologies előfizetéssel kell rendelkeznie.</span><span class="sxs-lookup"><span data-stu-id="4662a-108">You have an active HERE Technologies subscription.</span></span> <span data-ttu-id="4662a-109">Az előfizetés beszerzéséhez [regisztrálhat itt](https://developer.here.com/sign-up?utm_medium=referral&utm_source=Microsoft-Dynamics-CI&create=Freemium-Basic) vagy [felveheti a HERE Technologiesszel a kapcsolatot](https://developer.here.com/help?utm_medium=referral&utm_source=Microsoft-Dynamics-CI#how-can-we-help-you) közvetlenül.</span><span class="sxs-lookup"><span data-stu-id="4662a-109">To get a subscription, you can [sign-up here](https://developer.here.com/sign-up?utm_medium=referral&utm_source=Microsoft-Dynamics-CI&create=Freemium-Basic) or [contact HERE Technologies](https://developer.here.com/help?utm_medium=referral&utm_source=Microsoft-Dynamics-CI#how-can-we-help-you) directly.</span></span> [<span data-ttu-id="4662a-110">Itt többet is megtudhat a HERE Technologies helybővítéshez.</span><span class="sxs-lookup"><span data-stu-id="4662a-110">Learn more about HERE Technologies Location Enrichment.</span></span>](https://developer.here.com/location-enrichment?cid=Dev-MicrosoftDynamics-DB-0-Dev-&utm_source=MicrosoftDynamics&utm_medium=referral&utm_campaign=Online_Dev_ReferralMicrosoft)

- <span data-ttu-id="4662a-111">Egy HERE [kapcsolat](connections.md) áll rendelkezésre *vagy* Ön [rendszergazdai](permissions.md#administrator) engedélyekkel és a HERE Technologies API-kulcssal rendelkezik.</span><span class="sxs-lookup"><span data-stu-id="4662a-111">There is a HERE [connection](connections.md) available *or* you have [administrator](permissions.md#administrator) permissions and the HERE Technologies API key.</span></span>

## <a name="configure-the-enrichment"></a><span data-ttu-id="4662a-112">Bővítés konfigurálása</span><span class="sxs-lookup"><span data-stu-id="4662a-112">Configure the enrichment</span></span>

1. <span data-ttu-id="4662a-113">Lépjen az **Adatok** > **Bővítés** pontra.</span><span class="sxs-lookup"><span data-stu-id="4662a-113">Go to **Data** > **Enrichment**.</span></span> 

1. <span data-ttu-id="4662a-114">Válassza az **Adatok bővítése** lehetőséget a HERE Technologies csempén, majd válassza az **Első lépések** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="4662a-114">Select **Enrich my data** on the HERE Technologies tile and select **Get started**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="4662a-115">![HERE Technologies csempe](media/HERE-tile.png "HERE Technologies csempe")</span><span class="sxs-lookup"><span data-stu-id="4662a-115">![HERE Technologies tile](media/HERE-tile.png "HERE Technologies tile")</span></span>

1. <span data-ttu-id="4662a-116">Válasszon egy [kapcsolatot](connections.md) a legördülő listából.</span><span class="sxs-lookup"><span data-stu-id="4662a-116">Select a [connection](connections.md) from the drop-down.</span></span> <span data-ttu-id="4662a-117">Ha nem érhető el egy kapcsolat sem, akkor forduljon a rendszergazdához.</span><span class="sxs-lookup"><span data-stu-id="4662a-117">Contact  an administrator if no connection is available.</span></span> <span data-ttu-id="4662a-118">Ha Ön rendszergazda, a **Kapcsolat hozzáadása** lehetőség kiválasztásával hozhat létre kapcsolatot.</span><span class="sxs-lookup"><span data-stu-id="4662a-118">If you are an administrator, you can create a connection by selecting **Add connection**.</span></span> <span data-ttu-id="4662a-119">Válassza a legördülő listából a **HERE Technologies** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="4662a-119">Choose **HERE Technologies** from the drop-down.</span></span> 

1. <span data-ttu-id="4662a-120">A kijelölés megerősítéséhez válassza a **Kapcsolódás a HERE Technologies-hez** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="4662a-120">Select **Connect to HERE Technologies** to confirm the selection.</span></span>

1.  <span data-ttu-id="4662a-121">Válassza a **Következő** lehetőséget, és válassza a helyadatokkal bővíteni kívánt **Ügyfél adatkészletet** a HERE Technologies-ből.</span><span class="sxs-lookup"><span data-stu-id="4662a-121">Select **Next** and choose the **Customer data set** you want to enrich with location data from HERE Technologies.</span></span> <span data-ttu-id="4662a-122">Kiválaszthatja a **Vevő** entitást az összes ügyfélprofil gazdagítására, vagy kiválaszthat egy szegmens entitást, amely csak az adott szegmensben található vevőprofilokat gazdagítja.</span><span class="sxs-lookup"><span data-stu-id="4662a-122">You can select the **Customer** entity to enrich all your customer profiles or select a segment entity to enrich only customer profiles contained in that segment.</span></span>

    :::image type="content" source="media/enrichment-HERE-configuration-customer-data-set.png" alt-text="Képernyőkép az ügyféladatkészlet kiválasztásáról.":::

1. <span data-ttu-id="4662a-124">Válassza ki, hogy szeretné-e leképezni a mezőket az elsődleges és/vagy másodlagos címre.</span><span class="sxs-lookup"><span data-stu-id="4662a-124">Choose if you want to map fields to the primary and/or secondary address.</span></span> <span data-ttu-id="4662a-125">Mezőleképezést is megadhat a címekhez, és külön bővítheti a címekhez kapcsolódó profilokat.</span><span class="sxs-lookup"><span data-stu-id="4662a-125">You can specify a field mapping for both addresses and enrich the profiles for both addresses separately.</span></span> <span data-ttu-id="4662a-126">Ez lehet például az otthoni és a munkahelyi cím is.</span><span class="sxs-lookup"><span data-stu-id="4662a-126">For example, if there's a home and a business address.</span></span> <span data-ttu-id="4662a-127">Válassza a **Következő** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="4662a-127">Select **Next**.</span></span>

1. <span data-ttu-id="4662a-128">Adja meg, hogy az egyesített profilokból mely mezők használhatók a megfelelő helyadatok megkereséséhez a HERE Technologiesből.</span><span class="sxs-lookup"><span data-stu-id="4662a-128">Define which fields from your unified profiles should be used to look for matching location data from HERE Technologies.</span></span> <span data-ttu-id="4662a-129">A kiválasztott elsődleges és/vagy másodlagos címhez az **Utca 1.** és az **Irányítószám** mező megadása kötelező.</span><span class="sxs-lookup"><span data-stu-id="4662a-129">The **Street 1** and **Zip/Postal Code** fields are required for the selected primary and/or secondary address.</span></span> <span data-ttu-id="4662a-130">A nagyobb egyeztetési pontosság érdekében további mezők adhatók hozzá.</span><span class="sxs-lookup"><span data-stu-id="4662a-130">For a higher match accuracy, more fields can be added.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="4662a-131">![HERE Technologies bővítés konfigurációs oldal](media/enrichment-HERE-configuration.png "HERE Technologies bővítés konfigurációs oldal")</span><span class="sxs-lookup"><span data-stu-id="4662a-131">![HERE Technologies enrichment configuration page](media/enrichment-HERE-configuration.png "HERE Technologies enrichment configuration page")</span></span>

1. <span data-ttu-id="4662a-132">A mező leképezésének befejezéséhez válassza a **Következő** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="4662a-132">Select **Next** to complete the field mapping.</span></span>

1. <span data-ttu-id="4662a-133">Adjon nevet a bővítésnek.</span><span class="sxs-lookup"><span data-stu-id="4662a-133">Provide a name for the enrichment.</span></span> 

<span data-ttu-id="4662a-134">1. Válassza a **Bővítés mentése** lehetőséget, miután áttekintette a lehetőségeit.</span><span class="sxs-lookup"><span data-stu-id="4662a-134">1.Select **Save enrichment** after reviewing your choices.</span></span>

## <a name="configure-the-connection-for-here-technologies"></a><span data-ttu-id="4662a-135">Konfigurálja a kapcsolatot a HERE Technologies-hez</span><span class="sxs-lookup"><span data-stu-id="4662a-135">Configure the connection for HERE technologies</span></span> 

<span data-ttu-id="4662a-136">A kapcsolatok konfiguráljához rendszergazdának kell lennie.</span><span class="sxs-lookup"><span data-stu-id="4662a-136">You need to be an administrator to configure connections.</span></span> <span data-ttu-id="4662a-137">A bővítés konfigurálásakor válassza a **Kapcsolat hozzáadása** lehetőséget, *vagy* menjen a **Rendszergazda** > **Kapcsolatok** elemre, és válassza a **Beállítások** lehetőséget a HERE Technologies csempén.</span><span class="sxs-lookup"><span data-stu-id="4662a-137">Select **Add connection** when configuring an enrichment *or* go to **Admin** > **Connections** and select **Set up** on the HERE Technologies tile.</span></span>

1. <span data-ttu-id="4662a-138">Adja meg a kapcsolat nevét a **Megjelenítendő név** mezőben.</span><span class="sxs-lookup"><span data-stu-id="4662a-138">Enter a name for the connection in the **Display name** box.</span></span>

1. <span data-ttu-id="4662a-139">Adjon meg egy érvényes HERE Technologies API-kulcsot.</span><span class="sxs-lookup"><span data-stu-id="4662a-139">Provide a valid HERE Technologies API key.</span></span>

1. <span data-ttu-id="4662a-140">Ellenőrizze és adja meg az **adatvédelemre és a megfelelőségre** vonatkozó beleegyezését az **Elfogadom** jelölőnégyzet bejelölésével</span><span class="sxs-lookup"><span data-stu-id="4662a-140">Review and provide your consent for **Data privacy and compliance** by selecting the **I agree** checkbox</span></span>

1. <span data-ttu-id="4662a-141">A konfiguráció megerősítéséhez válassza az **Ellenőrzés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="4662a-141">Select **Verify** to validate the configuration.</span></span>

1. <span data-ttu-id="4662a-142">Az ellenőrzés befejezése után válassza a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="4662a-142">After completing the verification, select **Save**.</span></span>

> [!div class="mx-imgBorder"]
   > <span data-ttu-id="4662a-143">![A HERE Technologies kapcsolat konfigurációs oldala](media/enrichment-HERE-connection.png "A HERE Technologies kapcsolat konfigurációs oldala")</span><span class="sxs-lookup"><span data-stu-id="4662a-143">![HERE Technologies connection configuration page](media/enrichment-HERE-connection.png "HERE Technologies connection configuration page")</span></span>

## <a name="enrichment-results"></a><span data-ttu-id="4662a-144">Bővítési eredmények</span><span class="sxs-lookup"><span data-stu-id="4662a-144">Enrichment results</span></span>

<span data-ttu-id="4662a-145">A bővítési folyamat megkezdéséhez válassza a **Futtatás** parancsot a parancssorból.</span><span class="sxs-lookup"><span data-stu-id="4662a-145">To start the enrichment process, select **Run** from the command bar.</span></span> <span data-ttu-id="4662a-146">Azt is engedélyezheti, hogy a rendszer a bővítést automatikusan egy [ütemezett frissítés](system.md#schedule-tab) részeként futtassa.</span><span class="sxs-lookup"><span data-stu-id="4662a-146">You can also let the system run the enrichment automatically as part of a [scheduled refresh](system.md#schedule-tab).</span></span> <span data-ttu-id="4662a-147">A feldolgozási idő az ügyféladatok méretétől és a HERE Technologies API-reagálási időponttól függ.</span><span class="sxs-lookup"><span data-stu-id="4662a-147">The processing time will depend on the size of your customer data and the API response times from HERE Technologies.</span></span>

<span data-ttu-id="4662a-148">A bővítési folyamat befejeződése után áttekintheti az újonnan bővített ügyfelek profiljainak adatait a **Saját bővítések** alatt.</span><span class="sxs-lookup"><span data-stu-id="4662a-148">After the enrichment process completes, you can review the newly enriched customer profiles data under **My enrichments**.</span></span> <span data-ttu-id="4662a-149">Emellett megtalálhatja az utolsó frissítés időpontját és a bővített profilok számát is.</span><span class="sxs-lookup"><span data-stu-id="4662a-149">Additionally, you'll find the time of the last update and the number of enriched profiles.</span></span>

<span data-ttu-id="4662a-150">Az egyes bővített profilok részletes nézetét a **Bővített adatok megtekintése** lehetőségre kattintva érheti el.</span><span class="sxs-lookup"><span data-stu-id="4662a-150">You can access a detailed view of each enriched profile by selecting **View enriched data**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4662a-151">Következő lépések</span><span class="sxs-lookup"><span data-stu-id="4662a-151">Next steps</span></span>

<span data-ttu-id="4662a-152">Építsen a bővített ügyféladatokra.</span><span class="sxs-lookup"><span data-stu-id="4662a-152">Build on top of your enriched customer data.</span></span> <span data-ttu-id="4662a-153">Hozzon létre [szegmenseket](segments.md), [mértékeket](measures.md) , sőt [exportálhatja az adatokat](export-destinations.md), hogy személyre szabott élményeket tudjon nyújtani az ügyfeleknek.</span><span class="sxs-lookup"><span data-stu-id="4662a-153">Create [segments](segments.md), [measures](measures.md), and even [export the data](export-destinations.md) to deliver personalized experiences to your customers.</span></span>

## <a name="data-privacy-and-compliance"></a><span data-ttu-id="4662a-154">Adatvédelem és megfelelőség</span><span class="sxs-lookup"><span data-stu-id="4662a-154">Data privacy and compliance</span></span>

<span data-ttu-id="4662a-155">Amikor engedélyezi a Dynamics 365 Customer Insights szolgáltatást az adatok HERE Technologies szolgáltatásba való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat.</span><span class="sxs-lookup"><span data-stu-id="4662a-155">When you enable Dynamics 365 Customer Insights to transmit data to HERE Technologies, you allow transfer of data outside of the compliance boundary for Dynamics 365 Customer Insights, including potentially sensitive data such as Personal Data.</span></span> <span data-ttu-id="4662a-156">A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy a HERE Technologies megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek.</span><span class="sxs-lookup"><span data-stu-id="4662a-156">Microsoft will transfer such data at your instruction, but you are responsible for ensuring that HERE Technologies meets any privacy or security obligations you may have.</span></span> <span data-ttu-id="4662a-157">További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).</span><span class="sxs-lookup"><span data-stu-id="4662a-157">For more information, see [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?linkid=396732).</span></span>
<span data-ttu-id="4662a-158">A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt a bővítést.</span><span class="sxs-lookup"><span data-stu-id="4662a-158">Your Dynamics 365 Customer Insights Administrator can remove this enrichment at any time to discontinue use of this functionality.</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]
