---
title: A Customer Insights-adatok használata a Microsoft Dataverse-ben
description: Ismerje meg, hogyan csatlakoztathatja a Customer Insights szolgáltatást, és Microsoft Dataverse hogyan értelmezheti a kimeneti entitásokat, amelyek a következőre vannak exportálva:Dataverse.
ms.date: 05/30/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: conceptual
author: mukeshpo
ms.author: mukeshpo
manager: shellyha
searchScope:
- ci-system-diagnostic
- customerInsights
ms.openlocfilehash: 252723b8c174cb1ec488388c26fd2a1d398e9002
ms.sourcegitcommit: 5e26cbb6d2258074471505af2da515818327cf2c
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/14/2022
ms.locfileid: "9011523"
---
# <a name="work-with-customer-insights-data-in-microsoft-dataverse"></a>A Customer Insights-adatok használata a Microsoft Dataverse-ben

A Customer Insights lehetőséget biztosít arra, hogy a kimeneti entitásokat [Microsoft Dataverse](/powerapps/maker/data-platform/data-platform-intro). Ez az integráció egyszerű adatmegosztást és egyéni fejlesztést tesz lehetővé a kevés kódolást igénylő/kód nélküli megközelítéssel. A [kimeneti entitások](#output-entities) táblákként érhetők el egy Dataverse környezetben. Az adatokat táblák alapján Dataverse bármely más alkalmazáshoz használhatja. Ezek a táblák olyan forgatókönyveket tesznek lehetővé, mint az automatizált munkafolyamatok vagy Power Automate az alkalmazások létrehozása Power Apps.

A környezethez való Dataverse csatlakozás azt is lehetővé teszi, hogy [adatfolyamok és átjárók használatával Power Platform adatokat töltsön be helyszíni adatforrásokból](connect-power-query.md#add-data-from-on-premises-data-sources).

## <a name="prerequisites"></a>Előfeltételek

- A Customer Insights-nak és Dataverse a környezeteknek ugyanabban a régióban kell üzemeltetniük.
- Globális rendszergazdai szerepkörrel kell rendelkeznie a Dataverse környezetben. Ellenőrizze, hogy ez a környezet hozzá van-e [Dataverse társítva](/power-platform/admin/control-user-access#associate-a-security-group-with-a-dataverse-environment) bizonyos biztonsági csoportokhoz, és győződjön meg arról, hogy hozzá van adva ezekhez a biztonsági csoportokhoz.
- Egyetlen más Customer Insights-környezet sincs már társítva a Dataverse csatlakoztatni kívánt környezethez. Ismerje meg, [hogyan távolíthat el egy meglévő kapcsolatot egy Dataverse környezettel](#remove-an-existing-connection-to-a-dataverse-environment).
- A Microsoft Dataverse környezetek csak egyetlen tárfiókhoz csatlakozhatnak. Csak akkor érvényes, ha a környezetet [a .Azure Data Lake Storage](own-data-lake-storage.md)

## <a name="connect-a-dataverse-environment-to-customer-insights"></a>Dataverse Környezet csatlakoztatása a Customer Insights szolgáltatáshoz

A **Microsoft Dataverse** lépés lehetővé teszi, hogy összekapcsolja a Customer Insights-t a Dataverse környezetével, miközben [létrehoz egy Customer Insights-környezetet](create-environment.md).

:::image type="content" source="media/dataverse-provisioning.png" alt-text="adatmegosztás automatikus automatikus engedélyezésével Microsoft Dataverse a net új környezetekben.":::

A rendszergazdák konfigurálhatják a Customer Insights szolgáltatást egy meglévő Dataverse környezet csatlakoztatására. Azáltal, hogy megadja az URL-címet a Dataverse környezetnek, az az új Customer Insights-környezethez lesz csatolva.

Ha nem szeretne meglévő Dataverse környezetet használni, a rendszer új környezetet hoz létre a bérlő Customer Insights-adataihoz. [Power Platform a rendszergazdák szabályozhatják, hogy ki hozhat létre környezeteket](/power-platform/admin/control-environment-creation). Ha új Customer Insights-környezetet állít be, és a rendszergazda letiltotta a környezetek létrehozását Dataverse a rendszergazdák kivételével mindenki számára, előfordulhat, hogy nem tud új környezetet létrehozni.

**Engedélyezze az adatmegosztást** Dataverse az adatmegosztás jelölőnégyzet bejelölésével.

Ha saját Data Lake Storage-fiókját használja, szüksége lesz az **engedélyek azonosítójára** is. Az engedélyazonosító beszerzésével kapcsolatos további információkért tekintse át a következő szakaszt.

## <a name="enable-data-sharing-with-dataverse-from-your-own-azure-data-lake-storage-preview"></a>A sajáttól Dataverse származó adatmegosztás Azure Data Lake Storage engedélyezése (előzetes verzió)

Az adatmegosztás engedélyezéséhez Microsoft Dataverse, amikor a környezet [a saját Azure Data Lake Storage fiókját](own-data-lake-storage.md) használja, további konfigurációra van szükség. A Customer Insights környezetet beállító felhasználónak legalább **Storage Blob Data olvasó** engedélyekkel kell rendelkeznie a *fiók* CustomerInsights Azure Data Lake Storage tárolójában.

1. Hozzon létre két biztonsági csoportot az Azure-előfizetésében – egyet **olvasó** biztonsági csoportot és egy **közreműködő** biztonsági csoportot, és állítsa be a Microsoft Dataverse szolgáltatást mindkét biztonsági csoport tulajdonosaként.
2. A tárfiókban található CustomerInsights tárolón található Hozzáférés-vezérlési lista (ACL) kezelése ezeken a biztonsági csoportokon keresztül. Adja hozzá a Microsoft Dataverse szolgáltatást és minden olyan Dataverse alapú üzleti alkalmazást, mint a Dynamics 365 Marketing, a **olvasó** biztonsági csoporthoz, csak **olvasási engedélyekkel**. Csak *a Customers Insights alkalmazást adja hozzá* a **közreműködő** biztonsági csoporthoz, hogy olvasási és írási **engedélyeket is** adjon a profilok és elemzések írásához.

### <a name="limitations"></a>Korlátozások

A saját Dataverse fiókjával való használatnak Azure Data Lake Storage két korlátozása van:

- Van egy-az-egyhez leképezés a Dataverse szervezet és a Azure Data Lake Storage fiók között. Miután egy Dataverse szervezet csatlakozott egy tárfiókhoz, nem tud csatlakozni egy másik tárfiókhoz. Ez a korlátozás megakadályozza, hogy a Dataverse ne töltsön fel több tárfiókot.
- Az adatmegosztás nem fog működni, ha Azure Private Link beállításra van szükség a fiók eléréséhez Azure Data Lake Storage, mert az tűzfal mögött van. Dataverse jelenleg nem támogatja a privát végpontokhoz való csatlakozást a Private Link.

### <a name="set-up-powershell"></a>A PowerShell beállítása

A PowerShell-szkriptek végrehajtásához először ennek megfelelően kell beállítania a PowerShellt.

1. Telepítse a PowerShell legújabb verzióját [Azure Active Directory a Graph](/powershell/azure/active-directory/install-adv2).
   1. A számítógépen nyomja le a Windows gombot a billentyűzeten, és keressen a **Windows PowerShell** kifejezésre, és válassza a **Futtatás rendszergazdaként** lehetőséget.
   1. A megnyíló PowerShell ablakában adja meg az `Install-Module AzureAD` értéket.
2. Három modul importálása.
    1. A PowerShell ablakban adja meg `Install-Module -Name Az.Accounts` és kövesse a lépéseket.
    1. Ismételje meg a és `Install-Module -Name Az.Resources``Install-Module -Name Az.Storage`.

### <a name="configuration-steps"></a>Konfigurációs lépések

1. Töltse le a futtatásához szükséges két PowerShell-szkriptet a mérnökünk [GitHub-adattárából](https://github.com/trin-msft/byol).
    1. `CreateSecurityGroups.ps1`
       - A PowerShell-szkript futtatásához bérlői rendszergazdai *engedélyekre van szükség*.
       - Ez a PowerShell-szkript két biztonsági csoportot hoz létre az Azure-előfizetésében. Az egyik a olvasó csoportnak, a másik pedig a közreműködő csoportnak, és mindkét biztonsági csoport tulajdonosaként fog Microsoft Dataverse szolgálni.
       - Hajtsa végre ezt a PowerShell-szkriptet a Windows PowerShellben a .Azure Data Lake Storage Nyissa meg a PowerShell-szkriptet egy szerkesztőben a további információk és az implementált logika áttekintéséhez.
       - Mentse a szkript által generált mindkét biztonságicsoport-azonosító értékét, mert a `ByolSetup.ps1` szkriptben fogjuk használni őket.

        > [!NOTE]
        > A biztonsági csoport létrehozása letiltható a bérlőn. Ebben az esetben manuális beállításra van szükség, és a rendszergazdának engedélyeznie kell a Azure AD [biztonsági csoport létrehozását](/azure/active-directory/enterprise-users/groups-self-service-management).

    2. `ByolSetup.ps1`
        - A szkript futtatásához Storage Blob Data Owner *engedélyekre van szüksége* a tárfiók/tároló szintjén, különben ez a szkript létrehoz egyet az Ön számára. A szerepkör-hozzárendelés manuálisan is eltávolítható a szkript sikeres futtatása után.
        - Ez a PowerShell-szkript hozzáadja a szükséges tole-alapú hozzáférés-vezérlést (RBAC) a szolgáltatáshoz és bármely Microsoft Dataverse Dataverse-alapú üzleti alkalmazáshoz. Emellett frissíti a CustomerInsights tárolón található hozzáférés-vezérlési listát (ACL) a `CreateSecurityGroups.ps1` szkripttel létrehozott biztonsági csoportok számára. A közreműködő csoport rwx *engedéllyel rendelkezik*, az Olvasók csoport *pedig csak r-x* engedéllyel rendelkezik.
        - Hajtsa végre ezt a PowerShell-szkriptet a Windows PowerShellben úgy, hogy megadja az Azure-előfizetés azonosítóját, amely tartalmazza a Azure Data Lake Storage tárfiók nevét, az erőforráscsoport nevét, valamint a olvasó és közreműködő biztonságicsoport-azonosító értékeit. Nyissa meg a PowerShell-szkriptet egy szerkesztőben a további információk és az implementált logika áttekintéséhez.
        - Másolja ki a kimeneti sztringet a szkript sikeres futtatása után. A kimeneti sztring így néz ki: `https://DVBYODLDemo/customerinsights?rg=285f5727-a2ae-4afd-9549-64343a0gbabc&cg=720d2dae-4ac8-59f8-9e96-2fa675dbdabc`

2. Adja meg a fentről másolt kimeneti sztringet a **környezetkonfigurációs lépés Engedélyazonosító** mezőjébe Microsoft Dataverse.

:::image type="content" source="media/dataverse-enable-datasharing-BYODL.png" alt-text="Konfigurációs beállítások a saját Azure Data Lake Storage Microsoft Dataverse adatmegosztásának engedélyezéséhez a .":::

### <a name="remove-an-existing-connection-to-a-dataverse-environment"></a>Meglévő kapcsolat eltávolítása egy Dataverse környezettel

Környezethez Dataverse való csatlakozáskor a Ez a **CDS-szervezet már csatolva van egy másik Customer Insights-példányhoz**, hibaüzenet azt jelenti, hogy a Dataverse környezet már használatban van egy Customer Insights környezetben. A meglévő kapcsolatot globális rendszergazdaként is eltávolíthatja a Dataverse környezetből. A módosítások feltöltése eltarthat néhány óráig.

1. Menjen a [Power Apps](https://make.powerapps.com) felületre.
1. Válassza ki a környezetet a környezetválasztóból.
1. Tovább a **Megoldásokhoz**
1. Távolítsa el vagy törölje az Ügyfélkártya-bővítmény (előzetes verzió) **Dynamics 365 Customer Insights nevű** megoldást.

VAGY

1. Nyissa meg a Dataverse környezetet.
1. Lépjen a **Speciális beállítási** > **megoldások oldalra**.
1. Távolítsa el a **CustomerInsightsCustomerCard** megoldást.

Ha a kapcsolat eltávolítása függőségek miatt meghiúsul, a függőségeket is el kell távolítania. További információ: [Függőségek](/power-platform/alm/removing-dependencies) eltávolítása.

## <a name="output-entities"></a>Kimeneti entitások

A Customer Insights egyes kimeneti entitásai táblákként érhetők el a következő helyen:Dataverse. Az alábbi szakaszok e táblázatok várt sémáját írják le.

- [CustomerProfile](#customerprofile)
- [AlternateKey](#alternatekey)
- [UnifiedActivity](#unifiedactivity)
- [CustomerMeasure](#customermeasure)
- [Dúsítás](#enrichment)
- [Előrejelzés](#prediction)
- [Szegmens tagság](#segment-membership)

### <a name="customerprofile"></a>CustomerProfile

Ez a tábla a Customer Insights egységes ügyfélprofilját tartalmazza. Az egyesített ügyfélprofil sémája az adategyesítési folyamatban használt entitásoktól és attribútumoktól függ. Az ügyfélprofilséma általában a [CustomerProfile Common Data Model-definíciója](/common-data-model/schema/core/applicationcommon/foundationcommon/crmcommon/solutions/customerinsights/customerprofile) attribútumainak egy részhalmazát tartalmazza.

### <a name="alternatekey"></a>AlternateKey

Az AlternateKey-tábla az egyesítési folyamatban részt vett entitások kulcsait tartalmazza.

|Column  |Típus szerint  |Ismertetés  |
|---------|---------|---------|
|DataSourceName    |Sztring         | Az adatforrás neve. Például: `datasource5`        |
|EntityName        | Sztring        | Az entitás neve a Customer Insights szolgáltatásban. Például: `contact1`        |
|AlternateValue    |Sztring         |Az ügyfélazonosítóhoz leképezett alternatív azonosító. Példa: `cntid_1078`         |
|KeyRing           | Többsoros szöveg        | JSON-érték  </br> Minta: [{"dataSourceName":" datasource5 ",</br>"entityName":" contact1",</br>"preferredKey":" cntid_1078",</br>"keys":[" cntid_1078"]}]       |
|Vevőkód         | Sztring        | Az egységes ügyfélprofil azonosítója.         |
|AlternateKeyId     | GUID         |  AlternateKey determinisztikus GUID az msdynci_identifier alapján       |
|msdynci_identifier |   Sztring      |   `DataSourceName|EntityName|AlternateValue`  </br> Minta: `testdatasource|contact1|cntid_1078`    |

### <a name="unifiedactivity"></a>UnifiedActivity

Ez a táblázat a Customer Insights-szolgáltatásban elérhető felhasználók tevékenységeit tartalmazza.

| Column            | Típus szerint        | Ismertetés                                                                              |
|-------------------|-------------|------------------------------------------------------------------------------------------|
| Vevőkód        | Sztring      | Ügyfélprofil-azonosító                                                                      |
| ActivityId        | Sztring      | Az ügyféltevékenység belső azonosítója (elsődleges kulcs)                                       |
| SourceEntityName  | Sztring      | A forrásentitás neve                                                                |
| SourceActivityId  | Sztring      | Elsődleges kulcs a forrásentitásból                                                       |
| ActivityType      | Sztring      | Szemantikai tevékenység típusa vagy az egyéni tevékenység neve                                        |
| ActivityTimeStamp | DATETIME    | Tevékenység időbélyege                                                                      |
| Beosztás             | Sztring      | A tevékenység címe vagy neve                                                               |
| Ismertetés       | Sztring      | Tevékenység leírása                                                                     |
| URL-cím               | Sztring      | Hivatkozás a tevékenységhez specifikus külső URL-címre                                         |
| SemanticData      | JSON-sztring | Tartalmazza a tevékenységtípusra jellemző szemantikai leképezési mezők legfontosabb értékpárjainak listáját |
| RangeIndex        | Sztring      | A tevékenység idővonalának és az érvényes tartomány-lekérdezések rendezésére használt Unix időbélyegző |
| mydynci_unifiedactivityid   | GUID | Az ügyféltevékenység belső azonosítója (ActivityId) |

### <a name="customermeasure"></a>CustomerMeasure

Ez a tábla az ügyfél attribútumalapú mérőszámait tartalmazza.

| Column             | Típus szerint             | Ismertetés                 |
|--------------------|------------------|-----------------------------|
| Vevőkód         | Sztring           | Ügyfélprofil-azonosító        |
| Mérőszámok           | JSON-sztring      | Tartalmazza az adott vevő kulcsérték-párjait a mérőszám nevéhez és értékeihez | 
| msdynci_identifier | Sztring           | `Customer_Measure|CustomerId` |
| msdynci_customermeasureid | GUID      | Ügyfélprofil-azonosító |


### <a name="enrichment"></a>Dúsítás

Ez a tábla a bővítési folyamat kimenetét tartalmazza.

| Column               | Típus szerint             |  Ismertetés                                          |
|----------------------|------------------|------------------------------------------------------|
| Vevőkód           | Sztring           | Ügyfélprofil-azonosító                                 |
| EnrichmentProvider   | Sztring           | A bővítés szolgáltatójának neve                                  |
| EnrichmentType       | Sztring           | A bővítés típusa                                      |
| Értékek               | JSON-sztring      | A bővítési folyamat által előállított attribútumok listája |
| msdynci_enrichmentid | GUID             | A msdynci_identifier elemhez generált determinisztikus GUID |
| msdynci_identifier   | Sztring           | `EnrichmentProvider|EnrichmentType|CustomerId`         |

### <a name="prediction"></a>Előrejelzés

Ez a tábla a modell-előrejelzések kimenetét tartalmazza.

| Column               | Típus szerint        | Ismertetés                                          |
|----------------------|-------------|------------------------------------------------------|
| Vevőkód           | Sztring      | Ügyfélprofil-azonosító                                  |
| ModelProvider        | Sztring      | A modell szolgáltatójának neve                                      |
| Modell                | Sztring      | Modell neve                                                |
| Értékek               | JSON-sztring | A modell által előállított attribútumok listája |
| msdynci_predictionid | GUID        | A msdynci_identifier elemhez generált determinisztikus GUID | 
| msdynci_identifier   | Sztring      |  `Model|ModelProvider|CustomerId`                      |

### <a name="segment-membership"></a>Szegmens tagság

Ez a táblázat az ügyfélprofilok szegmenstagsági adatait tartalmazza.

| Column        | Type | Description                        |
|--------------------|--------------|-----------------------------|
| Vevőkód        | Sztring       | Ügyfélprofil-azonosító        |
| SzegmensProvider      | Sztring       | A szegmenseket közzétevő alkalmazás.      |
| Szegmenstagság Típusa | Sztring       | Az ügyfél típusa ez a szegmens tagsági rekord. Többféle típust támogat, például ügyfél, kapcsolattartó vagy partner. Alapértelmezett érték: Ügyfél  |
| Szegmensek       | JSON-sztring  | Azon egyedi szegmensek listája, amelyeknek az ügyfélprofil tagja      |
| msdynci_identifier  | Sztring   | A szegmenstagsági rekord egyedi azonosítója. `CustomerId|SegmentProvider|SegmentMembershipType|Name`  |
| msdynci_segmentmembershipid | GUID-azonosító      | Determinisztikus GUID azonosító, amelyet a`msdynci_identifier`          |

<!--
## FAQ: Update existing environments to use Microsoft Dataverse

Between mid-May 2022 and June 13, 2022, administrators can update the environment settings with a Dataverse environment that Customer Insights can use. On June 13, 2022, your environment will be updated automatically and we'll create a Dataverse environment on your tenant for you.

1. My environment uses my own Azure Data Lake Storage account. Do I still need to update?

   If there's already a Dataverse environment configured in your environment, the update isn't required. If no Dataverse is environment configured, the **Update now** button will create a Dataverse environment and update from the Customer Insights database to a Dataverse database.

1. Will we get extra Dataverse capacity, or will the update use my existing Dataverse capacity?

   - If there's already a Dataverse environment configured in your Customer Insights environment, or connected with other Dynamics 365 or Power Apps applications, the capacity remains unchanged.
   - If the Dataverse environment is new, it will add new storage and database capacity. The capacity added varies per environment and entitlements. You'll get 3 GB for trial and sandbox environment. Production environments get 15 GB.

1. I proceeded with the update and it seems like nothing happened. Is the update complete?

   If the notification in Customer Insights doesn't show anymore, the update is complete. You can check the status of the update by reviewing your environment settings.

1. Why do I still see the banner after completing the update steps?

   It can happen due to an upgrade or refresh failure. Contact support.

1. I received a "Failed to provision Dataverse environment" error after starting the update. What happened?

   It can happen due to an upgrade or refresh failure. Contact support.
   Common causes:
    - Insufficient capacity. There's no more capacity to create more environments. For more information, see [Manage capacity action](/power-platform/admin/capacity-storage#actions-to-take-for-a-storage-capacity-deficit).
    - Region mismatch between tenant region and Customer Insights environment region in the Australia and India regions.
    - Insufficient privileges to provision Dataverse. The users starting the update needs a Dynamics 365 admin role.
    - -->
