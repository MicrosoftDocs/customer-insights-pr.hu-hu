---
title: Hozza magával saját Azure kulcstartóját (előzetes verzió)
description: Megtudhatja, hogyan konfigurálhatja a Customer Insightst úgy, hogy a saját Azure Key Vaultot használja a titkos kulcsok kezeléséhez.
ms.date: 08/02/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: brndkfr
ms.author: bkief
manager: shellyha
searchScope:
- ci-system-security
- customerInsights
ms.openlocfilehash: 229fb5698a02d1d73c30442f61c7b1b5fce918bf
ms.sourcegitcommit: 49394c7216db1ec7b754db6014b651177e82ae5b
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/10/2022
ms.locfileid: "9246158"
---
# <a name="bring-your-own-azure-key-vault-preview"></a>Hozza magával saját Azure kulcstartóját (előzetes verzió)

Egy dedikált [Azure Key Vault](/azure/key-vault/general/basic-concepts) és egy Customer Insights-környezet összekapcsolása segít a szervezeteknek a megfelelőségi követelmények teljesítésében.

## <a name="link-the-key-vault-to-the-customer-insights-environment"></a>A kulcstartó csatolása a Customer Insights környezethez

Állítsa be a dedikált kulcstartót a szervezet megfelelőségi határában lévő titkos kulcsok szakaszához és használatához.

### <a name="prerequisites"></a>Előfeltételek

- Aktív Azure-előfizetés.

- A [Customer Insights szolgáltatásban hozzárendelt](permissions.md#admin) rendszergazdai [szerepkör](permissions.md#add-users).

- [közreműködő](/azure/role-based-access-control/built-in-roles#contributor) és [felhasználói hozzáférés-rendszergazdai](/azure/role-based-access-control/built-in-roles#user-access-administrator) szerepköröket a kulcstartóban vagy azon az erőforráscsoporton, amelyhez a kulcstartó tartozik. További tájékoztatásért menjen az [Azure-szerepkör-hozzárendelések hozzáadása vagy eltávolítása az Azure portálon](/azure/role-based-access-control/role-assignments-portal) részre. Ha nem rendelkezik felhasználói hozzáférés-rendszergazdai szerepkörrel a kulcstartóban, állítsa be külön az Azure-szolgáltatásnév Dynamics 365 Customer Insights szerepköralapú hozzáférés-vezérlési engedélyeit. Kövesse az [Azure szolgáltatásnév használatát használata](connect-service-principal.md) a csatolni szükséges kulcstartóhoz.

- A kulcstartóban le kell tiltani Key Vault **tűzfalat**.

- A Key Vault ugyanazon [az Azure-helyen](https://azure.microsoft.com/global-infrastructure/geographies/#overview) található, mint a Customer Insights környezet. A Customer Insightsban lépjen a **Felügyeleti** > **rendszer** és a **Névjegy** lapra a környezet régiójának megtekintéséhez.

### <a name="recommendations"></a>Javaslatok

- [Használjon külön vagy dedikált kulcstartót](/azure/key-vault/general/best-practices#why-we-recommend-separate-key-vaults), amely csak a Customer Insightshoz szükséges titkos kulcsokat tartalmazza.

- A [Key Vault gyakorlati tanácsok](/azure/key-vault/general/best-practices#turn-on-logging) szerint szabályozhatja a hozzáférést, a biztonsági mentést, a naplózást és a helyreállítást.

### <a name="link-a-key-vault-to-the-environment"></a>A kulcstartó csatolása a környezethez

1. Válassza a **Rendszergazdai** > **biztonság** lehetőséget, majd válassza a **Key Vault** lapot.
1. Válassza a **Key Vault** csempén a **Telepítőt**.
1. **Előfizetés** kiválasztása.
1. Válasszon egy kulcstartót a **Key Vault** legördülő listából. Ha túl sok kulcstartó érhető el, válasszon ki egy erőforráscsoportot a keresési eredmények korlátozásához.
1. Tekintse át az [Adatvédelem és a megfelelés](connections.md#data-privacy-and-compliance) lehetőséget, és válassza az **Elfogadom** lehetőséget.
1. Válassza a **Mentés** parancsot.

A **Key Vault** csempe a csatolt kulcstartó nevét, előfizetését és erőforráscsoportját jeleníti meg. Készen áll a kapcsolat beállításában való használatra.
A kulcstartón a Customer Insights számára adott engedélyekkel kapcsolatos részletekért tekintse meg [a kulcstartón](#permissions-granted-on-the-key-vault) megadott engedélyeket.

## <a name="use-the-key-vault-in-the-connection-setup"></a>A kulcstartó használata a kapcsolat beállításában

Amikor [kapcsolatokat állít be](connections.md) a támogatott külső [rendszerekhez](#supported-connection-types), a csatolt kulcstár titkos kulcsait használva konfigurálja a kapcsolatokat.

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.
1. **Kapcsolat hozzáadásának** kiválasztása.
1. A támogatott kapcsolattípusok esetén a **Key Vault használata** kapcsológomb érhető el, ha a kulcstartót csatolta.
1. A titkos kulcs manuális megadása helyett válassza ki azt a titkos nevet, amely a kulcstartóban lévő titkos értékre mutat.

   :::image type="content" source="media/use-key-vault-secret.png" alt-text="A Key Vault titkos kódot használó SFTP-kapcsolattal rendelkező kapcsolati panel.":::

1. Válassza a Mentés **lehetőséget** a kapcsolat létrehozásához.

## <a name="supported-connection-types"></a>Támogatott kapcsolattípusok

A következő [exportálási](export-destinations.md) kapcsolatok támogatottak:

* [ActiveCampaign](export-active-campaign.md)
* [Autopilot](export-autopilot.md)
* [DotDigital](export-dotdigital.md)
* [Google Ads](export-google-ads.md)
* [Klaviyo](export-klaviyo.md)
* [LiveRamp](export-liveramp.md)
* [Marketo](export-marketo.md)
* [Omnisend](export-omnisend.md)
* [Salesforce Marketing Cloud](export-salesforce.md)
* [Sendgrid](export-sendgrid.md)
* [Sendinblue](export-sendinblue.md)
* [SFTP](export-sftp.md)

## <a name="permissions-granted-on-the-key-vault"></a>A kulcstartón megadott engedélyek

A következő engedélyeket kapja meg a Customer Insights egy csatolt kulcstartón, ha a [Key Vault hozzáférési szabályzat](/azure/key-vault/general/assign-access-policy?tabs=azure-portal) vagy [az Azure szerepköralapú hozzáférés-vezérlése](/azure/key-vault/general/rbac-guide?tabs=azure-cli) engedélyezve van.

### <a name="key-vault-access-policy"></a>Key Vault hozzáférési szabályzat

| Típus szerint        | Jogosultságok          |
| ----------- | -------------------- |
| Billentyű         | [Kulcsok beszerzése](/rest/api/keyvault/keys/get-keys/get-keys), [Kulcs beszerzése](/rest/api/keyvault/keys/get-key/get-key)                                 |
| Titkos      | [Titkos kódok beszerzése](/rest/api/keyvault/secrets/get-secrets/get-secrets), [Titkos kód beszerzése](/rest/api/keyvault/secrets/get-secret/get-secret)                     |
| Tanúsítvány | [Tanúsítványok beszerzése](/rest/api/keyvault/certificates/get-certificates/get-certificates), [Tanúsítvány beszerzése](/rest/api/keyvault/certificates/get-certificate/get-certificate) |

Az előző értékek a minimumok, amelyeket fel kell sorolni és ki kell olvasni a végrehajtás során.

### <a name="azure-role-based-access-control"></a>Azure szerepköralapú hozzáférés-vezérlő

A [Key Vault olvasó és Key Vault titkos kulcsok felhasználói szerepkörei](/azure/key-vault/general/rbac-guide?tabs=azure-cli) hozzá lesznek adva a Customer Insightshoz.

## <a name="frequently-asked-questions"></a>Gyakori kérdések

### <a name="can-customer-insights-write-secrets-or-overwrite-secrets-into-the-key-vault"></a>A Customer Insights írhat titkos kulcsokat, vagy felülírhatja a titkos kulcsokat a kulcstartóba?

Nem. A Customer Insights csak a megadott engedélyekben [ismertetett](#permissions-granted-on-the-key-vault) olvasási és listaengedélyeket kapja meg. A rendszer nem tud titkos kódokat felvenni, törölni vagy felülírni a kulcstartóban. Ezért nem lehet hitelesítő adatokat megadni, ha egy kapcsolat a Key Vaultot használja.

### <a name="can-i-change-a-connection-from-using-key-vault-secrets-to-default-authentication"></a>Megváltoztathatom a Key Vault-titkok használatának kapcsolatát alapértelmezett hitelesítésre?

Szám Nem tud visszaváltani alapértelmezett kapcsolatra, miután konfigurálta egy csatolt kulcstartóból származó titkos kód használatával. Hozzon létre külön kapcsolatot, és törölje a régit, ha már nincs rá többé szüksége.

### <a name="how-can-i-revoke-access-to-a-key-vault-for-customer-insights"></a>Hogyan vonhatom vissza a Customer Insights kulcstartójához való hozzáférést?

Ha a Key Vault hozzáférési szabályzat [vagy](/azure/key-vault/general/assign-access-policy?tabs=azure-portal) az [Azure szerepköralapú hozzáférés-vezérlés](/azure/key-vault/general/rbac-guide?tabs=azure-cli) engedélyezve van, távolítsa el a szolgáltatásnév `0bfc4568-a4ba-4c58-bd3e-5d3e76bd7fff` engedélyeit a következő névvel`Dynamics 365 AI for Customer Insights`: . A kulcstartót használó összes kapcsolat leáll.

### <a name="a-secret-thats-used-in-a-connection-got-removed-from-the-key-vault-what-can-i-do"></a>A kapcsolatban használt titkos kódot a rendszer eltávolította a kulcstartóból. Mit tehetek?

Egy értesítés jelenik meg a Customer Insightsban, ha a kulcstartóból származó konfigurált titkos kulcs már nem érhető el. Ha véletlenül eltávolítják őket, engedélyezze a kulcstartónak a titkok [visszaállítását](/azure/key-vault/general/soft-delete-overview).

### <a name="a-connection-doesnt-work-but-my-secret-is-in-the-key-vault-what-might-be-the-cause"></a>A kapcsolat nem működik, de a kulcstartóban van a kapcsolat. Mi lehet az oka?

Egy értesítés jelenik meg a Customer Insightsban, ha nem fér hozzá a kulcstartóhoz. Az ok a következő lehet:

- A Customer Insights szolgáltatásnév engedélyei el lettek távolítva. Manuálisan kell visszaállítani őket.

- A kulcstartón engedélyezett a tűzfal. A tűzfalat le kell tiltani, hogy a kulcstartó újra elérhető legyen a Customer Insights számára.
