---
title: Customer Insights adatok exportálása a Marketóba
description: Megismerheti, hogyan konfigurálható a kapcsolat a Marketóval.
ms.date: 11/12/2020
ms.reviewer: philk
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: 34ccee2894f1f2b552d0c6a88a6810e2dfc677a3
ms.sourcegitcommit: 0b1d3ca11b8ba362a959da0eea15c37e9cdba084
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/18/2020
ms.locfileid: "4570406"
---
# <a name="connector-for-marketo-preview"></a><span data-ttu-id="13c82-103">A Marketo összekötője (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="13c82-103">Connector for Marketo (preview)</span></span>

<span data-ttu-id="13c82-104">Az egyesített ügyfélprofilok szegmensei exportálásának felhasználásával kampányokat hozhat létre, e-mail-marketing szolgáltatást biztosíthat és előnyt kovácsolhat az ügyfelek meghatározott csoportjából a Marketo szolgáltatással.</span><span class="sxs-lookup"><span data-stu-id="13c82-104">Export segments of unified customer profiles to generate campaigns, provide email marketing and use specific groups of customers with Marketo.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="13c82-105">Előfeltételek</span><span class="sxs-lookup"><span data-stu-id="13c82-105">Prerequisites</span></span>

-   <span data-ttu-id="13c82-106">Rendelkezik [Marketo-fiókkal](https://login.marketo.com/) és a megfelelő rendszergazdai hitelesítő adatokkal.</span><span class="sxs-lookup"><span data-stu-id="13c82-106">You have a [Marketo account](https://login.marketo.com/) and corresponding administrator credentials.</span></span>
-   <span data-ttu-id="13c82-107">A Marketóban és a megfelelő azonosítókban meglévő listák találhatók.</span><span class="sxs-lookup"><span data-stu-id="13c82-107">There are existing lists in Marketo and the corresponding IDs.</span></span> <span data-ttu-id="13c82-108">További tájékoztatásért keresse fel a [Marketo listák](https://docs.marketo.com/display/public/DOCS/Understanding+Static+Lists) webhelyet.</span><span class="sxs-lookup"><span data-stu-id="13c82-108">For more information, see [Marketo lists](https://docs.marketo.com/display/public/DOCS/Understanding+Static+Lists).</span></span>
-   <span data-ttu-id="13c82-109">Rendelkezik [konfigurált szegmensekkel](segments.md).</span><span class="sxs-lookup"><span data-stu-id="13c82-109">You have [configured segments](segments.md).</span></span>
-   <span data-ttu-id="13c82-110">Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.</span><span class="sxs-lookup"><span data-stu-id="13c82-110">Unified customer profiles in the exported segments contain a field representing an email address.</span></span>

## <a name="connect-to-marketo"></a><span data-ttu-id="13c82-111">Csatlakozás a Marketóhoz</span><span class="sxs-lookup"><span data-stu-id="13c82-111">Connect to Marketo</span></span>

1. <span data-ttu-id="13c82-112">Válassz a **Rendszergazda** > **Célok exportálása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="13c82-112">Go to **Admin** > **Export destinations**.</span></span>

1. <span data-ttu-id="13c82-113">A **Marketo** részben válassza a **Beállítás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="13c82-113">Under **Marketo**, select **Set up**.</span></span>

1. <span data-ttu-id="13c82-114">Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben az export helyének.</span><span class="sxs-lookup"><span data-stu-id="13c82-114">Give your export destination a recognizable name in the **Display name** field.</span></span>

1. <span data-ttu-id="13c82-115">Adja meg a **[Marketo ügyfél-azonosítót, titkos ügyfélkódot és REST végpont eszköznevét](https://developers.marketo.com/rest-api/authentication/)**.</span><span class="sxs-lookup"><span data-stu-id="13c82-115">Enter your **[Marketo client ID, Client secret and REST Endpoint Hostname](https://developers.marketo.com/rest-api/authentication/)**.</span></span>

1. <span data-ttu-id="13c82-116">Adja meg a **[Marketo-lista azonosítóját](https://docs.marketo.com/display/public/DOCS/Understanding+Static+Lists)**</span><span class="sxs-lookup"><span data-stu-id="13c82-116">Enter your **[Marketo list ID](https://docs.marketo.com/display/public/DOCS/Understanding+Static+Lists)**</span></span> 

1. <span data-ttu-id="13c82-117">Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez, majd válassza a **Csatlakozás** lehetőséget a Marketo kapcsolat inicializálásához.</span><span class="sxs-lookup"><span data-stu-id="13c82-117">Select **I agree** to confirm the **Data privacy and compliance** and select **Connect** to initialize the connection to Marketo.</span></span>

1. <span data-ttu-id="13c82-118">Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.</span><span class="sxs-lookup"><span data-stu-id="13c82-118">Select **Add yourself as export user** and provide your Customer Insights credentials.</span></span>

   :::image type="content" source="media/export-connect-marketo.png" alt-text="Képernyőkép exportálása a Marketo kapcsolatához":::

1. <span data-ttu-id="13c82-120">Az Exportálás konfigurálásához válassza a **Tovább** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="13c82-120">Select **Next** to configure the export.</span></span>

## <a name="configure-the-connector"></a><span data-ttu-id="13c82-121">Konfigurálja az összekötőt</span><span class="sxs-lookup"><span data-stu-id="13c82-121">Configure the connector</span></span>

1. <span data-ttu-id="13c82-122">Az **Adategyeztetés** szakaszban az **E-mail** mezőben jelölje ki az egyesített ügyfélprofil ügyfél e-mail-címét jelképező mezőjét.</span><span class="sxs-lookup"><span data-stu-id="13c82-122">In the **Data matching** section, in the **Email** field, select the field in your unified customer profile that represents a customer's email address.</span></span> 

1. <span data-ttu-id="13c82-123">Alternatív lehetőségként exportálhatja az **Utónév**, **Vezetéknév**, **Város**, **Állam** és **Ország/régió** mezőket további mezőként személyre szabottabb e-mailek létrehozásához.</span><span class="sxs-lookup"><span data-stu-id="13c82-123">Optionally, you can export **First name**, **Last name**, **City**, **State**, and **Country/Region**  as additional fields to create more personalized emails.</span></span> <span data-ttu-id="13c82-124">Válassza az **Attribútum hozzáadása** lehetőséget a mezők leképezéséhez.</span><span class="sxs-lookup"><span data-stu-id="13c82-124">Select **Add attribute** to map these fields.</span></span>

1. <span data-ttu-id="13c82-125">Jelölje ki a szegmenseket, amelyeket exportálni szeretne.</span><span class="sxs-lookup"><span data-stu-id="13c82-125">Select the segments you want to export.</span></span> <span data-ttu-id="13c82-126">Összesen legfeljebb 1 000 000 ügyfélprofilt exportálhat a Marketóba.</span><span class="sxs-lookup"><span data-stu-id="13c82-126">You can export up to 1 million customer profiles in total to Marketo.</span></span>

   :::image type="content" source="media/export-segment-marketo.png" alt-text="Marketóba exportálandó mezők és szegmensek kijelölése":::

1. <span data-ttu-id="13c82-128">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="13c82-128">Select **Save**.</span></span>

## <a name="export-the-data"></a><span data-ttu-id="13c82-129">Az adatok exportálása</span><span class="sxs-lookup"><span data-stu-id="13c82-129">Export the data</span></span>

<span data-ttu-id="13c82-130">[Igény szerint exportálhatja az adatot](export-destinations.md).</span><span class="sxs-lookup"><span data-stu-id="13c82-130">You can [export data on demand](export-destinations.md).</span></span> <span data-ttu-id="13c82-131">Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) együtt is lefut.</span><span class="sxs-lookup"><span data-stu-id="13c82-131">The export will also run with every [scheduled refresh](system.md#schedule-tab).</span></span> <span data-ttu-id="13c82-132">A Marketóban most már megtalálhatja a szegmenseket a [Marketo listában](ttps://docs.marketo.com/display/public/DOCS/Understanding+Static+Lists).</span><span class="sxs-lookup"><span data-stu-id="13c82-132">In Marketo, you can now find your segments under [Marketo lists](ttps://docs.marketo.com/display/public/DOCS/Understanding+Static+Lists).</span></span>

## <a name="known-limitations"></a><span data-ttu-id="13c82-133">Ismert korlátozások</span><span class="sxs-lookup"><span data-stu-id="13c82-133">Known limitations</span></span>

- <span data-ttu-id="13c82-134">Legfeljebb 1 000 000 profilt exportálhat egyszerre a Marketoba.</span><span class="sxs-lookup"><span data-stu-id="13c82-134">Up to 1 million profiles per export to Marketo.</span></span>
- <span data-ttu-id="13c82-135">A Marketoba való exportálás csak szegmensekre korlátozódik.</span><span class="sxs-lookup"><span data-stu-id="13c82-135">Exporting to Marketo is limited to segments.</span></span>
- <span data-ttu-id="13c82-136">Az összesen 1 000 000 profillal rendelkező szegmensek exportálása akár 3 óráig is eltarthat.</span><span class="sxs-lookup"><span data-stu-id="13c82-136">Exporting segments with a total of 1 million profiles can take up to 3 hours.</span></span> 
- <span data-ttu-id="13c82-137">A Marketoba exportálható profilok száma függ a Marketo szerződésről, és korlátozott.</span><span class="sxs-lookup"><span data-stu-id="13c82-137">The number of profiles that you can export to Marketo is dependent and limited on your contract with Marketo.</span></span>

## <a name="data-privacy-and-compliance"></a><span data-ttu-id="13c82-138">Adatvédelem és megfelelőség</span><span class="sxs-lookup"><span data-stu-id="13c82-138">Data privacy and compliance</span></span>

<span data-ttu-id="13c82-139">Amikor engedélyezi az Dynamics 365 Customer Insights szolgáltatást az adatok Marketoba való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat.</span><span class="sxs-lookup"><span data-stu-id="13c82-139">When you enable Dynamics 365 Customer Insights to transmit data to Marketo, you allow transfer of data outside of the compliance boundary for Dynamics 365 Customer Insights, including potentially sensitive data such as Personal Data.</span></span> <span data-ttu-id="13c82-140">A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy az Marketo megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek.</span><span class="sxs-lookup"><span data-stu-id="13c82-140">Microsoft will transfer such data at your instruction, but you are responsible for ensuring that Marketo meets any privacy or security obligations you may have.</span></span> <span data-ttu-id="13c82-141">További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).</span><span class="sxs-lookup"><span data-stu-id="13c82-141">For more information, see [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?linkid=396732).</span></span>
<span data-ttu-id="13c82-142">A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.</span><span class="sxs-lookup"><span data-stu-id="13c82-142">Your Dynamics 365 Customer Insights Administrator can remove this export destination at any time to discontinue use of this functionality.</span></span>
