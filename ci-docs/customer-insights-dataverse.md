---
title: A Customer Insights-adatok használata a Microsoft Dataverse-ben
description: További információ a Customer Insights összekapcsolásáról és Microsoft Dataverse a programba exportált kimeneti entitások megértéséről Dataverse.
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
ms.openlocfilehash: 3848e143bc7cb2f345bc698a274b92148ef00669
ms.sourcegitcommit: f5af5613afd9c3f2f0695e2d62d225f0b504f033
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/01/2022
ms.locfileid: "8833679"
---
# <a name="work-with-customer-insights-data-in-microsoft-dataverse"></a>A Customer Insights-adatok használata a Microsoft Dataverse-ben

A Customer Insights lehetőséget biztosít arra, hogy a kimeneti entitásokat a következőként tegye elérhetővé: [Microsoft Dataverse](/powerapps/maker/data-platform/data-platform-intro). Ez az integráció egyszerű adatmegosztást és egyéni fejlesztést tesz lehetővé alacsony kód/kód nélküli megközelítéssel. A [kimeneti entitások](#output-entities) táblákként érhetők el egy Dataverse környezetben. Az adatokat bármely más, táblákon Dataverse alapuló alkalmazáshoz használhatja. Ezek a táblák olyan forgatókönyveket tesznek lehetővé, mint az automatizált munkafolyamatok a segítségével Power Automate, vagy alkalmazásokat készítenek a segítségével Power Apps.

A környezethez Dataverse való csatlakozás lehetővé [teszi az adatok helyszíni adatforrásokból származó adatok adatáramlások és átjárók használatával történő Power Platform bevitelét](data-sources.md#add-data-from-on-premises-data-sources) is.

## <a name="prerequisites"></a>Előfeltételek

- Az ügyfélelemzéseket és Dataverse a környezeteket ugyanabban a régióban kell üzemeltetni.
- Globális rendszergazdai szerepkörrel kell rendelkeznie a Dataverse környezetben. Ellenőrizze, hogy ez [Dataverse a környezet bizonyos biztonsági csoportokhoz van-e társítva](/power-platform/admin/control-user-access#associate-a-security-group-with-a-dataverse-environment), és győződjön meg arról, hogy hozzá van-e adva ezekhez a biztonsági csoportokhoz.
- Nincs még társítva más Customer Insights-környezet a Dataverse csatlakozni kívánt környezethez. További információ a [környezettel Dataverse való meglévő kapcsolat eltávolításáról](#remove-an-existing-connection-to-a-dataverse-environment).
- A Microsoft Dataverse környezet csak egyetlen tárfiókhoz csatlakozhat. Csak akkor érvényes, ha a környezetet [a rendszer Azure Data Lake Storage](own-data-lake-storage.md) használatára állítja be.

## <a name="connect-a-dataverse-environment-to-customer-insights"></a>Környezet csatlakoztatása Dataverse az Ügyfélelemzéshez

A **Microsoft Dataverse** lépés lehetővé teszi, hogy összekapcsolja az Ügyfélelemzéseket a környezetével, Dataverse miközben [Ügyfélelemzési környezetet](create-environment.md) hoz létre.

:::image type="content" source="media/dataverse-provisioning.png" alt-text="adatmegosztás automatikus engedélyezve van Microsoft Dataverse az új, netes környezetekhez.":::

A rendszergazdák konfigurálhatják a Customer Insights alkalmazást egy meglévő Dataverse környezet összekapcsolására. Azáltal, hogy megadja az URL-címet a Dataverse környezetnek, az új Customer Insights környezethez kapcsolódik.

Ha nem szeretne meglévő Dataverse környezetet használni, a rendszer új környezetet hoz létre a bérlő Ügyfélelemzési adataihoz. [Power Platform a rendszergazdák szabályozhatják, hogy ki hozhat létre környezeteket](/power-platform/admin/control-environment-creation). Ha új Customer Insights-környezetet állít be, és a rendszergazda letiltotta a környezetek létrehozását Dataverse mindenki számára, kivéve a rendszergazdákat, előfordulhat, hogy nem tud új környezetet létrehozni.

**Engedélyezze az adatmegosztást** Dataverse az adatmegosztás jelölőnégyzet bejelölésével.

Ha saját Data Lake Storage-fiókot használ, szüksége van az **Engedélyek azonosítóra** is. Az engedélyazonosító lekéréséről a következő szakaszban olvashat bővebben.

## <a name="enable-data-sharing-with-dataverse-from-your-own-azure-data-lake-storage-preview"></a>Adatmegosztás engedélyezése saját Dataverse maga által Azure Data Lake Storage (Előzetes verzió)

Az adatmegosztás engedélyezéséhez, Microsoft Dataverse amikor a környezet [a saját Azure Data Lake Storage fiókját](own-data-lake-storage.md) használja, további konfigurációra van szükség. A Customer Insights környezetet állító felhasználónak legalább **tárolási blobadatokkal olvasó** engedélyekkel kell rendelkeznie a *fiók* CustomerInsights Azure Data Lake Storage tárolóján.

1. Hozzon létre két biztonsági csoportot az Azure-előfizetésen – egyet **olvasó** biztonsági csoportban és egy **közreműködő** biztonsági csoportban, és állítsa be a Microsoft Dataverse szolgáltatást mindkét biztonsági csoport tulajdonosaként.
2. Kezelje a hozzáférés-szabályozási listát (ACL) a tárfiók CustomerInsights tárolóján ezeken a biztonsági csoportokon keresztül. Adja hozzá a Microsoft Dataverse szolgáltatást és az olyan Dataverse alapú üzleti alkalmazásokat, mint a Dynamics 365 Marketing, hogy a **olvasó** biztonsági csoporthoz írásvédett **engedélyekkel**. Csak *a Customers Insights alkalmazást adja hozzá* a **közreműködő** biztonsági csoporthoz, hogy olvasási és írási **engedélyeket adjon** profilok és elemzések írásához.

### <a name="limitations"></a>Korlátozások

A saját Dataverse fiókkal való használatkor Azure Data Lake Storage két korlátozás van:

- Egy-az-egyhez leképezés van egy szervezet és egy Dataverse Azure Data Lake Storage fiók között. Ha egy Dataverse szervezet csatlakozik egy tárfiókhoz, nem tud csatlakozni egy másik tárfiókhoz. Ez a korlátozás megakadályozza, hogy a Dataverse ne töltsön fel több tárfiókot.
- Az adatmegosztás nem fog működni, ha az Azure Data Lake tárfiók eléréséhez azure-privát kapcsolat beállításra van szükség, mert az tűzfal mögött van. Dataverse jelenleg nem támogatja a privát végpontokkal való kapcsolatot a Private Linken keresztül.

### <a name="set-up-powershell"></a>A PowerShell beállítása

A PowerShell-parancsfájlok végrehajtásához először be kell állítania a PowerShellt.

1. Telepítse a PowerShell for Graph [Azure Active Directory legújabb verzióját](/powershell/azure/active-directory/install-adv2).
   1. A számítógépen nyomja le a Windows gombot a billentyűzeten, és keressen a **Windows PowerShell** kifejezésre, és válassza a **Futtatás rendszergazdaként** lehetőséget.
   1. A megnyíló PowerShell ablakában adja meg az `Install-Module AzureAD` értéket.
2. Három modul importálása.
    1. A PowerShell ablakban írja be `Install-Module -Name Az.Accounts` és kövesse a lépéseket.
    1. Ismételje meg a `Install-Module -Name Az.Resources` és `Install-Module -Name Az.Storage`.

### <a name="configuration-steps"></a>Konfigurációs lépések

1. Töltse le a két PowerShell-szkriptet, amelyeket futtatnia kell mérnökünk [GitHub-adattárából](https://github.com/trin-msft/byol).
    1. `CreateSecurityGroups.ps1`
       - A PowerShell-parancsfájl futtatásához bérlői rendszergazdai *engedélyekre van szükség*.
       - Ez a PowerShell-parancsfájl két biztonsági csoportot hoz létre az Azure-előfizetésen. Az egyik a olvasó csoportnak, a másik pedig a közreműködő csoportnak, és mindkét biztonsági csoport tulajdonosaként szolgáltatást nyújt Microsoft Dataverse.
       - Hajtsa végre ezt a PowerShell-parancsfájlt a Windows PowerShellben a következőket Azure Data Lake Storage tartalmazó Azure-előfizetési azonosító megadásával. Nyissa meg a PowerShell-parancsfájlt egy szerkesztőben a további információk és a megvalósított logika áttekintéséhez.
       - Mentse a parancsfájl által létrehozott mindkét biztonsági csoportazonosító értéket, mert a `ByolSetup.ps1` parancsfájlban fogjuk használni őket.

        > [!NOTE]
        > A biztonsági csoport létrehozása letiltható a bérlőn. Ebben az esetben manuális beállításra lenne szükség, és a rendszergazdának engedélyeznie kell Azure AD a [biztonsági csoport létrehozását](/azure/active-directory/enterprise-users/groups-self-service-management).

    2. `ByolSetup.ps1`
        - A parancsfájl futtatásához tárolófiók/tároló szintű Storage Blob Data Owner *engedélyekre van szükség*, különben ez a parancsfájl létrehoz egyet az Ön számára. A szerepkör-hozzárendelés manuálisan eltávolítható a parancsfájl sikeres futtatása után.
        - Ez a PowerShell-parancsfájl hozzáadja a szolgáltatáshoz és az Microsoft Dataverse összes Dataverse üzleti alkalmazáshoz szükséges tole-alapú hozzáférés-vezérlést (RBAC). Frissíti továbbá a CustomerInsights tároló hozzáférés-szabályozási listáját (ACL) a `CreateSecurityGroups.ps1` parancsfájllal létrehozott biztonsági csoportok számára. A közreműködő csoport rwx engedéllyel, *az Olvasók csoport pedig csak r-x* engedéllyel rendelkezik *.*
        - Hajtsa végre ezt a PowerShell-parancsfájlt a Windows PowerShellben úgy, hogy megadja az Azure-előfizetés azonosítóját, amely tartalmazza a Azure Data Lake Storage, a tárfiók nevét, az erőforráscsoport nevét, valamint a olvasó és közreműködő biztonsági csoportazonosító értékeit. Nyissa meg a PowerShell-parancsfájlt egy szerkesztőben a további információk és a megvalósított logika áttekintéséhez.
        - Másolja a kimeneti karakterláncot a parancsfájl sikeres futtatása után. A kimeneti karakterlánc így néz ki: `https://DVBYODLDemo/customerinsights?rg=285f5727-a2ae-4afd-9549-64343a0gbabc&cg=720d2dae-4ac8-59f8-9e96-2fa675dbdabc`

2. Írja be a felülről másolt kimeneti karakterláncot a **környezetkonfigurációs lépés Engedélyazonosító** mezőjébe Microsoft Dataverse.

:::image type="content" source="media/dataverse-enable-datasharing-BYODL.png" alt-text="Konfigurációs beállítások az adatok sajátból Azure Data Lake Storage történő megosztásának engedélyezéséhez a programmal Microsoft Dataverse.":::

### <a name="remove-an-existing-connection-to-a-dataverse-environment"></a>Meglévő kapcsolat eltávolítása környezettel Dataverse

Környezethez Dataverse való csatlakozáskor a hibaüzenet **: Ez a CDS-szervezet már egy másik Customer Insights-példányhoz** van csatolva, azt jelenti, hogy a Dataverse környezet már használatban van egy Customer Insights környezetben. A meglévő kapcsolatot globális rendszergazdaként eltávolíthatja a Dataverse környezetben. Eltarthat néhány óráig, amíg feltölti a változásokat.

1. Menjen a [Power Apps](https://make.powerapps.com) felületre.
1. Válassza ki a környezetet a környezetválasztóból.
1. Ugrás a **megoldásokra**
1. Távolítsa el vagy törölje az Ügyfélkártya bővítmény (Előnézet) **Dynamics 365 Customer Insights nevű** megoldást.

VAGY

1. Nyissa meg a Dataverse környezetet.
1. Nyissa meg a **Speciális beállítások** > **megoldásait**.
1. Távolítsa el a **CustomerInsightsCustomerCard** megoldást.

Ha függőségek miatt nem sikerül eltávolítani a kapcsolatot, el kell távolítania a függőségeket is. További információt a Függőségek [eltávolítása című témakörben talál](/power-platform/alm/removing-dependencies).

## <a name="output-entities"></a>Kimeneti entitások

A Customer Insights egyes kimeneti entitásai táblaként érhetők el a alkalmazásban Dataverse. Az alábbi szakaszok e táblázatok várt sémáját írják le.

- [CustomerProfile](#customerprofile)
- [AlternateKey](#alternatekey)
- [UnifiedActivity](#unifiedactivity)
- [CustomerMeasure](#customermeasure)
- [Dúsítás](#enrichment)
- [Előrejelzés](#prediction)
- [Szegmenstagság](#segment-membership)

### <a name="customerprofile"></a>CustomerProfile

Ez a tábla a Customer Insights egységes ügyfélprofilját tartalmazza. Az egységes ügyfélprofil sémája az adategyesítési folyamatban használt entitásoktól és attribútumoktól függ. Az ügyfélprofilséma általában a [CustomerProfile Common Data Model-definíciója](/common-data-model/schema/core/applicationcommon/foundationcommon/crmcommon/solutions/customerinsights/customerprofile) attribútumainak egy részhalmazát tartalmazza.

### <a name="alternatekey"></a>AlternateKey

Az AlternateKey-tábla az egyesítési folyamatban részt vett entitások kulcsait tartalmazza.

|Column  |Típus szerint  |Ismertetés  |
|---------|---------|---------|
|DataSourceName    |Sztring         | Az adatforrás neve. Például: `datasource5`        |
|EntityName        | Sztring        | Az entitás neve a Customer Insights alkalmazásban. Például: `contact1`        |
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

### <a name="segment-membership"></a>Szegmenstagság

Ez a tábla a vevőprofilok szegmenstagsági adatait tartalmazza.

| Column        | Type | Description                        |
|--------------------|--------------|-----------------------------|
| Vevőkód        | Sztring       | Ügyfélprofil-azonosító        |
| SegmentProvider      | Sztring       | A szegmenseket közzétevő alkalmazás.      |
| SegmentMembershipType | Sztring       | A szegmenstagsági bejegyzéshez tartozó vevő típusa. Többféle típust támogat, például vevőt, kapcsolattartót vagy partnert. Alapértelmezett: Vevő  |
| Szegmensek       | JSON-sztring  | Azon egyedi szegmensek listája, amelyeknek az ügyfélprofil tagja      |
| msdynci_identifier  | Sztring   | A szegmenstagsági rekord egyedi azonosítója `CustomerId|SegmentProvider|SegmentMembershipType|Name`  |
| msdynci_segmentmembershipid | GUID-azonosító      | A determinisztikus GUID a következőből lett létrehozva: `msdynci_identifier`          |

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
