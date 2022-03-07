---
title: Ügyfélprofilok gazdagítása a Microsoft Office 365
description: A védett adatok Microsoft Office használatával gazdagítsa ügyfélprofiljait elköteleződési adatokkal.
ms.date: 12/03/2021
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: jodahl
ms.author: jodahl
manager: shellyha
ms.openlocfilehash: 938a9de83fd8f5ff0c9ae815d626cdfa35228aba
ms.sourcegitcommit: e7cdf36a78a2b1dd2850183224d39c8dde46b26f
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/16/2022
ms.locfileid: "8228477"
---
# <a name="enrich-customer-profiles-with-engagement-data-preview"></a>Ügyfélprofilok gazdagítása elkötelezettségi adatokkal (előzetes verzió)

Ahonnan származó Microsoft Office 365 adatok segítségével gazdagodhat az ügyfélfiók-profilokkal az alkalmazásokon keresztüli Office 365 elkötelezettségekkel kapcsolatos elemzésekkel. Az elkötelezettségi adatok e-mail és értekezleti tevékenységből állnak, amelyek a fiók szintjén összesítve vannak. Például az üzleti fiókból származó e-mailek száma vagy a fiókkal való értekezletek száma. Az egyes felhasználókra vonatkozó adatok nem állnak rendelkezésre. 

Ez a dúsítás a következő régiókban érhető el: Egyesült Királyság, Európa, Észak-Amerika.

## <a name="prerequisites"></a>Előfeltételek

A gazdagodás konfigurálásához a következő előfeltételeknek kell teljesülniük:

- Aktív Office 365 felhőlicenccel rendelkezik.
- Az üzleti fiókok alapján [egységes ügyfélprofilokkal](customer-profiles.md) rendelkezik [...](work-with-business-accounts.md).
- A Customer Insights-környezethez [Microsoft Dataverse szervezethez kell csatolni](create-environment.md#step-3-connect-to-microsoft-dataverse).
- Rendszergazdai [engedélyekkel rendelkezik](permissions.md#administrator).
- A bérlő rendszergazdájától Office 365 beleegyezését kapja vagy kaphatja ahhoz, hogy az adatokat felhasználva Office 365 betekintést nyújtson **a Szervezet** számára a Dynamics 365-alkalmazásokon belül.

## <a name="configure-the-enrichment"></a>Bővítés konfigurálása

1. A célközönség információin belül nyissa meg a következőt: **Adatok** > **Bővítés**.

1. Lépjen a **Felfedezés** lapra, és válassza **a Fiókkapcsolati** csempén az **Adatok** gazdagítása lehetőséget.

   :::image type="content" source="media/enrichment-office-tile.png" alt-text="Fiókkapcsolati csempe.":::
   
1. Válassza a Tovább **lehetőséget** az **Áttekintés** lépésben, és adja meg a szervezet e-mail címeit, amelyekhez az Office-adatokat összesíteni fogja. Csak a felsorolt e-mail címek adatait dolgozzuk fel a megfelelő kommunikációhoz. A legjobb gyakorlat az e-mail csoportok használata, például *az egyesült államokbeli értékesítési csapat*, amelyek könnyen kezelhetők a .Office 365 A csoportokban lévő e-mail címek száma megoldódik és megjelenik. Az e-mail címek teljes számának legalább 2-nek kell lennie, és nem haladhatja meg a 2500-at.

   :::image type="content" source="media/enrichment-office-email-addresses.png" alt-text="Fiókkapcsolati e-mail címek.":::

1. Tekintse át a beleegyező nyilatkozatot, jelölje be az **Elfogadom** jelölőnégyzetet, és válassza a Tovább **gombot**.

1. Válassza ki a vevő adatkészlet, és válassza a Tovább **lehetőséget**.

1. Térképezze fel a kapcsolattartó e-mail cím mezőjét, és válassza a Tovább **lehetőséget**.

1. Tekintse át a gazdagodási konfigurációt, adjon nevet a gazdagodásnak, és a gazdagodás mentéséhez válassza a Gazdagodás **mentése lehetőséget**.

## <a name="office-365-tenant-administrator-consent"></a>Office 365 bérlői rendszergazdai hozzájárulás

Office 365 A gazdagodás aktiválásához bérlői rendszergazdának a beleegyezése szükséges. A gazdagodás mentésekor e-mailt küldünk a Office 365 bérlői rendszergazdáknak, amely arra kéri őket, hogy vizsgálják felül és járuljanak hozzá ahhoz, hogy a Dynamics 365-alkalmazások felhasználhassák a vállalatok Office 365 adatait a Szervezet **számára nyújtott elemzésekhez**. A Office 365 bérlő rendszergazdája közvetlenül a felügyeleti konzolon Office 365 is beleegyezhet, ha a Szervezethez **való Elemzések lehetőséget** választja.

## <a name="running-the-enrichment-for-the-first-time"></a>A gazdagodás első futtatása

Amikor a gazdagodás első alkalommal megkezdődik, miután a Office 365 bérlő adminisztrátora hozzájárult, megkezdődik az adatok letöltése Office 365. Ez a folyamat időbe telik. Az első gazdagodási sorozat a tervek szerint hat órás késéssel fog megtörténni. A fiókkapcsolat áttekintési oldalán a gazdagodás befejezése után láthatja, hogy az adatok hány napot fednek le. Nagy adatmennyiséggel néhány nap múlva futtassa újra a gazdagodást. Biztosítja, hogy az adatok teljesek kedének ek legyen a teljes időablakban, ami egy év.

A folyamat elindításához válassza **a Futtatás** a Fiókkapcsolat konfigurációs lapján lehetőséget. Ezenkívül lehetővé teheti, hogy a rendszer automatikusan futtassa a gazdagodást egy [ütemezett frissítés](system.md#schedule-tab) részeként. Alapértelmezés szerint a gazdagodás hetente egyszer fut.

Az Office-adatok méretétől függően a gazdagodási futtatás több órát is igénybe vehet.

A gazdagítás futtatásakor a Microsoft a megfelelőségi határokon belül dolgozza fel az Office 365 adatokat, hogy összesített elemzéseket hozzon létre, amelyeket ezután hozzáad a Customer Insights-környezethez. Az egyéni szintű adatok (például bármely e-mail vagy naptármeghívó törzse) nem válnak elérhetővé a Customer Insights felhasználói számára. 

[!INCLUDE [progress-details-pane](../includes/progress-details-pane.md)]

## <a name="enrichment-results"></a>Bővítési eredmények

A gazdagodási folyamat futtatása után menjen a **Gazdagításaimba**, hogy áttekintse a gazdagodás eredményeit. Megtalálja a gazdagított ügyfelek teljes számát és áttekintést a gazdagodás eredményeiről. Ez magában foglalja a feldolgozott e-mailek és értekezletek számát, az adatok összesítésének napjainak számát és így tovább.

Talál egy diagramot is, amely tartalmazza a gazdagított ügyfelek számát az idő múlásával, valamint a gazdagodási adatok előnézetét.  

:::image type="content" source="media/enrichment-office-results-overview.png" alt-text="Az eredmények előnézete a bővítési folyamat futtatása után.":::

Minden adat a fiók szintjéig összesítve történik. A rendszer minden számlára kiszámít egy elkötelezettségi pontszámot, amely 0 és 100 között mozog. Az elkötelezettségi pontszám összetett mértéket biztosít a fiók elkötelezettségéről az e-mailek és értekezletek között a többi fiókhoz képest. Az alábbi lista azokat az összesített adatokat tartalmazza, amelyeket a fiókkapcsolat-gazdagodás biztosít:



| Adat                                                                              | Oszlopnév                              |
| :-------------------------------------------------------------------------------- |:---------------------------------------- |
| Aktivitási pontszám                                                                  |  EngagementScore                         |
| A fiókba küldött e-mailek száma                                                       |  NoOfEmails_ToAccount                    |
| E-mailek száma a fiókból                                                     |  NoOfEmails_FromAccount                  | 
| A fiókkal kezdeményezett értekezletek száma                                           |  NoOfMeetings_FromAccount                | 
| A szervezet által kezdeményezett értekezletek száma                                 |  NoOfMeetings_ToAccount                  | 
| A szervezetből származó személyek száma a fiókkal rendelkező értekezleteken                  |  NoOfContactsInvolved_Meetings           | 
| A szervezetből származó személyek száma a fiókkal folytatott e-mail beszélgetésekben       |  NoOfContactsInvolved_Emails             | 
| A szervezettel folytatott értekezleteken a fiókból származó személyek száma                  |  NoOfAccountContactsInvolved_Meetings    | 
| A szervezettel folytatott e-mailes beszélgetésekben a fiókból származó személyek száma       |  NoOfAccountContactsInvolved_Emails      | 
| Az elkötelezettség kezdő dátuma (első e-mail vagy értekezlet az adatokban)                        |  EngagementStartDate                     | 
| Napok az utolsó e-mail óta                                                             |  DaysSinceLastEmail                      | 
| Napok a legutóbbi találkozó óta                                                           |  DaysSinceLastMeeting                    | 
| Az ülések átlagos időtartama                                                      |  AverageDuration_Of_Meetings             | 
| A fiókból érkező e-mail válaszok átlagos időtartama                                    |  AverageDuration_Of_AccountEmailReplies  | 
| Összesítés kezdő dátuma                                                            |  AggregationStartDate                    | 
| Összesítési szint (év, hónap vagy hét)                                          |  Összesítési szint                        | 


Tekintse át a bővített adatokat az Előnézeti szakasz Továbbiak **című témakörével**. Megnyitja az *Office* entitást. A Richment **csoportban felsorolt entitást a** DataEntities **csoportban** > **is megtalálhatja**. Megtalálja a *Office_UserEntity* is, amely tartalmazza a gazdagodás konfigurálása során kiválasztott e-mail címek Active Directory-hez tartozó figuráit 

## <a name="see-enrichment-data-on-the-customer-card"></a>A bővítési adatok megtekintése az ügyfélkártyán

A fiókkapcsolat az egyes ügyfélkártyákon is megtekinthető. Nyissa meg az **Ügyfelek** lehetőséget, és válassza ki az ügyfél profilját. Az ügyfélkártyán megtalálja a fiók elkötelezettségi pontszámát, az e-mailek teljes számát és az elmúlt évben összesítve lévő értekezletek teljes számát. Olyan diagramokat is talál, amelyek az e-mail és az értekezlet előzményeit mutatják.

:::image type="content" source="media/enrichment-office-customer-card.png" alt-text="Bővített adatokkal rendelkező ügyfél-kártya.":::

## <a name="create-segments-and-measures-based-on-the-enriched-data"></a>Szegmensek és mértékek létrehozása a bővített adatok alapján

A dúsított adatok az alábbiakban részletezett szegmensek és intézkedések létrehozására használhatók. Például egy szegmens, amely tartalmazza az összes olyan ügyfelet, akiknek értéke az utolsó e-mail *óta eltelt napokban és* az utolsó találkozó óta eltelt napokban 60-ra *van.* Ez a szegmens elavult fiókokat tartalmaz, amelyeket megpróbálhat újraaktiválni. 

## <a name="next-steps"></a>További lépések

[!INCLUDE [next-steps-enrichment](../includes/next-steps-enrichment.md)]


[!INCLUDE[footer-include](../includes/footer-banner.md)]
