---
title: Customer Insights-adatok exportálása az InMobi-ba
description: Ismerje meg, hogyan konfigurálhatja a kapcsolatot, és hogyan exportálhatja az InMobi szolgáltatásba.
ms.date: 06/27/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 8261c8adfe231792e70fc85432237cf73d5cd5a7
ms.sourcegitcommit: a97d31a647a5d259140a1baaeef8c6ea10b8cbde
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/29/2022
ms.locfileid: "9059610"
---
# <a name="export-segment-list-and-other-data-to-inmobi-preview"></a>Szegmenslista és egyéb adatok exportálása az InMobi szolgáltatásba (előzetes verzió)

Szegmenslistákat vagy egyéb adatokat exportálhat a Customer Insights-példányból az InMobi [szolgáltatásba](https://www.inmobi.com/).

## <a name="prerequisites"></a>Előfeltételek

1. InMobi-fiókkal [és rendszergazdai hitelesítő adatokkal rendelkezik](https://www.inmobi.com/).
1. Rendelkezik egy Azure Blob Storage-fióknévvel és a megfelelő fiókkulccsal. További információ: [Tárfiók-beállítások kezelése a Azure Portal](/azure/storage/common/storage-account-manage). A tárfiókban van egy tároló, amelybe exportálhatja az inMobi-adatokat. További információ: [Tároló létrehozása](/azure/storage/blobs/storage-quickstart-blobs-portal#create-a-container).
1. Az InMobi közvetlen kapcsolatot hoz létre a Blob Storage-ral, és konfigurálja az adatok automatikus importálását az InMobi szolgáltatásba. A folyamat kezdeményezéséhez lépjen kapcsolatba az InMobi képviselőjével.

## <a name="known-limitations"></a>Ismert korlátozások

1. Az Azure Blob Storage-ban választhat a Standard teljesítmény és a Prémium teljesítményszint [között](/azure/storage/blobs/storage-blob-performance-tiers). Ha a Felsőkategóriás teljesítményszintet választja, akkor válassza a megfelelő [fióktípusként a premium blockblobok](/azure/storage/common/storage-account-overview#types-of-storage-accounts) lehetőséget.

## <a name="set-up-the-connection-to-azure-blob-storage-and-configure-an-export"></a>Az Azure Blob Storage-hoz való kapcsolat beállítása és exportálás konfigurálása

1. Kövesse az utasításokat [az Azure Blob Storage-hoz](export-azure-blob-storage.md) való kapcsolat beállításához.
2. Az exportálás [konfigurálásához kövesse az](export-azure-blob-storage.md#configure-an-export) utasításokat.

[!INCLUDE [footer-include](includes/footer-banner.md)]
