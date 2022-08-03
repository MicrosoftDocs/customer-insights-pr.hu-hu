---
title: Szegmensek exportálása a Dynamics 365 Marketing rendszerbe (előzetes verzió)
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a Dynamics 365 Marketingbe.
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
ms.openlocfilehash: 123b565421a7d096e7341a8f600f91e59aefe8d0
ms.sourcegitcommit: 594081c82ca385f7143b3416378533aaf2d6d0d3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/27/2022
ms.locfileid: "9196627"
---
# <a name="export-segments-to-dynamics-365-marketing-preview"></a>Szegmensek exportálása a Dynamics 365 Marketing rendszerbe (előzetes verzió)

Szegmensek [használatával](segments.md) kampányokat hozhat létre, és kapcsolatba léphet az ügyfelek adott csoportjaival a Dynamics 365 Marketing [segítségével](/dynamics365/marketing/customer-insights-segments).

Ha a Dynamics 365 Marketing új lehetőségeit használja valós idejű ügyfélút-vezényleléshez egy Dataverse-szervezetben, nem kell szabványos exportálást létrehoznia a Dynamics 365 Marketing alkalmazásba. A Customer Insights kapcsolattartói és szegmensei közvetlenül a Dynamics 365 Marketing rendszerben érhetők el a Marketing és a Customer Insights összekapcsolása után. A meglévő exportálások törlése előtt tekintse át a Customer Insights és a Dynamics 365 Marketing ügyfélút vezénylés összekapcsolásának [dokumentációját](/dynamics365/marketing/real-time-marketing-ci-profile).

## <a name="prerequisite"></a>Előfeltétel

A kapcsolattartók bejegyzésének jelen kell lennie a Dynamics 365 Marketing alkalmazásban, mielőtt egy szegmenst exportálhatna a Customer Insights alkalmazásból a Marketing alkalmazásba. További információ a kapcsolattartók betöltéséről [a Dynamics 365 Marketing alkalmazásba a Microsoft Dataverse használatával](connect-dataverse-managed-lake.md).

> [!NOTE]
> A szegmensek Customer Insights szolgáltatásból Marketing formátumba történő exportálása nem hoz létre új kapcsolattartói rekordokat a Marketing-példányokban. A Marketing kapcsolattartói rekordjait be kell tölteni a Customer Insights szolgáltatásba, és adatforrás kell használni. Emellett szerepelniük kell az egyesített Ügyfél entitásban ahhoz, hogy a szegmensek exportálása előtt le tudják képezni az ügyfélazonosítókat.

## <a name="set-up-connection-to-marketing"></a>Állítsa be a Marketinggel való kapcsolatot

[!INCLUDE [export-connection-include](includes/export-connection-admn.md)]

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a Kapcsolat **hozzáadása lehetőséget**, majd válassza a Dynamics 365 Marketing **lehetőséget**.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Alapértelmezés szerint csak a rendszergazdák. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Adja meg a szervezet Marketing URL-címét a **Kiszolgáló címe** mezőben.

1. A **Kiszolgáló rendszergazdai fiókja** területen válassza a **Bejelentkezés** lehetőséget, és válasszon egy Dynamics 365 Marketing fiókot.

1. Rendelje hozzá a Kapcsolattartó azonosítója mezőt a Vevő entitásban a Dynamics 365 kapcsolattartói azonosítóhoz.

1. Tekintse át az adatvédelmet és a megfelelőséget, és válassza az [Elfogadom lehetőséget](connections.md#data-privacy-and-compliance)**.**

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

## <a name="configure-an-export"></a>Exportálás konfigurálása

[!INCLUDE [export-permission-include](includes/export-permission.md)]

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Válassza az Exportálás **hozzáadása lehetőséget**.

1. A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot a Dynamics 365 Marketing szakaszból. Ha nem érhető el egy kapcsolat sem, akkor forduljon a rendszergazdához.

1. Adja meg az exportálás nevét.

1. Válassza ki a Kapcsolattartói azonosító mezőt a Vevő entitásban, amely megegyezik a Dynamics 365 kapcsolattartói azonosítóval.

1. Jelölje ki a szegmenseket, amelyeket exportálni szeretne.

1. Válassza a **Mentés** parancsot.

[!INCLUDE [export-saving-include](includes/export-saving.md)]

[!INCLUDE [footer-include](includes/footer-banner.md)]
