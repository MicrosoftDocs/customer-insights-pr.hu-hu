---
title: Hasonló ügyfelek keresése AI-val
description: Hasonló ügyfél-szegmensek keresése mesterséges intelligenciával.
ms.date: 06/25/2020
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
ms.reviewer: jimsonc
manager: shellyha
ms.openlocfilehash: b9b2e7fa862b595c6a364a7208e42295b4f9df83
ms.sourcegitcommit: 139548f8a2d0f24d54c4a6c404a743eeeb8ef8e0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/15/2021
ms.locfileid: "5268873"
---
# <a name="similar-customers-preview"></a><span data-ttu-id="1773c-103">Hasonló ügyfelek (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="1773c-103">Similar Customers (preview)</span></span>

<span data-ttu-id="1773c-104">Ez a funkció lehetővé teszi, hogy a hasonló ügyfeleket keressen meg az ügyfélkörön belül mesterséges intelligencia segítségével.</span><span class="sxs-lookup"><span data-stu-id="1773c-104">This feature lets you find similar customers in your customer base using artificial intelligence.</span></span> <span data-ttu-id="1773c-105">A szolgáltatás használatához legalább egy szegmensnek létre kell lennie hozva.</span><span class="sxs-lookup"><span data-stu-id="1773c-105">You need to have at least one segment created to use this feature.</span></span> <span data-ttu-id="1773c-106">A meglévő szegmens feltételeinek kibővítésével a szegmenshez hasonló ügyfelek kereshetők meg.</span><span class="sxs-lookup"><span data-stu-id="1773c-106">Expanding the criteria of an existing segment help find customers that are similar to that segment.</span></span>

> [!NOTE]
> <span data-ttu-id="1773c-107">A *Hasonló ügyfelek megkeresése* automatizált eszközöket használ az adatok értékelésére és az előrejelzések készítéséhez az adatok alapján, és így egy olyan képessége van, ami profilalkotáshoz használható az Általános adatvédelmi rendelet („GDPR”) definíciója szerint.</span><span class="sxs-lookup"><span data-stu-id="1773c-107">*Find similar customers* uses automated means to evaluate data and make predictions based on that data, and therefore has the capability to be used as a method of profiling, as that term is defined by the General Data Protection Regulation (“GDPR”).</span></span> <span data-ttu-id="1773c-108">Ha az ügyfél ezt a funkciót adatok feldolgozására használja, az a GDPR vagy más törvények és szabályozások hatálya alá tartozhat.</span><span class="sxs-lookup"><span data-stu-id="1773c-108">Customer’s use of this feature to process data may be subject to GDPR or other laws or regulations.</span></span> <span data-ttu-id="1773c-109">Felelős azért, hogy biztosítsa, hogy a Dynamics 365 Customer Insights használata, az előrejelzésekkel együtt, megfelel a vonatkozó törvényeknek és szabályozásoknak, többek között az adatvédelemmel, személyes adatokkal, biometrikus adatokkal, adatok védelmével és a kommunikáció titkosságával kapcsolatos törvényeknek.</span><span class="sxs-lookup"><span data-stu-id="1773c-109">You are responsible for ensuring that your use of Dynamics 365 Customer Insights, including predictions, complies with all applicable laws and regulations, including laws related to privacy, personal data, biometric data, data protection, and confidentiality of communications.</span></span>

## <a name="finding-similar-customers"></a><span data-ttu-id="1773c-110">Hasonló ügyfelek keresése</span><span class="sxs-lookup"><span data-stu-id="1773c-110">Finding similar customers</span></span>

1. <span data-ttu-id="1773c-111">A célközönség-információkban lépjen a **Szegmensek** lehetőségre, és válassza a szegmenst, amelyre az új szegmenst alapozni szeretné.</span><span class="sxs-lookup"><span data-stu-id="1773c-111">In audience insights, go to **Segments** and select the segment you want to base your new segment on.</span></span> <span data-ttu-id="1773c-112">Ez a *Forrásszegmense*.</span><span class="sxs-lookup"><span data-stu-id="1773c-112">That's your *source segment*.</span></span>

1. <span data-ttu-id="1773c-113">A műveleti sávban válassza a **Hasonló ügyfelek keresése** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="1773c-113">In the action bar, select **Find similar customers**.</span></span>

1. <span data-ttu-id="1773c-114">Tekintse át az új szegmens javasolt nevét, és szükség szerint módosítsa azt.</span><span class="sxs-lookup"><span data-stu-id="1773c-114">Review the suggested name for your new segment and change it if necessary.</span></span>

1. <span data-ttu-id="1773c-115">Tekintse át az új szegmenst definiáló mezőket.</span><span class="sxs-lookup"><span data-stu-id="1773c-115">Review the fields that define your new segment.</span></span> <span data-ttu-id="1773c-116">Ezek a mezők határozzák meg, hogy a rendszer milyen alapon próbálja megkeresni a hasonló ügyfeleket a forrásszegmensében.</span><span class="sxs-lookup"><span data-stu-id="1773c-116">These fields define the basis on which the system will try to find similar customers to your source segment.</span></span> <span data-ttu-id="1773c-117">A rendszer alapértelmezés szerint az ajánlott mezőket választja ki.</span><span class="sxs-lookup"><span data-stu-id="1773c-117">The system will select recommended fields by default.</span></span>
  <span data-ttu-id="1773c-118">A modell teljesítményét jelentősen csökkentő mezők automatikusan ki vannak zárva:</span><span class="sxs-lookup"><span data-stu-id="1773c-118">Fields that can significantly reduce the model performance are automatically excluded:</span></span>
  
   - <span data-ttu-id="1773c-119">A következő adattípusú mezők: StringType, BooleanType, CharType, LongType, IntType, DoubleType, FloatType, ShortType</span><span class="sxs-lookup"><span data-stu-id="1773c-119">Fields with the following data types: StringType, BooleanType, CharType, LongType, IntType, DoubleType, FloatType, ShortType</span></span>
   - <span data-ttu-id="1773c-120">A 2 nél kevesebb vagy 30-nál nagyobb számosságú (a mező elemeinek száma) mezők</span><span class="sxs-lookup"><span data-stu-id="1773c-120">Fields with a cardinality (the number of elements in a field) of less than 2 or more than 30</span></span>

1. <span data-ttu-id="1773c-121">Válassza ki, hogy az **Összes ügyfelet** vagy csak az új szegmens egy **Adott meglévő szegmensében** szereplő ügyfeleket kívánja-e felvenni.</span><span class="sxs-lookup"><span data-stu-id="1773c-121">Choose if you want to include **All customers** or only customers in a **Specific existing segment** in your new segment.</span></span>

1. <span data-ttu-id="1773c-122">Kizárhatja a szegmensben lévő ügyfeleket, ha bejelöli a **Mindenki kizárása a forrásszegmensben** jelölőnégyzetet.</span><span class="sxs-lookup"><span data-stu-id="1773c-122">Exclude customers in your source segment by selecting the **Exclude everyone in source segment** checkbox.</span></span>

1. <span data-ttu-id="1773c-123">A rendszer alapértelmezés szerint azt javasolja, hogy a kimenetében a célközönség legfeljebb 20%-át adja meg.</span><span class="sxs-lookup"><span data-stu-id="1773c-123">By default, the system suggests including only 20% of the target audience size in your output.</span></span> <span data-ttu-id="1773c-124">Szükség szerint szerkessze ezt a küszöböt.</span><span class="sxs-lookup"><span data-stu-id="1773c-124">Edit this threshold as needed.</span></span> <span data-ttu-id="1773c-125">A küszöb növelése csökkenti a pontosságot.</span><span class="sxs-lookup"><span data-stu-id="1773c-125">Increasing the threshold will reduce the precision.</span></span>

1. <span data-ttu-id="1773c-126">Válassza az oldal alján található **Futtatás** lehetőséget, hogy egy bináris osztályozási feladatot (a gépi tanulás egy módszere) indítson el, amely elemzi az adatkészletet.</span><span class="sxs-lookup"><span data-stu-id="1773c-126">Select **Run** at the bottom of the page to start a binary classification task (a method of machine learning) which analyzes the dataset.</span></span>

## <a name="view-the-similar-segment"></a><span data-ttu-id="1773c-127">A hasonló szegmens megtekintése</span><span class="sxs-lookup"><span data-stu-id="1773c-127">View the similar segment</span></span>

<span data-ttu-id="1773c-128">A hasonló szegmens feldolgozását követően megtalálja az új szegmenst a **Szegmensek** oldalon.</span><span class="sxs-lookup"><span data-stu-id="1773c-128">After processing the similar segment, you'll find the new segment listed on the **Segments** page.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="1773c-129">![Hasonló ügyfelek szegmens](media/expanded-segment.png "Hasonló ügyfelek szegmens")</span><span class="sxs-lookup"><span data-stu-id="1773c-129">![Similar customers segment](media/expanded-segment.png "Similar customers segment")</span></span>

<span data-ttu-id="1773c-130">A szegmens részleteinek megnyitásához válassza a **Nézet** lehetőséget a műveleti sávban.</span><span class="sxs-lookup"><span data-stu-id="1773c-130">Select **View** in the action bar to open the segment detail.</span></span> <span data-ttu-id="1773c-131">Ez a nézet a [hasonlósági pontszámok](#about-similarity-scores) közötti eredményeloszlásra vonatkozó információkat tartalmaz .</span><span class="sxs-lookup"><span data-stu-id="1773c-131">This view contains information about the result distribution across [similarity scores](#about-similarity-scores).</span></span> <span data-ttu-id="1773c-132">Emellett megtalálja a hasonlóságok pontszámát is a **Szegmens tagok előnézete** részben.</span><span class="sxs-lookup"><span data-stu-id="1773c-132">You'll also find the similarity score values in the **Segment members preview**.</span></span>

## <a name="use-the-output-of-a-similar-segment"></a><span data-ttu-id="1773c-133">Hasonló szegmens kimenetének használata</span><span class="sxs-lookup"><span data-stu-id="1773c-133">Use the output of a similar segment</span></span>

<span data-ttu-id="1773c-134">A többi szegmenshez hasonlóan [egy hasonló szegmens kimenetével is dolgozhat](segments.md).</span><span class="sxs-lookup"><span data-stu-id="1773c-134">You can [work with the output of a similar segment](segments.md) as you do with other segments.</span></span> <span data-ttu-id="1773c-135">Exportálja például a szegmenst, vagy kiépíthet egy mérőszámot.</span><span class="sxs-lookup"><span data-stu-id="1773c-135">For example, export the segment or build a measure.</span></span>

## <a name="refresh-and-edit-a-similar-segment"></a><span data-ttu-id="1773c-136">Hasonló szegmens frissítése és szerkesztése</span><span class="sxs-lookup"><span data-stu-id="1773c-136">Refresh and edit a similar segment</span></span>

<span data-ttu-id="1773c-137">Hasonló szegmens frissítéséhez jelölje ki azt a **Szegmensek** oldalon, majd a műveleti sávban válassza a **Frissítés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="1773c-137">To refresh a similar segment, select it on the **Segments** page and select **Refresh** in the action bar.</span></span>

<span data-ttu-id="1773c-138">A hasonló szegmensek szerkesztése újra feldolgozza az adatait.</span><span class="sxs-lookup"><span data-stu-id="1773c-138">Editing a similar segment will reprocess your data.</span></span> <span data-ttu-id="1773c-139">A korábban létrehozott szegmens frissülni a frissített adatokkal.</span><span class="sxs-lookup"><span data-stu-id="1773c-139">The previously created segment gets updated with refreshed data.</span></span>    
<span data-ttu-id="1773c-140">Hasonló szegmens szerkesztéséhez jelölje ki azt a **Szegmensek** oldalon, majd a műveleti sávban válassza a **Szerkesztés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="1773c-140">To edit a similar segment, select it on the **Segments** page and select **Edit** in the action bar.</span></span> <span data-ttu-id="1773c-141">Alkalmazza a módosításokat, és a feldolgozás megkezdéséhez válassza a **Futtatás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="1773c-141">Apply your changes and select **Run** to start the processing.</span></span>

## <a name="delete-a-similar-segment"></a><span data-ttu-id="1773c-142">Hasonló szegmens törlése</span><span class="sxs-lookup"><span data-stu-id="1773c-142">Delete a similar segment</span></span>

<span data-ttu-id="1773c-143">Jelölje ki a szegmenst a **Szegmensek** oldalon, majd a műveleti sávban válassza a **Törlés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="1773c-143">Select the segment on the **Segments** page and select **Delete** in the action bar.</span></span> <span data-ttu-id="1773c-144">Majd hagyja jóvá a törlést.</span><span class="sxs-lookup"><span data-stu-id="1773c-144">Then, confirm your deletion.</span></span>

## <a name="about-similarity-scores"></a><span data-ttu-id="1773c-145">A hasonlósági pontszámokról</span><span class="sxs-lookup"><span data-stu-id="1773c-145">About similarity scores</span></span>

<span data-ttu-id="1773c-146">A bináris besorolású gépi tanulási modell egy pontszámot rendel hozzá a hasonló szegmensben lévő ügyfelekhez.</span><span class="sxs-lookup"><span data-stu-id="1773c-146">The binary classification machine learning model assigns a score to customers in the similar segment.</span></span> <span data-ttu-id="1773c-147">A pontszám a forrás-szegmensben lévő ügyfelekhez való hasonlóságon alapul.</span><span class="sxs-lookup"><span data-stu-id="1773c-147">The score is based on the similarity to customers in the source segment.</span></span>

- <span data-ttu-id="1773c-148">A 0,55 alatti hasonlósági pontszámmal rendelkező ügyfelek *nem hasonlóként* vannak besorolva a forrásszegmensben található ügyfelekhez</span><span class="sxs-lookup"><span data-stu-id="1773c-148">Similarity scores below 0.55 are customers the system classified as *not similar* to customers in the source segment</span></span>
- <span data-ttu-id="1773c-149">A 0,55 – 0,7 közötti hasonlósági pontszámok *némileg hasonlónak* minősülnek</span><span class="sxs-lookup"><span data-stu-id="1773c-149">Similarity scores between 0.55 – 0.7 are classified as *somewhat similar*</span></span>
- <span data-ttu-id="1773c-150">A 0,7 – 0,85 közötti hasonlósági pontszámok *hasonlónak* minősülnek</span><span class="sxs-lookup"><span data-stu-id="1773c-150">Similarity scores between 0.7 – 0.85 are classified as *similar*</span></span>
- <span data-ttu-id="1773c-151">A 0,85 – 1 között hasonlósági pontszámok az olyan ügyfelek, amelyeket a rendszer *nagyon hasonlónak* minősített</span><span class="sxs-lookup"><span data-stu-id="1773c-151">Similarity scores between 0.85 – 1 are customers the system classified as *very similar*</span></span>

<span data-ttu-id="1773c-152">A 0,4 alatti hasonlósági pontszámú ügyfelek nem szerepelnek a modell kimenetében.</span><span class="sxs-lookup"><span data-stu-id="1773c-152">Customers with similarity scores below 0.4 aren't included in the model output.</span></span> <span data-ttu-id="1773c-153">A rendszer ezeket nem tartja eléggé hasonlónak a forrásszegmenshez.</span><span class="sxs-lookup"><span data-stu-id="1773c-153">The system doesn't consider them similar enough to the source segment.</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]