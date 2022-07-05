---
title: Bővítse az ügyfélprofilokat a LiveRamp identitásadataival (előzetes verzió)
description: Bővítse az ügyfélprofilokat LiveRamp-adatokkal.
ms.date: 06/10/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: kishorem-ms
ms.author: kishorem
manager: shellyha
ms.openlocfilehash: 334440493c50448005ec90d0cfac11358d677b73
ms.sourcegitcommit: dca46afb9e23ba87a0ff59a1776c1d139e209a32
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/29/2022
ms.locfileid: "9082197"
---
# <a name="enrich-customer-profiles-with-identity-data-from-liveramp-preview"></a>Bővítse az ügyfélprofilokat a LiveRamp identitásadataival (előzetes verzió)

A LiveRamp determinisztikus offline identitásfeloldást és az ügyféladatok összevonását biztosítja. Az ügyféladatokban szereplő személyes azonosítókat leképezheti az AbiliTec identitásgráfra, és AbiliTec-azonosítókat kaphat. Ezután ezekkel az azonosítókkal jobban egyesítheti az ügyféladatokat.

## <a name="supported-countriesregions"></a>Támogatott országok/régiók

Jelenleg csak az Egyesült Államokban támogatjuk az ügyfélprofilok LiveRamp-adatokkal való gazdagítását.

## <a name="prerequisites"></a>Előfeltételek

- Aktív LiveRamp-előfizetés. Előfizetés megszerzéséhez vegye fel a kapcsolatot a LiveRamp-fiók csapatával, vagy [dynamics@liveramp.com](mailto:dynamics@liveramp.com) további információkért.

- Aktív AbiliTec-előfizetés ügyfél-azonosítóval és titkos kóddal az API eléréséhez. További információ: [AbiliTec API Fejlesztői központ](https://developers.liveramp.com/abilitec-api/).

- A LiveRamp-kapcsolatot [...](connections.md)[egy rendszergazda konfigurálja](#configure-the-connection-for-liveramp).

## <a name="configure-the-connection-for-liveramp"></a>A liveRamp-kapcsolat konfigurálása

Rendszergazdának [kell](permissions.md#admin) lennie a Customer Insights szolgáltatásban, és rendelkeznie kell aktív LiveRamp-ügyfél-azonosítóval és titkos kóddal.

1. Válassza a Kapcsolat **hozzáadása lehetőséget** a gazdagítás konfigurálásakor, vagy lépjen a **Rendszergazdai** > **kapcsolatok elemre**, és válassza a Beállítás **lehetőséget** a LiveRamp csempén.

   :::image type="content" source="media/liveramp-connection.png" alt-text="Konfigurációs panel a LiveRamp AbiliTec szolgáltatással való kapcsolat beállításához.":::

1. Adja meg a kapcsolat nevét, valamint egy érvényes LiveRamp-ügyfél-azonosítót és egy titkos kulcsot.

1. Tekintse át és adja meg hozzájárulását az [adatvédelem és a megfelelőséghez](#data-privacy-and-compliance) az **Elfogadom** által.

1. Válassza az Ellenőrzés **lehetőséget** a konfiguráció ellenőrzéséhez, majd válassza a Mentés **lehetőséget**.

### <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség

Ha engedélyezi Dynamics 365 Customer Insights az adatok továbbítását a LiveRamp-nek, akkor engedélyezi az adatok továbbítását a megfelelőségi határon kívülre Dynamics 365 Customer Insights, beleértve a potenciálisan bizalmas adatokat, például a személyes adatokat is. A Microsoft az Ön utasításainak megfelelően továbbítja ezeket az adatokat, de Ön felelős azért, hogy a LiveRamp megfeleljen az Ön esetleges adatvédelmi vagy biztonsági kötelezettségeinek. További információért tekintse át a [Microsoft adatvédelmi nyilatkozatát](https://go.microsoft.com/fwlink/?linkid=396732). A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt a bővítést.

## <a name="configure-the-enrichment"></a>Bővítés konfigurálása

1. Menjen a z **Adatok** > **Bővítés** menübe, és válassza a **Felfedezés** lapot.

1. Válassza az Adatok gazdagítása lehetőséget **az Identitás** a **LiveRamp csempéről csempén.**

   :::image type="content" source="media/liveramp-tile.png" alt-text="Identitás csempe a gazdagítás áttekintési oldalán.":::

1. Tekintse át az áttekintést, majd válassza a Tovább **lehetőséget**.

1. Válassza ki a kapcsolatot. Forduljon egy rendszergazdához, ha az egyik nem érhető el.

1. Válassza a **Következő** lehetőséget.

1. Válassza ki az **Ügyfél adatkészlet**, és válassza ki azt a profilt vagy szegmenst, amelyet identitásadatokkal szeretne gazdagítani a LiveRampből. Az *Ügyfél* entitás gazdagítja az összes ügyfélprofilt, míg egy szegmens csak az adott szegmensben található ügyfélprofilokat gazdagítja.

1. Határozza meg, hogy az egyesített profilokból mely típusú mezőket használja a LiveRamp identitásadatainak egyeztetéséhez. A Név és cím **,** E-mail **vagy** Telefon **mezők** közül legalább egy kötelező. A nagyobb egyezési pontosság érdekében adjon hozzá más mezőket. Válassza a **Következő** lehetőséget.

1. Leképezheti a mezőket a LiveRamp azonosító adataira.

   :::image type="content" source="media/liveramp-data-mapping.png" alt-text="Adatleképezési lehetőségek a LiveRamp gazdagításához.":::

1. A mező leképezésének befejezéséhez válassza a **Következő** lehetőséget.

1. **Adja meg a gazdagítás nevét** és a **Kimeneti entitás nevét**.

1. Válassza a **Bővítés mentése** lehetőséget, miután áttekintette a lehetőségeit.

1. Válassza a Futtatás **lehetőséget** a gazdagítási folyamat elindításához, vagy a közel lehetőséget a **Bővítések** lapra való visszatéréshez.

## <a name="view-enrichment-results"></a>Gazdagítási eredmények megtekintése

[!INCLUDE [enrichment-results](includes/enrichment-results.md)]

A **mező** által gazdagított ügyfelek száma részletezést biztosít az egyes bővített mezők lefedettségében.

## <a name="next-steps"></a>További lépések

Építsen a bővített ügyféladatokra. Az AbiliTec azonosítók segítségével egyesítheti az ügyfélprofilokat egy személyalapú nézetbe.
[!INCLUDE [next-steps-enrichment](includes/next-steps-enrichment.md)]

[!INCLUDE [footer-include](includes/footer-banner.md)]
