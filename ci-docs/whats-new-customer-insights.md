---
title: A Dynamics 365 Customer Insights újdonságai
description: Információ az új szolgáltatásokról, továbbfejlesztésekről és hibajavításokról.
ms.date: 08/31/2022
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
ms.reviewer: skumm
manager: shellyha
ms.openlocfilehash: 1e734464cec1f66428c3a2a2e403437a2a9d8500
ms.sourcegitcommit: 624b27bb65a0de1970dc1ac436643b493f0a31cf
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/31/2022
ms.locfileid: "9387297"
---
# <a name="whats-new-in-dynamics-365-customer-insights"></a>A Dynamics 365 Customer Insights újdonságai

Örömmel jelentjük be legújabb frissítéseinket! Ez a cikk összefoglalja a nyilvános előzetes funkciókat, általános elérhetőségű javításokat és a funkciófrissítéseket. A hosszú távú funkciótervekkel megtekintéséhez tekintse meg a [Dynamics 365 és Power Platform a kiadási terveket](/dynamics365/release-plans/).

A frissítéseket régiónként tesszük közzé. Így bizonyos régiók a mások előtt láthatják a funkciókat. Hacsak nincs másképp megadva, nem kell semmilyen műveletet végrehajtania, automatikusan frissítjük az alkalmazást állásidő nélkül.

> [!TIP]
> Funkciókérelmek és termékjavaslatok benyújtásához és szavazáshoz látogassa meg a [Dynamics 365 alkalmazás ötletek portálját](https://experience.dynamics.com/ideas/categories/?forum=79a8c474-4e35-e911-a971-000d3a4f3343&forumName=Dynamics%20365%20Customer%20Insights).

## <a name="august-2022-updates"></a>2022. augusztusi frissítések

A 2022. augusztusi frissítések új funkciókat, teljesítményfrissítéseket és hibajavításokat tartalmaznak.

### <a name="contact-unification-in-b-to-b-environments"></a>Kapcsolategyesítés B-B környezetekben

A Customer Insights B-to-B környezetei mostantól támogatják a továbbfejlesztett adategyesítési élményt.

Mostantól a fiókok mellett egyesítheti a kapcsolattartókat, hogy teljes képet kapjon az üzleti kapcsolattartókról. Az egyesített kapcsolattartók egységes fiókokhoz vannak társítva, és mostantól szerepelnek az ügyfélkártyákon. 

További információ: [Egyesített kapcsolattartói profil létrehozása](data-unification-contacts.md).

### <a name="create-and-export-of-segments-based-on-unified-contacts"></a>Szegmensek létrehozása és exportálása egyesített névjegyek alapján

Az új kapcsolategyesítésnek köszönhetően kapcsolattartói szegmenseket hozhat létre a kapcsolattartók, partnerek vagy mindkettő kritériumainak felhasználásával. Ezek a szegmensek exportálhatók más szolgáltatásokban való aktiváláshoz.

További információ: [Exportálások áttekintése](export-destinations.md).

## <a name="july-2022-updates"></a>2022. júliusi frissítések

A 2022. júliusi frissítések új funkciókat, teljesítményfrissítéseket és hibajavításokat tartalmaznak.

### <a name="export-to-moengage"></a>Exportálás a MoEngage-be

Exportálja az egyesített ügyfélprofilok szegmenseit a MoEngage-be, és használja őket e-mail marketinghez a MoEngage-ben.

További információ: [Szegmensek exportálása a MoEngage szolgáltatásba](export-moengage.md).

### <a name="ssh-support-for-sftp-based-exports"></a>SSH-támogatás SFTP-alapú exportálásokhoz

Válassza ki, hogy SSH-n vagy felhasználónévn/jelszón keresztül szeretne-e hitelesíteni az SFTP-exportálási célhelyekkel való kapcsolatokhoz.

További információ: [Adatok exportálása SFTP-gazdagépekre](export-sftp.md).

### <a name="personalize-experiences-with-data-about-known-and-unknown-users"></a>A felhasználói élmény személyre szabása ismert és ismeretlen felhasználókra vonatkozó adatokkal

Az ügyféladatok kezelése nem új kihívás, de egyre nehezebbé válik, ahogy a felhasználók eligazodnak a márkák által kínált különböző digitális csatornákon. Az egyik csatornán ismert (hitelesített) felhasználó ismeretlenné (nem hitelesítetté) válik egy másikban, ha nincs bejelentkezve. A probléma gyakran az, hogy a nem hitelesített (ismeretlen) felhasználók nem rendelkeznek közös azonosítóval. Használható értelmes profilok attribútumainak társítására és egységes ügyfélprofilok létrehozására. A Customer Insights segít megoldani ezt a problémát azáltal, hogy adatokat tölt be a forrásrendszereken lévő nyomkövetési módszerekből.

További információ: [A felhasználói élmény személyre szabása ismert és ismeretlen felhasználók](unknown-to-known.md) adataival.

## <a name="june-2022-updates"></a>2022. júniusi frissítések

A 2022. júniusi frissítések új funkciókat, teljesítményfrissítéseket és hibajavításokat tartalmaznak.

### <a name="updated-user-experience-for-data-sources-and-data-ingestion"></a>Frissített felhasználói élmény az adatforrásokhoz és az adatbetöltéshez

Az adatok importálása az adatforrások széles köréből az alapja annak, hogy az ügyféladatokat konszolidálja.Dynamics 365 Customer Insights Újra megvizsgáltuk az adatforrások importálásához és csatlakoztatásához szükséges felhasználói élményt. A frissítés célja, hogy megkönnyítse az adatok betöltését a Customer Insights szolgáltatásba.

További információ: [Adatforrások áttekintése](data-sources.md).

### <a name="export-to-inmobi"></a>Exportálás az InMobi szolgáltatásba

Az InMobi segít a márkáknak megérteni, azonosítani, bevonni és megszerezni a fogyasztókat. Szegmenseket és egyéb adatokat exportálhat az InMobi szolgáltatásba Azure Blob Storage-fiókokon keresztül.

További információ: [Exportálás Az InMobi szolgáltatásba (előzetes verzió)](export-inmobi.md)

### <a name="lockbox-support-in-customer-insights"></a>A lockbox támogatása a Customer Insights szolgáltatásban

Az ügyfél-kulcszárlat felületet biztosít az adatelérési kérelmek áttekintéséhez és jóváhagyásához (vagy elutasításához). Ezek a kérések akkor fordulnak elő, ha az ügyféladatokhoz való adathozzáférésre van szükség egy támogatási eset megoldásához.

További információ: [Ügyféladatok biztonságos elérése az ügyfélkostábbal (előzetes verzió)](security-overview.md#securely-access-customer-data-with-customer-lockbox-preview).

### <a name="connect-to-your-data-using-azure-private-link"></a>Csatlakozás az adatokhoz az Azure Private Link használatával

Azure Private Link lehetővé teszi, hogy a Customer Insights a virtuális hálózat privát végpont keresztül csatlakozzon a fiókjához Azure Data Lake Storage. A tárfiókban lévő adatok esetében, amelyek nincsenek kitéve a nyilvános internetnek, Private Link engedélyezi a kapcsolatot az adott korlátozott hálózattal.

További információ: [Use Private Link in Customer Insights (A Private Link használata a Customer Insights szolgáltatásban](security-overview.md#set-up-an-azure-private-link)).

## <a name="may-2022-updates"></a>2022. májusi frissítések

A 2022. májusi frissítések új funkciókat, teljesítményfrissítéseket és hibajavításokat tartalmaznak.

### <a name="updated-data-unification-experience"></a>Frissített adategyesítési élmény

 Az adatok egyesítése lehetővé teszi az egykor eltérő adatforrások egyesítését egyetlen fő adatkészletben, amely egységes nézetet biztosít az adatokról. Az adatok egyesíthetők egyetlen entitáson vagy több entitáson. [Először kiválaszthatja az entitásokat és a forrásmezőket](map-entities.md), [eltávolíthatja az ismétlődő rekordokat](remove-duplicates.md), szabályokat adhat meg a feltételek [egyeztetésére](match-entities.md), és meghatározhatja, hogy mely [mezőket kell belefoglalni az egységes ügyfélprofilokba](merge-entities.md).

További információ: [Adategyesítés – áttekintés](data-unification.md).

### <a name="refreshed-home-page-in-customer-insights"></a>Frissített kezdőlap a Customer Insights szolgáltatásban

**Az otthoni** verzió végigvezeti a legfontosabb funkciók konfigurációs folyamatán, és áttekintést nyújt a szegmensekről, a mértékekről és a gazdagítási adatokról. Frissítettük a felhasználói élményt, hogy egy pillanat alatt relevánsabb információkat nyújtsunk.

További információ: [A Customer Insights](home.md) felfedezése.

### <a name="track-usage-of-a-segment"></a>Szegmens használatának nyomon követése

Mostantól [nyomon követheti egy szegmens](segments.md#track-usage-of-a-segment) használatát az alkalmazásokban, amelyek a Dataverse Customer Insights szolgáltatáshoz kapcsolódó szervezeten alapulnak. A Dynamics 365 Marketing [ügyfélútjaiban használt Customer Insights szegmensek esetében](/dynamics365/marketing/real-time-marketing-ci-profile) a rendszer tájékoztatja Önt az adott szegmens használatáról.

### <a name="export-to-criteo"></a>Exportálás Criteo-ba

A Criteo egy online platform, amely segít a felhasználóknak a digitális hirdetések kezelésében. Mostantól exportálhatja az egységes ügyfélprofilok szegmenseit kampányok létrehozásához, e-mailes marketing biztosításához és meghatározott ügyfélcsoportok használatához a Criteo segítségével.

További információ: [Szegmensek exportálása Criteo-ba (előzetes verzió)](export-criteo.md).

### <a name="refined-documentation-structure-for-environment-creation"></a>Kifinomult dokumentációs struktúra a környezet létrehozásához

Újra áttekintettük a környezetek létrehozásával és kezelésével kapcsolatos súgódokumentumokat a Customer Insights szolgáltatásban. A cikkek mostantól a tartalomjegyzék Környezetek csomópontja alatt vannak csoportosítva. Az átstrukturált cikkek több útmutatást nyújtanak a környezetek beállításának különböző módjaihoz, és világosabb struktúrával rendelkeznek. Ha van megosztható visszajelzésed, tudasd velünk a súgócikkek vége felé található vezérlőkön keresztül.

További információ: [How to: Create a new environment (Hogyan lehet: Új környezet](create-environment.md) létrehozása).

## <a name="april-2022-updates"></a>2022. áprilisi frissítések

A 2022. áprilisi frissítések új funkciókat, teljesítményfrissítéseket és hibajavításokat tartalmaznak.

### <a name="dun--bradstreet-enrichment-preview"></a>Dun &Bradstreet enrichment (előzetes verzió)

A Dun & Bradstreet kereskedelmi adatokat, elemzéseket és betekintést nyújt a vállalkozások számára. Lehetővé teszi, hogy az ügyfelek az egyesített ügyfélprofilokkal bővítsék az adataikat. A bővítések olyan attribútumokat tartalmaznak, mint a DUNS-szám, a vállalat mérete, a hely, az ipar és egyebek.

További információ: [Vállalati profilok gazdagítása a Dun & Bradstreet (előzetes verzió)](enrichment-dnb.md)-val.

### <a name="define-the-measure-type-when-creating-a-new-measure"></a>A mérték típusának meghatározása új mérték létrehozásakor

Mostantól a teljes vállalkozásodban megkülönböztetheted az egyes profilokra és mértékekre vonatkozó mértékeket. Míg az üzleti mérések a Customer Insights kezdőlapján jelennek meg, az ügyfelek mérései a részletes ügyfélmegtekintésekben jelennek meg.

További információ: [Mértékkészítő használata a semmiből](measure-builder.md) történő intézkedések létrehozásához.

### <a name="consolidation-of-customer-insights-documentation"></a>A Customer Insights dokumentációjának konszolidálása

Újra áttekintettük a dokumentációs cikkeinket, és eltávolítottuk az elkötelezettségi elemzésekről és a célközönség elemzési képességekről szóló említéseket. A továbbiakban következetesen a Customer Insights terméknévre fogunk hivatkozni, amikor az alkalmazás alapvető funkcióiról írunk. Ez a változás a tartalomjegyzék, az URL-struktúra és a mögöttes dokumentációs adattárban található fájlútvonalak jelentős szerkezetátalakításához is vezet. Az összes könyvjelző vagy meglévő hivatkozás továbbra is működik, és átirányít a frissített URL-címekre.

Ha szeretnéd tudatni velünk, hogy hogyan érzékeled ezt a változást, vagy azt szeretnéd észrevenni, hogy valami nem a várt módon működik, mondd el nekünk az oldal visszajelzéseinek [beküldésével](https://github.com/MicrosoftDocs/customer-insights/issues/new?title=&body=%0A%0A%5BEnter%20feedback%20here%5D%0A%0A%0A---%0A%23%23%23%23%20Document%20Details%0A%0A%E2%9A%A0%20*Do%20not%20edit%20this%20section.%20It%20is%20required%20for%20docs.microsoft.com%20%E2%9E%9F%20GitHub%20issue%20linking.*%0A%0A*%20ID%3A%20d323ba46-f96e-1972-bc52-9b88f7d9cdfa%0A*%20Version%20Independent%20ID%3A%20d323ba46-f96e-1972-bc52-9b88f7d9cdfa%0A*%20Content%3A%20%5BNew%20and%20upcoming%20features%20-%20Dynamics%20365%20Customer%20Insights%5D(https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fdynamics365%2Fcustomer-insights%2Fwhats-new-customer-insights)%0A*%20Content%20Source%3A%20%5Bci-docs%2Fwhats-new-customer-insights.md%5D(https%3A%2F%2Fgithub.com%2FMicrosoftDocs%2Fcustomer-insights%2Fblob%2Fmain%2Fci-docs%2Fwhats-new-customer-insights.md)%0A*%20Service%3A%20**customer-insights**%0A*%20Sub-service%3A%20**audience-insights**%0A*%20GitHub%20Login%3A%20%40m-hartmann%0A*%20Microsoft%20Alias%3A%20**mhart**).

## <a name="march-2022-updates"></a>2022 márciusi frissítések

A 2022. márciusi frissítések új funkciókat, teljesítményfrissítéseket és hibajavításokat tartalmaznak.

### <a name="liveramp-abilitec-enrichment-preview"></a>LiveRamp AbiliTec gazdagítás (előzetes verzió)

A LiveRamp biztosítja az identitásfeloldást és az ügyféladatok összevonását. Az ügyféladatokban szereplő személyes azonosítókat leképezheti az AbiliTec identitásgráfra, és AbiliTec-azonosítókat kaphat. Ezután ezekkel az azonosítókkal jobban egyesítheti az ügyféladatokat.

További információ: [Ügyfélprofilok gazdagítása a LiveRamp (előzetes verzió) identitásadataival](enrichment-liveramp.md).

### <a name="organize-segments-and-measures-with-tags-and-filters"></a>Szegmensek és mértékek rendszerezése címkékkel és szűrőkkel

Ha a szervezet sok szegmenst vagy intézkedést tart fenn, a megfelelő megtalálása néha kihívást jelenthet. Ez az új funkció lehetővé teszi a listák címkék és oszlopok segítségével történő rendszerezését. Segít az adatok gyors és egyszerű megtalálásában és a nézetek testreszabásában.

További információ: [Címkék és oszlopok használata](work-with-tags-columns.md).

### <a name="enable-data-sharing-with-dataverse-when-using-your-own-storage-account"></a>Az adatmegosztás Dataverse engedélyezése saját tárfiók használata esetén

Ha a környezet Customer Insights-adatok tárolására használ Azure Data Lake Storage, az adatmegosztásnak Microsoft Dataverse további konfigurációra van szüksége.
Korábban csak akkor engedélyezheti az adatmegosztást Dataverse, ha az adatokat a felügyelt adattónkban tároltuk.

További információ: [Az adatmegosztás Dataverse engedélyezése a sajátjával Azure Data Lake Storage (előzetes verzió)](customer-insights-dataverse.md#enable-data-sharing-with-dataverse-from-your-own-azure-data-lake-storage-preview).

### <a name="new-export-destinations-iterable-and-braze"></a>Új exportcélpontok: Iterable és Braze

Új kapcsolatokkal bővítjük tovább az exportcélpontok ökoszisztémáját. Mostantól exportálhat szegmenseket az Iterable és a Braze alkalmazásba az aktiválási szolgáltatásaik használatához.

További információ: [Szegmensek exportálása Iterable-be (előzetes verzió)](export-iterable.md) és [Szegmensek exportálása Braze-be (előzetes verzió)](export-braze.md).

### <a name="improvements-to-marketo-and-google-ads-export"></a>A Marketo és a Google Ads exportálásának fejlesztései

A csatlakoztatott szolgáltatások API-jainak módosítása az összekötők megbízható és zökkenőmentes futtatásához szükséges frissítéseket eredményez. Kiadtunk néhány frissítést a Marketo és a Google Ads szolgáltatásokba történő exportálásokhoz:

- Google Ads: A Google Ads exportálási összekötő új verziója leegyszerűsíti a hitelesítési élményt, és mostantól lehetővé teszi, hogy automatikusan új Google Ads-közönségeket hozzon létre. 
- Marketo: A Marketo export-összekötő új verziója támogatja a Marketo ID-t, lehetővé téve az adatok megkettőzésének elkerülését, a meglévő rekordok frissítését és új rekordok létrehozását a Marketóban. 

## <a name="february-2022-updates"></a>2022. februári frissítések

A 2022. februári frissítések új funkciókat, teljesítményfrissítéseket és hibajavításokat tartalmaznak.

### <a name="general-availability-for-prediction-models"></a>A előrejelzés modellek általános elérhetősége

A beépített előrejelzés modellek, beleértve **az előfizetés-lemorzsolódást**, **a tranzakciós lemorzsolódást** és **az ügyfél élettartamra vetített értékét (CLV),** általánosan elérhetővé válnak a Customer Insights részeként. 

További tájékoztatás: [Az előrejelzések áttekintése](predictions-overview.md).

### <a name="new-data-source-integration-with-azure-synapse-analytics-preview"></a>Új adatforrás: Integráció Azure Synapse Analytics (előzetes verzió)

Azure Synapse Analytics egy vállalati elemzési szolgáltatás, amely felgyorsítja az adattárházak és big data-rendszerek közötti betekintéshez szükséges időt.

Azok a szervezetek, amelyek már használják Azure Synapse Analytics, betölthetik ezeket az adatokat a Customer Insights szolgáltatásba. 

További információ: [Adatforrás csatlakoztatása Azure Synapse (előzetes verzió)](connect-synapse.md).

### <a name="liveramp-enrichment-preview"></a>LiveRamp gazdagítás (előzetes verzió)

A LiveRamp biztosítja az identitásfeloldást és az ügyféladatok összevonását. Az ügyféladatokban szereplő személyes azonosítókat leképezheti az AbiliTec identitásgráfra, és AbiliTec-azonosítókat kaphat. Ezután ezekkel az azonosítókkal jobban egyesítheti az ügyféladatokat.

További információ: [Ügyfélprofilok gazdagítása a LiveRamp (előzetes verzió) identitásadataival](enrichment-liveramp.md).

### <a name="enrichment-for-data-sources-preview"></a>Adatforrások gazdagítása (előzetes verzió)

Használjon olyan forrásokból származó adatokat, mint a Microsoft és más partnerek, hogy az adatok egyesítése előtt gazdagítsa az ügyféladatokat. Adatforrás gazdagítások segítenek az adatok teljességének és minőségének javításában, ami segíthet jobb eredmények elérésében az adatok egységesítése után.

További információ: [Adatforrások gazdagítása (előzetes verzió)](data-sources-enrichment.md).

### <a name="change-owner-of-environment"></a>A környezet tulajdonosának megváltoztatása

Bár több felhasználó is rendelkezhet rendszergazdai engedélyekkel a Customer Insights szolgáltatásban, csak egy felhasználó a környezet tulajdonosa. A továbbfejlesztett felhasználói élmény lehetővé teszi a környezet tulajdonosainak megváltoztatását és tulajdonjogának igénylését, ha egy korábbi tulajdonos elhagyta a szervezetet. 

További információ: [Környezet](manage-environments.md#change-the-owner-of-an-environment) tulajdonosának módosítása.

### <a name="data-preparation-process-lists-corruption-reason-for-corrupted-records"></a>Az adat-előkészítési folyamat felsorolja a sérült rekordok sérülési okát

Az adatelőkészítés mostantól a sérült adatokat tartalmazó mezők sérülésének okát mutatja. Az információkat az egyedi rekord szintjén nyújtják a könnyű azonosítás érdekében. 

További információ: [Sérült adatforrások](entities.md#corrupted-data-sources).

### <a name="end-of-preview-for-reporting-features-in-the-engagement-insights-capability"></a>Az elköteleződési elemzési képesség jelentéskészítési funkcióinak előzetes verziójának vége

Az Dynamics 365 Customer Insights elkötelezettségi elemzések képesség előzetes verziója 2022. február 15-én ért véget.  
Ez a módosítás azt jelenti, hogy a Customer Insights próbaverziója már nem tartalmazza a csatornák létrehozásának és más jelentéskészítési funkciók létrehozásának lehetőségét.

Meghívjuk Önt, hogy fedezze fel és értékelje a Customer Insights [, a Microsoft ügyféladat-platformjának](https://dynamics.microsoft.com/ai/customer-insights/)(CDP) számos egyéb funkcióját.    
 
Egy átmeneti időszakban a meglévő előzetes verzió résztvevői továbbra is hozzáférhetnek néhány előzetes verziójú képességhez és funkcióhoz:

- Kód lekérése webhely vagy mobilalkalmazás tagolásához 
- Események és eseménytulajdonságok megtekintése 
- Az egyesített profilok fejlesztése betöltött és finomított eseményekkel, hogy kihasználják az ügyféladatok teljes értékét
  
Az átmeneti időszak alatt a rögzített események továbbra is streamelve vannak a csatlakoztatott Data Lake-be. A funkció kikapcsolása után az adatmegosztás leáll, és a rendszer nem küld új eseményeket a csatlakoztatott tárolóba.
Lépjen kapcsolatba közvetlenül a Microsoft-fiók csapatával, ha kérdése van a képesség előzetes verziójának végével kapcsolatban. A fiók csapata naprakészen tartja Önt a közelgő indításokkal kapcsolatban. 

## <a name="january-2022-updates"></a>2022. januári frissítések

A 2022. januári frissítések új funkciókat, teljesítményfrissítéseket és hibajavításokat tartalmaznak.

### <a name="sentiment-analysis-of-your-customers-feedback"></a>Az ügyfél visszajelzéseinek hangulatelemzése

A Customer Insights egy új, AI-alapú funkciót biztosít az ügyfelek hangulatának szintetizálásához és az egyes üzleti szempontok azonosításához a célzott fejlesztések lehetőségeként. Az ügyfelek írásos visszajelzéseinek elemzésével pontos betekintést nyerhetsz alacsony költségek mellett. Hangulatelemzés, amelyet természetes nyelvi feldolgozás (NLP) modellek működtetnek, amelyek két származtatott betekintést hoznak létre minden ügyfél-azonosítóhoz. Hangulati pontszám (–5–5) és az alkalmazandó üzleti szempontok listája. 

További információ: [Hangulatelemzés az ügyfelek visszajelzéseiben (előzetes verzió)](sentiment-analysis.md).


[!INCLUDE [footer-include](includes/footer-banner.md)]