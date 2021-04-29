---
title: A webes adatok integrálása az elkötelezettségi információkból a célközönséggel kapcsolatos információkba
description: Az ügyfelekre vonatkozó webes információkat az elkötelezettségi információkból eljuttathatja a célközönséggel kapcsolatos információkba.
ms.date: 12/17/2020
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: mukeshpo
ms.author: mukeshpo
ms.reviewer: mhart
manager: shellyha
ms.openlocfilehash: 9a4cb77bb4c6ef0d88b3f00802f66baab5520a07
ms.sourcegitcommit: aaa275c60c0c77c88196277b266a91d653f8f759
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 04/14/2021
ms.locfileid: "5896422"
---
# <a name="integrate-web-data-from-engagement-insights-with-audience-insights"></a>A webes adatok integrálása az elkötelezettségi információkból a célközönséggel kapcsolatos információkba

Az ügyfelek a napi tranzakciókat gyakran online, webhelyek segítségével végzik. A Dynamics 365 Customer Insights elkötelezettségi információk képessége egy hasznos megoldás, amely forrásként integrálja a webes adatokat. A tranzakciós, demográfiai vagy viselkedési adatok mellett a webes tevékenységeket is egységes ügyfélprofilban is láthatjuk. A profil segítségével további információkhoz juthatunk, például szegmensek, mértékek előrejelzések vagy a közönség aktivitása.

A cikk ismerteti, milyen lépésekkel lehet az ügyfelek webes tevékenységadatait áthozni az elkötelezettségi információkból a meglévő Célközönség információk környezetbe.

Ebben a példában egységes ügyfélprofilokat tartalmazó környezetet feltételezünk. A profilok egységesítettek a felmérések, a kiskereskedelmi értékesítés és a jegyrendszer forrásaival történt. Emellett megjeleníti az ügyfelek kapcsolódó tevékenységeit is. 

Most tudni szeretnénk, hogy egy ügyfél felkeresi-e webtulajdonságainkat, és meg szeretnénk érteni tevékenységeit. A tevékenységek közé tartoznak például a felkeresett webhelyek vagy a megtekintett termékoldalak egy e-mailben kapott hivatkozással.

## <a name="prerequisites"></a>Előfeltételek

Az elkötelezettségi információk adatainak integrálásához néhány előfeltételnek teljesülnie kell: 

- Az elkötelezettségi információk SDK integrálása a webhelyével. További információ: [Elsá lépések a webes SDK-val](../engagement-insights/instrument-website.md).
- Az elkötelezettségi információk webesemények exportálásához hozzáférés szükséges egy ADLS Gen 2 tárfiókhoz, amely a webes események adatainak betöltésére lesz felhasználva a célközönséggel kapcsolatos információkba. További tudnivalók: [Események exportálása](../engagement-insights/export-events.md).

## <a name="configure-refined-events-in-engagement-insights"></a>Kifinomult események konfigurálása az ügyfélkapcsolati információkban

Miután egy adminisztrátor tagolta a weboldalt az ügyfélkapcsolati információk SDK-val, *alapeseményeket* gyűjt a rendszer, amikor a felhasználó megtekint egy weboldalt, vagy rákattint valamire. Az alapesemények általában számos részletet tartalmaznak. A használt esettől függően az alapesemény adatainak csak egy részhalmazára van szükség. Az elkötelezettségi információk segítségével olyan *kifinomult eseményeket* hozhat létre, amelyek csak a kiválasztott alapesemény tulajdonságait tartalmazzák.     

További információkért lásd: [Kifinomult események létrehozása és módosítása](../engagement-insights/refined-events.md).

Szempontok a kifinomult események létrehozásához: 

- Adjon jól értelmezhető nevet a kifinomult eseménynek. A célközönséggel kapcsolatos információkban tevékenységnévként lesz használva.
- Válassza ki legalább az alábbi tulajdonságokat ahhoz, hogy tevékenységet hozzon létre a célközönség információkban: 
    - Signal.Action.Name - a tevékenység részleteit jelöli
    - Signal.User.Id - az ügyfélazonosítóval való leképezéshez használatos
    - Signal.View.Uri - webes címként használatos a szegmensek és vagy mértékek alapjaként
    - Signal.Export.Id - elsődleges kulcsként való használatra az eseményekhez
    - Lesiva.Timestamp - a tevékenység dátumának és időpontjának meghatározásához

Válassza ki a szűrőket, amelyek a használati eset szempontjából fontos eseményekre és oldalakra koncentrálnak. Ebben a példában az „E-mail promóció” műveletnevet használjuk.

## <a name="export-the-refined-web-events"></a>Exportálja a kifinomult webes eseményeket 

A kifinomult esemény definiálása után be kell állítani az eseményadatok exportálását egy Azure Data Lake Storage-tárhelyre, amely beállítható adatforrás betöltéséhez a célközönséggel kapcsolatos információkba. Az exportálások folyamatosan történnek, miközben az események a webes tulajdonságból áramlanak.

További tudnivalók: [Események exportálása](../engagement-insights/export-events.md).

## <a name="ingest-event-data-to-audience-insights"></a>Eseményadatok betöltése a célközönség információkba

Most, hogy definiálta a kifinomult eseményt, és konfigurálta az exportálását, áttértünk az adatok betöltésére célközönséggel kapcsolatos információkba. Új adatforrást kell létrehoznia a Common Data Model mappa alapján. Adja meg annak a tárfióknak az adatait, amelybe exportálja az eseményeket. A *default.cdm.json* fájlban válassza ki a betöltendő kifinomult eseményt, és hozza létre az entitást a célközönséggel kapcsolatos információkban.

További információ: [Kapcsolódás Common Data Model mappához egy Azure Data Lake-fiók használatával](connect-common-data-model.md)


## <a name="relate-refined-event-data-as-an-activity-of-a-customer-profile"></a>Kifinomult eseményadatok összekapcsolása az ügyfélprofil aktivitásaként

Az entitás betöltése után konfigurálhatja a tevékenységet az ügyfélprofilhoz.

További információ: [Ügyféltevékenységek](activities.md).

:::image type="content" source="media/web-event-activity.png" alt-text="Tevékenységek oldal kibontott Tevékenység szerkesztése ablaktáblával és kitöltött mezőkkel.":::

Konfigurálja az új tevékenységet a következő leképezésekkel: 

- **Elsődleges kulcs:** Signal.Export.Id, egy egyedi azonosító, amely az elkötelezettséggel kapcsolatos információkban minden eseményrekordhoz rendelkezésre áll. Ezt a tulajdonságot a program automatikusan generálja.

- **Időbélyegző:** Signal.Timestamp az eseménytulajdonságban.

- **Esemény:** Signal.Name, a követni kívánt esemény neve.

- **Webcím:** Signal.View.Uri, amely az eseményt létrehozó lap uri-jára hivatkozik.

- **Részletek:** Signal.Action.Name eseményhez társítani szükséges információkat képviseli. Ebben az esetben a kijelölt tulajdonság jelzi, hogy az esemény e-mail promócióhoz való.

- **Tevékenységtípus:** Ebben a példában a meglévő WebLog tevékenységtípust választjuk. Ez a beállítás jól használható szűrési beállítás előrejelzési modellek futtatására, illetve ezen tevékenységtípus alapján szegmensek létrehozására.

- **Kapcsolat beállítása:** Ez a fontos beállítás a tevékenységet meglévő ügyfélprofilokhoz társítja. **Signal.User.Id** az SDK készletben konfigurált azonosító, amely összegyűjtendő és az egyéb adatforrások felhasználói azonosítójára vonatkozik, és amely a célközönséggel kapcsolatos információkban konfigurált. Ebben a példában a Signal.User.Id és a RetailCustomers:CustomerRetailId közötti kapcsolatot konfiguráljuk, amely az adategyesítési folyamat leképezési lépésében meghatározott elsődleges kulcs volt.


A tevékenységek feldolgozása után áttekintheti az ügyfélrekordokat, és megnyithat egy ügyfélkártyát, és az idővonalon láthatja az aktivitási információkból származó tevékenységeket. 

> [!TIP]
> Ha olyan ügyfélazonosítót keres, amely rendelkezik a elkötelezettségi információk tevékenységgel, menjen az **Entitásokhoz**, és tekintse meg az UnifiedActivity entitás adatainak előnézetét. ActivityTypeDisplay = WebLog tartalmazza a fenti példában konfigurált elkötelezettségi információk tevékenységet. Másolja az ügyfélazonosítót az egyik rekordhoz és az azonosítóhoz az **Ügyfelek** oldalon.

## <a name="next-steps"></a>Következő lépések

Mostantól létrehozhat [szegmenseket](segments.md), [mértékeket](measures.md) és [előrejelzéseket](predictions.md), hogy hasznos kapcsolatot teremtsen az ügyfelekkel.


[!INCLUDE[footer-include](../includes/footer-banner.md)]