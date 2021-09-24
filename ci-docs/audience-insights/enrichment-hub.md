---
title: Az egyesített ügyfélprofilok bővítése
description: A funkciók segítségével bővítheti az ügyféladatokat.
ms.date: 08/31/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: jodahlMSFT
ms.author: jodahl
manager: shellyha
ms.custom: intro-internal
ms.openlocfilehash: 992c45e30e2dff00f5207290940b56b2fe1c08ad
ms.sourcegitcommit: b9a81c2acd42d774669d2db3d0430c7d81de991c
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/02/2021
ms.locfileid: "7469985"
---
# <a name="enrichment-for-customer-profiles-preview"></a>Az ügyfelek profiljainak bővítése (előzetes verzió)

Adatok felhasználása olyan forrásokból, mint például a Microsoft és más partnerek az ügyféladatok bővítése céljából.

:::image type="content" source="media/enrichment-hub-page.png" alt-text="A bővítési központ oldala.":::

A célközönség-információkban lépjen az **Adatok** > **Bővítés** pontra a bővítési lehetőségek használatához.  

A bővítések létrehozásához vagy módosításához Közreműködő vagy Rendszergazdai engedélyekkel kell rendelkeznie. További tudnivalók: [Engedélyek](permissions.md).

A **felderítés** lapon a következő bővítések találhatók:

- [Azure Maps](enrichment-azure-maps.md) a Microsoft jóvoltából
- A Microsoft által biztosított [márkák](enrichment-microsoft.md)
- A Microsoft által biztosított [érdeklődési körök](enrichment-microsoft.md)
- A Microsoft által biztosított [továbbfejlesztett címek](enrichment-enhanced-addresses.md)
- A Leadspace által biztosított [vállalati adatok](enrichment-leadspace.md)
- [Demográfiai adatok](enrichment-experian.md) az Experian által megadva
- A [Helyadatokat](enrichment-here.md) a HERE Technologies biztosította
- [Egyéni adatok](enrichment-SFTP-custom-import.md) SFTP-importálás biztonságos fájlátviteli protokollján keresztül

A **saját bővítések** lapon megtekintheti, hogy milyen bővítés van beállítva, illetve hogy szerkesztheti-e a tulajdonságait.

## <a name="manage-existing-enrichments"></a>Meglévő bővítések kezelése

Menjen a **Saját bővítéseim** fülre az összes konfigurált bővítés megtekintéséhez. Minden bővítés egy sor formájában jelenik meg, amely további információkat tartalmaz a bővítésről.

Az elérhető lehetőségekért válassza ki a bővítést. A listaelemen a három pont (...) kijelölésével megtekintheti a lehetőségeket. Ha több bővítést is konfigurált, a keresőmező segítségével gyorsan megkeresheti.

:::image type="content" source="media/enrichment-hub-options-run.png" alt-text="A bővítések listájában a bővítés kezelésére szolgáló lehetőségek.":::

- **Nézet** a bővítés részleteinek megtekintése a bővített ügyfelek profiljainak számával.
- **Szerkesztheti** bővítés konfigurációját.
- A bővítés **Futtatásával** frissítheti az ügyfelek profiljait a legfrissebb adatokkal.
- **Inaktiválhat** egy meglévő bővítést, hogy leállítsa annak automatikus frissítését az egyes ütemezett frissítések során. Az utolsó sikeres frissítésből származó adatok továbbra is elérhetők lesznek. **Aktiválhat** egy inaktív bővítést az automatikus frissítés újraindításához minden ütemezett frissítéshez.
- A bővítés **Törlése**.

A listában való kijelölésvel egyszerre futtathat vagy inaktiválhat több bővítést. A megtekintése és szerkesztés lehetőségek nem érhetők el tömeges műveletként. Egyszerre csak egy bővítéssel működnek.

## <a name="enrichments-and-connections"></a>Bővítések és kapcsolatok

A külső gyártótól származó bővítéseket a [kapcsolatok](connections.md) használatával konfigurálhatja, amelyekhez a rendszergazda hitelesítő adatokat állít be, és hozzájárul az adatok átviteléhez. A kapcsolat ezután a rendszergazdák és a közreműködők által is használható a bővítések konfigurálásához.  

## <a name="multiple-enrichments-of-the-same-type"></a>Azonos típusú többszörös bővítések

A bővíteni kívánt entitást a bővítési konfiguráció során adja meg, ezzel lehetővé teszi, hogy csak a profilok egy részében bővítsen. Például csak egy adott szegmens adatait bővítse. Konfigurálhat több ugyanolyan típusú bővítést, és újra felhasználhatja ugyanazt a kapcsolatot. Egyes bővítések az azonos típusú, létrehozható bővítések számára vonatkoznak korlátozások. A korlátok és az aktuális használat a **Bővítés** oldalon látható.

## <a name="see-the-progress-of-the-enrichment-process"></a>A gyarapítási folyamat előrehaladásának megtekintése

A gyarapítás feldolgozásáról részleteket, köztük az állapotot és a lehetséges problémákat megismerheti a frissítés közben vagy egy frissítés befejezése után. Megtudhatja, milyen folyamatok voltak érintettek egy bővítés frissítésében, és mennyi ideig tartott a folyamatok futtatása. A gyarapítási állapot támogatott az Experian, a Leadtér, a HERE Technologies, az SFTP Import és az Azure Maps esetében.

A gyarapítás állapotának megtekintése

1. Lépjen az **Adatok** > **Bővítés** pontra. 
1. Az oldalpanel megnyitásához válassza ki a **Saját bővítések** lapot a Gyarapítás állapotának megtekintéséhez. 
1. A **Folyamat részletei** ablaktáblában bontsa ki az **Bővítések** szakaszt. 
1. A bővítés során látni szeretné a haladást, válassza a **Részletek megtekintése** lehetőséget. 
1. A **Feladat részletei** ablaktáblában válassza a **Részletek megjelenítése** lehetőséget, és tekintse meg a bővítésben érintett folyamatokat és az állapotukat. 

[!INCLUDE[footer-include](../includes/footer-banner.md)]
