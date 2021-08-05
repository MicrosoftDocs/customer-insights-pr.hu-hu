---
title: Ügyfélprofilok keresése és szűrése
description: Gyorsan megtalálhatja az egyesített ügyfelek profiljaira vonatkozó információkat, és szűrhet a megadott attribútumokra.
ms.date: 01/19/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: NimrodMagen
ms.author: nimagen
manager: shellyha
ms.openlocfilehash: a6131d4dddce48b0fba153bcefe5631e0d22d808
ms.sourcegitcommit: dab2cbf818fafc9436e685376df94c5e44e4b144
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/13/2021
ms.locfileid: "6554024"
---
# <a name="customer-profiles-search--filter-index"></a>Felhasználói profilok: Keresés & szűrőindex

Az ügyféladatok egységesítésének eredménye egy Ügyfélprofil entitás, amely egységes nézetet biztosít a teljes ügyfélkörre. Egy [adott ügyfélre vagy ügyfelek egy csoportjára vonatkozó információk](customer-profiles.md) gyors megkereséséhez konfigurálhatja a **Keresés** és a **Szűrés** lehetőségeket az **Ügyfelek** lapon . A cikkből megtudhatja, hogyan szerkeszthetik a rendszergazdák az attribútumokat a **Keresési és szűrési index** lapon, amely a felhasználók számára elérhető a kereséshez és a szűréshez.

> [!div class="mx-imgBorder"]
> ![Keresési szűrő.](media/search-filter.png "Keresési szűrő")

## <a name="add-fields-and-specify-attributes"></a>Mezők hozzáadása és attribútumok megadása

Ha első alkalommal határozza meg a kereshető attribútumokat rendszergazdaként, először meg kell határoznia az indexelt mezőket. Javasoljuk, hogy az összes attribútumot válassza ki, amely alapján a felhasználók kereshetnek és szűrhetik az ügyfeleket az **Ügyfelek** oldalon. Csak az adategyesítési folyamat során létrehozott Felhasználói profil entitásban található attribútumokat adhatja meg.

1. Nyissa meg az **ügyfelek** oldalt, és válassza a **keresési & szűrő indexe** lehetőséget.

2. Válassza a **+ Hozzáadás** elemet az indexelt mezők meghatározásához.

3. A listában jelölje ki az indexelt mezőkként hozzáadni kívánt attribútumokat. A **Hozzáadás** lehetőséggel bármikor hozzáadhat további attribútumokat. A kijelölt attribútumokat az **Eltávolítás** szimbólum választásával is eltávolíthatja.

## <a name="explore-the-indexed-customer-fields-table"></a>Az indexelt ügyféladatokat tartalmazó tábla felfedezése

A következő információk láthatók a táblában.

- **Név**: Az attribútum nevét jelöli, ahogyan az az Ügyfélprofil entitásában jelenik meg.
- **Adattípus**: Azt adja meg, hogy az adattípus karakterlánc, szám vagy dátum-e.
- **A keresésben szerepel**: Azt adja meg, hogy az attribútum használható-e az ügyfelek keresésére az **Ügyfelek** oldalon a **Keresés** mező segítségével.
- **Szűrő hozzáadása**: Meghatározza, hogy az attribútum hogyan használható szűrésre az **Ügyfelek** lapon.

## <a name="editing-filtering-options-for-a-given-attribute"></a>Adott attribútum szűrési beállításainak módosítása

Az **Ügyfelek** oldalon megjelenő **Szűrő** menüben szerepelhet több attribútumszint (például különböző korcsoportok az ügyfelek szűrése céljából).

1. Válassza azadott attribútumhoz tartozó **Szűrő hozzáadása** lehetőséget a **Keresési és szűrési index** oldalon. Megadhatja az eredmények számát és a rendezési sorrendet. Az attribútum adattípusától függően a következő ablaktáblák egyike jelenik meg.

- Karakterlánc típusú attribútumok: Meghatározzák a kívánt eredmények számát a **Karakterlánc szűrőbeállításai** panelen és a rendezési irányelvben, amely alapján rendezve lesznek.

- Numerikus típusú attribútumok: Meghatározzák a belefoglalt intervallumokat a **Számok szűrőbeállításai** panelen és a rendezési irányelvben, amely alapján rendezve lesznek.

- Dátum típusú attribútumok: Meghatározzák a belefoglalt intervallumokat a **Dátumszűrő beállításai** panelen és a rendezési irányelvben, amely alapján rendezve lesznek.

2. Válassza a **Mentés** lehetőséget a módosítások alkalmazásához.

3. Válassza a **Futtatás** lehetőséget, ha már készen áll a beállítások alkalmazására.

## <a name="next-steps"></a>További lépések

Az **Ügyfelek** oldalon ügyfélprofilokat kereshet, illetve az indexelt mezők használatával az összes ügyfélprofil egy részhalmazát láthatja.


[!INCLUDE[footer-include](../includes/footer-banner.md)]