---
title: Előrejelzések áttekintése
description: A Dynamics 365 Customer Insights alkalmazás által lefedett előrejelzési forgatókönyvek és lehetőségek.
ms.date: 03/24/2022
ms.reviewer: mhart
ms.subservice: audience-insights
ms.topic: overview
author: zacookmsft
ms.author: zacook
manager: shellyha
ms.openlocfilehash: a87af80fa713a1ac70493345c0c920e416692b0f
ms.sourcegitcommit: dca46afb9e23ba87a0ff59a1776c1d139e209a32
ms.translationtype: MT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/29/2022
ms.locfileid: "9083100"
---
# <a name="predictions-overview"></a>Előrejelzések áttekintése

A Dynamics 365 Customer Insights számos olyan lehetőséggel rendelkezik, amelyek kihasználják az AI-t és a gépi tanulást az adatok előrejelzéséhez. 

## <a name="out-of-box-models"></a>Beépített modellek

Az adatok előrejelzésével való elindulás legegyszerűbb módja az előre definiált modellek használata, amelyeket gyakran beépített modelleknek neveznek. Csak bizonyos adatokra és struktúrára van szükségük ahhoz, hogy gyorsan elemzéseket generáljanak. Jelenleg a következő modellek állnak rendelkezésre: 

# <a name="individual-consumers-b-to-c"></a>[Egyéni fogyasztók (B-to-C)](#tab/b2c)

- [Ügyfél élettartamra vetített értéke](predict-customer-lifetime-value.md) : Előrejelzi az ügyfélhez kapcsolódó potenciális bevételt a vállalkozással való teljes interakció során.
- [Termékajánlás](predict-product-recommendation.md) : Prediktív termékajánlásokat javasol a vásárlási viselkedés és a hasonló vásárlási mintákkal rendelkező ügyfelek alapján.
- [előfizetés-lemorzsolódás](predict-subscription-churn.md) Megjósolja, hogy fennáll-e az ügyfélnél annak veszélye, hogy a jövőben már nem az Ön vállalatának termékeit vagy szolgáltatásait veszi igénybe.
- [Tranzakciós lemorzsolódás](predict-transactional-churn.md) : Megjósolja, hogy egy ügyfél egy bizonyos időkeret után már nem vásárolja meg termékeit vagy szolgáltatásait.
- [Hangulatelemzés](sentiment-analysis.md): Elemezze az ügyfelek visszajelzéseinek hangulatát, és azonosítsa a gyakran említett üzleti szempontokat.

# <a name="business-accounts-b-to-b"></a>[Üzleti számlák (B-to-B)](#tab/b2b)

- [Tranzakciós lemorzsolódás](predict-transactional-churn.md) : Megjósolja, hogy egy ügyfél egy bizonyos időkeret után már nem vásárolja meg termékeit vagy szolgáltatásait.

---

> [!TIP]
> Javasoljuk, hogy rendszeresen frissítse a beépített modelleket frissített adatokkal, hogy azok pontosan tájékoztassák az üzleti használati esetet. Az adatok ad-hoc módon frissülnek, amikor a rendszer új vagy frissített adatforrásokat tölt be. A modellek azonban ebben az esetben csak újrapontozzák a teljesítményt, és továbbra is a meglévő betanítási adatokat használják.
> 
> A frissítési ütemezést **úgy konfigurálhatja,** hogy beállítja a modell újraképzési ütemezését a konfigurációs élményben. A modell újratanítja és újrapontozza ezt az ütemezést, amelyet bármikor módosíthat.


## <a name="azure-machine-learning-integration"></a>Azure Machine Learning integrációja

Ha egy szervezet már használ az Azure Machine Learning kísérleteken alapuló forgatókönyveket, a Customer Insights egyéni modelljei segítenek a pontkapcsolatban. Hozzon létre olyan munkafolyamatokat, amelyek segítenek kiválasztani azokat az adatokat, amelyekből elemzéseket érdemes generálni, és az eredményeket az egységes ügyfélprofilokhoz térképezi fel. További tudnivalókat az [Egyéni gépi tanulás modellek](custom-models.md) című rész tartalmaz.

## <a name="ai-builder-prediction"></a>AI Builder előrejelzés

Néha az adatkészletek hiányosak, és néhány érték hiányzik. A Customer Insights segíthet megjósolni az ügyfél entitás és szegmenseinek hiányzó értékeit. További információ: [Egészítse ki a részleges adatait előrejelzésekkel](predictions.md).
