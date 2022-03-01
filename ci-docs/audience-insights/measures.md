---
title: Mérőszámok létrehozása és szerkesztése
description: Határozza meg az ügyfélhez kapcsolódó mérőszámokat, amelyekkel elemezheti és szemléltetheti bizonyos üzleti területek teljesítményét.
ms.date: 10/15/2020
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
ms.reviewer: wameng
manager: shellyha
ms.openlocfilehash: 0e214a6eb66abd27f7292db3ce2c2a6e16a8ff33
ms.sourcegitcommit: cf9b78559ca189d4c2086a66c879098d56c0377a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/03/2020
ms.locfileid: "4406021"
---
# <a name="define-and-manage-measures"></a>Az intézkedések definiálása és kezelése

A **Mérőszámok** olyan fő teljesítménymutatókat (KPI) jelentenek, amelyek adott üzleti területek teljesítményét és működését tükrözik. A célközönség-információk a különböző típusú intézkedések kiépítésére szolgáló intuitív élményt nyújt, egy lekérdezés-szerkesztő segítségével, amely nem igényli az intézkedések kézi kódolását vagy érvényesítését. Az üzleti mérőszámokat a **Kezdőlap** oldalon követheti nyomon, és megtekintheti az egyes ügyfelekre vonatkozó mérőszámokat az **Ügyfélkártya** részben, és mérőszámokkal meghatározhatja az ügyfélszegmenseket a **Szegmensek** oldalon.

## <a name="create-a-measure"></a>Mérőszám létrehozása

Ez a rész végigvezeti a mérőszám semmiből történő létrehozásának lépésein. Mérőszámokat hozhat létre olyan adatokkal, amelyek több adatforrásból származnak, és az ügyfél entitáson keresztül kapcsolódnak egymáshoz. Bizonyos [szolgáltatási korlátozások](service-limits.md) érvényesek.

1. A célközönség információin belül nyissa meg a következőt: **Mérőszámok**.

2. Válassza az **Új mérőszám** lehetőséget.

3. Válassza ki a mérőszám **típusát**:

   - **Ügyfélattribútum**: Egyetlen mező ügyfelenként, amely az ügyfél pontszámát, értékét vagy állapotát tükrözi. Az ügyfelek attribútumai egy új, a rendszer által létrehozott, **Customer_Measure** nevű entitásban attribútumokként jönnek létre.

   - **Ügyfélmérőszám**: Az ügyfelek viselkedésének vonatkozó információk a kijelölt dimenziók szerinti részletezéssel. A rendszer minden egyes mérőszámhoz létrehoz egy új entitást, amely esetleg több bejegyzést tartalmaz egy ügyfélnél.

   - **Üzleti mérőszám**: Nyomon követi a vállalkozás teljesítményét és egészségét. Az üzleti mérőszámok két különböző kimenettel rendelkezhetnek: egy numerikus kimenet, amely a **Kezdőlapon** jelenik meg, vagy egy új entitás, amelyet az **Entitások** oldalon talál.

4. Adjon meg egy **Név** értéket, és egy nem kötelező **Megjelenítendő nevet**, majd nyomja meg a **Tovább** lehetőséget.

5. Az **Entitás** részben válassza ki az első entitást a legördülő listából. Ezen a ponton el kell döntenie, hogy szükségesek-e további entitások a mértékegység meghatározásának részeként.

   > [!div class="mx-imgBorder"]
   > ![Mérőszám definíciója](media/measure-definition.png "Mérőszám definíciója")

   További entitások hozzáadásához válassza az **Entitás hozzáadása** lehetőséget, és válassza ki a mérőszámhoz használni kívánt entitásokat.

   > [!NOTE]
   > Olyan entitásokat választhat csak, amelyek kapcsolódnak az elsőként kiválasztott entitáshoz. Ha további tájékoztatást szeretne kapni a kapcsolatok meghatározásáról, lásd. [Kapcsolatok](relationships.md).

6. Másik megoldásként Ön is konfigurálhatja a változókat. A **Változók** szakaszban válassza az **új változó** elemet.

   A változók a kijelölt rekordokon végrehajtott számítások. Például a pénztári (POS) és online értékesítés összesítése az egyes ügyfelek rekordjaira vonatkozóan.

7. Adja meg a változó **nevét**.

8. A **Kifejezés** területen válassza ki azt a mezőt, amellyel el szeretné kezdeni a számítást.

9. Írjon be egy kifejezést a **Kifejezés** területen, és válassza ki a számításba szerepeltetendő további mezőket.

   > [!NOTE]
   > Jelenleg csak aritmetikai kifejezések támogatottak. Emellett a változók számítása nem támogatott a különböző [entitásútvonalról](relationships.md) származó entitások esetén.

10. Válassza a **Kész** lehetőséget.

11. A **Mértékegység meghatározása** szakaszban azt határozhatja meg, hogy a kiválasztott entitások és a számított változók hogyan legyenek összesítve egy új mérőszám entitásában vagy attribútumában.

12. Válassza az **Új dimenzió** elemet. A dimenzióra *csoportosítási szempont* függvényként is tekinthet. A Mérőszám entitás vagy attribútum adatkimeneteit a rendszer az összes megadott dimenzió alapján csoportosítja.

    > [!div class="mx-imgBorder"]
    > ![Összesítési ciklus kiválasztása](media/measures-businessreport-measure-definition2.png "Összesítési ciklus kiválasztása")

    Válassza ki vagy adja meg a következő adatokat a dimenzió meghatározása részeként:

    - **Entitás**: Ha egy Mérőszám entitást definiál, akkor legalább egy attribútumot tartalmaznia kell. Ha Mérőszám attribútumot határoz meg, akkor alapértelmezés szerint csak egyetlen attribútumot fog tartalmazni. Ez a beállítás az attribútumot tartalmazó entitás kiválasztásáról szól.
    - **Mező**: válassza ki azt a konkrét attribútumot, amelyet be szeretne vonni a mérőszám entitásba vagy attribútumba.
    - **Gyűjtő**: válassza ki, hogy az adatokat napi, havi vagy éves szinten szeretné összesíteni. Csak akkor szükséges, ha a Dátumtípus attribútumot jelölte ki.
    - **Mint**: Meghatározza az új mező nevét.
    - **Megjelenítendő név**: meghatározza a mező megjelenítendő nevét.

    > [!NOTE]
    > Az üzleti mérőszámot egyszámos entitásként menti a rendszer és megjelenik a **Kezdőlap** oldalon, ha csak nem ad több dimenziót a mérőszámhoz. További dimenziók hozzáadását követően a mérőszám *nem* jelenik meg a **kezdőlapon**.

13. Tetszés szerint az összesítési funkciókat is hozzáadhatja. Bármely Ön által létrehozott összesítés az eredményeket egy új értékben hozza létre a Mérőszám entitást vagy attribútumot. A támogatott aggregációs függvények a következők: **Min**, **Max**, **Average**, **Median**, **Sum**, **Count Unique**, **First** (a dimenzióérték rekordjai közül az elsőt veszi) és **Last** (a dimenzióértékhez utoljára hozzáadott rekordot veszi).

14. A mérőszám módosításainak alkalmazásához válassza a **Mentés** lehetőséget.

## <a name="manage-your-measures"></a>Intézkedések kezelése

Legalább egy mérték létrehozása után megtekintheti a mértékek listáját a **Mértékek** oldalon.

Itt információk találhatók a mérőszám típusáról, a létrehozóról, a létrehozás dátumáról és idejéről, az utolsó módosítás dátumáról és időpontjáról, állapotról (hogy a mérőszám aktív, inaktív vagy sikertelen) és az utolsó frissítés dátumáról és időpontjáról. Ha egy intézkedést kiválaszt a listából, láthatja a kimenetének előnézetét.

Ha egyszerre szeretné frissíteni az összes intézkedést, akkor jelölje be az **összes frissítése** lehetőséget egy adott intézkedés kiválasztása nélkül.

> [!div class="mx-imgBorder"]
> ![Az egyes intézkedések kezelésére szolgáló műveletek](media/measure-actions.png "Az egyes intézkedések kezelésére szolgáló műveletek")

Másik lehetőségként jelöljön ki egy intézkedést a listából, és hajtsa végre az alábbi műveletek egyikét:

- Adja meg a mérőszám nevét a részletek megtekintéséhez.
- **Szerkessze** a mérőszám konfigurációját.
- **Nevezze át** az intézkedést.
- **Törölje** az intézkedést.
- Jelölje ki a három pontot (...), majd a **Frissítés** lehetőséggel indítsa el az intézkedés frissítési folyamatát.
- Jelölje ki a három pontot (...), majd a **Letöltés** lehetőséggel töltse le az intézkedés .CSV fájlját.

> [!TIP]
> A feladatokhoz/folyamatokhoz [hatféle állapot](system.md#status-types) tartozhat. Emellett a legtöbb folyamat [más alsóbb szintű folyamatoktól is függ](system.md#refresh-policies). Kiválaszthatja egy folyamat állapotát, és megtekintheti a hozzá tartozó teljes feladat folyamatának részleteit. Miután kiválasztotta a **Részletek megtekintése** lehetőséget a feladat egyik feladatához, további információk jelennek meg: feldolgozási idő, legutóbbi feldolgozás dátuma, és a feladathoz társított összes hiba és figyelmeztetés.

## <a name="next-step"></a>Következő lépés

A meglévő mérőszámok használatával a **Szegmensek** oldalon hozhatja létre az első ügyfélszegmenst. További tudnivalókat a [Szegmensek](segments.md) részben talál.
