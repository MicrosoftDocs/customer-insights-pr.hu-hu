---
title: Üzleti partnerek használata
description: További információ az üzleti fiókokról, mint elsődleges célként célközönség a Dynamics 365 Customer Insights.
ms.date: 10/19/2021
ms.subservice: audience-insights
ms.topic: conceptual
author: v-wendysmith
ms.custom: intro-internal
ms.author: wimohabb
ms.reviewer: v-wendysmith
manager: shellyha
searchScope:
- ci-semantic-mapping
- ci-connections
- customerInsights
ms.openlocfilehash: abb77a720ab737520a905b0c93b65573e669109f
ms.sourcegitcommit: 267c317e10166146c9ac2c30560c479c9a005845
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/16/2022
ms.locfileid: "9303919"
---
# <a name="work-with-business-accounts"></a>Üzleti partnerek használata

Lehetővé Dynamics 365 Customer Insights teszi a környezet konfigurálását különböző elsődleges célközönségekhez: egyéni fogyasztókhoz (B-től C-ig) és üzleti fiókokhoz (B-től B-ig). A B-to-C helyzetekben az adatok egyének köré központosulnak. A B-to-B esetekben az elsődleges célközönség a partnerek – szervezetek vagy cégek – és a kapcsolattartók. Ez a cikk segít a kötrnyezettel rendelkező üzleti partnereknek az első lépésekben. Felsorolja a Customer Insights funkcióterületeinek különbségeit, a környezetre összpontosítva. Ha többet szeretne megtudni a különbségekről, tekintse át a funkcióterületek dokumentációját. 

## <a name="create-an-environment-for-business-accounts"></a>Hozzon létre környezetet az üzleti fiókokhoz

A rendszergazdák [létrehozhatnak egy környezetet egy meglévő szervezetben](create-environment.md). Az új környezet létrehozásának folyamatának egyik lépése a rendszergazdákat kéri a környezet elsődleges célközönségétől. Abban az esetben, ha ez a kezdeti beállítás a licenc megvásárlása után, az irányított élmény segít az első környezet létrehozásában.

Ezután az összes támogatott forrás adatforrásaként [adatokat tölthet be](data-sources.md) az üzleti fiókokhoz és a kapcsolódó névjegyekhez.

 [Egyesítse](data-unification.md) fiókadatait, majd kapcsolattartási adatait a kapcsolattartó és a fiók entitások összekapcsolásához.

## <a name="switch-between-primary-target-audience"></a>Váltás az elsődleges célközönségek között

Ha a szervezet egyéni ügyfelek és üzleti partnerek számára tart fenn környezeteket, a bal oldali ablaktáblában váltógomb segítségével kiválaszthatja az elsődleges célközönséget.

:::image type="content" source="media/switch-primary-target-audience.png" alt-text="Váltógomb az elsődleges célközönség ügyfelek és üzleti partnerek közötti váltásra.":::

## <a name="supported-feature-areas"></a>Támogatott funkcióterületek

- [Tevékenységek](activities.md): Partnerek és kapcsolódó kapcsolattartók támogatása tevékenységek létrehozására és idővonalon való megjelenítése érdekében.
- [Kapcsolatok](relationships.md): A Tevékenységvarázsló segít kapcsolatok létrehozásában az entitások között, így a fióknézetben a kapcsolatok összes tevékenysége megjeleníthető. A kapcsolattartók részletezve megtekinthetik a kapcsolattartók nézetét, és a partnerek tevékenység összesítéséhez hierarchiák használhatók.
- [Mértékegységek](measures.md): A mérőkészítőből létrehozott intézkedéseket támogatja egyetlen számítással. Egy nem kötelező beállítás lehetővé teszi az alfiókok összesítését az egyes beállítások létrehozásakor.
- [Szegmensek](segments.md): A szegmensszerkesztővel nulláról létrehozott szegmenseket támogat. A szegmensek fiókokon vagy kapcsolattartókon alapulhatnak.
- [Adatok beállítása](data-sources.md): Az ezen a területen található összes funkció azonos az üzleti partnerek és az egyéni ügyfelek esetében.
- A B-to-B adategyesítés nagyon hasonlít a B-C adategyesítéshez, de további lépéssel rendelkezik a kapcsolattartók egyesítésére a fiókegyesítés után. Lásd: [Üzleti fiókok (B-től B-ig)](data-unification.md).
- [Gyarapítás](enrichment-hub.md): Egyes gyarapítási típusok csak az egyes ügyfélhelyzetek esetén érhetők el, míg mások kizárólag üzleti partnerek számára.
- [Előrejelzések és használható modellek](predictions-overview.md): A tranzakciós lemorzsolódási előrejelzés üzleti partnerekre vonatkozó további lépéseket tartalmaz. Egyéb előrejelzések csak az egyes ügyfelek számára érhetők el.
- [Aktiválás és exportálás](export-destinations.md): Az exportálás üzleti partnerek és egyéni ügyfelek számára érhető el. Egyes exportálások esetén az adott szegmensben kivetített további konfigurálási és kapcsolattartási adatok érvényesek az üzleti partnerekre.
- [Rendszerbeállítások](system.md) és [felhasználókezelés](permissions.md): Az ezen a területen található összes funkció azonos az üzleti partnerek és az egyéni ügyfelek esetében.

[!INCLUDE [footer-include](includes/footer-banner.md)]
