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
ms.openlocfilehash: dcee60a73e0c32278553253040478c31e45237ae
ms.sourcegitcommit: 618ef15b434de0a68213383b6521ce2a60753afb
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 10/07/2022
ms.locfileid: "9638354"
---
# <a name="whats-new-in-dynamics-365-customer-insights"></a>A Dynamics 365 Customer Insights újdonságai

Örömmel jelentjük be legújabb frissítéseinket! Ez a cikk összefoglalja a nyilvános előzetes funkciókat, általános elérhetőségű javításokat és a funkciófrissítéseket. A hosszú távú funkciótervekkel megtekintéséhez tekintse meg a [Dynamics 365 és Power Platform a kiadási terveket](/dynamics365/release-plans/).

A frissítéseket régiónként tesszük közzé. Így bizonyos régiók a mások előtt láthatják a funkciókat. Hacsak másként nincs megadva, nem kell semmilyen műveletet végrehajtania, automatikusan frissítjük az alkalmazást állásidő nélkül.

> [!TIP]
> Funkciókérelmek és termékjavaslatok benyújtásához és szavazáshoz látogassa meg a [Dynamics 365 alkalmazás ötletek portálját](https://experience.dynamics.com/ideas/categories/?forum=79a8c474-4e35-e911-a971-000d3a4f3343&forumName=Dynamics%20365%20Customer%20Insights).

## <a name="september-2022-updates"></a>2022. szeptemberi frissítések

A 2022. szeptemberi frissítések új funkciókat, teljesítményfrissítéseket és hibajavításokat tartalmaznak.

### <a name="export-data-to-hubspot"></a>Adatok exportálása a HubSpot programba

Exportálja az egyesített ügyfélprofilok szegmenseit a HubSpotba, és használja őket e-mail marketinghez.

További információ: [Szegmensek exportálása a HubSpotba](export-hubspot.md).

### <a name="remove-a-unified-field-or-entity-from-data-unification"></a>Egyesített mező vagy entitás eltávolítása az adategyesítésből

Mezőket és entitásokat távolíthat el az adategyesítési folyamatból.

További információ: [Egyesített mező eltávolítása](data-unification-update.md#remove-a-unified-field).

### <a name="manage-unknown-customer-profiles"></a>Ismeretlen ügyfélprofilok kezelése

Az emlékezetes személyre szabás az ügyféladatok gazdagságától és teljességétől függ, és a Customer Insights segít elérni ezeket a célokat. Kezelheti azoknak a felhasználóknak az ügyfélprofiljait, akikhez az azonosítón kívül más információval nem rendelkezik.

További tájékoztatás: [Ismeretlen profilok kezelése a Customer Insights segítségével](manage-unknown-profiles.md).

## <a name="august-2022-updates"></a>2022. augusztusi frissítések

A 2022. augusztusi frissítések új funkciókat, teljesítményfrissítéseket és hibajavításokat tartalmaznak.

### <a name="contact-unification-in-b-to-b-environments"></a>Kapcsolategyesítés B-to-B környezetekben

A Customer Insights B-to-B környezetei mostantól támogatják a továbbfejlesztett adategyesítési élményt.

Mostantól a partnerek mellett egyesítheti a névjegyeket, hogy teljes képet kapjon az üzleti kapcsolatokról. Az egyesített kapcsolattartók az egyesített partnerekhez vannak társítva, és most már szerepelnek az ügyfélkártyákon. 

További tájékoztatás: [Egységes kapcsolattartói profil létrehozása](data-unification-contacts.md).

### <a name="create-and-export-of-segments-based-on-unified-contacts"></a>Szegmensek létrehozása és exportálása egységes kapcsolattartók alapján

Az új kapcsolattartó-egyesítésnek köszönhetően kapcsolattartói szegmenseket hozhat létre a kapcsolattartók, a partnerek vagy mindkettő feltételeinek használatával. Ezek a szegmensek exportálhatók más szolgáltatásokban való aktiváláshoz.

További információ: [Exportálások áttekintése](export-destinations.md).

### <a name="deployment-regions-aligned-with-microsoft-dataverse"></a>A következőhöz igazított üzembe helyezési régiók: Microsoft Dataverse

Új Customer Insights-környezet létrehozásakor kiválaszthatja azt a régiót, ahol üzembe szeretné helyezni és üzemeltetni szeretné a szolgáltatást. Frissítettük a régió kiválasztását, hogy igazodjon Microsoft Dataverse a Power Platform.

Mostantól könnyedén kiválaszthatja ugyanazt a régiót, mint a meglévő Microsoft Dataverse környezet vagy az Azure Data Lake Storage-fiókja (ha ezt a lehetőséget választja), attól függően, hogy a Customer Insights elérhető-e az adott régióban.

További információ: [Új környezet](create-environment.md) létrehozása és [A termék rendelkezésre állása földrajzi hely](https://dynamics.microsoft.com/availability-reports/) szerint.

## <a name="july-2022-updates"></a>2022. júliusi frissítések

A 2022. júliusi frissítések új funkciókat, teljesítményfrissítéseket és hibajavításokat tartalmaznak.

### <a name="export-to-moengage"></a>Exportálás a MoEngage programba

Exportálja az egységes ügyfélprofilok szegmenseit a MoEngage-be, és használja őket e-mail marketinghez a MoEngage-ben.

További információ: [Szegmensek exportálása a MoEngage szolgáltatásba](export-moengage.md).

### <a name="ssh-support-for-sftp-based-exports"></a>SSH-támogatás SFTP-alapú exportáláshoz

Válassza ki, hogy SSH-n vagy felhasználónévvel/jelszóval szeretne-e hitelesítést végezni az SFTP-exportálási célhelyekhez való csatlakozáshoz.

További információ: [Adatok exportálása SFTP-gazdagépekre](export-sftp.md).

### <a name="personalize-experiences-with-data-about-known-and-unknown-users"></a>A felhasználói élmény személyre szabása ismert és ismeretlen felhasználókra vonatkozó adatokkal

Az ügyféladatok kezelése nem új kihívás, de egyre nehezebbé válik, ahogy a felhasználók navigálnak a márkák által kínált különböző digitális csatornákon. Az egyik csatornán ismert (hitelesített) felhasználó ismeretlenné (nem hitelesítetté) válik egy másikban, ha nincs bejelentkezve. A probléma gyakran az, hogy a nem hitelesített (ismeretlen) felhasználók nem rendelkeznek közös azonosítóval. Használható értelmes profilattribútumok társítására és egységes ügyfélprofilok létrehozására. A Customer Insights segít megoldani ezt a problémát azáltal, hogy adatokat tölt be a forrásrendszerek nyomkövetési módszereiből.

További információ: [A felhasználói élmény személyre szabása ismert és ismeretlen felhasználók](unknown-to-known.md) adataival.

## <a name="june-2022-updates"></a>2022. júniusi frissítések

A 2022. júniusi frissítések új funkciókat, teljesítményfrissítéseket és hibajavításokat tartalmaznak.

### <a name="updated-user-experience-for-data-sources-and-data-ingestion"></a>Frissített felhasználói élmény az adatforrásokhoz és az adatbetöltéshez

Az adatforrások széles köréből származó adatok importálása az alapja az ügyféladatok Dynamics 365 Customer Insights összevonásának. Újra megvizsgáltuk a felhasználói élményt az adatforrások importálásához és összekapcsolásához. A frissítés célja, hogy megkönnyítse az adatok Customer Insights szolgáltatásba való betöltését.

További információ: [Adatforrások áttekintése](data-sources.md).

### <a name="export-to-inmobi"></a>Exportálás az InMobi programba

Az InMobi segít a márkáknak megérteni, azonosítani, bevonni és megszerezni a fogyasztókat. Szegmenseket és egyéb adatokat exportálhat az InMobi szolgáltatásba Azure Blob Storage-fiókokon keresztül.

További információ: [Exportálás InMobi formátumba (előzetes verzió)](export-inmobi.md)

### <a name="lockbox-support-in-customer-insights"></a>Kulcsszéftámogatás a Customer Insights szolgáltatásban

Az ügyfélszéf felületet biztosít az adatelérési kérelmek áttekintéséhez és jóváhagyásához (vagy elutasításához). Ezek a kérések akkor fordulnak elő, ha az ügyféladatokhoz való adathozzáférésre van szükség egy támogatási eset megoldásához.

További információ: [Ügyféladatok biztonságos elérése az ügyfélszéfdel (előzetes verzió)](security-overview.md#securely-access-customer-data-with-customer-lockbox-preview).

### <a name="connect-to-your-data-using-azure-private-link"></a>Csatlakozás az adatokhoz az Azure Private Link használatával

Azure Private Link lehetővé teszi, hogy a Customer Insights a virtuális hálózat privát végpont keresztül csatlakozzon a Azure Data Lake Storage fiókjához. A nyilvános interneten nem elérhető tárfiókban lévő adatok esetében a Private Link engedélyezi a kapcsolatot a korlátozott hozzáférésű hálózattal.

További tájékoztatás: [A Private Link használata a Customer Insights](security-overview.md#set-up-an-azure-private-link) szolgáltatásban.

## <a name="may-2022-updates"></a>2022. májusi frissítések

A 2022. májusi frissítések új funkciókat, teljesítményfrissítéseket és hibajavításokat tartalmaznak.

### <a name="updated-data-unification-experience"></a>Frissített adategyesítési élmény

 Az adategyesítés lehetővé teszi az egyszer már elkülönülő adatforrások egyesítését egyetlen törzsadatkészletben, amely egységes nézetet biztosít az adatokról. Az adatok egyesíthetők egyetlen entitáson vagy több entitáson. [Először válassza ki az entitásokat és a forrásmezőket](map-entities.md), távolítsa el az ismétlődő rekordokat [, adja meg az egyeztetési feltételek](remove-duplicates.md) szabályait, és határozza meg, [hogy mely](match-entities.md) mezőket vegye fel az [egyesített vevői profilokba](merge-entities.md).

További információ: [Adategyesítés áttekintése](data-unification.md).

### <a name="refreshed-home-page-in-customer-insights"></a>Frissített kezdőlap a Customer Insights szolgáltatásban

**A Home** végigvezeti a legfontosabb funkciók konfigurációs folyamatán, és áttekintést nyújt a szegmensekről, mértékekről és bővítési adatokról. Frissítettük a felhasználói élményt, hogy egy pillantással relevánsabb információkat nyújtsunk.

További tájékoztatás: [A Customer Insights felfedezése](home.md).

### <a name="track-usage-of-a-segment"></a>Szegmens használatának nyomon követése

Mostantól [nyomon követheti egy szegmens](segments.md#track-usage-of-a-segment) használatát az alkalmazásokban, amelyek a Dataverse Customer Insights szolgáltatáshoz kapcsolódó szervezeten alapulnak. A Dynamics 365 Marketing [ügyfélútjain használt Customer Insights-szegmensek esetében](/dynamics365/marketing/real-time-marketing-ci-profile) a rendszer tájékoztatja Önt az adott szegmens használatáról.

### <a name="export-to-criteo"></a>Exportálás a Criteo-ba

A Criteo egy online platform, amely segít a felhasználóknak a digitális hirdetések kezelésében. Mostantól exportálhatja az egységes ügyfélprofilok szegmenseit kampányok létrehozásához, e-mailes marketing biztosításához és adott ügyfélcsoportok használatához a Criteo segítségével.

További információ: [Szegmensek exportálása a Criteo nyelvbe (előzetes verzió)](export-criteo.md).

### <a name="refined-documentation-structure-for-environment-creation"></a>Kifinomult dokumentációs struktúra a környezet létrehozásához

Újra áttekintettük a Customer Insights környezetek létrehozásával és kezelésével kapcsolatos súgódokumentumokat. A cikkek mostantól a tartalomjegyzék Környezetek csomópontja alatt vannak csoportosítva. Az átstrukturált cikkek további útmutatást nyújtanak a környezetek beállításának különböző módjaihoz, és világosabb struktúrával rendelkeznek. Ha megosztanád a visszajelzésedet, tudasd velünk a súgócikkek végén található vezérlőkön keresztül.

További információ: [How to: Create a new environment (Útmutató: Új környezet](create-environment.md) létrehozása).

## <a name="april-2022-updates"></a>2022. áprilisi frissítések

A 2022. áprilisi frissítések új funkciókat, teljesítményfrissítéseket és hibajavításokat tartalmaznak.

### <a name="dun--bradstreet-enrichment-preview"></a>Dun & Bradstreet dúsítás (előzetes verzió)

A Dun & Bradstreet kereskedelmi adatokat, elemzéseket és betekintést nyújt a vállalkozások számára. Lehetővé teszi, hogy az ügyfelek az egyesített ügyfélprofilokkal bővítsék az adataikat. A bővítések olyan attribútumokat tartalmaznak, mint a DUNS-szám, a vállalat mérete, helye, iparága stb.

További információ: [Vállalati profilok gazdagítása a Dun & Bradstreet (előzetes verzió)](enrichment-dnb.md) segítségével.

### <a name="define-the-measure-type-when-creating-a-new-measure"></a>Az intézkedés típusának meghatározása új mérték létrehozásakor

Mostantól különbséget tehetsz az egyes profilokra vonatkozó mértékek és a teljes vállalkozásra kiterjedő mértékek között. Míg az üzleti mértékek a Customer Insights kezdőlapján jelennek meg, az ügyfélmértékek a részletes ügyfélnézeteken jelennek meg.

További tájékoztatás: [A mértékszerkesztő használata a mértékek nulláról](measure-builder.md) történő létrehozásához.

### <a name="consolidation-of-customer-insights-documentation"></a>A Customer Insights dokumentációjának összevonása

Újra áttekintettük a dokumentációs cikkeinket, és eltávolítottuk az elköteleződési elemzések és a célközönség elemzési képességek említését. A továbbiakban következetesen a Customer Insights terméknévre fogunk hivatkozni, amikor az alkalmazás alapvető funkcióiról írunk. Ez a változás a tartalomjegyzék, az URL-struktúra és a fájl elérési útjának jelentős átstrukturálásához is vezet a mögöttes dokumentációs adattárban. Az összes könyvjelző vagy meglévő link továbbra is működik, és átirányít a frissített URL-ekre.

Ha szeretnéd tudatni velünk, hogyan érzékeled a változást, vagy észre akarsz venni valamit, ami nem a várt módon működik, küldj [visszajelzést erre az oldalra](https://github.com/MicrosoftDocs/customer-insights/issues/new?title=&body=%0A%0A%5BEnter%20feedback%20here%5D%0A%0A%0A---%0A%23%23%23%23%20Document%20Details%0A%0A%E2%9A%A0%20*Do%20not%20edit%20this%20section.%20It%20is%20required%20for%20docs.microsoft.com%20%E2%9E%9F%20GitHub%20issue%20linking.*%0A%0A*%20ID%3A%20d323ba46-f96e-1972-bc52-9b88f7d9cdfa%0A*%20Version%20Independent%20ID%3A%20d323ba46-f96e-1972-bc52-9b88f7d9cdfa%0A*%20Content%3A%20%5BNew%20and%20upcoming%20features%20-%20Dynamics%20365%20Customer%20Insights%5D(https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fdynamics365%2Fcustomer-insights%2Fwhats-new-customer-insights)%0A*%20Content%20Source%3A%20%5Bci-docs%2Fwhats-new-customer-insights.md%5D(https%3A%2F%2Fgithub.com%2FMicrosoftDocs%2Fcustomer-insights%2Fblob%2Fmain%2Fci-docs%2Fwhats-new-customer-insights.md)%0A*%20Service%3A%20**customer-insights**%0A*%20Sub-service%3A%20**audience-insights**%0A*%20GitHub%20Login%3A%20%40m-hartmann%0A*%20Microsoft%20Alias%3A%20**mhart**).

## <a name="march-2022-updates"></a>2022 márciusi frissítések

A 2022. márciusi frissítések új funkciókat, teljesítményfrissítéseket és hibajavításokat tartalmaznak.

### <a name="liveramp-abilitec-enrichment-preview"></a>LiveRamp AbiliTec-gazdagítás (előzetes verzió)

A LiveRamp biztosítja az identitásfeloldást és az ügyféladatok összevonását. Az ügyféladatokban szereplő személyes azonosítókat leképezheti az AbiliTec identitásgráfra, és AbiliTec-azonosítókat kaphat. Ezután ezeket az azonosítókat felhasználhatja az ügyféladatok jobb egységesítéséhez.

További információ: [Ügyfélprofilok bővítése a LiveRamp (előzetes verzió)](enrichment-liveramp.md) identitásadataival.

### <a name="organize-segments-and-measures-with-tags-and-filters"></a>Szegmensek és mértékek rendszerezése címkékkel és szűrőkkel

Ha a szervezet sok szegmenst vagy intézkedést tart fenn, a megfelelő megtalálása néha kihívást jelenthet. Ez az új funkció lehetővé teszi a listák címkék és oszlopok használatával történő rendszerezését. Segít az adatok gyors és egyszerű megtalálásában és a nézetek testreszabásában.

További információ: [Címkék és oszlopok](work-with-tags-columns.md) használata.

### <a name="enable-data-sharing-with-dataverse-when-using-your-own-storage-account"></a>Adatmegosztás Dataverse engedélyezése saját tárfiók használata esetén

Ha a környezet a Customer Insights-adatok tárolására szolgál Azure Data Lake Storage, az adatmegosztáshoz Microsoft Dataverse további konfigurációra van szükség.
Korábban csak akkor engedélyezte az adatmegosztást Dataverse, ha az adatait a felügyelt data lake-ben tárolták.

További információ: [Adatmegosztás Dataverse engedélyezése a sajátból Azure Data Lake Storage (előzetes verzió)](customer-insights-dataverse.md#enable-data-sharing-with-dataverse-from-your-own-azure-data-lake-storage-preview).

### <a name="new-export-destinations-iterable-and-braze"></a>Új exportálási célok: Iterálható és Braze

Folyamatosan bővítjük az exportcélpontok ökoszisztémáját új kapcsolatokkal. Mostantól exportálhat szegmenseket az Iterable és a Braze alkalmazásba az aktiválási szolgáltatások használatához.

További információ: Szegmensek exportálása iterálhatóba (előzetes verzió) [és](export-iterable.md) Szegmensek [exportálása Braze-be (előzetes verzió).](export-braze.md)

### <a name="improvements-to-marketo-and-google-ads-export"></a>A Marketo és a Google Ads exportálásának fejlesztései

A csatlakoztatott szolgáltatások API-jainak módosítása az összekötők megbízható és zökkenőmentes futtatását eredményezi. Kiadtunk néhány frissítést a Marketo és a Google Ads szolgáltatásaiba irányuló exporttal kapcsolatban:

- Google Ads: A Google Ads exportálási összekötő új verziója leegyszerűsíti a hitelesítési élményt, és mostantól lehetővé teszi új Google Ads-közönségek automatikus létrehozását. 
- Marketo: A Marketo exportálási összekötő új verziója támogatja a Marketo-azonosítót, lehetővé téve az adatok duplikálásának elkerülését, a meglévő rekordok frissítését és új rekordok létrehozását a Marketo-ban. 

## <a name="february-2022-updates"></a>2022. februári frissítések

A 2022. februári frissítések új funkciókat, teljesítményfrissítéseket és hibajavításokat tartalmaznak.

### <a name="general-availability-for-prediction-models"></a>Általánosan elérhető előrejelzés modellekhez

A használatra kész előrejelzés modellek, beleértve az előfizetés-lemorzsolódást, a **tranzakciós lemorzsolódást** **és** az ügyfél élettartamra vetített értékét (CLV), **általánosan elérhetővé válnak a Customer Insights** részeként. 

További információ: [Előrejelzések áttekintése](predictions-overview.md).

### <a name="new-data-source-integration-with-azure-synapse-analytics-preview"></a>Új adatforrás: Integráció Azure Synapse Analytics (előzetes verzió)

Azure Synapse Analytics egy nagyvállalati elemzési szolgáltatás, amely felgyorsítja az adattárházak és big data rendszerek elemzéséhez szükséges időt.

A már használt Azure Synapse Analytics szervezetek betölthetik ezeket az adatokat a Customer Insights szolgáltatásba. 

További információ: [Csatlakozás adatforrás Azure Synapse (előzetes verzió)](connect-synapse.md).

### <a name="liveramp-enrichment-preview"></a>LiveRamp-bővítés (előzetes verzió)

A LiveRamp biztosítja az identitásfeloldást és az ügyféladatok összevonását. Az ügyféladatokban szereplő személyes azonosítókat leképezheti az AbiliTec identitásgráfra, és AbiliTec-azonosítókat kaphat. Ezután ezeket az azonosítókat felhasználhatja az ügyféladatok jobb egységesítéséhez.

További információ: [Ügyfélprofilok bővítése a LiveRamp (előzetes verzió)](enrichment-liveramp.md) identitásadataival.

### <a name="enrichment-for-data-sources-preview"></a>Adatforrások gazdagítása (előzetes verzió)

Az adatok egyesítése előtt olyan forrásokból származó adatok használatával bővítheti az ügyféladatokat, mint a Microsoft. Adatforrás gazdagítás segít az adatok jobb teljességének és minőségének elérésében, ami az adatok egységesítése után jobb eredményeket érhet el.

További információ: [Adatforrások gazdagítása (előzetes verzió)](data-sources-enrichment.md).

### <a name="change-owner-of-environment"></a>A környezet tulajdonosának megváltoztatása

Bár több felhasználó is rendelkezhet rendszergazdai engedélyekkel a Customer Insights alkalmazásban, csak egy felhasználó tulajdonosa egy környezetnek. A továbbfejlesztett felhasználói élmény lehetővé teszi a környezet tulajdonosainak módosítását és a tulajdonjog igénylését, ha egy korábbi tulajdonos elhagyta a szervezetet. 

További információ: [Környezet](manage-environments.md#change-the-owner-of-an-environment) tulajdonosának módosítása.

### <a name="data-preparation-process-lists-corruption-reason-for-corrupted-records"></a>Az adatelőkészítési folyamat felsorolja a sérült rekordok sérülésének okát

Az adatelőkészítés mostantól megjeleníti a sérült adatokkal rendelkező összes mező sérülésének okát. Az információkat az egyéni nyilvántartás szintjén adják meg a könnyű azonosítás érdekében.

További információ: [Sérült adatforrások](data-sources.md#corrupt-data-sources).

### <a name="end-of-preview-for-reporting-features-in-the-engagement-insights-capability"></a>Az aktivitáselemzési képesség jelentéskészítési funkcióinak előnézetének vége

Az Dynamics 365 Customer Insights elköteleződési elemzési képesség előnézete 2022. február 15-én ért véget.  
Ez a változás azt jelenti, hogy a Customer Insights próbaverziója már nem tartalmazza a csatornák létrehozásának lehetőségét, sem más jelentéskészítési funkciókat.

Meghívjuk Önt, hogy vizsgálja meg és értékelje ki a Customer Insights [, a Microsoft ügyféladat-platformjának (CDP) számos egyéb funkcióját](https://dynamics.microsoft.com/ai/customer-insights/).    
 
Egy átmeneti időszakban az előzetes verzió meglévő résztvevői továbbra is hozzáférhetnek néhány előzetes verziójú képességhez és funkcióhoz:

- Kód lekérése webhely vagy mobilalkalmazás tagolásához 
- Események és eseménytulajdonságok megtekintése 
- Egységes profilok továbbfejlesztése betöltött és finomított eseményekkel, hogy kihasználhassa az ügyféladatok teljes értékét
  
Az átmeneti időszak alatt a rögzített eseményeket a rendszer továbbra is streameli a csatlakoztatott Data Lake. Ha ez a funkció ki van kapcsolva, az adatmegosztás leáll, és a rendszer nem küld új eseményeket a csatlakoztatott tárolóba.
Forduljon közvetlenül a Microsoft-fiók csapatához, ha kérdése van a képesség-előnézet végével kapcsolatban. A fiókkezelő csapat naprakészen tartja Önt a közelgő bevezetésekkel kapcsolatban. 

## <a name="january-2022-updates"></a>2022. januári frissítések

A 2022. januári frissítések új funkciókat, teljesítményfrissítéseket és hibajavításokat tartalmaznak.

### <a name="sentiment-analysis-of-your-customers-feedback"></a>Az ügyfél visszajelzésének hangulatelemzése

A Customer Insights egy új, mesterséges intelligencián alapuló funkciót biztosít az ügyfelek hangulatának szintetizálásához és az egyes üzleti szempontok azonosításához, mint a célzott fejlesztések lehetőségeihez. Az ügyfelek írásbeli visszajelzéseinek elemzésével pontos betekintést nyerhet alacsony költségek mellett. A természetes nyelvi feldolgozási (NLP) modelleken alapuló hangulatelemzés két származtatott elemzést hoz létre minden ügyfél-azonosítóhoz. A hangulati pontszám (–5 és 5 között) és az alkalmazandó üzleti szempontok listája. 

További információ: [Hangulat elemzése az ügyfelek visszajelzéseiben (előzetes verzió)](sentiment-analysis.md).


[!INCLUDE [footer-include](includes/footer-banner.md)]