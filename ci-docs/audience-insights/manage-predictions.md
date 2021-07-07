---
title: Megosztott feladatok előrejelzés forgatókönyvekhez
description: Ismerje meg az előrejelzések kezelését, hibaelhárítását és finomítását.
ms.date: 05/17/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: how-to
author: diegogranados117
ms.author: digranad
manager: shellyha
ms.openlocfilehash: dccb8dcca8f65f64973e46fed9d83034d58282e2
ms.sourcegitcommit: bcc47d15d4f0eacf008e4dbc09baac7f062b3ca8
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 06/29/2021
ms.locfileid: "6315881"
---
# <a name="manage-predictions"></a><span data-ttu-id="622c6-103">Előrejelzések kezelése</span><span class="sxs-lookup"><span data-stu-id="622c6-103">Manage predictions</span></span>

<span data-ttu-id="622c6-104">Ez a cikk néhány olyan feladatot tárgyal, amelyeken a legtöbb előrejelzési forgatókönyv osztozik.</span><span class="sxs-lookup"><span data-stu-id="622c6-104">This article discusses some tasks that most prediction scenarios share.</span></span>

## <a name="troubleshoot-a-failed-prediction"></a><span data-ttu-id="622c6-105">A sikertelen előrejelzés hibáinak elhárítása.</span><span class="sxs-lookup"><span data-stu-id="622c6-105">Troubleshoot a failed prediction</span></span>

1. <span data-ttu-id="622c6-106">Nyissa meg az **Intelligencia** > **Előrejelzések** menüt, és válassza ki a **Saját előrejelzések** lapot.</span><span class="sxs-lookup"><span data-stu-id="622c6-106">Go to **Intelligence** > **Predictions** and select the **My predictions** tab.</span></span>

1. <span data-ttu-id="622c6-107">Válassza ki a függőleges ellipsziseket amellett az előrejelzés mellet, melynek hibanaplóját meg szeretné tekinteni.</span><span class="sxs-lookup"><span data-stu-id="622c6-107">Select the vertical ellipses next to the prediction you want to view error logs for.</span></span>

1. <span data-ttu-id="622c6-108">Válassza ki a **Naplók** menüpontot.</span><span class="sxs-lookup"><span data-stu-id="622c6-108">Select **Logs**.</span></span>

1. <span data-ttu-id="622c6-109">Tekintse át a hibákat.</span><span class="sxs-lookup"><span data-stu-id="622c6-109">Review all the errors.</span></span> <span data-ttu-id="622c6-110">Többféle típusú hiba fordulhat elő; a leírásból kiderül, milyen feltétel okozta a hibát.</span><span class="sxs-lookup"><span data-stu-id="622c6-110">There are several types of errors that can occur, and they describe what condition caused the error.</span></span> <span data-ttu-id="622c6-111">Ha például az a hiba, hogy nincs elég adat a pontos előrejelzéshez, akkor ez általában megoldható további adatok Customer Insightsba történő betöltésével.</span><span class="sxs-lookup"><span data-stu-id="622c6-111">For example, an error that there's not enough data to accurately predict is typically resolved by loading additional data into Customer Insights.</span></span>

## <a name="input-data-usability-report"></a><span data-ttu-id="622c6-112">Bemeneti adatok használhatósági jelentése</span><span class="sxs-lookup"><span data-stu-id="622c6-112">Input data usability report</span></span>

<span data-ttu-id="622c6-113">A bemeneti adatok használhatósági jelentése egységes képet ad azokról a hibákról és figyelmeztetésekről, amelyeket a gyári előrejelzések generálhatnak.</span><span class="sxs-lookup"><span data-stu-id="622c6-113">The input data usability report provides a consolidated view of the errors and warnings that your out-of-box predictions may be generating.</span></span> <span data-ttu-id="622c6-114">Ajánlásokat is ad a modell teljesítményének javítására.</span><span class="sxs-lookup"><span data-stu-id="622c6-114">It also gives recommendations how to improve the model performance.</span></span>

<span data-ttu-id="622c6-115">A jelentés a modell betanítási folyamatának befejezése után érhető el.</span><span class="sxs-lookup"><span data-stu-id="622c6-115">The report is available after a model has completed its training process.</span></span> <span data-ttu-id="622c6-116">Minden modellhez külön-külön van létrehozva, függetlenül attól, hogy sikeresen befejeződött-e vagy sem.</span><span class="sxs-lookup"><span data-stu-id="622c6-116">It's created for each model separately, regardless if it completed successfully or not.</span></span>

### <a name="view-the-input-data-usability-report"></a><span data-ttu-id="622c6-117">Bemeneti adatok használhatósági jelentésének megtekintése</span><span class="sxs-lookup"><span data-stu-id="622c6-117">View the input data usability report</span></span>

<span data-ttu-id="622c6-118">Miután egy beépített modell befejezte a betanítási lépést, tekintse meg a jelentést:</span><span class="sxs-lookup"><span data-stu-id="622c6-118">After an out-of-box model has completed its training step, view the report:</span></span>
- <span data-ttu-id="622c6-119">Jelölje ki a modell neve melletti három pontot, és válassza a **Bemeneti adatok használhatósági jelentése** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="622c6-119">Select the ellipses next to the model name and choose **Input data usability report**.</span></span>
- <span data-ttu-id="622c6-120">Válassza ki a modell állapotát, válassza a **Bemeneti adatok használhatósági jelentése** elemet az oldalsó ablaktáblában.</span><span class="sxs-lookup"><span data-stu-id="622c6-120">Select the status of a model select **See Input data usability report** in the side pane.</span></span>
- <span data-ttu-id="622c6-121">Válasszon ki egyet a lista egyik modellje közül, és válassza a **Bemeneti adatok használhatósági jelentését** a parancssoron.</span><span class="sxs-lookup"><span data-stu-id="622c6-121">Selecting one of the models in the list and select **Input data usability report** in the command bar.</span></span>
- <span data-ttu-id="622c6-122">Nyissa meg a modelleredmények oldalt, és válassza a **Bemeneti adatok használhatósági jelentését** a parancssoron.</span><span class="sxs-lookup"><span data-stu-id="622c6-122">Open the model results page and select **Input data usability report** in the command bar.</span></span>

### <a name="information-in-the-input-data-usability-report"></a><span data-ttu-id="622c6-123">Információk a bemeneti adatok használhatósági jelentésében</span><span class="sxs-lookup"><span data-stu-id="622c6-123">Information in the input data usability report</span></span>

<span data-ttu-id="622c6-124">A jelentés következő oszlopai hasznos információkat tartalmaznak a modell adatainak javításához.</span><span class="sxs-lookup"><span data-stu-id="622c6-124">The following columns in the report contain helpful information to improve the data for the model.</span></span>

:::image type="content" source="media/input-data-usability-report.png" alt-text="Példa egy bemeneti adatok használhatósági jelentésére, amely egy hibákat, figyelmeztetéseket és ajánlásokat megjelenítő táblázatot mutat be.":::

- <span data-ttu-id="622c6-126">Név: A hiba, figyelmeztetés vagy ajánlás leíró neve.</span><span class="sxs-lookup"><span data-stu-id="622c6-126">Name: Descriptive name of the error, warning, or recommendation.</span></span>
- <span data-ttu-id="622c6-127">Lépés: Modellfázis, tanítás vagy pontszám, amelyre az információ hivatkozik.</span><span class="sxs-lookup"><span data-stu-id="622c6-127">Step: Model phase, train or score, the information refers to.</span></span>
- <span data-ttu-id="622c6-128">Állapot: Az információ súlyossága (hiba, figyelmeztetés, ajánlás).</span><span class="sxs-lookup"><span data-stu-id="622c6-128">State: Severity of the information (error, warning, recommendation).</span></span>
- <span data-ttu-id="622c6-129">Oszlopnév: Oszlop egy entitásban, amelyet módosítani kell a modell teljesítményének javítása érdekében.</span><span class="sxs-lookup"><span data-stu-id="622c6-129">Column name: Column in an entity that needs to be modified to improve the model performance.</span></span>
- <span data-ttu-id="622c6-130">Entitásnév: Az entitás neve, amelyet módosítani kell a modell teljesítményének javítása érdekében.</span><span class="sxs-lookup"><span data-stu-id="622c6-130">Entity name: Name of the entity that needs to be modified to improve the model performance.</span></span>
- <span data-ttu-id="622c6-131">Részletek: Részletek a hibáról, figyelmeztetésről vagy ajánlásról.</span><span class="sxs-lookup"><span data-stu-id="622c6-131">Details: Details about the error, warning, or recommendation.</span></span>

## <a name="refresh-a-prediction"></a><span data-ttu-id="622c6-132">Előrejelzés frissítése</span><span class="sxs-lookup"><span data-stu-id="622c6-132">Refresh a prediction</span></span>

<span data-ttu-id="622c6-133">Az előrejelzések automatikusan frissülnek az [adatok beállítások között megadott frissítési ütemezése](system.md#schedule-tab) szerint.</span><span class="sxs-lookup"><span data-stu-id="622c6-133">Predictions will automatically refresh on the same [schedule your data refreshes](system.md#schedule-tab) as configured in settings.</span></span> <span data-ttu-id="622c6-134">Ezeket Ön manuálisan is frissíteni tudja.</span><span class="sxs-lookup"><span data-stu-id="622c6-134">You can refresh them manually too.</span></span>

1. <span data-ttu-id="622c6-135">Nyissa meg az **Intelligencia** > **Előrejelzések** menüt, és válassza ki a **Saját előrejelzések** lapot.</span><span class="sxs-lookup"><span data-stu-id="622c6-135">Go to **Intelligence** > **Predictions** and select the **My predictions** tab.</span></span>

1. <span data-ttu-id="622c6-136">Kattintson a frissíteni kívánt előrejelzés mellett lévő pontokra.</span><span class="sxs-lookup"><span data-stu-id="622c6-136">Select the vertical ellipses next to the prediction you want to refresh.</span></span>

1. <span data-ttu-id="622c6-137">Válassza a **Frissítés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="622c6-137">Select **Refresh**.</span></span>

## <a name="delete-a-prediction"></a><span data-ttu-id="622c6-138">Előrejelzés törlése</span><span class="sxs-lookup"><span data-stu-id="622c6-138">Delete a prediction</span></span>

<span data-ttu-id="622c6-139">Az előrejelzés törlésével annak kimeneti entitása is törlésre kerül.</span><span class="sxs-lookup"><span data-stu-id="622c6-139">Deleting a prediction also removes its output entity.</span></span>

1. <span data-ttu-id="622c6-140">Nyissa meg az **Intelligencia** > **Előrejelzések** menüt, és válassza ki a **Saját előrejelzések** lapot.</span><span class="sxs-lookup"><span data-stu-id="622c6-140">Go to **Intelligence** > **Predictions** and select the **My predictions** tab.</span></span>

1. <span data-ttu-id="622c6-141">Kattintson a törölni kívánt előrejelzés mellett lévő pontokra.</span><span class="sxs-lookup"><span data-stu-id="622c6-141">Select the vertical ellipses next to the prediction you want to delete.</span></span>

1. <span data-ttu-id="622c6-142">Válassza a **Törlés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="622c6-142">Select **Delete**.</span></span>
