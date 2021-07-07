---
title: Ügyfélprofilok bővítése a Microsoftból származó adatokkal
description: Használja a Microsoft tulajdonát képező adatokat az ügyféladatok márkahűséggel és érdeklődéssel való bővítésre.
ms.date: 06/14/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: kishorem-MS
ms.author: kishorem
manager: shellyha
ms.openlocfilehash: 1b11c325649b91ebb47cde924227eacedae64b7a
ms.sourcegitcommit: d84d664e67f263bfeb741154d309088c5101b9c3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/24/2021
ms.locfileid: "6305159"
---
# <a name="enrich-customer-profiles-with-brand-and-interest-affinities-preview"></a><span data-ttu-id="707e3-103">Az ügyfelek profiljainak bővítése márkahűséggel és érdeklődési körökkel (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="707e3-103">Enrich customer profiles with brand and interest affinities (preview)</span></span>

<span data-ttu-id="707e3-104">Használja a Microsoft tulajdonát képező adatokat az ügyféladatok márkahűséggel és érdeklődéssel való bővítésre.</span><span class="sxs-lookup"><span data-stu-id="707e3-104">Use Microsoft's proprietary data to enrich your customer data with brand and interest affinities.</span></span> <span data-ttu-id="707e3-105">Ezek az affinitások az Ön ügyfeleihez hasonló demográfiai jellemzőkkel rendelkező emberek adatain alapulnak.</span><span class="sxs-lookup"><span data-stu-id="707e3-105">These affinities are based on data from people with demographics similar to your customers.</span></span> <span data-ttu-id="707e3-106">Ez az információ segíti az ügyfelek jobb megértését és szegmentálásukban a márkahűségük és érdeklődésük alapján.</span><span class="sxs-lookup"><span data-stu-id="707e3-106">This information helps you to better understand and segment your customers based on their affinities to specific brands and interests.</span></span>

<span data-ttu-id="707e3-107">A célközönség-információkban lépjen az **Adatok** > **Bővítés** a [bővítések konfigurálásához és megtekintéséhez](enrichment-hub.md).</span><span class="sxs-lookup"><span data-stu-id="707e3-107">In audience insights, go to **Data** > **Enrichment** to [configure and view enrichments](enrichment-hub.md).</span></span>

<span data-ttu-id="707e3-108">A márkaaffinitások bővítésének konfigurálásához nyissa meg a **Felfedezés** lapot, és válassza a **Saját adatok bővítése** elemet a **Márkák** csempén.</span><span class="sxs-lookup"><span data-stu-id="707e3-108">To configure brand affinities enrichment, go to the **Discover** tab and select **Enrich my data** on the **Brands** tile.</span></span>

<span data-ttu-id="707e3-109">Az érdeklődésikör-affinitások bővítésének konfigurálásához nyissa meg a **Felfedezés** lapot, és válassza a **Saját adatok bővítése** elemet az **Érdeklődési körök** csempén.</span><span class="sxs-lookup"><span data-stu-id="707e3-109">To configure interest affinities enrichment, go to the **Discover** tab and select **Enrich my data** on the **Interests** tile.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="707e3-110">![Márkák és érdeklődési mozaikok](media/BrandsInterest-tile-Hub.png "Márkák és érdeklődési mozaikok")</span><span class="sxs-lookup"><span data-stu-id="707e3-110">![Brands and Interests tiles](media/BrandsInterest-tile-Hub.png "Brands and Interest tiles")</span></span>

## <a name="how-we-determine-affinities"></a><span data-ttu-id="707e3-111">Hogyan határozzuk meg a márkahűséget</span><span class="sxs-lookup"><span data-stu-id="707e3-111">How we determine affinities</span></span>

<span data-ttu-id="707e3-112">A Microsoft online keresési adatait használjuk fel különböző demográfiai szegmensek (kor, gender vagy hely szerint meghatározva) megkerséséhez, például márkahűség és érdeklődési kör.</span><span class="sxs-lookup"><span data-stu-id="707e3-112">We use Microsoft’s online search data to find affinities for brands and interests across various demographic segments (defined by age, gender, or location).</span></span> <span data-ttu-id="707e3-113">A márka vagy az érdeklődési kör online keresési mennyisége határozza meg, hogy egy demografikus szegmens mekkora hűséggel rendelkezik a többi szegmenssel összehasonlítva az adott márkához vagy érdeklődési körhöz.</span><span class="sxs-lookup"><span data-stu-id="707e3-113">The online search volume for a brand or interest determines how much affinity a demographic segment, compared to other segments, has to that brand or interest.</span></span>

## <a name="affinity-level-and-score"></a><span data-ttu-id="707e3-114">Affinitás szintje és pontszám</span><span class="sxs-lookup"><span data-stu-id="707e3-114">Affinity level and score</span></span>

<span data-ttu-id="707e3-115">Minden bővített ügyfélprofilon két kapcsolódó értéket biztosítunk: affinitás szintje és affinitás értéke.</span><span class="sxs-lookup"><span data-stu-id="707e3-115">On every enriched customer profile, we provide two related values: affinity level and affinity score.</span></span> <span data-ttu-id="707e3-116">Ezek az értékek segítenek annak meghatározásában, hogy milyen erős az affinitás profil demográfiai szegmensében a márkához vagy érdeklődési körhöz az egyéb demográfiai szegmensekkel összehasonlítva.</span><span class="sxs-lookup"><span data-stu-id="707e3-116">These values help you determine how strong the affinity is for that profile’s demographic segment, for a brand or interest, as compared to other demographic segments.</span></span>

<span data-ttu-id="707e3-117">Az *Affinitás szintje* négy szintből áll, és egy 100 pontos skálán számítja ki a rendszer az *affinitási pontszámot*, amely hozzárendeli az affintiási szinteket.</span><span class="sxs-lookup"><span data-stu-id="707e3-117">*Affinity level* consists of four levels and *affinity score* is calculated on a 100-point scale that maps to the affinity levels.</span></span>


|<span data-ttu-id="707e3-118">Affinitás szintje</span><span class="sxs-lookup"><span data-stu-id="707e3-118">Affinity level</span></span> |<span data-ttu-id="707e3-119">Affinitási pontszám</span><span class="sxs-lookup"><span data-stu-id="707e3-119">Affinity score</span></span>  |
|---------|---------|
|<span data-ttu-id="707e3-120">Nagyon magas</span><span class="sxs-lookup"><span data-stu-id="707e3-120">Very high</span></span>     | <span data-ttu-id="707e3-121">85-100</span><span class="sxs-lookup"><span data-stu-id="707e3-121">85-100</span></span>       |
|<span data-ttu-id="707e3-122">Magas</span><span class="sxs-lookup"><span data-stu-id="707e3-122">High</span></span>     | <span data-ttu-id="707e3-123">70-84</span><span class="sxs-lookup"><span data-stu-id="707e3-123">70-84</span></span>        |
|<span data-ttu-id="707e3-124">Közepes</span><span class="sxs-lookup"><span data-stu-id="707e3-124">Medium</span></span>     | <span data-ttu-id="707e3-125">35-69</span><span class="sxs-lookup"><span data-stu-id="707e3-125">35-69</span></span>        |
|<span data-ttu-id="707e3-126">Alacsony</span><span class="sxs-lookup"><span data-stu-id="707e3-126">Low</span></span>     | <span data-ttu-id="707e3-127">1-34</span><span class="sxs-lookup"><span data-stu-id="707e3-127">1-34</span></span>        |

<span data-ttu-id="707e3-128">Az affinitás méréséhez használt részletességtől függően használhatja az affinitás szintjét vagy a pontszámot is.</span><span class="sxs-lookup"><span data-stu-id="707e3-128">Depending on the granularity you would like for measuring the affinity, you can use either affinity level or score.</span></span> <span data-ttu-id="707e3-129">Pontosabban szabályozható az affinitási pontszám.</span><span class="sxs-lookup"><span data-stu-id="707e3-129">Affinity score gives you more precise control.</span></span>

## <a name="supported-countriesregions"></a><span data-ttu-id="707e3-130">Támogatott országok/régiók</span><span class="sxs-lookup"><span data-stu-id="707e3-130">Supported countries/regions</span></span>

<span data-ttu-id="707e3-131">Jelenleg a következő ország-/régió lehetőségeket támogatjuk: Ausztrália, Kanada (angol), Franciaország, Németország, Egyesült Királyság vagy Egyesült Államok (angol).</span><span class="sxs-lookup"><span data-stu-id="707e3-131">We currently support the following country/region options: Australia, Canada (English), France, Germany, United Kingdom, or United States (English).</span></span>

<span data-ttu-id="707e3-132">Ország vagy régió kiválasztásához nyissa meg a **Márkák bővítése** vagy **Érdeklődés bővítése** és válassza a **Változtat** lehetőséget az **Ország/Régió** mellett.</span><span class="sxs-lookup"><span data-stu-id="707e3-132">To select a country or region, open **Brands enrichment** or **Interest enrichment** and select **Change** next to **Country/Region**.</span></span> <span data-ttu-id="707e3-133">Az **Ország/régió beállításai** ablaktáblában válasszon egy beállítást, és válassza az **Alkalmaz** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="707e3-133">In the **Country/Region settings** pane, choose an option and select **Apply**.</span></span>

### <a name="implications-related-to-country-selection"></a><span data-ttu-id="707e3-134">Az országválasztással kapcsolatos következmények</span><span class="sxs-lookup"><span data-stu-id="707e3-134">Implications related to country selection</span></span>

- <span data-ttu-id="707e3-135">Saját [márkájának kiválasztásakor](#define-your-brands-or-interests) a rendszer a kiválasztott ország vagy régió alapján tesz javaslatokat.</span><span class="sxs-lookup"><span data-stu-id="707e3-135">When [choosing your own brands](#define-your-brands-or-interests), the system provides suggestions based on the selected country or region.</span></span>

- <span data-ttu-id="707e3-136">Egy [iparág kiválasztása](#define-your-brands-or-interests) esetén a kiválasztott ország vagy régió alapján megkapja a leginkább releváns márkákat és érdeklődési köröket.</span><span class="sxs-lookup"><span data-stu-id="707e3-136">When [choosing an industry](#define-your-brands-or-interests), you'll get the most relevant brands or interests based on the selected country or region.</span></span>

- <span data-ttu-id="707e3-137">A [profilok bővítésénél](#refresh-enrichment) minden olyan ügyfélprofilt bővítünk, amelynél adatokat kapunk a kiválasztott márkákhoz és érdeklődésekhez, tartalmazva a profilokat, amelyek nincsenek benne a kiválasztott országban vagy régióban.</span><span class="sxs-lookup"><span data-stu-id="707e3-137">When [enriching profiles](#refresh-enrichment), we'll enrich all customer profiles for which we get data for the selected brands and interests, including profiles that are not in the selected country or region.</span></span> <span data-ttu-id="707e3-138">Ha például Németországot választotta, akkor bővítjük az Egyesült Államokban található profilokat, ha rendelkezésre állnak adatok az Egyesült Államokban a kiválasztott márkákra és érdeklődésre.</span><span class="sxs-lookup"><span data-stu-id="707e3-138">For example, if you selected Germany, we'll enrich profiles located in the United States if we have data available for the selected brands and interests in the US.</span></span>

## <a name="configure-enrichment"></a><span data-ttu-id="707e3-139">A bővítés konfigurálása</span><span class="sxs-lookup"><span data-stu-id="707e3-139">Configure enrichment</span></span>

<span data-ttu-id="707e3-140">Az interaktív élmény végig segít Önnek a bővítések konfigurálásában.</span><span class="sxs-lookup"><span data-stu-id="707e3-140">A guided experience helps you through the configuration of the enrichments.</span></span> 

### <a name="define-your-brands-or-interests"></a><span data-ttu-id="707e3-141">Márkák vagy érdeklődési körök megadása</span><span class="sxs-lookup"><span data-stu-id="707e3-141">Define your brands or interests</span></span>

<span data-ttu-id="707e3-142">Válasszon legfeljebb öt márkát vagy érdeklődési kört az alábbi lehetőségek egyikének vagy mindkettőnek a használatával:</span><span class="sxs-lookup"><span data-stu-id="707e3-142">Choose up to five brands or interests using one or both of these options:</span></span>

- <span data-ttu-id="707e3-143">**Iparág**: válassza ki saját iparágát a legördülő listából, majd válasszon a csúcsmárkákból vagy érdeklődési körökből ezt az iparágat illetően.</span><span class="sxs-lookup"><span data-stu-id="707e3-143">**Industry**: Select your industry from the dropdown list and then choose from the top brands or interests for that industry.</span></span>
- <span data-ttu-id="707e3-144">**Válassza ki a sajátját**: Adjon meg egy, a szervezet számára releváns márkát vagy érdeklődési kört, majd válasszon a megfelelő javaslatok közül.</span><span class="sxs-lookup"><span data-stu-id="707e3-144">**Choose your own**: Enter a brand or interest that is relevant to your organization and then choose from the matching suggestions.</span></span> <span data-ttu-id="707e3-145">Ha a keresett márkát vagy érdeklődési kört nem sorolja fel a rendszer, küldjön visszajelzést a **Javaslat** hivatkozás segítségével.</span><span class="sxs-lookup"><span data-stu-id="707e3-145">If we don't list a brand or interest you're looking for, send us feedback using the **Suggest** link.</span></span>

### <a name="review-enrichment-preferences"></a><span data-ttu-id="707e3-146">Bővítési beállítások áttekintése</span><span class="sxs-lookup"><span data-stu-id="707e3-146">Review enrichment preferences</span></span>

<span data-ttu-id="707e3-147">Tekintse át az alapértelmezett bővítési beállításokat, és szükség szerint frissítse azokat.</span><span class="sxs-lookup"><span data-stu-id="707e3-147">Review your default enrichment preferences and update them as needed.</span></span>

:::image type="content" source="media/affinity-enrichment-preferences.png" alt-text="Képernyőkép a bővítési beállítások ablakáról.":::

### <a name="select-entity-to-enrich"></a><span data-ttu-id="707e3-149">Entitás kiválasztása bővítéshez</span><span class="sxs-lookup"><span data-stu-id="707e3-149">Select entity to enrich</span></span>

<span data-ttu-id="707e3-150">Válassza a **Bővített entitás** lehetőséget, és válassza a Microsoft vállalati adataival gyarapítani kívánt entitásokat.</span><span class="sxs-lookup"><span data-stu-id="707e3-150">Select **Enriched entity** and choose the data set you want to enrich with company data from the Microsoft.</span></span> <span data-ttu-id="707e3-151">Kiválaszthatja a Vevő entitást az összes ügyfélprofil gazdagítására, vagy kiválaszthat egy szegmens entitást, amely csak az adott szegmensben található vevőprofilokat gazdagítja.</span><span class="sxs-lookup"><span data-stu-id="707e3-151">You can select the Customer entity to enrich all your customer profiles or select a segment entity to enrich only customer profiles contained in that segment.</span></span>

### <a name="map-your-fields"></a><span data-ttu-id="707e3-152">Mezők megfeleltetése</span><span class="sxs-lookup"><span data-stu-id="707e3-152">Map your fields</span></span>

<span data-ttu-id="707e3-153">A egyesített ügyfélentitás mezőinek leképezésével meghatározhatja, hogy a rendszer az ügyféladatok gyarapítására melyik demográfiai szegmenst használja.</span><span class="sxs-lookup"><span data-stu-id="707e3-153">Map fields from your unified customer entity to define the demographic segment you want the system to use for enriching your customer data.</span></span> <span data-ttu-id="707e3-154">Ország/régió leképezése, és legalább a születési dátum vagy nem attribútumát.</span><span class="sxs-lookup"><span data-stu-id="707e3-154">Map Country/Region and at least Date of Birth or Gender attributes.</span></span> <span data-ttu-id="707e3-155">Ezenkívül le kell képeznie legalább egy várost (és államot/tartományt) vagy irányítószámot.</span><span class="sxs-lookup"><span data-stu-id="707e3-155">Additionally, you must map at least one of City (and State/Province) or Postal code.</span></span> <span data-ttu-id="707e3-156">Válassza a **Szerkesztés** lehetőséget a mezők leképezésének definiálásához, és válassza az **Alkalmazás** lehetőséget, amikor elkészült.</span><span class="sxs-lookup"><span data-stu-id="707e3-156">Select **Edit** to define the mapping of the fields and select **Apply** when you're done.</span></span> <span data-ttu-id="707e3-157">Válassza a **Mentés** lehetőséget a mezők leképezésének végrehajtásához.</span><span class="sxs-lookup"><span data-stu-id="707e3-157">Select **Save** to complete the field mapping.</span></span>

<span data-ttu-id="707e3-158">A következő formátumok és értékek támogatottak (az értékek nem különböztetik meg a kis- és nagybetűket):</span><span class="sxs-lookup"><span data-stu-id="707e3-158">The following formats and values are supported (values are not case-sensitive):</span></span>

- <span data-ttu-id="707e3-159">**Születési dátum**: Azt ajánljuk, hogy az adatok betöltése során a születési dátumot a rendszer datetime típusúra alakítsa.</span><span class="sxs-lookup"><span data-stu-id="707e3-159">**Date of Birth**: We recommend that date of birth is converted to DateTime type during data ingestion.</span></span> <span data-ttu-id="707e3-160">Másik lehetőségként sztring lehet [ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html) "yyyy-MM-ddd" vagy "yyyy-MM-ddTHH:mm:ss" formátumban.</span><span class="sxs-lookup"><span data-stu-id="707e3-160">Alternatively, it can be a string in [ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html) format "yyyy-MM-dd" or "yyyy-MM-ddTHH:mm:ss".</span></span>
- <span data-ttu-id="707e3-161">**Nem**: férfi, nő, ismeretlen.</span><span class="sxs-lookup"><span data-stu-id="707e3-161">**Gender**: Male, Female, Unknown.</span></span>
- <span data-ttu-id="707e3-162">**Irányítószám**: Ötjegyű irányítószámok az Egyesült Államok számára, standard irányítószám mindenhol máshol.</span><span class="sxs-lookup"><span data-stu-id="707e3-162">**Postal code**: Five-digit ZIP codes for United States, standard postal code everywhere else.</span></span>
- <span data-ttu-id="707e3-163">**Város**: A város neve angolul.</span><span class="sxs-lookup"><span data-stu-id="707e3-163">**City**: City name in English.</span></span>
- <span data-ttu-id="707e3-164">**Állam/megye**: Két betűs rövidítés az Egyesült Államok és Kanada esetében.</span><span class="sxs-lookup"><span data-stu-id="707e3-164">**State/Province**: Two-letter abbreviation for the US and Canada.</span></span> <span data-ttu-id="707e3-165">Két- vagy három betűs rövidítés Ausztrália esetében.</span><span class="sxs-lookup"><span data-stu-id="707e3-165">Two- or three-letter abbreviation for Australia.</span></span> <span data-ttu-id="707e3-166">Franciaország, Németország és az Egyesült Királyság esetében nem alkalmazható.</span><span class="sxs-lookup"><span data-stu-id="707e3-166">Not applicable for France, Germany, or the UK.</span></span>
- <span data-ttu-id="707e3-167">**Ország/régió**:</span><span class="sxs-lookup"><span data-stu-id="707e3-167">**Country/Region**:</span></span>

  - <span data-ttu-id="707e3-168">USA: Amerikai Egyesült Államok, Egyesült Államok, USA, US, Amerika</span><span class="sxs-lookup"><span data-stu-id="707e3-168">US: United States of America, United States, USA, US, America</span></span>
  - <span data-ttu-id="707e3-169">CA: Kanada, CA</span><span class="sxs-lookup"><span data-stu-id="707e3-169">CA: Canada, CA</span></span>
  - <span data-ttu-id="707e3-170">GB: Egyesült Királyság, UK, Nagy-Britannia, GB, Nagy-Britannia és Észak-Írország Egyesült Királysága, Nagy-Britannia Egyesült Királysága</span><span class="sxs-lookup"><span data-stu-id="707e3-170">GB: United Kingdom, UK, Great Britain, GB, United Kingdom of Great Britain and Northern Ireland, United Kingdom of Great Britain</span></span>
  - <span data-ttu-id="707e3-171">AU: Ausztrália, AU, Ausztrália, Ausztrál Nemzetközösség</span><span class="sxs-lookup"><span data-stu-id="707e3-171">AU: Australia, AU, Commonwealth of Australia</span></span>
  - <span data-ttu-id="707e3-172">FR: Franciaország, Francia Köztársaság</span><span class="sxs-lookup"><span data-stu-id="707e3-172">FR: France, FR, French Republic</span></span>
  - <span data-ttu-id="707e3-173">DE: Németország, német, Deutschland, Allemagne, DE, Német Szövetségi Köztársaság, Német Köztársaság</span><span class="sxs-lookup"><span data-stu-id="707e3-173">DE: Germany, German, Deutschland, Allemagne, DE, Federal Republic of Germany, Republic of Germany</span></span>

## <a name="review-and-name-the-enrichment"></a><span data-ttu-id="707e3-174">A bővítés áttekintése és elnevezése</span><span class="sxs-lookup"><span data-stu-id="707e3-174">Review and name the enrichment</span></span>

<span data-ttu-id="707e3-175">Végül áttekintheti az információkat, és nevet adhat a bővítésnek.</span><span class="sxs-lookup"><span data-stu-id="707e3-175">Finally, you get to review the information and provide a name for the enrichment.</span></span>

:::image type="content" source="media/enrichment-interests-summary.png" alt-text="Az érdeklődési kör áttekintése és elnevezési oldal.":::

## <a name="refresh-enrichment"></a><span data-ttu-id="707e3-177">A bővítés frissítése</span><span class="sxs-lookup"><span data-stu-id="707e3-177">Refresh enrichment</span></span>

<span data-ttu-id="707e3-178">Futtassa a bővítést a márkák, érdeklődési körök konfigurálása és a mezők demográfiai adatokra vonatkozó leképezése után.</span><span class="sxs-lookup"><span data-stu-id="707e3-178">Run the enrichment after configuring brands, interests, and the field mapping for demographics.</span></span> <span data-ttu-id="707e3-179">A folyamat megkezdéséhez válassza a márka vagy az érdeklődési kör konfigurációja lapon a **Futtatás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="707e3-179">To start the process, select **Run** on the brand or interest configuration page.</span></span> <span data-ttu-id="707e3-180">Emellett a rendszer automatikusan is futtathatja a dúsítást egy ütemezett frissítés részeként.</span><span class="sxs-lookup"><span data-stu-id="707e3-180">Additionally, you can let the system run the enrichment automatically as part of a scheduled refresh.</span></span>

<span data-ttu-id="707e3-181">Az ügyféladatok méretétől függően előfordulhat, hogy a bővítés futtatása néhány percig is eltarthat.</span><span class="sxs-lookup"><span data-stu-id="707e3-181">Depending on the size of your customer data, it may take several minutes for an enrichment run to complete.</span></span>

> [!TIP]
> <span data-ttu-id="707e3-182">A feladatokhoz/folyamatokhoz [hatféle állapot](system.md#status-types) tartozhat.</span><span class="sxs-lookup"><span data-stu-id="707e3-182">There are [six types of status](system.md#status-types) for tasks/processes.</span></span> <span data-ttu-id="707e3-183">Emellett a legtöbb folyamat [más alsóbb szintű folyamatoktól is függ](system.md#refresh-policies).</span><span class="sxs-lookup"><span data-stu-id="707e3-183">Additionally, most processes [depend on other downstream processes](system.md#refresh-policies).</span></span> <span data-ttu-id="707e3-184">Kiválaszthatja egy folyamat állapotát, és megtekintheti a hozzá tartozó teljes feladat folyamatának részleteit.</span><span class="sxs-lookup"><span data-stu-id="707e3-184">You can select the status of a process to see details on the progress of the entire job.</span></span> <span data-ttu-id="707e3-185">A Feladat egyik feladatának **Lásd részletek** kiválasztása után további információkat talál: feldolgozási idő, utolsó feldolgozási dátum, valamint a feladathoz kapcsolódó összes hiba és figyelmeztetés.</span><span class="sxs-lookup"><span data-stu-id="707e3-185">After selecting **See details** for one of the job's tasks, you'll find additional information: processing time, the last processing date, and all errors and warnings associated with the task.</span></span>

## <a name="enrichment-results"></a><span data-ttu-id="707e3-186">Bővítési eredmények</span><span class="sxs-lookup"><span data-stu-id="707e3-186">Enrichment results</span></span>

<span data-ttu-id="707e3-187">A bővítési folyamat futtatása után lépjen a **Saját bővítések** pontra, és nézze át a bővített ügyfelek teljes számát és a márkák vagy érdeklődési körök lebontását a bővített ügyfelek profiljaiban.</span><span class="sxs-lookup"><span data-stu-id="707e3-187">After running the enrichment process, go to **My enrichments** to review the total number of enriched customers and a breakdown of brands or interests in the enriched customer profiles.</span></span>

:::image type="content" source="media/my-enrichments.png" alt-text="Az eredmények előnézete a bővítési folyamat futtatása után":::

<span data-ttu-id="707e3-189">A bővített adatok áttekintéséhez jelölje be a **Bővített adatok megtekintése** lehetőséget a diagramban.</span><span class="sxs-lookup"><span data-stu-id="707e3-189">Review the enriched data by selecting **View enriched data** in the chart.</span></span> <span data-ttu-id="707e3-190">A márkák bővített adatai a **BrandAffinityFromMicrosoft** entitásba kerülnek.</span><span class="sxs-lookup"><span data-stu-id="707e3-190">Enriched data for brands goes to the **BrandAffinityFromMicrosoft** entity.</span></span> <span data-ttu-id="707e3-191">Az érdeklődési körök adatai az **InterestAffinityFromMicrosoft** entitásba kerülnek.</span><span class="sxs-lookup"><span data-stu-id="707e3-191">Data for interests is in the **InterestAffinityFromMicrosoft** entity.</span></span> <span data-ttu-id="707e3-192">Ezeket az entitásokat a **Bővítés** csoportban is megtekintheti az **Adatok** > **Entitások** helyen.</span><span class="sxs-lookup"><span data-stu-id="707e3-192">You'll also find these entities listed in the **Enrichment** group in **Data** > **Entities**.</span></span>

## <a name="see-enrichment-data-on-the-customer-card"></a><span data-ttu-id="707e3-193">A bővítési adatok megtekintése az ügyfélkártyán</span><span class="sxs-lookup"><span data-stu-id="707e3-193">See enrichment data on the customer card</span></span>

<span data-ttu-id="707e3-194">A márka és a érdeklődés affinitásokat az ügyfélkártyákon is meg lehet tekinteni.</span><span class="sxs-lookup"><span data-stu-id="707e3-194">Brand and interest affinities can also be viewed on individual customer cards.</span></span> <span data-ttu-id="707e3-195">Nyissa meg az **Ügyfelek** lehetőséget, és válassza ki az ügyfél profilját.</span><span class="sxs-lookup"><span data-stu-id="707e3-195">Go to **Customers** and select a customer profile.</span></span> <span data-ttu-id="707e3-196">Az ügyfélkártyán megkeresheti a márkákra vagy az érdeklődési körökre vonatkozó diagramokat, amelyek szerint az adott ügyfél demográfiai profiljához tartozó személyek affinitással rendelkeznek.</span><span class="sxs-lookup"><span data-stu-id="707e3-196">In the customer card, you'll find charts for the brands or interests that people in that customer's demographic profile have affinity for.</span></span>

:::image type="content" source="media/enrichment-customer-card.png" alt-text="Bővített adatokkal rendelkező ügyfél-kártya":::

## <a name="next-steps"></a><span data-ttu-id="707e3-198">Következő lépések</span><span class="sxs-lookup"><span data-stu-id="707e3-198">Next steps</span></span>

<span data-ttu-id="707e3-199">Építsen a bővített ügyféladatokra.</span><span class="sxs-lookup"><span data-stu-id="707e3-199">Build on top of your enriched customer data.</span></span> <span data-ttu-id="707e3-200">Hozzon létre [szegmenseket](segments.md) és [intézkedéseket](measures.md), továbbá [exportálja az adatokat](export-destinations.md) , hogy személyre szabott élményt nyújtson ügyfeleinek.</span><span class="sxs-lookup"><span data-stu-id="707e3-200">Create [Segments](segments.md) and [Measures](measures.md), and even [export the data](export-destinations.md) to deliver personalized experiences to your customers.</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]
