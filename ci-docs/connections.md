---
title: Kapcsolatok (előzetes verzió) áttekintése
description: Egyéb szolgáltatásokhoz való kapcsolódás a Customer Insightsból.
ms.date: 08/04/2022
ms.reviewer: nikeller
ms.subservice: audience-insights
ms.topic: overview
author: m-hartmann
ms.author: mhart
manager: shellyha
searchScope:
- ci-connections
- customerInsights
ms.openlocfilehash: 8580dc7d90c75f66f73efc15f8e38f5e10fbb8a7
ms.sourcegitcommit: 49394c7216db1ec7b754db6014b651177e82ae5b
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/10/2022
ms.locfileid: "9245514"
---
# <a name="connections-preview-overview"></a>Kapcsolatok (előzetes verzió) áttekintése

A kapcsolatok kulcsfontosságúak az adatok Customer Insightsba és abból való megosztásának engedélyezéséhez. Minden kapcsolat adatmegosztást hoz létre egy adott szolgáltatással. A kapcsolatok segítségével konfigurálhatja a [külső bővítéseket, és](enrichment-hub.md) konfigurálhatja az [exportálásokat](export-destinations.md). Egy kapcsolat többször is használható. A Dynamics 365 Marketing alkalmazással például egy kapcsolat több exportálásra használható, és egy Leadspace-kapcsolat használható több adat bővítésére is.

## <a name="export-connections"></a>Kapcsolatok exportálása

Csak a rendszergazdák konfigurálhatnak új kapcsolatokat, de hozzáférést adhatnak [a közreműködőknek](#allow-contributors-to-use-a-connection-for-exports) a meglévő kapcsolatok használatához. A rendszergazdák határozzák meg, hogy hová irányíthatják az adatokat, a munkatársak határozzák meg, hogy a hasznos adatok és a gyakoriság hogyan illeszkedjenek az igényekhez.

## <a name="enrichment-connections"></a>Gazdagító kapcsolatok

Csak a rendszergazdák konfigurálhatnak új kapcsolatokat, de a létrehozott kapcsolatok mindig elérhetők a rendszergazdák és a közreműködők számára is. A rendszergazdák kezelik az azonosító adatokat, és ők egyeznek bele az adatátvitelekbe. A kapcsolatok ezután mind a rendszergazdák, mind a munkatársak általi bővítésekre használhatók.

## <a name="add-a-new-connection"></a>Egy új kapcsolat hozzáadása

### <a name="prerequisites"></a>Előfeltételek

- [Rendszergazdai engedélyek](permissions.md)
- Más Microsoft-szolgáltatások, ha vannak ilyenek, ugyanabba a szervezetbe tartoznak

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a Kapcsolat **hozzáadása lehetőséget**, és válassza ki a létrehozni kívánt kapcsolat típusát. Vagy lépjen a Felfedezés **lapra, és válassza a** Beállítás **lehetőséget** egy kapcsolatcsempén.

1. Adjon meg egy felismerhető nevet a **Megjelenítendő név** mezőben a kapcsolatnak. A név és a kapcsolat típusa írja le ezt a kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.

1. Adja meg a szükséges adatokat. A pontos mezők attól függnek, hogy melyik szolgáltatáshoz csatlakozik. Egy adott kapcsolattípus részleteiért tekintse meg a célszolgáltatásról szóló cikket.

1. Ha [saját Key Vaultja segítségével](use-azure-key-vault.md) tárolja el a titkos kódokat, aktiválja a **Key Vault használatát**, és válassza ki a megfelelő kulcsot a listából.

1. Tekintse át az adatvédelmet és a megfelelőséget, és válassza az Elfogadom **lehetőséget**.

1. Válassza a Mentés **lehetőséget** a kapcsolat létrehozásához.

### <a name="data-privacy-and-compliance"></a>Adatvédelem és megfelelőség

Ha engedélyezi Dynamics 365 Customer Insights az adatok harmadik feleknek vagy más Microsoft-termékeknek történő továbbítását, engedélyezi az adatok továbbítását a megfelelőségi határon túlra Dynamics 365 Customer Insights, beleértve a potenciálisan bizalmas adatokat, például a személyes adatokat is. A Microsoft az Ön utasítására továbbítja ezeket az adatokat, de Ön felelős annak biztosításáért, hogy a harmadik fél teljesítse az Ön esetleges adatvédelmi vagy biztonsági kötelezettségeit. További információ: [Microsoft adatvédelmi nyilatkozat](https://go.microsoft.com/fwlink/?linkid=396732).

A Dynamics 365 Customer Insights rendszergazda bármikor eltávolíthatja a kapcsolatot, hogy abbahagyja a funkció használatát.

## <a name="allow-contributors-to-use-a-connection-for-exports"></a>Engedélyezze a közreműködőknek a kapcsolat exportálásokhoz való használatát

Exportálási kapcsolat beállításakor vagy szerkesztésekor válassza ki, hogy mely felhasználók használhatják ezt az adott kapcsolatot az exportálások [meghatározásához](export-destinations.md). Alapértelmezés szerint a kapcsolat a rendszergazdai szerepkörrel rendelkező felhasználók számára érhető el. Módosítsa a Választható ki használhatja ezt a **kapcsolatbeállítást**, hogy közreműködő szerepkörrel rendelkező felhasználók használhassák ezt a kapcsolatot.

- A közreműködő nem tudják majd megtekinteni vagy szerkeszteni ezt a kapcsolatot. Csak a megjelenítendő név és annak típusát fogják látni az exportálás létrehozásakor.
- A kapcsolat megosztásával lehetővé teszi a közreműködők számára a kapcsolat használatát. A közreműködő a megosztott kapcsolatokat láthatják az exportálások beállításakor. Ők felügyelik az adott kapcsolatot használó minden exportálást.
- Ezt a beállítást megváltoztathatja, miközben a közreműködők által már meghatározott exportálásokat megtartja.

## <a name="manage-existing-connections"></a>Meglévő kapcsolatok kezelése

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. A Bővítés **vagy** exportálás **lapon megtekintheti a** gazdagítási vagy exportálási kapcsolatok listáját, a kapcsolat típusát, a létrehozás időpontját és azt, hogy kinek van hozzáférése. A kapcsolatok listáját bármely oszlop szerint rendezheti.

1. Válassza ki a kapcsolatot az elérhető műveletek megtekintéséhez.

   - **Szerkessze** a kapcsolatot.
   - [**Kapcsolat eltávolítása**](#remove-a-connection).

### <a name="remove-a-connection"></a>Kapcsolat eltávolítása

Ha az eltávolítandó kapcsolatot gazdagítások vagy exportálások használják, először válassza le vagy távolítsa el őket. Az eltávolítás párbeszédpanel végigvezeti a megfelelő gazdagításokhoz vagy exportálásokhoz.

> [!TIP]
> A deaktivált gazdagodások és a leválasztott exportálások inaktívvá válnak. Újraaktiválhatja őket, ha új kapcsolatot ad hozzájuk a [Bővítések](enrichment-hub.md) és [Exportálások](export-destinations.md) oldalon.

1. Menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

1. Válassza a **Gazdagítás** vagy **exportálás lapot**.

1. Válassza ki az eltávolítani kívánt kapcsolatot.

1. Válassza a legördülő menü **Eltávolítás** elemét. Megjelenik a jóváhagyást kérő párbeszéd.

   1. Ha ezt a kapcsolatot bővítések vagy exportálások használják, akkor a gombra kattintva láthatja, hogy pontosan mi használja a kapcsolatot.
      - **Exportálások:** Válassza az **Exportálás eltávolítása** vagy **a Kapcsolat leválasztása lehetőséget**. A kapcsolat leválasztása megtartja az exportálási konfigurációt, de addig nem fut, amíg egy másik kapcsolatot nem adnak hozzá.
      - **Bővítések:** Válassza a **bővítések törlését** vagy **deaktiválását**.
   1. Ha a kapcsolatnak már nincsenek függőségei, menjen vissza a **Rendszergazda** > **Kapcsolatok** lehetőséghez, és próbálja meg ismét eltávolítani a kapcsolatot.

1. Jelölje be az **Eltávolít** lehetőséget a törlés megerősítéséhez.

## <a name="set-up-connections-with-secrets-managed-by-your-own-key-vault"></a>Saját Key Vault által kezelt titkokkal való kapcsolat beállítása

Egyes kapcsolatoknak szüksége van titkokra, például API-kulcsokra vagy jelszavakra. Egyes kapcsolatok a saját Key Vaultban tárolt titkokat támogatják. További információ a támogatott kapcsolatokról és arról, hogyan állíthatja be [saját Key Vault a Customer Insightshoz](use-azure-key-vault.md).

[!INCLUDE [footer-include](includes/footer-banner.md)]
