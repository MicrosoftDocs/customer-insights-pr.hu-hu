---
title: Adatjelentések megtekintése
description: A rendelkezésre álló jelentések segítségével valós idejű tevékenységeket láthat a webhelyén.
author: darrinw-docs
ms.reviewer: mhart
ms.author: darrinw
ms.date: 10/01/2021
ms.service: customer-insights
ms.subservice: engagement-insights
ms.topic: conceptual
ms.manager: shellyha
ms.openlocfilehash: 5ccdcb47db597154cf79b9f2e8fc238ab75dfde9
ms.sourcegitcommit: d9965f4bfc09391698a34042f6b44367e53819e3
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/30/2021
ms.locfileid: "7582925"
---
# <a name="view-reports"></a>Jelentések megtekintése

[!INCLUDE [cc-beta-prerelease-disclaimer](includes/cc-beta-prerelease-disclaimer.md)]

A jelentés olyan adatábrázolások gyűjteménye, amelyek az SDK-n keresztül összegyűjtött adatok segítségével mérhetők és megérthetőek a felhasználói viselkedésmódok. A Dynamics 365 Customer Insights tartalmazza a webes és mobilprojektekre vonatkozó, azonnal elkészíthető (OOB) jelentéseket.  

## <a name="web-reports"></a>Webes jelentések

A webes jelentéseket a **Felfedezés** lehetőség alatt találja, a bal oldali navigációs ablaktáblában.

:::image type="content" source="media/report-menu.png" alt-text="A rendelkezésre álló jelentések listáját megjelenítő navigáció.":::

### <a name="real-time-usage-report"></a>Valós idejű használati jelentés

A **Valós idejű használati** jelentés áttekintést ad a webhelyen végzett aktuális tevékenységről, amely percenként automatikusan frissül. A valós idejű használat segítségével nyomon követheti a marketingkampányok, sajtóeseményeket és más forgatókönyvek hatásait a webhely forgalmára.

### <a name="key-metrics-reports"></a>Alapvető mutatókról szóló jelentések

- Az **Oldalnézetek** listázza az egyes oldalak megtekintéseit, valamint a kiválasztott időkeretben az összes oldal megtekintés számát.

- A **Látogatások** a látogatások számával és időtartamával kapcsolatos információkat mutatják.

- A **Látogatók** tájékoztatást adnak az új és egyedi látogatókról a weboldaladon.

### <a name="content-reports"></a>Tartalommal kapcsolatos jelentések

- A **Linkek** a kattintások számát és típusát mutatják.

- Az **Oldalak elhagyása** listázza azokat a hivatkozásokat, amelyekre a látogatók a webhely elhagyásához kattintottak.

### <a name="traffic-sources-reports"></a>Forgalomforrásokról szóló jelentések

- A **Referálók** felsorolja azokat a domaineket és URL-címeket, amelyek a látogatókat az Ön webhelyére irányították.

- A **Nyomkövetési kódok** részleteket közölnek a látogatókat az Ön webhelyére irányító linkekben található nyomkövetési kódokról.

### <a name="visitor-profiles-reports"></a>Látogatói profilok jelentései

- Az **Eszközök** felsorolja a webhelye eléréséhez használt fizikai eszközöket.

- Az **Operációs rendszerek és böngészők** betekintéseket nyújt a webhely elérésekor használt operációs rendszerekbe és böngészőkbe.

- A **Helyek** országonként, régiónként és városonként mutatnak információkat a látogatókról.

- A **Nyelvek** az oldalmegtekintések listája a látogató által preferált nyelvek szerint.

## <a name="mobile-reports"></a>Mobiljelentések

A mobiljelentések valós idejű használat, alkalmazás és felhasználói kategóriák szerint vannak csoportosítva. A mobiljelentéseket a **Felfedezés** lehetőség alatt találja, a bal oldali navigációs ablaktáblában.   

:::image type="content" source="media/mobile-reports.png" alt-text="Az aktivitási információk felhasználói felülete bemutatja a valós idejű használati jelentést, amely adatokat renderel a diagramokban és listákban.":::   

### <a name="real-time-usage"></a>Valós idejű használat

A **Valós idejű használat** áttekintést ad a mobilalkalmazás aktuális tevékenységével kapcsolatban, amely automatikusan frissül minden percben. A valós idejű használat segítségével figyelheti az alkalmazásban aktív felhasználók és munkamenetek számát, valamint a felső képernyőnézeteket.

### <a name="app-reports"></a>Alkalmazás jelentések

- A **Képernyőnézetek** felsorolja az alkalmazás egyes képernyőinek képernyőnézettségét és a képernyőnézések teljes számát egy kiválasztott időkereten belül. A képernyőnézetek a képernyő neve vagy a képernyő címe szerint is megtekinthetők.

- A **Munkamenetek** a munkamenetek számával és időtartamával kapcsolatos információkat mutatják.

- A **Visszatérés gyakorisága** a munkamenetek számát az utolsó munkamenet óta eltelt napok száma szerint csoportosítja.

- **Felhasználók** új és visszatérő felhasználók megjelenítése a mobilalkalmazásban.

- **Események** felsorolja az alkalmazásból gyűjtött összes eseményt, valamint az egyes események összesített számát.

### <a name="user-reports"></a>Felhasználói jelentések

- **Alkalmazásverziók** felsorolja a mobilalkalmazás felhasználói bázis által használt verzióit.

- **Eszközök és operációs rendszerek verziói** betekintést nyújtanak, hogy mely eszközök és operációs rendszerek futtatják a mobilalkalmazást.

- A **Helyek** országonként, régiónként és városonként mutatnak információkat az app felhasználókról.

## <a name="filter-by-time-or-date-range"></a>Szűrés idő- vagy dátumtartomány szerint

Egy webes vagy mobilos jelentésben kiválaszthatja a időkeret dátumtartományt, hogy egy értékre vagy időszakra összpontosítson. 

- A kiválasztott időkeret a jelentés nézetének jobb felső sarkában jelöljön ki egy értéket a jelentés legördülő listájából. Választhat **Rögzített dátumtartományt** is. 

  :::image type="content" source="media/filter-by-time.png" alt-text="Szűrés idő- vagy dátumtartomány szerint.":::   

- A legtöbb jelentésnél a jelentés szűréséhez jelöljön ki egy értéket egy diagramban vagy listában.

> [!NOTE]
> Az időtartomány kiválasztása a valós idejű használati jelentéshez ki van kapcsolva; a valós idejű használati jelentés időtartománya a "most".


[!INCLUDE[footer-include](../includes/footer-banner.md)]
