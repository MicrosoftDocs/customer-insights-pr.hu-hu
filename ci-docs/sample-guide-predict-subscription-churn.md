---
title: Az Előfizetés-lemorzsolódási előrejelzési példamutató
description: Használja ezt a példamutatót, hogy kipróbálhassa a mezőn kívüli előfizetés lemorzsolódási modellt.
ms.date: 03/31/2022
ms.reviewer: v-wendysmith
ms.subservice: audience-insights
ms.topic: tutorial
author: m-hartmann
ms.author: wameng
manager: shellyha
searchScope:
- ci-create-prediction
- customerInsights
ms.openlocfilehash: 5a8eeafecacef3d0bb4a798b698cf490423ca98d
ms.sourcegitcommit: 6a5f4312a2bb808c40830863f26620daf65b921d
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/11/2022
ms.locfileid: "8741414"
---
# <a name="subscription-churn-prediction-sample-guide"></a>Az Előfizetés-lemorzsolódási előrejelzési példamutató

Elejétől végéig bemutatunk Önnek egy példán keresztül a egy előfizetés lemorzsolódási előrejelzést, használva az alább megadott példaadatokat. 

## <a name="scenario"></a>Forgatókönyv

A Contoso egy vállalat, amely kiváló minőségű kávét és kávégépet árusít, melyet a Contoso Coffee weboldalán keresztül adnak el. A közelmúltban indítottak el egy előfizetéses üzletet ügyfeleiknek, hogy azok rendszeresen megkaphassák kávéjukat. Céljuk, hogy megérthessék, melyik előfizetett ügyfelük fogja visszavonni előfizetését az elkövetkező pár hónapban. Tudva, melyek azok az ügyfelek, akik **várhatóan a lemorzsolódnak**, segítséget nyújthatnak a marketing-erőfeszítések megtakarításában, azzal, hogy megtartják őket.

## <a name="prerequisites"></a>Előfeltételek

- Legalább [közreműködői engedély](permissions.md) a Customer Insightsban.
- Javasoljuk, hogy a következő lépéseket hajtsa végre [egy új környezetben](manage-environments.md).

## <a name="task-1---ingest-data"></a>1. Feladat - Adatok betáplálása

Tekintse át az adatbetöltésről [és](data-sources.md) az adatforrások speciális összekötőkkel [történő Power Query importálásáról szóló cikkeket](connect-power-query.md). A következő információk azt feltételezik, hogy megismerkedett a betáplált adatokkal általánosságban. 

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

[!INCLUDE [sample-guide-unification](includes/sample-guide-unification.md)]

## <a name="task-3---configure-the-subscription-churn-prediction"></a>3. feladat – Konfigurálja az előfizetés lemorzsolódási előrejelzést

Az egységesített ügyfélprofilok elkészítése után, előfizetés lemorzsolódási előrejelzést futtathatunk. A részletes lépéseket az [Előfizetés lemorzsolódása előrejelzés](predict-subscription-churn.md) cikkben találja. 

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


[!INCLUDE [footer-include](includes/footer-banner.md)]