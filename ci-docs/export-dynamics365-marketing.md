---
title: Szegmensek exportálása a Dynamics 365 Marketing rendszerbe (előzetes verzió)
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a Dynamics 365 Marketingbe.
ms.date: 08/24/2021
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: pkieffer
ms.author: philk
manager: shellyha
searchScope:
- ci-export
- customerInsights
ms.openlocfilehash: fed4ae1b017cca2b6060c4dda155859cd77e0daf
ms.sourcegitcommit: a97d31a647a5d259140a1baaeef8c6ea10b8cbde
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/29/2022
ms.locfileid: "9054619"
---
# <a name="export-segments-to-dynamics-365-marketing-preview"></a>Szegmensek exportálása a Dynamics 365 Marketing rendszerbe (előzetes verzió)

A [szegmensek](segments.md) segítségével kampányok és az ügyfelek adott csoportjaihoz fordulhat a Dynamics 365 Marketing alkalmazással. További tudnivalók: [szegmensek használata a Dynamics 365 Customer Insights szolgáltatásból a Dynamics 365 Marketing alkalmazással](/dynamics365/marketing/customer-insights-segments).

Ha a Dynamics 365 Marketing új lehetőségeit használja valós idejű ügyfélút-vezényleléshez egy Dataverse-szervezetben, nem kell szabványos exportálást létrehoznia a Dynamics 365 Marketing alkalmazásba. A Customer Insights kapcsolattartói és szegmensei közvetlenül a Dynamics 365 Marketing rendszerben érhetők el a Marketing és a Customer Insights összekapcsolása után. A meglévő exportálások törlése előtt tekintse át a Customer Insights és a Dynamics 365 Marketing ügyfélút vezénylés összekapcsolásának [dokumentációját](/dynamics365/marketing/real-time-marketing-ci-profile).

## <a name="prerequisite-for-a-connection"></a>Egy kapcsolat előfeltétele

- A kapcsolattartók bejegyzésének jelen kell lennie a Dynamics 365 Marketing alkalmazásban, mielőtt egy szegmenst exportálhatna a Customer Insights alkalmazásból a Marketing alkalmazásba. További információ a kapcsolattartók betöltéséről [a Dynamics 365 Marketing alkalmazásba a Microsoft Dataverse használatával](connect-dataverse-managed-lake.md).

  > [!NOTE]
  > A szegmensek Customer Insights szolgáltatásból Marketing formátumba történő exportálása nem hoz létre új kapcsolattartói rekordokat a Marketing-példányokban. A Marketing kapcsolattartói rekordjait be kell tölteni a Customer Insights szolgáltatásba, és adatforrás kell használni. Emellett szerepelniük kell az egyesített Ügyfél entitásban ahhoz, hogy a szegmensek exportálása előtt le tudják képezni az ügyfélazonosítókat.

## <a name="set-up-connection-to-marketing"></a>Állítsa be a Marketinggel való kapcsolatot

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza a **Dynamics 365 Marketing** lehetőséget a kapcsolat konfigurálásához.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Adja meg a szervezet Marketing URL-címét a **Kiszolgáló címe** mezőben.

1. A **Kiszolgáló rendszergazdai fiókja** területen válassza a **Bejelentkezés** lehetőséget, és válasszon egy Dynamics 365 Marketing fiókot.

1. Rendelje hozzá a Kapcsolattartó azonosítója mezőt a Vevő entitásban a Dynamics 365 kapcsolattartói azonosítóhoz.

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget. 

## <a name="configure-an-export"></a>Exportálás konfigurálása

Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz. További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Új exportálás létrehozásához válassza a **Célhely hozzáadása** lehetőséget.

1. A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot a Dynamics 365 Marketing szakaszból. Ha nem látja ezt a szakasznevet, az Ön számára nincs ilyen típusú kapcsolat.

1. Jelöljön ki egy vagy több szegmenst.

1. Válassza a **Mentés** parancsot.

Az exportálás mentése nem futtatja azonnal az exportálást.

Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut. Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand). 

[!INCLUDE [footer-include](includes/footer-banner.md)]
