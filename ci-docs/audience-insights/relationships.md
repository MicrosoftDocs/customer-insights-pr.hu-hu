---
title: Az entitások és entitásútvonalak közti kapcsolatok.
description: Kapcsolatok létrehozása és kezelése a több adatforrásból származó entitások között.
ms.date: 06/01/2020
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: MichelleDevaney
ms.author: midevane
manager: shellyha
ms.openlocfilehash: d5b9566ec88096fec31d8e164a51598159ec26d4
ms.sourcegitcommit: ece48f80a7b470fb33cd36e3096b4f1e9190433a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/03/2021
ms.locfileid: "6171167"
---
# <a name="relationships-between-entities"></a>Entitások közötti kapcsolatok

Kapcsolatok összekapcsolják az entitásokat, és meghatározza az adatok grafikonját, ha az entitások közös azonosítón és idegen kulcson osztoznak. Ez az idegen kulcs egyik entitásról a másikra hivatkozhat. Az összekapcsolt entitások több adatforráson alapuló szegmensek és mérőszámok definiálását teszik lehetővé.

A kapcsolatoknak három típusa van: 
- Nem szerkeszthető rendszerkapcsolat, amelyet a rendszer az adategyesítési folyamat részeként hoz létre
- Nem szerkeszthető öröklött kapcsolatok, amelyek automatikusan jönnek létre az adatforrások betöltésekor 
- Szerkeszthető egyéni kapcsolatok, amelyet a felhasználók hoztak létre és konfiguráltak

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

1. A célközönség információin belül nyissa meg a következőt **Adatok** > **Kapcsolatok**.

2. Válassza az **Új kapcsolat** lehetőséget.

3. Az **Új kapcsolat** ablaktáblában adja meg a következő információkat:

   :::image type="content" source="media/relationship-add.png" alt-text="Új kapcsolat oldalsóablaktábla üres beviteli mezőkkel.":::

   - **Kapcsolat neve**: A kapcsolat célját tükröző név. Példa: CustomerToSupportCase.
   - **Leírás**: A kapcsolat leírása.
   - **Forrásentitás**: A kapcsolat forrásaként használt entitás. Példa: SupportCase.
   - **Célentitás**: A kapcsolat céljaként használt entitás. Példa: Ügyfél.
   - **Forrás-számossága**: Adja meg a forrásentitás számosságát. A számosság egy halmaz lehetséges elemeinek számát írja le. Mindig a cél számossághoz kapcsolódik. Választhat az **Egy** és a **Sok** közül. Csak sok-az-egyhez és egy-az-egyhez kapcsolatok támogatottak.  
     - Sok az egyhez: Több forrásrekord is kapcsolódhat egy célrekordhoz. Példa: Több támogatási eset egyetlen ügyféltől.
     - Egy az egyhez: Egyetlen forrásrekord egyetlen célrekordhoz kapcsolódik. Példa: Egyetlen ügyfél hűségazonosítója.

     > [!NOTE]
     > Sok-a-sok kapcsolatokat lehet létrehozni két sok-az-egyhez kapcsolattal és egy összekötő entitással, amely összeköti a forrás entitást és a cél entitást.

   - **Cél számossága**: Válassza ki a Célentitás rekordjainak számosságát. 
   - **Forráskulcs mező**: A forrásentitás idegen kulcs mezője. Példa: A SupportCase a CaseID-t idegen kulcsmezőként használhatja.
   - **Cél kulcsmezője**: A célentitás kulcsmezője. Példa: Az ügyfél használhatja a **CustomerID** kulcsmezőt.

4. Az egyéni folyamat létrehozásához válassza a **Mentés** lehetőséget.

## <a name="view-relationships"></a>Kapcsolatok megtekintése

A Kapcsolatok oldal felsorolja az összes létrehozott kapcsolatot. Minden sor egy kapcsolatot jelent, amely a forrásentitásra, a célentitásra és a számosságra vonatkozó részleteket is tartalmazza. 

:::image type="content" source="media/relationships-list.png" alt-text="A kapcsolatok és lehetőségek listája a Kapcsolatok oldal műveletsávjában.":::

Ez az oldal számos lehetőséget kínál a meglévő és új kapcsolatokhoz: 
- **Új kapcsolat:** Válassza az [Egyéni kapcsolat létrehozása](#create-a-custom-relationship) elemet.
- **Vizualizáció**: [Fedezze fel a kapcsolatvizualizálót](#explore-the-relationship-visualizer), hogy láthassa a meglévő kapcsolatok és azok számosságának hálózati diagramját.
- **Szűrési szempont**: Válassza ki a listában megjelenítendő kapcsolatok típusát.
- **Kapcsolatok keresése**: Szöveges keresés használata a kapcsolatok tulajdonságai közötti kereséshez.

### <a name="explore-the-relationship-visualizer"></a>Fedezze fel a kapcsolatvizualizálót

A kapcsolatvizualizálót megjelenít egy hálózati diagramot, hogy láthassa a meglévő kapcsolatok és azok számossága közötti kapcsolatot.

A nézet testreszabásához módosíthatja a dobozok helyzetét a húzásukkal a vásznon.

:::image type="content" source="media/relationship-visualizer.png" alt-text="Képernyőkép a kapcsolati vizualizáló hálózati diagramról a kapcsolódó entitások közötti kapcsolatokkal.":::

Választható beállítások: 
- **Exportálás képként**:Az aktuális nézet mentése képfájlként.
- **Módosítás vízszintes/függőleges elrendezésre**: Módosítja az entitások és kapcsolatok elrendezését.
- **Szerkesztés** : Az egyéni kapcsolatok tulajdonságainak frissítése a szerkesztőablakban, és módosítások mentése.

## <a name="manage-existing-relationships"></a>Meglévő kapcsolatok kezelése 

A Kapcsolatok oldalon minden kapcsolatot egy sor képvisel. 

Válasszon ki egy kapcsolatot, és válasszon az alábbi lehetőségek közül: 
 
- **Szerkesztés** : Az egyéni kapcsolatok tulajdonságainak frissítése a szerkesztőablakban, és módosítások mentése.
- **Törlés**: Egyéni kapcsolatok törlése.
- **Megtekintés**: A rendszer által létrehozott és örökölt kapcsolatok megtekintése. 

## <a name="next-step"></a>Következő lépés

A rendszerkapcsolatok és az egyéni kapcsolatok több adatforráson alapuló [szegmensek létrehozására](segments.md) szolgálnak, amelyek már nincsenek elszigetelve.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
