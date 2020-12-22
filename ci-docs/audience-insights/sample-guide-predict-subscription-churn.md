---
title: Az Előfizetés-lemorzsolódási előrejelzési példamutató
description: Használja ezt a példamutatót, hogy kipróbálhassa a mezőn kívüli előfizetés lemorzsolódási modellt.
ms.date: 11/19/2020
ms.reviewer: digranad
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: 2537cfb5dde0d1ce1af16f585f0bf91d15ea1870
ms.sourcegitcommit: a6e7df90d61450e00886753eb5db116f2f35bb6c
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/01/2020
ms.locfileid: "4653983"
---
# <a name="subscription-churn-prediction-preview-sample-guide"></a><span data-ttu-id="92ae0-103">Előfizetés-lemorzsolódási előrejelzési (előnézet) példamutató</span><span class="sxs-lookup"><span data-stu-id="92ae0-103">Subscription churn prediction (preview) sample guide</span></span>

<span data-ttu-id="92ae0-104">Elejétől végéig bemutatunk Önnek egy példán keresztül a egy előfizetés lemorzsolódási előrejelzést, használva az alább megadott példaadatokat.</span><span class="sxs-lookup"><span data-stu-id="92ae0-104">We'll walk you through an end to end example of subscription churn prediction using the sample data provided below.</span></span> 

## <a name="scenario"></a><span data-ttu-id="92ae0-105">Forgatókönyv</span><span class="sxs-lookup"><span data-stu-id="92ae0-105">Scenario</span></span>

<span data-ttu-id="92ae0-106">A Contoso egy vállalat, amely kiváló minőségű kávét és kávégépet árusít, melyet a Contoso Coffee weboldalán keresztül adnak el.</span><span class="sxs-lookup"><span data-stu-id="92ae0-106">Contoso is a company that produces high-quality coffee and coffee machines, which they sell through their Contoso Coffee website.</span></span> <span data-ttu-id="92ae0-107">A közelmúltban indítottak el egy előfizetéses üzletet ügyfeleiknek, hogy azok rendszeresen megkaphassák kávéjukat.</span><span class="sxs-lookup"><span data-stu-id="92ae0-107">They recently started a subscription business for their customers to get coffee on a regular basis.</span></span> <span data-ttu-id="92ae0-108">Céljuk, hogy megérthessék, melyik előfizetett ügyfelük fogja visszavonni előfizetését az elkövetkező pár hónapban.</span><span class="sxs-lookup"><span data-stu-id="92ae0-108">Their goal is to understand, which subscribed customers might cancel their subscription in the next few months.</span></span> <span data-ttu-id="92ae0-109">Tudva, melyek azok az ügyfelek, akik **várhatóan a lemorzsolódnak**, segítséget nyújthatnak a marketing-erőfeszítések megtakarításában, azzal, hogy megtartják őket.</span><span class="sxs-lookup"><span data-stu-id="92ae0-109">Knowing which of their customers is **likely to churn**, can help them save marketing efforts by focusing on keeping them.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="92ae0-110">Előfeltételek</span><span class="sxs-lookup"><span data-stu-id="92ae0-110">Prerequisites</span></span>

- <span data-ttu-id="92ae0-111">Legalább [közreműködői engedély](permissions.md) a Customer Insightsban.</span><span class="sxs-lookup"><span data-stu-id="92ae0-111">At least [Contributor permissions](permissions.md) in Customer Insights.</span></span>
- <span data-ttu-id="92ae0-112">Javasoljuk, hogy a következő lépéseket hajtsa végre [egy új környezetben](manage-environments.md).</span><span class="sxs-lookup"><span data-stu-id="92ae0-112">We recommend that you implement the following steps [in a new environment](manage-environments.md).</span></span>

## <a name="task-1---ingest-data"></a><span data-ttu-id="92ae0-113">1. Feladat - Adatok betáplálása</span><span class="sxs-lookup"><span data-stu-id="92ae0-113">Task 1 - Ingest Data</span></span>

<span data-ttu-id="92ae0-114">Olvassa el a cikkeket [az adatok betáplálásáról](data-sources.md) és [az adatforrások importálásáról a Power Query csatlakozók használatával](connect-power-query.md).</span><span class="sxs-lookup"><span data-stu-id="92ae0-114">Review the articles [about data ingestion](data-sources.md) and [importing data sources using Power Query connectors](connect-power-query.md) specifically.</span></span> <span data-ttu-id="92ae0-115">A következő információk azt feltételezik, hogy megismerkedett a betáplált adatokkal általánosságban.</span><span class="sxs-lookup"><span data-stu-id="92ae0-115">The following information assumes you familiarized with ingesting data in general.</span></span> 

### <a name="ingest-customer-data-from-ecommerce-platform"></a><span data-ttu-id="92ae0-116">Betáplált ügyféladatok az eCommerce platformról.</span><span class="sxs-lookup"><span data-stu-id="92ae0-116">Ingest customer data from eCommerce platform</span></span>

1. <span data-ttu-id="92ae0-117">Hozzon létre egy adatforrást, elnevezve **eCommerce**-nek, majd válassza az importálás lehetőséget, és jelölje ki a **Text/CSV** csatlakozót.</span><span class="sxs-lookup"><span data-stu-id="92ae0-117">Create a data source named **eCommerce**, choose the import option, and select the **Text/CSV** connector.</span></span>

1. <span data-ttu-id="92ae0-118">Adja meg az URL-címét az eCommerce kapcsolattartóknak https://aka.ms/ciadclasscontacts.</span><span class="sxs-lookup"><span data-stu-id="92ae0-118">Enter the URL for eCommerce contacts https://aka.ms/ciadclasscontacts.</span></span>

1. <span data-ttu-id="92ae0-119">Az adatok szerkesztése közben válassza az **Átalakítás** lehetőséget, majd a **Használja az első sort fejlécként** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="92ae0-119">While editing the data, select **Transform** and then **Use First Row as Headers**.</span></span>

1. <span data-ttu-id="92ae0-120">Frissítse az adattípust az alább felsorolt oszlopokhoz:</span><span class="sxs-lookup"><span data-stu-id="92ae0-120">Update the datatype for the columns listed below:</span></span>

   - <span data-ttu-id="92ae0-121">**SzületésiDátum**: Dátum</span><span class="sxs-lookup"><span data-stu-id="92ae0-121">**DateOfBirth**: Date</span></span>
   - <span data-ttu-id="92ae0-122">**CreatedOn**: Dátum/Idő/Zóna</span><span class="sxs-lookup"><span data-stu-id="92ae0-122">**CreatedOn**: Date/Time/Zone</span></span>

   [!div class="mx-imgBorder"]
   <span data-ttu-id="92ae0-123">![DoB átalakítása Dátummá](media/ecommerce-dob-date.PNG "A születési dátum átalakítása dátummá")</span><span class="sxs-lookup"><span data-stu-id="92ae0-123">![Transform DoB to Date](media/ecommerce-dob-date.PNG "transform date of birth to date")</span></span>

1. <span data-ttu-id="92ae0-124">A jobb oldali panelben a "Név" mezőben nevezze át az adatforrását a **Lekérdezés**-ről **eCommerceContacts**-ra.</span><span class="sxs-lookup"><span data-stu-id="92ae0-124">In the 'Name' field on the right-hand pane, rename your data source from **Query** to **eCommerceContacts**</span></span>

1. <span data-ttu-id="92ae0-125">Az adatforrások mentése.</span><span class="sxs-lookup"><span data-stu-id="92ae0-125">Save the data source.</span></span>

### <a name="ingest-customer-data-from-loyalty-schema"></a><span data-ttu-id="92ae0-126">Ügyféladatok bevitele a hűségsémából</span><span class="sxs-lookup"><span data-stu-id="92ae0-126">Ingest customer data from loyalty schema</span></span>

1. <span data-ttu-id="92ae0-127">Hozzon létre egy adatforrást, melynek neve **LoyaltyScheme**, majd válassza az importálás lehetőséget, és jelölje ki a **Text/CSV** csatlakozót.</span><span class="sxs-lookup"><span data-stu-id="92ae0-127">Create a data source named **LoyaltyScheme**, choose the import option, and select the **Text/CSV** connector.</span></span>

1. <span data-ttu-id="92ae0-128">Adja meg az URL-címét az eCommerce kapcsolattartóknak https://aka.ms/ciadclasscustomerloyalty.</span><span class="sxs-lookup"><span data-stu-id="92ae0-128">Enter the URL for eCommerce contacts https://aka.ms/ciadclasscustomerloyalty.</span></span>

1. <span data-ttu-id="92ae0-129">Az adatok szerkesztése közben válassza az **Átalakítás** lehetőséget, majd a **Használja az első sort fejlécként** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="92ae0-129">While editing the data, select **Transform** and then **Use First Row as Headers**.</span></span>

1. <span data-ttu-id="92ae0-130">Frissítse az adattípust az alább felsorolt oszlopokhoz:</span><span class="sxs-lookup"><span data-stu-id="92ae0-130">Update the datatype for the columns listed below:</span></span>

   - <span data-ttu-id="92ae0-131">**SzületésiDátum**: Dátum</span><span class="sxs-lookup"><span data-stu-id="92ae0-131">**DateOfBirth**: Date</span></span>
   - <span data-ttu-id="92ae0-132">**JutalmazásiPontok**: Egész Szám</span><span class="sxs-lookup"><span data-stu-id="92ae0-132">**RewardsPoints**: Whole Number</span></span>
   - <span data-ttu-id="92ae0-133">**KészültEkkor**: Dátum/Idő</span><span class="sxs-lookup"><span data-stu-id="92ae0-133">**CreatedOn**: Date/Time</span></span>

1. <span data-ttu-id="92ae0-134">A "Név" mezőben, a jobb oldali panelen, nevezze át az adatforrását **Lekérdezés**-ről **loyCustomers**-re.</span><span class="sxs-lookup"><span data-stu-id="92ae0-134">In the 'Name' field on the right-hand pane, rename your data source from **Query** to **loyCustomers**.</span></span>

1. <span data-ttu-id="92ae0-135">Az adatforrások mentése.</span><span class="sxs-lookup"><span data-stu-id="92ae0-135">Save the data source.</span></span>

### <a name="ingest-subscription-information"></a><span data-ttu-id="92ae0-136">Előfizetési információk betáplálása</span><span class="sxs-lookup"><span data-stu-id="92ae0-136">Ingest subscription information</span></span>

1. <span data-ttu-id="92ae0-137">Hozzon létre egy adatforrást, melynek neve **ElőfizetésiElőzmények**, majd válassza az importálás lehetőséget, és jelölje ki a **Text/CSV** csatlakozót.</span><span class="sxs-lookup"><span data-stu-id="92ae0-137">Create a data source named **SubscriptionHistory**, choose the import option, and select the **Text/CSV** connector.</span></span>

1. <span data-ttu-id="92ae0-138">Adja meg az URL-címét az eCommerce kapcsolattartóknak https://aka.ms/ciadchurnsubscriptionhistory.</span><span class="sxs-lookup"><span data-stu-id="92ae0-138">Enter the URL for eCommerce contacts https://aka.ms/ciadchurnsubscriptionhistory.</span></span>

1. <span data-ttu-id="92ae0-139">Az adatok szerkesztése közben válassza az **Átalakítás** lehetőséget, majd a **Használja az első sort fejlécként** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="92ae0-139">While editing the data, select **Transform** and then **Use First Row as Headers**.</span></span>

1. <span data-ttu-id="92ae0-140">Frissítse az adattípust az alább felsorolt oszlopokhoz:</span><span class="sxs-lookup"><span data-stu-id="92ae0-140">Update the datatype for the columns listed below:</span></span>

   - <span data-ttu-id="92ae0-141">**ElőfizetésAzonosító**: Egész szám</span><span class="sxs-lookup"><span data-stu-id="92ae0-141">**SubscriptioID**: Whole Number</span></span>
   - <span data-ttu-id="92ae0-142">**ElőfizetésiÖsszeg**: Pénznem</span><span class="sxs-lookup"><span data-stu-id="92ae0-142">**SubscriptionAmount**: Currency</span></span>
   - <span data-ttu-id="92ae0-143">**ElőfizetésVégénekDátuma**: Dátum/Idő</span><span class="sxs-lookup"><span data-stu-id="92ae0-143">**SubscriptionEndDate**: Date/Time</span></span>
   - <span data-ttu-id="92ae0-144">**ElőfizetésKezdeténekDátuma**: Dátum/Idő</span><span class="sxs-lookup"><span data-stu-id="92ae0-144">**SubscriptionStartDate**: Date/Time</span></span>
   - <span data-ttu-id="92ae0-145">**TranzakcióDátuma**: Dátum/Idő</span><span class="sxs-lookup"><span data-stu-id="92ae0-145">**TransactionDate**: Date/Time</span></span>
   - <span data-ttu-id="92ae0-146">**IsIsmétlődés**: Igaz/Hamis</span><span class="sxs-lookup"><span data-stu-id="92ae0-146">**IsRecurring**: True/False</span></span>
   - <span data-ttu-id="92ae0-147">**Is_auto_megújítás**: Igaz/Hamis</span><span class="sxs-lookup"><span data-stu-id="92ae0-147">**Is_auto_renew**: True/False</span></span>
   - <span data-ttu-id="92ae0-148">**IsmétlődésiGyakoriságInHónapok**: Egész Szám</span><span class="sxs-lookup"><span data-stu-id="92ae0-148">**RecurringFrequencyInMonths**: Whole Number</span></span>

1. <span data-ttu-id="92ae0-149">A 'Név' mezőben a jobb oldali panelen, nevezze át az adatforrását **Lekérdezés**-ről **SubscriptionHistory**-ra.</span><span class="sxs-lookup"><span data-stu-id="92ae0-149">In the 'Name' field on the right-hand pane, rename your data source from **Query** to **SubscriptionHistory**.</span></span>

1. <span data-ttu-id="92ae0-150">Az adatforrások mentése.</span><span class="sxs-lookup"><span data-stu-id="92ae0-150">Save the data source.</span></span>

### <a name="ingest-customer-data-from-website-reviews"></a><span data-ttu-id="92ae0-151">Tápláljon be ügyféladatokat a webhely értékelésekből.</span><span class="sxs-lookup"><span data-stu-id="92ae0-151">Ingest customer data from website reviews</span></span>

1. <span data-ttu-id="92ae0-152">Hozzon létre egy adatforrást, **eCommerce** néven, majd válassza az importálás lehetőséget, és jelölje ki a **Text/CSV** csatlakozót.</span><span class="sxs-lookup"><span data-stu-id="92ae0-152">Create a data source named **Website**, choose the import option, and select the **Text/CSV** connector.</span></span>

1. <span data-ttu-id="92ae0-153">Adja meg az URL-címét az eCommerce kapcsolattartóknak https://aka.ms/ciadclasswebsite.</span><span class="sxs-lookup"><span data-stu-id="92ae0-153">Enter the URL for eCommerce contacts https://aka.ms/ciadclasswebsite.</span></span>

1. <span data-ttu-id="92ae0-154">Az adatok szerkesztése közben válassza az **Átalakítás** lehetőséget, majd a **Használja az első sort fejlécként** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="92ae0-154">While editing the data, select **Transform** and then **Use First Row as Headers**.</span></span>

1. <span data-ttu-id="92ae0-155">Frissítse az adattípust az alább felsorolt oszlopokhoz:</span><span class="sxs-lookup"><span data-stu-id="92ae0-155">Update the datatype for the columns listed below:</span></span>

   - <span data-ttu-id="92ae0-156">**ÁttekintésiMinősítés**: Egész Szám</span><span class="sxs-lookup"><span data-stu-id="92ae0-156">**ReviewRating**: Whole Number</span></span>
   - <span data-ttu-id="92ae0-157">**ÁttekintésDátuma**: Dátum</span><span class="sxs-lookup"><span data-stu-id="92ae0-157">**ReviewDate**: Date</span></span>

1. <span data-ttu-id="92ae0-158">A "Név" mezőben, a jobb oldali panelen, nevezze át az adatforrását **Lekérdezés**-ről **webReviews**-re.</span><span class="sxs-lookup"><span data-stu-id="92ae0-158">In the 'Name' field on the right-hand pane, rename your data source from **Query** to **webReviews**.</span></span>

## <a name="task-2---data-unification"></a><span data-ttu-id="92ae0-159">2. feladat - Adatok egységesítése</span><span class="sxs-lookup"><span data-stu-id="92ae0-159">Task 2 - Data unification</span></span>

<span data-ttu-id="92ae0-160">Az adatok bevitele után elkezdhetjük a **Megfeleltetés/Egyeztetés/Egyesítés** folyamatot, hogy hogy létrehozzunk egy egyesített ügyfélprofilt.</span><span class="sxs-lookup"><span data-stu-id="92ae0-160">After ingesting the data we now begin the **Map, Match, Merge** process to create a unified customer profile.</span></span> <span data-ttu-id="92ae0-161">További információkért lásd: [Adatok egységesítése](data-unification.md).</span><span class="sxs-lookup"><span data-stu-id="92ae0-161">For more information, see [Data unification](data-unification.md).</span></span>

### <a name="map"></a><span data-ttu-id="92ae0-162">Map</span><span class="sxs-lookup"><span data-stu-id="92ae0-162">Map</span></span>

1. <span data-ttu-id="92ae0-163">Az adatok betáplálása után képezze le a kapcsolattartókat az eCommerce-ből és a Loyalty data-ból a közös adattípusokba.</span><span class="sxs-lookup"><span data-stu-id="92ae0-163">After ingesting the data, map contacts from eCommerce and Loyalty data to common data types.</span></span> <span data-ttu-id="92ae0-164">Nyissa meg az **Adatok** > **Egységesítés** > **Megfeleltetés**-t.</span><span class="sxs-lookup"><span data-stu-id="92ae0-164">Go to **Data** > **Unify** > **Map**.</span></span>

1. <span data-ttu-id="92ae0-165">Válassza ki az entitást, amely jelképezi az ügyfélprofilt – **eCommerceContacts** és **loyCustomers**.</span><span class="sxs-lookup"><span data-stu-id="92ae0-165">Select the entities that represent the customer profile – **eCommerceContacts** and **loyCustomers**.</span></span> 

   :::image type="content" source="media/unify-ecommerce-loyalty.PNG" alt-text="az ecommerce és a loyality adatforrások egységesítése.":::

1. <span data-ttu-id="92ae0-167">Jelölje ki a **ContactId**-t elsődleges kulcsaként az **eCommerceContacts**-hoz és a **LoyaltyID** a **loyCustomers** elsődleges kulcsaként.</span><span class="sxs-lookup"><span data-stu-id="92ae0-167">Select **ContactId** as the primary key for **eCommerceContacts** and **LoyaltyID** as the primary key for **loyCustomers**.</span></span>

   :::image type="content" source="media/unify-loyaltyid.PNG" alt-text="A LoyaltyId egyesítheti elsődleges kulcsként.":::

### <a name="match"></a><span data-ttu-id="92ae0-169">Egyeztetés</span><span class="sxs-lookup"><span data-stu-id="92ae0-169">Match</span></span>

1. <span data-ttu-id="92ae0-170">Ugorjon az **Egyeztetés** lapra és válassza a **Sorrend beállítását**.</span><span class="sxs-lookup"><span data-stu-id="92ae0-170">Go to the **Match** tab and select **Set Order**.</span></span>

1. <span data-ttu-id="92ae0-171">Az **Elsődleges** legördülő listában válassza az **eCommerceContacts : eCommerce** lehetőséget elsődleges forrásként, amely minden rekordot magában foglal.</span><span class="sxs-lookup"><span data-stu-id="92ae0-171">In the **Primary** drop-down list, choose **eCommerceContacts : eCommerce** as the primary source and include all records.</span></span>

1. <span data-ttu-id="92ae0-172">Az **Entitás 2** legördülő listájában válassza ki a **loyCustomers: LoyaltyScheme** lehetőséget, és adja meg az összes rekordot.</span><span class="sxs-lookup"><span data-stu-id="92ae0-172">In the **Entity 2** drop-down list, choose **loyCustomers : LoyaltyScheme** and include all records.</span></span>

   :::image type="content" source="media/unify-match-order.PNG" alt-text="Az egységesítéshez egyeztesse az eCommerce-t és a Loyality-t.":::

1. <span data-ttu-id="92ae0-174">Válassza az **Új szabály létrehozása** menüpontot</span><span class="sxs-lookup"><span data-stu-id="92ae0-174">Select **Create a new rule**</span></span>

1. <span data-ttu-id="92ae0-175">Adja hozzá az első feltételt a FullName segítségével.</span><span class="sxs-lookup"><span data-stu-id="92ae0-175">Add your first condition using FullName.</span></span>

   * <span data-ttu-id="92ae0-176">Az eCommerceContacts lehetőséghez válassza ki a **FullName** opciót a legördülő listából.</span><span class="sxs-lookup"><span data-stu-id="92ae0-176">For eCommerceContacts select **FullName** in the drop-down.</span></span>
   * <span data-ttu-id="92ae0-177">A loyCustumers lehetőséghez válassza ki a **FullName** opciót a legördülő listából.</span><span class="sxs-lookup"><span data-stu-id="92ae0-177">For loyCustomers select **FullName** in the drop-down.</span></span>
   * <span data-ttu-id="92ae0-178">Jelölje ki a **Normalizálás** legördülő parancsot, és válassza a **Típus (Telefon, Név, Cím,...)** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="92ae0-178">Select the **Normalize** drop down and choose **Type (Phone, Name, Address, ...)**.</span></span>
   * <span data-ttu-id="92ae0-179">Állítsa be a **Pontossági szintet**: **Alap** és **Érték**: **Magas**-ra.</span><span class="sxs-lookup"><span data-stu-id="92ae0-179">Set **Precision Level**: **Basic** and **Value**: **High**.</span></span>

1. <span data-ttu-id="92ae0-180">Adja meg a nevét **FullName, Email**, az új szabályhoz.</span><span class="sxs-lookup"><span data-stu-id="92ae0-180">Enter the name **FullName, Email** for the new rule.</span></span>

   * <span data-ttu-id="92ae0-181">Másik feltétel hozzáadása az e-mail címhez a **Feltétel hozzáadása** lehetőség választásával.</span><span class="sxs-lookup"><span data-stu-id="92ae0-181">Add a second condition for email address by selecting **Add Condition**</span></span>
   * <span data-ttu-id="92ae0-182">Az eCommerceContacts entitáshoz válassza az **Email** legördülő lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="92ae0-182">For entity eCommerceContacts, choose **EMail** in drop-down.</span></span>
   * <span data-ttu-id="92ae0-183">Az loyCustomers entitáshoz válassza az **Email** legördülő lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="92ae0-183">For entity loyCustomers, choose **EMail** in the drop-down.</span></span> 
   * <span data-ttu-id="92ae0-184">Hagyja üresen a Normalizálást.</span><span class="sxs-lookup"><span data-stu-id="92ae0-184">Leave Normalize blank.</span></span> 
   * <span data-ttu-id="92ae0-185">Állítsa be a **Pontossági szintet**: **Alap** és **Érték**: **Magas**-ra.</span><span class="sxs-lookup"><span data-stu-id="92ae0-185">Set **Precision Level**: **Basic** and **Value**: **High**.</span></span>

   :::image type="content" source="media/unify-match-rule.PNG" alt-text="Egységesítése az egyezési szabályt a névhez és az e-mailhez.":::

7. <span data-ttu-id="92ae0-187">Válassza a **Mentés** és **Futtatás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="92ae0-187">Select **Save** and **Run**.</span></span>

### <a name="merge"></a><span data-ttu-id="92ae0-188">Összefűzés</span><span class="sxs-lookup"><span data-stu-id="92ae0-188">Merge</span></span>

1. <span data-ttu-id="92ae0-189">Nyissa meg az **Egyesítés** lapot.</span><span class="sxs-lookup"><span data-stu-id="92ae0-189">Go to the **Merge** tab.</span></span>

1. <span data-ttu-id="92ae0-190">A **ContactId** **loyCustomers** entitáshoz változtassa meg a megjelenítendő nevet **ContactIdLOYALTY**-ra, hogy megkülönböztethesse azt a többi betáplált azonosítóval.</span><span class="sxs-lookup"><span data-stu-id="92ae0-190">On the **ContactId** for **loyCustomers** entity, change the display name to **ContactIdLOYALTY** to differentiate it from the other IDs ingested.</span></span>

   :::image type="content" source="media/unify-merge-contactid.PNG" alt-text="nevezze át a loyalty azonosítót contactid-re.":::

1. <span data-ttu-id="92ae0-192">Válassza a **Mentés** és **Futtatás** lehetőséget, hogy elindítsa a Egyesítés Folyamatot.</span><span class="sxs-lookup"><span data-stu-id="92ae0-192">Select **Save** and **Run** to start the Merge Process.</span></span>


## <a name="task-3---configure-the-subscription-churn-prediction"></a><span data-ttu-id="92ae0-193">3. feladat – Konfigurálja az előfizetés lemorzsolódási előrejelzést</span><span class="sxs-lookup"><span data-stu-id="92ae0-193">Task 3 - Configure the subscription churn prediction</span></span>

<span data-ttu-id="92ae0-194">Az egységesített ügyfélprofilok elkészítése után, előfizetés lemorzsolódási előrejelzést futtathatunk.</span><span class="sxs-lookup"><span data-stu-id="92ae0-194">With the unified customer profiles in place, we can now run the subscription churn prediction.</span></span> <span data-ttu-id="92ae0-195">A részletes lépésekért lásd az [Előfizetés lemorzsolódási előrejelzés (előnézet)](predict-subscription-churn.md) című cikket.</span><span class="sxs-lookup"><span data-stu-id="92ae0-195">For detailed steps, see the [Subscription churn prediction (preview)](predict-subscription-churn.md) article.</span></span> 

1. <span data-ttu-id="92ae0-196">Nyissa meg az **Intelligencia** > **Felfedezés** elemet, és válassza az **Ügyfél-lemorzsolódási modell** használatát.</span><span class="sxs-lookup"><span data-stu-id="92ae0-196">Go to **Intelligence** > **Discover** and select to use the **Customer churn model**.</span></span>

1. <span data-ttu-id="92ae0-197">Válassza az **Előfizetés** beállítást, majd válassza ki a **Kezdő lépések** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="92ae0-197">Select the **Subscription** option and select **Get started**.</span></span>

1. <span data-ttu-id="92ae0-198">Nevezze el a modellt **OOB Előfizetés-lemorzsolódási Előrejelzés**-nek és a kimeneti entitást **OOBElőfizetés-lemorzsolódásiElőrejelzés**-nek.</span><span class="sxs-lookup"><span data-stu-id="92ae0-198">Name the model **OOB Subscription Churn Prediction** and the output entity **OOBSubscriptionChurnPrediction**.</span></span>

1. <span data-ttu-id="92ae0-199">Határozzon meg két feltételt a lemorzsolódási modellhez.</span><span class="sxs-lookup"><span data-stu-id="92ae0-199">Define two conditions for the churn model:</span></span>

   * <span data-ttu-id="92ae0-200">**Amióta az előfizetés véget ért**: **legalább 60** nap.</span><span class="sxs-lookup"><span data-stu-id="92ae0-200">**Days since subscription ended**: **at least 60** days.</span></span> <span data-ttu-id="92ae0-201">Ha egy ügyfél nem újítja meg előfizetését ebben az időszakban, miután előző előfizetése lejárt, lemorzsolódónak tekintendő.</span><span class="sxs-lookup"><span data-stu-id="92ae0-201">If a customer doesn't renew the subscription in this period after their subscription ended, they are considered churned.</span></span> 

   * <span data-ttu-id="92ae0-202">**Lemorzsolódás meghatározása**: **legalább 93** nap.</span><span class="sxs-lookup"><span data-stu-id="92ae0-202">**Churn definition**: **at least 93** days.</span></span> <span data-ttu-id="92ae0-203">Az az időtartam, ami alatt a modell megjósolja, hogy mely ügyfelek morzsolódhatnak le.</span><span class="sxs-lookup"><span data-stu-id="92ae0-203">The duration the model predict which customers might churn.</span></span> <span data-ttu-id="92ae0-204">Minél távolabb tekint a jövőben, annál kevésbé pontosak az eredmények.</span><span class="sxs-lookup"><span data-stu-id="92ae0-204">The further in the future you look, the less precise the results.</span></span>

     :::image type="content" source="media/model-subs-levers.PNG" alt-text="Válassza ki a modellt, amely előhozza az Előrejelzési Ablakot és a Lemorzsolódás Meghatározását.":::

1. <span data-ttu-id="92ae0-206">Válassza ki a **Szükséges adatok hozzáadása** menüt, és ott válassza az **Adatok hozzáadása** lehetőséget az előfizetési előzményekhez.</span><span class="sxs-lookup"><span data-stu-id="92ae0-206">Select **Add required data** and select **Add data** for subscription history.</span></span>

1. <span data-ttu-id="92ae0-207">Adja hozzá a **Előfizetés : ElőfizetésiElőzmények** entitást és képezze le a mezőket az eCommerce-ből a megfelelő mezőkre, melyek modell által megköveteltek.</span><span class="sxs-lookup"><span data-stu-id="92ae0-207">Add the **Subscription : SubscriptionHistory** entity and map the fields from eCommerce to the corresponding fields required by the model.</span></span>

1. <span data-ttu-id="92ae0-208">Csatlakoztassa az **Előfizetés : ElőfizetésiElőzmények** entitáshoz az **eCommerceContacts : eCommerce**-t, nevezze el a kapcsolatot **eCommerceElőfizetések**-nek.</span><span class="sxs-lookup"><span data-stu-id="92ae0-208">Join the **Subscription : SubscriptionHistory** entity with **eCommerceContacts : eCommerce**, name the relationship **eCommerceSubscription**.</span></span>

   :::image type="content" source="media/model-subscription-join.PNG" alt-text="Csatlakoztassa az eCommerce entitásokhoz.":::

1. <span data-ttu-id="92ae0-210">Az Ügyféltevékenység alatt adja hozzá a **webReviews : Website** entitást és képezze le a mezőket a webReviewsból a megfelelő mezőkre, melyek modell által megköveteltek.</span><span class="sxs-lookup"><span data-stu-id="92ae0-210">Under Customer Activities, add the **webReviews : Website** entity and map the fields from webReviews to the corresponding fields required by the model.</span></span> 
   - <span data-ttu-id="92ae0-211">Elsődleges kulcs: ÉrtékelésId</span><span class="sxs-lookup"><span data-stu-id="92ae0-211">Primary key: ReviewId</span></span>
   - <span data-ttu-id="92ae0-212">Időbélyege: ÉrtékelésDátuma</span><span class="sxs-lookup"><span data-stu-id="92ae0-212">Timestamp: ReviewDate</span></span>
   - <span data-ttu-id="92ae0-213">Esemény: ÉrtékelésMinősítése</span><span class="sxs-lookup"><span data-stu-id="92ae0-213">Event: ReviewRating</span></span>

1. <span data-ttu-id="92ae0-214">Konfiguráljon egy tevékenységet a webhely értékeléseknek.</span><span class="sxs-lookup"><span data-stu-id="92ae0-214">Configure an activity for website reviews.</span></span> <span data-ttu-id="92ae0-215">Válassza ki az **Értékelés** tevékenységet és csatlakoztassa a **webÉrtékelések : Weboldal** entitást az **eCommerceContacts : eCommerce**-hez.</span><span class="sxs-lookup"><span data-stu-id="92ae0-215">Select the activity **Review** and join the **webReviews : Website** entity with **eCommerceContacts : eCommerce**.</span></span>

1. <span data-ttu-id="92ae0-216">Válassza a **Következő** lehetőséget a modell ütemezésének beállításához.</span><span class="sxs-lookup"><span data-stu-id="92ae0-216">Select **Next** to set the model schedule.</span></span>

   <span data-ttu-id="92ae0-217">A modell rendszeres betanítást igényel ahhoz, hogy új mintákat tanulhasson, amikor új adatok kerülnek a rendszerbe.</span><span class="sxs-lookup"><span data-stu-id="92ae0-217">The model needs to train regularly to learn new patterns when there is new data ingested.</span></span> <span data-ttu-id="92ae0-218">Ennél a példánál válassza a **Havonta** beállítást.</span><span class="sxs-lookup"><span data-stu-id="92ae0-218">For this example, select **Monthly**.</span></span>

1. <span data-ttu-id="92ae0-219">A részletek áttekintése után válassza a **Mentés és Futtatás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="92ae0-219">After reviewing all the details, select **Save and Run**.</span></span>

## <a name="task-4---review-model-results-and-explanations"></a><span data-ttu-id="92ae0-220">4. feladat – Modell eredmények és a magyarázatok áttekintése</span><span class="sxs-lookup"><span data-stu-id="92ae0-220">Task 4 - Review model results and explanations</span></span>

<span data-ttu-id="92ae0-221">Hagyja, hogy a modell teljesítse az adatok betanítását és pontozását.</span><span class="sxs-lookup"><span data-stu-id="92ae0-221">Let the model complete the training and scoring of the data.</span></span> <span data-ttu-id="92ae0-222">Most már megtekintheti az előfizetési lemorzsolódás modell magyarázatait.</span><span class="sxs-lookup"><span data-stu-id="92ae0-222">You can now review the subscription churn model explanations.</span></span> <span data-ttu-id="92ae0-223">További tudnivalókért olvassa el az [Előrejelzés állapotának és eredmények áttekintése](predict-subscription-churn.md#review-a-prediction-status-and-results) című témakört.</span><span class="sxs-lookup"><span data-stu-id="92ae0-223">For more information, see [Review a prediction status and results](predict-subscription-churn.md#review-a-prediction-status-and-results).</span></span>

## <a name="task-5---create-a-segment-of-high-churn-risk-customers"></a><span data-ttu-id="92ae0-224">5. feladat – Hozzon létre egy szegmenst a nagy lemorzsolódási kockázatú ügyfelekről</span><span class="sxs-lookup"><span data-stu-id="92ae0-224">Task 5 - Create a segment of high churn-risk customers</span></span>

<span data-ttu-id="92ae0-225">Futtatva a termékjavaslati modellt, létrehozhat egy új entitást, amelyet láthat a **Adat** > **Entitások**-nál.</span><span class="sxs-lookup"><span data-stu-id="92ae0-225">Running the production model creates a new entity that you can see in **Data** > **Entities**.</span></span>   

<span data-ttu-id="92ae0-226">Létrehozhat egy új szegmenst, a modell által létrehozott entitás alapján.</span><span class="sxs-lookup"><span data-stu-id="92ae0-226">You can create a new segment based on the entity created by the model.</span></span>

1.  <span data-ttu-id="92ae0-227">Kattintson a **Szegmensek** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="92ae0-227">Go to **Segments**.</span></span> <span data-ttu-id="92ae0-228">Válassza az **Új** lehetőséget, és válassza a **Létrehozás a következőkből** > **Intelligencia**.</span><span class="sxs-lookup"><span data-stu-id="92ae0-228">Select **New** and choose **Create from** > **Intelligence**.</span></span> 

   :::image type="content" source="media/segment-intelligence.PNG" alt-text="Szegmens létrehozása a modell kimenetével.":::

1. <span data-ttu-id="92ae0-230">Válassza ki a **OOBSubscriptionChurnPrediction** végpontot és definiálja a szegmenst:</span><span class="sxs-lookup"><span data-stu-id="92ae0-230">Select the **OOBSubscriptionChurnPrediction** endpoint and define the segment:</span></span> 
   - <span data-ttu-id="92ae0-231">Mező: ChurnScore</span><span class="sxs-lookup"><span data-stu-id="92ae0-231">Field: ChurnScore</span></span>
   - <span data-ttu-id="92ae0-232">Operátor: nagyobb, mint</span><span class="sxs-lookup"><span data-stu-id="92ae0-232">Operator: greater than</span></span>
   - <span data-ttu-id="92ae0-233">Érték: 0,6</span><span class="sxs-lookup"><span data-stu-id="92ae0-233">Value: 0.6</span></span>
   
   :::image type="content" source="media/segment-setup-subs.PNG" alt-text="Állítsa be az előfizetési lemorzsolódási szegmenset.":::

<span data-ttu-id="92ae0-235">Most már van egy szegmense, amely dinamikusan frissítve van, és amely meghatározza a magas lemorzsolódási kockázatot ennek az üzleti előfizetésnek az esetén.</span><span class="sxs-lookup"><span data-stu-id="92ae0-235">You now have a segment that is dynamically updated which identifies high churn-risk customers for this subscription business.</span></span>

<span data-ttu-id="92ae0-236">További információ: [Szegmensek létrehozása és kezelése](segments.md).</span><span class="sxs-lookup"><span data-stu-id="92ae0-236">For more information, see [Create and manage segments](segments.md).</span></span>
