---
title: Kapcsolódás a Common Data Model-mappához Azure Data Lake fiók használatával
description: Common Data Model-adatok használata Azure Data Lake Storage segítségével.
ms.date: 09/29/2022
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
ms.openlocfilehash: c12603b9ed8a814356a0f8d0137e97afc749b87c
ms.sourcegitcommit: be341cb69329e507f527409ac4636c18742777d2
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/30/2022
ms.locfileid: "9609945"
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

- A adatforrás kapcsolatot beállító felhasználónak szüksége van a legkevesebb Storage Blob Data közreműködő engedélyre a tárfiókon.

- A Data Lake Storage-ban lévő adatoknak az adatok tárolására vonatkozó Common Data Model szabványt kell követniük, és rendelkezniük kell az adatfájlok sémáját ábrázoló közös adatmodell-jegyzékfájllal (*.csv vagy *.parquet). A jegyzékfájlnak meg kell adnia az entitások részleteit, például az entitásoszlopokat és adattípusokat, valamint az adatfájl helyét és típusát. További információ: [A Common Data Model jegyzékfájl](/common-data-model/sdk/manifest). Ha a jegyzékfájl nincs jelen, a Storage Blob Data Owner vagy Storage Blob Data közreműködő hozzáféréssel rendelkező rendszergazda felhasználók meghatározhatják a sémát az adatok betöltésekor.

## <a name="recommendations"></a>Javaslatok

Az optimális teljesítmény érdekében a Customer Insights azt javasolja, hogy a partíció mérete legfeljebb 1 GB legyen, és a mappában lévő partíciófájlok száma nem haladhatja meg az 1000-et.

## <a name="connect-to-azure-data-lake-storage"></a>Csatlakozás a Azure Data Lake Storage szolgáltatáshoz

1. Válassza az **Adatok** > **Adatforrások** lehetőséget.

1. Válassza az **Adatforrás hozzáadása** lehetőséget.

1. Válassza az Azure Data Lake Storage **lehetőséget**.

   :::image type="content" source="media/data_sources_ADLS.png" alt-text="Párbeszédpanel az Azure Data Lake kapcsolati részleteinek megadásához." lightbox="media/data_sources_ADLS.png":::

1. **Adja meg a adatforrás nevét** és egy opcionális **leírást**. A név egyedileg azonosítja a adatforrás, és az alsóbb rétegbeli folyamatokban hivatkoznak rá, és nem módosítható.

1. Válasszon az alábbi lehetőségek közül a Csatlakozás a tárhely használatával **beállításhoz**. További információ: [Csatlakozás Customer Insights egy Azure Data Lake Storage Gen2-fiókhoz egy Azure-szolgáltatásnévvel](connect-service-principal.md).

   - **Azure-erőforrás**: Adja meg az **erőforrás-azonosítót**. Ha egy tárfiókból szeretne adatokat betölteni egy Azure Private Link, válassza az Enable Private Link (Enable Private Link **) lehetőséget**. További információ: [Privát hivatkozások](security-overview.md#set-up-an-azure-private-link).
   - **Azure-előfizetés**: Válassza ki az **előfizetést**, majd az erőforráscsoportot **és** a **Storage-fiókot**. Ha egy tárfiókból szeretne adatokat betölteni egy Azure Private Link, válassza az Enable Private Link (Enable Private Link **) lehetőséget**. További információ: [Privát hivatkozások](security-overview.md#set-up-an-azure-private-link).
  
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
   > Ha json-szerkesztői felületen szeretne szerkeszteni egy entitást, válassza ki az entitást, majd **a Sémafájl szerkesztése lehetőséget**. Végezze el a módosításokat, és válassza a Mentés **lehetőséget**.

1. A növekményes betöltést igénylő kiválasztott entitások esetében a **Kötelező** a Növekményes frissítés **alatt** jelenik meg. Ezen entitások mindegyikéhez lásd: [Növekményes frissítés konfigurálása Azure Data Lake adatforrásokhoz](incremental-refresh-data-sources.md).

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

   [!INCLUDE [progress-details-include](includes/progress-details-pane.md)]

Az adatok betöltése időbe telhet. A sikeres frissítés után a betöltött adatok az [**Entitások oldalon ellenőrizhetők**](entities.md).

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

1. A növekményes betöltést igénylő kiválasztott entitások esetében a **Kötelező** a Növekményes frissítés **alatt** jelenik meg. Ezen entitások mindegyikéhez lásd: [Növekményes frissítés konfigurálása Azure Data Lake adatforrásokhoz](incremental-refresh-data-sources.md).

1. A kiválasztott entitások esetében, ahol az elsődleges kulcs nincs definiálva, **a Kötelező** érték az Elsődleges kulcs **alatt** jelenik meg. Ezen entitások mindegyikére vonatkozóan:
   1. Válassza a Kötelező **lehetőséget**. Megjelenik a **Szerkesztés entitás** panel.
   1. Válassza ki az **Elsődleges kulcsot**. Az elsődleges kulcs az entitás egyedi attribútuma. Ahhoz, hogy egy attribútum érvényes elsődleges kulcs legyen, az ne tartalmazzon ismétlődő értékeket, a hiányzó értékeket vagy a null értékeket. A karakterlánc, az egész szám és a GUID adattípus attribútumai elsődleges kulcsként támogatottak.
   1. Ha szükséges, módosítsa a partíciós mintát.
   1. Válassza a Bezárás **gombot** a panel mentéséhez és bezárásához.

1. Válassza a **Mentés** parancsot. **Megnyílik az Adatforrások** lap, amelyen az új adatforrás a Frissítés **állapot.**

   [!INCLUDE [progress-details-include](includes/progress-details-pane.md)]

Az adatok betöltése időbe telhet. A sikeres frissítés után a betöltött adatok az [**Entitások oldalon ellenőrizhetők**](entities.md).

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

   - **Engedélyezze Private Link**, ha adatokat szeretne betölteni egy tárfiókból egy Azure Private Link. További információ: [Privát hivatkozások](security-overview.md#set-up-an-azure-private-link).

1. Válassza a **Következő** lehetőséget.
1. Módosítsa a következők bármelyikét:
   - Lépjen egy másik model.json vagy manifest.json fájlhoz a tárolótól eltérő entitáskészlettel.
   - Ha további entitásokat szeretne hozzáadni a betöltéshez, válassza az Új entitás **lehetőséget**.
   - Ha el szeretné távolítani a már kiválasztott entitásokat, ha nincsenek függőségek, válassza ki az entitást és **a Törlés lehetőséget**.
      > [!IMPORTANT]
      > Ha függőségek vannak a meglévő model.json vagy manifest.json fájlhoz és az entitások készletéhez. egy hibaüzenet jelenik meg, és nem választhat másik model.json vagy manifest.json fájlt. A model.json vagy a manifest.json fájl módosítása előtt távolítsa el ezeket a függőségeket, vagy hozzon létre egy új adatforrást a használni kívánt model.json vagy a manifest.json fájllal a függőségek elkerüléséhez szükséges.
   - Az adatfájl helyének vagy az elsődleges kulcsnak a módosításához válassza a Szerkesztés **lehetőséget**.
   - A növekményes betöltési adatok módosításához lásd: [Növekményes frissítés konfigurálása Azure Data Lake adatforrásokhoz](incremental-refresh-data-sources.md).
   - Csak úgy módosítsa az entitás nevét, hogy megfeleljen a .json fájlban található entitás nevének.

     > [!NOTE]
     > A Customer Insightsban az entitás neve mindig ugyanaz maradjon, mint a model.json vagy manifest.json fájlban található entitásnév a betöltés után. A Customer Insights minden rendszerfrissítés során ellenőrzi az összes entitásnevet a model.json vagy a manifest.json fájllal. Ha egy entitás neve megváltozik a Customer Insights alkalmazáson belül vagy azon kívül, hiba történik, mert a Customer Insights nem találja az új entitásnevet a .json fájlban. Ha egy betöltött entitás nevét véletlenül módosították, szerkessze az entitás nevét a Customer Insightsban, hogy az megegyezzen a .json fájlban szereplő névvel.

1. Válassza az Attribútumok **lehetőséget** attribútumok hozzáadásához vagy módosításához, illetve az adatprofil-készítés engedélyezéséhez. Majd válassza a **Kész** lehetőséget.

1. Kattintson a Mentés **gombra** a módosítások alkalmazásához és az **Adatforrások** lapra való visszatéréshez.

   [!INCLUDE [progress-details-include](includes/progress-details-pane.md)]

## <a name="common-reasons-for-ingestion-errors-or-corrupt-data"></a>A betöltési hibák vagy a sérült adatok gyakori okai

Az adatbetöltés során a leggyakoribb okok közül néhány, amiért egy rekord sérültnek tekinthető, a következők:

- Az adattípusok és a mezőértékek nem egyeznek a forrásfájl és a séma között
- A forrásfájl oszlopainak száma nem egyezik meg a sémával
- A mezők olyan karaktereket tartalmaznak, amelyek miatt az oszlopok a várt sémához képest eldőlnek. Például: helytelenül formázott idézőjelek, nem rögzített idézőjelek, újsoros karakterek vagy füles karakterek.
- A partíciós fájlok hiányoznak
- Ha vannak datetime/date/datetimeoffset oszlopok, akkor a formátumukat meg kell adni a sémában, ha az nem követi a szabványos formátumot.

### <a name="schema-or-data-type-mismatch"></a>Séma- vagy adattípus-eltérés

Ha az adatok nem felelnek meg a sémának, a betöltési folyamat hibákkal fejeződik be. Javítsa ki a forrásadatokat vagy a sémát, és töltse be újra az adatokat.

### <a name="partition-files-are-missing"></a>A partíciós fájlok hiányoznak

- Ha a betöltés sérült rekordok nélkül volt sikeres, de nem lát adatokat, szerkessze a model.json vagy a manifest.json fájlt, hogy a partíciók meg legyenek adva. [Ezután frissítse a adatforrás](data-sources.md#refresh-data-sources).

- Ha az adatbetöltés az adatforrások automatikus ütemezési frissítés során történő frissítésével egy időben történik, előfordulhat, hogy a partíciófájlok üresek vagy nem érhetők el a Customer Insights számára a feldolgozáshoz. Az upstream frissítési ütemezéshez való igazodáshoz módosítsa a [rendszerfrissítési ütemtervet](schedule-refresh.md) vagy a adatforrás frissítési ütemezését. Igazítsa az időzítést úgy, hogy a frissítések ne történjenek meg egyszerre, és a Customer Insights szolgáltatásban feldolgozandó legfrissebb adatokat biztosítsa.

### <a name="datetime-fields-in-the-wrong-format"></a>Rossz formátumú Datetime mezők

Az entitás dátumidő mezői nem ISO 8601 vagy en-US formátumban vannak. A Customer Insights alapértelmezett datetime formátuma az en-US formátum. Az entitás összes datetime mezőjének ugyanabban a formátumban kell lennie. A Customer Insights más formátumokat is támogat, feltéve, hogy a megjegyzéseket vagy tulajdonságokat a modell vagy a manifest.json forrás- vagy entitásszintjén készítik el. Például: 

**Model.json fájl**

   ```json
      "annotations": [
        {
          "name": "ci:CustomTimestampFormat",
          "value": "yyyy-MM-dd'T'HH:mm:ss:SSS"
        },
        {
          "name": "ci:CustomDateFormat",
          "value": "yyyy-MM-dd"
        }
      ]   
   ```

  A manifest.json fájlban a datetime formátum az entitás szintjén vagy az attribútum szintjén adható meg. Az entitás szintjén használja az "exhibitsTraits" parancsot az entitásban a *.manifest.cdm.json fájlban a datetime formátum meghatározásához. Az attribútum szintjén használja az "appliedTraits" attribútumot az entityname.cdm.json attribútumában.

**Manifest.json az entitás szintjén**

```json
"exhibitsTraits": [
    {
        "traitReference": "is.formatted.dateTime",
        "arguments": [
            {
                "name": "format",
                "value": "yyyy-MM-dd'T'HH:mm:ss"
            }
        ]
    },
    {
        "traitReference": "is.formatted.date",
        "arguments": [
            {
                "name": "format",
                "value": "yyyy-MM-dd"
            }
        ]
    }
]
```

**Entity.json attribútumszinten**

```json
   {
      "name": "PurchasedOn",
      "appliedTraits": [
        {
          "traitReference": "is.formatted.date",
          "arguments" : [
            {
              "name": "format",
              "value": "yyyy-MM-dd"
            }
          ]
        },
        {
          "traitReference": "is.formatted.dateTime",
          "arguments" : [
            {
              "name": "format",
              "value": "yyyy-MM-ddTHH:mm:ss"
            }
          ]
        }
      ],
      "attributeContext": "POSPurchases/attributeContext/POSPurchases/PurchasedOn",
      "dataFormat": "DateTime"
    }
```

[!INCLUDE [footer-include](includes/footer-banner.md)]
