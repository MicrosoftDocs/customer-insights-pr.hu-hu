---
title: Egyéb szolgáltatásokhoz való kapcsolódás a Customer Insightsból.
description: Adatok megosztása más szolgáltatásokkal.
ms.date: 04/09/2021
ms.reviewer: nikeller
ms.subservice: audience-insights
ms.topic: overview
author: m-hartmann
ms.author: mhart
manager: shellyha
searchScope:
- ci-connections
- customerInsights
ms.openlocfilehash: 10704e287960c1a9171031135ff8f78a45b6e965
ms.sourcegitcommit: b7dbcd5627c2ebfbcfe65589991c159ba290d377
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/27/2022
ms.locfileid: "8642648"
---
# <a name="connections-preview-overview"></a>Kapcsolatok (előzetes verzió) áttekintése

A kapcsolatok kulcsfontosságúak az adatok Customer Insightsba és abból való megosztásának engedélyezéséhez. Minden kapcsolat adatmegosztást hoz létre egy adott szolgáltatással. A kapcsolatok a [külső gyártótól származó bővítések](enrichment-hub.md) és az [exportálások konfigurációjának](export-destinations.md) az alapja. Egy kapcsolat többször is használható. A Dynamics 365 Marketing alkalmazással például egy kapcsolat több exportálásra használható, és egy Leadspace-kapcsolat használható több adat bővítésére is.

A kapcsolatok létrehozásához és megtekintéséhez menjen a **Rendszergazda** > **Kapcsolatok** lehetőségre.

A **Kapcsolatok** fül megjeleníti az összes aktív kapcsolatot. A listában minden kapcsolathoz egy sor tartozik. 

Gyors áttekintést és leírást kaphat, és a **Felfedezés** fülön megismerheti, hogy mikre lehet képes az egyes bővíthetőségi beállításokkal.

### <a name="exports"></a>Exportálások

Csak rendszergazdák konfigurálhatják az új kapcsolatokat, de hozzáférést adhatnak a munkatársaknak a meglévő kapcsolatok használatára. A rendszergazdák határozzák meg, hogy hová irányíthatják az adatokat, a munkatársak határozzák meg, hogy a hasznos adatok és a gyakoriság hogyan illeszkedjenek az igényekhez. További információért lásd a [Közreműködők engedélyezése, hogy az exportálásokhoz használjanak egy kapcsolatot](#allow-contributors-to-use-a-connection-for-exports).

### <a name="enrichments"></a>Bővítések

Csak rendszergazdák konfigurálhatják az új kapcsolatokat, de a létrehozott kapcsolatok mindig elérhetők mind a rendszergazdák, mind a munkatársak számára. A rendszergazdák kezelik az azonosító adatokat, és ők egyeznek bele az adatátvitelekbe. A kapcsolatok ezután mind a rendszergazdák, mind a munkatársak általi bővítésekre használhatók.

## <a name="add-a-new-connection"></a>Egy új kapcsolat hozzáadása

Kapcsolatok hozzáadásához [rendszergazdai engedélyekkel](permissions.md) kell rendelkeznie. Ha más Microsoft-szolgáltatásokhoz kapcsolódik, akkor azt feltételezzük, hogy mindkét szolgáltatás ugyanabban a szervezetben van.

1. Menjen a **Rendszergazda** > **Kapcsolatok (előzetes verzió)** lehetőségre.

1. Menjen a **Kapcsolatok** fülre.

1. Új kapcsolat létrehozásához válassza a **Kapcsolat hozzáadása** lehetőséget. Válassza ki a legördülő menüből, hogy milyen típusú kapcsolatot szeretne létrehozni.

1. Adja meg a szükséges adatokat a **Kapcsolat beállítása** ablaktáblán. 
   1. A **Megjelenítendő név** és a kapcsolat típusa ír le egy kapcsolatot. Javasoljuk, hogy olyan nevet válasszon, amely ismerteti a kapcsolat célját és szándékát.
   1. A pontos mezők attól függnek, hogy melyik szolgáltatáshoz kapcsolódik. A specifikus kapcsolattípus részleteiről a célszolgáltatásról szóló cikk nyújt részletes információt.
   1. Ha [saját Key Vaultja segítségével](use-azure-key-vault.md) tárolja el a titkos kódokat, aktiválja a **Key Vault használatát**, és válassza ki a megfelelő kulcsot a listából.

1. A kapcsolat létrehozásához válassza a **Mentés** lehetőséget.

A **Beállítás** lehetőséget is választhatja egy mozaikon a **Felderítés** lapon.

### <a name="allow-contributors-to-use-a-connection-for-exports"></a>Engedélyezze a közreműködőknek a kapcsolat exportálásokhoz való használatát

Az exportálási kapcsolat beállításakor és módosításakor megadhatja, hogy mely felhasználók használhatjak ezt a konkrét kapcsolatot az [exportálások](export-destinations.md) meghatározásához. Alapértelmezés szerint a rendszergazdai szerepkörrel rendelkező felhasználók számára érhető el a kapcsolat. Ezt a beállítást a **Válassza ki, hogy ki használhatja ezt a kapcsolatot** lehetőség alatt tudja megváltoztatni, és engedélyezheti a közreműködő szerepkörrel rendelkező felhasználóknak, hogy használják ezt a kapcsolatot.

- A közreműködő nem tudják majd megtekinteni vagy szerkeszteni ezt a kapcsolatot. Exportálás létrehozásakor csak a megjelenítendő név adatokat és azok típusát látják.
- A kapcsolat megosztásával lehetővé teszi a közreműködők számára a kapcsolat használatát. A közreműködő a megosztott kapcsolatokat láthatják az exportálások beállításakor. Ők felügyelik az adott kapcsolatot használó minden exportálást.
- Ezt a beállítást megváltoztathatja, miközben a közreműködők által már meghatározott exportálásokat megtartja.

## <a name="edit-a-connection"></a>Kapcsolat szerkesztése

1. Menjen a **Rendszergazda** > **Kapcsolatok (előzetes verzió)** lehetőségre.

1. Menjen a **Kapcsolatok** fülre.

1. Jelölje ki a szerkeszteni kívánt kapcsolat függőleges három pontját.

1. Válassza a **Szerkesztés** lehetőséget.

1. Módosítsa a frissíteni kívánt értékeket, majd válassza a **Mentés** lehetőséget.

## <a name="remove-a-connection"></a>Kapcsolat eltávolítása

Ha az eltávolítandó kapcsolatot bővítések vagy exportálások használják, előbb szét kell őket kapcsolni, vagy el kell távolítani. Az eltávolítási párbeszédpanel útmutatást nyújt a megfelelő bővítésekhez vagy exportálásokhoz. 

A szétkapcsolt bővítések és exportálások inaktívvá válnak. Újraaktiválhatja őket, ha új kapcsolatot ad hozzájuk a [Bővítések](enrichment-hub.md) és [Exportálások](export-destinations.md) oldalon.

1. Menjen a **Rendszergazda** > **Kapcsolatok (előzetes verzió)** lehetőségre.

1. Menjen a **Kapcsolatok** fülre.

1. Jelölje ki az eltávolítani kívánt kapcsolat függőleges három pontját.

1. Válassza a legördülő menü **Eltávolítás** elemét. Megjelenik a jóváhagyást kérő párbeszéd.

   1. Ha ezt a kapcsolatot bővítések vagy exportálások használják, akkor a gombra kattintva láthatja, hogy pontosan mi használja a kapcsolatot.
      - **Exportálások**: Kiválaszthatja az exportálás eltávolítását vagy bontását, hogy el tudja távolítani a kapcsolatot. Az exportálás bontása érdekében a rendszergazdák a **Szétkapcsolás** műveletet használhatják. Ez a művelet egyéni és több kijelölt exportáláshoz is elérhető. A kapcsolat szétkapcsolása megtartja az exportálási konfigurációs adatokat, de az mindaddig nem fut, amíg hozzá nem ad egy másik kapcsolatot.
      - **Bővítések:** Kiválaszthatja a bővítések eltávolítását vagy inaktiválását, hogy el tudja távolítani a kapcsolatot. 
   1. Ha a kapcsolatnak már nincsenek függőségei, menjen vissza a **Rendszergazda** > **Kapcsolatok** lehetőséghez, és próbálja meg ismét eltávolítani a kapcsolatot.

1. Jelölje be az **Eltávolít** lehetőséget a törlés megerősítéséhez.

## <a name="set-up-connections-with-secrets-managed-by-your-own-key-vault"></a>Saját Key Vault által kezelt titkokkal való kapcsolat beállítása

Egyes kapcsolatoknak szüksége van titkokra, például API-kulcsokra vagy jelszavakra. Egyes kapcsolatok a saját Key Vaultban tárolt titkokat támogatják. További információ a támogatott kapcsolatokról és arról, hogyan állíthatja be [saját Key Vault for Customer Insights szolgáltatását](use-azure-key-vault.md).
