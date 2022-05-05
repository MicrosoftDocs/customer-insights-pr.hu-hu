---
title: Saját Azure kulcstartót hozhat a titkok kezeléséhez
description: Ismerje meg, hogyan konfigurálhatja a Customer Insights-t a saját Azure Key Vault használatára.
ms.date: 10/06/2021
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: brndkfr
ms.author: bkief
manager: shellyha
searchScope:
- ci-system-security
- customerInsights
ms.openlocfilehash: 9eb06a1190fe4e8012ecd3d6742b8b3f5f4d6349
ms.sourcegitcommit: cf74b8c20d88eb96e1ac86e18cd44fe27aad5ab9
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/28/2022
ms.locfileid: "8653480"
---
# <a name="bring-your-own-azure-key-vault-preview"></a>Hozza magával saját Azure kulcstartóját (előzetes verzió)

A dedikált [Azure-kulcstartó](/azure/key-vault/general/basic-concepts) és a Customer Insights-környezet összekapcsolása segít a szervezeteknek megfelelni a megfelelőségi követelményeknek.
A dedikált kulcstartó a szervezet megfelelési határán belül a fázisok és a titkok használatára használható. A Customer Insights az Azure Key Vault titkos kulcsait felhasználhatja a harmadik féltől származó rendszerekhez való kapcsolatok [beállításához](connections.md).

## <a name="link-the-key-vault-to-the-customer-insights-environment"></a>A kulcstartó csatolása a Customer Insights környezethez

### <a name="prerequisites"></a>Előfeltételek

A Customer Insights kulcstartójának konfigurálásához a következő előfeltételeknek kell teljesülniük:

- Azure előfizetéssel kell rendelkeznie.

- Rendszergazdai [szerepkörrel](permissions.md#admin) rendelkezik a Customer Insights alkalmazásban. További információ a felhasználói engedélyekről [a Customer Insightsban](permissions.md#assign-roles-and-permissions).

- Rendelkezik a [Közreműködő](/azure/role-based-access-control/built-in-roles#contributor) és [Felhasználói hozzáférési rendszergazdai](/azure/role-based-access-control/built-in-roles#user-access-administrator) szerepkörökkel a kulcstartó vagy a kulcstartóhoz tartozó erőforráscsoportban. További tájékoztatásért menjen az [Azure-szerepkör-hozzárendelések hozzáadása vagy eltávolítása az Azure portálon](/azure/role-based-access-control/role-assignments-portal) részre. Ha nem rendelkezik Felhasználói hozzáférési rendszergazda szerepkörrel a kulcstartó szolgáltatásban, akkor külön kell beállítania a szerepköralapú hozzáférés-vezérlési engedélyeket a Dynamics 365 Customer Insights Azure szolgáltatásnévvel. Kövesse az [Azure szolgáltatásnév használatát használata](connect-service-principal.md) a csatolni szükséges kulcstartóhoz.

- A kulcstartónak le kell tiltani a **Key Vault-tűzfalat**.

- A kulcstartó ugyanabban [az Azure-helyen](https://azure.microsoft.com/global-infrastructure/geographies/#overview) található, mint a Customer Insights környezet. A Customer Insights környezetének régiója az **AdminSystemAboutRegion** > **·** > **·** > **csoportban** található.

### <a name="link-a-key-vault-to-the-environment"></a>A kulcstartó csatolása a környezethez

1. Nyissa meg az **AdminSecurity** > **elemet**, majd válassza a **Key Vault** lapot.
1. Válassza a **Key Vault** csempén a **Telepítőt**.
1. **Előfizetés** kiválasztása.
1. Válasszon egy kulcstartót a **Key Vault** legördülő listából. Ha túl sok kulcstartó jelenik meg, a keresés eredményének korlátozására jelöljön ki egy erőforráscsoportot.
1. Fogadja el az **Adatvédelmi és a megfelelőségi** nyilatkozatot.
1. Válassza a **Mentés** parancsot.

:::image type="content" source="media/set-up-azure-key-vault.png" alt-text="Csatolt kulcstartó beállításának lépései a Customer Insights alkalmazásban.":::

A **Key Vault** csempén most a csatolt kulcstartó neve, az erőforráscsoport és az előfizetés látható. Készen áll a kapcsolat beállításában való használatra.
A kulcstartóra vonatkozó engedélyek ügyfélelemzési szolgáltatással kapcsolatos részleteiről a cikk későbbi részében, [a kulcstartón](#permissions-granted-on-the-key-vault) megadott engedélyek című témakörben olvashat.

## <a name="use-the-key-vault-in-the-connection-setup"></a>A kulcstartó használata a kapcsolat beállításában

A külső rendszerekhez való [kapcsolatok beállítása](connections.md) során a csatolt Key Vault titkokat a kapcsolatok konfigurálására használhatja.

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.
1. **Kapcsolat hozzáadásának** kiválasztása.
1. A támogatott kapcsolattípusok esetén a **Key Vault használata** kapcsológomb érhető el, ha a kulcstartót csatolta.
1. Ahelyett, hogy kézzel lépne be a tárolóba, kiválaszthatja azt a nevet, amely a kulcstartóban megadott értékre mutat.

:::image type="content" source="media/use-key-vault-secret.png" alt-text="A Key Vault titkos kódot használó SFTP-kapcsolattal rendelkező kapcsolati panel.":::

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

## <a name="permissions-granted-on-the-key-vault"></a>A kulcstartóhoz megadott engedélyek

Ha a Key Vault hozzáférési szabályzata [vagy](/azure/key-vault/general/assign-access-policy?tabs=azure-portal) az Azure szerepköralapú hozzáférés-vezérlés [engedélyezve van, a következő engedélyek adhatók meg a Customer Insights számára egy csatolt kulcstartóban](/azure/key-vault/general/rbac-guide?tabs=azure-cli).

### <a name="key-vault-access-policy"></a>Key Vault hozzáférési szabályzat

| Típus szerint        | Jogosultságok          |
| ----------- | -------------------- |
| Billentyű         | [Kulcsok beszerzése](/rest/api/keyvault/get-keys), [Kulcs beszerzése](/rest/api/keyvault/get-key)                                 |
| Titkos      | [Titkos kódok beszerzése](/rest/api/keyvault/get-secrets), [Titkos kód beszerzése](/rest/api/keyvault/get-secret)                     |
| Tanúsítvány | [Tanúsítványok beszerzése](/rest/api/keyvault/get-certificates), [Tanúsítvány beszerzése](/rest/api/keyvault/get-certificate) |

Az előző értékek a minimumok, amelyeket fel kell sorolni és ki kell olvasni a végrehajtás során.

### <a name="azure-role-based-access-control"></a>Azure szerepköralapú hozzáférés-vezérlő

A Key Vault olvasó és Key Vault Secrets felhasználói szerepkörei hozzáadódnak a Customer Insightshoz. Ezekről a szerepkörökről a [Key Vault adatsík műveletekhez rendelt Azure beépített szerepkök](/azure/key-vault/general/rbac-guide?tabs=azure-cli) részben olvashat.

## <a name="recommendations"></a>Javaslatok

- Használjon külön vagy dedikált kulcstartót, amely csak a Customer Insightshoz szükséges titkos kulcsokat tartalmazza. További információk arról, hogy miért [ajánlott külön kulcstartókat ](/azure/key-vault/general/best-practices#why-we-recommend-separate-key-vaults) használni.

- A [Key Vault gyakorlati tanácsok](/azure/key-vault/general/best-practices#turn-on-logging) szerint szabályozhatja a hozzáférést, a biztonsági mentést, a naplózást és a helyreállítást.

## <a name="frequently-asked-questions"></a>Gyakori kérdések

### <a name="can-customer-insights-write-secrets-or-overwrite-secrets-into-the-key-vault"></a>A Customer Insights írhat-e titkokat vagy felülírhat titkokat a kulcstartóba?

Szám Csak a cikk korábbi részében megadott engedélyek [szakaszban ismertetett](#permissions-granted-on-the-key-vault) olvasási és listaengedélyek adhatók meg az Ügyfélelemzésnek. A rendszer nem tud titkos kódokat felvenni, törölni vagy felülírni a kulcstartóban. Ezért nem lehet hitelesítő adatokat megadni, ha egy kapcsolat a Key Vaultot használja.

### <a name="can-i-change-a-connection-from-using-key-vault-secrets-to-default-authentication"></a>Megváltoztathatom a Key Vault-titkok használatának kapcsolatát alapértelmezett hitelesítésre?

Szám Nem tud visszaváltani alapértelmezett kapcsolatra, miután konfigurálta egy csatolt kulcstartóból származó titkos kód használatával. Hozzon létre külön kapcsolatot, és törölje a régit, ha már nincs rá többé szüksége.

### <a name="how-can-i-revoke-access-to-a-key-vault-for-customer-insights"></a>Hogyan vonhatom vissza a hozzáférést a Customer Insights kulcstartójához?

Attól függően, hogy a [Key Vault hozzáférési irányelv](/azure/key-vault/general/assign-access-policy?tabs=azure-portal) vagy az [Azure szerepköralapú hozzáférés-vezérlő](/azure/key-vault/general/rbac-guide?tabs=azure-cli) engedélyezve van-e, el kell távolítania a `0bfc4568-a4ba-4c58-bd3e-5d3e76bd7fff` szolgáltatásnévvel rendelkező `Dynamics 365 AI for Customer Insights` nevű jogosultságokat. A kulcstartót használó összes kapcsolat leáll.

### <a name="a-secret-thats-used-in-a-connection-got-removed-from-the-key-vault-what-can-i-do"></a>A kapcsolatban használt titkos kódot a rendszer eltávolította a kulcstartóból. Mit tehetek?

Értesítés jelenik meg a Customer Insights alkalmazásban, ha a kulcstartóból származó konfigurált titok már nem érhető el. Ha véletlenül eltávolítják őket, engedélyezze a kulcstartónak a titkok [visszaállítását](/azure/key-vault/general/soft-delete-overview).

### <a name="a-connection-doesnt-work-but-my-secret-is-in-the-key-vault-what-might-be-the-cause"></a>A kapcsolat nem működik, de a kulcstartóban van a kapcsolat. Mi lehet az oka?

Értesítés jelenik meg a Customer Insights alkalmazásban, ha nem fér hozzá a kulcstartóhoz. Az ok a következő lehet:

- A Customer Insights szolgáltatásnév engedélyei törlődtek. Manuálisan kell visszaállítani őket.

- A kulcstartón engedélyezett a tűzfal. A tűzfalat le kell tiltani ahhoz, hogy a kulcstartó ismét elérhető legyen a Customer Insights számára.
