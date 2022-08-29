---
title: Forrásmezők kiválasztása az adatok egyesítéséhez
description: Az egyesítési folyamat első lépése az entitások, attribútumok, elsődleges kulcsok és szemantikai típusok kiválasztása az adatok egységes ügyfélprofilra való leképezéséhez.
recommendations: false
ms.date: 08/12/2022
ms.subservice: audience-insights
ms.topic: tutorial
author: v-wendysmith
ms.author: mukeshpo
ms.reviewer: v-wendysmith
manager: shellyha
searchScope:
- ci-map
- ci-match
- customerInsights
ms.openlocfilehash: bc120aa7a3713e1184ff278edf0942925faafa12
ms.sourcegitcommit: 267c317e10166146c9ac2c30560c479c9a005845
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/16/2022
ms.locfileid: "9304568"
---
# <a name="select-source-fields-for-data-unification"></a>Forrásmezők kiválasztása az adatok egyesítéséhez

Az egyesítés első lépése az adatkészleteken belüli olyan entitások és mezők kiválasztása, amelyeket egyesíteni szeretne. Válasszon olyan entitásokat, amelyek ügyféllel kapcsolatos adatokat tartalmaznak, például nevet, címet, telefonszámot és e-mailt. Kiválaszthat egy vagy több entitást.

[!INCLUDE [m3-first-run-note](includes/m3-first-run-note.md)]

## <a name="select-entities-and-fields"></a>Entitások és mezők kiválasztása

1. Lépjen az Adatok **egyesítése oldalra** > **·**.

   Az egyes ügyfelek (B-től C-ig) esetében az Egyesítés céloldalon az **Első lépések** a **Forrás mezőket jeleníti** meg.**·**

   :::image type="content" source="media/m3_unify_land.png" alt-text="Képernyőkép az egyesítendő céloldal egységesítéséről az egyes ügyfelek első futtatási élményéhez.":::

   Üzleti fiókok (B-től B-ig) esetén az Egyesítés céloldalon megjelenik az **Egyesítő fiókok**, **amelyeken az Első lépések** a **Forrás mezők** első lépésnél látható **.** A **Névjegyek egyesítése (előzetes verzió)** lépések nem kötelezőek, és a fiókegyesítés befejezéséig várnak.

   :::image type="content" source="media/b2b_unify_land.png" alt-text="Képernyőkép az üzleti fiókok első futtatási élményének egyesítése céloldaláról.":::

1. Válassza az **Első lépések** lehetőséget.

1. A Forrásmezők **lapon válassza az** Entitások és mezők **kiválasztása lehetőséget**. Megjelenik az **Entitások és mezők** kiválasztása panel.

1. Válasszon ki legalább egy entitást.

1. Minden kiválasztott entitásnál azonosítsa azokat a mezőket, amelyeket az egyesített profilban szerepeltetni kívánt ügyfélrekordok és mezők egyeztetéséhez szeretne használni. Ezeket a mezőket attribútumoknak *nevezzük*. A szükséges attribútumokat külön-külön is kiválaszthatja egy entitásból, vagy belefoglalhatja az entitás összes attribútumát az entitás szintjén lévő jelölőnégyzet bejelölésével. A kulcsszavakkal az összes attribútum és entitás közül keresheti ki a leképezni kívánt szükséges attribútumokat.

   :::image type="content" source="media/m3_select_entities.png" alt-text="Képernyőkép a kiválasztott entitásokról és attribútumokról.":::

   Ebben a példában az eCommerceContacts és **a** loyCustomer **entitásokat** adjuk hozzá. Ezen entitások kiválasztásával betekintést nyerhet, hogy mely online üzleti ügyfelek tagjai a törzsvásárlói programnak.

1. Válassza az **Alkalmaz** lehetőséget a kijelölések jóváhagyásához. Megjelennek a kijelölt entitások és attribútumok.

## <a name="select-primary-key-and-semantic-type-for-attributes"></a>Az elsődleges kulcs és a szemantikai típus kiválasztása az attribútumokhoz

   :::image type="content" source="media/m3_select_primary.png" alt-text="Képernyőkép a kiválasztott entitásokról, amelyek elsődleges kulcsa még nincs kiválasztva." lightbox="media/m3_select_primary.png":::

Minden entitás esetében hajtsa végre a következő lépéseket.

1. Válassza ki az **Elsődleges kulcsot**. Az elsődleges kulcs az entitás egyedi attribútuma. Ahhoz, hogy egy attribútum érvényes elsődleges kulcs legyen, az ne tartalmazzon ismétlődő értékeket, a hiányzó értékeket vagy a null értékeket. A karakterlánc, az egész szám és a GUID adattípus attribútumai elsődleges kulcsként támogatottak.

1. Ha AI-modelleket szeretne használni a szemantika intelligens előrejelzés, ami időt takarít meg és javítja a pontosságot, győződjön meg arról, hogy **az intelligens leképezés** be van kapcsolva. Az intelligens leképezés AI-alapú szemantikai javaslatokat biztosít a **Típus** mezőben.

1. Minden attribútumhoz válasszon egy szemantikus **típust**, amely a legjobban leírja az attribútumot, például nevet, várost vagy e-mail-címet.

   > [!NOTE]
   > A B-to-C-ben az egyik mezőnek a Person.FullName *szemantikai típusra* kell leképeznie, hogy feltöltse az ügyfél nevét az ügyfélkártyán. A B-től B-ig a fióknévnek Organization.Name kell *leképeznie*. Ellenkező esetben az ügyfélkártyák neve nem lesz látható.

   1. A rendszer által azonosított attribútumtípus felülbírálásához válasszon egy másik lehetőséget. Ha a típus nem létezik, hozzon létre egy egyéni szemantikai típust az **attribútum Típus** mezőjének kiválasztásával és az egyéni szemantikai típus nevének megadásával.

   1. Ha olyan attribútumot szeretne hozzáadni, amely URL-címet tartalmaz a nyilvánosan elérhető profilképekhez vagy emblémákhoz, válassza ki az URL-címet tartalmazó entitást és mezőt. **A Típus** mezőbe írja be a következőket:
      - Személy számára: Person.ProfileImage
      - Szervezet esetén: Organization.LogoImage

1. Tekintse át azokat az attribútumokat, ahol a rendszer automatikusan azonosítja a szemantikai típust. Ezek az attribútumok a Megfeleltetett mezők **áttekintése alatt** vannak felsorolva. Csak az azonos típusú attribútumok kombinálhatók az **Ügyfélmezők** egyesítése lépésben. A szemantikai típusok arra szolgálnak, hogy automatikusan sugallják az elemzéseket. Győződjön meg arról, hogy a kiválasztott típusok konzisztensek az összes kiválasztott entitás között.

1. Az olyan attribútumok esetében, amelyek nincsenek automatikusan leképezve szemantikai típusra, válasszon ki egy szemantikai típusmezőt, adja meg az egyéni attribútumtípus nevét, vagy hagyja őket leképezés nélkül. Ezek az attribútumok a Nem leképezett mezők **adatainak definiálása alatt** vannak felsorolva.

1. Az egyes entitások lépéseinek elvégzése után válassza a Forrásmezők **mentése lehetőséget**.

1. Válassza a **Következő** lehetőséget.

> [!div class="nextstepaction"]
> [Következő lépés: Távolítsa el az ismétlődéseket](remove-duplicates.md)

[!INCLUDE [footer-include](includes/footer-banner.md)]
