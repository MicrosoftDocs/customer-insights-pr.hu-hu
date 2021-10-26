---
title: A Customer Insights alkalmazásban létrehozott környezetek
description: A Dynamics 365 Customer Insights licencelt előfizetéssel rendelkező környezetek létrehozására vonatkozó lépések.
ms.date: 10/14/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: MichelleDevaney
ms.author: midevane
manager: shellyha
ms.custom: intro-internal
ms.openlocfilehash: 95afd1fedb98a451e4978ee66be2ea98ad7a4a76
ms.sourcegitcommit: 53b133a716c73cb71e8bcbedc6273cec70ceba6c
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/15/2021
ms.locfileid: "7645696"
---
# <a name="create-an-environment-in-audience-insights"></a>Hozzon létre egy környezetet a közönséggel kapcsolats információkban

Ez a cikk azt mutatja be, hogyan lehet új környezetet létrehozni azt követően, hogy a szervezete megvásárolt egy Dynamics 365 Customer Insights előfizetést. 

A szervezetek minden Customer Insights licenchez *két* környezetet hozhatnak létre. Ha a szervezete több licencet vásárol, a rendelkezésre álló környezetek számának növelése érdekében [forduljon a támogatási csoportunkhoz](https://go.microsoft.com/fwlink/?linkid=2079641). A kapacitással és a bővítménykapacitással kapcsolatos további információkért töltse le a [Dynamics 365 licencelési útmutatóját](https://go.microsoft.com/fwlink/?LinkId=866544).

> [!NOTE]
> Ha a szolgáltatást próbálja ki, akkor tekintse meg a [Próbakörnyezet beállítása](../trial-signup.md) részt.

## <a name="create-a-new-environment"></a>Új környezet létrehozása

Miután megvásárolta a Customer Insights előfizetéses licencét, a Microsoft 365 bérlő globális rendszergazdája kap egy e-mailt, amely meghívja őt a környezet létrehozására. A kezdéshez ugorjon a [https://home.ci.ai.dynamics.com/start](https://home.ci.ai.dynamics.com/start) weboldalra. 

Az interaktív élmény végigvezeti az új környezettel kapcsolatos összes szükséges információgyűjtés lépéseit. A környezetek létrehozásához célközönség környezetek kezeléséhez [rendszergazdai engedélyekre](permissions.md) van szüksége.

1. A célközönség nyissa meg a környezetválasztót, és válassza a **+ Új** lehetőséget.
  
   :::image type="content" source="../engagement-insights/media/environment-picker.png" alt-text="Környezetválasztó kiválasztása.":::

1. Kövesse a következő részekben ismertetett interaktív élményt.

### <a name="step-1-provide-environment-information"></a>1. lépés: Környezetinformációk szolgáltatása

Az **Alapinformáció** lépésben válassza ki, hogy nulláról hoz-e létre környezetet, vagy [más környezetből szeretne adatokat másolni](manage-environments.md#copy-the-environment-configuration).

   :::image type="content" source="media/environment-settings-dialog.png" alt-text="Párbeszédpanel az új Customer Insights-környezet létrehozásához.":::

Adja meg a következő részleteket:
   - **Név**: A környezet neve. Ha meglévő környezetből másolt, akkor ez a mező már ki van töltve, de ez módosítható.
   - **Válasszon vállalkozást**: Válassza ki az célközönség elsődleges elemét. Az egyes ügyfelekkel (B2C) és [üzleti fiókokkal](work-with-business-accounts.md) (B2B) is dolgozhat.
   - **Típus**: Adja meg, hogy szeretne-e termelési vagy tesztkörnyezetet létrehozni. A tesztkörnyezetek nem engedélyezik az ütemezett adatfrissítést, és előzetes megvalósításhoz és teszteléshez kínáljuk ezeket. A tesztkörnyezet környezetek ugyanazt az célközönség elsődleges környezetként használják, mint az éppen kijelölt éles környezet.
   - **Régió**: Az a régió, ahová a szolgáltatást telepítették és üzemeltetik.

### <a name="step-2-configure-data-storage"></a>2. lépés: Az adattárolás konfigurálása

Az **Adattárolási** lépésben válassza ki, hogy hová tárolja az adatokat a célközönség információkból.

Két lehetősége lesz: **Ügyfélelemzések tárolása** (a Customer Insights csapat által kezelt Azure Data Lake) és **Azure Data Lake Storage** (saját Azure Data Lake Storage). Alapértelmezés szerint a Customer Insights tárolóhely beállítás van kiválasztva.

:::image type="content" source="media/data-storage-environment.png" alt-text="Válassza az Azure Data Lake Storage szolgáltatást, hogy melyikben tárolja célközönséggel kapcsolatos információk adatait.":::

A rendszer az adatok Azure Data Lake Storage szolgáltatásba való mentésével hozzájárul, hogy a rendszer az adott Azure-tárfiók megfelelő földrajzi helyére továbbítja az adatokat, és abban tárolja el őket. Ez a hely eltérhet attól, hogy az adatokat hol tárolja Dynamics 365 Customer Insights szolgáltatásban. További információ a [Microsoft adatvédelmi központró](https://www.microsoft.com/trust-center).

> [!NOTE]
> A Customer Insights jelenleg a következőket támogatja:
> - A Microsoft Dataverse által felügyelt Data Lake-ben tárolt Power BI adatfolyamokból származó feldolgozott entitások.  
> - Azure Data Lake Storage partnereknek ugyanabban az Azure-régióban, mint amit a környezet létrehozásakor kiválasztott.
> - Azure Data Lake Storage-partnerek, amelyek *hierarchikus névtér* engedélyezve vannak.

A Azure Data Lake Storage beállításhoz választhat az erőforrás-alapú és az előfizetés-alapú hitelesítési lehetőség között. További információkért lásd: [Célközönség-információk összekapcsolása az Azure Data Lake Storage Gen2 fiókjához az Azure egyszerű szolgáltatásnévvel](connect-service-principal.md). A **Tároló** neve `customerinsights` értékre változik, és nem módosítható.

Amikor befejeződnek a rendszerfolyamatok, például az adatok betöltése, a rendszer a megfelelő mappákat hozza létre a megadott tárfiókban. Az adatfájlok és a *model.json* fájlok a folyamat neve alapján jönnek létre, és kerülnek a mappákba.

Ha a Customer Insights több környezetét hozza létre, és úgy dönt, hogy az ilyen környezetek kimeneti entitásokat menti a tárfiókba, akkor a Customer Insights külön mappákat hoz létre az egyes környezetekhez, amelyek a `ci_environmentID` értékkel találhatók a tárolóban.

### <a name="step-3-connect-to-microsoft-dataverse"></a>3. lépés: Csatlakozás a Microsoft Dataverse-hez
   
A **Microsoft Dataverse** lépéssel összekapcsolhatja a Customer Insightsot a Dataverse környezetével.

A [használható előrejelzési modellek](predictions-overview.md#out-of-box-models) használatra konfigurálja az adatok megosztását a Dataverse használatával. Vagy engedélyezheti az adatfeldolgozást a helyszíni adatforrásokból, megadva a szervezet által felügyelt Microsoft Dataverse környezet URL-címét. Válassza az **Adatmegosztás engedélyezése** lehetőséget, ha meg szeretné osztani a Customer Insights kimeneti adatait a Dataverse Managed Data Lake használatával.

:::image type="content" source="media/dataverse-data-sharing.png" alt-text="Konfigurálási lehetőségek az adatmegosztás engedélyezéséhez a Microsoft Dataverse szolgáltatással.":::

> [!NOTE]
> A Customer Insights nem támogatja a következő adatmegosztási forgatókönyveket:
> - Ha az összes adatot a saját maga Azure Data Lake Storage szolgáltatásához menti, akkor nem tudja engedélyezni az adatmegosztást a Microsoft Dataverse Managed Data Lake szolgáltatással.
> - Ha engedélyezi az adatmegosztást a Microsoft Dataverse Managed Data Lake szolgáltatással, akkor nem fogja tudni [létrehozni az előre jelzett vagy hiányzó értékeket egy entitásban](predictions.md).

### <a name="step-4-finalize-the-settings"></a>4. lépés: A beállítások véglegesítése

Az **Ellenőrzés** lépésben menjen végig az összes megadott beállításon. Ha minden befejeződött, válassza a **Létrehozás** lehetőséget a környezet beállításáhez. 

A beállítások nagy része később is megváltoztatható. További tudnivalókért lásd: [Környezetek kezelése](manage-environments.md).

## <a name="work-with-your-new-environment"></a>Az új környezettel való munka

Az alábbi cikkekből segítséget kaphat a Customer Insights konfigurálásával való megismerkedéshez. 

- [Adjon hozzá további felhasználókat, és rendeljen hozzá engedélyeket](permissions.md).
- [Töltse be az adatforrásait](data-sources.md), és futtassa azokat az [adategyesítési folyamaton](data-unification.md) keresztül, hogy [egyesített ügyfélprofilokat](customer-profiles.md) kapjon.
- [Bővítse az egységes ügyfélprofilokat](enrichment-hub.md), vagy futtasson [prediktív modelleket](predictions-overview.md).
- [Hozzon létre szegmenseket](segments.md) az ügyfelek és a [mértékek](measures.md) csoportosítása és a teljesítménymutatók áttekintésének értékelése érdekében.
- [Állítson be kapcsolatokat](connections.md) és [exportálásokat](export-destinations.md) az adatok bizonyos részhalmazának más alkalmazásokban történő feldolgozásához.
