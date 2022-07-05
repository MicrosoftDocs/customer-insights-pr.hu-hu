---
title: 'Útmutató: Új környezet létrehozása'
description: A környezetek létrehozásának lépései Dynamics 365 Customer Insights.
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
ms.openlocfilehash: 62969527ceed906ff06fb9be90b972496323ce0a
ms.sourcegitcommit: a97d31a647a5d259140a1baaeef8c6ea10b8cbde
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/29/2022
ms.locfileid: "9052748"
---
# <a name="how-to-create-a-new-environment"></a>Útmutató: Új környezet létrehozása

Miután [megvásárolta az Dynamics 365 Customer Insights](paid-license.md) előfizetési licencet, a bérlő globális rendszergazdája Microsoft 365 kap egy e-mailt, amely meghívja őket a környezet létrehozására. A kezdéshez ugorjon a [https://home.ci.ai.dynamics.com/start](https://home.ci.ai.dynamics.com/start) weboldalra. Ebben a forgatókönyvben közvetlenül az 1. lépés: Alapvető információk megadása című szakaszra [léphet](#step-1-provide-basic-information).

Az első környezet létrehozása után a bérlő globális rendszergazdája rendszergazdaként adhat Microsoft 365 hozzá felhasználókat a [szervezetükből](permissions.md). A továbbiakban ezek a rendszergazdák kezelhetik a felhasználókat és a környezeteket. Ha szervezete egynél több licencet vásárol a Customer Insights szolgáltatáshoz, [vegye fel a kapcsolatot ügyfélszolgálatunkkal](https://go.microsoft.com/fwlink/?linkid=2079641) az elérhető környezetek számának növelése érdekében. A kapacitással és a kiegészítő kapacitással kapcsolatos további információkért tekintse át a [Dynamics 365 licencelési útmutatóját](https://go.microsoft.com/fwlink/?LinkId=866544).

> [!TIP]
> Ha a szolgáltatást próbálja ki, akkor tekintse meg a [Próbakörnyezet beállítása](trial-signup.md) részt.

## <a name="prerequisites"></a>Előfeltételek

A környezetek létrehozásához és kezeléséhez rendszergazdai engedélyekre [van szükség](permissions.md) a Customer Insights szolgáltatásban.

## <a name="start-the-environment-creation-process"></a>A környezet létrehozásának folyamata

1. Nyissa meg a környezetválasztót, és válassza az + Új **lehetőséget**.
  
   :::image type="content" source="media/environment-picker.png" alt-text="Környezetválasztó kiválasztása.":::

1. Kövesse a következő szakaszokban ismertetett irányított élményt, hogy minden szükséges információt megadjon egy új környezethez. Ha korábban konfigurált egy környezetet, a konfigurációt [is](#copy-the-environment-configuration) átmásolhatja.

## <a name="step-1-provide-basic-information"></a>1. lépés: Alapvető információk megadása

Az **Alapinformáció** lépésben válassza ki, hogy nulláról hoz-e létre környezetet, vagy [más környezetből szeretne adatokat másolni](#copy-the-environment-configuration).

   :::image type="content" source="media/environment-settings-dialog.png" alt-text="Párbeszédpanel az új Customer Insights-környezet létrehozásához.":::

Adja meg a következő részleteket:

- **Név**: A környezet neve. Ha meglévő környezetből másolt, akkor ez a mező már ki van töltve, de ez módosítható.
- **Válassza ki a vállalkozását**: Válassza ki az elsődleges közönséget az új környezethez. Dolgozhat egyéni ügyfelekkel (B-to-C) vagy [üzleti fiókokkal](work-with-business-accounts.md) (B-to-B). Ha a szervezet elsősorban magánszemélyekkel, például kiskereskedővel vagy kávézóval köt üzletet, válasszon egyéni fogyasztókat. Abban az esetben, ha a fő célközönség más vállalatok, például autógyártó vagy papírgyártó cég, válasszon üzleti számlákat.
- **Típus**: Adja meg, hogy szeretne-e termelési vagy tesztkörnyezetet létrehozni. A tesztkörnyezetek nem engedélyezik az ütemezett adatfrissítést, és előzetes megvalósításhoz és teszteléshez kínáljuk ezeket. A tesztkörnyezet környezetek ugyanazt az célközönség elsődleges környezetként használják, mint az éppen kijelölt éles környezet.
- **Régió**: Az a régió, ahová a szolgáltatást telepítették és üzemeltetik. A [saját Azure Data Lake Storage fiók](own-data-lake-storage.md) használatához vagy [egy meglévő Microsoft Dataverse szervezethez](customer-insights-dataverse.md) való csatlakozáshoz a Customer Insights-környezetnek ugyanabban a régióban kell lennie.

## <a name="step-2-configure-data-storage"></a>2. lépés: Az adattárolás konfigurálása

**Az Adattárolás** lépésben válassza ki, hogy hol szeretné tárolni a Customer Insights-adatokat.

Két lehetőség közül választhat:

- **Customer Insights-tárolás**: Az adattárolást a Customer Insights csapata kezeli. Ez az alapértelmezett beállítás, és hacsak nincsenek konkrét követelmények az adatok saját tárfiókban való tárolására, javasoljuk, hogy használja ezt a lehetőséget.
- **Azure Data Lake Storage**: Adja meg saját Azure Data Lake Storage fiókját az adatok tárolásához, hogy teljes mértékben ön szabályozhassa az adatok tárolásának helyét. További információ: [Saját Azure Data Lake Storage fiók](own-data-lake-storage.md) használata.

:::image type="content" source="media/data-storage-environment.png" alt-text="Válassza ki az adatok tárolásához előnyben részesített lehetőséget.":::

## <a name="step-3-connect-to-microsoft-dataverse"></a>3. lépés: Csatlakozás a Microsoft Dataverse-hez

A **Microsoft Dataverse** lépéssel összekapcsolhatja a Customer Insightsot a Dataverse környezetével. Adatok megosztása az Dataverse üzleti alkalmazásokkal való használathoz, például a Dynamics 365 Marketing vagy a modellvezérelt alkalmazások Dataverse alapján Power Apps.


Hagyja üresen ezt a mezőt, ha nem rendelkezik saját Dataverse környezettel, és mi létrehozunk egyet az Ön számára.

További információ: Customer Insights-adatok használata a következőben: [Microsoft Dataverse](customer-insights-dataverse.md).

:::image type="content" source="media/dataverse-provisioning.png" alt-text="adatmegosztás automatikus automatikus engedélyezésével Microsoft Dataverse a net új környezetekben.":::

### <a name="step-4-finalize-the-settings"></a>4. lépés: A beállítások véglegesítése

**Az Áttekintés** lépésben menjen végig az összes megadott beállításon. Ha minden befejeződött, válassza a **Létrehozás** lehetőséget a környezet beállításáhez.

Néhány beállítást később módosíthat. További tudnivalókért lásd: [Környezetek kezelése](manage-environments.md).

## <a name="work-with-your-new-environment"></a>Az új környezettel való munka

A következő cikkekből segítséget kaphat a Customer Insights konfigurálásának első lépéseihez:

- [Adjon hozzá további felhasználókat, és rendeljen hozzá engedélyeket](permissions.md).
- [Töltse be az adatforrásait](data-sources.md), és futtassa azokat az [adategyesítési folyamaton](data-unification.md) keresztül, hogy [egyesített ügyfélprofilokat](customer-profiles.md) kapjon.
- [Bővítse az egységes ügyfélprofilokat](enrichment-hub.md), vagy futtasson [prediktív modelleket](predictions-overview.md).
- [Hozzon létre szegmenseket](segments.md) az ügyfelek és a [mértékek](measures.md) csoportosításához és a teljesítménymutatók áttekintéséhez.
- [Állítson be kapcsolatokat](connections.md) és [exportálásokat](export-destinations.md) az adatok bizonyos részhalmazának más alkalmazásokban történő feldolgozásához.

## <a name="copy-the-environment-configuration"></a>Másolja a környezet konfigurációját

Rendszergazdaként dönthet úgy, hogy átmásolja a konfigurációt egy meglévő környezetből, amikor újat hoz létre.

:::image type="content" source="media/environment-settings-dialog.png" alt-text="Képernyőkép a beállítási lehetőségekről a környezet beállításaiban.":::

A szervezetében összes elérhető környezet listáját látja, amelyekből adatokat másolhat.

A következő konfigurációbeállítások vannak másolva:

- Importált adatforrások Power Query
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

A környezeti konfiguráció másolásakor néhány további lépésen kell keresztülmennie a hitelesítő adatok megerősítéséhez:

- Ügyfélprofilok. Először hitelesítse és töltse be az adatforrásokat, és futtassa az adatok egyesítését az ügyfélprofilok újbóli létrehozásához.
- Adatforrás hitelesítő adatai. Minden adatforrás hitelesítő adatait meg kell adnia az adatforrások manuális hitelesítéséhez és frissítéséhez.
- Adatforrások a Common Data Model mappából és Dataverse. Ezeket az adatforrásokat manuálisan kell létrehoznia ugyanazzal a névvel, mint a forráskörnyezetben.
- Az exportáláshoz és a gazdagításhoz használt kapcsolati titkok. Újra kell hitelesítenie a kapcsolatokat, majd újra kell aktiválnia a gazdagításokat és exportálásokat.

A másolt környezet létrehozásakor megerősítő üzenet jelenik meg. Válassza az **Ugrás az adatforrásokhoz** lehetőséget az adatforrások listájának megjelenítéséhez.

Minden adatforrásnál megjelenik egy **Hitelesítő adatok szükségesek** állapot. Szerkessze az adatforrásokat, és adja meg a hitelesítő adatokat a frissítésükhöz.

:::image type="content" source="media/data-sources-copied.png" alt-text="A másolt és hitelesítést igényel adatforrások listája.":::

Az adatforrások frissítését követően nyissa meg az **Adatok** > **Egyesítés** pontot. Itt megtalálja a beállításokat a forráskörnyezetből. Igény szerint szerkessze őket, vagy válassza a **Futtatás** lehetőséget az adategyesítési folyamat elindításához, és hozzon létre egy egyesített ügyfélentitást.

Amikor az adatok egyesítése befejeződött, nyissa meg a **Mértékek** és a **Szegmensek** lehetőséget, hogy azokat is frissítse.

Az exportálások és bővítések újraaktiválása előtt a **Rendszergazdai** > **kapcsolatok** lapon újrahitelesítheti a kapcsolatokat az új környezetben.

[!INCLUDE [footer-include](includes/footer-banner.md)]
