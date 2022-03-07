---
title: A Customer Insights alkalmazásban létrehozott környezetek
description: A Dynamics 365 Customer Insights licencelt előfizetéssel rendelkező környezetek létrehozására vonatkozó lépések.
ms.date: 02/24/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: MichelleDevaney
ms.author: midevane
manager: shellyha
ms.custom: intro-internal
searchScope:
- ci-home
- customerInsights
ms.openlocfilehash: c37afd5649f8cf40d5379f3d39d0cbd96cde3bd3
ms.sourcegitcommit: 73cb021760516729e696c9a90731304d92e0e1ef
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/25/2022
ms.locfileid: "8354098"
---
# <a name="create-an-environment-in-audience-insights"></a>Hozzon létre egy környezetet a közönséggel kapcsolats információkban

Ez a cikk azt mutatja be, hogyan lehet új környezetet létrehozni azt követően, hogy a szervezete megvásárolt egy Dynamics 365 Customer Insights előfizetést. 

A szervezetek minden Customer Insights licenchez *két* környezetet hozhatnak létre. Ha a szervezete több licencet vásárol, a rendelkezésre álló környezetek számának növelése érdekében [forduljon a támogatási csoportunkhoz](https://go.microsoft.com/fwlink/?linkid=2079641). A kapacitással és a bővítménykapacitással kapcsolatos további információkért töltse le a [Dynamics 365 licencelési útmutatóját](https://go.microsoft.com/fwlink/?LinkId=866544).

> [!NOTE]
> Ha a szolgáltatást próbálja ki, akkor tekintse meg a [Próbakörnyezet beállítása](../trial-signup.md) részt.

## <a name="create-a-new-environment"></a>Új környezet létrehozása

A Customer Insights előfizetési licencének megvásárlása után a Microsoft 365 bérlő globális rendszergazdája e-mailt kap, amely meghívja őket a környezet létrehozására. A kezdéshez ugorjon a [https://home.ci.ai.dynamics.com/start](https://home.ci.ai.dynamics.com/start) weboldalra. 

Az interaktív élmény végigvezeti az új környezettel kapcsolatos összes szükséges információgyűjtés lépéseit. A környezetek létrehozásához célközönség környezetek kezeléséhez [rendszergazdai engedélyekre](permissions.md) van szüksége.

1. A célközönség nyissa meg a környezetválasztót, és válassza a **+ Új** lehetőséget.
  
   :::image type="content" source="../engagement-insights/media/environment-picker.png" alt-text="Környezetválasztó kiválasztása.":::

1. Kövesse a következő részekben ismertetett interaktív élményt.

### <a name="step-1-provide-environment-information"></a>1. lépés: Környezetinformációk szolgáltatása

Az **Alapinformáció** lépésben válassza ki, hogy nulláról hoz-e létre környezetet, vagy [más környezetből szeretne adatokat másolni](manage-environments.md#copy-the-environment-configuration).

   :::image type="content" source="media/environment-settings-dialog.png" alt-text="Párbeszédpanel az új Customer Insights-környezet létrehozásához.":::

Adja meg a következő részleteket:
   - **Név**: A környezet neve. Ha meglévő környezetből másolt, akkor ez a mező már ki van töltve, de ez módosítható.
   - **Válassza ki a vállalkozását**: Válassza ki az elsődleges közönséget az új környezethez. Dolgozhat egyéni ügyfelekkel (B-to-C) vagy [üzleti fiókokkal](work-with-business-accounts.md) (B-to-B).
   - **Típus**: Adja meg, hogy szeretne-e termelési vagy tesztkörnyezetet létrehozni. A tesztkörnyezetek nem engedélyezik az ütemezett adatfrissítést, és előzetes megvalósításhoz és teszteléshez kínáljuk ezeket. A tesztkörnyezet környezetek ugyanazt az célközönség elsődleges környezetként használják, mint az éppen kijelölt éles környezet.
   - **Régió**: Az a régió, ahová a szolgáltatást telepítették és üzemeltetik.

### <a name="step-2-configure-data-storage"></a>2. lépés: Az adattárolás konfigurálása

Az **Adattárolási** lépésben válassza ki, hogy hová tárolja az adatokat a célközönség információkból.

Két lehetőség közül választhat: **Customer Insights-tár** (a Customer Insights-csapat által kezelt Azure-adattó) vagy **Azure Data Lake Storage** (saját Azure Data Lake Storage). Alapértelmezés szerint a Customer Insights tárolóhely beállítás van kiválasztva.

:::image type="content" source="media/data-storage-environment.png" alt-text="Válassza az Azure Data Lake Storage szolgáltatást, hogy melyikben tárolja célközönséggel kapcsolatos információk adatait.":::

A rendszer az adatok Azure Data Lake Storage szolgáltatásba való mentésével hozzájárul, hogy a rendszer az adott Azure-tárfiók megfelelő földrajzi helyére továbbítja az adatokat, és abban tárolja el őket. Ez a hely eltérhet attól, hogy az adatokat hol tárolja Dynamics 365 Customer Insights szolgáltatásban. További információ a [Microsoft adatvédelmi központró](https://www.microsoft.com/trust-center).

> [!NOTE]
> A Customer Insights jelenleg a következőket támogatja:
> - A Microsoft Dataverse által felügyelt Data Lake-ben tárolt Power BI adatfolyamokból származó feldolgozott entitások.  
> - Azure Data Lake Storage partnereknek ugyanabban az Azure-régióban, mint amit a környezet létrehozásakor kiválasztott.
> - Azure Data Lake Storage gen2 fiókok, amelyek *hierarchikus névterét* engedélyezve. Az Azure Data Lake Gen1 tárfiókok nem támogatottak.

A Azure Data Lake Storage beállításhoz választhat az erőforrás-alapú és az előfizetés-alapú hitelesítési lehetőség között. További információ a [Kapcsolódás Azure Data Lake Storage-fiókhoz Azure-szolgáltatásnévvel](connect-service-principal.md) című cikkben található. A **Tároló** neve `customerinsights` értékre változik, és nem módosítható.

Amikor befejeződnek a rendszerfolyamatok, például az adatok betöltése, a rendszer a megfelelő mappákat hozza létre a megadott tárfiókban. Az adatfájlok és a *model.json* fájlok a folyamat neve alapján jönnek létre, és kerülnek a mappákba.

Ha a Customer Insights több környezetét hozza létre, és úgy dönt, hogy az ilyen környezetek kimeneti entitásokat menti a tárfiókba, akkor a Customer Insights külön mappákat hoz létre az egyes környezetekhez, amelyek a `ci_environmentID` értékkel találhatók a tárolóban.

### <a name="step-3-connect-to-microsoft-dataverse"></a>3. lépés: Csatlakozás a Microsoft Dataverse-hez
   
A **Microsoft Dataverse** lépéssel összekapcsolhatja a Customer Insightsot a Dataverse környezetével.

Biztosítsa saját Microsoft Dataverse környezetét az adatok (profilok és elemzések) megosztásához a, például a Dynamics 365 Marketing vagy a modellvezérelt alkalmazások alapján Dataverse Power Apps. Hagyja üresen ezt a mezőt, ha nincs saját Dataverse környezete, és mi kiépítünk önnek egyet.

A környezethez Dataverse való csatlakozás lehetővé teszi [az adatforrások helyszíni adatainak beolvasását is adatfolyamok és átjárók Power Platform használatával](data-sources.md#add-data-from-on-premises-data-sources). A környezethez [való csatlakozással beépített előrejelzés modelleket](predictions-overview.md?tabs=b2c#out-of-box-models) is használhat Dataverse.

> [!IMPORTANT]
> A Customer Insights-nak Dataverse ugyanabban a régióban kell lennie az adatmegosztás engedélyezéséhez.

:::image type="content" source="media/dataverse-provisioning.png" alt-text="adatmegosztás automatikus engedélyezve Microsoft Dataverse a net új példányok esetén.":::

> [!NOTE]
> A Customer Insights nem támogatja a következő adatmegosztási forgatókönyveket:
> - Ha az összes adatot a saját Azure Data Lake Storage szolgáltatásához menti, akkor nem tudja engedélyezni az adatmegosztást a kezelt Dataverse-adattóval.
> - Ha engedélyezi az adatmegosztást a Dataverse szolgáltatással, akkor nem fogja tudni [létrehozni az előrejelzett vagy hiányzó értékeket egy entitásban](predictions.md).

### <a name="step-4-finalize-the-settings"></a>4. lépés: A beállítások véglegesítése

Az **Ellenőrzés** lépésben menjen végig az összes megadott beállításon. Ha minden befejeződött, válassza a **Létrehozás** lehetőséget a környezet beállításáhez. 

A beállítások nagy része később is megváltoztatható. További tudnivalókért lásd: [Környezetek kezelése](manage-environments.md).

## <a name="work-with-your-new-environment"></a>Az új környezettel való munka

A következő cikkekből segítséget kaphat a Customer Insights konfigurálásának első lépéseihez: 

- [Adjon hozzá további felhasználókat, és rendeljen hozzá engedélyeket](permissions.md).
- [Töltse be az adatforrásait](data-sources.md), és futtassa azokat az [adategyesítési folyamaton](data-unification.md) keresztül, hogy [egyesített ügyfélprofilokat](customer-profiles.md) kapjon.
- [Bővítse az egységes ügyfélprofilokat](enrichment-hub.md), vagy futtasson [prediktív modelleket](predictions-overview.md).
- [Hozzon létre szegmenseket](segments.md) az ügyfelek és a [mértékek](measures.md) csoportosításához és a teljesítménymutatók áttekintéséhez.
- [Állítson be kapcsolatokat](connections.md) és [exportálásokat](export-destinations.md) az adatok bizonyos részhalmazának más alkalmazásokban történő feldolgozásához.
