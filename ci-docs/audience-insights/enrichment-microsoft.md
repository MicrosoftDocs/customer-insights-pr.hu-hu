---
title: Ügyfélprofilok bővítése a Microsoftból származó adatokkal
description: Használja a Microsoft tulajdonát képező adatokat az ügyféladatok márkahűséggel és érdeklődéssel való bővítésre.
ms.date: 04/09/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: kishorem-MS
ms.author: kishorem
manager: shellyha
ms.openlocfilehash: be042dd139607849b795c903fa58da2edb9ff589
ms.sourcegitcommit: 72603fb39c4d5dbca71128815a2e1692542ea4dc
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/19/2021
ms.locfileid: "6064894"
---
# <a name="enrich-customer-profiles-with-brand-and-interest-affinities-preview"></a><span data-ttu-id="426e2-103">Az ügyfelek profiljainak bővítése márkahűséggel és érdeklődési körökkel (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="426e2-103">Enrich customer profiles with brand and interest affinities (preview)</span></span>

<span data-ttu-id="426e2-104">Használja a Microsoft tulajdonát képező adatokat az ügyféladatok márkahűséggel és érdeklődéssel való bővítésre.</span><span class="sxs-lookup"><span data-stu-id="426e2-104">Use Microsoft's proprietary data to enrich your customer data with brand and interest affinities.</span></span> <span data-ttu-id="426e2-105">Ezeket az affinitásokat az ügyfelekihez hasonló demográfiai adatokkal rendelkező emberek adatai alapján határozzák meg.</span><span class="sxs-lookup"><span data-stu-id="426e2-105">These affinities are determined based on data from people with similar demographics to your customers.</span></span> <span data-ttu-id="426e2-106">Ez az információ segíti az ügyfelek jobb megértését és szegmentálásukban a márkahűségük és érdeklődésük alapján.</span><span class="sxs-lookup"><span data-stu-id="426e2-106">This information helps you to better understand and segment your customers based on their affinities to specific brands and interests.</span></span>

<span data-ttu-id="426e2-107">A célközönség-információkban lépjen az **Adatok** > **Bővítés** a [bővítések konfigurálásához és megtekintéséhez](enrichment-hub.md).</span><span class="sxs-lookup"><span data-stu-id="426e2-107">In audience insights, go to **Data** > **Enrichment** to [configure and view enrichments](enrichment-hub.md).</span></span>

<span data-ttu-id="426e2-108">A márkaaffinitások bővítésének konfigurálásához nyissa meg a **Felfedezés** lapot, és válassza a **Saját adatok bővítése** elemet a **Márkák** csempén.</span><span class="sxs-lookup"><span data-stu-id="426e2-108">To configure brand affinities enrichment, go to the **Discover** tab and select **Enrich my data** on the **Brands** tile.</span></span>

<span data-ttu-id="426e2-109">Az érdeklődésikör-affinitások bővítésének konfigurálásához nyissa meg a **Felfedezés** lapot, és válassza a **Saját adatok bővítése** elemet az **Érdeklődési körök** csempén.</span><span class="sxs-lookup"><span data-stu-id="426e2-109">To configure interest affinities enrichment, go to the **Discover** tab and select **Enrich my data** on the **Interests** tile.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="426e2-110">![Márkák és érdeklődési mozaikok](media/BrandsInterest-tile-Hub.png "Márkák és érdeklődés mozaikok")</span><span class="sxs-lookup"><span data-stu-id="426e2-110">![Brands & Interests tiles](media/BrandsInterest-tile-Hub.png "Brands & Interest tiles")</span></span>

## <a name="how-we-determine-affinities"></a><span data-ttu-id="426e2-111">Hogyan határozzuk meg a márkahűséget</span><span class="sxs-lookup"><span data-stu-id="426e2-111">How we determine affinities</span></span>

<span data-ttu-id="426e2-112">A Microsoft online keresési adatait használjuk fel különböző demográfiai szegmensek (kor, gender vagy hely szerint meghatározva) megkerséséhez, például márkahűség és érdeklődési kör.</span><span class="sxs-lookup"><span data-stu-id="426e2-112">We use Microsoft’s online search data to find affinities for brands and interests across various demographic segments (defined by age, gender, or location).</span></span> <span data-ttu-id="426e2-113">A márka vagy az érdeklődési kör online keresési mennyisége határozza meg, hogy egy demografikus szegmens mekkora hűséggel rendelkezik a többi szegmenssel összehasonlítva az adott márkához vagy érdeklődési körhöz.</span><span class="sxs-lookup"><span data-stu-id="426e2-113">The online search volume for a brand or interest determines how much affinity a demographic segment, compared to other segments, has to that brand or interest.</span></span>

## <a name="affinity-level-and-score"></a><span data-ttu-id="426e2-114">Affinitás szintje és pontszám</span><span class="sxs-lookup"><span data-stu-id="426e2-114">Affinity level and score</span></span>

<span data-ttu-id="426e2-115">Minden bővített ügyfélprofilon két kapcsolódó értéket biztosítunk – affinitás szintje és affinitás pontszáma.</span><span class="sxs-lookup"><span data-stu-id="426e2-115">On every enriched customer profile, we provide two related values – affinity level and affinity score.</span></span> <span data-ttu-id="426e2-116">Ezek az értékek segítenek annak meghatározásában, hogy milyen erős az affinitás profil demográfiai szegmensében a márkához vagy érdeklődési körhöz az egyéb demográfiai szegmensekkel összehasonlítva.</span><span class="sxs-lookup"><span data-stu-id="426e2-116">These values help you determine how strong the affinity is for that profile’s demographic segment, for a brand or interest, as compared to other demographic segments.</span></span>

<span data-ttu-id="426e2-117">Az *Affinitás szintje* négy szintből áll, és egy 100 pontos skálán számítja ki a rendszer az *affinitási pontszámot*, amely hozzárendeli az affintiási szinteket.</span><span class="sxs-lookup"><span data-stu-id="426e2-117">*Affinity level* consists of four levels and *affinity score* is calculated on a 100-point scale that maps to the affinity levels.</span></span>


|<span data-ttu-id="426e2-118">Affinitás szintje</span><span class="sxs-lookup"><span data-stu-id="426e2-118">Affinity level</span></span> |<span data-ttu-id="426e2-119">Affinitási pontszám</span><span class="sxs-lookup"><span data-stu-id="426e2-119">Affinity score</span></span>  |
|---------|---------|
|<span data-ttu-id="426e2-120">Nagyon magas</span><span class="sxs-lookup"><span data-stu-id="426e2-120">Very high</span></span>     | <span data-ttu-id="426e2-121">85-100</span><span class="sxs-lookup"><span data-stu-id="426e2-121">85-100</span></span>       |
|<span data-ttu-id="426e2-122">Magas</span><span class="sxs-lookup"><span data-stu-id="426e2-122">High</span></span>     | <span data-ttu-id="426e2-123">70-84</span><span class="sxs-lookup"><span data-stu-id="426e2-123">70-84</span></span>        |
|<span data-ttu-id="426e2-124">Közepes</span><span class="sxs-lookup"><span data-stu-id="426e2-124">Medium</span></span>     | <span data-ttu-id="426e2-125">35-69</span><span class="sxs-lookup"><span data-stu-id="426e2-125">35-69</span></span>        |
|<span data-ttu-id="426e2-126">Alacsony</span><span class="sxs-lookup"><span data-stu-id="426e2-126">Low</span></span>     | <span data-ttu-id="426e2-127">1-34</span><span class="sxs-lookup"><span data-stu-id="426e2-127">1-34</span></span>        |

<span data-ttu-id="426e2-128">Az affinitás méréséhez használt részletességtől függően használhatja az affinitás szintjét vagy a pontszámot is.</span><span class="sxs-lookup"><span data-stu-id="426e2-128">Depending on the granularity you would like for measuring the affinity, you can use either affinity level or score.</span></span> <span data-ttu-id="426e2-129">Pontosabban szabályozható az affinitási pontszám.</span><span class="sxs-lookup"><span data-stu-id="426e2-129">Affinity score gives you more precise control.</span></span>

## <a name="supported-countriesregions"></a><span data-ttu-id="426e2-130">Támogatott országok/régiók</span><span class="sxs-lookup"><span data-stu-id="426e2-130">Supported countries/regions</span></span>

<span data-ttu-id="426e2-131">Jelenleg a következő ország-/régió lehetőségeket támogatjuk: Ausztrália, Kanada (angol), Franciaország, Németország, Egyesült Királyság vagy Egyesült Államok (angol).</span><span class="sxs-lookup"><span data-stu-id="426e2-131">We currently support the following country/region options: Australia, Canada (English), France, Germany, United Kingdom, or United States (English).</span></span>

<span data-ttu-id="426e2-132">Ország kiválasztásához nyissa meg a **Márkák bővítése** vagy az **Érdeklődés bővítése** lehetőséget és válassza az **Módosítás** lehetőséget az **Ország/régió** mellett.</span><span class="sxs-lookup"><span data-stu-id="426e2-132">To select a country, open the **Brands enrichment** or **Interest enrichment** and select **Change** next to **Country/Region**.</span></span> <span data-ttu-id="426e2-133">Az **Ország/régió beállításai** ablaktáblában válasszon egy beállítást, és válassza az **Alkalmaz** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="426e2-133">In the **Country/Region settings** pane, choose an option and select **Apply**.</span></span>

### <a name="implications-related-to-country-selection"></a><span data-ttu-id="426e2-134">Az országválasztással kapcsolatos következmények</span><span class="sxs-lookup"><span data-stu-id="426e2-134">Implications related to country selection</span></span>

- <span data-ttu-id="426e2-135">Saját [márkájának kiválasztásakor](#define-your-brands-or-interests) a rendszer a kiválasztott ország vagy régió alapján tesz javaslatokat.</span><span class="sxs-lookup"><span data-stu-id="426e2-135">When [choosing your own brands](#define-your-brands-or-interests), the system provides suggestions based on the selected country or region.</span></span>

- <span data-ttu-id="426e2-136">Egy [iparág kiválasztása](#define-your-brands-or-interests) esetén a kiválasztott ország vagy régió alapján megkapja a leginkább releváns márkákat és érdeklődési köröket.</span><span class="sxs-lookup"><span data-stu-id="426e2-136">When [choosing an industry](#define-your-brands-or-interests), you'll get the most relevant brands or interests based on the selected country or region.</span></span>

- <span data-ttu-id="426e2-137">A [profilok bővítésekor](#refresh-enrichment) minden ügyfélprofilt bővítünk, amelyhez a kiválasztott márkák és érdeklődési körök kapcsán adatokat kapunk.</span><span class="sxs-lookup"><span data-stu-id="426e2-137">When [enriching profiles](#refresh-enrichment), we'll enrich all customer profiles for which we get data for the selected brands and interests.</span></span> <span data-ttu-id="426e2-138">A nem a kijelölt országban vagy régióban található profilokat is.</span><span class="sxs-lookup"><span data-stu-id="426e2-138">Including profiles that are not in the selected country or region.</span></span> <span data-ttu-id="426e2-139">Ha például Németországot választotta, akkor bővítjük az Egyesült Államokban található profilokat, ha rendelkezésre állnak adatok az Egyesült Államokban a kiválasztott márkákra és érdeklődésre.</span><span class="sxs-lookup"><span data-stu-id="426e2-139">For example, if you selected Germany, we'll enrich profiles located in the United States if we have data available for the selected brands and interests in the US.</span></span>

## <a name="configure-enrichment"></a><span data-ttu-id="426e2-140">A bővítés konfigurálása</span><span class="sxs-lookup"><span data-stu-id="426e2-140">Configure Enrichment</span></span>

<span data-ttu-id="426e2-141">Az interaktív élmény végig segít Önnek a bővítések konfigurálásában.</span><span class="sxs-lookup"><span data-stu-id="426e2-141">A guided experience helps you through the configuration of the enrichments.</span></span> 

### <a name="define-your-brands-or-interests"></a><span data-ttu-id="426e2-142">Márkák vagy érdeklődési körök megadása</span><span class="sxs-lookup"><span data-stu-id="426e2-142">Define your brands or interests</span></span>

<span data-ttu-id="426e2-143">Válasszon az alábbi lehetőségek közül:</span><span class="sxs-lookup"><span data-stu-id="426e2-143">Select one of the following options:</span></span>

- <span data-ttu-id="426e2-144">**Iparág**: A rendszer azonosítja az iparághoz kapcsolódó legnépszerűbb márkákat vagy érdeklődési köröket, és bővíti az ügyfelek adatait velük.</span><span class="sxs-lookup"><span data-stu-id="426e2-144">**Industry**: The system identifies the top brands or interests relevant to your industry and enriches your customer data with them.</span></span>
- <span data-ttu-id="426e2-145">**Válassza ki a sajátját**: Legfeljebb öt elemet jelölhet ki a szervezetéhez leginkább kapcsolódó márkák vagy érdeklődési körök listájából.</span><span class="sxs-lookup"><span data-stu-id="426e2-145">**Choose your own**: Select up to five items from the list of brands or interests that are most relevant to your organization.</span></span>

<span data-ttu-id="426e2-146">Ha márkát vagy érdeklődési kört szeretne hozzáadni, írja be a beviteli területen a megfelelő kifejezések alapján javaslatokat kapjon.</span><span class="sxs-lookup"><span data-stu-id="426e2-146">To add a brand or interest, enter it in the input area to get suggestions based on matching terms.</span></span> <span data-ttu-id="426e2-147">Ha a keresett márkát vagy érdeklődési kört nem sorolja fel a rendszer, küldjön visszajelzést a **Javaslat** hivatkozás segítségével.</span><span class="sxs-lookup"><span data-stu-id="426e2-147">If we don't list a brand or interest you're looking for, send us feedback using the **Suggest** link.</span></span>

### <a name="review-enrichment-preferences"></a><span data-ttu-id="426e2-148">Bővítési beállítások áttekintése</span><span class="sxs-lookup"><span data-stu-id="426e2-148">Review enrichment preferences</span></span>

<span data-ttu-id="426e2-149">Tekintse át az alapértelmezett bővítési beállításokat, és szükség szerint frissítse azokat.</span><span class="sxs-lookup"><span data-stu-id="426e2-149">Review your default enrichment preferences and update them as needed.</span></span>

:::image type="content" source="media/affinity-enrichment-preferences.png" alt-text="Képernyőkép a bővítési beállítások ablakáról.":::

### <a name="select-entity-to-enrich"></a><span data-ttu-id="426e2-151">Entitás kiválasztása bővítéshez</span><span class="sxs-lookup"><span data-stu-id="426e2-151">Select entity to enrich</span></span>

<span data-ttu-id="426e2-152">Válassza a **Bővített entitás** lehetőséget, és válassza a Microsoft vállalati adataival gyarapítani kívánt entitásokat.</span><span class="sxs-lookup"><span data-stu-id="426e2-152">Select **Enriched entity** and choose the data set you want to enrich with company data from the Microsoft.</span></span> <span data-ttu-id="426e2-153">Kiválaszthatja a Vevő entitást az összes ügyfélprofil gazdagítására, vagy kiválaszthat egy szegmens entitást, amely csak az adott szegmensben található vevőprofilokat gazdagítja.</span><span class="sxs-lookup"><span data-stu-id="426e2-153">You can select the Customer entity to enrich all your customer profiles or select a segment entity to enrich only customer profiles contained in that segment.</span></span>

### <a name="map-your-fields"></a><span data-ttu-id="426e2-154">Mezők megfeleltetése</span><span class="sxs-lookup"><span data-stu-id="426e2-154">Map your fields</span></span>

<span data-ttu-id="426e2-155">A egyesített ügyfélentitás mezőinek leképezésével meghatározhatja, hogy a rendszer az ügyféladatok gyarapítására melyik demográfiai szegmenst használja.</span><span class="sxs-lookup"><span data-stu-id="426e2-155">Map fields from your unified customer entity to define the demographic segment you want the system to use for enriching your customer data.</span></span> <span data-ttu-id="426e2-156">Ország/régió leképezése, és legalább a születési dátum vagy nem attribútumát.</span><span class="sxs-lookup"><span data-stu-id="426e2-156">Map Country/Region and at least Date of Birth or Gender attributes.</span></span> <span data-ttu-id="426e2-157">Ezenkívül le kell képeznie legalább egy várost (és államot/tartományt) vagy irányítószámot.</span><span class="sxs-lookup"><span data-stu-id="426e2-157">Additionally, you must map at least one of City (and State/Province) or Postal code.</span></span> <span data-ttu-id="426e2-158">Válassza a **Szerkesztés** lehetőséget a mezők leképezésének definiálásához, és válassza az **Alkalmazás** lehetőséget, amikor elkészült.</span><span class="sxs-lookup"><span data-stu-id="426e2-158">Select **Edit** to define the mapping of the fields and select **Apply** when you're done.</span></span> <span data-ttu-id="426e2-159">Válassza a **Mentés** lehetőséget a mezők leképezésének végrehajtásához.</span><span class="sxs-lookup"><span data-stu-id="426e2-159">Select **Save** to complete the field mapping.</span></span>

<span data-ttu-id="426e2-160">A következő formátumok és értékek támogatottak, az értékek nem különböztetik meg a kis- és nagybetűket:</span><span class="sxs-lookup"><span data-stu-id="426e2-160">The following formats and values are supported, values are not case-sensitive:</span></span>

- <span data-ttu-id="426e2-161">**Születési dátum**: Azt ajánljuk, hogy az adatok betöltése során a születési dátumot a rendszer datetime típusúra alakítsa.</span><span class="sxs-lookup"><span data-stu-id="426e2-161">**Date of Birth**: We recommend that date of birth is converted to DateTime type during data ingestion.</span></span> <span data-ttu-id="426e2-162">Másik lehetőségként [ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html) formátumú "éééé-hh-nn" vagy "éééé-hh-NNTóó:pp:mp" karakterláncot is meg lehet adni.</span><span class="sxs-lookup"><span data-stu-id="426e2-162">Alternatively, it can be a string in [ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html) format "yyyy-MM-dd" or "yyyy-MM-ddTHH:mm:ssZ".</span></span>
- <span data-ttu-id="426e2-163">**Nem**: férfi, nő, ismeretlen</span><span class="sxs-lookup"><span data-stu-id="426e2-163">**Gender**: Male, Female, Unknown</span></span>
- <span data-ttu-id="426e2-164">**Irányítószám**: Öt számjegyből álló ZIP-kód az Egyesült Államokban, szabványos irányítószám mindenhol máshol</span><span class="sxs-lookup"><span data-stu-id="426e2-164">**Postal code**: Five-digit ZIP Codes for US, standard postal code everywhere else</span></span>
- <span data-ttu-id="426e2-165">**Város**: A város neve angolul</span><span class="sxs-lookup"><span data-stu-id="426e2-165">**City**: City name in English</span></span>
- <span data-ttu-id="426e2-166">**Állam/megye**: Két betűs rövidítés az Egyesült Államok és Kanada esetében.</span><span class="sxs-lookup"><span data-stu-id="426e2-166">**State/Province**: Two-letter abbreviation for the US and Canada.</span></span> <span data-ttu-id="426e2-167">Két vagy három betű rövidítés Ausztrália esetében.</span><span class="sxs-lookup"><span data-stu-id="426e2-167">Two or three letter abbreviation for Australia.</span></span> <span data-ttu-id="426e2-168">Franciaország, Németország és az Egyesült Királyság esetében nem alkalmazható.</span><span class="sxs-lookup"><span data-stu-id="426e2-168">Not applicable for France, Germany, or the UK.</span></span>
- <span data-ttu-id="426e2-169">**Ország/régió**:</span><span class="sxs-lookup"><span data-stu-id="426e2-169">**Country/Region**:</span></span>

  - <span data-ttu-id="426e2-170">USA: Amerikai Egyesült Államok, Egyesült Államok, USA, US, Amerika</span><span class="sxs-lookup"><span data-stu-id="426e2-170">US: United States of America, United States, USA, US, America</span></span>
  - <span data-ttu-id="426e2-171">CA: Kanada, CA</span><span class="sxs-lookup"><span data-stu-id="426e2-171">CA: Canada, CA</span></span>
  - <span data-ttu-id="426e2-172">GB: Egyesült Királyság, UK, Nagy-Britannia, GB, Nagy-Britannia és Észak-Írország Egyesült Királysága, Nagy-Britannia Egyesült Királysága</span><span class="sxs-lookup"><span data-stu-id="426e2-172">GB: United Kingdom, UK, Great Britain, GB, United Kingdom of Great Britain and Northern Ireland, United Kingdom of Great Britain</span></span>
  - <span data-ttu-id="426e2-173">AU: Ausztrália, AU, Ausztrál nemzetközösség</span><span class="sxs-lookup"><span data-stu-id="426e2-173">AU: Australia, AU, Common Wealth of Australia</span></span>
  - <span data-ttu-id="426e2-174">FR: Franciaország, Francia Köztársaság</span><span class="sxs-lookup"><span data-stu-id="426e2-174">FR: France, FR, French Republic</span></span>
  - <span data-ttu-id="426e2-175">DE: Németország, német, Deutschland, Allemagne, DE, Német Szövetségi Köztársaság, Német Köztársaság</span><span class="sxs-lookup"><span data-stu-id="426e2-175">DE: Germany, German, Deutschland, Allemagne, DE, Federal Republic of Germany, Republic of Germany</span></span>

## <a name="review-and-name-the-enrichment"></a><span data-ttu-id="426e2-176">A bővítés áttekintése és elnevezése</span><span class="sxs-lookup"><span data-stu-id="426e2-176">Review and name the enrichment</span></span>

<span data-ttu-id="426e2-177">Végül áttekintheti az információkat, és nevet adhat a bővítésnek.</span><span class="sxs-lookup"><span data-stu-id="426e2-177">Finally, you get to review the information and provide a name for the enrichment.</span></span>

:::image type="content" source="media/enrichment-interests-summary.png" alt-text="Az érdeklődési kör áttekintése és elnevezési oldal.":::

## <a name="refresh-enrichment"></a><span data-ttu-id="426e2-179">A bővítés frissítése</span><span class="sxs-lookup"><span data-stu-id="426e2-179">Refresh enrichment</span></span>

<span data-ttu-id="426e2-180">Futtassa a bővítést a márkák, érdeklődési körök konfigurálása és a mezők demográfiai adatokra vonatkozó leképezése után.</span><span class="sxs-lookup"><span data-stu-id="426e2-180">Run the enrichment after configuring brands, interests, and the field mapping for demographics.</span></span> <span data-ttu-id="426e2-181">A folyamat megkezdéséhez válassza a márka vagy az érdeklődési kör konfigurációja lapon a **Futtatás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="426e2-181">To start the process, select **Run** on the brand or interest configuration page.</span></span> <span data-ttu-id="426e2-182">Emellett a rendszer automatikusan is futtathatja a dúsítást egy ütemezett frissítés részeként.</span><span class="sxs-lookup"><span data-stu-id="426e2-182">Additionally, you can let the system run the enrichment automatically as part of a scheduled refresh.</span></span>
<span data-ttu-id="426e2-183">Az ügyféladatok méretétől függően előfordulhat, hogy a bővítés futtatása néhány percig is eltarthat.</span><span class="sxs-lookup"><span data-stu-id="426e2-183">Depending on the size of your customer data, it may take several minutes for an enrichment run to complete.</span></span>

> [!TIP]
> <span data-ttu-id="426e2-184">A feladatokhoz/folyamatokhoz [hatféle állapot](system.md#status-types) tartozhat.</span><span class="sxs-lookup"><span data-stu-id="426e2-184">There are [six types of status](system.md#status-types) for tasks/processes.</span></span> <span data-ttu-id="426e2-185">Emellett a legtöbb folyamat [más alsóbb szintű folyamatoktól is függ](system.md#refresh-policies).</span><span class="sxs-lookup"><span data-stu-id="426e2-185">Additionally, most processes [depend on other downstream processes](system.md#refresh-policies).</span></span> <span data-ttu-id="426e2-186">Kiválaszthatja egy folyamat állapotát, és megtekintheti a hozzá tartozó teljes feladat folyamatának részleteit.</span><span class="sxs-lookup"><span data-stu-id="426e2-186">You can select the status of a process to see details on the progress of the entire job.</span></span> <span data-ttu-id="426e2-187">Miután kiválasztotta a **Részletek megtekintése** lehetőséget a feladat egyik feladatához, további információk jelennek meg: feldolgozási idő, legutóbbi feldolgozás dátuma, és a feladathoz társított összes hiba és figyelmeztetés.</span><span class="sxs-lookup"><span data-stu-id="426e2-187">After selecting **See details** for one of the job's tasks, you find additional information: processing time, the last processing date, and all errors and warnings associated with the task.</span></span>

## <a name="enrichment-results"></a><span data-ttu-id="426e2-188">Bővítési eredmények</span><span class="sxs-lookup"><span data-stu-id="426e2-188">Enrichment results</span></span>

<span data-ttu-id="426e2-189">A bővítési folyamat futtatása után lépjen a **Saját bővítések** pontra, és nézze át a bővített ügyfelek teljes számát és a márkák vagy érdeklődési körök lebontását a bővített ügyfelek profiljaiban.</span><span class="sxs-lookup"><span data-stu-id="426e2-189">After running the enrichment process, go to **My enrichments** to review the total number of enriched customers and a breakdown of brands or interests in the enriched customer profiles.</span></span>

:::image type="content" source="media/my-enrichments.png" alt-text="Az eredmények előnézete a bővítési folyamat futtatása után":::

<span data-ttu-id="426e2-191">A bővített adatok áttekintéséhez jelölje be a **Bővített adatok megtekintése** lehetőséget a diagramban.</span><span class="sxs-lookup"><span data-stu-id="426e2-191">Review the enriched data by selecting **View enriched data** in the chart.</span></span> <span data-ttu-id="426e2-192">A márkák bővített adatai a **BrandAffinityFromMicrosoft** entitásba kerülnek.</span><span class="sxs-lookup"><span data-stu-id="426e2-192">Enriched data for brands goes to the **BrandAffinityFromMicrosoft** entity.</span></span> <span data-ttu-id="426e2-193">Az érdeklődési körök adatai az **InterestAffinityFromMicrosoft** entitásba kerülnek.</span><span class="sxs-lookup"><span data-stu-id="426e2-193">Data for interests is in the **InterestAffinityFromMicrosoft** entity.</span></span> <span data-ttu-id="426e2-194">Ezeket az entitásokat a **Bővítés** csoportban is megtekintheti az **Adatok** > **Entitások** helyen.</span><span class="sxs-lookup"><span data-stu-id="426e2-194">You'll also find these entities listed in the **Enrichment** group in **Data** > **Entities**.</span></span>

## <a name="see-enrichment-data-on-the-customer-card"></a><span data-ttu-id="426e2-195">A bővítési adatok megtekintése az ügyfélkártyán</span><span class="sxs-lookup"><span data-stu-id="426e2-195">See enrichment data on the customer card</span></span>

<span data-ttu-id="426e2-196">A márka és a érdeklődés affinitásokat az ügyfélkártyákon is meg lehet tekinteni.</span><span class="sxs-lookup"><span data-stu-id="426e2-196">Brand and interest affinities can also be viewed on individual customer cards.</span></span> <span data-ttu-id="426e2-197">Nyissa meg az **Ügyfelek** lehetőséget, és válassza ki az ügyfél profilját.</span><span class="sxs-lookup"><span data-stu-id="426e2-197">Go to **Customers** and select a customer profile.</span></span> <span data-ttu-id="426e2-198">Az ügyfélkártyán megkeresheti a márkákra vagy az érdeklődési körökre vonatkozó diagramokat, amelyek szerint az adott ügyfél demográfiai profiljához tartozó személyek affinitással rendelkeznek.</span><span class="sxs-lookup"><span data-stu-id="426e2-198">In the customer card, you'll find charts for the brands or interests that people in that customer's demographic profile have affinity for.</span></span>

:::image type="content" source="media/enrichment-customer-card.png" alt-text="Bővített adatokkal rendelkező ügyfél-kártya":::

## <a name="next-steps"></a><span data-ttu-id="426e2-200">Következő lépések</span><span class="sxs-lookup"><span data-stu-id="426e2-200">Next steps</span></span>

<span data-ttu-id="426e2-201">Építsen a bővített ügyféladatokra.</span><span class="sxs-lookup"><span data-stu-id="426e2-201">Build on top of your enriched customer data.</span></span> <span data-ttu-id="426e2-202">Hozzon létre [Szegmenseket](segments.md), [Mértékeket](measures.md) , sőt [Exportálhatja az adatokat](export-destinations.md), hogy személyre szabott élményeket tudjon nyújtani az ügyfeleknek.</span><span class="sxs-lookup"><span data-stu-id="426e2-202">Create [Segments](segments.md), [Measures](measures.md), and even [export the data](export-destinations.md) to deliver personalized experiences to your customers.</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]
