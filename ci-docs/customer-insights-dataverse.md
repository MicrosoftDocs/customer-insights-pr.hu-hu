---
title: A Customer Insights-adatok használata a Microsoft Dataverse-ben
description: Ismerje meg, hogyan csatlakoztathatja a Customer Insights szolgáltatást, és Microsoft Dataverse hogyan értelmezheti a kimeneti entitásokat, amelyek a következőre vannak exportálva:Dataverse.
ms.date: 08/25/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: conceptual
author: mukeshpo
ms.author: mukeshpo
manager: shellyha
searchScope:
- ci-system-diagnostic
- customerInsights
ms.openlocfilehash: dfa63110fc5291f2b63aebf588d6fdd20ed4ab67
ms.sourcegitcommit: 134aac66e3e0b77b2e96a595d6acbb91bf9afda2
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/07/2022
ms.locfileid: "9424312"
---
# <a name="work-with-customer-insights-data-in-microsoft-dataverse"></a>A Customer Insights-adatok használata a Microsoft Dataverse-ben

A Customer Insights lehetőséget biztosít a kimeneti entitások elérhetővé tételére a [Microsoft Dataverse](/powerapps/maker/data-platform/data-platform-intro)-ben. Ez az integráció egyszerű adatmegosztást és egyéni fejlesztést tesz lehetővé a kevés kódolást igénylő/kód nélküli megközelítéssel. A [kimeneti entitások](#output-entities) táblákként érhetők el egy Dataverse környezetben. Az adatokat táblák alapján Dataverse bármely más alkalmazáshoz használhatja. Ezek a táblák olyan forgatókönyveket tesznek lehetővé, mint az automatizált munkafolyamatok vagy Power Automate az alkalmazások létrehozása Power Apps.

A környezethez való Dataverse csatlakozás azt is lehetővé teszi, hogy [adatfolyamok és átjárók használatával Power Platform adatokat töltsön be helyszíni adatforrásokból](connect-power-query.md#add-data-from-on-premises-data-sources).

## <a name="prerequisites"></a>Előfeltételek

- A Customer Insights-nak és Dataverse a környezeteknek ugyanabban a régióban kell üzemeltetniük.
- A környezetben beállított Dataverse globális rendszergazdai szerepkör. Ellenőrizze, hogy ez a környezet hozzá van-e [Dataverse társítva](/power-platform/admin/control-user-access#associate-a-security-group-with-a-dataverse-environment) bizonyos biztonsági csoportokhoz, és győződjön meg arról, hogy hozzá van adva ezekhez a biztonsági csoportokhoz.
- Nincs még olyan Customer Insights-környezet, amely a csatlakoztatni kívánt környezethez van Dataverse társítva. Ismerje meg, [hogyan távolíthat el egy meglévő kapcsolatot egy Dataverse környezettel](#remove-an-existing-connection-to-a-dataverse-environment).
- Egyetlen Microsoft Dataverse tárfiókhoz csatlakoztatott környezet, ha a környezetet [a .Azure Data Lake Storage](own-data-lake-storage.md)

## <a name="dataverse-storage-capacity-entitlement"></a>Dataverse tárolási kapacitásra való jogosultság

A Customer Insights-előfizetéssel további kapacitásra jogosult a szervezet meglévő [Dataverse tárolókapacitása](/power-platform/admin/capacity-storage) számára. A hozzáadott kapacitás az előfizetés által használt profilok számától függ.

**Példa:**

Feltéve, hogy 100 000 ügyfélprofilonként 15 GB-os adatbázis-tárterületet és 20 GB-os fájltárhelyet kap. Ha az előfizetése 300 000 ügyfélprofilt tartalmaz, a teljes tárolókapacitás 45 GB (3 x 15 GB) adatbázis-tárterület és 60 GB-os fájltárolás (3 x 20 GB). Hasonlóképpen, ha 30K-fiókkal rendelkező B-to-B előfizetéssel rendelkezik, a teljes tárolókapacitás 45 GB (3 x 15 GB) adatbázis-tárterület és 60 GB-os fájltárolás (3 x 20 GB).

A naplókapacitás nem növekményes és nem rögzített a szervezet számára.

A részletes kapacitásjogosultságokkal kapcsolatos további információkért lásd: [Dynamics 365 licencelési útmutató](https://go.microsoft.com/fwlink/?LinkId=866544).

## <a name="connect-a-dataverse-environment-to-customer-insights"></a>Dataverse Környezet csatlakoztatása a Customer Insights szolgáltatáshoz

A **Microsoft Dataverse** lépés lehetővé teszi, hogy összekapcsolja a Customer Insights-t a Dataverse környezetével, miközben [létrehoz egy Customer Insights-környezetet](create-environment.md).

:::image type="content" source="media/dataverse-provisioning.png" alt-text="adatmegosztás automatikus engedélyezésével Microsoft Dataverse az új környezetekben.":::

1. Adja meg a környezet URL-címét, Dataverse vagy hagyja üresen, hogy létrehozzon egyet az Ön számára.

   > [!NOTE]
   > Miután létrehozta a kapcsolatot a Customer Insights és Dataverse a, ne módosítsa a környezet szervezetnevét Dataverse. A rendszer a szervezet nevét használja az Dataverse URL-címben, és egy módosított név megszakítja a kapcsolatot a Customer Insights szolgáltatással.

   [Power Platform a rendszergazdák szabályozhatják, hogy ki hozhat létre új Dataverse környezeteket](/power-platform/admin/control-environment-creation). Ha új Customer Insights-környezetet próbál beállítani, de nem tudja, előfordulhat, hogy a rendszergazda a rendszergazdák kivételével mindenki számára letiltotta a környezetek létrehozását Dataverse.

1. Ha saját Data Lake Storage-fiókját használja:
   1. Válassza az **Adatmegosztás** engedélyezése Dataverse.
   1. Adja meg az **Engedélyek azonosítóját**. Az engedélyazonosító [megszerzéséhez engedélyezze az adatmegosztást Dataverse a saját Azure Data Lake Storage](#enable-data-sharing-with-dataverse-from-your-own-azure-data-lake-storage-preview).

## <a name="enable-data-sharing-with-dataverse-from-your-own-azure-data-lake-storage-preview"></a>A sajátoddal Dataverse való Azure Data Lake Storage adatmegosztás engedélyezése (előzetes verzió)

A saját [fiókjában Azure Data Lake Storage](own-data-lake-storage.md) ellenőrizze, hogy a Customer Insights-környezetet beállító felhasználó rendelkezik-e legalább **Storage Blob Data olvasó** engedélyekkel a `customerinsights` tárfiók tárolóján.

### <a name="limitations"></a>Korlátozások

- Csak egy-az-egyhez leképezés egy Dataverse szervezet és egy Azure Data Lake Storage fiók között. Miután egy Dataverse szervezet csatlakozott egy tárfiókhoz, nem tud csatlakozni egy másik tárfiókhoz. Ez a korlátozás megakadályozza Dataverse több tárfiók feltöltését.
- Az adatmegosztás nem fog működni, ha Azure Private Link beállításra van szükség a fiók eléréséhez Azure Data Lake Storage, mert az tűzfal mögött van. Dataverse jelenleg nem támogatja a privát végpontokhoz való csatlakozást a Private Link.

### <a name="set-up-security-groups-on-your-own-azure-data-lake-storage"></a>Biztonsági csoportok beállítása saját maga által Azure Data Lake Storage

1. Hozzon létre két biztonsági csoportot az Azure-előfizetésében – egyet **olvasó** biztonsági csoportot és egy **közreműködő** biztonsági csoportot, és állítsa be a Microsoft Dataverse szolgáltatást mindkét biztonsági csoport tulajdonosaként.

1. A tárfiókban lévő tárolón található `customerinsights` hozzáférés-vezérlési listát (ACL) ezeken a biztonsági csoportokon keresztül kezelheti.
   1. Adja hozzá a Microsoft Dataverse szolgáltatást és minden olyan Dataverse alapú üzleti alkalmazást, mint a Dynamics 365 Marketing, a **olvasó** biztonsági csoporthoz, csak **olvasási engedélyekkel**.
   1. Csak *a Customers Insights alkalmazást adja hozzá* a **közreműködő** biztonsági csoporthoz, hogy olvasási és írási **engedélyeket is** adjon a profilok és elemzések írásához.

### <a name="set-up-powershell"></a>A PowerShell beállítása

Állítsa be a PowerShellt a PowerShell-szkriptek végrehajtásához.

1. Telepítse a PowerShell legújabb verzióját [Azure Active Directory a Graph](/powershell/azure/active-directory/install-adv2).
   1. A számítógépen nyomja le a Windows gombot a billentyűzeten, és keressen a **Windows PowerShell** kifejezésre, és válassza a **Futtatás rendszergazdaként** lehetőséget.
   1. A megnyíló PowerShell ablakában adja meg az `Install-Module AzureAD` értéket.

1. Három modul importálása.
   1. A PowerShell ablakban adja meg `Install-Module -Name Az.Accounts` és kövesse a lépéseket.
   1. Ismételje meg a és `Install-Module -Name Az.Resources``Install-Module -Name Az.Storage`.

### <a name="execute-powershell-scripts-and-obtain-the-permission-identifier"></a>PowerShell-szkriptek végrehajtása és az engedélyazonosító beszerzése

1. Töltse le a futtatásához szükséges két PowerShell-szkriptet a mérnökünk [GitHub-adattárából](https://github.com/trin-msft/byol).
   - `CreateSecurityGroups.ps1`: Bérlői rendszergazdai engedélyeket igényel.
   - `ByolSetup.ps1`: Storage Blob-adattulajdonosi engedélyeket igényel a tárfiók/tároló szintjén. Ez a szkript létrehozza az engedélyt az Ön számára. A szerepkör-hozzárendelés manuálisan is eltávolítható a szkript sikeres futtatása után.

1. Hajtsa végre `CreateSecurityGroups.ps1` a Windows PowerShellben a Azure Data Lake Storage. Nyissa meg a PowerShell-szkriptet egy szerkesztőben a további információk és a megvalósított logika áttekintéséhez.

   Ez a szkript két biztonsági csoportot hoz létre az Azure-előfizetésében: egyet a olvasó csoporthoz, egyet pedig a közreműködő csoporthoz. Microsoft Dataverse service mindkét biztonsági csoport tulajdonosa.

1. Mentse a parancsfájl által létrehozott mindkét biztonságicsoport-azonosító értékét a `ByolSetup.ps1` szkriptben való használatra.

   > [!NOTE]
   > A biztonsági csoport létrehozása letiltható a bérlőn. Ebben az esetben manuális beállításra van szükség, és a rendszergazdának engedélyeznie kell a Azure AD [biztonsági csoport létrehozását](/azure/active-directory/enterprise-users/groups-self-service-management).

1. Hajtsa végre `ByolSetup.ps1` a Windows PowerShellben az Azure-előfizetés azonosítóját, amely tartalmazza a Azure Data Lake Storage tárfiók nevét, az erőforráscsoport nevét, valamint a olvasó és közreműködő biztonsági csoport azonosító értékeit. Nyissa meg a PowerShell-szkriptet egy szerkesztőben a további információk és a megvalósított logika áttekintéséhez.

   Ez a szkript hozzáadja a szükséges szerepköralapú hozzáférés-vezérlést a szolgáltatáshoz és a Microsoft Dataverse Dataverse bármely alapú üzleti alkalmazáshoz. Emellett frissíti a jogkivonaton található `customerinsights` hozzáférés-vezérlési listát (ACL) a `CreateSecurityGroups.ps1` szkripttel létrehozott biztonsági csoportok számára. A közreműködő csoport rwx engedélyt kap *, és az Olvasók csoport csak r-x* engedélyt kap *.*

1. Másolja ki a következő kimeneti sztringet: `https://DVBYODLDemo/customerinsights?rg=285f5727-a2ae-4afd-9549-64343a0gbabc&cg=720d2dae-4ac8-59f8-9e96-2fa675dbdabc`

1. Adja meg a másolt kimeneti sztringet a **környezet konfigurációs lépésének Engedélyek azonosítója** mezőjébe Microsoft Dataverse.

   :::image type="content" source="media/dataverse-enable-datasharing-BYODL.png" alt-text="Konfigurációs beállítások a saját Azure Data Lake Storage Microsoft Dataverse adatmegosztásának engedélyezéséhez a .":::

## <a name="remove-an-existing-connection-to-a-dataverse-environment"></a>Meglévő kapcsolat eltávolítása egy Dataverse környezettel

Környezethez Dataverse való csatlakozáskor a Ez a **CDS-szervezet már csatolva van egy másik Customer Insights-példányhoz**, hibaüzenet azt jelenti, hogy a Dataverse környezet már használatban van egy Customer Insights környezetben. A meglévő kapcsolatot globális rendszergazdaként is eltávolíthatja a Dataverse környezetből. A módosítások feltöltése eltarthat néhány óráig.

1. Menjen a [Power Apps](https://make.powerapps.com) felületre.
1. Válassza ki a környezetet a környezetválasztóból.
1. Lépjen a Megoldások **oldalra**.
1. Távolítsa el vagy törölje az Ügyfélkártya-bővítmény (előzetes verzió) **Dynamics 365 Customer Insights nevű** megoldást.

VAGY

1. Nyissa meg a Dataverse környezetet.
1. Lépjen a **Speciális beállítási** > **megoldások oldalra**.
1. Távolítsa el a **CustomerInsightsCustomerCard** megoldást.

Ha a kapcsolat eltávolítása függőségek miatt meghiúsul, a függőségeket is el kell távolítania. További információ: [Függőségek](/power-platform/alm/removing-dependencies) eltávolítása.

## <a name="output-entities"></a>Kimeneti entitások

A Customer Insights egyes kimeneti entitásai táblákként érhetők el a következő helyen:Dataverse. Az alábbi szakaszok e táblázatok várt sémáját írják le.

- [CustomerProfile](#customerprofile)
- [ContactProfile](#contactprofile)
- [AlternateKey](#alternatekey)
- [UnifiedActivity](#unifiedactivity)
- [CustomerMeasure](#customermeasure)
- [Dúsítás](#enrichment)
- [Előrejelzés](#prediction)
- [Szegmens tagság](#segment-membership)

### <a name="customerprofile"></a>CustomerProfile

Ez a tábla a Customer Insights egységes ügyfélprofilját tartalmazza. Az egyesített ügyfélprofil sémája az adategyesítési folyamatban használt entitásoktól és attribútumoktól függ. Az ügyfélprofilséma általában a [CustomerProfile Common Data Model-definíciója](/common-data-model/schema/core/applicationcommon/foundationcommon/crmcommon/solutions/customerinsights/customerprofile) attribútumainak egy részhalmazát tartalmazza. A B-to-B forgatókönyv esetében az ügyfélprofil egyesített fiókokat tartalmaz, és a séma általában a Fiók [Common Data Model definíciójából származó](/common-data-model/schema/core/applicationcommon/foundationcommon/crmcommon/account) attribútumok egy részhalmazát tartalmazza.

### <a name="contactprofile"></a>ContactProfile

A ContactProfile egyesített információkat tartalmaz egy névjegyről. A kapcsolattartók olyan [személyek, akik B-től B-ig terjedő forgatókönyv esetén vannak leképezve egy fiókra](data-unification-contacts.md).

| Column                       | Type                | Description     |
| ---------------------------- | ------------------- | --------------- |
|  BirthDate            | Dátum/idő       |  A kapcsolattartó születési ideje               |
|  City                 | Szöveges |  A kapcsolattartási cím városa               |
|  Kapcsolatazonosító            | Szöveges |  A kapcsolattartói profil azonosítója               |
|  ContactProfileId     | Egyedi azonosító   |  GUID azonosító a kapcsolattartó számára               |
|  CountryOrRegion      | Szöveges |  A kapcsolattartási cím országa/régiója               |
|  Vevőkód           | Szöveges |  Annak a fióknak az azonosítója, amelyhez a kapcsolattartó hozzá van rendelve               |
|  EntityName           | Szöveges |  Entitás, amelyből az adatok származnak                |
|  FirstName            | Szöveges |  A kapcsolattartó utóneve               |
|  Nem               | Szöveges |  A kapcsolattartó neme               |
|  Id                   | Szöveges |  Determinisztikus GUID a következők alapján: `Identifier`               |
|  Azonosító           | Szöveges |  A kapcsolattartói profil belső azonosítója: `ContactProfile|CustomerId|ContactId`               |
|  Munkakör             | Szöveges |  A kapcsolattartó beosztása               |
|  LastName             | Szöveges |  A kapcsolattartó vezetékneve               |
|  PostalCode           | Szöveges |  A kapcsolattartási cím irányítószáma               |
|  Elsődleges E-mail         | Szöveges |  A kapcsolattartó e-mail-címe               |
|  ElsődlegesPhone         | Szöveges |  A kapcsolattartó telefonszáma               |
|  Állam vagy megye      | Szöveges |  A kapcsolattartási cím szerinti állam vagy tartomány               |
|  StreetAddress        | Szöveges |  A kapcsolattartási cím utcaképe               |

### <a name="alternatekey"></a>AlternateKey

Az AlternateKey-tábla az egyesítési folyamatban részt vett entitások kulcsait tartalmazza.

|Column  |Type  |Description  |
|---------|---------|---------|
|DataSourceName    |Szöveges         | Az adatforrás neve. Például: `datasource5`        |
|EntityName        | Szöveges        | Az entitás neve a Customer Insights szolgáltatásban. Például: `contact1`        |
|AlternateValue    |Szöveges         |Az ügyfélazonosítóhoz leképezett alternatív azonosító. Példa: `cntid_1078`         |
|KeyRing           | Szöveges        | JSON-érték  </br> Minta: [{"dataSourceName":" datasource5 ",</br>"entityName":" contact1",</br>"preferredKey":" cntid_1078",</br>"keys":[" cntid_1078"]}]       |
|Vevőkód         | Szöveges        | Az egységes ügyfélprofil azonosítója.         |
|AlternateKeyId     | Egyedi azonosító        |  AlternateKey determinisztikus GUID azonosító alapján`Identifier`      |
|Azonosító |   Szöveges      |   `DataSourceName|EntityName|AlternateValue`  </br> Minta: `testdatasource|contact1|cntid_1078`    |

### <a name="unifiedactivity"></a>UnifiedActivity

Ez a táblázat a Customer Insights-szolgáltatásban elérhető felhasználók tevékenységeit tartalmazza.

| Column            | Type        | Description                                                                              |
|-------------------|-------------|------------------------------------------------------------------------------------------|
| Vevőkód        | Szöveges      | Ügyfélprofil-azonosító                                                                      |
| ActivityId        | Szöveges      | Az ügyféltevékenység belső azonosítója (elsődleges kulcs)                                       |
| SourceEntityName  | Szöveges      | A forrásentitás neve                                                                |
| SourceActivityId  | Szöveges      | Elsődleges kulcs a forrásentitásból                                                       |
| ActivityType      | Szöveges      | Szemantikai tevékenység típusa vagy az egyéni tevékenység neve                                        |
| ActivityTimeStamp | Dátum/idő    | Tevékenység időbélyegzője                                                                      |
| Title             | Szöveges      | A tevékenység címe vagy neve                                                               |
| Description       | Szöveges      | Tevékenység leírása                                                                     |
| URL-cím               | Szöveges      | Hivatkozás a tevékenységhez specifikus külső URL-címre                                         |
| SemanticData      | Szöveges | Tartalmazza a tevékenységtípusra jellemző szemantikai leképezési mezők legfontosabb értékpárjainak listáját |
| RangeIndex        | Szöveges      | A tevékenység idővonalának és az érvényes tartomány-lekérdezések rendezésére használt Unix időbélyegző |
| UnifiedActivityId   | Egyedi azonosító | Az ügyféltevékenység belső azonosítója (ActivityId) |

### <a name="customermeasure"></a>CustomerMeasure

Ez a tábla az ügyfél attribútumalapú mérőszámait tartalmazza.

| Column             | Type             | Description                 |
|--------------------|------------------|-----------------------------|
| Vevőkód         | Szöveges           | Ügyfélprofil-azonosító        |
| Mértékek           | Szöveges      | Tartalmazza az adott vevő kulcsérték-párjait a mérőszám nevéhez és értékeihez |
| Azonosító | Szöveges           | `Customer_Measure|CustomerId` |
| CustomerMeasureId | Egyedi azonosító     | Ügyfélprofil-azonosító |

### <a name="enrichment"></a>Dúsítás

Ez a tábla a bővítési folyamat kimenetét tartalmazza.

| Column               | Type             |  Description                                          |
|----------------------|------------------|------------------------------------------------------|
| Vevőkód           | Szöveges           | Ügyfélprofil-azonosító                                 |
| EnrichmentProvider   | Szöveges           | A bővítés szolgáltatójának neve                                  |
| EnrichmentType       | Szöveges           | A bővítés típusa                                      |
| Értékek               | Szöveges      | A bővítési folyamat által előállított attribútumok listája |
| EnrichmentId | Egyedi azonosító            | Determinisztikus GUID azonosító, amelyet a`Identifier` |
| Azonosító   | Szöveges           | `EnrichmentProvider|EnrichmentType|CustomerId`         |

### <a name="prediction"></a>Előrejelzés

Ez a tábla a modell-előrejelzések kimenetét tartalmazza.

| Column               | Type        | Description                                          |
|----------------------|-------------|------------------------------------------------------|
| Vevőkód           | Szöveges      | Ügyfélprofil-azonosító                                  |
| ModelProvider        | Szöveges      | A modell szolgáltatójának neve                                      |
| Modell                | Szöveges      | Modell neve                                                |
| Értékek               | Szöveges | A modell által előállított attribútumok listája |
| JóslatId | Egyedi azonosító       | Determinisztikus GUID azonosító, amelyet a`Identifier` |
| Azonosító   | Szöveges      |  `Model|ModelProvider|CustomerId`                      |

### <a name="segment-membership"></a>Szegmens tagság

Ez a táblázat az ügyfélprofilok szegmenstagsági adatait tartalmazza.

| Column        | Type | Description                        |
|--------------------|--------------|-----------------------------|
| Vevőkód        | Szöveges       | Ügyfélprofil-azonosító        |
| SzegmensProvider      | Szöveges       | A szegmenseket közzétevő alkalmazás.      |
| Szegmenstagság Típusa | Szöveges       | Az adott szegmenstagsági rekordhoz tartozó ügyfél típusa. Többféle típust támogat, például ügyfél, kapcsolattartó vagy partner. Alapértelmezett érték: Ügyfél  |
| Szegmensek       | Szöveges  | Azon egyedi szegmensek listája, amelyeknek az ügyfélprofil tagja      |
| Azonosító  | Szöveges   | A szegmenstagsági rekord egyedi azonosítója. `CustomerId|SegmentProvider|SegmentMembershipType|Name`  |
| SegmentMembershipId | Egyedi azonosító      | Determinisztikus GUID azonosító, amelyet a`Identifier`          |

[!INCLUDE [footer-include](includes/footer-banner.md)]
