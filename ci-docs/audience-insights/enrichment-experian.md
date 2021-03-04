---
title: Bővítés a harmadik fél bővítési Experiannal
description: Általános információk a Experian harmadik fél bővítésről.
ms.date: 12/10/2020
ms.reviewer: kishorem
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: baf3cc58a233b70c48fb94ac4a543d162f91bdd1
ms.sourcegitcommit: 139548f8a2d0f24d54c4a6c404a743eeeb8ef8e0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/15/2021
ms.locfileid: "5269563"
---
# <a name="enrich-customer-profiles-with-demographics-from-experian-preview"></a><span data-ttu-id="16435-103">Ügyfelek profiljainak gazdagítása az Experianból (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="16435-103">Enrich customer profiles with demographics from Experian (preview)</span></span>

<span data-ttu-id="16435-104">A Experian a fogyasztói és üzleti hitel-jelentési és marketing szolgáltatások globális vezetője.</span><span class="sxs-lookup"><span data-stu-id="16435-104">Experian is a global leader in consumer and business credit reporting and marketing services.</span></span> <span data-ttu-id="16435-105">Az Experian adatbővítési szolgáltatásai segítségével mélyebben megismerheti az ügyfeleket, ha bővíti az ügyfelek profilját demográfiai adatokkal, például a háztartás méretével, a jövedelemmel és más információkkal.</span><span class="sxs-lookup"><span data-stu-id="16435-105">With Experian’s data enrichment services, you can build a deeper understanding of your customers by enriching your customer profiles with demographic data such as household size, income, and more.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="16435-106">Előfeltételek</span><span class="sxs-lookup"><span data-stu-id="16435-106">Prerequisites</span></span>

<span data-ttu-id="16435-107">Az Experian konfigurálásához teljesülnie kell az alábbi előfeltételeknek:</span><span class="sxs-lookup"><span data-stu-id="16435-107">To configure Experian, the following prerequisites must be met:</span></span>

- <span data-ttu-id="16435-108">Aktív Experian-előfizetése van.</span><span class="sxs-lookup"><span data-stu-id="16435-108">You have an active Experian subscription.</span></span> <span data-ttu-id="16435-109">Az előfizetés megkezdéséhez [forduljon közvetlenül a Experianhoz](https://www.experian.com/marketing-services/contact).</span><span class="sxs-lookup"><span data-stu-id="16435-109">To get a subscription, [contact Experian](https://www.experian.com/marketing-services/contact) directly.</span></span> <span data-ttu-id="16435-110">[További információ az Experian adatgazdagításáról](https://www.experian.com/marketing-services/microsoft?cmpid=ems_web_mci_cdppage).</span><span class="sxs-lookup"><span data-stu-id="16435-110">[Learn more about Experian Data Enrichment](https://www.experian.com/marketing-services/microsoft?cmpid=ems_web_mci_cdppage).</span></span>
- <span data-ttu-id="16435-111">Rendelkezik a Felhasználói azonosítóval, Félazonosítóval és Modellszámmal aaz SSH-képes Secure Transport (ST) fiókhoz, amit az Experian hozott létre Önnek.</span><span class="sxs-lookup"><span data-stu-id="16435-111">You have the User ID, Party ID, and Model Number for your SSH-enabled Secure Transport (ST) account that Experian created for you.</span></span>
- <span data-ttu-id="16435-112">[Rendszergazdai](permissions.md#administrator) jogosultságokkal rendelkezik célközönségi-információkban.</span><span class="sxs-lookup"><span data-stu-id="16435-112">You have [Administrator](permissions.md#administrator) permissions in audience insights.</span></span>

## <a name="configuration"></a><span data-ttu-id="16435-113">Konfigurálás</span><span class="sxs-lookup"><span data-stu-id="16435-113">Configuration</span></span>

1. <span data-ttu-id="16435-114">Menjen a z **Adatok** > **Bővítés** menübe, és válassza a **Felfedezés** lapot.</span><span class="sxs-lookup"><span data-stu-id="16435-114">Go to **Data** > **Enrichment** and select the **Discover** tab.</span></span>

1. <span data-ttu-id="16435-115">Válassza **Az adataim bővítése** lehetőséget a Experian csempén.</span><span class="sxs-lookup"><span data-stu-id="16435-115">Select **Enrich my data** on the Experian tile.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="16435-116">![Experian csempe](media/experian-tile.png "Experian csempe")</span><span class="sxs-lookup"><span data-stu-id="16435-116">![Experian tile](media/experian-tile.png "Experian tile")</span></span>

1. <span data-ttu-id="16435-117">Válassza az **Első lépések** lehetőséget , és adja meg a Experian Secure Transport fiókjához tartozó felhasználói azonosítót, a félazonosítót és a modellszámot.</span><span class="sxs-lookup"><span data-stu-id="16435-117">Select **Get started** and enter the User ID, Party ID, and Model Number for your Experian Secure Transport account.</span></span> <span data-ttu-id="16435-118">Ellenőrizze és adja meg az **adatvédelemre és a megfelelőségre** vonatkozó beleegyezését az **Elfogadom** jelölőnégyzet bejelölésével.</span><span class="sxs-lookup"><span data-stu-id="16435-118">Review and provide your consent for **Data privacy and compliance** by selecting the **I agree** checkbox.</span></span> <span data-ttu-id="16435-119">Az **Alkalmaz** lehetőség választásával erősítse meg a összes bevitt adatot.</span><span class="sxs-lookup"><span data-stu-id="16435-119">Confirm all inputs by selecting **Apply**.</span></span>

## <a name="map-your-fields"></a><span data-ttu-id="16435-120">Mezők megfeleltetése</span><span class="sxs-lookup"><span data-stu-id="16435-120">Map your fields</span></span>

1.  <span data-ttu-id="16435-121">Válassza az **Adatok hozzáadása** lehetőséget, és az Experian vállalati adatokkal bővíteni kívánt **Ügyfél adatkészletet**.</span><span class="sxs-lookup"><span data-stu-id="16435-121">Select **Add data** and choose the **Customer data set** you want to enrich with demographics data from Experian.</span></span> <span data-ttu-id="16435-122">Kiválaszthatja a **Vevő** entitást az összes ügyfélprofil gazdagítására, vagy kiválaszthat egy szegmens entitást, amely csak az adott szegmensben található vevőprofilokat gazdagítja.</span><span class="sxs-lookup"><span data-stu-id="16435-122">You can select the **Customer** entity to enrich all your customer profiles or select a segment entity to enrich only customer profiles contained in that segment.</span></span>

1. <span data-ttu-id="16435-123">Válassza ki a kulcsazonosítókat a **Név és cím**, **E-mail** vagy **Telefon** közül, és küldje el az Experiannek a identitás feloldása érdekében.</span><span class="sxs-lookup"><span data-stu-id="16435-123">Select your key identifiers from **Name and Address**, **E-mail**, or **Phone** to send to Experian for identity resolution.</span></span>

   > [!TIP]
   > <span data-ttu-id="16435-124">Minél több kulcsazonosító-attribútumot küld el az Experian számára, valószínűleg annál nagyobb lesz az egyezési arány.</span><span class="sxs-lookup"><span data-stu-id="16435-124">More key identifier attributes sent to Experian likely yield a higher match rate.</span></span>

1. <span data-ttu-id="16435-125">Válassza a **Tovább** lehetőséget, és képezze le a megfelelő attribútumokat az egyesített ügyfél entitásból a kijelölt kulcsazonosító-mezőkhöz.</span><span class="sxs-lookup"><span data-stu-id="16435-125">Select **Next** and map the corresponding attributes from your unified customer entity for the selected key identifier fields.</span></span>

1. <span data-ttu-id="16435-126">Az **Attribútum hozzáadása** lehetőséget választva leképezheti az összes olyan további attribútumot, amelyet el szeretne küldeni a Experian számára.</span><span class="sxs-lookup"><span data-stu-id="16435-126">Select **Add attribute** to map any additional attributes you would like to send to Experian.</span></span>

1.  <span data-ttu-id="16435-127">Válassza a **Mentés** lehetőséget a mezők leképezésének végrehajtásához.</span><span class="sxs-lookup"><span data-stu-id="16435-127">Select **Save** to complete the field mapping.</span></span>

    > [!div class="mx-imgBorder"]
    > <span data-ttu-id="16435-128">![Experian mezőleképezés](media/experian-field-mapping.png "Experian mezőleképezés")</span><span class="sxs-lookup"><span data-stu-id="16435-128">![Experian field mapping](media/experian-field-mapping.png "Experian field mapping")</span></span>

## <a name="enrichment-results"></a><span data-ttu-id="16435-129">Bővítési eredmények</span><span class="sxs-lookup"><span data-stu-id="16435-129">Enrichment results</span></span>

<span data-ttu-id="16435-130">A bővítési folyamat megkezdéséhez válassza a **Futtatás** parancsot a parancssorból.</span><span class="sxs-lookup"><span data-stu-id="16435-130">To start the enrichment process, select **Run** from the command bar.</span></span> <span data-ttu-id="16435-131">Azt is engedélyezheti, hogy a rendszer a bővítést automatikusan egy [ütemezett frissítés](system.md#schedule-tab) részeként futtassa.</span><span class="sxs-lookup"><span data-stu-id="16435-131">You can also let the system run the enrichment automatically as part of a [scheduled refresh](system.md#schedule-tab).</span></span> <span data-ttu-id="16435-132">A feldolgozási idő az ügyféladatok méretétől és a Experian által a fiókjához beállított bővítési folyamattól függ.</span><span class="sxs-lookup"><span data-stu-id="16435-132">The processing time will depend on the size of your customer data and the enrichment processes set up for your account by Experian.</span></span>

<span data-ttu-id="16435-133">A bővítési folyamat befejeződése után áttekintheti az újonnan bővített ügyfelek profiljainak adatait a **Saját bővítések** alatt.</span><span class="sxs-lookup"><span data-stu-id="16435-133">After the enrichment process completes, you can review the newly enriched customer profiles data under **My enrichments**.</span></span> <span data-ttu-id="16435-134">Emellett megtalálhatja az utolsó frissítés időpontját és a bővített profilok számát is.</span><span class="sxs-lookup"><span data-stu-id="16435-134">Additionally, you'll find the time of the last update and the number of enriched profiles.</span></span>

<span data-ttu-id="16435-135">Az egyes bővített profilok részletes nézetét a **Bővített adatok megtekintése** lehetőségre kattintva érheti el.</span><span class="sxs-lookup"><span data-stu-id="16435-135">You can access a detailed view of each enriched profile by selecting **View enriched data**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="16435-136">Következő lépések</span><span class="sxs-lookup"><span data-stu-id="16435-136">Next steps</span></span>

<span data-ttu-id="16435-137">Építsen a bővített ügyféladatokra.</span><span class="sxs-lookup"><span data-stu-id="16435-137">Build on top of your enriched customer data.</span></span> <span data-ttu-id="16435-138">Hozzon létre [szegmenseket](segments.md), [mértékeket](measures.md) , sőt [exportálhatja az adatokat](export-destinations.md), hogy személyre szabott élményeket tudjon nyújtani az ügyfeleknek.</span><span class="sxs-lookup"><span data-stu-id="16435-138">Create [segments](segments.md), [measures](measures.md), and even [export the data](export-destinations.md) to deliver personalized experiences to your customers.</span></span>

## <a name="data-privacy-and-compliance"></a><span data-ttu-id="16435-139">Adatvédelem és megfelelőség</span><span class="sxs-lookup"><span data-stu-id="16435-139">Data privacy and compliance</span></span>

<span data-ttu-id="16435-140">Amikor engedélyezi az Dynamics 365 Customer Insights szolgáltatást az adatok Experianbe való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat.</span><span class="sxs-lookup"><span data-stu-id="16435-140">When you enable Dynamics 365 Customer Insights to transmit data to Experian, you allow transfer of data outside of the compliance boundary for Dynamics 365 Customer Insights, including potentially sensitive data such as Personal Data.</span></span> <span data-ttu-id="16435-141">A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy az Experian megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek.</span><span class="sxs-lookup"><span data-stu-id="16435-141">Microsoft will transfer such data at your instruction, but you are responsible for ensuring that Experian meets any privacy or security obligations you may have.</span></span> <span data-ttu-id="16435-142">További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).</span><span class="sxs-lookup"><span data-stu-id="16435-142">For more information, see [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?linkid=396732).</span></span>
<span data-ttu-id="16435-143">A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt a bővítést.</span><span class="sxs-lookup"><span data-stu-id="16435-143">Your Dynamics 365 Customer Insights Administrator can remove this enrichment at any time to discontinue use of this functionality.</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]