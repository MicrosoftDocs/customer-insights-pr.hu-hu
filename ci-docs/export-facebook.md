---
title: Szegmensek exportálása a Hirdetéskezelőbe Facebook (előzetes verzió) (videót tartalmaz)
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a Facebook Hirdetéskezelő.
ms.date: 07/25/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 01be1a075db0da05dc5536aea8a33093f9a2ea13
ms.sourcegitcommit: 594081c82ca385f7143b3416378533aaf2d6d0d3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/27/2022
ms.locfileid: "9195017"
---
# <a name="export-segments-to-facebook-ads-manager-preview"></a>Szegmensek exportálása a Hirdetéskezelőbe Facebook (előzetes verzió)

Az egyesített ügyfélprofilokat tartalmazó szegmensek exportálása a Facebook hirdetéskezelőbe kampányok létrehozásához a Facebook-on és az Instagramon.

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWO1aN]

## <a name="prerequisites"></a>Előfeltételek

- Olyan [Facebook hirdetési fiók](https://www.facebook.com/business/learn/lessons/step-by-step-ads-manager-account), amely tartalmaz egy [Facebook üzleti fiókot](https://business.facebook.com/).
- Rendszergazdai jogosultságok a [Facebook Hirdetési fiókban](https://www.facebook.com/business/learn/lessons/step-by-step-ads-manager-account).

## <a name="known-limitations"></a>Ismert korlátozások

- A Hirdetéskezelőbe irányuló Facebook exportálásonként akár 10 millió ügyfélprofil is lehet, ami akár 90 percet is igénybe vehet.
- Csak szegmensek.
- Facebook *ügyféllista* típusa csak egyéni [célközönségekben](https://www.facebook.com/business/help/744354708981227?id=2469097953376494).
  > [!NOTE]
  > Bizonyos esetekben különböző típusú egyéni célközönségeket láthatsz a legördülő listában. Ha a vevőlistától *eltérő* típust választ, az exportálás sikertelen lesz.

## <a name="set-up-connection-to-facebook-ads-manager"></a>Kapcsolat beállítása a Facebook Hirdetéskezelőhöz

[!INCLUDE [export-connection-include](includes/export-connection-admn.md)]

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válaszd a Kapcsolat **hozzáadása,** majd a Hirdetéskezelő **Facebook lehetőséget**.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. [Lehetővé teszi a közreműködők számára, hogy a kapcsolatot exportálásra](connections.md#allow-contributors-to-use-a-connection-for-exports) használják.

1. Hitelesítés a Facebook-hirdetések használatával:

   1. A **Folytatás Facebook** gomb kiválasztásával jelentkezzen be a Facebook hirdetési fiókjába.

   1. A hitelesítés után engedélyezze a **ads_management** engedélyt a Facebookkal.

   1. Válassza ki a **Facebook hirdetési fiókot**, amellyel dolgozni kíván.

   1. Válasszon egy **meglévő egyéni célközönséget** a legördülő listából, vagy hozzon létre egy **új egyéni célközönséget**.

1. Tekintse át az adatvédelmet és a megfelelőséget, és válassza az [Elfogadom lehetőséget](connections.md#data-privacy-and-compliance)**.**

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

## <a name="configure-an-export"></a>Exportálás konfigurálása

[!INCLUDE [export-permission-include](includes/export-permission.md)]

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Válassza az Exportálás **hozzáadása lehetőséget**.

1. **A Kapcsolat exportáláshoz** mezőben válassz ki egy kapcsolatot a Facebook Hirdetéskezelő szakaszból. Ha nem érhető el egy kapcsolat sem, akkor forduljon a rendszergazdához.

1. Adja meg az exportálás nevét.

1. Az Adatok összekapcsolása mezőben válaszd ki az **E-mail-cím**, **a Név és cím** vagy **a Telefon** lehetőséget **, amelyet el szeretnél küldeni a Hirdetéskezelőnek**.Facebook

1. Képezze le a megfelelő attribútumokat az egyesített ügyfél entitásból a kiválasztott kulcsazonosítóhoz.
   > [!TIP]
   > A legjobb esély akkor van az egyezésre, ha az **E-mail-cím** lehetőséget választja kulcsazonosítónak. A további azonosítók hozzáadásával javíthatja a megfeleltetést.

1. Válassza az **Attribútum hozzáadása** lehetőséget a több attribútum leképzésének Facebook hirdetéskezelőbe küldéséhez. A Facebook hirdetéskezelő attribútumai a következő felhasználóbarát neveket használják a leképezéshez: **FN** = **Keresztnév**, **LN** = **Utónév**, **FI** = **Első kezdőbetű**, **PHONE** = **Telefon**, **GEN** = **Nem**, **DOB** = **Születési idő**, **ST** = **Állam**, **CT** = **Város**, **ZIP** = **Irányítószám / postafiók**, **COUNTRY** = **Ország/régió**

1. Jelölje ki a szegmenseket, amelyeket exportálni szeretne.

1. Válassza a **Mentés** parancsot.

[!INCLUDE [export-saving-include](includes/export-saving.md)]

[!INCLUDE [footer-include](includes/footer-banner.md)]
