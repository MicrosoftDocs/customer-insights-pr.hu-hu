---
title: Környezetek kezelése
description: További információ a meglévő Customer Insights-környezetek rendszergazdaként való kezeléséről."
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
ms.openlocfilehash: 62a5856edac5e66e5e42c93313d78fa6826469b3
ms.sourcegitcommit: f5af5613afd9c3f2f0695e2d62d225f0b504f033
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/01/2022
ms.locfileid: "8833495"
---
# <a name="how-to-manage-environments"></a>Útmutató: Környezetek kezelése

A rendszergazdák környezeteket [hoznak létre](create-environment.md) és kezelnek. A meglévő környezetekben módosíthatják egyes beállításokat. A környezet létrehozása után a vállalkozás, a típus, a régió, a tárolási beállítás és Dataverse a beállítások javításra kerülnek. Ha módosítani szeretné ezeket a beállításokat, állítsa alaphelyzetbe a környezetet, vagy hozzon létre egy új környezetet.

## <a name="edit-an-existing-environment"></a>Egy meglévő környezet szerkesztése

A meglévő környezetek bizonyos részleteit szerkesztheti.

1. Válassza ki az alkalmazás fejlécében a **Környezet** választót.

1. Kattintson a **Szerkesztés** ikonra.

   :::image type="content" source="media/edit-environment.png" alt-text="Ikon a környezeti beállítások szerkesztéséhez.":::

1. A **Környezet szerkesztése** mezőben frissítheti a környezet beállításait.

Ha új környezettel szeretne kezdeni, olvassa el az Új környezet létrehozása című [témakört](create-environment.md).

## <a name="change-the-owner-of-an-environment"></a>Környezet tulajdonosának megváltoztatása

Több felhasználó is rendelkezhet rendszergazdai engedélyekkel, de csak egy felhasználó a környezet tulajdonosa. Alapértelmezés szerint kezdetben a rendszergazda hoz létre egy környezetet. A környezet rendszergazdájaként a tulajdonjogot rendszergazdai engedélyekkel rendelkező másik felhasználóhoz is hozzárendelheti.

1. Válassza ki az alkalmazás fejlécében a **Környezet** választót.

1. Kattintson a **Szerkesztés** ikonra.

1. **A Környezet** szerkesztése mezőben nyissa meg az **Alapvető információk** lépést.

1. **A Környezet** tulajdonosának módosítása mezőben válassza ki a környezet új tulajdonosát.  

1. A módosítások alkalmazásához válassza a Véleményezés és befejezés **, majd** a Frissítés **lehetőséget**.

## <a name="claim-ownership-of-an-environment"></a>Környezet tulajdonjogának követelése

Ha a tulajdonos felhasználói fiókját törlik vagy felfüggesztik, a környezetnek nem lesz tulajdonosa. Minden rendszergazda felhasználó igényelheti a tulajdonjogot, és új tulajdonossá válhat. Továbbra is birtokolhatják a környezetet, vagy [megváltoztathatják a tulajdonjogot egy másik rendszergazdára](#change-the-owner-of-an-environment).

A tulajdonjog megszerzéséhez válassza a **Tulajdonjog** átvétele gombot, amely az Ügyfélelemzések minden oldalának tetején jelenik meg, amikor az eredeti tulajdonos elhagyta a szervezetet.

## <a name="reset-an-existing-environment-preview"></a>Meglévő környezet alaphelyzetbe állítása (előzetes verzió)

A környezet tulajdonosaként visszaállíthat egy környezetet üres állapotba, ha törölni szeretné az összes konfigurációt, és el szeretné távolítani a betöltött adatokat.

1. Válassza ki az alkalmazás fejlécében a **Környezet** választót.

1. Jelölje ki az alaphelyzetbe állítani kívánt környezetet, és jelölje ki a függőleges ellipszis (&vellip;) elemet.

1. Válassza az **Alaphelyzetbe állítás** lehetőséget.

   :::image type="content" source="media/reset-environment.png" alt-text="Vezérlő a környezet alaphelyzetbe állításához.":::

1. Válassza ki, hogy a teljes környezetet, az adatforrások kivételével mindent vissza szeretne-e állítani, vagy bármit, ami az egyesített ügyfélprofil tetején van konfigurálva.

1. A megerősítéshez írja be a környezet nevét, és válassza az Alaphelyzet **lehetőséget**.

## <a name="delete-an-existing-environment"></a>Meglévő környezet törlése

A környezet tulajdonosaként törölheti az Ön által felügyelt környezetet.

1. Válassza ki az alkalmazás fejlécében a **Környezet** választót.

1. Jelölje ki az alaphelyzetbe állítani kívánt környezetet, és jelölje ki a függőleges ellipszis (&vellip;) elemet. 

1. Válassza a **Törlés** lehetőséget.

   :::image type="content" source="media/delete-environment.png" alt-text="Vezérlő a környezet törléséhez.":::

1. A törlés jóváhagyásához adja meg a környezet nevét, és válassza a **Törlés** lehetőséget.

> [!IMPORTANT]
> A környezet törlése nem távolítja el a kapcsolatot a Dataverse környezettel. Ha azt tervezi, hogy ugyanazt Dataverse a környezetet a jövőben egy új Customer Insights-környezethez csatlakoztatja, el kell távolítania ezt a kapcsolatot Ismerje meg, hogyan távolíthatja [el a meglévő kapcsolatot egy Dataverse környezettel](customer-insights-dataverse.md#remove-an-existing-connection-to-a-dataverse-environment).

[!INCLUDE [footer-include](includes/footer-banner.md)]
