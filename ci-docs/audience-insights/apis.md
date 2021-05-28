---
title: Az API-k használata
description: Az API-k használata és a korlátozások megismerése.
ms.date: 05/10/2021
ms.reviewer: wimohabb
ms.service: customer-insights
ms.subservice: audience-insights
ms.topic: conceptual
author: m-hartmann
ms.author: wimohabb
manager: shellyha
ms.openlocfilehash: 4d41d7d328dfa6699b5f5e992d3a5bf3179490d8
ms.sourcegitcommit: 33a8e21b3bf6521bdb8346f81f79fce88091ddfd
ms.translationtype: HT
ms.contentlocale: hu-HU
ms.lasthandoff: 05/10/2021
ms.locfileid: "6016595"
---
# <a name="work-with-customer-insights-apis"></a><span data-ttu-id="c9441-103">Customer Insights API-k használata</span><span class="sxs-lookup"><span data-stu-id="c9441-103">Work with Customer Insights APIs</span></span>

<span data-ttu-id="c9441-104">Dynamics 365 Customer Insights az API-kat biztosít, amivel saját alkalmazásokat hozhat létre a Customer Insights adatok alapján.</span><span class="sxs-lookup"><span data-stu-id="c9441-104">Dynamics 365 Customer Insights provides APIs to build your own applications based you data in Customer Insights.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c9441-105">Az API-k részletes ismertetése a [Customer Insights API-k segédeletében](https://developer.ci.ai.dynamics.com/api-details#api=CustomerInsights) található.</span><span class="sxs-lookup"><span data-stu-id="c9441-105">Details of these APIs, are listed on the [Customer Insights APIs reference](https://developer.ci.ai.dynamics.com/api-details#api=CustomerInsights).</span></span> <span data-ttu-id="c9441-106">További információkat tartalmaznak a műveletekről, a paraméterekről és a válaszokról.</span><span class="sxs-lookup"><span data-stu-id="c9441-106">They include additional information about operations, parameters, and responses.</span></span>

<span data-ttu-id="c9441-107">A cikk végigvezeti a Customer Insights API-k elérésén, Azure-alkalmazás regisztrálásának létrehozásához, valamint a rendelkezésre álló ügyféloldali tárak használatba vételéhez segítséget nyújt.</span><span class="sxs-lookup"><span data-stu-id="c9441-107">This article guides you to access to the Customer Insights APIs, create an Azure App Registration, and help you get started with the available client libraries.</span></span>

## <a name="get-started-trying-the-customer-insights-apis"></a><span data-ttu-id="c9441-108">Ismerkedés a Customer Insights API-k kipróbálásával</span><span class="sxs-lookup"><span data-stu-id="c9441-108">Get started trying the Customer Insights APIs</span></span>

1. <span data-ttu-id="c9441-109">[Jelentkezzen be](https://home.ci.ai.dynamics.com) a Customer Insights szolgáltatásba.</span><span class="sxs-lookup"><span data-stu-id="c9441-109">[Sign in](https://home.ci.ai.dynamics.com) to Customer Insights.</span></span> <span data-ttu-id="c9441-110">Ha még nincs előfizetése, [iratkozzon fel a Customer Insights próbaverziójára](https://aka.ms/tryci).</span><span class="sxs-lookup"><span data-stu-id="c9441-110">If you don't have a subscription yet, [sign up for a trial of Customer Insights](https://aka.ms/tryci).</span></span>

1. <span data-ttu-id="c9441-111">Az API-k engedélyezéséhez a Customer Insights környezetében látogasson el a **Rendszergazda** > **Engedélyek** pontra.</span><span class="sxs-lookup"><span data-stu-id="c9441-111">To enable APIs on your Customer Insights environment, go to **Admin** > **Permissions**.</span></span> <span data-ttu-id="c9441-112">Ehhez rendszergazdai engedélyekre van szükség.</span><span class="sxs-lookup"><span data-stu-id="c9441-112">You'll need admin permissions to do so.</span></span>

1. <span data-ttu-id="c9441-113">Nyissa meg az **API-k** lapot, és jelölje be az **Engedélyezés** gombot.</span><span class="sxs-lookup"><span data-stu-id="c9441-113">Go to the **APIs** tab and select the **Enable** button.</span></span>    
   <span data-ttu-id="c9441-114">Az API-k engedélyezésekor a rendszer elsődleges és másodlagos előfizetési kulcsot hoz létre az API-kérésekben használt példányhoz.</span><span class="sxs-lookup"><span data-stu-id="c9441-114">Enabling the APIs creates a primary and secondary subscription key for your instance that gets used in the API requests.</span></span> <span data-ttu-id="c9441-115">A kulcsok újbóli generálásához válassza az **Elsődleges újbóli létrehozása** vagy a **Másodlagos újbóli létrehozása** beállítást a **Rendszergazda** > **Engedélyek** > **API-k** között.</span><span class="sxs-lookup"><span data-stu-id="c9441-115">You can regenerate the keys by selecting the **Regenerate primary** or **Regenerate secondary** on **Admin** > **Permissions** > **APIs**.</span></span>

   :::image type="content" source="media/enable-apis.gif" alt-text="Customer Insights API-k engedélyezése":::

1. <span data-ttu-id="c9441-117">Az **API-k kipróbálásához** válassza az [API-k kipróbálása](https://developer.ci.ai.dynamics.com/api-details#api=CustomerInsights&operation=Get-all-instances) lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="c9441-117">Select **Explore our APIs** to [try out the APIs](https://developer.ci.ai.dynamics.com/api-details#api=CustomerInsights&operation=Get-all-instances).</span></span>

1. <span data-ttu-id="c9441-118">Válasszon egy API-műveletet, és válassza a **Kipróbálásá** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="c9441-118">Choose an API operation and select **Try it**.</span></span>

1. <span data-ttu-id="c9441-119">Az oldalsó ablaktáblában állítsa az **Engedélyezés** legördülő menüt **Implicit** értékre.</span><span class="sxs-lookup"><span data-stu-id="c9441-119">In the side pane, set the value in the **Authorization** drop-down menu to **implicit**.</span></span> <span data-ttu-id="c9441-120">Az `Authorization` fejléchez hozzáadásra kerül egy tulajdonosi jogkivonat.</span><span class="sxs-lookup"><span data-stu-id="c9441-120">The `Authorization` header gets with a bearer token added.</span></span> <span data-ttu-id="c9441-121">Az előfizetési kulcsot a rendszer automatikusan kitölti.</span><span class="sxs-lookup"><span data-stu-id="c9441-121">Your subscription key will be automatically populated.</span></span>
  
1. <span data-ttu-id="c9441-122">Tetszés szerint hozzáadhatja az összes szükséges lekérdezési paramétert.</span><span class="sxs-lookup"><span data-stu-id="c9441-122">Optionally, add all necessary query parameters.</span></span>

1. <span data-ttu-id="c9441-123">Görgessen az oldalsó panel aljára, és válassza a **Küldés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="c9441-123">Scroll to the bottom of the side pane and select **Send**.</span></span>

<span data-ttu-id="c9441-124">A HTTP-válasz hamarosan az alábbiakban jelenik meg.</span><span class="sxs-lookup"><span data-stu-id="c9441-124">The HTTP response will soon appear below.</span></span>


   :::image type="content" source="media/try-apis.gif" alt-text="Az API-k kiválasztott tesztelését bemutató animált gif.":::

## <a name="create-a-new-app-registration-in-the-azure-portal"></a><span data-ttu-id="c9441-126">Hozzon létre egy új alkalmazásregisztrációt az Azure Portalon</span><span class="sxs-lookup"><span data-stu-id="c9441-126">Create a new app registration in the Azure portal</span></span>

<span data-ttu-id="c9441-127">Ezekkel a lépésekkel megteheti az első lépéseket a Customer Insights API használatában egy Azure-alkalmazásban a delegált engedélyekkel.</span><span class="sxs-lookup"><span data-stu-id="c9441-127">These steps help you get started in using the Customer Insights APIs in an Azure application using delegated permissions.</span></span> <span data-ttu-id="c9441-128">Győződjön meg róla, hogy először elvégezte az [Első lépések](#get-started-trying-the-customer-insights-apis) részt.</span><span class="sxs-lookup"><span data-stu-id="c9441-128">Make sure to have completed [Getting started section](#get-started-trying-the-customer-insights-apis) first.</span></span>

1. <span data-ttu-id="c9441-129">Jelentkezzen be az [Azure portálba](https://portal.azure.com) weboldalára azzal a fiókkal, amely hozzáfér a Customer Insights adatokhoz.</span><span class="sxs-lookup"><span data-stu-id="c9441-129">Sign in to the [Azure portal](https://portal.azure.com) with the account that can access the Customer Insights data.</span></span>

1. <span data-ttu-id="c9441-130">A bal oldalon válassza az **Alkalmazásregisztrációk** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="c9441-130">On the left, select **App registrations**.</span></span>

1. <span data-ttu-id="c9441-131">Válassza az **Új regisztráció** lehetőséget, és adja meg az alkalmazás nevét és a fiók típusát.</span><span class="sxs-lookup"><span data-stu-id="c9441-131">Select **New registration** provide an application name and choose the account type.</span></span>
   <span data-ttu-id="c9441-132">Ha szeretne, megadhat egy átirányítási URL-címet.</span><span class="sxs-lookup"><span data-stu-id="c9441-132">Optionally, add a redirect URL.</span></span> <span data-ttu-id="c9441-133">http://localhost elegendő az alkalmazások helyi számítógépen történő fejlesztéséhez.</span><span class="sxs-lookup"><span data-stu-id="c9441-133">http://localhost is sufficient for developing an application on your local computer.</span></span>

1. <span data-ttu-id="c9441-134">Az új alkalmazás regisztrálásával nyissa meg az **API-engedélyeket**.</span><span class="sxs-lookup"><span data-stu-id="c9441-134">On your new App registration, go to **API permissions**.</span></span>

   :::image type="content" source="media/app-registration-1.gif" alt-text="API-engedélyek beállítása az alkalmazás regisztrálásához - animált gif.":::

1. <span data-ttu-id="c9441-136">Válassza az **Engedély hozzáadása** lehetőséget, és az oldalsó panelben válassza a **Customer Insights** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="c9441-136">Select **Add a permission** and select **Customer Insights** in the side pane.</span></span>

1. <span data-ttu-id="c9441-137">A **Engedély típusához** válassza a **Delegált engedélyek** lehetőséget, és jelölje ki a **user_impersonation** engedélyt.</span><span class="sxs-lookup"><span data-stu-id="c9441-137">For **Permission type**, select **Delegated permissions** and select the **user_impersonation** permission.</span></span>

1. <span data-ttu-id="c9441-138">Jelölje be az **Engedélyek hozzáadása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="c9441-138">Select **Add permissions**.</span></span> <span data-ttu-id="c9441-139">Ha felhasználói bejelentkezés nélkül kell elérnie az API-t, tekintse át a [Kiszolgálók közötti alkalmazásengedélyek](#server-to-server-application-permissions) szakaszt.</span><span class="sxs-lookup"><span data-stu-id="c9441-139">If you need to access the API without a user signing in, review the [Server-to-server application permissions](#server-to-server-application-permissions) section.</span></span>

1. <span data-ttu-id="c9441-140">Válassza a **Rendszergazdai hozzájárulás biztosítása a következőhöz:** lehetőséget az alkalmazásregisztráció befejezéséhez.</span><span class="sxs-lookup"><span data-stu-id="c9441-140">Select **Grant admin consent for...** to complete the app registration.</span></span>

<span data-ttu-id="c9441-141">Használhatja az alkalmazás/ügyfélazonosítót az alkalmazásregisztrációhoz a Microsoft hitelesítési függvénytárral (MSAL), hogy megszerezze a tulajdonosi jogkivonatot, amelyet elküldhet a kéréssel az API-nak.</span><span class="sxs-lookup"><span data-stu-id="c9441-141">You can use the Application/Client ID for this app registration with the Microsoft Authentication Library (MSAL) to obtain a bearer token to send with your request to the API.</span></span>

:::image type="content" source="media/grant-admin-consent.gif" alt-text="Animált gif a rendszergazdai hozzájárulás biztosítására.":::

<span data-ttu-id="c9441-143">Az MSAL-lel kapcsolatos további információkért tekintse át a [Microsoft hitelesítési függvénytár (MSAL) áttekintése](/azure/active-directory/develop/msal-overview).</span><span class="sxs-lookup"><span data-stu-id="c9441-143">For more information about MSAL, see [Overview of Microsoft Authentication Library (MSAL)](/azure/active-directory/develop/msal-overview).</span></span>

<span data-ttu-id="c9441-144">Az alkalmazással kapcsolatos további információkért tekintse meg [Az Azure Portal alkalmazás új regisztrációs élményét](/azure/active-directory/develop/app-registration-portal-training-guide).</span><span class="sxs-lookup"><span data-stu-id="c9441-144">For more information about app registration in Azure, see [The new Azure portal app registration experience](/azure/active-directory/develop/app-registration-portal-training-guide).</span></span>

<span data-ttu-id="c9441-145">Az API-k ügyféltárakban való használatára vonatkozó információkért tekintse meg a [Customer Insights ügyféloldali tárakat](#customer-insights-client-libraries).</span><span class="sxs-lookup"><span data-stu-id="c9441-145">For information on using the APIs our client libraries, see [Customer Insights client libraries](#customer-insights-client-libraries).</span></span>

### <a name="server-to-server-application-permissions"></a><span data-ttu-id="c9441-146">Kiszolgálók közötti alkalmazásengedélyek</span><span class="sxs-lookup"><span data-stu-id="c9441-146">Server-to-server application permissions</span></span>

<span data-ttu-id="c9441-147">Az [alkalmazásregisztráció című szakasz](#create-a-new-app-registration-in-the-azure-portal) ismerteti, hogyan lehet olyan alkalmazást regisztrálni, amelyhez a felhasználónak be kell jelentkeznie a hitelesítéshez.</span><span class="sxs-lookup"><span data-stu-id="c9441-147">The [app registration section](#create-a-new-app-registration-in-the-azure-portal) outlines how to register an app that requires a user to sign in for authentication.</span></span> <span data-ttu-id="c9441-148">Megismerheti, hogyan hozhat létre olyan alkalmazásregisztrációt, amelyhez nincs szükség felhasználói beavatkozásra, és futtatható kiszolgálón is.</span><span class="sxs-lookup"><span data-stu-id="c9441-148">Learn how to create an app registration that does not need user interaction and can be run on a server.</span></span>

1. <span data-ttu-id="c9441-149">Az Azure portál alkalmazásregisztrációja után nyissa meg az **API-engedélyeket**.</span><span class="sxs-lookup"><span data-stu-id="c9441-149">On your App registration in the Azure portal, go to **API permissions**.</span></span>

1. <span data-ttu-id="c9441-150">Válassza az **Engedély hozzáadása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="c9441-150">Select **Add a permission**.</span></span> 

1. <span data-ttu-id="c9441-151">Lépjen a **Szervezetem által használt API-k** lapra, és válassza ki a lista **Dynamics 365 AI for Customer Insights** elemét.</span><span class="sxs-lookup"><span data-stu-id="c9441-151">Select the **APIs my organization uses** tab and choose **Dynamics 365 AI for Customer Insights** from the list.</span></span> 

1. <span data-ttu-id="c9441-152">A **Engedély típusához** válassza az **Alkalmazásengedélyek** lehetőséget, és jelölje ki a **CustomerInsights.Api.All** engedélyt.</span><span class="sxs-lookup"><span data-stu-id="c9441-152">For **Permission type**, select **Application permissions** and select the **CustomerInsights.Api.All** permission.</span></span>

1. <span data-ttu-id="c9441-153">Jelölje be az **Engedélyek hozzáadása** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="c9441-153">Select **Add permissions**.</span></span>

1. <span data-ttu-id="c9441-154">Az alkalmazás regisztrálásához lépjen vissza az **API-engedélyekhez**.</span><span class="sxs-lookup"><span data-stu-id="c9441-154">Go back to **API permissions** for your app registration.</span></span>

1. <span data-ttu-id="c9441-155">Válassza a **Rendszergazdai hozzájárulás biztosítása a következőhöz:** lehetőséget az alkalmazásregisztráció befejezéséhez.</span><span class="sxs-lookup"><span data-stu-id="c9441-155">Select **Grant admin consent for...** to complete the app registration.</span></span>

   :::image type="content" source="media/grant-admin-consent.gif" alt-text="Animált gif a rendszergazdai hozzájárulás biztosítására.":::

1. <span data-ttu-id="c9441-157">Következtetésképp hozzá kell adnunk az alkalmazásregisztráció nevét felhasználóként a Customer Insightsban.</span><span class="sxs-lookup"><span data-stu-id="c9441-157">To conclude, we have to add the name of the app registration as a user in Customer Insights.</span></span>    
   <span data-ttu-id="c9441-158">Nyissa meg a Customer Insights szolgáltatást **Rendszergazda** > **Engedélyek** pontra, és válassza a **Felhasználó hozzáadása**.</span><span class="sxs-lookup"><span data-stu-id="c9441-158">Open Customer Insights, go to **Admin** > **Permissions** and select **Add user**.</span></span>

1. <span data-ttu-id="c9441-159">Keresse meg az alkalmazásregisztrációjának nevét, jelölje ki a keresési eredmények között, és válassza a **Mentés** lehetőséget.</span><span class="sxs-lookup"><span data-stu-id="c9441-159">Search for the name of your app registration, select it from the search results, and select **Save**.</span></span>

## <a name="customer-insights-client-libraries"></a><span data-ttu-id="c9441-160">Customer Insights ügyféloldali tárak</span><span class="sxs-lookup"><span data-stu-id="c9441-160">Customer Insights client libraries</span></span>

<span data-ttu-id="c9441-161">Ez a szakasz segítséget nyújt a Customer Insights API-k számára elérhető ügyféloldali függvénytárak használatba vételéhez.</span><span class="sxs-lookup"><span data-stu-id="c9441-161">This section helps you get started using the client libraries available for the Customer Insights APIs.</span></span> <span data-ttu-id="c9441-162">Minden függvénytár-forráskód és mintaalkalmazás megtalálható a [Customer Insights GitHub oldalon](https://github.com/microsoft/Dynamics365-CustomerInsights-Client-Libraries).</span><span class="sxs-lookup"><span data-stu-id="c9441-162">All library source code and sample applications can be found on the [Customer Insights GitHub page](https://github.com/microsoft/Dynamics365-CustomerInsights-Client-Libraries).</span></span> 

### <a name="c-nuget"></a><span data-ttu-id="c9441-163">C# NuGet</span><span class="sxs-lookup"><span data-stu-id="c9441-163">C# NuGet</span></span>

<span data-ttu-id="c9441-164">Ismerje meg a C# ügyféloldali függvénytárak használatának első lépéseit a NuGet.org webhelyről. A NuGet csomaggal kapcsolatos további információkért lásd: [Microsoft.Dynamics.CustomerInsights.Api](https://www.nuget.org/packages/Microsoft.Dynamics.CustomerInsights.Api/).</span><span class="sxs-lookup"><span data-stu-id="c9441-164">Learn how to get started using the C# client libraries from NuGet.org. For more information on the NuGet package, see [Microsoft.Dynamics.CustomerInsights.Api](https://www.nuget.org/packages/Microsoft.Dynamics.CustomerInsights.Api/).</span></span> <span data-ttu-id="c9441-165">A csomag jelenleg a netstandard2.0 és a netcoreapp2.0 keretrendszert célozza meg.</span><span class="sxs-lookup"><span data-stu-id="c9441-165">Currently, this package targets the netstandard2.0 and netcoreapp2.0 frameworks.</span></span>

#### <a name="add-the-c-client-library-to-a-c-project"></a><span data-ttu-id="c9441-166">C# ügyféloldali függvénytár hozzáadása C#-projekthez</span><span class="sxs-lookup"><span data-stu-id="c9441-166">Add the C# client library to a C# project</span></span>

1. <span data-ttu-id="c9441-167">A Visual Studio szolgáltatásban nyissa meg a **NuGet csomagkezelő** elemet a projekthez.</span><span class="sxs-lookup"><span data-stu-id="c9441-167">In Visual Studio, open the **NuGet Package Manager** for your project.</span></span>

1. <span data-ttu-id="c9441-168">Keresse meg a **Microsoft.Dynamics.CustomerInsights.Api**.</span><span class="sxs-lookup"><span data-stu-id="c9441-168">Search for **Microsoft.Dynamics.CustomerInsights.Api**.</span></span>

1. <span data-ttu-id="c9441-169">Válassza a **Telepítés** lehetőséget a csomag projekthez való hozzáadásához.</span><span class="sxs-lookup"><span data-stu-id="c9441-169">Select **Install** to add the package to the project.</span></span>
   <span data-ttu-id="c9441-170">Másik lehetőségként futtassa ezt a parancsot a **NuGet csomagkezelő konzolon**: `Install-Package -Id Microsoft.Dynamics.CustomerInsights.Api -Source nuget.org -ProjectName <project name> [-Version <version>]`</span><span class="sxs-lookup"><span data-stu-id="c9441-170">Alternatively, run this command in the **NuGet Package Manager Console**: `Install-Package -Id Microsoft.Dynamics.CustomerInsights.Api -Source nuget.org -ProjectName <project name> [-Version <version>]`</span></span>

   :::image type="content" source="media/visual-studio-nuget-package.gif" alt-text="NuGet-csomag hozzáadása Visual Studio-projekthez":::

#### <a name="use-the-c-client-library"></a><span data-ttu-id="c9441-172">A C# ügyféloldali függvénytár használata</span><span class="sxs-lookup"><span data-stu-id="c9441-172">Use the C# client library</span></span>

1. <span data-ttu-id="c9441-173">Használja a [Microsoft hitelesítési függvénytárat (MSAL)](/azure/active-directory/develop/msal-overview), és használja a `AccessToken` meglévő [Azure alkalmazásregisztrációt](#create-a-new-app-registration-in-the-azure-portal).</span><span class="sxs-lookup"><span data-stu-id="c9441-173">Use the [Microsoft Authentication Library (MSAL)](/azure/active-directory/develop/msal-overview) to get an `AccessToken` using your existing [Azure app registration](#create-a-new-app-registration-in-the-azure-portal).</span></span>

1. <span data-ttu-id="c9441-174">A token sikeres hitelesítése és megszerzése után hozzon létre egy új `HttpClient` elemet, vagy használjon egy meglévőt a kiegészítő **DefaultRequestHeaders "Authorization"** beállítást **Tulajdonos <access token>** értékre állítva, és az **Ocp-Apim-Subscription-Key** beállítást [**előfizetési kulcs** a Customer Insights környeuetről](#get-started-trying-the-customer-insights-apis).</span><span class="sxs-lookup"><span data-stu-id="c9441-174">After successfully authenticating and acquiring a token, construct a new or use an existing `HttpClient` with the additional **DefaultRequestHeaders "Authorization"** set to **Bearer <access token>** and **Ocp-Apim-Subscription-Key** set to the [**subscription key** from your Customer Insights environment](#get-started-trying-the-customer-insights-apis).</span></span>    
   <span data-ttu-id="c9441-175">Szükség esetén állítsa vissza az **Engedélyezés** fejlécet.</span><span class="sxs-lookup"><span data-stu-id="c9441-175">Reset the **Authorization** header when appropriate.</span></span> <span data-ttu-id="c9441-176">Ha például a token lejárt.</span><span class="sxs-lookup"><span data-stu-id="c9441-176">For example, when the token expired.</span></span>

1. <span data-ttu-id="c9441-177">Adja át ezt a `HttpClient` elemet a `CustomerInsights` ügyfél felépítéséhez.</span><span class="sxs-lookup"><span data-stu-id="c9441-177">Pass this `HttpClient` into the construction of the `CustomerInsights` client.</span></span>

   :::image type="content" source="media/httpclient-sample.png" alt-text="Httpclient mintája":::

1. <span data-ttu-id="c9441-179">Indítson hívást a klienssel a „kiterjesztési módszerekhez”, például `GetAllInstancesAsync`.</span><span class="sxs-lookup"><span data-stu-id="c9441-179">Make calls with the client to the "extension methods", for example, `GetAllInstancesAsync`.</span></span> <span data-ttu-id="c9441-180">Ha az alapul szolgáló `Microsoft.Rest.HttpOperationResponse` elem elérését részesíti előnyben, használja a "http-üzenetek módszereit", például `GetAllInstancesWithHttpMessagesAsync`.</span><span class="sxs-lookup"><span data-stu-id="c9441-180">If access to the underlying `Microsoft.Rest.HttpOperationResponse` is preferred, use the "http message methods", for example `GetAllInstancesWithHttpMessagesAsync`.</span></span>

1. <span data-ttu-id="c9441-181">A válasz valószínűleg `object` típusú lesz, mert a módszer többféle típust képes visszaadni (például `IList<InstanceInfo>` és `ApiErrorResult`).</span><span class="sxs-lookup"><span data-stu-id="c9441-181">The response will likely be of type `object` because the method can return multiple types (for example, `IList<InstanceInfo>` and `ApiErrorResult`).</span></span> <span data-ttu-id="c9441-182">A visszatérési típus ellenőrzéséhez biztonságosan konvertálhatja az objektumokat az adott művelet [API-részletek lapján](https://developer.ci.ai.dynamics.com/api-details#api=CustomerInsights) megadott választípusokká.</span><span class="sxs-lookup"><span data-stu-id="c9441-182">To check the return type, you can safely cast the objects into the response types specified on the [API details page](https://developer.ci.ai.dynamics.com/api-details#api=CustomerInsights) for that operation.</span></span>    
   <span data-ttu-id="c9441-183">Ha a kérésre vonatkozóan további információra van szükség, akkor a **http-üzenetek módszereit** használhatja a nyers válasz objektum eléréséhez.</span><span class="sxs-lookup"><span data-stu-id="c9441-183">If more information on the request is needed, use the **http message methods** to access the raw response object.</span></span>

### <a name="nodejs-package"></a><span data-ttu-id="c9441-184">NodeJS-csomag</span><span class="sxs-lookup"><span data-stu-id="c9441-184">NodeJS package</span></span>

<span data-ttu-id="c9441-185">Használja a NodeJS-ügyféltárakat, amelyek az NPM-en keresztül elérhetők: https://www.npmjs.com/package/@microsoft/customerinsights</span><span class="sxs-lookup"><span data-stu-id="c9441-185">Use the NodeJS client libraries available through NPM: https://www.npmjs.com/package/@microsoft/customerinsights</span></span>

### <a name="python-package"></a><span data-ttu-id="c9441-186">Python-csomag</span><span class="sxs-lookup"><span data-stu-id="c9441-186">Python package</span></span>

<span data-ttu-id="c9441-187">Használja a Python-ügyféltárakat, amelyek az PyPi-n keresztül elérhetők: https://pypi.org/project/customerinsights/</span><span class="sxs-lookup"><span data-stu-id="c9441-187">Use the Python client libraries available through PyPi: https://pypi.org/project/customerinsights/</span></span>

[!INCLUDE[footer-include](../includes/footer-banner.md)]
