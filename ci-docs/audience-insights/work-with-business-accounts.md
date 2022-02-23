---
title: Első lépések az üzleti partnerek beállítása elsődleges célközönségként szolgáltatással
description: További információ az üzleti partnerek beállítása elsődleges célközönségként Dynamics 365 Customer Insights szolgáltatásról.
ms.date: 10/19/2021
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.custom: intro-internal
ms.author: wimohabb
ms.reviewer: mhart
manager: shellyha
ms.openlocfilehash: fb943a91154e913c85c40fbf6077c171e9240ac5
ms.sourcegitcommit: bb1ca84bc38e81fb2ff2961c457384b7beb5b5fa
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 01/15/2022
ms.locfileid: "7977924"
---
# <a name="work-with-business-accounts-in-audience-insights"></a>Üzleti fiókokkal való munka a célközönséggel kapcsolatos információkban

A Dynamics 365 Customer Insights célközönséggel kapcsolatos információi lehetővé teszik a különböző elsődleges célközönségek – egyéni ügyfelek (B-to-C) és üzleti partnerek (B-to-B) – környezetének beállítását. A B-to-C helyzetekben az adatok egyének köré központosulnak. A B-to-B esetekben az elsődleges célközönség a partnerek – szervezetek vagy cégek – és a kapcsolattartók. Ez a cikk segít a kötrnyezettel rendelkező üzleti partnereknek az első lépésekben. A környezeti fókusztól függően felsorolja a közönségstatisztika jellemzői közötti különbségeket. Ha többet szeretne megtudni a különbségekről, tekintse át a funkcióterületek dokumentációját. 

## <a name="create-an-environment-for-business-accounts"></a>Hozzon létre környezetet az üzleti fiókokhoz

A rendszergazdák [létrehozhatnak egy környezetet egy meglévő szervezetben](create-environment.md). Az új környezet létrehozásának folyamatának egyik lépése a rendszergazdákat kéri a környezet elsődleges célközönségétől. Abban az esetben, ha ez a célközönség első beállítása a licenc megvásárlása után, az interaktív élmény segít az első környezet létrehozásában.

Ezután az összes támogatott forrás adatforrásaként [adatokat tölthet be](data-sources.md) az üzleti fiókokhoz és a kapcsolódó névjegyekhez.

Az adatok egyesítése után [adja meg a fiókhierarchiákat](relationships.md#set-up-account-hierarchies) a kapcsolatkonfiguráció részeként. A [szemantikai leképezéseket úgy is konfigurálhatja](semantic-mappings.md), hogy összekapcsolja a névjegyeket és a partnerentitásokat. 

## <a name="switch-between-primary-target-audience"></a>Váltás az elsődleges célközönségek között

Ha a szervezet egyéni ügyfelek és üzleti partnerek számára tart fenn környezeteket, a bal oldali ablaktáblában váltógomb segítségével kiválaszthatja az elsődleges célközönséget.

:::image type="content" source="media/switch-primary-target-audience.png" alt-text="Váltógomb az elsődleges célközönség ügyfelek és üzleti partnerek közötti váltásra.":::

## <a name="supported-feature-areas"></a>Támogatott funkcióterületek

- [Tevékenységek](activities.md): Partnerek és kapcsolódó kapcsolattartók támogatása tevékenységek létrehozására és idővonalon való megjelenítése érdekében.
- [Kapcsolatok](relationships.md): A Tevékenységvarázsló segít kapcsolatok létrehozásában az entitások között, így a fióknézetben a kapcsolatok összes tevékenysége megjeleníthető. A kapcsolattartók részletezve megtekinthetik a kapcsolattartók nézetét, és a partnerek tevékenység összesítéséhez hierarchiák használhatók.
- [Mértékegységek](measures.md): A mérőkészítőből létrehozott intézkedéseket támogatja egyetlen számítással. Egy nem kötelező beállítás lehetővé teszi az alfiókok összesítését az egyes beállítások létrehozásakor.
- [Szegmensek](segments.md): A szegmensszerkesztővel nulláról létrehozott szegmenseket támogat. Az új operátorok lehetővé teszik a fiókhierarchia kiépítését a szegmensek kiépítésekor.
- [Adatok beállítása](data-sources.md): Az ezen a területen található összes funkció azonos az üzleti partnerek és az egyéni ügyfelek esetében.
- [Adatok egyesítése](data-unification.md): Az ezen a területen található összes funkció azonos az üzleti partnerek és az egyéni ügyfelek esetében.
- [Gyarapítás](enrichment-hub.md): Egyes gyarapítási típusok csak az egyes ügyfélhelyzetek esetén érhetők el, míg mások kizárólag üzleti partnerek számára.
- [Előrejelzések és használható modellek](predictions-overview.md): A tranzakciós lemorzsolódási előrejelzés üzleti partnerekre vonatkozó további lépéseket tartalmaz. Egyéb előrejelzések csak az egyes ügyfelek számára érhetők el.
- [Aktiválás és exportálás](export-destinations.md): Az exportálás üzleti partnerek és egyéni ügyfelek számára érhető el. Egyes exportálások esetén az adott szegmensben kivetített további konfigurálási és kapcsolattartási adatok érvényesek az üzleti partnerekre.
- [Rendszerbeállítások](system.md) és [felhasználókezelés](permissions.md): Az ezen a területen található összes funkció azonos az üzleti partnerek és az egyéni ügyfelek esetében.

