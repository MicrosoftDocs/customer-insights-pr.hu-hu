---
title: Adatok exportálása a Gen2-be Azure Data Lake Storage (előzetes verzió)
description: Megismerheti, hogyan konfigurálható a kapcsolat az Azure Data Lake Storage Gen2 tárhellyel.
ms.date: 07/25/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: stefanie-msft
ms.author: sthe
manager: shellyha
ms.openlocfilehash: 55a61e4d9166df7809a64aeb1168a730402aaed6
ms.sourcegitcommit: 594081c82ca385f7143b3416378533aaf2d6d0d3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/27/2022
ms.locfileid: "9196443"
---
# <a name="export-data-to-azure-data-lake-storage-gen2-preview"></a>Adatok exportálása a Gen2-be Azure Data Lake Storage (előzetes verzió)

A Customer Insights adatokat a Data Lake Storage Gen2 fiókban tárolhatja, vagy segítségével adatait más alkalmazásokba továbbíthatja.

## <a name="prerequisites"></a>Előfeltételek

- Az [Azure Data Lake Gen2-vel használható tárfiók](/azure/storage/blobs/create-data-lake-storage-account). A tárfiók nevének és kulcsának megkereséséhez lásd: [Tárfiók-beállítások kezelése a Azure Portal](/azure/storage/common/storage-account-manage).
- Egy [Azure Blob Storage-tároló](/azure/storage/blobs/storage-quickstart-blobs-portal#create-a-container).

## <a name="known-limitations"></a>Ismert korlátozások

- A Gen2 esetében Azure Data Lake Storage válasszon a Standard teljesítmény és a Prémium teljesítményszint [között](/azure/storage/blobs/create-data-lake-storage-account). Ha a Felsőkategóriás teljesítményszintet választja, akkor válassza a megfelelő [fióktípusként a premium blockblobok](/azure/storage/common/storage-account-overview#types-of-storage-accounts) lehetőséget.

## <a name="set-up-connection-to-azure-data-lake-storage-gen2"></a>Kapcsolat beállítása a Gen2-höz Azure Data Lake Storage

[!INCLUDE [export-connection-include](includes/export-connection-admn.md)]

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a Kapcsolat **hozzáadása,** majd az Azure Data Lake Gen 2 **lehetőséget**.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Alapértelmezés szerint csak a rendszergazdák. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Adja meg a **Fiók neve**, a **Fiók kulcsa** és a **Tároló** adatait az Azure Data Lake Storage Gen2 tárolóhoz.

1. Tekintse át az adatvédelmet és a megfelelőséget, és válassza az [Elfogadom lehetőséget](connections.md#data-privacy-and-compliance)**.**

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

## <a name="configure-an-export"></a>Exportálás konfigurálása

[!INCLUDE [export-permission-include](includes/export-permission.md)]

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Válassza az Exportálás **hozzáadása lehetőséget**.

1. **A Kapcsolat exportáláshoz** mezőben válasszon ki egy kapcsolatot az Azure Data Lake szakaszból. Ha nem érhető el egy kapcsolat sem, akkor forduljon a rendszergazdához.

1. Adja meg az exportálás nevét.

1. Adja meg a Gen2-tároló mappanevét Azure Data Lake Storage.

1. Jelölje be a jelölőnégyzetet azon entitások mellett, amelyeket exportálni szeretne erre a célhelyre.

1. Válassza a **Mentés** parancsot.

[!INCLUDE [export-saving-include](includes/export-saving.md)]

Az exportált adatok az Ön által konfigurált az Azure Data Lake Gen 2 tárolóban lesznek tárolva.

> [!TIP]
> A nagy mennyiségű adatot tartalmazó entitások exportálása több CSV-fájlhoz vezethet ugyanabban a mappában minden exportáláshoz. Az exportálások felosztása teljesítménybeli okokból történik, hogy minimalizálja az exportálás befejezéséhez szükséges időt.

[!INCLUDE [footer-include](includes/footer-banner.md)]
