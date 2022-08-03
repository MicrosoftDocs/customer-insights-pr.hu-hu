---
title: Az Adategyesítés áttekintése
description: Az adatok egyesítésének folyamatán keresztül az adatokkal egyetlen, egységes ügyfélprofilokból álló adatkészletet hozhat létre.
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
ms.openlocfilehash: 766e688cb80c50a0d620943f87b76eb84a2fb89a
ms.sourcegitcommit: 3c5b0b40b2b45e420015bbdd228ce0e610245e6f
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/12/2022
ms.locfileid: "9139496"
---
# <a name="data-unification-overview"></a>Az Adategyesítés áttekintése

[Az adatforrások beállítása után](data-sources.md) egyesítheti az adatot. Az adatok egyesítése lehetővé teszi az egykor eltérő adatforrások egyesítését egyetlen fő adatkészletben, amely egységes nézetet biztosít az adatokról. Az egyéni fogyasztók (B-től C-ig), ahol az adatok egyének köré összpontosulnak, az egyesítés egységes képet nyújt az ügyfelekről. Az üzleti fiókok (B-től B-ig) esetében, ahol az adatok a fiókok köré összpontosulnak, az egyesítés egységes nézetet biztosít a fiókokról.

Az adatok egyesíthetők egyetlen entitáson vagy több entitáson. Az egyesítés a következő sorrendben történik:

1. [Forrásmezők](map-entities.md) (korábbi nevén Térkép): A forrásmezők lépésében válassza ki az egyesítési folyamatba felvenni kívánt entitásokat és mezőket. Mezőket képezzen le egy gyakori szemantikai típusra, amely leírja a mező célját.

1. [Ismétlődő rekordok](remove-duplicates.md) (korábban a Match része): Az ismétlődő rekordok lépésben opcionálisan definiálhat szabályokat az ismétlődő ügyfélrekordok eltávolításához az egyes entitásokon belül.

1. [Egyező feltételek](match-entities.md) (korábbi nevén Egyeztetés): Az egyező feltételek lépésben határozzon meg olyan szabályokat, amelyek megfelelnek az entitások ügyfélrekordjainak. Ha egy vevő két vagy több entitásban található, egyetlen konszolidált rekord jön létre az egyes entitások összes oszlopával és adatával.

1. [Egyesített vevőmezők](merge-entities.md) (korábbi nevén Egyesítés): Az egyesített vevőmezők lépésben határozza meg, hogy mely forrásmezőket kell belefoglalni, kizárni vagy egyesíteni egy egységes ügyfélprofilba.  

1. [Tekintse át](review-unification.md) és hozza létre az egyesített profilt.

Az adategyesítés befejezése után igény szerint a következőket teheti:

- [Állítson be kapcsolatok az entitások](relationships.md) között kifinomult szegmensek létrehozásához.
- [Gazdagítsa adatait](enrichment-hub.md), hogy szélesebb körű betekintést nyerjen ügyfeleiről.
- [Határozza meg a tevékenységeket](activities.md) néhány betöltött attribútumból.
- [Hozzon létre intézkedéseket](measures.md) az ügyfelek viselkedésének és üzleti teljesítményének jobb megértéséhez.

[!INCLUDE [footer-include](includes/footer-banner.md)]
