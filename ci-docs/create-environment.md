---
title: Hogyan hozzunk létre egy új környezetet
description: Környezetek létrehozásának lépései a következővel:Dynamics 365 Customer Insights.
ms.date: 05/31/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: mukeshpo
ms.author: mukeshpo
manager: shellyha
ms.custom: intro-internal
searchScope:
- ci-home
- customerInsights
ms.openlocfilehash: 795eaa3598257f5188070f6ea02d04e4423b66eb
ms.sourcegitcommit: f5af5613afd9c3f2f0695e2d62d225f0b504f033
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/01/2022
ms.locfileid: "8833561"
---
# <a name="how-to-create-a-new-environment"></a>Hogyan készítsünk új környezetet

Miután [előfizetési licencet vásárolt, Dynamics 365 Customer Insights](paid-license.md) a bérlő globális rendszergazdája Microsoft 365 e-mailt kap, amely meghívja őket a környezet létrehozására. A kezdéshez ugorjon a [https://home.ci.ai.dynamics.com/start](https://home.ci.ai.dynamics.com/start) weboldalra. Ebben a forgatókönyvben közvetlenül az 1. lépésre [léphet: Alapvető információk megadása](#step-1-provide-basic-information).

Az első környezet létrehozása után a bérlő globális rendszergazdája rendszergazdaként hozzáadhat Microsoft 365 felhasználókat a [szervezetükhez](permissions.md). A jövőben ezek a rendszergazdák kezelhetik a felhasználókat és a környezeteket. Ha szervezete egynél több licencet vásárol a Customer Insights számára, [vegye fel a kapcsolatot ügyfélszolgálatunkkal](https://go.microsoft.com/fwlink/?linkid=2079641) az elérhető környezetek számának növelése érdekében. A kapacitással és a kiegészítő kapacitással kapcsolatos további információkért tekintse meg a [Dynamics 365 licencelési útmutatóját](https://go.microsoft.com/fwlink/?LinkId=866544).

> [!TIP]
> Ha a szolgáltatást próbálja ki, akkor tekintse meg a [Próbakörnyezet beállítása](trial-signup.md) részt.

## <a name="prerequisites"></a>Előfeltételek

A környezetek létrehozásához és kezeléséhez rendszergazdai [engedélyekre van szükség](permissions.md) a Customer Insights alkalmazásban.

## <a name="start-the-environment-creation-process"></a>A környezetteremtési folyamat elindítása

1. Nyissa meg a környezetválasztót, és válassza a + Új **lehetőséget**.
  
   :::image type="content" source="media/environment-picker.png" alt-text="Környezetválasztó kiválasztása.":::

1. Kövesse a következő szakaszokban ismertetett interaktív tapasztalatokat, hogy minden szükséges információt megadjon egy új környezethez. Ha korábban konfigurált egy környezetet, átmásolhatja a konfigurációt [is](#copy-the-environment-configuration).

## <a name="step-1-provide-basic-information"></a>1. lépés: Alapvető információk megadása

Az **Alapinformáció** lépésben válassza ki, hogy nulláról hoz-e létre környezetet, vagy [más környezetből szeretne adatokat másolni](#copy-the-environment-configuration).

   :::image type="content" source="media/environment-settings-dialog.png" alt-text="Párbeszédpanel az új Customer Insights-környezet létrehozásához.":::

Adja meg a következő részleteket:

- **Név**: A környezet neve. Ha meglévő környezetből másolt, akkor ez a mező már ki van töltve, de ez módosítható.
- **Válassza ki a vállalkozását**: Válassza ki az elsődleges közönséget az új környezethez. Dolgozhat egyéni ügyfelekkel (B-to-C) vagy [üzleti fiókokkal](work-with-business-accounts.md) (B-to-B). Ha szervezete elsősorban magánszemélyekkel, például kiskereskedővel vagy kávézóval foglalkozik, válasszon egyéni fogyasztókat. Abban az esetben, ha a fő célközönség más vállalatok, például egy autógyártó vagy egy papírgyártó, válasszon üzleti számlákat.
- **Típus**: Adja meg, hogy szeretne-e termelési vagy tesztkörnyezetet létrehozni. A tesztkörnyezetek nem engedélyezik az ütemezett adatfrissítést, és előzetes megvalósításhoz és teszteléshez kínáljuk ezeket. A tesztkörnyezet környezetek ugyanazt az célközönség elsődleges környezetként használják, mint az éppen kijelölt éles környezet.
- **Régió**: Az a régió, ahová a szolgáltatást telepítették és üzemeltetik. Saját [fiók Azure Data Lake Storage használatához vagy](own-data-lake-storage.md) meglévő [szervezethez Microsoft Dataverse való csatlakozáshoz](customer-insights-dataverse.md) a Customer Insights környezetnek ugyanabban a régióban kell lennie.

## <a name="step-2-configure-data-storage"></a>2. lépés: Az adattárolás konfigurálása

**Az Adattárolási** lépésben válassza ki, hogy hol tárolja az Ügyfélelemzési adatokat.

Két lehetőség közül választhat:

- **Customer Insights storage**: Az adattárolást a Customer Insights csapata kezeli. Ez az alapértelmezett beállítás, és hacsak nincsenek speciális követelmények az adatok tárolására a saját tárfiókjában, javasoljuk, hogy használja ezt a lehetőséget.
- **Azure Data Lake Storage**: Adja meg saját Azure Data Lake Storage fiókját az adatok tárolására, így teljes mértékben szabályozhatja, hogy hol tárolják az adatokat. További információt a Saját [fiók Azure Data Lake Storage használata című témakörben talál](own-data-lake-storage.md).

:::image type="content" source="media/data-storage-environment.png" alt-text="Válassza ki az adatok tárolására előnyben részesített lehetőséget.":::

## <a name="step-3-connect-to-microsoft-dataverse"></a>3. lépés: Csatlakozás a Microsoft Dataverse-hez

A **Microsoft Dataverse** lépéssel összekapcsolhatja a Customer Insightsot a Dataverse környezetével. Ossza meg az adatokat a Dataverse használatával az üzleti alkalmazásokkal Dataverse, például a Dynamics 365 Marketing vagy a modellvezérelt alkalmazásokkal a alkalmazásban Power Apps.

Hagyja üresen ezt a mezőt, ha nincs saját Dataverse környezete, és létrehozunk egyet az Ön számára.

További információt a Customer Insights-adatok használata a alkalmazásban [című témakörben talál Microsoft Dataverse](customer-insights-dataverse.md).

:::image type="content" source="media/dataverse-provisioning.png" alt-text="adatmegosztás automatikus engedélyezve van Microsoft Dataverse az új, netes környezetekhez.":::

### <a name="step-4-finalize-the-settings"></a>4. lépés: A beállítások véglegesítése

**A Felülvizsgálat** lépésben tekintse át az összes megadott beállítást. Ha minden befejeződött, válassza a **Létrehozás** lehetőséget a környezet beállításáhez.

Néhány beállítást később módosíthat. További tudnivalókért lásd: [Környezetek kezelése](manage-environments.md).

## <a name="work-with-your-new-environment"></a>Az új környezettel való munka

A következő cikkekből segítséget kaphat a Customer Insights konfigurálásának első lépéseihez:

- [Adjon hozzá további felhasználókat, és rendeljen hozzá engedélyeket](permissions.md).
- [Töltse be az adatforrásait](data-sources.md), és futtassa azokat az [adategyesítési folyamaton](data-unification.md) keresztül, hogy [egyesített ügyfélprofilokat](customer-profiles.md) kapjon.
- [Bővítse az egységes ügyfélprofilokat](enrichment-hub.md), vagy futtasson [prediktív modelleket](predictions-overview.md).
- [Hozzon létre szegmenseket](segments.md) az ügyfelek és a [mértékek](measures.md) csoportosításához és a teljesítménymutatók áttekintéséhez.
- [Állítson be kapcsolatokat](connections.md) és [exportálásokat](export-destinations.md) az adatok bizonyos részhalmazának más alkalmazásokban történő feldolgozásához.

## <a name="copy-the-environment-configuration"></a>Másolja a környezet konfigurációját

Rendszergazdaként dönthet úgy, hogy a konfigurációt egy meglévő környezetből másolja, amikor újat hoz létre.

:::image type="content" source="media/environment-settings-dialog.png" alt-text="Képernyőkép a beállítási lehetőségekről a környezet beállításaiban.":::

A szervezetében összes elérhető környezet listáját látja, amelyekből adatokat másolhat.

A következő konfigurációbeállítások vannak másolva:

- A következőn keresztül importált adatforrások Power Query
- Adategyesítési konfiguráció
- Szegmensek
- Mértékek
- Kapcsolatok
- Tevékenységek
- Keresési és szűrőindex
- Exportálások
- Ütemezés frissítése
- Bővítések
- Előrejelzés modellek
- Szerepkör-hozzárendelések

## <a name="set-up-a-copied-environment"></a>Másolt környezet beállítása

A környezetkonfiguráció másolásakor néhány további lépést kell végrehajtania a hitelesítő adatok megerősítéséhez:

- Ügyfélprofilok. Először hitelesítse és töltse be az adatforrásokat, és futtassa az adategyesítést az ügyfélprofilok újbóli létrehozásához.
- Adatforrás hitelesítő adatai. Az adatforrások manuális hitelesítéséhez és frissítéséhez minden adatforrás meg kell adnia a hitelesítő adatokat.
- Adatforrások a Common Data Model mappából és Dataverse a rendszerből. Ezeket az adatforrásokat manuálisan kell létrehoznia ugyanazzal a névvel, mint a forráskörnyezetben.
- Az exportáláshoz és a gazdagodáshoz használt kapcsolati titkok. Újra kell engedélyeznie a kapcsolatokat, majd újra aktiválnia kell a gazdagodásokat és az exportálást.

A másolt környezet létrehozásakor egy megerősítő üzenet jelenik meg. Válassza az **Ugrás az adatforrásokhoz** lehetőséget az adatforrások listájának megjelenítéséhez.

Minden adatforrásnál megjelenik egy **Hitelesítő adatok szükségesek** állapot. Szerkessze az adatforrásokat, és adja meg a hitelesítő adatokat a frissítésükhöz.

:::image type="content" source="media/data-sources-copied.png" alt-text="A másolt és hitelesítést igényel adatforrások listája.":::

Az adatforrások frissítését követően nyissa meg az **Adatok** > **Egyesítés** pontot. Itt megtalálja a beállításokat a forráskörnyezetből. Igény szerint szerkessze őket, vagy válassza a **Futtatás** lehetőséget az adategyesítési folyamat elindításához, és hozzon létre egy egyesített ügyfélentitást.

Amikor az adatok egyesítése befejeződött, nyissa meg a **Mértékek** és a **Szegmensek** lehetőséget, hogy azokat is frissítse.

Az exportálások és a gazdagítások újraaktiválása előtt nyissa meg a **Felügyeleti** > **kapcsolatok lehetőséget** az új környezetben lévő kapcsolatok újbóli hitelesítéséhez.

[!INCLUDE [footer-include](includes/footer-banner.md)]
