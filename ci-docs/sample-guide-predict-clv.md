---
title: Ügyfélélettartam-érték (CLV) előrejelzés mintaútmutató
description: Ezzel a mintaútmutatóval próbálhatja ki az ügyfélélettartam-érték előrejelzése modellt.
ms.date: 09/15/2022
ms.reviewer: v-wendysmith
ms.subservice: audience-insights
ms.topic: tutorial
author: yashlundia
ms.author: yalundia
manager: shellyha
ms.openlocfilehash: fec43b279326daa17fb179181f5e310c99d48bb7
ms.sourcegitcommit: be341cb69329e507f527409ac4636c18742777d2
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/30/2022
ms.locfileid: "9609641"
---
# <a name="customer-lifetime-value-clv-prediction-sample-guide"></a>Ügyfélélettartam-érték (CLV) előrejelzés mintaútmutató

Ez az útmutató végigvezeti az ügyfél-élettartam értékének (CLV) teljes körű példáján, előrejelzés a Customer Insights-ban mintaadatok használatával. Javasoljuk, hogy ezt a előrejelzés [új környezetben próbálja ki](manage-environments.md).

## <a name="scenario"></a>Forgatókönyv

Contoso egy olyan cég, amely kiváló minőségű kávé- és kávéfőzőket gyárt. A termékeket a Contoso Coffee weboldalán keresztül értékesítik. A vállalat meg akarja érteni azt az értéket (bevételt), amelyet ügyfeleik a következő 12 hónapban generálhatnak. Ismerve az ügyfeleik várható értékét a következő 12 hónapra vonatkozóan segít nekik a marketingerőfeszítéseiket a nagy értékű ügyfelek felé irányítani.

## <a name="prerequisites"></a>Előfeltételek

- Legalább [közreműködői engedélyek](permissions.md).

## <a name="task-1---ingest-data"></a>1. Feladat - Adatok betáplálása

Tekintse át az adatbetöltésről [és](data-sources.md) a adatforrás való [csatlakozásról szóló cikkeket Power Query](connect-power-query.md). Az alábbi információk feltételezik, hogy általában ismeri az adatok betöltését.

### <a name="ingest-customer-data-from-ecommerce-platform"></a>Betáplált ügyféladatok az eCommerce platformról.

1. Hozzon létre egy e-kereskedelem **nevű Power Query adatforrás,** és válassza ki a **Text/CSV-összekötőt**.

1. Adja meg az URL-címét az eCommerce kapcsolattartóknak https://aka.ms/ciadclasscontacts.

1. Az adatok szerkesztése közben válassza **az Átalakítás**, majd **az Első sor használata fejlécként** lehetőséget.

1. Frissítse az adattípust az alább felsorolt oszlopokhoz:
   - **SzületésiDátum**: Dátum
   - **CreatedOn**: Dátum/Idő/Zóna

   :::image type="content" source="media/ecommerce-dob-date.PNG" alt-text="A születési dátum átalakítása dátummá.":::

1. **A jobb oldali ablaktábla Név** mezőjében nevezze át a adatforrás eCommerceContacts **névre**

1. **Mentse** az adatforrást.

### <a name="ingest-online-purchase-data"></a>Online vásárlási adatok betáplálása.

1. Adjon hozzá egy újabb adatforrást a megegyező **eCommerce** adatforráshoz. Válassza a **Text/CSV** csatlakozót újra.

1. Adja meg az URL-címét az **Online vásárlas** adataihoz https://aka.ms/ciadclassonline.

1. Az adatok szerkesztése közben válassza **az Átalakítás**, majd **az Első sor használata fejlécként** lehetőséget.

1. Frissítse az adattípust az alább felsorolt oszlopokhoz:
   - **PurchasedOn** : Dátum/Idő
   - **TotalPrice** : Pénznem

1. **Az oldalsó panel Név** mezőjében nevezze át a adatforrás eCommercePurchases **névre**.

1. **Mentse** az adatforrást.

### <a name="ingest-customer-data-from-loyalty-schema"></a>Ügyféladatok bevitele a hűségsémából

1. Hozzon létre egy LoyaltyScheme **nevű adatforrás,** és válassza ki a **Text/CSV-összekötőt**.

1. Adja meg a hűségügyfelek https://aka.ms/ciadclasscustomerloyalty URL-címét.

1. Az adatok szerkesztése közben válassza **az Átalakítás**, majd **az Első sor használata fejlécként** lehetőséget.

1. Frissítse az adattípust az alább felsorolt oszlopokhoz:
   - **SzületésiDátum**: Dátum
   - **JutalmazásiPontok**: Egész Szám
   - **KészültEkkor**: Dátum/Idő

1. **A jobb oldali panel Név** mezőjében nevezze át a adatforrás a következőre: **loyCustomers**.

1. **Mentse** az adatforrást.

### <a name="ingest-customer-data-from-website-reviews"></a>Tápláljon be ügyféladatokat a webhely értékelésekből.

1. Hozzon létre egy Webhely nevű **adatforrás,** és válassza ki a **Text/CSV-összekötőt**.

1. Adja meg a webhelyértékelések URL-jét https://aka.ms/CI-ILT/WebReviews.

1. Az adatok szerkesztése közben válassza **az Átalakítás**, majd **az Első sor használata fejlécként** lehetőséget.

1. Frissítse az adattípust az alább felsorolt oszlopokhoz:
   - **ReviewRating**: Decimális szám
   - **ÁttekintésDátuma**: Dátum

1. **A jobb oldali ablaktábla Név** mezőjében nevezze át a adatforrás Vélemények **névre**.

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

1. Adjon hozzá egy másik tevékenységet, és képezze le a mezők nevét a megfelelő mezőkre:
   - **Tevékenység entitás**: Vélemények:Webhely
   - **Elsődleges kulcs**: ReviewId
   - **Időbélyegző**: ReviewDate (ÁttekintésDate)
   - **Eseménytevékenység**: ActivityTypeDisplay
   - **További részletek**: Áttekintés
   - **Tevékenység típusa**: Felülvizsgálat

1. Futtassa a tevékenységet.

## <a name="task-4---configure-customer-lifetime-value-prediction"></a>4. feladat – Ügyfél élettartamra vetített értékének előrejelzése

Az egységes ügyfélprofilok és a létrehozott tevékenységek mellett futtassa az ügyfél élettartamának értékét (CLV) előrejelzés. Részletes lépésekért lásd: [Ügyfél élettartamra vetített érték előrejelzés](predict-customer-lifetime-value.md).

1. Ugrás az Intelligencia-előrejelzések **oldalra** > **·**.

1. A Létrehozás lapon válassza a **Modell** használata lehetőséget **az** Ügyfél élettartamának értéke **csempén.**

1. Válassza az **Első lépések** lehetőséget.

1. Nevezze el a modellt **OOB eCommerce CLV előrejelzés** névvel, a kimeneti entitás legyen **OOBeCommerceCLVPrediction**.

1. Modellbeállítások meghatározása:
   - **előrejelzés időszak**: **12 hónap vagy 1 év** annak meghatározására, hogy milyen messzire kell előre jelezni a jövőbe a CLV-t.
   - **Aktív vevők**: **Hagyja, hogy a modell kiszámítsa a vásárlási intervallumot**, amely az a időkeret, amelyben a vevőnek legalább egy tranzakcióval rendelkeznie kell ahhoz, hogy aktívnak minősüljön.
   - **Nagy értékű ügyfél**: manuálisan határozza meg a nagy értékű ügyfeleket az aktív ügyfelek felső 30%-aként **·**.

    :::image type="content" source="media/clv-model-preferences.png" alt-text="Beállítások lépés az CLV-modell interaktív élményében.":::

1. Válassza a **Következő** lehetőséget.

1. A **Szükséges adatok** lépésben válassza az **Adatok hozzáadása** lehetőséget a tranzakcióelőzmények adatainak megadásához.

    :::image type="content" source="media/clv-model-required.png" alt-text="Adja hozzá a szükséges adatlépést a CLV-modell irányított felhasználói élményéhez.":::

1. Válassza a **SalesOrderLine** lehetőséget és az eCommercePurchases entitást, majd kattintson a Tovább **gombra**. A szükséges adatok automatikusan kitöltésre kerülnek a tevékenységből. Válassza a Mentés, **majd a** Tovább lehetőséget **.**

1. A **További adatok (nem kötelező)** lépés lehetővé teszi további ügyféltevékenység-adatok hozzáadását, hogy több betekintést nyerjen az ügyfelekkel való interakciókba. Ebben a példában válassza az Adatok **hozzáadása lehetőséget**, és adja hozzá a webes felülvizsgálati tevékenységet.

1. Válassza a **Következő** lehetőséget.

1. Az Adatfrissítések **lépésben válassza a** Havi **lehetőséget** a modell ütemezéséhez.

1. Válassza a **Következő** lehetőséget.

1. A részletek áttekintése után válassza a **Mentés és Futtatás** lehetőséget.

## <a name="task-5---review-model-results-and-explanations"></a>5. feladat – Modell eredmények és a magyarázatok áttekintése

Hagyja, hogy a modell teljesítse az adatok betanítását és pontozását. Tekintse át a [CLV-modell eredményeit és magyarázatait](predict-customer-lifetime-value.md#view-prediction-results).

## <a name="task-6---create-a-segment-of-high-value-customers"></a>6. feladat - Nagy értékű ügyfelek szegmensének létrehozása

A modell futtatása új entitást hoz létre, amely listázva van az **Adatok** > **Entitások** helyen. Új ügyfélszegmenst hozhat létre a modell által létrehozott entitás alapján.

1. Az eredmény lapon válassza a **Szegmens létrehozása** lehetőséget.

1. Hozzon létre egy szabályt az **OOBeCommerceCLVPrediction entitás használatával,** és határozza meg a szegmenst:
   - **Mező**: CLVScore
   - **Operátor**: nagyobb, mint
   - **Érték**: 1500

1. Válassza a Szegmens mentése **és** futtatása **lehetőséget**.

Most már van egy szegmens, amely azonosítja azokat az ügyfeleket, akik az előrejelzések szerint több mint 1500 dollár bevételt generálnak a következő 12 hónapban. Ez a szegmens dinamikusan frissül, ha több adatot vesz fel. További információ: [Szegmensek létrehozása és kezelése](segments.md).

> [!TIP]
> A szegmensek **lapon is létrehozhat szegmenst egy előrejelzés modellhez az Új**, **majd a Létrehozás az** Intelligenciából **lehetőség kiválasztásával** > **·**. További információ: [Új szegmens létrehozása gyors szegmensekkel](segment-quick.md).

[!INCLUDE [footer-include](includes/footer-banner.md)]
