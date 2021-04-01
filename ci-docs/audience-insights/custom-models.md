---
title: Egyéni gépi tanulás modellek | Microsoft Docs
description: Munka az Azure Machine Learning megoldásból származó modellekkel a Dynamics 365 Customer Insights alkalmazásban.
ms.date: 03/22/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: tutorial
author: zacookmsft
ms.author: zacook
manager: shellyha
ms.openlocfilehash: 87fb517e9f0b380f9721f77470dceb3bcb7e5616
ms.sourcegitcommit: 55c00ea61c78db7b3b54894c01afb3246dff31c8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/22/2021
ms.locfileid: "5700671"
---
# <a name="custom-machine-learning-models"></a>Egyéni gépi tanulás modellek

Az **Információk** > **Egyéni modellek** ponttal kezelheti a munkafolyamatokat az Azure Machine Learning-modellek alapján. A munkafolyamatok segítségével kiválaszthatja azokat az adatokat, amelyekből betekintést szeretne létrehozni, és leképezi az eredményeket az egyesített ügyféladatokat. Az egyéni ML modellek készítésével kapcsolatos további információkért lásd: [Az Azure Machine Learning-alapú modellek használata](azure-machine-learning-experiments.md).

## <a name="responsible-ai"></a>Felelős AI

Az előrejelzések lehetőséget nyújtanak a jobb ügyfelekkel kapcsolatos tapasztalatok létrehozására, az üzleti lehetőségek fejlesztésére és a bevételi források javítására. Kifejezetten ajánljuk, hogy a előrejelzés értékét egyenlítsék ki annak hatásával és az esetleges torzításokkal szemben etikus módon. Ismerje meg, hogy a Microsoft hogyan [kezeli a felelős AI-t ](https://www.microsoft.com/ai/responsible-ai?activetab=pivot1%3aprimaryr6). Megtudhatja, hogyan használhatók [a felelős gépi tanulás technikái és folyamatai](/azure/machine-learning/concept-responsible-ml), amelyek az Azure Machine Learningre jellemzőek.

## <a name="prerequisites"></a>Előfeltételek

- Jelenleg ez a szolgáltatás támogatja a [Machine Learning Studio (klasszikus)](https://studio.azureml.net) verzióján és az [Azure Machine Learning kötegelt folyamaton](/azure/machine-learning/concept-ml-pipelines) keresztül közzétett webszolgáltatásokat .

- A funkció használatához az Azure Studio-példányhoz társított Azure Data Lake Gen2-fiókra van szükség. További információ: [Azure Data Lake Storage Gen2 tárfiók létrehozása](/azure/storage/blobs/data-lake-storage-quickstart-create-account).

- Az Azure Machine Learning-munkaterületek és folyamatok esetén tulajdonosi vagy felhasználói hozzáférésű rendszergazdai engedélyekre van szükség az Azure Machine Learning-munkaterülethez.

   > [!NOTE]
   > Az adatok átkerülnek a Customer Insights-példányok és a munkafolyamat kiválasztott Azure webes szolgáltatásai és folyamatai között. Amikor adatokat továbbít egy Azure-szolgáltatásnak, győződjön meg arról, hogy a szolgáltatás úgy van-e konfigurálva, hogy az adatokat a szervezetre vonatkozó jogi vagy szabályozási követelményeknek való megfeleléshez szükséges módon és helyen feldolgozza.

## <a name="add-a-new-workflow"></a>Új munkafolyamat hozzáadása

1. Nyissa meg a **Információk** > **Egyéni modellek** elemet, és válassza az **Új munkafolyamat** lehetőséget.

1. Adjon meg egy felismerhető nevet a **Név** mezőben az egyéni modellnek.

   > [!div class="mx-imgBorder"]
   > ![Képernyőkép – az új munkafolyamat ablaktábla](media/new-workflowv2.png "Képernyőkép – az új munkafolyamat ablaktábla")

1. Válassza ki azt a szervezetet, amely a webszolgáltatást tartalmazza a **Bérlő, amely tartalmazza a webszolgáltatást** pontban.

1. Ha az Azure Machine Learning-előfizetése egy másik bérlőn belül van, mint a Customer Insights, akkor válassza a **bejelentkezés** lehetőséget a kijelölt szervezethez tartozó hitelesítő adatokkal.

1. Jelölje ki a webszolgáltatáshoz társított **Munkaterületeket**. Két szakasz van felsorolva, egy az Azure Machine Learning v1 (Machine Learning Studio (klasszikus)) és az Azure Machine Learning v2 (Azure Machine Learning). Ha nem tudja biztosan, hogy melyik munkaterület a megfelelő a Machine Learning Studio (klasszikus) webszolgáltatáshoz, válassza a **Bármelyik** lehetőséget.

1. Válassza ki a Machine Learning Studio (klasszikus) webszolgáltatást vagy Azure Machine Learning folyamat lehetőséget a **Modellt tartalmazó webszolgáltatás** legördülő menüben. Azután válassza a **Következő** elemet.
   - További információ a [webszolgáltatás közzétételéről a Machine Learning Studio (classic) szolgáltatásban](/azure/machine-learning/studio/deploy-a-machine-learning-web-service#deploy-it-as-a-new-web-service)
   - További információ a [folyamatok közzétételéről az Azure Machine Learning a tervezővel](/azure/machine-learning/concept-ml-pipelines#building-pipelines-with-the-designer) vagy az [SDK-val](/azure/machine-learning/concept-ml-pipelines#building-pipelines-with-the-python-sdk). A folyamatokat a [folyamatvégpont](/azure/machine-learning/how-to-run-batch-predictions-designer#submit-a-pipeline-run) alatt közzé kell tenni.

1. Minden egyes **Webszolgáltatás-bemenetnél** válassza ki a megfelelő **Entitást** a célközönség-információkból, és válassza a **Következő** elemet.
   > [!NOTE]
   > Az egyéni modell-munkafolyamat heurisztikák segítségével leképezi a webszolgáltatás beviteli mezőit az entitás attribútumára a mező neve és adattípusa alapján. Hibaüzenet jelenik meg, ha egy webszolgáltatás mezőjét nem lehet egy entitásra leképezni.

   > [!div class="mx-imgBorder"]
   > ![Munkafolyamat konfigurálása](media/intelligence-screen2-updated.png "Munkafolyamat konfigurálása")

1. Állítsa be a következő tulajdonságokat a **Modell kimeneti paraméterek** lépésében:
   - Machine Learning Studio (klasszikus)
      1. Adja meg a kimeneti **Entitás nevét**, amelyet a webszolgáltatás kimenetének eredményére szeretne beáramlani.
   - Azure Machine Learning
      1. Adja meg a kimeneti **Entitás nevét**, amelyet a folyamat kimenetének eredményére szeretne beáramlani.
      1. Válassza ki a **kimeneti adattár paraméter nevét** a kötegfolyamathoz a legördülő listából.
      1. Válassza ki a **Kimeneti útvonal paraméter nevét** a kötegfolyamathoz a legördülő listából.

      > [!div class="mx-imgBorder"]
      > ![A modell kimenet paraméter panele](media/intelligence-screen3-outputparameters.png "A modell kimenet paraméter panele")

1. Válassza ki a megfelelő attribútumot az **Ügyfél-azonosító az eredményekben** legördülő listából, amely beazonosítja az ügyfeleket, és válassza a **Mentés** elemet.

   > [!div class="mx-imgBorder"]
   > ![Eredmények összekapcsolása az Ügyfél adatpanelhlel](media/intelligence-screen4-relatetocustomer.png "Eredmények összekapcsolása az Ügyfél adatpanelhlel")

1. Megjelenik a **Munkafolyamat mentve** képernyő a munkafolyamat részleteivel.    
   Ha az Azure Machine Learning folyamathoz munkafolyamatot konfigurált, a célközönség-információk hozzákapcsolja a munkaterülethez, amely a folyamatot tartalmazza. Célközönség-információk kap egy **Közreműködő** szerepkörrel az Azure workspace-ban.

1. Válassza a **Kész** lehetőséget.

1. Ezután a munkafolyamatot az **egyéni modellek** oldalról futtathatja.

## <a name="edit-a-workflow"></a>Egy munkafolyamat szerkesztése

1. Az **egyéni modellek** lapon jelölje ki a függőleges három pontot a **Műveletek** oszlopban a korábban létrehozott munkafolyamat mellett, és válassza a **Szerkesztés** lehetőséget.

1. A munkafolyamat felismerhető nevét a **megjelenítendő név** mezőben frissítheti, de a konfigurált webszolgáltatás vagy folyamat nem módosítható. Válassza a **Következő** lehetőséget.

1. Minden egyes **Webszolgáltatás-bemenetnél** frissítheti a megfelelő **Entitást** a célközönség-információkból, és válassza a Következő elemet. Azután válassza a **Következő** elemet.

1. Állítsa be a következő tulajdonságokat a **Modell kimeneti paraméterek** lépésében:
   - Machine Learning Studio (klasszikus)
      1. Adja meg a kimeneti **Entitás nevét**, amelyet a webszolgáltatás kimenetének eredményére szeretne beáramlani.
   - Azure Machine Learning
      1. Adja meg a kimeneti **Entitás nevét**, amelyet a folyamat kimenetének eredményére szeretne beáramlani.
      1. Válassza ki a **kimeneti adattár paraméter nevét** a tesztelési folyamathoz.
      1. Válassza ki a **kimeneti útvonal paraméter nevét** a tesztelési folyamathoz.

1. Válassza ki a megfelelő attribútumot az **Ügyfél-azonosító az eredményekben** legördülő listából, amely beazonosítja az ügyfeleket, és válassza a **Mentés** elemet.
   Ki kell választania egy attribútumot a származtatott kimenetből az ügyfél entitás ügyfél-azonosító oszlopához hasonló értékekkel. Ha nincs ilyen oszlop az adathalmazban, válasszon egy attribútumot, amely egyedileg azonosítja a sort.

## <a name="run-a-workflow"></a>Munkafolyamat futtatása

1. Az **Egyéni modellek** lapon jelölje ki a függőleges három pontot a **Műveletek** oszlopban a korábban létrehozott munkafolyamat mellett.

1. Válassza a **Futtatás** lehetőséget.

A munkafolyamat minden ütemezett frissítéssel együtt automatikusan lefut. További információk az [ütemezett frissítések beállításáról](system.md#schedule-tab).

## <a name="delete-a-workflow"></a>Egy munkafolyamat törlése

1. Az **Egyéni modellek** lapon jelölje ki a függőleges három pontot a **Műveletek** oszlopban a korábban létrehozott munkafolyamat mellett.

1. Válassza a **Törlés** lehetőséget, és hagyja jóvá a törlést.

A munkafolyamat törölve lesz. A munkafolyamat létrehozásakor létrehozott [entitás](entities.md) továbbra is megmarad, és az **Entitások** lapról tekinthető meg.

## <a name="results"></a>EREDMÉNY

A munkafolyamatok eredményeit a modell kimeneti paraméter fázisában beállított entitás tárolja. Ezek az adatok az [entitások oldalról](entities.md) vagy [API-hozzáféréssel](apis.md) érhetőek el.

### <a name="api-access"></a>API-hozzáférés

Ha egy adott OData lekérdezéssel egyéni modellentitásból származó adatokat szeretne lekérni, használja a következő formátumot:

`https://api.ci.ai.dynamics.com/v1/instances/<your instance id>/data/<custom model output entity name>%3Ffilter%3DCustomerId%20eq%20'<guid value>'`

1. Helyettesítse be a `<your instance id>` értékét a Customer Insights környezet azonosítójával, amelyet a Customer Insights elérésekor a böngésző címsorában talál.

1. Helyettesítse be a `<custom model output entity>` értékét az egyéni modellkonfiguráció Modell kimeneti paraméterei lépésében megadott entitásnévre.

1. Helyettesítse be a `<guid value>` értékét annak az ügyfélnek az ügyfél-azonosítójával, akire vonatkozóan el szeretné érni a rekordot. Ez az azonosító általában az [ügyfélprofilok oldalán](customer-profiles.md) a CustomerID mezőben található.

## <a name="frequently-asked-questions"></a>Gyakori kérdések

- Miért nem látható a folyamat egy egyéni modell munkafolyamatának beállításakor?    
  Ezt a problémát gyakran a folyamat konfigurációs problémája okozza. Meg kell győződni arról, hogy a [bemeneti paraméter be van állítva](azure-machine-learning-experiments.md#dataset-configuration), valamint a [kimeneti adattár és elérési út paraméterei](azure-machine-learning-experiments.md#import-pipeline-data-into-customer-insights) is meg vannak adva.

- Mit jelent "Az intelligenciaalapú munkafolyamat mentése nem sikerült" hibaüzenet?    
  A felhasználók általában akkor látják ezt a hibaüzenetet, ha nem rendelkezik tulajdonosi vagy felhasználói hozzáférési rendszergazdai jogosultsággal a munkaterületen. A felhasználónak magasabb szintű engedélyekre van szüksége ahhoz, hogy engedélyezze a Customer Insights számára a munkafolyamat feldolgozását szolgáltatásként, és nem a felhasználói hitelesítő adatokat használni a munkafolyamat későbbi futtatásaiban.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
