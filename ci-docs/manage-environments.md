---
title: A környezetek létrehozása és kezelése
description: Megismerheti, hogyan lehet regisztrálni a szolgáltatásra, és hogyan kezelhetők a környezetek.
ms.date: 03/28/2022
ms.subservice: audience-insights
ms.topic: how-to
ms.reviewer: mhart
author: adkuppa
ms.author: adkuppa
manager: shellyha
searchScope:
- ci-system-about
- customerInsights
ms.openlocfilehash: 599cbaf4e19c3a7331e92bfc54c701fefe6c69b3
ms.sourcegitcommit: 6a5f4312a2bb808c40830863f26620daf65b921d
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/11/2022
ms.locfileid: "8741044"
---
# <a name="manage-environments"></a>Környezetek kezelése

## <a name="switch-environments"></a>Váltás a környezetek között

A környezet módosításához válassza ki az oldal jobb felső sarkában található **Környezet** vezérlőt.

:::image type="content" source="media/home-page-environment-switcher.png" alt-text="Képernyőkép a környezetváltáshoz használható vezérlőről.":::

A rendszergazdák [létrehozhatnak](create-environment.md) és kezelhetnek környezeteket.

## <a name="edit-an-existing-environment"></a>Egy meglévő környezet szerkesztése

A meglévő környezetek bizonyos részleteit szerkesztheti.

1.  Válassza ki az alkalmazás fejlécében a **Környezet** választót.

2.  Kattintson a **Szerkesztés** ikonra.

3. A **Környezet szerkesztése** mezőben frissítheti a környezet beállításait.

További információ a környezet beállításaival kapcsolatban: [Új környezet létrehozása](create-environment.md).

## <a name="connect-to-microsoft-dataverse"></a>Csatlakozás a Microsoft Dataverse-hoz
   
A **Microsoft Dataverse** lépéssel összekapcsolhatja a Customer Insightsot a Dataverse környezetével. 

Adjon meg saját Microsoft Dataverse környezetet az adatok (profilok és elemzések) megosztásához olyan üzleti alkalmazásokkal, amelyek a Dynamics 365 Marketing vagy a modellvezérelt alkalmazásokon alapulnak Dataverse Power Apps.

A [használható előrejelzési modellek](predictions-overview.md#out-of-box-models) használatra konfigurálja az adatok megosztását a Dataverse használatával. Vagy engedélyezheti az adatfeldolgozást a helyszíni adatforrásokból, megadva a szervezet által felügyelt Microsoft Dataverse környezet URL-címét.

Ha engedélyezi az adatmegosztást Microsoft Dataverse az adatmegosztás jelölőnégyzet bejelölésével, akkor az adatforrások és az összes többi folyamat egyszeri teljes frissítése következik be.

> [!IMPORTANT]
> 1. Ügyfélelemzések, és Dataverse az adatmegosztás engedélyezéséhez ugyanabban a régióban kell lennie.
> 1. Globális rendszergazdai szerepkörrel kell rendelkeznie a Dataverse környezetben. Ellenőrizze, hogy ez [Dataverse a környezet bizonyos biztonsági csoportokhoz van-e társítva](/power-platform/admin/control-user-access#associate-a-security-group-with-a-dataverse-environment), és győződjön meg arról, hogy hozzá van adva ezekhez a biztonsági csoportokhoz.
> 1. Ehhez a környezethez még nincs társítva Dataverse meglévő Customer Insights-környezet. További információ a [környezettel való meglévő kapcsolat eltávolításáról Dataverse](#remove-an-existing-connection-to-a-dataverse-environment).

:::image type="content" source="media/dataverse-enable-datasharing.png" alt-text="Konfigurálási lehetőségek az adatmegosztás engedélyezéséhez a Microsoft Dataverse szolgáltatással.":::

### <a name="enable-data-sharing-with-dataverse-from-your-own-azure-data-lake-storage-preview"></a>Adatmegosztás engedélyezése saját Dataverse maga által Azure Data Lake Storage (Előzetes verzió)

Ha a környezet úgy van konfigurálva, hogy a sajátját Azure Data Lake Storage használja az Ügyfélelemzési adatok tárolására, az adatmegosztás engedélyezéséhez Microsoft Dataverse további konfigurációra van szükség.

1. Hozzon létre két biztonsági csoportot az Azure-előfizetésen – egyet **olvasó** biztonsági csoportban és egy **közreműködő** biztonsági csoportban, és állítsa be a Microsoft Dataverse szolgáltatást mindkét biztonsági csoport tulajdonosaként.
2. Kezelje a hozzáférés-szabályozási listát (ACL) a tárfiók CustomerInsights tárolóján ezeken a biztonsági csoportokon keresztül. Adja hozzá a Microsoft Dataverse szolgáltatást és az olyan Dataverse alapú üzleti alkalmazásokat, mint a Dynamics 365 Marketing, hogy a **olvasó** biztonsági csoporthoz írásvédett **engedélyekkel**. Csak *a Customers Insights alkalmazást adja hozzá* a **közreműködő** biztonsági csoporthoz, hogy olvasási és írási **engedélyeket adjon** profilok és elemzések írásához.
   
#### <a name="prerequisites"></a>Előfeltételek

A PowerShell-parancsfájlok végrehajtásához a következő három modult kell importálni. 

1. Telepítse a PowerShell for Graph [Azure Active Directory legújabb verzióját](/powershell/azure/active-directory/install-adv2).
   1. A számítógépen nyomja le a Windows gombot a billentyűzeten, és keressen a **Windows PowerShell** kifejezésre, és válassza a **Futtatás rendszergazdaként** lehetőséget.
   1. A megnyíló PowerShell ablakában adja meg az `Install-Module AzureAD` értéket.
2. Három modul importálása.
    1. A PowerShell ablakban írja be `Install-Module -Name Az.Accounts` és kövesse a lépéseket. 
    1. Ismételje meg a `Install-Module -Name Az.Resources` és `Install-Module -Name Az.Storage`.

#### <a name="configuration-steps"></a>Konfigurációs lépések

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
        - Másolja a kimeneti karakterláncot a parancsfájl sikeres futtatása után. A kimeneti karakterlánc így néz ki: `https: //DVBYODLDemo/customerinsights?rg=285f5727-a2ae-4afd-9549-64343a0gbabc&cg=720d2dae-4ac8-59f8-9e96-2fa675dbdabc`
        
2. Írja be a felülről másolt kimeneti karakterláncot a **környezetkonfigurációs lépés Engedélyazonosító** mezőjébe Microsoft Dataverse.

:::image type="content" source="media/dataverse-enable-datasharing-BYODL.png" alt-text="Konfigurációs beállítások az adatok sajátból Azure Data Lake Storage történő megosztásának engedélyezéséhez a programmal Microsoft Dataverse.":::

A Customer Insights nem támogatja a következő adatmegosztási forgatókönyveket:
- Ha engedélyezi az adatmegosztást a Dataverse szolgáltatással, akkor nem fogja tudni [létrehozni az előrejelzett vagy hiányzó értékeket egy entitásban](predictions.md).
- Ha engedélyezi az adatmegosztást a programmal Dataverse, nem fogja tudni megtekinteni a választható PowerBI Embedded-jelentéseket a Customer Insights környezetében.

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

## <a name="copy-the-environment-configuration"></a>Másolja a környezet konfigurációját

Rendszergazdaként dönthet úgy, hogy a konfigurációt egy meglévő környezetből másolja, amikor újat hoz létre. 

:::image type="content" source="media/environment-settings-dialog.png" alt-text="Képernyőkép a beállítási lehetőségekről a környezet beállításaiban.":::

A szervezetében összes elérhető környezet listáját látja, amelyekből adatokat másolhat.

A következő konfigurációbeállítások vannak másolva:

- Betöltött/importált adatforrások
- Adategyesítési konfiguráció
- Szegmensek
- Mértékek
- Kapcsolatok
- Tevékenységek
- Keresési és szűrőindex
- Exportálási célhelyek
- Ütemezett frissítés
- Bővítések
- Modellkezelés
- Szerepkör-hozzárendelések

## <a name="set-up-a-copied-environment"></a>Másolt környezet beállítása

A környezeti konfiguráció másolásakor a program nem *másolja a következő adatokat*:

- Ügyfélprofilok.
- Adatforrás hitelesítő adatai. A hitelesítő adatokat meg kell adnia minden adatforráshoz, és manuálisan kell frissítenie az adatforrásokat.
- A Common Data Model mappából származó adatforrások és a Dataverse használatával kezelt adattó. Ezeket az adatforrásokat manuálisan, ugyanolyan néven kell létrehoznia, mint a forráskörnyezetében.
- Az exportáláshoz és a gazdagodáshoz használt kapcsolati titkok. Újra kell engedélyeznie a kapcsolatokat, majd újra aktiválnia kell a gazdagodásokat és az exportálást. 

Környezet másolásakor egy megerősítő üzenet jelenik meg, amely szerint létrejött az új környezet. Válassza az **Ugrás az adatforrásokhoz** lehetőséget az adatforrások listájának megjelenítéséhez.

Minden adatforrásnál megjelenik egy **Hitelesítő adatok szükségesek** állapot. Szerkessze az adatforrásokat, és adja meg a hitelesítő adatokat a frissítésükhöz.

:::image type="content" source="media/data-sources-copied.png" alt-text="A másolt és hitelesítést igényel adatforrások listája.":::

Az adatforrások frissítését követően nyissa meg az **Adatok** > **Egyesítés** pontot. Itt megtalálja a beállításokat a forráskörnyezetből. Igény szerint szerkessze őket, vagy válassza a **Futtatás** lehetőséget az adategyesítési folyamat elindításához, és hozzon létre egy egyesített ügyfélentitást.

Amikor az adatok egyesítése befejeződött, nyissa meg a **Mértékek** és a **Szegmensek** lehetőséget, hogy azokat is frissítse.

Az exportálások és a gazdagítások újraaktiválása előtt nyissa meg a **Felügyeleti** > **kapcsolatok lehetőséget** az új környezetben lévő kapcsolatok újbóli hitelesítéséhez.

## <a name="change-the-owner-of-an-environment"></a>Környezet tulajdonosának megváltoztatása

Bár a Customer Insights szolgáltatásban több felhasználó is rendelkezhet rendszergazdai engedélyekkel, a környezetnek csak egy felhasználó a tulajdonosa. Alapértelmezés szerint kezdetben a rendszergazda hoz létre egy környezetet. A környezet rendszergazdájaként a tulajdonjogot rendszergazdai engedélyekkel rendelkező másik felhasználóhoz is hozzárendelheti.

1. Válassza ki az alkalmazás fejlécében a **Környezet** választót.

1. Kattintson a **Szerkesztés** ikonra.

1. **A Környezet** szerkesztése mezőben nyissa meg az **Alapvető információk** lépést.

1. **A Környezet** tulajdonosának módosítása mezőben válassza ki a környezet új tulajdonosát.  

1. A módosítások alkalmazásához válassza a Véleményezés és befejezés **, majd** a Frissítés **lehetőséget**. 

## <a name="claim-ownership-of-an-environment"></a>Környezet tulajdonjogának követelése

Ha egy környezet tulajdonosa elhagyja a szervezetet, vagy a felhasználói fiókját törlik, a környezetnek nem lesz tulajdonosa. A rendszergazdai engedélyekkel rendelkező felhasználó igényelheti a tulajdonjogot, és új tulajdonossá válhat. Továbbra is birtokolhatják a környezetet, vagy [megváltoztathatják a tulajdonjogot egy másik rendszergazdára](#change-the-owner-of-an-environment). 

A tulajdonjog megszerzéséhez válassza a **Tulajdonjog** átvétele gombot, amely az Ügyfélelemzések minden oldalának tetején jelenik meg, amikor az eredeti tulajdonos elhagyta a szervezetet.

## <a name="reset-an-existing-environment"></a>Meglévő környezet visszaállítása

A környezet tulajdonosaként visszaállíthat egy környezetet üres állapotba, ha törölni szeretné az összes konfigurációt, és el szeretné távolítani a betöltött adatokat.

1.  Válassza ki az alkalmazás fejlécében a **Környezet** választót. 

2.  Válassza ki az alaphelyzetbe állítani kívánt környezetet, és válassza ki a három pontot (**...**). 

3. Válassza az **Alaphelyzetbe állítás** lehetőséget. 

4.  A törlés jóváhagyásához írja be a környezet nevét, és válassza az **Alaphelyzetbe állítás** lehetőséget.

## <a name="delete-an-existing-environment"></a>Meglévő környezet törlése

A környezet tulajdonosaként törölheti az Ön által felügyelt környezetet.

1.  Válassza ki az alkalmazás fejlécében a **Környezet** választót.

2.  Válassza ki az alaphelyzetbe állítani kívánt környezetet, és válassza ki a három pontot (**...**). 

3. Válassza a **Törlés** lehetőséget. 

4.  A törlés jóváhagyásához adja meg a környezet nevét, és válassza a **Törlés** lehetőséget.

> [!NOTE]
> A környezet törlése nem távolítja el a társítást a Dataverse környezethez. További információ a [környezettel Dataverse való meglévő kapcsolat eltávolításáról](#remove-an-existing-connection-to-a-dataverse-environment).


[!INCLUDE [footer-include](includes/footer-banner.md)]
