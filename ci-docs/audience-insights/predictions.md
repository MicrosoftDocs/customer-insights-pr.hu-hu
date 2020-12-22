---
title: Részleges adatok kitöltése előrejelzések használatával
description: Az előrejelzések segítségével töltse ki a hiányos ügyféladatokat.
ms.date: 05/05/2020
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: mhart
ms.reviewer: zacook
manager: shellyha
ms.openlocfilehash: 66f0b16b5d05741ab98ca5ce2157da8c46b6d9e0
ms.sourcegitcommit: 5379c2b77d613d071a177f509e6417ebf3c47516
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 11/26/2020
ms.locfileid: "4648714"
---
# <a name="complete-your-partial-data-with-predictions"></a><span data-ttu-id="31231-103">Részleges adatok kiegészítése előrejelzésekkel</span><span class="sxs-lookup"><span data-stu-id="31231-103">Complete your partial data with predictions</span></span>

[!INCLUDE [cc-data-platform-banner](../includes/cc-data-platform-banner.md)]

<span data-ttu-id="31231-104">Az előrejelzések segítségével egyszerűen hozhat létre olyan előre jelzett értékeket, amelyek segíthetik az ügyfél megértését.</span><span class="sxs-lookup"><span data-stu-id="31231-104">Predictions lets you easily create predicted values that can enhance your understanding of a customer.</span></span> <span data-ttu-id="31231-105">Az **Intelligencia** > **Előrejelzések** oldalon kiválaszthatja a **Saját előrejelzések** elemet a célközönség-információk más részein konfigurált előrejelzések megtekintéséhez, és lehetővé teszi a további testreszabást.</span><span class="sxs-lookup"><span data-stu-id="31231-105">On the **Intelligence** > **Predictions** page, you can select **My predictions** to see predictions that you've configured in other parts of audience insights, and allow you to further customize them.</span></span>

> [!NOTE]
> <span data-ttu-id="31231-106">Ez a funkció nem használható, ha a környezet Azure Data Lake Gen 2 tárhelyet használ.</span><span class="sxs-lookup"><span data-stu-id="31231-106">You can't use this feature if your environment uses Azure Data Lake Gen 2 storage.</span></span>
>
> <span data-ttu-id="31231-107">Az előrejelzések funkció automatizált eszközöket használ az adatok értékelésére és az előrejelzések készítésére az adott adatok alapján, és így képes a profilkészítési módszerként használni, abban az értelemben, ahogy ezt a kifejezést az általános adatvédelmi rendelet ("GDPR") meghatározza.</span><span class="sxs-lookup"><span data-stu-id="31231-107">The predictions feature uses automated means to evaluate data and make predictions based on that data, and therefore has the capability to be used as a method of profiling, as that term is defined by the General Data Protection Regulation ("GDPR").</span></span> <span data-ttu-id="31231-108">Ha az ügyfél ezt a funkciót adatok feldolgozására használja, az a GDPR vagy más törvények és szabályozások hatálya alá tartozhat.</span><span class="sxs-lookup"><span data-stu-id="31231-108">Customer's use of this feature to process data may be subject to GDPR or other laws or regulations.</span></span> <span data-ttu-id="31231-109">Felelős azért, hogy biztosítsa, hogy a Dynamics 365 Customer Insights használata, az előrejelzésekkel együtt, megfelel a vonatkozó törvényeknek és szabályozásoknak, többek között az adatvédelemmel, személyes adatokkal, biometrikus adatokkal, adatok védelmével és a kommunikáció titkosságával kapcsolatos törvényeknek.</span><span class="sxs-lookup"><span data-stu-id="31231-109">You are responsible for ensuring that your use of Dynamics 365 Customer Insights, including predictions, complies with all applicable laws and regulations, including laws related to privacy, personal data, biometric data, data protection, and confidentiality of communications.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="31231-110">Előfeltételek</span><span class="sxs-lookup"><span data-stu-id="31231-110">Prerequisites</span></span>

<span data-ttu-id="31231-111">Ahhoz, hogy a szervezet használni tudja az Előrejelzések funkciót, gondoskodjon arról, hogy a következő előfeltételek teljesüljenek:</span><span class="sxs-lookup"><span data-stu-id="31231-111">Before your organization can use the predictions feature, the following prerequisites must be met:</span></span>

1. <span data-ttu-id="31231-112">A szervezetnél egy példányt [be kell állítani a Common Data Service-ben](https://docs.microsoft.com/ai-builder/build-model#prerequisites), és ugyanabban a szervezetben, mint a Customer Insights.</span><span class="sxs-lookup"><span data-stu-id="31231-112">Your organization has an instance [set up in the Common Data Service](https://docs.microsoft.com/ai-builder/build-model#prerequisites) and it's in the same organization as Customer Insights.</span></span>

2. <span data-ttu-id="31231-113">A környezet a Common Data Service példányához van csatolva.</span><span class="sxs-lookup"><span data-stu-id="31231-113">Your environment is attached to your Common Data Service instance.</span></span>

<span data-ttu-id="31231-114">Ha [új környezetet hoz létre](manage-environments.md), konfigurálja a **Környezet létrehozása** párbeszédablakban, és válassza a **Speciális** elemet.</span><span class="sxs-lookup"><span data-stu-id="31231-114">If you're [creating a new environment](manage-environments.md), configure it in the **Create an environment** dialog and select **Advanced**.</span></span> <span data-ttu-id="31231-115">Ha már létrehozott egy környezetet, nyissa meg a beállításait, és válassza a **Speciális** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="31231-115">If you've already created an environment, go to its settings and select **Advanced**.</span></span> <span data-ttu-id="31231-116">Akárhogy is, az **Előrejelzések használata** részben adja meg a Common Data Service-példány URL-címét, amelyre a környezetet csatolni szeretné.</span><span class="sxs-lookup"><span data-stu-id="31231-116">Either way, in the **Use predictions** section, enter the Common Data Service instance URL to which you want to attach your environment.</span></span>

## <a name="create-a-prediction-in-the-customer-entity"></a><span data-ttu-id="31231-117">Előrejelzés létrehozása az ügyfél entitásban</span><span class="sxs-lookup"><span data-stu-id="31231-117">Create a prediction in the Customer entity</span></span>

1. <span data-ttu-id="31231-118">A célközönség információin belül nyissa meg a következőt: **Adatok** > **Entitások**.</span><span class="sxs-lookup"><span data-stu-id="31231-118">In audience insights, go to **Data** > **Entities**.</span></span>

2. <span data-ttu-id="31231-119">Válassza az **Ügyfél** entitást.</span><span class="sxs-lookup"><span data-stu-id="31231-119">Select the **Customer** entity.</span></span>

3. <span data-ttu-id="31231-120">Az **Ügyfél: CustomerInsights** entitásban válassza a **Mezők** lapot.</span><span class="sxs-lookup"><span data-stu-id="31231-120">In the **Customer:CustomerInsights** entity, select on the **Fields** tab.</span></span>

4. <span data-ttu-id="31231-121">Keresse meg azt az attribútumot, amelyhez előre szeretné jelezni az értékeket, és válassza az **Áttekintés** ikont az **Összesítés** oszlopban.</span><span class="sxs-lookup"><span data-stu-id="31231-121">Find the attribute name you wish to predict values for, then select the **Overview** icon in the **Summary** column.</span></span>
   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="31231-122">![Áttekintés ikon](media/intelligence-overviewicon.png "Áttekintés ikon")</span><span class="sxs-lookup"><span data-stu-id="31231-122">![Overview icon](media/intelligence-overviewicon.png "Overview icon")</span></span>

5. <span data-ttu-id="31231-123">Ha az attribútumhoz nagy a hiányzó értékek aránya, akkor az előrejelzés folytatásához válassza a **Hiányzó értékek előrejelzése** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="31231-123">If there's a high rate of missing values for your attribute, select **Predict missing values** to continue with your prediction.</span></span>
   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="31231-124">![Áttekintési állapot, ahol a hiányzó értékek előrejelzése gomb látható](media/intelligence-overviewpredictmissingvalues.png "Áttekintési állapot, ahol a hiányzó értékek előrejelzése gomb látható")</span><span class="sxs-lookup"><span data-stu-id="31231-124">![Overview status with predict missing values button shown](media/intelligence-overviewpredictmissingvalues.png "Overview status with predict missing values button shown")</span></span>

6. <span data-ttu-id="31231-125">Adja meg a **Megjelenítendő név** és a **Kimeneti entitás neve** értékét az előrejelzés eredményéhez.</span><span class="sxs-lookup"><span data-stu-id="31231-125">Provide a **Display name** and an **Output entity name** for the results of the prediction.</span></span>

7. <span data-ttu-id="31231-126">Megjelenik a lehetőségek előre kitöltött listája, ahol az értékeket egy előre jelzett kategóriához rendelheti.</span><span class="sxs-lookup"><span data-stu-id="31231-126">A pre-populated list of options will show where you can map the values to a predicted category.</span></span> <span data-ttu-id="31231-127">Ebben az esetben az egyetlen kategórialehetőségek a 0 vagy az 1, mivel az előrejelzés igaz/hamis vagy bináris jellegével lesznek megfeleltetve.</span><span class="sxs-lookup"><span data-stu-id="31231-127">In this case, your only category options will be 0 or 1, as they map to the true/false or binary nature of the prediction.</span></span> <span data-ttu-id="31231-128">A Kategória oszlopban azokat a mezőértékeket, amelyeket a végső előrejelzésben „0” értékkel szeretne besorolni, feleltesse meg a „0” értékkel, a végső előrejelzésben „1” értékkel besorolandó elemeket pedig az „1” értékkel.</span><span class="sxs-lookup"><span data-stu-id="31231-128">In the Category column, map the field values you'd like to be classified as "0" in the final prediction to "0", and the items you'd like to be classified as "1" in the final prediction to "1".</span></span>
   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="31231-129">![Példa, amelyen kategóriákkal megfeleltetett mezőértékek láthatók](media/intelligence-categorymapping.png "Példa, amelyen kategóriákkal megfeleltetett mezőértékek láthatók")</span><span class="sxs-lookup"><span data-stu-id="31231-129">![Example showing mapped field values to categories](media/intelligence-categorymapping.png "Example showing mapped field values to categories")</span></span>

8. <span data-ttu-id="31231-130">Válassza a **Kész** lehetőséget, és a rendszer feldolgozza az előrejelzést.</span><span class="sxs-lookup"><span data-stu-id="31231-130">Select **Done** and the prediction will be processed.</span></span> <span data-ttu-id="31231-131">A feldolgozás egy kis időt vesz igénbe, az adatok méretétől és összetettségétől függően.</span><span class="sxs-lookup"><span data-stu-id="31231-131">The processing will take some time, depending on the size and complexity of data.</span></span> <span data-ttu-id="31231-132">Az eredmények egy új entitásban lesznek elérhetők a létrehozott előrejelzés **Kimeneti entitásának neve** alapján.</span><span class="sxs-lookup"><span data-stu-id="31231-132">Results will be available in a new entity based on the **Output entity name** of the prediction you created.</span></span>

## <a name="create-a-prediction-while-creating-a-segment"></a><span data-ttu-id="31231-133">Előrejelzés létrehozása a szegmens létrehozásakor</span><span class="sxs-lookup"><span data-stu-id="31231-133">Create a prediction while creating a segment</span></span>

<span data-ttu-id="31231-134">A kiválasztott attribútumok hiányzó értékeinek előrejelzése a szegmens létrehozásakor is lehetséges.</span><span class="sxs-lookup"><span data-stu-id="31231-134">Predicting missing values for a specific attribute of choice is also possible when creating a segment.</span></span> <span data-ttu-id="31231-135">Különösen, amikor gyorsan létrehoz egy szegmenst az egyesített Ügyfél entitás vagy a Customer_Measure entitás alapján.</span><span class="sxs-lookup"><span data-stu-id="31231-135">Specifically, when you quickly create a segment based on either your unified Customer entity or Customer_Measure entity.</span></span>

<span data-ttu-id="31231-136">Az adott folyamat részeként kiválaszthat egy specifikus attribútumot, amin alapulhat a szegmens, például Ügyfél-elégedettség, Vásárlás összege.</span><span class="sxs-lookup"><span data-stu-id="31231-136">As part of this flow, you'll choose a specific attribute to base your segment on, such as Customer Satisfaction or Purchase Amount.</span></span> <span data-ttu-id="31231-137">A szegmens létrehozásakor a rendszer javaslatot tesz az attribútum hiányzó értékeinek előrejelzésére.</span><span class="sxs-lookup"><span data-stu-id="31231-137">Upon segment creation, the system will suggest a method for predicting any missing values for this attribute.</span></span>

1. <span data-ttu-id="31231-138">A célközönség-információkban nyissa meg a **Szegmensek** oldalt, és válassza a **Profilok** csempét.</span><span class="sxs-lookup"><span data-stu-id="31231-138">In audience insights, go to **Segments** and select the **Profiles** tile.</span></span>

2. <span data-ttu-id="31231-139">A **Mező** pont kiválasztásával hozzon létre egy szegmenst, és válassza ki az **Operátor** elemet, majd a **Felülvizsgálat** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="31231-139">Choose a **Field** to create a segment on and select an **Operator**, then select **Review**.</span></span>

3. <span data-ttu-id="31231-140">Adja meg a **Név** és a **Megjelenítendő név** értékét a szegmenshez.</span><span class="sxs-lookup"><span data-stu-id="31231-140">Provide a **Name** and a **Display name** for the segment.</span></span>

4. <span data-ttu-id="31231-141">Válassza a **Mentés** parancsot.</span><span class="sxs-lookup"><span data-stu-id="31231-141">Select **Save**.</span></span>

5. <span data-ttu-id="31231-142">Ha a létrehozott szegmensben hiányos adatok szerepelnek a Forrás mezőben, dönthet úgy, hogy előre jelzi a hiányzó értékeket.</span><span class="sxs-lookup"><span data-stu-id="31231-142">If the segment you created has incomplete data in the source field, you can choose to predict the missing values.</span></span>
   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="31231-143">![Előrejelzés gomb](media/segments-predictoption.png "Előrejelzés gomb")</span><span class="sxs-lookup"><span data-stu-id="31231-143">![Prediction button](media/segments-predictoption.png "Prediction button")</span></span>

6. <span data-ttu-id="31231-144">Adja meg a **Megjelenítendő név** és a **Kimeneti entitás neve** értékét az előrejelzés eredményéhez.</span><span class="sxs-lookup"><span data-stu-id="31231-144">Provide a **Display name** and an **Output entity name** for the results of the prediction.</span></span>

7. <span data-ttu-id="31231-145">Válassza a **Kész** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="31231-145">Select **Done**.</span></span> <span data-ttu-id="31231-146">Az előrejelzés hamarosan létrejön egy új entitásban, amelynek neve a **Kimeneti entitás neve** mezőben megadott név.</span><span class="sxs-lookup"><span data-stu-id="31231-146">Your prediction will be generated shortly in a new entity with the name you provided for the **Output entity name**.</span></span>

## <a name="view-a-prediction"></a><span data-ttu-id="31231-147">Előrejelzés megtekintése</span><span class="sxs-lookup"><span data-stu-id="31231-147">View a prediction</span></span>

1. <span data-ttu-id="31231-148">A célközönség információin belül nyissa meg a következőt: **Információk** > **Előrejelzések** > **Saját előrejelzések**.</span><span class="sxs-lookup"><span data-stu-id="31231-148">In audience insights, go to **Intelligence** > **Predictions** > **My predictions**.</span></span>

2. <span data-ttu-id="31231-149">Jelölje ki az áttekinteni kívánt előrejelzést.</span><span class="sxs-lookup"><span data-stu-id="31231-149">Select the prediction you want to review.</span></span>

3. <span data-ttu-id="31231-150">Válassza a három pontot a **Műveletek** oszlopban, majd a **Megtekintés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="31231-150">Select the ellipsis in the **Actions** column and choose **View**.</span></span>

4. <span data-ttu-id="31231-151">Az előrejelzés nézetében számos adatpont jelenik meg.</span><span class="sxs-lookup"><span data-stu-id="31231-151">You'll see a number of data points in the view of your prediction.</span></span>
   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="31231-152">![Előrejelzések oldala](media/intelligence-predictionsviewpage.png "Előrejelzések oldala")</span><span class="sxs-lookup"><span data-stu-id="31231-152">![Predictions page](media/intelligence-predictionsviewpage.png "Predictions page")</span></span>

   - <span data-ttu-id="31231-153">**Előre jelzett értékek** bemutatja a Mező értékének a Kategóriával való megfeleltetési fázis során létrehozott megfeleltetését.</span><span class="sxs-lookup"><span data-stu-id="31231-153">**Predicted values** shows the mapping you created during the Field value to Category mapping phase.</span></span> <span data-ttu-id="31231-154">Ezek az adathalmaz azon értékeit, amelyek egy adott kategóriára vannak leképezve.</span><span class="sxs-lookup"><span data-stu-id="31231-154">These are the values in your dataset that have been mapped to a specific category.</span></span>
   <span data-ttu-id="31231-155">-**Legfontosabb befolyásolók** az adathalmaz olyan tényezői, amelyek nagy valószínűséggel befolyásolják a Mező értékének egy adott kategóriára való leképezésére vonatkozó előrejelzés konfidenciáját.</span><span class="sxs-lookup"><span data-stu-id="31231-155">-**Top influencers** are the factors within your dataset that were most likely to influence the prediction's confidence of your Field value being mapped to a specific category.</span></span>
   - <span data-ttu-id="31231-156">A **teljesítmény** jelzi az előrejelzések előrehaladását.</span><span class="sxs-lookup"><span data-stu-id="31231-156">**Performance** indicates how the predictions are doing.</span></span> <span data-ttu-id="31231-157">További tudnivalókért válassza a hivatkozást.</span><span class="sxs-lookup"><span data-stu-id="31231-157">Select the link to learn more.</span></span>
   - <span data-ttu-id="31231-158">Az **előnézet** mintákat mutat be az előrejelzés kimeneti adathalmazából, valamint az előre jelzett érték valószínűségét, azaz konfidenciáját, ahol 0 a bizonytalan és az 1 a biztos érték.</span><span class="sxs-lookup"><span data-stu-id="31231-158">**Preview** shows samples of the output dataset from your prediction and the likelihood, or our confidence, of the predicted value where 0 is uncertain, and 1 is certain.</span></span>

## <a name="update-a-prediction"></a><span data-ttu-id="31231-159">Előrejelzés frissítése</span><span class="sxs-lookup"><span data-stu-id="31231-159">Update a prediction</span></span>

1. <span data-ttu-id="31231-160">A célközönség információin belül nyissa meg a következőt: **Információk** > **Előrejelzések** > **Saját előrejelzések**.</span><span class="sxs-lookup"><span data-stu-id="31231-160">In audience insights, go to **Intelligence** > **Predictions** > **My predictions**.</span></span>

2. <span data-ttu-id="31231-161">Válassza ki a frissíteni kívánt előrejelzést, és válassza a **Frissítés** ikont.</span><span class="sxs-lookup"><span data-stu-id="31231-161">Select the prediction you want to update and select the **Update** icon.</span></span>

3. <span data-ttu-id="31231-162">A rendszer feldolgozásra ütemezi a előrejelzést.</span><span class="sxs-lookup"><span data-stu-id="31231-162">The prediction will be scheduled for processing.</span></span> <span data-ttu-id="31231-163">Megtekintheti az utolsó frissítés időpontját a **Frissítve** oszlopban, az **Előrejelzések** oldalon.</span><span class="sxs-lookup"><span data-stu-id="31231-163">You can see the time it was last updated in the **Updated** column of the **Predictions** page.</span></span>

## <a name="edit-a-prediction"></a><span data-ttu-id="31231-164">Előrejelzés szerkesztése</span><span class="sxs-lookup"><span data-stu-id="31231-164">Edit a prediction</span></span>

<span data-ttu-id="31231-165">Előrejelzés létrehozása után testreszabhatja az AI Builder modelljét, amellyel növelheti a modell hatékonyságát.</span><span class="sxs-lookup"><span data-stu-id="31231-165">After you've created a prediction, you can customize the model in the AI Builder to increase the effectiveness of your model.</span></span>  

1. <span data-ttu-id="31231-166">A célközönség információin belül nyissa meg a következőt: **Információk** > **Előrejelzések** > **Saját előrejelzések**.</span><span class="sxs-lookup"><span data-stu-id="31231-166">In audience insights, go to **Intelligence** > **Predictions** > **My predictions**.</span></span>

2. <span data-ttu-id="31231-167">Válassza ki a szerkeszteni kívánt előrejelzést.</span><span class="sxs-lookup"><span data-stu-id="31231-167">Select the prediction you want to edit.</span></span>

3. <span data-ttu-id="31231-168">Válassza a három pontot a **Műveletek** oszlopban, majd a **Megtekintés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="31231-168">Select the ellipsis in the **Actions** column and choose **View**.</span></span>

4. <span data-ttu-id="31231-169">Válassza a **Testreszabás az AI Builder segítségével** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="31231-169">Select **Customize in AI Builder**.</span></span>

5. <span data-ttu-id="31231-170">Frissítse a modellt az AI Builder alkalmazásban.</span><span class="sxs-lookup"><span data-stu-id="31231-170">Update your model in the AI Builder.</span></span> <span data-ttu-id="31231-171">[További információ az AI Builderben található modellek kezeléséről](https://docs.microsoft.com/ai-builder/manage-model#retrain-and-republish-existing-models).</span><span class="sxs-lookup"><span data-stu-id="31231-171">[Learn more about managing models in the AI builder](https://docs.microsoft.com/ai-builder/manage-model#retrain-and-republish-existing-models).</span></span>

<span data-ttu-id="31231-172">Az előrejelzés következő futtatása a létrehozott frissített modellt fogja használni.</span><span class="sxs-lookup"><span data-stu-id="31231-172">The next run of your prediction will use the updated model you've created.</span></span>

> [!NOTE]
> <span data-ttu-id="31231-173">Az AI Builder rendszerben létrehozott új modellek nem jelennek meg célközönség-információkban, kivéve ha a modell a fentiekben felsorolt tapasztalatokból jött létre.</span><span class="sxs-lookup"><span data-stu-id="31231-173">New models created in AI Builder will not be displayed in audience insights unless the model was created from the experiences listed above.</span></span>

## <a name="remove-a-prediction"></a><span data-ttu-id="31231-174">Előrejelzés eltávolítása</span><span class="sxs-lookup"><span data-stu-id="31231-174">Remove a prediction</span></span>

1. <span data-ttu-id="31231-175">A célközönség információin belül nyissa meg a következőt: **Információk** > **Előrejelzések** > **Saját előrejelzések**.</span><span class="sxs-lookup"><span data-stu-id="31231-175">In audience insights, go to **Intelligence** > **Predictions** > **My predictions**.</span></span>

2. <span data-ttu-id="31231-176">Jelölje ki a törlendő előrejelzést.</span><span class="sxs-lookup"><span data-stu-id="31231-176">Select the prediction you want to delete.</span></span>

3. <span data-ttu-id="31231-177">Válassza a három pontot a **Műveletek** oszlopban, majd a **Törlés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="31231-177">Select the ellipsis in the **Actions** column and choose **Delete**.</span></span>

4. <span data-ttu-id="31231-178">Törlés jóváhagyása.</span><span class="sxs-lookup"><span data-stu-id="31231-178">Confirm the deletion.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="31231-179">Hibaelhárítás</span><span class="sxs-lookup"><span data-stu-id="31231-179">Troubleshooting</span></span>

<span data-ttu-id="31231-180">Ha hiba miatt nem tudja elvégezni a csatolási Common Data Service folyamatot, megpróbálhatja manuálisan végrehajtani.</span><span class="sxs-lookup"><span data-stu-id="31231-180">If you can't complete the attach Common Data Service process due to an error, you can try to complete the process manually.</span></span> <span data-ttu-id="31231-181">A csatolási folyamat során két ismert probléma is előfordulhat:</span><span class="sxs-lookup"><span data-stu-id="31231-181">There are two known issues that can occur in the attach process:</span></span>

- <span data-ttu-id="31231-182">Nincs telepítve az Ügyfélkártya bővítmény megoldás.</span><span class="sxs-lookup"><span data-stu-id="31231-182">The Customer Card Add-in solution is not installed.</span></span>
    1. <span data-ttu-id="31231-183">Hajtsa végre a [megoldás telepítésére és konfigurálására vonatkozó](customer-card-add-in.md) utasításokat.</span><span class="sxs-lookup"><span data-stu-id="31231-183">Complete the instructions to [install and configure the solution](customer-card-add-in.md).</span></span>

- <span data-ttu-id="31231-184">Az alkalmazásengedélyek nincsenek megadva.</span><span class="sxs-lookup"><span data-stu-id="31231-184">App permissions aren't granted.</span></span>
    1. <span data-ttu-id="31231-185">Menjen a [https://admin.powerplatform.microsoft.com](https://admin.powerplatform.microsoft.com) felületre.</span><span class="sxs-lookup"><span data-stu-id="31231-185">Go to [https://admin.powerplatform.microsoft.com](https://admin.powerplatform.microsoft.com).</span></span>
    1. <span data-ttu-id="31231-186">**Környezetek** kiválasztása.</span><span class="sxs-lookup"><span data-stu-id="31231-186">Select **Environments**.</span></span>
    1. <span data-ttu-id="31231-187">Válassza azon környezet mellett látható három pontot, amelyhez engedélyt szeretne hozzáadni, majd válassza a **Beállítások** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="31231-187">Select the ellipsis next to the environment you want to add the permission to and select **Settings**.</span></span>
    1. <span data-ttu-id="31231-188">Bontsa ki a **Felhasználók + engedélyek** elemet, és válassza a **Felhasználók** elemet.</span><span class="sxs-lookup"><span data-stu-id="31231-188">Expand **Users + permissions** and select **Users**.</span></span>
    1. <span data-ttu-id="31231-189">Válassza az **+ Új** lehetőséget , és válassza a **Felhasználó** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="31231-189">Select **+ New** and select **User**.</span></span>
    1. <span data-ttu-id="31231-190">Válassza az **Alkalmazásfelhasználó** elemt, ha még nincs kijelölve, és adja meg a következő adatokat:</span><span class="sxs-lookup"><span data-stu-id="31231-190">Select **Application User** if it's not already selected and enter the following information:</span></span>
        - <span data-ttu-id="31231-191">**Felhasználónév:** cihelp@microsoft.com</span><span class="sxs-lookup"><span data-stu-id="31231-191">**User Name:** cihelp@microsoft.com</span></span>
        - <span data-ttu-id="31231-192">**Alkalmazás azonosítója:** 38c77d00-5fcb-4cce-9d93-af4738258e3c</span><span class="sxs-lookup"><span data-stu-id="31231-192">**Application ID:** 38c77d00-5fcb-4cce-9d93-af4738258e3c</span></span>
        - <span data-ttu-id="31231-193">**Utónév:** Customer</span><span class="sxs-lookup"><span data-stu-id="31231-193">**First Name:** Customer</span></span>
        - <span data-ttu-id="31231-194">**Vezetéknév:** Insights</span><span class="sxs-lookup"><span data-stu-id="31231-194">**Last Name:** Insights</span></span>
        - <span data-ttu-id="31231-195">**Elsődleges e-mail cím:** cihelp@microsoft.com</span><span class="sxs-lookup"><span data-stu-id="31231-195">**Primary Email:** cihelp@microsoft.com</span></span>
    1. <span data-ttu-id="31231-196">Válassza a **Mentés és bezárás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="31231-196">Select **Save & Close**.</span></span>
    1. <span data-ttu-id="31231-197">Jelölje ki a létrehozott felhasználókat.</span><span class="sxs-lookup"><span data-stu-id="31231-197">Select the user you just created.</span></span>
    1. <span data-ttu-id="31231-198">Válassza a **Szerepkörök kezelése** lehetőséget a felső menüsávon.</span><span class="sxs-lookup"><span data-stu-id="31231-198">Select **Manage Roles** in the top menu bar.</span></span>
    1. <span data-ttu-id="31231-199">Válassza a **Rendszergazda** lehetőséget, majd kattintson az **OK** gombra.</span><span class="sxs-lookup"><span data-stu-id="31231-199">Select **System Administrator**, then select **OK**.</span></span>
