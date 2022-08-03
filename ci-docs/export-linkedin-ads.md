---
title: Szegmensek exportálása a LinkedIn Ads szolgáltatásba (előzetes verzió)
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a LinkedIn Adsbe.
ms.date: 07/25/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: conceptual
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: d1a9ae985043398f4bc38163be26ecf0c3c8e2ba
ms.sourcegitcommit: 594081c82ca385f7143b3416378533aaf2d6d0d3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/27/2022
ms.locfileid: "9196811"
---
# <a name="export-segments-to-linkedin-ads-preview"></a>Szegmensek exportálása a LinkedIn Ads szolgáltatásba (előzetes verzió)

Az egyesített ügyfélprofilok szegmenseinek exportálása a LinkedIn Ads-szolgáltatásba, hogy egyeztetett célközönségeket hozzon létre. Használja az egyeztetett célközönségeket a vállalati célzáshoz és a kapcsolati célzáshoz.

## <a name="prerequisites"></a>Előfeltételek

- Egy [LinkedIn Campaign Manager fiók](https://business.linkedin.com/marketing-solutions/ads) és a megfelelő rendszergazdai hitelesítő adatok.
- Fiókazonosító [LinkedIn Campaign Manager](https://www.linkedin.com/help/lms/answer/a424270).
- [Konfigurált szegmensek](segments.md) a Customer Insights szolgáltatásban.
- Az exportált szegmensekben található egyesített ügyfélprofilok tartalmaznak mezőt, amelyek az e-mail-címet tartalmazza.

## <a name="known-limitations"></a>Ismert korlátozások

- LinkedIn-hirdetésekbe való exportálásonként akár 100 000 ügyfélprofil is lehet, ami akár 10 percet is igénybe vehet.
- Csak szegmensek. Egy szegmensnek legalább 300 egyedi profilt kell tartalmaznia.

## <a name="set-up-connection-to-linkedin-ads"></a>Kapcsolat beállítása a LinkedIn-hirdetésekkel

[!INCLUDE [export-connection-include](includes/export-connection-admn.md)]

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a Kapcsolat **hozzáadása,** majd a LinkedIn-hirdetések **lehetőséget**.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Alapértelmezés szerint csak a rendszergazdák. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Adja meg fiókazonosítóját LinkedIn Campaign Manager.

1. Tekintse át az adatvédelmet és a megfelelőséget, és válassza az [Elfogadom lehetőséget](connections.md#data-privacy-and-compliance)**.**

1. Válassza a Csatlakozás **lehetőséget** a kapcsolat inicializálásához.

1. Válassza a **Hitelesítés a LinkedInnel** lehetőséget, és adja meg a LinkedIn Campaign Manager hitelesítő adatait.

1. Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

## <a name="configure-an-export"></a>Exportálás konfigurálása

[!INCLUDE [export-permission-include](includes/export-permission.md)]

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Válassza az Exportálás **hozzáadása lehetőséget**.

1. A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot a LinkedIn Ads szakaszból. Ha nem érhető el egy kapcsolat sem, akkor forduljon a rendszergazdához.

1. Adja meg az exportálás nevét.

1. Válassza ki, hogy az adatokat a LinkedIn-en [kapcsolati célzáshoz](https://business.linkedin.com/marketing-solutions/ad-targeting/contact-targeting) vagy [Vállalati célzáshoz](https://business.linkedin.com/marketing-solutions/ad-targeting/account-targeting) exportálja.

1. A kapcsolattartók célzása érdekében az **Adatok egyeztetése** szakaszban jelöljön ki legalább egy olyan mezőt, amely az ügyfél e-mail címét, az Apple Ad ID azonosítót, a Google Ad ID azonosítót, a Google Felhasználói azonosítót, illetve a vezetéknevet tartalmazza. Ha a vállalat célzását választja, akkor jelöljön ki legalább egy olyan mezőt, amely cégnevet, e-mail tartományt, LinkedIn-oldal URL-címét, Tőzsdei szimbólumot vagy Webhelyet jelképez.

1. Ha szükséges, adjon hozzá mezőket az exportálás további meghatározásához. Válassza az **Attribútum hozzáadása** lehetőséget a mezők leképezéséhez.

1. Jelölje ki a szegmenseket, amelyeket exportálni szeretne. A LinkedIn Campaign Manager egyeztetett célközönségei automatikusan létrejönnek az exportálásra kiválasztott szegmensek nevével. Minden szegmens külön egyeztetett célközönséget eredményez.

1. Válassza a **Mentés** parancsot.

[!INCLUDE [export-saving-include](includes/export-saving.md)]

[!INCLUDE [footer-include](includes/footer-banner.md)]
