---
title: Ügyfélprofilok gyarapítása az Azure Maps szolgáltatásból származó helyadatokkal
description: Az Azure Maps független gyártótól származó bővítésre vonatkozó általános információk.
ms.date: 08/31/2021
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: jodahlMSFT
ms.author: jodahl
manager: shellyha
ms.openlocfilehash: cb1c0778a398ef6d338ce6cf9e199eae0c344a5c
ms.sourcegitcommit: e7cdf36a78a2b1dd2850183224d39c8dde46b26f
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/16/2022
ms.locfileid: "8226452"
---
# <a name="enrichment-of-customer-profiles-with-azure-maps-preview"></a>Ügyfélprofilok bővítése az Azure Maps segítségével (előzetes verzió)

Az Azure Maps helycentrikus adatokat és szolgáltatásokat biztosít, hogy a beépített helyintelligencia segítségével földrajzi adatokon alapuló élményeket nyújtsunk. Az Azure Maps adatbővítő szolgáltatásai javítják az ügyfelekre vonatkozó helyinformációk pontosságát. Olyan lehetőségeket biztosít, mint például a címek normalizálása, a földrajzi szélesség és hosszúság kinyerése a Dynamics 365 Customer Insights alkalmazásba.

## <a name="prerequisites"></a>Előfeltételek

Az Azure Maps adatbővítésének konfigurálása érdekében teljesülnie kell a következő előfeltételeknek:

- Aktív Azure Maps előfizetéssel kell rendelkeznie. Az előfizetéshez [regisztrálhat, illetve próba-előfizetést is kaphat](https://azure.microsoft.com/services/azure-maps/).

- Az Azure Maps [kapcsolat](connections.md) elérhető, *vagy* rendelkezik [rendszergazdai](permissions.md#administrator) engedélyekkel és egy aktív Azure Maps API-kulcssal.

## <a name="configure-the-enrichment"></a>Bővítés konfigurálása

1. Lépjen az **Adatok** > **Bővítés** pontra. 

1. A **Hely** csempén válassza **Az adataim bővítése** lehetőséget.

   :::image type="content" source="media/azure-maps-tile.png" alt-text="Azure Maps csempe":::

1. Válasszon egy [kapcsolatot](connections.md) a legördülő listából. Ha az Azure Maps nem érhető el, forduljon a rendszergazdához. Rendszergazdaként konfigurálhatja az [Azure Maps kapcsolatát](#configure-the-connection-for-azure-maps). 

1. A kijelölés megerősítéséhez válassza a **Tovább** lehetőséget.

1. Válassza ki az Azure Maps helyadataival bővíteni kívánt **Ügyféladatkészletet**. Kiválaszthatja az **Ügyfél** entitást, hogy az összes egyesített ügyfélprofilt bővítse, vagy kiválaszthat egy szegmens entitást, amely csak az adott szegmensben található ügyfélprofilokat bővítse.

    :::image type="content" source="media/enrichment-azure-maps-configuration-customer-data-set.png" alt-text="Képernyőkép az ügyféladatkészlet kiválasztásakor.":::

1. Válassza ki, hogy a mezőket elsődleges és/vagy másodlagos címre szeretné-e leképezni. Mezőleképezést is megadhat a címekhez, és mindkét cím esetében külön-külön bővítheti a profilokat &mdash; például egy otthoni és egy munkahelyi cím esetében. Válassza a **Következő** lehetőséget.

1. Határozza meg, hogy melyik mezőket kell használni az egyesített profiljaiból az egyező helyadatok kereséséhez az Azure Mapsből. A kijelölt elsődleges vagy másodlagos címhez az **Utca 1** és a **Irányítószám** mező szükséges. A nagyobb egyezési pontosság érdekében további mezőket adhat hozzá.

   :::image type="content" source="media/enrichment-azure-maps-configuration.png" alt-text="Azure Maps bővítés konfigurációs oldal.":::

1. A mező leképezésének befejezéséhez válassza a **Következő** lehetőséget.

1. Döntse el, hogy módosítani szeretné-e a **Speciális beállításokat**. Ezek maximális rugalmasságot biztosítanak a speciális esetek kezeléshez, de a legtöbb esetben az alapértelmezett értékek megfelelőek lesznek:
   - **Címek típusa**: Az alapértelmezett viselkedés az, hogy a gyarapítás akkor is a legjobb címet adja vissza, ha nem teljes. Ha például csak a teljes címeket szeretne kapni &mdash; tehát házszámot is tartalma címeket &mdash; törölje az összes jelölőnégyzet jelölését a **Pontcímek** kivételével. 
   - **Nyelv**: A rendszer alapértelmezés szerint annak a régiónak a nyelvén ad eredményül címeket, amelyhez a cím hozzá van tartozik. Ha egységesített címnyelvet kell használnia, válassza ki a nyelvet a legördülő menüből. Ha például az **angolt** választja, a **Copenhagen, Denmark** érték lesz visszaküldve a **København, Danmark** helyett.

1. Adjon nevet a bővítésnek.

1. Ellenőrizze a választások, majd válassza a **Bővítés mentése** parancsot.

## <a name="configure-the-connection-for-azure-maps"></a>A kapcsolat konfigurálása az Azure Mapshoz

A kapcsolatok konfigurálásához célközönség kapcsolatos információk rendszergazdájának kell lennie. Válassza a **Kapcsolat hozzáadása** lehetőséget, amikor bővítményt konfigurál vagy menjen a **Rendszergazda** > **Kapcsolatok** elemre, és válassza a **Beállítás** lehetőséget az Azure Maps csempén.

1. A **Megjelenítendő név** mezőben adja meg a kapcsolat nevét.

1. Adjon meg egy érvényes Azure Maps API-kulcsot.

1. Ellenőrizze és adja meg az **adatvédelemre és a megfelelőségre** vonatkozó beleegyezését az **Elfogadom** jelölőnégyzet bejelölésével

1. A konfiguráció megerősítéséhez válassza az **Ellenőrzés** lehetőséget.

1. Az ellenőrzés befejezése után válassza a **Mentés** lehetőséget.

:::image type="content" source="media/enrichment-azure-maps-connection.png" alt-text="Azure Maps-kapcsolat konfigurációs oldal.":::

## <a name="enrichment-results"></a>Bővítési eredmények

A bővítési folyamat megkezdéséhez válassza a **Futtatás** parancsot a parancssorból. Azt is engedélyezheti, hogy a rendszer a bővítést automatikusan egy [ütemezett frissítés](system.md#schedule-tab) részeként futtassa. A feldolgozási idő az ügyféladatok méretétől és az API-válaszidejétől függ.

A bővítési folyamat befejezése után áttekintheti az újonnan bővített ügyfélprofilok adatait a **Saját bővítések** alatt. Emellett megtalálhatja az utolsó frissítés időpontját és a bővített profilok számát is.

Az egyes bővített profilok részletes nézetét a **Bővített adatok megtekintése** lehetőségre kattintva érheti el.

## <a name="next-steps"></a>További lépések

[!INCLUDE [next-steps-enrichment](../includes/next-steps-enrichment.md)]

## <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség

Amikor engedélyezed a Dynamics 365 Customer Insights -nak, hogy továbbítsa az adatokat Azure Maps-be, engedélyezed az adatátvitelt a megfelelőséghatáron kívülre a Dynamics 365 Customer Insights -nak, beleértve az esetlegesen bizalmas adatokat, például személyes adatokat. A Microsoft az Ön utasítására továbbítja az ilyen adatokat, de Ön felelős annak biztosításáért, hogy az Azure Maps megfeleljen az esetleges adatvédelmi és biztonsági kötelezettségeknek. További tájékoztatásért menjen a [Microsoft adatvédelmi nyilatkozatára](https://go.microsoft.com/fwlink/?linkid=396732).
A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt a bővítést.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
