---
title: Termékjavaslat-előrejelzés mintaútmutató
description: Használja ezt a mintamutatót, hogy kipróbálja a termékjavaslat előrejelzési modellt.
ms.date: 02/10/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: tutorial
author: diegogranados117
ms.author: digranad
manager: shellyha
ms.openlocfilehash: a85ee598ec747d0594755314e83a127ce0f2af95
ms.sourcegitcommit: 0b754d194d765afef70d1008db7b347dd1f0ee40
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/24/2021
ms.locfileid: "6306169"
---
# <a name="product-recommendation-prediction-preview-sample-guide"></a>Termékjavaslat-előrejelzés (előzetes verzió) mintaútmutató

Elejétől végéig bemutatunk Önnek egy példán keresztül a egy termékajánlás előrejelzést, használva az alább megadott példaadatokat.

## <a name="scenario"></a>Forgatókönyv

A Contoso egy olyan cég, amely kiváló minőségű kávékat és kávéfőzőket gyárt, amelyeket a Contoso Coffee weboldalon keresztül értékesítenek. Céljuk, hogy megértsék, mely termékeket ajánlják ki a visszatérő ügyfeleiknek. Ha tudják azt, hogy az ügyfelek mit **vásárolnak valószínűleg**, segíthet a marketingráfordítások mérséklésében, ha bizonyos elemekre figyelnek.

## <a name="prerequisites"></a>Előfeltételek

- Legalább [közreműködői engedély](permissions.md) a Customer Insightsban.
- Javasoljuk, hogy a következő lépéseket hajtsa végre [egy új környezetben](manage-environments.md).

## <a name="task-1---ingest-data"></a>1. Feladat - Adatok betáplálása

Olvassa el a cikkeket [az adatok betáplálásáról](data-sources.md) és [az adatforrások importálásáról a Power Query csatlakozók használatával](connect-power-query.md). A következő információk azt feltételezik, hogy megismerkedett a betáplált adatokkal általánosságban.

### <a name="ingest-customer-data-from-ecommerce-platform"></a>Betáplált ügyféladatok az eCommerce platformról.

1. Hozzon létre egy adatforrást, elnevezve **eCommerce**-nek, majd válassza az importálás lehetőséget, és jelölje ki a **Text/CSV** csatlakozót.

1. Adja meg az URL-címét az eCommerce kapcsolattartóknak https://aka.ms/ciadclasscontacts.

1. Az adatok szerkesztése közben válassza az **Átalakítás** lehetőséget, majd a **Használja az első sort fejlécként** lehetőséget.

1. Frissítse az adattípust az alább felsorolt oszlopokhoz:
   - **SzületésiDátum**: Dátum
   - **CreatedOn**: Dátum/Idő/Zóna

   :::image type="content" source="media/ecommerce-dob-date.PNG" alt-text="A születési dátum átalakítása dátummá.":::

5. A jobb oldali panelben a "Név" mezőben nevezze át az adatforrását a **Lekérdezés**-ről **eCommerceContacts**-ra.

6. **Mentse** az adatforrást.

### <a name="ingest-online-purchase-data"></a>Online vásárlási adatok betáplálása.

1. Adjon hozzá egy újabb adatforrást a megegyező **eCommerce** adatforráshoz. Válassza a **Text/CSV** csatlakozót újra.

1. Adja meg az URL-címét az **Online vásárlas** adataihoz https://aka.ms/ciadclassonline.

1. Az adatok szerkesztése közben válassza az **Átalakítás** lehetőséget, majd a **Használja az első sort fejlécként** lehetőséget.

1. Frissítse az adattípust az alább felsorolt oszlopokhoz:
   - **PurchasedOn** : Dátum/Idő
   - **TotalPrice** : Pénznem

1. A **Név** mezőben az oldalsó panelen, nevezze át az adatforrását a **Lekérdezés** helyett **eCommercePurchases** értékre.

1. **Mentse** az adatforrást.


### <a name="ingest-customer-data-from-loyalty-schema"></a>Ügyféladatok bevitele a hűségsémából

1. Hozzon létre egy adatforrást, melynek neve **LoyaltyScheme**, majd válassza az importálás lehetőséget, és jelölje ki a **Text/CSV** csatlakozót.

1. Adja meg az URL-címét az eCommerce kapcsolattartóknak https://aka.ms/ciadclasscustomerloyalty.

1. Az adatok szerkesztése közben válassza az **Átalakítás** lehetőséget, majd a **Használja az első sort fejlécként** lehetőséget.

1. Frissítse az adattípust az alább felsorolt oszlopokhoz:
   - **SzületésiDátum**: Dátum
   - **JutalmazásiPontok**: Egész Szám
   - **KészültEkkor**: Dátum/Idő

1. A **Név** mezőben, a jobb oldali panelen, nevezze át az adatforrását **Lekérdezés** helyett **loyCustomers** értékre.

1. **Mentse** az adatforrást.

## <a name="task-2---data-unification"></a>2. feladat - Adatok egységesítése

Az adatok betöltése után most elkezdjük az adategyesítési folyamatot, hogy egységes ügyfélprofilt hozzunk létre. További információkért lásd: [Adatok egységesítése](data-unification.md).

### <a name="map"></a>Map

1. Az adatok betáplálása után képezze le a kapcsolattartókat az eCommerce-ből és a Loyalty data-ból a közös adattípusokba. Nyissa meg az **Adatok** > **Egységesítés** > **Megfeleltetés**-t.

2. Válassza ki az entitást, amely jelképezi az ügyfélprofilt – **eCommerceContacts** és **loyCustomers**.

   ![az ecommerce és a loyality adatforrások egységesítése.](media/unify-ecommerce-loyalty.png)

3. Jelölje ki a **ContactId**-t elsődleges kulcsaként az **eCommerceContacts**-hoz és a **LoyaltyID** a **loyCustomers** elsődleges kulcsaként.

   ![A LoyaltyId egyesítheti elsődleges kulcsként.](media/unify-loyaltyid.png)

### <a name="match"></a>Egyeztetés

1. Ugorjon az **Egyeztetés** lapra és válassza a **Sorrend beállítását**.

2. Az **Elsődleges** legördülő listában válassza az **eCommerceContacts : eCommerce** mint elsődleges forrást, és tartalmazza az összes rekordot.

3. Az **Entitás 2** legördülő listában válassza a **loyCustomers: LoyaltyScheme** lehetőséget, és adja meg az összes rekordot.

   ![Az egységesítéshez egyeztesse az eCommerce-t és a Loyality-t.](media/unify-match-order.png)

4. Válassza az **Új szabály létrehozása** menüpontot

5. Adja hozzá az első feltételt a FullName segítségével.

   - Az eCommerceContacts esetében válassza a **FullName** lehetőséget a legördülő menüben.
   - A loyCustomers esetében válassza a **FullName** lehetőséget a legördülő menüben.
   - Jelölje ki a **Normalizálás** legördülő parancsot, és válassza a **Típus (Telefon, Név, Cím,...)** lehetőséget.
   - Állítsa be a **Pontossági szintet**: **Alap** és **Érték**: **Magas**-ra.

6. Adja meg a nevét **FullName, Email**, az új szabályhoz.

   - Másik feltétel hozzáadása az e-mail címhez a **Feltétel hozzáadása** lehetőség választásával.
   - Az entitás eCommerceContacts esetében válassza az **EMail** lehetőséget a legördülő menüben.
   - Az entitás loyCustomers esetében válassza az **EMail** lehetőséget a legördülő menüben.
   - Hagyja üresen a Normalizálást.
   - Állítsa be a **Pontossági szintet**: **Alap** és **Érték**: **Magas**-ra.

   ![Egységesítése az egyezési szabályt a névhez és az e-mailhez.](media/unify-match-rule.png)

7. Válassza a **Mentés** és **Futtatás** lehetőséget.

### <a name="merge"></a>Összefűzés

1. Nyissa meg az **Egyesítés** lapot.

1. A **ContactId** **loyCustomers** entitáshoz változtassa meg a megjelenítendő nevet **ContactIdLOYALTY**-ra, hogy megkülönböztethesse azt a többi betáplált azonosítóval.

   ![nevezze át a loyalty azonosítót contactid-re.](media/unify-merge-contactid.png)

1. Válassza a **Mentés** és **Futtatás** lehetőséget, hogy elindítsa a Egyesítés Folyamatot.

## <a name="task-3---configure-product-recommendation-prediction"></a>3. feladat – Termékjavaslat előrejelzés létrehozása

Az egységesített ügyfélprofilok elkészítése után, előfizetés lemorzsolódási előrejelzést futtathatunk.

1. Válassza az **Információk** > **Előrejelzés** helyre, és válassza a **Termékjavaslat** lehetőséget.

1. Válassza az **Első lépések** lehetőséget.

1. Nevezze el a modellt **OOB termékjavaslatmodell-előrejelzés** értékre, és a kimeneti entitást **OOBProductRecommendationModelPrediction** értékre.

1. Határozzon meg három feltételt a modellhez.

   - **Termékek száma**: Állítsa ezt az értéket **5**-re. Ez a beállítás határozza meg, hogy hány terméket szeretne javasolni az ügyfeleknek.

   - **Ismétlődő vásárlások várhatóak** : Válassza az **Igen** lehetőséget annak jelzésére, hogy olyan termékeket szeretne belefoglalni az ajánlásba, amelyeket az ügyfelek korábban megvásároltak.

   - **Visszatekintő ablak**: Jelöljön ki legalább **365 napot**. Ez a beállítás határozza meg, hogy mennyi időre visszamenőleg vizsgálja meg a modell az ügyféltevékenységét, amelyet felhasznál a javaslataihoz.
   
   :::image type="content" source="media/product-recommendation-model-preferences.png" alt-text="Modellbeállítások a termékjavaslati modellhez.":::

1. Válassza ki a **Szükséges adatok** menüt, és ott válassza az **Adatok hozzáadása** lehetőséget a vásárlási előzményekhez.

1. Adja hozzá a **eCommercePurchases: eCommerce** entitást és képezze le a mezőket az eCommerce-ről a megfelelő mezőkre, melyek modell által megköveteltek.

1. Csatlakozzon az **eCommercePurchases: eCommerce** entitáshoz az **eCommerceContacts: eCommerce**-szel.

   ![Csatlakoztassa az eCommerce entitásokhoz.](media/model-purchase-join.png)

1. Válassza a **Következő** lehetőséget a modell ütemezésének beállításához.

   A modell rendszeres betanítást igényel ahhoz, hogy új mintákat tanulhasson, amikor új adatok kerülnek a rendszerbe. Ennél a példánál válassza a **Havonta** beállítást.

1. A részletek áttekintése után válassza a **Mentés és Futtatás** lehetőséget.


## <a name="task-4---review-model-results-and-explanations"></a>4. feladat – Modell eredmények és a magyarázatok áttekintése

Hagyja, hogy a modell teljesítse az adatok betanítását és pontozását. Most már megtekintheti a termékjavaslat modell magyarázatait. További tudnivalókért olvassa el az [Előrejelzés állapotának és eredmények áttekintése](predict-subscription-churn.md#review-a-prediction-status-and-results) című témakört.

## <a name="task-5---create-a-segment-of-high-purchased-products"></a>5. feladat – A gyakran megvásárolt termékek szegmensének létrehozása

Futtatva a termékjavaslati modellt, létrehozhat egy új entitást, amelyet láthat a **Adat** > **Entitások**-nál.

Létrehozhat egy új szegmenst, a modell által létrehozott entitás alapján.

1. Kattintson a **Szegmensek** lehetőségre. Válassza az **Új** lehetőséget, és válassza a **Létrehozás a következőkből** > **Intelligencia**.

   ![Szegmens létrehozása a modell kimenetével.](media/segment-intelligence.png)

1. Válassza ki a **OOBProductRecommendationModelPrediction** végpontot és definiálja a szegmenst:

   - Mező: ProductID
   - Operátor: Érték
   - Érték: Válassza ki a három legnépszerűbb termékazonosítót

   :::image type="content" source="media/product-recommendation-quick-segment.png" alt-text="Hozzon létre egy szegmenst a modell eredményeiből.":::

Most van egy dinamikusan frissített szegmense, amely azonosítja azokat az ügyfeleket, akik valószínűbb, hogy megvásárolják három leginkább javasolt terméket 

További információ: [Szegmensek létrehozása és kezelése](segments.md).


[!INCLUDE[footer-include](../includes/footer-banner.md)]
