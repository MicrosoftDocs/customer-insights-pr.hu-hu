---
title: Engedélyek és szerepkörök
description: A munkaterület tagjaira vonatkozó szerepkörök és jogosultságok áttekintése.
ms.reviewer: mhart
ms.author: jusali
author: jusali
ms.date: 10/01/2021
ms.subservice: engagement-insights
ms.topic: conceptual
ms.manager: shellyha
ms.openlocfilehash: ccc6a1b87b4cc28701e276b6e35432356e7647c4
ms.sourcegitcommit: e7cdf36a78a2b1dd2850183224d39c8dde46b26f
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/16/2022
ms.locfileid: "8227542"
---
# <a name="roles-and-permissions"></a>Engedélyek és szerepkörök

[!INCLUDE [cc-beta-prerelease-disclaimer](includes/cc-beta-prerelease-disclaimer.md)]

A munkaterület az események és jelentések tárolására és kezelésére szolgál. További tudnivalók: [Munkaterület létrehozása és tagok hozzáadása](create-workspace.md). 

A munkaterület a következő szerepköröket és engedélyeket tartalmazhatja:

- A *tagi* szerepkörök olyan felhasználók, akik elérhetik a munkaterületet. Hozzárendelheti a tagokat a munkaterülethez, és megadhatja a szerepköreiket és az engedélyeiket. 
- A *rendszergazdai* szerepkörök kezelik a munkaterületeket és a környezeteket, és beállítják az aktivitási információkat más felhasználók számára. 
- A *közreműködő* szerepkörök az elemzőkre irányulnak, akiknek nem kell konfigurálni az aktivitási információkat, de saját jelentéseket, tölcséreket vagy szegmenseket kell létrehozniuk.

## <a name="permissions"></a>Jogosultságok
  
Az alábbi táblázat azonosítja az egyes szerepkörre vonatkozó jogokat. 

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
