---
title: Egyéni gépi tanulás modellek | Microsoft Docs
description: Munka az Azure Machine Learning megoldásból származó modellekkel a Dynamics 365 Customer Insights alkalmazásban.
ms.date: 09/19/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: tutorial
author: zacookmsft
ms.author: zacook
manager: shellyha
searchScope:
- ci-custom-models
- customerInsights
ms.openlocfilehash: 89553b511d249fd586e36a1c4944a977513b0643
ms.sourcegitcommit: be341cb69329e507f527409ac4636c18742777d2
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/30/2022
ms.locfileid: "9609749"
---
# <a name="custom-machine-learning-models"></a>Egyéni gépi tanulás modellek

> [!NOTE]
> A Machine Learning Studio (klasszikus) támogatása 2024. augusztus 31-én megszűnik. Javasoljuk, hogy az azure-gépi tanulás [térjen át](/azure/machine-learning/overview-what-is-azure-machine-learning) erre a dátumra.
>
> 2021. december 1-jétől nem hozhat létre új Machine Learning Studio (klasszikus) erőforrásokat. 2024. augusztus 31-ig továbbra is használhatja a meglévő Machine Learning Studio (klasszikus) erőforrásokat. További információ: [Áttelepítés a Azure gépi tanulás](/azure/machine-learning/migrate-overview).

Az egyéni modellek lehetővé teszik a munkafolyamatok Kezelését Azure gépi tanulás modellek alapján. A munkafolyamatok segítségével kiválaszthatja azokat az adatokat, amelyekből betekintést szeretne létrehozni, és leképezi az eredményeket az egyesített ügyféladatokat. Az egyéni ML modellek készítésével kapcsolatos további információkért lásd: [Az Azure Machine Learning-alapú modellek használata](azure-machine-learning-experiments.md).

## <a name="prerequisites"></a>Előfeltételek

- Az Azure-gépi tanulás kötegelt folyamatokon keresztül [közzétett webszolgáltatások](/azure/machine-learning/concept-ml-pipelines).
- A folyamatot egy folyamat-végpont alatt [kell közzétenni](/azure/machine-learning/how-to-run-batch-predictions-designer#submit-a-pipeline-run).
- Egy [Azure Data Lake Gen2 tárfiók](/azure/storage/blobs/data-lake-storage-quickstart-create-account), amely a Azure Studio társította a Azure Studio társított tárfiókot.
- Az Azure gépi tanulás munkaterületek folyamatokkal, tulajdonosi vagy felhasználói hozzáférés-rendszergazdai engedélyekkel az Azure gépi tanulás munkaterülethez.

  > [!NOTE]
  > Az adatok átkerülnek a Customer Insights-példányok és a munkafolyamat kiválasztott Azure webes szolgáltatásai és folyamatai között. Amikor adatokat továbbít egy Azure-szolgáltatásnak, győződjön meg arról, hogy a szolgáltatás úgy van-e konfigurálva, hogy az adatokat a szervezetre vonatkozó jogi vagy szabályozási követelményeknek való megfeleléshez szükséges módon és helyen feldolgozza.

## <a name="add-a-new-workflow"></a>Új munkafolyamat hozzáadása

1. Nyissa meg a **Információk** > **Egyéni modellek** elemet, és válassza az **Új munkafolyamat** lehetőséget.

1. Adjon meg egy felismerhető **nevet**.

   :::image type="content" source="media/new-workflowv2.png" alt-text="Képernyőkép – az új munkafolyamat ablaktábla.":::

1. Válassza ki azt a szervezetet, amely a webszolgáltatást tartalmazza a **Bérlő, amely tartalmazza a webszolgáltatást** pontban.

1. Ha az Azure Machine Learning-előfizetése egy másik bérlőn belül van, mint a Customer Insights, akkor válassza a **bejelentkezés** lehetőséget a kijelölt szervezethez tartozó hitelesítő adatokkal.

1. Jelölje ki a webszolgáltatáshoz társított **Munkaterületeket**.

1. Válassza ki a Azure gépi tanulás folyamatot a **modellt** tartalmazó webszolgáltatás legördülő menüjében. Azután válassza a **Következő** elemet.
   További információ a [folyamatok közzétételéről az Azure Machine Learning a tervezővel](/azure/machine-learning/concept-ml-pipelines#building-pipelines-with-the-designer) vagy az [SDK-val](/azure/machine-learning/concept-ml-pipelines#building-pipelines-with-the-python-sdk).

1. Minden egyes **Webszolgáltatás-bemenetnél** válassza ki a megfelelő **Entitást** a Customer Insights megoldásból. Azután válassza a **Következő** elemet.
   > [!NOTE]
   > Az egyéni modell-munkafolyamat heurisztikák segítségével leképezi a webszolgáltatás beviteli mezőit az entitás attribútumára a mező neve és adattípusa alapján. Hibaüzenet jelenik meg, ha egy webszolgáltatás mezőjét nem lehet egy entitásra leképezni.

   :::image type="content" source="media/intelligence-screen2-updated.png" alt-text="Munkafolyamat konfigurálása.":::

1. A **Modell kimeneti paraméterei** beállításhoz állítsa be a következő tulajdonságokat:
   - **A folyamat kimeneti eredményeinek entitásneve**
   - **Kimeneti adattár a kötegelt folyamat paraméterneve**
   - **A kötegelt folyamat kimeneti elérésiút-paraméterének neve**

   :::image type="content" source="media/intelligence-screen3-outputparameters.png" alt-text="A modell kimenet paraméter panele.":::

1. Válassza ki az egyező attribútumot az ügyfél-azonosítóból **az ügyfeleket azonosító eredmények** között, majd válassza a Mentés **lehetőséget**.

   :::image type="content" source="media/intelligence-screen4-relatetocustomer.png" alt-text="Eredmények összekapcsolása az Ügyfél adatpanellel.":::

   A **Munkafolyamat mentett** képernyő megjeleníti a munkafolyamat részleteit. Ha munkafolyamatot konfigurált egy Azure gépi tanulás-folyamathoz, a Customer Insights a folyamatot tartalmazó munkaterülethez csatolja. A Customer Insights közreműködő **szerepkört** kap az Azure-munkaterületen.

1. Válassza a **Kész** lehetőséget. Megjelenik az **Egyéni modellek** oldal.

1. Válassza ki a munkafolyamat függőleges három pontját (&vellip;), majd válassza a Futtatás **lehetőséget**. A munkafolyamat is automatikusan fut minden [ütemezett frissítéssel](schedule-refresh.md).

## <a name="manage-an-existing-workflow"></a>Meglévő munkafolyamat kezelése

Az Intelligencia **egyéni modelljei** > **lapon** megtekintheti a létrehozott munkafolyamatokat.

Válasszon ki egy munkafolyamatot az elérhető műveletek megtekintéséhez.

- **Munkafolyamat szerkesztése**
- **Munkafolyamat futtatása**
- [**Munkafolyamat törlése**](#delete-a-workflow)

### <a name="edit-a-workflow"></a>Egy munkafolyamat szerkesztése

1. Nyissa meg az **Egyéni intelligenciamodellek** > **oldalt**.

1. A frissíteni kívánt munkafolyamat mellett válassza ki a függőleges három pontot (&vellip;), majd a Szerkesztés **lehetőséget**.

1. Szükség esetén módosítsa **megjelenítendő név**, majd válassza a Tovább lehetőséget.**·**

1. Ha szükséges, minden **webszolgáltatás-bemenethez** frissítse az egyező **entitást** a Customer Insights szolgáltatásból. Azután válassza a **Következő** elemet.

1. A Modell kimeneti paramétereihez **módosítsa** a következők bármelyikét:
   - **A folyamat kimeneti eredményeinek entitásneve**
   - **Kimeneti adattár a kötegelt folyamat paraméterneve**
   - **A kötegelt folyamat kimeneti elérésiút-paraméterének neve**

1. Módosítsa az egyező attribútumot az ügyfél-azonosítóból **az eredményekben az ügyfelek** azonosításához. Ki kell választania egy attribútumot a származtatott kimenetből az ügyfél entitás ügyfél-azonosító oszlopához hasonló értékekkel. Ha nincs ilyen oszlop a adatkészlet, válasszon egy olyan attribútumot, amely egyedileg azonosítja a sort.

1. Válassza a **Mentés** lehetőséget

### <a name="delete-a-workflow"></a>Egy munkafolyamat törlése

1. Nyissa meg az **Egyéni intelligenciamodellek** > **oldalt**.

1. A törölni kívánt munkafolyamat mellett válassza ki a függőleges három pontot (&vellip;), majd válassza a Törlés **lehetőséget**.

1. Hagyja jóvá a törlést.

A munkafolyamat törölve lesz. A [munkafolyamat létrehozásakor létrehozott entitás](entities.md) megmarad, és az **Adatentitások** > **lapról** tekinthető meg.

## <a name="view-the-results"></a>Az eredmények megtekintése

A munkafolyamat eredményei a modell kimeneti paramétereihez **meghatározott** entitásnévben vannak tárolva. Ezeket az adatokat az [**Adatentitások** > **oldalról**](entities.md) vagy [API-hozzáféréssel érheti el](apis.md).

### <a name="api-access"></a>API-hozzáférés

Ha egy adott OData lekérdezéssel egyéni modellentitásból származó adatokat szeretne lekérni, használja a következő formátumot:

`https://api.ci.ai.dynamics.com/v1/instances/<your instance id>/data/<custom model output entity name>%3Ffilter%3DCustomerId%20eq%20'<guid value>'`

1. Cserélje le a helyére `<your instance id>` a Customer Insights-környezet azonosítóját, amely a böngésző címsorában jelenik meg a Customer Insights elérésekor.

1. Cserélje le a helyére `<custom model output entity>` a **modell kimeneti paramétereihez** megadott entitásnevet.

1. Cserélje le a helyére `<guid value>` annak az ügyfélnek az ügyfél-azonosítóját, akihez hozzá szeretne férni. Ez az azonosító az [ügyfélprofilok oldalán](customer-profiles.md) jelenik meg az Ügyfél-azonosító mezőben.

## <a name="frequently-asked-questions"></a>Gyakran ismételt kérdések

- Miért nem látható a folyamat egy egyéni modell munkafolyamatának beállításakor?
  Ezt a problémát gyakran a folyamat konfigurációs problémája okozza. Meg kell győződni arról, hogy a [bemeneti paraméter be van állítva](azure-machine-learning-experiments.md#dataset-configuration), valamint a [kimeneti adattár és elérési út paraméterei](azure-machine-learning-experiments.md#import-pipeline-data-into-customer-insights) is meg vannak adva.

- Mit jelent "Az intelligenciaalapú munkafolyamat mentése nem sikerült" hibaüzenet? 
  A felhasználók általában akkor látják ezt a hibaüzenetet, ha nem rendelkezik tulajdonosi vagy felhasználói hozzáférési rendszergazdai jogosultsággal a munkaterületen. A felhasználónak magasabb szintű engedélyekre van szüksége ahhoz, hogy engedélyezze a Customer Insights számára a munkafolyamat feldolgozását szolgáltatásként, és nem a felhasználói hitelesítő adatokat használni a munkafolyamat későbbi futtatásaiban.

- Támogatott-e egy privát végpont/privát kapcsolat az egyéni modell munkafolyamatomhoz?
  A Customer Insights jelenleg nem támogatja az egyéni modellek privát végpont, de manuális megkerülő megoldás áll rendelkezésre. A részletekért kérjük, vegye fel a kapcsolatot az ügyfélszolgálattal.

## <a name="responsible-ai"></a>Felelős AI

Az előrejelzések lehetőséget nyújtanak a jobb ügyfelekkel kapcsolatos tapasztalatok létrehozására, az üzleti lehetőségek fejlesztésére és a bevételi források javítására. Kifejezetten ajánljuk, hogy a előrejelzés értékét egyenlítsék ki annak hatásával és az esetleges torzításokkal szemben etikus módon. Ismerje meg, hogy a Microsoft hogyan [kezeli a felelős AI-t ](https://www.microsoft.com/ai/responsible-ai?activetab=pivot1%3aprimaryr6). Megtudhatja, hogyan használhatók [a felelős gépi tanulás technikái és folyamatai](/azure/machine-learning/concept-responsible-ml), amelyek az Azure Machine Learningre jellemzőek.

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWRElk]

[!INCLUDE [footer-include](includes/footer-banner.md)]
