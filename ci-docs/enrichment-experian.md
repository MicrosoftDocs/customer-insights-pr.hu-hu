---
title: Ügyfélprofilok bővítése demográfiai adatokkal az Experian -ból (előzetes verzió)
description: A független gyártótól származó Experian bővítésre vonatkozó általános információk.
ms.date: 06/10/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: kishorem-ms
ms.author: kishorem
manager: shellyha
ms.openlocfilehash: 876853ab42e8c08ad1abacb8d8a205c0aadabcf7
ms.sourcegitcommit: 594081c82ca385f7143b3416378533aaf2d6d0d3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/27/2022
ms.locfileid: "9195939"
---
# <a name="enrich-customer-profiles-with-demographics-from-experian-preview"></a>Ügyfélprofilok bővítése demográfiai adatokkal az Experian -ból (előzetes verzió)

Az Experian a fogyasztói és üzleti hiteljelentési és marketingszolgáltatások globális vezetője. Az Experian adatbővítési szolgáltatások segítségével mélyebben megértheti ügyfeleit, az ügyfélprofilok bővítése által demográfiai adatokkal, mint például a háztartás nagysága, bevétel, stb.

## <a name="supported-countriesregions"></a>Támogatott országok/régiók

Jelenleg csak az Egyesült Államokban támogatjuk az ügyfélprofilok bővítését.

## <a name="prerequisites"></a>Előfeltételek

- Aktív Experian előfizetés. Az előfizetéshez közvetlenül [forduljon Experian](https://www.experian.com/marketing-services/contact) . [További információk Experian adatbővítésről](https://www.experian.com/marketing-services/microsoft?cmpid=ems_web_mci_cdppage).

- A Experian [kapcsolatot](connections.md) egy [rendszergazda konfigurálja](#configure-the-connection-for-experian).

- Experian Az Ön számára létrehozott SSH-kompatibilis Secure Transport (ST) fiók Experian felhasználói azonosítója, partiazonosítója és modellszáma.

## <a name="configure-the-connection-for-experian"></a>Kapcsolat konfigurálása Experian -hoz

Rendszergazdának [kell](permissions.md#admin) lennie a Customer Insights szolgáltatásban, és rendelkeznie Experian kell felhasználói azonosítóval, partiazonosítóval és modellszámmal.

1. Válassza a Kapcsolat **hozzáadása lehetőséget** a gazdagítás konfigurálásakor, vagy lépjen a Rendszergazdai **kapcsolatok** > **elemre**, és válassza a Beállítás **lehetőséget** a Experian csempén.

   :::image type="content" source="media/enrichment-Experian-connection.png" alt-text="Experian kapcsolati konfiguráció panel.":::

1. Adja meg a kapcsolat nevét, valamint a biztonságos átviteli fiók érvényes felhasználói azonosítóját, félazonosítóját és modellszámát Experian.

1. Tekintse át és adja meg hozzájárulását az [adatvédelem és a megfelelőséghez](#data-privacy-and-compliance) az **Elfogadom** által.

1. Válassza az Ellenőrzés **lehetőséget** a konfiguráció ellenőrzéséhez, majd válassza a Mentés **lehetőséget**.

### <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség

Amikor engedélyezed a Dynamics 365 Customer Insights -nak, hogy továbbítsa az adatokat Experian -ba, engedélyezed az adatátvitelt a megfelelőséghatáron kívülre a Dynamics 365 Customer Insights -nak, beleértve az esetlegesen bizalmas adatokat, például személyes adatokat. A Microsoft az Ön utasítására továbbítja az ilyen adatokat, de Ön felelős annak biztosításáért, hogy az Experian megfeleljen az esetleges adatvédelmi és biztonsági kötelezettségeknek. További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732). A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt a bővítést.

## <a name="configure-the-enrichment"></a>Bővítés konfigurálása

1. Menjen a z **Adatok** > **Bővítés** menübe, és válassza a **Felfedezés** lapot.

1. Válassza az Adatok **gazdagítása lehetőséget** a **Demográfiai adatok** csempén Experian.

   :::image type="content" source="media/experian-tile.png" alt-text="Experian csempét a gazdagodás áttekintése oldalon.":::

1. Tekintse át az áttekintést, majd válassza a Tovább **lehetőséget**.

1. Válassza ki a kapcsolatot. Ha nem érhető el egy kapcsolat sem, akkor forduljon a rendszergazdához.

1. Válassza a **Következő** lehetőséget.

1. Válassza ki az **Ügyfél adatkészlet**, és válassza ki azt a profilt vagy szegmenst, amelyből Experian demográfiai adatokkal szeretne gazdagítani. Az *Ügyfél* entitás gazdagítja az összes ügyfélprofilt, míg egy szegmens csak az adott szegmensben található ügyfélprofilokat gazdagítja.

    :::image type="content" source="media/enrichment-Experian-configuration-customer-data-set.png" alt-text="Képernyőkép az ügyféladatkészlet kiválasztásáról.":::

1. Határozza meg, hogy az egyesített profilokból mely típusú mezőket használja a demográfiai adatok Experian egyeztetéséhez. Legalább egy mezőben meg kell adni a **Név és cím**, a **Telefon** vagy az **E-mail-cím** adatokat. A nagyobb egyezési pontosság érdekében adjon hozzá más mezőket. Válassza a **Következő** lehetőséget.

1. A mezők hozzárendelése a demográfiai adatokhoz a következőből: Experian.

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
