---
title: Customer Insights adatok exportálása ActiveCampaign-be
description: További információ a kapcsolat konfigurálásához és az ActiveCampaign-hez való exportáláshoz.
ms.date: 06/29/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 14d420205a5c60d471ef21a04ab6d02295a65ca8fd5205ba782a300703b06102
ms.sourcegitcommit: aa0cfbf6240a9f560e3131bdec63e051a8786dd4
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/10/2021
ms.locfileid: "7032212"
---
# <a name="export-segments-to-activecampaign-preview"></a>Szegmensek exportálása ActiveCampaign-be (előzetes verzió)

Exportálja az egyesített ügyfélprofilok szegmenseit az ActiveCampaign-be, és használja őket marketingtevékenységekhez.

## <a name="prerequisites"></a>Előfeltételek

-   [ActiveCampaign fiókkal](https://www.activecampaign.com/) és a megfelelő rendszergazdai hitelesítő adatokkal rendelkezik.
-   [Konfigurált szegmensekkel](segments.md) rendelkezik a célközönségi-információkban.
-   Az exportált szegmensek egységes ügyfélprofiljai egy e-mail-címmel rendelkező mezőt tartalmaznak.

## <a name="known-limitations"></a>Ismert korlátozások

- Az ActiveCampaign-be exportálhat exportonként akár 1 millió profilt, és akár 90 percet is igénybe vehet.
- Az ActiveCampaign-be történő exportálás szegmensekre korlátozódik.
- Az ActiveCampaign-be exportálható profilok száma az ActiveCampaign-nel kötött szerződésétől függ.

## <a name="set-up-connection-to-activecampaign"></a>Állítsa be az ActiveCampaign-nel való kapcsolatot

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a **Kapcsolat hozzáadása** lehetőséget, és válassza az **ActiveCampaign** lehetőséget a kapcsolat konfigurálásához.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. A kapcsolat használóinak kiválasztása. Alapértelmezés szerint csak a rendszergazdák. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](connections.md#allow-contributors-to-use-a-connection-for-exports).

1. Adja meg [ActiveCampaign API-kulcsát és REST-végpont eszköznevet](https://help.activecampaign.com/hc/articles/207317590-Getting-started-with-the-API#how-to-obtain-your-activecampaign-api-url-and-key). A REST-végpont eszköznév csak eszköznév, a https:// tag nélkül. 

1. Válassza az **Elfogadom** lehetőséget az **Adatvédelem és a megfelelőség** megerősítéséhez.

1. Válassza a **Csatlakozás** lehetőséget, az ActiveCampaign inicializáláshoz.

1. Válassza a **Saját maga hozzáadása exportálási felhasználóként** lehetőséget, és adja meg Customer Insights-hitelesítő adatait.

1. A kapcsolat befejezéséhez válassza a **Mentés** lehetőséget.

## <a name="configure-an-export"></a>Exportálás konfigurálása

Az exportálás konfigurálható, ha hozzáfér az ilyen típusú kapcsolathoz. További tudnivalók: [Exportálás konfigurálásához szükséges engedélyek](export-destinations.md#set-up-a-new-export).

1. Menjen az **Adatok** > **Exportálások** lehetőségre.

1. Új exportálás létrehozásához válassza a **Célhely hozzáadása** lehetőséget.

1. Az **Exportálási kapcsolat** mezőben válasszon kapcsolatot az ActiveCampaign szakaszból. Ha nem látja ezt a szakasznevet, az Ön számára nincs ilyen típusú kapcsolat.

1. Adja meg [**ActiveCampaign listaazonosítóját**](https://help.activecampaign.com/hc/articles/360000030559-How-to-create-a-list-in-ActiveCampaign).    

3. Az **Adategyeztetés** szakaszban az **E-mail** mezőben jelölje ki az egyesített ügyfélprofil ügyfél e-mail-címét jelképező mezőjét. Kötelező a szegmensek ActiveCampaign-be történő exportálása. Opcionálisan exportálhat utónév, vezetéknév és telefonon, hogy személyre szabottabb e-maileket hozzon létre. Válassza az Attribútum hozzáadása lehetőséget a mezők leképezéséhez.

1. Válassza a **Mentés** parancsot.

Az exportálás mentése nem futtatja azonnal az exportálást.

Az exportálás minden [ütemezett frissítéssel](system.md#schedule-tab) fut. Az adatok [igény szerint exportálhatók is](export-destinations.md#run-exports-on-demand). 


## <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség

Amikor engedélyezed a Dynamics 365 Customer Insights -nak, hogy továbbítsa az adatokat ActiveCampaign-be, engedélyezed az adatátvitelt a megfelelőséghatáron kívülre a Dynamics 365 Customer Insights -nak, beleértve az esetlegesen bizalmas adatokat, például személyes adatokat. A Microsoft az Ön utasítására továbbítja az ilyen adatokat, de Ön felelős annak biztosításáért, hogy az ActiveCampaign megfeleljen az esetleges adatvédelmi és biztonsági kötelezettségeknek. További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).

A funkció használatának leállítása érdekében a Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja ezt az exportálási célhelyet.
