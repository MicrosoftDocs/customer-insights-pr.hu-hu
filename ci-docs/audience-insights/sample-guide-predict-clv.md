---
title: Ügyfélélettartam-érték előrejelzése mintaútmutató
description: Ezzel a mintaútmutatóval próbálhatja ki az ügyfélélettartam-érték előrejelzése modellt.
ms.date: 05/25/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: tutorial
author: yashlundia
ms.author: yalundia
manager: shellyha
ms.openlocfilehash: 73d294a285b4ad706bec7fe925c1daa0b839ddd6
ms.sourcegitcommit: 7b6189e47ed1f87e7ce35d40e4cf7a6730f31ef2
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/01/2021
ms.locfileid: "6129948"
---
# <a name="customer-lifetime-value-clv-prediction-sample-guide"></a>Ügyfélélettartam-érték (CLV) előrejelzés mintaútmutató

Ez az útmutató a mintaadatok felhasználásával átfogóan ismerteti az Ügyfél élettartamra vetített értékének (CLV) előrejelzését a Customer Insights alkalmazásban.

## <a name="scenario"></a>Forgatókönyv

A Contoso kiváló minőségű kávékat és kávéfőzőket gyártó vállalat. A termékeket a Contoso Coffee weboldalán keresztül értékesítik. A vállalat meg akarja érteni azt az értéket (bevételt), amelyet ügyfeleik a következő 12 hónapban generálhatnak. Ismerve az ügyfeleik várható értékét a következő 12 hónapra vonatkozóan segít nekik a marketingerőfeszítéseiket a nagy értékű ügyfelek felé irányítani.

## <a name="prerequisites"></a>Előfeltételek

- Legalább [közreműködői engedély](permissions.md) a célközönség betekintési információihoz.
- Javasoljuk, hogy a következő lépéseket hajtsa végre [egy új környezetben](manage-environments.md).

## <a name="task-1---ingest-data"></a>1. Feladat - Adatok betáplálása

Tekintse át az [adatbetöltéssel kapcsolatos információk](data-sources.md) és az [adatforrások importálása Power Query csatlakozók használatával](connect-power-query.md) cikkeket. A következő információk azt feltételezik, hogy megismerkedett a betáplált adatokkal általánosságban.

### <a name="ingest-customer-data-from-ecommerce-platform"></a>Betáplált ügyféladatok az eCommerce platformról.

1. Hozzon létre egy adatforrást, elnevezve **eCommerce-nek**, majd válassza az importálás lehetőséget, és jelölje ki a **Szöveg/CSV** összekötőt.

1. Adja meg az URL-címét az eCommerce kapcsolattartóknak [https://aka.ms/ciadclasscontacts](https://aka.ms/ciadclasscontacts).

1. Az adatok szerkesztése közben válassza az **Átalakítás** lehetőséget, majd a **Használja az első sort fejlécként** lehetőséget.

1. Frissítse az adattípust az alább felsorolt oszlopokhoz:
   - **SzületésiDátum**: Dátum
   - **CreatedOn**: Dátum/Idő/Zóna

   :::image type="content" source="media/ecommerce-dob-date.PNG" alt-text="A születési dátum átalakítása dátummá.":::

1. A jobb oldali panelben a "Név" mezőben nevezze át az adatforrását a **Lekérdezés**-ről **eCommerceContacts**-ra.

1. **Mentse** az adatforrást.

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

### <a name="ingest-customer-data-from-website-reviews"></a>Tápláljon be ügyféladatokat a webhely értékelésekből.

1. Hozzon létre egy adatforrást, **eCommerce** néven, majd válassza az importálás lehetőséget, és jelölje ki a **Text/CSV** csatlakozót.

1. Adja meg az URL-címét az eCommerce kapcsolattartóknak https://aka.ms/CI-ILT/WebReviews.

1. Az adatok szerkesztése közben válassza az **Átalakítás** lehetőséget, majd a **Használja az első sort fejlécként** lehetőséget.

1. Frissítse az adattípust az alább felsorolt oszlopokhoz:

   - **ReviewRating**: Decimális szám
   - **ÁttekintésDátuma**: Dátum

1. A jobb oldali ablaktáblán található "Név" mezőben nevezze át a adatforrás **Lekérdezés** értékről **Vélemények** értékre.

1. **Mentse** az adatforrást.

## <a name="task-2---data-unification"></a>2. feladat - Adatok egységesítése

Az adatok betöltése után most elkezdjük az adategyesítési folyamatot, hogy egységes ügyfélprofilt hozzunk létre. További információkért lásd: [Adatok egységesítése](data-unification.md).

### <a name="map"></a>Map

1. Az adatok betáplálása után képezze le a kapcsolattartókat az eCommerce-ből és a Loyalty data-ból a közös adattípusokba. Nyissa meg az **Adatok** > **Egységesítés** > **Megfeleltetés**-t.

1. Válassza ki az entitást, amely jelképezi az ügyfélprofilt – **eCommerceContacts** és **loyCustomers**. Ezután válassza az **Alkalmaz** lehetőséget.

   ![az ecommerce és a loyality adatforrások egységesítése.](media/unify-ecommerce-loyalty.png)

1. Jelölje ki a **ContactId**-t elsődleges kulcsaként az **eCommerceContacts**-hoz és a **LoyaltyID** a **loyCustomers** elsődleges kulcsaként.

   ![A LoyaltyId egyesítheti elsődleges kulcsként.](media/unify-loyaltyid.png)

1. Válassza a **Mentés** parancsot.

### <a name="match"></a>Egyeztetés

1. Ugorjon az **Egyeztetés** lapra és válassza a **Sorrend beállítását**.

1. Az **Elsődleges** legördülő listában válassza az **eCommerceContacts : eCommerce** lehetőséget elsődleges forrásként, amely minden rekordot magában foglal.

1. Az **Entitás 2** legördülő listájában válassza ki a **loyCustomers: LoyaltyScheme** lehetőséget, és adja meg az összes rekordot.

   ![Az egységesítéshez egyeztesse az eCommerce-t és a Loyality-t.](media/unify-match-order.png)

1. Válassza a **Szabály hozzáadása** lehetőséget

1. Adja hozzá az első feltételt a FullName segítségével.

   - Az eCommerceContacts lehetőséghez válassza ki a **FullName** opciót a legördülő listából.
   - A loyCustumers lehetőséghez válassza ki a **FullName** opciót a legördülő listából.
   - Jelölje ki a **Normalizálás** legördülő parancsot, és válassza a **Típus (Telefon, Név, Cím,...)** lehetőséget.
   - Állítsa be a **Pontossági szintet**: **Alap** és **Érték**: **Magas**-ra.

1. Adja meg a nevét **FullName, Email**, az új szabályhoz.

   - Másik feltétel hozzáadása az e-mail címhez a **Feltétel hozzáadása** lehetőség választásával.
   - Az eCommerceContacts entitáshoz válassza az **Email** legördülő lehetőséget.
   - Az loyCustomers entitáshoz válassza az **Email** legördülő lehetőséget.
   - Hagyja üresen a Normalizálást.
   - Állítsa be a **Pontossági szintet**: **Alap** és **Érték**: **Magas**-ra.

   ![Egységesítése az egyezési szabályt a névhez és az e-mailhez.](media/unify-match-rule.png)

1. Válassza a **Kész** lehetőséget.

1. Válassza a **Mentés** és **Futtatás** lehetőséget.

### <a name="merge"></a>Összefűzés

1. Nyissa meg az **Egyesítés** lapot.

1. A **ContactId** **loyCustomers** entitáshoz változtassa meg a megjelenítendő nevet **ContactIdLOYALTY**-ra, hogy megkülönböztethesse azt a többi betáplált azonosítóval.

   ![nevezze át a loyalty azonosítót contactid-re.](media/unify-merge-contactid.png)

1. Válassza a **Mentés**, majd az **Egyesítési és lefelé irányuló folyamatok futtatása** lehetőséget.

## <a name="task-3---configure-customer-lifetime-value-prediction"></a>3. feladat – Ügyfél élettartamra vetített értékének előrejelzése

Az egységes ügyfélprofilok segítségével immár futtathatja az ügyfél élettartamra vetített értékének előrejelzését. A részletes lépésekért lásd: [Ügyfél élettartamra vetített értékének előrejelzése (előzetes verzió)](predict-customer-lifetime-value.md).

1. Lépjen az **Információk**  > **Előrejelzések** lapra, és válassza ki az **Ügyfél élettartamának értékmodellje** lehetőséget.

1. Lépjen végig az oldalsó ablaktáblában található információkon, és válassza az **Első lépések** lehetőséget.

1. Nevezze el a modellt **OOB eCommerce CLV előrejelzés** névvel, a kimeneti entitás legyen **OOBeCommerceCLVPrediction**.

1. A CLV modell modellbeállításainak meghatározása:
   - **Előrejelzési időszak**: **12 hónap vagy 1 év**. Ez a beállítás határozza meg, hogy milyen időtávra legyen megbecsülve az ügyfél élettartamra vetített értéke.
   - **Aktív ügyfelek**  : Adja meg, hogy az aktív ügyfelek mit jelentenek vállalkozása esetében. Állítsa be azt a múltbeli időkeretet, amelyekben az ügyfélnek legalább egy tranzakcióval rendelkeznie kell ahhoz, hogy aktívnak minősüljön. A modell csak az aktív ügyfelek CLV-jét fogja előre jelezni. Válasszon aközött, hogy a modell a korábbi tranzakciós adatok alapján számítsa ki az időszakot, vagy konkrét időkeret ad meg ehhez. Ebben a minta útmutatóban **a modell számíthatja ki a vásárlási intervallumot** lehetőséget használjuk, ami az alapértelmezett lehetőség.
   - **Nagy értékű ügyfelek**: Határozza meg a nagy értékű ügyfeleket a legjobban fizető ügyfelek percentiliseként. A modell ezt a bemenetet használja, hogy olyan eredményeket biztosítson, amelyek megfelelnek a vállalkozása nagy értékű ügyfelek definíciójának. Választhatja azt, hogy a modell határozza meg a nagy értékű ügyfeleket. Egy heurisztikus szabályt használ, ami a percentilisből van származtatva. Meghatározhatja a nagy értékű ügyfeleket a jövőbeni legjobban fizető ügyfelek percentiliseként is. Ebben a minta útmutatóban manuálisan határozzuk meg a nagy értékű ügyfeleket az **aktív fizető ügyfelek felső 30% -aként**, és a **Tovább** lehetőséget választjuk.

    :::image type="content" source="media/clv-model-preferences.png" alt-text="Beállítások lépés az CLV-modell interaktív élményében.":::

1. A **Szükséges adatok** lépésben válassza az **Adatok hozzáadása** lehetőséget a tranzakcióelőzmények adatainak megadásához.

1. Adja hozzá az **eCommercePurchases : eCommerce** entitást, és képezze le a modell által megkövetelt attribútumokat:
   - Tranzakcióazonosító: eCommerce.eCommercePurchases.PurchaseId
   - Tranzakció dátuma: eCommerce.eCommercePurchases.PurchasedOn
   - Tranzakció összege: eCommerce.eCommercePurchases.TotalPrice
   - Termékazonosító: eCommerce.eCommercePurchases.ProductId

1. Válassza a **Következő** lehetőséget.

1. Az **eCommercePurchases : eCommerce** entitás és az **eCommerceContacts : eCommerce** entitás közötti kapcsolat beállítása.

1. A **További adatok (opcionális)** lépés lehetővé teszi további ügyféltaktivitási adatok hozzáadását. Ezek az adatok segíthetnek abban, hogy több betekintést nyerjen a vállalkozásával folytatott ügyfélinterakciókkal kapcsolatosan, ami hozzájárulhat a CLV-hez. Az olyan kulcsfontosságú ügyfél-interakciók hozzáadása, mint a webes naplók, ügyfélszolgálati naplók vagy a jutalomprogram előzményei javíthatják az előrejelzések pontosságát. Válassza az **Adatok hozzáadása** lehetőséget, hogy további ügyféltevékenységi adatokat vegyen fel.

1. Adja hozzá az ügyféltevékenység entitást, és képezze le a mezők nevét a modell által megkövetelt megfelelő mezőkhöz:
   - Ügyféltevékenységek entitás: Reviews:Website
   - Elsődleges kulcs: Website.Reviews.ReviewId
   - Időbélyeg: Website.Reviews.ReviewDate
   - Esemény (tevékenység neve): Website.Reviews.ActivityTypeDisplay
   - Részletek (összeg vagy érték): Website.Reviews.ReviewRating

1. Válassza a **Tovább** lehetőséget, és konfigurálja a tranzakciós adatok és az ügyféladatok közötti tevékenységet és kapcsolatot:  
   - Aktivitás típusa: Meglévő kiválasztása
   - Tevékenység címkéje: Vélemény
   - Megfelelő címke: Website.Reviews.UserId
   - Ügyfélentitás: eCommerceContacts:eCommerce
   - Kapcsolat: WebsiteReviews

1. Válassza a **Következő** lehetőséget a modell ütemezésének beállításához.

   Ezt a modellt rendszeresen tanítani kell, hogy új mintákat tanuljon, amikor új adatokat töltenek be. Ebben a példában válassza a **Havi** lehetőséget.

1. A részletek áttekintése után válassza a **Mentés és Futtatás** lehetőséget.

## <a name="task-4---review-model-results-and-explanations"></a>4. feladat – Modell eredmények és a magyarázatok áttekintése

Hagyja, hogy a modell teljesítse az adatok betanítását és pontozását. Ezután áttekintheti a CLV modell eredményeit és a magyarázatokat. További tudnivalókért olvassa el az [Előrejelzés állapotának és eredmények áttekintése](predict-customer-lifetime-value.md#review-prediction-status-and-results) című témakört.

## <a name="task-5---create-a-segment-of-high-value-customers"></a>5. feladat - Nagy értékű ügyfelek szegmensének létrehozása

A modell futtatása új entitást hoz létre, amely listázva van az **Adatok** > **Entitások** helyen. Új ügyfélszegmenst hozhat létre a modell által létrehozott entitás alapján.

1. Kattintson a **Szegmensek** lehetőségre. 

1. Válassza az **Új** lehetőséget, és válassza a **Létrehozás a következőkből** > **Információk** lehetőséget.

   ![Szegmens létrehozása a modell kimenetével.](media/segment-intelligence.png)

1. Válassza ki az **OOBeCommerceCLVPrediction** entitást, és definiálja a szegmenst:
  - Mező: CLVScore
  - Operátor: nagyobb, mint
  - Érték: 1500

1. Válassza a **Vélemény** lehetőséget, és **Mentse** a szegmenst.

Most már van egy szegmens, amely azonosítja azokat az ügyfeleket, akik az előrejelzések szerint több mint 1500 dollár bevételt generálnak a következő 12 hónapban. Ez a szegmens dinamikusan frissül, ha több adatot vesz fel.

További információ: [Szegmensek létrehozása és kezelése](segments.md).