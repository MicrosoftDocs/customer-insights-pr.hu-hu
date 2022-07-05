---
title: 'Hogyan: Környezetek kezelése'
description: Ismerje meg, hogyan kezelheti a meglévő Customer Insights-környezeteket rendszergazdaként."
ms.date: 05/31/2022
ms.subservice: audience-insights
ms.topic: how-to
ms.reviewer: mhart
author: mukeshpo
ms.author: mukeshpo
manager: shellyha
searchScope:
- ci-system-about
- customerInsights
ms.openlocfilehash: fc3b3f404cf0ac84c782778414494289c803babe
ms.sourcegitcommit: dca46afb9e23ba87a0ff59a1776c1d139e209a32
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/29/2022
ms.locfileid: "9083058"
---
# <a name="how-to-manage-environments"></a>Hogyan: Környezetek kezelése

A rendszergazdák [környezeteket hoznak létre](create-environment.md) és kezelnek. Módosíthatnak néhány beállítást a meglévő környezetekben. Az üzleti, a típus, a régió, a tárolási lehetőség és Dataverse a beállítások a környezet létrehozása után rögzülnek. Ha módosítani szeretné ezeket a beállításokat, állítsa alaphelyzetbe a környezetet, vagy hozzon létre egy új környezetet.

## <a name="edit-an-existing-environment"></a>Egy meglévő környezet szerkesztése

A meglévő környezetek bizonyos részleteit szerkesztheti.

1. Válassza ki az alkalmazás fejlécében a **Környezet** választót.

1. Kattintson a **Szerkesztés** ikonra.

   :::image type="content" source="media/edit-environment.png" alt-text="Ikon a környezeti beállítások szerkesztéséhez.":::

1. A **Környezet szerkesztése** mezőben frissítheti a környezet beállításait.

Egy új környezettel való kezdéshez lásd: [Új környezet létrehozása](create-environment.md).

## <a name="change-the-owner-of-an-environment"></a>Környezet tulajdonosának módosítása

Több felhasználó is rendelkezhet rendszergazdai engedélyekkel, de csak egy felhasználó a környezet tulajdonosa. Alapértelmezés szerint kezdetben a rendszergazda hozza létre a környezetet. Egy környezet rendszergazdájaként tulajdonosi jogosultságot rendelhet egy másik, rendszergazdai engedélyekkel rendelkező felhasználóhoz.

1. Válassza ki az alkalmazás fejlécében a **Környezet** választót.

1. Kattintson a **Szerkesztés** ikonra.

1. A Környezet **szerkesztése mezőben válassza az** **Alapvető információk** lépést.

1. **A Környezet** tulajdonosának módosítása mezőben válassza ki a környezet új tulajdonosát.  

1. Válassza az Áttekintés és befejezés **, majd** a Frissítés **lehetőséget** a módosítások alkalmazásához.

## <a name="claim-ownership-of-an-environment"></a>Környezet tulajdonjogának igénylése

Ha a tulajdonos felhasználói fiókját törlik vagy felfüggesztik, a környezetnek nem lesz tulajdonosa. Minden rendszergazdai felhasználó igényelheti a tulajdonjogot, és új tulajdonossá válhat. Továbbra is birtokolhatják a környezetet, vagy [megváltoztathatják a tulajdonjogot egy másik rendszergazdára](#change-the-owner-of-an-environment).

A tulajdonjog igényléséhez válassza a **Tulajdonjog** átvétele gombot, amely a Customer Insights minden oldalának tetején megjelenik, amikor az eredeti tulajdonos elhagyta a szervezetet.

## <a name="reset-an-existing-environment-preview"></a>Meglévő környezet alaphelyzetbe állítása (előzetes verzió)

Egy környezet tulajdonosaként visszaállíthatja a környezetet üres állapotba, ha törölni szeretné az összes konfigurációt, és el szeretné távolítani a betöltött adatokat.

1. Válassza ki az alkalmazás fejlécében a **Környezet** választót.

1. Válassza ki az alaphelyzetbe állítani kívánt környezetet, és válassza ki a függőleges három pontot (&vellip;).

1. Válassza az **Alaphelyzetbe állítás** lehetőséget.

   :::image type="content" source="media/reset-environment.png" alt-text="Vezérlés a környezet alaphelyzetbe állításához.":::

1. Válassza ki, hogy a teljes környezetet, az adatforrások kivételével mindent, vagy bármi mást, ami az egyesített ügyfélprofil tetején van konfigurálva, alaphelyzetbe szeretné-e állítani.

1. A megerősítéshez adja meg a környezet nevét, majd válassza a Visszaállítás **lehetőséget**.

## <a name="delete-an-existing-environment"></a>Meglévő környezet törlése

Egy környezet tulajdonosaként törölheti a felügyelt környezetet.

1. Válassza ki az alkalmazás fejlécében a **Környezet** választót.

1. Válassza ki az alaphelyzetbe állítani kívánt környezetet, és válassza ki a függőleges három pontot (&vellip;). 

1. Válassza a **Törlés** lehetőséget.

   :::image type="content" source="media/delete-environment.png" alt-text="A környezet törlésének vezérlése.":::

1. A törlés jóváhagyásához adja meg a környezet nevét, és válassza a **Törlés** lehetőséget.

> [!IMPORTANT]
> A környezet törlése nem szünteti meg a környezettel való Dataverse kapcsolatot. Ha azt tervezi, hogy ugyanazt Dataverse a környezetet a jövőben egy új Customer Insights-környezethez csatlakoztatja, el kell távolítania ezt a kapcsolatot Ismerje meg, [hogyan távolíthat el egy meglévő kapcsolatot egy Dataverse környezettel](customer-insights-dataverse.md#remove-an-existing-connection-to-a-dataverse-environment).

[!INCLUDE [footer-include](includes/footer-banner.md)]
