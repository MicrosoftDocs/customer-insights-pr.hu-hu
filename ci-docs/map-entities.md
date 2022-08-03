---
title: Forrásmezők kiválasztása az adatok egyesítéséhez
description: Az egyesítési folyamat első lépése az entitások, attribútumok, elsődleges kulcsok és szemantikai típusok kiválasztása az adatok egységes ügyfélprofilra való leképezéséhez.
recommendations: false
ms.date: 04/22/2022
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
ms.openlocfilehash: a75218c996b277e00924f2b7b38ea686a1f4dc38
ms.sourcegitcommit: 3c5b0b40b2b45e420015bbdd228ce0e610245e6f
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/12/2022
ms.locfileid: "9139785"
---
# <a name="select-source-fields-for-data-unification"></a>Forrásmezők kiválasztása az adatok egyesítéséhez

Az egyesítés első lépése az adatkészleteken belüli olyan entitások és mezők kiválasztása, amelyeket egyesíteni szeretne. Válasszon olyan entitásokat, amelyek ügyféllel kapcsolatos adatokat tartalmaznak, például nevet, címet, telefonszámot és e-mailt. Kiválaszthat egy vagy több entitást.

## <a name="select-entities-and-fields"></a>Entitások és mezők kiválasztása

1. Lépjen az Adatok **egyesítése oldalra** > **·**.

   :::image type="content" source="media/m3_unify_land.png" alt-text="Képernyőkép az egyesítse a céloldalt az első futtatás élményéhez az Első lépések kiemeléssel funkcióval.":::

1. Válassza az **Első lépések** lehetőséget.

1. A Forrásmezők **lapon válassza az** Entitások és mezők kiválasztása **lehetőséget**. Megjelenik az **Entitások és mezők** kiválasztása panel.

1. Válasszon ki legalább egy entitást.

1. Minden kiválasztott entitásnál azonosítsa azokat a mezőket, amelyeket az egyesített profilban szerepeltetni kívánt ügyfélrekordok és mezők egyeztetéséhez szeretne használni. Ezeket a mezőket attribútumoknak *nevezzük*. A szükséges attribútumokat külön-külön is kiválaszthatja egy entitásból, vagy belefoglalhatja az entitás összes attribútumát az entitás szintjén lévő jelölőnégyzet bejelölésével. A kulcsszavakkal az összes attribútum és entitás közül keresheti ki a leképezni kívánt szükséges attribútumokat.

   :::image type="content" source="media/m3_select_entities.png" alt-text="Képernyőkép a kiválasztott entitásokról és attribútumokról.":::

   Ebben a példában a Kapcsolattartók **és** a **CustomerLoyalty** entitásokat adjuk hozzá. Ezen entitások kiválasztásával betekintést nyerhet, hogy mely online üzleti ügyfelek tagjai a törzsvásárlói programnak.

1. Válassza az **Alkalmaz** lehetőséget a kijelölések jóváhagyásához. Megjelennek a kijelölt entitások és attribútumok.

## <a name="select-primary-key-and-semantic-type-for-attributes"></a>Az elsődleges kulcs és a szemantikai típus kiválasztása az attribútumokhoz

   :::image type="content" source="media/m3_select_primary.png" alt-text="Képernyőkép a kiválasztott entitásokról, amelyek elsődleges kulcsa nincs kiválasztva." lightbox="media/m3_select_primary.png":::

Minden entitás esetében hajtsa végre a következő lépéseket.

1. Válassza ki az **Elsődleges kulcsot**. Az elsődleges kulcs az entitás egyedi attribútuma. Ahhoz, hogy egy attribútum érvényes elsődleges kulcs legyen, az ne tartalmazzon ismétlődő értékeket, a hiányzó értékeket vagy a null értékeket. A karakterlánc, az egész szám és a GUID adattípus attribútumai elsődleges kulcsként támogatottak.

1. Ha AI-modelleket szeretne használni a szemantika intelligens előrejelzés, időt takaríthat meg és javíthatja a pontosságot, győződjön meg arról, hogy **az intelligens leképezés** be van kapcsolva. Az intelligens leképezés kiemeli az AI-alapú szemantikai ajánlást a **típus** mezőben. A javasolt kijelölést felülbírálhatja, ha bármilyen szemantikai típust kiválaszt a rendelkezésre álló lehetőségek listájából.

1. Minden attribútumhoz válasszon egy szemantikus **típust**, amely a legjobban leírja az attribútumot, például nevet, várost vagy e-mail-címet.

   > [!NOTE]
   > Az egyik mezőnek a Person.FullName *szemantikus típusra* kell leképeznie, hogy feltöltse az ügyfél nevét az ügyfélkártyán. Ellenkező esetben az ügyfélkártyák neve nem lesz látható.

   1. A rendszer által azonosított attribútumtípus módosításához válasszon másik típust. Ha a típus nem létezik, hozzon létre egy egyéni szemantikai típust az **attribútum Típus** mezőjének kiválasztásával, és adja meg az egyéni szemantikai típus nevét.

   1. Ha olyan attribútumot szeretne hozzáadni, amely URL-címet tartalmaz a nyilvánosan elérhető profilképekhez vagy emblémákhoz, válassza ki az URL-címet tartalmazó entitást és mezőt. **A Típus** mezőbe írja be a következőket:
      - Személy számára: Person.ProfileImage
      - Szervezet esetén: Organization.LogoImage

   1. Fióknév attribútumhoz írja be a "Organization.Name" kifejezést a **Típus** mezőbe.

1. Tekintse át azokat az attribútumokat, ahol a rendszer automatikusan azonosítja a szemantikai típust. Ezek az attribútumok a Megfeleltetett mezők **áttekintése alatt** vannak felsorolva. Csak az azonos típusú attribútumok kombinálhatók az **Egyesített ügyfélmezők** lépésben. A szemantikai típusok arra szolgálnak, hogy automatikusan sugallják az elemzéseket. Győződjön meg arról, hogy a kiválasztott típusok konzisztensek az összes kiválasztott entitás között.

1. Az olyan attribútumok esetében, amelyek nincsenek automatikusan leképezve szemantikai típusra, válasszon ki egy szemantikai típusmezőt, adja meg az egyéni attribútumtípus nevét, vagy hagyja őket leképezés nélkül. Ezek az attribútumok a Nem leképezett mezők **adatainak definiálása alatt** vannak felsorolva.

1. Az egyes entitások lépéseinek elvégzése után válassza a Forrásmezők **mentése lehetőséget**.

1. Válassza a **Következő** lehetőséget.

> [!div class="nextstepaction"]
> [Következő lépés: Távolítsa el az ismétlődéseket](remove-duplicates.md)

[!INCLUDE [footer-include](includes/footer-banner.md)]
