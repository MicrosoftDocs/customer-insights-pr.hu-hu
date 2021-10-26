---
title: Szegmensek megtekintése és létrehozása
description: Szegmensek létrehozása, szerkesztése és törlése, valamint azok használata.
ms.reviewer: mhart
ms.author: jusali
author: jusali
ms.date: 10/01/2021
ms.service: customer-insights
ms.subservice: engagement-insights
ms.topic: how-to
ms.manager: shellyha
ms.openlocfilehash: f6bba645a78173fb00dc75e6080f2aeda0b5a143
ms.sourcegitcommit: 565637f49cbdd05a82f42784f594c19cac299140
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/11/2021
ms.locfileid: "7623590"
---
# <a name="view-and-create-segments"></a>Szegmensek megtekintése és létrehozása

[!INCLUDE [cc-beta-prerelease-disclaimer](includes/cc-beta-prerelease-disclaimer.md)]

A szegmensek lehetővé teszik a látogatók részhalmazainak azonosítását a jellemzők vagy a webhely interakciói alapján. A szegmensek lehetővé teszik szűrők alkalmazását és a részhalmazok elemzését. Az elemzés segíthet megvizsgálni vállalkozás trendjeit és válaszolni azokra. 

:::image type="content" source="media/segments-page.png" alt-text="Képernyőkép az ügyfélkapcsolati alkalmazásról, amely a munkaterület meglévő szegmenseinek listáját mutatja.":::

## <a name="view-segments"></a>Szegmensek megtekintése

1. Válassza a bal navigációs ablaktáblán az **Adatok** elemet. 

1. Jelölje ki a **Szegmensek** lapot a munkaterület összes szegmense listájának megtekintéséhez. 

## <a name="create-a-segment"></a>Szegmens létrehozása

A szegmensek logikai operátorokhoz kapcsolódó szabályokból és feltételekből állnak. A feltételek szűrőket alkalmaznak egy kijelölt dimenzióra. Minden szegmens legfeljebb öt dimenzióval rendelkezhet.

A következő példa egy olyan szegmenst mutat be, amelynek egy szabályban két feltétele van. Kiszűri az összes olyan webhelyeseményt, ahol a böngésző Chrome, és az operációs rendszer iOS vagy Android.

:::image type="content" source="media/segment-sample.png" alt-text="Példa olyan szegmensekre, amelyekben a webhelyesemények szűrésére szolgáló szabályban két feltétel van.":::

Ez a szakasz azt ismerteti, hogyan hozhat létre üres *szegmenst* az alapoktól.

1. Nyissa meg az **Adatok** > **Szegmensek** megnyitása.

1. Válassza az **Új szegmens** lehetőséget.

1. Az **Erőforrástárban** válassza ki a (+) gombot a szűrni kívánt attribútum mellett. Jelenleg csak dimenziók alapján hozhat létre szegmenseket.

   :::image type="content" source="media/create-new-segment.png" alt-text="Új szegmens létrehozása.":::

1. A **Szabály** szakaszban válasszon egy operátort és egy értéket a kijelölt attribútum számára. A következő műveletek nem támogatottak.

   :::image type="content" source="media/choose-operator-segment.png" alt-text="Válasszon egy operátort az új szegmenshez.":::

   - **is**: az értékek pontos egyezését igényli. Az **egyenlő** használatos egy értékhez vagy a **következők bármelyike:** több érték esetében.
   - **nem**: pontos egyezés szükséges az értékek kizárásához. Az **egyenlő** használatos egy értékhez vagy a **következők bármelyike:** több érték esetében.
   - **a következővel kezdődik**: egy karakterlánc, amely az illeszkedő értékkel kezdődik.
   - **a következővel végződik**: egy karakterlánc, amely az illeszkedő értékkel végződik.
   - **tartalmazza**: egy sztring része az egyező értékeknek.

1. Ha további feltételeket szeretne hozzáadni egy csoporthoz, használhatja a logikai operátorokat. A vetített attribútumokat figyelembe veszi a rendszer a beállított operátorok használatakor.
   - **ÉS** operátor: mindkét feltételnek a szegmentálási folyamat részeként kell teljesülnie. Ez a beállítás akkor a leghasznosabb, ha különböző entitások között határoz meg feltételeket.
   - **VAGY** operátor: a szegmentálási folyamat részeként az egyik feltételnek meg kell felelnie. Ez a beállítás akkor a leghasznosabb, ha különböző feltételeket ad meg ugyanahhoz az entitáshoz.

1. Válassza a **Mentés** lehetőséget, és nevezze el a szegmenst. 

A szegmens megjelenik a **Szegmensek** lapon, és a munkaterület összes jelentésére és tölcsérére alkalmazhatja.

## <a name="use-a-segment-in-a-report-or-funnel"></a>Szegmens használata jelentésben vagy tölcsérben

Szegmenseket alkalmazhat egy jelentésre vagy egy tölcsérre, hogy szűrje őket a szegmens feltételei alapján. A valós idejű használati jelentésre azonban nem alkalmazhat szegmenseket.

:::image type="content" source="media/segment-reports-filter.png" alt-text="A kibontott legördülő listával megjelenő oldalnézetek jelentésében kiválaszthatja, hogy mely szegmenseket kell alkalmaznia.":::

Szegmens alkalmazásához nyissa meg a jelentést vagy a tölcsért. Válassza a **+ Feltétel hozzáadása** lehetőséget, és válassza a **Szűrés szegmensenként** lehetőséget. Válassza ki azt a szegmenst a listából, amelyet alkalmazni szeretne. A szegmens a jelentésre lesz alkalmazva. Ha egy diagram nem támogatja a szegmenst, hibaüzenet jelenik meg. További információ: [Tölcsérjelentések létrehozása és kezelése](funnel-reports.md).
 
Egy jelentésre vagy tölcsérre *legfeljebb három szegmenst* alkalmazhat.

## <a name="edit-a-segment"></a>Szegmens szerkesztése

1. Nyissa meg az **Adatok** > **Szegmensek** megnyitása.
1. Válassza ki a szegmenst a listában a megnyitásához. 
1. Szükség szerint módosítsa vagy adjon hozzá értékeket.
1. Válassza a **Mentés** lehetőséget a módosítások alkalmazásához.

## <a name="change-the-name-of-a-segment"></a>Megváltoztatja egy szegmens nevét

1. Nyissa meg az **Adatok** > **Szegmensek** megnyitása.
1. A szegmens listában válassza a **Tovább [...]** lehetőséget. 
1. Válassza a **Név szerkesztése** lehetőséget a legördülő listából.
1. Adja meg az új nevet, és válassza ki az **Átnevezés** lehetőséget.

## <a name="delete-a-segment"></a>Egy szegmens törlése

1. Nyissa meg az **Adatok** > **Szegmensek** megnyitása.
1. A szegmens listában válassza a **Tovább [...]** lehetőséget. 
1. Válassza a **Törlés** lehetőséget a legördülő listából.
1. A megerősítéshez válassza a **Törlés** lehetőséget.



[!INCLUDE[footer-include](../includes/footer-banner.md)]
