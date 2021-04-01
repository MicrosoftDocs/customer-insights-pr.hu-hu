---
title: Customer Insights adatok exportálása az AdRollba
description: Megismerheti, hogyan konfigurálható a kapcsolat az AdRoll szolgáltatással.
ms.date: 02/15/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 6fedd549c2e7de362f36e3fb23d363200bb92a04
ms.sourcegitcommit: d24e52150fe5a4fab45128e12d6a03637771d9b9
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/19/2021
ms.locfileid: "5697077"
---
# <a name="connector-for-adroll-preview"></a>Az AdRoll összekötője (előzetes verzió)

Exportálja az egyesített ügyfélprofilok szegmenseit az AdRollba, és használja őket a hirdetésekben. 

## <a name="prerequisites"></a>Előfeltételek

-   Rendelkezik [AdRoll-fiókkal](https://www.adroll.com/) és a megfelelő rendszergazdai hitelesítő adatokkal.
-   [Konfigurált szegmensekkel](segments.md) rendelkezik a célközönségi-információkban.
-   Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.

## <a name="connect-to-adroll"></a>Csatlakozás az AdRollhoz

1. Válassz a **Rendszergazda** > **Célok exportálása** lehetőséget.

1. A **AdRoll** részben válassza a **Beállítás** lehetőséget.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben az export helyének.

   :::image type="content" source="media/AdRoll_config.PNG" alt-text="Az AdRoll-kapcsolat konfigurációs ablaktáblája.":::

1. Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.

1. Válassza a **Csatlakozás** lehetőséget az AdRoll kapcsolat inicializálásához.

1. Válassza a **Hitelesítés az AdRoll szolgáltatással** lehetőséget, és adja meg AdRoll rendszergazdai hitelesítő adatait. 

1. Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.

1. Adja meg az **AdRoll hirdetői azonosítóját** [AdRoll hirdethetőség](https://help.adroll.com/hc/en-us/articles/212011838-Advertiser-Profiles).

1. Az Exportálás konfigurálásához válassza a **Tovább** lehetőséget.

## <a name="configure-the-connector"></a>Konfigurálja az összekötőt

1. Az **Adategyeztetés** szakaszban az **E-mail** mezőben jelölje ki az egyesített ügyfélprofil ügyfél e-mail-címét jelképező mezőjét. A szegmenseket exportálni kell az AdRollba.

1. Jelölje ki a szegmenseket, amelyeket exportálni szeretne. Jelöljön ki egy legalább 100 tagból álló szegmenst. Kisebb szegmensek nem exportálhatók. Az exportálni kívánt szegmens maximális mérete exportálásonként 250 000 tag. 

1. Válassza a **Mentés** parancsot.

## <a name="export-the-data"></a>Az adatok exportálása

[Igény szerint exportálhatja az adatot](export-destinations.md). Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) együtt is lefut.

## <a name="known-limitations"></a>Ismert korlátozások

- Összesen exportálásonként legfeljebb 250 000 ügyfélprofilt exportálhat az AdRollba.
- 100-nál kevesebb profillal rendelkező szegmensek nem exportálhatók az AdRollba. 
- Az AdRollba való exportálás csak szegmensekre korlátozódik.
- Legfeljebb 250 000 profil az AdRollba való exportálása eltarthat 10 percig. 
- A Marketoba exportálható profilok száma függ a AdRoll szerződéstől, és korlátozott.

## <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség

Amikor engedélyezi a Dynamics 365 Customer Insights szolgáltatást az adatok AdRoll szolgáltatásba való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat. A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy az AdRoll megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek. További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).

A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.
