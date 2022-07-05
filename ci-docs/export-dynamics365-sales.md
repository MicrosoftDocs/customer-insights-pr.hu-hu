---
title: Szegmensek exportálása a Dynamics 365 Sales rendszerbe (előzetes verzió)
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a Dynamics 365 Salesbe.
ms.date: 03/03/2021
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: pkieffer
ms.author: philk
manager: shellyha
searchScope:
- ci-export
- customerInsights
ms.openlocfilehash: b8e756313ca037dca41cb25587229808f0c584c9
ms.sourcegitcommit: dca46afb9e23ba87a0ff59a1776c1d139e209a32
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/29/2022
ms.locfileid: "9082386"
---
# <a name="export-segments-to-dynamics-365-sales-preview"></a>Szegmensek exportálása a Dynamics 365 Sales rendszerbe (előzetes verzió)

A Dynamics 365 Sales modullal az ügyféladatokból marketinglistákat hozhat létre, nyomon követheti a munkafolyamatokat, és promóciós anyagokat küldhet ki.

## <a name="known-limitations"></a>Ismert korlátozások

- A Dynamics 365 Sales rendszerbe irányuló exportálások szegmensenként 100'000 tagra vannak korlátozva.
- A Dynamics 365 Sales rendszerbe irányuló szegmensexportálás akár 3 órát is igénybe vehet. 

## <a name="prerequisite-for-connection"></a>A kapcsolat előfeltétele

1. A kapcsolattartók bejegyzésének jelen kell lennie a Dynamics 365 Sales alkalmazásban, mielőtt egy szegmenst exportálhatna a Customer Insights alkalmazásból a Sales alkalmazásba. További információ arról, hogyan tölthet be névjegyeket a Dynamics 365 Sales rendszerből [a következő használatával: Microsoft Dataverse](connect-dataverse-managed-lake.md).

   > [!NOTE]
   > A szegmensek Customer Insights szolgáltatásból értékesítésbe való exportálása nem hoz létre új kapcsolattartói rekordokat az Értékesítési példányokban. A Sales kapcsolattartói rekordjait be kell tölteni a Customer Insights szolgáltatásba, és adatforrás kell használni. Emellett szerepelniük kell az egyesített Ügyfél entitásban ahhoz, hogy a szegmensek exportálása előtt le tudják képezni az ügyfélazonosítókat.

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

[!INCLUDE [footer-include](includes/footer-banner.md)]
