---
title: Customer Insights entitások sémája a Common Data Modellben
description: Entitások használata a Common Data Model rendszerben.
ms.date: 08/13/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: mukeshpo
ms.author: mukeshpo
manager: shellyha
---

# <a name="entity-schemas-in-common-data-model"></a>Entitássémák a Common Data Modelben



A [Common Data Model](/common-data-model/) leíró specifikáció, és olyan szabványos entitások nyílt forrású gyűjteménye, amelyek az üzleti és termelékenységi alkalmazás általánosan használt fogalmait és tevékenységeit jelképezik. Ez a modell kiterjed a megfigyelési és analitikai adatokra is. A Common Data Model olyan jól meghatározott, moduláris és bővíthető üzleti entitásokat kínál, mint például Fiók, Üzleti Egység, Eset, Névjegy, Érdeklődő, Lehetőség, és Termék, továbbá a szállítók, a dolgozók és a vásárlók közötti kommunikáció és kapcsolathoz tevékenységeket és szolgáltatói szerződéseket. Bárki létrehozhat és bővíthet Common Data Model meghatározásokat, hogy további üzleti-specifikus ötleteket lehessen rögzíteni.

Ez egy megosztott adatmodell, amely lehetővé teszi, hogy az alkalmazások és az adatintegrátorok könnyebben együttműködjenek az egységesen definiált adatokkal. A Common Data Model gazdag metaadatrendszert tartalmaz, amely szabványos entitásokkal, kapcsolatokokkal, hierarchiákkal, közös jellemzőkkel és egyéb tulajdonságokkal rendelkezik. A Dynamics 365 alkalmazásokból származik, és a nyílt forráskódú GitHubon, több mint 260 szabványos entitással. A belső és külső partnerek nagy rendszere hozzájárul az ágazatra jellemző fogalmakhoz a Common Data Modelhez.

A Common Data Modelt ma több rendszeren és platformon is alkalmazva van, beleértve a Power BI adatfolyamokat és az Azure Data Servicest is. Már támogatott a Microsoft Dataverse, Dynamics 365, Power Apps, Power BI és a hamarosan megjelenő Azure adatszolgáltatásokban is, az értékeket közvetlenül az [Open Data Initiative](https://www.microsoft.com/open-data-initiative) felé közelítve.

## <a name="customer-insights-entity-schemas"></a>Customer Insights entitássémák

Az ügyfél 360 fokos nézetének létrehozásához és a Customer Insights modelljeinek elérhetővé tételére a Common Data Modelben a bővíthetőség érdekében, a következő entitássémákat tették közzé:

| Entitás | Leírás |
|---------|---------|
|[CustomerActivity](/common-data-model/schema/core/applicationcommon/foundationcommon/crmcommon/solutions/customerinsights/customeractivity) | A felhasználó által végzett tevékenység, amely megfigyelési értéket tartalmaz a vállalkozás számára. |
|[CustomerProfile](/common-data-model/schema/core/applicationcommon/foundationcommon/crmcommon/solutions/customerinsights/customerprofile) | Olyan személy vagy szervezet, aki vagy amely üzleti tevékenységeket folytat vagy képes folytatni. |
|[MeasureDefinition](/common-data-model/schema/core/applicationcommon/foundationcommon/crmcommon/solutions/customerinsights/measuredefinition) | Nulla vagy több dimenzióval particionált fő teljesítménymutatók (pl. havi aktív felhasználók, ügyfél összes kiadása, átlagos vevői beszerzési költség) definiálása |
|[Szegmens](/common-data-model/schema/core/applicationcommon/foundationcommon/crmcommon/solutions/customerinsights/segment) | Meghatároz tagokból álló csoportot közös jellemzőkkel. |
|[SegmentMembership](/common-data-model/schema/core/applicationcommon/foundationcommon/crmcommon/solutions/customerinsights/segmentmembership) | Az adott szegmensben részt vevő tagok. |

A további tudnivalókért lásd a [Customer Insights sémák a Common Data Modelben](/common-data-model/schema/core/applicationcommon/foundationcommon/crmcommon/solutions/customerinsights/overview) című részt.

## <a name="view-entities-using-the-common-data-model-entity-navigator"></a>Entitások megtekintése a Common Data Model entitás-navigátor használatával

Az entitások a [Common Data Model entitásnavigátorban](https://microsoft.github.io/CDM/) tekinthetők meg. A Customer Insights-entitások és definícióik listájának a kiválasztásával jelöljön ki egy entitást az Információs alkalmazás szakaszból.
> [!div class="mx-imgBorder"]
> ![A CDM-entitásnavigator CustomerActivity entitást mutatja.](media/CDM-entity-navigator.png "A CDM-entitásnavigator CustomerActivity entitást mutatja")


[!INCLUDE[footer-include](../includes/footer-banner.md)]
