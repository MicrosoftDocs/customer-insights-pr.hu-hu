---
title: Növekményes frissítés -alapú adatforrások esetén Power Query
description: Frissítse a nagy adatforrások új és frissített adatait a alapján Power Query.
ms.date: 12/06/2021
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: how-to
author: adkuppa
ms.author: adkuppa
manager: shellyha
searchScope:
- ci-system-schedule
- customerInsights
ms.openlocfilehash: 62632efda3c0c7e53fcdd8864b053ba93e2918bc
ms.sourcegitcommit: 73cb021760516729e696c9a90731304d92e0e1ef
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 02/25/2022
ms.locfileid: "8353685"
---
# <a name="incremental-refresh-for-data-sources-based-on-power-query"></a>Növekményes frissítés adatforrások alapján Power Query

Ez a cikk a növekményes frissítés konfigurálását ismerteti a Power Query.

Az adatforrások növekményes frissítése a következő előnyöket nyújtja:

- **Gyorsabb frissítések** - Csak a megváltozott adatok frissülnek. Előfordulhat például, hogy a régi adatkészletből csak az elmúlt öt napot frissíti.
- **Fokozott megbízhatóság** – Kisebb frissítésekkel nem kell kapcsolatot olyan sokáig fenntartania a változékony forrásoldali rendszerekkel így a kapcsolati problémák veszélye csökkenthető.
- **Csökkentett erőforrás- felhasználás** – A teljes adatok csak egy részhalmazának frissítése a számítási erőforrások hatékonyabb kihasználásával és a környezeti lábnyom csökkentésével jár.

## <a name="configure-incremental-refresh"></a>Növekményes frissítés konfigurálása

Célközönség elemzések lehetővé teszik a növekményes betöltést Power Query támogató adatforrások növekményes frissítését. Például a dátum és idő típusú mezőkkel rendelkező Azure SQL-adatbázisokat, amelyek jelzik az adatbejegyzések legutóbbi frissítését.

1. [Hozzon létre egy új adatforrás a alapján Power Query](connect-power-query.md).

1. Adjon nevet **a** adatforrás.

1. Válasszon ki egy adatforrás, amely támogatja a növekményes frissítést, például [az Azure SQL-adatbázist](/power-query/connectors/azuresqldatabase).

1. Jelölje ki a betölteni kívánt entitásokat vagy táblákat.

1. Hajtsa végre az átalakítási lépéseket, és válassza a **Tovább** lehetőséget.

1. A **Növekményes frissítés beállítása** párbeszédpanelen válassza a **Beállítás** lehetőséget **Növekményes frissítés beállításainak** megnyitásához. Ha a **Kihagyás** lehetőséget választja, akkor a adatforrás frissíti a teljes adatkészlet.
   > [!TIP]
   > A növekményes frissítést később is alkalmazhatja egy meglévő adatforrás szerkesztésével.

1. A **Növekményes frissítésbeállításai** alatt a adatforrás létrehozásakor kiválasztott összes entitásra vonatkozóan konfigurálja a növekményes frissítést.

   :::image type="content" source="media/incremental-refresh-settings.png" alt-text="Entitások konfigurálása egy adatforrásban növekményes frissítéshez.":::

1. Jelöljön ki egy entitást, és adja meg a következő adatokat:

   - **Adja meg az elsődlegeskulcsot**: Válasszon ki egy elsődleges kulcsot az entitáshoz vagy a táblához.
   - **Határozza meg a „legutóbbi frissítve”mezőt**: Ez a mező csak a dátum vagy idő típusú attribútumokat jeleníti meg. Jelöljön ki egy attribútumot, amely jelzi, hogy mikor frissítették utoljára a bejegyzéseket. A rendszer a növekményes frissítés időkeretébe tartozó bejegyzések azonosítására szolgál.
   - **Frissítések keresése minden**: Határozza meg, hogy a növekményes frissítés milyen hosszú időkerettel rendelkezzen.

1. Válassza a **Mentés** lehetőséget a adatforrás létrehozásának befejezéséhez. A kezdeti adatfrissítés teljes körű frissítés lesz. Ezt követően a növekményes adatfrissítés történik az előző lépésben beállítottak alapján.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
