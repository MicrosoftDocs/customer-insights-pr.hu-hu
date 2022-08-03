---
title: Customer Insights-szegmensek exportálása a Campaign Standard szolgáltatásba Adobe (előzetes verzió)
description: További információ a Customer Insights-szegmensek használatáról a Campaign Standardban Adobe.
ms.date: 07/25/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: conceptual
author: stefanie-msft
ms.author: antando
manager: shellyha
ms.openlocfilehash: 834880cac9c5023157983081ff2513d9b051491f
ms.sourcegitcommit: 594081c82ca385f7143b3416378533aaf2d6d0d3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/27/2022
ms.locfileid: "9195523"
---
# <a name="export-customer-insights-segments-to-adobe-campaign-standard-preview"></a>Customer Insights-szegmensek exportálása a Campaign Standard szolgáltatásba Adobe (előzetes verzió)

Exportálja a releváns közönségeket megcélzó szegmenseket a Campaign Standardba Adobe.

:::image type="content" source="media/ACS-flow.png" alt-text="A jelen cikkben ismertetett lépések folyamatábrája.":::

## <a name="prerequisites"></a>Előfeltételek

- Kampány Adobe standard licenc.
- Egy [Azure Blob Storage-fiók](/azure/storage/blobs/create-data-lake-storage-account) neve és fiókkulcsa. A név és a kulcs megkereséséhez lásd: [Tárfiók-beállítások kezelése a Azure Portal](/azure/storage/common/storage-account-manage).
- Egy [Azure Blob Storage-tároló](/azure/storage/blobs/storage-quickstart-blobs-portal#create-a-container).

## <a name="campaign-overview"></a>Kampány áttekintése

Ha jobban meg szeretné érteni, hogyan használhatja a Adobe Experience Platform Customer Insights szegmenseit, nézzünk meg egy fiktív mintakampányt.

Tegyük fel, hogy a vállalata havi előfizetéses szolgáltatást kínál egyesült államokbeli ügyfeleinek. Meg szeretné határozni azokat az ügyfeleket, akiknek az előfizetései a következő nyolc napban megújításra esedékesek, de még nem újították meg előfizetésüket. Ezeknek az ügyfeleknek a megtartása érdekében e-mailben szeretne promóciós ajánlatot küldeni nekik az Adobe Campaign Standard segítségével.

Ebben a példában egy promóciós e-mail-kampányt egyszer szeretnénk futtatni. Ez a cikk nem terjed ki a kampány egynél több esetben való futtatásának esetére. A Customer Insights és Adobe a Campaign Standard azonban beállítható úgy, hogy ismétlődő kampányforgatókönyveknél is működjön.

## <a name="identify-your-target-audience"></a>Azonosítsa a célközönséget

Forgatókönyvünkben feltételezzük, hogy az ügyfelek e-mail-címei elérhetők a Customer Insights szolgáltatásban, és promóciós preferenciáikat elemeztük a szegmens tagjainak azonosítása érdekében.

A [Customer Insightsban](segments.md) meghatározott szegmens neve **ChurnProneCustomers**, és azt tervezi, hogy elküldi ezeknek az ügyfeleknek az e-mailes promóciót.

:::image type="content" source="media/churn-prone-customers-segment.png" alt-text="Képernyőfelvétel a Szegmensek oldalról, amelyen a létrehozott ChurnProneCustomers szegmens látható.":::

Az elküldeni kívánt ajánlati e-mail tartalmazza az ügyfél utónevét, vezetéknevét és az előfizetés záró dátumát. Tájékoztatja az ügyfeleket az arról az engedményről, amit akkor kapnak, ha a vége előtt megújítják az előfizetésüket.

## <a name="export-your-target-audience"></a>Exportálja a célközönséget

### <a name="set-up-connection-to-adobe-campaign"></a>Kapcsolat beállítása a kampánnyal Adobe

[!INCLUDE [export-connection-include](includes/export-connection-admn.md)]

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a Kapcsolat **hozzáadása,** majd a Kampány **Adobe lehetőséget**.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Alapértelmezés szerint csak a rendszergazdák. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Adja meg a **Blob Storage-fiók fióknevét**, **fiókkulcsát** és **tárolóját**.  

   :::image type="content" source="media/azure-blob-configuration.png" alt-text="Képernyőkép a tárfiók konfigurációjáról.":::

1. Tekintse át az adatvédelmet és a megfelelőséget, és válassza az [Elfogadom lehetőséget](connections.md#data-privacy-and-compliance)**.**

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

### <a name="configure-an-export"></a>Exportálás konfigurálása

[!INCLUDE [export-permission-include](includes/export-permission.md)]

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Válassza az Exportálás **hozzáadása lehetőséget**.

1. Az **Exportálási kapcsolat** mezőben válasszon kapcsolatot az Adobe Campaign szakaszból. Ha nem érhető el egy kapcsolat sem, akkor forduljon a rendszergazdához.

1. Adja meg az exportálás nevét.

1. Válassza ki az exportálni kívánt szegmenst. Ebben a példában ez a **ChurnProneCustomers**.

   :::image type="content" source="media/select-segment-churnpronecustomers.png" alt-text="Képernyőkép a szegmenskijelölési felhasználói felületről, ahol a ChurnProneCustomers szegmens ki van választva.":::

1. Válassza a **Következő** lehetőséget.

1. Képezze le a **Customer Insights szegmens Forrás** mezőit a **Kampány standard profilsémában szereplő** Célmezőkre Adobe.

   :::image type="content" source="media/ACS-field-mapping.png" alt-text="Az Adobe Campaign Standard összekötő mezőleképezése.":::

   Ha további attribútumokat szeretne hozzáadni, válassza az **Attribútum hozzáadása** lehetőséget. A célnév eltérhet a forrásmező nevétől, így továbbra is leképezheti a szegmenskimeneteket a Customer Insights szolgáltatásból a Campaign Standard szolgáltatásba, Adobe ha a mezőknek nincs ugyanaz a neve a két rendszerben.

   > [!NOTE]
   > Az e-mail-cím identitásmezőként használatos, de az ügyfélprofil bármely más azonosítóját használhatja az adatok kampányszintű hozzárendeléséhez Adobe.

1. Válassza a **Mentés** parancsot.

[!INCLUDE [export-saving-include](includes/export-saving.md)]

> [!NOTE]
> Győződjön meg róla, hogy az exportált szegmens rekordjainak száma az Adobe Campaign Standard licenc engedélyezett korlátján belül van.

Az exportált adatokat a rendszer a fent beállított Azure Blob Storage tárolóban tárolja. A rendszer automatikusan létrehozza a következő mappa elérési útját a tárolóban: *%ContainerName%/CustomerInsights_%instanceID%/% exportdestination-name%_%segmentname%_%timestamp%.csv*

Példa: Dynamics365CustomerInsights/CustomerInsights_abcd1234-4312-11f4-93dc-24f72f43e7d5/ChurnSegmentDemo_ChurnProneCustomers_1613059542.csv

## <a name="configure-adobe-campaign-standard"></a>Az Adobe Campaign Standard konfigurálása

Az exportált szegmensek az exportálás konfigurálása során kiválasztott oszlopokat tartalmazzák. Ezek az adatok használhatók [profilok létrehozásához az Adobe Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard/using/profiles-and-audiences/managing-profiles/about-profiles.html#managing-profiles) szolgáltatásban.

Ha a szegmenst a Campaign Standardban Adobe szeretné használni, [terjessze ki a Profilsémát](https://experienceleague.adobe.com/docs/campaign-standard/using/developing/use-cases--extending-resources/extending-the-profile-resource-with-a-new-field.html#developing) a Kampány standardban Adobe két további mezőre.

Példánkban ezek a mezők a Szegmens neve és a Szegmens dátuma. Ezeket a mezőket arra használjuk, hogy azonosítsuk az Adobe Campaign Standard azon profiljait, amelyeket meg szeretnénk célozni ebben a kampányban.

Ha a Campaign Standardban Adobe az importálni kívánt adatokon kívül nincs más rekord, akkor hagyja ki ezt a lépést.

## <a name="import-data-into-adobe-campaign-standard"></a>Adatok importálása az Adobe Campaign Standardbe

Importálja az előkészített célközönség adatokat a Customer Insights szolgáltatásból a Campaign Standard alkalmazásba Adobe, hogy [profilokat hozzon létre egy munkafolyamat](https://experienceleague.adobe.com/docs/campaign-standard/using/profiles-and-audiences/managing-profiles/creating-profiles.html#profiles-and-audiences) használatával.

Az alábbi képen látható importálási munkafolyamat úgy van konfigurálva, hogy nyolc óránként fusson, és exportált Customer Insights-szegmenseket keressen (.csv fájlt az Azure Blob Storage-ban). A munkafolyamat meghatározott oszloprendben bontja ki a .csv fájl tartalmát. Ez a munkafolyamat az alapvető hibakezelés végrehajtásához készült, és gondoskodik arról, hogy minden rekordnak legyen e-mail címe, mielőtt a az Adobe Campaign Standardben hidratálnák az adatokat. A munkafolyamat a szegmens nevét is kinyeri a fájlnévből, mielőtt az Adobe Campaign Standard profiladataiba lépne.

:::image type="content" source="media/ACS-import-workflow.png" alt-text="Képernyőkép az importálási munkafolyamatról a Adobe Campaign Standard felhasználói felületen.":::

## <a name="retrieve-the-audience-in-adobe-campaign-standard"></a>Az célközönség beolvasása az Adobe Campaign Standardbe

Miután importálta az adatokat a Campaign Standard szolgáltatásba Adobe, hozzon létre egy munkafolyamatot [,](https://experienceleague.adobe.com/docs/campaign-standard/using/managing-processes-and-data/workflow-general-operation/building-a-workflow.html#managing-processes-and-data) és [kérdezze le](https://experienceleague.adobe.com/docs/campaign-standard/using/managing-processes-and-data/targeting-activities/query.html#managing-processes-and-data) az ügyfeleket a Szegmens neve és a Szegmens dátuma alapján a mintakampányhoz azonosított profilok kiválasztásához.

## <a name="create-and-send-the-email-using-adobe-campaign-standard"></a>Az e-mail létrehozása és elküldése a Adobe Campaign Standard segítségével

Hozza létre az e-mail tartalmát, majd [tesztelje, és küldje el](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/get-started-sending-messages.html#preparing-and-testing-messages) az e-mailt.

:::image type="content" source="media/contoso-sample-email.jpg" alt-text="E-mail minta az Adobe Campaign Standardben megújítási ajánlattal.":::

[!INCLUDE [footer-include](includes/footer-banner.md)]
