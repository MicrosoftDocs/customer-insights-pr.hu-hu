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
ms.openlocfilehash: c7a4b1be1c959d70fad929b56452169b40e5b592
ms.sourcegitcommit: c3ae7e7e0c9566f9479ba71a26afc5a17fb589c2
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/27/2022
ms.locfileid: "9724601"
---
# <a name="export-segments-to-facebook-ads-manager-preview"></a>Szegmensek exportálása a Hirdetéskezelőbe Facebook (előzetes verzió)

Az egyesített ügyfélprofilokat tartalmazó szegmensek exportálása a Facebook hirdetéskezelőbe kampányok létrehozásához a Facebook-on és az Instagramon.

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWO1aN]

## <a name="prerequisites"></a>Előfeltételek

- Üzleti [Facebook fiókot tartalmazó](https://www.facebook.com/business/learn/lessons/step-by-step-ads-manager-account) hirdetési fiók [Facebook](https://business.facebook.com/).
- Rendszergazdai jogosultságok a [Facebook hirdetési fiókban](https://www.facebook.com/business/learn/lessons/step-by-step-ads-manager-account).
- Az egyéni célközönség feltételeket el kell fogadnia annak a felhasználónak, aki beállítja a kapcsolatot a Customer Insights alkalmazásban.

## <a name="known-limitations"></a>Ismert korlátozások

- A Hirdetéskezelőbe Facebook exportálásonként akár 10 millió ügyfélprofil is lehet, ami akár 90 percet is igénybe vehet.
- Csak szegmensek.
- Facebook A hirdetések integrációja nem támogatja a 25-nél több hirdetési fiókkal rendelkező felhasználókat.
- Facebook *ügyféllista* típusa csak egyéni célközönségek [esetén](https://www.facebook.com/business/help/744354708981227?id=2469097953376494).
  > [!NOTE]
  > Bizonyos esetekben különböző típusú egyéni célközönségek jelenhetnek meg a legördülő listában. Ha az ügyféllistától *eltérő* típust választ, az exportálás sikertelen lesz.

## <a name="set-up-connection-to-facebook-ads-manager"></a>Kapcsolat beállítása a Facebook Hirdetéskezelőhöz

[!INCLUDE [export-connection-include](includes/export-connection-admn.md)]

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válaszd a Kapcsolat **hozzáadása, majd a** Hirdetéskezelő **Facebook lehetőséget**.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. [Engedélyezze a közreműködők számára, hogy a kapcsolatot exportáláshoz](connections.md#allow-contributors-to-use-a-connection-for-exports) használják.

1. Hitelesítés a Facebook-hirdetések használatával:

   1. A **Folytatás Facebook** gomb kiválasztásával jelentkezzen be a Facebook hirdetési fiókjába.

   1. A hitelesítés után engedélyezze a **ads_management** engedélyt a Facebookkal.

   1. Válassza ki a **Facebook hirdetési fiókot**, amellyel dolgozni kíván.

   1. Válasszon egy **meglévő egyéni célközönséget** a legördülő listából, vagy hozzon létre egy **új egyéni célközönséget**.

1. Tekintse át az adatvédelmet és a megfelelőséget [, és válassza az](connections.md#data-privacy-and-compliance) Elfogadom **lehetőséget**.

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

## <a name="configure-an-export"></a>Exportálás konfigurálása

[!INCLUDE [export-permission-include](includes/export-permission.md)]

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Válassza az Exportálás **hozzáadása lehetőséget**.

1. A Kapcsolat exportáláshoz **mezőben** válassz ki egy kapcsolatot a Facebook Hirdetéskezelő területen. Ha nem érhető el egy kapcsolat sem, akkor forduljon a rendszergazdához.

1. Adja meg az exportálás nevét.

1. **A Kapcsolódási adatok** mezőben válaszd az E-mail-cím **, a Név és cím** vagy **a Telefonszám lehetőséget**, **amelyet el szeretnél küldeni a** Hirdetéskezelőnek Facebook.

1. Képezze le a megfelelő attribútumokat az egyesített ügyfél entitásból a kiválasztott kulcsazonosítóhoz.
   > [!TIP]
   > A legjobb esély akkor van az egyezésre, ha az **E-mail-cím** lehetőséget választja kulcsazonosítónak. A további azonosítók hozzáadásával javíthatja a megfeleltetést.

1. Válassza az **Attribútum hozzáadása** lehetőséget a több attribútum leképzésének Facebook hirdetéskezelőbe küldéséhez. A Facebook hirdetéskezelő attribútumai a következő felhasználóbarát neveket használják a leképezéshez: **FN** = **Keresztnév**, **LN** = **Utónév**, **FI** = **Első kezdőbetű**, **PHONE** = **Telefon**, **GEN** = **Nem**, **DOB** = **Születési idő**, **ST** = **Állam**, **CT** = **Város**, **ZIP** = **Irányítószám / postafiók**, **COUNTRY** = **Ország/régió**

1. Jelölje ki a szegmenseket, amelyeket exportálni szeretne.

1. Válassza a **Mentés** parancsot.

[!INCLUDE [export-saving-include](includes/export-saving.md)]

[!INCLUDE [footer-include](includes/footer-banner.md)]
