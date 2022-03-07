---
title: Ügyfélkártya-bővítmény Dynamics 365-alkalmazásokhoz (videót tartalmaz)
description: Ezzel a bővítménnyel a célközönségből származó adatok jeleníthetők a Dynamics 365-alkalmazásokban.
ms.date: 02/02/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: conceptual
author: Nils-2m
ms.author: nikeller
manager: shellyha
searchScope:
- ci-customers-page
- ci-search-filter
- ci-customer-card
- customerInsights
ms.openlocfilehash: d67d8e2cb30cf20de204bfb293bb8ce81c7bb2f4
ms.sourcegitcommit: 73cb021760516729e696c9a90731304d92e0e1ef
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/25/2022
ms.locfileid: "8353868"
---
# <a name="customer-card-add-in-preview"></a>Ügyfélkártya bővítmény (előzetes verzió)



360 fokos képet kaphat az ügyfeleiről közvetlenül a Dynamics 365 alkalmazásokban. A támogatott Dynamics 365 alkalmazásban telepített Ügyfélkártya-bővítmény segítségével megjeleníthet ügyfélprofil-mezőket, információkat és tevékenységi idővonalat. A bővítmény úgy olvassa be az adatokat a Customer Insightsból, hogy a művelet nincs hatással a csatlakoztatott Dynamics 365-alkalmazásban található adatokra.

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWN1qv]

## <a name="prerequisites"></a>Előfeltételek

- A bővítmény csak a Dynamics 365 modellalapú alkalmazásaival működik (például az Értékesítés vagy a Customer Service 9.0-s vagy későbbi veziójával).
- Ahhoz, hogy a Dynamics 365-adatok leképeződjenek a célközönség elemzések ügyfélprofiljaira, javasoljuk, hogy [az összekötő használatával Microsoft Dataverse a Dynamics 365 alkalmazásból nyugtassák be őket](connect-power-query.md). Ha más módszert használ a Dynamics 365-kapcsolattartók (vagy partnerek) beolvasására, meg kell győződnie arról, hogy az adategyesítési folyamat térképlépésében a `contactid` (vagy `accountid`) mező van beállítva az adott adatforrás elsődleges [kulcsaként](map-entities.md#select-primary-key-and-semantic-type-for-attributes). 
- Az adatok megtekintéséhez az Ügyfélkártya bővítmény minden Dynamics 365-felhasználóját [hozzá kell adni felhasználóként](permissions.md) a célközönség betekintési információihoz.
- Az adatok csak akkor kereshetők,ha a célközönség betekintési információihoz [konfigurálja a keresési és szűrőfunkciókat](search-filter-index.md).
- Minden bővítményellenőrzés a célközönség információi között szereplő konkrét adatokra hagyatkozik. Egyes adatok és vezérlők csak meghatározott típusú környezetekben érhetők el. A bővítmény konfigurációja értesíteni fogja, ha a kijelölt környezettípus miatt egy vezérlő nem érhető el. További információ a [környezet helyreállításáról](work-with-business-accounts.md).
  - **Mértékegység-vezérlő**: [Ügyfélattribútumok](measures.md) típusú, konfigurált intézkedéseket igényel.
  - **Intelligenciavezérlés**: Előrejelzések vagy egyéni modellek [használatával](predictions-overview.md) generált adatokra van szükség.
  - **Ügyféladatok vezérlő**: A profilból minden mező elérhető az egységes ügyfélprofilban.
  - **Dúsítási vezérlő**: Az ügyfelek profiljaira alkalmazott aktív [dúsítást](enrichment-hub.md) igényel. A kártyabőség támogatja ezeket a gazdagodásokat: [a Microsoft által biztosított márkák](enrichment-microsoft.md), [a Microsoft által biztosított érdeklődési körök](enrichment-microsoft.md) és [a Microsoft által megadott Office-elkötelezettségi adatok](enrichment-office.md).
  - **Kapcsolattartók vezérlő**: A kapcsolattartók típusú szemantikus entitás definícióját igényli.
  - **Idősor-vezérlő**: [Konfigurált tevékenységeket](activities.md) igényel.

## <a name="install-the-customer-card-add-in"></a>Az Ügyfélkártya bővítmény telepítése

Az Ügyfélkártya bővítmény a Dynamics 365Customer Engagement alkalmazásihoz használható megoldás. A megoldás telepítéséhez nyissa meg az AppSource lehetőséget, és keresse meg a **Dynamics ügyfélkártyát**. Válassza ki az [ügyfélkártya bővítményt az AppSource megoldásban](https://appsource.microsoft.com/product/dynamics-365/mscrm.dynamics_365_customer_insights_customer_card_addin?tab=Overview), és válassza a **Letöltés most** lehetőséget.

A megoldás telepítéséhez előfordulhat, hogy rendszergazdai hitelesítő adataival kell bejelentkeznie a Dynamics 365 alkalmazásba. Eltarthat egy ideig, amíg a megoldást települ a környezetébe.

## <a name="configure-the-customer-card-add-in"></a>Az ügyfélkártya bővítmény konfigurálása

1. Rendszergazdaként nyissa meg a Dynamics 365 **Beállítások** szakaszát, és válassza a **Megoldások** lehetőséget.

1. Válassza ki a **Megjelenítendő név** hivatkozást a **Dynamics 365 Customer Insights ügyfélkártya bővítmény (előzetes verzió)** megoldáshoz.

   > [!div class="mx-imgBorder"]
   > ![Megjelenítendő név választása.](media/select-display-name.png "Megjelenítendő név választása.")

1. Válassza a **Bejelentkezés** lehetőséget, és adja meg a Customer Insights konfigurálásához használt rendszergazdai fiók hitelesítő adatait.

   > [!NOTE]
   > Ellenőrizze, hogy a böngésző előugró ablakok blokkolása funkció nem blokkolja-e a hitelesítési ablakot, amikor a **Bejelentkezés** gombot választja.

1. Válassza ki azt a Customer Insights-környezetet, amelyből az adatokat szeretné lekérni.

1. Adja meg a mezőleképezéseket a Dynamics 365-alkalmazásban szereplő rekordokhoz. A Customer Insightsban található adatoktól függően leképezheti a következő beállításokat:
   - Ha egy kapcsolattartót szeretne leképezni, akkor jelölje ki a mezőt az Ügyfél entitásban kapcsolattartói entitás azonosítójának megfelelő mezőben.
   - Ha egy partnert szeretne leképezni, akkor jelölje ki a mezőt az Ügyfél entitásban partner entitás azonosítójának megfelelő mezőben.

   > [!div class="mx-imgBorder"]
   > ![Kapcsolattartó azonosítója mező.](media/contact-id-field.png "Kapcsolattartó azonosítója mező.")

1. A beállítás mentéséhez válassza a **Konfiguráció mentése** lehetőséget.

1. A következő lépésként biztonsági szerepköröket kell hozzárendelnie a Dynamics 365-ben, hogy a felhasználók testreszabhassák és megtekintsék az ügyfélkártyát. A Dynamics 365 szolgáltatásban ugorjon a **Beállítások** > **Biztonság** > **Felhasználók** lehetőségre. Jelölje ki a felhasználói szerepkörök szerkesztéséhez használt felhasználókat, és válassza a **Szerepkörök kezelése** elemet.

1. Rendelje hozzá a **Customer Insights-kártya testreszabója** szerepkört azokhoz a felhasználókhoz, akik testre szabják a kártyán megjelenített tartalmat a teljes szervezetre vonatkozóan.

## <a name="add-customer-card-controls-to-forms"></a>Ügyfélkártya-vezérlők hozzáadása űrlapokhoz

Az adott helyzettől függően vezérlőelemeket adhat hozzá a **Kapcsolattartó** űrlaphoz vagy a **Partner** űrlaphoz. Ha a célközönséggel kapcsolatos információk környezete üzleti partnerekhez van, javasolt a vezérlők felvétele a Partnerek űrlapra. Ebben az esetben cserélje le az alábbi lépésekben a "kapcsolattartót" a "partnerrel".

1. Ha hozzá szeretné adni az ügyfélkártya vezérlőket a kapcsolattartói űrlaphoz, akkor nyissa meg a **Beállítások** > **Testreszabás** részt a Dynamics 365 megoldásban.

1. Válassza ki **A rendszer testreszabása** lehetőséget.

1. Tallózással keresse meg a **Kapcsolattartó** entitást, és bontsa ki, majd válassza az **Űrlapok** lehetőséget.

1. Válassza ki azt a kapcsolattartói űrlapot, amelyhez hozzá akarja adni az Ügyfélkártya vezérlőit.

    > [!div class="mx-imgBorder"]
    > ![Válassza a Kapcsolattartói űrlapot.](media/contact-active-forms.png "Válassza a Kapcsolattartói űrlapot.")

1. A vezérlő hozzáadásához húzza az űrlapszerkesztő bármelyik mezőjét a **Mezőkezelőből** arra a helyre, ahol a demográfiai vezérlőt meg szeretné jeleníteni.

1. Jelölje ki az imént hozzáadott mezőt az űrlapon, majd válassza a **Tulajdonságok módosítása** lehetőséget.

1. Lépjen a **Vezérlők** lapra, és válassza a **Vezérlő hozzáadása** lehetőséget. Válassza ki az egyik használható egyéni vezérlőt, és válassza a **Hozzáadás** lehetőséget.

1. Ha **Mezőtulajdonságok** párbeszédpanelen törölje a **Megjelenítendő címke az űrlapon** jelölését.

1. Válassza ki **Web** lehetőséget az vezérlőhöz. A Dúsítási vezérlőhöz adja meg, hogy milyen dúsítástípust szeretne megjeleníteni az **enrichmentType** mező konfigurálásával. Mindegyik bővítéstípushoz adjon hozzá külön bővítési vezérlőt.

1. Válassza a **Mentés** és a **Közzététel** lehetőséget a frissített kapcsolattartói űrlap közzétételéhez.

1. Nyissa meg a közzétett kapcsolattartó űrlapot. Ekkor megjelenik az újonnan hozzáadott vezérlő. Előfordulhat, hogy első használatkor be kell jelentkeznie.

1. Ha testre szeretné szabni, hogy mit szeretne megjeleníteni az egyéni vezérlőn, akkor válassza a jobb felső sarokban található szerkesztés gombot.

## <a name="upgrade-customer-card-add-in"></a>Ügyfélkártya bővítmény frissítése

Az Ügyfélkártya bővítmény nem frissül automatikusan. A legújabb verzióra való frissítéshez kövesse az alábbi lépéseket abban a Dynamics 365 alkalmazásban, amely telepítette a bővítményt.

1. A Dynamics 365 alkalmazásban válassza a **Beállítások** > **Testreszabás**, majd a **Megoldások** lehetőséget.

1. A bővítmények táblázatában keresse meg a **CustomerInsightsCustomerCard** elemet és jelölje ki a sort.

1. Válassza a **Megoldásfrissítés alkalmazása** lehetőséget a műveletsávban.

   :::image type="content" source="media/customer-card-add-in-upgrade.png" alt-text="Megoldás frissítése a Dynamics 365 alkalmazások Testreszabás területén.":::

1. A frissítési folyamat megkezdése után betöltési kijelző látható, amíg be nem fejeződik a frissítés. Ha nincs újabb verzió, a frissítés hibaüzenetet ad.

## <a name="troubleshooting"></a>Hibaelhárítás

### <a name="controls-from-customer-card-add-in-dont-find-data"></a>A vevőkártya-bővítmény vezérlői nem találnak adatokat

**Probléma:**

A vezérlők még a megfelelően konfigurált azonosítómezők esetén sem találnak adatokat egyetlen ügyfél számára sem.  

**Megoldás:**

1. Győződjön meg arról, hogy a kártyabővetítványt az utasításoknak megfelelően konfigurálta: [A vevőkártya-bővítmény konfigurálása](#configure-the-customer-card-add-in) 

1. Tekintse át az adatbetöltési konfigurációt. Szerkessze a partnerazonosító GUID azonosítóját tartalmazó Dynamics 365 rendszer adatforrás. Ha a partnerazonosító GUID azonosítója nagybetűkkel jelenik meg a Power Query szerkesztőben, próbálkozzon a következőkkel: 
    1. A adatforrás szerkesztéséhez nyissa meg a adatforrás a Szerkesztőben Power Query.
    1. Jelölje ki a partnerazonosító oszlopot.
    1. Az elérhető műveletek megtekintéséhez válassza az Átalakítás **lehetőséget** a fejlécsávon.
    1. Válassza a **kisbetűt**. Ellenőrizze, hogy a táblázatban szereplő GUID-ok kisbetűsek-e.
    1. Az adatforrások mentése.
    1. Futtassa az adatbetöltést, -egyesítést és lefelé irányuló folyamatokat a GUID módosításainak propagálásához. 

A teljes frissítés befejezése után a Customer Card bővítmény vezérlőinek meg kell jeleníteniük a várt adatokat. 

[!INCLUDE[footer-include](../includes/footer-banner.md)]
