---
title: Adatok exportálása Azure Blob Storage (előzetes verzió)
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja a Blob Storage-ba.
ms.date: 07/25/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: stefanie-msft
ms.author: sthe
manager: shellyha
ms.openlocfilehash: 22593ed05f403a40fe494e30f807b57658594f01
ms.sourcegitcommit: 594081c82ca385f7143b3416378533aaf2d6d0d3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/27/2022
ms.locfileid: "9195707"
---
# <a name="export-data-to-an-azure-blob-storage-preview"></a>Adatok exportálása Azure Blob Storage (előzetes verzió)

A Customer Insights-adatokat a Blob Storage-ban tárolhatja, vagy segítségével adatait más alkalmazásokba továbbíthatja.

## <a name="prerequisites"></a>Előfeltételek

- Egy [Azure Blob Storage-fiók](/azure/storage/blobs/create-data-lake-storage-account) neve és fiókkulcsa. A név és a kulcs megkereséséhez lásd: [Tárfiók-beállítások kezelése a Azure Portal](/azure/storage/common/storage-account-manage).
- Egy [Azure Blob Storage-tároló](/azure/storage/blobs/storage-quickstart-blobs-portal#create-a-container).

## <a name="known-limitations"></a>Ismert korlátozások

- Az Azure Blob Storage esetén válasszon a Standard teljesítmény és a Prémium teljesítményszint [között](/azure/storage/blobs/storage-blob-performance-tiers). Ha a Felsőkategóriás teljesítményszintet választja, akkor válassza a megfelelő [fióktípusként a premium blockblobok](/azure/storage/common/storage-account-overview#types-of-storage-accounts) lehetőséget.

## <a name="set-up-connection-to-blob-storage"></a>Kapcsolat beállítása a Blob Storage-hoz

[!INCLUDE [export-connection-include](includes/export-connection-admn.md)]

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a Kapcsolat **hozzáadása lehetőséget**, majd válassza az **Azure Blob Storage lehetőséget**.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Alapértelmezés szerint csak a rendszergazdák. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Adja meg a Blob Storage fiókja **Fióknevét**, **Fiókkulcsát**, és **Tárolóját**.

1. Tekintse át az adatvédelmet és a megfelelőséget, és válassza az [Elfogadom lehetőséget](connections.md#data-privacy-and-compliance)**.**

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

## <a name="configure-an-export"></a>Exportálás konfigurálása

Az exportálás konfigurálásához engedéllyel [kell rendelkeznie](export-destinations.md#set-up-a-new-export) ehhez a kapcsolattípushoz.

> [!IMPORTANT]
> Ha bekapcsolta az [Azure Blob Storage-fiók helyreállítható törlési beállítását](/azure/storage/blobs/soft-delete-blob-enable), az exportálás sikertelen lesz. Kikapcsolhatja az ideiglenes törlést, ha adatokat szeretne a blobokba exportálni.

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Válassza az Exportálás **hozzáadása lehetőséget**.

1. A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot az Azure Blob Storage szakaszból. Ha nem érhető el egy kapcsolat sem, akkor forduljon a rendszergazdához.

1. Adja meg az exportálás nevét.

1. Adja meg a Blob Storage mappanevét.

1. Jelölje be a jelölőnégyzetet azon entitások mellett, amelyeket exportálni szeretne erre a célhelyre.

1. Válassza a **Mentés** parancsot.

[!INCLUDE [export-saving-include](includes/export-saving.md)]

Az exportált adatok az Ön által konfigurált Blob Storage tárolóban lesznek tárolva. A tárolóban a következő elérési utak jönnek létre automatikusan:

- A rendszer által létrehozott forrásoldali entitások és entitások esetén:   
  *%ContainerName%/CustomerInsights_%instanceID%/%ExportDestinationName%/%EntityName%/%Year%/%Month%/%Day%/%HHMM%/%EntityName%_%PartitionId%.csv*  

  Példa: Dynamics365CustomerInsights/CustomerInsights_ abcd1234-4312-11f4-93dc-24f72f43e7d5/BlobExport/HighValueSegment/2020/08/24/1433/HighValueSegment_1.csv
  
  > [!TIP]
  > A nagy mennyiségű adatot tartalmazó entitások exportálása több CSV-fájlhoz vezethet ugyanabban a mappában minden exportáláshoz. Az exportálások felosztása teljesítménybeli okokból történik, hogy minimalizálja az exportálás befejezéséhez szükséges időt.

- Az exportált entitások model.json fájlja a *%ExportDestinationName%* szinten található.  
  
  Példa: Dynamics365CustomerInsights/CustomerInsights_ abcd1234-4312-11f4-93dc-24f72f43e7d5/BlobExport/model.json

[!INCLUDE [footer-include](includes/footer-banner.md)]
