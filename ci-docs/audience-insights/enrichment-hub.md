---
title: Az egyesített ügyfélprofilok bővítése
description: A funkciók segítségével bővítheti az ügyféladatokat.
ms.date: 04/09/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: jodahlMSFT
ms.author: jodahl
manager: shellyha
ms.openlocfilehash: c8e4a7247ccf575a62440038180010916b09d51b
ms.sourcegitcommit: f9e2fa3f11ecf11a5d9cccc376fdeb1ecea54880
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/28/2021
ms.locfileid: "5954490"
---
# <a name="enrichment-for-customer-profiles-preview"></a>Az ügyfelek profiljainak bővítése (előzetes verzió)

Adatok felhasználása olyan forrásokból, mint például a Microsoft és más partnerek az ügyféladatok bővítése céljából.

:::image type="content" source="media/enrichment-hub-page.png" alt-text="A bővítési központ oldala":::

A célközönség-információkban lépjen az **Adatok** > **Bővítés** pontra a bővítési lehetőségek használatához.    
A bővítések létrehozásához vagy módosításához Közreműködő vagy Rendszergazdai engedélyekkel kell rendelkeznie. További tudnivalók: [Engedélyek](permissions.md).

A **felderítés** lapon a következő bővítések találhatók:

- A Microsoft által biztosított [márkák](enrichment-microsoft.md)
- A Microsoft által biztosított [érdeklődési körök](enrichment-microsoft.md)
- A Microsoft által biztosított [továbbfejlesztett címek](enrichment-enhanced-addresses.md)
- A Leadspace által biztosított [vállalati adatok](enrichment-leadspace.md)
- [Demográfia](enrichment-experian.md) az Experiantól
- A [Helyadatokat](enrichment-here.md) a HERE Technologies biztosította
- [Egyéni adatok](enrichment-SFTP-custom-import.md) SFTP-importálás biztonságos fájlátviteli protokollján keresztül

A **saját bővítések** lapon megtekintheti, hogy milyen bővítés van beállítva, illetve hogy szerkesztheti-e a tulajdonságait.

## <a name="manage-existing-enrichments"></a>Meglévő bővítések kezelése

Nyissa meg a **Saját bővítések** lehetőséget az összes konfigurált bővítés megtekintéséhez. Minden bővítés egy sor formájában jelenik meg, amely további információkat tartalmaz a bővítésről.

A rendelkezésre álló lehetőségek megtekintéséhez válasszon egy bővítést. A listaelemen a három pont (...) kijelölésével megtekintheti a lehetőségeket.

:::image type="content" source="media/enrichment-hub-options-run.png" alt-text="A bővítések listájában a bővítés kezelésére szolgáló lehetőségek":::

- **Nézet** a bővítés részleteinek megtekintése a bővített ügyfelek profiljainak számával.
- **Szerkesztheti** bővítés konfigurációját.
- A bővítés **Futtatásával** frissítheti az ügyfelek profiljait a legfrissebb adatokkal.
- **Inaktiválhat** egy meglévő bővítést, hogy leállítsa annak automatikus frissítését az egyes ütemezett frissítések során. Az utolsó sikeres frissítésből származó adatok továbbra is elérhetők lesznek. **Aktiválhat** egy inaktív bővítést az automatikus frissítés újraindításához minden ütemezett frissítéshez.
- Egy bővítés **törlése**.

Egyszerre több bővítést is futtathat vagy inaktiválhat, ha kijelöli azokat a listából. A beállítások megtekintése és szerkesztése nem érhető el tömeges műveletként, és egyszerre csak egy bővítéshez használható.

## <a name="enrichments-and-connections"></a>Bővítések és kapcsolatok

A külső gyártótól származó bővítéseket a [kapcsolatok](connections.md) használatával konfigurálhatja, amelyekhez a rendszergazda hitelesítő adatokat állít be, és hozzájárul az adatok átviteléhez. A kapcsolat ezután a rendszergazdák és a közreműködők által is használható a bővítések konfigurálásához.  

## <a name="multiple-enrichments-of-the-same-type"></a>Azonos típusú többszörös bővítések

A bővíteni kívánt entitást a bővítési konfiguráció során adja meg, ezzel lehetővé teszi, hogy csak a profilok egy részében bővítsen. Például csak egy adott szegmensre vonatkozó adatok bővítése. Konfigurálhat több ugyanolyan típusú bővítést, és újra felhasználhatja ugyanazt a kapcsolatot. Egyes bővítések az azonos típusú, létrehozható bővítések számára vonatkoznak korlátozások. A korlátok és az aktuális használat a **Bővítés** oldalon látható.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
