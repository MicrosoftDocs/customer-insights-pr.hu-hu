---
title: Előrejelzési kimeneten alapuló szegmensek
description: Szegmensek létrehozása egy előrejelzési modell kimeneti entitása alapján.
ms.date: 03/24/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: zacookmsft
ms.author: zacook
manager: shellyha
ms.openlocfilehash: 488db1af865ce600ec012716327d053bee33aff8
ms.sourcegitcommit: a95c82f46c23f625cb34fceba021ccc70d4b1df6
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/30/2021
ms.locfileid: "5741432"
---
# <a name="create-a-segment-based-on-a-prediction-model-preview"></a><span data-ttu-id="b130d-103">Szegmens létrehozása egy előrejelzési modell (előzetes verzió) alapján</span><span class="sxs-lookup"><span data-stu-id="b130d-103">Create a segment based on a prediction model (preview)</span></span>

<span data-ttu-id="b130d-104">Az előrejelzések eredményei néha csak az ügyfelek egy részhalmazára vonatkoznak.</span><span class="sxs-lookup"><span data-stu-id="b130d-104">The results of predictions sometimes only apply to a subset of your customers.</span></span> <span data-ttu-id="b130d-105">A javaslatok személyre szabásának növelése az előrejelzési modellek eredményeiből való szegmensek létrehozásával.</span><span class="sxs-lookup"><span data-stu-id="b130d-105">Increase the personalization of recommendations by creating segments from results of prediction models.</span></span> <span data-ttu-id="b130d-106">Előfordulhat például, hogy konkrét javaslatokat szeretne adni egy adott szolgáltatástípust előnyben részesítő ügyfeleknek.</span><span class="sxs-lookup"><span data-stu-id="b130d-106">For example, you may want to give specific recommendations to customers that prefer a certain type of service.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="b130d-107">Előfeltételek</span><span class="sxs-lookup"><span data-stu-id="b130d-107">Prerequisites</span></span>

- <span data-ttu-id="b130d-108">Legalább [közreműködői engedély](permissions.md) a Customer Insightsban.</span><span class="sxs-lookup"><span data-stu-id="b130d-108">At least [Contributor permissions](permissions.md) in Customer Insights.</span></span>

- <span data-ttu-id="b130d-109">A Customer Insightsban konfigurált termékjavaslat, tranzakciós lemorzsolódás, előfizetési lemorzsolódás, vagy ügyfél élettartamra vetített értékmodell.</span><span class="sxs-lookup"><span data-stu-id="b130d-109">A product recommendation, transactional churn, subscription churn, or customer lifetime value model configured in Customer Insights.</span></span> <span data-ttu-id="b130d-110">A különböző modellek beállításához tekintse át a követelményeket:</span><span class="sxs-lookup"><span data-stu-id="b130d-110">Review the requirements to set up the different models:</span></span>

  - [<span data-ttu-id="b130d-111">Termékjavaslati modell</span><span class="sxs-lookup"><span data-stu-id="b130d-111">Product recommendation model</span></span>](predict-product-recommendation.md)
  - [<span data-ttu-id="b130d-112">Előfizetési lemorzsolódás modellje</span><span class="sxs-lookup"><span data-stu-id="b130d-112">Subscription churn model</span></span>](predict-subscription-churn.md)
  - [<span data-ttu-id="b130d-113">Tranzakciós lemorzsolódási modell</span><span class="sxs-lookup"><span data-stu-id="b130d-113">Transactional churn model</span></span>](predict-transactional-churn.md)
  - [<span data-ttu-id="b130d-114">Ügyfél élettartamára levetített értékmodell</span><span class="sxs-lookup"><span data-stu-id="b130d-114">Customer lifetime value model</span></span>](predict-customer-lifetime-value.md)

## <a name="create-a-customer-segment-based-on-predictions"></a><span data-ttu-id="b130d-115">Ügyfélszegmens létrehozása előrejelzések alapján</span><span class="sxs-lookup"><span data-stu-id="b130d-115">Create a customer segment based on predictions</span></span>

1. <span data-ttu-id="b130d-116">Nyissa meg az **Intelligencia** > **Előrejelzések** menüt, és válassza ki a **Saját előrejelzések** lapot.</span><span class="sxs-lookup"><span data-stu-id="b130d-116">Go to **Intelligence** > **Predictions** and select the **My predictions** tab.</span></span>

1. <span data-ttu-id="b130d-117">Válassza ki az áttekinteni kívánt modell melletti függőleges három pontot, majd válassza a **Nézet** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="b130d-117">Select the vertical ellipses next to the model you want to review and select **View**.</span></span>

1. <span data-ttu-id="b130d-118">Az eredmény lapon válassza a **Szegmens létrehozása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="b130d-118">On the results page, select **Create segment**.</span></span> <span data-ttu-id="b130d-119">Az eredmények oldallal kapcsolatos további tudnivalókat a modellt ismertető cikk tartalmaz.</span><span class="sxs-lookup"><span data-stu-id="b130d-119">For more information about the results page, review the article about the model.</span></span>

   :::image type="content" source="media/prediction-create-segment.png" alt-text="Képernyőkép az előrejelzés eredményei oldalról, a Szegmensművelet létrehozása kiemelésével.":::

1. <span data-ttu-id="b130d-121">Új szegmens létrehozása egy kiválasztott modell kimeneti entitása alapján.</span><span class="sxs-lookup"><span data-stu-id="b130d-121">Create a new segment based on the output entity of the selected model.</span></span> <span data-ttu-id="b130d-122">További információ: [Szegmensek létrehozása és kezelése](segments.md).</span><span class="sxs-lookup"><span data-stu-id="b130d-122">For more information, see [Create and manage segments](segments.md).</span></span>