---
title: A vállalati profilok bővítése a harmadik féltől származó bővítési Leadspace-szel
description: Általános információk a Leadspace harmadik fél bővítésről.
ms.date: 06/10/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: jodahlMSFT
ms.author: jodahl
manager: shellyha
ms.openlocfilehash: ca53f15bd7c71b3b4acb396c4daf52d7c7aff9eb
ms.sourcegitcommit: 27c5473eecd851263e60b2b6c96f6c0a99d68acb
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/13/2022
ms.locfileid: "8954182"
---
# <a name="enrichment-of-company-profiles-with-leadspace-preview"></a>A vállalati profilok bővítése Leadspace-szel (előzetes verzió)

A Leadspace egy adattudományokkal foglalkozó vállalat, amely üzleti számlákkal (B-to-B) kapcsolatos ügyféladatplatformot biztosít. Lehetővé teszi olyan környezetek számára, amelyek partnereken alapuló egységes ügyfélprofilokat tartalmaznak adataik gyarapítása érdekében. Az *ügyfélprofilok* gyarapítása attribútumokkal, például a vállalat méretével, helyével vagy iparágával. A *Kapcsolattartók* profiljainak bővítése attribútumokkal, például cím, személy vagy e-mail-ellenőrzés.

## <a name="prerequisites"></a>Előfeltételek

- Aktív Leadspace-licenc.
- [Egységes ügyfélprofilok](customer-profiles.md) fiókok alapján.
- A Leadspace-kapcsolatot [egy](connections.md) [rendszergazda konfigurálja](#configure-the-connection-for-leadspace). Termékeikkel kapcsolatos részletekért forduljon közvetlenül a [Leadspace-hez](https://www.leadspace.com/leadspace-microsoft-dynamics-365/).

## <a name="configure-the-connection-for-leadspace"></a>A Leadspace kapcsolatának beállítása

Rendszergazdának [kell](permissions.md#admin) lennie a Customer Insights szolgáltatásban, és rendelkeznie kell az "örök kulccsal" (más néven **Leadspace tokennel**).

1. Válassza a Kapcsolat **hozzáadása lehetőséget** a gazdagítás konfigurálásakor, vagy lépjen a Rendszergazdai **kapcsolatok** > **elemre**, és válassza a Beállítás **lehetőséget** a Leadspace csempén.

   :::image type="content" source="media/enrichment-Leadspace-connection.png" alt-text="Az Leadspace kapcsolat konfigurációs oldala.":::

1. Adja meg a kapcsolat nevét és egy érvényes Leadspace tokent.

1. Tekintse át és adja meg hozzájárulását az [adatvédelem és a megfelelőséghez](#data-privacy-and-compliance) az **Elfogadom** által.

1. Válassza az Ellenőrzés **lehetőséget** a konfiguráció ellenőrzéséhez, majd válassza a Mentés **lehetőséget**.

### <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség

Amikor engedélyezi a Dynamics 365 Customer Insights szolgáltatást az adatok Leadspace szolgáltatásba való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat. A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy a Leadspace megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek. További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).
A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt a bővítést.

## <a name="configure-the-enrichment"></a>Bővítés konfigurálása

1. Menjen a z **Adatok** > **Bővítés** menübe, és válassza a **Felfedezés** lapot.

1. Válassza az Adatok gazdagítása lehetőséget **a Vállalati adatok** a **Leadspace csempéről.**

   :::image type="content" source="media/leadspace-tile.png" alt-text="Képernyőkép – Leadspace csempe.":::

1. Tekintse át az áttekintést, majd válassza a Tovább **lehetőséget**.

1. Válassza ki a kapcsolatot. Forduljon egy rendszergazdához, ha az egyik nem érhető el.

1. Válassza a **Következő** lehetőséget.

1. Válassza ki az **Ügyfél adatkészlet**, és válassza ki azt a profilt vagy szegmenst, amelyet a Leadspace-ből származó vállalati adatokkal szeretne gazdagítani. Az *Ügyfél* entitás gazdagítja az összes ügyfélprofilt, míg egy szegmens csak az adott szegmensben található ügyfélprofilokat gazdagítja.

    :::image type="content" source="media/enrichment-Leadspace-configuration-customer-data-set.png" alt-text="Képernyőkép az ügyféladatkészlet kiválasztásáról.":::

1. Határozza meg, hogy az egyesített profilokból mely típusú mezőket használja az egyeztetéshez: az elsődleges és/vagy másodlagos címet. Mezőleképezést is megadhat a címekhez, és külön bővítheti a címekhez kapcsolódó profilokat. Például egy otthoni címhez és egy vállalkozás címéhez. Válassza a **Következő** lehetőséget.

1. Leképezheti a mezőket a Leadspace vállalati adataira. A **Vállalat neve** mező kitöltése kötelező. A nagyobb egyeztetési pontosság érdekében akár két másik mező is hozzáadható: **Vállalati webhely** és **Vállalat székhelye**.

   :::image type="content" source="media/enrichment-leadspace-mapping.png" alt-text="Leadspace mező leképezési ablaka.":::

1. A mező leképezésének befejezéséhez válassza a **Következő** lehetőséget.

1. Jelölje be a jelölőnégyzetet, ha vannak gyarapítani kívánt *Kapcsolattartói profilok*. A Customer Insights automatikusan leképezi a kötelező mezőket.

   :::image type="content" source="media/enrichment-leadspace-contacts.png" alt-text="Leadspace kapcsolattartói rekordok gazdagítása.":::

1. Válassza a **Következő** lehetőséget.

1. **Adja meg a gazdagítás nevét** és a **Kimeneti entitás nevét**.

1. Válassza a **Bővítés mentése** lehetőséget, miután áttekintette a lehetőségeit.

1. Válassza a Futtatás **lehetőséget** a gazdagítási folyamat elindításához, vagy a közel lehetőséget a **Bővítések** lapra való visszatéréshez.

## <a name="enrichment-results"></a>Bővítési eredmények

[!INCLUDE [enrichment-results](includes/enrichment-results.md)]

További tájékoztatásért tekintse meg a [Leadspace API-kat](https://support.leadspace.com/hc/en-us/sections/201997649-API).

## <a name="next-steps"></a>További lépések

[!INCLUDE [next-steps-enrichment](includes/next-steps-enrichment.md)]

[!INCLUDE [footer-include](includes/footer-banner.md)]
