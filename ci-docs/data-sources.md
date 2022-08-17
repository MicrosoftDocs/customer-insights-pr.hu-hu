---
title: Adatforrások áttekintése
description: További információ a különböző forrásokból származó adatok importálásáról és betöltéséről.
ms.date: 07/26/2022
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
ms.openlocfilehash: 591353bf1ba2f9ca05ddd137e1cf29dc0b0fba97
ms.sourcegitcommit: 49394c7216db1ec7b754db6014b651177e82ae5b
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 08/10/2022
ms.locfileid: "9245652"
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

Az adatforrások igény szerint automatikus frissítéssel vagy kézzel frissíthetők. [A helyszíni adatforrások](connect-power-query.md#add-data-from-on-premises-data-sources) a saját ütemezésük szerint frissülnek, amelyek az adatbetöltés során vannak beállítva. Csatolt adatforrások esetén az adatbetöltés az adott adatforrás elérhető legfrissebb adatokat használja fel.

**A Rendszergazdai** > **rendszerütemezés** > [**lapon**](schedule-refresh.md) konfigurálhatja a betöltött adatforrások rendszer által ütemezett frissítéseit.

Adatforrás igény szerinti frissítése:

1. Válassza az **Adatok** > **Adatforrások** lehetőséget.

1. Válassza ki a frissíteni kívánt adatforrás, majd válassza a Frissítés **lehetőséget**. Az adatforrás most már a manuális frissítésre váltja ki. Egy adatforrás frissítése frissíteni fogja az entitássémát és az adatokat a frissítésben megadott összes adatforrás számára.

1. Válassza ki az állapotot a **Folyamat részletei** panel megnyitásához és a folyamat megtekintéséhez. A feladat megszakításához válassza a Feladat **megszakítása lehetőséget** a panel alján.

[!INCLUDE [footer-include](includes/footer-banner.md)]
