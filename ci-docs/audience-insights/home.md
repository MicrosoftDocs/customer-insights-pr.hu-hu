---
title: Kezdőlap célközönség-információkban
description: Ismerje meg az alkalmazást a kezdőlapon.
ms.date: 09/30/2020
ms.reviewer: nimagen
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: bd16966eabb126d9c9945ededc53273df02c3369
ms.sourcegitcommit: cf9b78559ca189d4c2086a66c879098d56c0377a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/03/2020
ms.locfileid: "4406008"
---
# <a name="create-a-new-environment"></a>Új környezet létrehozása

## <a name="create-a-trial-environment"></a>Próbakörnyezet létrehozása

A próbaverzióra való feliratkozást a [próbaverzió regisztrációs oldalon](https://dynamics.microsoft.com/get-started/free-trial/?appname=customerinsights) teheti meg. 

> [!NOTE]
> A próbaverziók 30 nap elteltével járnak le.

1. Válassza ki a **Feliratkozás egy ingyenes próbára** lehetőséget, és válassza a **Feliratkozás most** lehetőséget.

1. Adja meg a munkahelyi vagy iskolai e-mail címét, meséljen többet magáról, és válassza a **következő** lehetőséget.

1. Adja meg az új környezet **nevét**. 

1. Válassza ki a próbaverzió típusát.

1. Válasszon **régiót** a környezethez.

1. Tetszés szerint, a rendszergazdák a Dynamics 365 szervezetnél: válassza a **Speciális beállításokat**, és adja meg a szervezet URL-címét az előrejelzés funkciók használatához, mint az ügyféllemorzsolódás.

1. Válassza a **Létrehozás** parancsot. 

A környezet létrehozása után megjelenik a **Bemutató** környezetet, amely lehetővé teszi, hogy a kitalált adatokkal tárja fel az alkalmazást. A mintaadatok az iparágnak megfelelően módosíthatók. Válassza ki a **Beállítások** ikont a fejlécben, és válassza a **demó beállítások** lehetőséget. Emellett megváltoztathatja a vizuális témát is. 

[Váltson arra a környezetre](#change-between-environments), amelyet a regisztrációs folyamat során hozott létre saját adataival.

## <a name="create-a-new-production-or-sandbox-environment"></a>Új vagy tesztkörnyezet létrehozása

A környezetében jelölje ki a **Beállítások** ikont a fejlécben, és válassza az **új környezet** lehetőséget.

Ha [próbakörnyezetet hoz létre](#create-a-trial-environment), hajtsa végre a lépéseket. További lehetőséget kap, amikor a **speciális beállítások** lehetőséget választja az adatoknak a saját Azure Data Lake-ben történő tárolásához. Adja meg a fiókja nevét és a fiók kulcsát az Azure Data Lake kapcsolat létrehozásához. Alapértelmezés szerint az adatokat a Customer Insights által felügyelt adattó tárolja.

> [!IMPORTANT]
> Az adatok Azure Data Lake Storage-tárhelyre való mentésével elfogadja, hogy az adatok az adott Azure-tárfiókhoz tartozó megfelelő földrajzi helyre kerülnek át, és ott tárolják őket; ez pedig eltérhet a Dynamics 365 Customer Insights szolgáltatásban tárolt adatok helyétől. [További információ a Microsoft adatvédelmi központról.](https://www.microsoft.com/trust-center)

## <a name="explore-the-home-page"></a>A kezdőlap felfedezése

A [Customer Insights környezethez hozzáférhet](https://home.ci.ai.dynamics.com/) a következő URL-címen: [https://home.ci.ai.dynamics.com/](https://home.ci.ai.dynamics.com/).
A **Kezdőlap** oldalon áttekintést kaphat az ügyfélkörről és a legfontosabb mérőszámokról, hogy nyomon követhesse a vállalkozás állapotát.

> [!div class="mx-imgBorder"] 
> ![Betekintések a Kezdőlapon](media/home-page-insights.png "Betekintések a Kezdőlapon")

A **Legutóbbi szegmensek** alatt a megadott demográfiai, viselkedési vagy tranzakciós attribútumok alapján megtekintheti az ügyfelek csoportjait. [A szegmensek létrehozásával](segments.md) könnyebben megcélozhatja az üzleti tevékenységeket.

A **Legújabb intézkedések** a [mérőszámokat](measures.md) tartalmazó csempéket jeleníti meg. Az mérőszámok a definiált fő teljesítménymutatók (KPI-k). Például az ügyfelek elvándorlásának átlagos valószínűsége vagy átlagos online kiadások ügyfelenként.

A **Legújabb kiegészítő információk** szakasz felsorolja a bővítési futtatások eredményeit, amely a közelmúltban fejeződtek be. A kiegészítő információk az ügyfélkörre vonatkozó információkat adnak hozzá. Például megtekintheti azokat az érdeklődési köröket és márkákat, amelyek fontosak számukra. Ez az információ a [bővítési](enrichment-microsoft-graph.md) lehetőségek segítségével tehető elérhetővé, a [Leképezés](map-entities.md), az [Egyeztetés](match-entities.md) és az [Egyesítés](merge-entities.md) fázisainak befejezése után.

## <a name="change-between-environments"></a>A környezetek közötti váltás

Az [adatforrások](data-sources.md) beállítása és konfigurálása után érdemes átváltania a bemutató környezetből egy élő környezetbe. Az éles üzemi környezet segítségével saját ügyféladatokat is használhat. A környezet módosításához válassza ki az oldal jobb felső sarkában található **Környezet** vezérlőt.

> [!div class="mx-imgBorder"] 
> ![Váltás a környezetek között](media/home-page-environment-switcher.png "Váltás a környezetek között")

A rendszergazdák [több környezetet](manage-environments.md) is létrehozhatnak és kezelhetnek. Az egynél több környezet fenntartása akkor lehet hasznos, ha például a szervezet nemzetközileg működik, és különböző módon kell elkülöníteni az adatokkal és a betekintő adatokat.

## <a name="next-step"></a>Következő lépés

Ha szeretné megtekinteni a saját betekintő adatait a kezdőlapon, előbb [hozzá kell adnia az adatforrásokat](data-sources.md), és [egyesítenie](data-unification.md) az adatait az ügyfelek profiljainak összeállításához.
