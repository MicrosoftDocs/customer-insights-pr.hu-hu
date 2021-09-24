---
title: Tölcsérjelentések
description: Tölcsérjelentések használata annak megértése érdekében, hogy a célközönség hogyan hoz döntéseket.
ms.reviewer: mhart
ms.author: kamacdon
author: kamacdon
ms.date: 09/17/2021
ms.service: customer-insights
ms.subservice: engagement-insights
ms.topic: how-to
ms.manager: shellyha
ms.openlocfilehash: 901e7ec50037d66c7c5ceb635d1c6cda6cfff83b
ms.sourcegitcommit: 3bafa27adae113948636b30c7462e0af060c7131
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/17/2021
ms.locfileid: "7498645"
---
# <a name="create-and-manage-funnel-reports"></a>Tölcsérjelentések létrehozása és kezelése

[!INCLUDE [cc-beta-prerelease-disclaimer](includes/cc-beta-prerelease-disclaimer.md)]

A tölcsérjelentés a webhelyen vagy mobilalkalmazáson keresztül ügyfélút információkat gyűjt a lépésekről. Így könnyebben megértheti, hogyan célközönség egy-egy folyamat, és hogyan azonosítja a legördülő pontokat. A tölcsérjelentés segítségével például megállapíthatja, hogy az ügyfelek milyen elérési utakat járnak végig a vásárlás előtt. A tölcsérjelentés olyan adatokat tartalmaz, amelyek a döntéseket tájékoztatják, és azonosítják az optimalizálási és folyamatfejlesztéshez szükséges területeket.

## <a name="create-a-funnel-report"></a>Tölcsérjelentés létrehozása

A tölcsérjelentés létrehozásához adja meg a szerepeltetni kívánt lépéseket, valamint adja meg az egyes lépésekhez a tevékenységet. A tevékenység a felhasználói viselkedésnek megfelelő [esemény](glossary.md). A tölcsérjelentés megjeleníti az egyes definiált lépéseket ellépő felhasználók számát. 

1. Tölcsérjelentés indításához lépjen a **Tölcsérek** elemre, majd válassza a **+Új tölcsér** lehetőséget.

1. A **Tölcsérszerkesztőben**, a **Lépések** alatt válassza a **+Lépés hozzáadása** lehetőséget. 

1. Adjon meg nevet a **Lépéscím** pontban.

   :::image type="content" source="media/new-funnel-report.png" alt-text="Új tölcsérjelentések.":::

1. Válasszon egy **Tevékenységet**. A tevékenység azt rögzíti, hogy a felhasználó mikor tekint meg egy oldalt (tevékenység **Megtekintése**), vagy lép kapcsolatba a tartalommal (**művelettevékenység**).

1. Használja a **Lépéskritériumok** lehetőséget a tevékenység dimenziójának megadásához. A [dimenziók](dimensions.md) olyan attribútumok, amelyek leírhatják, szűrhetik vagy csoportosíthatják az adatokat.

1. Tetszés szerint több feltételes tölcsérlépéseket is beállíthat. Válassza a **Feltétel hozzáadása** lehetőséget, ha több dimenziót szeretne megadni egy lépésben. A további feltételeknek ugyanazt a tevékenységtípust kell használniuk. Megadhatja, hogy az ÉS vagy VAGY operátorhoz több feltétel is kapcsolódjon.

   :::image type="content" source="media/funnel-add-condition.png" alt-text="A lépéskonfigurációt több feltételt megszabó lépésekkel bemutató tölcsérszerkesztő.":::

1. Válassza a **Lépés hozzáadása** lehetőséget, amíg be nem fejeződik a jelentésben kívánt összes művelet.

1. Válassza a **Mentés** lehetőséget, nevezze el a jelentést, majd **Mentse** újra. 

### <a name="example-fourth-coffee-company-funnel-report"></a>Példa: Fourth Coffee cég tölcsérjelentés

A következő forgatókönyv a tölcsérjelentések használatának egyik módját mutatja be. A Fourth Coffee vállalat elemzője látni szeretné, hogy milyen hatással van egy nemrégiben történt promóció az előfizetési árfolyamokra. Az elemző ügyféltevékenységet azonosító tölcsérjelentést hoz létre. Ez akkor kezdődik, amikor az ügyfelek addig érkeznek a vállalat kezdőlapjára, amíg az előfizetési promóció kódját nem használják. Az elemző a következő lépésekkel hozza létre a tölcsérjelentést:

1. lépés: A kezdőlapra érkező ügyfelek   
2. lépés: A vásárlást végrehajtó ügyfelek   
3. lépés: Azok az ügyfelek, akik a promóciós kódot használják, hogy kedvezményt kapjanak az előfizetésre   
4. lépés: Előfizetésre való feliratkozás   

:::image type="content" source="media/funnel-report-example.png" alt-text="tölcsérjelentés példája.":::
  
Ebben a tölcsérben látható, hogy hány felhasználó regisztrálta magát az előfizetési programra, miután egy alkalommal megvásárolta a promóciós kódot.

### <a name="configure-advanced-settings"></a>Speciális beállítások konfigurálása 

A tölcsérjelentések meghatározzák, hogy mennyi idő alatt fejeződik be a tölcsér. Beállíthatja például, hogy mikor fejeződjön be a tölcsér négy napra. Ez a beállítás csak azokat a sikeres feliratkozásokat számolja, amelyek négy napon belül megtörténtek ahhoz képest, hogy a felhasználó meglátogatta a kezdőlapot.

1. Lépjen a **Tölcsérek** pontra a **Tölcsérkönyvtár** megnyitásához.

1. Válasszon ki egy nevet a jelentés megnyitásához. 

1. A **Tölcsérszerkesztő** ablaktáblában válassza a **Speciális beállítások** lehetőséget. 

1. Állítsa a Tölcsér teljesítésének korlátja beállítást **Be** értékre.

   :::image type="content" source="media/funnel-limit-time.png" alt-text="A tölcsérszerkesztő bemutatja a speciális beállításokat és a tölcsér befejezéséhez szükséges időkorlátot.":::

1. Válassza ki, hogy a tölcsér mikor fejeződött be a **Korlát beállítása** legördülő listában.

1. Válassza a **Mentés** lehetőséget a módosítások alkalmazásához.


## <a name="cross-channel-funnel-reports"></a>Csatornák közötti tölcsérjelentések 

Az aktivitási információk segítségével viselkedéses ügyféladatokat is gyűjthet a mobilalkalmazásban. Ha már használta mobilalkalmazását az aktivitási információk segítségével [Android SDK](get-started-android.md) vagy [iOS SDK](get-started-ios.md), csatornaközi tölcsérjelentéseket hozhat létre. 

### <a name="create-a-cross-channel-funnel-report"></a>Csatornák közötti tölcsérjelentések létrehozása 

1. A következő lépésekkel [hozzon létre tölcsérjelentést](#create-a-funnel-report).    

1. Annak nyomon követéséhez, hogy az ügyfelek hogyan lépnek kapcsolatba a márkanévvel a webhelyen és mobilalkalmazásban, illetve több webhelyen is, a munkaterület-kapcsolóval hozzon létre tölcsérlépéseket a más munkaterületről származó adatokkal. A **Tölcsérszerkesztő** -ben, **Lépések** alatt válassza ki, hogy melyik munkaterületről származnak a tölcsér lépéshez szükséges adatok.

## <a name="manage-funnel-reports"></a>Tölcsérjelentések kezelése

A tölcsérjelentéseket áttekintheti az adatok elemzése, a teljesítmény nyomon követése és az információk gyűjtése érdekében.

> [!NOTE]
> - Az aktivitási információk tölcsérjelentései jelenleg olyan eseteket támogatnak, amikor a tölcsér összes felhasználója névtelen, vagy minden felhasználót hitelesít a rendszer. 
> - A tölcsérjelentések korábbi adatai az utolsó 30 napban elérhetők.

### <a name="view-funnel-reports"></a>Tölcsérjelentések megtekintése

1. Lépjen a **Tölcsérek** pontra a **Tölcsérkönyvtár** megnyitásához.
1. Válasszon ki egy nevet a jelentés megnyitásához.    

### <a name="see-the-data-collected-for-a-report"></a>Tekintse át az egy jelentéshez összegyűjtött adatokat   

A fázisra vonatkozó információk megtekintéséhez

- Irányítsa a jelentést egy lépésére.

:::image type="content" source="media/funnel-step-data.png" alt-text="tölcséradatok.":::

### <a name="change-the-date-range-for-the-funnel-report"></a>A tölcsérjelentés dátumtartományának módosítása

1. Lépjen a **Tölcsérek** pontra a **Tölcsérkönyvtár** megnyitásához.

1. Válasszon ki egy nevet a jelentés megnyitásához.

1. Nyissa meg a **időtartomány** lehetőséget, és válasszon ki egy új időszakot a listából, vagy a **Rögzített időtartomány** lehetőséget egy dátumtartomány megadásához.

## <a name="edit-or-delete-funnel-reports"></a>Tölcsérjelentések szerkesztése vagy törlése

Módosíthatja a tölcsérjelentés nevét, törölheti, illetve módosíthatja a jelentésben található lépéseket.

### <a name="rename-or-delete-a-funnel-report"></a>Tölcsérjelentés átnevezése vagy törlése

1. Lépjen a **Tölcsérek** pontra a **Tölcsérkönyvtár** megnyitásához. 

1. Válassza a **További** lehetőséget a módosítani kívánt jelentés mellett, és válassza a **Név szerkesztése** vagy a **Törlés** lehetőséget.

### <a name="edit-a-funnel-step"></a>Tölcsérlépés szerkesztése  

1. Lépjen a **Tölcsérek** pontra a **Tölcsérkönyvtár** megnyitásához. 

1. Válasszon ki egy nevet a jelentés megnyitásához.

1. Válassza ki a szerkeszteni kívánt lépést.

1. Válassza a **Szerkesztés** lehetőséget.

1. A **Tölcsérszerkesztőben** módosítsa a módosítani kívánt információkat.  

1. Válassza a **Mentés** parancsot.

### <a name="reorder-a-funnel-step"></a>Tölcsérlépés átrendezése

1. Lépjen a **Tölcsérek** pontra a **Tölcsérkönyvtár** megnyitásához. 

1. Válasszon ki egy nevet a jelentés megnyitásához.

1. Válassza ki az átrendezni kívánt lépést.

1. Válassza az **Áthelyezés**, majd **Fel**, **Le**, **Felülre** vagy **Alulra** lehetőséget a lépés áthelyezéséhez.

### <a name="delete-a-funnel-step"></a>Tölcsérlépés törlése

1. Lépjen a **Tölcsérek** pontra a **Tölcsérkönyvtár** megnyitásához. 

1. Válasszon ki egy nevet a jelentés megnyitásához.

1. Jelölje ki a törölni kívánt lépést, majd kattintson az **Eltávolítás** gombra.

## <a name="funnel-insights"></a>Tölcsérelemzések 

Az elkötelezettségi információk mostantól tölcsérelemzéseket is nyújt az ügyfeleknek. A tölcsérelemzések segítségével alaposan megismerheti az ügyfelek viselkedését a tölcsérjelentés lépéseivel kapcsolatosan. Új tölcsérjelentés létrehozásakor és mentésekor a jelentéshez automatikusan létrejön a tölcsérelemzés. 

A tölcsérelemzéseket a következő kategóriákból tekintheti meg, mind a fő szinten, mind a lépés szintjén: 

 - Átalakítási arány 
 - Váltásidő 
 - Befejezés ideje 

Ezek az információk segítségével mélyebben megismerheti az ügyfél viselkedését, és jobban megismerheti a tölcsérjelentésnél a kiesési pontokat és a konverziókat. 

A tölcsér információk újraszámítása 24 óránként történik, illetve a tölcsérjelentés **mentésekor** is. 

> [!NOTE]
> A tölcsérre vonatkozó elemzések megtekintéséhez minden alkalommal mentenie kell a jelentést, amikor módosítja az adatokat. 

