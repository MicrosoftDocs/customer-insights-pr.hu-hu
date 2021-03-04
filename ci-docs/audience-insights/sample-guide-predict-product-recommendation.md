---
title: Termékjavaslat-előrejelzés mintaútmutató
description: Használja ezt a mintamutatót, hogy kipróbálja a termékjavaslat előrejelzési modellt.
ms.date: 02/10/2021
ms.reviewer: digranad
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: tutorial
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: 0ee873d9b7caa5f891cb2d5b8c665dec90ad0e59
ms.sourcegitcommit: 139548f8a2d0f24d54c4a6c404a743eeeb8ef8e0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/15/2021
ms.locfileid: "5270500"
---
# <a name="product-recommendation-prediction-preview-sample-guide"></a><span data-ttu-id="49b90-103">Termékjavaslat-előrejelzés (előzetes verzió) mintaútmutató</span><span class="sxs-lookup"><span data-stu-id="49b90-103">Product recommendation prediction (preview) sample guide</span></span>

<span data-ttu-id="49b90-104">Elejétől végéig bemutatunk Önnek egy példán keresztül a egy termékajánlás előrejelzést, használva az alább megadott példaadatokat.</span><span class="sxs-lookup"><span data-stu-id="49b90-104">We'll walk you through an end to end example of product recommendation prediction using the sample data provided below.</span></span>

## <a name="scenario"></a><span data-ttu-id="49b90-105">Forgatókönyv</span><span class="sxs-lookup"><span data-stu-id="49b90-105">Scenario</span></span>

<span data-ttu-id="49b90-106">A Contoso egy vállalat, amely kiváló minőségű kávét és kávégépet árusít, melyet a Contoso Coffee weboldalán keresztül adnak el.</span><span class="sxs-lookup"><span data-stu-id="49b90-106">Contoso is a company that produces high-quality coffee and coffee machines, which they sell through their Contoso Coffee website.</span></span> <span data-ttu-id="49b90-107">Céljuk, hogy megértsék, mely termékeket ajánlják ki a visszatérő ügyfeleiknek.</span><span class="sxs-lookup"><span data-stu-id="49b90-107">Their goal is to understand which products should they recommend to their recurring customers.</span></span> <span data-ttu-id="49b90-108">Ha tudják azt, hogy az ügyfelek mit **vásárolnak valószínűleg**, segíthet a marketingráfordítások mérséklésében, ha bizonyos elemekre figyelnek.</span><span class="sxs-lookup"><span data-stu-id="49b90-108">Knowing what customers are more **likely to purchase**, can help them save marketing efforts by focusing on specific items.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="49b90-109">Előfeltételek</span><span class="sxs-lookup"><span data-stu-id="49b90-109">Prerequisites</span></span>

- <span data-ttu-id="49b90-110">Legalább [közreműködői engedély](permissions.md) a Customer Insightsban.</span><span class="sxs-lookup"><span data-stu-id="49b90-110">At least [Contributor permissions](permissions.md) in Customer Insights.</span></span>
- <span data-ttu-id="49b90-111">Javasoljuk, hogy a következő lépéseket hajtsa végre [egy új környezetben](manage-environments.md).</span><span class="sxs-lookup"><span data-stu-id="49b90-111">We recommend that you implement the following steps [in a new environment](manage-environments.md).</span></span>

## <a name="task-1---ingest-data"></a><span data-ttu-id="49b90-112">1. Feladat - Adatok betáplálása</span><span class="sxs-lookup"><span data-stu-id="49b90-112">Task 1 - Ingest data</span></span>

<span data-ttu-id="49b90-113">Olvassa el a cikkeket [az adatok betáplálásáról](data-sources.md) és [az adatforrások importálásáról a Power Query csatlakozók használatával](connect-power-query.md).</span><span class="sxs-lookup"><span data-stu-id="49b90-113">Review the articles [about data ingestion](data-sources.md) and [importing data sources using Power Query connectors](connect-power-query.md) specifically.</span></span> <span data-ttu-id="49b90-114">A következő információk azt feltételezik, hogy megismerkedett a betáplált adatokkal általánosságban.</span><span class="sxs-lookup"><span data-stu-id="49b90-114">The following information assumes you familiarized with ingesting data in general.</span></span>

### <a name="ingest-customer-data-from-ecommerce-platform"></a><span data-ttu-id="49b90-115">Betáplált ügyféladatok az eCommerce platformról.</span><span class="sxs-lookup"><span data-stu-id="49b90-115">Ingest customer data from eCommerce platform</span></span>

1. <span data-ttu-id="49b90-116">Hozzon létre egy adatforrást, elnevezve **eCommerce**-nek, majd válassza az importálás lehetőséget, és jelölje ki a **Text/CSV** csatlakozót.</span><span class="sxs-lookup"><span data-stu-id="49b90-116">Create a data source named **eCommerce**, choose the import option, and select the **Text/CSV** connector.</span></span>

1. <span data-ttu-id="49b90-117">Adja meg az URL-címét az eCommerce kapcsolattartóknak https://aka.ms/ciadclasscontacts.</span><span class="sxs-lookup"><span data-stu-id="49b90-117">Enter the URL for eCommerce contacts https://aka.ms/ciadclasscontacts.</span></span>

1. <span data-ttu-id="49b90-118">Az adatok szerkesztése közben válassza az **Átalakítás** lehetőséget, majd a **Használja az első sort fejlécként** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="49b90-118">While editing the data, select **Transform** and then **Use First Row as Headers**.</span></span>

1. <span data-ttu-id="49b90-119">Frissítse az adattípust az alább felsorolt oszlopokhoz:</span><span class="sxs-lookup"><span data-stu-id="49b90-119">Update the datatype for the columns listed below:</span></span>
   - <span data-ttu-id="49b90-120">**SzületésiDátum**: Dátum</span><span class="sxs-lookup"><span data-stu-id="49b90-120">**DateOfBirth**: Date</span></span>
   - <span data-ttu-id="49b90-121">**CreatedOn**: Dátum/Idő/Zóna</span><span class="sxs-lookup"><span data-stu-id="49b90-121">**CreatedOn**: Date/Time/Zone</span></span>

   :::image type="content" source="media/ecommerce-dob-date.PNG" alt-text="A születési dátum átalakítása dátummá.":::

5. <span data-ttu-id="49b90-123">A jobb oldali panelben a "Név" mezőben nevezze át az adatforrását a **Lekérdezés**-ről **eCommerceContacts**-ra.</span><span class="sxs-lookup"><span data-stu-id="49b90-123">In the 'Name' field on the right-hand pane, rename your data source from **Query** to **eCommerceContacts**</span></span>

6. <span data-ttu-id="49b90-124">**Mentse** az adatforrást.</span><span class="sxs-lookup"><span data-stu-id="49b90-124">**Save** the data source.</span></span>

### <a name="ingest-online-purchase-data"></a><span data-ttu-id="49b90-125">Online vásárlási adatok betáplálása.</span><span class="sxs-lookup"><span data-stu-id="49b90-125">Ingest online purchase data</span></span>

1. <span data-ttu-id="49b90-126">Adjon hozzá egy újabb adatforrást a megegyező **eCommerce** adatforráshoz.</span><span class="sxs-lookup"><span data-stu-id="49b90-126">Add another data set to the same **eCommerce** data source.</span></span> <span data-ttu-id="49b90-127">Válassza a **Text/CSV** csatlakozót újra.</span><span class="sxs-lookup"><span data-stu-id="49b90-127">Choose the **Text/CSV** connector again.</span></span>

1. <span data-ttu-id="49b90-128">Adja meg az URL-címét az **Online vásárlas** adataihoz https://aka.ms/ciadclassonline.</span><span class="sxs-lookup"><span data-stu-id="49b90-128">Enter the URL for **Online Purchases** data https://aka.ms/ciadclassonline.</span></span>

1. <span data-ttu-id="49b90-129">Az adatok szerkesztése közben válassza az **Átalakítás** lehetőséget, majd a **Használja az első sort fejlécként** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="49b90-129">While editing the data, select **Transform** and then **Use First Row as Headers**.</span></span>

1. <span data-ttu-id="49b90-130">Frissítse az adattípust az alább felsorolt oszlopokhoz:</span><span class="sxs-lookup"><span data-stu-id="49b90-130">Update the datatype for the columns listed below:</span></span>
   - <span data-ttu-id="49b90-131">**PurchasedOn** : Dátum/Idő</span><span class="sxs-lookup"><span data-stu-id="49b90-131">**PurchasedOn**: Date/Time</span></span>
   - <span data-ttu-id="49b90-132">**TotalPrice** : Pénznem</span><span class="sxs-lookup"><span data-stu-id="49b90-132">**TotalPrice**: Currency</span></span>

1. <span data-ttu-id="49b90-133">A **Név** mezőben az oldalsó panelen, nevezze át az adatforrását a **Lekérdezés** helyett **eCommercePurchases** értékre.</span><span class="sxs-lookup"><span data-stu-id="49b90-133">In the **Name** field on the side pane, rename your data source from **Query** to **eCommercePurchases**.</span></span>

1. <span data-ttu-id="49b90-134">Az adatforrások mentése.</span><span class="sxs-lookup"><span data-stu-id="49b90-134">Save the data source.</span></span>


### <a name="ingest-customer-data-from-loyalty-schema"></a><span data-ttu-id="49b90-135">Ügyféladatok bevitele a hűségsémából</span><span class="sxs-lookup"><span data-stu-id="49b90-135">Ingest customer data from loyalty schema</span></span>

1. <span data-ttu-id="49b90-136">Hozzon létre egy adatforrást, melynek neve **LoyaltyScheme**, majd válassza az importálás lehetőséget, és jelölje ki a **Text/CSV** csatlakozót.</span><span class="sxs-lookup"><span data-stu-id="49b90-136">Create a data source named **LoyaltyScheme**, choose the import option, and select the **Text/CSV** connector.</span></span>

1. <span data-ttu-id="49b90-137">Adja meg az URL-címét az eCommerce kapcsolattartóknak https://aka.ms/ciadclasscustomerloyalty.</span><span class="sxs-lookup"><span data-stu-id="49b90-137">Enter the URL for eCommerce contacts https://aka.ms/ciadclasscustomerloyalty.</span></span>

1. <span data-ttu-id="49b90-138">Az adatok szerkesztése közben válassza az **Átalakítás** lehetőséget, majd a **Használja az első sort fejlécként** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="49b90-138">While editing the data, select **Transform** and then **Use First Row as Headers**.</span></span>

1. <span data-ttu-id="49b90-139">Frissítse az adattípust az alább felsorolt oszlopokhoz:</span><span class="sxs-lookup"><span data-stu-id="49b90-139">Update the datatype for the columns listed below:</span></span>
   - <span data-ttu-id="49b90-140">**SzületésiDátum**: Dátum</span><span class="sxs-lookup"><span data-stu-id="49b90-140">**DateOfBirth**: Date</span></span>
   - <span data-ttu-id="49b90-141">**JutalmazásiPontok**: Egész Szám</span><span class="sxs-lookup"><span data-stu-id="49b90-141">**RewardsPoints**: Whole Number</span></span>
   - <span data-ttu-id="49b90-142">**KészültEkkor**: Dátum/Idő</span><span class="sxs-lookup"><span data-stu-id="49b90-142">**CreatedOn**: Date/Time</span></span>

1. <span data-ttu-id="49b90-143">A **Név** mezőben, a jobb oldali panelen, nevezze át az adatforrását **Lekérdezés** helyett **loyCustomers** értékre.</span><span class="sxs-lookup"><span data-stu-id="49b90-143">In the **Name** field on the right-hand pane, rename your data source from **Query** to **loyCustomers**.</span></span>

1. <span data-ttu-id="49b90-144">Az adatforrások mentése.</span><span class="sxs-lookup"><span data-stu-id="49b90-144">Save the data source.</span></span>

## <a name="task-2---data-unification"></a><span data-ttu-id="49b90-145">2. feladat - Adatok egységesítése</span><span class="sxs-lookup"><span data-stu-id="49b90-145">Task 2 - Data unification</span></span>

<span data-ttu-id="49b90-146">Az adatok bevitele után elkezdhetjük a **Megfeleltetés/Egyeztetés/Egyesítés** folyamatot, hogy hogy létrehozzunk egy egyesített ügyfélprofilt.</span><span class="sxs-lookup"><span data-stu-id="49b90-146">After ingesting the data we now begin the **Map, Match, Merge** process to create a unified customer profile.</span></span> <span data-ttu-id="49b90-147">További információkért lásd: [Adatok egységesítése](data-unification.md).</span><span class="sxs-lookup"><span data-stu-id="49b90-147">For more information, see [Data unification](data-unification.md).</span></span>

### <a name="map"></a><span data-ttu-id="49b90-148">Map</span><span class="sxs-lookup"><span data-stu-id="49b90-148">Map</span></span>

1. <span data-ttu-id="49b90-149">Az adatok betáplálása után képezze le a kapcsolattartókat az eCommerce-ből és a Loyalty data-ból a közös adattípusokba.</span><span class="sxs-lookup"><span data-stu-id="49b90-149">After ingesting the data, map contacts from eCommerce and Loyalty data to common data types.</span></span> <span data-ttu-id="49b90-150">Nyissa meg az **Adatok** > **Egységesítés** > **Megfeleltetés**-t.</span><span class="sxs-lookup"><span data-stu-id="49b90-150">Go to **Data** > **Unify** > **Map**.</span></span>

2. <span data-ttu-id="49b90-151">Válassza ki az entitást, amely jelképezi az ügyfélprofilt – **eCommerceContacts** és **loyCustomers**.</span><span class="sxs-lookup"><span data-stu-id="49b90-151">Select the entities that represent the customer profile – **eCommerceContacts** and **loyCustomers**.</span></span>

   ![az ecommerce és a loyality adatforrások egységesítése.](media/unify-ecommerce-loyalty.png)

3. <span data-ttu-id="49b90-153">Jelölje ki a **ContactId**-t elsődleges kulcsaként az **eCommerceContacts**-hoz és a **LoyaltyID** a **loyCustomers** elsődleges kulcsaként.</span><span class="sxs-lookup"><span data-stu-id="49b90-153">Select **ContactId** as the primary key for **eCommerceContacts** and **LoyaltyID** as the primary key for **loyCustomers**.</span></span>

   ![A LoyaltyId egyesítheti elsődleges kulcsként.](media/unify-loyaltyid.png)

### <a name="match"></a><span data-ttu-id="49b90-155">Egyeztetés</span><span class="sxs-lookup"><span data-stu-id="49b90-155">Match</span></span>

1. <span data-ttu-id="49b90-156">Ugorjon az **Egyeztetés** lapra és válassza a **Sorrend beállítását**.</span><span class="sxs-lookup"><span data-stu-id="49b90-156">Go to the **Match** tab and select **Set Order**.</span></span>

2. <span data-ttu-id="49b90-157">Az **Elsődleges** legördülő listában válassza az **eCommerceContacts : eCommerce** lehetőséget elsődleges forrásként, amely minden rekordot magában foglal.</span><span class="sxs-lookup"><span data-stu-id="49b90-157">In the **Primary** drop-down list, choose **eCommerceContacts : eCommerce** as the primary source and include all records.</span></span>

3. <span data-ttu-id="49b90-158">Az **Entitás 2** legördülő listájában válassza ki a **loyCustomers: LoyaltyScheme** lehetőséget, és adja meg az összes rekordot.</span><span class="sxs-lookup"><span data-stu-id="49b90-158">In the **Entity 2** drop-down list, choose **loyCustomers : LoyaltyScheme** and include all records.</span></span>

   ![Az egységesítéshez egyeztesse az eCommerce-t és a Loyality-t.](media/unify-match-order.png)

4. <span data-ttu-id="49b90-160">Válassza az **Új szabály létrehozása** menüpontot</span><span class="sxs-lookup"><span data-stu-id="49b90-160">Select **Create a new rule**</span></span>

5. <span data-ttu-id="49b90-161">Adja hozzá az első feltételt a FullName segítségével.</span><span class="sxs-lookup"><span data-stu-id="49b90-161">Add your first condition using FullName.</span></span>

   - <span data-ttu-id="49b90-162">Az eCommerceContacts lehetőséghez válassza ki a **FullName** opciót a legördülő listából.</span><span class="sxs-lookup"><span data-stu-id="49b90-162">For eCommerceContacts select **FullName** in the drop-down.</span></span>
   - <span data-ttu-id="49b90-163">A loyCustumers lehetőséghez válassza ki a **FullName** opciót a legördülő listából.</span><span class="sxs-lookup"><span data-stu-id="49b90-163">For loyCustomers select **FullName** in the drop-down.</span></span>
   - <span data-ttu-id="49b90-164">Jelölje ki a **Normalizálás** legördülő parancsot, és válassza a **Típus (Telefon, Név, Cím,...)** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="49b90-164">Select the **Normalize** drop down and choose **Type (Phone, Name, Address, ...)**.</span></span>
   - <span data-ttu-id="49b90-165">Állítsa be a **Pontossági szintet**: **Alap** és **Érték**: **Magas**-ra.</span><span class="sxs-lookup"><span data-stu-id="49b90-165">Set **Precision Level**: **Basic** and **Value**: **High**.</span></span>

6. <span data-ttu-id="49b90-166">Adja meg a nevét **FullName, Email**, az új szabályhoz.</span><span class="sxs-lookup"><span data-stu-id="49b90-166">Enter the name **FullName, Email** for the new rule.</span></span>

   - <span data-ttu-id="49b90-167">Másik feltétel hozzáadása az e-mail címhez a **Feltétel hozzáadása** lehetőség választásával.</span><span class="sxs-lookup"><span data-stu-id="49b90-167">Add a second condition for email address by selecting **Add Condition**</span></span>
   - <span data-ttu-id="49b90-168">Az eCommerceContacts entitáshoz válassza az **Email** legördülő lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="49b90-168">For entity eCommerceContacts, choose **EMail** in drop-down.</span></span>
   - <span data-ttu-id="49b90-169">Az loyCustomers entitáshoz válassza az **Email** legördülő lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="49b90-169">For entity loyCustomers, choose **EMail** in the drop-down.</span></span>
   - <span data-ttu-id="49b90-170">Hagyja üresen a Normalizálást.</span><span class="sxs-lookup"><span data-stu-id="49b90-170">Leave Normalize blank.</span></span>
   - <span data-ttu-id="49b90-171">Állítsa be a **Pontossági szintet**: **Alap** és **Érték**: **Magas**-ra.</span><span class="sxs-lookup"><span data-stu-id="49b90-171">Set **Precision Level**: **Basic** and **Value**: **High**.</span></span>

   ![Egységesítése az egyezési szabályt a névhez és az e-mailhez.](media/unify-match-rule.png)

7. <span data-ttu-id="49b90-173">Válassza a **Mentés** és **Futtatás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="49b90-173">Select **Save** and **Run**.</span></span>

### <a name="merge"></a><span data-ttu-id="49b90-174">Összefűzés</span><span class="sxs-lookup"><span data-stu-id="49b90-174">Merge</span></span>

1. <span data-ttu-id="49b90-175">Nyissa meg az **Egyesítés** lapot.</span><span class="sxs-lookup"><span data-stu-id="49b90-175">Go to the **Merge** tab.</span></span>

1. <span data-ttu-id="49b90-176">A **ContactId** **loyCustomers** entitáshoz változtassa meg a megjelenítendő nevet **ContactIdLOYALTY**-ra, hogy megkülönböztethesse azt a többi betáplált azonosítóval.</span><span class="sxs-lookup"><span data-stu-id="49b90-176">On the **ContactId** for **loyCustomers** entity, change the display name to **ContactIdLOYALTY** to differentiate it from the other IDs ingested.</span></span>

   ![nevezze át a loyalty azonosítót contactid-re.](media/unify-merge-contactid.png)

1. <span data-ttu-id="49b90-178">Válassza a **Mentés** és **Futtatás** lehetőséget, hogy elindítsa a Egyesítés Folyamatot.</span><span class="sxs-lookup"><span data-stu-id="49b90-178">Select **Save** and **Run** to start the Merge Process.</span></span>

## <a name="task-3---configure-product-recommendation-prediction"></a><span data-ttu-id="49b90-179">3. feladat – Termékjavaslat előrejelzés létrehozása</span><span class="sxs-lookup"><span data-stu-id="49b90-179">Task 3 - Configure product recommendation prediction</span></span>

<span data-ttu-id="49b90-180">Az egységesített ügyfélprofilok elkészítése után, előfizetés lemorzsolódási előrejelzést futtathatunk.</span><span class="sxs-lookup"><span data-stu-id="49b90-180">With the unified customer profiles in place, we can now run the subscription churn prediction.</span></span>

1. <span data-ttu-id="49b90-181">Válassza az **Információk** > **Előrejelzés** helyre, és válassza a **Termékjavaslat** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="49b90-181">Go to **Intelligence** > **Prediction** choose **Product recommendation**.</span></span>

1. <span data-ttu-id="49b90-182">Válassza az **Első lépések** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="49b90-182">Select **Get started**.</span></span>

1. <span data-ttu-id="49b90-183">Nevezze el a modellt **OOB termékjavaslatmodell-előrejelzés** értékre, és a kimeneti entitást **OOBProductRecommendationModelPrediction** értékre.</span><span class="sxs-lookup"><span data-stu-id="49b90-183">Name the model **OOB Product Recommendation Model Prediction** and the output entity **OOBProductRecommendationModelPrediction**.</span></span>

1. <span data-ttu-id="49b90-184">Határozzon meg három feltételt a modellhez.</span><span class="sxs-lookup"><span data-stu-id="49b90-184">Define three conditions for the model:</span></span>

   - <span data-ttu-id="49b90-185">**Termékek száma**: Állítsa ezt az értéket **5**-re.</span><span class="sxs-lookup"><span data-stu-id="49b90-185">**Number of products**: Set this value to **5**.</span></span> <span data-ttu-id="49b90-186">Ez a beállítás határozza meg, hogy hány terméket szeretne javasolni az ügyfeleknek.</span><span class="sxs-lookup"><span data-stu-id="49b90-186">This setting defines how many products you want to recommend to your customers.</span></span>

   - <span data-ttu-id="49b90-187">**Javasol olyan termékeket, amelyeket az ügyfelek a közelmúltban vásároltak?**: Válassza az **Igen** lehetőséget, ha jelezni szeretné, hogy a javaslatban az ügyfelek által korábban megvásárolt termékeket szeretne szerepeltetni.</span><span class="sxs-lookup"><span data-stu-id="49b90-187">**Suggest products customers have recently purchased?**: Select **Yes** to indicate that you want to include products in the recommendation that your customers have purchased before.</span></span>

   - <span data-ttu-id="49b90-188">**Visszatekintő ablak**: Jelöljön ki legalább **365 napot**.</span><span class="sxs-lookup"><span data-stu-id="49b90-188">**Look back window:** Select at least **365 days**.</span></span> <span data-ttu-id="49b90-189">Ez a beállítás határozza meg, hogy mennyi időre visszamenőleg vizsgálja meg a modell az ügyféltevékenységét, amelyet felhasznál a javaslataihoz.</span><span class="sxs-lookup"><span data-stu-id="49b90-189">This setting defines how far the model will look back at the customer's activity to use it as input to their recommendations.</span></span>
   
   :::image type="content" source="media/product-recommendation-model-preferences.png" alt-text="Modellbeállítások a termékjavaslati modellhez.":::

1. <span data-ttu-id="49b90-191">Válassza ki a **Szükséges adatok** menüt, és ott válassza az **Adatok hozzáadása** lehetőséget a vásárlási előzményekhez.</span><span class="sxs-lookup"><span data-stu-id="49b90-191">Select **Required data** and select **Add data** for purchase history.</span></span>

1. <span data-ttu-id="49b90-192">Adja hozzá a **eCommercePurchases: eCommerce** entitást és képezze le a mezőket az eCommerce-ről a megfelelő mezőkre, melyek modell által megköveteltek.</span><span class="sxs-lookup"><span data-stu-id="49b90-192">Add the **eCommercePurchases : eCommerce** entity and map the fields from eCommerce to the corresponding fields required by the model.</span></span>

1. <span data-ttu-id="49b90-193">Csatlakozzon az **eCommercePurchases: eCommerce** entitáshoz az **eCommerceContacts: eCommerce**-szel.</span><span class="sxs-lookup"><span data-stu-id="49b90-193">Join the **eCommercePurchases : eCommerce** entity with **eCommerceContacts : eCommerce**.</span></span>

   ![Csatlakoztassa az eCommerce entitásokhoz.](media/model-purchase-join.png)

1. <span data-ttu-id="49b90-195">Válassza a **Következő** lehetőséget a modell ütemezésének beállításához.</span><span class="sxs-lookup"><span data-stu-id="49b90-195">Select **Next** to set the model schedule.</span></span>

   <span data-ttu-id="49b90-196">A modell rendszeres betanítást igényel ahhoz, hogy új mintákat tanulhasson, amikor új adatok kerülnek a rendszerbe.</span><span class="sxs-lookup"><span data-stu-id="49b90-196">The model needs to train regularly to learn new patterns when there is new data ingested.</span></span> <span data-ttu-id="49b90-197">Ennél a példánál válassza a **Havonta** beállítást.</span><span class="sxs-lookup"><span data-stu-id="49b90-197">For this example, select **Monthly**.</span></span>

1. <span data-ttu-id="49b90-198">A részletek áttekintése után válassza a **Mentés és Futtatás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="49b90-198">After reviewing all the details, select **Save and Run**.</span></span>


## <a name="task-4---review-model-results-and-explanations"></a><span data-ttu-id="49b90-199">4. feladat – Modell eredmények és a magyarázatok áttekintése</span><span class="sxs-lookup"><span data-stu-id="49b90-199">Task 4 - Review model results and explanations</span></span>

<span data-ttu-id="49b90-200">Hagyja, hogy a modell teljesítse az adatok betanítását és pontozását.</span><span class="sxs-lookup"><span data-stu-id="49b90-200">Let the model complete the training and scoring of the data.</span></span> <span data-ttu-id="49b90-201">Most már megtekintheti a termékjavaslat modell magyarázatait.</span><span class="sxs-lookup"><span data-stu-id="49b90-201">You can now review the product recommendation model explanations.</span></span> <span data-ttu-id="49b90-202">További tudnivalókért olvassa el az [Előrejelzés állapotának és eredmények áttekintése](predict-subscription-churn.md#review-a-prediction-status-and-results) című témakört.</span><span class="sxs-lookup"><span data-stu-id="49b90-202">For more information, see [Review a prediction status and results](predict-subscription-churn.md#review-a-prediction-status-and-results).</span></span>

## <a name="task-5---create-a-segment-of-high-purchased-products"></a><span data-ttu-id="49b90-203">5. feladat – A gyakran megvásárolt termékek szegmensének létrehozása</span><span class="sxs-lookup"><span data-stu-id="49b90-203">Task 5 - Create a segment of high purchased products</span></span>

<span data-ttu-id="49b90-204">Futtatva a termékjavaslati modellt, létrehozhat egy új entitást, amelyet láthat a **Adat** > **Entitások**-nál.</span><span class="sxs-lookup"><span data-stu-id="49b90-204">Running the production model creates a new entity that you can see in **Data** > **Entities**.</span></span>

<span data-ttu-id="49b90-205">Létrehozhat egy új szegmenst, a modell által létrehozott entitás alapján.</span><span class="sxs-lookup"><span data-stu-id="49b90-205">You can create a new segment based on the entity created by the model.</span></span>

1. <span data-ttu-id="49b90-206">Kattintson a **Szegmensek** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="49b90-206">Go to **Segments**.</span></span> <span data-ttu-id="49b90-207">Válassza az **Új** lehetőséget, és válassza a **Létrehozás a következőkből** > **Intelligencia**.</span><span class="sxs-lookup"><span data-stu-id="49b90-207">Select **New** and choose **Create from** > **Intelligence**.</span></span>

   ![Szegmens létrehozása a modell kimenetével.](media/segment-intelligence.png)

1. <span data-ttu-id="49b90-209">Válassza ki a **OOBProductRecommendationModelPrediction** végpontot és definiálja a szegmenst:</span><span class="sxs-lookup"><span data-stu-id="49b90-209">Select the **OOBProductRecommendationModelPrediction** endpoint and define the segment:</span></span>

   - <span data-ttu-id="49b90-210">Mező: ProductID</span><span class="sxs-lookup"><span data-stu-id="49b90-210">Field: ProductID</span></span>
   - <span data-ttu-id="49b90-211">Operátor: Érték</span><span class="sxs-lookup"><span data-stu-id="49b90-211">Operator: Value</span></span>
   - <span data-ttu-id="49b90-212">Érték: Válassza ki a három legnépszerűbb termékazonosítót</span><span class="sxs-lookup"><span data-stu-id="49b90-212">Value: Select the top three product IDs</span></span>

   :::image type="content" source="media/product-recommendation-quick-segment.png" alt-text="Hozzon létre egy szegmenst a modell eredményeiből.":::

<span data-ttu-id="49b90-214">Most van egy dinamikusan frissített szegmense, amely azonosítja azokat az ügyfeleket, akik valószínűbb, hogy megvásárolják három leginkább javasolt terméket</span><span class="sxs-lookup"><span data-stu-id="49b90-214">You now have a segment that is dynamically updated which identifies the customers who are more willing to purchase the three most recommended products</span></span> 

<span data-ttu-id="49b90-215">További információ: [Szegmensek létrehozása és kezelése](segments.md).</span><span class="sxs-lookup"><span data-stu-id="49b90-215">For more information, see [Create and manage segments](segments.md).</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]