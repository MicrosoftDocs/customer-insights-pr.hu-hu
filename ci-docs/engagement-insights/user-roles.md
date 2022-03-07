---
title: Engedélyek és szerepkörök
description: A munkaterület tagjaira vonatkozó szerepkörök és jogosultságok áttekintése.
ms.reviewer: mhart
ms.author: jusali
author: jusali
ms.date: 07/06/2021
ms.service: customer-insights
ms.subservice: engagement-insights
ms.topic: conceptual
ms.manager: shellyha
ms.openlocfilehash: 6d7f4db4a130fc15a69b380c892538db5492d96d8e13f3c070c6a6b9bd098371
ms.sourcegitcommit: aa0cfbf6240a9f560e3131bdec63e051a8786dd4
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/10/2021
ms.locfileid: "7036696"
---
# <a name="roles-and-permissions"></a>Engedélyek és szerepkörök

[!INCLUDE [cc-beta-prerelease-disclaimer](includes/cc-beta-prerelease-disclaimer.md)]

A munkaterület biztosít módot arra, hogy tárolja és kezelje az eseményeket és jelentéseket. A tag olyan felhasználó, aki elérheti a munkaterületet. Hozzárendelheti a tagokat a munkaterülethez, és megadhatja a szerepköreiket és az engedélyeiket. A rendszergazdai szerepkörök kezelik a munkaterületeket és a környezeteket, és beállítják az aktivitási információkat más felhasználók számára. A közreműködő szerepkörök az elemzőkre irányulnak, akiknek nem kell konfigurálni az aktivitási információkat, de saját jelentéseket, tölcséreket vagy szegmenseket kell létrehozniuk.

## <a name="permissions"></a>Jogosultságok
  
A következő diagram azonosítja az egyes szerepkörre vonatkozó jogosultságokat. 

| Engedély | Környezet rendszergazdája | Munkaterület rendszergazdája | Környezeti közreműködő | Munkaterület-közreműködő | 
|--|--|--|--|--|
| Környezetek létrehozása (a létrehozó automatikusan környezet-rendszergazda lesz) | X* | X* | X* | X* |  
| Környezet konfigurálása (környezettagok, környezet törlése) | X |  |  |  |  
| Munkaterületek létrehozása | X |  |  |  |  
| Munkaterületek konfigurálása (munkaterület-tagok, munkaterület törlése) | X | X |  |  |  
| Események és finomított események konfigurálása | X | X | |  |  
| Munkaterület-események és finomított események megtekintése | X | X | |  |  
| Munkaterület-erőforrások (jelentések, szegmensek és metrika) megtekintése| X | X | X | X |  
| Egyéni jelentések és tölcsérek létrehozása | X | X | X | X |  
| Alapmérőszámok és dimenziók létrehozása| X | X |  |  |  
| Szegmensek létrehozása| X | X | X | X |  

*Csak előzetes verzióban hozhatók létre próbakörnyezetek. 

## <a name="add-members"></a>Tagok hozzáadása

A munkaterületekhez és környezetekhez tagokat adhat hozzá, illetve távolíthat el onnan. További információ a [Környezetek és munkaterületek](manage-environments-workspaces.md) oldalon található.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
