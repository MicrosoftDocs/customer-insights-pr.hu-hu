---
title: Bővítse az ügyfélprofilokat a HERE Technologies segítségével (előzetes verzió)
description: Általános információk a HERE Technologies harmadik fél bővítésről.
ms.date: 06/10/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: jodahlMSFT
ms.author: jodahl
manager: shellyha
ms.openlocfilehash: d88085b6be156dd1c895e9e5b38cc9d77acbdb95
ms.sourcegitcommit: a97d31a647a5d259140a1baaeef8c6ea10b8cbde
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/29/2022
ms.locfileid: "9052054"
---
# <a name="enrich-customer-profiles-with-here-technologies-preview"></a>Bővítse az ügyfélprofilokat a HERE Technologies segítségével (előzetes verzió)

A HERE Technologies egy helyplatformot biztosító vállalat, amely helyalapú adatokat és szolgáltatásokat nyújt. A HERE Technologies adatgazdagítási szolgáltatásai javítják az ügyfelekkel kapcsolatos helyadatok pontosságát. Ez biztosítja a cím normalizálását, a szélességi és hosszúsági kinyerést és még sok mást.

## <a name="prerequisites"></a>Előfeltételek

- Aktív HERE Technologies előfizetés. Ha előfizetést szeretne kapni, regisztráljon itt [,](https://developer.here.com/sign-up?utm_medium=referral&utm_source=Microsoft-Dynamics-CI&create=Freemium-Basic) vagy [lépjen kapcsolatba közvetlenül a HERE Technologies céggel](https://developer.here.com/help?utm_medium=referral&utm_source=Microsoft-Dynamics-CI#how-can-we-help-you). [Itt többet is megtudhat a HERE Technologies helybővítéshez.](https://developer.here.com/location-enrichment?cid=Dev-MicrosoftDynamics-DB-0-Dev-&utm_source=MicrosoftDynamics&utm_medium=referral&utm_campaign=Online_Dev_ReferralMicrosoft)

- A HERE [kapcsolatot](connections.md) egy [rendszergazda konfigurálja](#configure-the-connection-for-here-technologies).

## <a name="configure-the-connection-for-here-technologies"></a>Konfigurálja a kapcsolatot a HERE Technologies-hoz

Rendszergazdának [kell](permissions.md#admin) lennie a Customer Insights szolgáltatásban, és rendelkeznie kell egy aktív HERE Technologies API-kulccsal.

1. Válassza a **Kapcsolat** hozzáadása lehetőséget a gazdagítás konfigurálásakor, vagy lépjen a Rendszergazdai **kapcsolatok** > **elemre**, és válassza a Beállítás **lehetőséget** a HERE Technológiák csempén.

1. Adja meg a kapcsolat nevét és egy érvényes HERE Technologies API-kulcsot.

1. Tekintse át és adja meg hozzájárulását az [adatvédelem és a megfelelőséghez](#data-privacy-and-compliance) az **Elfogadom** által.

1. Válassza az Ellenőrzés **lehetőséget** a konfiguráció ellenőrzéséhez, majd válassza a Mentés **lehetőséget**.

   :::image type="content" source="media/enrichment-HERE-connection.png" alt-text="A HERE Technologies kapcsolat konfigurációs oldala.":::

### <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség

Amikor engedélyezi a Dynamics 365 Customer Insights szolgáltatást az adatok HERE Technologies szolgáltatásba való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat. A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy a HERE Technologies megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek. További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).
A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt a bővítést.

## <a name="configure-the-enrichment"></a>Bővítés konfigurálása

1. Menjen a z **Adatok** > **Bővítés** menübe, és válassza a **Felfedezés** lapot.

1. Válassza az Adatok gazdagítása lehetőséget **a Hely** a **HERE Technológiák csempéről.**

   :::image type="content" source="media/HERE-tile.png" alt-text="HERE Technologies csempe.":::

1. Tekintse át az áttekintést, majd válassza a Tovább **lehetőséget**.

1. Válassza ki a kapcsolatot. Forduljon egy rendszergazdához, ha az egyik nem érhető el.

1. Válassza a **Következő** lehetőséget.

1. Válassza ki az **Ügyfél adatkészlet**, és válassza ki azt a profilt vagy szegmenst, amelyet a HERE Technologies adataival szeretne gazdagítani. Az *Ügyfél* entitás gazdagítja az összes ügyfélprofilt, míg egy szegmens csak az adott szegmensben található ügyfélprofilokat gazdagítja.

1. Határozza meg, hogy az egyesített profilokból mely típusú mezőket használja az egyeztetéshez: az elsődleges és/vagy másodlagos címet. Mezőleképezést is megadhat a címekhez, és külön bővítheti a címekhez kapcsolódó profilokat. Például egy otthoni címhez és egy vállalkozás címéhez. Válassza a **Következő** lehetőséget.

1. Térképezze fel a mezőket a HERE Technologies adataira. A kiválasztott elsődleges és/vagy másodlagos címhez az **Utca 1.** és az **Irányítószám** mező megadása kötelező. A nagyobb egyezési pontosság érdekében adjon hozzá további mezőket.

1. A mező leképezésének befejezéséhez válassza a **Következő** lehetőséget.

1. **Adja meg a gazdagítás nevét** és a **Kimeneti entitás nevét**.

1. Válassza a **Bővítés mentése** lehetőséget, miután áttekintette a lehetőségeit.

1. Válassza a Futtatás **lehetőséget** a gazdagítási folyamat elindításához, vagy a közel lehetőséget a **Bővítések** lapra való visszatéréshez.

## <a name="view-enrichment-results"></a>Gazdagítási eredmények megtekintése

[!INCLUDE [enrichment-results](includes/enrichment-results.md)]

A **mező** által gazdagított ügyfelek száma részletezést biztosít az egyes bővített mezők lefedettségében.

## <a name="next-steps"></a>További lépések

[!INCLUDE [next-steps-enrichment](includes/next-steps-enrichment.md)]

[!INCLUDE [footer-include](includes/footer-banner.md)]
