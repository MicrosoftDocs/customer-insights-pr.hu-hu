---
title: Customer Insights-szegmensek exportálása a Campaign Standard szolgáltatásba Adobe (előzetes verzió)
description: További információ a Customer Insights-szegmensek használatáról a Campaign Standardban Adobe.
ms.date: 03/29/2021
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: conceptual
author: stefanie-msft
ms.author: antando
manager: shellyha
ms.openlocfilehash: 9915591cd969bf825f5d1669de43ed4f9953f898
ms.sourcegitcommit: dca46afb9e23ba87a0ff59a1776c1d139e209a32
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/29/2022
ms.locfileid: "9082344"
---
# <a name="export-customer-insights-segments-to-adobe-campaign-standard-preview"></a>Customer Insights-szegmensek exportálása a Campaign Standard szolgáltatásba Adobe (előzetes verzió)

Dynamics 365 Customer Insights Lehet, hogy Ön szegmenseket hozott létre, hogy a releváns közönségek megcélzásával hatékonyabbá tegye marketingkampányait. Ha a Customer Insights Adobe Experience Platform egy szegmensét és olyan alkalmazásokat szeretne használni, mint a Adobe Campaign Standard, kövesse a cikkben ismertetett néhány lépést.

:::image type="content" source="media/ACS-flow.png" alt-text="A jelen cikkben ismertetett lépések folyamatábrája.":::

## <a name="prerequisites"></a>Előfeltételek

- Dynamics 365 Customer Insights licenc
- Adobe Campaign Standard licenc
- Azure Blob Storage-fiók

## <a name="campaign-overview"></a>Kampány áttekintése

Ha jobban meg szeretné érteni, hogyan használhatja a Adobe Experience Platform Customer Insights szegmenseit, nézzünk meg egy fiktív mintakampányt.

Tegyük fel, hogy a vállalata havi előfizetéses szolgáltatást kínál egyesült államokbeli ügyfeleinek. Meg szeretné határozni azokat az ügyfeleket, akiknek az előfizetései a következő nyolc napban megújításra esedékesek, de még nem újították meg előfizetésüket. Ezeknek az ügyfeleknek a megtartása érdekében e-mailben szeretne promóciós ajánlatot küldeni nekik az Adobe Campaign Standard segítségével.

Ebben a példában egy promóciós e-mail-kampányt egyszer szeretnénk futtatni. Ez a cikk nem terjed ki a kampány egynél több esetben való futtatásának esetére. A Customer Insights és Adobe a Campaign Standard azonban beállítható úgy, hogy ismétlődő kampányforgatókönyveknél is működjön.

## <a name="identify-your-target-audience"></a>Azonosítsa a célközönséget

Forgatókönyvünkben feltételezzük, hogy az ügyfelek e-mail-címei elérhetők, és promóciós preferenciáikat elemeztük a szegmens tagjainak azonosítása érdekében.

A [Customer Insightsban](segments.md) meghatározott szegmens neve **ChurnProneCustomers**, és azt tervezi, hogy elküldi ezeknek az ügyfeleknek az e-mailes promóciót.

:::image type="content" source="media/churn-prone-customers-segment.png" alt-text="Képernyőfelvétel a Szegmensek oldalról, amelyen a létrehozott ChurnProneCustomers szegmens látható.":::

Az elküldeni kívánt ajánlati e-mail tartalmazza az ügyfél utónevét, vezetéknevét és az előfizetés záró dátumát. Tájékoztatja az ügyfeleket az arról az engedményről, amit akkor kapnak, ha a vége előtt megújítják az előfizetésüket.

## <a name="export-your-target-audience"></a>Exportálja a célközönséget

### <a name="configure-a-connection"></a>Kapcsolat konfigurálása

Ha a cél célközönség azonosítjuk, konfigurálhatjuk az exportálást egy Azure Blob Storage-fiókba.

1. A Customer Insightsban válassza a **Rendszergazdai** > **kapcsolatok lehetőséget**.

1. Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza az **Adobe Campaign** lehetőséget a kapcsolat konfigurálához, vagy válassza a **Beállítás** lehetőséget az **Adobe Campaign** csempén.

   :::image type="content" source="media/adobe-campaign-standard-tile.png" alt-text="Konfigurációs csempe az Adobe Campaign Standard számára.":::

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Ha nem teszi meg a szükséges lépéseket, az alapértelmezett beállítás a Rendszergazdák lesz. További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).

1. Adja meg annak az Azure Blob Storage fióknak a **Fiók nevét**, **Fiókkulcsát** és **Tárolóját**, ahová exportálni szeretné a szegmenst.  
      
   :::image type="content" source="media/azure-blob-configuration.png" alt-text="Képernyőkép a tárfiók konfigurációjáról."::: 

   - Az Azure Blob Storage fióknév és fiókkulcs megkeresésével kapcsolatos további tudnivalókat lásd: [A tárfiók beállításainak kezelése az Azure Portal webhelyen](/azure/storage/common/storage-account-manage).

   - A tároló létrehozásával kapcsolatosan lásd: [Tároló létrehozása](/azure/storage/blobs/storage-quickstart-blobs-portal#create-a-container).

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

### <a name="configure-an-export"></a>Exportálás konfigurálása

Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz. További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Új exportálás létrehozásához válassza az **Exportálás hozzáadása** lehetőséget.

1. Az **Exportálási kapcsolat** mezőben válasszon kapcsolatot az Adobe Campaign szakaszból. Ha nem látja ezt a szakasznevet, akkor ilyen típusú kapcsolatok nem állnak az Ön rendelkezésére.

1. Válassza ki az exportálni kívánt szegmenst. Ebben a példában ez a **ChurnProneCustomers**.

   :::image type="content" source="media/select-segment-churnpronecustomers.png" alt-text="Képernyőkép a szegmenskijelölési felhasználói felületről, ahol a ChurnProneCustomers szegmens ki van választva.":::

1. Válassza a **Következő** lehetőséget.

1. Most leképezzük a **Customer Insights szegmens Forrás** mezőit a **Kampány Standard profilsémában szereplő** Célmezőkre Adobe.

   :::image type="content" source="media/ACS-field-mapping.png" alt-text="Az Adobe Campaign Standard összekötő mezőleképezése.":::

   Ha további attribútumokat szeretne hozzáadni, válassza az **Attribútum hozzáadása** lehetőséget. A célnév eltérhet a forrásmező nevétől, így továbbra is leképezheti a szegmenskimeneteket a Customer Insights szolgáltatásból a Campaign Standard szolgáltatásba, Adobe ha a mezőknek nincs ugyanaz a neve a két rendszerben.

   > [!NOTE]
   > Az e-mail-cím identitásmezőként használatos, de az ügyfélprofil bármely más azonosítóját használhatja az adatok kampányszintű hozzárendeléséhez Adobe.

1. Válassza a **Mentés** parancsot.

Az exportálási cél mentése után az **Adatok** > **Exportálások** lehetőségnél található.

Mostantól [igény szerint exportálhatja a szegmenst](export-destinations.md#run-exports-on-demand). Az exportálás minden [ütemezett frissítéssel](system.md) együtt is lefut.

> [!NOTE]
> Győződjön meg róla, hogy az exportált szegmens rekordjainak száma az Adobe Campaign Standard licenc engedélyezett korlátján belül van.

Az exportált adatokat a rendszer a fent beállított Azure Blob Storage tárolóban tárolja. A következő mappa elérési útja automatikusan létrejön a tárolóban:

*%ContainerName%/CustomerInsights_%instanceID%/% exportdestination-name%_%segmentname%_%timestamp%.csv*

Példa: Dynamics365CustomerInsights/CustomerInsights_abcd1234-4312-11f4-93dc-24f72f43e7d5/ChurnSegmentDemo_ChurnProneCustomers_1613059542.csv

## <a name="configure-adobe-campaign-standard"></a>Az Adobe Campaign Standard konfigurálása

Az exportált szegmensek tartalmazzák azokat az oszlopokat, amelyeket az exportálási célnak az előző lépésben történő meghatározásakor választott ki. Ezek az adatok használhatók [profilok létrehozásához az Adobe Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard/using/profiles-and-audiences/managing-profiles/about-profiles.html#managing-profiles) szolgáltatásban.

Egy szegmens használatához az Adobe Campaign Standard szolgáltatásban ki kell bővítenünk a profilsémát az Adobe Campaign Standardben, hogy két további mezőt is tartalmazzon. Megismerheti, hogyan [bővítheti a profilerőforrást](https://experienceleague.adobe.com/docs/campaign-standard/using/developing/use-cases--extending-resources/extending-the-profile-resource-with-a-new-field.html#developing) az Adobe Campaign Standard új mezőivel.

A példában ezek a mezők a *Szegmens neve és a Szegmens dátuma (nem kötelező)*.

Ezeket a mezőket arra használjuk, hogy azonosítsuk az Adobe Campaign Standard azon profiljait, amelyeket meg szeretnénk célozni ebben a kampányban.

Ha az Adobe Campaign Standardban nincs más rekord, mint amit importálni fog, ezt a lépést kihagyhatja.

## <a name="import-data-into-adobe-campaign-standard"></a>Adatok importálása az Adobe Campaign Standardbe

Most, hogy minden a helyén van, importálnunk kell az előkészített célközönség adatokat a Customer Insights szolgáltatásból a Campaign Standard alkalmazásba Adobe profilok létrehozásához. Ismerje meg, [hogyan importálhat profilokat az Adobe Campaign Standardbe](https://experienceleague.adobe.com/docs/campaign-standard/using/profiles-and-audiences/managing-profiles/creating-profiles.html#profiles-and-audiences) munkafolyamattal.

Az alábbi képen látható importálási munkafolyamat úgy van konfigurálva, hogy nyolc óránként fusson, és exportált Customer Insights-szegmenseket keressen (.csv fájlt az Azure Blob Storage-ban). A munkafolyamat meghatározott oszloprendben bontja ki a .csv fájl tartalmát. Ez a munkafolyamat az alapvető hibakezelés végrehajtásához készült, és gondoskodik arról, hogy minden rekordnak legyen e-mail címe, mielőtt a az Adobe Campaign Standardben hidratálnák az adatokat. A munkafolyamat a szegmens nevét is kinyeri a fájlnévből, mielőtt az Adobe Campaign Standard profiladataiba lépne.

:::image type="content" source="media/ACS-import-workflow.png" alt-text="Képernyőkép az importálási munkafolyamatról a Adobe Campaign Standard felhasználói felületen.":::

## <a name="retrieve-the-audience-in-adobe-campaign-standard"></a>Az célközönség beolvasása az Adobe Campaign Standardbe

Miután megtörtént az adatok importálása az Adobe Campaign Standard szolgáltatásba, [létrehozhat egy munkafolyamatot](https://experienceleague.adobe.com/docs/campaign-standard/using/managing-processes-and-data/workflow-general-operation/building-a-workflow.html#managing-processes-and-data), és a *Szegmensnév* és a *Szegmensdátum* alapján [lekérdezheti](https://experienceleague.adobe.com/docs/campaign-standard/using/managing-processes-and-data/targeting-activities/query.html#managing-processes-and-data) az ügyfeleket a mintakampányhoz azonosított profilok kiválasztásához.

## <a name="create-and-send-the-email-using-adobe-campaign-standard"></a>Az e-mail létrehozása és elküldése a Adobe Campaign Standard segítségével

Hozza létre az e-mail tartalmát, majd [tesztelje, és küldje el](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/get-started-sending-messages.html#preparing-and-testing-messages) az e-mailt.

:::image type="content" source="media/contoso-sample-email.jpg" alt-text="E-mail minta az Adobe Campaign Standardben megújítási ajánlattal.":::
