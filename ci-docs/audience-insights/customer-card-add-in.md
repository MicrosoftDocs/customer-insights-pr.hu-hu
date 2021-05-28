---
title: Ügyfélkártya bővítmény Dynamics 365-alkalmazásokhoz
description: Ezzel a bővítménnyel a célközönségből származó adatok jeleníthetők a Dynamics 365-alkalmazásokban.
ms.date: 05/18/2021
ms.reviewer: mhart
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: pkieffer
ms.author: philk
manager: shellyha
ms.openlocfilehash: 88492943ddbf9ae30c64d92b261433b74f34f682
ms.sourcegitcommit: d74430270f1b754322287c4f045d7febdae35be2
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/18/2021
ms.locfileid: "6059591"
---
# <a name="customer-card-add-in-preview"></a><span data-ttu-id="931d2-103">Ügyfélkártya bővítmény (előzetes verzió)</span><span class="sxs-lookup"><span data-stu-id="931d2-103">Customer Card Add-in (preview)</span></span>

[!INCLUDE [cc-data-platform-banner](../includes/cc-data-platform-banner.md)]

<span data-ttu-id="931d2-104">360 fokos képet kaphat az ügyfeleiről közvetlenül a Dynamics 365 alkalmazásokban.</span><span class="sxs-lookup"><span data-stu-id="931d2-104">Get a 360-degree view of your customers directly in Dynamics 365 apps.</span></span> <span data-ttu-id="931d2-105">Ha egy támogatott Dynamics 365-alkalmazásban telepíti az Ügyfélkártya bővítményt, megjelenítheti a demográfiai adatok, a betekintő információkat és a tevékenységek idővonalait.</span><span class="sxs-lookup"><span data-stu-id="931d2-105">With the Customer Card Add-in installed in a supported Dynamics 365 app you can choose to display demographics, insights, and activity timelines.</span></span> <span data-ttu-id="931d2-106">A bővítmény úgy olvassa be az adatokat a Customer Insightsból, hogy a művelet nincs hatással a csatlakoztatott Dynamics 365-alkalmazásban található adatokra.</span><span class="sxs-lookup"><span data-stu-id="931d2-106">The add-in will retrieve data from Customer Insights without affecting the data in the connected Dynamics 365 app.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="931d2-107">Előfeltételek</span><span class="sxs-lookup"><span data-stu-id="931d2-107">Prerequisites</span></span>

- <span data-ttu-id="931d2-108">A bővítmény csak a Dynamics 365 modellalapú alkalmazásaival működik (például az Értékesítés vagy a Customer Service 9.0-s vagy későbbi veziójával).</span><span class="sxs-lookup"><span data-stu-id="931d2-108">The add-in only works with Dynamics 365 model-driven apps, such as Sales or Customer Service, version 9.0 and later.</span></span>
- <span data-ttu-id="931d2-109">Ha a Dynamics 365-adatokat le szeretné képezni a célközönségadatok ügyfélprofiljaira, akkor [a Common Data Service-összekötőt kell használni a Dynamics 365-alkalmazásból való betöltéshez](connect-power-query.md).</span><span class="sxs-lookup"><span data-stu-id="931d2-109">For your Dynamics 365 data to map to the audience insights customer profiles they need to be [ingested from the Dynamics 365 app using the Common Data Service connector](connect-power-query.md).</span></span>
- <span data-ttu-id="931d2-110">Az adatok megtekintéséhez az Ügyfélkártya bővítmény minden Dynamics 365-felhasználóját [hozzá kell adni felhasználóként](permissions.md) a célközönség betekintési információihoz.</span><span class="sxs-lookup"><span data-stu-id="931d2-110">All Dynamics 365 users of the Customer Card Add-in must be [added as users](permissions.md) in audience insights to see the data.</span></span>
- <span data-ttu-id="931d2-111">Az adatok csak akkor kereshetők,ha a célközönség betekintési információihoz [konfigurálja a keresési és szűrőfunkciókat](search-filter-index.md).</span><span class="sxs-lookup"><span data-stu-id="931d2-111">[Configured search and filter capabilities](search-filter-index.md) in audience insights are required for lookup of data to work.</span></span>
- <span data-ttu-id="931d2-112">Minden bővítményellenőrzés a célközönség információi között szereplő konkrét adatokra hagyatkozik:</span><span class="sxs-lookup"><span data-stu-id="931d2-112">Each add-in control relies on specific data in audience insights:</span></span>
  - <span data-ttu-id="931d2-113">Mérték ellenőrzése: [Konfigurált mértékek](measures.md) szükségesek.</span><span class="sxs-lookup"><span data-stu-id="931d2-113">Measure control: Requires [configured measures](measures.md).</span></span>
  - <span data-ttu-id="931d2-114">Információk ellenőrzése: Az [előrejelzések](predictions.md) vagy az [egyéni modellek](custom-models.md) használatával létrehozott adatokra van szükség.</span><span class="sxs-lookup"><span data-stu-id="931d2-114">Intelligence control: Requires data generated using [predictions](predictions.md) or [custom models](custom-models.md).</span></span>
  - <span data-ttu-id="931d2-115">Demográfiai ellenőrzés: Demográfiai mezők (például az életkor vagy a nemek) az egyesített ügyfélprofilban érhetők el.</span><span class="sxs-lookup"><span data-stu-id="931d2-115">Demographic control: Demographic fields(such as age or gender) are available in the unified customer profile.</span></span>
  - <span data-ttu-id="931d2-116">A dúsítási vezérlő: az ügyfelek profiljaira alkalmazott aktív [dúsítást](enrichment-hub.md) igényel.</span><span class="sxs-lookup"><span data-stu-id="931d2-116">Enrichment control: Requires active [enrichments](enrichment-hub.md) applied to customer profiles.</span></span>
  - <span data-ttu-id="931d2-117">Idősor-vezérlő: [Konfigurált tevékenységeket](activities.md) igényel.</span><span class="sxs-lookup"><span data-stu-id="931d2-117">Timeline control: Requires [configured activities](activities.md).</span></span>

## <a name="install-the-customer-card-add-in"></a><span data-ttu-id="931d2-118">Az Ügyfélkártya bővítmény telepítése</span><span class="sxs-lookup"><span data-stu-id="931d2-118">Install the Customer Card Add-in</span></span>

<span data-ttu-id="931d2-119">Az Ügyfélkártya bővítmény a Dynamics 365Customer Engagement alkalmazásihoz használható megoldás.</span><span class="sxs-lookup"><span data-stu-id="931d2-119">The Customer Card Add-in is a solution for customer engagement apps in Dynamics 365.</span></span> <span data-ttu-id="931d2-120">A megoldás telepítéséhez nyissa meg az AppSource lehetőséget, és keresse meg a **Dynamics ügyfélkártyát**.</span><span class="sxs-lookup"><span data-stu-id="931d2-120">To install the solution, go to AppSource and search for **Dynamics Customer Card**.</span></span> <span data-ttu-id="931d2-121">Válassza ki az [ügyfélkártya bővítményt az AppSource megoldásban](https://appsource.microsoft.com/product/dynamics-365/mscrm.dynamics_365_customer_insights_customer_card_addin?tab=Overview), és válassza a **Letöltés most** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="931d2-121">Select the [Customer Card Add-in on AppSource](https://appsource.microsoft.com/product/dynamics-365/mscrm.dynamics_365_customer_insights_customer_card_addin?tab=Overview) and select **Get It Now**.</span></span>

<span data-ttu-id="931d2-122">A megoldás telepítéséhez előfordulhat, hogy rendszergazdai hitelesítő adataival kell bejelentkeznie a Dynamics 365 alkalmazásba.</span><span class="sxs-lookup"><span data-stu-id="931d2-122">You may need to sign in with your admin credentials for the Dynamics 365 app to install the solution.</span></span>

<span data-ttu-id="931d2-123">Eltarthat egy ideig, amíg a megoldást települ a környezetébe.</span><span class="sxs-lookup"><span data-stu-id="931d2-123">It can take some time for the solution to be installed to your environment.</span></span>

## <a name="configure-the-customer-card-add-in"></a><span data-ttu-id="931d2-124">Az ügyfélkártya bővítmény konfigurálása</span><span class="sxs-lookup"><span data-stu-id="931d2-124">Configure the Customer Card Add-in</span></span>

1. <span data-ttu-id="931d2-125">Rendszergazdaként nyissa meg a Dynamics 365 **Beállítások** szakaszát, és válassza a **Megoldások** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="931d2-125">As an admin, go to the **Settings** section in Dynamics 365 and select **Solutions**.</span></span>

1. <span data-ttu-id="931d2-126">Válassza ki a **Megjelenítendő név** hivatkozást a **Dynamics 365 Customer Insights ügyfélkártya bővítmény (előzetes verzió)** megoldáshoz.</span><span class="sxs-lookup"><span data-stu-id="931d2-126">Select the **Display Name** link for the **Dynamics 365 Customer Insights Customer Card Add-in (Preview)** solution.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="931d2-127">![Megjelenítendő név választása](media/select-display-name.png "Megjelenítendő név választása")</span><span class="sxs-lookup"><span data-stu-id="931d2-127">![Select display name](media/select-display-name.png "Select display name")</span></span>

1. <span data-ttu-id="931d2-128">Válassza a **Bejelentkezés** lehetőséget, és adja meg a Customer Insights konfigurálásához használt rendszergazdai fiók hitelesítő adatait.</span><span class="sxs-lookup"><span data-stu-id="931d2-128">Select **Sign in** and enter the credentials for the admin account you use to configure Customer Insights.</span></span>

   > [!NOTE]
   > <span data-ttu-id="931d2-129">Ellenőrizze, hogy a böngésző előugró ablakok blokkolása funkció nem blokkolja-e a hitelesítési ablakot, amikor a **Bejelentkezés** gombot választja.</span><span class="sxs-lookup"><span data-stu-id="931d2-129">Check that the browser pop-up blocker does not block the authentication window when you select the **Sign in** button.</span></span>

1. <span data-ttu-id="931d2-130">Válassza ki azt a Customer Insights-környezetet, amelyből az adatokat szeretné lekérni.</span><span class="sxs-lookup"><span data-stu-id="931d2-130">Select the Customer Insights environment you want to fetch data from.</span></span>

1. <span data-ttu-id="931d2-131">Adja meg a mezőleképezéseket a Dynamics 365-alkalmazásban szereplő rekordokhoz.</span><span class="sxs-lookup"><span data-stu-id="931d2-131">Define the field mapping to records in the Dynamics 365 app.</span></span> <span data-ttu-id="931d2-132">A Customer Insightsban található adatoktól függően leképezheti a következő beállításokat:</span><span class="sxs-lookup"><span data-stu-id="931d2-132">Depending on your data in Customer Insights you can choose to map the following options:</span></span>
   - <span data-ttu-id="931d2-133">Ha egy kapcsolattartót szeretne leképezni, akkor jelölje ki a mezőt az Ügyfél entitásban kapcsolattartói entitás azonosítójának megfelelő mezőben.</span><span class="sxs-lookup"><span data-stu-id="931d2-133">To map with a contact, select the field in the Customer entity that matches the ID of your contact entity.</span></span>
   - <span data-ttu-id="931d2-134">Ha egy partnert szeretne leképezni, akkor jelölje ki a mezőt az Ügyfél entitásban partner entitás azonosítójának megfelelő mezőben.</span><span class="sxs-lookup"><span data-stu-id="931d2-134">To map with an account, select the field in the Customer entity that matches the ID of your account entity.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="931d2-135">![Kapcsolattartó azonosítója mező](media/contact-id-field.png "Kapcsolattartó azonosítója mező")</span><span class="sxs-lookup"><span data-stu-id="931d2-135">![Contact ID field](media/contact-id-field.png "Contact ID field")</span></span>

1. <span data-ttu-id="931d2-136">A beállítás mentéséhez válassza a **Konfiguráció mentése** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="931d2-136">Select **Save configuration** to save the settings.</span></span>

1. <span data-ttu-id="931d2-137">A következő lépésként biztonsági szerepköröket kell hozzárendelnie a Dynamics 365-ben, hogy a felhasználók testreszabhassák és megtekintsék az ügyfélkártyát.</span><span class="sxs-lookup"><span data-stu-id="931d2-137">Next, you need to assign security roles in Dynamics 365 so users can customize and see the customer card.</span></span> <span data-ttu-id="931d2-138">A Dynamics 365 szolgáltatásban ugorjon a **Beállítások** > **Biztonság** > **Felhasználók** lehetőségre.</span><span class="sxs-lookup"><span data-stu-id="931d2-138">In Dynamics 365, go to **Settings** > **Security** > **Users**.</span></span> <span data-ttu-id="931d2-139">Jelölje ki a felhasználói szerepkörök szerkesztéséhez használt felhasználókat, és válassza a **Szerepkörök kezelése** elemet.</span><span class="sxs-lookup"><span data-stu-id="931d2-139">Select the users to edit user roles and select **Manage roles**.</span></span>

1. <span data-ttu-id="931d2-140">Rendelje hozzá a **Customer Insights-kártya testreszabója** szerepkört azokhoz a felhasználókhoz, akik testre szabják a kártyán megjelenített tartalmat a teljes szervezetre vonatkozóan.</span><span class="sxs-lookup"><span data-stu-id="931d2-140">Assign the **Customer Insights Card Customizer** role to users who will customize the content shown on the card for the whole organization.</span></span>

## <a name="add-customer-card-controls-to-forms"></a><span data-ttu-id="931d2-141">Ügyfélkártya-vezérlők hozzáadása űrlapokhoz</span><span class="sxs-lookup"><span data-stu-id="931d2-141">Add Customer Card controls to forms</span></span>
  
1. <span data-ttu-id="931d2-142">Ha hozzá szeretné adni az ügyfélkártya vezérlőket a kapcsolattartói űrlaphoz, akkor nyissa meg a **Beállítások** > **Testreszabás** részt a Dynamics 365 megoldásban.</span><span class="sxs-lookup"><span data-stu-id="931d2-142">To add the Customer Card controls to your Contact form, go to the **Settings** > **Customizations** in Dynamics 365.</span></span>

1. <span data-ttu-id="931d2-143">Válassza ki **A rendszer testreszabása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="931d2-143">Select **Customize the System**.</span></span>

1. <span data-ttu-id="931d2-144">Tallózással keresse meg a **Kapcsolattartó** entitást, és bontsa ki, majd válassza az **Űrlapok** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="931d2-144">Browse to the **Contact** entity, expand it and select **Forms**.</span></span>

1. <span data-ttu-id="931d2-145">Válassza ki azt a kapcsolattartói űrlapot, amelyhez hozzá szeretné adni az Ügyfélkártya vezérlőit.</span><span class="sxs-lookup"><span data-stu-id="931d2-145">Select the contact form to which you want to add the Customer Card controls.</span></span>

    > [!div class="mx-imgBorder"]
    > <span data-ttu-id="931d2-146">![Válassza a Kapcsolattartói űrlapot](media/contact-active-forms.png "Válassza a Kapcsolattartói űrlapot")</span><span class="sxs-lookup"><span data-stu-id="931d2-146">![Select Contact form](media/contact-active-forms.png "Select Contact form")</span></span>

1. <span data-ttu-id="931d2-147">A vezérlő hozzáadásához húzza az űrlapszerkesztő bármelyik mezőjét a **Mezőkezelőből** arra a helyre, ahol a demográfiai vezérlőt meg szeretné jeleníteni.</span><span class="sxs-lookup"><span data-stu-id="931d2-147">To add a control, in the form editor, drag any field from the **Field Explorer** to where you want the control to appear.</span></span>

1. <span data-ttu-id="931d2-148">Jelölje ki az imént hozzáadott mezőt az űrlapon, majd válassza a **Tulajdonságok módosítása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="931d2-148">Select the field on the form that you just added, and select **Change Properties**.</span></span>

1. <span data-ttu-id="931d2-149">Lépjen a **Vezérlők** lapra, és válassza a **Vezérlő hozzáadása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="931d2-149">Go to the **Controls** tab and select **Add Control**.</span></span> <span data-ttu-id="931d2-150">Válassza ki az egyik használható egyéni vezérlőt, és válassza a **Hozzáadás** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="931d2-150">Choose one of the available custom controls and select **Add**.</span></span>

1. <span data-ttu-id="931d2-151">Ha **Mezőtulajdonságok** párbeszédpanelen törölje a **Megjelenítendő címke az űrlapon** jelölését.</span><span class="sxs-lookup"><span data-stu-id="931d2-151">In the **Field Properties** dialog, clear the **Display label on the form** check box.</span></span>

1. <span data-ttu-id="931d2-152">Válassza ki **Web** lehetőséget az vezérlőhöz.</span><span class="sxs-lookup"><span data-stu-id="931d2-152">Select the **Web** option for the control.</span></span> <span data-ttu-id="931d2-153">A Dúsítási vezérlőhöz adja meg, hogy milyen dúsítástípust szeretne megjeleníteni az **enrichmentType** mező konfigurálásával.</span><span class="sxs-lookup"><span data-stu-id="931d2-153">For the Enrichment control, select which enrichment type you want to display by configuring the **enrichmentType** field.</span></span> <span data-ttu-id="931d2-154">Mindegyik bővítéstípushoz adjon hozzá külön bővítési vezérlőt.</span><span class="sxs-lookup"><span data-stu-id="931d2-154">Add a separate enrichment control for each enrichment type.</span></span>

1. <span data-ttu-id="931d2-155">Válassza a **Mentés** és a **Közzététel** lehetőséget a frissített kapcsolattartói űrlap közzétételéhez.</span><span class="sxs-lookup"><span data-stu-id="931d2-155">Select **Save** and **Publish** to publish the updated contact form.</span></span>

1. <span data-ttu-id="931d2-156">Nyissa meg a közzétett kapcsolattartó űrlapot.</span><span class="sxs-lookup"><span data-stu-id="931d2-156">Go to the published contact form.</span></span> <span data-ttu-id="931d2-157">Ekkor megjelenik az újonnan hozzáadott vezérlő.</span><span class="sxs-lookup"><span data-stu-id="931d2-157">You'll see the newly added control.</span></span> <span data-ttu-id="931d2-158">Előfordulhat, hogy első használatkor be kell jelentkeznie.</span><span class="sxs-lookup"><span data-stu-id="931d2-158">You might need to sign in the first time you use it.</span></span>

1. <span data-ttu-id="931d2-159">Ha testre szeretné szabni, hogy mit szeretne megjeleníteni az egyéni vezérlőn, akkor válassza a jobb felső sarokban található szerkesztés gombot.</span><span class="sxs-lookup"><span data-stu-id="931d2-159">To customize what you want to show on the custom control, select the edit button in the upper-right corner.</span></span>

## <a name="upgrade-customer-card-add-in"></a><span data-ttu-id="931d2-160">Ügyfélkártya bővítmény frissítése</span><span class="sxs-lookup"><span data-stu-id="931d2-160">Upgrade Customer Card Add-in</span></span>
<span data-ttu-id="931d2-161">Az Ügyfélkártya bővítmény nem frissül automatikusan.</span><span class="sxs-lookup"><span data-stu-id="931d2-161">The Customer Card Add-in doesn't upgrade automatically.</span></span> <span data-ttu-id="931d2-162">A legújabb verzióra való frissítéshez kövesse a Dynamics 365 alkalmazásban, amelyhez telepítve van a bővítmény.</span><span class="sxs-lookup"><span data-stu-id="931d2-162">To upgrade to the latest version, follow this procedure in the Dynamics 365 app that has the Add-in installed.</span></span>

1. <span data-ttu-id="931d2-163">A Dynamics 365 alkalmazásban válassza a **Beállítások** > **Testreszabás**, majd a **Megoldások** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="931d2-163">In the Dynamics 365 app, go to **Settings** > **Customization** and select **Solutions**.</span></span>

1. <span data-ttu-id="931d2-164">A bővítmények táblázatában keresse meg a **CustomerInsightsCustomerCard** elemet és jelölje ki a sort.</span><span class="sxs-lookup"><span data-stu-id="931d2-164">In the table of add-ins look for **CustomerInsightsCustomerCard** and select the row.</span></span>

1. <span data-ttu-id="931d2-165">Válassza a **Megoldásfrissítés alkalmazása** lehetőséget a műveletsávban.</span><span class="sxs-lookup"><span data-stu-id="931d2-165">Select the **Apply Solution Upgrade** in the action bar.</span></span>

   :::image type="content" source="media/customer-card-add-in-upgrade.png" alt-text="Megoldás frissítése a Dynamics 365 alkalmazások Testreszabás területén":::

1. <span data-ttu-id="931d2-167">A frissítési folyamat megkezdése után betöltési kijelző látható, amíg be nem fejeződik a frissítés.</span><span class="sxs-lookup"><span data-stu-id="931d2-167">After starting the upgrade process, you'll see a loading indicator until the upgrade completes.</span></span> <span data-ttu-id="931d2-168">Ha nincs újabb verzió, a frissítés hibaüzenetet ad.</span><span class="sxs-lookup"><span data-stu-id="931d2-168">If there's no newer version, the upgrade will show an error message.</span></span>


[!INCLUDE[footer-include](../includes/footer-banner.md)]
