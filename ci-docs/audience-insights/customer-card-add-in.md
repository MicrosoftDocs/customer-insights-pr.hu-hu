---
title: Telepítheti és használhatja az Ügyfélkártya bővítményt
description: Az Ügyfélkártya bővítmény telepítése és konfigurálása a Dynamics 365 Customer Insights megoldásban.
ms.date: 01/20/2021
ms.reviewer: philk
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: a6d5b49380ed129cf147698a16f5f3f597bf7fbc
ms.sourcegitcommit: 139548f8a2d0f24d54c4a6c404a743eeeb8ef8e0
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/15/2021
ms.locfileid: "5268047"
---
# <a name="customer-card-add-in-preview"></a>Ügyfélkártya bővítmény (előzetes verzió)

[!INCLUDE [cc-data-platform-banner](../includes/cc-data-platform-banner.md)]

360 fokos képet kaphat az ügyfeleiről közvetlenül a Dynamics 365 alkalmazásokban. A demográfiai adatok, a betekintések és a tevékenységek ütemezése az ügyfélkarton bővítménnyel tekinthető meg.

## <a name="prerequisites"></a>Előfeltételek

- Dynamics 365 alkalmazás (például Értékesítési központ vagy Ügyfélszolgálati központ), 9.0 vagy újabb verziója, és az egyesített felület engedélyezve.
- Ügyfélprofilok [a Dynamics 365 alkalmazásból betöltve a Common Data Service szolgáltatással](connect-power-query.md).
- Az Ügyfélkártya bővítmény felhasználóit a célközönség-információkban [felhasználóként kell felvenni](permissions.md).
- [Konfigurált keresési és szűrési lehetőségek](search-filter-index.md).
- Demográfiai ellenőrzés: Demográfiai mezők (például az életkor vagy a nemek) az egyesített ügyfélprofilban érhetők el.
- A dúsítási vezérlő: az ügyfelek profiljaira alkalmazott aktív [dúsítást](enrichment-hub.md) igényel.
- Intelligenciai ellenőrzés: Az Azure Machine Learning ([Előrejelzések](predictions.md) vagy [Egyéni modellek](custom-models.md)) használatával létrehozott adatok szükségesek
- Mérték ellenőrzése: [Konfigurált mértékek](measures.md) szükségesek.
- Idősor-vezérlő: [Konfigurált tevékenységeket](activities.md) igényel.

## <a name="install-the-customer-card-add-in"></a>Az Ügyfélkártya bővítmény telepítése

Az Ügyfélkártya bővítmény a Dynamics 365Customer Engagement alkalmazásihoz használható megoldás. A megoldás telepítéséhez nyissa meg az AppSource lehetőséget, és keresse meg a **Dynamics ügyfélkártyát**. Válassza ki az [ügyfélkártya bővítményt az AppSource megoldásban](https://appsource.microsoft.com/product/dynamics-365/mscrm.dynamics_365_customer_insights_customer_card_addin?tab=Overview), és válassza a **Letöltés most** lehetőséget.

A megoldás telepítéséhez előfordulhat, hogy rendszergazdai hitelesítő adataival kell bejelentkeznie a Dynamics 365 alkalmazásba.

Eltarthat egy ideig, amíg a megoldást települ a környezetébe.

## <a name="configure-the-customer-card-add-in"></a>Az ügyfélkártya bővítmény konfigurálása

1. Rendszergazdaként nyissa meg a Dynamics 365 **Beállítások** szakaszát, és válassza a **Megoldások** lehetőséget.

1. Válassza ki a **Megjelenítendő név** hivatkozást a **Dynamics 365 Customer Insights ügyfélkártya bővítmény (előzetes verzió)** megoldáshoz.

   > [!div class="mx-imgBorder"]
   > ![Megjelenítendő név választása](media/select-display-name.png "Megjelenítendő név választása")

1. Válassza a **Bejelentkezés** lehetőséget, és adja meg a Customer Insights konfigurálásához használt rendszergazdai fiók hitelesítő adatait.

   > [!NOTE]
   > Ellenőrizze, hogy a böngésző előugró ablakok blokkolása funkció nem blokkolja-e a hitelesítési ablakot, amikor a **Bejelentkezés** gombot választja.

1. Válassza ki azt a környezetet, amelyből az adatokat szeretné lekérni.

1. Adja meg, hogy mely mezők legyenek hozzárendelve a Dynamics 365 alkalmazás rekordjait.
   - Ha egy kapcsolattartót szeretne leképezni, akkor jelölje ki a mezőt az Ügyfél entitásban kapcsolattartói entitás azonosítójának megfelelő mezőben.
   - Ha egy partnert szeretne leképezni, akkor jelölje ki a mezőt az Ügyfél entitásban partner entitás azonosítójának megfelelő mezőben.

   > [!div class="mx-imgBorder"]
   > ![Kapcsolattartó azonosítója mező](media/contact-id-field.png "Kapcsolattartó azonosítója mező")

1. A beállítás mentéséhez válassza a **Konfiguráció mentése** lehetőséget.

1. A következő lépésként biztonsági szerepköröket kell hozzárendelnie a Dynamics 365-ben, hogy a felhasználók testreszabhassák és megtekintsék az ügyfélkártyát. A Dynamics 365 szolgáltatásban ugorjon a **Beállítások** > **Biztonság** > **Felhasználók** lehetőségre. Jelölje ki a felhasználói szerepkörök szerkesztéséhez használt felhasználókat, és válassza a **Szerepkörök kezelése** elemet.

1. Rendelje hozzá a **Customer Insights-kártya testreszabója** szerepkört azokhoz a felhasználókhoz, akik testre szabják a kártyán megjelenített tartalmat a teljes szervezetre vonatkozóan.

## <a name="add-customer-card-controls-to-forms"></a>Ügyfélkártya-vezérlők hozzáadása űrlapokhoz
  
1. Ha hozzá szeretné adni az ügyfélkártya vezérlőket a kapcsolattartói űrlaphoz, akkor nyissa meg a **Beállítások** > **Testreszabás** részt a Dynamics 365 megoldásban.

1. Válassza ki **A rendszer testreszabása** lehetőséget.

1. Tallózással keresse meg a **Kapcsolattartó** entitást, és bontsa ki, majd válassza az **Űrlapok** lehetőséget.

1. Válassza ki azt a kapcsolattartói űrlapot, amelyhez hozzá szeretné adni az Ügyfélkártya vezérlőit.

    > [!div class="mx-imgBorder"]
    > ![Válassza a Kapcsolattartói űrlapot](media/contact-active-forms.png "Válassza a Kapcsolattartói űrlapot")

1. A vezérlő hozzáadásához húzza az űrlapszerkesztő bármelyik mezőjét a **Mezőkezelőből** arra a helyre, ahol a demográfiai vezérlőt meg szeretné jeleníteni.

1. Jelölje ki az imént hozzáadott mezőt az űrlapon, majd válassza a **Tulajdonságok módosítása** lehetőséget.

1. Lépjen a **Vezérlők** lapra, és válassza a **Vezérlő hozzáadása** lehetőséget. Válassza ki az egyik használható egyéni vezérlőt, és válassza a **Hozzáadás** lehetőséget.

1. Ha **Mezőtulajdonságok** párbeszédpanelen törölje a **Megjelenítendő címke az űrlapon** jelölését.

1. Válassza ki **Web** lehetőséget az vezérlőhöz. A Dúsítási vezérlőhöz adja meg, hogy milyen dúsítástípust szeretne megjeleníteni az **enrichmentType** mező konfigurálásával. Mindegyik bővítéstípushoz adjon hozzá külön bővítési vezérlőt.

1. Válassza a **Mentés** és a **Közzététel** lehetőséget a frissített kapcsolattartói űrlap közzétételéhez.

1. Nyissa meg a közzétett kapcsolattartó űrlapot. Ekkor megjelenik az újonnan hozzáadott vezérlő. Előfordulhat, hogy első használatkor be kell jelentkeznie.

1. Ha testre szeretné szabni, hogy mit szeretne megjeleníteni az egyéni vezérlőn, akkor válassza a jobb felső sarokban található szerkesztés gombot.

## <a name="upgrade-customer-card-add-in"></a>Ügyfélkártya bővítmény frissítése
Az Ügyfélkártya bővítmény nem frissül automatikusan. A legújabb verzióra való frissítéshez kövesse a Dynamics 365 alkalmazásban, amelyhez telepítve van a bővítmény.

1. A Dynamics 365 alkalmazásban válassza a **Beállítások** > **Testreszabás**, majd a **Megoldások** lehetőséget.

1. A bővítmények táblázatában keresse meg a **CustomerInsightsCustomerCard** elemet és jelölje ki a sort.

1. Válassza a **Megoldásfrissítés alkalmazása** lehetőséget a műveletsávban.

   :::image type="content" source="media/customer-card-add-in-upgrade.png" alt-text="Megoldás frissítése a Dynamics 365 alkalmazások Testreszabás területén":::

1. A frissítési folyamat megkezdése után betöltési kijelző látható, amíg be nem fejeződik a frissítés. Ha nincs újabb verzió, a frissítés hibaüzenetet ad.


[!INCLUDE[footer-include](../includes/footer-banner.md)]