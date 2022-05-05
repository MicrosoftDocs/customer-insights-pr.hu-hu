---
title: Customer Insights adatok exportálása Azure Data Lake Storage Gen 2 tárhelyre
description: Megismerheti, hogyan konfigurálható a kapcsolat az Azure Data Lake Storage Gen2 tárhellyel.
ms.date: 10/06/2021
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: stefanie-msft
ms.author: sthe
manager: shellyha
ms.openlocfilehash: 8b14992f8312d333d8a12501e8a28496c8434779
ms.sourcegitcommit: b7dbcd5627c2ebfbcfe65589991c159ba290d377
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/27/2022
ms.locfileid: "8642601"
---
# <a name="export-segment-list-and-other-data-to-azure-data-lake-storage-gen2-preview"></a>Szegmenslista és egyéb adatok exportálása az Azure Data Lake Storage Gen 2-es verzióba (előzetes verzió)

A Customer Insights adatokat a Data Lake Storage Gen2 fiókban tárolhatja, vagy segítségével adatait más alkalmazásokba továbbíthatja.

## <a name="known-limitations"></a>Ismert korlátozások

1. A Azure Data Lake Storage Gen2-es verzió esetében a [Normál teljesítmény és a Premium teljesítményszint](/azure/storage/blobs/create-data-lake-storage-account) közül választhat, amikor adattárolási fiókot hoz létre az adatokhoz. Ha a Felsőkategóriás teljesítményszintet választja, akkor válassza a megfelelő fióktípusként a premium blockblobok lehetőséget. 


## <a name="set-up-the-connection-to-azure-data-lake-storage-gen2"></a>Állítsa be az Azure Data Lake Storage Gen2 alkalmazásokkal való kapcsolatot 


1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza az **Azure Data Lake Gen 2** lehetőséget a kapcsolat konfigurálásához.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Adja meg a **Fiók neve**, a **Fiók kulcsa** és a **Tároló** adatait az Azure Data Lake Storage Gen2 tárolóhoz.
    - Ha meg szeretne ismerkedni vele, hogyan hozhat létre tárhelyfiókot az Azure Data Lake Storage Gen2 tárhellyel való használatra, olvassa el a [Tárhelyfiók létrehozása](/azure/storage/blobs/create-data-lake-storage-account) részt. 
    - Ha szeretne többet megtudni az Azure Data Lake Gen2 tárfiók nevét és fiókkulcsát, olvassa el a [Tárhelyfiók beállításainak kezelése az Azure-portálon](/azure/storage/common/storage-account-manage) részt.

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget. 

## <a name="configure-an-export"></a>Exportálás konfigurálása

Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz. További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Új exportálás létrehozásához válassza az **Exportálás hozzáadása** lehetőséget.

1. A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot az **Azure Data Lake** szakaszból. Ha nem látja ezt a szakasznevet, az Ön számára nincs ilyen típusú kapcsolat.

1. Jelölje be a jelölőnégyzetet azon entitások mellett, amelyeket exportálni szeretne erre a célhelyre.

1. Válassza a **Mentés** parancsot.

Az exportálás mentése nem futtatja azonnal az exportálást.

Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut. Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand). 

Az exportált adatok az Ön által konfigurált az Azure Data Lake Gen 2 tárolóban lesznek tárolva. 

[!INCLUDE [footer-include](includes/footer-banner.md)]
