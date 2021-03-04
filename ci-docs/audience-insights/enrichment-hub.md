---
title: Az egyesített ügyfélprofilok bővítése
description: A funkciók segítségével bővítheti az ügyféladatokat.
ms.date: 11/02/2020
ms.reviewer: kishorem
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: 6b73aa93ec1a98f2b8d20d02e88bc6304f887078
ms.sourcegitcommit: 139548f8a2d0f24d54c4a6c404a743eeeb8ef8e0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/15/2021
ms.locfileid: "5269471"
---
# <a name="enrichment-for-customer-profiles-preview"></a>Az ügyfelek profiljainak bővítése (előzetes verzió)

Adatok felhasználása olyan forrásokból, mint például a Microsoft és más partnerek az ügyféladatok bővítése céljából.

:::image type="content" source="media/enrichment-hub-page.png" alt-text="A bővítési központ oldala":::

A célközönség-információkban lépjen az **Adatok** > **Bővítés** pontra a bővítési lehetőségek használatához.    
A bővítések létrehozásához vagy módosításához Közreműködő vagy Rendszergazdai engedélyekkel kell rendelkeznie. További tudnivalók: [Engedélyek](permissions.md).

A **felderítés** lapon a következő bővítések találhatók:

- [Márkák](enrichment-microsoft-graph.md) a Microsoft Graph által biztosítva.
- [Érdeklődési körök](enrichment-microsoft-graph.md) a Microsoft Graph által biztosítva.
- A Leadspace által biztosított [vállalati adatok](enrichment-leadspace.md)
- [Demográfia](enrichment-experian.md) az Experiantól
- A [Helyadatokat](enrichment-here.md) a HERE Technologies biztosította
- [Egyéni adatok](enrichment-SFTP-custom-import.md) SFTP-importálás biztonságos fájlátviteli protokollján keresztül

A **saját bővítések** lapon megtekintheti, hogy milyen bővítés van beállítva, illetve hogy szerkesztheti-e a tulajdonságait.

## <a name="manage-existing-enrichments"></a>Meglévő bővítések kezelése

Nyissa meg a **Saját bővítések** lehetőséget az összes konfigurált bővítés megtekintéséhez. Minden bővítés egy sor formájában jelenik meg, amely további információkat tartalmaz a bővítésről.

A rendelkezésre álló lehetőségek megtekintéséhez válasszon egy bővítést. Másik lehetőségként kiválaszthatja a három pont (…) elemet egy listaelemnél a lehetőségek megtekintéséhez.

:::image type="content" source="media/enrichment-hub-options-run.png" alt-text="A bővítések listájában a bővítés kezelésére szolgáló lehetőségek":::

- **Nézet** a bővítés részleteinek megtekintése a bővített ügyfelek profiljainak számával.
- **Szerkesztheti** bővítés konfigurációját.
- A bővítés **Futtatásával** frissítheti az ügyfelek profiljait a legfrissebb adatokkal.
- **Inaktiválhat** egy meglévő bővítést, hogy leállítsa annak automatikus frissítését az egyes ütemezett frissítések során. Az utolsó sikeres frissítésből származó adatok továbbra is elérhetők lesznek. **Aktiválhat** egy inaktív bővítést az automatikus frissítés újraindításához minden ütemezett frissítéshez.
- Egy bővítés **törlése**.

Egyszerre több bővítést is futtathat vagy inaktiválhat, ha kijelöli azokat a listából. A beállítások megtekintése és szerkesztése nem érhető el tömeges műveletként, és egyszerre csak egy bővítéshez használható.


[!INCLUDE[footer-include](../includes/footer-banner.md)]