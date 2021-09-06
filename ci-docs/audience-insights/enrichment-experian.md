---
title: Független gyártótól származó bővítéssel történő Experian bővítés
description: A független gyártótól származó Experian bővítésre vonatkozó általános információk.
ms.date: 04/09/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: kishorem-ms
ms.author: kishorem
manager: shellyha
ms.openlocfilehash: c54f6a00cb28b0ab11716c02aa8761dfa382f07e3360183b5d38b9720e890c21
ms.sourcegitcommit: aa0cfbf6240a9f560e3131bdec63e051a8786dd4
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/10/2021
ms.locfileid: "7032623"
---
# <a name="enrich-customer-profiles-with-demographics-from-experian-preview"></a>Ügyfélprofilok bővítése demográfiai adatokkal az Experian -ból (előzetes verzió)

Az Experian a fogyasztói és üzleti hiteljelentési és marketingszolgáltatások globális vezetője. Az Experian adatbővítési szolgáltatások segítségével mélyebben megértheti ügyfeleit, az ügyfélprofilok bővítése által demográfiai adatokkal, mint például a háztartás nagysága, bevétel, stb.

## <a name="prerequisites"></a>Előfeltételek

Az Experian konfigurálásához teljesülnie kell az alábbi előfeltételeknek:

- Aktív Experian előfizetéssel kell rendelkeznie. Az előfizetéshez közvetlenül [forduljon Experian](https://www.experian.com/marketing-services/contact) . [További információk Experian adatbővítésről](https://www.experian.com/marketing-services/microsoft?cmpid=ems_web_mci_cdppage).

- Az Experian kapcsolatot már konfigurálta egy rendszergazda *vagy* Ön rendelkezik [rendszergazda](permissions.md#administrator) engedélyekkel. Szüksége van a felhasználói azonosítóra, partnerazonosítóra, és modellszámra is az SSH-kompatibilis Secure Transport (ST) fiókjához, amelyet az Experian hozott létre az Ön számára.

## <a name="supported-countriesregions"></a>Támogatott országok/régiók

Jelenleg csak az Egyesült Államokban támogatjuk az ügyfélprofilok bővítését.

## <a name="configure-the-enrichment"></a>Bővítés konfigurálása

1. Menjen a z **Adatok** > **Bővítés** menübe, és válassza a **Felfedezés** lapot.

1. Válassza ki az **Adatom bővítése** az Experian csempén.

   > [!div class="mx-imgBorder"]
   > ![Experian-csempe.](media/experian-tile.png "Experian tile")
   > 

1. Válasszon egy [kapcsolatot](connections.md) a legördülő listából. Ha nem érhető el egy kapcsolat sem, akkor forduljon a rendszergazdához. Ha Ön rendszergazda, akkor kapcsolatot hozhat létre a **Kapcsolat hozzáadása** majd Experian kiválasztásával a legördülő listából. 

1. Válassza a **Csatlakozás Experian** lehetőséget, a kapcsolat kiválasztásának megerősítéséhez.

1.  Válassza a **Tovább** lehetőséget, majd azt az **Ügyfél adatkészlet** -et, amelyet bővíteni szeretne demográfiai adatokkal Experian -ból. Kiválaszthatja a **Vevő** entitást az összes ügyfélprofil gazdagítására, vagy kiválaszthat egy szegmens entitást, amely csak az adott szegmensben található vevőprofilokat gazdagítja.

    :::image type="content" source="media/enrichment-Experian-configuration-customer-data-set.png" alt-text="Képernyőkép az ügyféladatkészlet kiválasztásáról.":::

1. Válassza a **Tovább** lehetőséget és határozza meg, hogy milyen típusú mezőket kell használni az egyesített profiljaiból az egyező demográfiai adatok kereséséhez Experian -ból . Legalább egy mezőben meg kell adni a **Név és cím**, a **Telefon** vagy az **E-mail-cím** adatokat. A nagyobb egyezési pontosság érdekében legfeljebb két másik mezőt lehet hozzáadni. Ez a beállítás hatással van a következő lépésben elérhető leképezési mezőkre.

    > [!TIP]
    > Minél több kulcsazonosító-attribútum kerül Experian -ba, annál valószínűbb a magasabb egyezés eredményezése.

1. A mező leképezésének elkezdéséhez válassza a **Következő** lehetőséget.

1. Határozza meg, hogy melyik mezőket kell használni az egyesített profiljaiból az egyező demográfiai adatok kereséséhez Experian -ból . A kötelező mezők meg vannak jelölve.

1. Adja meg a bővítés nevét és a kimeneti entitás nevét.

1. Válassza a **Bővítés mentése** lehetőséget, miután áttekintette a lehetőségeit.

## <a name="configure-the-connection-for-experian"></a>Kapcsolat konfigurálása Experian -hoz 

A kapcsolatok konfiguráljához rendszergazdának kell lennie. Válassza a **Kapcsolat hozzáadása** lehetőséget, amikor bővítményt konfigurál *vagy* menjen a **Rendszergazda** > **Kapcsolatok** elemre, és válassza a **Beállítás** lehetőséget az Experian csempén.

1. Válassza az **Első lépések** lehetőséget.

1. Adja meg a kapcsolat nevét a **Megjelenítendő név** mezőben.

1. Adja meg a felhasználó azonosítót, partnerazonosítót és modellszámot az Experian Secure Transport fiókjához.

1. Tekintse át és adja meg hozzájárulását az **adatvédelem és a megfelelőséghez** az **Elfogadom** által.

1. A konfiguráció megerősítéséhez válassza az **Ellenőrzés** lehetőséget.

1. Az ellenőrzés befejezése után válassza a **Mentés** lehetőséget.
   
   :::image type="content" source="media/enrichment-Experian-connection.png" alt-text="Experian kapcsolati konfiguráció panel.":::

## <a name="enrichment-results"></a>Bővítési eredmények

A bővítési folyamat megkezdéséhez válassza a **Futtatás** parancsot a parancssorból. Azt is engedélyezheti, hogy a rendszer a bővítést automatikusan egy [ütemezett frissítés](system.md#schedule-tab) részeként futtassa. A feldolgozási idő az ügyféladatok méretétől és azoktól a bővítés folyamatoktól függ, melyek az Experian fiókjához lettek beállítva.

A bővítési folyamat befejeződése után áttekintheti az újonnan bővített ügyfelek profiljainak adatait a **Saját bővítések** alatt. Emellett megtalálhatja az utolsó frissítés időpontját és a bővített profilok számát is.

Az egyes bővített profilok részletes nézetét a **Bővített adatok megtekintése** lehetőségre kattintva érheti el.

## <a name="next-steps"></a>Következő lépések

Építsen a bővített ügyféladatokra. Hozzon létre [szegmenseket](segments.md) és [intézkedéseket](measures.md), továbbá [exportálja az adatokat](export-destinations.md) , hogy személyre szabott élményt nyújtson ügyfeleinek.

## <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség

Amikor engedélyezed a Dynamics 365 Customer Insights -nak, hogy továbbítsa az adatokat Experian -ba, engedélyezed az adatátvitelt a megfelelőséghatáron kívülre a Dynamics 365 Customer Insights -nak, beleértve az esetlegesen bizalmas adatokat, például személyes adatokat. A Microsoft az Ön utasítására továbbítja az ilyen adatokat, de Ön felelős annak biztosításáért, hogy az Experian megfeleljen az esetleges adatvédelmi és biztonsági kötelezettségeknek. További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).
A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt a bővítést.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
