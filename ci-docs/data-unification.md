---
title: Ügyfelek egységes nézetének létrehozása
description: Az adatok egyesítésének folyamatán keresztül az adatokkal egyetlen adathalmazt hozhat létre az egységes ügyfélprofilokból.
ms.date: 05/10/2022
ms.reviewer: v-wendysmith
ms.subservice: audience-insights
ms.topic: overview
author: v-wendysmith
ms.author: mukeshpo
manager: shellyha
searchScope:
- ci-map
- customerInsights
ms.openlocfilehash: bb8da6f4b9f92f2b265ff9807e04638edae4f814
ms.sourcegitcommit: 4ae316c856b8de0f08a4605f73e75a8c2cf51c4e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2022
ms.locfileid: "8755737"
---
# <a name="data-unification-overview"></a>Az Adategyesítés áttekintése

[!INCLUDE [m3-prod-trial-note](includes/m3-prod-trial-note.md)]

[Az adatforrások beállítása után](data-sources.md) egyesítheti az adatot. Az adategyesítés lehetővé teszi az egyszer eltérő adatforrások egyetlen fő adatkészletbe történő egyesítését, amely egységes nézetet biztosít az adott adatokról. Az egyes fogyasztók (B-to-C) esetében, ahol az adatok egyének köré összpontosulnak, az egyesítés egységes képet nyújt az ügyfelekről. Azoknál az üzleti fiókoknál (B-től B-ig), ahol az adatok a fiókok köré összpontosulnak, az egyesítés egységes nézetet biztosít a fiókokról.

Az adatok egyetlen entitáson vagy több entitáson egyesíthetők. Az egyesítés a következő sorrendben történik:

1. [Forrásmezők](map-entities.md) (korábban Leképezésnek nevezték): A forrásmezők lépésében válassza ki az egyesítési folyamatba bevonandó entitásokat és mezőket. Mezők leképezése a mező célját leíró közös szemantikai típusra.

1. [Ismétlődő rekordok](remove-duplicates.md) (korábban a Match része): Az ismétlődő rekordok lépésben tetszés szerint definiáljon szabályokat az ismétlődő ügyfélrekordok eltávolítására az egyes entitásokból.

1. [Feltételek egyeztetése](match-entities.md) (korábban Egyezés): Az egyeztetési feltételek lépésben definiáljon olyan szabályokat, amelyek megfelelnek az entitások közötti ügyfélrekordoknak. Ha egy vevő két vagy több entitásban található, egyetlen konszolidált rekord jön létre az egyes entitások összes oszlopával és adatával.

1. [Egyesített vevőmezők](merge-entities.md) (korábbi nevén Egyesítés): Az egyesített vevőmezők lépésben határozza meg, hogy mely forrásmezőket kell belefoglalni, kizárni vagy egyesítette egy egységes vevőprofilba.  

1. [Tekintse át](review-unification.md) és hozza létre az egységes profilt.

Az adategyesítés befejezése után opcionálisan:

- [Állítsa be kapcsolatok entitások](relationships.md) között kifinomult szegmensek létrehozásához.
- [Gazdagítsa adatait](enrichment-hub.md), hogy szélesebb körű betekintést kapjon ügyfeleiről.
- [A betöltött attribútumok némelyikének tevékenységeinek](activities.md) meghatározása.
- [Hozzon létre intézkedéseket](measures.md) az ügyfelek viselkedésének és üzleti teljesítményének jobb megértése érdekében.

[!INCLUDE [footer-include](includes/footer-banner.md)]
