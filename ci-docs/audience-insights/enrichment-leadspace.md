---
title: A vállalati profilok bővítése a harmadik féltől származó bővítési Leadspace-szel
description: Általános információk a Leadspace harmadik fél bővítésről.
ms.date: 09/30/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: jodahlMSFT
ms.author: jodahl
manager: shellyha
ms.openlocfilehash: c57eb0ceb50e3b778acac72a4bbfd733a5b0c401
ms.sourcegitcommit: 23c8973a726b15050e368cc6e0aab78b266a89f6
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/08/2021
ms.locfileid: "7617404"
---
# <a name="enrichment-of-company-profiles-with-leadspace-preview"></a>A vállalati profilok bővítése Leadspace-szel (előzetes verzió)

A Leadspace egy adatelemző vállalat, amely egy B2B ügyfél-adatplatformot biztosít. Lehetővé teszi olyan környezetek számára, amelyek partnereken alapuló egységes ügyfélprofilokat tartalmaznak adataik gyarapítása érdekében. Az *ügyfélprofilok* gyarapítása attribútumokkal, például a vállalat méretével, helyével vagy iparágával. A *Kapcsolattartók* profiljainak bővítése attribútumokkal, például cím, személy vagy e-mail-ellenőrzés.

## <a name="prerequisites"></a>Előfeltételek

A Leadspace konfigurálásához teljesülnie kell az alábbi előfeltételeknek:

- Aktív Leadspace-licenccel rendelkezik.
- A partnereken alapuló [egységes ügyfélprofiljai](customer-profiles.md) vannak.
- A Leadspace kapcsolatot már konfigurálta egy rendszergazda, vagy rendelkezik [rendszergazdai](permissions.md#administrator) engedélyekkel, és a „végleges kulcs” (más néven **Leadspace token**). Termékeikkel kapcsolatos részletekért forduljon közvetlenül a [Leadspace-hez](https://www.leadspace.com/leadspace-microsoft-dynamics-365/).

## <a name="configure-the-enrichment"></a>Bővítés konfigurálása

1. A célközönség információin belül nyissa meg a következőt: **Adatok** > **Bővítés**.

1. Válassza az **Adatok bővítése** lehetőséget a Leadspace csempén, majd válassza az **Első lépések** lehetőséget.

   :::image type="content" source="media/leadspace-tile.png" alt-text="Képernyőkép – Leadspace csempe.":::

1. Válasszon egy [kapcsolatot](connections.md) a legördülő listából. Ha nem érhető el egy kapcsolat sem, akkor forduljon a rendszergazdához. Ha Ön rendszergazda, a **Kapcsolat hozzáadása**, és a **Leadspace** lehetőség kiválasztásával hozhat létre kapcsolatot. 

1. Válassza a **Kapcsolódás a Leadspace-hez** lehetőséget a kapcsolat megerősítéséhez.

1. Válassza a **Következő** lehetőséget, és válassza a vállalati adatokkal bővíteni kívánt **Ügyfél adatkészletet** a Leadspace-ből. Kiválaszthatja a **Vevő** entitást az összes ügyfélprofil gazdagítására, vagy kiválaszthat egy szegmens entitást, amely csak az adott szegmensben található vevőprofilokat gazdagítja.

    :::image type="content" source="media/enrichment-Leadspace-configuration-customer-data-set.png" alt-text="Képernyőkép az ügyféladatkészlet kiválasztásáról.":::

1. Válassza a **Következő** lehetőséget, és határozza meg, hogy az egyesített profilokból mely mezők használhatók a Leadspace-ből származó vállalati adatok egyeztetéséhez. A **Vállalat neve** mező kitöltése kötelező. A nagyobb egyeztetési pontosság érdekében akár két másik mező is hozzáadható: **Vállalati webhely** és **Vállalat székhelye**.

   :::image type="content" source="media/enrichment-leadspace-mapping.png" alt-text="Leadspace mező leképezési ablaka.":::

1. A mező leképezésének befejezéséhez válassza a **Következő** lehetőséget.

1. Jelölje be a jelölőnégyzetet, ha vannak gyarapítani kívánt *Kapcsolattartói profilok*. Célközönség insights automatikusan leképezi a kötelező mezőket.

   :::image type="content" source="media/enrichment-leadspace-contacts.png" alt-text="Leadspace kapcsolattartói rekordok gazdagítása.":::
 
1. Adja meg a bővítés nevét, és válassza a **Bővítés memtése** lehetőséget a lehetőségek áttekintése után.


## <a name="configure-the-connection-for-leadspace"></a>A Leadspace kapcsolatának beállítása 

A kapcsolatok konfiguráljához rendszergazdának kell lennie. A bővítés konfigurálásakor válassza a **Kapcsolat hozzáadása** lehetőséget, *vagy* menjen a **Rendszergazda** > **Kapcsolatok** elemre, és válassza a **Beállítások** lehetőséget a Leadspace csempén.

1. Válassza az **Első lépések** lehetőséget. 

1. Adja meg a kapcsolat nevét a **Megjelenítendő név** mezőben.

1. Adjon meg egy érvényes Leadspace jogkivonatot.

1. Tekintse át és adja meg hozzájárulását az **adatvédelem és a megfelelőséghez** az **Elfogadom** által.

1. A konfiguráció megerősítéséhez válassza az **Ellenőrzés** lehetőséget.

1. Az ellenőrzés befejezése után válassza a **Mentés** lehetőséget.
   
   :::image type="content" source="media/enrichment-Leadspace-connection.png" alt-text="Az Leadspace kapcsolat konfigurációs oldala.":::

## <a name="enrichment-results"></a>Bővítési eredmények

A bővítés frissítése után áttekintheti az újonnan bővített vállalati adatokat a [Saját bővítések](enrichment-hub.md) alatt. Megkeresheti az utolsó frissítés időpontját és a bővített profilok számát.

Az egyes bővített profilok részletes nézetét a **Bővített adatok megtekintése** lehetőségre kattintva érheti el.

További tájékoztatásért tekintse meg a [Leadspace API-kat](https://support.leadspace.com/hc/en-us/sections/201997649-API).

## <a name="next-steps"></a>További lépések


[!INCLUDE [next-steps-enrichment](../includes/next-steps-enrichment.md)]

## <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség

Amikor engedélyezi a Dynamics 365 Customer Insights szolgáltatást az adatok Leadspace szolgáltatásba való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat. A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy a Leadspace megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek. További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).
A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt a bővítést.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
