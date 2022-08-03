---
title: Az ügyfélprofilok keresési &szűrési indexének kezelése
description: Gyorsan megtalálhatja az egyesített ügyfelek profiljaira vonatkozó információkat, és szűrhet a megadott attribútumokra.
ms.date: 07/22/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: conceptual
author: NimrodMagen
ms.author: nimagen
manager: shellyha
searchScope:
- ci-search-filter
- customerInsights
ms.openlocfilehash: dfbfcbff3ffb3e4483252377e591229631d38556
ms.sourcegitcommit: c45c3e044034bf866b0662f80a59166cee4ababe
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/22/2022
ms.locfileid: "9187912"
---
# <a name="manage-the-search--filter-index-for-customer-profiles"></a>Az ügyfélprofilok keresési &szűrési indexének kezelése

Az ügyféladatok egységesítésének eredménye egy *Ügyfél* entitás, amely egységes nézetet biztosít a teljes ügyfélkörbe. Ahhoz, hogy a felhasználók gyorsan [megtalálják az információkat egy adott ügyfélről vagy ügyfélcsoportról](customer-profiles.md), a rendszergazdának konfigurálnia kell a **Keresési** és **szűrési** képességeket az **Ügyfelek** számára oldalon.

   :::image type="content" source="media/search-filter.png" alt-text="Keresési szűrő":::

## <a name="define-searchable-attributes-and-indexed-fields"></a>Kereshető attribútumok és indexelt mezők definiálása

Ha ez az első alkalom, hogy rendszergazdaként kereshető attribútumokat határoz meg, először definiálja az indexelt mezőket. Javasoljuk, hogy az összes attribútumot válassza ki, amely alapján a felhasználók kereshetnek és szűrhetik az ügyfeleket az **Ügyfelek** oldalon. Csak az *adategyesítési folyamat során létrehozott Ügyfél* entitásban létező attribútumok adhatók meg.

1. Lépjen az Ügyfelek **elemre,** és válassza a Keresés &szűrő index **lehetőséget**.

1. Válassza a + Hozzáadás **lehetőséget**.

1. Jelölje ki a listában szereplő attribútumokat, amelyeket indexelt mezőkként szeretne hozzáadni, majd kattintson az Alkalmaz **gombra**.

1. További attribútumok hozzáadásához válassza a Hozzáadás **lehetőséget**. Egy kijelölt attribútum eltávolításához jelölje ki az attribútumot, majd **törölje**.

   :::image type="content" source="media/search-filter-index.png" alt-text="Keresés &szűrő index oldal.":::

1. Válassza a Futtatás **lehetőséget**, ha készen áll a keresési és szűrési beállítások alkalmazására. A módosítások feldolgozása után tekintse meg őket az [ügyfélkártyákon az Ügyfél oldalon](customer-profiles.md).

## <a name="define-filtering-options-for-a-given-attribute"></a>Szűrési beállítások definiálása egy adott attribútumhoz

Állítsa be az ügyfelek szűrésére használható mezőket az **Ügyfelek** oldalon.

1. Lépjen az Ügyfelek **elemre,** és válassza a Keresés &szűrő index **lehetőséget**.

1. Válasszon ki egy attribútumot, és **a Szűrő hozzáadása lehetőséget**. Határozza meg az eredmények számát és a rendszerezés sorrendjét. Az attribútum adattípusától függően az alábbi ablaktáblák egyike jelenik meg.

   - Sztringtípus-attribútumok: Adja meg a kívánt eredmények számát a **Karakterláncszűrő** panelen, valamint azt a rendelési szabályzatot, amely alapján a rendszer szervezi őket.

   - Numerikus típusú attribútumok: Adja meg a Számszűrő **panelen szereplő** időközöket és a rendszerezésük sorrendjét.

   - Dátum típusú attribútumok: Adja meg a Dátumszűrő **panelen szereplő** időközöket és a rendszerezésük sorrendjét.

1. Válassza az **OK** lehetőséget. Ismételje meg az ismétlést minden olyan attribútumnál, amely alapján szűrni szeretne.

1. Válassza a Futtatás **lehetőséget**, ha készen áll a keresési és szűrési beállítások alkalmazására. A módosítások feldolgozása után tekintse meg őket az [ügyfélkártyákon az Ügyfél oldalon](customer-profiles.md).

## <a name="view-indexed-customer-fields"></a>Indexelt vevőmezők megtekintése

A **Keresés &szűrő index** oldal a következő információkat jeleníti meg:

- **Név**: Az attribútum nevét jelöli, ahogyan az a *Vevő* entitásban megjelenik.
- **Adattípus**: Azt adja meg, hogy az adattípus karakterlánc, szám vagy dátum-e.
- **A keresésben szerepel**: Azt adja meg, hogy az attribútum használható-e az ügyfelek keresésére az **Ügyfelek** oldalon a **Keresés** mező segítségével.
- **Szűrő hozzáadása**: Meghatározza, hogy az attribútum hogyan használható szűrésre az **Ügyfelek** lapon.

## <a name="next-steps"></a>További lépések

Tekintse át az [egyesített profilok lapot](customer-profiles.md) a profilok kereséséhez, vagy az indexelt mezők használatával tekintse meg az összes egyesített profil egy részhalmazát.

[!INCLUDE [footer-include](includes/footer-banner.md)]
