---
title: Bővítés a harmadik fél bővítési Experiannal
description: Általános információk a Experian harmadik fél bővítésről.
ms.date: 04/09/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: kishorem-ms
ms.author: kishorem
manager: shellyha
ms.openlocfilehash: 9cf2a7fa18ecc022ea67f6829f52381ad59f3172
ms.sourcegitcommit: aaa275c60c0c77c88196277b266a91d653f8f759
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/14/2021
ms.locfileid: "5896376"
---
# <a name="enrich-customer-profiles-with-demographics-from-experian-preview"></a><span data-ttu-id="ea4b8-103">Ügyfelek profiljainak gazdagítása az Experianból (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="ea4b8-103">Enrich customer profiles with demographics from Experian (preview)</span></span>

<span data-ttu-id="ea4b8-104">A Experian a fogyasztói és üzleti hitel-jelentési és marketing szolgáltatások globális vezetője.</span><span class="sxs-lookup"><span data-stu-id="ea4b8-104">Experian is a global leader in consumer and business credit reporting and marketing services.</span></span> <span data-ttu-id="ea4b8-105">Az Experian adatbővítési szolgáltatásai segítségével mélyebben megismerheti az ügyfeleket, ha bővíti az ügyfelek profilját demográfiai adatokkal, például a háztartás méretével, a jövedelemmel és más információkkal.</span><span class="sxs-lookup"><span data-stu-id="ea4b8-105">With Experian’s data enrichment services, you can build a deeper understanding of your customers by enriching your customer profiles with demographic data such as household size, income, and more.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ea4b8-106">Előfeltételek</span><span class="sxs-lookup"><span data-stu-id="ea4b8-106">Prerequisites</span></span>

<span data-ttu-id="ea4b8-107">Az Experian konfigurálásához teljesülnie kell az alábbi előfeltételeknek:</span><span class="sxs-lookup"><span data-stu-id="ea4b8-107">To configure Experian, the following prerequisites must be met:</span></span>

- <span data-ttu-id="ea4b8-108">Aktív Experian-előfizetése van.</span><span class="sxs-lookup"><span data-stu-id="ea4b8-108">You have an active Experian subscription.</span></span> <span data-ttu-id="ea4b8-109">Az előfizetés megkezdéséhez [forduljon közvetlenül a Experianhoz](https://www.experian.com/marketing-services/contact).</span><span class="sxs-lookup"><span data-stu-id="ea4b8-109">To get a subscription, [contact Experian](https://www.experian.com/marketing-services/contact) directly.</span></span> <span data-ttu-id="ea4b8-110">[További információ az Experian adatgazdagításáról](https://www.experian.com/marketing-services/microsoft?cmpid=ems_web_mci_cdppage).</span><span class="sxs-lookup"><span data-stu-id="ea4b8-110">[Learn more about Experian Data Enrichment](https://www.experian.com/marketing-services/microsoft?cmpid=ems_web_mci_cdppage).</span></span>

- <span data-ttu-id="ea4b8-111">Egy Experian-kapcsolatot már konfigurált egy rendszergazda, *vagy* Ön rendelkezik a [rendszergazdai](permissions.md#administrator) engedélyekkel.</span><span class="sxs-lookup"><span data-stu-id="ea4b8-111">An Experian connection has already been configured by an administrator *or* you have [administrator](permissions.md#administrator) permissions.</span></span> <span data-ttu-id="ea4b8-112">Szüksége van az Experian által az Ön számára létrehozott SSH-engedélyezett Secure Transport (ST) fiókjához a felhasználói azonosítóra, a félazonosítóra és a modellszámra is.</span><span class="sxs-lookup"><span data-stu-id="ea4b8-112">You also need the User ID, Party ID, and Model Number for your SSH-enabled Secure Transport (ST) account that Experian created for you.</span></span>

## <a name="configure-the-enrichment"></a><span data-ttu-id="ea4b8-113">Bővítés konfigurálása</span><span class="sxs-lookup"><span data-stu-id="ea4b8-113">Configure the enrichment</span></span>

1. <span data-ttu-id="ea4b8-114">Menjen a z **Adatok** > **Bővítés** menübe, és válassza a **Felfedezés** lapot.</span><span class="sxs-lookup"><span data-stu-id="ea4b8-114">Go to **Data** > **Enrichment** and select the **Discover** tab.</span></span>

1. <span data-ttu-id="ea4b8-115">Válassza **Az adataim bővítése** lehetőséget a Experian csempén.</span><span class="sxs-lookup"><span data-stu-id="ea4b8-115">Select **Enrich my data** on the Experian tile.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="ea4b8-116">![Experian csempe](media/experian-tile.png "Experian csempe")</span><span class="sxs-lookup"><span data-stu-id="ea4b8-116">![Experian tile](media/experian-tile.png "Experian tile")</span></span>
   > 

1. <span data-ttu-id="ea4b8-117">Válasszon egy [kapcsolatot](connections.md) a legördülő listából.</span><span class="sxs-lookup"><span data-stu-id="ea4b8-117">Select a [connection](connections.md) from the drop-down.</span></span> <span data-ttu-id="ea4b8-118">Ha nem érhető el egy kapcsolat sem, akkor forduljon a rendszergazdához.</span><span class="sxs-lookup"><span data-stu-id="ea4b8-118">Contact an administrator if no connection is available.</span></span> <span data-ttu-id="ea4b8-119">Ha Ön rendszergazda, akkor a legördülő menüből válassza ki a **Kapcsolat hozzáadása** és az Experian lehetőséget a kapcsolat létrehozásához.</span><span class="sxs-lookup"><span data-stu-id="ea4b8-119">If you are an administrator, you can create a connection by selecting **Add connection** and choosing Experian from the drop-down.</span></span> 

1. <span data-ttu-id="ea4b8-120">Válassza a **Kapcsolódás az Experianhez** lehetőséget a kapcsolat kiválasztásához.</span><span class="sxs-lookup"><span data-stu-id="ea4b8-120">Select **Connect to Experian** to confirm the connection selection.</span></span>

1.  <span data-ttu-id="ea4b8-121">Válassza a **Következő** lehetőséget, és válassza a demográfiai adatokkal bővíteni kívánt **Ügyfél adatkészletet** az Experianből.</span><span class="sxs-lookup"><span data-stu-id="ea4b8-121">Select **Next** and choose the **Customer data set** you want to enrich with demographics data from Experian.</span></span> <span data-ttu-id="ea4b8-122">Kiválaszthatja a **Vevő** entitást az összes ügyfélprofil gazdagítására, vagy kiválaszthat egy szegmens entitást, amely csak az adott szegmensben található vevőprofilokat gazdagítja.</span><span class="sxs-lookup"><span data-stu-id="ea4b8-122">You can select the **Customer** entity to enrich all your customer profiles or select a segment entity to enrich only customer profiles contained in that segment.</span></span>

    :::image type="content" source="media/enrichment-Experian-configuration-customer-data-set.png" alt-text="Képernyőkép az ügyféladatkészlet kiválasztásáról.":::

1. <span data-ttu-id="ea4b8-124">Válassza a **Következő** lehetőséget, és határozza meg, hogy az egyesített profilokból milyen típusú mezők használhatók az Experianből származó demográfiai adatok egyeztetéséhez.</span><span class="sxs-lookup"><span data-stu-id="ea4b8-124">Select **Next** and define which type of fields from your unified profiles should be used to look for matching demographics data from Experian.</span></span> <span data-ttu-id="ea4b8-125">Legalább egy mezőben meg kell adni a **Név és cím**, a **Telefon** vagy az **E-mail-cím** adatokat.</span><span class="sxs-lookup"><span data-stu-id="ea4b8-125">At least one of the fields **Name and address**, **Phone**, or **Email** is required.</span></span> <span data-ttu-id="ea4b8-126">A nagyobb egyezési pontosság érdekében legfeljebb két másik mezőt lehet hozzáadni.</span><span class="sxs-lookup"><span data-stu-id="ea4b8-126">For a higher match accuracy, up to two other fields can be added.</span></span> <span data-ttu-id="ea4b8-127">Ez a beállítás hatással van a következő lépésben elérhető leképezési mezőkre.</span><span class="sxs-lookup"><span data-stu-id="ea4b8-127">This selection will affect the mapping fields you have access to in the next step.</span></span>

    > [!TIP]
    > <span data-ttu-id="ea4b8-128">Minél több kulcsazonosító-attribútumot küld el az Experian számára, valószínűleg annál nagyobb lesz az egyezési arány.</span><span class="sxs-lookup"><span data-stu-id="ea4b8-128">More key identifier attributes sent to Experian likely yield a higher match rate.</span></span>

1. <span data-ttu-id="ea4b8-129">A mező leképezésének elkezdéséhez válassza a **Következő** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="ea4b8-129">Select **Next** to start the field mapping.</span></span>

1. <span data-ttu-id="ea4b8-130">Határozza meg, hogy az egyesített profilokból mely mezők használhatók az Experianből származó demográfiai adatok egyeztetéséhez.</span><span class="sxs-lookup"><span data-stu-id="ea4b8-130">Define which fields from your unified profiles should be used to look for matching demographics data from Experian.</span></span> <span data-ttu-id="ea4b8-131">A kötelező mezők meg vannak jelölve.</span><span class="sxs-lookup"><span data-stu-id="ea4b8-131">Required fields are marked.</span></span>

1. <span data-ttu-id="ea4b8-132">Adja meg a bővítés nevét és a kimeneti entitás nevét.</span><span class="sxs-lookup"><span data-stu-id="ea4b8-132">Provide a name for the enrichment and a name for the output entity.</span></span>

1. <span data-ttu-id="ea4b8-133">Válassza a **Bővítés mentése** lehetőséget, miután áttekintette a lehetőségeit.</span><span class="sxs-lookup"><span data-stu-id="ea4b8-133">Select **Save enrichment** after reviewing your choices.</span></span>

## <a name="configure-the-connection-for-experian"></a><span data-ttu-id="ea4b8-134">Az Experian kapcsolatának beállítása</span><span class="sxs-lookup"><span data-stu-id="ea4b8-134">Configure the connection for Experian</span></span> 

<span data-ttu-id="ea4b8-135">A kapcsolatok konfiguráljához rendszergazdának kell lennie.</span><span class="sxs-lookup"><span data-stu-id="ea4b8-135">You need to be an administrator to configure connections.</span></span> <span data-ttu-id="ea4b8-136">A bővítés konfigurálásakor válassza a **Kapcsolat hozzáadása** lehetőséget, *vagy* menjen a **Rendszergazda** > **Kapcsolatok** elemre, és válassza a **Beállítások** lehetőséget az Experian csempén.</span><span class="sxs-lookup"><span data-stu-id="ea4b8-136">Select **Add connection** when configuring an enrichment *or* go to **Admin** > **Connections** and select **Set up** on the Experian tile.</span></span>

1. <span data-ttu-id="ea4b8-137">Válassza az **Első lépések** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="ea4b8-137">Select **Get Started**.</span></span>

1. <span data-ttu-id="ea4b8-138">Adja meg a kapcsolat nevét a **Megjelenítendő név** mezőben.</span><span class="sxs-lookup"><span data-stu-id="ea4b8-138">Enter a name for the connection in the **Display name** box.</span></span>

1. <span data-ttu-id="ea4b8-139">Adja meg az Experian Secure Transport fiókjához tartozó érvényes felhasználói azonosítót, félazonosítót és modellszámot.</span><span class="sxs-lookup"><span data-stu-id="ea4b8-139">Enter valid User ID, Party ID, and Model Number for your Experian Secure Transport account.</span></span>

1. <span data-ttu-id="ea4b8-140">Ellenőrizze és adja meg az **adatvédelemre és a megfelelőségre** vonatkozó beleegyezését az **Elfogadom** jelölőnégyzet bejelölésével</span><span class="sxs-lookup"><span data-stu-id="ea4b8-140">Review and provide your consent for **Data privacy and compliance** by selecting the **I agree** checkbox</span></span>

1. <span data-ttu-id="ea4b8-141">A konfiguráció megerősítéséhez válassza az **Ellenőrzés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="ea4b8-141">Select **Verify** to validate the configuration.</span></span>

1. <span data-ttu-id="ea4b8-142">Az ellenőrzés befejezése után válassza a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="ea4b8-142">After completing the verification, select **Save**.</span></span>
   
   :::image type="content" source="media/enrichment-Experian-connection.png" alt-text="Az Experian kapcsolat konfigurációs ablaktábla.":::

## <a name="enrichment-results"></a><span data-ttu-id="ea4b8-144">Bővítési eredmények</span><span class="sxs-lookup"><span data-stu-id="ea4b8-144">Enrichment results</span></span>

<span data-ttu-id="ea4b8-145">A bővítési folyamat megkezdéséhez válassza a **Futtatás** parancsot a parancssorból.</span><span class="sxs-lookup"><span data-stu-id="ea4b8-145">To start the enrichment process, select **Run** from the command bar.</span></span> <span data-ttu-id="ea4b8-146">Azt is engedélyezheti, hogy a rendszer a bővítést automatikusan egy [ütemezett frissítés](system.md#schedule-tab) részeként futtassa.</span><span class="sxs-lookup"><span data-stu-id="ea4b8-146">You can also let the system run the enrichment automatically as part of a [scheduled refresh](system.md#schedule-tab).</span></span> <span data-ttu-id="ea4b8-147">A feldolgozási idő az ügyféladatok méretétől és a Experian által a fiókjához beállított bővítési folyamattól függ.</span><span class="sxs-lookup"><span data-stu-id="ea4b8-147">The processing time will depend on the size of your customer data and the enrichment processes set up for your account by Experian.</span></span>

<span data-ttu-id="ea4b8-148">A bővítési folyamat befejeződése után áttekintheti az újonnan bővített ügyfelek profiljainak adatait a **Saját bővítések** alatt.</span><span class="sxs-lookup"><span data-stu-id="ea4b8-148">After the enrichment process completes, you can review the newly enriched customer profiles data under **My enrichments**.</span></span> <span data-ttu-id="ea4b8-149">Emellett megtalálhatja az utolsó frissítés időpontját és a bővített profilok számát is.</span><span class="sxs-lookup"><span data-stu-id="ea4b8-149">Additionally, you'll find the time of the last update and the number of enriched profiles.</span></span>

<span data-ttu-id="ea4b8-150">Az egyes bővített profilok részletes nézetét a **Bővített adatok megtekintése** lehetőségre kattintva érheti el.</span><span class="sxs-lookup"><span data-stu-id="ea4b8-150">You can access a detailed view of each enriched profile by selecting **View enriched data**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ea4b8-151">Következő lépések</span><span class="sxs-lookup"><span data-stu-id="ea4b8-151">Next steps</span></span>

<span data-ttu-id="ea4b8-152">Építsen a bővített ügyféladatokra.</span><span class="sxs-lookup"><span data-stu-id="ea4b8-152">Build on top of your enriched customer data.</span></span> <span data-ttu-id="ea4b8-153">Hozzon létre [szegmenseket](segments.md), [mértékeket](measures.md) , sőt [exportálhatja az adatokat](export-destinations.md), hogy személyre szabott élményeket tudjon nyújtani az ügyfeleknek.</span><span class="sxs-lookup"><span data-stu-id="ea4b8-153">Create [segments](segments.md), [measures](measures.md), and even [export the data](export-destinations.md) to deliver personalized experiences to your customers.</span></span>

## <a name="data-privacy-and-compliance"></a><span data-ttu-id="ea4b8-154">Adatvédelem és megfelelőség</span><span class="sxs-lookup"><span data-stu-id="ea4b8-154">Data privacy and compliance</span></span>

<span data-ttu-id="ea4b8-155">Amikor engedélyezi az Dynamics 365 Customer Insights szolgáltatást az adatok Experianbe való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat.</span><span class="sxs-lookup"><span data-stu-id="ea4b8-155">When you enable Dynamics 365 Customer Insights to transmit data to Experian, you allow transfer of data outside of the compliance boundary for Dynamics 365 Customer Insights, including potentially sensitive data such as Personal Data.</span></span> <span data-ttu-id="ea4b8-156">A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy az Experian megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek.</span><span class="sxs-lookup"><span data-stu-id="ea4b8-156">Microsoft will transfer such data at your instruction, but you are responsible for ensuring that Experian meets any privacy or security obligations you may have.</span></span> <span data-ttu-id="ea4b8-157">További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).</span><span class="sxs-lookup"><span data-stu-id="ea4b8-157">For more information, see [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?linkid=396732).</span></span>
<span data-ttu-id="ea4b8-158">A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt a bővítést.</span><span class="sxs-lookup"><span data-stu-id="ea4b8-158">Your Dynamics 365 Customer Insights Administrator can remove this enrichment at any time to discontinue use of this functionality.</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]
