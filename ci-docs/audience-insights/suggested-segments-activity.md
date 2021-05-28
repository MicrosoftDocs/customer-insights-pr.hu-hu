---
title: Tevékenység alapján javasolt szegmensek.
description: A gépi tanulás segítségével új, érdekes szegmenseket találhat az ügyféltevékenység alapján.
ms.date: 05/11/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: JimsonChalissery
ms.author: jimsonc
manager: shellyha
ms.openlocfilehash: 14d9d4f0df6b5835f21fb63447d05853ee98a757
ms.sourcegitcommit: 8341fa964365c185b65bc4b71fc0c695ea127dc0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/14/2021
ms.locfileid: "6034081"
---
# <a name="suggested-segments-based-on-activity-data-preview"></a><span data-ttu-id="f143a-103">Tevékenységadatok alapján javasolt szegmensek (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="f143a-103">Suggested segments based on activity data (preview)</span></span>

<span data-ttu-id="f143a-104">Az ügyfelek Customer Insightsba feltöltött tevékenységadatai alapján az ügyfelek érdekes szegmenseit fedezheti fel.</span><span class="sxs-lookup"><span data-stu-id="f143a-104">Discover interesting segments of your customers based on customer activity data that is ingested to Customer Insights.</span></span> <span data-ttu-id="f143a-105">Tevékenységadatok például a tranzakciók, az ügyfélszolgálati hívás időtartama, a vásárlások vagy a visszatérítések.</span><span class="sxs-lookup"><span data-stu-id="f143a-105">Examples of activity data are transactions, support call duration, purchases, or returns.</span></span> <span data-ttu-id="f143a-106">A szegmensek javaslásához elemezni kell a tevékenységadatokat, a közelmúltbeli tevékenység, a gyakoriság és a pénzben megadott érték (vagy időtartam) alapján.</span><span class="sxs-lookup"><span data-stu-id="f143a-106">To suggest segments, activity data gets analyzed for recency, frequency, and monetary value (or duration).</span></span> <span data-ttu-id="f143a-107">Másik megoldásként létrehozhat [javasolt szegmenseket a mértékek tökéletesítéséhez vagy az attribútumokat befolyásoló részletek pontosabb megállapításához](suggested-segments.md).</span><span class="sxs-lookup"><span data-stu-id="f143a-107">Alternatively, you can generate [suggested segments to improve a measure or better understand what influences an attribute](suggested-segments.md).</span></span>

:::image type="content" source="media/suggested-segments-tab.png" alt-text="A Javasolt szegmensek lap, tevékenységalapú és attribútumalapú szegmensekre vonatkozó javaslatokkal.":::

## <a name="categorize-customers-by-activity"></a><span data-ttu-id="f143a-109">Ügyfelek kategorizálása tevékenység szerint</span><span class="sxs-lookup"><span data-stu-id="f143a-109">Categorize customers by activity</span></span>

<span data-ttu-id="f143a-110">A Customer Insights [tevékenységadatai](activities.md) alapján az ügyfélcsoportokat tükröző javaslatokat tudunk készíteni:</span><span class="sxs-lookup"><span data-stu-id="f143a-110">With [activity data](activities.md) available in Customer Insights, we can generate suggestions that represent customer groups:</span></span>

- <span data-ttu-id="f143a-111">legaktívabb ügyfelek</span><span class="sxs-lookup"><span data-stu-id="f143a-111">most active customers</span></span> 
- <span data-ttu-id="f143a-112">a legtöbb vásárlást végrehajtó ügyfelek</span><span class="sxs-lookup"><span data-stu-id="f143a-112">customers that have made the most purchases</span></span> 
- <span data-ttu-id="f143a-113">a legnagyobb bevételt eredményező ügyfelek</span><span class="sxs-lookup"><span data-stu-id="f143a-113">customers that generated the most revenue</span></span> 
- <span data-ttu-id="f143a-114">az utóbbi időben nem aktív ügyfelek</span><span class="sxs-lookup"><span data-stu-id="f143a-114">customers who haven’t been active lately</span></span> 
- <span data-ttu-id="f143a-115">ügyfelek, akik gyakran lépnek kapcsolatba a vállalkozással</span><span class="sxs-lookup"><span data-stu-id="f143a-115">customers who frequently interact with your business</span></span>  

<span data-ttu-id="f143a-116">Ha kiskereskedelmi vállalkozása van, akkor meg tudja állapítani, hogy melyik ügyfelek generálják a legnagyobb bevételt, és kuponokkal jutalmazhatja őket.</span><span class="sxs-lookup"><span data-stu-id="f143a-116">If you have a retail business, you could find out which customers generate the most revenue and reward them with a coupon.</span></span> <span data-ttu-id="f143a-117">Esetleg megtalálhatja az eseti ügyfeleket, és felajánlhatja nekik, hogy vegyenek részt egy jutalmazási programban, így gyakrabban kereshetik meg az Ön vállalkozását.</span><span class="sxs-lookup"><span data-stu-id="f143a-117">Or you can identify occasional customers and offer them to join a rewards program so they visit your business more often.</span></span>
<span data-ttu-id="f143a-118">Ha nyilvános egészségügyi szolgáltatást nyújt, és minimálisra szeretné csökkenteni az egyes betegek költségeit.</span><span class="sxs-lookup"><span data-stu-id="f143a-118">If you're in the healthcare business providing public healthcare and your goal is to minimize the expenses for individual patients.</span></span> <span data-ttu-id="f143a-119">Ennek egyik módja lehet az ismétlődő látogatások számának csökkentése azzal, hogy a lehető legkevesebb látogatás során a lehető legjobb ellátást biztosítja.</span><span class="sxs-lookup"><span data-stu-id="f143a-119">A way to do so could be to reduce recurring visits by providing best possible care in as few visits as possible.</span></span> <span data-ttu-id="f143a-120">Ebben az esetben az a célja, hogy a látogatások gyakorisága alacsony legyen, és hogy minimálisra csökkentse az ismétlődő költségeket.</span><span class="sxs-lookup"><span data-stu-id="f143a-120">In this case, your goal is to keep the visit frequency low and minimize recurring cost for the patients.</span></span> <span data-ttu-id="f143a-121">Esetleg megkeresheti a páciensek azon szegmenseit, amelyek esetében gyakoriak a találkozók és magasak az ismétlődő költségek, majd elemezheti az ilyen eseteket, hogy javítani tudja az egyes személyeknek kínált kezeléseket.</span><span class="sxs-lookup"><span data-stu-id="f143a-121">Or you can identify segments of patients who have frequent appointments and high recurring costs and analyze these cases to improve the treatment of the individual.</span></span> 

## <a name="required-data"></a><span data-ttu-id="f143a-122">Szükséges adatok</span><span class="sxs-lookup"><span data-stu-id="f143a-122">Required data</span></span>

<span data-ttu-id="f143a-123">A javaslatokat a kiválasztott bemeneti adatok alapján hozza létre a rendszer.</span><span class="sxs-lookup"><span data-stu-id="f143a-123">Suggestions are generated based on the selected input data.</span></span> 

- <span data-ttu-id="f143a-124">Ügyfélprofilok: Egy adott szegmens összes ügyfele vagy tagja.</span><span class="sxs-lookup"><span data-stu-id="f143a-124">Customer profiles: All customers or members of a specific segment.</span></span> 

- <span data-ttu-id="f143a-125">Időszak: Legutóbbi hónap, legutóbbi év vagy bármilyen egyéni időszak.</span><span class="sxs-lookup"><span data-stu-id="f143a-125">Time period: Last month, last year, or any custom time frame.</span></span>

- <span data-ttu-id="f143a-126">Tevékenységtípus: Vásárlások, kiskereskedelmi tranzakciók, online tranzakciók, ügyféltámogatási esetek, előfizetések stb.</span><span class="sxs-lookup"><span data-stu-id="f143a-126">Activity type: purchases, retail transactions, online transactions, customer support cases, subscriptions, and so on.</span></span>  

- <span data-ttu-id="f143a-127">A tevékenységadatokat tartalmazó Customer Insights-entitás: A UnifiedActivity entitás vagy egy adott tevékenységhez tartozó entitás.</span><span class="sxs-lookup"><span data-stu-id="f143a-127">Entity in Customer Insights that contains the activity data: The UnifiedActivity entity or the entity for a specific activity.</span></span> 

- <span data-ttu-id="f143a-128">Használandó dimenziók: Az üzleti igényektől függően közelmúltbeli tevékenység, gyakoriság vagy pénzbeli dimenzió.</span><span class="sxs-lookup"><span data-stu-id="f143a-128">Dimensions to include: Recency, frequency, or monetary dimension, depending on your business requirements.</span></span>

## <a name="generate-suggested-segments"></a><span data-ttu-id="f143a-129">Javasolt szegmensek létrehozása</span><span class="sxs-lookup"><span data-stu-id="f143a-129">Generate suggested segments</span></span>

1. <span data-ttu-id="f143a-130">Kattintson a **Szegmensek** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="f143a-130">Go to **Segments**.</span></span>

1. <span data-ttu-id="f143a-131">Válassza a **Javaslatok (előzetes verzió)** fület.</span><span class="sxs-lookup"><span data-stu-id="f143a-131">Select the **Suggestions (preview)** tab.</span></span>

1. <span data-ttu-id="f143a-132">Válassza az **Új javaslatok keresése**, majd **Az ügyfél viselkedésének megtekintése vagy előrejelzése** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="f143a-132">Select **Find new suggestions** and choose **See or anticipate customer behavior**.</span></span> <span data-ttu-id="f143a-133">Az irányított élmény futtatásához válassza az **Indítás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="f143a-133">Select **Start** to run the guided experience.</span></span>

   :::image type="content" source="media/suggested-segments-activity-wizard.png" alt-text="A konfigurációs varázsló első lépése tevékenységen alapuló javasolt szegmensnél.":::

1. <span data-ttu-id="f143a-135">Adja meg a szükséges bemeneti adatokat, és válassza a **Tovább** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="f143a-135">Provide the required input data and select **Next** proceed.</span></span>

   - <span data-ttu-id="f143a-136">Ügyfelek kiválasztása: Az összes ügyfelet tartalmazza, vagy egy adott szegmenst.</span><span class="sxs-lookup"><span data-stu-id="f143a-136">Choose customers: Include all customers or a specific segment.</span></span>
   - <span data-ttu-id="f143a-137">Tevékenység kiválasztása: Adja meg a tevékenység típusát és a tevékenységet leíró entitásokat.</span><span class="sxs-lookup"><span data-stu-id="f143a-137">Choose activity: Select the activity type and the entities that describe the activity.</span></span>
   - <span data-ttu-id="f143a-138">Beállítások: Állítsa be a figyelembe venni kívánt időszakot, a tényezőket a javaslatokhoz, és képezze le az attribútumokat.</span><span class="sxs-lookup"><span data-stu-id="f143a-138">Preferences: Set the time period to consider, the factors for suggestions, and map the attributes.</span></span>

1. <span data-ttu-id="f143a-139">Tekintse át a bemeneti adatokat, és válassza a **Futtatás** lehetőséget a modell futtatásához és a javaslatok létrehozásához.</span><span class="sxs-lookup"><span data-stu-id="f143a-139">Review your input and select **Run** to run the model and generate suggestions.</span></span>

1. <span data-ttu-id="f143a-140">Az ügyfélprofilok számától és a kijelölt tevékenységektől számától függően ez eltarthat néhány percig.</span><span class="sxs-lookup"><span data-stu-id="f143a-140">Depending on the number of customer profiles and selected activities, it can take a few minutes to complete.</span></span> 

<span data-ttu-id="f143a-141">A javaslatok létrehozása után szűrheti őket a dimenzió vagy a legérdekesebbnek tartott érték szerint.</span><span class="sxs-lookup"><span data-stu-id="f143a-141">After generating the suggestions, you can filter them by the dimension or value you're most interested in.</span></span> 

## <a name="view-details-of-a-suggested-segment"></a><span data-ttu-id="f143a-142">Javasolt szegmens részleteinek megtekintése</span><span class="sxs-lookup"><span data-stu-id="f143a-142">View details of a suggested segment</span></span>

<span data-ttu-id="f143a-143">A létrehozott javaslatok a **Szegmensek** > **Javaslatok (előzetes verzió)** részen, a **Tevékenységalapú javaslatok** szakaszban láthatók.</span><span class="sxs-lookup"><span data-stu-id="f143a-143">Once the suggestions are generated, you'll find them listed on **Segments** > **Suggestions (preview)** in the **Activity-based suggestions** section.</span></span>

:::image type="content" source="media/suggested-segments-details.png" alt-text="Egy javasolt szegmens részletes adatait mutató kibontott oldalpanel.":::

<span data-ttu-id="f143a-145">Az adott szegmens részleteinek megtekintéséhez válassza a **Javaslat megtekintése** lehetőséget egy javasolt szegmensnél.</span><span class="sxs-lookup"><span data-stu-id="f143a-145">Select **See suggestion** on a suggested segment to view the details of that segment.</span></span> <span data-ttu-id="f143a-146">Az oldalpanel olyan adatokat tartalmaz, mint például az egyes dimenziók célcsoporthoz viszonyított mérete.</span><span class="sxs-lookup"><span data-stu-id="f143a-146">The side pane provides details like the extent of each dimension in comparison to the target group.</span></span> <span data-ttu-id="f143a-147">Ezenkívül kiemeli a lehetséges tagok számát a szegmensben és a teljes ügyfelek közötti arányukat.</span><span class="sxs-lookup"><span data-stu-id="f143a-147">It also highlights the number of potential members in the segment and the corresponding percentage of the total customers.</span></span> <span data-ttu-id="f143a-148">Ha a javaslatot meg szeretné tartani szegmensként, válassza a **Szegmens létrehozása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="f143a-148">If you want to keep the suggestion as a segment, select **Create segment**.</span></span>    

## <a name="save-a-suggestion-as-a-segment"></a><span data-ttu-id="f143a-149">Javaslat mentése szegmensként</span><span class="sxs-lookup"><span data-stu-id="f143a-149">Save a suggestion as a segment</span></span>

1. <span data-ttu-id="f143a-150">Ugorjon a **Szegmensek** > **Javaslatok (előzetes verzió)** pontra.</span><span class="sxs-lookup"><span data-stu-id="f143a-150">Go to **Segments** > **Suggestions (preview)**.</span></span>

1. <span data-ttu-id="f143a-151">Válassza ki a menteni kívánt szegmenst.</span><span class="sxs-lookup"><span data-stu-id="f143a-151">Select the segment you want to save.</span></span> 

1. <span data-ttu-id="f143a-152">Az oldalpanelen válassza a **Szegmens létrehozása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="f143a-152">In the side pane, select **Create segment**.</span></span> 

1. <span data-ttu-id="f143a-153">A mentett szegmens megjelenik a **Minden szegmens** lapon lévő szegmenslistán. Most már [frissíthető és törölhetők, mint bármelyik más szegmens](segments.md).</span><span class="sxs-lookup"><span data-stu-id="f143a-153">After saving the segment, it will show in the list of segments on the **All segments** tab. It can now be [refreshed or deleted like any other segment](segments.md).</span></span> <span data-ttu-id="f143a-154">A szegmens részletei nem módosíthatók.</span><span class="sxs-lookup"><span data-stu-id="f143a-154">You can't edit the segment details.</span></span> <span data-ttu-id="f143a-155">A javaslatok bemeneti feltételei azonban megváltoztathatóak, és eltérő javaslatok is létrehozhatóak.</span><span class="sxs-lookup"><span data-stu-id="f143a-155">However, you can change the input criteria for the suggestions and generate different suggestions.</span></span>

## <a name="refresh-or-edit-a-set-of-suggestions"></a><span data-ttu-id="f143a-156">Javaslatok készletének frissítése és szerkesztése</span><span class="sxs-lookup"><span data-stu-id="f143a-156">Refresh or edit a set of suggestions</span></span>

1. <span data-ttu-id="f143a-157">Lépjen a **Szegmensek** > **Javaslatok (előzetes verzió)** részre, és keresse meg a szegmenst a **Tevékenységalapú javaslatok** szakaszban.</span><span class="sxs-lookup"><span data-stu-id="f143a-157">Go to **Segments** > **Suggestions (preview)** and look for the segment in the **Activity-based suggestions** section.</span></span>

1. <span data-ttu-id="f143a-158">Válassza a **Javaslatok frissítése** lehetőséget, a javaslatokat frissítéséhez, miközben a konfigurált attribútumokat megtartja.</span><span class="sxs-lookup"><span data-stu-id="f143a-158">Select **Refresh suggestions** to refresh the suggestions while keeping configured attributes.</span></span> <span data-ttu-id="f143a-159">Egy másik megoldás, hogy a **Javaslatok szerkesztése** lehetőséggel módosítja a konfigurált attribútumokat.</span><span class="sxs-lookup"><span data-stu-id="f143a-159">Or select **Edit suggestions** to modify the configured attributes.</span></span> <span data-ttu-id="f143a-160">A rendszer újrafuttatja a folyamatot, a legújabb adatok alapján szegmensjavaslatokat generál, és lecseréli az aktuális javaslatokat.</span><span class="sxs-lookup"><span data-stu-id="f143a-160">The system will rerun the process, generate segment suggestions based on the latest data, and replace the current suggestions.</span></span>

[!INCLUDE[footer-include](../includes/footer-banner.md)]
