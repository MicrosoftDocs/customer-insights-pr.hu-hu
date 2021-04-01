---
title: Adategyesítés
description: Megismerheti, hogyan egyesítheti a betöltött adatot.
ms.date: 04/16/2020
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: adkuppa
ms.author: adkuppa
manager: shellyha
ms.openlocfilehash: 73d8006c670268420f8cd6a2b37cb214ba1bbd6c
ms.sourcegitcommit: bae40184312ab27b95c140a044875c2daea37951
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/15/2021
ms.locfileid: "5597882"
---
# <a name="data-unification-overview"></a><span data-ttu-id="97b13-103">Az Adategyesítés áttekintése</span><span class="sxs-lookup"><span data-stu-id="97b13-103">Data unification overview</span></span>

<span data-ttu-id="97b13-104">[Az adatforrások beállítása után](data-sources.md) egyesítheti az adatot.</span><span class="sxs-lookup"><span data-stu-id="97b13-104">After [setting up the data sources](data-sources.md), you can unify the data.</span></span> <span data-ttu-id="97b13-105">Az Adategyesítés három lépésből áll: **Leképezés**, **Egyeztetés** és **Egyesítés**.</span><span class="sxs-lookup"><span data-stu-id="97b13-105">Data unification includes three steps: **Map**, **Match**, and **Merge**.</span></span>

<span data-ttu-id="97b13-106">Az adategyesítési folyamat lehetővé teszi, hogy egy-egy különálló adatforrást egyetlen fő adatkészletbe egyesítson, amely egységes képet ad az ügyfelekről.</span><span class="sxs-lookup"><span data-stu-id="97b13-106">The data unification process lets you unify once-disparate data sources into a single master dataset that provides a unified view of your customers.</span></span> <span data-ttu-id="97b13-107">Az egyesítési fázisok kötelezőek, és a következő sorrendben végezhetők el:</span><span class="sxs-lookup"><span data-stu-id="97b13-107">Unification stages are mandatory, and performed in the following order:</span></span>

1. [<span data-ttu-id="97b13-108">Leképezés</span><span class="sxs-lookup"><span data-stu-id="97b13-108">Map</span></span>](map-entities.md)
2. [<span data-ttu-id="97b13-109">Egyezés</span><span class="sxs-lookup"><span data-stu-id="97b13-109">Match</span></span>](match-entities.md)
3. [<span data-ttu-id="97b13-110">Összefésülés</span><span class="sxs-lookup"><span data-stu-id="97b13-110">Merge</span></span>](merge-entities.md)

<span data-ttu-id="97b13-111">Az adatok egyesítésének befejezése után tetszés szerint</span><span class="sxs-lookup"><span data-stu-id="97b13-111">After completing the data unification, you can optionally</span></span>

- <span data-ttu-id="97b13-112">[beállíthat az entitások közötti kapcsolatokat](relationships.md) kifinomult szegmensek létrehozásához</span><span class="sxs-lookup"><span data-stu-id="97b13-112">[set up relationships between entities](relationships.md) to create sophisticated segments</span></span>
- <span data-ttu-id="97b13-113">[bővítheti adatait](enrichment-hub.md), hogy szélesebb körű betekintést tudjon kapni az ügyfelekről</span><span class="sxs-lookup"><span data-stu-id="97b13-113">[enrich your data](enrichment-hub.md) to get a wider range of insights about your customers</span></span>
- <span data-ttu-id="97b13-114">[tevékenységeket definiálhat](activities.md) néhány betöltött attribútumból</span><span class="sxs-lookup"><span data-stu-id="97b13-114">[define activities](activities.md) from some of the ingested attributes</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]