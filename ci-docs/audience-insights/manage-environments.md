---
title: A környezetek létrehozása és kezelése
description: Megismerheti, hogyan lehet regisztrálni a szolgáltatásra, és hogyan kezelhetők a környezetek.
ms.date: 02/09/2022
ms.subservice: audience-insights
ms.topic: how-to
ms.reviewer: mhart
author: NimrodMagen
ms.author: nimagen
manager: shellyha
searchScope:
- ci-system-about
- customerInsights
ms.openlocfilehash: 4f4e5a8415f6c2128b0480edf67f317124eeeba9
ms.sourcegitcommit: 50d32a4cab01421a5c3689af789e20857ab009c4
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/03/2022
ms.locfileid: "8376879"
---
# <a name="manage-environments"></a>Környezetek kezelése

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

## <a name="connect-to-microsoft-dataverse"></a>Csatlakozás a Microsoft Dataverse-hoz
   
A **Microsoft Dataverse** lépéssel összekapcsolhatja a Customer Insightsot a Dataverse környezetével.

A [használható előrejelzési modellek](predictions-overview.md#out-of-box-models) használatra konfigurálja az adatok megosztását a Dataverse használatával. Vagy engedélyezheti az adatfeldolgozást a helyszíni adatforrásokból, megadva a szervezet által felügyelt Microsoft Dataverse környezet URL-címét.

> [!IMPORTANT]
> Ügyfélelemzések, és Dataverse az adatmegosztás engedélyezéséhez ugyanabban a régióban kell lennie.

:::image type="content" source="media/dataverse-provisioning.png" alt-text="Konfigurálási lehetőségek az adatmegosztás engedélyezéséhez a Microsoft Dataverse szolgáltatással.":::

> [!NOTE]
> A Customer Insights nem támogatja a következő adatmegosztási forgatókönyveket:
> - Ha az összes adatot a saját Azure Data Lake Storage szolgáltatásához menti, akkor nem tudja engedélyezni az adatmegosztást a kezelt Dataverse-adattóval.
> - Ha engedélyezi az adatmegosztást a Dataverse szolgáltatással, akkor nem fogja tudni [létrehozni az előrejelzett vagy hiányzó értékeket egy entitásban](predictions.md).

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

- A Common Data Model mappából származó adatforrások és a Dataverse használatával kezelt adattó. Ezeket az adatforrásokat manuálisan, ugyanolyan néven kell létrehoznia, mint a forráskörnyezetében.

Környezet másolásakor egy megerősítő üzenet jelenik meg, amely szerint létrejött az új környezet. Válassza az **Ugrás az adatforrásokhoz** lehetőséget az adatforrások listájának megjelenítéséhez.

Minden adatforrásnál megjelenik egy **Hitelesítő adatok szükségesek** állapot. Szerkessze az adatforrásokat, és adja meg a hitelesítő adatokat a frissítésükhöz.

:::image type="content" source="media/data-sources-copied.png" alt-text="A másolt és hitelesítést igényel adatforrások listája.":::

Az adatforrások frissítését követően nyissa meg az **Adatok** > **Egyesítés** pontot. Itt megtalálja a beállításokat a forráskörnyezetből. Igény szerint szerkessze őket, vagy válassza a **Futtatás** lehetőséget az adategyesítési folyamat elindításához, és hozzon létre egy egyesített ügyfélentitást.

Amikor az adatok egyesítése befejeződött, nyissa meg a **Mértékek** és a **Szegmensek** lehetőséget, hogy azokat is frissítse.

## <a name="change-the-owner-of-an-environment"></a>Környezet tulajdonosának megváltoztatása

Bár a Customer Insights szolgáltatásban több felhasználó is rendelkezhet rendszergazdai engedélyekkel, a környezetnek csak egy felhasználó a tulajdonosa. Alapértelmezés szerint kezdetben a rendszergazda hoz létre egy környezetet. A környezet rendszergazdájaként a tulajdonjogot rendszergazdai engedélyekkel rendelkező másik felhasználóhoz is hozzárendelheti.

1. Válassza ki az alkalmazás fejlécében a **Környezet** választót.

1. Kattintson a **Szerkesztés** ikonra.

1. **A Környezet** szerkesztése mezőben nyissa meg az **Alapvető információk** lépést.

1. **A Környezet** tulajdonosának módosítása mezőben válassza ki a környezet új tulajdonosát.  

1. A módosítások alkalmazásához válassza a Véleményezés és befejezés **, majd** a Frissítés **lehetőséget**. 

## <a name="claim-ownership-of-an-environment"></a>Környezet tulajdonjogának követelése

Ha egy környezet tulajdonosa elhagyja a szervezetet, vagy a felhasználói fiókját törlik, a környezetnek nem lesz tulajdonosa. A rendszergazdai engedélyekkel rendelkező felhasználó igényelheti a tulajdonjogot, és új tulajdonossá válhat. Továbbra is birtokolhatják a környezetet, vagy [megváltoztathatják a tulajdonjogot egy másik rendszergazdára](#change-the-owner-of-an-environment). 

A tulajdonjog megszerzéséhez válassza a **Tulajdonjog** átvétele gombot, amely az Ügyfélelemzések minden oldalának tetején jelenik meg, amikor az eredeti tulajdonos elhagyta a szervezetet.

## <a name="reset-an-existing-environment"></a>Meglévő környezet visszaállítása

A környezet tulajdonosaként visszaállíthat egy környezetet üres állapotba, ha törölni szeretné az összes konfigurációt, és el szeretné távolítani a betöltött adatokat.

1.  Válassza ki az alkalmazás fejlécében a **Környezet** választót. 

2.  Válassza ki az alaphelyzetbe állítani kívánt környezetet, és válassza ki a három pontot (**...**). 

3. Válassza az **Alaphelyzetbe állítás** lehetőséget. 

4.  A törlés jóváhagyásához írja be a környezet nevét, és válassza az **Alaphelyzetbe állítás** lehetőséget.

## <a name="delete-an-existing-environment"></a>Meglévő környezet törlése

A környezet tulajdonosaként törölheti az Ön által felügyelt környezetet.

1.  Válassza ki az alkalmazás fejlécében a **Környezet** választót.

2.  Válassza ki az alaphelyzetbe állítani kívánt környezetet, és válassza ki a három pontot (**...**). 

3. Válassza a **Törlés** lehetőséget. 

4.  A törlés jóváhagyásához adja meg a környezet nevét, és válassza a **Törlés** lehetőséget.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
