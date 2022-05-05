---
title: Bővítse az ügyfélprofilokat a Microsoft Office 365
description: Használjon saját adatokat Microsoft Office, hogy ügyfélprofiljait elkötelezettségi adatokkal gazdagítsa.
ms.date: 12/03/2021
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: jodahl
ms.author: jodahl
manager: shellyha
ms.openlocfilehash: 782042ff643bd0cc70ac53e5680bfd0c68944d84
ms.sourcegitcommit: b7dbcd5627c2ebfbcfe65589991c159ba290d377
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/27/2022
ms.locfileid: "8642718"
---
# <a name="enrich-customer-profiles-with-engagement-data-preview"></a>Ügyfélprofilok gazdagítása elkötelezettségi adatokkal (előzetes verzió)

Ahonnan Microsoft Office 365 származó adatokkal gazdagíthatja ügyfélfiók-profiljait az alkalmazásokon keresztüli Office 365 elkötelezettségekkel kapcsolatos betekintésekkel. Az elkötelezettségi adatok e-mailből és értekezlet-tevékenységből állnak, amelyeket a fiók szintjén összesítenek. Például az üzleti fiókból származó e-mailek száma vagy a fiókkal folytatott értekezletek száma. Az egyes felhasználókra vonatkozó adatok nem állnak rendelkezésre. 

Ez a gazdagodás a következő régiókban érhető el: Egyesült Királyság, Európa, Észak-Amerika.

## <a name="prerequisites"></a>Előfeltételek

A gazdagodás konfigurálásához a következő előfeltételeknek kell teljesülniük:

- Aktív Office 365 felhőlicenccel rendelkezik.
- Az üzleti fiókok alapján [egyesített ügyfélprofilokkal](customer-profiles.md) rendelkezik [...](work-with-business-accounts.md).
- A Customer Insights környezethez csatolni [Microsoft Dataverse kell egy](create-environment.md#step-3-connect-to-microsoft-dataverse) szervezetet.
- Rendszergazdai [engedélyekkel rendelkezik](permissions.md#admin).
- A bérlői rendszergazda beleegyezésével Office 365 rendelkezik, vagy megszerezheti, hogy az adatokat felhasználva Office 365 elemzési elemzéseket biztosítson **a szervezet** számára a Dynamics 365-alkalmazásokban.

## <a name="configure-the-enrichment"></a>Bővítés konfigurálása

1. Lépjen az **Adatok** > **Bővítés** pontra.

1. Lépjen a **Felfedezés** fülre, és válassza az Adatok **gazdagítása lehetőséget** a **Fiókmegjegyzés** csempén.

   :::image type="content" source="media/enrichment-office-tile.png" alt-text="Fiók elkötelezettség csempe.":::
   
1. Válassza **a Tovább** lehetőséget az **Áttekintés** lépésben, és adja meg a szervezet e-mail címét, amelyhez az Office-adatokat összesíteni fogja. Csak a felsorolt e-mail címekről származó adatok kerülnek feldolgozásra a megfelelő kommunikációhoz. A legjobb gyakorlat az e-mail csoportok használata, például *az egyesült államokbeli értékesítési csapat*, amelyek könnyen kezelhetők a alkalmazásban Office 365. A csoportokban lévő e-mail címek száma megoldódik és megjelenik. Az e-mail címek teljes számának legalább 2-nek kell lennie, és nem haladhatja meg a 2500-at.

   :::image type="content" source="media/enrichment-office-email-addresses.png" alt-text="Fiókkapcsolati e-mail címek.":::

1. Tekintse át a beleegyezési nyilatkozatot, jelölje be a **Egyetértek** jelölőnégyzetet, és válassza a Tovább **lehetőséget**.

1. Válassza ki a vevő adatkészlet, és válassza a Tovább **lehetőséget**.

1. Rendelje hozzá az ügyfél e-mail cím mezőjét, és válassza a Tovább **lehetőséget**.

1. Tekintse át a gazdagodás konfigurációját, adjon nevet a gazdagodásnak, és válassza a Gazdagodás **mentése lehetőséget** a gazdagodás mentéséhez.

## <a name="office-365-tenant-administrator-consent"></a>Office 365 bérlői rendszergazda hozzájárulása

Office 365 A gazdagodás aktiválásához a bérlő rendszergazdájának hozzájárulása szükséges. A gazdagodás mentésekor a rendszer e-mailt küld a Office 365 bérlői rendszergazdáknak, amely arra kéri őket, hogy vizsgálják felül és járuljanak hozzá ahhoz, hogy a Dynamics 365-alkalmazások felhasználhassák a vállalatok Office 365 adatait a szervezet **számára történő elemzések biztosításához**. A Office 365 bérlő rendszergazdája közvetlenül a felügyeleti konzolon Office 365 is jóváhagyhatja a beleegyezést **, ha a Szervezet** elemzési adatait választja.

## <a name="running-the-enrichment-for-the-first-time"></a>A gazdagodás első futtatása

Amikor a gazdagodás először kezdődik, miután a Office 365 bérlő adminisztrátora hozzájárult, megkezdődik az adatok letöltése Office 365. Ez a folyamat időbe telik. Az első dúsítási folyamat a tervek szerint hat órás késéssel fog megtörténni. Az adatok által lefedett napok számát a fiókkapcsolati áttekintő oldalon tekintheti meg a gazdagodás befejezése után. Nagy adatmennyiség esetén néhány nap múlva futtassa újra a gazdagodást. Biztosítja, hogy az adatok teljesek legyenek a teljes időablakban, ami egy év.

A folyamat elindításához válassza a Futtatás **lehetőséget** a Fiókkapcsolat konfigurációs lapján. Ezenkívül engedélyezheti, hogy a rendszer automatikusan futtassa a gazdagodást egy [ütemezett frissítés](system.md#schedule-tab) részeként. Alapértelmezés szerint a gazdagodás hetente egyszer fut.

Az Office-adatok méretétől függően több órát is igénybe vehet a gazdagodási futtatás befejezése.

A gazdagodás futtatásakor a Microsoft feldolgozza az adatokat a Office 365 megfelelőségi határokon belül, hogy összesített elemzéseket hozzon létre, amelyeket ezután hozzáad a Customer Insights környezethez. Az Ügyfélelemzés felhasználói számára nem válnak elérhetővé egyedi szintű adatok (például az e-mail vagy naptármeghívás törzse). 

[!INCLUDE [progress-details-pane](includes/progress-details-pane.md)]

## <a name="enrichment-results"></a>Bővítési eredmények

A gazdagodási folyamat futtatása után menj a **Gazdagodásaimba**, hogy áttekintsd a gazdagodás eredményeit. Megtalálja a gazdagodott ügyfelek teljes számát és a gazdagodás eredményeinek áttekintését. Ez magában foglalja a feldolgozott e-mailek és értekezletek számát, az adatok összesítésének napjainak számát és így tovább.

Talál egy diagramot is, amely tartalmazza a gazdagodott ügyfelek számát az idő múlásával, valamint a gazdagodási adatok előnézetét.  

:::image type="content" source="media/enrichment-office-results-overview.png" alt-text="Az eredmények előnézete a bővítési folyamat futtatása után.":::

A rendszer minden adatot a számla szintjéig összesít. A rendszer minden számlára kiszámítja az elkötelezettségi pontszámot, amely 0 és 100 között mozog. Az elkötelezettségi pontszám összetetten méri a fiók elkötelezettségét az e-mailek és értekezletek között a többi fiókhoz képest. Az alábbi lista a fiókkapcsolat gazdagodása által szolgáltatott összesített adatokat tartalmazza:



| Adat                                                                              | Oszlopnév                              |
| :-------------------------------------------------------------------------------- |:---------------------------------------- |
| Aktivitási pontszám                                                                  |  EngagementScore                         |
| A fiókba küldendő e-mailek száma                                                       |  NoOfEmails_ToAccount                    |
| Fiókból származó e-mailek száma                                                     |  NoOfEmails_FromAccount                  | 
| A fiók által kezdeményezett értekezletek száma                                           |  NoOfMeetings_FromAccount                | 
| A szervezet által kezdeményezett értekezletek száma                                 |  NoOfMeetings_ToAccount                  | 
| A szervezetből származó személyek száma a fiókkal rendelkező értekezleteken                  |  NoOfContactsInvolved_Meetings           | 
| A szervezetből származó személyek száma a fiókkal folytatott e-mailes beszélgetésekben       |  NoOfContactsInvolved_Emails             | 
| A szervezettel folytatott értekezleteken a fiókból származó személyek száma                  |  NoOfAccountContactsInvolved_Meetings    | 
| A szervezettel folytatott e-mailes beszélgetésekben a fiókból származó személyek száma       |  NoOfAccountContactsInvolved_Emails      | 
| Elkötelezettség kezdő dátuma (első e-mail vagy értekezlet az adatokban)                        |  EngagementStartDate                     | 
| Napok az utolsó e-mail óta                                                             |  DaysSinceLastEmail                      | 
| Napok az utolsó találkozó óta                                                           |  DaysSinceLastMeeting                    | 
| Az ülések átlagos időtartama                                                      |  AverageDuration_Of_Meetings             | 
| A fiókból származó e-mail válaszok átlagos időtartama                                    |  AverageDuration_Of_AccountEmailReplies  | 
| Összesítés kezdő dátuma                                                            |  AggregationStartDate                    | 
| Összesítési szint (év, hónap vagy hét)                                          |  Összesítési szint                        | 


Tekintse át a gazdagított adatokat az előnézeti szakaszban a Továbbiak **megtekintése jelölőnégyzet bejelölésével**. Megnyitja az *Office entitást*. A DataEntities Enrichment **csoportban** **felsorolt entitást is megtalálhatja** > **.** A gazdagodás konfigurálása során kiválasztott e-mail címek Active Directory-azonosítóit tartalmazó Office_UserEntity *is megtalálja*. 

## <a name="see-enrichment-data-on-the-customer-card"></a>A bővítési adatok megtekintése az ügyfélkártyán

A számlamegjegyzés az egyes ügyfélkártyákon is megtekinthető. Nyissa meg az **Ügyfelek** lehetőséget, és válassza ki az ügyfél profilját. Az ügyfélkártyán megtalálja a fiók elkötelezettségi pontszámát, az e-mailek teljes számát és az elmúlt évben összesített értekezletek teljes számát. Olyan diagramokat is talál, amelyek az e-mail és az értekezlet előzményeit mutatják.

:::image type="content" source="media/enrichment-office-customer-card.png" alt-text="Bővített adatokkal rendelkező ügyfél-kártya.":::

## <a name="create-segments-and-measures-based-on-the-enriched-data"></a>Szegmensek és intézkedések létrehozása a gazdagított adatok alapján

A gazdagított adatok felhasználhatók szegmensek és intézkedések létrehozására az alábbiakban részletezettek szerint. Például egy szegmens, amely tartalmazza az összes olyan ügyfelet, amelynek értéke meghaladja a 60-at az utolsó e-mail *óta eltelt napokban* és *az utolsó találkozó* óta eltelt napokban. Ez a szegmens elavult számlákat tartalmaz, amelyeket megpróbálhat újraaktiválni. 

## <a name="next-steps"></a>További lépések

[!INCLUDE [next-steps-enrichment](includes/next-steps-enrichment.md)]


[!INCLUDE [footer-include](includes/footer-banner.md)]
