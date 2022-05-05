---
title: Biztonsági beállítások a Dynamics 365 Customer Insights
description: További információ a biztonsági beállításokról a alkalmazásban Dynamics 365 Customer Insights.
ms.date: 04/28/2022
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
ms.reviewer: mhart
manager: shellyha
ms.openlocfilehash: 5d73bacccadc9193d76d8dfafd0365dabc911e00
ms.sourcegitcommit: cf74b8c20d88eb96e1ac86e18cd44fe27aad5ab9
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/28/2022
ms.locfileid: "8653786"
---
# <a name="security-overview-page"></a>Biztonság áttekintése lap

A **Biztonság** lap felsorolja a felhasználói engedélyek és szolgáltatások biztonságosabbá tételét Dynamics 365 Customer Insights segítő beállításokat. Csak rendszergazdák férhetnek hozzá ehhez a laphoz. 

A beállítások konfigurálásához nyissa meg **az AdminSecurity** > **webhelyet**.

A **Biztonság** lap a következő lapokat tartalmazza:
- [Felhasználók](#users-tab)
- [API-k](#apis-tab)
- [ Key Vault](#key-vault-tab)

## <a name="users-tab"></a>Felhasználók lap

Az Ügyfélelemzésekhez való hozzáférés a szervezet azon felhasználóira korlátozódik, akiket egy rendszergazda adott hozzá az alkalmazáshoz. A **Felhasználók** lapon kezelheti a felhasználói hozzáférést és engedélyeiket. További információt a Felhasználói engedélyek [című témakörben talál](permissions.md).

## <a name="apis-tab"></a>API-k lapja

Tekintse meg és kezelje a kulcsokat a [Customer Insights API-k](apis.md) környezetének adataival való használatához.

Új elsődleges és másodlagos kulcsokat az Elsődleges **újragenerálás vagy** a Másodlagos **újragenerálás lehetőséget választva** hozhat létre. 

Ha le szeretné tiltani az API-hozzáférést a környezethez, válassza a Letiltás **lehetőséget**. Ha az API-k le vannak tiltva, az Engedélyezés **lehetőséget választva** újra hozzáférést adhat.

## <a name="key-vault-tab"></a>Kulcstartó lap

A **Key Vault** lapon összekapcsolhatja és kezelheti saját [Azure-kulcstartóját](/azure/key-vault/general/basic-concepts) a környezethez.
A dedikált kulcstartó a szervezet megfelelési határán belül a fázisok és a titkok használatára használható. A Customer Insights az Azure Key Vault titkos kulcsait felhasználhatja a harmadik féltől származó rendszerekhez való kapcsolatok [beállításához](connections.md).

További információkért lásd: [Hozza magával saját Azure-kulcstartóját](use-azure-key-vault.md).


[!INCLUDE [footer-include](includes/footer-banner.md)]
