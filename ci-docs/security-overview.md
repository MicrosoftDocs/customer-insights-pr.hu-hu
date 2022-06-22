---
title: Biztonsági beállítások a Customer Insights szolgáltatásban
description: További információ a biztonsági beállításokról a Dynamics 365 Customer Insights.
ms.date: 06/08/2022
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
ms.reviewer: mhart
manager: shellyha
ms.openlocfilehash: 163deb9bed4f82d742c46cace27dd128f0aca18b
ms.sourcegitcommit: 8e9f0a9693fd8d91ad0227735ff03688fef5406f
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/10/2022
ms.locfileid: "8947418"
---
# <a name="security-settings-in-customer-insights"></a>Biztonsági beállítások a Customer Insights szolgáltatásban

A **Biztonság** lap felsorolja a felhasználói engedélyek és szolgáltatások konfigurálásának lehetőségeit, amelyek segítenek a biztonságosabbá tételben Dynamics 365 Customer Insights. Csak a rendszergazdák férhetnek hozzá ehhez az oldalhoz.

A Beállítások konfigurálásához lépjen a **Rendszergazdai** > **biztonság** elemre.

A **Biztonság** lap a következő lapokat tartalmazza:

- [Felhasználók](#users-tab)
- [API-k](#apis-tab)
- [Privát hivatkozások](#private-links-tab)
- [ Key Vault](#key-vault-tab)
- [Biztonságosan hozzáférhet az ügyféladatokhoz az ügyfélkostátusz-kulcs segítségével (előzetes verzió)](#securely-access-customer-data-with-customer-lockbox-preview)

## <a name="users-tab"></a>Felhasználók lap

A Customer Insightshoz való hozzáférés a szervezet azon felhasználóira korlátozódik, akiket egy rendszergazda adott hozzá az alkalmazáshoz. A **Felhasználók** lapon kezelheti a felhasználói hozzáférést és az engedélyeiket. További információ: [Felhasználói engedélyek](permissions.md).

## <a name="apis-tab"></a>API-k lap

Tekintse meg és kezelje a kulcsokat, hogy a [Customer Insights API-kat](apis.md) a környezet adataival használhassa.

Új elsődleges és másodlagos kulcsokat az Elsődleges **újragenerálása vagy** a Másodlagos **újragenerálása lehetőség kiválasztásával** hozhat létre. 

A környezethez való API-hozzáférés blokkolásához válassza a Letiltás **lehetőséget**. Ha az API-k le vannak tiltva, az Engedélyezés **lehetőséget választva** újra hozzáférést adhat.

## <a name="private-links-tab"></a>Privát hivatkozások lap

[Azure Private Link](/azure/private-link/private-link-overview) lehetővé teszi, hogy a Customer Insights a virtuális hálózat privát végpont keresztül csatlakozzon a fiókjához Azure Data Lake Storage. A tárfiókban lévő adatok esetében, amelyek nincsenek kitéve a nyilvános internetnek, Private Link engedélyezi a kapcsolatot az adott korlátozott hálózattal.

> [!IMPORTANT]
> Minimális szerepkör-követelmény a Private Link beállításához:
>
> - Customer Insights: Rendszergazda
> - Beépített Azure-szerepkör: [Storage-fiók közreműködő](/azure/role-based-access-control/built-in-roles#storage-account-contributor)
> - Engedélyek egyéni Azure-szerepkörhöz: [Microsoft.Storage/storageAccounts/read és Microsoft.Storage/storageAccounts/PrivateEndpointConnectionsApproval/action](/azure/role-based-access-control/resource-provider-operations#microsoftstorage)
>

A Private Link beállítása a Customer Insights szolgáltatásban kétlépéses folyamat. Először kezdeményezi egy privát kapcsolat létrehozását a Customer Insights rendszergazdai **biztonsági** > **privát hivatkozásaiból** > **·**. A **Private Link** hozzáadása panel felsorolja a bérlőtől származó olyan tárfiókokat, amelyek megtekintéséhez engedélyekkel rendelkezik. Válassza ki a tárfiókot, és adja meg a jóváhagyást a Private Link létrehozásához.

Ezután jóvá kell hagynia a Private Link a Data Lake Storage fiók oldalán. Nyissa meg a képernyőn megjelenő hivatkozást az új Private Link jóváhagyásához.

## <a name="key-vault-tab"></a>Key Vault lap

A **Key Vault** lapon összekapcsolhatja és kezelheti saját [Azure Key Vaultját](/azure/key-vault/general/basic-concepts) a környezettel.
A dedikált kulcstartó a szervezet megfelelési határán belül a fázisok és a titkok használatára használható. A Customer Insights a titkos kulcsok azure key vault használatával állíthat be [kapcsolatokat](connections.md) külső rendszerekhez.

További információkért lásd: [Hozza magával saját Azure-kulcstartóját](use-azure-key-vault.md).

## <a name="securely-access-customer-data-with-customer-lockbox-preview"></a>Biztonságosan hozzáférhet az ügyféladatokhoz az ügyfélkostátusz-kulcs segítségével (előzetes verzió)

A Customer Insights az Power Platform Ügyfélkombaszéf funkciót használja. Az ügyfél-kulcszárlat felületet biztosít az adatelérési kérelmek áttekintéséhez és jóváhagyásához (vagy elutasításához). Ezek a kérések akkor fordulnak elő, ha az ügyféladatokhoz való adathozzáférésre van szükség egy támogatási eset megoldásához. A funkció használatához a Customer Insightsnak meglévő kapcsolattal kell rendelkeznie a bérlő környezetéhez Microsoft Dataverse.

Az ügyfélkompatibilitás-szal kapcsolatos további információkért tekintse meg az [Ügyfélkompatibilitási](/power-platform/admin/about-lockbox#summary) kulcs mappában található összefoglalót Power Platform. A cikk ismerteti a [munkafolyamatot](/power-platform/admin/about-lockbox#workflow) és az ügyfélkompatibilitás engedélyezéséhez szükséges [beállításokat](/power-platform/admin/about-lockbox#enable-the-lockbox-policy) is.

> [!IMPORTANT]
> A globális rendszergazdák vagy Power Platform rendszergazdák jóváhagyhatják a Power Platform Customer Insights számára kiadott ügyfélkompatinás kérelmeket.

[!INCLUDE [footer-include](includes/footer-banner.md)]
