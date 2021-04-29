---
title: Bővítés a harmadik fél bővítési Experiannal
description: Általános információk a Experian harmadik fél bővítésről.
ms.date: 04/09/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: kishorem-ms
ms.author: kishorem
manager: shellyha
ms.openlocfilehash: 9cf2a7fa18ecc022ea67f6829f52381ad59f3172
ms.sourcegitcommit: aaa275c60c0c77c88196277b266a91d653f8f759
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/14/2021
ms.locfileid: "5896376"
---
# <a name="enrich-customer-profiles-with-demographics-from-experian-preview"></a>Ügyfelek profiljainak gazdagítása az Experianból (előzetes verzió)

A Experian a fogyasztói és üzleti hitel-jelentési és marketing szolgáltatások globális vezetője. Az Experian adatbővítési szolgáltatásai segítségével mélyebben megismerheti az ügyfeleket, ha bővíti az ügyfelek profilját demográfiai adatokkal, például a háztartás méretével, a jövedelemmel és más információkkal.

## <a name="prerequisites"></a>Előfeltételek

Az Experian konfigurálásához teljesülnie kell az alábbi előfeltételeknek:

- Aktív Experian-előfizetése van. Az előfizetés megkezdéséhez [forduljon közvetlenül a Experianhoz](https://www.experian.com/marketing-services/contact). [További információ az Experian adatgazdagításáról](https://www.experian.com/marketing-services/microsoft?cmpid=ems_web_mci_cdppage).

- Egy Experian-kapcsolatot már konfigurált egy rendszergazda, *vagy* Ön rendelkezik a [rendszergazdai](permissions.md#administrator) engedélyekkel. Szüksége van az Experian által az Ön számára létrehozott SSH-engedélyezett Secure Transport (ST) fiókjához a felhasználói azonosítóra, a félazonosítóra és a modellszámra is.

## <a name="configure-the-enrichment"></a>Bővítés konfigurálása

1. Menjen a z **Adatok** > **Bővítés** menübe, és válassza a **Felfedezés** lapot.

1. Válassza **Az adataim bővítése** lehetőséget a Experian csempén.

   > [!div class="mx-imgBorder"]
   > ![Experian csempe](media/experian-tile.png "Experian csempe")
   > 

1. Válasszon egy [kapcsolatot](connections.md) a legördülő listából. Ha nem érhető el egy kapcsolat sem, akkor forduljon a rendszergazdához. Ha Ön rendszergazda, akkor a legördülő menüből válassza ki a **Kapcsolat hozzáadása** és az Experian lehetőséget a kapcsolat létrehozásához. 

1. Válassza a **Kapcsolódás az Experianhez** lehetőséget a kapcsolat kiválasztásához.

1.  Válassza a **Következő** lehetőséget, és válassza a demográfiai adatokkal bővíteni kívánt **Ügyfél adatkészletet** az Experianből. Kiválaszthatja a **Vevő** entitást az összes ügyfélprofil gazdagítására, vagy kiválaszthat egy szegmens entitást, amely csak az adott szegmensben található vevőprofilokat gazdagítja.

    :::image type="content" source="media/enrichment-Experian-configuration-customer-data-set.png" alt-text="Képernyőkép az ügyféladatkészlet kiválasztásáról.":::

1. Válassza a **Következő** lehetőséget, és határozza meg, hogy az egyesített profilokból milyen típusú mezők használhatók az Experianből származó demográfiai adatok egyeztetéséhez. Legalább egy mezőben meg kell adni a **Név és cím**, a **Telefon** vagy az **E-mail-cím** adatokat. A nagyobb egyezési pontosság érdekében legfeljebb két másik mezőt lehet hozzáadni. Ez a beállítás hatással van a következő lépésben elérhető leképezési mezőkre.

    > [!TIP]
    > Minél több kulcsazonosító-attribútumot küld el az Experian számára, valószínűleg annál nagyobb lesz az egyezési arány.

1. A mező leképezésének elkezdéséhez válassza a **Következő** lehetőséget.

1. Határozza meg, hogy az egyesített profilokból mely mezők használhatók az Experianből származó demográfiai adatok egyeztetéséhez. A kötelező mezők meg vannak jelölve.

1. Adja meg a bővítés nevét és a kimeneti entitás nevét.

1. Válassza a **Bővítés mentése** lehetőséget, miután áttekintette a lehetőségeit.

## <a name="configure-the-connection-for-experian"></a>Az Experian kapcsolatának beállítása 

A kapcsolatok konfiguráljához rendszergazdának kell lennie. A bővítés konfigurálásakor válassza a **Kapcsolat hozzáadása** lehetőséget, *vagy* menjen a **Rendszergazda** > **Kapcsolatok** elemre, és válassza a **Beállítások** lehetőséget az Experian csempén.

1. Válassza az **Első lépések** lehetőséget.

1. Adja meg a kapcsolat nevét a **Megjelenítendő név** mezőben.

1. Adja meg az Experian Secure Transport fiókjához tartozó érvényes felhasználói azonosítót, félazonosítót és modellszámot.

1. Ellenőrizze és adja meg az **adatvédelemre és a megfelelőségre** vonatkozó beleegyezését az **Elfogadom** jelölőnégyzet bejelölésével

1. A konfiguráció megerősítéséhez válassza az **Ellenőrzés** lehetőséget.

1. Az ellenőrzés befejezése után válassza a **Mentés** lehetőséget.
   
   :::image type="content" source="media/enrichment-Experian-connection.png" alt-text="Az Experian kapcsolat konfigurációs ablaktábla.":::

## <a name="enrichment-results"></a>Bővítési eredmények

A bővítési folyamat megkezdéséhez válassza a **Futtatás** parancsot a parancssorból. Azt is engedélyezheti, hogy a rendszer a bővítést automatikusan egy [ütemezett frissítés](system.md#schedule-tab) részeként futtassa. A feldolgozási idő az ügyféladatok méretétől és a Experian által a fiókjához beállított bővítési folyamattól függ.

A bővítési folyamat befejeződése után áttekintheti az újonnan bővített ügyfelek profiljainak adatait a **Saját bővítések** alatt. Emellett megtalálhatja az utolsó frissítés időpontját és a bővített profilok számát is.

Az egyes bővített profilok részletes nézetét a **Bővített adatok megtekintése** lehetőségre kattintva érheti el.

## <a name="next-steps"></a>Következő lépések

Építsen a bővített ügyféladatokra. Hozzon létre [szegmenseket](segments.md), [mértékeket](measures.md) , sőt [exportálhatja az adatokat](export-destinations.md), hogy személyre szabott élményeket tudjon nyújtani az ügyfeleknek.

## <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség

Amikor engedélyezi az Dynamics 365 Customer Insights szolgáltatást az adatok Experianbe való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat. A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy az Experian megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek. További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).
A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt a bővítést.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
