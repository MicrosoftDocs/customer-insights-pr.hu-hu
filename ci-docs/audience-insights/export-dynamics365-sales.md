---
title: A Customer Insights adatok a Dynamics 365 Salesbe való exportálása
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a Dynamics 365 Salesbe.
ms.date: 03/03/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 328bb2f26ebcea234fb645e5225930ab12f82a8b
ms.sourcegitcommit: e8e03309ba2515374a70c132d0758f3e1e1851d0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/04/2021
ms.locfileid: "5976229"
---
# <a name="use-segments-in-dynamics-365-sales-preview"></a>Szegmensek használata a Dynamics 365 Sales alkalmazásban (előzetes verzió)

[!INCLUDE [cc-data-platform-banner](../includes/cc-data-platform-banner.md)]

A Dynamics 365 Sales modullal az ügyféladatokból marketinglistákat hozhat létre, nyomon követheti a munkafolyamatokat, és promóciós anyagokat küldhet ki.

## <a name="prerequisite-for-connection"></a>A kapcsolat előfeltétele

1. A kapcsolattartók bejegyzésének jelen kell lennie a Dynamics 365 Sales alkalmazásban, mielőtt egy szegmenst exportálhatna a Customer Insights alkalmazásból a Sales alkalmazásba. További információ a kapcsolattartók betöltéséről [a Dynamics 365 Sales alkalmazásba a Common Data Services használatával](connect-power-query.md).

   > [!NOTE]
   > Ha szegmenseket exportál a célközönséggel kapcsolatos információkból a Sales nem hoz létre új kapcsolattartói rekordokat a Sales példányban. A Sales kapcsolattartói bejegyzéseket be kell tölteni a célközönség kapcsolatos információkba és adatforrásként használni. Emellett szerepelniük kell az egyesített Ügyfél entitásban ahhoz, hogy a szegmensek exportálása előtt le tudják képezni az ügyfélazonosítókat.

## <a name="set-up-the-connection-to-sales"></a>Állítsa be a Sales rendszerrel való kapcsolatot

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza a **Dynamics 365 Sales** lehetőséget a kapcsolat konfigurálásához.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Adja meg a szervezet értékesítési URL-címét a **Kiszolgáló címe** mezőben.

1. A **Kiszolgáló rendszergazdai fiókja** területen válassza a **Bejelentkezés** lehetőséget, és válasszon egy Dynamics 365 Sales fiókot.

1. Az ügyfélazonosító mező leképezése a Dynamics 365 kapcsolattartói azonosítóhoz.

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget. 

## <a name="configure-an-export"></a>Exportálás konfigurálása

Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz. További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Új exportálás létrehozásához válassza a **Célhely hozzáadása** lehetőséget.

1. A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot a Dynamics 365 Sales szakaszból. Ha nem látja ezt a szakasznevet, az Ön számára nincs ilyen típusú kapcsolat.

1. Jelöljön ki egy vagy több szegmenst.

1. Válassza a **Mentés** lehetőséget

Az exportálás mentése nem futtatja azonnal az exportálást.

Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut. Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand). 

[!INCLUDE[footer-include](../includes/footer-banner.md)]
