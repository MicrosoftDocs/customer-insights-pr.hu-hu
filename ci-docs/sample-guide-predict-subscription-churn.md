---
title: Az Előfizetés-lemorzsolódási előrejelzési példamutató
description: Használja ezt a példamutatót, hogy kipróbálhassa a mezőn kívüli előfizetés lemorzsolódási modellt.
ms.date: 09/19/2022
ms.reviewer: v-wendysmith
ms.subservice: audience-insights
ms.topic: tutorial
author: m-hartmann
ms.author: wameng
manager: shellyha
searchScope:
- ci-create-prediction
- customerInsights
ms.openlocfilehash: 7e754be9a2cb9450949c6b3667bbd37aa39cf0bf
ms.sourcegitcommit: be341cb69329e507f527409ac4636c18742777d2
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 09/30/2022
ms.locfileid: "9610009"
---
# <a name="subscription-churn-prediction-sample-guide"></a>Az Előfizetés-lemorzsolódási előrejelzési példamutató

Ez az útmutató bemutatja az előfizetés lemorzsolódásának teljes körű példáját előrejelzés mintaadatok használatával. Javasoljuk, hogy ezt a előrejelzés [új környezetben próbálja ki](manage-environments.md).

## <a name="scenario"></a>Forgatókönyv

Contoso egy olyan cég, amely kiváló minőségű kávé- és kávéfőzőket gyárt. A termékeket a Contoso Coffee weboldalán keresztül értékesítik. A közelmúltban indítottak el egy előfizetéses üzletet ügyfeleiknek, hogy azok rendszeresen megkaphassák kávéjukat. Céljuk annak megértése, hogy mely feliratkozott ügyfelek mondhatják le előfizetésüket a következő néhány hónapban. Ha tudják, hogy melyik ügyfelük fog lemorzsolódni **,** az segíthet nekik megtakarítani a marketingtörekvéseket azáltal, hogy a megtartására összpontosít.

## <a name="prerequisites"></a>Előfeltételek

- Legalább [közreműködői engedély](permissions.md) a Customer Insightsban.

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

1. Az adatforrások mentése.

### <a name="ingest-customer-data-from-loyalty-schema"></a>Ügyféladatok bevitele a hűségsémából

1. Hozzon létre egy LoyaltyScheme **nevű adatforrás,** és válassza ki a **Text/CSV-összekötőt**.

1. Adja meg a hűségügyfelek https://aka.ms/ciadclasscustomerloyalty URL-címét.

1. Az adatok szerkesztése közben válassza **az Átalakítás**, majd **az Első sor használata fejlécként** lehetőséget.

1. Frissítse az adattípust az alább felsorolt oszlopokhoz:
   - **SzületésiDátum**: Dátum
   - **JutalmazásiPontok**: Egész Szám
   - **KészültEkkor**: Dátum/Idő

1. **A jobb oldali panel Név** mezőjében nevezze át a adatforrás a következőre: **loyCustomers**.

1. Az adatforrások mentése.

### <a name="ingest-subscription-information"></a>Előfizetési információk betáplálása

1. Hozzon létre egy SubscriptionHistory nevű **adatforrás, és válassza ki a** Text/CSV-összekötőt **.**

1. Adja meg az előfizetések URL-címét https://aka.ms/ciadchurnsubscriptionhistory.

1. Az adatok szerkesztése közben válassza **az Átalakítás**, majd **az Első sor használata fejlécként** lehetőséget.

1. Frissítse az adattípust az alább felsorolt oszlopokhoz:
   - **ElőfizetésAzonosító**: Egész szám
   - **ElőfizetésiÖsszeg**: Pénznem
   - **ElőfizetésVégénekDátuma**: Dátum/Idő
   - **ElőfizetésKezdeténekDátuma**: Dátum/Idő
   - **TranzakcióDátuma**: Dátum/Idő
   - **IsIsmétlődés**: Igaz/Hamis
   - **Is_auto_megújítás**: Igaz/Hamis
   - **IsmétlődésiGyakoriságInHónapok**: Egész Szám

1. **A jobb oldali panel Név** mezőjében nevezze át a adatforrás SubscriptionHistory **névre**.

1. Az adatforrások mentése.

### <a name="ingest-customer-data-from-website-reviews"></a>Tápláljon be ügyféladatokat a webhely értékelésekből.

1. Hozzon létre egy Webhely nevű **adatforrás,** és válassza ki a **Text/CSV-összekötőt**.

1. Adja meg a webhelyértékelések URL-jét https://aka.ms/ciadclasswebsite.

1. Az adatok szerkesztése közben válassza **az Átalakítás**, majd **az Első sor használata fejlécként** lehetőséget.

1. Frissítse az adattípust az alább felsorolt oszlopokhoz:
   - **ÁttekintésiMinősítés**: Egész Szám
   - **ÁttekintésDátuma**: Dátum

1. **A jobb oldali panel Név** mezőjében nevezze át a adatforrás webReviews **névre**.

## <a name="task-2---data-unification"></a>2. feladat - Adatok egységesítése

Tekintse át az adatok egyesítéséről [szóló cikket](data-unification.md). Az alábbi információk feltételezik, hogy általában ismeri az adatok egyesítését.

[!INCLUDE [sample-guide-unification](includes/sample-guide-unification.md)]

## <a name="task-3---create-transaction-history-activity"></a>3. feladat – Tranzakciós előzményekkel kapcsolatos tevékenység létrehozása

Tekintse át az ügyféltevékenységekről szóló [cikket](activities.md). Az alábbi információk feltételezik, hogy általában ismeri a tevékenységek létrehozását.

1. Hozzon létre egy SubscriptionHistory nevű **tevékenységet az** Előfizetés *entitással és annak elsődleges kulcsával,CustomerId* **.**

1. Hozzon létre egy kapcsolatot a SubscriptionHistory:Subscription *és* az eCommerceContacts:eCommerce *között*, ahol **a CustomerID** a két entitás összekapcsolásához szükséges idegen kulcs.

1. Válassza a SubscriptionType lehetőséget **az EventActivity** és **a** SubscriptionEndDate **elemhez a** TimeStamp **esetében**.

1. Válassza az Előfizetés **lehetőséget** a **tevékenységtípushoz,** és szemantikailag leképezi a tevékenységadatokat.

1. Futtassa a tevékenységet.

1. Adjon hozzá egy másik tevékenységet, és képezze le a mezők nevét a megfelelő mezőkre:
   - Ügyféltevékenységek entitás: Reviews:Website
   - Elsődleges kulcs: Website.Reviews.ReviewId
   - Időbélyeg: Website.Reviews.ReviewDate
   - Esemény (tevékenység neve): Website.Reviews.ActivityTypeDisplay
   - Részletek (összeg vagy érték): Website.Reviews.ReviewRating

1. Futtassa a tevékenységet.

## <a name="task-4---configure-the-subscription-churn-prediction"></a>4. feladat – Konfigurálja az előfizetés lemorzsolódási előrejelzést

Ha az egyesített ügyfélprofilok a helyükön vannak, és létrehozott tevékenység, futtassa az előfizetési adatváltozást előrejelzés. Részletes lépésekért lásd: [Előfizetési adatváltozás előrejelzés](predict-subscription-churn.md).

1. Ugrás az Intelligencia-előrejelzések **oldalra** > **·**.

1. A Létrehozás lapon válassza a **Modell** használata lehetőséget **az** Ügyfél adatváltozás modelljének csempéjén **.**

1. Válassza az Előfizetés lehetőséget **a lemorzsolódás típusához, majd** az Első lépések lehetőséget **.**

1. Nevezze el a modellt **OOB Előfizetés-lemorzsolódási Előrejelzés**-nek és a kimeneti entitást **OOBElőfizetés-lemorzsolódásiElőrejelzés**-nek.

1. Modellbeállítások meghatározása:
   - **Napok az előfizetés vége** óta: **60** nap annak jelzésére, hogy az ügyfél lemorzsolódottnak minősül, ha az előfizetése lejárta után ebben az időszakban nem újítja meg az előfizetést.
   - **Napok a jövőbeli lemorzsolódás** előrejelzésére: **93** nap, amely a modell által megjósolt időtartam, hogy mely ügyfelek hurcolhatnak le. Minél távolabb tekint a jövőben, annál kevésbé pontosak az eredmények.

   :::image type="content" source="media/model-subs-levers.PNG" alt-text="Válassza ki a modellbeállításokat és a lemorzsolódás definícióját.":::

1. Válassza a **Következő** lehetőséget.

1. A Szükséges adatok **lépésben válassza az** Adatok **hozzáadása lehetőséget** az előfizetési előzmények megadásához.

1. Válassza az **Előfizetés** és a SubscriptionHistory entitás lehetőséget, majd kattintson a Tovább **gombra**. A szükséges adatok automatikusan kitöltésre kerülnek a tevékenységből. Válassza a **Mentés** parancsot.

1. Az Ügyféltevékenységek alatt válassza az Adatok **hozzáadása lehetőséget**.

1. Ebben a példában adja hozzá a webes felülvizsgálati tevékenységet.

1. Válassza a **Következő** lehetőséget.

1. Az Adatfrissítések **lépésben válassza a** Havi **lehetőséget** a modell ütemezéséhez.

1. A részletek áttekintése után válassza a **Mentés és Futtatás** lehetőséget.

## <a name="task-5---review-model-results-and-explanations"></a>5. feladat – Modell eredmények és a magyarázatok áttekintése

Hagyja, hogy a modell teljesítse az adatok betanítását és pontozását. Tekintse át az előfizetés-lemorzsolódási modell magyarázatait. További információ: [előrejelzés eredmények](predict-subscription-churn.md#view-prediction-results) megtekintése.

## <a name="task-6---create-a-segment-of-high-churn-risk-customers"></a>6. feladat – Hozzon létre egy szegmenst a nagy lemorzsolódási kockázatú ügyfelekről

A modell futtatása új entitást hoz létre, amely listázva van az **Adatok** > **Entitások** helyen. Létrehozhat egy új szegmenst, a modell által létrehozott entitás alapján.

1. Az eredmény lapon válassza a **Szegmens létrehozása** lehetőséget.

1. Hozzon létre egy szabályt az **OOBSubscriptionChurnPrediction** entitás használatával, és határozza meg a szegmenst:
   - **Mező:** ChurnScore
   - **Operátor**: nagyobb, mint
   - **Érték**: 0,6

1. Válassza a Szegmens mentése **és** futtatása **lehetőséget**.

Most már van egy szegmense, amely dinamikusan frissítve van, és amely meghatározza a magas lemorzsolódási kockázatot ennek az üzleti előfizetésnek az esetén. További információ: [Szegmensek létrehozása és kezelése](segments.md).

> [!TIP]
> A szegmensek **lapon is létrehozhat szegmenst egy előrejelzés modellhez az Új**, **majd a Létrehozás az** Intelligenciából **lehetőség kiválasztásával** > **·**. További információ: [Új szegmens létrehozása gyors szegmensekkel](segment-quick.md).

[!INCLUDE [footer-include](includes/footer-banner.md)]
