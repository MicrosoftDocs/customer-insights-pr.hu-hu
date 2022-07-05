---
title: Kapcsolódás a Common Data Model-mappához Azure Data Lake fiók használatával
description: Common Data Model-adatok használata Azure Data Lake Storage segítségével.
ms.date: 05/30/2022
ms.topic: how-to
author: mukeshpo
ms.author: mukeshpo
ms.reviewer: v-wendysmith
manager: shellyha
searchScope:
- ci-data-sources
- ci-create-data-source
- ci-attach-cdm
- customerInsights
ms.openlocfilehash: b1cdcb46df17d722ad49d361ae4c7ab34c83eeb1
ms.sourcegitcommit: dca46afb9e23ba87a0ff59a1776c1d139e209a32
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/29/2022
ms.locfileid: "9082260"
---
# <a name="connect-to-data-in-azure-data-lake-storage"></a>Csatlakozás az adatokhoz a Azure Data Lake Storage-ban

Adatok betöltése a Dynamics 365 Customer Insights Gen2-fiók használatába Azure Data Lake Storage. Az adatbetöltés lehet teljes vagy növekményes.

## <a name="prerequisites"></a>Előfeltételek

- Az adatbetöltés kizárólag a Gen2-fiókokat Azure Data Lake Storage támogatja *·*. A Data Lake Storage Gen1-fiókok nem használhatók adatok betöltésére.

- A Azure Data Lake Storage fiókban engedélyezni kell [hierarchikus névteret](/azure/storage/blobs/data-lake-storage-namespace). Az adatokat hierarchikus mappa formátumban kell tárolni, amely meghatározza a gyökérmappát, és almappákkal rendelkezik az egyes entitásokhoz. Az almappák teljes adattal vagy növekményes adatmappákkal rendelkezhetnek.

- Az Azure-egyszerű szolgáltatásnév használatával történő hitelesítéshez ügyeljen arra, hogy az a bérlőn legyen konfigurálva. További információ: [Csatlakozás Azure Data Lake Storage Gen2-fiókhoz Azure-szolgáltatásnévvel](connect-service-principal.md).

- A Azure Data Lake Storage csatlakoztatni és adatokat be szeretné tölteni, ugyanabban az Azure-régióban kell lennie, mint a Dynamics 365 Customer Insights környezetnek. A Common Data Model-mappába egy másik Azure-régióban található adattóból való kapcsolódás nem támogatott. A környezet Azure-régiójának megismeréséhez tekintse meg **a Felügyeleti** > **rendszer** > **névjegye** a Customer Insights-bancímű témakört.

- Az online szolgáltatásokban tárolt adatok más helyen is tárolhatók, mint ahol az adatokat feldolgozzák vagy tárolják Dynamics 365 Customer Insights.Az online szolgáltatásokban tárolt adatok importálásával vagy az azokhoz való csatlakozással Ön elfogadja, hogy az adatok átvihetők és tárolhatók a következőkkel: Dynamics 365 Customer Insights. [További információt a Microsoft Adatvédelmi központban talál](https://www.microsoft.com/trust-center).

- A Customer Insights szolgáltatásnévnek az alábbi szerepkörök egyikében kell lennie a tárfiók eléréséhez. További információ: [Engedélyek megadása a szolgáltatásnévnek a tárfiók](connect-service-principal.md#grant-permissions-to-the-service-principal-to-access-the-storage-account) eléréséhez.
  - Storage Blob adatolvasó
  - Storage Blob adattulajdonos
  - Storage Blob adatközreműködő

- A Data Lake Storage-ban lévő adatoknak az adatok tárolására vonatkozó Common Data Model szabványt kell követniük, és rendelkezniük kell az adatfájlok sémáját ábrázoló közös adatmodell-jegyzékfájllal (*.csv vagy *.parquet). A jegyzékfájlnak meg kell adnia az entitások részleteit, például az entitásoszlopokat és adattípusokat, valamint az adatfájl helyét és típusát. További információ: [A Common Data Model jegyzékfájl](/common-data-model/sdk/manifest). Ha a jegyzékfájl nincs jelen, a Storage Blob Data Owner vagy Storage Blob Data közreműködő hozzáféréssel rendelkező rendszergazda felhasználók meghatározhatják a sémát az adatok betöltésekor.

## <a name="connect-to-azure-data-lake-storage"></a>Csatlakozás a Azure Data Lake Storage alkalmazáshoz

1. Válassza az **Adatok** > **Adatforrások** lehetőséget.

1. Válassza az **Adatforrás hozzáadása** lehetőséget.

1. Válassza az Azure Data Lake Storage **lehetőséget**.

   :::image type="content" source="media/data_sources_ADLS.png" alt-text="Párbeszédpanel az Azure Data Lake kapcsolati részleteinek megadásához." lightbox="media/data_sources_ADLS.png":::

1. **Adja meg a adatforrás nevét** és egy opcionális **leírást**. A név egyedileg azonosítja a adatforrás, és az alsóbb rétegbeli folyamatokban hivatkoznak rá, és nem módosítható.

1. Válasszon az alábbi lehetőségek közül a Csatlakozás a tárhely használatával **beállításhoz**. További információ: [Csatlakozás Customer Insights egy Azure Data Lake Storage Gen2-fiókhoz egy Azure-szolgáltatásnévvel](connect-service-principal.md).

   - **Azure-erőforrás**: Adja meg az **erőforrás-azonosítót**. Ha egy tárfiókból szeretne adatokat betölteni egy Azure Private Link, válassza az Enable Private Link (Enable Private Link **) lehetőséget**. További információ: [Privát hivatkozások](security-overview.md#private-links-tab).
   - **Azure-előfizetés**: Válassza ki az **előfizetést**, majd az erőforráscsoportot **és** a **Storage-fiókot**. Ha egy tárfiókból szeretne adatokat betölteni egy Azure Private Link, válassza az Enable Private Link (Enable Private Link **) lehetőséget**. További információ: [Privát hivatkozások](security-overview.md#private-links-tab).
  
   > [!NOTE]
   > A adatforrás létrehozásához az alábbi szerepkörök egyikére van szükség a tárolóhoz vagy a tárfiókhoz:
   >
   >  - Storage Blob Data olvasó elegendő ahhoz, hogy beolvassa a tárfiókból, és betöltse az adatokat a Customer Insightsba. 
   >  - Storage Blob Data közreműködő vagy tulajdonosra van szükség, ha a jegyzékfájlokat közvetlenül a Customer Insightsban szeretné szerkeszteni.  
  
1. Válassza ki annak a tárolónak **a** nevét, amely tartalmazza az adatokat és a sémát (model.json vagy manifest.json fájl), amelyből adatokat szeretne importálni, majd kattintson a Tovább **gombra**.
   > [!NOTE]
   > A környezetben más adatforrással társított egyéb model.json vagy manifest.json fájlok nem jelennek meg a listában. Ugyanakkor ugyanez a model.json vagy manifest.json fájl több környezetben is használható adatforrásokhoz.

1. Új séma létrehozásához lépjen [az Új sémafájl](#create-a-new-schema-file) létrehozásaelemre.

1. Meglévő séma használatához keresse meg a model.json vagy manifest.cdm.json fájlt tartalmazó mappát. A könyvtáron belül keresheti meg a fájlt.

1. Válassza ki a JSON-fájlt, majd kattintson a Tovább **gombra**. Megjelenik az elérhető entitások listája.

   :::image type="content" source="media/review-entities.png" alt-text="A kiválasztandó entitások listájának párbeszédpanelje":::

1. Válassza ki a felvenni kívánt entitásokat.

   :::image type="content" source="media/ADLS_required.png" alt-text="Az elsődleges kulcshoz szükséges párbeszédpanel":::

   > [!TIP]
   > A JSON-szerkesztési felületen lévő entitások szerkesztéséhez válassza a További **sémafájl** > **szerkesztése lehetőséget**. Végezze el a módosításokat, és válassza a Mentés **lehetőséget**.

1. A növekményes betöltést igénylő kiválasztott entitások esetében a **Kötelező** a Növekményes frissítés alatt **jelenik meg**. Ezen entitások mindegyikéhez lásd: [Növekményes frissítés konfigurálása Azure Data Lake adatforrásokhoz](incremental-refresh-data-sources.md).

1. A kiválasztott entitások esetében, ahol az elsődleges kulcs nincs definiálva, **a Kötelező** érték az Elsődleges kulcs **alatt** jelenik meg. Ezen entitások mindegyikére vonatkozóan:
   1. Válassza a Kötelező **lehetőséget**. Megjelenik a **Szerkesztés entitás** panel.
   1. Válassza ki az **Elsődleges kulcsot**. Az elsődleges kulcs az entitás egyedi attribútuma. Ahhoz, hogy egy attribútum érvényes elsődleges kulcs legyen, az ne tartalmazzon ismétlődő értékeket, a hiányzó értékeket vagy a null értékeket. A karakterlánc, az egész szám és a GUID adattípus attribútumai elsődleges kulcsként támogatottak.
   1. Ha szükséges, módosítsa a partíciós mintát.
   1. Válassza a Bezárás **gombot** a panel mentéséhez és bezárásához.

1. Válassza ki az attribútumok számát **az egyes belefoglalt entitásokhoz**. Megjelenik az **Attribútumok** kezelése lap.

   :::image type="content" source="media/dataprofiling-entities.png" alt-text="Párbeszédpanel az adatprofil-készítés kiválasztásához.":::

   1. Hozzon létre új attribútumokat, szerkessze vagy törölje a meglévő attribútumokat. Módosíthatja a nevet, az adatformátumot, vagy hozzáadhat egy szemantikai típust.
   1. Az elemzések és egyéb képességek engedélyezéséhez válassza az Adatprofil-készítés **lehetőséget** a teljes entitáshoz vagy adott attribútumokhoz. Alapértelmezés szerint egyetlen entitás sincs engedélyezve az adatok profilkészítéséhez.
   1. Válassza a **Kész** lehetőséget.

1. Válassza a **Mentés** parancsot. **Megnyílik az Adatforrások** lap, amelyen az új adatforrás a Frissítés **állapot.**

### <a name="create-a-new-schema-file"></a>Új sémafájl létrehozása

1. Válassza az Új sémafájl **lehetőséget**.

1. Adja meg a fájl nevét, majd válassza a Mentés **lehetőséget**.

1. Válassza az Új entitás **lehetőséget**. **Megjelenik az Új entitás** panel.

1. Adja meg az entitás nevét, és válassza ki az **adatfájlok helyét**.
   - **Több .csv- vagy .parquet-fájl**: Tallózással keresse meg a gyökérmappát, válassza ki a minta típusát, és írja be a kifejezést.
   - **Egyetlen .csv- vagy .parquet-fájl**: Keresse meg a .csv- vagy .parquet-fájlt, és jelölje ki.

   :::image type="content" source="media/ADLS_new_entity_location.png" alt-text="Párbeszédpanel új entitás létrehozásához, amelyen ki van emelve az adatfájlok helye.":::

1. Válassza a **Mentés** parancsot.

   :::image type="content" source="media/ADLS_new_entity_define_attributes.png" alt-text="Párbeszédpanel attribútumok definiálásához vagy automatikus létrehozásához.":::

1. Válassza **az attribútumok** definiálása lehetőséget az attribútumok manuális hozzáadásához, vagy válassza az automatikus létrehozásuk **lehetőséget**. Az attribútumok meghatározásához adjon meg egy nevet, válassza ki az adatformátumot és a választható szemantikai típust. Automatikusan generált attribútumok esetén:

   1. Az attribútumok automatikus létrehozása után válassza az Attribútumok **áttekintése lehetőséget**. Megjelenik az **Attribútumok** kezelése lap.

   1. Győződjön meg arról, hogy az adatformátum minden attribútumhoz megfelelő.

   1. Az elemzések és egyéb képességek engedélyezéséhez válassza az Adatprofil-készítés **lehetőséget** a teljes entitáshoz vagy adott attribútumokhoz. Alapértelmezés szerint egyetlen entitás sincs engedélyezve az adatok profilkészítéséhez.

      :::image type="content" source="media/dataprofiling-entities.png" alt-text="Párbeszédpanel az adatprofil-készítés kiválasztásához.":::

   1. Válassza a **Kész** lehetőséget. Megjelenik az **Entitások** kiválasztása lap.

1. Adott esetben folytassa az entitások és attribútumok hozzáadását.

1. Az összes entitás hozzáadása után válassza a Belefoglalás **lehetőséget** az entitások adatforrás való szerepeltetéshez.

   :::image type="content" source="media/ADLS_required.png" alt-text="Az elsődleges kulcshoz szükséges párbeszédpanel":::

1. A növekményes betöltést igénylő kiválasztott entitások esetében a **Kötelező** a Növekményes frissítés alatt **jelenik meg**. Ezen entitások mindegyikéhez lásd: [Növekményes frissítés konfigurálása Azure Data Lake adatforrásokhoz](incremental-refresh-data-sources.md).

1. A kiválasztott entitások esetében, ahol az elsődleges kulcs nincs definiálva, **a Kötelező** érték az Elsődleges kulcs **alatt** jelenik meg. Ezen entitások mindegyikére vonatkozóan:
   1. Válassza a Kötelező **lehetőséget**. Megjelenik a **Szerkesztés entitás** panel.
   1. Válassza ki az **Elsődleges kulcsot**. Az elsődleges kulcs az entitás egyedi attribútuma. Ahhoz, hogy egy attribútum érvényes elsődleges kulcs legyen, az ne tartalmazzon ismétlődő értékeket, a hiányzó értékeket vagy a null értékeket. A karakterlánc, az egész szám és a GUID adattípus attribútumai elsődleges kulcsként támogatottak.
   1. Ha szükséges, módosítsa a partíciós mintát.
   1. Válassza a Bezárás **gombot** a panel mentéséhez és bezárásához.

1. Válassza a **Mentés** parancsot. **Megnyílik az Adatforrások** lap, amelyen az új adatforrás a Frissítés **állapot.**


## <a name="edit-an-azure-data-lake-storage-data-source"></a>Azure Data Lake Storage adatforrás szerkesztése

A Csatlakozás tárfiókhoz lehetőséget *frissítheti*. További információ: [Csatlakozás Customer Insights egy Azure Data Lake Storage Gen2-fiókhoz egy Azure-szolgáltatásnévvel](connect-service-principal.md). Ha a tárfiókból egy másik tárolóhoz szeretne kapcsolódni, vagy módosítani szeretné a fiók nevét, akkor [hozzon létre egy új adatforrás-kapcsolatot](#connect-to-azure-data-lake-storage).

1. Válassza az **Adatok** > **Adatforrások** lehetőséget.

1. A frissíteni kívánt adatforrás mellett válassza a Szerkesztés **lehetőséget**.

   :::image type="content" source="media/data_sources_edit_ADLS.png" alt-text="Párbeszédpanel az Azure Data Lake adatforrás szerkesztéséhez.":::

1. Módosítsa a következő információk bármelyikét:

   - **Ismertetés**
   - **Csatlakoztassa a tárhelyet a kapcsolat adataival** és a kapcsolati adatokkal. A kapcsolat frissítésekor a **Tárolóra** vonatkozó információk nem módosíthatók.
      > [!NOTE]
      > A következő szerepkörök egyikét hozzá kell rendelni a tárfiókhoz vagy a tárolóhoz:
        > - Storage Blob adatolvasó
        > - Storage Blob adattulajdonos
        > - Storage Blob adatközreműködő

   - **Engedélyezze Private Link**, ha adatokat szeretne betölteni egy tárfiókból egy Azure Private Link. További információ: [Privát hivatkozások](security-overview.md#private-links-tab).

1. Válassza a **Következő** lehetőséget.
1. Módosítsa a következők bármelyikét:
   - Lépjen egy másik model.json vagy manifest.json fájlhoz a tárolótól eltérő entitáskészlettel.
   - Ha további entitásokat szeretne hozzáadni a betöltéshez, válassza az Új entitás **lehetőséget**.
   - Ha el szeretné távolítani a már kiválasztott entitásokat, ha nincsenek függőségek, válassza ki az entitást és **a Törlés lehetőséget**.
      > [!IMPORTANT]
      > Ha függőségek vannak a meglévő model.json vagy manifest.json fájlhoz és az entitások készletéhez. egy hibaüzenet jelenik meg, és nem választhat másik model.json vagy manifest.json fájlt. A model.json vagy a manifest.json fájl módosítása előtt távolítsa el ezeket a függőségeket, vagy hozzon létre egy új adatforrást a használni kívánt model.json vagy a manifest.json fájllal a függőségek elkerüléséhez szükséges.
   - Az adatfájl helyének vagy az elsődleges kulcsnak a módosításához válassza a Szerkesztés **lehetőséget**.
   - A növekményes betöltési adatok módosításához lásd: [Növekményes frissítés konfigurálása Azure Data Lake adatforrásokhoz](incremental-refresh-data-sources.md)

1. Válassza az Attribútumok **lehetőséget** attribútumok hozzáadásához vagy módosításához, illetve az adatprofil-készítés engedélyezéséhez. Majd válassza a **Kész** lehetőséget.

1. Kattintson a Mentés **gombra** a módosítások alkalmazásához és az **Adatforrások** lapra való visszatéréshez.
