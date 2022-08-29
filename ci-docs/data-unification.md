---
title: Ügyfelek egységes nézetének létrehozása
description: Az adatok egyesítésének folyamatán keresztül az adatokkal egyetlen fő adatkészletet hozhat létre a fiók- vagy ügyfélprofilokról.
ms.date: 08/12/2022
ms.reviewer: v-wendysmith
ms.subservice: audience-insights
ms.topic: overview
author: Scott-Stabbert
ms.author: sstabbert
manager: shellyha
searchScope:
- ci-map
- customerInsights
ms.openlocfilehash: c2a81776eab147c4b5209a6fbf89c0f4c9853d1d
ms.sourcegitcommit: 267c317e10166146c9ac2c30560c479c9a005845
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/16/2022
ms.locfileid: "9304430"
---
# <a name="data-unification-overview"></a>Az Adategyesítés áttekintése

[Az adatforrások beállítása után](data-sources.md) egyesítheti az adatot. Az adatok egyesítése lehetővé teszi az egykor eltérő adatforrások egyesítését egyetlen fő adatkészletben, amely egységes nézetet biztosít az adatokról.

Az egyéni fogyasztók (B-től C-ig), ahol az adatok egyének köré összpontosulnak, az egyesítés egységes képet nyújt az ügyfelekről. Az üzleti fiókok (B-től B-ig) esetében, ahol az adatok a fiókok köré összpontosulnak, az egyesítés egységes nézetet biztosít a fiókokról. [A kapcsolategyesítés (előzetes verzió)](data-unification-contacts.md) lehetővé teszi, hogy a partnerek kapcsolattartói külön-külön egységesek legyenek, és a fiókokhoz legyenek társítva.

Az adatok egyesíthetők egyetlen entitáson vagy több entitáson.

# <a name="individual-consumers-b-to-c"></a>[Egyéni fogyasztók (B-to-C)](#tab/b2c)

Az egyesítési folyamat leképezi az ügyféladatokat az adatforrásokból, eltávolítja az ismétlődéseket, egyezteti az adatokat az entitások között, és egységes profilt hoz létre. Az egyesítés a következő sorrendben történik:

1. [Forrásmezők](map-entities.md) (korábbi nevén Térkép): A forrásmezők lépésében válassza ki az egyesítési folyamatba felvenni kívánt entitásokat és mezőket. Mezőket képezzen le egy gyakori szemantikai típusra, amely leírja a mező célját.

1. [Ismétlődő rekordok](remove-duplicates.md) (korábban a Match része): Az ismétlődő rekordok lépésben opcionálisan definiálhat szabályokat az ismétlődő ügyfélrekordok eltávolításához az egyes entitásokon belül.

1. [Egyező feltételek](match-entities.md) (korábbi nevén Egyeztetés): Az egyező feltételek lépésben határozzon meg olyan szabályokat, amelyek megfelelnek az entitások ügyfélrekordjainak. Ha egy vevő két vagy több entitásban található, egyetlen konszolidált rekord jön létre az egyes entitások összes oszlopával és adatával.

1. [Egyesített vevőmezők](merge-entities.md) (korábbi nevén Egyesítés): Az egyesített vevőmezők lépésben határozza meg, hogy mely forrásmezőket kell belefoglalni, kizárni vagy egyesíteni egy egységes ügyfélprofilba.  

1. [Tekintse át](review-unification.md) és hozza létre az egyesített profilt.

# <a name="business-accounts-b-to-b"></a>[Üzleti számlák (B-to-B)](#tab/b2b)

Az egyesítési folyamat leképezi a fiókadatokat az adatforrásokból, eltávolítja az ismétlődéseket, egyezteti az adatokat az entitások között, és egységes profilt hoz létre. Az egyesítés a következő sorrendben történik:

1. [Forrásmezők](map-entities.md) (korábbi nevén Térkép): A forrásmezők lépésében válassza ki az egyesítő fiókfolyamatba felvenni kívánt entitásokat és mezőket. Mezőket képezzen le egy gyakori szemantikai típusra, amely leírja a mező célját.

1. [Ismétlődő rekordok](remove-duplicates.md) (korábban az egyezés része): Az ismétlődő rekordok lépésben opcionálisan definiálhat szabályokat az ismétlődő fiókrekordok eltávolításához az egyes entitásokból.

1. [Egyezési feltételek](match-entities.md) (korábbi nevén Egyezés): Az egyező feltételek lépésben határozzon meg olyan szabályokat, amelyek megfelelnek az entitások közötti számlarekordoknak. Ha egy számla két vagy több entitásban található, egyetlen konszolidált rekord jön létre az egyes entitások összes oszlopával és adatával.

1. [Egyesített vevőmezők](merge-entities.md) (korábbi nevén Egyesítés): Az egyesített vevőmezők lépésben határozza meg, hogy mely forrásmezőket kell belefoglalni, kizárni vagy egyesíteni egy egységes ügyfélprofilba.  

1. [Tekintse át](review-unification.md) és hozza létre az egyesített profilt.

A fiókok egyesítése után opcionálisan [egyesítheti a névjegyeket (előzetes verzió)](data-unification-contacts.md) ezekhez a fiókokhoz, és összekapcsolhatja az egyesített kapcsolattartókat az egyesített fiókokkal.

---

Az adategyesítés befejezése után opcionálisan a következőket teheti:

- [Állítson be kapcsolatok az entitások](relationships.md) között kifinomult szegmensek létrehozásához.
- [Gazdagítsa adatait](enrichment-hub.md), hogy szélesebb körű betekintést nyerjen ügyfeleiről.
- [Határozza meg a tevékenységeket](activities.md) néhány betöltött attribútumból.
- [Hozzon létre intézkedéseket](measures.md) az ügyfelek viselkedésének és üzleti teljesítményének jobb megértéséhez.

[!INCLUDE [footer-include](includes/footer-banner.md)]
