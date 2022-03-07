---
title: Common Data Model-adatok összekapcsolása egy Azure Data Lake-fiókkal
description: Common Data Model-adatok használata Azure Data Lake Storage segítségével.
ms.date: 01/25/2022
ms.subservice: audience-insights
ms.topic: how-to
author: adkuppa
ms.author: adkuppa
ms.reviewer: mhart
manager: shellyha
searchScope:
- ci-data-sources
- ci-create-data-source
- ci-attach-cdm
- customerInsights
ms.openlocfilehash: 1e3b28316c06d6a15dd5690837c365b0677a882e
ms.sourcegitcommit: 73cb021760516729e696c9a90731304d92e0e1ef
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/25/2022
ms.locfileid: "8354930"
---
# <a name="connect-to-a-common-data-model-folder-using-an-azure-data-lake-account"></a>Kapcsolódás a Common Data Model-mappához Azure Data Lake fiók használatával

A cikkből megtudhatja, hogyan lehet a Common Data Model mappából adatokat betölteni az Azure Data Lake Storage Gen2-fiók segítségével.

## <a name="important-considerations"></a>Fontos tényezők

- Az Azure Data Lake-ben szereplő adatoknak követniük kell a Common Data Model standardot. A többi formátum jelenleg nem támogatott.

- Az adatbetöltés kizárólag csak az Azure Data Lake *Gen2* tárfiókokat támogatja. Az Azure Data Lake Gen1 tárfiókok nem használhatók adatok betöltésére.

- Az Azure Data Lake-tárfiókban engedélyeznie [kell hierarchikus névteret](/azure/storage/blobs/data-lake-storage-namespace).

- Az Azure-egyszerű szolgáltatásnév használatával történő hitelesítéshez ügyeljen arra, hogy az a bérlőn legyen konfigurálva. További információkért lásd: [Célközönség-információk összekapcsolása az Azure Data Lake Storage Gen2 fiókjához az Azure egyszerű szolgáltatásnévvel](connect-service-principal.md).

- Az Azure Data Lake, amelyhez kapcsolódni szeretne, és be szeretné tölteni az adatokat, ugyanabban az Azure régióban kell lennie, mint a Dynamics 365 Customer Insights-környezet. A Common Data Model-mappába egy másik Azure-régióban található adattóból való kapcsolódás nem támogatott. A környezet Azure-régiójának megismeréséhez lépjen a **Rendszergazda** > **Rendszer** > **Névjegy** elemre a célközönség-információkban.

- Az online szolgáltatásokban tárolt adatok más helyen tárolhatók, mint ahol az adatokat feldolgozzák vagy tárolják a Dynamics 365 Customer Insights.Az online szolgáltatásokban tárolt adatok importálásával vagy az azokhoz való csatlakozással Ön elfogadja, hogy az adatok továbbíthatók és tárolhatók a .Dynamics 365 Customer Insights  [További információ a Microsoft Adatvédelmi központban](https://www.microsoft.com/trust-center).

## <a name="connect-to-a-common-data-model-folder"></a>Csatlakozás egy Common Data Model-mappához

1. A célközönség információin belül nyissa meg a következőt **Adatok** > **Adatforrások**.

1. Válassza az **Adatforrás hozzáadása** lehetőséget.

1. Válassza az **Azure Data Lake Storage lehetőséget**, adja meg **a adatforrás nevét**, majd válassza a Tovább **lehetőséget**.

   - Ha a rendszer kéri, válassza ki az iparághoz tartozó minta adatkészletek egyikét, majd válassza a Tovább **lehetőséget**. 

1. Választhat az erőforrás-alapú és az előfizetés-alapú hitelesítés használata között. További információkért lásd: [Célközönség-információk összekapcsolása az Azure Data Lake Storage Gen2 fiókjához az Azure egyszerű szolgáltatásnévvel](connect-service-principal.md). Írja be a **Kiszolgáló címét**, válassza a Bejelentkezés **lehetőséget**, majd válassza a Tovább **lehetőséget**.
   > [!div class="mx-imgBorder"]
   > ![Párbeszédpanelen adja meg az új kapcsolat adatait az Azure Data Lake-hez.](media/enter-new-storage-details.png)
   > [!NOTE]
   > Ahhoz, hogy a tárolóhoz vagy a fenti tárolókhoz kapcsolódhasson, és létre tudja hozni adatforrást a következő szerepkörök egyike szükséges:
   >  - Storage Blob adatolvasó
   >  - Storage Blob adattulajdonos
   >  - Storage Blob adatközreműködő

1. A **Common Data Model-mappa kiválasztása** párbeszédpanelen válassza azt a manifest.json fájlt, amelyből adatokat szeretne importálni, majd válassza a **Következő** lehetőséget.
   > [!NOTE]
   > A környezetben más adatforrással társított egyéb model.json vagy manifest.json fájlok nem jelennek meg a listában.

1. A kijelölt model.json vagy manifest.json fájlban megjelenik az elérhető entitások listája. Tekintse át és válasszon az elérhető entitások listájából, majd válassza a Mentés **lehetőséget**. A rendszer az összes kiválasztott entitást betölti az új adatforrásból.
   > [!div class="mx-imgBorder"]
   > ![Párbeszédpanel, amely az entitások listáját jeleníti meg egy model.json fájlból.](media/review-entities.png)

8. Adja meg, hogy mely adategyeteket szeretné engedélyezni az adatprofilozást, majd válassza a Mentés **lehetőséget**. Az adatprofil-készítés lehetővé teszi az elemzések és egyéb lehetőségek használatát. Kijelölheti a teljes entitást, amely az entitás összes attribútumát kijelöli, vagy kijelölhet bizonyos attribútumokat, amelyeket kiválasztott. Alapértelmezés szerint egyetlen entitás sincs engedélyezve az adatok profilkészítéséhez.
   > [!div class="mx-imgBorder"]
   > ![Adatprofil-készítést megjelenítő párbeszédpanel.](media/dataprofiling-entities.png)

9. A kiválasztott adatok mentése után megnyílik az **Adatforrások** lap. Ekkor a Common Data Model mappa kapcsolatot adatforrásként látja.

> [!NOTE]
> A model.json vagy manifest-json fájl csak egy-egy adatforráshoz társítható ugyanabban a környezetben. Ugyanakkor ugyanez a model.json vagy manifest.json fájl több környezetben is használható adatforrásokhoz.

## <a name="edit-a-common-data-model-folder-data-source"></a>Common Data Model-mappa adatforrás szerkesztése

A Common Data Model-mappát tartalmazó tárfiókhoz tartozó elérési kulcsot frissítheti. A model.json vagy a manifest.json fájlt is módosíthatja. Ha a tárfiókból egy másik tárolóhoz szeretne kapcsolódni, vagy módosítani szeretné a fiók nevét, akkor [hozzon létre egy új adatforrás-kapcsolatot](#connect-to-a-common-data-model-folder).

1. A célközönség információin belül nyissa meg a következőt **Adatok** > **Adatforrások**.

2. A frissíteni kívánt adatforrás mellett jelölje ki a három pontot.

3. Válassza a lista **Szerkesztés** elemét.

4. Opcionálisan frissítse a **Hozzáférési kulcsot**, és válassza a **Tovább** lehetőséget.

   ![Párbeszéd a meglévő adatforráshoz tartozó hozzáférési kulcs szerkesztéséhez és frissítéséhez.](media/edit-access-key.png)

5. Lehetőség van arra, hogy a fiókkulcs-kapcsolatot az erőforrás- vagy előfizetés-alapú kapcsolatra is frissítheti. További információkért lásd: [Célközönség-információk összekapcsolása az Azure Data Lake Storage Gen2 fiókjához az Azure egyszerű szolgáltatásnévvel](connect-service-principal.md). A kapcsolat frissítésekor a **Tárolóra** vonatkozó információk nem módosíthatók.
   > [!div class="mx-imgBorder"]

   > ![Párbeszédpanel az Azure Data Lake kapcsolati adatainak megadásához egy meglévő tárhelyfiókhoz.](media/enter-existing-storage-details.png)

   > [!NOTE]
   > Ahhoz, hogy a tárolóhoz vagy a fenti tárolókhoz kapcsolódhasson, és létre tudja hozni adatforrást a következő szerepkörök egyike szükséges:
   >  - Storage Blob adatolvasó
   >  - Storage Blob adattulajdonos
   >  - Storage Blob adatközreműködő


6. Másik model.json vagy manifest.json fájl is választható, a tárolóból származó más entitáskészletekkel.

7. Tetszés szerint kiválaszthat további entitásokat is, amelyeket betölthet. Ha nincsenek függőségek, akkor a már kijelölt entitásokat is eltávolíthatja.

   > [!IMPORTANT]
   > Ha függőségek vannak a meglévő model.json vagy manifest.json fájlhoz és az entitások készletéhez. egy hibaüzenet jelenik meg, és nem választhat másik model.json vagy manifest.json fájlt. A model.json vagy a manifest.json fájl módosítása előtt távolítsa el ezeket a függőségeket, vagy hozzon létre egy új adatforrást a használni kívánt model.json vagy a manifest.json fájllal a függőségek elkerüléséhez szükséges.

8. Tetszés szerint kiválaszthat további attribútumokat vagy entitásokat, amelyek lehetővé teszik az adatok profilkészítésének engedélyezését vagy letiltását a már kijelöltek esetén.   


[!INCLUDE[footer-include](../includes/footer-banner.md)]
