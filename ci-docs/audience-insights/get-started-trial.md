---
title: A Customer Insights próbaverziójának létrehozása és konfigurálása
description: A Dynamics 365 Customer Insights próba-előfizetés beszerzésének és konfigurációjának lépései.
ms.date: 07/22/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: MichelleDevaney
ms.author: midevane
manager: shellyha
ms.custom: intro-internal
ms.openlocfilehash: f038dedd369ac9e623146b66528efa87c47a8c23769037d8709fa9b804a0b723
ms.sourcegitcommit: aa0cfbf6240a9f560e3131bdec63e051a8786dd4
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/10/2021
ms.locfileid: "7035418"
---
# <a name="set-up-a-trial-environment"></a>Próbakörnyezet beállítása 

A Dynamics 365 Customer Insights próbaverziója segítségével áttekintheti a legfontosabb szolgáltatásokat, és többet megtudhatja a különböző szolgáltatásokról. A próbaelőfizetés a lejárat után törlődik. A próbakörnyezetet olyan egyéni felhasználók hozzák létre, akik a próbakörnyezet rendszergazdáivá válnak. Több felhasználót is meghívhatnak a próbaverzióra, és konfigurálhatja a különböző szolgáltatásokat.

## <a name="create-a-trial-environment"></a>Próbakörnyezet létrehozása

A próbaverzióra való feliratkozást a [próbaverzió regisztrációs oldalon](https://dynamics.microsoft.com/get-started/free-trial/?appname=customerinsights) teheti meg. 

1. Válassza ki a **Feliratkozás egy ingyenes próbára** lehetőséget, és válassza a **Feliratkozás most** lehetőséget.

1. Adja meg munkahelyi vagy iskolai e-mail címét, írjon be többet saját magával kapcsolatban, és válassza az **Első lépések** lehetőséget.

   :::image type="content" source="media/trial-signup-dialog.png" alt-text="Párbeszédpanel a próbapéldány regisztrációjához":::

1. Tekintse át a felhasználási feltételeket, majd kattintson az **Megerősítés** lehetőségre a megerősítéshez.

1. Adja meg az új környezet **nevét**. 

1. Állítsa be a környezet **Típust** **Próbaverzió** értékre.

1. Az **Iparág bemutató kiválasztása** mezőben tetszés szerint választhat egy iparág-specifikus adatkészletet. Később is [válthat iparági bemutatóra](#use-industry-specific-demo-data-sets-in-audience-insights), és kezdhet az alapértelmezett adatkészlettel.

1. Válasszon **régiót** a környezethez.

1. Opcionálisan, ha Ön Egy Dynamics 365-szervezet rendszergazdája: Válassza a **Speciális beállítások** lehetőséget, és adja meg a szervezet URL-címét az olyan előrejelzési funkciók használatához, mint például az ügyfelek elvándorlásának előrejelzése. 

1. Válassza a **Létrehozás** parancsot. 

A környezet beállításának végrehajtása néhány percig tart. A befejezést követően a rendszer átirányítja a bemutató környezetre vagy a fenti lépésben választott iparági bemutatóra. Most már megismerheti az alkalmazást csak olvasható bemutató adatokkal. Ha saját adatokat szeretne felvenni a környezetbe, akkor tekintse meg a [Forgatókönyv-specifikus bemutató adatok létrehozása a saját környezetben](#create-scenario-specific-demo-data-in-your-own-environment) részt.

:::image type="content" source="media/trial-environment.png" alt-text="Képernyőkép az újonnan létrehozott próbakörnyezetről.":::

## <a name="use-industry-specific-demo-data-sets-in-audience-insights"></a>Iparág-specifikus bemutatóadatkészletek használata a célközönség-információkban

A valódi adatforrások kapcsolása a Customer Insights rendszer teljesítménye kihasználásának egyik alapvető lépése. Ha a szolgáltatásokat a saját adataival való interferencia szeretné kipróbálni, akkor az iparágspecifikus bemutatóadatokat is használhatja. Néhány bemutatóadatkészlet áll rendelkezésre a következő iparágak számára: 

-   Automatizálás
-   Bank
-   Fogyasztási cikkek
-   Kormányzat
-   Egészségügy
-   Vendéglátás
-   Biztosítás
-   Termelés
-   Szakmai szolgáltatások
-   Kiskereskedelem

### <a name="see-industry-specific-demo-data-in-trials"></a>Iparágspecifikus bemutatóadatok megtekintése a próbaverziókban

A Customer Insights csak olvasható, adott iparághoz vagy forgatókönyvhöz igazított verziójához indítsa el a bemutatókörnyezetet. 
 
1.  Az célközönség-információkban válassza a **Bemutató** környezetet a környezetválasztóban.

2.  A **Kezdőlapon** válassza az Iparági bemutató kiválasztása legördülő menüjének egyik lehetőségét.

:::image type="content" source="media/trial-select-industry-demo.png" alt-text="Válasszon iparágat a próbakörnyezethez.":::

### <a name="create-scenario-specific-demo-data-in-your-own-environment"></a>Forgatókönyv-specifikus bemutatóadatok létrehozása a saját környezetében

Rendszergazdaként válassza ki az alkalmazásfejlécben a környezetválasztót, és hozzon létre egy új környezetet. Az új környezetben konfigurálhatja saját adatforrásait, és az alkalmazást az igényeinek megfelelően állítsa be. 

1.  A célközönség információin belül nyissa meg a következőt **Adatok** > **Adatforrások**.

2.  Saját adatforrások importálása esetén tekintse meg az [adatbetöltési útmutatót](data-sources.md).     
   Ha szívesebben dolgozik olyan mintaadatokkal, amelyek lehetővé teszi, hogy kipróbálja az adatbetöltést, akkor az iparág bemutató adatait a környezetébe betöltheti. Válassza az **Importálás a Datahub szolgáltatásból** lehetőséget, és hajtsa végre az alábbi lépéseket.

3.  Válassza ki az esetnek megfelelő iparági kártyát. 

4.  Tekintse át, majd tetszés szerint frissítse a adatforrás javasolt nevét. 

5.  Válassza a **tovább** lehetőséget a mintaadatok betöltéséhez. 

Immár használhatja a betöltött adatokat, hogy a Customer Insights alkalmazást a saját forgatókönyvéhez szabja. Ha a betöltött bemutatóadatokhoz specifikus környezetet szeretne látni, válassza a környezetválasztóban az **<Industry> Bemutató** lehetőséget.

## <a name="limitations-in-trials"></a>Próbaverziókra vonatkozó korlátozások

- A próbaverziók alapértelmezés szerint 30 napig aktívak. A próbaverzióba való bejelentkezéskor azonban a 23. nap után meghosszabíthatja azokat.
- A saját Azure Data Lake Storage-fiókja nem használható a kimeneti adatok tárolására a próbaidőszak során. Azonban betölthet adatokat a Data Lake tárfiókból.
- A Customer Insights próbaverziója indításakor 3 GB adat tárolható a Dataverse környezetben, amely automatikusan ki van építve.

## <a name="copy-data-from-a-trial-to-a-paid-subscription"></a>Adatok másolása próbaverzióból fizetett előfizetésbe

Általában javasoljuk, hogy a Customer Insights fizetett verziójára való frissítéskor elölről kezdje a saját adataival. 

Ha megvásárolja a Customer Insightsot, akkor másik lehetőségként a próbakörnyezetből is másolhatja az adatokat. Önnek kell a Customer Insights próbaverzió rendszergazdájának és a Microsoft 365-bérlő globális rendszergazdájának vagy a szervezet Dynamics 365 rendszergazdájának lennie ahhoz, hogy a beállításokat a próbakörnyezetből fizetett környezetbe át tudja telepíteni. 

Miután először bejelentkezett a Customer Insights fizetett példányába, a rendszer kéri, hogy hozzon létre egy új környezetet. Ebben a folyamatban megadhatja, hogy a konfigurációt egy meglévő környezetből másolja át, és a beállítások nagy részét áttelepíti. Ha rendelkezik a fenti jogosultságokkal, akkor a próbakörnyezet megjelenik ebben a listában. További információ: [Környezetkonfiguráció másolása](manage-environments.md#copy-the-environment-configuration).

## <a name="next-steps"></a>További lépések

Az alábbi cikkekből segítséget kaphat a Customer Insights konfigurálásával való megismerkedéshez. 

- [Adjon hozzá további felhasználókat, és rendeljen hozzá engedélyeket](permissions.md).
- [Töltse be az adatforrásait](data-sources.md), és futtassa azokat az [adategyesítési folyamaton](data-unification.md) keresztül, hogy [egyesített ügyfélprofilokat](customer-profiles.md) kapjon.
- [Bővítse az egységes ügyfélprofilokat](enrichment-hub.md), vagy futtasson [prediktív modelleket](predictions-overview.md).
- Hozzon létre [szegmenseket](segments.md) az ügyfelek és [mértékek](measures.md) csoportosítása és a teljesítménymutatók áttekintésének értékelése érdekében.
- Állítson be [kapcsolatokat](connections.md) és [exportálásokat](export-destinations.md) az adatok bizonyos részhalmazának más alkalmazásokban történő feldolgozásához.