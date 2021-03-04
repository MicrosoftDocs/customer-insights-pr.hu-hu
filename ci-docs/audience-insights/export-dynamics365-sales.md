---
title: A Customer Insights adatok a Dynamics 365 Salesbe való exportálása
description: Megismerheti, hogyan konfigurálható a kapcsolat a Dynamics 365 Sales megoldással.
ms.date: 02/01/2021
ms.reviewer: philk
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: 0013c4e6a96401d6cdbea55ed38f85f5e10dcc56
ms.sourcegitcommit: 139548f8a2d0f24d54c4a6c404a743eeeb8ef8e0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/15/2021
ms.locfileid: "5269011"
---
# <a name="connector-for-dynamics-365-sales-preview"></a>Dynamics 365 Sales összekötője (előzetes verzió)

[!INCLUDE [cc-data-platform-banner](../includes/cc-data-platform-banner.md)]

A Dynamics 365 Sales modullal az ügyféladatokból marketinglistákat hozhat létre, nyomon követheti a munkafolyamatokat, és promóciós anyagokat küldhet ki.

## <a name="prerequisite"></a>Előfeltétel

1. A kapcsolattartók bejegyzésének jelen kell lennie a Dynamics 365 Sales alkalmazásban, mielőtt egy szegmenst exportálhatna a Customer Insights alkalmazásból a Sales alkalmazásba. További információ a kapcsolattartók betöltéséről [a Dynamics 365 Sales alkalmazásba a Common Data Services használatával](connect-power-query.md).

   > [!NOTE]
   > Ha szegmenseket exportál a célközönséggel kapcsolatos információkból a Sales nem hoz létre új kapcsolattartói rekordokat a Sales példányban. A Sales kapcsolattartói bejegyzéseket be kell tölteni a célközönség kapcsolatos információkba és adatforrásként használni. Emellett szerepelniük kell az egyesített Ügyfél entitásban ahhoz, hogy a szegmensek exportálása előtt le tudják képezni az ügyfélazonosítókat.

## <a name="configure-the-connector-for-sales"></a>A Sales összekötő beállítása

1. A célközönség információin belül nyissa meg a következőt **Rendszergazda** > **Exportálási célhelyek**.

1. A **Dynamics 365 Sales** alatt válassza a **Beállítás** lehetőséget.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben az export helyének.

1. Adja meg a szervezet értékesítési URL-címét a **Kiszolgáló címe** mezőben.

1. A **Kiszolgáló rendszergazdai fiókja** területen válassza a **Bejelentkezés** lehetőséget, és válasszon egy Dynamics 365 Sales fiókot.

1. Az ügyfélazonosító mező leképezése a Dynamics 365 kapcsolattartói azonosítóhoz.

1. Válassza a **Következő** lehetőséget.

1. Jelöljön ki egy vagy több szegmenst.

1. Válassza a **Mentés** parancsot.

## <a name="export-the-data"></a>Az adatok exportálása

[Igény szerint exportálhatja az adatot](export-destinations.md). Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) együtt is lefut.


[!INCLUDE[footer-include](../includes/footer-banner.md)]