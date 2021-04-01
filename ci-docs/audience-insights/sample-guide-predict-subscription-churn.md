---
title: Az Előfizetés-lemorzsolódási előrejelzési példamutató
description: Használja ezt a példamutatót, hogy kipróbálhassa a mezőn kívüli előfizetés lemorzsolódási modellt.
ms.date: 11/19/2020
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: tutorial
author: diegogranados117
ms.author: digranad
manager: shellyha
ms.openlocfilehash: 324e5c19778230dd978b2f4e9156a2dd82b3d2bd
ms.sourcegitcommit: bae40184312ab27b95c140a044875c2daea37951
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/15/2021
ms.locfileid: "5595521"
---
# <a name="subscription-churn-prediction-preview-sample-guide"></a>Előfizetés-lemorzsolódási előrejelzési (előnézet) példamutató

Elejétől végéig bemutatunk Önnek egy példán keresztül a egy előfizetés lemorzsolódási előrejelzést, használva az alább megadott példaadatokat. 

## <a name="scenario"></a>Forgatókönyv

A Contoso egy vállalat, amely kiváló minőségű kávét és kávégépet árusít, melyet a Contoso Coffee weboldalán keresztül adnak el. A közelmúltban indítottak el egy előfizetéses üzletet ügyfeleiknek, hogy azok rendszeresen megkaphassák kávéjukat. Céljuk, hogy megérthessék, melyik előfizetett ügyfelük fogja visszavonni előfizetését az elkövetkező pár hónapban. Tudva, melyek azok az ügyfelek, akik **várhatóan a lemorzsolódnak**, segítséget nyújthatnak a marketing-erőfeszítések megtakarításában, azzal, hogy megtartják őket.

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

1. A jobb oldali panelben a **Név** mezőben nevezze át az adatforrását a **Lekérdezés** értékről **eCommerceContacts** értékre

1. Az adatforrások mentése.

### <a name="ingest-customer-data-from-loyalty-schema"></a>Ügyféladatok bevitele a hűségsémából

1. Hozzon létre egy adatforrást, melynek neve **LoyaltyScheme**, majd válassza az importálás lehetőséget, és jelölje ki a **Text/CSV** csatlakozót.

1. Adja meg az URL-címét az eCommerce kapcsolattartóknak https://aka.ms/ciadclasscustomerloyalty.

1. Az adatok szerkesztése közben válassza az **Átalakítás** lehetőséget, majd a **Használja az első sort fejlécként** lehetőséget.

1. Frissítse az adattípust az alább felsorolt oszlopokhoz:

   - **SzületésiDátum**: Dátum
   - **JutalmazásiPontok**: Egész Szám
   - **KészültEkkor**: Dátum/Idő

1. A **Név** mezőben, a jobb oldali panelen, nevezze át az adatforrását **Lekérdezés** helyett **loyCustomers** értékre.

1. Az adatforrások mentése.

### <a name="ingest-subscription-information"></a>Előfizetési információk betáplálása

1. Hozzon létre egy adatforrást, melynek neve **ElőfizetésiElőzmények**, majd válassza az importálás lehetőséget, és jelölje ki a **Text/CSV** csatlakozót.

1. Adja meg az URL-címét az eCommerce kapcsolattartóknak https://aka.ms/ciadchurnsubscriptionhistory.

1. Az adatok szerkesztése közben válassza az **Átalakítás** lehetőséget, majd a **Használja az első sort fejlécként** lehetőséget.

1. Frissítse az adattípust az alább felsorolt oszlopokhoz:

   - **ElőfizetésAzonosító**: Egész szám
   - **ElőfizetésiÖsszeg**: Pénznem
   - **ElőfizetésVégénekDátuma**: Dátum/Idő
   - **ElőfizetésKezdeténekDátuma**: Dátum/Idő
   - **TranzakcióDátuma**: Dátum/Idő
   - **IsIsmétlődés**: Igaz/Hamis
   - **Is_auto_megújítás**: Igaz/Hamis
   - **IsmétlődésiGyakoriságInHónapok**: Egész Szám

1. A **Név** mezőben a jobb oldali panelen, nevezze át az adatforrását **Lekérdezés**-ről **SubscriptionHistory**-ra.

1. Az adatforrások mentése.

### <a name="ingest-customer-data-from-website-reviews"></a>Tápláljon be ügyféladatokat a webhely értékelésekből.

1. Hozzon létre egy adatforrást, **eCommerce** néven, majd válassza az importálás lehetőséget, és jelölje ki a **Text/CSV** csatlakozót.

1. Adja meg az URL-címét az eCommerce kapcsolattartóknak https://aka.ms/ciadclasswebsite.

1. Az adatok szerkesztése közben válassza az **Átalakítás** lehetőséget, majd a **Használja az első sort fejlécként** lehetőséget.

1. Frissítse az adattípust az alább felsorolt oszlopokhoz:

   - **ÁttekintésiMinősítés**: Egész Szám
   - **ÁttekintésDátuma**: Dátum

1. A "Név" mezőben, a jobb oldali panelen, nevezze át az adatforrását **Lekérdezés**-ről **webReviews**-re.

## <a name="task-2---data-unification"></a>2. feladat - Adatok egységesítése

Az adatok bevitele után elkezdhetjük a **Megfeleltetés/Egyeztetés/Egyesítés** folyamatot, hogy hogy létrehozzunk egy egyesített ügyfélprofilt. További információkért lásd: [Adatok egységesítése](data-unification.md).

### <a name="map"></a>Map

1. Az adatok betáplálása után képezze le a kapcsolattartókat az eCommerce-ből és a Loyalty data-ból a közös adattípusokba. Nyissa meg az **Adatok** > **Egységesítés** > **Megfeleltetés**-t.

1. Válassza ki az entitást, amely jelképezi az ügyfélprofilt – **eCommerceContacts** és **loyCustomers**. 

   :::image type="content" source="media/unify-ecommerce-loyalty.PNG" alt-text="az ecommerce és a loyality adatforrások egységesítése.":::

1. Jelölje ki a **ContactId**-t elsődleges kulcsaként az **eCommerceContacts**-hoz és a **LoyaltyID** a **loyCustomers** elsődleges kulcsaként.

   :::image type="content" source="media/unify-loyaltyid.PNG" alt-text="A LoyaltyId egyesítheti elsődleges kulcsként.":::

### <a name="match"></a>Egyeztetés

1. Ugorjon az **Egyeztetés** lapra és válassza a **Sorrend beállítását**.

1. Az **Elsődleges** legördülő listában válassza az **eCommerceContacts : eCommerce** lehetőséget elsődleges forrásként, amely minden rekordot magában foglal.

1. Az **Entitás 2** legördülő listájában válassza ki a **loyCustomers: LoyaltyScheme** lehetőséget, és adja meg az összes rekordot.

   :::image type="content" source="media/unify-match-order.PNG" alt-text="Az egységesítéshez egyeztesse az eCommerce-t és a Loyality-t.":::

1. Válassza az **Új szabály létrehozása** menüpontot

1. Adja hozzá az első feltételt a FullName segítségével.

   * Az eCommerceContacts lehetőséghez válassza ki a **FullName** opciót a legördülő listából.
   * A loyCustumers lehetőséghez válassza ki a **FullName** opciót a legördülő listából.
   * Jelölje ki a **Normalizálás** legördülő parancsot, és válassza a **Típus (Telefon, Név, Cím,...)** lehetőséget.
   * Állítsa be a **Pontossági szintet**: **Alap** és **Érték**: **Magas**-ra.

1. Adja meg a nevét **FullName, Email**, az új szabályhoz.

   * Másik feltétel hozzáadása az e-mail címhez a **Feltétel hozzáadása** lehetőség választásával.
   * Az eCommerceContacts entitáshoz válassza az **Email** legördülő lehetőséget.
   * Az loyCustomers entitáshoz válassza az **Email** legördülő lehetőséget. 
   * Hagyja üresen a Normalizálást. 
   * Állítsa be a **Pontossági szintet**: **Alap** és **Érték**: **Magas**-ra.

   :::image type="content" source="media/unify-match-rule.PNG" alt-text="Egységesítése az egyezési szabályt a névhez és az e-mailhez.":::

7. Válassza a **Mentés** és **Futtatás** lehetőséget.

### <a name="merge"></a>Összefűzés

1. Nyissa meg az **Egyesítés** lapot.

1. A **ContactId** **loyCustomers** entitáshoz változtassa meg a megjelenítendő nevet **ContactIdLOYALTY**-ra, hogy megkülönböztethesse azt a többi betáplált azonosítóval.

   :::image type="content" source="media/unify-merge-contactid.PNG" alt-text="nevezze át a loyalty azonosítót contactid-re.":::

1. Válassza a **Mentés** és **Futtatás** lehetőséget, hogy elindítsa a Egyesítés Folyamatot.


## <a name="task-3---configure-the-subscription-churn-prediction"></a>3. feladat – Konfigurálja az előfizetés lemorzsolódási előrejelzést

Az egységesített ügyfélprofilok elkészítése után, előfizetés lemorzsolódási előrejelzést futtathatunk. A részletes lépésekért lásd az [Előfizetés lemorzsolódási előrejelzés (előnézet)](predict-subscription-churn.md) című cikket. 

1. Nyissa meg az **Intelligencia** > **Felfedezés** elemet, és válassza az **Ügyfél-lemorzsolódási modell** használatát.

1. Válassza az **Előfizetés** beállítást, majd válassza ki a **Kezdő lépések** lehetőséget.

1. Nevezze el a modellt **OOB Előfizetés-lemorzsolódási Előrejelzés**-nek és a kimeneti entitást **OOBElőfizetés-lemorzsolódásiElőrejelzés**-nek.

1. Határozzon meg két feltételt a lemorzsolódási modellhez.

   * **Amióta az előfizetés véget ért**: **legalább 60** nap. Ha egy ügyfél nem újítja meg előfizetését ebben az időszakban, miután előző előfizetése lejárt, lemorzsolódónak tekintendő. 

   * **Lemorzsolódás meghatározása**: **legalább 93** nap. Az az időtartam, ami alatt a modell megjósolja, hogy mely ügyfelek morzsolódhatnak le. Minél távolabb tekint a jövőben, annál kevésbé pontosak az eredmények.

     :::image type="content" source="media/model-subs-levers.PNG" alt-text="Válassza ki a modellt, amely előhozza az Előrejelzési Ablakot és a Lemorzsolódás Meghatározását.":::

1. Válassza ki a **Szükséges adatok hozzáadása** menüt, és ott válassza az **Adatok hozzáadása** lehetőséget az előfizetési előzményekhez.

1. Adja hozzá a **Előfizetés : ElőfizetésiElőzmények** entitást és képezze le a mezőket az eCommerce-ből a megfelelő mezőkre, melyek modell által megköveteltek.

1. Csatlakoztassa az **Előfizetés : ElőfizetésiElőzmények** entitáshoz az **eCommerceContacts : eCommerce**-t, nevezze el a kapcsolatot **eCommerceElőfizetések**-nek.

   :::image type="content" source="media/model-subscription-join.PNG" alt-text="Csatlakoztassa az eCommerce entitásokhoz.":::

1. Az Ügyféltevékenység alatt adja hozzá a **webReviews : Website** entitást és képezze le a mezőket a webReviewsból a megfelelő mezőkre, melyek modell által megköveteltek. 
   - Elsődleges kulcs: ÉrtékelésId
   - Időbélyege: ÉrtékelésDátuma
   - Esemény: ÉrtékelésMinősítése

1. Konfiguráljon egy tevékenységet a webhely értékeléseknek. Válassza ki az **Értékelés** tevékenységet és csatlakoztassa a **webÉrtékelések : Weboldal** entitást az **eCommerceContacts : eCommerce**-hez.

1. Válassza a **Következő** lehetőséget a modell ütemezésének beállításához.

   A modell rendszeres betanítást igényel ahhoz, hogy új mintákat tanulhasson, amikor új adatok kerülnek a rendszerbe. Ennél a példánál válassza a **Havonta** beállítást.

1. A részletek áttekintése után válassza a **Mentés és Futtatás** lehetőséget.

## <a name="task-4---review-model-results-and-explanations"></a>4. feladat – Modell eredmények és a magyarázatok áttekintése

Hagyja, hogy a modell teljesítse az adatok betanítását és pontozását. Most már megtekintheti az előfizetési lemorzsolódás modell magyarázatait. További tudnivalókért olvassa el az [Előrejelzés állapotának és eredmények áttekintése](predict-subscription-churn.md#review-a-prediction-status-and-results) című témakört.

## <a name="task-5---create-a-segment-of-high-churn-risk-customers"></a>5. feladat – Hozzon létre egy szegmenst a nagy lemorzsolódási kockázatú ügyfelekről

Futtatva a termékjavaslati modellt, létrehozhat egy új entitást, amelyet láthat a **Adat** > **Entitások**-nál.   

Létrehozhat egy új szegmenst, a modell által létrehozott entitás alapján.

1.  Kattintson a **Szegmensek** lehetőségre. Válassza az **Új** lehetőséget, és válassza a **Létrehozás a következőkből** > **Intelligencia**. 

   :::image type="content" source="media/segment-intelligence.PNG" alt-text="Szegmens létrehozása a modell kimenetével.":::

1. Válassza ki a **OOBSubscriptionChurnPrediction** végpontot és definiálja a szegmenst: 
   - Mező: ChurnScore
   - Operátor: nagyobb, mint
   - Érték: 0,6
   
   :::image type="content" source="media/segment-setup-subs.PNG" alt-text="Állítsa be az előfizetési lemorzsolódási szegmenset.":::

Most már van egy szegmense, amely dinamikusan frissítve van, és amely meghatározza a magas lemorzsolódási kockázatot ennek az üzleti előfizetésnek az esetén.

További információ: [Szegmensek létrehozása és kezelése](segments.md).


[!INCLUDE[footer-include](../includes/footer-banner.md)]