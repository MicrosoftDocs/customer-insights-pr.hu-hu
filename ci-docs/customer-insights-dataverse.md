---
title: A Customer Insights-adatok használata a Microsoft Dataverse-ben
description: Ismerje meg, hogyan kapcsolhatja össze a Customer Insights szolgáltatást, és Microsoft Dataverse hogyan értheti meg a kimeneti entitásokat, amelyekbe exportálva van Dataverse.
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
ms.openlocfilehash: 9433c411a2c7eb0db137c6392578993d47be82a2
ms.sourcegitcommit: 8559ca47a22d1d7cd9be13531c2eaf0c1083942b
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/12/2022
ms.locfileid: "9671254"
---
# <a name="work-with-customer-insights-data-in-microsoft-dataverse"></a>A Customer Insights-adatok használata a Microsoft Dataverse-ben

A Customer Insights lehetőséget biztosít a kimeneti entitások elérhetővé tételére a [Microsoft Dataverse](/powerapps/maker/data-platform/data-platform-intro)-ben. Ez az integráció egyszerű adatmegosztást és egyéni fejlesztést tesz lehetővé a kevés kódolást igénylő/kódolást nem igénylő megközelítéssel. A [kimeneti entitások](#output-entities) táblaként érhetők el egy Dataverse környezetben. Az adatokat bármely más, táblákon alapuló Dataverse alkalmazáshoz használhatja. Ezek a táblák olyan forgatókönyveket tesznek lehetővé, mint az automatizált munkafolyamatok vagy Power Automate az alkalmazások létrehozása a következővel:Power Apps.

A környezethez Dataverse való csatlakozás azt is lehetővé teszi, hogy [adatfolyamok és átjárók Power Platform használatával](connect-power-query.md#add-data-from-on-premises-data-sources) adatokat töltsön be helyszíni adatforrásokból.

## <a name="prerequisites"></a>Előfeltételek

- A Customer Insights és Dataverse a környezeteket ugyanabban a régióban kell üzemeltetni.
- A környezetben beállított Dataverse globális rendszergazdai szerepkör. Ellenőrizze, hogy ez a környezet társítva [Dataverse van-e bizonyos biztonsági csoportokhoz, és győződjön meg arról, hogy hozzá van adva ezekhez a](/power-platform/admin/control-user-access#associate-a-security-group-with-a-dataverse-environment) biztonsági csoportokhoz.
- Nincs más Customer Insights-környezet, amely már társítva van a Dataverse csatlakoztatni kívánt környezethez. Megtudhatja, hogyan távolíthat [el egy meglévő kapcsolatot egy Dataverse környezettel](#remove-an-existing-connection-to-a-dataverse-environment).
- Egyetlen Microsoft Dataverse tárfiókhoz csatlakoztatott környezet, ha a környezetet a [Azure Data Lake Storage](own-data-lake-storage.md).

## <a name="dataverse-storage-capacity-entitlement"></a>Dataverse Tárolási kapacitásra való jogosultság

A Customer Insights-előfizetés további kapacitásra jogosítja fel a szervezet meglévő [Dataverse tárolókapacitásához](/power-platform/admin/capacity-storage). A hozzáadott kapacitás az előfizetés által használt profilok számától függ.

**Példa:**

Feltéve, hogy 15 GB adatbázis-tárhelyet és 20 GB fájltárhelyet kap 100 000 ügyfélprofilonként. Ha az előfizetése 300 000 ügyfélprofilt tartalmaz, a teljes tárolókapacitás 45 GB (3 x 15 GB) adatbázis-tárterület és 60 GB fájltárhely (3 x 20 GB). Hasonlóképpen, ha 30 ezer fiókkal rendelkező B–B előfizetéssel rendelkezik, a teljes tárolókapacitás 45 GB (3 x 15 GB) adatbázis-tárterület és 60 GB fájltárhely (3 x 20 GB).

A naplókapacitás nem növekményes és rögzített a szervezet számára.

A részletes kapacitásjogosultságokkal kapcsolatos további információkért lásd: [Dynamics 365 licencelési útmutató](https://go.microsoft.com/fwlink/?LinkId=866544).

## <a name="connect-a-dataverse-environment-to-customer-insights"></a>Dataverse Környezet csatlakoztatása a Customer Insights szolgáltatáshoz

A **Microsoft Dataverse** lépés lehetővé teszi a Customer Insights és a Dataverse környezet összekapcsolását egy Customer Insights-környezet [létrehozása közben](create-environment.md).

:::image type="content" source="media/dataverse-provisioning.png" alt-text="Adatmegosztás Microsoft Dataverse automatikusan engedélyezve az új környezetekben.":::

1. Adja meg a környezet URL-címét Dataverse, vagy hagyja üresen, hogy létrehozzon egyet.

   > [!NOTE]
   > Miután létrehozta a kapcsolatot a Customer Insights és Dataverse a között, ne módosítsa a Dataverse környezet szervezetnevét. A rendszer a szervezet nevét használja az Dataverse URL-címben, és a módosított név megszakítja a kapcsolatot a Customer Insights szolgáltatással.

   [Power Platform A rendszergazdák szabályozhatják, hogy ki hozhat létre új Dataverse környezeteket](/power-platform/admin/control-environment-creation). Ha új Customer Insights-környezetet próbál beállítani, de nem tud, előfordulhat, hogy a rendszergazda a rendszergazdák kivételével mindenki számára letiltotta a környezetek létrehozását Dataverse.

1. Ha saját Data Lake Storage-fiókot használ:
   1. Válassza az Adatmegosztás **engedélyezése a következővel lehetőséget**:Dataverse.
   1. Adja meg az **engedélyek azonosítóját**. Az engedélyazonosító [lekéréséhez engedélyezze az adatmegosztást Dataverse a saját Azure Data Lake Storage](#enable-data-sharing-with-dataverse-from-your-own-azure-data-lake-storage-preview).

## <a name="enable-data-sharing-with-dataverse-from-your-own-azure-data-lake-storage-preview"></a>Adatmegosztás Dataverse engedélyezése a sajátból Azure Data Lake Storage (előzetes verzió)

A saját [fiókjában Azure Data Lake Storage](own-data-lake-storage.md) ellenőrizze, hogy a Customer Insights-környezetet beállító felhasználó rendelkezik-e legalább **Storage Blob-adatokkal olvasó** engedélyekkel a tárfiókban lévő tárolóhoz `customerinsights`.

> [!NOTE]
> Az adatmegosztás csak akkor alkalmazható, ha a saját Azure Data Lake Storage fiókját használja. Ez a beállítás nem érhető el, ha a Customer Insights környezet az alapértelmezett Dataverse tárolót használja.

### <a name="limitations"></a>Korlátozások

- Csak egy-az-egyhez leképezés egy Dataverse szervezet és egy Azure Data Lake Storage fiók között. Miután egy szervezet csatlakozik egy tárfiókhoz, nem tud csatlakozni egy Dataverse másik tárfiókhoz. Ez a korlátozás megakadályozza Dataverse több tárfiók feltöltését.
- Az adatmegosztás nem fog működni, ha Azure Private Link beállításra van szükség a Azure Data Lake Storage fiók eléréséhez, mert az tűzfal mögött van. Dataverse jelenleg nem támogatja a privát végpontokkal való kapcsolatot a Private Link.

### <a name="set-up-security-groups-on-your-own-azure-data-lake-storage"></a>Biztonsági csoportok beállítása saját maga Azure Data Lake Storage

1. Hozzon létre két biztonsági csoportot az Azure-előfizetésében – egy olvasó **biztonsági csoportot és egy** **közreműködő** biztonsági csoportot, és állítsa be a Microsoft Dataverse szolgáltatást mindkét biztonsági csoport tulajdonosaként.

1. Kezelje Access Control listát (ACL) a tárfiókban lévő tárolón ezeken a `customerinsights` biztonsági csoportokon keresztül.
   1. Adja hozzá a szolgáltatást és az esetleges Microsoft Dataverse alapú üzleti alkalmazásokat, például a Dynamics 365 Marketinget a Dataverse **olvasó** biztonsági csoporthoz **írásvédett** engedélyekkel.
   1. Csak *a Customers Elemzések alkalmazást adja hozzá* a közreműködő **biztonsági csoporthoz, hogy olvasási és írási engedélyeket is adjon** a **profilok és elemzések írásához**.

### <a name="set-up-powershell"></a>A PowerShell beállítása

Állítsa be a PowerShellt PowerShell-szkriptek végrehajtásához.

1. Telepítse a PowerShell for Graph [Azure Active Directory legújabb verzióját](/powershell/azure/active-directory/install-adv2).
   1. A számítógépen nyomja le a Windows gombot a billentyűzeten, és keressen a **Windows PowerShell** kifejezésre, és válassza a **Futtatás rendszergazdaként** lehetőséget.
   1. A megnyíló PowerShell ablakában adja meg az `Install-Module AzureAD` értéket.

1. Importáljon három modult.
   1. A PowerShell ablakban adja meg `Install-Module -Name Az.Accounts` és kövesse a lépéseket.
   1. Ismételje meg a és `Install-Module -Name Az.Resources` a elemet `Install-Module -Name Az.Storage`.

### <a name="execute-powershell-scripts-and-obtain-the-permission-identifier"></a>PowerShell-szkriptek végrehajtása és az engedélyazonosító beszerzése

1. Töltse le a futtatni szükséges két PowerShell-szkriptet a mérnökünk [GitHub adattárából](https://github.com/trin-msft/byol).
   - `CreateSecurityGroups.ps1`: Bérlői rendszergazdai engedélyeket igényel.
   - `ByolSetup.ps1`: Storage blobadat-tulajdonosi engedélyeket igényel a tárfiók/tároló szintjén. Ez a szkript létrehozza az engedélyt az Ön számára. A szerepkör-hozzárendelés manuálisan is eltávolítható a szkript sikeres futtatása után.

1. Végrehajtás `CreateSecurityGroups.ps1` a Windows PowerShellben a Azure Data Lake Storage. Nyissa meg a PowerShell-szkriptet egy szerkesztőben a további információk és a megvalósított logika áttekintéséhez.

   Ez a szkript két biztonsági csoportot hoz létre az Azure-előfizetésében: egyet a olvasó csoporthoz, egyet pedig a közreműködő csoporthoz. Microsoft Dataverse A szolgáltatás mindkét biztonsági csoport tulajdonosa.

1. Mentse a szkript által létrehozott mindkét biztonságicsoport-azonosítóértéket a `ByolSetup.ps1` szkriptben való használatra.

   > [!NOTE]
   > A biztonsági csoportok létrehozása letiltható a bérlőn. Ebben az esetben manuális beállításra van szükség, és a rendszergazdának Azure AD engedélyeznie kell a [biztonsági csoportok létrehozását](/azure/active-directory/enterprise-users/groups-self-service-management).

1. Hajtsa végre `ByolSetup.ps1` a Windows PowerShellben úgy, hogy megadja az Azure-előfizetés azonosítóját, amely tartalmazza a Azure Data Lake Storage tárfiók nevét, az erőforráscsoport nevét, valamint a olvasó és közreműködő biztonsági csoport azonosítójának értékeit. Nyissa meg a PowerShell-szkriptet egy szerkesztőben a további információk és a megvalósított logika áttekintéséhez.

   Ez a szkript hozzáadja a szükséges szerepköralapú hozzáférés-vezérlést a szolgáltatáshoz és bármely Microsoft Dataverse Dataverse-alapú üzleti alkalmazáshoz. Emellett frissíti a parancsfájllal `customerinsights` létrehozott biztonsági csoportok tárolójának `CreateSecurityGroups.ps1` hozzáférés-vezérlési listáját (ACL) is. A közreműködő csoport rwx engedélyt kap *, az Olvasók csoport* pedig csak r-x *engedélyt.*

1. Másolja ki a következőhöz hasonló kimeneti sztringet: `https://DVBYODLDemo/customerinsights?rg=285f5727-a2ae-4afd-9549-64343a0gbabc&cg=720d2dae-4ac8-59f8-9e96-2fa675dbdabc`

1. Adja meg a másolt kimeneti sztringet a **környezeti konfigurációs lépés Engedélyek azonosítója** mezőjébe.Microsoft Dataverse

   :::image type="content" source="media/dataverse-enable-datasharing-BYODL.png" alt-text="Konfigurációs beállítások az adatmegosztás engedélyezéséhez a saját Azure Data Lake Storage használatával .Microsoft Dataverse":::

## <a name="remove-an-existing-connection-to-a-dataverse-environment"></a>Meglévő kapcsolat eltávolítása egy Dataverse környezethez

Környezethez Dataverse való csatlakozáskor az Ez a **CDS-szervezet már csatolva van egy másik Customer Insights-példányhoz** hibaüzenet azt jelenti, hogy a Dataverse környezet már használatban van egy Customer Insights-környezetben. A meglévő kapcsolatot globális rendszergazdaként távolíthatja el a Dataverse környezetben. A módosítások feltöltése eltarthat néhány óráig.

1. Menjen a [Power Apps](https://make.powerapps.com) felületre.
1. Válassza ki a környezetet a környezetválasztóból.
1. Lépjen a Megoldások **oldalra**.
1. Távolítsa el vagy törölje az Ügyfélkártya-bővítmény (előzetes verzió) **Dynamics 365 Customer Insights nevű** megoldást.

VAGY

1. Nyissa meg a környezetet Dataverse.
1. Lépjen a Speciális beállítások **megoldásai** > **oldalra**.
1. Távolítsa el a **CustomerInsightsCustomerCard** megoldást.

Ha a kapcsolat eltávolítása függőségek miatt meghiúsul, a függőségeket is el kell távolítania. További információ: [Függőségek eltávolítása](/power-platform/alm/removing-dependencies).

## <a name="output-entities"></a>Kimeneti entitások

A Customer Insights egyes kimeneti entitásai táblaként érhetők el a Dataverse. Az alábbi szakaszok e táblázatok várt sémáját írják le.

- [CustomerProfile](#customerprofile)
- [ContactProfile](#contactprofile)
- [AlternateKey](#alternatekey)
- [UnifiedActivity](#unifiedactivity)
- [CustomerMeasure](#customermeasure)
- [Dúsítás](#enrichment)
- [Előrejelzés](#prediction)
- [Szegmens tagság](#segment-membership)

### <a name="customerprofile"></a>CustomerProfile

Ez a tábla a Customer Insights egységes ügyfélprofilját tartalmazza. Az egységes ügyfélprofil sémája az adategyesítési folyamatban használt entitásoktól és attribútumoktól függ. Az ügyfélprofilséma általában a [CustomerProfile Common Data Model-definíciója](/common-data-model/schema/core/applicationcommon/foundationcommon/crmcommon/solutions/customerinsights/customerprofile) attribútumainak egy részhalmazát tartalmazza. A B-to-B forgatókönyv esetében az ügyfélprofil egyesített partnereket tartalmaz, és a séma általában a Partner [Common Data Model definíciójában szereplő](/common-data-model/schema/core/applicationcommon/foundationcommon/crmcommon/account) attribútumok egy részhalmazát tartalmazza.

### <a name="contactprofile"></a>ContactProfile

A ContactProfile egységes információkat tartalmaz egy kapcsolattartóról. A kapcsolattartók olyan [személyek, akik egy B-to-B forgatókönyvben egy partnerhez](data-unification-contacts.md) vannak rendelve.

| Column                       | Type                | Description     |
| ---------------------------- | ------------------- | --------------- |
|  BirthDate            | Dátum/idő       |  A kapcsolattartó születési dátuma               |
|  City                 | Szöveges |  A kapcsolattartási cím városa               |
|  Kapcsolatazonosító            | Szöveges |  A kapcsolatfelvételi profil azonosítója               |
|  KapcsolatprofilId     | Egyedi azonosító   |  A kapcsolattartó GUID azonosítója               |
|  CountryOrRegion      | Szöveges |  A kapcsolattartási cím országa/régiója               |
|  Vevőkód           | Szöveges |  Annak a partnernek az azonosítója, amelyhez a kapcsolattartó hozzá van rendelve               |
|  EntityName           | Szöveges |  Az entitás, amelyből az adatok származnak                |
|  FirstName            | Szöveges |  A kapcsolattartó utóneve               |
|  Nem               | Szöveges |  A kapcsolattartó neme               |
|  Id                   | Szöveges |  Determinisztikus GUID azonosító a következők alapján: `Identifier`               |
|  Azonosító           | Szöveges |  A kapcsolatfelvételi profil belső azonosítója: `ContactProfile|CustomerId|ContactId`               |
|  Munkakör             | Szöveges |  A kapcsolattartó beosztása               |
|  LastName             | Szöveges |  A kapcsolattartó vezetékneve               |
|  PostalCode           | Szöveges |  A kapcsolattartási cím irányítószáma               |
|  Elsődleges e-mail         | Szöveges |  A kapcsolattartó e-mail-címe               |
|  Elsődleges telefon         | Szöveges |  A kapcsolattartó telefonszáma               |
|  Állam vagy megye      | Szöveges |  A kapcsolattartási cím szerinti állam vagy tartomány               |
|  StreetAddress        | Szöveges |  A kapcsolattartási cím utca               |

### <a name="alternatekey"></a>AlternateKey

Az AlternateKey-tábla az egyesítési folyamatban részt vett entitások kulcsait tartalmazza.

|Column  |Type  |Description  |
|---------|---------|---------|
|DataSourceName    |Szöveges         | Az adatforrás neve. Például: `datasource5`        |
|EntityName        | Szöveges        | Az entitás neve a Customer Insights szolgáltatásban. Például: `contact1`        |
|AlternateValue    |Szöveges         |Az ügyfélazonosítóhoz leképezett alternatív azonosító. Példa: `cntid_1078`         |
|KeyRing           | Szöveges        | JSON-érték  </br> Minta: [{"dataSourceName":" datasource5 ",</br>"entityName":" contact1",</br>"preferredKey":" cntid_1078",</br>"keys":[" cntid_1078"]}]       |
|Vevőkód         | Szöveges        | Az egységes ügyfélprofil azonosítója.         |
|AlternateKeyId     | Egyedi azonosító        |  AlternateKey determinisztikus GUID a következőn alapul: `Identifier`      |
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
| ÜgyfélMeasureId | Egyedi azonosító     | Ügyfélprofil-azonosító |

### <a name="enrichment"></a>Dúsítás

Ez a tábla a bővítési folyamat kimenetét tartalmazza.

| Column               | Type             |  Description                                          |
|----------------------|------------------|------------------------------------------------------|
| Vevőkód           | Szöveges           | Ügyfélprofil-azonosító                                 |
| EnrichmentProvider   | Szöveges           | A bővítés szolgáltatójának neve                                  |
| EnrichmentType       | Szöveges           | A bővítés típusa                                      |
| Értékek               | Szöveges      | A bővítési folyamat által előállított attribútumok listája |
| Dúsítási azonosító | Egyedi azonosító            | A következőből generált determinisztikus GUID azonosító: `Identifier` |
| Azonosító   | Szöveges           | `EnrichmentProvider|EnrichmentType|CustomerId`         |

### <a name="prediction"></a>Előrejelzés

Ez a tábla a modell-előrejelzések kimenetét tartalmazza.

| Column               | Type        | Description                                          |
|----------------------|-------------|------------------------------------------------------|
| Vevőkód           | Szöveges      | Ügyfélprofil-azonosító                                  |
| ModelProvider        | Szöveges      | A modell szolgáltatójának neve                                      |
| Modell                | Szöveges      | Modell neve                                                |
| Értékek               | Szöveges | A modell által előállított attribútumok listája |
| Előrejelzési azonosító | Egyedi azonosító       | A következőből generált determinisztikus GUID azonosító: `Identifier` |
| Azonosító   | Szöveges      |  `Model|ModelProvider|CustomerId`                      |

### <a name="segment-membership"></a>Szegmens tagság

Ez a táblázat az ügyfélprofilok szegmenstagsági adatait tartalmazza.

| Column        | Type | Description                        |
|--------------------|--------------|-----------------------------|
| Vevőkód        | Szöveges       | Ügyfélprofil-azonosító        |
| SzegmensSzolgáltató      | Szöveges       | A szegmenseket közzétevő alkalmazás.      |
| SegmentMembershipType típus | Szöveges       | Az ügyfél típusa ehhez a szegmens tagsági feljegyzéshez. Több típust támogat, például ügyfél, kapcsolattartó vagy partner. Alapértelmezett érték: Ügyfél  |
| Szegmensek       | Szöveges  | Azon egyedi szegmensek listája, amelyeknek az ügyfélprofil tagja      |
| Azonosító  | Szöveges   | A szegmenstagsági feljegyzés egyedi azonosítója. `CustomerId|SegmentProvider|SegmentMembershipType|Name`  |
| SegmentMembershipId | Egyedi azonosító      | A következőből generált determinisztikus GUID azonosító: `Identifier`          |

[!INCLUDE [footer-include](includes/footer-banner.md)]
