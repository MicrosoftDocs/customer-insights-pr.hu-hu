---
title: Egységes profilok használata a Dynamics 365 Marketingben
description: Ismerje meg, hogyan integrálhatja az egységes profilokat és szegmenseket a Dynamics 365 Marketing szolgáltatással.
ms.date: 04/20/2022
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: 4cc3cbde97d0f9da198652e86c0843476393b646
ms.sourcegitcommit: f5af5613afd9c3f2f0695e2d62d225f0b504f033
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/01/2022
ms.locfileid: "8833311"
---
# <a name="work-with-unified-customer-profiles-in-dynamics-365-marketing"></a>Egységes ügyfélprofilok használata a Dynamics 365 Marketingben

[A Dynamics 365 Marketing](/dynamics365/marketing/overview) növeli az ügyfélélményt, lehetővé téve, hogy személyre szabott utazásokat szervezzen az összes érintési ponton, hogy megerősítse kapcsolatok és hűséget szerezzen. A Dynamics 365 Marketing alkalmazás zökkenőmentesen működik a Dynamics 365 Sales és más termékekkel, Dynamics 365 Customer Insights Microsoft Teams és lehetővé teszi, hogy gyorsabb és jobb döntéseket hozzon az adatok és az AI erejével.

A Customer Insights-adatok marketinggel való összekapcsolásával a következőket teheti:

- Egységes ügyfélprofilok és szegmensek megcélzása. Ez lehetővé teszi, hogy minden ügyfelet bevonjon, függetlenül az ügyfél adatainak helyétől.
- Dinamikus tartalom (például személyre szabott tokenek) e-mailekben, SMS-ben és leküldéses értesítésekben olyan intézkedésekről, mint a hűség állapota, az előfizetés megújításának dátuma, a fölérendelt partner vagy bármely más intézkedés, amelyet az egyesített Customer Insights-profilban rögzített.
- Töltse be az adatokat a Marketingből a Customer Insights-ba, és kombinálja azokat más forrásokból származó ügyféladatokkal.
- Alkalmazza a Customer Insights adattisztító, gazdagító és homályos egyező eszközeit.

## <a name="use-rich-customer-profiles-in-real-time-marketing"></a>Gazdag ügyfélprofilok használata a valós idejű marketingben

A valós idejű marketing lehetővé teszi egyéni eseményindítók [létrehozását](/dynamics365/marketing/real-time-marketing-custom-triggers), amelyek bármilyen ügyfélművelet alapján elindítják az ügyfélutakat. Minél személyre szabottabbak az adataid, annál relevánsabbak és személyre szabottabbak lesznek az utazásaid. Ez teszi a marketing és az ügyfélelemzések kombinálását olyan erőssé. Egyesítheti [az adatokat](data-unification.md) bármilyen forrásból, majd felhasználhatja a hiper-személyre szabott ügyfélutak ösztönzésére.

További információ: [Ügyfélelemzési profilok és szegmensek használata valós idejű marketingben](/dynamics365/marketing/real-time-marketing-ci-profile)

## <a name="use-unified-segments-with-outbound-customer-journeys"></a>Egységes szegmensek használata kimenő ügyfélutakkal

A Customer Insights lehetővé teszi, hogy számos forrásból származó adatokat finomítson, és összesített ügyfélszegmensekbe egyesítse azokat. A [Customer Insights és a kimenő marketing](export-dynamics365-marketing.md) összekapcsolásával ezek a szegmensek automatikusan megjelennek és *automatikusan frissülnek* a ügyfélút tervezőben.

További információ: [Szegmensek használata a Dynamics 365 Marketing szolgáltatásból Dynamics 365 Customer Insights](/dynamics365/marketing/customer-insights-segments)

## <a name="pull-data-from-your-own-azure-data-lake-storage"></a>Adatok lekérése a sajátodból Azure Data Lake Storage

Nem korlátozódik a felhőtárhelyre, ha a Customer Insights-adatokat a Marketinggel szeretné használni. Ha már rendelkezik saját Azure Data Lake Storage beállítással, csatlakozhat a Customer Insights szolgáltatáshoz, majd ugyanúgy megoszthatja az adatokat a Marketing alkalmazással, mint egy felhőalapú beállítással.

További információ: [Adatmegosztás engedélyezése saját maga által Dataverse Azure Data Lake Storage](customer-insights-dataverse.md#enable-data-sharing-with-dataverse-from-your-own-azure-data-lake-storage-preview)
