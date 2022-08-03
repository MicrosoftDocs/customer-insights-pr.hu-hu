---
title: Növekményes frissítés az Azure Data Lake-adatforrásokhoz Power Query és az Azure Data Lake-adatforrásokhoz
description: Frissítse a nagyméretű adatforrások új és frissített adatait az Azure Data Lake adatforrásai alapján Power Query vagy Azure Data Lake-adatforrások alapján.
ms.date: 05/30/2022
ms.reviewer: v-wendysmith
ms.subservice: audience-insights
ms.topic: how-to
author: mukeshpo
ms.author: mukeshpo
manager: shellyha
searchScope:
- ci-system-schedule
- customerInsights
ms.openlocfilehash: de39743eb8728fac34e417724c5f73bf44309c89
ms.sourcegitcommit: 5807b7d8c822925b727b099713a74ce2cb7897ba
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 07/28/2022
ms.locfileid: "9207140"
---
# <a name="incremental-refresh-for-power-query-and-azure-data-lake-data-sources"></a>Növekményes frissítés az Azure Data Lake-adatforrásokhoz Power Query és az Azure Data Lake-adatforrásokhoz

Az adatforrások növekményes frissítése az Power Query Azure Data Lake alapján a következő előnyöket biztosítja:

- **Gyorsabb frissítések** - Csak a megváltozott adatok frissülnek. Előfordulhat például, hogy a régi adatkészletből csak az elmúlt öt napot frissíti.
- **Fokozott megbízhatóság** – Kisebb frissítésekkel nem kell kapcsolatot olyan sokáig fenntartania a változékony forrásoldali rendszerekkel így a kapcsolati problémák veszélye csökkenthető.
- **Csökkentett erőforrás- felhasználás** – A teljes adatok csak egy részhalmazának frissítése a számítási erőforrások hatékonyabb kihasználásával és a környezeti lábnyom csökkentésével jár.

## <a name="configure-incremental-refresh-for-data-sources-based-on-power-query"></a>Adatforrások növekményes frissítésének konfigurálása a következők alapján: Power Query

A Customer Insights lehetővé teszi a növekményes betöltésen keresztül Power Query importált adatforrások növekményes frissítését. Például a dátum és idő típusú mezőkkel rendelkező Azure SQL-adatbázisokat, amelyek jelzik az adatbejegyzések legutóbbi frissítését.

1. [Hozzon létre egy új adatforrás a következő alapján:Power Query](connect-power-query.md).

1. Válasszon ki egy olyan adatforrás, amely támogatja a növekményes frissítést, például [az Azure SQL-adatbázist](/power-query/connectors/azuresqldatabase).

1. Jelölje ki a betölteni kívánt entitásokat vagy táblákat.

1. Hajtsa végre az átalakítási lépéseket, és válassza a **Tovább** lehetőséget.

1. A **Növekményes frissítés beállítása** párbeszédpanelen válassza a **Beállítás** lehetőséget **Növekményes frissítés beállításainak** megnyitásához. Ha a **Kihagyás** lehetőséget választja, akkor a adatforrás frissíti a teljes adatkészlet.
   > [!TIP]
   > A növekményes frissítést később is alkalmazhatja egy meglévő adatforrás szerkesztésével.

1. A **Növekményes frissítésbeállításai** alatt a adatforrás létrehozásakor kiválasztott összes entitásra vonatkozóan konfigurálja a növekményes frissítést.

   :::image type="content" source="media/incremental-refresh-settings.png" alt-text="Konfigurálja a növekményes frissítési beállításokat.":::

1. Jelöljön ki egy entitást, és adja meg a következő adatokat:

   - **Adja meg az elsődlegeskulcsot**: Válasszon ki egy elsődleges kulcsot az entitáshoz vagy a táblához.
   - **Határozza meg a „legutóbbi frissítve”mezőt**: Ez a mező csak a dátum vagy idő típusú attribútumokat jeleníti meg. Jelöljön ki egy attribútumot, amely jelzi, hogy mikor frissítették utoljára a bejegyzéseket. A rendszer a növekményes frissítés időkeretébe tartozó bejegyzések azonosítására szolgál.
   - **Frissítések keresése minden**: Határozza meg, hogy a növekményes frissítés milyen hosszú időkerettel rendelkezzen.

1. Válassza a **Mentés** lehetőséget a adatforrás létrehozásának befejezéséhez. A kezdeti adatfrissítés teljes körű frissítés lesz. Ezt követően a növekményes adatfrissítés történik az előző lépésben beállítottak alapján.

## <a name="configure-incremental-refresh-for-azure-data-lake-data-sources"></a>Növekményes frissítés konfigurálása Azure Data Lake adatforrásokhoz

A Customer Insights lehetővé teszi a növekményes frissítést a .Azure Data Lake Storage Ha növekményes be- és frissítést szeretne használni egy entitáshoz, konfigurálja az entitást az Azure Data Lake adatforrás vagy újabb hozzáadásakor a adatforrás szerkesztésekor. Az entitás adatmappájának a következő mappákat kell tartalmaznia:

- **FullData**: Kezdeti rekordokat tartalmazó adatfájlokkal rendelkező mappa
- **Növekményes adatok**: Mappa dátum/időhierarchia mappákkal ééé/h/hd/hh **formátumban**, amely tartalmazza a növekményes frissítéseket. **A hh** a frissítések UTC óráját jelöli, és tartalmazza az **Upserts** és **a Deletes** mappákat. **Az Upserts** olyan adatfájlokat tartalmaz, amelyek frissítik a meglévő rekordokat vagy az új rekordokat. **A Törlések** olyan adatfájlokat tartalmaz, amelyeken el kell távolítani az eltávolítandó rekordokat.

1. Adatforrás hozzáadásakor vagy szerkesztésekor lépjen az **entitás Attribútumok** paneljére.

1. Tekintse át az attribútumokat. Győződjön meg arról, hogy a létrehozott vagy utoljára frissített dátumattribútum dateTime *Data* formátummal **és** Calendar.Date *Semantic* típussal **van** beállítva. Szükség esetén szerkessze az attribútumot, és válassza a Kész **lehetőséget**.

1. **Az Entitások** kiválasztása panelen szerkessze az entitást. A **Növekményes betöltés** jelölőnégyzet be van jelölve.

   :::image type="content" source="media/ADLS_inc_refresh.png" alt-text="Entitások konfigurálása egy adatforrásban növekményes frissítéshez.":::

   1. Keresse meg azt a gyökérmappát, amely a .csv vagy .parquet fájlokat tartalmazza a teljes adatokhoz, a növekményes adateredményekhez és a növekményes adattörlésekhez.
   1. Adja meg a teljes adat és a növekményes fájlok (\. csv vagy \. parketta) kiterjesztését.
   1. A .csv fájl esetén jelölje ki az oszlophatárolójelet, és ha a fájl első sorát oszlopfejlécként szeretné használni.
   1. Válassza a **Mentés** parancsot.

1. Az **Utolsó frissítés** beállításnál válassza ki a date timestamp attribútumot.

1. Ha az **Elsődleges kulcs** nincs kiválasztva, válassza ki az elsődleges kulcsot. Az elsődleges kulcs az entitás egyedi attribútuma. Ahhoz, hogy egy attribútum érvényes elsődleges kulcs legyen, az ne tartalmazzon ismétlődő értékeket, a hiányzó értékeket vagy a null értékeket. A karakterlánc, az egész szám és a GUID adattípus attribútumai elsődleges kulcsként támogatottak.

1. Válassza a Bezárás **lehetőséget** a panel mentéséhez és bezárásához.

1. Folytassa a adatforrás hozzáadásával vagy szerkesztésével.

[!INCLUDE [footer-include](includes/footer-banner.md)]
