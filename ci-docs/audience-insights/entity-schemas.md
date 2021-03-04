---
title: Customer Insights entitások sémája a Common Data Modellben
description: Entitások használata a Common Data Model rendszerben.
ms.date: 04/17/2020
ms.reviewer: mukeshpo
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: 9e7a6e944d37d25f4c25846644278b39b3ddd08e
ms.sourcegitcommit: 139548f8a2d0f24d54c4a6c404a743eeeb8ef8e0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/15/2021
ms.locfileid: "5269287"
---
# <a name="entity-schemas-in-common-data-model"></a>Entitássémák a Common Data Modelben

[!INCLUDE [cc-data-platform-banner](../includes/cc-data-platform-banner.md)]

A [Common Data Model](https://docs.microsoft.com/common-data-model/) leíró specifikáció, és olyan szabványos entitások nyílt forrású gyűjteménye, amelyek az üzleti és termelékenységi alkalmazás általánosan használt fogalmait és tevékenységeit jelképezik. Ez a modell kiterjed a megfigyelési és analitikai adatokra is. A Common Data Model olyan jól meghatározott, moduláris és bővíthető üzleti entitásokat kínál, mint például Fiók, Üzleti Egység, Eset, Névjegy, Érdeklődő, Lehetőség, és Termék, továbbá a szállítók, a dolgozók és a vásárlók közötti kommunikáció és kapcsolathoz tevékenységeket és szolgáltatói szerződéseket. Bárki létrehozhat és bővíthet Common Data Model meghatározásokat, hogy további üzleti-specifikus ötleteket lehessen rögzíteni.

Ez egy megosztott adatmodell, amely lehetővé teszi, hogy az alkalmazások és az adatintegrátorok könnyebben együttműködjenek az egységesen definiált adatokkal. A Common Data Model gazdag metaadatrendszert tartalmaz, amely szabványos entitásokkal, kapcsolatokokkal, hierarchiákkal, közös jellemzőkkel és egyéb tulajdonságokkal rendelkezik. A Dynamics 365 alkalmazásokból származik, és a nyílt forráskódú GitHubon, több mint 260 szabványos entitással. A belső és külső partnerek nagy rendszere hozzájárul az ágazatra jellemző fogalmakhoz a Common Data Modelhez.

A különböző rendszerek és platformok ma a Common Data Modelt alkalmazzák, beleértve a Power BI adatfolyamokat és az Azure Data Servicest is. Ez már támogatott a Common Data Service, Dynamics 365, Power Apps, Power BI és a közelgő Azure-Data Servicesben is, és közvetlenül adva értéket az [Open Data Iniative](https://www.microsoft.com/open-data-initiative) számára.

## <a name="customer-insights-entity-schemas"></a>Customer Insights entitássémák

Az ügyfél 360 fokos nézetének létrehozásához és a Customer Insights modelljeinek elérhetővé tételére a Common Data Modelben a bővíthetőség érdekében, a következő entitássémákat tették közzé:

| Entitás | Leírás |
|---------|---------|
|[CustomerActivity](https://docs.microsoft.com/common-data-model/schema/core/applicationcommon/foundationcommon/crmcommon/solutions/customerinsights/customeractivity) | A felhasználó által végzett tevékenység, amely megfigyelési értéket tartalmaz a vállalkozás számára. |
|[CustomerProfile](https://docs.microsoft.com/common-data-model/schema/core/applicationcommon/foundationcommon/crmcommon/solutions/customerinsights/customerprofile) | Olyan személy vagy szervezet, aki vagy amely üzleti tevékenységeket folytat vagy képes folytatni. |
|[MeasureDefinition](https://docs.microsoft.com/common-data-model/schema/core/applicationcommon/foundationcommon/crmcommon/solutions/customerinsights/measuredefinition) | Nulla vagy több dimenzióval particionált fő teljesítménymutatók (pl. havi aktív felhasználók, ügyfél összes kiadása, átlagos vevői beszerzési költség) definiálása |
|[Szegmens](https://docs.microsoft.com/common-data-model/schema/core/applicationcommon/foundationcommon/crmcommon/solutions/customerinsights/segment) | Meghatároz tagokból álló csoportot közös jellemzőkkel. |
|[SegmentMembership](https://docs.microsoft.com/common-data-model/schema/core/applicationcommon/foundationcommon/crmcommon/solutions/customerinsights/segmentmembership) | Az adott szegmensben részt vevő tagok. |

A további tudnivalókért lásd a [Customer Insights sémák a Common Data Modelben](https://docs.microsoft.com/common-data-model/schema/core/applicationcommon/foundationcommon/crmcommon/solutions/customerinsights/overview) című részt.

## <a name="view-entities-using-the-common-data-model-entity-navigator"></a>Entitások megtekintése a Common Data Model entitás-navigátor használatával

Az entitások a [Common Data Model entitásnavigátorban](https://microsoft.github.io/CDM/) tekinthetők meg. Válassza ki: **Betöltés GitHub-ról!** gombot és navigáljon a **foundationCommon** > **crmCommon** > **solutions** > **customerInsights** helyre, ahol megtalálja a Customer Insights entitásokat és azok definícióit.
> [!div class="mx-imgBorder"]
> ![A CDM-entitásnavigator CustomerActivity entitást mutatja](media/CDM-entity-navigator.png "A CDM-entitásnavigator CustomerActivity entitást mutatja")


[!INCLUDE[footer-include](../includes/footer-banner.md)]