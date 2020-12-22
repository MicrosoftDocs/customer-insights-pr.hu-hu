---
title: 'Bővítés külső bővítéssel: HERE Technologies'
description: Általános információk a HERE Technologies harmadik fél bővítésről.
ms.date: 10/27/2020
ms.reviewer: jodahl
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: 7082fcfec099c3c9436b233c193be23625f6691a
ms.sourcegitcommit: a9b2cf598f256d07a48bba8617347ee90024a1dd
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/03/2020
ms.locfileid: "4668681"
---
# <a name="enrichment-of-customer-profiles-with-here-technologies-preview"></a><span data-ttu-id="d6b87-103">Ügyfélprofilok bővítése a HERE Technologies (előzetes verzió) segítségével</span><span class="sxs-lookup"><span data-stu-id="d6b87-103">Enrichment of customer profiles with HERE Technologies (preview)</span></span>

<span data-ttu-id="d6b87-104">A HERE Technologies egy helyplatformot biztosító vállalat, amely helyalapú adatokat és szolgáltatásokat nyújt.</span><span class="sxs-lookup"><span data-stu-id="d6b87-104">HERE Technologies is a location platform company that provides location-centric data and services.</span></span> <span data-ttu-id="d6b87-105">A HERE Technologies adatbővítési szolgáltatásaival pontosabb helyértelmezést hozhat létre az ügyfelekről a cím normalizálásával, földrajzi hosszúság és szélesség kinyerésével stb.</span><span class="sxs-lookup"><span data-stu-id="d6b87-105">With HERE Technologies' data enrichment services, you can build a more precise location understanding of your customers with address normalization, latitude and longitude extraction, and more.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d6b87-106">Előfeltételek</span><span class="sxs-lookup"><span data-stu-id="d6b87-106">Prerequisites</span></span>

<span data-ttu-id="d6b87-107">A HERE Technologies bővítések konfigurálásához a következő előfeltételeknek kell teljesülnie:</span><span class="sxs-lookup"><span data-stu-id="d6b87-107">To configure HERE Technologies enrichments, the following prerequisites must be met:</span></span>

- <span data-ttu-id="d6b87-108">Aktív HERE Technologies előfizetéssel kell rendelkeznie.</span><span class="sxs-lookup"><span data-stu-id="d6b87-108">You have an active HERE Technologies subscription.</span></span> <span data-ttu-id="d6b87-109">Az előfizetés beszerzéséhez [regisztrálhat itt](https://developer.here.com/sign-up?utm_medium=referral&utm_source=Microsoft-Dynamics-CI&create=Freemium-Basic) vagy [felveheti a HERE Technologiesszel a kapcsolatot](https://developer.here.com/help?utm_medium=referral&utm_source=Microsoft-Dynamics-CI#how-can-we-help-you) közvetlenül.</span><span class="sxs-lookup"><span data-stu-id="d6b87-109">To get a subscription, you can [sign-up here](https://developer.here.com/sign-up?utm_medium=referral&utm_source=Microsoft-Dynamics-CI&create=Freemium-Basic) or [contact HERE Technologies](https://developer.here.com/help?utm_medium=referral&utm_source=Microsoft-Dynamics-CI#how-can-we-help-you) directly.</span></span> [<span data-ttu-id="d6b87-110">Itt többet is megtudhat a HERE Technologies helybővítéshez.</span><span class="sxs-lookup"><span data-stu-id="d6b87-110">Learn more about HERE Technologies Location Enrichment.</span></span>](https://developer.here.com/location-enrichment?cid=Dev-MicrosoftDynamics-DB-0-Dev-&utm_source=MicrosoftDynamics&utm_medium=referral&utm_campaign=Online_Dev_ReferralMicrosoft)

- <span data-ttu-id="d6b87-111">Rendelkezik a HERE Technologies API-kulccsal.</span><span class="sxs-lookup"><span data-stu-id="d6b87-111">You have the HERE Technologies API key.</span></span>

- <span data-ttu-id="d6b87-112">[Rendszergazda](permissions.md#administrator) engedéllyel rendelkezik.</span><span class="sxs-lookup"><span data-stu-id="d6b87-112">You have [Administrator](permissions.md#administrator) permissions.</span></span>

## <a name="configuration"></a><span data-ttu-id="d6b87-113">Konfigurálás</span><span class="sxs-lookup"><span data-stu-id="d6b87-113">Configuration</span></span>

1. <span data-ttu-id="d6b87-114">Lépjen az **Adatok** > **Bővítés** pontra.</span><span class="sxs-lookup"><span data-stu-id="d6b87-114">Go to **Data** > **Enrichment**.</span></span>

1. <span data-ttu-id="d6b87-115">Válassza a **Saját adatok bővítése** elemet a HERE Technologies csempén.</span><span class="sxs-lookup"><span data-stu-id="d6b87-115">Select **Enrich my data** on the HERE Technologies tile.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="d6b87-116">![HERE Technologies csempe](media/HERE-tile.png "HERE Technologies csempe")</span><span class="sxs-lookup"><span data-stu-id="d6b87-116">![HERE Technologies tile](media/HERE-tile.png "HERE Technologies tile")</span></span>

1. <span data-ttu-id="d6b87-117">Adja meg az aktív **HERE Technologies API-kulcsot**.</span><span class="sxs-lookup"><span data-stu-id="d6b87-117">Enter an active **HERE Technologies API key**.</span></span> <span data-ttu-id="d6b87-118">Ellenőrizze és adja meg az **adatvédelemre és a megfelelőségre** vonatkozó beleegyezését az **Elfogadom** jelölőnégyzet bejelölésével.</span><span class="sxs-lookup"><span data-stu-id="d6b87-118">Review and provide your consent for **Data privacy and compliance** by selecting the **I agree** checkbox.</span></span> 

1. <span data-ttu-id="d6b87-119">Erősítse meg mindkét bemenetet a **Csatlakozik a HERE-hez** lehetőség kiválasztásával.</span><span class="sxs-lookup"><span data-stu-id="d6b87-119">Confirm both inputs by selecting **Connect to HERE**.</span></span>

1. <span data-ttu-id="d6b87-120">Válassza az **Adatok hozzáadása** lehetőséget, és adja meg, hogy szeretné-e leképezni a mezőket az elsődleges és/vagy másodlagos címre.</span><span class="sxs-lookup"><span data-stu-id="d6b87-120">Select **Add data** and choose if you want to map fields to the primary and/or secondary address.</span></span> <span data-ttu-id="d6b87-121">Megadhatja a mezők leképezését mindkét címhez (például otthoni és üzleti cím), és a mindkét címhez tartozó profilt külön is bővítheti.</span><span class="sxs-lookup"><span data-stu-id="d6b87-121">You can specify a field mapping for both addresses (for example, a home and a business address) and enrich the profiles for both addresses separately.</span></span> <span data-ttu-id="d6b87-122">Válassza a **Következő** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="d6b87-122">Select **Next**.</span></span>

1. <span data-ttu-id="d6b87-123">Adja meg, hogy az egyesített profilokból mely mezők használhatók a megfelelő helyadatok megkereséséhez a HERE Technologiesből.</span><span class="sxs-lookup"><span data-stu-id="d6b87-123">Define which fields from your unified profiles should be used to look for matching location data from HERE Technologies.</span></span> <span data-ttu-id="d6b87-124">A kiválasztott elsődleges és/vagy másodlagos címhez az **Utca 1.** és az **Irányítószám** mező megadása kötelező.</span><span class="sxs-lookup"><span data-stu-id="d6b87-124">The **Street 1** and **Zip/Postal Code** fields are required for the selected primary and/or secondary address.</span></span> <span data-ttu-id="d6b87-125">A nagyobb egyeztetési pontosság érdekében további mezők adhatók hozzá.</span><span class="sxs-lookup"><span data-stu-id="d6b87-125">For a higher match accuracy, more fields can be added.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="d6b87-126">![HERE Technologies bővítés konfigurációs oldal](media/enrichment-HERE-configuration.png "HERE Technologies bővítés konfigurációs oldal")</span><span class="sxs-lookup"><span data-stu-id="d6b87-126">![HERE Technologies enrichment configuration page](media/enrichment-HERE-configuration.png "HERE Technologies enrichment configuration page")</span></span>

1. <span data-ttu-id="d6b87-127">Válassza az **Alkalmaz** lehetőséget a mezők leképezésének végrehajtásához.</span><span class="sxs-lookup"><span data-stu-id="d6b87-127">Select **Apply** to complete the field mapping.</span></span>

## <a name="enrichment-results"></a><span data-ttu-id="d6b87-128">Bővítési eredmények</span><span class="sxs-lookup"><span data-stu-id="d6b87-128">Enrichment results</span></span>

<span data-ttu-id="d6b87-129">A bővítési folyamat megkezdéséhez válassza a **Futtatás** parancsot a parancssorból.</span><span class="sxs-lookup"><span data-stu-id="d6b87-129">To start the enrichment process, select **Run** from the command bar.</span></span> <span data-ttu-id="d6b87-130">Azt is engedélyezheti, hogy a rendszer a bővítést automatikusan egy [ütemezett frissítés](system.md#schedule-tab) részeként futtassa.</span><span class="sxs-lookup"><span data-stu-id="d6b87-130">You can also let the system run the enrichment automatically as part of a [scheduled refresh](system.md#schedule-tab).</span></span> <span data-ttu-id="d6b87-131">A feldolgozási idő az ügyféladatok méretétől és a HERE Technologies API-reagálási időponttól függ.</span><span class="sxs-lookup"><span data-stu-id="d6b87-131">The processing time will depend on the size of your customer data and the API response times from HERE Technologies.</span></span>

<span data-ttu-id="d6b87-132">A bővítési folyamat befejeződése után áttekintheti az újonnan bővített ügyfelek profiljainak adatait a **Saját bővítések** alatt.</span><span class="sxs-lookup"><span data-stu-id="d6b87-132">After the enrichment process completes, you can review the newly enriched customer profiles data under **My enrichments**.</span></span> <span data-ttu-id="d6b87-133">Emellett megtalálhatja az utolsó frissítés időpontját és a bővített profilok számát is.</span><span class="sxs-lookup"><span data-stu-id="d6b87-133">Additionally, you'll find the time of the last update and the number of enriched profiles.</span></span>

<span data-ttu-id="d6b87-134">Az egyes bővített profilok részletes nézetét a **Bővített adatok megtekintése** lehetőségre kattintva érheti el.</span><span class="sxs-lookup"><span data-stu-id="d6b87-134">You can access a detailed view of each enriched profile by selecting **View enriched data**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="d6b87-135">Következő lépések</span><span class="sxs-lookup"><span data-stu-id="d6b87-135">Next steps</span></span>

<span data-ttu-id="d6b87-136">Építsen a bővített ügyféladatokra.</span><span class="sxs-lookup"><span data-stu-id="d6b87-136">Build on top of your enriched customer data.</span></span> <span data-ttu-id="d6b87-137">Hozzon létre [szegmenseket](segments.md), [mértékeket](measures.md) , sőt [exportálhatja az adatokat](export-destinations.md), hogy személyre szabott élményeket tudjon nyújtani az ügyfeleknek.</span><span class="sxs-lookup"><span data-stu-id="d6b87-137">Create [segments](segments.md), [measures](measures.md), and even [export the data](export-destinations.md) to deliver personalized experiences to your customers.</span></span>

## <a name="data-privacy-and-compliance"></a><span data-ttu-id="d6b87-138">Adatvédelem és megfelelőség</span><span class="sxs-lookup"><span data-stu-id="d6b87-138">Data privacy and compliance</span></span>

<span data-ttu-id="d6b87-139">Amikor engedélyezi a Dynamics 365 Customer Insights szolgáltatást az adatok HERE Technologies szolgáltatásba való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat.</span><span class="sxs-lookup"><span data-stu-id="d6b87-139">When you enable Dynamics 365 Customer Insights to transmit data to HERE Technologies, you allow transfer of data outside of the compliance boundary for Dynamics 365 Customer Insights, including potentially sensitive data such as Personal Data.</span></span> <span data-ttu-id="d6b87-140">A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy a HERE Technologies megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek.</span><span class="sxs-lookup"><span data-stu-id="d6b87-140">Microsoft will transfer such data at your instruction, but you are responsible for ensuring that HERE Technologies meets any privacy or security obligations you may have.</span></span> <span data-ttu-id="d6b87-141">További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).</span><span class="sxs-lookup"><span data-stu-id="d6b87-141">For more information, see [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?linkid=396732).</span></span>
<span data-ttu-id="d6b87-142">A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt a bővítést.</span><span class="sxs-lookup"><span data-stu-id="d6b87-142">Your Dynamics 365 Customer Insights Administrator can remove this enrichment at any time to discontinue use of this functionality.</span></span>
