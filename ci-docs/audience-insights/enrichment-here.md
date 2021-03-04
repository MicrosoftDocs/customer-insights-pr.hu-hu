---
title: 'Bővítés külső bővítéssel: HERE Technologies'
description: Általános információk a HERE Technologies harmadik fél bővítésről.
ms.date: 12/10/2020
ms.reviewer: jodahl
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: 258e37de9d9685d9ebc30b3c6b8d238d583431b4
ms.sourcegitcommit: 139548f8a2d0f24d54c4a6c404a743eeeb8ef8e0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/15/2021
ms.locfileid: "5269517"
---
# <a name="enrichment-of-customer-profiles-with-here-technologies-preview"></a><span data-ttu-id="e6176-103">Ügyfélprofilok bővítése a HERE Technologies (előzetes verzió) segítségével</span><span class="sxs-lookup"><span data-stu-id="e6176-103">Enrichment of customer profiles with HERE Technologies (preview)</span></span>

<span data-ttu-id="e6176-104">A HERE Technologies egy helyplatformot biztosító vállalat, amely helyalapú adatokat és szolgáltatásokat nyújt.</span><span class="sxs-lookup"><span data-stu-id="e6176-104">HERE Technologies is a location platform company that provides location-centric data and services.</span></span> <span data-ttu-id="e6176-105">A HERE Technologies adatbővítési szolgáltatásaival pontosabb helyértelmezést hozhat létre az ügyfelekről a cím normalizálásával, földrajzi hosszúság és szélesség kinyerésével stb.</span><span class="sxs-lookup"><span data-stu-id="e6176-105">With HERE Technologies' data enrichment services, you can build a more precise location understanding of your customers with address normalization, latitude and longitude extraction, and more.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e6176-106">Előfeltételek</span><span class="sxs-lookup"><span data-stu-id="e6176-106">Prerequisites</span></span>

<span data-ttu-id="e6176-107">A HERE Technologies bővítések konfigurálásához a következő előfeltételeknek kell teljesülnie:</span><span class="sxs-lookup"><span data-stu-id="e6176-107">To configure HERE Technologies enrichments, the following prerequisites must be met:</span></span>

- <span data-ttu-id="e6176-108">Aktív HERE Technologies előfizetéssel kell rendelkeznie.</span><span class="sxs-lookup"><span data-stu-id="e6176-108">You have an active HERE Technologies subscription.</span></span> <span data-ttu-id="e6176-109">Az előfizetés beszerzéséhez [regisztrálhat itt](https://developer.here.com/sign-up?utm_medium=referral&utm_source=Microsoft-Dynamics-CI&create=Freemium-Basic) vagy [felveheti a HERE Technologiesszel a kapcsolatot](https://developer.here.com/help?utm_medium=referral&utm_source=Microsoft-Dynamics-CI#how-can-we-help-you) közvetlenül.</span><span class="sxs-lookup"><span data-stu-id="e6176-109">To get a subscription, you can [sign-up here](https://developer.here.com/sign-up?utm_medium=referral&utm_source=Microsoft-Dynamics-CI&create=Freemium-Basic) or [contact HERE Technologies](https://developer.here.com/help?utm_medium=referral&utm_source=Microsoft-Dynamics-CI#how-can-we-help-you) directly.</span></span> [<span data-ttu-id="e6176-110">Itt többet is megtudhat a HERE Technologies helybővítéshez.</span><span class="sxs-lookup"><span data-stu-id="e6176-110">Learn more about HERE Technologies Location Enrichment.</span></span>](https://developer.here.com/location-enrichment?cid=Dev-MicrosoftDynamics-DB-0-Dev-&utm_source=MicrosoftDynamics&utm_medium=referral&utm_campaign=Online_Dev_ReferralMicrosoft)

- <span data-ttu-id="e6176-111">Rendelkezik a HERE Technologies API-kulccsal.</span><span class="sxs-lookup"><span data-stu-id="e6176-111">You have the HERE Technologies API key.</span></span>

- <span data-ttu-id="e6176-112">[Rendszergazda](permissions.md#administrator) engedéllyel rendelkezik.</span><span class="sxs-lookup"><span data-stu-id="e6176-112">You have [Administrator](permissions.md#administrator) permissions.</span></span>

## <a name="configuration"></a><span data-ttu-id="e6176-113">Konfigurálás</span><span class="sxs-lookup"><span data-stu-id="e6176-113">Configuration</span></span>

1. <span data-ttu-id="e6176-114">Lépjen az **Adatok** > **Bővítés** pontra.</span><span class="sxs-lookup"><span data-stu-id="e6176-114">Go to **Data** > **Enrichment**.</span></span>

1. <span data-ttu-id="e6176-115">Válassza a **Saját adatok bővítése** elemet a HERE Technologies csempén.</span><span class="sxs-lookup"><span data-stu-id="e6176-115">Select **Enrich my data** on the HERE Technologies tile.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="e6176-116">![HERE Technologies csempe](media/HERE-tile.png "HERE Technologies csempe")</span><span class="sxs-lookup"><span data-stu-id="e6176-116">![HERE Technologies tile](media/HERE-tile.png "HERE Technologies tile")</span></span>

1. <span data-ttu-id="e6176-117">Adja meg az aktív **HERE Technologies API-kulcsot**.</span><span class="sxs-lookup"><span data-stu-id="e6176-117">Enter an active **HERE Technologies API key**.</span></span> <span data-ttu-id="e6176-118">Ellenőrizze és adja meg az **adatvédelemre és a megfelelőségre** vonatkozó beleegyezését az **Elfogadom** jelölőnégyzet bejelölésével.</span><span class="sxs-lookup"><span data-stu-id="e6176-118">Review and provide your consent for **Data privacy and compliance** by selecting the **I agree** checkbox.</span></span> 

1. <span data-ttu-id="e6176-119">Erősítse meg mindkét bemenetet a **Csatlakozik a HERE-hez** lehetőség kiválasztásával.</span><span class="sxs-lookup"><span data-stu-id="e6176-119">Confirm both inputs by selecting **Connect to HERE**.</span></span>

1.  <span data-ttu-id="e6176-120">Válassza az **Adatok hozzáadása** lehetőséget, és az HERE helyadatokkal bővíteni kívánt **Ügyfél adatkészletet**.</span><span class="sxs-lookup"><span data-stu-id="e6176-120">Select **Add data** and choose the **Customer data set** you want to enrich with location data from HERE Technologies.</span></span> <span data-ttu-id="e6176-121">Kiválaszthatja a **Vevő** entitást az összes ügyfélprofil gazdagítására, vagy kiválaszthat egy szegmens entitást, amely csak az adott szegmensben található vevőprofilokat gazdagítja.</span><span class="sxs-lookup"><span data-stu-id="e6176-121">You can select the **Customer** entity to enrich all your customer profiles or select a segment entity to enrich only customer profiles contained in that segment.</span></span>

    :::image type="content" source="media/enrichment-HERE-configuration-customer-data-set.png" alt-text="Képernyőkép az ügyféladatkészlet kiválasztásáról.":::

1. <span data-ttu-id="e6176-123">Válassza ki, hogy szeretné-e leképezni a mezőket az elsődleges és/vagy másodlagos címre.</span><span class="sxs-lookup"><span data-stu-id="e6176-123">Choose if you want to map fields to the primary and/or secondary address.</span></span> <span data-ttu-id="e6176-124">Megadhatja a mezők leképezését mindkét címhez (például otthoni és üzleti cím), és a mindkét címhez tartozó profilt külön is bővítheti.</span><span class="sxs-lookup"><span data-stu-id="e6176-124">You can specify a field mapping for both addresses (for example, a home and a business address) and enrich the profiles for both addresses separately.</span></span> <span data-ttu-id="e6176-125">Válassza a **Következő** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="e6176-125">Select **Next**.</span></span>

1. <span data-ttu-id="e6176-126">Adja meg, hogy az egyesített profilokból mely mezők használhatók a megfelelő helyadatok megkereséséhez a HERE Technologiesből.</span><span class="sxs-lookup"><span data-stu-id="e6176-126">Define which fields from your unified profiles should be used to look for matching location data from HERE Technologies.</span></span> <span data-ttu-id="e6176-127">A kiválasztott elsődleges és/vagy másodlagos címhez az **Utca 1.** és az **Irányítószám** mező megadása kötelező.</span><span class="sxs-lookup"><span data-stu-id="e6176-127">The **Street 1** and **Zip/Postal Code** fields are required for the selected primary and/or secondary address.</span></span> <span data-ttu-id="e6176-128">A nagyobb egyeztetési pontosság érdekében további mezők adhatók hozzá.</span><span class="sxs-lookup"><span data-stu-id="e6176-128">For a higher match accuracy, more fields can be added.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="e6176-129">![HERE Technologies bővítés konfigurációs oldal](media/enrichment-HERE-configuration.png "HERE Technologies bővítés konfigurációs oldal")</span><span class="sxs-lookup"><span data-stu-id="e6176-129">![HERE Technologies enrichment configuration page](media/enrichment-HERE-configuration.png "HERE Technologies enrichment configuration page")</span></span>

1. <span data-ttu-id="e6176-130">Válassza az **Alkalmaz** lehetőséget a mezők leképezésének végrehajtásához.</span><span class="sxs-lookup"><span data-stu-id="e6176-130">Select **Apply** to complete the field mapping.</span></span>

## <a name="enrichment-results"></a><span data-ttu-id="e6176-131">Bővítési eredmények</span><span class="sxs-lookup"><span data-stu-id="e6176-131">Enrichment results</span></span>

<span data-ttu-id="e6176-132">A bővítési folyamat megkezdéséhez válassza a **Futtatás** parancsot a parancssorból.</span><span class="sxs-lookup"><span data-stu-id="e6176-132">To start the enrichment process, select **Run** from the command bar.</span></span> <span data-ttu-id="e6176-133">Azt is engedélyezheti, hogy a rendszer a bővítést automatikusan egy [ütemezett frissítés](system.md#schedule-tab) részeként futtassa.</span><span class="sxs-lookup"><span data-stu-id="e6176-133">You can also let the system run the enrichment automatically as part of a [scheduled refresh](system.md#schedule-tab).</span></span> <span data-ttu-id="e6176-134">A feldolgozási idő az ügyféladatok méretétől és a HERE Technologies API-reagálási időponttól függ.</span><span class="sxs-lookup"><span data-stu-id="e6176-134">The processing time will depend on the size of your customer data and the API response times from HERE Technologies.</span></span>

<span data-ttu-id="e6176-135">A bővítési folyamat befejeződése után áttekintheti az újonnan bővített ügyfelek profiljainak adatait a **Saját bővítések** alatt.</span><span class="sxs-lookup"><span data-stu-id="e6176-135">After the enrichment process completes, you can review the newly enriched customer profiles data under **My enrichments**.</span></span> <span data-ttu-id="e6176-136">Emellett megtalálhatja az utolsó frissítés időpontját és a bővített profilok számát is.</span><span class="sxs-lookup"><span data-stu-id="e6176-136">Additionally, you'll find the time of the last update and the number of enriched profiles.</span></span>

<span data-ttu-id="e6176-137">Az egyes bővített profilok részletes nézetét a **Bővített adatok megtekintése** lehetőségre kattintva érheti el.</span><span class="sxs-lookup"><span data-stu-id="e6176-137">You can access a detailed view of each enriched profile by selecting **View enriched data**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e6176-138">Következő lépések</span><span class="sxs-lookup"><span data-stu-id="e6176-138">Next steps</span></span>

<span data-ttu-id="e6176-139">Építsen a bővített ügyféladatokra.</span><span class="sxs-lookup"><span data-stu-id="e6176-139">Build on top of your enriched customer data.</span></span> <span data-ttu-id="e6176-140">Hozzon létre [szegmenseket](segments.md), [mértékeket](measures.md) , sőt [exportálhatja az adatokat](export-destinations.md), hogy személyre szabott élményeket tudjon nyújtani az ügyfeleknek.</span><span class="sxs-lookup"><span data-stu-id="e6176-140">Create [segments](segments.md), [measures](measures.md), and even [export the data](export-destinations.md) to deliver personalized experiences to your customers.</span></span>

## <a name="data-privacy-and-compliance"></a><span data-ttu-id="e6176-141">Adatvédelem és megfelelőség</span><span class="sxs-lookup"><span data-stu-id="e6176-141">Data privacy and compliance</span></span>

<span data-ttu-id="e6176-142">Amikor engedélyezi a Dynamics 365 Customer Insights szolgáltatást az adatok HERE Technologies szolgáltatásba való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat.</span><span class="sxs-lookup"><span data-stu-id="e6176-142">When you enable Dynamics 365 Customer Insights to transmit data to HERE Technologies, you allow transfer of data outside of the compliance boundary for Dynamics 365 Customer Insights, including potentially sensitive data such as Personal Data.</span></span> <span data-ttu-id="e6176-143">A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy a HERE Technologies megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek.</span><span class="sxs-lookup"><span data-stu-id="e6176-143">Microsoft will transfer such data at your instruction, but you are responsible for ensuring that HERE Technologies meets any privacy or security obligations you may have.</span></span> <span data-ttu-id="e6176-144">További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).</span><span class="sxs-lookup"><span data-stu-id="e6176-144">For more information, see [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?linkid=396732).</span></span>
<span data-ttu-id="e6176-145">A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt a bővítést.</span><span class="sxs-lookup"><span data-stu-id="e6176-145">Your Dynamics 365 Customer Insights Administrator can remove this enrichment at any time to discontinue use of this functionality.</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]