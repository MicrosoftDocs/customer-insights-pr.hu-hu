---
title: Szegmensek Adobe Experience Platform exportálása (előzetes verzió)
description: További információ a Customer Insights-szegmensek használatáról Adobe Experience Platform.
ms.date: 07/25/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: conceptual
author: stefanie-msft
ms.author: antando
manager: shellyha
ms.openlocfilehash: fcb43e0956c6d1f0ef36b222dd2b718906364244
ms.sourcegitcommit: 594081c82ca385f7143b3416378533aaf2d6d0d3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/27/2022
ms.locfileid: "9195293"
---
# <a name="export-segments-to-adobe-experience-platform-preview"></a>Szegmensek Adobe Experience Platform exportálása (előzetes verzió)

Exportálja a releváns közönségeket megcélzó szegmenseket a következőbe:Adobe Experience Platform.

:::image type="content" source="media/AEP-flow.png" alt-text="A jelen cikkben ismertetett lépések folyamatábrája.":::

## <a name="prerequisites"></a>Előfeltételek

- Egy Adobe Experience Platform licenc.
- Kampány Adobe standard licenc.
- Egy [Azure Blob Storage-fiók](/azure/storage/blobs/create-data-lake-storage-account) neve és fiókkulcsa. A név és a kulcs megkereséséhez lásd: [Tárfiók-beállítások kezelése a Azure Portal](/azure/storage/common/storage-account-manage).
- Egy [Azure Blob Storage-tároló](/azure/storage/blobs/storage-quickstart-blobs-portal#create-a-container).

## <a name="campaign-overview"></a>Kampány áttekintése

Ha jobban meg szeretné érteni, hogyan használhatja a Adobe Experience Platform Customer Insights szegmenseit, nézzünk meg egy fiktív mintakampányt.

Tegyük fel, hogy a vállalata havi előfizetéses szolgáltatást kínál egyesült államokbeli ügyfeleinek. Meg szeretné határozni azokat az ügyfeleket, akiknek az előfizetései a következő nyolc napban megújításra esedékesek, de még nem újították meg előfizetésüket. Ezeknek az ügyfeleknek a megtartása érdekében e-mailben szeretne promóciós ajánlatot küldeni nekik az Adobe Experience Platform segítségével.

Ebben a példában egy promóciós e-mail-kampányt egyszer szeretnénk futtatni. Ez a cikk nem terjed ki a kampány egynél több esetben való futtatásának esetére.

## <a name="identify-your-target-audience"></a>Azonosítsa a célközönséget

Forgatókönyvünkben feltételezzük, hogy az ügyfelek e-mail-címei elérhetők a Customer Insights szolgáltatásban, és promóciós preferenciáikat elemeztük a szegmens tagjainak azonosítása érdekében.

A [Customer Insightsban](segments.md) meghatározott szegmens neve **ChurnProneCustomers**, és azt tervezi, hogy elküldi ezeknek az ügyfeleknek az e-mailes promóciót.

:::image type="content" source="media/churn-prone-customers-segment.png" alt-text="Képernyőfelvétel a Szegmensek oldalról, amelyen a létrehozott ChurnProneCustomers szegmens látható.":::

Az elküldeni kívánt ajánlati e-mail tartalmazza az ügyfél utónevét, vezetéknevét és az előfizetés záró dátumát. Tájékoztatja az ügyfeleket az arról az engedményről, amit akkor kapnak, ha a vége előtt megújítják az előfizetésüket.

## <a name="export-your-target-audience"></a>Exportálja a célközönséget

Konfiguráljuk az exportálást a Customer Insightsból egy Azure Blob Storage-fiókba.

### <a name="set-up-connection-to-azure-blob-storage"></a>Kapcsolat beállítása az Azure Blob Storage-hoz

[!INCLUDE [export-connection-include](includes/export-connection-admn.md)]

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a Kapcsolat **hozzáadása lehetőséget**, majd válassza az **Azure Blob Storage lehetőséget**.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Alapértelmezés szerint csak a rendszergazdák. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Adja meg annak a Blob Storage fióknak a **Fiók nevét**, **Fiókkulcsát** és **Tárolóját**, ahová exportálni szeretné a szegmenst.  

   :::image type="content" source="media/azure-blob-configuration.png" alt-text="Képernyőkép a tárfiók konfigurációjáról.":::

1. Tekintse át az adatvédelmet és a megfelelőséget, és válassza az [Elfogadom lehetőséget](connections.md#data-privacy-and-compliance)**.**

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

### <a name="configure-an-export"></a>Exportálás konfigurálása

[!INCLUDE [export-permission-include](includes/export-permission.md)]

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Válassza az Exportálás **hozzáadása lehetőséget**.

1. A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot az Azure Blob Storage szakaszból. Ha nem érhető el egy kapcsolat sem, akkor forduljon a rendszergazdához.

1. Adja meg az exportálás nevét.

1. Válassza ki az exportálni kívánt szegmenst. Ebben a példában ez a **ChurnProneCustomers**.

   :::image type="content" source="media/select-segment-churnpronecustomers.png" alt-text="Képernyőkép a szegmenskijelölési felhasználói felületről, ahol a ChurnProneCustomers szegmens ki van választva.":::

1. Válassza a **Mentés** parancsot.

[!INCLUDE [export-saving-include](includes/export-saving.md)]

> [!NOTE]
> Győződjön meg róla, hogy az exportált szegmens rekordjainak száma az Adobe Campaign Standard licenc engedélyezett korlátján belül van.

Az exportált adatokat a rendszer a konfigurált Azure Blob Storage-tárolóban tárolja. A tárolóban a következő elérési utak jönnek létre automatikusan:

- A rendszer által létrehozott forrásoldali entitások és entitások esetén:  

  *%ContainerName%/CustomerInsights_%instanceID%/%ExportDestinationName%/%EntityName%/%Year%/%Month%/%Day%/%HHMM%/%EntityName%_%PartitionId%.csv*

  Példa: Dynamics365CustomerInsights/CustomerInsights_abcd1234-4312-11f4-93dc-24f72f43e7d5/BlobExport/ChurnSegmentDemo/2021/02/16/1433/ChurnProneCustomers_1.csv

- Az exportált entitások *model.json* fájlja az *%ExportDestinationName%* szintjén helyezkedik el

  Példa: Dynamics365CustomerInsights/CustomerInsights_abcd1234-4312-11f4-93dc-24f72f43e7d5/ChurnSegmentDemo/model.json

## <a name="define-experience-data-model-xdm-in-adobe-experience-platform"></a>Az élmény adatmodell (XDM) definiálás az Adobe Experience Platform szolgáltatásban

Mielőtt a Customer Insightsból exportált adatok felhasználhatók Adobe Experience Platform lennének, definiálja a Felhasználói élmény adatmodell sémáját, és [konfigurálja az adatokat a valós idejű ügyfélprofilhoz](https://experienceleague.adobe.com/docs/experience-platform/profile/tutorials/dataset-configuration.html#tutorials).

Ismerje meg, [mi az az XDM](https://experienceleague.adobe.com/docs/experience-platform/xdm/home.html), és ismerje meg a [sémaösszetétel alapjait](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html#schema).

## <a name="import-data-into-adobe-experience-platform"></a>Adatok importálása a Adobe Experience Platform rendszerbe

Importálja az előkészített célközönség adatokat a Customer Insights szolgáltatásból a következőbe:Adobe Experience Platform.

1. [Hozzon létre egy Azure Blob Storage-forráskapcsolatot](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/cloud-storage/blob.html#getting-started).

1. [Adatfolyam](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/dataflow/cloud-storage.html#ui-tutorials) konfigurálása felhőalapú tárolási kötegelt kapcsolathoz a szegmens kimenetének a Customer Insightsból a következőbe való importálásához Adobe Experience Platform: .

## <a name="create-an-audience-in-adobe-campaign-standard"></a>Az célközönség létrehozása az Adobe Campaign Standardben

A kampányhoz szükséges e-mail elküldéséhez az Adobe Campaign Standardot használjuk.

1. [Hozzon létre egy célközönség](https://experienceleague.adobe.com/docs/campaign-standard/using/profiles-and-audiences/get-started-profiles-and-audiences.html#permission) a Campaign Standard alkalmazásban Adobe a következő értékek Adobe Experience Platform felhasználásával: .

1. [A szegmenskészítő](https://experienceleague.adobe.com/docs/campaign-standard/using/integrating-with-adobe-cloud/adobe-experience-platform/audience-destinations/aep-using-segment-builder.html) használatával a Kampány standardban Adobe célközönség definiálhat a Adobe Experience Platform.

## <a name="create-and-send-the-email-using-adobe-campaign-standard"></a>Az e-mail létrehozása és elküldése a Adobe Campaign Standard segítségével

Hozza létre az e-mail tartalmát, majd [tesztelje, és küldje el](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/get-started-sending-messages.html#preparing-and-testing-messages) az e-mailt.

:::image type="content" source="media/contoso-sample-email.jpg" alt-text="E-mail minta az Adobe Campaign Standardben megújítási ajánlattal.":::

[!INCLUDE [footer-include](includes/footer-banner.md)]
