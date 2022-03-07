---
title: A szegmensek hozzájárulási szabályainak aktiválása
description: Kövesse az alábbi lépéseket a hozzájárulási adatok összekapcsolásához és a hozzájárulási ellenőrzések aktiválásához célközönség elemzésekben. A rendszergazda letilthatja a beleegyezési ellenőrzéseket is.
ms.date: 11/12/2021
ms.subservice: audience-insights
ms.topic: how-to
author: smithy7
ms.author: smithc
ms.reviewer: mhart
manager: shellyha
ms.openlocfilehash: 4b55c82229b1a6189c0dd67d145386344286df8a
ms.sourcegitcommit: e7cdf36a78a2b1dd2850183224d39c8dde46b26f
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/16/2022
ms.locfileid: "8227496"
---
# <a name="activate-consent-rules"></a>Hozzájárulási szabályok aktiválása

A [Consent Center (előzetes verzió)](../consent-management/overview.md) segít a különböző forrásokból származó hozzájárulási adatok harmonizálásában. Az alapértelmezett hozzájárulási ellenőrzések alkalmazásához használja az egyesített hozzájárulási *entitást*. Miután a hozzájárulási adatokat a Hozzájárulási központba importálta, és konfigurálta az adatokra vonatkozó szabályokat, a *Hozzájárulás* entitás automatikusan szinkronizálódik a célközönség elemzésekhez.

## <a name="enable-consent-checks"></a>Hozzájárulás-ellenőrzések engedélyezése

A hozzájárulási központba importált hozzájárulási adatokkal (előzetes verzió) és a beállított szabályokkal engedélyezheti a hozzájárulás ellenőrzését. 

:::image type="content" source="../consent-management/media/enable-consent-checks-audience-insights.png" alt-text="Az aktív hozzájárulási adatokkal rendelkező célközönség elemzések beállításainak hozzájárulási lapja.":::

1. A célközönség információin belül nyissa meg a következőt: **Rendszergazda** > **Rendszer**.

1. Válassza a **Hozzájárulás (előnézet)** lapot.

1. **A Hozzájárulás-ellenőrzések** engedélyezése szakaszban állítsa a váltást **Be** gombra az engedélyezni kívánt összes területen.

1. **Az alapértelmezett hozzájárulási szabályok** felülbírálásának engedélyezése jelölőnégyzet bejelölésével eltávolíthatja az adott szegmensen kényszerített alapértelmezett hozzájárulás-ellenőrzéseket. 

1. A legördülő menüben válassza ki, hogy hol szeretné engedélyezni a felülbírálásokat.     

1. A Hozzájárulás csatolása az **ügyfélprofilokhoz** szakaszban válassza ki azt az attribútumot, amelyet azonosítóként használ a hozzájárulási adatok ügyféladatokhoz való kapcsolásához. Valószínűleg telefonszám vagy e-mail cím lesz. 

1. A beállítások alkalmazásához válassza a Mentés **lehetőséget**.

## <a name="disable-consent-checks"></a>Hozzájárulás-ellenőrzések letiltása

Ahhoz, hogy a rendszergazda ne használjon beleegyezési adatokat célközönség elemzésekben, ennek megfelelően frissítenie kell a rendszerbeállításokat.

1. A célközönség információin belül nyissa meg a következőt: **Rendszergazda** > **Rendszer**.

1. Válassza a **Hozzájárulás (előnézet)** lapot.

1. **A Hozzájárulás-ellenőrzések** engedélyezése szakaszban állítsa a kapcsolót Ki **.**

> [!TIP]
> A hozzájáruláskezelési képesség használatának leállításához olvassa el a Rendszerbeállítások a Hozzájárulási központban (előzetes verzió) [című témakört](../consent-management/system-settings.md).
