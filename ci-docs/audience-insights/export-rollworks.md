---
title: Customer Insights-adatok exportálása a RollWorksra
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a RollWorksba.
ms.date: 03/03/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: d8ce4d867835dcb7cf56c6fffff4e25d1f5c109af0e401fc0eb8b3a7427c1de4
ms.sourcegitcommit: aa0cfbf6240a9f560e3131bdec63e051a8786dd4
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/10/2021
ms.locfileid: "7034593"
---
# <a name="export-segments-to-rollworks-preview"></a>Szegmensek exportálása a RollWorksba (előzetes verzió)

Exportálja az egyesített ügyfélprofilok szegmensét a RollWorksba, és használja őket hirdetési célokra. 

## <a name="prerequisites-for-a-connection"></a>Egy kapcsolat előfeltételei

-   Van egy [RollWorks fiókja](https://www.rollworks.com/) és ahhoz tartozó rendszergazdai hitelesítő adatai.
-   [Konfigurált szegmensekkel](segments.md) rendelkezik a célközönségi-információkban.
-   Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.

## <a name="known-limitations"></a>Ismert korlátozások

- A RollWorks exportálásonként legfeljebb 250 000 profil exportálható.
- A 100-nál kevesebb profillal rendelkező szegmensek nem exportálhatók a RollWorksba. 
- A RollWorksba való exportálás a szegmensekre korlátozódik.
- 250 000 profil exportálása a RollWorks alkalmazásba akár 10 percet is igénybe vehet. 
- A RollWorksba exportálható profilok száma a RollWorksszal kötött szerződéstől függ és az korlátozza.

## <a name="set-up-connection-to-rollworks"></a>Állítsa be a RollWorksszal való kapcsolatot

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza a **RollWorks** lehetőséget a kapcsolat konfigurálásához.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.

1. Válassza a **Kapcsolat** lehetőséget a RollWorks kapcsolatának inicializálására.

1. Válassza a **Hitelesítés a RollWorksszel** lehetőséget, és adja meg a RollWorks rendszergazdai hitelesítő adatait.

1. Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

## <a name="configure-an-export"></a>Exportálás konfigurálása

Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz. További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Új exportálás létrehozásához válassza a **Célhely hozzáadása** lehetőséget.

1. A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot a RollWorks szakaszból. Ha nem látja ezt a szakasznevet, az Ön számára nincs ilyen típusú kapcsolat.

1. Adja meg a **RollWorks Advertiser azonosítót** [RollWorks Advertisable](https://help.adroll.com/hc/articles/212011838-Advertiser-Profiles) értéket.

3. Az **Adategyeztetés** szakaszban az **E-mail** mezőben jelölje ki az egyesített ügyfélprofil ügyfél e-mail-címét jelképező mezőjét. A szegmenseket exportálni kell a RollWorks alkalmazásba.

1. Jelölje ki a szegmenseket, amelyeket exportálni szeretne. Jelöljön ki egy legalább 100 tagból álló szegmenst. Kisebb szegmensek nem exportálhatók. Az exportálni kívánt szegmens maximális mérete exportálásonként 250 000 tag. 

1. Válassza a **Mentés** parancsot.

Az exportálás mentése nem futtatja azonnal az exportálást.

Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut. Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand). 


## <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség

Amikor engedélyezi Dynamics 365 Customer Insightst, hogy adatokat továbbítson a RollWorksnek, akkor lehetővé teszi az adatok továbbítását a Dynamics 365 Customer Insights megfelelési határán kívülre is, beleértve az esetlegesen bizalmas adatokat is, például a Személyes adatokat. A Microsoft az Ön utasítására továbbítja az adatokat, de Ön a felelős azért, hogy a RollWorks megfeleljen az esetleges adatvédelmi vagy biztonsági kötelezettségeknek. További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).

A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.
