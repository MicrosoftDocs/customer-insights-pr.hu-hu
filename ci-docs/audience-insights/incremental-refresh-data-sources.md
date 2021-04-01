---
title: A Power Queryn alapuló adatforrások növekményes frissítése
description: Az új és frissített adatok frissítése a nagyméretű adatforrásoknál Power Query alapján.
ms.date: 09/28/2020
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: adkuppa
ms.author: adkuppa
manager: shellyha
ms.openlocfilehash: 03f76bcfc7336d8430146e8a26ffa649c6a17db0
ms.sourcegitcommit: bae40184312ab27b95c140a044875c2daea37951
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/15/2021
ms.locfileid: "5596824"
---
# <a name="incremental-refresh-for-data-sources-based-on-power-query"></a>A Power Queryn alapuló adatforrások növekményes frissítése

Az adatforrások növekményes frissítése a következő előnyöket nyújtja:

- **Gyorsabb frissítések** - Csak a megváltozott adatok frissülnek. Előfordulhat például, hogy a régi adatkészletből csak az elmúlt öt napot frissíti.
- **Fokozott megbízhatóság** – Kisebb frissítésekkel nem kell kapcsolatot olyan sokáig fenntartania a változékony forrásoldali rendszerekkel így a kapcsolati problémák veszélye csökkenthető.
- **Csökkentett erőforrás- felhasználás** – A teljes adatok csak egy részhalmazának frissítése a számítási erőforrások hatékonyabb kihasználásával és a környezeti lábnyom csökkentésével jár.

## <a name="configure-incremental-refresh"></a>Növekményes frissítés konfigurálása

A célközönség-információk lehetővé teszi a növekményes betöltést támogató Power Query keresztül importált adatforrások növekményes frissítésére. Például a dátum és idő típusú mezőkkel rendelkező Azure SQL-adatbázisokat, amelyek jelzik az adatbejegyzések legutóbbi frissítését.

1. [Új adatforrás létrehozása a Power Query alapján ](connect-power-query.md).

1. Írja be az adatforrás nevét.

1. Jelöljön ki egy olyan adatforrás, amely támogatja a növekményes frissítést, például egy Azure SQL-adatbázist.

1. Jelölje ki a betölteni kívánt entitásokat vagy táblákat.

1. Hajtsa végre az átalakítási lépéseket, és válassza a **Tovább** lehetőséget.

1. A **Növekményes frissítés beállítása** párbeszédpanelen válassza a **Beállítás** lehetőséget **Növekményes frissítés beállításainak** megnyitásához. Ha a **Kihagyás** lehetőséget választja, akkor a adatforrás frissíti a teljes adatkészlet.
   > [!TIP]
   > A növekményes frissítést később is alkalmazhatja egy meglévő adatforrás szerkesztésével.

1. A **Növekményes frissítésbeállításai** alatt a adatforrás létrehozásakor kiválasztott összes entitásra vonatkozóan konfigurálja a növekményes frissítést.

   > [!div class="mx-imgBorder"]
   > ![Entitások konfigurálása egy adatforrásban növekményes frissítéshez](media/incremental-refresh-settings.png "Entitások konfigurálása egy adatforrásban növekményes frissítéshez")

1. Jelöljön ki egy entitást, és adja meg a következő adatokat:

   - **Adja meg az elsődlegeskulcsot**: Válasszon ki egy elsődleges kulcsot az entitáshoz vagy a táblához.
   - **Határozza meg a „legutóbbi frissítve”mezőt**: Ez a mező csak a dátum vagy idő típusú attribútumokat jeleníti meg. Jelöljön ki egy attribútumot, amely jelzi, hogy mikor frissítették utoljára a bejegyzéseket. A rendszer a növekményes frissítés időkeretébe tartozó bejegyzések azonosítására szolgál.
   - **Frissítések keresése minden**: Határozza meg, hogy a növekményes frissítés milyen hosszú időkerettel rendelkezzen.

1. Válassza a **Mentés** lehetőséget a adatforrás létrehozásának befejezéséhez. A kezdeti adatfrissítés teljes körű frissítés lesz. Ezt követően a növekményes adatfrissítés történik az előző lépésben beállítottak alapján.


[!INCLUDE[footer-include](../includes/footer-banner.md)]