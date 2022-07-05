---
title: Szegmensek Adobe Experience Platform exportálása (előzetes verzió)
description: További információ a Customer Insights-szegmensek használatáról Adobe Experience Platform.
ms.date: 03/29/2021
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: conceptual
author: stefanie-msft
ms.author: antando
manager: shellyha
ms.openlocfilehash: c29b8264019669ffd954a298ce3a633c852477fa
ms.sourcegitcommit: a97d31a647a5d259140a1baaeef8c6ea10b8cbde
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/29/2022
ms.locfileid: "9052514"
---
# <a name="export-segments-to-adobe-experience-platform-preview"></a>Szegmensek Adobe Experience Platform exportálása (előzetes verzió)

Dynamics 365 Customer Insights Lehet, hogy Ön szegmenseket hozott létre, hogy a releváns közönségek megcélzásával hatékonyabbá tegye marketingkampányait. Ha a Customer Insights Adobe Experience Platform egy szegmensét és olyan alkalmazásokat szeretne használni, mint a Adobe Campaign Standard, kövesse a cikkben ismertetett néhány lépést.

:::image type="content" source="media/AEP-flow.png" alt-text="A jelen cikkben ismertetett lépések folyamatábrája.":::

## <a name="prerequisites"></a>Előfeltételek

-   Dynamics 365 Customer Insights licenc
-   Adobe Experience Platform licenc
-   Adobe Campaign Standard licenc
-   Azure Blob Storage-fiók

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

Ha a cél célközönség azonosítjuk, konfigurálhatjuk az exportálást a Customer Insightsból egy Azure Blob Storage-fiókba.

### <a name="configure-a-connection"></a>Kapcsolat konfigurálása

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza az **Azure Blob Storage** vagy válassza a **Beállítás** lehetőséget az **Azure Blob Storage** csempében a kapcsolat konfigurálásához.

   :::image type="content" source="media/export-azure-blob-storage-tile.png" alt-text="Az Azure Blob Storage konfigurációs csempéje."::: 

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Adja meg annak a Blob Storage fióknak a **Fiók nevét**, **Fiókkulcsát** és **Tárolóját**, ahová exportálni szeretné a szegmenst.  
      
   :::image type="content" source="media/azure-blob-configuration.png" alt-text="Képernyőkép a tárfiók konfigurációjáról."::: 
   
    - Ha szeretne többet megtudni arról, hogyan találja meg a Blob Storage fiók nevét és fiókkulcsát, olvassa el a [Tárfiók beállításainak kezelése az Azure-portálon](/azure/storage/common/storage-account-manage) részt.
    - A tároló létrehozásával kapcsolatosan lásd: [Tároló létrehozása](/azure/storage/blobs/storage-quickstart-blobs-portal#create-a-container).

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget. 

### <a name="configure-an-export"></a>Exportálás konfigurálása

Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz. További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Új exportálás létrehozásához válassza az **Exportálás hozzáadása** lehetőséget.

1. A **Kapcsolat exportáláshoz** mezőben válasszon egy kapcsolatot az Azure Blob Storage szakaszból. Ha nem látja ezt a szakasznevet, akkor ilyen típusú kapcsolatok nem állnak az Ön rendelkezésére.

1. Válassza ki az exportálni kívánt szegmenst. Ebben a példában ez a **ChurnProneCustomers**.

   :::image type="content" source="media/select-segment-churnpronecustomers.png" alt-text="Képernyőkép a szegmenskijelölési felhasználói felületről, ahol a ChurnProneCustomers szegmens ki van választva.":::

1. Válassza a **Mentés** parancsot.

Az exportálási cél mentése után az **Adatok** > **Exportálások** lehetőségnél található.

Mostantól [igény szerint exportálhatja a szegmenst](export-destinations.md#run-exports-on-demand). Az exportálás minden [ütemezett frissítéssel](system.md) együtt is lefut.

> [!NOTE]
> Győződjön meg róla, hogy az exportált szegmens rekordjainak száma az Adobe Campaign Standard licenc engedélyezett korlátján belül van.

Az exportált adatokat a rendszer a fent beállított Azure Blob Storage tárolóban tárolja. A következő mappa elérési útja automatikusan létrejön a tárolóban:

*%ContainerName%/CustomerInsights_%instanceID%/%ExportDestinationName%/%EntityName%/%Year%/%Month%/%Day%/%HHMM%/%EntityName%_%PartitionId%.csv*

Példa: Dynamics365CustomerInsights/CustomerInsights_abcd1234-4312-11f4-93dc-24f72f43e7d5/BlobExport/ChurnSegmentDemo/2021/02/16/1433/ChurnProneCustomers_1.csv

Az exportált entitások *model.json* fájlja az *%ExportDestinationName%* szintjén helyezkedik el

Példa: Dynamics365CustomerInsights/CustomerInsights_abcd1234-4312-11f4-93dc-24f72f43e7d5/ChurnSegmentDemo/model.json

## <a name="define-experience-data-model-xdm-in-adobe-experience-platform"></a>Az élmény adatmodell (XDM) definiálás az Adobe Experience Platform szolgáltatásban

Mielőtt a Customer Insightsból exportált adatok felhasználhatók Adobe Experience Platform lennének, meg kell határoznunk az élményadatmodell sémáját, és [konfigurálnunk kell az adatokat a valós idejű ügyfélprofilhoz](https://experienceleague.adobe.com/docs/experience-platform/profile/tutorials/dataset-configuration.html#tutorials).

Ismerje meg, [mi az az XDM](https://experienceleague.adobe.com/docs/experience-platform/xdm/home.html), és ismerje meg a [sémaösszetétel alapjait](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html#schema).

## <a name="import-data-into-adobe-experience-platform"></a>Adatok importálása a Adobe Experience Platform rendszerbe

Most, hogy minden a helyén van, importálnunk kell az előkészített célközönség adatokat a Customer Insights-ból Adobe Experience Platform a.

Először [hozzon létre egy Azure Blob Storage-forráskapcsolatot](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/cloud-storage/blob.html#getting-started).    

A forráskapcsolat meghatározása után konfiguráljon egy adatfolyamot [egy felhőalapú tárolási kötegelt kapcsolathoz,](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/dataflow/cloud-storage.html#ui-tutorials) hogy importálja a szegmens kimenetét a Customer Insightsból a következőbe Adobe Experience Platform: .

## <a name="create-an-audience-in-adobe-campaign-standard"></a>Az célközönség létrehozása az Adobe Campaign Standardben

A kampányhoz szükséges e-mail elküldéséhez az Adobe Campaign Standardot használjuk. Az adatoknak az Adobe Experience Platform szolgáltatásba történő importálása után [létre kell hozni egy célközönséget](https://experienceleague.adobe.com/docs/campaign-standard/using/profiles-and-audiences/get-started-profiles-and-audiences.html#permission) az Adobe Campaign Standardbe az Adobe Experience Platform adataival.


A [szegmensszerkesztő használata](https://experienceleague.adobe.com/docs/campaign-standard/using/integrating-with-adobe-cloud/adobe-experience-platform/audience-destinations/aep-using-segment-builder.html) az Adobe Campaign Standardben a célközönség-adatokon alapuló új információk meghatározására az Adobe Experience Platform-szolgáltatásban.

## <a name="create-and-send-the-email-using-adobe-campaign-standard"></a>Az e-mail létrehozása és elküldése a Adobe Campaign Standard segítségével

Hozza létre az e-mail tartalmát, majd [tesztelje, és küldje el](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/get-started-sending-messages.html#preparing-and-testing-messages) az e-mailt.

:::image type="content" source="media/contoso-sample-email.jpg" alt-text="E-mail minta az Adobe Campaign Standardben megújítási ajánlattal.":::
