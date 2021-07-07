---
title: Szegmensinformációk a meglevő szegmensekről
description: Szerezzen információkat a meglevő szegmensekről, hogy felfedezhesse a különbségeket és egyezéseket.
ms.date: 06/10/2020
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: JimsonChalissery
ms.author: jimsonc
ms.reviewer: mhart
manager: shellyha
ms.openlocfilehash: 2856888d6ac64d5daabcc5a234f13bc6f88bb3df
ms.sourcegitcommit: 0b754d194d765afef70d1008db7b347dd1f0ee40
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/24/2021
ms.locfileid: "6306077"
---
# <a name="segment-insights-preview"></a><span data-ttu-id="ad2da-103">Szegmensekkel kapcsolatosa információk (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="ad2da-103">Segment insights (preview)</span></span>

<span data-ttu-id="ad2da-104">Ismerje meg a meglévő szegmensekhez kapcsolódó további információkat és betekintést.</span><span class="sxs-lookup"><span data-stu-id="ad2da-104">Discover additional information and insights around your existing segments.</span></span> <span data-ttu-id="ad2da-105">Megtudhatja, hogy mi különbözteti meg a két szegmenst, illetve hogy mi a közös bennük.</span><span class="sxs-lookup"><span data-stu-id="ad2da-105">Find out what differentiates two segments or what they have in common.</span></span>

## <a name="segment-overlap"></a><span data-ttu-id="ad2da-106">Szegmensátfedés</span><span class="sxs-lookup"><span data-stu-id="ad2da-106">Segment overlap</span></span>

<span data-ttu-id="ad2da-107">A szegmensátfedés elemzése azt mutatja, hogy hány és mely ügyfelek közösen két vagy több szegmensben.</span><span class="sxs-lookup"><span data-stu-id="ad2da-107">Segment overlap analysis shows how many and which customers are common to two or more segments.</span></span> <span data-ttu-id="ad2da-108">Tegyük fel például, hogy a gyakori ügyfelek egy szegmense átfedésben van egy olyan szegmenssel, amely a szolgáltatásával vagy a termékkel elégedett ügyfeleket tartalmaz.</span><span class="sxs-lookup"><span data-stu-id="ad2da-108">For example, how a segment of frequent customers overlaps with a segment that contains customers that are satisfied with your service or product.</span></span>
<span data-ttu-id="ad2da-109">Elemezheti azt is, hogyan módosul az átfedés az egyes attribútumok esetében.</span><span class="sxs-lookup"><span data-stu-id="ad2da-109">You can also analyze how the overlap changes for specific attributes.</span></span>

### <a name="run-an-overlap-analysis"></a><span data-ttu-id="ad2da-110">Átfedéselemzés futtatása</span><span class="sxs-lookup"><span data-stu-id="ad2da-110">Run an overlap analysis</span></span>

1. <span data-ttu-id="ad2da-111">Nyissa meg a **Szegmenseket** menüt, és válassza a **Háttér-információk** (előzetes verzió) lapot.</span><span class="sxs-lookup"><span data-stu-id="ad2da-111">Go to **Segments** and select the **Insights (preview)** tab.</span></span>

1. <span data-ttu-id="ad2da-112">Válassza az **Új** lehetőséget, és válassza az **Átfedés** beállítást a **Háttér-információ típusának kiválasztása** ablaktáblában.</span><span class="sxs-lookup"><span data-stu-id="ad2da-112">Select **New** and choose the **Overlap** option in the **Choose Insight Type** pane.</span></span>

1. <span data-ttu-id="ad2da-113">Válassza ki az érdekes szegmenseket, és válassza a **Következő** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="ad2da-113">Choose the segments of interest and select **Next**.</span></span>

1. <span data-ttu-id="ad2da-114">Tetszés szerint kiválaszthat egy vagy több érdekes mezőt is, amelyekkel elemezheti a átfedéseket minden lehetséges mezőérték esetében, majd válassza a **Tovább** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="ad2da-114">Optionally, choose one or more fields of interest to analyze overlaps for every possible field value and select **Next**.</span></span>

1. <span data-ttu-id="ad2da-115">Adja meg az átfedéselemzés nevét, a választható megjelenítendő nevet és leírást.</span><span class="sxs-lookup"><span data-stu-id="ad2da-115">Provide a name for you overlap analysis, an optional display name, and a description.</span></span>

1. <span data-ttu-id="ad2da-116">Az elemzés megkezdéséhez válassza a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="ad2da-116">Select **Save** to start the analysis.</span></span> <span data-ttu-id="ad2da-117">Az átfedések elemzése elkészül, amikor az állapot a Frissítés értékről a Sikeres értékre változik.</span><span class="sxs-lookup"><span data-stu-id="ad2da-117">The overlap analysis is ready when the status changes from Refreshing to Successful.</span></span>

### <a name="view-and-optimize-an-overlap-analysis"></a><span data-ttu-id="ad2da-118">Átfedések elemzésének megtekintése és optimalizálása</span><span class="sxs-lookup"><span data-stu-id="ad2da-118">View and optimize an overlap analysis</span></span>

<span data-ttu-id="ad2da-119">Az elemzés befejezése után a háttér-információ részleteit a **Szegmensek** > **Háttér információk (előzetes verzió)** helyen találja.</span><span class="sxs-lookup"><span data-stu-id="ad2da-119">After completing the analysis, find details on this insight on **Segments** > **Insights (preview)**.</span></span>

> [!div class="mx-imgBorder"]
> :::image type="content" source="media/segment-overlap.png" alt-text="Szegmens átfedés háttér-információinak részletei":::

<span data-ttu-id="ad2da-121">Az elemzési eredmények megtekintéséhez válasszon ki egy betekintést:</span><span class="sxs-lookup"><span data-stu-id="ad2da-121">Select an insight to see the analysis results:</span></span>

- <span data-ttu-id="ad2da-122">Az elemzésre kiválasztott szegmensekben található átfedő tagok száma.</span><span class="sxs-lookup"><span data-stu-id="ad2da-122">The number of members overlapping the segments selected for analysis.</span></span>
- <span data-ttu-id="ad2da-123">A szegmensek egyikében, azonban a többiben nem szereplő tagok száma.</span><span class="sxs-lookup"><span data-stu-id="ad2da-123">The number of members included in one of the segments but not in the rest of the segments.</span></span>
- <span data-ttu-id="ad2da-124">Ha az átfedési elemzés konfigurálásakor kijelölt mezőket, a megfelelő lapokon találja azokat.</span><span class="sxs-lookup"><span data-stu-id="ad2da-124">If you selected fields while configuring the overlap analysis, you'll find them in the corresponding tabs.</span></span> <span data-ttu-id="ad2da-125">A legördülő szűrő segítségével bármilyen attribútum szintet kijelölhet, és az alsó táblázatban a megfelelő adatok fognak mutatni.</span><span class="sxs-lookup"><span data-stu-id="ad2da-125">You can use the filter dropdown to select any attribute level of interest and the table at the bottom will show the corresponding data.</span></span>

## <a name="segment-differentiators"></a><span data-ttu-id="ad2da-126">Szegmensmegkülönböztetők</span><span class="sxs-lookup"><span data-stu-id="ad2da-126">Segment differentiators</span></span>

<span data-ttu-id="ad2da-127">A szegmens-megkülönböztetők segítségével megtudhatja, hogy mi különbözteti meg a szegmenseket az ügyfelek többi részétől vagy egy másik szegmenstől.</span><span class="sxs-lookup"><span data-stu-id="ad2da-127">Segment differentiators help you find out what differentiates a segment from the rest of your customers or from another segment.</span></span> <span data-ttu-id="ad2da-128">Csak ki kell választania egy szegmenst, és a rendszer azonosítja a profilattribútumokat és mértékeket, amelyek megkülönböztetik a kijelölt szegmenst.</span><span class="sxs-lookup"><span data-stu-id="ad2da-128">You just have to select a segment and the system will identify profile attributes and measures that distinguish the selected segment.</span></span>

### <a name="run-a-differentiator-analysis"></a><span data-ttu-id="ad2da-129">Megkülönböztető elemzés futtatása</span><span class="sxs-lookup"><span data-stu-id="ad2da-129">Run a differentiator analysis</span></span>

1. <span data-ttu-id="ad2da-130">Nyissa meg a **Szegmenseket** menüt, és válassza a **Háttér-információk** (előzetes verzió) lapot.</span><span class="sxs-lookup"><span data-stu-id="ad2da-130">Go to **Segments** and select the **Insights (preview)** tab.</span></span>

1. <span data-ttu-id="ad2da-131">Válassza az **Új** lehetőséget, és válassza az **Átfedés** beállítást a **Háttér-információ típusának kiválasztása** ablaktáblában.</span><span class="sxs-lookup"><span data-stu-id="ad2da-131">Select **New** and choose the **Overlap** option in the **Choose Insight Type** pane.</span></span>

1. <span data-ttu-id="ad2da-132">Válassza ki azt a szegmenst, amelyet szeretne elemezni **Elsődleges szegmensnek**, majd válassza a **Tovább** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="ad2da-132">Choose the segment you want to analyze as **Primary segment** and select **Next**.</span></span>

1. <span data-ttu-id="ad2da-133">Válassza az **Összes ügyfél** vagy **Másodlagos szegmens** elemet az elsődleges szegmenssel való összehasonlításához, majd válassza a **Tovább** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="ad2da-133">Choose **All customers** or a **Secondary segment** to compare your primary segment with and select **Next**.</span></span>

1. <span data-ttu-id="ad2da-134">Tetszés szerint kiválaszthat egy vagy több érdekes mezőt is, amelyekkel az elemzést meghatározott attribútumokra összpontosíthatja, majd válassza a **Tovább** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="ad2da-134">Optionally, choose one or more fields of interest to focus the analysis on specific attributes and select **Next**.</span></span>

1. <span data-ttu-id="ad2da-135">Adja meg az átfedéselemzés nevét, a választható megjelenítendő nevet és leírást.</span><span class="sxs-lookup"><span data-stu-id="ad2da-135">Provide a name for you overlap analysis, an optional display name, and a description.</span></span>

1. <span data-ttu-id="ad2da-136">Az elemzés megkezdéséhez válassza a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="ad2da-136">Select **Save** to start the analysis.</span></span> <span data-ttu-id="ad2da-137">Az átfedések elemzése elkészül, amikor az állapot a Frissítés értékről a Sikeres értékre változik.</span><span class="sxs-lookup"><span data-stu-id="ad2da-137">The overlap analysis is ready when the status changes from Refreshing to Successful.</span></span>

### <a name="view-and-optimize-a-differentiators-analysis"></a><span data-ttu-id="ad2da-138">Megkülönböztető elemzés megtekintése és optimalizálása</span><span class="sxs-lookup"><span data-stu-id="ad2da-138">View and optimize a differentiators analysis</span></span>

<span data-ttu-id="ad2da-139">Az elemzés befejezése után a háttér-információ részleteit a **Szegmensek** > **Háttér információk (előzetes verzió)** helyen találja.</span><span class="sxs-lookup"><span data-stu-id="ad2da-139">After completing the analysis, find details on this insight on **Segments** > **Insights (preview)**.</span></span>

> [!div class="mx-imgBorder"]
> :::image type="content" source="media/segment-differentiators.png" alt-text="Szegmens megkülönböztető háttér-információinak részletei":::

<span data-ttu-id="ad2da-141">Az elemzési eredmények megtekintéséhez válasszon ki egy betekintést.</span><span class="sxs-lookup"><span data-stu-id="ad2da-141">Select an insight to see the analysis results.</span></span> <span data-ttu-id="ad2da-142">A megkülönböztető elemzés két lapból áll.</span><span class="sxs-lookup"><span data-stu-id="ad2da-142">A differentiator analysis includes two tabs.</span></span> <span data-ttu-id="ad2da-143">Az **Attribútumok** lap felsorolja a megkülönböztető tulajdonságokkal rendelkező profil attribútumokat.</span><span class="sxs-lookup"><span data-stu-id="ad2da-143">The **Attributes** tab lists profile attributes considered as differentiators.</span></span> <span data-ttu-id="ad2da-144">Az **Mértékek** lapon a megkülönböztető elemek szerepelnek.</span><span class="sxs-lookup"><span data-stu-id="ad2da-144">The **Measures** tab lists differentiators.</span></span> <span data-ttu-id="ad2da-145">Minden lap a következő adatokat tartalmazza:</span><span class="sxs-lookup"><span data-stu-id="ad2da-145">Each tab includes the following details:</span></span>

- <span data-ttu-id="ad2da-146">A megkülönböztetők rangsorolt listája, a különbségpontszám szerint rendezve.</span><span class="sxs-lookup"><span data-stu-id="ad2da-146">Ranked list of differentiators, sorted by difference score.</span></span>
- <span data-ttu-id="ad2da-147">Az egyes megkülönböztető elemek **Különbségi pontszáma**.</span><span class="sxs-lookup"><span data-stu-id="ad2da-147">The **Difference score** for each differentiator.</span></span> <span data-ttu-id="ad2da-148">A különbségi pontszám egy attribútum két szegmens közötti különbségének fokát jelenti.</span><span class="sxs-lookup"><span data-stu-id="ad2da-148">The difference score represents the degree of difference of an attribute between two segments.</span></span> <span data-ttu-id="ad2da-149">Minél nagyobb a különbség, annál több attribútum tér el a két szegmens között.</span><span class="sxs-lookup"><span data-stu-id="ad2da-149">The higher the difference score, the more the attributes differ between the two segments.</span></span> <span data-ttu-id="ad2da-150">Válassza ki a pontszám értékét, a **Különbségi pontszám** ablaktábla megnyitásához az attribútumra vonatkozó értékek eloszlásával.</span><span class="sxs-lookup"><span data-stu-id="ad2da-150">Select a score to open the **Difference score** pane with the distributions of values for that attribute.</span></span>

## <a name="manage-segment-insights"></a><span data-ttu-id="ad2da-151">Az Szegmensbetekintések kezelése</span><span class="sxs-lookup"><span data-stu-id="ad2da-151">Manage segment insights</span></span>

<span data-ttu-id="ad2da-152">A parancssorban a következő beállításokat használhatja a betekintésekhez:</span><span class="sxs-lookup"><span data-stu-id="ad2da-152">You can use the following options on your insights from the command bar:</span></span>

- <span data-ttu-id="ad2da-153">**Vissza** a visszatéréshez betekintések listájához</span><span class="sxs-lookup"><span data-stu-id="ad2da-153">**Back** to return the list of insights</span></span>
- <span data-ttu-id="ad2da-154">**Frissítés** az analízis ismételt futtatásához</span><span class="sxs-lookup"><span data-stu-id="ad2da-154">**Refresh** to run the analysis again</span></span>
- <span data-ttu-id="ad2da-155">**Törlés** a betekintés eltávolításához</span><span class="sxs-lookup"><span data-stu-id="ad2da-155">**Delete** to remove this insight</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]