---
title: Az entitások és entitásútvonalak közti kapcsolatok.
description: Kapcsolatok létrehozása és kezelése a több adatforrásból származó entitások között.
ms.date: 04/14/2020
ms.reviewer: mukeshpo
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: 295c372bb452e7c40aa950506dc494d4a2de1108
ms.sourcegitcommit: cf9b78559ca189d4c2086a66c879098d56c0377a
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/03/2020
ms.locfileid: "4406024"
---
# <a name="relationships-between-entities"></a>Entitások közötti kapcsolatok

A kapcsolatok segítséget nyújtanak az entitások összekapcsolásában, illetve az adatok gráfjának generálásában, amikor az entitások egy közös azonosítóval (idegen kulccsal) rendelkeznek, amellyel hivatkozni lehet az egyik entitásról a másikra. Az összekapcsolt entitások több adatforráson alapuló szegmensek és mérőszámok definiálását teszik lehetővé.

A kapcsolatoknak két típusa van: Nem szerkeszthető rendszerkapcsolatok, amelyek automatikusan jönnek létre, és egyéni kapcsolatok, amelyeket felhasználók hoznak létre és konfigurálnak.

Az egyeztetési és egyesítési folyamatok során a rendszerkapcsolatok a háttérben jönnek létre az intelligens egyeztetés alapján. Ezek a kapcsolatok segítenek az Ügyfélprofil rekordjainak összekapcsolásában más kapcsolódó entitások rekordjaival. A következő ábra három rendszerkapcsolat létrehozását mutatja be, amikor az ügyfél entitást további entitásokkal társítják, hogy előállítsák a végső ügyfélprofil entitást.

> [!div class="mx-imgBorder"]
> ![Kapcsolat létrehozása](media/relationships-entities-merge.png "Kapcsolat létrehozása")

- ***CustomerToContact* kapcsolat** jaz Ügyfél entitás és a Kapcsolattartó entitás között jött létre. Az Ügyfél entitás **Contact_contactId** kulcsmezőjét kapcsolja össze a Kapcsolattartó entitás **contactId** kulcsmezőjével.
- **_CustomerToAccount_ kapcsolat** az Ügyfél entitás és a Partner entitás között jött létre. Az Ügyfél entitás **Account_accountId** kulcsmezőjét kapcsolja össze a Partner entitás **accountId** kulcsmezőjével.
- **_CustomerToWebAccount_ kapcsolat** az Ügyfél entitás és a WebAccount entitás között jött létre. Az Ügyfél entitás **WebAccount_webaccountId** kulcsmezőjét kapcsolja össze a WebAccount entitás **webaccountId** kulcsmezőjével.

## <a name="create-a-relationship"></a>Egy kapcsolat létrehozása

Egyéni kapcsolatok definiálása a **kapcsolatok** oldalon történhet. Minden kapcsolat egy forrásoldali entitásból (az idegen kulcsot tartalmazó entitásból) és a céloldali entitásból (az a entitás, amelyre a forrásentitás idegen kulcsa mutat) áll.

1. A célközönség információin belül nyissa meg a következőt **Adatok** > **Kapcsolatok**.

2. Válassza az **Új kapcsolat** lehetőséget.

3. A **Kapcsolat hozzáadása** ablaktáblában adja meg a következő információkat:

   > [!div class="mx-imgBorder"]
   > ![Kapcsolati adatok megadása](media/relationships-add.png "Kapcsolati adatok megadása")

   - **Kapcsolat neve**: A kapcsolat célját tükröző név (például **AccountWebLogs**).
   - **Leírás**: A kapcsolat leírása.
   - **Forrásoldali entitás**: válassza ki azt az entitást, amelyet a kapcsolat forrásaként használ (például WebLog).
   - **Számosság**: Válassza ki a Forrásentitás rekordjainak számosságát. Például a „sok” azt jelenti, hogy több Webnapló-rekord egy WebAccount partnerhez kapcsolódik.
   - **Forrás kulcsmezője**: Ez a forrásentitás idegenkulcs-mezőjének felel meg. A WebLog például a **accountId** idegen kulcsmezőt tartalmazza.
   - **Céloldali entitás**: válassza ki azt az entitást, amelyet a kapcsolat céljaként használ (például WebAccount).
   - **Cél számossága**: Válassza ki a Célentitás rekordjainak számosságát. Például az „egy” azt jelenti, hogy több Webnapló-rekord egy WebAccount partnerhez kapcsolódik.
   - **Cél kulcsmezője**: Ez a mező a célentitás kulcsmezőjének felel meg. A WebAccount például a **accountId** kulcsmezőt tartalmazza.

> [!NOTE]
> Csak sok-az-egyhez és egy-az-egyhez kapcsolatok támogatottak. A sok-a-sokhoz kapcsolatok létrehozhatók két, sok-az-egyhez kapcsolat és egy kapcsolóentitás segítségével (egy entitás, amely a forrásoldali entitás és a céloldali entitás összekapcsolására szolgál).

## <a name="delete-a-relationship"></a>Kapcsolat törlése

1. A célközönség információin belül nyissa meg a következőt **Adatok** > **Kapcsolatok**.

2. Jelölje be a törölni kívánt kapcsolatok jelölőnégyzetét.

3. Válassza a **Törlés** lehetőséget a **kapcsolatok** tábla tetején.

4. Hagyja jóvá a törlést.

## <a name="next-step"></a>Következő lépés

A rendszerkapcsolatok és az egyéni kapcsolatok több adatforráson alapuló szegmensek létrehozására szolgálnak, amelyek már nincsenek elszigetelve. További tudnivalókat a [Szegmensek](segments.md) részben talál.
