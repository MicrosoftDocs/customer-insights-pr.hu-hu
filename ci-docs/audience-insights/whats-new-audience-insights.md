---
title: Új és jövőbeni funkciók
description: Információ az új szolgáltatásokról, továbbfejlesztésekről és hibajavításokról.
ms.date: 04/07/2021
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
ms.reviewer: midevane
manager: shellyha
ms.openlocfilehash: 2159481f9355de738a7b457dcf0849a45c3e08db
ms.sourcegitcommit: aaa275c60c0c77c88196277b266a91d653f8f759
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/14/2021
ms.locfileid: "5896238"
---
# <a name="whats-new-in-the-audience-insights-capability-of-dynamics-365-customer-insights"></a>A célközönséggel kapcsolatos újdonságok a Dynamics 365 Customer Insights-ban.

[!INCLUDE [cc-data-platform-banner](../includes/cc-data-platform-banner.md)]

Örömmel jelentjük be legújabb frissítéseinket! Ez a cikk összefoglalja a nyilvános előzetes funkciókat, általános elérhetőségű javításokat és a funkciófrissítéseket. A hosszú távú funkciótervekkel megtekintéséhez tekintse meg a [Dynamics 365 és Power Platform a kiadási terveket](/dynamics365/release-plans/).

A frissítéseket régiónként tesszük közzé. Így bizonyos régiók a mások előtt láthatják a funkciókat. Hacsak nincs másképpen meghatározva, nem kell semmilyen műveletet végrehajtania, és az alkalmazás automatikusan, leállás nélkül frissíthető.

> [!TIP]
> Funkciókérelmek és termékjavaslatok benyújtásához és szavazáshoz látogassa meg a [Dynamics 365 alkalmazás ötletek portálját](https://experience.dynamics.com/ideas/categories/?forum=79a8c474-4e35-e911-a971-000d3a4f3343&forumName=Dynamics%20365%20Customer%20Insights).

## <a name="march-2021-updates"></a>2021 márciusi frissítések

A 2021 márciusi frissítések számos funkciót, teljesítményfrissítést és hibajavítást tartalmaznak.

### <a name="activities"></a>Tevékenységek

- **Tevékenység varázsló és szemantikus típusok** Továbbfejlesztettük és frissítettük tevékenységleképezési élményünket, hogy útmutatóként szolgáljon és egyszerűbbé tegye a tevékenységleképezések létrehozását. Ebben az új élményben a felhasználók interaktív élményben részesülnek, amely segíthet a folyamat egyes lépéseinek elvégzésében. A tevékenységleképezési lépésben a felhasználó nemcsak a különböző tevékenységtípusokból választhat, hanem kiválaszthatja, hogy szemnatikusan szeretné-e leképezni az adatokat az *Előfizetés* és/vagy *SalesOrderLine* ipraági standard sémákhoz, amelyeket a lefelé irányuló folyasztáshoz is lehet használni.    
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

- **Szegmensek exportálása a RollWorksbe** Kiterjesztettük az exportálási célhelyeket, amelyek most már megtalálhatók a RollWorksben is. Mostantól exportálhatja a szegmenseket a Customer Insightsból a RollWorks célközönségekbe, és ezeket használhatja a B2B hirdetések kiindulási alapértékeként.    
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

  A rendszergazdák ugyanannak a szervezetnek az új környezetére másolhatják a környezetkonfigurációkat. Ez a funkció kibővíti a környezet másolási funkciójának működését az olyan esetekre, amikor Common Data Service adattón vagy Common Data Model-mappán alapuló adatforrásokat használnak.

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


## <a name="december-2020-updates"></a>2020 decemberi frissítések

A 2020. decemberi frissítések számos szolgáltatást, teljesítménnyel kapcsolatos frissítést és hibajavítást tartalmaznak.

### <a name="new-and-updated-features-in-december-2020"></a>Új és frissített szolgáltatások 2020 decemberében

#### <a name="data-enrichment"></a>Adatbővítés

- **Továbbfejlesztett márka- és érdeklődésaffinitás bővítések**
  
  Egyszerűsítettük az affinitási pontszámainkat, hogy könnyebben megérthetőek és használhatóak. Most már gyorsan azonosíthatja az ügyfeleket az alapján, hogy mennyi affinitást mutatnak van egy adott márka vagy érdeklődés irányában.

  Emellett új konfigurációs lehetőségeket is hozzáadtunk, hogy jobban szabályozni tudjuk, hogyan szeretné, hogy az ügyfélprofilokat bővíteni. 

  További információkért lásd: [Ügyfélprofilok bővítése márka- és érdeklődésikör-hűséggel](enrichment-microsoft.md).

- **Annak szabályozása, hogy mely profilokat bővítse**

  Most már csak az ügyfélprofilok egy részhalmazát bővítheti azzal a lehetőséggel, hogy az alapértelmezett ügyfélentitás helyett egy szegmens entitást válasszon. Hozzon létre egy szegmenst a vevőprofilokkal, amelyeket bővíteni szeretne és válassza ki a bővítési adatkészlete az ügyféladatkészlethez.
  Ez a funkció jelenleg csak az Experian és a HERE Technologies által biztosított bővítésekhez érhető el. Hamarosan lehetővé fogjuk tenni, hogy ez a képességet további bővítésekhez is.

  További információ: [Ügyfélprofilok bővítése demográfiai az Experian demográfiai adataival](enrichment-experian.md) vagy [Ügyfélprofilok bővítése a HERE Technologies segítségével](enrichment-here.md).

#### <a name="extensibility"></a>Bővíthetőség

- **A szegmensek aktiválása az Autopilot segítségével**

  Exportálhat szegmenseket az Autopilotba és használhatja ezeket marketingcélokra. További információért lásd: [Autopilot összekötő (előzetes verzió)](export-autopilot.md).

- **A szegmensek aktiválása a SendGrid segítségével**

  Exportálhat szegmenseket a SendGridbe, és használhatja ezeket marketingcélokra. További információért lásd: [Csatlakozó a SendGrid szolgáltatáshoz](export-sendgrid.md).

#### <a name="system-administration"></a>Rendszergazda

- **Frissített környezetkezelési élmény**
  
  Mostantól közvetlenül az alkalmazásfejléc környezetválasztójában hozhat létre, szerkeszthet, törölhet és állíthat vissza környezeteket. 
  
  Ezenkívül a használt környezet a környezetpanel tetején lesz rögzítve, így többé nem kell keresnie.

  További tudnivalókért lásd: [Környezetek kezelése](manage-environments.md).

## <a name="november-2020-updates"></a>2020. novemberi frissítések

A 2020-as novemberi frissítések számos szolgáltatást, teljesítménnyel kapcsolatos frissítést és hibajavítást tartalmaznak.

### <a name="new-and-updated-features-in-november-2020"></a>Új és frissített szolgáltatások 2020 novemberében

#### <a name="data-enrichment"></a>Adatbővítés

- **Olvassa be saját bővítési adatait a Secure File Transfer Protocol (SFTP) egyéni importálás segítségével**
  
  Az SFTP egyéni importálás lehetővé teszi, hogy olyan bővítési adatokat importáljon, amik még nem mentek keresztül az adategységesítési folyamaton. Tudjon meg többet az SFTP egyéni importálásról.

  További információkért lásd: [Ügyfélprofilok gazdagítása egyéni adatokkal (előnézet)](enrichment-SFTP-custom-import.md).
 
- **Az ügyféladatok gazdagítása helyadatokkal a HERE Technologies szolgáltatásból**

  A HERE Technologies adatbővítési szolgáltatásaival pontosabb helyértelmezést hozhat létre az ügyfelekről a cím normalizálásával, földrajzi hosszúság és szélesség kinyerésével stb. Tudjon meg többet HERE Technologies szolgáltatáson keresztül történő gazdagításról.

  További információkért lásd: [Ügyfélprofilok gazdagítása a HERE Technologies segítségével](enrichment-here.md).

#### <a name="data-unification"></a>Adategyesítés

- **Az adatprofil készítésének engedélyezési rugalmassága a kiválasztott entitásokon és mezőkön a tárfiókján**

  Kijelölheti, hogy melyik adatentitást és mezőt szeretné a Common Data Model mappájából az Azure Data Lake-tárfiókjában engedélyezni adatprofilozásra az adatbetöltési folyamat részeként.

  További információkért lásd: [Csatlakozás a Common Data Model mappájához](connect-common-data-model.md#connect-to-a-common-data-model-folder).

#### <a name="extensibility"></a>Bővíthetőség

- **A szegmensek aktiválása a Google Ads segítségével**

  Exportáljon szegmenseket a Google Ads célközönséglistából és használja ezeket a listákat, hogy reklámozhasson a Google Search, Google Display Network, YouTube és Gmail felületein. Tudjon meg többet a szegmensek aktiválásáról a Google Ads segítségével.

  További információért lásd: [Csatlakozó a Google Ads szolgáltatáshoz](export-google-ads.md).

- **A szegmensek aktiválása a Marketo segítségével**

  Exportáljon szegmenseket a Marketo célközönségekbe és használja ezeket a célközönségeket a marketing-automatizálásra. Tudjon meg többet a szegmensek aktiválásáról Marketo segítségével. 

  További információért lásd: [Csatlakozó a Marketo szolgáltatáshoz](export-marketo.md).

- **A szegmensek aktiválása a DotDigital segítségével**

  Exportáljon szegmenseket a DotDigitalba és használja ezeket marketingcélokra. Tudjon meg többet a szegmensek aktiválásáról a DotDigital segítségével. 

  További információért lásd: [Csatlakozó a DotDigital szolgáltatáshoz](export-dotdigital.md).

#### <a name="predictions"></a>Előrejelzések

- **Tranzakció lemorzsolódás előrejelzése**

  A tranzakciólemorzsolódási előrejelzés funkció lehetővé teszi, hogy egy adattudós segítsége nélkül megjósolja annak a valószínűségét, hogy egy ügyfél abbahagyja egy termék vagy szolgáltatás vásárlását.  Az előrejelzési pontszám használatával kombinálhatja az információkat ügyfeleiről, mint például az ügyfélérték, hogy szegmenseket hozhasson létre a magas lemorzsolódási kockázatról egy nagy értékű ügyfél esetében. Ennek a szegmensnek a használatával közvetlenül megcélozhat egy ügyfelet a marketing tevékenységein keresztül, az ügyféltámogatáson, vagy más forgatókönyvek segítségével, hogy csökkentse a lemorzsolódási kockázatot.
 
  Állítsa be a lemorzsolódás meghatározását idő alapú ablak-specifikusra az üzletéhez, és határozza meg, hogy egy ügyfél mikor tekintendő lemorzsolódónak. Például, egy élelmiszerüzlet valószínűleg lemorzsolódónak minősítene egy ügyfelet, ha az nem vásárolt semmit az elmúlt 30 napban.
 
  Ha folytatja az előrejelzés létrehozását, megmutatjuk Önnek, mely adatok szükségesek, és engedélyezzük az adatleképezést az üzletéről, azon mezőkre, amelyek szükségesek, hogy előre jelezzék a vásárlóinak lemorzsolódását. Emellett az ütemezést újratanításra is állíthatja, így a modell új információn alapul a rendszerében, és ennek megfelelően változtatja az üzleti körülményeket.
 
  További információért lásd: [Tranzakciólemorzsolódási előrejelzés (előnézet)](predict-transactional-churn.md).

#### <a name="system-administration"></a>Rendszergazda

- **Környezet visszaállítása**

  Állítson mindent alaphelyzetbe egy környezeten belül egy kiválasztott példányon, hogy megkezdhesse a frissítést.

  További információt lásd: [Egy már meglevő környezet visszaállítása](manage-environments.md#reset-an-existing-environment).


- **Csatlakozás az Azure Data Lake-tárfiókjához, fő szolgáltatás használatával**

  Írjon hozzá további kimeneti adatokat vagy olvassa adatait tárfiókjából az Azure fő szolgáltatás használatával. A meglévő tárfiók-kapcsolatok segítségével tovább használhatja fiókkulcsát. Emellett egy olyan frissítési beállítást is ajánlanak, mellyel használhatja a fő szolgáltatást előremozdulásához. Az új kapcsolatok a fő szolgáltatás hitelesítési módszerén fognak alapulni az Ön tárfiókján.

  További információkért lásd: [Csatlakozás az Azure Data Lake Storage Gen2 fiókjához az Azure fő szolgáltatás célközönség információk funkcióján keresztül](connect-service-principal.md).

## <a name="october-2020-updates"></a>2020. októberi frissítések

A 2020-as októberi frissítések számos szolgáltatást, teljesítménnyel kapcsolatos frissítést és hibajavítást tartalmaznak.

### <a name="new-and-updated-features-in-october-2020"></a>Új és frissített szolgáltatások 2020 októberében

#### <a name="extensibility"></a>Bővíthetőség

- **Exportálás a Mailchimpbe**

Exportáljon szegmenseket a meglévő célközönség-listákhoz a Mailchimpben, hogy a személyre szabott e-mail élményét biztosíthassa felhasználóinak.

További információért lásd: [Csatlakozó a Mailchimp szolgáltatáshoz](export-mailchimp.md).

#### <a name="data-enrichment"></a>Adatbővítés

- **Az egyező forrásrekordok törlése az Egyezési entitásban**

Adja meg a másodpéldányok törlési szabályait az entitásokban az egyezési folyamat használatával, hogy meghatározhassa a duplikált rekordokat. Egyesítse őket egy rekordba és csatolja hozzá az összes forrásrekordot ehhez az egyesített rekordhoz. Ez a duplikátum-mentesített rekord ezután felhasználásra kerül az entitáson keresztüli egyeztetési folyamatban.

További információ lásd: [A deduplikáció meghatározása az egyezési entitásban](match-entities.md#define-deduplication-on-a-match-entity).

#### <a name="system-administration"></a>Rendszergazda

- **Vezénylés: Új frissítési beállítás az Egyesítésben**

Egészen a mai napig, amikor egyesítési folyamatot folytat, a rendszer lefuttatta mindazon későbbi folyamatokat, amelyek az egységesítési és a további folyamatok. Most már ellenőrizhető az egyesítési folyamat kimenetét (az egységesített ügyfélentitást) mielőtt használná ezt a későbbi feldolgozásban, mint a szegmensek vagy a mennyiségek.
Az egyesítési oldalon most már választhatja, hogy csak az egyesítési lépést futtatja le, és így csak ezt folyamatot futtatja. Hogy frissítsen minden későbbi folyamatot is, választhatja az egyesítési és későbbi folyamatok futtatása opciót. 

## <a name="september-2020-updates"></a>2020. szeptemberi frissítések

A 2020. szeptemberi frissítések számos szolgáltatást, teljesítménnyel kapcsolatos frissítést és hibajavítást tartalmaznak.

### <a name="new-and-updated-features-in-september-2020"></a>Új és frissített szolgáltatások 2020. szeptemberben

#### <a name="activities"></a>Tevékenységek

- **Attribútum-szemantika intelligens előrejelzése**

Ez az új funkció azt jósolja, hogy milyen szemantikai típusú bemeneti attribútumok kerülnek át az adategyesítési folyamatba. Gépi tanulás modelleket használ, amelyek javítják a pontosságot és időt takarítanak meg.

#### <a name="enrichments"></a>Bővítések

- **Demográfiai adatok bővítése az Experian szolgáltatásból**

A demográfiai bővítés a Experianból mostantól elérhető az előzetes verzióban. A Experian a fogyasztói és üzleti hitel-jelentési és marketing szolgáltatások globális vezetője. Az [Experian adatbővítési szolgáltatásai segítségével](https://www.experian.com/marketing-services/microsoft?cmpid=ems_web_mci_cdppage) mélyebben megismerheti az ügyfeleket, ha bővíti az ügyfelek profilját demográfiai adatokkal, például a háztartás méretével, a jövedelemmel és más információkkal.

A funkció használatához aktív Experian-előfizetésnek kell lennie.

További információkért lásd: [Ügyfelek profiljainak gazdagítása az Experianból](enrichment-experian.md)


#### <a name="system-administration"></a>Rendszergazda

- **Feladatrészletek panel**

A feladat részletei ablaktábla segítségével megtekintheti a rendszer által futtatott feladatokra vonatkozó részleteket. A konfigurálással és a megoldásokkal kapcsolatos problémák azonosítására szolgáló praktikus módszer.
Tekintse át a hibaüzeneteket, tekintse meg, hogyan kezeli a lehetséges problémákat.
 
- **További oldalakhoz hozzáadott adatok feldolgozása**

Ez a javítás az **entitások** és az **ügyfelek** oldalon található entitások állapotára vonatkozó információkat ad meg.
 
Emellett a folyamatok előrehaladásával, valamint a feladat részleteivel is megtekintheti mindkét oldalon.

- **A rendszer állapotának javítása oldal**

Javítottuk az állapot részletei tábla struktúráját a **rendszer** > **Állapot** pontban az adatexportálások áttekintésekor.
 
Emellett a **részletek** oszlopban szereplő hibák részletesebbek és hasznosíthatók is. 
 
- **A visszavonás visszaállítja a feladatot az előző állapotba**

Amikor visszavon egy feladatot, például a egyeztetési folyamatban, vissza fog térni a legutolsó állapotába. Ha például tegnap befejezte a egyeztetési folyamatot, és ma visszavonja, akkor a tegnapi sikeres állapotra vált vissza.


## <a name="august-2020-updates"></a>2020. augusztusi frissítések

A 2020. augusztusi frissítések számos szolgáltatást, teljesítménnyel kapcsolatos frissítést és hibajavítást tartalmaznak.

### <a name="new-and-updated-features-in-august-2020"></a>Új és frissített szolgáltatások 2020. augusztusban

#### <a name="data-unification"></a>Adategyesítés

- **A leképezési fázis jobb élménye az adatok egyesítése során**

  Az adategyesítési folyamat leképezés fázisában tapasztalható élmény lehetővé teszi az entitások, attribútumok kiválasztását, és szemantikai elemek megadását egy zökkenőmentesebb módon.

  A változások:
  
  - entitások és mezők hozzáadásához szükséges kevesebb kapcsolati tevékenység
  - továbbfejlesztett keresési lehetőségek a leképezési lapon
  - a javasolt típusú mező vizuális és egyszerű azonosítása

#### <a name="enrichment"></a>Dúsítás

- **Érdeklődés affinitások bővítése elérhető több piacon**

  Az érdeklődési affinitások elérhetőségét az Egyesült Államokon kívül további öt piacra is kiterjesztjük: Kanadára, Ausztráliára, az Egyesült Királyságra, Franciaországra és Németországra. Ezzel a kiterjesztéssel az ügyféladatokat több, ezekre a piacokra vonatkozó érdeklődési körrel gazdagíthatja. Az ezeken a piacokon található ügyfélprofilokat is bővíthetjük a Microsoft helyi saját adatainak segítségével.
  További információkért lásd: [Ügyfélprofilok bővítése márka- és érdeklődésikör-hűséggel](enrichment-microsoft.md)


## <a name="july-2020-updates"></a>2020. júliusi frissítések

A 2020. júliusi frissítések számos szolgáltatást, teljesítménnyel kapcsolatos frissítést és hibajavítást tartalmaznak.

### <a name="new-and-updated-features-in-july-2020"></a>2020. júliusban bevezetett új és frissített funkciók

#### <a name="extensibility"></a>Bővíthetőség

- **Power Automate-trigger teljesített egyesítési folyamathoz**

  Kibővítettük a triggereket a Power Automate-hoz, és lehetővé tettük, hogy értesítést vagy műveletet hozzon létre az egyesítési folyamat (Megfeleltetés/Egyeztetés/Egyesítés) frissítésének befejeződése után.    
  További információ: [Power Automate összekötő](export-power-automate.md)

#### <a name="enrichment"></a>Dúsítás

- **A márkaaffinitások bővítése elérhető több piacon**

  A márkaaffinitások elérhetőségét az Egyesült Államokon kívül további öt piacra is kiterjesztjük: Kanadára, Ausztráliára, az Egyesült Királyságra, Franciaországra és Németországra. Ezzel a kiterjesztéssel az ügyfelek adatait a helyi márkákkal bővítheti ezeken a piacokon. Az ezeken a piacokon található ügyfélprofilokat is bővíthetjük a Microsoft helyi saját adatainak segítségével.
  További információkért lásd: [Ügyfélprofilok bővítése márka- és érdeklődésikör-hűséggel](enrichment-microsoft.md)

## <a name="june-2020-updates"></a>2020. júniusi frissítések

A 2020. júniusi frissítések számos szolgáltatást, teljesítménnyel kapcsolatos frissítést és hibajavítást tartalmaznak.

### <a name="new-and-updated-features-in-june-2020"></a>2020. júniusban bevezetett új és frissített funkciók

#### <a name="enrichment"></a>Bővítés

- **A Leadspace-ből származó vállalati adatokkal való bővítés**
  
  Az egyesített ügyfelek profiljaiban adja meg azokat a mezőket, amelyek a kapcsolódó vállalati adatok Leadspace-ben való keresésére szolgálnak. A bővítési folyamat futtatása után a B2B-profilok több attribútummal lesznek bővítve, beleértve a vállalat méretét, helyét, iparágát stb.    
  Az együttműködés lehetővé teszi az adatok minőségének javítását harmadik féltől származó szolgáltatások bevitelével. A bővítés használatához a Leadspace licenc szükséges ahhoz, hogy hozzáférjenek a B2B vállalati adatokhoz. Ez a rendszer azt a licencet fogja használni, hogy adatait folyamatosan gyarapítsa.    
  További információkért lásd: [Vállalati profilok bővítése a Leadspace-szel](enrichment-leadspace.md).

- **A bővítési központ oldala**

  Az első és a harmadik féltől származó bővítési szolgáltatóktól származó összes rendelkezésre álló adatbővítés ugyanazon a helyen van beállítva. Az adatbővítés konfigurálása zökkenőmentes élmény, amelyet egy közös helyről lehet kezelni.    
  További információkért lásd: [Az ügyfelek profiljainak bővítése](enrichment-hub.md).

- **Különálló márka- és érdeklődési kör hűség bővítése**

  A márkák és érdeklődési körök hűsége immár két független bővítés formájában érhető el. A szétválasztott bővítések révén rugalmasan konfigurálhatja és kezelheti azokat egyénileg, az üzleti igényektől és szükségletektől függően.    
  További információkért lásd: [Ügyfélprofilok bővítése márka- és érdeklődésikör-hűséggel](enrichment-microsoft.md).

#### <a name="extensibility"></a>Bővíthetőség

- **Kattintható URL-címek az egyesített tevékenységekhez a Dynamics 365 ügyfélkártya-bővítményében**

  Az egységesített tevékenységek az Ügyfélkártya-bővítményben most már kattintható URL-ek lesznek, hogyha példa URL-ek lettek megadva a tevékenységek konfigurálásánál.    
  További információ: [Ügyfélkártya bővítmény](customer-card-add-in.md).

- **A Dynamics 365 ügyfélkártya-bővítményben elérhető márka- és érdeklődésikör-hűségek**

  A Dynamics 365 ügyfélkártya-bővítmény új vezérlője lehetővé teszi, hogy a Dynamics 365-ben megjelenő ügyfélkapcsolati alkalmazásokban a kapcsolattartókon megjelenjenek márka- és érdeklődésikör-hűségek.    
  További információ: [Ügyfélkártya bővítmény](customer-card-add-in.md).

- **További Power Automate eseményindítók**

  Kibővítettük a triggereket a Power Automate-hez a következő triggerek hozzáadásával:
  - Értesítés kérése vagy művelet végrehajtása az automatizált teljes frissítés (adatforrások, Egyesítés, szegmensek, mérőszámok, exportálás) befejeződésekor
  - Küszöbérték definiálása egy üzleti intézkedéshez. Létrehozhat például egy értesítést, amelyet a rendszer a megadott küszöb átlépésekor küld el. Emellett az eseményindító olyan adatokat hoz át, amelyekkel összetettebb munkafolyamatok is létrehozhatók a Power Automate alkalmazásban.    
  További információ: [Power Automate összekötő](export-power-automate.md)

- **Exportálás a Facebook Ads Managerbe**
  
  Ezzel a funkcióval szegmenseket exportálhat a Facebook ADS Managerbe. A szegmensek exportálásra kerültek mint egyéni célközönségek, hogy egységesített ügyfélprofiloknál kerülhessenek felhasználásra a Facebook-on marketingkampányoknál és reklámoknál. Az egyéni célközönségek is használhatók kampányok létrehozásához az Instagramon a Facebook Ads Manageren keresztül.    
  További tudnivalókért lásd: [a Facebook Ads Manager összekötője](export-facebook.md).

#### <a name="predictions"></a>Előrejelzések

- **Előfizetési lemorzsolódás előrejelzése**

  Interaktív felületet követhet a lemorzsolódási előrejezések létrehozásához az előfizetési területeken, például felhőszolgáltatások, ügyféltagságok és más területeken. 

  Az előfizetési lemorzsolódás előrejelzése funkció lehetővé teszi, hogy megjósolja annak valószínűségét, hogy egy ügyfél nem folytatja az előfizetéses termékeket vagy szolgáltatásokat adatszekértő bevonása nélkül. A előrejelzési pontszám segítségével összekapcsolhatja az ügyfelekkel kapcsolatos egyéb információkat, hogy a nagy lemorzsolódás kockázatát jelentő szegmenseket hozzon létre. Ennek a szegmensnek a használatával közvetlenül megcélozhat egy ügyfelet a marketingben, az ügyféltámogatásban és más forgatókönyveken, hogy csökkentse a lemorzsolódás veszélyét egyes specifikus vásárlóknál, és hogy növelje bevételeit, csökkentse költségeit.

  A tapasztalaton belül a lemorzsolódás meghatározását a vállalatra jellemző időalapú ablakként állíthatja be. Előfordulhat például, hogy a havi előfizetési folyamattal rendelkező videóstreamelési vállalat lemorzsolódottként kezelhet egy ügyfelet az előfizetés lejárata után 15 nappal.

  Ahogy továbbhalad az előrejelzésen, végigvezetjük a szükséges adatokon, és lehetővé tesszük, hogy leképezze a vállalkozásával kapcsolatos adatokat az ügyfél-lemorzsolódás előrejelzéséhez szükságes mezőkkel. Az üzleti adatok módosításakor az ütemezést beállíthatja úgy is, hogy a rendszert átképezze az új információk alapján a változó üzleti körülményekhez való alkalmazkodáshoz.    
  További információkért lásd: [Előfizetési lemorzsolódás előrejelzése (előzetes verzió)](predict-subscription-churn.md).

#### <a name="segments"></a>Szegmensek

- **Hasonló ügyfelek keresése**
  
  Hasonló ügyfelek keresése az ügyfélkörben mesterséges intelligencia használatával. A bináris besorolás gépi tanulási modellje a kibontott szegmensben lévő ügyfelekhez hasonlítja a hasonlóságok pontszámát. A pontszám a forrás-szegmensben lévő ügyfelekhez való hasonlóságon alapul. A hasonlósági pontszámtól függően az ügyfelek profiljait az újonnan létrehozott szegmenshez adja hozzá a rendszer.

  A digitális marketingben hasonmás modellezésnek is nevezik, de AI modellt használ, hogy segítsen megtalálni azokat az ügyfeleket, akik hasonlóak az ügyfelei egy másik fontos szegmenséhez, úgy hogy több attribútumot vesz figyelembe. Ez nem csak lehetővé teszi, hogy kiválassza az attribútumokat, de azt is lehetővé teszi, hogy megadhatja azoknak az ügyfeleknek a maximális számát, akik ebben az új szegmensben kell lenniük. Az AI modell ezután a kiválasztott attribútumok alapján kiszámítja a hasonlósági pontszámokat az egyes ügyfelekre, és a magasabb átlagos hasonlósági pontszámmal rendelkező ügyfeleket keres. Az eredményül kapott szegmens olyan ügyfeleket fog tartalmazni, akik az eredeti szegmensben szereplő ügyfélhez hasonlónak tűnnek.    
  További információkért lásd: [Hasonló ügyfelek](find-similar-customer-segments.md).

- **Szegmensátfedések és differenciálók**

  A szegmens átfedéssel megtekintheti, hogy hány és melyik ügyfél közös két vagy több szegmensben. Például, hogy a nagy költésű szegmens átfedése milyen a nagy elégedettségű ügyfelek szegmensével, vagy hogy a lemorzsolódó ügyfélszegmens hogyan van átfedésben az alacsony elégedettségű ügyfelek szegmensével. Ezenkívül elemezheti, hogy az átfedés hogyan változik az Ön által választott extra attribútum alapján.

  A szegmensdifferenciálók azt mutatják, hogy mi különbözteti meg az egyik szegmenst az ügyfelek többi részétől vagy egy másik szegmenstől. Mindössze annyit kell tennie, hogy azonosítja a szegmenset, és a rendszer azonosítja a profil attribútumait és mérőszámait, amelyek megkülönböztetik a szegmenst a differenciálók rangsorolt listájának formájában – a legerősebb differenciálótól a leggyengébbig.    
  További információk: [Szegmens betekintő információi (előzetes verzió)](segment-insights.md).

- **Szegmens élettartama**
  
  Adja meg a szegmens aktiválásához vagy inaktiválásához alkalmas ütemezést.    
  További tudnivalókért lásd: [A Meglévő szegmensek kezelése](segments.md#manage-existing-segments).

## <a name="may-2020-updates"></a>2020. májusi frissítések

A 2020. májusi frissítések számos szolgáltatást, teljesítménnyel kapcsolatos frissítést és hibajavítást tartalmaznak.

### <a name="new-and-updated-features-in-may-2020"></a>Új és frissített funkciók 2020. májusában

#### <a name="data-ingestion"></a>Adatok betöltése

- **Valós idejű adatbetöltés: előzménynézetek**

  A valós idejű frissítések betöltésére szolgáló API-verzióval akár 30 napra vonatkozóan is megtekintheti a frissítések összesített előzményeit. Az összes sikeres vagy sikertelen API-hívás összesítéséhez hozzáférhet, beleértve azok eredményét, a forrásrendszert és más hasznos metaadatokat.    
  További információ: [Valós idejű adatbetöltés](real-time-data-ingestion.md).

- **Valós idejű adatbetöltés: profilfrissítések**

  A valós idejű adatbetöltés kiterjesztése lehetővé teszi, hogy másodpercen belül megtekintse bizonyos felhasználói profilok mezőinek változásait.    
  A tevékenységekre vonatkozó valós idejű funkciók mellet a rendszer támogatja az alacsony késleltetésű frissítéseket a profil mezőkhöz. A profil típusú mezők valós idejű frissítéseihez lejárati idő tartozik, ezért nem helyettesítik az ütemezett frissítéseket.    
  További információ: [Valós idejű adatbetöltés](real-time-data-ingestion.md).

#### <a name="extensibility"></a>Bővíthetőség

- **Frissített idősor és tördelés az Ügyfélkártya bővítményben**

  Az Ügyfélkártya-bővítmény idővonala végeredményben egyezik a tevékenység-idővonallal. A tördelés az idővonalon javult, amely akár 50 tevékenységet is megjeleníthet egyszerre. Azt is lehetővé teszi, hogy több tevékenységet töltsön be az idővonalon.    
  További információ: [Ügyfélkártya bővítmény](customer-card-add-in.md).

- **Power Automate eseményindító szegmensmódosításokhoz**

  A Power Automate eseményindítói meghatározzák, hogy miből hozhat létre folyamatot. Az újonnan hozzáadott eseményindító segítségével meghatározhatja a szegmenshez tartozó küszöbértéket. Létrehozhat például egy értesítést, amelyet a rendszer a megadott küszöb átlépésekor küld el.    
  További információ: [Power Automate összekötő](export-power-automate.md).

- **Többvállalatos támogatás egyéni modellekhez**

  Egyéni modellek munkafolyamatának konfigurálása egy másik Azure Machine Learning-bérlővel. Bejelentkezhet az Azure Machine Learning bérlőbe, amikor létrehoz egy új munkafolyamatot az egyéni modellekhez. Ez a képessége kibővítése a meglévő képességnek, amellyel integrálhatja saját Azure Machine Learning webszolgáltatását.    
  További tudnivalókat az [Egyéni gépi tanulás modellek](custom-models.md) című rész tartalmaz.

#### <a name="segments"></a>Szegmensek

- **Entitás elérési útjának automatizálása**

  Amikor a felhasználók létrehoznak egy szegmenst, meg kell hogy adják az entitás elérési útját. Ez a képesség az első lépése az entitás elérési útja meghatározásának automatizálásában, hogy Ön a tervezett szegmentálási kritériumra koncentrálhasson.    
  Ha az entitás, amely alapján az ügyfeleket szegmentálni szeretné, közvetlenül kapcsolódik az egyesített ügyfélentitáshoz, akkor többé nem kell megadnia az entitás elérési útját. Ha azonban egynél több lehetséges entitás elérési út van, akkor továbbra is manuálisan kell azt definiálni.

- **Több szegmensre vonatkozó műveletek**
  
  A felhasználók több szegmenst is kijelölhetnek, és műveleteket végezhetnek rajtuk, például a szegmenseket frissíthetik egyetlen kattintással.    

- **Szegmensek frissítése**

  A felhasználók frissíthetnek egyetlen szegmenst, vagy kiválaszthatják csak azokat a szegmenseket módosíthatják, amelyeket frissíteni kívánnak.    

  
- **Az összetett szegmensek javításai**

  A felhasználók más szegmenseken alapuló szegmenseket hozhatnak létre, módosíthatnak és törölhetnek. Például létrehozható egy szegmens egy másik szegmensen, amely egy harmadik szegmensen lett létrehozva.    

- **Szegment listaoldal**

  A szegmensek oldal új kialakítása egy listaformátumot használ, amely lehetővé teszi több szegmens egyszerre történő megjelenítését. A keresési mezővel gyorsan megkereshetők a szegmensek. A felhasználók mostantól több szegmensen is alkalmazhatnak olyan műveleteket,mint a letöltés vagy törlés. Az új trend élmény szegmensek jelentős változásainak gyors meghatározásához használható.    
  További információ: [Szegmensek létrehozása és kezelése](segments.md).

#### <a name="system-administration"></a>Rendszergazda

- **A Customer Insights elérhető a Microsoft Dynamics 365 Online Government-szolgáltatásban**

  Az interakciók több és több csatornájának köszönhetően a polgárok adatai elszórva vannak a számtalan rendszerben, ami silózott adatokhoz vezet, és a polgárokkal folytatott interakcióra vonatkozó információk töredékes nézetéhez. Anélkül, hogy teljes képet kapnának a polgárok interakcióról a csatornákon, lehetetlen, hogy a kormányok átfogó modernizálást hajtsanak végre. A Microsoft elkötelezett amellett, hogy támogassa a kormányzati szektor technológiai igényeit, hogy az lépést tudjon tartani a polgárok elvárásaival a következetes és reszponzív élmények tekintetében.    
  A 2020-as 1. kiadási hullámmal a Dynamics 365 Customer Insights elérhető lesz a Government Community Cloud (GCC) számára, amely egy környezet, amely úgy lett létrehozva, hogy megfeleljen az Egyesült Államok kormányzati szervei magasabb megfelelőségi igényeinek. Az ügynökségek egységes képet kapnak a polgárokról, és beépített AI-t használnak a kommunikációt javító betekintések, a munkatársak felhatalmazása és a közösségek átalakítása céljából, miközben csökkenthetik az informatikai összetettséget, és megfelelnek az Egyesült Államok megfelelőségi és biztonsági normáinak. A Dynamics 365 Government teljesíti az Egyesült Államok Federal Risk and Authorization Management Program (FedRAMP) magas szintű követelményeit, lehetővé téve az amerikai szövetségi hivatalok számára a költségmegtakarítást és elérhetővé téve a Microsoft Cloud mindenre kiterjedő biztonságát.

## <a name="april-2020-updates"></a>2020. áprilisi frissítések

A 2020-as áprilisi frissítések számos szolgáltatást, teljesítménnyel kapcsolatos frissítést és hibajavítást tartalmaznak.

### <a name="new-and-updated-features-in-april-2020"></a>Új és frissített funkciók 2020. áprilisában

#### <a name="activities"></a>Tevékenységek

- **Tevékenység entitás leképezése normál tevékenységtípushoz**
  
  A tevékenység konfigurációja és tárhelye jelenleg egy statikus kialakításon alapul, amellyel egy idővonalon tekinthetők meg. A tevékenységek szemantikai értelmezése, amely több felhasználásra is alkalmas az AI-modellekben, jelenleg nincs kihasználva teljes mértékben. Azt tervezzük, hogy a tevékenység idővonala dinamikusabb lesz, a tevékenységtípus és a tevékenységek jobb szemantikai értelmezése alapján. Ez a funkció a Common Data Model-szolgáltatásban meghatározott tevékenységtípus azonosítását célozza minden egyes betöltött tevékenység esetében.
  További információ: [Ügyféltevékenységek](activities.md).

#### <a name="data-ingestion"></a>Adatok betöltése

- **Valós idejű adatbetöltés: tevékenységek**
  
  A valós idejű adatbetáplálás azonnali módon biztosítja az adatokat a felhasználáshoz, amíg a következő ütemezett frissítés be nem hívja az adatokat az adatforrásból.    
  További információ: [Valós idejű adatbetöltés](real-time-data-ingestion.md).

- **Az adatok előkészítésének javítása**
  
  Tudjon meg többet az entitásba betöltött adatokról. Az adatösszesítéssel megismerheti azokat az adatminőségi tulajdonságokat, amelyek segíthetnek a megfelelő lépések megtételében.    
  További tudnivalók: [Entitásadatok felfedezése](entities.md#exploring-a-specific-entitys-data).

- **A Dynamics 365 analitikus adatainak betöltése a Common Data Service-szolgáltatással**
  
  A Common Data Service az adatforrások létrehozásának egy lehetséges módja. A meglévő Dynamics 365-ügyfelek az elemző entitásokat táplálhatnak be a Common Data Service-szolgáltatásból a Customer Insights alkalmazásba. Egyetlen adatforrás egyidejűleg használhat két megegyező Common Data Service-felügyelte adattavat a Customer Insights-környezetben.    
  További információ: [Kapcsolódás a Common Data Service felügyelt adattó adataihoz](connect-common-data-service-lake.md).

#### <a name="extensibility"></a>Bővíthetőség

- **Exportálás LiveRampbe**

  Az adatok aktiválása a LiveRamp® megoldásban, hogy a digitális, a közösségi és a TV-ökoszisztémákban több mint 500 platformot csatlakoztasson. Adatait a LiveRamp alkalmazásban hirdetési kampányok célzására, elrejtésére és személyre szabására használhatja.    
  További információ: [LiveRamp&reg; összekötő](export-liveramp.md).

- **Customer Insights Teams bővítmény**
  
  A robot keresési lehetőségeket biztosít az egyesített ügyfelek profiljaihoz. A megjelenő ügyfél profilból egy legfeljebb 15 mezőt tartalmazó kártyát jelenít meg. A többszörös egyezések olyan eredménylistát adnak vissza, ahol lehetőség van a profilok kiválasztására.    
  További információkért lásd: [Teams robot a Customer Insights alkalmazáshoz](export-teams-bot.md).

#### <a name="measures"></a>Mértékek

- **Listaoldal mérése**
  
  Az mérések oldalainak tökéletesítése magában foglalja a műveletek támogatását egy méréshez vagy több egyszerre végzett méréshez. Emellett a keresési mező segítségével gyorsan megkeresheti és nyomon követheti a méréseket.    
  További információ: [Szegmensek létrehozása és kezelése](segments.md).

- **Az összetett mérések javításai**
  
  A felhasználók más mérésken alapuló méréseket hozhatnak létre, módosíthatnak és törölhetnek. Például létrehozható egy mérés egy másik mérésben, amely egy harmadik mérésben lett létrehozva.

#### <a name="segments"></a>Szegmensek

- **Egy másik operátor**
  
  A Halmazban operátor több lehetséges sztringérték használatával lehetővé teszi az ügyfelek szegmentálását. Az operátor hozzáadását megelőzően az ilyen szegmenseket több VAGY feltétellel kellett létrehozni. A Halmazban operátorral egyetlen feltétellel teheti ezt meg.    
  További információ: [Szegmensek létrehozása és kezelése](segments.md).

#### <a name="system-administration"></a>Rendszergazda

- **A konfigurációs beállítások másolása új környezetbe**
  
  Másolja konfigurációit egyik környezetből a másikba. Új környezet létrehozásakor kiválaszthat egy meglévő környezetet, amelyből a konfigurációt másolni szeretné. Jelenleg az adatforrásokat, az adategyesítést, a kapcsolatokat, az méréseket és a szegmenseket lehetséges másolni. Adatforrás hitelesítő adatokat és a tényleges adatokat nem másolja a rendszer.    
  További tudnivalókért lásd: [Környezetek kezelése](manage-environments.md).


[!INCLUDE[footer-include](../includes/footer-banner.md)]