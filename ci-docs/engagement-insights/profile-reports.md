---
title: Egyedi profiljelentések engedélyezése
description: Hogyan hozhat létre egyedi profiljelentéseket különböző csoportokba a különböző eredetű termékekből, korból és megyéből vagy régióból.
author: darrinw-docs
ms.reviewer: mhart
ms.author: darrinw
ms.date: 05/03/2021
ms.service: customer-insights
ms.subservice: engagement-insights
ms.topic: conceptual
ms.manager: shellyha
ms.openlocfilehash: 3aa9599fc780098a2f7f31f0210d76ed2ef27ece774dd6212b5cb2a599ad537e
ms.sourcegitcommit: aa0cfbf6240a9f560e3131bdec63e051a8786dd4
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/10/2021
ms.locfileid: "7033955"
---
# <a name="out-of-box-profile-reports"></a>Egyedi profiljelentések

[!INCLUDE [cc-beta-prerelease-disclaimer](includes/cc-beta-prerelease-disclaimer.md)]

A jelentések az adatvizualizációs gyűjtemények, amelyek segítenek jobban megérteni a felhasználók viselkedését. Ha a Customer Insights célközönség-információihoz csatlakozik, akkor az aktivitási információk egy olyan jelentést mutatnak, amelyek egységesített ügyfélprofilokkal kapcsolatos információkat tartalmaznak. Ez a jelentés tartalmazza a profilok számát nem, életkor és földrajzi elhelyezkedés szerint csoportosítva.

## <a name="prerequisites"></a>Előfeltételek

A célközönség-információk környezetnek az adatokat ügyfél által felügyelt Azure Data Lake Storage-fiókokban kell tárolnia.

Ha a célközönség-információk szolgáltatásának vagy környezetének próbaverzióját használja egy Customer Insights által felügyelt adatkapcsolati szolgáltatásban, akkor segítségért [forduljon hozzánk](https://go.microsoft.com/fwlink/?linkid=2145734).  


## <a name="enable-the-customer-profile-report"></a>Az ügyfélprofil-jelentés engedélyezése

A környezet rendszergazdáinak [létre kell hozniuk egy kapcsolatot az célközönség információkhoz](configure-connections.md).

A kapcsolat részleteinek megadása után a rendszergazda hozzáférést adhat a szervezet más tagjainak a jelentés megtekintése érdekében. A kapcsolatot létrehozó környezet-rendszergazda automatikusan hozzáfér a jelentéshez. 

A kapcsolat befejezése után a **Profilok** funkció elérhető lesz a bal navigációs ablaktáblában. 

- A jelentés megtekintéséhez lépjen a **Felfedezés** > **Profilok** elemre.

A **Profilok** jelentés a csatlakoztatott ügyfélprofilok nemével, korával és földrajzi elhelyezkedésével kapcsolatos megjelenítéseket tartalmaz.

:::image type="content" source="media/customer-profiles.png" alt-text="Ügyfélprofil-jelentés.":::

[!INCLUDE[footer-include](../includes/footer-banner.md)]