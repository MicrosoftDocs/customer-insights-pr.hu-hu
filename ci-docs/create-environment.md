---
title: Új környezet létrehozása
description: A környezetek létrehozásának lépései Dynamics 365 Customer Insights.
ms.date: 08/15/2022
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
ms.openlocfilehash: 0a45e2fd2bdb7b85883a536f8b42ee650e54db7e
ms.sourcegitcommit: 267c317e10166146c9ac2c30560c479c9a005845
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/16/2022
ms.locfileid: "9304246"
---
# <a name="create-a-new-environment"></a>Új környezet létrehozása

Miután [megvásárolta az Dynamics 365 Customer Insights](paid-license.md) előfizetési licencet, a bérlő globális rendszergazdája Microsoft 365 kap egy e-mailt, amely meghívja őket a környezet létrehozására. A kezdéshez ugorjon a [https://home.ci.ai.dynamics.com/start](https://home.ci.ai.dynamics.com/start) weboldalra. Ebben a forgatókönyvben kezdje az 1. lépéssel [: Alapvető információk megadása](#step-1-provide-basic-information).

Az első környezet létrehozása után a bérlő globális rendszergazdája rendszergazdaként adhat Microsoft 365 hozzá felhasználókat a [szervezetből](permissions.md). Ezek a rendszergazdák ezután kezelhetik a felhasználókat és a környezeteket. Ha szervezete egynél több licencet vásárol a Customer Insights szolgáltatáshoz, [vegye fel a kapcsolatot ügyfélszolgálatunkkal](https://go.microsoft.com/fwlink/?linkid=2079641) az elérhető környezetek számának növelése érdekében. A kapacitással és a kiegészítő kapacitással kapcsolatos további információkért tekintse át a [Dynamics 365 licencelési útmutatóját](https://go.microsoft.com/fwlink/?LinkId=866544). Ha lehetősége van további környezetek létrehozására, lépjen [a Környezet létrehozásának folyamatának elindítása elemre](#start-the-environment-creation-process).

> [!TIP]
> Ha a szolgáltatást próbálja ki, akkor tekintse meg a [Próbakörnyezet beállítása](trial-signup.md) részt.

## <a name="prerequisites"></a>Előfeltételek

[Rendszergazdai engedélyek](permissions.md) a Customer Insights szolgáltatásban

## <a name="start-the-environment-creation-process"></a>A környezet létrehozásának folyamata

1. Nyissa meg a környezetválasztót, és válassza az + Új **lehetőséget**.
  
   :::image type="content" source="media/environment-picker.png" alt-text="Környezetválasztó kiválasztása.":::

1. Kövesse a következő szakaszokban ismertetett irányított élményt, hogy minden szükséges információt megadjon egy új környezethez.

## <a name="step-1-provide-basic-information"></a>1. lépés: Alapvető információk megadása

1. Válassza ki, hogy a környezet semmiből szeretne-e létrehozni, vagy egy másik környezetből szeretne adatokat másolni. [Az adatok másik környezetből](#copy-the-environment-configuration) való másolásához további lépésekre van szükség.

   :::image type="content" source="media/environment-settings-dialog.png" alt-text="Párbeszédpanel az új Customer Insights-környezet létrehozásához.":::

1. Adja meg a következő részleteket:

   - **Név**: A környezet neve. Ha meglévő környezetből másolt, akkor ez a mező már ki van töltve, de ez módosítható.
   - **Válassza ki vállalkozását**: Elsődleges célközönség az új környezethez: egyéni fogyasztók (B-től C-ig) vagy [üzleti fiókok](work-with-business-accounts.md) (B-től B-ig). Ha a szervezet elsősorban magánszemélyekkel, például kiskereskedővel vagy kávézóval köt üzletet, válasszon egyéni fogyasztókat. Ha a fő célközönség más vállalatok, például autógyártó vagy papírgyártó cég, válassza az üzleti számlákat.
   - **Típus**: A környezet típusa: éles vagy tesztkörnyezet. A tesztkörnyezetek nem engedélyezik az ütemezett adatfrissítést, és előzetes megvalósításhoz és teszteléshez kínáljuk ezeket. A tesztkörnyezet környezetek ugyanazt az célközönség elsődleges környezetként használják, mint az éppen kijelölt éles környezet.
   - **Régió**: Régió, ahol a szolgáltatás telepítve és üzemel. A [saját Azure Data Lake Storage fiók](own-data-lake-storage.md) használatához vagy [egy meglévő Microsoft Dataverse szervezethez](customer-insights-dataverse.md) való csatlakozáshoz a Customer Insights-környezetnek ugyanabban a régióban kell lennie.

1. Válassza a **Következő** lehetőséget.

## <a name="step-2-configure-data-storage"></a>2. lépés: Az adattárolás konfigurálása

1. Válassza ki, hogy hol szeretné tárolni a Customer Insights-adatokat:

   - **Customer Insights-tárolás**: Az adattárolás kezelése automatikusan történik. Ez az alapértelmezett beállítás, és hacsak nincsenek konkrét követelmények az adatok saját tárfiókban való tárolására, javasoljuk, hogy használja ezt a lehetőséget.
   - **Azure Data Lake Storage**: Saját Azure Data Lake Storage fiókja az adatok tárolására, így teljes mértékben szabályozhatja az adatok tárolásának helyét. Kövesse a Saját [fiók Azure Data Lake Storage használata című](own-data-lake-storage.md) témakör lépéseit.

   :::image type="content" source="media/data-storage-environment.png" alt-text="Válassza ki az adatok tárolásához előnyben részesített lehetőséget.":::

1. Válassza a **Következő** lehetőséget.

## <a name="step-3-connect-to-microsoft-dataverse"></a>3. lépés: Csatlakozás a Microsoft Dataverse-hez

Ha van környezete Dataverse, csatlakoztassa a Customer Insights szolgáltatást. Adatok megosztása az Dataverse üzleti alkalmazásokkal való használathoz, például a Dynamics 365 Marketing vagy a modellvezérelt alkalmazások Dataverse alapján Power Apps.

1. Kövesse a Customer Insights-adatokkal való munka a következőben található [Microsoft Dataverse](customer-insights-dataverse.md) lépéseket: .

   :::image type="content" source="media/dataverse-provisioning.png" alt-text="adatmegosztás automatikus automatikus engedélyezésével Microsoft Dataverse a net új környezetekben.":::

1. Válassza a **Következő** lehetőséget.

## <a name="step-4-finalize-the-settings"></a>4. lépés: A beállítások véglegesítése

Tekintse át a megadott beállításokat. Ha minden befejeződött, válassza a **Létrehozás** lehetőséget a környezet beállításáhez.

Ha később módosítani szeretne néhány beállítást, tekintse meg a Környezetek kezelésecímű [témakört](manage-environments.md).

## <a name="work-with-your-new-environment"></a>Az új környezettel való munka

A következő cikkekből segítséget kaphat a Customer Insights konfigurálásának első lépéseihez:

- [Adjon hozzá további felhasználókat, és rendeljen hozzá engedélyeket](permissions.md).
- [Töltse be az adatforrásait](data-sources.md), és futtassa azokat az [adategyesítési folyamaton](data-unification.md) keresztül, hogy [egyesített ügyfélprofilokat](customer-profiles.md) kapjon.
- [Bővítse az egységes ügyfélprofilokat](enrichment-hub.md), vagy futtasson [prediktív modelleket](predictions-overview.md).
- [Hozzon létre szegmenseket](segments.md) az ügyfelek és a [mértékek](measures.md) csoportosításához és a teljesítménymutatók áttekintéséhez.
- [Állítson be kapcsolatokat](connections.md) és [exportálásokat](export-destinations.md) az adatok bizonyos részhalmazának más alkalmazásokban történő feldolgozásához.

## <a name="copy-the-environment-configuration"></a>Másolja a környezet konfigurációját

Rendszergazdaként, ha úgy döntött, hogy a konfigurációt egy meglévő környezetből másolja, válasszon a szervezet összes elérhető környezetének listájából.

:::image type="content" source="media/environment-settings-dialog.png" alt-text="Képernyőkép a beállítási lehetőségekről a környezet beállításaiban.":::

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

### <a name="set-up-a-copied-environment"></a>Másolt környezet beállítása

A környezeti konfiguráció másolásakor egy megerősítő üzenet jelenik meg, amikor a másolt környezet létrejött. A hitelesítő adatok megerősítéséhez hajtsa végre a következő lépéseket.

1. Válassza az **Ugrás az adatforrásokhoz** lehetőséget az adatforrások listájának megjelenítéséhez. Az összes adatforrás a Hitelesítő adatok szükséges **állapotát mutatja**.

   :::image type="content" source="media/data-sources-copied.png" alt-text="A másolt és hitelesítést igényel adatforrások listája.":::

1. Szerkessze az adatforrásokat, és adja meg a hitelesítő adatokat a frissítésükhöz. A Common Data Model mappából származó adatforrások, és Dataverse manuálisan kell létrehozni őket ugyanazzal a névvel, mint a forráskörnyezetben.

1. Az adatforrások frissítését követően nyissa meg az **Adatok** > **Egyesítés** pontot. Itt megtalálja a beállításokat a forráskörnyezetből. Szükség szerint szerkessze őket, vagy válassza az Ügyfélprofilok és -függőségek **egyesítése** > **lehetőséget** az adategyesítési folyamat elindításához és az egységes ügyfélentitás létrehozásához.

   > [!TIP]
   > Partnerek és kapcsolattartók esetén válassza a Fiókok **egyesítése profilok és függőségek egyesítése lehetőséget** > **·**.

1. Amikor az adatok egyesítése befejeződött, a Frissítések **és** szegmensek **területen** frissítheti őket.

1. A Rendszergazdai **kapcsolatok lapon** > **újrahitelesítheti** a kapcsolatokat az új környezetben.

1. Az **Adatgazdagítás** > **és** az **Adatexportálás** > **elemre** kattintva újraaktiválhatja őket.

[!INCLUDE [footer-include](includes/footer-banner.md)]
