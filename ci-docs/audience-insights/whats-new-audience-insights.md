---
title: Új és jövőbeni funkciók
description: Információ az új szolgáltatásokról, továbbfejlesztésekről és hibajavításokról.
ms.date: 04/05/2022
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
ms.reviewer: skumm
manager: shellyha
ms.openlocfilehash: 2f081306271a170cf3e250fc1a193cedb70aeec6
ms.sourcegitcommit: 0363559a1af7ae16da2a96b09d6a4a8a53a8cbb8
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/05/2022
ms.locfileid: "8547675"
---
# <a name="whats-new-in-the-audience-insights-capability-of-dynamics-365-customer-insights"></a>A célközönséggel kapcsolatos újdonságok a Dynamics 365 Customer Insights-ban.

Örömmel jelentjük be legújabb frissítéseinket! Ez a cikk összefoglalja a nyilvános előzetes funkciókat, általános elérhetőségű javításokat és a funkciófrissítéseket. A hosszú távú funkciótervekkel megtekintéséhez tekintse meg a [Dynamics 365 és Power Platform a kiadási terveket](/dynamics365/release-plans/).

A frissítéseket régiónként tesszük közzé. Így bizonyos régiók a mások előtt láthatják a funkciókat. Hacsak nincs másképpen meghatározva, nem kell semmilyen műveletet végrehajtania, és az alkalmazás automatikusan, leállás nélkül frissíthető.

> [!TIP]
> Funkciókérelmek és termékjavaslatok benyújtásához és szavazáshoz látogassa meg a [Dynamics 365 alkalmazás ötletek portálját](https://experience.dynamics.com/ideas/categories/?forum=79a8c474-4e35-e911-a971-000d3a4f3343&forumName=Dynamics%20365%20Customer%20Insights).


## <a name="march-2022-updates"></a>2022 márciusi frissítések

A 2022. márciusi frissítések új funkciókat, teljesítményfrissítéseket és hibajavításokat tartalmaznak.

### <a name="liveramp-abilitec-enrichment-preview"></a>LiveRamp AbiliTec gazdagodás (Preview)

A LiveRamp identitásfeloldást és az ügyféladatok összevonását biztosítja. Az ügyféladatokban szereplő személyes azonosítókat leképezheti az AbiliTec identitásdiagramra, és AbiliTec azonosítókat kaphat. Ezután ezeket az azonosítókat használhatja az ügyféladatok jobb egyesítéséhez.

További információt az Ügyfélprofilok bővítése a LiveRamp (Preview) azonosító adataival című témakörben [talál](enrichment-liveramp.md).

### <a name="organize-segments-and-measures-with-tags-and-filters"></a>Szegmensek és mértékek rendszerezése címkékkel és szűrőkkel
Ha a szervezet sok szegmenst vagy intézkedést tart fenn, a megfelelő megtalálása néha kihívást jelenthet. Ez az új funkció lehetővé teszi listák szervezését címkék és oszlopok használatával. Segít gyorsan és egyszerűen megtalálni az adatokat, és testreszabhatja a nézeteket.

További információt a Címkék és oszlopok használata című témakörben [talál](work-with-tags-columns.md).

### <a name="enable-data-sharing-with-dataverse-when-using-your-own-storage-account"></a>Adatmegosztás Dataverse engedélyezése saját tárfiók használatakor

Ha a környezet a Customer Insights-adatok tárolására szolgál Azure Data Lake Storage, az adatmegosztáshoz Microsoft Dataverse további konfigurációra van szükség.
Korábban csak akkor engedélyezhette az adatmegosztást Dataverse, ha adatait a kezelt adattavankban tároltuk. 

További információt az Adatmegosztás engedélyezése saját [(előzetes verzió)Dataverse című Azure Data Lake Storage témakörben talál](manage-environments.md#enable-data-sharing-with-dataverse-from-your-own-azure-data-lake-storage-preview).

### <a name="new-export-destinations-iterable-and-braze"></a>Új exportcélpontok: Iterable és Braze

Új kapcsolatokkal bővítjük exportcélok ökoszisztémáját. Mostantól exportálhat szegmenseket az Iterable és a Braze szolgáltatásba az aktiválási szolgáltatásaik használatához.

További információt a Szegmensek exportálása iterable-be (előnézet) [és](export-iterable.md) szegmensek exportálása a Braze-be (előnézet) című [témakörben talál](export-braze.md).

### <a name="improvements-to-marketo-and-google-ads-export"></a>A Marketo és a Google Ads exportjának fejlesztései

A csatlakoztatott szolgáltatások API-jának módosítása az összekötők megbízható és zökkenőmentes működéséhez szükséges frissítésekhez vezet. Közzétettünk néhány frissítést a Marketo és a Google Ads szolgáltatásokba történő exportáláshoz:

- Google Ads: A Google Ads exportálási összekötőjének új verziója leegyszerűsíti a hitelesítési élményt, és most lehetővé teszi új Google Ads-célközönségek automatikus létrehozását. 
- Marketo: A Marketo exportcsatlakozó új verziója támogatja a Marketo ID azonosítót, lehetővé téve az adatok megkettőzésének elkerülését, a meglévő rekordok frissítését és új rekordok létrehozását a Marketo-ban. 


## <a name="february-2022-updates"></a>2022. februári frissítések

A 2022. februári frissítések új funkciókat, teljesítményfrissítéseket és hibajavításokat tartalmaznak.

### <a name="general-availability-for-prediction-models"></a>A előrejelzés modellek általános elérhetősége

A beépített előrejelzés modellek, beleértve **az előfizetés lemorzsolódását**, **a tranzakciós lemorzsolódást** és **az ügyfél élettartamának értékét (CLV),** általánosan elérhetővé válnak a Customer Insights részeként. 

További információt az Előrejelzések – áttekintés című témakörben [talál](predictions-overview.md).

### <a name="new-data-source-integration-with-azure-synapse-analytics-preview"></a>Új adatforrás: Integráció a Azure Synapse Analytics (preview)

Azure Synapse Analytics egy vállalati elemzési szolgáltatás, amely felgyorsítja az adattárházak és a big data rendszerek betekintésének idejét.

Azok a szervezetek, amelyek már használják Azure Synapse Analytics, betölthetik ezeket az adatokat a Customer Insightsba. 

További információt a adatforrás csatlakoztatása [(előnézet) című Azure Synapse témakörben talál](connect-synapse.md).

### <a name="liveramp-enrichment-preview"></a>LiveRamp gazdagodás (előzetes verzió)

A LiveRamp identitásfeloldást és az ügyféladatok összevonását biztosítja. Az ügyféladatokban szereplő személyes azonosítókat leképezheti az AbiliTec identitásdiagramra, és AbiliTec azonosítókat kaphat. Ezután ezeket az azonosítókat használhatja az ügyféladatok jobb egyesítéséhez.

További információt az Ügyfélprofilok bővítése a LiveRamp (Preview) azonosító adataival című témakörben [talál](enrichment-liveramp.md).

### <a name="enrichment-for-data-sources-preview"></a>Adatforrások gazdagítása (előzetes verzió)

Az adatok egyesítése előtt olyan forrásokból származó adatokat használhat, mint a Microsoft és más partnerek. Adatforrás gazdagodás segít a nagyobb adattömörség és minőség elérésében, ami segíthet jobb eredmények elérésében az adatok egységesítése után.

További információt az adatforrások gazdagítása (Előnézet) című [témakörben talál](data-sources-enrichment.md).

### <a name="change-owner-of-environment"></a>A környezet tulajdonosának megváltoztatása

Bár a Customer Insights szolgáltatásban több felhasználó is rendelkezhet rendszergazdai engedélyekkel, a környezetnek csak egy felhasználó a tulajdonosa. A továbbfejlesztett élmény lehetővé teszi a környezet tulajdonosainak megváltoztatását és a tulajdonjog megszerzését, ha egy korábbi tulajdonos elhagyta a szervezetet. 

További információt a Környezet [tulajdonosának módosítása című témakörben talál](manage-environments.md#change-the-owner-of-an-environment).

### <a name="data-preparation-process-lists-corruption-reason-for-corrupted-records"></a>Az adatelőkészítési folyamat felsorolja a sérült rekordok sérülési okát

Az adatelőkészítés most megmutatja a sérült adatokat tartalmazó összes mező sérülésének okát. Az információkat az egyes nyilvántartási szinten adják meg a könnyű azonosítás érdekében. 

További információt a Sérült adatforrások [című témakörben talál](entities.md#corrupted-data-sources).

### <a name="end-of-preview-for-reporting-features-in-the-engagement-insights-capability"></a>Előzetes verzió vége az elkötelezettségelemzési képesség jelentési funkcióinak jelentéséhez

Az Dynamics 365 Customer Insights engagement insights képesség előnézete 2022. február 15-én ért véget.  
Ez a változás azt jelenti, hogy a Customer Insights próbaverziója már nem tartalmazza a tölcsérek létrehozásának vagy más jelentéskészítési funkcióknak a képességét.

Meghívjuk Önt, hogy vizsgálja meg és értékelje a Customer Insights [, a Microsoft ügyféladat-platform (CDP) számos egyéb funkcióját](https://dynamics.microsoft.com/ai/customer-insights/).    
 
Átmeneti időszakban a meglévő előzetes verzió résztvevői továbbra is hozzáférhetnek bizonyos előnézeti képességekhez és funkciókhoz:

- Kód lekérése webhely vagy mobilalkalmazás tagolásához 
- Események és eseménytulajdonságok megtekintése 
- Az egyesített profilok fejlesztése a beszivárgott és kifinomult eseményekkel, hogy kihasználhassa az ügyféladatok teljes értékét
  
Az átmeneti időszak alatt a rögzített eseményeket továbbra is a csatlakoztatott Data Lake-be továbbítják. Miután ez a funkció ki van kapcsolva, az elkötelezettségi elemzések és a célközönség elemzések közötti adatmegosztás leáll, és nem küld új eseményeket a csatlakoztatott tárolóba.
Ha kérdése van a képesség előnézetének végével kapcsolatban, forduljon közvetlenül a Microsoft-fiók csapatához. Fiókcsapata naprakészen tartja Önt a közelgő indításokkal kapcsolatban. 

## <a name="january-2022-updates"></a>2022. januári frissítések

A 2022. januári frissítések új funkciókat, teljesítményfrissítéseket és hibajavításokat tartalmaznak.

### <a name="sentiment-analysis-of-your-customers-feedback"></a>Az ügyfél visszajelzéseinek hangulatelemzése

A Customer Insights egy új, AI-alapú funkciót kínál az ügyfelek hangulatának szintetizálásához és a konkrét üzleti szempontok azonosításához, mint a célzott fejlesztések lehetőségeihez. Az ügyfelek írásbeli visszajelzéseinek elemzésével pontos betekintést kaphat alacsony költséggel. A natural language processing (NLP) modellek által működtetett hangulatelemzés, amely minden ügyfélazonosítóhoz két származtatott betekintést hoz létre. Hangulati pontszám (-5-től 5-ig) és az alkalmazandó üzleti szempontok listája. 

További információt az Érzelmek elemzése az ügyfelek visszajelzéseiben (Előnézet) című témakörben [talál](sentiment-analysis.md).


[!INCLUDE[footer-include](../includes/footer-banner.md)]