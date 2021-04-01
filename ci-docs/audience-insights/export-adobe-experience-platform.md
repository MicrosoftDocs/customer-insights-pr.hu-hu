---
title: A Customer Insights adatainak exportálása az Adobe Experience Platformba
description: Ismerje meg, hogyan használhatja a célközönség-infomációs szegmenseket az Adobe Experience Platformban.
ms.date: 02/26/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: stefanie-msft
ms.author: antando
manager: shellyha
ms.openlocfilehash: d1856861562be55c6d1d051050fe965560fa42f8
ms.sourcegitcommit: bae40184312ab27b95c140a044875c2daea37951
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/15/2021
ms.locfileid: "5596272"
---
# <a name="use-customer-insights-segments-in-adobe-experience-platform-preview"></a>A Customer Insights-szegmensek használata az Adobe Experience Platformban (előzetes verzió)

A Dynamics 365 Customer Insights célközönség-információinak felhasználójaként létrehozott szegmenseket, hogy a marketingkampányok hatékonyságát növelje a releváns célközönségek megcélzásával. Az Adobe Experience Platformban és az Adobe Campaign Standardhoz hasonló alkalmazásokban található célközönség-információs szegmensek használatához a jelen cikkben ismertetett lépéseket kell követnie.

:::image type="content" source="media/AEP-flow.png" alt-text="A jelen cikkben ismertetett lépések folyamatábrája.":::

## <a name="prerequisites"></a>Előfeltételek

-   Dynamics 365 Customer Insights licenc
-   Adobe Experience Platform-licenc
-   Adobe Campaign Standard-licenc
-   Azure Blob Storage-fiók

## <a name="campaign-overview"></a>Kampány áttekintése

Hogy jobban meg tudja érteni, hogyan használhatja a célközönség-információs szegmenseket az Adobe Experience Platformban, tekintsünk át egy kitalált mintakampányt.

Tegyük fel, hogy a vállalata havi előfizetéses szolgáltatást kínál egyesült államokbeli ügyfeleinek. Meg szeretné határozni azokat az ügyfeleket, akiknek az előfizetései a következő nyolc napban megújításra esedékesek, de még nem újították meg előfizetésüket. Ezeknek az ügyfeleknek a megtartása érdekében e-mailben szeretne promóciós ajánlatot küldeni nekik az Adobe Experience Platform segítségével.

Ebben a példában egy promóciós e-mail-kampányt egyszer szeretnénk futtatni. Ez a cikk nem terjed ki a kampány egynél több esetben való futtatásának esetére.

## <a name="identify-your-target-audience"></a>Azonosítsa a célközönséget

A mi esetünkben feltételezzük, hogy az ügyfelek e-mail-címei elérhetők a célközönség-információkban, és promóciós preferenciáik elemzésével azonosítottuk a szegmens tagjait.

A [célközönség-információkban meghatározott szegmens](segments.md) neve **ChurnProneCustomers**, és az e-mail-promóció elküldését tervezi ezeknek az ügyfeleknek.

:::image type="content" source="media/churn-prone-customers-segment.png" alt-text="Képernyőfelvétel a Szegmensek oldalról, amelyen a létrehozott ChurnProneCustomers szegmens látható.":::

Az elküldeni kívánt ajánlati e-mail tartalmazza az ügyfél utónevét, vezetéknevét és az előfizetés záró dátumát. Tájékoztatja az ügyfeleket az arról az engedményről, amit akkor kapnak, ha a vége előtt megújítják az előfizetésüket.

## <a name="export-your-target-audience"></a>Exportálja a célközönséget

Az azonosított célközönség segítségével konfigurálható az exportálás az célközönség-információkból egy Azure Blob Storage-fiókba.

1. A célközönség információin belül nyissa meg a következőt **Rendszergazda** > **Exportálási célhelyek**.

1. Az **Azure Blob Storage** csempén válassza a **Beállítás** lehetőséget.

   :::image type="content" source="media/export-azure-blob-storage-tile.png" alt-text="Az Azure Blob Storage konfigurációs csempéje.":::

1. Adja meg az új exportálási célhely **Megjelenítendő nevét**, és adja meg a **Fiók neve**, a **Fiókkulcs** és a **Tároló** értékét arra az Azure Blob Storage-fiókra vonatkozóan, ahova exportálni szeretné a szegmenst.  
      
   :::image type="content" source="media/azure-blob-configuration.png" alt-text="Képernyőkép a tárfiók konfigurációjáról."::: 

   - Az Azure Blob Storage fióknév és fiókkulcs megkeresésével kapcsolatos további tudnivalókat lásd: [A tárolófiók beállításainak kezelése az Azure Portal webhelyen](/azure/storage/common/storage-account-manage).

   - A tároló létrehozásával kapcsolatosan lásd: [Tároló létrehozása](/azure/storage/blobs/storage-quickstart-blobs-portal#create-a-container).

1. Válassza a **Következő** lehetőséget.

1. Válassza ki az exportálni kívánt szegmenst. Ebben a példában ez a **ChurnProneCustomers**.

   :::image type="content" source="media/select-segment-churnpronecustomers.png" alt-text="Képernyőkép a szegmenskijelölési felhasználói felületről, ahol a ChurnProneCustomers szegmens ki van választva.":::

1. Válassza a **Mentés** parancsot.

Az exportálási cél mentése után megtalálja a **Felügyelet** > **Exportálások** > **Saját exportálási célhelyek** helyen.

:::image type="content" source="media/export-destination-azure-blob-storage.png" alt-text="Képernyőkép az exportálások listájáról, amelyen a kiemelt mintaszegmens látható.":::

Mostantól [igény szerint exportálhatja a szegmenst](export-destinations.md#export-data-on-demand). Az exportálás minden [ütemezett frissítéssel](system.md) együtt is lefut.

> [!NOTE]
> Győződjön meg róla, hogy az exportált szegmens rekordjainak száma az Adobe Campaign Standard licencének megengedett korlátjan belül van.

Az exportált adatokat a rendszer a fent beállított Azure Blob Storage-tárolóban tárolja. A következő mappa elérési útja automatikusan létrejön a tárolóban:

*%ContainerName%/CustomerInsights_%instanceID%/%ExportDestinationName%/%EntityName%/%Year%/%Month%/%Day%/%HHMM%/%EntityName%_%PartitionId%.csv*

Példa: Dynamics365CustomerInsights/CustomerInsights_abcd1234-4312-11f4-93dc-24f72f43e7d5/BlobExport/ChurnSegmentDemo/2021/02/16/1433/ChurnProneCustomers_1.csv

Az exportált entitások *model.json* fájlja az *%ExportDestinationName%* szintjén helyezkedik el

Példa: Dynamics365CustomerInsights/CustomerInsights_abcd1234-4312-11f4-93dc-24f72f43e7d5/ChurnSegmentDemo/model.json

## <a name="define-experience-data-model-xdm-in-adobe-experience-platform"></a>A Tapasztalati adatmodell (XDM) definiálása az Adobe Experience Platformon

Mielőtt az célközönség-információkból exportált adatokat használhatjuk az Adobe Experience Platformon belül, meg kell határozni a Tapasztalat adatmodell sémáját, és [konfigurálni kell az adatokat a valós idejű ügyfélprofilhoz](https://experienceleague.adobe.com/docs/experience-platform/profile/tutorials/dataset-configuration.html#tutorials).

Ismerje meg, [mi az az XDM](https://experienceleague.adobe.com/docs/experience-platform/xdm/home.html), és ismerje meg a [sémaösszetétel alapjait](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html#schema).

## <a name="import-data-into-adobe-experience-platform"></a>Adatok importálása az Adobe Experience Platformba

Most, hogy minden a helyén van, a profilok létrehozásához importálni kell az előkészített célközönségadatokat az célközönség-információkból az Adobe Experience Platformba.

Először [hozzon létre egy Azure Blob Storage-forráskapcsolatot](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/cloud-storage/blob.html#getting-started).    

A forráskapcsolat definiálása után [konfigurálja egy felhőalapú tároló kötegfájl-kapcsolat adatfolyamát](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/dataflow/cloud-storage.html#ui-tutorials), hogy a szegmens kimenetét a célközönség-információkból az Adobe Experience Platformba importálja.

## <a name="create-an-audience-in-adobe-campaign-standard"></a>A célközönség létrehozása az Adobe Campaign Standardban

A kampányhoz tartozó e-mail elküldéséhez az Adobe Campaign Standardot fogjuk használni. Miután importálta az adatokat az Adobe Experience Platformba, [létre kell hozni egy célközönséget](https://experienceleague.adobe.com/docs/campaign-standard/using/profiles-and-audiences/get-started-profiles-and-audiences.html#permission) az Adobe Campaign Standardban, az Adobe Experience Platform adatai segítségével.

Ismerje meg, hogyan [használható a szegmensszerkesztő](https://experienceleague.adobe.com/docs/campaign-standard/using/profiles-and-audiences/working-with-adobe-experience-platform/aep-using-segment-builder.html#building-a-segment) az Adobe Campaign Standardban egy célközönség meghatározásához az Adobe Experience Platform adatai alapján.

## <a name="create-and-send-the-email-using-adobe-campaign-standard"></a>Az e-mail létrehozása és elküldése az Adobe Campaign Standard használatával

Hozza létre az e-mail tartalmát, majd [tesztelje, és küldje el](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/get-started-sending-messages.html#preparing-and-testing-messages) az e-mailt.

:::image type="content" source="media/contoso-sample-email.jpg" alt-text="E-mail minta az Adobe Campaign Standard megújítási ajánlatával.":::