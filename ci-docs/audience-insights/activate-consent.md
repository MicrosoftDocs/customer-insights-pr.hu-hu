---
title: Szegmensekre vonatkozó hozzájárulási szabályok aktiválása
description: Kövesse az alábbi lépéseket a hozzájárulási adatok összekapcsolásához és a hozzájárulási ellenőrzések aktiválásához célközönség elemzésben. A rendszergazda letilthatja a hozzájárulás-ellenőrzéseket is.
ms.date: 11/03/2021
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: smithy7
ms.author: smithc
ms.reviewer: mhart
manager: shellyha
ms.openlocfilehash: 45899738d39bd5caa433e123f9fe59020e831998
ms.sourcegitcommit: 79b09498d1328e5551fb8684c44af1fb149f9881
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/10/2021
ms.locfileid: "7790779"
---
# <a name="activate-consent-rules"></a>Hozzájárulási szabályok aktiválása

A [Hozzájárulási központ (előzetes verzió)](../consent-management/overview.md) segít a különböző forrásokból származó hozzájárulási adatok harmonizálásában. Az egyesített *hozzájárulási entitás használatával* alapértelmezett hozzájárulási ellenőrzéseket alkalmazhat. Miután a hozzájárulási adatokat a Hozzájárulási központba importálta, és konfigurálta az adatokra vonatkozó szabályokat, a *hozzájárulási* entitás automatikusan szinkronizálódik célközönség elemzési adatokkal.

## <a name="enable-consent-checks"></a>Hozzájárulás-ellenőrzések engedélyezése

A Hozzájárulási központba importált hozzájárulási adatokkal (előzetes verzió) és a beállított szabályokkal engedélyezheti a hozzájárulás-ellenőrzéseket. 

:::image type="content" source="../consent-management/media/enable-consent-checks-audience-insights.png" alt-text="Hozzájárulás lap célközönség elemzési beállításokban aktivált hozzájárulási adatokkal.":::

1. A célközönség információin belül nyissa meg a következőt: **Rendszergazda** > **Rendszer**.

1. Válassza a **Beleegyezés (előnézet)** fület.

1. A **Hozzájárulás-ellenőrzések engedélyezése** szakaszban állítsa be a kapcsolót **Be-re az összes engedélyezni kívánt** területen.

1. Jelölje be az **Alapértelmezett hozzájárulási szabályok felülbírálásának engedélyezése** jelölőnégyzetet az adott szegmensre kényszerített alapértelmezett hozzájárulási ellenőrzések eltávolításához. 

1. A legördülő menüben válassza ki, hogy hol szeretné engedélyezni a felülbírálásokat.     

1. A **Hozzájárulás csatolása az ügyfélprofilokhoz** szakaszban válassza ki azt az attribútumot, amely azonosítóként van használva a hozzájárulási adatok ügyféladatokhoz való kapcsolásához. Valószínűleg telefonszám vagy e-mail cím lesz. 

1. A **·** beállítások alkalmazásához válassza a Mentés lehetőséget.

## <a name="disable-consent-checks"></a>Hozzájárulás-ellenőrzések letiltása

Ahhoz, hogy a rendszergazda ne használjon beleegyezési adatokat célközönség elemzési adatokban, ennek megfelelően frissítenie kell a rendszerbeállításokat.

1. A célközönség információin belül nyissa meg a következőt: **Rendszergazda** > **Rendszer**.

1. Válassza a **Beleegyezés (előnézet)** fület.

1. A **Hozzájárulás-ellenőrzések engedélyezése** szakaszban állítsa a váltást **Ki** gombra.
