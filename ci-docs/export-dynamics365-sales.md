---
title: Szegmensek exportálása a Dynamics 365 Sales rendszerbe (előzetes verzió)
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a Dynamics 365 Salesbe.
ms.date: 07/25/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: pkieffer
ms.author: philk
manager: shellyha
searchScope:
- ci-export
- customerInsights
ms.openlocfilehash: c3497f4625cada49ae33c6987e58994a15536f9b
ms.sourcegitcommit: 594081c82ca385f7143b3416378533aaf2d6d0d3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/27/2022
ms.locfileid: "9195984"
---
# <a name="export-segments-to-dynamics-365-sales-preview"></a>Szegmensek exportálása a Dynamics 365 Sales rendszerbe (előzetes verzió)

A Dynamics 365 Sales modullal az ügyféladatokból marketinglistákat hozhat létre, nyomon követheti a munkafolyamatokat, és promóciós anyagokat küldhet ki.

## <a name="prerequisites"></a>Előfeltételek

A kapcsolattartók bejegyzésének jelen kell lennie a Dynamics 365 Sales alkalmazásban, mielőtt egy szegmenst exportálhatna a Customer Insights alkalmazásból a Sales alkalmazásba. További információ arról, hogyan tölthet be névjegyeket a Dynamics 365 Sales rendszerből [a következő használatával:Microsoft Dataverse](connect-dataverse-managed-lake.md).

   > [!NOTE]
   > A szegmensek Customer Insights szolgáltatásból értékesítésbe való exportálása nem hoz létre új kapcsolattartói rekordokat az Értékesítési példányokban. A Sales kapcsolattartói rekordjait be kell tölteni a Customer Insights szolgáltatásba, és adatforrás kell használni. Emellett szerepelniük kell az egyesített Ügyfél entitásban ahhoz, hogy a szegmensek exportálása előtt le tudják képezni az ügyfélazonosítókat.

## <a name="known-limitations"></a>Ismert korlátozások

A Dynamics 365 Sales rendszerbe irányuló exportálások szegmensenként 100 000-re vannak korlátozva, ami akár 3 órát is igénybe vehet.

## <a name="set-up-connection-to-sales"></a>Kapcsolat beállítása az Értékesítésekhez

[!INCLUDE [export-connection-include](includes/export-connection-admn.md)]

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a Kapcsolat **hozzáadása lehetőséget**, majd válassza a Dynamics 365 Sales **lehetőséget**.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Alapértelmezés szerint csak a rendszergazdák. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Adja meg a szervezet értékesítési URL-címét a **Kiszolgáló címe** mezőben.

1. A **Kiszolgáló rendszergazdai fiókja** területen válassza a **Bejelentkezés** lehetőséget, és válasszon egy Dynamics 365 Sales fiókot.

1. Az ügyfélazonosító mező leképezése a Dynamics 365 kapcsolattartói azonosítóhoz.

1. Tekintse át az adatvédelmet és a megfelelőséget, és válassza az [Elfogadom lehetőséget](connections.md#data-privacy-and-compliance)**.**

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

## <a name="configure-an-export"></a>Exportálás konfigurálása

[!INCLUDE [export-permission-include](includes/export-permission.md)]

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Válassza az Exportálás **hozzáadása lehetőséget**.

1. A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot a Dynamics 365 Sales szakaszból. Ha nem érhető el egy kapcsolat sem, akkor forduljon a rendszergazdához.

1. Adja meg az exportálás nevét.

1. Válassza ki a Kapcsolattartói azonosító mezőt a Vevő entitásban, amely megegyezik a Dynamics 365 kapcsolattartói azonosítóval.

1. Jelölje ki a szegmenseket, amelyeket exportálni szeretne.

1. Válassza a **Mentés** lehetőséget

[!INCLUDE [export-saving-include](includes/export-saving.md)]

[!INCLUDE [footer-include](includes/footer-banner.md)]
