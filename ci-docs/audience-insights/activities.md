---
title: Ügyféltevékenységek
description: Az ügyféltevékenységek definiálása és a megtekintése az ügyfelek idővonalában.
ms.date: 10/13/2020
ms.service: customer-insights
ms.subservice: audience-insights
ms.reviewer: adkuppa
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: dcef8f0547009e1488f1abe91423fa0bf5b061de
ms.sourcegitcommit: 139548f8a2d0f24d54c4a6c404a743eeeb8ef8e0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/15/2021
ms.locfileid: "5267435"
---
# <a name="customer-activities"></a>Ügyféltevékenységek

Az ügyféltevékenységeket kombinálja a [különböző adatforrásokból](data-sources.md) a Dynamics 365 Customer Insights-ban olyan ügyfélidővonal létrehozásához, amely a tevékenységeket időrendi sorrendben sorolja fel. Az idővonalat alkalmazhat Dynamics 365 az ügyfélkapcsolati alkalmazásaiban az [Ügyfélkártya bővítmény](customer-card-add-in.md) vagy a Power BI irányítópult segítségével.

## <a name="define-an-activity"></a>Egy tevékenység definiálása

Az adatforrások több adatforrásból származó, tranzakciós és tevékenységi adatokkal rendelkező entitásokat tartalmaznak. Azonosítsa ezeket az entitásokat, és jelölje ki az ügyfél idővonalán megtekinteni kívánt tevékenységeket. Válassza ki azt az entitást, amely a cél tevékenységet vagy tevékenységeket tartalmazza.

1. A célközönség információin belül nyissa meg a következőt: **Adatok** > **Tevékenységek**.

1. Válassza a **Tevékenység hozzáadása** lehetőséget.

   > [!NOTE]
   > Egy entitásben legalább egy **Dátum** típusú attribútumnak szerepelnie kell, hogy az bekerüljön az ügyfél idővonalába, és nem lehet entitásokat felvenni **Dátum** mezők nélkül. A **Tevékenység hozzáadása** vezérlő le van tiltva, ha nem talál ilyen entitást.

1. A **Tevékenység hozzáadása** ablaktáblában adja meg a következő mezők értékeit:

   - **Entitás**: Jelöljön ki egy entitást, amely tranzakciós vagy tevékenységi adatot tartalmaz.
   - **Elsődleges kulcs**: Válassza ki azt a mezőt, amely egyértelműen azonosítja a rekordot. Nem tartalmazhat ismétlődő értékeket, üres értékeket vagy hiányzó értékeket.
   - **Időbélyegző**: Válassza ki azt a mezőt, amely a tevékenység kezdési időpontját jelzi.
   - **Esemény**: Válassza ki azt a mezőt, amely a tevékenységhez tartozó esemény.
   - **Internetcím**: Válassza ki azt a mezőt, amely a tevékenységre vonatkozóan további információkat tartalmazó URL-címet jelent. Például a tevékenység forrását jelentő tranzakciós rendszer. Ez az URL-cím az adatforrás tetszőleges mezője lehet, vagy Power Query átalakítást használó új mezőként lehet kialakítani. Ez az URL-cím az egyesített tevékenység entitásban tárolódik, amelyet lefelé irányulóan az API-k használatával lehet használni.
   - **Részletek**: Tetszés szerint jelölje ki a további részletekért hozzáadott mezőt.
   - **Ikon**: Tetszés szerint jelölje ki a tevékenységet jelképező ikont.
   - **Tevékenység típusa**: Adja meg a tevékenységtípus hivatkozását a Common Data Modelhez, amely a legjobban leírja a művelet szemantikai meghatározását.

1. A **Kapcsolat beállítása** szakaszban állítsa be a részleteket, hogy a tevékenység adatait a megfelelő ügyfélhez csatlakoztassa.

    - **Tevékenység entitás mezője**: Jelölje ki a tevékenység entitásban egy másik entitással fennálló kapcsolat létesítéséhez használandó mezőt.
    - **Ügyfél entitás**: Válassza ki a megfelelő forrás ügyfélentitást, amellyel a tevékenység entitása kapcsolatban lesz. Csak az adategyesítési folyamat során használt forrás ügyfél-entitásokhoz kapcsolódhat.
    - **Ügyfél entitás mezője**: Ez a mező mutatja a forrás ügyfél entitás elsődleges kulcsát a leképezési folyamatban kiválasztottként. A forrás ügyfél entitásban ez az elsődlegeskulcs-mező a tevékenység entitással fennálló kapcsolat létrehozására használt.
    - **Név**: Ha a tevékenység entitás és a kiválasztott forrásoldali ügyfél entitás között már létezik kapcsolat, a kapcsolat neve írásvédett módban lesz. Ha nincs ilyen kapcsolat, akkor létrejön egy új kapcsolat az itt megadott néven.
   
   > [!div class="mx-imgBorder"]
   > ![Definiálja az entitás kapcsolatát](media/activities-entities-define.png "Definiálja az entitás kapcsolatát")

1. Válassza a **Mentés** lehetőséget a módosítások alkalmazásához.

1. A **Tevékenységek** lapon válassza a **Futtatás** lehetőséget.

> [!TIP]
> A feladatokhoz/folyamatokhoz [hatféle állapot](system.md#status-types) tartozhat. Emellett a legtöbb folyamat [más alsóbb szintű folyamatoktól is függ](system.md#refresh-policies). Kiválaszthatja egy folyamat állapotát, és megtekintheti a hozzá tartozó teljes feladat folyamatának részleteit. Miután kiválasztotta a **Részletek megtekintése** lehetőséget a feladat egyik feladatához, további információk jelennek meg: feldolgozási idő, legutóbbi feldolgozás dátuma, és a feladathoz társított összes hiba és figyelmeztetés.

## <a name="edit-an-activity"></a>Tevékenység szerkesztése

1. A célközönség információin belül nyissa meg a következőt: **Adatok** > **Tevékenységek**.

2. Keresse meg a szerkeszteni kívánt tevékenységentitást, és válassza a **Szerkesztés** lehetőséget. Másik lehetőségként az egérmutatót az entitás sorára helyezheti, és kiválaszthatja a **Szerkesztés** ikont.

3. Kattintson a **Szerkesztés** ikonra.

4. A **Tevékenység szerkesztése** ablaktáblában frissítse az értékeket, és válassza a **Mentés** lehetőséget.

5. A **Tevékenységek** lapon válassza a **Futtatás** lehetőséget.

## <a name="delete-an-activity"></a>Tevékenység törlése

1. A célközönség információin belül nyissa meg a következőt: **Adatok** > **Tevékenységek**.

2. Keresse meg az eltávolítani kívánt tevékenységentitást, és válassza a **Törlés** lehetőséget. Másik lehetőségként az egérmutatót az entitás sorára helyezheti, és kiválaszthatja a **Törlés** ikont. Emellett több tevékenységentitás is kijelölhető, amelyet egyszerre kell törölni.
   > [!div class="mx-imgBorder"]
   > ![Az entitáskapcsolatok szerkesztése vagy törlése](media/activities-entities-edit-delete.png "Az entitáskapcsolatok szerkesztése vagy törlése")

3. **Törlés** ikon kiválasztása.

4. Hagyja jóvá a törlést.


[!INCLUDE[footer-include](../includes/footer-banner.md)]