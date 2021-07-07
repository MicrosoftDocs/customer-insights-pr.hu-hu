---
title: A környezetek létrehozása és kezelése
description: Megismerheti, hogyan lehet regisztrálni a szolgáltatásra, és hogyan kezelhetők a környezetek.
ms.date: 06/15/2021
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
ms.reviewer: mhart
author: NimrodMagen
ms.author: nimagen
manager: shellyha
ms.openlocfilehash: 904ce68336cba4b7a4d5a37692b72d091400559d
ms.sourcegitcommit: d84d664e67f263bfeb741154d309088c5101b9c3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/24/2021
ms.locfileid: "6304883"
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

> [!NOTE]
> A szervezetek minden Customer Insights licenchez *két* környezetet hozhatnak létre. Ha a szervezete egynél több licencet vásárol, a rendelkezésre álló környezetek számának növelése érdekében [lépjen kapcsolatba a támogatási csoporttal](https://go.microsoft.com/fwlink/?linkid=2079641). A kapacitással és a bővítménykapacitással kapcsolatos további információkért töltse le a [Dynamics 365 licencelési útmutatóját](https://go.microsoft.com/fwlink/?LinkId=866544).

Környezet létrehozásához:

1. Válassza ki az alkalmazás fejlécében a **Környezet** választót.

1. Válassza az **Új** lehetőséget.

   > [!div class="mx-imgBorder"]
   > ![Környezeti beállítások.](media/environment-settings-dialog.png)

1. A **Környezet létrehozása** párbeszédpanelen válassza az **Új környezet** lehetőséget.

   Ha [az aktuális környezetből szeretne adatot másolni](#considerations-for-copy-configuration-preview), akkor válassza a **Másolás meglévő környezetből** lehetőséget. A szervezetében összes elérhető környezet listáját látja, amelyekből adatokat másolhat.

1. Adja meg a következő részleteket:
   - **Név**: A környezet neve. Ha meglévő környezetből másolt, akkor ez a mező már ki van töltve, de ez módosítható.
   - **Típus**: Adja meg, hogy szeretne-e működési vagy tesztkörnyezetet létrehozni.
   - **Régió**: Az a régió, ahová a szolgáltatást telepítették és üzemeltetik.
   
1. Nem kötelezően kiválaszthatja a **Speciális beállításokat**:

   - **Összes adat mentése ide**: Megadja, hogy hol szeretné tárolni a Customer Insights-ból előállított kimeneti adatait. Két lehetősége lesz: **Ügyfélelemzések tárolása** (a Customer Insights csapat által kezelt Azure Data Lake) és **Azure Data Lake Storage** (saját Azure Data Lake Storage). Alapértelmezés szerint a Customer Insights tárolóhely beállítás van kiválasztva.

     > [!NOTE]
     > Ha adatokat ment az Azure Data Lake Storage tárhelyre azzal elfogadja, hogy az adatok át lesznek víve az Azure tárfióknak megfelelő földrajzi helyre, és ott lesznek tárolva; ez eltérhet attól a helytől, ahol a Dynamics 365 Customer Insights adatai vannak tárolva. [További információ a Microsoft adatvédelmi központról.](https://www.microsoft.com/trust-center)
     >
     > Jelenleg a beolvasott entitások tárolása mindig a Customer Insights által kezelt Managed Data Lake-ben történik. 
     > 
     > Csak az Azure Data Lake Storage fiókokat támogatjuk ugyanabból az Azure-régióból, amelyet a környezet létrehozásakor kiválasztott. 
     > 
     > Csak olyan Azure Data Lake Storage fiókokat támogatunk, amelyeknél engedélyezve van a hierarchikus névtér.


   - A Azure Data Lake Storage beállításhoz választhat az erőforrás-alapú és az előfizetés-alapú hitelesítési lehetőség között. További információkért lásd: [Célközönség-információk összekapcsolása az Azure Data Lake Storage Gen2 fiókjához az Azure egyszerű szolgáltatásnévvel](connect-service-principal.md). A **Tároló** neve nem változtatható meg, és `customerinsights` lesz.
   
   - Ha [előrejelzéseket](predictions.md) szeretne használni, konfigurálja az adatok megosztását a Microsoft Dataverse használatával, vagy engedélyezze a helyszíni környezet adatforrásokból való adatbetöltést, adja meg a Microsoft Dataverse környezet URL-címét az **Adatmegosztás konfigurálása Microsoft Dataverse-szel, és további képességek engedélyezése** alatt. Válassza az **Adatmegosztás engedélyezése** lehetőséget, ha meg szeretné osztani a Customer Insights kimeneti adatait a Microsoft Dataverse Managed Data Lake használatával.

     > [!NOTE]
     > - A Microsoft Dataverse Managed Data Lake használatával való adatmegosztás jelenleg nem támogatott, ha az adatokat a saját Azure Data Lake Storage tárhelyére menti.
     > - [Az entitásból hiányzó értékek előrejelzése](predictions.md) jelenleg nem támogatott, ha engedélyezi az adatok megosztását a Microsoft Dataverse Managed Data Lake használatával.

     > [!div class="mx-imgBorder"]
     > ![Konfigurálási lehetőségek az adatmegosztás engedélyezéséhez a Microsoft Dataverse szolgáltatással.](media/datasharing-with-DataverseMDL.png)

   A folyamatok – például adatbetöltés vagy szegmenslétrehozás – futtatásakor a megfelelő mappák létrejönnek a fent megadott tárfiókban. A rendszer a folyamat neve alapján adatfájlokat és model.json fájlokat hoz létre, és ad hozzá a megfelelőmappákhoz.

   Ha több Customer Insights-környezetet hoz létre, és úgy dönt, hogy menti a kimeneti entitást ezekből a környezetekből a tárfiókba, a rendszer minden környezethez külön mappát hoz létre a tárolóban ci_<environmentid>.

### <a name="considerations-for-copy-configuration-preview"></a>A másolási konfigurációval kapcsolatos szempontok (előzetes verzió)

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
- Adatforrások a Common Data Model mappából és Dataverse a kezelt Data Lake-ből. Ezeket az adatforrásokat manuálisan, ugyanolyan néven kell létrehoznia, mint a forráskörnyezetében.

Környezet másolásakor egy megerősítő üzenet jelenik meg, amely szerint létrejött az új környezet. Válassza az **Ugrás az adatforrásokhoz** lehetőséget az adatforrások listájának megjelenítéséhez.

Minden adatforrásnál megjelenik egy **Hitelesítő adatok szükségesek** állapot. Szerkessze az adatforrásokat, és adja meg a hitelesítő adatokat a frissítésükhöz.

> [!div class="mx-imgBorder"]
> ![Másolt adatforrások.](media/data-sources-copied.png)

Az adatforrások frissítését követően nyissa meg az **Adatok** > **Egyesítés** pontot. Itt megtalálja a beállításokat a forráskörnyezetből. Igény szerint szerkessze őket, vagy válassza a **Futtatás** lehetőséget az adategyesítési folyamat elindításához, és hozzon létre egy egyesített ügyfélentitást.

Amikor az adatok egyesítése befejeződött, nyissa meg a **Mértékek** és a **Szegmensek** lehetőséget, hogy azokat is frissítse.

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
   > - [Entitásból hiányzó értékek előrejelzése](predictions.md) jelenleg nem támogatott, ha engedélyezi az adatok megosztását a Microsoft Dataverse Managed Data Lake szolgáltatással.

   Miután engedélyezi az adatok megosztását a Microsoft Dataverse-szel, az adatforrások és más folyamatok egyszeri teljes frissítése elkezdődik. Ha folyamatok futnak és, akkor nem fogja látni a lehetőséget, amelltel engedélyezhetné az adatok megosztását a Microsoft Dataverse-szel. Az adatmegosztás engedélyezéséhez várja meg, amíg befejeződnek vagy visszavonják ezeket a folyamatokat. 
   
   :::image type="content" source="media/datasharing-with-DataverseMDL.png" alt-text="Konfigurálási lehetőségek az adatmegosztás engedélyezéséhez a Microsoft Dataverse szolgáltatással.":::
   
   A folyamatok – például adatbetöltés vagy szegmenslétrehozás – futtatásakor a megfelelő mappák létrejönnek a fent megadott tárfiókban. A rendszer a futtatott folyamattól függően adatfájlokat és model.json fájlokat hoz létre, és ad hozzá a megfelelő almappákhoz.

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
