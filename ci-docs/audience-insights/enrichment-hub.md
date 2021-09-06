---
title: Az egyesített ügyfélprofilok bővítése
description: A funkciók segítségével bővítheti az ügyféladatokat.
ms.date: 07/01/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: jodahlMSFT
ms.author: jodahl
manager: shellyha
ms.custom: intro-internal
ms.openlocfilehash: a64bbd754d4013d0a6243074ac9f55991547be82b269047a9937b583baf98697
ms.sourcegitcommit: aa0cfbf6240a9f560e3131bdec63e051a8786dd4
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/10/2021
ms.locfileid: "7032531"
---
# <a name="enrichment-for-customer-profiles-preview"></a>Az ügyfelek profiljainak bővítése (előzetes verzió)

Adatok felhasználása olyan forrásokból, mint például a Microsoft és más partnerek az ügyféladatok bővítése céljából.

:::image type="content" source="media/enrichment-hub-page.png" alt-text="A bővítési központ oldala.":::

A célközönség-információkban lépjen az **Adatok** > **Bővítés** pontra a bővítési lehetőségek használatához.  

A bővítések létrehozásához vagy módosításához Közreműködő vagy Rendszergazdai engedélyekkel kell rendelkeznie. További tudnivalók: [Engedélyek](permissions.md).

A **felderítés** lapon a következő bővítések találhatók:

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

[!INCLUDE[footer-include](../includes/footer-banner.md)]
