---
title: A környezetek létrehozása és kezelése
description: Megismerheti, hogyan lehet regisztrálni a szolgáltatásra, és hogyan kezelhetők a környezetek.
ms.date: 07/22/2021
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
ms.reviewer: mhart
author: NimrodMagen
ms.author: nimagen
manager: shellyha
ms.openlocfilehash: 2f115269b9d07dd118ec18cc48b55de8aea9b5bb
ms.sourcegitcommit: 98267da3f3eddbdfbc89600a7f54e5e664a8f069
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/28/2021
ms.locfileid: "6683476"
---
# <a name="manage-environments"></a>Környezetek kezelése

[!INCLUDE [cc-data-platform-banner](../includes/cc-data-platform-banner.md)]

## <a name="switch-environments"></a>Váltás a környezetek között

A környezet módosításához válassza ki az oldal jobb felső sarkában található **Környezet** vezérlőt.

:::image type="content" source="media/home-page-environment-switcher.png" alt-text="Képernyőkép a környezetváltáshoz használható vezérlőről.":::

A rendszergazdák [létrehozhatnak](get-started-paid.md) és kezelhetnek környezeteket.

## <a name="edit-an-existing-environment"></a>Egy meglévő környezet szerkesztése

A meglévő környezetek bizonyos részleteit szerkesztheti.

1.  Válassza ki az alkalmazás fejlécében a **Környezet** választót.

2.  Kattintson a **Szerkesztés** ikonra.

3. A **Környezet szerkesztése** mezőben frissítheti a környezet **Megejelenő nevét**, de a **Régió** vagy a **Típus** nem módosítható.

4. Ha egy környezet úgy van beállítva, hogy adatokat Azure Data Lake Storage -ban tároljon, frissítheti a **Fiókkulcs** billentyűt. A **partner neve** vagy a **tároló** neve azonban nem módosítható.

5. Lehetőség van arra, hogy a fiókkulcs-alapú kapcsolatot az erőforrás- vagy előfizetés-alapú kapcsolatra is frissítheti. A frissítést követően a frissítés után nem térhet vissza a fiókkulcshoz. További információkért lásd: [Célközönség-információk összekapcsolása az Azure Data Lake Storage Gen2 fiókjához az Azure egyszerű szolgáltatásnévvel](connect-service-principal.md). A kapcsolat frissítésekor a **Tárolóra** vonatkozó információk nem módosíthatók.

6. Tetszés szerint megadhat egy Microsoft Dataverse környezet URL-címet az **Adatok megosztásának konfigurálása Microsoft Dataverseszel, és további képességek engedélyezése** alatt. Ezek a lehetőségek olyan alkalmazások és megoldások használatával való adatmegosztásra használhatók, amelyek Microsoft Dataverse-en, helyszíni adatforrásból származó adatokon vagy a használat [előrejelzéseken](predictions.md) alapulnak. Válassza az **Adatmegosztás engedélyezése** lehetőséget, ha meg szeretné osztani a Customer Insights kimeneti adatait a Microsoft Dataverse Managed Data Lake használatával.

   > [!NOTE]
   > - A Microsoft Dataverse Managed Data Lake használatával való adatmegosztás jelenleg nem támogatott, ha az adatokat a saját Azure Data Lake Storage tárhelyére menti.
   > - [Hiányzó értékek becslése entitásban](predictions.md) és a PowerBi beágyazott jelentések a célközönség információkban (amennyiben engedélyezve vannak a környezetben) jelenleg nem támogatottak, ha engedélyezi az adatmegosztást a Microsoft Dataverse felügyelt adattóval.

   Miután engedélyezi az adatok megosztását a Microsoft Dataverse-szel, az adatforrások és más folyamatok egyszeri teljes frissítése elkezdődik. Ha folyamatok futnak és, akkor nem fogja látni a lehetőséget, amelltel engedélyezhetné az adatok megosztását a Microsoft Dataverse-szel. Az adatmegosztás engedélyezéséhez várja meg, amíg befejeződnek vagy visszavonják ezeket a folyamatokat. 
   
   :::image type="content" source="media/datasharing-with-DataverseMDL.png" alt-text="Konfigurálási lehetőségek az adatmegosztás engedélyezéséhez a Microsoft Dataverse szolgáltatással.":::
   
   A folyamatok – például adatbetöltés vagy szegmenslétrehozás – futtatásakor a megfelelő mappák létrejönnek a fent megadott tárfiókban. A rendszer a futtatott folyamattól függően adatfájlokat és model.json fájlokat hoz létre, és ad hozzá a megfelelő almappákhoz.

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
- Adatforrások a Common Data Model mappából és Dataverse a kezelt Data Lake-ből. Ezeket az adatforrásokat manuálisan, ugyanolyan néven kell létrehoznia, mint a forráskörnyezetében.

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
