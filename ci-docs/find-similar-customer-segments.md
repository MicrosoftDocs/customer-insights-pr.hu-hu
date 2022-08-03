---
title: Hasonló ügyfelek keresése mesterséges intelligenciával (előzetes verzió) (videót tartalmaz)
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
ms.openlocfilehash: 09fe36a4da45d114cbfccf8dad1e7b80b4b7e320
ms.sourcegitcommit: 8a28e9458b857adf8e90e25e43b9bc422ebbb2cd
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/18/2022
ms.locfileid: "9170730"
---
# <a name="find-similar-customers-with-ai-preview"></a>Hasonló ügyfelek keresése mesterséges intelligenciával (előzetes verzió)

Hasonló ügyfelek keresése az ügyfélkörben mesterséges intelligencia használatával. A funkció használatához legalább egy szegmenst létre kell hoznia. Egy meglévő szegmens feltételeinek kibővítése segít megtalálni az adott szegmenshez hasonló ügyfeleket.

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWOFou]

> [!NOTE]
> *A hasonló ügyfelek* keresése automatizált eszközökkel értékeli ki az adatokat, és előrejelzéseket készít ezen adatok alapján. Ezért képes profilalkotási módszerként használni, mivel ezt a kifejezést az általános adatvédelmi rendelet ("GDPR") határozza meg. Ha az ügyfél ezt a funkciót adatok feldolgozására használja, az a GDPR vagy más törvények és szabályozások hatálya alá tartozhat. Felelős azért, hogy biztosítsa, hogy a Dynamics 365 Customer Insights használata, az előrejelzésekkel együtt, megfelel a vonatkozó törvényeknek és szabályozásoknak, többek között az adatvédelemmel, személyes adatokkal, biometrikus adatokkal, adatok védelmével és a kommunikáció titkosságával kapcsolatos törvényeknek.

## <a name="find-similar-customers"></a>Hasonló ügyfelek keresése

1. Lépjen a Szegmensek **elemre**, és válassza ki azt a szegmenst, amelyre az új szegmenst alapozni szeretné. Ez a *Forrásszegmense*.

1. Válassza a Hasonló ügyfelek keresése **lehetőséget**.

1. Tekintse át az új szegmens javasolt nevét, és szükség szerint módosítsa azt.

1. Ha szükséges, adjon hozzá [címkéket](work-with-tags-columns.md#manage-tags) az új szegmenshez.

1. Tekintse át az új szegmenst definiáló mezőket. Ezek a mezők határozzák meg, hogy a rendszer milyen alapon próbálja megkeresni a hasonló ügyfeleket a forrásszegmensében. A rendszer alapértelmezés szerint kiválasztja az ajánlott mezőket. Ha szükséges, adjon hozzá további mezőket.
  A modell teljesítményét jelentősen csökkentő mezők automatikusan ki vannak zárva:
  
   - A következő adattípusú mezők: StringType, BooleanType, CharType, LongType, IntType, DoubleType, FloatType, ShortType
   - A 2 nél kevesebb vagy 30-nál nagyobb számosságú (a mező elemeinek száma) mezők

1. Válassza ki, hogy a forrásszegmens kivételével az összes ügyfelet **vagy csak az új szegmens egy** másik szegmensében **lévő ügyfeleket szeretné-e szerepeltetni**.

1. A rendszer alapértelmezés szerint azt javasolja, hogy a kimenetében a célközönség legfeljebb 20%-át adja meg. Szükség szerint szerkessze ezt a küszöböt. A küszöb növelése csökkenti a pontosságot.

1. Vegye fel az ügyfeleket a forrásszegmensbe a Tagok felvétele a **forrásszegmensből** a hasonló attribútumokkal rendelkező ügyfelek mellett jelölőnégyzet bejelölésével.

1. Válassza a Futtatás **lehetőséget** az oldal alján egy [bináris besorolási feladat](#about-similarity-scores) (egy gépi tanulás-módszer) elindításához, amely elemzi az adatkészletet.

## <a name="view-the-similar-segment"></a>A hasonló szegmens megtekintése

A hasonló szegmens feldolgozása után az új szegmenst a **Szegmensek** oldalon találja a Bővítés **típussal**.

Válassza a Nézet **lehetőséget** az eredmények eloszlásának megtekintéséhez a [hasonlósági pontszámok és a hasonlósági pontszámok között a Szegmenstagok](#about-similarity-scores) előnézete **alatt**.

:::image type="content" source="media/expanded-segment.png" alt-text="Hasonló ügyfelek szegmens.":::

## <a name="manage-a-similar-segment"></a>Hasonló szegmens kezelése

[Hasonló szegmenssel](segments.md#manage-existing-segments) dolgozhat és kezelhet, mint más szegmensekkel. Exportálja például a szegmenst, vagy kiépíthet egy mérőszámot.

Hasonló szegmens szerkesztése, frissítése, átnevezése, letöltése és törlése. Egy hasonló szegmens szerkesztése újra feldolgozza az adatokat. A korábban létrehozott szegmens frissülni a frissített adatokkal.

## <a name="about-similarity-scores"></a>A hasonlósági pontszámokról

A bináris besorolású gépi tanulási modell egy pontszámot rendel hozzá a hasonló szegmensben lévő ügyfelekhez. A pontszám a forrás-szegmensben lévő ügyfelekhez való hasonlóságon alapul.

- A 0,55 alatti hasonlósági pontszámmal rendelkező ügyfelek *nem hasonlóként* vannak besorolva a forrásszegmensben található ügyfelekhez
- A 0,55 – 0,7 közötti hasonlósági pontszámok *némileg hasonlónak* minősülnek
- A 0,7 – 0,85 közötti hasonlósági pontszámok *hasonlónak* minősülnek
- A 0,85 – 1 között hasonlósági pontszámok az olyan ügyfelek, amelyeket a rendszer *nagyon hasonlónak* minősített

A 0,4 alatti hasonlósági pontszámú ügyfelek nem szerepelnek a modell kimenetében. A rendszer ezeket nem tartja eléggé hasonlónak a forrásszegmenshez.

[!INCLUDE [footer-include](includes/footer-banner.md)]
