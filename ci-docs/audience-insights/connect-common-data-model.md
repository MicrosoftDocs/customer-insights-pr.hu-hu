---
title: Common Data Model-adatok összekapcsolása egy Azure Data Lake-fiókkal
description: Common Data Model-adatok használata Azure Data Lake Storage segítségével.
ms.date: 05/29/2020
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: adkuppa
ms.author: adkuppa
ms.reviewer: mhart
manager: shellyha
ms.openlocfilehash: 385406b706890d741fec2694c190c0fada7809d7
ms.sourcegitcommit: bae40184312ab27b95c140a044875c2daea37951
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/15/2021
ms.locfileid: "5596548"
---
# <a name="connect-to-a-common-data-model-folder-using-an-azure-data-lake-account"></a>Kapcsolódás a Common Data Model-mappához Azure Data Lake fiók használatával

A cikkből megtudhatja, hogyan lehet a Common Data Model mappából adatokat betölteni az Azure Data Lake Storage Gen2-fiók segítségével.

## <a name="important-considerations"></a>Fontos tényezők

- Az Azure Data Lake-ben szereplő adatoknak követniük kell a Common Data Model standardot. A többi formátum jelenleg nem támogatott.

- Az adatbetöltés kizárólag csak az Azure Data Lake *Gen2* tárfiókokat támogatja. Az Azure Data Lake Gen1 tárfiókok nem használhatók adatok betöltésére.

- Az Azure-egyszerű szolgáltatásnév használatával történő hitelesítéshez ügyeljen arra, hogy az a bérlőn legyen konfigurálva. További információkért lásd: [Célközönség-információk összekapcsolása az Azure Data Lake Storage Gen2 fiókjához az Azure egyszerű szolgáltatásnévvel](connect-service-principal.md).

- Az Azure Data Lake, amelyhez kapcsolódni szeretne, és be szeretné tölteni az adatokat, ugyanabban az Azure régióban kell lennie, mint a Dynamics 365 Customer Insights-környezet. A Common Data Model-mappába egy másik Azure-régióban található adattóból való kapcsolódás nem támogatott. A környezet Azure-régiójának megismeréséhez lépjen a **Rendszergazda** > **Rendszer** > **Névjegy** elemre a célközönség-információkban.

- Az online szolgáltatásokban tárolt adatok más helyen is tárolhatók, mint ahol az adatok feldolgozása vagy tárolása történik a Dynamics 365 Customer Insights szolgáltatásban. Az online szolgáltatásokban tárolt adatok importálásával vagy az ahhoz való kapcsolódással Ön elfogadja, hogy az adatok átvihetők és tárolhatók a Dynamics 365 Customer Insights alkalmazásban.  [Ismerje meg a Microsoft adatvédelmi központot](https://www.microsoft.com/trust-center)

## <a name="connect-to-a-common-data-model-folder"></a>Csatlakozás egy Common Data Model-mappához

1. A célközönség információin belül nyissa meg a következőt **Adatok** > **Adatforrások**.

1. Válassza az **Adatforrás hozzáadása** lehetőséget.

1. Válassza a **Csatlakozás egy Common Data Model-mappához** lehetőséget , írja be az adatforrás **Nevét**, majd válassza a **Következő** lehetőséget. Névvel kapcsolatos irányelvek: 
   - Kezdje egy betűvel.
   - Csak betűket és számokat használjon. Speciális karakterek és szóközök nem adhatók meg.
   - 3–64 karakter használható.

1. Választhat az erőforrás-alapú és az előfizetés-alapú hitelesítés használata között. További információkért lásd: [Célközönség-információk összekapcsolása az Azure Data Lake Storage Gen2 fiókjához az Azure egyszerű szolgáltatásnévvel](connect-service-principal.md). Adja meg a **Tároló** adatait, és válassza a **Következő** lehetőséget.
   > [!div class="mx-imgBorder"]
   > ![Párbeszédpanelen adja meg az új kapcsolat adatait az Azure Data Lake-hez](media/enter-new-storage-details.png)
   > [!NOTE]
   > Ahhoz, hogy a tárolóhoz vagy a fenti tárolókhoz kapcsolódhasson, és létre tudja hozni adatforrást a következő szerepkörök egyike szükséges:
   >  - Storage Blob adatolvasó
   >  - Storage Blob adattulajdonos
   >  - Storage Blob adatközreműködő

1. A **Common Data Model-mappa kiválasztása** párbeszédpanelen válassza azt a manifest.json fájlt, amelyből adatokat szeretne importálni, majd válassza a **Következő** lehetőséget.
   > [!NOTE]
   > A környezetben más adatforrással társított egyéb model.json vagy manifest.json fájlok nem jelennek meg a listában.

1. A kiválasztott model.json vagy manifest.json fájlban a rendelkezésre álló entitások listája látható. Áttekinthet és kiválaszthat rendelkezésre álló entitások listájából, és válassza a **Mentés** lehetőséget. A rendszer az összes kiválasztott entitást betölti az új adatforrásból.
   > [!div class="mx-imgBorder"]
   > ![Párbeszédpanel, amely az entitások listáját jeleníti meg egy model.json fájlból](media/review-entities.png)

8. Adja meg, hogy milyen adatentitásokat szeretne az adatprofil-készítés engedélyezéséhez, és válassza a **Mentést**. Az adatprofil-készítés lehetővé teszi az elemzések és egyéb lehetőségek használatát. Kijelölheti a teljes entitást, amely az entitás összes attribútumát kijelöli, vagy kijelölhet bizonyos attribútumokat, amelyeket kiválasztott. Alapértelmezés szerint egyetlen entitás sincs engedélyezve az adatok profilkészítéséhez.
   > [!div class="mx-imgBorder"]
   > ![Adatprofil-készítést megjelenítő párbeszédpanel](media/dataprofiling-entities.png)

9. A kiválasztott adatok mentése után megnyílik az **Adatforrások** lap. Ekkor a Common Data Model mappa kapcsolatot adatforrásként látja.

> [!NOTE]
> A model.json vagy manifest-json fájl csak egy-egy adatforráshoz társítható ugyanabban a környezetben. Ugyanakkor ugyanez a model.json vagy manifest.json fájl több környezetben is használható adatforrásokhoz.

## <a name="edit-a-common-data-model-folder-data-source"></a>Common Data Model-mappa adatforrás szerkesztése

A Common Data Model-mappát tartalmazó tárfiókhoz tartozó elérési kulcsot frissítheti. A model.json vagy a manifest.json fájlt is módosíthatja. Ha a tárfiókból egy másik tárolóhoz szeretne kapcsolódni, vagy módosítani szeretné a fiók nevét, akkor [hozzon létre egy új adatforrás-kapcsolatot](#connect-to-a-common-data-model-folder).

1. A célközönség információin belül nyissa meg a következőt **Adatok** > **Adatforrások**.

2. A frissíteni kívánt adatforrás mellett jelölje ki a három pontot.

3. Válassza a lista **Szerkesztés** elemét.

4. Opcionálisan frissítse a **Hozzáférési kulcsot**, és válassza a **Tovább** lehetőséget.

   ![Párbeszéd a meglévő adatforráshoz tartozó hozzáférési kulcs szerkesztéséhez és frissítéséhez](media/edit-access-key.png)

5. Lehetőség van arra, hogy a fiókkulcs-kapcsolatot az erőforrás- vagy előfizetés-alapú kapcsolatra is frissítheti. További információkért lásd: [Célközönség-információk összekapcsolása az Azure Data Lake Storage Gen2 fiókjához az Azure egyszerű szolgáltatásnévvel](connect-service-principal.md). A kapcsolat frissítésekor a **Tárolóra** vonatkozó információk nem módosíthatók.
   > [!div class="mx-imgBorder"]

   > ![Párbeszédpanel az Azure Data Lake kapcsolati adatainak megadásához egy meglévő tárhelyfiókhoz](media/enter-existing-storage-details.png)

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