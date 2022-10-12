---
title: Adatforrások áttekintése
description: További információ a különböző forrásokból származó adatok importálásáról és betöltéséről.
ms.date: 09/29/2022
ms.subservice: audience-insights
ms.topic: overview
author: mukeshpo
ms.author: mukeshpo
ms.reviewer: v-wendysmith
manager: shellyha
searchScope:
- ci-data-sources
- ci-create-data-source
- customerInsights
ms.openlocfilehash: f89da3cf5b56e367bd673740f80cd82ec0907b28
ms.sourcegitcommit: be341cb69329e507f527409ac4636c18742777d2
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/30/2022
ms.locfileid: "9610055"
---
# <a name="data-sources-overview"></a>Adatforrások áttekintése

Dynamics 365 Customer Insights kapcsolatokat biztosít az adatok széles köréből való átviteléhez. A adatforrások összeskapcsolását gyakran nevezik *adatbetöltésnek*. Az adatok betöltése után egyesítheti [, elemzéseket hozhat létre, és aktiválhatja](data-unification.md) az adatokat a személyre szabott élmények létrehozásához.

## <a name="add-or-edit-data-sources"></a>Adatforrások hozzáadása vagy szerkesztése

Adatforrásokat csatolhat vagy importálhat a Customer Insights szolgáltatásba. Az alábbi hivatkozások az adatforrások hozzáadására és szerkesztésére vonatkozó utasításokat tartalmaznak.

**Adatforrás csatolása**

Ha a Microsoft egyik Azure-adatszolgáltatásában előkészített adatokkal rendelkezik, a Customer Insights egyszerűen csatlakozhat a adatforrás anélkül, hogy újra be kellene töltenie az adatokat. Válasszon az alábbi lehetőségek közül:
- [Azure Data Lake Storage(csv- vagy parkettafájlok egy Common Data Model mappában)](connect-common-data-model.md)
- [Azure Synapse Analytics(Lake adatbázisok)](connect-synapse.md)
- [Microsoft Dataverse data lake (adattó)](connect-dataverse-managed-lake.md)

**Importálás és átalakítás**

Ha helyszíni adatforrásokat, Microsoft- vagy külső adatokat használ, importálja és alakítsa át az adatokat összekötők használatával Power Query.
- [Power Query Csatlakozók](connect-power-query.md)

## <a name="review-data-sources"></a>Adatforrások áttekintése

Ha a környezet úgy van konfigurálva, hogy Customer Insights-tárolót használjon, és helyszíni adatforrásokat használ, adatfolyamokat használ Power Platform. Az Power Platform adatfolyamokkal megtekintheti a megosztott adatforrásokat és a mások által kezelt adatforrásokat. Az **Adatforrások** lap három szakaszban sorolja fel az adatforrásokat:
- **Megosztott**: Olyan adatforrások, amelyeket az összes Customer Insights-rendszergazda kezelhet. Power Platform az adatfolyamok, a saját tárfiókja és a Dataverse-managed data lake-hez való csatolás példák a megosztott adatforrásokra.
- **Általam** kezelt: Power Platform csak Ön által létrehozott és kezelt adatfolyamok. Más Customer Insights-rendszergazdák csak megtekinthetik ezeket az adatfolyamokat, de nem szerkeszthetik, frissíthetik vagy törölhetik őket.
- **Mások** kezelik: Power Platform más rendszergazdák által létrehozott adatfolyamok. Csak megtekintheti őket. Felsorolja az adatfolyam tulajdonosát, akivel bármilyen segítségért kapcsolatba léphet.
> [!NOTE]
> Az összes entitást más felhasználók is megtekinthetik és használhatják. Bár az adatforrások az őket létrehozó felhasználó tulajdonában vannak, az adatbetöltésből eredő entitásokat a Customer Insights minden felhasználója használhatja.

Ha a környezet nem használ Power Platform adatfolyamokat, az **Adatforrások** lap csak az összes adatforrás listáját tartalmazza. Nincsenek szakaszok.

## <a name="manage-existing-data-sources"></a>Meglévő adatforrások kezelése

Az **Adatforrások** > **lapon** megtekintheti az egyes betöltött adatforrás nevét, állapotát és azt, hogy az adatok utoljára mikor frissültek az adott forráshoz. Az adatforrások listáját rendezheti bármely oszlop szerint, vagy a keresőmező segítségével megkeresheti a kezelni kívánt adatforrás.

Válasszon ki egy adatforrás az elérhető műveletek megtekintéséhez.

:::image type="content" source="media/data_sources_showmore.png" alt-text="Adatforrás hozzáadva.":::

- [**Szerkessze**](#add-or-edit-data-sources) a adatforrás a tulajdonságainak módosításához.
- [**Frissítse**](#refresh-data-sources) a adatforrás, hogy a legfrissebb adatokat tartalmazza.
- [**Gazdagítsa**](data-sources-enrichment.md) a adatforrás az egyesítés előtt.
- **Törölje** a adatforrás. A adatforrás csak akkor törölhető, ha az adatokat nem használják fel semmilyen feldolgozáshoz, például egyesítéshez, elemzésekhez, aktiváláshoz vagy exportáláshoz.

## <a name="refresh-data-sources"></a>Adatforrások frissítése

Az adatforrások igény szerint automatikus frissítéssel vagy kézzel frissíthetők. [A helyszíni adatforrások](connect-power-query.md#add-data-from-on-premises-data-sources) a saját ütemezésük szerint frissülnek, amelyek az adatbetöltés során vannak beállítva. Hibaelhárítási tippekért lásd: [PPDF-alapú Power Query adatforrás frissítési problémák](connect-power-query.md#troubleshoot-ppdf-power-query-based-data-source-refresh-issues) elhárítása.

Csatolt adatforrások esetén az adatbetöltés az adott adatforrás elérhető legfrissebb adatokat használja fel.

**A Rendszergazdai** > **rendszerütemezés** > [**lapon**](schedule-refresh.md) konfigurálhatja a betöltött adatforrások rendszer által ütemezett frissítéseit.

Adatforrás igény szerinti frissítése:

1. Válassza az **Adatok** > **Adatforrások** lehetőséget.

1. Válassza ki a frissíteni kívánt adatforrás, majd válassza a Frissítés **lehetőséget**. Az adatforrás most már a manuális frissítésre váltja ki. Egy adatforrás frissítése frissíteni fogja az entitássémát és az adatokat a frissítésben megadott összes adatforrás számára.

1. Válassza ki az állapotot a **Folyamat részletei** panel megnyitásához és a folyamat megtekintéséhez. A feladat megszakításához válassza a Feladat **megszakítása lehetőséget** a panel alján.

## <a name="corrupt-data-sources"></a>Sérült adatforrások

A betöltött adatok sérült rekordokkal rendelkezhetnek, ami miatt az adatbetöltési folyamat hibákkal vagy figyelmeztetésekkel fejeződhet be.

> [!NOTE]
> Ha az adatbetöltés hibákkal fejeződik be, a adatforrás kihasználó későbbi feldolgozás (például egyesítés vagy tevékenység-létrehozás) kihagyásra kerül. Ha a betöltés figyelmeztetésekkel fejeződik be, a későbbi feldolgozás folytatódik, de előfordulhat, hogy néhány rekord nem szerepel benne.

Ezek a hibák a feladat részleteiben láthatók.

:::image type="content" source="media/corrupt-task-error.png" alt-text="A feladat részletei, amelyek sérült adathibát mutatnak.":::

A sérült rekordok a rendszer által létrehozott entitásokban jelennek meg.

### <a name="fix-corrupt-data"></a>Sérült adatok kijavítása

1. A sérült adatok megtekintéséhez lépjen az **Adatentitások** > **elemre**, és keresse meg a sérült entitásokat a **Rendszer** szakaszban. A sérült entitások elnevezési sémája: "DataSourceName_EntityName_corrupt".

1. Válasszon ki egy sérült entitást, majd az **Adatok** lapot.

1. Azonosítsa a rekord sérült mezőit és az okot.

   :::image type="content" source="media/corruption-reason.png" alt-text="Korrupciós ok." lightbox="media/corruption-reason.png":::

   > [!NOTE]
   > **Az adatentitások** > **csak** a sérült rekordok egy részét jelenítik meg. Az összes sérült rekord megtekintéséhez exportálja a fájlokat a tárfiók egyik tárolójába a [Customer Insights exportálási folyamatával](export-destinations.md). Ha saját tárfiókot használt, a tárfiókban a Customer Insights mappát is megtekintheti.

1. Javítsa ki a sérült adatokat. Az Azure Data Lake-adatforrások esetében például javítsa ki az adatokat a Data Lake Storage-ban, [vagy frissítse az adattípusokat a manifest/model.json fájlban](connect-common-data-model.md#common-reasons-for-ingestion-errors-or-corrupt-data). Adatforrások esetén Power Query javítsa ki a forrásfájlban lévő adatokat, és [javítsa ki az átalakítási lépés](connect-power-query.md#data-type-does-not-match-data) adattípusát a **Power Query - Lekérdezések** szerkesztése lapon.

Az adatforrás következő frissítésekor a kijavított bejegyzéseket a Customer Insights alkalmazásba be lesznek töltve és tovább lesznek küldve a későbbi folyamatoknak.

Például egy "születési" oszlop adattípusának beállítása "dátum". Egy ügyfélrekord ban a születésnap értéke „01/01/19777”. A rendszer ezt a rekordot sérültként jelöli meg. Módosítsa a születésnapot a forrásrendszerben "1977"-re. Az adatforrások automatikus frissítése után a mező most már érvényes formátumú, és a rekord el lesz távolítva a sérült entitásból.

[!INCLUDE [footer-include](includes/footer-banner.md)]
