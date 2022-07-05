---
title: Ügyfélmezők egyesítése az adatok egyesítéséhez
description: Entitások egyesítése az egyesített ügyfélprofilok létrehozásához.
recommendations: false
ms.date: 05/04/2022
ms.subservice: audience-insights
ms.topic: tutorial
author: v-wendysmith
ms.author: mukeshpo
ms.reviewer: v-wendysmith
manager: shellyha
searchScope:
- ci-merge
- ci-match
- ci-relationships
- customerInsights
ms.openlocfilehash: ceb2724ad490c1ba44fd9b7ff2be04721892fca4
ms.sourcegitcommit: dca46afb9e23ba87a0ff59a1776c1d139e209a32
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/29/2022
ms.locfileid: "9082953"
---
# <a name="unify-customer-fields-for-data-unification"></a>Ügyfélmezők egyesítése az adatok egyesítéséhez

[!INCLUDE [m3-prod-trial-note](includes/m3-prod-trial-note.md)]

Az egyesítési folyamat ezen lépésében válassza ki és zárja ki az egyesített profil entitáson belüli egyesíteni kívánt attribútumokat. Ha például három entitás rendelkezett e-mail adatokkal, érdemes lehet megtartani mindhárom különálló e-mail mezőt, vagy egyesíteni őket egyetlen e-mail mezőbe az egyesített profilhoz. Egyes attribútumokat a rendszer automatikusan kombinál. Létrehozhat stabil és egyedi ügyfél-azonosítókat, és csoportosíthatja a kapcsolódó profilokat egy fürtbe.

:::image type="content" source="media/m3_unify.png" alt-text="Oldalak egyesítése az adategyesítési folyamatban; az egységes ügyfélprofilt meghatározó egyesített mezőket tartalmazó táblázat látható.":::

## <a name="review-and-update-the-customer-fields"></a>Az ügyfélmezők áttekintése és frissítése

1. Tekintse át a tábla Ügyfélmezők **lapján egységesíteni** kívánt mezők listáját. Ha van ilyen, végezze el a módosításokat.

   1. Bármely kombinált mező esetében a következőket teheti:
      - [Szerkesztés](#edit-a-merged-field)
      - [Átnevezés](#rename-fields)
      - [Szétválasztás](#separate-merged-fields)
      - [Kizárás](#exclude-fields)
      - [Mozgás felfelé vagy lefelé](#change-the-order-of-fields)

   1. Bármely egyes mező esetében a következőket teheti:
      - [Mezők kombinálása](#combine-fields-manually)
      - [Mezők egy csoportjának egyesítése](#combine-a-group-of-fields)
      - [Átnevezés](#rename-fields)
      - [Kizárás](#exclude-fields)
      - [Mozgás felfelé vagy lefelé](#change-the-order-of-fields)

1. [Igény szerint hozza létre az ügyfél-azonosító konfigurációját](#configure-customer-id-generation).

1. A profilokat nem kötelezően [háztartásokba vagy klaszterekbe csoportosíthatja](#group-profiles-into-households-or-clusters).

> [!div class="nextstepaction"]
> [Következő lépés: Egységesítés áttekintése](review-unification.md)

### <a name="edit-a-merged-field"></a>Egy egyesített mező szerkesztése

1. Jelöljön ki egy egyesített mezőt, és válassza a Szerkesztés **lehetőséget**. Megjelenik a Mezők kombinálása panel.

1. Adja meg a mezők egyesítésének vagy összefésülésének módját a következő három lehetőség egyikével:
    - **Fontosság**: A résztvevő mezőkhöz megadott fontossági rang alapján meghatározza a győztes értékét. Ez az alapértelmezett egyesítési beállítás. A fontosság sorrendjének beállításhoz válassza a **Mozgatás felfelé vagy lefelé** lehetőséget.

      :::image type="content" source="media/importance-merge-option.png" alt-text="Fontosság beállítás a mezők egyesítése párbeszédpanelen.":::

    - **Legújabb**: A győztes értékét a leginkább friss alapján azonosítja. Az létrehozás idejének meghatározásához az egyesítés mezők hatókörében minden részt vevő entitáshoz dátum vagy numerikus mező szükséges.

      :::image type="content" source="media/recency-merge-option.png" alt-text="Viszonosság beállítás a mezők egyesítése párbeszédpanelen.":::

    - **Legérlegebbi**: A győztes értékét a leginkább régi alapján azonosítja. Az létrehozás idejének meghatározásához az egyesítés mezők hatókörében minden részt vevő entitáshoz dátum vagy numerikus mező szükséges.

1. Az összefésülésben való részvételhez további mezőket adhat hozzá.

1. Az egyesített mező átnevezhető.

1. Válassza a **Kész** lehetőséget a módosítások alkalmazásához.

### <a name="rename-fields"></a>Mezők átnevezése

Módosítsa az egyesített vagy különálló mezők megjelenítendő név. A kimeneti entitás neve nem módosítható.

1. Jelölje ki a mezőt, majd válassza az Átnevezés **lehetőséget**.

1. Adja meg az új megjelenítendő név.

1. Válassza a **Kész** lehetőséget.

### <a name="separate-merged-fields"></a>Egyesített mezők szétválasztása

Az egyesített mezők szétválasztásához keresse meg az attribútumot a táblázatban. A szétválasztott mezők egyéni adatpontokként jelennek meg az egységes ügyfélprofilban.

1. Jelölje ki az egyesített mezőt, és válassza a Mezők **elkülönítése lehetőséget**.

1. Erősítse meg a szétválasztást.

### <a name="exclude-fields"></a>Mezők kizárása

Zárja ki az egyesített vagy különálló mezőt az egyesített vevői profilból. Ha a mező más folyamatokban – például szegmensekben – használatos, akkor az ügyfélprofilból való kizárás előtt távolítsa el ezekből a folyamatokból.

1. Jelöljön ki egy mezőt, és válassza a Kizárás **lehetőséget**.

1. Erősítse meg a kizárást.

Az összes kizárt mező listájának megtekintéséhez válassza a Kizárt mezők **lehetőséget**. Szükség esetén elolvashatja a kizárt mezőt.

### <a name="change-the-order-of-fields"></a>Mezők sorrendjének módosítása

Egyes entitások több adatot tartalmaznak, mint mások. Ha egy entitás egy mezőre vonatkozóan a legfrissebb adatokat tartalmazza, az értékek egyesítésekor prioritást adhat neki a többi entitáshoz képest.

1. Válassza ki a mezőt.
  
1. Válassza a Mozgatás felfelé/lefelé **lehetőséget** a sorrend beállításához, vagy húzza őket a kívánt pozícióba.

### <a name="combine-fields-manually"></a>Mezők manuális kombinálása

Különálló mezők kombinálásával hozzon létre egyesített attribútumot.

1. Válassza a Mezők **kombinálása** > **lehetőséget**. Megjelenik a Mezők kombinálása panel.

1. Adja meg az egyesítés győztesének irányelvét a **Mezők összevonása a következő alapján:** legördülő menüben.

1. Válassza a Mező **hozzáadása lehetőséget** további mezők egyesítéséhez.

1. Adja meg a **Nevet** és egy **Kimeneti mező nevét**.

1. Válassza a **Kész** lehetőséget a módosítások alkalmazásához.

### <a name="combine-a-group-of-fields"></a>Mezők egy csoportjának egyesítése

A mezők egy csoportját egyetlen egységként kezelje. Ha például a rekordjaink tartalmazzák a Address1, Address2, City, State és Zip mezőket, akkor nem szeretnénk egyesíteni egy másik rekord Address2 mezőjében, azt gondolva, hogy ez teljesebbé tenné az adatainkat.

1. Válassza a Mezők **csoportjának kombinálása** > **lehetőséget**.

1. Adja meg az egyesítési győztes házirendjét a **Rangsor csoportok** legördülő menüben.

1. Válassza a Hozzáadás **lehetőséget**, és válassza ki, hogy további mezőket vagy csoportokat szeretne-e hozzáadni a mezőkhöz.

1. Adjon meg egy **nevet** és egy **kimeneti nevet** minden kombinált mezőhöz.

1. Adja meg **a mezők csoportjának nevét**.

1. Válassza a **Kész** lehetőséget a módosítások alkalmazásához.

## <a name="configure-customer-id-generation"></a>Ügyfél-azonosító létrehozásának konfigurálása

Határozza meg, hogyan hozhat létre ügyfél-azonosító értékeket, az egyedi ügyfélprofil-azonosítókat. Az adategyesítési folyamat egyesítő mezőkre vonatkozó lépése létrehozza az egyedi ügyfélprofil-azonosítót. Az azonosító az *ügyfélentitás* ügyfél-azonosítója *·*, amely az adategyesítési folyamat eredménye.

A *CustomerId* a nem null nyertes elsődleges kulcsok első értékének kivonatán alapul. Ezek a kulcsok az adategyesítéshez használt entitásokból származnak, és az egyezési sorrend befolyásolja őket.Így a létrehozott ügyfél-azonosító változhat, ha egy elsődleges kulcs értéke megváltozik az egyezési sorrend elsődleges entitásában. Előfordulhat, hogy az elsődleges kulcs értéke nem mindig ugyanazt a vevőt jelöli.

A megbízható ügyfélazonosító konfigurálása lehetővé teszi, hogy elkerülje ezt a viselkedést.

1. Válassza ki a **Kulcsok** lapot.

1. Vigye az egérmutatót a **CustomerId** sorba, és válassza a Konfigurálás **lehetőséget**.
   :::image type="content" source="media/customize-stable-id.png" alt-text="Vezérlés az azonosítók generálásának testreszabásához.":::

1. Jelöljön ki legfeljebb öt olyan mezőt, amely egyedi ügyfélazonosítót tartalmaz, és stabilabb. A konfigurációnak nem megfelelő rekordok a rendszer által konfigurált azonosítót kell használják.  

1. Válassza a **Kész** lehetőséget.

## <a name="group-profiles-into-households-or-clusters"></a>A csoportos profilokat háztartásokba vagy fürtökbe kell csoportosítani

Szabályokat határozhat meg a kapcsolódó profilok fürtbe csoportosításához. Jelenleg két fürttípus áll rendelkezésre: háztartási és egyéni fürtök. A rendszer automatikusan kiválasztja az előre definiált szabályokkal való használatot, ha az *Ügyfél* entitása a *Person.LastName* és *Location.Address* szemantikus mezőket tartalmazza. Az [egyező szabályokhoz](match-entities.md#define-rules-for-match-pairs) hasonlóan saját szabályokkal és feltételekkel is létrehozhat fürtöt.

1. Válassza a Speciális **fürt** > **létrehozása lehetőséget**.

   :::image type="content" source="media/create-cluster.png" alt-text="Új fürt létrehozásához szükséges vezérlő.":::

1. Válasszon a **Háztartási** vagy az **Egyéni** fürt lehetőségekközül. Ha a *Person.LastName* és *Location.Address* szemantikus mezők léteznek az *Ügyfél* entitásban, a program automatikusan kiválasztja a címzett nevét.

1. Adja meg a fürt nevét, és válassza a **Kész** lehetőséget.

1. A létrehozott fürt kereséséhez válassza a **Fürtök** lapot.

1. Adja meg a fürt definiáló szabályait és feltételeit.

1. Válassza a **Kész** lehetőséget. A fürt akkor jön létre, amikor az egyesítési folyamat befejeződött. A fürtazonosítók új mezőkként lesznek hozzáadva a *Vevő* entitáshoz.

> [!div class="nextstepaction"]
> [Következő lépés: Egységesítés áttekintése](review-unification.md)

[!INCLUDE [footer-include](includes/footer-banner.md)]
