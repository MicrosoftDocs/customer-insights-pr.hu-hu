---
title: Független gyártótól származó bővítéssel történő Experian bővítés
description: A független gyártótól származó Experian bővítésre vonatkozó általános információk.
ms.date: 04/09/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: kishorem-ms
ms.author: kishorem
manager: shellyha
ms.openlocfilehash: 7c82fe92b3351a782a4fa6510300d870b742d042
ms.sourcegitcommit: 42b3bce1e20e7cc707d232844dacfeed3d6fc096
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/28/2021
ms.locfileid: "6309823"
---
# <a name="enrich-customer-profiles-with-demographics-from-experian-preview"></a><span data-ttu-id="0cfbf-103">Ügyfélprofilok bővítése demográfiai adatokkal az Experian -ból (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="0cfbf-103">Enrich customer profiles with demographics from Experian (preview)</span></span>

<span data-ttu-id="0cfbf-104">Az Experian a fogyasztói és üzleti hiteljelentési és marketingszolgáltatások globális vezetője.</span><span class="sxs-lookup"><span data-stu-id="0cfbf-104">Experian is a global leader in consumer and business credit reporting and marketing services.</span></span> <span data-ttu-id="0cfbf-105">Az Experian adatbővítési szolgáltatások segítségével mélyebben megértheti ügyfeleit, az ügyfélprofilok bővítése által demográfiai adatokkal, mint például a háztartás nagysága, bevétel, stb.</span><span class="sxs-lookup"><span data-stu-id="0cfbf-105">With Experian’s data enrichment services, you can build a deeper understanding of your customers by enriching your customer profiles with demographic data such as household size, income, and more.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0cfbf-106">Előfeltételek</span><span class="sxs-lookup"><span data-stu-id="0cfbf-106">Prerequisites</span></span>

<span data-ttu-id="0cfbf-107">Az Experian konfigurálásához teljesülnie kell az alábbi előfeltételeknek:</span><span class="sxs-lookup"><span data-stu-id="0cfbf-107">To configure Experian, the following prerequisites must be met:</span></span>

- <span data-ttu-id="0cfbf-108">Aktív Experian előfizetéssel kell rendelkeznie.</span><span class="sxs-lookup"><span data-stu-id="0cfbf-108">You have an active Experian subscription.</span></span> <span data-ttu-id="0cfbf-109">Az előfizetéshez közvetlenül [forduljon Experian](https://www.experian.com/marketing-services/contact) .</span><span class="sxs-lookup"><span data-stu-id="0cfbf-109">To get a subscription, [contact Experian](https://www.experian.com/marketing-services/contact) directly.</span></span> <span data-ttu-id="0cfbf-110">[További információk Experian adatbővítésről](https://www.experian.com/marketing-services/microsoft?cmpid=ems_web_mci_cdppage).</span><span class="sxs-lookup"><span data-stu-id="0cfbf-110">[Learn more about Experian Data Enrichment](https://www.experian.com/marketing-services/microsoft?cmpid=ems_web_mci_cdppage).</span></span>

- <span data-ttu-id="0cfbf-111">Az Experian kapcsolatot már konfigurálta egy rendszergazda *vagy* Ön rendelkezik [rendszergazda](permissions.md#administrator) engedélyekkel.</span><span class="sxs-lookup"><span data-stu-id="0cfbf-111">An Experian connection has already been configured by an administrator *or* you have [administrator](permissions.md#administrator) permissions.</span></span> <span data-ttu-id="0cfbf-112">Szüksége van a felhasználói azonosítóra, partnerazonosítóra, és modellszámra is az SSH-kompatibilis Secure Transport (ST) fiókjához, amelyet az Experian hozott létre az Ön számára.</span><span class="sxs-lookup"><span data-stu-id="0cfbf-112">You also need the User ID, Party ID, and Model Number for your SSH-enabled Secure Transport (ST) account that Experian created for you.</span></span>

## <a name="supported-countriesregions"></a><span data-ttu-id="0cfbf-113">Támogatott országok/régiók</span><span class="sxs-lookup"><span data-stu-id="0cfbf-113">Supported countries/regions</span></span>

<span data-ttu-id="0cfbf-114">Jelenleg csak az Egyesült Államokban támogatjuk az ügyfélprofilok bővítését.</span><span class="sxs-lookup"><span data-stu-id="0cfbf-114">We currently support enriching customer profiles in the United States only.</span></span>

## <a name="configure-the-enrichment"></a><span data-ttu-id="0cfbf-115">Bővítés konfigurálása</span><span class="sxs-lookup"><span data-stu-id="0cfbf-115">Configure the enrichment</span></span>

1. <span data-ttu-id="0cfbf-116">Menjen a z **Adatok** > **Bővítés** menübe, és válassza a **Felfedezés** lapot.</span><span class="sxs-lookup"><span data-stu-id="0cfbf-116">Go to **Data** > **Enrichment** and select the **Discover** tab.</span></span>

1. <span data-ttu-id="0cfbf-117">Válassza ki az **Adatom bővítése** az Experian csempén.</span><span class="sxs-lookup"><span data-stu-id="0cfbf-117">Select **Enrich my data** on the Experian tile.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="0cfbf-118">![Experian mozaikot](media/experian-tile.png "Experian tile")</span><span class="sxs-lookup"><span data-stu-id="0cfbf-118">![Experian tile](media/experian-tile.png "Experian tile")</span></span>
   > 

1. <span data-ttu-id="0cfbf-119">Válasszon egy [kapcsolatot](connections.md) a legördülő listából.</span><span class="sxs-lookup"><span data-stu-id="0cfbf-119">Select a [connection](connections.md) from the dropdown list.</span></span> <span data-ttu-id="0cfbf-120">Ha nem érhető el egy kapcsolat sem, akkor forduljon a rendszergazdához.</span><span class="sxs-lookup"><span data-stu-id="0cfbf-120">Contact an administrator if no connection is available.</span></span> <span data-ttu-id="0cfbf-121">Ha Ön rendszergazda, akkor kapcsolatot hozhat létre a **Kapcsolat hozzáadása** majd Experian kiválasztásával a legördülő listából.</span><span class="sxs-lookup"><span data-stu-id="0cfbf-121">If you are an administrator, you can create a connection by selecting **Add connection** and choosing Experian from the dropdown list.</span></span> 

1. <span data-ttu-id="0cfbf-122">Válassza a **Csatlakozás Experian** lehetőséget, a kapcsolat kiválasztásának megerősítéséhez.</span><span class="sxs-lookup"><span data-stu-id="0cfbf-122">Select **Connect to Experian** to confirm the connection selection.</span></span>

1.  <span data-ttu-id="0cfbf-123">Válassza a **Tovább** lehetőséget, majd azt az **Ügyfél adatkészlet** -et, amelyet bővíteni szeretne demográfiai adatokkal Experian -ból.</span><span class="sxs-lookup"><span data-stu-id="0cfbf-123">Select **Next** and choose the **Customer data set** you want to enrich with demographics data from Experian.</span></span> <span data-ttu-id="0cfbf-124">Kiválaszthatja a **Vevő** entitást az összes ügyfélprofil gazdagítására, vagy kiválaszthat egy szegmens entitást, amely csak az adott szegmensben található vevőprofilokat gazdagítja.</span><span class="sxs-lookup"><span data-stu-id="0cfbf-124">You can select the **Customer** entity to enrich all your customer profiles or select a segment entity to enrich only customer profiles contained in that segment.</span></span>

    :::image type="content" source="media/enrichment-Experian-configuration-customer-data-set.png" alt-text="Képernyőkép az ügyféladatkészlet kiválasztásáról.":::

1. <span data-ttu-id="0cfbf-126">Válassza a **Tovább** lehetőséget és határozza meg, hogy milyen típusú mezőket kell használni az egyesített profiljaiból az egyező demográfiai adatok kereséséhez Experian -ból .</span><span class="sxs-lookup"><span data-stu-id="0cfbf-126">Select **Next** and define which type of fields from your unified profiles should be used to look for matching demographics data from Experian.</span></span> <span data-ttu-id="0cfbf-127">Legalább egy mezőben meg kell adni a **Név és cím**, a **Telefon** vagy az **E-mail-cím** adatokat.</span><span class="sxs-lookup"><span data-stu-id="0cfbf-127">At least one of the fields **Name and address**, **Phone**, or **Email** is required.</span></span> <span data-ttu-id="0cfbf-128">A nagyobb egyezési pontosság érdekében legfeljebb két másik mezőt lehet hozzáadni.</span><span class="sxs-lookup"><span data-stu-id="0cfbf-128">For a higher match accuracy, up to two other fields can be added.</span></span> <span data-ttu-id="0cfbf-129">Ez a beállítás hatással van a következő lépésben elérhető leképezési mezőkre.</span><span class="sxs-lookup"><span data-stu-id="0cfbf-129">This selection will affect the mapping fields you have access to in the next step.</span></span>

    > [!TIP]
    > <span data-ttu-id="0cfbf-130">Minél több kulcsazonosító-attribútum kerül Experian -ba, annál valószínűbb a magasabb egyezés eredményezése.</span><span class="sxs-lookup"><span data-stu-id="0cfbf-130">More key identifier attributes sent to Experian likely yield a higher match rate.</span></span>

1. <span data-ttu-id="0cfbf-131">A mező leképezésének elkezdéséhez válassza a **Következő** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="0cfbf-131">Select **Next** to start the field mapping.</span></span>

1. <span data-ttu-id="0cfbf-132">Határozza meg, hogy melyik mezőket kell használni az egyesített profiljaiból az egyező demográfiai adatok kereséséhez Experian -ból .</span><span class="sxs-lookup"><span data-stu-id="0cfbf-132">Define which fields from your unified profiles should be used to look for matching demographics data from Experian.</span></span> <span data-ttu-id="0cfbf-133">A kötelező mezők meg vannak jelölve.</span><span class="sxs-lookup"><span data-stu-id="0cfbf-133">Required fields are marked.</span></span>

1. <span data-ttu-id="0cfbf-134">Adja meg a bővítés nevét és a kimeneti entitás nevét.</span><span class="sxs-lookup"><span data-stu-id="0cfbf-134">Provide a name for the enrichment and a name for the output entity.</span></span>

1. <span data-ttu-id="0cfbf-135">Válassza a **Bővítés mentése** lehetőséget, miután áttekintette a lehetőségeit.</span><span class="sxs-lookup"><span data-stu-id="0cfbf-135">Select **Save enrichment** after reviewing your choices.</span></span>

## <a name="configure-the-connection-for-experian"></a><span data-ttu-id="0cfbf-136">Kapcsolat konfigurálása Experian -hoz</span><span class="sxs-lookup"><span data-stu-id="0cfbf-136">Configure the connection for Experian</span></span> 

<span data-ttu-id="0cfbf-137">A kapcsolatok konfiguráljához rendszergazdának kell lennie.</span><span class="sxs-lookup"><span data-stu-id="0cfbf-137">You need to be an administrator to configure connections.</span></span> <span data-ttu-id="0cfbf-138">Válassza a **Kapcsolat hozzáadása** lehetőséget, amikor bővítményt konfigurál *vagy* menjen a **Rendszergazda** > **Kapcsolatok** elemre, és válassza a **Beállítás** lehetőséget az Experian csempén.</span><span class="sxs-lookup"><span data-stu-id="0cfbf-138">Select **Add connection** when configuring an enrichment *or* go to **Admin** > **Connections** and select **Set up** on the Experian tile.</span></span>

1. <span data-ttu-id="0cfbf-139">Válassza az **Első lépések** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="0cfbf-139">Select **Get Started**.</span></span>

1. <span data-ttu-id="0cfbf-140">Adja meg a kapcsolat nevét a **Megjelenítendő név** mezőben.</span><span class="sxs-lookup"><span data-stu-id="0cfbf-140">Enter a name for the connection in the **Display name** box.</span></span>

1. <span data-ttu-id="0cfbf-141">Adja meg a felhasználó azonosítót, partnerazonosítót és modellszámot az Experian Secure Transport fiókjához.</span><span class="sxs-lookup"><span data-stu-id="0cfbf-141">Enter valid User ID, Party ID, and Model Number for your Experian Secure Transport account.</span></span>

1. <span data-ttu-id="0cfbf-142">Tekintse át és adja meg hozzájárulását az **adatvédelem és a megfelelőséghez** az **Elfogadom** által.</span><span class="sxs-lookup"><span data-stu-id="0cfbf-142">Review and provide your consent for **Data privacy and compliance** by selecting **I agree**.</span></span>

1. <span data-ttu-id="0cfbf-143">A konfiguráció megerősítéséhez válassza az **Ellenőrzés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="0cfbf-143">Select **Verify** to validate the configuration.</span></span>

1. <span data-ttu-id="0cfbf-144">Az ellenőrzés befejezése után válassza a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="0cfbf-144">After completing the verification, select **Save**.</span></span>
   
   :::image type="content" source="media/enrichment-Experian-connection.png" alt-text="Experian kapcsolati konfiguráció panel.":::

## <a name="enrichment-results"></a><span data-ttu-id="0cfbf-146">Bővítési eredmények</span><span class="sxs-lookup"><span data-stu-id="0cfbf-146">Enrichment results</span></span>

<span data-ttu-id="0cfbf-147">A bővítési folyamat megkezdéséhez válassza a **Futtatás** parancsot a parancssorból.</span><span class="sxs-lookup"><span data-stu-id="0cfbf-147">To start the enrichment process, select **Run** from the command bar.</span></span> <span data-ttu-id="0cfbf-148">Azt is engedélyezheti, hogy a rendszer a bővítést automatikusan egy [ütemezett frissítés](system.md#schedule-tab) részeként futtassa.</span><span class="sxs-lookup"><span data-stu-id="0cfbf-148">You can also let the system run the enrichment automatically as part of a [scheduled refresh](system.md#schedule-tab).</span></span> <span data-ttu-id="0cfbf-149">A feldolgozási idő az ügyféladatok méretétől és azoktól a bővítés folyamatoktól függ, melyek az Experian fiókjához lettek beállítva.</span><span class="sxs-lookup"><span data-stu-id="0cfbf-149">The processing time will depend on the size of your customer data and the enrichment processes set up for your account by Experian.</span></span>

<span data-ttu-id="0cfbf-150">A bővítési folyamat befejeződése után áttekintheti az újonnan bővített ügyfelek profiljainak adatait a **Saját bővítések** alatt.</span><span class="sxs-lookup"><span data-stu-id="0cfbf-150">After the enrichment process completes, you can review the newly enriched customer profiles data under **My enrichments**.</span></span> <span data-ttu-id="0cfbf-151">Emellett megtalálhatja az utolsó frissítés időpontját és a bővített profilok számát is.</span><span class="sxs-lookup"><span data-stu-id="0cfbf-151">Additionally, you'll find the time of the last update and the number of enriched profiles.</span></span>

<span data-ttu-id="0cfbf-152">Az egyes bővített profilok részletes nézetét a **Bővített adatok megtekintése** lehetőségre kattintva érheti el.</span><span class="sxs-lookup"><span data-stu-id="0cfbf-152">You can access a detailed view of each enriched profile by selecting **View enriched data**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="0cfbf-153">Következő lépések</span><span class="sxs-lookup"><span data-stu-id="0cfbf-153">Next steps</span></span>

<span data-ttu-id="0cfbf-154">Építsen a bővített ügyféladatokra.</span><span class="sxs-lookup"><span data-stu-id="0cfbf-154">Build on top of your enriched customer data.</span></span> <span data-ttu-id="0cfbf-155">Hozzon létre [szegmenseket](segments.md) és [intézkedéseket](measures.md), továbbá [exportálja az adatokat](export-destinations.md) , hogy személyre szabott élményt nyújtson ügyfeleinek.</span><span class="sxs-lookup"><span data-stu-id="0cfbf-155">Create [segments](segments.md) and [measures](measures.md), and even [export the data](export-destinations.md) to deliver personalized experiences to your customers.</span></span>

## <a name="data-privacy-and-compliance"></a><span data-ttu-id="0cfbf-156">Adatvédelem és megfelelőség</span><span class="sxs-lookup"><span data-stu-id="0cfbf-156">Data privacy and compliance</span></span>

<span data-ttu-id="0cfbf-157">Amikor engedélyezed a Dynamics 365 Customer Insights -nak, hogy továbbítsa az adatokat Experian -ba, engedélyezed az adatátvitelt a megfelelőséghatáron kívülre a Dynamics 365 Customer Insights -nak, beleértve az esetlegesen bizalmas adatokat, például személyes adatokat.</span><span class="sxs-lookup"><span data-stu-id="0cfbf-157">When you enable Dynamics 365 Customer Insights to transmit data to Experian, you allow transfer of data outside of the compliance boundary for Dynamics 365 Customer Insights, including potentially sensitive data such as Personal Data.</span></span> <span data-ttu-id="0cfbf-158">A Microsoft az Ön utasítására továbbítja az ilyen adatokat, de Ön felelős annak biztosításáért, hogy az Experian megfeleljen az esetleges adatvédelmi és biztonsági kötelezettségeknek.</span><span class="sxs-lookup"><span data-stu-id="0cfbf-158">Microsoft will transfer such data at your instruction, but you are responsible for ensuring that Experian meets any privacy or security obligations you may have.</span></span> <span data-ttu-id="0cfbf-159">További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).</span><span class="sxs-lookup"><span data-stu-id="0cfbf-159">For more information, see [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?linkid=396732).</span></span>
<span data-ttu-id="0cfbf-160">A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt a bővítést.</span><span class="sxs-lookup"><span data-stu-id="0cfbf-160">Your Dynamics 365 Customer Insights administrator can remove this enrichment at any time to discontinue use of this functionality.</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]
