---
title: Ügyfélprofilok gazdagítása helyadatok Azure Maps (előzetes verzió)
description: Az Azure Maps független gyártótól származó bővítésre vonatkozó általános információk.
ms.date: 08/08/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: jodahlMSFT
ms.author: jodahl
manager: shellyha
ms.openlocfilehash: f14b4fc20a9a1d8842f42f9e0e656b3d8dcddcf4
ms.sourcegitcommit: b1d06fe26934f12f0c5ed13e8ef1d37e52e67cc7
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/08/2022
ms.locfileid: "9238045"
---
# <a name="enrich-customer-profiles-with-location-data-from-azure-maps-preview"></a>Ügyfélprofilok gazdagítása helyadatok Azure Maps (előzetes verzió)

Azure Maps helyközpontú adatokat és szolgáltatásokat biztosít, hogy térinformatikai adatokon alapuló élményeket biztosítson beépített helyalapú intelligenciával. Az Azure Maps adatbővítő szolgáltatásai javítják az ügyfelekre vonatkozó helyinformációk pontosságát. Olyan lehetőségeket biztosít, mint például a címek normalizálása, a földrajzi szélesség és hosszúság kinyerése a Dynamics 365 Customer Insights alkalmazásba.

## <a name="prerequisites"></a>Előfeltételek

- Aktív Azure Maps-előfizetés. Előfizetés megszerzéséhez regisztráljon vagy [ingyenes próbaverziót kapjon](https://azure.microsoft.com/services/azure-maps/).

- A Azure Maps [kapcsolatot](connections.md)[egy rendszergazda konfigurálja](#configure-the-connection-for-azure-maps).

## <a name="configure-the-connection-for-azure-maps"></a>A kapcsolat konfigurálása az Azure Mapshoz

Rendszergazdának [kell](permissions.md#admin) lennie a Customer Insights szolgáltatásban, és aktív Azure Maps API-kulccsal kell rendelkeznie.

1. Válassza a **Kapcsolat hozzáadása** lehetőséget, amikor bővítményt konfigurál vagy menjen a **Rendszergazda** > **Kapcsolatok** elemre, és válassza a **Beállítás** lehetőséget az Azure Maps csempén.

   :::image type="content" source="media/enrichment-azure-maps-connection.png" alt-text="Azure Maps-kapcsolat konfigurációs oldal.":::

1. Adja meg a kapcsolat nevét és egy érvényes Azure Maps API-kulcsot.

1. Tekintse át az adatvédelmet és a megfelelőséget, és válassza az [Elfogadom lehetőséget](connections.md#data-privacy-and-compliance)**.**

1. Válassza az Ellenőrzés **lehetőséget** a konfiguráció ellenőrzéséhez, majd válassza a Mentés **lehetőséget**.

## <a name="configure-the-enrichment"></a>Bővítés konfigurálása

1. Menjen a z **Adatok** > **Bővítés** menübe, és válassza a **Felfedezés** lapot.

1. Válassza az Adatok gazdagítása lehetőséget **a Hely** a **Térképekből** csempén.Microsoft Azure

   :::image type="content" source="media/azure-maps-tile.png" alt-text="Azure Maps csempe":::

1. Tekintse át az áttekintést, majd válassza a Tovább **lehetőséget**.

1. Válassza ki a kapcsolatot. Ha nem érhető el egy kapcsolat sem, akkor forduljon a rendszergazdához.

1. Válassza a **Következő** lehetőséget.

1. Válassza ki az **Ügyfél adatkészlet**, és válassza ki azt a profilt vagy szegmenst, amelyet a Microsofttól származó adatokkal szeretne gazdagítani. Az *Ügyfél* entitás gazdagítja az összes ügyfélprofilt, míg egy szegmens csak az adott szegmensben található ügyfélprofilokat gazdagítja.

1. Határozza meg, hogy az egyesített profilokból mely típusú mezőket használja az egyeztetéshez: az elsődleges és/vagy másodlagos címet. Mezőleképezést is megadhat a címekhez, és külön bővítheti a címekhez kapcsolódó profilokat. Például egy otthoni címhez és egy vállalkozás címéhez. Válassza a **Következő** lehetőséget.

1. Leképezheti a mezőket a helyadatok a Azure Maps. A kiválasztott elsődleges és/vagy másodlagos címhez az **Utca 1.** és az **Irányítószám** mező megadása kötelező. A nagyobb egyezési pontosság érdekében adjon hozzá további mezőket.

   :::image type="content" source="media/enrichment-azure-maps-attributes.png" alt-text="Azure Maps attribútumleképezés.":::

1. A mező leképezésének befejezéséhez válassza a **Következő** lehetőséget.

1. Tekintse át **a Speciális beállításokat**, amelyek maximális rugalmasságot biztosítanak a speciális használati esetek kezeléséhez. A következő alapértelmezett értékeket azonban általában nem kell módosítani.

   - **Címek** típusa: A legjobb címegyezés akkor is visszatér, ha hiányos. Ha például csak a teljes címeket szeretne kapni &mdash; tehát házszámot is tartalma címeket &mdash; törölje az összes jelölőnégyzet jelölését a **Pontcímek** kivételével.
   - **Nyelv**: A címek a címterület alapján a nyelven adnak vissza. Ha egységesített címnyelvet kell használnia, válassza ki a nyelvet a legördülő menüből. Ha például az angolt **választja**, az visszaadja **Koppenhágát, Dániát** a Dániel, **A Danmark** helyett.
   - **Az eredmények** maximális száma: Az eredmények száma címenként.

1. Válassza a **Következő** lehetőséget.

1. **Adja meg a gazdagítás nevét** és a **Kimeneti entitás nevét**.

1. Válassza a **Bővítés mentése** lehetőséget, miután áttekintette a lehetőségeit.

1. Válassza a Futtatás **lehetőséget** a gazdagítási folyamat elindításához, vagy a közel lehetőséget a **Bővítések** lapra való visszatéréshez.

## <a name="view-enrichment-results"></a>Gazdagítási eredmények megtekintése

[!INCLUDE [enrichment-results](includes/enrichment-results.md)]

A **mező** által gazdagított ügyfelek száma részletezést biztosít az egyes bővített mezők lefedettségében.

## <a name="next-steps"></a>További lépések

[!INCLUDE [next-steps-enrichment](includes/next-steps-enrichment.md)]

[!INCLUDE [footer-include](includes/footer-banner.md)]
