---
title: 'Bővítse az ügyfélprofilokat a következő adatokkal Microsoft Office 365 : (előzetes verzió)'
description: Használjon védett adatokat, Microsoft Office hogy ügyfélprofiljait elkötelezettségi adatokkal gazdagítsa.
ms.date: 06/10/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: jodahl
ms.author: jodahl
manager: shellyha
ms.openlocfilehash: 75762afb70814c8a81c1574ee7ea1553a2048737
ms.sourcegitcommit: a97d31a647a5d259140a1baaeef8c6ea10b8cbde
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/29/2022
ms.locfileid: "9055677"
---
# <a name="enrich-customer-profiles-with-data-from-microsoft-office-365-preview"></a>Bővítse az ügyfélprofilokat a következő adatokkal Microsoft Office 365 : (előzetes verzió)

Használja a innen származó Microsoft Office 365 adatokat, hogy bővítse ügyfélfiók-profiljait az alkalmazásokon keresztüli Office 365 elköteleződésekkel kapcsolatos elemzésekkel. Az elköteleződési adatok e-mailből és értekezleti tevékenységből állnak, amelyeket a fiók szintjén összesítünk. Például az üzleti fiókból érkező e-mailek száma vagy a fiókkal való értekezletek száma. Az egyes felhasználókra vonatkozó adatok nem állnak rendelkezésre.

## <a name="supported-countries-or-regions"></a>Támogatott országok és régiók

Jelenleg a következő régiókat támogatjuk: Egyesült Királyság, Európa, Észak-Amerika.

## <a name="prerequisites"></a>Előfeltételek

- Aktív Office 365 felhőlicenc.
- [Egyesített ügyfélprofilok](customer-profiles.md) üzleti fiókok [alapján](work-with-business-accounts.md).
- A [Microsoft Dataverse Customer Insights-környezetben csatolt](create-environment.md#step-3-connect-to-microsoft-dataverse) szervezet.
- [Rendszergazdai](permissions.md#admin) engedélyek.
- Office 365 A bérlői rendszergazda hozzájárulása ahhoz, hogy az adatok felhasználásával Office 365 elemzéseket biztosítson **a szervezet** számára a Dynamics 365 alkalmazásokban.

## <a name="configure-the-enrichment"></a>Bővítés konfigurálása

1. Menjen a z **Adatok** > **Bővítés** menübe, és válassza a **Felfedezés** lapot.

1. Válassza az Adatok **gazdagítása lehetőséget** az **Account Engagement** csempén.

   :::image type="content" source="media/enrichment-office-tile.png" alt-text="Fiók elköteleződési csempe.":::

1. Tekintse át az áttekintést, majd válassza a Tovább **lehetőséget**.

1. Adja meg a szervezettől származó e-mail-címeket, amelyek Office-adatait összesíteni fogja. Csak a felsorolt e-mail-címekről származó adatokat dolgozzuk fel a releváns kommunikáció érdekében. Az ajánlott eljárás az e-mail csoportok, például *az egyesült államokbeli értékesítési csapat* használata, amelyet a Office 365. A csoportokban lévő e-mail címek száma megoldódik és megjelenik. Az e-mail címek teljes számának legalább 2-nek kell lennie, és nem haladhatja meg a 2,500-at.

   :::image type="content" source="media/enrichment-office-email-addresses.png" alt-text="Fiókkapcsolati e-mail címek.":::

1. Tekintse át és adja meg a bérlői rendszergazdai jóváhagyáshoz való [Office 365 hozzájárulását az Elfogadom](#office-365-tenant-administrator-consent) lehetőség kiválasztásával **.**

1. Válassza a **Következő** lehetőséget.

1. Válassza ki a **Kapcsolattartó adatkészlet**, és válassza ki a gazdagítani kívánt profilt. Válassza a **Következő** lehetőséget.

1. Térképezze fel a kapcsolattartói e-mail-cím mezőt, és válassza a Tovább **lehetőséget**.

1. **Adja meg a gazdagítás nevét** és a **Kimenet entitást**.

1. Válassza a **Bővítés mentése** lehetőséget, miután áttekintette a lehetőségeit.

1. Válassza a Bezárás **lehetőséget** a **Bővítések** lapra való visszatéréshez.

### <a name="office-365-tenant-administrator-consent"></a>Office 365 bérlői rendszergazdai hozzájárulás

A bővítés aktiválásához bérlői Office 365 rendszergazda hozzájárulása szükséges. A rendszer a gazdagítás mentésekor e-mailt küld a Office 365 bérlői rendszergazdáknak, amely arra kéri őket, hogy tekintsék át és járuljanak hozzá ahhoz, hogy a Dynamics 365-alkalmazások a vállalatok adatait felhasználhassák a szervezet Office 365 **számára betekintést nyújtva**. A Office 365 bérlői rendszergazda közvetlenül a felügyeleti konzolján Office 365 is hozzájárulhat a **szervezet** elemzések.

## <a name="running-the-enrichment-for-the-first-time"></a>A dúsítás első futtatása

Amikor a gazdagítás első alkalommal elindul, miután a Office 365 bérlői rendszergazda hozzájárulását adta, megkezdődik az adatok letöltése Office 365. Ez a folyamat eltart egy ideig. Az első dúsítási futtatásra hat órás késéssel kerül sor. Az adatok által lefedett napok számát a fiókjegyzet áttekintő oldalán láthatja a gazdagodás befejezése után. Nagy adatmennyiség esetén néhány nap múlva futtassa újra a gazdagítást. Ez biztosítja, hogy az adatok a teljes időablakban, azaz egy évig teljesek legyenek.

Az Office-adatok méretétől függően a gazdagítási futtatás befejezése több órát is igénybe vehet.

Ha gazdagítást futtat, a Microsoft a megfelelőségi határon belül feldolgozza az Office 365 adatokat, hogy összesített elemzéseket hozzon létre, amelyeket aztán hozzáad a Customer Insights-környezethez. Az egyes szinteken (például az e-mailek vagy naptármeghívók törzse) semmilyen adat nem válik elérhetővé a Customer Insights felhasználói számára.

Válassza a Futtatás **lehetőséget** a gazdagítási folyamat elindításához.

[!INCLUDE [progress-details-pane](includes/progress-details-pane.md)]

## <a name="view-enrichment-results"></a>Gazdagítási eredmények megtekintése

[!INCLUDE [enrichment-results](includes/enrichment-results.md)] Ez az *Office entitás*. A *Office_UserEntity* tartalmazza a gazdagítási konfiguráció során kiválasztott e-mail-címek Active Directory-azonosítóit.

:::image type="content" source="media/enrichment-office-results-overview.png" alt-text="Az eredmények előnézete a bővítési folyamat futtatása után.":::

Az összes adat a fiók szintjéig összesítve van. A rendszer minden fiókhoz kiszámít egy elkötelezettségi pontszámot, amely 0 és 100 között mozog. Az elköteleződési pontszám összetett mérőszámt biztosít az e-mailek és értekezletek fiókkapcsolatáról a többi fiókhoz képest. Az alábbi lista a fiókjegyzetség gazdagítása által biztosított összesített adatokat tartalmazza:

| Adat                                                                              | Oszlopnév                              |
| :-------------------------------------------------------------------------------- |:---------------------------------------- |
| Aktivitási pontszám                                                                  |  EngagementScore (Elkötelezettségpont)                         |
| A fiókba kerülő e-mailek száma                                                       |  NoOfEmails_ToAccount                    |
| A fiókból érkező e-mailek száma                                                     |  NoOfEmails_FromAccount                  |
| A számla által kezdeményezett ülések száma                                           |  NoOfMeetings_FromAccount                |
| A szervezet által kezdeményezett értekezletek száma                                 |  NoOfMeetings_ToAccount                  |
| A szervezetből származó személyek száma a fiókkal folytatott értekezleteken                  |  NoOfContactsInvolved_Meetings           |
| A szervezetből származó személyek száma a fiókkal folytatott e-mailes beszélgetésekben       |  NoOfContactsInvolved_Emails             |
| A fiókból származó személyek száma a szervezettel folytatott értekezleteken                  |  NoOfAccountContactsInvolved_Meetings    |
| A szervezettel folytatott e-mailes beszélgetések során a fiókból származó személyek száma       |  NoOfAccountContactsInvolved_Emails      |
| Elköteleződés kezdő dátuma (első e-mail vagy értekezlet az adatokban)                        |  EngagementStartDate                     |
| Az utolsó e-mail óta eltelt napok                                                             |  DaysSinceLastEmail                      |
| Napok az utolsó ülés óta                                                           |  DaysSinceLastMeeting                    |
| Az ülések átlagos időtartama                                                      |  AverageDuration_Of_Meetings             |
| A fiókból érkező e-mailes válaszok átlagos időtartama                                    |  AverageDuration_Of_AccountEmailReplies  |
| Összesítés kezdő dátuma                                                            |  AggregationStartDate                    |
| Összesítési szint (év, hónap vagy hét)                                          |  Aggregációs szint                        |

## <a name="see-enrichment-data-on-the-customer-card"></a>A bővítési adatok megtekintése az ügyfélkártyán

A fiókkapcsolat az egyes ügyfélkártyákon is megtekinthető. Nyissa meg az **Ügyfelek** lehetőséget, és válassza ki az ügyfél profilját. Az ügyfélkártyán megtalálja a fiók elköteleződési pontszámát, az e-mailek teljes számát és az értekezletek összesített teljes számát az elmúlt évben. Olyan diagramokat is talál, amelyek az e-maileket és az értekezlet-előzményeket mutatják.

:::image type="content" source="media/enrichment-office-customer-card.png" alt-text="Bővített adatokkal rendelkező ügyfél-kártya.":::

## <a name="next-steps"></a>További lépések

[!INCLUDE [next-steps-enrichment](includes/next-steps-enrichment.md)]
Például egy olyan szegmens, amely tartalmazza az összes olyan ügyfelet, amelynek értéke meghaladja a 60-at az utolsó e-mail óta eltelt napokban *és* az utolsó értekezlet *óta eltelt napokban*. Ez a szegmens elavult fiókokat tartalmaz, amelyeket megpróbálhat újraaktiválni.

[!INCLUDE [footer-include](includes/footer-banner.md)]
