---
title: Adategyesítés
description: Megismerheti, hogyan egyesítheti a betöltött adatot.
ms.date: 04/16/2020
ms.reviewer: adkuppa
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: 24321e9e11f9fd4e800526673726e5146ed33674
ms.sourcegitcommit: cf9b78559ca189d4c2086a66c879098d56c0377a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/03/2020
ms.locfileid: "4405986"
---
# <a name="data-unification"></a>Adategyesítés

[Az adatforrások beállítása után](data-sources.md) egyesítheti az adatot. Az Adategyesítés három lépésből áll: **Leképezés**, **Egyeztetés** és **Egyesítés**.

Az adategyesítési folyamat lehetővé teszi, hogy egy-egy különálló adatforrást egyetlen fő adatkészletbe egyesítson, amely egységes képet ad az ügyfelekről. Az egyesítési fázisok kötelezőek, és a következő sorrendben végezhetők el:

1. [Leképezés](map-entities.md)
2. [Egyezés](match-entities.md)
3. [Összefésülés](merge-entities.md)

Az adatok egyesítésének befejezése után tetszés szerint

- [beállíthat az entitások közötti kapcsolatokat](relationships.md) kifinomult szegmensek létrehozásához
- [bővítheti adatait](enrichment-hub.md), hogy szélesebb körű betekintést tudjon kapni az ügyfelekről
- [tevékenységeket definiálhat](activities.md) néhány betöltött attribútumból
