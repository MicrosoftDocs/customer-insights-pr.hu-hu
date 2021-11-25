---
title: A környezetek létrehozása és kezelése
description: Megismerheti, hogyan lehet regisztrálni a szolgáltatásra, és hogyan kezelhetők a környezetek.
ms.date: 11/12/2021
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
ms.reviewer: mhart
author: NimrodMagen
ms.author: nimagen
manager: shellyha
ms.openlocfilehash: 65c6a68f550c2873ec30c6ac54f1752d880ce12c
ms.sourcegitcommit: fb9f118b4e16b5aabb3e503463efca21718f5d72
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/12/2021
ms.locfileid: "7799639"
---
# <a name="manage-environments"></a>Környezetek kezelése

[!INCLUDE [cc-data-platform-banner](../includes/cc-data-platform-banner.md)]

## <a name="switch-environments"></a>Váltás a környezetek között

A környezet módosításához válassza ki az oldal jobb felső sarkában található **Környezet** vezérlőt.

:::image type="content" source="media/home-page-environment-switcher.png" alt-text="Képernyőkép a környezetváltáshoz használható vezérlőről.":::

A rendszergazdák [létrehozhatnak](create-environment.md) és kezelhetnek környezeteket.

## <a name="edit-an-existing-environment"></a>Egy meglévő környezet szerkesztése

A meglévő környezetek bizonyos részleteit szerkesztheti.

1.  Válassza ki az alkalmazás fejlécében a **Környezet** választót.

2.  Kattintson a **Szerkesztés** ikonra.

3. A **Környezet szerkesztése** mezőben frissítheti a környezet beállításait.

További információ a környezet beállításaival kapcsolatban: [Új környezet létrehozása](create-environment.md).

## <a name="connect-to-microsoft-dataverse"></a>Csatlakozás Microsoft Dataverse
   
A **Microsoft Dataverse lépés lehetővé** teszi, hogy összekapcsolja a Customer Insights-t a Dataverse környezetével.

A beépített előrejelzés modellek használatához [konfigurálja az](predictions-overview.md#out-of-box-models) adatmegosztást Dataverse. Vagy engedélyezheti az adatok betöltését helyszíni adatforrásokból, megadva a szervezet által kezelt Microsoft Dataverse környezet URL-címét. Válassza **az Adatmegosztás engedélyezése lehetőséget** a Customer Insights kimeneti adatainak megosztásához egy Dataverse által felügyelt adattóval.

:::image type="content" source="media/dataverse-data-sharing.png" alt-text="Konfigurációs beállítások az adatok megosztásának engedélyezéséhez Microsoft Dataverse.":::

> [!NOTE]
> A Customer Insights nem támogatja a következő adatmegosztási forgatókönyveket:
> - Ha az összes adatot saját Azure Data Lake Storage menti, nem fogja tudni engedélyezni az adatmegosztást a Dataverse által felügyelt adattóval.
> - Ha engedélyezi az adatmegosztást Dataverse, akkor nem hozhat [létre előrejelzett vagy hiányzó értékeket egy entitásban](predictions.md).

## <a name="copy-the-environment-configuration"></a>Másolja a környezet konfigurációját

Új környezet létrehozásakor megadhatja, hogy a konfigurációt egy meglévő környezetből másolja át. 

:::image type="content" source="media/environment-settings-dialog.png" alt-text="Képernyőkép a beállítási lehetőségekről a környezet beállításaiban.":::

A szervezetében összes elérhető környezet listáját látja, amelyekből adatokat másolhat.

A következő konfigurációbeállítások vannak másolva:

- Betöltött/importált adatforrások
- Adategységesítési (Megfeleltetés/Egyeztetés/Egyesítés) konfiguráció
- Szegmensek
- Mértékek
- Kapcsolatok
- Tevékenységek
- Keresési és szűrőindex
- Exportálási célhelyek
- Ütemezett frissítés
- Bővítések
- Modellkezelés
- Szerepkör-hozzárendelések

A következő adatok *nem* lesznek másolva:

- Ügyfélprofilok.
- Adatforrás hitelesítő adatai. A hitelesítő adatokat meg kell adnia minden adatforráshoz, és manuálisan kell frissítenie az adatforrásokat.

- Adatforrások a Common Data Model mappából és a Dataverse által felügyelt adattóból. Ezeket az adatforrásokat manuálisan, ugyanolyan néven kell létrehoznia, mint a forráskörnyezetében.

Környezet másolásakor egy megerősítő üzenet jelenik meg, amely szerint létrejött az új környezet. Válassza az **Ugrás az adatforrásokhoz** lehetőséget az adatforrások listájának megjelenítéséhez.

Minden adatforrásnál megjelenik egy **Hitelesítő adatok szükségesek** állapot. Szerkessze az adatforrásokat, és adja meg a hitelesítő adatokat a frissítésükhöz.

:::image type="content" source="media/data-sources-copied.png" alt-text="A másolt és hitelesítést igényel adatforrások listája.":::

Az adatforrások frissítését követően nyissa meg az **Adatok** > **Egyesítés** pontot. Itt megtalálja a beállításokat a forráskörnyezetből. Igény szerint szerkessze őket, vagy válassza a **Futtatás** lehetőséget az adategyesítési folyamat elindításához, és hozzon létre egy egyesített ügyfélentitást.

Amikor az adatok egyesítése befejeződött, nyissa meg a **Mértékek** és a **Szegmensek** lehetőséget, hogy azokat is frissítse.

## <a name="reset-an-existing-environment"></a>Meglévő környezet visszaállítása

Rendszergazdaként a környezetet visszaállíthatja üres állapotba, ha szeretné törölni az összes konfigurációt, és eltávolítani a betöltött adatokat.

1.  Válassza ki az alkalmazás fejlécében a **Környezet** választót. 

2.  Válassza ki az alaphelyzetbe állítani kívánt környezetet, és válassza ki a három pontot (**...**). 

3. Válassza az **Alaphelyzetbe állítás** lehetőséget. 

4.  A törlés jóváhagyásához írja be a környezet nevét, és válassza az **Alaphelyzetbe állítás** lehetőséget.

## <a name="delete-an-existing-environment"></a>Meglévő környezet törlése

Rendszergazdaként törölheti az Ön által felügyelt környezetet.

1.  Válassza ki az alkalmazás fejlécében a **Környezet** választót.

2.  Válassza ki az alaphelyzetbe állítani kívánt környezetet, és válassza ki a három pontot (**...**). 

3. Válassza a **Törlés** lehetőséget. 

4.  A törlés jóváhagyásához adja meg a környezet nevét, és válassza a **Törlés** lehetőséget.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
