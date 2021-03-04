---
title: A környezetek létrehozása és kezelése
description: Megismerheti, hogyan lehet regisztrálni a szolgáltatásra, és hogyan kezelhetők a környezetek.
ms.date: 02/01/2021
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
ms.reviewer: nimagen
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: 744f0bcbf5d2700363180f44e38d6dee9bf5df63
ms.sourcegitcommit: 139548f8a2d0f24d54c4a6c404a743eeeb8ef8e0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/15/2021
ms.locfileid: "5270115"
---
# <a name="manage-environments"></a>Környezetek kezelése

[!INCLUDE [cc-data-platform-banner](../includes/cc-data-platform-banner.md)]

Ez a cikk azt mutatja be, hogyan hozhat létre új szervezetet, és hogyan lehet létrehozni egy környezetet.

## <a name="sign-up-and-create-an-organization"></a>Regisztráció és szervezet létrehozása

1. Nyissa meg a [Dynamics 365 Customer Insights](https://dynamics.microsoft.com/ai/customer-insights/) webhelyet.

2. Válassza az **Első lépések** lehetőséget.

3. Válassza ki az előnyben részesített feliratkozási forgatókönyvet, és válassza ki az ahhoz tartozó hivatkozást.

4. Fogadja el a feltételeket, és válassza a **Folytatás** lehetőséget a szervezet létrehozásának megkezdéséhez.

5. A környezet létrehozása után a rendszer átirányítja a [Customer Insights](https://home.ci.ai.dynamics.com) szolgáltatásra.

6. A bemutató környezettel ismerje meg az alkalmazást, vagy hozzon létre egy új környezetet a következő szakasz lépéseinek végrehajtásával.

7. A környezeti beállítások megadása után válassza a **Létrehozás** lehetőséget.

8. A környezet sikeres létrehozása után a rendszer bejelentkezteti a környezetbe.

## <a name="create-an-environment-in-an-existing-organization"></a>Környezet létrehozása meglévő szervezetből

Kétféleképpen hozhat létre új környezetet. MEghatározhat teljesen új konfigurációt, vagy másolhat néhány konfigurációs beállítást egy meglévő környezetből.

Környezet létrehozásához:

1. Válassza ki az alkalmazás fejlécében a **Környezet** választót.

1. Válassza az **Új** lehetőséget.

   > [!div class="mx-imgBorder"]
   > ![Környezeti beállítások](media/environment-settings-dialog.png)

1. Az **új környezet létrehozása** párbeszédpanelen válassza az **új környezet** lehetőséget.

   Ha [az aktuális környezetből szeretne adatot másolni](#additional-considerations-for-copy-configuration-preview), akkor válassza a **Másolás meglévő környezetből** lehetőséget. A szervezetében összes elérhető környezet listáját látja, amelyekből adatokat másolhat.

1. Adja meg a következő részleteket:
   - **Név**: A környezet neve. Ha meglévő környezetből másolt, akkor ez a mező már ki van töltve, de ez módosítható.
   - **Régió**: Az a régió, ahová a szolgáltatást telepítették és üzemeltetik.
   - **Típus**: Adja meg, hogy szeretne-e működési vagy tesztkörnyezetet létrehozni.

2. Nem kötelezően kiválaszthatja a **Speciális beállításokat**:

   - **Összes adat mentése ide**: Megadja, hogy hol szeretné tárolni a Customer Insights-ból előállított kimeneti adatait. Két lehetőség közül választhat **Customer Insights tároló** ( egy Azure Data Lake, amelyet a Customer Insights csapata kezel) és **Azure Data Lake Storage Gen2** (saját Azure Data Lake Storage tárolója). Alapértelmezés szerint a Customer Insights tárolóhely beállítás van kiválasztva.

   > [!NOTE]
   > Ha adatokat ment az Azure Data Lake Storage tárhelyre azzal elfogadja, hogy az adatok át lesznek víve az Azure tárfióknak megfelelő földrajzi helyre, és ott lesznek tárolva; ez eltérhet attól a helytől, ahol a Dynamics 365 Customer Insights adatai vannak tárolva. [További információ a Microsoft adatvédelmi központról.](https://www.microsoft.com/trust-center)
   >
   > Jelenleg a beolvasott entitások tárolása mindig a Customer Insights által kezelt adattóban történik.
   > Csak az Azure Data Lake Gen2 tárfiókokat támogatjuk, amelyek a környezet létrehozásakor kiválasztott Azure-régióból származnak.
   > Csak az Azure Data Lake Gen2 Hierarchical Name Space (HNS) képes tárhelyfiókokat támogatjuk.

   - Az Azure Data Lake Storage Gen2 beállításnál választhat az erőforrás-alapú és az előfizetés-alapú hitelesítés használata között. További információkért lásd: [Célközönség-információk összekapcsolása az Azure Data Lake Storage Gen2 fiókjához az Azure egyszerű szolgáltatásnévvel](connect-service-principal.md). A **Tároló** neve nem módosítható, és "customerinsights" lesz.
   
   - Ha [Előrejelzéseket](predictions.md) szeretne használni, vagy szeretné konfigurálni az adatok megosztását az alkalmazásokkal és megoldásokkal a Microsoft Dataverse alapján, akkor adja meg a Microsoft Dataverse környezet URL-címét a **konfigurálja a Microsoft Dataverse adatmegosztást és engedélyezze a további szolgáltatásokat** alatt. Válassza az **Adatmegosztás engedélyezése** lehetőséget, ha meg szeretné osztani a Customer Insights kimeneti adatait a Microsoft Dataverse Managed Data Lake használatával.

     > [!NOTE]
     > - A Microsoft Dataverse Managed Data Lake használatával való adatmegosztás jelenleg nem támogatott, ha az adatokat a saját Azure Data Lake Storage tárhelyére menti.
     > - [Az entitásból hiányzó értékek előrejelzése](predictions.md) jelenleg nem támogatott, ha engedélyezi az adatok megosztását a Microsoft Dataverse Managed Data Lake használatával.

     > [!div class="mx-imgBorder"]
     > ![Konfigurálási lehetőségek az adatmegosztás engedélyezéséhez a Microsoft Dataverse-szolgáltatással](media/Datasharing-with-DataverseMDL.png)

   A folyamatok – például adatbetöltés vagy szegmenslétrehozás – futtatásakor a megfelelő mappák létrejönnek a fent megadott tárfiókban. Az adatfájlok és a model.json fájlok a futtatott folyamat alapján jönnek létre, és hozzáadódnak a megfelelő almappákhoz.

   Ha több Customer Insights-környezetet hoz létre, és úgy dönt, hogy menti a kimeneti entitást ezekből a környezetekből a tárfiókba, a rendszer minden környezethez külön mappát hoz létre a tárolóban ci_<environmentid>.

### <a name="additional-considerations-for-copy-configuration-preview"></a>A konfiguráció másolásának további szempontjai (előzetes verzió)

A következő konfigurációbeállítások vannak másolva:

- Funkciókonfigurációk
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

A következő konfigurációbeállítások *nincsenek* másolva:

- Ügyfélprofilok.
- Adatforrás hitelesítő adatai. A hitelesítő adatokat meg kell adnia minden adatforráshoz, és manuálisan kell frissítenie az adatforrásokat.
- Adatforrások a Common Data Model mappából és a Common Data Service felügyelt tóból. Ezeket az adatforrásokat manuálisan, ugyanolyan néven kell létrehoznia, mint a forráskörnyezetében.

Környezet másolásakor egy megerősítő üzenet jelenik meg, amely szerint létrejött az új környezet. Válassza az **Ugrás az adatforrásokhoz** lehetőséget az adatforrások listájának megjelenítéséhez.

Minden adatforrásnál megjelenik egy **Hitelesítő adatok szükségesek** állapot. Szerkessze az adatforrásokat, és adja meg a hitelesítő adatokat a frissítésükhöz.

> [!div class="mx-imgBorder"]
> ![Másolt adatforrások](media/data-sources-copied.png)

Az adatforrások frissítését követően nyissa meg az **Adatok** > **Egyesítés** pontot. Itt megtalálja a beállításokat a forráskörnyezetből. Igény szerint szerkessze őket, vagy válassza a **Futtatás** lehetőséget az adategyesítési folyamat elindításához, és hozzon létre egy egyesített ügyfélentitást.

Amikor az adatok egyesítése befejeződött, nyissa meg a **Mértékek** és a **Szegmensek** lehetőséget, hogy azokat is frissítse.

## <a name="edit-an-existing-environment"></a>Egy meglévő környezet szerkesztése

A meglévő környezetek bizonyos részleteit szerkesztheti.

1.  Válassza ki az alkalmazás fejlécében a **Környezet** választót.

2.  Kattintson a **Szerkesztés** ikonra.

3. A **Környezet szerkesztése** mezőben frissítheti a környezet **Megejelenő nevét**, de a **Régió** vagy a **Típus** nem módosítható.

4. Ha egy környezet úgy van beállítva, hogy az Azure Data Lake Storage Gen2-ben tárolja az adatokat, akkor frissítheti a **Fiókkulcsot**. A **partner neve** vagy a **tároló** neve azonban nem módosítható.

5. Lehetőség van arra, hogy a fiókkulcs-alapú kapcsolatot az erőforrás- vagy előfizetés-alapú kapcsolatra is frissítheti. A frissítést követően a frissítés után nem térhet vissza a fiókkulcshoz. További információkért lásd: [Célközönség-információk összekapcsolása az Azure Data Lake Storage Gen2 fiókjához az Azure egyszerű szolgáltatásnévvel](connect-service-principal.md). A kapcsolat frissítésekor a **Tárolóra** vonatkozó információk nem módosíthatók.

## <a name="reset-an-existing-environment"></a>Meglévő környezet visszaállítása

Rendszergazdaként a környezetet visszaállíthatja üres állapotba, ha szeretné törölni az összes konfigurációt, és eltávolítani a betöltött adatokat.

1.  Válassza ki az alkalmazás fejlécében a **Környezet** választót. 

2.  Válassza ki az alaphelyzetbe állítani kívánt környezetet, és válassza ki a három pontot **...**. 

3. Válassza az **Alaphelyzetbe állítás** lehetőséget. 

4.  A törlés jóváhagyásához írja be a környezet nevét, és válassza az **Alaphelyzetbe állítás** lehetőséget.

## <a name="delete-an-existing-environment-available-only-for-admins"></a>Meglévő környezet törlése (csak rendszergazdák számára érhető el)

Rendszergazdaként törölheti az Ön által felügyelt környezetet.

1.  Válassza ki az alkalmazás fejlécében a **Környezet** választót.

2.  Válassza ki az alaphelyzetbe állítani kívánt környezetet, és válassza ki a három pontot **...**. 

3. Válassza a **Törlés** lehetőséget. 

4.  A törlés jóváhagyásához adja meg a környezet nevét, és válassza a **Törlés** lehetőséget.


[!INCLUDE[footer-include](../includes/footer-banner.md)]