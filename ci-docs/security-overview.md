---
title: Biztonsági beállítások konfigurálása
description: További információ a biztonsági beállításokról a Dynamics 365 Customer Insights.
ms.date: 08/02/2022
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
ms.reviewer: mhart
manager: shellyha
ms.openlocfilehash: ea21163d7dd05370de28ca8340ae9583846adb26
ms.sourcegitcommit: 49394c7216db1ec7b754db6014b651177e82ae5b
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/10/2022
ms.locfileid: "9246065"
---
# <a name="configure-security-settings"></a>Biztonsági beállítások konfigurálása

Api-kulcsokat kezelhet, hozzáférhet az ügyféladatokhoz, és beállíthat egy Azure Private Link.

## <a name="manage-api-keys"></a>API-kulcsok kezelése

Tekintse meg és kezelje a kulcsokat, hogy a [Customer Insights API-kat](apis.md) a környezetében lévő adatokkal használhassa.

1. Lépjen a **Rendszerbiztonság** > **elemre,** és válassza az **API-k** lapot.

1. Ha a környezethez való API-hozzáférés nincs beállítva, válassza az Engedélyezés **lehetőséget**. Vagy a környezethez való API-hozzáférés blokkolásához válassza a Letiltás **és megerősítés lehetőséget**.

1. Az elsődleges és másodlagos API-kulcsok kezelése:

   1. Az elsődleges vagy másodlagos API-kulcs megjelenítéséhez válassza a **Megjelenítés** szimbólumot.

   1. Az elsődleges vagy másodlagos API-kulcs másolásához válassza a **Másolás** szimbólumot.

   1. Új elsődleges vagy másodlagos API-kulcsok létrehozásához válassza az Elsődleges **vagy a Másodlagos újragenerálás lehetőséget** **.**

## <a name="securely-access-customer-data-with-customer-lockbox-preview"></a>Biztonságosan hozzáférhet az ügyféladatokhoz az ügyfélkostátusz-kulcs segítségével (előzetes verzió)

A Customer Insights az Power Platform Ügyfélkompatibilitási lehetőséget használja. Az ügyfél-kulcszárlat felületet biztosít az adatelérési kérelmek áttekintéséhez és jóváhagyásához (vagy elutasításához). Ezek a kérések akkor fordulnak elő, ha az ügyféladatokhoz való adathozzáférésre van szükség egy támogatási eset megoldásához. A funkció használatához a Customer Insightsnak meglévő kapcsolattal kell rendelkeznie a bérlő környezetéhez Microsoft Dataverse.

Az ügyfélkompatibilitás-szal kapcsolatos további információkért tekintse meg az [Ügyfélkompatibilitási](/power-platform/admin/about-lockbox#summary) kulcs mappában található összefoglalót Power Platform. A cikk ismerteti a [munkafolyamatot](/power-platform/admin/about-lockbox#workflow) és az ügyfélkompatibilitás engedélyezéséhez szükséges [beállításokat](/power-platform/admin/about-lockbox#enable-the-lockbox-policy) is.

> [!IMPORTANT]
> A globális rendszergazdák vagy Power Platform rendszergazdák jóváhagyhatják a Power Platform Customer Insights számára kiadott ügyfélkompatinás kérelmeket.

## <a name="set-up-an-azure-private-link"></a>Azure Private Link beállítása

[Azure Private Link](/azure/private-link/private-link-overview) lehetővé teszi, hogy a Customer Insights a virtuális hálózat privát végpont keresztül csatlakozzon a fiókjához Azure Data Lake Storage. A tárfiókban lévő adatok esetében, amelyek nincsenek kitéve a nyilvános internetnek, Private Link engedélyezi a kapcsolatot az adott korlátozott hálózattal.

> [!IMPORTANT]
> Minimális szerepkör-követelmény a Private Link beállításához:
>
> - Customer Insights: Rendszergazda
> - Beépített Azure-szerepkör: [Storage-fiók közreműködő](/azure/role-based-access-control/built-in-roles#storage-account-contributor)
> - Engedélyek egyéni Azure-szerepkörhöz: [Microsoft.Storage/storageAccounts/read és Microsoft.Storage/storageAccounts/PrivateEndpointConnectionsApproval/action](/azure/role-based-access-control/resource-provider-operations#microsoftstorage)

1. A Customer Insightsban válassza a Rendszergazdai biztonság lehetőséget **, és válassza a** > **Privát hivatkozások** **lapot.**

1. Válassza a Private Link **hozzáadása lehetőséget**.

   A **Private Link** hozzáadása panel felsorolja a bérlőtől származó olyan tárfiókokat, amelyek megtekintéséhez engedélyekkel rendelkezik.

1. Válassza ki az előfizetést, az erőforráscsoportot és a tárfiókot.

1. Tekintse át az adatvédelmet és a megfelelőséget, és válassza az [Elfogadom lehetőséget](connections.md#data-privacy-and-compliance)**.**

1. Válassza a **Mentés** parancsot.

1. Nyissa meg a Data Lake Storage-fiókját, és nyissa meg a képernyőn megjelenő hivatkozást.

1. Hagyja jóvá a Private Link.


[!INCLUDE [footer-include](includes/footer-banner.md)]
