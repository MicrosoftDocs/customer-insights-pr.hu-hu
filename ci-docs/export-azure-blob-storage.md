---
title: Adatok exportálása Azure Blob Storage (előzetes verzió)
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a Blob Storage-ba.
ms.date: 06/09/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: stefanie-msft
ms.author: sthe
manager: shellyha
ms.openlocfilehash: 059c8364ca0f3740bc0e4ffeeeba94246c9e5696
ms.sourcegitcommit: a97d31a647a5d259140a1baaeef8c6ea10b8cbde
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/29/2022
ms.locfileid: "9055493"
---
# <a name="export-data-to-an-azure-blob-storage-preview"></a>Adatok exportálása Azure Blob Storage (előzetes verzió)

A Customer Insights-adatokat a Blob Storage-ban tárolhatja, vagy segítségével adatait más alkalmazásokba továbbíthatja.

## <a name="known-limitations"></a>Ismert korlátozások

1. Az Azure Blob Storage esetében a [Normál teljesítmény és a Magasabb szintű teljesítményszint](/azure/storage/blobs/storage-blob-performance-tiers) közül választhat. Ha a Felsőkategóriás teljesítményszintet választja, akkor válassza a megfelelő [fióktípusként a premium blockblobok](/azure/storage/common/storage-account-overview#types-of-storage-accounts) lehetőséget.

## <a name="set-up-the-connection-to-blob-storage"></a>Állítsa be a Blob Storage-tárhelyel való kapcsolatot

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza az **Azure Blob Storage** lehetőséget a kapcsolat konfigurálásához.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Adja meg a Blob Storage fiókja **Fióknevét**, **Fiókkulcsát**, és **Tárolóját**.
    - Ha szeretne többet megtudni arról, hogyan találja meg a Blob Storage fiók nevét és fiókkulcsát, olvassa el a [Tárfiók beállításainak kezelése az Azure-portálon](/azure/storage/common/storage-account-manage) részt.
    - A tároló létrehozásával kapcsolatosan lásd: [Tároló létrehozása](/azure/storage/blobs/storage-quickstart-blobs-portal#create-a-container).

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget. 

## <a name="configure-an-export"></a>Exportálás konfigurálása

Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz. További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).

> [!IMPORTANT]
> Ha bekapcsolta az Azure Blob Storage-fiók ideiglenes törlési beállítását, az exportálás sikertelen lesz. Kikapcsolhatja az ideiglenes törlést, ha adatokat szeretne a blobokba exportálni. További információ: [Blob ideiglenes törlésének engedélyezése](/azure/storage/blobs/soft-delete-blob-enable)

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Új exportálás létrehozásához válassza a **Célhely hozzáadása** lehetőséget.

1. A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot az Azure Blob Storage szakaszból. Ha nem látja ezt a szakasznevet, akkor ilyen típusú kapcsolatok nem állnak az Ön rendelkezésére.

1. Jelölje be a jelölőnégyzetet azon entitások mellett, amelyeket exportálni szeretne erre a célhelyre.

1. Válassza a **Mentés** parancsot.

Az exportálás mentése nem futtatja azonnal az exportálást.

Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut.

Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand).

Az exportált adatok az Ön által konfigurált Blob Storage tárolóban lesznek tárolva. A tárolóban a következő elérési utak jönnek létre automatikusan:

- A rendszer által létrehozott forrásoldali entitások és entitások esetén:   
  `%ContainerName%/CustomerInsights_%instanceID%/%ExportDestinationName%/%EntityName%/%Year%/%Month%/%Day%/%HHMM%/%EntityName%_%PartitionId%.csv`  
  - Példa: `Dynamics365CustomerInsights/CustomerInsights_abcd1234-4312-11f4-93dc-24f72f43e7d5/BlobExport/HighValueSegment/2020/08/24/1433/HighValueSegment_1.csv`
  
  > [!TIP]
  > A nagy mennyiségű adatot tartalmazó entitások exportálása több CSV-fájlhoz vezethet ugyanabban a mappában minden exportáláshoz. Az exportálások felosztása teljesítménybeli okokból történik, hogy minimalizálja az exportálás befejezéséhez szükséges időt.

- Az exportált entitások model.json fájlja a(z) %ExportDestinationName% szinten lesz.  
  - Példa: `Dynamics365CustomerInsights/CustomerInsights_abcd1234-4312-11f4-93dc-24f72f43e7d5/BlobExport/model.json`

[!INCLUDE [footer-include](includes/footer-banner.md)]
