---
title: Termékjavaslat-előrejelzés mintaútmutató
description: Használja ezt a mintamutatót, hogy kipróbálja a termékjavaslat előrejelzési modellt.
ms.date: 09/19/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: tutorial
author: m-hartmann
ms.author: wameng
manager: shellyha
searchScope:
- ci-predictions
- ci-create-prediction
- customerInsights
ms.openlocfilehash: 2b42a89e3f4ec8cf4f0769128b8536973365f1cb
ms.sourcegitcommit: be341cb69329e507f527409ac4636c18742777d2
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/30/2022
ms.locfileid: "9610147"
---
# <a name="product-recommendation-prediction-sample-guide"></a>Termékjavaslat-előrejelzés mintaútmutató

Ez az útmutató végigvezeti a mintaadatok felhasználásával előrejelzés termékajánlások teljes körű példáján. Javasoljuk, hogy ezt a előrejelzés [új környezetben próbálja ki](manage-environments.md).

## <a name="scenario"></a>Forgatókönyv

Contoso egy olyan cég, amely kiváló minőségű kávé- és kávéfőzőket gyárt. A termékeket a Contoso Coffee weboldalán keresztül értékesítik. Céljuk, hogy megértsék, mely termékeket ajánlják ki a visszatérő ügyfeleiknek. Ha tudják, hogy az ügyfelek **nagyobb valószínűséggel vásárolnak**, az segíthet nekik megtakarítani a marketingtörekvéseket azáltal, hogy bizonyos termékekre összpontosít.

## <a name="prerequisites"></a>Előfeltételek

- Legalább [közreműködői engedély](permissions.md) a Customer Insightsban.

## <a name="task-1---ingest-data"></a>1. Feladat - Adatok betáplálása

Tekintse át az adatbetöltésről [és](data-sources.md) a adatforrás való [csatlakozásról szóló cikkeket Power Query](connect-power-query.md). Az alábbi információk feltételezik, hogy általában ismeri az adatok betöltését.

### <a name="ingest-customer-data-from-ecommerce-platform"></a>Betáplált ügyféladatok az eCommerce platformról.

1. Hozzon létre egy e-kereskedelem **nevű Power Query adatforrás,** és válassza ki a **Text/CSV-összekötőt**.

1. Adja meg az e-kereskedelmi kapcsolatok URL-jét:https://aka.ms/ciadclasscontacts.

1. Az adatok szerkesztése közben válassza **az Átalakítás**, majd **az Első sor használata fejlécként** lehetőséget.

1. Frissítse az adattípust az alább felsorolt oszlopokhoz:
   - **SzületésiDátum**: Dátum
   - **CreatedOn**: Dátum/Idő/Zóna

   :::image type="content" source="media/ecommerce-dob-date.PNG" alt-text="A születési dátum átalakítása dátummá.":::

1. **A jobb oldali panel Név** mezőjében nevezze át a adatforrás eCommerceContacts **névre**.

1. **Mentse** az adatforrást.

### <a name="ingest-online-purchase-data"></a>Online vásárlási adatok betáplálása.

1. Adjon hozzá egy újabb adatforrást a megegyező **eCommerce** adatforráshoz. Válassza a **Text/CSV** csatlakozót újra.

1. Adja meg az online vásárlási adatok URL-címét https://aka.ms/ciadclassonline.

1. Az adatok szerkesztése közben válassza **az Átalakítás**, majd **az Első sor használata fejlécként** lehetőséget.

1. Frissítse az adattípust az alább felsorolt oszlopokhoz:
   - **PurchasedOn** : Dátum/Idő
   - **TotalPrice** : Pénznem

1. **Az oldalsó panel Név** mezőjében nevezze át a adatforrás eCommercePurchases **névre**.

1. **Mentse** az adatforrást.

### <a name="ingest-customer-data-from-loyalty-schema"></a>Ügyféladatok bevitele a hűségsémából

1. Hozzon létre egy LoyaltyScheme **nevű adatforrás,** és válassza ki a **Text/CSV-összekötőt**.

1. Adja meg a hűséges ügyfelek URL-címét https://aka.ms/ciadclasscustomerloyalty.

1. Az adatok szerkesztése közben válassza **az Átalakítás**, majd **az Első sor használata fejlécként** lehetőséget.

1. Frissítse az adattípust az alább felsorolt oszlopokhoz:
   - **SzületésiDátum**: Dátum
   - **JutalmazásiPontok**: Egész Szám
   - **KészültEkkor**: Dátum/Idő

1. **A jobb oldali panel Név** mezőjében nevezze át a adatforrás a következőre: **loyCustomers**.

1. **Mentse** az adatforrást.

## <a name="task-2---data-unification"></a>2. feladat - Adatok egységesítése

Tekintse át az adatok egyesítéséről [szóló cikket](data-unification.md). Az alábbi információk feltételezik, hogy általában ismeri az adatok egyesítését.

[!INCLUDE [sample-guide-unification](includes/sample-guide-unification.md)]

## <a name="task-3---create-transaction-history-activity"></a>3. feladat – Tranzakciós előzményekkel kapcsolatos tevékenység létrehozása

Tekintse át az ügyféltevékenységekről szóló [cikket](activities.md). Az alábbi információk feltételezik, hogy általában ismeri a tevékenységek létrehozását.

1. Hozzon létre egy eCommercePurchases nevű **tevékenységet az** eCommercePurchases:eCommerce *entitással és annak elsődleges kulcsával,* a PurchaseId azonosítóval **.**

1. Hozzon létre kapcsolatot az eCommercePurchases:eCommerce *és* az eCommerceContacts:eCommerce *között*, a ContactID-vel **, mint idegen kulccsal** a két entitás összekapcsolásához.

1. Válassza a TotalPrice lehetőséget **az EventActivity** és **a** PurchasedOn **lehetőséget a** TimeStamp **esetében**.

1. Válassza a SalesOrderLine **lehetőséget** a Tevékenység típusa beállításnál **,** és szemantikailag leképezi a tevékenységadatokat.

1. Futtassa a tevékenységet.

## <a name="task-4---configure-product-recommendation-prediction"></a>4. feladat – Termékjavaslat előrejelzés létrehozása

Ha az egyesített ügyfélprofilok rendelkezésre állnak, és létrehozott tevékenység, futtassa a termékajánlást előrejelzés.

1. Ugrás az Intelligencia-előrejelzések **oldalra** > **·**.

1. A Létrehozás **lapon válassza a** Modell **használata lehetőséget** a **Termékajánlások (előzetes verzió)** csempén.

1. Válassza az **Első lépések** lehetőséget.

1. Nevezze el a modellt **OOB termékjavaslatmodell-előrejelzés** értékre, és a kimeneti entitást **OOBProductRecommendationModelPrediction** értékre.

1. Válassza a **Következő** lehetőséget.

1. Modellbeállítások meghatározása:
   - **Termékek** száma: **5** annak meghatározásához, hogy hány terméket szeretne ajánlani ügyfeleinek.
   - **Várható ismételt vásárlások**: **Igen**, ha a korábban megvásárolt termékeket is felveszi a javaslatba.
   - **Visszatekintési ablak:** **365 nap** annak meghatározásához, hogy a modell milyen messzire nézzen vissza, mielőtt újra ajánlana egy terméket.

   :::image type="content" source="media/product-recommendation-model-preferences.png" alt-text="Modellbeállítások a termékjavaslati modellhez.":::

1. Válassza a **Következő** lehetőséget.

1. A Vásárlási előzmények **hozzáadása lépésben válassza az** Adatok **hozzáadása lehetőséget**.

1. Válassza a **SalesOrderLine** lehetőséget és az eCommercePurchases entitást, majd kattintson a Tovább **gombra**. A szükséges adatok automatikusan kitöltésre kerülnek a tevékenységből. Válassza a Mentés, **majd a** Tovább lehetőséget **.**

1. Hagyja ki a **Termékinformációk** hozzáadása és **a Termékszűrők** lépéseit, mert nem rendelkezünk termékinformációs adatokkal.

1. Az Adatfrissítések **lépésben válassza a** Havi **lehetőséget** a modell ütemezéséhez.

1. Válassza a **Következő** lehetőséget.

1. A részletek áttekintése után válassza a **Mentés és Futtatás** lehetőséget.

## <a name="task-5---review-model-results-and-explanations"></a>5. feladat – Modell eredmények és a magyarázatok áttekintése

Hagyja, hogy a modell teljesítse az adatok betanítását és pontozását. Tekintse át a [termékajánlási modell magyarázatait](predict-transactional-churn.md#view-prediction-results).

## <a name="task-6---create-a-segment-of-high-purchased-products"></a>6. feladat – A gyakran megvásárolt termékek szegmensének létrehozása

A modell futtatása új entitást hoz létre, amely listázva van az **Adatok** > **Entitások** helyen. Létrehozhat egy új szegmenst, a modell által létrehozott entitás alapján.

1. Az eredmény lapon válassza a **Szegmens létrehozása** lehetőséget.

1. Hozzon létre egy szabályt az **OOBProductRecommendationModelPrediction** entitás használatával, és határozza meg a szegmenst:
   - **Mező**: ProductID
   - **Érték**: Válassza ki az első három termékazonosítót

1. Válassza a Szegmens mentése **és** futtatása **lehetőséget**.

Most már van egy dinamikusan frissített szegmense, amely azonosítja azokat az ügyfeleket, akik érdeklődhetnek az öt leginkább ajánlott termék megvásárlása iránt. További információ: [Szegmensek létrehozása és kezelése](segments.md).

> [!TIP]
> A szegmensek **lapon is létrehozhat szegmenst egy előrejelzés modellhez az Új**, **majd a Létrehozás az** Intelligenciából **lehetőség kiválasztásával** > **·**. További információ: [Új szegmens létrehozása gyors szegmensekkel](segment-quick.md).

[!INCLUDE [footer-include](includes/footer-banner.md)]
