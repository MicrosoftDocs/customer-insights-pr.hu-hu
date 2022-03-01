---
title: Customer Insights adatok exportálása Azure Data Lake Storage Gen 2 tárhelyre
description: Megismerheti, hogyan konfigurálható a kapcsolat az Azure Data Lake Storage Gen2 tárhellyel.
ms.date: 02/04/2021
ms.reviewer: sthe
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: b00c3d6178150cbc93fe800779f094809d4dc67b
ms.sourcegitcommit: 0260ed244b97c2fd0be5e9a084c4c489358e8d4f
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/18/2021
ms.locfileid: "5477182"
---
# <a name="connector-for-azure-data-lake-storage-gen2-preview"></a>Az Azure Data Lake Storage Gen2 összekötője (előzetes verzió)

A Customer Insights-adatokat az Azure Data Lake Storage Gen2 tárolóban tárolhatja, vagy segítségével adatait más alkalmazásokba továbbíthatja.

## <a name="configure-the-connector-for-azure-data-lake-storage-gen2"></a>Az Azure Data Lake Storage Gen2 összekötőjének konfigurálása

1. A célközönség információin belül nyissa meg a következőt **Rendszergazda** > **Exportálási célhelyek**.

1. A **Azure Data Lake Storage Gen2** részben válassza a **Beállítás** lehetőséget.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben.

1. Adja meg a **Fiók neve**, a **Fiók kulcsa** és a **Tároló** adatait az Azure Data Lake Storage Gen2 tárolóhoz.
    - Ha meg szeretne ismerkedni vele, hogyan hozhat létre tárhelyfiókot az Azure Data Lake Storage Gen2 tárhellyel való használatra, olvassa el a [Tárhelyfiók létrehozása](https://docs.microsoft.com/azure/storage/blobs/create-data-lake-storage-account) részt. 
    - Ha szeretne többet megtudni az Azure Data Lake Gen2 tárfiók nevének és fiókkulcsának megkereséséről, olvassa el a [Tárfiók beállításainak kezelése az Azure portálon](https://docs.microsoft.com/azure/storage/common/storage-account-manage) című részt.

1. Válassza a **Következő** lehetőséget.

1. Jelölje be a jelölőnégyzetet azon entitások mellett, amelyeket exportálni szeretne erre a célhelyre.

1. Válassza a **Mentés** parancsot.

## <a name="export-the-data"></a>Az adatok exportálása

[Igény szerint exportálhatja az adatot](export-destinations.md#export-data-on-demand). Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) együtt is lefut.
