---
title: Customer Insights adatok exportálása az AdRollba
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja az AdRollba.
ms.date: 03/03/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 67bfa23d56b26ae592efa4d7197713664bb02623
ms.sourcegitcommit: d84d664e67f263bfeb741154d309088c5101b9c3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/24/2021
ms.locfileid: "6304830"
---
# <a name="export-segments-to-adroll-preview"></a>Szegmensek exportálása az AdRollba (előzetes verzió)

Exportálja az egyesített ügyfélprofilok szegmenseit az AdRollba, és használja őket a hirdetésekben. 

## <a name="prerequisites-for-a-connection"></a>Egy kapcsolat előfeltételei

-   Rendelkezik [AdRoll-fiókkal](https://www.adroll.com/) és a megfelelő rendszergazdai hitelesítő adatokkal.
-   [Konfigurált szegmensekkel](segments.md) rendelkezik a célközönségi-információkban.
-   Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.

## <a name="known-limitations"></a>Ismert korlátozások

- Egyidejűleg legfeljebb 250 000 profilt exportálhat AdRoll-ba.
- 100-nál kevesebb profillal rendelkező szegmensek nem exportálhatók az AdRollba. 
- Az AdRollba való exportálás csak szegmensekre korlátozódik.
- Legfeljebb 250 000 profil AdRollba való exportálása eltarthat 10 percig. 
- Az AdRoll-ba exportálható profilok száma az AdRoll- lal kötött szerződésétől függ.

## <a name="set-up-connection-to-adroll"></a>Állítsa be az AdRollal való kapcsolatot

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza az **AdRoll** lehetőséget a kapcsolat konfigurálásához.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.

1. Válassza a **Csatlakozás** lehetőséget az AdRoll kapcsolat inicializálásához.

1. Válassza a **Hitelesítés az AdRoll szolgáltatással** lehetőséget, és adja meg AdRoll rendszergazdai hitelesítő adatait. 

1. Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

## <a name="configure-an-export"></a>Exportálás konfigurálása

Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz. További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Új exportálás létrehozásához válassza a **Célhely hozzáadása** lehetőséget.

1. A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot az AdRoll szakaszból. Ha nem látja ezt a szakasznevet, akkor ilyen típusú kapcsolatok nem állnak az Ön rendelkezésére.

1. Adja meg **AdRoll hirdetői azonosítóját**. További információ: [AdRoll Hirdetői Profilok](https://help.adroll.com/hc/articles/212011838-Advertiser-Profiles).

3. Az **Adategyeztetés** szakaszban az **E-mail** mezőben jelölje ki az egyesített ügyfélprofil ügyfél e-mail-címét jelképező mezőjét. A szegmenseket exportálni kell az AdRollba.

1. Jelölje ki a szegmenseket, amelyeket exportálni szeretne. Jelöljön ki egy legalább 100 tagból álló szegmenst. Kisebb szegmensek nem exportálhatók. Továbbá az exportálni kívánt szegmens maximális mérete exportálásonként 250 000 tag. 

1. Válassza a **Mentés** parancsot.

Az exportálás mentése nem futtatja azonnal az exportálást.

Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut. 

Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand). 


## <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség

Amikor engedélyezi a Dynamics 365 Customer Insights szolgáltatást az adatok AdRoll szolgáltatásba való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat. A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy az AdRoll megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek. További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).

A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.
