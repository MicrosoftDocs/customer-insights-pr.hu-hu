---
title: Customer Insights-adatok exportálása a LinkedIn Ads szolgáltatásba
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a LinkedIn Adsbe.
ms.date: 10/08/2021
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: conceptual
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 7a6bb466652b8703a4784329a5e675965f557e82
ms.sourcegitcommit: e7cdf36a78a2b1dd2850183224d39c8dde46b26f
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/16/2022
ms.locfileid: "8231106"
---
# <a name="export-segments-to-linkedin-ads-preview"></a>Szegmensek exportálása a LinkedIn Ads szolgáltatásba (előzetes verzió)

Az egyesített ügyfélprofilok szegmenseinek exportálása a LinkedIn Ads-szolgáltatásba, hogy egyeztetett célközönségeket hozzon létre. Használja az egyeztetett célközönségeket a vállalati célzáshoz és a kapcsolati célzáshoz.

## <a name="prerequisites"></a>Előfeltételek

-   Van egy [LinkedIn Campaign Manager-fiókja](https://business.linkedin.com/marketing-solutions/ads) és ahhoz tartozó rendszergazdai hitelesítő adatai.
-   [Konfigurált szegmensekkel](segments.md) rendelkezik a célközönségi-információkban.
-   Az exportált szegmensek ügyfélprofiljai egy e-mail-címmel rendelkező mezőt tartalmaznak.

## <a name="known-limitations"></a>Ismert korlátozások

- A Customer Insights szegmensének legalább 300 egyedi profilt kell tartalmaznia. 
- Exportálásonként legfeljebb 100 000 ügyfélprofilt exportálhat a LinkedIn Ads hirdetésekbe.
- A LinkedIn Ads szolgáltatásba való exportálás a szegmensekre korlátozódik.
- 100 000 ügyfélprofil exportálása a LinkedIn Ads hirdetésekbe akár 10 percet is igénybe vehet. 

## <a name="set-up-the-connection-to-linkedin-ads"></a>Állítsa be a LinkedIn Ads szolgáltatással való kapcsolatot

1. A célközönség információkban menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza a **LinkedIn Ads** lehetőséget a kapcsolat konfigurálásához.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a rendszergazdák. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Adja meg [LinkedIn Campaign Manager fiókazonosítóját](https://www.linkedin.com/help/lms/answer/a424270).

1. Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.

1. Válassza a **Kapcsolat** lehetőséget a Campaign Monitor kapcsolatának inicializálására.

1. Válassza a **Hitelesítés a LinkedInnel** lehetőséget, és adja meg a LinkedIn Campaign Manager hitelesítő adatait.

1. Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

## <a name="configure-an-export"></a>Exportálás konfigurálása

Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz. További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Új exportálás létrehozásához válassza a **Célhely hozzáadása** lehetőséget.

1. A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot a LinkedIn Ads szakaszból. Ha nem látja ezt a szakasznevet, az Ön számára nincs ilyen típusú kapcsolat.

1. Válassza ki, hogy az adatokat a LinkedIn-en [kapcsolati célzáshoz](https://business.linkedin.com/marketing-solutions/ad-targeting/contact-targeting) vagy [Vállalati célzáshoz](https://business.linkedin.com/marketing-solutions/ad-targeting/account-targeting) exportálja. 

1. A kapcsolattartók célzása érdekében az **Adatok egyeztetése** szakaszban jelöljön ki legalább egy olyan mezőt, amely az ügyfél e-mail címét, az Apple Ad ID azonosítót, a Google Ad ID azonosítót, a Google Felhasználói azonosítót, illetve a vezetéknevet tartalmazza. Ha a vállalat célzását választja, akkor jelöljön ki legalább egy olyan mezőt, amely cégnevet, e-mail tartományt, LinkedIn-oldal URL-címét, Tőzsdei szimbólumot vagy Webhelyet jelképez. Az exportálás további mezői választhatók ki. 

1. Jelölje ki a szegmenseket, amelyeket exportálni szeretne. A LinkedIn Campaign Manager egyeztetett célközönségei automatikusan létrejönnek az exportálásra kiválasztott szegmensek nevével. Minden szegmens külön egyeztetett célközönséget eredményez. 

1. Válassza a **Mentés** parancsot.

Az exportálás mentése nem futtatja azonnal az exportálást.

Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut. Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand). 


## <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség

Amikor engedélyezi Dynamics 365 Customer Insights számára, hogy adatokat továbbítson a LinkedIn Ads számára, akkor lehetővé teszi az adatok továbbítását a Dynamics 365 Customer Insights megfelelési határán kívülre is, beleértve az esetlegesen bizalmas adatokat is, például a Személyes adatokat. A Microsoft az Ön utasítására továbbítja az adatokat, de Ön a felelős azért, hogy a LinkedIn Ads megfeleljen az esetleges adatvédelmi vagy biztonsági kötelezettségeknek. További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).

A funkció használatának leállítása érdekében az Ön Dynamics 365 Customer Insights rendszergazdája bármikor eltávolíthatja ezt az exportálási célhelyet.
