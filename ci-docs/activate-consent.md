---
title: Szegmensek hozzájárulási szabályainak aktiválása
description: Kövesse az alábbi lépéseket a hozzájárulási adatok összekapcsolásához és a hozzájárulási ellenőrzések aktiválásához a alkalmazásban Dynamics 365 Customer Insights. A rendszergazda letilthatja a beleegyezési ellenőrzéseket is.
ms.date: 04/27/2022
ms.topic: how-to
author: anubhav-t
ms.author: antando
ms.reviewer: mhart
manager: shellyha
ms.openlocfilehash: f82e3a4031fee8bcaa88575cbd68b37385a7fffb
ms.sourcegitcommit: 4ae316c856b8de0f08a4605f73e75a8c2cf51c4e
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/13/2022
ms.locfileid: "8755173"
---
# <a name="activate-consent-rules"></a>Hozzájárulási szabályok aktiválása

A [Hozzájárulási Központ (előzetes verzió)](consent-management/overview.md) segít a különböző forrásokból származó hozzájárulási adatok összehangolásában. Az egyesített *hozzájárulás entitással* alapértelmezett hozzájárulás-ellenőrzéseket alkalmazhat. A hozzájárulási adatok importálása és a térképszabályok konfigurálása után a Rendszer automatikusan szinkronizálja a *Hozzájárulás* entitást a programmal Dynamics 365 Customer Insights.

## <a name="enable-consent-checks"></a>Hozzájárulás-ellenőrzések engedélyezése

A Hozzájárulási központba importált hozzájárulási adatokkal (előzetes verzió) és a beállított szabályokkal engedélyezheti a hozzájárulások ellenőrzését. 

:::image type="content" source="consent-management/media/enable-consent-checks.png" alt-text="Hozzájárulás lap a Customer Insights beállításaiban az aktivált hozzájárulási adatokkal.":::

1. A Customer Insights szolgáltatásban lépjen a **Felügyelet** > **Rendszer** részre.

1. Válassza a **Hozzájárulás (előnézet)** lapot.

1. **A Hozzájárulás-ellenőrzések** engedélyezése szakaszban állítsa a váltást Be **értékre** az összes engedélyezni kívánt terület esetében.

1. Jelölje be az **Alapértelmezett hozzájárulási szabályok** felülbírálásának engedélyezése jelölőnégyzetet az adott szegmensre kényszerített alapértelmezett hozzájárulásellenőrzések eltávolításához. 

1. A legördülő menüben válassza ki, hogy hol szeretné engedélyezni a felülbírálásokat.     

1. **Az Ügyfélprofilokhoz** való hozzájárulás csatolása szakaszban válassza ki azt az attribútumot, amelyet azonosítóként használnak a hozzájárulási adatok ügyféladatokhoz való csatolásához. Valószínűleg telefonszám vagy e-mail cím lesz. 

1. A beállítások alkalmazásához válassza a Mentés **lehetőséget**.

## <a name="disable-consent-checks"></a>Hozzájárulás-ellenőrzések letiltása

Ahhoz, hogy a rendszergazda ne használja a hozzájárulási adatokat a Customer Insights alkalmazásban, ennek megfelelően frissítenie kell a rendszerbeállításokat.

1. A Customer Insights szolgáltatásban lépjen a **Felügyelet** > **Rendszer** részre.

1. Válassza a **Hozzájárulás (előnézet)** lapot.

1. **A Hozzájárulás-ellenőrzések** engedélyezése szakaszban állítsa a váltást Ki **értékre**.

> [!TIP]
> A hozzájáruláskezelési képesség használatának leállításához olvassa el a Hozzájárulási központ Rendszerbeállításai (előzetes verzió) [című témakörét](consent-management/system-settings.md).
