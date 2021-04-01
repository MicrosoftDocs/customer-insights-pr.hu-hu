---
title: A Customer Insights adatainak exportálása az Adobe Campaign Standardba
description: Ismerje meg, hogyan használhatja a célközönség-infomációs szegmenseket az Adobe Campaign Standardban.
ms.date: 02/26/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: stefanie-msft
ms.author: antando
manager: shellyha
ms.openlocfilehash: a5d0154c3d7c473dcba03fac0847bafcf97de2f2
ms.sourcegitcommit: bae40184312ab27b95c140a044875c2daea37951
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/15/2021
ms.locfileid: "5596318"
---
# <a name="use-customer-insights-segments-in-adobe-campaign-standard-preview"></a>A Customer Insights-szegmensek használata az Adobe Campaign Standardban (előzetes verzió)

A Dynamics 365 Customer Insights célközönség-információinak felhasználójaként létrehozott szegmenseket, hogy a marketingkampányok hatékonyságát növelje a releváns célközönségek megcélzásával. Az Adobe Experience Platformban és az Adobe Campaign Standardhoz hasonló alkalmazásokban található célközönség-információs szegmensek használatához a jelen cikkben ismertetett lépéseket kell követnie.

:::image type="content" source="media/ACS-flow.png" alt-text="A jelen cikkben ismertetett lépések folyamatábrája.":::

## <a name="prerequisites"></a>Előfeltételek

-   Dynamics 365 Customer Insights licenc
-   Adobe Campaign Standard-licenc
-   Azure Blob Storage-fiók

## <a name="campaign-overview"></a>Kampány áttekintése

Hogy jobban meg tudja érteni, hogyan használhatja a célközönség-információs szegmenseket az Adobe Experience Platformban, tekintsünk át egy kitalált mintakampányt.

Tegyük fel, hogy a vállalata havi előfizetéses szolgáltatást kínál egyesült államokbeli ügyfeleinek. Meg szeretné határozni azokat az ügyfeleket, akiknek az előfizetései a következő nyolc napban megújításra esedékesek, de még nem újították meg előfizetésüket. Ezeknek az ügyfeleknek a megtartása érdekében e-mailben szeretne promóciós ajánlatot küldeni nekik az Adobe Campaign Standard segítségével.

Ebben a példában egy promóciós e-mail-kampányt egyszer szeretnénk futtatni. Ez a cikk nem terjed ki a kampány egynél több esetben való futtatásának esetére. A célközönség-információk és az Adobe Campaign Standard azonban beállítható úgy is, hogy ismétlődő kampány esetén is működjön.

## <a name="identify-your-target-audience"></a>Azonosítsa a célközönséget

A mi esetünkben feltételezzük, hogy az ügyfelek e-mail-címei elérhetők a célközönség-információkban, és promóciós preferenciáik elemzésével azonosítottuk a szegmens tagjait.

A [célközönség-információkban meghatározott szegmens](segments.md) neve **ChurnProneCustomers**, és az e-mail-promóció elküldését tervezi ezeknek az ügyfeleknek.

:::image type="content" source="media/churn-prone-customers-segment.png" alt-text="Képernyőfelvétel a Szegmensek oldalról, amelyen a létrehozott ChurnProneCustomers szegmens látható.":::

Az elküldeni kívánt ajánlati e-mail tartalmazza az ügyfél utónevét, vezetéknevét és az előfizetés záró dátumát. Tájékoztatja az ügyfeleket az arról az engedményről, amit akkor kapnak, ha a vége előtt megújítják az előfizetésüket.

## <a name="export-your-target-audience"></a>Exportálja a célközönséget

Az azonosított célközönség segítségével konfigurálható az exportálás az célközönség-információkból egy Azure Blob Storage-fiókba.

1. A célközönség információin belül nyissa meg a következőt **Rendszergazda** > **Exportálási célhelyek**.

1. A **Adobe Campaign** csempében válassza a **Beállítás** lehetőséget.

   :::image type="content" source="media/adobe-campaign-standard-tile.png" alt-text="Az Adobe Campaign Standard konfigurációs csempéje.":::

1. Adja meg az új exportálási célhely **Megjelenítendő nevét**, és adja meg a **Fiók neve**, a **Fiókkulcs** és a **Tároló** értékét arra az Azure Blob Storage-fiókra vonatkozóan, ahova exportálni szeretné a szegmenst.  
      
   :::image type="content" source="media/azure-blob-configuration.png" alt-text="Képernyőkép a tárfiók konfigurációjáról."::: 

   - Az Azure Blob Storage fióknév és fiókkulcs megkeresésével kapcsolatos további tudnivalókat lásd: [A tárolófiók beállításainak kezelése az Azure Portal webhelyen](/azure/storage/common/storage-account-manage).

   - A tároló létrehozásával kapcsolatosan lásd: [Tároló létrehozása](/azure/storage/blobs/storage-quickstart-blobs-portal#create-a-container).

1. Válassza a **Következő** lehetőséget.

1. Válassza ki az exportálni kívánt szegmenst. Ebben a példában ez a **ChurnProneCustomers**.

   :::image type="content" source="media/select-segment-churnpronecustomers.png" alt-text="Képernyőkép a szegmenskijelölési felhasználói felületről, ahol a ChurnProneCustomers szegmens ki van választva.":::

1. Válassza a **Következő** lehetőséget.

1. Most leképezzük a célközönség-információk szegmens **Forrás** mezőit az Adobe Campaign Standard profilsémában szereplő **Cél** mezők neveire.

   :::image type="content" source="media/ACS-field-mapping.png" alt-text="Az Adobe Campaign Standard-összekötő mezőleképezése.":::

   Ha további attribútumokat szeretne hozzáadni, válassza az **Attribútum hozzáadása** lehetőséget. A cél neve nem lehet azonos a forrásmező nevével, így továbbra is leképezheti a célközönség-információkból származó szegmens kimenetét az Adobe Campaign Standard szolgáltatásba, ha mezőknek a két rendszerben nem ugyanaz a neve.

   > [!NOTE]
   > Az e-mail-címet identitásmezőként használja a rendszer, de a célközönség-információk ügyfélprofil egyéb azonosítói segítségével az adatokat leképezheti az Adobe Campaign Standardra.

1. Válassza a **Mentés** parancsot.

Az exportálási cél mentése után megtalálja a **Felügyelet** > **Exportálások** > **Saját exportálási célhelyek** helyen.

:::image type="content" source="media/export-destination-adobe-campaign-standard.png" alt-text="Képernyőkép az exportálások listájáról, amelyen a kiemelt mintaszegmens látható.":::

Mostantól [igény szerint exportálhatja a szegmenst](export-destinations.md#export-data-on-demand). Az exportálás minden [ütemezett frissítéssel](system.md) együtt is lefut.

> [!NOTE]
> Győződjön meg róla, hogy az exportált szegmens rekordjainak száma az Adobe Campaign Standard licencének megengedett korlátjan belül van.

Az exportált adatokat a rendszer a fent beállított Azure Blob Storage-tárolóban tárolja. A következő mappa elérési útja automatikusan létrejön a tárolóban:

*%ContainerName%/CustomerInsights_%instanceID%/% exportdestination-name%_%segmentname%_%timestamp%.csv*

Példa: Dynamics365CustomerInsights/CustomerInsights_abcd1234-4312-11f4-93dc-24f72f43e7d5/ChurnSegmentDemo_ChurnProneCustomers_1613059542.csv

## <a name="configure-adobe-campaign-standard"></a>Adobe Campaign Standard konfigurálása

Ha egy szegmenst exportál célközönség-információkból, akkor az előző lépésben az exportálási cél meghatározása során kiválasztott oszlopokat tartalmazza. Ezek az adatok használhatók [profilok létrehozásához az Adobe Campaign Standardban](https://experienceleague.adobe.com/docs/campaign-standard/using/profiles-and-audiences/managing-profiles/about-profiles.html#managing-profiles).

A szegmens az Adobe Campaign Standardban való használata esetén két további mezőre is ki kell bővítenünk a profilsémát az Adobe Campaign Standardban. Ismerje meg, hogyan [bővítheti a profilerőforrást](https://experienceleague.adobe.com/docs/campaign-standard/using/developing/use-cases--extending-resources/extending-the-profile-resource-with-a-new-field.html#developing) az Adobe Campaign Standard új mezőivel.

A példában ezek a mezők a *Szegmens neve és a Szegmens dátuma (nem kötelező).*

Ezeket a mezőket arra használjuk, hogy azonosítsuk a kampányhoz megcélozni kívánt Adobe Campaign Standard-profilokat.

Ha az Adobe Campaign Standardban nincs más rekord, mint amit importálni fog, ezt a lépést kihagyhatja.

## <a name="import-data-into-adobe-campaign-standard"></a>Adatok importálása az Adobe Campaign Standard programba

Most, hogy minden a helyén van, a profilok létrehozásához importálni kell az előkészített célközönségadatokat az célközönség-információkból az Adobe Campaign Standardba. Ismerje meg, [hogyan importálhat profilokat az Adobe Campaign Standardba](https://experienceleague.adobe.com/docs/campaign-standard/using/profiles-and-audiences/managing-profiles/creating-profiles.html#profiles-and-audiences) munkafolyamatok használatával.

Az alábbi képen az importálási munkafolyamat 8 óránként fut, és exportált célközönség-információs szegmensek (.csv fájl az Azure Blob Storage-ban) után kutat. A munkafolyamat meghatározott oszloprendben bontja ki a .csv fájl tartalmát. Ez a munkafolyamat az alapvető hibakezelés végrehajtásához készült, és biztosítja, hogy minden rekordhoz tartozzon e-mail-cím, mielőtt az adatokat átveszi az Adobe Campaign Standardban. A munkafolyamat ki is bontja a szegmens nevét a fájlnévből, mielőtt az ACS-profiladatokba upsertelné.

:::image type="content" source="media/ACS-import-workflow.png" alt-text="Képernyőkép az importálási munkafolyamatról az Adobe Campaign Standard felhasználói felületén.":::

## <a name="retrieve-the-audience-in-adobe-campaign-standard"></a>A célközönség lekérése az Adobe Campaign Standardban

Miután megtörtént az adatok importálása az Adobe Campaign Standardba, [létrehozhat egy munkafolyamatot](https://experienceleague.adobe.com/docs/campaign-standard/using/managing-processes-and-data/workflow-general-operation/building-a-workflow.html#managing-processes-and-data), és [lekérdezheti](https://experienceleague.adobe.com/docs/campaign-standard/using/managing-processes-and-data/targeting-activities/query.html#managing-processes-and-data) az ügyfeleket a *Szegmensnév* és *Szegmens dátuma* alapján, hogy kiválaszthassa a mintakampányhoz beazonosítótt profilokat.

## <a name="create-and-send-the-email-using-adobe-campaign-standard"></a>Az e-mail létrehozása és elküldése az Adobe Campaign Standard használatával

Hozza létre az e-mail tartalmát, majd [tesztelje, és küldje el](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/get-started-sending-messages.html#preparing-and-testing-messages) az e-mailt.

:::image type="content" source="media/contoso-sample-email.jpg" alt-text="E-mail minta az Adobe Campaign Standard megújítási ajánlatával.":::