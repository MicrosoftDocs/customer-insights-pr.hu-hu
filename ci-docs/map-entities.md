---
title: Forrásmezők kiválasztása adategyesítéshez
description: Az egyesítési folyamat első lépése az entitások, attribútumok, elsődleges kulcsok és szemantikai típusok kiválasztása az adatok egységes ügyfélprofilhoz való hozzárendeléséhez.
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
ms.openlocfilehash: a962f1353b6e25b40c60b39a81ac936873f34d92
ms.sourcegitcommit: 6a5f4312a2bb808c40830863f26620daf65b921d
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/11/2022
ms.locfileid: "8740998"
---
# <a name="select-source-fields-for-data-unification"></a>Forrásmezők kiválasztása adategyesítéshez

[!INCLUDE [m3-prod-trial-note](includes/m3-prod-trial-note.md)]

Az egyesítés első lépése az egyesítendő adatkészletek azon entitásainak és mezőinek kijelölése, amelyeket egyesíteni szeretne. Válasszon olyan entitásokat, amelyek ügyféllel kapcsolatos adatokat tartalmaznak, például nevet, címet, telefonszámot és e-maileket. Kiválaszthat egy vagy több entitást.

## <a name="select-entities-and-fields"></a>Entitások és mezők kiválasztása

1. Nyissa meg az **Adatok** > **egyesítését**.

   :::image type="content" source="media/m3_unify_land.png" alt-text="Képernyőkép a céloldal egyesítéséről az első futtatási élményhez az Első lépések kiemelve funkcióval.":::

1. Válassza az **Első lépések** lehetőséget.

1. A Forrás mezők **lapon válassza az** Entitások és mezők kijelölése **lehetőséget**. Megjelenik az **Entitások és mezők** kijelölése ablaktábla.

1. Jelöljön ki legalább egy entitást.

1. Minden kijelölt entitásnál azonosítsa azokat a mezőket, amelyeket az egyesített profilba felvenni kívánt vevői bejegyzések és mezők egyeztetésére kíván használni. Ezeket a mezőket attribútumoknak *nevezzük*. A szükséges attribútumokat külön-külön is kiválaszthatja egy entitásból, vagy felveheti az entitás összes attribútumát, ha bejelöli az entitásszinten jelölőnégyzetet. A kulcsszavakkal az összes attribútum és entitás közül keresheti ki a leképezni kívánt szükséges attribútumokat.

   :::image type="content" source="media/m3_select_entities.png" alt-text="Képernyőkép a kijelölt entitásokról és attribútumokról.":::

   Ebben a példában a Névjegyalbum **és** a **CustomerLoyalty** entitásokat adjuk hozzá. Ezen entitások kiválasztásával betekintést nyerhet, hogy mely online üzleti ügyfelek tagjai a törzsvásárlói programnak.

1. Válassza az **Alkalmaz** lehetőséget a kijelölések jóváhagyásához. A kijelölt entitások és attribútumok megjelennek.

## <a name="select-primary-key-and-semantic-type-for-attributes"></a>Az elsődleges kulcs és a szemantikai típus kiválasztása az attribútumokhoz

   :::image type="content" source="media/m3_select_primary.png" alt-text="Képernyőkép a kijelölt entitásokról, amelyek elsődleges kulcsa nincs kijelölve." lightbox="media/m3_select_primary.png":::

Minden entitás esetében hajtsa végre a következő lépéseket.

1. Válassza ki az **Elsődleges kulcsot**. Az elsődleges kulcs az entitásra jellemző attribútum. Ahhoz, hogy egy attribútum érvényes elsődleges kulcs legyen, az ne tartalmazzon ismétlődő értékeket, a hiányzó értékeket vagy a null értékeket. A karakterlánc-, egész- és GUID adattípus-attribútumok elsődleges kulcsként támogatottak.

1. Ha mesterségesintelligencia-modelleket szeretne használni a szemantika intelligens előrejelzés, időt takaríthat meg és javíthatja a pontosságot, győződjön meg arról, hogy **az intelligens térképezés** be van kapcsolva. Az intelligens leképezés kiemeli az AI-alapú szemantikai ajánlást a **típus** mezőben. A javasolt kijelölést úgy bírálhatja felül, hogy a rendelkezésre álló beállítások listájából bármilyen szemantikai típust kiválaszt.

1. Minden attribútumhoz válasszon egy szemantikai **típust**, amely a legjobban leírja az adott attribútumot, például nevet, várost vagy e-mail címet.

   > [!NOTE]
   > Az egyik mezőnek a Person.FullName *szemantikai típusra* kell leképeznie a vevő nevét a vevő kartonon való feltöltéséhez. Ellenkező esetben az ügyfélkártyák neve nem lesz látható.

   1. A rendszer által azonosított attribútumtípus módosításához válasszon másik típust. Ha a típus nem létezik, hozzon létre egyéni szemantikai típust az **attribútum Típus** mezőjének kiválasztásával és az egyéni szemantikai típus nevének megadásával.

   1. Ha URL-címet tartalmazó attribútumot szeretne hozzáadni a nyilvánosan elérhető profilképekhez vagy emblémákhoz, jelölje ki az URL-címet tartalmazó entitást és mezőt. **A Típus** mezőbe írja be a következőket:
      - Személy számára: Person.ProfileImage
      - Szervezet esetén: Organization.LogoImage

   1. Fióknév-attribútum esetén írja be a "Organization.Name" szót a **Típus** mezőbe.

1. Tekintse át azokat az attribútumokat, amelyekben a szemantikai típust automatikusan azonosítják. Ezek az attribútumok a Leképezett mezők **áttekintése csoportban** találhatók. Az Egységes vevőmezők **lépésben** csak azonos típusú attribútumok kombinálhatók. A szemantikai típusok automatikusan elemzéseket javasolnak. Győződjön meg arról, hogy a kiválasztott típusok konzisztensek az összes kijelölt entitás között.

1. Olyan attribútumok esetén, amelyek nincsenek automatikusan szemantikai típushoz rendelve, jelöljön ki egy szemantikai típusmezőt, írja be az egyéni attribútumtípus nevét, vagy hagyja őket leképezetlenül. Ezek az attribútumok a Leképezetlen mezők **adatainak definiálása csoportban** találhatók.

1. Az egyes entitások lépéseinek végrehajtása után válassza a Forrásmezők **mentése lehetőséget**.

1. Válassza a **Következő** lehetőséget.

> [!div class="nextstepaction"]
> [Következő lépés: Duplikátumok eltávolítása](remove-duplicates.md)

[!INCLUDE [footer-include](includes/footer-banner.md)]
