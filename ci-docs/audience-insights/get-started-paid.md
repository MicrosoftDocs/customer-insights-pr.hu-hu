---
title: A Customer Insights fizetett licencének létrehozása és konfigurálása
description: A Dynamics 365 Customer Insights licencelt telőfizetés beszerzésének és konfigurációjának lépései.
ms.date: 07/22/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: MichelleDevaney
ms.author: midevane
manager: shellyha
ms.custom: intro-internal
ms.openlocfilehash: f8cf1be97ee8af46145a450009fd278b1821f8fe
ms.sourcegitcommit: 5c9c54ffe045017c19f0042437ada2c101dcaa0f
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/22/2021
ms.locfileid: "6650478"
---
# <a name="get-started-with-a-paid-subscription"></a>Első lépések a fizetett előfizetéssel

Ez a cikk azt mutatja be, hogyan lehet új környezetet létrehozni azt követően, hogy a szervezete megvásárolt egy Dynamics 365 Customer Insights előfizetést. Ha meg szeretné vásárolni a Customer Insights alkalmazást, akkor használja a [Dynamics 365 Customer Insights weboldalon](https://dynamics.microsoft.com/ai/customer-insights/) felsorolt kapcsolatfelvételi lehetőségeket. 

Ha a szolgáltatást és a funkciókat szeretné kipróbálni, akkor tekintse meg a [Próbakörnyezet beállítása](get-started-trial.md) részt.

## <a name="create-an-environment-in-an-existing-organization"></a>Környezet létrehozása meglévő szervezetből

Miután megvásárolta a Customer Insights előfizetéses licencét, a Microsoft 365 bérlő globális rendszergazdája kap egy e-mailt, amely meghívja őt a környezet létrehozására. A kezdéshez ugorjon a [https://home.ci.dynamics.com/start](https://home.ci.dynamics.com/start) weboldalra. 

A Customer Insights nem felhasználónként van licencelve , így nem fog megjelenni a Licencek területen. Ha a Microsoft 365 felügyeleti központban keres licencet, akkor a **Saját termékek** oldalon keresse. 

> [!NOTE]
> A szervezetek minden Customer Insights licenchez *két* környezetet hozhatnak létre. Ha a szervezete egynél több licencet vásárol, a rendelkezésre álló környezetek számának növelése érdekében [lépjen kapcsolatba a támogatási csoporttal](https://go.microsoft.com/fwlink/?linkid=2079641). A kapacitással és a bővítménykapacitással kapcsolatos további információkért töltse le a [Dynamics 365 licencelési útmutatóját](https://go.microsoft.com/fwlink/?LinkId=866544).

Környezet létrehozásához:

1. A **Környezet létrehozása** párbeszédpanelen válassza az **Új környezet** lehetőséget.

   :::image type="content" source="media/environment-settings-dialog.png" alt-text="Párbeszédpanel az új Customer Insights-környezet létrehozásához.":::

   Javasoljuk, hogy nulláról kezdje el a környezet beállítását. Ha azonban rendszergazda vagy egy próbakörnyezet tagja, akkor [más környezetből is másolhat adatokat](manage-environments.md#copy-the-environment-configuration), ha a **Másolás meglévő környezetből** parancsot választja. A szervezetében összes elérhető környezet listáját látja, amelyekből adatokat másolhat.

1. Adja meg a következő részleteket:
   - **Név**: A környezet neve. Ha meglévő környezetből másolt, akkor ez a mező már ki van töltve, de ez módosítható.
   - **Régió**: Az a régió, ahová a szolgáltatást telepítették és üzemeltetik.
   - **Típus**: Adja meg, hogy szeretne-e termelési vagy tesztkörnyezetet létrehozni. A tesztkörnyezetek nem engedélyezik az ütemezett adatfrissítést, és előzetes megvalósításhoz és teszteléshez kínáljuk ezeket.
   
1. Nem kötelezően kiválaszthatja a **Speciális beállításokat**:

   - **Összes adat mentése ide**: Megadja, hogy hol szeretné tárolni a Customer Insights-ból előállított kimeneti adatait. Két lehetősége lesz: **Ügyfélelemzések tárolása** (a Customer Insights csapat által kezelt Azure Data Lake) és **Azure Data Lake Storage** (saját Azure Data Lake Storage). Alapértelmezés szerint a Customer Insights tárolóhely beállítás van kiválasztva.

     > [!NOTE]
     > Ha adatokat ment az Azure Data Lake Storage tárhelyre azzal elfogadja, hogy az adatok át lesznek víve az Azure tárfióknak megfelelő földrajzi helyre, és ott lesznek tárolva; ez eltérhet attól a helytől, ahol a Dynamics 365 Customer Insights adatai vannak tárolva. [További információ a Microsoft adatvédelmi központról.](https://www.microsoft.com/trust-center)
     >
     > Jelenleg a Power BI-adatfolyamokból beolvasott entitások tárolása mindig a Microsoft Dataverse által kezelt Data Lake-ben történik. 
     > 
     > Csak az Azure Data Lake Storage fiókokat támogatjuk ugyanabból az Azure-régióból, amelyet a környezet létrehozásakor kiválasztott. 
     > 
     > Csak olyan Azure Data Lake Storage fiókokat támogatunk, amelyeknél engedélyezve van a hierarchikus névtér.


   - A Azure Data Lake Storage beállításhoz választhat az erőforrás-alapú és az előfizetés-alapú hitelesítési lehetőség között. További információkért lásd: [Célközönség-információk összekapcsolása az Azure Data Lake Storage Gen2 fiókjához az Azure egyszerű szolgáltatásnévvel](connect-service-principal.md). A **Tároló** neve nem változtatható meg, és `customerinsights` lesz.
   
   - Ha [előre elkészített modelleket](predictions-overview.md#out-of-box-models), konfigurálni szeretné az adatmegosztást a Microsoft Dataverse-szolgáltatással, vagy engedélyezni az adatbetöltést helyszíni adatforrásokból, adja meg a Microsoft Dataverse-környezet URL-címét az **Adatmegosztás konfigurálása a Microsoft Dataverse segítségével, valamint további funkciók engedélyezése helyen**. Válassza az **Adatmegosztás engedélyezése** lehetőséget, ha meg szeretné osztani a Customer Insights kimeneti adatait a Microsoft Dataverse Managed Data Lake használatával.

     > [!NOTE]
     > - A Microsoft Dataverse Managed Data Lake használatával való adatmegosztás jelenleg nem támogatott, ha az adatokat a saját Azure Data Lake Storage tárhelyére menti.
     > - [Entitásból hiányzó értékek előrejelzése](predictions.md) jelenleg nem támogatott, ha engedélyezi az adatok megosztását a Microsoft Dataverse Managed Data Lake szolgáltatással.

     :::image type="content" source="media/Datasharing-with-DataverseMDL.png" alt-text="Konfigurálási lehetőségek az adatmegosztás engedélyezéséhez a Microsoft Dataverse szolgáltatással.":::

   Amikor a rendszer feldolgozza az adatok betöltését, a rendszer a megfelelő mappákat létrehozza a megadott tárfiókban. Az adatfájlok és a model.json fájlok a folyamat neve alapján jönnek létre, és kerülnek a mappákba.

   Ha több Customer Insights-környezetet hoz létre, és úgy dönt, hogy menti a kimeneti entitást ezekből a környezetekből a tárfiókba, a rendszer minden környezethez külön mappát hoz létre a tárolóban ci_<environmentid>.

1. Válassza a **Létrehozás** lehetőséget a környezet beállításához. 

## <a name="configure-an-environment"></a>Környezet konfigurálása

Az alábbi cikkekből segítséget kaphat a Customer Insights konfigurálásával való megismerkedéshez. 

- [Adjon hozzá további felhasználókat, és rendeljen hozzá engedélyeket](permissions.md).
- [Töltse be az adatforrásait](data-sources.md), és futtassa azokat az [adategyesítési folyamaton](data-unification.md) keresztül, hogy [egyesített ügyfélprofilokat](customer-profiles.md) kapjon.
- [Bővítse az egységes ügyfélprofilokat](enrichment-hub.md), vagy futtasson [prediktív modelleket](predictions-overview.md).
- Hozzon létre [szegmenseket](segments.md) az ügyfelek és [mértékek](measures.md) csoportosítása és a teljesítménymutatók áttekintésének értékelése érdekében.
- Állítson be [kapcsolatokat](connections.md) és [exportálásokat](export-destinations.md) az adatok bizonyos részhalmazának más alkalmazásokban történő feldolgozásához.
