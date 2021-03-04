---
title: Customer Insights adatok exportálása az Autopilotba
description: Megismerheti, hogyan konfigurálható a kapcsolat a Autopilottal.
ms.date: 12/08/2020
ms.reviewer: philk
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: 33a8cd1ae4a77ce2248bc2805d25687c9a2c2732
ms.sourcegitcommit: 139548f8a2d0f24d54c4a6c404a743eeeb8ef8e0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/15/2021
ms.locfileid: "5269241"
---
# <a name="connector-for-autopilot-preview"></a>Az Autopilot összekötője (előzetes verzió)

Exportálja az egyesített ügyfélprofilok szegmenseit az Autopilotba, és használja őket kampányokhoz és e-mail marketinghez az Autopilotban. 

## <a name="prerequisites"></a>Előfeltételek

-   Rendelkezik [Autopilot-fiókkal](https://www.autopilothq.com/) és a megfelelő rendszergazdai hitelesítő adatokkal.
-   [Konfigurált szegmensekkel](segments.md) rendelkezik a célközönségi-információkban.
-   Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.

## <a name="connect-to-autopilot"></a>Csatlakozás az AutoPilothoz

1. Válassz a **Rendszergazda** > **Célok exportálása** lehetőséget.

1. Az **Autopilot** részben válassza a **Beállítás** lehetőséget.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben az export helyének.

   :::image type="content" source="media/export-autopilot.PNG" alt-text="Az Autopilot-kapcsolat konfigurációs ablaktáblája.":::

1. Adja meg az **Autopilot API kulcsát** [Autopilot API-kulcs](https://autopilot.docs.apiary.io/#).

1. Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.

1. Válassza a **Csatlakozás** lehetőséget az Autopilot kapcsolat inicializálásához.

1. Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.

1. Az Exportálás konfigurálásához válassza a **Tovább** lehetőséget.

## <a name="configure-the-connector"></a>Konfigurálja az összekötőt

1. Az **Adategyeztetés** szakaszban az **E-mail** mezőben jelölje ki az egyesített ügyfélprofil ügyfél e-mail-címét jelképező mezőjét. Ismételje meg ugyanezeket a lépéseket az egyéb választható mezőkön, például az **Utónév**, a **Vezetéknév**.

1. Jelölje ki a szegmenseket, amelyeket exportálni szeretne. Fokozottan **javasoljuk, hogy ne exportáljon összesen 100 000-nél több ügyfélprofilt** az Autopilotba. 

1. Válassza a **Mentés** parancsot.

## <a name="export-the-data"></a>Az adatok exportálása

[Igény szerint exportálhatja az adatot](export-destinations.md). Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) együtt is lefut.

## <a name="known-limitations"></a>Ismert korlátozások

- Összesen legfeljebb 100 000 ügyfélprofilt exportálhat az Autopilotba.
- Az Autopilotba való exportálás csak szegmensekre korlátozódik.
- Akár 100 000 profil Autopilotba való exportálása néhány órát is igénybe vehet. 
- Az Autopilotba exportálható profilok száma függ az Autopilot szerződésről, és korlátozott.

## <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség

Amikor engedélyezi a Dynamics 365 Customer Insights szolgáltatást az adatok Autopilot szolgáltatásba való átviteléhez, lehetővé teszi az adatok átvitelét a megfelelőségi határvonalon kívülre a Dynamics 365 Customer Insights szolgáltatás számára, beleértve a potenciálisan érzékeny adatokat, például a személyes adatokat. A Microsoft ezeket az adatokat átviszi az utasítás alapján, de Ön felelős azért, hogy az Autopilot megfeleljen az esetlegesen fennálló adatvédelmi és biztonsági kötelezettségeknek. További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).
A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.


[!INCLUDE[footer-include](../includes/footer-banner.md)]