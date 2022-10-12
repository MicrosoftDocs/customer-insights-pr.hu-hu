---
title: Tranzakcionális lemorzsolódási előrejelzési példamutató
description: Használja ezt a példamutatót, hogy kipróbálja a mezőn kívüli lemorzsolódás-előrejelzési modellt.
ms.date: 09/19/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: tutorial
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: 0ccc32b6e5e96adf6f2fa8c6d52960a07d1513f3
ms.sourcegitcommit: be341cb69329e507f527409ac4636c18742777d2
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/30/2022
ms.locfileid: "9609687"
---
# <a name="transactional-churn-prediction-sample-guide"></a>Tranzakcionális lemorzsolódási előrejelzési példamutató

Ez az útmutató elmagyarázza Önnek a tranzakciós adatváltozás teljes körű példáját előrejelzés mintaadatok felhasználásával. Javasoljuk, hogy ezt a előrejelzés [új környezetben próbálja ki](manage-environments.md).

## <a name="scenario"></a>Forgatókönyv

Contoso egy olyan cég, amely kiváló minőségű kávé- és kávéfőzőket gyárt. A termékeket a Contoso Coffee weboldalán keresztül értékesítik. Céljuk, hogy megtudják, mely ügyfelek azok, akik általában rendszeresen vásárolnak termékeket, mégis az elkövetkezendő 60 napon megszűnnek aktív ügyfelek lenni. Tudva, melyek azok az ügyfelek, akik **várhatóan a lemorzsolódnak**, segítséget nyújthatnak a marketing-erőfeszítések megtakarításában, azzal, hogy megtartják őket.

## <a name="prerequisites"></a>Előfeltételek

- Legalább [közreműködői engedélyek](permissions.md).

## <a name="task-1---ingest-data"></a>1. Feladat - Adatok betáplálása

Tekintse át az adatbetöltésről [és](data-sources.md) a adatforrás való [csatlakozásról szóló cikkeket Power Query](connect-power-query.md). Az alábbi információk feltételezik, hogy általában ismeri az adatok betöltését.

### <a name="ingest-customer-data-from-ecommerce-platform"></a>Betáplált ügyféladatok az eCommerce platformról.

1. Hozzon létre egy e-kereskedelem **nevű adatforrás,** és válassza ki a **Text/CSV-összekötőt**.

1. Adja meg az URL-címét az eCommerce kapcsolattartóknak https://aka.ms/ciadclasscontacts.

1. Az adatok szerkesztése közben válassza **az Átalakítás**, majd **az Első sor használata fejlécként** lehetőséget.

1. Frissítse az adattípust az alább felsorolt oszlopokhoz:

   - **SzületésiDátum**: Dátum
   - **CreatedOn**: Dátum/Idő/Zóna

   :::image type="content" source="media/ecommerce-dob-date.PNG" alt-text="DoB átalakítása Dátummá.":::

1. **A jobb oldali ablaktábla Név** mezőjében nevezze át a adatforrás eCommerceContacts **névre**

1. Az adatforrások mentése.

### <a name="ingest-online-purchase-data"></a>Online vásárlási adatok betáplálása.

1. Adjon hozzá egy újabb adatforrást a megegyező **eCommerce** adatforráshoz. Válassza a **Text/CSV** csatlakozót újra.

1. Adja meg az online vásárlási adatok URL-címét https://aka.ms/ciadclassonline.

1. Az adatok szerkesztése közben válassza **az Átalakítás**, majd **az Első sor használata fejlécként** lehetőséget.

1. Frissítse az adattípust az alább felsorolt oszlopokhoz:

   - **PurchasedOn** : Dátum/Idő
   - **TotalPrice** : Pénznem

1. **A jobb oldali panel Név** mezőjében nevezze át a adatforrás eCommercePurchases **névre**.

1. Az adatforrások mentése.

### <a name="ingest-customer-data-from-loyalty-schema"></a>Ügyféladatok bevitele a hűségsémából

1. Hozzon létre egy LoyaltyScheme **nevű adatforrás,** és válassza ki a **Text/CSV-összekötőt**.

1. Adja meg az URL-címét az eCommerce kapcsolattartóknak https://aka.ms/ciadclasscustomerloyalty.

1. Az adatok szerkesztése közben válassza **az Átalakítás**, majd **az Első sor használata fejlécként** lehetőséget.

1. Frissítse az adattípust az alább felsorolt oszlopokhoz:

   - **SzületésiDátum**: Dátum
   - **JutalmazásiPontok**: Egész Szám
   - **KészültEkkor**: Dátum/Idő

1. **A jobb oldali panel Név** mezőjében nevezze át a adatforrás a következőre: **loyCustomers**.

1. Az adatforrások mentése.

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

## <a name="task-4---configure-transaction-churn-prediction"></a>4. feladat – Konfigurálja a tranzakciót a lemorzsolódási előrejelzéshez.

Ha az egyesített ügyfélprofilok és a tevékenység a helyén van, futtassa a tranzakciós adatváltozást előrejelzés.

1. Ugrás az Intelligencia-előrejelzések **oldalra** > **·**.

1. A Létrehozás lapon válassza a **Modell** használata lehetőséget **az** Ügyfél adatváltozás modelljén **.**

1. Válassza a Tranzakciós lehetőséget **a lemorzsolódás típusához, majd** az Első lépések lehetőséget **.**

1. Nevezze el a modellt **OOB eCommerce Lemorzsolódási Előrejelzés**-nek és a kimeneti entitást **OOBeCommerceChurnPrediction**-nak.

1. Válassza a **Következő** lehetőséget.

1. Modellbeállítások meghatározása:

   - **előrejelzés ablak**: **60** nap annak meghatározására, hogy a jövőbe nézve milyen messzire szeretnénk megjósolni az ügyfelek lemorzsolódását.

   - **Lemorzsolódás definíciója**: **60** nap annak a vásárlás nélküli időtartamnak a jelzésére, amely után az ügyfelet lemorzsolódottnak tekintik.

     :::image type="content" source="media/model-levers.PNG" alt-text="Válassza ki a modellbeállításokat előrejelzés Ablak és a Lemorzsolódás definíciója lehetőséget.":::

1. Válassza a **Következő** lehetőséget.

1. Válassza ki a **Vásárlási előzményeket (kötelező)** és válassza az **Adatok hozzáadása** lehetőséget az vásárlási előzményekhez.

1. Válassza a **SalesOrderLine** lehetőséget és az eCommercePurchases entitást, majd kattintson a Tovább **gombra**. A szükséges adatok automatikusan kitöltésre kerülnek a tevékenységből. Válassza a Mentés, **majd a** Tovább lehetőséget **.**

   :::image type="content" source="media/model-purchase-join.PNG" alt-text="Csatlakoztassa az eCommerce entitásokhoz.":::

1. Hagyja ki a **További adatok (nem kötelező)** lépést.

1. Az Adatfrissítések **lépésben válassza a** Havi **lehetőséget** a modell ütemezéséhez.

1. A részletek áttekintése után válassza a **Mentés és Futtatás** lehetőséget.

## <a name="task-5---review-model-results-and-explanations"></a>5. feladat – Modell eredmények és a magyarázatok áttekintése

Hagyja, hogy a modell teljesítse az adatok betanítását és pontozását. Tekintse át a lemorzsolódási modell magyarázatait. További információ: [előrejelzés eredmények](predict-transactional-churn.md#view-prediction-results) megtekintése.

## <a name="task-6---create-a-segment-of-high-churn-risk-customers"></a>6. feladat – Hozzon létre egy szegmenst a nagy lemorzsolódási kockázatú ügyfelekről

Az éles modell futtatása létrehoz egy új entitást, amely az **Adatentitások** > **között** szerepel. Létrehozhat egy új szegmenst, a modell által létrehozott entitás alapján.

1. Az eredmény lapon válassza a **Szegmens létrehozása** lehetőséget.

1. Hozzon létre egy szabályt az **OOBeCommerceChurnPrediction** entitás használatával, és határozza meg a szegmenst:
   - **Mező:** ChurnScore
   - **Operátor**: nagyobb, mint
   - **Érték**: 0,6

1. Válassza a Szegmens mentése **és** futtatása **lehetőséget**.

Most már van egy dinamikusan frissített szegmense, amely azonosítja a nagy lemorzsolódási kockázatot jelentő ügyfeleket. További információ: [Szegmensek létrehozása és kezelése](segments.md).

> [!TIP]
> A szegmensek **lapon is létrehozhat szegmenst egy előrejelzés modellhez az Új**, **majd a Létrehozás az** Intelligenciából **lehetőség kiválasztásával** > **·**. További információ: [Új szegmens létrehozása gyors szegmensekkel](segment-quick.md).

[!INCLUDE [footer-include](includes/footer-banner.md)]
