---
title: Környezetek kezelése
description: Ismerje meg, hogyan kezelheti a meglévő Customer Insights-környezeteket rendszergazdaként."
ms.date: 08/15/2022
ms.subservice: audience-insights
ms.topic: how-to
ms.reviewer: mhart
author: mukeshpo
ms.author: mukeshpo
manager: shellyha
searchScope:
- ci-system-about
- customerInsights
ms.openlocfilehash: 8b4a88bdb75c6e638a76c39d18647681ad4556d7
ms.sourcegitcommit: 267c317e10166146c9ac2c30560c479c9a005845
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/16/2022
ms.locfileid: "9304283"
---
# <a name="manage-environments"></a>Környezetek kezelése

A rendszergazdák [környezeteket hoznak létre](create-environment.md) és kezelnek. Módosíthatnak néhány beállítást a meglévő környezetekben. Az üzleti, a típus, a régió, a tárolási lehetőség és Dataverse a beállítások a környezet létrehozása után rögzülnek. Ha módosítani szeretné ezeket a beállításokat, állítsa alaphelyzetbe a környezetet [,](#reset-an-existing-environment-preview) vagy [hozzon létre egy új környezetet](create-environment.md).

## <a name="edit-an-existing-environment"></a>Egy meglévő környezet szerkesztése

Szerkessze egy meglévő környezet részleteit, például a nevet vagy az alapértelmezett környezet beállítását.

1. Válassza ki az alkalmazás fejlécében a **Környezet** választót.

1. Kattintson a **Szerkesztés** ikonra.

   :::image type="content" source="media/edit-environment.png" alt-text="Ikon a környezeti beállítások szerkesztéséhez.":::

1. **A Környezet** szerkesztése panelen frissítse a környezeti beállításokat.

1. Válassza az Áttekintés és befejezés **, majd** a Frissítés **lehetőséget** a módosítások alkalmazásához.

## <a name="change-the-owner-of-an-environment"></a>Környezet tulajdonosának módosítása

Több felhasználó is rendelkezhet rendszergazdai engedélyekkel, de csak egy felhasználó a környezet tulajdonosa. Alapértelmezés szerint kezdetben a rendszergazda hozza létre a környezetet. Egy környezet rendszergazdájaként tulajdonosi jogosultságot rendelhet egy másik, rendszergazdai engedélyekkel rendelkező felhasználóhoz.

1. Válassza ki az alkalmazás fejlécében a **Környezet** választót.

1. Kattintson a **Szerkesztés** ikonra.

1. **A Környezet** szerkesztése panelen válassza az **Alapvető információk** lépést.

1. **A Környezet** tulajdonosának módosítása mezőben válassza ki a környezet új tulajdonosát.  

1. Válassza az Áttekintés és befejezés **, majd** a Frissítés **lehetőséget** a módosítások alkalmazásához.

## <a name="claim-ownership-of-an-environment"></a>Környezet tulajdonjogának igénylése

Ha a tulajdonos felhasználói fiókját törlik vagy felfüggesztik, a környezetnek nem lesz tulajdonosa. Bármely rendszergazdai felhasználó igényelheti a tulajdonjogot, és új tulajdonossá válhat. A tulajdonos rendszergazda továbbra is birtokolhatja a környezetet, vagy [módosíthatja a tulajdonjogot egy másik rendszergazdára](#change-the-owner-of-an-environment).

A tulajdonjog igényléséhez válassza a **Tulajdonjog** átvétele gombot, amely a Customer Insights minden oldalának tetején megjelenik, amikor az eredeti tulajdonos elhagyta a szervezetet.

## <a name="reset-an-existing-environment-preview"></a>Meglévő környezet alaphelyzetbe állítása (előzetes verzió)

Egy környezet tulajdonosaként állítsa vissza a környezetet üres állapotba, ha törölni szeretné az összes konfigurációt, és el szeretné távolítani a betöltött adatokat.

1. Válassza ki az alkalmazás fejlécében a **Környezet** választót.

1. Válassza ki az alaphelyzetbe állítani kívánt környezetet, és válassza ki a függőleges három pontot (&vellip;).

1. Válassza a Visszaállítás (előnézet) lehetőséget **·**.

   :::image type="content" source="media/reset-environment.png" alt-text="Vezérlés a környezet alaphelyzetbe állításához.":::

1. Válassza ki, hogy a teljes környezetet, az adatforrások kivételével mindent, vagy bármi mást, ami az egyesített ügyfélprofil tetején van konfigurálva, alaphelyzetbe szeretné-e állítani.

1. A megerősítéshez adja meg a környezet nevét, majd válassza a Visszaállítás **lehetőséget**.

## <a name="delete-an-existing-environment"></a>Meglévő környezet törlése

Egy környezet tulajdonosaként törölheti azt.

> [!IMPORTANT]
> A környezet törlése nem szünteti meg a környezettel való Dataverse kapcsolatot. Ha azt tervezi, hogy a jövőben ugyanazt Dataverse a környezetet egy új Customer Insights-környezethez csatlakoztatja, el kell [távolítania ezt a kapcsolatot a Dataverse környezettel](customer-insights-dataverse.md#remove-an-existing-connection-to-a-dataverse-environment).

1. Válassza ki az alkalmazás fejlécében a **Környezet** választót.

1. Válassza ki a törölni kívánt környezetet, és válassza ki a függőleges három pontot (&vellip;). 

1. Válassza a Törlés **lehetőséget**.

   :::image type="content" source="media/delete-environment.png" alt-text="A környezet törlésének vezérlése.":::

1. A törlés jóváhagyásához adja meg a környezet nevét, és válassza a **Törlés** lehetőséget.

[!INCLUDE [footer-include](includes/footer-banner.md)]
