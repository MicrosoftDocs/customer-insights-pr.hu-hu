---
title: Bővítés a harmadik fél bővítési Experiannal
description: Általános információk a Experian harmadik fél bővítésről.
ms.date: 12/10/2020
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: kishorem-ms
ms.author: kishorem
manager: shellyha
ms.openlocfilehash: 4d4723e8f793ee857c4f5204a42be8338c71d4c3
ms.sourcegitcommit: bae40184312ab27b95c140a044875c2daea37951
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/15/2021
ms.locfileid: "5597790"
---
# <a name="enrich-customer-profiles-with-demographics-from-experian-preview"></a>Ügyfelek profiljainak gazdagítása az Experianból (előzetes verzió)

A Experian a fogyasztói és üzleti hitel-jelentési és marketing szolgáltatások globális vezetője. Az Experian adatbővítési szolgáltatásai segítségével mélyebben megismerheti az ügyfeleket, ha bővíti az ügyfelek profilját demográfiai adatokkal, például a háztartás méretével, a jövedelemmel és más információkkal.

## <a name="prerequisites"></a>Előfeltételek

Az Experian konfigurálásához teljesülnie kell az alábbi előfeltételeknek:

- Aktív Experian-előfizetése van. Az előfizetés megkezdéséhez [forduljon közvetlenül a Experianhoz](https://www.experian.com/marketing-services/contact). [További információ az Experian adatgazdagításáról](https://www.experian.com/marketing-services/microsoft?cmpid=ems_web_mci_cdppage).
- Rendelkezik a Felhasználói azonosítóval, Félazonosítóval és Modellszámmal aaz SSH-képes Secure Transport (ST) fiókhoz, amit az Experian hozott létre Önnek.
- [Rendszergazdai](permissions.md#administrator) jogosultságokkal rendelkezik célközönségi-információkban.

## <a name="configuration"></a>Konfigurálás

1. Menjen a z **Adatok** > **Bővítés** menübe, és válassza a **Felfedezés** lapot.

1. Válassza **Az adataim bővítése** lehetőséget a Experian csempén.

   > [!div class="mx-imgBorder"]
   > ![Experian csempe](media/experian-tile.png "Experian csempe")

1. Válassza az **Első lépések** lehetőséget , és adja meg a Experian Secure Transport fiókjához tartozó felhasználói azonosítót, a félazonosítót és a modellszámot. Ellenőrizze és adja meg az **adatvédelemre és a megfelelőségre** vonatkozó beleegyezését az **Elfogadom** jelölőnégyzet bejelölésével. Az **Alkalmaz** lehetőség választásával erősítse meg a összes bevitt adatot.

## <a name="map-your-fields"></a>Mezők megfeleltetése

1.  Válassza az **Adatok hozzáadása** lehetőséget, és az Experian vállalati adatokkal bővíteni kívánt **Ügyfél adatkészletet**. Kiválaszthatja a **Vevő** entitást az összes ügyfélprofil gazdagítására, vagy kiválaszthat egy szegmens entitást, amely csak az adott szegmensben található vevőprofilokat gazdagítja.

1. Válassza ki a kulcsazonosítókat a **Név és cím**, **E-mail** vagy **Telefon** közül, és küldje el az Experiannek a identitás feloldása érdekében.

   > [!TIP]
   > Minél több kulcsazonosító-attribútumot küld el az Experian számára, valószínűleg annál nagyobb lesz az egyezési arány.

1. Válassza a **Tovább** lehetőséget, és képezze le a megfelelő attribútumokat az egyesített ügyfél entitásból a kijelölt kulcsazonosító-mezőkhöz.

1. Az **Attribútum hozzáadása** lehetőséget választva leképezheti az összes olyan további attribútumot, amelyet el szeretne küldeni a Experian számára.

1.  Válassza a **Mentés** lehetőséget a mezők leképezésének végrehajtásához.

    > [!div class="mx-imgBorder"]
    > ![Experian mezőleképezés](media/experian-field-mapping.png "Experian mezőleképezés")

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