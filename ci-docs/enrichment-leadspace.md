---
title: Vállalati profilok gazdagítása a Leadspace-szel (előzetes verzió)
description: Általános információk a Leadspace harmadik fél bővítésről.
ms.date: 08/08/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: jodahlMSFT
ms.author: jodahl
manager: shellyha
ms.openlocfilehash: f45fabc036775e11fc439f69513678d0607729d0
ms.sourcegitcommit: b1d06fe26934f12f0c5ed13e8ef1d37e52e67cc7
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/08/2022
ms.locfileid: "9237953"
---
# <a name="enrich-company-profiles-with-leadspace-preview"></a>Vállalati profilok gazdagítása a Leadspace-szel (előzetes verzió)

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

1. Tekintse át az adatvédelmet és a megfelelőséget, és válassza az [Elfogadom lehetőséget](connections.md#data-privacy-and-compliance)**.**

1. Válassza az Ellenőrzés **lehetőséget** a konfiguráció ellenőrzéséhez, majd válassza a Mentés **lehetőséget**.

## <a name="configure-the-enrichment"></a>Bővítés konfigurálása

1. Menjen a z **Adatok** > **Bővítés** menübe, és válassza a **Felfedezés** lapot.

1. Válassza az Adatok gazdagítása lehetőséget **a Vállalati adatok** a **Leadspace csempéről.**

   :::image type="content" source="media/leadspace-tile.png" alt-text="Képernyőkép – Leadspace csempe.":::

1. Tekintse át az áttekintést, majd válassza a Tovább **lehetőséget**.

1. Válassza ki a kapcsolatot. Ha nem érhető el egy kapcsolat sem, akkor forduljon a rendszergazdához.

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

## <a name="view-enrichment-results"></a>Gazdagítási eredmények megtekintése

[!INCLUDE [enrichment-results](includes/enrichment-results.md)]

További tájékoztatásért tekintse meg a [Leadspace API-kat](https://support.leadspace.com/hc/en-us/sections/201997649-API).

## <a name="next-steps"></a>További lépések

[!INCLUDE [next-steps-enrichment](includes/next-steps-enrichment.md)]

[!INCLUDE [footer-include](includes/footer-banner.md)]