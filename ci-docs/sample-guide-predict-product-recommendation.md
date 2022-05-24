---
title: Termékjavaslat-előrejelzés mintaútmutató
description: Használja ezt a mintamutatót, hogy kipróbálja a termékjavaslat előrejelzési modellt.
ms.date: 05/16/2022
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
ms.openlocfilehash: cc72cce15fa0c9e92dbf202c803e99514c9ce2b1
ms.sourcegitcommit: 82f417cfb0a16600e9f552d7a21d598cc8f5a267
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/16/2022
ms.locfileid: "8762689"
---
# <a name="product-recommendation-prediction-sample-guide"></a>Termékjavaslat-előrejelzés mintaútmutató

Elejétől végéig bemutatunk Önnek egy példán keresztül a egy termékajánlás előrejelzést, használva az alább megadott példaadatokat.

## <a name="scenario"></a>Forgatókönyv

A Contoso egy vállalat, amely kiváló minőségű kávét és kávégépet árusít, melyet a Contoso Coffee weboldalán keresztül adnak el. Céljuk, hogy megértsék, mely termékeket ajánlják ki a visszatérő ügyfeleiknek. Ha tudják azt, hogy az ügyfelek mit **vásárolnak valószínűleg**, segíthet a marketingráfordítások mérséklésében, ha bizonyos elemekre figyelnek.

## <a name="prerequisites"></a>Előfeltételek

- Legalább [közreműködői engedély](permissions.md) a Customer Insightsban.
- Javasoljuk, hogy a következő lépéseket hajtsa végre [egy új környezetben](manage-environments.md).

## <a name="task-1---ingest-data"></a>1. Feladat - Adatok betáplálása

Tekintse át az adatbetöltésről [és](data-sources.md) az adatforrások speciális összekötőkkel [történő Power Query importálásáról szóló cikkeket](connect-power-query.md). A következő információk azt feltételezik, hogy megismerkedett a betáplált adatokkal általánosságban.

### <a name="ingest-customer-data-from-ecommerce-platform"></a>Betáplált ügyféladatok az eCommerce platformról.

1. Hozzon létre egy adatforrást, elnevezve **eCommerce**-nek, majd válassza az importálás lehetőséget, és jelölje ki a **Text/CSV** csatlakozót.

1. Adja meg az e-kereskedelmi partnerek URL-címét: [https://aka.ms/ciadclasscontacts](https://aka.ms/ciadclasscontacts).

1. Az adatok szerkesztése közben válassza az **Átalakítás** lehetőséget, majd a **Használja az első sort fejlécként** lehetőséget.

1. Frissítse az adattípust az alább felsorolt oszlopokhoz:
   - **SzületésiDátum**: Dátum
   - **CreatedOn**: Dátum/Idő/Zóna

   :::image type="content" source="media/ecommerce-dob-date.PNG" alt-text="A születési dátum átalakítása dátummá.":::

1. A jobb oldali panelben a "Név" mezőben nevezze át az adatforrását a **Lekérdezés**-ről **eCommerceContacts**-ra.

1. **Mentse** az adatforrást.

### <a name="ingest-online-purchase-data"></a>Online vásárlási adatok betáplálása.

1. Adjon hozzá egy újabb adatforrást a megegyező **eCommerce** adatforráshoz. Válassza a **Text/CSV** csatlakozót újra.

1. Adja meg az online vásárlások **adatainak URL-címét**[https://aka.ms/ciadclassonline](https://aka.ms/ciadclassonline).

1. Az adatok szerkesztése közben válassza az **Átalakítás** lehetőséget, majd a **Használja az első sort fejlécként** lehetőséget.

1. Frissítse az adattípust az alább felsorolt oszlopokhoz:
   - **PurchasedOn** : Dátum/Idő
   - **TotalPrice** : Pénznem

1. A **Név** mezőben az oldalsó panelen, nevezze át az adatforrását a **Lekérdezés** helyett **eCommercePurchases** értékre.

1. **Mentse** az adatforrást.

### <a name="ingest-customer-data-from-loyalty-schema"></a>Ügyféladatok bevitele a hűségsémából

1. Hozzon létre egy adatforrást, melynek neve **LoyaltyScheme**, majd válassza az importálás lehetőséget, és jelölje ki a **Text/CSV** csatlakozót.

1. Adja meg az e-kereskedelmi partnerek URL-címét [https://aka.ms/ciadclasscustomerloyalty](https://aka.ms/ciadclasscustomerloyalty).

1. Az adatok szerkesztése közben válassza az **Átalakítás** lehetőséget, majd a **Használja az első sort fejlécként** lehetőséget.

1. Frissítse az adattípust az alább felsorolt oszlopokhoz:
   - **SzületésiDátum**: Dátum
   - **JutalmazásiPontok**: Egész Szám
   - **KészültEkkor**: Dátum/Idő

1. A **Név** mezőben, a jobb oldali panelen, nevezze át az adatforrását **Lekérdezés** helyett **loyCustomers** értékre.

1. **Mentse** az adatforrást.

## <a name="task-2---data-unification"></a>2. feladat - Adatok egységesítése

[!INCLUDE [sample-guide-unification](includes/sample-guide-unification.md)]

## <a name="task-3---configure-product-recommendation-prediction"></a>3. feladat – Termékjavaslat előrejelzés létrehozása

Az egységes ügyfélprofilok megléte mellett most már futtathatjuk a termékajánlási előrejelzés.

1. Válassza az **Információk** > **Előrejelzés** helyre, és válassza a **Termékjavaslat** lehetőséget.

1. Válassza az **Első lépések** lehetőséget.

1. Nevezze el a modellt **OOB termékjavaslatmodell-előrejelzés** értékre, és a kimeneti entitást **OOBProductRecommendationModelPrediction** értékre.

1. Határozzon meg három feltételt a modellhez.

   - **Termékek száma**: Állítsa ezt az értéket **5**-re. Ez a beállítás határozza meg, hogy hány terméket szeretne javasolni az ügyfeleknek.

   - **Ismétlődő vásárlások várhatóak** : Válassza az **Igen** lehetőséget annak jelzésére, hogy olyan termékeket szeretne belefoglalni az ajánlásba, amelyeket az ügyfelek korábban megvásároltak.

   - **Visszatekintő ablak**: Jelöljön ki legalább **365 napot**. Ez a beállítás határozza meg, hogy mennyi időre visszamenőleg vizsgálja meg a modell az ügyféltevékenységét, amelyet felhasznál a javaslataihoz.

   :::image type="content" source="media/product-recommendation-model-preferences.png" alt-text="Modellbeállítások a termékjavaslati modellhez.":::

1. **A Szükséges adatok** hozzáadása lépésben válassza az Adatok **hozzáadása lehetőséget**.

1. **Az Adatok** hozzáadása ablaktáblán válassza a **SalesOrderLine elemet** beszerzési előzmény entitásként. Ezen a ponton valószínűleg még nincs konfigurálva. Nyissa meg a hivatkozást az ablaktáblán, és hozza létre a tevékenységet a következő lépésekkel:
   1. Adjon meg egy tevékenységnevet, és válassza az **eCommercePurchases:eCommerce** mint Tevékenység entitás *lehetőséget*.**·** Az **elsődleges kulcs** a *PurchaseId*.
   1. Határozza meg és nevezze el a kapcsolatot az *eCommerceContacts:eCommerce entitással,* és válassza a ContactId **lehetőséget** idegen kulcsként.
   1. A tevékenységegyesítéshez állítsa **az Eseménytevékenységet** TotalPrice *és Időbélyeg értékben* PurchasedOn *értékre*. A Vevői tevékenységekben [leírtak](activities.md) szerint további mezőket is megadhat.
   1. A Tevékenységtípus csoportban **válassza a SalesOrderLine lehetőséget** *.* A következő tevékenységmezők leképezése:
      - Rendelési sor azonosítója: Beszerzési azonosító
      - Rendelés azonosítója: PurchaseId
      - Rendelési adatok: PurchasedOn
      - Termékazonosító: ProductId
      - Összeg: TotalPrice
   1. A modellkonfigurációhoz való visszatérés előtt tekintse át és fejezze be a tevékenységet.

1. A Tevékenységek kiválasztása lépésben **válassza ki az újonnan létrehozott tevékenységet a** Tevékenységek **szakaszban.** Válassza a Tovább **lehetőséget**, és az attribútumleképezés már ki van töltve. Válassza a Mentés **lehetőséget**.

1. Ebben a minta útmutatóban kihagyjuk a **Termékinformációk** és **termékszűrők** hozzáadása beállítást, mert nem rendelkezünk termékinformációs adatokkal.

1. **Az Adatfrissítések** lépésben állítsa be a modellütemezést.

   A modell rendszeres betanítást igényel ahhoz, hogy új mintákat tanulhasson, amikor új adatok kerülnek a rendszerbe. Ennél a példánál válassza a **Havonta** beállítást.

1. A részletek áttekintése után válassza a **Mentés és Futtatás** lehetőséget. A modell első futtatása néhány percet vesz igénybe.

## <a name="task-4---review-model-results-and-explanations"></a>4. feladat – Modell eredmények és a magyarázatok áttekintése

Hagyja, hogy a modell teljesítse az adatok betanítását és pontozását. Most már megtekintheti a termékjavaslat modell magyarázatait. További tudnivalókért olvassa el az [Előrejelzés állapotának és eredmények áttekintése](predict-transactional-churn.md#review-a-prediction-status-and-results) című témakört.

## <a name="task-5---create-a-segment-of-high-purchased-products"></a>5. feladat – A gyakran megvásárolt termékek szegmensének létrehozása

Futtatva a termékjavaslati modellt, létrehozhat egy új entitást, amelyet láthat a **Adat** > **Entitások**-nál.

Létrehozhat egy új szegmenst, a modell által létrehozott entitás alapján.

1. Kattintson a **Szegmensek** lehetőségre. Válassza az Új lehetőséget **, és válassza a Létrehozás az intelligenciából lehetőséget** **.**

   ![Szegmens létrehozása a modell kimenetével.](media/segment-intelligence.png)

1. Válassza ki a **OOBProductRecommendationModelPrediction** végpontot és definiálja a szegmenst:

   - Mező: ProductID
   - Érték: Válassza ki a három legnépszerűbb termékazonosítót

   :::image type="content" source="media/product-recommendation-quick-segment.png" alt-text="Hozzon létre egy szegmenst a modell eredményeiből.":::

Most már van egy dinamikusan frissített szegmense, amely azonosítja azokat az ügyfeleket, akiket érdekelhet a három leginkább ajánlott termék megvásárlása.

További információ: [Szegmensek létrehozása és kezelése](segments.md).

[!INCLUDE [footer-include](includes/footer-banner.md)]
