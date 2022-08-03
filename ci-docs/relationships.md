---
title: Az entitások és entitásútvonalak közti kapcsolatok.
description: Kapcsolatok létrehozása és kezelése a több adatforrásból származó entitások között.
ms.date: 09/27/2021
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: conceptual
author: CadeSanthaMSFT
ms.author: cadesantha
manager: shellyha
searchScope:
- ci-semantic-mapping
- ci-entities
- ci-relationships
- ci-activities
- ci-activities-wizard
- ci-measures
- ci-segments
- ci-segment-builder
- ci-measure-builder
- ci-measure-template
- ci-permissions
- customerInsights
ms.openlocfilehash: e622e5fa0b5738e31db1c668d95312adbc4f7d36
ms.sourcegitcommit: ad74ace653db9a25fce4343adef7db1c9b0d8904
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/21/2022
ms.locfileid: "9183564"
---
# <a name="relationships-between-entities-and-entity-paths"></a>Az entitások és entitásútvonalak közti kapcsolatok.

Kapcsolatok összekapcsolják az entitásokat, és meghatározza az adatok grafikonját, ha az entitások közös azonosítón és idegen kulcson osztoznak. Ez az idegen kulcs egyik entitásról a másikra hivatkozhat. Az összekapcsolt entitások több adatforráson alapuló szegmensek és mérőszámok definiálását teszik lehetővé.

A kapcsolatoknak három típusa van: 
- Nem szerkeszthető rendszer- kapcsolatok a rendszer hoz létre az adategyesítési folyamat részeként
- A nem szerkeszthető öröklött kapcsolatok automatikusan létrejönnek az adatforrások betöltéséből
- A szerkeszthető egyéni kapcsolatok a felhasználók hozzák létre és konfigurálják

## <a name="non-editable-system-relationships"></a>Nem szerkeszthető rendszerkapcsolatok

Az adatok egyesítése során a rendszerkapcsolatok automatikusan jönnek létre az intelligens egyeztetés alapján. Ezek a kapcsolatok segítenek az ügyfélprofil rekordjainak összekapcsolásában más kapcsolódó entitások rekordjaival. Az alábbi ábra három rendszeralapú kapcsolat létrehozását szemlélteti. Az ügyfél entitása más entitásokkal van egyeztetve az egységes *Ügyfél* entitás előállításához.

:::image type="content" source="media/relationships-entities-merge.png" alt-text="Diagram az ügyfél entitás kapcsolati elérési útjaival három 1-n kapcsolattal.":::

- ***CustomerToContact* kapcsolat** az *Ügyfél* entitás és a *Kapcsolattartó* entitás között jött létre. Az *Ügyfél* entitás a **Contact_contactId** kulcsmezőjét kapcsolja össze a *Kapcsolattartó* entitás **contactId** kulcsmezőjével.
- A ***CustomerToAccount* kapcsolat** az *Ügyfél* entitás és a *Partner* entitás között jött létre. Az *Ügyfél* entitás **Account_accountID** kulcsmezőjét kapcsolja össze a *Partner* entitás **accountID** kulcsmezőjével.
- A ***CustomerToWebAccount* kapcsolat** az *Ügyfél* entitás és a *WebAccount* entitás között jött létre. Az *Ügyfél* entitás **WebAccount_webaccountID** kulcsmezőjét kapcsolja össze a *WebAccount* entitás **webaccountID** kulcsmezőjével.

## <a name="non-editable-inherited-relationships"></a>Nem szerkeszthető örökölt kapcsolatok

Az adatbetöltési folyamat során a rendszer ellenőrzi a meglévő kapcsolatokhoz tartozó adatforrásokat. Ha nincs kapcsolat, a rendszer automatikusan létrehozza azokat. Ezeket a kapcsolatokat a lefelé irányuló folyamatokban is használják.

## <a name="create-a-custom-relationship"></a>Egyéni kapcsolat létrehozása

A kapcsolat egy olyan *forrásentitásból* áll, amely tartalmazza az idegen kulcsot és egy *célentitást*, amelyre a forrás entitás idegen kulcsa mutat. 

1. Ugrás az **Adatok** > **Kapcsolatok** részre.

2. Válassza az **Új kapcsolat** lehetőséget.

3. Az **Új kapcsolat** ablaktáblában adja meg a következő információkat:

   :::image type="content" source="media/relationship-add.png" alt-text="Új kapcsolat oldalsóablaktábla üres beviteli mezőkkel.":::

   - **Kapcsolat neve**: A kapcsolat célját tükröző név. Példa: CustomerToSupportCase.
   - **Leírás**: A kapcsolat leírása.
   - **Forrásentitás**: A kapcsolat forrásaként használt entitás. Példa: SupportCase.
   - **Célentitás**: A kapcsolat céljaként használt entitás. Példa: Ügyfél.
   - **Forrás-számosság**: A forrás entitás számossága. A számosság egy halmaz lehetséges elemeinek számát írja le. Mindig a cél számossághoz kapcsolódik. Választhat az **Egy** és a **Sok** közül. Csak sok-az-egyhez és egy-az-egyhez kapcsolatok támogatottak.  
     - Sok az egyhez: Több forrásrekord is kapcsolódhat egy célrekordhoz. Példa: Több támogatási eset egyetlen ügyféltől.
     - Egy az egyhez: Egyetlen forrásrekord egyetlen célrekordhoz kapcsolódik. Példa: Egyetlen ügyfél hűségazonosítója.

     > [!NOTE]
     > Sok-a-sok kapcsolatokat lehet létrehozni két sok-az-egyhez kapcsolattal és egy összekötő entitással, amely összeköti a forrás entitást és a cél entitást.

   - **Cél számosság**: A cél entitásrekordok számossága.
   - **Forráskulcs mező**: Idegen kulcs mező a forrásentitásban. Példa: A SupportCase a CaseID-t **használja** idegen kulcsmezőként.
   - **Célkulcs mező**: A célentitás kulcsmezője. Példa: Az ügyfél a CustomerID-t **használja** kulcsmezőként.

4. Az egyéni folyamat létrehozásához válassza a **Mentés** lehetőséget.

## <a name="set-up-account-hierarchies"></a>Fiókhierarchiák beállítása

Azok a környezetek, amelyek úgy vannak konfigurálva, hogy üzleti fiókokat használjanak elsődleges célként, célközönség fiókhierarchiákat konfigurálhatnak a kapcsolódó üzleti fiókokhoz. Ez lehet például egy olyan vállalat, amely külön üzleti egységekkel rendelkezik.

A szervezetek fiókhierarchiákat hoznak létre a partnerek és a partnerek közötti kapcsolatok kezelésére. A Customer Insights támogatja a szülő-gyermek fiók hierarchiákat, amelyek már léteznek a betöltött ügyféladatokban. Például partnerek a Dynamics 365 Sales alkalmazásból. Ezek a hierarchiák a **kapcsolatok** oldalon konfigurálhatók.

1. Ugrás az **Adatok** > **Kapcsolatok** részre.
1. A **Fiókhierarchia** lap kiválasztása.
1. Az **Új fiókhierarchia** kiválasztása.
1. Adja meg a hierarchia nevét a **Számlahierarchia** ablaktáblán. A rendszer létrehoz egy nevet a kimeneti entitásnak, de Ön módosíthatja azt.
1. Válassza ki a fiókhierarchiát tartalmazó entitást. Ez általában ugyanabban az entitásban található, amely a partnerekből áll.
1. Válassza ki a **fiók UID-jét** és **a szülő UID-t** a kiválasztott entitásból.
1. Válassza a Mentés **lehetőséget** a fiókhierarchia véglegesítéséhez.

## <a name="manage-existing-relationships"></a>Meglévő kapcsolatok kezelése

**A kapcsolatok** oldalon megtekintheti az összes létrehozott kapcsolatok, azok forrásegyentitását, a célentitást és a számosságot.

:::image type="content" source="media/relationships-list.png" alt-text="A kapcsolatok és lehetőségek listája a Kapcsolatok oldal műveletsávjában.":::

Használja a **Szűrés szó szerint** vagy **a Keresés kapcsolatok** lehetőséget egy adott kapcsolat megkereséséhez. A meglévő kapcsolatok és számosságuk hálózati diagramjának megtekintéséhez válassza a Vizualizációk [**lehetőséget**](#explore-the-relationship-visualizer).

Válasszon ki egy kapcsolatot az elérhető műveletek megtekintéséhez:
- **Szerkesztés** : Az egyéni kapcsolatok tulajdonságainak frissítése a szerkesztőablakban, és módosítások mentése.
- **Törlés**: Egyéni kapcsolatok törlése.
- **Megtekintés**: A rendszer által létrehozott és örökölt kapcsolatok megtekintése.

### <a name="explore-the-relationship-visualizer"></a>Fedezze fel a kapcsolatvizualizálót

A kapcsolatvizualizálót megjelenít egy hálózati diagramot, hogy láthassa a meglévő kapcsolatok és azok számossága közötti kapcsolatot. Emellett a kapcsolati útvonalat is ábrázolja.

:::image type="content" source="media/relationship-visualizer.png" alt-text="Képernyőkép a kapcsolati vizualizáló hálózati diagramról a kapcsolódó entitások közötti kapcsolatokkal.":::

A nézet testreszabásához módosíthatja a dobozok helyzetét a húzásukkal a vásznon. További lehetőségek: 
- **Exportálás képként**:Az aktuális nézet mentése képfájlként.
- **Módosítás vízszintes/függőleges elrendezésre**: Módosítja az entitások és kapcsolatok elrendezését.
- **Szerkesztés** : Az egyéni kapcsolatok tulajdonságainak frissítése a szerkesztőablakban, és módosítások mentése.

## <a name="relationship-paths"></a>Kapcsolat elérési útjai

A kapcsolati elérési út azokat az entitásokat írja le, amelyek a forrásentitás és a célentitás közötti kapcsolattal kapcsolódnak. Olyan szegmens vagy mérték létrehozásakor használatos, amely az egyesített profilentitástól eltérő entitásokat is tartalmaz, és több lehetőség is van az egységes profilentitás elérésére. A különböző kapcsolati elérési utak eltérő eredményeket adhatnak.

Például az *eCommerce_eCommercePurchases* entitás a következő kapcsolatokkal rendelkezikaz *Ügyfél* entitáshoz:

- eCommerce_eCommercePurchases > Ügyfél
- eCommerce_eCommercePurchases > eCommerce_eCommerceContacts > POS_posPurchases > Ügyfél
- eCommerce_eCommercePurchases > eCommerce_eCommerceContacts > POS_posPurchases > loyaltyScheme_loyCustomers > Ügyfél

A kapcsolati elérési út határozza meg, hogy mely entitásokat használhatja amikor szabályokat hoz létre a mértékekhez vagy szegmensekhez. Ha a leghosszabb kapcsolati útvonalat választja, az valószínűleg kevesebb eredményt hoz, mivel az egyező rekordoknak az összes entitás részének kell lenniük. Ebben a példában az ügyfélnek az e-commerce(eCommerce_eCommercePurchases) elemen keresztül kell az értékesítési ponton (POS_posPurchases) vásárolnia az termékeket, és részt vennie a hűségprogramban (loyaltyScheme_loyCustomers). Az első lehetőség kiválasztásakor valószínűleg több eredményt kapna, mivel az ügyfeleknek csak egy további entitásban kell létezniük.

### <a name="direct-relationship"></a>Közvetlen kapcsolat

A kapcsolat **közvetlen kapcsolatnak** minősül, ha egy forrásentitás csak egy kapcsolaton keresztül hivatkozik egy célentitásra.

Ha például egy *eCommerce_eCommercePurchases* nevű tevékenységentitás az *eCommerce_eCommerceContacts* entitáshoz csak egy *ContactId* elemen keresztül kapcsolódik., az közvetlen kapcsolat.

:::image type="content" source="media/direct_Relationship.png" alt-text="A forrásentitás közvetlenül kapcsolódik a célentitáshoz.":::

#### <a name="multi-path-relationship"></a>Kapcsolat több elérési úttal

A **Kapcsolat több elérési úttal** a közvetlen kapcsolatok egy speciális típusa, amely a forrásentitást egynél több célentitáshoz kapcsolja.

Ha például egy *eCommerce_eCommercePurchases* nevű tevékenységentitás két célentitáshoz kapcsolódik, a *eCommerce_eCommerceContacts* és a *loyaltyScheme_loyCustomers* entitáshoz is, akkor ez több útvonalból álló kapcsolat.

:::image type="content" source="media/multi-path_relationship.png" alt-text="A forrásentitás több ugrásból álló kapcsolaton keresztül közvetlenül kapcsolódik egynél több célentitáshoz.":::

### <a name="indirect-relationship"></a>Követett kapcsolat

A kapcsolat **közvetett kapcsolatnak** minősül, ha egy forrásentitás egy vagy több további entitáshoz kapcsolódik, mielőtt hivatkozna egy célentitásra.

#### <a name="multi-hop-relationship"></a>Több ugrásos kapcsolat

A **több ugrásból álló kapcsolat** olyan *közvetett kapcsolat*, amely lehetővé teszi egy forrásentitásnak egy célentitáshoz való kapcsolását egy vagy több más közvetítő entitáson keresztül.

Ha például egy *eCommerce_eCommercePurchasesWest* nevű tevékenységentitás egy *eCommerce_eCommercePurchasesEast* nevű köztes entitáshoz csatlakozik, majd egy *eCommerce_eCommerceContacts* nevű célentitáshoz kapcsolódik, akkor ez több ugrásból álló kapcsolat.

:::image type="content" source="media/multi-hop_relationship.png" alt-text="A forrásentitás közvetlenül kapcsolódik egy köztes entitással rendelkező célentitáshoz.":::

### <a name="multi-hop-multi-path-relationship"></a>Kapcsolat több ugrással és több elérési úttal

A több ugrással és több elérési úttal rendelkező kapcsolatok használhatók **több ugrásból, több útvonalból álló kapcsolatok** létrehozásához. Ez a speciális típus egyesíti a **több ugrásból** és **több útvonalból** álló kapcsolatokat. Köztes entitások használatával egynél több célentitáshoz is kapcsolódhat.

Ha például egy *eCommerce_eCommercePurchasesWest* nevű tevékenységentitás egy *eCommerce_eCommercePurchasesEast* nevű köztes entitáshoz csatlakozik, majd a *eCommerce_eCommerceContacts* and *loyaltyScheme_loyCustomers* célentitásokhoz kapcsolódik, akkor ez több útvonalból álló kapcsolat.

:::image type="content" source="media/multi-hop_multi-path_relationship.png" alt-text="A forrásentitás közvetlenül kapcsolódik az egyik célentitáshoz, és egy köztes entitáson keresztül kapcsolódik egy másik célentitáshoz.":::

## <a name="next-step"></a>Következő lépés

A rendszer- és egyéni és kapcsolatok használhatók [szegmensek](segments.md) és [mértékek](measures.md) létrehozásához több adatforrás alapján, amelyek már nincsenek silózva.

[!INCLUDE [footer-include](includes/footer-banner.md)]
