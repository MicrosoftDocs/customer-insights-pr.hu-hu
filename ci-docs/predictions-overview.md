---
title: Előrejelzések áttekintése
description: A Dynamics 365 Customer Insights alkalmazás által lefedett előrejelzési forgatókönyvek és lehetőségek.
ms.date: 09/29/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: overview
author: zacookmsft
ms.author: zacook
manager: shellyha
ms.openlocfilehash: f8c61d7530126890d26ce482a27a0f97a39e836c
ms.sourcegitcommit: be341cb69329e507f527409ac4636c18742777d2
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/30/2022
ms.locfileid: "9610193"
---
# <a name="predictions-overview"></a>Előrejelzések áttekintése

A Dynamics 365 Customer Insights számos olyan lehetőséggel rendelkezik, amelyek kihasználják az AI-t és a gépi tanulást az adatok előrejelzéséhez.

## <a name="out-of-box-models"></a>Beépített modellek

Az adatok előrejelzésével való elindulás legegyszerűbb módja az előre definiált modellek használata, amelyeket gyakran beépített modelleknek neveznek. Csak bizonyos adatokra és struktúrára van szükségük ahhoz, hogy gyorsan elemzéseket generáljanak. A következő modellek érhetők el:

# <a name="individual-consumers-b-to-c"></a>[Egyéni fogyasztók (B-to-C)](#tab/b2c)

- [Ügyfél élettartamra vetített értéke](predict-customer-lifetime-value.md) : Előrejelzi az ügyfélhez kapcsolódó potenciális bevételt a vállalkozással való teljes interakció során.
- [Termékajánlás](predict-product-recommendation.md) : Prediktív termékajánlásokat javasol a vásárlási viselkedés és a hasonló vásárlási mintákkal rendelkező ügyfelek alapján.
- [előfizetés-lemorzsolódás](predict-subscription-churn.md) Megjósolja, hogy fennáll-e az ügyfélnél annak veszélye, hogy a jövőben már nem az Ön vállalatának termékeit vagy szolgáltatásait veszi igénybe.
- [Tranzakciós adatváltozás](predict-transactional-churn.md): Előrejelzi, hogy egy adott ügyfél nem vásárolja-e meg többé az Ön termékeit vagy szolgáltatásait egy bizonyos időkeret.
- [Hangulatelemzés](sentiment-analysis.md): Elemzi az ügyfelek visszajelzéseinek hangulatát, és azonosítja a gyakran említett üzleti szempontokat.

# <a name="business-accounts-b-to-b"></a>[Üzleti számlák (B-to-B)](#tab/b2b)

- [Tranzakciós adatváltozás](predict-transactional-churn.md): Előrejelzi, hogy egy ügyfélfiók nem vásárolja-e meg többé a termékeket vagy szolgáltatásokat egy bizonyos időkeret.

---

> [!TIP]
> Javasoljuk, hogy rendszeresen frissítse a beépített modelleket frissített adatokkal, hogy azok pontosan tájékoztassák az üzleti használati esetet. Az adatok ad-hoc módon frissülnek, amikor a rendszer új vagy frissített adatforrásokat tölt be. A modellek azonban ebben az esetben csak újrapontozzák a teljesítményt, és továbbra is a meglévő betanítási adatokat használják.
>
> Konfiguráljon egy frissítési ütemezést **a** modell újraképzési ütemezésének beállításával a konfiguráció során. A modell újratanítja és újrapontozza ezt az ütemezést, amelyet bármikor módosíthat.

## <a name="azure-machine-learning-integration"></a>Azure Machine Learning integrációja

Ha egy szervezet már használ az Azure Machine Learning kísérleteken alapuló forgatókönyveket, a Customer Insights egyéni modelljei segítenek a pontkapcsolatban. Hozzon létre olyan munkafolyamatokat, amelyek segítenek kiválasztani azokat az adatokat, amelyekből elemzéseket érdemes generálni, és az eredményeket az egységes ügyfélprofilokhoz térképezi fel. További tudnivalókat az [Egyéni gépi tanulás modellek](custom-models.md) című rész tartalmaz.

## <a name="manage-existing-predictions"></a>Meglévő előrejelzések kezelése

Lépjen az **Intelligencia-előrejelzések** > **oldalra**. **A Saját előrejelzések** lapon tekintse meg a létrehozott előrejelzéseket, azok előrejelzés típusát, a kimeneti entitás nevét, állapotát, a előrejelzés legutóbbi szerkesztésének időpontját, valamint az adatok legutóbbi frissítését. Az előrejelzések listáját bármely oszlop szerint rendezheti.

Válasszon ki egy előrejelzés az elérhető műveletek megtekintéséhez.

:::image type="content" source="media/predictions.png" alt-text="Jóslataim oldala.":::

- **Szerkessze** a előrejelzés a tulajdonságainak módosításához.
- [**Frissítse**](#refresh-a-prediction) a előrejelzés, hogy a legfrissebb adatokat tartalmazza.
- **Tekintse meg** a előrejelzés részleteit.
- [**Bemeneti adat használhatósági jelentés**](#view-the-input-data-usability-report) a hibák, figyelmeztetések és ajánlások megtekintéséhez.
- **Törölje** a előrejelzés.

### <a name="refresh-a-prediction"></a>Előrejelzés frissítése

Az előrejelzések automatikus ütemezéssel frissíthetők, vagy igény szerint manuálisan frissíthetők. Az összes előrejelzés manuális frissítéséhez válassza az Összes **frissítése lehetőséget**. Egy előrejelzés manuális frissítéséhez jelölje ki, majd válassza a Frissítés **lehetőséget**. Az automatikus frissítés ütemezéséhez [lépjen a Rendszergazdai](schedule-refresh.md) rendszerütemezés **lapra** > **·** > **.**

[!INCLUDE [progress-details-include](includes/progress-details-pane.md)]

### <a name="view-the-input-data-usability-report"></a>Bemeneti adatok használhatósági jelentésének megtekintése

A bemeneti adatok használhatósági jelentése egységes képet ad azokról a hibákról és figyelmeztetésekről, amelyeket a gyári előrejelzések generálhatnak. Emellett javaslatokat is ad a modell teljesítményének javítására.

A jelentés a modell betanítási folyamatának befejezése után érhető el. Minden modellhez külön-külön jön létre, függetlenül attól, hogy sikeresen befejezte-e a betanítást vagy sem.

**Az Előrejelzéseim** lapon válassza ki a előrejelzés, majd válassza az Adatok használhatósági jelentésének **bevitele lehetőséget**. Vagy a előrejelzés részletek nézetében válassza a Beviteli adatok használhatósági jelentés **lehetőséget**.

:::image type="content" source="media/input-data-usability-report.png" alt-text="Példa egy bemeneti adatok használhatósági jelentésére, amely egy hibákat, figyelmeztetéseket és ajánlásokat megjelenítő táblázatot mutat be.":::

A jelentés a következőket tartalmazza:

- **Név:** A hiba, figyelmeztetés vagy javaslat leíró neve.
- **Lépés:** Modellfázis, betanítás vagy pontszám, az információ utal.
- **Állapot:** Az információ súlyossága (hiba, figyelmeztetés, ajánlás).
- **Oszlop neve:** Egy entitás oszlopa, amelyet módosítani kell a modell teljesítményének javítása érdekében.
- **Entitás neve:** Annak az entitásnak a neve, amelyet módosítani kell a modell teljesítményének javítása érdekében.
- **Részletek:** A hiba, figyelmeztetés vagy javaslat részletei.

[!INCLUDE [footer-include](includes/footer-banner.md)]
