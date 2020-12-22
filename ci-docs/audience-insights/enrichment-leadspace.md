---
title: A vállalati profilok bővítése a harmadik féltől származó bővítési Leadspace-szel
description: Általános információk a Leadspace harmadik fél bővítésről.
ms.date: 11/24/2020
ms.reviewer: kishorem
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: 1b5c6e46e8e424df83e855d81fc4dd7ecb394e3c
ms.sourcegitcommit: a9b2cf598f256d07a48bba8617347ee90024a1dd
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/03/2020
ms.locfileid: "4668726"
---
# <a name="enrichment-of-company-profiles-with-leadspace-preview"></a><span data-ttu-id="600bd-103">A vállalati profilok bővítése Leadspace-szel (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="600bd-103">Enrichment of company profiles with Leadspace (preview)</span></span>

<span data-ttu-id="600bd-104">A Leadspace egy adatelemző vállalat, amely egy B2B ügyfél-adatplatformot biztosít.</span><span class="sxs-lookup"><span data-stu-id="600bd-104">Leadspace is a data science company that provides a B2B Customer Data Platform.</span></span> <span data-ttu-id="600bd-105">Lehetővé teszi, hogy az ügyfelek az egyesített ügyfélprofilokkal bővítsék az adataikat.</span><span class="sxs-lookup"><span data-stu-id="600bd-105">It enables customers with unified customer profiles for companies to enrich their data.</span></span> <span data-ttu-id="600bd-106">A bővítések tartalmaznak kiegészítő attribútumokkal, mint például vállalatméret, székhely, iparág stb.</span><span class="sxs-lookup"><span data-stu-id="600bd-106">Enrichments include additional attributes such as company size, location, industry, and more.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="600bd-107">Előfeltételek</span><span class="sxs-lookup"><span data-stu-id="600bd-107">Prerequisites</span></span>

<span data-ttu-id="600bd-108">A Leadspace konfigurálásához teljesülnie kell az alábbi előfeltételeknek:</span><span class="sxs-lookup"><span data-stu-id="600bd-108">To configure Leadspace, the following prerequisites must be met:</span></span>

- <span data-ttu-id="600bd-109">Aktív Leadspace licence van, és "végleges kulcsa" (más néven **Leadspace-token**).</span><span class="sxs-lookup"><span data-stu-id="600bd-109">You have an active Leadspace license and the “perpetual key” (referred to as **Leadspace token**).</span></span> <span data-ttu-id="600bd-110">A termékkel kapcsolatos részletekért forduljon közvetlenül a [Leadspace](https://www.leadspace.com/products/leadspace-on-demand/) vállalathoz.</span><span class="sxs-lookup"><span data-stu-id="600bd-110">Contact directly [Leadspace](https://www.leadspace.com/products/leadspace-on-demand/) for details about their product.</span></span>
- <span data-ttu-id="600bd-111">[Rendszergazda](permissions.md#administrator) engedéllyel rendelkezik.</span><span class="sxs-lookup"><span data-stu-id="600bd-111">You have [Administrator](permissions.md#administrator) permissions.</span></span>
- <span data-ttu-id="600bd-112">A vállalatokhoz [egyesített ügyfélprofilok](customer-profiles.md) tartoznak.</span><span class="sxs-lookup"><span data-stu-id="600bd-112">You have [unified customer profiles](customer-profiles.md) for companies.</span></span>

## <a name="configuration"></a><span data-ttu-id="600bd-113">Konfigurálás</span><span class="sxs-lookup"><span data-stu-id="600bd-113">Configuration</span></span>

1. <span data-ttu-id="600bd-114">A célközönség információin belül nyissa meg a következőt: **Adatok** > **Bővítés**.</span><span class="sxs-lookup"><span data-stu-id="600bd-114">In audience insights, go to **Data** > **Enrichment**.</span></span>

1. <span data-ttu-id="600bd-115">Válassza az **Adataim bővítése** lehetőséget a Leadspace csempéjén.</span><span class="sxs-lookup"><span data-stu-id="600bd-115">Select **Enrich my data** on the Leadspace tile.</span></span>

   :::image type="content" source="media/leadspace-tile.png" alt-text="Képernyőkép – Leadspace csempe.":::

1. <span data-ttu-id="600bd-117">Válassza az **Első lépések** lehetőséget , majd adja meg az aktív **Leadspace-tokent** (végleges kulcs).</span><span class="sxs-lookup"><span data-stu-id="600bd-117">Select **Get Started** and then enter an active **Leadspace token** (perpetual key).</span></span> <span data-ttu-id="600bd-118">Ellenőrizze és adja meg az **adatvédelemre és a megfelelőségre** vonatkozó beleegyezését az **Elfogadom** jelölőnégyzet bejelölésével.</span><span class="sxs-lookup"><span data-stu-id="600bd-118">Review and provide your consent for **Data privacy and compliance** by selecting the **I agree** checkbox.</span></span> <span data-ttu-id="600bd-119">Erősítse meg mindkét bemenetet a **Csatlakozik a Leadspace-hez** lehetőség kiválasztásával.</span><span class="sxs-lookup"><span data-stu-id="600bd-119">Confirm both inputs by selecting **Connect to Leadspace**.</span></span>

1. <span data-ttu-id="600bd-120">Válassza az **Adatok leképezése** lehetőséget, és adja meg, hogy az egyesített profilokból mely mezők használhatók a Leadspace-ből származó megfelelő vállalati adatok kereséséhez.</span><span class="sxs-lookup"><span data-stu-id="600bd-120">Select **Map data** and define which fields from your unified profiles should be used to look for matching company data from Leadspace.</span></span> <span data-ttu-id="600bd-121">A **Vállalat neve** mező kitöltése kötelező.</span><span class="sxs-lookup"><span data-stu-id="600bd-121">The **Name of company** field is required.</span></span> <span data-ttu-id="600bd-122">A nagyobb egyeztetési pontosság érdekében akár két másik mező is hozzáadható: **Vállalati webhely** és **Vállalat székhelye**.</span><span class="sxs-lookup"><span data-stu-id="600bd-122">For a higher match accuracy, up to two other fields, **Company website** and **Company location**, can be added.</span></span>

   :::image type="content" source="media/enrichment-leadspace-mapping.png" alt-text="Leadspace mező leképezési ablaka.":::
   
1. <span data-ttu-id="600bd-124">Válassza az **Alkalmaz** lehetőséget a mezők leképezésének végrehajtásához.</span><span class="sxs-lookup"><span data-stu-id="600bd-124">Select **Apply** to complete the field mapping.</span></span>

1. <span data-ttu-id="600bd-125">Válassza a **Futtatás** lehetőséget a vállalati profilok bővítése érdekében.</span><span class="sxs-lookup"><span data-stu-id="600bd-125">Select **Run** to enrich the company profiles.</span></span> <span data-ttu-id="600bd-126">A bővítés időtartama az egyesített ügyfélprofilok számától függ.</span><span class="sxs-lookup"><span data-stu-id="600bd-126">How long an enrichment takes depends on the number of unified customer profiles.</span></span>

## <a name="enrichment-results"></a><span data-ttu-id="600bd-127">Bővítési eredmények</span><span class="sxs-lookup"><span data-stu-id="600bd-127">Enrichment results</span></span>

<span data-ttu-id="600bd-128">A bővítés frissítése után áttekintheti az újonnan bővített vállalati adatokat a [Saját bővítések](enrichment-hub.md) alatt.</span><span class="sxs-lookup"><span data-stu-id="600bd-128">After refreshing the enrichment, you can review the newly enriched company data under [My enrichments](enrichment-hub.md).</span></span> <span data-ttu-id="600bd-129">Megkeresheti az utolsó frissítés időpontját és a bővített profilok számát.</span><span class="sxs-lookup"><span data-stu-id="600bd-129">You can find the time of the last update and the number of enriched profiles.</span></span>

<span data-ttu-id="600bd-130">Az egyes bővített profilok részletes nézetét a **Bővített adatok megtekintése** lehetőségre kattintva érheti el.</span><span class="sxs-lookup"><span data-stu-id="600bd-130">You can access a detailed view of each enriched profile by selecting **View enriched data**.</span></span>

<span data-ttu-id="600bd-131">További tájékoztatásért tekintse meg a [Leadspace API-kat](https://support.leadspace.com/hc/en-us/sections/201997649-API).</span><span class="sxs-lookup"><span data-stu-id="600bd-131">For more information, see [Leadspace APIs](https://support.leadspace.com/hc/en-us/sections/201997649-API).</span></span>

## <a name="next-steps"></a><span data-ttu-id="600bd-132">Következő lépések</span><span class="sxs-lookup"><span data-stu-id="600bd-132">Next steps</span></span>

<span data-ttu-id="600bd-133">Építsen a bővített ügyféladatokra.</span><span class="sxs-lookup"><span data-stu-id="600bd-133">Build on top of your enriched customer data.</span></span> <span data-ttu-id="600bd-134">Hozzon létre [szegmenseket](segments.md), [mértékeket](measures.md) , sőt [exportálhatja az adatokat](export-destinations.md), hogy személyre szabott élményeket tudjon nyújtani az ügyfeleknek.</span><span class="sxs-lookup"><span data-stu-id="600bd-134">Create [segments](segments.md), [measures](measures.md), and even [export the data](export-destinations.md) to deliver personalized experiences to your customers.</span></span>

## <a name="data-privacy-and-compliance"></a><span data-ttu-id="600bd-135">Adatvédelem és megfelelőség</span><span class="sxs-lookup"><span data-stu-id="600bd-135">Data privacy and compliance</span></span>

<span data-ttu-id="600bd-136">Amikor engedélyezi a Dynamics 365 Customer Insights szolgáltatást az adatok Leadspace szolgáltatásba való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat.</span><span class="sxs-lookup"><span data-stu-id="600bd-136">When you enable Dynamics 365 Customer Insights to transmit data to Leadspace, you allow transfer of data outside of the compliance boundary for Dynamics 365 Customer Insights, including potentially sensitive data such as Personal Data.</span></span> <span data-ttu-id="600bd-137">A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy a Leadspace megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek.</span><span class="sxs-lookup"><span data-stu-id="600bd-137">Microsoft will transfer such data at your instruction, but you are responsible for ensuring that Leadspace meets any privacy or security obligations you may have.</span></span> <span data-ttu-id="600bd-138">További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).</span><span class="sxs-lookup"><span data-stu-id="600bd-138">For more information, see [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?linkid=396732).</span></span>
<span data-ttu-id="600bd-139">A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt a bővítést.</span><span class="sxs-lookup"><span data-stu-id="600bd-139">Your Dynamics 365 Customer Insights Administrator can remove this enrichment at any time to discontinue use of this functionality.</span></span>