---
title: Customer Insights adatok exportálása az Adobe Campaign Standardbe
description: Ismerje meg, hogyan lehet célközönséggel kapcsolatos információk szegmenseit használni az Adobe Campaign Standard szolgáltatásban.
ms.date: 03/29/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: stefanie-msft
ms.author: antando
manager: shellyha
ms.openlocfilehash: d301b4f0cb875303fb3d373b77177acd1c1f5219cd6f23c2a1d29ce67a222eab
ms.sourcegitcommit: aa0cfbf6240a9f560e3131bdec63e051a8786dd4
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/10/2021
ms.locfileid: "7032166"
---
# <a name="use-customer-insights-segments-in-adobe-campaign-standard-preview"></a>Customer Insights-szegmensek használata az Adobe Campaign Standard szolgáltatásban(előzetes verzió)

A célközönségi elemzések felhasználójaként Dynamics 365 Customer Insights -ban előfordulhat, hogy szegmenseket hozott létre, hogy hatékonyabbá tegye marketingkampányait a releváns célközönségek megcélzásával. Ha használni szeretné a célközönséggel kapcsolatosa információkat az Adobe Experience Platform felületen és olyan alkalmazásokban, mint az Adobe Campaign Standard néhány, a cikkben felvázolt lépést el kell végeznie.

:::image type="content" source="media/ACS-flow.png" alt-text="A jelen cikkben ismertetett lépések folyamatábrája.":::

## <a name="prerequisites"></a>Előfeltételek

-   Dynamics 365 Customer Insights licenc
-   Adobe Campaign Standard licenc
-   Azure Blob Storage-fiók

## <a name="campaign-overview"></a>Kampány áttekintése

Hogy jobban megérthesse, hogyan használhatók fel a célközönséggel kapcsolatos információk szegmensei az Adobe Experience Platform szolgáltatásban, nézzünk meg egy kitalált mintakampányt.

Tegyük fel, hogy a vállalata havi előfizetéses szolgáltatást kínál egyesült államokbeli ügyfeleinek. Meg szeretné határozni azokat az ügyfeleket, akiknek az előfizetései a következő nyolc napban megújításra esedékesek, de még nem újították meg előfizetésüket. Ezeknek az ügyfeleknek a megtartása érdekében e-mailben szeretne promóciós ajánlatot küldeni nekik az Adobe Campaign Standard segítségével.

Ebben a példában egy promóciós e-mail-kampányt egyszer szeretnénk futtatni. Ez a cikk nem terjed ki a kampány egynél több esetben való futtatásának esetére. A célközönséggel kapcsolatos információk és az Adobe Campaign Standard beállítható úgy, hogy ismétlődő kampány esetén is működjenek.

## <a name="identify-your-target-audience"></a>Azonosítsa a célközönséget

A mi esetünkben feltételezzük, hogy az ügyfelek e-mail-címei elérhetők a célközönség-információkban, és promóciós preferenciáik elemzésével azonosítottuk a szegmens tagjait.

A [célközönség-információkban meghatározott szegmens](segments.md) neve **ChurnProneCustomers**, és az e-mail-promóció elküldését tervezi ezeknek az ügyfeleknek.

:::image type="content" source="media/churn-prone-customers-segment.png" alt-text="Képernyőfelvétel a Szegmensek oldalról, amelyen a létrehozott ChurnProneCustomers szegmens látható.":::

Az elküldeni kívánt ajánlati e-mail tartalmazza az ügyfél utónevét, vezetéknevét és az előfizetés záró dátumát. Tájékoztatja az ügyfeleket az arról az engedményről, amit akkor kapnak, ha a vége előtt megújítják az előfizetésüket.

## <a name="export-your-target-audience"></a>Exportálja a célközönséget

### <a name="configure-a-connection"></a>Kapcsolat konfigurálása

Az azonosított célközönség segítségével konfigurálható az exportálás az célközönség-információkból egy Azure Blob Storage-fiókba.

1. A célközönség információkban menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

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

1. Most leképezzük a Célközönséggel kapcsolatos információk szegmens **Forrás** mezőit az Adobe Campaign Standard profilsémában szereplő **Cél** mezőnevekre.

   :::image type="content" source="media/ACS-field-mapping.png" alt-text="Az Adobe Campaign Standard összekötő mezőleképezése.":::

   Ha további attribútumokat szeretne hozzáadni, válassza az **Attribútum hozzáadása** lehetőséget. A célnév eltérhet a forrásmező nevétől, így továbbra is leképezheti célközönség szegmens kimenetét célközönséggrl kapcsolatos információkból az Adobe Campaign Standardbe ha a mezőknek nem ugyanaz a neve a két rendszerben.

   > [!NOTE]
   > Az e-mail címet identitásmezőként használja a rendszer, de a célközönséggel kapcsolatos információk ügyfélprofilból bármely más azonosítót használhat az adatok leképezéséhez az Adobe Campaign Standard irányába.

1. Válassza a **Mentés** parancsot.

Az exportálási cél mentése után az **Adatok** > **Exportálások** lehetőségnél található.

Mostantól [igény szerint exportálhatja a szegmenst](export-destinations.md#run-exports-on-demand). Az exportálás minden [ütemezett frissítéssel](system.md) együtt is lefut.

> [!NOTE]
> Győződjön meg róla, hogy az exportált szegmens rekordjainak száma az Adobe Campaign Standard licenc engedélyezett korlátján belül van.

Az exportált adatokat a rendszer a fent beállított Azure Blob Storage tárolóban tárolja. A következő mappa elérési útja automatikusan létrejön a tárolóban:

*%ContainerName%/CustomerInsights_%instanceID%/% exportdestination-name%_%segmentname%_%timestamp%.csv*

Példa: Dynamics365CustomerInsights/CustomerInsights_abcd1234-4312-11f4-93dc-24f72f43e7d5/ChurnSegmentDemo_ChurnProneCustomers_1613059542.csv

## <a name="configure-adobe-campaign-standard"></a>Az Adobe Campaign Standard konfigurálása

Ha egy szegmenst exportál célközönség-információkból, akkor az előző lépésben az exportálási cél meghatározása során kiválasztott oszlopokat tartalmazza. Ezek az adatok használhatók [profilok létrehozásához az Adobe Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard/using/profiles-and-audiences/managing-profiles/about-profiles.html#managing-profiles) szolgáltatásban.

Egy szegmens használatához az Adobe Campaign Standard szolgáltatásban ki kell bővítenünk a profilsémát az Adobe Campaign Standardben, hogy két további mezőt is tartalmazzon. Megismerheti, hogyan [bővítheti a profilerőforrást](https://experienceleague.adobe.com/docs/campaign-standard/using/developing/use-cases--extending-resources/extending-the-profile-resource-with-a-new-field.html#developing) az Adobe Campaign Standard új mezőivel.

A példában ezek a mezők a *Szegmens neve és a Szegmens dátuma (nem kötelező)*.

Ezeket a mezőket arra használjuk, hogy azonosítsuk az Adobe Campaign Standard azon profiljait, amelyeket meg szeretnénk célozni ebben a kampányban.

Ha az Adobe Campaign Standardban nincs más rekord, mint amit importálni fog, ezt a lépést kihagyhatja.

## <a name="import-data-into-adobe-campaign-standard"></a>Adatok importálása az Adobe Campaign Standardbe

Most, hogy minden a helyén van, a profilok létrehozásához importálni kell az előkészített célközönség adatokat a célközönéggel kapcsolatos információkból az Adobe Campaign Standardbe a profilok létrehozásához. Ismerje meg, [hogyan importálhat profilokat az Adobe Campaign Standardbe](https://experienceleague.adobe.com/docs/campaign-standard/using/profiles-and-audiences/managing-profiles/creating-profiles.html#profiles-and-audiences) munkafolyamattal.

Az alábbi képen látható importálási munkafolyamat úgy van konfigurálva, hogy nyolc óránként fusson, és keresse meg az exportált célközönségi elemzések szegmenseket (.csv fájl az Azure Blob Storage-ban). A munkafolyamat meghatározott oszloprendben bontja ki a .csv fájl tartalmát. Ez a munkafolyamat az alapvető hibakezelés végrehajtásához készült, és gondoskodik arról, hogy minden rekordnak legyen e-mail címe, mielőtt a az Adobe Campaign Standardben hidratálnák az adatokat. A munkafolyamat a szegmens nevét is kinyeri a fájlnévből, mielőtt az Adobe Campaign Standard profiladataiba lépne.

:::image type="content" source="media/ACS-import-workflow.png" alt-text="Képernyőkép az importálási munkafolyamatról a Adobe Campaign Standard felhasználói felületen.":::

## <a name="retrieve-the-audience-in-adobe-campaign-standard"></a>Az célközönség beolvasása az Adobe Campaign Standardbe

Miután megtörtént az adatok importálása az Adobe Campaign Standard szolgáltatásba, [létrehozhat egy munkafolyamatot](https://experienceleague.adobe.com/docs/campaign-standard/using/managing-processes-and-data/workflow-general-operation/building-a-workflow.html#managing-processes-and-data), és a *Szegmensnév* és a *Szegmensdátum* alapján [lekérdezheti](https://experienceleague.adobe.com/docs/campaign-standard/using/managing-processes-and-data/targeting-activities/query.html#managing-processes-and-data) az ügyfeleket a mintakampányhoz azonosított profilok kiválasztásához.

## <a name="create-and-send-the-email-using-adobe-campaign-standard"></a>Az e-mail létrehozása és elküldése a Adobe Campaign Standard segítségével

Hozza létre az e-mail tartalmát, majd [tesztelje, és küldje el](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/get-started-sending-messages.html#preparing-and-testing-messages) az e-mailt.

:::image type="content" source="media/contoso-sample-email.jpg" alt-text="E-mail minta az Adobe Campaign Standardben megújítási ajánlattal.":::
