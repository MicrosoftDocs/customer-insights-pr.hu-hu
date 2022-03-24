---
title: Bővítés a HERE Technologies független gyártótól származó bővítéssel
description: Általános információk a HERE Technologies harmadik fél bővítésről.
ms.date: 04/09/2021
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: jodahlMSFT
ms.author: jodahl
manager: shellyha
ms.openlocfilehash: 1cbbad9bfe559bcb15b23894fc7475507aae8add
ms.sourcegitcommit: 50d32a4cab01421a5c3689af789e20857ab009c4
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/03/2022
ms.locfileid: "8376353"
---
# <a name="enrichment-of-customer-profiles-with-here-technologies-preview"></a>Ügyfélprofilok bővítése a HERE Technologies (előzetes verzió) segítségével

A HERE Technologies egy helyplatformot biztosító vállalat, amely helyalapú adatokat és szolgáltatásokat nyújt. A HERE Technologies adatbővítési szolgáltatásaival pontosabb helyértelmezést hozhat létre az ügyfelekről a cím normalizálásával, földrajzi hosszúság és szélesség kinyerésével stb.

## <a name="prerequisites"></a>Előfeltételek

A HERE Technologies bővítések konfigurálásához a következő előfeltételeknek kell teljesülnie:

- Aktív HERE Technologies előfizetéssel kell rendelkeznie. Az előfizetéshez [regisztrálhat itt](https://developer.here.com/sign-up?utm_medium=referral&utm_source=Microsoft-Dynamics-CI&create=Freemium-Basic) vagy [felveheti a HERE Technologies-szel a kapcsolatot](https://developer.here.com/help?utm_medium=referral&utm_source=Microsoft-Dynamics-CI#how-can-we-help-you) közvetlenül. [Itt többet is megtudhat a HERE Technologies helybővítéshez.](https://developer.here.com/location-enrichment?cid=Dev-MicrosoftDynamics-DB-0-Dev-&utm_source=MicrosoftDynamics&utm_medium=referral&utm_campaign=Online_Dev_ReferralMicrosoft)

- Egy HERE [kapcsolat](connections.md) elérhető *vagy* rendelkezik [rendszergazdai](permissions.md#admin) engedélyekkel és HERE Technologies API-kulccsal.

## <a name="configure-the-enrichment"></a>Bővítés konfigurálása

1. Lépjen az **Adatok** > **Bővítés** pontra. 

1. Válassza az **Adatok bővítése** lehetőséget a HERE Technologies csempén, majd válassza az **Első lépések** lehetőséget.

   > [!div class="mx-imgBorder"]
   > ![HERE Technologies csempe.](media/HERE-tile.png "HERE Technologies csempe")

1. Válasszon egy [kapcsolatot](connections.md) a legördülő listából. Ha nem érhető el egy kapcsolat sem, akkor forduljon a rendszergazdához. Ha Ön rendszergazda, a **Kapcsolat hozzáadása** lehetőség kiválasztásával hozhat létre kapcsolatot. Válassza a **HERE Technologies** -t a legördülő listából. 

1. A kijelölés megerősítéséhez válassza a **Kapcsolódás a HERE Technologies-hez** lehetőséget.

1.  Válassza a **Következő** lehetőséget, és válassza a helyadatokkal bővíteni kívánt **Ügyfél adatkészletet** a HERE Technologies-ből. Kiválaszthatja a **Vevő** entitást az összes ügyfélprofil gazdagítására, vagy kiválaszthat egy szegmens entitást, amely csak az adott szegmensben található vevőprofilokat gazdagítja.

    :::image type="content" source="media/enrichment-HERE-configuration-customer-data-set.png" alt-text="Képernyőkép az ügyféladatkészlet kiválasztásáról.":::

1. Válassza ki, hogy szeretné-e leképezni a mezőket az elsődleges és/vagy másodlagos címre. Mezőleképezést is megadhat a címekhez, és külön bővítheti a címekhez kapcsolódó profilokat. Ez lehet például az otthoni és a munkahelyi cím is. Válassza a **Következő** lehetőséget.

1. Adja meg, hogy az egyesített profilokból mely mezők használhatók a megfelelő helyadatok megkereséséhez a HERE Technologiesből. A kiválasztott elsődleges és/vagy másodlagos címhez az **Utca 1.** és az **Irányítószám** mező megadása kötelező. A nagyobb egyeztetési pontosság érdekében további mezők adhatók hozzá.

   > [!div class="mx-imgBorder"]
   > ![HERE Technologies bővítés konfigurációs oldal.](media/enrichment-HERE-configuration.png "HERE Technologies bővítés konfigurációs oldal")

1. A mező leképezésének befejezéséhez válassza a **Következő** lehetőséget.

1. Adjon nevet a bővítésnek. 

1. Válassza a **Bővítés mentése** lehetőséget, miután áttekintette a lehetőségeit.

## <a name="configure-the-connection-for-here-technologies"></a>Konfigurálja a kapcsolatot a HERE Technologies-hoz 

A kapcsolatok konfiguráljához rendszergazdának kell lennie. A bővítés konfigurálásakor válassza a **Kapcsolat hozzáadása** lehetőséget, *vagy* menjen a **Rendszergazda** > **Kapcsolatok** elemre, és válassza a **Beállítások** lehetőséget a HERE Technologies csempén.

1. Adja meg a kapcsolat nevét a **Megjelenítendő név** mezőben.

1. Adjon meg egy érvényes HERE Technologies API-kulcsot.

1. Tekintse át és adja meg hozzájárulását az **adatvédelem és a megfelelőséghez** az **Elfogadom** által.

1. A konfiguráció megerősítéséhez válassza az **Ellenőrzés** lehetőséget.

1. Az ellenőrzés befejezése után válassza a **Mentés** lehetőséget.

   > [!div class="mx-imgBorder"]
   > ![A HERE Technologies kapcsolat konfigurációs oldala.](media/enrichment-HERE-connection.png "A HERE Technologies kapcsolat konfigurációs oldala")

## <a name="enrichment-results"></a>Bővítési eredmények

A bővítési folyamat megkezdéséhez válassza a **Futtatás** parancsot a parancssorból. Azt is engedélyezheti, hogy a rendszer a bővítést automatikusan egy [ütemezett frissítés](system.md#schedule-tab) részeként futtassa. A feldolgozási idő az ügyféladatok méretétől és a HERE Technologies API-reagálási időponttól függ.

A bővítési folyamat befejeződése után áttekintheti az újonnan bővített ügyfelek profiljainak adatait a **Saját bővítések** alatt. Emellett megtalálhatja az utolsó frissítés időpontját és a bővített profilok számát is.

Az egyes bővített profilok részletes nézetét a **Bővített adatok megtekintése** lehetőségre kattintva érheti el.

## <a name="next-steps"></a>További lépések

[!INCLUDE [next-steps-enrichment](../includes/next-steps-enrichment.md)]

## <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség

Amikor engedélyezi a Dynamics 365 Customer Insights szolgáltatást az adatok HERE Technologies szolgáltatásba való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat. A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy a HERE Technologies megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek. További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).
A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt a bővítést.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
