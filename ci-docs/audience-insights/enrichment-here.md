---
title: 'Bővítés külső bővítéssel: HERE Technologies'
description: Általános információk a HERE Technologies harmadik fél bővítésről.
ms.date: 10/27/2020
ms.reviewer: jodahl
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: 7082fcfec099c3c9436b233c193be23625f6691a
ms.sourcegitcommit: a9b2cf598f256d07a48bba8617347ee90024a1dd
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/03/2020
ms.locfileid: "4668681"
---
# <a name="enrichment-of-customer-profiles-with-here-technologies-preview"></a>Ügyfélprofilok bővítése a HERE Technologies (előzetes verzió) segítségével

A HERE Technologies egy helyplatformot biztosító vállalat, amely helyalapú adatokat és szolgáltatásokat nyújt. A HERE Technologies adatbővítési szolgáltatásaival pontosabb helyértelmezést hozhat létre az ügyfelekről a cím normalizálásával, földrajzi hosszúság és szélesség kinyerésével stb.

## <a name="prerequisites"></a>Előfeltételek

A HERE Technologies bővítések konfigurálásához a következő előfeltételeknek kell teljesülnie:

- Aktív HERE Technologies előfizetéssel kell rendelkeznie. Az előfizetés beszerzéséhez [regisztrálhat itt](https://developer.here.com/sign-up?utm_medium=referral&utm_source=Microsoft-Dynamics-CI&create=Freemium-Basic) vagy [felveheti a HERE Technologiesszel a kapcsolatot](https://developer.here.com/help?utm_medium=referral&utm_source=Microsoft-Dynamics-CI#how-can-we-help-you) közvetlenül. [Itt többet is megtudhat a HERE Technologies helybővítéshez.](https://developer.here.com/location-enrichment?cid=Dev-MicrosoftDynamics-DB-0-Dev-&utm_source=MicrosoftDynamics&utm_medium=referral&utm_campaign=Online_Dev_ReferralMicrosoft)

- Rendelkezik a HERE Technologies API-kulccsal.

- [Rendszergazda](permissions.md#administrator) engedéllyel rendelkezik.

## <a name="configuration"></a>Konfigurálás

1. Lépjen az **Adatok** > **Bővítés** pontra.

1. Válassza a **Saját adatok bővítése** elemet a HERE Technologies csempén.

   > [!div class="mx-imgBorder"]
   > ![HERE Technologies csempe](media/HERE-tile.png "HERE Technologies csempe")

1. Adja meg az aktív **HERE Technologies API-kulcsot**. Ellenőrizze és adja meg az **adatvédelemre és a megfelelőségre** vonatkozó beleegyezését az **Elfogadom** jelölőnégyzet bejelölésével. 

1. Erősítse meg mindkét bemenetet a **Csatlakozik a HERE-hez** lehetőség kiválasztásával.

1. Válassza az **Adatok hozzáadása** lehetőséget, és adja meg, hogy szeretné-e leképezni a mezőket az elsődleges és/vagy másodlagos címre. Megadhatja a mezők leképezését mindkét címhez (például otthoni és üzleti cím), és a mindkét címhez tartozó profilt külön is bővítheti. Válassza a **Következő** lehetőséget.

1. Adja meg, hogy az egyesített profilokból mely mezők használhatók a megfelelő helyadatok megkereséséhez a HERE Technologiesből. A kiválasztott elsődleges és/vagy másodlagos címhez az **Utca 1.** és az **Irányítószám** mező megadása kötelező. A nagyobb egyeztetési pontosság érdekében további mezők adhatók hozzá.

   > [!div class="mx-imgBorder"]
   > ![HERE Technologies bővítés konfigurációs oldal](media/enrichment-HERE-configuration.png "HERE Technologies bővítés konfigurációs oldal")

1. Válassza az **Alkalmaz** lehetőséget a mezők leképezésének végrehajtásához.

## <a name="enrichment-results"></a>Bővítési eredmények

A bővítési folyamat megkezdéséhez válassza a **Futtatás** parancsot a parancssorból. Azt is engedélyezheti, hogy a rendszer a bővítést automatikusan egy [ütemezett frissítés](system.md#schedule-tab) részeként futtassa. A feldolgozási idő az ügyféladatok méretétől és a HERE Technologies API-reagálási időponttól függ.

A bővítési folyamat befejeződése után áttekintheti az újonnan bővített ügyfelek profiljainak adatait a **Saját bővítések** alatt. Emellett megtalálhatja az utolsó frissítés időpontját és a bővített profilok számát is.

Az egyes bővített profilok részletes nézetét a **Bővített adatok megtekintése** lehetőségre kattintva érheti el.

## <a name="next-steps"></a>Következő lépések

Építsen a bővített ügyféladatokra. Hozzon létre [szegmenseket](segments.md), [mértékeket](measures.md) , sőt [exportálhatja az adatokat](export-destinations.md), hogy személyre szabott élményeket tudjon nyújtani az ügyfeleknek.

## <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség

Amikor engedélyezi a Dynamics 365 Customer Insights szolgáltatást az adatok HERE Technologies szolgáltatásba való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat. A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy a HERE Technologies megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek. További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).
A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt a bővítést.
