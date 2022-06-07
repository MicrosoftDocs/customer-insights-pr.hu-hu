---
title: Részleges adatok kitöltése előrejelzések használatával
description: Az előrejelzések segítségével töltse ki a hiányos ügyféladatokat.
ms.date: 11/01/2021
ms.subservice: audience-insights
ms.topic: how-to
author: zacookmsft
ms.author: zacook
ms.reviewer: mhart
manager: shellyha
searchScope:
- ci-predictions
- ci-custom-models
- customerInsights
ms.openlocfilehash: 57ef46416db0a11cde9f9d7650a0b502a01bf0ab
ms.sourcegitcommit: b515120bebd2638f2639004422cee3cff42fbdf7
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/24/2022
ms.locfileid: "8800653"
---
# <a name="complete-your-partial-data-with-predictions-deprecated"></a>Töltse ki részleges adatait előrejelzésekkel (elavult)

> [!IMPORTANT]
> Ez a **funkció 2021. november 5-től** elavult **lesz**. A jelenlegi implementációk a funkció eltávolításáig továbbra is működnek, de az alábbi utasítások segítségével nem hozhat létre új integrációkat.

Az előrejelzések segítségével egyszerűen hozhat létre olyan előre jelzett értékeket, amelyek segíthetik az ügyfél megértését. Az **Információk** > **Előrejelzések** lapon kiválaszthatja a **Saját előrejelzések** lehetőséget, hogy megtekintse a Customer Insights egyéb részein konfigurált előrejelzéseket, és lehetősége legyen azok további testreszabására.

> [!NOTE]
> Ez a funkció nem használható, ha a környezet Azure Data Lake Gen 2 tárhelyet használ.
>
> Az előrejelzések funkció automatizált eszközöket használ az adatok értékelésére és az előrejelzések készítésére az adott adatok alapján, és így képes a profilkészítési módszerként használni, abban az értelemben, ahogy ezt a kifejezést az általános adatvédelmi rendelet ("GDPR") meghatározza. Ha az ügyfél ezt a funkciót adatok feldolgozására használja, az a GDPR vagy más törvények és szabályozások hatálya alá tartozhat. Felelős azért, hogy biztosítsa, hogy a Dynamics 365 Customer Insights használata, az előrejelzésekkel együtt, megfelel a vonatkozó törvényeknek és szabályozásoknak, többek között az adatvédelemmel, személyes adatokkal, biometrikus adatokkal, adatok védelmével és a kommunikáció titkosságával kapcsolatos törvényeknek.

## <a name="prerequisites"></a>Előfeltételek

Ahhoz, hogy a szervezet használni tudja az Előrejelzések funkciót, gondoskodjon arról, hogy a következő előfeltételek teljesüljenek:

1. A szervezete rendelkezik egy példánnyal [beállítva a Microsoft Dataverse-ben](/ai-builder/build-model#prerequisites), amely ugyanabban a szervezetben található, mint a Customer Insights.

2. Customer Insights-környezete össze van kapcsolva a Dataverse-példánnyal.

További információ: [Új környezet létrehozása](create-environment.md).

## <a name="create-a-prediction-in-the-customer-entity"></a>Előrejelzés létrehozása az ügyfél entitásban

1. Nyissa meg az **adat entitásokat** > **·**.

2. Válassza az **Ügyfél** entitást.

3. Az **Ügyfél: CustomerInsights** entitásban válassza a **Mezők** lapot.

4. Keresse meg azt az attribútumot, amelyhez előre szeretné jelezni az értékeket, és válassza az **Áttekintés** ikont az **Összesítés** oszlopban.
   > [!div class="mx-imgBorder"]
   > ![Áttekintés ikon.](media/intelligence-overviewicon.png "Áttekintés ikon")

5. Ha az attribútumhoz nagy a hiányzó értékek aránya, akkor az előrejelzés folytatásához válassza a **Hiányzó értékek előrejelzése** lehetőséget.
   > [!div class="mx-imgBorder"]
   > ![Áttekintési állapot, ahol a hiányzó értékek előrejelzése gomb látható.](media/intelligence-overviewpredictmissingvalues.png "Áttekintési állapot, ahol a hiányzó értékek előrejelzése gomb látható")

6. Adja meg a **Megjelenítendő név** és a **Kimeneti entitás neve** értékét az előrejelzés eredményéhez.

7. Megjelenik a lehetőségek előre kitöltött listája, ahol az értékeket egy előre jelzett kategóriához rendelheti. Ebben az esetben az egyetlen kategórialehetőségek a 0 vagy az 1, mivel az előrejelzés igaz/hamis vagy bináris jellegével lesznek megfeleltetve. A Kategória oszlopban azokat a mezőértékeket, amelyeket a végső előrejelzésben „0” értékkel szeretne besorolni, feleltesse meg a „0” értékkel, a végső előrejelzésben „1” értékkel besorolandó elemeket pedig az „1” értékkel.
   > [!div class="mx-imgBorder"]
   > ![Példa, amelyen kategóriákkal megfeleltetett mezőértékek láthatók.](media/intelligence-categorymapping.png "Példa, amelyen kategóriákkal megfeleltetett mezőértékek láthatók")

8. Válassza a **Kész** lehetőséget, és a rendszer feldolgozza az előrejelzést. A feldolgozás egy kis időt vesz igénbe, az adatok méretétől és összetettségétől függően. Az eredmények egy új entitásban lesznek elérhetők a létrehozott előrejelzés **Kimeneti entitásának neve** alapján.

[!INCLUDE [progress-details-include](includes/progress-details-pane.md)]

## <a name="create-a-prediction-while-creating-a-segment"></a>Előrejelzés létrehozása a szegmens létrehozásakor

A kiválasztott attribútumok hiányzó értékeinek előrejelzése a szegmens létrehozásakor is lehetséges. Különösen, amikor gyorsan létrehoz egy szegmenst az egyesített Ügyfél entitás vagy a Customer_Measure entitás alapján.

Az adott folyamat részeként kiválaszthat egy specifikus attribútumot, amin alapulhat a szegmens, például Ügyfél-elégedettség, Vásárlás összege. A szegmens létrehozásakor a rendszer javaslatot tesz az attribútum hiányzó értékeinek előrejelzésére.

1. Nyissa meg a Szegmensek lehetőséget, **és** válassza a **Profilok** csempét.

2. A **Mező** pont kiválasztásával hozzon létre egy szegmenst, és válassza ki az **Operátor** elemet, majd a **Felülvizsgálat** lehetőséget.

3. Adja meg a **Név** és a **Megjelenítendő név** értékét a szegmenshez.

4. Válassza a **Mentés** parancsot.

5. Ha a létrehozott szegmensben hiányos adatok szerepelnek a Forrás mezőben, dönthet úgy, hogy előre jelzi a hiányzó értékeket.
   > [!div class="mx-imgBorder"]
   > ![Előrejelzés gomb.](media/segments-predictoption.png "Előrejelzés gomb")

6. Adja meg a **Megjelenítendő név** és a **Kimeneti entitás neve** értékét az előrejelzés eredményéhez.

7. Válassza a **Kész** lehetőséget. Az előrejelzés hamarosan létrejön egy új entitásban, amelynek neve a **Kimeneti entitás neve** mezőben megadott név.

## <a name="view-a-prediction"></a>Előrejelzés megtekintése

1. Ugrás az **Intelligencia** > **előrejelzések** > **saját jóslatok**.

2. Jelölje ki az áttekinteni kívánt előrejelzést.

3. Jelölje ki a függőleges ellipszis (&vellip;) pontot a Műveletek **oszlopban, és válassza a** Nézet **lehetőséget**.

4. Az előrejelzés nézetében számos adatpont jelenik meg.
   > [!div class="mx-imgBorder"]
   > ![Előrejelzések oldala.](media/intelligence-predictionsviewpage.png "Előrejelzések oldala")

   - **Előre jelzett értékek** bemutatja a Mező értékének a Kategóriával való megfeleltetési fázis során létrehozott megfeleltetését. Ezek az adathalmaz azon értékeit, amelyek egy adott kategóriára vannak leképezve.
   -**Legfontosabb befolyásolók** az adathalmaz olyan tényezői, amelyek nagy valószínűséggel befolyásolják a Mező értékének egy adott kategóriára való leképezésére vonatkozó előrejelzés konfidenciáját.
   - A **teljesítmény** jelzi az előrejelzések előrehaladását. További tudnivalókért válassza a hivatkozást.
   - Az **előnézet** mintákat mutat be az előrejelzés kimeneti adathalmazából, valamint az előre jelzett érték valószínűségét, azaz konfidenciáját, ahol 0 a bizonytalan és az 1 a biztos érték.

## <a name="update-a-prediction"></a>Előrejelzés frissítése

1. Ugrás az **Intelligencia** > **előrejelzések** > **saját jóslatok**.

2. Válassza ki a frissíteni kívánt előrejelzést, és válassza a **Frissítés** ikont.

3. A rendszer feldolgozásra ütemezi a előrejelzést. Megtekintheti az utolsó frissítés időpontját a **Frissítve** oszlopban, az **Előrejelzések** oldalon.

## <a name="edit-a-prediction"></a>Előrejelzés szerkesztése

Miután létrehozott egy előrejelzés, testreszabhatja a modellt a AI Builder modell hatékonyságának növelése érdekében.  

1. Ugrás az **Intelligencia** > **előrejelzések** > **saját jóslatok**.

2. Válassza ki a szerkeszteni kívánt előrejelzést.

3. Jelölje ki a függőleges ellipszis (&vellip;) pontot a Műveletek **oszlopban, és válassza a** Nézet **lehetőséget**.

4. Válassza **a Testreszabás lehetőséget a alkalmazásban AI Builder**.

5. Frissítse a modellt a AI Builder alkalmazásban. [További információ az AI Builderben található modellek kezeléséről](/ai-builder/manage-model#retrain-and-republish-existing-models).

Az előrejelzés következő futtatása a létrehozott frissített modellt fogja használni.

> [!NOTE]
> A létrehozott AI Builder új modellek csak akkor jelennek meg a Customer Insights alkalmazásban, ha a modellt a fent felsorolt tapasztalatok alapján hozták létre.

## <a name="remove-a-prediction"></a>Előrejelzés eltávolítása

1. Ugrás az **Intelligencia** > **előrejelzések** > **saját jóslatok**.

2. Jelölje ki a törlendő előrejelzést.

3. Jelölje ki a függőleges ellipszis (&vellip;) elemet a Műveletek **oszlopban, és válassza a** Törlés **lehetőséget**.

4. Törlés jóváhagyása.

## <a name="troubleshooting"></a>Hibaelhárítás

Ha hiba miatt nem tudja elvégezni a csatolási Dataverse folyamatot, megpróbálhatja manuálisan végrehajtani. A csatolási folyamat során két ismert probléma is előfordulhat:

- Nincs telepítve az Ügyfélkártya bővítmény megoldás.
    1. Hajtsa végre a [megoldás telepítésére és konfigurálására vonatkozó](customer-card-add-in.md) utasításokat.

- Az alkalmazásengedélyek nincsenek megadva.
    1. Menjen a [https://admin.powerplatform.microsoft.com](https://admin.powerplatform.microsoft.com) felületre.
    1. **Környezetek** kiválasztása.
    1. Jelölje ki a függőleges ellipszis (&vellip;) mellett a környezet mellett, amelyhez hozzá szeretné adni az engedélyt, és válassza a Beállítások **lehetőséget**.
    1. Bontsa ki a **Felhasználók + engedélyek** elemet, és válassza a **Felhasználók** elemet.
    1. Válassza az **+ Új** lehetőséget , és válassza a **Felhasználó** lehetőséget.
    1. Válassza az **Alkalmazásfelhasználó** elemt, ha még nincs kijelölve, és adja meg a következő adatokat:
        - **Felhasználónév:** cihelp@microsoft.com
        - **Alkalmazás azonosítója:** 38c77d00-5fcb-4cce-9d93-af4738258e3c
        - **Utónév:** Customer
        - **Vezetéknév:** Insights
        - **Elsődleges e-mail cím:** cihelp@microsoft.com
    1. Válassza a **Mentés és bezárás** lehetőséget.
    1. Jelölje ki a létrehozott felhasználókat.
    1. Válassza a **Szerepkörök kezelése** lehetőséget a felső menüsávon.
    1. Válassza a **Rendszergazda** lehetőséget, majd kattintson az **OK** gombra.


[!INCLUDE [footer-include](includes/footer-banner.md)]
