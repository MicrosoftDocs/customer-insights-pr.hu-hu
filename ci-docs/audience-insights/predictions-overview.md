---
title: Áttekintés a támogatott előrejelzési forgatókönyvekről
description: A Dynamics 365 Customer Insights alkalmazás által lefedett előrejelzési forgatókönyvek és lehetőségek.
ms.date: 05/18/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: get-started
author: zacookmsft
ms.author: zacook
manager: shellyha
ms.openlocfilehash: 69ae945b22819521db217508c6fc232876346747
ms.sourcegitcommit: 6b07c9c3102761be162e4842f3c9fbc19f948a9b
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/25/2021
ms.locfileid: "6095717"
---
# <a name="predictions-overview"></a>Előrejelzések áttekintése

A Dynamics 365 Customer Insights számos olyan lehetőséggel rendelkezik, amelyek kihasználják az AI-t és a gépi tanulást az adatok előrejelzéséhez. 

## <a name="out-of-box-models"></a>Beépített modellek

Az adatok előrejelzésével való elindulás legegyszerűbb módja az előre definiált modellek használata, amelyeket gyakran beépített modelleknek neveznek. Csak bizonyos adatokra és struktúrára van szükségük ahhoz, hogy gyorsan elemzéseket generáljanak. Jelenleg a következő modellek állnak rendelkezésre: 
- [Ügyfél élettartamra vetített értéke](predict-customer-lifetime-value.md) : Előrejelzi az ügyfélhez kapcsolódó potenciális bevételt a vállalkozással való teljes interakció során. 
- [Termékajánlás](predict-product-recommendation.md) : Prediktív termékajánlásokat javasol a vásárlási viselkedés és a hasonló vásárlási mintákkal rendelkező ügyfelek alapján.
- [előfizetés-lemorzsolódás](predict-subscription-churn.md) Megjósolja, hogy fennáll-e az ügyfélnél annak veszélye, hogy a jövőben már nem az Ön vállalatának termékeit vagy szolgáltatásait veszi igénybe.
- [Tranzakciós lemorzsolódás](predict-transactional-churn.md) : Megjósolja, hogy egy ügyfél egy bizonyos időkeret után már nem vásárolja meg termékeit vagy szolgáltatásait.

## <a name="azure-machine-learning-integration"></a>Azure Machine Learning integrációja

Ha egy szervezet már használ az Azure Machine Learning kísérleteken alapuló forgatókönyveket, a Customer Insights egyéni modelljei segítenek a pontkapcsolatban. Hozzon létre olyan munkafolyamatokat, amelyek segítenek kiválasztani azokat az adatokat, amelyekből elemzéseket érdemes generálni, és az eredményeket az egységes ügyfélprofilokhoz térképezi fel. További tudnivalókat az [Egyéni gépi tanulás modellek](custom-models.md) című rész tartalmaz.

## <a name="ai-builder-prediction"></a>AI Builder-előrejelzés

Néha az adatkészletek hiányosak, és néhány érték hiányzik. A Customer Insights segíthet megjósolni az ügyfél entitás és szegmenseinek hiányzó értékeit. További információ: [Egészítse ki a részleges adatait előrejelzésekkel](predictions.md).
