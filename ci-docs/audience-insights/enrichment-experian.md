---
title: Bővítés a harmadik fél bővítési Experiannal
description: Általános információk a Experian harmadik fél bővítésről.
ms.date: 09/17/2020
ms.reviewer: kishorem
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: 60fc49734e54740e83b47a7028be216a0eb81e49
ms.sourcegitcommit: a9b2cf598f256d07a48bba8617347ee90024a1dd
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/03/2020
ms.locfileid: "4668815"
---
# <a name="enrich-customer-profiles-with-demographics-from-experian-preview"></a><span data-ttu-id="5ba6c-103">Ügyfelek profiljainak gazdagítása az Experianból (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="5ba6c-103">Enrich customer profiles with demographics from Experian (preview)</span></span>

<span data-ttu-id="5ba6c-104">A Experian a fogyasztói és üzleti hitel-jelentési és marketing szolgáltatások globális vezetője.</span><span class="sxs-lookup"><span data-stu-id="5ba6c-104">Experian is a global leader in consumer and business credit reporting and marketing services.</span></span> <span data-ttu-id="5ba6c-105">Az Experian adatbővítési szolgáltatásai segítségével mélyebben megismerheti az ügyfeleket, ha bővíti az ügyfelek profilját demográfiai adatokkal, például a háztartás méretével, a jövedelemmel és más információkkal.</span><span class="sxs-lookup"><span data-stu-id="5ba6c-105">With Experian’s data enrichment services, you can build a deeper understanding of your customers by enriching your customer profiles with demographic data such as household size, income, and more.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5ba6c-106">Előfeltételek</span><span class="sxs-lookup"><span data-stu-id="5ba6c-106">Prerequisites</span></span>

<span data-ttu-id="5ba6c-107">Az Experian konfigurálásához teljesülnie kell az alábbi előfeltételeknek:</span><span class="sxs-lookup"><span data-stu-id="5ba6c-107">To configure Experian, the following prerequisites must be met:</span></span>

- <span data-ttu-id="5ba6c-108">Aktív Experian-előfizetése van.</span><span class="sxs-lookup"><span data-stu-id="5ba6c-108">You have an active Experian subscription.</span></span> <span data-ttu-id="5ba6c-109">Az előfizetés megkezdéséhez [forduljon közvetlenül a Experianhoz](https://www.experian.com/marketing-services/contact).</span><span class="sxs-lookup"><span data-stu-id="5ba6c-109">To get a subscription, [contact Experian](https://www.experian.com/marketing-services/contact) directly.</span></span> <span data-ttu-id="5ba6c-110">[További információ az Experian adatgazdagításáról](https://www.experian.com/marketing-services/microsoft?cmpid=ems_web_mci_cdppage).</span><span class="sxs-lookup"><span data-stu-id="5ba6c-110">[Learn more about Experian Data Enrichment](https://www.experian.com/marketing-services/microsoft?cmpid=ems_web_mci_cdppage).</span></span>
- <span data-ttu-id="5ba6c-111">Rendelkezik a Felhasználói azonosítóval, Félazonosítóval és Modellszámmal aaz SSH-képes Secure Transport (ST) fiókhoz, amit az Experian hozott létre Önnek.</span><span class="sxs-lookup"><span data-stu-id="5ba6c-111">You have the User ID, Party ID, and Model Number for your SSH-enabled Secure Transport (ST) account that Experian created for you.</span></span>
- <span data-ttu-id="5ba6c-112">[Rendszergazdai](permissions.md#administrator) jogosultságokkal rendelkezik célközönségi-információkban.</span><span class="sxs-lookup"><span data-stu-id="5ba6c-112">You have [Administrator](permissions.md#administrator) permissions in audience insights.</span></span>

## <a name="configuration"></a><span data-ttu-id="5ba6c-113">Konfigurálás</span><span class="sxs-lookup"><span data-stu-id="5ba6c-113">Configuration</span></span>

1. <span data-ttu-id="5ba6c-114">Menjen a z **Adatok** > **Bővítés** menübe, és válassza a **Felfedezés** lapot.</span><span class="sxs-lookup"><span data-stu-id="5ba6c-114">Go to **Data** > **Enrichment** and select the **Discover** tab.</span></span>

1. <span data-ttu-id="5ba6c-115">Válassza **Az adataim bővítése** lehetőséget a Experian csempén.</span><span class="sxs-lookup"><span data-stu-id="5ba6c-115">Select **Enrich my data** on the Experian tile.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="5ba6c-116">![Experian csempe](media/experian-tile.png "Experian csempe")</span><span class="sxs-lookup"><span data-stu-id="5ba6c-116">![Experian tile](media/experian-tile.png "Experian tile")</span></span>

1. <span data-ttu-id="5ba6c-117">Válassza az **Első lépések** lehetőséget , és adja meg a Experian Secure Transport fiókjához tartozó felhasználói azonosítót, a félazonosítót és a modellszámot.</span><span class="sxs-lookup"><span data-stu-id="5ba6c-117">Select **Get started** and enter the User ID, Party ID, and Model Number for your Experian Secure Transport account.</span></span> <span data-ttu-id="5ba6c-118">Ellenőrizze és adja meg az **adatvédelemre és a megfelelőségre** vonatkozó beleegyezését az **Elfogadom** jelölőnégyzet bejelölésével.</span><span class="sxs-lookup"><span data-stu-id="5ba6c-118">Review and provide your consent for **Data privacy and compliance** by selecting the **I agree** checkbox.</span></span> <span data-ttu-id="5ba6c-119">Az **Alkalmaz** lehetőség választásával erősítse meg a összes bevitt adatot.</span><span class="sxs-lookup"><span data-stu-id="5ba6c-119">Confirm all inputs by selecting **Apply**.</span></span>

## <a name="map-your-fields"></a><span data-ttu-id="5ba6c-120">Mezők leképezése</span><span class="sxs-lookup"><span data-stu-id="5ba6c-120">Map your fields</span></span>

1. <span data-ttu-id="5ba6c-121">Válassza az **Adatok hozzáadása** lehetőséget, és adja meg a kulcsazonosítókat a **Név és a cím**, **E-mail** vagy a **Telefon** helyről, hogyelküldje Experian számára a személyazonosság feloldásához.</span><span class="sxs-lookup"><span data-stu-id="5ba6c-121">Select **Add data** and choose your key identifiers from **Name and Address**, **E-mail**, or **Phone** to send to Experian for identity resolution.</span></span>

   > [!TIP]
   > <span data-ttu-id="5ba6c-122">Minél több kulcsazonosító-attribútumot küld el az Experian számára, valószínűleg annál nagyobb lesz az egyezési arány.</span><span class="sxs-lookup"><span data-stu-id="5ba6c-122">More key identifier attributes sent to Experian likely yield a higher match rate.</span></span>

1. <span data-ttu-id="5ba6c-123">Válassza a **Tovább** lehetőséget, és képezze le a megfelelő attribútumokat az egyesített ügyfél entitásból a kijelölt kulcsazonosító-mezőkhöz.</span><span class="sxs-lookup"><span data-stu-id="5ba6c-123">Select **Next** and map the corresponding attributes from your unified customer entity for the selected key identifier fields.</span></span>

1. <span data-ttu-id="5ba6c-124">Az **Attribútum hozzáadása** lehetőséget választva leképezheti az összes olyan további attribútumot, amelyet el szeretne küldeni a Experian számára.</span><span class="sxs-lookup"><span data-stu-id="5ba6c-124">Select **Add attribute** to map any additional attributes you would like to send to Experian.</span></span>

1.  <span data-ttu-id="5ba6c-125">Válassza a **Mentés** lehetőséget a mezők leképezésének végrehajtásához.</span><span class="sxs-lookup"><span data-stu-id="5ba6c-125">Select **Save** to complete the field mapping.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="5ba6c-126">![Experian mezőleképezés](media/experian-field-mapping.png "Experian mezőleképezés")</span><span class="sxs-lookup"><span data-stu-id="5ba6c-126">![Experian field mapping](media/experian-field-mapping.png "Experian field mapping")</span></span>

## <a name="enrichment-results"></a><span data-ttu-id="5ba6c-127">Bővítési eredmények</span><span class="sxs-lookup"><span data-stu-id="5ba6c-127">Enrichment results</span></span>

<span data-ttu-id="5ba6c-128">A bővítési folyamat megkezdéséhez válassza a **Futtatás** parancsot a parancssorból.</span><span class="sxs-lookup"><span data-stu-id="5ba6c-128">To start the enrichment process, select **Run** from the command bar.</span></span> <span data-ttu-id="5ba6c-129">Azt is engedélyezheti, hogy a rendszer a bővítést automatikusan egy [ütemezett frissítés](system.md#schedule-tab) részeként futtassa.</span><span class="sxs-lookup"><span data-stu-id="5ba6c-129">You can also let the system run the enrichment automatically as part of a [scheduled refresh](system.md#schedule-tab).</span></span> <span data-ttu-id="5ba6c-130">A feldolgozási idő az ügyféladatok méretétől és a Experian által a fiókjához beállított bővítési folyamattól függ.</span><span class="sxs-lookup"><span data-stu-id="5ba6c-130">The processing time will depend on the size of your customer data and the enrichment processes set up for your account by Experian.</span></span>

<span data-ttu-id="5ba6c-131">A bővítési folyamat befejeződése után áttekintheti az újonnan bővített ügyfelek profiljainak adatait a **Saját bővítések** alatt.</span><span class="sxs-lookup"><span data-stu-id="5ba6c-131">After the enrichment process completes, you can review the newly enriched customer profiles data under **My enrichments**.</span></span> <span data-ttu-id="5ba6c-132">Emellett megtalálhatja az utolsó frissítés időpontját és a bővített profilok számát is.</span><span class="sxs-lookup"><span data-stu-id="5ba6c-132">Additionally, you'll find the time of the last update and the number of enriched profiles.</span></span>

<span data-ttu-id="5ba6c-133">Az egyes bővített profilok részletes nézetét a **Bővített adatok megtekintése** lehetőségre kattintva érheti el.</span><span class="sxs-lookup"><span data-stu-id="5ba6c-133">You can access a detailed view of each enriched profile by selecting **View enriched data**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="5ba6c-134">Következő lépések</span><span class="sxs-lookup"><span data-stu-id="5ba6c-134">Next steps</span></span>

<span data-ttu-id="5ba6c-135">Építsen a bővített ügyféladatokra.</span><span class="sxs-lookup"><span data-stu-id="5ba6c-135">Build on top of your enriched customer data.</span></span> <span data-ttu-id="5ba6c-136">Hozzon létre [szegmenseket](segments.md), [mértékeket](measures.md) , sőt [exportálhatja az adatokat](export-destinations.md), hogy személyre szabott élményeket tudjon nyújtani az ügyfeleknek.</span><span class="sxs-lookup"><span data-stu-id="5ba6c-136">Create [segments](segments.md), [measures](measures.md), and even [export the data](export-destinations.md) to deliver personalized experiences to your customers.</span></span>

## <a name="data-privacy-and-compliance"></a><span data-ttu-id="5ba6c-137">Adatvédelem és megfelelőség</span><span class="sxs-lookup"><span data-stu-id="5ba6c-137">Data privacy and compliance</span></span>

<span data-ttu-id="5ba6c-138">Amikor engedélyezi az Dynamics 365 Customer Insights szolgáltatást az adatok Experianbe való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat.</span><span class="sxs-lookup"><span data-stu-id="5ba6c-138">When you enable Dynamics 365 Customer Insights to transmit data to Experian, you allow transfer of data outside of the compliance boundary for Dynamics 365 Customer Insights, including potentially sensitive data such as Personal Data.</span></span> <span data-ttu-id="5ba6c-139">A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy az Experian megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek.</span><span class="sxs-lookup"><span data-stu-id="5ba6c-139">Microsoft will transfer such data at your instruction, but you are responsible for ensuring that Experian meets any privacy or security obligations you may have.</span></span> <span data-ttu-id="5ba6c-140">További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).</span><span class="sxs-lookup"><span data-stu-id="5ba6c-140">For more information, see [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?linkid=396732).</span></span>
<span data-ttu-id="5ba6c-141">A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt a bővítést.</span><span class="sxs-lookup"><span data-stu-id="5ba6c-141">Your Dynamics 365 Customer Insights Administrator can remove this enrichment at any time to discontinue use of this functionality.</span></span>
