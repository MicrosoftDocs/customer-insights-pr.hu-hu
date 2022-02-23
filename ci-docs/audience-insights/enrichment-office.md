---
title: Ügyfélprofilok gazdagítása a Microsoft Office 365
description: Használja a saját Microsoft Office adatait, hogy az ügyfélprofilokat elkötelezettségi adatokkal gazdagítsa.
ms.date: 12/03/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: jodahl
ms.author: jodahl
manager: shellyha
ms.openlocfilehash: a30e09b5ed491c8d36019b5f0d35e0a2f7a0199c
ms.sourcegitcommit: 48d799535fad84e8b63c80aef48b5c5e87628f58
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 12/03/2021
ms.locfileid: "7889776"
---
# <a name="enrich-customer-profiles-with-engagement-data-preview"></a>Ügyfélprofilok gazdagítása elkötelezettségi adatokkal (előzetes verzió)

A from-adatok segítségével Microsoft Office 365 gazdagíthatja ügyfélfiók-profiljait az alkalmazásokon keresztüli elkötelezettségekkel kapcsolatos Office 365 elemzésekkel. Az elkötelezettségi adatok e-mail és értekezlet-tevékenységből állnak, amelyet a fiók szintjén összesítünk. Például egy üzleti fiókból származó e-mailek száma vagy a fiókkal való találkozók száma. Az egyes felhasználókra vonatkozó adatok nem állnak rendelkezésre. 

Ez a gazdagodás a következő régiókban érhető el: Egyesült Királyság, Európa, Észak-Amerika.

## <a name="prerequisites"></a>Előfeltételek

A gazdagodás konfigurálásához a következő előfeltételeknek kell teljesülniük:

- Aktív Office 365 felhőlicence van.
- Az [üzleti fiókok alapján egységes ügyfélprofilokkal](customer-profiles.md)[rendelkezik](work-with-business-accounts.md).
- A Customer Insights környezethez csatolni kell egy [Microsoft Dataverse](create-environment.md#step-3-connect-to-microsoft-dataverse) szervezetet.
- [Rendszergazdai](permissions.md#administrator) engedélyekkel rendelkezik.
- A bérlői rendszergazdának beleegyezése van vagy kaphat, Office 365 Office 365 hogy adatokat használjon a Szervezet számára a **Dynamics** 365-alkalmazásokon belüli elemzések biztosításához.

## <a name="configure-the-enrichment"></a>Bővítés konfigurálása

1. A célközönség információin belül nyissa meg a következőt: **Adatok** > **Bővítés**.

1. Lépjen a **Felfedezés** fülre, és válassza az Adatok gazdagítása lehetőséget **a** **Fiókkapcsolat** csempén.

   :::image type="content" source="media/enrichment-office-tile.png" alt-text="Fiók elkötelezettség csempe.":::
   
1. Válassza a Tovább gombra **az** Áttekintés lépésben, és adja meg a szervezet **e**-mail-címét, amelyre az Office-adatokat összesíteni fogja. Csak a felsorolt e-mail címekről származó adatok lesznek feldolgozva a megfelelő kommunikációhoz. Az ajánlott eljárás az e-mail csoportok, például *az amerikai értékesítési csapat* használata, amelyek könnyen kezelhetők a Office 365. A csoportokban lévő e-mail címek száma megoldódik és megjelenik. Az e-mail címek teljes számának legalább 2-nek kell lennie, és nem haladhatja meg a 2500-at.

   :::image type="content" source="media/enrichment-office-email-addresses.png" alt-text="Fiókkapcsolati e-mail-címek.":::

1. Tekintse át a hozzájárulási nyilatkozatot, jelölje be a **Elfogadom** jelölőnégyzetet, és válassza a **Következő** lehetőséget.

1. Válassza ki a vevő adatkészlet, és válassza a **Következő** lehetőséget.

1. Térképezze fel a kapcsolattartó e-mail cím mezőjét, és válassza a **Következő** lehetőséget.

1. Tekintse át a dúsítási konfigurációt, adjon nevet a gazdagodásnak, és válassza **a dúsítás mentése lehetőséget** a gazdagítás mentéséhez.

## <a name="office-365-tenant-administrator-consent"></a>Office 365 bérlői rendszergazdai hozzájárulás

A Office 365 gazdagítás aktiválásához bérlői rendszergazda hozzájárulása szükséges. A gazdagítás mentésekor e-mailt küldünk Office 365 a bérlő rendszergazdáinak, amely arra kéri őket, hogy vizsgálják felül és járuljanak hozzá ahhoz, hogy a Dynamics 365-alkalmazások felhasználhassák a vállalatok Office 365 adatait a Szervezet **elemzési adatainak** biztosításához. A Office 365 bérlői rendszergazda közvetlenül a rendszergazdai konzolon is beleegyezhet Office 365 a Szervezet Elemzési adatai lehetőség kiválasztásával. **·**

## <a name="running-the-enrichment-for-the-first-time"></a>A gazdagodás első alkalommal

Amikor a gazdagítás első alkalommal elindul, miután a Office 365 bérlői rendszergazda beleegyezett, megkezdődik az adatok Office 365 letöltése. Ez a folyamat eltart egy ideig. Az első dúsítási futás a tervek szerint hat órás késéssel történik. A dúsítás befejezése után láthatja, hogy az adatok hány napot fednek le a fiókkapcsolatok áttekintő oldalán. Nagy adatmennyiséggel néhány nap múlva futtassa újra a gazdagodást. Biztosítja, hogy az adatok teljesek legyenek a teljes időablakban, ami egy év.

A folyamat elindításához válassza a Futtatás lehetőséget **a** Fiókkapcsolat konfigurációs lapján. Ezenkívül az ütemezett frissítés részeként a rendszer automatikusan futtathatja a [gazdagítást](system.md#schedule-tab). Alapértelmezés szerint a dúsítás hetente egyszer fut.

Az Office-adatok méretétől függően a gazdagítás futtatása több órát is igénybe vehet.

Gazdagítás futtatásakor a Microsoft feldolgozza az adatokat a Office 365 megfelelőségi határon belül, hogy összesített elemzéseket hozzon létre, amelyeket ezután hozzáad a Customer Insights környezethez. Az ügyfélelemzés felhasználói számára nem válnak elérhetővé egyéni szintű adatok (például bármely e-mail vagy naptármeghívás törzse). 

[!INCLUDE [progress-details-pane](../includes/progress-details-pane.md)]

## <a name="enrichment-results"></a>Bővítési eredmények

A dúsítási folyamat futtatása után látogasson el a **Gazdagodásomra,** hogy áttekintse a dúsítási eredményeket. Megtalálja a gazdagított ügyfelek teljes számát és áttekintést a dúsítási eredményekről. Ez magában foglalja a feldolgozott e-mailek és értekezletek számát, azon napok számát, amelyekre az adatokat összesítették, és így tovább.

Talál egy diagramot is a gazdagított ügyfelek számával az idő múlásával, és előnézetet a gazdagítási adatokból.  

:::image type="content" source="media/enrichment-office-results-overview.png" alt-text="Az eredmények előnézete a bővítési folyamat futtatása után.":::

Az összes adatot a fiók szintjére összesítik. A rendszer kiszámítja az elkötelezettségi pontszámot, amely minden fiókhoz 0 és 100 között mozog. Az elkötelezettségi pontszám összetetten méri a fiók elkötelezettségét az e-mailek és értekezletek között a többi fiókjához képest. Az alábbi lista tartalmazza a fiókkapcsolati gazdagodás által nyújtott összesített adatokat:



| Adat                                                                              | Oszlopnév                              |
| :-------------------------------------------------------------------------------- |:---------------------------------------- |
| Aktivitási pontszám                                                                  |  EngagementScore                         |
| A fiókba küldandó e-mailek száma                                                       |  NoOfEmails_ToAccount                    |
| A fiókból érkező e-mailek száma                                                     |  NoOfEmails_FromAccount                  | 
| A számlán kezdeményezett ülések száma                                           |  NoOfMeetings_FromAccount                | 
| A szervezet által kezdeményezett értekezletek száma                                 |  NoOfMeetings_ToAccount                  | 
| A szervezetből származó személyek száma a fiókkal rendelkező értekezleteken                  |  NoOfContactsInvolved_Meetings           | 
| A szervezetből származó személyek száma a fiókkal folytatott e-mail beszélgetésekben       |  NoOfContactsInvolved_Emails             | 
| A szervezettel folytatott értekezleteken a fiókból származó személyek száma                  |  NoOfAccountContactsInvolved_Meetings    | 
| A szervezettel folytatott e-mailes beszélgetésekben a fiókból származó személyek száma       |  NoOfAccountContactsInvolved_Emails      | 
| Elkötelezettség kezdő dátuma (az első e-mail vagy értekezlet az adatokban)                        |  EngagementStartDate                     | 
| Napok az utolsó e-mail óta                                                             |  DaysSinceLastEmail                      | 
| Napok a legutóbbi találkozó óta                                                           |  DaysSinceLastMeeting                    | 
| Az értekezletek átlagos időtartama                                                      |  AverageDuration_Of_Meetings             | 
| A fiókból érkező e-mail-válaszok átlagos időtartama                                    |  AverageDuration_Of_AccountEmailReplies  | 
| Összesítés kezdési dátuma                                                            |  ÖsszesítésStartDate                    | 
| Összesítési szint (év, hónap vagy hét)                                          |  Összesítési szint                        | 


Tekintse át a dúsított adatokat az **Előnézet szakasz További információk lehetőségével.** Megnyitja az *Office* entitást. Az adatkapcsolatok gazdagítás csoportjában felsorolt entitást **is** **·** > **megtalálhatja**. Megtalálja a Office_UserEntity *is*, amely tartalmazza a gazdagítás konfigurálása során kiválasztott e-mail-címek Active Directory-jának-eit. 

## <a name="see-enrichment-data-on-the-customer-card"></a>A bővítési adatok megtekintése az ügyfélkártyán

A fiókkapcsolat az egyes ügyfélkártyákon is megtekinthető. Nyissa meg az **Ügyfelek** lehetőséget, és válassza ki az ügyfél profilját. Az ügyfélkártyán megtalálja a fiók elkötelezettségi pontszámát, az e-mailek teljes számát és az elmúlt évben összesített értekezletek teljes számát. Olyan diagramokat is talál, amelyek az e-maileket és az értekezletek előzményeit mutatják.

:::image type="content" source="media/enrichment-office-customer-card.png" alt-text="Bővített adatokkal rendelkező ügyfél-kártya.":::

## <a name="create-segments-and-measures-based-on-the-enriched-data"></a>Szegmensek és intézkedések létrehozása a dúsított adatok alapján

A dúsított adatok felhasználhatók szegmensek és intézkedések létrehozására az alábbiakban részletezve. Például egy szegmens, amely tartalmazza az összes olyan ügyfelet, amely az utolsó e-mail óta napokig 60-ra több értéket *képvisel*, és *az utolsó találkozó óta eltelt* napokig. Ez a szegmens elavult fiókokat tartalmaz, amelyeket megpróbálhat újraaktiválni. 

## <a name="next-steps"></a>További lépések

[!INCLUDE [next-steps-enrichment](../includes/next-steps-enrichment.md)]


[!INCLUDE[footer-include](../includes/footer-banner.md)]
