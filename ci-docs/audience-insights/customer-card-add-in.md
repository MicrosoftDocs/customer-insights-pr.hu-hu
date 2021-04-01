---
title: Telepítheti és használhatja az Ügyfélkártya bővítményt
description: Az Ügyfélkártya bővítmény telepítése és konfigurálása a Dynamics 365 Customer Insights megoldásban.
ms.date: 01/20/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: f3c4a01f9ce7749eeee72f7901620dae7cb9b8d3
ms.sourcegitcommit: bae40184312ab27b95c140a044875c2daea37951
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 03/15/2021
ms.locfileid: "5597330"
---
# <a name="customer-card-add-in-preview"></a><span data-ttu-id="a5448-103">Ügyfélkártya bővítmény (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="a5448-103">Customer Card Add-in (preview)</span></span>

[!INCLUDE [cc-data-platform-banner](../includes/cc-data-platform-banner.md)]

<span data-ttu-id="a5448-104">360 fokos képet kaphat az ügyfeleiről közvetlenül a Dynamics 365 alkalmazásokban.</span><span class="sxs-lookup"><span data-stu-id="a5448-104">Get a 360-degree view of your customers directly in Dynamics 365 apps.</span></span> <span data-ttu-id="a5448-105">A demográfiai adatok, a betekintések és a tevékenységek ütemezése az ügyfélkarton bővítménnyel tekinthető meg.</span><span class="sxs-lookup"><span data-stu-id="a5448-105">View demographics, insights, and activity timelines with the Customer Card Add-in.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a5448-106">Előfeltételek</span><span class="sxs-lookup"><span data-stu-id="a5448-106">Prerequisites</span></span>

- <span data-ttu-id="a5448-107">Dynamics 365 alkalmazás (például Értékesítési központ vagy Ügyfélszolgálati központ), 9.0 vagy újabb verziója, és az egyesített felület engedélyezve.</span><span class="sxs-lookup"><span data-stu-id="a5448-107">Dynamics 365 app (such as Sales Hub or Customer Service Hub), version 9.0 and later with Unified Interface enabled.</span></span>
- <span data-ttu-id="a5448-108">Ügyfélprofilok [a Dynamics 365 alkalmazásból betöltve a Common Data Service szolgáltatással](connect-power-query.md).</span><span class="sxs-lookup"><span data-stu-id="a5448-108">Customer profiles [ingested from the Dynamics 365 app using Common Data Service](connect-power-query.md).</span></span>
- <span data-ttu-id="a5448-109">Az Ügyfélkártya bővítmény felhasználóit a célközönség-információkban [felhasználóként kell felvenni](permissions.md).</span><span class="sxs-lookup"><span data-stu-id="a5448-109">Users of the Customer Card Add-in need to be [added as users](permissions.md) in audience insights.</span></span>
- <span data-ttu-id="a5448-110">[Konfigurált keresési és szűrési lehetőségek](search-filter-index.md).</span><span class="sxs-lookup"><span data-stu-id="a5448-110">[Configured search and filter capabilities](search-filter-index.md).</span></span>
- <span data-ttu-id="a5448-111">Demográfiai ellenőrzés: Demográfiai mezők (például az életkor vagy a nemek) az egyesített ügyfélprofilban érhetők el.</span><span class="sxs-lookup"><span data-stu-id="a5448-111">Demographic control: Demographic fields(such as age or gender) are available in the unified customer profile.</span></span>
- <span data-ttu-id="a5448-112">A dúsítási vezérlő: az ügyfelek profiljaira alkalmazott aktív [dúsítást](enrichment-hub.md) igényel.</span><span class="sxs-lookup"><span data-stu-id="a5448-112">Enrichment control: Requires active [enrichments](enrichment-hub.md) applied to customer profiles.</span></span>
- <span data-ttu-id="a5448-113">Intelligenciai ellenőrzés: Az Azure Machine Learning ([Előrejelzések](predictions.md) vagy [Egyéni modellek](custom-models.md)) használatával létrehozott adatok szükségesek</span><span class="sxs-lookup"><span data-stu-id="a5448-113">Intelligence control: Requires data generated using Azure Machine Learning ([Predictions](predictions.md) or [Custom Models](custom-models.md))</span></span>
- <span data-ttu-id="a5448-114">Mérték ellenőrzése: [Konfigurált mértékek](measures.md) szükségesek.</span><span class="sxs-lookup"><span data-stu-id="a5448-114">Measure control: Requires [configured measures](measures.md).</span></span>
- <span data-ttu-id="a5448-115">Idősor-vezérlő: [Konfigurált tevékenységeket](activities.md) igényel.</span><span class="sxs-lookup"><span data-stu-id="a5448-115">Timeline control: Requires [configured activities](activities.md).</span></span>

## <a name="install-the-customer-card-add-in"></a><span data-ttu-id="a5448-116">Az Ügyfélkártya bővítmény telepítése</span><span class="sxs-lookup"><span data-stu-id="a5448-116">Install the Customer Card Add-in</span></span>

<span data-ttu-id="a5448-117">Az Ügyfélkártya bővítmény a Dynamics 365Customer Engagement alkalmazásihoz használható megoldás.</span><span class="sxs-lookup"><span data-stu-id="a5448-117">The Customer Card Add-in is a solution for customer engagement apps in Dynamics 365.</span></span> <span data-ttu-id="a5448-118">A megoldás telepítéséhez nyissa meg az AppSource lehetőséget, és keresse meg a **Dynamics ügyfélkártyát**.</span><span class="sxs-lookup"><span data-stu-id="a5448-118">To install the solution, go to AppSource and search for **Dynamics Customer Card**.</span></span> <span data-ttu-id="a5448-119">Válassza ki az [ügyfélkártya bővítményt az AppSource megoldásban](https://appsource.microsoft.com/product/dynamics-365/mscrm.dynamics_365_customer_insights_customer_card_addin?tab=Overview), és válassza a **Letöltés most** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="a5448-119">Select the [Customer Card Add-in on AppSource](https://appsource.microsoft.com/product/dynamics-365/mscrm.dynamics_365_customer_insights_customer_card_addin?tab=Overview) and select **Get It Now**.</span></span>

<span data-ttu-id="a5448-120">A megoldás telepítéséhez előfordulhat, hogy rendszergazdai hitelesítő adataival kell bejelentkeznie a Dynamics 365 alkalmazásba.</span><span class="sxs-lookup"><span data-stu-id="a5448-120">You may need to sign in with your admin credentials for the Dynamics 365 app to install the solution.</span></span>

<span data-ttu-id="a5448-121">Eltarthat egy ideig, amíg a megoldást települ a környezetébe.</span><span class="sxs-lookup"><span data-stu-id="a5448-121">It can take some time for the solution to be installed to your environment.</span></span>

## <a name="configure-the-customer-card-add-in"></a><span data-ttu-id="a5448-122">Az ügyfélkártya bővítmény konfigurálása</span><span class="sxs-lookup"><span data-stu-id="a5448-122">Configure the Customer Card Add-in</span></span>

1. <span data-ttu-id="a5448-123">Rendszergazdaként nyissa meg a Dynamics 365 **Beállítások** szakaszát, és válassza a **Megoldások** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="a5448-123">As an admin, go to the **Settings** section in Dynamics 365 and select **Solutions**.</span></span>

1. <span data-ttu-id="a5448-124">Válassza ki a **Megjelenítendő név** hivatkozást a **Dynamics 365 Customer Insights ügyfélkártya bővítmény (előzetes verzió)** megoldáshoz.</span><span class="sxs-lookup"><span data-stu-id="a5448-124">Select the **Display Name** link for the **Dynamics 365 Customer Insights Customer Card Add-in (Preview)** solution.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="a5448-125">![Megjelenítendő név választása](media/select-display-name.png "Megjelenítendő név választása")</span><span class="sxs-lookup"><span data-stu-id="a5448-125">![Select display name](media/select-display-name.png "Select display name")</span></span>

1. <span data-ttu-id="a5448-126">Válassza a **Bejelentkezés** lehetőséget, és adja meg a Customer Insights konfigurálásához használt rendszergazdai fiók hitelesítő adatait.</span><span class="sxs-lookup"><span data-stu-id="a5448-126">Select **Sign in** and enter the credentials for the admin account you use to configure Customer Insights.</span></span>

   > [!NOTE]
   > <span data-ttu-id="a5448-127">Ellenőrizze, hogy a böngésző előugró ablakok blokkolása funkció nem blokkolja-e a hitelesítési ablakot, amikor a **Bejelentkezés** gombot választja.</span><span class="sxs-lookup"><span data-stu-id="a5448-127">Check that the browser pop-up blocker does not block the authentication window when you select the **Sign in** button.</span></span>

1. <span data-ttu-id="a5448-128">Válassza ki azt a környezetet, amelyből az adatokat szeretné lekérni.</span><span class="sxs-lookup"><span data-stu-id="a5448-128">Select the environment you want to fetch data from.</span></span>

1. <span data-ttu-id="a5448-129">Adja meg, hogy mely mezők legyenek hozzárendelve a Dynamics 365 alkalmazás rekordjait.</span><span class="sxs-lookup"><span data-stu-id="a5448-129">Define which the field mapping to records in the Dynamics 365 app.</span></span>
   - <span data-ttu-id="a5448-130">Ha egy kapcsolattartót szeretne leképezni, akkor jelölje ki a mezőt az Ügyfél entitásban kapcsolattartói entitás azonosítójának megfelelő mezőben.</span><span class="sxs-lookup"><span data-stu-id="a5448-130">To map with a contact, select the field in the Customer entity that matches the ID of your contact entity.</span></span>
   - <span data-ttu-id="a5448-131">Ha egy partnert szeretne leképezni, akkor jelölje ki a mezőt az Ügyfél entitásban partner entitás azonosítójának megfelelő mezőben.</span><span class="sxs-lookup"><span data-stu-id="a5448-131">To map with an account, select the field in the Customer entity that matches the ID of your account entity.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="a5448-132">![Kapcsolattartó azonosítója mező](media/contact-id-field.png "Kapcsolattartó azonosítója mező")</span><span class="sxs-lookup"><span data-stu-id="a5448-132">![Contact ID field](media/contact-id-field.png "Contact ID field")</span></span>

1. <span data-ttu-id="a5448-133">A beállítás mentéséhez válassza a **Konfiguráció mentése** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="a5448-133">Select **Save configuration** to save the settings.</span></span>

1. <span data-ttu-id="a5448-134">A következő lépésként biztonsági szerepköröket kell hozzárendelnie a Dynamics 365-ben, hogy a felhasználók testreszabhassák és megtekintsék az ügyfélkártyát.</span><span class="sxs-lookup"><span data-stu-id="a5448-134">Next, you need to assign security roles in Dynamics 365 so users can customize and see the customer card.</span></span> <span data-ttu-id="a5448-135">A Dynamics 365 szolgáltatásban ugorjon a **Beállítások** > **Biztonság** > **Felhasználók** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="a5448-135">In Dynamics 365, go to **Settings** > **Security** > **Users**.</span></span> <span data-ttu-id="a5448-136">Jelölje ki a felhasználói szerepkörök szerkesztéséhez használt felhasználókat, és válassza a **Szerepkörök kezelése** elemet.</span><span class="sxs-lookup"><span data-stu-id="a5448-136">Select the users to edit user roles and select **Manage roles**.</span></span>

1. <span data-ttu-id="a5448-137">Rendelje hozzá a **Customer Insights-kártya testreszabója** szerepkört azokhoz a felhasználókhoz, akik testre szabják a kártyán megjelenített tartalmat a teljes szervezetre vonatkozóan.</span><span class="sxs-lookup"><span data-stu-id="a5448-137">Assign the **Customer Insights Card Customizer** role to users who will customize the content shown on the card for the whole organization.</span></span>

## <a name="add-customer-card-controls-to-forms"></a><span data-ttu-id="a5448-138">Ügyfélkártya-vezérlők hozzáadása űrlapokhoz</span><span class="sxs-lookup"><span data-stu-id="a5448-138">Add Customer Card controls to forms</span></span>
  
1. <span data-ttu-id="a5448-139">Ha hozzá szeretné adni az ügyfélkártya vezérlőket a kapcsolattartói űrlaphoz, akkor nyissa meg a **Beállítások** > **Testreszabás** részt a Dynamics 365 megoldásban.</span><span class="sxs-lookup"><span data-stu-id="a5448-139">To add the Customer Card controls to your Contact form, go to the **Settings** > **Customizations** in Dynamics 365.</span></span>

1. <span data-ttu-id="a5448-140">Válassza ki **A rendszer testreszabása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="a5448-140">Select **Customize the System**.</span></span>

1. <span data-ttu-id="a5448-141">Tallózással keresse meg a **Kapcsolattartó** entitást, és bontsa ki, majd válassza az **Űrlapok** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="a5448-141">Browse to the **Contact** entity, expand it and select **Forms**.</span></span>

1. <span data-ttu-id="a5448-142">Válassza ki azt a kapcsolattartói űrlapot, amelyhez hozzá szeretné adni az Ügyfélkártya vezérlőit.</span><span class="sxs-lookup"><span data-stu-id="a5448-142">Select the contact form to which you want to add the Customer Card controls.</span></span>

    > [!div class="mx-imgBorder"]
    > <span data-ttu-id="a5448-143">![Válassza a Kapcsolattartói űrlapot](media/contact-active-forms.png "Válassza a Kapcsolattartói űrlapot")</span><span class="sxs-lookup"><span data-stu-id="a5448-143">![Select Contact form](media/contact-active-forms.png "Select Contact form")</span></span>

1. <span data-ttu-id="a5448-144">A vezérlő hozzáadásához húzza az űrlapszerkesztő bármelyik mezőjét a **Mezőkezelőből** arra a helyre, ahol a demográfiai vezérlőt meg szeretné jeleníteni.</span><span class="sxs-lookup"><span data-stu-id="a5448-144">To add a control, in the form editor, drag any field from the **Field Explorer** to where you want the control to appear.</span></span>

1. <span data-ttu-id="a5448-145">Jelölje ki az imént hozzáadott mezőt az űrlapon, majd válassza a **Tulajdonságok módosítása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="a5448-145">Select the field on the form that you just added, and select **Change Properties**.</span></span>

1. <span data-ttu-id="a5448-146">Lépjen a **Vezérlők** lapra, és válassza a **Vezérlő hozzáadása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="a5448-146">Go to the **Controls** tab and select **Add Control**.</span></span> <span data-ttu-id="a5448-147">Válassza ki az egyik használható egyéni vezérlőt, és válassza a **Hozzáadás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="a5448-147">Choose one of the available custom controls and select **Add**.</span></span>

1. <span data-ttu-id="a5448-148">Ha **Mezőtulajdonságok** párbeszédpanelen törölje a **Megjelenítendő címke az űrlapon** jelölését.</span><span class="sxs-lookup"><span data-stu-id="a5448-148">In the **Field Properties** dialog, clear the **Display label on the form** check box.</span></span>

1. <span data-ttu-id="a5448-149">Válassza ki **Web** lehetőséget az vezérlőhöz.</span><span class="sxs-lookup"><span data-stu-id="a5448-149">Select the **Web** option for the control.</span></span> <span data-ttu-id="a5448-150">A Dúsítási vezérlőhöz adja meg, hogy milyen dúsítástípust szeretne megjeleníteni az **enrichmentType** mező konfigurálásával.</span><span class="sxs-lookup"><span data-stu-id="a5448-150">For the Enrichment control, select which enrichment type you want to display by configuring the **enrichmentType** field.</span></span> <span data-ttu-id="a5448-151">Mindegyik bővítéstípushoz adjon hozzá külön bővítési vezérlőt.</span><span class="sxs-lookup"><span data-stu-id="a5448-151">Add a separate enrichment control for each enrichment type.</span></span>

1. <span data-ttu-id="a5448-152">Válassza a **Mentés** és a **Közzététel** lehetőséget a frissített kapcsolattartói űrlap közzétételéhez.</span><span class="sxs-lookup"><span data-stu-id="a5448-152">Select **Save** and **Publish** to publish the updated contact form.</span></span>

1. <span data-ttu-id="a5448-153">Nyissa meg a közzétett kapcsolattartó űrlapot.</span><span class="sxs-lookup"><span data-stu-id="a5448-153">Go to the published contact form.</span></span> <span data-ttu-id="a5448-154">Ekkor megjelenik az újonnan hozzáadott vezérlő.</span><span class="sxs-lookup"><span data-stu-id="a5448-154">You'll see the newly added control.</span></span> <span data-ttu-id="a5448-155">Előfordulhat, hogy első használatkor be kell jelentkeznie.</span><span class="sxs-lookup"><span data-stu-id="a5448-155">You might need to sign in the first time you use it.</span></span>

1. <span data-ttu-id="a5448-156">Ha testre szeretné szabni, hogy mit szeretne megjeleníteni az egyéni vezérlőn, akkor válassza a jobb felső sarokban található szerkesztés gombot.</span><span class="sxs-lookup"><span data-stu-id="a5448-156">To customize what you want to show on the custom control, select the edit button in the upper-right corner.</span></span>

## <a name="upgrade-customer-card-add-in"></a><span data-ttu-id="a5448-157">Ügyfélkártya bővítmény frissítése</span><span class="sxs-lookup"><span data-stu-id="a5448-157">Upgrade Customer Card Add-in</span></span>
<span data-ttu-id="a5448-158">Az Ügyfélkártya bővítmény nem frissül automatikusan.</span><span class="sxs-lookup"><span data-stu-id="a5448-158">The Customer Card Add-in doesn't upgrade automatically.</span></span> <span data-ttu-id="a5448-159">A legújabb verzióra való frissítéshez kövesse a Dynamics 365 alkalmazásban, amelyhez telepítve van a bővítmény.</span><span class="sxs-lookup"><span data-stu-id="a5448-159">To upgrade to the latest version, follow this procedure in the Dynamics 365 app that has the Add-in installed.</span></span>

1. <span data-ttu-id="a5448-160">A Dynamics 365 alkalmazásban válassza a **Beállítások** > **Testreszabás**, majd a **Megoldások** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="a5448-160">In the Dynamics 365 app, go to **Settings** > **Customization** and select **Solutions**.</span></span>

1. <span data-ttu-id="a5448-161">A bővítmények táblázatában keresse meg a **CustomerInsightsCustomerCard** elemet és jelölje ki a sort.</span><span class="sxs-lookup"><span data-stu-id="a5448-161">In the table of add-ins look for **CustomerInsightsCustomerCard** and select the row.</span></span>

1. <span data-ttu-id="a5448-162">Válassza a **Megoldásfrissítés alkalmazása** lehetőséget a műveletsávban.</span><span class="sxs-lookup"><span data-stu-id="a5448-162">Select the **Apply Solution Upgrade** in the action bar.</span></span>

   :::image type="content" source="media/customer-card-add-in-upgrade.png" alt-text="Megoldás frissítése a Dynamics 365 alkalmazások Testreszabás területén":::

1. <span data-ttu-id="a5448-164">A frissítési folyamat megkezdése után betöltési kijelző látható, amíg be nem fejeződik a frissítés.</span><span class="sxs-lookup"><span data-stu-id="a5448-164">After starting the upgrade process, you'll see a loading indicator until the upgrade completes.</span></span> <span data-ttu-id="a5448-165">Ha nincs újabb verzió, a frissítés hibaüzenetet ad.</span><span class="sxs-lookup"><span data-stu-id="a5448-165">If there's no newer version, the upgrade will show an error message.</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]