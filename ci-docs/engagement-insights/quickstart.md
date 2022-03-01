---
title: A termék gyors üzembe helyezésének bemutatása
description: Első alkalommal futtatott élmény az aktivitási információk szolgáltatás beállításával.
author: mochimochi016
ms.reviewer: mhart
ms.author: jefhar
ms.date: 11/05/2020
ms.service: customer-insights
ms.subservice: engagement-insights
ms.topic: conceptual
ms.manager: shellyha
ms.openlocfilehash: eebe51d343f6afbed52a66c52ab6a60eb5cd410367fb2e4409eb8679f357c91e
ms.sourcegitcommit: aa0cfbf6240a9f560e3131bdec63e051a8786dd4
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/10/2021
ms.locfileid: "7033910"
---
# <a name="first-run-experience"></a>Első tapasztalat

[!INCLUDE [cc-beta-prerelease-disclaimer](includes/cc-beta-prerelease-disclaimer.md)]

Az Dynamics 365 Customer Insights aktivitási információk szolgáltatásának segítségével összegyűjtheti és lemérheti az ügyfelek viselkedését a webhelyén. Ez a cikk azt ismerteti, hogyan regisztrálhat az aktivitási információk szolgáltatásra, állíthat be munkaterületet, adhat hozzá tagokat, és hogyan módosíthat.

## <a name="sign-up-for-a-demo-of-engagement-insights"></a>Feliratkozás az aktivitási információk bemutatóra

Aktív Microsoft Azure Active Directory-felhasználói fiókkal kell lennie. 

1. Nyissa meg az [aktivitási információk](https://pi.dynamics.com/) webhelyet. 

1. Bejelentkezés iskolai vagy munkahelyi fiókkal.

1. Válassza ki a régiót, és a jelölőnégyzet bejelölésével jelezze, hogy be szeretné-e fogadni e-mailben frissítéseket és ajánlatokat.

1. Tekintse át az **aktivitási információk (előzetes verzió) használati feltételeit** és **adatvédelmi nyilatkozatát**, majd válassza a **Demó megtekintése** lehetőséget az elfogadásukhoz.

1. Fedezze fel a terméket egy sor mintaadat segítségével. 

## <a name="set-up-your-first-workspace-in-engagement-insights"></a>Első munkaterület beállítása az aktivitási információk szolgáltatásban

A munkaterület biztosít módot arra, hogy tárolja és kezelje az eseményeket és jelentéseket.

Az első saját munkaterület létrehozásához

1. Az aktivitási információk szolgáltatásban válassza az **Adatok összekapcsolása** lehetőséget a varázsló indításhoz. 

:::image type="content" source="media/banner.png" alt-text="Customer Insights oldal az adatok összekapcsolása gombbal.":::

2. Válassza ki az új munkaterületen mérni kívánt tevékenységtípust. Jelenleg csak a **Webhelytevékenység** érhető el. Az **Alkalmazástevékenység** és az **Eszköztevékenység** a jövőben elérhetővé válik.

1. A munkaterület megerősítéséhez és létrehozásához válassza a **Tovább** lehetőséget.

1. Vegyen fel egy kódrészletet, hogy elindítsa az adatok fogadását az aktivitási információk szolgáltatásban. Ezt azonnal végrehajthatja, vagy megoszthatja a kódot és az utasításokat a webhely rendszergazdájával. A kódrészletet később a **Felügyelet** > **Munkaterület** > **Telepítési útmutató** pontban találhatja meg.

   > [!IMPORTANT]
   > Az adatok mindaddig nem fognak a munkaterületen megjelenni, amíg nem alkalmazzák a kódot a webhelyén.

1. Az új munkaterület megnyitásához válassza a **Kész** lehetőséget. 

## <a name="add-members-to-an-existing-workspace"></a>Tagok hozzáadása meglévő munkaterülethez

Alapértelmezés szerint csak a munkaterületet létrehozó személy fér hozzá. Bármikor hozzáadhat más felhasználókat a szervezetéből egy meglévő munkaterülethez.

:::image type="content" source="media/add-members.png" alt-text="Tagok oldal lehívással a Tagok hozzáadása gombon.":::

1. Lépjen a **Felügyelet** > **Munkaterület** > **Tagok** pontra.

2. Válassza ki a **Tagok hozzáadása** lehetőséget. A **Tagok** mező segítségével vegyen fel másokat a szervezetbe. Egyszerre több tag is felvehető.

3. Válassza ki az új tagokhoz hozzárendelni kívánt **szerepkört**. Jelenleg csak a **Munkaterület-rendszergazda** elérhető kiválasztásra. A későbbi kiadásokban más szerepkörök is bekerülnek.

4. Jelölje ki a megerősítéshez a **Tagok hozzáadása** lehetőséget.

Ha tagokat szeretne eltávolítani a munkaterületről, válassza a **...** a nevük mellett a **Tagok** oldalon, majd válassza a **Törlés** parancsot a legördülő listában.

## <a name="edit-a-workspace"></a>Munkaterület szerkesztése

A meglévő munkaterületek adatait bármikor módosíthatja.

:::image type="content" source="media/change-workspace-settings.png" alt-text="Munkaterület-beállítások oldal lehívással a munkaterület nevével és leírásával.":::

1. Válassza a **Felügyelet** > **Munkaterület** > **Beállítások** lehetőséget.

1. Módosítsa a munkaterület **Nevét**.

1. Válassza a **Mentés** lehetőséget a módosítások alkalmazásához.

## <a name="add-another-new-workspace"></a>További új munkaterület hozzáadása

:::image type="content" source="media/workspace-switcher.png" alt-text="Customer Insights oldal lehívással a navigációs ablaktáblában és leírásban.":::

Az adatok osztályozásához további munkaterületeket is létrehozhat.

1. A munkaterület-választóban válassza az **Új munkaterület** lehetőséget.

1. Adjon meg egy **Nevet** és **Leírást**.

1. Válassza a **Létrehozás** parancsot.

## <a name="switch-between-workspaces"></a>Váltás a munkaterületek között

A munkaterületek közötti váltáshoz válassza ki a munkaterület-átváltót. Új munkaterületet is létrehozhat, illetve a **Webes minta** gombra kiválasztva láthatja a jelentéseket, és mintaadatok segítségével kipróbálhatja a szolgáltatásokat. 



[!INCLUDE[footer-include](../includes/footer-banner.md)]