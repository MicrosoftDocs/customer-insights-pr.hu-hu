---
title: Keressen hasonló ügyfeleket az AI-val (videót tartalmaz)
description: Hasonló ügyfél-szegmensek keresése mesterséges intelligenciával.
ms.date: 03/25/2022
ms.subservice: audience-insights
ms.topic: conceptual
author: JimsonChalissery
ms.author: jimsonc
ms.reviewer: v-wendysmith
manager: shellyha
searchScope:
- ci-segment-builder
- ci-segment-insights
- customerInsights
ms.openlocfilehash: 7877349817829f7486a63a1355a81361e1cb2c13
ms.sourcegitcommit: b7dbcd5627c2ebfbcfe65589991c159ba290d377
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/27/2022
ms.locfileid: "8642678"
---
# <a name="similar-customers-preview"></a>Hasonló ügyfelek (előzetes verzió)

Ez a funkció lehetővé teszi, hogy a hasonló ügyfeleket keressen meg az ügyfélkörön belül mesterséges intelligencia segítségével. A szolgáltatás használatához legalább egy szegmensnek létre kell lennie hozva. A meglévő szegmens feltételeinek kibővítésével a szegmenshez hasonló ügyfelek kereshetők meg.

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWOFou]

> [!NOTE]
> A *Hasonló ügyfelek megkeresése* automatizált eszközöket használ az adatok értékelésére és az előrejelzések készítéséhez az adatok alapján, és így egy olyan képessége van, ami profilalkotáshoz használható az Általános adatvédelmi rendelet („GDPR”) definíciója szerint. Ha az ügyfél ezt a funkciót adatok feldolgozására használja, az a GDPR vagy más törvények és szabályozások hatálya alá tartozhat. Felelős azért, hogy biztosítsa, hogy a Dynamics 365 Customer Insights használata, az előrejelzésekkel együtt, megfelel a vonatkozó törvényeknek és szabályozásoknak, többek között az adatvédelemmel, személyes adatokkal, biometrikus adatokkal, adatok védelmével és a kommunikáció titkosságával kapcsolatos törvényeknek.

## <a name="finding-similar-customers"></a>Hasonló ügyfelek keresése

1. Nyissa meg a **Szegmensek lehetőséget,** és válassza ki azt a szegmenst, amelyre az új szegmenst alapozni szeretné. Ez a *Forrásszegmense*.

1. A műveleti sávban válassza a **Hasonló ügyfelek keresése** lehetőséget.

1. Tekintse át az új szegmens javasolt nevét, és szükség szerint módosítsa azt.

1. Szükség esetén címkéket [is hozzáadhat](work-with-tags-columns.md#manage-tags) az új szegmenshez.

1. Tekintse át az új szegmenst definiáló mezőket. Ezek a mezők határozzák meg, hogy a rendszer milyen alapon próbálja megkeresni a hasonló ügyfeleket a forrásszegmensében. A rendszer alapértelmezés szerint az ajánlott mezőket választja ki.
  A modell teljesítményét jelentősen csökkentő mezők automatikusan ki vannak zárva:
  
   - A következő adattípusú mezők: StringType, BooleanType, CharType, LongType, IntType, DoubleType, FloatType, ShortType
   - A 2 nél kevesebb vagy 30-nál nagyobb számosságú (a mező elemeinek száma) mezők

1. Válassza ki, hogy az **Összes ügyfelet** vagy csak az új szegmens egy **Adott meglévő szegmensében** szereplő ügyfeleket kívánja-e felvenni.

1. A rendszer alapértelmezés szerint azt javasolja, hogy a kimenetében a célközönség legfeljebb 20%-át adja meg. Szükség szerint szerkessze ezt a küszöböt. A küszöb növelése csökkenti a pontosságot.

1. Az ügyfelek felvétele a forrásszegmensbe a hasonló attribútumokkal rendelkező ügyfelek mellett a **forrásszegmensből** származó tagok felvétele jelölőnégyzet bejelölésével.

1. Válassza az oldal alján található **Futtatás** lehetőséget, hogy egy bináris osztályozási feladatot (a gépi tanulás egy módszere) indítson el, amely elemzi az adatkészletet.

## <a name="view-the-similar-segment"></a>A hasonló szegmens megtekintése

A hasonló szegmens feldolgozását követően megtalálja az új szegmenst a **Szegmensek** oldalon.

> [!div class="mx-imgBorder"]
> ![Hasonló ügyfelek szegmens.](media/expanded-segment.png "Hasonló ügyfelek szegmens")

A szegmens részleteinek megnyitásához válassza a **Nézet** lehetőséget a műveleti sávban. Ez a nézet a [hasonlósági pontszámok](#about-similarity-scores) közötti eredményeloszlásra vonatkozó információkat tartalmaz . Emellett megtalálja a hasonlóságok pontszámát is a **Szegmens tagok előnézete** részben.

## <a name="use-the-output-of-a-similar-segment"></a>Hasonló szegmens kimenetének használata

A többi szegmenshez hasonlóan [egy hasonló szegmens kimenetével is dolgozhat](segments.md). Exportálja például a szegmenst, vagy kiépíthet egy mérőszámot.

## <a name="refresh-and-edit-a-similar-segment"></a>Hasonló szegmens frissítése és szerkesztése

Hasonló szegmens frissítéséhez jelölje ki azt a **Szegmensek** oldalon, majd a műveleti sávban válassza a **Frissítés** lehetőséget.

A hasonló szegmensek szerkesztése újra feldolgozza az adatait. A korábban létrehozott szegmens frissülni a frissített adatokkal.
Hasonló szegmens szerkesztéséhez jelölje ki azt a **Szegmensek** oldalon, majd a műveleti sávban válassza a **Szerkesztés** lehetőséget. Alkalmazza a módosításokat, és a feldolgozás megkezdéséhez válassza a **Futtatás** lehetőséget.

## <a name="delete-a-similar-segment"></a>Hasonló szegmens törlése

Jelölje ki a szegmenst a **Szegmensek** oldalon, majd a műveleti sávban válassza a **Törlés** lehetőséget. Majd hagyja jóvá a törlést.

## <a name="about-similarity-scores"></a>A hasonlósági pontszámokról

A bináris besorolású gépi tanulási modell egy pontszámot rendel hozzá a hasonló szegmensben lévő ügyfelekhez. A pontszám a forrás-szegmensben lévő ügyfelekhez való hasonlóságon alapul.

- A 0,55 alatti hasonlósági pontszámmal rendelkező ügyfelek *nem hasonlóként* vannak besorolva a forrásszegmensben található ügyfelekhez
- A 0,55 – 0,7 közötti hasonlósági pontszámok *némileg hasonlónak* minősülnek
- A 0,7 – 0,85 közötti hasonlósági pontszámok *hasonlónak* minősülnek
- A 0,85 – 1 között hasonlósági pontszámok az olyan ügyfelek, amelyeket a rendszer *nagyon hasonlónak* minősített

A 0,4 alatti hasonlósági pontszámú ügyfelek nem szerepelnek a modell kimenetében. A rendszer ezeket nem tartja eléggé hasonlónak a forrásszegmenshez.

[!INCLUDE [footer-include](includes/footer-banner.md)]
