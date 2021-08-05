---
title: Entitások leképezése az adategyesítésben
description: Adatok leképezése az egyesített ügyfélprofilok létrehozásához.
ms.date: 09/25/2020
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: tutorial
author: adkuppa
ms.author: adkuppa
ms.reviewer: mhart
manager: shellyha
ms.openlocfilehash: 7fc05aca61d1136f620019ee82dc6937ea39d8e5
ms.sourcegitcommit: dab2cbf818fafc9436e685376df94c5e44e4b144
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/13/2021
ms.locfileid: "6555126"
---
# <a name="map-entities-and-attributes"></a>Entitások és attribútumok leképezése

A **Leképezés** az adategyesítési folyamat első fázisa a célközönség-információknál. A leképezés három fázisból áll:

- *Entitás kiválasztása*: Azonosítsa azokat az kombinálható-entitásokat, amelyek egy adatkészlethez vezetnek, amely az ügyfelekkel kapcsolatos bővebb információkat tartalmaznak.
- *Attribútumok kijelölése*: Az egyes entitások esetében azonosítsa az összekapcsolni és összeegyeztetni kívánt oszlopokat a *egyeztetési* és *egyesítési* fázisokban. Ezeket az oszlopokat *Attribútumoknak* nevezik.
- *Elsődleges kulcs és szemantikai típus kijelölése*: Minden egyes entitásnál azonosítson egy attribútumot, amelyet az adott entitás elsődleges kulcsaként szeretne definiálni, és minden attribútumnál azonosítson egy olyan szemantikai típust, amely a legjobban leírja az adott attribútumot.

Az Adategyesítés általános folyamatáról az [Egységesítés](data-unification.md) című rész tartalmaz további tudnivalókat.

## <a name="select-the-first-entities"></a>Jelölje ki az első entitásokat

1. A célközönség információin belül nyissa meg a következőt: **Adatok** > **Egyesítés** > **Leképezés**.

2. Az **Entitások kiválasztása** lehetőség választásával indítsa el a leképezési fázist.

3. Válassza ki a használni kívánt entitásokat és attribútumokat az *egyeztetés* és *egyesítés* fázisokban. A kötelező attribútumokat egyenként is kijelölheti egy entitásból, illetve az összes attribútumot szerepeltetheti egy entitásban, ha bejelöli az **Összes mező belefoglalása** jelölőnégyzetet az entitás szintjén. Javasoljuk, hogy legalább két entitást válasszon az adategyesítési folyamat előnyeinek kiaknázásához.

   > [!div class="mx-imgBorder"]
   > ![Példa entitások hozzáadására.](media/data-manager-configure-map-add-entities-example.png "Példa entitások hozzáadására")

   Ebben a példában az **eCommerceContacts** és az **loyCustomers** entitásokat adjuk hozzá. Ezen entitások kiválasztásával betekintést nyerhet, hogy mely online üzleti ügyfelek tagjai a törzsvásárlói programnak.
   
   A kulcsszavakkal az összes attribútum és entitás közül keresheti ki a leképezni kívánt szükséges attribútumokat.
   
     > [!div class="mx-imgBorder"]
   > ![Példa keresési mezőkre.](media/data-manager-configure-map-search-fields-example.png "Példa keresési mezőkre")

4. Válassza az **Alkalmaz** lehetőséget a kijelölések jóváhagyásához.

## <a name="select-primary-key-and-semantic-type-for-attributes"></a>Az elsődleges kulcs és a szemantikai típus kiválasztása az attribútumokhoz

Az entitások kijelölése után a **Leképezés** lap megjeleníti a kijelölt entitásokat az ellenőrzéshez. Határozza meg egy entitás elsődleges kulcsát, és azonosítsa az entitáshoz tartozó attribútumok szemantikai típusát.

- **Elsődleges kulcs**:Az egyes entitások esetében jelöljön ki egy attribútumot elsődleges kulcsként. Ahhoz, hogy egy attribútum érvényes elsődleges kulcs legyen, az ne tartalmazzon ismétlődő értékeket, a hiányzó értékeket vagy a null értékeket. A karakterlánc, egész szám és a GUID-adattípus attribútumait elsődleges kulcsként támogatja a rendszer, és megjelenik abban a mezőben, amelyből választhat.

- **Attribútum szemantikai típusa**: Az attribútumai kategóriái, például e-mail cím vagy név. Ha AI modelleket szeretne használni a szemantika intelligens előrejelzéséhoz, időt takaríthat meg, és javíthatja a pontosságot, beállíthatja az **intelligens leképezés** értékét **BE** értékre. Az intelligens leképezés kiemeli az AI-alapú szemantikai ajánlást a **típus** mezőben. Ha a beállítás értéke **KI**, akkor rendszeres leképezési javaslatokat lát majd. A választható lehetőségek listájából tetszőleges szemantikai típust választhat, és felülbírálhatja a javasolt kijelölést.

> [!div class="mx-imgBorder"]
> ![az attribútum típusa és a szemantikai előrejelzés.](media/data-manager-configure-map-add-attributes-semantic-prediction.png "Az attribútum típusa és a szemantikai előrejelzés")

Az egyéni szemantikus típus hozzáadása is lehetséges. Válassza ki egy attribútum típus mezőjét, majd írja be a szemantikus attribútum-típus nevét. Így a rendszer által automatikusan azonosított attribútum-típusokat is módosíthatja.

Minden attribútum, amelyhez a rendszer automatikusan azonosít egy szemantikai típust a **Leképezett mezők áttekintése** szakaszban van csoportosítva. Tekintse át ezeket az attribútumokat és a szemantikai típusokat, mivel ezek lesznek az adategyesítési lépésben az entitások egyesítésére használva.

A szemantikai típusokhoz automatikusan nem leképezett attribútumok az **Adatok definiálása a nem leképezett mezőkben** szakaszban vannak összegyűjtve. Jelölje ki a nem leképezett attribútumok szemantikai típus mezőjét, vagy írja be az egyéni attribútumtípus nevét.

> [!div class="mx-imgBorder"]
> ![Elsődleges kulcs és attribútum típusa.](media/data-manager-configure-map-add-attributes.png "Elsődleges kulcs és attribútum típusa")

> [!NOTE]
> Egy mezőnek a szemantika Person.FullName típushoz kell lennie leképezve, hogy fel legyen töltve az ügyfél neve az ügyfélkártyában. Ellenkező esetben az ügyfélkártyák neve nem lesz látható. 

## <a name="add-and-remove-attributes-and-entities"></a>Attribútumok és entitások hozzáadása és eltávolítása

1. Az **Egyesítés** > **Leképezés** alatt válassza a **Mezők szerkesztése** lehetőséget.

2. Adja hozzá vagy távolítsa el az attribútumokat és entitásokat a **Mezők szerkesztése** ablaktáblában. A keresés vagy a görgetés segítségével keresse meg és jelölje ki az érintett attribútumokat és entitásokat. Az attribútumok és entitások nem távolíthatók el, ha már egyeztetve lettek.

   > [!div class="mx-imgBorder"]
   > ![Entitások hozzáadása vagy eltávolítása.](media/configure-data-map-edit.png "Entitások hozzáadása vagy eltávolítása")

3. Válassza az **Alkalmaz** lehetőséget.

## <a name="add-images-to-profiles"></a>Képek hozzáadása profilokhoz

Ha egy entitás a nyilvánosan elérhető profilhoz tartozó képekhez vagy emblémához URL-címeket tartalmaz, azokat felveheti az egyesített felhasználói profilba.

Jelölje ki az entitást, és keresse meg azt a mezőt, amely a profilkép URL-címét tartalmazza. A **Típus** beviteli mezőben adja meg manuálisan a következő értéket: 
- Személy számára: Person.ProfileImage
- Szervezet esetén: Organization.LogoImage

Folytassa az egyesítési lépéseket, és gondoskodjon róla, hogy a kép URL-címét tartalmazó attribútumot is hozzáadja az [Egyesítés](merge-entities.md) lépéshez.

## <a name="set-attributes-for-organizations"></a>Attribútumok beállítása szervezetekhez

A szervezetek (előnézet) esetében az attribútum típusát le kell képezni az "Organization.Name" értékhez
> [!div class="mx-imgBorder"]
> ![Elsődleges kulcs és attribútum B2B](media/configure-data-map-edit-b2b.png "Elsődleges kulcs és attribútum B2B")

## <a name="next-step"></a>Következő lépés

Az adategyesítési folyamat részeként nyissa meg az **Egyeztetés** oldalt. Tekintse meg az [**Egyeztetés**](match-entities.md) szakaszt, ha többet szeretne megtudni erről a fázisról.

> [!TIP]
> Tekintse meg a következő videótL [Első lépések: Egyesített ügyfél profillétrehozása](https://youtu.be/oBfGEhucAxs).


[!INCLUDE[footer-include](../includes/footer-banner.md)]