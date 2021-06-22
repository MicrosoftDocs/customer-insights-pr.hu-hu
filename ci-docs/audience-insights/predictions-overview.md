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
# <a name="predictions-overview"></a><span data-ttu-id="daed1-103">Előrejelzések áttekintése</span><span class="sxs-lookup"><span data-stu-id="daed1-103">Predictions overview</span></span>

<span data-ttu-id="daed1-104">A Dynamics 365 Customer Insights számos olyan lehetőséggel rendelkezik, amelyek kihasználják az AI-t és a gépi tanulást az adatok előrejelzéséhez.</span><span class="sxs-lookup"><span data-stu-id="daed1-104">Dynamics 365 Customer Insights comes with a variety of options that leverage AI and machine learning to predict data.</span></span> 

## <a name="out-of-box-models"></a><span data-ttu-id="daed1-105">Beépített modellek</span><span class="sxs-lookup"><span data-stu-id="daed1-105">Out-of-box models</span></span>

<span data-ttu-id="daed1-106">Az adatok előrejelzésével való elindulás legegyszerűbb módja az előre definiált modellek használata, amelyeket gyakran beépített modelleknek neveznek.</span><span class="sxs-lookup"><span data-stu-id="daed1-106">The easiest way to start with predicting data are predefined models, often referred to as out-of-box models.</span></span> <span data-ttu-id="daed1-107">Csak bizonyos adatokra és struktúrára van szükségük ahhoz, hogy gyorsan elemzéseket generáljanak.</span><span class="sxs-lookup"><span data-stu-id="daed1-107">They only require certain data and structure to generate insights quickly.</span></span> <span data-ttu-id="daed1-108">Jelenleg a következő modellek állnak rendelkezésre:</span><span class="sxs-lookup"><span data-stu-id="daed1-108">Currently, the following models are available:</span></span> 
- <span data-ttu-id="daed1-109">[Ügyfél élettartamra vetített értéke](predict-customer-lifetime-value.md) : Előrejelzi az ügyfélhez kapcsolódó potenciális bevételt a vállalkozással való teljes interakció során.</span><span class="sxs-lookup"><span data-stu-id="daed1-109">[Customer lifetime value](predict-customer-lifetime-value.md): Predicts the potential revenue of a customer throughout the entire interaction with a business.</span></span> 
- <span data-ttu-id="daed1-110">[Termékajánlás](predict-product-recommendation.md) : Prediktív termékajánlásokat javasol a vásárlási viselkedés és a hasonló vásárlási mintákkal rendelkező ügyfelek alapján.</span><span class="sxs-lookup"><span data-stu-id="daed1-110">[Product recommendation](predict-product-recommendation.md): Suggests sets of predictive product recommendations based on purchase behavior and customers with similar purchase patterns.</span></span>
- <span data-ttu-id="daed1-111">[előfizetés-lemorzsolódás](predict-subscription-churn.md) Megjósolja, hogy fennáll-e az ügyfélnél annak veszélye, hogy a jövőben már nem az Ön vállalatának termékeit vagy szolgáltatásait veszi igénybe.</span><span class="sxs-lookup"><span data-stu-id="daed1-111">[Subscription churn](predict-subscription-churn.md): Predicts whether a customer is at risk for no longer using your company’s subscription products or services.</span></span>
- <span data-ttu-id="daed1-112">[Tranzakciós lemorzsolódás](predict-transactional-churn.md) : Megjósolja, hogy egy ügyfél egy bizonyos időkeret után már nem vásárolja meg termékeit vagy szolgáltatásait.</span><span class="sxs-lookup"><span data-stu-id="daed1-112">[Transactional churn](predict-transactional-churn.md): Predict if a customer will no longer purchase your products or services in a certain time frame.</span></span>

## <a name="azure-machine-learning-integration"></a><span data-ttu-id="daed1-113">Azure Machine Learning integrációja</span><span class="sxs-lookup"><span data-stu-id="daed1-113">Azure Machine Learning integration</span></span>

<span data-ttu-id="daed1-114">Ha egy szervezet már használ az Azure Machine Learning kísérleteken alapuló forgatókönyveket, a Customer Insights egyéni modelljei segítenek a pontkapcsolatban.</span><span class="sxs-lookup"><span data-stu-id="daed1-114">If an organization already uses machine learning scenarios based on Azure Machine Learning experiments, the custom models feature in Customer Insights helps to connect the dots.</span></span> <span data-ttu-id="daed1-115">Hozzon létre olyan munkafolyamatokat, amelyek segítenek kiválasztani azokat az adatokat, amelyekből elemzéseket érdemes generálni, és az eredményeket az egységes ügyfélprofilokhoz térképezi fel.</span><span class="sxs-lookup"><span data-stu-id="daed1-115">Create workflows that help you choose the data you want to generate insights from and map the results to your unified customer profiles.</span></span> <span data-ttu-id="daed1-116">További tudnivalókat az [Egyéni gépi tanulás modellek](custom-models.md) című rész tartalmaz.</span><span class="sxs-lookup"><span data-stu-id="daed1-116">For more information, see [Custom machine learning models](custom-models.md).</span></span>

## <a name="ai-builder-prediction"></a><span data-ttu-id="daed1-117">AI Builder-előrejelzés</span><span class="sxs-lookup"><span data-stu-id="daed1-117">AI Builder prediction</span></span>

<span data-ttu-id="daed1-118">Néha az adatkészletek hiányosak, és néhány érték hiányzik.</span><span class="sxs-lookup"><span data-stu-id="daed1-118">Sometimes, data sets are incomplete and some values are missing.</span></span> <span data-ttu-id="daed1-119">A Customer Insights segíthet megjósolni az ügyfél entitás és szegmenseinek hiányzó értékeit.</span><span class="sxs-lookup"><span data-stu-id="daed1-119">Customer Insights can help to predict missing values for the Customer entity and segments.</span></span> <span data-ttu-id="daed1-120">További információ: [Egészítse ki a részleges adatait előrejelzésekkel](predictions.md).</span><span class="sxs-lookup"><span data-stu-id="daed1-120">For more information, see [Complete your partial data with predictions](predictions.md).</span></span>
