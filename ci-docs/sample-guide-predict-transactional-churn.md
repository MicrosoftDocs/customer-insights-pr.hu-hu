---
title: Tranzakcionális lemorzsolódási előrejelzési példamutató
description: Használja ezt a példamutatót, hogy kipróbálja a mezőn kívüli lemorzsolódás-előrejelzési modellt.
ms.date: 05/11/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: tutorial
author: m-hartmann
ms.author: mhart
manager: shellyha
ms.openlocfilehash: 3edbf2a471313379c28db874d7f19c3265a23299
ms.sourcegitcommit: 6a5f4312a2bb808c40830863f26620daf65b921d
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/11/2022
ms.locfileid: "8741322"
---
# <a name="transactional-churn-prediction-sample-guide"></a>Tranzakcionális lemorzsolódási előrejelzési példamutató

Ez az útmutató elejétől végéig bemutatja Önnek egy példán keresztül a tranzakciólemorzsolódási előrejelzést a Customer Insightsban, a lent megadott adatok használatával. Az ebben az útmutatóban felhasznált adatok nem valós ügyféladatok, és részei a Contoso-adatkészletnek, ami megtalálható a *Bemutató* környezetben a Customer Insights Előfizetésében.

## <a name="scenario"></a>Forgatókönyv

A Contoso egy vállalat, amely kiváló minőségű kávét és kávégépet árusít, melyet a Contoso Coffee weboldalán keresztül adnak el. Céljuk, hogy megtudják, mely ügyfelek azok, akik általában rendszeresen vásárolnak termékeket, mégis az elkövetkezendő 60 napon megszűnnek aktív ügyfelek lenni. Tudva, melyek azok az ügyfelek, akik **várhatóan a lemorzsolódnak**, segítséget nyújthatnak a marketing-erőfeszítések megtakarításában, azzal, hogy megtartják őket.

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

   :::image type="content" source="media/ecommerce-dob-date.PNG" alt-text="DoB átalakítása Dátummá.":::

1. A jobb oldali panelben a **Név** mezőben nevezze át az adatforrását a **Lekérdezés** értékről **eCommerceContacts** értékre

1. Az adatforrások mentése.

### <a name="ingest-online-purchase-data"></a>Online vásárlási adatok betáplálása.

1. Adjon hozzá egy újabb adatforrást a megegyező **eCommerce** adatforráshoz. Válassza a **Text/CSV** csatlakozót újra.

1. Adja meg az URL-címét az **Online vásárlas** adataihoz https://aka.ms/ciadclassonline.

1. Az adatok szerkesztése közben válassza az **Átalakítás** lehetőséget, majd a **Használja az első sort fejlécként** lehetőséget.

1. Frissítse az adattípust az alább felsorolt oszlopokhoz:

   - **PurchasedOn** : Dátum/Idő
   - **TotalPrice** : Pénznem
   
1. A **Név** mezőben a jobb oldali panelen, nevezze át az adatforrását a **Lekérdezés**-ről **eCommercePurchases**-ra.

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

## <a name="task-2---data-unification"></a>2. feladat - Adatok egységesítése

[!INCLUDE [sample-guide-unification](includes/sample-guide-unification.md)]

## <a name="task-3---configure-transaction-churn-prediction"></a>3. feladat – Konfigurálja a tranzakciót a lemorzsolódási előrejelzéshez.

Az egységes ügyfélprofilok meglétével most már előrejelzés futtathatjuk a tranzakciós lemorzsolódást. A részletes lépéseket a [Tranzakció lemorzsolódása előrejelzés](predict-transactional-churn.md) cikkben találja. 

1. Nyissa meg az **Intelligencia** > **Felfedezés** elemet, és válassza az **Ügyfél-lemorzsolódási modell** használatát.

1. Válassza a **Tranzakciós** beállítást, és válassza ki a **Kezdő lépések** lehetőséget.

1. Nevezze el a modellt **OOB eCommerce Lemorzsolódási Előrejelzés**-nek és a kimeneti entitást **OOBeCommerceChurnPrediction**-nak.

1. Határozzon meg két feltételt a lemorzsolódási modellhez.

   * **Előrejelzési ablak**: **legalább 60** nap. Ez a beállítás meghatározza, a jövőben milyen távol szeretné előre jelezni az ügyfél lemorzsolódást.

   * **Lemorzsolódás meghatározása**: **legalább 60** nap. A vásárlás nélküli időtartam, ami után egy ügyfél lemorzsolódónak minősül.

     :::image type="content" source="media/model-levers.PNG" alt-text="Válassza ki a modellt, amely előhozza az Előrejelzési Ablakot és a Lemorzsolódás Meghatározását.":::

1. Válassza ki a **Vásárlási előzményeket (kötelező)** és válassza az **Adatok hozzáadása** lehetőséget az vásárlási előzményekhez.

1. Adja hozzá a **eCommercePurchases: eCommerce** entitást és képezze le a mezőket az eCommerce-ről a megfelelő mezőkre, melyek modell által megköveteltek.

1. Csatlakozzon az **eCommercePurchases: eCommerce** entitáshoz az **eCommerceContacts: eCommerce**-szel.

   :::image type="content" source="media/model-purchase-join.PNG" alt-text="Csatlakoztassa az eCommerce entitásokhoz.":::

1. Válassza a **Következő** lehetőséget a modell ütemezésének beállításához.

   A modell rendszeres betanítást igényel ahhoz, hogy új mintákat tanulhasson, amikor új adatok kerülnek a rendszerbe. Ennél a példánál válassza a **Havonta** beállítást.

1. A részletek áttekintése után válassza a **Mentés és Futtatás** lehetőséget.

## <a name="task-4---review-model-results-and-explanations"></a>4. feladat – Modell eredmények és a magyarázatok áttekintése

Hagyja, hogy a modell teljesítse az adatok betanítását és pontozását. Most áttekintheti a lemorzsolódási modell magyarázatait. További tudnivalókért olvassa el az [Előrejelzés állapotának és eredmények áttekintése](predict-transactional-churn.md#review-a-prediction-status-and-results) című témakört.

## <a name="task-5---create-a-segment-of-high-churn-risk-customers"></a>5. feladat – Hozzon létre egy szegmenst a nagy lemorzsolódási kockázatú ügyfelekről

Futtatva a termékjavaslati modellt, létrehozhat egy új entitást, amelyet láthat a **Adat** > **Entitások**-nál.   

Létrehozhat egy új szegmenst, a modell által létrehozott entitás alapján.

1.  Kattintson a **Szegmensek** lehetőségre. Válassza az **Új** lehetőséget, és válassza a **Létrehozás a következőkből** > **Intelligencia**. 

   :::image type="content" source="media/segment-intelligence.PNG" alt-text="Szegmens létrehozása a modell kimenetével.":::

1. Válassza ki az **OOBeCommerceChurnPrediction** végpont, és határozza meg a szegmenst: 
   - Mező: ChurnScore
   - Operátor: nagyobb, mint
   - Érték: 0,6

Most már van egy dinamikusan frissített szegmense, amely azonosítja a magas lemorzsolódási kockázatú ügyfeleket.

További információ: [Szegmensek létrehozása és kezelése](segments.md).


[!INCLUDE [footer-include](includes/footer-banner.md)]
