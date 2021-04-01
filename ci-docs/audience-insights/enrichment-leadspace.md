---
title: A vállalati profilok bővítése a harmadik féltől származó bővítési Leadspace-szel
description: Általános információk a Leadspace harmadik fél bővítésről.
ms.date: 11/24/2020
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: kishorem-MS
ms.author: kishorem
manager: shellyha
ms.openlocfilehash: 41c56aece043c2d7658fd2655713e1e98775edec
ms.sourcegitcommit: bae40184312ab27b95c140a044875c2daea37951
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/15/2021
ms.locfileid: "5597652"
---
# <a name="enrichment-of-company-profiles-with-leadspace-preview"></a>A vállalati profilok bővítése Leadspace-szel (előzetes verzió)

A Leadspace egy adatelemző vállalat, amely egy B2B ügyfél-adatplatformot biztosít. Lehetővé teszi, hogy az ügyfelek az egyesített ügyfélprofilokkal bővítsék az adataikat. A bővítések tartalmaznak kiegészítő attribútumokkal, mint például vállalatméret, székhely, iparág stb.

## <a name="prerequisites"></a>Előfeltételek

A Leadspace konfigurálásához teljesülnie kell az alábbi előfeltételeknek:

- Aktív Leadspace licence van, és "végleges kulcsa" (más néven **Leadspace-token**). A termékkel kapcsolatos részletekért forduljon közvetlenül a [Leadspace](https://www.leadspace.com/products/leadspace-on-demand/) vállalathoz.
- [Rendszergazda](permissions.md#administrator) engedéllyel rendelkezik.
- A vállalatokhoz [egyesített ügyfélprofilok](customer-profiles.md) tartoznak.

## <a name="configuration"></a>Konfigurálás

1. A célközönség információin belül nyissa meg a következőt: **Adatok** > **Bővítés**.

1. Válassza az **Adataim bővítése** lehetőséget a Leadspace csempéjén.

   :::image type="content" source="media/leadspace-tile.png" alt-text="Képernyőkép – Leadspace csempe.":::

1. Válassza az **Első lépések** lehetőséget , majd adja meg az aktív **Leadspace-tokent** (végleges kulcs). Ellenőrizze és adja meg az **adatvédelemre és a megfelelőségre** vonatkozó beleegyezését az **Elfogadom** jelölőnégyzet bejelölésével. Erősítse meg mindkét bemenetet a **Csatlakozik a Leadspace-hez** lehetőség kiválasztásával.

1. Válassza az **Adatok leképezés** lehetőséget, és a Leadspace vállalati adatokkal bővíteni kívánt adatkészletet. Kiválaszthatja a *Vevő* entitást az összes ügyfélprofil gazdagítására, vagy kiválaszthat egy szegmens entitást, amely csak az adott szegmensben található vevőprofilokat gazdagítja.

   :::image type="content" source="media/enrichment-leadspace-select-segment.png" alt-text="Válasszon az ügyfélprofil és a szegmensek bővítése közül.":::

1. Kattintson a **Tovább** lehetőségre, és adja meg, hogy az egyesített profilokból mely mezők használhatók a Leadspace-ből származó megfelelő vállalati adatok kereséséhez. A **Vállalat neve** mező kitöltése kötelező. A nagyobb egyeztetési pontosság érdekében akár két másik mező is hozzáadható: **Vállalati webhely** és **Vállalat székhelye**.

   :::image type="content" source="media/enrichment-leadspace-mapping.png" alt-text="Leadspace mező leképezési ablaka.":::
   
1. Válassza az **Alkalmaz** lehetőséget a mezők leképezésének végrehajtásához.

1. Válassza a **Futtatás** lehetőséget a vállalati profilok bővítése érdekében. A bővítés időtartama az egyesített ügyfélprofilok számától függ.

## <a name="enrichment-results"></a>Bővítési eredmények

A bővítés frissítése után áttekintheti az újonnan bővített vállalati adatokat a [Saját bővítések](enrichment-hub.md) alatt. Megkeresheti az utolsó frissítés időpontját és a bővített profilok számát.

Az egyes bővített profilok részletes nézetét a **Bővített adatok megtekintése** lehetőségre kattintva érheti el.

További tájékoztatásért tekintse meg a [Leadspace API-kat](https://support.leadspace.com/hc/en-us/sections/201997649-API).

## <a name="next-steps"></a>Következő lépések

Építsen a bővített ügyféladatokra. Hozzon létre [szegmenseket](segments.md), [mértékeket](measures.md) , sőt [exportálhatja az adatokat](export-destinations.md), hogy személyre szabott élményeket tudjon nyújtani az ügyfeleknek.

## <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség

Amikor engedélyezi a Dynamics 365 Customer Insights szolgáltatást az adatok Leadspace szolgáltatásba való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat. A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy a Leadspace megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek. További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).
A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt a bővítést.


[!INCLUDE[footer-include](../includes/footer-banner.md)]