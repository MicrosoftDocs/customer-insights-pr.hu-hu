---
title: Adatok exportálása a Customer Insightsból
description: Exportálások kezelése az adatok megosztásához.
ms.date: 03/25/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: c1078ed0ba259a6e9cde3c7ede3570890ae48e67
ms.sourcegitcommit: 33a8e21b3bf6521bdb8346f81f79fce88091ddfd
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/10/2021
ms.locfileid: "6016617"
---
# <a name="exports-preview-overview"></a>Exportálások (előzetes verzió) áttekintése

Az **Exportálások** lap megjeleníti az összes konfigurált exportálást. Az exportálások meghatározott adatokat osztanak meg különböző alkalmazásokkal. Ezek tartalmazhatnak ügyfélprofilokat vagy entitásokat, sémákat és leképezési részleteket. Mindegyik exportáláshoz szükség van egy [rendszergazda kapcsolatra, beállításra, hogy kezelhesse a hitelesítést és a hozzáférést](connections.md).

Az exportálási lap megtekintéséhez menjen az **Adatok** > **Exportpálások** lehetőségre. Minden felhasználói szerepkörrel rendelkező megtekintheti a konfigurált exportálásokat. A parancssávban a keresési mező segítségével keresse meg az exportálás nevét, a kapcsolat nevét, vagy a kapcsolat típusát.

## <a name="set-up-a-new-export"></a>Új exportálás beállítása

Az exportálás beállításához vagy szerkesztéséhez elérhető kapcsolatokra van szüksége. A kapcsolatok a [felhasználói szerepkörtől](permissions.md) függnek:
- A rendszergazdák minden kapcsolathoz rendelkeznek hozzáféréssel. Az exportálás beállításakor új kapcsolatokat is létrehozhatnak.
- A közreműködő adott kapcsolatokhoz férhetnek hozzá. Ezek a rendszergazdáktól függnek, a kapcsolatok konfigurálásához és megosztásához. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).
- A megtekintők csak a meglévő exportálásokat tekinthetik meg, létrehozni azonban nem jogosultak.

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Új exportálási cél létrehozásához válassza az **Exportálás hozzáadása** lehetőséget.

1. Az **Exportálás beállítása** ablaktáblában válassza ki a használni kívánt kapcsolatot. A [Kapcsolatokat](connections.md) a rendszergazdák kezelik. 

1. Adja meg a szükséges adatokat, majd az exportálás létrehozásához válassza a **Mentés** lehetőséget.

### <a name="edit-an-export"></a>Egy exportálás szerkesztése

1. Jelölje ki a szerkeszteni kívánt exportálási célhely függőleges három pontját.

1. Válassza a legördülő menü **Szerkesztés** lehetőséget.

1. Módosítsa a frissíteni kívánt értékeket, majd válassza a **Mentés** lehetőséget.

## <a name="view-exports-and-export-details"></a>Exportálás és exportálás részleteinek megtekintése

Az exportálási célhelyek a létrehozása után az **Adatok** > **Exportálások** listán jelennek meg. Minden felhasználó láthatja, hogy mely adatok lettek megosztva, és hogy milyen állapotúak.

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. A szerkesztési jogosultsággal nem rendelkező felhasználók a **Szerkesztés** helyett a **Megtekintés** lehetőséget választhatják az exportálás részleteinek megtekintéséhez.

1. Ez az oldalpanel mutatja az exportálás beállítását. Az értékek a szerkesztési jogosultságok nélkül nem módosíthatók. Az exportálások lapra való visszatéréshez válassza a **Bezárás** lehetőséget.

## <a name="run-exports-on-demand"></a>Exportálások futtatása igény szerint

Az exportálás konfigurálása után az összes [ütemezett frissítéssel](system.md#schedule-tab) futni fog, amíg van működő kapcsolata.

Ütemezett frissítésre való várakozás nélküli adatexportáláshoz menjen az **Adatok** > **Exportálások** lehetőségre. Két lehetőség közül választhat:

- Az összes exportálás futtatásához válassza az **Összes futtatása** lehetőséget. 
- Egyetlen exportálás futtatásához jelölje ki a három pontot (...) a listaelemen, majd válassza a **Futtatás** lehetőséget.

## <a name="remove-an-export"></a>Exportálás eltávolítása

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Jelölje ki az eltávolítani kívánt Exportálás függőleges három pontját.

1. Válassza a legördülő menü **Eltávolítás** elemét.

1. Erősítse meg az eltávolítást az **Eltávolítás** lehetőség választásával a megerősítő képernyőn.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
