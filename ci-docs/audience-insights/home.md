---
title: Kezdőlap célközönség-információkban
description: Ismerje meg az alkalmazást a kezdőlapon.
ms.date: 01/07/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: NimrodMagen
ms.author: nimagen
manager: shellyha
ms.openlocfilehash: bf9080c564850bca0c239b7317eed2fc0f77d9f3
ms.sourcegitcommit: bae40184312ab27b95c140a044875c2daea37951
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/15/2021
ms.locfileid: "5597238"
---
# <a name="create-a-new-environment"></a>Új környezet létrehozása

## <a name="create-a-trial-environment"></a>Próbakörnyezet létrehozása

A próbaverzióra való feliratkozást a [próbaverzió regisztrációs oldalon](https://dynamics.microsoft.com/get-started/free-trial/?appname=customerinsights) teheti meg. 

> [!NOTE]
> A próbaverziók 30 nap elteltével járnak le.

1. Válassza ki a **Feliratkozás egy ingyenes próbára** lehetőséget, és válassza a **Feliratkozás most** lehetőséget.

1. Adja meg a munkahelyi vagy iskolai e-mail címét, meséljen többet magáról, és válassza a **következő** lehetőséget.

   :::image type="content" source="media/trial-signup-dialog.png" alt-text="Párbeszédpanel a próbapéldány regisztrációjához":::

1. Adja meg az új környezet **nevét**. 

1. Válassza ki a próbaverzió típusát.

1. Válasszon **régiót** a környezethez.

1. Tetszés szerint, a rendszergazdák a Dynamics 365 szervezetnél: válassza a **Speciális beállításokat**, és adja meg a szervezet URL-címét az előrejelzés funkciók használatához, mint az ügyféllemorzsolódás.

1. Válassza a **Létrehozás** parancsot. 

A környezet létrehozása után megjelenik a **Bemutató** környezetet, amely lehetővé teszi, hogy a kitalált adatokkal tárja fel az alkalmazást. A mintaadatok az iparágnak megfelelően módosíthatók. Válassza ki a **Beállítások** ikont a fejlécben, és válassza a **demó beállítások** lehetőséget. Emellett megváltoztathatja a vizuális témát is. 

[Váltson arra a környezetre](#switch-environments), amelyet a regisztrációs folyamat során hozott létre saját adataival.

## <a name="create-a-new-production-or-sandbox-environment"></a>Új vagy tesztkörnyezet létrehozása

Válassza ki az alkalmazás fejlécében a **Környezet** választó lehetőséget, és válassza az **Új** lehetőséget.

Ha [próbakörnyezetet hoz létre](#create-a-trial-environment), hajtsa végre a lépéseket. Alapértelmezés szerint az adatokat a Customer Insights által felügyelt adattó tárolja. További lehetőséget kap, amikor a **speciális beállítások** lehetőséget választja az adatoknak a saját Azure Data Lake-ben történő tárolásához. Adja meg a fiókja nevét és a fiók kulcsát az Azure Data Lake kapcsolat létrehozásához. 

> [!IMPORTANT]
> Az adatok Azure Data Lake Storage-tárhelyre való mentésével elfogadja, hogy az adatok az adott Azure-tárfiókhoz tartozó megfelelő földrajzi helyre kerülnek át, és ott tárolják őket; ez pedig eltérhet a Dynamics 365 Customer Insights szolgáltatásban tárolt adatok helyétől. [További információ a Microsoft adatvédelmi központról.](https://www.microsoft.com/trust-center)

## <a name="explore-the-home-page"></a>A kezdőlap felfedezése

A [célközönséggel kapcsolatos információkat a Dynamics 365 Customer Insights alkalmazásból](https://home.ci.ai.dynamics.com/) a következő URL-címről is elérheti: [https://home.ci.ai.dynamics.com/](https://home.ci.ai.dynamics.com/).
A **Kezdőlap** oldal a [leképezés](map-entities.md) és [egyeztetés](match-entities.md) és [egyesítés](merge-entities.md) fázisok elvégzését követően áttekintést nyújt a szegmensekről, mértékekről és bővítési adatokról.

> [!div class="mx-imgBorder"] 
> ![Betekintések a Kezdőlapon](media/home-page-insights.png "Betekintések a Kezdőlapon")

A **Legutóbbi szegmensek** alatt a megadott demográfiai, viselkedési vagy tranzakciós attribútumok alapján megtekintheti az ügyfelek csoportjait. A [szegmensek létrehozása](segments.md) segít Önnek az ügyfélkört csoportosításában, és hogy jobban célozni tudja az üzleti tevékenységeket.

A **legújabb mértékek** a definiált [meghatározott teljesítménymutatókat (KPI-k)](measures.md) tartalmazó csempéket is megjelenítenek. Például az ügyfél lemorzsolódásának átlagos valószínűsége vagy átlagos online költés ügyfelenként.

A **Legújabb kiegészítő információk** szakasz felsorolja a bővítési futtatások eredményeit, amely a közelmúltban fejeződtek be. A [Bővítések](enrichment-hub.md) az ügyfélkörre vonatkozó információkat adnak hozzá. Például megtekintheti azokat az érdeklődési köröket és márkákat, amelyek fontosak számukra.

## <a name="switch-environments"></a>Váltás a környezetek között

A környezet módosításához válassza ki az oldal jobb felső sarkában található **Környezet** vezérlőt.

> [!div class="mx-imgBorder"] 
> ![Váltás a környezetek között](media/home-page-environment-switcher.png "Váltás a környezetek között")

A rendszergazdák [több környezetet](manage-environments.md) is létrehozhatnak és kezelhetnek. Az egynél több környezet fenntartása akkor lehet hasznos, ha például a szervezet nemzetközileg működik, és különböző módon kell elkülöníteni az adatokkal és a betekintő adatokat.

## <a name="next-step"></a>Következő lépés

Ha szeretné megtekinteni a saját betekintő adatait a kezdőlapon, előbb [hozzá kell adnia az adatforrásokat](data-sources.md), és [egyesítenie](data-unification.md) az adatait az ügyfelek profiljainak összeállításához.


[!INCLUDE[footer-include](../includes/footer-banner.md)]