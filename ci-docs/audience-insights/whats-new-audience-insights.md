---
title: Új és jövőbeni funkciók
description: Információ az új szolgáltatásokról, továbbfejlesztésekről és hibajavításokról.
ms.date: 03/02/2022
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
ms.reviewer: midevane
manager: shellyha
ms.openlocfilehash: 0e25ed4e4e25b130fda410d4ba1c78caded7f0f9
ms.sourcegitcommit: b7189b8621e66ee738e4164d4b3ce2af0def3f51
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/03/2022
ms.locfileid: "8088288"
---
# <a name="whats-new-in-the-audience-insights-capability-of-dynamics-365-customer-insights"></a>A célközönséggel kapcsolatos újdonságok a Dynamics 365 Customer Insights-ban.



Örömmel jelentjük be legújabb frissítéseinket! Ez a cikk összefoglalja a nyilvános előzetes funkciókat, általános elérhetőségű javításokat és a funkciófrissítéseket. A hosszú távú funkciótervekkel megtekintéséhez tekintse meg a [Dynamics 365 és Power Platform a kiadási terveket](/dynamics365/release-plans/).

A frissítéseket régiónként tesszük közzé. Így bizonyos régiók a mások előtt láthatják a funkciókat. Hacsak nincs másképpen meghatározva, nem kell semmilyen műveletet végrehajtania, és az alkalmazás automatikusan, leállás nélkül frissíthető.

> [!TIP]
> Funkciókérelmek és termékjavaslatok benyújtásához és szavazáshoz látogassa meg a [Dynamics 365 alkalmazás ötletek portálját](https://experience.dynamics.com/ideas/categories/?forum=79a8c474-4e35-e911-a971-000d3a4f3343&forumName=Dynamics%20365%20Customer%20Insights).


## <a name="january-2022-updates"></a>2022. januári frissítések

A 2022. januári frissítések új funkciókat, teljesítményfrissítéseket és hibajavításokat tartalmaznak.

### <a name="sentiment-analysis-of-your-customers-feedback"></a>Az ügyfél visszajelzéseinek hangulatelemzése

A Customer Insights egy új, AI-alapú funkciót kínál az ügyfelek hangulatának szintetizálásához és bizonyos üzleti szempontok azonosításához, mint a célzott fejlesztések lehetőségeihez. Az ügyfelek írásbeli visszajelzéseinek elemzésével pontos betekintést kaphat alacsony költséggel. A természetes nyelvi feldolgozás (NLP) modelljei által működtetett hangulatelemzés, amely minden ügyfélazonosítóhoz két származtatott betekintést hoz létre. A hangulat pontszám (-5-5) és az alkalmazandó üzleti szempontok listája. 

További információt a Hangulat elemzése az ügyfelek visszajelzéseiben (Előzetes verzió) című témakörben [talál](sentiment-analysis.md).


## <a name="december-2021-updates"></a>2021 decemberi frissítések

A 2021. decemberi frissítések új funkciókat, teljesítményfrissítéseket és hibajavításokat tartalmaznak.

### <a name="forward-customer-insights-logs-to-azure-monitor"></a>Ügyfélelemzési naplók továbbítása az Azure Monitorra

A Customer Insights közvetlen integrációt biztosít az Azure Monitorral. Ez a funkció magában foglalja a naplózási eseményeket és az operatív eseményeket. Az Azure Monitor erőforrásnaplói lehetővé teszik a naplók figyelése és elküldése az Azure Storageba, az Azure Log Analytics-be, vagy streamelheti őket az Azure Event Hubs.

További információt a Bejelentkezés az [Azure Monitorral (Előzetes verzió) című témakörben talál Dynamics 365 Customer Insights](diagnostics.md).

### <a name="enrich-customer-profiles-with-engagement-data"></a>Ügyfélprofilok gazdagítása elkötelezettségi adatokkal

Ahonnan származó Microsoft Office 365 adatok segítségével gazdagodhat az ügyfélfiók-profilokkal az alkalmazásokon keresztüli Office 365 elkötelezettségekkel kapcsolatos elemzésekkel. Az elkötelezettségi adatok e-mail és értekezleti tevékenységből állnak, amelyeket a fiók szintjén összesítünk. Például az üzleti fiókból származó e-mailek száma vagy a fiókkal való értekezletek száma. Az egyes felhasználókra vonatkozó adatok nincsenek megosztva. Ez a dúsítás a következő régiókban érhető el: Egyesült Királyság, Európa, Észak-Amerika.

További információt az Ügyfélprofilok gazdagítása elköteleződési adatokkal (Előzetes verzió) című témakörben [talál](enrichment-office.md).

### <a name="advanced-data-unification-features"></a>Speciális adategyesítési szolgáltatások

#### <a name="enable-conflict-resolution-policies-at-the-individual-attribute-level"></a>Ütközéskezelési házirendek engedélyezése egyéni attribútumszinten

Ha egy entitáson belül vevőrekordokat hoz ki, előfordulhat, hogy nem kell győztesként teljes rekordot választania. Most lehetővé tesszük, hogy egyesítse a különböző rekordok legjobb mezőit az egyes attribútumok szabályai alapján. Dönthet például úgy, hogy megtartja a legutóbbi e-mailt és a legteljesebb címet a különböző rekordokból. 

Mostantól külön egyesítési szabályokat határozhat meg az egyes attribútumokhoz, miközben egyetlen entitáson belül deduplikál és egyesíti a rekordokat. Korábban csak egyetlen egyesítési szabályt engedtünk ki (a reklenciás adatok teljessége alapján nyilvántartást vezet), és ezt a szabályt rekordszinten alkalmazták az összes attribútumra. Ez nem ideális, ha a megtartani kívánt adatok egy része megtalálható az A nyilvántartásban, és más jó adatok a B rekordban találhatók.

További információ lásd: [A deduplikáció meghatározása az egyezési entitásban](match-entities.md#define-deduplication-on-a-match-entity).

#### <a name="custom-rules-for-matching"></a>Egyéni szabályok az egyeztetéshez

Vannak olyan időszakok, amikor kivételt kell megadnia az általános szabályok alól ahhoz, hogy a REKORDOK NE egyezzenek meg. Ez akkor fordulhat elő, ha több személy elegendő információt oszt meg, hogy a rendszer egyetlen személyként illeszkedik hozzájuk. Például az azonos vezetéknév ikrek, ugyanabban a városban élnek, és megosztják a születési dátumot.

A kivételek biztosítják, hogy az egyesítési szabályokban kezelhető legyen a helytelen adategyesítés. Egy szabályhoz több kivételt is hozzáadhat.

További információt a Kivételek hozzáadása szabályhoz [című témakörben talál](match-entities.md#add-exceptions-to-a-rule).

#### <a name="provide-additional-conflict-resolution-policies-and-enable-grouping-of-attributes"></a>További ütközéskezelési házirendek biztosítása és attribútumok csoportosításának engedélyezése

Ez a funkció lehetővé teszi, hogy egy mezőcsoportot egyetlen egységként kezeljen. Ha például a rekordjaink a Cím1, a Cím2, a Város, az Állapot és a Zip mezőket tartalmazzák. Valószínűleg nem akarunk egyesülni egy másik rekord Address2-ben, azt gondolva, hogy ez teljesebbé tenné az adatainkat.

Mostantól kombinálhat kapcsolódó mezők egy csoportját, és egyetlen egyesítési szabályzatot alkalmazhat a csoportra. 

További információt a Mezők [csoportjának egyesítése című témakörben talál](merge-entities.md#combine-a-group-of-fields).


## <a name="november-2021-updates"></a>2021. novemberi frissítések

A 2021. novemberi frissítések új funkciókat, teljesítményfrissítéseket és hibajavításokat tartalmaznak.

### <a name="segment-membership-now-available-in-dataverse"></a>A szegmenstagság már elérhető a Dataverse

Az ügyfélprofilok szegmenstagsági adatai mostantól elérhetők Dataverse az ügyfélprofilokkal és elemzésekkel együtt. A Dynamics 365 műveletalkalmazások és modellvezérelt alkalmazások használhatják ezeket az adatokat, és megkereshetik a szegmenstagság részleteit egy adott ügyfél számára.

### <a name="activities-support-contact-level-details-for-business-accounts"></a>A tevékenységek támogatják az üzleti számlák kapcsolattartási szintű adatait

Mostantól konfigurálhatja, megjelenítheti és szűrheti az üzleti fiók tevékenységi ütemtervében lévő kapcsolattartók tevékenységeit, hogy jobban megértse, mely partnerpartnerek vettek részt az egyes tevékenységekben.

## <a name="october-2021-updates"></a>2021. októberi frissítések

A 2021. októberi frissítések új funkciókat, teljesítményfrissítéseket és hibajavításokat tartalmaznak.

### <a name="b-to-b"></a>B-B-hez

2021 októberétől az üzleti partnerekkel és a kapcsolódó kapcsolattartókkal dolgozhat a Customer Insights alkalmazásban. Korábban az alkalmazást többnyire az egyéni fogyasztókra szabták. Számos jellemzőterületet frissítettek, hogy támogassák a B-B forgatókönyveket az új környezeti típuson felül. A támogatott B-to-B funkciók áttekintéséhez olvassa el a Üzleti fiókok célközönség elemzésekben című [témakört](work-with-business-accounts.md).

A következő szakaszok kiemelik azokat a kulcsfontosságú területeket, amelyeket az üzleti számlák és az egyéni fogyasztók támogatására alakítottak ki.

#### <a name="export-segments-based-on-business-accounts"></a>Szegmensek exportálása üzleti számlák alapján

A célközönség elemzésekben szereplő összes szegmensexport elérhető az üzleti számlákkal összefüggésben. A legtöbb szegmensexporthoz további konfigurációs és [kapcsolattartási adatokra van szükség, amelyek az alapul szolgáló szegmensekben vannak előrevetített](segment-builder.md#create-a-new-segment) adatok, hogy érvényesek legyenek az üzleti számlákra. További információt a Szegmensek [exportálása című témakörben talál](export-destinations.md#export-segments).

#### <a name="use-the-linkedin-ads-export-with-business-accounts"></a>A LinkedIn Ads exportálásának használata üzleti fiókokkal

A LinkedIn Ads exportálása mostantól elérhető a kapcsolattartók és a vállalati célzás számára az üzleti fiókok összefüggésében. Amikor a vállalati célzást választja a LinkedIn-exportálás elsődleges fókuszaként, exportálhat üzleti számlákra épülő szegmenseket anélkül, hogy ügyféladatokat kellene kivetítene. További információért lépjen a LinkedIn Ads exportálásával kapcsolatos [dokumentumokban, valamint a kapcsolatfelvételi célzás](export-linkedin-ads.md) és [a vállalati célzás közötti](https://business.linkedin.com/marketing-solutions/ad-targeting/contact-targeting) különbségben [.](https://business.linkedin.com/marketing-solutions/ad-targeting/account-targeting) 

#### <a name="create-measures-based-on-business-accounts-and-their-hierarchy"></a>Intézkedések létrehozása az üzleti számlák és hierarchiájuk alapján

A mértékszerkesztő lehetővé teszi, hogy mértékeket hozzon létre az üzleti számlák körül, és opcionálisan használja a hierarchiaadatokat. A hierarchiaadatok a mértékszámítás összesítésére szolgálnak egy fiókban és az összes kapcsolódó alfiókban. Létrehozhat például olyan mértékeket, mint a hierarchiájuk által azonosított üzleti számlák minden egyes csoportjának teljes bevétele. További információ: [Mérőszámok meghatározása és kezelése](measures.md).

#### <a name="create-segments-based-on-business-accounts-and-their-hierarchy"></a>Szegmensek létrehozása az üzleti számlák és hierarchiájuk alapján

A szegmensszerkesztő lehetővé teszi az üzleti számlák olyan szegmenseinek létrehozását, amelyek opcionálisan tartalmazzák a szegmens egyes fiókjaihoz szükséges kapcsolattartási adatokat. Ha beállította a fiókhierarchiát, a szegmens létrehozásához használhatja a fiókhierarchia adatait. További információt a Új szegmens [létrehozása című témakörben talál](segment-builder.md#create-a-new-segment).

#### <a name="retain-your-business-accounts-with-deep-insights-to-their-churn-tendency"></a>Tartsa meg üzleti fiókjait mély betekintéssel a lemorzsolódási tendenciájukba

Az ügyfél lemorzsolódása előrejelzés modell mostantól az üzleti számlákat is támogatja. Nemcsak egy fiók, hanem egy fiók és egy tőled vásárolt termék- vagy szolgáltatáskategória kombinációjának kockázatát is értékelheti. Ez a kiegészítés segít megérteni, hogy egy fiók nagyobb valószínűséggel hagyja-e abba a vásárlást tőled általában, vagy csak egy bizonyos áru- vagy szolgáltatáskategóriára. Az AI-modell további használata érdekében felsorolja azokat az okokat is, amelyek miatt egy fiók valószínűleg lemorzsolódik. További információt a Tranzakció lemorzsolódás előrejelzés (előzetes verzió) című témakörben [talál](predict-transactional-churn.md).

#### <a name="see-contacts-of-a-business-account-in-customer-view"></a>Üzleti fiók névjegyeinek megtekintése Vevő nézetben

Ha az üzleti fiókok a kapcsolódó fiókokhoz vannak leképezve, a Customer Insights alkalmazás megjeleníti ezeket a kapcsolódó névjegyeket az ügyféladatok nézet részeként. További információ: [Ügyfélprofilok](customer-profiles.md).


## <a name="september-2021-updates"></a>2021. szeptemberi frissítések

A 2021. szeptemberi frissítések új szolgáltatásokat, teljesítményfrissítéseket és hibajavításokat tartalmaznak.

### <a name="activities"></a>Tevékenységek

- **Tevékenység idővonalának továbbfejlesztései** Kiterjesztettük a tevékenység ütemezésére vonatkozó szűrőket az ügyfélprofilok esetében. Az új szűrőtálat emellett tevékenységtípus és dátum szerint is szűrheti. A dátumok szűrhetők más feltételekkel. További információkért lásd a [Tevékenység ütemezésének megtekintése az ügyfélprofilon](activities.md#view-activity-timelines-on-customer-profiles) részt.

### <a name="relationships"></a>Kapcsolatok

- **Több ugrásos kapcsolattámogatás** A tevékenységek konfigurálásakor és az entitások közötti kapcsolatok definiálásakor több ugrásos kapcsolatokat használjon. A többugrásos kapcsolatok köztes entitás használatával két entitást kapcsolhat össze. A tevékenységek konfigurálásakor több ugrásból álló kapcsolat segítségével a tevékenységentitást egy köztes entitáshoz, majd egy ügyfélentitáshoz kapcsolhatja. A több ugrásból álló kapcsolatok több útvonalból álló kapcsolatok. További információt a [Több ugrásos kapcsolat](relationships.md#multi-hop-relationship) részben talál.

- **Több útvonalból álló kapcsolattámogatás** A tevékenységek konfigurálásakor és az entitások közötti kapcsolatok definiálásakor több útvonalból álló kapcsolatokat használjon. A több elérési útvonalból álló kapcsolatok a forrásentitást egynél több entitáshoz kapcsolják. A tevékenységek konfigurálásakor több elérési útvonalból álló kapcsolat segítségével a tevékenységentitást több mint egy ügyfélentitáshoz kapcsolhatja. A több elérési útvonalból álló kapcsolatok több ugrásból álló kapcsolatok. További információt a [Több elérési útvonalból álló kapcsolat](relationships.md#multi-path-relationship) részben talál.

## <a name="august-2021-updates"></a>2021. augusztusi frissítések

A 2021. júliusi és augusztusi frissítések egy új funkciót, teljesítményfrissítéseket és hibajavításokat tartalmaznak.

### <a name="extensibility"></a>Bővíthetőség

- **Szegmenseket Klaviyoba** Az exportálási célpontokat kiterjesztettük a [Klaviyo](export-klaviyo.md) szolgáltatásra is. A szegmensek exportálásával kampányokat hozhat létre, e-mail-marketing szolgáltatást biztosíthat és előnyt kovácsolhat az ügyfelek meghatározott csoportjából a Klaviyo szolgáltatással. 


## <a name="june-2021-updates"></a>2021. júniusi frissítések

A 2021. júniusi frissítések számos szolgáltatást, teljesítménnyel kapcsolatos frissítést és hibajavítást tartalmaznak.

### <a name="data-ingestion"></a>Adatok betöltése

- **Továbbfejlesztett adategyesítési folyamat frissítései** Mostantól részletesebb, továbbfejlesztett dinamikus állapotfrissítéseket lehet megtekinteni az [adategyesítési folyamat](data-unification.md) lépéseinél. A funkció segítségével nyomon követheti a részletes folyamatot, így megértheti a folyamatot, és cselekedhet, ha valamelyik lépés figyelmet igényel.

### <a name="extensibility"></a>Bővíthetőség

- **Szegmensek és egyéb adatok exportálása a Salesforce Marketing Cloudba** Kiterjesztettük az exportálási célokat a [Salesforce Marketing Cloud](export-salesforce.md) tárhelyre is. Mostantól exportálhat a szegmenseket és más típusú adatokat a Salesforce Marketing Cloud szolgáltatásba márkanévvel ellátott SFTP-exportálással. Az adatok importálása teljesen automatizálni lehet a Salesforce-ban, és hatékonyabb marketingkampányok létrehozásához használhatók fel.  
 
- **Szegmenseket ActiveCampaign-be** Az exportálási célpontokat kiterjesztettük az [Aktív Campaignre](export-active-campaign.md) is. A szegmensek exportálásával kampányokat hozhat létre, e-mail-marketing szolgáltatást biztosíthat és előnyt kovácsolhat az ügyfelek meghatározott csoportjából az ActiveCampaign szolgáltatással.
 
- **Szegmenseket Sendinblue-ba** Az exportálási célpontokat kiterjesztettük a [Sendinblue](export-sendinblue.md) szolgáltatásra is. A szegmensek exportálásával kampányokat hozhat létre, e-mail-marketing szolgáltatást biztosíthat és előnyt kovácsolhat az ügyfelek meghatározott csoportjából az Sendinblue szolgáltatással.
 
### <a name="ux-updates"></a>UK-frissítések 

- **Új és továbbfejlesztett Ügyfelek oldal és profilrészletek oldal** Átalakítottuk az Ügyfelek oldalt és a profilrészletek oldalakat a jobb felhasználói élmény és jobb teljesítmény érdekében. A módosítások segítségével megtekintheti, rendezheti, keresheti és szűrheti az ügyfeleket. A szűrők mostantól megjelennek az URL-ben, és így zökkenőmentesen megoszthatja a keresési eredményeket más felhasználókkal. A keresési eredmények szegmensként is menthetők.    
  Az ügyfélprofilok részletes lapja mostantól különféle alszakaszokba (például demográfiai adatok, azonosítók egyéb profilattribútumok) vannak rendezve olvashatóság javítása érdekében. A profil részletei oldalon található egyéb szakaszok mostantól interaktívak. A tevékenységek szakasz például most már lehetővé teszi a szűrést és a rendezést.


## <a name="may-2021-updates"></a>2021. májusi frissítések

A 2021 májusi frissítések számos funkciót, teljesítményfrissítést és hibajavítást tartalmaznak.

### <a name="data-ingestion"></a>Adatok betöltése

- **Metaadatok vagy entitásdefiníció megtekintése vagy módosítása az Azure Data Lake Storage**-tárhely adatainak csatolása esetén.Mostantól megtekintheti és szerkesztheti a metaadatokat vagy az entitásdefiníciókat célközönség elemzésekben, amikor adatokat csatol egy Common Data Model-mappából az Azure Data Lake Storage-tárhelyéről. Ez a képesség valós idejű visszajelzést, modellérvényesítést és hibaellenőrzést biztosít. Lehetővé teszi a model.json és a manifest.json egyszerű szerkesztését.

### <a name="extensibility"></a>Bővíthetőség

- **Továbbfejlesztett szegmensexport, egyéni ütemezés és duplikáció:** Mostantól egy listában [egy adott szegmensének összes exportja látható](export-destinations.md#view-exports-and-export-details). Ez az új nézet segít kezelni egy adott szegmens használatát, illetve egy meglévő adaptálását vagy új exportálások létrehozását.    
  [Egyéni frissítési ütemezéseket](export-destinations.md#schedule-and-run-exports) az egyes exportálásokhoz és egyszerre több exportáláshoz is definiálhat. Eddig minden exportálás minden rendszerfrissítéssel futtatva lett.    
  Ahelyett, hogy új exportot hozna létre a semmiből, elkezdheti egy meglévő alapján, hogy időt takarítson meg.

- **Szegmensek exportálása a Microsoft Advertising-szolgáltatásba** Kiterjesztettük az exportálási célhelyeket, amelyek immár a Microsoft Advertising-szolgáltatásra is kiterjednek. Hozzon létre ügyfélegyezési célközönségeket a Microsoft Advertising szolgáltatásban az egyesített ügyfélprofilok adataival, és használja a célközönségeket a hirdetési kampányokhoz. További információ: [Szegmensek exportálása a Microsoft Advertising-szolgáltatásba](export-microsoft-advertising.md).

- **Szegmensek exportálása LinkedIn Ads-szolgáltatásba** Kiterjesztettük exportálási célokat a LinkedIn Ads-szolgáltatásra is, és lehetővé tesszük a Kapcsolattartókra célzást, valamint a Vállalatokra célzást is a LinkedIn-en keresztül az egyesített ügyfélprofil-adatok exportálásával. További információ: [Szegmensek exportálása a LinkedIn Ads-szolgáltatásba](export-linkedin-ads.md).


- **Szegmensek exportálása az Omnisend-szolgáltatásba** Kiterjesztettük az exportálási célhelyeket, amelyek most már az Ominsend szolgáltatásra is kiterjednek. A célközönésg információk szolgáltatásban létrehozott szegmensek felhasználásával kampányokat hozhat létre, e-mail-marketing szolgáltatást biztosíthat és előnyt kovácsolhat az ügyfelek meghatározott csoportjából az Omnisend szolgáltatással. További tájékoztatás a [Szegmensek exportálása az Omnisend szolgáltatásba](export-omnisend.md) című témakörben olvasható

### <a name="predictions"></a>Előrejelzések

- **Bemeneti adatok használhatósági jelentése** A bemeneti adatok használhatósági jelentése egységes képet ad azokról a hibákról és figyelmeztetésekről, amelyeket a gyári előrejelzések generálhatnak. Ajánlásokat is ad a modell teljesítményének javítására.    
  A jelentés a modell betanítási folyamatának befejezése után érhető el. Minden modellhez külön-külön van létrehozva, függetlenül attól, hogy sikeresen befejeződött-e vagy sem.
  Jelenleg ez a funkció csak a Tranzakciólemorzsolódási modellhez érhető el. További információ: [Bemeneti adatok használhatósági jelentése](manage-predictions.md#input-data-usability-report).

### <a name="relationships"></a>Kapcsolatok

- **Kapcsolat vizualizáló** A kapcsolat vizualizáló nézet lehetővé teszi az entitások és azok számossága közötti összes meglévő kapcsolat megtekintését. Kapcsolatok most csoportokba vannak rendezve: felhasználó által létrehozott, rendszer és örökölt kapcsolatok. A nézetet képként is exportálhatja. További tudnivalók: [Kapcsolatok megtekintése](relationships.md#view-relationships). 

## <a name="april-2021-updates"></a>2021. áprilisi frissítések

A 2021. áprilisi frissítések számos funkciót, teljesítményfrissítést és hibajavítást tartalmaznak.

### <a name="data-unification"></a>Adategyesítés
 
- **Továbbfejlesztett egyesítési környezet az adategyesítéshez**    
  
   Mostantól az adategyesítési folyamat egyesítési konfigurációjában továbbfejlesztett felhasználói élményt kínálunk. A változások közé tartozik az egyesített mezők intuitív sorrendbe rendezése, valamint a kombinált és az egyedülálló mezők részletes statisztikai adatai.

- **Az entitások újrarendezése és az összes forrásrekordot Ügyfél entitásba történő konfigurálása**  
      
   Mostantól újrarendezheti és eltávolíthatja az adategyesítési folyamat összevonási tervében lévő entitásokat. A megoldás rugalmas lehetőséget kínál az egyeztetési folyamatban szereplő entitások üzleti igények szerinti átrendezésére. Emellett lehetséges, hogy az összes nem egyeztetett bejegyzés szerepeljen a végső *Ügyfél* entitásban, ami lehetővé teszi számukra az ügyfélprofil adathalmazának definiálását.

### <a name="enrichments"></a>Bővítések

 - **Új bővítés: Továbbfejlesztett címek**    
  
   Izgatottan mutatjuk be az új bővítést, amely az ügyféladatokban szereplő címeket fejleszti tovább. Az adatokban szereplő címek strukturálatlanok, hiányosak vagy helytelenek lehetnek. Ez a funkció a Microsoft modelljeivel normalizálja és bővíti a címeket a Common Data Model formátumba, hogy pontosabbak és részletesebbek legyenek.
 
   További információ: [Az ügyfélprofilok bővítése továbbfejlesztett címekkel](enrichment-enhanced-addresses.md).

- **Interaktív konfigurációs környezet a bővítéshez**    
  
   A bővítés konfigurálási környezetetét egyszerű, interaktív környezetté alakítottuk. Most már egyértelmű, lépésekre bontott folyamat áll rendelkezésre a bővítések létrehozásához és szerkesztéséhez.
 
   Ezenkívül különválasztottuk a külső gyártótól származó bővítések kapcsolatainak konfigurációját, hogy ugyanazt a kapcsolatot több bővítés is használhassa. Csak rendszergazdák konfigurálhatják az új kapcsolatokat, de a létrehozott kapcsolatok elérhetők mind a rendszergazdák, mind a munkatársak számára.    

   További tudnivalókért lásd: [Kapcsolatok áttekintése](connections.md).

- **Azonos típusú többszörös bővítések**    
  
   A felhasználók most már létrehozhatnak és kezelhetnek több, ugyanolyan bővítési típusba tartozó bővítést is. Létrehozhat például két külön címbővítést, hogy két különböző ügyfélszegmenst bővítsen. A korlátok arra vonatkoznak, hogy hány ugyanolyan típusú bővítést lehet létrehozni, és a bővítés típusától függően eltérnek.
  
   További információkért lásd: [Az ügyfelek profiljainak bővítése](enrichment-hub.md).

## <a name="march-2021-updates"></a>2021 márciusi frissítések

A 2021 márciusi frissítések számos funkciót, teljesítményfrissítést és hibajavítást tartalmaznak.

### <a name="activities"></a>Tevékenységek

- **Tevékenység varázsló és szemantikus típusok**

   Továbbfejlesztettük és frissítettük a tevékenységleképezési szolgáltatást, hogy útmutatóként szolgáljon a tevékenységleképezések létrehozáshoz, és egyszerűbbé tegye azt. Ebben az új élményben a felhasználók interaktív élményben részesülnek, amely segíthet a folyamat egyes lépéseinek elvégzésében. A tevékenységleképezési lépésben a felhasználó nemcsak a különböző tevékenységtípusokból választhat, hanem kiválaszthatja, hogy szemnatikusan szeretné-e leképezni az adatokat az *Előfizetés* és/vagy *SalesOrderLine* ipraági standard sémákhoz, amelyeket a lefelé irányuló folyasztáshoz is lehet használni.   

   További információ: [Ügyféltevékenységek](activities.md).

### <a name="data-ingestion"></a>Adatok betöltése

- **Csatlakozzon helyszíni adatforrásokhoz Power Platform adatfolyamok és átjárók használatával** Örömmel jelentjük be a Customer Insightshoz társított Power Platform vagy Dataverse környezetben található, átjárókat használó Power Platform adatfolyamok és helyszíni összekapcsolhatóságok előzetes verzióját. A Customer Insights környezetben létrehozott, kapcsolt Dataverse környezettel rendelkező új adatforrások alapértelmezés szerint Power Platform adatforrásokká fognak válni, helyszíni összekapcsolhatósággal, valamint az összekapcsolók és átalakítási lehetőségek gazdag készletével.

### <a name="extensibility"></a>Bővíthetőség

- **Kapcsolatokba és exportálásokba rendezett exportálások** Az **Exportálás céljai** lap nevét megváltoztattuk **Kapcsolatok** lapra, és egy külön oldalt adtunk hozzá az **Exportálások** lehetőségekhez. A frissítés részeként a meglévő exportálásokat kapcsolatpárokba állítjuk össze, illetve egy kapcsolatot használó exportálásba. A rendszergazdák most már jobban átláthatják a kimenő adatokat a **Kapcsolatok** oldalon. Minden felhasználói szerepkörnek van hozzáférése az **Exportálások** laphoz, de csak a rendszergazdák engedélyezhetik a munkatársaknak, hogy megosztott kapcsolatokkal szerkesszék az adott exportálásokat.     
  További tudnivalókhoz lásd: [Kapcsolatok áttekintése](connections.md) és [Exportálások áttekintése](export-destinations.md).

- **Szegmensek exportálása a Campaign Monitorba** Kiterjesztettük az exportálási célhelyeket, amelyek most már megtalálhatók a Campaign Monitorben is. Mostantól exportálhatja a szegmenseket a Customer Insightsból a Campaign Monitor listáiba, és ezeket használhatja a marketingkampányok kiindulási alapértékeként.    
   További tájékoztatás az [Exportálás a Campaign Monitorba](export-campaign-monitor.md) című témakörben olvasható.

- **Szegmensek exportálása az Constant Contactba** Kiterjesztettük az exportálási célhelyeket, amelyek most már megtalálhatók az Constant Contactban is. Mostantól exportálhatja a szegmenseket a Customer Insightsból az Constant Contact listáiba, és ezeket használhatja a marketingkampányok kiindulási alapértékeként.   
   További tájékoztatás az [Exportálás az Constant Contactba](export-constant-contact.md) című témakörben olvasható.

- **Szegmensek exportálása a RollWorksbe** Kiterjesztettük az exportálási célhelyeket, amelyek most már megtalálhatók a RollWorksben is. Most már exportálhat szegmenseket a Customer Insightsból a RollWorks-közönségekbe, és ezeket használhatja a „B-to-B” hirdetések kiindulási értékeként.    
   További tájékoztatás az [Adatok exportálása RollWorksbe ](export-rollworks.md)című témakörben olvasható.

- **Szegmensek exportálása a Snapchatbe** Kiterjesztettük az exportálási célhelyeket, amelyek most már megtalálhatók a Snapchatben is. Mostantól exportálhatja a szegmenseket a Customer Insightsból a Snapchat célközönségekbe, és ezeket használhatja a hirdetések kiindulási alapértékeként.     
   További tájékoztatás az [Adatok exportálása Snapchatbe](export-snapchat.md) című témakörben olvasható.

### <a name="predictions"></a>Előrejelzések

- **Használja a termékszűrőket a prediktív termékjavaslatokban** A termékjavaslat modellhez hozzáadtunk egy képességet, amelynek segítségével termékszűrőket is használhat. Mostantól létrehozhat egy olyan előrejelzést, amely a termékek egy alkészletét használja.    
   További információkért lásd: [Termékszűrők konfigurálása](predict-product-recommendation.md#configure-product-filters).

- **Szegmensek létrehozása modellelőrejelzésekből** Egy olyan lehetőséget adtunk hozzá, amellyel gyorsan hozhat létre szegmenseket egy előrejelzés eredményeinek segítségével. A modell eredményei oldalról egyszerűen létrehozhat egy új szegmenst az új **Szegmens létrehozása** lehetőséggel.    
  További információért lásd: [Szegmens létrehozása saját modell előrejelzés alapján](prediction-based-segment.md).

- **A termékre vonatkozó javaslatok magyarázatai** Az AI-modell által a termékre vonatkozó javaslatok előállításához szükséges alapvető tényezőket ismerteti, valamint azt, hogy milyen mértékben járulnak hozzá ezek a tényezők a termékre vonatkozó javaslatokhoz. Ez az információ jelenik meg a modell eredményeinek képernyőjén.    
   További tudnivalókért olvassa el az [Előrejelzés állapotának és eredmények áttekintése](predict-product-recommendation.md#review-a-prediction-status-and-results) című témakört.

## <a name="february-2021-updates"></a>2021. februári frissítések

A 2021. februári frissítések számos szolgáltatást, teljesítménnyel kapcsolatos frissítést és hibajavítást tartalmaznak.

#### <a name="extensibility"></a>Bővíthetőség

- **Szegmensek exportálása az AdRoll alkalmazásba**

  Az exportálási célpontokat kiterjesztettük az AdRollra is. Mostantól exportálhatja a szegmenseket a Customer Insightsból az AdRoll-célközönségekbe, és ezeket használhatja a hirdetések alapértékeként. További információért lásd: [Összekötő a AdRoll szolgáltatáshoz](export-adroll.md).

#### <a name="segments"></a>Szegmensek
 
- **Szegmens megkettőzése**
  
  Ha új szegmenst szeretne létrehozni egy meglévő alapján, akkor most duplikálhatja a szegmenst, és a tovább finomítás érdekében szerkesztheti azt. 

- **További attribútumok hozzáadása egy szegmenshez**

  Mostantól attribútumokat is felvehet a szegmens kimenetébe, még akkor is, ha ezek az attribútumok nem részei az ügyfélprofilnak. Az előfizetési azonosítókat például akkor is felveheti egy szegmensbe, ha része annak az előfizetési entitásnak, amely M:1 kapcsolatban áll az ügyfélentitással. Amíg az attribútum az ügyfélentitáshoz kapcsolódó entitáshoz tartozik, ezeket az attribútumokat most már átveheti.  

#### <a name="predictions"></a>Előrejelzések

- **Prediktív termékjavaslatok létrehozása**

  Ha megérti, hogy az ügyfelek minek megvásárlása iránt érdeklődnek, az egyik első lépés az üzleti bevételek javításához és az ügyfelek hűségének kiépítéséhez a személyre szabás és az elköteleződés révén. Ha az ügyfél érdeklődésének nem megfelelő termékekre vonatkozó javaslatokat tesz, akkor kapcsolódási problémát teremthet az ügyfél és a vállalata között, és végül korlátozza az ügyfél általános potenciális bevételeit és tapasztalatait. 

  Mostantól saját adatok használatával előrejelzéseket készíthet arra nézve, hogy milyen termékeket vásárolnak majd a jövőben az ügyfelek. További információkat a [Termékjavaslat-előrejelzések](predict-product-recommendation.md) részben talál.

#### <a name="system-administration"></a>Rendszergazda

- **A környezet másolása több típusú adatforrást támogat**

  A rendszergazdák ugyanannak a szervezetnek az új környezetére másolhatják a környezetkonfigurációkat. Ez a funkció kibővíti a környezet másolása funkciót olyan esetekre, amikor az adatforrások Microsoft Dataverse kezelt adattón alapulnak vagy a Common Data Model mappa van használva.

## <a name="january-2021-updates"></a>2021. januári frissítések

A 2021. januári frissítések számos szolgáltatást, teljesítménnyel kapcsolatos frissítést és hibajavítást tartalmaznak.

#### <a name="extensibility"></a>Bővíthetőség

- **Bővített funkcionalitás és megnövelt teljesítmény az SFTP-exportáláshoz** Most már exportálhatja az összes kimeneti entitást a Customer Insightsból egy SFTP-állomásra. Korábban az export a szegmensentitásokra volt korlátozva. Ezenkívül az SFTP-exportálás teljesítménye kevesebb idő alatt több adatmennyiséget tesz lehetővé, az SFTP-állomás teljesítményétől függően.    
  További információért lásd: [SFTP összekötő (előzetes verzió)](export-sftp.md).  

#### <a name="segments"></a>Szegmensek

- **Gépi tanulás alapú szegmensjavaslatok a metrikák javítása érdekében** Van egy új módja a szegmensek felfedezésének és létrehozásának. A rendszer egy AI modell segítségével olyan szegmenseket javasol, amelyek segíthetnek a már nyomon követhetett KPI (mérték) javításában. Megmutatjuk a mértéken vagy más elsődleges attribútumon kiválasztott attribútumok hatásának mértékét. Ez az információ segít megtalálni a lehetőségeket kínáló potenciális szegmenseket.    
  További információért lásd: [Javasolt szegmensek (előzetes verzió)](suggested-segments.md).

#### <a name="data-unification"></a>Adategyesítés

- **Továbbfejlesztett egyeztetési élmény** Az adategyesítési területen az egyeztetési élmény frissült. Lehetővé teszi az egyeztetési szabályok konfigurálását és megtekintése, beleértve a részletes statisztikákat, hogy tovább magyarázza az egyeztetés működését. Vannak olyan beállítások, amelyek letiltják az egyezési szabályt, így az már nem aktív, miközben megőrzi a konfigurációt, egyeztetési szabályok húzása stb.
  További információ: [Entitások egyeztetése](match-entities.md).

- **Az egyeztetési folyamat deduplikációs kimenete entitásként elérhető** Az egyezési folyamatból származó deduplikációs folyamat kimenete most egy külön entitásba van írva további elemzés céljából. Ez az entitás a deduplikációs folyamatban használt mezőkből, valamint a nyertes rekordból és a nyertes rekordhoz egyesített megfelelő alternatív rekordokból áll.
  További információ lásd: [A deduplikáció kimenete entitásként](match-entities.md#deduplication-output-as-an-entity).

#### <a name="system-administration"></a>Rendszergazda

- **Az adatok zökkenőmentes megosztása a Microsoft Dataverse-szolgáltatással** most már megoszthatja a Customer Insights kimenetet a Microsoft Dataverse alkalmazással a Microsoft Dataverse Managed Data Lake használatával. Miután társít egy Dataverse környezetet a Customer Insights szolgáltatáshoz, lehetősége van engedélyezni az adatmegosztást.
  További tudnivalókért lásd: [Környezetek kezelése](manage-environments.md).




[!INCLUDE[footer-include](../includes/footer-banner.md)]