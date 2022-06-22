---
title: Vállalati profilok gazdagítása a Dun &Bradstreet-tel
description: Általános információk a Dun &Bradstreet harmadik féltől származó gazdagításáról.
ms.date: 06/10/2022
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: jodahlMSFT
ms.author: jodahl
manager: shellyha
ms.openlocfilehash: b1038970b6aee3bbdd7f79cc457f79aaf1c38222
ms.sourcegitcommit: 27c5473eecd851263e60b2b6c96f6c0a99d68acb
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/13/2022
ms.locfileid: "8953894"
---
# <a name="enrichment-of-company-profiles-with-dun--bradstreet-preview"></a>Vállalati profilok gazdagítása a Dun & Bradstreettel (előzetes verzió)

A Dun & Bradstreet kereskedelmi adatokat, elemzéseket és betekintést nyújt a vállalkozások számára. Lehetővé teszi, hogy az ügyfelek az egyesített ügyfélprofilokkal bővítsék az adataikat. A bővítések olyan attribútumokat tartalmaznak, mint a DUNS-szám, a vállalat mérete, a hely, az ipar és egyebek.

## <a name="prerequisites"></a>Előfeltételek

- Aktív [Dun & Bradstreet](https://www.dnb.com/marketing/media/give-your-data-a-boost.html?source=microsoft_audience_insights) licenc.
- [Egységes ügyfélprofilok](customer-profiles.md) vállalatok számára.
- Létrejön egy Dun & Bradstreet [projekt](#set-up-your-dun--bradstreet-project).
- A Dun & Bradstreet [kapcsolatot](connections.md) egy [rendszergazda konfigurálja](#configure-a-connection-for-dun--bradstreet).

## <a name="set-up-your-dun--bradstreet-project"></a>A Dun &Bradstreet projekt beállítása

A Dun & Bradstreet licencelt felhasználójaként létrehozhat egy projektet a Dun & Bradstreet [Connectben](https://connect.dnb.com?lead_source=microsoft_audienceinsights).

1. Jelentkezzen be a Dun & Bradstreet Connect [szolgáltatásba](https://connect.dnb.com?lead_source=microsoft_audienceinsights). A hitelesítő [adatok lekéréséhez állítsa vissza a jelszavát](https://sso.dnb.com/signin/forgot-password?lead_source=microsoft_audienceinsights).

1. Töltse le [csv-sablonfájlunkat](https://c360devenrichment.blob.core.windows.net/mapping/DnBCIdatamapping.csv), amely a Customer Insights mezőknek a megfelelő Dun &Bradstreet mezőkre való leképezéséhez lesz használva.

1. Töltse fel a fájlt a **Dun & Bradstreet projekt létrehozási élményének Adatok** feltöltése lépésében.

1. Válassza ki a vízszintes pontokat a megfelelő **forrás** alatt az újonnan létrehozott Dun & Bradstreet projektben az elérhető lehetőségek megtekintéséhez.

   :::image type="content" source="media/enrichment-dnb-dots.png" alt-text="Képernyőkép egy Dun &Bradstreet projekt pontjairól.":::

1. Válassza az S3-adatok **lekérése lehetőséget**. Tárolja ezeket az információkat biztonságos helyen. Szüksége lesz rá a kapcsolat beállításához [a Customer Insights gazdagításához](#configure-a-connection-for-dun--bradstreet).

   :::image type="content" source="media/enrichment-dnb-s3info.png" alt-text="Képernyőkép az s3 információk kiválasztásáról egy Dun & Bradstreet projektben.":::

## <a name="configure-a-connection-for-dun--bradstreet"></a>Kapcsolat konfigurálása Dun &Bradstreethez

Rendszergazdának [kell](permissions.md#admin) lennie a Customer Insights szolgáltatásban, és rendelkeznie kell a Dun &Bradstreet Connect hitelesítő adataival.

1. Válassza a Kapcsolat **hozzáadása lehetőséget** a gazdagítás konfigurálásakor, vagy lépjen a Rendszergazdai **kapcsolatok** > **elemre**, és válassza a Beállítás **lehetőséget** a Dun & Bradstreet csempén.

1. Adja meg a kapcsolat nevét.

1. Adja meg a Dun & Bradstreet érvényes hitelesítő adatait és a Dun & Bradstreet projekt részleteit *Régió, a Mappa eldobása elérési útja és a Mappa eldobása név*. Ezt [az információt](#set-up-your-dun--bradstreet-project) a Dun & Bradstreet projektből kapja.

1. Tekintse át és adja meg hozzájárulását az [adatvédelem és a megfelelőséghez](#data-privacy-and-compliance) az **Elfogadom** által.

1. Válassza az Ellenőrzés **lehetőséget** a konfiguráció ellenőrzéséhez, majd válassza a Mentés **lehetőséget**.

   :::image type="content" source="media/enrichment-dnb-connection.png" alt-text="Dun &Bradstreet kapcsolat konfigurációs oldala.":::

### <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség

Ha engedélyezi Dynamics 365 Customer Insights az adatok Dun &Bradstreet részére történő továbbítását, engedélyezi az adatok továbbítását a megfelelőségi határon túlra Dynamics 365 Customer Insights, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat is. A Microsoft az Ön utasítására továbbítja ezeket az adatokat, de Ön felelős annak biztosításáért, hogy a Dun &Bradstreet teljesítse az Ön esetleges adatvédelmi vagy biztonsági kötelezettségeit. További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).
A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt a bővítést.

## <a name="supported-countries-or-regions"></a>Támogatott országok és régiók

Jelenleg a következő ország-/régióbeállításokat támogatjuk: Kanada (angol) vagy Egyesült Államok (angol).

## <a name="configure-the-enrichment"></a>Bővítés konfigurálása

1. Menjen a z **Adatok** > **Bővítés** menübe, és válassza a **Felfedezés** lapot.

1. Válassza az Adatok **gazdagítása lehetőséget** a **Dun &Bradstreet vállalati adatai** csempén.

   :::image type="content" source="media/enrichment-dnb-tile.png" alt-text="Képernyőkép a Dun &Bradstreet csempéről.":::

1. Tekintse át az áttekintést, majd válassza a Tovább **lehetőséget**.

1. Válassza ki a kapcsolatot, és erősítse meg. Forduljon egy rendszergazdához, ha az egyik nem érhető el.

1. Válassza a **Következő** lehetőséget.

1. Válassza ki az **Ügyfél adatkészlet**, és válassza ki azt a profilt vagy szegmenst, amelyet a Dun &Bradstreet vállalati adataival szeretne gazdagítani. Az *Ügyfél* entitás gazdagítja az összes ügyfélprofilt, míg egy szegmens csak az adott szegmensben található ügyfélprofilokat gazdagítja.

1. Határozza meg, hogy az egyesített profilokból mely típusú mezőket használja a Dun & Bradstreet vállalati adatainak egyeztetéséhez. Legalább egy mezőben meg kell adni a **Név és cím**, a **Telefon** vagy az **E-mail-cím** adatokat.

1. Válassza a **Tovább** lehetőséget

1. Térképezze fel a mezőket a Dun &Bradstreet vállalati adataira. A **DUNS-szám** vagy **a Vállalat** neve és **az Ország** mezők kitöltése kötelező.

      :::image type="content" source="media/enrichment-dnb-mapping.png" alt-text="Dun & Bradstreet mezőleképezési panel.":::

1. A mező leképezésének befejezéséhez válassza a **Következő** lehetőséget.

1. **Adja meg a gazdagítás nevét** és a **Kimeneti entitás nevét**.

1. Válassza a **Bővítés mentése** lehetőséget, miután áttekintette a lehetőségeit.

1. Válassza a Futtatás **lehetőséget** a gazdagítási folyamat elindításához, vagy a közel lehetőséget a **Bővítések** lapra való visszatéréshez.

## <a name="enrichment-results"></a>Bővítési eredmények

[!INCLUDE [enrichment-results](includes/enrichment-results.md)]

## <a name="next-steps"></a>További lépések

[!INCLUDE [next-steps-enrichment](includes/next-steps-enrichment.md)]

[!INCLUDE[footer-include](includes/footer-banner.md)]
