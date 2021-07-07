---
title: Ügyfélélettartam-érték előrejelzése mintaútmutató
description: Ezzel a mintaútmutatóval próbálhatja ki az ügyfélélettartam-érték előrejelzése modellt.
ms.date: 05/25/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: tutorial
author: yashlundia
ms.author: yalundia
manager: shellyha
ms.openlocfilehash: 19c1fbadb79ba22c0dc11aa7c3b5b2415add70a7
ms.sourcegitcommit: 0b754d194d765afef70d1008db7b347dd1f0ee40
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/24/2021
ms.locfileid: "6306352"
---
# <a name="customer-lifetime-value-clv-prediction-sample-guide"></a><span data-ttu-id="3c033-103">Ügyfélélettartam-érték (CLV) előrejelzés mintaútmutató</span><span class="sxs-lookup"><span data-stu-id="3c033-103">Customer lifetime value (CLV) prediction sample guide</span></span>

<span data-ttu-id="3c033-104">Ez az útmutató a mintaadatok felhasználásával átfogóan ismerteti az Ügyfél élettartamra vetített értékének (CLV) előrejelzését a Customer Insights alkalmazásban.</span><span class="sxs-lookup"><span data-stu-id="3c033-104">This guide will walk you through an end to end example of Customer lifetime value (CLV) prediction in Customer Insights using sample data.</span></span>

## <a name="scenario"></a><span data-ttu-id="3c033-105">Forgatókönyv</span><span class="sxs-lookup"><span data-stu-id="3c033-105">Scenario</span></span>

<span data-ttu-id="3c033-106">A Contoso kiváló minőségű kávékat és kávéfőzőket gyártó vállalat.</span><span class="sxs-lookup"><span data-stu-id="3c033-106">Contoso is a company that produces high-quality coffee and coffee machines.</span></span> <span data-ttu-id="3c033-107">A termékeket a Contoso Coffee weboldalán keresztül értékesítik.</span><span class="sxs-lookup"><span data-stu-id="3c033-107">They sell the products through their Contoso Coffee website.</span></span> <span data-ttu-id="3c033-108">A vállalat meg akarja érteni azt az értéket (bevételt), amelyet ügyfeleik a következő 12 hónapban generálhatnak.</span><span class="sxs-lookup"><span data-stu-id="3c033-108">The company wants to understand the value (revenue) that their customers can generate in the next 12 months.</span></span> <span data-ttu-id="3c033-109">Ismerve az ügyfeleik várható értékét a következő 12 hónapra vonatkozóan segít nekik a marketingerőfeszítéseiket a nagy értékű ügyfelek felé irányítani.</span><span class="sxs-lookup"><span data-stu-id="3c033-109">Knowing the expected value of their customers in the next 12 months will help them steer their marketing efforts on high value customers.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3c033-110">Előfeltételek</span><span class="sxs-lookup"><span data-stu-id="3c033-110">Prerequisites</span></span>

- <span data-ttu-id="3c033-111">Legalább [közreműködői engedély](permissions.md) a célközönség betekintési információihoz.</span><span class="sxs-lookup"><span data-stu-id="3c033-111">At least [Contributor permissions](permissions.md) in audience insights.</span></span>
- <span data-ttu-id="3c033-112">Javasoljuk, hogy a következő lépéseket hajtsa végre [egy új környezetben](manage-environments.md).</span><span class="sxs-lookup"><span data-stu-id="3c033-112">We recommend that you implement the following steps [in a new environment](manage-environments.md).</span></span>

## <a name="task-1---ingest-data"></a><span data-ttu-id="3c033-113">1. Feladat - Adatok betáplálása</span><span class="sxs-lookup"><span data-stu-id="3c033-113">Task 1 - Ingest data</span></span>

<span data-ttu-id="3c033-114">Tekintse át az [adatbetöltéssel kapcsolatos információk](data-sources.md) és az [adatforrások importálása Power Query csatlakozók használatával](connect-power-query.md) cikkeket.</span><span class="sxs-lookup"><span data-stu-id="3c033-114">Review the articles [about data ingestion](data-sources.md) and [importing data sources using Power Query connectors](connect-power-query.md).</span></span> <span data-ttu-id="3c033-115">A következő információk azt feltételezik, hogy megismerkedett a betáplált adatokkal általánosságban.</span><span class="sxs-lookup"><span data-stu-id="3c033-115">The following information assumes you familiarized with ingesting data in general.</span></span>

### <a name="ingest-customer-data-from-ecommerce-platform"></a><span data-ttu-id="3c033-116">Betáplált ügyféladatok az eCommerce platformról.</span><span class="sxs-lookup"><span data-stu-id="3c033-116">Ingest customer data from eCommerce platform</span></span>

1. <span data-ttu-id="3c033-117">Hozzon létre egy adatforrást, elnevezve **eCommerce-nek**, majd válassza az importálás lehetőséget, és jelölje ki a **Szöveg/CSV** összekötőt.</span><span class="sxs-lookup"><span data-stu-id="3c033-117">Create a data source named  **eCommerce** , choose the import option, and select the **Text/CSV** connector.</span></span>

1. <span data-ttu-id="3c033-118">Adja meg az URL-címét az eCommerce kapcsolattartóknak [https://aka.ms/ciadclasscontacts](https://aka.ms/ciadclasscontacts).</span><span class="sxs-lookup"><span data-stu-id="3c033-118">Enter the URL for eCommerce contacts [https://aka.ms/ciadclasscontacts](https://aka.ms/ciadclasscontacts).</span></span>

1. <span data-ttu-id="3c033-119">Az adatok szerkesztése közben válassza az **Átalakítás** lehetőséget, majd a **Használja az első sort fejlécként** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="3c033-119">While editing the data, select  **Transform**  and then  **Use First Row as Headers**.</span></span>

1. <span data-ttu-id="3c033-120">Frissítse az adattípust az alább felsorolt oszlopokhoz:</span><span class="sxs-lookup"><span data-stu-id="3c033-120">Update the datatype for the columns listed below:</span></span>
   - <span data-ttu-id="3c033-121">**SzületésiDátum**: Dátum</span><span class="sxs-lookup"><span data-stu-id="3c033-121">**DateOfBirth** : Date</span></span>
   - <span data-ttu-id="3c033-122">**CreatedOn**: Dátum/Idő/Zóna</span><span class="sxs-lookup"><span data-stu-id="3c033-122">**CreatedOn** : Date/Time/Zone</span></span>

   :::image type="content" source="media/ecommerce-dob-date.PNG" alt-text="A születési dátum átalakítása dátummá.":::

1. <span data-ttu-id="3c033-124">A jobb oldali panelben a "Név" mezőben nevezze át az adatforrását a **Lekérdezés**-ről **eCommerceContacts**-ra.</span><span class="sxs-lookup"><span data-stu-id="3c033-124">In the 'Name' field on the right-hand pane, rename your data source from **Query** to **eCommerceContacts**</span></span>

1. <span data-ttu-id="3c033-125">**Mentse** az adatforrást.</span><span class="sxs-lookup"><span data-stu-id="3c033-125">**Save** the data source.</span></span>

### <a name="ingest-online-purchase-data"></a><span data-ttu-id="3c033-126">Online vásárlási adatok betáplálása.</span><span class="sxs-lookup"><span data-stu-id="3c033-126">Ingest online purchase data</span></span>

1. <span data-ttu-id="3c033-127">Adjon hozzá egy újabb adatforrást a megegyező **eCommerce** adatforráshoz.</span><span class="sxs-lookup"><span data-stu-id="3c033-127">Add another data set to the same **eCommerce** data source.</span></span> <span data-ttu-id="3c033-128">Válassza a **Text/CSV** csatlakozót újra.</span><span class="sxs-lookup"><span data-stu-id="3c033-128">Choose the **Text/CSV** connector again.</span></span>

1. <span data-ttu-id="3c033-129">Adja meg az URL-címét az **Online vásárlas** adataihoz https://aka.ms/ciadclassonline.</span><span class="sxs-lookup"><span data-stu-id="3c033-129">Enter the URL for **Online Purchases** data https://aka.ms/ciadclassonline.</span></span>

1. <span data-ttu-id="3c033-130">Az adatok szerkesztése közben válassza az **Átalakítás** lehetőséget, majd a **Használja az első sort fejlécként** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="3c033-130">While editing the data, select **Transform** and then **Use First Row as Headers**.</span></span>

1. <span data-ttu-id="3c033-131">Frissítse az adattípust az alább felsorolt oszlopokhoz:</span><span class="sxs-lookup"><span data-stu-id="3c033-131">Update the datatype for the columns listed below:</span></span>
   - <span data-ttu-id="3c033-132">**PurchasedOn** : Dátum/Idő</span><span class="sxs-lookup"><span data-stu-id="3c033-132">**PurchasedOn**: Date/Time</span></span>
   - <span data-ttu-id="3c033-133">**TotalPrice** : Pénznem</span><span class="sxs-lookup"><span data-stu-id="3c033-133">**TotalPrice**: Currency</span></span>

1. <span data-ttu-id="3c033-134">A **Név** mezőben az oldalsó panelen, nevezze át az adatforrását a **Lekérdezés** helyett **eCommercePurchases** értékre.</span><span class="sxs-lookup"><span data-stu-id="3c033-134">In the **Name** field on the side pane, rename your data source from **Query** to **eCommercePurchases**.</span></span>

1. <span data-ttu-id="3c033-135">**Mentse** az adatforrást.</span><span class="sxs-lookup"><span data-stu-id="3c033-135">**Save** the data source.</span></span>

### <a name="ingest-customer-data-from-loyalty-schema"></a><span data-ttu-id="3c033-136">Ügyféladatok bevitele a hűségsémából</span><span class="sxs-lookup"><span data-stu-id="3c033-136">Ingest customer data from loyalty schema</span></span>

1. <span data-ttu-id="3c033-137">Hozzon létre egy adatforrást, melynek neve **LoyaltyScheme**, majd válassza az importálás lehetőséget, és jelölje ki a **Text/CSV** csatlakozót.</span><span class="sxs-lookup"><span data-stu-id="3c033-137">Create a data source named **LoyaltyScheme**, choose the import option, and select the **Text/CSV** connector.</span></span>

1. <span data-ttu-id="3c033-138">Adja meg az URL-címét az eCommerce kapcsolattartóknak https://aka.ms/ciadclasscustomerloyalty.</span><span class="sxs-lookup"><span data-stu-id="3c033-138">Enter the URL for eCommerce contacts https://aka.ms/ciadclasscustomerloyalty.</span></span>

1. <span data-ttu-id="3c033-139">Az adatok szerkesztése közben válassza az **Átalakítás** lehetőséget, majd a **Használja az első sort fejlécként** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="3c033-139">While editing the data, select **Transform** and then **Use First Row as Headers**.</span></span>

1. <span data-ttu-id="3c033-140">Frissítse az adattípust az alább felsorolt oszlopokhoz:</span><span class="sxs-lookup"><span data-stu-id="3c033-140">Update the datatype for the columns listed below:</span></span>
   - <span data-ttu-id="3c033-141">**SzületésiDátum**: Dátum</span><span class="sxs-lookup"><span data-stu-id="3c033-141">**DateOfBirth**: Date</span></span>
   - <span data-ttu-id="3c033-142">**JutalmazásiPontok**: Egész Szám</span><span class="sxs-lookup"><span data-stu-id="3c033-142">**RewardsPoints**: Whole Number</span></span>
   - <span data-ttu-id="3c033-143">**KészültEkkor**: Dátum/Idő</span><span class="sxs-lookup"><span data-stu-id="3c033-143">**CreatedOn**: Date/Time</span></span>

1. <span data-ttu-id="3c033-144">A **Név** mezőben, a jobb oldali panelen, nevezze át az adatforrását **Lekérdezés** helyett **loyCustomers** értékre.</span><span class="sxs-lookup"><span data-stu-id="3c033-144">In the **Name** field on the right-hand pane, rename your data source from **Query** to **loyCustomers**.</span></span>

1. <span data-ttu-id="3c033-145">**Mentse** az adatforrást.</span><span class="sxs-lookup"><span data-stu-id="3c033-145">**Save** the data source.</span></span>

### <a name="ingest-customer-data-from-website-reviews"></a><span data-ttu-id="3c033-146">Tápláljon be ügyféladatokat a webhely értékelésekből.</span><span class="sxs-lookup"><span data-stu-id="3c033-146">Ingest customer data from website reviews</span></span>

1. <span data-ttu-id="3c033-147">Hozzon létre egy adatforrást, **eCommerce** néven, majd válassza az importálás lehetőséget, és jelölje ki a **Text/CSV** csatlakozót.</span><span class="sxs-lookup"><span data-stu-id="3c033-147">Create a data source named **Website**, choose the import option, and select the **Text/CSV** connector.</span></span>

1. <span data-ttu-id="3c033-148">Adja meg az URL-címét az eCommerce kapcsolattartóknak https://aka.ms/CI-ILT/WebReviews.</span><span class="sxs-lookup"><span data-stu-id="3c033-148">Enter the URL for eCommerce contacts https://aka.ms/CI-ILT/WebReviews.</span></span>

1. <span data-ttu-id="3c033-149">Az adatok szerkesztése közben válassza az **Átalakítás** lehetőséget, majd a **Használja az első sort fejlécként** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="3c033-149">While editing the data, select **Transform** and then **Use First Row as Headers**.</span></span>

1. <span data-ttu-id="3c033-150">Frissítse az adattípust az alább felsorolt oszlopokhoz:</span><span class="sxs-lookup"><span data-stu-id="3c033-150">Update the datatype for the columns listed below:</span></span>

   - <span data-ttu-id="3c033-151">**ReviewRating**: Decimális szám</span><span class="sxs-lookup"><span data-stu-id="3c033-151">**ReviewRating**: Decimal number</span></span>
   - <span data-ttu-id="3c033-152">**ÁttekintésDátuma**: Dátum</span><span class="sxs-lookup"><span data-stu-id="3c033-152">**ReviewDate**: Date</span></span>

1. <span data-ttu-id="3c033-153">A jobb oldali ablaktáblán található "Név" mezőben nevezze át a adatforrás **Lekérdezés** értékről **Vélemények** értékre.</span><span class="sxs-lookup"><span data-stu-id="3c033-153">In the 'Name' field on the right-hand pane, rename your data source from **Query** to **Reviews**.</span></span>

1. <span data-ttu-id="3c033-154">**Mentse** az adatforrást.</span><span class="sxs-lookup"><span data-stu-id="3c033-154">**Save** the data source.</span></span>

## <a name="task-2---data-unification"></a><span data-ttu-id="3c033-155">2. feladat - Adatok egységesítése</span><span class="sxs-lookup"><span data-stu-id="3c033-155">Task 2 - Data unification</span></span>

<span data-ttu-id="3c033-156">Az adatok betöltése után most elkezdjük az adategyesítési folyamatot, hogy egységes ügyfélprofilt hozzunk létre.</span><span class="sxs-lookup"><span data-stu-id="3c033-156">After ingesting the data, we now begin the data unification process to create a unified customer profile.</span></span> <span data-ttu-id="3c033-157">További információkért lásd: [Adatok egységesítése](data-unification.md).</span><span class="sxs-lookup"><span data-stu-id="3c033-157">For more information, see [Data unification](data-unification.md).</span></span>

### <a name="map"></a><span data-ttu-id="3c033-158">Map</span><span class="sxs-lookup"><span data-stu-id="3c033-158">Map</span></span>

1. <span data-ttu-id="3c033-159">Az adatok betáplálása után képezze le a kapcsolattartókat az eCommerce-ből és a Loyalty data-ból a közös adattípusokba.</span><span class="sxs-lookup"><span data-stu-id="3c033-159">After ingesting the data, map contacts from eCommerce and Loyalty data to common data types.</span></span> <span data-ttu-id="3c033-160">Nyissa meg az **Adatok** > **Egységesítés** > **Megfeleltetés**-t.</span><span class="sxs-lookup"><span data-stu-id="3c033-160">Go to **Data** > **Unify** > **Map**.</span></span>

1. <span data-ttu-id="3c033-161">Válassza ki az entitást, amely jelképezi az ügyfélprofilt – **eCommerceContacts** és **loyCustomers**.</span><span class="sxs-lookup"><span data-stu-id="3c033-161">Select the entities that represent the customer profile – **eCommerceContacts** and **loyCustomers**.</span></span> <span data-ttu-id="3c033-162">Ezután válassza az **Alkalmaz** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="3c033-162">Then, select **Apply**.</span></span>

   ![az ecommerce és a loyality adatforrások egységesítése.](media/unify-ecommerce-loyalty.png)

1. <span data-ttu-id="3c033-164">Jelölje ki a **ContactId**-t elsődleges kulcsaként az **eCommerceContacts**-hoz és a **LoyaltyID** a **loyCustomers** elsődleges kulcsaként.</span><span class="sxs-lookup"><span data-stu-id="3c033-164">Select **ContactId** as the primary key for **eCommerceContacts** and **LoyaltyID** as the primary key for **loyCustomers**.</span></span>

   ![A LoyaltyId egyesítheti elsődleges kulcsként.](media/unify-loyaltyid.png)

1. <span data-ttu-id="3c033-166">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="3c033-166">Select **Save**.</span></span>

### <a name="match"></a><span data-ttu-id="3c033-167">Egyeztetés</span><span class="sxs-lookup"><span data-stu-id="3c033-167">Match</span></span>

1. <span data-ttu-id="3c033-168">Ugorjon az **Egyeztetés** lapra és válassza a **Sorrend beállítását**.</span><span class="sxs-lookup"><span data-stu-id="3c033-168">Go to the **Match** tab and select **Set Order**.</span></span>

1. <span data-ttu-id="3c033-169">Az **Elsődleges** legördülő listában válassza az **eCommerceContacts : eCommerce** mint elsődleges forrást, és tartalmazza az összes rekordot.</span><span class="sxs-lookup"><span data-stu-id="3c033-169">In the **Primary** dropdown list, choose **eCommerceContacts : eCommerce** as the primary source and include all records.</span></span>

1. <span data-ttu-id="3c033-170">Az **Entitás 2** legördülő listában válassza a **loyCustomers: LoyaltyScheme** lehetőséget, és adja meg az összes rekordot.</span><span class="sxs-lookup"><span data-stu-id="3c033-170">In the **Entity 2** dropdown list, choose **loyCustomers : LoyaltyScheme** and include all records.</span></span>

   ![Az egységesítéshez egyeztesse az eCommerce-t és a Loyality-t.](media/unify-match-order.png)

1. <span data-ttu-id="3c033-172">Válassza a **Szabály hozzáadása** lehetőséget</span><span class="sxs-lookup"><span data-stu-id="3c033-172">Select **Add rule**</span></span>

1. <span data-ttu-id="3c033-173">Adja hozzá az első feltételt a FullName segítségével.</span><span class="sxs-lookup"><span data-stu-id="3c033-173">Add your first condition using FullName.</span></span>

   - <span data-ttu-id="3c033-174">Az eCommerceContacts esetében válassza a **FullName** lehetőséget a legördülő menüben.</span><span class="sxs-lookup"><span data-stu-id="3c033-174">For eCommerceContacts select **FullName** in the dropdown.</span></span>
   - <span data-ttu-id="3c033-175">A loyCustomers esetében válassza a **FullName** lehetőséget a legördülő menüben.</span><span class="sxs-lookup"><span data-stu-id="3c033-175">For loyCustomers select **FullName** in the dropdown.</span></span>
   - <span data-ttu-id="3c033-176">Válassza a **Normalizálás** legördülő menüt, és válassza a **Típus (Telefon, Név, Cím, ...)** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="3c033-176">Select the **Normalize** dropdown and choose **Type (Phone, Name, Address, ...)**.</span></span>
   - <span data-ttu-id="3c033-177">Állítsa be a **Pontossági szintet**: **Alap** és **Érték**: **Magas**-ra.</span><span class="sxs-lookup"><span data-stu-id="3c033-177">Set **Precision Level**: **Basic** and **Value**: **High**.</span></span>

1. <span data-ttu-id="3c033-178">Adja meg a nevét **FullName, Email**, az új szabályhoz.</span><span class="sxs-lookup"><span data-stu-id="3c033-178">Enter the name **FullName, Email** for the new rule.</span></span>

   - <span data-ttu-id="3c033-179">Másik feltétel hozzáadása az e-mail címhez a **Feltétel hozzáadása** lehetőség választásával.</span><span class="sxs-lookup"><span data-stu-id="3c033-179">Add a second condition for email address by selecting **Add Condition**</span></span>
   - <span data-ttu-id="3c033-180">Az entitás eCommerceContacts esetében válassza az **EMail** lehetőséget a legördülő menüben.</span><span class="sxs-lookup"><span data-stu-id="3c033-180">For entity eCommerceContacts, choose **EMail** in dropdown.</span></span>
   - <span data-ttu-id="3c033-181">Az entitás loyCustomers esetében válassza az **EMail** lehetőséget a legördülő menüben.</span><span class="sxs-lookup"><span data-stu-id="3c033-181">For entity loyCustomers, choose **EMail** in the dropdown.</span></span>
   - <span data-ttu-id="3c033-182">Hagyja üresen a Normalizálást.</span><span class="sxs-lookup"><span data-stu-id="3c033-182">Leave Normalize blank.</span></span>
   - <span data-ttu-id="3c033-183">Állítsa be a **Pontossági szintet**: **Alap** és **Érték**: **Magas**-ra.</span><span class="sxs-lookup"><span data-stu-id="3c033-183">Set **Precision Level**: **Basic** and **Value**: **High**.</span></span>

   ![Egységesítése az egyezési szabályt a névhez és az e-mailhez.](media/unify-match-rule.png)

1. <span data-ttu-id="3c033-185">Válassza a **Kész** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="3c033-185">Select **Done**.</span></span>

1. <span data-ttu-id="3c033-186">Válassza a **Mentés** és **Futtatás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="3c033-186">Select **Save** and **Run**.</span></span>

### <a name="merge"></a><span data-ttu-id="3c033-187">Összefűzés</span><span class="sxs-lookup"><span data-stu-id="3c033-187">Merge</span></span>

1. <span data-ttu-id="3c033-188">Nyissa meg az **Egyesítés** lapot.</span><span class="sxs-lookup"><span data-stu-id="3c033-188">Go to the **Merge** tab.</span></span>

1. <span data-ttu-id="3c033-189">A **ContactId** **loyCustomers** entitáshoz változtassa meg a megjelenítendő nevet **ContactIdLOYALTY**-ra, hogy megkülönböztethesse azt a többi betáplált azonosítóval.</span><span class="sxs-lookup"><span data-stu-id="3c033-189">On the **ContactId** for **loyCustomers** entity, change the display name to **ContactIdLOYALTY** to differentiate it from the other IDs ingested.</span></span>

   ![nevezze át a loyalty azonosítót contactid-re.](media/unify-merge-contactid.png)

1. <span data-ttu-id="3c033-191">Válassza a **Mentés**, majd az **Egyesítési és lefelé irányuló folyamatok futtatása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="3c033-191">Select **Save** and **Run merge and downstream processes**.</span></span>

## <a name="task-3---configure-customer-lifetime-value-prediction"></a><span data-ttu-id="3c033-192">3. feladat – Ügyfél élettartamra vetített értékének előrejelzése</span><span class="sxs-lookup"><span data-stu-id="3c033-192">Task 3 - Configure customer lifetime value prediction</span></span>

<span data-ttu-id="3c033-193">Az egységes ügyfélprofilok segítségével immár futtathatja az ügyfél élettartamra vetített értékének előrejelzését.</span><span class="sxs-lookup"><span data-stu-id="3c033-193">With the unified customer profiles in place, we can now run the customer lifetime value prediction.</span></span> <span data-ttu-id="3c033-194">A részletes lépésekért lásd: [Ügyfél élettartamra vetített értékének előrejelzése (előzetes verzió)](predict-customer-lifetime-value.md).</span><span class="sxs-lookup"><span data-stu-id="3c033-194">For detailed steps, see [Customer Lifetime Value prediction (preview)](predict-customer-lifetime-value.md).</span></span>

1. <span data-ttu-id="3c033-195">Lépjen az **Információk**  > **Előrejelzések** lapra, és válassza ki az **Ügyfél élettartamának értékmodellje** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="3c033-195">Go to  **Intelligence**  > **Predictions**  and select the **Customer lifetime value model**.</span></span>

1. <span data-ttu-id="3c033-196">Lépjen végig az oldalsó ablaktáblában található információkon, és válassza az **Első lépések** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="3c033-196">Go through the information in the side pane and select **Get started**.</span></span>

1. <span data-ttu-id="3c033-197">Nevezze el a modellt **OOB eCommerce CLV előrejelzés** névvel, a kimeneti entitás legyen **OOBeCommerceCLVPrediction**.</span><span class="sxs-lookup"><span data-stu-id="3c033-197">Name the model **OOB eCommerce CLV Prediction** and the output entity  **OOBeCommerceCLVPrediction**.</span></span>

1. <span data-ttu-id="3c033-198">A CLV modell modellbeállításainak meghatározása:</span><span class="sxs-lookup"><span data-stu-id="3c033-198">Define model preferences for the CLV model:</span></span>
   - <span data-ttu-id="3c033-199">**Előrejelzési időszak**: **12 hónap vagy 1 év**.</span><span class="sxs-lookup"><span data-stu-id="3c033-199">**Prediction time period**: **12 months or 1 year**.</span></span> <span data-ttu-id="3c033-200">Ez a beállítás határozza meg, hogy milyen időtávra legyen megbecsülve az ügyfél élettartamra vetített értéke.</span><span class="sxs-lookup"><span data-stu-id="3c033-200">This setting defines how far into the future to predict customer lifetime value.</span></span>
   - <span data-ttu-id="3c033-201">**Aktív ügyfelek**  : Adja meg, hogy az aktív ügyfelek mit jelentenek vállalkozása esetében.</span><span class="sxs-lookup"><span data-stu-id="3c033-201">**Active customers**: Specify what active customers mean for your business.</span></span> <span data-ttu-id="3c033-202">Állítsa be azt a múltbeli időkeretet, amelyekben az ügyfélnek legalább egy tranzakcióval rendelkeznie kell ahhoz, hogy aktívnak minősüljön.</span><span class="sxs-lookup"><span data-stu-id="3c033-202">Set the historical time frame in which a customer must have had at least one transaction to be considered active.</span></span> <span data-ttu-id="3c033-203">A modell csak az aktív ügyfelek CLV-jét fogja előre jelezni.</span><span class="sxs-lookup"><span data-stu-id="3c033-203">The model will only predict CLV for active customers.</span></span> <span data-ttu-id="3c033-204">Válasszon aközött, hogy a modell a korábbi tranzakciós adatok alapján számítsa ki az időszakot, vagy konkrét időkeret ad meg ehhez.</span><span class="sxs-lookup"><span data-stu-id="3c033-204">Choose between letting the model calculate the time period based on historical transaction data or provide a specific time frame.</span></span> <span data-ttu-id="3c033-205">Ebben a minta útmutatóban **a modell számíthatja ki a vásárlási intervallumot** lehetőséget használjuk, ami az alapértelmezett lehetőség.</span><span class="sxs-lookup"><span data-stu-id="3c033-205">In this sample guide, we **let the model calculate purchase interval**, which is the default option.</span></span>
   - <span data-ttu-id="3c033-206">**Nagy értékű ügyfelek**: Határozza meg a nagy értékű ügyfeleket a legjobban fizető ügyfelek percentiliseként.</span><span class="sxs-lookup"><span data-stu-id="3c033-206">**High value customers**: Define high value customers as a percentile of top-paying customers.</span></span> <span data-ttu-id="3c033-207">A modell ezt a bemenetet használja, hogy olyan eredményeket biztosítson, amelyek megfelelnek a vállalkozása nagy értékű ügyfelek definíciójának.</span><span class="sxs-lookup"><span data-stu-id="3c033-207">The model uses this input to provide results that fit your business definition of high value customers.</span></span> <span data-ttu-id="3c033-208">Választhatja azt, hogy a modell határozza meg a nagy értékű ügyfeleket.</span><span class="sxs-lookup"><span data-stu-id="3c033-208">You can choose to let the model define high value customers.</span></span> <span data-ttu-id="3c033-209">Egy heurisztikus szabályt használ, ami a percentilisből van származtatva.</span><span class="sxs-lookup"><span data-stu-id="3c033-209">It uses a heuristic rule that derives the percentile.</span></span> <span data-ttu-id="3c033-210">Meghatározhatja a nagy értékű ügyfeleket a jövőbeni legjobban fizető ügyfelek percentiliseként is.</span><span class="sxs-lookup"><span data-stu-id="3c033-210">You can also define high value customers as a percentile of top future paying customers.</span></span> <span data-ttu-id="3c033-211">Ebben a minta útmutatóban manuálisan határozzuk meg a nagy értékű ügyfeleket az **aktív fizető ügyfelek felső 30% -aként**, és a **Tovább** lehetőséget választjuk.</span><span class="sxs-lookup"><span data-stu-id="3c033-211">In this sample guide, we manually define high value customers as **top 30% of active paying customers** and select **Next**.</span></span>

    :::image type="content" source="media/clv-model-preferences.png" alt-text="Beállítások lépés az CLV-modell interaktív élményében.":::

1. <span data-ttu-id="3c033-213">A **Szükséges adatok** lépésben válassza az **Adatok hozzáadása** lehetőséget a tranzakcióelőzmények adatainak megadásához.</span><span class="sxs-lookup"><span data-stu-id="3c033-213">In the **Required Data** step, select **Add data** to provide the transaction history data.</span></span>

1. <span data-ttu-id="3c033-214">Adja hozzá az **eCommercePurchases : eCommerce** entitást, és képezze le a modell által megkövetelt attribútumokat:</span><span class="sxs-lookup"><span data-stu-id="3c033-214">Add the **eCommercePurchases : eCommerce** entity and map the attributes that are required by the model:</span></span>
   - <span data-ttu-id="3c033-215">Tranzakcióazonosító: eCommerce.eCommercePurchases.PurchaseId</span><span class="sxs-lookup"><span data-stu-id="3c033-215">Transaction ID: eCommerce.eCommercePurchases.PurchaseId</span></span>
   - <span data-ttu-id="3c033-216">Tranzakció dátuma: eCommerce.eCommercePurchases.PurchasedOn</span><span class="sxs-lookup"><span data-stu-id="3c033-216">Transaction date: eCommerce.eCommercePurchases.PurchasedOn</span></span>
   - <span data-ttu-id="3c033-217">Tranzakció összege: eCommerce.eCommercePurchases.TotalPrice</span><span class="sxs-lookup"><span data-stu-id="3c033-217">Transaction amount: eCommerce.eCommercePurchases.TotalPrice</span></span>
   - <span data-ttu-id="3c033-218">Termékazonosító: eCommerce.eCommercePurchases.ProductId</span><span class="sxs-lookup"><span data-stu-id="3c033-218">Product ID: eCommerce.eCommercePurchases.ProductId</span></span>

1. <span data-ttu-id="3c033-219">Válassza a **Következő** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="3c033-219">Select **Next**.</span></span>

1. <span data-ttu-id="3c033-220">Az **eCommercePurchases : eCommerce** entitás és az **eCommerceContacts : eCommerce** entitás közötti kapcsolat beállítása.</span><span class="sxs-lookup"><span data-stu-id="3c033-220">Set up the relationship between the **eCommercePurchases : eCommerce** entity and  **eCommerceContacts : eCommerce**.</span></span>

1. <span data-ttu-id="3c033-221">A **További adatok (opcionális)** lépés lehetővé teszi további ügyféltaktivitási adatok hozzáadását.</span><span class="sxs-lookup"><span data-stu-id="3c033-221">The **Additional data (optional)** step allows you to add more customer activity data.</span></span> <span data-ttu-id="3c033-222">Ezek az adatok segíthetnek abban, hogy több betekintést nyerjen a vállalkozásával folytatott ügyfélinterakciókkal kapcsolatosan, ami hozzájárulhat a CLV-hez.</span><span class="sxs-lookup"><span data-stu-id="3c033-222">This data can help to get more insights for customer interactions with your business, which can contribute to CLV.</span></span> <span data-ttu-id="3c033-223">Az olyan kulcsfontosságú ügyfél-interakciók hozzáadása, mint a webes naplók, ügyfélszolgálati naplók vagy a jutalomprogram előzményei javíthatják az előrejelzések pontosságát.</span><span class="sxs-lookup"><span data-stu-id="3c033-223">Adding key customer interactions like web logs, customer service logs, or rewards program history can improve the accuracy of predictions.</span></span> <span data-ttu-id="3c033-224">Válassza az **Adatok hozzáadása** lehetőséget, hogy további ügyféltevékenységi adatokat vegyen fel.</span><span class="sxs-lookup"><span data-stu-id="3c033-224">Select **Add data** to include more customer activity data.</span></span>

1. <span data-ttu-id="3c033-225">Adja hozzá az ügyféltevékenység entitást, és képezze le a mezők nevét a modell által megkövetelt megfelelő mezőkhöz:</span><span class="sxs-lookup"><span data-stu-id="3c033-225">Add the customer activity entity and map its fields names to the corresponding fields required by the model:</span></span>
   - <span data-ttu-id="3c033-226">Ügyféltevékenységek entitás: Reviews:Website</span><span class="sxs-lookup"><span data-stu-id="3c033-226">Customer activity entity: Reviews:Website</span></span>
   - <span data-ttu-id="3c033-227">Elsődleges kulcs: Website.Reviews.ReviewId</span><span class="sxs-lookup"><span data-stu-id="3c033-227">Primary key: Website.Reviews.ReviewId</span></span>
   - <span data-ttu-id="3c033-228">Időbélyeg: Website.Reviews.ReviewDate</span><span class="sxs-lookup"><span data-stu-id="3c033-228">Timestamp: Website.Reviews.ReviewDate</span></span>
   - <span data-ttu-id="3c033-229">Esemény (tevékenység neve): Website.Reviews.ActivityTypeDisplay</span><span class="sxs-lookup"><span data-stu-id="3c033-229">Event (activity name): Website.Reviews.ActivityTypeDisplay</span></span>
   - <span data-ttu-id="3c033-230">Részletek (összeg vagy érték): Website.Reviews.ReviewRating</span><span class="sxs-lookup"><span data-stu-id="3c033-230">Details (amount or value): Website.Reviews.ReviewRating</span></span>

1. <span data-ttu-id="3c033-231">Válassza a **Tovább** lehetőséget, és konfigurálja a tranzakciós adatok és az ügyféladatok közötti tevékenységet és kapcsolatot:</span><span class="sxs-lookup"><span data-stu-id="3c033-231">Select **Next** and configure the activity and the relationship between the transaction data and the customer data:</span></span>  
   - <span data-ttu-id="3c033-232">Aktivitás típusa: Meglévő kiválasztása</span><span class="sxs-lookup"><span data-stu-id="3c033-232">Activity type: Choose existing</span></span>
   - <span data-ttu-id="3c033-233">Tevékenység címkéje: Vélemény</span><span class="sxs-lookup"><span data-stu-id="3c033-233">Activity label: Review</span></span>
   - <span data-ttu-id="3c033-234">Megfelelő címke: Website.Reviews.UserId</span><span class="sxs-lookup"><span data-stu-id="3c033-234">Corresponding label: Website.Reviews.UserId</span></span>
   - <span data-ttu-id="3c033-235">Ügyfélentitás: eCommerceContacts:eCommerce</span><span class="sxs-lookup"><span data-stu-id="3c033-235">Customer entity: eCommerceContacts:eCommerce</span></span>
   - <span data-ttu-id="3c033-236">Kapcsolat: WebsiteReviews</span><span class="sxs-lookup"><span data-stu-id="3c033-236">Relationship: WebsiteReviews</span></span>

1. <span data-ttu-id="3c033-237">Válassza a **Következő** lehetőséget a modell ütemezésének beállításához.</span><span class="sxs-lookup"><span data-stu-id="3c033-237">Select **Next** to set the model schedule.</span></span>

   <span data-ttu-id="3c033-238">Ezt a modellt rendszeresen tanítani kell, hogy új mintákat tanuljon, amikor új adatokat töltenek be.</span><span class="sxs-lookup"><span data-stu-id="3c033-238">The model needs to train regularly to learn new patterns when there's new data ingested.</span></span> <span data-ttu-id="3c033-239">Ebben a példában válassza a **Havi** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="3c033-239">For this example, choose **Monthly**.</span></span>

1. <span data-ttu-id="3c033-240">A részletek áttekintése után válassza a **Mentés és Futtatás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="3c033-240">After reviewing all the details, select  **Save and Run**.</span></span>

## <a name="task-4---review-model-results-and-explanations"></a><span data-ttu-id="3c033-241">4. feladat – Modell eredmények és a magyarázatok áttekintése</span><span class="sxs-lookup"><span data-stu-id="3c033-241">Task 4 - Review model results and explanations</span></span>

<span data-ttu-id="3c033-242">Hagyja, hogy a modell teljesítse az adatok betanítását és pontozását.</span><span class="sxs-lookup"><span data-stu-id="3c033-242">Let the model complete the training and scoring of the data.</span></span> <span data-ttu-id="3c033-243">Ezután áttekintheti a CLV modell eredményeit és a magyarázatokat.</span><span class="sxs-lookup"><span data-stu-id="3c033-243">Next, you can review the CLV model results and explanations.</span></span> <span data-ttu-id="3c033-244">További tudnivalókért olvassa el az [Előrejelzés állapotának és eredmények áttekintése](predict-customer-lifetime-value.md#review-prediction-status-and-results) című témakört.</span><span class="sxs-lookup"><span data-stu-id="3c033-244">For more information, see [Review a prediction status and results](predict-customer-lifetime-value.md#review-prediction-status-and-results).</span></span>

## <a name="task-5---create-a-segment-of-high-value-customers"></a><span data-ttu-id="3c033-245">5. feladat - Nagy értékű ügyfelek szegmensének létrehozása</span><span class="sxs-lookup"><span data-stu-id="3c033-245">Task 5 - Create a segment of high value customers</span></span>

<span data-ttu-id="3c033-246">A modell futtatása új entitást hoz létre, amely listázva van az **Adatok** > **Entitások** helyen.</span><span class="sxs-lookup"><span data-stu-id="3c033-246">Running the model creates a new entity, which is listed on **Data** > **Entities**.</span></span> <span data-ttu-id="3c033-247">Új ügyfélszegmenst hozhat létre a modell által létrehozott entitás alapján.</span><span class="sxs-lookup"><span data-stu-id="3c033-247">You can create a new customer segment based on the entity created by the model.</span></span>

1. <span data-ttu-id="3c033-248">Kattintson a **Szegmensek** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="3c033-248">Go to **Segments**.</span></span> 

1. <span data-ttu-id="3c033-249">Válassza az **Új** lehetőséget, és válassza a **Létrehozás a következőkből** > **Információk** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="3c033-249">Select  **New** and choose **Create from** > **Intelligence**.</span></span>

   ![Szegmens létrehozása a modell kimenetével.](media/segment-intelligence.png)

1. <span data-ttu-id="3c033-251">Válassza ki az **OOBeCommerceCLVPrediction** entitást, és definiálja a szegmenst:</span><span class="sxs-lookup"><span data-stu-id="3c033-251">Select the  **OOBeCommerceCLVPrediction** entity and define the segment:</span></span>
  - <span data-ttu-id="3c033-252">Mező: CLVScore</span><span class="sxs-lookup"><span data-stu-id="3c033-252">Field: CLVScore</span></span>
  - <span data-ttu-id="3c033-253">Operátor: nagyobb, mint</span><span class="sxs-lookup"><span data-stu-id="3c033-253">Operator: greater than</span></span>
  - <span data-ttu-id="3c033-254">Érték: 1500</span><span class="sxs-lookup"><span data-stu-id="3c033-254">Value: 1500</span></span>

1. <span data-ttu-id="3c033-255">Válassza a **Vélemény** lehetőséget, és **Mentse** a szegmenst.</span><span class="sxs-lookup"><span data-stu-id="3c033-255">Select **Review** and **Save** the segment.</span></span>

<span data-ttu-id="3c033-256">Most már van egy szegmens, amely azonosítja azokat az ügyfeleket, akik az előrejelzések szerint több mint 1500 dollár bevételt generálnak a következő 12 hónapban.</span><span class="sxs-lookup"><span data-stu-id="3c033-256">You now have a segment that identifies customers who are predicted to generate more than $1500 of revenue in the next 12 months.</span></span> <span data-ttu-id="3c033-257">Ez a szegmens dinamikusan frissül, ha több adatot vesz fel.</span><span class="sxs-lookup"><span data-stu-id="3c033-257">This segment gets updated dynamically if more data is ingested.</span></span>

<span data-ttu-id="3c033-258">További információ: [Szegmensek létrehozása és kezelése](segments.md).</span><span class="sxs-lookup"><span data-stu-id="3c033-258">For more information, see [Create and manage segments](segments.md).</span></span>
