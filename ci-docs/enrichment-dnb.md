---
title: A vállalati profilok gazdagítása a Dun & Bradstreet segítségével
description: Általános információk a Dun & Bradstreet harmadik fél gazdagodásáról.
ms.date: 04/26/2022
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: jodahlMSFT
ms.author: jodahl
manager: shellyha
ms.openlocfilehash: ecbbf2c94020bf395f4eb70a99a63cea335af2dd
ms.sourcegitcommit: cf74b8c20d88eb96e1ac86e18cd44fe27aad5ab9
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/28/2022
ms.locfileid: "8653783"
---
# <a name="enrichment-of-company-profiles-with-dun--bradstreet-preview"></a>Vállalati profilok gazdagítása a Dun & Bradstreet segítségével (előzetes verzió)

A Dun & Bradstreet kereskedelmi adatokat, elemzéseket és betekintést nyújt a vállalkozások számára. Lehetővé teszi, hogy az ügyfelek az egyesített ügyfélprofilokkal bővítsék az adataikat. A gazdagodás olyan attribútumokat tartalmaz, mint a DUNS-szám, a vállalat mérete, a hely, az ipar és így tovább.

## <a name="prerequisites"></a>Előfeltételek

A Dun & Bradstreet gazdagodás konfigurálásához a következő előfeltételeknek kell teljesülniük:

- Aktív [Dun & Bradstreet](https://www.dnb.com/marketing/media/give-your-data-a-boost.html?source=microsoft_audience_insights) engedéllyel rendelkezik.
- A vállalatokhoz [egyesített ügyfélprofilok](customer-profiles.md) tartoznak.
- A Dun & Bradstreet [kapcsolatot](connections.md) egy rendszergazda konfigurálja. Akkor hozhatja létre, ha rendszergazdai [engedélyekkel és a Dun & Bradstreet Connect hitelesítő adataival rendelkezik](permissions.md#admin). 

## <a name="setting-up-your-dun--bradstreet-project"></a>A Dun & Bradstreet projekt beállítása

A Dun & Bradstreet licencelt felhasználójaként a Dun & Bradstreet Connect programban [állíthat be egy projektet](https://connect.dnb.com?lead_source=microsoft_audienceinsights). 


1. Jelentkezzen be a [Dun & Bradstreet Connect szolgáltatásba](https://connect.dnb.com?lead_source=microsoft_audienceinsights). A hitelesítő [adatok lekéréséhez állítsa vissza a jelszót](https://sso.dnb.com/signin/forgot-password?lead_source=microsoft_audienceinsights).

1. Töltse le [csv sablonfájlunkat](https://c360devenrichment.blob.core.windows.net/mapping/DnBCIdatamapping.csv), amellyel a célközönség insights mezőket a megfelelő Dun & Bradstreet mezőkhöz rendeli. 

1. Töltse fel a fájlt a **Dun & Bradstreet projektkészítési élmény feltöltési lépésébe**. 

1. Válassza ki a vízszintes pontokat a megfelelő **forrás** alatt az újonnan létrehozott Dun & Bradstreet projektben a rendelkezésre álló lehetőségek megtekintéséhez.

   :::image type="content" source="media/enrichment-dnb-dots.png" alt-text="Képernyőkép a Dun & Bradstreet projekt pontjairól.":::

1. Válassza az S3 részleteinek lekérése **lehetőséget**. Tárolja ezeket az információkat biztonságos helyen. Szüksége lesz rá, hogy [beállítsa a kapcsolatot a gazdagodáshoz](#configure-a-connection-for-dun--bradstreet) célközönség betekintésben. 

   :::image type="content" source="media/enrichment-dnb-s3info.png" alt-text="Képernyőkép az s3 információk kiválasztásáról egy Dun & Bradstreet projektben.":::



## <a name="configure-the-enrichment"></a>Bővítés konfigurálása

1. A célközönség információin belül nyissa meg a következőt: **Adatok** > **Bővítés**.

1. Válassza **az Adatok** gazdagítása lehetőséget a Dun & Bradstreet csempén, és válassza az Első lépések **lehetőséget**.

   :::image type="content" source="media/enrichment-dnb-tile.png" alt-text="Képernyőkép a Dun & Bradstreet csempéről.":::

1. Válasszon egy [kapcsolatot](connections.md) a legördülő listából. Ha nem érhető el egy kapcsolat sem, akkor forduljon a rendszergazdához. Ha Ön rendszergazda, létrehozhat egy kapcsolatot. Válassza **a Kapcsolat** hozzáadása lehetőséget, és válassza a Dun & Bradstreet **lehetőséget**. 

1. A kapcsolat megerősítéséhez válassza **a Csatlakozás Dunhoz & Bradstreet** lehetőséget.

1. Válassza a Tovább **lehetőséget**, és válassza ki az **Ügyfél adatkészlet**, amelyet a Dun & Bradstreet vállalati adataival szeretne gazdagítani. Kiválaszthatja a Vevő **entitást az összes ügyfélprofil gazdagításához, vagy kiválaszthat egy szegmensegységet, hogy csak az** adott szegmensben található egységes ügyfélprofilokat gazdagítsa.

1. Válassza a Tovább lehetőséget **,** és határozza meg, hogy az egyesített profilok mely mezőivel keresse meg a Dun & Bradstreet megfelelő vállalati adatait. A **DUNS-szám** vagy **a Vállalat** neve és **az Ország** mező megadása kötelező. Az ország mező támogatja [a két- vagy hárombetűs országkódokat](https://www.iso.org/iso-3166-country-codes.html), az angol nyelvű országnevet, az anyanyelvi országnevet és a telefonelőtagot. Néhány gyakori országváltozat a következők:

   * Usa: Amerikai Egyesült Államok, Egyesült Államok, USA, Amerika.
   * CA: Kanada.
   * GB: Egyesült Királyság, Egyesült Királyság, Nagy-Britannia, GB, Nagy-Britannia és Észak-Írország Egyesült Királysága, Nagy-Britannia Egyesült Királysága.
   * AU: Ausztrália, Ausztrál Nemzetközösség.
   * FR: Franciaország, Francia Köztársaság.
   * DE: Németország, Német, Deutschland, Allemagne, Németországi Szövetségi Köztársaság, Németországi Köztársaság.

   :::image type="content" source="media/enrichment-dnb-mapping.png" alt-text="Dun & Bradstreet mezőleképezési ablaktábla.":::

1. A mező leképezésének befejezéséhez válassza a **Következő** lehetőséget.

1. Adja meg a bővítés nevét, és válassza a **Bővítés memtése** lehetőséget a lehetőségek áttekintése után.


## <a name="configure-a-connection-for-dun--bradstreet"></a>Kapcsolat konfigurálása a következőhöz: Dun & Bradstreet 

A kapcsolatok konfiguráljához rendszergazdának kell lennie. Válassza **a Kapcsolat hozzáadása lehetőséget** gazdagítás *konfigurálásakor, vagy* nyissa meg az **AdminConnections** > **lehetőséget,** és válassza **a Beállítás** a Dun & Bradstreet csempén lehetőséget.

1. Válassza az **Első lépések** lehetőséget. 

1. Adja meg a kapcsolat nevét a **Megjelenítendő név** mezőben.

1. Adjon meg érvényes Dun & Bradstreet hitelesítő adatokat és Dun & Bradstreet projektrészleteket *Régió, Drop mappa elérési útja és Drop mappa neve*. Ezt az információt [a Dun & Bradstreet projektből szerzi](#setting-up-your-dun--bradstreet-project).

1. Tekintse át és adja meg hozzájárulását az **adatvédelem és a megfelelőséghez** az **Elfogadom** által.

1. A konfiguráció megerősítéséhez válassza az **Ellenőrzés** lehetőséget.

1. Az ellenőrzés befejezése után válassza a **Mentés** lehetőséget.
   
   :::image type="content" source="media/enrichment-dnb-connection.png" alt-text="Dun & Bradstreet kapcsolatkonfigurációs oldal.":::

## <a name="enrichment-results"></a>Bővítési eredmények

A bővítés frissítése után áttekintheti az újonnan bővített vállalati adatokat a [Saját bővítések](enrichment-hub.md) alatt. Megkeresheti az utolsó frissítés időpontját és a bővített profilok számát.

Az egyes bővített profilok részletes nézetét a **Bővített adatok megtekintése** lehetőségre kattintva érheti el.

## <a name="next-steps"></a>További lépések

[!INCLUDE [next-steps-enrichment](includes/next-steps-enrichment.md)]

## <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség

Ha engedélyezi Dynamics 365 Customer Insights az adatok továbbítását a Dun & Bradstreet részére, engedélyezi az adatok továbbítását a megfelelőségi határokon kívülre Dynamics 365 Customer Insights, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat is. A Microsoft az Ön utasítására továbbítja ezeket az adatokat, de Ön felelős annak biztosításáért, hogy a Dun & Bradstreet eleget tegyen az Esetleges adatvédelmi vagy biztonsági kötelezettségeinek. További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).
A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt a bővítést.


[!INCLUDE[footer-include](includes/footer-banner.md)]
