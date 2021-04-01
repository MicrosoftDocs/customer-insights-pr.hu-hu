---
title: A Customer Insights adatok exportálása az Azure Blob Storage rendszerbe
description: Megismerheti, hogyan konfigurálható a kapcsolat az Azure Blob Storage rendszerhez.
ms.date: 09/18/2020
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: phkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 0986ee5caf5fa079994ca584fb2c4d9294ddb80b
ms.sourcegitcommit: bae40184312ab27b95c140a044875c2daea37951
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/15/2021
ms.locfileid: "5596180"
---
# <a name="connector-for-azure-blob-storage-preview"></a>Az Azure Blob Storage (előzetes verzió) összekötője

A Customer Insights adatijat tárolhatja egy Azure Blob Storage-ban, vagy segítségével adatokat vihet át más alkalmazásokba.

## <a name="configure-the-connector-for-azure-blob-storage"></a>Az Azure Blob Storage összekötőjének konfigurálása

1. A célközönség információin belül nyissa meg a következőt **Rendszergazda** > **Exportálási célhelyek**.

1. Az **Azure Blob Storage** alatt válassza a **Beállítás** lehetőséget.

1. Írja be a **Partner nevét**, a **Partner kulcsát** és a **Tárolót** az Azure Blob Storage fiókjához.
    - Az Azure Blob Storage fióknév és fiókkulcs megkeresésével kapcsolatos további tudnivalókat lásd: [A tárolófiók beállításainak kezelése az Azure Portal webhelyen](/azure/storage/common/storage-account-manage).
    - A tároló létrehozásával kapcsolatosan lásd: [Tároló létrehozása](/azure/storage/blobs/storage-quickstart-blobs-portal#create-a-container).

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben.

1. Válassza a **Következő** lehetőséget.

1. Jelölje be a jelölőnégyzetet azon entitások mellett, amelyeket exportálni szeretne erre a célhelyre.

1. Válassza a **Mentés** parancsot.

Az exportált adatok tárolása a konfigurált Azure Blob Storage tárolóban történik. A tárolóban a következő elérési utak jönnek létre automatikusan:

- A rendszer által létrehozott forrásoldali entitások és entitások esetén: `%ContainerName%/CustomerInsights_%instanceID%/%ExportDestinationName%/%EntityName%/%Year%/%Month%/%Day%/%HHMM%/%EntityName%_%PartitionId%.csv`
  - Példa: `Dynamics365CustomerInsights/CustomerInsights_abcd1234-4312-11f4-93dc-24f72f43e7d5/BlobExport/HighValueSegment/2020/08/24/1433/HighValueSegment_1.csv`
- Az exportált entitások model.json fájlja az %ExportDestinationName% szintjén helyezkedik el
  - Példa: `Dynamics365CustomerInsights/CustomerInsights_abcd1234-4312-11f4-93dc-24f72f43e7d5/BlobExport/model.json`

## <a name="export-the-data"></a>Az adatok exportálása

[Igény szerint exportálhatja az adatot](export-destinations.md#export-data-on-demand). Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) együtt is lefut.


[!INCLUDE[footer-include](../includes/footer-banner.md)]