---
title: Továbbfejlesztett címek bővítése
description: A Microsoft modelljeivel rendelkező ügyfélprofilok címinformációinak bővítése és normalizálása.
ms.date: 04/21/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: kishorem-ms
ms.author: kishorem
manager: shellyha
ms.openlocfilehash: e0ca731f944da9a7eaae7c2dc2d7568b6386089f
ms.sourcegitcommit: d84d664e67f263bfeb741154d309088c5101b9c3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/24/2021
ms.locfileid: "6305435"
---
# <a name="enrichment-of-customer-profiles-with-enhanced-addresses"></a><span data-ttu-id="15862-103">Ügyfélprofilok bővítése továbbfejlesztett címekkel</span><span class="sxs-lookup"><span data-stu-id="15862-103">Enrichment of customer profiles with enhanced addresses</span></span>

<span data-ttu-id="15862-104">Az adatokban szereplő címek strukturálatlanok, hiányosak vagy helytelenek lehetnek.</span><span class="sxs-lookup"><span data-stu-id="15862-104">Addresses in your data can be unstructured, incomplete, or incorrect.</span></span> <span data-ttu-id="15862-105">A Microsoft modelljeivel normalizálhatja és bővítheti [Common Data Model formátumba](/common-data-model/schema/core/applicationcommon/address) a címeket, amelyek így pontosabbak lehetnek.</span><span class="sxs-lookup"><span data-stu-id="15862-105">Use Microsoft's models to normalize and enrich your addresses into the [Common Data Model format](/common-data-model/schema/core/applicationcommon/address) for better accuracy and insights.</span></span>

## <a name="how-we-enhance-addresses"></a><span data-ttu-id="15862-106">Hogyan történik a címek továbbfejlesztése?</span><span class="sxs-lookup"><span data-stu-id="15862-106">How we enhance addresses</span></span>

<span data-ttu-id="15862-107">A modell két lépést használ a címek továbbfejlesztéséhez.</span><span class="sxs-lookup"><span data-stu-id="15862-107">Our model goes through a two-step process to enhance an address.</span></span> <span data-ttu-id="15862-108">Először elemezi a címet, azonosítja az összetevőit, és strukturált formátumba alakítja őket.</span><span class="sxs-lookup"><span data-stu-id="15862-108">First, it parses the address to identify its components and puts them into a structured format.</span></span> <span data-ttu-id="15862-109">Ezután az AI-t használjuk a címben lévő értékek javítására, befejezésére és szabványosítására.</span><span class="sxs-lookup"><span data-stu-id="15862-109">Then, we use AI to correct, complete, and standardize the values in the address.</span></span>

### <a name="example"></a><span data-ttu-id="15862-110">Példa</span><span class="sxs-lookup"><span data-stu-id="15862-110">Example</span></span>

<span data-ttu-id="15862-111">Előfordulhat, hogy a címadatok nem szabványos formátumúak, és helyesírási hibákat tartalmaznak.</span><span class="sxs-lookup"><span data-stu-id="15862-111">Address information might be in a nonstandard format and contain spelling errors.</span></span> <span data-ttu-id="15862-112">A modell ezeket a problémákat ki tudja javítani, és egységes címeket hozhat létre az egységes ügyfélprofilokban.</span><span class="sxs-lookup"><span data-stu-id="15862-112">The model can fix these issues and create consistent addresses in unified customer profiles.</span></span>

```Input
4567 w main stret californa missouri 54321 us
```

```Output
- Street1: 4567 W Main St
- City: California
- StateOrProvince: MO
- ZipOrPostalCode: 54321
- CountryOrRegion: United States of America

- Address: 4567 W Main St, California, MO, 54321, United States of America
```

### <a name="limitations"></a><span data-ttu-id="15862-113">Korlátozások</span><span class="sxs-lookup"><span data-stu-id="15862-113">Limitations</span></span>

<span data-ttu-id="15862-114">A továbbfejlesztett címek csak a betöltött címadatokban már megtalálható értékekkel működnek.</span><span class="sxs-lookup"><span data-stu-id="15862-114">Enhanced addresses only works with the values that already exist in your ingested address data.</span></span> <span data-ttu-id="15862-115">A modell nem:</span><span class="sxs-lookup"><span data-stu-id="15862-115">The model doesn't:</span></span> 

1. <span data-ttu-id="15862-116">ellenőrzi, hogy a cím érvényes-e;</span><span class="sxs-lookup"><span data-stu-id="15862-116">Verify if the address is a valid address.</span></span>
2. <span data-ttu-id="15862-117">ellenőrzi, hogy az értékek (például az irányítószám vagy az utcanév) érvényesek-e;</span><span class="sxs-lookup"><span data-stu-id="15862-117">Verify if any of the values, such as ZIP codes or street names, are valid.</span></span>
3. <span data-ttu-id="15862-118">módosítja a fel nem ismert értékeket.</span><span class="sxs-lookup"><span data-stu-id="15862-118">Change values it doesn't recognize.</span></span>

<span data-ttu-id="15862-119">A modell gépi tanuláson alapuló technikákat alkalmaz a címek továbbfejlesztéséhez.</span><span class="sxs-lookup"><span data-stu-id="15862-119">The model uses machine learning-based techniques to enhance addresses.</span></span> <span data-ttu-id="15862-120">Bár magas megbízhatósági küszöböt alkalmazunk arra az időre, amikor a modell megváltoztatja a bemeneti értéket, mint minden gépi tanuláson alapuló modell esetében, a 100 százalékos pontosság nem garantált.</span><span class="sxs-lookup"><span data-stu-id="15862-120">While we apply a high confidence threshold for when the model changes an input value, as with any machine learning-based model, 100 percent accuracy is not guaranteed.</span></span>

## <a name="supported-countries-or-regions"></a><span data-ttu-id="15862-121">Támogatott országok és régiók</span><span class="sxs-lookup"><span data-stu-id="15862-121">Supported countries or regions</span></span>

<span data-ttu-id="15862-122">Jelenleg a következő országokban és régiókban támogatjuk a címek bővítését:</span><span class="sxs-lookup"><span data-stu-id="15862-122">We currently support enriching addresses in these countries or regions:</span></span> 

- <span data-ttu-id="15862-123">Ausztrália</span><span class="sxs-lookup"><span data-stu-id="15862-123">Australia</span></span>
- <span data-ttu-id="15862-124">Kanada</span><span class="sxs-lookup"><span data-stu-id="15862-124">Canada</span></span>
- <span data-ttu-id="15862-125">Egyesült Királyság</span><span class="sxs-lookup"><span data-stu-id="15862-125">United Kingdom</span></span>
- <span data-ttu-id="15862-126">Egyesült Államok</span><span class="sxs-lookup"><span data-stu-id="15862-126">United States</span></span>

<span data-ttu-id="15862-127">A címek egy ország/régió értéket tartalmazhatnak.</span><span class="sxs-lookup"><span data-stu-id="15862-127">Addresses must contain a country/region value.</span></span> <span data-ttu-id="15862-128">Nem dolgozunk fel nem támogatott országokban és régiókban lévő címeket, illetve olyan címeket, ahol nincs megadva ország vagy régió.</span><span class="sxs-lookup"><span data-stu-id="15862-128">We don't process addresses for countries or regions that aren't supported and addresses that have no country or region provided.</span></span>

## <a name="configure-the-enrichment"></a><span data-ttu-id="15862-129">Bővítés konfigurálása</span><span class="sxs-lookup"><span data-stu-id="15862-129">Configure the enrichment</span></span>

1. <span data-ttu-id="15862-130">Lépjen az **Adatok** > **Bővítés** pontra.</span><span class="sxs-lookup"><span data-stu-id="15862-130">Go to **Data** > **Enrichment**.</span></span>

1. <span data-ttu-id="15862-131">A **Továbbfejlesztett címek** csempén válassza **Az adataim bővítése** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="15862-131">Select **Enrich my data** on the **Enhanced addresses** tile.</span></span>

   :::image type="content" source="media/enhanced-addresses-tile.png" alt-text="A Továbbfejlesztett címek csempe képernyőképe.":::

1. <span data-ttu-id="15862-133">Válassza ki az **Ügyféladatok beállítva** lehetőséget, majd a bővíteni kívánt címeket tartalmazó entitást.</span><span class="sxs-lookup"><span data-stu-id="15862-133">Select the **Customer data set** and choose the entity containing the addresses you want to enrich.</span></span> <span data-ttu-id="15862-134">Az *Ügyfél* entitás kiválasztásával az összes ügyfélprofilban lévő címeket bővítheti, de kijelölhet olyan szegmensentitást is, amely csak az adott szegmensben található ügyfélprofilok címeit bővíti.</span><span class="sxs-lookup"><span data-stu-id="15862-134">You can select the *Customer* entity to enrich addresses in all your customer profiles or select a segment entity to enrich addresses only in customer profiles contained in that segment.</span></span>

1. <span data-ttu-id="15862-135">Adja meg, hogyan történjen az adatkészletben lévő címek formázása.</span><span class="sxs-lookup"><span data-stu-id="15862-135">Select how addresses are formatted in your data set.</span></span> <span data-ttu-id="15862-136">Ha az adatokban lévő címek egy mezőt használnak, válassza az **Egyattribútumos cím** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="15862-136">Choose **Single-attribute address** if addresses in your data use a single field.</span></span> <span data-ttu-id="15862-137">Ha az adatokban lévő címek több adatmezőt használnak, válassza a **Többattribútumos cím** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="15862-137">Choose **Multiple-attribute address** if addresses in your data use more than one data field.</span></span>

   > [!NOTE]
   > <span data-ttu-id="15862-138">Az ország/régió kötelező mind az egy-attribútumos, mind a több attribútumos címekben.</span><span class="sxs-lookup"><span data-stu-id="15862-138">Country/Region is mandatory in both single-attribute and multiple-attribute addresses.</span></span> <span data-ttu-id="15862-139">Az érvényes vagy támogatott ország/régió értékeket nem tartalmazó címek nem kerülnek bővítésre.</span><span class="sxs-lookup"><span data-stu-id="15862-139">Addresses that don't contain valid or supported country/region values won't be enriched.</span></span>

1.  <span data-ttu-id="15862-140">Képezze le az egyesített ügyfélentitásból származó címmezőket.</span><span class="sxs-lookup"><span data-stu-id="15862-140">Map the address fields from your unified customer entity.</span></span>

    :::image type="content" source="media/enhanced-address-mapping.png" alt-text="Továbbfejlesztett címmező-leképezési oldal.":::

1. <span data-ttu-id="15862-142">A mező leképezésének befejezéséhez válassza a **Következő** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="15862-142">Select **Next** to complete the field mapping.</span></span>

1. <span data-ttu-id="15862-143">Adja meg a bővítés és a kimeneti entitás nevét.</span><span class="sxs-lookup"><span data-stu-id="15862-143">Provide a name for the enrichment and the output entity.</span></span>

1. <span data-ttu-id="15862-144">Válassza a **Bővítés mentése** lehetőséget, miután áttekintette a lehetőségeit.</span><span class="sxs-lookup"><span data-stu-id="15862-144">Select **Save enrichment** after reviewing your choices.</span></span>

## <a name="enrichment-results"></a><span data-ttu-id="15862-145">Bővítési eredmények</span><span class="sxs-lookup"><span data-stu-id="15862-145">Enrichment results</span></span>

<span data-ttu-id="15862-146">A bővítési folyamat megkezdéséhez válassza a **Futtatás** parancsot a parancssorból.</span><span class="sxs-lookup"><span data-stu-id="15862-146">To start the enrichment process, select **Run** from the command bar.</span></span> <span data-ttu-id="15862-147">Azt is engedélyezheti, hogy a rendszer a bővítést automatikusan egy [ütemezett frissítés](system.md#schedule-tab) részeként futtassa.</span><span class="sxs-lookup"><span data-stu-id="15862-147">You can also let the system run the enrichment automatically as part of a [scheduled refresh](system.md#schedule-tab).</span></span> <span data-ttu-id="15862-148">A feldolgozási idő az ügyféladatok mennyiségétől függ.</span><span class="sxs-lookup"><span data-stu-id="15862-148">The processing time depends on the size of your customer data.</span></span>

<span data-ttu-id="15862-149">A bővítési folyamat befejeződése után áttekintheti az újonnan bővített ügyfelek profiljainak adatait a **Saját bővítések** alatt.</span><span class="sxs-lookup"><span data-stu-id="15862-149">After the enrichment process completes, you can review the newly enriched customer profiles data under **My enrichments**.</span></span> <span data-ttu-id="15862-150">Emellett megtalálhatja az utolsó frissítés időpontját és a bővített profilok számát is.</span><span class="sxs-lookup"><span data-stu-id="15862-150">Additionally, you'll find the time of the last update and the number of enriched profiles.</span></span>

<span data-ttu-id="15862-151">Az egyes bővített profilok részletes nézetét a **Bővített adatok megtekintése** lehetőségre kattintva érheti el.</span><span class="sxs-lookup"><span data-stu-id="15862-151">You can access a detailed view of each enriched profile by selecting **View enriched data**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="15862-152">Következő lépések</span><span class="sxs-lookup"><span data-stu-id="15862-152">Next steps</span></span>

<span data-ttu-id="15862-153">Építsen a bővített ügyféladatokra.</span><span class="sxs-lookup"><span data-stu-id="15862-153">Build on top of your enriched customer data.</span></span> <span data-ttu-id="15862-154">Hozzon létre [szegmenseket](segments.md) és [intézkedéseket](measures.md), továbbá [exportálja az adatokat](export-destinations.md) , hogy személyre szabott élményt nyújtson ügyfeleinek.</span><span class="sxs-lookup"><span data-stu-id="15862-154">Create [segments](segments.md) and [measures](measures.md), and even [export the data](export-destinations.md) to deliver personalized experiences to your customers.</span></span>

[!INCLUDE[footer-include](../includes/footer-banner.md)]
