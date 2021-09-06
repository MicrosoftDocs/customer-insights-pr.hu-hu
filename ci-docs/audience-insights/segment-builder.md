---
title: Szegmensek létrehozása és kezelése
description: Hozzon létre ügyfelekből álló szegmenseket, és csoportosítsa őket különböző attribútumok alapján.
ms.date: 07/18/2021
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: JimsonChalissery
ms.author: jimsonc
ms.reviewer: mhart
manager: shellyha
ms.openlocfilehash: e759872643cc7387cf732d73c7a320ae8901e5a9
ms.sourcegitcommit: 42692a815695b9fdc93b9358eae09f2c3e97293c
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/13/2021
ms.locfileid: "7377791"
---
# <a name="create-and-manage-segments"></a>Szegmensek létrehozása és kezelése

> [!IMPORTANT]
> 2021 szeptemberében számos változás várható a szegmensek létrehozási folyamatában: 
> - A szegmensszerkesztő kissé eltérő lesz az újratervezett elemekkel és a továbbfejlesztett felhasználói folyamattal.
> - A szegmensszerkesztőben engedélyezve vannak az új dátumidő-operátorok és a továbbfejlesztett dátumválasztó.
> - A szegmensekbe felvehet feltételeket és szabályokat, illetve el is távolíthatja azokat. 
> - Elérhetővé válnak a VAGY feltétellel kezdődő egymásba ágyazott szabályok. Már nincs szükség ÉS feltételre a legkülső rétegben.
> - Az attribútumok kiválasztására használható oldalsó panel folyamatosan elérhető lesz.
> - Az entitáskapcsolatok elérési útjainak kiválasztására vonatkozó lehetőség.
> Az új szegmensszerkesztő kipróbálásához küldjön „Request to enable the new segment builder” tárggyal e-mail a cihelp [at] microsoft.com címre. Tűntesse fel a szervezete nevét és a tesztkörnyezet azonosítóját.
> :::image type="content" source="media/segment-builder-overview.png" alt-text="A szegmensszerkesztő elemei." lightbox="media/segment-builder-overview.png":::
>
> 1 . A szegmens rendszerezése szabályok és alszabályok szerint. Minden szabály vagy alszabály feltételekből áll. A feltételeket logikai operátorokkal egyesítése
>
> 2 . Válassza ki a szabályra vonatkozó entitások közötti [kapcsolati elérési utat](relationships.md). A kapcsolati elérési út határozza meg, hogy mely attribútumok használhatók egy feltételben.
>
> 3 – Szabályok és alszabályok kezelése. Szabály pozíciójának módosítása vagy törlése.
>
> 4 . Feltételek hozzáadása és a megfelelő szintű egymásba ágyazás kiépítése az alszabályokkal.
>
> 5 – Halmaz-műveletek alkalmazása a csatlakoztatott szabályokra.
>
> 6 – Az attribútumpanel használható entitásattribútumok hozzáadására vagy attribútumok alapján feltételek létrehozására. Az ablaktáblán a kijelölt szabály számára elérhető entitások és attribútumok listája látható a kijelölt kapcsolati útvonal alapján.
>
> 7 – Attribútumon alapuló feltételek hozzáadása a meglévő szabályokhoz és alszabályokhoz, illetve új szabályhoz.
>
> 8 – A változtatások visszavonása és ismétlése a szegmens létrehozása közben.

Összetett szűrőket definiálhat az egyesített ügyfélentitás és a kapcsolódó entitások körül. A feldolgozást követően minden szegmens létrehoz egy csoport olyan ügyfélrekordot, amellyel az exportálás után műveletek végezhetők. A szegmensek kezelése a **Szegmensek** oldalon történik. 

A következő példa bemutatja a szegmentációs képességet. Egy szegmenst definiáltak azokhoz az ügyfelekhez, akik legalább $500 értékben árukat rendeltek az utolsó 90 napban, *és* részt vettek egy ügyfélszolgálat-hívásban, amelyet eszkaláltak.

:::image type="content" source="media/segmentation-group1-2.png" alt-text="Képernyőkép a szegmensszerkesztő felhasználói felületéről; két, ügyfélszegmenst meghatározó csoport látható.":::

## <a name="create-a-new-segment"></a>Új szegmens létrehozása

Új szegmens többféleképpen is létrehozható. Ez a szakasz azt ismerteti, hogyan hozhat létre üres *szegmenst* az alapoktól. *Üres szegmenst* a meglévő entitások alapján, illetve a gépi tanulási modell *javasolt szegmensei* alapján is létrehozhat. További információk: [Szegmensek áttekintése](segments.md).

A szegmensek létrehozásakor mentheti a tervezetet. A rendszer inaktív szegmensként menti a tervezetet, amely nem aktiválható, amíg be nem lett fejezve érvényes konfigurációval.

1. Lépjen a **Szegmensek** oldalra.

1. Válassza az **új** > **üres szegmens** lehetőséget.

1. Az **Új szegmens** panelen válasszon egy szegmenstípust:

   - A **dinamikus szegmens** ismétlődő ütemezés szerint [frissül](segments.md#refresh-segments).
   - A **statikus szegmensek** egyszer, a létrehozásukkor futnak.

1. Adja meg a szegmens **Kimeneti entitásának nevét**. Tetszés szerint megadhat egy megjelenítendő nevet és egy leírást is, amely segít a szegmens azonosításában.

1. Válassza a **Következő** elemet a **Szegmensépítő** oldalára való eljutáshoz, ahol megadhat egy csoportot. A csoport az ügyfelek halmaza.

1. Válassza ki az entitást, amelyben szerepel az attribútum, amely alapján szegmentálni szeretne.

1. Válassza ki a szegmenshez tartozó attribútumot. Ez az attribútum a következő négy értéktípus egyike lehet: numerikus, szöveges, dátum vagy logikai.

1. Válasszon egy operátort, és adja meg a kijelölt attribútum értékét.

   > [!div class="mx-imgBorder"]
   > ![Egyéni csoportszűrő.](media/customer-group-numbers.png "Ügyfélcsoportszűrő")

   |Szám |Definíció  |
   |---------|---------|
   |1     |Entity          |
   |2     |Attribútum          |
   |3    |Operátor         |
   |4    |Érték         |

   1. Ha további feltételeket szeretne hozzáadni egy csoporthoz, akkor két logikai operátort használhat:

      - **ÉS** operátor: mindkét feltételnek a szegmentálási folyamat részeként kell teljesülnie. Ez a beállítás akkor a leghasznosabb, ha különböző entitások között határoz meg feltételeket.

      - **VAGY** operátor: a szegmentálási folyamat részeként az egyik feltételnek meg kell felelnie. Ez a beállítás akkor a leghasznosabb, ha különböző feltételeket ad meg ugyanahhoz az entitáshoz.

      > [!div class="mx-imgBorder"]
      > ![VAGY operátor, ahol valamelyik feltételt teljesíteni kell.](media/segmentation-either-condition.png "VAGY operátor, ahol valamelyik feltételt teljesíteni kell")

      Jelenleg lehetséges egy **VAGY** operátor beágyazása egy **ÉS** operátor alá, de fordítva nem.

   1. Minden csoport ügyfelek egy csoportjával egyezik. A csoportok kombinálhatók, hogy tartalmazzák az üzleti esethez szükséges ügyfeleket.    
   Válassza a **Csoport hozzáadása** lehetőséget.

      > [!div class="mx-imgBorder"]
      > ![Ügyfélcsoport hozzáadása csoport.](media/customer-group-add-group.png "Ügyfélcsoport hozzáadása csoport")

   1. Válasszon egyet a készletre vonatkozó operátorok közül: **Unió**, **Metszet** vagy **Kivétel**.

   > [!div class="mx-imgBorder"]
   > ![Ügyfélcsoport hozzáadása egyesülés.](media/customer-group-union.png "Ügyfélcsoport hozzáadása egyesülés")

   - Az **Egyesülés** egyesíti a két csoportot.

   - A **Metszet** a két csoport átfedését veszi. Csak az az adat *amely közös* kerül megtartásra mindkét egységesített csoportban.

   - **Kivéve** kombinálja a két csoportot. Csak azon adat kerül megtartásra az A csoportban, amely *nem közös* a B csoport adatival.

1. Ha az entitás [kapcsolatokon](relationships.md) keresztül kapcsolódik az egyesített ügyfél entitáshoz, meg kell határoznia a kapcsolati útvonalat az érvényes szegmens létrehozásához. Adjon hozzá entitásokat a kapcsolati útvonalról, amíg ki nem tudja választani az **Ügyfél: CustomerInsights** entitást a legördülő menüből. Ezután minden lépéshez válassza ki az **Összes rekord** lehetőséget.

   > [!div class="mx-imgBorder"]
   > ![Kapcsolati útvonal a szegmens létrehozása során.](media/segments-multiple-relationships.png "Kapcsolati útvonal a szegmens létrehozása során")

1. A szegmensek alapértelmezés szerint létrehoznak egy kimeneti entitást, amely a definiált szűrőknek megfelelő ügyfélprofilok összes attribútumát tartalmazza. Ha egy szegmens nem az *Ügyfél* entitáson alapul, akkor ezekből az entitásokból további attribútumokat adhat a kimeneti entitáshoz. A **Projektattribútumok** kiválasztásával kiválaszthatja a kimeneti entitáshoz hozzáfűzni kívánt attribútumokat.  
  
   Példa: A szegmens egy olyan entitáson alapul, amely az *Ügyfél* entitáshoz kapcsolódó ügyféltevékenységi adatokat tartalmaz. A szegmens az utóbbi 60 napban a súgónak telefonáló összes ügyfelet keresi. Megadhatja, hogy a hívás időtartamát és a hívások számát hozzáfűzi a kimeneti entitásban található összes egyező ügyfélrekordhoz. Ez az információ hasznosnak bizonyulhat, ha a gyakran telefonáló ügyfeleknek online súgócikkekre irányuló hasznos hivatkozásokat és a gyakori kérdések hivatkozását szeretné elküldeni.

   > [!NOTE]
   > - A vetített attribútumok csak olyan entitások esetén működnek, amelyek egy-a-sokhoz kapcsolatban vannak az ügyfélentitással. Egy ügyfél például több előfizetéssel is rendelkezhet.
   > - Csak olyan entitásból vetíthető attribútum, amely a készített szegmenslekérdezés minden csoportjában használatos.
   > - A vetített attribútumokat figyelembe veszi a rendszer a beállított operátorok használatakor.

1. Válassza a **Mentés** lehetőséget a szegmens mentéséhez. A rendszer menti a szegmenst és feldolgozza, ha az összes követelményt ellenőrizte. Ellenkező esetben vázlatként menti a program.

1. A **Szegmensek** oldalra a **Vissza a szegmensekhez** elemre kattintva léphet vissza.



## <a name="quick-segments"></a>Gyors szegmens

A gyorsszegmensek segítségével gyorsan készíthet egyszerű, egy operátorral rendelkező szegmenseket a gyors elemzéshez.

1. A **Szegmensek** oldalon válassza az **Új** > **Létrehozás a következőből** lehetőséget.

   - Válassza a **Profilok** lehetőséget, ha az *egyesített ügyfél* entitáson alapuló szegmenset szeretne létrehozni.
   - Ha korábban létrehozott mértékekhez szeretne szegmenst létrehozni, válassza a **Mértékek** lehetőséget.
   - Válassza az **Információ** lehetőséget, ha egy szegmenst szeretne létrehozni az egyik olyan kimeneti entitás köré, amelyet vagy az **Előrejelzések** vagy az **egyéni modellek** használatával hozott létre.

2. Az **új gyors szegmens** párbeszédpanelen jelöljön ki egy attribútumot a **Mező** legördülő listában.

3. A rendszer néhány további betekintést biztosít, amelyek segítségével jobb szegmenseket hozhat létre az ügyfelek számára.
   - A kategorikus mezők esetén 10 első számú ügyfél számít. Válasszon egy **Értéket**, és válassza a **Felülvizsgálat** elemet.

   - Numerikus attribútumok esetében a rendszer azt mutatja, hogy az egyes ügyfelek percentilis értékei alá milyen attribútumértékek tartoznak. Válasszon egy **operátort** és egy **értéket**, majd válassza a **Felülvizsgálat** lehetőséget.

4. A rendszer megadja a **Becsült szegmensméret** értékét. Kiválaszthatja, hogy létrehozza-e a megadott szegmenst, vagy először újra meg szeretné vizsgálni, hogy egy másik szegmens méretet kap-e.

    > [!div class="mx-imgBorder"]
    > ![Gyorsszegmens neve és becslése.](media/quick-segment-name.png "Gyorsszegmens neve és becslése")

5. Adjon meg egy **Név** értéket a szegmens számára. Másik lehetőségként adjon meg **Megjelenítendő nevet**.

6. Válassza a **Mentés** lehetőséget a szegmens létrehozásához.

7. Miután a szegmens befejezte a feldolgozást, megtekintheti azt a létrehozott többi szegmenshez hasonlóan.

## <a name="next-steps"></a>További lépések

[Exportáljon egy szegmenst](export-destinations.md), és fedezze fel az [Ügyfélkártya integrációját](customer-card-add-in.md), hogy használhassa a szegmenseket más alkalmazásokban.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
