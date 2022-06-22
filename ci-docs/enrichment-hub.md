---
title: Az egyesített ügyfélprofilok bővítése
description: A funkciók segítségével bővítheti az ügyféladatokat.
ms.date: 06/10/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: conceptual
author: jodahlMSFT
ms.author: jodahl
manager: shellyha
ms.custom: intro-internal
searchScope:
- ci-enrichments
- ci-enrichment-details
- ci-enrichment-wizard
- customerInsights
ms.openlocfilehash: 3bbe8b829a6698da55d84709dbab6c36aa76792a
ms.sourcegitcommit: 27c5473eecd851263e60b2b6c96f6c0a99d68acb
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/13/2022
ms.locfileid: "8954044"
---
# <a name="enrichment-for-customer-profiles-preview"></a>Az ügyfelek profiljainak bővítése (előzetes verzió)

Adatok felhasználása olyan forrásokból, mint például a Microsoft és más partnerek az ügyféladatok bővítése céljából.

:::image type="content" source="media/enrichment-hub-page.png" alt-text="A bővítési központ oldala.":::

Lépjen az **Adatgazdagítás** > **elemre** a gazdagítási lehetőségek kezeléséhez.  

A bővítések létrehozásához vagy módosításához Közreműködő vagy Rendszergazdai engedélyekkel kell rendelkeznie. További tudnivalók: [Engedélyek](permissions.md).

A **Felfedezés** lapon található az összes támogatott gyarapítási lehetőség.

# <a name="individual-consumers-b-to-c"></a>[Egyéni fogyasztók (B-to-C)](#tab/b2c)

- [Az AbiliTec identitását](enrichment-liveramp.md) a LiveRamp AbiliTec biztosítja
- A Microsoft által biztosított [márkák](enrichment-microsoft.md)
- [Demográfiai adatok](enrichment-experian.md) az Experian által megadva
- A Microsoft által biztosított [továbbfejlesztett címek](enrichment-enhanced-addresses.md)
- A Microsoft által biztosított [érdeklődési körök](enrichment-microsoft.md)
- [helyadatok](enrichment-azure-maps.md) Maps biztosítja Microsoft Azure
- A [Helyadatokat](enrichment-here.md) a HERE Technologies biztosította
- [Egyéni SFTP-adatok](enrichment-SFTP-custom-import.md) a Secure File Transfer Protocol (SFTP) protokollon keresztül

# <a name="business-accounts-b-to-b"></a>[Üzleti számlák (B-to-B)](#tab/b2b)

- [A Microsoft által biztosított fiókkapcsolati adatok](enrichment-office.md)
- [A cég adatait](enrichment-dnb.md) a Dun & Bradstreet bocsátotta rendelkezésre
- A Leadspace által biztosított [vállalati adatok](enrichment-leadspace.md)
- A Microsoft által biztosított [továbbfejlesztett címek](enrichment-enhanced-addresses.md)
- [A Microsoft által biztosított továbbfejlesztett vállalati adatok](enrichment-enhanced-company-data.md)
- [helyadatok](enrichment-azure-maps.md) Maps biztosítja Microsoft Azure
- A [Helyadatokat](enrichment-here.md) a HERE Technologies biztosította
- [Egyéni SFTP-adatok](enrichment-SFTP-custom-import.md) a Secure File Transfer Protocol (SFTP) protokollon keresztül

---

A **saját bővítések** lapon megtekintheti, hogy milyen bővítés van beállítva, illetve hogy szerkesztheti-e a tulajdonságait. A gazdagításokból szegmenseket [vagy](segments.md) mértékeket [is létrehozhat](measures.md).

## <a name="manage-existing-enrichments"></a>Meglévő bővítések kezelése

Menjen a **Saját bővítéseim** fülre az összes konfigurált bővítés megtekintéséhez. Minden bővítés egy sor formájában jelenik meg, amely további információkat tartalmaz a bővítésről.

Az elérhető lehetőségekért válassza ki a bővítést. A beállítások megtekintéséhez kiválaszthatja a függőleges három pontot (&vellip;) egy listaelemen. Ha több bővítést is konfigurált, a keresőmező segítségével gyorsan megkeresheti.

:::image type="content" source="media/enrichment-hub-options-run.png" alt-text="A bővítések listájában a bővítés kezelésére szolgáló lehetőségek.":::

- **Nézet** a bővítés részleteinek megtekintése a bővített ügyfelek profiljainak számával.
- **Szerkesztheti** bővítés konfigurációját.
- A bővítés **Futtatásával** frissítheti az ügyfelek profiljait a legfrissebb adatokkal.
- **Inaktiválhat** egy meglévő bővítést, hogy leállítsa annak automatikus frissítését az egyes ütemezett frissítések során. Az utolsó sikeres frissítésből származó adatok továbbra is elérhetők lesznek. **Aktiválhat** egy inaktív bővítést az automatikus frissítés újraindításához minden ütemezett frissítéshez.
- A bővítés **Törlése**.

A listában való kijelölésvel egyszerre futtathat vagy inaktiválhat több bővítést. A megtekintése és szerkesztés lehetőségek nem érhetők el tömeges műveletként. Egyszerre csak egy bővítéssel működnek.

## <a name="enrichments-and-connections"></a>Bővítések és kapcsolatok

A külső gyártótól származó bővítéseket a [kapcsolatok](connections.md) használatával konfigurálhatja, amelyekhez a rendszergazda hitelesítő adatokat állít be, és hozzájárul az adatok átviteléhez. A kapcsolatotokat a rendszergazdák és közreműködők is használhatják bővítmények beállítására.  

## <a name="multiple-enrichments-of-the-same-type"></a>Azonos típusú többszörös bővítések

A bővíteni kívánt entitást a bővítési konfiguráció során adja meg, ezzel lehetővé teszi, hogy csak a profilok egy részében bővítsen. Például csak egy adott szegmens adatait bővítse. Konfigurálhat több ugyanolyan típusú bővítést, és újra felhasználhatja ugyanazt a kapcsolatot. Egyes bővítések az azonos típusú, létrehozható bővítések számára vonatkoznak korlátozások. A korlátok és az aktuális használat a Gazdagítás **oldal Felfedezés** lapján **található egyes csempéken** láthatók.

## <a name="enrich-data-sources-before-unification"></a>Adatforrások gazdagítása az egyesítés előtt

Az adatok egyesítése előtt gazdagíthatja az ügyféladatokat, hogy javítsa az adategyezés minőségét. További információ: [adatforrás gazdagítás](data-sources-enrichment.md).

## <a name="run-or-refresh-enrichments"></a>Bővítések futtatása vagy frissítése

1. A gazdagítási folyamat elindításához válassza a Futtatás **lehetőséget**. Vagy hagyja, hogy a rendszer automatikusan futtassa a gazdagítást egy [ütemezett frissítés](system.md#schedule-tab) részeként. A feldolgozási idő az ügyféladatok mennyiségétől függ.

1. Ha szükséges, [tekintse meg a gazdagítási folyamat](#see-the-progress-of-the-enrichment-process) előrehaladását.

1. A gazdagítási folyamat befejezése után a Saját bővítések **lapon** tekintse át az újonnan bővített ügyfélprofilok adatait, az utolsó frissítés időpontját és a bővített profilok számát.

1. Válassza ki a gazdagítást a gazdagítási eredmények [megtekintéséhez](#enrichment-results).

### <a name="see-the-progress-of-the-enrichment-process"></a>A gyarapítási folyamat előrehaladásának megtekintése

A gyarapítás feldolgozásáról részleteket, köztük az állapotot és a lehetséges problémákat megismerheti a frissítés közben vagy egy frissítés befejezése után. Megtudhatja, milyen folyamatok voltak érintettek egy bővítés frissítésében, és mennyi ideig tartott a folyamatok futtatása. A gyarapítási állapot támogatott az Experian, a Leadtér, a HERE Technologies, az SFTP Import és az Azure Maps esetében.

1. Lépjen az **Adatok** > **Bővítés** pontra.
1. **A Saját bővítések** lapon válassza ki a gazdagítás állapotát egy oldalsó panel megnyitásához.
1. A **Folyamat részletei** ablaktáblában bontsa ki az **Bővítések** szakaszt.
1. A bővítés során látni szeretné a haladást, válassza a **Részletek megtekintése** lehetőséget.
1. A **Feladat részletei** ablaktáblában válassza a **Részletek megjelenítése** lehetőséget, és tekintse meg a bővítésben érintett folyamatokat és az állapotukat.

## <a name="enrichment-results"></a>Bővítési eredmények

A befejezett gazdagítási futtatás után tekintse át a gazdagítási eredményeket.

1. Lépjen az **Adatok** > **Bővítés** pontra.
1. **A Saját bővítések** lapon válassza ki azt a gazdagítást, amelyről információt szeretne kapni.

Minden gazdagítás olyan alapvető információkat jelenít meg, mint a bővített profilok száma és a bővített profilok száma az idő múlásával. A **Bővített ügyfelek előzetes verzió** csempe a létrehozott gazdagítási entitás egy mintáját jeleníti meg. A részletes nézet megtekintéséhez válassza a Továbbiak **,** majd az **Adatok** lapot.

:::image type="content" source="media/enrichments-results.png" alt-text="A bővítések eredményoldala.":::

Ha rendelkezésre áll, a **mezőnként** gazdagított ügyfelek száma részletezést biztosít az egyes bővített mezők lefedettségében.

Egyes dúsítások a gazdagítás típusára jellemző információkat is megmutatják. További információt a kapcsolódó dokumentációban talál.

[!INCLUDE [footer-include](includes/footer-banner.md)]
