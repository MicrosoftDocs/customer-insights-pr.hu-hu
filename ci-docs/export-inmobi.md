---
title: Customer Insights-adatok exportálása az InMobi-ba
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja az InMobi szolgáltatásba.
ms.date: 07/25/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: ef486ad6786ef01be977f3d6bda69ce8a2b081c7
ms.sourcegitcommit: 594081c82ca385f7143b3416378533aaf2d6d0d3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/27/2022
ms.locfileid: "9195891"
---
# <a name="export-customer-insights-data-to-inmobi-preview"></a>Customer Insights-adatok exportálása az InMobi szolgáltatásba (előzetes verzió)

Szegmenslistákat vagy egyéb adatokat exportálhat a Customer Insights-példányból az InMobi [szolgáltatásba](https://www.inmobi.com/).

## <a name="prerequisites"></a>Előfeltételek

- InMobi-fiók [és](https://www.inmobi.com/) rendszergazdai hitelesítő adatok.
- Egy [Azure Blob Storage-fiók](/azure/storage/blobs/create-data-lake-storage-account) neve és fiókkulcsa. A név és a kulcs megkereséséhez lásd: [Tárfiók-beállítások kezelése a Azure Portal](/azure/storage/common/storage-account-manage).
- Egy [Azure Blob Storage-tároló](/azure/storage/blobs/storage-quickstart-blobs-portal#create-a-container), amelybe InMobi-adatokat exportálhat.
- Az InMobi közvetlen kapcsolatot hoz létre a Blob Storage-ral, és konfigurálja az adatok automatikus importálását az InMobi szolgáltatásba. A folyamat kezdeményezéséhez lépjen kapcsolatba az InMobi képviselőjével.

## <a name="known-limitations"></a>Ismert korlátozások

- Az Azure Blob Storage esetén válasszon a Standard teljesítmény és a Prémium teljesítményszint [között](/azure/storage/blobs/storage-blob-performance-tiers). Ha a Felsőkategóriás teljesítményszintet választja, akkor válassza a megfelelő [fióktípusként a premium blockblobok](/azure/storage/common/storage-account-overview#types-of-storage-accounts) lehetőséget.

## <a name="set-up-connection-to-azure-blob-storage"></a>Kapcsolat beállítása az Azure Blob Storage-hoz

[Állítson be egy kapcsolatot az Azure Blob Storage-hoz](export-azure-blob-storage.md).

## <a name="configure-an-export"></a>Exportálás konfigurálása

[Exportálás](export-azure-blob-storage.md#configure-an-export) konfigurálása.

[!INCLUDE [footer-include](includes/footer-banner.md)]
