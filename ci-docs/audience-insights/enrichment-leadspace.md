---
title: A vállalati profilok bővítése a harmadik féltől származó bővítési Leadspace-szel
description: Általános információk a Leadspace harmadik fél bővítésről.
ms.date: 04/09/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: kishorem-MS
ms.author: kishorem
manager: shellyha
ms.openlocfilehash: ccf4f661ecffb281556a4545b1f26ee809c697cd
ms.sourcegitcommit: aaa275c60c0c77c88196277b266a91d653f8f759
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/14/2021
ms.locfileid: "5895916"
---
# <a name="enrichment-of-company-profiles-with-leadspace-preview"></a><span data-ttu-id="c8cb7-103">A vállalati profilok bővítése Leadspace-szel (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="c8cb7-103">Enrichment of company profiles with Leadspace (preview)</span></span>

<span data-ttu-id="c8cb7-104">A Leadspace egy adatelemző vállalat, amely egy B2B ügyfél-adatplatformot biztosít.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-104">Leadspace is a data science company that provides a B2B Customer Data Platform.</span></span> <span data-ttu-id="c8cb7-105">Lehetővé teszi, hogy az ügyfelek az egyesített ügyfélprofilokkal bővítsék az adataikat.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-105">It enables customers with unified customer profiles for companies to enrich their data.</span></span> <span data-ttu-id="c8cb7-106">A bővítések több attribútumot tartalmaznak,mint például a vállalatméret, székhely, iparág stb.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-106">Enrichments include more attributes such as company size, location, industry, and more.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c8cb7-107">Előfeltételek</span><span class="sxs-lookup"><span data-stu-id="c8cb7-107">Prerequisites</span></span>

<span data-ttu-id="c8cb7-108">A Leadspace konfigurálásához teljesülnie kell az alábbi előfeltételeknek:</span><span class="sxs-lookup"><span data-stu-id="c8cb7-108">To configure Leadspace, the following prerequisites must be met:</span></span>

- <span data-ttu-id="c8cb7-109">Aktív Leadspace-licenccel rendelkezik.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-109">You have an active Leadspace license.</span></span>
- <span data-ttu-id="c8cb7-110">A vállalatokhoz [egyesített ügyfélprofilok](customer-profiles.md) tartoznak.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-110">You have [unified customer profiles](customer-profiles.md) for companies.</span></span>
- <span data-ttu-id="c8cb7-111">A Leadspace kapcsolatot már konfigurálta egy rendszergazda, vagy rendelkezik [rendszergazdai](permissions.md#administrator) engedélyekkel, és a „végleges kulcs” (más néven **Leadspace token**).</span><span class="sxs-lookup"><span data-stu-id="c8cb7-111">A Leadspace connection has already been configured by an administrator or you have [administrator](permissions.md#administrator) permissions and the “perpetual key” (referred to as **Leadspace token**).</span></span> <span data-ttu-id="c8cb7-112">Termékeikkel kapcsolatos részletekért forduljon közvetlenül a [Leadspace-hez](https://www.leadspace.com/products/leadspace-on-demand/).</span><span class="sxs-lookup"><span data-stu-id="c8cb7-112">Contact [Leadspace](https://www.leadspace.com/products/leadspace-on-demand/) directly for details about their product.</span></span>

## <a name="configure-the-enrichment"></a><span data-ttu-id="c8cb7-113">Bővítés konfigurálása</span><span class="sxs-lookup"><span data-stu-id="c8cb7-113">Configure the enrichment</span></span>

1. <span data-ttu-id="c8cb7-114">A célközönség információin belül nyissa meg a következőt: **Adatok** > **Bővítés**.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-114">In audience insights, go to **Data** > **Enrichment**.</span></span>

1. <span data-ttu-id="c8cb7-115">Válassza az **Adatok bővítése** lehetőséget a Leadspace csempén, majd válassza az **Első lépések** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-115">Select **Enrich my data** on the Leadspace tile and select **Get started**.</span></span>

   :::image type="content" source="media/leadspace-tile.png" alt-text="Képernyőkép – Leadspace csempe.":::

1. <span data-ttu-id="c8cb7-117">Válasszon egy [kapcsolatot](connections.md) a legördülő listából.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-117">Select a [connection](connections.md) from the drop-down.</span></span> <span data-ttu-id="c8cb7-118">Ha nem érhető el egy kapcsolat sem, akkor forduljon a rendszergazdához.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-118">Contact an administrator if no connection is available.</span></span> <span data-ttu-id="c8cb7-119">Ha Ön rendszergazda, a **Kapcsolat hozzáadása**, és a **Leadspace** lehetőség kiválasztásával hozhat létre kapcsolatot.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-119">If you are an administrator, you can create a connection by selecting **Add connection** and choosing **Leadspace**.</span></span> 

1. <span data-ttu-id="c8cb7-120">Válassza a **Kapcsolódás a Leadspace-hez** lehetőséget a kapcsolat megerősítéséhez.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-120">Select **Connect to Leadspace** to confirm the connection.</span></span>

1. <span data-ttu-id="c8cb7-121">Válassza a **Következő** lehetőséget, és válassza a vállalati adatokkal bővíteni kívánt **Ügyfél adatkészletet** a Leadspace-ből.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-121">Select **Next** and choose the **Customer data set** you want to enrich with company data from Leadspace.</span></span> <span data-ttu-id="c8cb7-122">Kiválaszthatja a **Vevő** entitást az összes ügyfélprofil gazdagítására, vagy kiválaszthat egy szegmens entitást, amely csak az adott szegmensben található vevőprofilokat gazdagítja.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-122">You can select the **Customer** entity to enrich all your customer profiles or select a segment entity to enrich only customer profiles contained in that segment.</span></span>

    :::image type="content" source="media/enrichment-Leadspace-configuration-customer-data-set.png" alt-text="Képernyőkép az ügyféladatkészlet kiválasztásáról.":::

1. <span data-ttu-id="c8cb7-124">Válassza a **Következő** lehetőséget, és határozza meg, hogy az egyesített profilokból mely mezők használhatók a Leadspace-ből származó vállalati adatok egyeztetéséhez.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-124">Select **Next** and define which fields from your unified profiles are used to look for matching company data from Leadspace.</span></span> <span data-ttu-id="c8cb7-125">A **Vállalat neve** mező kitöltése kötelező.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-125">The **Name of company** field is required.</span></span> <span data-ttu-id="c8cb7-126">A nagyobb egyeztetési pontosság érdekében akár két másik mező is hozzáadható: **Vállalati webhely** és **Vállalat székhelye**.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-126">For a higher match accuracy, up to two other fields, **Company website** and **Company location**, can be added.</span></span>

   :::image type="content" source="media/enrichment-leadspace-mapping.png" alt-text="Leadspace mező leképezési ablaka.":::

1. <span data-ttu-id="c8cb7-128">A mező leképezésének befejezéséhez válassza a **Következő** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-128">Select **Next** to complete the field mapping.</span></span>

1. <span data-ttu-id="c8cb7-129">Adja meg a bővítés nevét, és válassza a **Bővítés memtése** lehetőséget a lehetőségek áttekintése után.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-129">Provide a name for the enrichment and select **Save enrichment** after reviewing your choices.</span></span>


## <a name="configure-the-connection-for-leadspace"></a><span data-ttu-id="c8cb7-130">A Leadspace kapcsolatának beállítása</span><span class="sxs-lookup"><span data-stu-id="c8cb7-130">Configure the connection for Leadspace</span></span> 

<span data-ttu-id="c8cb7-131">A kapcsolatok konfiguráljához rendszergazdának kell lennie.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-131">You need to be an administrator to configure connections.</span></span> <span data-ttu-id="c8cb7-132">A bővítés konfigurálásakor válassza a **Kapcsolat hozzáadása** lehetőséget, *vagy* menjen a **Rendszergazda** > **Kapcsolatok** elemre, és válassza a **Beállítások** lehetőséget a Leadspace csempén.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-132">Select **Add connection** when configuring an enrichment *or* go to **Admin** > **Connections** and select **Set up** on the Leadspace tile.</span></span>

1. <span data-ttu-id="c8cb7-133">Válassza az **Első lépések** lehetőséget</span><span class="sxs-lookup"><span data-stu-id="c8cb7-133">Select **Get Started**</span></span> 

1. <span data-ttu-id="c8cb7-134">Adja meg a kapcsolat nevét a **Megjelenítendő név** mezőben.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-134">Enter a name for the connection in the **Display name** box.</span></span>

1. <span data-ttu-id="c8cb7-135">Adjon meg egy érvényes Leadspace jogkivonatot.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-135">Provide a valid Leadspace token.</span></span>

1. <span data-ttu-id="c8cb7-136">Ellenőrizze és adja meg az **adatvédelemre és a megfelelőségre** vonatkozó beleegyezését az **Elfogadom** jelölőnégyzet bejelölésével</span><span class="sxs-lookup"><span data-stu-id="c8cb7-136">Review and provide your consent for **Data privacy and compliance** by selecting the **I agree** checkbox</span></span>

1. <span data-ttu-id="c8cb7-137">A konfiguráció megerősítéséhez válassza az **Ellenőrzés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-137">Select **Verify** to validate the configuration.</span></span>

1. <span data-ttu-id="c8cb7-138">Az ellenőrzés befejezése után válassza a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-138">After completing the verification, select **Save**.</span></span>
   
   :::image type="content" source="media/enrichment-Leadspace-connection.png" alt-text="Az Leadspace kapcsolat konfigurációs oldala.":::

## <a name="enrichment-results"></a><span data-ttu-id="c8cb7-140">Bővítési eredmények</span><span class="sxs-lookup"><span data-stu-id="c8cb7-140">Enrichment results</span></span>

<span data-ttu-id="c8cb7-141">A bővítés frissítése után áttekintheti az újonnan bővített vállalati adatokat a [Saját bővítések](enrichment-hub.md) alatt.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-141">After refreshing the enrichment, you can review the newly enriched company data under [My enrichments](enrichment-hub.md).</span></span> <span data-ttu-id="c8cb7-142">Megkeresheti az utolsó frissítés időpontját és a bővített profilok számát.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-142">You can find the time of the last update and the number of enriched profiles.</span></span>

<span data-ttu-id="c8cb7-143">Az egyes bővített profilok részletes nézetét a **Bővített adatok megtekintése** lehetőségre kattintva érheti el.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-143">You can access a detailed view of each enriched profile by selecting **View enriched data**.</span></span>

<span data-ttu-id="c8cb7-144">További tájékoztatásért tekintse meg a [Leadspace API-kat](https://support.leadspace.com/hc/en-us/sections/201997649-API).</span><span class="sxs-lookup"><span data-stu-id="c8cb7-144">For more information, see [Leadspace APIs](https://support.leadspace.com/hc/en-us/sections/201997649-API).</span></span>

## <a name="next-steps"></a><span data-ttu-id="c8cb7-145">Következő lépések</span><span class="sxs-lookup"><span data-stu-id="c8cb7-145">Next steps</span></span>

<span data-ttu-id="c8cb7-146">Építsen a bővített ügyféladatokra.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-146">Build on top of your enriched customer data.</span></span> <span data-ttu-id="c8cb7-147">Hozzon létre [szegmenseket](segments.md), [mértékeket](measures.md) , sőt [exportálhatja az adatokat](export-destinations.md), hogy személyre szabott élményeket tudjon nyújtani az ügyfeleknek.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-147">Create [segments](segments.md), [measures](measures.md), and even [export the data](export-destinations.md) to deliver personalized experiences to your customers.</span></span>

## <a name="data-privacy-and-compliance"></a><span data-ttu-id="c8cb7-148">Adatvédelem és megfelelőség</span><span class="sxs-lookup"><span data-stu-id="c8cb7-148">Data privacy and compliance</span></span>

<span data-ttu-id="c8cb7-149">Amikor engedélyezi a Dynamics 365 Customer Insights szolgáltatást az adatok Leadspace szolgáltatásba való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-149">When you enable Dynamics 365 Customer Insights to transmit data to Leadspace, you allow transfer of data outside of the compliance boundary for Dynamics 365 Customer Insights, including potentially sensitive data such as Personal Data.</span></span> <span data-ttu-id="c8cb7-150">A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy a Leadspace megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-150">Microsoft will transfer such data at your instruction, but you are responsible for ensuring that Leadspace meets any privacy or security obligations you may have.</span></span> <span data-ttu-id="c8cb7-151">További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).</span><span class="sxs-lookup"><span data-stu-id="c8cb7-151">For more information, see [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?linkid=396732).</span></span>
<span data-ttu-id="c8cb7-152">A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt a bővítést.</span><span class="sxs-lookup"><span data-stu-id="c8cb7-152">Your Dynamics 365 Customer Insights Administrator can remove this enrichment at any time to discontinue use of this functionality.</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]
