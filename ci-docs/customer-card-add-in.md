---
title: Ügyfélkártya-bővítmény a Dynamics 365 alkalmazásokhoz (előzetes verzió) (videót tartalmaz)
description: Ügyfélprofil-adatok megjelenítése a Customer Insights rendszerből a Dynamics 365 alkalmazásokban ezzel a bővítménysel.
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
ms.openlocfilehash: 8b3b6a0d54b80d7df454e9dc925f14cc3c39684c
ms.sourcegitcommit: 594081c82ca385f7143b3416378533aaf2d6d0d3
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/27/2022
ms.locfileid: "9194926"
---
# <a name="customer-card-add-in-for-dynamics-365-apps-preview"></a>Ügyfélkártya-bővítmény a Dynamics 365 alkalmazásokhoz (előzetes verzió)

360 fokos képet kaphat az ügyfeleiről közvetlenül a Dynamics 365 alkalmazásokban. A támogatott Dynamics 365 alkalmazásban telepített Ügyfélkártya-bővítmény segítségével megjeleníthet ügyfélprofil-mezőket, információkat és tevékenységi idővonalat. A bővítmény úgy olvassa be az adatokat a Customer Insightsból, hogy a művelet nincs hatással a csatlakoztatott Dynamics 365-alkalmazásban található adatokra.

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWN1qv]

## <a name="prerequisites"></a>Előfeltételek

- Dynamics 365 modellvezérelt alkalmazások, például Sales vagy ügyfélszolgálat, 9.0-s és újabb verzió.
- Ahhoz, hogy a Dynamics 365-adatok leképeződjenek a Customer Insights ügyfélprofiljaira, javasoljuk, hogy azokat [a Dynamics 365 alkalmazásból töltse be az Microsoft Dataverse összekötő használatával](connect-power-query.md). Ha más módszert használ a Dynamics 365 kapcsolattartók (vagy partnerek) betöltésére, győződjön meg arról, hogy a `contactid` (vagy `accountid`) mező az adott adatforrás elsődleges kulcsaként [van beállítva az adategyesítési folyamat során](map-entities.md#select-primary-key-and-semantic-type-for-attributes).
- Az adatok megtekintéséhez az Ügyfélkártya bővítmény minden Dynamics 365-felhasználóját felhasználóként [kell](permissions.md) hozzáadni a Customer Insights szolgáltatáshoz.
- [Konfigurált keresési és szűrési lehetőségek](search-filter-index.md) a Customer Insights megoldásban.
- Minden bővítményvezérlő a Customer Insights adott adataira támaszkodik. Egyes adatok és vezérlők csak meghatározott típusú környezetekben érhetők el. A bővítmény konfigurációja tájékoztatja, ha egy vezérlő nem érhető el a kiválasztott környezettípus miatt. További információ a [környezet helyreállításáról](work-with-business-accounts.md).
  - **A mértékvezérléshez** konfigurált ügyfélattribútum-mértékekre [van szükség](measures.md).
  - **Az intelligenciavezérléshez** előrejelzések vagy egyéni modellek [használatával](predictions-overview.md) létrehozott adatokra van szükség.
  - **Az Ügyféladatok vezérlő** az egyesített ügyfélprofilban elérhető profil összes mezőjét megjeleníti.
  - **A gazdagodás szabályozásához** aktív [gazdagításokra van szükség az ügyfélprofilokra](enrichment-hub.md) alkalmazva. A kártyabővítmény a következő bővítéseket támogatja: [a Microsoft által biztosított márkák](enrichment-microsoft.md), [a Microsoft által biztosított érdeklődési körök](enrichment-microsoft.md) és [a Microsoft által biztosított Office engagement adatok](enrichment-office.md).
  - **A kapcsolattartók vezérlőjéhez** kapcsolatszemantikai entitástípusra van szükség.
  - **Az ütemterv-vezérléshez** konfigurált tevékenységekre [van szükség](activities.md).

## <a name="install-the-customer-card-add-in"></a>Az Ügyfélkártya bővítmény telepítése

Az Ügyfélkártya bővítmény a Dynamics 365Customer Engagement alkalmazásihoz használható megoldás. A megoldás telepítése:

1. Nyissa meg AppSource és keresse meg a **Dynamics-ügyfélkártyát**.

1. Válassza ki az [ügyfélkártya bővítményt az AppSource megoldásban](https://appsource.microsoft.com/product/dynamics-365/mscrm.dynamics_365_customer_insights_customer_card_addin?tab=Overview), és válassza a **Letöltés most** lehetőséget.

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

Az adott helyzettől függően vezérlőelemeket adhat hozzá a **Kapcsolattartó** űrlaphoz vagy a **Partner** űrlaphoz. Ha a Customer Insights-környezet üzleti fiókokhoz készült, javasoljuk, hogy adja hozzá a vezérlőket a Fiók űrlaphoz. Ebben az esetben cserélje le az alábbi lépésekben a "kapcsolattartót" a "partnerrel".

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

### <a name="controls-from-customer-card-add-in-dont-find-data"></a>Az ügyfélkártya-bővítmény vezérlői nem találnak adatokat

**Probléma:**

A vezérlők még a megfelelően konfigurált azonosítómezők esetén sem találják az ügyfelek adatait.  

**Megoldás:**

1. Győződjön meg arról, hogy a Kártyabővítményt a következő utasításoknak megfelelően konfigurálta: [Az ügyfélkártya-bővítmény konfigurálása](#configure-the-customer-card-add-in)

1. Tekintse át az adatbetöltési konfigurációt. Szerkessze a adatforrás a Kapcsolatazonosító GUID azonosítót tartalmazó Dynamics 365 rendszerhez. Ha a névjegyazonosító GUID azonosítója nagybetűkkel jelenik meg a Power Query szerkesztőben, próbálkozzon az alábbi lépésekkel:
    1. Szerkessze a adatforrás a adatforrás megnyitásához a Szerkesztőben Power Query.
    1. Válassza ki a kapcsolattartó azonosítója oszlopot.
    1. Válassza az Átalakítás **lehetőséget** a fejlécsávon az elérhető műveletek megtekintéséhez.
    1. Válassza a kisbetűk **lehetőséget**. Ellenőrizze, hogy a táblázatban szereplő GUID azonosítók most kisbetűek-e.
    1. Az adatforrások mentése.
    1. Adatbetöltési, -egyesítési és -letöltési folyamatok futtatásával terjesztheti a GUID azonosító módosításait.

Miután a rendszer befejezte a teljes frissítést, az Ügyfélkártya bővítmény vezérlőinek meg kell jeleníteniük a várt adatokat.

[!INCLUDE [footer-include](includes/footer-banner.md)]
