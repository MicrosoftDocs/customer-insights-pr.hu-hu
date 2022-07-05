---
title: Egyesített profilok használata a Dynamics 365 Marketing rendszerben
description: Ismerje meg, hogyan integrálhatja az egyesített profilokat és szegmenseket a Dynamics 365 Marketing alkalmazással.
ms.date: 04/20/2022
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: 99ec463299a24ea81cfe26bb785e36bdefdcd080
ms.sourcegitcommit: a97d31a647a5d259140a1baaeef8c6ea10b8cbde
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/29/2022
ms.locfileid: "9054435"
---
# <a name="use-unified-customer-profiles-in-dynamics-365-marketing"></a>Egyesített ügyfélprofilok használata a Dynamics 365 Marketing rendszerben

[A Dynamics 365 Marketing](/dynamics365/marketing/overview) magasabb szintre emeli az ügyfélélményt, lehetővé téve, hogy személyre szabott utazásokat szervezzen az összes érintkezési ponton, hogy megerősítse kapcsolatok és hűséget szerezzen. A Dynamics 365 Marketing alkalmazás zökkenőmentesen együttműködik a Dynamics 365 Sales rendszerrel, Dynamics 365 Customer Insights Microsoft Teams, és más termékekkel, és lehetővé teszi, hogy gyorsabb és jobb döntéseket hozzon az adatok és a mesterséges intelligencia erejével.

A Customer Insights-adatok és a Marketing összekapcsolásával a következőket teheti:

- Egységes ügyfélprofilok és szegmensek megcélzása. Ez lehetővé teszi, hogy minden ügyfelet bevonjon, függetlenül az ügyfél adatainak helyétől.
- A dinamikus tartalmakat (például személyre szabott tokeneket) e-mailekben, SMS-ekben és leküldéses értesítésekben olyan mértékekre alapozhatja, mint a hűség állapota, az előfizetés megújításának dátuma, a fölérendelt partner vagy bármely más, az egyesített Customer Insights-profilban rögzített mérték.
- Töltsön be adatokat a Marketingből a Customer Insights szolgáltatásba, és kombinálja azokat más forrásokból származó ügyféladatokkal.
- Alkalmazza a Customer Insights adattisztító, gazdagító és fuzzy egyező eszközöket.

## <a name="use-rich-customer-profiles-in-real-time-marketing"></a>Gazdag ügyfélprofilok használata a valós idejű marketingben

A valós idejű marketing lehetővé teszi egyéni eseményindítók [létrehozását](/dynamics365/marketing/real-time-marketing-custom-triggers), amelyek bármilyen ügyfélművelet alapján elindítják az ügyfélutakat. Minél személyre szabottabbak az adataid, annál relevánsabbak és személyre szabottabbak lesznek az utazásaid. Ez teszi olyan erőssé a Marketing és a Customer Insights kombinálását. Bármely forrásból származó adatokat [egyesíthet](data-unification.md), majd felhasználhatja őket a hiper-személyre szabott ügyfélutak táplálására.

További információ: [Customer Insights profilok és szegmensek használata valós idejű marketingben](/dynamics365/marketing/real-time-marketing-ci-profile)

## <a name="use-unified-segments-with-outbound-customer-journeys"></a>Egységes szegmensek használata kimenő ügyfélutakkal

A Customer Insights lehetővé teszi, hogy számos forrásból származó adatokat finomítson, és összesített ügyfélszegmensekbe egyesítse őket. A [Customer Insights kimenő marketinggel](export-dynamics365-marketing.md) való összekapcsolásával ezek a szegmensek automatikusan megjelennek *és* automatikusan frissülnek a ügyfélút tervezőben.

További információ: [Szegmensek használata a Dynamics 365 Customer Insights Dynamics 365 Marketing alkalmazással](/dynamics365/marketing/customer-insights-segments)

## <a name="pull-data-from-your-own-azure-data-lake-storage"></a>Adatok lekérése a sajátodból Azure Data Lake Storage

Nem korlátozódik a felhőalapú tárolásra, ha a Customer Insights-adatokat a Marketing szolgáltatással szeretné használni. Ha már rendelkezik saját Azure Data Lake Storage beállítással, csatlakozhat a Customer Insights szolgáltatáshoz, majd megoszthatja az adatokat a Marketing alkalmazással, ugyanúgy, mint egy felhőalapú beállításnál.

További információ: [Engedélyezze az adatmegosztást Dataverse a sajátjával Azure Data Lake Storage](customer-insights-dataverse.md#enable-data-sharing-with-dataverse-from-your-own-azure-data-lake-storage-preview)
